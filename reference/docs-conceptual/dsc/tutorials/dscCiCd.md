---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: DSC를 사용하여 연속 통합 및 연속 배포 파이프라인 빌드
ms.openlocfilehash: 2d049cd640f0df9b018a88ad106e59dbeed7bcee
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954240"
---
# <a name="building-a-continuous-integration-and-continuous-deployment-pipeline-with-dsc"></a>DSC를 사용하여 연속 통합 및 연속 배포 파이프라인 빌드

이 예제에는 PowerShell, DSC, Pester 및 Visual Studio TFS(Team Foundation Server)를 사용하여 CI/CD(연속 통합/연속 배포) 파이프라인을 빌드하는 방법을 보여 줍니다.

빌드 및 구성한 파이프라인은 DNS 서버와 관련 호스트 레코드를 완전하게 배포, 구성 및 테스트하는 데 사용할 수 있습니다.
이 프로세스에서는 개발 환경에서 사용되는 파이프라인의 첫 부분을 시뮬레이션합니다.

자동화된 CI/CD 파이프라인을 사용하면 소프트웨어를 보다 안정적이며 빠르게 업데이트할 수 있으며, 모든 코드를 테스트하고 코드의 최신 빌드를 항상 제공할 수 있습니다.

## <a name="prerequisites"></a>필수 구성 요소

이 예제를 사용하려면 다음에 대해 잘 알고 있어야 합니다.

