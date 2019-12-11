---
title: Visual Studio Code에서 ISE 환경을 복제하는 방법
description: Visual Studio Code에서 ISE 환경을 복제하는 방법
ms.date: 08/06/2018
ms.openlocfilehash: d5542e9a3a48b1ae64356309be669418edf6c79e
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74117502"
---
# <a name="how-to-replicate-the-ise-experience-in-visual-studio-code"></a><span data-ttu-id="b470d-103">Visual Studio Code에서 ISE 환경을 복제하는 방법</span><span class="sxs-lookup"><span data-stu-id="b470d-103">How to replicate the ISE experience in Visual Studio Code</span></span>

<span data-ttu-id="b470d-104">VSCode용 PowerShell 확장 PowerShell ISE와 완전히 동일한 기능을 제공하지는 않지만, ISE 사용자를 위해 VSCode 환경을 더 자연스럽게 만드는 대체 기능이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b470d-104">While the PowerShell extension for VSCode doesn't seek complete feature parity with the PowerShell ISE, there are features in place to make the VSCode experience more natural for users of the ISE.</span></span>

<span data-ttu-id="b470d-105">이 문서에는 사용자 환경을 ISE보다는 조금 더 친숙하게 만들도록 VSCode에서 구성할 수 있는 설정이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b470d-105">This document tries to list settings you can configure in VSCode to make the user experience a bit more familiar compared to the ISE.</span></span>

## <a name="key-bindings"></a><span data-ttu-id="b470d-106">키 바인딩</span><span class="sxs-lookup"><span data-stu-id="b470d-106">Key bindings</span></span>

| <span data-ttu-id="b470d-107">기능</span><span class="sxs-lookup"><span data-stu-id="b470d-107">Function</span></span>                              | <span data-ttu-id="b470d-108">ISE 바인딩</span><span class="sxs-lookup"><span data-stu-id="b470d-108">ISE Binding</span></span>                  | <span data-ttu-id="b470d-109">VSCode 바인딩</span><span class="sxs-lookup"><span data-stu-id="b470d-109">VSCode Binding</span></span>                              |
| ----------------                      | -----------                  | --------------                              |
| <span data-ttu-id="b470d-110">디버거 중단</span><span class="sxs-lookup"><span data-stu-id="b470d-110">Interrupt and break debugger</span></span>          | <span data-ttu-id="b470d-111"><kbd>Ctrl</kbd>+<kbd>B</kbd></span><span class="sxs-lookup"><span data-stu-id="b470d-111"><kbd>Ctrl</kbd>+<kbd>B</kbd></span></span> | <span data-ttu-id="b470d-112"><kbd>F6</kbd></span><span class="sxs-lookup"><span data-stu-id="b470d-112"><kbd>F6</kbd></span></span>                               |
| <span data-ttu-id="b470d-113">현재 줄/강조 표시된 텍스트 실행</span><span class="sxs-lookup"><span data-stu-id="b470d-113">Execute current line/highlighted text</span></span> | <span data-ttu-id="b470d-114"><kbd>F8</kbd></span><span class="sxs-lookup"><span data-stu-id="b470d-114"><kbd>F8</kbd></span></span>                | <span data-ttu-id="b470d-115"><kbd>F8</kbd></span><span class="sxs-lookup"><span data-stu-id="b470d-115"><kbd>F8</kbd></span></span>                               |
| <span data-ttu-id="b470d-116">사용 가능한 코드 조각 나열</span><span class="sxs-lookup"><span data-stu-id="b470d-116">List available snippets</span></span>               | <span data-ttu-id="b470d-117"><kbd>Ctrl</kbd>+<kbd>J</kbd></span><span class="sxs-lookup"><span data-stu-id="b470d-117"><kbd>Ctrl</kbd>+<kbd>J</kbd></span></span> | <span data-ttu-id="b470d-118"><kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd></span><span class="sxs-lookup"><span data-stu-id="b470d-118"><kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd></span></span> |

### <a name="custom-key-bindings"></a><span data-ttu-id="b470d-119">사용자 지정 키 바인딩</span><span class="sxs-lookup"><span data-stu-id="b470d-119">Custom Key bindings</span></span>

<span data-ttu-id="b470d-120">VSCode에서도 [고유한 키 바인딩을 구성](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings)할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b470d-120">You can [configure your own key bindings](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) in VSCode as well.</span></span>

## <a name="simplified-ise-like-ui"></a><span data-ttu-id="b470d-121">간소화된 ISE와 유사한 UI</span><span class="sxs-lookup"><span data-stu-id="b470d-121">Simplified ISE-like UI</span></span>

<span data-ttu-id="b470d-122">Visual Studio Code UI를 간소화하여 ISE의 UI를 보다 자세히 살펴보려면 다음 두 가지 설정을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="b470d-122">If you're looking to simplify the Visual Studio Code UI to look more closely to the UI of the ISE, apply these two settings:</span></span>

