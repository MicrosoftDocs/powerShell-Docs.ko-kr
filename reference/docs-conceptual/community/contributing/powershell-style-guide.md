---
title: PowerShell-Docs 스타일 가이드
description: 이 문서에서는 PowerShell 설명서 작성을 위한 스타일 규칙을 제공합니다.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: b60ad9a4965e75cc5f68309604f1893e5757f351
ms.sourcegitcommit: 17d798a041851382b406ed789097843faf37692d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83690852"
---
# <a name="powershell-docs-style-guide"></a><span data-ttu-id="1b3b8-103">PowerShell-Docs 스타일 가이드</span><span class="sxs-lookup"><span data-stu-id="1b3b8-103">PowerShell-Docs style guide</span></span>

<span data-ttu-id="1b3b8-104">이 문서에서는 PowerShell-Docs 콘텐츠에 관한 스타일 지침을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-104">This article provides style guidance specific to the PowerShell-Docs content.</span></span> <span data-ttu-id="1b3b8-105">이 지침은 [개요](overview.md#get-started-writing-docs)에 설명된 정보를 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-105">This builds on the information outlined in the [Overview](overview.md#get-started-writing-docs).</span></span>

## <a name="product-terminology"></a><span data-ttu-id="1b3b8-106">제품 용어</span><span class="sxs-lookup"><span data-stu-id="1b3b8-106">Product Terminology</span></span>

<span data-ttu-id="1b3b8-107">PowerShell에는 몇 가지 변형이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-107">There are several variants of PowerShell.</span></span>

- <span data-ttu-id="1b3b8-108">**PowerShell** - 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-108">**PowerShell** - This is the default.</span></span> <span data-ttu-id="1b3b8-109">앞으로는 PowerShell 7 이상이 유일한 정식 PowerShell로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-109">We consider PowerShell 7 and beyond to be the one, true PowerShell going forward.</span></span>
- <span data-ttu-id="1b3b8-110">**PowerShell Core** - .NET Core를 기반으로 빌드된 PowerShell입니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-110">**PowerShell Core** - PowerShell built on .NET Core.</span></span> <span data-ttu-id="1b3b8-111">용어 **Core**는 Windows PowerShell과 구분해야 하는 경우에만 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-111">Usage of the term **Core** should be limited to cases where it is necessary to differentiate it from Windows PowerShell.</span></span>
- <span data-ttu-id="1b3b8-112">**Windows PowerShell** - .NET Framework를 기반으로 빌드된 PowerShell입니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-112">**Windows PowerShell** - PowerShell built on .NET Framework.</span></span> <span data-ttu-id="1b3b8-113">Windows PowerShell은 Windows에만 제공되며 전체 Framework가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-113">Windows PowerShell ships only on Windows and requires the complete Framework.</span></span>

  <span data-ttu-id="1b3b8-114">일반적으로 설명서의 "Windows PowerShell"에 대한 참조는 "PowerShell"로 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-114">In general, references to "Windows PowerShell" in documentation can be changed to "PowerShell".</span></span>
  <span data-ttu-id="1b3b8-115">"WindowsPowerShell" 관련 동작을 설명할 때는 "Windows PowerShell"을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-115">"Windows PowerShell" should be used when "Windows PowerShell"-specific behavior is being discussed.</span></span>

<span data-ttu-id="1b3b8-116">관련 제품</span><span class="sxs-lookup"><span data-stu-id="1b3b8-116">Related products</span></span>

- <span data-ttu-id="1b3b8-117">**Visual Studio Code(VS Code)** - Microsoft의 무료 오픈 소스 편집기입니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-117">**Visual Studio Code (VS Code)** - This is Microsoft's free, open source editor.</span></span> <span data-ttu-id="1b3b8-118">처음 언급할 때는 전체 이름을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-118">At first mention, the full name should be used.</span></span> <span data-ttu-id="1b3b8-119">그런 다음 **VS Code**라고 언급할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-119">After that you may use **VS Code**.</span></span> <span data-ttu-id="1b3b8-120">"VSCode"를 사용하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-120">Do not use "VSCode".</span></span>
- <span data-ttu-id="1b3b8-121">**Visual Studio Code에 대한 Powershell 확장** - 확장은 VS Code를 PowerShell의 기본 IDE로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-121">**PowerShell Extension for Visual Studio Code** - The extension turns VS Code into the preferred IDE for PowerShell.</span></span> <span data-ttu-id="1b3b8-122">처음 언급할 때는 전체 이름을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-122">At first mention, the full name should be used.</span></span> <span data-ttu-id="1b3b8-123">그런 다음 **PowerShell 확장**이라고 언급할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-123">After that you may use **PowerShell extension**.</span></span>
- <span data-ttu-id="1b3b8-124">**Azure PowerShell** - Azure 서비스를 관리하는 데 사용되는 Powershell 모듈의 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-124">**Azure PowerShell** - This is the collection of PowerShell modules used to manage Azure services.</span></span>
- <span data-ttu-id="1b3b8-125">**Azure Stack PowerShell** - Microsoft의 하이브리드 클라우드 솔루션을 관리하는 데 사용되는 Powershell 모듈의 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-125">**Azure Stack PowerShell** - This is the collection of PowerShell modules used to manage Microsoft's hybrid cloud solution.</span></span>

## <a name="markdown-specifics"></a><span data-ttu-id="1b3b8-126">Markdown 세부보</span><span class="sxs-lookup"><span data-stu-id="1b3b8-126">Markdown specifics</span></span>

<span data-ttu-id="1b3b8-127">설명서를 빌드하는 Microsoft OPS(Open Publishing System)는 [markdig][]를 사용하여 Markdown 문서를 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-127">The Microsoft Open Publishing System (OPS) that builds our documentation uses [markdig][] to process the Markdown documents.</span></span> <span data-ttu-id="1b3b8-128">markdig는 최신 [CommonMark][] 사양의 규칙에 따라 문서를 구문 분석합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-128">Markdig parses the documents based on the rules of the latest [CommonMark][] specification.</span></span>

<span data-ttu-id="1b3b8-129">새 CommonMark 사양은 일부 Markdown 요소 생성에 대해 훨씬 더 엄격하게 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-129">The new CommonMark spec is much stricter about the construction of some Markdown elements.</span></span> <span data-ttu-id="1b3b8-130">이 문서에 제공된 세부 정보에 각별히 주의하세요.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-130">Pay close attention to the details provided in this document.</span></span>

### <a name="blank-lines-spaces-and-tabs"></a><span data-ttu-id="1b3b8-131">빈 줄, 공백, 탭</span><span class="sxs-lookup"><span data-stu-id="1b3b8-131">Blank lines, spaces, and tabs</span></span>

<span data-ttu-id="1b3b8-132">또한 빈 줄은 Markdown에서 블록이 끝난다는 신호입니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-132">Blank lines also signal the end of a block in Markdown.</span></span> <span data-ttu-id="1b3b8-133">서로 다른 형식의 Markdown 블록 사이(예: 단락과 목록 또는 헤더 사이)에는 빈 줄이 하나 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-133">There should be a single blank between Markdown blocks of different types (for example, between a paragraph and a list or header).</span></span>

<span data-ttu-id="1b3b8-134">중복된 빈 줄을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-134">Remove duplicate blank lines.</span></span> <span data-ttu-id="1b3b8-135">HTML에서는 여러 개의 빈 줄이 하나의 빈 줄로 렌더링되므로 빈 줄을 여러 개 넣을 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-135">Multiple blank lines render as a single blank line in HTML so there is no purpose for multiple blank lines.</span></span> <span data-ttu-id="1b3b8-136">코드 블록 내에 빈 줄이 여러 개 있으면 코드 블록이 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-136">Multiple blank lines within a code block break the code block.</span></span>

<span data-ttu-id="1b3b8-137">줄의 끝부분에서 추가 공백을 제거해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-137">Remove extra spaces at the end of lines.</span></span>

> [!NOTE]
> <span data-ttu-id="1b3b8-138">Markdown에서는 간격이 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-138">Spacing is significant in Markdown.</span></span> <span data-ttu-id="1b3b8-139">항상 하드 탭 대신 공백을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-139">Always uses spaces instead of hard tabs.</span></span> <span data-ttu-id="1b3b8-140">후행 공백은 Markdown이 렌더링하는 방식을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-140">Trailing spaces can change how Markdown renders.</span></span>

### <a name="titles-and-headings"></a><span data-ttu-id="1b3b8-141">제목 및 머리글</span><span class="sxs-lookup"><span data-stu-id="1b3b8-141">Titles and headings</span></span>

<span data-ttu-id="1b3b8-142">[ATX 머리글][atx](`=` 또는 `-` 스타일 헤더가 아닌 # 스타일)만 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-142">Only use [ATX headings][atx] (# style, as opposed to `=` or `-` style headers).</span></span>

- <span data-ttu-id="1b3b8-143">문장의 첫 글자를 대문자로 시작하세요. 고유 명사와 제목 또는 헤더의 첫 글자만 대문자로 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-143">Use sentence case - only proper nouns and the first letter of a title or header should be capitalized</span></span>
- <span data-ttu-id="1b3b8-144">`#`와 머리글의 첫 문자 사이에는 공백이 하나 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-144">There must be a single space between the `#` and the first letter of the heading</span></span>
- <span data-ttu-id="1b3b8-145">머리글은 빈 줄 하나로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-145">Headings should be surrounded by a single blank line</span></span>
- <span data-ttu-id="1b3b8-146">H1은 문서당 하나만 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-146">Only one H1 per document</span></span>
- <span data-ttu-id="1b3b8-147">헤더 수준은 1씩 증가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-147">Header levels should increment by one.</span></span> <span data-ttu-id="1b3b8-148">수준을 건너뛰지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-148">Do not skip levels</span></span>
- <span data-ttu-id="1b3b8-149">헤더에 굵은 글꼴 또는 기타 태그를 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-149">Do not use bold or other markup in headers</span></span>

### <a name="limit-line-length-to-100-characters"></a><span data-ttu-id="1b3b8-150">줄 길이는 100자로 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-150">Limit line length to 100 characters</span></span>

<span data-ttu-id="1b3b8-151">이는 개념 문서와 cmdlet 참조에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-151">This applies to conceptual articles and cmdlet reference.</span></span> <span data-ttu-id="1b3b8-152">줄 길이를 제한하면 git diff의 가독성과 기록이 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-152">Limiting the line length improves the readability of git diffs and history.</span></span> <span data-ttu-id="1b3b8-153">또한 다른 작성자가 보다 쉽게 기여할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-153">It also makes it easier for other writers to make contributions.</span></span>

<span data-ttu-id="1b3b8-154">사전 설정된 줄 길이에 맞게 단락을 쉽게 재배치하려면 Visual Studio Code에서 [Reflow Markdown][reflow] 확장을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-154">Use the [Reflow Markdown][reflow] extension in Visual Studio Code to easily reflow paragraphs to fit the prescribed line length.</span></span>

<span data-ttu-id="1b3b8-155">about_topics는 80자로 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-155">About_topics are limited to 80 characters.</span></span> <span data-ttu-id="1b3b8-156">자세한 내용은 [참조 문서 편집](./editing-cmdlet-ref.md#formatting-about_-files)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-156">For more specific information, see [Editing reference articles](./editing-cmdlet-ref.md#formatting-about_-files).</span></span>

### <a name="lists"></a><span data-ttu-id="1b3b8-157">목록</span><span class="sxs-lookup"><span data-stu-id="1b3b8-157">Lists</span></span>

<span data-ttu-id="1b3b8-158">목록에 여러 문장이나 단락이 포함되어 있으면 목록 대신 하위 수준 헤더를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-158">If your list contains multiple sentences or paragraphs, consider using a sub-level header rather than a list.</span></span>

<span data-ttu-id="1b3b8-159">목록은 빈 줄 하나로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-159">List should be surrounded by a single blank line.</span></span>

#### <a name="unordered-lists"></a><span data-ttu-id="1b3b8-160">순서가 지정되지 않은 목록</span><span class="sxs-lookup"><span data-stu-id="1b3b8-160">Unordered lists</span></span>

<span data-ttu-id="1b3b8-161">목록 항목의 끝에 마침표를 사용하지 않습니다(여러 문장이 있는 경우만 허용).</span><span class="sxs-lookup"><span data-stu-id="1b3b8-161">Do not end list items with a period unless they contain multiple sentences.</span></span> <span data-ttu-id="1b3b8-162">목록 항목 글머리 기호에 하이픈 문자(`-`)를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-162">Use the hyphen character (`-`) for list item bullets.</span></span> <span data-ttu-id="1b3b8-163">이렇게 하면 별표[`*`]를 사용하는 굵게 또는 기울임꼴 태그와의 혼동을 피할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-163">This avoids confusion with bold or italic markup that uses the asterisk [`*`].</span></span> <span data-ttu-id="1b3b8-164">글머리 기호 항목 아래에 단락이나 기타 요소를 포함하려면 줄 바꿈을 삽입하고 글머리 기호 뒤 첫 번째 문자에 들여쓰기를 맞춥니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-164">To include a paragraph or other elements under a bullet item, insert a line break and align indentation with the first character after the bullet.</span></span>

<span data-ttu-id="1b3b8-165">다음은 그 예입니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-165">For example:</span></span>

```markdown
This is a list that contain sub-elements under a bullet item.

- First bullet item

  Sentence explaining the first bullet.

  - Sub-bullet item

    Sentence explaining the sub-bullet.

- Second bullet item
- Third bullet item
```

<span data-ttu-id="1b3b8-166">글머리 기호 항목 아래 하위 요소를 포함하는 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-166">This is a list that contains sub-elements under a bullet item.</span></span>

- <span data-ttu-id="1b3b8-167">첫 번째 글머리 기호 항목</span><span class="sxs-lookup"><span data-stu-id="1b3b8-167">First bullet item</span></span>

  <span data-ttu-id="1b3b8-168">첫 번째 글머리 기호를 설명하는 문장입니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-168">Sentence explaining the first bullet.</span></span>

  - <span data-ttu-id="1b3b8-169">하위 글머리 기호 항목</span><span class="sxs-lookup"><span data-stu-id="1b3b8-169">Sub-bullet item</span></span>

    <span data-ttu-id="1b3b8-170">하위 글머리 기호를 설명하는 문장입니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-170">Sentence explaining the sub-bullet.</span></span>

- <span data-ttu-id="1b3b8-171">두 번째 글머리 기호 항목</span><span class="sxs-lookup"><span data-stu-id="1b3b8-171">Second bullet item</span></span>
- <span data-ttu-id="1b3b8-172">세 번째 글머리 기호 항목</span><span class="sxs-lookup"><span data-stu-id="1b3b8-172">Third bullet item</span></span>

#### <a name="ordered-lists"></a><span data-ttu-id="1b3b8-173">순서가 지정된 목록</span><span class="sxs-lookup"><span data-stu-id="1b3b8-173">Ordered lists</span></span>

<span data-ttu-id="1b3b8-174">번호 매기기 항목 아래에 단락이나 기타 요소를 포함하려면 항목 번호 뒤 첫 번째 문자에 들여쓰기를 맞춥니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-174">To include a paragraph or other elements under a numbered item, align indentation with the first character after the item number.</span></span> <span data-ttu-id="1b3b8-175">번호 매기기 목록의 모든 항목은 각 항목을 증가시키는 것이 아니라 숫자 `1.`을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-175">All items in a numbered listed should use the number `1.` rather than incrementing each item.</span></span> <span data-ttu-id="1b3b8-176">Markdown 렌더링은 값을 자동으로 증가시킵니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-176">Markdown rendering increments the value automatically.</span></span> <span data-ttu-id="1b3b8-177">이렇게 하면 보다 쉽게 항목 순서를 다시 매기고 하위 콘텐츠의 들여쓰기를 표준화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-177">This makes reordering items easier and standardizes the indentation of subordinate content.</span></span>

<span data-ttu-id="1b3b8-178">다음은 그 예입니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-178">For example:</span></span>

```markdown
1. For the first element, insert a single space after the 1. Long sentences should be
   wrapped to the next line and must line up with the first character after the numbered
   list marker.

   To include a second element (like this one), insert a line break after the first
   and align indentations. The indentation of the second element must line up with
   the first character after the numbered list marker. For single digit items, like
   this one, you indent to column 4. For double digits items, for example item number
   10, you indent to column 5.

1. The next numbered item starts here.
```

<span data-ttu-id="1b3b8-179">결과 Markdown은 다음과 같이 렌더링됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-179">The resulting Markdown is rendered as follows:</span></span>

1. <span data-ttu-id="1b3b8-180">첫 번째 요소의 경우 1 뒤에 단일 공백을 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-180">For the first element, insert a single space after the 1.</span></span> <span data-ttu-id="1b3b8-181">긴 문장은 다음 줄로 줄바꿈되어야 하며, 번호 매기기 목록 마커 뒤의 첫 번째 문자에 맞춰야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-181">Long sentences should be wrapped to the next line and must line up with the first character after the numbered list marker.</span></span>

   <span data-ttu-id="1b3b8-182">(다음과 같은) 두 번째 요소를 포함하려면 첫 번째 요소 뒤에 줄 바꿈을 삽입하고 들여쓰기를 정렬합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-182">To include a second element (like this one), insert a line break after the first and align indentations.</span></span> <span data-ttu-id="1b3b8-183">두 번째 요소의 들여쓰기는 번호 매기기 목록 마커 뒤의 첫 번째 문자에 맞춰야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-183">The indentation of the second element must line up with the first character after the numbered list marker.</span></span> <span data-ttu-id="1b3b8-184">이와 같은 한 자리 항목의 경우 열 4로 들여씁니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-184">For single digit items, like this one, you indent to column 4.</span></span> <span data-ttu-id="1b3b8-185">항목 번호 10과 같은 두 자리 항목의 경우 열 5로 들여씁니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-185">For double digits items, for example item number 10, you indent to column 5.</span></span>

1. <span data-ttu-id="1b3b8-186">다음 번호 매기기 항목은 여기에서 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-186">The next numbered item starts here.</span></span>

### <a name="images"></a><span data-ttu-id="1b3b8-187">이미지</span><span class="sxs-lookup"><span data-stu-id="1b3b8-187">Images</span></span>

<span data-ttu-id="1b3b8-188">이미지를 포함할 구문의 경우:</span><span class="sxs-lookup"><span data-stu-id="1b3b8-188">The syntax to include an image is:</span></span>

```markdown
![[alt text]](<folderPath>)

Example:
![Introduction](./media/overview/Introduction.png)
```

<span data-ttu-id="1b3b8-189">여기서 `alt text`는 이미지에 대한 간략한 설명이고 `<folder path>`는 이미지의 상대 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-189">Where `alt text` is a brief description of the image and `<folder path>` is a relative path to the image.</span></span> <span data-ttu-id="1b3b8-190">대체 텍스트는 시각 장애인을 위한 화면 읽기 프로그램에 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-190">Alternate text is required for screen readers for the visually impaired.</span></span> <span data-ttu-id="1b3b8-191">대체 텍스트는 이미지를 렌더링할 수 없는 사이트 버그가 있는 경우에도 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-191">It is also useful in case there is a site bug where the image cannot be rendered.</span></span>

<span data-ttu-id="1b3b8-192">이미지는 문서가 있는 폴더 내의 `media/<article-name>` 폴더에 저장해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-192">Images should be stored in a `media/<article-name>` folder within the folder containing the article.</span></span>
<span data-ttu-id="1b3b8-193">문서 간에 이미지를 공유하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-193">Images should not be shared between articles.</span></span> <span data-ttu-id="1b3b8-194">`media` 폴더 아래에 문서의 파일 이름과 일치하는 폴더를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-194">Create a folder that matches the filename of your article under the `media` folder.</span></span> <span data-ttu-id="1b3b8-195">해당 문서의 이미지를 새 폴더에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-195">Copy the images for that article to that new folder.</span></span> <span data-ttu-id="1b3b8-196">여러 문서에서 이미지를 사용하는 경우, 각 이미지 폴더에는 해당 이미지 파일의 복사본이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-196">If an image is used by multiple articles, each image folder must have a copy of that image file.</span></span> <span data-ttu-id="1b3b8-197">이렇게 하면 한 문서의 이미지를 변경해도 다른 문서는 영향을 받지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-197">This practice prevents a change to an image in one article affecting another article.</span></span>

<span data-ttu-id="1b3b8-198">`*.png`, `*.gif`, `*.jpeg`, `*.jpg`, `*.svg` 형식의 이미지 파일이 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-198">The following image file types are supported: `*.png`, `*.gif`, `*.jpeg`, `*.jpg`, `*.svg`</span></span>

### <a name="markdown-extensions-supported-by-open-publishing"></a><span data-ttu-id="1b3b8-199">Open Publishing이 지원하는 Markdown 확장</span><span class="sxs-lookup"><span data-stu-id="1b3b8-199">Markdown extensions supported by Open Publishing</span></span>

<span data-ttu-id="1b3b8-200">[Microsoft Docs Authoring Pack](/contribute/how-to-write-docs-auth-pack)에는 Microsoft 게시 시스템에 고유한 기능을 지원하는 도구가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-200">The [Microsoft Docs Authoring Pack](/contribute/how-to-write-docs-auth-pack) contains tools that support features unique to our publishing system.</span></span> <span data-ttu-id="1b3b8-201">경고는 콘텐츠의 중요도를 강조하는 색과 아이콘으로 docs.microsoft.com에서 렌더링되는 블록 따옴표를 만드는 Markdown 확장입니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-201">Alerts are a Markdown extension to create blockquotes that render on docs.microsoft.com with colors and icons that highlight the significance of the content.</span></span> <span data-ttu-id="1b3b8-202">다음 경고 유형이 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-202">The following alert types are supported:</span></span>

```markdown
> [!NOTE]
> Information the user should notice even if skimming.

> [!TIP]
> Optional information to help a user be more successful.

> [!IMPORTANT]
> Essential information required for user success.

> [!CAUTION]
> Negative potential consequences of an action.

> [!WARNING]
> Dangerous certain consequences of an action.
```

<span data-ttu-id="1b3b8-203">이러한 경고는 docs.microsoft.com에서 다음과 같이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-203">These alerts look like this on docs.microsoft.com:</span></span>

<span data-ttu-id="1b3b8-204">메모 블록</span><span class="sxs-lookup"><span data-stu-id="1b3b8-204">Note block</span></span>

> [!NOTE]
> <span data-ttu-id="1b3b8-205">훑어보는 경우에도 사용자가 주목해야 하는 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-205">Information the user should notice even if skimming.</span></span>

<span data-ttu-id="1b3b8-206">팁 블록</span><span class="sxs-lookup"><span data-stu-id="1b3b8-206">Tip block</span></span>

> [!TIP]
> <span data-ttu-id="1b3b8-207">사용자의 성공을 돕는 선택적 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-207">Optional information to help a user be more successful.</span></span>

<span data-ttu-id="1b3b8-208">중요 블록</span><span class="sxs-lookup"><span data-stu-id="1b3b8-208">Important block</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1b3b8-209">사용자의 성공에 필요한 필수 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-209">Essential information required for user success.</span></span>

<span data-ttu-id="1b3b8-210">주의 블록</span><span class="sxs-lookup"><span data-stu-id="1b3b8-210">Caution block</span></span>

> [!CAUTION]
> <span data-ttu-id="1b3b8-211">작업에서 발생할 수 있는 부정적 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-211">Negative potential consequences of an action.</span></span>

<span data-ttu-id="1b3b8-212">경고 블록</span><span class="sxs-lookup"><span data-stu-id="1b3b8-212">Warning block</span></span>

> [!WARNING]
> <span data-ttu-id="1b3b8-213">작업의 위험한 특정 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-213">Dangerous certain consequences of an action.</span></span>

### <a name="hyperlinks"></a><span data-ttu-id="1b3b8-214">하이퍼링크</span><span class="sxs-lookup"><span data-stu-id="1b3b8-214">Hyperlinks</span></span>

- <span data-ttu-id="1b3b8-215">하이퍼링크는 Markdown 구문(`[friendlyname](url-or-path)`)을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-215">Hyperlinks must use Markdown syntax `[friendlyname](url-or-path)`</span></span>
- <span data-ttu-id="1b3b8-216">링크는 가능하면 HTTPS 형식이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-216">Links should be HTTPS when possible.</span></span>
- <span data-ttu-id="1b3b8-217">링크에는 일반적으로 연결된 토픽의 제목인 식별 이름이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-217">Links must have a friendly name, usually the title of the linked topic</span></span>
- <span data-ttu-id="1b3b8-218">맨 아래의 "관련 링크" 섹션에 있는 항목은 모두 하이퍼링크로 처리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-218">All items in the "related links" section at the bottom should be hyperlinked</span></span>
- <span data-ttu-id="1b3b8-219">하이퍼링크의 대괄호 안에는 역따옴표, 굵은 글꼴 또는 기타 태그를 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-219">Do not use backticks, bold, or other markup inside the brackets of a hyperlink.</span></span>
- <span data-ttu-id="1b3b8-220">특정 URI에 대해 이야기할 때는 기본 URL을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-220">Bare URLs may be used when you are talking about a specific URI.</span></span> <span data-ttu-id="1b3b8-221">URI는 역따옴표로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-221">The URI must be enclosed in backticks.</span></span> <span data-ttu-id="1b3b8-222">다음은 그 예입니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-222">For example:</span></span>

  ```markdown
  By default, if you do not specify this parameter, the DMTF standard resource URI
  `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` is used and the class name is appended to it.
  ```

#### <a name="linking-to-other-content"></a><span data-ttu-id="1b3b8-223">다른 콘텐츠에 연결</span><span class="sxs-lookup"><span data-stu-id="1b3b8-223">Linking to other content</span></span>

<span data-ttu-id="1b3b8-224">게시 시스템에서 지원하는 하이퍼링크의 유형은</span><span class="sxs-lookup"><span data-stu-id="1b3b8-224">There are two types of hyperlinks supported by the publishing system:</span></span>

<span data-ttu-id="1b3b8-225">**URL 링크**는 docs.microsoft.com의 루트를 기준으로 하는 URL 경로이거나</span><span class="sxs-lookup"><span data-stu-id="1b3b8-225">A **URL link** can be a URL path that is relative to the root of docs.microsoft.com.</span></span> <span data-ttu-id="1b3b8-226">전체 URL 구문을 포함하는 절대 URL일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-226">Or an absolute URL that include the full URL syntax.</span></span> <span data-ttu-id="1b3b8-227">예: `https:/github.com/MicrosoftDocs/PowerShell-Docs`</span><span class="sxs-lookup"><span data-stu-id="1b3b8-227">For example: `https:/github.com/MicrosoftDocs/PowerShell-Docs`</span></span>

- <span data-ttu-id="1b3b8-228">PowerShell-Docs 외부 콘텐츠에 연결하거나 PowerShell-Docs 내의 cmdlet 참조와 개념 문서 사이를 연결하는 경우 URL 링크를 사용합니다. 상대 링크를 만드는 가장 간단한 방법은 브라우저에서 URL을 복사한 다음 Markdown에 붙여넣는 값에서 `https://docs.microsoft.com/en-us`를 제거하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-228">Use URL links when linking to content outside of PowerShell-Docs or between cmdlet reference and conceptual articles within PowerShell-docs. The simplest way to create a relative link is to copy the URL from your browser then remove `https://docs.microsoft.com/en-us` from the value you paste into markdown.</span></span>
- <span data-ttu-id="1b3b8-229">Microsoft 속성에서 URL에 로캘을 포함하지 마세요(예:</span><span class="sxs-lookup"><span data-stu-id="1b3b8-229">Do not include locales in URLs on Microsoft properties (eg.</span></span> <span data-ttu-id="1b3b8-230">URL에서 `/en-us`를 제거).</span><span class="sxs-lookup"><span data-stu-id="1b3b8-230">remove `/en-us` from URL).</span></span>
- <span data-ttu-id="1b3b8-231">문서의 특정 버전에 연결해야 하는 경우가 아니면 URL에서 불필요한 쿼리 매개 변수를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-231">Remove any unnecessary query parameters from the URL unless you need to link to a specific version of an article.</span></span> <span data-ttu-id="1b3b8-232">예제:</span><span class="sxs-lookup"><span data-stu-id="1b3b8-232">Examples:</span></span>
  - <span data-ttu-id="1b3b8-233">`?view=powershell-5.1` - PowerShell의 특정 버전에 연결하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-233">`?view=powershell-5.1` - this is used to link to a specific version of PowerShell</span></span>
  - <span data-ttu-id="1b3b8-234">`?redirectedfrom=MSDN` - 이전 문서에서 새 위치로 리디렉션될 때 URL에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-234">`?redirectedfrom=MSDN` - this is added to the URL when you get redirected from an old article to its new location</span></span>
- <span data-ttu-id="1b3b8-235">외부 웹 사이트에 대한 모든 URL은 대상 사이트에 유효하지 않은 경우가 아니라면 HTTPS를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-235">All URLs to external websites should use HTTPS unless that is not valid for the target site.</span></span>

<span data-ttu-id="1b3b8-236">**파일 링크**는 참조 문서를 다른 참조 문서로 또는 개념 문서를 다른 개념 문서로 연결하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-236">A **file link** is used to link from one reference article to another, or from one conceptual article to another.</span></span> <span data-ttu-id="1b3b8-237">특정 PowerShell 버전의 참조 문서에 연결해야 하는 경우 URL 링크를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-237">If you need to link to a reference article for a specific version of PowerShell, then you must use a URL link.</span></span>

- <span data-ttu-id="1b3b8-238">파일 링크에는 상대 파일 경로가 포함됩니다(예: `../folder/file.md`).</span><span class="sxs-lookup"><span data-stu-id="1b3b8-238">File links contain a relative file path (for example: `../folder/file.md`)</span></span>
- <span data-ttu-id="1b3b8-239">모든 파일 경로에는 슬래시(`/`) 문자를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-239">All file paths use forward-slash (`/`) characters</span></span>

<span data-ttu-id="1b3b8-240">URL 및 파일 링크 모두에 딥 링크를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-240">Deep linking is allowed on both URL and file links.</span></span> <span data-ttu-id="1b3b8-241">대상 경로의 끝에 앵커를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-241">Add the anchor to the end of the target path.</span></span>
<span data-ttu-id="1b3b8-242">다음은 그 예입니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-242">For example:</span></span>

- `[about_Splatting](about_Splatting.md#splatting-with-arrays)`
- `[custom key bindings](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings)`

<span data-ttu-id="1b3b8-243">자세한 내용은 [문서에서 링크 사용](https://docs.microsoft.com/contribute/how-to-write-links)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-243">For more information, see [Use links in documentation](https://docs.microsoft.com/contribute/how-to-write-links).</span></span>

## <a name="formatting-command-syntax-elements"></a><span data-ttu-id="1b3b8-244">명령 구문 요소 서식 지정</span><span class="sxs-lookup"><span data-stu-id="1b3b8-244">Formatting command syntax elements</span></span>

- <span data-ttu-id="1b3b8-245">cmdlet 및 매개 변수에는 항상 전체 이름을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-245">Always use the full name for cmdlets and parameters.</span></span> <span data-ttu-id="1b3b8-246">특별히 보여 주어야 하는 것이 아니라면 별칭을 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-246">Avoid using aliases unless you are specifically demonstrating the alias.</span></span>

- <span data-ttu-id="1b3b8-247">속성, 매개 변수, 개체, 형식 이름, 클래스 이름, 클래스 메서드는 **굵게** 표시해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-247">Property, parameter, object, type names, class names, class methods should be **bold**.</span></span>
  - <span data-ttu-id="1b3b8-248">속성 및 매개 변수 값은 역따옴표(`` ` ``)로 래핑해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-248">Property and parameter values should be wrapped in backticks (`` ` ``).</span></span>
  - <span data-ttu-id="1b3b8-249">대괄호로 묶은 스타일을 사용하여 형식을 참조하는 경우에는 역따옴표를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-249">When referring to types using the bracketed style, use backticks.</span></span> <span data-ttu-id="1b3b8-250">예: `[System.Io.FileInfo]`</span><span class="sxs-lookup"><span data-stu-id="1b3b8-250">For example: `[System.Io.FileInfo]`</span></span>

- <span data-ttu-id="1b3b8-251">언어 키워드, cmdlet 이름, 함수, 변수, 기본 EXE, 파일 경로, 인라인 구문 예제는 역따옴표(`` ` ``) 문자로 래핑해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-251">Language keywords, cmdlet names, functions, variables, native EXEs, file paths, and inline syntax examples should be wrapped in backtick (`` ` ``) characters.</span></span>

  <span data-ttu-id="1b3b8-252">다음은 그 예입니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-252">For example:</span></span>

  ~~~markdown
  The following code uses `Get-ChildItem` to list the contents of `C:\Windows` and assigns
  the output to the `$files` variable.

  ```powershell
  $files = Get-ChildItem C:\Windows
  ```
  ~~~

  - <span data-ttu-id="1b3b8-253">이름으로 매개 변수를 참조하는 경우에는 이름을 **굵게** 표시해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-253">When referring to a parameter by name, the name should be **bold**.</span></span> <span data-ttu-id="1b3b8-254">하이픈 접두사를 사용하여 매개 변수 사용을 보여 주는 경우, 매개 변수를 역따옴표으로 래핑해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-254">When illustrating the use of a parameter with the hyphen prefix, the parameter should be wrapped in backticks.</span></span> <span data-ttu-id="1b3b8-255">다음은 그 예입니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-255">For example:</span></span>

    ```markdown
    The parameter's name is **Name**, but it is typed as `-Name` when used on the command
    line as a parameter.
    ```

  - <span data-ttu-id="1b3b8-256">외부 명령의 사용 예제를 표시하는 경우, 예제를 역따옴표로 래핑해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-256">When showing example usage of an external command, the example should be wrapped in backticks.</span></span>
    <span data-ttu-id="1b3b8-257">항상 기본 명령에 파일 확장명을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-257">Always include the file extension in the native command.</span></span> <span data-ttu-id="1b3b8-258">다음은 그 예입니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-258">For example:</span></span>

    ```markdown
    To start the spooler service on a remote computer named DC01, you type `sc.exe \\DC01 start spooler`.
    ```

    <span data-ttu-id="1b3b8-259">파일 확장명을 포함하면 PowerShell의 명령 우선 순위에 따라 올바른 명령이 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-259">Including the file extension ensures that the correct command is executed according PowerShell's command precedence.</span></span>

- <span data-ttu-id="1b3b8-260">참조 콘텐츠가 아닌 개념 문서를 작성할 때, 처음으로 나오는 cmdlet 이름은 하이퍼링크로 cmdlet 설명서에 연결되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-260">When writing a conceptual article (as opposed to reference content), the first instance of a cmdlet name should be hyperlinked to the cmdlet documentation.</span></span> <span data-ttu-id="1b3b8-261">하이퍼링크의 대괄호 안에는 역따옴표, 굵은 글꼴 또는 기타 태그를 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-261">Do not use backticks, bold, or other markup inside the brackets of a hyperlink.</span></span>

  <span data-ttu-id="1b3b8-262">다음은 그 예입니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-262">For example:</span></span>

  ```markdown
  This [Write-Host](/powershell/module/Microsoft.PowerShell.Utility/Write-Host) cmdlet
  uses the **Object** parameter to ...
  ```

  <span data-ttu-id="1b3b8-263">자세한 내용은 이 문서의 [하이퍼링크](#hyperlinks) 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-263">For more information, see [Hyperlinks](#hyperlinks) section of this article.</span></span>

## <a name="markdown-for-code-samples"></a><span data-ttu-id="1b3b8-264">코드 샘플용 Markdown</span><span class="sxs-lookup"><span data-stu-id="1b3b8-264">Markdown for code samples</span></span>

<span data-ttu-id="1b3b8-265">Markdown은 다음 두 가지 코드 스타일을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-265">Markdown supports two different code styles:</span></span>

- <span data-ttu-id="1b3b8-266">**코드 범위(인라인)** - 단일 역따옴표(`` ` ``) 문자로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-266">**Code spans (inline)** - marked by a single backtick (`` ` ``) character.</span></span> <span data-ttu-id="1b3b8-267">독립 실행형 블록으로 사용되지 않고 단락 내에서 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-267">Used within a paragraph rather than as a standalone block.</span></span>
- <span data-ttu-id="1b3b8-268">**코드 블록** - 삼중 역따옴표(`` ``` ``) 문자열로 묶인 여러 줄의 블록입니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-268">**Code blocks** - a multi-line block surrounded by triple-backtick (`` ``` ``) strings.</span></span> <span data-ttu-id="1b3b8-269">코드 블록에는 역따옴표 뒤에 언어 레이블이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-269">Code blocks may also have a language label following the backticks.</span></span> <span data-ttu-id="1b3b8-270">언어 레이블로 코드 블록의 내용에 구문 강조 표시를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-270">The language label enables syntax highlighting for the contents of the code block.</span></span>

<span data-ttu-id="1b3b8-271">모든 코드 블록은 코드 펜스에 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-271">All code blocks should be contained in a code fence.</span></span> <span data-ttu-id="1b3b8-272">코드 블록에는 절대 들여쓰기를 사용하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-272">Never use indentation for code blocks.</span></span> <span data-ttu-id="1b3b8-273">Markdown은 이 패턴을 허용하지만 문제가 발생할 수 있으므로 피해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-273">Markdown allows this pattern but it can be problematic and should be avoided.</span></span>

<span data-ttu-id="1b3b8-274">코드 블록은 삼중 역따옴표(`` ``` ``) 코드 펜스로 둘러싸인 하나 이상의 코드 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-274">A code block is one or more lines of code surrounded by a triple-backtick (`` ``` ``) code fence.</span></span>
<span data-ttu-id="1b3b8-275">코드 펜스 마커는 코드 샘플 앞뒤의 고유한 줄에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-275">The code fence markers must be on their own line before and after the code sample.</span></span> <span data-ttu-id="1b3b8-276">코드 블록의 시작 부분에 있는 마커에는 선택적 언어 레이블이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-276">The marker at the start of the code block may have an optional language label.</span></span> <span data-ttu-id="1b3b8-277">Microsoft OPS(Open Publishing System)는 언어 레이블을 사용하여 구문 강조 표시 기능을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-277">Microsoft's Open Publishing System (OPS) uses the language label to support the syntax highlighting feature.</span></span>

<span data-ttu-id="1b3b8-278">지원되는 언어 태그의 전체 목록은 중앙 참가자 가이드의 [펜스된 코드 블록](/contribute/code-in-docs#fenced-code-blocks)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-278">For a full list of supported language tags, see [Fenced code blocks](/contribute/code-in-docs#fenced-code-blocks) in the centralized contributor guide.</span></span>

<span data-ttu-id="1b3b8-279">또한 OPS는 코드 블록의 내용을 클립보드에 복사하는 **복사** 단추를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-279">OPS also adds a **Copy** button that copies the contents of the code block to the clipboard.</span></span> <span data-ttu-id="1b3b8-280">그러면 스크립트에 코드를 빠르게 붙여넣어서 코드 샘플을 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-280">This allows you to quickly paste the code into a script to test the code sample.</span></span> <span data-ttu-id="1b3b8-281">하지만 설명서의 모든 예제가 그대로 실행된다고 간주하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-281">However, not all examples in our documentation are intended to be run as-is.</span></span> <span data-ttu-id="1b3b8-282">일부 코드 블록은 PowerShell 개념의 간단한 예시입니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-282">Some code blocks are simple illustrations of a PowerShell concept.</span></span>

<span data-ttu-id="1b3b8-283">설명서에 사용되는 코드 블록에는 다음 세 가지 형식이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-283">There are three types code blocks used in our documentation:</span></span>

1. <span data-ttu-id="1b3b8-284">구문 블록</span><span class="sxs-lookup"><span data-stu-id="1b3b8-284">Syntax blocks</span></span>
1. <span data-ttu-id="1b3b8-285">설명 예제</span><span class="sxs-lookup"><span data-stu-id="1b3b8-285">Illustrative examples</span></span>
1. <span data-ttu-id="1b3b8-286">실행 파일 예제</span><span class="sxs-lookup"><span data-stu-id="1b3b8-286">Executable examples</span></span>

### <a name="syntax-code-blocks"></a><span data-ttu-id="1b3b8-287">구문 코드 블록</span><span class="sxs-lookup"><span data-stu-id="1b3b8-287">Syntax code blocks</span></span>

<span data-ttu-id="1b3b8-288">구문 코드 블록은 명령의 구문 구조를 설명하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-288">Syntax code blocks are used to describe the syntactic structure of a command.</span></span> <span data-ttu-id="1b3b8-289">코드 펜스에서 언어 태그를 사용하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-289">Do not use a language tag on the code fence.</span></span> <span data-ttu-id="1b3b8-290">이 예제는 `Get-Command` cmdlet의 가능한 모든 매개 변수를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-290">This example illustrates all the possible parameters of the `Get-Command` cmdlet.</span></span>

~~~markdown
```
Get-Command [-Verb <String[]>] [-Noun <String[]>] [-Module <String[]>]
  [-FullyQualifiedModule <ModuleSpecification[]>] [-TotalCount <Int32>] [-Syntax]
  [-ShowCommandInfo] [[-ArgumentList] <Object[]>] [-All] [-ListImported]
  [-ParameterName <String[]>] [-ParameterType <PSTypeName[]>] [<CommonParameters>]
```
~~~

<span data-ttu-id="1b3b8-291">이 예제는 일반적인 용어로 `for` 문을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-291">This example describes the `for` statement in generalized terms:</span></span>

~~~markdown
```
for (<init>; <condition>; <repeat>)
{<statement list>}
```
~~~

### <a name="illustrative-examples"></a><span data-ttu-id="1b3b8-292">설명 예제</span><span class="sxs-lookup"><span data-stu-id="1b3b8-292">Illustrative examples</span></span>

<span data-ttu-id="1b3b8-293">설명 예제는 PowerShell 개념을 설명하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-293">Illustrative examples are used to explain a PowerShell concept.</span></span> <span data-ttu-id="1b3b8-294">실행을 위해 클립보드로 복사하기 위한 예제가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-294">They are not meant to be copied to the clipboard for execution.</span></span> <span data-ttu-id="1b3b8-295">이 예제는 쉽게 입력하고 이해할 수 있는 간단한 예제에 가장 흔히 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-295">These are most commonly used for simple examples that are easy to type and easy to understand.</span></span> <span data-ttu-id="1b3b8-296">코드 블록에는 PowerShell 프롬프트와 예제 출력이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-296">The code block can include the PowerShell prompt and example output.</span></span>

<span data-ttu-id="1b3b8-297">다음은 PowerShell 비교 연산자를 보여주는 간단한 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-297">Here is a simple example illustrating the PowerShell comparison operators.</span></span> <span data-ttu-id="1b3b8-298">이 예제는 독자가 복사하고 실행하는 것이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-298">In this case, we don't intend the reader to copy and run this example.</span></span>

~~~markdown
```powershell
PS> 2 -eq 2
True

PS> 2 -eq 3
False

PS>  1,2,3 -eq 2
2

PS> "abc" -eq "abc"
True

PS> "abc" -eq "abc", "def"
False

PS> "abc", "def" -eq "abc"
abc
```
~~~

### <a name="executable-examples"></a><span data-ttu-id="1b3b8-299">실행 파일 예제</span><span class="sxs-lookup"><span data-stu-id="1b3b8-299">Executable examples</span></span>

<span data-ttu-id="1b3b8-300">더 복잡한 예제나 복사 및 실행될 예제에는 다음 블록 스타일 표시를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-300">Complex examples, or examples that are intended to be copied and executed, should use the following block-style markup:</span></span>

~~~markdown
```powershell
<Your PowerShell code goes here>
```
~~~

<span data-ttu-id="1b3b8-301">PowerShell 명령이 표시하는 출력은 구문 강조 표시를 방지하기 위해 **출력** 코드 블록으로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-301">The output displayed by PowerShell commands should be enclosed in an **Output** code block to prevent syntax highlighting.</span></span> <span data-ttu-id="1b3b8-302">다음은 그 예입니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-302">For example:</span></span>

~~~markdown
```powershell
Get-Command -Module Microsoft.PowerShell.Security
```

```Output
CommandType  Name                        Version    Source
-----------  ----                        -------    ------
Cmdlet       ConvertFrom-SecureString    3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       ConvertTo-SecureString      3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-Acl                     3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-AuthenticodeSignature   3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-CmsMessage              3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-Credential              3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-ExecutionPolicy         3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-PfxCertificate          3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       New-FileCatalog             3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Protect-CmsMessage          3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Set-Acl                     3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Set-AuthenticodeSignature   3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Set-ExecutionPolicy         3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Test-FileCatalog            3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Unprotect-CmsMessage        3.0.0.0    Microsoft.PowerShell.Security
```
~~~

<span data-ttu-id="1b3b8-303">**출력** 코드 레이블은 구문 강조 표시 시스템에서 지원하는 공식 "언어"가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-303">The **Output** code label is not an official "language" supported by the syntax highlighting system.</span></span>
<span data-ttu-id="1b3b8-304">그러나 이 레이블은 OPS가 웹 페이지의 코드 상자 프레임에 "출력" 레이블을 추가하기 때문에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-304">However, this label is useful because OPS adds the "Output" label to the code box frame on the web page.</span></span> <span data-ttu-id="1b3b8-305">"출력" 코드 상자에는 구문 강조 표시가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-305">The "Output" code box has no syntax highlighting.</span></span>

## <a name="coding-style-rules"></a><span data-ttu-id="1b3b8-306">코딩 스타일 규칙</span><span class="sxs-lookup"><span data-stu-id="1b3b8-306">Coding style rules</span></span>

### <a name="avoid-line-continuation-in-code-samples"></a><span data-ttu-id="1b3b8-307">코드 샘플에서 줄 연속 사용하지 않음</span><span class="sxs-lookup"><span data-stu-id="1b3b8-307">Avoid line continuation in code samples</span></span>

<span data-ttu-id="1b3b8-308">PowerShell 코드 예제에서 줄 연속 문자(`` ` ``)를 사용하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-308">Avoid using line continuation characters (`` ` ``) in PowerShell code examples.</span></span> <span data-ttu-id="1b3b8-309">줄 연속 문자는 가독성이 떨어지며, 줄의 끝에 추가 공백이 있는 경우 문제를 일으킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-309">These are hard to see and can cause problems if there are extra spaces at the end of the line.</span></span>

- <span data-ttu-id="1b3b8-310">매개 변수가 많은 cmdlet의 줄 길이를 줄이려면 PowerShell 스플래팅을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-310">Use PowerShell splatting to reduce line length for cmdlets that have a lot of parameters.</span></span>
- <span data-ttu-id="1b3b8-311">파이프(`|`) 문자 뒤, 여는 중괄호, 괄호, 대괄호 등 PowerShell의 자연스러운 줄 바꿈 방법을 활용하세요.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-311">Take advantage of PowerShell's natural line break opportunities, like after pipe (`|`) characters, opening braces, parentheses, and brackets.</span></span>

### <a name="avoid-using-powershell-prompts-in-examples"></a><span data-ttu-id="1b3b8-312">예제에서 PowerShell 프롬프트 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="1b3b8-312">Avoid using PowerShell prompts in examples</span></span>

<span data-ttu-id="1b3b8-313">프롬프트 문자열은 사용하지 않는 것이 좋으며, 명령줄 사용법을 보여 주는 시나리오에만 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-313">Use of the prompt string is discouraged and should be limited to scenarios that are meant to illustrate command line usage.</span></span> <span data-ttu-id="1b3b8-314">이러한 예제 대부분에서 프롬프트 문자열은 `PS>`여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-314">For most of these examples, the prompt string should be `PS>`.</span></span> <span data-ttu-id="1b3b8-315">이 프롬프트는 OS별 표시기와는 독립적입니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-315">This prompt is independent of OS-specific indicators.</span></span>

<span data-ttu-id="1b3b8-316">프롬프트는 프롬프트를 변경하는 명령을 보여 주는 예제나 표시 경로가 예시 시나리오에 중요한 경우 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-316">Prompts are required for examples that illustrate commands that alter the prompt or when the path displayed is significant to the scenario being illustrated.</span></span> <span data-ttu-id="1b3b8-317">다음 예제는 레지스트리 공급자를 사용할 때 프롬프트가 변경되는 방식을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-317">The following example illustrates how the prompt changes when using the Registry provider.</span></span>

```powershell
PS C:\> cd HKCU:\System\
PS HKCU:\System\> dir

    Hive: HKEY_CURRENT_USER\System

Name                   Property
----                   --------
CurrentControlSet
GameConfigStore        GameDVR_Enabled                       : 1
                       GameDVR_FSEBehaviorMode               : 2
                       Win32_AutoGameModeDefaultProfile      : {2, 0, 1, 0...}
                       Win32_GameModeRelatedProcesses        : {1, 0, 1, 0...}
                       GameDVR_HonorUserFSEBehaviorMode      : 0
                       GameDVR_DXGIHonorFSEWindowsCompatible : 0
```

### <a name="do-not-use-aliases-in-examples"></a><span data-ttu-id="1b3b8-318">예제에서 별칭 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="1b3b8-318">Do not use aliases in examples</span></span>

<span data-ttu-id="1b3b8-319">별칭에 대해 구체적으로 이야기해야 하는 경우가 아니라면 항상 모든 cmdlet과 매개 변수의 전체 이름을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-319">You should always use the full name of all cmdlets and parameters unless you are specifically talking about the alias.</span></span> <span data-ttu-id="1b3b8-320">Cmdlet 및 매개 변수 이름은 적절한 파스칼식 대/소문자를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-320">Cmdlet and parameter names must use the proper Pascal-cased names.</span></span>

### <a name="using-parameters-in-examples"></a><span data-ttu-id="1b3b8-321">예제에서 매개 변수 사용</span><span class="sxs-lookup"><span data-stu-id="1b3b8-321">Using parameters in examples</span></span>

<span data-ttu-id="1b3b8-322">위치 매개 변수 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="1b3b8-322">Avoid using positional parameters.</span></span> <span data-ttu-id="1b3b8-323">일반적으로 매개 변수가 위치 매개 변수인 경우에도 항상 매개 변수 이름을 예제에 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-323">In general, you should always include the parameter name in an example, even if the parameter is positional.</span></span> <span data-ttu-id="1b3b8-324">이렇게 하면 예제에서 혼동 가능성이 줄어듭니다.</span><span class="sxs-lookup"><span data-stu-id="1b3b8-324">This reduces the chance of confusion in your examples.</span></span>

## <a name="next-steps"></a><span data-ttu-id="1b3b8-325">다음 단계</span><span class="sxs-lookup"><span data-stu-id="1b3b8-325">Next steps</span></span>

[<span data-ttu-id="1b3b8-326">cmdlet 참조 편집</span><span class="sxs-lookup"><span data-stu-id="1b3b8-326">Editing cmdlet reference</span></span>](editing-cmdlet-ref.md)

<!-- External URLs -->
[platyPS]: https://github.com/PowerShell/platyPS
[markdig]: https://github.com/lunet-io/markdig
[CommonMark]: https://spec.commonmark.org/
[atx]: https://github.github.com/gfm/#atx-headings
[pascal-case]: https://en.wikipedia.org/wiki/PascalCase
[reflow]: https://marketplace.visualstudio.com/items?itemName=marvhen.reflow-markdown
