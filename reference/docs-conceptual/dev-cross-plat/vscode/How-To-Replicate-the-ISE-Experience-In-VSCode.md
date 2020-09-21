---
title: Visual Studio Code에서 ISE 환경을 복제하는 방법
description: Visual Studio Code에서 ISE 환경을 복제하는 방법
ms.date: 08/06/2018
ms.openlocfilehash: 6b0b8ce054695d6cc0fc578290c554e2dc1472bc
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784625"
---
# <a name="how-to-replicate-the-ise-experience-in-visual-studio-code"></a>Visual Studio Code에서 ISE 환경을 복제하는 방법

VS Code용 PowerShell 확장 PowerShell ISE와 완전히 동일한 기능을 제공하지는 않지만, ISE 사용자를 위해 VS Code 환경을 더 자연스럽게 만드는 대체 기능이 있습니다.

이 문서에는 사용자 환경을 ISE보다는 조금 더 친숙하게 만들도록 VS Code에서 구성할 수 있는 설정이 나와 있습니다.

## <a name="ise-mode"></a>ISE 모드

> [!NOTE]
> 이 기능은 버전 2019.12.0 이후 PowerShell 미리 보기 확장과 버전 2020.3.0 이후 PowerShell 확장에서 사용할 수 있습니다.

Visual Studio Code에서 ISE 환경을 복제하는 가장 쉬운 방법은 "ISE 모드"를 설정하는 것입니다.
이 작업을 수행하려면 명령 팔레트(<kbd>F1</kbd> 또는 <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> 또는 macOS에서 <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>)를 열고 "ISE 모드"를 입력합니다. 목록에서 "PowerShell: ISE 모드 사용"을 선택합니다.

이 명령은 아래에 설명된 설정을 자동으로 적용합니다. 결과는 다음과 같습니다.

![ISE 모드의 Visual Studio Code](media/How-To-Replicate-the-ISE-Experience-In-VSCode/3-ise-mode.png)

## <a name="ise-mode-configuration-settings"></a>ISE 모드 구성 설정

ISE 모드를 사용하면 VS Code 설정이 다음과 같이 변경됩니다.

- 키 바인딩

  |               함수                |         ISE 바인딩          |              VS Code 바인딩                |
  | ------------------------------------- | ---------------------------- | ------------------------------------------- |
  | 디버거 중단          | <kbd>Ctrl</kbd>+<kbd>B</kbd> | <kbd>F6</kbd>                               |
  | 현재 줄/강조 표시된 텍스트 실행 | <kbd>F8</kbd>                | <kbd>F8</kbd>                               |
  | 사용 가능한 코드 조각 나열               | <kbd>Ctrl</kbd>+<kbd>J</kbd> | <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd> |

  > [!NOTE]
  > VS Code에서도 [고유한 키 바인딩을 구성](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings)할 수 있습니다.

- 간소화된 ISE와 유사한 UI

  Visual Studio Code UI를 간소화하여 ISE의 UI를 보다 자세히 살펴보려면 다음 두 가지 설정을 적용합니다.

  ```json
  "workbench.activityBar.visible": false,
  "debug.openDebug": "neverOpen",
  ```

  이러한 설정은 빨간색 상자 내부 아래에 있는 "작업 표시줄" 및 "디버그 사이드 막대" 섹션을 숨깁니다.

  ![강조 표시된 섹션에는 작업 표시줄과 디버그 사이드 막대가 포함됨](media/How-To-Replicate-the-ISE-Experience-In-VSCode/1-highlighted-sidebar.png)

  최종 결과는 다음과 같습니다.

  ![VS Code의 단순화된 보기](media/How-To-Replicate-the-ISE-Experience-In-VSCode/2-simplified-ui.png)

- 탭 완성

  더 ISE와 유사한 탭 완성을 사용하려면 이 설정을 추가합니다.

  ```json
  "editor.tabCompletion": "on",
  ```

- 실행 시 콘솔에 포커스 없음

  <kbd>F8</kbd>로 실행할 때 편집기에서 포커스를 유지하려면

  ```json
  "powershell.integratedConsole.focusConsoleOnExecute": false
  ```

  기본값은 액세스 가능성을 위해 `true`가 됩니다.

