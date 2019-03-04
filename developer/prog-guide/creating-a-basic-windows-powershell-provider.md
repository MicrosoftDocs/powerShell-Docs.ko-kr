---
title: 기본 Windows PowerShell 공급자 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- base provider [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], base provider
ms.assetid: 11eeea41-15c8-47ad-9016-0f4b72573305
caps.latest.revision: 7
ms.openlocfilehash: 19cc3817016d96e1412a5f3506e9d694ba55b48d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861769"
---
# <a name="creating-a-basic-windows-powershell-provider"></a><span data-ttu-id="95591-102">기본 Windows PowerShell 공급자 만들기</span><span class="sxs-lookup"><span data-stu-id="95591-102">Creating a Basic Windows PowerShell Provider</span></span>

<span data-ttu-id="95591-103">이 항목은 Windows PowerShell 공급자를 만드는 방법을 학습 하기 위한 시작 지점입니다.</span><span class="sxs-lookup"><span data-stu-id="95591-103">This topic is the starting point for learning how to create a Windows PowerShell provider.</span></span> <span data-ttu-id="95591-104">여기에 설명 된 기본 공급자를 시작 및 중지를 공급자에 대 한 메서드를 제공 하 고이 공급자는 데이터 저장소에 액세스 하려면 또는 가져오기 또는 데이터 저장소에서 데이터를 설정 하는 수단을 제공 하지 않습니다., 하지만에 필요한 기본 기능을 제공지 않습니다. 모든 공급자입니다.</span><span class="sxs-lookup"><span data-stu-id="95591-104">The basic provider described here provides methods for starting and stopping the provider, and although this provider does not provide a means to access a data store or to get or set the data in the data store, it does provide the basic functionality that is required by all providers.</span></span>

<span data-ttu-id="95591-105">이전에 설명 된 기본 공급자를 설명한 것 처럼 여기 시작 및 중지 공급자에 대 한 메서드를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="95591-105">As mentioned previously, the basic provider described here implements methods for starting and stopping the provider.</span></span> <span data-ttu-id="95591-106">Windows PowerShell 런타임을 초기화 하 고 공급자를 초기화 합니다. 이러한 메서드를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="95591-106">The Windows PowerShell runtime calls these methods to initialize and uninitialize the provider.</span></span>

> [!NOTE]
> <span data-ttu-id="95591-107">Windows PowerShell에서 제공 되는 AccessDBSampleProvider01.cs 파일에서이 공급자의 샘플을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95591-107">You can find a sample of this provider in the AccessDBSampleProvider01.cs file provided by Windows PowerShell.</span></span>

<span data-ttu-id="95591-108">이 항목의 섹션은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="95591-108">The sections in this topic include the following:</span></span>

