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
ms.openlocfilehash: d9109e8d5b69a25ad52b90bcaff9628b01067211
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081024"
---
# <a name="accessdbprovidersample04"></a><span data-ttu-id="d1664-102">AccessDBProviderSample04</span><span class="sxs-lookup"><span data-stu-id="d1664-102">AccessDBProviderSample04</span></span>

<span data-ttu-id="d1664-103">이 샘플에 대 한 호출을 지원 하기 위해 컨테이너 메서드를 덮어쓰는 방법을 보여 줍니다 합니다 `Copy-Item`, `Get-ChildItem`를 `New-Item`, 및 `Remove-Item` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d1664-103">This sample shows how to overwrite container methods to support calls to the `Copy-Item`, `Get-ChildItem`, `New-Item`, and `Remove-Item` cmdlets.</span></span> <span data-ttu-id="d1664-104">이러한 메서드는 데이터 저장소에 컨테이너 항목이 포함될 때 구현해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1664-104">These methods should be implemented when the data store contains items that are containers.</span></span> <span data-ttu-id="d1664-105">컨테이너는 공통 부모 항목 아래에 있는 자식 항목 그룹입니다.</span><span class="sxs-lookup"><span data-stu-id="d1664-105">A container is a group of child items under a common parent item.</span></span> <span data-ttu-id="d1664-106">이 샘플의 공급자 클래스에서 파생 된 [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="d1664-106">The provider class in this sample derives from the [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="d1664-107">데모</span><span class="sxs-lookup"><span data-stu-id="d1664-107">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d1664-108">공급자 클래스에서 파생 가능성이 됩니다는 [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)</span><span class="sxs-lookup"><span data-stu-id="d1664-108">Your provider class will most likely derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)</span></span>

<span data-ttu-id="d1664-109">이 샘플에는 다음 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d1664-109">This sample demonstrates the following:</span></span>

- <span data-ttu-id="d1664-110">선언 된 `CmdletProvider` 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="d1664-110">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="d1664-111">파생 되는 공급자 클래스를 정의 합니다 [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="d1664-111">Defining a provider class that derives from the [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span>

- <span data-ttu-id="d1664-112">덮어쓰기 합니다 [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) 의 동작을 변경 하는 방법의 `Copy-Item` 다른 한 위치에서 항목을 복사할 수 있는 cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d1664-112">Overwriting the [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) method to change the behavior of the `Copy-Item` cmdlet which allows the user to copy items from one location to another.</span></span> <span data-ttu-id="d1664-113">(이 샘플의 동적 매개 변수를 추가 하는 방법을 보여주지 않습니다는 `Copy-Item` cmdlet입니다.)</span><span class="sxs-lookup"><span data-stu-id="d1664-113">(This sample does not show how to add dynamic parameters to the `Copy-Item` cmdlet.)</span></span>

- <span data-ttu-id="d1664-114">덮어쓰기 합니다 [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) 부모 항목의 자식 항목을 검색할 수 있는 Get ChildItems cmdlet의 동작을 변경 하는 방법 .</span><span class="sxs-lookup"><span data-stu-id="d1664-114">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) method to change the behavior of the Get-ChildItems cmdlet, which allows the user to retrieve the child items of the parent item.</span></span> <span data-ttu-id="d1664-115">(이 샘플 ChildItems Get cmdlet에 동적 매개 변수를 추가 하는 표시 되지 않습니다.)</span><span class="sxs-lookup"><span data-stu-id="d1664-115">(This sample does not show how to add dynamic parameters to the Get-ChildItems cmdlet.)</span></span>

- <span data-ttu-id="d1664-116">덮어쓰기 합니다 [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) ChildItems Get cmdlet의 동작을 변경 하는 방법 때는 `Name` cmdlet의 매개 변수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1664-116">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) method to change the behavior of the Get-ChildItems cmdlet when the `Name` parameter of the cmdlet is specified.</span></span>

- <span data-ttu-id="d1664-117">덮어쓰지는 [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) 의 동작을 변경 하는 방법의 `New-Item` cmdlet는 데이터 저장소에 항목을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1664-117">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) method to change the behavior of the `New-Item` cmdlet, which allows the user to add items to the data store.</span></span> <span data-ttu-id="d1664-118">(이 샘플의 동적 매개 변수를 추가 하는 방법을 보여주지 않습니다는 `New-Item` cmdlet입니다.)</span><span class="sxs-lookup"><span data-stu-id="d1664-118">(This sample does not show how to add dynamic parameters to the `New-Item` cmdlet.)</span></span>

- <span data-ttu-id="d1664-119">덮어쓰기 합니다 [System.Management.Automation.Provider.Containercmdletprovider.Removeitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) 의 동작을 변경 하는 방법의 `Remove-Item` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d1664-119">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Removeitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) method to change the behavior of the `Remove-Item` cmdlet.</span></span> <span data-ttu-id="d1664-120">(이 샘플의 동적 매개 변수를 추가 하는 방법을 보여주지 않습니다는 `Remove-Item` cmdlet입니다.)</span><span class="sxs-lookup"><span data-stu-id="d1664-120">(This sample does not show how to add dynamic parameters to the `Remove-Item` cmdlet.)</span></span>

## <a name="example"></a><span data-ttu-id="d1664-121">예제</span><span class="sxs-lookup"><span data-stu-id="d1664-121">Example</span></span>

<span data-ttu-id="d1664-122">이 예제를 복사, 생성 및 자식 부모 항목의 항목을 가져오기 위한 메서드에 뿐만 아니라 항목을 제거 하는 데 필요한 메서드를 덮어쓰는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d1664-122">This sample shows how to overwrite the methods needed to copy, create, and remove items, as well as methods for getting the child items of a parent item.</span></span>

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L1635 "AccessDBProviderSample04.cs")]

## <a name="see-also"></a><span data-ttu-id="d1664-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d1664-123">See Also</span></span>

[<span data-ttu-id="d1664-124">System.Management.Automation.Provider.Itemcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="d1664-124">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="d1664-125">System.Management.Automation.Provider.Containercmdletprovider</span><span class="sxs-lookup"><span data-stu-id="d1664-125">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="d1664-126">System.Management.Automation.Provider.Navigationcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="d1664-126">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="d1664-127">Windows PowerShell 공급자를 디자인합니다.</span><span class="sxs-lookup"><span data-stu-id="d1664-127">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)