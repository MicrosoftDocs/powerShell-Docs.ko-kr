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
# <a name="how-to-replicate-the-ise-experience-in-visual-studio-code"></a>Visual Studio Code에서 ISE 환경을 복제하는 방법

VSCode용 PowerShell 확장 PowerShell ISE와 완전히 동일한 기능을 제공하지는 않지만, ISE 사용자를 위해 VSCode 환경을 더 자연스럽게 만드는 대체 기능이 있습니다.

이 문서에는 사용자 환경을 ISE보다는 조금 더 친숙하게 만들도록 VSCode에서 구성할 수 있는 설정이 나와 있습니다.

## <a name="key-bindings"></a>키 바인딩

| 기능                              | ISE 바인딩                  | VSCode 바인딩                              |
| ----------------                      | -----------                  | --------------                              |
| 디버거 중단          | <kbd>Ctrl</kbd>+<kbd>B</kbd> | <kbd>F6</kbd>                               |
| 현재 줄/강조 표시된 텍스트 실행 | <kbd>F8</kbd>                | <kbd>F8</kbd>                               |
| 사용 가능한 코드 조각 나열               | <kbd>Ctrl</kbd>+<kbd>J</kbd> | <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd> |

### <a name="custom-key-bindings"></a>사용자 지정 키 바인딩

VSCode에서도 [고유한 키 바인딩을 구성](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings)할 수 있습니다.

## <a name="simplified-ise-like-ui"></a>간소화된 ISE와 유사한 UI

Visual Studio Code UI를 간소화하여 ISE의 UI를 보다 자세히 살펴보려면 다음 두 가지 설정을 적용합니다.

```json
"workbench.activityBar.visible": false,
"debug.openDebug": "neverOpen",
```

이렇게 하면 빨간색 상자 내부 아래에 있는 "작업 표시줄" 및 "디버그 사이드 막대" 섹션이 숨겨집니다.

![강조 표시된 섹션에는 작업 표시줄과 디버그 사이드 막대가 포함됩니다.](images/How-To-Replicate-the-ISE-Experience-In-VSCode/1-highlighted-sidebar.png)

최종 결과는 다음과 같습니다.

![VS Code의 단순화된 보기](images/How-To-Replicate-the-ISE-Experience-In-VSCode/2-simplified-ui.png)

## <a name="tab-completion"></a>탭 완성

더 ISE와 유사한 탭 완성을 사용하려면 이 설정을 추가합니다.

```json
"editor.tabCompletion": "on",
```

> [!NOTE]
> 이 설정은 VSCode에 직접 추가되었습니다(확장으로 추가되지 않음). 해당 동작은 VSCode에 의해 직접 결정되며 확장에 의해 변경될 수 없습니다.

## <a name="no-focus-on-console-when-executing"></a>실행할 때 콘솔에 포커스 없음

<kbd>F8</kbd>로 실행할 때 편집기에서 포커스를 유지하려면

```json
"powershell.integratedConsole.focusConsoleOnExecute": false
```

기본값은 `true`입니다.

## <a name="dont-start-integrated-console-on-startup"></a>시작 시 통합 콘솔을 시작하지 않음

시작 시 통합 콘솔을 중지하려면 다음을 설정합니다.

```json
"powershell.integratedConsole.showOnStartup": false
```

> [!NOTE]
> 백그라운드 PowerShell 프로세스는 IntelliSense, 스크립트 분석, 기호 탐색 등을 제공하므로 계속 시작됩니다. 그러나 콘솔이 표시되지 않습니다.

## <a name="assume-files-are-powershell-by-default"></a>파일이 기본적으로 PowerShell이라고 가정합니다.

새/제목 없는 파일을 만들려면 기본적으로 PowerShell로 등록합니다.

```json
"files.defaultLanguage": "powershell",
```

## <a name="color-scheme"></a>색 구성표

VSCode에서 편집기 모양을 ISE와 훨씬 더 비슷하게 설정하는 데 사용할 수 있는 다양한 ISE 테마가 있습니다.

[명령 팔레트]에 `theme`를 입력하여 `Preferences: Color Theme`를 가져오고 <kbd>Enter</kbd> 키를 누릅니다.
드롭다운 목록에서 `PowerShell ISE`를 선택합니다.

다음을 사용하여 설정에서 이 테마를 설정할 수 있습니다.

```json
"workbench.colorTheme": "PowerShell ISE",
```

## <a name="powershell-command-explorer"></a>PowerShell Command Explorer

[@corbob](https://github.com/corbob)의 작업 덕분에 PowerShell 확장에는 고유한 초기 명령 탐색기가 있습니다.

[명령 팔레트]에 `PowerShell Command Explorer`를 입력하고 <kbd>Enter</kbd> 키를 누릅니다.

## <a name="open-in-the-ise"></a>ISE에서 열기

어떤 방식으로든 ISE에서 파일을 열게 되는 경우 <kbd>Shift</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>를 사용할 수 있습니다.

## <a name="other-resources"></a>다른 리소스

- 4sysops에는 VSCode를 ISE와 더 유사하게 구성하는 방법에 대한 [유용한 문서](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/)가 있습니다.
- Mike F Robbins는 VSCode 설정에 대한 [유용한 게시물](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/)을 제공합니다.
- PowerShell에 있는 PowerShell용 VSCode 설정에 대한 [유용한 문서](https://www.learnpwsh.com/setup-vs-code-for-powershell/)를 알아봅니다.

## <a name="more-settings"></a>추가 설정

ISE 사용자가 더 친숙하게 느끼도록 VSCode를 설정하는 더 많은 방법을 알고 있다면 이 문서에 참여하세요. 찾고 있는 호환성 구성이 있지만 해당 구성을 사용하도록 설정하는 방법을 찾을 수 없으면 [문제를 열고](https://github.com/PowerShell/vscode-powershell/issues/new/choose) 모든 궁금한 사항을 질문하세요.

PR 및 참여도 언제든지 환영합니다.

## <a name="vscode-tips"></a>VSCode 팁

### <a name="command-palette"></a>명령 팔레트

<kbd>F1</kbd> 키 또는 <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>(macOS의 경우 <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>)

VSCode에서 명령을 실행하는 편리한 방법입니다.
자세한 내용은 [VSCode 문서](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette)를 참조하세요.

[명령 팔레트]: #command-palette
