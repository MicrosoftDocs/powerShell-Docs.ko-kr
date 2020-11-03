---
description: PowerShell에서 특별 한 의미가 있기 때문에 식별자로 사용할 수 없는 예약 된 단어를 나열 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 07/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_reserved_words?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Reserved_Words
ms.openlocfilehash: edf37ce528c8fd98ce3ca7741a1a6c9e0443173a
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93223930"
---
# <a name="about-reserved-words"></a><span data-ttu-id="7ad71-104">예약 된 단어 정보</span><span class="sxs-lookup"><span data-stu-id="7ad71-104">About Reserved Words</span></span>

## <a name="short-description"></a><span data-ttu-id="7ad71-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="7ad71-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="7ad71-106">PowerShell에서 특별 한 의미가 있기 때문에 식별자로 사용할 수 없는 예약 된 단어를 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ad71-106">Lists the reserved words that cannot be used as identifiers because they have a special meaning in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="7ad71-107">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="7ad71-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="7ad71-108">PowerShell에서 특별 한 의미가 있는 특정 단어가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ad71-108">There are certain words that have special meaning in PowerShell.</span></span> <span data-ttu-id="7ad71-109">이러한 단어가 따옴표 없이 표시 되는 경우 PowerShell은 문자열을 문자열로 처리 하는 대신 특별 한 의미를 적용 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ad71-109">When these words appear without quotation marks, PowerShell attempts to apply their special meaning rather than treating them as character strings.</span></span> <span data-ttu-id="7ad71-110">이러한 단어를 특수 한 의미를 호출 하지 않고 명령 또는 스크립트에서 매개 변수 인수로 사용 하려면 예약어를 따옴표로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="7ad71-110">To use these words as parameter arguments in a command or script without invoking their special meaning, enclose the reserved words in quotation marks.</span></span>

<span data-ttu-id="7ad71-111">다음은 PowerShell에서 예약 된 단어입니다.</span><span class="sxs-lookup"><span data-stu-id="7ad71-111">The following are the reserved words in PowerShell:</span></span>

```
assembly         exit            process
base             filter          public
begin            finally         return
break            for             sequence
catch            foreach         static
class            from (*)        switch
command          function        throw
configuration    hidden          trap
continue         if              try
data             in              type
define (*)       inlinescript    until
do               interface       using
dynamicparam     module          var (*)
else             namespace       while
elseif           parallel        workflow
end              param
enum             private

(*) These keywords are reserved for future use.
```

<span data-ttu-id="7ad71-112">,, 및를 비롯 한 여러 언어 키워드에는 `Foreach` `If` `For` `While` 고유한 도움말 문서가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ad71-112">Several language keywords, including `Foreach`, `If`, `For`, and `While`, have their own help articles.</span></span> <span data-ttu-id="7ad71-113">이를 보려면를 입력 하 `Get-Help about_` 고 키워드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ad71-113">To view them, type `Get-Help about_` and add the keyword.</span></span> <span data-ttu-id="7ad71-114">예를 들어 문에 대 한 정보를 가져오려면 `Foreach` 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ad71-114">For example, to get information about the `Foreach` statement, type:</span></span>

```powershell
Get-Help about_ForEach
```

<span data-ttu-id="7ad71-115">문 또는 문 구문에 대 한 자세한 내용을 보려면 `Filter` `Return` 다음을 입력 하십시오.</span><span class="sxs-lookup"><span data-stu-id="7ad71-115">For information about the `Filter` statement or the `Return` statement syntax, type:</span></span>

```powershell
Get-Help about_Functions
```

<span data-ttu-id="7ad71-116">다른 예약어에 대 한 자세한 내용을 보려면 다음을 입력 하십시오.</span><span class="sxs-lookup"><span data-stu-id="7ad71-116">For information about other reserved words, type:</span></span>

```powershell
Get-Help <Reserved_Word>
```

> [!NOTE]
> <span data-ttu-id="7ad71-117">모든 예약어에 자체 도움말 문서가 있는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="7ad71-117">Not every reserved word has its own help article.</span></span> <span data-ttu-id="7ad71-118">`Get-Help`에서 문서를 반환 하지 않는 경우 다음 명령을 사용 하 여 예약 된 단어에 대해 설명 하는 문서를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ad71-118">If `Get-Help` does not return an article, you can search for articles that talk about the reserved word using the following command:</span></span>
>
> ```powershell
> Get-Help <Reserved_Word> -Category:HelpFile
> ```

## <a name="see-also"></a><span data-ttu-id="7ad71-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7ad71-119">SEE ALSO</span></span>

- [<span data-ttu-id="7ad71-120">about_Command_Syntax</span><span class="sxs-lookup"><span data-stu-id="7ad71-120">about_Command_Syntax</span></span>](about_Command_Syntax.md)
- [<span data-ttu-id="7ad71-121">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="7ad71-121">about_Language_Keywords</span></span>](about_Language_Keywords.md)
- [<span data-ttu-id="7ad71-122">about_Parsing</span><span class="sxs-lookup"><span data-stu-id="7ad71-122">about_Parsing</span></span>](about_Parsing.md)
- [<span data-ttu-id="7ad71-123">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="7ad71-123">about_Quoting_Rules</span></span>](about_Quoting_Rules.md)
- [<span data-ttu-id="7ad71-124">about_Script_Blocks</span><span class="sxs-lookup"><span data-stu-id="7ad71-124">about_Script_Blocks</span></span>](about_Script_Blocks.md)
- [<span data-ttu-id="7ad71-125">about_Special_Characters</span><span class="sxs-lookup"><span data-stu-id="7ad71-125">about_Special_Characters</span></span>](about_Special_Characters.md)
