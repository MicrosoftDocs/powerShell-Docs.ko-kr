---
description: PowerShell에서 트랜잭션 작업을 관리 하는 방법을 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_transactions?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Transactions
ms.openlocfilehash: 522e0f727754b0b0153571039f3bf3966d0abf20
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93222481"
---
# <a name="about-transactions"></a>트랜잭션 정보

## <a name="short-description"></a>간단한 설명

PowerShell에서 트랜잭션 작업을 관리 하는 방법을 설명 합니다.

## <a name="long-description"></a>자세한 설명

트랜잭션은 PowerShell 2.0부터 PowerShell에서 지원 됩니다. 이 기능을 사용 하면 트랜잭션을 시작 하 고 트랜잭션에 포함 된 명령을 표시 하며 트랜잭션을 커밋하거나 롤백할 수 있습니다.

## <a name="about-transactions"></a>트랜잭션 정보

PowerShell에서 트랜잭션은 논리적 단위로 관리 되는 하나 이상의 명령 집합입니다. 트랜잭션의 영향을 받는 데이터를 변경 하는 트랜잭션을 완료할 수 있습니다 ("커밋됨"). 또는 트랜잭션이 완전히 취소 ("롤백") 될 수 있으므로 트랜잭션에 의해 영향을 받는 데이터가 변경 되지 않습니다.

트랜잭션의 명령은 하나의 단위로 관리 되기 때문에 모든 명령이 커밋되거나 모든 명령이 롤백됩니다.

트랜잭션은 데이터 처리에서 널리 사용 되며, 특히 데이터베이스 작업 및 금융 트랜잭션에 사용 됩니다. 트랜잭션은 명령 집합에 대 한 최악의 시나리오에서 모두 실패 하는 것은 아니지만 일부 명령이 실패 하는 경우에는 복구 하기 어려운 손상 됨, 거짓 또는 중단 되지 않은 상태에서 시스템을 종료 하는 경우에 가장 자주 사용 됩니다.

## <a name="transaction-cmdlets"></a>트랜잭션 CMDLET

PowerShell에는 트랜잭션 관리를 위해 설계 된 몇 가지 cmdlet이 포함 되어 있습니다.

- Start-Transaction: 새 트랜잭션을 시작 합니다.
- Use-Transaction: 트랜잭션에 명령 또는 식을 추가 합니다. 명령은 트랜잭션 사용 개체를 사용 해야 합니다.
- 실행 취소-트랜잭션에 의해 데이터가 변경 되지 않도록 트랜잭션을 롤백합니다.
- Complete-Transaction: 트랜잭션을 커밋합니다. 트랜잭션의 영향을 받는 데이터가 변경 됩니다.
- Get Transaction: 활성 트랜잭션에 대 한 정보를 가져옵니다.

트랜잭션 cmdlet 목록을 보려면 다음을 입력 하십시오.

```powershell
get-command *transaction
```

Cmdlet에 대 한 자세한 내용을 보려면 다음을 입력 하십시오.

```powershell
get-help use-transaction -detailed
```

## <a name="transaction-enabled-elements"></a>트랜잭션 사용 요소

트랜잭션에 참여 하려면 cmdlet과 공급자 모두 트랜잭션을 지원 해야 합니다. 이 기능은 트랜잭션의 영향을 받는 개체에 기본 제공 됩니다.

PowerShell 레지스트리 공급자는 Windows Vista에서 트랜잭션을 지원 합니다. TransactedString 개체 (TransactedString)는 PowerShell을 실행 하는 모든 운영 체제에서 작동 합니다.

다른 PowerShell 공급자는 트랜잭션을 지원할 수 있습니다. 세션에서 트랜잭션을 지 원하는 PowerShell 공급자를 찾으려면 다음 명령을 사용 하 여 공급자의 기능 속성에서 "트랜잭션" 값을 찾습니다.

```powershell
get-psprovider | where {$_.Capabilities -like "*transactions*"}
```

공급자에 대 한 자세한 내용은 공급자에 대 한 도움말을 참조 하십시오. 공급자 도움말을 가져오려면 다음을 입력 합니다.

```
get-help <provider-name>
```

예를 들어 레지스트리 공급자에 대한 도움말을 보려면 다음과 같이 입력합니다.

```powershell
get-help registry
```

## <a name="the-usetransaction-parameter"></a>USETRANSACTION 매개 변수

