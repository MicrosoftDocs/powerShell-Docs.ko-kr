---
ms.date: 09/09/2019
keywords: powershell,cmdlet
title: 부록 1 호환성 별칭
ms.openlocfilehash: 2351fdf23711fe1417f7e3fc3cca5b642d5a59fc
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2020
ms.locfileid: "70848172"
---
# <a name="appendix-1---compatibility-aliases"></a><span data-ttu-id="15a25-103">부록 1 - 호환성 별칭</span><span class="sxs-lookup"><span data-stu-id="15a25-103">Appendix 1 - Compatibility Aliases</span></span>

<span data-ttu-id="15a25-104">PowerShell에는 **UNIX** 및 **cmd.exe** 사용자가 친숙한 명령을 사용할 수 있게 하는 몇 가지 별칭이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15a25-104">PowerShell has several aliases that allow **UNIX** and **cmd.exe** users to use familiar commands.</span></span>
<span data-ttu-id="15a25-105">명령, 관련 PowerShell cmdlet 및 PowerShell 별칭은 다음 표에 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15a25-105">The commands and their related PowerShell cmdlet and PowerShell alias are shown in the following table:</span></span>

|<span data-ttu-id="15a25-106">cmd.exe 명령</span><span class="sxs-lookup"><span data-stu-id="15a25-106">cmd.exe command</span></span>|<span data-ttu-id="15a25-107">UNIX 명령</span><span class="sxs-lookup"><span data-stu-id="15a25-107">UNIX command</span></span>|<span data-ttu-id="15a25-108">PowerShell cmdlet</span><span class="sxs-lookup"><span data-stu-id="15a25-108">PowerShell cmdlet</span></span>|<span data-ttu-id="15a25-109">PowerShell 별칭</span><span class="sxs-lookup"><span data-stu-id="15a25-109">PowerShell alias</span></span>|
|---------------|----------------|--------------|------------|
|<span data-ttu-id="15a25-110">**cls**</span><span class="sxs-lookup"><span data-stu-id="15a25-110">**cls**</span></span>|<span data-ttu-id="15a25-111">**clear**</span><span class="sxs-lookup"><span data-stu-id="15a25-111">**clear**</span></span>|<span data-ttu-id="15a25-112">`Clear-Host`(함수)</span><span class="sxs-lookup"><span data-stu-id="15a25-112">`Clear-Host` (function)</span></span>|`cls`|
|<span data-ttu-id="15a25-113">**copy**</span><span class="sxs-lookup"><span data-stu-id="15a25-113">**copy**</span></span>|<span data-ttu-id="15a25-114">**cp**</span><span class="sxs-lookup"><span data-stu-id="15a25-114">**cp**</span></span>|`Copy-Item`|`cpi`|
|<span data-ttu-id="15a25-115">**dir**</span><span class="sxs-lookup"><span data-stu-id="15a25-115">**dir**</span></span>|<span data-ttu-id="15a25-116">**ls**</span><span class="sxs-lookup"><span data-stu-id="15a25-116">**ls**</span></span>|`Get-ChildItem`|`gci`|
|<span data-ttu-id="15a25-117">**type**</span><span class="sxs-lookup"><span data-stu-id="15a25-117">**type**</span></span>|<span data-ttu-id="15a25-118">**cat**</span><span class="sxs-lookup"><span data-stu-id="15a25-118">**cat**</span></span>|`Get-Content`|`gc`|
|<span data-ttu-id="15a25-119">**move**</span><span class="sxs-lookup"><span data-stu-id="15a25-119">**move**</span></span>|<span data-ttu-id="15a25-120">**mv**</span><span class="sxs-lookup"><span data-stu-id="15a25-120">**mv**</span></span>|`Move-Item`|`mi`|
|<span data-ttu-id="15a25-121">**md**</span><span class="sxs-lookup"><span data-stu-id="15a25-121">**md**</span></span>|<span data-ttu-id="15a25-122">**mkdir**</span><span class="sxs-lookup"><span data-stu-id="15a25-122">**mkdir**</span></span>|`New-Item`|`ni`|
|<span data-ttu-id="15a25-123">**pushd**</span><span class="sxs-lookup"><span data-stu-id="15a25-123">**pushd**</span></span>|<span data-ttu-id="15a25-124">**pushd**</span><span class="sxs-lookup"><span data-stu-id="15a25-124">**pushd**</span></span>|`Push-Location`|`pushd`|
|<span data-ttu-id="15a25-125">**popd**</span><span class="sxs-lookup"><span data-stu-id="15a25-125">**popd**</span></span>|<span data-ttu-id="15a25-126">**popd**</span><span class="sxs-lookup"><span data-stu-id="15a25-126">**popd**</span></span>|`Pop-Location`|`popd`|
|<span data-ttu-id="15a25-127">**del**, **erase**, **rd**, **rmdir**</span><span class="sxs-lookup"><span data-stu-id="15a25-127">**del**, **erase**, **rd**, **rmdir**</span></span>|<span data-ttu-id="15a25-128">**rm**</span><span class="sxs-lookup"><span data-stu-id="15a25-128">**rm**</span></span>|`Remove-Item`|`ri`|
|<span data-ttu-id="15a25-129">**ren**</span><span class="sxs-lookup"><span data-stu-id="15a25-129">**ren**</span></span>|<span data-ttu-id="15a25-130">**mv**</span><span class="sxs-lookup"><span data-stu-id="15a25-130">**mv**</span></span>|`Rename-Item`|`rni`|
|<span data-ttu-id="15a25-131">**cd**, **chdir**</span><span class="sxs-lookup"><span data-stu-id="15a25-131">**cd**, **chdir**</span></span>|<span data-ttu-id="15a25-132">**cd**</span><span class="sxs-lookup"><span data-stu-id="15a25-132">**cd**</span></span>|`Set-Location`|`sl`|

<span data-ttu-id="15a25-133">PowerShell 별칭을 찾으려면 [Get Alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="15a25-133">To find the PowerShell aliases, use the [Get-Alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) cmdlet.</span></span> <span data-ttu-id="15a25-134">Cmdlet의 별칭을 표시하려면 **Definition** 매개 변수를 사용하고 cmdlet 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="15a25-134">To display a cmdlet's aliases, use the **Definition** parameter and specify the cmdlet name.</span></span>
<span data-ttu-id="15a25-135">별칭의 cmdlet 이름을 찾으려면 **Name** 매개 변수를 사용하고 별칭을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="15a25-135">Or, to find an alias's cmdlet name, use the **Name** parameter and specify the alias.</span></span>

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
