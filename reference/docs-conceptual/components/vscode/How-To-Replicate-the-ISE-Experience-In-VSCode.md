---
title: Visual Studio Code에서 ISE 환경을 복제하는 방법
description: Visual Studio Code에서 ISE 환경을 복제하는 방법
ms.date: 08/06/2018
ms.openlocfilehash: 983da850c13d72bcdc7b2d33970c6e9e06b3d869
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058525"
---
# <a name="how-to-replicate-the-ise-experience-in-visual-studio-code"></a><span data-ttu-id="d8d61-103">Visual Studio Code에서 ISE 환경을 복제하는 방법</span><span class="sxs-lookup"><span data-stu-id="d8d61-103">How to replicate the ISE experience in Visual Studio Code</span></span>

<span data-ttu-id="d8d61-104">VSCode용 PowerShell 확장 PowerShell ISE와 완전히 동일한 기능을 제공하지는 않지만, ISE 사용자를 위해 VSCode 환경을 더 자연스럽게 만드는 대체 기능이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8d61-104">While the PowerShell extension for VSCode doesn't seek complete feature parity with the PowerShell ISE, there are features in place to make the VSCode experience more natural for users of the ISE.</span></span>

<span data-ttu-id="d8d61-105">이 문서에는 사용자 환경을 ISE보다는 조금 더 친숙하게 만들도록 VSCode에서 구성할 수 있는 설정이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8d61-105">This document tries to list settings you can configure in VSCode to make the user experience a bit more familiar compared to the ISE.</span></span>

## <a name="key-bindings"></a><span data-ttu-id="d8d61-106">키 바인딩</span><span class="sxs-lookup"><span data-stu-id="d8d61-106">Key bindings</span></span>

| <span data-ttu-id="d8d61-107">기능</span><span class="sxs-lookup"><span data-stu-id="d8d61-107">Function</span></span>                              | <span data-ttu-id="d8d61-108">ISE 바인딩</span><span class="sxs-lookup"><span data-stu-id="d8d61-108">ISE Binding</span></span>                  | <span data-ttu-id="d8d61-109">VSCode 바인딩</span><span class="sxs-lookup"><span data-stu-id="d8d61-109">VSCode Binding</span></span>                              |
| ----------------                      | -----------                  | --------------                              |
| <span data-ttu-id="d8d61-110">디버거 중단</span><span class="sxs-lookup"><span data-stu-id="d8d61-110">Interrupt and break debugger</span></span>          | <span data-ttu-id="d8d61-111"><kbd>Ctrl</kbd>+<kbd>B</kbd></span><span class="sxs-lookup"><span data-stu-id="d8d61-111"><kbd>Ctrl</kbd>+<kbd>B</kbd></span></span> | <span data-ttu-id="d8d61-112"><kbd>F6</kbd></span><span class="sxs-lookup"><span data-stu-id="d8d61-112"><kbd>F6</kbd></span></span>                               |
| <span data-ttu-id="d8d61-113">현재 줄/강조 표시된 텍스트 실행</span><span class="sxs-lookup"><span data-stu-id="d8d61-113">Execute current line/highlighted text</span></span> | <span data-ttu-id="d8d61-114"><kbd>F8</kbd></span><span class="sxs-lookup"><span data-stu-id="d8d61-114"><kbd>F8</kbd></span></span>                | <span data-ttu-id="d8d61-115"><kbd>F8</kbd></span><span class="sxs-lookup"><span data-stu-id="d8d61-115"><kbd>F8</kbd></span></span>                               |
| <span data-ttu-id="d8d61-116">사용 가능한 코드 조각 나열</span><span class="sxs-lookup"><span data-stu-id="d8d61-116">List available snippets</span></span>               | <span data-ttu-id="d8d61-117"><kbd>Ctrl</kbd>+<kbd>J</kbd></span><span class="sxs-lookup"><span data-stu-id="d8d61-117"><kbd>Ctrl</kbd>+<kbd>J</kbd></span></span> | <span data-ttu-id="d8d61-118"><kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd></span><span class="sxs-lookup"><span data-stu-id="d8d61-118"><kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd></span></span> |

### <a name="custom-key-bindings"></a><span data-ttu-id="d8d61-119">사용자 지정 키 바인딩</span><span class="sxs-lookup"><span data-stu-id="d8d61-119">Custom Key bindings</span></span>

<span data-ttu-id="d8d61-120">VSCode에서도 [고유한 키 바인딩을 구성](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings)할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8d61-120">You can [configure your own key bindings](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) in VSCode as well.</span></span>

