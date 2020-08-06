---
title: AccessDBProviderSample05 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 67a10d9192350b339da1b82d9eb367ee4af6ef86
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786852"
---
# <a name="accessdbprovidersample05"></a><span data-ttu-id="5e44d-102">AccessDBProviderSample05</span><span class="sxs-lookup"><span data-stu-id="5e44d-102">AccessDBProviderSample05</span></span>

<span data-ttu-id="5e44d-103">이 샘플에서는 및 cmdlet에 대 한 호출을 지원 하도록 컨테이너 메서드를 덮어쓰는 방법을 보여 줍니다 `Move-Item` `Join-Path` .</span><span class="sxs-lookup"><span data-stu-id="5e44d-103">This sample shows how to overwrite container methods to support calls to the `Move-Item` and `Join-Path` cmdlets.</span></span> <span data-ttu-id="5e44d-104">이러한 메서드는 사용자가 컨테이너 내의 항목을 이동해야 하고 데이터 저장소에 중첩된 컨테이너가 포함되는 경우에 구현해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e44d-104">These methods should be implemented when the user needs to move items within a container and if the data store contains nested containers.</span></span> <span data-ttu-id="5e44d-105">이 샘플의 공급자 클래스는 [system.object](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 에서 파생 된 공급자 클래스에서 파생 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e44d-105">The provider class in this sample derives from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="5e44d-106">데모</span><span class="sxs-lookup"><span data-stu-id="5e44d-106">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5e44d-107">공급자 클래스는 다음 클래스 중 하나에서 파생 되 고 다른 공급자 인터페이스를 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e44d-107">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> - <span data-ttu-id="5e44d-108">[System.object. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="5e44d-108">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span> <span data-ttu-id="5e44d-109">[AccessDBProviderSample03](./accessdbprovidersample03.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5e44d-109">See [AccessDBProviderSample03](./accessdbprovidersample03.md).</span></span>
> - <span data-ttu-id="5e44d-110">[Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) 클래스를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e44d-110">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="5e44d-111">[AccessDBProviderSample04](./accessdbprovidersample04.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5e44d-111">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> - <span data-ttu-id="5e44d-112">[System.object](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 클래스를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e44d-112">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>
>
> <span data-ttu-id="5e44d-113">공급자 기능을 기반으로 파생 시킬 공급자 클래스를 선택 하는 방법에 대 한 자세한 내용은 [Windows PowerShell 공급자 디자인](./provider-types.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5e44d-113">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="5e44d-114">이 샘플은 다음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5e44d-114">This sample demonstrates the following:</span></span>

- <span data-ttu-id="5e44d-115">특성 선언 `CmdletProvider`</span><span class="sxs-lookup"><span data-stu-id="5e44d-115">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="5e44d-116">[System.object](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 클래스에서 파생 되는 공급자 클래스를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e44d-116">Defining a provider class that derives from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>

- <span data-ttu-id="5e44d-117">[Moveitem \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) 메서드를 덮어써서 cmdlet의 동작을 변경 하 여 `Move-Item` 사용자가 한 위치에서 다른 위치로 항목을 이동할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e44d-117">Overwriting the [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) method to change the behavior of the `Move-Item` cmdlet, allowing the user to move items from one location to another.</span></span> <span data-ttu-id="5e44d-118">이 샘플에서는 cmdlet에 동적 매개 변수를 추가 하는 방법을 보여 주지 않습니다 `Move-Item` .</span><span class="sxs-lookup"><span data-stu-id="5e44d-118">(This sample does not show how to add dynamic parameters to the `Move-Item` cmdlet.)</span></span>

- <span data-ttu-id="5e44d-119">Cmdlet의 동작을 변경 하는 메서드를 덮어쓰는 중입니다 [. Makepath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) 메서드를 덮어씁니다. `Join-Path`</span><span class="sxs-lookup"><span data-stu-id="5e44d-119">Overwriting the [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) method to change the behavior of the `Join-Path` cmdlet.</span></span>

- <span data-ttu-id="5e44d-120">System.object를 덮어씁니다. [Isitemcontainer \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) 메서드를 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="5e44d-120">Overwriting the [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) method.</span></span>

- <span data-ttu-id="5e44d-121">System.object를 덮어씁니다. [Getchildname \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) 메서드를 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="5e44d-121">Overwriting the [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) method.</span></span>

- <span data-ttu-id="5e44d-122">System.object를 덮어씁니다. [Getparentpath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) 메서드를 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="5e44d-122">Overwriting the [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) method.</span></span>

- <span data-ttu-id="5e44d-123">System.object를 덮어씁니다. [Normalizerelativepath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) 메서드를 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="5e44d-123">Overwriting the [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) method.</span></span>

## <a name="example"></a><span data-ttu-id="5e44d-124">예제</span><span class="sxs-lookup"><span data-stu-id="5e44d-124">Example</span></span>

<span data-ttu-id="5e44d-125">이 샘플에서는 Microsoft Access 데이터 베이스에서 항목을 이동 하는 데 필요한 메서드를 덮어쓰는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5e44d-125">This sample shows how to overwrite the methods needed to move items in a Microsoft Access data base.</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample05/AccessDBProviderSample05.cs" range="11-1960":::

## <a name="see-also"></a><span data-ttu-id="5e44d-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5e44d-126">See Also</span></span>

[<span data-ttu-id="5e44d-127">System.object.. i n g.</span><span class="sxs-lookup"><span data-stu-id="5e44d-127">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="5e44d-128">Containercmdletprovider입니다.</span><span class="sxs-lookup"><span data-stu-id="5e44d-128">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="5e44d-129">System.object.. i n.</span><span class="sxs-lookup"><span data-stu-id="5e44d-129">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="5e44d-130">Windows PowerShell 공급자 설계</span><span class="sxs-lookup"><span data-stu-id="5e44d-130">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)
