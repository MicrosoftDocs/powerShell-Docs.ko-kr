---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 07/30/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/register-wmievent?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-WmiEvent
ms.openlocfilehash: be29ce6376dea7686c0c063cc5528fbc7d840a9d
ms.sourcegitcommit: 41b072f0b6046d619b0e7f758982783fb648a3d5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/31/2020
ms.locfileid: "93219049"
---
# Register-WmiEvent

## 개요
WMI(Windows Management Instrumentation) 이벤트를 구독합니다.

## SYNTAX

### 클래스 (기본값)

```
Register-WmiEvent [-Namespace <String>] [-Credential <PSCredential>] [-ComputerName <String>] [-Class] <String>
 [-Timeout <Int64>] [[-SourceIdentifier] <String>] [[-Action] <ScriptBlock>] [-MessageData <PSObject>]
 [-SupportEvent] [-Forward] [-MaxTriggerCount <Int32>] [<CommonParameters>]
```

### Query

```
Register-WmiEvent [-Namespace <String>] [-Credential <PSCredential>] [-ComputerName <String>] [-Query] <String>
 [-Timeout <Int64>] [[-SourceIdentifier] <String>] [[-Action] <ScriptBlock>] [-MessageData <PSObject>]
 [-SupportEvent] [-Forward] [-MaxTriggerCount <Int32>] [<CommonParameters>]
```

## 설명

`Register-WmiEvent`Cmdlet은 로컬 컴퓨터 또는 원격 컴퓨터에서 WMI(Windows Management Instrumentation) (WMI) 이벤트를 구독 합니다.

구독한 WMI 이벤트가 발생할 경우 원격 컴퓨터에서 이벤트가 발생해도 로컬 세션의 이벤트 큐에 추가됩니다. 이벤트 큐에서 이벤트를 가져오려면 cmdlet을 사용 `Get-Event` 합니다.

의 매개 변수를 사용 하 여 `Register-WmiEvent` 원격 컴퓨터의 이벤트를 구독 하 고, 큐에서 이벤트를 식별 하는 데 도움이 될 수 있는 이벤트의 속성 값을 지정할 수 있습니다. **Action** 매개 변수를 사용 하 여 구독 된 이벤트가 발생할 때 수행할 작업을 지정할 수도 있습니다.

이벤트를 구독하면 이벤트 구독자가 세션에 추가됩니다. 세션의 이벤트 구독자를 가져오려면 cmdlet을 사용 합니다 `Get-EventSubscriber` . 구독을 취소 하려면 `Unregister-Event` 세션에서 이벤트 구독자를 삭제 하는 cmdlet을 사용 합니다.

Windows PowerShell 3.0에서 도입 된 새로운 CIM(Common Information Model) (CIM) cmdlet은 WMI cmdlet과 동일한 작업을 수행 합니다. CIM cmdlet은 Windows 운영 체제를 실행 하는 컴퓨터 및 다른 운영 체제를 실행 하는 컴퓨터를 관리 하는 데 동일한 기술을 사용할 수 있도록 하는 CIM 표준과 WS-Management (WSMan) 표준을 준수 합니다. 를 사용 하는 대신 `Register-WmiEvent` [CimIndicationEvent](../cimcmdlets/register-cimindicationevent.md) cmdlet을 사용 하는 것이 좋습니다.

## 예제

### 예제 1: 클래스에서 생성 된 이벤트 구독

이 명령은 **Win32_ProcessStartTrace** 클래스에 의해 생성 된 이벤트를 구독 합니다. 이 클래스는 프로세스가 시작될 때마다 이벤트를 발생시킵니다.

```powershell
Register-WmiEvent -Class 'Win32_ProcessStartTrace' -SourceIdentifier "ProcessStarted"
```

### 예 2: 프로세스에 대 한 생성 이벤트 구독

이 명령은 쿼리를 사용하여 Win32_process 인스턴스 만들기 이벤트를 구독합니다.

```powershell
$wmiParameters = @{
  Query = "select * from __instancecreationevent within 5 where targetinstance isa 'win32_process'"
  SourceIdentifier = "WMIProcess"
  MessageData = "Test 01"
  TimeOut = 500
}
Register-WmiEvent @wmiParameters
```

### 예제 3: 작업을 사용 하 여 이벤트에 응답

이 예제에서는 작업을 사용하여 이벤트에 응답하는 방법을 보여 줍니다. 이 경우 프로세스가 시작 되 면 `Start-Process` 현재 세션의 모든 명령이 XML 파일에 기록 됩니다.

```powershell
$action = { Get-History | where { $_.commandline -like "*start-process*" } | export-cliXml "commandHistory.clixml" }
Register-WmiEvent -Class 'Win32_ProcessStartTrace' -SourceIdentifier "ProcessStarted" -Action $action
```

```Output
Id    Name            State      HasMoreData   Location  Command
--    ----            -----      -----------   --------  -------
1     ProcessStarted  NotStarted False                   get-history | where {...
```

**Action** 매개 변수를 사용 하는 경우는 `Register-WmiEvent` 이벤트 동작을 나타내는 백그라운드 작업을 반환 합니다. **작업** cmdlet (예: 및)을 사용 `Get-Job` `Receive-Job` 하 여 이벤트 작업을 관리할 수 있습니다.

자세한 내용은 about_Jobs를 참조하세요.

### 예제 4: 원격 컴퓨터의 이벤트 등록

