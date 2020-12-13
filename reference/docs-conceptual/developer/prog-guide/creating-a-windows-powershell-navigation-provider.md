---
ms.date: 09/13/2016
ms.topic: reference
title: Windows PowerShell 탐색 공급자 만들기
description: Windows PowerShell 탐색 공급자 만들기
ms.openlocfilehash: 73d4971fb91acaef9e1f20226e7b9b883730e394
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92658661"
---
# <a name="creating-a-windows-powershell-navigation-provider"></a><span data-ttu-id="36f9e-103">Windows PowerShell 탐색 공급자 만들기</span><span class="sxs-lookup"><span data-stu-id="36f9e-103">Creating a Windows PowerShell Navigation Provider</span></span>

<span data-ttu-id="36f9e-104">이 항목에서는 데이터 저장소를 탐색할 수 있는 Windows PowerShell 탐색 공급자를 만드는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-104">This topic describes how to create a Windows PowerShell navigation provider that can navigate the data store.</span></span> <span data-ttu-id="36f9e-105">이 유형의 공급자는 재귀 명령, 중첩 된 컨테이너 및 상대 경로를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-105">This type of provider supports recursive commands, nested containers, and relative paths.</span></span>

> [!NOTE]
> <span data-ttu-id="36f9e-106">Windows Vista 및 .NET Framework 3.0 런타임 구성 요소에 대 한 Microsoft Windows 소프트웨어 개발 키트를 사용 하 여이 공급자에 대 한 c # 소스 파일 (AccessDBSampleProvider05.cs)을 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-106">You can download the C# source file (AccessDBSampleProvider05.cs) for this provider using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="36f9e-107">다운로드 지침은 [Windows powershell을 설치 하 고 Windows POWERSHELL SDK를 다운로드 하는 방법](/powershell/scripting/developer/installing-the-windows-powershell-sdk)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="36f9e-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="36f9e-108">다운로드 된 원본 파일은 디렉터리에서 사용할 수 있습니다 **\<PowerShell Samples>** .</span><span class="sxs-lookup"><span data-stu-id="36f9e-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span> <span data-ttu-id="36f9e-109">다른 Windows PowerShell 공급자 구현에 대 한 자세한 내용은 [Windows Powershell 공급자 디자인](./designing-your-windows-powershell-provider.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="36f9e-109">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

<span data-ttu-id="36f9e-110">여기에 설명 된 공급자를 사용 하면 사용자가 데이터베이스의 데이터 테이블로 이동할 수 있도록 Access 데이터베이스를 드라이브로 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-110">The provider described here enables the user handle an Access database as a drive so that the user can navigate to the data tables in the database.</span></span> <span data-ttu-id="36f9e-111">사용자 고유의 탐색 공급자를 만들 때 탐색에 필요한 드라이브 정규화 된 경로를 지정 하 고, 상대 경로를 정규화 하 고, 데이터 저장소의 항목을 이동 하 고, 자식 이름을 가져오는 메서드 뿐만 아니라 항목의 부모 경로를 가져오고, 항목이 컨테이너 인지 여부를 식별 하는 테스트를 수행할 수 있는 메서드를 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-111">When creating your own navigation provider, you can implement methods that can make drive-qualified paths required for navigation, normalize relative paths, move items of the data store, as well as methods that get child names, get the parent path of an item, and test to identify if an item is a container.</span></span>

> [!CAUTION]
> <span data-ttu-id="36f9e-112">이 설계에서는 이름이 ID가 인 필드가 있는 데이터베이스를 가정 하 고 해당 필드의 형식은가 중 정수 라는 것을 알고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-112">Be aware that this design assumes a database that has a field with the name ID, and that the type of the field is LongInteger.</span></span>

## <a name="define-the-windows-powershell-provider"></a><span data-ttu-id="36f9e-113">Windows PowerShell 공급자 정의</span><span class="sxs-lookup"><span data-stu-id="36f9e-113">Define the Windows PowerShell provider</span></span>

<span data-ttu-id="36f9e-114">Windows PowerShell 탐색 공급자는 [system.object](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 클래스에서 파생 되는 .net 클래스를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-114">A Windows PowerShell navigation provider must create a .NET class that derives from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) base class.</span></span> <span data-ttu-id="36f9e-115">이 섹션에서 설명 하는 탐색 공급자에 대 한 클래스 정의는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-115">Here is the class definition for the navigation provider described in this section.</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample05/AccessDBProviderSample05.cs" range="31-32":::

<span data-ttu-id="36f9e-116">이 공급자에서 [Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) 특성에는 두 개의 매개 변수가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-116">Note that in this provider, the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attribute includes two parameters.</span></span> <span data-ttu-id="36f9e-117">첫 번째 매개 변수는 Windows PowerShell에서 사용 되는 공급자에 대 한 친숙 한 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-117">The first parameter specifies a user-friendly name for the provider that is used by Windows PowerShell.</span></span> <span data-ttu-id="36f9e-118">두 번째 매개 변수는 명령을 처리 하는 동안 공급자가 Windows PowerShell 런타임에 노출 하는 Windows PowerShell 특정 기능을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-118">The second parameter specifies the Windows PowerShell specific capabilities that the provider exposes to the Windows PowerShell runtime during command processing.</span></span> <span data-ttu-id="36f9e-119">이 공급자의 경우 추가 되는 Windows PowerShell 관련 기능이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-119">For this provider, there are no Windows PowerShell specific capabilities that are added.</span></span>

## <a name="defining-base-functionality"></a><span data-ttu-id="36f9e-120">기본 기능 정의</span><span class="sxs-lookup"><span data-stu-id="36f9e-120">Defining Base Functionality</span></span>

<span data-ttu-id="36f9e-121">[PS 공급자 디자인](./designing-your-windows-powershell-provider.md)에 설명 된 대로 다른 공급자 기능을 제공 하는 다른 여러 클래스에서 [파생 됩니다.](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)</span><span class="sxs-lookup"><span data-stu-id="36f9e-121">As described in [Design Your PS Provider](./designing-your-windows-powershell-provider.md), the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) base class derives from several other classes that provided different provider functionality.</span></span> <span data-ttu-id="36f9e-122">따라서 Windows PowerShell 탐색 공급자는 해당 클래스에서 제공 하는 기능을 모두 정의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-122">A Windows PowerShell navigation provider, therefore, must define all of the functionality provided by those classes.</span></span>

