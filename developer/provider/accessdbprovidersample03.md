---
title: AccessDBProviderSample03 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9e576199-49c7-4355-9686-f9ed40c64a5f
caps.latest.revision: 10
ms.openlocfilehash: 57b6cfaa5f29300c60a5a745797111b6beba3133
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081073"
---
# <a name="accessdbprovidersample03"></a><span data-ttu-id="2f1ad-102">AccessDBProviderSample03</span><span class="sxs-lookup"><span data-stu-id="2f1ad-102">AccessDBProviderSample03</span></span>

<span data-ttu-id="2f1ad-103">이 샘플에서는를 덮어쓰는 방법을 보여 줍니다.는 [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) 하 고 [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) 메서드를 호출을 지원 합니다 `Get-Item` 및 `Set-Item` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2f1ad-103">This sample shows how to overwrite the [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) and [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) methods to support calls to the `Get-Item` and `Set-Item` cmdlets.</span></span> <span data-ttu-id="2f1ad-104">이 샘플의 공급자 클래스에서 파생 된 [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="2f1ad-104">The provider class in this sample derives from the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="2f1ad-105">데모</span><span class="sxs-lookup"><span data-stu-id="2f1ad-105">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2f1ad-106">공급자 클래스는 대부분 다음 클래스 중 하나에서 파생 되며 다른 공급자 인터페이스를 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f1ad-106">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> -   <span data-ttu-id="2f1ad-107">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span><span class="sxs-lookup"><span data-stu-id="2f1ad-107">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span>
> -   <span data-ttu-id="2f1ad-108">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span><span class="sxs-lookup"><span data-stu-id="2f1ad-108">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="2f1ad-109">참조 [AccessDBProviderSample04](./accessdbprovidersample04.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="2f1ad-109">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> -   <span data-ttu-id="2f1ad-110">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span><span class="sxs-lookup"><span data-stu-id="2f1ad-110">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span> <span data-ttu-id="2f1ad-111">참조 [AccessDBProviderSample05](./accessdbprovidersample05.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="2f1ad-111">See [AccessDBProviderSample05](./accessdbprovidersample05.md).</span></span>
>
> <span data-ttu-id="2f1ad-112">자세한 내용은 공급자 기능에 따라에서 파생 되는 공급자 클래스를 선택 하는 방법에 대 한 [Your Windows PowerShell 공급자 디자인](./provider-types.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="2f1ad-112">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="2f1ad-113">이 샘플에는 다음 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2f1ad-113">This sample demonstrates the following:</span></span>

- <span data-ttu-id="2f1ad-114">선언 된 `CmdletProvider` 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="2f1ad-114">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="2f1ad-115">파생 되는 공급자 클래스를 정의 합니다 [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="2f1ad-115">Defining a provider class that derives from the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span>

- <span data-ttu-id="2f1ad-116">덮어쓰지는 [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) 의 동작을 변경 하는 방법의 `New-PSDrive` cmdlet에 새 드라이브를 만들 수 있도록 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f1ad-116">Overwriting the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method to change the behavior of the `New-PSDrive` cmdlet, allowing the user to create new drives.</span></span> <span data-ttu-id="2f1ad-117">(이 샘플의 동적 매개 변수를 추가 하는 방법을 보여주지 않습니다는 `New-PSDrive` cmdlet입니다.)</span><span class="sxs-lookup"><span data-stu-id="2f1ad-117">(This sample does not show how to add dynamic parameters to the `New-PSDrive` cmdlet.)</span></span>

- <span data-ttu-id="2f1ad-118">덮어쓰기 합니다 [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) 지원 기존 드라이브를 제거 하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="2f1ad-118">Overwriting the [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method to support removing existing drives.</span></span>

- <span data-ttu-id="2f1ad-119">덮어쓰지는 [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) 의 동작을 변경 하는 방법의 `Get-Item` cmdlet, 사용자가 데이터 저장소에서 항목을 검색할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f1ad-119">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) method to change the behavior of the `Get-Item` cmdlet, allowing the user to retrieve items from the data store.</span></span> <span data-ttu-id="2f1ad-120">(이 샘플의 동적 매개 변수를 추가 하는 방법을 보여주지 않습니다는 `Get-Item` cmdlet입니다.)</span><span class="sxs-lookup"><span data-stu-id="2f1ad-120">(This sample does not show how to add dynamic parameters to the `Get-Item` cmdlet.)</span></span>

- <span data-ttu-id="2f1ad-121">덮어쓰기 합니다 [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) 의 동작을 변경 하는 방법의 `Set-Item` cmdlet, 사용자가 데이터 저장소에서 항목을 업데이트할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f1ad-121">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) method to change the behavior of the `Set-Item` cmdlet, allowing the user to update the items in the data store.</span></span> <span data-ttu-id="2f1ad-122">(이 샘플의 동적 매개 변수를 추가 하는 방법을 보여주지 않습니다는 `Get-Item` cmdlet입니다.)</span><span class="sxs-lookup"><span data-stu-id="2f1ad-122">(This sample does not show how to add dynamic parameters to the `Get-Item` cmdlet.)</span></span>

- <span data-ttu-id="2f1ad-123">덮어쓰기 합니다 [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) 의 동작을 변경 하는 방법의 `Test-Path` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2f1ad-123">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) method to change the behavior of the `Test-Path` cmdlet.</span></span> <span data-ttu-id="2f1ad-124">(이 샘플의 동적 매개 변수를 추가 하는 방법을 보여주지 않습니다는 `Test-Path` cmdlet입니다.)</span><span class="sxs-lookup"><span data-stu-id="2f1ad-124">(This sample does not show how to add dynamic parameters to the `Test-Path` cmdlet.)</span></span>

- <span data-ttu-id="2f1ad-125">덮어쓰기 합니다 [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) 메서드를 제공 된 경로가 유효한 지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f1ad-125">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) method to determine if the provided path is valid.</span></span>

## <a name="example"></a><span data-ttu-id="2f1ad-126">예제</span><span class="sxs-lookup"><span data-stu-id="2f1ad-126">Example</span></span>

<span data-ttu-id="2f1ad-127">이 예제를 가져오고 Microsoft Access 데이터에서 항목을 기본 설정 하는 데 필요한 메서드를 덮어쓰는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2f1ad-127">This sample shows how to overwrite the methods needed to get and set items in a Microsoft Access data base.</span></span>

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L976 "AccessDBProviderSample03.cs")]

## <a name="see-also"></a><span data-ttu-id="2f1ad-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2f1ad-128">See Also</span></span>

[<span data-ttu-id="2f1ad-129">System.Management.Automation.Provider.Itemcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="2f1ad-129">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="2f1ad-130">System.Management.Automation.Provider.Containercmdletprovider</span><span class="sxs-lookup"><span data-stu-id="2f1ad-130">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="2f1ad-131">System.Management.Automation.Provider.Navigationcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="2f1ad-131">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="2f1ad-132">Windows PowerShell 공급자를 디자인합니다.</span><span class="sxs-lookup"><span data-stu-id="2f1ad-132">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)