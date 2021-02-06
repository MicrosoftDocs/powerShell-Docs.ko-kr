---
description: 조건부 테스트의 결과에 따라 명령 블록을 실행 하는 데 사용할 수 있는 언어 문에 대해 설명 합니다.
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_while?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_While
ms.openlocfilehash: 37c277a5919ba5fc39f953e05edaf58d159f3e7c
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99600846"
---
# <a name="about-while"></a><span data-ttu-id="9fd2f-103">While 정보</span><span class="sxs-lookup"><span data-stu-id="9fd2f-103">About While</span></span>

## <a name="short-description"></a><span data-ttu-id="9fd2f-104">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="9fd2f-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="9fd2f-105">조건부 테스트의 결과에 따라 명령 블록을 실행 하는 데 사용할 수 있는 언어 문에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fd2f-105">Describes a language statement that you can use to run a command block based on the results of a conditional test.</span></span>

## <a name="long-description"></a><span data-ttu-id="9fd2f-106">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="9fd2f-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="9fd2f-107">While 문 (While 루프 라고도 함)은 조건부 테스트가 true로 평가 되는 한 명령 블록에서 명령을 실행 하는 루프를 만들기 위한 언어 구문입니다.</span><span class="sxs-lookup"><span data-stu-id="9fd2f-107">The While statement (also known as a While loop) is a language construct for creating a loop that runs commands in a command block as long as a conditional test evaluates to true.</span></span> <span data-ttu-id="9fd2f-108">While 문은 구문이 더 복잡 하기 때문에 For 문 보다 생성 하기가 더 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="9fd2f-108">The While statement is easier to construct than a For statement because its syntax is less complicated.</span></span> <span data-ttu-id="9fd2f-109">또한 While 문에서 조건부 테스트를 지정 하 여 루프가 실행 되는 횟수를 제어 하므로 Foreach 문 보다 유연성이 높습니다.</span><span class="sxs-lookup"><span data-stu-id="9fd2f-109">In addition, it is more flexible than the Foreach statement because you specify a conditional test in the While statement to control how many times the loop runs.</span></span>

<span data-ttu-id="9fd2f-110">다음은 While 문 구문을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9fd2f-110">The following shows the While statement syntax:</span></span>

```powershell
while (<condition>){<statement list>}
```

<span data-ttu-id="9fd2f-111">While 문을 실행 하는 경우 PowerShell은 섹션을 `<condition>` 시작 하기 전에 문의 섹션을 평가 합니다 `<statement list>` .</span><span class="sxs-lookup"><span data-stu-id="9fd2f-111">When you run a While statement, PowerShell evaluates the `<condition>` section of the statement before entering the `<statement list>` section.</span></span> <span data-ttu-id="9fd2f-112">문의 조건 부분은 true 또는 false로 확인 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fd2f-112">The condition portion of the statement resolves to either true or false.</span></span> <span data-ttu-id="9fd2f-113">조건이 true로 유지 되는 한 PowerShell은 섹션을 다시 활성화 합니다 `<statement list>` .</span><span class="sxs-lookup"><span data-stu-id="9fd2f-113">As long as the condition remains true, PowerShell reruns the `<statement list>` section.</span></span>

<span data-ttu-id="9fd2f-114">`<statement list>`문의 섹션에는 루프가 입력 되거나 반복 될 때마다 실행 되는 명령이 하나 이상 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fd2f-114">The `<statement list>` section of the statement contains one or more commands that are run each time the loop is entered or repeated.</span></span>

<span data-ttu-id="9fd2f-115">예를 들어 다음 While 문에는 $val 변수가 만들어지지 않았거나 $val 변수가 생성 되 고 0으로 초기화 된 경우 1에서 3 까지의 숫자가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fd2f-115">For example, the following While statement displays the numbers 1 through 3 if the $val variable has not been created or if the $val variable has been created and initialized to 0.</span></span>

```powershell
while($val -ne 3)
{
    $val++
    Write-Host $val
}
```

<span data-ttu-id="9fd2f-116">이 예제에서 조건 ($val 3과 같지 않음)은 true ( \= 0, 1, 2 $val)입니다.</span><span class="sxs-lookup"><span data-stu-id="9fd2f-116">In this example, the condition ($val is not equal to 3) is true while $val \= 0, 1, 2.</span></span> <span data-ttu-id="9fd2f-117">루프가 반복 될 때마다 $val \+ \+ 단항 증가 연산자 ($val)를 사용 하 여 1 씩 증가 \+ \+ 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fd2f-117">Each time through the loop, $val is incremented by 1 using the \+\+ unary increment operator ($val\+\+).</span></span> <span data-ttu-id="9fd2f-118">루프를 마지막으로 수행한 후에는 $val \= 3입니다.</span><span class="sxs-lookup"><span data-stu-id="9fd2f-118">The last time through the loop, $val \= 3.</span></span> <span data-ttu-id="9fd2f-119">$Val이 3 이면 condition 문이 false로 계산 되 고 루프가 종료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fd2f-119">When $val equals 3, the condition statement evaluates to false, and the loop exits.</span></span>

<span data-ttu-id="9fd2f-120">PowerShell 명령 프롬프트에서이 명령을 편리 하 게 작성 하려면 다음과 같은 방법으로 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fd2f-120">To conveniently write this command at the PowerShell command prompt, you can enter it in the following way:</span></span>

```powershell
while($val -ne 3){$val++; Write-Host $val}
```

<span data-ttu-id="9fd2f-121">세미콜론은 $val 값을 콘솔에 기록 하는 두 번째 명령에서 $val 1을 추가 하는 첫 번째 명령을 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fd2f-121">Notice that the semicolon separates the first command that adds 1 to $val from the second command that writes the value of $val to the console.</span></span>

## <a name="see-also"></a><span data-ttu-id="9fd2f-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9fd2f-122">SEE ALSO</span></span>

[<span data-ttu-id="9fd2f-123">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="9fd2f-123">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="9fd2f-124">about_Do</span><span class="sxs-lookup"><span data-stu-id="9fd2f-124">about_Do</span></span>](about_Do.md)

[<span data-ttu-id="9fd2f-125">about_Foreach</span><span class="sxs-lookup"><span data-stu-id="9fd2f-125">about_Foreach</span></span>](about_Foreach.md)

[<span data-ttu-id="9fd2f-126">about_For</span><span class="sxs-lookup"><span data-stu-id="9fd2f-126">about_For</span></span>](about_For.md)

[<span data-ttu-id="9fd2f-127">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="9fd2f-127">about_Language_Keywords</span></span>](about_Language_Keywords.md)

