---
title: 편집 검사 목록
description: PowerShell 설명서를 편집하기 위한 규칙의 요약된 목록입니다.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: b5baf7366239084779d34e23f218e5e6222ed1a3
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81624740"
---
# <a name="editors-checklist"></a><span data-ttu-id="9f8da-103">편집자 검사 목록</span><span class="sxs-lookup"><span data-stu-id="9f8da-103">Editor's checklist</span></span>

<span data-ttu-id="9f8da-104">새 문서를 작성하거나 기존 문서를 업데이트할 때 적용할 규칙의 요약입니다.</span><span class="sxs-lookup"><span data-stu-id="9f8da-104">This is a summary of rules to apply when writing new or updating existing articles.</span></span> <span data-ttu-id="9f8da-105">이러한 규칙에 대한 자세한 설명과 예제는 참가자 가이드의 다른 문서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9f8da-105">See other articles in the Contributor's Guide for detailed explanations and examples of these rules.</span></span>

## <a name="metadata"></a><span data-ttu-id="9f8da-106">메타데이터</span><span class="sxs-lookup"><span data-stu-id="9f8da-106">Metadata</span></span>

- <span data-ttu-id="9f8da-107">`ms.date`: **MM/DD/YYYY** 형식이어야 함</span><span class="sxs-lookup"><span data-stu-id="9f8da-107">`ms.date`: must be in the format **MM/DD/YYYY**</span></span>
  - <span data-ttu-id="9f8da-108">주요 또는 팩트 업데이트가 있는 날짜 변경</span><span class="sxs-lookup"><span data-stu-id="9f8da-108">Change the date when there is a significant or factual update</span></span>
    - <span data-ttu-id="9f8da-109">문서 재구성</span><span class="sxs-lookup"><span data-stu-id="9f8da-109">Reorganizing the article</span></span>
    - <span data-ttu-id="9f8da-110">실제 오류 수정</span><span class="sxs-lookup"><span data-stu-id="9f8da-110">Fixing factual errors</span></span>
    - <span data-ttu-id="9f8da-111">새 정보 추가</span><span class="sxs-lookup"><span data-stu-id="9f8da-111">Adding new information</span></span>
  - <span data-ttu-id="9f8da-112">주요 업데이트가 아닌 경우 날짜를 변경하지 않음</span><span class="sxs-lookup"><span data-stu-id="9f8da-112">Do not change the date if the update is insignificant</span></span>
    - <span data-ttu-id="9f8da-113">오타 또는 서식 수정</span><span class="sxs-lookup"><span data-stu-id="9f8da-113">Fixing typos and formatting</span></span>
- <span data-ttu-id="9f8da-114">`title`: 공백 포함 43~59자의 고유한 문자열</span><span class="sxs-lookup"><span data-stu-id="9f8da-114">`title`: unique string of 43-59 chars including spaces</span></span>
  - <span data-ttu-id="9f8da-115">사이트 식별자를 포함하지 않음(자동 생성됨)</span><span class="sxs-lookup"><span data-stu-id="9f8da-115">Do not include site identifier (it is auto-generated)</span></span>
  - <span data-ttu-id="9f8da-116">문장 대문자 사용 - 첫 번째 단어와 고유명사만 대문자로 시작</span><span class="sxs-lookup"><span data-stu-id="9f8da-116">Use sentence case - capitalize only the first word and any proper nouns</span></span>
- <span data-ttu-id="9f8da-117">`description`: 115~145자(공백 포함) - 이 요약이 검색 결과에 표시됨</span><span class="sxs-lookup"><span data-stu-id="9f8da-117">`description`: 115-145 characters including spaces - this abstract displays in the search result</span></span>

## <a name="formatting"></a><span data-ttu-id="9f8da-118">서식 지정</span><span class="sxs-lookup"><span data-stu-id="9f8da-118">Formatting</span></span>

