---
title: Visual Studio Code에서 ISE 환경을 복제하는 방법
description: Visual Studio Code에서 ISE 환경을 복제하는 방법
ms.date: 08/06/2018
ms.openlocfilehash: 899e1c393fd49b0659631b88d610e80ec885e69e
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/23/2020
ms.locfileid: "83809599"
---
# <a name="how-to-replicate-the-ise-experience-in-visual-studio-code"></a><span data-ttu-id="b8469-103">Visual Studio Code에서 ISE 환경을 복제하는 방법</span><span class="sxs-lookup"><span data-stu-id="b8469-103">How to replicate the ISE experience in Visual Studio Code</span></span>

<span data-ttu-id="b8469-104">VS Code용 PowerShell 확장 PowerShell ISE와 완전히 동일한 기능을 제공하지는 않지만, ISE 사용자를 위해 VS Code 환경을 더 자연스럽게 만드는 대체 기능이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8469-104">While the PowerShell extension for VS Code doesn't seek complete feature parity with the PowerShell ISE, there are features in place to make the VS Code experience more natural for users of the ISE.</span></span>

<span data-ttu-id="b8469-105">이 문서에는 사용자 환경을 ISE보다는 조금 더 친숙하게 만들도록 VS Code에서 구성할 수 있는 설정이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8469-105">This document tries to list settings you can configure in VS Code to make the user experience a bit more familiar compared to the ISE.</span></span>

## <a name="ise-mode"></a><span data-ttu-id="b8469-106">ISE 모드</span><span class="sxs-lookup"><span data-stu-id="b8469-106">ISE Mode</span></span>

> [!NOTE]
> <span data-ttu-id="b8469-107">이 기능은 버전 2019.12.0 이후 PowerShell 미리 보기 확장과 버전 2020.3.0 이후 PowerShell 확장에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8469-107">This feature is available in the PowerShell Preview extension since version 2019.12.0 and in the PowerShell extension since version 2020.3.0.</span></span>

<span data-ttu-id="b8469-108">Visual Studio Code에서 ISE 환경을 복제하는 가장 쉬운 방법은 "ISE 모드"를 설정하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="b8469-108">The easiest way to replicate the ISE experience in Visual Studio Code is by turning on "ISE Mode".</span></span>
<span data-ttu-id="b8469-109">이 작업을 수행하려면 명령 팔레트(<kbd>F1</kbd> 또는 <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> 또는 macOS에서 <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>)를 열고 "ISE 모드"를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b8469-109">To do this, open the command palette (<kbd>F1</kbd> OR <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> OR <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on macOS) and type in "ISE Mode".</span></span> <span data-ttu-id="b8469-110">목록에서 "PowerShell: ISE 모드 사용"을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b8469-110">Select "PowerShell: Enable ISE Mode" from the list.</span></span>

<span data-ttu-id="b8469-111">이 명령은 아래에 설명된 설정을 자동으로 적용합니다. 결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b8469-111">This command automatically applies the settings described below The result looks like this:</span></span>

![ISE 모드](media/How-To-Replicate-the-ISE-Experience-In-VSCode/3-ise-mode.png)

## <a name="ise-mode-configuration-settings"></a><span data-ttu-id="b8469-113">ISE 모드 구성 설정</span><span class="sxs-lookup"><span data-stu-id="b8469-113">ISE Mode configuration settings</span></span>

<span data-ttu-id="b8469-114">ISE 모드를 사용하면 VS Code 설정이 다음과 같이 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8469-114">ISE Mode makes the following changes to VS Code settings.</span></span>

