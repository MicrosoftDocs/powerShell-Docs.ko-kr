---
description: PowerShell 세션 (PSSession)에 대 한 연결을 끊고 다시 연결 하는 방법을 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 12/01/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_disconnected_sessions?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Disconnected_Sessions
ms.openlocfilehash: f4dbcd4d9255e4285687692902a41a3f3f40e093
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93223801"
---
# <a name="about-remote-disconnected-sessions"></a>연결 되지 않은 원격 세션 정보

## <a name="short-description"></a>간단한 설명

PowerShell 세션 (PSSession)에 대 한 연결을 끊고 다시 연결 하는 방법을 설명 합니다.

## <a name="long-description"></a>자세한 설명입니다.

PowerShell 3.0부터 PSSession에서 연결을 끊고 동일한 컴퓨터 또는 다른 컴퓨터의 PSSession에 다시 연결할 수 있습니다. 세션의 연결이 끊어지면 세션 상태가 유지 되 고 PSSession의 명령이 계속 실행 됩니다.

연결이 끊어진 세션 기능은 원격 컴퓨터에서 PowerShell 3.0 이상 버전을 실행 하는 경우에만 사용할 수 있습니다.

연결 끊김 세션 기능을 사용 하면 pssession이 생성 된 세션을 닫고, PowerShell을 닫고, PSSession에서 실행 중인 명령을 방해 하지 않고 컴퓨터를 종료할 수도 있습니다. 연결 되지 않은 세션은 완료 하는 데 오랜 시간이 걸리는 명령을 실행 하는 데 유용 하며 IT 전문가에 게 필요한 시간과 장치 유연성을 제공 합니다.

Cmdlet을 사용 하 여 시작 된 대화형 세션에서 연결을 끊을 수 없습니다 `Enter-PSSession` .

연결 되지 않은 세션을 사용 하 여 컴퓨터 또는 네트워크 중단으로 인해 실수로 연결 해제 된 pssession을 관리할 수 있습니다.

실제 사용에서 연결 끊김 기능을 사용 하면 문제 해결을 시작 하 고, 더 높은 우선 순위 문제를 확인 하 고, 다른 위치에 있는 다른 컴퓨터를 비롯 하 여 솔루션에서 작업을 다시 시작할 수 있습니다.

## <a name="disconnected-session-cmdlets"></a>연결 되지 않은 세션 cmdlet

다음 cmdlet은 Disconnected 세션 기능을 지원 합니다.

- `Connect-PSSession`: 연결 되지 않은 PSSession에 연결 합니다.
- `Disconnect-PSSession`: PSSession의 연결을 끊습니다.
- `Get-PSSession`: 로컬 컴퓨터 또는 원격 컴퓨터에서 PSSessions를 가져옵니다.
- `Receive-PSSession`: 연결 되지 않은 세션에서 실행 된 명령의 결과를 가져옵니다.
- `Invoke-Command`: **InDisconnectedSession** 매개 변수는 PSSession을 만들고 즉시 연결을 끊습니다.

## <a name="how-the-disconnected-sessions-feature-works"></a>연결 되지 않은 세션 기능의 작동 방식

PowerShell 3.0부터 pssession은 생성 된 세션과는 독립적입니다. 활성 PSSession은 PSSession을 만든 세션이 닫히고 원래 컴퓨터가 종료 되거나 네트워크에서 연결이 끊어진 경우에도 연결의 원격 컴퓨터 또는 **서버 쪽** 에서 유지 관리 됩니다.

PowerShell 2.0에서 PSSession은 원래 세션이 나 생성 된 세션이 종료 될 때 원격 컴퓨터에서 삭제 됩니다.

PSSession의 연결을 끊으면 PSSession이 활성 상태로 유지 되 고 원격 컴퓨터에서 유지 관리 됩니다. 세션 상태가 **실행 중** 에서 **Disconnected** 로 변경 됩니다. 현재 세션 또는 동일한 컴퓨터의 다른 세션이 나 다른 컴퓨터에서 연결이 끊어진 PSSession에 다시 연결할 수 있습니다. 세션을 유지 관리 하는 원격 컴퓨터가 실행 중 이어야 하 고 네트워크에 연결 되어 있어야 합니다.

