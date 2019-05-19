---
title: Windows PowerShell 드라이브 공급자 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- drive providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], drive provider
- drives [PowerShell Programmer's Guide]
ms.assetid: 2b446841-6616-4720-9ff8-50801d7576ed
caps.latest.revision: 6
ms.openlocfilehash: 2696d78cae7739310b7684161b597ce436dabe92
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855198"
---
# <a name="creating-a-windows-powershell-drive-provider"></a><span data-ttu-id="b8fa8-102">Windows PowerShell 드라이브 공급자 만들기</span><span class="sxs-lookup"><span data-stu-id="b8fa8-102">Creating a Windows PowerShell Drive Provider</span></span>

<span data-ttu-id="b8fa8-103">이 항목에서는 Windows PowerShell 드라이브를 통해 데이터 저장소에 액세스 하는 방법을 제공 하는 Windows PowerShell 드라이브 공급자를 만드는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8fa8-103">This topic describes how to create a Windows PowerShell drive provider that provides a way to access a data store through a Windows PowerShell drive.</span></span> <span data-ttu-id="b8fa8-104">이 유형의 공급자는 Windows PowerShell 드라이브 공급자 라고도 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8fa8-104">This type of provider is also referred to as Windows PowerShell drive providers.</span></span> <span data-ttu-id="b8fa8-105">공급자가 사용 되는 Windows PowerShell 드라이브를 데이터 저장소에 연결 하는 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8fa8-105">The Windows PowerShell drives used by the provider provide the means to connect to the data store.</span></span>

<span data-ttu-id="b8fa8-106">여기에 설명 된 Windows PowerShell 드라이브 공급자는 Microsoft Access 데이터베이스에 대 한 액세스를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8fa8-106">The Windows PowerShell drive provider described here provides access to a Microsoft Access database.</span></span> <span data-ttu-id="b8fa8-107">이 공급자에 대 한 Windows PowerShell 드라이브 (드라이브 개수에 관계 없이 드라이브 공급자에 추가할 수는) 데이터베이스를 나타내는 드라이브의 최상위 컨테이너 데이터베이스의 테이블을 나타낼 및 컨테이너의 항목을 나타내는 행 테이블입니다.</span><span class="sxs-lookup"><span data-stu-id="b8fa8-107">For this provider, the Windows PowerShell drive represents the database (it is possible to add any number of drives to a drive provider), the top-level containers of the drive represent the tables in the database, and the items of the containers represent the rows in the tables.</span></span>

## <a name="defining-the-windows-powershell-provider-class"></a><span data-ttu-id="b8fa8-108">Windows PowerShell 공급자 클래스를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="b8fa8-108">Defining the Windows PowerShell Provider Class</span></span>

<span data-ttu-id="b8fa8-109">드라이브 공급자에서 파생 되는.NET 클래스를 정의 해야 합니다 [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) 기본 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="b8fa8-109">Your drive provider must define a .NET class that derives from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) base class.</span></span> <span data-ttu-id="b8fa8-110">이 드라이브 공급자에 대 한 클래스 정의 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b8fa8-110">Here is the class definition for this drive provider:</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L29-L30 "AccessDBProviderSample02.cs")]

<span data-ttu-id="b8fa8-111">이 예제는 [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) 특성 공급자 및 Windows PowerShell 특정 기능에 대 한 알기 쉬운 이름을 지정 하는 공급자 명령 처리 하는 동안 Windows PowerShell 런타임에 노출합니다.</span><span class="sxs-lookup"><span data-stu-id="b8fa8-111">Notice that in this example, the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attribute specifies a user-friendly name for the provider and the Windows PowerShell specific capabilities that the provider exposes to the Windows PowerShell runtime during command processing.</span></span> <span data-ttu-id="b8fa8-112">공급자 기능에 대 한 가능한 값은 정의한 합니다 [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) 열거형입니다.</span><span class="sxs-lookup"><span data-stu-id="b8fa8-112">The possible values for the provider capabilities are defined by the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="b8fa8-113">이 드라이브 공급자 이러한 기능 중 하나를 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b8fa8-113">This drive provider does not support any of these capabilities.</span></span>

