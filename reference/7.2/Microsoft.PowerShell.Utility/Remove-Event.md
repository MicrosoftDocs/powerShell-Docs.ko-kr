---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/remove-event?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Event
ms.openlocfilehash: 3193de9020f2f54795bde9d5cce1bb86c4431ef9
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603253"
---
# Remove-Event

## 개요
이벤트 큐에서 이벤트를 삭제합니다.

## SYNTAX

### BySource (기본값)

```
Remove-Event [-SourceIdentifier] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByIdentifier

```
Remove-Event [-EventIdentifier] <Int32> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명

`Remove-Event`Cmdlet은 현재 세션의 이벤트 큐에서 이벤트를 삭제 합니다.

이 cmdlet은 현재 큐에 있는 이벤트만 삭제합니다. 이벤트 등록을 취소 하거나 구독을 취소 하려면 `Unregister-Event` cmdlet을 사용 합니다.

## 예제

### 예제 1: 소스 식별자로 이벤트 제거

```
PS C:\> Remove-Event -SourceIdentifier "ProcessStarted"
```

이 명령은 이벤트 큐에서 시작 된 프로세스의 원본 식별자를 사용 하 여 이벤트를 삭제 합니다.

### 예제 2: 이벤트 식별자로 이벤트 제거

```
PS C:\> Remove-Event -EventIdentifier 30
```

이 명령은 이벤트 ID가 30인 이벤트를 이벤트 큐에서 삭제합니다.

### 예제 3: 모든 이벤트 제거

```
PS C:\> Get-Event | Remove-Event
```

이 명령은 이벤트 큐에서 모든 이벤트를 삭제합니다.

## PARAMETERS

### -EventIdentifier

Cmdlet이 삭제 하는 이벤트 식별자를 지정 합니다. **EventIdentifier** 또는 **SourceIdentifier** 매개 변수는 모든 명령에 필요 합니다.

```yaml
Type: System.Int32
Parameter Sets: ByIdentifier
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -SourceIdentifier

이 cmdlet이 이벤트를 삭제할 원본 식별자를 지정 합니다. 와일드카드는 사용할 수 없습니다. **EventIdentifier** 또는 **SourceIdentifier** 매개 변수는 모든 명령에 필요 합니다.

```yaml
Type: System.String
Parameter Sets: BySource
Aliases:

Required: True
Position: 0
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

cmdlet을 실행할 경우 발생하는 일을 표시합니다. cmdlet은 실행되지 않습니다.

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

### PSEventArgs.

에서로 이벤트를 파이프 할 수 있습니다 `Get-Event` `Remove-Event` .

## 출력

### 없음

이 cmdlet에서 어떠한 출력도 생성되지 않습니다.

## 참고

Linux 또는 macOS 플랫폼에서 사용할 수 있는 이벤트 원본이 없습니다.

이벤트, 이벤트 구독 및 이벤트 큐는 현재 세션에만 있습니다. 현재 세션을 닫으면 이벤트 큐가 삭제되고 이벤트 구독이 취소됩니다.

## 관련 링크

[Get-Event](Get-Event.md)

[New-Event](New-Event.md)

[Register-EngineEvent](Register-EngineEvent.md)

[Register-ObjectEvent](Register-ObjectEvent.md)

[Remove-Event](Remove-Event.md)

[Unregister-Event](Unregister-Event.md)

[Wait-Event](Wait-Event.md)