트랜잭션을 지원할 수 있는 cmdlet에는 UseTransaction 매개 변수가 있습니다. 이 매개 변수는 활성 트랜잭션에 명령을 포함 합니다. 전체 매개 변수 이름 또는 해당 별칭 ("usetx")을 사용할 수 있습니다.

매개 변수는 세션이 활성 트랜잭션을 포함 하는 경우에만 사용할 수 있습니다. 활성 트랜잭션이 없을 때 UseTransaction 매개 변수를 사용 하 여 명령을 입력 하면 명령이 실패 합니다.

UseTransaction 매개 변수를 사용 하 여 cmdlet을 찾으려면 다음을 입력 합니다.

```powershell
get-help * -parameter UseTransaction
```

PowerShell core에서 PowerShell 공급자와 함께 작동 하도록 설계 된 모든 cmdlet은 트랜잭션을 지원 합니다. 따라서 공급자 cmdlet을 사용 하 여 트랜잭션을 관리할 수 있습니다.

PowerShell 공급자에 대 한 자세한 내용은 [about_Providers](about_Providers.md)를 참조 하세요.

## <a name="the-transaction-object"></a>트랜잭션 개체입니다.

트랜잭션은 PowerShell에서 트랜잭션 개체인 System.object로 표시 됩니다.

개체에는 다음 속성이 있습니다.

- RollbackPreference: 현재 트랜잭션에 대 한 롤백 기본 설정 집합을 포함 합니다. Start-Transaction를 사용 하 여 트랜잭션을 시작할 때 롤백 기본 설정을 지정할 수 있습니다.

  Rollback 기본 설정에 따라 트랜잭션이 자동으로 롤백됩니다. 유효한 값은 Error, TerminatingError 및 Never입니다. 기본값은 Error입니다.

- 상태: 트랜잭션의 현재 상태를 포함 합니다. 유효한 값은 활성, 커밋 및 RolledBack입니다.

- SubscriberCount: 트랜잭션에 대 한 구독자 수를 포함 합니다. 다른 트랜잭션이 진행 중인 동안에는 트랜잭션을 시작할 때 구독자가 트랜잭션에 추가 됩니다. 구독자가 트랜잭션을 커밋하면 구독자 수가 감소 합니다.

## <a name="active-transactions"></a>활성 트랜잭션

PowerShell에서는 한 번에 하나의 트랜잭션만 활성화 되며 활성 트랜잭션만 관리할 수 있습니다. 동시에 여러 트랜잭션이 동일한 세션에서 진행 될 수 있지만 가장 최근에 시작 된 트랜잭션만 활성 상태입니다.

따라서 트랜잭션 cmdlet을 사용 하는 경우 특정 트랜잭션을 지정할 수 없습니다. 명령은 항상 활성 트랜잭션에 적용 됩니다.

이는 Get-Transaction cmdlet의 동작에서 가장 분명 하 게 드러납니다. Get-Transaction 명령을 입력 하면 항상 하나의 트랜잭션 개체만 가져옵니다 Get-Transaction. 이 개체는 활성 트랜잭션을 나타내는 개체입니다.

다른 트랜잭션을 관리 하려면 먼저 해당 트랜잭션을 커밋하거나 롤백하여 활성 트랜잭션을 완료 해야 합니다. 이렇게 하면 이전 트랜잭션이 자동으로 활성화 됩니다. 트랜잭션은 시작 된 순서와 반대로 활성화 되므로 가장 최근에 시작 된 트랜잭션이 항상 활성 상태가 됩니다.

## <a name="subscribers-and-independent-transactions"></a>구독자 및 독립 트랜잭션

다른 트랜잭션이 진행 되는 동안 트랜잭션을 시작 하면 기본적으로 PowerShell에서 새 트랜잭션을 시작 하지 않습니다. 대신 "구독자"를 현재 트랜잭션에 추가 합니다.

트랜잭션에 여러 구독자가 있는 경우 모든 시점에서 단일 Undo-Transaction 명령은 모든 구독자에 대 한 전체 트랜잭션을 롤백합니다. 그러나 트랜잭션을 커밋하려면 모든 구독자에 대해 Complete-Transaction 명령을 입력 해야 합니다.