- [<span data-ttu-id="95591-109">Windows PowerShell 공급자 클래스를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="95591-109">Defining the Windows PowerShell Provider Class</span></span>](#Defining-the-Windows-PowerShell-Provider-Class)

- [<span data-ttu-id="95591-110">공급자 관련 상태 정보를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="95591-110">Defining Provider-Specific State Information</span></span>](#Defining-Provider-Specific-State-Information)

- [<span data-ttu-id="95591-111">공급자를 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="95591-111">Initializing the Provider</span></span>](#Initializing-the-Provider)

- [<span data-ttu-id="95591-112">동적 매개 변수를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="95591-112">Start Dynamic Parameters</span></span>](#Start-Dynamic-Parameters)

- [<span data-ttu-id="95591-113">공급자 초기화 취소</span><span class="sxs-lookup"><span data-stu-id="95591-113">Uninitializing the Provider</span></span>](#Uninitializing-the-Provider)

- [<span data-ttu-id="95591-114">코드 샘플</span><span class="sxs-lookup"><span data-stu-id="95591-114">Code Sample</span></span>](#Code-Sample)

- [<span data-ttu-id="95591-115">Windows PowerShell 공급자 테스트</span><span class="sxs-lookup"><span data-stu-id="95591-115">Testing the Windows PowerShell Provider</span></span>](#Testing-the-Windows-PowerShell-Provider)

## <a name="defining-the-windows-powershell-provider-class"></a><span data-ttu-id="95591-116">Windows PowerShell 공급자 클래스를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="95591-116">Defining the Windows PowerShell Provider Class</span></span>

<span data-ttu-id="95591-117">Windows PowerShell 공급자를 만드는 첫 번째 단계는 해당.NET 클래스를 정의 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="95591-117">The first step in creating a Windows PowerShell provider is to define its .NET class.</span></span> <span data-ttu-id="95591-118">이 기본 공급자 라는 클래스를 정의 `AccessDBProvider` 에서 파생 되는 [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) 기본 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="95591-118">This basic provider defines a class called `AccessDBProvider` that derives from the [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) base class.</span></span>

<span data-ttu-id="95591-119">공급자 클래스를 배치 하는 것이 좋습니다는 `Providers` xxx 예를 들어 API 네임 스페이스의 네임 스페이스입니다. PowerShell.Providers 합니다.</span><span class="sxs-lookup"><span data-stu-id="95591-119">It is recommended that you place your provider classes in a `Providers` namespace of your API namespace, for example, xxx.PowerShell.Providers.</span></span> <span data-ttu-id="95591-120">이 공급자가 사용 하 여 `Microsoft.Samples.PowerShell.Provider` 네임 스페이스에 있는 모든 Windows PowerShell 공급자 샘플을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="95591-120">This provider uses the `Microsoft.Samples.PowerShell.Provider` namespace, in which all Windows PowerShell provider samples run.</span></span>

> [!NOTE]
> <span data-ttu-id="95591-121">Windows PowerShell 공급자에 대 한 클래스 해야 명시적으로 공용으로 표시 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="95591-121">The class for a Windows PowerShell provider must be explicitly marked as public.</span></span> <span data-ttu-id="95591-122">공용으로 표시 되지 않은 클래스는 기본적으로 내부 및 Windows PowerShell 런타임에 의해 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="95591-122">Classes not marked as public will default to internal and will not be found by the Windows PowerShell runtime.</span></span>

<span data-ttu-id="95591-123">이 기본 공급자에 대 한 클래스 정의 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="95591-123">Here is the class definition for this basic provider:</span></span>

[!code-csharp[AccessDBProviderSample01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs#L23-L24 "AccessDBProviderSample01.cs")]

<span data-ttu-id="95591-124">클래스 정의 직전 선언 해야 합니다 [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) [CmdletProvider()] 구문 사용 하 여 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="95591-124">Right before the class definition, you must declare the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attribute, with the syntax [CmdletProvider()].</span></span>

<span data-ttu-id="95591-125">필요한 경우 추가 클래스를 선언 하려면 키워드 특성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95591-125">You can set attribute keywords to further declare the class if necessary.</span></span> <span data-ttu-id="95591-126">다음에 유의 합니다 [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) 여기에 선언 된 특성에는 두 매개 변수가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="95591-126">Notice that the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attribute declared here includes two parameters.</span></span> <span data-ttu-id="95591-127">첫 번째 특성 매개 변수는 사용자가 나중에 수정할 수 있는 공급자에 대 한 기본 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="95591-127">The first attribute parameter specifies the default-friendly name for the provider, which the user can modify later.</span></span> <span data-ttu-id="95591-128">두 번째 매개 변수는 명령 처리 하는 동안 공급자가 Windows PowerShell 런타임에 노출 하는 Windows PowerShell 정의 기능을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="95591-128">The second parameter specifies the Windows PowerShell-defined capabilities that the provider exposes to the Windows PowerShell runtime during command processing.</span></span> <span data-ttu-id="95591-129">공급자 기능에 대 한 가능한 값은 정의한 합니다 [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) 열거형입니다.</span><span class="sxs-lookup"><span data-stu-id="95591-129">The possible values for the provider capabilities are defined by the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="95591-130">기본 공급자 이기 때문에 없는 기능을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="95591-130">Because this is a base provider, it supports no capabilities.</span></span>

> [!NOTE]
> <span data-ttu-id="95591-131">Windows PowerShell 공급자의 정규화 된 이름을 어셈블리 이름 및 공급자를 등록 하면 Windows PowerShell에서 결정 하는 다른 특성을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="95591-131">The fully qualified name of the Windows PowerShell provider includes the assembly name and other attributes determined by Windows PowerShell upon registration of the provider.</span></span>

## <a name="defining-provider-specific-state-information"></a><span data-ttu-id="95591-132">공급자 관련 상태 정보를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="95591-132">Defining Provider-Specific State Information</span></span>

<span data-ttu-id="95591-133">합니다 [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) 기본 클래스와 모든 파생된 클래스는 상태 비저장으로 간주 되므로 Windows PowerShell 런타임에 필요한 만큼만 공급자 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="95591-133">The [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) base class and all derived classes are considered stateless because the Windows PowerShell runtime creates provider instances only as required.</span></span> <span data-ttu-id="95591-134">따라서 공급자에 게 완전 한 제어 및 상태 유지 관리 공급자 관련 데이터에 필요한 경우 클래스에서 파생 되어야 합니다는 [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="95591-134">Therefore, if your provider requires full control and state maintenance for provider-specific data, it must derive a class from the [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) class.</span></span> <span data-ttu-id="95591-135">파생된 클래스는 Windows PowerShell 런타임에 호출 하는 경우 공급자 특정 데이터에 액세스할 수 있도록 상태를 유지 하는 데 필요한 멤버를 정의 해야 합니다 [System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) 공급자를 초기화 하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="95591-135">Your derived class should define the members necessary to maintain the state so that the provider-specific data can be accessed when the Windows PowerShell runtime calls the [System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) method to initialize the provider.</span></span>

<span data-ttu-id="95591-136">Windows PowerShell 공급자는 연결 기반 상태를 유지할 수도 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95591-136">A Windows PowerShell provider can also maintain connection-based state.</span></span> <span data-ttu-id="95591-137">연결 상태를 유지 하는 방법에 대 한 자세한 내용은 참조 하세요. [PowerShell 드라이브 공급자 만들기](./creating-a-windows-powershell-drive-provider.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="95591-137">For more information about maintaining connection state, see [Creating a PowerShell Drive Provider](./creating-a-windows-powershell-drive-provider.md).</span></span>

## <a name="initializing-the-provider"></a><span data-ttu-id="95591-138">공급자를 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="95591-138">Initializing the Provider</span></span>

<span data-ttu-id="95591-139">Windows PowerShell 런타임 호출 공급자를 초기화 합니다 [System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) Windows PowerShell이 시작 될 때 메서드.</span><span class="sxs-lookup"><span data-stu-id="95591-139">To initialize the provider, the Windows PowerShell runtime calls the [System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) method when Windows PowerShell is started.</span></span> <span data-ttu-id="95591-140">공급자 단순히 반환 하는이 메서드의 기본 구현은 사용 하는 대부분의 경우는 [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) 공급자를 설명 하는 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="95591-140">For the most part, your provider can use the default implementation of this method, which simply returns the [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) object that describes your provider.</span></span> <span data-ttu-id="95591-141">그러나 추가 초기화 정보를 추가 하려는 경우 구현 해야 사용자 고유의 [System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) 합니다 의수정된된버전을반환하는메서드[ System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) 공급자에 전달 되는 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="95591-141">However, in the case where you want to add additional initialization information, you should implement your own [System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) method that returns a modified version of the [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) object that is passed to your provider.</span></span> <span data-ttu-id="95591-142">일반적으로이 메서드는 제공 된 반환할지 [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) 개체 또는 수정 된 전달할 [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) 개체 다른 초기화 정보를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="95591-142">In general, this method should return the provided [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) object passed to it or a modified [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) object that contains other initialization information.</span></span>

<span data-ttu-id="95591-143">이 기본 공급자는이 메서드를 재정의 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="95591-143">This basic provider does not override this method.</span></span> <span data-ttu-id="95591-144">그러나 다음 코드는이 메서드의 기본 구현을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="95591-144">However, the following code shows the default implementation of this method:</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderStart](Msh_samplesaccessdbprov01#accessdbprov01ProviderStart)]  -->

<span data-ttu-id="95591-145">에 설명 된 대로 공급자의 공급자별 정보 상태를 유지 관리할 수 있습니다 [정의 공급자별 데이터 상태](#Defining-Provider-Specific-State-Information)합니다.</span><span class="sxs-lookup"><span data-stu-id="95591-145">The provider can maintain the state of provider-specific information as described in [Defining Provider-specific Data State](#Defining-Provider-Specific-State-Information).</span></span> <span data-ttu-id="95591-146">이 경우 구현 재정의 해야 합니다 [System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) 파생된 클래스의 인스턴스를 반환 하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="95591-146">In this case, your implementation must override the [System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) method to return an instance of the derived class.</span></span>

## <a name="start-dynamic-parameters"></a><span data-ttu-id="95591-147">동적 매개 변수를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="95591-147">Start Dynamic Parameters</span></span>

<span data-ttu-id="95591-148">공급자 구현 된 [System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) 메서드 추가 매개 변수가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="95591-148">Your provider implementation of the [System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) method might require additional parameters.</span></span> <span data-ttu-id="95591-149">이 경우 공급자를 재정의 해야 합니다 [System.Management.Automation.Provider.Cmdletprovider.Startdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.StartDynamicParameters) 메서드와 반환 된 속성 및 필드를 구문 분석 하는 개체 특성 비슷합니다는 cmdlet 클래스 또는 [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="95591-149">In this case, the provider should override the [System.Management.Automation.Provider.Cmdletprovider.Startdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.StartDynamicParameters) method and return an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span>

<span data-ttu-id="95591-150">이 기본 공급자는이 메서드를 재정의 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="95591-150">This basic provider does not override this method.</span></span> <span data-ttu-id="95591-151">그러나 다음 코드는이 메서드의 기본 구현을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="95591-151">However, the following code shows the default implementation of this method:</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderDynamicParameters](Msh_samplesaccessdbprov01#accessdbprov01ProviderDynamicParameters)]  -->

## <a name="uninitializing-the-provider"></a><span data-ttu-id="95591-152">공급자 초기화 취소</span><span class="sxs-lookup"><span data-stu-id="95591-152">Uninitializing the Provider</span></span>

<span data-ttu-id="95591-153">Windows PowerShell 공급자를 사용 하는 리소스를 확보 하기 위해 공급자에 구현 해야 자체 [System.Management.Automation.Provider.Cmdletprovider.Stop\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Stop) 메서드.</span><span class="sxs-lookup"><span data-stu-id="95591-153">To free resources that the Windows PowerShell provider uses, your provider should implement its own [System.Management.Automation.Provider.Cmdletprovider.Stop\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Stop) method.</span></span> <span data-ttu-id="95591-154">이 메서드는 세션을 종료할 때 공급자 초기화를 취소 하려면 Windows PowerShell 런타임에 의해 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="95591-154">This method is called by the Windows PowerShell runtime to uninitialize the provider at the close of a session.</span></span>

<span data-ttu-id="95591-155">이 기본 공급자는이 메서드를 재정의 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="95591-155">This basic provider does not override this method.</span></span> <span data-ttu-id="95591-156">그러나 다음 코드는이 메서드의 기본 구현을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="95591-156">However, the following code shows the default implementation of this method:</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderStop](Msh_samplesaccessdbprov01#accessdbprov01ProviderStop)]  -->

## <a name="code-sample"></a><span data-ttu-id="95591-157">코드 예제</span><span class="sxs-lookup"><span data-stu-id="95591-157">Code Sample</span></span>

<span data-ttu-id="95591-158">전체 샘플 코드를 보려면 [AccessDbProviderSample01 코드 샘플](./accessdbprovidersample01-code-sample.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="95591-158">For complete sample code, see [AccessDbProviderSample01 Code Sample](./accessdbprovidersample01-code-sample.md).</span></span>

## <a name="testing-the-windows-powershell-provider"></a><span data-ttu-id="95591-159">Windows PowerShell 공급자 테스트</span><span class="sxs-lookup"><span data-stu-id="95591-159">Testing the Windows PowerShell Provider</span></span>

<span data-ttu-id="95591-160">Windows PowerShell을 사용 하 여 Windows PowerShell 공급자가 등록 되 면 명령줄에서 지원 되는 cmdlet을 실행 하 여 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95591-160">Once your Windows PowerShell provider has been registered with Windows PowerShell, you can test it by running the supported cmdlets on the command line.</span></span> <span data-ttu-id="95591-161">이 기본 공급자에 대 한 새 셸을 실행 하 고 사용 된 `Get-PSProvider` cmdlet 공급자 목록을 가져와 AccessDb 공급자 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="95591-161">For this basic provider, run the new shell and use the `Get-PSProvider` cmdlet to retrieve the list of providers and ensure that the AccessDb provider is present.</span></span>

```powershell
Get-PSProvider
```

<span data-ttu-id="95591-162">다음과 같은 출력이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="95591-162">The following output appears:</span></span>

```output
Name                 Capabilities                  Drives
----                 ------------                  ------
AccessDb             None                          {}
Alias                ShouldProcess                 {Alias}
Environment          ShouldProcess                 {Env}
FileSystem           Filter, ShouldProcess         {C, Z}
Function             ShouldProcess                 {function}
Registry             ShouldProcess                 {HKLM, HKCU}
```

## <a name="see-also"></a><span data-ttu-id="95591-163">참고 항목</span><span class="sxs-lookup"><span data-stu-id="95591-163">See Also</span></span>

[<span data-ttu-id="95591-164">Windows PowerShell 공급자 만들기</span><span class="sxs-lookup"><span data-stu-id="95591-164">Creating Windows PowerShell Providers</span></span>](./how-to-create-a-windows-powershell-provider.md)

[<span data-ttu-id="95591-165">Windows PowerShell 공급자를 디자인합니다.</span><span class="sxs-lookup"><span data-stu-id="95591-165">Designing Your Windows PowerShell Provider</span></span>](./designing-your-windows-powershell-provider.md)