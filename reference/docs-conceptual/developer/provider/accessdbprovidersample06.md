---
title: AccessDBProviderSample06 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 46dc0657-110f-4367-8bb6-a95dca2c5016
caps.latest.revision: 8
ms.openlocfilehash: 9c00ec6de987729fec42dc57245a949d11e31f4b
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366332"
---
# <a name="accessdbprovidersample06"></a><span data-ttu-id="00738-102">AccessDBProviderSample06</span><span class="sxs-lookup"><span data-stu-id="00738-102">AccessDBProviderSample06</span></span>

<span data-ttu-id="00738-103">이 샘플에서는 `Clear-Content`, `Get-Content` 및 `Set-Content` cmdlet에 대 한 호출을 지원 하도록 콘텐츠 메서드를 덮어쓰는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="00738-103">This sample shows how to overwrite content methods to support calls to the `Clear-Content`, `Get-Content`, and `Set-Content` cmdlets.</span></span> <span data-ttu-id="00738-104">이러한 메서드는 사용자가 데이터 저장소에 있는 항목의 콘텐츠를 관리해야 하는 경우에 구현해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="00738-104">These methods should be implemented when the user needs to manage the content of the items in the data store.</span></span> <span data-ttu-id="00738-105">이 샘플의 공급자 클래스는 [Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) 인터페이스를 구현 하는 클래스에서 파생 되며, [이 클래스는](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) system.object를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="00738-105">The provider class in this sample derives from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class, and it implements the [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="00738-106">보여</span><span class="sxs-lookup"><span data-stu-id="00738-106">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="00738-107">공급자 클래스는 다음 클래스 중 하나에서 파생 되 고 다른 공급자 인터페이스를 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00738-107">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> -   <span data-ttu-id="00738-108">[System.object. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="00738-108">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span> <span data-ttu-id="00738-109">[AccessDBProviderSample03](./accessdbprovidersample03.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="00738-109">See [AccessDBProviderSample03](./accessdbprovidersample03.md).</span></span>
> -   <span data-ttu-id="00738-110">[Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) 클래스를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="00738-110">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="00738-111">[AccessDBProviderSample04](./accessdbprovidersample04.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="00738-111">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> -   <span data-ttu-id="00738-112">[System.object](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 클래스를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="00738-112">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>
>
> <span data-ttu-id="00738-113">공급자 기능을 기반으로 파생 시킬 공급자 클래스를 선택 하는 방법에 대 한 자세한 내용은 [Windows PowerShell 공급자 디자인](./provider-types.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="00738-113">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="00738-114">이 샘플은 다음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="00738-114">This sample demonstrates the following:</span></span>

- <span data-ttu-id="00738-115">@No__t_0 특성을 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="00738-115">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="00738-116">[Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) 인터페이스를 선언 하 고 system.object 클래스에서 파생 되는 [공급자 클래스를](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 정의 하는 것입니다 (.</span><span class="sxs-lookup"><span data-stu-id="00738-116">Defining a provider class that derives from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class and that declares the [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface.</span></span>

- <span data-ttu-id="00738-117">@No__t_1 cmdlet의 동작을 변경 하 여 사용자가 항목에서 콘텐츠를 제거할 수 있도록 하는 [Clearcontent \*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) 메서드를 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="00738-117">Overwriting the [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) method to change the behavior of the `Clear-Content` cmdlet, allowing the user to remove the content from an item.</span></span> <span data-ttu-id="00738-118">(이 샘플은 `Clear-Content` cmdlet에 동적 매개 변수를 추가 하는 방법을 보여 주지 않습니다.)</span><span class="sxs-lookup"><span data-stu-id="00738-118">(This sample does not show how to add dynamic parameters to the `Clear-Content` cmdlet.)</span></span>

- <span data-ttu-id="00738-119">@No__t_1 cmdlet의 동작을 변경 하 여 사용자가 항목의 콘텐츠를 검색할 수 있도록 하는 [Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) 메서드를 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="00738-119">Overwriting the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) method to change the behavior of the `Get-Content` cmdlet, allowing the user to retrieve the content of an item.</span></span> <span data-ttu-id="00738-120">(이 샘플은 `Get-Content` cmdlet에 동적 매개 변수를 추가 하는 방법을 보여 주지 않습니다.)</span><span class="sxs-lookup"><span data-stu-id="00738-120">(This sample does not show how to add dynamic parameters to the `Get-Content` cmdlet.).</span></span>

- <span data-ttu-id="00738-121">@No__t_1 cmdlet의 동작을 변경 하 여 사용자가 항목의 내용을 업데이트할 수 있도록 하는 [Filesystemprovider](/dotnet/api/Microsoft.PowerShell.Commands.FileSystemProvider.GetContentWriter) 메서드를 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="00738-121">Overwriting the [Microsoft.PowerShell.Commands.Filesystemprovider.Getcontentwriter\*](/dotnet/api/Microsoft.PowerShell.Commands.FileSystemProvider.GetContentWriter) method to change the behavior of the `Set-Content` cmdlet, allowing the user to update the content of an item.</span></span> <span data-ttu-id="00738-122">(이 샘플은 `Set-Content` cmdlet에 동적 매개 변수를 추가 하는 방법을 보여 주지 않습니다.)</span><span class="sxs-lookup"><span data-stu-id="00738-122">(This sample does not show how to add dynamic parameters to the `Set-Content` cmdlet.)</span></span>

## <a name="example"></a><span data-ttu-id="00738-123">예제</span><span class="sxs-lookup"><span data-stu-id="00738-123">Example</span></span>

<span data-ttu-id="00738-124">이 샘플에서는 Microsoft Access 데이터 베이스에서 항목의 내용을 지우고 가져오고 설정 하는 데 필요한 메서드를 덮어쓰는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="00738-124">This sample shows how to overwrite the methods needed to clear, get, and set the content of items in a Microsoft Access data base.</span></span>

[!code-csharp[AccessDBProviderSample06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L2399 "AccessDBProviderSample06.cs")]

## <a name="see-also"></a><span data-ttu-id="00738-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="00738-125">See Also</span></span>

[<span data-ttu-id="00738-126">System.object. i n g.</span><span class="sxs-lookup"><span data-stu-id="00738-126">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="00738-127">Containercmdletprovider입니다.</span><span class="sxs-lookup"><span data-stu-id="00738-127">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="00738-128">System.object. i n.</span><span class="sxs-lookup"><span data-stu-id="00738-128">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="00738-129">Windows PowerShell 공급자 디자인</span><span class="sxs-lookup"><span data-stu-id="00738-129">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)