연결 끊김 PSSession의 명령은 명령이 완료 되거나 출력 버퍼가 채워질 때까지 원격 컴퓨터에서 중단 없이 계속 실행 됩니다. 전체 출력 버퍼가 명령을 일시 중단 하지 않도록 하려면, 또는 cmdlet의 **OutputBufferingMode** 매개 변수를 `Disconnect-PSSession` 사용 `New-PSSessionOption` `New-PSTransportOption` 합니다.

연결 되지 않은 세션은 원격 컴퓨터에서 연결 되지 않은 상태로 유지 됩니다. Cmdlet을 사용 `Remove-PSSession` 하거나 pssession의 유휴 시간 제한이 만료 될 때 까지는 pssession을 삭제할 때까지 다시 연결할 수 있습니다. , 또는 cmdlet의 **IdleTimeoutSec** 또는 **IdleTimeout** 매개 변수를 사용 하 여 PSSession의 유휴 시간 제한을 조정할 수 있습니다 `Disconnect-PSSession` `New-PSSessionOption` `New-PSTransportOption` .

다른 사용자가 만든 pssession에 연결할 수 있지만 세션을 만드는 데 사용 된 자격 증명을 제공할 수 있는 경우에만 `RunAs` 세션 구성의 자격 증명을 사용할 수 있습니다.

## <a name="how-to-get-pssessions"></a>PSSessions를 가져오는 방법

PowerShell 3.0부터 `Get-PSSession` cmdlet은 로컬 컴퓨터와 원격 컴퓨터에서 PSSessions를 가져옵니다. 현재 세션에서 만들어진 pssession도 가져올 수 있습니다.

로컬 컴퓨터 또는 원격 컴퓨터에서 pssession을 가져오려면 **ComputerName** 또는 **connectionuri** 매개 변수를 사용 합니다. 매개 변수가 없으면는 `Get-PSSession` 종료 위치에 관계 없이 로컬 세션에서 만들어진 PSSession을 가져옵니다.

Pssession을 가져올 때는 해당 세션이 유지 되 고 있는 컴퓨터, 즉 원격 **서버 또는 서버 쪽** 컴퓨터에서이를 확인 해야 합니다.

예를 들어 Server01 컴퓨터에 대 한 PSSession을 만드는 경우 Server01 컴퓨터에서 세션을 가져옵니다. 다른 컴퓨터에서 로컬 컴퓨터로 PSSession을 만드는 경우 로컬 컴퓨터에서 세션을 가져옵니다.

다음 명령 시퀀스는가 작동 하는 방법을 보여 줍니다 `Get-PSSession` .

첫 번째 명령은 Server01 컴퓨터에 대 한 세션을 만듭니다. 세션은 Server01 컴퓨터에 상주 합니다.

```powershell
New-PSSession -ComputerName Server01
```

```Output
Id Name      ComputerName  State    ConfigurationName     Availability
-- ----      ------------  -----    -----------------     ------------
 2 Session2  Server01      Opened   Microsoft.PowerShell     Available
```

세션을 가져오려면의 **ComputerName** 매개 변수를 `Get-PSSession` Server01 값과 함께 사용 합니다.

```powershell
Get-PSSession -ComputerName Server01
```

```Output
Id Name      ComputerName  State    ConfigurationName     Availability
-- ----      ------------  -----    -----------------     ------------
 2 Session2  Server01      Opened   Microsoft.PowerShell     Available
```

의 **ComputerName** 매개 변수 값 `Get-PSSession` 이 localhost 인 경우는 `Get-PSSession` 에서 종료 되 고 로컬 컴퓨터에서 유지 관리 되는 pssession을 가져옵니다. 로컬 컴퓨터에서 시작 된 경우에도 Server01 컴퓨터에서 pssession을 가져오지 않습니다.

```powershell
Get-PSSession -ComputerName localhost
```

현재 세션에서 만든 세션을 가져오려면 `Get-PSSession` 매개 변수 없이 cmdlet을 사용 합니다. 이 예에서는 `Get-PSSession` 현재 세션에서 만들어진 PSSession을 가져오고 Server01 컴퓨터에 연결 합니다.

```powershell
Get-PSSession
```

