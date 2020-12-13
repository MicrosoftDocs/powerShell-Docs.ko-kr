---
ms.date: 09/13/2016
ms.topic: reference
title: PowerShell cmdlet에 대한 도움말 작성
description: PowerShell cmdlet에 대한 도움말 작성
ms.openlocfilehash: b1deaa5998dbc54add93764db785d57afcc0a779
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92658109"
---
# <a name="writing-help-for-powershell-cmdlets"></a><span data-ttu-id="63f68-103">PowerShell cmdlet에 대한 도움말 작성</span><span class="sxs-lookup"><span data-stu-id="63f68-103">Writing Help for PowerShell Cmdlets</span></span>

<span data-ttu-id="63f68-104">PowerShell cmdlet은 유용할 수 있지만, 도움말 항목에서 cmdlet이 수행 하는 작업 및 사용 방법에 대해 명확 하 게 설명 하지 않는 한, cmdlet을 사용 하지 못할 수도 있습니다. 그렇지 않으면 사용자가 불편 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63f68-104">PowerShell cmdlets can be useful, but unless your Help topics clearly explain what the cmdlet does and how to use it, the cmdlet may not get used or, even worse, it might frustrate users.</span></span> <span data-ttu-id="63f68-105">XML 기반 cmdlet 도움말 파일 형식을 사용 하면 일관성을 향상 시킬 수 있지만 매우 많은 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="63f68-105">The XML-based cmdlet Help file format enhances consistency, but great help requires much more.</span></span>

<span data-ttu-id="63f68-106">Cmdlet 도움말을 작성 한 적이 없는 경우에는 다음 지침을 검토 하세요.</span><span class="sxs-lookup"><span data-stu-id="63f68-106">If you have never written cmdlet Help, review the following guidelines.</span></span> <span data-ttu-id="63f68-107">다음 섹션에서는 cmdlet 도움말 항목을 작성 하는 데 필요한 XML 스키마에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="63f68-107">The XML schema required to author the cmdlet Help topic is described in the following section.</span></span> <span data-ttu-id="63f68-108">[Cmdlet 도움말 파일을 만드는](./how-to-create-the-cmdlet-help-file.md)것으로 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="63f68-108">Start with [Creating the Cmdlet Help File](./how-to-create-the-cmdlet-help-file.md).</span></span> <span data-ttu-id="63f68-109">이 항목에는 최상위 XML 노드에 대 한 설명이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63f68-109">That topic includes a description of the top-level XML nodes.</span></span>

## <a name="writing-guidelines-for-cmdlet-help"></a><span data-ttu-id="63f68-110">Cmdlet 도움말 작성 지침</span><span class="sxs-lookup"><span data-stu-id="63f68-110">Writing Guidelines for Cmdlet Help</span></span>

### <a name="write-well"></a><span data-ttu-id="63f68-111">쓰기 웰</span><span class="sxs-lookup"><span data-stu-id="63f68-111">Write well</span></span>

<span data-ttu-id="63f68-112">잘 작성 된 항목은 아무 것도 대체 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="63f68-112">Nothing replaces a well-written topic.</span></span> <span data-ttu-id="63f68-113">전문 작성자가 아닌 경우 도움이 되는 작성기 또는 편집기를 찾으십시오.</span><span class="sxs-lookup"><span data-stu-id="63f68-113">If you are not a professional writer, find a writer or editor to help you.</span></span> <span data-ttu-id="63f68-114">다른 대안은 도움말 텍스트를 Microsoft Word로 복사 하 고 문법 및 맞춤법 검사를 사용 하 여 작업을 개선 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="63f68-114">Another alternative is to copy your Help text into Microsoft Word and use the grammar and spelling checks to improve your work.</span></span>

### <a name="write-simply"></a><span data-ttu-id="63f68-115">쓰기 간단히</span><span class="sxs-lookup"><span data-stu-id="63f68-115">Write simply</span></span>

