---
ms.date: 12/05/2019
keywords: powershell,cmdlet
title: Windows PowerShell 시작
ms.openlocfilehash: 32ed85510899ea239c9dc332a023554ce9b53e47
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/23/2020
ms.locfileid: "83809019"
---
# <a name="starting-windows-powershell"></a><span data-ttu-id="3bd54-103">Windows PowerShell 시작</span><span class="sxs-lookup"><span data-stu-id="3bd54-103">Starting Windows PowerShell</span></span>

<span data-ttu-id="3bd54-104">Windows PowerShell은 여러 호스트에 내장된 스크립팅 엔진 `.DLL`입니다.</span><span class="sxs-lookup"><span data-stu-id="3bd54-104">Windows PowerShell is a scripting engine `.DLL` that's embedded into multiple hosts.</span></span> <span data-ttu-id="3bd54-105">시작할 가장 일반적인 호스트는 대화형 명령줄 **powershell.exe**와 대화형 스크립팅 환경 **powershell_ise.exe**입니다.</span><span class="sxs-lookup"><span data-stu-id="3bd54-105">The most common hosts you'll start are the interactive command-line **powershell.exe** and the Interactive Scripting Environment **powershell_ise.exe**.</span></span>

<span data-ttu-id="3bd54-106">Windows Server® 2012 R2, Windows® 8.1, Windows Server 2012 및 Windows 8에서 Windows PowerShell®을 시작하려면 [Windows의 일반 관리 작업 및 탐색](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831491(v=ws.11))을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3bd54-106">To start Windows PowerShell® on Windows Server® 2012 R2, Windows® 8.1, Windows Server 2012, and Windows 8, see [Common Management Tasks and Navigation in Windows](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831491(v=ws.11)).</span></span>

## <a name="powershell-core-has-renamed-binary"></a><span data-ttu-id="3bd54-107">PowerShell Core의 이진 이름 변경</span><span class="sxs-lookup"><span data-stu-id="3bd54-107">PowerShell Core has renamed binary</span></span>

<span data-ttu-id="3bd54-108">PowerShell Core(PowerShell 이라고 함)는 오픈 소스이고 .NET Core를 사용하는 버전 6 이상입니다.</span><span class="sxs-lookup"><span data-stu-id="3bd54-108">PowerShell Core, referred to as PowerShell, is version 6 and higher that's open source and uses .NET Core.</span></span> <span data-ttu-id="3bd54-109">지원되는 버전은 Windows, macOS 및 Linux에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3bd54-109">Supported versions are available on Windows, macOS, and Linux.</span></span>

