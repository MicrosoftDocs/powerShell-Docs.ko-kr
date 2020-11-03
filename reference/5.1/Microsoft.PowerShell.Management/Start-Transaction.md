---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/start-transaction?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Transaction
ms.openlocfilehash: 53be131f45f15e5d2053b183040dc7b3dca4a14c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93214393"
---
# Start-Transaction

## 개요
트랜잭션을 시작합니다.

## SYNTAX

```
Start-Transaction [-Timeout <Int32>] [-Independent] [-RollbackPreference <RollbackSeverity>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## 설명
**시작-트랜잭션** cmdlet은 하나의 단위로 관리 되는 일련의 명령인 트랜잭션을 시작 합니다.
트랜잭션을 완료 하거나 커밋할 수 있습니다.
또는 트랜잭션을 통해 변경 된 모든 데이터가 원래 상태로 복원 되도록 완전히 실행 취소 하거나 롤백할 수 있습니다.
트랜잭션의 명령은 하나의 단위로 관리되므로 모든 명령이 커밋되거나 롤백됩니다.

기본적으로 트랜잭션의 명령에서 오류가 생성 되 면 트랜잭션이 자동으로 롤백됩니다.
*RollbackPreference* 매개 변수를 사용 하 여이 동작을 변경할 수 있습니다.

트랜잭션에 사용된 cmdlet은 트랜잭션을 지원해야 합니다.
트랜잭션을 지 원하는 cmdlet에는 *UseTransaction* 매개 변수가 있습니다.
공급자에서 트랜잭션을 수행하려면 공급자가 트랜잭션을 지원해야 합니다.
Windows Vista 이상 버전의 windows PowerShell 레지스트리 공급자는 트랜잭션을 지원 합니다.
**TransactedString** 클래스를 사용 하 여 windows PowerShell을 지 원하는 모든 버전의 windows 시스템에서 트랜잭션에 식을 포함할 수도 있습니다.
다른 Windows PowerShell 공급자도 트랜잭션을 지원할 수 있습니다.

한 번에 하나의 트랜잭션만 활성화할 수 있습니다.
트랜잭션이 진행 되는 동안 새 독립 트랜잭션을 시작 하면 새 트랜잭션이 활성 트랜잭션이 되며 원본 트랜잭션을 변경 하기 전에 새 트랜잭션을 커밋하거나 롤백해야 합니다 (예를 들어,

**Start-Transaction** Cmdlet은 Windows PowerShell의 트랜잭션 기능을 지 원하는 cmdlet 집합 중 하나입니다.
자세한 내용은 about_Transactions를 참조하세요.

## 예제

### 예제 1: 트랜잭션 시작 및 롤백

```
PS C:\> cd hkcu:\software
PS HKCU:\software> Start-Transaction
PS HKCU:\software> New-Item "ContosoCompany" -UseTransaction
PS HKCU:\software> New-ItemProperty "ContosoCompany" -Name "MyKey" -Value 123 -UseTransaction
PS HKCU:\software> Undo-Transaction
```

이들 명령은 트랜잭션을 시작한 후 롤백합니다.
트랜잭션이 롤백되므로 레지스트리가 변경되지 않습니다.

### 예 2: 트랜잭션 시작 및 완료

```
PS C:\> cd hkcu:\software
PS HKCU:\software> Start-Transaction
PS HKCU:\software> New-Item "ContosoCompany" -UseTransaction
PS HKCU:\software> New-ItemProperty "ContosoCompany" -Name "MyKey" -Value 123 -UseTransaction
PS HKCU:\software> Complete-Transaction
```

이들 명령은 전체 트랜잭션을 시작한 후 완료합니다.
**Complete Transaction** 명령을 사용할 때까지 레지스트리가 변경 되지 않습니다.

### 예제 3: 다른 롤백 기본 설정 사용

```
PS C:\> cd HKCU:\software
PS HKCU:\software> Start-Transaction
PS HKCU:\software> New-Item -Path "NoPath" -Name "ContosoCompany" -UseTransaction
PS HKCU:\software> New-Item -Path . -Name "ContosoCompany" -UseTransaction
PS HKCU:\software> Start-Transaction -RollbackPreference never
PS HKCU:\software> New-Item -Path "NoPath" -Name "ContosoCompany" -UseTransaction
PS HKCU:\software> New-Item -Path . -Name "ContosoCompany" -UseTransaction