- <span data-ttu-id="9f8da-119">단락 안에 인라인으로 표시되는 역따옴표 구문 요소</span><span class="sxs-lookup"><span data-stu-id="9f8da-119">Backtick syntax elements that appear, inline, within a paragraph</span></span>
  - <span data-ttu-id="9f8da-120">Cmdlet 이름 `Verb-Noun`</span><span class="sxs-lookup"><span data-stu-id="9f8da-120">Cmdlet names `Verb-Noun`</span></span>
  - <span data-ttu-id="9f8da-121">변수 `$counter`</span><span class="sxs-lookup"><span data-stu-id="9f8da-121">Variable `$counter`</span></span>
  - <span data-ttu-id="9f8da-122">구문 예제 `Verb-Noun -Parameter`</span><span class="sxs-lookup"><span data-stu-id="9f8da-122">Syntactic examples `Verb-Noun -Parameter`</span></span>
  - <span data-ttu-id="9f8da-123">파일 경로 `C:\Program Files\PowerShell`, `/usr/bin/pwsh`</span><span class="sxs-lookup"><span data-stu-id="9f8da-123">File paths `C:\Program Files\PowerShell`, `/usr/bin/pwsh`</span></span>
  - <span data-ttu-id="9f8da-124">문서에서 클릭할 수 없는 URL</span><span class="sxs-lookup"><span data-stu-id="9f8da-124">URLs that are not meant to be clickable in the document</span></span>
  - <span data-ttu-id="9f8da-125">속성 또는 매개 변수 값</span><span class="sxs-lookup"><span data-stu-id="9f8da-125">Property or parameter values</span></span>
- <span data-ttu-id="9f8da-126">속성 이름, 매개 변수 이름, 클래스 이름, 모듈 이름, 엔터티 이름, 개체 또는 형식 이름을 굵게 표시</span><span class="sxs-lookup"><span data-stu-id="9f8da-126">Use bold for property names, parameter names, class names, module names, entity names, object or type names</span></span>
  - <span data-ttu-id="9f8da-127">굵게는 강조 표시가 아니라 의미 체계 태그에 사용</span><span class="sxs-lookup"><span data-stu-id="9f8da-127">Bold is used for semantic markup, not emphasis</span></span>
  - <span data-ttu-id="9f8da-128">굵게 - 별표 `**` 사용</span><span class="sxs-lookup"><span data-stu-id="9f8da-128">Bold - use asterisks `**`</span></span>
- <span data-ttu-id="9f8da-129">기울임꼴 - 밑줄 `_` 사용</span><span class="sxs-lookup"><span data-stu-id="9f8da-129">Italic - use underscore `_`</span></span>
  - <span data-ttu-id="9f8da-130">의미 체계 태그가 아니라 강조 표시에만 사용</span><span class="sxs-lookup"><span data-stu-id="9f8da-130">Only used for emphasis, not for semantic markup</span></span>
- <span data-ttu-id="9f8da-131">100열에서 줄 바꿈(또는 **about_Topics**의 경우 80열)</span><span class="sxs-lookup"><span data-stu-id="9f8da-131">Line breaks at 100 columns (or at 80 for **about_Topics**)</span></span>
- <span data-ttu-id="9f8da-132">하드 탭 없음 - 공백만 사용</span><span class="sxs-lookup"><span data-stu-id="9f8da-132">No hard tabs - use spaces only</span></span>
- <span data-ttu-id="9f8da-133">줄에 후행 공백 없음</span><span class="sxs-lookup"><span data-stu-id="9f8da-133">No trailing spaces on lines</span></span>

### <a name="headers"></a><span data-ttu-id="9f8da-134">headers</span><span class="sxs-lookup"><span data-stu-id="9f8da-134">Headers</span></span>

