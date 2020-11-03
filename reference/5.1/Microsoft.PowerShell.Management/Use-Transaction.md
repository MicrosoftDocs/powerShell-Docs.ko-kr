---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/use-transaction?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Use-Transaction
ms.openlocfilehash: db8423aef6dc4b25c4ddd13f9b29b774463c6a6c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93214354"
---
# Use-Transaction

## 개요
스크립트 블록을 활성 트랜잭션에 추가합니다.

## SYNTAX

```
Use-Transaction [-TransactedScript] <ScriptBlock> [-UseTransaction] [<CommonParameters>]
```

## 설명
**Use-transaction** cmdlet은 활성 트랜잭션에 스크립트 블록을 추가 합니다.
이렇게 하면 트랜잭션 사용 Microsoft .NET 프레임 워크 개체를 사용 하 여 트랜잭션 스크립팅 작업을 수행할 수 있습니다.
이 스크립트 블록에는 Microsoft.PowerShell.Commands.Management.TransactedString 클래스 등 트랜잭션이 사용 가능한 .NET Framework 개체만 포함될 수 있습니다.

이 cmdlet을 사용 하는 경우 대부분의 cmdlet에 대 한 옵션인 *UseTransaction* 매개 변수가 필요 합니다.

**Use-Transaction** 은 Windows PowerShell의 트랜잭션 기능을 지 원하는 cmdlet 집합 중 하나입니다.
자세한 내용은 about_Transactions를 참조하세요.

## 예제

### 예제 1: 트랜잭션 사용 개체를 사용 하 여 스크립팅

```
PS C:\> Start-Transaction
PS C:\> $transactedString = New-Object Microsoft.PowerShell.Commands.Management.TransactedString
PS C:\> $transactedString.Append("Hello")
PS C:\> Use-Transaction -TransactedScript { $transactedString.Append(", World") } -UseTransaction
PS C:\> $transactedString.ToString()
Hello
PS C:\> Use-Transaction -TransactedScript { $transactedString.ToString() } -UseTransaction
Hello, World
PS C:\> Complete-Transaction
PS C:\> $transactedString.ToString()
Hello, World
```

이 예에서는 transaction 사용 .NET Framework 개체에 대해 **스크립트를 사용 하 여** 스크립트를 사용 하는 방법을 보여 줍니다.
이 경우 개체는 **TransactedString** 개체입니다.

첫 번째 명령은 Start-Transaction cmdlet을 사용하여 트랜잭션을 시작합니다.

두 번째 명령은 New-Object 명령을 사용 하 여 **TransactedString** 개체를 만듭니다.
개체를 $TransactedString 변수에 저장합니다.

세 번째 및 네 번째 명령은 모두 **TransactedString** 개체의 **Append** 메서드를 사용 하 여 $TransactedString 값에 텍스트를 추가 합니다.
한 명령은 트랜잭션의 일부입니다.
다른 명령은이 아닙니다.

세 번째 명령은 트랜잭션 문자열의 **Append** 메서드를 사용 하 여 $TransactedString 값에 Hello를 추가 합니다.
이 명령은 트랜잭션의 일부가 아니므로 변경 사항이 즉시 적용됩니다.

네 번째 명령은 **-transaction을 사용** 하 여 트랜잭션의 문자열에 텍스트를 추가 합니다.
이 명령은 **Append** 메서드를 사용 하 여 $TransactedString 값에 ", 세계"를 추가 합니다.
명령은 중괄호 ()로 묶어 {} 스크립트 블록으로 만듭니다.
*UseTransaction* 매개 변수는이 명령에 필요 합니다.

다섯 번째 및 여섯 번째 명령은 **TransactedString** 개체의 **ToString** 메서드를 사용 하 여 **TransactedString** 값을 문자열로 표시 합니다.
다시 한 가지 명령은 트랜잭션의 일부입니다.
다른 트랜잭션은 그렇지 않습니다.

