---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery,psget,갤러리
title: PowerShell 갤러리
ms.openlocfilehash: d3e3b9d8bb3d6cefd3a3bfe79b012bb1dc1d8a2d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "71327864"
---
# <a name="the-powershell-gallery"></a><span data-ttu-id="8b287-103">PowerShell 갤러리</span><span class="sxs-lookup"><span data-stu-id="8b287-103">The PowerShell Gallery</span></span>

<span data-ttu-id="8b287-104">PowerShell 갤러리는 PowerShell 콘텐츠의 중앙 리포지토리입니다.</span><span class="sxs-lookup"><span data-stu-id="8b287-104">The PowerShell Gallery is the central repository for PowerShell content.</span></span> <span data-ttu-id="8b287-105">PowerShell 갤러리에서 PowerShell 명령 및 DSC(필요한 상태 구성) 리소스가 포함된 유용한 PowerShell 모듈을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b287-105">In it, you can find useful PowerShell modules containing PowerShell commands and Desired State Configuration (DSC) resources.</span></span>
<span data-ttu-id="8b287-106">PowerShell 워크플로가 포함된 경우도 있으며 일련의 작업을 간략하게 설명하고 해당 작업 순서를 제공하는 PowerShell 스크립트를 찾을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b287-106">You can also find PowerShell scripts, some of which may contain PowerShell workflows, and which outline a set of tasks and provide sequencing for those tasks.</span></span> <span data-ttu-id="8b287-107">이러한 패키지 중 일부는 Microsoft에서 작성되었으며 다른 항목은 PowerShell 커뮤니티에서 작성되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8b287-107">Some of these packages are authored by Microsoft, and others are authored by the PowerShell community.</span></span>

## <a name="powershellget-overview"></a><span data-ttu-id="8b287-108">PowerShellGet 개요</span><span class="sxs-lookup"><span data-stu-id="8b287-108">PowerShellGet Overview</span></span>

