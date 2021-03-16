---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/clear-host?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-Host
ms.openlocfilehash: 6b7541fba77c4160cf8d5c2dd36a4bad0bf99c5f
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/12/2021
ms.locfileid: "103195175"
---
# <span data-ttu-id="03f80-102">Clear-Host</span><span class="sxs-lookup"><span data-stu-id="03f80-102">Clear-Host</span></span>

## <span data-ttu-id="03f80-103">개요</span><span class="sxs-lookup"><span data-stu-id="03f80-103">SYNOPSIS</span></span>

<span data-ttu-id="03f80-104">호스트 프로그램의 표시를 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="03f80-104">Clears the display in the host program.</span></span>

## <span data-ttu-id="03f80-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="03f80-105">SYNTAX</span></span>

```
Clear-Host [<CommonParameters>]
```

## <span data-ttu-id="03f80-106">설명</span><span class="sxs-lookup"><span data-stu-id="03f80-106">DESCRIPTION</span></span>

<span data-ttu-id="03f80-107">`Clear-Host`함수는 누적 되었을 수 있는 명령 및 출력을 포함 하 여 현재 디스플레이에서 모든 텍스트를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="03f80-107">The `Clear-Host` function removes all text from the current display, including commands and output that might have accumulated.</span></span> <span data-ttu-id="03f80-108">완료되면 명령 프롬프트가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="03f80-108">When complete, it displays the command prompt.</span></span> <span data-ttu-id="03f80-109">함수 이름 또는 해당 별칭인를 사용할 수 있습니다 `cls` .</span><span class="sxs-lookup"><span data-stu-id="03f80-109">You can use the function name or its alias, `cls`.</span></span>

<span data-ttu-id="03f80-110">`Clear-Host` 현재 표시에만 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="03f80-110">`Clear-Host` affects only the current display.</span></span> <span data-ttu-id="03f80-111">세션에서 저장된 결과를 삭제하지 않으며 어떤 항목도 제거하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="03f80-111">It does not delete saved results or remove any items from the session.</span></span> <span data-ttu-id="03f80-112">세션별 항목(예: 변수 및 함수)은 이 함수의 영향을 받지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="03f80-112">Session-specific items, such as variables and functions, are not affected by this function.</span></span>

<span data-ttu-id="03f80-113">`Clear-Host`함수의 동작은 호스트 프로그램에 의해 결정 되므로 `Clear-Host` 호스트 프로그램 마다 다르게 작동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="03f80-113">Because the behavior of the `Clear-Host` function is determined by the host program, `Clear-Host` might work differently in different host programs.</span></span>

## <span data-ttu-id="03f80-114">예제</span><span class="sxs-lookup"><span data-stu-id="03f80-114">EXAMPLES</span></span>

### <span data-ttu-id="03f80-115">예 1</span><span class="sxs-lookup"><span data-stu-id="03f80-115">Example 1</span></span>

```
# Before

PS C:\> Get-Process

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    843      33    14428      22556    99    17.41   1688 CcmExec
     44       6     2196       4964    52     0.23    692 conhost
    646      12     2332       4896    49     1.12    388 csrss
    189      11     2860       7084   114     0.66   2896 csrss
     78      11     1876       4008    42     0.22   4000 csrss
     76       7     1848       5064    54     0.08   1028 dwm
    610      41    23952      44048   208     4.40   2080 explorer
      0       0        0         24     0               0 Idle
    182      32     7692      15980    91     0.23   3056 LogonUI
    186      25     7832      16068    91     0.27   3996 LogonUI
   1272      32    11512      20432    58    25.07    548 lsass
    267      10     3536       6736    34     0.80    556 lsm
    137      17     3520       7472    61     0.05   1220 msdtc
    447      31    70316      84476   201 1,429.67    836 MsMpEng
    265      18     7136      15628   134     2.20   3544 msseces
    248      16     6476       4076    76     0.22   1592 NisSrv
    368      25    61312      65508   614     1.78    848 powershell
    101       8     2304       6624    70     0.64   3648 rdpclip
    258      15     6804      12156    50     2.65    536 services
...

PS C:\> cls
#After

PS C:>
```

<span data-ttu-id="03f80-116">이 명령은의 별칭을 사용 하 여 `cls` `Clear-Host` 현재 표시를 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="03f80-116">This command uses the `cls` alias of `Clear-Host` to clear the current display.</span></span>

## <span data-ttu-id="03f80-117">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="03f80-117">PARAMETERS</span></span>

### <span data-ttu-id="03f80-118">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="03f80-118">CommonParameters</span></span>
<span data-ttu-id="03f80-119">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="03f80-119">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="03f80-120">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="03f80-120">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="03f80-121">입력</span><span class="sxs-lookup"><span data-stu-id="03f80-121">INPUTS</span></span>

### <span data-ttu-id="03f80-122">None</span><span class="sxs-lookup"><span data-stu-id="03f80-122">None</span></span>

<span data-ttu-id="03f80-123">입력을로 파이프 할 수 없습니다 `Clear-Host` .</span><span class="sxs-lookup"><span data-stu-id="03f80-123">You cannot pipe input to `Clear-Host`.</span></span>

## <span data-ttu-id="03f80-124">출력</span><span class="sxs-lookup"><span data-stu-id="03f80-124">OUTPUTS</span></span>

### <span data-ttu-id="03f80-125">None</span><span class="sxs-lookup"><span data-stu-id="03f80-125">None</span></span>

<span data-ttu-id="03f80-126">`Clear-Host` 출력을 생성 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="03f80-126">`Clear-Host` does not generate any output</span></span>

## <span data-ttu-id="03f80-127">참고</span><span class="sxs-lookup"><span data-stu-id="03f80-127">NOTES</span></span>

<span data-ttu-id="03f80-128">`Clear-Host` 는 고급 함수가 아닌 간단한 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="03f80-128">`Clear-Host` is a simple function, not an advanced function.</span></span> <span data-ttu-id="03f80-129">따라서 **디버그** 와 같은 일반 매개 변수를 명령에서 사용할 수 없습니다 `Clear-Host` .</span><span class="sxs-lookup"><span data-stu-id="03f80-129">As such, you cannot use common parameters, such as **Debug**, in a `Clear-Host` command.</span></span>

## <span data-ttu-id="03f80-130">관련 링크</span><span class="sxs-lookup"><span data-stu-id="03f80-130">RELATED LINKS</span></span>

[<span data-ttu-id="03f80-131">Get-Host</span><span class="sxs-lookup"><span data-stu-id="03f80-131">Get-Host</span></span>](../Microsoft.PowerShell.Utility/Get-Host.md)

[<span data-ttu-id="03f80-132">Out-Host</span><span class="sxs-lookup"><span data-stu-id="03f80-132">Out-Host</span></span>](Out-Host.md)

[<span data-ttu-id="03f80-133">Read-Host</span><span class="sxs-lookup"><span data-stu-id="03f80-133">Read-Host</span></span>](../Microsoft.PowerShell.Utility/Read-Host.md)

[<span data-ttu-id="03f80-134">Write-Host</span><span class="sxs-lookup"><span data-stu-id="03f80-134">Write-Host</span></span>](../Microsoft.PowerShell.Utility/Write-Host.md)