## <a name="defining-base-functionality"></a><span data-ttu-id="b8fa8-114">기본 기능 정의</span><span class="sxs-lookup"><span data-stu-id="b8fa8-114">Defining Base Functionality</span></span>

<span data-ttu-id="b8fa8-115">에 설명 된 대로 [디자인 해당 Windows PowerShell 공급자](./designing-your-windows-powershell-provider.md)서 [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) 클래스에서 파생 되는 [ System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) 기본 초기화 및 공급자를 초기화 해제에 필요한 메서드를 정의 하는 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="b8fa8-115">As described in [Design Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md), the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class derives from the [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) base class that defines the methods needed for initializing and uninitializing the provider.</span></span> <span data-ttu-id="b8fa8-116">특정 세션 초기화 정보를 추가 하 고 공급자가 사용 되는 리소스를 해제 하는 것에 대 한 기능을 구현 하려면 참조 [는 기본 Windows PowerShell 공급자를 만들어](./creating-a-basic-windows-powershell-provider.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="b8fa8-116">To implement functionality for adding session-specific initialization information and for releasing resources that are used by the provider, see [Creating a Basic Windows PowerShell Provider](./creating-a-basic-windows-powershell-provider.md).</span></span> <span data-ttu-id="b8fa8-117">그러나 여기에 설명 된 공급자 등 대부분의 공급자 기본적으로 Windows PowerShell에서 제공 하는이 기능을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8fa8-117">However, most providers (including the provider described here) can use the default implementation of this functionality that is provided by Windows PowerShell.</span></span>

## <a name="creating-drive-state-information"></a><span data-ttu-id="b8fa8-118">드라이브 상태 정보를 만드는 중</span><span class="sxs-lookup"><span data-stu-id="b8fa8-118">Creating Drive State Information</span></span>

<span data-ttu-id="b8fa8-119">즉, 드라이브 공급자 공급자를 호출할 때 Windows PowerShell 런타임에 의해 필요한 모든 상태 정보를 만들 필요가 있는지 모든 Windows PowerShell 공급자 상태 비저장 간주 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8fa8-119">All Windows PowerShell providers are considered stateless, which means that your drive provider needs to create any state information that is needed by the Windows PowerShell runtime when it calls your provider.</span></span>

<span data-ttu-id="b8fa8-120">이 드라이브 공급자에 대 한 상태 정보에는 드라이브 정보로 유지 되는 데이터베이스 연결이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8fa8-120">For this drive provider, state information includes the connection to the database that is kept as part of the drive information.</span></span> <span data-ttu-id="b8fa8-121">다음은이 정보에 저장 되는 방법을 보여 주는 코드를 [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) 드라이브를 설명 하는 개체:</span><span class="sxs-lookup"><span data-stu-id="b8fa8-121">Here is code that shows how this information is stored in the [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object that describes the drive:</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L130-L151 "AccessDBProviderSample02.cs")]

## <a name="creating-a-drive"></a><span data-ttu-id="b8fa8-122">드라이브 만들기</span><span class="sxs-lookup"><span data-stu-id="b8fa8-122">Creating a Drive</span></span>

<span data-ttu-id="b8fa8-123">드라이브를 만들려면 Windows PowerShell 런타임에 허용 하려면 드라이브 공급자를 구현 해야 합니다 [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) 메서드.</span><span class="sxs-lookup"><span data-stu-id="b8fa8-123">To allow the Windows PowerShell runtime to create a drive, the drive provider must implement the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method.</span></span> <span data-ttu-id="b8fa8-124">다음 코드의 구현을 보여 줍니다.는 [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) 이 드라이브 공급자에 대 한 메서드:</span><span class="sxs-lookup"><span data-stu-id="b8fa8-124">The following code shows the implementation of the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method for this drive provider:</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L42-L84 "AccessDBProviderSample02.cs")]

<span data-ttu-id="b8fa8-125">이 메서드의 재정의 다음을 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8fa8-125">Your override of this method should do the following:</span></span>

