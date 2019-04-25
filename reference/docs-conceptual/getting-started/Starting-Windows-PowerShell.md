---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Windows PowerShell 시작
ms.assetid: 59b649a2-c90c-4cf4-bf95-a740c59148e7
ms.openlocfilehash: 9184e8b0e508610e7f4775f1032f3a69c93bb8c1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058355"
---
# <a name="starting-windows-powershell"></a><span data-ttu-id="19d29-103">Windows PowerShell 시작</span><span class="sxs-lookup"><span data-stu-id="19d29-103">Starting Windows PowerShell</span></span>
<span data-ttu-id="19d29-104">PowerShell은 여러 호스트에 내장된 스크립팅 엔진 dll입니다.</span><span class="sxs-lookup"><span data-stu-id="19d29-104">PowerShell is a scripting engine dll which is embedded into multiple hosts.</span></span>  <span data-ttu-id="19d29-105">시작할 가장 일반적인 호스트는 대화형 명령줄 PowerShell.exe와 대화형 스크립팅 환경 PowerShell_ISE.exe입니다.</span><span class="sxs-lookup"><span data-stu-id="19d29-105">The most common host you will start are the interactive command line PowerShell.exe and the Interactive Scripting Environment PowerShell_ISE.exe.</span></span>

<span data-ttu-id="19d29-106">Windows Server® 2012 R2, Windows® 8.1, Windows Server 2012 및 Windows 8에서 Windows PowerShell®을 시작하려면 [일반 관리 작업 및 탐색](https://technet.microsoft.com/library/hh831491.aspx)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="19d29-106">To start Windows PowerShell® on Windows Server® 2012 R2, Windows® 8.1, Windows Server 2012, and Windows 8, see [Common Management Tasks and Navigation](https://technet.microsoft.com/library/hh831491.aspx).</span></span>

## <a name="how-to-start-windows-powershell-on-earlier-versions-of-windows"></a><span data-ttu-id="19d29-107">이전 버전의 Windows에서 Windows PowerShell을 시작하는 방법</span><span class="sxs-lookup"><span data-stu-id="19d29-107">How to Start Windows PowerShell on Earlier Versions of Windows</span></span>

<span data-ttu-id="19d29-108">이 섹션에서는 Windows® 7, Windows Server® 2008 R2 및 Windows Server® 2008에서 Windows PowerShell 및 Windows PowerShell ISE(통합 스크립팅 환경)을 시작하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="19d29-108">This section explains how to start Windows PowerShell and Windows PowerShell Integrated Scripting Environment (ISE) on Windows® 7, Windows Server® 2008 R2, and Windows Server® 2008.</span></span> <span data-ttu-id="19d29-109">또한 Windows Server® 2008 R2 및 Windows Server® 2008의 Windows PowerShell 2.0에서 Windows PowerShell ISE에 대한 선택적 기능을 사용하도록 설정하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="19d29-109">It also explains how to enable the optional feature for Windows PowerShell ISE in Windows PowerShell 2.0 on Windows Server® 2008 R2 and Windows Server® 2008.</span></span>

<span data-ttu-id="19d29-110">다음 방법 중 하나를 사용하여 Windows PowerShell 3.0 또는 Windows PowerShell 4.0의 설치된 버전을 시작합니다(해당하는 경우).</span><span class="sxs-lookup"><span data-stu-id="19d29-110">Use any of the following methods to start the installed version of Windows PowerShell 3.0, or Windows PowerShell 4.0, where applicable.</span></span>

#### <a name="from-the-start-menu"></a><span data-ttu-id="19d29-111">시작 메뉴</span><span class="sxs-lookup"><span data-stu-id="19d29-111">From the Start Menu</span></span>

- <span data-ttu-id="19d29-112">**시작**을 클릭하고 **PowerShell**을 입력한 다음 **Windows PowerShell**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="19d29-112">Click **Start**, type **PowerShell**, and then click **Windows PowerShell**.</span></span>
- <span data-ttu-id="19d29-113">**시작** 메뉴에서 **시작**, **모든 프로그램**, **보조프로그램**, **Windows PowerShell** 폴더, **Windows PowerShell**을 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="19d29-113">From the **Start** menu, click **Start**, click **All Programs**, click **Accessories**, click the **Windows PowerShell** folder, and then click **Windows PowerShell**.</span></span>

#### <a name="at-the-command-prompt"></a><span data-ttu-id="19d29-114">명령 프롬프트</span><span class="sxs-lookup"><span data-stu-id="19d29-114">At the Command Prompt</span></span>

<span data-ttu-id="19d29-115">Cmd.exe, Windows PowerShell 또는 Windows PowerShell ISE에서 Windows PowerShell을 시작하려면 다음과 같이 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="19d29-115">In Cmd.exe, Windows PowerShell, or Windows PowerShell ISE, to start Windows PowerShell, type:</span></span>

```
PowerShell
```

<span data-ttu-id="19d29-116">PowerShell.exe 프로그램의 매개 변수를 사용하여 세션을 사용자 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19d29-116">You can also use the parameters of the PowerShell.exe program to customize the session.</span></span> <span data-ttu-id="19d29-117">자세한 내용은 [PowerShell.exe 명령줄 도움말](../core-powershell/console/PowerShell.exe-Command-Line-Help.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="19d29-117">For more information, see [PowerShell.exe Command-Line Help](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).</span></span>

#### <a name="with-administrative-privileges-run-as-administrator"></a><span data-ttu-id="19d29-118">관리자 권한("관리자 권한으로 실행")</span><span class="sxs-lookup"><span data-stu-id="19d29-118">With Administrative privileges ("Run as administrator")</span></span>

<span data-ttu-id="19d29-119">**시작**을 클릭하고 **PowerShell**을 입력한 다음 **Windows PowerShell**을 마우스 오른쪽 단추로 클릭하고 **관리자 권한으로 실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="19d29-119">Click **Start**, type **PowerShell**, right-click **Windows PowerShell**, and then click **Run as administrator**.</span></span>

## <a name="how-to-start-windows-powershell-ise-on-earlier-releases-of-windows"></a><span data-ttu-id="19d29-120">이전 릴리스의 Windows에서 Windows PowerShell ISE를 시작하는 방법</span><span class="sxs-lookup"><span data-stu-id="19d29-120">How to Start Windows PowerShell ISE on Earlier Releases of Windows</span></span>

<span data-ttu-id="19d29-121">다음 방법 중 하나를 사용하여 Windows PowerShell ISE를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="19d29-121">Use any of the following methods to start Windows PowerShell ISE.</span></span>

#### <a name="from-the-start-menu"></a><span data-ttu-id="19d29-122">시작 메뉴</span><span class="sxs-lookup"><span data-stu-id="19d29-122">From the Start Menu</span></span>

- <span data-ttu-id="19d29-123">**시작**을 클릭하고 **ISE**를 입력한 다음 **Windows PowerShell ISE**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="19d29-123">Click **Start**, type **ISE**, and then click **Windows PowerShell ISE**.</span></span>
- <span data-ttu-id="19d29-124">**시작** 메뉴에서 **시작**, **모든 프로그램**, **보조프로그램**, **Windows PowerShell** 폴더, **Windows PowerShell ISE**를 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="19d29-124">From the **Start** menu, click **Start**, click **All Programs**, click **Accessories**, click the **Windows PowerShell** folder, and then click **Windows PowerShell ISE**.</span></span>

#### <a name="at-the-command-prompt"></a><span data-ttu-id="19d29-125">명령 프롬프트</span><span class="sxs-lookup"><span data-stu-id="19d29-125">At the Command Prompt</span></span>

<span data-ttu-id="19d29-126">Cmd.exe, Windows PowerShell 또는 Windows PowerShell ISE에서 Windows PowerShell을 시작하려면 다음과 같이 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="19d29-126">In Cmd.exe, Windows PowerShell, or Windows PowerShell ISE, to start Windows PowerShell, type:</span></span>

```
PowerShell_ISE
```

<span data-ttu-id="19d29-127">또는</span><span class="sxs-lookup"><span data-stu-id="19d29-127">or</span></span>

```
ISE
```

#### <a name="with-administrative-privileges-run-as-administrator"></a><span data-ttu-id="19d29-128">관리자 권한("관리자 권한으로 실행")</span><span class="sxs-lookup"><span data-stu-id="19d29-128">With Administrative privileges ("Run as administrator")</span></span>

<span data-ttu-id="19d29-129">**시작**을 클릭하고 **ISE**를 입력한 다음 **Windows PowerShell ISE**를 마우스 오른쪽 단추로 클릭하고 **관리자 권한으로 실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="19d29-129">Click **Start**, type **ISE**, right-click **Windows PowerShell ISE**, and then click **Run as administrator**.</span></span>

## <a name="how-to-enable-windows-powershell-ise-on-earlier-releases-of-windows"></a><span data-ttu-id="19d29-130">이전 릴리스의 Windows에서 Windows PowerShell ISE를 사용하도록 설정하는 방법</span><span class="sxs-lookup"><span data-stu-id="19d29-130">How to Enable Windows PowerShell ISE on Earlier Releases of Windows</span></span>

<span data-ttu-id="19d29-131">Windows PowerShell 4.0 및 Windows PowerShell 3.0의 경우 모든 버전의 Windows에서 Windows PowerShell ISE가 기본적으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="19d29-131">In Windows PowerShell 4.0 and Windows PowerShell 3.0, Windows PowerShell ISE is enabled by default on all versions of Windows.</span></span> <span data-ttu-id="19d29-132">아직 사용되지 않는 경우 Windows Management Framework 4.0 또는 Windows Management Framework 3.0에서 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="19d29-132">If it is not already enabled, Windows Management Framework 4.0 or Windows Management Framework 3.0 enables it.</span></span>

<span data-ttu-id="19d29-133">Windows PowerShell 2.0의 경우 Windows 7에서는 Windows PowerShell ISE가 기본적으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="19d29-133">In Windows PowerShell 2.0, Windows PowerShell ISE is enabled by default on Windows 7.</span></span> <span data-ttu-id="19d29-134">그러나 Windows Server 2008 R2 및 Windows Server 2008에서는 선택적 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="19d29-134">However, on Windows Server 2008 R2 and Windows Server 2008, it is an optional feature.</span></span>

<span data-ttu-id="19d29-135">Windows Server 2008 R2 또는 Windows Server 2008의 Windows PowerShell 2.0에서 Windows PowerShell ISE를 사용하도록 설정하려면 다음 절차를 따르세요.</span><span class="sxs-lookup"><span data-stu-id="19d29-135">To enable Windows PowerShell ISE in Windows PowerShell 2.0 on Windows Server 2008 R2 or Windows Server 2008, use the following procedure.</span></span>

#### <a name="to-enable-windows-powershell-integrated-scripting-environment-ise"></a><span data-ttu-id="19d29-136">Windows PowerShell ISE(통합 스크립팅 환경)를 사용하도록 설정하려면</span><span class="sxs-lookup"><span data-stu-id="19d29-136">To enable Windows PowerShell Integrated Scripting Environment (ISE)</span></span>

1. <span data-ttu-id="19d29-137">서버 관리자를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="19d29-137">Start Server Manager.</span></span>
2. <span data-ttu-id="19d29-138">**기능**을 클릭한 다음 **기능 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="19d29-138">Click **Features** and then click **Add Features**.</span></span>
3. <span data-ttu-id="19d29-139">기능 선택에서 Windows PowerShell ISE(통합 스크립팅 환경)를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="19d29-139">In Select Features, click Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

## <a name="starting-the-32-bit-version-of-windows-powershell"></a><span data-ttu-id="19d29-140">Windows PowerShell 32비트 버전 시작</span><span class="sxs-lookup"><span data-stu-id="19d29-140">Starting the 32-Bit Version of Windows PowerShell</span></span>

<span data-ttu-id="19d29-141">64비트 컴퓨터에 Windows PowerShell을 설치하면 64비트 버전뿐 아니라 Windows PowerShell 32비트 버전인 **Windows PowerShell (x86)** 도 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="19d29-141">When you install Windows PowerShell on a 64-bit computer, **Windows PowerShell (x86)**, a 32-bit version of Windows PowerShell is installed in addition to the 64-bit version.</span></span> <span data-ttu-id="19d29-142">Windows PowerShell을 실행하는 경우 기본적으로 64비트 버전이 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="19d29-142">When you run Windows PowerShell, the 64-bit version runs by default.</span></span>

<span data-ttu-id="19d29-143">그러나 32비트 버전이 필요한 모듈을 사용하거나 32비트 컴퓨터에 원격으로 연결하는 경우와 같이 **Windows PowerShell(x86)** 을 실행해야 하는 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19d29-143">However, you might occasionally need to run **Windows PowerShell (x86)**, such as when you are using a module that requires the 32-bit version or when you are connecting remotely to a 32-bit computer.</span></span>

<span data-ttu-id="19d29-144">Windows PowerShell 32비트 버전을 시작하려면 다음 절차 중 하나를 따르세요.</span><span class="sxs-lookup"><span data-stu-id="19d29-144">To start a 32-bit version of Windows PowerShell, use any of the following procedures.</span></span>

#### <a name="in-windows-server-2012-r2"></a><span data-ttu-id="19d29-145">Windows Server® 2012 R2에서</span><span class="sxs-lookup"><span data-stu-id="19d29-145">In Windows Server® 2012 R2</span></span>

- <span data-ttu-id="19d29-146">**시작** 화면에서 **Windows PowerShell(x86)** 을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="19d29-146">On the **Start** screen, type **Windows PowerShell (x86)**.</span></span> <span data-ttu-id="19d29-147">**Windows PowerShell x86** 타일을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="19d29-147">Click the **Windows PowerShell x86** tile.</span></span>
- <span data-ttu-id="19d29-148">**서버 관리자**의 **도구** 메뉴에서 **Windows PowerShell(x86)** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="19d29-148">In **Server Manager**, from the **Tools** menu, select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="19d29-149">바탕 화면에서 커서를 오른쪽 위 모서리로 이동하고 **검색**을 클릭한 다음 **PowerShell x86**을 입력하고 **Windows PowerShell(x86)** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="19d29-149">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell x86** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="19d29-150">명령줄을 통해 다음을 입력합니다.`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="19d29-150">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-server-2012"></a><span data-ttu-id="19d29-151">Windows Server® 2012에서</span><span class="sxs-lookup"><span data-stu-id="19d29-151">In Windows Server® 2012</span></span>

- <span data-ttu-id="19d29-152">**시작** 화면에서 **PowerShell**을 입력하고 **Windows PowerShell(x86)** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="19d29-152">On the **Start** screen, type **PowerShell** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="19d29-153">**서버 관리자**의 **도구** 메뉴에서 **Windows PowerShell(x86)** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="19d29-153">In **Server Manager**, from the **Tools** menu, select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="19d29-154">바탕 화면에서 커서를 오른쪽 위 모서리로 이동하고 **검색**을 클릭한 다음 **PowerShell**을 입력하고 **Windows PowerShell(x86)** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="19d29-154">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="19d29-155">명령줄을 통해 다음을 입력합니다.`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="19d29-155">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-81"></a><span data-ttu-id="19d29-156">Windows® 8.1에서</span><span class="sxs-lookup"><span data-stu-id="19d29-156">In Windows® 8.1</span></span>

- <span data-ttu-id="19d29-157">**시작** 화면에서 **Windows PowerShell(x86)** 을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="19d29-157">On the **Start** screen, type **Windows PowerShell (x86)**.</span></span> <span data-ttu-id="19d29-158">**Windows PowerShell x86** 타일을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="19d29-158">Click the **Windows PowerShell x86** tile.</span></span>
- <span data-ttu-id="19d29-159">Windows 8.1용 [원격 서버 관리 도구](https://go.microsoft.com/fwlink/?LinkID=304145)를 실행하는 경우 **서버 관리자 도구** 메뉴에서 Windows PowerShell x86을 열 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19d29-159">If you are running [Remote Server Administration Tools](https://go.microsoft.com/fwlink/?LinkID=304145) for Windows 8.1, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span>
  <span data-ttu-id="19d29-160">**Windows PowerShell(x86)** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="19d29-160">Select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="19d29-161">바탕 화면에서 커서를 오른쪽 위 모서리로 이동하고 **검색**을 클릭한 다음 **PowerShell x86**을 입력하고 **Windows PowerShell(x86)** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="19d29-161">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell x86** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="19d29-162">명령줄을 통해 다음을 입력합니다.`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="19d29-162">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-8"></a><span data-ttu-id="19d29-163">Windows® 8에서</span><span class="sxs-lookup"><span data-stu-id="19d29-163">In Windows® 8</span></span>

- <span data-ttu-id="19d29-164">**시작** 화면에서 커서를 오른쪽 위 모서리로 이동하고 **설정**, **타일**을 차례로 클릭한 다음 **관리 도구 표시** 슬라이더를 예로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="19d29-164">On the **Start** screen, move the cursor to the upper right corner, click **Settings**, click **Tiles**, and then move the **Show Administrative Tools** slider to Yes.</span></span> <span data-ttu-id="19d29-165">**PowerShell**을 입력하고 **Windows PowerShell(x86)** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="19d29-165">Then, type **PowerShell** and click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="19d29-166">Windows 8용 [원격 서버 관리 도구](https://www.microsoft.com/download/details.aspx?id=28972)를 실행하는 경우 **서버 관리자 도구** 메뉴에서 Windows PowerShell x86을 열 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19d29-166">If you are running [Remote Server Administration Tools](https://www.microsoft.com/download/details.aspx?id=28972) for Windows 8, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span> <span data-ttu-id="19d29-167">**Windows PowerShell(x86)** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="19d29-167">Select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="19d29-168">**시작** 화면이나 바탕 화면에서 **PowerShell(x86)** 을 입력하고 **Windows PowerShell(x86)** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="19d29-168">On the **Start** screen or the desktop, type **PowerShell (x86)** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="19d29-169">명령줄을 통해 다음을 입력합니다.`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="19d29-169">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>