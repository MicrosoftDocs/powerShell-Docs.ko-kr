---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 11/11/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/update-list?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-List
ms.openlocfilehash: 00ada05f52967c0857cfad63a94cd23c49b69367
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93210497"
---
# <span data-ttu-id="e4c83-103">Update-List</span><span class="sxs-lookup"><span data-stu-id="e4c83-103">Update-List</span></span>

## <span data-ttu-id="e4c83-104">개요</span><span class="sxs-lookup"><span data-stu-id="e4c83-104">SYNOPSIS</span></span>
<span data-ttu-id="e4c83-105">개체 컬렉션을 포함하는 속성 값에 항목을 추가하거나 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="e4c83-105">Adds items to and removes items from a property value that contains a collection of objects.</span></span>

## <span data-ttu-id="e4c83-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e4c83-106">SYNTAX</span></span>

### <span data-ttu-id="e4c83-107">AddRemoveSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="e4c83-107">AddRemoveSet (Default)</span></span>

```
Update-List [-Add <Object[]>] [-Remove <Object[]>] [-InputObject <PSObject>] [[-Property] <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="e4c83-108">ReplaceSet</span><span class="sxs-lookup"><span data-stu-id="e4c83-108">ReplaceSet</span></span>

```
Update-List -Replace <Object[]> [-InputObject <PSObject>] [[-Property] <String>] [<CommonParameters>]
```

## <span data-ttu-id="e4c83-109">설명</span><span class="sxs-lookup"><span data-stu-id="e4c83-109">DESCRIPTION</span></span>

<span data-ttu-id="e4c83-110">`Update-List`Cmdlet은 개체의 속성 값에 있는 항목을 추가, 제거 또는 바꾸고 업데이트 된 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4c83-110">The `Update-List` cmdlet adds, removes, or replaces items in a property value of an object and returns the updated object.</span></span> <span data-ttu-id="e4c83-111">이 cmdlet은 개체 컬렉션을 포함하는 속성에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e4c83-111">This cmdlet is designed for properties that contain collections of objects.</span></span>

<span data-ttu-id="e4c83-112">**Add** 및 **remove** 매개 변수는 컬렉션에서 개별 항목을 추가 하 고 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4c83-112">The **Add** and **Remove** parameters add individual items to and remove them from the collection.</span></span>
<span data-ttu-id="e4c83-113">**Replace** 매개 변수는 전체 컬렉션을 대체 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4c83-113">The **Replace** parameter replaces the entire collection.</span></span>

<span data-ttu-id="e4c83-114">명령에서 속성을 지정 하지 않으면에서 개체를 업데이트 하는 `Update-List` 대신 업데이트를 설명 하는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4c83-114">If you do not specify a property in the command, `Update-List` returns an object that describes the update instead of updating the object.</span></span> <span data-ttu-id="e4c83-115">Cmdlet과 같은 개체를 변경 하는 cmdlet에 업데이트 개체를 제출할 수 있습니다 `Set` .</span><span class="sxs-lookup"><span data-stu-id="e4c83-115">You can submit the update object to cmdlets that change objects, such as `Set` cmdlets.</span></span>

<span data-ttu-id="e4c83-116">이 cmdlet은 업데이트 되는 속성이를 사용 하는 **IList** 인터페이스를 지 원하는 경우에만 작동 `Update-List` 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4c83-116">This cmdlet works only when the property that is being updated supports the **IList** interface that `Update-List` uses.</span></span> <span data-ttu-id="e4c83-117">또한 업데이트를 `Set` 수락 하는 모든 cmdlet은 **IList** 인터페이스를 지원 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4c83-117">Also, any `Set` cmdlets that accept an update must support the **IList** interface.</span></span>

<span data-ttu-id="e4c83-118">PowerShell과 함께 설치 된 핵심 cmdlet은이 인터페이스를 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e4c83-118">The core cmdlets that are installed with PowerShell do not support this interface.</span></span> <span data-ttu-id="e4c83-119">Cmdlet이를 지원 하는지 확인 하려면 `Update-List` Cmdlet 도움말 항목을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e4c83-119">To determine whether a cmdlet supports `Update-List`, see the cmdlet Help topic.</span></span>

<span data-ttu-id="e4c83-120">이 cmdlet은 PowerShell 7에서 다시 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e4c83-120">This cmdlet was reintroduced in PowerShell 7.</span></span>

## <span data-ttu-id="e4c83-121">예제</span><span class="sxs-lookup"><span data-stu-id="e4c83-121">EXAMPLES</span></span>

### <span data-ttu-id="e4c83-122">예제 1: 속성 값에 항목 추가</span><span class="sxs-lookup"><span data-stu-id="e4c83-122">Example 1: Add items to a property value</span></span>

<span data-ttu-id="e4c83-123">이 예제에서는 카드가 **목록** 컬렉션 개체로 저장 되는 카드의 데크를 나타내는 클래스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e4c83-123">In this example we create a class that represents a deck of cards where the cards are stored as a **List** collection object.</span></span> <span data-ttu-id="e4c83-124">**Newdeck ()** 메서드는 `Update-List` 를 사용 하 여 카드 컬렉션에 카드 값의 전체 **cards** 데크를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4c83-124">The **NewDeck()** method uses `Update-List`to add a complete deck of card values to the **cards** collection.</span></span>

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
> <span data-ttu-id="e4c83-125">`Update-List`Cmdlet은 업데이트 된 개체를 파이프라인으로 출력 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4c83-125">The `Update-List` cmdlet outputs the updated object to the pipeline.</span></span> <span data-ttu-id="e4c83-126">출력을로 파이프 하 여 `Out-Null` 원치 않는 표시를 표시 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e4c83-126">We pipe the output to `Out-Null` to suppress the unwanted display.</span></span>

### <span data-ttu-id="e4c83-127">예제 2: 컬렉션 속성 항목 추가 및 제거</span><span class="sxs-lookup"><span data-stu-id="e4c83-127">Example 2: Add and remove items of a collection property</span></span>

<span data-ttu-id="e4c83-128">예 1의 코드를 계속 진행 하면 카드 클래스의 인스턴스를 만들어 **카드의** 데크와 두 플레이어가 보유 한 카드를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e4c83-128">Continuing with the code in Example 1, we will create instances of the **Cards** class to represent a deck of cards and the cards held by two players.</span></span> <span data-ttu-id="e4c83-129">Cmdlet을 사용 `Update-List` 하 여 플레이어의 손으로 카드를 추가 하 고 데크에서 카드를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4c83-129">We use the `Update-List` cmdlet to add cards to the players' hands and to remove cards from the deck.</span></span>

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

<span data-ttu-id="e4c83-130">출력은 카드가 플레이어에 처리 되기 전의 데크 상태를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e4c83-130">The output shows the state of the deck before the cards were dealt to the players.</span></span> <span data-ttu-id="e4c83-131">각 플레이어가 데크에서 5 개의 카드를 수신 하는 것을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4c83-131">You can see that each player received five cards from the deck.</span></span> <span data-ttu-id="e4c83-132">최종 출력은 플레이어에 카드를 처리 한 후 데크 상태를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e4c83-132">The final output shows the state of the deck after dealing the cards to the players.</span></span> <span data-ttu-id="e4c83-133">`Update-List` 는 데크에서 카드를 선택 하 여 플레이어의 컬렉션에 추가 하는 데 사용 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e4c83-133">`Update-List` was used to select the cards from the deck and add them to the players' collection.</span></span> <span data-ttu-id="e4c83-134">그런 다음를 사용 하 여 플레이어의 카드를 데크에서 제거 했습니다 `Update-List` .</span><span class="sxs-lookup"><span data-stu-id="e4c83-134">Then the players' cards were removed from the deck using `Update-List`.</span></span>

### <span data-ttu-id="e4c83-135">예제 3: 단일 명령에서 항목 추가 및 제거</span><span class="sxs-lookup"><span data-stu-id="e4c83-135">Example 3: Add and remove items in a single command</span></span>

<span data-ttu-id="e4c83-136">`Update-List` 단일 명령에 **추가** 및 **제거** 매개 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4c83-136">`Update-List` allows you to use the **Add** and **Remove** parameters in a single command.</span></span> <span data-ttu-id="e4c83-137">이 예에서 플레이어 1은 및를 삭제 하 `4♦` `6♦` 고 두 개의 새 카드를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="e4c83-137">In this example, Player 1 wants to discard the `4♦` and `6♦` and get two new cards.</span></span>

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

## <span data-ttu-id="e4c83-138">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e4c83-138">PARAMETERS</span></span>

### <span data-ttu-id="e4c83-139">-Add</span><span class="sxs-lookup"><span data-stu-id="e4c83-139">-Add</span></span>

<span data-ttu-id="e4c83-140">컬렉션에 추가할 속성 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e4c83-140">Specifies the property values to be added to the collection.</span></span> <span data-ttu-id="e4c83-141">컬렉션에 표시할 순서대로 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e4c83-141">Enter the values in the order that they should appear in the collection.</span></span>

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

### <span data-ttu-id="e4c83-142">-InputObject</span><span class="sxs-lookup"><span data-stu-id="e4c83-142">-InputObject</span></span>

<span data-ttu-id="e4c83-143">업데이트할 개체를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e4c83-143">Specifies the objects to be updated.</span></span> <span data-ttu-id="e4c83-144">업데이트할 개체를 파이프 할 수도 있습니다 `Update-List` .</span><span class="sxs-lookup"><span data-stu-id="e4c83-144">You can also pipe the object to be updated to `Update-List`.</span></span>

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

### <span data-ttu-id="e4c83-145">-속성</span><span class="sxs-lookup"><span data-stu-id="e4c83-145">-Property</span></span>

<span data-ttu-id="e4c83-146">업데이트 되는 컬렉션을 포함 하는 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4c83-146">Specifies the property that contains the collection that is being updated.</span></span> <span data-ttu-id="e4c83-147">이 매개 변수를 생략 하면는 개체를 변경 하는 `Update-List` 대신 변경 내용을 나타내는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4c83-147">If you omit this parameter, `Update-List` returns an object that represents the change instead of changing the object.</span></span>

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

### <span data-ttu-id="e4c83-148">-Remove</span><span class="sxs-lookup"><span data-stu-id="e4c83-148">-Remove</span></span>

<span data-ttu-id="e4c83-149">컬렉션에서 제거할 속성 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e4c83-149">Specifies the property values to be removed from the collection.</span></span>

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

### <span data-ttu-id="e4c83-150">-Replace</span><span class="sxs-lookup"><span data-stu-id="e4c83-150">-Replace</span></span>

<span data-ttu-id="e4c83-151">새 컬렉션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e4c83-151">Specifies a new collection.</span></span> <span data-ttu-id="e4c83-152">이 매개 변수는 원래 컬렉션에 있는 모든 항목을 이 매개 변수에 지정된 항목으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="e4c83-152">This parameter replaces all items in the original collection with the items specified by this parameter.</span></span>

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

### <span data-ttu-id="e4c83-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e4c83-153">CommonParameters</span></span>

<span data-ttu-id="e4c83-154">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e4c83-154">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e4c83-155">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e4c83-155">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e4c83-156">입력</span><span class="sxs-lookup"><span data-stu-id="e4c83-156">INPUTS</span></span>

### <span data-ttu-id="e4c83-157">System.web. PSObject</span><span class="sxs-lookup"><span data-stu-id="e4c83-157">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="e4c83-158">업데이트할 개체를 파이프 할 수 있습니다 `Update-List` .</span><span class="sxs-lookup"><span data-stu-id="e4c83-158">You can pipe the objects to be updated to `Update-List`.</span></span>

## <span data-ttu-id="e4c83-159">출력</span><span class="sxs-lookup"><span data-stu-id="e4c83-159">OUTPUTS</span></span>

### <span data-ttu-id="e4c83-160">Objects 또는 System.object입니다.</span><span class="sxs-lookup"><span data-stu-id="e4c83-160">Objects or System.Management.Automation.PSListModifier</span></span>

<span data-ttu-id="e4c83-161">`Update-List` 업데이트 된 개체를 반환 하거나 업데이트 작업을 나타내는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4c83-161">`Update-List` returns the updated object, or it returns an object that represents the update action.</span></span>

## <span data-ttu-id="e4c83-162">참고</span><span class="sxs-lookup"><span data-stu-id="e4c83-162">NOTES</span></span>

## <span data-ttu-id="e4c83-163">관련 링크</span><span class="sxs-lookup"><span data-stu-id="e4c83-163">RELATED LINKS</span></span>

[<span data-ttu-id="e4c83-164">Format-List</span><span class="sxs-lookup"><span data-stu-id="e4c83-164">Format-List</span></span>](Format-List.md)

[<span data-ttu-id="e4c83-165">Select-Object</span><span class="sxs-lookup"><span data-stu-id="e4c83-165">Select-Object</span></span>](Select-Object.md)
