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
ms.openlocfilehash: e825581b96f0f33893b38f9f6499dd46a7bf38eb
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72360522"
---
# <a name="creating-a-basic-windows-powershell-provider"></a><span data-ttu-id="dd1fe-102">기본 Windows PowerShell 공급자 만들기</span><span class="sxs-lookup"><span data-stu-id="dd1fe-102">Creating a Basic Windows PowerShell Provider</span></span>

<span data-ttu-id="dd1fe-103">이 항목은 Windows PowerShell 공급자를 만드는 방법을 배우는 시작점입니다.</span><span class="sxs-lookup"><span data-stu-id="dd1fe-103">This topic is the starting point for learning how to create a Windows PowerShell provider.</span></span> <span data-ttu-id="dd1fe-104">여기서 설명 하는 기본 공급자는 공급자를 시작 하 고 중지 하는 방법을 제공 합니다 .이 공급자는 데이터 저장소에 액세스 하거나 데이터 저장소의 데이터를 가져오거나 설정 하는 방법을 제공 하지 않지만에 필요한 기본 기능을 제공 합니다. 모든 공급자.</span><span class="sxs-lookup"><span data-stu-id="dd1fe-104">The basic provider described here provides methods for starting and stopping the provider, and although this provider does not provide a means to access a data store or to get or set the data in the data store, it does provide the basic functionality that is required by all providers.</span></span>

<span data-ttu-id="dd1fe-105">앞에서 설명한 대로 여기에 설명 된 기본 공급자는 공급자를 시작 및 중지 하기 위한 메서드를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd1fe-105">As mentioned previously, the basic provider described here implements methods for starting and stopping the provider.</span></span> <span data-ttu-id="dd1fe-106">Windows PowerShell 런타임에서는 이러한 메서드를 호출 하 여 공급자를 초기화 하 고 초기화 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd1fe-106">The Windows PowerShell runtime calls these methods to initialize and uninitialize the provider.</span></span>

> [!NOTE]
> <span data-ttu-id="dd1fe-107">이 공급자의 샘플은 Windows PowerShell에서 제공 하는 AccessDBSampleProvider01.cs 파일에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd1fe-107">You can find a sample of this provider in the AccessDBSampleProvider01.cs file provided by Windows PowerShell.</span></span>

## <a name="defining-the-windows-powershell-provider-class"></a><span data-ttu-id="dd1fe-108">Windows PowerShell 공급자 클래스 정의</span><span class="sxs-lookup"><span data-stu-id="dd1fe-108">Defining the Windows PowerShell Provider Class</span></span>

<span data-ttu-id="dd1fe-109">Windows PowerShell 공급자를 만드는 첫 번째 단계는 해당 .NET 클래스를 정의 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="dd1fe-109">The first step in creating a Windows PowerShell provider is to define its .NET class.</span></span> <span data-ttu-id="dd1fe-110">이 기본 공급자는 System.object 클래스를 정의 합니다 .이 클래스는 [system.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) 의 기본 클래스에서 파생 되는 `AccessDBProvider` 클래스를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd1fe-110">This basic provider defines a class called `AccessDBProvider` that derives from the [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) base class.</span></span>

<span data-ttu-id="dd1fe-111">API 네임 스페이스의 `Providers` 네임 스페이스에 공급자 클래스를 추가 하는 것이 좋습니다 (예: xxx). PowerShell. 공급자.</span><span class="sxs-lookup"><span data-stu-id="dd1fe-111">It is recommended that you place your provider classes in a `Providers` namespace of your API namespace, for example, xxx.PowerShell.Providers.</span></span> <span data-ttu-id="dd1fe-112">이 공급자는 모든 Windows PowerShell 공급자 샘플이 실행 되는 `Microsoft.Samples.PowerShell.Provider` 네임 스페이스를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd1fe-112">This provider uses the `Microsoft.Samples.PowerShell.Provider` namespace, in which all Windows PowerShell provider samples run.</span></span>

