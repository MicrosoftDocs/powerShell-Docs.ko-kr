---
title: 부록 A - 도움말 구문
description: 이 문서에서는 Get-Help에서 제공하는 cmdlet의 구문을 읽고 이해하는 방법을 설명합니다.
ms.date: 06/02/2020
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: b8fe218f2a9af1ad1ee6b88740414ecede0194bd
ms.sourcegitcommit: df5e6f032ee2d4b556d50406832732d2f7dc2502
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/14/2021
ms.locfileid: "99601828"
---
# <a name="appendix-a---help-syntax"></a><span data-ttu-id="b073f-103">부록 A - 도움말 구문</span><span class="sxs-lookup"><span data-stu-id="b073f-103">Appendix A - Help Syntax</span></span>

<span data-ttu-id="b073f-104">다음 예제에서는 `Get-EventLog` cmdlet 도움말의 **SYNTAX** 섹션을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b073f-104">The following example shows the **SYNTAX** section of the help for the `Get-EventLog` cmdlet.</span></span>

```powershell
help Get-EventLog
```

```Output
NAME
    Get-EventLog

SYNOPSIS
    Gets the events in an event log, or a list of the event logs, on the local or remote
    computers.


SYNTAX
    Get-EventLog [-LogName] <String> [[-InstanceId] <Int64[]>] [-After <DateTime>]
    [-AsBaseObject] [-Before <DateTime>] [-ComputerName <String[]>] [-EntryType {Error |
    Information | FailureAudit | SuccessAudit | Warning}] [-Index <Int32[]>] [-Message
    <String>] [-Newest <Int32>] [-Source <String[]>] [-UserName <String[]>]
    [<CommonParameters>]

    Get-EventLog [-AsString] [-ComputerName <String[]>] [-List] [<CommonParameters>]
```

<span data-ttu-id="b073f-105">이 예제에서는 도움말 중 관련된 부분만 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b073f-105">Only the relevant portion of the help is shown in this example.</span></span>

<span data-ttu-id="b073f-106">구문은 주로 다양한 여는 대괄호와 닫는 대괄호(`[]`) 집합으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="b073f-106">The syntax is primarily made up of several sets of opening and closing brackets (`[]`).</span></span> <span data-ttu-id="b073f-107">이것은 사용 방법에 따라 두 가지 의미를 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="b073f-107">These have two different meanings depending on how they're used.</span></span> <span data-ttu-id="b073f-108">대괄호 안에 있는 모든 항목은 빈 대괄호 집합(`[]`)일 때를 제외하면 모두 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="b073f-108">Anything contained within square brackets is optional unless they're a set of empty square brackets `[]`.</span></span> <span data-ttu-id="b073f-109">빈 대괄호는 `<string[]>` 같은 데이터 유형 뒤에만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b073f-109">Empty square brackets only appear after a datatype such as `<string[]>`.</span></span> <span data-ttu-id="b073f-110">특정 매개 변수가 해당 형식의 값을 두 개 이상 사용할 수 있다는 뜻입니다.</span><span class="sxs-lookup"><span data-stu-id="b073f-110">This means that particular parameter can accept more than one value of that type.</span></span>

<span data-ttu-id="b073f-111">`Get-EventLog`의 첫 번째 매개 변수 집합에 있는 첫 번째 매개 변수는 **LogName** 입니다.</span><span class="sxs-lookup"><span data-stu-id="b073f-111">The first parameter in the first parameter set of `Get-EventLog` is **LogName**.</span></span> <span data-ttu-id="b073f-112">LogName은 대괄호로 묶여 있는데 이는 위치 매개 변수라는 뜻입니다.</span><span class="sxs-lookup"><span data-stu-id="b073f-112">LogName is surrounded by square brackets which means that it's a positional parameter.</span></span> <span data-ttu-id="b073f-113">다시 말해 올바른 위치에 지정되어 있다면 매개 변수 자체의 이름을 지정하는 것은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="b073f-113">In other words, specifying the name of the parameter itself is optional as long as it's specified in the correct position.</span></span> <span data-ttu-id="b073f-114">매개 변수 이름 다음에 있는 꺾쇠 괄호(`<>`)의 정보는 단일 **문자열** 값이 필요함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b073f-114">The information in the angle brackets (`<>`) after the parameter name indicates that it needs a single **string** value.</span></span> <span data-ttu-id="b073f-115">전체 매개 변수 이름과 데이터 유형은 대괄호로 묶여 있지 않으므로 이 매개 변수 집합을 사용할 때는 **LogName** 매개 변수가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="b073f-115">The entire parameter name and datatype are not surrounded by square brackets so the **LogName** parameter is required when using this parameter set.</span></span>