```json
"workbench.activityBar.visible": false,
"debug.openDebug": "neverOpen",
```

<span data-ttu-id="b470d-123">이렇게 하면 빨간색 상자 내부 아래에 있는 "작업 표시줄" 및 "디버그 사이드 막대" 섹션이 숨겨집니다.</span><span class="sxs-lookup"><span data-stu-id="b470d-123">This will hide the "Activity Bar" and the "Debug Side Bar" sections below inside of the red box:</span></span>

![강조 표시된 섹션에는 작업 표시줄과 디버그 사이드 막대가 포함됩니다.](images/How-To-Replicate-the-ISE-Experience-In-VSCode/1-highlighted-sidebar.png)

<span data-ttu-id="b470d-125">최종 결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b470d-125">The end result looks like this:</span></span>

![VS Code의 단순화된 보기](images/How-To-Replicate-the-ISE-Experience-In-VSCode/2-simplified-ui.png)

## <a name="tab-completion"></a><span data-ttu-id="b470d-127">탭 완성</span><span class="sxs-lookup"><span data-stu-id="b470d-127">Tab completion</span></span>

<span data-ttu-id="b470d-128">더 ISE와 유사한 탭 완성을 사용하려면 이 설정을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="b470d-128">To enable more ISE-like tab completion, add this setting:</span></span>

```json
"editor.tabCompletion": "on",
```

> [!NOTE]
> <span data-ttu-id="b470d-129">이 설정은 VSCode에 직접 추가되었습니다(확장으로 추가되지 않음).</span><span class="sxs-lookup"><span data-stu-id="b470d-129">This setting was added directly to VSCode (rather than in the extension).</span></span> <span data-ttu-id="b470d-130">해당 동작은 VSCode에 의해 직접 결정되며 확장에 의해 변경될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b470d-130">Its behavior is determined by VSCode directly and cannot be changed by the extension.</span></span>

## <a name="no-focus-on-console-when-executing"></a><span data-ttu-id="b470d-131">실행할 때 콘솔에 포커스 없음</span><span class="sxs-lookup"><span data-stu-id="b470d-131">No focus on console when executing</span></span>

<span data-ttu-id="b470d-132"><kbd>F8</kbd>로 실행할 때 편집기에서 포커스를 유지하려면</span><span class="sxs-lookup"><span data-stu-id="b470d-132">To keep the focus in the editor when you execute with <kbd>F8</kbd>:</span></span>

```json
"powershell.integratedConsole.focusConsoleOnExecute": false
```

<span data-ttu-id="b470d-133">기본값은 `true`입니다.</span><span class="sxs-lookup"><span data-stu-id="b470d-133">The default is `true` for accessibility purposes.</span></span>

## <a name="dont-start-integrated-console-on-startup"></a><span data-ttu-id="b470d-134">시작 시 통합 콘솔을 시작하지 않음</span><span class="sxs-lookup"><span data-stu-id="b470d-134">Don't start integrated console on startup</span></span>

<span data-ttu-id="b470d-135">시작 시 통합 콘솔을 중지하려면 다음을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="b470d-135">To stop the integrated console on startup, set:</span></span>

```json
"powershell.integratedConsole.showOnStartup": false
```

> [!NOTE]
> <span data-ttu-id="b470d-136">백그라운드 PowerShell 프로세스는 IntelliSense, 스크립트 분석, 기호 탐색 등을 제공하므로 계속 시작됩니다. 그러나 콘솔이 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b470d-136">The background PowerShell process will still start since that provides IntelliSense, script analysis, symbol navigation, etc. But the console won't be shown.</span></span>

## <a name="assume-files-are-powershell-by-default"></a><span data-ttu-id="b470d-137">파일이 기본적으로 PowerShell이라고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="b470d-137">Assume files are PowerShell by default</span></span>

<span data-ttu-id="b470d-138">새/제목 없는 파일을 만들려면 기본적으로 PowerShell로 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="b470d-138">To make new/untitled files, register as PowerShell by default:</span></span>

```json
"files.defaultLanguage": "powershell",
```

## <a name="color-scheme"></a><span data-ttu-id="b470d-139">색 구성표</span><span class="sxs-lookup"><span data-stu-id="b470d-139">Color scheme</span></span>

<span data-ttu-id="b470d-140">VSCode에서 편집기 모양을 ISE와 훨씬 더 비슷하게 설정하는 데 사용할 수 있는 다양한 ISE 테마가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b470d-140">There are a number of ISE themes available for VSCode to make the editor look much more like the ISE.</span></span>

<span data-ttu-id="b470d-141">[명령 팔레트]에 `theme`를 입력하여 `Preferences: Color Theme`를 가져오고 <kbd>Enter</kbd> 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="b470d-141">In the [Command Palette] type `theme` to get `Preferences: Color Theme` and press <kbd>Enter</kbd>.</span></span>
<span data-ttu-id="b470d-142">드롭다운 목록에서 `PowerShell ISE`를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b470d-142">In the drop-down list, select `PowerShell ISE`.</span></span>