> [!NOTE]
> <span data-ttu-id="dd1fe-113">Windows PowerShell 공급자에 대 한 클래스는 명시적으로 public으로 표시 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd1fe-113">The class for a Windows PowerShell provider must be explicitly marked as public.</span></span> <span data-ttu-id="dd1fe-114">Public으로 표시 되지 않은 클래스는 기본적으로 내부로 표시 되 고 Windows PowerShell 런타임에서 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="dd1fe-114">Classes not marked as public will default to internal and will not be found by the Windows PowerShell runtime.</span></span>

<span data-ttu-id="dd1fe-115">이 기본 공급자에 대 한 클래스 정의는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="dd1fe-115">Here is the class definition for this basic provider:</span></span>

[!code-csharp[AccessDBProviderSample01.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs#L23-L24 "AccessDBProviderSample01.cs")]

<span data-ttu-id="dd1fe-116">클래스 정의 바로 앞에 [CmdletProvider ()] 구문을 사용 하 여 [Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) 특성을 선언 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd1fe-116">Right before the class definition, you must declare the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attribute, with the syntax [CmdletProvider()].</span></span>

<span data-ttu-id="dd1fe-117">필요한 경우 특성 키워드를 설정 하 여 클래스를 추가로 선언할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd1fe-117">You can set attribute keywords to further declare the class if necessary.</span></span> <span data-ttu-id="dd1fe-118">여기에 선언 된 [Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) 특성에는 두 개의 매개 변수가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd1fe-118">Notice that the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attribute declared here includes two parameters.</span></span> <span data-ttu-id="dd1fe-119">첫 번째 특성 매개 변수는 사용자가 나중에 수정할 수 있는 공급자의 기본 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd1fe-119">The first attribute parameter specifies the default-friendly name for the provider, which the user can modify later.</span></span> <span data-ttu-id="dd1fe-120">두 번째 매개 변수는 명령을 처리 하는 동안 공급자가 Windows PowerShell 런타임에 노출 하는 Windows PowerShell 정의 기능을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd1fe-120">The second parameter specifies the Windows PowerShell-defined capabilities that the provider exposes to the Windows PowerShell runtime during command processing.</span></span> <span data-ttu-id="dd1fe-121">공급자 기능에 사용할 수 있는 값은 [system.web](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . x m m.</span><span class="sxs-lookup"><span data-stu-id="dd1fe-121">The possible values for the provider capabilities are defined by the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="dd1fe-122">이 공급자는 기본 공급자 이므로 기능을 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dd1fe-122">Because this is a base provider, it supports no capabilities.</span></span>

> [!NOTE]
> <span data-ttu-id="dd1fe-123">Windows PowerShell 공급자의 정규화 된 이름에는 공급자를 등록할 때 Windows PowerShell에서 결정 한 어셈블리 이름 및 기타 특성이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd1fe-123">The fully qualified name of the Windows PowerShell provider includes the assembly name and other attributes determined by Windows PowerShell upon registration of the provider.</span></span>

## <a name="defining-provider-specific-state-information"></a><span data-ttu-id="dd1fe-124">공급자별 상태 정보 정의</span><span class="sxs-lookup"><span data-stu-id="dd1fe-124">Defining Provider-Specific State Information</span></span>

<span data-ttu-id="dd1fe-125">Windows PowerShell 런타임이 필요한 경우에만 공급자 인스턴스를 만들기 때문에 [system.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) 및 모든 파생 클래스는 상태 비저장으로 간주 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd1fe-125">The [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) base class and all derived classes are considered stateless because the Windows PowerShell runtime creates provider instances only as required.</span></span> <span data-ttu-id="dd1fe-126">따라서 공급자에 게 공급자별 데이터에 대 한 모든 권한 및 상태 유지 관리가 필요한 경우 [Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) 클래스에서 클래스를 파생 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd1fe-126">Therefore, if your provider requires full control and state maintenance for provider-specific data, it must derive a class from the [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) class.</span></span> <span data-ttu-id="dd1fe-127">파생 된 클래스는 상태를 유지 관리 하는 데 필요한 멤버를 정의 해야 합니다. 이렇게 하면 Windows PowerShell 런타임에서 공급자를 초기화할 때 공급자 특정 데이터에 액세스할 수 [있습니다.](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start)</span><span class="sxs-lookup"><span data-stu-id="dd1fe-127">Your derived class should define the members necessary to maintain the state so that the provider-specific data can be accessed when the Windows PowerShell runtime calls the [System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) method to initialize the provider.</span></span>

<span data-ttu-id="dd1fe-128">Windows PowerShell 공급자는 연결 기반 상태를 유지할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd1fe-128">A Windows PowerShell provider can also maintain connection-based state.</span></span> <span data-ttu-id="dd1fe-129">연결 상태를 유지 관리 하는 방법에 대 한 자세한 내용은 [PowerShell 드라이브 공급자 만들기](./creating-a-windows-powershell-drive-provider.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="dd1fe-129">For more information about maintaining connection state, see [Creating a PowerShell Drive Provider](./creating-a-windows-powershell-drive-provider.md).</span></span>

## <a name="initializing-the-provider"></a><span data-ttu-id="dd1fe-130">공급자 초기화</span><span class="sxs-lookup"><span data-stu-id="dd1fe-130">Initializing the Provider</span></span>

<span data-ttu-id="dd1fe-131">Windows powershell이 시작 될 때 공급자를 초기화 하기 위해 Windows PowerShell 런타임에서는 [system.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) 를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd1fe-131">To initialize the provider, the Windows PowerShell runtime calls the [System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) method when Windows PowerShell is started.</span></span> <span data-ttu-id="dd1fe-132">대부분의 경우 공급자는이 메서드의 기본 구현을 사용할 수 있습니다 .이 메서드는 공급자를 설명 하는 [Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) 개체를 반환 하기만 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd1fe-132">For the most part, your provider can use the default implementation of this method, which simply returns the [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) object that describes your provider.</span></span> <span data-ttu-id="dd1fe-133">그러나 초기화 정보를 추가하려는 경우에는 수정된 버전의 [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo)를 반환하는 사용자 고유의 [System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start)공급자에게 전달되는 Providerinfo 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="dd1fe-133">However, in the case where you want to add additional initialization information, you should implement your own [System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) method that returns a modified version of the [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) object that is passed to your provider.</span></span> <span data-ttu-id="dd1fe-134">일반적으로이 메서드는 전달 된 [Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) 개체 또는 다른 초기화 정보를 포함 하는 수정 된 [Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) 개체를 반환 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd1fe-134">In general, this method should return the provided [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) object passed to it or a modified [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) object that contains other initialization information.</span></span>

<span data-ttu-id="dd1fe-135">이 기본 공급자는이 메서드를 재정의 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dd1fe-135">This basic provider does not override this method.</span></span> <span data-ttu-id="dd1fe-136">그러나 다음 코드는이 메서드의 기본 구현을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="dd1fe-136">However, the following code shows the default implementation of this method:</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderStart](Msh_samplesaccessdbprov01#accessdbprov01ProviderStart)]  -->

<span data-ttu-id="dd1fe-137">공급자는 공급자별 [데이터 상태 정의](#defining-provider-specific-state-information)에 설명 된 대로 공급자별 정보의 상태를 유지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd1fe-137">The provider can maintain the state of provider-specific information as described in [Defining Provider-specific Data State](#defining-provider-specific-state-information).</span></span> <span data-ttu-id="dd1fe-138">이 경우, 구현에서 파생 클래스의 인스턴스를 반환 하려면 System.object를 재정의 하 여 다시 [시작](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd1fe-138">In this case, your implementation must override the [System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) method to return an instance of the derived class.</span></span>

## <a name="start-dynamic-parameters"></a><span data-ttu-id="dd1fe-139">동적 매개 변수 시작</span><span class="sxs-lookup"><span data-stu-id="dd1fe-139">Start Dynamic Parameters</span></span>

<span data-ttu-id="dd1fe-140">공급자를 구현 [하는 경우](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) 에는 추가 매개 변수가 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd1fe-140">Your provider implementation of the [System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) method might require additional parameters.</span></span> <span data-ttu-id="dd1fe-141">이 경우 공급자는 [system.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.StartDynamicParameters) 를 재정의 하 고 cmdlet 클래스 또는 [Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 개체와 유사한 구문 분석 특성을 가진 속성 및 필드가 있는 개체를 반환 해야 하는 경우를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd1fe-141">In this case, the provider should override the [System.Management.Automation.Provider.Cmdletprovider.Startdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.StartDynamicParameters) method and return an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span>

<span data-ttu-id="dd1fe-142">이 기본 공급자는이 메서드를 재정의 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dd1fe-142">This basic provider does not override this method.</span></span> <span data-ttu-id="dd1fe-143">그러나 다음 코드는이 메서드의 기본 구현을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="dd1fe-143">However, the following code shows the default implementation of this method:</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderDynamicParameters](Msh_samplesaccessdbprov01#accessdbprov01ProviderDynamicParameters)]  -->

## <a name="uninitializing-the-provider"></a><span data-ttu-id="dd1fe-144">공급자 초기화</span><span class="sxs-lookup"><span data-stu-id="dd1fe-144">Uninitializing the Provider</span></span>

<span data-ttu-id="dd1fe-145">Windows PowerShell 공급자가 사용 하는 리소스를 해제 하려면 공급자가 자체의 [system.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Stop) 를 구현 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd1fe-145">To free resources that the Windows PowerShell provider uses, your provider should implement its own [System.Management.Automation.Provider.Cmdletprovider.Stop\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Stop) method.</span></span> <span data-ttu-id="dd1fe-146">이 메서드는 세션을 닫을 때 공급자의 초기화를 취소 하기 위해 Windows PowerShell 런타임에서 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd1fe-146">This method is called by the Windows PowerShell runtime to uninitialize the provider at the close of a session.</span></span>

<span data-ttu-id="dd1fe-147">이 기본 공급자는이 메서드를 재정의 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dd1fe-147">This basic provider does not override this method.</span></span> <span data-ttu-id="dd1fe-148">그러나 다음 코드는이 메서드의 기본 구현을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="dd1fe-148">However, the following code shows the default implementation of this method:</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderStop](Msh_samplesaccessdbprov01#accessdbprov01ProviderStop)]  -->

## <a name="code-sample"></a><span data-ttu-id="dd1fe-149">코드 예제</span><span class="sxs-lookup"><span data-stu-id="dd1fe-149">Code Sample</span></span>

<span data-ttu-id="dd1fe-150">전체 샘플 코드는 [AccessDbProviderSample01 코드 샘플](./accessdbprovidersample01-code-sample.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="dd1fe-150">For complete sample code, see [AccessDbProviderSample01 Code Sample](./accessdbprovidersample01-code-sample.md).</span></span>

## <a name="testing-the-windows-powershell-provider"></a><span data-ttu-id="dd1fe-151">Windows PowerShell 공급자 테스트</span><span class="sxs-lookup"><span data-stu-id="dd1fe-151">Testing the Windows PowerShell Provider</span></span>

<span data-ttu-id="dd1fe-152">Windows powershell 공급자를 Windows PowerShell에 등록 한 후에는 명령줄에서 지원 되는 cmdlet을 실행 하 여 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd1fe-152">Once your Windows PowerShell provider has been registered with Windows PowerShell, you can test it by running the supported cmdlets on the command line.</span></span> <span data-ttu-id="dd1fe-153">이 기본 공급자의 경우 새 셸을 실행 하 고 `Get-PSProvider` cmdlet을 사용 하 여 공급자 목록을 검색 하 고 AccessDb 공급자가 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd1fe-153">For this basic provider, run the new shell and use the `Get-PSProvider` cmdlet to retrieve the list of providers and ensure that the AccessDb provider is present.</span></span>

```powershell
Get-PSProvider
```

<span data-ttu-id="dd1fe-154">다음과 같은 출력이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="dd1fe-154">The following output appears:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="dd1fe-155">참고 항목</span><span class="sxs-lookup"><span data-stu-id="dd1fe-155">See Also</span></span>

[<span data-ttu-id="dd1fe-156">Windows PowerShell 공급자 만들기</span><span class="sxs-lookup"><span data-stu-id="dd1fe-156">Creating Windows PowerShell Providers</span></span>](./how-to-create-a-windows-powershell-provider.md)

[<span data-ttu-id="dd1fe-157">Windows PowerShell 공급자 디자인</span><span class="sxs-lookup"><span data-stu-id="dd1fe-157">Designing Your Windows PowerShell Provider</span></span>](./designing-your-windows-powershell-provider.md)