## <a name="tab-completion"></a><span data-ttu-id="d8d61-121">탭 완성</span><span class="sxs-lookup"><span data-stu-id="d8d61-121">Tab completion</span></span>

<span data-ttu-id="d8d61-122">더 ISE와 유사한 탭 완성을 사용하려면 이 설정을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="d8d61-122">To enable more ISE-like tab completion, add this setting:</span></span>

```json
"editor.tabCompletion": "on"
```

> [!NOTE]
> <span data-ttu-id="d8d61-123">이 설정은 VSCode에 직접 추가되었습니다(확장으로 추가되지 않음).</span><span class="sxs-lookup"><span data-stu-id="d8d61-123">This setting was added directly to VSCode (rather than in the extension).</span></span> <span data-ttu-id="d8d61-124">해당 동작은 VSCode에 의해 직접 결정되며 확장에 의해 변경될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d8d61-124">Its behavior is determined by VSCode directly and cannot be changed by the extension.</span></span>

## <a name="no-focus-on-console-when-executing"></a><span data-ttu-id="d8d61-125">실행할 때 콘솔에 포커스 없음</span><span class="sxs-lookup"><span data-stu-id="d8d61-125">No focus on console when executing</span></span>

<span data-ttu-id="d8d61-126"><kbd>F8</kbd>로 실행할 때 편집기에서 포커스를 유지하려면</span><span class="sxs-lookup"><span data-stu-id="d8d61-126">To keep the focus in the editor when you execute with <kbd>F8</kbd>:</span></span>

```json
"powershell.integratedConsole.focusConsoleOnExecute": false
```

<span data-ttu-id="d8d61-127">기본값은 `true`입니다.</span><span class="sxs-lookup"><span data-stu-id="d8d61-127">The default is `true` for accessibility purposes.</span></span>

## <a name="dont-start-integrated-console-on-startup"></a><span data-ttu-id="d8d61-128">시작 시 통합 콘솔을 시작하지 않음</span><span class="sxs-lookup"><span data-stu-id="d8d61-128">Don't start integrated console on startup</span></span>

<span data-ttu-id="d8d61-129">시작 시 통합 콘솔을 중지하려면 다음을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="d8d61-129">To stop the integrated console on startup, set:</span></span>

```json
"powershell.integratedConsole.showOnStartup": false
```

> [!NOTE]
> <span data-ttu-id="d8d61-130">백그라운드 PowerShell 프로세스는 IntelliSense, 스크립트 분석, 기호 탐색 등을 제공하므로 계속 시작됩니다. 그러나 콘솔이 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d8d61-130">The background PowerShell process will still start since that provides IntelliSense, script analysis, symbol navigation, etc. But the console won't be shown.</span></span>

## <a name="assume-files-are-powershell-by-default"></a><span data-ttu-id="d8d61-131">파일이 기본적으로 PowerShell이라고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="d8d61-131">Assume files are PowerShell by default</span></span>

<span data-ttu-id="d8d61-132">새/제목 없는 파일을 만들려면 기본적으로 PowerShell로 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="d8d61-132">To make new/untitled files, register as PowerShell by default:</span></span>

```json
"files.defaultLanguage": "powershell"
```

## <a name="color-scheme"></a><span data-ttu-id="d8d61-133">색 구성표</span><span class="sxs-lookup"><span data-stu-id="d8d61-133">Color scheme</span></span>

<span data-ttu-id="d8d61-134">VSCode에서 편집기 모양을 ISE와 훨씬 더 비슷하게 설정하는 데 사용할 수 있는 다양한 ISE 테마가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8d61-134">There are a number of ISE themes available for VSCode to make the editor look much more like the ISE.</span></span>

<span data-ttu-id="d8d61-135">[명령 팔레트]에 `theme`를 입력하여 `Preferences: Color Theme`를 가져오고 <kbd>Enter</kbd> 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="d8d61-135">In the [Command Palette] type `theme` to get `Preferences: Color Theme` and press <kbd>Enter</kbd>.</span></span>
<span data-ttu-id="d8d61-136">드롭다운 목록에서 `PowerShell ISE`를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d8d61-136">In the drop-down list, select `PowerShell ISE`.</span></span>

<span data-ttu-id="d8d61-137">다음을 사용하여 설정에서 이 테마를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8d61-137">You can set this theme in the settings with:</span></span>

```json
"workbench.colorTheme": "PowerShell ISE"
```

## <a name="powershell-command-explorer"></a><span data-ttu-id="d8d61-138">PowerShell Command Explorer</span><span class="sxs-lookup"><span data-stu-id="d8d61-138">PowerShell Command Explorer</span></span>

