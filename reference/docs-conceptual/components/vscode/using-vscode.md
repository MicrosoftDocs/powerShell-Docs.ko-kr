---
title: PowerShell 개발에 Visual Studio 코드 사용
description: PowerShell 개발에 Visual Studio 코드 사용
ms.date: 11/07/2019
ms.openlocfilehash: 8644aa7c648d649651ca679238e0b79ff35ac579
ms.sourcegitcommit: 30ccbbb32915b551c4cd4c91ef1df96b5b7514c4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/01/2020
ms.locfileid: "80500907"
---
# <a name="using-visual-studio-code-for-powershell-development"></a><span data-ttu-id="8ef91-103">PowerShell 개발에 Visual Studio 코드 사용</span><span class="sxs-lookup"><span data-stu-id="8ef91-103">Using Visual Studio Code for PowerShell Development</span></span>

<span data-ttu-id="8ef91-104">[Visual Studio Code](https://code.visualstudio.com/)는 Microsoft의 플랫폼 간(Windows, macOS 및 Linux) 스크립트 편집기입니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-104">[Visual Studio Code](https://code.visualstudio.com/) is a cross-platform (Windows, macOS, and Linux) script editor by Microsoft.</span></span> <span data-ttu-id="8ef91-105">[PowerShell 확장](https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell)과 함께 풍부한 대화형 스크립트 편집 환경을 제공하므로 안정적인 PowerShell 스크립트를 더 쉽게 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-105">Together with the [the PowerShell extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell), it provides a rich and interactive script editing experience, making it easier to write reliable PowerShell scripts.</span></span>

<span data-ttu-id="8ef91-106">PowerShell 확장이 있는 Visual Studio Code는 PowerShell 스크립트 작성을 위한 권장 편집기입니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-106">Visual Studio Code with the PowerShell extension is the recommended editor for writing PowerShell scripts.</span></span>
<span data-ttu-id="8ef91-107">지원하는 PowerShell 버전은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-107">It supports the following PowerShell versions:</span></span>

- <span data-ttu-id="8ef91-108">PowerShell 7 이상</span><span class="sxs-lookup"><span data-stu-id="8ef91-108">PowerShell 7 and up</span></span>
- <span data-ttu-id="8ef91-109">PowerShell Core 6</span><span class="sxs-lookup"><span data-stu-id="8ef91-109">PowerShell Core 6</span></span>
- <span data-ttu-id="8ef91-110">Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="8ef91-110">Windows PowerShell 5.1</span></span>

<span data-ttu-id="8ef91-111">시작하기 전에 시스템에 PowerShell이 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-111">Before you begin, make sure PowerShell exists on your system.</span></span> <span data-ttu-id="8ef91-112">Windows, macOS 및 Linux에서 최신 작업을 수행하려면 다음 링크를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8ef91-112">For modern workloads on Windows, macOS, and Linux, see the following links:</span></span>

- <span data-ttu-id="8ef91-113">[Linux에 PowerShell 설치][install-pscore-linux]</span><span class="sxs-lookup"><span data-stu-id="8ef91-113">[Installing PowerShell on Linux][install-pscore-linux]</span></span>
- <span data-ttu-id="8ef91-114">[macOS에 PowerShell 설치][install-pscore-macos]</span><span class="sxs-lookup"><span data-stu-id="8ef91-114">[Installing PowerShell on macOS][install-pscore-macos]</span></span>
- <span data-ttu-id="8ef91-115">[Windows에 PowerShell 설치][install-pscore-windows]</span><span class="sxs-lookup"><span data-stu-id="8ef91-115">[Installing PowerShell on Windows][install-pscore-windows]</span></span>

<span data-ttu-id="8ef91-116">기존 Windows PowerShell 워크로드의 경우 [Windows PowerShell 설치][install-winps]를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8ef91-116">For traditional Windows PowerShell workloads, see [Installing Windows PowerShell][install-winps].</span></span>

> [!NOTE]
> <span data-ttu-id="8ef91-117">Visual Studio Code는 [Visual Studio](https://visualstudio.microsoft.com/)와는 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-117">Visual Studio Code is not the same as [Visual Studio](https://visualstudio.microsoft.com/).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8ef91-118">[Windows PowerShell ISE][ise]도 여전히 Windows에서 사용할 수 있지만 더 이상 활성 기능 개발에 포함되지 않으며 PowerShell 7 이상 또는 PowerShell Core 6에서 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-118">The [Windows PowerShell ISE][ise] is also still available for Windows, however, it is no longer in active feature development and does not work with PowerShell 7 and up or PowerShell Core 6.</span></span>
> <span data-ttu-id="8ef91-119">Windows의 배송 구성 요소로서 보안 및 우선 순위가 높은 서비스 수정 사항을 위해 공식적으로 계속 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-119">As a shipping component of Windows, it continues to be officially supported for security and high-priority servicing fixes.</span></span> <span data-ttu-id="8ef91-120">현재 Windows에서 ISE를 제거할 계획은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-120">We currently have no plans to remove the ISE from Windows.</span></span>

## <a name="editing-with-visual-studio-code"></a><span data-ttu-id="8ef91-121">Visual Studio Code로 편집</span><span class="sxs-lookup"><span data-stu-id="8ef91-121">Editing with Visual Studio Code</span></span>

1. <span data-ttu-id="8ef91-122">Visual Studio Code를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-122">Install Visual Studio Code.</span></span> <span data-ttu-id="8ef91-123">자세한 내용은 [Visual Studio Code 설치](https://code.visualstudio.com/Docs/setup/setup-overview) 개요를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8ef91-123">For more information, see the overview [Setting up Visual Studio Code](https://code.visualstudio.com/Docs/setup/setup-overview).</span></span>

    <span data-ttu-id="8ef91-124">각 플랫폼에 대한 설치 지침은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-124">There are installation instructions for each platform:</span></span>

    - <span data-ttu-id="8ef91-125">**Windows**: [Windows에서 Visual Studio Code 실행](https://code.visualstudio.com/docs/setup/windows) 페이지의 설치 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-125">**Windows**: follow the installation instructions on the [Running Visual Studio Code on Windows](https://code.visualstudio.com/docs/setup/windows) page.</span></span>
    - <span data-ttu-id="8ef91-126">**macOS**: [macOS에서 Visual Studio Code 실행](https://code.visualstudio.com/docs/setup/mac) 페이지의 설치 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-126">**macOS**: follow the installation instructions on the [Running Visual Studio Code on macOS](https://code.visualstudio.com/docs/setup/mac) page.</span></span>
    - <span data-ttu-id="8ef91-127">**Linux**: [Linux에서 Visual Studio Code 실행](https://code.visualstudio.com/docs/setup/linux) 페이지의 설치 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-127">**Linux**: follow the installation instructions on the [Running Visual Studio Code on Linux](https://code.visualstudio.com/docs/setup/linux) page.</span></span>

1. <span data-ttu-id="8ef91-128">PowerShell 확장을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-128">Install the PowerShell Extension.</span></span>

   1. <span data-ttu-id="8ef91-129">콘솔 또는 `code-insiders`(Visual Studio Code Insiders를 설치한 경우)에 `code`를 입력하여 Visual Studio Code 앱을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-129">Launch the Visual Studio Code app by typing `code` in a console or `code-insiders` if you installed Visual Studio Code Insiders.</span></span>
   1. <span data-ttu-id="8ef91-130"><kbd>Ctrl</kbd>+<kbd>P</kbd>를 눌러 Windows 또는 Linux에서 **Quick Open**을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-130">Launch **Quick Open** on Windows or Linux by pressing <kbd>Ctrl</kbd>+<kbd>P</kbd>.</span></span> <span data-ttu-id="8ef91-131">macOS에서 <kbd>Cmd</kbd>+<kbd>P</kbd>를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-131">On macOS, press <kbd>Cmd</kbd>+<kbd>P</kbd>.</span></span>
   1. <span data-ttu-id="8ef91-132">Quick Open에서 `ext install powershell`을 입력하고**Enter** 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-132">In Quick Open, type `ext install powershell` and press **Enter**.</span></span>
   1. <span data-ttu-id="8ef91-133">사이드바에 **확장** 보기가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-133">The **Extensions** view opens on the Side Bar.</span></span> <span data-ttu-id="8ef91-134">Microsoft의 PowerShell 확장을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-134">Select the PowerShell extension from Microsoft.</span></span>
      <span data-ttu-id="8ef91-135">다음 이미지와 비슷한 Visual Studio Code 화면이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-135">You should see a Visual Studio Code screen similar to the following image:</span></span>

      ![Visual Studio Code](media/using-vscode/vscode.png)

   1. <span data-ttu-id="8ef91-137">Microsoft의 PowerShell 확장에서 **설치** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-137">Click the **Install** button on the PowerShell extension from Microsoft.</span></span>
   1. <span data-ttu-id="8ef91-138">설치 후 **설치** 단추가 **다시 로드**로 바뀌면 **다시 로드**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-138">After the install, if you see the **Install** button turn into **Reload**, Click on **Reload**.</span></span>
   1. <span data-ttu-id="8ef91-139">Visual Studio Code가 다시 로드되면 편집할 준비가 된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-139">After Visual Studio Code has reloaded, you're ready for editing.</span></span>

<span data-ttu-id="8ef91-140">예를 들어 새 파일을 만들려면 **파일 > 새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-140">For example, to create a new file, click **File > New**.</span></span> <span data-ttu-id="8ef91-141">저장하려면 **파일 > 저장**을 클릭한 후 파일 이름을 제공합니다(예: `HelloWorld.ps1`).</span><span class="sxs-lookup"><span data-stu-id="8ef91-141">To save it, click **File > Save** and then provide a file name, such as `HelloWorld.ps1`.</span></span> <span data-ttu-id="8ef91-142">파일을 닫으려면 파일 이름 옆에 있는 `X`를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-142">To close the file, click the `X` next to the file name.</span></span> <span data-ttu-id="8ef91-143">Visual Studio Code를 종료하려면 **파일 > 종료**를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-143">To exit Visual Studio Code, **File > Exit**.</span></span>

### <a name="installing-the-powershell-extension-on-restricted-systems"></a><span data-ttu-id="8ef91-144">제한된 시스템에 PowerShell 확장 설치</span><span class="sxs-lookup"><span data-stu-id="8ef91-144">Installing the PowerShell Extension on Restricted Systems</span></span>

<span data-ttu-id="8ef91-145">일부 시스템은 모든 코드 서명을 확인하여 시스템에서 실행될 PowerShell Editor Services를 수동으로 승인해야 하는 방식으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-145">Some systems are set up in a way that requires all code signatures to be checked and requires PowerShell Editor Services to be manually approved to run on the system.</span></span> <span data-ttu-id="8ef91-146">PowerShell 확장을 설치했지만 다음과 같은 오류가 수신되는 경우 실행 정책을 변경하는 그룹 정책 업데이트가 원인일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-146">A Group Policy update that changes execution policy is a likely cause if you've installed the PowerShell extension but are receiving an error such as:</span></span>

```
Language server startup failed.
```

<span data-ttu-id="8ef91-147">PowerShell Editor Services를 수동으로 승인하여 Visual Studio Code용 PowerShell 확장을 수동으로 승인하려면 PowerShell 프롬프트를 열고 다음을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-147">To manually approve PowerShell Editor Services and the PowerShell extension for Visual Studio Code, open a PowerShell prompt and run the following command:</span></span>

```powershell
Import-Module $HOME\.vscode\extensions\ms-vscode.powershell*\modules\PowerShellEditorServices\PowerShellEditorServices.psd1
```

<span data-ttu-id="8ef91-148">**이 신뢰되지 않은 게시자가 서명한 소프트웨어를 실행하시겠습니까?** 가 포함된 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-148">You're prompted with **Do you want to run software from this untrusted publisher?**</span></span>
<span data-ttu-id="8ef91-149">`A`을 입력하여 파일을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-149">Type `A` to run the file.</span></span> <span data-ttu-id="8ef91-150">그런 다음, Visual Studio Code를 열고 PowerShell 확장이 제대로 작동하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-150">Then, open Visual Studio Code and check that the PowerShell extension is functioning properly.</span></span> <span data-ttu-id="8ef91-151">그래도 시작하는 데 문제가 있으면 [GitHub](https://github.com/PowerShell/vscode-powershell/issues)에서 알려 주세요.</span><span class="sxs-lookup"><span data-stu-id="8ef91-151">If you still have issues getting started, let us know on [GitHub](https://github.com/PowerShell/vscode-powershell/issues).</span></span>

> [!NOTE]
> <span data-ttu-id="8ef91-152">Visual Studio Code용 PowerShell 확장은 제한된 언어 모드에서의 실행을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-152">The PowerShell extension for Visual Studio Code does not support running in constrained language mode.</span></span> <span data-ttu-id="8ef91-153">자세한 내용은 [이 지원을 추적하는 GitHub 문제](https://github.com/PowerShell/vscode-powershell/issues/606)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8ef91-153">Please see the [GitHub issue tracking that support](https://github.com/PowerShell/vscode-powershell/issues/606) for more information.</span></span>

### <a name="using-an-older-version-of-the-powershell-extension-for-windows-powershell-v3-and-v4"></a><span data-ttu-id="8ef91-154">Windows PowerShell v3 및 v4를 위해 이전 버전의 PowerShell 확장 사용</span><span class="sxs-lookup"><span data-stu-id="8ef91-154">Using an older version of the PowerShell Extension for Windows PowerShell v3 and v4</span></span>

<span data-ttu-id="8ef91-155">현재 PowerShell 확장은 [v3 및 v4 지원을 중단](https://github.com/PowerShell/vscode-powershell/issues/1310)했지만 마지막으로 v3 및 v4를 지원한 확장 버전은 계속 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-155">Although the current PowerShell extension [stopped supporting v3 and v4](https://github.com/PowerShell/vscode-powershell/issues/1310), you can still use the last version of the extension that did.</span></span>

> [!NOTE]
> <span data-ttu-id="8ef91-156">이 이전 버전의 확장에 대한 추가 수정 사항은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-156">There will be no additional fixes to this older version of the extension.</span></span> <span data-ttu-id="8ef91-157">이 버전은 "있는 그대로" 제공되지만 Windows PowerShell v3 및 Windows PowerShell v4를 여전히 사용하고 있다면 이 버전을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-157">It's provided "AS IS" but is available for you if you are still using Windows PowerShell v3 and Windows PowerShell v4.</span></span>

<span data-ttu-id="8ef91-158">먼저 확장 창을 열고 `PowerShell`을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-158">First, open the Extension pane and search for `PowerShell`.</span></span> <span data-ttu-id="8ef91-159">그런 다음 기어 아이콘을 클릭하고 **다른 버전 설치...** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-159">Then click the gear and select **Install another version...**.</span></span>

![다른 버전 설치...](media/using-vscode/install-another-version.png)

<span data-ttu-id="8ef91-161">그런 다음 **`2020.1.0`** 버전을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-161">Then select the **`2020.1.0`** version.</span></span> <span data-ttu-id="8ef91-162">이 확장 버전은 마지막으로 v3 및 v4를 지원한 버전이었습니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-162">This version of the extension was the last version to support v3 and v4.</span></span>

<span data-ttu-id="8ef91-163">또한 확장 버전이 자동으로 업데이트되지 않도록 다음 설정을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-163">Also, add the following setting so that your extension version doesn't update automatically:</span></span>

```json
{
    "extensions.autoUpdate": false
}
```

<span data-ttu-id="8ef91-164">당분간은 이 버전이 작동하지만, Visual Studio Code에서 이 확장 버전을 중단하는 변경이 구현될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-164">Although this will work in the forseeable future, Visual Studio Code could implement a change that breaks this version of the extension.</span></span>
<span data-ttu-id="8ef91-165">이러한 이유로 지원이 되지 않기 때문에 다음 중 하나를 권장합니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-165">Because of this, and lack of support, we highly recommend either:</span></span>

- <span data-ttu-id="8ef91-166">PowerShell 7 다운로드 - Windows PowerShell과 함께 설치되며 PowerShell 확장에서 가장 잘 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-166">Downloading PowerShell 7 - which is a side-by-side install to Windows PowerShell and works the best with the PowerShell extension</span></span>
- <span data-ttu-id="8ef91-167">Windows PowerShell 5.1로 업그레이드</span><span class="sxs-lookup"><span data-stu-id="8ef91-167">Upgrading to Windows PowerShell 5.1</span></span>

<span data-ttu-id="8ef91-168">이 문서의 [Visual Studio Code를 사용하여 편집](#editing-with-visual-studio-code) 섹션에서 이러한 항목을 설치할 위치에 대한 링크를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-168">The [Editing with Visual Studio Code](#editing-with-visual-studio-code) section in this article links to where to install these.</span></span>

### <a name="choosing-a-version-of-powershell-to-use-with-the-extension"></a><span data-ttu-id="8ef91-169">확장과 함께 사용할 PowerShell 버전 선택</span><span class="sxs-lookup"><span data-stu-id="8ef91-169">Choosing a version of PowerShell to use with the extension</span></span>

<span data-ttu-id="8ef91-170">Windows PowerShell과 함께 PowerShell Core를 side-by-side 설치하면 PowerShell 확장과 함께 특정 버전의 PowerShell을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-170">With PowerShell Core installing side-by-side with Windows PowerShell, it's now possible to use a particular version of PowerShell with the PowerShell extension.</span></span> <span data-ttu-id="8ef91-171">다음 단계에 따라 해당 버전을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-171">Use the following steps to choose the version:</span></span>

1. <span data-ttu-id="8ef91-172">Windows 또는 Linux에서 <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>를 눌러 **명령 팔레트**를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-172">Open the **Command Palette** on Windows or Linux with <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>.</span></span> <span data-ttu-id="8ef91-173">macOS에서 <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-173">On macOS, use <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>.</span></span>
1. <span data-ttu-id="8ef91-174">**세션**을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-174">Search for **Session**.</span></span>
1. <span data-ttu-id="8ef91-175">**PowerShell: 세션 메뉴 표시**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-175">Click on **PowerShell: Show Session Menu**.</span></span>
1. <span data-ttu-id="8ef91-176">목록에서 사용하려는 PowerShell 버전을 선택합니다(예: **PowerShell Core**).</span><span class="sxs-lookup"><span data-stu-id="8ef91-176">Choose the version of PowerShell you want to use from the list, for example: **PowerShell Core**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8ef91-177">이 기능은 운영 체제별로 몇 가지 잘 알려진 경로를 확인하여 PowerShell의 설치 위치를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-177">This feature looks at a few well-known paths on different operating systems to discover install locations of PowerShell.</span></span> <span data-ttu-id="8ef91-178">일반적이지 않은 위치에 PowerShell을 설치한 경우 처음에 PowerShell이 세션 메뉴에 표시되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-178">If you installed PowerShell to a non-typical location, it might not show up initially in the Session Menu.</span></span> <span data-ttu-id="8ef91-179">아래 설명된 대로 [사용자 지정 경로를 추가](#adding-your-own-powershell-paths-to-the-session-menu)하여 세션 메뉴를 확장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-179">You can extend the session menu by [adding your own custom paths](#adding-your-own-powershell-paths-to-the-session-menu) as described below.</span></span>

>[!NOTE]
> <span data-ttu-id="8ef91-180">세션 메뉴에 액세스하는 또 다른 방법이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-180">There's another way to get to the session menu.</span></span> <span data-ttu-id="8ef91-181">PowerShell 파일이 편집기에서 열리면 오른쪽 아래에 녹색 버전 번호가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-181">When a PowerShell file is open in your editor, you see a green version number in the bottom right.</span></span> <span data-ttu-id="8ef91-182">이 버전 번호를 클릭하면 세션 메뉴로 이동됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-182">Clicking this version number will bring you to the session menu.</span></span>

### <a name="adding-your-own-powershell-paths-to-the-session-menu"></a><span data-ttu-id="8ef91-183">세션 메뉴에 고유한 PowerShell 경로 추가</span><span class="sxs-lookup"><span data-stu-id="8ef91-183">Adding your own PowerShell paths to the session menu</span></span>

<span data-ttu-id="8ef91-184">[Visual Studio Code 설정](https://code.visualstudio.com/docs/getstarted/settings)을 통해 세션 메뉴에 다른 PowerShell 실행 파일 경로를 추가할 수 있습니다. `powershell.powerShellAdditionalExePaths`.</span><span class="sxs-lookup"><span data-stu-id="8ef91-184">You can add other PowerShell executable paths to the session menu through the [Visual Studio Code setting](https://code.visualstudio.com/docs/getstarted/settings): `powershell.powerShellAdditionalExePaths`.</span></span>

<span data-ttu-id="8ef91-185">`powershell.powerShellAdditionalExePaths` 목록에 항목을 추가하거나, 목록이 `settings.json`에 없는 경우 목록을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-185">Add an item to the list `powershell.powerShellAdditionalExePaths` or create the list if it doesn't exist in your `settings.json`:</span></span>

```json
{
    // other settings...

    "powershell.powerShellAdditionalExePaths": [
        {
            "exePath": "C:\\Users\\tyler\\Downloads\\PowerShell\\pwsh.exe",
            "versionName": "Downloaded PowerShell"
        }
    ],

    // other settings...
}
```

<span data-ttu-id="8ef91-186">각 항목은 다음을 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-186">Each item must have:</span></span>

- <span data-ttu-id="8ef91-187">`exePath`: `pwsh` 또는 `powershell` 실행 파일의 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-187">`exePath`: The path to the `pwsh` or `powershell` executable.</span></span>
- <span data-ttu-id="8ef91-188">`versionName`: 세션 메뉴에 표시되는 텍스트입니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-188">`versionName`: The text that will show up in the session menu.</span></span>

<span data-ttu-id="8ef91-189">`powershell.powerShellDefaultVersion` 설정을 세션 메뉴에 표시되는 텍스트(마지막 설정의 `versionName`)로 설정하여 이 설정을 통해 사용하도록 기본 PowerShell 버전을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-189">You can set the default PowerShell version to use the `powershell.powerShellDefaultVersion` setting by setting this to the text displayed in the session menu (also known as the `versionName` in the last setting):</span></span>

```json
{
    // other settings...

    "powershell.powerShellAdditionalExePaths": [
        {
            "exePath": "C:\\Users\\tyler\\Downloads\\PowerShell\\pwsh.exe",
            "versionName": "Downloaded PowerShell"
        }
    ],

    "powershell.powerShellDefaultVersion": "Downloaded PowerShell",

    // other settings...
}
```

<span data-ttu-id="8ef91-190">이 설정을 구성한 후에는 Visual Studio Code를 다시 시작합니다. 또는 **명령 팔레트**에서 현재 Visual Studio Code 창을 다시 로드하려면 **Developer: Reload Window**를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-190">After you've configured this setting, restart Visual Studio Code or to reload the current Visual Studio Code window from the **Command Palette**, type **Developer: Reload Window**.</span></span>

<span data-ttu-id="8ef91-191">세션 메뉴를 열면 이제 추가 PowerShell 버전이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-191">If you open the session menu, you now see your additional PowerShell versions!</span></span>

> [!NOTE]
> <span data-ttu-id="8ef91-192">원본에서 PowerShell을 빌드하는 경우 이 방법은 PowerShell의 로컬 빌드를 테스트하는 좋은 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-192">If you build PowerShell from source, this is a great way to test out your local build of PowerShell.</span></span>

### <a name="configuration-settings-for-visual-studio-code"></a><span data-ttu-id="8ef91-193">Visual Studio Code에 대한 구성 파일</span><span class="sxs-lookup"><span data-stu-id="8ef91-193">Configuration settings for Visual Studio Code</span></span>

<span data-ttu-id="8ef91-194">먼저, Visual Studio Code에서 설정을 변경하는 방법에 익숙하지 않은 경우 [Visual Studio Code 설정 설명서](https://code.visualstudio.com/docs/getstarted/settings)를 확인하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-194">First, if you're not familiar with how to change settings in Visual Studio Code, we recommend looking at [Visual Studio Code's settings documentation](https://code.visualstudio.com/docs/getstarted/settings).</span></span>

<span data-ttu-id="8ef91-195">이전 단락의 단계를 따라 `settings.json`에 구성 설정을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-195">By using the steps in the previous paragraph, you can add configuration settings in `settings.json`.</span></span>

```json
{
    "editor.renderWhitespace": "all",
    "editor.renderControlCharacters": true,
    "files.trimTrailingWhitespace": true,
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

<span data-ttu-id="8ef91-196">이러한 설정이 모든 파일 형식에 영향을 주지 않으려는 경우 Visual Studio Code에서 언어별 구성을 허용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-196">If you don't want these settings to affect all files types, Visual Studio Code also allows per-language configurations.</span></span> <span data-ttu-id="8ef91-197">`[<language-name>]` 필드에서 설정을 지정하여 언어별 설정을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-197">Create a language-specific setting by putting settings in a `[<language-name>]` field.</span></span> <span data-ttu-id="8ef91-198">다음은 그 예입니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-198">For example:</span></span>

```json
{
    "[powershell]": {
        "files.encoding": "utf8bom",
        "files.autoGuessEncoding": true
    }
}
```

> [!TIP]
> <span data-ttu-id="8ef91-199">Visual Studio Code의 파일 인코딩에 대한 자세한 내용은 [파일 인코딩 이해](understanding-file-encoding.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8ef91-199">For more information about file encoding in Visual Studio Code, see [Understanding file encoding](understanding-file-encoding.md).</span></span>
>
> <span data-ttu-id="8ef91-200">PowerShell 편집을 위해 Visual Studio Code를 구성하는 방법에 대한 다른 팁은 [Visual Studio Code에서 ISE 환경을 복제하는 방법](How-To-Replicate-the-ISE-Experience-In-VSCode.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8ef91-200">Also check out the [How to replicate the ISE experience in Visual Studio Code](How-To-Replicate-the-ISE-Experience-In-VSCode.md) for other tips on how to configure Visual Studio Code for PowerShell editing.</span></span>

## <a name="debugging-with-visual-studio-code"></a><span data-ttu-id="8ef91-201">Visual Studio Code 디버깅</span><span class="sxs-lookup"><span data-stu-id="8ef91-201">Debugging with Visual Studio Code</span></span>

### <a name="no-workspace-debugging"></a><span data-ttu-id="8ef91-202">작업 공간 없이 디버깅</span><span class="sxs-lookup"><span data-stu-id="8ef91-202">No-workspace debugging</span></span>

<span data-ttu-id="8ef91-203">Visual Studio Code 버전 1.9부터 PowerShell 스크립트가 포함된 폴더를 열지 않고도 PowerShell 스크립트를 디버그할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-203">As of Visual Studio Code version 1.9 you can debug PowerShell scripts without opening the folder that contains the PowerShell script.</span></span> <span data-ttu-id="8ef91-204">**파일 > 파일 열기...** 로 PowerShell 스크립트 파일을 열고 특정 줄에 중단점을 설정한 후(<kbd>F9</kbd> 키 누름) <kbd>F5</kbd> 키를 눌러 디버깅을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-204">Open the PowerShell script file with **File > Open File...**, set a breakpoint on a line, press <kbd>F9</kbd>, and then press <kbd>F5</kbd> to start debugging.</span></span> <span data-ttu-id="8ef91-205">디버거, 단계, 디버깅 다시 시작 및 중지로 나눌 수 있는 디버그 작업 창이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-205">You should see the Debug actions pane appear which allows you to break into the debugger, step, resume, and stop debugging.</span></span>

### <a name="workspace-debugging"></a><span data-ttu-id="8ef91-206">작업 영역에서 디버깅</span><span class="sxs-lookup"><span data-stu-id="8ef91-206">Workspace debugging</span></span>

<span data-ttu-id="8ef91-207">작업 영역에서 디버깅은 Visual Studio Code의 **파일** 메뉴에서 **폴더 열기...** 를 사용하여 연 폴더의 컨텍스트에서 디버깅하는 것을 말합니다. 사용자가 여는 폴더는 일반적으로 PowerShell 프로젝트 폴더 및/또는 Git 리포지토리의 루트입니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-207">Workspace debugging refers to debugging in the context of a folder that you've opened in Visual Studio Code from the **File** menu using **Open Folder...**. The folder you open is typically your PowerShell project folder and/or the root of your Git repository.</span></span>

<span data-ttu-id="8ef91-208">이 모드에서도 <kbd>F5</kbd> 키만 눌러 현재 선택된 PowerShell 스크립트의 디버깅을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-208">Even in this mode, you can start debugging the currently selected PowerShell script by pressing <kbd>F5</kbd>.</span></span> <span data-ttu-id="8ef91-209">그러나 작업 영역에서 디버깅을 사용하면 현재 열려 있는 파일만 디버깅하는 것이 아니라 여러 디버그 구성도 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-209">However, workspace debugging allows you to define multiple debug configurations other than just debugging the currently open file.</span></span> <span data-ttu-id="8ef91-210">이에 대해서는 잠시 후에 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-210">We'll get to those in a moment.</span></span>

<span data-ttu-id="8ef91-211">디버그 구성 파일을 만들려면 다음 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-211">Follow these steps to create your debug configuration file:</span></span>

  1. <span data-ttu-id="8ef91-212"><kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>를 눌러 Windows 또는 Linux에서 **디버그** 보기를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-212">Open the **Debug** view on Windows or Linux by pressing <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>.</span></span> <span data-ttu-id="8ef91-213">macOS에서 <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-213">On macOS, press <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>.</span></span>
  1. <span data-ttu-id="8ef91-214">"launch.json 파일 만들기" 링크를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-214">Click the "create a launch.json file" link.</span></span>
  1. <span data-ttu-id="8ef91-215">Visual Studio Code에서 **환경 선택**에 대한 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-215">Visual Studio Code prompts you to **Select Environment**.</span></span> <span data-ttu-id="8ef91-216">**PowerShell**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-216">Choose **PowerShell**.</span></span>
  1. <span data-ttu-id="8ef91-217">마지막으로, 사용할 디버깅 형식을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-217">Lastly, choose the type of debugging you'd like to use:</span></span>

- <span data-ttu-id="8ef91-218">**현재 파일 시작** - 현재 활성화된 편집기 창에서 파일을 시작 및 디버그</span><span class="sxs-lookup"><span data-stu-id="8ef91-218">**Launch Current File** - Launch and debug the file in the currently active editor window</span></span>
- <span data-ttu-id="8ef91-219">**스크립트 실행** - 지정된 파일 또는 명령을 실행 및 디버그</span><span class="sxs-lookup"><span data-stu-id="8ef91-219">**Launch Script** - Launch and debug the specified file or command</span></span>
- <span data-ttu-id="8ef91-220">**대화형 세션** - 통합 콘솔에서 실행된 디버그 명령</span><span class="sxs-lookup"><span data-stu-id="8ef91-220">**Interactive Session** - Debug commands executed from the Integrated Console</span></span>
- <span data-ttu-id="8ef91-221">**연결** - 실행 중인 PowerShell 호스트 프로세스에 디버거를 연결</span><span class="sxs-lookup"><span data-stu-id="8ef91-221">**Attach** - Attach the debugger to a running PowerShell Host Process</span></span>

<span data-ttu-id="8ef91-222">이렇게 하면 Visual Studio Code는 작업 영역 폴더의 루트에 디렉터리와 파일 `.vscode\launch.json`을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-222">The result is that Visual Studio Code creates a directory and a file `.vscode\launch.json` in the root of your workspace folder.</span></span> <span data-ttu-id="8ef91-223">이 위치에 디버그 구성이 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-223">This location is where your debug configuration is stored.</span></span> <span data-ttu-id="8ef91-224">파일이 Git 리포지토리에 있을 경우 일반적으로 `launch.json` 파일을 커밋하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-224">If your files are in a Git repository, you typically want to commit the `launch.json` file.</span></span> <span data-ttu-id="8ef91-225">`launch.json` 파일의 내용은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-225">The contents of the `launch.json` file are:</span></span>

```json
{
  "version": "0.2.0",
  "configurations": [
      {
          "type": "PowerShell",
          "request": "launch",
          "name": "PowerShell Launch (current file)",
          "script": "${file}",
          "args": [],
          "cwd": "${file}"
      },
      {
          "type": "PowerShell",
          "request": "attach",
          "name": "PowerShell Attach to Host Process",
          "processId": "${command.PickPSHostProcess}",
          "runspaceId": 1
      },
      {
          "type": "PowerShell",
          "request": "launch",
          "name": "PowerShell Interactive Session",
          "cwd": "${workspaceRoot}"
      }
  ]
}
```

<span data-ttu-id="8ef91-226">이 파일은 일반적인 디버그 시나리오를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-226">This file represents the common debug scenarios.</span></span> <span data-ttu-id="8ef91-227">편집기에서 이 파일을 열면 **구성 추가...** 단추가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-227">When you open this file in the editor, you see an **Add Configuration...** button.</span></span> <span data-ttu-id="8ef91-228">이 단추를 클릭하여 더 많은 PowerShell 디버그 구성을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-228">You can click this button to add more PowerShell debug configurations.</span></span> <span data-ttu-id="8ef91-229">한 가지 유용한 구성은 **PowerShell: 스크립트 시작**입니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-229">One useful configuration to add is **PowerShell: Launch Script**.</span></span> <span data-ttu-id="8ef91-230">이 구성을 사용하면 편집기에서 현재 어떤 파일이 활성화되어 있는지 관계없이 <kbd>F5</kbd> 키를 누를 때마다 시작되어야 하는 선택적 인수를 갖는 파일을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-230">With this configuration, you can specify a file with optional arguments that should be launched whenever you press <kbd>F5</kbd> no matter which file is currently active in the editor.</span></span>

<span data-ttu-id="8ef91-231">디버그 구성이 설정된 후에 디버그 세션 중에 사용하려는 구성을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-231">After the debug configuration is established, you can select which configuration you want to use during a debug session.</span></span> <span data-ttu-id="8ef91-232">**디버그** 보기의 도구 모음에 있는 디버그 구성 드롭다운에서 구성을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-232">Select a configuration from the debug configuration drop-down in the **Debug** view's toolbar.</span></span>

## <a name="useful-resources"></a><span data-ttu-id="8ef91-233">유용한 리소스</span><span class="sxs-lookup"><span data-stu-id="8ef91-233">Useful resources</span></span>

<span data-ttu-id="8ef91-234">Visual Studio Code에 대한 PowerShell 확장 사용을 시작하는 데 도움이 되는 몇 가지 동영상 및 블로그 게시물이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-234">There are a few videos and blog posts that may be helpful to get you started using the PowerShell extension for Visual Studio Code:</span></span>

### <a name="videos"></a><span data-ttu-id="8ef91-235">동영상</span><span class="sxs-lookup"><span data-stu-id="8ef91-235">Videos</span></span>

- [<span data-ttu-id="8ef91-236">기본 PowerShell 편집기로 Visual Studio Code 사용</span><span class="sxs-lookup"><span data-stu-id="8ef91-236">Using Visual Studio Code as Your Default PowerShell Editor</span></span>](https://youtu.be/bGn45vIeAMM)
- [<span data-ttu-id="8ef91-237">Visual Studio Code: PowerShell 스크립트 디버깅 자세히 알아보기</span><span class="sxs-lookup"><span data-stu-id="8ef91-237">Visual Studio Code: deep dive into debugging your PowerShell scripts</span></span>](https://youtu.be/cSbIXmlkr8o)

### <a name="blog-posts"></a><span data-ttu-id="8ef91-238">블로그 게시물</span><span class="sxs-lookup"><span data-stu-id="8ef91-238">Blog posts</span></span>

- <span data-ttu-id="8ef91-239">[PowerShell 확장][ps-extension]</span><span class="sxs-lookup"><span data-stu-id="8ef91-239">[PowerShell Extension][ps-extension]</span></span>
- <span data-ttu-id="8ef91-240">[Visual Studio Code에서 PowerShell 스크립트 작성 및 디버깅][debug]</span><span class="sxs-lookup"><span data-stu-id="8ef91-240">[Write and debug PowerShell scripts in Visual Studio Code][debug]</span></span>
- <span data-ttu-id="8ef91-241">[Visual Studio Code 디버깅 지침][vscode-guide]</span><span class="sxs-lookup"><span data-stu-id="8ef91-241">[Debugging Visual Studio Code Guidance][vscode-guide]</span></span>
- <span data-ttu-id="8ef91-242">[Visual Studio Code에서 PowerShell 디버깅][ps-vscode]</span><span class="sxs-lookup"><span data-stu-id="8ef91-242">[Debugging PowerShell in Visual Studio Code][ps-vscode]</span></span>
- <span data-ttu-id="8ef91-243">[Visual Studio Code에서 PowerShell 개발 시작][getting-started]</span><span class="sxs-lookup"><span data-stu-id="8ef91-243">[Get started with PowerShell development in Visual Studio Code][getting-started]</span></span>
- <span data-ttu-id="8ef91-244">[PowerShell 개발을 위한 Visual Studio Code 편집 기능 – 1부][editing-part1]</span><span class="sxs-lookup"><span data-stu-id="8ef91-244">[Visual Studio Code editing features for PowerShell development – Part 1][editing-part1]</span></span>
- <span data-ttu-id="8ef91-245">[PowerShell 개발을 위한 Visual Studio Code 편집 기능 – 2부][editing-part2]</span><span class="sxs-lookup"><span data-stu-id="8ef91-245">[Visual Studio Code editing features for PowerShell development – Part 2][editing-part2]</span></span>
- <span data-ttu-id="8ef91-246">[Visual Studio Code에서 PowerShell 스크립트 디버깅 – 1부][debugging-part1]</span><span class="sxs-lookup"><span data-stu-id="8ef91-246">[Debugging PowerShell script in Visual Studio Code – Part 1][debugging-part1]</span></span>
- <span data-ttu-id="8ef91-247">[Visual Studio Code에서 PowerShell 스크립트 디버깅 – 2부][debugging-part2]</span><span class="sxs-lookup"><span data-stu-id="8ef91-247">[Debugging PowerShell script in Visual Studio Code – Part 2][debugging-part2]</span></span>

## <a name="powershell-extension-for-visual-studio-code"></a><span data-ttu-id="8ef91-248">Visual Studio Code용 PowerShell 확장</span><span class="sxs-lookup"><span data-stu-id="8ef91-248">PowerShell extension for Visual Studio Code</span></span>

<span data-ttu-id="8ef91-249">PowerShell 확장의 소스 코드는 [GitHub](https://github.com/PowerShell/vscode-powershell)에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-249">The PowerShell extension's source code can be found on [GitHub](https://github.com/PowerShell/vscode-powershell).</span></span>

<span data-ttu-id="8ef91-250">참가에 관심이 있는 경우 끌어오기 요청은 언제나 환영합니다.</span><span class="sxs-lookup"><span data-stu-id="8ef91-250">If you're interested in contributing, Pull Request are greatly appreciated.</span></span> <span data-ttu-id="8ef91-251">[GitHub의 개발자 설명서](https://github.com/PowerShell/vscode-powershell/blob/master/docs/development.md)를 따라 시작하세요.</span><span class="sxs-lookup"><span data-stu-id="8ef91-251">Follow along with the [developer documentation on GitHub](https://github.com/PowerShell/vscode-powershell/blob/master/docs/development.md) to get started.</span></span>

## <a name="troubleshooting-the-powershell-extension-for-visual-studio-code"></a><span data-ttu-id="8ef91-252">Visual Studio Code용 PowerShell 확장 문제 해결</span><span class="sxs-lookup"><span data-stu-id="8ef91-252">Troubleshooting the PowerShell extension for Visual Studio Code</span></span>

<span data-ttu-id="8ef91-253">PowerShell 스크립트 개발을 위해 Visual Studio Code를 사용하는 데 문제가 발생하는 경우 [GitHub의 문제 해결 가이드](https://github.com/PowerShell/vscode-powershell/blob/master/docs/troubleshooting.md)를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="8ef91-253">If you experience any issues using Visual Studio Code for PowerShell script development, please take a look at the [troubleshooting guide on GitHub](https://github.com/PowerShell/vscode-powershell/blob/master/docs/troubleshooting.md)</span></span>

[ise]: ../ise/Introducing-the-Windows-PowerShell-ISE.md
[install-pscore-linux]:  ../../install/Installing-PowerShell-Core-on-Linux.md
[install-pscore-macos]:  ../../install/Installing-PowerShell-Core-on-macOS.md
[install-pscore-windows]: ../../install/Installing-PowerShell-Core-on-Windows.md
[install-winps]: ../../install/Installing-Windows-PowerShell.md
[ps-extension]: https://blogs.msdn.microsoft.com/cdndevs/2015/12/11/visual-studio-code-powershell-extension/
[debug]: https://devblogs.microsoft.com/powershell/announcing-powershell-language-support-for-visual-studio-code-and-more/
[vscode-guide]: https://johnpapa.net/debugging-with-visual-studio-code/
[ps-vscode]: https://github.com/PowerShell/vscode-powershell/tree/master/examples
[getting-started]: https://devblogs.microsoft.com/scripting/get-started-with-powershell-development-in-visual-studio-code/
[editing-part1]: https://devblogs.microsoft.com/scripting/visual-studio-code-editing-features-for-powershell-development-part-1/
[editing-part2]: https://devblogs.microsoft.com/scripting/visual-studio-code-editing-features-for-powershell-development-part-2/
[debugging-part1]: https://devblogs.microsoft.com/scripting/debugging-powershell-script-in-visual-studio-code-part-1/
[debugging-part2]: https://devblogs.microsoft.com/scripting/debugging-powershell-script-in-visual-studio-code-part-2/
