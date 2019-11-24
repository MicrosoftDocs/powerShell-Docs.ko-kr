---
title: AccessDBProviderSample04 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ee3a7e56-7331-4f71-9ecb-7a59b8021c68
caps.latest.revision: 10
ms.openlocfilehash: 7096f8066568c214a5902f6943a2c093932d3b56
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366342"
---
# <a name="accessdbprovidersample04"></a><span data-ttu-id="f77b7-102">AccessDBProviderSample04</span><span class="sxs-lookup"><span data-stu-id="f77b7-102">AccessDBProviderSample04</span></span>

<span data-ttu-id="f77b7-103">이 샘플에서는 `Copy-Item`, `Get-ChildItem`, `New-Item`및 `Remove-Item` cmdlet에 대 한 호출을 지원 하도록 컨테이너 메서드를 덮어쓰는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f77b7-103">This sample shows how to overwrite container methods to support calls to the `Copy-Item`, `Get-ChildItem`, `New-Item`, and `Remove-Item` cmdlets.</span></span> <span data-ttu-id="f77b7-104">이러한 메서드는 데이터 저장소에 컨테이너 항목이 포함될 때 구현해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f77b7-104">These methods should be implemented when the data store contains items that are containers.</span></span> <span data-ttu-id="f77b7-105">컨테이너는 공통 부모 항목 아래에 있는 자식 항목 그룹입니다.</span><span class="sxs-lookup"><span data-stu-id="f77b7-105">A container is a group of child items under a common parent item.</span></span> <span data-ttu-id="f77b7-106">이 샘플의 공급자 클래스는 [Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) 클래스에서 파생 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f77b7-106">The provider class in this sample derives from the [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="f77b7-107">데모</span><span class="sxs-lookup"><span data-stu-id="f77b7-107">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f77b7-108">공급자 클래스는 대부분 [system.object](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 에서 파생 될 가능성이 높습니다.</span><span class="sxs-lookup"><span data-stu-id="f77b7-108">Your provider class will most likely derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)</span></span>

<span data-ttu-id="f77b7-109">이 샘플은 다음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f77b7-109">This sample demonstrates the following:</span></span>

- <span data-ttu-id="f77b7-110">`CmdletProvider` 특성을 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="f77b7-110">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="f77b7-111">[Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) 클래스에서 파생 되는 공급자 클래스를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="f77b7-111">Defining a provider class that derives from the [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span>

- <span data-ttu-id="f77b7-112">[ContainerCmdletProvider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) 메서드를 덮어써서 사용자가 한 위치에서 다른 위치로 항목을 복사할 수 있도록 하는 `Copy-Item` cmdlet의 동작을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="f77b7-112">Overwriting the [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) method to change the behavior of the `Copy-Item` cmdlet which allows the user to copy items from one location to another.</span></span> <span data-ttu-id="f77b7-113">(이 샘플은 `Copy-Item` cmdlet에 동적 매개 변수를 추가 하는 방법을 보여 주지 않습니다.)</span><span class="sxs-lookup"><span data-stu-id="f77b7-113">(This sample does not show how to add dynamic parameters to the `Copy-Item` cmdlet.)</span></span>

- <span data-ttu-id="f77b7-114">[Containercmdletprovider Getchilditems \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) 메서드를 덮어써서 사용자가 부모 항목의 자식 항목을 검색할 수 있도록 하는 Get childitems cmdlet의 동작을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="f77b7-114">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) method to change the behavior of the Get-ChildItems cmdlet, which allows the user to retrieve the child items of the parent item.</span></span> <span data-ttu-id="f77b7-115">(이 샘플은 동적 매개 변수를 Get ChildItems cmdlet에 추가 하는 방법을 보여 주지 않습니다.)</span><span class="sxs-lookup"><span data-stu-id="f77b7-115">(This sample does not show how to add dynamic parameters to the Get-ChildItems cmdlet.)</span></span>

- <span data-ttu-id="f77b7-116">Cmdlet의 `Name` 매개 변수가 지정 된 경우 [Containercmdletprovider Getchildnames \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) 메서드를 덮어써서 Get childitems cmdlet의 동작을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="f77b7-116">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) method to change the behavior of the Get-ChildItems cmdlet when the `Name` parameter of the cmdlet is specified.</span></span>

- <span data-ttu-id="f77b7-117">사용자가 데이터 저장소에 항목을 추가할 수 있도록 하는 `New-Item` cmdlet의 동작을 변경 하기 위해 [Containercmdletprovider. Newitem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) 메서드를 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="f77b7-117">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) method to change the behavior of the `New-Item` cmdlet, which allows the user to add items to the data store.</span></span> <span data-ttu-id="f77b7-118">(이 샘플은 `New-Item` cmdlet에 동적 매개 변수를 추가 하는 방법을 보여 주지 않습니다.)</span><span class="sxs-lookup"><span data-stu-id="f77b7-118">(This sample does not show how to add dynamic parameters to the `New-Item` cmdlet.)</span></span>

- <span data-ttu-id="f77b7-119">`Remove-Item` cmdlet의 동작을 변경 하기 위해 [Containercmdletprovider. Removeitem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) 메서드를 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="f77b7-119">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Removeitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) method to change the behavior of the `Remove-Item` cmdlet.</span></span> <span data-ttu-id="f77b7-120">(이 샘플은 `Remove-Item` cmdlet에 동적 매개 변수를 추가 하는 방법을 보여 주지 않습니다.)</span><span class="sxs-lookup"><span data-stu-id="f77b7-120">(This sample does not show how to add dynamic parameters to the `Remove-Item` cmdlet.)</span></span>

## <a name="example"></a><span data-ttu-id="f77b7-121">예제</span><span class="sxs-lookup"><span data-stu-id="f77b7-121">Example</span></span>

<span data-ttu-id="f77b7-122">이 샘플에서는 항목을 복사, 만들기 및 제거 하는 데 필요한 메서드 뿐만 아니라 부모 항목의 자식 항목을 가져오는 메서드를 덮어쓰는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f77b7-122">This sample shows how to overwrite the methods needed to copy, create, and remove items, as well as methods for getting the child items of a parent item.</span></span>

[!code-csharp[AccessDBProviderSample04.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L1635 "AccessDBProviderSample04.cs")]

## <a name="see-also"></a><span data-ttu-id="f77b7-123">관련 항목</span><span class="sxs-lookup"><span data-stu-id="f77b7-123">See Also</span></span>

[<span data-ttu-id="f77b7-124">System.object. i n g.</span><span class="sxs-lookup"><span data-stu-id="f77b7-124">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="f77b7-125">Containercmdletprovider입니다.</span><span class="sxs-lookup"><span data-stu-id="f77b7-125">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="f77b7-126">System.object. i n.</span><span class="sxs-lookup"><span data-stu-id="f77b7-126">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="f77b7-127">Windows PowerShell 공급자 디자인</span><span class="sxs-lookup"><span data-stu-id="f77b7-127">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)
