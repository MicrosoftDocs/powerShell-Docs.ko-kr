---
title: Visual Studio Code에서 ISE 환경을 복제하는 방법
description: Visual Studio Code에서 ISE 환경을 복제하는 방법
ms.date: 08/06/2018
ms.openlocfilehash: 983da850c13d72bcdc7b2d33970c6e9e06b3d869
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55681948"
---
# <a name="how-to-replicate-the-ise-experience-in-visual-studio-code"></a><span data-ttu-id="fd155-103">Visual Studio Code에서 ISE 환경을 복제하는 방법</span><span class="sxs-lookup"><span data-stu-id="fd155-103">How to replicate the ISE experience in Visual Studio Code</span></span>

<span data-ttu-id="fd155-104">VSCode 용 PowerShell 확장 PowerShell ISE를 사용 하 여 완전 한 기능 패리티를 검색 하지 않습니다, 하지만 기능은 VSCode 환경을 ISE의 사용자에 대 한 더 자연 스러운 확인 하기 위해 작동에서 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd155-104">While the PowerShell extension for VSCode doesn't seek complete feature parity with the PowerShell ISE, there are features in place to make the VSCode experience more natural for users of the ISE.</span></span>

<span data-ttu-id="fd155-105">이 문서는 사용자를 ISE에 비해 조금 더 친숙 한 환경을 위해 VSCode에서 구성할 수 있는 목록 설정 하려고 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd155-105">This document tries to list settings you can configure in VSCode to make the user experience a bit more familiar compared to the ISE.</span></span>

## <a name="key-bindings"></a><span data-ttu-id="fd155-106">키 바인딩</span><span class="sxs-lookup"><span data-stu-id="fd155-106">Key bindings</span></span>

| <span data-ttu-id="fd155-107">기능</span><span class="sxs-lookup"><span data-stu-id="fd155-107">Function</span></span>                              | <span data-ttu-id="fd155-108">ISE 바인딩</span><span class="sxs-lookup"><span data-stu-id="fd155-108">ISE Binding</span></span>                  | <span data-ttu-id="fd155-109">VSCode 바인딩</span><span class="sxs-lookup"><span data-stu-id="fd155-109">VSCode Binding</span></span>                              |
| ----------------                      | -----------                  | --------------                              |
| <span data-ttu-id="fd155-110">중단 하 고 디버거를 중단 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd155-110">Interrupt and break debugger</span></span>          | <span data-ttu-id="fd155-111"><kbd>Ctrl</kbd>+<kbd>B</kbd></span><span class="sxs-lookup"><span data-stu-id="fd155-111"><kbd>Ctrl</kbd>+<kbd>B</kbd></span></span> | <span data-ttu-id="fd155-112"><kbd>F6</kbd></span><span class="sxs-lookup"><span data-stu-id="fd155-112"><kbd>F6</kbd></span></span>                               |
| <span data-ttu-id="fd155-113">현재 줄/강조 표시 된 텍스트를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd155-113">Execute current line/highlighted text</span></span> | <span data-ttu-id="fd155-114"><kbd>F8</kbd></span><span class="sxs-lookup"><span data-stu-id="fd155-114"><kbd>F8</kbd></span></span>                | <span data-ttu-id="fd155-115"><kbd>F8</kbd></span><span class="sxs-lookup"><span data-stu-id="fd155-115"><kbd>F8</kbd></span></span>                               |
| <span data-ttu-id="fd155-116">사용 가능한 코드 조각 목록</span><span class="sxs-lookup"><span data-stu-id="fd155-116">List available snippets</span></span>               | <span data-ttu-id="fd155-117"><kbd>Ctrl</kbd>+<kbd>J</kbd></span><span class="sxs-lookup"><span data-stu-id="fd155-117"><kbd>Ctrl</kbd>+<kbd>J</kbd></span></span> | <span data-ttu-id="fd155-118"><kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd></span><span class="sxs-lookup"><span data-stu-id="fd155-118"><kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd></span></span> |

### <a name="custom-key-bindings"></a><span data-ttu-id="fd155-119">사용자 지정 키 바인딩</span><span class="sxs-lookup"><span data-stu-id="fd155-119">Custom Key bindings</span></span>

<span data-ttu-id="fd155-120">할 수 있습니다 [사용자 고유의 키 바인딩을 구성](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) 도 VSCode에서.</span><span class="sxs-lookup"><span data-stu-id="fd155-120">You can [configure your own key bindings](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) in VSCode as well.</span></span>

## <a name="tab-completion"></a><span data-ttu-id="fd155-121">탭 완성</span><span class="sxs-lookup"><span data-stu-id="fd155-121">Tab completion</span></span>