트랜잭션에 대 한 구독자 수를 찾으려면 트랜잭션 개체의 SubscriberCount 속성을 확인 합니다. 예를 들어 다음 명령은 Get-Transaction cmdlet을 사용 하 여 활성 트랜잭션의 SubscriberCount 속성 값을 가져옵니다.

```powershell
(Get-Transaction).SubscriberCount
```

다른 트랜잭션이 진행 되는 동안 시작 된 대부분의 트랜잭션이 원래 트랜잭션과 관련 되기 때문에 구독자를 추가 하는 것이 기본 동작입니다. 일반적인 모델에서 트랜잭션이 포함 된 스크립트는 자체 트랜잭션을 포함 하는 도우미 스크립트를 호출 합니다. 트랜잭션은 관련 되어 있으므로 하나의 단위로 롤백하거나 커밋해야 합니다.

그러나 Start-Transaction cmdlet의 독립 매개 변수를 사용 하 여 현재 트랜잭션과 독립적인 트랜잭션을 시작할 수 있습니다.

독립 트랜잭션을 시작 하면 Start-Transaction 새 트랜잭션 개체를 만들고 새 트랜잭션이 활성 트랜잭션이 됩니다.
원본 트랜잭션에 영향을 주지 않고 독립 트랜잭션을 커밋하거나 롤백할 수 있습니다.

독립 트랜잭션이 완료 (커밋 또는 롤백) 되 면 원래 트랜잭션은 다시 활성 트랜잭션이 됩니다.

## <a name="changing-data"></a>데이터 변경

트랜잭션을 사용 하 여 데이터를 변경 하는 경우 트랜잭션에 의해 영향을 받는 데이터는 트랜잭션을 커밋할 때까지 변경 되지 않습니다. 그러나 트랜잭션의 일부가 아닌 명령으로 동일한 데이터를 변경할 수 있습니다.

트랜잭션을 사용 하 여 공유 데이터를 관리 하는 경우이 점을 염두에 두어야 합니다.
일반적으로 데이터베이스에는 작업 하는 동안 데이터를 잠그는 메커니즘이 있습니다 .이 메커니즘을 사용 하면 다른 사용자 및 다른 명령, 스크립트 및 함수를 변경할 수 없습니다.

그러나 잠금은 데이터베이스의 기능입니다. 트랜잭션과는 관련이 없습니다. 트랜잭션 사용 파일 시스템이 나 다른 데이터 저장소에서 작업 하는 경우 트랜잭션이 진행 되는 동안 데이터를 변경할 수 있습니다.

## <a name="examples"></a>예제

이 섹션의 예제에서는 PowerShell 레지스트리 공급자를 사용 하며 사용자가 잘 알고 있다고 가정 합니다. 레지스트리 공급자에 대 한 자세한 내용을 보려면 "get-help Registry"를 입력 하십시오.

### <a name="example-1-committing-a-transaction"></a>예 1: 트랜잭션 커밋

트랜잭션을 만들려면 Start-Transaction cmdlet을 사용 합니다. 다음 명령은 기본 설정을 사용 하 여 트랜잭션을 시작 합니다.

```powershell
start-transaction
```

트랜잭션에 명령을 포함 하려면 cmdlet의 UseTransaction 매개 변수를 사용 합니다. 기본적으로 명령은 트랜잭션에 포함 되지 않습니다.

예를 들어 HKCU: 드라이브의 소프트웨어 키에서 현재 위치를 설정 하는 다음 명령은 트랜잭션에 포함 되지 않습니다.

```powershell
cd hkcu:\Software
```

MyCompany 키를 만드는 다음 명령은 New-Item cmdlet의 UseTransaction 매개 변수를 사용 하 여 활성 트랜잭션에 명령을 포함 합니다.

```powershell
new-item MyCompany -UseTransaction
```

이 명령은 새 키를 나타내는 개체를 반환 하지만, 명령이 트랜잭션의 일부 이므로 레지스트리가 아직 변경 되지 않았습니다.

```
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
  0   0 MyCompany                      {}
```

트랜잭션을 커밋하려면 Complete-Transaction cmdlet을 사용 합니다. 항상 활성 트랜잭션에 영향을 주므로 트랜잭션을 지정할 수 없습니다.

```powershell
complete-transaction
```

따라서 MyCompany 키가 레지스트리에 추가 됩니다.

```powershell
dir m*
```

```output
Hive: HKEY_CURRENT_USER\software

SKC  VC Name                           Property
---  -- ----                           --------
 83   1 Microsoft                      {(default)}
  0   0 MyCompany                      {}
```

