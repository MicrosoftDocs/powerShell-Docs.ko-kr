---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 12/20/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-pssession?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSSession
ms.openlocfilehash: 4b40d765002791f45f093c7912b8f9ba58248da9
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99601467"
---
# New-PSSession

## 개요
로컬 또는 원격 컴퓨터에 대한 영구 연결을 만듭니다.

## SYNTAX

### ComputerName (기본값)

```
New-PSSession [[-ComputerName] <String[]>] [-Credential <PSCredential>] [-Name <String[]>]
 [-EnableNetworkAccess] [-ConfigurationName <String>] [-Port <Int32>] [-UseSSL]
 [-ApplicationName <String>] [-ThrottleLimit <Int32>] [-SessionOption <PSSessionOption>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

### URI

```
New-PSSession [-Credential <PSCredential>] [-Name <String[]>] [-EnableNetworkAccess]
 [-ConfigurationName <String>] [-ThrottleLimit <Int32>] [-ConnectionUri] <Uri[]> [-AllowRedirection]
 [-SessionOption <PSSessionOption>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [<CommonParameters>]
```

### VMId

```
New-PSSession -Credential <PSCredential> [-Name <String[]>] [-ConfigurationName <String>]
 [-VMId] <Guid[]> [-ThrottleLimit <Int32>] [<CommonParameters>]
```

### VMName

```
New-PSSession -Credential <PSCredential> [-Name <String[]>] [-ConfigurationName <String>]
 -VMName <String[]> [-ThrottleLimit <Int32>] [<CommonParameters>]
```

### 세션

```
New-PSSession [[-Session] <PSSession[]>] [-Name <String[]>] [-EnableNetworkAccess]
 [-ThrottleLimit <Int32>] [<CommonParameters>]
```

### ContainerId

```
New-PSSession [-Name <String[]>] [-ConfigurationName <String>] -ContainerId <String[]>
 [-RunAsAdministrator] [-ThrottleLimit <Int32>] [<CommonParameters>]
```

### UseWindowsPowerShellParameterSet

```
New-PSSession [-Name <String[]>] [-UseWindowsPowerShell] [<CommonParameters>]
```

### SSHHost

```
New-PSSession [-Name <String[]>] [-Port <Int32>] [-HostName] <String[]> [-UserName <String>]
 [-KeyFilePath <String>] [-SSHTransport] [-Subsystem <String>] [<CommonParameters>]
```

### SSHHostHashParam

```
New-PSSession [-Name <String[]>] -SSHConnection <Hashtable[]> [<CommonParameters>]
```

## 설명

`New-PSSession`Cmdlet은 로컬 또는 원격 컴퓨터에 PowerShell 세션 (**PSSession**)을 만듭니다. **PSSession** 을 만들 때 PowerShell은 원격 컴퓨터에 대 한 영구 연결을 설정 합니다.

**PSSession** 을 사용 하 여 함수 또는 변수 값과 같은 데이터를 공유 하는 여러 명령을 실행할 수 있습니다. **PSSession** 에서 명령을 실행 하려면 cmdlet을 사용 `Invoke-Command` 합니다. **PSSession** 을 사용 하 여 원격 컴퓨터와 직접 상호 작용 하려면 cmdlet을 사용 `Enter-PSSession` 합니다. 자세한 내용은 [about_PSSessions](about/about_PSSessions.md)를 참조 하세요.

또는의 **ComputerName** 매개 변수를 사용 하 여 **PSSession** 을 만들지 않고 원격 컴퓨터에서 명령을 실행할 수 있습니다 `Enter-PSSession` `Invoke-Command` . **ComputerName** 매개 변수를 사용 하는 경우 PowerShell은 명령에 사용 되는 임시 연결을 만든 다음 닫힙니다.

PowerShell 6.0부터 ssh (Secure Shell)를 사용 하 여 원격 컴퓨터에 대 한 연결을 설정 하 고 원격 컴퓨터에서 SSH를 사용할 수 있고 원격 컴퓨터가 PowerShell SSH 끝점으로 구성 된 경우 원격 컴퓨터에서 세션을 만들 수 있습니다. SSH 기반 PowerShell 원격 세션의 혜택은 여러 플랫폼 (Windows, Linux, macOS)에서 작동할 수 있다는 것입니다. SSH 기반 세션의 경우 **HostName** 또는 **SSHConnection** 매개 변수 집합을 사용 하 여 원격 컴퓨터 및 관련 연결 정보를 지정 합니다. PowerShell SSH 원격을 설정 하는 방법에 대 한 자세한 내용은 [ssh를 통한 Powershell 원격](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core)을 참조 하세요.

> [!NOTE]
> 서버 인증서를 신뢰할 수 없는 HTTPS 끝점을 사용 하 여 Linux 또는 macOS 클라이언트에서 WSMan 원격을 사용 하는 경우 (예: 자체 서명 된 인증서) 연결을 성공적으로 `PSSessionOption` `-SkipCACheck` 설정 하려면 및를 포함 하는를 제공 해야 합니다 `-SkipCNCheck` . 서버 인증서와 대상 시스템에 대 한 네트워크 연결을 지정할 수 있는 환경에 있는 경우에만이 작업을 수행 합니다.

## 예제

### 예 1: 로컬 컴퓨터에서 세션 만들기

```powershell
$s = New-PSSession
```

이 명령은 로컬 컴퓨터에 새 **pssession** 을 만든 다음 변수에 **pssession** 을 저장 합니다 `$s` .

이제이 **PSSession** 을 사용 하 여 로컬 컴퓨터에서 명령을 실행할 수 있습니다.

### 예 2: 원격 컴퓨터에서 세션 만들기

```powershell
$Server01 = New-PSSession -ComputerName Server01
```

이 명령은 Server01 컴퓨터에 새 **PSSession** 을 만든 다음 `$Server01` 변수에 저장 합니다.

여러 **PSSession** 개체를 만들 때 유용한 이름의 변수에 할당 합니다. 이렇게 하면 이후 명령에서 **PSSession** 개체를 관리 하는 데 도움이 됩니다.

### 예 3: 여러 컴퓨터에서 세션 만들기

```powershell
$s1, $s2, $s3 = New-PSSession -ComputerName Server01,Server02,Server03
```

이 명령은 **ComputerName** 매개 변수로 지정 된 각 컴퓨터에 하나씩 세 개의 **PSSession** 개체를 만듭니다.

이 명령은 대입 연산자 (=)를 사용 하 여 새 **PSSession** 개체를 변수에 할당 합니다. `$s1` , `$s2` , `$s3` Server01 **pssession** 을에 할당 하 `$s1` 고, Server02 **Pssession** 을에 `$s2` , Server03 **pssession** 을에 할당 `$s3` 합니다.

여러 개체를 일련의 변수에 할당 하면 PowerShell에서 각 개체를 계열의 변수에 각각 할당 합니다. 변수보다 개체가 많은 경우에는 나머지 모든 개체가 마지막 변수에 할당됩니다. 개체보다 변수가 많은 경우에는 나머지 변수가 비어 있습니다(null).

### 예제 4: 지정 된 포트를 사용 하 여 세션 만들기

```powershell
New-PSSession -ComputerName Server01 -Port 8081 -UseSSL -ConfigurationName E12
```

이 명령은 서버 포트 8081에 연결 되 고 SSL 프로토콜을 사용 하는 Server01 컴퓨터에 새 **PSSession** 을 만듭니다. 새 **PSSession** 은 E12 라는 대체 세션 구성을 사용 합니다.

포트를 설정하기 전에 포트 8081에서 수신 대기하도록 원격 컴퓨터의 WinRM 수신기를 구성해야 합니다. 자세한 내용은 **Port** 매개 변수에 대 한 설명을 참조 하세요.

### 예 5: 기존 세션을 기반으로 세션 만들기

```powershell
New-PSSession -Session $s -Credential Domain01\User01
```

이 명령은 기존 **pssession** 과 동일한 속성을 사용 하 여 **PSSession** 을 만듭니다. 기존 **pssession** 의 리소스가 모두 소모 되 고 일부 수요를 오프 로드 하는 데 새 **pssession** 이 필요한 경우이 명령 형식을 사용할 수 있습니다.

이 명령은의 **Session** 매개 변수를 사용 하 여 `New-PSSession` 변수에 저장 된 **PSSession** 을 지정 합니다 `$s` . Domain1\Admin01 사용자의 자격 증명이 이 명령을 완료하는 데 사용됩니다.

### 예 6: 다른 도메인에서 전역 범위를 사용 하 여 세션 만들기

```powershell
$global:s = New-PSSession -ComputerName Server1.Domain44.Corpnet.Fabrikam.com -Credential Domain01\Admin01
```

이 예제에서는 다른 도메인의 컴퓨터에 전역 범위를 사용 하 여 **PSSession** 을 만드는 방법을 보여 줍니다.

기본적으로 명령줄에서 생성 된 **pssession** 개체는 로컬 범위를 사용 하 여 생성 되 고 스크립트에서 생성 된 **pssession** 개체에는 스크립트 범위가 있습니다.

전역 범위를 사용 하 여 **pssession** 을 만들려면 새 **pssession** 을 만든 다음 전역 범위로 캐스팅 되는 변수에 **pssession** 을 저장 합니다. 이 경우 `$s` 변수는 전역 범위로 캐스팅 됩니다.

이 명령은 **ComputerName** 매개 변수를 사용하여 원격 컴퓨터를 지정합니다. 컴퓨터가 사용자 계정과 다른 도메인에 있기 때문에 컴퓨터의 전체 이름은 사용자의 자격 증명과 함께 지정 됩니다.

### 예 7: 많은 컴퓨터에 대 한 세션 만들기

```powershell
$rs = Get-Content C:\Test\Servers.txt | New-PSSession -ThrottleLimit 50
```

이 명령은 Servers.txt 파일에 나열 된 각 200 컴퓨터에 **pssession** 을 만들고 결과 **pssession** 을 변수에 저장 합니다 `$rs` . **PSSession** 개체의 스로틀 제한은 50입니다.

컴퓨터의 이름이 데이터베이스, 스프레드시트, 텍스트 파일 또는 다른 텍스트 변환 가능 형식에 저장된 경우 이 명령 형식을 사용할 수 있습니다.

### 예 8: URI를 사용 하 여 세션 만들기

```powershell
$s = New-PSSession -URI http://Server01:91/NewSession -Credential Domain01\User01
```

이 명령은 Server01 컴퓨터에 **PSSession** 을 만들어 `$s` 변수에 저장 합니다. **URI** 매개 변수를 사용 하 여 전송 프로토콜, 원격 컴퓨터, 포트 및 대체 세션 구성을 지정 합니다. 또한 **Credential** 매개 변수를 사용 하 여 원격 컴퓨터에서 세션을 만들 수 있는 권한을 가진 사용자 계정을 지정 합니다.

### 예 9: 세션 집합에서 백그라운드 작업 실행

```powershell
$s = New-PSSession -ComputerName (Get-Content Servers.txt) -Credential Domain01\Admin01 -ThrottleLimit 16
Invoke-Command -Session $s -ScriptBlock {Get-Process PowerShell} -AsJob
```

이러한 명령은 **pssession** 개체 집합을 만든 다음 각 **pssession** 개체에서 백그라운드 작업을 실행 합니다.

첫 번째 명령은 Servers.txt 파일에 나열 된 각 컴퓨터에 새 **PSSession** 을 만듭니다. Cmdlet을 사용 하 여 `New-PSSession` **PSSession** 을 만듭니다. **ComputerName** 매개 변수 값은 cmdlet을 사용 하 여 `Get-Content` Servers.txt 파일의 컴퓨터 이름 목록을 가져오는 명령입니다.

이 명령은 **Credential** 매개 변수를 사용 하 여 도메인 관리자의 권한이 있는 **PSSession** 개체를 만들고 **ThrottleLimit** 매개 변수를 사용 하 여 명령을 동시 연결 16 개로 제한 합니다. 이 명령은 **PSSession** 개체를 변수에 저장 합니다 `$s` .

두 번째 명령은 cmdlet의 **AsJob** 매개 변수를 사용 하 여 `Invoke-Command` `Get-Process PowerShell` 의 각 **PSSession** 개체에서 명령을 실행 하는 백그라운드 작업을 시작 합니다 `$s` .

PowerShell 백그라운드 작업에 대 한 자세한 내용은 [about_Jobs](About/about_Jobs.md) 및 [about_Remote_Jobs](About/about_Remote_Jobs.md)를 참조 하세요.

### 예 10: 해당 URI를 사용 하 여 컴퓨터에 대 한 세션 만들기

```powershell
New-PSSession -ConnectionURI https://management.exchangelabs.com/Management
```

이 명령은 컴퓨터 이름이 아닌 URI로 지정 된 컴퓨터에 연결 하는 **PSSession** 개체를 만듭니다.

### 예 11: 세션 옵션 만들기

```powershell
$so = New-PSSessionOption -SkipCACheck
New-PSSession -ConnectionUri https://management.exchangelabs.com/Management -SessionOption $so -Credential Server01\Admin01
```

이 예에서는 세션 옵션 개체를 만들고 **sessionoption** 매개 변수를 사용 하는 방법을 보여 줍니다.

첫 번째 명령은 cmdlet을 사용 하 여 `New-PSSessionOption` 세션 옵션을 만듭니다. 결과 **Sessionoption** 개체를 `$so` 변수에 저장 합니다.

두 번째 명령은 새 세션의 옵션을 사용합니다. 이 명령은 cmdlet을 사용 하 여 `New-PSSession` 새 세션을 만듭니다. SessionOption 매개 변수 값은 변수의 **sessionoption** 개체입니다 `$so` .

### 예 12: SSH를 사용 하 여 세션 만들기

```powershell
New-PSSession -HostName UserA@LinuxServer01
```

이 예제에서는 Secure Shell (SSH)를 사용 하 여 새 **PSSession** 을 만드는 방법을 보여 줍니다. SSH가 원격 컴퓨터에서 암호를 묻는 메시지를 표시 하도록 구성 된 경우 암호를 입력 하 라는 메시지가 표시 됩니다. 그렇지 않은 경우에는 SSH 키 기반 사용자 인증을 사용 해야 합니다.

### 예 13: SSH를 사용 하 여 세션을 만들고 포트 및 사용자 인증 키 지정

```powershell
New-PSSession -HostName UserA@LinuxServer01:22 -KeyFilePath c:\<path>\userAKey_rsa
```

이 예제에서는 Secure Shell (SSH)를 사용 하 여 **PSSession** 을 만드는 방법을 보여 줍니다. **Port** 매개 변수를 사용 하 여 사용할 포트를 지정 하 고 **keyfilepath** 매개 변수를 사용 하 여 원격 컴퓨터에서 사용자를 식별 하 고 인증 하는 데 사용 되는 RSA 키를 지정 합니다.

### 예제 14: SSH를 사용 하 여 여러 세션 만들기

```powershell
$sshConnections = @{ HostName="WinServer1"; UserName="domain\userA"; KeyFilePath="c:\users\UserA\id_rsa" }, @{ HostName="UserB@LinuxServer5"; KeyFilePath="c:\UserB\<path>\id_rsa" }
New-PSSession -SSHConnection $sshConnections
```

이 예에서는 Secure Shell (SSH) 및 **SSHConnection** 매개 변수 집합을 사용 하 여 여러 세션을 만드는 방법을 보여 줍니다. **SSHConnection** 매개 변수는 각 세션에 대 한 연결 정보를 포함 하는 해시 테이블의 배열을 사용 합니다. 이 예제에서는 대상 원격 컴퓨터에 키 기반 사용자 인증을 지원 하도록 구성 된 SSH가 있어야 합니다.

## PARAMETERS

### -AllowRedirection

이 cmdlet이이 연결을 대체 URI (Uniform Resource Identifier)로 리디렉션할 수 있음을 나타냅니다.

**ConnectionURI** 매개 변수를 사용하면 원격 대상에서 다른 URI로 리디렉션하는 명령을 반환할 수 있습니다. 기본적으로 PowerShell은 연결을 리디렉션하지 않지만이 매개 변수를 사용 하 여 연결을 리디렉션할 수 있도록 설정할 수 있습니다.

또한 **MaximumConnectionRedirectionCount** 세션 옵션 값을 변경하여 연결이 리디렉션되는 횟수를 제한할 수도 있습니다. Cmdlet의 **Maximumredirection** 매개 변수를 사용 `New-PSSessionOption` 하거나 **$PSSessionOption** 기본 설정 변수의 **MaximumConnectionRedirectionCount** 속성을 설정 합니다. 기본값은 5입니다.

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

WinRM 서비스는 애플리케이션 이름을 사용하여 연결 요청을 제공하는 수신기를 선택합니다.
이 매개 변수 값은 원격 컴퓨터에 있는 수신기의 **URLPrefix** 속성 값과 일치해야 합니다.

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

사용자 자격 증명을 인증하는 데 사용되는 메커니즘을 지정합니다.
이 매개 변수에 허용되는 값은 다음과 같습니다.

- 기본값
- Basic
- Credssp
- 다이제스트
- Kerberos
- Negotiate
- NegotiateWithImplicitCredential

기본값은 Default입니다.

이 매개 변수 값에 대 한 자세한 내용은 [Authenticationmechanism 열거](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)를 참조 하세요.

> [!CAUTION]
> 사용자 자격 증명이 인증을 위해 원격 컴퓨터에 전달 되는 CredSSP (자격 증명 보안 지원 공급자) 인증은 둘 이상의 리소스 (예: 원격 네트워크 공유 액세스)에 대 한 인증이 필요한 명령에 대해 설계 되었습니다. 이렇게 하면 원격 작업의 보안 위험이 커집니다. 원격 컴퓨터가 손상된 경우 이 컴퓨터로 전달된 자격 증명을 사용하여 네트워크 세션을 제어할 수 있습니다.

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

컴퓨터 이름 배열을 지정 합니다. 이 cmdlet은 지정 된 컴퓨터에 대 한 영구 연결 (**PSSession**)을 만듭니다. 여러 컴퓨터 이름을 입력 하면에서 `New-PSSession` 각 컴퓨터에 대해 하나씩 여러 **PSSession** 개체를 만듭니다. 기본값은 로컬 컴퓨터입니다.

하나 이상의 원격 컴퓨터의 NetBIOS 이름, IP 주소 또는 정규화된 도메인 이름을 입력하세요. 로컬 컴퓨터를 지정 하려면 컴퓨터 이름, localhost 또는 점 (.)을 입력 합니다. 컴퓨터가 사용자와 다른 도메인에 있는 경우 정규화된 도메인 이름이 필요합니다. 컴퓨터 이름을 따옴표로 파이프 할 수도 있습니다 `New-PSSession` .

**ComputerName** 매개 변수 값에 IP 주소를 사용 하려면 명령에 **Credential** 매개 변수를 포함 해야 합니다. 또한 HTTPS 전송을 사용하도록 컴퓨터를 구성하거나 원격 컴퓨터의 IP 주소를 로컬 컴퓨터의 WinRM TrustedHosts 목록에 포함해야 합니다. TrustedHosts 목록에 컴퓨터 이름을 추가 하는 방법에 대 한 지침은 [about_Remote_Troubleshooting](about/about_Remote_Troubleshooting.md)의 "신뢰할 수 있는 호스트 목록에 컴퓨터를 추가 하는 방법"을 참조 하십시오.

**ComputerName** 매개 변수 값에 로컬 컴퓨터를 포함 하려면 관리자 권한으로 실행 옵션을 사용 하 여 Windows PowerShell을 시작 합니다.

```yaml
Type: System.String[]
Parameter Sets: ComputerName
Aliases: Cn

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -ConfigurationName

새 **PSSession** 에 사용 되는 세션 구성을 지정 합니다.

세션 구성의 구성 이름 또는 정규화된 리소스 URI를 입력합니다. 구성 이름만 지정 하는 경우에는 다음 스키마 URI가 앞에와 야 `http://schemas.microsoft.com/PowerShell` 합니다.

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

**ConnectionURI** 를 지정하지 않은 경우 **UseSSL**, **ComputerName**, **Port** 및 **ApplicationName** 매개 변수를 사용하여 **ConnectionURI** 값을 지정할 수 있습니다.

URI의 전송 세그먼트에 유효한 값은 HTTP 및 HTTPS입니다. 전송 세그먼트를 사용 하 여 연결 URI를 지정 하 고 포트를 지정 하지 않으면 세션은 표준 포트 80 (HTTP의 경우, HTTPS의 경우 443)를 사용 하 여 만들어집니다. PowerShell 원격을 위한 기본 포트를 사용 하려면 HTTP의 경우 포트 5985을, HTTPS의 경우 5986을 지정 합니다.

대상 컴퓨터에서 연결을 다른 URI로 리디렉션하는 경우 명령에서 **allowredirection** 매개 변수를 사용 하지 않으면 PowerShell에서 리디렉션을 방지 합니다.

```yaml
Type: System.Uri[]
Parameter Sets: Uri
Aliases: URI, CU

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ContainerId

컨테이너의 Id 배열을 지정 합니다. 이 cmdlet은 지정 된 각 컨테이너와 대화형 세션을 시작 합니다. 명령을 사용 `docker ps` 하 여 컨테이너 id 목록을 가져옵니다. 자세한 내용은 [docker ps](https://docs.docker.com/engine/reference/commandline/ps/) 명령에 대 한 도움말을 참조 하세요.

```yaml
Type: System.String[]
Parameter Sets: ContainerId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Credential

이 작업을 수행할 수 있는 권한이 있는 사용자 계정을 지정 합니다. 기본값은 현재 사용자입니다.

**User01** 또는 **Domain01\User01** 과 같은 사용자 이름을 입력 하거나 cmdlet에 의해 생성 된 **PSCredential** 개체를 입력 합니다 `Get-Credential` . 사용자 이름을 입력 하면 암호를 입력 하 라는 메시지가 표시 됩니다.

자격 증명은 [PSCredential](/dotnet/api/system.management.automation.pscredential) 개체에 저장 되 고 암호는 [SecureString](/dotnet/api/system.security.securestring)으로 저장 됩니다.

> [!NOTE]
> **Securestring** 데이터 보호에 대 한 자세한 [내용은 참조 하십시오](/dotnet/api/system.security.securestring#how-secure-is-securestring).

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerName, Uri, VMId, VMName
Aliases:

Required: True (VMId, VMName), False (ComputerName, Uri)
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -EnableNetworkAccess

이 cmdlet이 루프백 세션에 대화형 보안 토큰을 추가 함을 나타냅니다. 대화형 토큰을 사용하면 다른 컴퓨터에서 데이터를 가져오는 명령을 루프백 세션에서 실행할 수 있습니다. 예를 들어 원격 컴퓨터에서 로컬 컴퓨터로 XML 파일을 복사하는 세션에서 명령을 실행할 수 있습니다.

루프백 세션은 동일한 컴퓨터에서 시작 하 여 종료 되는 **PSSession** 입니다. 루프백 세션을 만들려면 **ComputerName** 매개 변수를 생략 하거나 해당 값을 점 (.), localhost 또는 로컬 컴퓨터 이름으로 설정 합니다.

기본적으로이 cmdlet은 원격 컴퓨터를 인증 하는 데 충분 한 권한을 제공 하지 않을 수 있는 네트워크 토큰을 사용 하 여 루프백 세션을 만듭니다.

**EnableNetworkAccess** 매개 변수는 루프백 세션에서만 유효합니다. 원격 컴퓨터에서 세션을 만들 때 **EnableNetworkAccess** 를 사용 하는 경우 명령은 성공 하지만 매개 변수는 무시 됩니다.

또한 세션 자격 증명을 다른 컴퓨터에 위임 하는 **인증** 매개 변수의 CredSSP 값을 사용 하 여 루프백 세션에서 원격 액세스를 사용 하도록 설정할 수 있습니다.

악의적인 액세스 로부터 컴퓨터를 보호 하기 위해 **EnableNetworkAccess** 매개 변수를 사용 하 여 만든 대화형 토큰을 포함 하는 분리 된 루프백 세션은 세션을 만든 컴퓨터 에서만 다시 연결할 수 있습니다. CredSSP 인증을 사용하는 연결이 끊어진 세션은 다른 컴퓨터에서 다시 연결할 수 있습니다. 자세한 내용은 `Disconnect-PSSession`를 참조하세요.

이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName, Uri, Session
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -HostName

Secure Shell (SSH) 기반 연결에 대 한 컴퓨터 이름 배열을 지정 합니다. 이는 원격 컴퓨터에 대 한 연결이 Windows WinRM이 아닌 SSH를 사용 하는 경우를 제외 하 고 ComputerName 매개 변수와 비슷합니다.

이 매개 변수는 PowerShell 6.0에서 도입 되었습니다.

```yaml
Type: System.String[]
Parameter Sets: SSHHost
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
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

**PSSession** 의 이름을 지정 합니다.

및 등의 다른 cmdlet을 사용 하는 경우 이름을 사용 하 여 **PSSession** 을 참조할 수 `Get-PSSession` 있습니다 `Enter-PSSession` . 이 이름은 컴퓨터나 현재 세션에서 고유하지 않아도 됩니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Port

이 명령에 사용되는 원격 컴퓨터의 네트워크 포트를 지정합니다. 원격 컴퓨터에 연결하려면 원격 컴퓨터가 연결에서 사용하는 포트에서 수신 대기하고 있어야 합니다. 기본 포트는 HTTP의 WinRM 포트인 5985이 고, HTTPS의 경우 WinRM 포트인 5986입니다.

다른 포트를 사용 하기 전에 해당 포트에서 수신 대기 하도록 원격 컴퓨터의 WinRM 수신기를 구성 해야 합니다. 다음 명령을 사용하여 수신기를 구성합니다.

1. `winrm delete winrm/config/listener?Address=*+Transport=HTTP`
2. `winrm create winrm/config/listener?Address=*+Transport=HTTP @{Port="\<port-number\>"}`

필요한 경우가 아니면 **Port** 매개 변수를 사용하지 마세요. 명령의 포트 설정은 이 명령이 실행되는 모든 컴퓨터나 세션에 적용됩니다. 대체 포트 설정을 사용하면 일부 컴퓨터에서 명령이 실행되지 않을 수 있습니다.

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

이 cmdlet이 새 **pssession** 의 모델로 사용 하는 **PSSession** 개체의 배열을 지정 합니다. 이 매개 변수는 지정 된 **pssession** 개체와 동일한 속성을 가진 새 **pssession** 개체를 만듭니다.

**Pssession** 개체를 포함 하는 변수를 입력 하거나 **pssession** 개체를 만들거나 가져오는 명령 (예: 또는 명령)을 입력 합니다 `New-PSSession` `Get-PSSession` .

결과로 생성 된 **PSSession** 개체의 컴퓨터 이름, 응용 프로그램 이름, 연결 URI, 포트, 구성 이름, 제한 한도 및 SSL(SECURE SOCKETS LAYER) (SSL) 값이 원본과 동일 하지만 표시 이름, ID 및 인스턴스 ID (GUID)는 다릅니다.

```yaml
Type: System.Management.Automation.Runspaces.PSSession[]
Parameter Sets: Session
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -SessionOption

세션에 대 한 고급 옵션을 지정 합니다. Cmdlet을 사용 하 여 만든 것과 같은 **sessionoption** 개체를 입력 `New-PSSessionOption` 하거나 키가 세션 옵션 이름이 고 값이 session 옵션 값인 해시 테이블을 입력 합니다.

옵션의 기본값은 기본 설정 `$PSSessionOption` 변수의 값 (설정 된 경우)에 따라 결정 됩니다. 그러지 않으면 기본값은 세션 구성에 설정된 옵션에 따라 설정됩니다.

세션 옵션 값은 기본 설정 변수 및 세션 구성에 설정 된 세션의 기본값 보다 우선 적용 `$PSSessionOption` 됩니다. 그러나 이러한 값은 세션 구성에 설정된 최대값, 할당량 또는 제한보다 우선하지 않습니다.

기본값을 포함 하는 세션 옵션에 대 한 설명은를 참조 하십시오 `New-PSSessionOption` . 기본 설정 변수에 대 한 자세한 내용은 `$PSSessionOption` [about_Preference_Variables](About/about_Preference_Variables.md)를 참조 하세요. 세션 구성에 대 한 자세한 내용은 [about_Session_Configurations](About/about_Session_Configurations.md)를 참조 하세요.

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

### -SSHConnection

이 매개 변수는 해시 테이블의 배열을 사용 합니다. 여기서 각 해시 테이블에는 SSH (Secure Shell) 연결을 설정 하는 데 필요한 하나 이상의 연결 매개 변수가 포함 되어 있습니다 (호스트 이름, 포트, 사용자 이름, KeyFilePath).

Hashtable 연결 매개 변수는 **HostName** 매개 변수 집합에 대해 정의 된 것과 동일 합니다.

**SSHConnection** 매개 변수는 각 세션에 다른 연결 정보가 필요한 여러 세션을 만드는 데 유용 합니다.

이 매개 변수는 PowerShell 6.0에서 도입 되었습니다.

```yaml
Type: System.Collections.Hashtable[]
Parameter Sets: SSHHostHashParam
Aliases:

Required: True
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

### -ThrottleLimit

이 명령을 실행하도록 설정할 수 있는 최대 동시 연결 수를 지정합니다.
이 매개 변수를 생략하거나 값 0을 입력하면 기본값 32가 사용됩니다.

제한 한도는 현재 명령에만 적용되며 세션이나 컴퓨터에는 적용되지 않습니다.

```yaml
Type: System.Int32
Parameter Sets: ComputerName, Uri, VMId, VMName, Session, ContainerId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UserName

원격 컴퓨터에서 세션을 만드는 데 사용 되는 계정의 사용자 이름을 지정 합니다. 사용자 인증 방법은 원격 컴퓨터에서 SSH (Secure Shell)가 구성 된 방식에 따라 달라 집니다.

SSH가 기본 암호 인증으로 구성 된 경우 사용자 암호를 입력 하 라는 메시지가 표시 됩니다.

키 기반 사용자 인증에 대해 SSH를 구성 하는 경우 키 파일 경로를 KeyFilePath 매개 변수를 통해 제공할 수 있으며 암호 프롬프트가 발생 하지 않습니다. 클라이언트 사용자 키 파일이 SSH 알려진 위치에 있는 경우 키 기반 인증에는 KeyFilePath 매개 변수가 필요 하지 않으며 사용자 인증은 사용자 이름에 따라 자동으로 수행 됩니다. 자세한 내용은 키 기반 사용자 인증에 대 한 SSH 설명서를 참조 하세요.

필수 매개 변수가 아닙니다. UserName 매개 변수를 지정 하지 않으면 현재 로그온 사용자 이름이 연결에 사용 됩니다.

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

이 cmdlet이 SSL 프로토콜을 사용 하 여 원격 컴퓨터에 대 한 연결을 설정 함을 나타냅니다.
기본적으로 SSL은 사용되지 않습니다.

WS-Management는 네트워크를 통해 전송 되는 모든 PowerShell 콘텐츠를 암호화 합니다. **UseSSL** 매개 변수는 HTTP 연결 대신 HTTPS 연결을 통해 데이터를 전송 하는 추가 보호 기능을 제공 합니다.

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

가상 컴퓨터의 ID 배열을 지정 합니다. 이 cmdlet은 지정 된 각 가상 컴퓨터와 대화형 세션을 시작 합니다. 사용할 수 있는 가상 컴퓨터를 보려면 다음 명령을 사용 합니다.

`Get-VM | Select-Object -Property Name, ID`

```yaml
Type: System.Guid[]
Parameter Sets: VMId
Aliases: VMGuid

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -VMName

가상 컴퓨터의 이름 배열을 지정합니다. 이 cmdlet은 지정 된 각 가상 컴퓨터와 대화형 세션을 시작 합니다. 사용할 수 있는 가상 컴퓨터를 확인 하려면 cmdlet을 사용 합니다 `Get-VM` .

```yaml
Type: System.String[]
Parameter Sets: VMName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -하위 시스템

새 **PSSession** 에 사용 되는 SSH 하위 시스템을 지정 합니다.

이는 sshd_config에 정의 된 대로 대상에서 사용할 하위 시스템을 지정 합니다.
하위 시스템은 미리 정의 된 매개 변수를 사용 하 여 특정 버전의 PowerShell을 시작 합니다.
지정 된 하위 시스템이 원격 컴퓨터에 없는 경우 명령이 실패 합니다.

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

### -UseWindowsPowerShell

{{Fill UseWindowsPowerShell Description}}

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: UseWindowsPowerShellParameterSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 about_CommonParameters(https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.string, SYSTEM.URI, Runspace. n a m a.

문자열, URI 또는 세션 개체를이 cmdlet으로 파이프 할 수 있습니다.

## 출력

### Runspace입니다.

## 참고

- 이 cmdlet은 PowerShell 원격 인프라를 사용 합니다. 이 cmdlet을 사용 하려면 PowerShell 원격을 사용 하도록 로컬 컴퓨터와 모든 원격 컴퓨터를 구성 해야 합니다. 자세한 내용은 [about_Remote_Requirements](About/about_Remote_Requirements.md)을 참조하세요.
- 로컬 컴퓨터에서 **PSSession** 을 만들려면 관리자 권한으로 실행 옵션을 사용 하 여 PowerShell을 시작 합니다.
- **Pssession** 을 마친 후에는 cmdlet을 사용 `Remove-PSSession` 하 여 **pssession** 을 삭제 하 고 해당 리소스를 해제 합니다.
- **HostName** 및 **SSHConnection** 매개 변수 집합은 PowerShell 6.0부터 포함 되었습니다.
  Secure Shell (SSH)를 기반으로 PowerShell 원격 기능을 제공 하기 위해 추가 되었습니다. SSH와 PowerShell은 여러 플랫폼 (Windows, Linux, macOS)에서 지원 되며 powershell 원격은 PowerShell 및 SSH가 설치 되 고 구성 되는 이러한 플랫폼에서 작동 합니다. 이는 WinRM을 기반으로 하는 이전 Windows 전용 원격 시스템과 별개 이며, 대부분의 WinRM 특정 기능 및 제한 사항이 적용 되지 않습니다. 예를 들어 WinRM 기반 할당량, 세션 옵션, 사용자 지정 끝점 구성 및 연결 끊기/다시 연결 기능은 현재 지원 되지 않습니다. PowerShell SSH 원격을 설정 하는 방법에 대 한 자세한 내용은 [ssh를 통한 Powershell 원격](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core)을 참조 하세요.

## 관련 링크

[Connect-PSSession](Connect-PSSession.md)

[Disconnect-PSSession](Disconnect-PSSession.md)

[Enter-PSSession](Enter-PSSession.md)

[Exit-PSSession](Exit-PSSession.md)

[Get-PSSession](Get-PSSession.md)

[Invoke-Command](Invoke-Command.md)

[Receive-PSSession](Receive-PSSession.md)

[Remove-PSSession](Remove-PSSession.md)

