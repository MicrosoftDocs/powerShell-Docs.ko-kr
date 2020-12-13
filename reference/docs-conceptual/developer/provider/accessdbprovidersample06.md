---
ms.date: 09/13/2016
ms.topic: reference
title: AccessDBProviderSample06
description: AccessDBProviderSample06
ms.openlocfilehash: a2037c6f13ba24ba2dcb4ffecbd802566452d64e
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92656927"
---
# <a name="accessdbprovidersample06"></a><span data-ttu-id="d13ff-103">AccessDBProviderSample06</span><span class="sxs-lookup"><span data-stu-id="d13ff-103">AccessDBProviderSample06</span></span>

<span data-ttu-id="d13ff-104">이 샘플에서는 `Clear-Content` , 및 cmdlet에 대 한 호출을 지원 하도록 콘텐츠 메서드를 덮어쓰는 방법을 보여 줍니다 `Get-Content` `Set-Content` .</span><span class="sxs-lookup"><span data-stu-id="d13ff-104">This sample shows how to overwrite content methods to support calls to the `Clear-Content`, `Get-Content`, and `Set-Content` cmdlets.</span></span> <span data-ttu-id="d13ff-105">이러한 메서드는 사용자가 데이터 저장소에 있는 항목의 콘텐츠를 관리해야 하는 경우에 구현해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d13ff-105">These methods should be implemented when the user needs to manage the content of the items in the data store.</span></span> <span data-ttu-id="d13ff-106">이 샘플의 공급자 클래스는 [Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) 인터페이스를 구현 하는 클래스에서 파생 되며, [이 클래스는](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) system.object를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="d13ff-106">The provider class in this sample derives from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class, and it implements the [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="d13ff-107">데모</span><span class="sxs-lookup"><span data-stu-id="d13ff-107">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d13ff-108">공급자 클래스는 다음 클래스 중 하나에서 파생 되 고 다른 공급자 인터페이스를 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d13ff-108">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> - <span data-ttu-id="d13ff-109">[System.object. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="d13ff-109">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span> <span data-ttu-id="d13ff-110">[AccessDBProviderSample03](./accessdbprovidersample03.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d13ff-110">See [AccessDBProviderSample03](./accessdbprovidersample03.md).</span></span>
> - <span data-ttu-id="d13ff-111">[Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) 클래스를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="d13ff-111">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="d13ff-112">[AccessDBProviderSample04](./accessdbprovidersample04.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d13ff-112">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> - <span data-ttu-id="d13ff-113">[System.object](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 클래스를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="d13ff-113">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>
>
> <span data-ttu-id="d13ff-114">공급자 기능을 기반으로 파생 시킬 공급자 클래스를 선택 하는 방법에 대 한 자세한 내용은 [Windows PowerShell 공급자 디자인](./provider-types.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d13ff-114">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="d13ff-115">이 샘플은 다음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d13ff-115">This sample demonstrates the following:</span></span>

- <span data-ttu-id="d13ff-116">특성 선언 `CmdletProvider`</span><span class="sxs-lookup"><span data-stu-id="d13ff-116">Declaring the `CmdletProvider` attribute.</span></span>
- <span data-ttu-id="d13ff-117">[Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) 인터페이스를 선언 하 고 system.object 클래스에서 파생 되는 [공급자 클래스를](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 정의 하는 것입니다 (.</span><span class="sxs-lookup"><span data-stu-id="d13ff-117">Defining a provider class that derives from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class and that declares the [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface.</span></span>
- <span data-ttu-id="d13ff-118">사용자가 항목에서 콘텐츠를 제거할 수 있도록 cmdlet의 동작을 변경 하기 위해 [Icontentcmdletprovider. Clearcontent \*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) 메서드를 덮어씁니다. `Clear-Content`</span><span class="sxs-lookup"><span data-stu-id="d13ff-118">Overwriting the [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) method to change the behavior of the `Clear-Content` cmdlet, allowing the user to remove the content from an item.</span></span> <span data-ttu-id="d13ff-119">이 샘플에서는 cmdlet에 동적 매개 변수를 추가 하는 방법을 보여 주지 않습니다 `Clear-Content` .</span><span class="sxs-lookup"><span data-stu-id="d13ff-119">(This sample does not show how to add dynamic parameters to the `Clear-Content` cmdlet.)</span></span>
- <span data-ttu-id="d13ff-120">Cmdlet의 [](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) 동작을 변경 하 여 `Get-Content` 사용자가 항목의 콘텐츠를 검색할 수 있도록 하는 Icontentcmdletprovider을 덮어쓰는 경우.</span><span class="sxs-lookup"><span data-stu-id="d13ff-120">Overwriting the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) method to change the behavior of the `Get-Content` cmdlet, allowing the user to retrieve the content of an item.</span></span> <span data-ttu-id="d13ff-121">이 샘플에서는 cmdlet에 동적 매개 변수를 추가 하는 방법을 보여 주지 않습니다 `Get-Content` .</span><span class="sxs-lookup"><span data-stu-id="d13ff-121">(This sample does not show how to add dynamic parameters to the `Get-Content` cmdlet.).</span></span>
- <span data-ttu-id="d13ff-122">Cmdlet의 동작을 변경 하 여 사용자가 항목의 내용을 업데이트할 수 있도록 하는 Filesystemprovider. [Getcontentwriter \*](/dotnet/api/Microsoft.PowerShell.Commands.FileSystemProvider.GetContentWriter) 메서드를 덮어씁니다. `Set-Content`</span><span class="sxs-lookup"><span data-stu-id="d13ff-122">Overwriting the [Microsoft.PowerShell.Commands.Filesystemprovider.Getcontentwriter\*](/dotnet/api/Microsoft.PowerShell.Commands.FileSystemProvider.GetContentWriter) method to change the behavior of the `Set-Content` cmdlet, allowing the user to update the content of an item.</span></span> <span data-ttu-id="d13ff-123">이 샘플에서는 cmdlet에 동적 매개 변수를 추가 하는 방법을 보여 주지 않습니다 `Set-Content` .</span><span class="sxs-lookup"><span data-stu-id="d13ff-123">(This sample does not show how to add dynamic parameters to the `Set-Content` cmdlet.)</span></span>

## <a name="example"></a><span data-ttu-id="d13ff-124">예제</span><span class="sxs-lookup"><span data-stu-id="d13ff-124">Example</span></span>

<span data-ttu-id="d13ff-125">이 샘플에서는 Microsoft Access 데이터 베이스에서 항목의 내용을 지우고 가져오고 설정 하는 데 필요한 메서드를 덮어쓰는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d13ff-125">This sample shows how to overwrite the methods needed to clear, get, and set the content of items in a Microsoft Access data base.</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs" range="11-2399":::

## <a name="see-also"></a><span data-ttu-id="d13ff-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d13ff-126">See Also</span></span>

[<span data-ttu-id="d13ff-127">System.object.. i n g.</span><span class="sxs-lookup"><span data-stu-id="d13ff-127">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="d13ff-128">Containercmdletprovider입니다.</span><span class="sxs-lookup"><span data-stu-id="d13ff-128">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="d13ff-129">System.object.. i n.</span><span class="sxs-lookup"><span data-stu-id="d13ff-129">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="d13ff-130">Windows PowerShell 공급자 설계</span><span class="sxs-lookup"><span data-stu-id="d13ff-130">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)