### <a name="example-2-rolling-back-a-transaction"></a>예 2: 트랜잭션 롤백

트랜잭션을 만들려면 Start-Transaction cmdlet을 사용 합니다. 다음 명령은 기본 설정을 사용 하 여 트랜잭션을 시작 합니다.

```powershell
start-transaction
```

MyOtherCompany 키를 만드는 다음 명령은 New-Item cmdlet의 UseTransaction 매개 변수를 사용 하 여 활성 트랜잭션에 명령을 포함 합니다.

```powershell
new-item MyOtherCompany -UseTransaction
```

이 명령은 새 키를 나타내는 개체를 반환 하지만, 명령이 트랜잭션의 일부 이므로 레지스트리가 아직 변경 되지 않았습니다.

```
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
  0   0 MyOtherCompany                 {}
```

트랜잭션을 롤백하려면 Undo-Transaction cmdlet을 사용 합니다. 항상 활성 트랜잭션에 영향을 주므로 트랜잭션을 지정 하지 않습니다.

```powershell
Undo-transaction
```

그러면 MyOtherCompany 키가 레지스트리에 추가 되지 않습니다.

```powershell
dir m*
```

```output
Hive: HKEY_CURRENT_USER\software

SKC  VC Name                           Property
---  -- ----                           --------
 83   1 Microsoft                      {(default)}
  0   0 MyCompany                      {}
```

### <a name="example-3-previewing-a-transaction"></a>예 3: 트랜잭션 미리 보기

일반적으로 트랜잭션 변경 데이터에 사용 되는 명령입니다. 그러나 데이터를 가져오는 명령은 트랜잭션 내에서 데이터를 가져오기 때문에 트랜잭션 에서도 유용 합니다. 이렇게 하면 트랜잭션을 커밋하는 변경 내용에 대 한 미리 보기가 제공 됩니다.

다음 예에서는 Get-ChildItem 명령을 사용 하는 방법을 보여 줍니다. 별칭은 "dir"을 사용 하 여 트랜잭션의 변경 내용을 미리 봅니다.

다음 명령은 트랜잭션을 시작 합니다.

```powershell
start-transaction
```

다음 명령은 New-ItemProperty cmdlet을 사용 하 여 MyCompany 키에 MyKey 레지스트리 항목을 추가 합니다. 이 명령은 UseTransaction 매개 변수를 사용 하 여 트랜잭션에 명령을 포함 합니다.

```powershell
new-itemproperty -path MyCompany -Name MyKey -value 123 -UseTransaction
```

이 명령은 새 레지스트리 항목을 나타내는 개체를 반환 하지만 레지스트리 항목은 변경 되지 않습니다.

```
MyKey
-----
123
```

현재 레지스트리에 있는 항목을 가져오려면 UseTransaction 매개 변수 없이 Get-ChildItem 명령 ("dir")을 사용 합니다. 다음 명령은 "M"으로 시작 하는 항목을 가져옵니다.

```powershell
dir m*
```

결과는 아직 MyCompany 키에 추가 된 항목이 없음을 보여 줍니다.

```output
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
 83   1 Microsoft                      {(default)}
  0   0 MyCompany                      {}
```

트랜잭션 커밋의 효과를 미리 보려면 UseTransaction 매개 변수를 사용 하 여 Get-ChildItem ("dir") 명령을 입력 합니다. 이 명령에는 트랜잭션 내의 데이터 뷰가 있습니다.

```powershell
dir m* -useTransaction
```

결과가 표시 되 면 트랜잭션이 커밋되면 MyKey 항목이 MyCompany 키에 추가 됩니다.

```output
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
 83   1 Microsoft                      {(default)}
  0   1 MyCompany                      {MyKey}
```

### <a name="example-4-combining-transacted-and-non-transacted-commands"></a>예제 4: 트랜잭션 및 비트랜잭션 명령 결합

트랜잭션 중에 비트랜잭션 명령을 입력할 수 있습니다. 비트랜잭션 명령은 데이터에 즉시 영향을 주지만 트랜잭션에는 영향을 주지 않습니다.
다음 명령은 HKCU: \ Software 레지스트리 키에서 트랜잭션을 시작 합니다.

```powershell
start-transaction
```

