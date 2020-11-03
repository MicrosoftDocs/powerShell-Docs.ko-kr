---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 11/11/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/update-list?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-List
ms.openlocfilehash: c0d5c5b9ed6beed635b9df1ba9523b29c5cac9eb
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93217553"
---
# Update-List

## 개요
개체 컬렉션을 포함하는 속성 값에 항목을 추가하거나 제거합니다.

## SYNTAX

### AddRemoveSet (기본값)

```
Update-List [-Add <Object[]>] [-Remove <Object[]>] [-InputObject <PSObject>] [[-Property] <String>]
 [<CommonParameters>]
```

### ReplaceSet

```
Update-List -Replace <Object[]> [-InputObject <PSObject>] [[-Property] <String>] [<CommonParameters>]
```

## 설명

`Update-List`Cmdlet은 개체의 속성 값에 있는 항목을 추가, 제거 또는 바꾸고 업데이트 된 개체를 반환 합니다. 이 cmdlet은 개체 컬렉션을 포함하는 속성에 사용됩니다.

**Add** 및 **remove** 매개 변수는 컬렉션에서 개별 항목을 추가 하 고 제거 합니다.
**Replace** 매개 변수는 전체 컬렉션을 대체 합니다.

명령에서 속성을 지정 하지 않으면에서 개체를 업데이트 하는 `Update-List` 대신 업데이트를 설명 하는 개체를 반환 합니다. Cmdlet과 같은 개체를 변경 하는 cmdlet에 업데이트 개체를 제출할 수 있습니다 `Set` .

이 cmdlet은 업데이트 되는 속성이를 사용 하는 **IList** 인터페이스를 지 원하는 경우에만 작동 `Update-List` 합니다. 또한 업데이트를 `Set` 수락 하는 모든 cmdlet은 **IList** 인터페이스를 지원 해야 합니다.

PowerShell과 함께 설치 된 핵심 cmdlet은이 인터페이스를 지원 하지 않습니다. Cmdlet이를 지원 하는지 확인 하려면 `Update-List` Cmdlet 도움말 항목을 참조 하세요.

이 cmdlet은 PowerShell 7에서 다시 도입 되었습니다.

## 예제

### 예제 1: 속성 값에 항목 추가

이 예제에서는 카드가 **목록** 컬렉션 개체로 저장 되는 카드의 데크를 나타내는 클래스를 만듭니다. **Newdeck ()** 메서드는 `Update-List` 를 사용 하 여 카드 컬렉션에 카드 값의 전체 **cards** 데크를 추가 합니다.

```powershell
class Cards {

    [System.Collections.Generic.List[string]]$cards
    [string]$name

    Cards([string]$_name) {
        $this.name = $_name
        $this.cards = [System.Collections.Generic.List[string]]::new()
    }

    NewDeck() {
        $_suits = "`u{2663}","`u{2666}","`u{2665}","`u{2660}"
        $_values = 'A',2,3,4,5,6,7,8,9,10,'J','Q','K'
        $_deck = foreach ($s in $_suits){ foreach ($v in $_values){ "$v$s"} }
        $this | Update-List -Property cards -Add $_deck | Out-Null
    }

    Show() {
        Write-Host
        Write-Host $this.name ": " $this.cards[0..12]
        if ($this.cards.count -gt 13) {
            Write-Host (' ' * ($this.name.length+3)) $this.cards[13..25]
        }
        if ($this.cards.count -gt 26) {
            Write-Host (' ' * ($this.name.length+3)) $this.cards[26..38]
        }
        if ($this.cards.count -gt 39) {
            Write-Host (' ' * ($this.name.length+3)) $this.cards[39..51]
        }
    }

    Shuffle() { $this.cards = Get-Random -InputObject $this.cards -Count 52 }

    Sort() { $this.cards.Sort() }
}
```

> [!NOTE]
> `Update-List`Cmdlet은 업데이트 된 개체를 파이프라인으로 출력 합니다. 출력을로 파이프 하 여 `Out-Null` 원치 않는 표시를 표시 하지 않습니다.

### 예제 2: 컬렉션 속성 항목 추가 및 제거

예 1의 코드를 계속 진행 하면 카드 클래스의 인스턴스를 만들어 **카드의** 데크와 두 플레이어가 보유 한 카드를 나타냅니다. Cmdlet을 사용 `Update-List` 하 여 플레이어의 손으로 카드를 추가 하 고 데크에서 카드를 제거 합니다.

```powershell
$player1 = [Cards]::new('Player 1')
$player2 = [Cards]::new('Player 2')

$deck = [Cards]::new('Deck')
$deck.NewDeck()
$deck.Shuffle()
$deck.Show()

# Deal two hands
$player1 | Update-List -Property cards -Add $deck.cards[0,2,4,6,8] | Out-Null
$player2 | Update-List -Property cards -Add $deck.cards[1,3,5,7,9] | Out-Null
$deck | Update-List -Property cards -Remove $player1.cards | Out-Null
$deck | Update-List -Property cards -Remove $player2.cards | Out-Null

$player1.Show()
$player2.Show()
$deck.Show()
```

