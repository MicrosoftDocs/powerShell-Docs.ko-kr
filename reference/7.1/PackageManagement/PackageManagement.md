---
Download Help Link: https://aka.ms/powershell71-help
Help Version: 7.1.0.0
keywords: powershell,cmdlet
Locale: en-US
Module Guid: 4ae9fd46-338a-459c-8186-07f910774cb8
Module Name: PackageManagement
ms.date: 06/09/2017
schema: 2.0.0
title: PackageManagement
ms.openlocfilehash: 88dcb47bee268af3553bb797aaa264e27ed8c51c
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94889643"
---
# <span data-ttu-id="b9651-103">PackageManagement 모듈</span><span class="sxs-lookup"><span data-stu-id="b9651-103">PackageManagement Module</span></span>

## <span data-ttu-id="b9651-104">설명</span><span class="sxs-lookup"><span data-stu-id="b9651-104">Description</span></span>

<span data-ttu-id="b9651-105">이 항목에서는 패키지 관리 Cmdlet에 대 한 도움말 항목을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9651-105">This topic displays help topics for the Package Management Cmdlets.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b9651-106">2020 4 월부터 PowerShell 갤러리는 더 이상 TLS (Transport Layer Security) 버전 1.0 및 1.1을 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b9651-106">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="b9651-107">TLS 1.2 이상을 사용 하지 않는 경우 PowerShell 갤러리에 액세스 하려고 하면 오류가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b9651-107">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="b9651-108">다음 명령을 사용 하 여 TLS 1.2을 사용 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9651-108">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="b9651-109">자세한 내용은 PowerShell 블로그의 [공지](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b9651-109">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="b9651-110">PackageManagement Cmdlet</span><span class="sxs-lookup"><span data-stu-id="b9651-110">PackageManagement Cmdlets</span></span>

### [<span data-ttu-id="b9651-111">Find-Package</span><span class="sxs-lookup"><span data-stu-id="b9651-111">Find-Package</span></span>](Find-Package.md)
<span data-ttu-id="b9651-112">사용 가능한 패키지 소스에서 소프트웨어 패키지를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="b9651-112">Finds software packages in available package sources.</span></span>

### [<span data-ttu-id="b9651-113">Find-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="b9651-113">Find-PackageProvider</span></span>](Find-PackageProvider.md)
<span data-ttu-id="b9651-114">설치에 사용할 수 있는 패키지 관리 패키지 공급자 목록을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9651-114">Returns a list of Package Management package providers available for installation.</span></span>

### [<span data-ttu-id="b9651-115">Get-Package</span><span class="sxs-lookup"><span data-stu-id="b9651-115">Get-Package</span></span>](Get-Package.md)
<span data-ttu-id="b9651-116">**PackageManagement** 를 사용 하 여 설치 된 모든 소프트웨어 패키지 목록을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9651-116">Returns a list of all software packages that were installed with **PackageManagement**.</span></span>

### [<span data-ttu-id="b9651-117">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="b9651-117">Get-PackageProvider</span></span>](Get-PackageProvider.md)
<span data-ttu-id="b9651-118">패키지 관리에 연결 된 패키지 공급자의 목록을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9651-118">Returns a list of package providers that are connected to Package Management.</span></span>

### [<span data-ttu-id="b9651-119">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="b9651-119">Get-PackageSource</span></span>](Get-PackageSource.md)
<span data-ttu-id="b9651-120">패키지 공급자에 대해 등록 된 패키지 소스 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b9651-120">Gets a list of package sources that are registered for a package provider.</span></span>

### [<span data-ttu-id="b9651-121">Import-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="b9651-121">Import-PackageProvider</span></span>](Import-PackageProvider.md)
<span data-ttu-id="b9651-122">현재 세션에 패키지 관리 패키지 공급자를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9651-122">Adds Package Management package providers to the current session.</span></span>

### [<span data-ttu-id="b9651-123">Install-Package</span><span class="sxs-lookup"><span data-stu-id="b9651-123">Install-Package</span></span>](Install-Package.md)
<span data-ttu-id="b9651-124">하나 이상의 소프트웨어 패키지를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9651-124">Installs one or more software packages.</span></span>

### [<span data-ttu-id="b9651-125">Install-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="b9651-125">Install-PackageProvider</span></span>](Install-PackageProvider.md)
<span data-ttu-id="b9651-126">하나 이상의 패키지 관리 패키지 공급자를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9651-126">Installs one or more Package Management package providers.</span></span>

### [<span data-ttu-id="b9651-127">Register-PackageSource</span><span class="sxs-lookup"><span data-stu-id="b9651-127">Register-PackageSource</span></span>](Register-PackageSource.md)
<span data-ttu-id="b9651-128">지정 된 패키지 공급자에 대 한 패키지 소스를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9651-128">Adds a package source for a specified package provider.</span></span>

### [<span data-ttu-id="b9651-129">Save-Package</span><span class="sxs-lookup"><span data-stu-id="b9651-129">Save-Package</span></span>](Save-Package.md)
<span data-ttu-id="b9651-130">패키지를 설치 하지 않고 로컬 컴퓨터에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9651-130">Saves packages to the local computer without installing them.</span></span>

### [<span data-ttu-id="b9651-131">Set-PackageSource</span><span class="sxs-lookup"><span data-stu-id="b9651-131">Set-PackageSource</span></span>](Set-PackageSource.md)
<span data-ttu-id="b9651-132">지정 된 패키지 공급자에 대 한 패키지 원본을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="b9651-132">Replaces a package source for a specified package provider.</span></span>

### [<span data-ttu-id="b9651-133">Uninstall-Package</span><span class="sxs-lookup"><span data-stu-id="b9651-133">Uninstall-Package</span></span>](Uninstall-Package.md)
<span data-ttu-id="b9651-134">하나 이상의 소프트웨어 패키지를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9651-134">Uninstalls one or more software packages.</span></span>

### [<span data-ttu-id="b9651-135">Unregister-PackageSource</span><span class="sxs-lookup"><span data-stu-id="b9651-135">Unregister-PackageSource</span></span>](Unregister-PackageSource.md)
<span data-ttu-id="b9651-136">등록 된 패키지 소스를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9651-136">Removes a registered package source.</span></span>

