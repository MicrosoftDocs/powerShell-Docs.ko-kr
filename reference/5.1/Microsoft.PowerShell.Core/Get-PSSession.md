---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 5/15/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-pssession?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSSession
ms.openlocfilehash: c9c927ccdbc70d07ad8fa2cf13f3e2fe4a83f8c5
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/23/2020
ms.locfileid: "93218217"
---
# Get-PSSession

## 개요
로컬 및 원격 컴퓨터의 PowerShell 세션을 가져옵니다.

## SYNTAX

### 이름 (기본값)

```
Get-PSSession [-Name <String[]>] [<CommonParameters>]
```

### 컴퓨터 이름

```
Get-PSSession [-ComputerName] <String[]> [-ApplicationName <String>] [-ConfigurationName <String>]
 [-Name <String[]>] [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [-Port <Int32>] [-UseSSL] [-ThrottleLimit <Int32>]
 [-State <SessionFilterState>] [-SessionOption <PSSessionOption>] [<CommonParameters>]
```

### ComputerInstanceId

```
Get-PSSession [-ComputerName] <String[]> [-ApplicationName <String>] [-ConfigurationName <String>]
 -InstanceId <Guid[]> [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [-Port <Int32>] [-UseSSL] [-ThrottleLimit <Int32>]
 [-State <SessionFilterState>] [-SessionOption <PSSessionOption>] [<CommonParameters>]
```

### ConnectionUriInstanceId

```
Get-PSSession [-ConnectionUri] <Uri[]> [-ConfigurationName <String>] [-AllowRedirection] -InstanceId <Guid[]>
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [-ThrottleLimit <Int32>] [-State <SessionFilterState>] [-SessionOption <PSSessionOption>] [<CommonParameters>]
```

### ConnectionUri

```
Get-PSSession [-ConnectionUri] <Uri[]> [-ConfigurationName <String>] [-AllowRedirection] [-Name <String[]>]
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [-ThrottleLimit <Int32>] [-State <SessionFilterState>] [-SessionOption <PSSessionOption>] [<CommonParameters>]
```

### ContainerId

```
Get-PSSession [-ConfigurationName <String>] [-Name <String[]>] [-State <SessionFilterState>]
 -ContainerId <String[]> [<CommonParameters>]
```

### ContainerIdInstanceId

```
Get-PSSession [-ConfigurationName <String>] -InstanceId <Guid[]> [-State <SessionFilterState>]
 -ContainerId <String[]> [<CommonParameters>]
```

### VMId

```
Get-PSSession [-ConfigurationName <String>] [-Name <String[]>] [-State <SessionFilterState>] -VMId <Guid[]>
 [<CommonParameters>]
```

### VMIdInstanceId

```
Get-PSSession [-ConfigurationName <String>] -InstanceId <Guid[]> [-State <SessionFilterState>] -VMId <Guid[]>
 [<CommonParameters>]
```

### VMName

```
Get-PSSession [-ConfigurationName <String>] [-Name <String[]>] [-State <SessionFilterState>] -VMName <String[]>
 [<CommonParameters>]
```

### VMNameInstanceId

```
Get-PSSession [-ConfigurationName <String>] -InstanceId <Guid[]> [-State <SessionFilterState>]
 -VMName <String[]> [<CommonParameters>]
```

### InstanceId

```
Get-PSSession [-InstanceId <Guid[]>] [<CommonParameters>]
```

### Id

```
Get-PSSession [-Id] <Int32[]> [<CommonParameters>]
```

## 설명

`Get-PSSession`Cmdlet은 로컬 및 원격 컴퓨터의 사용자 관리 PowerShell 세션 ( **pssessions** )을 가져옵니다.

Windows PowerShell 3.0부터 세션은 각 연결의 원격 끝에 있는 컴퓨터에 저장 됩니다. 의 **ComputerName** 또는 **connectionuri** 매개 변수를 사용 하 여 `Get-PSSession` 현재 세션에서 생성 되지 않은 경우에도 로컬 컴퓨터 또는 원격 컴퓨터에 연결 되는 세션을 가져올 수 있습니다.

매개 변수가 없으면 `Get-PSSession` 현재 세션에서 만들어진 모든 세션을 가져옵니다.