다섯 번째 명령은 **ToString** 메서드를 사용 하 여 $TransactedString 변수의 현재 값을 표시 합니다.
이 명령은 트랜잭션의 일부가 아니므로 문자열의 현재 상태만 표시됩니다.

여섯 번째 명령은 **Use-transaction** 을 사용 하 여 트랜잭션에서 동일한 명령을 실행 합니다.
이 명령은 트랜잭션의 일부 이므로 트랜잭션 변경 내용 미리 보기와 매우 유사 하 게 트랜잭션의 현재 문자열 값을 표시 합니다.

일곱 번째 명령은 Complete-Transaction cmdlet을 사용하여 트랜잭션을 커밋합니다.

마지막 명령은 **ToString** 메서드를 사용 하 여 변수의 결과 값을 문자열로 표시 합니다.

### 예 2: 트랜잭션 롤백

```
PS C:\> Start-Transaction
PS C:\> $transactedString = New-Object Microsoft.PowerShell.Commands.Management.TransactedString
PS C:\> $transactedString.Append("Hello")
PS C:\> Use-Transaction -TransactedScript { $transactedString.Append(", World") } -UseTransaction
PS C:\> Undo-Transaction
PS C:\> $transactedString.ToString()
Hello
```

이 예에서는 **Use transaction** 명령을 포함 하는 트랜잭션을 롤백하는 경우의 결과를 보여 줍니다.
트랜잭션의 다른 명령과 마찬가지로, 트랜잭션을 롤백하면 변경 사항이 취소되고 데이터가 원래대로 돌아갑니다.

첫 번째 명령은 **Start transaction** 을 사용 하 여 트랜잭션을 시작 합니다.

두 번째 명령은 **TransactedString** 개체를 사용 하 여 **새** 개체를 만듭니다.
개체를 $TransactedString 변수에 저장합니다.

트랜잭션의 일부가 아닌 세 번째 명령은 **Append** 메서드를 사용 하 여 $TransactedString 값에 "Hello"를 추가 합니다.

네 번째 명령은 transaction을 **사용** 하 여 트랜잭션에서 **Append** 메서드를 사용 하는 다른 명령을 실행 합니다.
이 명령은 **Append** 메서드를 사용 하 여 $TransactedString 값에 ", 세계"를 추가 합니다.

다섯 번째 명령은 Undo-Transaction cmdlet을 사용하여 트랜잭션을 롤백합니다.
따라서 트랜잭션에서 수행 된 모든 명령이 되돌려집니다.

마지막 명령은 **ToString** 메서드를 사용 하 여 $TransactedString 결과 값을 문자열로 표시 합니다.
결과는 트랜잭션 외부에서 수행 된 변경 내용만 개체에 적용 되었음을 보여 줍니다.

## PARAMETERS

### -TransactedScript
트랜잭션에서 실행되는 스크립트 블록을 지정합니다.
유효한 스크립트 블록을 중괄호( { } )로 묶어 입력합니다.
이 매개 변수는 필수적 요소입니다.

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseTransaction
활성 트랜잭션에 명령을 포함합니다.
이 매개 변수는 트랜잭션이 진행 중인 경우에만 사용할 수 있습니다.
자세한 내용은 about_transactions를 참조 하세요.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: usetx

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

### PSObject
이 cmdlet은 트랜잭션 결과를 반환 합니다.

## 참고

* *UseTransaction* 매개 변수는 활성 트랜잭션에 명령을 포함 합니다. **Transaction** cmdlet은 항상 트랜잭션에서 사용 되기 때문에이 매개 변수는 사용 하는 **트랜잭션** 명령을 효과적으로 만드는 데 필요 합니다.

*

## 관련 링크

[Complete-Transaction](Complete-Transaction.md)

[Get-Transaction](Get-Transaction.md)

[Start-Transaction](Start-Transaction.md)

[Undo-Transaction](Undo-Transaction.md)
