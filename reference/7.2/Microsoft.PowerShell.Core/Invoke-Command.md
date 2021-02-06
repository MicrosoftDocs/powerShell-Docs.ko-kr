---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/invoke-command?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-Command
ms.openlocfilehash: d8f0a8a56792a39371a307166788f047fec99a9a
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599959"
---
# Invoke-Command

## 개요
로컬 및 원격 컴퓨터에서 명령을 실행합니다.

## SYNTAX

### InProcess (기본값)

```
Invoke-Command [-ScriptBlock] <ScriptBlock> [-NoNewScope] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [<CommonParameters>]
```

### FilePathRunspace

```
Invoke-Command [[-Session] <PSSession[]>] [-ThrottleLimit <Int32>] [-AsJob] [-HideComputerName]
 [-JobName <String>] [-FilePath] <String> [-RemoteDebug] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [<CommonParameters>]
```

### 세션

```
Invoke-Command [[-Session] <PSSession[]>] [-ThrottleLimit <Int32>] [-AsJob] [-HideComputerName]
 [-JobName <String>] [-ScriptBlock] <ScriptBlock> [-RemoteDebug] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [<CommonParameters>]
```

### FilePathComputerName

```
Invoke-Command [[-ComputerName] <String[]>] [-Credential <PSCredential>] [-Port <Int32>] [-UseSSL]
 [-ConfigurationName <String>] [-ApplicationName <String>] [-ThrottleLimit <Int32>] [-AsJob]
 [-InDisconnectedSession] [-SessionName <String[]>] [-HideComputerName] [-JobName <String>]
 [-FilePath] <String> [-SessionOption <PSSessionOption>] [-Authentication <AuthenticationMechanism>]
 [-EnableNetworkAccess] [-RemoteDebug] [-InputObject <PSObject>] [-ArgumentList <Object[]>]
 [<CommonParameters>]
```

### 컴퓨터 이름

```
Invoke-Command [[-ComputerName] <String[]>] [-Credential <PSCredential>] [-Port <Int32>] [-UseSSL]
 [-ConfigurationName <String>] [-ApplicationName <String>] [-ThrottleLimit <Int32>] [-AsJob]
 [-InDisconnectedSession] [-SessionName <String[]>] [-HideComputerName] [-JobName <String>]
 [-ScriptBlock] <ScriptBlock> [-SessionOption <PSSessionOption>]
 [-Authentication <AuthenticationMechanism>] [-EnableNetworkAccess] [-RemoteDebug]
 [-InputObject <PSObject>] [-ArgumentList <Object[]>] [-CertificateThumbprint <String>]
 [<CommonParameters>]
```

### URI

```
Invoke-Command [-Credential <PSCredential>] [-ConfigurationName <String>] [-ThrottleLimit <Int32>]
 [[-ConnectionUri] <Uri[]>] [-AsJob] [-InDisconnectedSession] [-HideComputerName]
 [-JobName <String>] [-ScriptBlock] <ScriptBlock> [-AllowRedirection]
 [-SessionOption <PSSessionOption>] [-Authentication <AuthenticationMechanism>]
 [-EnableNetworkAccess] [-RemoteDebug] [-InputObject <PSObject>] [-ArgumentList <Object[]>]
 [-CertificateThumbprint <String>] [<CommonParameters>]
```

### FilePathUri

```
Invoke-Command [-Credential <PSCredential>] [-ConfigurationName <String>] [-ThrottleLimit <Int32>]
 [[-ConnectionUri] <Uri[]>] [-AsJob] [-InDisconnectedSession] [-HideComputerName]
 [-JobName <String>] [-FilePath] <String> [-AllowRedirection] [-SessionOption <PSSessionOption>]
 [-Authentication <AuthenticationMechanism>] [-EnableNetworkAccess] [-RemoteDebug]
 [-InputObject <PSObject>] [-ArgumentList <Object[]>] [<CommonParameters>]
```

### VMId

```
Invoke-Command -Credential <PSCredential> [-ConfigurationName <String>] [-ThrottleLimit <Int32>]
 [-AsJob] [-HideComputerName] [-ScriptBlock] <ScriptBlock> [-RemoteDebug] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [-VMId] <Guid[]> [<CommonParameters>]
```

### VMName

```
Invoke-Command -Credential <PSCredential> [-ConfigurationName <String>] [-ThrottleLimit <Int32>]
 [-AsJob] [-HideComputerName] [-ScriptBlock] <ScriptBlock> [-RemoteDebug] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] -VMName <String[]> [<CommonParameters>]
```

### FilePathVMId

```
Invoke-Command -Credential <PSCredential> [-ConfigurationName <String>] [-ThrottleLimit <Int32>]
 [-AsJob] [-HideComputerName] [-FilePath] <String> [-RemoteDebug] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [-VMId] <Guid[]> [<CommonParameters>]
```

### FilePathVMName

```
Invoke-Command -Credential <PSCredential> [-ConfigurationName <String>] [-ThrottleLimit <Int32>]
 [-AsJob] [-HideComputerName] [-FilePath] <String> [-RemoteDebug] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] -VMName <String[]> [<CommonParameters>]
```

### SSHHost

```
Invoke-Command [-Port <Int32>] [-AsJob] [-HideComputerName] [-JobName <String>]
 [-ScriptBlock] <ScriptBlock> -HostName <String[]> [-UserName <String>] [-KeyFilePath <String>]
 [-SSHTransport] [-RemoteDebug] [-InputObject <PSObject>] [-ArgumentList <Object[]>]
 [-Subsystem <String>] [<CommonParameters>]
```

### ContainerId

```
Invoke-Command [-ConfigurationName <String>] [-ThrottleLimit <Int32>] [-AsJob] [-HideComputerName]
 [-JobName <String>] [-ScriptBlock] <ScriptBlock> [-RunAsAdministrator] [-RemoteDebug]
 [-InputObject <PSObject>] [-ArgumentList <Object[]>] -ContainerId <String[]> [<CommonParameters>]
```

### FilePathContainerId

```
Invoke-Command [-ConfigurationName <String>] [-ThrottleLimit <Int32>] [-AsJob] [-HideComputerName]
 [-JobName <String>] [-FilePath] <String> [-RunAsAdministrator] [-RemoteDebug]
 [-InputObject <PSObject>] [-ArgumentList <Object[]>] -ContainerId <String[]> [<CommonParameters>]
```

### SSHHostHashParam

```
Invoke-Command [-AsJob] [-HideComputerName] [-JobName <String>] [-ScriptBlock] <ScriptBlock>
 -SSHConnection <Hashtable[]> [-RemoteDebug] [-InputObject <PSObject>] [-ArgumentList <Object[]>]
 [<CommonParameters>]
```

### FilePathSSHHost

```
Invoke-Command [-AsJob] [-HideComputerName] -FilePath <String> -HostName <String[]>
 [-UserName <String>] [-KeyFilePath <String>] [-SSHTransport] [-RemoteDebug]
 [-InputObject <PSObject>] [-ArgumentList <Object[]>] [<CommonParameters>]
```

### FilePathSSHHostHash

```
Invoke-Command [-AsJob] [-HideComputerName] -FilePath <String> -SSHConnection <Hashtable[]>
 [-RemoteDebug] [-InputObject <PSObject>] [-ArgumentList <Object[]>] [<CommonParameters>]
```

## 설명

`Invoke-Command`Cmdlet은 로컬 또는 원격 컴퓨터에서 명령을 실행 하 고 오류를 포함 하 여 명령에서 모든 출력을 반환 합니다. 단일 명령을 사용 하 여 `Invoke-Command` 여러 컴퓨터에서 명령을 실행할 수 있습니다.

원격 컴퓨터에서 명령 중 하나를 실행하려면 **ComputerName** 매개 변수를 사용합니다. 데이터를 공유 하는 일련의 관련 명령을 실행 하려면 cmdlet을 사용 하 여 `New-PSSession` 원격 컴퓨터에서 **pssession** (영구 연결)을 만든 다음의 **Session** 매개 변수를 사용 하 여 `Invoke-Command` **pssession** 에서 명령을 실행 합니다. 연결이 끊긴 세션에서 명령을 실행하려면 **InDisconnectedSession** 매개 변수를 사용합니다. 백그라운드 작업에서 명령을 실행하려면 **AsJob** 매개 변수를 사용합니다.

`Invoke-Command`로컬 컴퓨터에서 스크립트 블록에 명령으로를 사용할 수도 있습니다. PowerShell은 현재 범위의 자식 범위에서 즉시 스크립트 블록을 실행 합니다.

를 사용 하 여 `Invoke-Command` 원격 컴퓨터에서 명령을 실행 하기 전에 [about_Remote](./About/about_Remote.md)을 읽습니다.

PowerShell 6.0부터 SSH (Secure Shell)를 사용 하 여 원격 컴퓨터에 대 한 연결을 설정 하 고 명령을 호출할 수 있습니다. SSH는 로컬 컴퓨터에 설치 해야 하 고 원격 컴퓨터는 PowerShell SSH 끝점을 사용 하 여 구성 해야 합니다. SSH 기반 PowerShell 원격 세션의 혜택은 여러 플랫폼 (Windows, Linux, macOS)에서 작동 한다는 것입니다. SSH 기반 세션의 경우 **HostName** 또는 **SSHConnection** 매개 변수를 사용 하 여 원격 컴퓨터 및 관련 연결 정보를 지정 합니다. PowerShell SSH 원격을 설정 하는 방법에 대 한 자세한 내용은 [ssh를 통한 Powershell 원격](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core)을 참조 하세요.

