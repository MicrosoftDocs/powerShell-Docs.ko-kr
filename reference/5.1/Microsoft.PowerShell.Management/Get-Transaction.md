---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-transaction?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Transaction
ms.openlocfilehash: bb8e9e1f204c67207f31613181f856d3bcaf8dc3
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/02/2020
ms.locfileid: "93209024"
---
# Get-Transaction

## 개요
현재(활성) 트랜잭션을 가져옵니다.

## SYNTAX

```
Get-Transaction [<CommonParameters>]
```

## 설명
**Get Transaction** cmdlet은 세션의 현재 트랜잭션을 나타내는 개체를 가져옵니다.

한 번에 하나의 트랜잭션만 활성화되기 때문에 이 cmdlet은 개체를 하나만 반환합니다.
독립 트랜잭션을 하나 이상 시작 하는 경우 (즉, 시작 트랜잭션의 독립 매개 변수를 사용 하 여) 가장 최근에 시작 된 트랜잭션이 활성 상태가 되 고이 트랜잭션이 **Get transaction** 이 반환 됩니다.

모든 활성 트랜잭션이 롤백되고 커밋되거나 커밋되면이 cmdlet은 세션에서 가장 최근에 활성화 된 트랜잭션을 표시 합니다.

이 cmdlet은 Windows PowerShell의 트랜잭션 기능을 지 원하는 cmdlet 집합 중 하나입니다.
자세한 내용은 about_Transactions를 참조하세요.

## 예제

### 예 1: 현재 트랜잭션 가져오기

```
PS C:\> Start-Transaction
PS C:\> Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                1                 Active
```

이 명령은 Get-Transaction cmdlet을 사용하여 현재 트랜잭션을 가져옵니다.

### 예 2: 트랜잭션 개체의 속성 및 메서드 표시

```
PS C:\> Get-Transaction | Get-Member

Name               MemberType Definition
----               ---------- ----------
Dispose            Method     System.Void Dispose(), System.Void Dispose(Boolean disposing)
Equals             Method     System.Boolean Equals(Object obj)
GetHashCode        Method     System.Int32 GetHashCode()
GetType            Method     System.Type GetType()
ToString           Method     System.String ToString()
IsCommitted        Property   System.Boolean IsCommitted {get;}
IsRolledBack       Property   System.Boolean IsRolledBack {get;}
RollbackPreference Property   System.Management.Automation.RollbackSeverity RollbackPreference {get;}
SubscriberCount    Property   System.Int32 SubscriberCount {get;set;}
```

이 명령은 Get-Member cmdlet을 사용하여 트랜잭션 개체의 속성과 메서드를 보여 줍니다.

### 예제 3: 롤백된 트랜잭션의 속성 값 표시

```
PS C:\> cd hklm:\software
HKLM:\SOFTWARE> Start-Transaction
HKLM:\SOFTWARE> New-Item MyCompany -UseTransaction
HKLM:\SOFTWARE> Undo-Transaction
HKLM:\SOFTWARE> Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   ----------
Error                0                 RolledBack
```

이 명령은 롤백된 트랜잭션에 대한 트랜잭션 개체의 속성 값을 보여 줍니다.

### 예제 4: 커밋된 트랜잭션의 속성 값 표시

```
PS C:\> cd hklm:\software
HKLM:\SOFTWARE> Start-Transaction
HKLM:\SOFTWARE> New-Item MyCompany -UseTransaction
HKLM:\SOFTWARE> Complete-Transaction
HKLM:\SOFTWARE> Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   ---------
Error                1                 Committed
```

이 명령은 커밋된 트랜잭션에 대한 트랜잭션 개체의 속성 값을 보여 줍니다.

### 예 5: 다른 작업이 진행 되는 동안 트랜잭션 시작

