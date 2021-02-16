---
description: PowerShell에서 와일드 카드 문자를 사용 하는 방법을 설명 합니다.
Locale: en-US
ms.date: 02/13/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_wildcards?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Wildcards
ms.openlocfilehash: 189bff70783b9277f242e8c4ca1c227ae68bae62
ms.sourcegitcommit: 9777152e026c47ba8d319593051416054cb62246
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/16/2021
ms.locfileid: "100529960"
---
# <a name="about-wildcards"></a><span data-ttu-id="fa845-103">와일드 카드 정보</span><span class="sxs-lookup"><span data-stu-id="fa845-103">About Wildcards</span></span>

## <a name="short-description"></a><span data-ttu-id="fa845-104">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="fa845-104">SHORT DESCRIPTION</span></span>

<span data-ttu-id="fa845-105">PowerShell에서 와일드 카드 문자를 사용 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa845-105">Describes how to use wildcard characters in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="fa845-106">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="fa845-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="fa845-107">와일드 카드 문자는 하나 이상의 문자를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="fa845-107">Wildcard characters represent one or many characters.</span></span> <span data-ttu-id="fa845-108">이를 사용 하 여 명령에서 단어 패턴을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa845-108">You can use them to create word patterns in commands.</span></span> <span data-ttu-id="fa845-109">와일드 카드 식은 연산자와 함께 사용 `-like` 되거나 와일드 카드를 허용 하는 모든 매개 변수와 함께 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa845-109">Wildcard expressions are used with the `-like` operator or with any parameter that accepts wildcards.</span></span>

<span data-ttu-id="fa845-110">예를 들어 `C:\Techdocs` 파일 이름 확장명을 사용 하 여 디렉터리의 모든 파일을 일치 시키려면 `.ppt` 다음과 같이 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa845-110">For example, to match all the files in the `C:\Techdocs` directory with a `.ppt` file name extension, type:</span></span>

```powershell
Get-ChildItem C:\Techdocs\*.ppt
```

<span data-ttu-id="fa845-111">이 경우 별표 ( `*` ) 와일드 카드 문자는 파일 이름 확장명 앞에 나타나는 모든 문자를 나타냅니다 `.ppt` .</span><span class="sxs-lookup"><span data-stu-id="fa845-111">In this case, the asterisk (`*`) wildcard character represents any characters that appear before the `.ppt` file name extension.</span></span>

<span data-ttu-id="fa845-112">와일드 카드 식은 정규식 보다 간단 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa845-112">Wildcard expressions are simpler than regular expressions.</span></span> <span data-ttu-id="fa845-113">자세한 내용은 [about_Regular_Expressions](./about_Regular_Expressions.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="fa845-113">For more information, see [about_Regular_Expressions](./about_Regular_Expressions.md).</span></span>

<span data-ttu-id="fa845-114">PowerShell은 다음 와일드 카드 문자를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa845-114">PowerShell supports the following wildcard characters:</span></span>

|<span data-ttu-id="fa845-115">와일드카드</span><span class="sxs-lookup"><span data-stu-id="fa845-115">Wildcard</span></span>|<span data-ttu-id="fa845-116">설명</span><span class="sxs-lookup"><span data-stu-id="fa845-116">Description</span></span>               |<span data-ttu-id="fa845-117">예제</span><span class="sxs-lookup"><span data-stu-id="fa845-117">Example</span></span> |<span data-ttu-id="fa845-118">일치</span><span class="sxs-lookup"><span data-stu-id="fa845-118">Match</span></span>        |<span data-ttu-id="fa845-119">일치 하지 않음</span><span class="sxs-lookup"><span data-stu-id="fa845-119">No Match</span></span>|
|--------|--------------------------|--------|-------------|--------|
|\*      |<span data-ttu-id="fa845-120">0 개 이상의 문자를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="fa845-120">Match zero or more characters</span></span> | <span data-ttu-id="fa845-121">은\*</span><span class="sxs-lookup"><span data-stu-id="fa845-121">a\*</span></span>  | <span data-ttu-id="fa845-122">aA, ag, Apple</span><span class="sxs-lookup"><span data-stu-id="fa845-122">aA, ag, Apple</span></span> | <span data-ttu-id="fa845-123">바나나</span><span class="sxs-lookup"><span data-stu-id="fa845-123">banana</span></span> |
|<span data-ttu-id="fa845-124">?</span><span class="sxs-lookup"><span data-stu-id="fa845-124">?</span></span>       |<span data-ttu-id="fa845-125">해당 위치에서 한 문자 일치</span><span class="sxs-lookup"><span data-stu-id="fa845-125">Match one character in that position</span></span> | <span data-ttu-id="fa845-126">? n</span><span class="sxs-lookup"><span data-stu-id="fa845-126">?n</span></span> | <span data-ttu-id="fa845-127">, in, on</span><span class="sxs-lookup"><span data-stu-id="fa845-127">an, in, on</span></span> | <span data-ttu-id="fa845-128">되었음</span><span class="sxs-lookup"><span data-stu-id="fa845-128">ran</span></span> |
|<span data-ttu-id="fa845-129">\[ \]</span><span class="sxs-lookup"><span data-stu-id="fa845-129">\[ \]</span></span>   |<span data-ttu-id="fa845-130">문자 범위 일치</span><span class="sxs-lookup"><span data-stu-id="fa845-130">Match a range of characters</span></span> | <span data-ttu-id="fa845-131">\[a-l \] ook</span><span class="sxs-lookup"><span data-stu-id="fa845-131">\[a-l\]ook</span></span> | <span data-ttu-id="fa845-132">책, 쿡, 모양</span><span class="sxs-lookup"><span data-stu-id="fa845-132">book, cook, look</span></span> | <span data-ttu-id="fa845-133">이나</span><span class="sxs-lookup"><span data-stu-id="fa845-133">took</span></span> |
|<span data-ttu-id="fa845-134">\[ \]</span><span class="sxs-lookup"><span data-stu-id="fa845-134">\[ \]</span></span>   |<span data-ttu-id="fa845-135">특정 문자 일치</span><span class="sxs-lookup"><span data-stu-id="fa845-135">Match specific characters</span></span> | <span data-ttu-id="fa845-136">\[bc \] ook</span><span class="sxs-lookup"><span data-stu-id="fa845-136">\[bc\]ook</span></span> | <span data-ttu-id="fa845-137">책, 쿡</span><span class="sxs-lookup"><span data-stu-id="fa845-137">book, cook</span></span> | <span data-ttu-id="fa845-138">갈고리</span><span class="sxs-lookup"><span data-stu-id="fa845-138">hook</span></span> |

