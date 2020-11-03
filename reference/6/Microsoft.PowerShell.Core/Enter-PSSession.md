---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 07/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enter-pssession?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enter-PSSession
ms.openlocfilehash: 3b087eb53fa575b2af7b18ec17823f9197e719d6
ms.sourcegitcommit: 9dddf1d2e91ebcd347fcfb7bf6ef670d49a12ab7
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/24/2020
ms.locfileid: "93218938"
---
# Enter-PSSession

## 개요
원격 컴퓨터와 대화형 세션을 시작합니다.

## SYNTAX

### ComputerName (기본값)

```
Enter-PSSession [-ComputerName] <String> [-EnableNetworkAccess] [[-Credential] <PSCredential>]
 [-ConfigurationName <String>] [-Port <Int32>] [-UseSSL] [-ApplicationName <String>]
 [-SessionOption <PSSessionOption>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [<CommonParameters>]
```

### SSHHost

```
Enter-PSSession [-HostName] <String> [-Port <Int32>] [-UserName <String>] [-KeyFilePath <String>]
 [-SSHTransport] [<CommonParameters>]
```

### 세션

```
Enter-PSSession [[-Session] <PSSession>] [<CommonParameters>]
```

### URI

```
Enter-PSSession [[-ConnectionUri] <Uri>] [-EnableNetworkAccess] [[-Credential] <PSCredential>]
 [-ConfigurationName <String>] [-AllowRedirection] [-SessionOption <PSSessionOption>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

### InstanceId

```
Enter-PSSession [-InstanceId <Guid>] [<CommonParameters>]
```

### Id

```
Enter-PSSession [[-Id] <Int32>] [<CommonParameters>]
```

### Name

```
Enter-PSSession [-Name <String>] [<CommonParameters>]
```

### VMId

```
Enter-PSSession [-VMId] <Guid> [-Credential] <PSCredential> [-ConfigurationName <String>] [<CommonParameters>]
```

### VMName

```
Enter-PSSession [-VMName] <String> [-Credential] <PSCredential> [-ConfigurationName <String>]
 [<CommonParameters>]
```

### ContainerId

```
Enter-PSSession [-ContainerId] <String> [-ConfigurationName <String>] [-RunAsAdministrator]
 [<CommonParameters>]