# Start-Transaction (-rollbackpreference error)

PS HKCU:\software> Start-Transaction
PS HKCU:\software> New-Item -Path "NoPath" -Name "ContosoCompany" -UseTransaction
New-Item : The registry key at the specified path does not exist.
At line:1 char:9
+ new-item <<<<  -Path NoPath -Name ContosoCompany -UseTransaction

PS HKCU:\software> New-Item -Path . -Name "Contoso" -UseTransaction

New-Item : Cannot use transaction. The transaction has been rolled back or has timed out.
At line:1 char:9
+ new-item <<<<  -Path . -Name ContosoCompany -UseTransaction

# Start-Transaction (-rollbackpreference never)

PS HKCU:\software> Start-Transaction -RollbackPreference never
PS HKCU:\software> New-Item -Path "NoPath" -Name "ContosoCompany" -UseTransaction

New-Item : The registry key at the specified path does not exist.
At line:1 char:9
+ new-item <<<<  -Path NoPath -Name "ContosoCompany" -UseTransaction
PS HKCU:\software> New-Item -Path . -Name "ContosoCompany" -UseTransaction

Hive: HKEY_CURRENT_USER\Software
SKC  VC Name                           Property
---  -- ----                           --------
0   0 ContosoCompany                 {}
PS HKCU:\Software> Complete-Transaction

