---
description: PowerShell에서 와일드 카드 문자를 사용 하는 방법을 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 3/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_wildcards?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Wildcards
ms.openlocfilehash: ccd869e46ee682f6dade31ef0c782ff17653ba38
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93221049"
---
# <a name="about-wildcards"></a><span data-ttu-id="dbdcf-104">와일드 카드 정보</span><span class="sxs-lookup"><span data-stu-id="dbdcf-104">About Wildcards</span></span>

## <a name="short-description"></a><span data-ttu-id="dbdcf-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="dbdcf-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="dbdcf-106">PowerShell에서 와일드 카드 문자를 사용 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="dbdcf-106">Describes how to use wildcard characters in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="dbdcf-107">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="dbdcf-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="dbdcf-108">와일드 카드 문자는 하나 이상의 문자를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="dbdcf-108">Wildcard characters represent one or many characters.</span></span> <span data-ttu-id="dbdcf-109">이를 사용 하 여 명령에서 단어 패턴을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dbdcf-109">You can use them to create word patterns in commands.</span></span> <span data-ttu-id="dbdcf-110">예를 들어 파일 이름 확장명을 사용 하 여 디렉터리의 모든 파일을 가져오려면 `C:\Techdocs` `.ppt` 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="dbdcf-110">For example, to get all the files in the `C:\Techdocs` directory with a `.ppt` file name extension, type:</span></span>

```powershell
Get-ChildItem C:\Techdocs\*.ppt
```

<span data-ttu-id="dbdcf-111">이 경우 별표 ( `*` ) 와일드 카드 문자는 파일 이름 확장명 앞에 나타나는 모든 문자를 나타냅니다 `.ppt` .</span><span class="sxs-lookup"><span data-stu-id="dbdcf-111">In this case, the asterisk (`*`) wildcard character represents any characters that appear before the `.ppt` file name extension.</span></span>

<span data-ttu-id="dbdcf-112">PowerShell은 다음 와일드 카드 문자를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="dbdcf-112">PowerShell supports the following wildcard characters:</span></span>

|<span data-ttu-id="dbdcf-113">와일드카드</span><span class="sxs-lookup"><span data-stu-id="dbdcf-113">Wildcard</span></span>|<span data-ttu-id="dbdcf-114">Description</span><span class="sxs-lookup"><span data-stu-id="dbdcf-114">Description</span></span>               |<span data-ttu-id="dbdcf-115">예제</span><span class="sxs-lookup"><span data-stu-id="dbdcf-115">Example</span></span> |<span data-ttu-id="dbdcf-116">일치</span><span class="sxs-lookup"><span data-stu-id="dbdcf-116">Match</span></span>        |<span data-ttu-id="dbdcf-117">일치 하지 않음</span><span class="sxs-lookup"><span data-stu-id="dbdcf-117">No Match</span></span>|
|--------|--------------------------|--------|-------------|--------|
|\*      |<span data-ttu-id="dbdcf-118">0 개 이상의 문자를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="dbdcf-118">Match zero or more characters</span></span> | <span data-ttu-id="dbdcf-119">은\*</span><span class="sxs-lookup"><span data-stu-id="dbdcf-119">a\*</span></span>  | <span data-ttu-id="dbdcf-120">aA, ag, Apple</span><span class="sxs-lookup"><span data-stu-id="dbdcf-120">aA, ag, Apple</span></span> | <span data-ttu-id="dbdcf-121">바나나</span><span class="sxs-lookup"><span data-stu-id="dbdcf-121">banana</span></span> |
|<span data-ttu-id="dbdcf-122">?</span><span class="sxs-lookup"><span data-stu-id="dbdcf-122">?</span></span>       |<span data-ttu-id="dbdcf-123">해당 위치에서 한 문자 일치</span><span class="sxs-lookup"><span data-stu-id="dbdcf-123">Match one character in that position</span></span> | <span data-ttu-id="dbdcf-124">? n</span><span class="sxs-lookup"><span data-stu-id="dbdcf-124">?n</span></span> | <span data-ttu-id="dbdcf-125">, in, on</span><span class="sxs-lookup"><span data-stu-id="dbdcf-125">an, in, on</span></span> | <span data-ttu-id="dbdcf-126">되었음</span><span class="sxs-lookup"><span data-stu-id="dbdcf-126">ran</span></span> |
|<span data-ttu-id="dbdcf-127">\[ \]</span><span class="sxs-lookup"><span data-stu-id="dbdcf-127">\[ \]</span></span>   |<span data-ttu-id="dbdcf-128">문자 범위 일치</span><span class="sxs-lookup"><span data-stu-id="dbdcf-128">Match a range of characters</span></span> | <span data-ttu-id="dbdcf-129">\[a-l \] ook</span><span class="sxs-lookup"><span data-stu-id="dbdcf-129">\[a-l\]ook</span></span> | <span data-ttu-id="dbdcf-130">책, 쿡, 모양</span><span class="sxs-lookup"><span data-stu-id="dbdcf-130">book, cook, look</span></span> | <span data-ttu-id="dbdcf-131">이나</span><span class="sxs-lookup"><span data-stu-id="dbdcf-131">took</span></span> |
|<span data-ttu-id="dbdcf-132">\[ \]</span><span class="sxs-lookup"><span data-stu-id="dbdcf-132">\[ \]</span></span>   |<span data-ttu-id="dbdcf-133">특정 문자 일치</span><span class="sxs-lookup"><span data-stu-id="dbdcf-133">Match specific characters</span></span> | <span data-ttu-id="dbdcf-134">\[bc \] ook</span><span class="sxs-lookup"><span data-stu-id="dbdcf-134">\[bc\]ook</span></span> | <span data-ttu-id="dbdcf-135">책, 쿡</span><span class="sxs-lookup"><span data-stu-id="dbdcf-135">book, cook</span></span> | <span data-ttu-id="dbdcf-136">갈고리</span><span class="sxs-lookup"><span data-stu-id="dbdcf-136">hook</span></span> |