<span data-ttu-id="3bd54-110">PowerShell 6부터 PowerShell 이진의 이름이 Windows의 경우 **pwsh.exe**, macOS 및 Linux의 경우 **pwsh**로 변경되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3bd54-110">Beginning in PowerShell 6, the PowerShell binary was renamed **pwsh.exe** for Windows and **pwsh** for macOS and Linux.</span></span> <span data-ttu-id="3bd54-111">**pwsh-preview**를 사용하여 PowerShell 미리 보기 버전을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3bd54-111">You can start PowerShell preview versions using **pwsh-preview**.</span></span> <span data-ttu-id="3bd54-112">자세한 내용은 [PowerShell Core 6.0의 새로운 기능](/powershell/scripting/whats-new/what-s-new-in-powershell-core-60#renamed-powershellexe-to-pwshexe) 및 [pwsh 정보](/powershell/module/microsoft.powershell.core/about/about_pwsh?view=powershell-7)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3bd54-112">For more information, see [What's New in PowerShell Core 6.0](/powershell/scripting/whats-new/what-s-new-in-powershell-core-60#renamed-powershellexe-to-pwshexe) and [About pwsh](/powershell/module/microsoft.powershell.core/about/about_pwsh?view=powershell-7).</span></span>

<span data-ttu-id="3bd54-113">PowerShell 7에 대한 cmdlet 참조 및 설치 설명서를 찾으려면 다음 링크를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3bd54-113">To find cmdlet reference and installation documentation for PowerShell 7, use the following links:</span></span>

| <span data-ttu-id="3bd54-114">문서</span><span class="sxs-lookup"><span data-stu-id="3bd54-114">Document</span></span> | <span data-ttu-id="3bd54-115">링크</span><span class="sxs-lookup"><span data-stu-id="3bd54-115">Link</span></span> |
| ----- | ----- |
| <span data-ttu-id="3bd54-116">Cmdlet 참조</span><span class="sxs-lookup"><span data-stu-id="3bd54-116">Cmdlet reference</span></span> | [<span data-ttu-id="3bd54-117">PowerShell 모듈 브라우저</span><span class="sxs-lookup"><span data-stu-id="3bd54-117">PowerShell Module Browser</span></span>](/powershell/module/?view=powershell-7) |
| <span data-ttu-id="3bd54-118">Windows 설치</span><span class="sxs-lookup"><span data-stu-id="3bd54-118">Windows installation</span></span> | [<span data-ttu-id="3bd54-119">Windows에서 PowerShell Core 설치</span><span class="sxs-lookup"><span data-stu-id="3bd54-119">Installing PowerShell Core on Windows</span></span>](/powershell/scripting/install/installing-powershell-core-on-windows?view=powershell-7) |
| <span data-ttu-id="3bd54-120">macOS 설치</span><span class="sxs-lookup"><span data-stu-id="3bd54-120">macOS installation</span></span> | [<span data-ttu-id="3bd54-121">macOS에서 PowerShell Core 설치</span><span class="sxs-lookup"><span data-stu-id="3bd54-121">Installing PowerShell Core on macOS</span></span>](/powershell/scripting/install/installing-powershell-core-on-macos?view=powershell-7) |
| <span data-ttu-id="3bd54-122">Linux 설치</span><span class="sxs-lookup"><span data-stu-id="3bd54-122">Linux installation</span></span> | [<span data-ttu-id="3bd54-123">Linux에서 PowerShell Core 설치</span><span class="sxs-lookup"><span data-stu-id="3bd54-123">Installing PowerShell Core on Linux</span></span>](/powershell/scripting/install/installing-powershell-core-on-linux?view=powershell-7) |

<span data-ttu-id="3bd54-124">다른 PowerShell 버전에 대한 콘텐츠를 보려면 [PowerShell을 사용하는 방법 설명서](../how-to-use-docs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3bd54-124">To view content for other PowerShell versions, see [How to use the PowerShell documentation](../how-to-use-docs.md).</span></span>

## <a name="how-to-start-windows-powershell-on-earlier-versions-of-windows"></a><span data-ttu-id="3bd54-125">이전 버전의 Windows에서 Windows PowerShell을 시작하는 방법</span><span class="sxs-lookup"><span data-stu-id="3bd54-125">How to Start Windows PowerShell on Earlier Versions of Windows</span></span>

<span data-ttu-id="3bd54-126">이 섹션에서는 Windows® 7, Windows Server® 2008 R2 및 Windows Server® 2008에서 Windows PowerShell 및 Windows PowerShell ISE(통합 스크립팅 환경)을 시작하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3bd54-126">This section explains how to start Windows PowerShell and Windows PowerShell Integrated Scripting Environment (ISE) on Windows® 7, Windows Server® 2008 R2, and Windows Server® 2008.</span></span> <span data-ttu-id="3bd54-127">또한 Windows Server® 2008 R2 및 Windows Server® 2008의 Windows PowerShell 2.0에서 Windows PowerShell ISE에 대한 선택적 기능을 사용하도록 설정하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3bd54-127">It also explains how to enable the optional feature for Windows PowerShell ISE in Windows PowerShell 2.0 on Windows Server® 2008 R2 and Windows Server® 2008.</span></span>

<span data-ttu-id="3bd54-128">다음 방법 중 하나를 사용하여 Windows PowerShell 3.0 또는 Windows PowerShell 4.0의 설치된 버전을 시작합니다(해당하는 경우).</span><span class="sxs-lookup"><span data-stu-id="3bd54-128">Use any of the following methods to start the installed version of Windows PowerShell 3.0, or Windows PowerShell 4.0, where applicable.</span></span>

#### <a name="from-the-start-menu"></a><span data-ttu-id="3bd54-129">시작 메뉴</span><span class="sxs-lookup"><span data-stu-id="3bd54-129">From the Start Menu</span></span>

- <span data-ttu-id="3bd54-130">**시작**을 클릭하고 **PowerShell**을 입력한 다음 **Windows PowerShell**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3bd54-130">Click **Start**, type **PowerShell**, and then click **Windows PowerShell**.</span></span>
- <span data-ttu-id="3bd54-131">**시작** 메뉴에서 **시작**, **모든 프로그램**, **보조프로그램**, **Windows PowerShell** 폴더, **Windows PowerShell**을 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3bd54-131">From the **Start** menu, click **Start**, click **All Programs**, click **Accessories**, click the **Windows PowerShell** folder, and then click **Windows PowerShell**.</span></span>

#### <a name="at-the-command-prompt"></a><span data-ttu-id="3bd54-132">명령 프롬프트</span><span class="sxs-lookup"><span data-stu-id="3bd54-132">At the Command Prompt</span></span>

<span data-ttu-id="3bd54-133">**cmd.exe**, Windows PowerShell 또는 Windows PowerShell ISE에서 Windows PowerShell을 시작하려면 다음과 같이 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3bd54-133">In **cmd.exe**, Windows PowerShell, or Windows PowerShell ISE, to start Windows PowerShell, type:</span></span>

```
PowerShell
```

<span data-ttu-id="3bd54-134">**powershell.exe** 프로그램의 매개 변수를 사용하여 세션을 사용자 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3bd54-134">You can also use the parameters of the **powershell.exe** program to customize the session.</span></span> <span data-ttu-id="3bd54-135">자세한 내용은 [PowerShell.exe 명령줄 도움말](/powershell/module/Microsoft.PowerShell.Core/About/about_PowerShell_exe)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3bd54-135">For more information, see [PowerShell.exe Command-Line Help](/powershell/module/Microsoft.PowerShell.Core/About/about_PowerShell_exe).</span></span>

#### <a name="with-administrative-privileges-run-as-administrator"></a><span data-ttu-id="3bd54-136">관리자 권한(관리자 권한으로 실행)</span><span class="sxs-lookup"><span data-stu-id="3bd54-136">With Administrative privileges (Run as administrator)</span></span>

<span data-ttu-id="3bd54-137">**시작**을 클릭하고 **PowerShell**을 입력한 다음 **Windows PowerShell**을 마우스 오른쪽 단추로 클릭하고 **관리자 권한으로 실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3bd54-137">Click **Start**, type **PowerShell**, right-click **Windows PowerShell**, and then click **Run as administrator**.</span></span>

## <a name="how-to-start-windows-powershell-ise-on-earlier-releases-of-windows"></a><span data-ttu-id="3bd54-138">이전 릴리스의 Windows에서 Windows PowerShell ISE를 시작하는 방법</span><span class="sxs-lookup"><span data-stu-id="3bd54-138">How to Start Windows PowerShell ISE on Earlier Releases of Windows</span></span>

<span data-ttu-id="3bd54-139">다음 방법 중 하나를 사용하여 Windows PowerShell ISE를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="3bd54-139">Use any of the following methods to start Windows PowerShell ISE.</span></span>

#### <a name="from-the-start-menu"></a><span data-ttu-id="3bd54-140">시작 메뉴</span><span class="sxs-lookup"><span data-stu-id="3bd54-140">From the Start Menu</span></span>

- <span data-ttu-id="3bd54-141">**시작**을 클릭하고 **ISE**를 입력한 다음 **Windows PowerShell ISE**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3bd54-141">Click **Start**, type **ISE**, and then click **Windows PowerShell ISE**.</span></span>
- <span data-ttu-id="3bd54-142">**시작** 메뉴에서 **시작**, **모든 프로그램**, **보조프로그램**, **Windows PowerShell** 폴더, **Windows PowerShell ISE**를 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3bd54-142">From the **Start** menu, click **Start**, click **All Programs**, click **Accessories**, click the **Windows PowerShell** folder, and then click **Windows PowerShell ISE**.</span></span>

#### <a name="at-the-command-prompt"></a><span data-ttu-id="3bd54-143">명령 프롬프트</span><span class="sxs-lookup"><span data-stu-id="3bd54-143">At the Command Prompt</span></span>

<span data-ttu-id="3bd54-144">**cmd.exe**, Windows PowerShell 또는 Windows PowerShell ISE에서 Windows PowerShell을 시작하려면 다음과 같이 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3bd54-144">In **cmd.exe**, Windows PowerShell, or Windows PowerShell ISE, to start Windows PowerShell, type:</span></span>

```
PowerShell_ISE
```

<span data-ttu-id="3bd54-145">또는</span><span class="sxs-lookup"><span data-stu-id="3bd54-145">or</span></span>

```
ISE
```

#### <a name="with-administrative-privileges-run-as-administrator"></a><span data-ttu-id="3bd54-146">관리자 권한(관리자 권한으로 실행)</span><span class="sxs-lookup"><span data-stu-id="3bd54-146">With Administrative privileges (Run as administrator)</span></span>

<span data-ttu-id="3bd54-147">**시작**을 클릭하고 **ISE**를 입력한 다음 **Windows PowerShell ISE**를 마우스 오른쪽 단추로 클릭하고 **관리자 권한으로 실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3bd54-147">Click **Start**, type **ISE**, right-click **Windows PowerShell ISE**, and then click **Run as administrator**.</span></span>

## <a name="how-to-enable-windows-powershell-ise-on-earlier-releases-of-windows"></a><span data-ttu-id="3bd54-148">이전 릴리스의 Windows에서 Windows PowerShell ISE를 사용하도록 설정하는 방법</span><span class="sxs-lookup"><span data-stu-id="3bd54-148">How to Enable Windows PowerShell ISE on Earlier Releases of Windows</span></span>

<span data-ttu-id="3bd54-149">Windows PowerShell 4.0 및 Windows PowerShell 3.0의 경우 모든 버전의 Windows에서 Windows PowerShell ISE가 기본적으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3bd54-149">In Windows PowerShell 4.0 and Windows PowerShell 3.0, Windows PowerShell ISE is enabled by default on all versions of Windows.</span></span> <span data-ttu-id="3bd54-150">아직 사용되지 않는 경우 Windows Management Framework 4.0 또는 Windows Management Framework 3.0에서 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3bd54-150">If it isn't already enabled, Windows Management Framework 4.0 or Windows Management Framework 3.0 enables it.</span></span>

<span data-ttu-id="3bd54-151">Windows PowerShell 2.0의 경우 Windows 7에서는 Windows PowerShell ISE가 기본적으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3bd54-151">In Windows PowerShell 2.0, Windows PowerShell ISE is enabled by default on Windows 7.</span></span> <span data-ttu-id="3bd54-152">그러나 Windows Server 2008 R2 및 Windows Server 2008에서는 선택적 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="3bd54-152">However, on Windows Server 2008 R2 and Windows Server 2008, it's an optional feature.</span></span>

<span data-ttu-id="3bd54-153">Windows Server 2008 R2 또는 Windows Server 2008의 Windows PowerShell 2.0에서 Windows PowerShell ISE를 사용하도록 설정하려면 다음 절차를 따르세요.</span><span class="sxs-lookup"><span data-stu-id="3bd54-153">To enable Windows PowerShell ISE in Windows PowerShell 2.0 on Windows Server 2008 R2 or Windows Server 2008, use the following procedure.</span></span>

#### <a name="to-enable-windows-powershell-integrated-scripting-environment-ise"></a><span data-ttu-id="3bd54-154">Windows PowerShell ISE(통합 스크립팅 환경)를 사용하도록 설정하려면</span><span class="sxs-lookup"><span data-stu-id="3bd54-154">To enable Windows PowerShell Integrated Scripting Environment (ISE)</span></span>

1. <span data-ttu-id="3bd54-155">서버 관리자를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="3bd54-155">Start Server Manager.</span></span>
2. <span data-ttu-id="3bd54-156">**기능**을 클릭한 다음 **기능 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3bd54-156">Click **Features** and then click **Add Features**.</span></span>
3. <span data-ttu-id="3bd54-157">기능 선택에서 Windows PowerShell ISE(통합 스크립팅 환경)를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3bd54-157">In Select Features, click Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

## <a name="starting-the-32-bit-version-of-windows-powershell"></a><span data-ttu-id="3bd54-158">Windows PowerShell 32비트 버전 시작</span><span class="sxs-lookup"><span data-stu-id="3bd54-158">Starting the 32-Bit Version of Windows PowerShell</span></span>

<span data-ttu-id="3bd54-159">64비트 컴퓨터에 Windows PowerShell을 설치하면 64비트 버전뿐 아니라 Windows PowerShell 32비트 버전인 **Windows PowerShell (x86)** 도 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="3bd54-159">When you install Windows PowerShell on a 64-bit computer, **Windows PowerShell (x86)**, a 32-bit version of Windows PowerShell is installed in addition to the 64-bit version.</span></span> <span data-ttu-id="3bd54-160">Windows PowerShell을 실행하는 경우 기본적으로 64비트 버전이 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="3bd54-160">When you run Windows PowerShell, the 64-bit version runs by default.</span></span>

<span data-ttu-id="3bd54-161">그러나 32비트 버전이 필요한 모듈을 사용하거나 32비트 컴퓨터에 원격으로 연결하는 경우와 같이 **Windows PowerShell(x86)** 을 실행해야 하는 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3bd54-161">However, you might occasionally need to run **Windows PowerShell (x86)**, such as when you're using a module that requires the 32-bit version or when you're connecting remotely to a 32-bit computer.</span></span>

<span data-ttu-id="3bd54-162">Windows PowerShell 32비트 버전을 시작하려면 다음 절차 중 하나를 따르세요.</span><span class="sxs-lookup"><span data-stu-id="3bd54-162">To start a 32-bit version of Windows PowerShell, use any of the following procedures.</span></span>

#### <a name="in-windows-server-2012-r2"></a><span data-ttu-id="3bd54-163">Windows Server® 2012 R2에서</span><span class="sxs-lookup"><span data-stu-id="3bd54-163">In Windows Server® 2012 R2</span></span>

- <span data-ttu-id="3bd54-164">**시작** 화면에서 **Windows PowerShell(x86)** 을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3bd54-164">On the **Start** screen, type **Windows PowerShell (x86)**.</span></span> <span data-ttu-id="3bd54-165">**Windows PowerShell x86** 타일을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3bd54-165">Click the **Windows PowerShell x86** tile.</span></span>
- <span data-ttu-id="3bd54-166">**서버 관리자**의 **도구** 메뉴에서 **Windows PowerShell(x86)** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3bd54-166">In **Server Manager**, from the **Tools** menu, select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="3bd54-167">바탕 화면에서 커서를 오른쪽 위 모서리로 이동하고 **검색**을 클릭한 다음 **PowerShell x86**을 입력하고 **Windows PowerShell(x86)** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3bd54-167">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell x86** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="3bd54-168">명령줄을 통해 다음을 입력합니다.`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="3bd54-168">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-server-2012"></a><span data-ttu-id="3bd54-169">Windows Server® 2012에서</span><span class="sxs-lookup"><span data-stu-id="3bd54-169">In Windows Server® 2012</span></span>

- <span data-ttu-id="3bd54-170">**시작** 화면에서 **PowerShell**을 입력하고 **Windows PowerShell(x86)** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3bd54-170">On the **Start** screen, type **PowerShell** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="3bd54-171">**서버 관리자**의 **도구** 메뉴에서 **Windows PowerShell(x86)** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3bd54-171">In **Server Manager**, from the **Tools** menu, select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="3bd54-172">바탕 화면에서 커서를 오른쪽 위 모서리로 이동하고 **검색**을 클릭한 다음 **PowerShell**을 입력하고 **Windows PowerShell(x86)** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3bd54-172">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="3bd54-173">명령줄을 통해 다음을 입력합니다.`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="3bd54-173">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-81"></a><span data-ttu-id="3bd54-174">Windows® 8.1에서</span><span class="sxs-lookup"><span data-stu-id="3bd54-174">In Windows® 8.1</span></span>

- <span data-ttu-id="3bd54-175">**시작** 화면에서 **Windows PowerShell(x86)** 을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3bd54-175">On the **Start** screen, type **Windows PowerShell (x86)**.</span></span> <span data-ttu-id="3bd54-176">**Windows PowerShell x86** 타일을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3bd54-176">Click the **Windows PowerShell x86** tile.</span></span>
- <span data-ttu-id="3bd54-177">Windows 8.1용 [원격 서버 관리 도구](https://go.microsoft.com/fwlink/?LinkID=304145)를 실행하는 경우 **서버 관리자 도구** 메뉴에서 Windows PowerShell x86을 열 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3bd54-177">If you're running [Remote Server Administration Tools](https://go.microsoft.com/fwlink/?LinkID=304145) for Windows 8.1, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span> <span data-ttu-id="3bd54-178">**Windows PowerShell(x86)** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3bd54-178">Select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="3bd54-179">바탕 화면에서 커서를 오른쪽 위 모서리로 이동하고 **검색**을 클릭한 다음 **PowerShell x86**을 입력하고 **Windows PowerShell(x86)** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3bd54-179">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell x86** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="3bd54-180">명령줄을 통해 다음을 입력합니다.`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="3bd54-180">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-8"></a><span data-ttu-id="3bd54-181">Windows® 8에서</span><span class="sxs-lookup"><span data-stu-id="3bd54-181">In Windows® 8</span></span>

- <span data-ttu-id="3bd54-182">**시작** 화면에서 커서를 오른쪽 위 모서리로 이동하고 **설정**, **타일**을 차례로 클릭한 다음 **관리 도구 표시** 슬라이더를 **예**로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="3bd54-182">On the **Start** screen, move the cursor to the upper right corner, click **Settings**, click **Tiles**, and then move the **Show Administrative Tools** slider to **Yes**.</span></span> <span data-ttu-id="3bd54-183">**PowerShell**을 입력하고 **Windows PowerShell(x86)** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3bd54-183">Then, type **PowerShell** and click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="3bd54-184">Windows 8용 [원격 서버 관리 도구](https://www.microsoft.com/download/details.aspx?id=28972)를 실행하는 경우 **서버 관리자 도구** 메뉴에서 Windows PowerShell x86을 열 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3bd54-184">If you're running [Remote Server Administration Tools](https://www.microsoft.com/download/details.aspx?id=28972) for Windows 8, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span> <span data-ttu-id="3bd54-185">**Windows PowerShell(x86)** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3bd54-185">Select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="3bd54-186">**시작** 화면이나 바탕 화면에서 **PowerShell(x86)** 을 입력하고 **Windows PowerShell(x86)** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3bd54-186">On the **Start** screen or the desktop, type **PowerShell (x86)** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="3bd54-187">명령줄을 통해 다음을 입력합니다.`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="3bd54-187">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>