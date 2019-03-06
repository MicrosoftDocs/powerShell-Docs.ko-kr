---
title: Windows PowerShell 콘텐츠 공급자 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- content providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], content provider
ms.assetid: 3da88ff9-c4c7-4ace-aa24-0a29c8cfa060
caps.latest.revision: 6
ms.openlocfilehash: 5e35d2fdfa4c6bd70c1b69ca1f357ee8d8ebcdc4
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429978"
---
# <a name="creating-a-windows-powershell-content-provider"></a><span data-ttu-id="16b7d-102">Windows PowerShell 콘텐츠 공급자 만들기</span><span class="sxs-lookup"><span data-stu-id="16b7d-102">Creating a Windows PowerShell Content Provider</span></span>

<span data-ttu-id="16b7d-103">이 항목에서는 데이터 저장소에 있는 항목의 내용을 조작할 수 있도록 해 주는 Windows PowerShell 공급자를 만드는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-103">This topic describes how to create a Windows PowerShell provider that enables the user to manipulate the contents of the items in a data store.</span></span> <span data-ttu-id="16b7d-104">결과적으로 항목의 내용을 조작할 수 있는 공급자는 Windows PowerShell 콘텐츠 공급자로 하 라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-104">As a consequence, a provider that can manipulate the contents of items is referred to as a Windows PowerShell content provider.</span></span>

