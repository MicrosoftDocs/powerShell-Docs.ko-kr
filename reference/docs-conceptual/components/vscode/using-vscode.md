---
title: PowerShell 개발에 Visual Studio 코드 사용
description: PowerShell 개발에 Visual Studio 코드 사용
ms.date: 08/06/2018
ms.openlocfilehash: 1e9b9d811a39656327af2810bd6dc8aaf3fde3a4
ms.sourcegitcommit: ce46e5098786e19d521b4bf948ff62d2b90bc53e
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251390"
---
# <a name="using-visual-studio-code-for-powershell-development"></a><span data-ttu-id="09e3d-103">PowerShell 개발에 Visual Studio 코드 사용</span><span class="sxs-lookup"><span data-stu-id="09e3d-103">Using Visual Studio Code for PowerShell Development</span></span>

<span data-ttu-id="09e3d-104">[PowerShell ISE][ise] 외에 PowerShell도 Visual Studio Code에서 원활하게 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="09e3d-104">In addition to the [PowerShell ISE][ise], PowerShell is also well-supported in Visual Studio Code.</span></span>
<span data-ttu-id="09e3d-105">또한 ISE는 PowerShell Core에 지원되지 않지만 Visual Studio Code는 모든 플랫폼(Windows, macOS 및 Linux)의 PowerShell Core에 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="09e3d-105">Furthermore, the ISE is not supported with PowerShell Core, while Visual Studio Code is supported for PowerShell Core on all platforms (Windows, macOS, and Linux)</span></span>

<span data-ttu-id="09e3d-106">Windows 10을 사용하거나 하위 수준의 Windows OS(예: Windows 8.1 등)에 [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395)을 설치하여 PowerShell 버전 5와 Windows의 Visual Studio Code를 함께 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="09e3d-106">You can use Visual Studio Code on Windows with PowerShell version 5 by using Windows 10 or by installing [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395) for down-level Windows OSs (e.g. Windows 8.1, etc.).</span></span>

<span data-ttu-id="09e3d-107">시작하기 전에 시스템에 PowerShell이 있는지 확인하시기 바랍니다.</span><span class="sxs-lookup"><span data-stu-id="09e3d-107">Before starting it, please make sure PowerShell exists on your system.</span></span>
<span data-ttu-id="09e3d-108">Windows, macOS 및 Linux의 현대식 워크로드의 경우 다음을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="09e3d-108">For modern workloads on Windows, macOS, and Linux, see:</span></span>

- <span data-ttu-id="09e3d-109">[Linux에서 PowerShell Core 설치][install-pscore-linux]</span><span class="sxs-lookup"><span data-stu-id="09e3d-109">[Installing PowerShell Core on Linux][install-pscore-linux]</span></span>
- <span data-ttu-id="09e3d-110">[macOS에서 PowerShell Core 설치][install-pscore-macos]</span><span class="sxs-lookup"><span data-stu-id="09e3d-110">[Installing PowerShell Core on macOS][install-pscore-macos]</span></span>
- <span data-ttu-id="09e3d-111">[Windows에서 PowerShell Core 설치][install-pscore-windows]</span><span class="sxs-lookup"><span data-stu-id="09e3d-111">[Installing PowerShell Core on Windows][install-pscore-windows]</span></span>

<span data-ttu-id="09e3d-112">기존 Windows PowerShell 워크로드의 경우 [Windows PowerShell 설치][install-winps]를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="09e3d-112">For traditional Windows PowerShell workloads, see [Installing Windows PowerShell][install-winps].</span></span>

## <a name="editing-with-visual-studio-code"></a><span data-ttu-id="09e3d-113">Visual Studio Code로 편집</span><span class="sxs-lookup"><span data-stu-id="09e3d-113">Editing with Visual Studio Code</span></span>

### <a name="1-installing-visual-studio-codehttpscodevisualstudiocomdocssetupsetup-overview"></a>[<span data-ttu-id="09e3d-114">1. Visual Studio Code 설치</span><span class="sxs-lookup"><span data-stu-id="09e3d-114">1. Installing Visual Studio Code</span></span>](https://code.visualstudio.com/Docs/setup/setup-overview)

