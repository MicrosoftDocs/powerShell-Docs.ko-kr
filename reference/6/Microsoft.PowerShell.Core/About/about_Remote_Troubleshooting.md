---
description: PowerShell에서 원격 작업의 문제를 해결 하는 방법을 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_troubleshooting?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Troubleshooting
ms.openlocfilehash: b78f3004e316b6d4de1082b914970d3c8b56f955
ms.sourcegitcommit: c1e4739f5d52282fb05a8cff92b0f5d10e2edac1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "93225298"
---
# <a name="about-remote-troubleshooting"></a>원격 문제 해결 정보

## <a name="short-description"></a>간단한 설명
PowerShell에서 원격 작업의 문제를 해결 하는 방법을 설명 합니다.

## <a name="long-description"></a>자세한 설명입니다.

이 섹션에서는 WS-Management 기술을 기반으로 하는 PowerShell의 원격 기능을 사용 하는 경우 발생할 수 있는 몇 가지 문제에 대해 설명 하 고 이러한 문제에 대 한 해결 방법을 제안 합니다.

PowerShell 원격 기능을 사용 하기 전에 [about_Remote](about_remote.md) 및 [about_Remote_Requirements](about_Remote_Requirements.md) 에서 구성 및 기본 사용에 대 한 지침을 참조 하세요. 또한 각 원격 cmdlet에 대 한 도움말 항목 (특히 매개 변수 설명)에는 문제를 방지 하는 데 도움이 되도록 설계 된 유용한 정보가 있습니다.

> [!NOTE]
> WSMan: 드라이브에서 세션 구성, 신뢰할 수 있는 호스트, 포트 또는 수신기에 대 한 변경 내용을 포함 하 여 로컬 컴퓨터에 대 한 설정을 보거나 변경 하려면 **관리자 권한으로 실행** 옵션을 사용 하 여 PowerShell을 시작 합니다.

## <a name="troubleshooting-permission-and-authentication-issues"></a>권한 및 인증 문제 해결

이 섹션에서는 사용자 및 컴퓨터 권한 및 원격 요구 사항과 관련 된 원격 문제에 대해 설명 합니다.

### <a name="how-to-run-as-administrator"></a>관리자 권한으로 실행 하는 방법

```
ERROR: Access is denied. You need to run this cmdlet from an elevated
process.
```

로컬 컴퓨터에서 원격 세션을 시작 하거나 WSMan: 드라이브에서 로컬 컴퓨터에 대 한 설정을 확인 하거나 변경 하려면 (세션 구성, 신뢰할 수 있는 호스트, 포트 또는 수신기 변경 포함) **관리자 권한으로 실행** 옵션을 사용 하 여 Windows PowerShell을 시작 합니다.

**관리자 권한으로 실행** 옵션을 사용 하 여 Windows PowerShell을 시작 하려면 다음을 수행 합니다.

- Windows PowerShell (또는 Windows PowerShell ISE) 아이콘을 마우스 오른쪽 단추로 클릭 한 다음 **관리자 권한으로 실행** 을 클릭 합니다.

  Windows 7 및 Windows Server 2008 r 2에서 **관리자 권한으로 실행** 옵션을 사용 하 여 windows PowerShell을 시작 합니다.

- Windows 작업 표시줄에서 Windows PowerShell 아이콘을 마우스 오른쪽 단추로 클릭 한 다음 **관리자 권한으로 실행** 을 클릭 합니다.

  Windows Server 2008 r 2에서 Windows PowerShell 아이콘은 기본적으로 작업 표시줄에 고정 됩니다.

### <a name="how-to-enable-remoting"></a>원격 기능을 사용 하도록 설정 하는 방법

```
ERROR:  ACCESS IS DENIED

or

ERROR: The connection to the remote host was refused. Verify that the
WS-Management service is running on the remote host and configured to
listen for requests on the correct port and HTTP URL.
```

컴퓨터에서 원격 명령을 보낼 수 있도록 하는 구성은 필요 하지 않습니다.
그러나 원격 명령을 받으려면 컴퓨터에서 PowerShell 원격을 사용 하도록 설정 해야 합니다. 을 사용 하도록 설정 하려면 WinRM 서비스를 시작 하 고, WinRM 서비스의 시작 유형을 자동으로 설정 하 고, HTTP 및 HTTPS 연결에 대 한 수신기를 만들고, 기본 세션 구성을 만듭니다.

Windows PowerShell remoting은 기본적으로 windows server 2012 및 최신 버전의 Windows Server에서 사용 하도록 설정 됩니다. 다른 모든 시스템에서 cmdlet을 실행 `Enable-PSRemoting` 하 여 원격 기능을 사용 하도록 설정 합니다. 또한 `Enable-PSRemoting` 원격 기능을 사용 하지 않도록 설정 된 경우 cmdlet을 실행 하 여 windows server 2012 및 최신 버전의 Windows server에서 원격 기능을 다시 사용 하도록 설정할 수 있습니다.

원격 명령을 받도록 컴퓨터를 구성 하려면 cmdlet을 사용 `Enable-PSRemoting` 합니다. 다음 명령은 필요한 모든 원격 설정을 사용 하도록 설정 하 고, 세션 구성을 사용 하도록 설정 하 고, 변경 내용을 적용 하기 위해 WinRM 서비스를 다시 시작 합니다.