```Output
Deck :  4♦ 7♥ J♦ 5♣ A♣ 8♦ J♣ Q♥ 6♦ 3♦ 9♦ 6♣ 2♣
        K♥ 4♠ 10♥ 8♠ 10♦ 9♠ 6♠ K♦ 7♣ 3♣ Q♣ A♥ Q♠
        3♥ 5♥ 2♦ 5♠ J♥ J♠ 10♣ 4♥ Q♦ 10♠ 4♣ 2♠ 2♥
        6♥ 7♦ A♠ 5♦ 8♣ 9♥ K♠ 7♠ 3♠ 9♣ A♦ K♣ 8♥

Player 1 :  4♦ J♦ A♣ J♣ 6♦

Player 2 :  7♥ 5♣ 8♦ Q♥ 3♦

Deck :  9♦ 6♣ 2♣ K♥ 4♠ 10♥ 8♠ 10♦ 9♠ 6♠ K♦ 7♣ 3♣
        Q♣ A♥ Q♠ 3♥ 5♥ 2♦ 5♠ J♥ J♠ 10♣ 4♥ Q♦ 10♠
        4♣ 2♠ 2♥ 6♥ 7♦ A♠ 5♦ 8♣ 9♥ K♠ 7♠ 3♠ 9♣
        A♦ K♣ 8♥
```

출력은 카드가 플레이어에 처리 되기 전의 데크 상태를 보여 줍니다. 각 플레이어가 데크에서 5 개의 카드를 수신 하는 것을 볼 수 있습니다. 최종 출력은 플레이어에 카드를 처리 한 후 데크 상태를 보여 줍니다. `Update-List` 는 데크에서 카드를 선택 하 여 플레이어의 컬렉션에 추가 하는 데 사용 되었습니다. 그런 다음를 사용 하 여 플레이어의 카드를 데크에서 제거 했습니다 `Update-List` .

### 예제 3: 단일 명령에서 항목 추가 및 제거

`Update-List` 단일 명령에 **추가** 및 **제거** 매개 변수를 사용할 수 있습니다. 이 예에서 플레이어 1은 및를 삭제 하 `4♦` `6♦` 고 두 개의 새 카드를 가져옵니다.

```powershell
# Player 1 wants two new cards - remove 2 cards & add 2 cards
$player1 | Update-List -Property cards -Remove $player1.cards[0,4] -Add $deck.cards[0..1] | Out-Null
$player1.Show()

# remove dealt cards from deck
$deck | Update-List -Property cards -Remove $deck.cards[0..1] | Out-Null
$deck.Show()
```

```Output
Player 1 :  J♦ A♣ J♣ 9♦ 6♣

Deck :  2♣ K♥ 4♠ 10♥ 8♠ 10♦ 9♠ 6♠ K♦ 7♣ 3♣ Q♣ A♥
        Q♠ 3♥ 5♥ 2♦ 5♠ J♥ J♠ 10♣ 4♥ Q♦ 10♠ 4♣ 2♠
        2♥ 6♥ 7♦ A♠ 5♦ 8♣ 9♥ K♠ 7♠ 3♠ 9♣ A♦ K♣
        8♥
```

## PARAMETERS

### -Add

컬렉션에 추가할 속성 값을 지정합니다. 컬렉션에 표시할 순서대로 값을 입력합니다.

```yaml
Type: System.Object[]
Parameter Sets: AddRemoveSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

업데이트할 개체를 지정합니다. 업데이트할 개체를 파이프 할 수도 있습니다 `Update-List` .

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -속성

업데이트 되는 컬렉션을 포함 하는 속성을 지정 합니다. 이 매개 변수를 생략 하면는 개체를 변경 하는 `Update-List` 대신 변경 내용을 나타내는 개체를 반환 합니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Remove

컬렉션에서 제거할 속성 값을 지정합니다.

```yaml
Type: System.Object[]
Parameter Sets: AddRemoveSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Replace

새 컬렉션을 지정합니다. 이 매개 변수는 원래 컬렉션에 있는 모든 항목을 이 매개 변수에 지정된 항목으로 바꿉니다.

```yaml
Type: System.Object[]
Parameter Sets: ReplaceSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.web. PSObject

업데이트할 개체를 파이프 할 수 있습니다 `Update-List` .

## 출력

### Objects 또는 System.object입니다.

`Update-List` 업데이트 된 개체를 반환 하거나 업데이트 작업을 나타내는 개체를 반환 합니다.

## 참고

## 관련 링크

[Format-List](Format-List.md)

[Select-Object](Select-Object.md)

