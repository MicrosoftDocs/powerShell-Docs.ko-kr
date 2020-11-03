---
description: WMI(Windows Management Instrumentation) (WMI)는 CIM(Common Information Model) (CIM)를 사용 하 여 최신 기업의 시스템, 응용 프로그램, 네트워크, 장치 및 기타 관리 가능한 구성 요소를 나타냅니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_wmi?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_WMI
ms.openlocfilehash: d24b952ee167e51815d6d9920e95bbc9a6bb9608
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93223209"
---
# <a name="about-wmi"></a><span data-ttu-id="c61fc-104">WMI 정보</span><span class="sxs-lookup"><span data-stu-id="c61fc-104">About WMI</span></span>

## <a name="short-description"></a><span data-ttu-id="c61fc-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="c61fc-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="c61fc-106">WMI(Windows Management Instrumentation) (WMI)는 CIM(Common Information Model) (CIM)를 사용 하 여 최신 기업의 시스템, 응용 프로그램, 네트워크, 장치 및 기타 관리 가능한 구성 요소를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c61fc-106">Windows Management Instrumentation (WMI) uses the Common Information Model (CIM) to represent systems, applications, networks, devices, and other manageable components of the modern enterprise.</span></span>

## <a name="long-description"></a><span data-ttu-id="c61fc-107">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="c61fc-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="c61fc-108">WMI(Windows Management Instrumentation) (WMI)는 업계 표준으로, Microsoft의 WBEM (Web-Based Enterprise Management) 구현입니다.</span><span class="sxs-lookup"><span data-stu-id="c61fc-108">Windows Management Instrumentation (WMI) is Microsoft's implementation of Web-Based Enterprise Management (WBEM), the industry standard.</span></span>

<span data-ttu-id="c61fc-109">클래식 WMI는 DCOM을 사용 하 여 원격 시스템을 관리 하는 네트워크 장치와 통신 합니다.</span><span class="sxs-lookup"><span data-stu-id="c61fc-109">Classic WMI uses DCOM to communicate with networked devices to manage remote systems.</span></span> <span data-ttu-id="c61fc-110">Windows PowerShell 3.0에서는 WinRM을 사용 하 여 DCOM에 대 한 종속성을 제거 하는 CIM 공급자 모델을 소개 합니다.</span><span class="sxs-lookup"><span data-stu-id="c61fc-110">Windows PowerShell 3.0 introduces a CIM provider model that uses WinRM to remove the dependency on DCOM.</span></span> <span data-ttu-id="c61fc-111">또한이 CIM 공급자 모델은 개발자가 네이티브 코드 (C)로 Windows PowerShell cmdlet을 작성할 수 있도록 하는 새로운 WMI 공급자 Api를 사용 \+ \+ 합니다.</span><span class="sxs-lookup"><span data-stu-id="c61fc-111">This CIM provider model also uses new WMI provider APIs that enable developers to write Windows PowerShell cmdlets in native code (C\+\+).</span></span>

<span data-ttu-id="c61fc-112">WMI 공급자와 Windows PowerShell 공급자를 혼동 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="c61fc-112">Do not confuse WMI providers with Windows PowerShell providers.</span></span> <span data-ttu-id="c61fc-113">많은 Windows 기능에는 관리 기능을 제공 하는 연결 된 WMI 공급자가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c61fc-113">Many Windows features have an associated WMI provider that exposes their management capabilities.</span></span> <span data-ttu-id="c61fc-114">WMI 공급자를 가져오려면 다음 쿼리와 같이 __Provider WMI 클래스의 인스턴스를 가져오는 WMI 쿼리를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="c61fc-114">To get WMI providers, run a WMI query that gets instances of the __Provider WMI class, such as the following query.</span></span>

```powershell
Get-WmiObject -Class __Provider
```

## <a name="three-components-of-wmi"></a><span data-ttu-id="c61fc-115">WMI의 세 가지 구성 요소</span><span class="sxs-lookup"><span data-stu-id="c61fc-115">THREE COMPONENTS OF WMI</span></span>

