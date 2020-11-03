---
description: PowerShell 공급자와 함께 사용 하도록 디자인 된 cmdlet을 나열 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_core_commands?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Core_Commands
ms.openlocfilehash: 5c784518ae30108813d32497f654198e7d10b379
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93220730"
---
# <a name="about-core-commands"></a><span data-ttu-id="b34b5-104">핵심 명령 정보</span><span class="sxs-lookup"><span data-stu-id="b34b5-104">About Core Commands</span></span>

## <a name="short-description"></a><span data-ttu-id="b34b5-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="b34b5-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="b34b5-106">PowerShell 공급자와 함께 사용 하도록 디자인 된 cmdlet을 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="b34b5-106">Lists the cmdlets that are designed for use with PowerShell providers.</span></span>

## <a name="long-description"></a><span data-ttu-id="b34b5-107">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="b34b5-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="b34b5-108">PowerShell에는 PowerShell 공급자가 제공 하는 데이터 저장소의 항목을 관리 하도록 특별히 설계 된 cmdlet 집합이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b34b5-108">PowerShell includes a set of cmdlets that are specifically designed to manage the items in the data stores that are exposed by PowerShell providers.</span></span>
<span data-ttu-id="b34b5-109">이러한 cmdlet을 동일한 방법으로 사용 하 여 공급자가 제공 하는 다양 한 유형의 데이터를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b34b5-109">You can use these cmdlets in the same ways to manage all the different types of data that the providers make available to you.</span></span> <span data-ttu-id="b34b5-110">공급자에 대 한 자세한 내용을 보려면 "get-help about_providers"를 입력 하십시오.</span><span class="sxs-lookup"><span data-stu-id="b34b5-110">For more information about providers, type "get-help about_providers".</span></span>

<span data-ttu-id="b34b5-111">예를 들어 Get-ChildItem cmdlet을 사용 하 여 파일 시스템 디렉터리, 레지스트리 키 아래의 키 또는 사용자가 쓰거나 다운로드 하는 공급자가 노출 하는 항목을 나열할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b34b5-111">For example, you can use the Get-ChildItem cmdlet to list the files in a file system directory, the keys under a registry key, or the items that are exposed by a provider that you write or download.</span></span>

<span data-ttu-id="b34b5-112">다음은 공급자와 함께 사용 하도록 디자인 된 PowerShell cmdlet의 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="b34b5-112">The following is a list of the PowerShell cmdlets that are designed for use with providers:</span></span>

<span data-ttu-id="b34b5-113">ChildItem cmdlet</span><span class="sxs-lookup"><span data-stu-id="b34b5-113">ChildItem cmdlets</span></span>

- <span data-ttu-id="b34b5-114">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="b34b5-114">Get-ChildItem</span></span>

<span data-ttu-id="b34b5-115">콘텐츠 cmdlet</span><span class="sxs-lookup"><span data-stu-id="b34b5-115">Content cmdlets</span></span>

- <span data-ttu-id="b34b5-116">Add-Content</span><span class="sxs-lookup"><span data-stu-id="b34b5-116">Add-Content</span></span>
- <span data-ttu-id="b34b5-117">Clear-Content</span><span class="sxs-lookup"><span data-stu-id="b34b5-117">Clear-Content</span></span>
- <span data-ttu-id="b34b5-118">Get-Content</span><span class="sxs-lookup"><span data-stu-id="b34b5-118">Get-Content</span></span>
- <span data-ttu-id="b34b5-119">Set-Content</span><span class="sxs-lookup"><span data-stu-id="b34b5-119">Set-Content</span></span>

<span data-ttu-id="b34b5-120">항목 cmdlet</span><span class="sxs-lookup"><span data-stu-id="b34b5-120">Item cmdlets</span></span>

- <span data-ttu-id="b34b5-121">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="b34b5-121">Clear-Item</span></span>
- <span data-ttu-id="b34b5-122">Copy-Item</span><span class="sxs-lookup"><span data-stu-id="b34b5-122">Copy-Item</span></span>
- <span data-ttu-id="b34b5-123">Get-Item</span><span class="sxs-lookup"><span data-stu-id="b34b5-123">Get-Item</span></span>
- <span data-ttu-id="b34b5-124">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="b34b5-124">Invoke-Item</span></span>
- <span data-ttu-id="b34b5-125">Move-Item</span><span class="sxs-lookup"><span data-stu-id="b34b5-125">Move-Item</span></span>
- <span data-ttu-id="b34b5-126">New-Item</span><span class="sxs-lookup"><span data-stu-id="b34b5-126">New-Item</span></span>
- <span data-ttu-id="b34b5-127">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="b34b5-127">Remove-Item</span></span>
- <span data-ttu-id="b34b5-128">Rename-Item</span><span class="sxs-lookup"><span data-stu-id="b34b5-128">Rename-Item</span></span>
- <span data-ttu-id="b34b5-129">Set-Item</span><span class="sxs-lookup"><span data-stu-id="b34b5-129">Set-Item</span></span>

