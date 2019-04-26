---
title: Cmdlet 매개 변수에서 와일드 카드 문자를 지 원하는 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- wildcards [PowerShell Programmer's Guide]
- parameters [PowerShell Programmer's Guide], wildcards
ms.assetid: 9b26e1e9-9350-4a5a-aad5-ddcece658d93
caps.latest.revision: 12
ms.openlocfilehash: 6c762d3889bc4b649252390625525db4735f4c1d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067402"
---
# <a name="supporting-wildcard-characters-in-cmdlet-parameters"></a><span data-ttu-id="cfbd0-102">Cmdlet 매개 변수에서 와일드카드 문자 지원</span><span class="sxs-lookup"><span data-stu-id="cfbd0-102">Supporting Wildcard Characters in Cmdlet Parameters</span></span>

<span data-ttu-id="cfbd0-103">종종 단일 리소스 아닌 리소스 그룹에 대해 실행 하는 cmdlet를 디자인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cfbd0-103">Often, you will have to design a cmdlet to run against a group of resources rather than against a single resource.</span></span> <span data-ttu-id="cfbd0-104">예를 들어 cmdlet 이름이 없거나 확장 하는 데이터 저장소에서 모든 파일을 찾을 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cfbd0-104">For example, a cmdlet might need to locate all the files in a data store that have the same name or extension.</span></span> <span data-ttu-id="cfbd0-105">리소스 그룹에 대해 실행 되는 cmdlet를 디자인할 때 와일드 카드 문자를 지원 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cfbd0-105">You must provide support for wildcard characters when you design a cmdlet that will be run against a group of resources.</span></span>

> [!NOTE]
> <span data-ttu-id="cfbd0-106">와일드 카드 문자를 사용 하는 경우에 따라 라고도 *와일드 카드 사용*합니다.</span><span class="sxs-lookup"><span data-stu-id="cfbd0-106">Using wildcard characters is sometimes referred to as *globbing*.</span></span>

## <a name="windows-powershell-cmdlets-that-use-wildcards"></a><span data-ttu-id="cfbd0-107">와일드 카드를 사용 하는 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="cfbd0-107">Windows PowerShell Cmdlets That Use Wildcards</span></span>

 <span data-ttu-id="cfbd0-108">많은 Windows PowerShell cmdlet의 매개 변수 값에 대 한 와일드 카드 문자를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="cfbd0-108">Many Windows PowerShell cmdlets support wildcard characters for their parameter values.</span></span> <span data-ttu-id="cfbd0-109">예를 들어, 거의 모든 cmdlet는에 `Name` 또는 `Path` 매개 변수는 이러한 매개 변수에 대 한 와일드 카드 문자를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="cfbd0-109">For example, almost every cmdlet that has a `Name` or `Path` parameter supports wildcard characters for these parameters.</span></span> <span data-ttu-id="cfbd0-110">(하지만 있는 대부분의 cmdlet을 `Path` 매개 변수 수도 `LiteralPath` 와일드 카드 문자를 지원 하지 않는 매개 변수.) 다음 명령을 Get 동사를 포함 하는 이름이 현재 세션의 모든 cmdlet을 반환 하려면 와일드 카드 문자는 사용 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="cfbd0-110">(Although most cmdlets that have a `Path` parameter also have a `LiteralPath` parameter that does not support wildcard characters.) The following command shows how a wildcard character is used to return all the cmdlets in the current session whose name contains the Get verb.</span></span>

 <span data-ttu-id="cfbd0-111">**PS > get 명령을 get-\***</span><span class="sxs-lookup"><span data-stu-id="cfbd0-111">**PS>get-command get-\***</span></span>

## <a name="supported-wildcard-characters"></a><span data-ttu-id="cfbd0-112">지원 되는 와일드 카드 문자</span><span class="sxs-lookup"><span data-stu-id="cfbd0-112">Supported Wildcard Characters</span></span>

<span data-ttu-id="cfbd0-113">Windows PowerShell 와일드 카드 문자를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="cfbd0-113">Windows PowerShell supports the following wildcard characters.</span></span>

|<span data-ttu-id="cfbd0-114">와일드 카드 문자</span><span class="sxs-lookup"><span data-stu-id="cfbd0-114">Wildcard character</span></span>|<span data-ttu-id="cfbd0-115">설명</span><span class="sxs-lookup"><span data-stu-id="cfbd0-115">Description</span></span>|<span data-ttu-id="cfbd0-116">예제</span><span class="sxs-lookup"><span data-stu-id="cfbd0-116">Example</span></span>|<span data-ttu-id="cfbd0-117">일치 항목</span><span class="sxs-lookup"><span data-stu-id="cfbd0-117">Matches</span></span>|<span data-ttu-id="cfbd0-118">일치 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cfbd0-118">Does not match</span></span>|
|------------------------|-----------------|-------------|-------------|--------------------|
|*|<span data-ttu-id="cfbd0-119">지정 된 위치 에서부터 0 개 이상의 문자 일치</span><span class="sxs-lookup"><span data-stu-id="cfbd0-119">Matches zero or more characters, starting at the specified position</span></span>|<span data-ttu-id="cfbd0-120">a\*</span><span class="sxs-lookup"><span data-stu-id="cfbd0-120">a\*</span></span>|<span data-ttu-id="cfbd0-121">Apple ag</span><span class="sxs-lookup"><span data-stu-id="cfbd0-121">A, ag, Apple</span></span>||
|<span data-ttu-id="cfbd0-122">?</span><span class="sxs-lookup"><span data-stu-id="cfbd0-122">?</span></span>|<span data-ttu-id="cfbd0-123">지정된 된 위치에 문자 일치</span><span class="sxs-lookup"><span data-stu-id="cfbd0-123">Matches anycharacter at the specified position</span></span>|<span data-ttu-id="cfbd0-124">? n</span><span class="sxs-lookup"><span data-stu-id="cfbd0-124">?n</span></span>|<span data-ttu-id="cfbd0-125">프로그램에서는,에서</span><span class="sxs-lookup"><span data-stu-id="cfbd0-125">An, in, on</span></span>|<span data-ttu-id="cfbd0-126">실행</span><span class="sxs-lookup"><span data-stu-id="cfbd0-126">ran</span></span>|
|<span data-ttu-id="cfbd0-127">[ ]</span><span class="sxs-lookup"><span data-stu-id="cfbd0-127">[ ]</span></span>|<span data-ttu-id="cfbd0-128">다양 한 문자 일치</span><span class="sxs-lookup"><span data-stu-id="cfbd0-128">Matches a range of characters</span></span>|<span data-ttu-id="cfbd0-129">[a-l]ook</span><span class="sxs-lookup"><span data-stu-id="cfbd0-129">[a-l]ook</span></span>|<span data-ttu-id="cfbd0-130">책, 쿡, 모양</span><span class="sxs-lookup"><span data-stu-id="cfbd0-130">book, cook, look</span></span>|<span data-ttu-id="cfbd0-131">수행한</span><span class="sxs-lookup"><span data-stu-id="cfbd0-131">took</span></span>|
|<span data-ttu-id="cfbd0-132">[ ]</span><span class="sxs-lookup"><span data-stu-id="cfbd0-132">[ ]</span></span>|<span data-ttu-id="cfbd0-133">지정된 된 문자 일치</span><span class="sxs-lookup"><span data-stu-id="cfbd0-133">Matches the specified characters</span></span>|<span data-ttu-id="cfbd0-134">[bc]ook</span><span class="sxs-lookup"><span data-stu-id="cfbd0-134">[bc]ook</span></span>|<span data-ttu-id="cfbd0-135">서적, 쿡</span><span class="sxs-lookup"><span data-stu-id="cfbd0-135">book, cook</span></span>|<span data-ttu-id="cfbd0-136">look</span><span class="sxs-lookup"><span data-stu-id="cfbd0-136">look</span></span>|

<span data-ttu-id="cfbd0-137">와일드 카드 문자를 지 원하는 cmdlet를 디자인할 때 와일드 카드 문자 조합을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="cfbd0-137">When you design cmdlets that support wildcard characters, allow for combinations of wildcard characters.</span></span> <span data-ttu-id="cfbd0-138">예를 들어, 다음 명령을 사용 하 여 `Get-ChildItem` c:\Techdocs 폴더에 있으며 문자로 시작 하는 "a"부터 "l." 모든.txt 파일을 검색 하기 위한 cmdlet</span><span class="sxs-lookup"><span data-stu-id="cfbd0-138">For example, the following command uses the `Get-ChildItem` cmdlet to retrieve all the .txt files that are in the c:\Techdocs folder and that begin with the letters "a" through "l."</span></span>

<span data-ttu-id="cfbd0-139">**get-childitem c:\techdocs\\[a-l]\*.txt**</span><span class="sxs-lookup"><span data-stu-id="cfbd0-139">**get-childitem c:\techdocs\\[a-l]\*.txt**</span></span>

<span data-ttu-id="cfbd0-140">이전 명령은 범위 와일드 카드 **[a-l]** "a"부터 "l." 파일 이름은 문자로 시작 해야를 지정 하려면</span><span class="sxs-lookup"><span data-stu-id="cfbd0-140">The previous command uses the range wildcard **[a-l]** to specify that the file name should begin with the characters "a" through "l."</span></span> <span data-ttu-id="cfbd0-141">다음 명령은 \* 파일 이름의 첫 번째 문자와.txt 확장명 사이 있는 문자에 대 한 자리 표시자로 와일드 카드 문자입니다.</span><span class="sxs-lookup"><span data-stu-id="cfbd0-141">The command then uses the \* wildcard character as a placeholder for any characters between the first letter of the file name and the .txt extension.</span></span>

<span data-ttu-id="cfbd0-142">다음 예제에서는 "d" 문자를 제외 하지만 "a"부터 "f." 다른 모든 문자를 포함 하는 범위 와일드 카드 패턴</span><span class="sxs-lookup"><span data-stu-id="cfbd0-142">The following example uses a range wildcard pattern that excludes the letter "d" but includes all the other letters from "a" through "f."</span></span>

<span data-ttu-id="cfbd0-143">**get-childitem c:\techdocs\\[a-cef]\*.txt**</span><span class="sxs-lookup"><span data-stu-id="cfbd0-143">**get-childitem c:\techdocs\\[a-cef]\*.txt**</span></span>

## <a name="handling-literal-characters-in-wildcard-patterns"></a><span data-ttu-id="cfbd0-144">와일드 카드 패턴의 리터럴 문자를 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="cfbd0-144">Handling Literal Characters in Wildcard Patterns</span></span>

<span data-ttu-id="cfbd0-145">지정한 와일드 카드 패턴 리터럴 문자열을 포함 하는 경우 억음 악센트 문자 (') 이스케이프 문자로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="cfbd0-145">If the wildcard pattern you specify contains literal characters, use the backtick character (\`) as an escape character.</span></span> <span data-ttu-id="cfbd0-146">리터럴 문자를 프로그래밍 방식으로 지정 하는 경우 단일 억음 악센트 기호를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="cfbd0-146">When you specify literal characters programmatically, use a single backtick.</span></span> <span data-ttu-id="cfbd0-147">명령 프롬프트에서 리터럴 문자를 지정 하는 경우에 두 개의 backtick을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="cfbd0-147">When you specify literal characters at the command prompt, use two backticks.</span></span> <span data-ttu-id="cfbd0-148">예를 들어, 다음 패턴에 문자 그대로 수행 해야 하는 두 개의 대괄호가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cfbd0-148">For example, the following pattern contains two brackets that must be taken literally.</span></span>

<span data-ttu-id="cfbd0-149">"John Smith \`[\*']" (프로그래밍 방식으로 지정)</span><span class="sxs-lookup"><span data-stu-id="cfbd0-149">"John Smith \`[\*\`]" (specified programmatically)</span></span>

<span data-ttu-id="cfbd0-150">"John Smith \` \`[\*\`']" (명령 프롬프트에서 지정 됨)</span><span class="sxs-lookup"><span data-stu-id="cfbd0-150">"John Smith \`\`[\*\`\`]"  (specified at the command prompt)</span></span>

<span data-ttu-id="cfbd0-151">이 패턴에는 "John Smith [마케팅]" 또는 "John Smith [개발]"와 일치합니다.</span><span class="sxs-lookup"><span data-stu-id="cfbd0-151">This pattern matches "John Smith [Marketing]" or "John Smith [Development]".</span></span>

## <a name="cmdlet-output-and-wildcard-characters"></a><span data-ttu-id="cfbd0-152">Cmdlet 출력 및 와일드 카드 문자</span><span class="sxs-lookup"><span data-stu-id="cfbd0-152">Cmdlet Output and Wildcard Characters</span></span>

<span data-ttu-id="cfbd0-153">Cmdlet 매개 변수는 와일드 카드 문자를 지원 하는 경우 cmdlet은 작업을 일반적으로 배열 출력을 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="cfbd0-153">When cmdlet parameters support wildcard characters, a cmdlet operation usually generates an array output.</span></span> <span data-ttu-id="cfbd0-154">경우에 따라이 의미가 없습니다 사용자는 한 번에 하나의 항목만 사용할 수 있으므로 출력 배열을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="cfbd0-154">Occasionally, it makes no sense to support an array output because the user might use only a single item at a time.</span></span> <span data-ttu-id="cfbd0-155">예를 들어를 `Set-Location` cmdlet은 사용자만 단일 위치를 설정 하기 때문에 출력 배열을 지원지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cfbd0-155">For example, the `Set-Location` cmdlet does support an array output because the user sets only a single location.</span></span> <span data-ttu-id="cfbd0-156">이 예에서는 cmdlet을 계속 와일드 카드 문자를 지원 하지만 단일 위치를 확인 하 게 하기.</span><span class="sxs-lookup"><span data-stu-id="cfbd0-156">In this instance, the cmdlet still supports wildcard characters, but it forces resolution to a single location.</span></span>

## <a name="see-also"></a><span data-ttu-id="cfbd0-157">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cfbd0-157">See Also</span></span>

<span data-ttu-id="cfbd0-158">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="cfbd0-158">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>

[<span data-ttu-id="cfbd0-159">WildcardPattern 클래스</span><span class="sxs-lookup"><span data-stu-id="cfbd0-159">WildcardPattern Class</span></span>](/dotnet/api/system.management.automation.wildcardpattern)