<span data-ttu-id="8b287-109">PowerShellGet 모듈에는 [PowerShell 갤러리](https://www.PowerShellGallery.com) 및 다른 개인 리포지토리에서 모듈, DSC 리소스, 역할 기능 및 스크립트와 같은 아티팩트가 포함된 PowerShell 패키지를 검색, 설치, 업데이트 및 게시하기 위한 cmdlet이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b287-109">The PowerShellGet module contains cmdlets for discovering, installing, updating and publishing PowerShell packages which contain artifacts such as Modules, DSC Resources, Role Capabilities and Scripts from the [PowerShell Gallery](https://www.PowerShellGallery.com) and other private repositories.</span></span>

## <a name="getting-started-with-the-gallery"></a><span data-ttu-id="8b287-110">갤러리 시작</span><span class="sxs-lookup"><span data-stu-id="8b287-110">Getting Started with the Gallery</span></span>

<span data-ttu-id="8b287-111">갤러리에서 패키지를 설치하려면 최신 버전의 PowerShellGet 모듈이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="8b287-111">Installing packages from the Gallery requires the latest version of the PowerShellGet module.</span></span>
<span data-ttu-id="8b287-112">자세한 지침은 [PowerShellGet](installing-psget.md) 설치를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8b287-112">See [Installing PowerShellGet](installing-psget.md) for complete instructions.</span></span>

<span data-ttu-id="8b287-113">갤러리와 함께 PowerShellGet 명령을 사용하는 방법에 대한 자세한 내용은 [시작](getting-started.md) 페이지를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8b287-113">Check out the [Getting Started](getting-started.md) page for more information on how to use PowerShellGet commands with the Gallery.</span></span> <span data-ttu-id="8b287-114">*Update-Help -Module PowerShellGet*을 실행하여 이러한 명령에 대한 로컬 도움말을 설치할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b287-114">You can also run *Update-Help -Module PowerShellGet* to install local help for these commands.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="8b287-115">지원되는 운영 체제</span><span class="sxs-lookup"><span data-stu-id="8b287-115">Supported Operating Systems</span></span>

<span data-ttu-id="8b287-116">**PowerShellGet** 모듈을 사용하려면 **Windows PowerShell 3.0 이상** 또는 **PowerShell Core 6.0 이상**이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="8b287-116">The **PowerShellGet** module requires **Windows PowerShell 3.0 or newer**, or **PowerShell Core 6.0 or newer**.</span></span>

<span data-ttu-id="8b287-117">적합한 **Windows PowerShell** 버전을 사용할 수 있는 운영 체제는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8b287-117">A suitable version of **Windows PowerShell** is available for these operating systems:</span></span>

- <span data-ttu-id="8b287-118">Windows 10</span><span class="sxs-lookup"><span data-stu-id="8b287-118">Windows 10</span></span>
- <span data-ttu-id="8b287-119">Windows 8.1 Pro</span><span class="sxs-lookup"><span data-stu-id="8b287-119">Windows 8.1 Pro</span></span>
- <span data-ttu-id="8b287-120">Windows 8.1 Enterprise</span><span class="sxs-lookup"><span data-stu-id="8b287-120">Windows 8.1 Enterprise</span></span>
- <span data-ttu-id="8b287-121">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="8b287-121">Windows 7 SP1</span></span>
- <span data-ttu-id="8b287-122">Windows Server 2019</span><span class="sxs-lookup"><span data-stu-id="8b287-122">Windows Server 2019</span></span>
- <span data-ttu-id="8b287-123">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="8b287-123">Windows Server 2016</span></span>
- <span data-ttu-id="8b287-124">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="8b287-124">Windows Server 2012 R2</span></span>
- <span data-ttu-id="8b287-125">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="8b287-125">Windows Server 2008 R2 SP1</span></span>

<span data-ttu-id="8b287-126">**PowerShellGet**을 사용하려면 .NET Framework 4.5 이상이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="8b287-126">**PowerShellGet** requires .NET Framework 4.5 or above.</span></span> <span data-ttu-id="8b287-127">.NET Framework 4.5 이상은 [여기](https://msdn.microsoft.com/library/5a4x27ek.aspx)에서 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b287-127">You can install .NET Framework 4.5 or above from [here](https://msdn.microsoft.com/library/5a4x27ek.aspx).</span></span>

<span data-ttu-id="8b287-128">**PowerShell Core**는 교차 플랫폼이므로 Windows, Linux 및 MacOS에서 작동하며, 그렇기 때문에 **PowerShellGet**을 이러한 시스템들에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b287-128">Since **PowerShell Core** is cross-platform and that means it works on Windows, Linux and MacOS, that also makes **PowerShellGet** available on those systems.</span></span> <span data-ttu-id="8b287-129">**PowerShell Core**가 지원하는 전체 시스템 목록은 [PowerShell 설치](/powershell/scripting/setup/installing-powershell)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8b287-129">For a full list of systems supported by **PowerShell Core** see [Installing PowerShell](/powershell/scripting/setup/installing-powershell).</span></span>

<span data-ttu-id="8b287-130">갤러리에 호스트된 많은 모듈은 각기 다른 OS를 지원하며 추가 요구 사항이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b287-130">Many modules hosted in the gallery will support different OSes and have additional requirements.</span></span> <span data-ttu-id="8b287-131">자세한 내용은 모듈 설명서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8b287-131">Please refer to the documentation for the modules for more information.</span></span>

## <a name="got-a-question-have-feedback"></a><span data-ttu-id="8b287-132">궁금한 점이 있나요?</span><span class="sxs-lookup"><span data-stu-id="8b287-132">Got a question?</span></span> <span data-ttu-id="8b287-133">피드백이 있습니까?</span><span class="sxs-lookup"><span data-stu-id="8b287-133">Have feedback?</span></span>

<span data-ttu-id="8b287-134">PowerShell 갤러리 및 PowerShellGet에 대한 자세한 내용은 [시작](getting-started.md) 페이지에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b287-134">More information about the PowerShell Gallery and PowerShellGet can be found in the [Getting Started](getting-started.md) page.</span></span> <span data-ttu-id="8b287-135">[UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell)를 사용하여 피드백을 제공하고 문제를 신고하세요.</span><span class="sxs-lookup"><span data-stu-id="8b287-135">Please provide feedback and report issues using [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span></span>
