---
description: 고급 함수에서 매개 변수 집합을 정의 하 고 사용 하는 방법을 설명 합니다.
title: about_Parameter_Sets
ms.date: 01/05/2021
ms.openlocfilehash: 876f6336dd344412b514ea22d413a97a98c9cd02
ms.sourcegitcommit: eb7ad1850550032880f5529b4e4281514cba1673
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/06/2021
ms.locfileid: "97917827"
---
# <a name="about-parameter-sets"></a><span data-ttu-id="ef512-103">매개 변수 집합 정보</span><span class="sxs-lookup"><span data-stu-id="ef512-103">About parameter sets</span></span>

## <a name="short-description"></a><span data-ttu-id="ef512-104">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="ef512-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="ef512-105">고급 함수에서 매개 변수 집합을 정의 하 고 사용 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef512-105">Describes how to define and use parameter sets in advanced functions.</span></span>

## <a name="long-description"></a><span data-ttu-id="ef512-106">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="ef512-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="ef512-107">PowerShell은 매개 변수 집합을 사용 하 여 다양 한 시나리오에 대해 다른 작업을 수행할 수 있는 단일 함수를 작성할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef512-107">PowerShell uses parameter sets to enable you to write a single function that can do different actions for different scenarios.</span></span> <span data-ttu-id="ef512-108">매개 변수 집합을 사용 하면 사용자에 게 서로 다른 매개 변수를 노출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef512-108">Parameter sets enable you to expose different parameters to the user.</span></span> <span data-ttu-id="ef512-109">사용자가 지정한 매개 변수를 기반으로 다른 정보를 반환 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef512-109">And, to return different information based on the parameters specified by the user.</span></span>

## <a name="parameter-set-requirements"></a><span data-ttu-id="ef512-110">매개 변수 집합 요구 사항</span><span class="sxs-lookup"><span data-stu-id="ef512-110">Parameter set requirements</span></span>

<span data-ttu-id="ef512-111">모든 매개 변수 집합에는 다음 요구 사항이 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef512-111">The following requirements apply to all parameter sets.</span></span>

- <span data-ttu-id="ef512-112">각 매개 변수 집합은 고유한 매개 변수 조합을 포함 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef512-112">Each parameter set must have a unique combination of parameters.</span></span> <span data-ttu-id="ef512-113">가능 하면 고유한 매개 변수 중 하나 이상이 필수 매개 변수 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef512-113">If possible, at least one of the unique parameters should be a mandatory parameter.</span></span>

- <span data-ttu-id="ef512-114">여러 위치 매개 변수를 포함 하는 매개 변수 집합은 각 매개 변수에 대해 고유한 위치를 정의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef512-114">A parameter set that contains multiple positional parameters must define unique positions for each parameter.</span></span> <span data-ttu-id="ef512-115">두 위치 매개 변수는 같은 위치를 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ef512-115">No two positional parameters can specify the same position.</span></span>

- <span data-ttu-id="ef512-116">집합에 있는 하나의 매개 변수만 `ValueFromPipeline` 값을 사용 하 여 키워드를 선언할 수 있습니다 `true` .</span><span class="sxs-lookup"><span data-stu-id="ef512-116">Only one parameter in a set can declare the `ValueFromPipeline` keyword with a value of `true`.</span></span> <span data-ttu-id="ef512-117">여러 매개 변수는 `ValueFromPipelineByPropertyName` 값을 사용 하 여 키워드를 정의할 수 있습니다 `true` .</span><span class="sxs-lookup"><span data-stu-id="ef512-117">Multiple parameters can define the `ValueFromPipelineByPropertyName` keyword with a value of `true`.</span></span>

- <span data-ttu-id="ef512-118">매개 변수에 대 한 매개 변수 집합이 지정 되지 않은 경우 매개 변수는 모든 매개 변수 집합에 속합니다.</span><span class="sxs-lookup"><span data-stu-id="ef512-118">If no parameter set is specified for a parameter, the parameter belongs to all parameter sets.</span></span>

> [!NOTE]
> <span data-ttu-id="ef512-119">매개 변수 집합은 32 개로 제한 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef512-119">There is a limit of 32 parameter sets.</span></span>

## <a name="default-parameter-sets"></a><span data-ttu-id="ef512-120">기본 매개 변수 집합</span><span class="sxs-lookup"><span data-stu-id="ef512-120">Default parameter sets</span></span>