- <span data-ttu-id="b8469-115">키 바인딩</span><span class="sxs-lookup"><span data-stu-id="b8469-115">Key bindings</span></span>

  |               <span data-ttu-id="b8469-116">함수</span><span class="sxs-lookup"><span data-stu-id="b8469-116">Function</span></span>                |         <span data-ttu-id="b8469-117">ISE 바인딩</span><span class="sxs-lookup"><span data-stu-id="b8469-117">ISE Binding</span></span>          |              <span data-ttu-id="b8469-118">VS Code 바인딩</span><span class="sxs-lookup"><span data-stu-id="b8469-118">VS Code Binding</span></span>                |
  | ------------------------------------- | ---------------------------- | ------------------------------------------- |
  | <span data-ttu-id="b8469-119">디버거 중단</span><span class="sxs-lookup"><span data-stu-id="b8469-119">Interrupt and break debugger</span></span>          | <span data-ttu-id="b8469-120"><kbd>Ctrl</kbd>+<kbd>B</kbd></span><span class="sxs-lookup"><span data-stu-id="b8469-120"><kbd>Ctrl</kbd>+<kbd>B</kbd></span></span> | <span data-ttu-id="b8469-121"><kbd>F6</kbd></span><span class="sxs-lookup"><span data-stu-id="b8469-121"><kbd>F6</kbd></span></span>                               |
  | <span data-ttu-id="b8469-122">현재 줄/강조 표시된 텍스트 실행</span><span class="sxs-lookup"><span data-stu-id="b8469-122">Execute current line/highlighted text</span></span> | <span data-ttu-id="b8469-123"><kbd>F8</kbd></span><span class="sxs-lookup"><span data-stu-id="b8469-123"><kbd>F8</kbd></span></span>                | <span data-ttu-id="b8469-124"><kbd>F8</kbd></span><span class="sxs-lookup"><span data-stu-id="b8469-124"><kbd>F8</kbd></span></span>                               |
  | <span data-ttu-id="b8469-125">사용 가능한 코드 조각 나열</span><span class="sxs-lookup"><span data-stu-id="b8469-125">List available snippets</span></span>               | <span data-ttu-id="b8469-126"><kbd>Ctrl</kbd>+<kbd>J</kbd></span><span class="sxs-lookup"><span data-stu-id="b8469-126"><kbd>Ctrl</kbd>+<kbd>J</kbd></span></span> | <span data-ttu-id="b8469-127"><kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd></span><span class="sxs-lookup"><span data-stu-id="b8469-127"><kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd></span></span> |

  > [!NOTE]
  > <span data-ttu-id="b8469-128">VS Code에서도 [고유한 키 바인딩을 구성](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings)할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8469-128">You can [configure your own key bindings](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) in VS Code as well.</span></span>

- <span data-ttu-id="b8469-129">간소화된 ISE와 유사한 UI</span><span class="sxs-lookup"><span data-stu-id="b8469-129">Simplified ISE-like UI</span></span>

  <span data-ttu-id="b8469-130">Visual Studio Code UI를 간소화하여 ISE의 UI를 보다 자세히 살펴보려면 다음 두 가지 설정을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="b8469-130">If you're looking to simplify the Visual Studio Code UI to look more closely to the UI of the ISE, apply these two settings:</span></span>

  ```json
  "workbench.activityBar.visible": false,
  "debug.openDebug": "neverOpen",
  ```

  <span data-ttu-id="b8469-131">이러한 설정은 빨간색 상자 내부 아래에 있는 "작업 표시줄" 및 "디버그 사이드 막대" 섹션을 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="b8469-131">These settings hide the "Activity Bar" and the "Debug Side Bar" sections shown inside the red box below:</span></span>

  ![강조 표시된 섹션에는 작업 표시줄과 디버그 사이드 막대가 포함됩니다.](media/How-To-Replicate-the-ISE-Experience-In-VSCode/1-highlighted-sidebar.png)

  <span data-ttu-id="b8469-133">최종 결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b8469-133">The end result looks like this:</span></span>

  ![VS Code의 단순화된 보기](media/How-To-Replicate-the-ISE-Experience-In-VSCode/2-simplified-ui.png)

- <span data-ttu-id="b8469-135">탭 완성</span><span class="sxs-lookup"><span data-stu-id="b8469-135">Tab completion</span></span>

  <span data-ttu-id="b8469-136">더 ISE와 유사한 탭 완성을 사용하려면 이 설정을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="b8469-136">To enable more ISE-like tab completion, add this setting:</span></span>

  ```json
  "editor.tabCompletion": "on",
  ```

- <span data-ttu-id="b8469-137">실행 시 콘솔에 포커스 없음</span><span class="sxs-lookup"><span data-stu-id="b8469-137">No focus on console when executing</span></span>

  <span data-ttu-id="b8469-138"><kbd>F8</kbd>로 실행할 때 편집기에서 포커스를 유지하려면</span><span class="sxs-lookup"><span data-stu-id="b8469-138">To keep the focus in the editor when you execute with <kbd>F8</kbd>:</span></span>

  ```json
  "powershell.integratedConsole.focusConsoleOnExecute": false
  ```

  <span data-ttu-id="b8469-139">기본값은 액세스 가능성을 위해 `true`가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8469-139">The default is `true` for accessibility purposes.</span></span>