```

## 설명

`Enter-PSSession`Cmdlet은 단일 원격 컴퓨터와 대화형 세션을 시작 합니다.
세션 중에 입력 하는 명령은 원격 컴퓨터에서 직접 입력 하는 것 처럼 원격 컴퓨터에서 실행 됩니다. 한 번에 하나의 대화형 세션만 사용할 수 있습니다.

일반적으로 **ComputerName** 매개 변수를 사용하여 원격 컴퓨터의 이름을 지정합니다.
그러나 대화형 세션에 cmdlet을 사용 하 여 만든 세션을 사용할 수도 있습니다 `New-PSSession` . 그러나 `Disconnect-PSSession` , `Connect-PSSession` 또는 cmdlet을 사용 하 여 `Receive-PSSession` 대화형 세션에서 연결을 끊거나 다시 연결할 수는 없습니다.

PowerShell 6.0부터 ssh (Secure Shell)를 사용 하 여 원격 컴퓨터에 대 한 연결을 설정 하 고, SSH를 로컬 컴퓨터에서 사용할 수 있고, 원격 컴퓨터가 PowerShell SSH 끝점을 사용 하 여 구성 된 경우 원격 컴퓨터에 연결할 수 있습니다. SSH 기반 PowerShell 원격 세션의 혜택은 여러 플랫폼 (Windows, Linux, macOS)에서 작동 한다는 것입니다. SSH 기반 원격의 경우 **HostName** 매개 변수 집합을 사용 하 여 원격 컴퓨터 및 관련 연결 정보를 지정 합니다. PowerShell SSH 원격을 설정 하는 방법에 대 한 자세한 내용은 [ssh를 통한 Powershell 원격](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core)을 참조 하세요.

대화형 세션을 종료 하 고 원격 컴퓨터와의 연결을 끊으려면 `Exit-PSSession` cmdlet을 사용 하거나를 입력 `exit` 합니다.

## 예제

### 예제 1: 대화형 세션 시작

```
PS> Enter-PSSession
[localhost]: PS>
```

이 명령은 로컬 컴퓨터에서 대화형 세션을 시작합니다. 명령 프롬프트가 변경되어 현재 다른 세션에서 명령을 실행하고 있음을 나타냅니다.

입력한 명령은 새 세션에서 실행되고 결과가 기본 세션에 텍스트로 반환됩니다.

### 예제 2: 대화형 세션 작업

첫 번째 명령은 cmdlet을 사용 하 여 `Enter-PSSession` Server01, 원격 컴퓨터와 대화형 세션을 시작 합니다. 세션이 시작되면 명령 프롬프트가 변경되어 컴퓨터 이름을 포함합니다.

두 번째 명령은 PowerShell 프로세스를 가져오고 출력을 Process.txt 파일로 리디렉션합니다. 이 명령은 원격 컴퓨터에 전송되고 Process.txt 파일이 원격 컴퓨터에 저장됩니다.

세 번째 명령은 **Exit** 키워드를 사용 하 여 대화형 세션을 종료 하 고 연결을 닫습니다.
네 번째 명령은 Process.txt 파일이 원격 컴퓨터에 있는지 확인합니다. `Get-ChildItem`로컬 컴퓨터의 ("dir") 명령으로 파일을 찾을 수 없습니다.

```powershell
PS C:\> Enter-PSSession -ComputerName Server01
[Server01]: PS>
[Server01]: PS C:\> Get-Process PowerShell > C:\ps-test\Process.txt
[Server01]: PS C:\> exit
PS C:\>
PS C:\> dir C:\ps-test\process.txt
Get-ChildItem : Cannot find path 'C:\ps-test\process.txt' because it does not exist.
At line:1 char:4
+ dir <<<<  c:\ps-test\process.txt
```

이 명령은 원격 컴퓨터와의 대화형 세션에서 작업하는 방법을 보여 줍니다.

### 예 3: Session 매개 변수 사용

```powershell
PS> $s = New-PSSession -ComputerName Server01
PS> Enter-PSSession -Session $s
[Server01]: PS>
```

이러한 명령은의 **Session** 매개 변수를 사용 `Enter-PSSession` 하 여 기존 PowerShell 세션 ( **PSSession** )에서 대화형 세션을 실행 합니다.

### 예 4: 대화형 세션을 시작 하 고 포트 및 자격 증명 매개 변수 지정

```powershell
PS> Enter-PSSession -ComputerName Server01 -Port 90 -Credential Domain01\User01
[Server01]: PS>
```

이 명령은 Server01 컴퓨터와 대화형 세션을 시작합니다. **Port** 매개 변수를 사용 하 여 포트를 지정 하 고 **Credential** 매개 변수를 사용 하 여 원격 컴퓨터에 연결할 수 있는 권한을 가진 사용자의 계정을 지정 합니다.

### 예 5: 대화형 세션 중지

```powershell
PS> Enter-PSSession -ComputerName Server01
[Server01]: PS> Exit-PSSession
PS>
```

이 예제에서는 대화형 세션을 시작하고 중지하는 방법을 보여 줍니다. 첫 번째 명령은 cmdlet을 사용 하 여 `Enter-PSSession` Server01 컴퓨터와 대화형 세션을 시작 합니다.

두 번째 명령은 cmdlet을 사용 하 여 `Exit-PSSession` 세션을 종료 합니다. **Exit** 키워드를 사용 하 여 대화형 세션을 종료할 수도 있습니다. `Exit-PSSession` 및 **종료** 는 동일한 효과를 가집니다.

### 예제 6: SSH를 사용 하 여 대화형 세션 시작

```powershell
PS> Enter-PSSession -HostName UserA@LinuxServer01
```

이 예제에서는 Secure Shell (SSH)를 사용 하 여 대화형 세션을 시작 하는 방법을 보여 줍니다. SSH가 원격 컴퓨터에서 암호를 묻는 메시지를 표시 하도록 구성 된 경우 암호를 입력 하 라는 메시지가 표시 됩니다.
그렇지 않은 경우에는 SSH 키 기반 사용자 인증을 사용 해야 합니다.

### 예 7: SSH를 사용 하 여 대화형 세션을 시작 하 고 포트 및 사용자 인증 키 지정

```powershell
PS> Enter-PSSession -HostName UserA@LinuxServer02:22 -KeyFilePath c:\<path>\userAKey_rsa
```

이 예제에서는 SSH를 사용 하 여 대화형 세션을 시작 하는 방법을 보여 줍니다. **Port** 매개 변수를 사용 하 여 사용할 포트를 지정 하 고 **keyfilepath** 매개 변수를 사용 하 여 원격 컴퓨터에서 사용자를 인증 하는 데 사용 되는 RSA 키를 지정 합니다.

## PARAMETERS

### -AllowRedirection

이 연결을 대체 URI(Uniform Resource Identifier)로 리디렉션할 수 있도록 허용합니다. 기본적으로 리디렉션은 사용할 수 없습니다.

**ConnectionURI** 매개 변수를 사용하면 원격 대상에서 다른 URI로 리디렉션하는 명령을 반환할 수 있습니다. 기본적으로 PowerShell은 연결을 리디렉션하지 않지만이 매개 변수를 사용 하 여 연결을 리디렉션할 수 있습니다.

또한 **MaximumConnectionRedirectionCount** 세션 옵션 값을 변경하여 연결이 리디렉션되는 횟수를 제한할 수도 있습니다. Cmdlet의 **Maximumredirection** 매개 변수를 사용 `New-PSSessionOption` 하거나 기본 설정 변수의 **MaximumConnectionRedirectionCount** 속성을 설정 `$PSSessionOption` 합니다. 기본값은 5입니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Uri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ApplicationName

연결 URI의 애플리케이션 이름 세그먼트를 지정합니다. 명령에서 **ConnectionURI**  매개 변수를 사용하지 않는 경우 이 매개 변수를 사용하여 응용 프로그램 이름을 지정할 수 있습니다.

기본값은 `$PSSessionApplicationName` 로컬 컴퓨터의 기본 설정 변수 값입니다. 이 기본 설정 변수를 정의하지 않으면 WSMAN이 기본값으로 사용됩니다. 이 값은 대부분의 사용에 적합합니다. 자세한 내용은 [about_Preference_Variables](About/about_Preference_Variables.md)를 참조 하세요.

**WinRM** 서비스는 응용 프로그램 이름을 사용 하 여 연결 요청을 처리 하는 수신기를 선택 합니다. 이 매개 변수 값은 원격 컴퓨터에 있는 수신기의 **URLPrefix** 속성 값과 일치해야 합니다.

```yaml
Type: System.String
Parameter Sets: ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -인증

