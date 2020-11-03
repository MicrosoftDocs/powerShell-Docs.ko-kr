---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/limit-eventlog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Limit-EventLog
ms.openlocfilehash: 3ec3214103dc6151e148f7482b0be8b821871e3c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93214665"
---
# Limit-EventLog

## 개요
이벤트 로그의 크기와 로그 항목의 보관 기간을 제한하는 이벤트 로그 속성을 설정합니다.

## SYNTAX

```
Limit-EventLog [-LogName] <String[]> [-ComputerName <String[]>] [-RetentionDays <Int32>]
 [-OverflowAction <OverflowAction>] [-MaximumSize <Int64>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명
**Limit EventLog** cmdlet은 클래식 이벤트 로그의 최대 크기, 각 이벤트를 보존 해야 하는 기간 및 로그가 최대 크기에 도달할 때 발생 하는 결과를 설정 합니다.
이 cmdlet을 사용하여 로컬 또는 원격 컴퓨터의 이벤트 로그를 제한할 수 있습니다.

EventLog 명사를 포함하는 cmdlet(EventLog cmdlet)은 클래식 이벤트 로그에서만 작동합니다.
Windows Vista 이상에서 Windows 이벤트 로그 기술을 사용하는 로그의 이벤트를 가져오려면 Get-WinEvent를 사용합니다.

## 예제

### 예제 1: 이벤트 로그 크기 늘리기

```
PS C:\> Limit-EventLog -LogName "Windows PowerShell" -MaximumSize 20KB
```

이 명령은 로컬 컴퓨터에 있는 Windows PowerShell 이벤트 로그의 최대 크기를 20480바이트(20KB)로 늘립니다.

### 예 2: 지정 된 기간 동안 이벤트 로그 유지

```
PS C:\> Limit-EventLog -LogName Security -ComputerName "Server01", "Server02" -RetentionDays 7
```

이 명령은 Server01 및 Server02 컴퓨터의 보안 로그에 있는 이벤트를 7일 이상 보관하도록 합니다.

### 예 3: 모든 이벤트 로그의 오버플로 작업 변경

```
PS C:\> $Logs = Get-EventLog -List | ForEach {$_.log}
PS C:\> Limit-EventLog -OverflowAction OverwriteOlder -LogName $Logs
PS C:\> Get-EventLog -List

Max(K) Retain OverflowAction     Entries  Log
------ ------ --------------     -------  ---
15,168      0 OverwriteOlder       3,412  Application
512         0 OverwriteOlder           0  DFS Replication
512         0 OverwriteOlder          17  DxStudio
10,240      7 OverwriteOlder           0  HardwareEvents
512         0 OverwriteOlder           0  Internet Explorer
512         0 OverwriteOlder           0  Key Management Service
16,384      0 OverwriteOlder           4  ODiag
16,384      0 OverwriteOlder         389  OSession Security
15,168      0 OverwriteOlder      19,360  System
15,360      0 OverwriteOlder      15,828  Windows PowerShell
```

이 예에서는 로컬 컴퓨터에 있는 모든 이벤트 로그의 오버플로 작업을 OverwriteOlder로 변경 합니다.

첫 번째 명령은 로컬 컴퓨터에 있는 모든 로그의 로그 이름을 가져옵니다.
두 번째 명령은 오버플로 작업을 설정합니다.
세 번째 명령은 결과를 표시합니다.

## PARAMETERS

### -ComputerName
원격 컴퓨터를 지정 합니다.
기본값은 로컬 컴퓨터입니다.

원격 컴퓨터의 NetBIOS 이름, IP (인터넷 프로토콜) 주소 또는 FQDN (정규화 된 도메인 이름)을 입력 합니다.
로컬 컴퓨터를 지정 하려면 컴퓨터 이름, 점 (.) 또는 localhost를 입력 합니다.

이 매개 변수는 Windows PowerShell 원격 기능을 사용하지 않습니다.
원격 명령을 실행 하도록 컴퓨터를 구성 하지 않은 경우에도 **Limit 이벤트 로그** 의 *ComputerName* 매개 변수를 사용할 수 있습니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LogName
이벤트 로그를 지정합니다.
하나 이상 이벤트 로그의 로그 이름(Log 표시 이름이 아닌 Log 속성의 값)을 쉼표로 구분하여 입력합니다.
와일드카드 문자는 사용할 수 없습니다.
이 매개 변수는 필수적 요소입니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: LN

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaximumSize
이벤트 로그의 최대 크기를 바이트 단위로 지정합니다.
64KB에서 4GB 사이의 값을 입력합니다.
64KB(65536)로 나눌 수 있는 값이어야 합니다.

이 매개 변수는 클래식 이벤트 로그를 나타내는 **system.web. EventLog** 개체의 **maximumkilobytes** 속성 값을 지정 합니다.

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -OverflowAction
이벤트 로그가 최대 크기에 도달할 경우 수행할 작업을 지정합니다.

이 매개 변수에 허용되는 값은 다음과 같습니다.

- DoNotOverwrite: 기존 항목은 유지 되 고 새 항목은 삭제 됩니다.
- OverwriteAsNeeded: 각각의 새 항목이 가장 오래 된 항목을 덮어씁니다.
- OverwriteOlder: 새 이벤트는 새 **이벤트는이 속성에** 지정 된 값 보다 오래 된 이벤트를 덮어씁니다. 이 **속성 값에 지정 된 것** 보다 오래 된 이벤트가 없는 경우 새 이벤트가 삭제 됩니다.

이 매개 변수는 클래식 이벤트 로그를 나타내는 **OverflowAction** 개체 **의** 속성 값을 지정 합니다.

```yaml
Type: System.Diagnostics.OverflowAction
Parameter Sets: (All)
Aliases: OFA
Accepted values: OverwriteOlder, OverwriteAsNeeded, DoNotOverwrite

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -보존 기간 (일)
이벤트 로그에서 이벤트를 유지해야 할 최소 일수를 지정합니다.

이 매개 변수는 클래식 이벤트 로그를 나타내는 **system.object** **속성의 값을 지정** 합니다.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: MRD

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm
cmdlet을 실행하기 전에 확인을 요청합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf
cmdlet을 실행할 경우 발생하는 일을 표시합니다.
cmdlet은 실행되지 않습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### 없음
이 cmdlet에 입력을 파이프할 수 없습니다.

## 출력

### 없음
이 cmdlet은 어떠한 출력도 생성하지 않습니다.

## 참고

* Windows Vista 이상 버전에서이 cmdlet을 사용 하려면 관리자 권한으로 실행 옵션을 사용 하 여 Windows PowerShell을 엽니다.

  이 cmdlet은 클래식 이벤트 로그를 나타내는 **system.web** 이벤트 로그 개체의 속성을 변경 합니다.
이벤트 로그 속성의 현재 설정을 보려면을 입력 `Get-EventLog -List` 합니다.

*

## 관련 링크

[Clear-EventLog](Clear-EventLog.md)

[Get-EventLog](Get-EventLog.md)

[Limit-EventLog](Limit-EventLog.md)

[New-EventLog](New-EventLog.md)

[Remove-EventLog](Remove-EventLog.md)

[Show-EventLog](Show-EventLog.md)

[Write-EventLog](Write-EventLog.md)
