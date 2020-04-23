---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Linux용 DSC(필요한 상태 구성) 시작
ms.openlocfilehash: b1bc9b9fafd89a1af0f967de38a817bff1f3ffe3
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2020
ms.locfileid: "73933843"
---
# <a name="get-started-with-desired-state-configuration-dsc-for-linux"></a>Linux용 DSC(필요한 상태 구성) 시작

이 항목에서는 Linux용 PowerShell DSC(필요한 상태 구성) 사용 방법에 대해 설명합니다. DSC에 대한 일반적인 내용은 [Windows PowerShell 필요한 상태 구성 시작](../overview/overview.md)을 참조하세요.

## <a name="supported-linux-operation-system-versions"></a>지원되는 Linux 운영 체제 버전

다음의 Linux 운영 체제 버전이 Linux용 DSC에 대해 지원됩니다.

- CentOS 5, 6 및 7(x86/x64)
- Debian GNU/Linux 6, 7 및 8(x86/x64)
- Oracle Linux 5, 6 및 7(x86/x64)
- Red Hat Enterprise Linux Server 5, 6 및 7(x86/x64)
- SUSE Linux Enterprise Server 10, 11 및 12(x86/x64)
- Ubuntu Server 12.04 LTS, 14.04 LTS 및 16.04 LTS(x86/x64)

다음 표에서는 Linux용 DSC에 대한 필수 패키지 종속성에 대해 설명합니다.

|  필수 패키지 |  Description |  최소 버전 |
|---|---|---|
| glibc| GNU 라이브러리| 2…4 – 31.30|
| python| Python| 2.4 – 3.4|
| omiserver| 개방형 관리 인프라| 1.0.8.1|
| openssl| OpenSSL 라이브러리| 0.9.8 또는 1.0|
| ctypes| Python CTypes 라이브러리| Python 버전과 일치해야 합니다.|
| libcurl| cURL http 클라이언트 라이브러리| 7.15.1|

## <a name="installing-dsc-for-linux"></a>Linux용 DSC 설치