<span data-ttu-id="b34b5-130">Get-itemproperty cmdlet</span><span class="sxs-lookup"><span data-stu-id="b34b5-130">ItemProperty cmdlets</span></span>

- <span data-ttu-id="b34b5-131">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="b34b5-131">Clear-ItemProperty</span></span>
- <span data-ttu-id="b34b5-132">Copy-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="b34b5-132">Copy-ItemProperty</span></span>
- <span data-ttu-id="b34b5-133">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="b34b5-133">Get-ItemProperty</span></span>
- <span data-ttu-id="b34b5-134">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="b34b5-134">Move-ItemProperty</span></span>
- <span data-ttu-id="b34b5-135">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="b34b5-135">New-ItemProperty</span></span>
- <span data-ttu-id="b34b5-136">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="b34b5-136">Remove-ItemProperty</span></span>
- <span data-ttu-id="b34b5-137">Rename-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="b34b5-137">Rename-ItemProperty</span></span>
- <span data-ttu-id="b34b5-138">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="b34b5-138">Set-ItemProperty</span></span>

<span data-ttu-id="b34b5-139">위치 cmdlet</span><span class="sxs-lookup"><span data-stu-id="b34b5-139">Location cmdlets</span></span>

- <span data-ttu-id="b34b5-140">Get-Location</span><span class="sxs-lookup"><span data-stu-id="b34b5-140">Get-Location</span></span>
- <span data-ttu-id="b34b5-141">Pop-Location</span><span class="sxs-lookup"><span data-stu-id="b34b5-141">Pop-Location</span></span>
- <span data-ttu-id="b34b5-142">Push-Location</span><span class="sxs-lookup"><span data-stu-id="b34b5-142">Push-Location</span></span>
- <span data-ttu-id="b34b5-143">Set-Location</span><span class="sxs-lookup"><span data-stu-id="b34b5-143">Set-Location</span></span>

<span data-ttu-id="b34b5-144">경로 cmdlet</span><span class="sxs-lookup"><span data-stu-id="b34b5-144">Path cmdlets</span></span>

- <span data-ttu-id="b34b5-145">Join-Path</span><span class="sxs-lookup"><span data-stu-id="b34b5-145">Join-Path</span></span>
- <span data-ttu-id="b34b5-146">Convert-Path</span><span class="sxs-lookup"><span data-stu-id="b34b5-146">Convert-Path</span></span>
- <span data-ttu-id="b34b5-147">Split-Path</span><span class="sxs-lookup"><span data-stu-id="b34b5-147">Split-Path</span></span>
- <span data-ttu-id="b34b5-148">Resolve-Path</span><span class="sxs-lookup"><span data-stu-id="b34b5-148">Resolve-Path</span></span>
- <span data-ttu-id="b34b5-149">Test-Path</span><span class="sxs-lookup"><span data-stu-id="b34b5-149">Test-Path</span></span>

<span data-ttu-id="b34b5-150">PSDrive cmdlet</span><span class="sxs-lookup"><span data-stu-id="b34b5-150">PSDrive cmdlets</span></span>

- <span data-ttu-id="b34b5-151">Get-PSDrive</span><span class="sxs-lookup"><span data-stu-id="b34b5-151">Get-PSDrive</span></span>
- <span data-ttu-id="b34b5-152">New-PSDrive</span><span class="sxs-lookup"><span data-stu-id="b34b5-152">New-PSDrive</span></span>
- <span data-ttu-id="b34b5-153">Remove-PSDrive</span><span class="sxs-lookup"><span data-stu-id="b34b5-153">Remove-PSDrive</span></span>

<span data-ttu-id="b34b5-154">PSProvider cmdlet</span><span class="sxs-lookup"><span data-stu-id="b34b5-154">PSProvider cmdlets</span></span>

- <span data-ttu-id="b34b5-155">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="b34b5-155">Get-PSProvider</span></span>

<span data-ttu-id="b34b5-156">Cmdlet에 대 한 자세한 내용을 보려면를 입력 하십시오 `get-help <cmdlet-name>` .</span><span class="sxs-lookup"><span data-stu-id="b34b5-156">For more information about a cmdlet, type `get-help <cmdlet-name>`.</span></span>

## <a name="see-also"></a><span data-ttu-id="b34b5-157">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b34b5-157">SEE ALSO</span></span>

[<span data-ttu-id="b34b5-158">about_Providers</span><span class="sxs-lookup"><span data-stu-id="b34b5-158">about_Providers</span></span>](about_Providers.md)
