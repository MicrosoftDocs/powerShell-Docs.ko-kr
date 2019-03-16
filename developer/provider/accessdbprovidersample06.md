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
ms.openlocfilehash: f020f023f9a379ff8a610edb7d5dcfe207170394
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055549"
---
# <a name="accessdbprovidersample06"></a><span data-ttu-id="b8d5b-102">AccessDBProviderSample06</span><span class="sxs-lookup"><span data-stu-id="b8d5b-102">AccessDBProviderSample06</span></span>

<span data-ttu-id="b8d5b-103">이 샘플에 대 한 호출을 지원 하기 위해 콘텐츠 메서드를 덮어쓰는 방법을 보여 줍니다 합니다 `Clear-Content`, `Get-Content`, 및 `Set-Content` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b8d5b-103">This sample shows how to overwrite content methods to support calls to the `Clear-Content`, `Get-Content`, and `Set-Content` cmdlets.</span></span> <span data-ttu-id="b8d5b-104">이러한 메서드는 사용자가 데이터 저장소에 있는 항목의 콘텐츠를 관리해야 하는 경우에 구현해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8d5b-104">These methods should be implemented when the user needs to manage the content of the items in the data store.</span></span> <span data-ttu-id="b8d5b-105">이 샘플의 공급자 클래스에서 파생 되는 [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 클래스에 구현 된 [ System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) 인터페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="b8d5b-105">The provider class in this sample derives from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class, and it implements the [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="b8d5b-106">시연</span><span class="sxs-lookup"><span data-stu-id="b8d5b-106">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b8d5b-107">공급자 클래스는 대부분 다음 클래스 중 하나에서 파생 되며 다른 공급자 인터페이스를 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8d5b-107">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> -   <span data-ttu-id="b8d5b-108">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span><span class="sxs-lookup"><span data-stu-id="b8d5b-108">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span> <span data-ttu-id="b8d5b-109">참조 [AccessDBProviderSample03](./accessdbprovidersample03.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="b8d5b-109">See [AccessDBProviderSample03](./accessdbprovidersample03.md).</span></span>
> -   <span data-ttu-id="b8d5b-110">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span><span class="sxs-lookup"><span data-stu-id="b8d5b-110">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="b8d5b-111">참조 [AccessDBProviderSample04](./accessdbprovidersample04.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="b8d5b-111">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> -   <span data-ttu-id="b8d5b-112">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span><span class="sxs-lookup"><span data-stu-id="b8d5b-112">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>
>
> <span data-ttu-id="b8d5b-113">자세한 내용은 공급자 기능에 따라에서 파생 되는 공급자 클래스를 선택 하는 방법에 대 한 [Your Windows PowerShell 공급자 디자인](./provider-types.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="b8d5b-113">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="b8d5b-114">이 샘플에는 다음 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b8d5b-114">This sample demonstrates the following:</span></span>

- <span data-ttu-id="b8d5b-115">선언 된 `CmdletProvider` 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="b8d5b-115">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="b8d5b-116">파생 되는 공급자 클래스를 정의 합니다 [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 선언 클래스를 사용 하 여 [ System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) 인터페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="b8d5b-116">Defining a provider class that derives from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class and that declares the [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface.</span></span>

- <span data-ttu-id="b8d5b-117">덮어쓰기 합니다 [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) 의 동작을 변경 하는 방법의 `Clear-Content` cmdlet, 사용자가 항목에서 콘텐츠를 제거할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8d5b-117">Overwriting the [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) method to change the behavior of the `Clear-Content` cmdlet, allowing the user to remove the content from an item.</span></span> <span data-ttu-id="b8d5b-118">(이 샘플의 동적 매개 변수를 추가 하는 방법을 보여주지 않습니다는 `Clear-Content` cmdlet입니다.)</span><span class="sxs-lookup"><span data-stu-id="b8d5b-118">(This sample does not show how to add dynamic parameters to the `Clear-Content` cmdlet.)</span></span>

- <span data-ttu-id="b8d5b-119">덮어쓰기 합니다 [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) 의 동작을 변경 하는 방법의 `Get-Content` cmdlet, 사용자가 항목의 콘텐츠를 검색할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8d5b-119">Overwriting the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) method to change the behavior of the `Get-Content` cmdlet, allowing the user to retrieve the content of an item.</span></span> <span data-ttu-id="b8d5b-120">(이 샘플의 동적 매개 변수를 추가 하는 방법을 보여주지 않습니다는 `Get-Content` cmdlet입니다.).</span><span class="sxs-lookup"><span data-stu-id="b8d5b-120">(This sample does not show how to add dynamic parameters to the `Get-Content` cmdlet.).</span></span>

- <span data-ttu-id="b8d5b-121">덮어쓰기 합니다 [Microsoft.PowerShell.Commands.Filesystemprovider.Getcontentwriter\*](/dotnet/api/Microsoft.PowerShell.Commands.FileSystemProvider.GetContentWriter) 의 동작을 변경 하는 방법의 `Set-Content` cmdlet, 사용자가 항목의 콘텐츠를 업데이트할 수.</span><span class="sxs-lookup"><span data-stu-id="b8d5b-121">Overwriting the [Microsoft.PowerShell.Commands.Filesystemprovider.Getcontentwriter\*](/dotnet/api/Microsoft.PowerShell.Commands.FileSystemProvider.GetContentWriter) method to change the behavior of the `Set-Content` cmdlet, allowing the user to update the content of an item.</span></span> <span data-ttu-id="b8d5b-122">(이 샘플의 동적 매개 변수를 추가 하는 방법을 보여주지 않습니다는 `Set-Content` cmdlet입니다.)</span><span class="sxs-lookup"><span data-stu-id="b8d5b-122">(This sample does not show how to add dynamic parameters to the `Set-Content` cmdlet.)</span></span>

## <a name="example"></a><span data-ttu-id="b8d5b-123">예제</span><span class="sxs-lookup"><span data-stu-id="b8d5b-123">Example</span></span>

<span data-ttu-id="b8d5b-124">이 샘플의 선택을 취소 하 고, 가져오기 및 기본 Microsoft Access 데이터에서 항목의 콘텐츠를 설정 하는 데 필요한 메서드를 덮어쓰는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b8d5b-124">This sample shows how to overwrite the methods needed to clear, get, and set the content of items in a Microsoft Access data base.</span></span>

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L2399 "AccessDBProviderSample06.cs")]

## <a name="see-also"></a><span data-ttu-id="b8d5b-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b8d5b-125">See Also</span></span>

[<span data-ttu-id="b8d5b-126">System.Management.Automation.Provider.Itemcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="b8d5b-126">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="b8d5b-127">System.Management.Automation.Provider.Containercmdletprovider</span><span class="sxs-lookup"><span data-stu-id="b8d5b-127">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="b8d5b-128">System.Management.Automation.Provider.Navigationcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="b8d5b-128">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="b8d5b-129">Windows PowerShell 공급자를 디자인합니다.</span><span class="sxs-lookup"><span data-stu-id="b8d5b-129">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)