```Output
Id Name      ComputerName  State    ConfigurationName     Availability
-- ----      ------------  -----    -----------------     ------------
 2 Session2  Server01      Opened   Microsoft.PowerShell     Available
```

## <a name="how-to-disconnect-sessions"></a>세션의 연결을 끊는 방법

PSSession의 연결을 끊으려면 cmdlet을 사용 `Disconnect-PSSession` 합니다. PSSession을 식별 하려면 **Session** 매개 변수를 사용 하거나 또는 cmdlet에서로 pssession을 파이프라인 합니다 `New-PSSession` `Get-PSSession` `Disconnect-PSSession` .

다음 명령은 PSSession을 Server01 컴퓨터와의 연결을 끊습니다.
**State** 속성의 값이 **Disconnected** 이 고 **Availability** 가 **None** 입니다.

```powershell
Get-PSSession -ComputerName Server01 | Disconnect-PSSession
```

```Output
Id Name      ComputerName  State         ConfigurationName     Availability
-- ----      ------------  -----         -----------------     ------------
 2 Session2  Server01      Disconnected  Microsoft.PowerShell          None
```

연결 되지 않은 세션을 만들려면 cmdlet의 **InDisconnectedSession** 매개 변수를 사용 합니다 `Invoke-Command` . 명령이 출력을 반환 하기 전에 세션을 만들고, 명령을 시작 하 고, 즉시 연결을 끊습니다.

다음 명령은 `Get-WinEvent` Server02 원격 컴퓨터의 연결 되지 않은 세션에서 명령을 실행 합니다.

```powershell
Invoke-Command -ComputerName Server02 -InDisconnectedSession -ScriptBlock {
   Get-WinEvent -LogName "*PowerShell*" }
```

```Output
Id Name      ComputerName  State         ConfigurationName     Availability
-- ----      ------------  -----         -----------------     ------------
 4 Session3  Server02      Disconnected  Microsoft.PowerShell          None
```

## <a name="how-to-connect-to-disconnected-sessions"></a>연결이 끊어진 세션에 연결 하는 방법

PSSession을 만든 세션이 나 로컬 컴퓨터 또는 다른 컴퓨터의 다른 세션에서 연결이 끊어진 모든 PSSession에 연결할 수 있습니다.

PSSession을 만들고, PSSession에서 명령을 실행 하 고, PSSession에서 연결을 끊고, PowerShell을 닫고, 컴퓨터를 종료할 수 있습니다. 나중에 다른 컴퓨터를 열고, PSSession을 가져오고, 연결 하 고, 연결이 끊어진 동안 PSSession에서 실행 된 명령의 결과를 가져올 수 있습니다. 그런 다음 세션에서 더 많은 명령을 실행할 수 있습니다.

연결이 끊어진 PSSession을 연결 하려면 cmdlet을 사용 `Connect-PSSession` 합니다. **ComputerName** 또는 **connectionuri** 매개 변수를 사용 하 여 pssession을 식별 하거나에서로 pssession을 파이프라인 합니다 `Get-PSSession` `Connect-PSSession` .

다음 명령은 Server02 컴퓨터의 세션을 가져옵니다. 출력에는 두 개의 연결 되지 않은 세션 (둘 다 사용 가능)이 포함 됩니다.

```powershell
Get-PSSession -ComputerName Server02
```

```Output
Id Name      ComputerName   State         ConfigurationName     Availability
-- ----      ------------   -----         -----------------     ------------
 2 Session2  juneb-srv8320  Disconnected  Microsoft.PowerShell          None
 4 Session3  juneb-srv8320  Disconnected  Microsoft.PowerShell          None
```

다음 명령은 Session2에 연결 합니다. 이제 PSSession이 열리고 사용할 수 있습니다.

```powershell
Connect-PSSession -ComputerName Server02 -Name Session2
```

```Output
Id Name      ComputerName    State    ConfigurationName     Availability
-- ----      ------------    -----    -----------------     ------------
 2 Session2  juneb-srv8320   Opened   Microsoft.PowerShell     Available
```

## <a name="how-to-get-the-results"></a>결과를 얻는 방법

연결 되지 않은 PSSession에서 실행 된 명령의 결과를 가져오려면 cmdlet을 사용 합니다 `Receive-PSSession` .