일부 코드 샘플에서는 스 플랫를 사용 하 여 줄 길이를 줄입니다. 자세한 내용은 [about_Splatting](./About/about_Splatting.md)를 참조 하세요.

## 예제

### 예제 1: 서버에서 스크립트 실행

이 예에서는 `Test.ps1` Server01 컴퓨터에서 스크립트를 실행 합니다.

```powershell
Invoke-Command -FilePath c:\scripts\test.ps1 -ComputerName Server01
```

**FilePath** 매개 변수는 로컬 컴퓨터에 있는 스크립트를 지정 합니다. 원격 컴퓨터에서 스크립트가 실행되고 그 결과가 로컬 컴퓨터로 반환됩니다.

### 예 2: 원격 서버에서 명령 실행

이 예제에서는 `Get-Culture` Server01 원격 컴퓨터에서 명령을 실행 합니다.

```powershell
Invoke-Command -ComputerName Server01 -Credential Domain01\User01 -ScriptBlock { Get-Culture }
```

**ComputerName** 매개 변수는 원격 컴퓨터의 이름을 지정 합니다. **Credential** 매개 변수는 명령을 실행할 권한이 있는 사용자 인 Domain01\User01의 보안 컨텍스트에서 명령을 실행 하는 데 사용 됩니다. **ScriptBlock** 매개 변수는 원격 컴퓨터에서 실행할 명령을 지정 합니다.

이에 대 한 응답으로 PowerShell은 User01 계정에 대 한 암호와 인증 방법을 요청 합니다.
Server01 컴퓨터에서 이 명령을 실행하고 결과를 반환합니다.

### 예제 3: 영구 연결에서 명령 실행

이 예에서는 `Get-Culture` Server02 이라는 원격 컴퓨터에서 영구 연결을 사용 하 여 세션에서 동일한 명령을 실행 합니다.

```powershell
$s = New-PSSession -ComputerName Server02 -Credential Domain01\User01
Invoke-Command -Session $s -ScriptBlock {Get-Culture}
```

`New-PSSession`Cmdlet은 Server02 원격 컴퓨터에서 세션을 만들어 변수에 저장 합니다 `$s` . 일반적으로 원격 컴퓨터에서 일련의 명령을 실행 하는 경우에만 세션을 만듭니다.

`Invoke-Command`Cmdlet은 `Get-Culture` Server02에서 명령을 실행 합니다. **Session** 매개 변수는 변수에 저장 된 세션을 지정 합니다 `$s` .

이에 대 한 응답으로 PowerShell은 Server02 컴퓨터의 세션에서 명령을 실행 합니다.

### 예제 4: 세션을 사용 하 여 데이터를 공유 하는 일련의 명령 실행

이 예에서는의 **ComputerName** 및 **Session** 매개 변수를 사용한 결과를 비교 합니다 `Invoke-Command` . 세션을 사용하여 동일한 데이터를 공유하는 일련의 명령을 실행하는 방법을 보여 줍니다.

```powershell
Invoke-Command -ComputerName Server02 -ScriptBlock {$p = Get-Process PowerShell}
Invoke-Command -ComputerName Server02 -ScriptBlock {$p.VirtualMemorySize}
$s = New-PSSession -ComputerName Server02
Invoke-Command -Session $s -ScriptBlock {$p = Get-Process PowerShell}
Invoke-Command -Session $s -ScriptBlock {$p.VirtualMemorySize}
```

```Output
17930240
```

처음 두 명령은의 **ComputerName** 매개 변수를 사용 `Invoke-Command` 하 여 Server02 원격 컴퓨터에서 명령을 실행 합니다. 첫 번째 명령은 cmdlet을 사용 하 여 `Get-Process` 원격 컴퓨터의 PowerShell 프로세스를 가져온 다음 변수에 저장 합니다 `$p` . 두 번째 명령은 PowerShell 프로세스의 **VirtualMemorySize** 속성 값을 가져옵니다.

**ComputerName** 매개 변수를 사용 하는 경우 PowerShell은 명령을 실행할 새 세션을 만듭니다.
명령이 완료 되 면 세션이 닫힙니다. `$p`변수가 하나의 연결에서 만들어졌지만 두 번째 명령을 위해 만들어진 연결에는 없습니다.

이 문제는 원격 컴퓨터에서 영구 세션을 만든 다음 동일한 세션에서 두 명령을 실행 하 여 해결할 수 있습니다.

`New-PSSession`Cmdlet은 컴퓨터 Server02에 영구 세션을 만들고이 세션을 `$s` 변수에 저장 합니다. `Invoke-Command`다음 줄은 **session** 매개 변수를 사용 하 여 동일한 세션에서 두 명령을 실행 합니다. 두 명령이 모두 동일한 세션에서 실행 되므로 값은 `$p` 활성 상태로 유지 됩니다.

### 예 5: 지역 변수에 저장 된 명령 입력

이 예에서는 지역 변수에 스크립트 블록으로 저장 된 명령을 만드는 방법을 보여 줍니다.
스크립트 블록을 지역 변수에 저장 하는 경우 변수를 **ScriptBlock** 매개 변수 값으로 지정할 수 있습니다.

```powershell
$command = { Get-WinEvent -LogName PowerShellCore/Operational |
  Where-Object {$_.Message -like "*certificate*"} }
Invoke-Command -ComputerName S1, S2 -ScriptBlock $command
```

`$command`변수는 `Get-WinEvent` 스크립트 블록으로 형식이 지정 된 명령을 저장 합니다. 는 `Invoke-Command` `$command` S1 및 S2 원격 컴퓨터의에 저장 된 명령을 실행 합니다.

### 예제 6: 여러 컴퓨터에서 단일 명령 실행

이 예제에서는를 사용 하 여 `Invoke-Command` 여러 컴퓨터에서 단일 명령을 실행 하는 방법을 보여 줍니다.

```powershell
$parameters = @{
  ComputerName = "Server01", "Server02", "TST-0143", "localhost"
  ConfigurationName = 'MySession.PowerShell'
  ScriptBlock = { Get-WinEvent -LogName PowerShellCore/Operational }
}
Invoke-Command @parameters
```

**ComputerName** 매개 변수는 쉼표로 구분 된 컴퓨터 이름 목록을 지정 합니다. 컴퓨터 목록에는 로컬 컴퓨터를 나타내는 localhost 값이 포함 되어 있습니다. **ConfigurationName** 매개 변수는 대체 세션 구성을 지정 합니다. **ScriptBlock** 매개 변수는 `Get-WinEvent` 를 실행 하 여 각 컴퓨터에서 Powershellcore/Operational 이벤트 로그를 가져옵니다.

### 예 7: 여러 컴퓨터에서 호스트 프로그램의 버전 가져오기

이 예제에서는 200 원격 컴퓨터에서 실행 되는 PowerShell 호스트 프로그램의 버전을 가져옵니다.

```powershell
$version = Invoke-Command -ComputerName (Get-Content Machines.txt) -ScriptBlock {(Get-Host).Version}
```

하나의 명령만 실행 되므로 각 컴퓨터에 대 한 영구 연결을 만들 필요가 없습니다. 대신 이 명령은 **ComputerName** 매개 변수를 사용하여 컴퓨터를 지정합니다. 컴퓨터를 지정 하기 위해 cmdlet을 사용 하 여 `Get-Content` 컴퓨터 이름 파일의 Machine.txt 파일의 내용을 가져옵니다.

`Invoke-Command`Cmdlet은 `Get-Host` 원격 컴퓨터에서 명령을 실행 합니다. 점 표기법을 사용 하 여 PowerShell 호스트의 **Version** 속성을 가져옵니다.

이러한 명령은 한 번에 하나씩 실행 됩니다. 명령이 완료 되 면 모든 컴퓨터의 명령 출력이 변수에 저장 됩니다 `$version` . 출력에는 데이터가 제공된 컴퓨터의 이름이 포함됩니다.

### 예 8: 여러 원격 컴퓨터에서 백그라운드 작업 실행

이 예제에서는 두 원격 컴퓨터에서 명령을 실행 합니다. `Invoke-Command`이 명령은 **AsJob** 매개 변수를 사용 하 여 명령이 백그라운드 작업으로 실행 되도록 합니다. 명령은 원격 컴퓨터에서 실행 되지만 작업은 로컬 컴퓨터에 있습니다. 결과는 로컬 컴퓨터에 전송 됩니다.

```powershell
$s = New-PSSession -ComputerName Server01, Server02
Invoke-Command -Session $s -ScriptBlock {Get-EventLog system} -AsJob
```

```Output
Id   Name    State      HasMoreData   Location           Command
---  ----    -----      -----         -----------        ---------------
1    Job1    Running    True          Server01,Server02  Get-EventLog system
```

```powershell
$j = Get-Job
$j | Format-List -Property *
```