<span data-ttu-id="63f68-116">간단한 단어와 구를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="63f68-116">Use simple words and phrases.</span></span> <span data-ttu-id="63f68-117">전문 용어를 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="63f68-117">Avoid jargon.</span></span> <span data-ttu-id="63f68-118">대부분의 판독기는 외국어 사전과 도움말 항목에만 포함 되어 있다고 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="63f68-118">Consider that many readers are equipped only with a foreign-language dictionary and your Help topic.</span></span>

### <a name="write-consistently"></a><span data-ttu-id="63f68-119">일관 되 게 쓰기</span><span class="sxs-lookup"><span data-stu-id="63f68-119">Write consistently</span></span>

<span data-ttu-id="63f68-120">관련 cmdlet에 대 한 도움말은 유사 해야 합니다 (예: get x 및 set-x).</span><span class="sxs-lookup"><span data-stu-id="63f68-120">Help for related cmdlets should be similar (for example, get-x and set-x).</span></span> <span data-ttu-id="63f68-121">**Force** 및 **InputObject** 와 같은 표준 매개 변수에 대 한 표준 설명을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="63f68-121">Use the standard descriptions for standard parameters, like **Force** and **InputObject**.</span></span> <span data-ttu-id="63f68-122">핵심 cmdlet에 대 한 도움말에서 복사 합니다. 표준 용어를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="63f68-122">(Copy them from Help for the core cmdlets.) Use standard terms.</span></span> <span data-ttu-id="63f68-123">예를 들어 "argument"가 아닌 "parameter"를 사용 하 고 "command" 또는 "command-let"이 아닌 "cmdlet"을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="63f68-123">For example, use "parameter", not "argument", and use "cmdlet" not "command" or "command-let."</span></span>

### <a name="start-the-synopsis-with-a-verb"></a><span data-ttu-id="63f68-124">동사를 사용 하 여 개요 시작</span><span class="sxs-lookup"><span data-stu-id="63f68-124">Start the synopsis with a verb</span></span>

<span data-ttu-id="63f68-125">개요 필드는 cmdlet이 수행 하는 작업 또는 작동 방식을 사용자에 게 알립니다.</span><span class="sxs-lookup"><span data-stu-id="63f68-125">The synopsis field informs the user what the cmdlet does, not what it is or how it works.</span></span> <span data-ttu-id="63f68-126">동사는이 cmdlet이 요구 사항을 충족 하는 경우 사용자에 게 알리는 작업 기반 문을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="63f68-126">Verbs create a task-based statement that informs users if this cmdlet meets their requirements.</span></span> <span data-ttu-id="63f68-127">"Get", "create" 및 "change"와 같은 간단한 동사를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="63f68-127">Use simple verbs like "get", "create", and "change."</span></span> <span data-ttu-id="63f68-128">"설정"을 사용 하지 마세요 .이는 모호 하 고 "수정"과 같은 유용한 단어 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63f68-128">Avoid "set", which can be vague and fancy words like "modify".</span></span>

### <a name="focus-on-objects"></a><span data-ttu-id="63f68-129">개체에 포커스 설정</span><span class="sxs-lookup"><span data-stu-id="63f68-129">Focus on objects</span></span>

<span data-ttu-id="63f68-130">대부분의 "get" cmdlet은 무언가를 표시 하지만 기본 함수는 개체를 가져오는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="63f68-130">Most "get" cmdlets display something, but their primary function is to get an object.</span></span> <span data-ttu-id="63f68-131">사용자가 기본 표시 중 하나를 다른 방식으로 검색 한 개체의 메서드 및 속성을 사용할 수 있도록 도움말에서 개체에 대해 중점적으로 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="63f68-131">In your Help, focus on the object, so that users understand that the default display is one of many, and that they can use the methods and properties of the object that you retrieved for them in different ways.</span></span>

### <a name="write-detailed-descriptions"></a><span data-ttu-id="63f68-132">자세한 설명 작성</span><span class="sxs-lookup"><span data-stu-id="63f68-132">Write detailed descriptions</span></span>