사용자 자격 증명을 인증하는 데 사용되는 메커니즘을 지정합니다. 이 매개 변수에 허용되는 값은 다음과 같습니다.

- 기본값
- Basic
- Credssp
- 다이제스트
- Kerberos
- Negotiate
- NegotiateWithImplicitCredential

기본값은 Default입니다.

CredSSP 인증은 windows Vista, Windows Server 2008 이상 버전의 Windows 운영 체제 에서만 사용할 수 있습니다.

이 매개 변수 값에 대 한 자세한 내용은 [Authenticationmechanism 열거형](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)을 참조 하세요.

주의: 사용자의 자격 증명이 인증을 위해 원격 컴퓨터에 전달 되는 CredSSP (자격 증명 보안 지원 공급자) 인증은 원격 네트워크 공유에 액세스 하는 것과 같이 둘 이상의 리소스에서 인증이 필요한 명령에 대해 설계 되었습니다. 이렇게 하면 원격 작업의 보안 위험이 커집니다. 원격 컴퓨터가 손상된 경우 이 컴퓨터로 전달된 자격 증명을 사용하여 네트워크 세션을 제어할 수 있습니다.

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ComputerName, Uri
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CertificateThumbprint

이 작업을 수행할 권한이 있는 사용자 계정의 디지털 공개 키 인증서(X509)를 지정합니다. 인증서의 인증서 지문을 입력합니다.

인증서는 클라이언트 인증서 기반 인증에 사용됩니다. 인증서는 로컬 사용자 계정에만 매핑할 수 있으며 도메인 계정에는 사용할 수 없습니다.

인증서를 가져오려면 `Get-Item` `Get-ChildItem` PowerShell Cert: 드라이브에서 또는 명령을 사용 합니다.

