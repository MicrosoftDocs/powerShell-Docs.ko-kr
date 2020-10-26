---
ms.date: 08/03/2020
keywords: powershell,cmdlet
title: 부록 1 호환성 별칭
description: PowerShell에는 UNIX 및 cmd.exe 사용자가 친숙한 명령을 사용할 수 있게 하는 몇 가지 별칭이 있습니다.
ms.openlocfilehash: 8cbbd5a358de9018fcb5c840e711cd76f7a9a353
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500745"
---
# <a name="appendix-1---compatibility-aliases"></a><span data-ttu-id="842c4-104">부록 1 - 호환성 별칭</span><span class="sxs-lookup"><span data-stu-id="842c4-104">Appendix 1 - Compatibility Aliases</span></span>

<span data-ttu-id="842c4-105">PowerShell에는 **UNIX** 및 **cmd.exe** 사용자가 친숙한 명령을 사용할 수 있게 하는 몇 가지 별칭이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="842c4-105">PowerShell has several aliases that allow **UNIX** and **cmd.exe** users to use familiar commands.</span></span>
<span data-ttu-id="842c4-106">명령, 관련 PowerShell cmdlet 및 PowerShell 별칭은 다음 표에 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="842c4-106">The commands and their related PowerShell cmdlet and PowerShell alias are shown in the following table:</span></span>

|            <span data-ttu-id="842c4-107">cmd.exe 명령</span><span class="sxs-lookup"><span data-stu-id="842c4-107">cmd.exe command</span></span>            | <span data-ttu-id="842c4-108">UNIX 명령</span><span class="sxs-lookup"><span data-stu-id="842c4-108">UNIX command</span></span> | <span data-ttu-id="842c4-109">PowerShell cmdlet</span><span class="sxs-lookup"><span data-stu-id="842c4-109">PowerShell cmdlet</span></span> | <span data-ttu-id="842c4-110">PowerShell 별칭</span><span class="sxs-lookup"><span data-stu-id="842c4-110">PowerShell alias</span></span> |
| ------------------------------------- | ------------ | ----------------- | ---------------- |
| <span data-ttu-id="842c4-111">**cd** , **chdir**</span><span class="sxs-lookup"><span data-stu-id="842c4-111">**cd** , **chdir**</span></span>                     | <span data-ttu-id="842c4-112">**cd**</span><span class="sxs-lookup"><span data-stu-id="842c4-112">**cd**</span></span>       | `Set-Location`    | `sl`             |
| <span data-ttu-id="842c4-113">**cls**</span><span class="sxs-lookup"><span data-stu-id="842c4-113">**cls**</span></span>                               | <span data-ttu-id="842c4-114">**clear**</span><span class="sxs-lookup"><span data-stu-id="842c4-114">**clear**</span></span>    | `Clear-Host`      | `cls`            |
| <span data-ttu-id="842c4-115">**copy**</span><span class="sxs-lookup"><span data-stu-id="842c4-115">**copy**</span></span>                              | <span data-ttu-id="842c4-116">**cp**</span><span class="sxs-lookup"><span data-stu-id="842c4-116">**cp**</span></span>       | `Copy-Item`       | `cpi`            |
| <span data-ttu-id="842c4-117">**del** , **erase** , **rd** , **rmdir**</span><span class="sxs-lookup"><span data-stu-id="842c4-117">**del** , **erase** , **rd** , **rmdir**</span></span> | <span data-ttu-id="842c4-118">**rm**</span><span class="sxs-lookup"><span data-stu-id="842c4-118">**rm**</span></span>       | `Remove-Item`     | `ri`             |
| <span data-ttu-id="842c4-119">**dir**</span><span class="sxs-lookup"><span data-stu-id="842c4-119">**dir**</span></span>                               | <span data-ttu-id="842c4-120">**ls**</span><span class="sxs-lookup"><span data-stu-id="842c4-120">**ls**</span></span>       | `Get-ChildItem`   | `gci`            |
| <span data-ttu-id="842c4-121">**echo**</span><span class="sxs-lookup"><span data-stu-id="842c4-121">**echo**</span></span>                              | <span data-ttu-id="842c4-122">**echo**</span><span class="sxs-lookup"><span data-stu-id="842c4-122">**echo**</span></span>     | `Write-Output`    | `write`          |
| <span data-ttu-id="842c4-123">**md**</span><span class="sxs-lookup"><span data-stu-id="842c4-123">**md**</span></span>                                | <span data-ttu-id="842c4-124">**mkdir**</span><span class="sxs-lookup"><span data-stu-id="842c4-124">**mkdir**</span></span>    | `New-Item`        | `ni`             |
| <span data-ttu-id="842c4-125">**move**</span><span class="sxs-lookup"><span data-stu-id="842c4-125">**move**</span></span>                              | <span data-ttu-id="842c4-126">**mv**</span><span class="sxs-lookup"><span data-stu-id="842c4-126">**mv**</span></span>       | `Move-Item`       | `mi`             |
| <span data-ttu-id="842c4-127">**popd**</span><span class="sxs-lookup"><span data-stu-id="842c4-127">**popd**</span></span>                              | <span data-ttu-id="842c4-128">**popd**</span><span class="sxs-lookup"><span data-stu-id="842c4-128">**popd**</span></span>     | `Pop-Location`    | `popd`           |
| <span data-ttu-id="842c4-129">**pushd**</span><span class="sxs-lookup"><span data-stu-id="842c4-129">**pushd**</span></span>                             | <span data-ttu-id="842c4-130">**pushd**</span><span class="sxs-lookup"><span data-stu-id="842c4-130">**pushd**</span></span>    | `Push-Location`   | `pushd`          |
| <span data-ttu-id="842c4-131">**ren**</span><span class="sxs-lookup"><span data-stu-id="842c4-131">**ren**</span></span>                               | <span data-ttu-id="842c4-132">**mv**</span><span class="sxs-lookup"><span data-stu-id="842c4-132">**mv**</span></span>       | `Rename-Item`     | `rni`            |
| <span data-ttu-id="842c4-133">**type**</span><span class="sxs-lookup"><span data-stu-id="842c4-133">**type**</span></span>                              | <span data-ttu-id="842c4-134">**cat**</span><span class="sxs-lookup"><span data-stu-id="842c4-134">**cat**</span></span>      | `Get-Content`     | `gc`             |

<span data-ttu-id="842c4-135">PowerShell 별칭을 찾으려면 [Get Alias](xref:Microsoft.PowerShell.Utility.Get-Alias) cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="842c4-135">To find the PowerShell aliases, use the [Get-Alias](xref:Microsoft.PowerShell.Utility.Get-Alias) cmdlet.</span></span> <span data-ttu-id="842c4-136">Cmdlet의 별칭을 표시하려면 **Definition** 매개 변수를 사용하고 cmdlet 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="842c4-136">To display a cmdlet's aliases, use the **Definition** parameter and specify the cmdlet name.</span></span>
<span data-ttu-id="842c4-137">별칭의 cmdlet 이름을 찾으려면 **Name** 매개 변수를 사용하고 별칭을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="842c4-137">Or, to find an alias's cmdlet name, use the **Name** parameter and specify the alias.</span></span>

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