이 예제에서는 Server01 원격 컴퓨터의 이벤트를 등록합니다.

```powershell
Register-WmiEvent -Class 'Win32_ProcessStartTrace' -SourceIdentifier "Start" -Computername Server01
Get-Event -SourceIdentifier "Start"
```

WMI에서 이벤트를 로컬 컴퓨터에 반환하고 현재 세션의 이벤트 큐에 저장합니다. 이벤트를 검색 하려면 로컬 `Get-Event` 명령을 실행 합니다.

## PARAMETERS

### -Action

이벤트를 처리하는 명령을 지정합니다. 이벤트 큐에 이벤트를 전송 하는 대신 이벤트를 발생 시킬 때 **Action** 매개 변수의 명령이 실행 됩니다. 명령을 중괄호 ()로 묶어 `{}` 스크립트 블록을 만듭니다.

**Action** 값에는 `$Event` `$EventSubscriber` `$Sender` `$EventArgs` `$Args` **동작** 스크립트 블록에 이벤트 정보를 제공 하는,,, 및 자동 변수가 포함 될 수 있습니다. 자세한 내용은 about_Automatic_Variables를 참조하세요.

작업을 지정 하면 `Register-WmiEvent` 는 해당 동작을 나타내는 이벤트 작업 개체를 반환 합니다. **작업** 명사 ( **job** cmdlet)를 포함 하는 cmdlet을 사용 하 여 이벤트 작업을 관리할 수 있습니다.

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: False
Position: 101
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -클래스

구독할 이벤트를 지정합니다. 이벤트를 생성하는 WMI 클래스를 입력합니다. **클래스** 또는 **쿼리** 매개 변수는 모든 명령에 필요 합니다.

```yaml
Type: System.String
Parameter Sets: class
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

명령이 실행 되는 컴퓨터의 이름을 지정 합니다. 기본값은 로컬 컴퓨터입니다.

컴퓨터의 NetBIOS 이름, IP 주소 또는 정규화된 도메인 이름을 입력하세요. 로컬 컴퓨터를 지정 하려면 컴퓨터 이름, 점 ( `.` ) 또는 localhost를 입력 합니다.

이 매개 변수는 Windows PowerShell 원격 기능을 사용하지 않습니다. 원격 명령을 실행하도록 컴퓨터를 구성하지 않은 경우에도 **ComputerName** 매개 변수를 사용할 수 있습니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Cn

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential

이 작업을 수행할 권한이 있는 사용자 계정을 지정합니다. 기본값은 현재 사용자입니다.

User01 또는 Domain01\User01과 같은 사용자 이름을 입력 하거나, cmdlet에 의해 생성 된 것과 같은 **PSCredential** 개체를 입력 합니다 `Get-Credential` . 사용자 이름을 입력 하는 경우이 cmdlet은 암호를 묻는 메시지를 표시 합니다.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -전달

이 cmdlet이이 구독에 대 한 이벤트를 로컬 컴퓨터의 세션으로 보내도록 지정 합니다.
원격 컴퓨터 또는 원격 세션에서 이벤트를 등록할 때 이 매개 변수를 사용합니다.

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

최대 트리거 수를 지정 합니다.

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

이 이벤트 구독에 연결할 추가 데이터를 지정합니다. 이 매개 변수 값은이 구독과 연결 된 모든 이벤트의 **Messagedata** 속성에 표시 됩니다.

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

WMI 클래스의 네임스페이스를 지정합니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: NS

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Query

WMI 이벤트 클래스를 식별 하는 쿼리를 WQL(WMI Query Language) (WQL)로 지정 합니다 (예:) `select * from __InstanceDeletionEvent` .

```yaml
Type: System.String
Parameter Sets: query
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SourceIdentifier

선택한 구독 이름을 지정합니다. 선택한 이름은 현재 세션에서 고유해야 합니다. 기본값은 Windows PowerShell이 할당하는 GUID입니다.

이 매개 변수 값은 구독자 개체 및 이 구독과 연결된 모든 이벤트 개체의 **SourceIdentifier** 속성 값에 표시됩니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 100
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SupportEvent

이 cmdlet이 이벤트 구독을 숨기는 것을 나타냅니다. 현재 구독이 더 복잡한 이벤트 등록 메커니즘의 일부이며 독립적으로 검색되지 않아야 하는 경우 이 매개 변수를 사용합니다.

**Supportevent** 매개 변수를 사용 하 여 만든 구독을 보거나 취소 하려면 및 Cmdlet의 **Force** 매개 변수를 지정 `Get-EventSubscriber` 합니다 `Unregister-Event` .

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

### -시간 제한

Windows PowerShell에서이 명령이 완료 될 때까지 대기 하는 기간을 지정 합니다.

기본값 0은 시간 제한이 없음을 의미하며 Windows PowerShell에서 무기한 대기합니다.

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases: TimeoutMSec

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

이 cmdlet에 개체를 파이프할 수 없습니다.

## 출력

### 없음

이 cmdlet은 어떠한 출력도 생성하지 않습니다.

## 참고

Windows Vista 또는 이후 버전의 Windows 운영 체제에서이 cmdlet을 사용 하려면 관리자 권한으로 실행 옵션을 사용 하 여 Windows PowerShell을 시작 합니다.

이벤트, 이벤트 구독 및 이벤트 큐는 현재 세션에만 있습니다. 현재 세션을 닫으면 이벤트 큐가 삭제되고 이벤트 구독이 취소됩니다.

## 관련 링크
