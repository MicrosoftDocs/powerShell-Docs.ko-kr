---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 02/20/2019
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/register-cimindicationevent?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-CimIndicationEvent
ms.openlocfilehash: a5e801c2b41fff618c78b4abcec9d90d09ea2323
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93215121"
---
# Register-CimIndicationEvent

## 개요
필터 식이나 쿼리 식을 사용 하 여 표시를 구독 합니다.

## SYNTAX

### ClassNameComputerSet (기본값)

```
Register-CimIndicationEvent [-Namespace <String>] [-ClassName] <String>
 [-OperationTimeoutSec <UInt32>] [-ComputerName <String>] [[-SourceIdentifier] <String>]
 [[-Action] <ScriptBlock>] [-MessageData <PSObject>] [-SupportEvent] [-Forward]
 [-MaxTriggerCount <Int32>] [<CommonParameters>]
```

### ClassNameSessionSet

```
Register-CimIndicationEvent [-Namespace <String>] [-ClassName] <String>
 [-OperationTimeoutSec <UInt32>] -CimSession <CimSession> [[-SourceIdentifier] <String>]
 [[-Action] <ScriptBlock>] [-MessageData <PSObject>] [-SupportEvent] [-Forward]
 [-MaxTriggerCount <Int32>] [<CommonParameters>]
```

### QueryExpressionSessionSet

```
Register-CimIndicationEvent [-Namespace <String>] [-Query] <String> [-QueryDialect <String>]
 [-OperationTimeoutSec <UInt32>] -CimSession <CimSession> [[-SourceIdentifier] <String>]
 [[-Action] <ScriptBlock>] [-MessageData <PSObject>] [-SupportEvent] [-Forward]
 [-MaxTriggerCount <Int32>] [<CommonParameters>]
```

### QueryExpressionComputerSet

```
Register-CimIndicationEvent [-Namespace <String>] [-Query] <String> [-QueryDialect <String>]
 [-OperationTimeoutSec <UInt32>] [-ComputerName <String>] [[-SourceIdentifier] <String>]
 [[-Action] <ScriptBlock>] [-MessageData <PSObject>] [-SupportEvent] [-Forward]
 [-MaxTriggerCount <Int32>] [<CommonParameters>]
```

## 설명

Cmdlet은 표시 `Register-CimIndicationEvent` 클래스 이름 또는 쿼리 식을 사용 하 여 표시를 구독 합니다. **SourceIdentifier** 매개 변수를 사용 하 여 구독에 이름을 지정 합니다.

이 cmdlet은 **Eventsubscription** 개체를 반환 합니다. 이 개체를 사용 하 여 구독을 취소할 수 있습니다.

## 예제

### 예제 1: 클래스에 의해 생성 된 이벤트 등록

이 예제에서는 **Win32_ProcessStartTrace** 이라는 클래스에서 생성 된 이벤트를 구독 합니다. 이 클래스는 프로세스가 시작될 때마다 이벤트를 발생시킵니다.

```powershell
Register-CimIndicationEvent -ClassName 'Win32_ProcessStartTrace' -SourceIdentifier "ProcessStarted"
Get-Event -SourceIdentifier "ProcessStarted"
```

`Get-Event`Cmdlet은 **processstarted** 구독이 있는 이벤트를 가져옵니다. 자세한 내용은 [Get 이벤트](../Microsoft.PowerShell.Utility/Get-Event.md)를 참조 하세요.

> [!NOTE]
> 이 예에서는 관리자 권한으로 PowerShell을 실행 해야 합니다.

### 예제 2: 쿼리를 사용 하 여 이벤트 등록

이 예제에서는 쿼리를 사용 하 여 **Win32_LocalTime** 클래스 인스턴스가 변경 될 때마다 생성 되는 이벤트를 구독 합니다.

```powershell
$query = "SELECT * FROM CIM_InstModification WHERE TargetInstance ISA 'Win32_LocalTime'"
Register-CimIndicationEvent -Query $query -SourceIdentifier "Timer"
```

### 예제 3: 이벤트가 도착할 때 스크립트 실행

