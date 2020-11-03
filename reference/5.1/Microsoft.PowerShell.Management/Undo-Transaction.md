---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/undo-transaction?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Undo-Transaction
ms.openlocfilehash: 1acb06ea7b05a2127b04a22c4c51b92cd68056f2
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93214338"
---
# Undo-Transaction

## 개요
활성 트랜잭션을 롤백합니다.

## SYNTAX

```
Undo-Transaction [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명
**실행 취소-트랜잭션** cmdlet은 활성 트랜잭션을 롤백합니다.
트랜잭션을 롤백하면 트랜잭션의 명령에의 한 변경 내용이 취소 되 고 데이터가 원래 형식으로 복원 됩니다.

트랜잭션에 여러 구독자가 포함 된 경우 **실행 취소 트랜잭션** 명령은 모든 구독자에 대 한 전체 트랜잭션을 롤백합니다.

기본적으로 트랜잭션의 명령에서 오류가 생성될 경우 트랜잭션은 자동으로 롤백됩니다.
그러나 다른 롤백 기본 설정을 사용 하 여 트랜잭션을 시작할 수 있으며이 cmdlet을 사용 하 여 언제 든 지 활성 트랜잭션을 롤백할 수 있습니다.

**실행 취소-트랜잭션** Cmdlet은 Windows PowerShell의 트랜잭션 기능을 지 원하는 cmdlet 집합 중 하나입니다.
자세한 내용은 about_Transactions를 참조하세요.

## 예제

### 예 1: 현재 트랜잭션 롤백

```
PS C:\> Undo-Transaction
```

이 명령은 현재 활성 트랜잭션를 롤백합니다.

### 예제 2: 트랜잭션 시작 및 롤백

```
PS C:\> cd hkcu:\software
PS HKCU:\Software> Start-Transaction
PS HKCU:\Software> New-Item -Path "ContosoCompany" -UseTransaction
PS HKCU:\Software> Undo-Transaction
```

이 예에서는 트랜잭션을 시작한 후 롤백합니다.
따라서 레지스트리가 변경되지 않습니다.

### 예 3: 모든 구독자에 대 한 트랜잭션 롤백

```
PS C:\> cd hkcu:\software
PS HKCU:\Software> Start-Transaction
PS HKCU:\Software> New-Item -Path "ContosoCompany" -UseTransaction
PS HKCU:\Software> Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   -----
Error                1                 Active

PS HKCU:\Software> Start-Transaction
PS HKCU:\Software> Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   -----
Error                2                 Active

PS HKCU:\Software> Undo-Transaction
PS HKCU:\Software> Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   -----
Error                0                 RolledBack
```

이 예에서는 모든 구독자가 트랜잭션을 롤백할 때 모든 구독자에 대해 전체 트랜잭션이 롤백되는 것을 보여 줍니다.

첫 번째 명령은 HKCU:\Software 레지스트리 키의 위치를 변경합니다.

두 번째 명령은 트랜잭션을 시작합니다.

세 번째 명령은 New-Item cmdlet을 사용하여 새 레지스트리 키를 만든 다음
이 명령은 *UseTransaction* 매개 변수를 사용 하 여 트랜잭션에 변경 내용을 포함 합니다.

네 번째 명령은 Get-Transaction cmdlet을 사용하여 활성 트랜잭션을 가져옵니다.
이때 상태는 Active이고 가입자 수는 1입니다.

다섯 번째 명령은 Start-Transaction 명령을 다시 사용합니다.
일반적으로 기본 트랜잭션에 사용 되는 스크립트에 자체의 완전 한 트랜잭션이 포함 되는 경우 다른 트랜잭션이 진행 되는 동안 트랜잭션을 시작 합니다.
이 예제는 단계에서 검사할 수 있도록 대화형으로 수행 됩니다.
다른 트랜잭션이 진행 중인 동안에는 **시작 트랜잭션** 명령을 실행할 때 기존 트랜잭션을 새 구독자로 조인 하면 구독자 수가 증가 합니다.

여섯 번째 명령은 **Get transaction** cmdlet을 사용 하 여 활성 트랜잭션을 가져옵니다.
이제 가입자 수는 2가 됩니다.

일곱 번째 명령은 **실행 취소 트랜잭션을** 사용 하 여 트랜잭션을 롤백합니다.
이 명령은 개체를 반환하지 않습니다.

최종 명령은 활성 (이 경우 가장 최근 활성 트랜잭션)을 가져오는 **Get transaction** 명령입니다.
결과를 보면 트랜잭션이 롤백되고 가입자 수가 0이 되면서 모든 가입자에 대한 트랜잭션이 롤백되는 것을 확인할 수 있습니다.

## PARAMETERS

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
이 cmdlet은 어떠한 출력도 반환되지 않습니다.

## 참고

* 이미 커밋된 트랜잭션은 롤백할 수 없습니다.

  활성 트랜잭션이 아닌 트랜잭션은 롤백할 수 없습니다.
다른 독립 트랜잭션을 롤백하려면 먼저 활성 트랜잭션을 커밋하거나 롤백해야 합니다.

  트랜잭션을 롤백하면 트랜잭션이 종료됩니다.
트랜잭션을 다시 사용하려면 새 트랜잭션을 시작해야 합니다.

## 관련 링크

[Complete-Transaction](Complete-Transaction.md)

[Get-Transaction](Get-Transaction.md)

[Start-Transaction](Start-Transaction.md)

[Use-Transaction](Use-Transaction.md)