**Name** , **ID** , **InstanceID** , **State** , **ApplicationName** 및 **ConfigurationName** 을 비롯 한 필터링 매개 변수를 사용 하 여에서 반환 하는 세션 중에서 선택할 수 `Get-PSSession` 있습니다.

`Get-PSSession` **ComputerName** 또는 **connectionuri** 매개 변수를 사용할 때 명령이 실행 되는 임시 연결을 구성 하려면 나머지 매개 변수를 사용 합니다.

참고: Windows PowerShell 2.0에서 매개 변수가 없는 경우 `Get-PSSession` 현재 세션에서 만들어진 모든 세션을 가져옵니다. **ComputerName** 매개 변수는 현재 세션에서 생성 된 세션을 가져오고 지정 된 컴퓨터에 연결 합니다.

PowerShell 세션에 대 한 자세한 내용은 [about_PSSessions](about/about_PSSessions.md)를 참조 하세요.

## 예제

### 예 1: 현재 세션에서 만든 세션 가져오기

```powershell
Get-PSSession
```

이 명령은 현재 세션에서 만들어진 모든 **pssession을 가져옵니다** . 다른 세션이 나 다른 컴퓨터에서 만들어진 pssession은이 컴퓨터에 연결 하는 경우에 **도 가져오지 않습니다** .

### 예 2: 로컬 컴퓨터에 연결 된 세션 가져오기

```powershell
Get-PSSession -ComputerName "localhost"
```

이 명령은 로컬 컴퓨터에 연결 된 **Pssessions** 를 가져옵니다. 로컬 컴퓨터를 나타내려면 컴퓨터 이름, localhost 또는 점 (.)을 입력 합니다.

이 명령은 다른 세션이나 다른 컴퓨터에서 만들어진 세션을 비롯하여 로컬 컴퓨터의 모든 세션을 반환합니다.

### 예 3: 컴퓨터에 연결 된 세션 가져오기

```powershell
Get-PSSession -ComputerName "Server02"
```

```Output
 Id Name            ComputerName    State         ConfigurationName     Availability
 -- ----            ------------    -----         -----------------     ------------
  2 Session3        Server02       Disconnected  ITTasks                       Busy
  1 ScheduledJobs   Server02       Opened        Microsoft.PowerShell     Available
  3 Test            Server02       Disconnected  Microsoft.PowerShell          Busy
```

이 명령은 Server02 컴퓨터에 연결 된 **Pssessions** 를 가져옵니다.

이 명령은 다른 세션이나 다른 컴퓨터에서 만들어진 세션을 비롯하여 Server02의 모든 세션을 반환합니다.

출력은 두 세션에 Disconnected 상태와 Busy 가용성이 있음을 보여 줍니다. 두 세션은 다른 세션에서 만들어졌으며 현재 사용 중입니다. 현재 세션에서 열려 있고 사용할 수 있는 ScheduledJobs 세션이 생성 되었습니다.

### 예제 4:이 명령의 결과 저장

```powershell
New-PSSession -ComputerName Server01, Server02, Server03
$s1, $s2, $s3 = Get-PSSession
```

이 예에서는 명령의 결과를 여러 변수에 저장 하는 방법을 보여 줍니다 `Get-PSSession` .

첫 번째 명령은 cmdlet을 사용 하 여 `New-PSSession` 세 개의 원격 컴퓨터에 pssession을 만듭니다. **PSSessions**

두 번째 명령은 cmdlet을 사용 하 여 `Get-PSSession` 세 개의 **PSSessions** pssession을 가져옵니다. 그런 다음 **별도의 변수에** 각 pssession을 저장 합니다.

PowerShell은 개체 배열을 변수 배열에 할당할 때 첫 번째 변수에 첫 번째 개체를 할당 하 고 두 번째 개체를 두 번째 변수에 할당 합니다. 개체가 변수보다 많을 경우 배열의 마지막 변수에 남은 개체를 모두 할당합니다. 변수가 개체보다 많을 경우 추가 변수는 사용되지 않습니다.

### 예 5: 인스턴스 ID를 사용 하 여 세션 삭제

