---
ms.date: 01/08/2020
keywords: dsc,powershell,configuration,setup
title: DSC 끌어오기 서비스
ms.openlocfilehash: d71c87e0420a0ee54eca36f1792b43103431233f
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75870815"
---
# <a name="desired-state-configuration-pull-service"></a>원하는 상태 구성 끌어오기 서비스

> [!IMPORTANT]
> 끌어오기 서버(Windows 기능 *DSC-Service*)는 Windows Server의 지원되는 구성 요소이지만 새로운 기능을 제공할 계획은 없습니다. 관리되는 클라우드를 [Azure Automation DSC](/azure/automation/automation-dsc-getting-started)(Windows Server에 끌어오기 서버 이외의 기능 포함) 또는 [여기](pullserver.md#community-solutions-for-pull-service)에 나열된 커뮤니티 솔루션 중 하나로 전환하기 시작하는 것이 좋습니다.

끌어오기 서비스 솔루션을 사용하여 LCM(로컬 구성 관리자)을 중앙 집중식으로 관리할 수 있습니다. 이러한 접근 방법을 사용할 경우 관리되는 노드가 서비스에 등록되고, 해당 노드에 LCM 설정의 구성이 할당됩니다. 구성과 해당 구성에 대한 종속성으로 필요한 모든 DSC 리소스가 컴퓨터에 다운로드되고 LCM에서 구성을 관리하는 데 사용됩니다. 관리하는 컴퓨터의 상태에 대한 정보는 보고를 위해 서비스에 업로드됩니다. 이 개념을 "끌어오기 서비스"라고 합니다.

풀 서비스에 대한 현재 옵션은 다음과 같습니다.

- Azure Automation 필요한 상태 구성 서비스
- Windows Server에서 실행되는 끌어오기 서비스
- 커뮤니티에서 유지 관리하는 오픈 소스 솔루션
- SMB 공유

**권장 솔루션**이며, 대부분의 기능에서 사용 가능한 옵션은 [Azure Automation DSC](/azure/automation/automation-dsc-getting-started)입니다.

Azure 서비스는 개인 데이터 센터의 온-프레미스에 있는 노드를 관리하거나 Azure와 AWS 같은 퍼블릭 클라우드에 있는 노드를 관리할 수 있습니다. 서버를 인터넷에 직접 연결할 수 없는 개인 환경의 경우, 아웃바운드 트래픽을 게시된 Azure IP 범위로만 제한하세요([Azure Datacenter IP Ranges](https://www.microsoft.com/download/details.aspx?id=41653)(Azure 데이터 센터 IP 범위) 참조).

Windows Server의 풀 서비스에서 현재 사용할 수 없는 온라인 서비스의 기능은 다음과 같습니다.

- 전송 중 및 미사용 중인 모든 데이터 암호화
- 클라이언트 인증서 자동 생성 및 관리
- [암호/자격 증명](/azure/automation/automation-credentials) 또는 서버 이름이나 연결 문자열 같은[변수](/azure/automation/automation-variables)를 중앙에서 관리하기 위한 비밀 저장소
- [LCM 구성](../managing-nodes/metaConfig.md#basic-settings) 노드를 중앙에서 관리
- 중앙에서 클라이언트 노드에 구성 할당
- 프로덕션으로 전환하기 전에 테스트를 위해 “카나리아 그룹”에 구성 변경 내용 릴리스
- 그래픽 보고
  - DSC 리소스 수준 단위에서 상태 세부 정보
  - 문제 해결을 위해 클라이언트 시스템의 상세 오류 메시지
- 경고, 자동화된 작업, 보고 및 경고용 Android/iOS 앱에 대해 [Azure Log Analytics와 통합](/azure/automation/automation-dsc-diagnostics)

## <a name="dsc-pull-service-in-windows-server"></a>Windows Server의 DSC 끌어오기 서비스

Windows Server에서 실행할 끌어오기 서비스를 구성할 수 있습니다. Windows Server에 포함된 끌어오기 서비스 솔루션에는 다운로드할 구성/모듈을 저장하고 보고서 데이터를 데이터베이스에 캡처하는 기능한 포함되어 있다는 사실을 알아두세요. Azure의 서비스에서 제공하는 다양한 기능은 포함되어 있지 않으므로 서비스가 사용되는 방식을 평가하기에 좋은 도구는 아닙니다.

Windows Server에서 제공되는 끌어오기 서버는 해당 노드에서 요청하면 OData 인터페이스를 사용하여 DSC 구성 파일을 대상 노드에 사용할 수 있도록 하는 IIS의 웹 서비스입니다.

끌어오기 서버 사용을 위한 요구 사항:

- 다음 항목을 실행 중인 서버:
  - WMF/PowerShell 4.0 이상
  - IIS 서버 역할
  - DSC 서비스
- 인증서를 생성하여 대상 노드에서 LCM(로컬 구성 관리자)에 전달된 자격 증명을 보호할 방법이 있으면 가장 좋습니다.

가져오기 서비스를 호스트하도록 Windows Server를 구성하는 가장 좋은 방법은 DSC 구성을 사용하는 것입니다. 예제 스크립트는 아래에 제공됩니다.

### <a name="supported-database-systems"></a>지원되는 데이터베이스 시스템

| WMF 4.0 |       WMF 5.0        |       WMF 5.1        | WMF 5.1(Windows Server Insider Preview 17090) |
| ------- | -------------------- | -------------------- | ---------------------------------------------- |
| MDB     | ESENT(기본값), MDB | ESENT(기본값), MDB | ESENT(기본값), SQL Server, MDB               |

[Windows Server Insider Preview](https://www.microsoft.com/software-download/windowsinsiderpreviewserver) 17090 릴리스부터 SQL Server는 끌어오기 서비스(Windows 기능 *DSC-Service*)에 지원되는 옵션입니다. 이는 [Azure Automation DSC](/azure/automation/automation-dsc-getting-started)로 마이그레이션되지 않은 대규모 DSC 환경의 규모를 조정하기 위한 새로운 옵션을 제공합니다.

> [!NOTE]
> SQL Server 지원은 WMF 5.1(이하)의 이전 버전에 추가되지 않으며, Windows Server 17090 이상 버전에서만 제공됩니다.

SQL Server를 사용하도록 끌어오기 서버를 구성하려면 **SqlProvider**를 `$true`로, **SqlConnectionString**을 유효한 SQL Server 연결 문자열로 설정하세요. 자세한 내용은 [SqlClient 연결 문자열](/dotnet/framework/data/adonet/connection-string-syntax#sqlclient-connection-strings)을 참조하세요.
**xDscWebService**를 사용한 SQL Server 구성의 예를 보려면 먼저 [xDscWebService 리소스 사용](#using-the-xdscwebservice-resource)을 읽은 후 [GitHub의 Sample_xDscWebServiceRegistration_UseSQLProvider.ps1](https://github.com/dsccommunity/xPSDesiredStateConfiguration/blob/master/source/Examples/Sample_xDscWebServiceRegistration_UseSQLProvider.ps1)을 살펴보세요.

### <a name="using-the-xdscwebservice-resource"></a>xDscWebService 리소스 사용

웹 끌어오기 서버를 설정하는 가장 쉬운 방법은 **xPSDesiredStateConfiguration** 모듈에 포함된 **xDscWebService** 리소스를 사용하는 것입니다. 다음 단계에서는 웹 서비스를 설정하는 `Configuration`에서 리소스를 사용하는 방법에 대해 설명합니다.

1. [Install-Module](/reference/6/PowerShellGet/Install-Module.md) cmdlet을 호출하여 **xPSDesiredStateConfiguration** 모듈을 설치하세요.

   > [!NOTE]
   > `Install-Module`은 PowerShell 5.0 이상에 포함된 **PowerShellGet** 모듈에 포함되어 있습니다.

1. 조직 내 또는 공공 기관 내의 신뢰할 수 있는 인증 기관에서 DSC 끌어오기 서버에 대한 SSL 인증서를 가져옵니다. 기관에서 받은 인증서는 일반적으로 PFX 형식입니다.
1. `CERT:\LocalMachine\My`라는 기본 위치에 DSC 끌어오기 서버 역할을 할 노드의 인증서를 설치합니다.
   - 인증서 지문을 기록해 둡니다.
1. 등록 키로 사용할 GUID를 선택합니다. PowerShell을 사용하여 생성하려면 PS 프롬프트에 '`[guid]::newGuid()`' 또는 '`New-Guid`'를 입력하고 Enter 키를 누릅니다. 이 키는 클라이언트 노드에서 등록할 때 인증할 공유 키로 사용됩니다. 자세한 내용은 아래 등록 키 섹션을 참조하세요.
1. PowerShell ISE에서 다음의 구성 스크립트(**xPSDesiredStateConfiguration** 모듈의 폴더에 `Sample_xDscWebServiceRegistration.ps1`으로 포함됨)를 시작합니다(<kbd>F5</kbd>). 이 스크립트는 끌어오기 서버를 설정합니다.

    ```powershell
    configuration Sample_xDscWebServiceRegistration
    {
        param
        (
            [string[]]$NodeName = 'localhost',

            [ValidateNotNullOrEmpty()]
            [string] $certificateThumbPrint,

            [Parameter(HelpMessage='This should be a string with enough entropy (randomness) to protect the registration of clients to the pull server.  We will use new GUID by default.')]
            [ValidateNotNullOrEmpty()]
            [string] $RegistrationKey   # A guid that clients use to initiate conversation with pull server
        )

        Import-DSCResource -ModuleName PSDesiredStateConfiguration
        Import-DSCResource -ModuleName xPSDesiredStateConfiguration

        Node $NodeName
        {
            WindowsFeature DSCServiceFeature
            {
                Ensure = "Present"
                Name   = "DSC-Service"
            }

            xDscWebService PSDSCPullServer
            {
                Ensure                  = "Present"
                EndpointName            = "PSDSCPullServer"
                Port                    = 8080
                PhysicalPath            = "$env:SystemDrive\inetpub\PSDSCPullServer"
                CertificateThumbPrint   = $certificateThumbPrint
                ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
                ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
                State                   = "Started"
                DependsOn               = "[WindowsFeature]DSCServiceFeature"
                RegistrationKeyPath     = "$env:PROGRAMFILES\WindowsPowerShell\DscService"
                AcceptSelfSignedCertificates = $true
                UseSecurityBestPractices     = $true
                Enable32BitAppOnWin64   = $false
            }

            File RegistrationKeyFile
            {
                Ensure          = 'Present'
                Type            = 'File'
                DestinationPath = "$env:ProgramFiles\WindowsPowerShell\DscService\RegistrationKeys.txt"
                Contents        = $RegistrationKey
            }
        }
    }
    ```

1. 구성을 실행합니다. 이때 SSL 인증서의 지문을 **certificateThumbPrint** 매개 변수로 전달하고 GUID 등록 키를 **RegistrationKey** 매개 변수로 전달합니다.

    ```powershell
    # To find the Thumbprint for an installed SSL certificate for use with the pull server list all certificates in your local store
    # and then copy the thumbprint for the appropriate certificate by reviewing the certificate subjects
    dir Cert:\LocalMachine\my

    # Then include this thumbprint when running the configuration
    Sample_xDscWebServiceRegistration -certificateThumbprint 'A7000024B753FA6FFF88E966FD6E19301FAE9CCC' -RegistrationKey '140a952b-b9d6-406b-b416-e0f759c9c0e4' -OutputPath c:\Configs\PullServer

    # Run the compiled configuration to make the target node a DSC Pull Server
    Start-DscConfiguration -Path c:\Configs\PullServer -Wait -Verbose
    ```

#### <a name="registration-key"></a>등록 키

구성 ID 대신 구성 이름을 사용할 수 있도록 클라이언트 노드가 서버에 등록할 수 있도록 하려면 위 구성에서 만든 등록 키가 `C:\Program Files\WindowsPowerShell\DscService`에서 `RegistrationKeys.txt`라는 파일에 저장되어 있어야 합니다. 등록 키는 끌어오기 서버에 클라이언트를 처음 등록할 때 사용되는 공유 암호 역할을 합니다. 클라이언트는 등록이 완료되면 끌어오기 서버에 고유하게 인증하는 데 사용되는 자체 서명된 인증서를 생성합니다. 이 인증서의 지문은 로컬에 저장되고 끌어오기 서버의 URL과 연결됩니다.

> [!NOTE]
> PowerShell 4.0에서는 등록 키가 지원되지 않습니다.

끌어오기 서버에 인증하도록 노드를 구성하려면 이 끌어오기 서버에 등록할 모든 대상 노드의 메타 구성에 등록 키가 있어야 합니다. 아래 메타 구성에서 **RegistrationKey**는 대상 머신이 성공적으로 등록된 후에 제거되며, 해당 값은 끌어오기 서버의 `RegistrationKeys.txt` 파일에 저장된 값과 일치해야 합니다(이 예제의 경우 '140a952b-b9d6-406b-b416-e0f759c9c0e4'). 등록 키 값을 알면 대상 컴퓨터가 끌어오기 서버에 등록할 수 있으므로 등록 키 값을 항상 안전하게 보관하세요.

```powershell
[DSCLocalConfigurationManager()]
configuration Sample_MetaConfigurationToRegisterWithLessSecurePullServer
{
    param
    (
        [ValidateNotNullOrEmpty()]
        [string] $NodeName = 'localhost',

        [ValidateNotNullOrEmpty()]
        [string] $RegistrationKey, #same as the one used to set up pull server in previous configuration

        [ValidateNotNullOrEmpty()]
        [string] $ServerName = 'localhost' #node name of the pull server, same as $NodeName used in previous configuration
    )

    Node $NodeName
    {
        Settings
        {
            RefreshMode        = 'Pull'
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL          = "https://$ServerName`:8080/PSDSCPullServer.svc" # notice it is https
            RegistrationKey    = $RegistrationKey
            ConfigurationNames = @('ClientConfig')
        }

        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL       = "https://$ServerName`:8080/PSDSCPullServer.svc" # notice it is https
            RegistrationKey = $RegistrationKey
        }
    }
}

Sample_MetaConfigurationToRegisterWithLessSecurePullServer -RegistrationKey $RegistrationKey -OutputPath c:\Configs\TargetNodes
```

> [!NOTE]
> **ReportServerWeb** 섹션을 사용하면 보고 데이터를 끌어오기 서버로 보낼 수 있습니다.

메타 구성 파일에 **ConfigurationID** 속성이 없으면 끌어오기 서버가 V2 버전의 끌어오기 서버 프로토콜을 지원하므로 초기 등록이 필요하다는 의미입니다. 반대로 **ConfigurationID**가 있으면 V1 버전의 끌어오기 서버 프로토콜이 사용되고 등록 처리가 없습니다.

> [!NOTE]
> 밀어넣기 시나리오의 현재 릴리스에는 버그가 있기 때문에 끌어오기 서버에 등록하지 않은 노드에 대해 메타 구성 파일에서 ConfigurationID 속성을 정의해야 합니다. 따라서 V1 끌어오기 서버 프로토콜이 강제로 사용되고 등록 실패 메시지가 표시되지 않습니다.

## <a name="placing-configurations-and-resources"></a>구성 및 리소스 배치

끌어오기 서버 설정이 완료되면 끌어오기 서버 구성의 **ConfigurationPath** 및 **ModulePath** 속성에 정의된 폴더에 끌어올 대상 노드에 사용할 수 있는 모듈 및 구성을 배치합니다. 이러한 파일은 특정 형식이어야만 끌어오기 서버에서 올바로 처리할 수 있습니다.

### <a name="dsc-resource-module-package-format"></a>DSC 리소스 모듈 패키지 형식

각 리소스 모듈은 압축해야 하며 `{Module Name}_{Module Version}.zip` 패턴에 따라 이름을 지정해야 합니다.

예를 들어 모듈 버전이 3.1.2.0인 xWebAdminstration이라는 모듈은 `xWebAdministration_3.1.2.0.zip`으로 이름이 지정됩니다. 모듈의 각 버전은 단일 zip 파일에 포함되어야 합니다.
각 zip 파일에 리소스의 단일 버전만 있으므로 단일 디렉터리에서 여러 모듈 버전을 지원하는 WMF 5.0에서 추가된 모듈 형식은 지원되지 않습니다. 따라서 끌어오기 서버에서 사용할 DSC 리소스 모듈을 패키징하기 전에 디렉터리 구조를 약간 변경해야 합니다. WMF 5.0의 DSC 리소스를 포함하는 모듈의 기본 형식은 `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`입니다. 끌어오기 서버에 대해 패키징하기 전에 **{모듈 버전}** 폴더를 제거하면 되므로 경로는 `{Module Folder}\DscResources\{DSC Resource Folder}\`가 됩니다. 이렇게 변경하고 위에서 설명한 대로 폴더를 압축하여 이러한 zip 파일을 **ModulePath** 폴더에 배치합니다.

`New-DscChecksum {module zip file}`을 사용하여 새로 추가된 모듈에 대한 체크섬 파일을 만듭니다.

### <a name="configuration-mof-format"></a>구성 MOF 형식

구성 MOF 파일은 대상 노드의 LCM이 구성에 대한 유효성을 검사할 수 있도록 체크섬 파일과 함께 사용해야 합니다. 체크섬을 만들려면 [New-DscChecksum](/reference/6/PSDesiredStateConfiguration/New-DSCCheckSum.md) cmdlet을 호출합니다. 이 cmdlet은 구성 MOF가 있는 폴더를 지정하는 **Path** 매개 변수를 사용합니다. cmdlet은 `ConfigurationMOFName.mof.checksum`이라는 체크섬 파일을 만들며, 여기서 `ConfigurationMOFName`은 구성 mof 파일의 이름입니다. 지정된 폴더에 구성 MOF 파일이 두 개 이상 있는 경우, 폴더에 있는 각 구성에 대해 체크섬이 만들어집니다. MOF 파일 및 연관된 체크섬 파일을 **ConfigurationPath** 폴더에 배치합니다.

> [!NOTE]
> 어떤 식으로든 구성 MOF 파일을 변경하는 경우 체크섬 파일도 다시 만들어야 합니다.

### <a name="tooling"></a>도구

끌어오기 서버를 더 간단히 설정하고 유효성을 검사하고 관리할 수 있도록 xPSDesiredStateConfiguration 모듈의 최신 버전에는 다음 도구가 예제로 포함되어 있습니다.

1. 끌어오기 서버에서 사용할 DSC 리소스 모듈 및 구성 파일을 패키징하는 데 도움이 되는 모듈:
   [PublishModulesAndMofsToPullServer.psm1](https://github.com/dsccommunity/xPSDesiredStateConfiguration/blob/master/source/Modules/DscPullServerSetup/DscPullServerSetup.psm1).
   다음은 예제입니다.

    ```powershell
        # Example 1 - Package all versions of given modules installed locally and MOF files are in c:\LocalDepot
         $moduleList = @('xWebAdministration', 'xPhp')
         Publish-DSCModuleAndMof -Source C:\LocalDepot -ModuleNameList $moduleList

         # Example 2 - Package modules and mof documents from c:\LocalDepot
         Publish-DSCModuleAndMof -Source C:\LocalDepot -Force
    ```

1. 끌어오기 서버가 올바로 구성되었는지 확인하는 스크립트: [PullServerSetupTests.ps1](https://github.com/dsccommunity/xPSDesiredStateConfiguration/blob/master/source/Modules/DscPullServerSetup/DscPullServerSetupTest/DscPullServerSetupTest.ps1).

## <a name="community-solutions-for-pull-service"></a>끌어오기 서비스에 대한 커뮤니티 솔루션

DSC 커뮤니티는 끌어오기 서비스 프로토콜을 구현하는 여러 가지 솔루션을 제작했습니다. 이러한 솔루션은 온-프레미스 환경에 끌어오기 서비스 기능을 제공하며, 증분 향상 기능으로 커뮤니티에 다시 기여할 수 있는 기회를 제공합니다.

- [Tug](https://github.com/powershellorg/tug)
- [DSC-TRÆK](https://github.com/powershellorg/dsc-traek)

## <a name="pull-client-configuration"></a>끌어오기 클라이언트 구성

다음 항목에서는 끌어오기 클라이언트를 설정하는 것에 대해 자세히 설명합니다.

- [구성 ID를 사용하여 DSC 끌어오기 클라이언트 설정](pullClientConfigID.md)
- [구성 이름을 사용하여 DSC 끌어오기 클라이언트 설정](pullClientConfigNames.md)
- [부분 구성](partialConfigs.md)

## <a name="see-also"></a>참고 항목

- [Windows PowerShell Desired State Configuration 개요](../overview/overview.md)
- [구성 시행](enactingConfigurations.md)
- [DSC 보고서 서버 사용](reportServer.md)
- [[MS-DSCPM]: 필요한 상태 구성 끌어오기 모델 프로토콜](https://docs.microsoft.com/openspecs/windows_protocols/ms-dscpm/ea744c01-51a2-4000-9ef2-312711dcc8c9)
- [[MS-DSCPM]: 필요한 상태 구성 끌어오기 모델 프로토콜 오류](https://docs.microsoft.com/openspecs/windows_protocols/ms-winerrata/f5fc7ae3-9172-41e8-ac6a-2a5a5b7bfaf5)