<span data-ttu-id="c61fc-116">WMI의 다음 세 가지 구성 요소는 Windows PowerShell과 상호 작용 합니다. 네임 스페이스, 공급자 및 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="c61fc-116">The following three components of WMI interact with Windows PowerShell: Namespaces, Providers, and Classes.</span></span>

<span data-ttu-id="c61fc-117">Wmi 네임 스페이스는 WMI 공급자와 WMI 클래스를 관련 구성 요소 그룹으로 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="c61fc-117">WMI Namespaces organize WMI providers and WMI classes into groups of related components.</span></span> <span data-ttu-id="c61fc-118">이러한 방식으로 .NET Framework 네임 스페이스와 유사 합니다.</span><span class="sxs-lookup"><span data-stu-id="c61fc-118">In this way, they are similar to .NET Framework namespaces.</span></span>
<span data-ttu-id="c61fc-119">네임 스페이스는 물리적 위치가 아니라 논리적 데이터베이스와 유사 합니다.</span><span class="sxs-lookup"><span data-stu-id="c61fc-119">Namespaces are not physical locations, but are more like logical databases.</span></span>
<span data-ttu-id="c61fc-120">모든 WMI 네임 스페이스는 __Namespace 시스템 클래스의 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="c61fc-120">All WMI namespaces are instances of the __Namespace system class.</span></span> <span data-ttu-id="c61fc-121">기본 WMI 네임 스페이스는 Root \/ CIMV2 (Microsoft Windows 2000 이후)입니다.</span><span class="sxs-lookup"><span data-stu-id="c61fc-121">The default WMI namespace is Root\/CIMV2 (since Microsoft Windows 2000).</span></span> <span data-ttu-id="c61fc-122">Windows PowerShell을 사용 하 여 현재 세션에서 WMI 네임 스페이스를 가져오려면 다음 형식의 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c61fc-122">To use Windows PowerShell to get WMI namespaces in the current session, use a command with the following format.</span></span>

```powershell
Get-WmiObject -Class __Namespace
```

<span data-ttu-id="c61fc-123">다른 네임 스페이스에 있는 WMI 네임 스페이스를 가져오려면 Namespace 매개 변수를 사용 하 여 검색 위치를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="c61fc-123">To get WMI namespaces in other namespaces, use the Namespace parameter to change the location of the search.</span></span> <span data-ttu-id="c61fc-124">다음 명령은 Root/Cimv2/Applications 네임 스페이스에 상주 하는 WMI 네임 스페이스를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="c61fc-124">The following command finds WMI namespaces that reside in the Root/Cimv2/Applications namespace.</span></span>

```powershell
Get-WmiObject -Class __Namespace -Namespace root/CIMv2/applications
```

<span data-ttu-id="c61fc-125">WMI 네임 스페이스는 계층 구조입니다.</span><span class="sxs-lookup"><span data-stu-id="c61fc-125">WMI namespaces are hierarchical.</span></span> <span data-ttu-id="c61fc-126">따라서 특정 시스템에서 모든 네임 스페이스 목록을 가져오려면 루트 네임 스페이스에서 시작 하는 재귀 쿼리를 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c61fc-126">Therefore, obtaining a list of all namespaces on a particular system requires performing a recursive query starting at the root namespace.</span></span>

<span data-ttu-id="c61fc-127">WMI 공급자는 Windows 관리 가능한 개체에 대 한 정보를 노출 합니다.</span><span class="sxs-lookup"><span data-stu-id="c61fc-127">WMI Providers expose information about Windows manageable objects.</span></span> <span data-ttu-id="c61fc-128">공급자는 구성 요소에서 데이터를 검색 하 고 WMI를 통해 Windows PowerShell과 같은 관리 응용 프로그램으로 해당 데이터를 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="c61fc-128">A provider retrieves data from a component, and passes that data through WMI to a management application, such as Windows PowerShell.</span></span> <span data-ttu-id="c61fc-129">대부분의 WMI 공급자는 동적 공급자 이므로 관리 응용 프로그램을 통해 요청 될 때 데이터를 동적으로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c61fc-129">Most WMI providers are dynamic providers, which means that they obtain the data dynamically when it is requested through the management application.</span></span>

