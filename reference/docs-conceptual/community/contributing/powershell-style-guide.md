---
title: PowerShell-Docs 스타일 가이드
description: 이 문서에서는 PowerShell 설명서 작성을 위한 스타일 규칙을 제공합니다.
ms.date: 12/09/2020
ms.topic: conceptual
ms.openlocfilehash: 6f23f63cffc9fed9cbbcf84539875bfaf4247732
ms.sourcegitcommit: 61765d08321623743dc5db5367160f6982fe7857
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/12/2020
ms.locfileid: "99600615"
---
# <a name="powershell-docs-style-guide"></a><span data-ttu-id="21501-103">PowerShell-Docs 스타일 가이드</span><span class="sxs-lookup"><span data-stu-id="21501-103">PowerShell-Docs style guide</span></span>

<span data-ttu-id="21501-104">이 문서에서는 PowerShell-Docs 콘텐츠에 관한 스타일 지침을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-104">This article provides style guidance specific to the PowerShell-Docs content.</span></span> <span data-ttu-id="21501-105">[개요](overview.md#get-started-writing-docs)에 설명 된 정보를 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-105">It builds on the information outlined in the [Overview](overview.md#get-started-writing-docs).</span></span>

## <a name="product-terminology"></a><span data-ttu-id="21501-106">제품 용어</span><span class="sxs-lookup"><span data-stu-id="21501-106">Product Terminology</span></span>

<span data-ttu-id="21501-107">PowerShell에는 몇 가지 변형이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21501-107">There are several variants of PowerShell.</span></span>

- <span data-ttu-id="21501-108">**PowerShell** - 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="21501-108">**PowerShell** - This is the default.</span></span> <span data-ttu-id="21501-109">PowerShell 7 이상을 진정한 PowerShell이 아닌 것으로 간주 합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-109">We consider PowerShell 7 and beyond to be the one, true PowerShell.</span></span>
- <span data-ttu-id="21501-110">**PowerShell Core** - .NET Core를 기반으로 빌드된 PowerShell입니다.</span><span class="sxs-lookup"><span data-stu-id="21501-110">**PowerShell Core** - PowerShell built on .NET Core.</span></span> <span data-ttu-id="21501-111">**핵심** 이라는 용어는 Windows PowerShell과 구분 해야 하는 경우에만 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-111">Usage of the term **Core** should be limited to cases where it's necessary to differentiate it from Windows PowerShell.</span></span>
- <span data-ttu-id="21501-112">**Windows PowerShell** - .NET Framework를 기반으로 빌드된 PowerShell입니다.</span><span class="sxs-lookup"><span data-stu-id="21501-112">**Windows PowerShell** - PowerShell built on .NET Framework.</span></span> <span data-ttu-id="21501-113">Windows PowerShell은 Windows에만 제공되며 전체 Framework가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-113">Windows PowerShell ships only on Windows and requires the complete Framework.</span></span>

  <span data-ttu-id="21501-114">일반적으로 설명서의 "Windows PowerShell"에 대 한 참조를 _PowerShell_ 로 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21501-114">In general, references to "Windows PowerShell" in documentation can be changed to _PowerShell_.</span></span>
  <span data-ttu-id="21501-115">_Windows powershell_ 특정 동작을 설명 하는 경우 "windows powershell"을 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-115">"Windows PowerShell" should be used when _Windows PowerShell_-specific behavior is being discussed.</span></span>

<span data-ttu-id="21501-116">관련 제품</span><span class="sxs-lookup"><span data-stu-id="21501-116">Related products</span></span>

- <span data-ttu-id="21501-117">**Visual Studio Code (VS Code)** -Microsoft의 무료 오픈 소스 편집기입니다.</span><span class="sxs-lookup"><span data-stu-id="21501-117">**Visual Studio Code (VS Code)** - This is Microsoft's free, open-source editor.</span></span> <span data-ttu-id="21501-118">처음 언급할 때는 전체 이름을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-118">At first mention, the full name should be used.</span></span> <span data-ttu-id="21501-119">그런 다음 **VS Code** 라고 언급할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21501-119">After that you may use **VS Code**.</span></span> <span data-ttu-id="21501-120">"VSCode"를 사용 하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="21501-120">Don't use "VSCode".</span></span>
- <span data-ttu-id="21501-121">**Visual Studio Code에 대한 Powershell 확장** - 확장은 VS Code를 PowerShell의 기본 IDE로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-121">**PowerShell Extension for Visual Studio Code** - The extension turns VS Code into the preferred IDE for PowerShell.</span></span> <span data-ttu-id="21501-122">처음 언급할 때는 전체 이름을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-122">At first mention, the full name should be used.</span></span> <span data-ttu-id="21501-123">그런 다음 **PowerShell 확장** 이라고 언급할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21501-123">After that you may use **PowerShell extension**.</span></span>
- <span data-ttu-id="21501-124">**Azure PowerShell** - Azure 서비스를 관리하는 데 사용되는 Powershell 모듈의 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="21501-124">**Azure PowerShell** - This is the collection of PowerShell modules used to manage Azure services.</span></span>
- <span data-ttu-id="21501-125">**Azure Stack PowerShell** - Microsoft의 하이브리드 클라우드 솔루션을 관리하는 데 사용되는 Powershell 모듈의 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="21501-125">**Azure Stack PowerShell** - This is the collection of PowerShell modules used to manage Microsoft's hybrid cloud solution.</span></span>

## <a name="markdown-specifics"></a><span data-ttu-id="21501-126">Markdown 세부보</span><span class="sxs-lookup"><span data-stu-id="21501-126">Markdown specifics</span></span>

<span data-ttu-id="21501-127">설명서를 빌드하는 Microsoft OPS(Open Publishing System)는 [markdig][]를 사용하여 Markdown 문서를 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-127">The Microsoft Open Publishing System (OPS) that builds our documentation uses [markdig][] to process the Markdown documents.</span></span> <span data-ttu-id="21501-128">markdig는 최신 [CommonMark][] 사양의 규칙에 따라 문서를 구문 분석합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-128">Markdig parses the documents based on the rules of the latest [CommonMark][] specification.</span></span>

<span data-ttu-id="21501-129">새 CommonMark 사양은 일부 Markdown 요소 생성에 대해 훨씬 더 엄격하게 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="21501-129">The new CommonMark spec is much stricter about the construction of some Markdown elements.</span></span> <span data-ttu-id="21501-130">이 문서에 제공된 세부 정보에 각별히 주의하세요.</span><span class="sxs-lookup"><span data-stu-id="21501-130">Pay close attention to the details provided in this document.</span></span>

### <a name="blank-lines-spaces-and-tabs"></a><span data-ttu-id="21501-131">빈 줄, 공백, 탭</span><span class="sxs-lookup"><span data-stu-id="21501-131">Blank lines, spaces, and tabs</span></span>

<span data-ttu-id="21501-132">또한 빈 줄은 Markdown에서 블록이 끝난다는 신호입니다.</span><span class="sxs-lookup"><span data-stu-id="21501-132">Blank lines also signal the end of a block in Markdown.</span></span> <span data-ttu-id="21501-133">서로 다른 형식의 Markdown 블록 사이(예: 단락과 목록 또는 헤더 사이)에는 빈 줄이 하나 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-133">There should be a single blank between Markdown blocks of different types (for example, between a paragraph and a list or header).</span></span>

<span data-ttu-id="21501-134">여러 개의 연속 된 빈 줄은 HTML에서 하나의 빈 줄로 렌더링 됩니다.</span><span class="sxs-lookup"><span data-stu-id="21501-134">Multiple consecutive blank lines render as a single blank line in HTML.</span></span> <span data-ttu-id="21501-135">용도는 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="21501-135">They serve no purpose.</span></span>
<span data-ttu-id="21501-136">코드 블록 내에서 연속 된 빈 줄은 코드 블록을 중단 합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-136">Within a code block, consecutive blank lines break the code block.</span></span>

<span data-ttu-id="21501-137">줄의 끝부분에서 추가 공백을 제거해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-137">Remove extra spaces at the end of lines.</span></span>

> [!NOTE]
> <span data-ttu-id="21501-138">Markdown에서는 간격이 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-138">Spacing is significant in Markdown.</span></span> <span data-ttu-id="21501-139">항상 하드 탭 대신 공백을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="21501-139">Always uses spaces instead of hard tabs.</span></span> <span data-ttu-id="21501-140">후행 공백은 Markdown이 렌더링하는 방식을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21501-140">Trailing spaces can change how Markdown renders.</span></span>

### <a name="titles-and-headings"></a><span data-ttu-id="21501-141">제목 및 머리글</span><span class="sxs-lookup"><span data-stu-id="21501-141">Titles and headings</span></span>

<span data-ttu-id="21501-142">[ATX 머리글][atx](`=` 또는 `-` 스타일 헤더가 아닌 # 스타일)만 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-142">Only use [ATX headings][atx] (# style, as opposed to `=` or `-` style headers).</span></span>

- <span data-ttu-id="21501-143">문장의 첫 글자를 대문자로 시작하세요. 고유 명사와 제목 또는 헤더의 첫 글자만 대문자로 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-143">Use sentence case - only proper nouns and the first letter of a title or header should be capitalized</span></span>
- <span data-ttu-id="21501-144">`#`와 머리글의 첫 문자 사이에는 공백이 하나 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-144">There must be a single space between the `#` and the first letter of the heading</span></span>
- <span data-ttu-id="21501-145">머리글은 빈 줄 하나로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-145">Headings should be surrounded by a single blank line</span></span>
- <span data-ttu-id="21501-146">H1은 문서당 하나만 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-146">Only one H1 per document</span></span>
- <span data-ttu-id="21501-147">헤더 수준은 1씩 증가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-147">Header levels should increment by one.</span></span> <span data-ttu-id="21501-148">수준 건너뛰기 안 함</span><span class="sxs-lookup"><span data-stu-id="21501-148">Don't skip levels</span></span>
- <span data-ttu-id="21501-149">머리글에 굵은 또는 기타 태그를 사용 하지 않음</span><span class="sxs-lookup"><span data-stu-id="21501-149">Don't use bold or other markup in headers</span></span>

### <a name="limit-line-length-to-100-characters"></a><span data-ttu-id="21501-150">줄 길이는 100자로 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-150">Limit line length to 100 characters</span></span>

<span data-ttu-id="21501-151">이는 개념 문서와 cmdlet 참조에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="21501-151">This applies to conceptual articles and cmdlet reference.</span></span> <span data-ttu-id="21501-152">줄 길이를 제한하면 git diff의 가독성과 기록이 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="21501-152">Limiting the line length improves the readability of git diffs and history.</span></span> <span data-ttu-id="21501-153">또한 다른 작성자가 보다 쉽게 기여할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21501-153">It also makes it easier for other writers to make contributions.</span></span>

<span data-ttu-id="21501-154">사전 설정된 줄 길이에 맞게 단락을 쉽게 재배치하려면 Visual Studio Code에서 [Reflow Markdown][reflow] 확장을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-154">Use the [Reflow Markdown][reflow] extension in Visual Studio Code to easily reflow paragraphs to fit the prescribed line length.</span></span>

<span data-ttu-id="21501-155">about_topics는 80자로 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="21501-155">About_topics are limited to 80 characters.</span></span> <span data-ttu-id="21501-156">자세한 내용은 [About_ 파일 서식 지정](#formatting-about_-files)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="21501-156">For more specific information, see [Formatting About_ files](#formatting-about_-files).</span></span>

### <a name="lists"></a><span data-ttu-id="21501-157">목록</span><span class="sxs-lookup"><span data-stu-id="21501-157">Lists</span></span>

<span data-ttu-id="21501-158">목록에 여러 문장이 나 단락이 포함 되어 있으면 목록 대신 하위 수준 헤더를 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="21501-158">If your list contains multiple sentences or paragraphs, consider using a sublevel header rather than a list.</span></span>

<span data-ttu-id="21501-159">목록은 빈 줄 하나로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-159">List should be surrounded by a single blank line.</span></span>

#### <a name="unordered-lists"></a><span data-ttu-id="21501-160">순서가 지정되지 않은 목록</span><span class="sxs-lookup"><span data-stu-id="21501-160">Unordered lists</span></span>

<span data-ttu-id="21501-161">여러 문장을 포함 하지 않는 한 마침표를 사용 하 여 목록 항목을 종료 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="21501-161">Don't end list items with a period unless they contain multiple sentences.</span></span> <span data-ttu-id="21501-162">목록 항목 글머리 기호에 하이픈 문자(`-`)를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-162">Use the hyphen character (`-`) for list item bullets.</span></span> <span data-ttu-id="21501-163">이렇게 하면 별표[`*`]를 사용하는 굵게 또는 기울임꼴 태그와의 혼동을 피할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21501-163">This avoids confusion with bold or italic markup that uses the asterisk [`*`].</span></span> <span data-ttu-id="21501-164">글머리 기호 항목 아래에 단락이나 기타 요소를 포함하려면 줄 바꿈을 삽입하고 글머리 기호 뒤 첫 번째 문자에 들여쓰기를 맞춥니다.</span><span class="sxs-lookup"><span data-stu-id="21501-164">To include a paragraph or other elements under a bullet item, insert a line break and align indentation with the first character after the bullet.</span></span>

<span data-ttu-id="21501-165">다음은 그 예입니다.</span><span class="sxs-lookup"><span data-stu-id="21501-165">For example:</span></span>

```markdown
This is a list that contain child elements under a bullet item.

- First bullet item

  Sentence explaining the first bullet.

  - Child bullet item

    Sentence explaining the child bullet.

- Second bullet item
- Third bullet item
```

<span data-ttu-id="21501-166">글머리 기호 항목 아래의 자식 요소를 포함 하는 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="21501-166">This is a list that contains child elements under a bullet item.</span></span>

- <span data-ttu-id="21501-167">첫 번째 글머리 기호 항목</span><span class="sxs-lookup"><span data-stu-id="21501-167">First bullet item</span></span>

  <span data-ttu-id="21501-168">첫 번째 글머리 기호를 설명하는 문장입니다.</span><span class="sxs-lookup"><span data-stu-id="21501-168">Sentence explaining the first bullet.</span></span>

  - <span data-ttu-id="21501-169">자식 글머리 기호 항목</span><span class="sxs-lookup"><span data-stu-id="21501-169">Child bullet item</span></span>

    <span data-ttu-id="21501-170">자식 글머리 기호를 설명 하는 문장입니다.</span><span class="sxs-lookup"><span data-stu-id="21501-170">Sentence explaining the child bullet.</span></span>

- <span data-ttu-id="21501-171">두 번째 글머리 기호 항목</span><span class="sxs-lookup"><span data-stu-id="21501-171">Second bullet item</span></span>
- <span data-ttu-id="21501-172">세 번째 글머리 기호 항목</span><span class="sxs-lookup"><span data-stu-id="21501-172">Third bullet item</span></span>

#### <a name="ordered-lists"></a><span data-ttu-id="21501-173">순서가 지정된 목록</span><span class="sxs-lookup"><span data-stu-id="21501-173">Ordered lists</span></span>

<span data-ttu-id="21501-174">번호 매기기 항목 아래에 단락이나 기타 요소를 포함하려면 항목 번호 뒤 첫 번째 문자에 들여쓰기를 맞춥니다.</span><span class="sxs-lookup"><span data-stu-id="21501-174">To include a paragraph or other elements under a numbered item, align indentation with the first character after the item number.</span></span> <span data-ttu-id="21501-175">번호 매기기 목록의 모든 항목은 각 항목을 증가시키는 것이 아니라 숫자 `1.`을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-175">All items in a numbered listed should use the number `1.` rather than incrementing each item.</span></span> <span data-ttu-id="21501-176">Markdown 렌더링은 값을 자동으로 증가시킵니다.</span><span class="sxs-lookup"><span data-stu-id="21501-176">Markdown rendering increments the value automatically.</span></span> <span data-ttu-id="21501-177">이렇게 하면 보다 쉽게 항목 순서를 다시 매기고 하위 콘텐츠의 들여쓰기를 표준화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21501-177">This makes reordering items easier and standardizes the indentation of subordinate content.</span></span>

<span data-ttu-id="21501-178">다음은 그 예입니다.</span><span class="sxs-lookup"><span data-stu-id="21501-178">For example:</span></span>

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

<span data-ttu-id="21501-179">결과 Markdown은 다음과 같이 렌더링됩니다.</span><span class="sxs-lookup"><span data-stu-id="21501-179">The resulting Markdown is rendered as follows:</span></span>

1. <span data-ttu-id="21501-180">첫 번째 요소의 경우 1 뒤에 단일 공백을 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-180">For the first element, insert a single space after the 1.</span></span> <span data-ttu-id="21501-181">긴 문장은 다음 줄로 줄바꿈되어야 하며, 번호 매기기 목록 마커 뒤의 첫 번째 문자에 맞춰야 합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-181">Long sentences should be wrapped to the next line and must line up with the first character after the numbered list marker.</span></span>

   <span data-ttu-id="21501-182">(다음과 같은) 두 번째 요소를 포함하려면 첫 번째 요소 뒤에 줄 바꿈을 삽입하고 들여쓰기를 정렬합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-182">To include a second element (like this one), insert a line break after the first and align indentations.</span></span> <span data-ttu-id="21501-183">두 번째 요소의 들여쓰기는 번호 매기기 목록 마커 뒤의 첫 번째 문자에 맞춰야 합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-183">The indentation of the second element must line up with the first character after the numbered list marker.</span></span> <span data-ttu-id="21501-184">이와 같은 한 자리 항목의 경우 열 4로 들여씁니다.</span><span class="sxs-lookup"><span data-stu-id="21501-184">For single digit items, like this one, you indent to column 4.</span></span> <span data-ttu-id="21501-185">항목 번호 10과 같은 두 자리 항목의 경우 열 5로 들여씁니다.</span><span class="sxs-lookup"><span data-stu-id="21501-185">For double digits items, for example item number 10, you indent to column 5.</span></span>

1. <span data-ttu-id="21501-186">다음 번호 매기기 항목은 여기에서 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="21501-186">The next numbered item starts here.</span></span>

### <a name="images"></a><span data-ttu-id="21501-187">이미지</span><span class="sxs-lookup"><span data-stu-id="21501-187">Images</span></span>

<span data-ttu-id="21501-188">이미지를 포함할 구문의 경우:</span><span class="sxs-lookup"><span data-stu-id="21501-188">The syntax to include an image is:</span></span>

```markdown
![[alt text]](<folderPath>)

Example:
![Introduction](./media/overview/Introduction.png)
```

<span data-ttu-id="21501-189">여기서 `alt text`는 이미지에 대한 간략한 설명이고 `<folder path>`는 이미지의 상대 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="21501-189">Where `alt text` is a brief description of the image and `<folder path>` is a relative path to the image.</span></span> <span data-ttu-id="21501-190">대체 텍스트는 시각 장애인을 위한 화면 읽기 프로그램에 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-190">Alternate text is required for screen readers for the visually impaired.</span></span>

<span data-ttu-id="21501-191">이미지는 `media/<article-name>` 문서를 포함 하는 폴더 내의 폴더에 저장 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-191">Images should be stored in a `media/<article-name>` folder within the folder containing the article.</span></span>
<span data-ttu-id="21501-192">문서 간에 이미지를 공유 하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="21501-192">Don't share images between articles.</span></span> <span data-ttu-id="21501-193">`media` 폴더 아래 문서의 파일 이름과 일치하는 폴더를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="21501-193">Create a folder that matches the filename of your article under the `media` folder.</span></span> <span data-ttu-id="21501-194">해당 문서의 이미지를 해당하는 새 폴더로 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-194">Copy the images for that article to that new folder.</span></span> <span data-ttu-id="21501-195">이미지가 여러 문서에서 사용되는 경우 각 이미지 폴더에는 해당 이미지 파일의 복사본이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-195">If an image is used by multiple articles, each image folder must have a copy of that image file.</span></span> <span data-ttu-id="21501-196">이 사례에서는 다른 문서에 영향을 주는 문서에서 이미지가 변경되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="21501-196">This practice prevents a change to an image in one article affecting another article.</span></span>

<span data-ttu-id="21501-197">다음 이미지 파일 형식이 지원 됩니다. `*.png` ,, `*.gif` `*.jpeg` , `*.jpg` , `*.svg`</span><span class="sxs-lookup"><span data-stu-id="21501-197">The following image file types are supported: `*.png`, `*.gif`, `*.jpeg`, `*.jpg`, `*.svg`</span></span>

### <a name="markdown-extensions-supported-by-open-publishing"></a><span data-ttu-id="21501-198">공개 게시에서 지원되는 Markdown 확장</span><span class="sxs-lookup"><span data-stu-id="21501-198">Markdown extensions supported by Open Publishing</span></span>

<span data-ttu-id="21501-199">[Microsoft Docs Authoring Pack](/contribute/how-to-write-docs-auth-pack) 에는 게시 시스템에 고유한 기능을 지 원하는 도구가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21501-199">The [Microsoft Docs Authoring Pack](/contribute/how-to-write-docs-auth-pack) contains tools that support features unique to our publishing system.</span></span> <span data-ttu-id="21501-200">경고는 콘텐츠의 중요도를 강조 하는 색 및 아이콘을 사용 하 여 docs.microsoft.com에서 렌더링 하는 블록 따옴표를 만드는 Markdown 확장입니다.</span><span class="sxs-lookup"><span data-stu-id="21501-200">Alerts are a Markdown extension to create blockquotes that render on docs.microsoft.com with colors and icons that highlight the significance of the content.</span></span> <span data-ttu-id="21501-201">다음과 같은 경고 유형이 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="21501-201">The following alert types are supported:</span></span>

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

<span data-ttu-id="21501-202">이러한 경고는 docs.microsoft.com에서 다음과 같이 보입니다.</span><span class="sxs-lookup"><span data-stu-id="21501-202">These alerts look like this on docs.microsoft.com:</span></span>

<span data-ttu-id="21501-203">참고 블록</span><span class="sxs-lookup"><span data-stu-id="21501-203">Note block</span></span>

> [!NOTE]
> <span data-ttu-id="21501-204">Information the user should notice even if skimming.</span><span class="sxs-lookup"><span data-stu-id="21501-204">Information the user should notice even if skimming.</span></span>

<span data-ttu-id="21501-205">팁 블록</span><span class="sxs-lookup"><span data-stu-id="21501-205">Tip block</span></span>

> [!TIP]
> <span data-ttu-id="21501-206">Optional information to help a user be more successful.</span><span class="sxs-lookup"><span data-stu-id="21501-206">Optional information to help a user be more successful.</span></span>

<span data-ttu-id="21501-207">중요 블록</span><span class="sxs-lookup"><span data-stu-id="21501-207">Important block</span></span>

> [!IMPORTANT]
> <span data-ttu-id="21501-208">Essential information required for user success.</span><span class="sxs-lookup"><span data-stu-id="21501-208">Essential information required for user success.</span></span>

<span data-ttu-id="21501-209">주의 블록</span><span class="sxs-lookup"><span data-stu-id="21501-209">Caution block</span></span>

> [!CAUTION]
> <span data-ttu-id="21501-210">Negative potential consequences of an action.</span><span class="sxs-lookup"><span data-stu-id="21501-210">Negative potential consequences of an action.</span></span>

<span data-ttu-id="21501-211">경고 블록</span><span class="sxs-lookup"><span data-stu-id="21501-211">Warning block</span></span>

> [!WARNING]
> <span data-ttu-id="21501-212">작업의 위험한 특정 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="21501-212">Dangerous certain consequences of an action.</span></span>

### <a name="hyperlinks"></a><span data-ttu-id="21501-213">하이퍼링크</span><span class="sxs-lookup"><span data-stu-id="21501-213">Hyperlinks</span></span>

- <span data-ttu-id="21501-214">하이퍼링크는 Markdown 구문을 사용 해야 합니다 `[friendlyname](url-or-path)` .</span><span class="sxs-lookup"><span data-stu-id="21501-214">Hyperlinks must use Markdown syntax `[friendlyname](url-or-path)`.</span></span> <span data-ttu-id="21501-215">[링크 참조가][linkref] 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="21501-215">[Link references][linkref] are supported.</span></span>
- <span data-ttu-id="21501-216">게시 시스템은 세 가지 유형의 링크를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-216">The publishing system supports three types of links:</span></span>
  - <span data-ttu-id="21501-217">URL 링크</span><span class="sxs-lookup"><span data-stu-id="21501-217">URL links</span></span>
  - <span data-ttu-id="21501-218">파일 링크</span><span class="sxs-lookup"><span data-stu-id="21501-218">File links</span></span>
  - <span data-ttu-id="21501-219">상호 참조 링크</span><span class="sxs-lookup"><span data-stu-id="21501-219">Cross-reference links</span></span>
- <span data-ttu-id="21501-220">Docs.microsoft.com의 다른 문서에 대 한 링크는 사이트 상대 경로 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-220">Links to other articles on docs.microsoft.com must be site-relative paths</span></span>
- <span data-ttu-id="21501-221">외부 웹 사이트에 대 한 모든 Url은 대상 사이트에 대해 유효 하지 않은 경우 HTTPS를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-221">All URLs to external websites should use HTTPS unless that isn't valid for the target site.</span></span>
- <span data-ttu-id="21501-222">링크의 이름은 일반적으로 연결 된 아티클의 제목 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-222">Links must have a friendly name, usually the title of the linked article</span></span>
- <span data-ttu-id="21501-223">아래쪽에 있는 _관련 링크_ 섹션의 모든 항목에는 하이퍼링크가 지정 되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-223">All items in the _Related links_ section at the bottom should be hyperlinked</span></span>
- <span data-ttu-id="21501-224">하이퍼링크의 대괄호 안에는 backticks, 굵게 또는 기타 태그를 사용 하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="21501-224">Don't use backticks, bold, or other markup inside the brackets of a hyperlink.</span></span>
- <span data-ttu-id="21501-225">특정 URI를 문서화 하는 경우에는 완전 한 Url을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21501-225">Bare URLs may be used when you're documenting a specific URI.</span></span> <span data-ttu-id="21501-226">URI는 backticks으로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-226">The URI must be enclosed in backticks.</span></span> <span data-ttu-id="21501-227">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="21501-227">For example:</span></span>

  ```markdown
  By default, if you don't specify this parameter, the DMTF standard resource URI
  `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` is used and the class name is appended to it.
  ```

#### <a name="linking-to-other-content-on-docsmicrosoftcom"></a><span data-ttu-id="21501-228">Docs.microsoft.com의 다른 콘텐츠에 연결</span><span class="sxs-lookup"><span data-stu-id="21501-228">Linking to other content on docs.microsoft.com</span></span>

- <span data-ttu-id="21501-229">Docs.microsoft.com의 다른 아티클에 대 한 **URL 링크** 는 사이트 상대 경로 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-229">**URL links** to other articles on docs.microsoft.com must be site-relative paths.</span></span> <span data-ttu-id="21501-230">상대 링크를 만드는 가장 간단한 방법은 브라우저에서 URL을 복사한 다음 `https://docs.microsoft.com/en-us` markdown에 붙여넣은 값에서 제거 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="21501-230">The simplest way to create a relative link is to copy the URL from your browser then remove `https://docs.microsoft.com/en-us` from the value you paste into markdown.</span></span> <span data-ttu-id="21501-231">Microsoft 속성의 Url에는 로캘을 포함 하지 않습니다 ( `/en-us` url에서 제거).</span><span class="sxs-lookup"><span data-stu-id="21501-231">Don't include locales in URLs on Microsoft properties (remove `/en-us` from URL).</span></span> <span data-ttu-id="21501-232">URL에서 불필요 한 쿼리 매개 변수를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-232">Remove any unnecessary query parameters from the URL.</span></span> <span data-ttu-id="21501-233">제거 해야 하는 예제:</span><span class="sxs-lookup"><span data-stu-id="21501-233">Examples that should be removed:</span></span>

  - <span data-ttu-id="21501-234">`?view=powershell-5.1` -특정 버전의 PowerShell에 연결 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="21501-234">`?view=powershell-5.1` - used to link to a specific version of PowerShell</span></span>
  - <span data-ttu-id="21501-235">`?redirectedfrom=MSDN` -이전 문서에서 새 위치로 리디렉션되는 경우 URL에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="21501-235">`?redirectedfrom=MSDN` - added to the URL when you get redirected from an old article to its new location</span></span>

  <span data-ttu-id="21501-236">특정 버전의 문서에 연결 해야 하는 경우 `&preserve_view=true` 쿼리 문자열에 매개 변수를 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-236">If you need to link to a specific version of a document, then you need to add the `&preserve_view=true` parameter to the query string.</span></span> <span data-ttu-id="21501-237">예: `?view=powershell-5.1&preserve_view=true`</span><span class="sxs-lookup"><span data-stu-id="21501-237">For example: `?view=powershell-5.1&preserve_view=true`</span></span>

- <span data-ttu-id="21501-238">**파일 링크** 를 사용 하 여 참조 문서 간에 연결 하거나 한 개념 문서에서 다른 문서에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-238">A **file link** is used to link from one reference article to another, or from one conceptual article to another.</span></span> <span data-ttu-id="21501-239">특정 버전의 PowerShell에 대 한 참조 문서에 연결 해야 하는 경우 URL 링크를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-239">If you need to link to a reference article for a specific version of PowerShell, then you must use a URL link.</span></span>

  - <span data-ttu-id="21501-240">파일 링크에 상대 파일 경로 (예:)가 포함 되어 있습니다. `../folder/file.md`</span><span class="sxs-lookup"><span data-stu-id="21501-240">File links contain a relative file path (for example: `../folder/file.md`)</span></span>
  - <span data-ttu-id="21501-241">모든 파일 경로에는 슬래시 () 문자를 사용 합니다. `/`</span><span class="sxs-lookup"><span data-stu-id="21501-241">All file paths use forward-slash (`/`) characters</span></span>

- <span data-ttu-id="21501-242">**상호 참조 링크** 는 게시 시스템에서 지 원하는 특별 한 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="21501-242">**Cross-reference links** are a special feature supported by the publishing system.</span></span> <span data-ttu-id="21501-243">개념 문서에서 상호 참조 링크를 사용 하 여 .NET API 또는 cmdlet 참조에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21501-243">You can use cross-reference links in conceptual articles to link to .NET API or cmdlet reference.</span></span>

  <span data-ttu-id="21501-244">.NET API 참조에 대 한 링크는 중앙 참가자 가이드에서 [설명서의 사용 링크](/contribute/how-to-write-links#xref-cross-reference-links) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="21501-244">For links to .NET API reference, see [Use links in documentation](/contribute/how-to-write-links#xref-cross-reference-links) in the central Contributor Guide.</span></span>

  <span data-ttu-id="21501-245">Cmdlet 참조 링크의 형식은 `xref:<module-name>.<cmdlet-name>` 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="21501-245">Links to cmdlet reference have the following format: `xref:<module-name>.<cmdlet-name>`.</span></span> <span data-ttu-id="21501-246">예를 들어,을 (를) `Get-Content` **Microsoft. PowerShell 관리** 모듈의 cmdlet에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-246">For example, to link to the `Get-Content` cmdlet in the **Microsoft.PowerShell.Management** module.</span></span>

  `[Get-Content](xref:Microsoft.PowerShell.Management.Get-Content)`

<span data-ttu-id="21501-247">URL 및 파일 링크 모두에 대해 딥 링크를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21501-247">Deep linking is allowed on both URL and file links.</span></span> <span data-ttu-id="21501-248">대상 경로의 끝에 앵커를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-248">Add the anchor to the end of the target path.</span></span>
<span data-ttu-id="21501-249">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="21501-249">For example:</span></span>

- `[about_Splatting](about_Splatting.md#splatting-with-arrays)`
- `[custom key bindings](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings)`

<span data-ttu-id="21501-250">자세한 내용은 [설명서의 사용 링크](/contribute/how-to-write-links)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="21501-250">For more information, see [Use links in documentation](/contribute/how-to-write-links).</span></span>

## <a name="formatting-command-syntax-elements"></a><span data-ttu-id="21501-251">명령 구문 요소 서식 지정</span><span class="sxs-lookup"><span data-stu-id="21501-251">Formatting command syntax elements</span></span>

- <span data-ttu-id="21501-252">Cmdlet 및 매개 변수에는 항상 전체 이름을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-252">Always use the full name for cmdlets and parameters.</span></span> <span data-ttu-id="21501-253">별칭을 특별히 설명 하지 않는 한 별칭을 사용 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="21501-253">Avoid using aliases unless you're specifically demonstrating the alias.</span></span>

- <span data-ttu-id="21501-254">속성, 매개 변수, 개체, 형식 이름, 클래스 이름, 클래스 메서드는 **굵게 표시** 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-254">Property, parameter, object, type names, class names, class methods should be **bold**.</span></span>
  - <span data-ttu-id="21501-255">속성 및 매개 변수 값은 backtick ()으로 래핑해야 합니다 `` ` `` .</span><span class="sxs-lookup"><span data-stu-id="21501-255">Property and parameter values should be wrapped in backticks (`` ` ``).</span></span>
  - <span data-ttu-id="21501-256">대괄호로 묶은 스타일을 사용 하 여 형식을 참조 하는 경우에는 backticks을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-256">When referring to types using the bracketed style, use backticks.</span></span> <span data-ttu-id="21501-257">예: `[System.Io.FileInfo]`</span><span class="sxs-lookup"><span data-stu-id="21501-257">For example: `[System.Io.FileInfo]`</span></span>

- <span data-ttu-id="21501-258">언어 키워드, cmdlet 이름, 함수, 변수, 네이티브 exe, 파일 경로 및 인라인 구문 예제는 억음 ( `` ` `` ) 문자로 래핑해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-258">Language keywords, cmdlet names, functions, variables, native EXEs, file paths, and inline syntax examples should be wrapped in backtick (`` ` ``) characters.</span></span>

  <span data-ttu-id="21501-259">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="21501-259">For example:</span></span>

  ~~~markdown
  The following code uses `Get-ChildItem` to list the contents of `C:\Windows` and assigns
  the output to the `$files` variable.

  ```powershell
  $files = Get-ChildItem C:\Windows
  ```
  ~~~

  - <span data-ttu-id="21501-260">이름으로 매개 변수를 참조하는 경우 이름은 **굵게** 표시되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-260">When referring to a parameter by name, the name should be **bold**.</span></span> <span data-ttu-id="21501-261">하이픈 접두사로 매개 변수 사용을 나타내는 경우 매개 변수는 억음 악센트로 래핑되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-261">When illustrating the use of a parameter with the hyphen prefix, the parameter should be wrapped in backticks.</span></span> <span data-ttu-id="21501-262">다음은 그 예입니다.</span><span class="sxs-lookup"><span data-stu-id="21501-262">For example:</span></span>

    ```markdown
    The parameter's name is **Name**, but it's typed as `-Name` when used on the command
    line as a parameter.
    ```

  - <span data-ttu-id="21501-263">외부 명령의 사용 예제를 표시하는 경우 예제는 억음 악센트로 래핑되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-263">When showing example usage of an external command, the example should be wrapped in backticks.</span></span>
    <span data-ttu-id="21501-264">항상 네이티브 명령에 파일 확장명을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-264">Always include the file extension in the native command.</span></span> <span data-ttu-id="21501-265">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="21501-265">For example:</span></span>

    ```markdown
    To start the spooler service on a remote computer named DC01, you type `sc.exe \\DC01 start spooler`.
    ```

    <span data-ttu-id="21501-266">파일 확장명을 포함 하면 PowerShell의 명령 우선 순위에 따라 올바른 명령이 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="21501-266">Including the file extension ensures that the correct command is executed according to PowerShell's command precedence.</span></span>

- <span data-ttu-id="21501-267">개념 문서(참조 콘텐츠가 아님)를 작성하는 경우 cmdlet 이름의 첫 번째 인스턴스는 cmdlet 문서에 연결되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-267">When writing a conceptual article (as opposed to reference content), the first instance of a cmdlet name should be hyperlinked to the cmdlet documentation.</span></span> <span data-ttu-id="21501-268">하이퍼링크의 대괄호 안에는 backticks, 굵게 또는 기타 태그를 사용 하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="21501-268">Don't use backticks, bold, or other markup inside the brackets of a hyperlink.</span></span>

  <span data-ttu-id="21501-269">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="21501-269">For example:</span></span>

  ```markdown
  This [Write-Host](/powershell/module/Microsoft.PowerShell.Utility/Write-Host) cmdlet
  uses the **Object** parameter to ...
  ```

  <span data-ttu-id="21501-270">자세한 내용은이 문서의 [하이퍼링크](#hyperlinks) 섹션을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="21501-270">For more information, see [Hyperlinks](#hyperlinks) section of this article.</span></span>

## <a name="markdown-for-code-samples"></a><span data-ttu-id="21501-271">코드 샘플에 대 한 Markdown</span><span class="sxs-lookup"><span data-stu-id="21501-271">Markdown for code samples</span></span>

<span data-ttu-id="21501-272">Markdown은 다음 두 가지 코드 스타일을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-272">Markdown supports two different code styles:</span></span>

- <span data-ttu-id="21501-273">**코드 범위 (인라인)** -단일 억음 ( `` ` `` ) 문자로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="21501-273">**Code spans (inline)** - marked by a single backtick (`` ` ``) character.</span></span> <span data-ttu-id="21501-274">독립 실행형 블록이 아닌 단락 내에서 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="21501-274">Used within a paragraph rather than as a standalone block.</span></span>
- <span data-ttu-id="21501-275">**코드 블록** -삼중-backtick () 문자열로 묶은 여러 줄 블록 `` ``` `` 입니다.</span><span class="sxs-lookup"><span data-stu-id="21501-275">**Code blocks** - a multi-line block surrounded by triple-backtick (`` ``` ``) strings.</span></span> <span data-ttu-id="21501-276">코드 블록에는 backticks 뒤에 언어 레이블이 있을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21501-276">Code blocks may also have a language label following the backticks.</span></span> <span data-ttu-id="21501-277">언어 레이블은 코드 블록의 내용에 대해 구문 강조 표시를 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-277">The language label enables syntax highlighting for the contents of the code block.</span></span>

<span data-ttu-id="21501-278">모든 코드 블록은 코드 펜스에 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-278">All code blocks should be contained in a code fence.</span></span> <span data-ttu-id="21501-279">코드 블록에는 들여쓰기를 사용 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="21501-279">Never use indentation for code blocks.</span></span> <span data-ttu-id="21501-280">Markdown는이 패턴을 허용 하지만 문제가 될 수 있으므로 피해 야 합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-280">Markdown allows this pattern but it can be problematic and should be avoided.</span></span>

<span data-ttu-id="21501-281">코드 블록은 세 개의 코드 줄로, 삼중-백 틱 ( `` ``` `` ) 코드 펜스로 둘러싸여 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21501-281">A code block is one or more lines of code surrounded by a triple-backtick (`` ``` ``) code fence.</span></span>
<span data-ttu-id="21501-282">코드 펜스 마커는 코드 샘플 앞 및 뒤의 고유한 줄에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-282">The code fence markers must be on their own line before and after the code sample.</span></span> <span data-ttu-id="21501-283">코드 블록 시작 부분의 마커에는 선택적 언어 레이블이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21501-283">The marker at the start of the code block may have an optional language label.</span></span> <span data-ttu-id="21501-284">Microsoft의 OPS(Open Publishing System)는 언어 레이블을 사용하여 구문 강조 표시 기능을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-284">Microsoft's Open Publishing System (OPS) uses the language label to support the syntax highlighting feature.</span></span>

<span data-ttu-id="21501-285">지원 되는 언어 태그의 전체 목록은 중앙의 참여자 가이드에서 [친 코드 블록](/contribute/code-in-docs#fenced-code-blocks) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="21501-285">For a full list of supported language tags, see [Fenced code blocks](/contribute/code-in-docs#fenced-code-blocks) in the centralized contributor guide.</span></span>

<span data-ttu-id="21501-286">또한 OPS는 코드 블록의 콘텐츠를 클립보드에 복사하는 **복사** 단추를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-286">OPS also adds a **Copy** button that copies the contents of the code block to the clipboard.</span></span> <span data-ttu-id="21501-287">이렇게 하면 코드를 스크립트에 신속 하 게 붙여넣어 코드 샘플을 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21501-287">This allows you to quickly paste the code into a script to test the code sample.</span></span> <span data-ttu-id="21501-288">그러나 설명서의 모든 예제를 그대로 실행 하기 위한 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="21501-288">However, not all examples in our documentation are intended to be run as-is.</span></span> <span data-ttu-id="21501-289">일부 코드 블록은 PowerShell 개념을 간단히 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="21501-289">Some code blocks are simple illustrations of a PowerShell concept.</span></span>

<span data-ttu-id="21501-290">설명서에 사용 되는 세 가지 유형의 코드 블록이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21501-290">There are three types code blocks used in our documentation:</span></span>

1. <span data-ttu-id="21501-291">구문 블록</span><span class="sxs-lookup"><span data-stu-id="21501-291">Syntax blocks</span></span>
1. <span data-ttu-id="21501-292">설명 예제</span><span class="sxs-lookup"><span data-stu-id="21501-292">Illustrative examples</span></span>
1. <span data-ttu-id="21501-293">실행 가능한 예제</span><span class="sxs-lookup"><span data-stu-id="21501-293">Executable examples</span></span>

### <a name="syntax-code-blocks"></a><span data-ttu-id="21501-294">구문 코드 블록</span><span class="sxs-lookup"><span data-stu-id="21501-294">Syntax code blocks</span></span>

<span data-ttu-id="21501-295">구문 코드 블록은 명령의 구문 구조를 설명 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="21501-295">Syntax code blocks are used to describe the syntactic structure of a command.</span></span> <span data-ttu-id="21501-296">코드 fence에서 언어 태그를 사용 하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="21501-296">Don't use a language tag on the code fence.</span></span> <span data-ttu-id="21501-297">이 예제는 `Get-Command` cmdlet의 가능한 모든 매개 변수를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="21501-297">This example illustrates all the possible parameters of the `Get-Command` cmdlet.</span></span>

~~~markdown
```
Get-Command [-Verb <String[]>] [-Noun <String[]>] [-Module <String[]>]
  [-FullyQualifiedModule <ModuleSpecification[]>] [-TotalCount <Int32>] [-Syntax]
  [-ShowCommandInfo] [[-ArgumentList] <Object[]>] [-All] [-ListImported]
  [-ParameterName <String[]>] [-ParameterType <PSTypeName[]>] [<CommonParameters>]
```
~~~

<span data-ttu-id="21501-298">이 예제는 `for` 문을 일반화된 용어로 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-298">This example describes the `for` statement in generalized terms:</span></span>

~~~markdown
```
for (<init>; <condition>; <repeat>)
{<statement list>}
```
~~~

### <a name="illustrative-examples"></a><span data-ttu-id="21501-299">설명 예제</span><span class="sxs-lookup"><span data-stu-id="21501-299">Illustrative examples</span></span>

<span data-ttu-id="21501-300">설명 예제는 PowerShell 개념을 설명하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="21501-300">Illustrative examples are used to explain a PowerShell concept.</span></span> <span data-ttu-id="21501-301">실행을 위해 클립보드로 복사 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="21501-301">They aren't meant to be copied to the clipboard for execution.</span></span> <span data-ttu-id="21501-302">이러한 기능은 쉽게 입력 하 고 이해 하기 쉬운 간단한 예제에 가장 일반적으로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="21501-302">These are most commonly used for simple examples that are easy to type and easy to understand.</span></span> <span data-ttu-id="21501-303">코드 블록에는 PowerShell 프롬프트와 예제 출력이 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21501-303">The code block can include the PowerShell prompt and example output.</span></span>

<span data-ttu-id="21501-304">PowerShell 비교 연산자를 보여 주는 간단한 예제는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="21501-304">Here's a simple example illustrating the PowerShell comparison operators.</span></span> <span data-ttu-id="21501-305">이 경우 독자가 이 예제를 복사하고 실행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="21501-305">In this case, we don't intend the reader to copy and run this example.</span></span>

~~~markdown
```powershell
PS> 2 -eq 2
True

PS> 2 -eq 3
False

PS> 1,2,3 -eq 2
2

PS> "abc" -eq "abc"
True

PS> "abc" -eq "abc", "def"
False

PS> "abc", "def" -eq "abc"
abc
```
~~~

### <a name="executable-examples"></a><span data-ttu-id="21501-306">실행 가능한 예제</span><span class="sxs-lookup"><span data-stu-id="21501-306">Executable examples</span></span>

<span data-ttu-id="21501-307">복사 및 실행 하기 위한 복잡 한 예제 또는 예제는 다음과 같은 블록 스타일 태그를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-307">Complex examples, or examples that are intended to be copied and executed, should use the following block-style markup:</span></span>

~~~markdown
```powershell
<Your PowerShell code goes here>
```
~~~

<span data-ttu-id="21501-308">PowerShell 명령으로 표시되는 출력은 구문 강조 표시를 방지하기 위해 **출력** 코드 블록으로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-308">The output displayed by PowerShell commands should be enclosed in an **Output** code block to prevent syntax highlighting.</span></span> <span data-ttu-id="21501-309">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="21501-309">For example:</span></span>

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

<span data-ttu-id="21501-310">**출력** 코드 레이블은 구문 강조 표시 시스템에서 지 원하는 공식 "언어"가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="21501-310">The **Output** code label isn't an official "language" supported by the syntax highlighting system.</span></span>
<span data-ttu-id="21501-311">그러나 OPS는 웹 페이지의 코드 상자 프레임에 "출력" 레이블을 추가 하기 때문에이 레이블은 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-311">However, this label is useful because OPS adds the "Output" label to the code box frame on the web page.</span></span> <span data-ttu-id="21501-312">"출력" 코드 상자에는 강조 표시 된 구문이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="21501-312">The "Output" code box has no syntax highlighting.</span></span>

## <a name="coding-style-rules"></a><span data-ttu-id="21501-313">코딩 스타일 규칙</span><span class="sxs-lookup"><span data-stu-id="21501-313">Coding style rules</span></span>

### <a name="avoid-line-continuation-in-code-samples"></a><span data-ttu-id="21501-314">코드 샘플에 줄 연속을 사용하지 않음</span><span class="sxs-lookup"><span data-stu-id="21501-314">Avoid line continuation in code samples</span></span>

<span data-ttu-id="21501-315">PowerShell 코드 예제에서 줄 연속 문자(`` ` ``)를 사용하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="21501-315">Avoid using line continuation characters (`` ` ``) in PowerShell code examples.</span></span> <span data-ttu-id="21501-316">줄 연속 문자는 확인하기 어려우며 줄 끝에 추가 공백이 있는 경우 문제를 초래할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21501-316">These are hard to see and can cause problems if there are extra spaces at the end of the line.</span></span>

- <span data-ttu-id="21501-317">PowerShell 스 플랫을 사용 하 여 여러 매개 변수가 있는 cmdlet의 줄 길이를 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="21501-317">Use PowerShell splatting to reduce line length for cmdlets that have several parameters.</span></span>
- <span data-ttu-id="21501-318">파이프 ( `|` ) 문자, 여는 중괄호 ( `{` ), 괄호 ( `(` ) 및 대괄호 ()와 같은 PowerShell의 자연 스러운 줄 바꿈 기회를 활용 `[` 합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-318">Take advantage of PowerShell's natural line break opportunities, like after pipe (`|`) characters, opening braces (`{`), parentheses (`(`), and brackets (`[`).</span></span>

### <a name="avoid-using-powershell-prompts-in-examples"></a><span data-ttu-id="21501-319">예제에서 PowerShell 프롬프트를 사용하지 않음</span><span class="sxs-lookup"><span data-stu-id="21501-319">Avoid using PowerShell prompts in examples</span></span>

<span data-ttu-id="21501-320">프롬프트 문자열은 사용 하지 않는 것이 좋습니다. 명령줄 사용법을 보여 주는 시나리오로 제한 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-320">Use of the prompt string is discouraged and should be limited to scenarios that are meant to illustrate command-line usage.</span></span> <span data-ttu-id="21501-321">대부분의 예제에서 프롬프트 문자열은 이어야 합니다 `PS>` .</span><span class="sxs-lookup"><span data-stu-id="21501-321">For most of these examples, the prompt string should be `PS>`.</span></span> <span data-ttu-id="21501-322">이 프롬프트는 OS 특정 표시기와 관계가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="21501-322">This prompt is independent of OS-specific indicators.</span></span>

<span data-ttu-id="21501-323">프롬프트를 변경 하거나 표시 되는 경로가 시나리오에 중요 한 경우에는 프롬프트를 변경 하는 명령을 보여 주는 프롬프트가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-323">Prompts are required in examples to illustrate commands that alter the prompt or when the path displayed is significant to the scenario.</span></span> <span data-ttu-id="21501-324">다음 예제에서는 레지스트리 공급자를 사용할 때 프롬프트가 어떻게 변경되는지 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="21501-324">The following example illustrates how the prompt changes when using the Registry provider.</span></span>

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

### <a name="dont-use-aliases-in-examples"></a><span data-ttu-id="21501-325">예제에서 별칭 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="21501-325">Don't use aliases in examples</span></span>

<span data-ttu-id="21501-326">특별히 별칭을 문서화 하지 않는 한 모든 cmdlet 및 매개 변수의 전체 이름을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-326">Use the full name of all cmdlets and parameters unless you're specifically documenting the alias.</span></span>
<span data-ttu-id="21501-327">Cmdlet 및 매개 변수 이름은 적절 한 [파스칼식 대/소문자][] 이름을 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-327">Cmdlet and parameter names must use the proper [Pascal-cased][] names.</span></span>

### <a name="using-parameters-in-examples"></a><span data-ttu-id="21501-328">예제에서 매개 변수 사용</span><span class="sxs-lookup"><span data-stu-id="21501-328">Using parameters in examples</span></span>

<span data-ttu-id="21501-329">위치 매개 변수를 사용하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="21501-329">Avoid using positional parameters.</span></span> <span data-ttu-id="21501-330">일반적으로 매개 변수가 위치 이더라도 예에서는 매개 변수 이름을 항상 포함 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-330">In general, you should always include the parameter name in an example, even if the parameter is positional.</span></span> <span data-ttu-id="21501-331">이렇게 하면 예제에서 혼동할 가능성이 줄어듭니다.</span><span class="sxs-lookup"><span data-stu-id="21501-331">This reduces the chance of confusion in your examples.</span></span>

## <a name="formatting-cmdlet-reference-articles"></a><span data-ttu-id="21501-332">서식 지정 cmdlet 참조 문서</span><span class="sxs-lookup"><span data-stu-id="21501-332">Formatting cmdlet reference articles</span></span>

<span data-ttu-id="21501-333">Cmdlet 참조 문서에는 특정 구조가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21501-333">Cmdlet reference articles have a specific structure.</span></span> <span data-ttu-id="21501-334">이 구조는 [PlatyPS][]에 의해 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="21501-334">This structure is defined by [PlatyPS][].</span></span>
<span data-ttu-id="21501-335">PlatyPS는 Markdown의 PowerShell 모듈에 대 한 cmdlet 도움말을 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-335">PlatyPS generates the cmdlet help for PowerShell modules in Markdown.</span></span> <span data-ttu-id="21501-336">Markdown 파일을 편집한 후 PlatyPS는 `Get-Help` cmdlet에서 사용되는 MAML 도움말 파일을 만드는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="21501-336">After editing the Markdown files, PlatyPS is used create the MAML help files used by the `Get-Help` cmdlet.</span></span>

<span data-ttu-id="21501-337">PlatyPS에는 코드로 작성되는 cmdlet 참조용 하드 코드된 스키마가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21501-337">PlatyPS has a hard-coded schema for cmdlet reference that is written into the code.</span></span> <span data-ttu-id="21501-338">[platyPS.schema.md][] 문서는 이 구조를 설명하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-338">The [platyPS.schema.md][] document attempts to describe this structure.</span></span> <span data-ttu-id="21501-339">스키마 위반으로 인해 기여를 수락하기 전에 수정해야 하는 빌드 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-339">Schema violations cause build errors that must be fixed before we can accept your contribution.</span></span>

- <span data-ttu-id="21501-340">ATX 헤더 구조를 제거 하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="21501-340">Don't remove any of the ATX header structures.</span></span> <span data-ttu-id="21501-341">PlatyPS에는 특정 헤더 세트가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-341">PlatyPS expects a specific set of headers.</span></span>
- <span data-ttu-id="21501-342">**입력 형식** 및 **출력 형식** 헤더에는 형식이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-342">The **Input type** and **Output type** headers must have a type.</span></span> <span data-ttu-id="21501-343">Cmdlet이 입력을 취하지 않거나 값을 반환 하지 않는 경우에는 값을 사용 `None` 합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-343">If the cmdlet doesn't take input or return a value, then use the value `None`.</span></span>
- <span data-ttu-id="21501-344">인라인 코드 범위는 모든 단락에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21501-344">Inline code spans can be used in any paragraph.</span></span>
- <span data-ttu-id="21501-345">친 코드 블록은 **예제** 섹션 에서만 허용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="21501-345">Fenced code blocks are only allowed in the **EXAMPLES** section.</span></span>

<span data-ttu-id="21501-346">PlatyPS 스키마에서 **예제** 는 H2 헤더입니다.</span><span class="sxs-lookup"><span data-stu-id="21501-346">In the PlatyPS schema, **EXAMPLES** is an H2 header.</span></span> <span data-ttu-id="21501-347">각 예제는 H3 헤더입니다.</span><span class="sxs-lookup"><span data-stu-id="21501-347">Each example is an H3 header.</span></span> <span data-ttu-id="21501-348">예제에서 스키마는 코드 블록을 단락으로 구분할 수 없도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-348">Within an example, the schema doesn't allow code blocks to be separated by paragraphs.</span></span> <span data-ttu-id="21501-349">스키마는 다음과 같은 구조를 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-349">The schema allows the following structure:</span></span>

```
### Example X - Title sentence

0 or more paragraphs
1 or more code blocks
0 or more paragraphs.
```

<span data-ttu-id="21501-350">각 예제에 번호를 매기고 간단한 제목을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-350">Number each example and add a brief title.</span></span>

<span data-ttu-id="21501-351">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="21501-351">For example:</span></span>

~~~markdown
### Example 1: Get cmdlets, functions, and aliases

This command gets the PowerShell cmdlets, functions, and aliases that are installed on the
computer.

```powershell
Get-Command
```

### Example 2: Get commands in the current session

```powershell
Get-Command -ListImported
```
~~~

## <a name="formatting-about_-files"></a><span data-ttu-id="21501-352">About_ 파일 서식 지정</span><span class="sxs-lookup"><span data-stu-id="21501-352">Formatting About_ files</span></span>

<span data-ttu-id="21501-353">`About_*` 파일은 Markdown로 작성 되지만 일반 텍스트 파일로 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="21501-353">`About_*` files are written in Markdown but are shipped as plain text files.</span></span> <span data-ttu-id="21501-354">Markdown을 일반 텍스트로 변환 하는 [데 사용 됩니다][] .</span><span class="sxs-lookup"><span data-stu-id="21501-354">We use [Pandoc][] to convert the Markdown to plain text.</span></span> <span data-ttu-id="21501-355">`About_*` 파일은 모든 버전의 PowerShell 및 게시 도구를 사용 하 여 최상의 호환성을 위해 포맷 됩니다.</span><span class="sxs-lookup"><span data-stu-id="21501-355">`About_*` files are formatted for the best compatibility across all versions of PowerShell and with the publishing tools.</span></span>

<span data-ttu-id="21501-356">기본 서식 지정 지침:</span><span class="sxs-lookup"><span data-stu-id="21501-356">Basic formatting guidelines:</span></span>

- <span data-ttu-id="21501-357">표준 줄을 80 자로 제한</span><span class="sxs-lookup"><span data-stu-id="21501-357">Limit normal lines to 80 characters</span></span>
- <span data-ttu-id="21501-358">코드 블록은 76 자로 제한 됩니다.</span><span class="sxs-lookup"><span data-stu-id="21501-358">Code blocks are limited to 76 characters</span></span>
- <span data-ttu-id="21501-359">블록 따옴표 (및 경고)는 78 자로 제한 됩니다.</span><span class="sxs-lookup"><span data-stu-id="21501-359">Blockquotes (and Alerts) are limited 78 characters</span></span>
- <span data-ttu-id="21501-360">이러한 특수 한 메타 문자, 및를 사용 하는 경우 `\` `$` `<` :</span><span class="sxs-lookup"><span data-stu-id="21501-360">When using these special meta-characters `\`,`$`, and `<`:</span></span>
  - <span data-ttu-id="21501-361">헤더 내에서 이러한 문자는 선행 문자를 사용 하 여 이스케이프 `\` 되거나 backtick ()을 사용 하 여 코드 범위에 포함 되어야 합니다. `` ` ``</span><span class="sxs-lookup"><span data-stu-id="21501-361">Within a header, these characters must be escaped using a leading `\` character or enclosed in code spans using backticks (`` ` ``)</span></span>
  - <span data-ttu-id="21501-362">단락 내에서 이러한 문자를 코드 범위에 넣어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-362">Within a paragraph, these characters should be put into code spans.</span></span> <span data-ttu-id="21501-363">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="21501-363">For example:</span></span>

    ~~~markdown
    ### The purpose of the \$foo variable

    The `$foo` variable is used to store ...
    ~~~

- <span data-ttu-id="21501-364">테이블이 76 자 이내에 부합 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="21501-364">Tables need to fit within 76 characters</span></span>
  - <span data-ttu-id="21501-365">여러 줄에서 셀 콘텐츠를 수동으로 래핑</span><span class="sxs-lookup"><span data-stu-id="21501-365">Manually wrap contents of cells across multiple lines</span></span>
  - <span data-ttu-id="21501-366">각 줄에서 여는 및 닫는 `|` 문자 사용</span><span class="sxs-lookup"><span data-stu-id="21501-366">Use opening and closing `|` characters on each line</span></span>
  - <span data-ttu-id="21501-367">다음 예에서는 셀 내에서 여러 줄로 래핑하는 정보가 포함 된 테이블을 올바르게 생성 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="21501-367">The following example illustrates how to properly construct a table that contains information that wraps on multiple lines within a cell.</span></span>

    ~~~markdown
    ```
    |Operator|Description                |Example                          |
    |--------|---------------------------|---------------------------------|
    |`-is`   |Returns TRUE when the input|`(get-date) -is [DateTime]`      |
    |        |is an instance of the      |`True`                           |
    |        |specified .NET type.       |                                 |
    |`-isNot`|Returns TRUE when the input|`(get-date) -isNot [DateTime]`   |
    |        |not an instance of the     |`False`                          |
    |        |specified.NET type.        |                                 |
    |`-as`   |Converts the input to the  |`"5/7/07" -as [DateTime]`        |
    |        |specified .NET type.       |`Monday, May 7, 2007 12:00:00 AM`|
    ```
    ~~~

    > [!NOTE]
    > <span data-ttu-id="21501-368">76 열 제한은 항목에만 적용 됩니다 `About_*` .</span><span class="sxs-lookup"><span data-stu-id="21501-368">The 76-column limitation applies only to `About_*` topics.</span></span> <span data-ttu-id="21501-369">개념 또는 cmdlet 참조 문서에서 넓은 열을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21501-369">You can use wide columns in conceptual or cmdlet reference articles.</span></span>

## <a name="next-steps"></a><span data-ttu-id="21501-370">다음 단계</span><span class="sxs-lookup"><span data-stu-id="21501-370">Next steps</span></span>

[<span data-ttu-id="21501-371">편집 검사 목록</span><span class="sxs-lookup"><span data-stu-id="21501-371">Editorial checklist</span></span>](editorial-checklist.md)

<!-- link references -->
[atx]: https://github.github.com/gfm/#atx-headings
[CommonMark]: https://spec.commonmark.org/
[markdig]: https://github.com/lunet-io/markdig
[Pandoc]: https://pandoc.org
[파스칼식-대/소문자]: https://en.wikipedia.org/wiki/PascalCase
[Pascal-cased]: https://en.wikipedia.org/wiki/PascalCase
[platyPS.schema.md]: https://github.com/PowerShell/platyPS/blob/master/platyPS.schema.md
[PlatyPS]: https://github.com/powershell/platyps
[reflow]: https://marketplace.visualstudio.com/items?itemName=marvhen.reflow-markdown
[linkref]: https://spec.commonmark.org/0.29/#link-reference-definitions