```yaml
Type: System.String
Parameter Sets: ComputerName, Uri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

컴퓨터 이름을 지정 합니다. 이 cmdlet은 지정 된 원격 컴퓨터와의 대화형 세션을 시작 합니다. 컴퓨터 이름을 하나만 입력하세요. 기본값은 로컬 컴퓨터입니다.

컴퓨터의 NetBIOS 이름, IP 주소 또는 정규화된 도메인 이름을 입력하세요. 컴퓨터 이름을로 파이프 할 수도 있습니다 `Enter-PSSession` .

**ComputerName** 매개 변수 값에 IP 주소를 사용 하려면 명령에 **Credential** 매개 변수를 포함 해야 합니다. 또한 HTTPS 전송을 사용하도록 컴퓨터를 구성하거나 원격 컴퓨터의 IP 주소를 로컬 컴퓨터의 WinRM TrustedHosts 목록에 포함해야 합니다. TrustedHosts 목록에 컴퓨터 이름을 추가 하는 방법에 대 한 지침은 [about_Remote_Troubleshooting](About/about_Remote_Troubleshooting.md)의 "신뢰할 수 있는 호스트 목록에 컴퓨터를 추가 하는 방법"을 참조 하십시오.

참고: Windows Vista 이상 버전의 Windows 운영 체제에서 **ComputerName** 매개 변수 값에 로컬 컴퓨터를 포함 하려면 관리자 권한으로 실행 옵션을 사용 하 여 PowerShell을 시작 해야 합니다.

```yaml
Type: System.String
Parameter Sets: ComputerName
Aliases: Cn

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -ConfigurationName

대화형 세션에 사용할 세션 구성을 지정합니다.

세션 구성의 구성 이름 또는 정규화된 리소스 URI를 입력합니다. 구성 이름만 지정 하는 경우에는 다음 스키마 URI가 앞에와 야 `http://schemas.microsoft.com/powershell` 합니다.

SSH와 함께 사용 하는 경우 sshd_config에 정의 된 대로 대상에서 사용할 하위 시스템을 지정 합니다. SSH의 기본값은 `powershell` 하위 시스템입니다.

세션의 세션 구성은 원격 컴퓨터에 있습니다. 지정된 세션 구성이 원격 컴퓨터에 없으면 명령이 실패합니다.

기본값은 `$PSSessionConfigurationName` 로컬 컴퓨터의 기본 설정 변수 값입니다. 이 기본 설정 변수를 설정하지 않으면 Microsoft.PowerShell이 기본값으로 사용됩니다. 자세한 내용은 [about_Preference_Variables](About/about_Preference_Variables.md)를 참조 하세요.

```yaml
Type: System.String
Parameter Sets: ComputerName, Uri, VMId, VMName, ContainerId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ConnectionUri

세션에 대 한 연결 끝점을 정의 하는 URI를 지정 합니다. URI는 정규화된 URI여야 합니다. 이 문자열의 형식은 다음과 같습니다.

`<Transport>://<ComputerName>:<Port>/<ApplicationName>`

기본값은 다음과 같습니다.

`http://localhost:5985/WSMAN`

**ConnectionURI** 를 지정하지 않은 경우 **UseSSL** , **ComputerName** , **Port** 및 **ApplicationName** 매개 변수를 사용하여 **ConnectionURI** 값을 지정할 수 있습니다.

URI의 전송 세그먼트에 유효한 값은 HTTP 및 HTTPS입니다. 전송 세그먼트를 사용 하 여 연결 URI를 지정 하 고 포트를 지정 하지 않으면 세션은 표준 포트 80 (HTTP의 경우, HTTPS의 경우 443)를 사용 하 여 만들어집니다. PowerShell 원격을 위한 기본 포트를 사용 하려면 HTTP의 경우 포트 5985을, HTTPS의 경우 5986을 지정 합니다.

대상 컴퓨터에서 연결을 다른 URI로 리디렉션하는 경우 명령에서 **allowredirection** 매개 변수를 사용 하지 않으면 PowerShell에서 리디렉션을 방지 합니다.

```yaml
Type: System.Uri
Parameter Sets: Uri
Aliases: URI, CU

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ContainerId

컨테이너의 ID를 지정 합니다.

```yaml
Type: System.String
Parameter Sets: ContainerId
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Credential

이 작업을 수행할 권한이 있는 사용자 계정을 지정합니다. 기본값은 현재 사용자입니다.

**User01** 또는 **Domain01\User01** 과 같은 사용자 이름을 입력 하거나 cmdlet에 의해 생성 된 **PSCredential** 개체를 입력 합니다 `Get-Credential` . 사용자 이름을 입력 하면 암호를 입력 하 라는 메시지가 표시 됩니다.

