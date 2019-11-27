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
ms.openlocfilehash: 4afe0370f7a2c5b17826544e94e76650611c9d68
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74417511"
---
# <a name="creating-a-windows-powershell-content-provider"></a><span data-ttu-id="6e5d2-102">Windows PowerShell 콘텐츠 공급자 만들기</span><span class="sxs-lookup"><span data-stu-id="6e5d2-102">Creating a Windows PowerShell Content Provider</span></span>

<span data-ttu-id="6e5d2-103">이 항목에서는 사용자가 데이터 저장소에 있는 항목의 내용을 조작할 수 있도록 하는 Windows PowerShell 공급자를 만드는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-103">This topic describes how to create a Windows PowerShell provider that enables the user to manipulate the contents of the items in a data store.</span></span> <span data-ttu-id="6e5d2-104">결과적으로 항목의 내용을 조작할 수 있는 공급자를 Windows PowerShell 콘텐츠 공급자 라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-104">As a consequence, a provider that can manipulate the contents of items is referred to as a Windows PowerShell content provider.</span></span>

> [!NOTE]
> <span data-ttu-id="6e5d2-105">Windows Vista 및 .NET Framework C# 3.0 런타임 구성 요소에 대 한 Microsoft Windows 소프트웨어 개발 키트를 사용 하 여이 공급자에 대 한 원본 파일 (AccessDBSampleProvider06.cs)을 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-105">You can download the C# source file (AccessDBSampleProvider06.cs) for this provider using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="6e5d2-106">다운로드 지침은 [Windows powershell을 설치 하 고 Windows POWERSHELL SDK를 다운로드 하는 방법](/powershell/scripting/developer/installing-the-windows-powershell-sdk)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="6e5d2-107">다운로드 된 원본 파일은 **\<PowerShell Samples >** 디렉터리에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>
>
> <span data-ttu-id="6e5d2-108">다른 Windows PowerShell 공급자 구현에 대 한 자세한 내용은 [Windows Powershell 공급자 디자인](./designing-your-windows-powershell-provider.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-108">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

## <a name="define-the-windows-powershell-content-provider-class"></a><span data-ttu-id="6e5d2-109">Windows PowerShell 콘텐츠 공급자 클래스 정의</span><span class="sxs-lookup"><span data-stu-id="6e5d2-109">Define the Windows PowerShell Content Provider Class</span></span>

<span data-ttu-id="6e5d2-110">Windows PowerShell 콘텐츠 공급자는 [Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) 인터페이스를 지 원하는 .net 클래스를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-110">A Windows PowerShell content provider must create a .NET class that supports the [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface.</span></span> <span data-ttu-id="6e5d2-111">이 섹션에서 설명 하는 항목 공급자에 대 한 클래스 정의는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-111">Here is the class definition for the item provider described in this section.</span></span>

[!code-csharp[AccessDBProviderSample06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L32-L33 "AccessDBProviderSample06.cs")]

<span data-ttu-id="6e5d2-112">이 클래스 정의에서 [Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) 특성에는 두 개의 매개 변수가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-112">Note that in this class definition, the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attribute includes two parameters.</span></span> <span data-ttu-id="6e5d2-113">첫 번째 매개 변수는 Windows PowerShell에서 사용 되는 공급자에 대 한 친숙 한 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-113">The first parameter specifies a user-friendly name for the provider that is used by Windows PowerShell.</span></span> <span data-ttu-id="6e5d2-114">두 번째 매개 변수는 명령을 처리 하는 동안 공급자가 Windows PowerShell 런타임에 노출 하는 Windows PowerShell 특정 기능을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-114">The second parameter specifies the Windows PowerShell specific capabilities that the provider exposes to the Windows PowerShell runtime during command processing.</span></span> <span data-ttu-id="6e5d2-115">이 공급자의 경우 추가 된 Windows PowerShell 관련 기능이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-115">For this provider, there are no added Windows PowerShell specific capabilities.</span></span>

## <a name="define-functionality-of-base-class"></a><span data-ttu-id="6e5d2-116">기본 클래스의 기능 정의</span><span class="sxs-lookup"><span data-stu-id="6e5d2-116">Define Functionality of Base Class</span></span>

<span data-ttu-id="6e5d2-117">[Windows PowerShell 공급자 디자인](./designing-your-windows-powershell-provider.md)에 설명 된 대로, 다른 공급자 기능을 제공 하는 다른 여러 클래스에서 [파생 된 다른](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 클래스에서 파생 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-117">As described in [Design Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md), the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class derives from several other classes that provided different provider functionality.</span></span> <span data-ttu-id="6e5d2-118">따라서 Windows PowerShell 콘텐츠 공급자는 일반적으로 해당 클래스에서 제공 하는 모든 기능을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-118">A Windows PowerShell content provider, therefore, typically defines all of the functionality provided by those classes.</span></span>

<span data-ttu-id="6e5d2-119">세션 관련 초기화 정보를 추가 하 고 공급자가 사용 하는 리소스를 해제 하기 위한 기능을 구현 하는 방법에 대 한 자세한 내용은 [기본 Windows PowerShell 공급자 만들기](./creating-a-basic-windows-powershell-provider.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-119">For more information about how to implement functionality for adding session-specific initialization information and for releasing resources that are used by the provider, see [Creating a Basic Windows PowerShell Provider](./creating-a-basic-windows-powershell-provider.md).</span></span> <span data-ttu-id="6e5d2-120">그러나 여기에 설명 된 공급자를 비롯 한 대부분의 공급자는 Windows PowerShell에서 제공 하는이 기능의 기본 구현을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-120">However, most providers, including the provider described here, can use the default implementation of this functionality that is provided by Windows PowerShell.</span></span>

<span data-ttu-id="6e5d2-121">데이터 저장소에 액세스 하려면 공급자는 [system.object](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) 의 메서드를 구현 해야 합니다 (예를 들어).</span><span class="sxs-lookup"><span data-stu-id="6e5d2-121">To access the data store, the provider must implement the methods of the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) base class.</span></span> <span data-ttu-id="6e5d2-122">이러한 메서드를 구현 하는 방법에 대 한 자세한 내용은 [Windows PowerShell 드라이브 공급자 만들기](./creating-a-windows-powershell-drive-provider.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-122">For more information about implementing these methods, see [Creating a Windows PowerShell Drive Provider](./creating-a-windows-powershell-drive-provider.md).</span></span>

<span data-ttu-id="6e5d2-123">항목 가져오기, 설정 및 지우기와 같은 데이터 저장소의 항목을 조작 하려면 공급자는 [system.object](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) 에서 제공 하는 메서드를 구현 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-123">To manipulate the items of a data store, such as getting, setting, and clearing items, the provider must implement the methods provided by the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) base class.</span></span> <span data-ttu-id="6e5d2-124">이러한 메서드를 구현 하는 방법에 대 한 자세한 내용은 [Windows PowerShell 항목 공급자 만들기](./creating-a-windows-powershell-item-provider.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-124">For more information about implementing these methods, see [Creating a Windows PowerShell Item Provider](./creating-a-windows-powershell-item-provider.md).</span></span>

<span data-ttu-id="6e5d2-125">다중 계층 데이터 저장소에서 작업 하려면 공급자가 [Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) 기본 클래스에서 제공 하는 메서드를 구현 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-125">To work on multi-layer data stores, the provider must implement the methods provided by the [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) base class.</span></span> <span data-ttu-id="6e5d2-126">이러한 메서드를 구현 하는 방법에 대 한 자세한 내용은 [Windows PowerShell 컨테이너 공급자 만들기](./creating-a-windows-powershell-container-provider.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-126">For more information about implementing these methods, see [Creating a Windows PowerShell Container Provider](./creating-a-windows-powershell-container-provider.md).</span></span>

<span data-ttu-id="6e5d2-127">재귀 명령, 중첩 된 컨테이너 및 상대 경로를 지원 하려면 공급자가 [system.object](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 를 구현 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-127">To support recursive commands, nested containers, and relative paths, the provider must implement the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) base class.</span></span> <span data-ttu-id="6e5d2-128">또한이 Windows PowerShell 콘텐츠 공급자는 [Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) 인터페이스를 [system.object](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 에 연결할 수 있으며, 따라서 해당 클래스에서 제공 하는 메서드를 구현 해야 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-128">In addition, this Windows PowerShell content provider can attaches [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface to the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) base class, and must therefore implement the methods provided by that class.</span></span> <span data-ttu-id="6e5d2-129">자세한 내용은 이러한 메서드 구현을 참조 하세요. [탐색 Windows PowerShell 공급자 구현](./creating-a-windows-powershell-navigation-provider.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-129">For more information, see implementing those methods, see [Implement a Navigation Windows PowerShell Provider](./creating-a-windows-powershell-navigation-provider.md).</span></span>

## <a name="implementing-a-content-reader"></a><span data-ttu-id="6e5d2-130">콘텐츠 판독기 구현</span><span class="sxs-lookup"><span data-stu-id="6e5d2-130">Implementing a Content Reader</span></span>

<span data-ttu-id="6e5d2-131">항목에서 콘텐츠를 읽으려면 공급자가 [Icontentreader](/dotnet/api/System.Management.Automation.Provider.IContentReader)에서 파생 되는 콘텐츠 판독기 클래스를 구현 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-131">To read content from an item, a provider must implements a content reader class that derives from [System.Management.Automation.Provider.Icontentreader](/dotnet/api/System.Management.Automation.Provider.IContentReader).</span></span> <span data-ttu-id="6e5d2-132">이 공급자에 대 한 콘텐츠 판독기를 사용 하면 데이터 테이블의 행 내용에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-132">The content reader for this provider allows access to the contents of a row in a data table.</span></span> <span data-ttu-id="6e5d2-133">콘텐츠 판독기 클래스는 표시 된 행에서 데이터를 검색 하 고 해당 데이터를 나타내는 목록, 콘텐츠 판독기를 이동 하는 **Seek** 메서드, 콘텐츠 판독기를 닫는 **Close** 메서드 및 **Dispose** 메서드를 반환 하는 **읽기** 메서드를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-133">The content reader class defines a **Read** method that retrieves the data from the indicated row and returns a list representing that data, a **Seek** method that moves the content reader, a **Close** method that closes the content reader, and a **Dispose** method.</span></span>

[!code-csharp[AccessDBProviderSample06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L2115-L2241 "AccessDBProviderSample06.cs")]

## <a name="implementing-a-content-writer"></a><span data-ttu-id="6e5d2-134">콘텐츠 작성기 구현</span><span class="sxs-lookup"><span data-stu-id="6e5d2-134">Implementing a Content Writer</span></span>

<span data-ttu-id="6e5d2-135">항목에 콘텐츠를 쓰려면 공급자가 [Icontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter)에서 파생 된 콘텐츠 작성기 클래스를 구현 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-135">To write content to an item, a provider must implement a content writer class derives from [System.Management.Automation.Provider.Icontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter).</span></span> <span data-ttu-id="6e5d2-136">콘텐츠 작성기 클래스는 지정 된 행 내용을 쓰는 **Write** 메서드, 콘텐츠 작성기를 이동 하는 **Seek** 메서드, 콘텐츠 작성기를 닫는 **Close** 메서드 및 **Dispose** 메서드를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-136">The content writer class defines a **Write** method that writes the specified row content, a **Seek** method that moves the content writer, a **Close** method that closes the content writer, and a **Dispose** method.</span></span>

[!code-csharp[AccessDBProviderSample06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L2250-L2394 "AccessDBProviderSample06.cs")]

## <a name="retrieving-the-content-reader"></a><span data-ttu-id="6e5d2-137">콘텐츠 판독기를 검색 하는 중</span><span class="sxs-lookup"><span data-stu-id="6e5d2-137">Retrieving the Content Reader</span></span>

<span data-ttu-id="6e5d2-138">항목에서 콘텐츠를 가져오기 위해 공급자는 `Get-Content` cmdlet을 지원 하기 위해 [Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) 을 구현 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-138">To get content from an item, the provider must implement the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) to support the `Get-Content` cmdlet.</span></span> <span data-ttu-id="6e5d2-139">이 메서드는 지정 된 경로에 있는 항목에 대 한 콘텐츠 판독기를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-139">This method returns the content reader for the item located at the specified path.</span></span> <span data-ttu-id="6e5d2-140">그러면 판독기 개체를 열어 콘텐츠를 읽을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-140">The reader object can then be opened to read the content.</span></span>

<span data-ttu-id="6e5d2-141">다음은이 공급자에 대 한이 메서드에 대 한 [Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) 의 구현입니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-141">Here is the implementation of [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) for this method for this provider.</span></span>

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

[!code-csharp[AccessDBProviderSample06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1829-L1846 "AccessDBProviderSample06.cs")]

#### <a name="things-to-remember-about-implementing-getcontentreader"></a><span data-ttu-id="6e5d2-142">GetContentReader 구현에 대해 기억할 사항</span><span class="sxs-lookup"><span data-stu-id="6e5d2-142">Things to Remember About Implementing GetContentReader</span></span>

<span data-ttu-id="6e5d2-143">다음 조건은 Icontentcmdletprovider의 구현에 적용 될 수 있습니다. [\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader)입니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-143">The following conditions may apply to an implementation of [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader):</span></span>

- <span data-ttu-id="6e5d2-144">공급자 클래스를 정의 하는 경우 Windows PowerShell 콘텐츠 공급자가 ExpandWildcards, Filter, Include 또는 Exclude의 공급자 기능을 [system.object](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) 열거형에서 선언할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-144">When defining the provider class, a Windows PowerShell content provider might declare provider capabilities of ExpandWildcards, Filter, Include, or Exclude, from the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="6e5d2-145">이러한 경우 [Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) 를 구현 하면 메서드에 전달 된 경로가 지정 된 기능의 요구 사항을 충족 하는지 확인 해야 합니다 (예를 들어).</span><span class="sxs-lookup"><span data-stu-id="6e5d2-145">In these cases, the implementation of the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) method must ensure that the path passed to the method meets the requirements of the specified capabilities.</span></span> <span data-ttu-id="6e5d2-146">이 작업을 수행 하려면 메서드가 적절 한 속성 (예: System.object)에 액세스 해야 합니다. [\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) 및 [system.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .... n a m.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-146">To do this, the method should access the appropriate property, for example, the [System.Management.Automation.Provider.Cmdletprovider.Exclude\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) and [System.Management.Automation.Provider.Cmdletprovider.Include\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) properties.</span></span>

- <span data-ttu-id="6e5d2-147">기본적으로이 메서드의 재정의는 사용자에 게 표시 되는 개체에 대 한 판독기를 검색 해서는 안 됩니다 .이 경우에는 [system.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 를 `true`으로 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-147">By default, overrides of this method should not retrieve a reader for objects that are hidden from the user unless the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is set to `true`.</span></span> <span data-ttu-id="6e5d2-148">경로가 사용자 및 시스템에서 숨겨진 항목을 나타내는 경우에는 오류를 작성 해야 합니다 [. Force \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 는 `false`로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-148">An error should be written if the path represents an item that is hidden from the user and [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) is set to `false`.</span></span>

## <a name="attaching-dynamic-parameters-to-the-get-content-cmdlet"></a><span data-ttu-id="6e5d2-149">Get Content Cmdlet에 동적 매개 변수 연결</span><span class="sxs-lookup"><span data-stu-id="6e5d2-149">Attaching Dynamic Parameters to the Get-Content Cmdlet</span></span>

<span data-ttu-id="6e5d2-150">`Get-Content` cmdlet에는 런타임에 동적으로 지정 되는 추가 매개 변수가 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-150">The `Get-Content` cmdlet might require additional parameters that are specified dynamically at runtime.</span></span> <span data-ttu-id="6e5d2-151">이러한 동적 매개 변수를 제공 하려면 Windows PowerShell 콘텐츠 공급자가 Icontentcmdletprovider. [Getcontentreaderdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) 메서드를 구현 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-151">To provide these dynamic parameters, the Windows PowerShell content provider must implement the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreaderdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) method.</span></span> <span data-ttu-id="6e5d2-152">이 메서드는 지정 된 경로에서 항목에 대 한 동적 매개 변수를 검색 하 고 cmdlet 클래스 또는 [Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 개체와 유사한 구문 분석 특성이 있는 속성 및 필드가 있는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-152">This method retrieves dynamic parameters for the item at the indicated path and returns an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span> <span data-ttu-id="6e5d2-153">Windows PowerShell 런타임은 반환 된 개체를 사용 하 여 cmdlet에 매개 변수를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-153">The Windows PowerShell runtime uses the returned object to add the parameters to the cmdlet.</span></span>

<span data-ttu-id="6e5d2-154">이 Windows PowerShell 컨테이너 공급자는이 메서드를 구현 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-154">This Windows PowerShell container provider does not implement this method.</span></span> <span data-ttu-id="6e5d2-155">그러나 다음 코드는이 메서드의 기본 구현입니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-155">However, the following code is the default implementation of this method.</span></span>

```csharp
public object GetContentReaderDynamicParameters(string path)
{
    return null;
}
```

[!code-csharp[AccessDBProviderSample06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1853-L1856 "AccessDBProviderSample06.cs")]

## <a name="retrieving-the-content-writer"></a><span data-ttu-id="6e5d2-156">콘텐츠 기록기를 검색 하는 중</span><span class="sxs-lookup"><span data-stu-id="6e5d2-156">Retrieving the Content Writer</span></span>

<span data-ttu-id="6e5d2-157">항목에 콘텐츠를 쓰려면 공급자가 `Set-Content` 및 `Add-Content` cmdlet을 지원 하기 위해 [Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) 을 구현 해야 합니다 ().</span><span class="sxs-lookup"><span data-stu-id="6e5d2-157">To write content to an item, the provider must implement the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) to support the `Set-Content` and `Add-Content` cmdlets.</span></span> <span data-ttu-id="6e5d2-158">이 메서드는 지정 된 경로에 있는 항목에 대 한 콘텐츠 작성기를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-158">This method returns the content writer for the item located at the specified path.</span></span>

<span data-ttu-id="6e5d2-159">다음은이 메서드에 대 한 [Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) 의 구현입니다 (예를 들어,</span><span class="sxs-lookup"><span data-stu-id="6e5d2-159">Here is the implementation of [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) for this method.</span></span>

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

[!code-csharp[AccessDBProviderSample06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1863-L1880 "AccessDBProviderSample06.cs")]

#### <a name="things-to-remember-about-implementing-getcontentwriter"></a><span data-ttu-id="6e5d2-160">GetContentWriter 구현에 대해 기억할 사항</span><span class="sxs-lookup"><span data-stu-id="6e5d2-160">Things to Remember About Implementing GetContentWriter</span></span>

<span data-ttu-id="6e5d2-161">다음 조건은 Icontentcmdletprovider의 구현에 적용 될 수 있습니다. [Getcontentwriter \*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter):</span><span class="sxs-lookup"><span data-stu-id="6e5d2-161">The following conditions may apply to your implementation of [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter):</span></span>

- <span data-ttu-id="6e5d2-162">공급자 클래스를 정의 하는 경우 Windows PowerShell 콘텐츠 공급자가 ExpandWildcards, Filter, Include 또는 Exclude의 공급자 기능을 [system.object](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) 열거형에서 선언할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-162">When defining the provider class, a Windows PowerShell content provider might declare provider capabilities of ExpandWildcards, Filter, Include, or Exclude, from the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="6e5d2-163">이러한 경우 [Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) 메서드를 구현 하 여 메서드에 전달 된 경로가 지정 된 기능의 요구 사항을 충족 하는지 확인 해야 합니다 (예).</span><span class="sxs-lookup"><span data-stu-id="6e5d2-163">In these cases, the implementation of the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) method must ensure that the path passed to the method meets the requirements of the specified capabilities.</span></span> <span data-ttu-id="6e5d2-164">이 작업을 수행 하려면 메서드가 적절 한 속성 (예: System.object)에 액세스 해야 합니다. [\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) 및 [system.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .... n a m.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-164">To do this, the method should access the appropriate property, for example, the [System.Management.Automation.Provider.Cmdletprovider.Exclude\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) and [System.Management.Automation.Provider.Cmdletprovider.Include\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) properties.</span></span>

- <span data-ttu-id="6e5d2-165">기본적으로이 메서드의 재정의는 사용자에 게 표시 되는 개체에 대 한 기록기를 검색 해서는 안 됩니다 .이 경우에는 [system.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 를 `true`으로 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-165">By default, overrides of this method should not retrieve a writer for objects that are hidden from the user unless the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is set to `true`.</span></span> <span data-ttu-id="6e5d2-166">경로가 사용자 및 시스템에서 숨겨진 항목을 나타내는 경우에는 오류를 작성 해야 합니다 [. Force \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 는 `false`로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-166">An error should be written if the path represents an item that is hidden from the user and [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) is set to `false`.</span></span>

## <a name="attaching-dynamic-parameters-to-the-add-content-and-set-content-cmdlets"></a><span data-ttu-id="6e5d2-167">동적 매개 변수를 추가 내용 및 집합 내용 Cmdlet에 연결</span><span class="sxs-lookup"><span data-stu-id="6e5d2-167">Attaching Dynamic Parameters to the Add-Content and Set-Content Cmdlets</span></span>

<span data-ttu-id="6e5d2-168">`Add-Content` 및 `Set-Content` cmdlet에는 런타임에 추가 된 추가 동적 매개 변수가 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-168">The `Add-Content` and `Set-Content` cmdlets might require additional dynamic parameters that are added a runtime.</span></span> <span data-ttu-id="6e5d2-169">이러한 동적 매개 변수를 제공 하려면 Windows PowerShell 콘텐츠 공급자가 이러한 매개 변수를 처리 하는 [Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) 을 구현 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-169">To provide these dynamic parameters, the Windows PowerShell content provider must implement the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriterdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) method to handle these parameters.</span></span> <span data-ttu-id="6e5d2-170">이 메서드는 지정 된 경로에서 항목에 대 한 동적 매개 변수를 검색 하 고 cmdlet 클래스 또는 [Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 개체와 유사한 구문 분석 특성이 있는 속성 및 필드가 있는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-170">This method retrieves dynamic parameters for the item at the indicated path and returns an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span> <span data-ttu-id="6e5d2-171">Windows PowerShell 런타임은 반환 된 개체를 사용 하 여 cmdlet에 매개 변수를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-171">The Windows PowerShell runtime uses the returned object to add the parameters to the cmdlets.</span></span>

<span data-ttu-id="6e5d2-172">이 Windows PowerShell 컨테이너 공급자는이 메서드를 구현 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-172">This Windows PowerShell container provider does not implement this method.</span></span> <span data-ttu-id="6e5d2-173">그러나 다음 코드는이 메서드의 기본 구현입니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-173">However, the following code is the default implementation of this method.</span></span>

[!code-csharp[AccessDBProviderSample06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1887-L1890 "AccessDBProviderSample06.cs")]

## <a name="clearing-content"></a><span data-ttu-id="6e5d2-174">콘텐츠 지우기</span><span class="sxs-lookup"><span data-stu-id="6e5d2-174">Clearing Content</span></span>

<span data-ttu-id="6e5d2-175">콘텐츠 공급자는 `Clear-Content` cmdlet을 지 원하는 [Icontentcmdletprovider. Clearcontent \*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) 메서드를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-175">Your content provider implements the [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) method in support of the `Clear-Content` cmdlet.</span></span> <span data-ttu-id="6e5d2-176">이 메서드는 지정 된 경로에 있는 항목의 내용을 제거 하지만 항목은 그대로 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-176">This method removes the contents of the item at the specified path, but leaves the item intact.</span></span>

<span data-ttu-id="6e5d2-177">이 공급자에 대 한 [Icontentcmdletprovider. Clearcontent \*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) 메서드의 구현은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-177">Here is the implementation of the [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) method for this provider.</span></span>

[!code-csharp[AccessDBProviderSample06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1775-L1812 "AccessDBProviderSample06.cs")]

#### <a name="things-to-remember-about-implementing-clearcontent"></a><span data-ttu-id="6e5d2-178">ClearContent 구현에 대해 기억할 사항</span><span class="sxs-lookup"><span data-stu-id="6e5d2-178">Things to Remember About Implementing ClearContent</span></span>

<span data-ttu-id="6e5d2-179">다음 조건은 Icontentcmdletprovider의 구현에 적용 될 수 있습니다. [Clearcontent \*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent):</span><span class="sxs-lookup"><span data-stu-id="6e5d2-179">The following conditions may apply to an implementation of [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent):</span></span>

- <span data-ttu-id="6e5d2-180">공급자 클래스를 정의 하는 경우 Windows PowerShell 콘텐츠 공급자가 ExpandWildcards, Filter, Include 또는 Exclude의 공급자 기능을 [system.object](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) 열거형에서 선언할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-180">When defining the provider class, a Windows PowerShell content provider might declare provider capabilities of ExpandWildcards, Filter, Include, or Exclude, from the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="6e5d2-181">이러한 경우 [Icontentcmdletprovider. Clearcontent \*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) 메서드를 구현 하면 메서드에 전달 된 경로가 지정 된 기능의 요구 사항을 충족 하는지 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-181">In these cases, the implementation of the [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) method must ensure that the path passed to the method meets the requirements of the specified capabilities.</span></span> <span data-ttu-id="6e5d2-182">이 작업을 수행 하려면 메서드가 적절 한 속성 (예: System.object)에 액세스 해야 합니다. [\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) 및 [system.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .... n a m.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-182">To do this, the method should access the appropriate property, for example, the [System.Management.Automation.Provider.Cmdletprovider.Exclude\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) and [System.Management.Automation.Provider.Cmdletprovider.Include\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) properties.</span></span>

- <span data-ttu-id="6e5d2-183">기본적으로이 메서드를 재정의 하면 사용자에 게 표시 되는 개체의 콘텐츠를 지워야 합니다 .이 경우에는 [system.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 를 `true`으로 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-183">By default, overrides of this method should not clear the contents of objects that are hidden from the user unless the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is set to `true`.</span></span> <span data-ttu-id="6e5d2-184">경로가 사용자 및 시스템에서 숨겨진 항목을 나타내는 경우에는 오류를 작성 해야 합니다 [. Force \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 는 `false`로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-184">An error should be written if the path represents an item that is hidden from the user and [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) is set to `false`.</span></span>

- <span data-ttu-id="6e5d2-185">[Icontentcmdletprovider. Clearcontent \*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) 메서드를 구현 하면 데이터 저장소를 변경 하기 전에 해당 반환 값을 확인 [하 고 해당 반환 값을 확인](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-185">Your implementation of the [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) method should call [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) and verify its return value before making any changes to the data store.</span></span> <span data-ttu-id="6e5d2-186">이 메서드는 콘텐츠 지우기와 같은 데이터 저장소가 변경 될 때 작업 실행을 확인 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-186">This method is used to confirm execution of an operation when a change is made to the data store, such as clearing content.</span></span> <span data-ttu-id="6e5d2-187">[System.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 는 사용자에 게 변경할 리소스의 이름을 보냅니다 .이 메서드는 사용자에 게 표시 되는 모든 명령줄 설정 또는 기본 설정 변수를 처리 하는 사용자에 게 변경할 리소스의 이름을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-187">The [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) method sends the name of the resource to be changed to the user, with the Windows PowerShell runtime handling any command-line settings or preference variables in determining what should be displayed.</span></span>

  <span data-ttu-id="6e5d2-188">Icontentcmdletprovider를 호출한 후에는 [ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 가 `true`를 반환 합니다. Clearcontent \* 메서드는 [system.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) 를 호출 해야 합니다. [\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) 메서드를 호출 하는 경우에는 메서드를 호출 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-188">After the call to [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) returns `true`, the [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) method should call the [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) method.</span></span> <span data-ttu-id="6e5d2-189">이 메서드는 사용자에 게 작업을 계속 해야 하는지 여부를 확인 하기 위해 사용자에 게 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-189">This method sends a message to the user to allow feedback to verify if the operation should be continued.</span></span> <span data-ttu-id="6e5d2-190">System.object를 호출 하면 잠재적으로 위험한 시스템 수정에 대 한 추가 검사를 수행할 수 있습니다 [.](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)</span><span class="sxs-lookup"><span data-stu-id="6e5d2-190">The call to [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) allows an additional check for potentially dangerous system modifications.</span></span>

## <a name="attaching-dynamic-parameters-to-the-clear-content-cmdlet"></a><span data-ttu-id="6e5d2-191">동적 매개 변수를 Clear Content Cmdlet에 연결</span><span class="sxs-lookup"><span data-stu-id="6e5d2-191">Attaching Dynamic Parameters to the Clear-Content Cmdlet</span></span>

<span data-ttu-id="6e5d2-192">`Clear-Content` cmdlet에는 런타임에 추가 되는 추가 동적 매개 변수가 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-192">The `Clear-Content` cmdlet might require additional dynamic parameters that are added at runtime.</span></span> <span data-ttu-id="6e5d2-193">이러한 동적 매개 변수를 제공 하려면 Windows PowerShell 콘텐츠 공급자가 이러한 매개 변수를 처리 하는 [Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) 을 구현 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-193">To provide these dynamic parameters, the Windows PowerShell content provider must implement the [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontentdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) method to handle these parameters.</span></span> <span data-ttu-id="6e5d2-194">이 메서드는 지정 된 경로에서 항목에 대 한 매개 변수를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-194">This method retrieves the parameters for the item at the indicated path.</span></span> <span data-ttu-id="6e5d2-195">이 메서드는 지정 된 경로에서 항목에 대 한 동적 매개 변수를 검색 하 고 cmdlet 클래스 또는 [Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 개체와 유사한 구문 분석 특성이 있는 속성 및 필드가 있는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-195">This method retrieves dynamic parameters for the item at the indicated path and returns an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span> <span data-ttu-id="6e5d2-196">Windows PowerShell 런타임은 반환 된 개체를 사용 하 여 cmdlet에 매개 변수를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-196">The Windows PowerShell runtime uses the returned object to add the parameters to the cmdlet.</span></span>

<span data-ttu-id="6e5d2-197">이 Windows PowerShell 컨테이너 공급자는이 메서드를 구현 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-197">This Windows PowerShell container provider does not implement this method.</span></span> <span data-ttu-id="6e5d2-198">그러나 다음 코드는이 메서드의 기본 구현입니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-198">However, the following code is the default implementation of this method.</span></span>

```csharp
public object ClearContentDynamicParameters(string path)
{
    return null;
}
```

[!code-csharp[AccessDBProviderSample06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1819-L1822 "AccessDBProviderSample06.cs")]

## <a name="code-sample"></a><span data-ttu-id="6e5d2-199">코드 예제</span><span class="sxs-lookup"><span data-stu-id="6e5d2-199">Code Sample</span></span>

<span data-ttu-id="6e5d2-200">전체 샘플 코드는 [AccessDbProviderSample06 코드 샘플](./accessdbprovidersample06-code-sample.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-200">For complete sample code, see [AccessDbProviderSample06 Code Sample](./accessdbprovidersample06-code-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="6e5d2-201">개체 형식 및 서식 정의</span><span class="sxs-lookup"><span data-stu-id="6e5d2-201">Defining Object Types and Formatting</span></span>

<span data-ttu-id="6e5d2-202">공급자를 작성할 때 기존 개체에 멤버를 추가 하거나 새 개체를 정의 해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-202">When writing a provider, it may be necessary to add members to existing objects or define new objects.</span></span> <span data-ttu-id="6e5d2-203">이 작업이 완료 되 면 Windows PowerShell에서 개체의 멤버와 개체 표시 방법을 정의 하는 서식 파일을 식별 하는 데 사용할 수 있는 형식 파일을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-203">When this is done, you must create a Types file that Windows PowerShell can use to identify the members of the object and a Format file that defines how the object is displayed.</span></span> <span data-ttu-id="6e5d2-204">자세한 내용은 [개체 형식 확장 및 서식 지정](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-204">For more information, see [Extending Object Types and Formatting](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-windows-powershell-provider"></a><span data-ttu-id="6e5d2-205">Windows PowerShell 공급자 빌드</span><span class="sxs-lookup"><span data-stu-id="6e5d2-205">Building the Windows PowerShell Provider</span></span>

<span data-ttu-id="6e5d2-206">[Cmdlet, 공급자 및 호스트 응용 프로그램을 등록 하는 방법을](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-206">See [How to Register Cmdlets, Providers, and Host Applications](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-windows-powershell-provider"></a><span data-ttu-id="6e5d2-207">Windows PowerShell 공급자 테스트</span><span class="sxs-lookup"><span data-stu-id="6e5d2-207">Testing the Windows PowerShell Provider</span></span>

<span data-ttu-id="6e5d2-208">Windows powershell 공급자를 Windows PowerShell에 등록 한 경우 명령줄에서 지원 되는 cmdlet을 실행 하 여 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-208">When your Windows PowerShell provider has been registered with Windows PowerShell, you can test it by running the supported cmdlets on the command line.</span></span> <span data-ttu-id="6e5d2-209">예를 들어 샘플 콘텐츠 공급자를 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-209">For example, test the sample content provider.</span></span>

<span data-ttu-id="6e5d2-210">`Get-Content` cmdlet을 사용 하 여 `Path` 매개 변수로 지정 된 경로에서 데이터베이스 테이블의 지정 된 항목 내용을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-210">Use the `Get-Content` cmdlet to retrieve the contents of specified item in the database table at the path specified by the `Path` parameter.</span></span> <span data-ttu-id="6e5d2-211">`ReadCount` 매개 변수는 정의 된 콘텐츠 판독기에서 읽을 항목 수를 지정 합니다 (기본값 1).</span><span class="sxs-lookup"><span data-stu-id="6e5d2-211">The `ReadCount` parameter specifies the number of items for the defined content reader to read (default 1).</span></span> <span data-ttu-id="6e5d2-212">다음 명령 항목을 사용 하 여 cmdlet은 테이블에서 두 개의 행 (항목)을 검색 하 고 해당 내용을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-212">With the following command entry, the cmdlet retrieves two rows (items) from the table and displays their contents.</span></span> <span data-ttu-id="6e5d2-213">다음 예제 출력에서는 가상의 Access 데이터베이스를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d2-213">Note that the following example output uses a fictitious Access database.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="6e5d2-214">관련 항목</span><span class="sxs-lookup"><span data-stu-id="6e5d2-214">See Also</span></span>

[<span data-ttu-id="6e5d2-215">Windows PowerShell 공급자 만들기</span><span class="sxs-lookup"><span data-stu-id="6e5d2-215">Creating Windows PowerShell providers</span></span>](./how-to-create-a-windows-powershell-provider.md)

[<span data-ttu-id="6e5d2-216">Windows PowerShell 공급자 디자인</span><span class="sxs-lookup"><span data-stu-id="6e5d2-216">Design Your Windows PowerShell provider</span></span>](./designing-your-windows-powershell-provider.md)

[<span data-ttu-id="6e5d2-217">개체 형식 및 서식 확장</span><span class="sxs-lookup"><span data-stu-id="6e5d2-217">Extending Object Types and Formatting</span></span>](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="6e5d2-218">탐색 Windows PowerShell 공급자 구현</span><span class="sxs-lookup"><span data-stu-id="6e5d2-218">Implement a Navigation Windows PowerShell provider</span></span>](./creating-a-windows-powershell-navigation-provider.md)

[<span data-ttu-id="6e5d2-219">Cmdlet, 공급자 및 호스트 응용 프로그램을 등록 하는 방법</span><span class="sxs-lookup"><span data-stu-id="6e5d2-219">How to Register Cmdlets, Providers, and Host Applications</span></span>](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="6e5d2-220">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="6e5d2-220">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="6e5d2-221">Windows PowerShell 프로그래머 가이드</span><span class="sxs-lookup"><span data-stu-id="6e5d2-221">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)