<span data-ttu-id="fd155-122">더 ISE 모양의 탭 완성 기능을 사용 하도록 설정 하려면이 설정을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd155-122">To enable more ISE-like tab completion, add this setting:</span></span>

```json
"editor.tabCompletion": "on"
```

> [!NOTE]
> <span data-ttu-id="fd155-123">이 설정은 VSCode에 직접 (아닌 확장)에 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="fd155-123">This setting was added directly to VSCode (rather than in the extension).</span></span> <span data-ttu-id="fd155-124">해당 동작 직접 VSCode에 의해 결정 됩니다 및 확장 하 여 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fd155-124">Its behavior is determined by VSCode directly and cannot be changed by the extension.</span></span>

## <a name="no-focus-on-console-when-executing"></a><span data-ttu-id="fd155-125">실행할 때 콘솔에서 포커스 없음</span><span class="sxs-lookup"><span data-stu-id="fd155-125">No focus on console when executing</span></span>

<span data-ttu-id="fd155-126">사용 하 여 실행 하면 편집기에서 포커스를 유지할 <kbd>F8</kbd>:</span><span class="sxs-lookup"><span data-stu-id="fd155-126">To keep the focus in the editor when you execute with <kbd>F8</kbd>:</span></span>

```json
"powershell.integratedConsole.focusConsoleOnExecute": false
```

<span data-ttu-id="fd155-127">기본값은 `true` 편리한 액세스를 위해.</span><span class="sxs-lookup"><span data-stu-id="fd155-127">The default is `true` for accessibility purposes.</span></span>

## <a name="dont-start-integrated-console-on-startup"></a><span data-ttu-id="fd155-128">시작 시 통합된 콘솔을 시작 하지 마십시오</span><span class="sxs-lookup"><span data-stu-id="fd155-128">Don't start integrated console on startup</span></span>

<span data-ttu-id="fd155-129">통합된 된 콘솔에서 시작을 중지 하려면 다음을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd155-129">To stop the integrated console on startup, set:</span></span>

```json
"powershell.integratedConsole.showOnStartup": false
```

> [!NOTE]
> <span data-ttu-id="fd155-130">IntelliSense, 스크립트 분석, 기호 탐색을 제공 하는 이후 백그라운드 PowerShell 프로세스를 시작할 수 있습니다. 그러나 콘솔에 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fd155-130">The background PowerShell process will still start since that provides IntelliSense, script analysis, symbol navigation, etc. But the console won't be shown.</span></span>

## <a name="assume-files-are-powershell-by-default"></a><span data-ttu-id="fd155-131">파일은 기본적으로 PowerShell 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd155-131">Assume files are PowerShell by default</span></span>

<span data-ttu-id="fd155-132">새 제목 없는 파일을 확인 하려면 기본적으로 PowerShell로 등록 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd155-132">To make new/untitled files, register as PowerShell by default:</span></span>

```json
"files.defaultLanguage": "powershell"
```

## <a name="color-scheme"></a><span data-ttu-id="fd155-133">색 구성표</span><span class="sxs-lookup"><span data-stu-id="fd155-133">Color scheme</span></span>

<span data-ttu-id="fd155-134">VSCode 훨씬와 좀 더 비슷하게 ISE 편집기를 사용할 수 있습니다 ISE 테마는 여러 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fd155-134">There are a number of ISE themes available for VSCode to make the editor look much more like the ISE.</span></span>

<span data-ttu-id="fd155-135">에 [명령 팔레트] 형식을 `theme` 가져오려고 `Preferences: Color Theme` 키를 누릅니다 <kbd>Enter</kbd>합니다.</span><span class="sxs-lookup"><span data-stu-id="fd155-135">In the [Command Palette] type `theme` to get `Preferences: Color Theme` and press <kbd>Enter</kbd>.</span></span>
<span data-ttu-id="fd155-136">드롭다운 목록에서 선택 `PowerShell ISE`합니다.</span><span class="sxs-lookup"><span data-stu-id="fd155-136">In the drop-down list, select `PowerShell ISE`.</span></span>

<span data-ttu-id="fd155-137">이 테마를 사용 하 여 설정에서 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fd155-137">You can set this theme in the settings with:</span></span>

```json
"workbench.colorTheme": "PowerShell ISE"
```

## <a name="powershell-command-explorer"></a><span data-ttu-id="fd155-138">PowerShell 명령을 탐색기</span><span class="sxs-lookup"><span data-stu-id="fd155-138">PowerShell Command Explorer</span></span>

