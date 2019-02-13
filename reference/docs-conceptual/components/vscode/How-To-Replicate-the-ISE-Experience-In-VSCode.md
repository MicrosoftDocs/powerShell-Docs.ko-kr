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
# <a name="how-to-replicate-the-ise-experience-in-visual-studio-code"></a>Visual Studio Code에서 ISE 환경을 복제하는 방법

VSCode 용 PowerShell 확장 PowerShell ISE를 사용 하 여 완전 한 기능 패리티를 검색 하지 않습니다, 하지만 기능은 VSCode 환경을 ISE의 사용자에 대 한 더 자연 스러운 확인 하기 위해 작동에서 합니다.

이 문서는 사용자를 ISE에 비해 조금 더 친숙 한 환경을 위해 VSCode에서 구성할 수 있는 목록 설정 하려고 시도 합니다.

## <a name="key-bindings"></a>키 바인딩

| 기능                              | ISE 바인딩                  | VSCode 바인딩                              |
| ----------------                      | -----------                  | --------------                              |
| 중단 하 고 디버거를 중단 합니다.          | <kbd>Ctrl</kbd>+<kbd>B</kbd> | <kbd>F6</kbd>                               |
| 현재 줄/강조 표시 된 텍스트를 실행 합니다. | <kbd>F8</kbd>                | <kbd>F8</kbd>                               |
| 사용 가능한 코드 조각 목록               | <kbd>Ctrl</kbd>+<kbd>J</kbd> | <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd> |

### <a name="custom-key-bindings"></a>사용자 지정 키 바인딩

할 수 있습니다 [사용자 고유의 키 바인딩을 구성](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) 도 VSCode에서.

## <a name="tab-completion"></a>탭 완성

더 ISE 모양의 탭 완성 기능을 사용 하도록 설정 하려면이 설정을 추가 합니다.

```json
"editor.tabCompletion": "on"
```

> [!NOTE]
> 이 설정은 VSCode에 직접 (아닌 확장)에 추가 되었습니다. 해당 동작 직접 VSCode에 의해 결정 됩니다 및 확장 하 여 변경할 수 없습니다.

## <a name="no-focus-on-console-when-executing"></a>실행할 때 콘솔에서 포커스 없음

사용 하 여 실행 하면 편집기에서 포커스를 유지할 <kbd>F8</kbd>:

```json
"powershell.integratedConsole.focusConsoleOnExecute": false
```

기본값은 `true` 편리한 액세스를 위해.

## <a name="dont-start-integrated-console-on-startup"></a>시작 시 통합된 콘솔을 시작 하지 마십시오

통합된 된 콘솔에서 시작을 중지 하려면 다음을 설정 합니다.

```json
"powershell.integratedConsole.showOnStartup": false
```

> [!NOTE]
> IntelliSense, 스크립트 분석, 기호 탐색을 제공 하는 이후 백그라운드 PowerShell 프로세스를 시작할 수 있습니다. 그러나 콘솔에 표시 되지 않습니다.

## <a name="assume-files-are-powershell-by-default"></a>파일은 기본적으로 PowerShell 가정 합니다.

새 제목 없는 파일을 확인 하려면 기본적으로 PowerShell로 등록 합니다.

```json
"files.defaultLanguage": "powershell"
```

## <a name="color-scheme"></a>색 구성표

VSCode 훨씬와 좀 더 비슷하게 ISE 편집기를 사용할 수 있습니다 ISE 테마는 여러 가지가 있습니다.

에 [명령 팔레트] 형식을 `theme` 가져오려고 `Preferences: Color Theme` 키를 누릅니다 <kbd>Enter</kbd>합니다.
드롭다운 목록에서 선택 `PowerShell ISE`합니다.

이 테마를 사용 하 여 설정에서 설정할 수 있습니다.

```json
"workbench.colorTheme": "PowerShell ISE"
```

## <a name="powershell-command-explorer"></a>PowerShell 명령을 탐색기

작업을 덕분 [ @corbob ](https://github.com/corbob), PowerShell 확장에는 자체 명령 탐색기의 처음과 끝입니다.

에 [명령 팔레트]를 입력 `PowerShell Command Explorer` 키를 누릅니다 <kbd>Enter</kbd>합니다.

## <a name="open-in-the-ise"></a>ISE에서 열기

ISE에서 파일을 여시겠습니까 하려는 얻게 되는 경우 사용할 수 있습니다 <kbd>Shift</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>합니다.

## <a name="other-resources"></a>다른 리소스

- 4sysops 했습니다 [훌륭한 기사](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/) ISE와 같은 더 VSCode를 구성 하는 방법에 있습니다.
- Mike F Robbins 했습니다 [유용한 게시물](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/) VSCode를 설정 합니다.
- PowerShell에 알아봅니다 [하는 뛰어난 쓰기](https://www.learnpwsh.com/setup-vs-code-for-powershell/) VSCode를 가져오는 방법에 PowerShell에 대 한 설정입니다.

## <a name="more-settings"></a>추가 설정

VSCode ISE 사용자에 대 한 더 익숙하게 느껴질 것을 확인 하는 방법의 경우이 문서에 기여 합니다. 경우에 대 한 원하는 호환성 구성 없지만 사용 하도록 설정 하는 방식으로 찾을 수 없는 [문제를 제기](https://github.com/PowerShell/vscode-powershell/issues/new/choose) 모든 궁금한 사항을 질문 하 고!

와 기여를 환영 언제나!

## <a name="vscode-tips"></a>VSCode 팁

### <a name="command-palette"></a>명령 팔레트

<kbd>F1</kbd> 나 <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd> + <kbd> 시프트</kbd>+<kbd>P</kbd> macos)

VSCode에서 명령을 실행 하는 편리한 방법입니다.
자세한 내용은 [VSCode docs](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette)합니다.

[명령 팔레트]: #command-palette