- <span data-ttu-id="b8fa8-126">있는지 확인 합니다 [System.Management.Automation.PSDriveinfo.Root\*](/dotnet/api/System.Management.Automation.PSDriveInfo.Root) 멤버 존재 하 고 데이터 저장소에 연결 될 수 있는 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8fa8-126">Verify that the [System.Management.Automation.PSDriveinfo.Root\*](/dotnet/api/System.Management.Automation.PSDriveInfo.Root) member exists and that a connection to the data store can be made.</span></span>

- <span data-ttu-id="b8fa8-127">드라이브를 만들고 연결 하는 멤버를 지 원하는 채우기는 `New-PSDrive` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b8fa8-127">Create a drive and populate the connection member, in support of the `New-PSDrive` cmdlet.</span></span>

- <span data-ttu-id="b8fa8-128">유효성을 검사 합니다 [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) 제안 된 드라이브에 대 한 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="b8fa8-128">Validate the [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object for the proposed drive.</span></span>

- <span data-ttu-id="b8fa8-129">수정 된 [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) 모든 필요한 성능 또는 안정성 정보를 사용 하 여 드라이브를 설명 하는 개체 또는 드라이브를 사용 하 여 호출자에 대 한 추가 데이터를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8fa8-129">Modify the [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object that describes the drive with any required performance or reliability information, or provide extra data for callers using the drive.</span></span>

- <span data-ttu-id="b8fa8-130">사용 하 여 오류를 처리 합니다 [System.Management.Automation.Provider.Cmdletprovider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) 메서드와 반환 `null`합니다.</span><span class="sxs-lookup"><span data-stu-id="b8fa8-130">Handle failures using the [System.Management.Automation.Provider.Cmdletprovider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) method and then return `null`.</span></span>

  <span data-ttu-id="b8fa8-131">이 메서드는 메서드 또는 해당 공급자 버전으로 두 드라이브 정보를 전달 된를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8fa8-131">This method returns either the drive information that was passed to the method or a provider-specific version of it.</span></span>

## <a name="attaching-dynamic-parameters-to-newdrive"></a><span data-ttu-id="b8fa8-132">동적 매개 변수 매핑하려고 시도에 연결</span><span class="sxs-lookup"><span data-stu-id="b8fa8-132">Attaching Dynamic Parameters to NewDrive</span></span>

<span data-ttu-id="b8fa8-133">`New-PSDrive` 드라이브 공급자에서 지 원하는 cmdlet에 추가 매개 변수가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8fa8-133">The `New-PSDrive` cmdlet supported by your drive provider might require additional parameters.</span></span> <span data-ttu-id="b8fa8-134">이러한 동적 매개 변수를 cmdlet에 연결 하려면 공급자를 구현 합니다 [System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) 메서드.</span><span class="sxs-lookup"><span data-stu-id="b8fa8-134">To attach these dynamic parameters to the cmdlet, the provider implements the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) method.</span></span> <span data-ttu-id="b8fa8-135">속성 및 cmdlet 클래스와 유사한 특성을 구문 분석 된 필드에 있는 개체를 반환 하는이 메서드 또는 [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="b8fa8-135">This method returns an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span>

<span data-ttu-id="b8fa8-136">이 드라이브 공급자는이 메서드를 재정의 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b8fa8-136">This drive provider does not override this method.</span></span> <span data-ttu-id="b8fa8-137">그러나 다음 코드는이 메서드의 기본 구현을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b8fa8-137">However, the following code shows the default implementation of this method:</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters](Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters)]  -->

## <a name="removing-a-drive"></a><span data-ttu-id="b8fa8-138">드라이브를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="b8fa8-138">Removing a Drive</span></span>