<span data-ttu-id="63f68-133">자세한 설명에서 cmdlet이 수행할 수 있는 모든 항목을 간략하게 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="63f68-133">Briefly list everything that the cmdlet can do in the detailed description.</span></span> <span data-ttu-id="63f68-134">Main 함수가 속성 하나를 변경 하는 것 이지만 cmdlet이 모든 속성을 변경할 수 있는 경우 자세한 설명에이 목록을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="63f68-134">If the main function is to change one property, but the cmdlet can change all properties, list this in the detailed description.</span></span>

### <a name="use-conventional-syntax"></a><span data-ttu-id="63f68-135">기본 구문 사용</span><span class="sxs-lookup"><span data-stu-id="63f68-135">Use conventional syntax</span></span>

<span data-ttu-id="63f68-136">Windows 및 UNIX 명령줄 도움말에 일반적으로 사용 되는 표준 Backus-Naur 형식을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="63f68-136">Use the standard Backus-Naur format which is common for Windows and UNIX command-line Help.</span></span>

### <a name="use-microsoft-net-types-for-parameter-values"></a><span data-ttu-id="63f68-137">매개 변수 값에 Microsoft .NET 형식 사용</span><span class="sxs-lookup"><span data-stu-id="63f68-137">Use Microsoft .NET types for parameter values</span></span>

<span data-ttu-id="63f68-138">매개 변수 값에 대 한 자리 표시자 (구문 및 매개 변수 설명)에는 매개 변수가 허용 하는 개체의 .NET Framework 형식이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="63f68-138">The placeholders for parameter values (in the syntax and parameter descriptions) show the .NET Framework types of the objects that the parameter will accept.</span></span> <span data-ttu-id="63f68-139">PowerShell 팀은 사용자에 게 .NET Framework에 대해 학습 하는 데 도움이 되는이 규칙을 개발 했습니다.</span><span class="sxs-lookup"><span data-stu-id="63f68-139">The PowerShell team developed this convention to help teach users about the .NET Framework.</span></span>

### <a name="write-complete-parameter-descriptions"></a><span data-ttu-id="63f68-140">전체 매개 변수 설명을 작성 합니다.</span><span class="sxs-lookup"><span data-stu-id="63f68-140">Write complete parameter descriptions</span></span>

<span data-ttu-id="63f68-141">매개 변수 설명은 매개 변수의 용도, 매개 변수 값에 입력 해야 하는 항목에 대 한 두 가지 사항을 사용자에 게 알려 주어 야 합니다.</span><span class="sxs-lookup"><span data-stu-id="63f68-141">Parameter descriptions must inform users of two things: what the parameter does (its effect) and what they must type for the parameter values.</span></span>

### <a name="write-practical-examples"></a><span data-ttu-id="63f68-142">실제 사례 작성</span><span class="sxs-lookup"><span data-stu-id="63f68-142">Write practical examples</span></span>

<span data-ttu-id="63f68-143">이 예에서는 모든 매개 변수를 사용 하는 방법을 보여 주지만, 가장 중요 한 점은 실제 작업에서 cmdlet을 사용 하는 방법을 보여 주는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="63f68-143">The examples should show how to use all of the parameters, but the most important thing is to show how to use the cmdlet in real-world tasks.</span></span> <span data-ttu-id="63f68-144">간단한 예제를 시작 하 고 점점 더 복잡 한 예제를 작성 합니다.</span><span class="sxs-lookup"><span data-stu-id="63f68-144">Start with a simple example and write increasingly complex examples.</span></span> <span data-ttu-id="63f68-145">마지막 예제에서는 파이프라인에서 cmdlet을 사용 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="63f68-145">In the final example, show how to use the cmdlet in a pipeline.</span></span>

### <a name="use-the-notes-field"></a><span data-ttu-id="63f68-146">참고 필드 사용</span><span class="sxs-lookup"><span data-stu-id="63f68-146">Use the Notes field</span></span>