다음 세 명령은 New-Item cmdlet을 사용 하 여 레지스트리에 키를 추가 합니다.
첫 번째 및 세 번째 명령은 UseTransaction 매개 변수를 사용 하 여 트랜잭션에 명령을 포함 합니다. 두 번째 명령은 매개 변수를 생략 합니다. 두 번째 명령이 트랜잭션에 포함 되지 않기 때문에 즉시 적용 됩니다.

```powershell
new-item MyCompany1 -UseTransaction
new-item MyCompany2
new-item MyCompany3 -UseTransaction
```

레지스트리의 현재 상태를 보려면 UseTransaction 매개 변수 없이 Get-ChildItem ("dir") 명령을 사용 합니다. 이 명령은 "M"으로 시작 하는 항목을 가져옵니다.

```powershell
dir m*
```

결과는 MyCompany2 키가 레지스트리에 추가 되었음을 보여 주지만 트랜잭션의 일부인 MyCompany1 및 MyCompany3 키는 추가 되지 않습니다.

```output
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
 83   1 Microsoft                      {(default)}
  0    0 MyCompany2                     {}
```

다음 명령은 트랜잭션을 커밋합니다.

```powershell
complete-transaction
```

이제 트랜잭션의 일부로 추가 된 키가 레지스트리에 표시 됩니다.

```powershell
dir m*
```

```output
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
83   1 Microsoft                      {(default)}
0    0 MyCompany1                     {}
0    0 MyCompany2                     {}
0    0 MyCompany3                     {}
```

### <a name="example-5-using-automatic-rollback"></a>예 5: 자동 롤백 사용

트랜잭션의 명령이 어떤 종류의 오류를 생성 하는 경우 트랜잭션이 자동으로 롤백됩니다.

이 기본 동작은 트랜잭션을 실행 하는 스크립트를 위해 설계 되었습니다. 스크립트는 일반적으로 잘 테스트 되 고 오류 처리 논리를 포함 하므로 오류가 예상 되지 않으며 트랜잭션을 종료 해야 합니다.

첫 번째 명령은 HKCU: \ Software 레지스트리 키에서 트랜잭션을 시작 합니다.

```powershell
start-transaction
```

다음 명령은 New-Item cmdlet을 사용 하 여 MyCompany 키를 레지스트리에 추가 합니다. 이 명령은 UseTransaction 매개 변수를 사용 하 여 (별칭은 "usetx") 트랜잭션에 명령을 포함 합니다.

```powershell
New-Item MyCompany -UseTX
```

MyCompany 키가 레지스트리에 이미 존재 하기 때문에 명령이 실패 하 고 트랜잭션이 롤백됩니다.

```output
New-Item : A key at this path already exists
At line:1 char:9
+ new-item <<<<  MyCompany -usetx
```