```
PS C:\> cd hklm:\software
HKLM:\SOFTWARE> Start-Transaction
HKLM:\SOFTWARE> New-Item MyCompany -UseTransaction
HKLM:\SOFTWARE> Start-Transaction
HKLM:\SOFTWARE> New-Item MyCompany2 -UseTransaction
HKLM:\SOFTWARE> Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                2                 Active

HKLM:\SOFTWARE> Complete-Transaction
HKLM:\SOFTWARE> Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                1                 Active

HKLM:\SOFTWARE> Complete-Transaction
HKLM:\SOFTWARE> Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   ---------
Error                1                 Committed
```

이 예제에서는 다른 트랜잭션이 진행되는 동안 트랜잭션을 시작할 경우 트랜잭션 개체에 미치는 영향을 보여 줍니다.
일반적으로 트랜잭션을 실행하는 스크립트가 함수를 포함하거나 다른 전체 트랜잭션이 포함된 스크립트를 호출하는 경우에 발생합니다.

두 번째 **시작 트랜잭션** 명령에 *독립* 매개 변수가 포함 되어 있지 않으면 **start transaction** 은 새 트랜잭션을 만들지 않습니다.
대신 원본 트랜잭션에 두 번째 구독자를 추가합니다.

첫 번째 **시작 트랜잭션** 명령은 트랜잭션을 시작 합니다.
*UseTransaction* 매개 변수를 사용 하는 New-Item 명령은 트랜잭션의 일부입니다.

두 번째 **시작 트랜잭션** 명령은 구독자를 트랜잭션에 추가 합니다.
다음 New-Item 명령도 트랜잭션의 일부입니다.

첫 번째 **Get transaction** 명령은 다중 구독자 트랜잭션을 표시 합니다.
구독자 개수는 2입니다.

첫 번째 Complete-Transaction 명령은 트랜잭션을 커밋하지 않고 구독자 개수를 1로 줄입니다.

두 번째 **Complete transaction** 명령은 트랜잭션을 커밋합니다.

### 예 6: 다른 작업이 진행 되는 동안 독립 트랜잭션을 시작 합니다.

```
PS C:\>
HKLM:\SOFTWARE> Start-Transaction
HKLM:\SOFTWARE> Get-Transaction

RollbackPreference   SubscriberCount   IsRolledBack   IsCommitted
------------------   ---------------   ------------   -----------
Error                1                 False          False

HKLM:\SOFTWARE> Start-Transaction -Independent
HKLM:\SOFTWARE> Get-Transaction

RollbackPreference   SubscriberCount   IsRolledBack   IsCommitted
------------------   ---------------   ------------   -----------
Error                1                 False          False

HKLM:\SOFTWARE> Complete-Transaction
HKLM:\SOFTWARE> Get-Transaction
HKLM:\SOFTWARE> Complete-Transaction
HKLM:\SOFTWARE> Get-Transaction
```

이 예제에서는 다른 트랜잭션이 진행되는 동안 독립 트랜잭션을 시작할 경우 트랜잭션 개체에 미치는 영향을 보여 줍니다.

첫 번째 **시작 트랜잭션** 명령은 트랜잭션을 시작 합니다.
*UseTransaction* 매개 변수를 사용 하는 **새 항목** 명령은 트랜잭션의 일부입니다.

두 번째 **시작 트랜잭션** 명령은 구독자를 트랜잭션에 추가 합니다.
다음 **새 항목** 명령은 트랜잭션의 일부 이기도 합니다.

첫 번째 **Get transaction** 명령은 다중 구독자 트랜잭션을 표시 합니다.
구독자 개수는 2입니다.

**Complete transaction** 명령은 구독자 수를 1로 줄인 후에는 트랜잭션을 커밋하지 않습니다.

두 번째 **Complete transaction** 명령은 트랜잭션을 커밋합니다.

## PARAMETERS

### CommonParameters
이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### 없음
이 cmdlet에 개체를 파이프할 수 없습니다.

## 출력

### PSTransaction.
이 cmdlet은 현재 트랜잭션을 나타내는 개체를 반환 합니다.

## 참고

## 관련 링크

[Complete-Transaction](Complete-Transaction.md)

[Start-Transaction](Start-Transaction.md)

[Undo-Transaction](Undo-Transaction.md)

[Use-Transaction](Use-Transaction.md)

[New-Item](New-Item.md)
