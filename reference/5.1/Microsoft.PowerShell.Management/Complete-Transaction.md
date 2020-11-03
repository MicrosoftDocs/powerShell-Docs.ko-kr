---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/complete-transaction?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Complete-Transaction
ms.openlocfilehash: 20fbdd86aab07dda065492eff2da4f358fb2ffca
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93215554"
---
# Complete-Transaction

## 개요
활성 트랜잭션을 커밋합니다.

## SYNTAX

```
Complete-Transaction [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명
**Complete transaction** cmdlet은 활성 트랜잭션을 커밋합니다.
트랜잭션을 커밋하면 트랜잭션의 명령이 마무리되어 명령의 영향을 받는 데이터가 변경됩니다.

트랜잭션에 여러 구독자가 포함 된 경우 트랜잭션을 커밋하려면 모든 Start-Transaction 명령에 대해 하나의 **Complete transaction** 명령을 입력 해야 합니다.

**Complete-Transaction** Cmdlet은 Windows PowerShell의 트랜잭션 기능을 지 원하는 cmdlet 집합 중 하나입니다.
자세한 내용은 about_Transactions를 참조하세요.

## 예제

### 예제 1: 트랜잭션 커밋

```
PS C:\> cd hkcu:\software
PS HKCU:\software> Start-Transaction
PS HKCU:\software> New-Item MyCompany -UseTransaction
PS HKCU:\software> dir m*
Hive: HKEY_CURRENT_USER\software

SKC  VC Name                           Property
---  -- ----                           --------
82   1 Microsoft                      {(default)}

PS HKCU:\software> Complete-Transaction
PS HKCU:\software> dir m*
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
82   1 Microsoft                      {(default)}
0   0 MyCompany                      {}
```

이 예에서는 **전체 트랜잭션** cmdlet을 사용 하 여 트랜잭션을 커밋하는 경우 발생 하는 상황을 보여 줍니다.

**Start transaction** 명령은 트랜잭션을 시작 합니다.
New-Item 명령은 *UseTransaction* 매개 변수를 사용 하 여 트랜잭션에 명령을 포함 합니다.

첫 번째 dir (Get ChildItem) 명령은 새 항목이 레지스트리에 아직 추가 되지 않은 것을 보여 줍니다.

**Complete transaction** 명령을 사용 하면 트랜잭션이 커밋되고 레지스트리 변경 내용이 적용 됩니다.
그 결과 두 번째 dir 명령은 레지스트리가 변경 되었음을 보여 줍니다.

### 예 2: 둘 이상의 구독자가 있는 트랜잭션 커밋

```
PS C:\> cd hkcu:\software
PS HKCU:\software> Start-Transaction
PS HKCU:\software> New-Item MyCompany -UseTransaction
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
0   0 MyCompany                      {}

PS HKCU:\software> Start-Transaction
PS HKCU:\Software> Get-Transaction

RollbackPreference   SubscriberCount  Status
------------------   ---------------  ------
Error                2                Active

PS HKCU:\software> New-ItemProperty -Path MyCompany -Name MyKey -Value -UseTransaction

MyKey
-----
123

PS HKCU:\software> Complete-Transaction
PS HKCU:\software> Get-Transaction

RollbackPreference   SubscriberCount  Status
------------------   ---------------  ------
Error                1                Active

PS HKCU:\software> dir m*
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
82   1 Microsoft                      {(default)}