`Receive-PSSession`Cmdlet을 사용 하는 대신을 사용할 수 있습니다 `Connect-PSSession` . 세션이 이미 다시 연결 된 경우 `Receive-PSSession` 세션의 연결이 끊어질 때 실행 된 명령의 결과를 가져옵니다. PSSession의 연결이 끊어지면에서 연결 된 `Receive-PSSession` 후에도 연결을 끊은 후 실행 된 명령의 결과를 가져옵니다.

`Receive-PSSession` 작업 (비동기적으로) 또는 호스트 프로그램 (동기적)으로 결과를 반환할 수 있습니다. **Outtarget** 매개 변수를 사용 하 여 **작업** 또는 **호스트** 를 선택 합니다. 기본값은 **Host** 입니다. 그러나 수신 중인 명령이 현재 세션에서 **작업** 으로 시작 된 경우에는 기본적으로 **작업** 으로 반환 됩니다.

다음 명령은 cmdlet을 사용 하 여 `Receive-PSSession` Server02 컴퓨터의 PSSession에 연결 하 고 `Get-WinEvent` Session3 세션에서 실행 된 명령의 결과를 가져옵니다. 이 명령은 **Outtarget** 매개 변수를 사용 하 여 **작업** 의 결과를 가져옵니다.

```powershell
Receive-PSSession -ComputerName Server02 -Name Session3 -OutTarget Job
```

```Output
Id   Name   PSJobTypeName   State         HasMoreData     Location
--   ----   -------------   -----         -----------     --------
 3   Job3   RemoteJob       Running       True            Server02
```

작업의 결과를 가져오려면 cmdlet을 사용 합니다 `Receive-Job` .

```powershell
Get-Job | Receive-Job -Keep
```

```Output
ProviderName: PowerShell

TimeCreated             Id LevelDisplayName Message     PSComputerName
-----------             -- ---------------- -------     --------------
5/14/2012 7:26:04 PM   400 Information      Engine stat Server02
5/14/2012 7:26:03 PM   600 Information      Provider "W Server02
5/14/2012 7:26:03 PM   600 Information      Provider "C Server02
5/14/2012 7:26:03 PM   600 Information      Provider "V Server02
```

## <a name="state-and-availability-properties"></a>상태 및 가용성 속성

연결이 끊어진 PSSession의 **상태** 및 **가용성** 속성은 세션을 연결할 수 있는지 여부를 알려 줍니다.

PSSession이 현재 세션에 연결 되 면 상태가 **열리고** 해당 가용성을 **사용할 수** 있습니다. PSSession에서 연결을 끊으면 PSSession 상태의 **연결이 끊어지고** 해당 가용성은 **None** 입니다.

**State** 속성 값은 현재 세션을 기준으로 합니다. **연결 끊김** 값은 PSSession이 현재 세션에 연결 되지 않았음을 의미 합니다. 그러나 모든 세션에서 PSSession의 연결이 끊어졌음을 의미 하는 것은 아닙니다. 다른 세션에 연결되어 있을 수도 있습니다.

PSSession에 연결 하거나 다시 연결할 수 있는지 확인 하려면 **Availability** 속성을 사용 합니다. **None** 값은 세션에 연결할 수 있음을 나타냅니다. **사용 중** 값은 다른 세션에 연결 되어 있으므로 PSSession에 연결할 수 없음을 나타냅니다.

다음 예제는 동일한 컴퓨터의 두 PowerShell 세션에서 실행 됩니다.
PSSession로 각 세션에서 **상태** 및 **가용성** 속성의 변경 값이 연결 해제 되 고 다시 연결 됩니다.

```powershell
# Session 1
New-PSSession -ComputerName Server30 -Name Test
```

```Output
Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
1  Test   Server30        Opened        Microsoft.PowerShell     Available
```

```powershell
# Session 2
Get-PSSession -ComputerName Server30 -Name Test
```

```Output
Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
1 Test    Server30        Disconnected  Microsoft.PowerShell          Busy
```

```powershell
# Session 1
Get-PSSession -ComputerName Server30 -Name Test | Disconnect-PSSession
```

```Output
Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
1 Test    Server30        Disconnected  Microsoft.PowerShell          None
```

```powershell
# Session 2
Get-PSSession -ComputerName Server30
```

