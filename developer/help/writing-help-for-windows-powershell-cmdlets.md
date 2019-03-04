---
title: PowerShell Cmdlet에 대 한 도움말을 작성 합니다. | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 55908d67-7cbe-482a-a105-5a6da93c5311
caps.latest.revision: 4
ms.openlocfilehash: 8d692cf88d1d356886ef973f0989294d6b51ee6d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857859"
---
# <a name="writing-help-for-powershell-cmdlets"></a><span data-ttu-id="df46f-102">PowerShell Cmdlet에 대 한 도움말 작성</span><span class="sxs-lookup"><span data-stu-id="df46f-102">Writing Help for PowerShell Cmdlets</span></span>

<span data-ttu-id="df46f-103">PowerShell cmdlet 유용할 수 있지만 도움말 항목에는 명확 하 게 cmdlet이 수행 하 고 사용 하는 방법을 설명, 하지 않으면 cmdlet은 사용 되지 않을 수 있습니다, 설상가상으로 사용자가 불편 해질 수 있습니다 것입니다.</span><span class="sxs-lookup"><span data-stu-id="df46f-103">PowerShell cmdlets can be useful, but unless your Help topics clearly explain what the cmdlet does and how to use it, the cmdlet may not get used or, even worse, it might frustrate users.</span></span>
<span data-ttu-id="df46f-104">XML 기반 cmdlet 도움말 파일 형식 일관성을 향상 시킵니다. 하지만 큰 도움이 더 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="df46f-104">The XML-based cmdlet Help file format enhances consistency, but great help requires much more.</span></span>

