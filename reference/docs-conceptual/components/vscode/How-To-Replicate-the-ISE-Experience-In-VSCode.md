---
title: Visual Studio Code에서 ISE 환경을 복제하는 방법
description: Visual Studio Code에서 ISE 환경을 복제하는 방법
ms.date: 08/06/2018
ms.openlocfilehash: 193243dc2e3e921b22a6ee068370200ae84ce4ac
ms.sourcegitcommit: 01c60c0c97542dbad48ae34339cddbd813f1353b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78279264"
---
# <a name="how-to-replicate-the-ise-experience-in-visual-studio-code"></a><span data-ttu-id="cc2cb-103">Visual Studio Code에서 ISE 환경을 복제하는 방법</span><span class="sxs-lookup"><span data-stu-id="cc2cb-103">How to replicate the ISE experience in Visual Studio Code</span></span>

<span data-ttu-id="cc2cb-104">VSCode용 PowerShell 확장 PowerShell ISE와 완전히 동일한 기능을 제공하지는 않지만, ISE 사용자를 위해 VSCode 환경을 더 자연스럽게 만드는 대체 기능이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc2cb-104">While the PowerShell extension for VSCode doesn't seek complete feature parity with the PowerShell ISE, there are features in place to make the VSCode experience more natural for users of the ISE.</span></span>

<span data-ttu-id="cc2cb-105">이 문서에는 사용자 환경을 ISE보다는 조금 더 친숙하게 만들도록 VSCode에서 구성할 수 있는 설정이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc2cb-105">This document tries to list settings you can configure in VSCode to make the user experience a bit more familiar compared to the ISE.</span></span>

## <a name="ise-mode"></a><span data-ttu-id="cc2cb-106">ISE 모드</span><span class="sxs-lookup"><span data-stu-id="cc2cb-106">ISE Mode</span></span>

> [!NOTE]
> <span data-ttu-id="cc2cb-107">이 기능은 버전 2019.12.0 이후 PowerShell 미리 보기 확장과 버전 2020.3.0 이후 PowerShell 확장에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc2cb-107">This feature is available in the PowerShell Preview extension since version 2019.12.0 and in the PowerShell extension since version 2020.3.0.</span></span>

<span data-ttu-id="cc2cb-108">Visual Studio Code에서 ISE 환경을 복제하는 가장 쉬운 방법은 "ISE 모드"를 설정하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="cc2cb-108">The easiest way to replicate the ISE experience in Visual Studio Code is by turning on "ISE Mode".</span></span>
<span data-ttu-id="cc2cb-109">이 작업을 수행하려면 명령 팔레트(<kbd>F1</kbd> 또는 <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> 또는 macOS에서 <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>)를 열고 "ISE 모드"를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="cc2cb-109">To do this, open the command pallet (<kbd>F1</kbd> OR <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> OR <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on macOS) and type in "ISE Mode".</span></span>
<span data-ttu-id="cc2cb-110">목록에서 "PowerShell: ISE 모드 사용"을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cc2cb-110">Select "PowerShell: Enable ISE Mode" from the list.</span></span>

<span data-ttu-id="cc2cb-111">이 명령은 이 문서에 있는 많은 설정을 자동으로 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="cc2cb-111">This command will apply a lot of the settings found in this document automatically.</span></span>
<span data-ttu-id="cc2cb-112">결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="cc2cb-112">The result looks like this:</span></span>

![ISE 모드](media/How-To-Replicate-the-ISE-Experience-In-VSCode/3-ise-mode.png)

<span data-ttu-id="cc2cb-114">이 문서의 나머지 부분에는 ISE 모드의 설정 및 몇 가지 추가 설정에 대한 자세한 정보가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc2cb-114">The rest of this article includes more detailed information on settings in ISE Mode and some additional settings.</span></span>

## <a name="key-bindings"></a><span data-ttu-id="cc2cb-115">키 바인딩</span><span class="sxs-lookup"><span data-stu-id="cc2cb-115">Key bindings</span></span>

