---
description: PowerShell 공급자와 함께 사용 하도록 디자인 된 cmdlet을 나열 합니다.
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_core_commands?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Core_Commands
ms.openlocfilehash: 1f023c5a66265f561ef6644afdc45cd0149f35b7
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99602070"
---
# <a name="about-core-commands"></a><span data-ttu-id="6639d-103">핵심 명령 정보</span><span class="sxs-lookup"><span data-stu-id="6639d-103">About Core Commands</span></span>

## <a name="short-description"></a><span data-ttu-id="6639d-104">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="6639d-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="6639d-105">PowerShell 공급자와 함께 사용 하도록 디자인 된 cmdlet을 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="6639d-105">Lists the cmdlets that are designed for use with PowerShell providers.</span></span>

## <a name="long-description"></a><span data-ttu-id="6639d-106">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="6639d-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="6639d-107">PowerShell에는 PowerShell 공급자가 제공 하는 데이터 저장소의 항목을 관리 하도록 특별히 설계 된 cmdlet 집합이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6639d-107">PowerShell includes a set of cmdlets that are specifically designed to manage the items in the data stores that are exposed by PowerShell providers.</span></span>
<span data-ttu-id="6639d-108">이러한 cmdlet을 동일한 방법으로 사용 하 여 공급자가 제공 하는 다양 한 유형의 데이터를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6639d-108">You can use these cmdlets in the same ways to manage all the different types of data that the providers make available to you.</span></span> <span data-ttu-id="6639d-109">공급자에 대 한 자세한 내용을 보려면 "get-help about_providers"를 입력 하십시오.</span><span class="sxs-lookup"><span data-stu-id="6639d-109">For more information about providers, type "get-help about_providers".</span></span>

<span data-ttu-id="6639d-110">예를 들어 Get-ChildItem cmdlet을 사용 하 여 파일 시스템 디렉터리, 레지스트리 키 아래의 키 또는 사용자가 쓰거나 다운로드 하는 공급자가 노출 하는 항목을 나열할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6639d-110">For example, you can use the Get-ChildItem cmdlet to list the files in a file system directory, the keys under a registry key, or the items that are exposed by a provider that you write or download.</span></span>

<span data-ttu-id="6639d-111">다음은 공급자와 함께 사용 하도록 디자인 된 PowerShell cmdlet의 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="6639d-111">The following is a list of the PowerShell cmdlets that are designed for use with providers:</span></span>

<span data-ttu-id="6639d-112">ChildItem cmdlet</span><span class="sxs-lookup"><span data-stu-id="6639d-112">ChildItem cmdlets</span></span>

- <span data-ttu-id="6639d-113">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="6639d-113">Get-ChildItem</span></span>

<span data-ttu-id="6639d-114">콘텐츠 cmdlet</span><span class="sxs-lookup"><span data-stu-id="6639d-114">Content cmdlets</span></span>

- <span data-ttu-id="6639d-115">Add-Content</span><span class="sxs-lookup"><span data-stu-id="6639d-115">Add-Content</span></span>
- <span data-ttu-id="6639d-116">Clear-Content</span><span class="sxs-lookup"><span data-stu-id="6639d-116">Clear-Content</span></span>
- <span data-ttu-id="6639d-117">Get-Content</span><span class="sxs-lookup"><span data-stu-id="6639d-117">Get-Content</span></span>
- <span data-ttu-id="6639d-118">Set-Content</span><span class="sxs-lookup"><span data-stu-id="6639d-118">Set-Content</span></span>

<span data-ttu-id="6639d-119">항목 cmdlet</span><span class="sxs-lookup"><span data-stu-id="6639d-119">Item cmdlets</span></span>

- <span data-ttu-id="6639d-120">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="6639d-120">Clear-Item</span></span>
- <span data-ttu-id="6639d-121">Copy-Item</span><span class="sxs-lookup"><span data-stu-id="6639d-121">Copy-Item</span></span>
- <span data-ttu-id="6639d-122">Get-Item</span><span class="sxs-lookup"><span data-stu-id="6639d-122">Get-Item</span></span>
- <span data-ttu-id="6639d-123">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="6639d-123">Invoke-Item</span></span>
- <span data-ttu-id="6639d-124">Move-Item</span><span class="sxs-lookup"><span data-stu-id="6639d-124">Move-Item</span></span>
- <span data-ttu-id="6639d-125">New-Item</span><span class="sxs-lookup"><span data-stu-id="6639d-125">New-Item</span></span>
- <span data-ttu-id="6639d-126">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="6639d-126">Remove-Item</span></span>
- <span data-ttu-id="6639d-127">Rename-Item</span><span class="sxs-lookup"><span data-stu-id="6639d-127">Rename-Item</span></span>
- <span data-ttu-id="6639d-128">Set-Item</span><span class="sxs-lookup"><span data-stu-id="6639d-128">Set-Item</span></span>

