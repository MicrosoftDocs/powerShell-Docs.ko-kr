---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: WMF 5.1의 향상된 DSC
ms.openlocfilehash: 99434d14100de54d2d4c89c5888741ab2f1c512a
ms.sourcegitcommit: 01c60c0c97542dbad48ae34339cddbd813f1353b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78277639"
---
# <a name="improvements-in-desired-state-configuration-dsc-in-wmf-51"></a>WMF 5.1에서 DSC(필요한 상태 구성)의 개선 사항

## <a name="dsc-class-resource-improvements"></a>향상된 DSC 클래스 리소스

WMF 5.1에서 다음과 같은 알려진 문제를 해결했습니다.

- 클래스 기반 DSC 리소스의 Get() 함수에서 복합/해시 테이블 형식을 반환하는 경우 Get-DscConfiguration에서 빈 값(null) 또는 오류를 반환할 수 있습니다.
- DSC 구성에 RunAs 자격 증명이 사용된 경우 Get-DscConfiguration에서 오류를 반환합니다.
- 복합 구성에서는 클래스 기반 리소스를 사용할 수 없습니다.
- 클래스 기반 리소스에 자체 형식의 속성이 있는 경우 Start-DscConfiguration이 중단됩니다.
- 클래스 기반 리소스를 단독 리소스로 사용할 수 없습니다.

## <a name="dsc-resource-debugging-improvements"></a>향상된 DSC 리소스 디버깅

WMF 5.0에서 PowerShell 디버거는 클래스 기반 리소스 메서드(Get/Set/Test)에서 바로 중지되지 않았습니다. WMF 5.1에서는 디버거가 MOF 기반 리소스 메서드와 동일하게 클래스 기반 리소스 메서드에서 중지됩니다.

## <a name="dsc-pull-client-supports-tls-11-and-tls-12"></a>DSC 끌어오기 클라이언트가 TLS 1.1 및 TLS 1.2 지원

기존에 DSC 끌어오기 클라이언트는 HTTPS 연결을 통해 SSL3.0 및 TLS1.0만 지원했습니다. 더 안전한 프로토콜을 사용하도록 하는 경우 끌어오기 클라이언트의 작동이 중지되었습니다. WMF 5.1에서는 DSC 끌어오기 클라이언트가 SSL 3.0을 더 이상 지원하지 않고 더 안전한 TLS 1.1 및 TLS 1.2 프로토콜을 추가로 지원합니다.

## <a name="improved-pull-server-registration"></a>향상된 끌어오기 서버 등록

이전 버전의 WMF에서는 ESENT 데이터베이스를 사용하는 동안 DSC 끌어오기 서버에 동시 등록/보고 요청을 하는 경우 LCM이 등록 및/또는 보고에 실패했습니다. 이러한 경우 끌어오기 서버의 이벤트 로그에 "이미 사용 중인 인스턴스 이름" 오류가 표시됩니다. 이는 다중 스레드 시나리오에서 잘못된 패턴을 사용하여 ESENT 데이터베이스에 액세스하기 때문이었습니다. WMF 5.1에서는 이 문제가 해결되었습니다. WMF 5.1에서는 동시 등록 또는 보고(ESENT 데이터베이스 포함)가 올바로 작동합니다. 이 문제는 ESENT 데이터베이스에만 적용되고 OLEDB 데이터베이스에는 적용되지 않습니다.

## <a name="enable-circular-log-on-esent-database-instance"></a>ESENT 데이터베이스 인스턴스에 순환 로그 사용

이전 버전의 DSC-PullServer에서는 데이터베이스 인스턴스가 순환 로깅 없이 만들어지므로 ESENT 데이터베이스 로그 파일이 끌어오기 서버의 디스크 공간을 가득 채웠습니다. 이 릴리스에서는 끌어오기 서버의 web.config를 사용하여 인스턴스의 순환 로깅 동작을 제어할 수 있습니다. 기본적으로 CircularLogging은 TRUE로 설정됩니다.