<span data-ttu-id="b8fa8-139">데이터베이스 연결을 닫으려면 드라이브 공급자를 구현 해야 합니다 [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) 메서드.</span><span class="sxs-lookup"><span data-stu-id="b8fa8-139">To close the database connection, the drive provider must implement the [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method.</span></span> <span data-ttu-id="b8fa8-140">이 메서드는 공급자 관련 정보를 정리 후 드라이브에 대 한 연결을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="b8fa8-140">This method closes the connection to the drive after cleaning up any provider-specific information.</span></span>

<span data-ttu-id="b8fa8-141">다음 코드의 구현을 보여 줍니다.는 [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) 이 드라이브 공급자에 대 한 메서드:</span><span class="sxs-lookup"><span data-stu-id="b8fa8-141">The following code shows the implementation of the [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method for this drive provider:</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L91-L116 "AccessDBProviderSample02.cs")]

<span data-ttu-id="b8fa8-142">메서드를 통해 메서드에 전달 된 정보를 반환 해야 드라이브를 제거할 수 있는 경우는 `drive` 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="b8fa8-142">If the drive can be removed, the method should return the information passed to the method through the `drive` parameter.</span></span> <span data-ttu-id="b8fa8-143">드라이브를 제거할 수 없는 경우 메서드는 예외가 쓰고 돌아와서 `null`합니다.</span><span class="sxs-lookup"><span data-stu-id="b8fa8-143">If the drive cannot be removed, the method should write an exception and then return `null`.</span></span> <span data-ttu-id="b8fa8-144">공급자에이 메서드를 재정의 하지 않습니다이 메서드의 기본 구현에만 입력으로 전달 드라이브 정보를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8fa8-144">If your provider does not override this method, the default implementation of this method just returns the drive information passed as input.</span></span>

## <a name="initializing-default-drives"></a><span data-ttu-id="b8fa8-145">초기화 하는 동안 기본 드라이브</span><span class="sxs-lookup"><span data-stu-id="b8fa8-145">Initializing Default Drives</span></span>

<span data-ttu-id="b8fa8-146">드라이브 공급자가 구현 하는 [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) 드라이브를 탑재 하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="b8fa8-146">Your drive provider implements the [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) method to mount drives.</span></span> <span data-ttu-id="b8fa8-147">예를 들어, Active Directory 공급자를 기본 명명 컨텍스트 컴퓨터가 도메인에 가입 되어 있는 경우에 대 한 드라이브를 탑재할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8fa8-147">For example, the Active Directory provider might mount a drive for the default naming context if the computer is joined to a domain.</span></span>

<span data-ttu-id="b8fa8-148">이 메서드는 초기화 된 드라이브의 드라이브 정보 컬렉션 이거나 빈 컬렉션을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="b8fa8-148">This method returns a collection of drive information about the initialized drives, or an empty collection.</span></span> <span data-ttu-id="b8fa8-149">Windows PowerShell 런타임 호출한 후이 메서드는 호출 된 [System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) 공급자를 초기화 하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="b8fa8-149">The call to this method is made after the Windows PowerShell runtime calls the [System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) method to initialize the provider.</span></span>

<span data-ttu-id="b8fa8-150">이 드라이브 공급자를 재정의 하지 않습니다 합니다 [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) 메서드.</span><span class="sxs-lookup"><span data-stu-id="b8fa8-150">This drive provider does not override the [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) method.</span></span> <span data-ttu-id="b8fa8-151">그러나 다음 코드를 빈 드라이브 컬렉션을 반환 하는 기본 구현을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b8fa8-151">However, the following code shows the default implementation, which returns an empty drive collection:</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinitializedefaultdrives](Msh_samplestestcmdlets#testproviderinitializedefaultdrives)]  -->

#### <a name="things-to-remember-about-implementing-initializedefaultdrives"></a><span data-ttu-id="b8fa8-152">InitializeDefaultDrives를 구현 하는 방법에 대 한 고려해 야 할 사항</span><span class="sxs-lookup"><span data-stu-id="b8fa8-152">Things to Remember About Implementing InitializeDefaultDrives</span></span>