<span data-ttu-id="63f68-147">참고 필드를 사용 하 여 사용자가 cmdlet을 이해 하는 데 필요한 개념을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="63f68-147">Use the Notes field to explain concepts that users need to understand the cmdlet.</span></span> <span data-ttu-id="63f68-148">또한 사용자가 일반적인 오류를 방지 하는 데 도움이 되는 정보를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63f68-148">You can also use notes to help users avoid common errors.</span></span> <span data-ttu-id="63f68-149">Url이 변경 되 면 사용 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="63f68-149">Avoid URLs as they change.</span></span> <span data-ttu-id="63f68-150">대신 검색할 사용자 용어를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="63f68-150">Instead, provide users terms to search for.</span></span>

### <a name="test-your-help"></a><span data-ttu-id="63f68-151">도움말 테스트</span><span class="sxs-lookup"><span data-stu-id="63f68-151">Test your Help</span></span>

<span data-ttu-id="63f68-152">코드를 테스트 하는 것과 같은 방법으로 도움말을 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="63f68-152">Test the Help just like you test your code.</span></span> <span data-ttu-id="63f68-153">친구와 동료가 도움말 콘텐츠를 읽고 피드백을 제공 하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="63f68-153">Have friends and colleagues read your Help content and provide feedback.</span></span> <span data-ttu-id="63f68-154">뉴스 그룹에서 피드백을 요청할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63f68-154">You can also solicit feedback from newsgroups.</span></span>

## <a name="see-also"></a><span data-ttu-id="63f68-155">참고 항목</span><span class="sxs-lookup"><span data-stu-id="63f68-155">See Also</span></span>

 [<span data-ttu-id="63f68-156">Cmdlet 도움말 파일을 만드는 방법</span><span class="sxs-lookup"><span data-stu-id="63f68-156">How to Create the Cmdlet Help File</span></span>](./how-to-create-the-cmdlet-help-file.md)

 [<span data-ttu-id="63f68-157">Cmdlet 도움말 항목에 Cmdlet 이름 및 개요를 추가하는 방법</span><span class="sxs-lookup"><span data-stu-id="63f68-157">How to Add the Cmdlet Name and Synopsis to a Cmdlet Help Topic</span></span>](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="63f68-158">Cmdlet 도움말 항목에 자세한 설명을 추가 하는 방법</span><span class="sxs-lookup"><span data-stu-id="63f68-158">How to Add the Detailed Description to a Cmdlet Help Topic</span></span>](./how-to-add-a-cmdlet-description.md)

 [<span data-ttu-id="63f68-159">Cmdlet 도움말 항목에 구문을 추가하는 방법</span><span class="sxs-lookup"><span data-stu-id="63f68-159">How to Add Syntax to a Cmdlet Help Topic</span></span>](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="63f68-160">Cmdlet 도움말 항목에 매개 변수를 추가 하는 방법</span><span class="sxs-lookup"><span data-stu-id="63f68-160">How to Add Parameters to a Cmdlet Help Topic</span></span>](./how-to-add-parameter-information.md)

 [<span data-ttu-id="63f68-161">Cmdlet 도움말 항목에 입력 유형을 추가 하는 방법</span><span class="sxs-lookup"><span data-stu-id="63f68-161">How to add Input Types to a Cmdlet Help Topic</span></span>](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="63f68-162">Cmdlet 도움말 항목에 반환 값을 추가하는 방법</span><span class="sxs-lookup"><span data-stu-id="63f68-162">How to Add Return Values to a Cmdlet Help Topic</span></span>](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="63f68-163">Cmdlet 도움말 항목에 메모를 추가하는 방법</span><span class="sxs-lookup"><span data-stu-id="63f68-163">How to Add Notes to a Cmdlet Help Topic</span></span>](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="63f68-164">Cmdlet 도움말 항목에 예제를 추가하는 방법</span><span class="sxs-lookup"><span data-stu-id="63f68-164">How to Add Examples to a Cmdlet Help Topic</span></span>](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="63f68-165">Cmdlet 도움말 항목에 관련 링크를 추가하는 방법</span><span class="sxs-lookup"><span data-stu-id="63f68-165">How to Add Related Links to a Cmdlet Help Topic</span></span>](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="63f68-166">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="63f68-166">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
