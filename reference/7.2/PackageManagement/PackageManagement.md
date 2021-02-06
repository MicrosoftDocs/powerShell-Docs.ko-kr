---
Download Help Link: https://aka.ms/powershell72-help
Help Version: 7.2.0.0
Locale: en-US
Module Guid: 4ae9fd46-338a-459c-8186-07f910774cb8
Module Name: PackageManagement
ms.date: 06/09/2017
schema: 2.0.0
title: PackageManagement
ms.openlocfilehash: 86e6f37f6f7f0527c5dcca309cf581cb6f1b4de5
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/19/2020
ms.locfileid: "99599751"
---
# <span data-ttu-id="4bc99-102">PackageManagement 모듈</span><span class="sxs-lookup"><span data-stu-id="4bc99-102">PackageManagement Module</span></span>

## <span data-ttu-id="4bc99-103">설명</span><span class="sxs-lookup"><span data-stu-id="4bc99-103">Description</span></span>

<span data-ttu-id="4bc99-104">이 항목에서는 패키지 관리 Cmdlet에 대 한 도움말 항목을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="4bc99-104">This topic displays help topics for the Package Management Cmdlets.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4bc99-105">2020년 4월부터 PowerShell 갤러리는 더 이상 TLS(전송 계층 보안) 버전 1.0 및 1.1을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4bc99-105">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="4bc99-106">TLS 1.2 이상을 사용하지 않을 경우 PowerShell 갤러리에 액세스하려고 하면 오류가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4bc99-106">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="4bc99-107">다음 명령을 사용하여 TLS 1.2를 사용하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="4bc99-107">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="4bc99-108">자세한 내용은 PowerShell 블로그의 [공지](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4bc99-108">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="4bc99-109">PackageManagement Cmdlet</span><span class="sxs-lookup"><span data-stu-id="4bc99-109">PackageManagement Cmdlets</span></span>

### [<span data-ttu-id="4bc99-110">Find-Package</span><span class="sxs-lookup"><span data-stu-id="4bc99-110">Find-Package</span></span>](Find-Package.md)
<span data-ttu-id="4bc99-111">사용 가능한 패키지 소스에서 소프트웨어 패키지를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="4bc99-111">Finds software packages in available package sources.</span></span>

### [<span data-ttu-id="4bc99-112">Find-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="4bc99-112">Find-PackageProvider</span></span>](Find-PackageProvider.md)
<span data-ttu-id="4bc99-113">설치에 사용할 수 있는 패키지 관리 패키지 공급자 목록을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="4bc99-113">Returns a list of Package Management package providers available for installation.</span></span>

### [<span data-ttu-id="4bc99-114">Get-Package</span><span class="sxs-lookup"><span data-stu-id="4bc99-114">Get-Package</span></span>](Get-Package.md)
<span data-ttu-id="4bc99-115">**PackageManagement** 를 사용 하 여 설치 된 모든 소프트웨어 패키지 목록을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="4bc99-115">Returns a list of all software packages that were installed with **PackageManagement**.</span></span>

### [<span data-ttu-id="4bc99-116">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="4bc99-116">Get-PackageProvider</span></span>](Get-PackageProvider.md)
<span data-ttu-id="4bc99-117">패키지 관리에 연결 된 패키지 공급자의 목록을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="4bc99-117">Returns a list of package providers that are connected to Package Management.</span></span>

### [<span data-ttu-id="4bc99-118">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="4bc99-118">Get-PackageSource</span></span>](Get-PackageSource.md)
<span data-ttu-id="4bc99-119">패키지 공급자에 대해 등록 된 패키지 소스 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="4bc99-119">Gets a list of package sources that are registered for a package provider.</span></span>

### [<span data-ttu-id="4bc99-120">Import-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="4bc99-120">Import-PackageProvider</span></span>](Import-PackageProvider.md)
<span data-ttu-id="4bc99-121">현재 세션에 패키지 관리 패키지 공급자를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="4bc99-121">Adds Package Management package providers to the current session.</span></span>

### [<span data-ttu-id="4bc99-122">Install-Package</span><span class="sxs-lookup"><span data-stu-id="4bc99-122">Install-Package</span></span>](Install-Package.md)
<span data-ttu-id="4bc99-123">하나 이상의 소프트웨어 패키지를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="4bc99-123">Installs one or more software packages.</span></span>

### [<span data-ttu-id="4bc99-124">Install-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="4bc99-124">Install-PackageProvider</span></span>](Install-PackageProvider.md)
<span data-ttu-id="4bc99-125">하나 이상의 패키지 관리 패키지 공급자를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="4bc99-125">Installs one or more Package Management package providers.</span></span>

### [<span data-ttu-id="4bc99-126">Register-PackageSource</span><span class="sxs-lookup"><span data-stu-id="4bc99-126">Register-PackageSource</span></span>](Register-PackageSource.md)
<span data-ttu-id="4bc99-127">지정 된 패키지 공급자에 대 한 패키지 소스를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="4bc99-127">Adds a package source for a specified package provider.</span></span>

### [<span data-ttu-id="4bc99-128">Save-Package</span><span class="sxs-lookup"><span data-stu-id="4bc99-128">Save-Package</span></span>](Save-Package.md)
<span data-ttu-id="4bc99-129">패키지를 설치 하지 않고 로컬 컴퓨터에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="4bc99-129">Saves packages to the local computer without installing them.</span></span>

### [<span data-ttu-id="4bc99-130">Set-PackageSource</span><span class="sxs-lookup"><span data-stu-id="4bc99-130">Set-PackageSource</span></span>](Set-PackageSource.md)
<span data-ttu-id="4bc99-131">지정 된 패키지 공급자에 대 한 패키지 원본을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="4bc99-131">Replaces a package source for a specified package provider.</span></span>

### [<span data-ttu-id="4bc99-132">Uninstall-Package</span><span class="sxs-lookup"><span data-stu-id="4bc99-132">Uninstall-Package</span></span>](Uninstall-Package.md)
<span data-ttu-id="4bc99-133">하나 이상의 소프트웨어 패키지를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="4bc99-133">Uninstalls one or more software packages.</span></span>

### [<span data-ttu-id="4bc99-134">Unregister-PackageSource</span><span class="sxs-lookup"><span data-stu-id="4bc99-134">Unregister-PackageSource</span></span>](Unregister-PackageSource.md)
<span data-ttu-id="4bc99-135">등록 된 패키지 소스를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="4bc99-135">Removes a registered package source.</span></span>