```powershell
Get-PSSession | Format-Table -Property ComputerName, InstanceID
$s = Get-PSSession -InstanceID a786be29-a6bb-40da-80fb-782c67f7db0f
Remove-PSSession -Session $s
```

이 예제에서는 인스턴스 ID를 사용 하 여 **pssession** 을 가져온 다음 **pssession** 을 삭제 하는 방법을 보여 줍니다.

첫 번째 명령은 현재 세션에서 만들어진 모든 **pssession을 가져옵니다** . 이 명령은 각 **PSSession** 의 **ComputerName** 및 **InstanceID** 속성을 표시 하는 Format-Table cmdlet으로 **pssessions** 를 보냅니다.

두 번째 명령은 cmdlet을 사용 하 여 `Get-PSSession` 특정 **PSSession** 을 가져온 다음 변수에 저장 합니다 `$s` . 이 명령은 **InstanceID** 매개 변수를 사용 하 여 **PSSession** 을 식별 합니다.

세 번째 명령은 Remove-PSSession cmdlet을 사용 하 여 변수의 **PSSession** 을 삭제 합니다 `$s` .

### 예 6: 특정 이름을 가진 세션 가져오기

이 예제의 명령은 특정 이름 형식으로 되어 있으며 특정 세션 구성을 사용하는 세션을 찾아 연결합니다. 이러한 명령을 사용하면 동료가 작업을 시작한 세션을 찾아 연결하여 작업을 마칠 수 있습니다.

```powershell
Get-PSSession -ComputerName Server02, Server12 -Name BackupJob* -ConfigurationName ITTasks -SessionOption @{OperationTimeout=240000}
```

```Output
 Id Name            ComputerName    State         ConfigurationName     Availability
 -- ----            ------------    -----         -----------------     ------------
  3 BackupJob04     Server02        Disconnected        ITTasks                  None
```

```powershell
$s = Get-PSSession -ComputerName Server02 -Name BackupJob04 -ConfigurationName ITTasks | Connect-PSSession
$s
```

```Output
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 5 BackupJob04     Server02        Opened        ITTasks                  Available
```

첫 번째 명령은 Server02 및 Server12 원격 컴퓨터에서 이름이 BackupJob로 시작 하 고 ITTasks 세션 구성을 사용 하는 세션을 가져옵니다. 이 명령은 **name** 매개 변수를 사용 하 여 이름 패턴을 지정 하 고 **ConfigurationName** 매개 변수를 사용 하 여 세션 구성을 지정 합니다. **SessionOption** 매개 변수 값은 **OperationTimeout** 값을 240000밀리초(4분)로 설정하는 해시 테이블입니다. 이 설정은 명령을 완료 하는 데 더 많은 시간을 제공 합니다. **ConfigurationName** 및 **sessionoption** 매개 변수는 `Get-PSSession` 각 컴퓨터에서 cmdlet이 실행 되는 임시 세션을 구성 하는 데 사용 됩니다. 출력은 명령이 BackupJob04 세션을 반환 한다는 것을 보여 줍니다. 세션의 연결이 끊어져 **가용성이** None 이며 사용 중이 아님을 나타냅니다.

두 번째 명령은 cmdlet을 사용 하 여 `Get-PSSession` BackupJob04 세션을 가져오고 Connect-PSSession cmdlet을 사용 하 여 세션에 연결 합니다. 이 명령은 세션을 $s 변수에 저장합니다.

세 번째 명령은 $s 변수의 세션을 가져옵니다. 출력은 명령이 성공 했음을 보여 줍니다 `Connect-PSSession` . 세션이 **Opened** 상태이며 사용 가능합니다.

### 예 7: 해당 ID를 사용 하 여 세션 가져오기

```powershell
Get-PSSession -Id 2
```

이 명령은 ID가 2 인 **PSSession** 을 가져옵니다. **Id** 속성의 값은 현재 세션 에서만 고유 하기 때문에 **id** 매개 변수는 로컬 명령에 대해서만 유효 합니다.

## PARAMETERS

### -AllowRedirection

이 cmdlet이이 연결을 대체 URI (Uniform Resource Identifier)로 리디렉션할 수 있음을 나타냅니다. 기본적으로 PowerShell은 연결을 리디렉션하지 않습니다.