<span data-ttu-id="b8fa8-153">모든 드라이브 공급자 검색 기능을 사용 하 여 사용자를 위해 루트 드라이브를 탑재 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8fa8-153">All drive providers should mount a root drive to help the user with discoverability.</span></span> <span data-ttu-id="b8fa8-154">루트 드라이브에는 다른 탑재 된 드라이브에 대 한 루트 클래스로 사용 되는 위치 나열 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8fa8-154">The root drive might list locations that serve as roots for other mounted drives.</span></span> <span data-ttu-id="b8fa8-155">예를 들어, Active Directory 공급자에서 찾을 명명 컨텍스트를 나열 하는 드라이브를 만들 수는 `namingContext` 분산 시스템 환경 (DSE) 루트에는 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="b8fa8-155">For example, the Active Directory provider might create a drive that lists the naming contexts found in the `namingContext` attributes on the root Distributed System Environment (DSE).</span></span> <span data-ttu-id="b8fa8-156">이렇게 하면 사용자가 다른 드라이브에 대 한 탑재 지점을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8fa8-156">This helps users discover mount points for other drives.</span></span>

## <a name="code-sample"></a><span data-ttu-id="b8fa8-157">코드 예제</span><span class="sxs-lookup"><span data-stu-id="b8fa8-157">Code Sample</span></span>