- CI-CD 개념. [릴리스 파이프라인 모델](https://aka.ms/thereleasepipelinemodelpdf)에서 유용한 참조 정보를 확인할 수 있습니다.
- [Git](https://git-scm.com/) 소스 제어
- [Pester](https://github.com/pester/Pester) 테스트 프레임워크
- [Team Foundation Server](https://visualstudio.microsoft.com/tfs/)

## <a name="what-you-will-need"></a>필요한 사항

이 예제를 빌드하고 실행하려면 여러 컴퓨터 및/또는 가상 컴퓨터가 포함된 환경이 필요합니다.

### <a name="client"></a>Client

예제를 설정하고 실행하는 모든 작업을 수행할 컴퓨터입니다.

클라이언트 컴퓨터는 다음 항목이 설치된 Windows 컴퓨터여야 합니다.

- [Git](https://git-scm.com/)
- [https://github.com/PowerShell/Demo_CI](https://github.com/PowerShell/Demo_CI )에서 복제된 로컬 Git 리포지토리
- [Visual Studio Code](https://code.visualstudio.com/)와 같은 텍스트 편집기

### <a name="tfssrv1"></a>TFSSrv1

빌드와 릴리스를 정의할 TFS 서버를 호스트하는 컴퓨터입니다.
이 컴퓨터에는 [Team Foundation Server 2017](https://visualstudio.microsoft.com/tfs/)이 설치되어 있어야 합니다.

### <a name="buildagent"></a>BuildAgent

프로젝트를 빌드하는 Windows 빌드 에이전트를 실행할 컴퓨터입니다.
이 컴퓨터에는 빌드 에이전트가 설치되어 있으며 실행 중이어야 합니다.
Windows 빌드 에이전트를 설치하고 실행하는 방법에 대한 지침은 [Windows에서 에이전트 배포](/azure/devops/pipelines/agents/v2-windows)를 참조하세요.

또한 이 컴퓨터에는 `xDnsServer` 및 `xNetworking` DSC 모듈을 둘 다 설치해야 합니다.

### <a name="testagent1"></a>TestAgent1

이 예제에서 DSC 구성을 통해 DNS 서버로 구성하는 컴퓨터입니다.
이 컴퓨터에서는 [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016)을 실행해야 합니다.

### <a name="testagent2"></a>TestAgent2

이 예제에서 구성하는 웹 사이트를 호스트하는 컴퓨터입니다.
이 컴퓨터에서는 [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016)을 실행해야 합니다.

## <a name="add-the-code-to-tfs"></a>TFS에 코드 추가

먼저 TFS에서 Git 리포지토리를 만들고 클라이언트 컴퓨터의 로컬 리포지토리에서 코드를 가져옵니다.
클라이언트 컴퓨터에 Demo_CI 리포지토리를 아직 복제하지 않은 경우 다음 git 명령을 실행하여 지금 복제합니다.

`git clone https://github.com/PowerShell/Demo_CI`

1. 클라이언트 컴퓨터의 웹 브라우저에서 TFS 서버로 이동합니다.
1. TFS에서 Demo_CI라는 [새 팀 프로젝트를 만듭니다](/azure/devops/organizations/projects/create-project).

   **버전 제어**가 **Git**으로 설정되어 있는지 확인합니다.
1. 클라이언트 컴퓨터에서 다음 명령을 사용하여 방금 TFS에서 만든 리포지토리에 remote를 추가합니다.

   `git remote add tfs <YourTFSRepoURL>`

   여기서 `<YourTFSRepoURL>`은 이전 단계에서 만든 TFS 리포지토리의 복제 URL입니다.

   이 URL을 확인할 수 있는 위치를 모르는 경우 [기존 Git 리포지토리 복제](/azure/devops/repos/git/clone)를 참조하세요.
1. 다음 명령을 사용하여 로컬 리포지토리의 코드를 TFS 리포지토리로 푸시합니다.

   `git push tfs --all`
1. TFS 리포지토리에 Demo_CI 코드가 채워집니다.

> [!NOTE]
> 이 예제에서는 Git 리포지토리의 `ci-cd-example` 분기에 있는 코드를 사용합니다.
> TFS 프로젝트에서, 그리고 작성하는 CI/CD 트리거에 대해 이 분기를 기본 분기로 지정해야 합니다.

## <a name="understanding-the-code"></a>코드 파악

빌드 및 배포 파이프라인을 만들기 전에 몇 가지 코드를 확인하여 수행되는 작업을 파악해 보겠습니다.
클라이언트 컴퓨터에서 자주 사용하는 텍스트 편집기를 열고 Demo_CI Git 리포지토리의 루트로 이동합니다.

### <a name="the-dsc-configuration"></a>DSC 구성

로컬 Demo_CI 리포지토리의 루트에서 `DNSServer.ps1` 파일을 엽니다(`./InfraDNS/Configs/DNSServer.ps1`).

이 파일에는 DNS 서버를 설정하는 DSC 구성이 포함되어 있습니다. 전체 구성은 다음과 같습니다.

```powershell
configuration DNSServer
{
    Import-DscResource -module 'xDnsServer','xNetworking', 'PSDesiredStateConfiguration'

    Node $AllNodes.Where{$_.Role -eq 'DNSServer'}.NodeName
    {
        WindowsFeature DNS
        {
            Ensure  = 'Present'
            Name    = 'DNS'
        }

        xDnsServerPrimaryZone $Node.zone
        {
            Ensure    = 'Present'
            Name      = $Node.Zone
            DependsOn = '[WindowsFeature]DNS'
        }

        foreach ($ARec in $Node.ARecords.keys) {
            xDnsRecord $ARec
            {
                Ensure    = 'Present'
                Name      = $ARec
                Zone      = $Node.Zone
                Type      = 'ARecord'
                Target    = $Node.ARecords[$ARec]
                DependsOn = '[WindowsFeature]DNS'
            }
        }

        foreach ($CName in $Node.CNameRecords.keys) {
            xDnsRecord $CName
            {
                Ensure    = 'Present'
                Name      = $CName
                Zone      = $Node.Zone
                Type      = 'CName'
                Target    = $Node.CNameRecords[$CName]
                DependsOn = '[WindowsFeature]DNS'
            }
        }
    }
}
```

아래의 `Node` 문을 살펴보세요.

```powershell
Node $AllNodes.Where{$_.Role -eq 'DNSServer'}.NodeName
```

이 문은 `DevEnv.ps1` 스크립트를 통해 작성되는 [구성 데이터](../configurations/configData.md)에서 역할이 `DNSServer`로 정의된 노드를 찾습니다.

[about_arrays](/powershell/module/microsoft.powershell.core/about/about_arrays)의 `Where` 메서드에 대해 자세히 알아볼 수 있습니다.

CI 수행 시에는 구성 데이터를 사용하여 노드를 정의해야 합니다. 노드 정보는 환경 간에 변경될 가능성이 높은데, 구성 데이터를 사용하면 구성 코드를 변경하지 않고도 노드 정보를 쉽게 변경할 수 있기 때문입니다.

첫 번째 리소스 블록에서 구성은 **WindowsFeature**를 호출하여 DNS 기능이 사용하도록 설정되어 있는지 확인합니다.
그 다음 리소스 블록은 [xDnsServer](https://github.com/PowerShell/xDnsServer) 모듈의 리소스를 호출하여 주 영역 및 DNS 레코드를 구성합니다.

두 `xDnsRecord` 블록은 구성 데이터의 배열에서 반복되는 `foreach` 루프에 래핑됩니다.
이 구성 데이터 역시 `DevEnv.ps1` 스크립트를 통해 작성됩니다. 다음으로는 구성 데이터에 대해 살펴보겠습니다.

### <a name="configuration-data"></a>구성 데이터

로컬 Demo_CI 리포지토리의 `DevEnv.ps1` 파일(`./InfraDNS/DevEnv.ps1`)은 해시 테이블에서 환경별 구성 데이터를 지정한 다음 `DscPipelineTools.psm`(`./Assets/DscPipelineTools/DscPipelineTools.psm1`)에 정의된 `New-DscConfigurationDataDocument` 함수 호출로 해당 해시 테이블을 전달합니다.

`DevEnv.ps1` 파일은 다음과 같습니다.

```powershell
param(
    [parameter(Mandatory=$true)]
    [string]
    $OutputPath
)

Import-Module $PSScriptRoot\..\Assets\DscPipelineTools\DscPipelineTools.psd1 -Force

# Define Unit Test Environment
$DevEnvironment = @{
    Name                        = 'DevEnv';
    Roles = @(
        @{  Role                = 'DNSServer';
            VMName              = 'TestAgent1';
            Zone                = 'Contoso.com';
            ARecords            = @{'TFSSrv1'= '10.0.0.10';'Client'='10.0.0.15';'BuildAgent'='10.0.0.30';'TestAgent1'='10.0.0.40';'TestAgent2'='10.0.0.50'};
            CNameRecords        = @{'DNS' = 'TestAgent1.contoso.com'};
        }
    )
}

Return New-DscConfigurationDataDocument -RawEnvData $DevEnvironment -OutputPath $OutputPath
```

`\Assets\DscPipelineTools\DscPipelineTools.psm1`에 정의된 `New-DscConfigurationDataDocument` 함수는 `RawEnvData` 및 `OtherEnvData` 매개 변수로 전달되는 해시 테이블(노드 데이터) 및 배열(비노드 데이터)에서 구성 데이터 문서를 프로그래밍 방식으로 작성합니다.

이 예제에서는 `RawEnvData` 매개 변수만 사용합니다.

### <a name="the-psake-build-script"></a>psake 빌드 스크립트

Demo_CI 리포지토리 루트(`./InfraDNS/Build.ps1`)의 `Build.ps1`에 정의된 [psake](https://github.com/psake/psake) 빌드 스크립트는 빌드의 일부분인 작업을 정의합니다.
또한 각 작업이 사용하는 다른 작업도 정의합니다.
psake 스크립트는 호출 시 지정된 작업(작업이 지정되지 않은 경우 이름이 `Default`인 작업)이 실행되는지와 모든 종속성도 실행되는지를 확인합니다. 즉, 재귀적인 방식으로 종속성, 종속성의 종속성 등이 모두 실행되는지를 순차적으로 확인합니다.

이 예제에서 `Default` 작업은 다음과 같이 정의됩니다.

```powershell
Task Default -depends UnitTests
```

`Default` 작업 자체의 구현은 없으며 `CompileConfigs` 작업에 대한 종속성만 포함되어 있습니다.
작업 종속성의 결과 체인은 빌드 스크립트의 모든 작업이 실행되는지 확인합니다.

이 예제에서는 Demo_CI 리포지토리의 루트에 있는 `Initiate.ps1` 파일에서 `Invoke-PSake`를 호출하여 psake 스크립트를 호출합니다.

```powershell
param(
    [parameter()]
    [ValidateSet('Build','Deploy')]
    [string]
    $fileName
)

#$Error.Clear()

Invoke-PSake $PSScriptRoot\InfraDNS\$fileName.ps1

<#if($Error.count)
{
    Throw "$fileName script failed. Check logs for failure details."
}
#>
```

TFS에서 예제용 빌드 정의를 작성할 때 이 스크립트의 `fileName` 매개 변수로 psake 스크립트 파일을 제공할 것입니다.

빌드 스크립트는 다음과 같은 작업을 정의합니다.

#### <a name="generateenvironmentfiles"></a>GenerateEnvironmentFiles

구성 데이터 파일을 생성하는 `DevEnv.ps1`을 실행합니다.

#### <a name="installmodules"></a>InstallModules

구성 `DNSServer.ps1`에 필요한 모듈을 설치합니다.

#### <a name="scriptanalysis"></a>ScriptAnalysis

[PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer)를 호출합니다.

#### <a name="unittests"></a>UnitTests

[Pester](https://github.com/pester/Pester/wiki) 단위 테스트를 실행합니다.

#### <a name="compileconfigs"></a>CompileConfigs

`GenerateEnvironmentFiles` 작업을 통해 생성된 구성 데이터를 사용하여 구성(`DNSServer.ps1`)을 MOF 파일로 컴파일합니다.

#### <a name="clean"></a>정리

예제에 사용되는 폴더를 만들고 이전 실행의 테스트 결과, 구성 데이터 파일 및 모듈을 제거합니다.

### <a name="the-psake-deploy-script"></a>psake 배포 스크립트

Demo_CI 리포지토리 루트(`./InfraDNS/Deploy.ps1`)의 `Deploy.ps1`에 정의된 [psake](https://github.com/psake/psake) 배포 스크립트는 구성을 배포하고 실행하는 작업을 정의합니다.

`Deploy.ps1`은 다음 작업을 정의합니다.

#### <a name="deploymodules"></a>DeployModules

`TestAgent1`에서 PowerShell 세션을 시작하고 구성에 필요한 DSC 리소스가 포함된 모듈을 설치합니다.

#### <a name="deployconfigs"></a>DeployConfigs

[Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet을 호출하여 `TestAgent1`에서 구성을 실행합니다.

#### <a name="integrationtests"></a>IntegrationTests

[Pester](https://github.com/pester/Pester/wiki) 통합 테스트를 실행합니다.

#### <a name="acceptancetests"></a>AcceptanceTests

[Pester](https://github.com/pester/Pester/wiki) 수용 테스트를 실행합니다.

#### <a name="clean"></a>정리

이전 실행에서 설치된 모듈을 제거하고 테스트 결과 폴더가 있는지 확인합니다.

### <a name="test-scripts"></a>테스트 스크립트

수용, 통합 및 단위 테스트는 Demo_CI 리포지토리 루트의 `Tests` 폴더(`./InfraDNS/Tests`)에서 정의되며 각각 해당 폴더의 `DNSServer.tests.ps1` 파일에 포함되어 있습니다.

테스트 스크립트는 [Pester](https://github.com/pester/Pester/wiki) 및 [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) 구문을 사용합니다.

#### <a name="unit-tests"></a>단위 테스트

단위 테스트에서는 DSC 구성 자체를 테스트하여 구성을 실행하면 필요한 작업이 수행되는지를 확인합니다.
단위 테스트 스크립트는 [Pester](https://github.com/pester/Pester/wiki)를 사용합니다.

#### <a name="integration-tests"></a>통합 테스트

통합 테스트에서는 시스템 구성을 테스트하여 다른 구성 요소와 통합하는 경우 시스템이 올바르게 구성되는지를 확인합니다. 이러한 테스트는 DSC를 통해 구성된 대상 노드에서 실행됩니다.
통합 테스트 스크립트는 [Pester](https://github.com/pester/Pester/wiki) 및 [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) 구문을 함께 사용합니다.

#### <a name="acceptance-tests"></a>수용 테스트

수용 테스트에서는 시스템을 테스트하여 정상적으로 동작하는지를 확인합니다.
예를 들어 웹 페이지 쿼리 시 올바른 정보가 반환되는지를 테스트하여 확인합니다.
이러한 테스트는 실제 시나리오를 테스트하기 위해 대상 노드에서 원격으로 실행됩니다.
통합 테스트 스크립트는 [Pester](https://github.com/pester/Pester/wiki) 및 [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) 구문을 함께 사용합니다.

## <a name="define-the-build"></a>빌드 정의

지금까지 코드를 TFS에 업로드하고 코드가 수행하는 작업을 살펴보았습니다. 그러면 이제 빌드를 정의해 보겠습니다.

여기서는 빌드에 추가할 빌드 단계에 대해서만 설명합니다. TFS에서 빌드 정의를 작성하는 방법에 대한 지침은 [빌드 정의 만들기 및 큐에 넣기](/azure/devops/pipelines/create-first-pipeline)를 참조하세요.

**빈** 템플릿을 선택하여 새 빌드 정의 "InfraDNS"를 만들고
빌드 정의에 다음 단계를 추가합니다.

- PowerShell 스크립트
- 테스트 결과 게시
- 파일 복사
- 아티팩트 게시

이러한 빌드 단계를 추가한 후에 다음과 같이 각 단계의 속성을 편집합니다.

### <a name="powershell-script"></a>PowerShell 스크립트

1. **형식** 속성을 `File Path`로 설정합니다.
1. **스크립트 경로** 속성을 `initiate.ps1`로 설정합니다.
1. `-fileName build`를 **인수** 속성에 추가합니다.

이 빌드 단계는 psake 빌드 스크립트를 호출하는 `initiate.ps1` 파일을 실행합니다.

### <a name="publish-test-results"></a>테스트 결과 게시

1. **테스트 결과 형식**을 `NUnit`으로 설정합니다.
1. **테스트 결과 파일**을 `InfraDNS/Tests/Results/*.xml`로 설정합니다.
1. **테스트 실행 제목**을 `Unit`으로 설정합니다.
1. **제어 옵션** **사용** 및 **항상 실행**이 둘 다 선택되어 있는지 확인합니다.

이 빌드 단계는 앞에서 살펴본 Pester 스크립트에서 단위 테스트를 실행하고 결과를 `InfraDNS/Tests/Results/*.xml` 폴더에 저장합니다.

### <a name="copy-files"></a>파일 복사

1. 다음 각 줄을 **내용**에 추가합니다.

   ```
   initiate.ps1
   **\deploy.ps1
   **\Acceptance\**
   **\Integration\**
   ```

1. **TargetFolder**를 `$(Build.ArtifactStagingDirectory)\`로 설정합니다.

이 단계는 다음 단계에서 빌드 아티팩트로 게시할 수 있도록 빌드 및 테스트 스크립트를 스테이징 디렉터리에 복사합니다.

### <a name="publish-artifact"></a>아티팩트 게시

1. **게시할 경로**를 `$(Build.ArtifactStagingDirectory)\`로 설정합니다.
1. **아티팩트 이름**을 `Deploy`로 설정합니다.
1. **아티팩트 형식**을 `Server`로 설정합니다.
1. **제어 옵션**에서 `Enabled`를 선택합니다.

## <a name="enable-continuous-integration"></a>연속 통합을 사용하도록 설정

이제 git 리포지토리의 `ci-cd-example` 분기에 변경 내용을 체크 인할 때마다 프로젝트가 빌드되도록 하는 트리거를 설정하겠습니다.

1. TFS에서 **빌드 및 릴리스** 탭을 클릭합니다.
1. `DNS Infra` 빌드 정의를 선택하고 **편집**을 클릭합니다.
1. **트리거** 탭을 클릭합니다.
1. **연속 통합(CI)** 을 선택하고 분기 드롭다운 목록에서 `refs/heads/ci-cd-example`을 선택합니다.
1. **저장**, **확인**을 차례로 클릭합니다.

이제 TFS git 리포지토리에서 변경을 수행하면 자동화된 빌드가 트리거됩니다.

## <a name="create-the-release-definition"></a>릴리스 정의 만들기

다음으로는 코드를 체크 인할 때마다 개발 환경에 프로젝트가 배포되도록 릴리스 정의를 만들어 보겠습니다.

이렇게 하려면 앞에서 만든 `InfraDNS` 빌드 정의와 연결된 새 릴리스 정의를 추가합니다.
새 빌드를 완료할 때마다 새 릴리스가 트리거되도록 **연속 배포**를 선택해야 합니다.
해당 방법은 [릴리스 파이프라인이란?](/azure/devops/pipelines/release/)을 참조하세요. 다음과 같이 새 릴리스 정의를 구성합니다.

릴리스 정의에 다음 단계를 추가합니다.

- PowerShell 스크립트
- 테스트 결과 게시
- 테스트 결과 게시

다음과 같이 단계를 편집합니다.

### <a name="powershell-script"></a>PowerShell 스크립트

1. **스크립트 경로** 필드를 `$(Build.DefinitionName)\Deploy\initiate.ps1"`로 설정합니다.
1. **인수** 필드를 `-fileName Deploy`로 설정합니다.

### <a name="first-publish-test-results"></a>테스트 결과 첫 번째 게시

1. **테스트 결과 형식** 필드에서 `NUnit`을 선택합니다.
1. **테스트 결과 파일** 필드를 `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Integration*.xml`로 설정합니다.
1. **테스트 실행 제목**을 `Integration`로 설정합니다.
1. **제어 옵션**에서 **항상 실행**을 선택합니다.

### <a name="second-publish-test-results"></a>테스트 결과 두 번째 게시

1. **테스트 결과 형식** 필드에서 `NUnit`을 선택합니다.
1. **테스트 결과 파일** 필드를 `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Acceptance*.xml`로 설정합니다.
1. **테스트 실행 제목**을 `Acceptance`로 설정합니다.
1. **제어 옵션**에서 **항상 실행**을 선택합니다.

## <a name="verify-your-results"></a>결과 확인

이제 `ci-cd-example` 분기에서 TFS에 변경 내용을 푸시할 때마다 새 빌드가 시작됩니다.
빌드가 정상적으로 완료되면 새 배포가 트리거됩니다.

클라이언트 컴퓨터에서 브라우저를 열고 `www.contoso.com`으로 이동하면 배포 결과를 확인할 수 있습니다.

## <a name="next-steps"></a>다음 단계

이 예제에서는 `www.contoso.com` URL이 `TestAgent2`로 확인되도록 DNS 서버 `TestAgent1`을 구성하지만 웹 사이트가 실제로 배포되지는 않습니다.
웹 사이트 배포를 위한 코드 구조는 리포지토리의 `WebApp` 폴더에서 제공됩니다.
제공된 스텁을 사용하여 psake 스크립트, Pester 테스트 및 DSC 구성을 만들어서 웹 사이트를 직접 배포할 수 있습니다.
