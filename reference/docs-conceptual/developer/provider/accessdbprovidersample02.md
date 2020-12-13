---
ms.date: 09/13/2016
ms.topic: reference
title: AccessDBProviderSample02
description: AccessDBProviderSample02
ms.openlocfilehash: ebba2381370cf73f1e39015990f81dc4fd6dd937
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667439"
---
# <a name="accessdbprovidersample02"></a><span data-ttu-id="11007-103">AccessDBProviderSample02</span><span class="sxs-lookup"><span data-stu-id="11007-103">AccessDBProviderSample02</span></span>

<span data-ttu-id="11007-104">이 샘플에서는 및 cmdlet에 대 한 호출을 지원 하기 위해 [Newdrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) 및 [Removedrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) 메서드를 덮어쓰는 방법을 보여 줍니다 .이 샘플은 및 cmdlet에 대 한 호출을 지원 `New-PSDrive` `Remove-PSDrive` 합니다.</span><span class="sxs-lookup"><span data-stu-id="11007-104">This sample shows how to overwrite the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) and [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) methods to support calls to the `New-PSDrive` and `Remove-PSDrive` cmdlets.</span></span> <span data-ttu-id="11007-105">이 샘플의 공급자 클래스는 [system.object](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) 에서 파생 된 공급자 클래스에서 파생 됩니다.</span><span class="sxs-lookup"><span data-stu-id="11007-105">The provider class in this sample derives from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="11007-106">데모</span><span class="sxs-lookup"><span data-stu-id="11007-106">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="11007-107">공급자 클래스는 다음 클래스 중 하나에서 파생 되 고 다른 공급자 인터페이스를 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11007-107">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> - <span data-ttu-id="11007-108">[System.object. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="11007-108">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span> <span data-ttu-id="11007-109">[AccessDBProviderSample03](./accessdbprovidersample03.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="11007-109">See [AccessDBProviderSample03](./accessdbprovidersample03.md).</span></span>
> - <span data-ttu-id="11007-110">[Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) 클래스를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="11007-110">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="11007-111">[AccessDBProviderSample04](./accessdbprovidersample04.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="11007-111">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> - <span data-ttu-id="11007-112">[System.object](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 클래스를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="11007-112">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span> <span data-ttu-id="11007-113">[AccessDBProviderSample05](./accessdbprovidersample05.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="11007-113">See [AccessDBProviderSample05](./accessdbprovidersample05.md).</span></span>
>
> <span data-ttu-id="11007-114">공급자 기능을 기반으로 파생 시킬 공급자 클래스를 선택 하는 방법에 대 한 자세한 내용은 [Windows PowerShell 공급자 디자인](./provider-types.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="11007-114">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="11007-115">이 샘플은 다음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="11007-115">This sample demonstrates the following:</span></span>

- <span data-ttu-id="11007-116">특성 선언 `CmdletProvider`</span><span class="sxs-lookup"><span data-stu-id="11007-116">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="11007-117">[System.object](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) 에서 구동 하는 공급자 클래스를 정의 합니다...</span><span class="sxs-lookup"><span data-stu-id="11007-117">Defining a provider class that drives from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class.</span></span>

- <span data-ttu-id="11007-118">새 드라이브 생성을 지원 하기 위해 [Newdrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) 메서드를 덮어씁니다 (영문).</span><span class="sxs-lookup"><span data-stu-id="11007-118">Overwriting the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method to support creating new drives.</span></span> <span data-ttu-id="11007-119">이 샘플에서는 cmdlet에 동적 매개 변수를 추가 하는 방법을 보여 주지 않습니다 `New-PSDrive` .</span><span class="sxs-lookup"><span data-stu-id="11007-119">(This sample does not show how to add dynamic parameters to the `New-PSDrive` cmdlet.)</span></span>

- <span data-ttu-id="11007-120">기존 드라이브 제거를 지원 하기 위해 [Removedrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) 메서드를 덮어씁니다 (영문).</span><span class="sxs-lookup"><span data-stu-id="11007-120">Overwriting the [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method to support removing existing drives.</span></span>

## <a name="example"></a><span data-ttu-id="11007-121">예제</span><span class="sxs-lookup"><span data-stu-id="11007-121">Example</span></span>

<span data-ttu-id="11007-122">이 샘플에서는 [Newdrive \* 및 \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) 및 [Removedrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) 메서드를 덮어쓰는 방법을 보여 줍니다 .이 샘플은를 설명 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11007-122">This sample shows how to overwrite the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) and [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) methods.</span></span> <span data-ttu-id="11007-123">이 샘플 공급자의 경우 드라이브를 만들 때 연결 정보는 개체에 저장 됩니다 `AccessDBPsDriveInfo` .</span><span class="sxs-lookup"><span data-stu-id="11007-123">For this sample provider, when a drive is created its connection information is stored in an `AccessDBPsDriveInfo` object.</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs" range="11-154":::

## <a name="see-also"></a><span data-ttu-id="11007-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="11007-124">See Also</span></span>

[<span data-ttu-id="11007-125">System.object.. i n g.</span><span class="sxs-lookup"><span data-stu-id="11007-125">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="11007-126">Containercmdletprovider입니다.</span><span class="sxs-lookup"><span data-stu-id="11007-126">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="11007-127">System.object.. i n.</span><span class="sxs-lookup"><span data-stu-id="11007-127">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="11007-128">Windows PowerShell 공급자 설계</span><span class="sxs-lookup"><span data-stu-id="11007-128">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)