<span data-ttu-id="ef512-121">여러 매개 변수 집합을 정의 하는 경우 `DefaultParameterSetName` **cmdletbinding** 특성의 키워드는 기본 매개 변수 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef512-121">When multiple parameter sets are defined, the `DefaultParameterSetName` keyword of the **CmdletBinding** attribute specifies the default parameter set.</span></span>
<span data-ttu-id="ef512-122">PowerShell은 명령에 제공 된 정보를 기반으로 사용할 매개 변수 집합을 확인할 수 없을 때 기본 매개 변수 집합을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef512-122">PowerShell uses the default parameter set when it can't determine the parameter set to use based on the information provided to the command.</span></span> <span data-ttu-id="ef512-123">**Cmdletbinding** 특성에 대 한 자세한 내용은 [about_functions_cmdletbindingattribute](about_functions_cmdletbindingattribute.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ef512-123">For more information about the **CmdletBinding** attribute, see [about_functions_cmdletbindingattribute](about_functions_cmdletbindingattribute.md).</span></span>

## <a name="declaring-parameter-sets"></a><span data-ttu-id="ef512-124">매개 변수 집합 선언</span><span class="sxs-lookup"><span data-stu-id="ef512-124">Declaring parameter sets</span></span>

<span data-ttu-id="ef512-125">매개 변수 집합을 만들려면 매개 변수 `ParameterSetName` 집합의 모든 매개 변수에 대 **한 매개 변수** 특성의 키워드를 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef512-125">To create a parameter set, you must specify the `ParameterSetName` keyword of the **Parameter** attribute for every parameter in the parameter set.</span></span> <span data-ttu-id="ef512-126">여러 매개 변수 집합에 속하는 매개 변수의 경우 각 매개 변수 집합에 대 한 **매개 변수** 특성을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef512-126">For parameters that belong to multiple parameter sets, add a **Parameter** attribute for each parameter set.</span></span>

<span data-ttu-id="ef512-127">매개 **변수 특성을** 사용 하면 매개 변수 집합 마다 매개 변수를 다르게 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef512-127">The **Parameter** attribute enables you to define the parameter differently for each parameter set.</span></span> <span data-ttu-id="ef512-128">예를 들어 매개 변수를 한 집합에서 필수로 정의 하 고 다른 집합에서는 선택적으로 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef512-128">For example, you can define a parameter as mandatory in one set and optional in another.</span></span> <span data-ttu-id="ef512-129">그러나 각 매개 변수 집합은 하나 이상의 고유 매개 변수를 포함 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef512-129">However, each parameter set must contain at least one unique parameter.</span></span>

<span data-ttu-id="ef512-130">매개 변수 집합 이름이 할당 되지 않은 매개 변수는 모든 매개 변수 집합에 속합니다.</span><span class="sxs-lookup"><span data-stu-id="ef512-130">Parameters that don't have an assigned parameter set name belong to all parameter sets.</span></span>

### <a name="example"></a><span data-ttu-id="ef512-131">예제</span><span class="sxs-lookup"><span data-stu-id="ef512-131">Example</span></span>

<span data-ttu-id="ef512-132">다음 예제 함수는 텍스트 파일의 숫자 줄, 문자 및 단어 수를 계산 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef512-132">The following example function counts the number lines, characters, and words in a text file.</span></span> <span data-ttu-id="ef512-133">매개 변수를 사용 하 여 반환할 값과 측정 하려는 파일을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef512-133">Using parameters, you can specify which values you want returned and which files you want to measure.</span></span> <span data-ttu-id="ef512-134">다음 네 가지 매개 변수 집합이 정의 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef512-134">There are four parameter sets defined:</span></span>

- <span data-ttu-id="ef512-135">경로</span><span class="sxs-lookup"><span data-stu-id="ef512-135">Path</span></span>
- <span data-ttu-id="ef512-136">PathAll</span><span class="sxs-lookup"><span data-stu-id="ef512-136">PathAll</span></span>
- <span data-ttu-id="ef512-137">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="ef512-137">LiteralPath</span></span>
- <span data-ttu-id="ef512-138">LiteralPathAll</span><span class="sxs-lookup"><span data-stu-id="ef512-138">LiteralPathAll</span></span>