이 예제에서는 이벤트에 대 한 응답으로 작업을 사용 하는 방법을 보여 줍니다. 변수는 `$action` 변수를 사용 하 여 CIM에서 받은 이벤트에 액세스 하는 **동작** 에 대 한 스크립트 블록을 포함 합니다 `$event` .

```powershell
$action = {
  $name = $event.SourceEventArgs.NewEvent.ProcessName
  $id = $event.SourceEventArgs.NewEvent.ProcessId
  Write-Host -Object "New Process Started : Name = $name
 ID = $id"
}
Register-CimIndicationEvent -ClassName 'Win32_ProcessStartTrace' -SourceIdentifier "ProcessStarted" -Action $action
```

자세한 내용은 [Win32_ProcessStartTrace](/previous-versions/windows/desktop/krnlprov/win32-processstarttrace)를 참조 하세요.

### 예제 4: 원격 컴퓨터에 이벤트 등록

이 예제에서는 **Server01** 라는 원격 컴퓨터의 이벤트를 구독 합니다. CIM 서버에서 받은 이벤트는 현재 PowerShell 세션의 이벤트 큐에 저장 된 후 로컬를 실행 `Get-Event` 하 여 이벤트를 검색 합니다.

```powershell
Register-CimIndicationEvent -ClassName 'Win32_ProcessStartTrace' -SourceIdentifier "ProcessStarted" -ComputerName Server01
Get-Event -SourceIdentifier "ProcessStarted"
```

## PARAMETERS

### -Action

이벤트를 처리 하는 명령을 지정 합니다. 이 매개 변수에서 지정 하는 명령은 이벤트를 이벤트 큐로 보내는 대신 이벤트가 발생할 때 실행 됩니다. 명령을 중괄호 ()로 묶어 `{}` 스크립트 블록을 만듭니다.

**Action** 으로 지정 된 스크립트 블록에는 `$Event` `$EventSubscriber` `$Sender` `$SourceEventArgs` `$SourceArgs` **action** 스크립트 블록에 이벤트 정보를 제공 하는,,, 및 자동 변수가 포함 될 수 있습니다. 자세한 내용은 [자동 변수 정보](../microsoft.powershell.core/about/about_automatic_variables.md)를 참조 하세요.

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CimSession

지정 된 CIM 세션을 사용 하 여 명령을 실행 합니다. CIM 세션을 포함 하는 변수 또는 CIM 세션을 만들거나 가져오는 명령 (예: 또는 cmdlet)을 입력 합니다 `New-CimSession` `Get-CimSession` . 자세한 내용은 [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md)를 참조 하세요.