<span data-ttu-id="b8fa8-158">전체 샘플 코드를 보려면 [AccessDbProviderSample02 코드 샘플](./accessdbprovidersample02-code-sample.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="b8fa8-158">For complete sample code, see [AccessDbProviderSample02 Code Sample](./accessdbprovidersample02-code-sample.md).</span></span>

## <a name="testing-the-windows-powershell-drive-provider"></a><span data-ttu-id="b8fa8-159">Windows PowerShell 드라이브 공급자 테스트</span><span class="sxs-lookup"><span data-stu-id="b8fa8-159">Testing the Windows PowerShell Drive Provider</span></span>

<span data-ttu-id="b8fa8-160">Windows PowerShell을 사용 하 여 Windows PowerShell 공급자가 등록 하는 경우에 파생에서 사용할 수 있는 모든 cmdlet을 포함 하 여 명령줄에서 지원 되는 cmdlet을 실행 하 여 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8fa8-160">When your Windows PowerShell provider has been registered with Windows PowerShell, you can test it by running the supported cmdlets on the command line, including any cmdlets made available by derivation.</span></span> <span data-ttu-id="b8fa8-161">샘플 드라이브 공급자를 테스트해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="b8fa8-161">Let's test the sample drive provider.</span></span>

1. <span data-ttu-id="b8fa8-162">실행 된 `Get-PSProvider` AccessDB 드라이브 공급자 있는지 확인 하는 공급자 목록을 검색 하는 cmdlet:</span><span class="sxs-lookup"><span data-stu-id="b8fa8-162">Run the `Get-PSProvider` cmdlet to retrieve the list of providers to ensure that the AccessDB drive provider is present:</span></span>

   <span data-ttu-id="b8fa8-163">**PS> `Get-PSProvider`**</span><span class="sxs-lookup"><span data-stu-id="b8fa8-163">**PS> `Get-PSProvider`**</span></span>

   <span data-ttu-id="b8fa8-164">다음과 같은 출력이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="b8fa8-164">The following output appears:</span></span>

   ```output
   Name                 Capabilities                  Drives
   ----                 ------------                  ------
   AccessDB             None                          {}
   Alias                ShouldProcess                 {Alias}
   Environment          ShouldProcess                 {Env}
   FileSystem           Filter, ShouldProcess         {C, Z}
   Function             ShouldProcess                 {function}
   Registry             ShouldProcess                 {HKLM, HKCU}
   ```

2. <span data-ttu-id="b8fa8-165">에 액세스 하 여 데이터베이스에 데이터베이스 서버 이름 (DSN)가 있는지 확인 합니다 **데이터 원본** 부분을 **관리 도구** 운영 체제에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8fa8-165">Ensure that a database server name (DSN) exists for the database by accessing the **Data Sources** portion of the **Administrative Tools** for the operating system.</span></span> <span data-ttu-id="b8fa8-166">에 **사용자 DSN** 테이블에서 두 번 클릭 **MS Access 데이터베이스** C:\ps\northwind.mdb 드라이브 경로 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8fa8-166">In the **User DSN** table, double-click **MS Access Database** and add the drive path C:\ps\northwind.mdb.</span></span>

3. <span data-ttu-id="b8fa8-167">샘플 드라이브 공급자를 사용 하 여 새 드라이브를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b8fa8-167">Create a new drive using the sample drive provider:</span></span>

   <span data-ttu-id="b8fa8-168">**PS> new-psdrive -name mydb -root c:\ps\northwind.mdb -psprovider AccessDb**</span><span class="sxs-lookup"><span data-stu-id="b8fa8-168">**PS> new-psdrive -name mydb -root c:\ps\northwind.mdb -psprovider AccessDb**</span></span>

   <span data-ttu-id="b8fa8-169">다음과 같은 출력이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="b8fa8-169">The following output appears:</span></span>

   ```output
   Name     Provider     Root                   CurrentLocation
   ----     --------     ----                   ---------------
   mydb     AccessDB     c:\ps\northwind.mdb
   ```

4. <span data-ttu-id="b8fa8-170">연결의 유효성을 검사 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8fa8-170">Validate the connection.</span></span> <span data-ttu-id="b8fa8-171">연결에는 드라이브의 멤버로 정의 PDDrive Get cmdlet을 사용 하 여 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8fa8-171">Because the connection is defined as a member of the drive, you can check it using the Get-PDDrive cmdlet.</span></span>

   > [!NOTE]
   > <span data-ttu-id="b8fa8-172">사용자는 상호 작용에 대 한 컨테이너 기능을 필요로 하는 공급자 처럼에 아직 드라이브 공급자 상호 작용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b8fa8-172">The user cannot yet interact with the provider as a drive, as the provider needs container functionality for that interaction.</span></span> <span data-ttu-id="b8fa8-173">자세한 내용은 [Windows PowerShell 컨테이너 공급자 만들기](./creating-a-windows-powershell-container-provider.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="b8fa8-173">For more information, see [Creating a Windows PowerShell Container Provider](./creating-a-windows-powershell-container-provider.md).</span></span>

   <span data-ttu-id="b8fa8-174">**PS > (get psdrive mydb).connection**</span><span class="sxs-lookup"><span data-stu-id="b8fa8-174">**PS> (get-psdrive mydb).connection**</span></span>

   <span data-ttu-id="b8fa8-175">다음과 같은 출력이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="b8fa8-175">The following output appears:</span></span>

   ```output
   ConnectionString  : Driver={Microsoft Access Driver (*.mdb)};DBQ=c:\ps\northwind.mdb
   ConnectionTimeout : 15
   Database          : c:\ps\northwind
   DataSource        : ACCESS
   ServerVersion     : 04.00.0000
   Driver            : odbcjt32.dll
   State             : Open
   Site              :
   Container         :
   ```

5. <span data-ttu-id="b8fa8-176">드라이브를 제거 하 고 셸을 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8fa8-176">Remove the drive and exit the shell:</span></span>

   <span data-ttu-id="b8fa8-177">**PS >-remove-psdrive mydb**</span><span class="sxs-lookup"><span data-stu-id="b8fa8-177">**PS> remove-psdrive mydb**</span></span>

   <span data-ttu-id="b8fa8-178">**PS > 종료**</span><span class="sxs-lookup"><span data-stu-id="b8fa8-178">**PS> exit**</span></span>

## <a name="see-also"></a><span data-ttu-id="b8fa8-179">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b8fa8-179">See Also</span></span>

[<span data-ttu-id="b8fa8-180">Windows PowerShell 공급자 만들기</span><span class="sxs-lookup"><span data-stu-id="b8fa8-180">Creating Windows PowerShell Providers</span></span>](./how-to-create-a-windows-powershell-provider.md)

[<span data-ttu-id="b8fa8-181">Windows PowerShell 공급자를 디자인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8fa8-181">Design Your Windows PowerShell Provider</span></span>](./designing-your-windows-powershell-provider.md)

[<span data-ttu-id="b8fa8-182">기본 Windows PowerShell 공급자 만들기</span><span class="sxs-lookup"><span data-stu-id="b8fa8-182">Creating a Basic Windows PowerShell Provider</span></span>](./creating-a-basic-windows-powershell-provider.md)