```Output
Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
1 Test    Server30        Disconnected  Microsoft.PowerShell          None
```

```powershell
# Session 2
Connect-PSSession -ComputerName Server30 -Name Test
```

```Output
Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
3 Test    Server30        Opened        Microsoft.PowerShell     Available
```

```powershell
# Session 1
Get-PSSession -ComputerName Server30
```

```Output
Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
1 Test    Server30        Disconnected  Microsoft.PowerShell          Busy
```

```Output
# Idle Timeout
```

연결 되지 않은 세션은 cmdlet을 사용 하는 등의 방법으로 삭제 하거나 시간 초과 될 때까지 원격 컴퓨터에서 유지 관리 됩니다 `Remove-PSSession` . PSSession의 **IdleTimeout** 속성은 연결이 끊어진 세션이 삭제 되기 전에 유지 되는 기간을 결정 합니다.

PSSessions는 **하트 비트 스레드가** 응답을 받지 못한 경우 유휴 상태입니다.
연결이 끊어진 세션에서 아직 실행 되 고 있는 경우에도 세션의 연결을 해제 하면 해당 세션은 유휴 상태가 되 고 **IdleTimeout** 시계가 시작 됩니다. PowerShell은 연결 되지 않은 세션을 활성 상태로 유지 하지만 유휴 상태로 간주 합니다.

세션을 만들고 연결을 끊을 때 PSSession의 유휴 시간 제한 시간이 사용자 요구에 대 한 세션을 유지 하는 데 충분 한 긴 하지만 원격 컴퓨터에서 불필요 한 리소스를 사용 하는 것은 아닙니다.

세션 구성의 **IdleTimeoutMs** 속성은 세션 구성을 사용 하는 세션의 기본 유휴 제한 시간을 결정 합니다. 기본값을 재정의할 수 있지만 사용자가 사용 하는 값은 세션 구성의 **MaxIdleTimeoutMs** 속성을 초과할 수 없습니다.

세션 구성의 **IdleTimeoutMs** 및 **MaxIdleTimeoutMs** 값 값을 찾으려면 다음 명령 형식을 사용 합니다.

```powershell
Get-PSSessionConfiguration |
  Format-Table Name, IdleTimeoutMs, MaxIdleTimeoutMs
```

PSSession을 만들 때 및 연결을 끊을 때 세션 구성에서 기본값을 재정의 하 고 PSSession의 유휴 시간 제한을 설정할 수 있습니다.

원격 컴퓨터에서 Administrators 그룹의 구성원 인 경우 세션 구성의 **IdleTimeoutMs** 및 **MaxIdleTimeoutMs** 속성을 만들고 변경할 수 있습니다.

## <a name="idle-timeout-values"></a>유휴 시간 제한 값

세션 구성 및 세션 옵션의 유휴 시간 제한 값은 밀리초 단위입니다. 세션의 유휴 시간 제한 값과 세션 구성 옵션은 초 단위입니다.

PSSession ( `New-PSSession` ,)을 만들고 `Invoke-Command` 연결을 끊을 때 () pssession의 유휴 시간 제한을 설정할 수 있습니다 `Disconnect-PSSession` . 그러나 PSSession ()에 연결 하거나 결과를 가져올 때는 **IdleTimeout** 값을 변경할 수 없습니다 `Connect-PSSession` ( `Receive-PSSession` ).

`Connect-PSSession`및 cmdlet에는 `Receive-PSSession` cmdlet에서 반환 된 것과 같은 **sessionoption** 개체를 사용 하는 **sessionoption** 매개 변수가 있습니다 `New-PSSessionOption` . **Sessionoption** 개체의 **idletimeout** 값과 기본 설정 변수의 **idletimeout** 값은 `$PSSessionOption` 또는 명령에서 PSSession의 **idletimeout** 값을 변경 하지 않습니다 `Connect-PSSession` `Receive-PSSession` .

특정 유휴 시간 제한 값을 사용 하 여 PSSession을 만들려면 `$PSSessionOption` 기본 설정 변수를 만듭니다. **IdleTimeout** 속성의 값을 원하는 값 (밀리초)으로 설정 합니다.

Pssession을 만들 때 변수 값이 `$PSSessionOption` 세션 구성의 값 보다 우선 적용 됩니다.