이 매개 변수는 `Get-PSSession` **connectionuri** 매개 변수를 사용 하 여 명령을 실행 하기 위해 만들어지는 임시 연결을 구성 합니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ConnectionUri, ConnectionUriInstanceId
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -ApplicationName

애플리케이션의 이름을 지정합니다. 이 cmdlet은 지정 된 응용 프로그램을 사용 하는 세션에만 연결 합니다.

연결 URI의 애플리케이션 이름 세그먼트를 입력합니다. 예를 들어, 다음 연결 URI에서 응용 프로그램 이름은 WSMan입니다 `http://localhost:5985/WSMAN` . 세션의 응용 프로그램 이름은 세션의 **Runspace.ConnectionInfo.AppName** 속성에 저장됩니다.

이 매개 변수 값은 세션을 선택 및 필터링하는 데 사용됩니다. 세션에서 사용하는 애플리케이션을 변경하지 않습니다.

```yaml
Type: System.String
Parameter Sets: ComputerInstanceId, ComputerName
Aliases:

Required: False
Position: Named
Default value: All sessions
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -인증

명령이 실행 되는 세션에 대 한 자격 증명을 인증 하는 데 사용 되는 메커니즘을 지정 합니다 `Get-PSSession` .

이 매개 변수는 `Get-PSSession` **ComputerName** 또는 **connectionuri** 매개 변수를 사용 하 여 명령을 실행 하기 위해 만들어지는 임시 연결을 구성 합니다.

이 매개 변수에 허용되는 값은 다음과 같습니다.

- 기본값
- Basic
- Credssp
- 다이제스트
- Kerberos
- Negotiate
- NegotiateWithImplicitCredential.

기본값은 Default입니다.

이 매개 변수 값에 대 한 자세한 내용은 MSDN library에서 [Authenticationmechanism 열거](https://msdn.microsoft.com/library/system.management.automation.runspaces.authenticationmechanism) 를 참조 하세요.

주의: 사용자의 자격 증명이 인증을 위해 원격 컴퓨터에 전달 되는 CredSSP (자격 증명 보안 지원 공급자) 인증은 원격 네트워크 공유에 액세스 하는 것과 같이 둘 이상의 리소스에서 인증이 필요한 명령에 대해 설계 되었습니다. 이렇게 하면 원격 작업의 보안 위험이 커집니다. 원격 컴퓨터가 손상된 경우 이 컴퓨터로 전달된 자격 증명을 사용하여 네트워크 세션을 제어할 수 있습니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUri, ConnectionUriInstanceId
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### -CertificateThumbprint

명령이 실행 되는 세션을 만들 수 있는 권한이 있는 사용자 계정의 디지털 공개 키 인증서 (X509)를 지정 합니다 `Get-PSSession` . 인증서의 인증서 지문을 입력합니다.

이 매개 변수는 `Get-PSSession` **ComputerName** 또는 **connectionuri** 매개 변수를 사용 하 여 명령을 실행 하기 위해 만들어지는 임시 연결을 구성 합니다.

인증서는 클라이언트 인증서 기반 인증에 사용됩니다. 인증서는 로컬 사용자 계정에만 매핑할 수 있으며 도메인 계정에는 사용할 수 없습니다.

인증서 지문을 가져오려면 PowerShell Cert: 드라이브에서 Get-Item 또는 Get-ChildItem 명령을 사용 합니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.String
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUri, ConnectionUriInstanceId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

컴퓨터 이름 배열을 지정 합니다. 지정한 컴퓨터에 연결되는 세션을 가져옵니다.
와일드카드 문자는 사용할 수 없습니다. 기본값은 없습니다.

Windows PowerShell 3.0부터 **PSSession** 개체는 각 연결의 원격 끝에 있는 컴퓨터에 저장 됩니다. 지정 된 컴퓨터의 세션을 가져오기 위해 PowerShell은 각 컴퓨터에 대 한 임시 연결을 만들고 `Get-PSSession` 명령을 실행 합니다.

하나 이상 컴퓨터의 NetBIOS 이름, IP 주소 또는 정규화된 도메인 이름을 입력하세요. 로컬 컴퓨터를 지정 하려면 컴퓨터 이름, localhost 또는 점 (.)을 입력 합니다.

참고:이 매개 변수는 Windows PowerShell 3.0 이상 버전의 PowerShell을 실행 하는 컴퓨터 에서만 세션을 가져옵니다. 이전 버전은 세션을 저장하지 않습니다.

```yaml
Type: System.String[]
Parameter Sets: ComputerInstanceId, ComputerName
Aliases: Cn

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ConfigurationName

