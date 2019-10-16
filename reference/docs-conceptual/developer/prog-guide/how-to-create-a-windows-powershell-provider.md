---
title: Windows PowerShell 공급자를 만드는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- providers [PowerShell Programmer's Guide]
- providers [PowerShellProgrammer's Guide], creating
- Windows PowerShell Programmer's Guide, providers
ms.assetid: 863e48e9-7206-4c6a-a59a-2ab2d30396bc
caps.latest.revision: 5
ms.openlocfilehash: ffbf8028ba2b52e77d8e22c061baa9b8b67f6da3
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366652"
---
# <a name="how-to-create-a-windows-powershell-provider"></a><span data-ttu-id="07ce3-102">Windows PowerShell 공급자를 만드는 방법</span><span class="sxs-lookup"><span data-stu-id="07ce3-102">How to Create a Windows PowerShell Provider</span></span>

<span data-ttu-id="07ce3-103">이 섹션에서는 Windows PowerShell 공급자를 빌드하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="07ce3-103">This section describes how to build a Windows PowerShell provider.</span></span> <span data-ttu-id="07ce3-104">Windows PowerShell 공급자를 두 가지 방법으로 고려할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07ce3-104">A Windows PowerShell provider can be considered in two ways.</span></span> <span data-ttu-id="07ce3-105">사용자에 게 공급자는 저장 된 데이터 집합을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="07ce3-105">To the user, the provider represents a set of stored data.</span></span> <span data-ttu-id="07ce3-106">예를 들어 저장 된 데이터는 인터넷 정보 서비스 (IIS) 메타 베이스, Microsoft Windows 레지스트리, Windows 파일 시스템, Active Directory, Windows PowerShell에서 저장 한 변수 및 별칭 데이터 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07ce3-106">For example, the stored data can be the Internet Information Services (IIS) Metabase, the Microsoft Windows Registry, the Windows file system, Active Directory, and the variable and alias data stored by Windows PowerShell.</span></span>

<span data-ttu-id="07ce3-107">개발자에 게 Windows PowerShell 공급자는 사용자가 액세스 해야 하는 데이터와 사용자 간의 인터페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="07ce3-107">To the developer, the Windows PowerShell provider is the interface between the user and the data that the user needs to access.</span></span> <span data-ttu-id="07ce3-108">이 섹션에서 설명 하는 각 유형의 공급자는 Windows PowerShell 런타임에서 특정 cmdlet을 일반적인 방법으로 사용자에 게 노출 하는 데 사용할 수 있는 특정 기본 클래스 및 인터페이스 집합을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="07ce3-108">From this perspective, each type of provider described in this section supports a set of specific base classes and interfaces that allow the Windows PowerShell runtime to expose certain cmdlets to the user in a common way.</span></span>

## <a name="providers-provided-by-windows-powershell"></a><span data-ttu-id="07ce3-109">Windows PowerShell에서 제공 하는 공급자</span><span class="sxs-lookup"><span data-stu-id="07ce3-109">Providers Provided by Windows PowerShell</span></span>

<span data-ttu-id="07ce3-110">Windows PowerShell은 알려진 데이터 저장소에 액세스 하는 데 사용 되는 여러 공급자 (예: 파일 시스템 공급자, 레지스트리 공급자 및 별칭 공급자)를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="07ce3-110">Windows PowerShell provides several providers (such as the FileSystem provider, Registry provider, and Alias provider) that are used to access known data stores.</span></span> <span data-ttu-id="07ce3-111">Windows PowerShell에서 제공 하는 공급자에 대 한 자세한 내용은 다음 명령을 사용 하 여 온라인 도움말에 액세스 합니다.</span><span class="sxs-lookup"><span data-stu-id="07ce3-111">For more information about the providers supplied by Windows PowerShell, use the following command to access online Help:</span></span>

<span data-ttu-id="07ce3-112">**PS > get-help about_providers**</span><span class="sxs-lookup"><span data-stu-id="07ce3-112">**PS>get-help about_providers**</span></span>

## <a name="accessing-the-stored-data-using-windows-powershell-paths"></a><span data-ttu-id="07ce3-113">Windows PowerShell 경로를 사용 하 여 저장 된 데이터에 액세스</span><span class="sxs-lookup"><span data-stu-id="07ce3-113">Accessing the Stored Data Using Windows PowerShell Paths</span></span>

<span data-ttu-id="07ce3-114">Windows powershell 공급자는 windows powershell 런타임 및 windows PowerShell 경로를 사용 하 여 프로그래밍 방식으로 명령에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07ce3-114">Windows PowerShell providers are accessible to the Windows PowerShell runtime and to commands programmatically through the use of Windows PowerShell paths.</span></span> <span data-ttu-id="07ce3-115">대부분의 경우 이러한 경로는 공급자를 통해 데이터에 직접 액세스 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="07ce3-115">Most of the time, these paths are used to directly access the data through the provider.</span></span> <span data-ttu-id="07ce3-116">그러나 일부 경로는 cmdlet이 비 Windows PowerShell Api (응용 프로그래밍 인터페이스)를 사용 하 여 데이터에 액세스할 수 있도록 하는 공급자 내부 경로로 확인 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07ce3-116">However, some paths can be resolved to provider-internal paths that allow a cmdlet to use non-Windows PowerShell application programming interfaces (APIs) to access the data.</span></span> <span data-ttu-id="07ce3-117">Windows powershell에서 windows powershell 공급자가 작동 하는 방식에 대 한 자세한 내용은 [Windows Powershell 작동 방법](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="07ce3-117">For more information about how Windows PowerShell providers operate within Windows PowerShell, see [How Windows PowerShell Works](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58).</span></span>

## <a name="exposing-provider-cmdlets-using-windows-powershell-drives"></a><span data-ttu-id="07ce3-118">Windows PowerShell 드라이브를 사용 하 여 공급자 Cmdlet 노출</span><span class="sxs-lookup"><span data-stu-id="07ce3-118">Exposing Provider Cmdlets Using Windows PowerShell Drives</span></span>

<span data-ttu-id="07ce3-119">Windows PowerShell 공급자는 가상 Windows PowerShell 드라이브를 사용 하 여 지원 되는 cmdlet을 노출 합니다.</span><span class="sxs-lookup"><span data-stu-id="07ce3-119">A Windows PowerShell provider exposes its supported cmdlets using virtual Windows PowerShell drives.</span></span> <span data-ttu-id="07ce3-120">Windows PowerShell은 Windows PowerShell 드라이브에 대해 다음 규칙을 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="07ce3-120">Windows PowerShell applies the following rules for a Windows PowerShell drive:</span></span>

- <span data-ttu-id="07ce3-121">드라이브 이름은 영숫자 시퀀스가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07ce3-121">The name of a drive can be any alphanumeric sequence.</span></span>

- <span data-ttu-id="07ce3-122">드라이브는 "root" 라는 경로의 모든 유효한 지점에서 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07ce3-122">A drive can be specified at any valid point on a path, called a "root".</span></span>

- <span data-ttu-id="07ce3-123">파일 시스템 뿐만 아니라 저장 된 모든 데이터에 대해 드라이브를 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07ce3-123">A drive can be implemented for any stored data, not just the file system.</span></span>

- <span data-ttu-id="07ce3-124">각 드라이브는 자신의 현재 작업 위치를 유지 하므로 사용자는 드라이브 간을 이동할 때 컨텍스트를 유지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07ce3-124">Each drive keeps its own current working location, allowing the user to retain context when shifting between drives.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="07ce3-125">이 섹션의 내용</span><span class="sxs-lookup"><span data-stu-id="07ce3-125">In This Section</span></span>

<span data-ttu-id="07ce3-126">다음 표에서는 서로를 구성 하는 코드 예제를 포함 하는 항목을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="07ce3-126">The following table lists topics that include code examples that build on each other.</span></span> <span data-ttu-id="07ce3-127">두 번째 항목부터 Windows PowerShell 런타임으로 기본 Windows PowerShell 공급자를 초기화 하 고 초기화할 수 있습니다. 다음 항목에서는 데이터에 액세스 하는 기능을 추가 합니다. 다음 항목에서는 데이터를 조작 하는 기능을 추가 합니다. 저장 된 데이터의 항목 등).</span><span class="sxs-lookup"><span data-stu-id="07ce3-127">Starting with the second topic, the basic Windows PowerShell provider can be initialized and uninitialized by the Windows PowerShell runtime, the next topic adds functionality for accessing the data, the next topic adds functionality for manipulating the data (the items in the stored data), and so on.</span></span>

|<span data-ttu-id="07ce3-128">항목</span><span class="sxs-lookup"><span data-stu-id="07ce3-128">Topic</span></span>|<span data-ttu-id="07ce3-129">정의</span><span class="sxs-lookup"><span data-stu-id="07ce3-129">Definition</span></span>|
|-----------|----------------|
|[<span data-ttu-id="07ce3-130">Windows PowerShell 공급자 디자인</span><span class="sxs-lookup"><span data-stu-id="07ce3-130">Designing Your Windows PowerShell Provider</span></span>](./designing-your-windows-powershell-provider.md)|<span data-ttu-id="07ce3-131">이 항목에서는 Windows PowerShell 공급자를 구현 하기 전에 고려해 야 할 사항에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="07ce3-131">This topic discusses things you should consider before implementing a Windows PowerShell provider.</span></span> <span data-ttu-id="07ce3-132">사용 되는 Windows PowerShell 공급자 기본 클래스 및 인터페이스를 요약 합니다.</span><span class="sxs-lookup"><span data-stu-id="07ce3-132">It summarizes the Windows PowerShell provider base classes and interfaces that are used.</span></span>|
|[<span data-ttu-id="07ce3-133">기본 Windows PowerShell 공급자 만들기</span><span class="sxs-lookup"><span data-stu-id="07ce3-133">Creating a Basic Windows PowerShell Provider</span></span>](./creating-a-basic-windows-powershell-provider.md)|<span data-ttu-id="07ce3-134">이 항목에서는 Windows PowerShell 런타임에서 공급자를 초기화 하 고 초기화 하지 않도록 허용 하는 Windows PowerShell 공급자를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="07ce3-134">This topic shows how to create a Windows PowerShell provider that allows the Windows PowerShell runtime to initialize and uninitialize the provider.</span></span>|
|[<span data-ttu-id="07ce3-135">Windows PowerShell 드라이브 공급자 만들기</span><span class="sxs-lookup"><span data-stu-id="07ce3-135">Creating a Windows PowerShell Drive Provider</span></span>](./creating-a-windows-powershell-drive-provider.md)|<span data-ttu-id="07ce3-136">이 항목에서는 사용자가 Windows PowerShell 드라이브를 통해 데이터 저장소에 액세스할 수 있도록 하는 Windows PowerShell 공급자를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="07ce3-136">This topic shows how to create a Windows PowerShell provider that allows the user to access a data store through a Windows PowerShell drive.</span></span>|
|[<span data-ttu-id="07ce3-137">Windows PowerShell 항목 공급자 만들기</span><span class="sxs-lookup"><span data-stu-id="07ce3-137">Creating a Windows PowerShell Item Provider</span></span>](./creating-a-windows-powershell-item-provider.md)|<span data-ttu-id="07ce3-138">이 항목에서는 사용자가 데이터 저장소의 항목을 조작할 수 있도록 하는 Windows PowerShell 공급자를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="07ce3-138">This topic shows how to create a Windows PowerShell provider that allows the user to manipulate the items in a data store.</span></span>|
|[<span data-ttu-id="07ce3-139">Windows PowerShell 컨테이너 공급자 만들기</span><span class="sxs-lookup"><span data-stu-id="07ce3-139">Creating a Windows PowerShell Container Provider</span></span>](./creating-a-windows-powershell-container-provider.md)|<span data-ttu-id="07ce3-140">이 항목에서는 사용자가 다중 계층 데이터 저장소에서 작업할 수 있도록 하는 Windows PowerShell 공급자를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="07ce3-140">This topic shows how to create a Windows PowerShell provider that allows the user to work on multilayer data stores.</span></span>|
|[<span data-ttu-id="07ce3-141">Windows PowerShell 탐색 공급자 만들기</span><span class="sxs-lookup"><span data-stu-id="07ce3-141">Creating a Windows PowerShell Navigation Provider</span></span>](./creating-a-windows-powershell-navigation-provider.md)|<span data-ttu-id="07ce3-142">이 항목에서는 사용자가 계층적 방식으로 데이터 저장소의 항목을 탐색할 수 있도록 하는 Windows PowerShell 공급자를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="07ce3-142">This topic shows how to create a Windows PowerShell provider that allows the user to navigate the items of a data store in a hierarchical manner.</span></span>|
|[<span data-ttu-id="07ce3-143">Windows PowerShell 콘텐츠 공급자 만들기</span><span class="sxs-lookup"><span data-stu-id="07ce3-143">Creating a Windows PowerShell Content Provider</span></span>](./creating-a-windows-powershell-content-provider.md)|<span data-ttu-id="07ce3-144">이 항목에서는 사용자가 데이터 저장소에 있는 항목의 내용을 조작할 수 있도록 하는 Windows PowerShell 공급자를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="07ce3-144">This topic shows how to create a Windows PowerShell provider that allows the user to manipulate the content of items in a data store.</span></span>|
|[<span data-ttu-id="07ce3-145">Windows PowerShell 속성 공급자 만들기</span><span class="sxs-lookup"><span data-stu-id="07ce3-145">Creating a Windows PowerShell Property Provider</span></span>](./creating-a-windows-powershell-property-provider.md)|<span data-ttu-id="07ce3-146">이 항목에서는 사용자가 데이터 저장소에 있는 항목의 속성을 조작할 수 있도록 하는 Windows PowerShell 공급자를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="07ce3-146">This topic shows how to create a Windows PowerShell provider that allows the user to manipulate the properties of items in a data store.</span></span>|

## <a name="see-also"></a><span data-ttu-id="07ce3-147">참고 항목</span><span class="sxs-lookup"><span data-stu-id="07ce3-147">See Also</span></span>

[<span data-ttu-id="07ce3-148">Windows PowerShell 작동 방법</span><span class="sxs-lookup"><span data-stu-id="07ce3-148">How Windows PowerShell Works</span></span>](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[<span data-ttu-id="07ce3-149">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="07ce3-149">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="07ce3-150">Windows PowerShell 프로그래머 가이드</span><span class="sxs-lookup"><span data-stu-id="07ce3-150">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)
