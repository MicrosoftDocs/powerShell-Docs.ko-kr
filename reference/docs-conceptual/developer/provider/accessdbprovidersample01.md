---
title: AccessDBProviderSample01 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 50ec218e8d0fe6b2be5c8ac00956f72c6723f84a
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786920"
---
# <a name="accessdbprovidersample01"></a><span data-ttu-id="fda59-102">AccessDBProviderSample01</span><span class="sxs-lookup"><span data-stu-id="fda59-102">AccessDBProviderSample01</span></span>

<span data-ttu-id="fda59-103">이 샘플에서는 [system.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) 클래스에서 직접 파생 되는 공급자 클래스를 선언 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="fda59-103">This sample shows how to declare a provider class that derives directly from the [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) class.</span></span> <span data-ttu-id="fda59-104">여기서는 참조용으로만 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="fda59-104">It is included here only for completeness.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="fda59-105">데모</span><span class="sxs-lookup"><span data-stu-id="fda59-105">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fda59-106">공급자 클래스는 다음 클래스 중 하나에서 파생 되 고 다른 공급자 인터페이스를 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fda59-106">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> - <span data-ttu-id="fda59-107">[System.object. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="fda59-107">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span> <span data-ttu-id="fda59-108">[AccessDBProviderSample03](./accessdbprovidersample03.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="fda59-108">See [AccessDBProviderSample03](./accessdbprovidersample03.md).</span></span>
> - <span data-ttu-id="fda59-109">[Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) 클래스를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="fda59-109">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="fda59-110">[AccessDBProviderSample04](./accessdbprovidersample04.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="fda59-110">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> - <span data-ttu-id="fda59-111">[System.object](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 클래스를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="fda59-111">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span> <span data-ttu-id="fda59-112">[AccessDBProviderSample05](./accessdbprovidersample05.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="fda59-112">See [AccessDBProviderSample05](./accessdbprovidersample05.md).</span></span>
>
> <span data-ttu-id="fda59-113">공급자 기능을 기반으로 파생 시킬 공급자 클래스를 선택 하는 방법에 대 한 자세한 내용은 [Windows PowerShell 공급자 디자인](./provider-types.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="fda59-113">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="fda59-114">이 샘플은 다음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="fda59-114">This sample demonstrates the following:</span></span>

- <span data-ttu-id="fda59-115">특성 선언 `CmdletProvider`</span><span class="sxs-lookup"><span data-stu-id="fda59-115">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="fda59-116">[System.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) 클래스에서 직접 파생 되는 공급자 클래스를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="fda59-116">Defining a provider class that derives directly from the [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) class.</span></span>

## <a name="example"></a><span data-ttu-id="fda59-117">예제</span><span class="sxs-lookup"><span data-stu-id="fda59-117">Example</span></span>

<span data-ttu-id="fda59-118">이 샘플에서는 공급자 클래스를 정의 하는 방법과 특성을 선언 하는 방법을 보여 줍니다 `CmdletProvider` .</span><span class="sxs-lookup"><span data-stu-id="fda59-118">This sample shows how to define a provider class and how to declare the `CmdletProvider` attribute.</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs" range="11-30":::

## <a name="see-also"></a><span data-ttu-id="fda59-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fda59-119">See Also</span></span>

[<span data-ttu-id="fda59-120">System.object.. i n g.</span><span class="sxs-lookup"><span data-stu-id="fda59-120">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="fda59-121">Containercmdletprovider입니다.</span><span class="sxs-lookup"><span data-stu-id="fda59-121">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="fda59-122">System.object.. i n.</span><span class="sxs-lookup"><span data-stu-id="fda59-122">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="fda59-123">Windows PowerShell 공급자 설계</span><span class="sxs-lookup"><span data-stu-id="fda59-123">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)