```powershell
function Measure-Lines {
    [CmdletBinding(DefaultParameterSetName = 'Path')]
    param (
        [Parameter(Mandatory = $true,
            ParameterSetName = 'Path',
            HelpMessage = 'Enter one or more filenames',
            Position = 0)]
        [Parameter(Mandatory = $true,
            ParameterSetName = 'PathAll',
            Position = 0)]
        [string[]]$Path,

        [Parameter(Mandatory = $true, ParameterSetName = 'LiteralPathAll')]
        [Parameter(Mandatory = $true,
            ParameterSetName = 'LiteralPath',
            HelpMessage = 'Enter a single filename',
            ValueFromPipeline = $true)]
        [string]$LiteralPath,

        [Parameter(ParameterSetName = 'Path')]
        [Parameter(ParameterSetName = 'LiteralPath')]
        [switch]$Lines,

        [Parameter(ParameterSetName = 'Path')]
        [Parameter(ParameterSetName = 'LiteralPath')]
        [switch]$Words,

        [Parameter(ParameterSetName = 'Path')]
        [Parameter(ParameterSetName = 'LiteralPath')]
        [switch]$Characters,

        [Parameter(Mandatory = $true, ParameterSetName = 'PathAll')]
        [Parameter(Mandatory = $true, ParameterSetName = 'LiteralPathAll')]
        [switch]$All,

        [Parameter(ParameterSetName = 'Path')]
        [Parameter(ParameterSetName = 'PathAll')]
        [switch]$Recurse
    )

    begin {
        if ($All) {
            $Lines = $Words = $Characters = $true
        }
        elseif (($Words -eq $false) -and ($Characters -eq $false)) {
            $Lines = $true
        }

        if ($Path) {
            $Files = Get-ChildItem -Path $Path -Recurse:$Recurse
        }
        else {
            $Files = Get-ChildItem -LiteralPath $LiteralPath
        }
    }
    process {
        foreach ($file in $Files) {
            $result = [ordered]@{ }
            $result.Add('File', $file.fullname)

            $content = Get-Content -LiteralPath $file.fullname

            if ($Lines) { $result.Add('Lines', $content.Length) }

            if ($Words) {
                $wc = 0
                foreach ($line in $content) { $wc += $line.split(' ').Length }
                $result.Add('Words', $wc)
            }

            if ($Characters) {
                $cc = 0
                foreach ($line in $content) { $cc += $line.Length }
                $result.Add('Characters', $cc)
            }

            New-Object -TypeName psobject -Property $result
        }
    }
}
```

<span data-ttu-id="ef512-139">각 매개 변수 집합은 고유한 매개 변수 또는 고유한 매개 변수 조합을 포함 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef512-139">Each parameter set must have a unique parameter or a unique combination of parameters.</span></span> <span data-ttu-id="ef512-140">`Path`및 `PathAll` 매개 변수 집합은 매우 유사 하지만 **All** 매개 변수는 `PathAll` 매개 변수 집합에 대해 고유 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef512-140">The `Path` and `PathAll` parameter sets are very similar but the **All** parameter is unique to the `PathAll` parameter set.</span></span> <span data-ttu-id="ef512-141">`LiteralPath`및 매개 변수 집합에도 마찬가지입니다 `LiteralPathAll` .</span><span class="sxs-lookup"><span data-stu-id="ef512-141">The same is true with the `LiteralPath` and `LiteralPathAll` parameter sets.</span></span> <span data-ttu-id="ef512-142">`PathAll`및 매개 변수 집합에 모두 `LiteralPathAll` 매개 변수가 있는 경우에도 **Path** 및 **LiteralPath** 매개 변수는이를 구분 합니다. </span><span class="sxs-lookup"><span data-stu-id="ef512-142">Even though the `PathAll` and `LiteralPathAll` parameter sets both have the **All** parameter, the **Path** and **LiteralPath** parameters differentiate them.</span></span>

<span data-ttu-id="ef512-143">사용은 `Get-Command -Syntax` 각 매개 변수 집합의 구문을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ef512-143">Use `Get-Command -Syntax` shows you the syntax of each parameter set.</span></span> <span data-ttu-id="ef512-144">그러나 매개 변수 집합의 이름은 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ef512-144">However it does not show the name of the parameter set.</span></span> <span data-ttu-id="ef512-145">다음 예에서는 각 매개 변수 집합에 사용할 수 있는 매개 변수를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ef512-145">The following example shows which parameters can be used in each parameter set.</span></span>

```powershell
(Get-Command Measure-Lines).ParameterSets |
  Select-Object -Property @{n='ParameterSetName';e={$_.name}},
    @{n='Parameters';e={$_.ToString()}}
```

```Output
ParameterSetName Parameters
---------------- ----------
Path             [-Path] <string[]> [-Lines] [-Words] [-Characters] [-Recurse] [<CommonParameters>]
PathAll          [-Path] <string[]> -All [-Recurse] [<CommonParameters>]
LiteralPath      -LiteralPath <string> [-Lines] [-Words] [-Characters] [<CommonParameters>]
LiteralPathAll   -LiteralPath <string> -All [<CommonParameters>]
```

### <a name="parameter-sets-in-action"></a><span data-ttu-id="ef512-146">작업 중인 매개 변수 집합</span><span class="sxs-lookup"><span data-stu-id="ef512-146">Parameter sets in action</span></span>

<span data-ttu-id="ef512-147">이 예제에서는 `PathAll` 매개 변수 집합을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef512-147">In this example, we are using the `PathAll` parameter set.</span></span>

```powershell
Measure-Lines test* -All
```

```Output
File                       Lines Words Characters
----                       ----- ----- ----------
C:\temp\test\test.help.txt    31   562       2059
C:\temp\test\test.md          30  1527       3224
C:\temp\test\test.ps1          3     3         79
C:\temp\test\test[1].txt      31   562       2059
```