```xml
<appSettings>
    <add key="dbprovider" value="ESENT" />
    <add key="dbconnectionstr" value="C:\Program Files\WindowsPowerShell\DscService\Devices.edb" />
    <add key="CheckpointDepthMaxKB" value="512" />
    <add key="UseCircularESENTLogs" value="TRUE" />
  </appSettings>
```

## <a name="wow64-support-for-configuration-keyword"></a>WOW64에서 구성 키워드 지원

이제 64비트 컴퓨터의 WOW64에서 `Configuration` 키워드가 지원됩니다. 즉, 64비트 컴퓨터에서 실행되는 Windows PowerShell ISE(x86) 같은 32비트 프로세스 내에서 DSC 구성을 정의하고 컴파일할 수 있습니다.

## <a name="pull-partial-configuration-naming-convention"></a>부분 구성 명명 규칙 끌어오기

이전 릴리스에서는 부분 구성에 대한 명명 규칙에 따라 끌어오기 서버/서비스의 MOF 파일 이름이 로컬 구성 관리자 설정에 지정된 부분 구성 이름과 일치하여 MOF 파일에 포함된 구성 이름과 일치해야 했습니다.

아래 스냅샷을 참조하세요.

- 노드가 수신할 수 있는 부분 구성을 정의하는 로컬 구성 설정입니다.

  ![샘플 메타 구성](media/DSC-improvements/MetaConfigPartialOne.png)

- 샘플 부분 구성 정의

  ```powershell
  Configuration PartialOne
  {
      Node('localhost')
      {
          File test
          {
              DestinationPath = "$env:TEMP\partialconfigexample.txt"
              Contents = 'Partial Config Example'
          }
      }
  }
  PartialOne
  ```

- 생성된 MOF 파일에 포함된 ‘ConfigurationName’

  ![생성된 mof 파일 샘플](media/DSC-improvements/PartialGeneratedMof.png)

- 풀 구성 리포지토리의 FileName

  ![구성 리포지토리의 FileName](media/DSC-improvements/PartialInConfigRepository.png)

  Azure 자동화 서비스 이름은 MOF 파일을 `<ConfigurationName>.<NodeName>.mof`로 생성했습니다. 따라서 아래 구성은 PartialOne.localhost.mof로 컴파일됩니다.

  따라서 Azure 자동화 서비스에서 부분 구성 중 하나를 끌어올 수 없었습니다.

  ```powershell
  Configuration PartialOne
  {
      Node('localhost')
      {
          File test
          {
              DestinationPath = "$env:TEMP\partialconfigexample.txt"
              Contents = 'Partial Config Example'
          }
      }
  }
  PartialOne
  ```

  WMF 5.1에서는 끌어오기 서버/서비스의 부분 구성을 `<ConfigurationName>.<NodeName>.mof`로 명명할 수 있습니다. 또한 컴퓨터가 끌어오기 서버/서비스에서 단일 구성을 끌어오는 경우 끌어오기 서버 구성 리포지토리의 구성 파일에 원하는 이름을 지정할 수 있습니다. 이러한 명명 유연성을 통해 노드를 Azure Automation 서비스로 부분적으로 관리할 수 있습니다. 이 경우 노드의 일부 구성을 Azure Automation DSC에서 가져오고 부분 구성을 로컬로 관리할 수 있습니다.

  아래 메타 구성은 노드를 로컬뿐 아니라 Azure Automation 서비스에서 관리하도록 설정합니다.

  ```powershell
  [DscLocalConfigurationManager()]
  Configuration RegistrationMetaConfig
  {
      Settings
      {
          RefreshFrequencyMins = 30
          RefreshMode = "PULL"
      }

      ConfigurationRepositoryWeb web
      {
          ServerURL =  $endPoint
          RegistrationKey = $registrationKey
          ConfigurationNames = $configurationName
      }

      # Partial configuration managed by Azure Automation service.
      PartialConfiguration PartialConfigurationManagedByAzureAutomation
      {
          ConfigurationSource = "[ConfigurationRepositoryWeb]Web"
      }

      # This partial configuration is managed locally.
      PartialConfiguration OnPremisesConfig
      {
          RefreshMode = "PUSH"
          ExclusiveResources = @("Script")
      }

  }

  RegistrationMetaConfig
  Set-DscLocalConfigurationManager -Path .\RegistrationMetaConfig -Verbose
  ```