<span data-ttu-id="df46f-105">Cmdlet 도움말을 작성 하지 한 경우 다음 지침을 검토 합니다.</span><span class="sxs-lookup"><span data-stu-id="df46f-105">If you have never written cmdlet Help, review the following guidelines.</span></span>
<span data-ttu-id="df46f-106">Cmdlet 도움말 항목을 작성 하는 데 필요한 XML 스키마는 다음 섹션에 설명 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df46f-106">The XML schema required to author the cmdlet Help topic is described in the following section.</span></span>
<span data-ttu-id="df46f-107">시작 [Cmdlet 도움말 파일을 만드는](./how-to-create-the-cmdlet-help-file.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="df46f-107">Start with [Creating the Cmdlet Help File](./how-to-create-the-cmdlet-help-file.md).</span></span>
<span data-ttu-id="df46f-108">해당 항목에는 최상위 XML 노드에 대 한 설명을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="df46f-108">That topic includes a description of the top-level XML nodes.</span></span>

## <a name="writing-guidelines-for-cmdlet-help"></a><span data-ttu-id="df46f-109">Cmdlet 도움말에 대 한 작성 지침</span><span class="sxs-lookup"><span data-stu-id="df46f-109">Writing Guidelines for Cmdlet Help</span></span>

### <a name="write-well"></a><span data-ttu-id="df46f-110">잘 작성</span><span class="sxs-lookup"><span data-stu-id="df46f-110">Write well</span></span>
<span data-ttu-id="df46f-111">아무 것도 잘 작성 된 항목을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="df46f-111">Nothing replaces a well-written topic.</span></span>
<span data-ttu-id="df46f-112">전문 기록기에 없는 경우에 기록기 또는 편집기를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="df46f-112">If you are not a professional writer, find a writer or editor to help you.</span></span>
<span data-ttu-id="df46f-113">Microsoft Word에 도움말 텍스트를 복사 하 여 문법을 사용 하는 다른 대안은 및 작업을 개선 하기 위해 맞춤법 검사 합니다.</span><span class="sxs-lookup"><span data-stu-id="df46f-113">Another alternative is to copy your Help text into Microsoft Word and use the grammar and spelling checks to improve your work.</span></span>

### <a name="write-simply"></a><span data-ttu-id="df46f-114">단순히 작성</span><span class="sxs-lookup"><span data-stu-id="df46f-114">Write simply</span></span>
<span data-ttu-id="df46f-115">간단한 단어 및 구를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="df46f-115">Use simple words and phrases.</span></span>
<span data-ttu-id="df46f-116">용어를 방지 합니다.</span><span class="sxs-lookup"><span data-stu-id="df46f-116">Avoid jargon.</span></span>
<span data-ttu-id="df46f-117">여러 독자 여러분 장착 되어만 외국어 사전 및 도움말 항목을 고려 합니다.</span><span class="sxs-lookup"><span data-stu-id="df46f-117">Consider that many readers are equipped only with a foreign-language dictionary and your Help topic.</span></span>

### <a name="write-consistently"></a><span data-ttu-id="df46f-118">일관 되 게 작성</span><span class="sxs-lookup"><span data-stu-id="df46f-118">Write consistently</span></span>
<span data-ttu-id="df46f-119">도움말 관련된 cmdlet (예를 들어, get-x 및 x 집합) 유사 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="df46f-119">Help for related cmdlets should be similar (for example, get-x and set-x).</span></span>
<span data-ttu-id="df46f-120">표준 매개 변수에 대 한 표준 설명을 사용할 **Force** 하 고 **InputObject**합니다.</span><span class="sxs-lookup"><span data-stu-id="df46f-120">Use the standard descriptions for standard parameters, like **Force** and **InputObject**.</span></span>
<span data-ttu-id="df46f-121">(복사한 도움말에서 핵심 cmdlet에 대 한 합니다.) 표준 용어를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="df46f-121">(Copy them from Help for the core cmdlets.) Use standard terms.</span></span>
<span data-ttu-id="df46f-122">예: 사용 하 여 "매개 변수", 없습니다 "인수" 및 "cmdlet" 사용 되지 않습니다 "명령" 또는 "명령을 사용 합니다."</span><span class="sxs-lookup"><span data-stu-id="df46f-122">For example, use "parameter", not "argument", and use "cmdlet" not "command" or "command-let."</span></span>

### <a name="start-the-synopsis-with-a-verb"></a><span data-ttu-id="df46f-123">개요는 동사를 사용 하 여 시작</span><span class="sxs-lookup"><span data-stu-id="df46f-123">Start the synopsis with a verb</span></span>
<span data-ttu-id="df46f-124">어떤 cmdlet이 수행, 없습니다 무엇 인지 또는 작동 방식 개요 필드를 사용자에 게 알립니다.</span><span class="sxs-lookup"><span data-stu-id="df46f-124">The synopsis field informs the user what the cmdlet does, not what it is or how it works.</span></span>
<span data-ttu-id="df46f-125">동사에는이 cmdlet은 해당 요구 사항을 충족 하는 경우 사용자에 게 알려 주는 작업 기반의 문을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="df46f-125">Verbs create a task-based statement that informs users if this cmdlet meets their requirements.</span></span>
<span data-ttu-id="df46f-126">"Get", "만들기" 및 "변경"과 같은 간단한 동사 사용</span><span class="sxs-lookup"><span data-stu-id="df46f-126">Use simple verbs like "get", "create", and "change."</span></span>
<span data-ttu-id="df46f-127">"수정"와 같은 단어를 모호 하 고 멋진 일 수 있음 "설정"을 방지 합니다.</span><span class="sxs-lookup"><span data-stu-id="df46f-127">Avoid "set", which can be vague and fancy words like "modify".</span></span>

### <a name="focus-on-objects"></a><span data-ttu-id="df46f-128">개체에 집중</span><span class="sxs-lookup"><span data-stu-id="df46f-128">Focus on objects</span></span>
<span data-ttu-id="df46f-129">대부분 "get" cmdlet 디스플레이 무엇 인가 이지만 해당 기본 함수 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="df46f-129">Most "get" cmdlets display something, but their primary function is to get an object.</span></span>
<span data-ttu-id="df46f-130">도움을 집중적으로 개체를 사용자가 이해할 기본 표시는 많은 중 고 메서드 및 다양 한 방식에 검색 된 개체의 속성을 사용할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="df46f-130">In your Help, focus on the object, so that users understand that the default display is one of many, and that they can use the methods and properties of the object that you retrieved for them in different ways.</span></span>

### <a name="write-detailed-descriptions"></a><span data-ttu-id="df46f-131">자세한 설명을 기록합니다</span><span class="sxs-lookup"><span data-stu-id="df46f-131">Write detailed descriptions</span></span>
<span data-ttu-id="df46f-132">간단히 cmdlet 자세한 설명에서는 할 수 있는 모든를 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="df46f-132">Briefly list everything that the cmdlet can do in the detailed description.</span></span>
<span data-ttu-id="df46f-133">주 함수 하나의 속성을 변경 하는 cmdlet은 모든 속성을 변경할 수 있지만 경우 자세한 설명에이 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="df46f-133">If the main function is to change one property, but the cmdlet can change all properties, list this in the detailed description.</span></span>

### <a name="use-conventional-syntax"></a><span data-ttu-id="df46f-134">기존 구문을 사용 하십시오.</span><span class="sxs-lookup"><span data-stu-id="df46f-134">Use conventional syntax</span></span>
<span data-ttu-id="df46f-135">Windows 및 UNIX 명령줄 도움말에 공통 되는 표준 Backus Naur 형식을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="df46f-135">Use the standard Backus-Naur format which is common for Windows and UNIX command-line Help.</span></span>

### <a name="use-microsoft-net-framework-types-for-parameter-values"></a><span data-ttu-id="df46f-136">매개 변수 값에 대 한 Microsoft.NET Framework 형식을 사용합니다</span><span class="sxs-lookup"><span data-stu-id="df46f-136">Use Microsoft .NET Framework types for parameter values</span></span>
<span data-ttu-id="df46f-137">매개 변수 값 (구문 및 매개 변수 설명)에 대 한 자리 표시자 매개 변수 허용 하는 개체의.NET Framework 형식을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="df46f-137">The placeholders for parameter values (in the syntax and parameter descriptions) show the .NET Framework types of the objects that the parameter will accept.</span></span>
<span data-ttu-id="df46f-138">PowerShell 팀에는.NET Framework에 대 한 사용자를 교육 하는 데이 규칙 개발 했습니다.</span><span class="sxs-lookup"><span data-stu-id="df46f-138">The PowerShell team developed this convention to help teach users about the .NET Framework.</span></span>

### <a name="write-complete-parameter-descriptions"></a><span data-ttu-id="df46f-139">전체 매개 변수 설명 작성</span><span class="sxs-lookup"><span data-stu-id="df46f-139">Write complete parameter descriptions</span></span>
<span data-ttu-id="df46f-140">매개 변수 설명의 두 가지 사용자에 게 알려야 합니다: 어떤 매개 변수 (미치는) 않으며 매개 변수 값에 대 한 입력 해야 새로운 합니다.</span><span class="sxs-lookup"><span data-stu-id="df46f-140">Parameter descriptions must inform users of two things: what the parameter does (its effect) and what they must type for the parameter values.</span></span>

### <a name="write-practical-examples"></a><span data-ttu-id="df46f-141">실제 예제를 작성 합니다.</span><span class="sxs-lookup"><span data-stu-id="df46f-141">Write practical examples</span></span>
<span data-ttu-id="df46f-142">예에는 모든 매개 변수를 사용 하는 방법을 보여 줍니다 해야 하지만 가장 중요 한 점은 실제 작업에서 cmdlet을 사용 하는 방법을 보여 주는 합니다.</span><span class="sxs-lookup"><span data-stu-id="df46f-142">The examples should show how to use all of the parameters, but the most important thing is to show how to use the cmdlet in real-world tasks.</span></span>
<span data-ttu-id="df46f-143">간단한 예제로 시작 하 고 점점 더 복잡 한 예제를 작성 합니다.</span><span class="sxs-lookup"><span data-stu-id="df46f-143">Start with a simple example and write increasingly complex examples.</span></span>
<span data-ttu-id="df46f-144">마지막 예제에서는 파이프라인에서 cmdlet을 사용 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="df46f-144">In the final example, show how to use the cmdlet in a pipeline.</span></span>

### <a name="use-the-notes-field"></a><span data-ttu-id="df46f-145">참고 필드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="df46f-145">Use the Notes field</span></span>
<span data-ttu-id="df46f-146">참고 필드를 사용 하 여 사용자가 cmdlet을 이해 해야 하는 개념을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="df46f-146">Use the Notes field to explain concepts that users need to understand the cmdlet.</span></span>
<span data-ttu-id="df46f-147">또한 일반 오류를 방지 하는 사용자가 정보를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df46f-147">You can also use notes to help users avoid common errors.</span></span>
<span data-ttu-id="df46f-148">변경 될 때 해당 Url을 방지 합니다.</span><span class="sxs-lookup"><span data-stu-id="df46f-148">Avoid URLs as they change.</span></span>
<span data-ttu-id="df46f-149">대신, 검색할 사용자 사용 약관을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="df46f-149">Instead, provide users terms to search for.</span></span>

### <a name="test-your-help"></a><span data-ttu-id="df46f-150">테스트 프로그램 도움말</span><span class="sxs-lookup"><span data-stu-id="df46f-150">Test your Help</span></span>
<span data-ttu-id="df46f-151">코드를 테스트 하는 것 처럼 도움말을 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="df46f-151">Test the Help just like you test your code.</span></span>
<span data-ttu-id="df46f-152">친구 있고 동료 도움말 콘텐츠를 읽기 및 피드백을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="df46f-152">Have friends and colleagues read your Help content and provide feedback.</span></span>
<span data-ttu-id="df46f-153">또한 뉴스 그룹에서 피드백을 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df46f-153">You can also solicit feedback from newsgroups.</span></span>

## <a name="see-also"></a><span data-ttu-id="df46f-154">참고 항목</span><span class="sxs-lookup"><span data-stu-id="df46f-154">See Also</span></span>

 [<span data-ttu-id="df46f-155">Cmdlet 도움말 파일을 만드는 방법</span><span class="sxs-lookup"><span data-stu-id="df46f-155">How to Create the Cmdlet Help File</span></span>](./how-to-create-the-cmdlet-help-file.md)

 [<span data-ttu-id="df46f-156">Cmdlet 이름 및 개요 Cmdlet 도움말 항목을 추가 하는 방법</span><span class="sxs-lookup"><span data-stu-id="df46f-156">How to Add the Cmdlet Name and Synopsis to a Cmdlet Help Topic</span></span>](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="df46f-157">자세한 설명은 Cmdlet 도움말 항목을 추가 하는 방법</span><span class="sxs-lookup"><span data-stu-id="df46f-157">How to Add the Detailed Description to a Cmdlet Help Topic</span></span>](./how-to-add-a-cmdlet-description.md)

 [<span data-ttu-id="df46f-158">구문 Cmdlet 도움말 항목을 추가 하는 방법</span><span class="sxs-lookup"><span data-stu-id="df46f-158">How to Add Syntax to a Cmdlet Help Topic</span></span>](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="df46f-159">Cmdlet 도움말 항목 매개 변수를 추가 하는 방법</span><span class="sxs-lookup"><span data-stu-id="df46f-159">How to Add Parameters to a Cmdlet Help Topic</span></span>](./how-to-add-parameter-information.md)

 [<span data-ttu-id="df46f-160">입력 형식 Cmdlet 도움말 항목을 추가 하는 방법</span><span class="sxs-lookup"><span data-stu-id="df46f-160">How to add Input Types to a Cmdlet Help Topic</span></span>](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="df46f-161">Cmdlet 도움말 항목에 반환 값을 추가 하는 방법</span><span class="sxs-lookup"><span data-stu-id="df46f-161">How to Add Return Values to a Cmdlet Help Topic</span></span>](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="df46f-162">Cmdlet 도움말 항목을 추가 하는 방법 정보</span><span class="sxs-lookup"><span data-stu-id="df46f-162">How to Add Notes to a Cmdlet Help Topic</span></span>](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="df46f-163">예제 Cmdlet 도움말 항목을 추가 하는 방법</span><span class="sxs-lookup"><span data-stu-id="df46f-163">How to Add Examples to a Cmdlet Help Topic</span></span>](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="df46f-164">관련된 링크 Cmdlet 도움말 항목을 추가 하는 방법</span><span class="sxs-lookup"><span data-stu-id="df46f-164">How to Add Related Links to a Cmdlet Help Topic</span></span>](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="df46f-165">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="df46f-165">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)