<span data-ttu-id="fa845-139">동일한 단어 패턴에 여러 와일드 카드 문자를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa845-139">You can include multiple wildcard characters in the same word pattern.</span></span> <span data-ttu-id="fa845-140">예를 들어 이름이 **a** 부터 **l** 로 시작 하는 텍스트 파일을 찾으려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa845-140">For example, to find text files with names that begin with the letters **a** through **l**, type:</span></span>

```powershell
Get-ChildItem C:\Techdocs\[a-l]*.txt
```

<span data-ttu-id="fa845-141">많은 cmdlet은 매개 변수 값에 와일드 카드 문자를 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa845-141">Many cmdlets accept wildcard characters in parameter values.</span></span> <span data-ttu-id="fa845-142">각 cmdlet에 대 한 도움말 항목에서는 와일드 카드 문자를 허용 하는 매개 변수에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa845-142">The Help topic for each cmdlet describes which parameters accept wildcard characters.</span></span> <span data-ttu-id="fa845-143">와일드 카드 문자를 허용 하는 매개 변수의 경우에는 대/소문자를 구분 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fa845-143">For parameters that accept wildcard characters, their use is case-insensitive.</span></span>

<span data-ttu-id="fa845-144">명령 및 스크립트 블록에서 와일드 카드 문자를 사용 하 여 속성 값을 나타내는 단어 패턴을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa845-144">You can use wildcard characters in commands and script blocks, such as to create a word pattern that represents property values.</span></span> <span data-ttu-id="fa845-145">예를 들어 다음 명령은 **ServiceType** 속성 값이 **Interactive** 를 포함 하는 서비스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="fa845-145">For example, the following command gets services in which the **ServiceType** property value includes **Interactive**.</span></span>

```powershell
Get-Service | Where-Object {$_.ServiceType -Like "*Interactive*"}
```

<span data-ttu-id="fa845-146">다음 예에서 `If` 문에는 와일드 카드 문자를 사용 하 여 속성 값을 찾는 조건이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa845-146">In the following example, the `If` statement includes a condition that uses wildcard characters to find property values.</span></span> <span data-ttu-id="fa845-147">복원 지점의 **설명** 에 **PowerShell** 이 포함 되어 있는 경우이 명령은 복원 지점의 **CreationTime** 속성 값을 로그 파일에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa845-147">If the restore point's **Description** includes **PowerShell**, the command adds the value of the restore point's **CreationTime** property to a log file.</span></span>

```powershell
$p = Get-ComputerRestorePoint
foreach ($point in $p) {
  if ($point.description -like "*PowerShell*") {
    Add-Content -Path C:\TechDocs\RestoreLog.txt "$($point.CreationTime)"
  }
}
```

## <a name="see-also"></a><span data-ttu-id="fa845-148">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fa845-148">SEE ALSO</span></span>

[<span data-ttu-id="fa845-149">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="fa845-149">about_Language_Keywords</span></span>](about_Language_Keywords.md)

[<span data-ttu-id="fa845-150">about_If</span><span class="sxs-lookup"><span data-stu-id="fa845-150">about_If</span></span>](about_If.md)

[<span data-ttu-id="fa845-151">about_Script_Blocks</span><span class="sxs-lookup"><span data-stu-id="fa845-151">about_Script_Blocks</span></span>](about_Script_Blocks.md)