Get-Transaction 명령은 트랜잭션이 롤백되고 SubscriberCount가 0 인지 확인 합니다.

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                0                 RolledBack
```

### <a name="example-6-changing-the-rollback-preference"></a>예 6: 롤백 기본 설정 변경

트랜잭션을 더 이상 오류를 허용 하려면 Start-Transaction의 RollbackPreference 매개 변수를 사용 하 여 기본 설정을 변경할 수 있습니다.

다음 명령은 rollback 기본 설정인 "Never"를 사용 하 여 트랜잭션을 시작 합니다.

```powershell
start-transaction -rollbackpreference Never
```

이 경우 명령이 실패 하면 트랜잭션이 자동으로 롤백되지 않습니다.

```powershell
New-Item MyCompany -UseTX
```

```output
New-Item : A key at this path already exists
At line:1 char:9
+ new-item <<<<  MyCompany -usetx
```

트랜잭션이 아직 활성 상태 이므로 트랜잭션의 일부로 명령을 다시 제출할 수 있습니다.

```powershell
New-Item MyOtherCompany -UseTX
```

### <a name="example-7-using-the-use-transaction-cmdlet"></a>예 7: USE-TRANSACTION CMDLET 사용

Use-Transaction cmdlet을 사용 하면 트랜잭션 사용 Microsoft .NET Framework 개체에 대해 직접 스크립팅을 수행할 수 있습니다. Use-Transaction은 TransactedString 클래스의 인스턴스와 같이 트랜잭션 사용 .NET Framework 개체를 사용 하는 명령 및 식만 포함할 수 있는 스크립트 블록을 사용 합니다.

다음 명령은 트랜잭션을 시작 합니다.

```powershell
start-transaction
```

다음 New-Object 명령은 TransactedString 클래스의 인스턴스를 만들어 $t 변수에 저장 합니다.

```powershell
$t = New-Object Microsoft.PowerShell.Commands.Management.TransactedString
```

다음 명령은 TransactedString 개체의 Append 메서드를 사용 하 여 문자열에 텍스트를 추가 합니다. 이 명령은 트랜잭션의 일부가 아니므로 변경 내용이 즉시 적용 됩니다.

```powershell
$t.append("Windows")
```

다음 명령은 동일한 Append 메서드를 사용 하 여 텍스트를 추가 하지만 트랜잭션 일부로 텍스트를 추가 합니다. 명령은 중괄호로 묶이고 Use-Transaction의 ScriptBlock 매개 변수 값으로 설정 됩니다. UseTransaction 매개 변수 (UseTx)가 필요 합니다.

```powershell
use-transaction {$t.append(" PowerShell")} -usetx
```

$T에서 트랜잭션 문자열의 현재 내용을 보려면 TransactedString 개체의 ToString 메서드를 사용 합니다.

```powershell
$t.tostring()
```

출력에는 비트랜잭션 변경 내용만 적용 됨이 표시 됩니다.

```output
Windows
```

트랜잭션 내에서 $t 트랜잭션 문자열의 현재 내용을 보려면 Use-Transaction 명령에 식을 포함 합니다.

```powershell
use-transaction {$s.tostring()} -usetx
```

출력은 트랜잭션 뷰를 표시 합니다.

```output
PowerShell
```

다음 명령은 트랜잭션을 커밋합니다.

```powershell
complete-transaction
```

최종 문자열을 보려면 다음을 수행 합니다.

```
$t.tostring()
PowerShell
```

### <a name="example-8-managing-multi-subscriber-transactions"></a>예 8: 다중 구독자 트랜잭션 관리

다른 트랜잭션이 진행 되는 동안 트랜잭션을 시작할 때 PowerShell은 기본적으로 두 번째 트랜잭션을 만들지 않습니다. 대신 현재 트랜잭션에 구독자를 추가 합니다.

이 예에서는 다중 구독자 트랜잭션을 보고 관리 하는 방법을 보여 줍니다.

먼저 HKCU: \ Software 키에서 트랜잭션을 시작 합니다.

```powershell
start-transaction
```

다음 명령은 Get-Transaction 명령을 사용 하 여 활성 트랜잭션을 가져옵니다.

```powershell
get-transaction
```

결과는 활성 트랜잭션을 나타내는 개체를 표시 합니다.

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                1                 Active
```

다음 명령은 레지스트리에 MyCompany 키를 추가 합니다. 이 명령은 UseTransaction 매개 변수를 사용 하 여 트랜잭션에 명령을 포함 합니다.

```powershell
new-item MyCompany -UseTransaction
```

다음 명령은 Start-Transaction 명령을 사용 하 여 트랜잭션을 시작 합니다. 명령 프롬프트에서이 명령을 입력 하는 경우에도이 시나리오는 트랜잭션이 포함 된 스크립트를 실행할 때 발생할 수 있습니다.

```powershell
start-transaction
```

Get-Transaction 명령은 트랜잭션 개체의 구독자 수가 증가 하는 것을 보여 줍니다. 값은 이제 2입니다.

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                2                 Active
```

다음 명령은 New-ItemProperty cmdlet을 사용 하 여 MyCompany 키에 MyKey 레지스트리 항목을 추가 합니다. UseTransaction 매개 변수를 사용 하 여 트랜잭션에 명령을 포함 합니다.

```powershell
new-itemproperty -path MyCompany -name MyKey -UseTransaction
```

MyCompany 키가 레지스트리에 없지만이 명령은 두 명령이 동일한 트랜잭션에 포함 되어 있기 때문에 성공 합니다.

다음 명령은 트랜잭션을 커밋합니다. 트랜잭션을 롤백하는 경우 모든 구독자에 대해 트랜잭션이 롤백됩니다.

```powershell
complete-transaction
```

Get-Transaction 명령은 트랜잭션 개체의 구독자 수가 1 이지만 Status 값이 아직 활성 (커밋되지 않음) 임을 보여 줍니다.

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                1                 Active
```

