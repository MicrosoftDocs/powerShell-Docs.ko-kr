---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Windows PowerShell 2.0 엔진 설치
ms.openlocfilehash: 24bca7bd18fd33392f4f79b958189d3251ec35c1
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75870543"
---
# <a name="installing-the-windows-powershell-20-engine"></a><span data-ttu-id="e9d2c-103">Windows PowerShell 2.0 엔진 설치</span><span class="sxs-lookup"><span data-stu-id="e9d2c-103">Installing the Windows PowerShell 2.0 Engine</span></span>

<span data-ttu-id="e9d2c-104">이 항목에서는 Windows PowerShell 2.0 엔진을 설치하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e9d2c-104">This topic explains how to install the Windows PowerShell 2.0 Engine.</span></span>

<span data-ttu-id="e9d2c-105">Windows PowerShell 3.0은 이전 버전인 Windows PowerShell 2.0과 호환되도록 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e9d2c-105">Windows PowerShell 3.0 is designed to be backwards compatible with Windows PowerShell 2.0.</span></span> <span data-ttu-id="e9d2c-106">Windows PowerShell 2.0 및 Windows PowerShell 3.0용으로 작성된 cmdlet, 공급자, 스냅인, 모듈 및 스크립트는 Windows PowerShell 4.0에서 변경하지 않고 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="e9d2c-106">Cmdlets, providers, snap-ins, modules, and scripts written for Windows PowerShell 2.0 run unchanged in Windows PowerShell 3.0 and Windows PowerShell 4.0.</span></span> <span data-ttu-id="e9d2c-107">그러나 Microsoft .NET Framework 4의 런타임 정품 인증 정책 변경으로 인해 Windows PowerShell 2.0용으로 작성되고 CLR(공용 언어 런타임) 2.0으로 컴파일된 Windows PowerShell 호스트 프로그램은 CLR 4.0으로 컴파일된 Windows PowerShell의 이후 릴리스에서 수정 없이 실행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e9d2c-107">However, due to a change in the runtime activation policy in Microsoft .NET Framework 4, Windows PowerShell host programs that were written for Windows PowerShell 2.0 and compiled with Common Language Runtime (CLR) 2.0 cannot run without modification in later releases of Windows PowerShell, which is compiled with CLR 4.0.</span></span>

<span data-ttu-id="e9d2c-108">이러한 변경의 영향을 받는 이전 버전의 명령 및 호스트 프로그램과 호환성을 유지하기 위해 Windows PowerShell 2.0, Windows PowerShell 3.0 및 Windows PowerShell 4.0 엔진은 나란히 실행되도록 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e9d2c-108">To maintain backward compatibility with commands and host programs that are affected by these changes, the Windows PowerShell 2.0, Windows PowerShell 3.0, and Windows PowerShell 4.0 engines are designed to run side-by-side.</span></span> <span data-ttu-id="e9d2c-109">또한 Windows Server 2012 R2, Windows 8.1, Windows 8, Windows Server 2012 및 Windows Management Framework 3.0에는 Windows PowerShell 2.0 엔진이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e9d2c-109">Also, the Windows PowerShell 2.0 Engine is included in Windows Server 2012 R2, Windows 8.1, Windows 8, Windows Server 2012, and Windows Management Framework 3.0.</span></span> <span data-ttu-id="e9d2c-110">Windows PowerShell 2.0 엔진은 기존 스크립트 또는 호스트 프로그램이 Windows PowerShell 3.0, Windows PowerShell 4.0 또는 Microsoft .NET Framework 4와 호환되지 않아 실행할 수 없는 경우에만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e9d2c-110">The Windows PowerShell 2.0 Engine is intended to be used only when an existing script or host program cannot run because it is incompatible with Windows PowerShell 3.0, Windows PowerShell 4.0, or Microsoft .NET Framework 4.</span></span> <span data-ttu-id="e9d2c-111">이러한 경우는 많지 않을 것으로 예상됩니다.</span><span class="sxs-lookup"><span data-stu-id="e9d2c-111">Such cases are expected to be rare.</span></span>