## <a name="using-psdscrunascredential-with-dsc-composite-resources"></a>DSC 복합 리소스와 함께 PsDscRunAsCredential 사용

[PsDscRunAsCredential](/powershell/scripting/dsc/configurations/runAsUser)을 DSC [복합](/powershell/scripting/dsc/authoringresourcecomposite) 리소스와 함께 사용할 수 있도록 지원을 추가했습니다.

이제 구성 내에서 복합 리소스를 사용할 때 **PsDscRunAsCredential** 값을 지정할 수 있습니다. 이 값을 지정할 경우 모든 리소스가 복합 리소스 내에서 RunAs 사용자로 실행됩니다. 복합 리소스가 다른 복합 리소스를 호출하는 경우에도 해당 리소스가 모두 RunAs 사용자로 실행됩니다. RunAs 자격 증명은 복합 리소스 계층 구조의 모든 수준에 전파됩니다. 복합 리소스 내의 리소스가 **PsDscRunAsCredential**의 고유한 값을 지정하는 경우 구성 컴파일 중 병합 오류가 발생합니다.

이 예제에서는 PSDesiredStateConfiguration 모듈에 포함된 [WindowsFeatureSet](/powershell/scripting/dsc/reference/resources/windows/windowsfeaturesetresource) 복합 리소스와 함께 사용하는 방법입니다.

```powershell
Configuration InstallWindowsFeature
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node $AllNodes.NodeName
    {
        WindowsFeatureSet features
        {
            Name = @("Telnet-Client","SNMP-Service")
            Ensure = "Present"
            IncludeAllSubFeature = $true
            PsDscRunAsCredential = Get-Credential
        }
    }
}

$configData = @{
    AllNodes = @(
        @{
            NodeName             = 'localhost'
            PSDscAllowDomainUser = $true
            CertificateFile      = 'C:\publicKeys\targetNode.cer'
            Thumbprint           = '7ee7f09d-4be0-41aa-a47f-96b9e3bdec25'
        }
    )
}

InstallWindowsFeature -ConfigurationData $configData
```

## <a name="allowing-for-identical-duplicate-resources-in-a-configuration"></a>구성에서 동일한 중복 리소스 허용

DSC는 구성 내에서 충돌하는 리소스 정의를 허용하거나 처리하지 않습니다. 충돌을 해결하려고 하지 않고 단순히 실패합니다. 구성 다시 사용이 복합 리소스 등을 통해 더 많이 활용되면 충돌이 더 자주 발생합니다. 충돌하는 리소스 정의가 동일하면 DSC가 지능적이어서 이를 허용해야 합니다. 이 릴리스에서는 정의가 동일한 리소스 인스턴스가 여러 개 있어도 됩니다.

```powershell
Configuration IIS_FrontEnd
{
    WindowsFeature FE_IIS         #Identical resource
    {
        Ensure = 'Present'
        Name = 'Web-Server'
    }

    WindowsFeature FTP
    {
        Ensure = 'Present'
        Name = 'Web-FTP-Server'
    }
}

Configuration IIS_Worker
{
    WindowsFeature Worker_IIS      #Identical resource
    {
        Ensure = 'Present'
        Name = 'Web-Server'
    }

    WindowsFeature ASP
    {
        Ensure = 'Present'
        Name = 'Web-ASP-Net45'
    }
}

Configuration WebApplication
{
    IIS_Frontend Web {}

    IIS_Worker ASP {}
}
```