구성의 이름을 지정 합니다. 이 cmdlet은 지정 된 세션 구성을 사용 하는 세션만 가져옵니다.

세션 구성의 구성 이름 또는 정규화된 리소스 URI를 입력합니다. 구성 이름만 지정 하는 경우에는 다음 스키마 URI가 앞에와 야 `http://schemas.microsoft.com/powershell` 합니다. 세션의 구성 이름은 세션의 **ConfigurationName** 속성에 저장됩니다.

이 매개 변수 값은 세션을 선택 및 필터링하는 데 사용됩니다. 세션에서 사용하는 세션 구성을 변경하지 않습니다.

세션 구성에 대 한 자세한 내용은 [about_Session_Configurations](About/about_Session_Configurations.md)를 참조 하세요.

```yaml
Type: System.String
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUri, ConnectionUriInstanceId, ContainerId, ContainerIdInstanceId, VMId, VMIdInstanceId, VMName, VMNameInstanceId
Aliases:

Required: False
Position: Named
Default value: All sessions
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ConnectionUri

명령이 실행 되는 임시 세션의 연결 끝점을 정의 하는 URI를 지정 합니다 `Get-PSSession` . URI는 정규화된 URI여야 합니다.

이 매개 변수는 `Get-PSSession` **connectionuri** 매개 변수를 사용 하 여 명령을 실행 하기 위해 만들어지는 임시 연결을 구성 합니다.

이 문자열의 형식은 다음과 같습니다.

`<Transport>://<ComputerName>:<Port\>/<ApplicationName>`

기본값은 `http://localhost:5985/WSMAN` 입니다.

**Connectionuri** 를 지정 하지 않으면 **UseSSL** , **ComputerName** , **Port** 및 **ApplicationName** 매개 변수를 사용 하 여 **connectionuri** 값을 지정할 수 있습니다. URI의 전송 세그먼트에 유효한 값은 HTTP 및 HTTPS입니다. 전송 세그먼트를 사용 하 여 연결 URI를 지정 하 고 포트를 지정 하지 않으면 세션은 표준 포트 80 (HTTP의 경우, HTTPS의 경우 443)를 사용 하 여 만들어집니다. PowerShell 원격을 위한 기본 포트를 사용 하려면 HTTP의 경우 포트 5985을, HTTPS의 경우 5986을 지정 합니다.

대상 컴퓨터에서 연결을 다른 URI로 리디렉션하는 경우 명령에서 **allowredirection** 매개 변수를 사용 하지 않으면 PowerShell에서 리디렉션을 방지 합니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

이 매개 변수는 windows powershell 3.0 이상 버전의 Windows PowerShell을 실행 하는 컴퓨터 에서만 세션을 가져옵니다. 이전 버전은 세션을 저장하지 않습니다.

```yaml
Type: System.Uri[]
Parameter Sets: ConnectionUri, ConnectionUriInstanceId
Aliases: URI, CU

Required: True
Position: 0
Default value: Http://localhost:5985/WSMAN
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ContainerId

컨테이너의 Id 배열을 지정 합니다. 이 cmdlet은 지정 된 각 컨테이너와 대화형 세션을 시작 합니다. 명령을 사용 `docker ps` 하 여 컨테이너 id 목록을 가져옵니다. 자세한 내용은 [docker ps](https://docs.docker.com/engine/reference/commandline/ps/) 명령에 대 한 도움말을 참조 하세요.

```yaml
Type: System.String[]
Parameter Sets: ContainerId, ContainerIdInstanceId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Credential

사용자 자격 증명을 지정 합니다. 이 cmdlet은 지정 된 사용자의 권한으로 명령을 실행 합니다. 원격 컴퓨터에 연결할 수 있는 권한을 가진 사용자 계정을 지정 하 고 `Get-PSSession` 명령을 실행 합니다. 기본값은 현재 사용자입니다.