<span data-ttu-id="36f9e-123">세션 관련 초기화 정보를 추가 하 고 공급자가 사용 하는 리소스를 해제 하는 기능을 구현 하려면 [기본 PS 공급자 만들기](./creating-a-basic-windows-powershell-provider.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="36f9e-123">To implement functionality for adding session-specific initialization information and for releasing resources that are used by the provider, see [Creating a Basic PS Provider](./creating-a-basic-windows-powershell-provider.md).</span></span> <span data-ttu-id="36f9e-124">그러나 여기에 설명 된 공급자를 비롯 한 대부분의 공급자는 Windows PowerShell에서 제공 하는이 기능의 기본 구현을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-124">However, most providers (including the provider described here) can use the default implementation of this functionality provided by Windows PowerShell.</span></span>

<span data-ttu-id="36f9e-125">Windows PowerShell 드라이브를 통해 데이터 저장소에 대 한 액세스 권한을 얻으려면 [system.object](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) 의 메서드를 구현 해야 합니다...</span><span class="sxs-lookup"><span data-stu-id="36f9e-125">To get access to the data store through a Windows PowerShell drive, you must implement the methods of the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) base class.</span></span> <span data-ttu-id="36f9e-126">이러한 메서드를 구현 하는 방법에 대 한 자세한 내용은 [Windows PowerShell 드라이브 공급자 만들기](./creating-a-windows-powershell-drive-provider.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="36f9e-126">For more information about implementing these methods, see [Creating a Windows PowerShell Drive Provider](./creating-a-windows-powershell-drive-provider.md).</span></span>

<span data-ttu-id="36f9e-127">항목 가져오기, 설정 및 지우기와 같은 데이터 저장소의 항목을 조작 하려면 공급자는 [system.object](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) 에서 제공 하는 메서드를 구현 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-127">To manipulate the items of a data store, such as getting, setting, and clearing items, the provider must implement the methods provided by the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) base class.</span></span> <span data-ttu-id="36f9e-128">이러한 메서드를 구현 하는 방법에 대 한 자세한 내용은 [Windows PowerShell 항목 공급자 만들기](./creating-a-windows-powershell-item-provider.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="36f9e-128">For more information about implementing these methods, see [Creating an Windows PowerShell Item Provider](./creating-a-windows-powershell-item-provider.md).</span></span>

<span data-ttu-id="36f9e-129">항목을 만들고, 복사 하 고, 이름을 바꾸고, 제거 하는 메서드 뿐만 아니라 자식 항목 또는 데이터 저장소의 이름을 가져오려면 [Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) 기본 클래스에서 제공 하는 메서드를 구현 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-129">To get to the child items, or their names, of the data store, as well as methods that create, copy, rename, and remove items, you must implement the methods provided by the [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) base class.</span></span> <span data-ttu-id="36f9e-130">이러한 메서드를 구현 하는 방법에 대 한 자세한 내용은 [Windows PowerShell 컨테이너 공급자 만들기](./creating-a-windows-powershell-container-provider.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="36f9e-130">For more information about implementing these methods, see [Creating a Windows PowerShell Container Provider](./creating-a-windows-powershell-container-provider.md).</span></span>

## <a name="creating-a-windows-powershell-path"></a><span data-ttu-id="36f9e-131">Windows PowerShell 경로 만들기</span><span class="sxs-lookup"><span data-stu-id="36f9e-131">Creating a Windows PowerShell Path</span></span>

<span data-ttu-id="36f9e-132">Windows PowerShell 탐색 공급자는 공급자 내부 Windows PowerShell 경로를 사용 하 여 데이터 저장소의 항목을 탐색 합니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-132">Windows PowerShell navigation provider use a provider-internal Windows PowerShell path to navigate the items of the data store.</span></span> <span data-ttu-id="36f9e-133">공급자 내부 경로를 만들려면 공급자가 Combine-Path cmdlet의 호출을 지원 하기 위해 System.object를 구현 해야 합니다. [makepath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) 메서드를 구현 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-133">To create a provider-internal path the provider must implement the [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) method to supports calls from the Combine-Path cmdlet.</span></span> <span data-ttu-id="36f9e-134">이 메서드는 부모 및 자식 경로 사이에 공급자별 경로 구분 기호를 사용 하 여 부모 및 자식 경로를 공급자 내부 경로로 결합 합니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-134">This method combines a parent and child path into a provider-internal path, using a provider-specific path separator between the parent and child paths.</span></span>

<span data-ttu-id="36f9e-135">기본 구현에서는 경로 구분 기호로 "/" 또는 ""를 사용 하 여 경로를 사용 하 고, \\ 경로 구분 기호를 ""로 정규화 하 고 \\ , 부모 및 자식 경로 부분을 구분 기호와 결합 한 다음 조합 된 경로를 포함 하는 문자열을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-135">The default implementation takes paths with "/" or "\\" as the path separator, normalizes the path separator to "\\", combines the parent and child path parts with the separator between them, and then returns a string that contains the combined paths.</span></span>

<span data-ttu-id="36f9e-136">이 탐색 공급자는이 메서드를 구현 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-136">This navigation provider does not implement this method.</span></span> <span data-ttu-id="36f9e-137">그러나 다음 코드는 System.object의 기본 구현입니다. [Makecmdletprovider. Makepath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) 메서드를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-137">However, the following code is the default implementation of the [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) method.</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermakepath](Msh_samplestestcmdlets#testprovidermakepath)]  -->

#### <a name="things-to-remember-about-implementing-makepath"></a><span data-ttu-id="36f9e-138">MakePath 구현에 대해 기억할 사항</span><span class="sxs-lookup"><span data-stu-id="36f9e-138">Things to Remember About Implementing MakePath</span></span>

<span data-ttu-id="36f9e-139">다음 조건은 System.object의 구현에 적용 될 수 있습니다. [Makecmdletprovider \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath):</span><span class="sxs-lookup"><span data-stu-id="36f9e-139">The following conditions may apply to your implementation of [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath):</span></span>

- <span data-ttu-id="36f9e-140">[System.object](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) 의 구현에서는 공급자 네임 스페이스의 올바른 정규화 된 경로로 경로의 유효성을 검사 하면 안 됩니다 .이 메서드를 구현 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-140">Your implementation of the [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) method should not validate the path as a legal fully-qualified path in the provider namespace.</span></span> <span data-ttu-id="36f9e-141">각 매개 변수는 경로의 일부만 나타낼 수 있고 결합 된 부분은 정규화 된 경로를 생성 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-141">Be aware that each parameter can only represent a part of a path, and the combined parts might not generate a fully-qualified path.</span></span> <span data-ttu-id="36f9e-142">예를 들어 파일 [시스템](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) 공급자에 대 한 windows\system32는 매개 변수에서 ""를 수신 `parent` 하 고 `child` 매개 변수에서 "abc.dll"를 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-142">For example, the [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) method for the filesystem provider might receive "windows\system32" in the `parent` parameter and "abc.dll" in the `child` parameter.</span></span> <span data-ttu-id="36f9e-143">메서드는 "" 구분 기호를 사용 하 여 이러한 값 \\ 을 조인 하 고 정규화 된 파일 시스템 경로가 아닌 "windows\system32\abc.dll"을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-143">The method joins these values with the "\\" separator and returns "windows\system32\abc.dll", which is not a fully-qualified file system path.</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="36f9e-144">System.object에 대 한 호출에 제공 된 경로 부분입니다 [. makepath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) 는 공급자 네임 스페이스에 허용 되지 않는 문자를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-144">The path parts provided in the call to [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) might contain characters not allowed in the provider namespace.</span></span> <span data-ttu-id="36f9e-145">이러한 문자는 와일드 카드 확장에 사용 되며,이 메서드를 구현 하면 이러한 문자를 제거 하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-145">These characters are most likely used for wildcard expansion and the implementation of this method should not remove them.</span></span>

## <a name="retrieving-the-parent-path"></a><span data-ttu-id="36f9e-146">부모 경로를 검색 하는 중</span><span class="sxs-lookup"><span data-stu-id="36f9e-146">Retrieving the Parent Path</span></span>

<span data-ttu-id="36f9e-147">Windows PowerShell 탐색 공급자는 표시 된 전체 또는 부분 공급자별 경로의 부모 파트를 검색 하는 [Getparentpath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) 메서드를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-147">Windows PowerShell navigation providers implement the [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) method to retrieve the parent part of the indicated full or partial provider-specific path.</span></span> <span data-ttu-id="36f9e-148">메서드는 경로의 자식 부분을 제거 하 고 부모 경로 부분을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-148">The method removes the child part of the path and returns the parent path part.</span></span> <span data-ttu-id="36f9e-149">`root`매개 변수는 드라이브의 루트에 대 한 정규화 된 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-149">The `root` parameter specifies the fully-qualified path to the root of a drive.</span></span> <span data-ttu-id="36f9e-150">탑재 된 드라이브가 검색 작업에 사용 되 고 있지 않으면이 매개 변수는 null 이거나 비어 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-150">This parameter can be null or empty if a mounted drive is not in use for the retrieval operation.</span></span> <span data-ttu-id="36f9e-151">루트가 지정 된 경우 메서드는 루트와 동일한 트리의 컨테이너에 대 한 경로를 반환 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-151">If a root is specified, the method must return a path to a container in the same tree as the root.</span></span>

<span data-ttu-id="36f9e-152">샘플 탐색 공급자는이 메서드를 재정의 하지 않지만 기본 구현을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-152">The sample navigation provider does not override this method, but uses the default implementation.</span></span>
<span data-ttu-id="36f9e-153">"/" 및 ""를 경로 구분 기호로 사용 하는 경로를 허용 \\ 합니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-153">It accepts paths that use both "/" and "\\" as path separators.</span></span> <span data-ttu-id="36f9e-154">먼저 "" 구분 기호를 포함 하도록 경로를 정규화 한 \\ 다음 마지막 ""에서 부모 경로를 분할 하 \\ 고 부모 경로를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-154">It first normalizes the path to have only "\\" separators, then splits the parent path off at the last "\\" and returns the parent path.</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetparentpath](Msh_samplestestcmdlets#testprovidergetparentpath)]  -->

#### <a name="to-remember-about-implementing-getparentpath"></a><span data-ttu-id="36f9e-155">GetParentPath 구현에 대 한 자세한 내용은</span><span class="sxs-lookup"><span data-stu-id="36f9e-155">To Remember About Implementing GetParentPath</span></span>

<span data-ttu-id="36f9e-156">[Getparentpath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) 메서드를 구현 하는 경우 공급자 네임 스페이스에 대 한 경로 구분 기호에서 경로를 어휘 단위로 분할 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-156">Your implementation of the [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) method should split the path lexically on the path separator for the provider namespace.</span></span> <span data-ttu-id="36f9e-157">예를 들어 파일 시스템 공급자는이 메서드를 사용 하 여 마지막 " \\ "을 찾은 다음 구분 기호의 왼쪽에 있는 모든 항목을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-157">For example, the filesystem provider uses this method to look for the last "\\" and returns everything to the left of the separator.</span></span>

## <a name="retrieve-the-child-path-name"></a><span data-ttu-id="36f9e-158">자식 경로 이름 검색</span><span class="sxs-lookup"><span data-stu-id="36f9e-158">Retrieve the Child Path Name</span></span>

<span data-ttu-id="36f9e-159">탐색 공급자는 표시 된 전체 또는 부분 공급자별 경로에 있는 항목의 자식에 대 한 이름 (리프 요소)을 검색 하는 [Getchildname \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) 메서드를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-159">Your navigation provider implements the [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) method to retrieve the name (leaf element) of the child of the item located at the indicated full or partial provider-specific path.</span></span>

<span data-ttu-id="36f9e-160">샘플 탐색 공급자는이 메서드를 재정의 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-160">The sample navigation provider does not override this method.</span></span> <span data-ttu-id="36f9e-161">기본 구현은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-161">The default implementation is shown below.</span></span> <span data-ttu-id="36f9e-162">"/" 및 ""를 경로 구분 기호로 사용 하는 경로를 허용 \\ 합니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-162">It accepts paths that use both "/" and "\\" as path separators.</span></span> <span data-ttu-id="36f9e-163">먼저 "" 구분 기호를 포함 하도록 경로를 정규화 한 \\ 다음 마지막 ""에서 부모 경로를 분할 하 \\ 고 자식 경로 부분의 이름을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-163">It first normalizes the path to have only "\\" separators, then splits the parent path off at the last "\\" and returns the name of the child path part.</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchildname](Msh_samplestestcmdlets#testprovidergetchildname)]  -->

#### <a name="things-to-remember-about-implementing-getchildname"></a><span data-ttu-id="36f9e-164">GetChildName 구현에 대해 기억할 사항</span><span class="sxs-lookup"><span data-stu-id="36f9e-164">Things to Remember About Implementing GetChildName</span></span>

<span data-ttu-id="36f9e-165">[Getchildname \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) 메서드를 구현 하면 경로 구분 기호에서 경로를 어휘 적으로 분할 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-165">Your implementation of the [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) method should split the path lexically on the path separator.</span></span> <span data-ttu-id="36f9e-166">제공 된 경로에 경로 구분 기호가 포함 되어 있지 않으면이 메서드는 수정 되지 않은 경로를 반환 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-166">If the supplied path contains no path separators, the method should return the path unmodified.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="36f9e-167">이 메서드에 대 한 호출에 제공 된 경로에 공급자 네임 스페이스에 잘못 된 문자가 포함 되어 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-167">The path provided in the call to this method might contain characters that are illegal in the provider namespace.</span></span> <span data-ttu-id="36f9e-168">이러한 문자는 와일드 카드 확장 또는 정규식 일치에 사용 될 수 있으며,이 메서드를 구현 하면 이러한 문자를 제거 하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-168">These characters are most likely used for wildcard expansion or regular expression matching, and the implementation of this method should not remove them.</span></span>

## <a name="determining-if-an-item-is-a-container"></a><span data-ttu-id="36f9e-169">항목이 컨테이너 인지 확인</span><span class="sxs-lookup"><span data-stu-id="36f9e-169">Determining if an Item is a Container</span></span>

<span data-ttu-id="36f9e-170">탐색 공급자는 지정 된 경로가 컨테이너를 표시 하는지 확인 하기 위해 [Isitemcontainer \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) 메서드를 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-170">The navigation provider can implement the [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) method to determine if the specified path indicates a container.</span></span> <span data-ttu-id="36f9e-171">경로가 컨테이너를 나타내면 true를 반환 하 고 그렇지 않으면 false를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-171">It returns true if the path represents a container, and false otherwise.</span></span> <span data-ttu-id="36f9e-172">사용자는 `Test-Path` 제공 된 경로에 대해 cmdlet을 사용할 수 있으려면이 메서드가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-172">The user needs this method to be able to use the `Test-Path` cmdlet for the supplied path.</span></span>

<span data-ttu-id="36f9e-173">다음 코드는 샘플 탐색 공급자의 [Isitemcontainer \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) 구현을 보여 줍니다 .이 예제에서는</span><span class="sxs-lookup"><span data-stu-id="36f9e-173">The following code shows the [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) implementation in our sample navigation provider.</span></span> <span data-ttu-id="36f9e-174">메서드는 지정 된 경로가 올바른지 그리고 테이블이 있는지 확인 하 고 경로가 컨테이너를 나타내는 경우 true를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-174">The method verifies that the specified path is correct and if the table exists, and returns true if the path indicates a container.</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample05/AccessDBProviderSample05.cs" range="847-872":::

#### <a name="things-to-remember-about-implementing-isitemcontainer"></a><span data-ttu-id="36f9e-175">IsItemContainer 구현에 대해 기억할 사항</span><span class="sxs-lookup"><span data-stu-id="36f9e-175">Things to Remember About Implementing IsItemContainer</span></span>

<span data-ttu-id="36f9e-176">탐색 공급자 .NET 클래스가 ExpandWildcards, Filter, Include 또는 Exclude의 공급자 기능을 [system.object](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) 열거에서 선언할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-176">Your navigation provider .NET class might declare provider capabilities of ExpandWildcards, Filter, Include, or Exclude, from the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="36f9e-177">이 경우에는 전달 된 경로가 요구 사항을 충족 하는지 확인 하기 위해 [Isitemcontainer \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) 를 구현 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-177">In this case, the implementation of [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) needs to ensure that the path passed meets requirements.</span></span> <span data-ttu-id="36f9e-178">이 작업을 수행 하려면 메서드가 적절 한 속성 (예: [system.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) )에 액세스 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-178">To do this, the method should access the appropriate property, for example, the [System.Management.Automation.Provider.Cmdletprovider.Exclude\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) property.</span></span>

## <a name="moving-an-item"></a><span data-ttu-id="36f9e-179">항목 이동</span><span class="sxs-lookup"><span data-stu-id="36f9e-179">Moving an Item</span></span>

<span data-ttu-id="36f9e-180">`Move-Item`Cmdlet을 지원 하기 위해 탐색 공급자는 [Moveitem \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) 메서드를 구현 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-180">In support of the `Move-Item` cmdlet, your navigation provider implements the [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) method.</span></span> <span data-ttu-id="36f9e-181">이 메서드는 매개 변수에 지정 된 항목을 `path` 매개 변수에 제공 된 경로의 컨테이너로 이동 합니다 `destination` .</span><span class="sxs-lookup"><span data-stu-id="36f9e-181">This method moves the item specified by the `path` parameter to the container at the path supplied in the `destination` parameter.</span></span>

<span data-ttu-id="36f9e-182">샘플 탐색 공급자는 [Moveitem \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) 메서드를 재정의 하지 않습니다 .이 메서드는</span><span class="sxs-lookup"><span data-stu-id="36f9e-182">The sample navigation provider does not override the [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) method.</span></span> <span data-ttu-id="36f9e-183">다음은 기본 구현입니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-183">The following is the default implementation.</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermoveitem](Msh_samplestestcmdlets#testprovidermoveitem)]  -->

#### <a name="things-to-remember-about-implementing-moveitem"></a><span data-ttu-id="36f9e-184">MoveItem 구현에 대해 기억할 사항</span><span class="sxs-lookup"><span data-stu-id="36f9e-184">Things to Remember About Implementing MoveItem</span></span>

<span data-ttu-id="36f9e-185">탐색 공급자 .NET 클래스가 ExpandWildcards, Filter, Include 또는 Exclude의 공급자 기능을 [system.object](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) 열거에서 선언할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-185">Your navigation provider .NET class might declare provider capabilities of ExpandWildcards, Filter, Include, or Exclude, from the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="36f9e-186">이 경우 [Moveitem \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) 를 구현 하면 전달 된 경로가 요구 사항을 충족 하는지 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-186">In this case, the implementation of [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) must ensure that the path passed meets requirements.</span></span> <span data-ttu-id="36f9e-187">이렇게 하려면 메서드가 적절 한 속성 (예: **Cmdletprovider. Exclude** 속성)에 액세스 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-187">To do this, the method should access the appropriate property, for example, the **CmdletProvider.Exclude** property.</span></span>

<span data-ttu-id="36f9e-188">기본적으로이 메서드의 재정의는 [system.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 를로 설정 하지 않으면 기존 개체를 통해 개체를 이동 하면 안 됩니다. `true`</span><span class="sxs-lookup"><span data-stu-id="36f9e-188">By default, overrides of this method should not move objects over existing objects unless the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is set to `true`.</span></span> <span data-ttu-id="36f9e-189">예를 들어 파일 [시스템](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 공급자는 기존 c:\bar.txt 파일을 통해 c:\temp\abc.txt를 복사 하지 않습니다. 예를 들어,이 속성은로 설정 되어 있지 않습니다. `true`</span><span class="sxs-lookup"><span data-stu-id="36f9e-189">For example, the filesystem provider will not copy c:\temp\abc.txt over an existing c:\bar.txt file unless the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is set to `true`.</span></span> <span data-ttu-id="36f9e-190">매개 변수에 지정 된 경로가 있고 컨테이너인 경우에는 System.web.. m a n. a m a. m `destination` a n [\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 속성이 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-190">If the path specified in the `destination` parameter exists and is a container, the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is not required.</span></span> <span data-ttu-id="36f9e-191">이 경우 [Moveitem \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) 는 매개 변수로 표시 되는 항목을 `path` 매개 변수로 표시 된 컨테이너에 `destination` 자식으로 이동 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-191">In this case, [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) should move the item indicated by the `path` parameter to the container indicated by the `destination` parameter as a child.</span></span>

<span data-ttu-id="36f9e-192">[Moveitem \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) 메서드를 구현 하는 경우에는 데이터 저장소를 변경 하기 전에 해당 반환 값을 확인 [하 고 해당 반환 값을 확인](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-192">Your implementation of the [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) method should call [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) and check its return value before making any changes to the data store.</span></span> <span data-ttu-id="36f9e-193">이 메서드는 시스템 상태가 변경 될 때 (예: 파일 삭제) 작업 실행을 확인 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-193">This method is used to confirm execution of an operation when a change is made to system state, for example, deleting files.</span></span>
<span data-ttu-id="36f9e-194">Windows PowerShell 런타임이 사용자에 게 표시 되는 항목을 확인 하는 데 필요한 명령줄 설정이 나 기본 설정 변수를 고려 하 여 사용자에 게 변경할 리소스의 [이름을 보냅니다.](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)</span><span class="sxs-lookup"><span data-stu-id="36f9e-194">[System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) sends the name of the resource to be changed to the user, with the Windows PowerShell runtime taking into account any command line settings or preference variables in determining what should be displayed to the user.</span></span>

<span data-ttu-id="36f9e-195">Moveitem \* 메서드는 [system.object를 호출한](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 후에를 호출 하 여를 호출한 후에는 `true` [system.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) 를 [](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) 호출 해야 합니다 .이 메서드를 호출 하는 경우에는 system.object를 호출 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-195">After the call to [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) returns `true`, the [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) method should call the [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) method.</span></span> <span data-ttu-id="36f9e-196">이 메서드는 사용자에 게 작업을 계속 해야 하는 경우 사용자에 게 메시지를 보내 사용자에 게 피드백을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-196">This method sends a message to the user to allow feedback to say if the operation should be continued.</span></span> <span data-ttu-id="36f9e-197">공급자는 System.object를 호출 해야 합니다 [. shouldcontinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) 잠재적으로 위험한 시스템 수정에 대 한 추가 검사로 계속 합니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-197">Your provider should call [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) as an additional check for potentially dangerous system modifications.</span></span>

## <a name="attaching-dynamic-parameters-to-the-move-item-cmdlet"></a><span data-ttu-id="36f9e-198">Move-Item Cmdlet에 동적 매개 변수 연결</span><span class="sxs-lookup"><span data-stu-id="36f9e-198">Attaching Dynamic Parameters to the Move-Item Cmdlet</span></span>

<span data-ttu-id="36f9e-199">경우에 따라 cmdlet에는 `Move-Item` 런타임에 동적으로 제공 되는 추가 매개 변수가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-199">Sometimes the `Move-Item` cmdlet requires additional parameters that are provided dynamically at runtime.</span></span> <span data-ttu-id="36f9e-200">이러한 동적 매개 변수를 제공 하기 위해 탐색 공급자는 지정 된 경로의 항목에서 필수 매개 변수 값을 가져오고 cmdlet 클래스 또는 [Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 개체와 유사한 구문 분석 특성을 가진 속성 및 필드가 있는 개체를 반환 하기 위해 system.web. c a g. c a n [g](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) .</span><span class="sxs-lookup"><span data-stu-id="36f9e-200">To provide these dynamic parameters, the navigation provider must implement the [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) method to get the required parameter values from the item at the indicated path, and return an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span>

<span data-ttu-id="36f9e-201">이 탐색 공급자는이 메서드를 구현 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-201">This navigation provider does not implement this method.</span></span> <span data-ttu-id="36f9e-202">그러나 다음 코드는 System.object의 기본 구현입니다. [Moveitemdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters)입니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-202">However, the following code is the default implementation of [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters).</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermoveitemdynamicparameters](Msh_samplestestcmdlets#testprovidermoveitemdynamicparameters)]  -->

## <a name="normalizing-a-relative-path"></a><span data-ttu-id="36f9e-203">상대 경로 정규화</span><span class="sxs-lookup"><span data-stu-id="36f9e-203">Normalizing a Relative Path</span></span>

<span data-ttu-id="36f9e-204">탐색 공급자는 매개 변수에 [](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) `path` 지정 된 경로를 기준으로 매개 변수에 지정 된 정규화 된 경로를 정규화 하는 Normalizerelativepath \* 메서드를 구현 합니다. `basePath`</span><span class="sxs-lookup"><span data-stu-id="36f9e-204">Your navigation provider implements the [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) method to normalize the fully-qualified path indicated in the `path` parameter as being relative to the path specified by the `basePath` parameter.</span></span> <span data-ttu-id="36f9e-205">메서드는 정규화 된 경로에 대 한 문자열 표현을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-205">The method returns a string representation of the normalized path.</span></span> <span data-ttu-id="36f9e-206">`path`매개 변수가 존재 하지 않는 경로를 지정 하는 경우 오류를 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-206">It writes an error if the `path` parameter specifies a nonexistent path.</span></span>

<span data-ttu-id="36f9e-207">샘플 탐색 공급자는이 메서드를 재정의 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-207">The sample navigation provider does not override this method.</span></span> <span data-ttu-id="36f9e-208">다음은 기본 구현입니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-208">The following is the default implementation.</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernormalizepath](Msh_samplestestcmdlets#testprovidernormalizepath)]  -->

#### <a name="things-to-remember-about-implementing-normalizerelativepath"></a><span data-ttu-id="36f9e-209">NormalizeRelativePath 구현에 대해 기억할 사항</span><span class="sxs-lookup"><span data-stu-id="36f9e-209">Things to Remember About Implementing NormalizeRelativePath</span></span>

<span data-ttu-id="36f9e-210">[Normalizerelativepath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) 의 구현은 매개 변수를 구문 분석 해야 하지만, 순수 하 게 구문 분석을 사용 하지 않아도 됩니다. `path`</span><span class="sxs-lookup"><span data-stu-id="36f9e-210">Your implementation of [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) should parse the `path` parameter, but it does not have to use purely syntactical parsing.</span></span> <span data-ttu-id="36f9e-211">경로를 사용 하 여 데이터 저장소의 경로 정보를 조회 하 고 대/소문자 구분 및 표준화 된 경로 구문과 일치 하는 경로를 생성 하도록이 메서드를 설계 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-211">You are encouraged to design this method to use the path to look up the path information in the data store and create a path that matches the casing and standardized path syntax.</span></span>

## <a name="code-sample"></a><span data-ttu-id="36f9e-212">코드 예제</span><span class="sxs-lookup"><span data-stu-id="36f9e-212">Code Sample</span></span>

<span data-ttu-id="36f9e-213">전체 샘플 코드는 [AccessDbProviderSample05 코드 샘플](./accessdbprovidersample05-code-sample.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="36f9e-213">For complete sample code, see [AccessDbProviderSample05 Code Sample](./accessdbprovidersample05-code-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="36f9e-214">개체 형식 및 서식 정의</span><span class="sxs-lookup"><span data-stu-id="36f9e-214">Defining Object Types and Formatting</span></span>

<span data-ttu-id="36f9e-215">공급자는 기존 개체에 멤버를 추가 하거나 새 개체를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-215">It is possible for a provider to add members to existing objects or define new objects.</span></span> <span data-ttu-id="36f9e-216">자세한 내용은[개체 형식 확장 및 서식 지정](/previous-versions/ms714665(v=vs.85))을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="36f9e-216">For more information, see[Extending Object Types and Formatting](/previous-versions/ms714665(v=vs.85)).</span></span>

## <a name="building-the-windows-powershell-provider"></a><span data-ttu-id="36f9e-217">Windows PowerShell 공급자 빌드</span><span class="sxs-lookup"><span data-stu-id="36f9e-217">Building the Windows PowerShell provider</span></span>

<span data-ttu-id="36f9e-218">자세한 내용은 [cmdlet, 공급자 및 호스트 응용 프로그램을 등록 하는 방법](/previous-versions/ms714644(v=vs.85))을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="36f9e-218">For more information, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions/ms714644(v=vs.85)).</span></span>

## <a name="testing-the-windows-powershell-provider"></a><span data-ttu-id="36f9e-219">Windows PowerShell 공급자 테스트</span><span class="sxs-lookup"><span data-stu-id="36f9e-219">Testing the Windows PowerShell provider</span></span>

<span data-ttu-id="36f9e-220">Windows powershell 공급자를 Windows PowerShell에 등록 한 경우에는 파생에서 사용할 수 있는 cmdlet을 포함 하 여 명령줄에서 지원 되는 cmdlet을 실행 하 여 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-220">When your Windows PowerShell provider has been registered with Windows PowerShell, you can test it by running the supported cmdlets on the command line, including cmdlets made available by derivation.</span></span> <span data-ttu-id="36f9e-221">이 예제에서는 샘플 탐색 공급자를 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-221">This example will test the sample navigation provider.</span></span>

1. <span data-ttu-id="36f9e-222">새 셸을 실행 하 고 cmdlet을 사용 `Set-Location` 하 여 Access 데이터베이스를 나타내는 경로를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-222">Run your new shell and use the `Set-Location` cmdlet to set the path to indicate the Access database.</span></span>

   ```powershell
   Set-Location mydb:
   ```

2. <span data-ttu-id="36f9e-223">이제 cmdlet을 실행 `Get-Childitem` 하 여 사용 가능한 데이터베이스 테이블인 데이터베이스 항목 목록을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-223">Now run the `Get-Childitem` cmdlet to retrieve a list of the database items, which are the available database tables.</span></span> <span data-ttu-id="36f9e-224">각 테이블에 대해이 cmdlet은 테이블 행의 수도 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-224">For each table, this cmdlet also retrieves the number of table rows.</span></span>

   ```powershell
   Get-ChildItem | Format-Table rowcount,name -AutoSize
   ```

   ```Output
   RowCount   Name
   --------   ----
        180   MSysAccessObjects
          0   MSysACEs
          1   MSysCmdbars
          0   MSysIMEXColumns
          0   MSysIMEXSpecs
          0   MSysObjects
          0   MSysQueries
          7   MSysRelationships
          8   Categories
         91   Customers
          9   Employees
       2155   Order Details
        830   Orders
         77   Products
          3   Shippers
         29   Suppliers
   ```

3. <span data-ttu-id="36f9e-225">Cmdlet을 `Set-Location` 다시 사용 하 여 Employees 데이터 테이블의 위치를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-225">Use the `Set-Location` cmdlet again to set the location of the Employees data table.</span></span>

   ```powershell
   Set-Location Employees
   ```

4. <span data-ttu-id="36f9e-226">이제 cmdlet을 사용 `Get-Location` 하 여 Employees 테이블에 대 한 경로를 검색 해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-226">Let's now use the `Get-Location` cmdlet to retrieve the path to the Employees table.</span></span>

   ```powershell
   Get-Location
   ```

   ```Output
   Path
   ----
   mydb:\Employees
   ```

5. <span data-ttu-id="36f9e-227">이제 `Get-Childitem` cmdlet에 파이프 된 cmdlet을 사용 `Format-Table` 합니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-227">Now use the `Get-Childitem` cmdlet piped to the `Format-Table` cmdlet.</span></span> <span data-ttu-id="36f9e-228">이 cmdlet 집합은 Employees 데이터 테이블 (테이블 행)에 대 한 항목을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-228">This set of cmdlets retrieves the items for the Employees data table, which are the table rows.</span></span> <span data-ttu-id="36f9e-229">Cmdlet에 지정 된 대로 형식이 지정 됩니다 `Format-Table` .</span><span class="sxs-lookup"><span data-stu-id="36f9e-229">They are formatted as specified by the `Format-Table` cmdlet.</span></span>

   ```powershell
   Get-ChildItem | Format-Table rownumber,psiscontainer,data -AutoSize
   ```

   ```Output
   RowNumber   PSIsContainer   Data
   ---------   --------------   ----
   0           False            System.Data.DataRow
   1           False            System.Data.DataRow
   2           False            System.Data.DataRow
   3           False            System.Data.DataRow
   4           False            System.Data.DataRow
   5           False            System.Data.DataRow
   6           False            System.Data.DataRow
   7           False            System.Data.DataRow
   8           False            System.Data.DataRow
   ```

6. <span data-ttu-id="36f9e-230">이제 cmdlet을 실행 `Get-Item` 하 여 Employees 데이터 테이블의 행 0에 대 한 항목을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-230">You can now run the `Get-Item` cmdlet to retrieve the items for row 0 of the Employees data table.</span></span>

   ```powershell
   Get-Item 0
   ```

   ```Output
   PSPath        : AccessDB::C:\PS\Northwind.mdb\Employees\0
   PSParentPath  : AccessDB::C:\PS\Northwind.mdb\Employees
   PSChildName   : 0
   PSDrive       : mydb
   PSProvider    : System.Management.Automation.ProviderInfo
   PSIsContainer : False
   Data           : System.Data.DataRow
   RowNumber      : 0
   ```

7. <span data-ttu-id="36f9e-231">Cmdlet을 `Get-Item` 다시 사용 하 여 0 행의 항목에 대 한 직원 데이터를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="36f9e-231">Use the `Get-Item` cmdlet again to retrieve the employee data for the items in row 0.</span></span>

   ```powershell
   (Get-Item 0).data
   ```

   ```Output
   EmployeeID      : 1
   LastName        : Davis
   FirstName       : Sara
   Title           : Sales Representative
   TitleOfCourtesy : Ms.
   BirthDate       : 12/8/1968 12:00:00 AM
   HireDate        : 5/1/1992 12:00:00 AM
   Address         : 4567 Main Street
                     Apt. 2A
   City            : Buffalo
   Region          : NY
   PostalCode      : 98052
   Country         : USA
   HomePhone       : (206) 555-9857
   Extension       : 5467
   Photo           : EmpID1.bmp
   Notes           : Education includes a BA in psychology from
                     Colorado State University. She also completed "The
                     Art of the Cold Call."  Nancy is a member of
                     Toastmasters International.
   ReportsTo       : 2
   ```

## <a name="see-also"></a><span data-ttu-id="36f9e-232">참고 항목</span><span class="sxs-lookup"><span data-stu-id="36f9e-232">See Also</span></span>

[<span data-ttu-id="36f9e-233">Windows PowerShell 공급자 만들기</span><span class="sxs-lookup"><span data-stu-id="36f9e-233">Creating Windows PowerShell providers</span></span>](./how-to-create-a-windows-powershell-provider.md)

[<span data-ttu-id="36f9e-234">Windows PowerShell 공급자 디자인</span><span class="sxs-lookup"><span data-stu-id="36f9e-234">Design Your Windows PowerShell provider</span></span>](./designing-your-windows-powershell-provider.md)

<span data-ttu-id="36f9e-235">[개체 형식 및 서식 확장](/previous-versions/ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="36f9e-235">[Extending Object Types and Formatting](/previous-versions/ms714665(v=vs.85))</span></span>

[<span data-ttu-id="36f9e-236">컨테이너 Windows PowerShell 공급자 구현</span><span class="sxs-lookup"><span data-stu-id="36f9e-236">Implement a Container Windows PowerShell provider</span></span>](./creating-a-windows-powershell-container-provider.md)

<span data-ttu-id="36f9e-237">[Cmdlet, 공급자 및 호스트 응용 프로그램을 등록 하는 방법](/previous-versions/ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="36f9e-237">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions/ms714644(v=vs.85))</span></span>

[<span data-ttu-id="36f9e-238">Windows PowerShell 프로그래머 가이드</span><span class="sxs-lookup"><span data-stu-id="36f9e-238">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="36f9e-239">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="36f9e-239">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