이전 릴리스에서는 'Web-Server' 역할을 설치하려는 WindowsFeature FE_IIS와 WindowsFeature Worker_IIS 인스턴스 간의 충돌로 인해 컴파일이 실패했습니다. 이러한 두 구성에서 구성하려는 *모든* 속성이 동일합니다. 이러한 두 리소스의 *모든* 속성이 동일하므로 이제 컴파일이 성공합니다.

두 리소스 간에 다른 속성이 있으면 동일한 것으로 간주되지 않고 컴파일이 실패합니다.

## <a name="dsc-module-and-configuration-signing-validations"></a>DSC 모듈 및 구성 서명 유효성 검사

DSC에서는 구성 및 모듈이 끌어오기 서버에서 관리되는 컴퓨터로 배포됩니다. 끌어오기 서버가 손상되는 경우 공격자가 끌어오기 서버의 구성 및 모듈을 수정하여 모든 관리형 노드로 배포할 수 있습니다.

WMF 5.1의 DSC에서는 카탈로그 및 구성(.MOF) 파일에 있는 디지털 서명의 유효성을 검사할 수 있습니다. 이 기능은 노드에서 신뢰할 수 있는 서명자가 서명하지 않았거나 신뢰할 수 있는 서명자가 서명한 후 변조된 구성 또는 모듈 파일을 실행하지 못하게 합니다.

### <a name="how-to-sign-configuration-and-module"></a>구성 및 모듈에 서명하는 방법

- 구성 파일(.MOF): 기존 PowerShell cmdlet [Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature)가 MOF 파일 서명을 지원하도록 확장되었습니다.
- 모듈: 다음 단계에 따라 해당 모듈 카탈로그에 서명하여 모듈 서명을 수행합니다.
  1. 카탈로그 파일 만들기: 카탈로그 파일에는 암호화 해시 또는 지문의 컬렉션이 포함됩니다. 각 지문은 모듈에 포함된 파일에 해당합니다. 사용자가 모듈의 카탈로그 파일을 만들 수 있도록 지원하는 새로운 [New-FileCatalog](/powershell/module/microsoft.powershell.security/new-filecatalog) cmdlet이 추가되었습니다.
  2. 카탈로그 파일에 서명: [Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature)를 사용하여 카탈로그 파일에 서명합니다.
  3. 카탈로그 파일을 모듈 폴더 내에 배치합니다. 규칙에 따라 모듈 카탈로그 파일은 모듈과 이름이 같은 모듈 폴더에 배치해야 합니다.

### <a name="localconfigurationmanager-settings-to-enable-signing-validations"></a>서명 유효성 검사를 사용하도록 설정하는 LocalConfigurationManager 설정

#### <a name="pull"></a>끌어오기

노드의 LocalConfigurationManager는 현재 설정에 따라 모듈 및 구성의 서명 유효성 검사를 수행합니다. 기본적으로 서명 유효성 검사를 사용하지 않도록 설정되어 있습니다. 서명 유효성 검사를 사용하도록 설정하려면 아래 표시된 노드의 메타 구성 정의에 'SignatureValidation' 블록을 추가합니다.

```powershell
[DSCLocalConfigurationManager()]
Configuration EnableSignatureValidation
{
    Settings
    {
        RefreshMode = 'PULL'
    }

    ConfigurationRepositoryWeb pullserver{
      ConfigurationNames = 'sql'
      ServerURL = 'http://localhost:8080/PSDSCPullServer/PSDSCPullServer.svc'
      AllowUnsecureConnection = $true
      RegistrationKey = 'd6750ff1-d8dd-49f7-8caf-7471ea9793fc' # Replace this with correct registration key.
    }
    SignatureValidation validations{
        # If the TrustedStorePath property is provided then LCM will use the custom path. Otherwise, the LCM will use default trusted store path (Cert:\LocalMachine\DSCStore) to find the signing certificate.
        TrustedStorePath = 'Cert:\LocalMachine\DSCStore'
        SignedItemType = 'Configuration','Module'         # This is a list of DSC artifacts, for which LCM need to verify their digital signature before executing them on the node.
    }

}
EnableSignatureValidation
Set-DscLocalConfigurationManager -Path .\EnableSignatureValidation -Verbose
```