예를 들어 다음 명령은 유휴 시간 제한을 48 시간으로 설정 합니다.

```powershell
$PSSessionOption = New-PSSessionOption -IdleTimeoutMSec 172800000
```

특정 유휴 시간 제한 값을 사용 하 여 PSSession을 만들려면 cmdlet의 **IdleTimeoutMSec** 매개 변수를 사용 합니다 `New-PSSessionOption` . 그런 다음 또는 cmdlet의 **sessionoption** 매개 변수 값에서 session 옵션을 사용 합니다 `New-PSSession` `Invoke-Command` .

세션을 만들 때 설정 된 값은 `$PSSessionOption` 기본 설정 변수 및 세션 구성에 설정 된 값 보다 우선 적용 됩니다.

다음은 그 예입니다. 

```powershell
$o = New-PSSessionOption -IdleTimeoutMSec 172800000
New-PSSession -SessionOption $o
```

연결을 끊을 때 PSSession의 유휴 시간 제한을 변경 하려면 cmdlet의 **IdleTimeoutSec** 매개 변수를 사용 합니다 `Disconnect-PSSession` .

다음은 그 예입니다. 

```powershell
Disconnect-PSSession -IdleTimeoutSec 172800
```

특정 유휴 시간 제한 및 최대 유휴 시간 제한으로 세션 구성을 만들려면 cmdlet의 **IdleTimeoutSec** 및 **MaxIdleTimeoutSec** 매개 변수를 사용 합니다 `New-PSTransportOption` . 그런 다음 **의 매개 변수** 값에서 transport 옵션을 사용 `Register-PSSessionConfiguration` 합니다.

다음은 그 예입니다. 

```powershell
$o = New-PSTransportOption -IdleTimeoutSec 172800 -MaxIdleTimeoutSec 259200
Register-PSSessionConfiguration -Name Test -TransportOption $o
```

세션 구성의 기본 유휴 시간 제한 및 최대 유휴 시간 제한을 변경 하려면 cmdlet의 **IdleTimeoutSec** 및 **MaxIdleTimeoutSec** 매개 변수를 사용 합니다 `New-PSTransportOption` . 그런 다음 **의 매개 변수** 값에서 transport 옵션을 사용 `Set-PSSessionConfiguration` 합니다.

다음은 그 예입니다. 

```powershell
$o = New-PSTransportOption -IdleTimeoutSec 172800 -MaxIdleTimeoutSec 259200
Set-PSSessionConfiguration -Name Test -TransportOption $o
```

## <a name="output-buffering-mode"></a>출력 버퍼링 모드

PSSession의 출력 버퍼링 모드는 PSSession의 출력 버퍼가 가득 찬 경우 명령 출력을 관리 하는 방법을 결정 합니다.

연결이 끊어진 세션에서 출력 버퍼링 모드는 세션의 연결이 끊어지는 동안 명령이 계속 실행 되는지 여부를 효과적으로 결정 합니다.

유효한 값은 다음과 같습니다.

- **블록**. 출력 버퍼가 가득 찰 경우 버퍼를 지울 때까지 실행이 일시 중단됩니다. 기본값입니다.
- **Drop** 출력 버퍼가 가득 차도 실행이 계속됩니다. 새 출력이 생성 되 면 가장 오래 된 출력이 삭제 됩니다.

**Block** 은 데이터를 유지 하지만 명령을 중단할 수 있습니다. 값이 **Drop** 이면 데이터가 손실될 수는 있지만 명령을 완료할 수 있습니다. **Drop** 값을 사용할 경우 명령 출력을 디스크의 파일로 리디렉션합니다. 이 값은 연결이 끊어진 세션에 권장 됩니다.

세션 구성의 **OutputBufferingMode** 속성은 세션 구성을 사용 하는 세션의 기본 출력 버퍼링 모드를 결정 합니다.

**OutputBufferingMode** 의 세션 구성 값을 찾기 위해 다음 명령 형식 중 하나를 사용할 수 있습니다.

```powershell
(Get-PSSessionConfiguration <ConfigurationName>).OutputBufferingMode
```

```powershell
Get-PSSessionConfiguration | Format-Table Name, OutputBufferingMode
```

