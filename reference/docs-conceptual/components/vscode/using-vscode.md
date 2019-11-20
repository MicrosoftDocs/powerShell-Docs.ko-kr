---
title: PowerShell 개발에 Visual Studio 코드 사용
description: PowerShell 개발에 Visual Studio 코드 사용
ms.date: 11/07/2019
ms.openlocfilehash: 4f197e71d3b79828f466584f5d862415726818b1
ms.sourcegitcommit: a6e54a305fdeb6482321c77da8066d2f991c93e1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/15/2019
ms.locfileid: "74117389"
---
# <a name="using-visual-studio-code-for-powershell-development"></a><span data-ttu-id="2f458-103">PowerShell 개발에 Visual Studio 코드 사용</span><span class="sxs-lookup"><span data-stu-id="2f458-103">Using Visual Studio Code for PowerShell Development</span></span>

<span data-ttu-id="2f458-104">[PowerShell ISE][ise] 외에 PowerShell도 VSCode(Visual Studio Code)에서 원활하게 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-104">In addition to the [PowerShell ISE][ise], PowerShell is also well-supported in Visual Studio Code (VSCode).</span></span> <span data-ttu-id="2f458-105">또한 ISE는 PowerShell Core에 지원되지 않지만 VSCode는 모든 플랫폼(Windows, macOS 및 Linux)의 PowerShell Core에 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-105">The ISE isn't supported with PowerShell Core, but VSCode is supported for PowerShell Core on all platforms: Windows, macOS, and Linux.</span></span>

<span data-ttu-id="2f458-106">Windows 10을 사용하거나 하위 수준의 Windows OS(예: Windows 8.1 등)에 Windows Management Framework 5.1을 설치하여 PowerShell 버전 5와 Windows의 VSCode를 함께 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-106">You can use VSCode on Windows with PowerShell version 5 by using Windows 10 or by installing Windows Management Framework 5.1 for down-level Windows OSs such as Windows 8.1.</span></span> <span data-ttu-id="2f458-107">자세한 내용은 [WMF 5.1 설치 및 구성](/powershell/scripting/wmf/setup/install-configure)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2f458-107">For more information, see [Install and Configure WMF 5.1](/powershell/scripting/wmf/setup/install-configure).</span></span>

<span data-ttu-id="2f458-108">시작하기 전에 시스템에 PowerShell이 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-108">Before you begin, make sure PowerShell exists on your system.</span></span> <span data-ttu-id="2f458-109">Windows, macOS 및 Linux에서 최신 작업을 수행하려면 다음 링크를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2f458-109">For modern workloads on Windows, macOS, and Linux, see the following links:</span></span>

- <span data-ttu-id="2f458-110">[Linux에서 PowerShell Core 설치][install-pscore-linux]</span><span class="sxs-lookup"><span data-stu-id="2f458-110">[Installing PowerShell Core on Linux][install-pscore-linux]</span></span>
- <span data-ttu-id="2f458-111">[macOS에서 PowerShell Core 설치][install-pscore-macos]</span><span class="sxs-lookup"><span data-stu-id="2f458-111">[Installing PowerShell Core on macOS][install-pscore-macos]</span></span>
- <span data-ttu-id="2f458-112">[Windows에서 PowerShell Core 설치][install-pscore-windows]</span><span class="sxs-lookup"><span data-stu-id="2f458-112">[Installing PowerShell Core on Windows][install-pscore-windows]</span></span>

<span data-ttu-id="2f458-113">기존 Windows PowerShell 워크로드의 경우 [Windows PowerShell 설치][install-winps]를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2f458-113">For traditional Windows PowerShell workloads, see [Installing Windows PowerShell][install-winps].</span></span>

## <a name="editing-with-vscode"></a><span data-ttu-id="2f458-114">VSCode를 사용하여 편집</span><span class="sxs-lookup"><span data-stu-id="2f458-114">Editing with VSCode</span></span>