<span data-ttu-id="b470d-143">다음을 사용하여 설정에서 이 테마를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b470d-143">You can set this theme in the settings with:</span></span>

```json
"workbench.colorTheme": "PowerShell ISE",
```

## <a name="powershell-command-explorer"></a><span data-ttu-id="b470d-144">PowerShell Command Explorer</span><span class="sxs-lookup"><span data-stu-id="b470d-144">PowerShell Command Explorer</span></span>

<span data-ttu-id="b470d-145">[@corbob](https://github.com/corbob)의 작업 덕분에 PowerShell 확장에는 고유한 초기 명령 탐색기가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b470d-145">Thanks to the work of [@corbob](https://github.com/corbob), the PowerShell extension has the beginnings of its own command explorer.</span></span>

<span data-ttu-id="b470d-146">[명령 팔레트]에 `PowerShell Command Explorer`를 입력하고 <kbd>Enter</kbd> 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="b470d-146">In the [Command Palette], enter `PowerShell Command Explorer` and press <kbd>Enter</kbd>.</span></span>

## <a name="open-in-the-ise"></a><span data-ttu-id="b470d-147">ISE에서 열기</span><span class="sxs-lookup"><span data-stu-id="b470d-147">Open in the ISE</span></span>

<span data-ttu-id="b470d-148">어떤 방식으로든 ISE에서 파일을 열게 되는 경우 <kbd>Shift</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b470d-148">If you end up wanting to open a file in the ISE anyway, you can use <kbd>Shift</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>.</span></span>

## <a name="other-resources"></a><span data-ttu-id="b470d-149">다른 리소스</span><span class="sxs-lookup"><span data-stu-id="b470d-149">Other resources</span></span>

- <span data-ttu-id="b470d-150">4sysops에는 VSCode를 ISE와 더 유사하게 구성하는 방법에 대한 [유용한 문서](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/)가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b470d-150">4sysops has [a great article](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/) on configuring VSCode to be more like the ISE.</span></span>
- <span data-ttu-id="b470d-151">Mike F Robbins는 VSCode 설정에 대한 [유용한 게시물](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/)을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b470d-151">Mike F Robbins has [a great post](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/) on setting up VSCode.</span></span>
- <span data-ttu-id="b470d-152">PowerShell에 있는 PowerShell용 VSCode 설정에 대한 [유용한 문서](https://www.learnpwsh.com/setup-vs-code-for-powershell/)를 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="b470d-152">Learn PowerShell has [an excellent write up](https://www.learnpwsh.com/setup-vs-code-for-powershell/) on getting VSCode setup for PowerShell.</span></span>

## <a name="more-settings"></a><span data-ttu-id="b470d-153">추가 설정</span><span class="sxs-lookup"><span data-stu-id="b470d-153">More settings</span></span>

<span data-ttu-id="b470d-154">ISE 사용자가 더 친숙하게 느끼도록 VSCode를 설정하는 더 많은 방법을 알고 있다면 이 문서에 참여하세요. 찾고 있는 호환성 구성이 있지만 해당 구성을 사용하도록 설정하는 방법을 찾을 수 없으면 [문제를 열고](https://github.com/PowerShell/vscode-powershell/issues/new/choose) 모든 궁금한 사항을 질문하세요.</span><span class="sxs-lookup"><span data-stu-id="b470d-154">If you know of more ways to make VSCode feel more familiar for ISE users, contribute to this doc. If there's a compatibility configuration you're looking for, but you can't find any way to enable it, [open an issue](https://github.com/PowerShell/vscode-powershell/issues/new/choose) and ask away!</span></span>

<span data-ttu-id="b470d-155">PR 및 참여도 언제든지 환영합니다.</span><span class="sxs-lookup"><span data-stu-id="b470d-155">We're always happy to accept PRs and contributions as well!</span></span>

## <a name="vscode-tips"></a><span data-ttu-id="b470d-156">VSCode 팁</span><span class="sxs-lookup"><span data-stu-id="b470d-156">VSCode Tips</span></span>

### <a name="command-palette"></a><span data-ttu-id="b470d-157">명령 팔레트</span><span class="sxs-lookup"><span data-stu-id="b470d-157">Command Palette</span></span>

<span data-ttu-id="b470d-158"><kbd>F1</kbd> 키 또는 <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>(macOS의 경우 <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>)</span><span class="sxs-lookup"><span data-stu-id="b470d-158"><kbd>F1</kbd> OR <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on macOS)</span></span>

<span data-ttu-id="b470d-159">VSCode에서 명령을 실행하는 편리한 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="b470d-159">A handy way of executing commands in VSCode.</span></span>
<span data-ttu-id="b470d-160">자세한 내용은 [VSCode 문서](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b470d-160">For more information, see [the VSCode docs](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette).</span></span>

[명령 팔레트]: #command-palette
[Command Palette]: #command-palette
