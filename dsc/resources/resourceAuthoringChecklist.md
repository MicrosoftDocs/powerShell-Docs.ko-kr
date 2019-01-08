---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: 리소스 작성 검사 목록
ms.openlocfilehash: 7b1a096bba1b729c096b6689178ee022e12e4634
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402732"
---
# <a name="resource-authoring-checklist"></a>리소스 작성 검사 목록

이 검사 목록은 새 DSC 리소스를 작성할 때 따를 모범 사례 목록입니다.

## <a name="resource-module-contains-psd1-file-and-schemamof-for-every-resource"></a>리소스 모듈에 모든 리소스에 대한 .psd1 파일과 schema.mof가 포함되어 있음

리소스가 올바른 구조이고 필요한 파일을 모두 포함하는지 확인합니다. 모든 리소스 모듈에 .psd1 파일이 포함되어 있고 모든 비복합 리소스에 schema.mof 파일이 있어야 합니다. 스키마가 포함되지 않은 리소스는 `Get-DscResource`로 나열되지 않고 사용자는 ISE에서 해당 모듈에 대해 코드를 작성할 때 intellisense를 사용할 수 없습니다.
[xPSDesiredStateConfiguration 리소스 모듈](https://github.com/PowerShell/xPSDesiredStateConfiguration)의 일부인 xRemoteFile 리소스에 대한 디렉터리 구조는 다음과 같이 표시됩니다.

```
xPSDesiredStateConfiguration
    DSCResources
        MSFT_xRemoteFile
            MSFT_xRemoteFile.psm1
            MSFT_xRemoteFile.schema.mof
    Examples
        xRemoteFile_DownloadFile.ps1
    ResourceDesignerScripts
        GenerateXRemoteFileSchema.ps1
    Tests
        ResourceDesignerTests.ps1
    xPSDesiredStateConfiguration.psd1
```

## <a name="resource-and-schema-are-correct"></a>리소스 및 스키마가 올바름

리소스 스키마(*.schema.mof) 파일을 확인합니다. [DSC Resource Designer](https://www.powershellgallery.com/packages/xDSCResourceDesigner/1.12.0.0)(DSC 리소스 디자이너)를 사용하여 스키마를 개발하고 테스트할 수 있습니다.
다음 사항을 확인하세요.

- 속성 형식이 올바릅니다. 예를 들어 숫자 값을 허용하는 속성에 문자열을 사용하지 마세요. 대신 UInt32나 다른 숫자 형식을 사용해야 합니다.
- 속성 특성이 다음과 같이 올바르게 지정되었습니다([key], [required], [write], [read]).
- 스키마에서 하나 이상의 매개 변수가 [key]로 표시되어야 합니다.
- [read] 속성은 [required], [key], [write] 중 하나와 함께 사용할 수 없습니다.
- [read]를 제외한 여러 한정자가 지정된 경우 [key]가 우선적으로 적용됩니다.
- [write] 및 [required]가 지정된 경우 [required]가 우선적으로 적용됩니다.
- ValueMap이 적절하게 지정되었습니다. 예:

  ```
  [Read, ValueMap{"Present", "Absent"}, Values{"Present", "Absent"}, Description("Says whether DestinationPath exists on the machine")] String Ensure;
  ```

- 식별 이름이 지정되고 DSC 명명 규칙을 준수합니다.

  예: `[ClassVersion("1.0.0.0"), FriendlyName("xRemoteFile")]`

- 모든 필드에 의미 있는 설명이 있습니다. PowerShell GitHub 리포지토리에는 [the .schema.mof for xRemoteFile](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCResources/MSFT_xRemoteFile/MSFT_xRemoteFile.schema.mof)(xRemoteFile용 .schema.mof)과 같은 좋은 예가 있습니다.

또한 [DSC Resource Designer](https://www.powershellgallery.com/packages/xDSCResourceDesigner/1.12.0.0)(DSC 리소스 디자이너)의 **Test-xDscResource** 및 **Test-xDscSchema** cmdlet을 사용하여 리소스 및 스키마를 자동으로 확인해야 합니다.

```
Test-xDscResource <Resource_folder>
Test-xDscSchema <Path_to_resource_schema_file>
```

예:

```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof
```

## <a name="resource-loads-without-errors"></a>리소스가 오류 없이 로드됨

리소스 모듈을 로드할 수 있는지 확인합니다.
이 작업은 `Import-Module <resource_module> -force`을 실행하고 오류가 발생하지 않는지 확인하거나, 테스트 자동화를 작성하여 수동으로 수행할 수 있습니다. 후자의 경우 테스트 사례에서 다음 구조를 따를 수 있습니다.

```powershell
$error = $null
Import-Module <resource_module> –force
If ($error.count –ne 0) {
    Throw “Module was not imported correctly. Errors returned: $error”
}
```

## <a name="resource-is-idempotent-in-the-positive-case"></a>리소스가 양성 사례에서 idempotent임

DSC 리소스의 기본 특성 중 하나는 idempotence입니다. 즉, 해당 리소스를 포함하는 DSC 구성을 여러 번 적용하면 항상 같은 결과가 나옵니다. 예를 들면 다음과 같은 파일 리소스를 포함하는 구성을 만드는 경우입니다.

```powershell
File file {
    DestinationPath = "C:\test\test.txt"
    Contents = "Sample text"
}
```

처음으로 적용한 후 test.txt 파일이 `C:\test` 폴더에 나타나야 합니다. 그러나 동일한 구성의 후속 실행에서도 컴퓨터의 상태는 변경되지 않아야 합니다. 예를 들어 `test.txt` 파일의 복사본이 만들어지지 않아야 합니다.
리소스가 idempotent인지 확인하려면 리소스를 직접 테스트할 때 `Set-TargetResource`를 반복적으로 호출하거나 종단 간 테스트를 수행할 때 `Start-DscConfiguration`을 여러 번 호출할 수 있습니다. 결과는 모든 실행 후에 동일해야 합니다.

## <a name="test-user-modification-scenario"></a>테스트 사용자 수정 시나리오

컴퓨터의 상태를 변경한 다음 DSC를 다시 실행하면 `Set-TargetResource` 및 `Test-TargetResource`가 올바르게 작동하는지 확인할 수 있습니다. 수행해야 하는 단계는 다음과 같습니다.

1. 원하는 상태가 아닌 리소스에서 시작합니다.
2. 리소스에서 구성을 실행합니다.
3. `Test-DscConfiguration`이 True를 반환하는지 확인
4. 구성된 항목이 원하는 상태에서 해제되도록 수정합니다.
5. `Test-DscConfiguration`이 false를 반환하는지 확인

다음은 레지스트리 키를 사용하는 보다 구체적인 예입니다.

1. 원하는 상태가 아닌 레지스트리 키에서 시작합니다.
2. 구성에서 `Start-DscConfiguration`을 실행하여 원하는 상태로 전환하고 통과하는지 확인합니다.
3. `Test-DscConfiguration`을 실행하고 true를 반환하는지 확인
4. 키의 값을 수정하여 원하는 상태가 되지 않도록 합니다.
5. `Test-DscConfiguration`을 실행하고 false를 반환하는지 확인
6. `Get-TargetResource` 기능을 `Get-DscConfiguration`을 사용하여 확인했습니다.

`Get-TargetResource`는 리소스의 현재 상태에 대한 세부 정보를 반환해야 합니다. 구성을 적용한 후 `Get-DscConfiguration`을 호출하고 출력에 컴퓨터의 현재 상태가 올바르게 반영되는지 확인하여 테스트해야 합니다. `Start-DscConfiguration`을 호출할 때 이 영역의 문제가 나타나지 않으므로 별도로 테스트해야 합니다.

## <a name="call-getsettest-targetresource-functions-directly"></a>**Get/Set/Test-TargetResource** 함수 직접 호출

리소스에 구현된 **Get/Set/Test-TargetResource** 함수를 직접 호출하고 예상대로 작동하는지 확인하여 이 함수를 테스트해야 합니다.

## <a name="verify-end-to-end-using-start-dscconfiguration"></a>**Start-DscConfiguration**을 사용하여 종단 간 확인

**Get/Set/Test-TargetResource** 함수를 직접 호출하여 테스트하는 것이 중요하지만 이런 방식으로 모든 문제가 검색되는 것은 아닙니다. `Start-DscConfiguration` 또는 끌어오기 서버 사용에 테스트의 초점을 맞추어야 합니다. 실제로 사용자가 리소스를 사용하는 방법이므로 이러한 테스트 유형의 중요성을 간과해서는 안 됩니다.
가능한 문제 유형:

- DSC 에이전트가 서비스로 실행되기 때문에 자격 증명/세션이 다르게 동작할 수 있습니다.  여기에서 모든 기능을 종단 간 테스트해야 합니다.
- `Start-DscConfiguration`에 의해 출력된 오류가 `Set-TargetResource` 함수를 직접 호출할 때 표시되는 오류와 다를 수 있습니다.

## <a name="test-compatability-on-all-dsc-supported-platforms"></a>모든 DSC 지원 플랫폼에서 호환성 테스트

리소스는 모든 DSC 지원 플랫폼(Windows Server 2008 R2 이상)에서 작동해야 합니다. 최신 버전의 DSC를 가져오려면 OS에 최신 WMF(Windows Management Framework)를 설치합니다. 리소스가 디자인에 따라 이러한 플랫폼 일부에서 작동하지 않을 경우 특정 오류 메시지가 반환되어야 합니다. 또한 호출하는 cmdlet이 특정 컴퓨터에 있는지 여부를 리소스에서 확인해야 합니다. Windows Server 2012에서는 Windows Server 2008 R2에서 WMF가 설치된 경우에도 제공하지 않는 많은 새로운 cmdlet이 추가되었습니다.

## <a name="verify-on-windows-client-if-applicable"></a>Windows 클라이언트에서 확인(해당되는 경우)

매우 일반적인 테스트 간격은 Windows의 서버 버전에서만 리소스를 확인하는 것입니다. 또한 많은 리소스가 클라이언트 SKU에서 작동하도록 설계되었으므로 해당되는 경우 해당 플랫폼에서도 테스트해야 합니다.

## <a name="get-dscresource-lists-the-resource"></a>Get-DSCResource에서 리소스를 나열함

모듈을 배포한 후 `Get-DscResource`를 호출하면 결과로 리소스를 나열해야 합니다. 목록에서 리소스를 찾을 수 없으면 해당 리소스에 대한 schema.mof 파일이 있는지 확인하세요.

## <a name="resource-module-contains-examples"></a>리소스 모듈에 예제가 포함되어 있음

다른 사용자가 사용 방법을 이해하는 데 도움이 되는 우수한 예제 만들기. 따라서 이 작업은 중요하며 특히 많은 사용자가 샘플 코드를 설명서로 처리하기 때문에 더욱 그렇습니다.

- 먼저 모듈에 포함될 예제를 결정해야 합니다. 최소한 리소스에 대한 가장 중요한 사용 사례를 포함해야 합니다.
- 종단 간 시나리오에서 함께 작동해야 하는 여러 가지 리소스가 모듈에 포함된 경우 기본적인 종단 간 예제가 첫 번째로 포함되는 것이 좋습니다.
- 초기 예제는 매우 간단해야 합니다. 즉, 관리할 수 있는 작은 청크(예: 새 VHD 만들기)로 리소스를 시작하는 방법이 될 수 있습니다.
- 이후 예제는 이 예제를 기반으로 해야 하며(예: VHD에서 VM 만들기, VM 제거, VM 수정) 고급 기능(예: 동적 메모리로 VM 만들기)을 보여 주어야 합니다.
- 예제 구성을 매개 변수화해야 합니다. 즉, 모든 값을 매개 변수로 구성에 전달해야 하며 하드 코드된 값이 없어야 합니다.

  ```powershell
  configuration Sample_xRemoteFile_DownloadFile
  {
    param
    (
        [string[]] $nodeName = 'localhost',

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String] $destinationPath,

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String] $uri,

        [String] $userAgent,

        [Hashtable] $headers
    )

    Import-DscResource -Name MSFT_xRemoteFile -ModuleName xPSDesiredStateConfiguration

    Node $nodeName
    {
        xRemoteFile DownloadFile
        {
            DestinationPath = $destinationPath
            Uri = $uri
            UserAgent = $userAgent
            Headers = $headers
        }
    }
  }
  ```

- 예제 스크립트의 끝에 실제 값으로 구성을 호출하는 방법에 대한 예제를 포함(주석으로 처리)하는 것이 좋습니다.
  예를 들어 위의 구성에서는 UserAgent를 지정하는 가장 좋은 방법이 다음과 같은지 확실하지 않습니다.

  `UserAgent = [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer` 이 경우 주석을 사용하여 구성의 올바른 실행을 명확히 설명할 수 있습니다.

  ```powershell
  <#
  Sample use (parameter values need to be changed according to your scenario):

  Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg"

  Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg" `
  -userAgent [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer -headers @{"Accept-Language" = "en-US"}
  #>
  ```

- 각 예제에 대해 용도, 매개 변수의 의미를 설명하는 간단한 설명을 작성합니다.
- 리소스에 가장 중요한 시나리오가 예제에 포함되었는지 확인하고 누락된 내용이 없을 경우 모두 실행되고 컴퓨터가 원하는 상태로 전환되는지 확인합니다.

## <a name="error-messages-are-easy-to-understand-and-help-users-solve-problems"></a>오류 메시지가 이해하기 쉽고 사용자가 문제를 해결하는 데 도움이 됨

좋은 오류 메시지는 다음과 같아야 합니다.

- 있습니다. 오류 메시지를 사용 하 여 가장 큰 문제는가는 종종 존재 하지 않는다는 해야 합니다.
- 이해 하기 쉽습니다. 더 모호한 사람이 읽을 수 있는 오류 코드
- 정확 무엇이 문제 정확 하 게 설명 합니다.
- 건설적인: 조언 문제를 해결 하는 방법
- 처리 완료 후: 사용자를 비난 하거나 잘못 된 것으로 생각 될 수 있도록 하지 마세요

리소스 함수를 직접 실행할 때 반환되는 오류와 다를 수 있으므로 종단 간 시나리오에서 `Start-DscConfiguration`을 사용하여 오류를 확인해야 합니다.

## <a name="log-messages-are-easy-to-understand-and-informative-including-verbose-debug-and-etw-logs"></a>로그 메시지는 이해하기 쉽고 정보를 제공해야 함(–verbose, –debug 및 ETW 로그 포함)

리소스에 의해 출력된 로그가 이해하기 쉽고 사용자에게 값을 제공하는지 확인합니다. 리소스는 사용자에게 도움이 될 수 있는 모든 정보를 출력해야 하지만 로그가 많을수록 항상 더 좋은 것은 아닙니다. 추가 값을 제공하지 않는 데이터의 출력 및 중복성을 방지해야 합니다. 즉, 원하는 항목을 찾기 위해 수백 개의 로그 항목을 검토하는 일이 없도록 해야 합니다. 물론 로그가 없는 것도 이 문제에 적합한 솔루션은 아닐 수 있습니다.

테스트할 때 ETW 로그뿐만 아니라 자세한 정보 로그 및 디버그 로그(`–Verbose` 및 `–Debug` 스위치를 적절히 사용하여 `Start-DscConfiguration` 실행)도 분석해야 합니다. DSC ETW 로그를 보려면 이벤트 뷰어로 이동 하 고 폴더를 엽니다. 응용 프로그램 및 서비스-Microsoft-Windows-Desired State Configuration.  기본적으로 작동 채널이 있지만 구성을 실행하기 전에 분석 및 디버그 채널을 사용하도록 설정해야 합니다.
분석/디버그 채널을 사용하려면 다음 스크립트를 실행할 수 있습니다.

```powershell
$statusEnabled = $true
# Use "Analytic" to enable Analytic channel
$eventLogFullName = "Microsoft-Windows-Dsc/Debug"
$commandToExecute = "wevtutil set-log $eventLogFullName /e:$statusEnabled /q:$statusEnabled   "
$log = New-Object System.Diagnostics.Eventing.Reader.EventLogConfiguration $eventLogFullName
if($statusEnabled -eq $log.IsEnabled)
{
    Write-Host -Verbose "The channel event log is already enabled"
    return
}
Invoke-Expression $commandToExecute
```

## <a name="resource-implementation-does-not-contain-hardcoded-paths"></a>리소스 구현에 하드 코드된 경로가 포함되지 않음

리소스 구현에 하드 코드된 경로가 없는지 확인합니다. 특히 언어(en-us)를 가정하거나 사용할 수 있는 시스템 변수가 있는 경우는 더욱 그렇습니다.
리소스에서 특정 경로에 액세스해야 하는 경우 다른 컴퓨터에서는 달라질 수 있으므로 경로를 하드코딩하는 대신 환경 변수를 사용하세요.

예:

다음 문자열 대신에

```powershell
$tempPath = "C:\Users\kkaczma\AppData\Local\Temp\MyResource"
$programFilesPath = "C:\Program Files (x86)"
```

다음과 같이 작성:

```powershell
$tempPath = Join-Path $env:temp "MyResource"
$programFilesPath = ${env:ProgramFiles(x86)}
```

## <a name="resource-implementation-does-not-contain-user-information"></a>리소스 구현에 사용자 정보가 포함되지 않음

코드에 메일 이름, 계정 정보 또는 사람 이름이 없는지 확인합니다.

## <a name="resource-was-tested-with-validinvalid-credentials"></a>리소스가 유효한/잘못된 자격 증명으로 테스트됨

리소스에서 자격 증명을 매개 변수로 사용하는 경우:

- 로컬 시스템(또는 원격 리소스에 대한 컴퓨터 계정)에 액세스 권한이 없는 경우에 리소스가 작동하는지 확인합니다.
- Get, Set 및 Test에 지정된 자격 증명에서 리소스가 작동하는지 확인합니다.
- 리소스에서 공유에 액세스하는 경우 지원해야 하는 다음과 같은 모든 변형을 테스트합니다.
  - 표준 Windows 공유
  - DFS 공유
  - SAMBA 공유(Linux를 지원하려는 경우)

## <a name="resource-does-not-require-interactive-input"></a>리소스에 대화형 입력이 필요하지 않음

**Get/Set/Test-TargetResource** 함수는 자동으로 실행되어야 하며 모든 실행 단계에서 사용자의 입력을 대기하지 않아야 합니다. 예를 들어 이러한 함수 내부에서 `Get-Credential`을 사용해서는 안 됩니다. 사용자의 입력을 제공해야 하는 경우 컴파일 단계 중 매개 변수로 구성에 전달해야 합니다.

## <a name="resource-functionality-was-thoroughly-tested"></a>리소스 기능이 철저하게 테스트됨

이 검사 목록에는 테스트해야 하거나 누락되는 경우가 많은 항목이 포함되어 있습니다. 다양한 테스트가 있을 수 있으며, 주로 테스트하고 있지만 여기에 언급되지 않은 리소스와 관련된 기능 테스트입니다. 부정적인 테스트 사례를 기억해 두어야 합니다.

## <a name="best-practice-resource-module-contains-tests-folder-with-resourcedesignertestsps1-script"></a>모범 사례 리소스 모듈에 ResourceDesignerTests.ps1 스크립트가 된 Tests 폴더가 포함 되어 있습니다.

리소스 모듈 내에 “Tests” 폴더를 만들고 `ResourceDesignerTests.ps1` 파일을 만든 다음 지정된 모듈의 모든 리소스에 대해 **Test-xDscResource** 및 **Test-xDscSchema**를 사용하여 테스트를 추가하는 것이 좋습니다.
이런 방식으로 지정된 모듈에서 모든 리소스의 스키마에 대해 신속하게 유효성을 검사하고 게시하기 전에 온전성 검사를 수행할 수 있습니다.
xRemoteFile의 경우 `ResourceTests.ps1`이 다음과 같이 간단하게 표시될 수 있습니다.

```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof
```

## <a name="best-practice-resource-folder-contains-resource-designer-script-for-generating-schema"></a>모범 사례 리소스 폴더에 스키마를 생성 하는 것에 대 한 리소스 디자이너 스크립트가

각 리소스에는 리소스의 mof 스키마를 생성하는 리소스 디자이너 스크립트가 있어야 합니다. 이 파일은 `<ResourceName>\ResourceDesignerScripts`에 저장되며 이름은 Generate `<ResourceName>Schema.ps1`로 지정됩니다. xRemoteFile 리소스의 경우 이 파일을 `GenerateXRemoteFileSchema.ps1`이라고 하며 다음을 포함합니다.

```powershell
$DestinationPath = New-xDscResourceProperty -Name DestinationPath -Type String -Attribute Key -Description 'Path under which downloaded or copied file should be accessible after operation.'
$Uri = New-xDscResourceProperty -Name Uri -Type String -Attribute Required -Description 'Uri of a file which should be copied or downloaded. This parameter supports HTTP and HTTPS values.'
$Headers = New-xDscResourceProperty -Name Headers -Type Hashtable[] -Attribute Write -Description 'Headers of the web request.'
$UserAgent = New-xDscResourceProperty -Name UserAgent -Type String -Attribute Write -Description 'User agent for the web request.'
$Ensure = New-xDscResourceProperty -Name Ensure -Type String -Attribute Read -ValidateSet "Present", "Absent" -Description 'Says whether DestinationPath exists on the machine'
$Credential = New-xDscResourceProperty -Name Credential -Type PSCredential -Attribute Write -Description 'Specifies a user account that has permission to send the request.'
$CertificateThumbprint = New-xDscResourceProperty -Name CertificateThumbprint -Type String -Attribute Write -Description 'Digital public key certificate that is used to send the request.'

New-xDscResource -Name MSFT_xRemoteFile -Property @($DestinationPath, $Uri, $Headers, $UserAgent, $Ensure, $Credential, $CertificateThumbprint) -ModuleName xPSDesiredStateConfiguration2 -FriendlyName xRemoteFile
```

## <a name="best-practice-resource-supports--whatif"></a>모범 사례 리소스에서-whatif를 지원함

리소스에서 “위험한” 작업을 수행하고 있는 경우 `-WhatIf` 기능을 구현하는 것이 좋습니다. 완료된 후에는 명령이 `-WhatIf` 스위치 없이 실행된 경우 수행된 작업에 대해 `-WhatIf` 출력이 올바르게 설명하는지 확인합니다.
또한 `–WhatIf` 스위치가 있으면 작업이 실행되지 않고 노드의 상태가 변경되지 않는지 확인합니다.
예를 들어 파일 리소스를 테스트한다고 가정해 보겠습니다. 다음은 "test" 콘텐츠로 `test.txt` 파일을 만드는 간단한 구성입니다.

```powershell
configuration config
{
    node localhost
    {
        File file
        {
            Contents="test"
            DestinationPath="C:\test\test.txt"
        }
    }
}
config
```

`-WhatIf` 스위치를 사용하여 구성을 컴파일한 다음 실행하면 출력에서 구성을 실행할 때 수행된 작업을 정확하게 알려줍니다. 그러나 구성 자체는 실행되지 않았습니다. `test.txt` 파일이 생성되지 않았습니다.

```powershell
Start-DscConfiguration -Path .\config -ComputerName localhost -Wait -Verbose -WhatIf
```

```output
VERBOSE: Perform operation 'Invoke CimMethod' with following parameters, ''methodName' =
SendConfigurationApply,'className' = MSFT_DSCLocalConfigurationManager,'namespaceName' =
root/Microsoft/Windows/DesiredStateConfiguration'.
VERBOSE: An LCM method call arrived from computer CHARLESX1 with user sid
S-1-5-21-397955417-626881126-188441444-5179871.
What if: [X]: LCM:  [ Start  Set      ]
What if: [X]: LCM:  [ Start  Resource ]  [[File]file]
What if: [X]: LCM:  [ Start  Test     ]  [[File]file]
What if: [X]:                            [[File]file] The system cannot find the file specified.
What if: [X]:                            [[File]file] The related file/directory is: C:\test\test.txt.
What if: [X]: LCM:  [ End    Test     ]  [[File]file]  in 0.0270 seconds.
What if: [X]: LCM:  [ Start  Set      ]  [[File]file]
What if: [X]:                            [[File]file] The system cannot find the file specified.
What if: [X]:                            [[File]file] The related file/directory is: C:\test\test.txt.
What if: [X]:                            [C:\test\test.txt] Creating and writing contents and setting attributes.
What if: [X]: LCM:  [ End    Set      ]  [[File]file]  in 0.0180 seconds.
What if: [X]: LCM:  [ End    Resource ]  [[File]file]
What if: [X]: LCM:  [ End    Set      ]
VERBOSE: [X]: LCM:  [ End    Set      ]    in  0.1050 seconds.
VERBOSE: Operation 'Invoke CimMethod' complete.
```

이 목록은 완벽하지는 않지만 DSC 리소스를 디자인, 개발 및 테스트하는 동안 발생할 수 있는 여러 가지 중요한 문제를 다루고 있습니다.