# Succeeds
```

이 예에서는 *RollbackPreference* 매개 변수 값을 변경 하는 경우의 효과를 보여 줍니다.

첫 번째 명령 집합에서 **Start Transaction** 은 *RollbackPreference* 를 사용 하지 않습니다.
따라서 기본값 (오류)이 사용 됩니다.
트랜잭션 명령에 오류가 발생 하는 경우, 즉 지정 된 경로가 존재 하지 않으면 트랜잭션이 자동으로 롤백됩니다.

두 번째 명령 집합에서 **시작 트랜잭션은** 값이 Never 인 *RollbackPreference* 을 사용 합니다.
그 결과 트랜잭션 명령에 오류가 발생해도 트랜잭션이 여전히 활성 상태가 되므로 성공적으로 완료할 수 있습니다.

대부분의 트랜잭션은 오류 없이 수행 해야 하므로 일반적으로 *RollbackPreference* 의 기본값을 사용 하는 것이 좋습니다.

### 예 4: 트랜잭션이 진행 되는 동안이 cmdlet 사용

```
PS C:\> cd HKCU:\software
PS HKCU:\software> Start-Transaction
PS HKCU:\software> New-Item "ContosoCompany" -UseTransaction
PS HKCU:\software> Start-Transaction
PS HKCU:\software> Get-Transaction
PS HKCU:\software> New-Item "ContosoCompany2" -UseTransaction
PS HKCU:\software> Complete-Transaction
PS HKCU:\software> Complete-Transaction
PS HKCU:\Software> Get-Transaction
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                2                 Active
```

이 예에서는 트랜잭션이 진행 되는 동안 **시작 트랜잭션** 사용의 영향을 보여 줍니다.
효과는 진행 중인 트랜잭션에 가입하는 것과 매우 유사합니다.

이는 단순화 된 명령 이지만이 시나리오는 트랜잭션이 전체 트랜잭션을 포함 하는 스크립트를 실행 해야 하는 경우에 자주 발생 합니다.

첫 번째 **시작 트랜잭션** 명령은 트랜잭션을 시작 합니다.
첫 번째 **새 항목** 명령은 트랜잭션의 일부입니다.

두 번째 **Start transaction** 명령은 트랜잭션에 새 구독자를 추가 합니다.
이제 **Get transaction** 명령은 구독자 수가 2 인 트랜잭션을 반환 합니다.
두 번째 **새 항목** 명령은 동일한 트랜잭션의 일부입니다.

전체 트랜잭션이 완료 될 때까지 레지스트리가 변경 되지 않습니다.
트랜잭션을 완료 하려면 각 구독자에 대해 하나씩 두 개의 **Complete transaction** 명령을 입력 해야 합니다.
언제 든 지 트랜잭션을 롤백하려면 두 구독자에 대해 모든 트랜잭션이 롤백됩니다.

### 예 5: 진행 중인 독립 트랜잭션 시작

```
PS C:\> cd HKCU:\software
PS HKCU:\software> Start-Transaction
PS HKCU:\software> New-Item "ContosoCompany" -UseTransaction
PS HKCU:\software> Start-Transaction -Independent
PS HKCU:\software> Get-Transaction
PS HKCU:\software> Undo-Transaction
PS HKCU:\software> New-ItemProperty -Path "ContosoCompany" -Name "MyKey" -Value 123 -UseTransaction
PS HKCU:\software> Complete-Transaction
PS HKCU:\software> dir contoso*
PS HKCU:\Software> Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                1                 Active
PS HKCU:\software> Undo-Transaction
PS HKCU:\software> New-ItemProperty -Path "ContosoCompany" -Name "MyKey" -Value 123 -UseTransaction
MyKey
-----
123
PS HKCU:\software> Complete-Transaction
PS HKCU:\software> dir contoso*
Hive: HKEY_CURRENT_USER\Software
SKC  VC Name                           Property
---  -- ----                           --------
0   1 MyCompany                      {MyKey}
```

이 예에서는 다른 트랜잭션이 진행 되는 동안 트랜잭션을 시작 하기 위해 **Start transaction** 의 *독립적인* 매개 변수를 사용 하는 경우의 결과를 보여 줍니다.
이 경우 원본 트랜잭션에 영향을 주지 않고 새 트랜잭션이 롤백됩니다.

트랜잭션은 논리적으로 독립적이지만 한 번의 한 개의 트랜잭션만 활성 상태일 수 있으므로 원본 트랜잭션 작업을 다시 시작하기 전에 최신의 트랜잭션을 롤백하거나 커밋해야 합니다.

첫 번째 명령은 트랜잭션을 시작합니다.
**새 항목** 명령은 첫 번째 트랜잭션의 일부입니다.

두 번째 명령 집합에서 **시작 트랜잭션** 명령은 *독립* 매개 변수를 사용 합니다.
다음에 나오는 **Get transaction** 명령은 활성 트랜잭션에 대 한 트랜잭션 개체 (최신 트랜잭션 개체)를 보여 줍니다.
구독자 수는 트랜잭션과 관련이 없다는 것을 보여 주는 1과 같습니다.

**실행 취소-트랜잭션** 명령을 사용 하 여 활성 트랜잭션을 롤백하는 경우 원본 트랜잭션이 다시 활성화 됩니다.

원래 트랜잭션의 일부인 **get-itemproperty** 명령은 오류 없이 완료 되며 원래 트랜잭션은 **Complete transaction** 명령을 사용 하 여 완료할 수 있습니다.
그 결과 레지스트리가 변경됩니다.

### 예 6: 트랜잭션의 일부가 아닌 명령 실행

```
PS C:\> cd hkcu:\software
PS HKCU:\software> Start-Transaction
PS HKCU:\software> New-Item "ContosoCompany1" -UseTransaction
PS HKCU:\software> New-Item "ContosoCompany2"
PS HKCU:\software> New-Item "ContosoCompany3" -UseTransaction
PS HKCU:\software> dir contoso*
PS HKCU:\software> Complete-Transaction
PS HKCU:\software> dir contoso*
PS HKCU:\Software> dir contoso*

Hive: HKEY_CURRENT_USER\Software
SKC  VC Name                           Property
---  -- ----                           --------
0   0 ContosoCompany2                {}

PS HKCU:\Software> Complete-Transaction
PS HKCU:\Software> dir contoso*

Hive: HKEY_CURRENT_USER\Software
SKC  VC Name                           Property
---  -- ----                           --------
0   0 ContosoCompany1                     {}
0   0 ContosoCompany2                     {}
0   0 ContosoCompany3                     {}
```

이 예제에서는 트랜잭션 진행 중 전송된 명령이 트랜잭션에 포함되는지 여부를 보여 줍니다.
*UseTransaction* 매개 변수를 사용 하는 명령만 트랜잭션의 일부입니다.

첫 번째 및 세 번째 **새 항목** 명령은 *UseTransaction* 매개 변수를 사용 합니다.
트랜잭션의 일부입니다.
두 번째 **새 항목** 명령은 *UseTransaction* 매개 변수를 사용 하지 않으므로 트랜잭션의 일부가 아닙니다.

첫 번째 dir 명령은 효과를 표시 합니다.
두 번째 **새 항목** 명령은 즉시 완료 되지만 첫 번째 및 세 번째 **새 항목** 명령은 트랜잭션이 커밋될 때까지 유효 하지 않습니다.

**Complete transaction** 명령은 트랜잭션을 커밋합니다.
그 결과 두 번째 dir 명령은 모든 새 항목이 레지스트리에 추가 된 것을 보여 줍니다.

### 예 7: 지정 된 시간 내에 완료 되지 않은 트랜잭션 롤백

```
PS C:\> Start-Transaction -Timeout 2