- <span data-ttu-id="9f8da-135">H1이 첫 번째 - H1은 문서당 1개만</span><span class="sxs-lookup"><span data-stu-id="9f8da-135">H1 is first - only one H1 per article</span></span>
- <span data-ttu-id="9f8da-136">[ATX 헤더](https://github.github.com/gfm/#atx-headings)만 사용</span><span class="sxs-lookup"><span data-stu-id="9f8da-136">Use [ATX Headers](https://github.github.com/gfm/#atx-headings) only</span></span>
- <span data-ttu-id="9f8da-137">모든 헤더에 문장 대문자 사용</span><span class="sxs-lookup"><span data-stu-id="9f8da-137">Use sentence case for all headers</span></span>
- <span data-ttu-id="9f8da-138">수준 건너뛰지 않음 - H2 없이 H3 없음</span><span class="sxs-lookup"><span data-stu-id="9f8da-138">Do not skip levels - no H3 without an H2</span></span>
- <span data-ttu-id="9f8da-139">H3 또는 H4의 최대 깊이</span><span class="sxs-lookup"><span data-stu-id="9f8da-139">Max depth of H3 or H4</span></span>
- <span data-ttu-id="9f8da-140">앞뒤의 빈 줄</span><span class="sxs-lookup"><span data-stu-id="9f8da-140">Blank line before and after</span></span>
- <span data-ttu-id="9f8da-141">PlatyPS는 해당 스키마에 특정 헤더를 적용 - 헤더를 추가 또는 제거하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="9f8da-141">PlatyPS enforces specific headers in its schema - do not add or remove headers</span></span>

### <a name="code-blocks"></a><span data-ttu-id="9f8da-142">코드 블록</span><span class="sxs-lookup"><span data-stu-id="9f8da-142">Code blocks</span></span>

- <span data-ttu-id="9f8da-143">앞뒤의 빈 줄</span><span class="sxs-lookup"><span data-stu-id="9f8da-143">Blank line before and after</span></span>
- <span data-ttu-id="9f8da-144">태그가 지정된 코드 펜스를 사용 - **powershell**, **Output** 또는 기타 적절한 언어 ID</span><span class="sxs-lookup"><span data-stu-id="9f8da-144">Use tagged code fences - **powershell**, **Output**, or other appropriate language ID</span></span>
- <span data-ttu-id="9f8da-145">태그가 없는 펜스 - 구문 블록 또는 기타 셸</span><span class="sxs-lookup"><span data-stu-id="9f8da-145">Untagged fence - syntax blocks or other shells</span></span>
- <span data-ttu-id="9f8da-146">개별 코드 블록에 출력을 배치(독자가 **Copy** 단추를 사용할 필요가 없는 간단한 예제는 제외)</span><span class="sxs-lookup"><span data-stu-id="9f8da-146">Put output in separate code block except for simple examples where you don't intend the for the reader to use the **Copy** button</span></span>
- <span data-ttu-id="9f8da-147">[지원되는 언어](/contribute/code-in-docs#supported-languages) 목록 참조</span><span class="sxs-lookup"><span data-stu-id="9f8da-147">See list of [supported languages](/contribute/code-in-docs#supported-languages)</span></span>

### <a name="lists"></a><span data-ttu-id="9f8da-148">목록</span><span class="sxs-lookup"><span data-stu-id="9f8da-148">Lists</span></span>

- <span data-ttu-id="9f8da-149">올바르게 들여쓰기</span><span class="sxs-lookup"><span data-stu-id="9f8da-149">Indented properly</span></span>
- <span data-ttu-id="9f8da-150">첫 번째 항목 앞과 마지막 항목 뒤의 빈 줄</span><span class="sxs-lookup"><span data-stu-id="9f8da-150">Blank line before first item and after last item</span></span>
- <span data-ttu-id="9f8da-151">글머리 기호 - 별표(`*`)가 아니라 하이픈(`-`)을 사용 - 강조와 혼동하기 쉬움</span><span class="sxs-lookup"><span data-stu-id="9f8da-151">Bullet - use hyphen (`-`) not asterisk (`*`) - too easy to confuse with emphasis</span></span>
- <span data-ttu-id="9f8da-152">번호가 매겨진 목록의 경우 모든 숫자는 "1."입니다.</span><span class="sxs-lookup"><span data-stu-id="9f8da-152">For numbered lists, all numbers are "1."</span></span>

## <a name="terminology"></a><span data-ttu-id="9f8da-153">용어</span><span class="sxs-lookup"><span data-stu-id="9f8da-153">Terminology</span></span>

- <span data-ttu-id="9f8da-154">PowerShell vs. Windows PowerShell vs. PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="9f8da-154">PowerShell vs. Windows PowerShell vs. PowerShell Core</span></span>
- <span data-ttu-id="9f8da-155">[제품 용어](powershell-style-guide.md#product-terminology) 참조</span><span class="sxs-lookup"><span data-stu-id="9f8da-155">See [Product Terminology](powershell-style-guide.md#product-terminology)</span></span>

## <a name="cmdlet-reference-examples"></a><span data-ttu-id="9f8da-156">Cmdlet 참조 예제</span><span class="sxs-lookup"><span data-stu-id="9f8da-156">Cmdlet reference examples</span></span>

- <span data-ttu-id="9f8da-157">Cmdlet 참조에는 하나 이상의 예제가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f8da-157">Must have at least one example in cmdlet reference</span></span>
- <span data-ttu-id="9f8da-158">예제는 사용법을 보여 주는 코드면 충분합니다.</span><span class="sxs-lookup"><span data-stu-id="9f8da-158">Examples should be just enough code to demonstrate the usage</span></span>
- <span data-ttu-id="9f8da-159">PowerShell 구문</span><span class="sxs-lookup"><span data-stu-id="9f8da-159">PowerShell syntax</span></span>
  - <span data-ttu-id="9f8da-160">Cmdlet 및 매개 변수에 별칭이 아니라 전체 이름을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9f8da-160">Use full names of cmdlets and parameters - no aliases</span></span>
  - <span data-ttu-id="9f8da-161">명령줄이 너무 길면 매개 변수에 스플랫을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9f8da-161">Use splatting for parameters when the command line gets too long</span></span>
  - <span data-ttu-id="9f8da-162">줄 연속 역따옴표는 가급적 사용하지 않습니다(필요할 때만 사용).</span><span class="sxs-lookup"><span data-stu-id="9f8da-162">Avoid using line continuation backticks - only use when necessary</span></span>
- <span data-ttu-id="9f8da-163">예제에 필요한 경우를 제외하고 PowerShell 프롬프트(`PS>`)를 제거 또는 단순화합니다.</span><span class="sxs-lookup"><span data-stu-id="9f8da-163">Remove or simplify the PowerShell prompt (`PS>`) except where required for the example</span></span>
- <span data-ttu-id="9f8da-164">Cmdlet 참조 예제는 다음 PlatyPS 스키마를 따라야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f8da-164">Cmdlet reference example must follow the following PlatyPS schema</span></span>

  ~~~Markdown
  ### Example 1 - Descriptive title

  Zero or more short descriptive paragraphs explaining the context of the example followed by one or
  more code blocks. Recommend at least one and no more than two.

  ```powershell
  ... one or more PowerShell code statements ...
  ```

  ```Output
  Example output of the code above.
  ```

  Zero or more optional follow up paragraphs that explain the details of the code and output.
  ~~~

- <span data-ttu-id="9f8da-165">코드 블록 사이에 단락을 넣지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="9f8da-165">Do not put paragraphs between the code blocks.</span></span> <span data-ttu-id="9f8da-166">모든 설명 콘텐츠는 코드 블록 앞 또는 뒤에 와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f8da-166">All descriptive content must come before or after the code blocks.</span></span>

## <a name="linking-to-other-documents"></a><span data-ttu-id="9f8da-167">다른 문서 연결</span><span class="sxs-lookup"><span data-stu-id="9f8da-167">Linking to other documents</span></span>

- <span data-ttu-id="9f8da-168">Docset 외부 또는 cmdlet 참조와 개념 간에 연결</span><span class="sxs-lookup"><span data-stu-id="9f8da-168">Linking outside the docset or between cmdlet reference and conceptual</span></span>
  - <span data-ttu-id="9f8da-169">docs.microsoft.com에 연결할 때 상대 URL을 사용합니다(`https://docs.microsoft.com/en-us`를 제거).</span><span class="sxs-lookup"><span data-stu-id="9f8da-169">Use relative URLs when linking to docs.microsoft.com (remove `https://docs.microsoft.com/en-us`)</span></span>
  - <span data-ttu-id="9f8da-170">Microsoft 속성의 Url에 로캘을 포함하지 않습니다(예:</span><span class="sxs-lookup"><span data-stu-id="9f8da-170">Do not include locales in URLs on Microsoft properties (eg.</span></span> <span data-ttu-id="9f8da-171">URL에서 `/en-us`를 제거).</span><span class="sxs-lookup"><span data-stu-id="9f8da-171">remove `/en-us` from URL)</span></span>
  - <span data-ttu-id="9f8da-172">외부 웹 사이트에 대한 모든 URL은 대상 사이트에 유효하지 않은 경우가 아니라면 HTTPS를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f8da-172">All URLs to external websites should use HTTPS unless that is not valid for the target site</span></span>
- <span data-ttu-id="9f8da-173">Docset 내에서</span><span class="sxs-lookup"><span data-stu-id="9f8da-173">Within docset</span></span>
  - <span data-ttu-id="9f8da-174">파일 경로에 대한 링크(예: `../folder/file.md`)</span><span class="sxs-lookup"><span data-stu-id="9f8da-174">Link to file path (e.g. `../folder/file.md`)</span></span>
  - <span data-ttu-id="9f8da-175">모든 파일 경로에 슬래시(`/`) 문자를 사용</span><span class="sxs-lookup"><span data-stu-id="9f8da-175">All file paths use forward-slash (`/`) characters</span></span>
- <span data-ttu-id="9f8da-176">이미지 링크에는 고유한 대체 텍스트가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f8da-176">Image links should have unique alt text</span></span>