PS HKCU:\software> Complete-Transaction
PS HKCU:\software> dir m*
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
82   1 Microsoft                      {(default)}
0   1 MyCompany                      {MyKey}
```

이 예에서는 **Complete transaction** 을 사용 하 여 구독자가 둘 이상인 트랜잭션을 커밋하는 방법을 보여 줍니다.

다중 구독자 트랜잭션을 커밋하려면 모든 **시작 트랜잭션** 명령에 대해 하나의 **Complete transaction** 명령을 입력 해야 합니다.
데이터는 최종 **전체 트랜잭션** 명령이 전송 될 때만 변경 됩니다.

이 예제에서는 이해를 돕기 위해 명령줄에 입력하는 일련의 명령을 보여 줍니다.
실제 환경에서는 대개 스크립트로 트랜잭션을 실행하며 보조 트랜잭션은 주 스크립트로 호출되는 함수나 도우미 스크립트를 통해 실행합니다.

이 예에서는 **시작 트랜잭션** 명령이 트랜잭션을 시작 합니다.
*UseTransaction* 매개 변수를 사용 하는 **새 항목** 명령은 MyCompany 키를 소프트웨어 키에 추가 합니다.
**새 항목** cmdlet은 키 개체를 반환 하지만 레지스트리의 데이터는 아직 변경 되지 않았습니다.

두 번째 **시작 트랜잭션** 명령은 기존 트랜잭션에 두 번째 구독자를 추가 합니다.
**Get Transaction** cmdlet은 구독자 수가 2 인지 확인 합니다.
*UseTransaction* 매개 변수가 있는 New-ItemProperty 명령은 레지스트리 항목을 새 MyCompany 키에 추가 합니다.
다시 명령이 값을 반환하지만 레지스트리는 변경되지 않습니다.

첫 번째 **Complete Transaction** 명령은 구독자 수를 1만 큼 줄입니다.
이는 **Get Transaction** 명령에 의해 확인 됩니다.
그러나 dir m * (복합적 **item** ) 명령에의 한 데이터는 변경 되지 않습니다.

두 번째 **Complete transaction** 명령은 전체 트랜잭션을 커밋하고 레지스트리에서 데이터를 변경 합니다.
이는 변경 내용을 표시 하는 두 번째 dir m * 명령에 의해 확인 됩니다.

### 예 3: 데이터를 변경 하지 않는 트랜잭션 수행

```
PS C:\> cd hkcu:\software
PS HKCU:\software> Start-Transaction
PS HKCU:\software> New-Item MyCompany -UseTransaction
PS HKCU:\software> dir m*
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
82   1 Microsoft                      {(default)}

PS HKCU:\software> dir m* -UseTransaction
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
82   1 Microsoft                      {(default)}
0   0 MyCompany                      {}

PS HKCU:\software> Complete-Transaction
```

이 예에서는 \* 트랜잭션에서 Get 명령과 데이터를 변경 하지 않는 다른 명령을 사용 하는 값을 보여 줍니다.
트랜잭션에서 Get 명령이 사용 되는 경우 \* 트랜잭션에 포함 된 개체를 가져옵니다.
이 경우 트랜잭션의 변경 내용을 커밋하기 전에 미리 볼 수 있습니다.

이 예제에서는 트랜잭션이 시작됩니다.
*UseTransaction* 매개 변수가 있는 New-Item 명령은 트랜잭션의 일부로 레지스트리에 새 키를 추가 합니다.

**Complete Transaction** 명령이 실행 될 때까지 새 레지스트리 키가 레지스트리에 추가 되지 않기 때문에 간단한 Dir ( **Get-childitem** ) 명령에 새 키가 없는 레지스트리가 표시 됩니다.

그러나 *UseTransaction* 매개 변수를 dir 명령에 추가 하면이 명령은 트랜잭션의 일부가 되며 데이터에 아직 추가 되지 않은 경우에도 트랜잭션의 항목을 가져옵니다.

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
이 cmdlet에 개체를 파이프할 수 없습니다.

## 출력

### 없음
이 cmdlet은 어떠한 출력도 생성하지 않습니다.

## 참고

* 커밋된 트랜잭션을 롤백하거나 롤백된 트랜잭션을 커밋할 수 없습니다.

  활성 트랜잭션이 아닌 트랜잭션은 롤백할 수 없습니다.
다른 트랜잭션을 롤백하려면 먼저 활성 트랜잭션을 커밋하거나 롤백해야 합니다.

  트랜잭션의 명령에서 오류가 발생할 경우와 같이 트랜잭션 일부를 커밋할 수 없는 경우에는 기본적으로 전체 트랜잭션이 롤백됩니다.

*

## 관련 링크

[Get-Transaction](Get-Transaction.md)

[Start-Transaction](Start-Transaction.md)

[Undo-Transaction](Undo-Transaction.md)

[Use-Transaction](Use-Transaction.md)

[Get-ChildItem](Get-ChildItem.md)

[New-Item](New-Item.md)

[New-ItemProperty](New-ItemProperty.md)
