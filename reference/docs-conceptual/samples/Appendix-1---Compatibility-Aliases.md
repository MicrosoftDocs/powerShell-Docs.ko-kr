---
ms.date: 08/03/2020
keywords: powershell,cmdlet
title: 부록 1 호환성 별칭
ms.openlocfilehash: e5bd170fea6b6109d2ef4fd58863d6cc8a0e3ae1
ms.sourcegitcommit: d3f78120bdc9096c72aa0dfdbdd91efaf254c738
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87758502"
---
# <a name="appendix-1---compatibility-aliases"></a><span data-ttu-id="52105-103">부록 1 - 호환성 별칭</span><span class="sxs-lookup"><span data-stu-id="52105-103">Appendix 1 - Compatibility Aliases</span></span>

<span data-ttu-id="52105-104">PowerShell에는 **UNIX** 및 **cmd.exe** 사용자가 친숙한 명령을 사용할 수 있게 하는 몇 가지 별칭이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52105-104">PowerShell has several aliases that allow **UNIX** and **cmd.exe** users to use familiar commands.</span></span>
<span data-ttu-id="52105-105">명령, 관련 PowerShell cmdlet 및 PowerShell 별칭은 다음 표에 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52105-105">The commands and their related PowerShell cmdlet and PowerShell alias are shown in the following table:</span></span>

|            <span data-ttu-id="52105-106">cmd.exe 명령</span><span class="sxs-lookup"><span data-stu-id="52105-106">cmd.exe command</span></span>            | <span data-ttu-id="52105-107">UNIX 명령</span><span class="sxs-lookup"><span data-stu-id="52105-107">UNIX command</span></span> | <span data-ttu-id="52105-108">PowerShell cmdlet</span><span class="sxs-lookup"><span data-stu-id="52105-108">PowerShell cmdlet</span></span> | <span data-ttu-id="52105-109">PowerShell 별칭</span><span class="sxs-lookup"><span data-stu-id="52105-109">PowerShell alias</span></span> |
| ------------------------------------- | ------------ | ----------------- | ---------------- |
| <span data-ttu-id="52105-110">**cd**, **chdir**</span><span class="sxs-lookup"><span data-stu-id="52105-110">**cd**, **chdir**</span></span>                     | <span data-ttu-id="52105-111">**cd**</span><span class="sxs-lookup"><span data-stu-id="52105-111">**cd**</span></span>       | `Set-Location`    | `sl`             |
| <span data-ttu-id="52105-112">**cls**</span><span class="sxs-lookup"><span data-stu-id="52105-112">**cls**</span></span>                               | <span data-ttu-id="52105-113">**clear**</span><span class="sxs-lookup"><span data-stu-id="52105-113">**clear**</span></span>    | `Clear-Host`      | `cls`            |
| <span data-ttu-id="52105-114">**copy**</span><span class="sxs-lookup"><span data-stu-id="52105-114">**copy**</span></span>                              | <span data-ttu-id="52105-115">**cp**</span><span class="sxs-lookup"><span data-stu-id="52105-115">**cp**</span></span>       | `Copy-Item`       | `cpi`            |
| <span data-ttu-id="52105-116">**del**, **erase**, **rd**, **rmdir**</span><span class="sxs-lookup"><span data-stu-id="52105-116">**del**, **erase**, **rd**, **rmdir**</span></span> | <span data-ttu-id="52105-117">**rm**</span><span class="sxs-lookup"><span data-stu-id="52105-117">**rm**</span></span>       | `Remove-Item`     | `ri`             |
| <span data-ttu-id="52105-118">**dir**</span><span class="sxs-lookup"><span data-stu-id="52105-118">**dir**</span></span>                               | <span data-ttu-id="52105-119">**ls**</span><span class="sxs-lookup"><span data-stu-id="52105-119">**ls**</span></span>       | `Get-ChildItem`   | `gci`            |
| <span data-ttu-id="52105-120">**echo**</span><span class="sxs-lookup"><span data-stu-id="52105-120">**echo**</span></span>                              | <span data-ttu-id="52105-121">**echo**</span><span class="sxs-lookup"><span data-stu-id="52105-121">**echo**</span></span>     | `Write-Output`    | `write`          |
| <span data-ttu-id="52105-122">**md**</span><span class="sxs-lookup"><span data-stu-id="52105-122">**md**</span></span>                                | <span data-ttu-id="52105-123">**mkdir**</span><span class="sxs-lookup"><span data-stu-id="52105-123">**mkdir**</span></span>    | `New-Item`        | `ni`             |
| <span data-ttu-id="52105-124">**move**</span><span class="sxs-lookup"><span data-stu-id="52105-124">**move**</span></span>                              | <span data-ttu-id="52105-125">**mv**</span><span class="sxs-lookup"><span data-stu-id="52105-125">**mv**</span></span>       | `Move-Item`       | `mi`             |
| <span data-ttu-id="52105-126">**popd**</span><span class="sxs-lookup"><span data-stu-id="52105-126">**popd**</span></span>                              | <span data-ttu-id="52105-127">**popd**</span><span class="sxs-lookup"><span data-stu-id="52105-127">**popd**</span></span>     | `Pop-Location`    | `popd`           |
| <span data-ttu-id="52105-128">**pushd**</span><span class="sxs-lookup"><span data-stu-id="52105-128">**pushd**</span></span>                             | <span data-ttu-id="52105-129">**pushd**</span><span class="sxs-lookup"><span data-stu-id="52105-129">**pushd**</span></span>    | `Push-Location`   | `pushd`          |
| <span data-ttu-id="52105-130">**ren**</span><span class="sxs-lookup"><span data-stu-id="52105-130">**ren**</span></span>                               | <span data-ttu-id="52105-131">**mv**</span><span class="sxs-lookup"><span data-stu-id="52105-131">**mv**</span></span>       | `Rename-Item`     | `rni`            |
| <span data-ttu-id="52105-132">**type**</span><span class="sxs-lookup"><span data-stu-id="52105-132">**type**</span></span>                              | <span data-ttu-id="52105-133">**cat**</span><span class="sxs-lookup"><span data-stu-id="52105-133">**cat**</span></span>      | `Get-Content`     | `gc`             |

<span data-ttu-id="52105-134">PowerShell 별칭을 찾으려면 [Get Alias](xref:Microsoft.PowerShell.Utility.Get-Alias) cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="52105-134">To find the PowerShell aliases, use the [Get-Alias](xref:Microsoft.PowerShell.Utility.Get-Alias) cmdlet.</span></span> <span data-ttu-id="52105-135">Cmdlet의 별칭을 표시하려면 **Definition** 매개 변수를 사용하고 cmdlet 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="52105-135">To display a cmdlet's aliases, use the **Definition** parameter and specify the cmdlet name.</span></span>
<span data-ttu-id="52105-136">별칭의 cmdlet 이름을 찾으려면 **Name** 매개 변수를 사용하고 별칭을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="52105-136">Or, to find an alias's cmdlet name, use the **Name** parameter and specify the alias.</span></span>

```powershell
Get-Alias -Definition Get-ChildItem
```

```Output
CommandType     Name
-----------     ----
Alias           dir -> Get-ChildItem
Alias           gci -> Get-ChildItem
Alias           ls -> Get-ChildItem
```

```powershell
Get-Alias -Name gci
```

```Output
CommandType     Name
-----------     ----
Alias           gci -> Get-ChildItem
```