<span data-ttu-id="d8d61-139">[@corbob](https://github.com/corbob)의 작업 덕분에 PowerShell 확장에는 고유한 초기 명령 탐색기가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8d61-139">Thanks to the work of [@corbob](https://github.com/corbob), the PowerShell extension has the beginnings of its own command explorer.</span></span>

<span data-ttu-id="d8d61-140">[명령 팔레트]에 `PowerShell Command Explorer`를 입력하고 <kbd>Enter</kbd> 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="d8d61-140">In the [Command Palette], enter `PowerShell Command Explorer` and press <kbd>Enter</kbd>.</span></span>

## <a name="open-in-the-ise"></a><span data-ttu-id="d8d61-141">ISE에서 열기</span><span class="sxs-lookup"><span data-stu-id="d8d61-141">Open in the ISE</span></span>

<span data-ttu-id="d8d61-142">어떤 방식으로든 ISE에서 파일을 열게 되는 경우 <kbd>Shift</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8d61-142">If you end up wanting to open a file in the ISE anyway, you can use <kbd>Shift</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>.</span></span>

## <a name="other-resources"></a><span data-ttu-id="d8d61-143">다른 리소스</span><span class="sxs-lookup"><span data-stu-id="d8d61-143">Other resources</span></span>

- <span data-ttu-id="d8d61-144">4sysops에는 VSCode를 ISE와 더 유사하게 구성하는 방법에 대한 [유용한 문서](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/)가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8d61-144">4sysops has [a great article](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/) on configuring VSCode to be more like the ISE.</span></span>
- <span data-ttu-id="d8d61-145">Mike F Robbins는 VSCode 설정에 대한 [유용한 게시물](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/)을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d8d61-145">Mike F Robbins has [a great post](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/) on setting up VSCode.</span></span>
- <span data-ttu-id="d8d61-146">PowerShell에 있는 PowerShell용 VSCode 설정에 대한 [유용한 문서](https://www.learnpwsh.com/setup-vs-code-for-powershell/)를 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="d8d61-146">Learn PowerShell has [an excellent write up](https://www.learnpwsh.com/setup-vs-code-for-powershell/) on getting VSCode setup for PowerShell.</span></span>

## <a name="more-settings"></a><span data-ttu-id="d8d61-147">추가 설정</span><span class="sxs-lookup"><span data-stu-id="d8d61-147">More settings</span></span>

<span data-ttu-id="d8d61-148">ISE 사용자가 더 친숙하게 느끼도록 VSCode를 설정하는 더 많은 방법을 알고 있다면 이 문서에 참여하세요. 찾고 있는 호환성 구성이 있지만 해당 구성을 사용하도록 설정하는 방법을 찾을 수 없으면 [문제를 열고](https://github.com/PowerShell/vscode-powershell/issues/new/choose) 모든 궁금한 사항을 질문하세요.</span><span class="sxs-lookup"><span data-stu-id="d8d61-148">If you know of more ways to make VSCode feel more familiar for ISE users, contribute to this doc. If there's a compatibility configuration you're looking for, but you can't find any way to enable it, [open an issue](https://github.com/PowerShell/vscode-powershell/issues/new/choose) and ask away!</span></span>

<span data-ttu-id="d8d61-149">PR 및 참여도 언제든지 환영합니다.</span><span class="sxs-lookup"><span data-stu-id="d8d61-149">We're always happy to accept PRs and contributions as well!</span></span>

## <a name="vscode-tips"></a><span data-ttu-id="d8d61-150">VSCode 팁</span><span class="sxs-lookup"><span data-stu-id="d8d61-150">VSCode Tips</span></span>

### <a name="command-palette"></a><span data-ttu-id="d8d61-151">명령 팔레트</span><span class="sxs-lookup"><span data-stu-id="d8d61-151">Command Palette</span></span>

<span data-ttu-id="d8d61-152"><kbd>F1</kbd> 키 또는 <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>(macOS의 경우 <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>)</span><span class="sxs-lookup"><span data-stu-id="d8d61-152"><kbd>F1</kbd> OR <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on macOS)</span></span>

<span data-ttu-id="d8d61-153">VSCode에서 명령을 실행하는 편리한 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="d8d61-153">A handy way of executing commands in VSCode.</span></span>
<span data-ttu-id="d8d61-154">자세한 내용은 [VSCode 문서](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d8d61-154">For more information, see [the VSCode docs](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette).</span></span>

[명령 팔레트]: #command-palette
[Command Palette]: #command-palette