<span data-ttu-id="6639d-129">Get-itemproperty cmdlet</span><span class="sxs-lookup"><span data-stu-id="6639d-129">ItemProperty cmdlets</span></span>

- <span data-ttu-id="6639d-130">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="6639d-130">Clear-ItemProperty</span></span>
- <span data-ttu-id="6639d-131">Copy-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="6639d-131">Copy-ItemProperty</span></span>
- <span data-ttu-id="6639d-132">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="6639d-132">Get-ItemProperty</span></span>
- <span data-ttu-id="6639d-133">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="6639d-133">Move-ItemProperty</span></span>
- <span data-ttu-id="6639d-134">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="6639d-134">New-ItemProperty</span></span>
- <span data-ttu-id="6639d-135">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="6639d-135">Remove-ItemProperty</span></span>
- <span data-ttu-id="6639d-136">Rename-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="6639d-136">Rename-ItemProperty</span></span>
- <span data-ttu-id="6639d-137">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="6639d-137">Set-ItemProperty</span></span>

<span data-ttu-id="6639d-138">위치 cmdlet</span><span class="sxs-lookup"><span data-stu-id="6639d-138">Location cmdlets</span></span>

- <span data-ttu-id="6639d-139">Get-Location</span><span class="sxs-lookup"><span data-stu-id="6639d-139">Get-Location</span></span>
- <span data-ttu-id="6639d-140">Pop-Location</span><span class="sxs-lookup"><span data-stu-id="6639d-140">Pop-Location</span></span>
- <span data-ttu-id="6639d-141">Push-Location</span><span class="sxs-lookup"><span data-stu-id="6639d-141">Push-Location</span></span>
- <span data-ttu-id="6639d-142">Set-Location</span><span class="sxs-lookup"><span data-stu-id="6639d-142">Set-Location</span></span>

<span data-ttu-id="6639d-143">경로 cmdlet</span><span class="sxs-lookup"><span data-stu-id="6639d-143">Path cmdlets</span></span>

- <span data-ttu-id="6639d-144">Join-Path</span><span class="sxs-lookup"><span data-stu-id="6639d-144">Join-Path</span></span>
- <span data-ttu-id="6639d-145">Convert-Path</span><span class="sxs-lookup"><span data-stu-id="6639d-145">Convert-Path</span></span>
- <span data-ttu-id="6639d-146">Split-Path</span><span class="sxs-lookup"><span data-stu-id="6639d-146">Split-Path</span></span>
- <span data-ttu-id="6639d-147">Resolve-Path</span><span class="sxs-lookup"><span data-stu-id="6639d-147">Resolve-Path</span></span>
- <span data-ttu-id="6639d-148">Test-Path</span><span class="sxs-lookup"><span data-stu-id="6639d-148">Test-Path</span></span>

<span data-ttu-id="6639d-149">PSDrive cmdlet</span><span class="sxs-lookup"><span data-stu-id="6639d-149">PSDrive cmdlets</span></span>

- <span data-ttu-id="6639d-150">Get-PSDrive</span><span class="sxs-lookup"><span data-stu-id="6639d-150">Get-PSDrive</span></span>
- <span data-ttu-id="6639d-151">New-PSDrive</span><span class="sxs-lookup"><span data-stu-id="6639d-151">New-PSDrive</span></span>
- <span data-ttu-id="6639d-152">Remove-PSDrive</span><span class="sxs-lookup"><span data-stu-id="6639d-152">Remove-PSDrive</span></span>

<span data-ttu-id="6639d-153">PSProvider cmdlet</span><span class="sxs-lookup"><span data-stu-id="6639d-153">PSProvider cmdlets</span></span>

- <span data-ttu-id="6639d-154">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="6639d-154">Get-PSProvider</span></span>

<span data-ttu-id="6639d-155">Cmdlet에 대 한 자세한 내용을 보려면를 입력 하십시오 `get-help <cmdlet-name>` .</span><span class="sxs-lookup"><span data-stu-id="6639d-155">For more information about a cmdlet, type `get-help <cmdlet-name>`.</span></span>

## <a name="see-also"></a><span data-ttu-id="6639d-156">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6639d-156">SEE ALSO</span></span>

[<span data-ttu-id="6639d-157">about_Providers</span><span class="sxs-lookup"><span data-stu-id="6639d-157">about_Providers</span></span>](about_Providers.md)