세션 구성에서 기본값을 재정의 하 고 PSSession을 만들 때, 연결을 끊을 때 및 다시 연결할 때 PSSession의 출력 버퍼링 모드를 설정할 수 있습니다.

원격 컴퓨터에서 Administrators 그룹의 구성원 인 경우 세션 구성의 출력 버퍼링 모드를 만들고 변경할 수 있습니다.

출력 버퍼링 모드가 **drop** 인 PSSession을 만들려면 `$PSSessionOption` **OutputBufferingMode** 속성 값이 **drop** 인 기본 설정 변수를 만듭니다.

Pssession을 만들 때 변수 값이 `$PSSessionOption` 세션 구성의 값 보다 우선 적용 됩니다.

다음은 그 예입니다. 

```powershell
$PSSessionOption = New-PSSessionOption -OutputBufferingMode Drop
```

출력 버퍼링 모드가 **drop** 인 PSSession을 만들려면 Cmdlet의 **OutputBufferingMode** 매개 변수를 사용 하 여 drop 값을 사용 하 `New-PSSessionOption` 여 세션 옵션을 만듭니다. **Drop** 그런 다음 또는 cmdlet의 **sessionoption** 매개 변수 값에서 session 옵션을 사용 합니다 `New-PSSession` `Invoke-Command` .

세션을 만들 때 설정 된 값은 `$PSSessionOption` 기본 설정 변수 및 세션 구성에 설정 된 값 보다 우선 적용 됩니다.

다음은 그 예입니다. 

```powershell
$o = New-PSSessionOption -OutputBufferingMode Drop
New-PSSession -SessionOption $o
```

연결을 끊을 때 PSSession의 출력 버퍼링 모드를 변경 하려면 cmdlet의 **OutputBufferingMode** 매개 변수를 사용 합니다 `Disconnect-PSSession` .

다음은 그 예입니다. 

```powershell
Disconnect-PSSession -OutputBufferingMode Drop
```

다시 연결할 때 PSSession의 출력 버퍼링 모드를 변경 하려면 cmdlet의 **OutputBufferingMode** 매개 변수를 사용 `New-PSSessionOption` 하 여 **Drop** 값을 사용 하 여 세션 옵션을 만듭니다. 그런 다음 또는의 **sessionoption** 매개 변수 값에서 session 옵션을 사용 합니다 `Connect-PSSession` `Receive-PSSession` .

다음은 그 예입니다. 

```powershell
$o = New-PSSessionOption -OutputBufferingMode Drop
Connect-PSSession -ComputerName Server01 -Name Test -SessionOption $o
```

**Drop** 의 기본 출력 버퍼링 모드를 사용 하 여 세션 구성을 만들려면 Cmdlet의 **OutputBufferingMode** 매개 변수를 사용 하 여 `New-PSTransportOption` 값을 **drop** 으로 설정 하 여 전송 옵션 개체를 만듭니다. 그런 다음 **의 매개 변수** 값에서 transport 옵션을 사용 `Register-PSSessionConfiguration` 합니다.

다음은 그 예입니다. 

```powershell
$o = New-PSTransportOption -OutputBufferingMode Drop
Register-PSSessionConfiguration -Name Test -TransportOption $o
```

세션 구성의 기본 출력 버퍼링 모드를 변경 하려면 cmdlet의 **OutputBufferingMode** 매개 변수를 사용 `New-PSTransportOption` 하 여 값을 **Drop** 으로 설정 하 여 전송 옵션을 만듭니다. 그런 다음의 **sessionoption** 매개 변수 값에서 Transport 옵션을 사용 합니다 `Set-PSSessionConfiguration` .

다음은 그 예입니다. 

```powershell
$o = New-PSTransportOption -OutputBufferingMode Drop
Set-PSSessionConfiguration -Name Test -TransportOption $o
```

## <a name="disconnecting-loopback-sessions"></a>루프백 세션 연결 끊기

루프백 세션 또는 로컬 세션은 동일한 컴퓨터에서 시작 하 여 종료 되는 pssession입니다. 다른 pssession과 마찬가지로 활성 루프백 세션은 연결의 원격 끝에 있는 컴퓨터 (로컬 컴퓨터)에서 유지 되므로 루프백 세션에서 연결을 끊고 다시 연결할 수 있습니다.