<span data-ttu-id="e9d2c-112">Windows PowerShell 2.0 엔진은 Windows Server 2012 R2, Windows 8.1, Windows® 8 및 Windows Server® 2012의 선택적 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="e9d2c-112">The Windows PowerShell 2.0 Engine is an optional feature of Windows Server 2012 R2, Windows 8.1, Windows® 8 and Windows Server® 2012.</span></span> <span data-ttu-id="e9d2c-113">이전 버전의 Windows에서 Windows Management Framework 3.0을 설치하면 Windows PowerShell 3.0 설치가 Windows PowerShell 설치 디렉터리의 Windows PowerShell 2.0 설치를 완전히 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="e9d2c-113">On earlier versions of Windows, when you install Windows Management Framework 3.0, the Windows PowerShell 3.0 installation completely replaces the Windows PowerShell 2.0 installation in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="e9d2c-114">그러나 Windows PowerShell 2.0 엔진은 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="e9d2c-114">However, the Windows PowerShell 2.0 Engine is retained.</span></span>

<span data-ttu-id="e9d2c-115">Windows PowerShell 2.0 엔진을 시작하는 방법에 대한 자세한 내용은 [Windows PowerShell 2.0 엔진 시작](../getting-started/Starting-the-Windows-PowerShell-2.0-Engine.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e9d2c-115">For information about starting the Windows PowerShell 2.0 Engine, see [Starting the Windows PowerShell 2.0 Engine](../getting-started/Starting-the-Windows-PowerShell-2.0-Engine.md).</span></span>

## <a name="on-windows-81-and-windows-8"></a><span data-ttu-id="e9d2c-116">Windows 8.1 및 Windows 8에서</span><span class="sxs-lookup"><span data-stu-id="e9d2c-116">On Windows 8.1 and Windows 8</span></span>

<span data-ttu-id="e9d2c-117">Windows 8.1 및 Windows 8에서는 Windows PowerShell 2.0 엔진 기능이 기본적으로 설정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e9d2c-117">On Windows 8.1 and Windows 8, the Windows PowerShell 2.0 Engine feature is turned on by default.</span></span>
<span data-ttu-id="e9d2c-118">그러나 이 기능을 사용하려면 필요한 Microsoft .NET Framework 3.5에 대한 옵션을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9d2c-118">However, to use it, you need to turn on the option for Microsoft .NET Framework 3.5, which it requires.</span></span> <span data-ttu-id="e9d2c-119">이 섹션에서는 Windows PowerShell 2.0 엔진 기능을 설정 및 해제하는 방법도 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e9d2c-119">This section also explains how to turn the Windows PowerShell 2.0 Engine feature on and off.</span></span>

#### <a name="to-turn-on-net-framework-35"></a><span data-ttu-id="e9d2c-120">.NET Framework 3.5를 설정하려면</span><span class="sxs-lookup"><span data-stu-id="e9d2c-120">To turn on .NET Framework 3.5</span></span>

1. <span data-ttu-id="e9d2c-121">**시작** 화면에서 **Windows 기능**을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e9d2c-121">On the **Start** screen, type **Windows Features**.</span></span>
2. <span data-ttu-id="e9d2c-122">**앱** 바에서 **설정**을 클릭한 다음 **Windows 기능 설정 또는 해제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e9d2c-122">On the **Apps** bar, click **Settings**, and then click **Turn Windows features on or off**.</span></span>
3. <span data-ttu-id="e9d2c-123">**Windows 기능** 상자에서 **.NET Framework 3.5(.NET 2.0 및 3.0 포함)** 을 클릭하여 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e9d2c-123">In the **Windows Features** box, click **.NET Framework 3.5 (includes .NET 2.0 and 3.0** to select it.</span></span>

   <span data-ttu-id="e9d2c-124">**.NET Framework 3.5(.NET 2.0 및 3.0 포함)** 를 선택하면 상자가 채워져 기능의 일부만 선택되었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e9d2c-124">When you select **.NET Framework 3.5 (includes .NET 2.0 and 3.0**, the box fills to indicate that only part of the feature is selected.</span></span> <span data-ttu-id="e9d2c-125">그러나 Windows PowerShell 2.0 엔진에는 이것만으로 충분합니다.</span><span class="sxs-lookup"><span data-stu-id="e9d2c-125">However, this is sufficient for the Windows PowerShell 2.0 Engine.</span></span>

#### <a name="to-turn-the-windows-powershell-20-engine-on-and-off"></a><span data-ttu-id="e9d2c-126">Windows PowerShell 2.0 엔진을 설정 및 해제하려면</span><span class="sxs-lookup"><span data-stu-id="e9d2c-126">To turn the Windows PowerShell 2.0 Engine on and off</span></span>

1. <span data-ttu-id="e9d2c-127">**시작** 화면에서 **Windows 기능**을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e9d2c-127">On the **Start** screen, type **Windows Features**.</span></span>

2. <span data-ttu-id="e9d2c-128">**앱** 바에서 **설정**을 클릭한 다음 **Windows 기능 설정 또는 해제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e9d2c-128">On the **Apps** bar, click **Settings**, and then click **Turn Windows features on or off**.</span></span>

3. <span data-ttu-id="e9d2c-129">**Windows 기능** 상자에서 **Windows PowerShell 2.0** 노드를 확장하고 **Windows PowerShell 2.0 엔진** 상자를 클릭하여 선택하거나 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="e9d2c-129">In the **Windows Features** box, expand the **Windows PowerShell 2.0** node, and click the **Windows PowerShell 2.0 Engine** box to select or clear it.</span></span>

## <a name="on-windows-server-2012-r2-and-windows-server-2012"></a><span data-ttu-id="e9d2c-130">Windows Server 2012 R2 및 Windows Server 2012에서</span><span class="sxs-lookup"><span data-stu-id="e9d2c-130">On Windows Server 2012 R2 and Windows Server 2012</span></span>

<span data-ttu-id="e9d2c-131">Windows PowerShell 2.0 엔진과 Microsoft .NET Framework 3.5 기능을 추가하려면 다음 절차를 따르세요.</span><span class="sxs-lookup"><span data-stu-id="e9d2c-131">Use the following procedures to add the Windows PowerShell 2.0 Engine and Microsoft .NET Framework 3.5 features.</span></span> <span data-ttu-id="e9d2c-132">Windows PowerShell 2.0 엔진에는 최소한 Microsoft .NET Framework 2.0.50727이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="e9d2c-132">The Windows PowerShell 2.0 Engine requires Microsoft .NET Framework 2.0.50727 at a minimum.</span></span> <span data-ttu-id="e9d2c-133">이 요구 사항은 Microsoft .NET Framework 3.5에 의해 충족됩니다.</span><span class="sxs-lookup"><span data-stu-id="e9d2c-133">This requirement is fulfilled by Microsoft .NET Framework 3.5.</span></span>

#### <a name="to-add-the-net-framework-35-feature"></a><span data-ttu-id="e9d2c-134">.NET Framework 3.5 기능을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="e9d2c-134">To add the .NET Framework 3.5 feature</span></span>

1. <span data-ttu-id="e9d2c-135">**서버 관리자**의 **관리** 메뉴에서 **역할 및 기능 추가**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e9d2c-135">In **Server Manager**, from the **Manage** menu, select **Add Roles and Features**.</span></span>

    <span data-ttu-id="e9d2c-136">또는 **서버 관리자**에서 **모든 서버**를 클릭하고 서버 이름을 마우스 오른쪽 단추로 클릭한 다음 **역할 및 기능 추가**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e9d2c-136">Or in **Server Manager**, click **All Servers**, right-click a server name, and then select  **Add Roles and Features**.</span></span>

2. <span data-ttu-id="e9d2c-137">**설치 유형** 페이지에서 **역할 기반 또는 기능 기반 설치**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e9d2c-137">On the **Installation Type** page, select **Role-based or feature-based installation**.</span></span>

3. <span data-ttu-id="e9d2c-138">**기능** 페이지에서 **.NET 3.5 Framework 기능** 노드를 확장하고 **.NET Framework 3.5(.NET 2.0 및 3.0 포함)** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e9d2c-138">On the **Features** page, expand the **.NET 3.5 Framework Features** node and select **.NET Framework 3.5 (includes .NET 2.0 and 3.0)**.</span></span>

   <span data-ttu-id="e9d2c-139">해당 노드 아래에 있는 다른 옵션은 Windows PowerShell 2.0 엔진에 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e9d2c-139">The other options under that node are not required for the Windows PowerShell 2.0 Engine.</span></span>

#### <a name="to-add-the-windows-powershell-20-engine-feature"></a><span data-ttu-id="e9d2c-140">Windows PowerShell 2.0 엔진 기능을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="e9d2c-140">To add the Windows PowerShell 2.0 Engine feature</span></span>

- <span data-ttu-id="e9d2c-141">**서버 관리자**의 **관리** 메뉴에서 **역할 및 기능 추가**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e9d2c-141">In **Server Manager**, from the **Manage** menu, select **Add Roles and Features**.</span></span>

  <span data-ttu-id="e9d2c-142">또는 **서버 관리자**에서 **모든 서버**를 클릭하고 서버 이름 마우스 오른쪽 단추로 클릭한 다음 **역할 및 기능 추가**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e9d2c-142">Or **Server Manager**, click **All Servers**, right-click a server name, and then select **Add Roles and Features**.</span></span>

- <span data-ttu-id="e9d2c-143">**설치 유형** 페이지에서 **역할 기반 또는 기능 기반 설치**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e9d2c-143">On the **Installation Type** page, select **Role-based or feature-based installation**.</span></span>

- <span data-ttu-id="e9d2c-144">**기능** 페이지에서 **Windows PowerShell(설치됨)** 노드를 확장하고 **Windows PowerShell 2.0 엔진**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e9d2c-144">On the **Features** page, expand the **Windows PowerShell (Installed)** node and select **Windows PowerShell 2.0 Engine**.</span></span>

<span data-ttu-id="e9d2c-145">Windows PowerShell 2.0 엔진을 시작하는 방법에 대한 자세한 내용은 [Windows PowerShell 2.0 엔진 시작](../getting-started/Starting-the-Windows-PowerShell-2.0-Engine.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e9d2c-145">For information about starting the Windows PowerShell 2.0 Engine, see [Starting the Windows PowerShell 2.0 Engine](../getting-started/Starting-the-Windows-PowerShell-2.0-Engine.md).</span></span>

## <a name="on-earlier-systems"></a><span data-ttu-id="e9d2c-146">이전 시스템</span><span class="sxs-lookup"><span data-stu-id="e9d2c-146">On Earlier Systems</span></span>

<span data-ttu-id="e9d2c-147">Windows 7, Windows Server 2008 R2 및 Windows Server 2012에 Windows PowerShell 4.0을 설치하는 [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/?LinkID=293881) 패키지에는 Windows PowerShell 2.0 엔진이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e9d2c-147">The [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/?LinkID=293881) package that installs Windows PowerShell 4.0 on Windows 7, Windows Server 2008 R2, and Windows Server 2012, includes the Windows PowerShell 2.0 Engine.</span></span> <span data-ttu-id="e9d2c-148">추가 설치, 설정 또는 구성 없이 Windows PowerShell 2.0 엔진을 사용할 수 있고 사용할 준비가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e9d2c-148">The Windows PowerShell 2.0 Engine is enabled and ready to use, if necessary, without additional installation, setup, or configuration.</span></span>

<span data-ttu-id="e9d2c-149">Windows 7, Windows Server 2008 R2 및 Windows Server 2008에 Windows PowerShell 3.0을 설치하는 Windows Management Framework 3.0 패키지에는 Windows PowerShell 2.0 엔진이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e9d2c-149">The Windows Management Framework 3.0 package that installs Windows PowerShell 3.0 on Windows 7, Windows Server 2008 R2, and Windows Server 2008, includes the Windows PowerShell 2.0 Engine.</span></span> <span data-ttu-id="e9d2c-150">추가 설치, 설정 또는 구성 없이 Windows PowerShell 2.0 엔진을 사용할 수 있고 사용할 준비가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e9d2c-150">The Windows PowerShell 2.0 Engine is enabled and ready to use, if necessary, without additional installation, setup, or configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="e9d2c-151">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e9d2c-151">See Also</span></span>

- [<span data-ttu-id="e9d2c-152">Windows PowerShell 시스템 요구 사항</span><span class="sxs-lookup"><span data-stu-id="e9d2c-152">Windows PowerShell System Requirements</span></span>](Windows-PowerShell-System-Requirements.md)
- [<span data-ttu-id="e9d2c-153">Windows PowerShell 설치</span><span class="sxs-lookup"><span data-stu-id="e9d2c-153">Installing Windows PowerShell</span></span>](Installing-Windows-PowerShell.md)
- <span data-ttu-id="e9d2c-154">[Windows PowerShell 시작](/previous-versions/ms714415(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="e9d2c-154">[Starting Windows PowerShell](/previous-versions/ms714415(v=vs.85))</span></span>
- [<span data-ttu-id="e9d2c-155">Windows PowerShell 2.0 엔진 시작</span><span class="sxs-lookup"><span data-stu-id="e9d2c-155">Starting the Windows PowerShell 2.0 Engine</span></span>](../getting-started/Starting-the-Windows-PowerShell-2.0-Engine.md)
