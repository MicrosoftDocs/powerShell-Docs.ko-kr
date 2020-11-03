---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/unregister-event?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unregister-Event
ms.openlocfilehash: 748ef22203f59090be6f5491ea76b50d54930a95
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93217562"
---
# Unregister-Event

## 개요
이벤트 구독을 취소합니다.

## SYNTAX

### BySource (기본값)

```
Unregister-Event [-SourceIdentifier] <String> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ById

```
Unregister-Event [-SubscriptionId] <Int32> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명
Register-engineevent, Register-ObjectEvent 또는 Register-WmiEvent cmdlet을 사용 하 여 생성 된 이벤트 등록을 취소 **하는 이벤트를 취소** 합니다.

이벤트 구독을 취소하면 이벤트 구독자가 세션에서 삭제되고 가입된 이벤트는 더 이상 이벤트 큐에 추가되지 않습니다.
New-Event cmdlet을 사용하여 만든 이벤트에 대한 가입을 취소하면 새 이벤트도 세션에서 삭제됩니다.

**등록 취소** 이벤트는 이벤트 큐에서 이벤트를 삭제 하지 않습니다.
이벤트를 삭제하려면 Remove-Event cmdlet을 사용합니다.

## 예제

### 예제 1: 소스 식별자로 이벤트 구독 취소

```
PS C:\> Unregister-Event -SourceIdentifier "ProcessStarted"
```

이 명령은 ProcessStarted의 원본 식별자를 가진 이벤트 구독을 취소 합니다.

이벤트의 원본 식별자를 찾으려면 Get-Event cmdlet을 사용합니다.
이벤트 구독의 원본 식별자를 찾으려면 **Get EventSubscriber** cmdlet을 사용 합니다.

### 예제 2: 구독 식별자로 이벤트 구독 취소

```
PS C:\> Unregister-Event -SubscriptionId 2
```

이 명령은 가입 식별자가 2인 이벤트 구독을 취소합니다.

이벤트 구독의 구독 식별자를 찾으려면 **Get EventSubscriber** cmdlet을 사용 합니다.

### 예 3: 모든 이벤트 구독 취소

```
PS C:\> Get-EventSubscriber -Force | Unregister-Event -Force
```

이 명령은 세션에서 모든 이벤트 구독을 취소합니다.

이 명령은 이벤트 등록 cmdlet의 *supportevent* 매개 변수를 사용 하 여 숨겨진 구독자를 포함 하 여 세션의 모든 이벤트 구독자 개체 **를 가져오는 데** 사용 됩니다.

파이프라인 연산자 (|)를 사용 하 여 구독자 개체를 **등록 취소** 로 보내면이 이벤트는 세션에서 해당 개체를 삭제 합니다.
작업을 완료 하려면 **이벤트 등록 취소** 에도 *Force* 매개 변수가 필요 합니다.

## PARAMETERS

### -Force
**Register-wmievent** 및 **Register-engineevent** 의 *supportevent* 매개 **변수를 사용** 하 여 숨겨진 구독을 포함 하 여 모든 이벤트 구독을 취소 합니다.

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

### -SourceIdentifier
이 cmdlet이 이벤트 구독을 취소 하는 원본 식별자를 지정 합니다.

*SourceIdentifier* 또는 *SubscriptionId* 매개 변수는 모든 명령에 포함 되어야 합니다.

```yaml
Type: System.String
Parameter Sets: BySource
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -SubscriptionId
이 cmdlet이 이벤트 구독을 취소 하는 원본 식별자 ID를 지정 합니다.

*SourceIdentifier* 또는 *SubscriptionId* 매개 변수는 모든 명령에 포함 되어야 합니다.

```yaml
Type: System.Int32
Parameter Sets: ById
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
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

### PSEventSubscriber.
Get-EventSubscriber 출력을 **이벤트 등록 취소** 로 파이프 할 수 있습니다.

## 출력

### 없음
이 cmdlet은 어떠한 출력도 반환되지 않습니다.

## 참고

* 이벤트, 이벤트 구독 및 이벤트 큐는 현재 세션에만 있습니다. 현재 세션을 닫으면 이벤트 큐가 삭제되고 이벤트 구독이 취소됩니다.

  **Register-engineevent** cmdlet을 사용 하 여 이벤트를 구독 하지 않은 경우 **이벤트 등록 취소** 는 New-Event cmdlet을 사용 하 여 만든 이벤트를 삭제할 수 없습니다.
세션에서 사용자 지정 이벤트를 삭제하려면 프로그래밍 방식으로 제거하거나 세션을 닫아야 합니다.

*

## 관련 링크

[Get-Event](Get-Event.md)

[Get-EventSubscriber](Get-EventSubscriber.md)

[New-Event](New-Event.md)

[Register-EngineEvent](Register-EngineEvent.md)

[Register-ObjectEvent](Register-ObjectEvent.md)

[Remove-Event](Remove-Event.md)

[Unregister-Event](Unregister-Event.md)

[Wait-Event](Wait-Event.md)