**User01** 또는 **Domain01\User01** 과 같은 사용자 이름을 입력 하거나 cmdlet에 의해 생성 된 **PSCredential** 개체를 입력 합니다 `Get-Credential` . 사용자 이름을 입력 하면 암호를 입력 하 라는 메시지가 표시 됩니다.

자격 증명은 [PSCredential](/dotnet/api/system.management.automation.pscredential) 개체에 저장 되 고 암호는 [SecureString](/dotnet/api/system.security.securestring)으로 저장 됩니다.

> [!NOTE]
> **Securestring** 데이터 보호에 대 한 자세한 [내용은 참조 하십시오](/dotnet/api/system.security.securestring#how-secure-is-securestring).

이 매개 변수 `Get-PSSession` 는 **ComputerName** 또는 **connectionuri** 매개 변수를 사용 하 여 명령을 실행 하기 위해 만들어지는 임시 연결을 구성 합니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUri, ConnectionUriInstanceId
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### -Id

세션 Id의 배열을 지정 합니다. 이 cmdlet은 지정 된 Id를 가진 세션만 가져옵니다. 하나 이상의 Id를 쉼표로 구분 하 여 입력 하거나 범위 연산자 (...)를 사용 하 여 Id 범위를 지정 합니다. **ComputerName** 매개 변수와 함께 ID 매개 변수를 사용할 수 없습니다.

ID는 현재 세션의 사용자 관리 세션을 고유 하 게 식별 하는 정수입니다. **InstanceId** 보다 쉽게 기억할 수 있으며 입력 하는 것은 쉽지만 현재 세션 내 에서만 고유 합니다. 세션 ID는 세션의 ID 속성에 저장됩니다.

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases:

Required: True
Position: 0
Default value: All sessions
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -InstanceId

세션의 인스턴스 Id 배열을 지정 합니다. 이 cmdlet은 지정 된 인스턴스 Id를 가진 세션만 가져옵니다.

인스턴스 ID는 로컬 또는 원격 컴퓨터의 세션을 고유하게 식별하는 GUID입니다. **InstanceID** 는 PowerShell에서 여러 세션을 실행 하는 경우에도 고유 합니다.

세션의 인스턴스 ID는 세션의 **InstanceID** 속성에 저장됩니다.

```yaml
Type: System.Guid[]
Parameter Sets: ComputerInstanceId, ConnectionUriInstanceId, ContainerIdInstanceId, VMIdInstanceId, VMNameInstanceId, InstanceId
Aliases:

Required: True (ComputerInstanceId, ConnectionUriInstanceId, ContainerIdInstanceId, VMIdInstanceId, VMNameInstanceId), False (InstanceId)
Position: Named
Default value: All sessions
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

세션 이름 배열을 지정 합니다. 이 cmdlet은 지정한 이름을 가진 세션만 가져옵니다. 와일드카드 문자를 사용할 수 있습니다.

세션 이름은 세션의 **Name** 속성에 저장됩니다.

```yaml
Type: System.String[]
Parameter Sets: Name, ComputerName, ConnectionUri, ContainerId, VMId, VMName
Aliases:

Required: False
Position: Named
Default value: All sessions
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Port

명령이 실행 되는 임시 연결에 사용 되는 지정 된 네트워크 포트를 지정 합니다 `Get-PSSession` . 원격 컴퓨터에 연결하려면 원격 컴퓨터가 연결에서 사용하는 포트에서 수신 대기하고 있어야 합니다. 기본 포트는 HTTP의 WinRM 포트인 5985이 고, HTTPS의 경우 WinRM 포트인 5986입니다.

대체 포트를 사용하려면 먼저 원격 컴퓨터에 해당 포트에서 수신 대기할 WinRM 수신기를 구성해야 합니다. 수신기를 구성 하려면 PowerShell 프롬프트에 다음 두 명령을 입력 합니다.

`Remove-Item -Path WSMan:\Localhost\listener\listener* -Recurse`

`New-Item -Path WSMan:\Localhost\listener -Transport http -Address * -Port \<port-number\>`

이 매개 변수 `Get-PSSession` 는 **ComputerName** 또는 **connectionuri** 매개 변수를 사용 하 여 명령을 실행 하기 위해 만들어지는 임시 연결을 구성 합니다.

필요한 경우가 아니면 **Port** 매개 변수를 사용하지 마세요. 명령에 설정 된 **포트** 는 명령이 실행 되는 모든 컴퓨터 또는 세션에 적용 됩니다. 대체 포트 설정을 사용하면 일부 컴퓨터에서 명령이 실행되지 않을 수 있습니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Int32
Parameter Sets: ComputerInstanceId, ComputerName
Aliases:

Required: False
Position: Named
Default value: 5985, 5986
Accept pipeline input: False
Accept wildcard characters: False
```

### -SessionOption

세션에 대 한 고급 옵션을 지정 합니다. New-PSSessionOption cmdlet을 사용 하 여 만든 것과 같은 **sessionoption** 개체를 입력 하거나 키가 세션 옵션 이름이 고 값이 session 옵션 값인 해시 테이블을 입력 합니다.

옵션의 기본값은 $PSSessionOption 기본 설정 변수 값(설정되어 있는 경우)에 따라 결정됩니다. 그러지 않으면 기본값은 세션 구성에 설정된 옵션에 따라 설정됩니다.

세션 옵션 값은 $PSSessionOption 기본 설정 변수 및 세션 구성에 설정된 세션의 기본값보다 우선합니다. 그러나 이러한 값은 세션 구성에 설정된 최대값, 할당량 또는 제한보다 우선하지 않습니다.

기본값을 포함 하 여 세션 옵션에 대 한 자세한 내용은을 참조 하십시오 `New-PSSessionOption` .
기본 설정 변수에 대 한 자세한 내용은 `$PSSessionOption` [about_Preference_Variables](About/about_Preference_Variables.md)를 참조 하세요. 세션 구성에 대 한 자세한 내용은 [about_Session_Configurations](About/about_Session_Configurations.md)를 참조 하세요.

```yaml
Type: System.Management.Automation.Remoting.PSSessionOption
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUri, ConnectionUriInstanceId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -상태

세션 상태를 지정 합니다. 이 cmdlet은 지정 된 상태의 세션만 가져옵니다. 이 매개 변수에 허용 되는 값은 모두, 열린, 연결 끊김, 닫힘 및 손상입니다. 기본값은 All입니다.

세션 상태 값은 현재 세션을 기준으로 합니다. 현재 세션에서 만들어지지 않았으며 현재 세션에 연결되지 않은 세션은 다른 세션에 연결된 경우에도 Disconnected 상태입니다.

세션 상태는 세션의 **State** 속성에 저장됩니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: Microsoft.PowerShell.Commands.SessionFilterState
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUri, ConnectionUriInstanceId, ContainerId, ContainerIdInstanceId, VMId, VMIdInstanceId, VMName, VMNameInstanceId
Aliases:
Accepted values: All, Opened, Disconnected, Closed, Broken

Required: False
Position: Named
Default value: All
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit

명령을 실행 하기 위해 설정할 수 있는 최대 동시 연결 수를 지정 합니다 `Get-PSSession` . 이 매개 변수를 생략하거나 값 0을 입력하면 기본값 32가 사용됩니다. 제한 한도는 현재 명령에만 적용되며 세션이나 컴퓨터에는 적용되지 않습니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Int32
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUri, ConnectionUriInstanceId
Aliases:

Required: False
Position: Named
Default value: 32
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseSSL

이 cmdlet이 SSL(Secure Sockets Layer) (SSL) 프로토콜을 사용 하 여 명령이 실행 되는 연결을 설정 함을 나타냅니다 `Get-PSSession` . 기본적으로 SSL은 사용되지 않습니다. 이 매개 변수를 사용하지만 명령에 사용되는 포트에서 SSL을 사용할 수 없는 경우 명령이 실패합니다.

이 매개 변수는 `Get-PSSession` **ComputerName** 매개 변수를 사용 하 여 명령을 실행 하기 위해 만들어지는 임시 연결을 구성 합니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerInstanceId, ComputerName
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -VMId

가상 컴퓨터의 ID 배열을 지정 합니다. 이 cmdlet은 지정 된 각 가상 컴퓨터와 대화형 세션을 시작 합니다. 사용할 수 있는 가상 컴퓨터를 보려면 다음 명령을 사용 합니다.

`Get-VM | Select-Object -Property Name, ID`

```yaml
Type: System.Guid[]
Parameter Sets: VMId, VMIdInstanceId
Aliases: VMGuid

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -VMName

가상 컴퓨터의 이름 배열을 지정합니다. 이 cmdlet은 지정 된 각 가상 컴퓨터와 대화형 세션을 시작 합니다. 사용할 수 있는 가상 컴퓨터를 확인 하려면 cmdlet을 사용 합니다 `Get-VM` .

```yaml
Type: System.String[]
Parameter Sets: VMName, VMNameInstanceId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### 없음

이 cmdlet에 입력을 파이프할 수 없습니다.

## 출력

### Runspace입니다.

## 참고

- 이 cmdlet은 새 PSSession, 및 Invoke-Command cmdlet을 사용 하 여 만든 것과 같은 사용자 관리 세션 **PSSession** 개체를 가져옵니다 `Enter-PSSession` . PowerShell을 시작할 때 만들어진 시스템 관리 세션은 가져오지 않습니다.
- Windows PowerShell 3.0부터 **PSSession** 개체는 연결의 서버 쪽 또는 수신 끝에 있는 컴퓨터에 저장 됩니다. PowerShell은 로컬 컴퓨터 또는 원격 컴퓨터에 저장 된 세션을 가져오기 위해 지정 된 컴퓨터에 대 한 임시 세션을 설정 하 고 세션에서 쿼리 명령을 실행 합니다.
- 원격 컴퓨터에 연결되는 세션을 가져오려면 **ComputerName** 또는 **ConnectionUri** 매개 변수를 사용하여 원격 컴퓨터를 지정합니다. 에서 가져오는 세션을 필터링 하려면 `Get-PSSession` **Name** , **ID** , **InstanceID** 및 **State** 매개 변수를 사용 합니다. 나머지 매개 변수를 사용 하 여에서 사용 하는 임시 세션을 구성 합니다 `Get-PSSession` .
- **ComputerName** 또는 **connectionuri** 매개 변수를 사용 하는 경우 `Get-PSSession` Windows PowerShell 3.0 이상 버전의 powershell을 실행 하는 컴퓨터의 세션만 가져옵니다.
- **PSSession** 의 **State** 속성 값은 현재 세션을 기준으로 합니다.
  따라서 **연결 끊김** 값은 **PSSession** 이 현재 세션에 연결 되지 않았음을 의미 합니다. 그러나 모든 세션에서 **PSSession** 의 연결이 끊어졌음을 의미 하는 것은 아닙니다. 다른 세션에 연결되어 있을 수도 있습니다. 현재 세션에서 **PSSession** 에 연결 하거나 다시 연결할 수 있는지 확인 하려면 **Availability** 속성을 사용 합니다.

**Availability** 값이 **None** 이면 세션에 연결할 수 있습니다. **사용 중** 값은 다른 세션에 연결 되어 있으므로 **PSSession** 에 연결할 수 없음을 나타냅니다.

세션의 **State** 속성 값에 대 한 자세한 내용은 [RunspaceState 열거형](https://msdn.microsoft.com/library/system.management.automation.runspaces.runspacestate)을 참조 하세요.

세션의 **Availability** 속성 값에 대 한 자세한 내용은 [RunspaceAvailability 열거형](https://msdn.microsoft.com/library/system.management.automation.runspaces.runspaceavailability)을 참조 하세요.

## 관련 링크

[Connect-PSSession](Connect-PSSession.md)

[Disconnect-PSSession](Disconnect-PSSession.md)

[Receive-PSSession](Receive-PSSession.md)

[Enter-PSSession](Enter-PSSession.md)

[Exit-PSSession](Exit-PSSession.md)

[Invoke-Command](Invoke-Command.md)

[New-PSSession](New-PSSession.md)

[Remove-PSSession](Remove-PSSession.md)

[about_PSSessions](About/about_PSSessions.md)

[about_Remote](About/about_Remote.md)