<span data-ttu-id="dbdcf-137">동일한 단어 패턴에 여러 와일드 카드 문자를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dbdcf-137">You can include multiple wildcard characters in the same word pattern.</span></span> <span data-ttu-id="dbdcf-138">예를 들어 이름이 **a** 부터 **l** 로 시작 하는 텍스트 파일을 찾으려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="dbdcf-138">For example, to find text files with names that begin with the letters **a** through **l** , type:</span></span>

```powershell
Get-ChildItem C:\Techdocs\[a-l]*.txt
```

<span data-ttu-id="dbdcf-139">많은 cmdlet은 매개 변수 값에 와일드 카드 문자를 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="dbdcf-139">Many cmdlets accept wildcard characters in parameter values.</span></span> <span data-ttu-id="dbdcf-140">각 cmdlet에 대 한 도움말 항목에서는 와일드 카드 문자를 허용 하는 매개 변수에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="dbdcf-140">The Help topic for each cmdlet describes which parameters accept wildcard characters.</span></span> <span data-ttu-id="dbdcf-141">와일드 카드 문자를 허용 하는 매개 변수의 경우에는 대/소문자를 구분 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dbdcf-141">For parameters that accept wildcard characters, their use is case-insensitive.</span></span>

<span data-ttu-id="dbdcf-142">명령 및 스크립트 블록에서 와일드 카드 문자를 사용 하 여 속성 값을 나타내는 단어 패턴을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dbdcf-142">You can use wildcard characters in commands and script blocks, such as to create a word pattern that represents property values.</span></span> <span data-ttu-id="dbdcf-143">예를 들어 다음 명령은 **ServiceType** 속성 값이 **Interactive** 를 포함 하는 서비스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="dbdcf-143">For example, the following command gets services in which the **ServiceType** property value includes **Interactive**.</span></span>

```powershell
Get-Service | Where-Object {$_.ServiceType -Like "*Interactive*"}
```

<span data-ttu-id="dbdcf-144">다음 예에서 `If` 문에는 와일드 카드 문자를 사용 하 여 속성 값을 찾는 조건이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dbdcf-144">In the following example, the `If` statement includes a condition that uses wildcard characters to find property values.</span></span> <span data-ttu-id="dbdcf-145">복원 지점의 **설명** 에 **PowerShell** 이 포함 되어 있는 경우이 명령은 복원 지점의 **CreationTime** 속성 값을 로그 파일에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="dbdcf-145">If the restore point's **Description** includes **PowerShell** , the command adds the value of the restore point's **CreationTime** property to a log file.</span></span>

```powershell
$p = Get-ComputerRestorePoint
foreach ($point in $p) {
  if ($point.description -like "*PowerShell*") {
    Add-Content -Path C:\TechDocs\RestoreLog.txt "$($point.CreationTime)"
  }
}
```

## <a name="see-also"></a><span data-ttu-id="dbdcf-146">참고 항목</span><span class="sxs-lookup"><span data-stu-id="dbdcf-146">SEE ALSO</span></span>

[<span data-ttu-id="dbdcf-147">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="dbdcf-147">about_Language_Keywords</span></span>](about_Language_Keywords.md)

[<span data-ttu-id="dbdcf-148">about_If</span><span class="sxs-lookup"><span data-stu-id="dbdcf-148">about_If</span></span>](about_If.md)

[<span data-ttu-id="dbdcf-149">about_Script_Blocks</span><span class="sxs-lookup"><span data-stu-id="dbdcf-149">about_Script_Blocks</span></span>](about_Script_Blocks.md)