```Output
HasMoreData   : True
StatusMessage :
Location      : Server01,Server02
Command       : Get-EventLog system
JobStateInfo  : Running
Finished      : System.Threading.ManualResetEvent
InstanceId    : e124bb59-8cb2-498b-a0d2-2e07d4e030ca
Id            : 1
Name          : Job1
ChildJobs     : {Job2, Job3}
Output        : {}
Error         : {}
Progress      : {}
Verbose       : {}
Debug         : {}
Warning       : {}
StateChanged  :
```

```powershell
$results = $j | Receive-Job
```

`New-PSSession`Cmdlet은 Server01 및 Server02 원격 컴퓨터에서 세션을 만듭니다. `Invoke-Command`Cmdlet은 각 세션에서 백그라운드 작업을 실행 합니다. 이 명령은 **AsJob** 매개 변수를 사용하여 백그라운드 작업으로 명령을 실행하며, 이 명령은 두 원격 컴퓨터에서 실행되는 각 작업에 해당하는 두 하위 작업 개체가 포함된 작업 개체를 반환합니다.

이 `Get-Job` 명령은 작업 개체를 `$j` 변수에 저장 합니다. `$j`그런 다음 변수를 cmdlet으로 파이프 하 여 `Format-List` 작업 개체의 모든 속성을 목록으로 표시 합니다. 마지막 명령은 작업의 결과를 가져옵니다. 에서 작업 개체를 `$j` cmdlet으로 파이프 하 `Receive-Job` 고 결과를 `$results` 변수에 저장 합니다.

### 예 9: 원격 컴퓨터에서 실행 되는 명령에 로컬 변수 포함

이 예제에서는 원격 컴퓨터에서 실행되는 명령에 로컬 변수 값을 포함하는 방법을 보여 줍니다. 이 명령은 scope 한정자를 사용 하 여 `Using` 원격 명령에서 지역 변수를 식별 합니다. 기본적으로 모든 변수는 원격 세션에서 정의된다고 가정됩니다. `Using`범위 한정자는 PowerShell 3.0에서 도입 되었습니다. 범위 한정자에 대 한 자세한 내용은 `Using` [about_Remote_Variables](./About/about_Remote_Variables.md) 및 [about_Scopes](./about/about_scopes.md)를 참조 하세요.

```powershell
$Log = "PowerShellCore/Operational"
Invoke-Command -ComputerName Server01 -ScriptBlock {Get-WinEvent -LogName $Using:Log -MaxEvents 10}
```

`$Log`변수는 이벤트 로그 (PowerShellCore/Operational)의 이름을 저장 합니다. 이 `Invoke-Command` cmdlet은 `Get-WinEvent` Server01에서 실행 되어 이벤트 로그에서 10 개의 최신 이벤트를 가져옵니다. **LogName** 매개 변수 값은 `$Log` `Using` 범위 한정자가 접두사로 지정 되어 원격 세션이 아닌 로컬 세션에서 생성 되었음을 나타내는 변수입니다.

### 예 10: 컴퓨터 이름 숨기기

이 예에서는의 **HideComputerName** 매개 변수를 사용한 결과를 보여 줍니다 `Invoke-Command` .
**HideComputerName** 는이 cmdlet이 반환 하는 개체를 변경 하지 않습니다. 표시만 변경 합니다. 여전히 **Format** cmdlet을 사용 하 여 영향을 받는 개체의 **PsComputerName** 속성을 표시할 수 있습니다.

```powershell
Invoke-Command -ComputerName S1, S2 -ScriptBlock {Get-Process PowerShell}
```

```Output
PSComputerName    Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id   ProcessName
--------------    -------  ------    -----      ----- -----   ------     --   -----------
S1                575      15        45100      40988   200     4.68     1392 PowerShell
S2                777      14        35100      30988   150     3.68     67   PowerShell
```

```powershell
Invoke-Command -ComputerName S1, S2 -ScriptBlock {Get-Process PowerShell} -HideComputerName
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id   ProcessName
-------  ------    -----      ----- -----   ------     --   -----------
575      15        45100      40988   200     4.68     1392 PowerShell
777      14        35100      30988   150     3.68     67   PowerShell
```

처음 두 명령은를 사용 `Invoke-Command` 하 여 `Get-Process` PowerShell 프로세스에 대 한 명령을 실행 합니다. 첫 번째 명령의 출력에는 명령이 실행된 컴퓨터의 이름을 포함하는 **PsComputerName** 속성이 포함됩니다. **HideComputerName** 를 사용 하는 두 번째 명령의 출력에는 **PsComputerName** 열이 포함 되지 않습니다.

### 예 11: 스크립트 블록에서 Param 키워드 사용

`Param`키워드 및 **argumentlist** 매개 변수는 스크립트 블록의 명명 된 매개 변수에 변수 값을 전달 하는 데 사용 됩니다. 이 예에서는 문자로 시작 하 `a` 고 확장을 포함 하는 파일 이름을 표시 합니다 `.pdf` .

