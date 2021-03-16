---
description: PowerShell에서 특별 한 의미가 있기 때문에 식별자로 사용할 수 없는 예약 된 단어를 나열 합니다.
Locale: en-US
ms.date: 07/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_reserved_words?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Reserved_Words
ms.openlocfilehash: 95911e328a50c173235f47a7610393124781555d
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99602251"
---
# <a name="about-reserved-words"></a><span data-ttu-id="d1e23-103">예약 된 단어 정보</span><span class="sxs-lookup"><span data-stu-id="d1e23-103">About Reserved Words</span></span>

## <a name="short-description"></a><span data-ttu-id="d1e23-104">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="d1e23-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="d1e23-105">PowerShell에서 특별 한 의미가 있기 때문에 식별자로 사용할 수 없는 예약 된 단어를 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1e23-105">Lists the reserved words that cannot be used as identifiers because they have a special meaning in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="d1e23-106">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="d1e23-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="d1e23-107">PowerShell에서 특별 한 의미가 있는 특정 단어가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1e23-107">There are certain words that have special meaning in PowerShell.</span></span> <span data-ttu-id="d1e23-108">이러한 단어가 따옴표 없이 표시 되는 경우 PowerShell은 문자열을 문자열로 처리 하는 대신 특별 한 의미를 적용 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1e23-108">When these words appear without quotation marks, PowerShell attempts to apply their special meaning rather than treating them as character strings.</span></span> <span data-ttu-id="d1e23-109">이러한 단어를 특수 한 의미를 호출 하지 않고 명령 또는 스크립트에서 매개 변수 인수로 사용 하려면 예약어를 따옴표로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="d1e23-109">To use these words as parameter arguments in a command or script without invoking their special meaning, enclose the reserved words in quotation marks.</span></span>

<span data-ttu-id="d1e23-110">다음은 PowerShell에서 예약 된 단어입니다.</span><span class="sxs-lookup"><span data-stu-id="d1e23-110">The following are the reserved words in PowerShell:</span></span>

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

<span data-ttu-id="d1e23-111">,, 및를 비롯 한 여러 언어 키워드에는 `Foreach` `If` `For` `While` 고유한 도움말 문서가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1e23-111">Several language keywords, including `Foreach`, `If`, `For`, and `While`, have their own help articles.</span></span> <span data-ttu-id="d1e23-112">이를 보려면를 입력 하 `Get-Help about_` 고 키워드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1e23-112">To view them, type `Get-Help about_` and add the keyword.</span></span> <span data-ttu-id="d1e23-113">예를 들어 문에 대 한 정보를 가져오려면 `Foreach` 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1e23-113">For example, to get information about the `Foreach` statement, type:</span></span>

```powershell
Get-Help about_ForEach
```

<span data-ttu-id="d1e23-114">문 또는 문 구문에 대 한 자세한 내용을 보려면 `Filter` `Return` 다음을 입력 하십시오.</span><span class="sxs-lookup"><span data-stu-id="d1e23-114">For information about the `Filter` statement or the `Return` statement syntax, type:</span></span>

```powershell
Get-Help about_Functions
```

<span data-ttu-id="d1e23-115">다른 예약어에 대 한 자세한 내용을 보려면 다음을 입력 하십시오.</span><span class="sxs-lookup"><span data-stu-id="d1e23-115">For information about other reserved words, type:</span></span>

```powershell
Get-Help <Reserved_Word>
```

> [!NOTE]
> <span data-ttu-id="d1e23-116">모든 예약어에 자체 도움말 문서가 있는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="d1e23-116">Not every reserved word has its own help article.</span></span> <span data-ttu-id="d1e23-117">`Get-Help`에서 문서를 반환 하지 않는 경우 다음 명령을 사용 하 여 예약 된 단어에 대해 설명 하는 문서를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1e23-117">If `Get-Help` does not return an article, you can search for articles that talk about the reserved word using the following command:</span></span>
>
> ```powershell
> Get-Help <Reserved_Word> -Category:HelpFile
> ```

## <a name="see-also"></a><span data-ttu-id="d1e23-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d1e23-118">SEE ALSO</span></span>

- [<span data-ttu-id="d1e23-119">about_Command_Syntax</span><span class="sxs-lookup"><span data-stu-id="d1e23-119">about_Command_Syntax</span></span>](about_Command_Syntax.md)
- [<span data-ttu-id="d1e23-120">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="d1e23-120">about_Language_Keywords</span></span>](about_Language_Keywords.md)
- [<span data-ttu-id="d1e23-121">about_Parsing</span><span class="sxs-lookup"><span data-stu-id="d1e23-121">about_Parsing</span></span>](about_Parsing.md)
- [<span data-ttu-id="d1e23-122">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="d1e23-122">about_Quoting_Rules</span></span>](about_Quoting_Rules.md)
- [<span data-ttu-id="d1e23-123">about_Script_Blocks</span><span class="sxs-lookup"><span data-stu-id="d1e23-123">about_Script_Blocks</span></span>](about_Script_Blocks.md)
- [<span data-ttu-id="d1e23-124">about_Special_Characters</span><span class="sxs-lookup"><span data-stu-id="d1e23-124">about_Special_Characters</span></span>](about_Special_Characters.md)