- <span data-ttu-id="b8469-140">시작 시 통합 콘솔을 시작하지 않음</span><span class="sxs-lookup"><span data-stu-id="b8469-140">Don't start integrated console on startup</span></span>

  <span data-ttu-id="b8469-141">시작 시 통합 콘솔을 중지하려면 다음을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="b8469-141">To stop the integrated console on startup, set:</span></span>

  ```json
  "powershell.integratedConsole.showOnStartup": false
  ```

  > [!NOTE]
  > <span data-ttu-id="b8469-142">백그라운드 PowerShell 프로세스는 IntelliSense, 스크립트 분석, 기호 탐색 등을 계속 제공하지만 콘솔은 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b8469-142">The background PowerShell process still starts to provide IntelliSense, script analysis, symbol navigation, etc., but the console won't be shown.</span></span>

- <span data-ttu-id="b8469-143">파일이 기본적으로 PowerShell이라고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="b8469-143">Assume files are PowerShell by default</span></span>

  <span data-ttu-id="b8469-144">새/제목 없는 파일을 만들려면 기본적으로 PowerShell로 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="b8469-144">To make new/untitled files, register as PowerShell by default:</span></span>

  ```json
  "files.defaultLanguage": "powershell",
  ```

- <span data-ttu-id="b8469-145">색 구성표</span><span class="sxs-lookup"><span data-stu-id="b8469-145">Color scheme</span></span>

  <span data-ttu-id="b8469-146">VS Code에서 편집기 모양을 ISE와 훨씬 더 비슷하게 설정하는 데 사용할 수 있는 다양한 ISE 테마가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8469-146">There are a number of ISE themes available for VS Code to make the editor look much more like the ISE.</span></span>

  <span data-ttu-id="b8469-147">[명령 팔레트][]에 `theme`를 입력하여 `Preferences: Color Theme`를 가져오고 <kbd>Enter</kbd> 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="b8469-147">In the [Command Palette][] type `theme` to get `Preferences: Color Theme` and press <kbd>Enter</kbd>.</span></span> <span data-ttu-id="b8469-148">드롭다운 목록에서 `PowerShell ISE`를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b8469-148">In the drop-down list, select `PowerShell ISE`.</span></span>

  <span data-ttu-id="b8469-149">다음을 사용하여 설정에서 이 테마를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8469-149">You can set this theme in the settings with:</span></span>

  ```json
  "workbench.colorTheme": "PowerShell ISE",
  ```

