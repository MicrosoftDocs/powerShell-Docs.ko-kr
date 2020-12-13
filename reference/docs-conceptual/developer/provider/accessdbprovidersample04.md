---
ms.date: 09/13/2016
ms.topic: reference
title: AccessDBProviderSample04
description: AccessDBProviderSample04
ms.openlocfilehash: 962d0ab673ff797a60b56ccae7a16a810cc43c58
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92649035"
---
# <a name="accessdbprovidersample04"></a><span data-ttu-id="e8191-103">AccessDBProviderSample04</span><span class="sxs-lookup"><span data-stu-id="e8191-103">AccessDBProviderSample04</span></span>

<span data-ttu-id="e8191-104">이 샘플에서는 `Copy-Item` ,, `Get-ChildItem` `New-Item` 및 cmdlet에 대 한 호출을 지원 하도록 컨테이너 메서드를 덮어쓰는 방법을 보여 줍니다 `Remove-Item` .</span><span class="sxs-lookup"><span data-stu-id="e8191-104">This sample shows how to overwrite container methods to support calls to the `Copy-Item`, `Get-ChildItem`, `New-Item`, and `Remove-Item` cmdlets.</span></span> <span data-ttu-id="e8191-105">이러한 메서드는 데이터 저장소에 컨테이너 항목이 포함될 때 구현해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8191-105">These methods should be implemented when the data store contains items that are containers.</span></span> <span data-ttu-id="e8191-106">컨테이너는 공통 부모 항목 아래에 있는 자식 항목 그룹입니다.</span><span class="sxs-lookup"><span data-stu-id="e8191-106">A container is a group of child items under a common parent item.</span></span> <span data-ttu-id="e8191-107">이 샘플의 공급자 클래스는 [Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) 클래스에서 파생 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8191-107">The provider class in this sample derives from the [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="e8191-108">데모</span><span class="sxs-lookup"><span data-stu-id="e8191-108">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e8191-109">공급자 클래스는 대부분 [system.object](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 에서 파생 될 가능성이 높습니다.</span><span class="sxs-lookup"><span data-stu-id="e8191-109">Your provider class will most likely derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)</span></span>

<span data-ttu-id="e8191-110">이 샘플은 다음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e8191-110">This sample demonstrates the following:</span></span>

- <span data-ttu-id="e8191-111">특성 선언 `CmdletProvider`</span><span class="sxs-lookup"><span data-stu-id="e8191-111">Declaring the `CmdletProvider` attribute.</span></span>
- <span data-ttu-id="e8191-112">[Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) 클래스에서 파생 되는 공급자 클래스를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8191-112">Defining a provider class that derives from the [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span>
- <span data-ttu-id="e8191-113">[](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) `Copy-Item` 사용자가 한 위치에서 다른 위치로 항목을 복사할 수 있도록 하는 cmdlet의 동작을 변경 하는 ContainerCmdletProvider 메서드를 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="e8191-113">Overwriting the [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) method to change the behavior of the `Copy-Item` cmdlet which allows the user to copy items from one location to another.</span></span> <span data-ttu-id="e8191-114">이 샘플에서는 cmdlet에 동적 매개 변수를 추가 하는 방법을 보여 주지 않습니다 `Copy-Item` .</span><span class="sxs-lookup"><span data-stu-id="e8191-114">(This sample does not show how to add dynamic parameters to the `Copy-Item` cmdlet.)</span></span>
- <span data-ttu-id="e8191-115">Get-ChildItems cmdlet의 동작을 변경 하 여 사용자가 부모 항목의 자식 항목을 검색할 수 있도록 하는 [Getchilditems \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) 메서드를 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="e8191-115">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) method to change the behavior of the Get-ChildItems cmdlet, which allows the user to retrieve the child items of the parent item.</span></span> <span data-ttu-id="e8191-116">(이 샘플은 Get-ChildItems cmdlet에 동적 매개 변수를 추가 하는 방법을 보여 주지 않습니다.)</span><span class="sxs-lookup"><span data-stu-id="e8191-116">(This sample does not show how to add dynamic parameters to the Get-ChildItems cmdlet.)</span></span>
- <span data-ttu-id="e8191-117">Cmdlet의 매개 변수를 지정할 때 Get-ChildItems cmdlet의 동작을 변경 하려면 [Getchildnames \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) 메서드를 덮어씁니다 `Name` .</span><span class="sxs-lookup"><span data-stu-id="e8191-117">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) method to change the behavior of the Get-ChildItems cmdlet when the `Name` parameter of the cmdlet is specified.</span></span>
- <span data-ttu-id="e8191-118">사용자가 데이터 저장소에 항목을 추가할 수 있도록 하는 cmdlet의 동작을 변경 하기 위해 [Containercmdletprovider. Newitem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) 메서드를 덮어씁니다 `New-Item` .</span><span class="sxs-lookup"><span data-stu-id="e8191-118">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) method to change the behavior of the `New-Item` cmdlet, which allows the user to add items to the data store.</span></span> <span data-ttu-id="e8191-119">이 샘플에서는 cmdlet에 동적 매개 변수를 추가 하는 방법을 보여 주지 않습니다 `New-Item` .</span><span class="sxs-lookup"><span data-stu-id="e8191-119">(This sample does not show how to add dynamic parameters to the `New-Item` cmdlet.)</span></span>
- <span data-ttu-id="e8191-120">Cmdlet의 동작을 변경 하기 위해 [Containercmdletprovider. Removeitem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) 메서드를 덮어씁니다. `Remove-Item`</span><span class="sxs-lookup"><span data-stu-id="e8191-120">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Removeitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) method to change the behavior of the `Remove-Item` cmdlet.</span></span> <span data-ttu-id="e8191-121">이 샘플에서는 cmdlet에 동적 매개 변수를 추가 하는 방법을 보여 주지 않습니다 `Remove-Item` .</span><span class="sxs-lookup"><span data-stu-id="e8191-121">(This sample does not show how to add dynamic parameters to the `Remove-Item` cmdlet.)</span></span>

## <a name="example"></a><span data-ttu-id="e8191-122">예제</span><span class="sxs-lookup"><span data-stu-id="e8191-122">Example</span></span>

<span data-ttu-id="e8191-123">이 샘플에서는 항목을 복사, 만들기 및 제거 하는 데 필요한 메서드 뿐만 아니라 부모 항목의 자식 항목을 가져오는 메서드를 덮어쓰는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e8191-123">This sample shows how to overwrite the methods needed to copy, create, and remove items, as well as methods for getting the child items of a parent item.</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs" range="11-1635":::

## <a name="see-also"></a><span data-ttu-id="e8191-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e8191-124">See Also</span></span>

[<span data-ttu-id="e8191-125">System.object.. i n g.</span><span class="sxs-lookup"><span data-stu-id="e8191-125">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="e8191-126">Containercmdletprovider입니다.</span><span class="sxs-lookup"><span data-stu-id="e8191-126">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="e8191-127">System.object.. i n.</span><span class="sxs-lookup"><span data-stu-id="e8191-127">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="e8191-128">Windows PowerShell 공급자 설계</span><span class="sxs-lookup"><span data-stu-id="e8191-128">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)