<span data-ttu-id="fd155-139">작업을 덕분 [ @corbob ](https://github.com/corbob), PowerShell 확장에는 자체 명령 탐색기의 처음과 끝입니다.</span><span class="sxs-lookup"><span data-stu-id="fd155-139">Thanks to the work of [@corbob](https://github.com/corbob), the PowerShell extension has the beginnings of its own command explorer.</span></span>

<span data-ttu-id="fd155-140">에 [명령 팔레트]를 입력 `PowerShell Command Explorer` 키를 누릅니다 <kbd>Enter</kbd>합니다.</span><span class="sxs-lookup"><span data-stu-id="fd155-140">In the [Command Palette], enter `PowerShell Command Explorer` and press <kbd>Enter</kbd>.</span></span>

## <a name="open-in-the-ise"></a><span data-ttu-id="fd155-141">ISE에서 열기</span><span class="sxs-lookup"><span data-stu-id="fd155-141">Open in the ISE</span></span>

<span data-ttu-id="fd155-142">ISE에서 파일을 여시겠습니까 하려는 얻게 되는 경우 사용할 수 있습니다 <kbd>Shift</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>합니다.</span><span class="sxs-lookup"><span data-stu-id="fd155-142">If you end up wanting to open a file in the ISE anyway, you can use <kbd>Shift</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>.</span></span>

## <a name="other-resources"></a><span data-ttu-id="fd155-143">다른 리소스</span><span class="sxs-lookup"><span data-stu-id="fd155-143">Other resources</span></span>

- <span data-ttu-id="fd155-144">4sysops 했습니다 [훌륭한 기사](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/) ISE와 같은 더 VSCode를 구성 하는 방법에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fd155-144">4sysops has [a great article](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/) on configuring VSCode to be more like the ISE.</span></span>
- <span data-ttu-id="fd155-145">Mike F Robbins 했습니다 [유용한 게시물](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/) VSCode를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd155-145">Mike F Robbins has [a great post](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/) on setting up VSCode.</span></span>
- <span data-ttu-id="fd155-146">PowerShell에 알아봅니다 [하는 뛰어난 쓰기](https://www.learnpwsh.com/setup-vs-code-for-powershell/) VSCode를 가져오는 방법에 PowerShell에 대 한 설정입니다.</span><span class="sxs-lookup"><span data-stu-id="fd155-146">Learn PowerShell has [an excellent write up](https://www.learnpwsh.com/setup-vs-code-for-powershell/) on getting VSCode setup for PowerShell.</span></span>

## <a name="more-settings"></a><span data-ttu-id="fd155-147">추가 설정</span><span class="sxs-lookup"><span data-stu-id="fd155-147">More settings</span></span>

<span data-ttu-id="fd155-148">VSCode ISE 사용자에 대 한 더 익숙하게 느껴질 것을 확인 하는 방법의 경우이 문서에 기여 합니다. 경우에 대 한 원하는 호환성 구성 없지만 사용 하도록 설정 하는 방식으로 찾을 수 없는 [문제를 제기](https://github.com/PowerShell/vscode-powershell/issues/new/choose) 모든 궁금한 사항을 질문 하 고!</span><span class="sxs-lookup"><span data-stu-id="fd155-148">If you know of more ways to make VSCode feel more familiar for ISE users, contribute to this doc. If there's a compatibility configuration you're looking for, but you can't find any way to enable it, [open an issue](https://github.com/PowerShell/vscode-powershell/issues/new/choose) and ask away!</span></span>

<span data-ttu-id="fd155-149">와 기여를 환영 언제나!</span><span class="sxs-lookup"><span data-stu-id="fd155-149">We're always happy to accept PRs and contributions as well!</span></span>

## <a name="vscode-tips"></a><span data-ttu-id="fd155-150">VSCode 팁</span><span class="sxs-lookup"><span data-stu-id="fd155-150">VSCode Tips</span></span>

### <a name="command-palette"></a><span data-ttu-id="fd155-151">명령 팔레트</span><span class="sxs-lookup"><span data-stu-id="fd155-151">Command Palette</span></span>

<span data-ttu-id="fd155-152"><kbd>F1</kbd> 나 <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd> + <kbd> 시프트</kbd>+<kbd>P</kbd> macos)</span><span class="sxs-lookup"><span data-stu-id="fd155-152"><kbd>F1</kbd> OR <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on macOS)</span></span>

<span data-ttu-id="fd155-153">VSCode에서 명령을 실행 하는 편리한 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="fd155-153">A handy way of executing commands in VSCode.</span></span>
<span data-ttu-id="fd155-154">자세한 내용은 [VSCode docs](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette)합니다.</span><span class="sxs-lookup"><span data-stu-id="fd155-154">For more information, see [the VSCode docs](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette).</span></span>

[명령 팔레트]: #command-palette
[Command Palette]: #command-palette