- <span data-ttu-id="09e3d-115">**Linux**: [Linux에서 VS Code 실행](https://code.visualstudio.com/docs/setup/linux) 페이지의 설치 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="09e3d-115">**Linux**: follow the installation instructions on the [Running VS Code on Linux](https://code.visualstudio.com/docs/setup/linux) page</span></span>

- <span data-ttu-id="09e3d-116">**macOS**: [macOS에서 VS Code 실행](https://code.visualstudio.com/docs/setup/mac) 페이지의 설치 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="09e3d-116">**macOS**: follow the installation instructions on the [Running VS Code on macOS](https://code.visualstudio.com/docs/setup/mac) page</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="09e3d-117">macOS에서 PowerShell 확장이 제대로 작동하려면 OpenSSL을 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="09e3d-117">On macOS, you must install OpenSSL for the PowerShell extension to work correctly.</span></span>
  > <span data-ttu-id="09e3d-118">이를 위한 가장 쉬운 방법은 [Homebrew](https://brew.sh/)를 설치한 후 `brew install openssl`을 실행하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="09e3d-118">The easiest way to accomplish this is to install [Homebrew](https://brew.sh/) and then run `brew install openssl`.</span></span>
  > <span data-ttu-id="09e3d-119">이제 VS Code는 PowerShell 확장을 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="09e3d-119">VS Code can now load the PowerShell extension successfully.</span></span>

- <span data-ttu-id="09e3d-120">**Windows**: [Windows에서 VS Code 실행](https://code.visualstudio.com/docs/setup/windows) 페이지의 설치 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="09e3d-120">**Windows**: follow the installation instructions on the [Running VS Code on Windows](https://code.visualstudio.com/docs/setup/windows) page</span></span>

### <a name="2-installing-powershell-extension"></a><span data-ttu-id="09e3d-121">2. PowerShell 확장 설치</span><span class="sxs-lookup"><span data-stu-id="09e3d-121">2. Installing PowerShell Extension</span></span>

- <span data-ttu-id="09e3d-122">다음과 같은 방법으로 Visual Studio Code 앱을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="09e3d-122">Launch the Visual Studio Code app by:</span></span>
  - <span data-ttu-id="09e3d-123">**Windows**: PowerShell 세션에서 `code` 입력</span><span class="sxs-lookup"><span data-stu-id="09e3d-123">**Windows**: typing `code` in your PowerShell session</span></span>
  - <span data-ttu-id="09e3d-124">**Linux**: 터미널에서 `code` 입력</span><span class="sxs-lookup"><span data-stu-id="09e3d-124">**Linux**: typing `code` in your terminal</span></span>
  - <span data-ttu-id="09e3d-125">**macOS**: 터미널에서 `code` 입력</span><span class="sxs-lookup"><span data-stu-id="09e3d-125">**macOS**: typing `code` in your terminal</span></span>

- <span data-ttu-id="09e3d-126">**Ctrl+P**(Mac에서는 **Cmd+P**)를 눌러 **Quick Open**을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="09e3d-126">Launch **Quick Open** by pressing **Ctrl+P** (**Cmd+P** on Mac).</span></span>
- <span data-ttu-id="09e3d-127">Quick Open에서 `ext install powershell`을 입력하고 **Enter** 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="09e3d-127">In Quick Open, type `ext install powershell` and hit **Enter**.</span></span>
- <span data-ttu-id="09e3d-128">사이드바에 **확장** 보기가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="09e3d-128">The **Extensions** view opens on the Side Bar.</span></span> <span data-ttu-id="09e3d-129">Microsoft의 PowerShell 확장을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="09e3d-129">Select the PowerShell extension from Microsoft.</span></span>
  <span data-ttu-id="09e3d-130">아래와 비슷한 결과가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="09e3d-130">You should see something like below:</span></span>

  ![VSCode](../../images/vscode.png)

- <span data-ttu-id="09e3d-132">Microsoft의 PowerShell 확장에서 **설치** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="09e3d-132">Click the **Install** button on the PowerShell extension from Microsoft.</span></span>
- <span data-ttu-id="09e3d-133">설치 후 **설치** 단추가 **다시 로드**로 바뀌는 것을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="09e3d-133">After the install, you see the **Install** button turns to **Reload**.</span></span>
  <span data-ttu-id="09e3d-134">**다시 로드**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="09e3d-134">Click on **Reload**.</span></span>
- <span data-ttu-id="09e3d-135">Visual Studio Code가 다시 로드되면 편집할 준비가 된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="09e3d-135">After Visual Studio Code has reload, you are ready for editing.</span></span>

<span data-ttu-id="09e3d-136">예를 들어 새 파일을 만들려면 **파일->새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="09e3d-136">For example, to create a new file, click **File->New**.</span></span>
<span data-ttu-id="09e3d-137">저장하려면 **파일->저장**을 클릭한 후 파일 이름을 지정합니다(예: `HelloWorld.ps1`).</span><span class="sxs-lookup"><span data-stu-id="09e3d-137">To save it, click **File->Save** and then provide a file name, let's say `HelloWorld.ps1`.</span></span>
<span data-ttu-id="09e3d-138">파일을 닫으려면 파일 이름 옆에 있는 "x"를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="09e3d-138">To close the file, click on "x" next to the file name.</span></span>
<span data-ttu-id="09e3d-139">Visual Studio Code를 종료하려면 **파일->종료**를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="09e3d-139">To exit Visual Studio Code, **File->Exit**.</span></span>

### <a name="installing-the-powershell-extension-on-restricted-systems"></a><span data-ttu-id="09e3d-140">제한 된 시스템에 PowerShell 확장 설치</span><span class="sxs-lookup"><span data-stu-id="09e3d-140">Installing the PowerShell Extension on Restricted Systems</span></span>

<span data-ttu-id="09e3d-141">일부 시스템 검사할 모든 코드 서명 해야 하 고 PowerShell 편집기 서비스를 시스템에서 실행을 수동으로 승인 해야 하는 방식으로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="09e3d-141">Some systems are set up in a way that requires all code signatures to be checked and thus requires PowerShell Editor Services to be manually approved to run on the system.</span></span>
<span data-ttu-id="09e3d-142">실행 정책을 변경 하는 그룹 정책 업데이트 때문일 경우 PowerShell 확장을 설치 했지만 같은 오류에 도달 합니다.</span><span class="sxs-lookup"><span data-stu-id="09e3d-142">A Group Policy update that changes execution policy is a likely cause if you have installed the PowerShell extension but are reaching an error like:</span></span>

```
Language server startup failed.
```

<span data-ttu-id="09e3d-143">PowerShell 편집기 서비스 이므로 VSCode 용 PowerShell 확장을 수동으로 승인 하려면 프롬프트 및 실행 하는 PowerShell을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="09e3d-143">To manually approve PowerShell Editor Services and thus the PowerShell extension for VSCode open a PowerShell prompt and run:</span></span>

```powershell
Import-Module $HOME\.vscode\extensions\ms-vscode.powershell*\modules\PowerShellEditorServices\PowerShellEditorServices.psd1
```

<span data-ttu-id="09e3d-144">"이 신뢰할 수 없는 게시자의 소프트웨어를 실행 하 시겠습니까?" 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="09e3d-144">You are prompted with "Do you want to run software from this untrusted publisher?"</span></span>
<span data-ttu-id="09e3d-145">형식 `R` 파일을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="09e3d-145">Type `R` to run the file.</span></span> <span data-ttu-id="09e3d-146">그런 다음 Visual Studio Code를 열고 PowerShell 확장이 제대로 작동 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="09e3d-146">Then, open Visual Studio Code and check that the PowerShell extension is functioning properly.</span></span> <span data-ttu-id="09e3d-147">시작 하는 문제가 여전히 있는 경우에 알려 주세요 [GitHub](https://github.com/PowerShell/vscode-powershell/issues)합니다.</span><span class="sxs-lookup"><span data-stu-id="09e3d-147">If you still have issues getting started, let us know on [GitHub](https://github.com/PowerShell/vscode-powershell/issues).</span></span>

#### <a name="using-a-specific-installed-version-of-powershell"></a><span data-ttu-id="09e3d-148">설치된 특정 버전의 PowerShell 사용</span><span class="sxs-lookup"><span data-stu-id="09e3d-148">Using a specific installed version of PowerShell</span></span>

<span data-ttu-id="09e3d-149">Visual Studio Code에 설치된 특정 버전의 PowerShell을 사용하려면 사용자 설정 파일에 새로운 변수를 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="09e3d-149">If you wish to use a specific installation of PowerShell with Visual Studio Code, you need to add a new variable to your user settings file.</span></span>

1. <span data-ttu-id="09e3d-150">**파일 -> 기본 설정 -> 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="09e3d-150">Click **File -> Preferences -> Settings**</span></span>
1. <span data-ttu-id="09e3d-151">두 개의 편집기 창이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="09e3d-151">Two editor panes appear.</span></span>
   <span data-ttu-id="09e3d-152">맨 오른쪽 창(`settings.json`)에서 두 개의 중괄호(`{` 및 `}`) 사이에 아래에서 사용 중인 OS에 해당하는 설정을 삽입하고 **\<버전\>** 을 설치된 PowerShell 버전으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="09e3d-152">In the right-most pane (`settings.json`), insert the setting below appropriate for your OS somewhere between the two curly brackets (`{` and `}`) and replace **\<version\>** with the installed PowerShell version:</span></span>

   ```json
    // On Windows:
    "powershell.powerShellExePath": "c:/Program Files/PowerShell/<version>/pwsh.exe"

    // On Linux:
    "powershell.powerShellExePath": "/opt/microsoft/powershell/<version>/pwsh"

    // On macOS:
    "powershell.powerShellExePath": "/usr/local/microsoft/powershell/<version>/pwsh"
   ```

1. <span data-ttu-id="09e3d-153">설정을 원하는 PowerShell 실행 파일에 대한 경로로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="09e3d-153">Replace the setting with the path to the desired PowerShell executable</span></span>
1. <span data-ttu-id="09e3d-154">설정 파일을 저장하고 Visual Studio Code를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="09e3d-154">Save the settings file and restart Visual Studio Code</span></span>

#### <a name="configuration-settings-for-visual-studio-code"></a><span data-ttu-id="09e3d-155">Visual Studio Code에 대한 구성 파일</span><span class="sxs-lookup"><span data-stu-id="09e3d-155">Configuration settings for Visual Studio Code</span></span>

<span data-ttu-id="09e3d-156">이전 단락의 단계를 따라 `settings.json`에 구성 설정을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="09e3d-156">By using the steps in the previous paragraph you can add configuration settings in `settings.json`.</span></span>

<span data-ttu-id="09e3d-157">Visual Studio Code에는 다음 구성 설정을 권장합니다.</span><span class="sxs-lookup"><span data-stu-id="09e3d-157">We recommend the following configuration settings for Visual Studio Code:</span></span>

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

<span data-ttu-id="09e3d-158">모든 파일 형식에 영향을 하기 위해 이러한 설정을 사용 하지 않으려는 경우 VSCode 언어별 구성을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="09e3d-158">If you don't want these settings to affect all files types, VSCode also allows per-language configurations.</span></span> <span data-ttu-id="09e3d-159">설정에 배치 하 여 특정 언어 설정이 만들기를 `[<language-name>]` 필드입니다.</span><span class="sxs-lookup"><span data-stu-id="09e3d-159">Create a language specific setting by putting settings in a `[<language-name>]` field.</span></span> <span data-ttu-id="09e3d-160">예:</span><span class="sxs-lookup"><span data-stu-id="09e3d-160">For example:</span></span>

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

<span data-ttu-id="09e3d-161">파일에 대 한 자세한 내용은 참조 VS Code에서 인코딩을 [파일 인코딩 이해](understanding-file-encoding.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="09e3d-161">For more information about file encoding in VS Code, see [Understanding file encoding](understanding-file-encoding.md).</span></span>

## <a name="debugging-with-visual-studio-code"></a><span data-ttu-id="09e3d-162">Visual Studio Code 디버깅</span><span class="sxs-lookup"><span data-stu-id="09e3d-162">Debugging with Visual Studio Code</span></span>

### <a name="no-workspace-debugging"></a><span data-ttu-id="09e3d-163">작업 공간 없이 디버깅</span><span class="sxs-lookup"><span data-stu-id="09e3d-163">No-workspace debugging</span></span>

<span data-ttu-id="09e3d-164">Visual Studio Code 버전 1.9부터 PowerShell 스크립트가 포함된 폴더를 열지 않고도 PowerShell 스크립트를 디버깅할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="09e3d-164">As of Visual Studio Code version 1.9 you can debug PowerShell scripts without having to open the folder containing the PowerShell script.</span></span> <span data-ttu-id="09e3d-165">PowerShell 스크립트 파일을 엽니다 **파일에는 열려 있는 파일->...** ((f9 키 누름) 줄에 중단점을 설정 하 고 다음 f5 키를 눌러 디버깅을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="09e3d-165">Open the PowerShell script file with **File->Open File...**, set a breakpoint on a line (press F9) and then press F5 to start debugging.</span></span> <span data-ttu-id="09e3d-166">디버거, 단계, 디버깅 다시 시작 및 중지로 나눌 수 있는 디버그 작업 창이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="09e3d-166">You should see the Debug actions pane appear which allows you to break into the debugger, step, resume and stop debugging.</span></span>

### <a name="workspace-debugging"></a><span data-ttu-id="09e3d-167">작업 영역에서 디버깅</span><span class="sxs-lookup"><span data-stu-id="09e3d-167">Workspace debugging</span></span>

<span data-ttu-id="09e3d-168">작업 영역에서 디버깅은 Visual Studio Code의 **파일** 메뉴에서 **폴더 열기...** 를 사용하여 연 폴더의 컨텍스트에서 디버깅하는 것을 말합니다.</span><span class="sxs-lookup"><span data-stu-id="09e3d-168">Workspace debugging refers to debugging in the context of a folder that you have opened in Visual Studio Code using **Open Folder...** from the **File** menu.</span></span>
<span data-ttu-id="09e3d-169">사용자가 여는 폴더는 일반적으로 PowerShell 프로젝트 폴더 및/또는 Git 리포지토리의 루트입니다.</span><span class="sxs-lookup"><span data-stu-id="09e3d-169">The folder you open is typically your PowerShell project folder and/or the root of your Git repository.</span></span>

<span data-ttu-id="09e3d-170">이 모드에서도 간단히 F5 키만 눌러 현재 선택된 PowerShell 스크립트의 디버깅을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="09e3d-170">Even in this mode, you can start debugging the currently selected PowerShell script by simply pressing F5.</span></span>
<span data-ttu-id="09e3d-171">그러나 작업 영역에서 디버깅을 사용하면 현재 열려 있는 파일만 디버깅하는 것이 아니라 여러 디버그 구성도 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="09e3d-171">However, workspace debugging allows you to define multiple debug configurations other than just debugging the currently open file.</span></span>
<span data-ttu-id="09e3d-172">예를 들어 다음을 위한 구성을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="09e3d-172">For instance, you can add a configurations to:</span></span>

- <span data-ttu-id="09e3d-173">디버거에서 Pester 테스트 시작</span><span class="sxs-lookup"><span data-stu-id="09e3d-173">Launch Pester tests in the debugger</span></span>
- <span data-ttu-id="09e3d-174">디버거에서 인수를 갖는 특정 파일 시작</span><span class="sxs-lookup"><span data-stu-id="09e3d-174">Launch a specific file with arguments in the debugger</span></span>
- <span data-ttu-id="09e3d-175">디버거에서 대화형 세션 시작</span><span class="sxs-lookup"><span data-stu-id="09e3d-175">Launch an interactive session in the debugger</span></span>
- <span data-ttu-id="09e3d-176">PowerShell 호스트 프로세스에 디버거 연결</span><span class="sxs-lookup"><span data-stu-id="09e3d-176">Attach the debugger to a PowerShell host process</span></span>

<span data-ttu-id="09e3d-177">디버그 구성 파일을 만들려면 다음 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="09e3d-177">Follow these steps to create your debug configuration file:</span></span>

  1. <span data-ttu-id="09e3d-178">**Ctrl+Shift+D**(Mac에서는 **Cmd+Shift+D**)를 눌러 **디버그** 보기를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="09e3d-178">Open the **Debug** view by pressing **Ctrl+Shift+D** (**Cmd+Shift+D** on Mac).</span></span>
  2. <span data-ttu-id="09e3d-179">도구 모음에서 **구성** 기어 아이콘을 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="09e3d-179">Press the **Configure** gear icon in the toolbar.</span></span>
  3. <span data-ttu-id="09e3d-180">Visual Studio Code에서 **환경 선택**에 대한 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="09e3d-180">Visual Studio Code prompts you to **Select Environment**.</span></span> <span data-ttu-id="09e3d-181">**PowerShell**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="09e3d-181">Choose **PowerShell**.</span></span>

  <span data-ttu-id="09e3d-182">그러면 Visual Studio Code에서 작업 영역 폴더의 루트에 ".vscode\launch.json"이라는 파일과 디렉터리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="09e3d-182">When you do this, Visual Studio Code creates a directory and a file ".vscode\launch.json" in the root of your workspace folder.</span></span>
  <span data-ttu-id="09e3d-183">여기에 디버그 구성이 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="09e3d-183">This is where your debug configuration is stored.</span></span> <span data-ttu-id="09e3d-184">파일이 Git 리포지토리에 있을 경우 일반적으로 launch.json 파일을 커밋하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="09e3d-184">If your files are in a Git repository, you typically want to commit the launch.json file.</span></span>
  <span data-ttu-id="09e3d-185">launch.json 파일의 내용은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="09e3d-185">The contents of the launch.json file are:</span></span>

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

  <span data-ttu-id="09e3d-186">이는 일반적인 디버그 시나리오를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="09e3d-186">This represents the common debug scenarios.</span></span>
  <span data-ttu-id="09e3d-187">그러나 편집기에서 이 파일을 열면 **구성 추가...** 단추가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="09e3d-187">However, when you open this file in the editor, you see an **Add Configuration...** button.</span></span>
  <span data-ttu-id="09e3d-188">이 단추를 눌러 더 많은 PowerShell 디버그 구성을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="09e3d-188">You can press this button to add more PowerShell debug configurations.</span></span> <span data-ttu-id="09e3d-189">한 가지 간편한 구성은 **PowerShell: 스크립트 시작**입니다.</span><span class="sxs-lookup"><span data-stu-id="09e3d-189">One handy configuration to add is **PowerShell: Launch Script**.</span></span>
  <span data-ttu-id="09e3d-190">이 구성을 사용하면 편집기에서 현재 어떤 파일이 활성화되어 있는지 관계없이 F5 키를 누를 때마다 시작되어야 하는 선택적 인수를 갖는 특정 파일을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="09e3d-190">With this configuration, you can specify a specific file with optional arguments that should be launched whenever you press F5 no matter which file is currently active in the editor.</span></span>

  <span data-ttu-id="09e3d-191">디버그 구성이 설정되면 **디버그** 보기의 도구 모음에 있는 디버그 구성 드롭다운에서 항목을 선택하여 디버그 세션 중에 사용할 구성을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="09e3d-191">Once the debug configuration is established, you can select which configuration you want to use during a debug session by selecting one from the debug configuration drop-down in the **Debug** view's toolbar.</span></span>

<span data-ttu-id="09e3d-192">Visual Studio Code에 대한 PowerShell 확장 사용을 시작하는 데 도움이 되는 몇 가지 블로그가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="09e3d-192">There are a few blogs that may be helpful to get you started using PowerShell extension for Visual Studio Code:</span></span>

- <span data-ttu-id="09e3d-193">[PowerShell 확장][ps-extension]</span><span class="sxs-lookup"><span data-stu-id="09e3d-193">[PowerShell Extension][ps-extension]</span></span>
- <span data-ttu-id="09e3d-194">[Visual Studio Code에서 PowerShell 스크립트 작성 및 디버깅][debug]</span><span class="sxs-lookup"><span data-stu-id="09e3d-194">[Write and debug PowerShell scripts in Visual Studio Code][debug]</span></span>
- <span data-ttu-id="09e3d-195">[Visual Studio Code 디버깅 지침][vscode-guide]</span><span class="sxs-lookup"><span data-stu-id="09e3d-195">[Debugging Visual Studio Code Guidance][vscode-guide]</span></span>
- <span data-ttu-id="09e3d-196">[Visual Studio Code에서 PowerShell 디버깅][ps-vscode]</span><span class="sxs-lookup"><span data-stu-id="09e3d-196">[Debugging PowerShell in Visual Studio Code][ps-vscode]</span></span>
- <span data-ttu-id="09e3d-197">[Visual Studio Code에서 PowerShell 개발 시작][getting-started]</span><span class="sxs-lookup"><span data-stu-id="09e3d-197">[Get started with PowerShell development in Visual Studio Code][getting-started]</span></span>
- <span data-ttu-id="09e3d-198">[PowerShell 개발을 위한 Visual Studio Code 편집 기능 – 1부][editing-part1]</span><span class="sxs-lookup"><span data-stu-id="09e3d-198">[Visual Studio Code editing features for PowerShell development – Part 1][editing-part1]</span></span>
- <span data-ttu-id="09e3d-199">[PowerShell 개발을 위한 Visual Studio Code 편집 기능 – 2부][editing-part2]</span><span class="sxs-lookup"><span data-stu-id="09e3d-199">[Visual Studio Code editing features for PowerShell development – Part 2][editing-part2]</span></span>
- <span data-ttu-id="09e3d-200">[Visual Studio Code에서 PowerShell 스크립트 디버깅 – 1부][debugging-part1]</span><span class="sxs-lookup"><span data-stu-id="09e3d-200">[Debugging PowerShell script in Visual Studio Code – Part 1][debugging-part1]</span></span>
- <span data-ttu-id="09e3d-201">[Visual Studio Code에서 PowerShell 스크립트 디버깅 – 2부][debugging-part2]</span><span class="sxs-lookup"><span data-stu-id="09e3d-201">[Debugging PowerShell script in Visual Studio Code – Part 2][debugging-part2]</span></span>

[ise]: ../ise/Introducing-the-Windows-PowerShell-ISE.md
[install-pscore-linux]:  ../../setup/Installing-PowerShell-Core-on-Linux.md
[install-pscore-macos]:  ../../setup/Installing-PowerShell-Core-on-macOS.md
[install-pscore-windows]: ../../setup/Installing-PowerShell-Core-on-Windows.md
[install-winps]: ../../setup/Installing-Windows-PowerShell.md
[ps-extension]: https://blogs.msdn.microsoft.com/cdndevs/2015/12/11/visual-studio-code-powershell-extension/
[debug]: https://blogs.msdn.microsoft.com/powershell/2015/11/16/announcing-powershell-language-support-for-visual-studio-code-and-more/
[vscode-guide]: https://johnpapa.net/debugging-with-visual-studio-code/
[ps-vscode]: https://github.com/PowerShell/vscode-powershell/tree/master/examples
[getting-started]: https://blogs.technet.microsoft.com/heyscriptingguy/2016/12/05/get-started-with-powershell-development-in-visual-studio-code/
[editing-part1]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/01/11/visual-studio-code-editing-features-for-powershell-development-part-1/
[editing-part2]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/01/12/visual-studio-code-editing-features-for-powershell-development-part-2/
[debugging-part1]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/02/06/debugging-powershell-script-in-visual-studio-code-part-1/
[debugging-part2]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/02/13/debugging-powershell-script-in-visual-studio-code-part-2/

## <a name="powershell-extension-for-visual-studio-code"></a><span data-ttu-id="09e3d-202">Visual Studio Code용 PowerShell 확장</span><span class="sxs-lookup"><span data-stu-id="09e3d-202">PowerShell Extension for Visual Studio Code</span></span>

<span data-ttu-id="09e3d-203">PowerShell 확장의 소스 코드는 [GitHub](https://github.com/PowerShell/vscode-powershell)에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="09e3d-203">The PowerShell extension's source code can be found on [GitHub](https://github.com/PowerShell/vscode-powershell).</span></span>
