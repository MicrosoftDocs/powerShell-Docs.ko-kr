---
ms.date: 09/13/2016
ms.topic: reference
title: AccessDBProviderSample03
description: AccessDBProviderSample03
ms.openlocfilehash: bfd402903a9023b58dec8865663e3d649a50e1e1
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667405"
---
# <a name="accessdbprovidersample03"></a><span data-ttu-id="6af35-103">AccessDBProviderSample03</span><span class="sxs-lookup"><span data-stu-id="6af35-103">AccessDBProviderSample03</span></span>

<span data-ttu-id="6af35-104">이 샘플에서는 및 cmdlet에 대 한 호출을 지원 하기 위해 [Getitem \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) 및 [Setitem \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) 메서드를 덮어쓰는 방법을 보여 줍니다 .이 샘플은 `Get-Item` 및 cmdlet에 대 한 호출을 지원 합니다. `Set-Item`</span><span class="sxs-lookup"><span data-stu-id="6af35-104">This sample shows how to overwrite the [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) and [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) methods to support calls to the `Get-Item` and `Set-Item` cmdlets.</span></span> <span data-ttu-id="6af35-105">이 샘플의 공급자 클래스는 [system.web. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) 클래스에서 파생 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6af35-105">The provider class in this sample derives from the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="6af35-106">데모</span><span class="sxs-lookup"><span data-stu-id="6af35-106">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6af35-107">공급자 클래스는 다음 클래스 중 하나에서 파생 되 고 다른 공급자 인터페이스를 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6af35-107">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> - <span data-ttu-id="6af35-108">[System.object. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="6af35-108">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span>
> - <span data-ttu-id="6af35-109">[Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) 클래스를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="6af35-109">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="6af35-110">[AccessDBProviderSample04](./accessdbprovidersample04.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6af35-110">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> - <span data-ttu-id="6af35-111">[System.object](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 클래스를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="6af35-111">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span> <span data-ttu-id="6af35-112">[AccessDBProviderSample05](./accessdbprovidersample05.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6af35-112">See [AccessDBProviderSample05](./accessdbprovidersample05.md).</span></span>
>
> <span data-ttu-id="6af35-113">공급자 기능을 기반으로 파생 시킬 공급자 클래스를 선택 하는 방법에 대 한 자세한 내용은 [Windows PowerShell 공급자 디자인](./provider-types.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6af35-113">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="6af35-114">이 샘플은 다음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6af35-114">This sample demonstrates the following:</span></span>

- <span data-ttu-id="6af35-115">특성 선언 `CmdletProvider`</span><span class="sxs-lookup"><span data-stu-id="6af35-115">Declaring the `CmdletProvider` attribute.</span></span>
- <span data-ttu-id="6af35-116">[System.object](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) 클래스에서 파생 되는 공급자 클래스를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="6af35-116">Defining a provider class that derives from the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span>
- <span data-ttu-id="6af35-117">Cmdlet의 동작을 변경 하 여 사용자가 새 드라이브를 만들 수 있도록 하는 [Newdrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) 메서드를 덮어씁니다. `New-PSDrive`</span><span class="sxs-lookup"><span data-stu-id="6af35-117">Overwriting the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method to change the behavior of the `New-PSDrive` cmdlet, allowing the user to create new drives.</span></span>
  <span data-ttu-id="6af35-118">이 샘플에서는 cmdlet에 동적 매개 변수를 추가 하는 방법을 보여 주지 않습니다 `New-PSDrive` .</span><span class="sxs-lookup"><span data-stu-id="6af35-118">(This sample does not show how to add dynamic parameters to the `New-PSDrive` cmdlet.)</span></span>
- <span data-ttu-id="6af35-119">기존 드라이브 제거를 지원 하기 위해 [Removedrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) 메서드를 덮어씁니다 (영문).</span><span class="sxs-lookup"><span data-stu-id="6af35-119">Overwriting the [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method to support removing existing drives.</span></span>
- <span data-ttu-id="6af35-120">[Getitem \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) 메서드를 덮어써서 cmdlet의 동작을 변경 하 여 `Get-Item` 사용자가 데이터 저장소에서 항목을 검색할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="6af35-120">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) method to change the behavior of the `Get-Item` cmdlet, allowing the user to retrieve items from the data store.</span></span> <span data-ttu-id="6af35-121">이 샘플에서는 cmdlet에 동적 매개 변수를 추가 하는 방법을 보여 주지 않습니다 `Get-Item` .</span><span class="sxs-lookup"><span data-stu-id="6af35-121">(This sample does not show how to add dynamic parameters to the `Get-Item` cmdlet.)</span></span>
- <span data-ttu-id="6af35-122">[Setitem \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) 메서드를 덮어써서 cmdlet의 동작을 변경 하 여 `Set-Item` 사용자가 데이터 저장소의 항목을 업데이트할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="6af35-122">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) method to change the behavior of the `Set-Item` cmdlet, allowing the user to update the items in the data store.</span></span> <span data-ttu-id="6af35-123">이 샘플에서는 cmdlet에 동적 매개 변수를 추가 하는 방법을 보여 주지 않습니다 `Get-Item` .</span><span class="sxs-lookup"><span data-stu-id="6af35-123">(This sample does not show how to add dynamic parameters to the `Get-Item` cmdlet.)</span></span>
- <span data-ttu-id="6af35-124">Cmdlet의 동작을 변경 하기 위해 System.object를 덮어쓰는 중입니다 [. Itemexists \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) 메서드. `Test-Path`</span><span class="sxs-lookup"><span data-stu-id="6af35-124">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) method to change the behavior of the `Test-Path` cmdlet.</span></span> <span data-ttu-id="6af35-125">이 샘플에서는 cmdlet에 동적 매개 변수를 추가 하는 방법을 보여 주지 않습니다 `Test-Path` .</span><span class="sxs-lookup"><span data-stu-id="6af35-125">(This sample does not show how to add dynamic parameters to the `Test-Path` cmdlet.)</span></span>
- <span data-ttu-id="6af35-126">제공 된 경로가 유효한 지 여부를 확인 하기 위해 [system.web. Itemcmdletprovider. Isvalid path \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) 메서드를 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="6af35-126">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) method to determine if the provided path is valid.</span></span>

## <a name="example"></a><span data-ttu-id="6af35-127">예제</span><span class="sxs-lookup"><span data-stu-id="6af35-127">Example</span></span>

<span data-ttu-id="6af35-128">이 샘플에서는 Microsoft Access 데이터 베이스에서 항목을 가져오고 설정 하는 데 필요한 메서드를 덮어쓰는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6af35-128">This sample shows how to overwrite the methods needed to get and set items in a Microsoft Access data base.</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs" range="11-976":::

## <a name="see-also"></a><span data-ttu-id="6af35-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6af35-129">See Also</span></span>

[<span data-ttu-id="6af35-130">System.object.. i n g.</span><span class="sxs-lookup"><span data-stu-id="6af35-130">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="6af35-131">Containercmdletprovider입니다.</span><span class="sxs-lookup"><span data-stu-id="6af35-131">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="6af35-132">System.object.. i n.</span><span class="sxs-lookup"><span data-stu-id="6af35-132">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="6af35-133">Windows PowerShell 공급자 설계</span><span class="sxs-lookup"><span data-stu-id="6af35-133">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)