- <span data-ttu-id="b8469-150">PowerShell Command Explorer</span><span class="sxs-lookup"><span data-stu-id="b8469-150">PowerShell Command Explorer</span></span>

  <span data-ttu-id="b8469-151">[@corbob](https://github.com/corbob)의 작업 덕분에 PowerShell 확장에는 고유한 초기 명령 탐색기가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8469-151">Thanks to the work of [@corbob](https://github.com/corbob), the PowerShell extension has the beginnings of its own command explorer.</span></span>

  <span data-ttu-id="b8469-152">[명령 팔레트][]에 `PowerShell Command Explorer`를 입력하고 <kbd>Enter</kbd> 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="b8469-152">In the [Command Palette][], enter `PowerShell Command Explorer` and press <kbd>Enter</kbd>.</span></span>

- <span data-ttu-id="b8469-153">ISE에서 열기</span><span class="sxs-lookup"><span data-stu-id="b8469-153">Open in the ISE</span></span>

  <span data-ttu-id="b8469-154">그래도 Windows PowerShell ISE에서 파일을 열려면 [명령 팔레트][]를 열고 "open in ise"를 검색한 다음 **PowerShell을 선택합니다. PowerShell ISE**에서 현재 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="b8469-154">If you want to open a file in the Windows PowerShell ISE anyway, open the [Command Palette][], search for "open in ise", then select **PowerShell: Open Current File in PowerShell ISE**.</span></span>

## <a name="other-resources"></a><span data-ttu-id="b8469-155">기타 리소스</span><span class="sxs-lookup"><span data-stu-id="b8469-155">Other resources</span></span>

- <span data-ttu-id="b8469-156">4sysops에는 VS Code를 ISE와 더 유사하게 구성하는 방법에 대한 [유용한 문서][4sysops]가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8469-156">4sysops has [a great article][4sysops] on configuring VS Code to be more like the ISE.</span></span>
- <span data-ttu-id="b8469-157">Mike F Robbins는 VS Code 설정에 대한 [유용한 게시물][mikefrobbins]을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b8469-157">Mike F Robbins has [a great post][mikefrobbins] on setting up VS Code.</span></span>
- <span data-ttu-id="b8469-158">PowerShell에 있는 PowerShell 설정에 대한 [유용한 문서][learnpwsh]를 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="b8469-158">Learn PowerShell has [an excellent write up][learnpwsh] setup for PowerShell.</span></span>

## <a name="vs-code-tips"></a><span data-ttu-id="b8469-159">VS Code 팁</span><span class="sxs-lookup"><span data-stu-id="b8469-159">VS Code Tips</span></span>

- <span data-ttu-id="b8469-160">명령 팔레트</span><span class="sxs-lookup"><span data-stu-id="b8469-160">Command Palette</span></span>

  <span data-ttu-id="b8469-161">명령 팔레트는 VS Code에서 명령을 실행할 수 있는 편리한 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="b8469-161">The Command Palette is handy way of executing commands in VS Code.</span></span> <span data-ttu-id="b8469-162">macOS에서 <kbd>F1</kbd> 또는 <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> 또는 <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>를 사용하여 명령 팔레트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="b8469-162">Open the command palette using <kbd>F1</kbd> OR <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> OR <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on macOS.</span></span>

  <span data-ttu-id="b8469-163">자세한 내용은 [VS Code 설명서][vsc-docs]를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b8469-163">For more information, see [the VS Code documentation][vsc-docs].</span></span>

- <span data-ttu-id="b8469-164">디버그 콘솔 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="b8469-164">Disable the Debug Console</span></span>

  <span data-ttu-id="b8469-165">PowerShell 스크립팅에 VS Code만 사용하도록 계획한 경우 PowerShell 확장에서 사용되지 않으므로 **디버그 콘솔**을 숨길 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8469-165">If you only plan on using VS Code for PowerShell scripting, you can hide the **Debug Console** since it is not used by the PowerShell extension.</span></span> <span data-ttu-id="b8469-166">이렇게 하려면 마우스 오른쪽 단추로 **디버그 콘솔**을 클릭한 다음 확인 표시를 클릭하여 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="b8469-166">To do so, right click on **Debug Console** then click on the check mark to hide it.</span></span>

## <a name="more-settings"></a><span data-ttu-id="b8469-167">추가 설정</span><span class="sxs-lookup"><span data-stu-id="b8469-167">More settings</span></span>

<span data-ttu-id="b8469-168">ISE 사용자가 더 친숙하게 느끼도록 VS Code를 설정하는 더 많은 방법을 알고 있다면 이 문서에 참여하세요. 찾고 있는 호환성 구성이 있지만 해당 구성을 사용하도록 설정하는 방법을 찾을 수 없으면 [문제를 열고][] 모든 궁금한 사항을 질문하세요.</span><span class="sxs-lookup"><span data-stu-id="b8469-168">If you know of more ways to make VS Code feel more familiar for ISE users, contribute to this doc. If there's a compatibility configuration you're looking for, but you can't find any way to enable it, [open an issue][] and ask away!</span></span>

<span data-ttu-id="b8469-169">PR 및 참여도 언제든지 환영합니다.</span><span class="sxs-lookup"><span data-stu-id="b8469-169">We're always happy to accept PRs and contributions as well!</span></span>

<!-- link references -->
[vsc-docs]: https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette
[명령 팔레트]: #vs-code-tips
[Command Palette]: #vs-code-tips
[문제를 열고]: https://github.com/PowerShell/VSCode-powershell/issues/new/choose
[open an issue]: https://github.com/PowerShell/VSCode-powershell/issues/new/choose

[4sysops]: https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/
[mikefrobbins]: https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/
[learnpwsh]: https://www.learnpwsh.com/setup-vs-code-for-powershell/