| <span data-ttu-id="cc2cb-116">함수</span><span class="sxs-lookup"><span data-stu-id="cc2cb-116">Function</span></span>                              | <span data-ttu-id="cc2cb-117">ISE 바인딩</span><span class="sxs-lookup"><span data-stu-id="cc2cb-117">ISE Binding</span></span>                  | <span data-ttu-id="cc2cb-118">VSCode 바인딩</span><span class="sxs-lookup"><span data-stu-id="cc2cb-118">VSCode Binding</span></span>                              |
| ----------------                      | -----------                  | --------------                              |
| <span data-ttu-id="cc2cb-119">디버거 중단</span><span class="sxs-lookup"><span data-stu-id="cc2cb-119">Interrupt and break debugger</span></span>          | <span data-ttu-id="cc2cb-120"><kbd>Ctrl</kbd>+<kbd>B</kbd></span><span class="sxs-lookup"><span data-stu-id="cc2cb-120"><kbd>Ctrl</kbd>+<kbd>B</kbd></span></span> | <span data-ttu-id="cc2cb-121"><kbd>F6</kbd></span><span class="sxs-lookup"><span data-stu-id="cc2cb-121"><kbd>F6</kbd></span></span>                               |
| <span data-ttu-id="cc2cb-122">현재 줄/강조 표시된 텍스트 실행</span><span class="sxs-lookup"><span data-stu-id="cc2cb-122">Execute current line/highlighted text</span></span> | <span data-ttu-id="cc2cb-123"><kbd>F8</kbd></span><span class="sxs-lookup"><span data-stu-id="cc2cb-123"><kbd>F8</kbd></span></span>                | <span data-ttu-id="cc2cb-124"><kbd>F8</kbd></span><span class="sxs-lookup"><span data-stu-id="cc2cb-124"><kbd>F8</kbd></span></span>                               |
| <span data-ttu-id="cc2cb-125">사용 가능한 코드 조각 나열</span><span class="sxs-lookup"><span data-stu-id="cc2cb-125">List available snippets</span></span>               | <span data-ttu-id="cc2cb-126"><kbd>Ctrl</kbd>+<kbd>J</kbd></span><span class="sxs-lookup"><span data-stu-id="cc2cb-126"><kbd>Ctrl</kbd>+<kbd>J</kbd></span></span> | <span data-ttu-id="cc2cb-127"><kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd></span><span class="sxs-lookup"><span data-stu-id="cc2cb-127"><kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd></span></span> |

### <a name="custom-key-bindings"></a><span data-ttu-id="cc2cb-128">사용자 지정 키 바인딩</span><span class="sxs-lookup"><span data-stu-id="cc2cb-128">Custom Key bindings</span></span>

<span data-ttu-id="cc2cb-129">VSCode에서도 [고유한 키 바인딩을 구성](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings)할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc2cb-129">You can [configure your own key bindings](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) in VSCode as well.</span></span>

## <a name="simplified-ise-like-ui"></a><span data-ttu-id="cc2cb-130">간소화된 ISE와 유사한 UI</span><span class="sxs-lookup"><span data-stu-id="cc2cb-130">Simplified ISE-like UI</span></span>

<span data-ttu-id="cc2cb-131">Visual Studio Code UI를 간소화하여 ISE의 UI를 보다 자세히 살펴보려면 다음 두 가지 설정을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="cc2cb-131">If you're looking to simplify the Visual Studio Code UI to look more closely to the UI of the ISE, apply these two settings:</span></span>

```json
"workbench.activityBar.visible": false,
"debug.openDebug": "neverOpen",
```