- 시작 시 통합 콘솔을 시작하지 않음

  시작 시 통합 콘솔을 중지하려면 다음을 설정합니다.

  ```json
  "powershell.integratedConsole.showOnStartup": false
  ```

  > [!NOTE]
  > 백그라운드 PowerShell 프로세스는 IntelliSense, 스크립트 분석, 기호 탐색 등을 계속 제공하지만 콘솔은 표시되지 않습니다.

- 파일이 기본적으로 PowerShell이라고 가정합니다.

  새/제목 없는 파일을 만들려면 기본적으로 PowerShell로 등록합니다.

  ```json
  "files.defaultLanguage": "powershell",
  ```

- 색 구성표

  VS Code에서 편집기 모양을 ISE와 훨씬 더 비슷하게 설정하는 데 사용할 수 있는 다양한 ISE 테마가 있습니다.

  [명령 팔레트][]에 `theme`를 입력하여 `Preferences: Color Theme`를 가져오고 <kbd>Enter</kbd> 키를 누릅니다. 드롭다운 목록에서 `PowerShell ISE`를 선택합니다.

  다음을 사용하여 설정에서 이 테마를 설정할 수 있습니다.

  ```json
  "workbench.colorTheme": "PowerShell ISE",
  ```

- PowerShell Command Explorer

  [@corbob](https://github.com/corbob)의 작업 덕분에 PowerShell 확장에는 고유한 초기 명령 탐색기가 있습니다.

  [명령 팔레트][]에 `PowerShell Command Explorer`를 입력하고 <kbd>Enter</kbd> 키를 누릅니다.

- ISE에서 열기

  그래도 Windows PowerShell ISE에서 파일을 열려면 [명령 팔레트][]를 열고 "open in ise"를 검색한 다음 **PowerShell을 선택합니다. PowerShell ISE**에서 현재 파일을 엽니다.

## <a name="other-resources"></a>기타 리소스

- 4sysops에는 VS Code를 ISE와 더 유사하게 구성하는 방법에 대한 [유용한 문서][4sysops]가 있습니다.
- Mike F Robbins는 VS Code 설정에 대한 [유용한 게시물][mikefrobbins]을 제공합니다.
<!-- - Learn PowerShell has [an excellent write up][learnpwsh] setup for PowerShell. -->

## <a name="vs-code-tips"></a>VS Code 팁

- 명령 팔레트

  명령 팔레트는 VS Code에서 명령을 실행할 수 있는 편리한 방법입니다. macOS에서 <kbd>F1</kbd> 또는 <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> 또는 <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>를 사용하여 명령 팔레트를 엽니다.

  자세한 내용은 [VS Code 설명서][vsc-docs]를 참조하세요.

- 디버그 콘솔 사용 안 함

  PowerShell 스크립팅에 VS Code만 사용하도록 계획한 경우 PowerShell 확장에서 사용되지 않으므로 **디버그 콘솔**을 숨길 수 있습니다. 이렇게 하려면 마우스 오른쪽 단추로 **디버그 콘솔**을 클릭한 다음 확인 표시를 클릭하여 숨깁니다.

## <a name="more-settings"></a>추가 설정

ISE 사용자가 더 친숙하게 느끼도록 VS Code를 설정하는 더 많은 방법을 알고 있다면 이 문서에 참여하세요. 찾고 있는 호환성 구성이 있지만 해당 구성을 사용하도록 설정하는 방법을 찾을 수 없으면 [문제를 열고][] 모든 궁금한 사항을 질문하세요.

PR 및 참여도 언제든지 환영합니다.

<!-- link references -->
[vsc-docs]: https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette
[명령 팔레트]: #vs-code-tips
[문제 열기]: https://github.com/PowerShell/VSCode-powershell/issues/new/choose

[4sysops]: https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/
[mikefrobbins]: https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/
[learnpwsh]: https://www.learnpwsh.com/setup-vs-code-for-powershell/