> [!NOTE]
> <span data-ttu-id="16b7d-105">다운로드할 수 있습니다는 C# Microsoft Windows 소프트웨어 개발 키트에 대 한 Windows Vista 및.NET Framework 3.0 런타임 구성 요소를 사용 하 여이 공급자에 대 한 원본 파일 (AccessDBSampleProvider06.cs).</span><span class="sxs-lookup"><span data-stu-id="16b7d-105">You can download the C# source file (AccessDBSampleProvider06.cs) for this provider using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="16b7d-106">다운로드 지침에 대해서 [Windows PowerShell 설치 및 Windows PowerShell SDK를 다운로드 하는 방법을](/powershell/developer/installing-the-windows-powershell-sdk)합니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="16b7d-107">다운로드 한 소스 파일에서 사용할 수는  **\<PowerShell 샘플 >** 디렉터리입니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>
>
> <span data-ttu-id="16b7d-108">다른 Windows PowerShell 공급자 구현에 대 한 자세한 내용은 참조 하십시오 [Your Windows PowerShell 공급자 디자인](./designing-your-windows-powershell-provider.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-108">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

<span data-ttu-id="16b7d-109">다음은이 항목의 섹션을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-109">The following list contains the sections in this topic.</span></span> <span data-ttu-id="16b7d-110">Windows PowerShell 콘텐츠 공급자 쓰기와 잘 모르는 경우 표시 되는 순서 대로 다음이 섹션을 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-110">If you are unfamiliar with writing a Windows PowerShell content provider, read these sections in the order that they appear.</span></span> <span data-ttu-id="16b7d-111">그러나 Windows PowerShell 콘텐츠 공급자 작성에 익숙한 경우 다음과 같이 해야 하는 정보에 직접 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-111">However, if you are familiar with writing a Windows PowerShell content provider, go directly to the information that you need.</span></span>

- [<span data-ttu-id="16b7d-112">Windows PowerShell 콘텐츠 공급자 클래스를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-112">Defining the Windows PowerShell Content Provider Class</span></span>](#Define-the-Windows-PowerShell-Content-Provider-Class)

- [<span data-ttu-id="16b7d-113">기본 기능 정의</span><span class="sxs-lookup"><span data-stu-id="16b7d-113">Defining Base Functionality</span></span>](#Define-Functionality-of-Base-Class)

- [<span data-ttu-id="16b7d-114">콘텐츠 판독기 구현</span><span class="sxs-lookup"><span data-stu-id="16b7d-114">Implementing a Content Reader</span></span>](#Implementing-a-Content-Reader)

- [<span data-ttu-id="16b7d-115">콘텐츠 작성자를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-115">Implementing a Content Writer</span></span>](#Implementing-a-Content-Writer)

- [<span data-ttu-id="16b7d-116">콘텐츠 판독기를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-116">Retrieving the Content Reader</span></span>](#Retrieving-the-Content-Reader)

- [<span data-ttu-id="16b7d-117">동적 매개 변수를 연결 합니다 `Get-Content` Cmdlet</span><span class="sxs-lookup"><span data-stu-id="16b7d-117">Attaching Dynamic Parameters to the `Get-Content` Cmdlet</span></span>](#Attaching-Dynamic-Parameters-to-the-Get-Content-Cmdlet)

- [<span data-ttu-id="16b7d-118">콘텐츠 작성기를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-118">Retrieving the Content Writer</span></span>](#Retrieving-the-Content-Writer)

- [<span data-ttu-id="16b7d-119">동적 매개 변수는 Add_Content 연결할 및 `Set-Content` Cmdlet</span><span class="sxs-lookup"><span data-stu-id="16b7d-119">Attaching Dynamic Parameters to the Add_Content and `Set-Content` Cmdlets</span></span>](#Attaching-Dynamic-Parameters-to-the-Add-Content-and-Set-Content-Cmdlets)

- [<span data-ttu-id="16b7d-120">콘텐츠 지우기</span><span class="sxs-lookup"><span data-stu-id="16b7d-120">Clearing Content</span></span>](#Clearing-Content)

- [<span data-ttu-id="16b7d-121">동적 매개 변수를 연결 합니다 `Clear-Content` Cmdlet</span><span class="sxs-lookup"><span data-stu-id="16b7d-121">Attaching Dynamic Parameters to the  `Clear-Content` Cmdlet</span></span>](#Attaching-Dynamic-Parameters-to-the-Clear-Content-Cmdlet)

- [<span data-ttu-id="16b7d-122">코드 샘플</span><span class="sxs-lookup"><span data-stu-id="16b7d-122">Code Sample</span></span>](#Code-Sample)

- [<span data-ttu-id="16b7d-123">개체 유형 정의 및 서식 지정</span><span class="sxs-lookup"><span data-stu-id="16b7d-123">Defining Object Types and Formatting</span></span>]()

- [<span data-ttu-id="16b7d-124">Windows PowerShell 공급자 작성</span><span class="sxs-lookup"><span data-stu-id="16b7d-124">Building the Windows PowerShell provider</span></span>](#Building-the-Windows-PowerShell-Provider)

- [<span data-ttu-id="16b7d-125">Windows PowerShell 공급자 테스트</span><span class="sxs-lookup"><span data-stu-id="16b7d-125">Testing the Windows PowerShell provider</span></span>](#Testing-the-Windows-PowerShell-Provider)

## <a name="define-the-windows-powershell-content-provider-class"></a><span data-ttu-id="16b7d-126">Windows PowerShell 콘텐츠 공급자 클래스를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-126">Define the Windows PowerShell Content Provider Class</span></span>

<span data-ttu-id="16b7d-127">Windows PowerShell 콘텐츠 공급자를 지 원하는.NET 클래스를 만들어야 합니다 [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) 인터페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-127">A Windows PowerShell content provider must create a .NET class that supports the [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface.</span></span> <span data-ttu-id="16b7d-128">이 섹션에 설명 된 항목 공급자에 대 한 클래스 정의 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-128">Here is the class definition for the item provider described in this section.</span></span>

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L32-L33 "AccessDBProviderSample06.cs")]

<span data-ttu-id="16b7d-129">이 클래스를 정의 하는 합니다 [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) 특성에는 두 개의 매개 변수가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-129">Note that in this class definition, the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attribute includes two parameters.</span></span> <span data-ttu-id="16b7d-130">첫 번째 매개 변수는 Windows PowerShell에서 사용 되는 공급자에 대 한 알기 쉬운 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-130">The first parameter specifies a user-friendly name for the provider that is used by Windows PowerShell.</span></span> <span data-ttu-id="16b7d-131">두 번째 매개 변수는 명령 처리 하는 동안 공급자가 Windows PowerShell 런타임에 노출 하는 Windows PowerShell 특정 기능을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-131">The second parameter specifies the Windows PowerShell specific capabilities that the provider exposes to the Windows PowerShell runtime during command processing.</span></span> <span data-ttu-id="16b7d-132">이 공급자에 대 한 추가 Windows PowerShell 특정 기능이 없으며 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-132">For this provider, there are no added Windows PowerShell specific capabilities.</span></span>

## <a name="define-functionality-of-base-class"></a><span data-ttu-id="16b7d-133">기본 클래스의 기능 정의</span><span class="sxs-lookup"><span data-stu-id="16b7d-133">Define Functionality of Base Class</span></span>

<span data-ttu-id="16b7d-134">에 설명 된 대로 [디자인 해당 Windows PowerShell 공급자](./designing-your-windows-powershell-provider.md)서 [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 제공 하는 다른 여러 클래스에서 파생 되는 클래스 다른 공급자 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-134">As described in [Design Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md), the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class derives from several other classes that provided different provider functionality.</span></span> <span data-ttu-id="16b7d-135">Windows PowerShell 콘텐츠 공급자, 따라서 일반적으로 모든 정의 해당 클래스에서 제공 하는 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-135">A Windows PowerShell content provider, therefore, typically defines all of the functionality provided by those classes.</span></span>

<span data-ttu-id="16b7d-136">특정 세션 초기화 정보를 추가 하 고 공급자가 사용 되는 리소스를 해제 하는 것에 대 한 기능을 구현 하는 방법에 대 한 자세한 내용은 참조 하세요. [는 기본 Windows PowerShell 공급자를 만들어](./creating-a-basic-windows-powershell-provider.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-136">For more information about how to implement functionality for adding session-specific initialization information and for releasing resources that are used by the provider, see [Creating a Basic Windows PowerShell Provider](./creating-a-basic-windows-powershell-provider.md).</span></span> <span data-ttu-id="16b7d-137">그러나 여기에 설명 된 공급자를 비롯 한 대부분의 공급자를 Windows PowerShell에서 제공 하는이 기능의 기본 구현을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-137">However, most providers, including the provider described here, can use the default implementation of this functionality that is provided by Windows PowerShell.</span></span>

<span data-ttu-id="16b7d-138">데이터 저장소에 액세스 하려면 공급자의 메서드를 구현 해야 합니다 [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) 기본 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-138">To access the data store, the provider must implement the methods of the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) base class.</span></span> <span data-ttu-id="16b7d-139">이러한 메서드를 구현 하는 방법에 대 한 자세한 내용은 참조 하세요. [Windows PowerShell 드라이브 공급자 만들기](./creating-a-windows-powershell-drive-provider.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-139">For more information about implementing these methods, see [Creating a Windows PowerShell Drive Provider](./creating-a-windows-powershell-drive-provider.md).</span></span>

<span data-ttu-id="16b7d-140">가져오기, 설정 및 지우기 항목을 같은 데이터 저장소의 항목을 조작 하는 공급자에서 제공 하는 메서드를 구현 해야 합니다는 [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) 기본 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-140">To manipulate the items of a data store, such as getting, setting, and clearing items, the provider must implement the methods provided by the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) base class.</span></span> <span data-ttu-id="16b7d-141">이러한 메서드를 구현 하는 방법에 대 한 자세한 내용은 참조 하세요. [Windows PowerShell 항목 공급자 만들기](./creating-a-windows-powershell-item-provider.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-141">For more information about implementing these methods, see [Creating a Windows PowerShell Item Provider](./creating-a-windows-powershell-item-provider.md).</span></span>

<span data-ttu-id="16b7d-142">다중 계층 데이터 저장소에서 작업 하려면, 공급자에서 제공 하는 메서드를 구현 해야 합니다 [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) 기본 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-142">To work on multi-layer data stores, the provider must implement the methods provided by the [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) base class.</span></span> <span data-ttu-id="16b7d-143">이러한 메서드를 구현 하는 방법에 대 한 자세한 내용은 참조 하세요. [Windows PowerShell 컨테이너 공급자 만들기](./creating-a-windows-powershell-container-provider.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-143">For more information about implementing these methods, see [Creating a Windows PowerShell Container Provider](./creating-a-windows-powershell-container-provider.md).</span></span>

<span data-ttu-id="16b7d-144">재귀적 명령, 중첩 된 컨테이너 및 상대 경로 지원 하려면 공급자를 구현 해야 합니다 [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 기본 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-144">To support recursive commands, nested containers, and relative paths, the provider must implement the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) base class.</span></span> <span data-ttu-id="16b7d-145">이 Windows PowerShell 콘텐츠 공급자의 연결 수 뿐만 [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) 인터페이스는 [ System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 기본 클래스 및 해당 클래스에서 제공 하는 메서드를 구현 하므로 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-145">In addition, this Windows PowerShell content provider can attaches [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface to the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) base class, and must therefore implement the methods provided by that class.</span></span> <span data-ttu-id="16b7d-146">자세한 내용은 해당 메서드를 구현 참조 하십시오 [탐색 Windows PowerShell 공급자를 구현](./creating-a-windows-powershell-navigation-provider.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-146">For more information, see implementing those methods, see [Implement a Navigation Windows PowerShell Provider](./creating-a-windows-powershell-navigation-provider.md).</span></span>

## <a name="implementing-a-content-reader"></a><span data-ttu-id="16b7d-147">콘텐츠 판독기 구현</span><span class="sxs-lookup"><span data-stu-id="16b7d-147">Implementing a Content Reader</span></span>

<span data-ttu-id="16b7d-148">항목에서 콘텐츠를 읽으려면 공급자에서 파생 되는 콘텐츠 판독기 클래스를 구현 해야 합니다 [System.Management.Automation.Provider.Icontentreader](/dotnet/api/System.Management.Automation.Provider.IContentReader)합니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-148">To read content from an item, a provider must implements a content reader class that derives from [System.Management.Automation.Provider.Icontentreader](/dotnet/api/System.Management.Automation.Provider.IContentReader).</span></span> <span data-ttu-id="16b7d-149">이 공급자에 대 한 콘텐츠 판독기에는 데이터 테이블의 행의 내용에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-149">The content reader for this provider allows access to the contents of a row in a data table.</span></span> <span data-ttu-id="16b7d-150">콘텐츠 판독기 클래스 정의 **읽기** 표시 된 행에서 데이터를 검색 하 고 해당 데이터를 나타내는 목록을 반환 하는 메서드를 **Seek** 콘텐츠 판독기를 이동 하는 메서드는  **닫기** 콘텐츠는 판독기가 닫히고 하는 메서드 및 **Dispose** 메서드.</span><span class="sxs-lookup"><span data-stu-id="16b7d-150">The content reader class defines a **Read** method that retrieves the data from the indicated row and returns a list representing that data, a **Seek** method that moves the content reader, a **Close** method that closes the content reader, and a **Dispose** method.</span></span>

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L2115-L2241 "AccessDBProviderSample06.cs")]

## <a name="implementing-a-content-writer"></a><span data-ttu-id="16b7d-151">콘텐츠 작성자를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-151">Implementing a Content Writer</span></span>

<span data-ttu-id="16b7d-152">공급자를 항목에 콘텐츠를 쓸 콘텐츠를 구현 해야 작성기 클래스에서 파생 되며 [System.Management.Automation.Provider.Icontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter)합니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-152">To write content to an item, a provider must implement a content writer class derives from [System.Management.Automation.Provider.Icontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter).</span></span> <span data-ttu-id="16b7d-153">콘텐츠 작성기 클래스를 정의 **작성** 지정 된 행 콘텐츠를 기록 하는 메서드를 **Seek** 작성기에 해당 콘텐츠를 이동 하는 메서드를 **닫기** 닫는 메서드를 콘텐츠 작성자와 **Dispose** 메서드.</span><span class="sxs-lookup"><span data-stu-id="16b7d-153">The content writer class defines a **Write** method that writes the specified row content, a **Seek** method that moves the content writer, a **Close** method that closes the content writer, and a **Dispose** method.</span></span>

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L2250-L2394 "AccessDBProviderSample06.cs")]

## <a name="retrieving-the-content-reader"></a><span data-ttu-id="16b7d-154">콘텐츠 판독기를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-154">Retrieving the Content Reader</span></span>

<span data-ttu-id="16b7d-155">를 활용 하려면 콘텐츠 항목 공급자를 구현 해야 합니다 [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) 지원 하기 위해는 `Get-Content` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="16b7d-155">To get content from an item, the provider must implement the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) to support the `Get-Content` cmdlet.</span></span> <span data-ttu-id="16b7d-156">이 메서드는 지정된 된 경로에 있는 항목에 대 한 콘텐츠 판독기를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-156">This method returns the content reader for the item located at the specified path.</span></span> <span data-ttu-id="16b7d-157">판독기 개체는 다음 콘텐츠를 읽기 위해 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-157">The reader object can then be opened to read the content.</span></span>

<span data-ttu-id="16b7d-158">여기의 구현인 [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) 이 공급자에 대 한이 메서드에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-158">Here is the implementation of [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) for this method for this provider.</span></span>

```csharp
public IContentReader GetContentReader(string path)
{
    string tableName;
    int rowNumber;

    PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

    if (type == PathType.Invalid)
    {
        ThrowTerminatingInvalidPathException(path);
    }
    else if (type == PathType.Row)
    {
        throw new InvalidOperationException("contents can be obtained only for tables");
    }

    return new AccessDBContentReader(path, this);
} // GetContentReader
```

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1829-L1846 "AccessDBProviderSample06.cs")]

#### <a name="things-to-remember-about-implementing-getcontentreader"></a><span data-ttu-id="16b7d-159">GetContentReader를 구현 하는 방법에 대 한 고려해 야 할 사항</span><span class="sxs-lookup"><span data-stu-id="16b7d-159">Things to Remember About Implementing GetContentReader</span></span>

<span data-ttu-id="16b7d-160">다음과의 구현에 적용 될 수 있습니다 [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader):</span><span class="sxs-lookup"><span data-stu-id="16b7d-160">The following conditions may apply to an implementation of [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader):</span></span>

- <span data-ttu-id="16b7d-161">공급자 클래스를 정의 하는 경우 Windows PowerShell 콘텐츠 공급자에서 ExpandWildcards, 필터, 포함 또는 제외의 공급자 기능을 선언할 수 있습니다는 [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)열거형입니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-161">When defining the provider class, a Windows PowerShell content provider might declare provider capabilities of ExpandWildcards, Filter, Include, or Exclude, from the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="16b7d-162">이러한 경우의 구현에는 [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) 메서드는 메서드에 전달 된 경로 지정 된 요구 사항을 충족 하는지 확인 해야 합니다 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-162">In these cases, the implementation of the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) method must ensure that the path passed to the method meets the requirements of the specified capabilities.</span></span> <span data-ttu-id="16b7d-163">이 작업을 수행 하는 메서드 액세스 해야 적절 한 속성을 예를 들어, [System.Management.Automation.Provider.Cmdletprovider.Exclude\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) 고 [ System.Management.Automation.Provider.Cmdletprovider.Include\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-163">To do this, the method should access the appropriate property, for example, the [System.Management.Automation.Provider.Cmdletprovider.Exclude\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) and [System.Management.Automation.Provider.Cmdletprovider.Include\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) properties.</span></span>

- <span data-ttu-id="16b7d-164">기본적으로이 메서드는 재정의 하지 않는 한 사용자 로부터 숨겨진 개체에 대 한 판독기를 검색 하지 않아야 합니다 [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 속성이 `true`합니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-164">By default, overrides of this method should not retrieve a reader for objects that are hidden from the user unless the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is set to `true`.</span></span> <span data-ttu-id="16b7d-165">경로 사용자 로부터 숨겨진 항목을 나타내는 경우 오류를 작성 해야 하 고 [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 로 설정 된 `false`합니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-165">An error should be written if the path represents an item that is hidden from the user and [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) is set to `false`.</span></span>

## <a name="attaching-dynamic-parameters-to-the-get-content-cmdlet"></a><span data-ttu-id="16b7d-166">Get-content Cmdlet에 연결 하는 동적 매개 변수</span><span class="sxs-lookup"><span data-stu-id="16b7d-166">Attaching Dynamic Parameters to the Get-Content Cmdlet</span></span>

<span data-ttu-id="16b7d-167">`Get-Content` cmdlet 런타임에 동적으로 지정 된 추가 매개 변수가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-167">The `Get-Content` cmdlet might require additional parameters that are specified dynamically at runtime.</span></span> <span data-ttu-id="16b7d-168">이러한 동적 매개 변수를 제공 하려면 Windows PowerShell 콘텐츠 공급자를 구현 해야 합니다 [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreaderdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) 메서드.</span><span class="sxs-lookup"><span data-stu-id="16b7d-168">To provide these dynamic parameters, the Windows PowerShell content provider must implement the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreaderdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) method.</span></span> <span data-ttu-id="16b7d-169">이 메서드는 지정 된 경로에 있는 항목에 대 한 동적 매개 변수를 검색 하 고 속성 및 cmdlet 클래스와 유사한 특성을 구문 분석 된 필드에 있는 개체를 반환 또는 [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-169">This method retrieves dynamic parameters for the item at the indicated path and returns an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span> <span data-ttu-id="16b7d-170">Windows PowerShell 런타임이 cmdlet에 매개 변수를 추가할 반환된 된 개체를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-170">The Windows PowerShell runtime uses the returned object to add the parameters to the cmdlet.</span></span>

<span data-ttu-id="16b7d-171">이 Windows PowerShell 컨테이너 공급자는이 메서드를 구현 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-171">This Windows PowerShell container provider does not implement this method.</span></span> <span data-ttu-id="16b7d-172">그러나 다음 코드는이 메서드의 기본 구현입니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-172">However, the following code is the default implementation of this method.</span></span>

```csharp
public object GetContentReaderDynamicParameters(string path)
{
    return null;
}
```

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1853-L1856 "AccessDBProviderSample06.cs")]

## <a name="retrieving-the-content-writer"></a><span data-ttu-id="16b7d-173">콘텐츠 작성기를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-173">Retrieving the Content Writer</span></span>

<span data-ttu-id="16b7d-174">항목에 콘텐츠를 작성 하려면 공급자를 구현 해야 합니다 [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) 지원 하기 위해는 `Set-Content` 및 `Add-Content` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="16b7d-174">To write content to an item, the provider must implement the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) to support the `Set-Content` and `Add-Content` cmdlets.</span></span> <span data-ttu-id="16b7d-175">이 메서드는 지정된 된 경로에 있는 항목에 대 한 콘텐츠 작성기를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-175">This method returns the content writer for the item located at the specified path.</span></span>

<span data-ttu-id="16b7d-176">여기의 구현인 [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) 이 메서드에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-176">Here is the implementation of [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) for this method.</span></span>

```csharp
public IContentWriter GetContentWriter(string path)
{
    string tableName;
    int rowNumber;

    PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

    if (type == PathType.Invalid)
    {
        ThrowTerminatingInvalidPathException(path);
    }
    else if (type == PathType.Row)
    {
        throw new InvalidOperationException("contents can be added only to tables");
    }

    return new AccessDBContentWriter(path, this);
}
```

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1863-L1880 "AccessDBProviderSample06.cs")]

#### <a name="things-to-remember-about-implementing-getcontentwriter"></a><span data-ttu-id="16b7d-177">GetContentWriter를 구현 하는 방법에 대 한 고려해 야 할 사항</span><span class="sxs-lookup"><span data-stu-id="16b7d-177">Things to Remember About Implementing GetContentWriter</span></span>

<span data-ttu-id="16b7d-178">다음과의 구현에 적용 될 수 있습니다 [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter):</span><span class="sxs-lookup"><span data-stu-id="16b7d-178">The following conditions may apply to your implementation of [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter):</span></span>

- <span data-ttu-id="16b7d-179">공급자 클래스를 정의 하는 경우 Windows PowerShell 콘텐츠 공급자에서 ExpandWildcards, 필터, 포함 또는 제외의 공급자 기능을 선언할 수 있습니다는 [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)열거형입니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-179">When defining the provider class, a Windows PowerShell content provider might declare provider capabilities of ExpandWildcards, Filter, Include, or Exclude, from the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="16b7d-180">이러한 경우의 구현에는 [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) 메서드는 메서드에 전달 된 경로 지정 된 요구 사항을 충족 하는지 확인 해야 합니다 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-180">In these cases, the implementation of the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) method must ensure that the path passed to the method meets the requirements of the specified capabilities.</span></span> <span data-ttu-id="16b7d-181">이 작업을 수행 하는 메서드 액세스 해야 적절 한 속성을 예를 들어, [System.Management.Automation.Provider.Cmdletprovider.Exclude\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) 고 [ System.Management.Automation.Provider.Cmdletprovider.Include\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-181">To do this, the method should access the appropriate property, for example, the [System.Management.Automation.Provider.Cmdletprovider.Exclude\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) and [System.Management.Automation.Provider.Cmdletprovider.Include\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) properties.</span></span>

- <span data-ttu-id="16b7d-182">기본적으로이 메서드는 재정의 하지 않는 한 사용자 로부터 숨겨진 개체에 대 한 작성기를 검색 하지 않아야 합니다 [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 속성이 `true`합니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-182">By default, overrides of this method should not retrieve a writer for objects that are hidden from the user unless the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is set to `true`.</span></span> <span data-ttu-id="16b7d-183">경로 사용자 로부터 숨겨진 항목을 나타내는 경우 오류를 작성 해야 하 고 [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 로 설정 된 `false`합니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-183">An error should be written if the path represents an item that is hidden from the user and [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) is set to `false`.</span></span>

## <a name="attaching-dynamic-parameters-to-the-add-content-and-set-content-cmdlets"></a><span data-ttu-id="16b7d-184">동적 매개 변수를 Add-content 및 Set-content Cmdlet에 연결</span><span class="sxs-lookup"><span data-stu-id="16b7d-184">Attaching Dynamic Parameters to the Add-Content and Set-Content Cmdlets</span></span>

<span data-ttu-id="16b7d-185">합니다 `Add-Content` 및 `Set-Content` cmdlet 런타임에 추가 되는 추가 동적 매개 변수가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-185">The `Add-Content` and `Set-Content` cmdlets might require additional dynamic parameters that are added a runtime.</span></span> <span data-ttu-id="16b7d-186">이러한 동적 매개 변수를 제공 하려면 Windows PowerShell 콘텐츠 공급자를 구현 해야 합니다 [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriterdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) 이러한 처리 하는 방법 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-186">To provide these dynamic parameters, the Windows PowerShell content provider must implement the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriterdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) method to handle these parameters.</span></span> <span data-ttu-id="16b7d-187">이 메서드는 지정 된 경로에 있는 항목에 대 한 동적 매개 변수를 검색 하 고 속성 및 cmdlet 클래스와 유사한 특성을 구문 분석 된 필드에 있는 개체를 반환 또는 [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-187">This method retrieves dynamic parameters for the item at the indicated path and returns an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span> <span data-ttu-id="16b7d-188">Windows PowerShell 런타임에 반환 되는 개체를 사용 하 여 cmdlet에 대 한 매개 변수를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-188">The Windows PowerShell runtime uses the returned object to add the parameters to the cmdlets.</span></span>

<span data-ttu-id="16b7d-189">이 Windows PowerShell 컨테이너 공급자는이 메서드를 구현 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-189">This Windows PowerShell container provider does not implement this method.</span></span> <span data-ttu-id="16b7d-190">그러나 다음 코드는이 메서드의 기본 구현입니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-190">However, the following code is the default implementation of this method.</span></span>

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1887-L1890 "AccessDBProviderSample06.cs")]

## <a name="clearing-content"></a><span data-ttu-id="16b7d-191">콘텐츠 지우기</span><span class="sxs-lookup"><span data-stu-id="16b7d-191">Clearing Content</span></span>

<span data-ttu-id="16b7d-192">콘텐츠 공급자가 구현 하는 [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) 지 원하는 메서드를 `Clear-Content` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="16b7d-192">Your content provider implements the [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) method in support of the `Clear-Content` cmdlet.</span></span> <span data-ttu-id="16b7d-193">이 메서드는 지정된 된 경로에 있는 항목의 콘텐츠를 제거 하지만 항목을 그대로 둡니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-193">This method removes the contents of the item at the specified path, but leaves the item intact.</span></span>

<span data-ttu-id="16b7d-194">여기의 구현은 합니다 [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) 이 공급자에 대 한 메서드.</span><span class="sxs-lookup"><span data-stu-id="16b7d-194">Here is the implementation of the [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) method for this provider.</span></span>

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1775-L1812 "AccessDBProviderSample06.cs")]

#### <a name="things-to-remember-about-implementing-clearcontent"></a><span data-ttu-id="16b7d-195">ClearContent를 구현 하는 방법에 대 한 고려해 야 할 사항</span><span class="sxs-lookup"><span data-stu-id="16b7d-195">Things to Remember About Implementing ClearContent</span></span>

<span data-ttu-id="16b7d-196">다음과의 구현에 적용 될 수 있습니다 [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent):</span><span class="sxs-lookup"><span data-stu-id="16b7d-196">The following conditions may apply to an implementation of [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent):</span></span>

- <span data-ttu-id="16b7d-197">공급자 클래스를 정의 하는 경우 Windows PowerShell 콘텐츠 공급자에서 ExpandWildcards, 필터, 포함 또는 제외의 공급자 기능을 선언할 수 있습니다는 [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)열거형입니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-197">When defining the provider class, a Windows PowerShell content provider might declare provider capabilities of ExpandWildcards, Filter, Include, or Exclude, from the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="16b7d-198">이러한 경우의 구현에는 [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) 메서드는 메서드에 전달 된 경로 지정 된 요구 사항을 충족 하는지 확인 해야 합니다 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-198">In these cases, the implementation of the [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) method must ensure that the path passed to the method meets the requirements of the specified capabilities.</span></span> <span data-ttu-id="16b7d-199">이 작업을 수행 하는 메서드 액세스 해야 적절 한 속성을 예를 들어, [System.Management.Automation.Provider.Cmdletprovider.Exclude\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) 고 [ System.Management.Automation.Provider.Cmdletprovider.Include\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-199">To do this, the method should access the appropriate property, for example, the [System.Management.Automation.Provider.Cmdletprovider.Exclude\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) and [System.Management.Automation.Provider.Cmdletprovider.Include\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) properties.</span></span>

- <span data-ttu-id="16b7d-200">기본적으로이 메서드는 재정의 하지 않는 한 사용자 로부터 숨겨진 개체의 내용을 지우지 해야 합니다 [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 속성이 `true`합니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-200">By default, overrides of this method should not clear the contents of objects that are hidden from the user unless the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is set to `true`.</span></span> <span data-ttu-id="16b7d-201">경로 사용자 로부터 숨겨진 항목을 나타내는 경우 오류를 작성 해야 하 고 [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 로 설정 된 `false`합니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-201">An error should be written if the path represents an item that is hidden from the user and [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) is set to `false`.</span></span>

- <span data-ttu-id="16b7d-202">구현 된 [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) 메서드를 호출 해야 [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess\* ](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 데이터 저장소로 변경 하기 전에 해당 반환 값을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-202">Your implementation of the [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) method should call [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) and verify its return value before making any changes to the data store.</span></span> <span data-ttu-id="16b7d-203">이 메서드는 콘텐츠 지우기와 같은 데이터 저장소에 변경 될 때 작업의 실행을 확인 하려면 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-203">This method is used to confirm execution of an operation when a change is made to the data store, such as clearing content.</span></span> <span data-ttu-id="16b7d-204">합니다 [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 메서드는 명령줄 설정이 나 기본 설정 처리 하는 Windows PowerShell 런타임에 사용자에 게 변경 될 리소스의 이름을 전송 합니다. 표시할 내용을 결정 하는 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-204">The [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) method sends the name of the resource to be changed to the user, with the Windows PowerShell runtime handling any command-line settings or preference variables in determining what should be displayed.</span></span>

  <span data-ttu-id="16b7d-205">호출한 후 [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 반환 `true`는 [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\* ](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) 메서드를 호출 해야 합니다 [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) 메서드.</span><span class="sxs-lookup"><span data-stu-id="16b7d-205">After the call to [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) returns `true`, the [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) method should call the [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) method.</span></span> <span data-ttu-id="16b7d-206">이 메서드는 작업을 계속 진행 해야 하는 경우를 확인 하는 피드백을 허용 하도록 사용자에 게 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-206">This method sends a message to the user to allow feedback to verify if the operation should be continued.</span></span> <span data-ttu-id="16b7d-207">에 대 한 호출 [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) 잠재적으로 위험한 시스템 수정에 대 한 추가 검사를 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-207">The call to [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) allows an additional check for potentially dangerous system modifications.</span></span>

## <a name="attaching-dynamic-parameters-to-the-clear-content-cmdlet"></a><span data-ttu-id="16b7d-208">Clear-content Cmdlet에 연결 하는 동적 매개 변수</span><span class="sxs-lookup"><span data-stu-id="16b7d-208">Attaching Dynamic Parameters to the Clear-Content Cmdlet</span></span>

<span data-ttu-id="16b7d-209">`Clear-Content` cmdlet 런타임에 추가 되는 추가 동적 매개 변수가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-209">The `Clear-Content` cmdlet might require additional dynamic parameters that are added at runtime.</span></span> <span data-ttu-id="16b7d-210">이러한 동적 매개 변수를 제공 하려면 Windows PowerShell 콘텐츠 공급자를 구현 해야 합니다 [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontentdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) 이러한 처리 하는 방법 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-210">To provide these dynamic parameters, the Windows PowerShell content provider must implement the [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontentdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) method to handle these parameters.</span></span> <span data-ttu-id="16b7d-211">이 메서드는 지정 된 경로에 있는 항목에 대 한 매개 변수를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-211">This method retrieves the parameters for the item at the indicated path.</span></span> <span data-ttu-id="16b7d-212">이 메서드는 지정 된 경로에 있는 항목에 대 한 동적 매개 변수를 검색 하 고 속성 및 cmdlet 클래스와 유사한 특성을 구문 분석 된 필드에 있는 개체를 반환 또는 [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-212">This method retrieves dynamic parameters for the item at the indicated path and returns an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span> <span data-ttu-id="16b7d-213">Windows PowerShell 런타임이 cmdlet에 매개 변수를 추가할 반환된 된 개체를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-213">The Windows PowerShell runtime uses the returned object to add the parameters to the cmdlet.</span></span>

<span data-ttu-id="16b7d-214">이 Windows PowerShell 컨테이너 공급자는이 메서드를 구현 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-214">This Windows PowerShell container provider does not implement this method.</span></span> <span data-ttu-id="16b7d-215">그러나 다음 코드는이 메서드의 기본 구현입니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-215">However, the following code is the default implementation of this method.</span></span>

```csharp
public object ClearContentDynamicParameters(string path)
{
    return null;
}
```

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1819-L1822 "AccessDBProviderSample06.cs")]

## <a name="code-sample"></a><span data-ttu-id="16b7d-216">코드 예제</span><span class="sxs-lookup"><span data-stu-id="16b7d-216">Code Sample</span></span>

<span data-ttu-id="16b7d-217">전체 샘플 코드를 보려면 [AccessDbProviderSample06 코드 샘플](./accessdbprovidersample06-code-sample.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-217">For complete sample code, see [AccessDbProviderSample06 Code Sample](./accessdbprovidersample06-code-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="16b7d-218">개체 유형 정의 및 서식 지정</span><span class="sxs-lookup"><span data-stu-id="16b7d-218">Defining Object Types and Formatting</span></span>

<span data-ttu-id="16b7d-219">공급자를 작성할 때 기존 개체에 멤버를 추가 하거나 새 개체를 정의 해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-219">When writing a provider, it may be necessary to add members to existing objects or define new objects.</span></span> <span data-ttu-id="16b7d-220">이 완료 되 면 Windows PowerShell 개체의 멤버를 식별 하는 데 사용할 수 있는 형식 파일 및 개체 표시 되는 방식을 정의 하는 서식 파일을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-220">When this is done, you must create a Types file that Windows PowerShell can use to identify the members of the object and a Format file that defines how the object is displayed.</span></span> <span data-ttu-id="16b7d-221">자세한 내용은 [확장 개체 형식 및 서식](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)합니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-221">For more information, see [Extending Object Types and Formatting](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-windows-powershell-provider"></a><span data-ttu-id="16b7d-222">Windows PowerShell 공급자 작성</span><span class="sxs-lookup"><span data-stu-id="16b7d-222">Building the Windows PowerShell Provider</span></span>

<span data-ttu-id="16b7d-223">참조 [Cmdlet, 공급자, 등록 및 응용 프로그램을 호스트 하는 방법을](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)합니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-223">See [How to Register Cmdlets, Providers, and Host Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-windows-powershell-provider"></a><span data-ttu-id="16b7d-224">Windows PowerShell 공급자 테스트</span><span class="sxs-lookup"><span data-stu-id="16b7d-224">Testing the Windows PowerShell Provider</span></span>

<span data-ttu-id="16b7d-225">Windows PowerShell을 사용 하 여 Windows PowerShell 공급자가 등록 하는 경우 명령줄에서 지원 되는 cmdlet을 실행 하 여 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-225">When your Windows PowerShell provider has been registered with Windows PowerShell, you can test it by running the supported cmdlets on the command line.</span></span> <span data-ttu-id="16b7d-226">예를 들어 샘플 콘텐츠 공급자를 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-226">For example, test the sample content provider.</span></span>

<span data-ttu-id="16b7d-227">사용 합니다 `Get-Content` cmdlet은 지정한 경로에 데이터베이스 테이블에서 지정 된 항목의 콘텐츠를 검색 하는 `Path` 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-227">Use the `Get-Content` cmdlet to retrieve the contents of specified item in the database table at the path specified by the `Path` parameter.</span></span> <span data-ttu-id="16b7d-228">`ReadCount` 매개 변수 (기본값 1)를 읽는 데 사용할 콘텐츠 정의 판독기에 대 한 항목 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-228">The `ReadCount` parameter specifies the number of items for the defined content reader to read (default 1).</span></span> <span data-ttu-id="16b7d-229">다음 명령은 항목을 사용 하 여 cmdlet 테이블에서 두 행 (항목)을 검색 하 고 해당 내용이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-229">With the following command entry, the cmdlet retrieves two rows (items) from the table and displays their contents.</span></span> <span data-ttu-id="16b7d-230">다음 예제 출력에서는 가상의 Access 데이터베이스는 참고 합니다.</span><span class="sxs-lookup"><span data-stu-id="16b7d-230">Note that the following example output uses a fictitious Access database.</span></span>

```powershell
Get-Content -Path mydb:\Customers -ReadCount 2
```

```output
ID        : 1
FirstName : Eric
LastName  : Gruber
Email     : ericgruber@fabrikam.com
Title     : President
Company   : Fabrikam
WorkPhone : (425) 555-0100
Address   : 4567 Main Street
City      : Buffalo
State     : NY
Zip       : 98052
Country   : USA
ID        : 2
FirstName : Eva
LastName  : Corets
Email     : evacorets@cohowinery.com
Title     : Sales Representative
Company   : Coho Winery
WorkPhone : (360) 555-0100
Address   : 8910 Main Street
City      : Cabmerlot
State     : WA
Zip       : 98089
Country   : USA
```

## <a name="see-also"></a><span data-ttu-id="16b7d-231">참고 항목</span><span class="sxs-lookup"><span data-stu-id="16b7d-231">See Also</span></span>

[<span data-ttu-id="16b7d-232">Windows PowerShell 공급자 만들기</span><span class="sxs-lookup"><span data-stu-id="16b7d-232">Creating Windows PowerShell providers</span></span>](./how-to-create-a-windows-powershell-provider.md)

[<span data-ttu-id="16b7d-233">디자인 Your Windows PowerShell 공급자</span><span class="sxs-lookup"><span data-stu-id="16b7d-233">Design Your Windows PowerShell provider</span></span>](./designing-your-windows-powershell-provider.md)

[<span data-ttu-id="16b7d-234">확장 개체 형식 및 서식 지정</span><span class="sxs-lookup"><span data-stu-id="16b7d-234">Extending Object Types and Formatting</span></span>](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="16b7d-235">Windows PowerShell 탐색 공급자 구현</span><span class="sxs-lookup"><span data-stu-id="16b7d-235">Implement a Navigation Windows PowerShell provider</span></span>](./creating-a-windows-powershell-navigation-provider.md)

[<span data-ttu-id="16b7d-236">Cmdlet, 공급자, 등록 및 응용 프로그램을 호스트 하는 방법</span><span class="sxs-lookup"><span data-stu-id="16b7d-236">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="16b7d-237">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="16b7d-237">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="16b7d-238">Windows PowerShell 프로그래머 가이드</span><span class="sxs-lookup"><span data-stu-id="16b7d-238">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)