키워드에 대 한 자세한 내용은 `Param` [about_Language_Keywords](./about/about_language_keywords.md#param)를 참조 하세요.

```powershell
$parameters = @{
    ComputerName = "Server01"
    ScriptBlock = { Param ($param1,$param2) Get-ChildItem -Name $param1 -Include $param2 }
    ArgumentList = "a*", "*.pdf"
}
Invoke-Command @parameters
```

```Output
aa.pdf
ab.pdf
ac.pdf
az.pdf
```

`Invoke-Command` 및의 두 변수를 정의 하는 **ScriptBlock** 매개 변수를 사용 `$param1` `$param2` 합니다. `Get-ChildItem` 명명 된 매개 변수, **이름** 및 변수 이름을 **포함** 하는을 사용 합니다. **Argumentlist** 는 변수에 값을 전달 합니다.

### 예 12: 스크립트 블록에서 $args 자동 변수 사용

`$args`자동 변수 및 **argumentlist** 매개 변수는 스크립트 블록의 매개 변수 위치에 배열 값을 전달 하는 데 사용 됩니다. 이 예제에서는 서버의 디렉터리 콘텐츠를 표시 `.txt` 합니다. `Get-ChildItem` **Path** 매개 변수는 position 0이 고 **필터** 매개 변수는 position입니다.
1.

변수에 대 한 자세한 내용은 `$args` 을 참조 하십시오 [about_Automatic_Variables](./about/about_automatic_variables.md#args)

```powershell
$parameters = @{
    ComputerName = "Server01"
    ScriptBlock = { Get-ChildItem $args[0] $args[1] }
    ArgumentList = "C:\Test", "*.txt*"
}
Invoke-Command @parameters
```

```Output
    Directory: C:\Test

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a---           6/12/2019    15:15            128 alog.txt
-a---           7/27/2019    15:16            256 blog.txt
-a---           9/28/2019    17:10             64 zlog.txt
```

`Invoke-Command`**ScriptBlock** 매개 변수를 사용 하 고 `Get-ChildItem` `$args[0]` 및 `$args[1]` 배열 값을 지정 합니다. **Argumentlist** 는 `$args` `Get-ChildItem` **경로** 및 **필터** 에 대 한 매개 변수 위치에 배열 값을 전달 합니다.

### 예제 13: 텍스트 파일에 나열 된 모든 컴퓨터에서 스크립트 실행

이 예제에서는 cmdlet을 사용 하 여 `Invoke-Command` `Sample.ps1` 파일에 나열 된 모든 컴퓨터에서 스크립트를 실행 합니다 `Servers.txt` . 이 명령은 **FilePath** 매개 변수를 사용하여 스크립트 파일을 지정합니다. 이 명령을 사용 하면 원격 컴퓨터에서 스크립트 파일에 액세스할 수 없는 경우에도 원격 컴퓨터에서 스크립트를 실행할 수 있습니다.

```powershell
Invoke-Command -ComputerName (Get-Content Servers.txt) -FilePath C:\Scripts\Sample.ps1 -ArgumentList Process, Service
```

명령을 제출할 때 파일의 내용이 `Sample.ps1` 스크립트 블록으로 복사 되 고 스크립트 블록이 각 원격 컴퓨터에서 실행 됩니다. 이 절차는 **ScriptBlock** 매개 변수를 사용하여 스크립트 내용을 제출하는 작업과 동일합니다.

### 예제 14: URI를 사용 하 여 원격 컴퓨터에서 명령 실행

이 예제에서는 URI (Uniform Resource Identifier)로 식별 되는 원격 컴퓨터에서 명령을 실행 하는 방법을 보여 줍니다. 이 특정 예제에서는 `Set-Mailbox` 원격 Exchange 서버에서 명령을 실행 합니다.

```powershell
$LiveCred = Get-Credential
$parameters = @{
  ConfigurationName = 'Microsoft.Exchange'
  ConnectionUri = 'https://ps.exchangelabs.com/PowerShell'
  Credential = $LiveCred
  Authentication = 'Basic'
  ScriptBlock = {Set-Mailbox Dan -DisplayName "Dan Park"}
}
Invoke-Command @parameters
```

첫 번째 줄에서는 cmdlet을 사용 하 여 `Get-Credential` Windows LIVE ID 자격 증명을 변수에 저장 합니다 `$LiveCred` . PowerShell에서 사용자에 게 Windows Live ID 자격 증명을 입력 하 라는 메시지를 표시 합니다.

`$parameters`변수는 cmdlet에 전달할 매개 변수를 포함 하는 해시 테이블입니다 `Invoke-Command` . `Invoke-Command`Cmdlet은 `Set-Mailbox` **Microsoft. Exchange** 세션 구성을 사용 하 여 명령을 실행 합니다. **ConnectionURI** 매개 변수는 Exchange 서버 끝점의 URL을 지정합니다. **Credential** 매개 변수는 변수에 저장 된 자격 증명을 지정 합니다 `$LiveCred` . **AuthenticationMechanism** 매개 변수는 기본 인증의 사용을 지정합니다. **ScriptBlock** 매개 변수는 명령이 포함된 스크립트 블록을 지정합니다.

### 예 15: session 옵션 사용

이 예에서는 **Sessionoption** 매개 변수를 만들고 사용 하는 방법을 보여 줍니다.

```powershell
$so = New-PSSessionOption -SkipCACheck -SkipCNCheck -SkipRevocationCheck
Invoke-Command -ComputerName server01 -UseSSL -ScriptBlock { Get-HotFix } -SessionOption $so -Credential server01\user01
```

`New-PSSessionOption`Cmdlet은 들어오는 HTTPS 연결을 평가 하는 동안 원격 끝에서 인증 기관, 정식 이름 및 해지 목록을 확인 하지 않도록 하는 세션 옵션 개체를 만듭니다. **Sessionoption** 개체는 변수에 저장 됩니다 `$so` .

> [!NOTE]
> 이러한 검사를 사용 하지 않도록 설정 하는 것은 문제 해결에 편리 하지만 안전 하지 않습니다.

`Invoke-Command`Cmdlet은 `Get-HotFix` 명령을 원격으로 실행 합니다. **Sessionoption** 매개 변수에 변수가 지정 됩니다 `$so` .

### 예 16: 원격 명령의 URI 리디렉션 관리

이 예제에서는 **Allowredirection** **sessionoption** 매개 변수를 사용 하 여 원격 명령에서 URI 리디렉션을 관리 하는 방법을 보여 줍니다.

```powershell
$max = New-PSSessionOption -MaximumRedirection 1
$parameters = @{
  ConnectionUri = "https://ps.exchangelabs.com/PowerShell"
  ScriptBlock = { Get-Mailbox dan }
  AllowRedirection = $true
  SessionOption = $max
}
Invoke-Command @parameters
```

`New-PSSessionOption`Cmdlet은 변수에 저장 된 **Pssessionoption** 개체를 만듭니다 `$max` . 이 명령은 **MaximumRedirection** 매개 변수를 사용하여 **PSSessionOption** 개체의 **MaximumConnectionRedirectionCount** 속성을 1로 설정합니다.

`Invoke-Command`Cmdlet은 `Get-Mailbox` 원격 Microsoft Exchange 서버에서 명령을 실행 합니다. **Allowredirection** 매개 변수는 대체 끝점에 대 한 연결을 리디렉션할 수 있는 명시적 권한을 제공 합니다. **Sessionoption** 매개 변수는 변수에 저장 된 세션 개체를 사용 합니다 `$max` .

결과적으로 **Connectionuri** 로 지정 된 원격 컴퓨터에서 리디렉션 메시지를 반환 하는 경우 PowerShell은 연결을 리디렉션하고, 새 대상이 다른 리디렉션 메시지를 반환 하는 경우 1의 리디렉션 수 값을 초과 하 여 `Invoke-Command` 종료 되지 않는 오류를 반환 합니다.

### 예제 17: 원격 세션에서 네트워크 공유 액세스

이 예제에서는 원격 세션에서 네트워크 공유에 액세스 하는 방법을 보여 줍니다. 예제를 보여 주기 위해 세 대의 컴퓨터가 사용 됩니다. Server01는 로컬 컴퓨터이 고, Server02는 원격 컴퓨터 이며, Net03는 네트워크 공유를 포함 합니다. Server01는 Server02에 연결 하 고, Server02는 Net03에 두 번째 홉을 사용 하 여 네트워크 공유에 액세스 합니다. PowerShell Remoting에서 컴퓨터 간 홉을 지 원하는 방법에 대 한 자세한 내용은 [Powershell 원격에서 두 번째 홉 만들기](/powershell/scripting/learn/remoting/ps-remoting-second-hop)를 참조 하세요.

필요한 CredSSP (자격 증명 보안 지원 공급자) 위임은 로컬 컴퓨터의 클라이언트 설정과 원격 컴퓨터의 서비스 설정에서 사용 하도록 설정 됩니다. 이 예의 명령을 실행 하려면 로컬 컴퓨터와 원격 컴퓨터에서 **Administrators** 그룹의 구성원 이어야 합니다.

```powershell
Enable-WSManCredSSP -Role Client -DelegateComputer Server02
$s = New-PSSession Server02
Invoke-Command -Session $s -ScriptBlock {Enable-WSManCredSSP -Role Server -Force}
$parameters = @{
  Session = $s
  ScriptBlock = { Get-Item \\Net03\Scripts\LogFiles.ps1 }
  Authentication = "CredSSP"
  Credential = "Domain01\Admin01"
}
Invoke-Command @parameters
```

`Enable-WSManCredSSP`Cmdlet은 Server01 로컬 컴퓨터에서 Server02 원격 컴퓨터로 CredSSP 위임을 사용 하도록 설정 합니다. **Role** 매개 변수는 **클라이언트** 를 지정 하 여 로컬 컴퓨터에서 CredSSP 클라이언트 설정을 구성 합니다.

`New-PSSession` Server02에 대 한 **PSSession** 개체를 만들고 해당 개체를 `$s` 변수에 저장 합니다.

`Invoke-Command`이 cmdlet은 변수를 사용 하 여 `$s` 원격 컴퓨터 Server02에 연결 합니다. **ScriptBlock** 매개 변수는 `Enable-WSManCredSSP` 원격 컴퓨터에서 실행 됩니다. **Role** 매개 변수는 원격 컴퓨터에서 CredSSP 서버 설정을 구성 하는 **서버** 를 지정 합니다.

`$parameters`변수는 네트워크 공유에 연결 하기 위한 매개 변수 값을 포함 합니다. `Invoke-Command`Cmdlet은 `Get-Item` 의 세션에서 명령을 실행 합니다 `$s` . 이 명령은 네트워크 공유에서 스크립트를 가져옵니다 `\\Net03\Scripts` . 이 명령은 **CredSSP** 값을 가진 **Authentication** 매개 변수 및 값이 **Domain01\Admin01** 인 **Credential** 매개 변수를 사용 합니다.

### 예 18: 여러 원격 컴퓨터에서 스크립트 시작

이 예제에서는 100 대 이상의 컴퓨터에서 스크립트를 실행 합니다. 로컬 컴퓨터에 대한 영향을 최소화하려면 각 컴퓨터에 연결하고 스크립트를 시작한 다음 각 컴퓨터에서 연결을 끊습니다.
이 스크립트는 연결이 끊어진 세션에서 계속 실행됩니다.

```powershell
$parameters = @{
  ComputerName = (Get-Content -Path C:\Test\Servers.txt)
  InDisconnectedSession = $true
  FilePath = "\\Scripts\Public\ConfigInventory.ps1"
  SessionOption = @{OutputBufferingMode="Drop";IdleTimeout=43200000}
}
Invoke-Command @parameters
```

명령을 사용 하 여 `Invoke-Command` 스크립트를 실행 합니다. **ComputerName** 매개 변수 값은 `Get-Content` 텍스트 파일에서 원격 컴퓨터의 이름을 가져오는 명령입니다. **InDisconnectedSession** 매개 변수는 명령을 시작하는 즉시 세션의 연결을 끊습니다. **FilePath** 매개 변수 값은 `Invoke-Command` 각 컴퓨터에서 실행 되는 스크립트입니다.

**Sessionoption** 값은 해시 테이블입니다. **OutputBufferingMode** 값은 **Drop** 으로 설정 되 고 **IdleTimeout** 값은 **4320만** 밀리초 (12 시간)로 설정 됩니다.

연결 되지 않은 세션에서 실행 되는 명령 및 스크립트의 결과를 얻으려면 cmdlet을 사용 합니다 `Receive-PSSession` .

### 예 19: SSH를 사용 하 여 원격 컴퓨터에서 명령 실행

이 예제에서는 Secure Shell (SSH)를 사용 하 여 원격 컴퓨터에서 명령을 실행 하는 방법을 보여 줍니다. SSH가 원격 컴퓨터에서 암호를 묻는 메시지를 표시 하도록 구성 된 경우 암호를 입력 하 라는 메시지가 표시 됩니다.
그렇지 않으면 SSH 키 기반 사용자 인증을 사용 해야 합니다.

```powershell
Invoke-Command -HostName UserA@LinuxServer01 -ScriptBlock { Get-MailBox * }
```

### 예제 20: SSH를 사용 하 여 원격 컴퓨터에서 명령을 실행 하 고 사용자 인증 키 지정

이 예제에서는 SSH를 사용 하 여 원격 컴퓨터에서 명령을 실행 하 고 사용자 인증을 위한 키 파일을 지정 하는 방법을 보여 줍니다. 키 인증에 실패 하 고 기본 암호 인증을 허용 하도록 원격 컴퓨터를 구성한 경우를 제외 하 고는 암호를 입력 하 라는 메시지가 표시 되지 않습니다.

```powershell
Invoke-Command -HostName UserA@LinuxServer01 -ScriptBlock { Get-MailBox * } -KeyFilePath /UserA/UserAKey_rsa
```

### 예제 21: SSH를 작업으로 사용 하 여 여러 원격 컴퓨터에서 스크립트 파일 실행

이 예제에서는 SSH 및 **SSHConnection** 매개 변수 집합을 사용 하 여 여러 원격 컴퓨터에서 스크립트 파일을 실행 하는 방법을 보여 줍니다. **SSHConnection** 매개 변수는 각 컴퓨터에 대 한 연결 정보를 포함 하는 해시 테이블의 배열을 사용 합니다. 이 예에서는 대상 원격 컴퓨터가 키 기반 사용자 인증을 지원 하도록 구성 된 SSH를 사용 해야 합니다.

```powershell
$sshConnections =
@{ HostName="WinServer1"; UserName="Domain\UserA"; KeyFilePath="C:\Users\UserA\id_rsa" },
@{ HostName="UserB@LinuxServer5"; KeyFilePath="/Users/UserB/id_rsa" }
$results = Invoke-Command -FilePath c:\Scripts\CollectEvents.ps1 -SSHConnection $sshConnections
```

## PARAMETERS

### -AllowRedirection

이 연결을 대체 URI(Uniform Resource Identifier)로 리디렉션할 수 있도록 허용합니다.

**ConnectionURI** 매개 변수를 사용하면 원격 대상에서 다른 URI로 리디렉션하는 명령을 반환할 수 있습니다. 기본적으로 PowerShell은 연결을 리디렉션하지 않지만이 매개 변수를 사용 하 여 연결을 리디렉션할 수 있습니다.

또한 **MaximumConnectionRedirectionCount** 세션 옵션 값을 변경하여 연결이 리디렉션되는 횟수를 제한할 수도 있습니다. Cmdlet의 **Maximumredirection** 매개 변수를 사용 `New-PSSessionOption` 하거나 기본 설정 변수의 **MaximumConnectionRedirectionCount** 속성을 설정 `$PSSessionOption` 합니다. 기본값은 5입니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Uri, FilePathUri
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -ApplicationName

연결 URI의 애플리케이션 이름 세그먼트를 지정합니다. 명령에 **Connectionuri** 매개 변수를 사용 하지 않는 경우이 매개 변수를 사용 하 여 응용 프로그램 이름을 지정 합니다.

기본값은 `$PSSessionApplicationName` 로컬 컴퓨터의 기본 설정 변수 값입니다. 이 기본 설정 변수가 정의 되지 않은 경우 기본값은 WSMAN입니다. 이 값은 대부분의 사용에 적합합니다. 자세한 내용은 [about_Preference_Variables](./About/about_Preference_Variables.md)를 참조 하세요.

WinRM 서비스는 애플리케이션 이름을 사용하여 연결 요청을 제공하는 수신기를 선택합니다.
이 매개 변수 값은 원격 컴퓨터에 있는 수신기의 **URLPrefix** 속성 값과 일치해야 합니다.

```yaml
Type: System.String
Parameter Sets: ComputerName, FilePathComputerName
Aliases:

Required: False
Position: Named
Default value: $PSSessionApplicationName if set on the local computer, otherwise WSMAN
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ArgumentList

명령에 있는 로컬 변수의 값을 제공합니다. 명령에 있는 변수는 원격 컴퓨터에서 명령이 실행되기 전에 이 값으로 교체됩니다. 쉼표로 구분된 목록으로 값을 입력합니다. 값은 나열 된 순서 대로 변수와 연결 됩니다. **Argumentlist** 의 별칭은 Args입니다.

**Argumentlist** 매개 변수의 값은 1024 같은 실제 값 이거나와 같은 지역 변수에 대 한 참조일 수 있습니다 `$max` .

명령에서 로컬 변수를 사용하려면 다음 명령 형식을 사용합니다.

`{param($<name1>[, $<name2>]...) <command-with-local-variables>} -ArgumentList <value>` 또는 `<local-variable>`

**Param** 키워드는 명령에 사용 되는 지역 변수를 나열 합니다. **Argumentlist** 는 나열 된 순서 대로 변수의 값을 제공 합니다. **Argumentlist** 의 동작에 대 한 자세한 내용은 [about_Splatting](about/about_Splatting.md#splatting-with-arrays)를 참조 하세요.

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AsJob

이 cmdlet이 명령을 원격 컴퓨터에서 백그라운드 작업으로 실행 함을 나타냅니다. 이 매개 변수를 사용 하 여 완료 하는 데 오랜 시간이 걸리는 명령을 실행할 수 있습니다.

**AsJob** 매개 변수를 사용 하는 경우이 명령은 작업을 나타내는 개체를 반환한 다음 명령 프롬프트를 표시 합니다. 작업을 마치는 동안 세션에서 작업을 계속할 수 있습니다. 작업을 관리 하려면 cmdlet을 사용 `*-Job` 합니다. 작업 결과를 가져오려면 cmdlet을 사용 합니다 `Receive-Job` .

**AsJob** 매개 변수는 cmdlet을 사용 하 여 `Invoke-Command` cmdlet을 원격으로 실행 하는 것과 비슷합니다 `Start-Job` . 그러나 **AsJob** 을 사용 하면 작업이 원격 컴퓨터에서 실행 되는 경우에도 로컬 컴퓨터에 작업이 생성 됩니다. 원격 작업의 결과는 로컬 컴퓨터에 자동으로 반환 됩니다.

PowerShell 백그라운드 작업에 대 한 자세한 내용은 [about_Jobs](About/about_Jobs.md) 및 [about_Remote_Jobs](About/about_Remote_Jobs.md)를 참조 하세요.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: FilePathRunspace, Session, ComputerName, FilePathComputerName, Uri, FilePathUri, VMId, VMName, FilePathVMId, FilePathVMName, SSHHost, ContainerId, FilePathContainerId, SSHHostHashParam, FilePathSSHHost, FilePathSSHHostHash
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -인증

사용자의 자격 증명을 인증 하는 데 사용 되는 메커니즘을 지정 합니다. CredSSP 인증은 windows Vista, Windows Server 2008 이상 버전의 Windows 운영 체제 에서만 사용할 수 있습니다.

이 매개 변수에 허용 되는 값은 다음과 같습니다.

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
> 사용자의 자격 증명이 인증을 위해 원격 컴퓨터로 전달되는 CredSSP(자격 증명 보안 지원 공급자) 인증은 둘 이상의 리소스에서 인증이 필요한 명령(예: 원격 네트워크 공유 액세스)에 사용됩니다. 이렇게 하면 원격 작업의 보안 위험이 커집니다. 원격 컴퓨터가 손상된 경우 이 컴퓨터로 전달된 자격 증명을 사용하여 네트워크 세션을 제어할 수 있습니다. 자세한 내용은 [자격 증명 보안 지원 공급자](/windows/win32/secauthn/credential-security-support-provider)를 참조 하세요.

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ComputerName, FilePathComputerName, Uri, FilePathUri
Aliases:
Accepted values: Basic, Default, Credssp, Digest, Kerberos, Negotiate, NegotiateWithImplicitCredential

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### -CertificateThumbprint

연결이 끊긴 세션에 연결할 권한이 있는 사용자 계정의 디지털 공개 키 인증서(X509)를 지정합니다. 인증서의 인증서 지문을 입력합니다.

인증서는 클라이언트 인증서 기반 인증에 사용됩니다. 로컬 사용자 계정에만 매핑할 수 있으며 도메인 계정에는 사용할 수 없습니다.

인증서 지문을 가져오려면 `Get-Item` `Get-ChildItem` PowerShell Cert: 드라이브에서 또는 명령을 사용 합니다.

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

명령이 실행되는 컴퓨터를 지정합니다. 기본값은 로컬 컴퓨터입니다.

**ComputerName** 매개 변수를 사용 하는 경우 PowerShell은 지정 된 명령을 실행 하는 데만 사용 되 고 닫힌 임시 연결을 만듭니다. 영구 연결이 필요 하면 **Session** 매개 변수를 사용 합니다.

하나 이상 컴퓨터의 NetBIOS 이름, IP 주소 또는 정규화된 도메인 이름을 쉼표로 구분된 목록으로 입력합니다. 로컬 컴퓨터를 지정 하려면 컴퓨터 이름, localhost 또는 점 ()을 입력 `.` 합니다.

**ComputerName** 값에 IP 주소를 사용 하려면 명령에 **Credential** 매개 변수를 포함 해야 합니다. 컴퓨터를 HTTPS 전송에 대해 구성 하거나 원격 컴퓨터의 IP 주소를 로컬 컴퓨터의 WinRM **TrustedHosts** 목록에 포함 해야 합니다. **TrustedHosts** 목록에 컴퓨터 이름을 추가 하는 방법에 대 한 지침은 [신뢰할 수 있는 호스트 목록에 컴퓨터를 추가 하는 방법](./about/about_remote_troubleshooting.md#how-to-add-a-computer-to-the-trusted-hosts-list)을 참조 하세요.

Windows Vista 이상 버전의 Windows 운영 체제에서 로컬 컴퓨터를 **ComputerName** 값에 포함 하려면 **관리자 권한으로 실행** 옵션을 사용 하 여 PowerShell을 실행 해야 합니다.

```yaml
Type: System.String[]
Parameter Sets: ComputerName, FilePathComputerName
Aliases: Cn

Required: False
Position: 0
Default value: Local computer
Accept pipeline input: False
Accept wildcard characters: False
```

### -ConfigurationName

새 **PSSession** 에 사용 되는 세션 구성을 지정 합니다.

세션 구성의 구성 이름 또는 정규화된 리소스 URI를 입력합니다. 구성 이름만 지정 하는 경우에는 다음 스키마 URI가 앞에와 야 `http://schemas.microsoft.com/PowerShell` 합니다.

SSH와 함께 사용 하는 경우이 매개 변수는에 정의 된 대로 대상에서 사용할 하위 시스템을 지정 합니다 `sshd_config` . SSH의 기본값은 `powershell` 하위 시스템입니다.

세션의 세션 구성은 원격 컴퓨터에 있습니다. 지정 된 세션 구성이 원격 컴퓨터에 없으면 명령이 실패 합니다.

기본값은 `$PSSessionConfigurationName` 로컬 컴퓨터의 기본 설정 변수 값입니다. 이 기본 설정 변수가 설정 되지 않은 경우 기본값은 **Microsoft. PowerShell** 입니다. 자세한 내용은 [about_Preference_Variables](about/about_Preference_Variables.md)를 참조 하세요.

```yaml
Type: System.String
Parameter Sets: ComputerName, FilePathComputerName, Uri, FilePathUri, VMId, VMName, FilePathVMId, FilePathVMName, ContainerId, FilePathContainerId
Aliases:

Required: False
Position: Named
Default value: $PSSessionConfigurationName if set on the local computer, otherwise Microsoft.PowerShell
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ConnectionUri

세션에 대한 연결 엔드포인트를 정의하는 URI(Uniform Resource Identifier)를 지정합니다.
URI는 정규화된 URI여야 합니다.

이 문자열의 형식은 다음과 같습니다.

`<Transport>://<ComputerName>:<Port>/<ApplicationName>`

기본값은 다음과 같습니다.

`http://localhost:5985/WSMAN`

연결 URI를 지정 하지 않으면 **UseSSL** 및 **Port** 매개 변수를 사용 하 여 연결 uri 값을 지정할 수 있습니다.

URI의 **Transport** 세그먼트에 유효한 값은 HTTP 및 HTTPS입니다. 전송 세그먼트를 사용 하 여 연결 URI를 지정 하 고 포트를 지정 하지 않으면 세션은 표준 포트 80 (HTTP의 경우, HTTPS의 경우 443)를 사용 하 여 만들어집니다. PowerShell 원격을 위한 기본 포트를 사용 하려면 HTTP의 경우 포트 5985을, HTTPS의 경우 5986을 지정 합니다.

대상 컴퓨터에서 연결을 다른 URI로 리디렉션하는 경우 명령에서 **allowredirection** 매개 변수를 사용 하지 않으면 PowerShell에서 리디렉션을 방지 합니다.

```yaml
Type: System.Uri[]
Parameter Sets: Uri, FilePathUri
Aliases: URI, CU

Required: False
Position: 0
Default value: http://localhost:5985/WSMAN
Accept pipeline input: False
Accept wildcard characters: False
```

### -ContainerId

컨테이너 Id의 배열을 지정 합니다.

```yaml
Type: System.String[]
Parameter Sets: ContainerId, FilePathContainerId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
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
Parameter Sets: ComputerName, FilePathComputerName, Uri, FilePathUri, VMId, VMName, FilePathVMId, FilePathVMName
Aliases:

Required: True (VMId, VMName, FilePathVMId, FilePathVMName), False (ComputerName, FilePathComputerName, Uri, FilePathUri)
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -EnableNetworkAccess

이 cmdlet이 루프백 세션에 대화형 보안 토큰을 추가 함을 나타냅니다. 대화형 토큰을 사용하면 다른 컴퓨터에서 데이터를 가져오는 명령을 루프백 세션에서 실행할 수 있습니다. 예를 들어 원격 컴퓨터에서 로컬 컴퓨터로 XML 파일을 복사하는 세션에서 명령을 실행할 수 있습니다.

루프백 세션은 동일한 컴퓨터에서 시작 하 여 종료 되는 **PSSession** 입니다. 루프백 세션을 만들려면 **ComputerName** 매개 변수를 생략 하거나 해당 값을 점 ( `.` ), localhost 또는 로컬 컴퓨터 이름으로 설정 합니다.

기본적으로 루프백 세션은 원격 컴퓨터를 인증 하는 데 충분 한 권한을 제공 하지 않을 수 있는 네트워크 토큰을 사용 하 여 생성 됩니다.

**EnableNetworkAccess** 매개 변수는 루프백 세션에서만 유효합니다. 원격 컴퓨터에서 세션을 만들 때 **EnableNetworkAccess** 를 사용 하는 경우 명령은 성공 하지만 매개 변수는 무시 됩니다.

세션 자격 증명을 다른 컴퓨터에 위임 하는 **인증** 매개 변수의 **CredSSP** 값을 사용 하 여 루프백 세션에서 원격 액세스를 허용할 수 있습니다.

악의적인 액세스 로부터 컴퓨터를 보호 하기 위해 **EnableNetworkAccess** 를 사용 하 여 만든 대화형 토큰을 포함 하는 분리 된 루프백 세션은 세션을 만든 컴퓨터 에서만 다시 연결할 수 있습니다. CredSSP 인증을 사용하는 연결이 끊어진 세션은 다른 컴퓨터에서 다시 연결할 수 있습니다. 자세한 내용은 `Disconnect-PSSession`를 참조하세요.

이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName, FilePathComputerName, Uri, FilePathUri
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilePath

하나 이상의 원격 컴퓨터에서이 cmdlet이 실행 되는 로컬 스크립트를 지정 합니다. 스크립트의 경로와 파일 이름을 입력 하거나에 대 한 스크립트 경로를 파이프 `Invoke-Command` 합니다. 스크립트는 로컬 컴퓨터 또는 로컬 컴퓨터에서 액세스할 수 있는 디렉터리에 있어야 합니다. **Argumentlist** 를 사용 하 여 스크립트의 매개 변수 값을 지정 합니다.

이 매개 변수를 사용 하는 경우 PowerShell은 지정 된 스크립트 파일의 내용을 스크립트 블록으로 변환 하 고 스크립트 블록을 원격 컴퓨터로 전송한 다음 원격 컴퓨터에서 실행 합니다.

```yaml
Type: System.String
Parameter Sets: FilePathRunspace, FilePathComputerName, FilePathUri, FilePathVMId, FilePathVMName, FilePathContainerId, FilePathSSHHost, FilePathSSHHostHash
Aliases: PSPath

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -HideComputerName

이 cmdlet이 출력 표시에서 각 개체의 컴퓨터 이름을 생략 함을 나타냅니다. 기본적으로 개체를 생성한 컴퓨터의 이름은 화면에 표시됩니다.

이 매개 변수는 출력 표시에만 영향을 줍니다. 개체를 변경 하지 않습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: FilePathRunspace, Session, ComputerName, FilePathComputerName, Uri, FilePathUri, VMId, VMName, FilePathVMId, FilePathVMName, SSHHost, ContainerId, FilePathContainerId, SSHHostHashParam, FilePathSSHHost, FilePathSSHHostHash
Aliases: HCN

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -HostName

Secure Shell (SSH) 기반 연결에 대 한 컴퓨터 이름 배열을 지정 합니다. 이는 원격 컴퓨터에 대 한 연결이 Windows WinRM이 아닌 SSH를 사용 하는 경우를 제외 하 고 **ComputerName** 매개 변수와 비슷합니다.

이 매개 변수는 PowerShell 6.0에서 도입 되었습니다.

```yaml
Type: System.String[]
Parameter Sets: SSHHost, FilePathSSHHost
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InDisconnectedSession

이 cmdlet이 연결 되지 않은 세션에서 명령 또는 스크립트를 실행 함을 나타냅니다.

**InDisconnectedSession** 매개 변수를 사용 하는 경우는 `Invoke-Command` 각 원격 컴퓨터에 영구 세션을 만들고, **ScriptBlock** 또는 **FilePath** 매개 변수로 지정 된 명령을 시작한 다음 세션에서 연결을 끊습니다. 명령은 연결 되지 않은 세션에서 계속 실행 됩니다. **InDisconnectedSession** 를 사용 하면 원격 세션에 대 한 연결을 유지 하지 않고 명령을 실행할 수 있습니다. 결과를 반환 하기 전에 세션의 연결이 끊어져서 **InDisconnectedSession** 는 세션 간에 분할 되지 않고 다시 연결 된 세션에 모든 명령 결과가 반환 되도록 합니다.

**InDisconnectedSession** 은 **Session** 매개 변수 또는 **AsJob** 매개 변수와 함께 사용할 수 없습니다.

**InDisconnectedSession** 를 사용 하는 명령은 연결 되지 않은 세션을 나타내는 **PSSession** 개체를 반환 합니다. 명령 출력을 반환 하지 않습니다. 연결이 끊어진 세션에 연결 하려면 `Connect-PSSession` 또는 cmdlet을 사용 `Receive-PSSession` 합니다. 세션에서 실행 된 명령의 결과를 가져오려면 cmdlet을 사용 합니다 `Receive-PSSession` . 연결 되지 않은 세션에서 출력을 생성 하는 명령을 실행 하려면 **OutputBufferingMode** 세션 옵션의 값을 **Drop** 으로 설정 합니다. 연결이 끊어진 세션에 연결 하려면 세션을 삭제 하기 전에 연결 하는 데 충분 한 시간을 제공 하도록 세션의 유휴 제한 시간을 설정 합니다.

**Sessionoption** 매개 변수 또는 기본 설정 변수에서 출력 버퍼링 모드 및 유휴 제한 시간을 설정할 수 있습니다 `$PSSessionOption` . 세션 옵션에 대 한 자세한 내용은 `New-PSSessionOption` 및 [about_Preference_Variables](./about/about_preference_variables.md)을 참조 하세요.

연결이 끊긴 세션 기능에 대한 자세한 내용은 [about_Remote_Disconnected_Sessions](about/about_Remote_Disconnected_Sessions.md)를 참조하세요.

이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName, FilePathComputerName, Uri, FilePathUri
Aliases: Disconnected

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

명령에 대한 입력을 지정합니다. 개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요.

**InputObject** 매개 변수를 사용 하는 경우 `$Input` **ScriptBlock** 매개 변수 값의 자동 변수를 사용 하 여 입력 개체를 나타냅니다.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -JobName

백그라운드 작업의 이름을 지정합니다. 기본적으로 작업의 이름은 이며 `Job<n>` , 여기서 `<n>` 는 서 수입니다.

명령에서 **JobName** 매개 변수를 사용 하는 경우 명령 `Invoke-Command` 에 **AsJob** 를 포함 하지 않는 경우에도 명령이 작업으로 실행 되 고 작업 개체를 반환 합니다.

PowerShell 백그라운드 작업에 대 한 자세한 내용은 [about_Jobs](./About/about_Jobs.md)를 참조 하세요.

```yaml
Type: System.String
Parameter Sets: FilePathRunspace, Session, ComputerName, FilePathComputerName, Uri, FilePathUri, SSHHost, ContainerId, FilePathContainerId, SSHHostHashParam
Aliases:

Required: False
Position: Named
Default value: Job<n>
Accept pipeline input: False
Accept wildcard characters: False
```

### -KeyFilePath

SSH (Secure Shell)에서 원격 컴퓨터의 사용자를 인증 하는 데 사용 하는 키 파일 경로를 지정 합니다.

SSH를 사용 하면 기본 암호 인증 대신 개인 및 공개 키를 통해 사용자 인증을 수행할 수 있습니다. 키 인증을 사용 하도록 원격 컴퓨터를 구성 하는 경우이 매개 변수를 사용 하 여 사용자를 식별 하는 키를 제공할 수 있습니다.

이 매개 변수는 PowerShell 6.0에서 도입 되었습니다.

```yaml
Type: System.String
Parameter Sets: SSHHost, FilePathSSHHost
Aliases: IdentityFilePath

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NoNewScope

이 cmdlet이 현재 범위의 지정 된 명령을 실행 함을 나타냅니다. 기본적으로는 `Invoke-Command` 자체 범위에서 명령을 실행 합니다.

이 매개 변수는 현재 세션에서 실행하는 명령 즉, **ComputerName** 및 **Session** 매개 변수를 모두 생략하는 명령에서만 유효합니다.

이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: InProcess
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Port

이 명령에 사용 되는 원격 컴퓨터의 네트워크 포트를 지정 합니다. 원격 컴퓨터에 연결하려면 원격 컴퓨터가 연결에서 사용하는 포트에서 수신 대기하고 있어야 합니다. 기본 포트는 5985 (HTTP의 경우 WinRM 포트) 및 5986 (HTTPS의 경우 WinRM 포트)입니다.

대체 포트를 사용하기 전에 원격 컴퓨터가 해당 포트에서 수신하도록 원격 컴퓨터의 WinRM 수신기를 구성해야 합니다. 수신기를 구성 하려면 PowerShell 프롬프트에 다음 두 명령을 입력 합니다.

`Remove-Item -Path WSMan:\Localhost\listener\listener* -Recurse`

`New-Item -Path WSMan:\Localhost\listener -Transport http -Address * -Port \<port-number\>`

반드시 필요한 경우가 아니면 **Port** 매개 변수를 사용 하지 마세요. 이 명령에 설정된 포트는 명령이 실행되는 모든 컴퓨터나 세션에 적용됩니다. 대체 포트 설정을 사용하면 일부 컴퓨터에서 명령이 실행되지 않을 수 있습니다.

```yaml
Type: System.Int32
Parameter Sets: ComputerName, FilePathComputerName, SSHHost
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RemoteDebug

호출 된 명령을 원격 PowerShell 세션의 디버그 모드에서 실행 하는 데 사용 됩니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: FilePathRunspace, Session, ComputerName, FilePathComputerName, Uri, FilePathUri, VMId, VMName, FilePathVMId, FilePathVMName, SSHHost, ContainerId, FilePathContainerId, SSHHostHashParam, FilePathSSHHost, FilePathSSHHostHash
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -RunAsAdministrator

이 cmdlet이 명령을 관리자 권한으로 호출 함을 나타냅니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ContainerId, FilePathContainerId
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -ScriptBlock

실행할 명령을 지정합니다. 명령을 중괄호로 묶어 `{ }` 스크립트 블록을 만듭니다.
이 매개 변수는 필수입니다.

기본적으로 명령에 있는 모든 변수는 원격 컴퓨터에서 평가됩니다. 명령에 로컬 변수를 포함 하려면 **Argumentlist** 를 사용 합니다.

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: InProcess, Session, ComputerName, Uri, VMId, VMName, SSHHost, ContainerId, SSHHostHashParam
Aliases: Command

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Session

이 cmdlet이 명령을 실행 하는 세션의 배열을 지정 합니다. **Pssession** 개체를 포함 하는 변수를 입력 하거나 **pssession** 개체를 만들거나 가져오는 명령 (예: 또는 명령)을 입력 합니다 `New-PSSession` `Get-PSSession` .

**PSSession** 을 만들 때 PowerShell은 원격 컴퓨터에 대 한 영구 연결을 설정 합니다. **PSSession** 을 사용 하 여 데이터를 공유 하는 일련의 관련 명령을 실행 합니다. 단일 명령이 나 일련의 관련 되지 않은 명령을 실행 하려면 **ComputerName** 매개 변수를 사용 합니다. 자세한 내용은 [about_PSSessions](./About/about_PSSessions.md)를 참조 하세요.

```yaml
Type: System.Management.Automation.Runspaces.PSSession[]
Parameter Sets: FilePathRunspace, Session
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -세션 이름

연결이 끊긴 세션의 표시 이름을 지정합니다. 이 이름을 사용 하 여 명령 등의 후속 명령에서 세션을 참조할 수 있습니다 `Get-PSSession` . 이 매개 변수는 **InDisconnectedSession** 매개 변수와 함께 사용할 경우에만 유효합니다.

이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.String[]
Parameter Sets: ComputerName, FilePathComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SessionOption

세션에 대 한 고급 옵션을 지정 합니다. Cmdlet을 사용 하 여 만든 것과 같은 **sessionoption** 개체를 입력 `New-PSSessionOption` 하거나 키가 세션 옵션 이름이 고 값이 session 옵션 값인 해시 테이블을 입력 합니다.

옵션의 기본값은 설정 된 경우 기본 설정 변수의 값에 따라 결정 됩니다 `$PSSessionOption` . 그러지 않으면 기본값은 세션 구성에 설정된 옵션에 따라 설정됩니다.

세션 옵션 값은 기본 설정 변수 및 세션 구성에 설정 된 세션의 기본값 보다 우선 적용 `$PSSessionOption` 됩니다. 그러나 세션 구성에 설정 된 최대값, 할당량 또는 제한 보다 우선 적용 되지 않습니다.

기본값을 포함 하는 세션 옵션에 대 한 설명은를 참조 하십시오 `New-PSSessionOption` . 기본 설정 변수에 대 한 자세한 내용은 `$PSSessionOption` [about_Preference_Variables](About/about_Preference_Variables.md)를 참조 하세요.
세션 구성에 대 한 자세한 내용은 [about_Session_Configurations](About/about_Session_Configurations.md)를 참조 하세요.

```yaml
Type: System.Management.Automation.Remoting.PSSessionOption
Parameter Sets: ComputerName, FilePathComputerName, Uri, FilePathUri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SSHConnection

이 매개 변수는 해시 테이블의 배열을 사용 합니다. 여기서 각 해시 테이블에는 SSH (Secure Shell) 연결을 설정 하는 데 필요한 하나 이상의 연결 매개 변수가 포함 되어 있습니다. **SSHConnection** 매개 변수는 각 세션에 다른 연결 정보가 필요한 여러 세션을 만드는 데 유용 합니다.

해시 테이블에는 다음과 같은 멤버가 있습니다.

- **ComputerName** (또는 **HostName**)
- **포트**
- **UserName**
- **Keyfilepath** (또는 **IdentityFilePath**)

**ComputerName** (또는 **HostName**)은 필요한 유일한 키-값 쌍입니다.

이 매개 변수는 PowerShell 6.0에서 도입 되었습니다.

```yaml
Type: System.Collections.Hashtable[]
Parameter Sets: SSHHostHashParam, FilePathSSHHostHash
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SSHTransport

SSH (Secure Shell)를 사용 하 여 원격 연결을 설정 했음을 나타냅니다.

기본적으로 PowerShell은 Windows WinRM을 사용 하 여 원격 컴퓨터에 연결 합니다. 이 스위치를 사용 하면 PowerShell에서 **호스트 이름** 매개 변수를 사용 하 여 SSH 기반 원격 연결을 설정 합니다.

이 매개 변수는 PowerShell 6.0에서 도입 되었습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: SSHHost, FilePathSSHHost
Aliases:
Accepted values: true

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit

이 명령을 실행하도록 설정할 수 있는 최대 동시 연결 수를 지정합니다.
이 매개 변수를 생략하거나 값 0을 입력하면 기본값 32가 사용됩니다.

제한 한도는 현재 명령에만 적용되며 세션이나 컴퓨터에는 적용되지 않습니다.

```yaml
Type: System.Int32
Parameter Sets: FilePathRunspace, Session, ComputerName, FilePathComputerName, Uri, FilePathUri, VMId, VMName, FilePathVMId, FilePathVMName, ContainerId, FilePathContainerId
Aliases:

Required: False
Position: Named
Default value: 32
Accept pipeline input: False
Accept wildcard characters: False
```

### -UserName

원격 컴퓨터에서 명령을 실행 하는 데 사용 되는 계정의 사용자 이름을 지정 합니다. 사용자 인증 방법은 원격 컴퓨터에서 SSH (Secure Shell)가 구성 된 방식에 따라 달라 집니다.

SSH가 기본 암호 인증으로 구성 된 경우 사용자 암호를 입력 하 라는 메시지가 표시 됩니다.

키 기반 사용자 인증에 대해 SSH를 구성 하는 경우 키 파일 경로는 **Keyfilepath** 매개 변수를 통해 제공할 수 있으며 암호 프롬프트는 발생 하지 않습니다. 클라이언트 사용자 키 파일이 SSH의 알려진 위치에 있는 경우 키 기반 인증에는 **Keyfilepath** 매개 변수가 필요 하지 않으며 사용자 인증은 사용자 이름에 따라 자동으로 수행 됩니다. 자세한 내용은 키 기반 사용자 인증에 대 한 플랫폼의 SSH 설명서를 참조 하세요.

이 매개 변수는 필수 매개 변수가 아닙니다. **UserName** 매개 변수를 지정 하지 않으면 현재 로그온 한 사용자 이름이 연결에 사용 됩니다.

이 매개 변수는 PowerShell 6.0에서 도입 되었습니다.

```yaml
Type: System.String
Parameter Sets: SSHHost, FilePathSSHHost
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseSSL

이 cmdlet이 SSL(Secure Sockets Layer) (SSL) 프로토콜을 사용 하 여 원격 컴퓨터에 대 한 연결을 설정 함을 나타냅니다. 기본적으로 SSL은 사용 되지 않습니다.

WS-Management는 네트워크를 통해 전송 되는 모든 PowerShell 콘텐츠를 암호화 합니다. **UseSSL** 매개 변수는 HTTP 대신 HTTPS를 통해 데이터를 전송 하는 추가 보호 기능입니다.

이 매개 변수를 사용 하지만 명령에 사용 되는 포트에서 SSL을 사용할 수 없는 경우 명령이 실패 합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName, FilePathComputerName
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -VMId

가상 컴퓨터의 Id 배열을 지정 합니다.

```yaml
Type: System.Guid[]
Parameter Sets: VMId, FilePathVMId
Aliases: VMGuid

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -VMName

가상 컴퓨터의 이름 배열을 지정합니다.

```yaml
Type: System.String[]
Parameter Sets: VMName, FilePathVMName
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

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.object.

스크립트 블록의 명령을로 파이프 할 수 있습니다 `Invoke-Command` . `$Input`자동 변수를 사용 하 여 명령에서 입력 개체를 나타냅니다.

## 출력

### Runspace (호출 된 명령의 출력 또는 호출 된 명령의 출력)를 실행 해야 합니다.

**AsJob** 매개 변수를 사용 하는 경우이 cmdlet은 작업 개체를 반환 합니다. **InDisconnectedSession** 매개 변수를 지정 하면는 `Invoke-Command` **PSSession** 개체를 반환 합니다. 그렇지 않으면 호출 된 명령의 출력을 반환 합니다 .이는 **ScriptBlock** 매개 변수의 값입니다.

## 참고

Windows Vista 이상 버전의 Windows 운영 체제에서 **ComputerName** 매개 변수를 사용 하 여 `Invoke-Command` 로컬 컴퓨터에서 명령을 실행 하려면 **관리자 권한으로 실행** 옵션을 사용 하 여 PowerShell을 실행 해야 합니다.

여러 컴퓨터에서 명령을 실행 하는 경우 PowerShell은 목록에 나타나는 순서 대로 컴퓨터에 연결 합니다. 그러나 명령 출력은 원격 컴퓨터에서 수신 된 순서 대로 표시 됩니다 .이는 다를 수 있습니다.

실행 되는 명령으로 인해 발생 하는 오류는 `Invoke-Command` 명령 결과에 포함 됩니다.
로컬 명령에서 종료 오류인 오류는 원격 명령에서 종료되지 않는 오류로 취급됩니다. 이 전략은 한 컴퓨터에서 종료 오류가 실행 되는 모든 컴퓨터에서 해당 명령을 닫지 않도록 합니다. 이 방법은 원격 명령이 한 컴퓨터에서 실행되는 경우에도 사용됩니다.

원격 컴퓨터가 로컬 컴퓨터가 신뢰 하는 도메인에 없는 경우 컴퓨터에서 사용자 자격 증명을 인증 하지 못할 수 있습니다. WS-MANAGEMENT에서 신뢰할 수 있는 호스트 목록에 원격 컴퓨터를 추가 하려면 공급자에서 다음 명령을 사용 합니다 `WSMAN` `<Remote-Computer-Name>` . 여기서은 원격 컴퓨터의 이름입니다.

`Set-Item -Path WSMan:\Localhost\Client\TrustedHosts -Value \<Remote-Computer-Name\>`

**InDisconnectedSession** 매개 변수를 사용 하 여 **PSSession** 의 연결을 끊으면 세션 상태가 **Disconnected** 이 고 availability가 **None** 입니다. **State** 속성 값은 현재 세션을 기준으로 합니다. **연결 끊김** 값은 **PSSession** 이 현재 세션에 연결 되지 않았음을 의미 합니다. 그러나 모든 세션에서 **PSSession** 의 연결이 끊어졌음을 의미 하는 것은 아닙니다. 다른 세션에 연결되어 있을 수도 있습니다. 세션에 연결하거나 다시 연결할 수 있는지 확인하려면 **Availability** 속성을 사용합니다.

**Availability** 값이 **None** 이면 세션에 연결할 수 있습니다. **사용 중** 값은 다른 세션에 연결 되어 있으므로 **PSSession** 에 연결할 수 없음을 나타냅니다. 세션의 **State** 속성 값에 대 한 자세한 내용은 [RunspaceState](/dotnet/api/system.management.automation.runspaces.runspacestate)를 참조 하세요. 세션의 **Availability** 속성 값에 대 한 자세한 내용은 [RunspaceAvailability](/dotnet/api/system.management.automation.runspaces.runspaceavailability)를 참조 하십시오.

**HostName** 및 **SSHConnection** 매개 변수는 PowerShell 6.0부터 포함 되었습니다. Secure Shell (SSH)를 기반으로 PowerShell 원격 기능을 제공 하기 위해 추가 되었습니다. Powershell 및 SSH는 여러 플랫폼 (Windows, Linux, macOS)에서 지원 되며 powershell 원격은 PowerShell 및 SSH가 설치 되 고 구성 되는 이러한 플랫폼에 대해 작동 합니다. 이는 WinRM을 기반으로 하는 이전 Windows 전용 원격 시스템과 별개 이며, 많은 WinRM 특정 기능 및 제한 사항이 적용 되지 않습니다. 예를 들어 WinRM 기반 할당량, 세션 옵션, 사용자 지정 끝점 구성 및 연결 끊기/다시 연결 기능은 현재 지원 되지 않습니다. PowerShell SSH 원격을 설정 하는 방법에 대 한 자세한 내용은 [ssh를 통한 Powershell 원격](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core)을 참조 하세요.

## 관련 링크

[about_PSSessions](./About/about_PSSessions.md)

[about_Remote](./About/about_Remote.md)

[about_Remote_Disconnected_Sessions](./About/about_Remote_Disconnected_Sessions.md)

[about_Remote_Troubleshooting](./About/about_remote_troubleshooting.md)

[about_Remote_Variables](./About/about_Remote_Variables.md)

[about_Scopes](./About/about_scopes.md)

[Enter-PSSession](Enter-PSSession.md)

[Exit-PSSession](Exit-PSSession.md)

[Get-PSSession](Get-PSSession.md)

[Invoke-Item](../Microsoft.PowerShell.Management/Invoke-Item.md)

[New-PSSession](New-PSSession.md)

[Remove-PSSession](Remove-PSSession.md)

[WSMan 공급자](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