## <a name="finding-wmi-classes"></a><span data-ttu-id="c61fc-130">WMI 클래스 찾기</span><span class="sxs-lookup"><span data-stu-id="c61fc-130">FINDING WMI CLASSES</span></span>

<span data-ttu-id="c61fc-131">Windows 8의 기본 설치에서 Root Cimv2에는 1100 개가 넘는 WMI 클래스가 있습니다 \/ .</span><span class="sxs-lookup"><span data-stu-id="c61fc-131">In a default installation of Windows 8, there are more than 1,100 WMI classes in Root\/Cimv2.</span></span> <span data-ttu-id="c61fc-132">이 많은 WMI 클래스를 사용 하면 특정 작업을 수행 하는 데 사용할 적절 한 WMI 클래스를 식별 하 게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c61fc-132">With this many WMI classes, the challenge becomes identifying the appropriate WMI class to use to perform a specific task.</span></span> <span data-ttu-id="c61fc-133">Windows PowerShell 3.0에서는 두 가지 방법으로 특정 항목과 관련 된 WMI 클래스를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c61fc-133">Windows PowerShell 3.0 provides two ways to find WMI classes that are related to a specific topic.</span></span>

<span data-ttu-id="c61fc-134">예를 들어, \\ 디스크와 관련 된 루트 CIMV2 wmi 네임 스페이스에서 wmi 클래스를 찾으려면 여기에 표시 된 것과 같은 쿼리를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c61fc-134">For example,to find WMI classes in the root\\CIMV2 WMI namespace that are related to disks, you can use a query such as the one shown here.</span></span>

```powershell
Get-WmiObject -List *disk*
```

<span data-ttu-id="c61fc-135">메모리와 관련 된 WMI 클래스를 찾으려면 여기에 표시 된 것과 같은 쿼리를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c61fc-135">To find WMI classes that are related to memory, you might use a query such as the one shown here.</span></span>

```powershell
Get-WmiObject -List *memory*
```

<span data-ttu-id="c61fc-136">CIM cmdlet은 WMI 클래스를 검색 하는 기능도 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="c61fc-136">The CIM cmdlets also provide the ability to discover WMI classes.</span></span> <span data-ttu-id="c61fc-137">이렇게 하려면 Get-CIMClass cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c61fc-137">To do this, use the Get-CIMClass cmdlet.</span></span> <span data-ttu-id="c61fc-138">여기에 표시 된 명령은 비디오와 관련 된 WMI 클래스를 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="c61fc-138">The command shown here lists WMI classes related to video.</span></span>

```powershell
Get-CimClass *video*
```

<span data-ttu-id="c61fc-139">탭 확장은 WMI 네임 스페이스를 변경할 때 작동 하므로 탭 확장을 사용 하면 하위 WMI 네임 스페이스를 쉽게 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c61fc-139">Tab expansion works when changing WMI namespaces, and therefore use of tab expansion makes sub-WMI namespaces easily discoverable.</span></span> <span data-ttu-id="c61fc-140">다음 예제에서 Get-CimClass cmdlet은 전원 설정과 관련 된 WMI 클래스를 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="c61fc-140">In the following example, the Get-CimClass cmdlet lists WMI classes related to power settings.</span></span>
<span data-ttu-id="c61fc-141">이를 찾으려면 네임 스페이스를 입력 한 `root/CIMV2/` 다음 power 네임 스페이스가 나타날 때까지 tab 키를 여러 번 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="c61fc-141">To find it, type the `root/CIMV2/` namespace and then press the Tab key several times until the power namespace appears.</span></span> <span data-ttu-id="c61fc-142">명령은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c61fc-142">Here is the command:</span></span>

```powershell
Get-CimClass *power* -Namespace root/cimv2/power
```