> [!NOTE]
> <span data-ttu-id="cc2cb-132">이러한 설정은 ["ISE 모드"](#ise-mode)에 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc2cb-132">These settings are included in ["ISE Mode"](#ise-mode).</span></span>

<span data-ttu-id="cc2cb-133">이렇게 하면 빨간색 상자 내부 아래에 있는 "작업 표시줄" 및 "디버그 사이드 막대" 섹션이 숨겨집니다.</span><span class="sxs-lookup"><span data-stu-id="cc2cb-133">This will hide the "Activity Bar" and the "Debug Side Bar" sections below inside of the red box:</span></span>

![강조 표시된 섹션에는 작업 표시줄과 디버그 사이드 막대가 포함됩니다.](media/How-To-Replicate-the-ISE-Experience-In-VSCode/1-highlighted-sidebar.png)

<span data-ttu-id="cc2cb-135">최종 결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="cc2cb-135">The end result looks like this:</span></span>

![VS Code의 단순화된 보기](media/How-To-Replicate-the-ISE-Experience-In-VSCode/2-simplified-ui.png)

## <a name="tab-completion"></a><span data-ttu-id="cc2cb-137">탭 완성</span><span class="sxs-lookup"><span data-stu-id="cc2cb-137">Tab completion</span></span>

<span data-ttu-id="cc2cb-138">더 ISE와 유사한 탭 완성을 사용하려면 이 설정을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="cc2cb-138">To enable more ISE-like tab completion, add this setting:</span></span>

```json
"editor.tabCompletion": "on",
```

> [!NOTE]
> <span data-ttu-id="cc2cb-139">이 설정은 VSCode에 직접 추가되었습니다(확장으로 추가되지 않음).</span><span class="sxs-lookup"><span data-stu-id="cc2cb-139">This setting was added directly to VSCode (rather than in the extension).</span></span> <span data-ttu-id="cc2cb-140">해당 동작은 VSCode에 의해 직접 결정되며 확장에 의해 변경될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cc2cb-140">Its behavior is determined by VSCode directly and cannot be changed by the extension.</span></span>

> [!NOTE]
> <span data-ttu-id="cc2cb-141">이 설정은 ["ISE 모드"](#ise-mode)에 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc2cb-141">This setting is included in ["ISE Mode"](#ise-mode).</span></span>

## <a name="no-focus-on-console-when-executing"></a><span data-ttu-id="cc2cb-142">실행 시 콘솔에 포커스 없음</span><span class="sxs-lookup"><span data-stu-id="cc2cb-142">No focus on console when executing</span></span>

<span data-ttu-id="cc2cb-143"><kbd>F8</kbd>로 실행할 때 편집기에서 포커스를 유지하려면</span><span class="sxs-lookup"><span data-stu-id="cc2cb-143">To keep the focus in the editor when you execute with <kbd>F8</kbd>:</span></span>

```json
"powershell.integratedConsole.focusConsoleOnExecute": false
```

> [!NOTE]
> <span data-ttu-id="cc2cb-144">이 설정은 ["ISE 모드"](#ise-mode)에 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc2cb-144">This setting is included in ["ISE Mode"](#ise-mode).</span></span>

<span data-ttu-id="cc2cb-145">기본값은 액세스 가능성을 위해 `true`가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cc2cb-145">The default is `true` for accessibility purposes.</span></span>

## <a name="dont-start-integrated-console-on-startup"></a><span data-ttu-id="cc2cb-146">시작 시 통합 콘솔을 시작하지 않음</span><span class="sxs-lookup"><span data-stu-id="cc2cb-146">Don't start integrated console on startup</span></span>

<span data-ttu-id="cc2cb-147">시작 시 통합 콘솔을 중지하려면 다음을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="cc2cb-147">To stop the integrated console on startup, set:</span></span>

```json
"powershell.integratedConsole.showOnStartup": false
```

> [!NOTE]
> <span data-ttu-id="cc2cb-148">백그라운드 PowerShell 프로세스는 IntelliSense, 스크립트 분석, 기호 탐색 등을 제공하므로 계속 시작됩니다. 그러나 콘솔이 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cc2cb-148">The background PowerShell process will still start since that provides IntelliSense, script analysis, symbol navigation, etc. But the console won't be shown.</span></span>

## <a name="assume-files-are-powershell-by-default"></a><span data-ttu-id="cc2cb-149">파일이 기본적으로 PowerShell이라고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="cc2cb-149">Assume files are PowerShell by default</span></span>

<span data-ttu-id="cc2cb-150">새/제목 없는 파일을 만들려면 기본적으로 PowerShell로 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="cc2cb-150">To make new/untitled files, register as PowerShell by default:</span></span>

```json
"files.defaultLanguage": "powershell",
```

> [!NOTE]
> <span data-ttu-id="cc2cb-151">이 설정은 ["ISE 모드"](#ise-mode)에 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc2cb-151">This setting is included in ["ISE Mode"](#ise-mode).</span></span>

## <a name="color-scheme"></a><span data-ttu-id="cc2cb-152">색 구성표</span><span class="sxs-lookup"><span data-stu-id="cc2cb-152">Color scheme</span></span>

<span data-ttu-id="cc2cb-153">VSCode에서 편집기 모양을 ISE와 훨씬 더 비슷하게 설정하는 데 사용할 수 있는 다양한 ISE 테마가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc2cb-153">There are a number of ISE themes available for VSCode to make the editor look much more like the ISE.</span></span>

<span data-ttu-id="cc2cb-154">[명령 팔레트]에 `theme`를 입력하여 `Preferences: Color Theme`를 가져오고 <kbd>Enter</kbd> 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="cc2cb-154">In the [Command Palette] type `theme` to get `Preferences: Color Theme` and press <kbd>Enter</kbd>.</span></span>
<span data-ttu-id="cc2cb-155">드롭다운 목록에서 `PowerShell ISE`를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cc2cb-155">In the drop-down list, select `PowerShell ISE`.</span></span>

<span data-ttu-id="cc2cb-156">다음을 사용하여 설정에서 이 테마를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc2cb-156">You can set this theme in the settings with:</span></span>

```json
"workbench.colorTheme": "PowerShell ISE",
```

> [!NOTE]
> <span data-ttu-id="cc2cb-157">이 설정은 ["ISE 모드"](#ise-mode)에 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc2cb-157">This setting is included in ["ISE Mode"](#ise-mode).</span></span>

## <a name="powershell-command-explorer"></a><span data-ttu-id="cc2cb-158">PowerShell Command Explorer</span><span class="sxs-lookup"><span data-stu-id="cc2cb-158">PowerShell Command Explorer</span></span>

<span data-ttu-id="cc2cb-159">[@corbob](https://github.com/corbob)의 작업 덕분에 PowerShell 확장에는 고유한 초기 명령 탐색기가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc2cb-159">Thanks to the work of [@corbob](https://github.com/corbob), the PowerShell extension has the beginnings of its own command explorer.</span></span>

<span data-ttu-id="cc2cb-160">[명령 팔레트]에 `PowerShell Command Explorer`를 입력하고 <kbd>Enter</kbd> 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="cc2cb-160">In the [Command Palette], enter `PowerShell Command Explorer` and press <kbd>Enter</kbd>.</span></span>

> [!NOTE]
> <span data-ttu-id="cc2cb-161">["ISE 모드"](#ise-mode)에서는 자동으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="cc2cb-161">This is shown automatically in ["ISE Mode"](#ise-mode).</span></span>

## <a name="open-in-the-ise"></a><span data-ttu-id="cc2cb-162">ISE에서 열기</span><span class="sxs-lookup"><span data-stu-id="cc2cb-162">Open in the ISE</span></span>

<span data-ttu-id="cc2cb-163">어떤 방식으로든 ISE에서 파일을 열게 되는 경우 <kbd>Shift</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc2cb-163">If you end up wanting to open a file in the ISE anyway, you can use <kbd>Shift</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>.</span></span>

## <a name="other-resources"></a><span data-ttu-id="cc2cb-164">기타 리소스</span><span class="sxs-lookup"><span data-stu-id="cc2cb-164">Other resources</span></span>

- <span data-ttu-id="cc2cb-165">4sysops에는 VSCode를 ISE와 더 유사하게 구성하는 방법에 대한 [유용한 문서](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/)가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc2cb-165">4sysops has [a great article](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/) on configuring VSCode to be more like the ISE.</span></span>
- <span data-ttu-id="cc2cb-166">Mike F Robbins는 VSCode 설정에 대한 [유용한 게시물](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/)을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="cc2cb-166">Mike F Robbins has [a great post](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/) on setting up VSCode.</span></span>
- <span data-ttu-id="cc2cb-167">PowerShell에 있는 PowerShell용 VSCode 설정에 대한 [유용한 문서](https://www.learnpwsh.com/setup-vs-code-for-powershell/)를 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="cc2cb-167">Learn PowerShell has [an excellent write up](https://www.learnpwsh.com/setup-vs-code-for-powershell/) on getting VSCode setup for PowerShell.</span></span>

## <a name="more-settings"></a><span data-ttu-id="cc2cb-168">추가 설정</span><span class="sxs-lookup"><span data-stu-id="cc2cb-168">More settings</span></span>

<span data-ttu-id="cc2cb-169">ISE 사용자가 더 친숙하게 느끼도록 VSCode를 설정하는 더 많은 방법을 알고 있다면 이 문서에 참여하세요. 찾고 있는 호환성 구성이 있지만 해당 구성을 사용하도록 설정하는 방법을 찾을 수 없으면 [문제를 열고](https://github.com/PowerShell/vscode-powershell/issues/new/choose) 모든 궁금한 사항을 질문하세요.</span><span class="sxs-lookup"><span data-stu-id="cc2cb-169">If you know of more ways to make VSCode feel more familiar for ISE users, contribute to this doc. If there's a compatibility configuration you're looking for, but you can't find any way to enable it, [open an issue](https://github.com/PowerShell/vscode-powershell/issues/new/choose) and ask away!</span></span>

<span data-ttu-id="cc2cb-170">PR 및 참여도 언제든지 환영합니다.</span><span class="sxs-lookup"><span data-stu-id="cc2cb-170">We're always happy to accept PRs and contributions as well!</span></span>

## <a name="vscode-tips"></a><span data-ttu-id="cc2cb-171">VSCode 팁</span><span class="sxs-lookup"><span data-stu-id="cc2cb-171">VSCode Tips</span></span>

### <a name="command-palette"></a><span data-ttu-id="cc2cb-172">명령 팔레트</span><span class="sxs-lookup"><span data-stu-id="cc2cb-172">Command Palette</span></span>

<span data-ttu-id="cc2cb-173"><kbd>F1</kbd> 키 또는 <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>(macOS의 경우 <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>)</span><span class="sxs-lookup"><span data-stu-id="cc2cb-173"><kbd>F1</kbd> OR <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on macOS)</span></span>

<span data-ttu-id="cc2cb-174">VSCode에서 명령을 실행하는 편리한 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="cc2cb-174">A handy way of executing commands in VSCode.</span></span>
<span data-ttu-id="cc2cb-175">자세한 내용은 [VSCode 문서](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cc2cb-175">For more information, see [the VSCode docs](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette).</span></span>

[명령 팔레트]: #command-palette
[Command Palette]: #command-palette