`Enable-PSRemoting`

모든 사용자 프롬프트를 표시 하지 않으려면 다음을 입력 합니다.

`Enable-PSRemoting -Force`

자세한 내용은 [enable-psremoting](xref:Microsoft.PowerShell.Core.Enable-PSRemoting)를 참조 하세요.

### <a name="how-to-enable-remoting-in-an-enterprise"></a>엔터프라이즈에서 원격 기능을 사용 하도록 설정 하는 방법

```
ERROR:  ACCESS IS DENIED

or

ERROR: The connection to the remote host was refused. Verify that the
WS-Management service is running on the remote host and configured to listen
for requests on the correct port and HTTP URL.
```

단일 컴퓨터에서 원격 PowerShell 명령을 수신 하 고 연결을 허용할 수 있도록 설정 하려면 `Enable-PSRemoting` cmdlet을 사용 합니다.

기업에서 여러 컴퓨터에 대 한 원격 기능을 사용 하도록 설정 하려면 다음과 같은 크기 조정 옵션을 사용할 수 있습니다.

- 원격을 위한 수신기를 구성 하려면 **수신기의 자동 구성 허용** 그룹 정책을 사용 하도록 설정 합니다.

- 여러 컴퓨터에서 WinRM (Windows 원격 관리의 시작 유형을 자동으로 설정 하려면 cmdlet을 사용 합니다 `Set-Service` .

- 방화벽 예외를 사용 하도록 설정 하려면 **Windows 방화벽: 로컬 포트 예외 허용** 그룹 정책을 사용 합니다.

### <a name="how-to-enable-listeners-by-using-a-group-policy"></a>그룹 정책을 사용 하 여 수신기를 사용 하도록 설정 하는 방법

```
ERROR:  ACCESS IS DENIED

or

ERROR: The connection to the remote host was refused. Verify that the
WS-Management service is running on the remote host and configured to listen
for requests on the correct port and HTTP URL.
```

도메인의 모든 컴퓨터에 대 한 수신기를 구성 하려면 다음 그룹 정책 경로에서 **수신기 자동 구성 허용** 정책을 사용 하도록 설정 합니다.

```
Computer Configuration\Administrative Templates\Windows Components
    \Windows Remote Management (WinRM)\WinRM service
```

정책을 사용 하도록 설정 하 고 IPv4 및 IPv6 필터를 지정 합니다. 와일드 카드 ( `*` )를 사용할 수 있습니다.

### <a name="how-to-enable-remoting-on-public-networks"></a>공용 네트워크에서 원격 기능을 사용 하도록 설정 하는 방법

```
ERROR:  Unable to check the status of the firewall
```

`Enable-PSRemoting`로컬 네트워크가 public이 고 명령에서 **SkipNetworkProfileCheck** 매개 변수를 사용 하지 않는 경우 cmdlet은이 오류를 반환 합니다.

서버 버전의 Windows에서는 `Enable-PSRemoting` 모든 네트워크 위치 형식에 대해 성공 합니다. 개인 및 도메인 ("홈" 및 "회사") 네트워크에 대 한 원격 액세스를 허용 하는 방화벽 규칙을 만듭니다. 공용 네트워크의 경우 동일한 로컬 서브넷의 원격 액세스를 허용 하는 방화벽 규칙을 만듭니다.

클라이언트 버전의 Windows에서는 `Enable-PSRemoting` 개인 및 도메인 네트워크에 대해 성공 합니다. 기본적으로 공용 네트워크에서는 실패 하지만, **SkipNetworkProfileCheck** 매개 변수를 사용 하는 경우가 `Enable-PSRemoting` 성공 하 고 동일한 로컬 서브넷의 트래픽을 허용 하는 방화벽 규칙을 만듭니다.

공용 네트워크에 대 한 로컬 서브넷 제한을 제거 하 고 모든 위치에서 원격 액세스를 허용 하려면 다음 명령을 실행 합니다.

```powershell
Set-NetFirewallRule -Name "WINRM-HTTP-In-TCP-PUBLIC" -RemoteAddress Any
```

`Set-NetFirewallRule`NetSecurity 모듈에서 cmdlet을 내보냅니다.

> [!NOTE]
> Windows PowerShell 2.0에서는 Windows의 서버 버전을 실행 하는 컴퓨터에서 `Enable-PSRemoting` 개인, 도메인 및 공용 네트워크에 대 한 원격 액세스를 허용 하는 방화벽 규칙을 만듭니다. 클라이언트 버전의 Windows를 실행 하는 컴퓨터에서는 `Enable-PSRemoting` 개인 및 도메인 네트워크에 대 한 원격 액세스만 허용 하는 방화벽 규칙을 만듭니다.

### <a name="how-to-enable-a-firewall-exception-by-using-a-group-policy"></a>그룹 정책을 사용 하 여 방화벽 예외를 사용 하도록 설정 하는 방법

```
ERROR:  ACCESS IS DENIED

or

ERROR: The connection to the remote host was refused. Verify that the
WS-Management service is running on the remote host and configured to listen
for requests on the correct port and HTTP URL.
```

도메인의 모든 컴퓨터에서에 대해 방화벽 예외를 사용 하도록 설정 하려면 다음 그룹 정책 경로에서 **Windows 방화벽: 로컬 포트 예외 허용** 정책을 사용 하도록 설정 합니다.

```
Computer Configuration\Administrative Templates\Network
    \Network Connections\Windows Firewall\Domain Profile
```

이 정책을 사용 하면 컴퓨터의 Administrators 그룹 구성원은 **제어판** 의 **Windows 방화벽** 을 사용 하 여 Windows 원격 관리 서비스에 대 한 방화벽 예외를 만들 수 있습니다.

정책 구성이 잘못 된 경우 다음 오류가 표시 될 수 있습니다.

```
The client cannot connect to the destination specified in the request. Verify
that the service on the destination is running and is accepting requests.
```

정책에서 구성 오류가 발생 하면 **ListeningOn** 속성에 대해 빈 값이 반환 됩니다. 다음 명령을 사용 하 여 값을 확인 합니다.

```powershell
PS> Get-WSManInstance winrm/config/listener -Enumerate

cfg                   : http://schemas.microsoft.com/wbem/wsman/1/config/listener
xsi                   : http://www.w3.org/2001/XMLSchema-instance
Source                : GPO
lang                  : en-US
Address               : *
Transport             : HTTP
Port                  : 5985
Hostname              :
Enabled               : true
URLPrefix             : wsman
CertificateThumbprint :
ListeningOn           : {}
```

### <a name="how-to-set-the-startup-type-of-the-winrm-service"></a>WinRM 서비스의 시작 유형을 설정 하는 방법

```
ERROR:  ACCESS IS DENIED
```

PowerShell remoting은 Windows 원격 관리 (WinRM) 서비스에 따라 달라 집니다.
원격 명령을 지원 하려면 서비스가 실행 중 이어야 합니다.

Windows의 서버 버전에서 WinRM (Windows 원격 관리) 서비스의 시작 유형은 자동입니다.

그러나 Windows의 클라이언트 버전에서는 WinRM 서비스가 기본적으로 사용 하지 않도록 설정 되어 있습니다.

원격 컴퓨터에서 서비스의 시작 유형을 설정 하려면 cmdlet을 사용 합니다 `Set-Service` .

여러 컴퓨터에서 명령을 실행 하려면 컴퓨터 이름의 텍스트 파일 또는 CSV 파일을 만들 수 있습니다.

예를 들어 다음 명령은 파일에서 컴퓨터 이름 목록을 가져온 `Servers.txt` 다음 모든 컴퓨터에서 WinRM 서비스의 시작 유형을 **자동** 으로 설정 합니다.

```powershell
$servers = Get-Content servers.txt
Set-Service WinRM -ComputerName $servers -startuptype Automatic
```

결과를 보려면 `Get-WMIObject` **Win32_Service** 개체와 함께 cmdlet을 사용 합니다. 자세한 내용은 [설정-서비스](xref:Microsoft.PowerShell.Management.Set-Service)를 참조 하세요.

### <a name="how-to-recreate-the-default-session-configurations"></a>기본 세션 구성을 다시 만드는 방법

```
ERROR:  ACCESS IS DENIED
```

로컬 컴퓨터에 연결 하 여 원격으로 명령을 실행 하려면 로컬 컴퓨터에 원격 명령에 대 한 세션 구성을 포함 해야 합니다.

를 사용 하면 `Enable-PSRemoting` 로컬 컴퓨터에 기본 세션 구성이 만들어집니다. 원격 사용자는 원격 명령이 **ConfigurationName** 매개 변수를 포함 하지 않을 때마다 이러한 세션 구성을 사용 합니다.

컴퓨터의 기본 구성이 등록 취소 되거나 삭제 된 경우 cmdlet을 사용 `Enable-PSRemoting` 하 여 다시 만듭니다. 이 cmdlet은 반복적으로 사용할 수 있습니다. 기능이 이미 구성 되어 있으면 오류를 생성 하지 않습니다.

기본 세션 구성을 변경 하 고 원래 기본 세션 구성을 복원 하려면 cmdlet을 사용 `Unregister-PSSessionConfiguration` 하 여 변경 된 세션 구성을 삭제 한 다음 cmdlet을 사용 하 여 `Enable-PSRemoting` 복원 합니다.
`Enable-PSRemoting` 기존 세션 구성을 변경 하지 않습니다.

> [!NOTE]
> 는 `Enable-PSRemoting` 기본 세션 구성을 복원할 때 구성에 대 한 명시적인 보안 설명자를 만들지 않습니다. 대신, 구성은 기본적으로 보안 되는 RootSDDL의 보안 설명자를 상속 합니다.

RootSDDL 보안 설명자를 표시 하려면 다음을 입력 합니다.

```powershell
Get-Item wsman:\localhost\Service\RootSDDL
```

RootSDDL를 변경 하려면 `Set-Item` WSMan: 드라이브에서 cmdlet을 사용 합니다. 세션 구성의 보안 설명자를 변경 하려면 `Set-PSSessionConfiguration` **SecurityDescriptorSDDL** 또는 **ShowSecurityDescriptorUI** 매개 변수와 함께 cmdlet을 사용 합니다.

WSMan: 드라이브에 대 한 자세한 내용은 WSMan 공급자에 대 한 도움말 항목 ("Get-help WSMan")을 참조 하십시오.

### <a name="how-to-provide-administrator-credentials"></a>관리자 자격 증명을 제공 하는 방법

```
ERROR:  ACCESS IS DENIED
```

PSSession을 만들거나 원격 컴퓨터에서 명령을 실행 하려면 기본적으로 현재 사용자가 원격 컴퓨터에서 Administrators 그룹의 구성원 이어야 합니다. 자격 증명은 현재 사용자가 Administrators 그룹의 구성원 인 계정에 로그온 한 경우에도 필요할 수 있습니다.

현재 사용자가 원격 컴퓨터에서 Administrators 그룹의 구성원 이거나 Administrators 그룹의 멤버 자격 증명을 제공할 수 있는 경우, 또는 cmdlet의 **Credential** 매개 변수를 사용 하 여 원격으로 `New-PSSession` `Enter-PSSession` `Invoke-Command` 연결 합니다.

예를 들어 다음 명령은 관리자의 자격 증명을 제공 합니다.

```powershell
Invoke-Command -ComputerName Server01 -Credential Domain01\Admin01
```

**Credential** 매개 변수에 대 한 자세한 내용은 [New-pssession](xref:Microsoft.PowerShell.Core.New-PSSession), [Enter-pssession](xref:Microsoft.PowerShell.Core.Enter-PSSession) 또는 [Invoke 명령을](xref:Microsoft.PowerShell.Core.Invoke-Command)참조 하세요.

### <a name="how-to-enable-remoting-for-non-administrative-users"></a>비관리자 사용자에 대해 원격 기능을 사용 하도록 설정 하는 방법

```
ERROR:  ACCESS IS DENIED
```

PSSession을 설정 하거나 원격 컴퓨터에서 명령을 실행 하려면 사용자가 원격 컴퓨터에서 세션 구성을 사용할 수 있는 권한이 있어야 합니다.

기본적으로 컴퓨터의 Administrators 그룹 구성원 에게만 기본 세션 구성을 사용할 수 있는 권한이 있습니다. 따라서 Administrators 그룹의 멤버만이 컴퓨터에 원격으로 연결할 수 있습니다.

다른 사용자가 로컬 컴퓨터에 연결할 수 있도록 하려면 로컬 컴퓨터의 기본 세션 구성에 대 한 실행 권한을 사용자에 게 부여 합니다.

다음 명령을 사용 하 여 로컬 컴퓨터에서 기본 Microsoft. PowerShell 세션 구성의 보안 설명자를 변경할 수 있는 속성 시트를 엽니다.

```powershell
Set-PSSessionConfiguration Microsoft.PowerShell -ShowSecurityDescriptorUI
```

자세한 내용은 [about_Session_Configurations](about_Session_Configurations.md)를 참조 하세요.

### <a name="how-to-enable-remoting-for-administrators-in-other-domains"></a>다른 도메인의 관리자가 원격 기능을 사용 하도록 설정 하는 방법

```
ERROR:  ACCESS IS DENIED
```

다른 도메인의 사용자가 로컬 컴퓨터에서 Administrators 그룹의 구성원이 면 사용자는 관리자 권한으로 로컬 컴퓨터에 원격으로 연결할 수 없습니다. 기본적으로 다른 도메인의 원격 연결은 표준 사용자 권한 토큰만 사용 하 여 실행 됩니다.

그러나 **LocalAccountTokenFilterPolicy** 레지스트리 항목을 사용 하 여 기본 동작을 변경 하 고 관리자 그룹의 멤버인 원격 사용자가 관리자 권한으로 실행할 수 있습니다.

> [!CAUTION]
> **LocalAccountTokenFilterPolicy** 항목은 영향을 받는 모든 컴퓨터의 모든 사용자에 대해 UAC (사용자 계정 컨트롤) 원격 제한을 사용 하지 않도록 설정 합니다. 정책을 변경 하기 전에이 설정의 영향을 신중 하 게 고려해 야 합니다.

정책을 변경 하려면 다음 명령을 사용 하 여 **LocalAccountTokenFilterPolicy** 레지스트리 항목의 값을 1로 설정 합니다.

```powershell
New-ItemProperty -Name LocalAccountTokenFilterPolicy `
  -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System `
  -PropertyType DWord -Value 1
```

### <a name="how-to-use-an-ip-address-in-a-remote-command"></a>원격 명령에서 ip 주소를 사용 하는 방법

```
ERROR: The WinRM client cannot process the request. If the authentication
scheme is different from Kerberos, or if the client computer is not joined to a
domain, then HTTPS transport must be used or the destination machine must be
added to the TrustedHosts configuration setting.
```

, Cmdlet의 **ComputerName** 매개 변수는 `New-PSSession` `Enter-PSSession` `Invoke-Command` IP 주소를 유효한 값으로 받아들입니다. 그러나 Kerberos 인증은 IP 주소를 지원 하지 않기 때문에 IP 주소를 지정할 때마다 기본적으로 NTLM 인증이 사용 됩니다.

NTLM 인증을 사용 하는 경우 원격 작업에 다음 절차가 필요 합니다.

1. HTTPS 전송을 사용할 컴퓨터를 구성 하거나 원격 컴퓨터의 IP 주소를 로컬 컴퓨터의 TrustedHosts 목록에 추가 합니다.

1. 모든 원격 명령에 **Credential** 매개 변수를 사용 합니다.

   현재 사용자의 자격 증명을 제출 하는 경우에도 필요 합니다.

### <a name="how-to-connect-remotely-from-a-workgroup-based-computer"></a>작업 그룹 기반 컴퓨터에서 원격으로 연결 하는 방법

```
ERROR: The WinRM client cannot process the request. If the authentication
scheme is different from Kerberos, or if the client computer is not joined to a
domain, then HTTPS transport must be used or the destination machine must be
added to the TrustedHosts configuration setting.
```

로컬 컴퓨터가 도메인에 있지 않은 경우 원격 작업에 다음 절차가 필요 합니다.

1. HTTPS 전송을 위해 컴퓨터를 구성 하거나 로컬 컴퓨터의 TrustedHosts 목록에 원격 컴퓨터의 이름을 추가 합니다.

1. 작업 그룹 기반 컴퓨터에 암호가 설정 되어 있는지 확인 합니다. 암호를 설정 하지 않거나 암호 값이 비어 있으면 원격 명령을 실행할 수 없습니다.

   사용자 계정에 대 한 암호를 설정 하려면 제어판의 사용자 계정을 사용 합니다.

1. 모든 원격 명령에 **Credential** 매개 변수를 사용 합니다.

   현재 사용자의 자격 증명을 제출 하는 경우에도 필요 합니다.

### <a name="how-to-add-a-computer-to-the-trusted-hosts-list"></a>신뢰할 수 있는 호스트 목록에 컴퓨터를 추가 하는 방법

TrustedHosts 항목은 컴퓨터 이름, IP 주소 및 정규화 된 도메인 이름의 쉼표로 구분 된 목록을 포함할 수 있습니다. 와일드카드가 지원됩니다.

신뢰할 수 있는 호스트 목록을 보거나 변경 하려면 WSMan: 드라이브를 사용 합니다. 호스트 항목이 `WSMan:\localhost\Client` 노드에 있습니다.

컴퓨터에서 Administrators 그룹의 구성원 에게만 컴퓨터의 신뢰할 수 있는 호스트 목록을 변경할 수 있는 권한이 있습니다.

주의: TrustedHosts 항목에 대해 설정한 값은 컴퓨터의 모든 사용자에 게 영향을 줍니다.

신뢰할 수 있는 호스트 목록을 보려면 다음 명령을 사용 합니다.

```powershell
Get-Item wsman:\localhost\Client\TrustedHosts
```

또한 `Set-Location` cmdlet (alias = cd)을 사용 하 여 WSMan: 드라이브에서 위치로 이동할 수 있습니다. 다음은 그 예입니다. 

```powershell
cd WSMan:\localhost\Client; dir
```

모든 컴퓨터를 신뢰할 수 있는 호스트 목록에 추가 하려면 다음 명령을 사용 합니다 .이 명령을 사용 하면 컴퓨터 이름에 * (모두) 값이 저장 됩니다.

```powershell
Set-Item wsman:localhost\client\trustedhosts -Value *
```

와일드 카드 문자 ()를 사용 `*` 하 여 특정 도메인의 모든 컴퓨터를 신뢰할 수 있는 호스트 목록에 추가할 수도 있습니다. 예를 들어 다음 명령은 Fabrikam 도메인의 모든 컴퓨터를 신뢰할 수 있는 호스트 목록에 추가 합니다.

```powershell
Set-Item wsman:localhost\client\trustedhosts *.fabrikam.com
```

특정 컴퓨터의 이름을 신뢰할 수 있는 호스트 목록에 추가 하려면 다음 명령 형식을 사용 합니다.

```powershell
Set-Item wsman:\localhost\Client\TrustedHosts -Value <ComputerName>
```

각 값 `<ComputerName>` 의 형식은 다음과 같아야 합니다.

```
<Computer>.<Domain>.<Company>.<top-level-domain>
```

다음은 그 예입니다. 

```powershell
$server = 'Server01.Domain01.Fabrikam.com'
Set-Item wsman:\localhost\Client\TrustedHosts -Value $server
```

컴퓨터 이름을 신뢰할 수 있는 호스트의 기존 목록에 추가 하려면 먼저 현재 값을 변수에 저장 한 다음 현재 값과 새 값을 포함 하는 쉼표로 구분 된 목록으로 값을 설정 합니다.

예를 들어 신뢰할 수 있는 호스트의 기존 목록에 Server01 컴퓨터를 추가 하려면 다음 명령을 사용 합니다.

```powershell
$curValue = (Get-Item wsman:\localhost\Client\TrustedHosts).value

Set-Item wsman:\localhost\Client\TrustedHosts -Value `
  "$curValue, Server01.Domain01.Fabrikam.com"
```

특정 컴퓨터의 IP 주소를 신뢰할 수 있는 호스트 목록에 추가 하려면 다음 명령 형식을 사용 합니다.

```powershell
Set-Item wsman:\localhost\Client\TrustedHosts -Value <IP Address>
```

다음은 그 예입니다. 

```powershell
Set-Item wsman:\localhost\Client\TrustedHosts -Value 172.16.0.0
```

원격 컴퓨터의 TrustedHosts 목록에 컴퓨터를 추가 하려면 cmdlet을 사용 하 여 `Connect-WSMan` 원격 컴퓨터의 노드를 로컬 컴퓨터의 WSMan: 드라이브에 추가 합니다. 그런 다음 `Set-Item` 명령을 사용 하 여 컴퓨터를 추가 합니다.

Cmdlet에 대 한 자세한 내용은 `Connect-WSMan` [연결-WSMan](xref:Microsoft.WSMan.Management.Connect-WSMan)을 참조 하세요.

## <a name="troubleshooting-computer-configuration-issues"></a>컴퓨터 구성 문제 해결

이 섹션에서는 컴퓨터, 도메인 또는 엔터프라이즈의 특정 구성과 관련 된 원격 문제에 대해 설명 합니다.

### <a name="how-to-configure-remoting-on-alternate-ports"></a>대체 포트에서 원격 기능을 구성 하는 방법

```
ERROR: The connection to the specified remote host was refused. Verify that the
WS-Management service is running on the remote host and configured to listen
for requests on the correct port and HTTP URL.
```

PowerShell remoting은 기본적으로 포트 80를 HTTP 전송에 사용 합니다. 사용자가 원격 명령에서 **Connectionuri** 또는 **포트** 매개 변수를 지정 하지 않을 때마다 기본 포트가 사용 됩니다.

PowerShell에서 사용 하는 기본 포트를 변경 하려면 `Set-Item` WSMan: 드라이브에서 cmdlet을 사용 하 여 수신기 리프 노드의 포트 값을 변경 합니다.

예를 들어 다음 명령은 기본 포트를 8080로 변경 합니다.

```powershell
Set-Item wsman:\localhost\listener\listener*\port -Value 8080
```

### <a name="how-to-configure-remoting-with-a-proxy-server"></a>프록시 서버를 사용 하 여 원격을 구성 하는 방법

```
ERROR: The client cannot connect to the destination specified in the request.
Verify that the service on the destination is running and is accepting
requests.
```

PowerShell remoting은 HTTP 프로토콜을 사용 하므로 HTTP 프록시 설정의 영향을 받습니다. 프록시 서버가 있는 기업은 사용자가 PowerShell 원격 컴퓨터에 직접 액세스할 수 없습니다.

이 문제를 해결 하려면 원격 명령의 프록시 설정 옵션을 사용 합니다. 다음 설정을 사용할 수 있습니다.

- System.management.automation.remoting.proxyaccesstype
- ProxyAuthentication
- ProxyCredential

특정 명령에 대해 이러한 옵션을 설정 하려면 다음 절차를 따르십시오.

1. Cmdlet의 **system.management.automation.remoting.proxyaccesstype** , **Proxyauthentication** 및 **ProxyCredential** 매개 변수를 사용 `New-PSSessionOption` 하 여 엔터프라이즈에 대 한 프록시 설정을 사용 하 여 세션 옵션 개체를 만듭니다. 옵션 개체는 변수를 저장 합니다.

1. Option 개체를 포함 하는 변수를, 또는 명령의 **sessionoption** 매개 변수 값으로 사용 `New-PSSession` `Enter-PSSession` `Invoke-Command` 합니다.

예를 들어 다음 명령은 프록시 세션 옵션을 사용 하 여 세션 옵션 개체를 만든 다음 개체를 사용 하 여 원격 세션을 만듭니다.

```powershell
$SessionOption = New-PSSessionOption -ProxyAccessType IEConfig `
-ProxyAuthentication Negotiate -ProxyCredential Domain01\User01

New-PSSession -ConnectionURI https://www.fabrikam.com
```

Cmdlet에 대 한 자세한 내용은 `New-PSSessionOption` [New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption)을 참조 하세요.

현재 세션의 모든 원격 명령에 대해 이러한 옵션을 설정 하려면 `New-PSSessionOption` 기본 설정 변수 값에 생성 되는 option 개체를 사용 `$PSSessionOption` 합니다. 자세한 내용은 [about_Preference_Variables](about_Preference_Variables.md)를 참조 하세요.

모든 원격 명령에 대 한 이러한 옵션을 로컬 컴퓨터의 모든 PowerShell 세션에 설정 하려면 `$PSSessionOption` 기본 설정 변수를 powershell 프로필에 추가 합니다. PowerShell 프로필에 대 한 자세한 내용은 [about_Profiles](about_Profiles.md)를 참조 하세요.

### <a name="how-to-detect-a-32-bit-session-on-a-64-bit-computer"></a>64 비트 컴퓨터에서 32 비트 세션을 검색 하는 방법

```
ERROR: The term "<tool-Name>" is not recognized as the name of a cmdlet,
function, script file, or operable program. Check the spelling of the name, or
if a path was included, verify that the path is correct and try again.
```

원격 컴퓨터에서 64 비트 버전의 Windows를 실행 중이 고 원격 명령이 32 비트 세션 구성을 사용 하는 경우 (예: Microsoft.powershell32 Windows 원격 관리 (WinRM) WOW64 프로세스를 로드 하 고 Windows에서 디렉터리에 대 한 모든 참조를 디렉터리로 자동으로 리디렉션합니다 `$env:Windir\System32` `$env:Windir\SysWOW64` .

결과적으로, System32 디렉터리에 해당 하는 도구를 사용 하려고 할 때 (예:) `Defrag.exe` 디렉터리에서 도구를 찾을 수 없습니다.

세션에 사용 되는 프로세서 아키텍처를 찾으려면 **PROCESSOR_ARCHITECTURE** 환경 변수의 값을 사용 합니다. 다음 명령은 변수에서 세션의 프로세서 아키텍처를 찾습니다 `$s` .

```powershell
$s = New-PSSession -ComputerName Server01 -ConfigurationName CustomShell
Invoke-Command -Session $s {$env:PROCESSOR_ARCHITECTURE}
```

```Output
x86
```

세션 구성에 대 한 자세한 내용은 [about_Session_Configurations](about_Session_Configurations.md)를 참조 하세요.

## <a name="troubleshooting-policy-and-preference-issues"></a>정책 및 기본 설정 문제 해결

이 섹션에서는 로컬 및 원격 컴퓨터에 설정 된 정책 및 기본 설정과 관련 된 원격 문제에 대해 설명 합니다.

### <a name="how-to-change-the-execution-policy-for-import-pssession-and-import-module"></a>Import-PSSession 및 Import-Module에 대 한 실행 정책을 변경 하는 방법

```
ERROR: Import-Module: File <filename> cannot be loaded because the
execution of scripts is disabled on this system.
```

`Import-PSSession`및 `Export-PSSession` cmdlet은 서명 되지 않은 스크립트 파일 및 형식 지정 파일을 포함 하는 모듈을 만듭니다.

또는를 사용 하 여 이러한 cmdlet에서 만든 모듈을 가져오려면 `Import-PSSession` `Import-Module` 현재 세션의 실행 정책을 제한 하거나 AllSigned 수 없습니다. PowerShell 실행 정책에 대 한 자세한 내용은 [about_Execution_Policies](about_Execution_Policies.md)를 참조 하세요.

레지스트리에 설정 된 로컬 컴퓨터에 대 한 실행 정책을 변경 하지 않고 모듈을 가져오려면의 **Scope** 매개 변수를 사용 `Set-ExecutionPolicy` 하 여 단일 프로세스에 대 한 덜 제한적인 실행 정책을 설정 합니다.

예를 들어 다음 명령은 실행 정책으로 프로세스를 시작 합니다 `RemoteSigned` . 실행 정책 변경 내용은 현재 프로세스에만 영향을 미치고 PowerShell **set-executionpolicy** 레지스트리 설정을 변경 하지 않습니다.

```powershell
Set-ExecutionPolicy -Scope process -ExecutionPolicy RemoteSigned
```

의 **set-executionpolicy** 매개 변수를 사용 하 여 `PowerShell.exe` 덜 제한적인 실행 정책으로 단일 세션을 시작할 수도 있습니다.

```powershell
PowerShell.exe -ExecutionPolicy RemoteSigned
```

실행 정책에 대 한 자세한 내용은 [about_Execution_Policies](about_Execution_Policies.md)를 참조 하세요. 자세한 내용을 보려면 `PowerShell.exe -?`를 입력하십시오.

### <a name="how-to-set-and-change-quotas"></a>할당량을 설정 및 변경 하는 방법

```
ERROR: The total data received from the remote client exceeded allowed
maximum.
```

할당량을 사용 하 여 로컬 컴퓨터와 원격 컴퓨터를 과도 한 리소스 사용 (예를 들어, 우발적인 및 악성) 으로부터 보호할 수 있습니다.

다음 할당량은 기본 구성에서 사용할 수 있습니다.

- Wsman 공급자 (WSMan:) 노드의 **MaxEnvelopeSizeKB** 및 **maxproviderrequests** 설정, 노드의 `WSMan:<ComputerName>` **MaxConcurrentOperations** , **MaxConcurrentOperationsPerUser** 및 **MaxConnections** 설정과 같은 몇 가지 할당량 설정을 제공 합니다 `WSMan:<ComputerName>\Service` .

- Cmdlet의 **MaximumReceivedDataSizePerCommand** 및 **MaximumReceivedObjectSize** 매개 변수와 `New-PSSessionOption` 기본 설정 변수를 사용 하 여 로컬 컴퓨터를 보호할 수 있습니다 `$PSSessionOption` .

- Cmdlet의 **MaximumReceivedDataSizePerCommandMB** 및 **MaximumReceivedObjectSizeMB** 매개 변수를 사용 하는 등의 방법으로 세션 구성에 제한을 추가 하 여 원격 컴퓨터를 보호할 수 있습니다 `Register-PSSessionConfiguration` .

할당량이 명령과 충돌 하는 경우 PowerShell에서 오류를 생성 합니다.

이 오류를 해결 하려면 할당량을 준수 하도록 원격 명령을 변경 합니다. 또는 할당량의 원본을 확인 하 고 할당량을 늘려 명령이 완료 될 수 있도록 합니다.

예를 들어 다음 명령은 원격 컴퓨터의 Microsoft PowerShell 세션 구성에 있는 개체 크기 할당량을 10mb (기본값)에서 11mb로 늘립니다.

```powershell
Set-PSSessionConfiguration -Name microsoft.PowerShell `
  -MaximumReceivedObjectSizeMB 11 -Force
```

Cmdlet에 대 한 자세한 내용은 `New-PSSessionOption` 을 참조 하십시오 `New-PSSessionOption` .

WS-Management 할당량에 대 한 자세한 내용은 [about_WSMan_Provider](../../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)을 참조 하세요.

### <a name="how-to-resolve-timeout-errors"></a>시간 제한 오류를 해결 하는 방법

```
ERROR: The WS-Management service cannot complete the operation within
the time specified in OperationTimeout.
```

제한 시간을 사용 하 여 로컬 컴퓨터와 원격 컴퓨터를 과도 하 게 사용 하는 컴퓨터와 악의적인 리소스를 사용 하지 않도록 보호할 수 있습니다. 로컬 및 원격 컴퓨터 모두에 시간 초과가 설정 된 경우 PowerShell에서 가장 짧은 시간 제한 설정을 사용 합니다.

다음 시간 제한은 기본 구성에서 사용할 수 있습니다.

- Wsman 공급자 (WSMan:) 노드의 **Maxtimeoutms** 설정, 노드의 `WSMan:<ComputerName>` **Enumerationtimeoutms** 및 **MaxPacketRetrievalTimeSeconds** 설정과 같은 여러 클라이언트 쪽 및 서비스 쪽 제한 시간 설정을 제공 합니다 `WSMan:<ComputerName>\Service` .

- Cmdlet의 **canceltimeout** , **IdleTimeout** , **OpenTimeout** 및 **operationtimeout** 매개 변수와 `New-PSSessionOption` `$PSSessionOption` 기본 설정 변수를 사용 하 여 로컬 컴퓨터를 보호할 수 있습니다.

- 세션에 대 한 세션 구성에서 프로그래밍 방식으로 시간 제한 값을 설정 하 여 원격 컴퓨터를 보호할 수도 있습니다.

시간 제한 값으로 작업이 완료 되는 것을 허용 하지 않으면 PowerShell에서 작업을 종료 하 고 오류를 생성 합니다.

오류를 해결 하려면 시간 제한 간격 내에 명령을 완료로 변경 하거나 시간 제한의 원본을 확인 하 고 제한 시간 간격을 늘려 명령이 완료 될 수 있도록 합니다.

예를 들어 다음 명령은 cmdlet을 사용 `New-PSSessionOption` 하 여 **operationtimeout** 값이 4 분 (밀리초) 인 세션 옵션 개체를 만든 다음 세션 옵션 개체를 사용 하 여 원격 세션을 만듭니다.

```powershell
$pso = New-PSSessionoption -OperationTimeout 240000

New-PSSession -ComputerName Server01 -sessionOption $pso
```

WS-Management 제한 시간에 대 한 자세한 내용은 WSMan 공급자 (유형)에 대 한 도움말 항목을 참조 하십시오 `Get-Help WSMan` .

Cmdlet에 대 한 자세한 내용은 `New-PSSessionOption` [New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption)을 참조 하세요.

## <a name="troubleshooting-unresponsive-behavior"></a>응답 하지 않는 동작 문제 해결

이 섹션에서는 명령이 완료 되지 않도록 하 고 PowerShell 프롬프트의 반환을 방지 하거나 지연 하는 원격 문제에 대해 설명 합니다.

### <a name="how-to-interrupt-a-command"></a>명령을 중단 하는 방법

사용자 인터페이스가 있는 프로그램, 입력을 요청 하는 콘솔 응용 프로그램, Win32 콘솔 API를 사용 하는 콘솔 응용 프로그램 등의 일부 네이티브 Windows 프로그램은 PowerShell 원격 호스트에서 제대로 작동 하지 않습니다.

이러한 프로그램을 사용 하는 경우 출력 없음, 부분 출력 또는 완료 되지 않은 원격 명령과 같은 예기치 않은 동작이 나타날 수 있습니다.

응답 하지 않는 프로그램을 종료 하려면 <kbd>CTRL</kbd> + <kbd>C</kbd>를 입력 합니다. 보고 되었을 수 있는 모든 오류를 보려면 `$error` 로컬 호스트와 원격 세션에를 입력 합니다.

## <a name="how-to-recover-from-an-operation-failure"></a>작업 오류에서 복구 하는 방법

```
ERROR: The I/O operation has been aborted because of either a thread exit
or an  application request.
```

작업이 완료 되기 전에 종료 되 면이 오류가 반환 됩니다.
일반적으로 다른 WinRM 작업이 진행 되는 동안 WinRM 서비스를 중지 하거나 다시 시작할 때 발생 합니다.

이 문제를 해결 하려면 WinRM 서비스가 실행 중인지 확인 하 고 명령을 다시 시도 하십시오.

1. **관리자 권한으로 실행** 옵션을 사용 하 여 PowerShell을 시작 합니다.
1. 다음 명령을 실행합니다.

   `Start-Service WinRM`

1. 오류를 생성 한 명령을 다시 실행 합니다.

## <a name="linux-and-macos-limitations"></a>Linux 및 macOS 제한 사항

### <a name="authentication"></a>인증

MacOS에서 기본 인증만 작동 하 고 다른 인증 체계를 사용 하려고 하면 프로세스가 충돌을 일으킬 수 있습니다.

[OMI 인증](https://github.com/PowerShell/psl-omi-provider#connecting-from-linux-to-windows) 지침을 참조 하세요.

## <a name="see-also"></a>참고 항목

[Import-PSSession](xref:Microsoft.PowerShell.Utility.Import-PSSession)

[Export-PSSession](xref:Microsoft.PowerShell.Utility.Export-PSSession)

[모듈 가져오기](xref:Microsoft.PowerShell.Core.Import-Module)

[about_Remote](about_Remote.md)

[about_Remote_Requirements](about_Remote_Requirements.md)

[about_Remote_Variables](about_Remote_Variables.md)