자격 증명은 [PSCredential](/dotnet/api/system.management.automation.pscredential) 개체에 저장 되 고 암호는 [SecureString](/dotnet/api/system.security.securestring)으로 저장 됩니다.

> [!NOTE]
> **Securestring** 데이터 보호에 대 한 자세한 [내용은 참조 하십시오](/dotnet/api/system.security.securestring#how-secure-is-securestring).

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerName, Uri, VMId, VMName
Aliases:

Required: True (VMId, VMName), False (ComputerName, Uri)
Position: 1
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -EnableNetworkAccess

이 cmdlet이 루프백 세션에 대화형 보안 토큰을 추가 함을 나타냅니다. 대화형 토큰을 사용하면 다른 컴퓨터에서 데이터를 가져오는 명령을 루프백 세션에서 실행할 수 있습니다. 예를 들어 원격 컴퓨터에서 로컬 컴퓨터로 XML 파일을 복사하는 세션에서 명령을 실행할 수 있습니다.

루프백 세션은 동일한 컴퓨터에서 시작 하 여 종료 되는 **PSSession** 입니다. 루프백 세션을 만들려면 **ComputerName** 매개 변수를 생략 하거나 값을로 설정 합니다. (점), localhost 또는 로컬 컴퓨터의 이름입니다.

기본적으로 루프백 세션은 원격 컴퓨터를 인증 하는 데 충분 한 권한을 제공 하지 않을 수 있는 네트워크 토큰을 사용 하 여 생성 됩니다.

**EnableNetworkAccess** 매개 변수는 루프백 세션에서만 유효합니다. 원격 컴퓨터에서 세션을 만들 때 **EnableNetworkAccess** 를 사용 하는 경우 명령은 성공 하지만 매개 변수는 무시 됩니다.

또한 세션 자격 증명을 다른 컴퓨터에 위임하는 **CredSSP** 매개 변수의 **Authentication** 값을 사용하여 루프백 세션에서 원격 액세스를 허용할 수도 있습니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName, Uri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -HostName

SSH (Secure Shell) 기반 연결에 대 한 컴퓨터 이름을 지정 합니다. 이는 원격 컴퓨터에 대 한 연결이 Windows WinRM이 아닌 SSH를 사용 하는 경우를 제외 하 고 **ComputerName** 매개 변수와 비슷합니다. 이 매개 변수는 형식을 사용 하 여 호스트 이름 매개 변수 값의 일부로 사용자 이름 및/또는 포트를 지정 하도록 지원 합니다 `user@hostname:port` . 호스트 이름의 일부로 지정 된 사용자 이름 및/또는 포트가 `-UserName` 지정 된 경우 및 매개 변수 보다 우선적으로 적용 `-Port` 됩니다. 이를 통해 특정 사용자 이름 및/또는 포트를 포함 하는 여러 컴퓨터 이름을이 매개 변수에 전달할 수 있으며, 다른 사용자 이름 및/또는 포트는 `-UserName` 및 매개 변수에서 사용할 수 있습니다 `-Port` .

이 매개 변수는 PowerShell 6.0에서 도입 되었습니다.

```yaml
Type: System.String
Parameter Sets: SSHHost
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Id

기존 세션의 ID를 지정합니다. `Enter-PSSession` 대화형 세션에 대해 지정 된 세션을 사용 합니다.

세션의 ID를 찾으려면 cmdlet을 사용 합니다 `Get-PSSession` .

```yaml
Type: System.Int32
Parameter Sets: Id
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -InstanceId

기존 세션의 인스턴스 ID를 지정합니다. `Enter-PSSession` 대화형 세션에 대해 지정 된 세션을 사용 합니다.

인스턴스 ID는 GUID입니다. 세션의 인스턴스 ID를 확인 하려면 cmdlet을 사용 합니다 `Get-PSSession` . **Session** , **Name** 또는 **ID** 매개 변수를 사용 하 여 기존 세션을 지정할 수도 있습니다. 또는 **ComputerName** 매개 변수를 사용 하 여 임시 세션을 시작할 수 있습니다.

```yaml
Type: System.Guid
Parameter Sets: InstanceId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -KeyFilePath

SSH (Secure Shell)에서 원격 컴퓨터의 사용자를 인증 하는 데 사용 하는 키 파일 경로를 지정 합니다.

SSH를 사용 하면 기본 암호 인증 대신 개인/공개 키를 통해 사용자 인증을 수행할 수 있습니다. 키 인증을 사용 하도록 원격 컴퓨터를 구성 하는 경우이 매개 변수를 사용 하 여 사용자를 식별 하는 키를 제공할 수 있습니다.

이 매개 변수는 PowerShell 6.0에서 도입 되었습니다.

```yaml
Type: System.String
Parameter Sets: SSHHost
Aliases: IdentityFilePath

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

기존 세션의 이름을 지정합니다. `Enter-PSSession` 대화형 세션에 대해 지정 된 세션을 사용 합니다.

지정한 이름이 둘 이상의 세션과 일치하는 경우 명령이 실패합니다. **Session** , **InstanceID** 또는 **ID** 매개 변수를 사용 하 여 기존 세션을 지정할 수도 있습니다. 또는 **ComputerName** 매개 변수를 사용 하 여 임시 세션을 시작할 수 있습니다.

세션의 이름을 설정 하려면 cmdlet의 **name** 매개 변수를 사용 합니다 `New-PSSession` .

```yaml
Type: System.String
Parameter Sets: Name
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Port

이 명령에 사용 되는 원격 컴퓨터의 네트워크 포트를 지정 합니다.

PowerShell 6.0에서이 매개 변수는 SSH (Secure Shell) 연결을 지 원하는 **HostName** 매개 변수 집합에서 가져왔습니다.

**WinRM (ComputerName 매개 변수 설정)**

원격 컴퓨터에 연결하려면 원격 컴퓨터가 연결에서 사용하는 포트에서 수신 대기하고 있어야 합니다. 기본 포트는 HTTP의 WinRM 포트인 5985이 고, HTTPS의 경우 WinRM 포트인 5986입니다.

대체 포트를 사용하려면 먼저 원격 컴퓨터에 해당 포트에서 수신 대기할 WinRM 수신기를 구성해야 합니다. 다음 명령을 사용하여 수신기를 구성합니다.

1. `winrm delete winrm/config/listener?Address=*+Transport=HTTP`
2. `winrm create winrm/config/listener?Address=*+Transport=HTTP @{Port="\<port-number\>"}`

필요한 경우가 아니면 **Port** 매개 변수를 사용하지 마세요. 명령의 포트 설정은 이 명령이 실행되는 모든 컴퓨터나 세션에 적용됩니다. 대체 포트 설정을 사용하면 일부 컴퓨터에서 명령이 실행되지 않을 수 있습니다.

**SSH (호스트 이름 매개 변수 집합)**

원격 컴퓨터에 연결 하려면 SSH 서비스 (SSHD)를 사용 하 여 원격 컴퓨터를 구성 하 고 연결에서 사용 하는 포트에서 수신 대기 해야 합니다. SSH에 대 한 기본 포트는 22입니다.

```yaml
Type: System.Int32
Parameter Sets: ComputerName, SSHHost
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RunAsAdministrator

**PSSession** 이 관리자 권한으로 실행 됨을 나타냅니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ContainerId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Session

대화형 세션에 사용할 PowerShell 세션 ( **PSSession** )을 지정 합니다. 이 매개 변수는 세션 개체를 받습니다. **Name** , **InstanceID** 또는 **ID** 매개 변수를 사용 하 여 **PSSession** 을 지정할 수도 있습니다.

세션 개체를 포함 하는 변수를 입력 하거나 세션 개체를 만들거나 가져오는 명령 (예: 또는 명령)을 입력 `New-PSSession` `Get-PSSession` 합니다. 세션 개체를로 파이프 할 수도 있습니다 `Enter-PSSession` . 이 매개 변수를 사용 하 여 하나의 **PSSession** 만 제출할 수 있습니다. 둘 이상의 **PSSession** 이 포함 된 변수를 입력 하는 경우 명령이 실패 합니다.

`Exit-PSSession`또는 **EXIT** 키워드를 사용 하는 경우 대화형 세션이 종료 되지만 사용자가 만든 **PSSession** 은 계속 열려 있고 사용할 수 있습니다.

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: Session
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -SessionOption

세션의 고급 옵션을 설정합니다. Cmdlet을 사용 하 여 만든 것과 같은 **sessionoption** 개체를 입력 `New-PSSessionOption` 하거나 키가 세션 옵션 이름이 고 값이 session 옵션 값인 해시 테이블을 입력 합니다.

옵션의 기본값은 기본 설정 `$PSSessionOption` 변수의 값 (설정 된 경우)에 따라 결정 됩니다. 그러지 않으면 기본값은 세션 구성에 설정된 옵션에 따라 설정됩니다.

세션 옵션 값은 기본 설정 변수 및 세션 구성에 설정 된 세션의 기본값 보다 우선 적용 `$PSSessionOption` 됩니다. 그러나 이러한 값은 세션 구성에 설정된 최대값, 할당량 또는 제한보다 우선하지 않습니다.

기본값을 포함 하 여 세션 옵션에 대 한 자세한 내용은을 참조 하십시오 `New-PSSessionOption` .
기본 설정 변수에 대 한 자세한 내용은 `$PSSessionOption` [about_Preference_Variables](About/about_Preference_Variables.md)를 참조 하세요. 세션 구성에 대 한 자세한 내용은 [about_Session_Configurations](About/about_Session_Configurations.md)를 참조 하세요.

```yaml
Type: System.Management.Automation.Remoting.PSSessionOption
Parameter Sets: ComputerName, Uri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SSHTransport

SSH (Secure Shell)를 사용 하 여 원격 연결을 설정 했음을 나타냅니다.

기본적으로 PowerShell은 Windows WinRM을 사용 하 여 원격 컴퓨터에 연결 합니다. 이 스위치를 사용 하면 PowerShell에서 호스트 이름 매개 변수 집합을 사용 하 여 SSH 기반 원격 연결을 설정 합니다.

이 매개 변수는 PowerShell 6.0에서 도입 되었습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: SSHHost
Aliases:
Accepted values: true

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -하위 시스템

새 **PSSession** 에 사용 되는 SSH 하위 시스템을 지정 합니다.

이는 sshd_config에 정의 된 대로 대상에서 사용할 하위 시스템을 지정 합니다. 하위 시스템은 미리 정의 된 매개 변수를 사용 하 여 특정 버전의 PowerShell을 시작 합니다. 지정 된 하위 시스템이 원격 컴퓨터에 없는 경우 명령이 실패 합니다.

이 매개 변수를 사용 하지 않는 경우 기본값은 ' powershell ' 하위 시스템입니다.

```yaml
Type: System.String
Parameter Sets: SSHHost
Aliases:

Required: False
Position: Named
Default value: powershell
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -UserName

원격 컴퓨터에서 세션을 만드는 데 사용 되는 계정의 사용자 이름을 지정 합니다. 사용자 인증 방법은 원격 컴퓨터에서 SSH (Secure Shell)가 구성 된 방식에 따라 달라 집니다.

SSH가 기본 암호 인증으로 구성 된 경우 사용자 암호를 입력 하 라는 메시지가 표시 됩니다.

키 기반 사용자 인증에 대해 SSH를 구성 하는 경우 키 파일 경로를 **Keyfilepath** 매개 변수를 통해 제공할 수 있으며 암호 프롬프트가 발생 하지 않습니다. 클라이언트 사용자 키 파일이 SSH 알려진 위치에 있는 경우 키 기반 인증에는 **Keyfilepath** 매개 변수가 필요 하지 않으며 사용자 인증은 사용자 이름에 따라 자동으로 수행 됩니다. 자세한 내용은 키 기반 사용자 인증에 대 한 SSH 설명서를 참조 하세요.

필수 매개 변수가 아닙니다. **UserName** 매개 변수를 지정 하지 않으면 현재 로그온 사용자 이름이 연결에 사용 됩니다.

이 매개 변수는 PowerShell 6.0에서 도입 되었습니다.

```yaml
Type: System.String
Parameter Sets: SSHHost
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseSSL

이 cmdlet이 SSL(Secure Sockets Layer) (SSL) 프로토콜을 사용 하 여 원격 컴퓨터에 대 한 연결을 설정 함을 나타냅니다. 기본적으로 SSL은 사용되지 않습니다.

WS-Management는 네트워크를 통해 전송 되는 모든 PowerShell 콘텐츠를 암호화 합니다. **UseSSL** 매개 변수는 HTTP 연결 대신 HTTPS 연결을 통해 데이터를 전송 하는 추가 보호 기능입니다.

이 매개 변수를 사용 하지만 명령에 사용 되는 포트에서 SSL을 사용할 수 없는 경우 명령이 실패 합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -VMId

가상 컴퓨터의 ID를 지정 합니다.

```yaml
Type: System.Guid
Parameter Sets: VMId
Aliases: VMGuid

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -VMName

가상 컴퓨터의 이름을 지정합니다.

```yaml
Type: System.String
Parameter Sets: VMName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.string (Runspace, 시스템.

컴퓨터 이름, 문자열 또는 세션 개체를이 cmdlet으로 파이프 할 수 있습니다.

## 출력

### 없음

이 cmdlet은 어떠한 출력도 반환되지 않습니다.

## 참고

원격 컴퓨터에 연결하려면 원격 컴퓨터의 Administrators 그룹 구성원이어야 합니다. 로컬 컴퓨터에서 대화형 세션을 시작 하려면 **관리자 권한으로 실행** 옵션을 사용 하 여 PowerShell을 시작 해야 합니다.

를 사용 하는 경우 `Enter-PSSession` 원격 컴퓨터의 사용자 프로필이 대화형 세션에 사용 됩니다. PowerShell 모듈을 추가 하 고 명령 프롬프트를 변경 하는 명령을 비롯 한 원격 사용자 프로필의 명령은 원격 프롬프트가 표시 되기 전에 실행 됩니다.

`Enter-PSSession` 는 대화형 세션을 위해 로컬 컴퓨터에서 UI 문화권 설정을 사용 합니다. 로컬 UI 문화권을 찾으려면 자동 변수를 사용 `$UICulture` 합니다.

`Enter-PSSession``Get-Command`, `Out-Default` 및 cmdlet이 필요 `Exit-PSSession` 합니다. 이러한 cmdlet이 원격 컴퓨터의 세션 구성에 포함 되지 않은 경우 `Enter-PSSession` 명령이 실패 합니다.

가 `Invoke-Command` 원격 컴퓨터에 보내기 전에 명령을 구문 분석 하 고 해석 하는와 달리는 `Enter-PSSession` 명령을 해석 하지 않고 원격 컴퓨터에 직접 보냅니다.

입력 하려는 세션이 명령을 처리 하는 중이면 PowerShell이 명령에 응답 하기 전에 지연이 있을 수 있습니다 `Enter-PSSession` . 세션을 사용할 수 있게 되 면 즉시 연결 됩니다. 명령을 취소 하려면 `Enter-PSSession` <kbd>ctrl</kbd> + <kbd>C</kbd>를 누릅니다.

**HostName** 매개 변수 집합은 PowerShell 6.0부터 포함 되었습니다. Secure Shell (SSH)를 기반으로 PowerShell 원격 기능을 제공 하기 위해 추가 되었습니다. SSH와 PowerShell은 여러 플랫폼 (Windows, Linux, macOS)에서 지원 되며 powershell 원격은 PowerShell 및 SSH가 설치 되 고 구성 되는 이러한 플랫폼에서 작동 합니다. 이는 WinRM을 기반으로 하는 이전 Windows 전용 원격 시스템과 별개 이며, 대부분의 WinRM 특정 기능 및 제한 사항이 적용 되지 않습니다. 예를 들어 WinRM 기반 할당량, 세션 옵션, 사용자 지정 끝점 구성 및 연결 끊기/다시 연결 기능은 현재 지원 되지 않습니다. PowerShell SSH 원격을 설정 하는 방법에 대 한 자세한 내용은 [ssh를 통한 Powershell 원격](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core)을 참조 하세요.

PowerShell 7.1 이전에는 SSH를 통한 원격 기능이 두 번째 홉 원격 세션을 지원하지 않았습니다. 해당 기능은 WinRM을 사용하는 세션으로 제한되었습니다. PowerShell 7.1을 사용하면 `Enter-PSSession` 및 `Enter-PSHostProcess`가 대화형 원격 세션 내에서 작동할 수 있습니다.

## 관련 링크

[Exit-PSSession](Exit-PSSession.md)

[Get-PSSession](Get-PSSession.md)

[Invoke-Command](Invoke-Command.md)

[New-PSSession](New-PSSession.md)

[Remove-PSSession](Remove-PSSession.md)

[Connect-PSSession](Connect-PSSession.md)

[Disconnect-PSSession](Disconnect-PSSession.md)

[Receive-PSSession](Receive-PSSession.md)

[about_PSSessions](About/about_PSSessions.md)

[about_Remote](About/about_Remote.md)
