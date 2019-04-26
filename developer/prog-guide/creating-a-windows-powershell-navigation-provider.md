---
title: Windows PowerShell 탐색 공급자 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- navigation providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], navigation provider
ms.assetid: 8bd3224d-ca6f-4640-9464-cb4d9f4e13b1
caps.latest.revision: 5
ms.openlocfilehash: 40454f880b57d5b3a8a8ded21c8c97aebba027fe
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081855"
---
# <a name="creating-a-windows-powershell-navigation-provider"></a><span data-ttu-id="8ba21-102">Windows PowerShell 탐색 공급자 만들기</span><span class="sxs-lookup"><span data-stu-id="8ba21-102">Creating a Windows PowerShell Navigation Provider</span></span>

<span data-ttu-id="8ba21-103">이 항목에서는 데이터 저장소를 탐색할 수 있는 Windows PowerShell 탐색 공급자를 만드는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-103">This topic describes how to create a Windows PowerShell navigation provider that can navigate the data store.</span></span> <span data-ttu-id="8ba21-104">이 유형의 공급자는 재귀 명령, 중첩 된 컨테이너 및 상대 경로 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-104">This type of provider supports recursive commands, nested containers, and relative paths.</span></span>

> [!NOTE]
> <span data-ttu-id="8ba21-105">다운로드할 수 있습니다는 C# Microsoft Windows 소프트웨어 개발 키트에 대 한 Windows Vista 및.NET Framework 3.0 런타임 구성 요소를 사용 하 여이 공급자에 대 한 원본 파일 (AccessDBSampleProvider05.cs).</span><span class="sxs-lookup"><span data-stu-id="8ba21-105">You can download the C# source file (AccessDBSampleProvider05.cs) for this provider using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="8ba21-106">다운로드 지침에 대해서 [Windows PowerShell 설치 및 Windows PowerShell SDK를 다운로드 하는 방법을](/powershell/developer/installing-the-windows-powershell-sdk)합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="8ba21-107">다운로드 한 소스 파일에서 사용할 수는  **\<PowerShell 샘플 >** 디렉터리입니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>
>
> <span data-ttu-id="8ba21-108">다른 Windows PowerShell 공급자 구현에 대 한 자세한 내용은 참조 하십시오 [Your Windows PowerShell 공급자 디자인](./designing-your-windows-powershell-provider.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-108">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

<span data-ttu-id="8ba21-109">여기에 설명 된 공급자는 사용자 데이터베이스에 있는 데이터 테이블을 이동할 수 있도록 사용자 핸들 Access 데이터베이스 드라이브를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-109">The provider described here enables the user handle an Access database as a drive so that the user can navigate to the data tables in the database.</span></span> <span data-ttu-id="8ba21-110">사용자 고유의 탐색 공급자를 만들 때 드라이브의 정규화 된 경로 탐색 하는 데 필요한 확인, 상대 경로 정규화, 자식 이름을 가져올 항목의 부모 경로 가져옵니다 하 고 테스트 하는 방법 뿐만 아니라 데이터 저장소의 항목을 이동할 수 있는 메서드를 구현할 수 있습니다. 항목이 컨테이너인 경우를 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-110">When creating your own navigation provider, you can implement methods that can make drive-qualified paths required for navigation, normalize relative paths, move items of the data store, as well as methods that get child names, get the parent path of an item, and test to identify if an item is a container.</span></span>

> [!CAUTION]
> <span data-ttu-id="8ba21-111">이 디자인 이름 ID 사용 하 여 필드가 있는 데이터베이스를 가정 하 고 필드의 형식이 LongInteger 알아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-111">Be aware that this design assumes a database that has a field with the name ID, and that the type of the field is LongInteger.</span></span>

<span data-ttu-id="8ba21-112">다음은이 항목에서 섹션을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-112">The following list includes sections in this topic.</span></span> <span data-ttu-id="8ba21-113">Windows PowerShell 탐색 공급자 작성에 익숙한 경우 나타나는 순서에 따라이 정보를 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-113">If you are unfamiliar with writing a Windows PowerShell navigation provider, read this information in the order that it appears.</span></span> <span data-ttu-id="8ba21-114">그러나 Windows PowerShell 탐색 공급자 작성에 익숙한 경우 하세요로 직접 이동 해야 하는 정보.</span><span class="sxs-lookup"><span data-stu-id="8ba21-114">However, if you are familiar with writing a Windows PowerShell navigation provider, please go directly to the information that you need.</span></span>

- [<span data-ttu-id="8ba21-115">PS 탐색 공급자 클래스를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-115">Defining a PS Navigation Provider Class</span></span>](#Define-the-Windows-PowerShell-provider)

- [<span data-ttu-id="8ba21-116">기본 기능 정의</span><span class="sxs-lookup"><span data-stu-id="8ba21-116">Defining Base Functionality</span></span>](#Defining-Base-Functionality)

- [<span data-ttu-id="8ba21-117">PS 경로 만들기</span><span class="sxs-lookup"><span data-stu-id="8ba21-117">Creating a PS Path</span></span>](#Creating-a-Windows-PowerShell-Path)

- [<span data-ttu-id="8ba21-118">부모 경로 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-118">Retrieving the Parent Path</span></span>](#Retrieving-the-Parent-Path)

- [<span data-ttu-id="8ba21-119">자식 경로 이름 검색</span><span class="sxs-lookup"><span data-stu-id="8ba21-119">Retrieving the Child Path Name</span></span>](#Retrieve-the-Child-Path-Name)

- [<span data-ttu-id="8ba21-120">항목 컨테이너 인지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-120">Determining if an Item is a Container</span></span>](#Determining-if-an-Item-is-a-Container)

- [<span data-ttu-id="8ba21-121">항목 이동</span><span class="sxs-lookup"><span data-stu-id="8ba21-121">Moving an Item</span></span>](#Moving-an-Item)

- [<span data-ttu-id="8ba21-122">동적 매개 변수를 연결 합니다 `Move-Item` Cmdlet</span><span class="sxs-lookup"><span data-stu-id="8ba21-122">Attaching Dynamic Parameters to the `Move-Item` Cmdlet</span></span>](#Attaching-Dynamic-Parameters-to-the-Move-Item-Cmdlet)

- [<span data-ttu-id="8ba21-123">상대 경로 정규화합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-123">Normalizing a Relative Path</span></span>](#Normalizing-a-Relative-Path)

- [<span data-ttu-id="8ba21-124">코드 샘플</span><span class="sxs-lookup"><span data-stu-id="8ba21-124">Code Sample</span></span>](#Code-Sample)

- [<span data-ttu-id="8ba21-125">개체 유형 정의 및 서식 지정</span><span class="sxs-lookup"><span data-stu-id="8ba21-125">Defining Object Types and Formatting</span></span>](#Defining-Object-Types-and-Formatting)

- [<span data-ttu-id="8ba21-126">Windows PowerShell 공급자 작성</span><span class="sxs-lookup"><span data-stu-id="8ba21-126">Building the Windows PowerShell Provider</span></span>](#Building-the-Windows-PowerShell-provider)

- [<span data-ttu-id="8ba21-127">Windows PowerShell 공급자 테스트</span><span class="sxs-lookup"><span data-stu-id="8ba21-127">Testing the Windows PowerShell Provider</span></span>](#Testing-the-Windows-PowerShell-provider)

## <a name="define-the-windows-powershell-provider"></a><span data-ttu-id="8ba21-128">Windows PowerShell 공급자를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-128">Define the Windows PowerShell provider</span></span>

<span data-ttu-id="8ba21-129">Windows PowerShell 탐색 공급자에서 파생 되는.NET 클래스를 만들어야 합니다 [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 기본 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-129">A Windows PowerShell navigation provider must create a .NET class that derives from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) base class.</span></span> <span data-ttu-id="8ba21-130">이 섹션에 설명 된 탐색 공급자에 대 한 클래스 정의 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-130">Here is the class definition for the navigation provider described in this section.</span></span>

[!code-csharp[AccessDBProviderSample05.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample05/AccessDBProviderSample05.cs#L31-L32 "AccessDBProviderSample05.cs")]

<span data-ttu-id="8ba21-131">이 공급자는 [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) 특성에는 두 개의 매개 변수가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-131">Note that in this provider, the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attribute includes two parameters.</span></span> <span data-ttu-id="8ba21-132">첫 번째 매개 변수는 Windows PowerShell에서 사용 되는 공급자에 대 한 알기 쉬운 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-132">The first parameter specifies a user-friendly name for the provider that is used by Windows PowerShell.</span></span> <span data-ttu-id="8ba21-133">두 번째 매개 변수는 명령 처리 하는 동안 공급자가 Windows PowerShell 런타임에 노출 하는 Windows PowerShell 특정 기능을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-133">The second parameter specifies the Windows PowerShell specific capabilities that the provider exposes to the Windows PowerShell runtime during command processing.</span></span> <span data-ttu-id="8ba21-134">이 공급자에 대 한 추가 되는 Windows PowerShell 특정 기능이 없으며 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-134">For this provider, there are no Windows PowerShell specific capabilities that are added.</span></span>

## <a name="defining-base-functionality"></a><span data-ttu-id="8ba21-135">기본 기능 정의</span><span class="sxs-lookup"><span data-stu-id="8ba21-135">Defining Base Functionality</span></span>

<span data-ttu-id="8ba21-136">에 설명 된 대로 [디자인 해당 PS 공급자](./designing-your-windows-powershell-provider.md)서 [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 다른 공급자를 제공 하는 다른 여러 클래스에서 파생 되는 기본 클래스 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-136">As described in [Design Your PS Provider](./designing-your-windows-powershell-provider.md), the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) base class derives from several other classes that provided different provider functionality.</span></span> <span data-ttu-id="8ba21-137">Windows PowerShell 탐색 공급자, 따라서 정의 해야 모든 해당 클래스에서 제공 하는 기능.</span><span class="sxs-lookup"><span data-stu-id="8ba21-137">A Windows PowerShell navigation provider, therefore, must define all of the functionality provided by those classes.</span></span>

<span data-ttu-id="8ba21-138">특정 세션 초기화 정보를 추가 하 고 공급자가 사용 되는 리소스를 해제 하는 것에 대 한 기능을 구현 하려면 참조 [기본 PS 공급자 만들기](./creating-a-basic-windows-powershell-provider.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-138">To implement functionality for adding session-specific initialization information and for releasing resources that are used by the provider, see [Creating a Basic PS Provider](./creating-a-basic-windows-powershell-provider.md).</span></span> <span data-ttu-id="8ba21-139">그러나 여기에 설명 된 공급자 등 대부분의 공급자 기본적으로 Windows PowerShell에서 제공 하는이 기능을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-139">However, most providers (including the provider described here) can use the default implementation of this functionality provided by Windows PowerShell.</span></span>

<span data-ttu-id="8ba21-140">Windows PowerShell 드라이브를 통해 데이터 저장소에 액세스 하려면의 메서드를 구현 해야 합니다 [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) 기본 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-140">To get access to the data store through a Windows PowerShell drive, you must implement the methods of the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) base class.</span></span> <span data-ttu-id="8ba21-141">이러한 메서드를 구현 하는 방법에 대 한 자세한 내용은 참조 하세요. [Windows PowerShell 드라이브 공급자 만들기](./creating-a-windows-powershell-drive-provider.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-141">For more information about implementing these methods, see [Creating a Windows PowerShell Drive Provider](./creating-a-windows-powershell-drive-provider.md).</span></span>

<span data-ttu-id="8ba21-142">가져오기, 설정 및 지우기 항목을 같은 데이터 저장소의 항목을 조작 하는 공급자에서 제공 하는 메서드를 구현 해야 합니다는 [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) 기본 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-142">To manipulate the items of a data store, such as getting, setting, and clearing items, the provider must implement the methods provided by the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) base class.</span></span> <span data-ttu-id="8ba21-143">이러한 메서드를 구현 하는 방법에 대 한 자세한 내용은 참조 하세요. [Windows PowerShell 항목 공급자 만들기](./creating-a-windows-powershell-item-provider.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-143">For more information about implementing these methods, see [Creating an Windows PowerShell Item Provider](./creating-a-windows-powershell-item-provider.md).</span></span>

<span data-ttu-id="8ba21-144">자식 항목 또는 데이터 저장소 뿐만 아니라 만들기, 복사, 이름 바꾸기 및 항목을 제거 하는 메서드 이름을 제공한 메서드를 구현 해야 합니다 [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)기본 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-144">To get to the child items, or their names, of the data store, as well as methods that create, copy, rename, and remove items, you must implement the methods provided by the [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) base class.</span></span> <span data-ttu-id="8ba21-145">이러한 메서드를 구현 하는 방법에 대 한 자세한 내용은 참조 하세요. [Windows PowerShell 컨테이너 공급자 만들기](./creating-a-windows-powershell-container-provider.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-145">For more information about implementing these methods, see [Creating a Windows PowerShell Container Provider](./creating-a-windows-powershell-container-provider.md).</span></span>

## <a name="creating-a-windows-powershell-path"></a><span data-ttu-id="8ba21-146">Windows PowerShell 경로 만들기</span><span class="sxs-lookup"><span data-stu-id="8ba21-146">Creating a Windows PowerShell Path</span></span>

<span data-ttu-id="8ba21-147">Windows PowerShell 탐색 공급자에서는 공급자-내부 Windows PowerShell 경로 사용 하 여 데이터 저장소의 항목을 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-147">Windows PowerShell navigation provider use a provider-internal Windows PowerShell path to navigate the items of the data store.</span></span> <span data-ttu-id="8ba21-148">공급자 공급자-내부 경로 만들려면 구현 해야 합니다 [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) 결합-Path cmdlet에서 지원 메서드를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-148">To create a provider-internal path the provider must implement the [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) method to supports calls from the Combine-Path cmdlet.</span></span> <span data-ttu-id="8ba21-149">이 메서드는 부모 및 자식 경로 간의 공급자별 경로 구분 기호를 사용 하 여 내부 공급자 경로로 부모와 자식 경로 결합 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-149">This method combines a parent and child path into a provider-internal path, using a provider-specific path separator between the parent and child paths.</span></span>

<span data-ttu-id="8ba21-150">기본 구현에서는 사용 하 여 경로 "/" 또는 "\\""를 경로 구분 기호 정규화 경로 구분 기호로\\", 둘 사이의 구분 기호를 사용 하 여 부모 및 자식 경로 부분을 결합 및 다음 포함 된 문자열을 반환 합니다 결합 된 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-150">The default implementation takes paths with "/" or "\\" as the path separator, normalizes the path separator to "\\", combines the parent and child path parts with the separator between them, and then returns a string that contains the combined paths.</span></span>

<span data-ttu-id="8ba21-151">이 탐색 공급자는이 메서드를 구현 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-151">This navigation provider does not implement this method.</span></span> <span data-ttu-id="8ba21-152">그러나 다음 코드는 기본 구현의 합니다 [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) 메서드.</span><span class="sxs-lookup"><span data-stu-id="8ba21-152">However, the following code is the default implementation of the [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) method.</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermakepath](Msh_samplestestcmdlets#testprovidermakepath)]  -->

#### <a name="things-to-remember-about-implementing-makepath"></a><span data-ttu-id="8ba21-153">MakePath를 구현 하는 방법에 대 한 고려해 야 할 사항</span><span class="sxs-lookup"><span data-stu-id="8ba21-153">Things to Remember About Implementing MakePath</span></span>

<span data-ttu-id="8ba21-154">다음과의 구현에 적용 될 수 있습니다 [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath):</span><span class="sxs-lookup"><span data-stu-id="8ba21-154">The following conditions may apply to your implementation of [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath):</span></span>

- <span data-ttu-id="8ba21-155">구현의 합니다 [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) 메서드 공급자 네임 스페이스에 잘못 된 정규화 된 경로와 경로 확인 하지 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-155">Your implementation of the [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) method should not validate the path as a legal fully-qualified path in the provider namespace.</span></span> <span data-ttu-id="8ba21-156">각 매개 변수에 경로 부분을 나타낼 수 있습니다 하는 결합 된 부분 정규화 된 경로 생성 하지 않습니다 주의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-156">Be aware that each parameter can only represent a part of a path, and the combined parts might not generate a fully-qualified path.</span></span> <span data-ttu-id="8ba21-157">예를 들어 합니다 [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) 파일 시스템 공급자에 대 한 메서드는에서 "windows\system32" 나타날는 `parent` 매개 변수와 "abc.dll"에 `child` 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-157">For example, the [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) method for the filesystem provider might receive "windows\system32" in the `parent` parameter and "abc.dll" in the `child` parameter.</span></span> <span data-ttu-id="8ba21-158">이러한 값을 조인 하는 메서드는 "\\" 구분 기호 및 반환 "windows\system32\abc.dll"에 정규화 된 파일 시스템 경로가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-158">The method joins these values with the "\\" separator and returns "windows\system32\abc.dll", which is not a fully-qualified file system path.</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="8ba21-159">호출에서 제공 하는 경로 파트 [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) 공급자 네임 스페이스에서 사용할 수 없는 문자가 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-159">The path parts provided in the call to [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) might contain characters not allowed in the provider namespace.</span></span> <span data-ttu-id="8ba21-160">이러한 문자는 와일드 카드 확장에 대 한 대부분 사용 하 고이 메서드의 구현은 제거 하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-160">These characters are most likely used for wildcard expansion and the implementation of this method should not remove them.</span></span>

## <a name="retrieving-the-parent-path"></a><span data-ttu-id="8ba21-161">부모 경로 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-161">Retrieving the Parent Path</span></span>

<span data-ttu-id="8ba21-162">Windows PowerShell 탐색 공급자를 구현 합니다 [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) 상위 파트의 지정 된 전체 또는 일부를 검색 하는 방법 공급자 관련 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-162">Windows PowerShell navigation providers implement the [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) method to retrieve the parent part of the indicated full or partial provider-specific path.</span></span> <span data-ttu-id="8ba21-163">메서드는 경로의 하위 파트를 제거 하 고 부모 경로 부분을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-163">The method removes the child part of the path and returns the parent path part.</span></span> <span data-ttu-id="8ba21-164">`root` 매개 변수는 드라이브의 루트에 정규화 된 경로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-164">The `root` parameter specifies the fully-qualified path to the root of a drive.</span></span> <span data-ttu-id="8ba21-165">이 매개 변수는 null 이거나 탑재 된 드라이브 검색 작업에 대 한 사용에 없는 경우 비어 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-165">This parameter can be null or empty if a mounted drive is not in use for the retrieval operation.</span></span> <span data-ttu-id="8ba21-166">루트를 지정 하는 경우 메서드는 루트 동일한 트리에 있는 컨테이너에 경로 반환 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-166">If a root is specified, the method must return a path to a container in the same tree as the root.</span></span>

<span data-ttu-id="8ba21-167">샘플 탐색 공급자는이 메서드를 재정의 하지 않습니다 하지만 기본 구현을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-167">The sample navigation provider does not override this method, but uses the default implementation.</span></span> <span data-ttu-id="8ba21-168">함께 사용 하는 경로 받아들이는지 "/" 및 "\\" 경로 구분 기호로 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-168">It accepts paths that use both "/" and "\\" as path separators.</span></span> <span data-ttu-id="8ba21-169">만 있는 경로 정규화 먼저 "\\" 구분 기호를 마지막으로 오프 부모 경로 분할 "\\" 부모 경로 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-169">It first normalizes the path to have only "\\" separators, then splits the parent path off at the last "\\" and returns the parent path.</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetparentpath](Msh_samplestestcmdlets#testprovidergetparentpath)]  -->

#### <a name="to-remember-about-implementing-getparentpath"></a><span data-ttu-id="8ba21-170">GetParentPath를 구현 하는 방법에 대 한 기억 하기</span><span class="sxs-lookup"><span data-stu-id="8ba21-170">To Remember About Implementing GetParentPath</span></span>

<span data-ttu-id="8ba21-171">구현 된 [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) 메서드는 공급자 네임 스페이스에 대 한 경로 구분 기호에 어휘 적으로 경로 분할 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-171">Your implementation of the [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) method should split the path lexically on the path separator for the provider namespace.</span></span> <span data-ttu-id="8ba21-172">예를 들어, 파일 시스템 공급자가이 메서드를 사용 하 여 마지막 검색할 "\\" 구분 기호 왼쪽에 모든 항목을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-172">For example, the filesystem provider uses this method to look for the last "\\" and returns everything to the left of the separator.</span></span>

## <a name="retrieve-the-child-path-name"></a><span data-ttu-id="8ba21-173">자식 경로 이름을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-173">Retrieve the Child Path Name</span></span>

<span data-ttu-id="8ba21-174">공급자가 구현 하 여 탐색 합니다 [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) 표시 된 전체에 있는 항목의 자식 (리프 요소) 이름을 검색 하는 방법 또는 공급자별 경로 부분입니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-174">Your navigation provider implements the [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) method to retrieve the name (leaf element) of the child of the item located at the indicated full or partial provider-specific path.</span></span>

<span data-ttu-id="8ba21-175">샘플 탐색 공급자는이 메서드를 재정의 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-175">The sample navigation provider does not override this method.</span></span> <span data-ttu-id="8ba21-176">기본 구현은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-176">The default implementation is shown below.</span></span> <span data-ttu-id="8ba21-177">함께 사용 하는 경로 받아들이는지 "/" 및 "\\" 경로 구분 기호로 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-177">It accepts paths that use both "/" and "\\" as path separators.</span></span> <span data-ttu-id="8ba21-178">만 있는 경로 정규화 먼저 "\\" 구분 기호를 마지막으로 오프 부모 경로 분할 "\\" 자식 요소의 이름을 경로 부분을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-178">It first normalizes the path to have only "\\" separators, then splits the parent path off at the last "\\" and returns the name of the child path part.</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchildname](Msh_samplestestcmdlets#testprovidergetchildname)]  -->

#### <a name="things-to-remember-about-implementing-getchildname"></a><span data-ttu-id="8ba21-179">GetChildName를 구현 하는 방법에 대 한 고려해 야 할 사항</span><span class="sxs-lookup"><span data-stu-id="8ba21-179">Things to Remember About Implementing GetChildName</span></span>

<span data-ttu-id="8ba21-180">구현 된 [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) 메서드는 경로 구분 기호에 어휘 적으로 경로 분할 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-180">Your implementation of the [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) method should split the path lexically on the path separator.</span></span> <span data-ttu-id="8ba21-181">제공된 된 경로의 경로 구분 기호를 포함 하는 경우 메서드는 수정 되지 않은 경로 반환 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-181">If the supplied path contains no path separators, the method should return the path unmodified.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8ba21-182">이 메서드에 대 한 호출에서 제공한 경로 공급자 네임 스페이스에서 유효 하지 않은 문자를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-182">The path provided in the call to this method might contain characters that are illegal in the provider namespace.</span></span> <span data-ttu-id="8ba21-183">이러한 문자는 와일드 카드 확장 또는 정규식 일치에 사용 되는 가장 가능성이 높은 및이 메서드의 구현은 제거 하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-183">These characters are most likely used for wildcard expansion or regular expression matching, and the implementation of this method should not remove them.</span></span>

## <a name="determining-if-an-item-is-a-container"></a><span data-ttu-id="8ba21-184">항목 컨테이너 인지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-184">Determining if an Item is a Container</span></span>

<span data-ttu-id="8ba21-185">탐색 공급자를 구현할 수는 [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) 메서드를 지정된 된 경로 컨테이너를 가리키는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-185">The navigation provider can implement the [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) method to determine if the specified path indicates a container.</span></span> <span data-ttu-id="8ba21-186">경로 컨테이너 및 false 나타냅니다 그렇지 않은 경우 true를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-186">It returns true if the path represents a container, and false otherwise.</span></span> <span data-ttu-id="8ba21-187">사용자가이 메서드를 사용할 수는 `Test-Path` 제공 된 경로 대 한 cmdlet입니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-187">The user needs this method to be able to use the `Test-Path` cmdlet for the supplied path.</span></span>

<span data-ttu-id="8ba21-188">다음 코드에서는 합니다 [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) 샘플 탐색 공급자에서 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-188">The following code shows the [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) implementation in our sample navigation provider.</span></span> <span data-ttu-id="8ba21-189">메서드는 지정 된 경로가 올바른지와 테이블 존재 및 경로 컨테이너를 나타내면 true를 반환 하는 경우를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-189">The method verifies that  the specified path is correct and if the table exists, and returns true if the path indicates a container.</span></span>

[!code-csharp[AccessDBProviderSample05.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample05/AccessDBProviderSample05.cs#L847-L872 "AccessDBProviderSample05.cs")]

#### <a name="things-to-remember-about-implementing-isitemcontainer"></a><span data-ttu-id="8ba21-190">IsItemContainer를 구현 하는 방법에 대 한 고려해 야 할 사항</span><span class="sxs-lookup"><span data-stu-id="8ba21-190">Things to Remember About Implementing IsItemContainer</span></span>

<span data-ttu-id="8ba21-191">.NET 클래스 탐색 공급자에서 ExpandWildcards, 필터, 포함 또는 제외의 공급자 기능을 선언할 수 있습니다 합니다 [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) 열거형입니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-191">Your navigation provider .NET class might declare provider capabilities of ExpandWildcards, Filter, Include, or Exclude, from the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="8ba21-192">이 예에서 구현의 [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) 전달 경로 요구 사항을 충족 하는지 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-192">In this case, the implementation of [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) needs to ensure that the path passed meets requirements.</span></span> <span data-ttu-id="8ba21-193">이 작업을 수행 하는 메서드 액세스 해야 적절 한 속성을 예를 들어, [System.Management.Automation.Provider.Cmdletprovider.Exclude\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-193">To do this, the method should access the appropriate property, for example, the [System.Management.Automation.Provider.Cmdletprovider.Exclude\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) property.</span></span>

## <a name="moving-an-item"></a><span data-ttu-id="8ba21-194">항목 이동</span><span class="sxs-lookup"><span data-stu-id="8ba21-194">Moving an Item</span></span>

<span data-ttu-id="8ba21-195">지 원하는 합니다 `Move-Item` cmdlet을 탐색 공급자 구현 합니다 [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) 메서드.</span><span class="sxs-lookup"><span data-stu-id="8ba21-195">In support of the `Move-Item` cmdlet, your navigation provider implements the [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) method.</span></span> <span data-ttu-id="8ba21-196">로 지정한 항목을 이동 하는이 메서드는 `path` 컨테이너에 제공 된 경로에 매개 변수는 `destination` 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-196">This method moves the item specified by the `path` parameter to the container at the path supplied in the `destination` parameter.</span></span>

<span data-ttu-id="8ba21-197">샘플 탐색 공급자를 재정의 하지 않습니다 합니다 [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) 메서드.</span><span class="sxs-lookup"><span data-stu-id="8ba21-197">The sample navigation provider does not override the [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) method.</span></span> <span data-ttu-id="8ba21-198">다음은 기본 구현입니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-198">The following is the default implementation.</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermoveitem](Msh_samplestestcmdlets#testprovidermoveitem)]  -->

#### <a name="things-to-remember-about-implementing-moveitem"></a><span data-ttu-id="8ba21-199">MoveItem를 구현 하는 방법에 대 한 고려해 야 할 사항</span><span class="sxs-lookup"><span data-stu-id="8ba21-199">Things to Remember About Implementing MoveItem</span></span>

<span data-ttu-id="8ba21-200">.NET 클래스 탐색 공급자에서 ExpandWildcards, 필터, 포함 또는 제외의 공급자 기능을 선언할 수 있습니다 합니다 [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) 열거형입니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-200">Your navigation provider .NET class might declare provider capabilities of ExpandWildcards, Filter, Include, or Exclude, from the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="8ba21-201">이 예에서 구현의 [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) 전달 경로 요구 사항을 충족 하는지 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-201">In this case, the implementation of [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) must ensure that the path passed meets requirements.</span></span> <span data-ttu-id="8ba21-202">이 작업을 수행 하는 메서드 액세스 해야 적절 한 속성을 예를 들어, **CmdletProvider.Exclude** 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-202">To do this, the method should access the appropriate property, for example, the **CmdletProvider.Exclude** property.</span></span>

<span data-ttu-id="8ba21-203">기본적으로이 메서드는 재정의 이동 하지 않아야 개체 기존 개체에 대해 경우가 아니면 합니다 [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 속성이 `true`합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-203">By default, overrides of this method should not move objects over existing objects unless the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is set to `true`.</span></span> <span data-ttu-id="8ba21-204">예를 들어, 파일 시스템 공급자는 복사 하지 c:\temp\abc.txt 기존 c:\bar.txt 파일 경우가 아니면 합니다 [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 속성이 `true`합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-204">For example, the filesystem provider will not copy c:\temp\abc.txt over an existing c:\bar.txt file unless the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is set to `true`.</span></span> <span data-ttu-id="8ba21-205">경로에 지정 된 경우는 `destination` 매개 변수가 존재 하며 컨테이너에는 [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 속성이 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-205">If the path specified in the `destination` parameter exists and is a container, the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is not required.</span></span> <span data-ttu-id="8ba21-206">이 경우 [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) 가리키는 항목을 이동 해야 합니다 `path` 매개 변수는 컨테이너를 가리키는 `destination` 자식으로 매개 변수.</span><span class="sxs-lookup"><span data-stu-id="8ba21-206">In this case, [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) should move the item indicated by the `path` parameter to the container indicated by the `destination` parameter as a child.</span></span>

<span data-ttu-id="8ba21-207">구현 된 [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) 메서드를 호출 해야 [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 데이터 저장소로 변경 하기 전에 해당 반환 값을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-207">Your implementation of the [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) method should call [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) and check its return value before making any changes to the data store.</span></span> <span data-ttu-id="8ba21-208">이 메서드는 변경 될 때 시스템 상태를 예를 들어 파일을 삭제 하는 작업의 실행을 확인 하려면 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-208">This method is used to confirm execution of an operation when a change is made to system state, for example, deleting files.</span></span> <span data-ttu-id="8ba21-209">[System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 명령줄 설정이 나 기본 설정 변수에서 고려 Windows PowerShell 런타임에 사용자에 게 변경 될 리소스의 이름을 전송 사용자에 게 표시 되어야 할 사항을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-209">[System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) sends the name of the resource to be changed to the user, with the Windows PowerShell runtime taking into account any command line settings or preference variables in determining what should be displayed to the user.</span></span>

<span data-ttu-id="8ba21-210">호출한 후 [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 반환 `true`는 [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) 메서드를 호출 해야 합니다 [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) 메서드.</span><span class="sxs-lookup"><span data-stu-id="8ba21-210">After the call to [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) returns `true`, the [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) method should call the [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) method.</span></span> <span data-ttu-id="8ba21-211">이 메서드는 작업을 계속 해야 하는 경우에 피드백을 허용 하도록 사용자에 게 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-211">This method sends a message to the user to allow feedback to say if the operation should be continued.</span></span> <span data-ttu-id="8ba21-212">공급자를 호출 해야 [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) 잠재적으로 위험한 시스템 수정에 대 한 추가 검사 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-212">Your provider should call [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) as an additional check for potentially dangerous system modifications.</span></span>

## <a name="attaching-dynamic-parameters-to-the-move-item-cmdlet"></a><span data-ttu-id="8ba21-213">동적 연결 매개 변수를 Move-item Cmdlet</span><span class="sxs-lookup"><span data-stu-id="8ba21-213">Attaching Dynamic Parameters to the Move-Item Cmdlet</span></span>

<span data-ttu-id="8ba21-214">경우에 따라는 `Move-Item` cmdlet에는 런타임에 동적으로 제공 되는 추가 매개 변수가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-214">Sometimes the `Move-Item` cmdlet requires additional parameters that are provided dynamically at runtime.</span></span> <span data-ttu-id="8ba21-215">이러한 동적 매개 변수를 제공 하려면 탐색 공급자를 구현 해야 합니다 [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) 필수 매개 변수 값을 가져오는 방법 cmdlet 클래스와 유사한 특성에 속성과 필드를 구문 분석 하는 개체 돌아가 표시 된 경로에 있는 항목에서 또는 [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-215">To provide these dynamic parameters, the navigation provider must implement the [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) method to get the required parameter values from the item at the indicated path, and return an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span>

<span data-ttu-id="8ba21-216">이 탐색 공급자는이 메서드를 구현 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-216">This navigation provider does not implement this method.</span></span> <span data-ttu-id="8ba21-217">그러나 다음 코드는 기본 구현의 [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters)합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-217">However, the following code is the default implementation of [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters).</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermoveitemdynamicparameters](Msh_samplestestcmdlets#testprovidermoveitemdynamicparameters)]  -->

## <a name="normalizing-a-relative-path"></a><span data-ttu-id="8ba21-218">상대 경로 정규화합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-218">Normalizing a Relative Path</span></span>

<span data-ttu-id="8ba21-219">공급자가 구현 하 여 탐색 합니다 [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) 에 지정 된 정규화 된 경로 정규화 하는 메서드가 `path` 매개 변수 지정 된 경로 상대적인 것으로 `basePath` 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-219">Your navigation provider implements the [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) method to normalize the fully-qualified path indicated in the `path` parameter as being relative to the path specified by the `basePath` parameter.</span></span> <span data-ttu-id="8ba21-220">메서드는 정규화 된 경로 문자열 표현을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-220">The method returns a string representation of the normalized path.</span></span> <span data-ttu-id="8ba21-221">경우에 오류를 기록 합니다 `path` 매개 변수가 존재 하지 않는 경로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-221">It writes an error if the `path` parameter specifies a nonexistent path.</span></span>

<span data-ttu-id="8ba21-222">샘플 탐색 공급자는이 메서드를 재정의 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-222">The sample navigation provider does not override this method.</span></span> <span data-ttu-id="8ba21-223">다음은 기본 구현입니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-223">The following is the default implementation.</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernormalizepath](Msh_samplestestcmdlets#testprovidernormalizepath)]  -->

#### <a name="things-to-remember-about-implementing-normalizerelativepath"></a><span data-ttu-id="8ba21-224">NormalizeRelativePath를 구현 하는 방법에 대 한 고려해 야 할 사항</span><span class="sxs-lookup"><span data-stu-id="8ba21-224">Things to Remember About Implementing NormalizeRelativePath</span></span>

<span data-ttu-id="8ba21-225">구현의 [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) 구문 분석 되어야 합니다는 `path` 매개 변수 이지만 해당를 순수 하 게 구문 구문 분석을 사용 하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-225">Your implementation of [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) should parse the `path` parameter, but it does not have to use purely syntactical parsing.</span></span> <span data-ttu-id="8ba21-226">디자인 데이터 저장소의 경로 정보를 조회 하는 경로 만들 경로 사용 하도록이 메서드는 대/소문자와 일치 하는 것이 좋습니다 하 경로 구문 표준화 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-226">You are encouraged to design this method to use the path to look up the path information in the data store and create a path that matches the casing and standardized path syntax.</span></span>

## <a name="code-sample"></a><span data-ttu-id="8ba21-227">코드 예제</span><span class="sxs-lookup"><span data-stu-id="8ba21-227">Code Sample</span></span>

<span data-ttu-id="8ba21-228">전체 샘플 코드를 보려면 [AccessDbProviderSample05 코드 샘플](./accessdbprovidersample05-code-sample.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-228">For complete sample code, see [AccessDbProviderSample05 Code Sample](./accessdbprovidersample05-code-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="8ba21-229">개체 유형 정의 및 서식 지정</span><span class="sxs-lookup"><span data-stu-id="8ba21-229">Defining Object Types and Formatting</span></span>

<span data-ttu-id="8ba21-230">기존 개체에 멤버를 추가 하거나 새 개체를 정의 하는 공급자에 대 한 것 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-230">It is possible for a provider to add members to existing objects or define new objects.</span></span> <span data-ttu-id="8ba21-231">자세한 내용은[확장 개체 형식 및 서식](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-231">For more information, see[Extending Object Types and Formatting](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-windows-powershell-provider"></a><span data-ttu-id="8ba21-232">Windows PowerShell 공급자 작성</span><span class="sxs-lookup"><span data-stu-id="8ba21-232">Building the Windows PowerShell provider</span></span>

<span data-ttu-id="8ba21-233">자세한 내용은 [등록 Cmdlet, 공급자 및 응용 프로그램을 호스트 하는 방법을](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-233">For more information, see [How to Register Cmdlets, Providers, and Host Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-windows-powershell-provider"></a><span data-ttu-id="8ba21-234">Windows PowerShell 공급자 테스트</span><span class="sxs-lookup"><span data-stu-id="8ba21-234">Testing the Windows PowerShell provider</span></span>

<span data-ttu-id="8ba21-235">Windows PowerShell을 사용 하 여 Windows PowerShell 공급자가 등록 하는 경우에 파생에서 사용할 수 있는 cmdlet을 포함 하 여 명령줄에서 지원 되는 cmdlet을 실행 하 여 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-235">When your Windows PowerShell provider has been registered with Windows PowerShell, you can test it by running the supported cmdlets on the command line, including cmdlets made available by derivation.</span></span> <span data-ttu-id="8ba21-236">이 예제에서는 샘플 탐색 공급자를 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-236">This example will test the sample navigation provider.</span></span>

1. <span data-ttu-id="8ba21-237">새 셸을 실행 하 고 사용 된 `Set-Location` Access 데이터베이스를 가리키는 경로 설정 하는 cmdlet입니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-237">Run your new shell and use the `Set-Location` cmdlet to set the path to indicate the Access database.</span></span>

   ```powershell
   Set-Location mydb:
   ```

2. <span data-ttu-id="8ba21-238">이제 실행을 `Get-Childitem` cmdlet을 사용할 수 있는 데이터베이스 테이블에는 데이터베이스 항목의 목록을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-238">Now run the `Get-Childitem` cmdlet to retrieve a list of the database items, which are the available database tables.</span></span> <span data-ttu-id="8ba21-239">각 테이블에 대해이 cmdlet도 테이블 행의 수를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-239">For each table, this cmdlet also retrieves the number of table rows.</span></span>

   ```powershell
   Get-ChildItem | Format-Table rowcount,name -AutoSize
   ```

   ```output
   RowCount   Name
   --------   ----
        180   MSysAccessObjects
          0   MSysACEs
          1   MSysCmdbars
          0   MSysIMEXColumns
          0   MSysIMEXSpecs
          0   MSysObjects
          0   MSysQueries
          7   MSysRelationships
          8   Categories
         91   Customers
          9   Employees
       2155   Order Details
        830   Orders
         77   Products
          3   Shippers
         29   Suppliers
   ```

3. <span data-ttu-id="8ba21-240">사용 된 `Set-Location` 직원 데이터 테이블의 위치를 설정 하려면 다시 cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8ba21-240">Use the `Set-Location` cmdlet again to set the location of the Employees data table.</span></span>

   ```powershell
   Set-Location Employees
   ```

4. <span data-ttu-id="8ba21-241">이제 사용해 보겠습니다는 `Get-Location` Employees 테이블에 경로 검색 하는 cmdlet입니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-241">Let's now use the `Get-Location` cmdlet to retrieve the path to the Employees table.</span></span>

   ```powershell
   Get-Location
   ```

   ```output
   Path
   ----
   mydb:\Employees
   ```

5. <span data-ttu-id="8ba21-242">이제 사용 합니다 `Get-Childitem` cmdlet으로 파이프 합니다 `Format-Table` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8ba21-242">Now use the `Get-Childitem` cmdlet piped to the `Format-Table` cmdlet.</span></span> <span data-ttu-id="8ba21-243">Cmdlet이이 집합이 테이블 행에는 직원 데이터 테이블에 대 한 항목을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-243">This set of cmdlets retrieves the items for the Employees data table, which are the table rows.</span></span> <span data-ttu-id="8ba21-244">형식이 지정 될 지정 된 대로 `Format-Table` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8ba21-244">They are formatted as specified by the `Format-Table` cmdlet.</span></span>

   ```powershell
   Get-ChildItem | Format-Table rownumber,psiscontainer,data -AutoSize
   ```

   ```output
   RowNumber   PSIsContainer   Data
   ---------   --------------   ----
   0           False            System.Data.DataRow
   1           False            System.Data.DataRow
   2           False            System.Data.DataRow
   3           False            System.Data.DataRow
   4           False            System.Data.DataRow
   5           False            System.Data.DataRow
   6           False            System.Data.DataRow
   7           False            System.Data.DataRow
   8           False            System.Data.DataRow
   ```

6. <span data-ttu-id="8ba21-245">이제 실행할 수 있습니다는 `Get-Item` 직원 데이터 테이블의 행 0에 대 한 항목을 검색 하기 위한 cmdlet입니다.</span><span class="sxs-lookup"><span data-stu-id="8ba21-245">You can now run the `Get-Item` cmdlet to retrieve the items for row 0 of the Employees data table.</span></span>

   ```powershell
   Get-Item 0
   ```

   ```output
   PSPath        : AccessDB::C:\PS\Northwind.mdb\Employees\0
   PSParentPath  : AccessDB::C:\PS\Northwind.mdb\Employees
   PSChildName   : 0
   PSDrive       : mydb
   PSProvider    : System.Management.Automation.ProviderInfo
   PSIsContainer : False
   Data           : System.Data.DataRow
   RowNumber      : 0
   ```

7. <span data-ttu-id="8ba21-246">사용 된 `Get-Item` 행 0에에서 있는 항목에 대 한 직원 데이터를 검색 하기 위한 다시 cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8ba21-246">Use the `Get-Item` cmdlet again to retrieve the employee data for the items in row 0.</span></span>

   ```powershell
   (Get-Item 0).data
   ```

   ```output
   EmployeeID      : 1
   LastName        : Davis
   FirstName       : Sara
   Title           : Sales Representative
   TitleOfCourtesy : Ms.
   BirthDate       : 12/8/1968 12:00:00 AM
   HireDate        : 5/1/1992 12:00:00 AM
   Address         : 4567 Main Street
                     Apt. 2A
   City            : Buffalo
   Region          : NY
   PostalCode      : 98052
   Country         : USA
   HomePhone       : (206) 555-9857
   Extension       : 5467
   Photo           : EmpID1.bmp
   Notes           : Education includes a BA in psychology from
                     Colorado State University. She also completed "The
                     Art of the Cold Call."  Nancy is a member of
                     Toastmasters International.
   ReportsTo       : 2
   ```

## <a name="see-also"></a><span data-ttu-id="8ba21-247">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8ba21-247">See Also</span></span>

[<span data-ttu-id="8ba21-248">Windows PowerShell 공급자 만들기</span><span class="sxs-lookup"><span data-stu-id="8ba21-248">Creating Windows PowerShell providers</span></span>](./how-to-create-a-windows-powershell-provider.md)

[<span data-ttu-id="8ba21-249">디자인 Your Windows PowerShell 공급자</span><span class="sxs-lookup"><span data-stu-id="8ba21-249">Design Your Windows PowerShell provider</span></span>](./designing-your-windows-powershell-provider.md)

[<span data-ttu-id="8ba21-250">확장 개체 형식 및 서식 지정</span><span class="sxs-lookup"><span data-stu-id="8ba21-250">Extending Object Types and Formatting</span></span>](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="8ba21-251">Windows PowerShell 컨테이너 공급자 구현</span><span class="sxs-lookup"><span data-stu-id="8ba21-251">Implement a Container Windows PowerShell provider</span></span>](./creating-a-windows-powershell-container-provider.md)

[<span data-ttu-id="8ba21-252">Cmdlet, 공급자, 등록 및 응용 프로그램을 호스트 하는 방법</span><span class="sxs-lookup"><span data-stu-id="8ba21-252">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="8ba21-253">Windows PowerShell 프로그래머 가이드</span><span class="sxs-lookup"><span data-stu-id="8ba21-253">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="8ba21-254">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="8ba21-254">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)