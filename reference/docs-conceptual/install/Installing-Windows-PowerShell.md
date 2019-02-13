---
ms.date: 08/09/2017
keywords: powershell,cmdlet,다운로드,설치,설정,windows 10, windows 8.1, windows 8.0,windows 7
title: Windows PowerShell 설치
ms.openlocfilehash: 37f28c2af5a11af26d9110cc6c5f7612124be557
ms.sourcegitcommit: 10c347a8c3dcbf8962295601834f5ba85342a87b
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55887619"
---
# <a name="installing-windows-powershell"></a><span data-ttu-id="675cf-103">Windows PowerShell 설치</span><span class="sxs-lookup"><span data-stu-id="675cf-103">Installing Windows PowerShell</span></span>

<span data-ttu-id="675cf-104">Windows PowerShell은 Windows 7 SP1 및 Windows Server 2008 R2 SP1부터 모든 Windows에 기본적으로 설치되어 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="675cf-104">Windows PowerShell comes installed by default in every Windows, starting with Windows 7 SP1 and Windows Server 2008 R2 SP1.</span></span>

<span data-ttu-id="675cf-105">PowerShell 6 이상에 관심이 있는 경우 Windows PowerShell 대신 PowerShell Core를 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="675cf-105">If you are interested in PowerShell 6 and later, you need to install PowerShell Core instead of Windows PowerShell.</span></span> <span data-ttu-id="675cf-106">이 경우 [Windows에서 PowerShell Core 설치](Installing-PowerShell-Core-on-Windows.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="675cf-106">For that, see [Installing PowerShell Core on Windows](Installing-PowerShell-Core-on-Windows.md).</span></span>

## <a name="finding-powershell-in-windows-10-81-80-and-7"></a><span data-ttu-id="675cf-107">Windows 10, 8.1, 8.0 및 7에서 PowerShell 찾기</span><span class="sxs-lookup"><span data-stu-id="675cf-107">Finding PowerShell in Windows 10, 8.1, 8.0, and 7</span></span>

<span data-ttu-id="675cf-108">Windows 버전에 따라 위치가 바뀌므로 때때로 Windows에서 PowerShell 콘솔 또는 ISE(통합 스크립팅 환경)를 찾기가 어려울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="675cf-108">Sometimes locating PowerShell console or ISE (Integrated Scripting Environment) in Windows can be difficult, as its location moves from one version of Windows to the next.</span></span>

<span data-ttu-id="675cf-109">다음 표는 사용 중인 Windows 버전에서 PowerShell을 찾는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="675cf-109">The following tables should help you find PowerShell in your Windows version.</span></span>
<span data-ttu-id="675cf-110">여기에 나열된 모든 버전은 업데이트가 포함되지 않은 릴리스된 원래 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="675cf-110">All versions listed here are the original version, as released, with no updates.</span></span>

### <a name="for-console"></a><span data-ttu-id="675cf-111">콘솔의 경우</span><span class="sxs-lookup"><span data-stu-id="675cf-111">For Console</span></span>

<span data-ttu-id="675cf-112">버전</span><span class="sxs-lookup"><span data-stu-id="675cf-112">Version</span></span> | <span data-ttu-id="675cf-113">위치</span><span class="sxs-lookup"><span data-stu-id="675cf-113">Location</span></span>
-- | --
<span data-ttu-id="675cf-114">Windows 10</span><span class="sxs-lookup"><span data-stu-id="675cf-114">Windows 10</span></span> | <span data-ttu-id="675cf-115">왼쪽 아래 모서리에 있는 Windows 아이콘을 클릭하고 PowerShell 입력을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="675cf-115">Click left lower corner Windows icon, start typing PowerShell</span></span>
<span data-ttu-id="675cf-116">Windows 8.1, 8.0</span><span class="sxs-lookup"><span data-stu-id="675cf-116">Windows 8.1, 8.0</span></span> | <span data-ttu-id="675cf-117">시작 화면에서 PowerShell 입력을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="675cf-117">On the start screen, start typing PowerShell.</span></span><br/><span data-ttu-id="675cf-118">바탕 화면에 있는 경우 왼쪽 아래 모서리에 있는 Windows 아이콘을 클릭하고 PowerShell 입력을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="675cf-118">If on desktop, click left lower corner Windows icon, start typing PowerShell</span></span>
<span data-ttu-id="675cf-119">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="675cf-119">Windows 7 SP1</span></span> | <span data-ttu-id="675cf-120">왼쪽 아래 모서리에 있는 Windows 아이콘을 클릭하고 검색 상자에서 PowerShell 입력을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="675cf-120">Click left lower corner Windows icon, on the search box start typing PowerShell</span></span>

### <a name="for-ise"></a><span data-ttu-id="675cf-121">ISE의 경우</span><span class="sxs-lookup"><span data-stu-id="675cf-121">For ISE</span></span>

<span data-ttu-id="675cf-122">버전</span><span class="sxs-lookup"><span data-stu-id="675cf-122">Version</span></span> | <span data-ttu-id="675cf-123">위치</span><span class="sxs-lookup"><span data-stu-id="675cf-123">Location</span></span>
-- | --
<span data-ttu-id="675cf-124">Windows 10</span><span class="sxs-lookup"><span data-stu-id="675cf-124">Windows 10</span></span> | <span data-ttu-id="675cf-125">왼쪽 아래 모서리에 있는 Windows 아이콘을 클릭하고 ISE 입력을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="675cf-125">Click left lower corner Windows icon, start typing ISE</span></span>
<span data-ttu-id="675cf-126">Windows 8.1, 8.0</span><span class="sxs-lookup"><span data-stu-id="675cf-126">Windows 8.1, 8.0</span></span> | <span data-ttu-id="675cf-127">시작 화면에서 **PowerShell ISE**를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="675cf-127">On the start screen, type **PowerShell ISE**.</span></span><br/><span data-ttu-id="675cf-128">바탕 화면에 있는 경우 왼쪽 아래 모서리에 있는 Windows 아이콘을 클릭하고 **PowerShell ISE**를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="675cf-128">If on desktop, click left lower corner Windows icon, type **PowerShell ISE**</span></span>
<span data-ttu-id="675cf-129">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="675cf-129">Windows 7 SP1</span></span> | <span data-ttu-id="675cf-130">왼쪽 아래 모서리에 있는 Windows 아이콘을 클릭하고 검색 상자에서 PowerShell 입력을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="675cf-130">Click left lower corner Windows icon, on the search box start typing PowerShell</span></span>

## <a name="finding-powershell-in-windows-server-versions"></a><span data-ttu-id="675cf-131">Windows Server 버전에서 PowerShell 찾기</span><span class="sxs-lookup"><span data-stu-id="675cf-131">Finding PowerShell in Windows Server versions</span></span>

<span data-ttu-id="675cf-132">Windows Server 2008 R2부터 GUI(그래픽 사용자 인터페이스) 없이 Windows 운영 체제를 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="675cf-132">Starting with Windows Server 2008 R2, Windows operating system can be installed without the graphical user interface (GUI).</span></span>
<span data-ttu-id="675cf-133">GUI가 없는 Windows Server 버전은 이름이 **Core** 버전으로 지정되고 GUI가 있는 버전은 이름이 **Desktop**으로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="675cf-133">Editions of Windows Server without GUI are named **Core** editions, and editions with the GUI are named **Desktop**.</span></span>

### <a name="windows-server-core-editions"></a><span data-ttu-id="675cf-134">Windows Server Core 버전</span><span class="sxs-lookup"><span data-stu-id="675cf-134">Windows Server Core editions</span></span>

<span data-ttu-id="675cf-135">모든 Core 버전에서는 서버에 로그온하면 Windows 명령 프롬프트 창이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="675cf-135">In all Core editions, when you log to the server you get a Windows command prompt window.</span></span>

<span data-ttu-id="675cf-136">`powershell`을 입력하고 **Enter** 키를 눌러 명령 프롬프트 세션 내에서 PowerShell을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="675cf-136">Type `powershell` and press **ENTER** to start PowerShell inside the command prompt session.</span></span>
<span data-ttu-id="675cf-137">`exit`를 입력하여 PowerShell 세션을 종료하고 명령 프롬프트로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="675cf-137">Type `exit` to terminate the PowerShell session and return to command prompt.</span></span>

### <a name="windows-server-desktop-editions"></a><span data-ttu-id="675cf-138">Windows Server Desktop 버전</span><span class="sxs-lookup"><span data-stu-id="675cf-138">Windows Server Desktop editions</span></span>

<span data-ttu-id="675cf-139">모든 Desktop 버전에서는 왼쪽 아래 모서리에 있는 Windows 아이콘을 클릭하고 PowerShell 입력을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="675cf-139">In all desktop editions, click the left lower corner Windows icon, start typing PowerShell.</span></span>
<span data-ttu-id="675cf-140">콘솔 및 ISE 옵션을 모두 이용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="675cf-140">You get both console and ISE options.</span></span>

<span data-ttu-id="675cf-141">위 규칙에 대한 유일한 예외는 Windows Server 2008 R2 SP1의 ISE입니다. 이 경우에는 왼쪽 아래 모서리에 있는 Windows 아이콘을 클릭하고 PowerShell ISE를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="675cf-141">The only exception to the above rule is the ISE in Windows Server 2008 R2 SP1; in this case, click the left lower corner Windows icon, type PowerShell ISE.</span></span>

## <a name="how-to-check-the-version-of-powershell"></a><span data-ttu-id="675cf-142">PowerShell 버전을 확인하는 방법</span><span class="sxs-lookup"><span data-stu-id="675cf-142">How to check the version of PowerShell</span></span>

<span data-ttu-id="675cf-143">설치한 PowerShell 버전을 찾으려면 PowerShell 콘솔(또는 ISE)을 시작하고 `$PSVersionTable`을 입력한 다음 **Enter** 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="675cf-143">To find which version of PowerShell you have installed, start a PowerShell console (or the ISE) and type `$PSVersionTable` and press **ENTER**.</span></span> <span data-ttu-id="675cf-144">`PSVersion` 값을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="675cf-144">Look for the `PSVersion` value.</span></span>

## <a name="upgrading-existing-windows-powershell"></a><span data-ttu-id="675cf-145">기존 Windows PowerShell 업그레이드</span><span class="sxs-lookup"><span data-stu-id="675cf-145">Upgrading existing Windows PowerShell</span></span>

<span data-ttu-id="675cf-146">PowerShell 설치 패키지는 WMF 설치 관리자 내에 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="675cf-146">The installation package for PowerShell comes inside a WMF installer.</span></span>
<span data-ttu-id="675cf-147">WMF 설치 관리자 버전은 PowerShell 버전과 일치합니다. Windows PowerShell용 독립 실행형 설치 관리자는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="675cf-147">The version of the WMF installer matches the version of PowerShell; there's no stand alone installer for Windows PowerShell.</span></span>

<span data-ttu-id="675cf-148">Windows에서 기존 PowerShell 버전을 업데이트해야 할 경우 다음 표를 사용하여 업데이트하려는 PowerShell 버전의 설치 관리자를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="675cf-148">If you need to update your existing version of PowerShell, in Windows, use the following table to locate the installer for the version of PowerShell you want to update to.</span></span>

<span data-ttu-id="675cf-149">Windows</span><span class="sxs-lookup"><span data-stu-id="675cf-149">Windows</span></span> | <span data-ttu-id="675cf-150">PS 3.0</span><span class="sxs-lookup"><span data-stu-id="675cf-150">PS 3.0</span></span> | <span data-ttu-id="675cf-151">PS 4.0</span><span class="sxs-lookup"><span data-stu-id="675cf-151">PS 4.0</span></span> | <span data-ttu-id="675cf-152">PS 5.0</span><span class="sxs-lookup"><span data-stu-id="675cf-152">PS 5.0</span></span> | <span data-ttu-id="675cf-153">PS 5.1</span><span class="sxs-lookup"><span data-stu-id="675cf-153">PS 5.1</span></span> |
--|--|--|--|--|
<span data-ttu-id="675cf-154">Windows 10(참고 1 참조)</span><span class="sxs-lookup"><span data-stu-id="675cf-154">Windows 10 (see Note1)</span></span><br/><span data-ttu-id="675cf-155">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="675cf-155">Windows Server 2016</span></span> | - | - | - | <span data-ttu-id="675cf-156">설치됨</span><span class="sxs-lookup"><span data-stu-id="675cf-156">installed</span></span>
<span data-ttu-id="675cf-157">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="675cf-157">Windows 8.1</span></span><br/><span data-ttu-id="675cf-158">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="675cf-158">Windows Server 2012 R2</span></span> | - | <span data-ttu-id="675cf-159">설치됨</span><span class="sxs-lookup"><span data-stu-id="675cf-159">installed</span></span> | [<span data-ttu-id="675cf-160">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="675cf-160">WMF 5.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [<span data-ttu-id="675cf-161">WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="675cf-161">WMF 5.1</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=54616)
<span data-ttu-id="675cf-162">Windows 8</span><span class="sxs-lookup"><span data-stu-id="675cf-162">Windows 8</span></span><br/><span data-ttu-id="675cf-163">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="675cf-163">Windows Server 2012</span></span> | <span data-ttu-id="675cf-164">설치됨</span><span class="sxs-lookup"><span data-stu-id="675cf-164">installed</span></span> | [<span data-ttu-id="675cf-165">WMF 4.0</span><span class="sxs-lookup"><span data-stu-id="675cf-165">WMF 4.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=40855) | [<span data-ttu-id="675cf-166">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="675cf-166">WMF 5.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [<span data-ttu-id="675cf-167">WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="675cf-167">WMF 5.1</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=54616)
<span data-ttu-id="675cf-168">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="675cf-168">Windows 7 SP1</span></span><br/><span data-ttu-id="675cf-169">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="675cf-169">Windows Server 2008 R2 SP1</span></span> | [<span data-ttu-id="675cf-170">WMF 3.0</span><span class="sxs-lookup"><span data-stu-id="675cf-170">WMF 3.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=34595) | [<span data-ttu-id="675cf-171">WMF 4.0</span><span class="sxs-lookup"><span data-stu-id="675cf-171">WMF 4.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=40855) | [<span data-ttu-id="675cf-172">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="675cf-172">WMF 5.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [<span data-ttu-id="675cf-173">WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="675cf-173">WMF 5.1</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=54616)

> [!NOTE]
>
> <span data-ttu-id="675cf-174">자동 업데이트가 사용하도록 설정된 Windows 10의 초기 릴리스에서는 PowerShell이 버전 5.0에서 5.1로 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="675cf-174">On the initial release of Windows 10, with automatic updates enabled, PowerShell gets updated from version 5.0 to 5.1.</span></span>
>
> <span data-ttu-id="675cf-175">Windows 업데이트를 통해 Windows 10의 원래 버전이 업데이트되지 않으면 PowerShell 버전은 5.0입니다.</span><span class="sxs-lookup"><span data-stu-id="675cf-175">If the original version of Windows 10 is not updated through Windows Updates, the version of PowerShell is 5.0.</span></span>

## <a name="need-azure-powershell"></a><span data-ttu-id="675cf-176">Azure PowerShell 필요</span><span class="sxs-lookup"><span data-stu-id="675cf-176">Need Azure PowerShell</span></span>

<span data-ttu-id="675cf-177">**Azure PowerShell**을 찾는 경우 [Overview of Azure PowerShell](/powershell/azure/overview)(Azure PowerShell 개요)에서 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="675cf-177">If you're looking for **Azure PowerShell**, you could start with [Overview of Azure PowerShell](/powershell/azure/overview).</span></span>

<span data-ttu-id="675cf-178">그러지 않으면 [Install and configure Azure PowerShell](/powershell/azure/install-azurerm-ps)(Azure PowerShell 설치 및 구성)이 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="675cf-178">Otherwise, what you might need is [Install and configure Azure PowerShell](/powershell/azure/install-azurerm-ps)</span></span>

## <a name="see-also"></a><span data-ttu-id="675cf-179">참고 항목</span><span class="sxs-lookup"><span data-stu-id="675cf-179">See Also</span></span>

[<span data-ttu-id="675cf-180">Windows PowerShell 시스템 요구 사항</span><span class="sxs-lookup"><span data-stu-id="675cf-180">Windows PowerShell System Requirements</span></span>](Windows-PowerShell-System-Requirements.md)

[<span data-ttu-id="675cf-181">Windows PowerShell 시작</span><span class="sxs-lookup"><span data-stu-id="675cf-181">Starting Windows PowerShell</span></span>](../getting-started/Starting-Windows-PowerShell.md)