트랜잭션 커밋을 완료 하려면 두 번째 Complete Transaction 명령을 입력 합니다. 다중 구독자 트랜잭션을 커밋하려면 각 Start-Transaction 명령에 대해 하나의 Complete-Transaction 명령을 입력 해야 합니다.

```powershell
complete-transaction
```

다른 Get-Transaction 명령은 트랜잭션이 커밋 되었음을 보여 줍니다.

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                0                 Committed
```

### <a name="example-9-managing-independent-transactions"></a>예 9: 독립 트랜잭션 관리

다른 트랜잭션이 진행 되는 동안 트랜잭션을 시작할 때 Start-Transaction의 독립적인 매개 변수를 사용 하 여 새 트랜잭션을 원래 트랜잭션과 독립적으로 만들 수 있습니다.

이렇게 하면 Start-Transaction 새 트랜잭션 개체를 만들고 새 트랜잭션을 활성 트랜잭션으로 만듭니다.

먼저 HKCU: Software 키에서 트랜잭션을 시작 \\ 합니다.

```powershell
start-transaction
```

다음 명령은 Get-Transaction 명령을 사용 하 여 활성 트랜잭션을 가져옵니다.

```powershell
get-transaction
```

결과는 활성 트랜잭션을 나타내는 개체를 표시 합니다.

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                1                 Active
```

다음 명령은 트랜잭션의 일부로 MyCompany 레지스트리 키를 추가 합니다. UseTransaction 매개 변수 (UseTx)를 사용 하 여 활성 트랜잭션에 명령을 포함 합니다.

```powershell
new-item MyCompany -use
```

다음 명령은 새 트랜잭션을 시작 합니다. 이 명령은 독립 매개 변수를 사용 하 여이 트랜잭션이 활성 트랜잭션에 대 한 구독자가 아님을 표시 합니다.

```powershell
start-transaction -independent
```

독립 트랜잭션을 만들 때 새로운 (가장 최근에 생성 된) 트랜잭션이 활성 트랜잭션이 됩니다. Get-Transaction 명령을 사용 하 여 활성 트랜잭션을 가져올 수 있습니다.

```powershell
get-transaction
```

트랜잭션의 SubscriberCount는 1로, 다른 구독자가 없고 트랜잭션이 새로운 것을 나타냅니다.

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                1                 Active
```

원본 트랜잭션을 관리 하려면 먼저 새 트랜잭션을 완료 (커밋 또는 롤백) 해야 합니다.

다음 명령은 MyOtherCompany 키를 레지스트리에 추가 합니다. UseTransaction 매개 변수 (UseTx)를 사용 하 여 활성 트랜잭션에 명령을 포함 합니다.

```powershell
new-item MyOtherCompany -usetx
```

이제 트랜잭션을 롤백합니다. 두 개의 구독자가 있는 단일 트랜잭션이 있는 경우 트랜잭션을 롤백하면 모든 구독자에 대 한 전체 트랜잭션이 롤백됩니다.

그러나 이러한 트랜잭션은 독립적 이기 때문에 최신 트랜잭션을 롤백하여 레지스트리 변경 내용을 취소 하 고 원래 트랜잭션을 활성 트랜잭션으로 만듭니다.

```powershell
undo-transaction
```

Get-Transaction 명령은 원본 트랜잭션이 세션에서 여전히 활성 상태임을 확인 합니다.

```powershell
get-transaction
```

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                1                 Active
```

다음 명령은 활성 트랜잭션을 커밋합니다.

```powershell
complete-transaction
```

Get-ChildItem 명령은 레지스트리가 변경 되었음을 보여 줍니다.

```powershell
dir m*
```

```output
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
 83   1 Microsoft                      {(default)}
  0   0 MyCompany                      {}
```

## <a name="see-also"></a>참고 항목

[Start-Transaction](xref:Microsoft.PowerShell.Management.Start-Transaction)

[Get-Transaction](xref:Microsoft.PowerShell.Management.Get-Transaction)

[Complete-Transaction](xref:Microsoft.PowerShell.Management.Complete-Transaction)

[Undo-Transaction](xref:Microsoft.PowerShell.Management.Undo-Transaction)

[Use-Transaction](xref:Microsoft.PowerShell.Management.Use-Transaction)

[Get-PSProvider](xref:Microsoft.PowerShell.Management.Get-PSProvider)

[Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)

[about_Providers](about_Providers.md)