```yaml
Type: Microsoft.Management.Infrastructure.CimSession
Parameter Sets: ClassNameSessionSet, QueryExpressionSessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ClassName

구독할 표시 클래스를 지정 합니다. PowerShell은 클래스 이름 목록을 제공 하기 위해 로컬 WMI 서버에서 클래스 목록을 가져오기 때문에 탭 완성 기능을 사용 하 여 클래스 목록을 찾아볼 수 있습니다.

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, ClassNameSessionSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

CIM 작업을 실행 하려는 컴퓨터의 이름을 지정 합니다. FQDN (정규화 된 도메인 이름), NetBIOS 이름 또는 IP 주소를 지정할 수 있습니다.

이 매개 변수를 지정 하면 cmdlet이 WsMan 프로토콜을 사용 하 여 지정 된 컴퓨터에 대 한 임시 세션을 만듭니다. 이 매개 변수를 지정 하지 않으면 cmdlet은 COM (구성 요소 개체 모델)을 사용 하 여 로컬 시스템에서 작업을 수행 합니다.

동일한 컴퓨터에서 여러 작업을 수행 하는 경우 더 나은 성능을 위해 CIM 세션을 사용 하 여 연결 합니다.

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, QueryExpressionComputerSet
Aliases: CN, ServerName

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -전달

구독에 대 한 이벤트가 로컬 컴퓨터의 세션에 전달 됨을 나타냅니다. 원격 컴퓨터 또는 원격 세션에서 이벤트를 등록할 때 이 매개 변수를 사용합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaxTriggerCount

지정 된 시간 동안 트리거된 후 구독자가 자동으로 등록 취소 되어야 함을 나타내는 매개 변수입니다. 값이 0 보다 작거나 같으면 이벤트를 등록 취소 하지 않고 트리거할 수 있는 횟수에 제한이 없습니다.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MessageData

이 이벤트 구독에 연결할 추가 데이터를 지정 합니다. 이 매개 변수 값은이 구독과 연결 된 모든 이벤트의 **Messagedata** 속성에 표시 됩니다.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Namespace

CIM 작업에 대 한 네임 스페이스를 지정 합니다. 기본 네임 스페이스는 **root/cimv2** 입니다. PowerShell에서 네임 스페이스 목록을 제공 하기 위해 로컬 WMI 서버에서 네임 스페이스 목록을 가져오기 때문에 탭 완성 기능을 사용 하 여 네임 스페이스 목록을 찾아볼 수 있습니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -OperationTimeoutSec

Cmdlet이 컴퓨터의 응답을 기다리는 시간을 지정 합니다. 기본적으로이 매개 변수의 값은 0 이며이는 cmdlet이 서버에 대 한 기본 시간 제한 값을 사용 함을 의미 합니다.

**Operationtimeoutsec** 매개 변수가 강력한 연결 다시 시도 시간 제한 3 분 보다 작은 값으로 설정 된 경우, 서버에서 작업을 다시 연결할 수 있기 때문에 **operationtimeoutsec** 매개 변수의 값 보다 마지막으로 네트워크 오류가 복구 되지 않습니다.

```yaml
Type: System.UInt32
Parameter Sets: (All)
Aliases: OT

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Query

CIM 서버에서 실행할 쿼리를 지정 합니다. 지정 된 값에 큰따옴표 `"` , 작은따옴표 또는 백슬래시가 포함 된 경우 `'` `\` 백슬래시 문자를 접두사로 사용 하 여 해당 문자를 이스케이프 해야 합니다. 지정 된 값이 WQL LIKE 연산자를 사용 하는 경우 대괄호 ( `[]` 백분율 `%` , 밑줄 `_` 또는 여는 대괄호)로 묶어 다음 문자를 이스케이프 해야 `[` 합니다.

```yaml
Type: System.String
Parameter Sets: QueryExpressionSessionSet, QueryExpressionComputerSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -QueryDialect

**쿼리** 매개 변수에 사용 되는 쿼리 언어를 지정 합니다. 이 매개 변수에 허용 되는 값은 **WQL** 또는 **CQL** 입니다. 기본값은 **WQL** 입니다.

```yaml
Type: System.String
Parameter Sets: QueryExpressionSessionSet, QueryExpressionComputerSet
Aliases:

Required: False
Position: Named
Default value: WQL
Accept pipeline input: False
Accept wildcard characters: False
```

### -SourceIdentifier

구독의 이름을 지정 합니다. 지정 하는 이름은 현재 세션에서 고유 해야 합니다. 기본값은 PowerShell이 할당 하는 GUID입니다. 이 값은 구독자 개체 및이 구독과 연결 된 모든 이벤트 개체의 **SourceIdentifier** 속성 값에 표시 됩니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SupportEvent

이벤트 구독이 숨겨져 있음을 나타냅니다. 현재 구독이 더 복잡한 이벤트 등록 메커니즘의 일부이며 독립적으로 검색되지 않아야 하는 경우 이 매개 변수를 사용합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### 없음

이 cmdlet은 입력 개체를 허용 하지 않습니다.

## 출력

### System.Object

이 cmdlet은 **Eventsubscription** 개체를 출력 합니다.

## 참고

## 관련 링크

[Get-Event](../microsoft.powershell.utility/get-event.md)

[Remove-Event](../microsoft.powershell.utility/remove-event.md)

[Unregister-Event](../microsoft.powershell.utility/unregister-event.md)

[Write-Host](../microsoft.powershell.utility/write-host.md)

[Get-CimSession](Get-CimSession.md)

[New-CimSession](New-CimSession.md)