```powershell
Get-EventLog [-LogName] <String>
```

<span data-ttu-id="b073f-116">두 번째 매개 변수는 **InstanceId** 입니다.</span><span class="sxs-lookup"><span data-stu-id="b073f-116">The second parameter is **InstanceId**.</span></span> <span data-ttu-id="b073f-117">매개 변수 이름과 데이터 유형이 모두 대괄호로 묶여 있다는 사실에 주목하세요.</span><span class="sxs-lookup"><span data-stu-id="b073f-117">Notice that the parameter name and the datatype are both completely surrounded by square brackets.</span></span> <span data-ttu-id="b073f-118">**InstanceId** 매개 변수가 필수가 아닌 선택 사항이라는 뜻입니다.</span><span class="sxs-lookup"><span data-stu-id="b073f-118">This means that the **InstanceId** parameter is optional, not mandatory.</span></span> <span data-ttu-id="b073f-119">**InstanceId** 가 자체 대괄호로 묶여 있다는 사실도 주목해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b073f-119">Also notice that **InstanceId** is surrounded by its own set of square brackets.</span></span> <span data-ttu-id="b073f-120">**LogName** 매개 변수처럼 이 매개 변수도 위치적이라는 뜻입니다.</span><span class="sxs-lookup"><span data-stu-id="b073f-120">As with the **LogName** parameter, this means the parameter is positional.</span></span> <span data-ttu-id="b073f-121">데이터 유형 뒤에 마지막 대괄호 집합이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b073f-121">There's one last set of square brackets after the datatype.</span></span> <span data-ttu-id="b073f-122">배열이나 쉼표로 구분된 목록 형태의 값을 두 개 이상 사용할 수 있다는 뜻입니다.</span><span class="sxs-lookup"><span data-stu-id="b073f-122">This means that it can accept more than one value in the form of an array or a comma-separated list.</span></span>

```
[[-InstanceId] <Int64[]>]
```

<span data-ttu-id="b073f-123">두 번째 매개 변수 집합에는 **List** 매개 변수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b073f-123">The second parameter set has a **List** parameter.</span></span> <span data-ttu-id="b073f-124">매개 변수 이름 다음에 데이터 유형이 없기 때문에 스위치 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="b073f-124">It's a switch parameter because there's no datatype following the parameter name.</span></span> <span data-ttu-id="b073f-125">**List** 매개 변수가 지정되었다면 값은 **True** 입니다.</span><span class="sxs-lookup"><span data-stu-id="b073f-125">When the **List** parameter is specified, the value is **True**.</span></span> <span data-ttu-id="b073f-126">지정하지 않았다면 값은 **False** 입니다.</span><span class="sxs-lookup"><span data-stu-id="b073f-126">When it's not specified, the value is **False**.</span></span>

```
[-List]
```

<span data-ttu-id="b073f-127">명령의 구문 정보는 **Syntax** 매개 변수를 사용하는 `Get-Command`로 검색할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b073f-127">The syntax information for a command can also be retrieved using `Get-Command` using the **Syntax** parameter.</span></span> <span data-ttu-id="b073f-128">필자가 자주 사용하는 편리한 지름길입니다.</span><span class="sxs-lookup"><span data-stu-id="b073f-128">This is a handy shortcut that I use all the time.</span></span> <span data-ttu-id="b073f-129">도움말 정보의 여러 페이지를 살펴보지 않고도 명령 사용 방법을 빠르게 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b073f-129">It allows me to quickly learn how to use a command without having to sift through multiple pages of help information.</span></span> <span data-ttu-id="b073f-130">추가 정보가 필요하다면 필자는 다시 실제 도움말 콘텐츠를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b073f-130">If I end up needing more information, then I'll revert to using the actual help content.</span></span>

```powershell
Get-Command -Name Get-EventLog -Syntax
```

```Output
Get-EventLog [-LogName] <string> [[-InstanceId] <long[]>] [-ComputerName <string[]>] [-Newest <int>]
 [-After <datetime>] [-Before <datetime>] [-UserName <string[]>] [-Index <int[]> ]
 [-EntryType <string[]>] [-Source <string[]>] [-Message <string>] [-AsBaseObject]
 [<CommonParameters>]

Get-EventLog [-ComputerName <string[]>] [-List] [-AsString] [<CommonParameters>]
```

<span data-ttu-id="b073f-131">PowerShell에서 도움말 시스템을 많이 사용할수록 미묘한 차이를 쉽게 기억할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b073f-131">The more you use the help system in PowerShell, the easier remembering all of the different nuances becomes.</span></span> <span data-ttu-id="b073f-132">나중에는 거의 무의식적으로 사용할 수 있게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b073f-132">Before you know it, using it becomes second nature.</span></span>