노드에서 위의 메타 구성을 설정하면 다운로드된 구성 및 모듈에서 서명 유효성을 검사할 수 있습니다. 로컬 구성 관리자는 다음 단계를 수행하여 디지털 서명을 확인합니다.

1. `Get-AuthenticodeSignature` cmdlet을 사용하여 구성 파일(.MOF)의 서명이 유효한지 확인합니다.
2. 서명자에게 권한을 부여한 인증 기관을 신뢰할 수 있는지 확인합니다.
3. 구성의 모듈/리소스 종속성을 임시 위치로 다운로드합니다.
4. 모듈 내에 포함된 카탈로그의 서명을 확인합니다.
   - `<moduleName>.cat` 파일을 찾고 `Get-AuthenticodeSignature`를 사용하여 해당 서명을 확인합니다.
   - 서명자를 인증한 인증 기관을 신뢰할 수 있는지 확인합니다.
   - 새 `Test-FileCatalog` cmdlet을 사용하여 모듈의 콘텐츠가 변조되지 않았는지 확인합니다.
5. `$env:ProgramFiles\WindowsPowerShell\Modules\`에 대한 `Install-Module`
6. 구성 처리

> [!NOTE]
> 모듈 카탈로그 및 구성의 서명 유효성 검사는 시스템에 구성을 처음으로 적용할 때나 모듈을 다운로드하여 설치할 때만 수행됩니다.
> 일관성 검사에서는 Current.mof 또는 해당 모듈 종속성의 서명 유효성을 검사하지 않습니다. 끌어오기 서버에서 끌어온 구성에 서명이 되어 있지 않은 등 어느 단계에서든 유효성 검사가 실패하면 구성 처리가 종료되고 아래와 같은 오류가 표시되며 모든 임시 파일이 삭제됩니다.

![샘플 오류 출력 구성](media/DSC-improvements/PullUnsignedConfigFail.png)

마찬가지로 카탈로그에 서명이 되어 있지 않은 모듈을 끌어오면 다음 오류가 발생합니다.

![샘플 오류 출력 모듈](media/DSC-improvements/PullUnisgnedCatalog.png)

#### <a name="push"></a>밀어넣기

푸시를 사용하여 전달된 구성은 노드로 전달되기 전에 해당 소스에서 변조될 수 있습니다. 로컬 구성 관리자는 푸시되거나 게시된 구성에 대해 비슷한 서명 유효성 검사 단계를 수행합니다. 다음은 푸시에 대한 서명 유효성 검사의 완전한 예제입니다.

- 노드에서 서명 유효성 검사를 사용하도록 설정합니다.

  ```powershell
  [DSCLocalConfigurationManager()]
  Configuration EnableSignatureValidation
  {
      Settings
      {
          RefreshMode = 'PUSH'
      }
      SignatureValidation validations{
          TrustedStorePath = 'Cert:\LocalMachine\DSCStore'
          SignedItemType =  'Configuration','Module'
      }

  }
  EnableSignatureValidation
  Set-DscLocalConfigurationManager -Path .\EnableSignatureValidation -Verbose
  ```

- 샘플 구성 파일을 만듭니다.

  ```powershell
  # Sample configuration
  Configuration Test
  {

      File foo
      {
          DestinationPath =  "$env:TEMP\signingTest.txt"
          Contents = "ABC"
      }
  }
  Test
  ```

- 서명되지 않은 구성 파일을 노드로 푸시해 봅니다.

  ```powershell
  Start-DscConfiguration -Path .\Test -Wait -Verbose -Force
  ```

  ![ErrorUnsignedMofPushed](media/DSC-improvements/PushUnsignedMof.png)

- 코드 서명 인증서를 사용하여 구성 파일에 서명합니다.

  ![SignMofFile](media/DSC-improvements/SignMofFile.png)

- 서명된 MOF 파일을 푸시해 봅니다.

  ![PushSignedMofFile](media/DSC-improvements/PushSignedMof.png)