1. <span data-ttu-id="2f458-115">VSCode를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-115">Install VSCode.</span></span> <span data-ttu-id="2f458-116">자세한 내용은 [Visual Studio Code 설치](https://code.visualstudio.com/Docs/setup/setup-overview) 개요를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2f458-116">For more information, see the overview [Setting up Visual Studio Code](https://code.visualstudio.com/Docs/setup/setup-overview).</span></span>

   <span data-ttu-id="2f458-117">각 플랫폼에 대한 설치 지침은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-117">There are installation instructions for each platform:</span></span>

   - <span data-ttu-id="2f458-118">**Linux**: [Linux에서 VSCode 실행](https://code.visualstudio.com/docs/setup/linux) 페이지의 설치 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-118">**Linux**: follow the installation instructions on the [Running VSCode on Linux](https://code.visualstudio.com/docs/setup/linux) page.</span></span>
   - <span data-ttu-id="2f458-119">**macOS**: [macOS에서 VSCode 실행](https://code.visualstudio.com/docs/setup/mac) 페이지의 설치 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-119">**macOS**: follow the installation instructions on the [Running VSCode on macOS](https://code.visualstudio.com/docs/setup/mac) page.</span></span>

     > [!IMPORTANT]
     > <span data-ttu-id="2f458-120">macOS에서 PowerShell 확장이 제대로 작동하려면 OpenSSL을 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-120">On macOS, you must install OpenSSL for the PowerShell extension to work correctly.</span></span> <span data-ttu-id="2f458-121">이를 위한 가장 쉬운 방법은 [Homebrew](https://brew.sh/)를 설치한 후 `brew install openssl`을 실행하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-121">The easiest way to accomplish this is to install [Homebrew](https://brew.sh/) and then run `brew install openssl`.</span></span> <span data-ttu-id="2f458-122">이제 VSCode는 PowerShell 확장을 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-122">VSCode can now load the PowerShell extension successfully.</span></span>

   - <span data-ttu-id="2f458-123">**Windows**: [Windows에서 VSCode 실행](https://code.visualstudio.com/docs/setup/windows) 페이지의 설치 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-123">**Windows**: follow the installation instructions on the [Running VSCode on Windows](https://code.visualstudio.com/docs/setup/windows) page.</span></span>

1. <span data-ttu-id="2f458-124">PowerShell 확장을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-124">Install the PowerShell Extension.</span></span>

   1. <span data-ttu-id="2f458-125">다음을 수행하여 VSCode 앱을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-125">Launch the VSCode app by:</span></span>
      - <span data-ttu-id="2f458-126">**Windows**: PowerShell 세션에서 `code` 입력</span><span class="sxs-lookup"><span data-stu-id="2f458-126">**Windows**: typing `code` in your PowerShell session</span></span>
      - <span data-ttu-id="2f458-127">**Linux**: 터미널에서 `code` 입력</span><span class="sxs-lookup"><span data-stu-id="2f458-127">**Linux**: typing `code` in your terminal</span></span>
      - <span data-ttu-id="2f458-128">**macOS**: 터미널에서 `code` 입력</span><span class="sxs-lookup"><span data-stu-id="2f458-128">**macOS**: typing `code` in your terminal</span></span>
   1. <span data-ttu-id="2f458-129"><kbd>Ctrl</kbd>+<kbd>P</kbd>를 눌러 Windows 또는 Linux에서 **Quick Open**을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-129">Launch **Quick Open** on Windows or Linux by pressing <kbd>Ctrl</kbd>+<kbd>P</kbd>.</span></span> <span data-ttu-id="2f458-130">macOS에서 <kbd>Cmd</kbd>+<kbd>P</kbd>를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-130">On macOS, press <kbd>Cmd</kbd>+<kbd>P</kbd>.</span></span>
   1. <span data-ttu-id="2f458-131">Quick Open에서 `ext install powershell`을 입력하고**Enter** 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-131">In Quick Open, type `ext install powershell` and press **Enter**.</span></span>
   1. <span data-ttu-id="2f458-132">사이드바에 **확장** 보기가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-132">The **Extensions** view opens on the Side Bar.</span></span> <span data-ttu-id="2f458-133">Microsoft의 PowerShell 확장을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-133">Select the PowerShell extension from Microsoft.</span></span>
      <span data-ttu-id="2f458-134">다음 이미지와 비슷한 VSCode 화면이 표시되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-134">You should see a VSCode screen similar to the following image:</span></span>

      ![VSCode](../../images/using-vscode/vscode.png)

   1. <span data-ttu-id="2f458-136">Microsoft의 PowerShell 확장에서 **설치** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-136">Click the **Install** button on the PowerShell extension from Microsoft.</span></span>
   1. <span data-ttu-id="2f458-137">설치 후 **설치** 단추가 **다시 로드**로 바뀌는 것을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-137">After the install, you see the **Install** button turns to **Reload**.</span></span> <span data-ttu-id="2f458-138">**다시 로드**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-138">Click on **Reload**.</span></span>
   1. <span data-ttu-id="2f458-139">VSCode가 다시 로드되면 편집할 준비가 된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-139">After VSCode has reloaded, you're ready for editing.</span></span>

<span data-ttu-id="2f458-140">예를 들어 새 파일을 만들려면 **파일 > 새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-140">For example, to create a new file, click **File > New**.</span></span> <span data-ttu-id="2f458-141">저장하려면 **파일 > 저장**을 클릭한 후 파일 이름을 제공합니다(예: `HelloWorld.ps1`).</span><span class="sxs-lookup"><span data-stu-id="2f458-141">To save it, click **File > Save** and then provide a file name, such as `HelloWorld.ps1`.</span></span> <span data-ttu-id="2f458-142">파일을 닫으려면 파일 이름 옆에 있는 `X`를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-142">To close the file, click the `X` next to the file name.</span></span> <span data-ttu-id="2f458-143">VSCode를 종료하려면 **파일 > 끝내기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-143">To exit VSCode, **File > Exit**.</span></span>

### <a name="installing-the-powershell-extension-on-restricted-systems"></a><span data-ttu-id="2f458-144">제한된 시스템에 PowerShell 확장 설치</span><span class="sxs-lookup"><span data-stu-id="2f458-144">Installing the PowerShell Extension on Restricted Systems</span></span>

<span data-ttu-id="2f458-145">일부 시스템은 모든 코드 서명을 확인하여 시스템에서 실행될 PowerShell Editor Services를 수동으로 승인해야 하는 방식으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-145">Some systems are set up in a way that requires all code signatures to be checked and requires PowerShell Editor Services to be manually approved to run on the system.</span></span> <span data-ttu-id="2f458-146">PowerShell 확장을 설치했지만 다음과 같은 오류가 수신되는 경우 실행 정책을 변경하는 그룹 정책 업데이트가 원인일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-146">A Group Policy update that changes execution policy is a likely cause if you've installed the PowerShell extension but are receiving an error such as:</span></span>

```
Language server startup failed.
```

<span data-ttu-id="2f458-147">PowerShell Editor Services를 수동으로 승인하여 VSCode용 PowerShell 확장을 수동으로 승인하려면 PowerShell 프롬프트를 열고 다음을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-147">To manually approve PowerShell Editor Services and the PowerShell extension for VSCode, open a PowerShell prompt and run the following command:</span></span>

```powershell
Import-Module $HOME\.vscode\extensions\ms-vscode.powershell*\modules\PowerShellEditorServices\PowerShellEditorServices.psd1
```

<span data-ttu-id="2f458-148">**이 신뢰되지 않은 게시자가 서명한 소프트웨어를 실행하시겠습니까?** 가 포함된 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-148">You're prompted with **Do you want to run software from this untrusted publisher?**</span></span> <span data-ttu-id="2f458-149">`A`을 입력하여 파일을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-149">Type `A` to run the file.</span></span> <span data-ttu-id="2f458-150">그런 다음, VSCode를 열고 PowerShell 확장이 제대로 작동하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-150">Then, open VSCode and check that the PowerShell extension is functioning properly.</span></span> <span data-ttu-id="2f458-151">그래도 시작하는 데 문제가 있으면 [GitHub](https://github.com/PowerShell/vscode-powershell/issues)에서 알려 주세요.</span><span class="sxs-lookup"><span data-stu-id="2f458-151">If you still have issues getting started, let us know on [GitHub](https://github.com/PowerShell/vscode-powershell/issues).</span></span>

### <a name="choosing-a-version-of-powershell-to-use-with-the-extension"></a><span data-ttu-id="2f458-152">확장과 함께 사용할 PowerShell 버전 선택</span><span class="sxs-lookup"><span data-stu-id="2f458-152">Choosing a version of PowerShell to use with the extension</span></span>

<span data-ttu-id="2f458-153">Windows PowerShell과 함께 PowerShell Core를 side-by-side 설치하면 PowerShell 확장과 함께 특정 버전의 PowerShell을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-153">With PowerShell Core installing side-by-side with Windows PowerShell, it's now possible to use a particular version of PowerShell with the PowerShell extension.</span></span> <span data-ttu-id="2f458-154">다음 단계에 따라 해당 버전을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-154">Use the following steps to choose the version:</span></span>

1. <span data-ttu-id="2f458-155">Windows 또는 Linux에서 <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>를 눌러 **명령 팔레트**를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-155">Open the **Command Palette** on Windows or Linux with <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>.</span></span> <span data-ttu-id="2f458-156">macOS에서 <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-156">On macOS, use <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>.</span></span>
1. <span data-ttu-id="2f458-157">**세션**을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-157">Search for **Session**.</span></span>
1. <span data-ttu-id="2f458-158">**PowerShell: 세션 메뉴 표시**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-158">Click on **PowerShell: Show Session Menu**.</span></span>
1. <span data-ttu-id="2f458-159">목록에서 사용하려는 PowerShell 버전을 선택합니다(예: **PowerShell Core**).</span><span class="sxs-lookup"><span data-stu-id="2f458-159">Choose the version of PowerShell you want to use from the list, for example: **PowerShell Core**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2f458-160">이 기능은 운영 체제별로 몇 가지 잘 알려진 경로를 확인하여 PowerShell의 설치 위치를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-160">This feature looks at a few well-known paths on different operating systems to discover install locations of PowerShell.</span></span> <span data-ttu-id="2f458-161">일반적이지 않은 위치에 PowerShell을 설치한 경우 처음에 PowerShell이 세션 메뉴에 표시되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-161">If you installed PowerShell to a non-typical location, it might not show up initially in the Session Menu.</span></span> <span data-ttu-id="2f458-162">아래 설명된 대로 [사용자 지정 경로를 추가](#adding-your-own-powershell-paths-to-the-session-menu)하여 세션 메뉴를 확장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-162">You can extend the session menu by [adding your own custom paths](#adding-your-own-powershell-paths-to-the-session-menu) as described below.</span></span>

>[!NOTE]
> <span data-ttu-id="2f458-163">세션 메뉴에 액세스하는 또 다른 방법이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-163">There's another way to get to the session menu.</span></span> <span data-ttu-id="2f458-164">PowerShell 파일이 편집기에서 열리면 오른쪽 아래에 녹색 버전 번호가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-164">When a PowerShell file is open in your editor, you see a green version number in the bottom right.</span></span> <span data-ttu-id="2f458-165">이 버전 번호를 클릭하면 세션 메뉴로 이동됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-165">Clicking this version number will bring you to the session menu.</span></span>

### <a name="adding-your-own-powershell-paths-to-the-session-menu"></a><span data-ttu-id="2f458-166">세션 메뉴에 고유한 PowerShell 경로 추가</span><span class="sxs-lookup"><span data-stu-id="2f458-166">Adding your own PowerShell paths to the session menu</span></span>

<span data-ttu-id="2f458-167">VSCode 설정을 통해 세션 메뉴에 다른 PowerShell 실행 파일 경로를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-167">You can add other PowerShell executable paths to the session menu through a VSCode setting.</span></span>

<span data-ttu-id="2f458-168">`powershell.powerShellAdditionalExePaths` 목록에 항목을 추가하거나, 목록이 `settings.json`에 없는 경우 목록을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-168">Add an item to the list `powershell.powerShellAdditionalExePaths` or create the list if it doesn't exist in your `settings.json`:</span></span>

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

<span data-ttu-id="2f458-169">각 항목은 다음을 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-169">Each item must have:</span></span>

* <span data-ttu-id="2f458-170">`exePath`: `pwsh` 또는 `powershell` 실행 파일의 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-170">`exePath`: The path to the `pwsh` or `powershell` executable.</span></span>
* <span data-ttu-id="2f458-171">`versionName`: 세션 메뉴에 표시되는 텍스트입니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-171">`versionName`: The text that will show up in the session menu.</span></span>

<span data-ttu-id="2f458-172">`powershell.powerShellDefaultVersion` 설정을 세션 메뉴에 표시되는 텍스트(마지막 설정의 `versionName`)로 설정하여 이 설정을 통해 사용하도록 기본 PowerShell 버전을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-172">You can set the default PowerShell version to use the `powershell.powerShellDefaultVersion` setting by setting this to the text displayed in the session menu (also known as the `versionName` in the last setting):</span></span>

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

<span data-ttu-id="2f458-173">이 설정을 구성한 후에는 VSCode를 다시 시작하거나 **명령 팔레트**에서 현재 VSCode 창을 다시 로드하려면 **Developer: Reload Window**를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-173">After you've configured this setting, restart VSCode or to reload the current VSCode window from the **Command Palette**, type **Developer: Reload Window**.</span></span>

<span data-ttu-id="2f458-174">세션 메뉴를 열면 이제 추가 PowerShell 버전이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-174">If you open the session menu, you now see your additional PowerShell versions!</span></span>

> [!NOTE]
> <span data-ttu-id="2f458-175">원본에서 PowerShell을 빌드하는 경우 이 방법은 PowerShell의 로컬 빌드를 테스트하는 좋은 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-175">If you build PowerShell from source, this is a great way to test out your local build of PowerShell.</span></span>

### <a name="configuration-settings-for-vscode"></a><span data-ttu-id="2f458-176">VSCode에 대한 구성 설정 편집</span><span class="sxs-lookup"><span data-stu-id="2f458-176">Configuration settings for VSCode</span></span>

<span data-ttu-id="2f458-177">이전 단락의 단계를 따라 `settings.json`에 구성 설정을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-177">By using the steps in the previous paragraph, you can add configuration settings in `settings.json`.</span></span>

<span data-ttu-id="2f458-178">VSCode에는 다음 구성 설정을 권장합니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-178">We recommend the following configuration settings for VSCode:</span></span>

```json
{
    "csharp.suppressDotnetRestoreNotification": true,
    "editor.renderWhitespace": "all",
    "editor.renderControlCharacters": true,
    "omnisharp.projectLoadTimeout": 120,
    "files.trimTrailingWhitespace": true,
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

<span data-ttu-id="2f458-179">이러한 설정이 모든 파일 형식에 영향을 주지 않으려는 경우 VSCode에서 언어별 구성을 허용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-179">If you don't want these settings to affect all files types, VSCode also allows per-language configurations.</span></span> <span data-ttu-id="2f458-180">`[<language-name>]` 필드에서 설정을 지정하여 언어별 설정을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-180">Create a language-specific setting by putting settings in a `[<language-name>]` field.</span></span> <span data-ttu-id="2f458-181">예:</span><span class="sxs-lookup"><span data-stu-id="2f458-181">For example:</span></span>

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

<span data-ttu-id="2f458-182">VSCode의 파일 인코딩에 대한 자세한 내용은 [파일 인코딩 이해](understanding-file-encoding.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2f458-182">For more information about file encoding in VSCode, see [Understanding file encoding](understanding-file-encoding.md).</span></span>

## <a name="debugging-with-vscode"></a><span data-ttu-id="2f458-183">VSCode를 사용하여 디버깅</span><span class="sxs-lookup"><span data-stu-id="2f458-183">Debugging with VSCode</span></span>

### <a name="no-workspace-debugging"></a><span data-ttu-id="2f458-184">작업 공간 없이 디버깅</span><span class="sxs-lookup"><span data-stu-id="2f458-184">No-workspace debugging</span></span>

<span data-ttu-id="2f458-185">VSCode 버전 1.9부터 PowerShell 스크립트가 포함된 폴더를 열지 않고도 PowerShell 스크립트를 디버그할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-185">As of VSCode version 1.9 you can debug PowerShell scripts without opening the folder that contains the PowerShell script.</span></span> <span data-ttu-id="2f458-186">**파일 > 파일 열기...** 로 PowerShell 스크립트 파일을 열고 특정 줄에 중단점을 설정한 후(<kbd>F9</kbd> 키 누름) <kbd>F5</kbd> 키를 눌러 디버깅을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-186">Open the PowerShell script file with **File > Open File...**, set a breakpoint on a line, press <kbd>F9</kbd>, and then press <kbd>F5</kbd> to start debugging.</span></span> <span data-ttu-id="2f458-187">디버거, 단계, 디버깅 다시 시작 및 중지로 나눌 수 있는 디버그 작업 창이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-187">You should see the Debug actions pane appear which allows you to break into the debugger, step, resume, and stop debugging.</span></span>

### <a name="workspace-debugging"></a><span data-ttu-id="2f458-188">작업 영역에서 디버깅</span><span class="sxs-lookup"><span data-stu-id="2f458-188">Workspace debugging</span></span>

<span data-ttu-id="2f458-189">작업 영역에서 디버깅은 Visual Studio Code의 **파일** 메뉴에서 **폴더 열기...** 를 사용하여 연 폴더의 컨텍스트에서 디버깅하는 것을 말합니다. 사용자가 여는 폴더는 일반적으로 PowerShell 프로젝트 폴더 및/또는 Git 리포지토리의 루트입니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-189">Workspace debugging refers to debugging in the context of a folder that you've opened in Visual Studio Code from the **File** menu using **Open Folder...**. The folder you open is typically your PowerShell project folder and/or the root of your Git repository.</span></span>

<span data-ttu-id="2f458-190">이 모드에서도 <kbd>F5</kbd> 키만 눌러 현재 선택된 PowerShell 스크립트의 디버깅을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-190">Even in this mode, you can start debugging the currently selected PowerShell script by pressing <kbd>F5</kbd>.</span></span> <span data-ttu-id="2f458-191">그러나 작업 영역에서 디버깅을 사용하면 현재 열려 있는 파일만 디버깅하는 것이 아니라 여러 디버그 구성도 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-191">However, workspace debugging allows you to define multiple debug configurations other than just debugging the currently open file.</span></span> <span data-ttu-id="2f458-192">예를 들어, 다음을 위한 구성을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-192">For instance, you can add a configuration to:</span></span>

- <span data-ttu-id="2f458-193">디버거에서 Pester 테스트를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-193">Launch Pester tests in the debugger.</span></span>
- <span data-ttu-id="2f458-194">디버거에서 인수를 갖는 특정 파일을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-194">Launch a specific file with arguments in the debugger.</span></span>
- <span data-ttu-id="2f458-195">디버거에서 대화형 세션을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-195">Launch an interactive session in the debugger.</span></span>
- <span data-ttu-id="2f458-196">PowerShell 호스트 프로세스에 디버거를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-196">Attach the debugger to a PowerShell host process.</span></span>

<span data-ttu-id="2f458-197">디버그 구성 파일을 만들려면 다음 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-197">Follow these steps to create your debug configuration file:</span></span>

  1. <span data-ttu-id="2f458-198"><kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>를 눌러 Windows 또는 Linux에서 **디버그** 보기를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-198">Open the **Debug** view on Windows or Linux by pressing <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>.</span></span> <span data-ttu-id="2f458-199">macOS에서 <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-199">On macOS, press <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>.</span></span>
  1. <span data-ttu-id="2f458-200">도구 모음에서 **구성** 기어 아이콘을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-200">Click the **Configure** gear icon in the toolbar.</span></span>
  1. <span data-ttu-id="2f458-201">VSCode에서 **환경 선택** 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-201">VSCode prompts you to **Select Environment**.</span></span> <span data-ttu-id="2f458-202">**PowerShell**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-202">Choose **PowerShell**.</span></span>

<span data-ttu-id="2f458-203">이렇게 하면 VSCode는 작업 영역 폴더의 루트에 디렉터리와 파일 `.vscode\launch.json`을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-203">The result is that VSCode creates a directory and a file `.vscode\launch.json` in the root of your workspace folder.</span></span> <span data-ttu-id="2f458-204">이 위치에 디버그 구성이 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-204">This location is where your debug configuration is stored.</span></span> <span data-ttu-id="2f458-205">파일이 Git 리포지토리에 있을 경우 일반적으로 `launch.json` 파일을 커밋하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-205">If your files are in a Git repository, you typically want to commit the `launch.json` file.</span></span> <span data-ttu-id="2f458-206">`launch.json` 파일의 내용은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-206">The contents of the `launch.json` file are:</span></span>

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

<span data-ttu-id="2f458-207">이 파일은 일반적인 디버그 시나리오를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-207">This file represents the common debug scenarios.</span></span> <span data-ttu-id="2f458-208">편집기에서 이 파일을 열면 **구성 추가...** 단추가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-208">When you open this file in the editor, you see an **Add Configuration...** button.</span></span> <span data-ttu-id="2f458-209">이 단추를 클릭하여 더 많은 PowerShell 디버그 구성을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-209">You can click this button to add more PowerShell debug configurations.</span></span> <span data-ttu-id="2f458-210">한 가지 유용한 구성은 **PowerShell: 스크립트 시작**입니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-210">One useful configuration to add is **PowerShell: Launch Script**.</span></span> <span data-ttu-id="2f458-211">이 구성을 사용하면 편집기에서 현재 어떤 파일이 활성화되어 있는지 관계없이 <kbd>F5</kbd> 키를 누를 때마다 시작되어야 하는 선택적 인수를 갖는 파일을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-211">With this configuration, you can specify a file with optional arguments that should be launched whenever you press <kbd>F5</kbd> no matter which file is currently active in the editor.</span></span>

<span data-ttu-id="2f458-212">디버그 구성이 설정된 후에 디버그 세션 중에 사용하려는 구성을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-212">After the debug configuration is established, you can select which configuration you want to use during a debug session.</span></span> <span data-ttu-id="2f458-213">**디버그** 보기의 도구 모음에 있는 디버그 구성 드롭다운에서 구성을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-213">Select a configuration from the debug configuration drop-down in the **Debug** view's toolbar.</span></span>

<span data-ttu-id="2f458-214">Visual Studio Code에 대한 PowerShell 확장 사용을 시작하는 데 도움이 되는 몇 가지 블로그가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-214">There are a few blogs that may be helpful to get you started using PowerShell extension for Visual Studio Code:</span></span>

- <span data-ttu-id="2f458-215">[PowerShell 확장][ps-extension]</span><span class="sxs-lookup"><span data-stu-id="2f458-215">[PowerShell Extension][ps-extension]</span></span>
- <span data-ttu-id="2f458-216">[Visual Studio Code에서 PowerShell 스크립트 작성 및 디버깅][debug]</span><span class="sxs-lookup"><span data-stu-id="2f458-216">[Write and debug PowerShell scripts in Visual Studio Code][debug]</span></span>
- <span data-ttu-id="2f458-217">[Visual Studio Code 디버깅 지침][vscode-guide]</span><span class="sxs-lookup"><span data-stu-id="2f458-217">[Debugging Visual Studio Code Guidance][vscode-guide]</span></span>
- <span data-ttu-id="2f458-218">[Visual Studio Code에서 PowerShell 디버깅][ps-vscode]</span><span class="sxs-lookup"><span data-stu-id="2f458-218">[Debugging PowerShell in Visual Studio Code][ps-vscode]</span></span>
- <span data-ttu-id="2f458-219">[Visual Studio Code에서 PowerShell 개발 시작][getting-started]</span><span class="sxs-lookup"><span data-stu-id="2f458-219">[Get started with PowerShell development in Visual Studio Code][getting-started]</span></span>
- <span data-ttu-id="2f458-220">[PowerShell 개발을 위한 Visual Studio Code 편집 기능 – 1부][editing-part1]</span><span class="sxs-lookup"><span data-stu-id="2f458-220">[Visual Studio Code editing features for PowerShell development – Part 1][editing-part1]</span></span>
- <span data-ttu-id="2f458-221">[PowerShell 개발을 위한 Visual Studio Code 편집 기능 – 2부][editing-part2]</span><span class="sxs-lookup"><span data-stu-id="2f458-221">[Visual Studio Code editing features for PowerShell development – Part 2][editing-part2]</span></span>
- <span data-ttu-id="2f458-222">[Visual Studio Code에서 PowerShell 스크립트 디버깅 – 1부][debugging-part1]</span><span class="sxs-lookup"><span data-stu-id="2f458-222">[Debugging PowerShell script in Visual Studio Code – Part 1][debugging-part1]</span></span>
- <span data-ttu-id="2f458-223">[Visual Studio Code에서 PowerShell 스크립트 디버깅 – 2부][debugging-part2]</span><span class="sxs-lookup"><span data-stu-id="2f458-223">[Debugging PowerShell script in Visual Studio Code – Part 2][debugging-part2]</span></span>

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

## <a name="powershell-extension-for-vscode"></a><span data-ttu-id="2f458-224">VSCode용 PowerShell 확장</span><span class="sxs-lookup"><span data-stu-id="2f458-224">PowerShell Extension for VSCode</span></span>

<span data-ttu-id="2f458-225">PowerShell 확장의 소스 코드는 [GitHub](https://github.com/PowerShell/vscode-powershell)에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f458-225">The PowerShell extension's source code can be found on [GitHub](https://github.com/PowerShell/vscode-powershell).</span></span>