기본적으로 루프백 세션은 세션에서 명령을 실행 하 여 다른 컴퓨터에 액세스할 수 없도록 하는 네트워크 보안 토큰을 사용 하 여 생성 됩니다. 로컬 컴퓨터 또는 원격 컴퓨터의 모든 세션에서 네트워크 보안 토큰이 있는 루프백 세션에 다시 연결할 수 있습니다.

그러나, 또는 cmdlet의 **EnableNetworkAccess** 매개 변수를 사용 하는 경우 `New-PSSession` `Enter-PSSession` `Invoke-Command` 루프백 세션은 대화형 보안 토큰을 사용 하 여 만들어집니다. 대화형 토큰을 사용 하면 루프백 세션에서 실행 되는 명령을 사용 하 여 다른 컴퓨터에서 데이터를 가져올 수 있습니다.

대화형 토큰을 사용 하 여 루프백 세션의 연결을 끊은 다음 동일한 세션 또는 동일한 컴퓨터의 다른 세션에서 다시 연결할 수 있습니다.
그러나 악의적인 액세스를 방지 하기 위해 자신이 만든 컴퓨터 에서만 대화형 토큰을 사용 하 여 루프백 세션에 다시 연결할 수 있습니다.

## <a name="waiting-for-jobs-in-disconnected-sessions"></a>연결 되지 않은 세션에서 작업을 기다리는 중

`Wait-Job`Cmdlet은 작업이 완료 될 때까지 대기한 다음 명령 프롬프트나 다음 명령으로 돌아갑니다. 기본적으로는 `Wait-Job` 작업이 실행 중인 세션의 연결이 끊어질 때를 반환 합니다. `Wait-Job`세션이 다시 연결 될 때까지 대기 하도록 cmdlet을 지시 하려면 **열린** 상태에서 **Force** 매개 변수를 사용 합니다. 자세한 내용은 [대기 작업](xref:Microsoft.PowerShell.Core.Wait-Job)을 참조 하세요.

## <a name="robust-sessions-and-unintentional-disconnection"></a>강력한 세션 및 의도 하지 않은 연결 끊기

컴퓨터 오류 또는 네트워크 중단으로 인해 PSSession의 연결을 실수로 해제할 수 있습니다. PowerShell은 PSSession을 복구 하려고 시도 하지만 성공 여부는 문제의 심각도와 기간에 따라 달라 집니다.

실수로 연결이 끊긴 PSSession의 상태가 **끊어졌거나** **닫힐** 수 있지만 **연결이 끊어질** 수도 있습니다. **상태** 값이 **disconnected** 인 경우 세션의 연결이 해제 되는 것 처럼 동일한 기술을 사용 하 여 PSSession을 관리할 수 있습니다. 예를 들어 cmdlet을 사용 하 여 `Connect-PSSession` 세션에 다시 연결 하 고 cmdlet을 사용 하 여 `Receive-PSSession` 세션 연결이 끊어진 동안 실행 된 명령의 결과를 가져올 수 있습니다.

명령이 PSSession에서 실행 되는 동안 PSSession이 생성 된 세션을 닫은 (종료) 하면 PowerShell에서 원격 컴퓨터의 **연결 끊김** 상태로 pssession을 유지 관리 합니다. PSSession을 만든 세션을 닫거나 PSSession에서 실행 되는 명령이 없는 경우 PowerShell은 PSSession을 유지 관리 하려고 시도 하지 않습니다.

## <a name="see-also"></a>참고 항목

[about_Jobs](about_Jobs.md)

[about_Remote](about_Remote.md)

[about_Remote_Variables](about_Remote_Variables.md)

[about_PSSessions](about_PSSessions.md)

[about_Session_Configurations](about_Session_Configurations.md)

[Connect-PSSession](xref:Microsoft.PowerShell.Core.Connect-PSSession)

[Disconnect-PSSession](xref:Microsoft.PowerShell.Core.Disconnect-PSSession)

[Get-PSSession](xref:Microsoft.PowerShell.Core.Get-PSSession)

[Receive-PSSession](xref:Microsoft.PowerShell.Core.Receive-PSSession)

[Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command)