Linux용 DSC를 설치하려면 먼저 [OMI(개방형 관리 인프라)](https://github.com/Microsoft/omi)를 설치해야 합니다.

### <a name="installing-omi"></a>OMI 설치

Linux용 필요한 상태 구성을 사용하려면 OMI(개방형 관리 인프라) CIM 서버 버전 1.0.8.1 이상이 있어야 합니다. OMI는 Open Group: [Open Management Infrastructure(OMI)](https://github.com/Microsoft/omi)(개방형 관리 인프라)에서 다운로드할 수 있습니다.

OMI를 설치하려면 Linux 시스템(.rpm 또는.deb)과 OpenSSL 버전(ssl_098 또는 ssl_100) 및 아키텍처(x64/x86)에 적절한 패키지를 설치합니다. RPM 패키지는 CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server 및 Oracle Linux에 적합합니다. DEB 패키지는 Debian GNU/Linux 및 Ubuntu 서버에 적합합니다. ssl_098 패키지는 OpenSSL 0.9.8이 설치된 컴퓨터에 적합하고, ssl_100 패키지는 OpenSSL 1.0이 설치된 컴퓨터에 적합합니다.

> [!NOTE]
> 설치된 OpenSSL 버전을 확인하려면 `openssl version` 명령을 실행합니다.

CentOS 7 x64 시스템에 OMI를 설치하려면 다음 명령을 실행합니다.

`# sudo rpm -Uvh omiserver-1.0.8.ssl_100.rpm`

### <a name="installing-dsc"></a>DSC 설치

Linux용 DSC는 [여기](https://github.com/Microsoft/PowerShell-DSC-for-Linux/releases/tag/v1.1.1-294)에서 다운로드할 수 있습니다.

DSC를 설치하려면 Linux 시스템(.rpm 또는.deb)과 OpenSSL 버전(ssl_098 또는 ssl_100) 및 아키텍처(x64/x86)에 적절한 패키지를 설치합니다. RPM 패키지는 CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server 및 Oracle Linux에 적합합니다. DEB 패키지는 Debian GNU/Linux 및 Ubuntu 서버에 적합합니다. ssl_098 패키지는 OpenSSL 0.9.8이 설치된 컴퓨터에 적합하고, ssl_100 패키지는 OpenSSL 1.0이 설치된 컴퓨터에 적합합니다.

> [!NOTE]
> 설치된 OpenSSL 버전을 확인하려면 openssl version 명령을 실행합니다.

CentOS 7 x64 시스템에 DSC를 설치하려면 다음 명령을 실행합니다.

`# sudo rpm -Uvh dsc-1.0.0-254.ssl_100.x64.rpm`

## <a name="using-dsc-for-linux"></a>Linux용 DSC 사용

다음 섹션에서는 Linux 컴퓨터에서 DSC 구성을 만들고 실행하는 방법을 설명합니다.

### <a name="creating-a-configuration-mof-document"></a>구성 MOF 문서 만들기

Windows PowerShell 구성 키워드는 Windows 컴퓨터와 마찬가지로 Linux 컴퓨터용 구성을 만드는 데 사용됩니다. 다음 단계에서는 Windows PowerShell을 사용한 Linux 컴퓨터용 구성 문서 작성에 대해 설명합니다.

1. nx 모듈을 가져옵니다. nx Windows PowerShell 모듈은 Linux용 DSC를 위한 기본 제공 리소스에 대한 스키마를 포함하며, 로컬 컴퓨터에 설치되어 구성에 가져와야 합니다.

   - nx 모듈을 설치하려면 nx 모듈 디렉터리를 `$env:USERPROFILE\Documents\WindowsPowerShell\Modules\` 또는 `$PSHOME\Modules`에 복사합니다. nx 모듈은 Linux용 DSC 설치 패키지에 포함되어 있습니다. 구성에서 nx 모듈을 가져오려면 `Import-DSCResource` 명령을 사용합니다.

   ```powershell
   Configuration ExampleConfiguration{

    Import-DSCResource -Module nx

   }
   ```

2. 구성을 정의하고 구성 문서를 생성합니다.

   ```powershell
   Configuration ExampleConfiguration
   {
        Import-DscResource -Module nx

        Node  "linuxhost.contoso.com"
        {
            nxFile ExampleFile 
            {
                DestinationPath = "/tmp/example"
                Contents = "hello world `n"
                Ensure = "Present"
                Type = "File"
            }
        }
   }

   ExampleConfiguration -OutputPath:"C:\temp"
   ```

### <a name="push-the-configuration-to-the-linux-computer"></a>구성을 Linux 컴퓨터에 밀어넣기

구성 문서(MOF 파일)을 [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet을 사용하여 Linux 컴퓨터에 밀어넣을 수 있습니다. 원격으로 Linux 컴퓨터에 [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) 또는 [Test-DscConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration) cmdlet과 함께 이 cmdlet을 사용하려면 CIMSession을 사용해야 합니다. CIMSession를 Linux 컴퓨터에 만드는 데에는 [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) cmdlet이 사용됩니다.

다음 코드는 Linux용 DSC를 위한 CIMSession을 만드는 방법을 보여 줍니다.

```powershell
$Node = "ostc-dsc-01"
$Credential = Get-Credential -UserName "root" -Message "Enter Password:"

#Ignore SSL certificate validation
#$opt = New-CimSessionOption -UseSsl $true -SkipCACheck $true -SkipCNCheck $true -SkipRevocationCheck $true

#Options for a trusted SSL certificate
$opt = New-CimSessionOption -UseSsl $true
$Sess=New-CimSession -Credential $credential -ComputerName $Node -Port 5986 -Authentication basic -SessionOption $opt -OperationTimeoutSec 90
```

> [!NOTE]
> "밀어넣기" 모드의 경우, 사용자 자격 증명은 Linux 컴퓨터 상의 루트 사용자여야 합니다.
> Linux용 DSC에는 SSL/TLS 연결만 지원되며, `New-CimSession`은 $true로 설정된 –UseSSL 매개 변수와 함께 사용해야 합니다.
> OMI(DSC용)에서 사용하는 SSL 인증서는 속성이 pemfile 및 keyfile인 `/etc/opt/omi/conf/omiserver.conf` 파일에 지정되어 있습니다.
> 이 인증서를 [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) cmdlet을 실행 중인 Windows 컴퓨터에서 신뢰하지 않는 경우에는 CIMSession 옵션 `-SkipCACheck $true -SkipCNCheck $true -SkipRevocationCheck $true`을 사용하여 인증서 유효성 검사를 무시하도록 선택할 수 있습니다.

Linux 노드에 DSC 구성을 밀어 넣으려면 다음 명령을 실행합니다.

`Start-DscConfiguration -Path:"C:\temp" -CimSession $Sess -Wait -Verbose`

### <a name="distribute-the-configuration-with-a-pull-server"></a>끌어오기 서버로 구성 배포

구성은 Windows 컴퓨터와 마찬가지로 끌어오기 서버로 Linux 컴퓨터에 배포할 수 있습니다. 끌어오기 서버 사용에 대한 지침이 필요하면 [Windows PowerShell Desired State Configuration Pull Servers(Windows PowerShell 필요한 상태 구성 끌어오기 서버)](../pull-server/pullServer.md)를 참조하세요. 추가 정보 및 끌어오기 서버와 함께 Linux 컴퓨터를 사용하는 것과 관련된 제한 사항에 대해서는 Linux용 필요한 상태 구성에 대한 릴리스 정보를 참조하세요.

### <a name="working-with-configurations-locally"></a>로컬에서 구성 사용

Linux용 DSC는 로컬 Linux 컴퓨터의 구성으로 작업하는 스크립트를 포함합니다. 이 스크립트는 `/opt/microsoft/dsc/Scripts`에 있으며 다음 내용을 포함합니다.

- GetDscConfiguration.py

컴퓨터에 적용된 현재 구성을 반환합니다. Windows PowerShell cmdlet `Get-DscConfiguration` cmdlet과 유사합니다.

`# sudo ./GetDscConfiguration.py`

- GetDscLocalConfigurationManager.py

컴퓨터에 적용된 현재 메타 구성을 반환합니다. cmdlet [Get-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) cmdlet과 유사합니다.

`# sudo ./GetDscLocalConfigurationManager.py`

- InstallModule.py

사용자 지정 DSC 리소스 모듈을 설치합니다. 모듈 공유 개체 라이브러리 및 스키마 MOF 파일을 포함하는 .zip 파일의 경로가 필요합니다.

`# sudo ./InstallModule.py /tmp/cnx_Resource.zip`

- RemoveModule.py

사용자 지정 DSC 리소스 모듈을 제거합니다. 제거할 모듈의 이름이 필요합니다.

`# sudo ./RemoveModule.py cnx_Resource`

- StartDscLocalConfigurationManager.py

구성 MOF 파일을 컴퓨터에 적용합니다. [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet과 유사합니다. 적용할 구성 MOF의 경로가 필요합니다.

`# sudo ./StartDscLocalConfigurationManager.py –configurationmof /tmp/localhost.mof`

- SetDscLocalConfigurationManager.py

메타 구성 MOF 파일을 컴퓨터에 적용합니다. [Set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) cmdlet과 유사합니다. 적용할 메타 구성 MOF의 경로가 필요합니다.

`# sudo ./SetDscLocalConfigurationManager.py –configurationmof /tmp/localhost.meta.mof`

## <a name="powershell-desired-state-configuration-for-linux-log-files"></a>Linux용 PowerShell 필요한 상태 구성 로그 파일

Linux용 DSC 메시지용으로 다음 로그 파일이 생성됩니다.

|로그 파일|디렉터리|Description|
|---|---|---|
|**omiserver.log**|`/var/opt/omi/log`|OMI CIM 서버의 작업에 관한 메시지입니다.|
|**dsc.log**|`/var/opt/omi/log`|LCM(로컬 구성 관리자)의 작업 및 DSC 리소스 작업에 대한 메시지입니다.|