# Wait two minutes...

PS C:\> Get-Transaction
PS C:\> New-Item HKCU:\Software\ContosoCompany -UseTransaction
PS C:\> Start-Transaction -Timeout 2

# Wait two minutes...

PS C:\> > Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   -----------
Error                1                 RolledBack

PS C:\> New-Item HKCU:\Software\ContosoCompany -UseTransaction

New-Item : Cannot use transaction. The transaction has been rolled back or has timed out.
At line:1 char:9
+ new-item <<<<  MyCompany -UseTransaction
```

이 명령은 **Start transaction** 의 *Timeout* 매개 변수를 사용 하 여 2 분 이내에 완료 해야 하는 트랜잭션을 시작 합니다.
제한 시간이 만료 되 면 트랜잭션이 완료 되지 않으면 자동으로 롤백됩니다.

제한 시간이 만료 되 면 알림이 표시 되지 않지만 트랜잭션 개체의 **Status** 속성은 RolledBack로 설정 되 고 *UseTransaction* 매개 변수를 사용 하는 명령은 실패 합니다.

## PARAMETERS

### -독립적
이 cmdlet이 진행 중인 트랜잭션과 독립적인 트랜잭션을 시작 함을 나타냅니다.
기본적으로 다른 트랜잭션이 진행 되는 동안에는 **Start transaction** 을 사용 하는 경우 진행 중인 트랜잭션에 새 구독자가 추가 됩니다.
이 매개 변수는 세션에서 트랜잭션이 이미 진행 중인 경우에만 적용됩니다.

기본적으로 트랜잭션이 진행 되는 동안 **시작-트랜잭션을** 사용 하면 기존 트랜잭션 개체가 다시 사용 되 고 구독자 수가 증가 합니다.
결과는 원본 트랜잭션 가입과 매우 유사합니다.
Undo-Transaction 명령은 전체 트랜잭션을 롤백합니다.
트랜잭션을 완료하려면 각 가입자에 대해 Complete-Transaction 명령을 입력해야 합니다.
동시에 진행 중인 트랜잭션은 거의 관련되어 있으므로 대부분의 경우 기본값을 사용하면 됩니다.

*독립* 매개 변수를 지정 하는 경우이 cmdlet은 원본 트랜잭션에 영향을 주지 않고 완료 하거나 취소할 수 있는 새 트랜잭션을 만듭니다.
그러나 한 번의 한 개의 트랜잭션만 활성 상태일 수 있으므로 새 트랜잭션을 완료하거나 롤백해야만 원본 트랜잭션을 다시 사용할 수 있습니다.

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

### -RollbackPreference
트랜잭션이 자동으로 롤백되는 조건을 지정합니다.
이 매개 변수에 허용되는 값은 다음과 같습니다.

- 오류.
종료되는 오류 또는 종료되지 않는 오류가 발생하면 트랜잭션이 자동으로 롤백됩니다.
- TerminatingError.
종료되는 오류가 발생하면 트랜잭션이 자동으로 롤백됩니다.
- 불가능
트랜잭션이 자동으로 롤백되지 않습니다.

기본값은 Error입니다.

```yaml
Type: System.Management.Automation.RollbackSeverity
Parameter Sets: (All)
Aliases:
Accepted values: Error, TerminatingError, Never

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -시간 제한
트랜잭션이 활성 상태일 수 있는 최대 시간(분)을 지정합니다.
제한 시간이 만료되면 트랜잭션이 자동으로 롤백됩니다.

기본적으로 명령줄에서 시작된 트랜잭션에 대한 제한 시간은 없습니다.
트랜잭션을 스크립트로 시작하면 기본 제한 시간은 30분입니다.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: TimeoutMins

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

## 관련 링크

[Complete-Transaction](Complete-Transaction.md)

[Get-Transaction](Get-Transaction.md)

[Undo-Transaction](Undo-Transaction.md)

[Use-Transaction](Use-Transaction.md)
