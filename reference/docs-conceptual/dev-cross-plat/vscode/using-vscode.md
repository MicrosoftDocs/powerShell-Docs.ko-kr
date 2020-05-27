---
title: PowerShell 개발에 Visual Studio 코드 사용
description: PowerShell 개발에 Visual Studio 코드 사용
ms.date: 11/07/2019
ms.openlocfilehash: b492e59f340f4cec92c177ad44bbab9dc95da5da
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/23/2020
ms.locfileid: "83808859"
---
# <a name="using-visual-studio-code-for-powershell-development"></a>PowerShell 개발에 Visual Studio 코드 사용

[Visual Studio Code][vscode]는 Microsoft의 플랫폼 간 스크립트 편집기입니다. [PowerShell 확장][psext]과 함께 풍부한 대화형 스크립트 편집 환경을 제공하므로 안정적인 PowerShell 스크립트를 더 쉽게 작성할 수 있습니다. PowerShell 확장이 있는 Visual Studio Code는 PowerShell 스크립트 작성을 위한 권장 편집기입니다.

지원하는 PowerShell 버전은 다음과 같습니다.

- PowerShell 7 이상(Windows, macOS 및 Linux)
- PowerShell Core 6(Windows, macOS 및 Linux)
- Windows PowerShell 5.1(Windows 전용)

> [!NOTE]
> Visual Studio Code는 [Visual Studio][]와는 다릅니다.

## <a name="getting-started"></a>시작

시작하기 전에 시스템에 PowerShell이 있는지 확인합니다. Windows, macOS 및 Linux에서 최신 작업을 수행하려면 다음 링크를 참조하세요.

- [Linux에 PowerShell 설치][install-pscore-linux]
- [macOS에 PowerShell 설치][install-pscore-macos]
- [Windows에 PowerShell 설치][install-pscore-windows]

기존 Windows PowerShell 워크로드의 경우 [Windows PowerShell 설치][install-winps]를 참조하세요.

> [!IMPORTANT]
> [Windows PowerShell ISE][ise]는 여전히 Windows에서 사용할 수 있습니다. 하지만 더 이상 활성 기능 개발에 필요하지 않습니다. ISE는 PowerShell 6 이상에서 작동하지 않습니다. Windows의 구성 요소로서 보안 및 우선 순위가 높은 서비스 수정 사항을 위해 공식적으로 계속 지원됩니다.
> Windows에서 ISE를 제거할 계획은 없습니다.

## <a name="editing-with-visual-studio-code"></a>Visual Studio Code로 편집

1. Visual Studio Code를 설치합니다. 자세한 내용은 [Visual Studio Code 설치][vsc-setup] 개요를 참조하세요.

   각 플랫폼에 대한 설치 지침은 다음과 같습니다.

   - **Windows**: [Windows에서 Visual Studio Code 실행][vsc-setup-win] 페이지의 설치 지침을 따릅니다.
   - **macOS**: [macOS에서 Visual Studio Code 실행][vsc-setup-macOS] 페이지의 설치 지침을 따릅니다.
   - **Linux**: [Linux에서 Visual Studio Code 실행][vsc-setup-linux] 페이지의 설치 지침을 따릅니다.

1. PowerShell 확장을 설치합니다.

   1. 콘솔 또는 `code-insiders`(Visual Studio Code Insiders를 설치한 경우)에 `code`를 입력하여 Visual Studio Code 앱을 시작합니다.
   1. <kbd>Ctrl</kbd>+<kbd>P</kbd>를 눌러 Windows 또는 Linux에서 **Quick Open**을 시작합니다. macOS에서 <kbd>Cmd</kbd>+<kbd>P</kbd>를 누릅니다.
   1. Quick Open에서 `ext install powershell`을 입력하고**Enter** 키를 누릅니다.
   1. 사이드바에 **확장** 보기가 열립니다. Microsoft의 PowerShell 확장을 선택합니다.
      다음 이미지와 비슷한 Visual Studio Code 화면이 표시됩니다.

      ![Visual Studio Code](media/using-vscode/vscode.png)

   1. Microsoft의 PowerShell 확장에서 **설치** 단추를 클릭합니다.
   1. 설치 후 **설치** 단추가 **다시 로드**로 바뀌면 **다시 로드**를 클릭합니다.
   1. Visual Studio Code가 다시 로드되면 편집할 준비가 된 것입니다.

예를 들어 새 파일을 만들려면 **파일 > 새로 만들기**를 클릭합니다. 저장하려면 **파일 > 저장**을 클릭한 후 파일 이름을 제공합니다(예: `HelloWorld.ps1`). 파일을 닫으려면 파일 이름 옆에 있는 `X`를 클릭합니다. Visual Studio Code를 종료하려면 **파일 > 종료**를 누릅니다.

### <a name="installing-the-powershell-extension-on-restricted-systems"></a>제한된 시스템에 PowerShell 확장 설치

일부 시스템은 모든 코드 서명의 유효성 검사를 요구하도록 설정되어 있습니다. 다음 오류 메시지가 표시될 수 있습니다.

```
Language server startup failed.
```

Windows 그룹 정책에서 PowerShell의 실행 정책이 설정된 경우 이 문제가 발생할 수 있습니다. PowerShell Editor Services를 수동으로 승인하여 Visual Studio Code용 PowerShell 확장을 수동으로 승인하려면 PowerShell 프롬프트를 열고 다음을 실행합니다.

```powershell
Import-Module $HOME\.vscode\extensions\ms-vscode.powershell*\modules\PowerShellEditorServices\PowerShellEditorServices.psd1
```

**이 신뢰되지 않은 게시자가 서명한 소프트웨어를 실행하시겠습니까?** 가 포함된 메시지가 표시됩니다. `A`을 입력하여 파일을 실행합니다. 그런 다음, Visual Studio Code를 열고 PowerShell 확장이 제대로 작동하는지 확인합니다. 그래도 시작하는 데 문제가 있으면 [GitHub 문제][]에서 알려주세요.

> [!NOTE]
> Visual Studio Code용 PowerShell 확장은 제한된 언어 모드에서의 실행을 지원하지 않습니다. 자세한 내용은 [GitHub 문제 #606][i606]을 참조하세요.

### <a name="choosing-a-version-of-powershell-to-use-with-the-extension"></a>확장과 함께 사용할 PowerShell 버전 선택

Windows PowerShell과 함께 PowerShell Core를 side-by-side 설치하면 PowerShell 확장과 함께 특정 버전의 PowerShell을 사용할 수 있습니다. 이 기능은 다른 운영 체제에서 몇 가지 잘 알려진 경로를 확인하여 PowerShell의 설치 위치를 검색합니다.

다음 단계에 따라 해당 버전을 선택합니다.

1. Windows 또는 Linux에서 <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>를 눌러 **명령 팔레트**를 엽니다. macOS에서 <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>를 누릅니다.
1. **세션**을 검색합니다.
1. **PowerShell: 세션 메뉴 표시**를 클릭합니다.
1. 목록에서 사용하려는 PowerShell 버전을 선택합니다(예: **PowerShell Core**).

일반적이지 않은 위치에 PowerShell을 설치한 경우 처음에 PowerShell이 세션 메뉴에 표시되지 않을 수 있습니다. 아래 설명된 대로 [사용자 지정 경로를 추가](#adding-your-own-powershell-paths-to-the-session-menu)하여 세션 메뉴를 확장할 수 있습니다.

> [!NOTE]
> PowerShell 세션 메뉴는 상태 표시줄의 오른쪽 아래에 있는 녹색 버전 번호에서 액세스할 수도 있습니다. 이 버전 번호를 클릭하면 세션 메뉴가 열립니다.

## <a name="configuration-settings-for-visual-studio-code"></a>Visual Studio Code에 대한 구성 파일

먼저, Visual Studio Code에서 설정을 변경하는 방법에 익숙하지 않은 경우 [Visual Studio Code 설정 설명서][vsc-settings]를 읽어보는 것이 좋습니다.

설명서를 읽은 후 `settings.json`에서 구성 설정을 추가할 수 있습니다.

```json
{
    "editor.renderWhitespace": "all",
    "editor.renderControlCharacters": true,
    "files.trimTrailingWhitespace": true,
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

이러한 설정이 모든 파일 형식에 영향을 주지 않으려는 경우 Visual Studio Code에서 언어별 구성을 허용할 수도 있습니다. `[<language-name>]` 필드에서 설정을 지정하여 언어별 설정을 만듭니다. 다음은 그 예입니다.

```json
{
    "[powershell]": {
        "files.encoding": "utf8bom",
        "files.autoGuessEncoding": true
    }
}
```

> [!TIP]
> Visual Studio Code의 파일 인코딩에 대한 자세한 내용은 [파일 인코딩 이해][file-encoding]를 참조하세요.
>
> PowerShell 편집을 위해 Visual Studio Code를 구성하는 방법에 대한 다른 팁은 [Visual Studio Code에서 ISE 환경을 복제하는 방법][vsc-ise]을 참조하세요.

### <a name="adding-your-own-powershell-paths-to-the-session-menu"></a>세션 메뉴에 고유한 PowerShell 경로 추가

[Visual Studio Code 설정](https://code.visualstudio.com/docs/getstarted/settings)을 통해 세션 메뉴에 다른 PowerShell 실행 파일 경로를 추가할 수 있습니다. `powershell.powerShellAdditionalExePaths`.

`powershell.powerShellAdditionalExePaths` 목록에 항목을 추가하거나, 목록이 `settings.json`에 없는 경우 목록을 만듭니다.

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

각 항목은 다음을 포함해야 합니다.

- `exePath`: `pwsh` 또는 `powershell` 실행 파일의 경로입니다.
- `versionName`: 세션 메뉴에 표시되는 텍스트입니다.

기본 PowerShell 버전을 설정하려면 `powershell.powerShellDefaultVersion` 값을 세션 메뉴에 표시된 텍스트(`versionName`이라고도 함)로 설정합니다.

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

이 설정을 구성한 후에는 Visual Studio Code를 다시 시작합니다. 또는 **명령 팔레트**에서 현재 Visual Studio Code 창을 다시 로드하려면 **Developer: Reload Window**를 입력합니다.

세션 메뉴를 열면 이제 추가 PowerShell 버전이 표시됩니다.

> [!NOTE]
> 원본에서 PowerShell을 빌드하는 경우 이 방법은 PowerShell의 로컬 빌드를 테스트하는 좋은 방법입니다.

### <a name="using-an-older-version-of-the-powershell-extension-for-windows-powershell-v3-and-v4"></a>Windows PowerShell v3 및 v4를 위해 이전 버전의 PowerShell 확장 사용

현재 PowerShell 확장은 [PowerShell v3 및 v4][i1310]를 지원하지 않습니다. 하지만 PowerShell v3 및 v4를 지원하는 최신 버전의 확장을 사용할 수 있습니다.

> [!CAUTION]
> 이 이전 버전의 확장에 대한 추가 수정 사항은 없습니다. 이 버전은 "있는 그대로" 제공되지만 Windows PowerShell v3 및 Windows PowerShell v4를 여전히 사용하고 있다면 이 버전을 사용할 수 있습니다.

먼저 확장 창을 열고 `PowerShell`을 검색합니다. 그런 다음 기어 아이콘을 클릭하고 **다른 버전 설치...** 를 선택합니다.

![다른 버전 설치...](media/using-vscode/install-another-version.png)

그런 다음 **2020.1.0** 버전을 선택합니다. 이 확장 버전은 마지막으로 v3 및 v4를 지원한 버전이었습니다. 확장 버전이 자동으로 업데이트되지 않도록 다음 설정을 추가합니다.

```json
{
    "extensions.autoUpdate": false
}
```

**2020.1.0** 버전은 가까운 미래에 제공됩니다. 하지만 Visual Studio Code에서 이 확장 버전을 중단하는 변경이 구현될 수 있습니다. 이러한 이유로 지원이 되지 않기 때문에 다음을 권장합니다.

- Windows PowerShell 5.1로 업그레이드
- PowerShell 7 설치는 Windows PowerShell과 함께 설치되며 PowerShell 확장에서 가장 잘 작동합니다.

## <a name="debugging-with-visual-studio-code"></a>Visual Studio Code 디버깅

### <a name="no-workspace-debugging"></a>작업 공간 없이 디버깅

Visual Studio Code 버전 1.9 이상에서는 PowerShell 스크립트가 포함된 폴더를 열지 않고도 PowerShell 스크립트를 디버그할 수 있습니다.

1. **파일 > 파일 열기...** 를 사용하여 PowerShell 스크립트 파일 열기
1. 중단점 설정 - 줄을 선택한 다음 <kbd>F9</kbd> 키 누름
1. <kbd>F5</kbd> 키를 눌러 디버깅 시작

디버거, 단계, 디버깅 다시 시작 및 중지로 나눌 수 있는 디버그 작업 창이 표시됩니다.

### <a name="workspace-debugging"></a>작업 영역에서 디버깅

작업 영역에서 디버깅은 **파일** 메뉴에서 **폴더 열기...** 를 사용하여 연 폴더의 컨텍스트에서 디버깅하는 것을 말합니다. 사용자가 여는 폴더는 일반적으로 PowerShell 프로젝트 폴더 또는 Git 리포지토리의 루트입니다. 작업 영역에서 디버깅을 사용하면 현재 열려 있는 파일만 디버깅하는 것이 아니라 여러 디버그 구성도 정의할 수 있습니다.

디버그 구성 파일을 만들려면 다음 단계를 수행합니다.

1. <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>를 눌러 Windows 또는 Linux에서 **디버그** 보기를 엽니다. macOS에서 <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>를 누릅니다.
1. **launch.json 파일 만들기** 링크를 클릭합니다.
1. **환경 선택** 프롬프트에서 **PowerShell**을 선택합니다.
1. 사용할 디버깅 형식을 선택합니다.

   - **현재 파일 시작** - 현재 활성화된 편집기 창에서 파일을 시작 및 디버그
   - **스크립트 실행** - 지정된 파일 또는 명령을 실행 및 디버그
   - **대화형 세션** - 통합 콘솔에서 실행된 디버그 명령
   - **연결** - 실행 중인 PowerShell 호스트 프로세스에 디버거를 연결

Visual Studio Code는 작업 영역 폴더의 루트에 디렉터리와 파일 `.vscode\launch.json`을 만들어서 디버그 구성을 저장합니다. 파일이 Git 리포지토리에 있을 경우 일반적으로 `launch.json` 파일을 커밋하는 것이 좋습니다. `launch.json` 파일의 내용은 다음과 같습니다.

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

이 파일은 일반적인 디버그 시나리오를 나타냅니다. 편집기에서 이 파일을 열면 **구성 추가...** 단추가 표시됩니다. 이 단추를 클릭하여 더 많은 PowerShell 디버그 구성을 추가할 수 있습니다. 한 가지 유용한 구성은 **PowerShell: 스크립트 시작**입니다. 이 구성을 사용하면 편집기에서 어떤 파일이 활성화되어 있는지 관계없이 <kbd>F5</kbd> 키를 누를 때마다 사용되는 선택적 인수를 포함한 파일을 지정할 수 있습니다.

디버그 구성이 설정된 후에 디버그 세션 중에 사용하려는 구성을 선택할 수 있습니다. **디버그** 보기의 도구 모음에 있는 디버그 구성 드롭다운에서 구성을 선택합니다.

## <a name="troubleshooting-the-powershell-extension-for-visual-studio-code"></a>Visual Studio Code용 PowerShell 확장 문제 해결

PowerShell 스크립트 개발을 위해 Visual Studio Code를 사용하는 데 문제가 발생하는 경우 GitHub의 [문제 해결 가이드][troubleshooting]를 참조하세요.

## <a name="useful-resources"></a>유용한 리소스

Visual Studio Code에 대한 PowerShell 확장 사용을 시작하는 데 도움이 되는 몇 가지 동영상 및 블로그 게시물이 있습니다.

### <a name="videos"></a>동영상

- [기본 PowerShell 편집기로 Visual Studio Code 사용](https://youtu.be/bGn45vIeAMM)
- [Visual Studio Code: PowerShell 스크립트 디버깅 자세히 알아보기](https://youtu.be/cSbIXmlkr8o)

### <a name="blog-posts"></a>블로그 게시물

- [PowerShell 확장][pscdn]
- [Visual Studio Code에서 PowerShell 스크립트 작성 및 디버깅][debug]
- [Visual Studio Code 디버깅 지침][psdbgblog]
- [Visual Studio Code에서 PowerShell 디버깅][psdbg-gh]
- [Visual Studio Code에서 PowerShell 개발 시작][getting-started]
- [PowerShell 개발을 위한 Visual Studio Code 편집 기능 – 1부][editing-part1]
- [PowerShell 개발을 위한 Visual Studio Code 편집 기능 – 2부][editing-part2]
- [Visual Studio Code에서 PowerShell 스크립트 디버깅 – 1부][debugging-part1]
- [Visual Studio Code에서 PowerShell 스크립트 디버깅 – 2부][debugging-part2]

## <a name="powershell-extension-project-source-code"></a>PowerShell 확장 프로젝트 소스 코드

PowerShell 확장의 소스 코드는 [GitHub][psext-src]에서 확인할 수 있습니다.

참가에 관심이 있는 경우 끌어오기 요청은 언제나 환영합니다. GitHub의 [개발자 설명서][dev-docs]를 따라 시작하세요.

<!-- related articles -->
[ise]:                    ../../windows-powershell/ise/Introducing-the-Windows-PowerShell-ISE.md
[install-pscore-linux]:   ../../install/Installing-PowerShell-Core-on-Linux.md
[install-pscore-macos]:   ../../install/Installing-PowerShell-Core-on-macOS.md
[install-pscore-windows]: ../../install/Installing-PowerShell-Core-on-Windows.md
[install-winps]:          ../../install/Installing-Windows-PowerShell.md
[file-encoding]:          understanding-file-encoding.md
[vsc-ise]:                How-To-Replicate-the-ISE-Experience-In-VSCode.md

<!-- blogs -->
[debug]:                  https://devblogs.microsoft.com/powershell/announcing-powershell-language-support-for-visual-studio-code-and-more/
[debugging-part1]:        https://devblogs.microsoft.com/scripting/debugging-powershell-script-in-visual-studio-code-part-1/
[debugging-part2]:        https://devblogs.microsoft.com/scripting/debugging-powershell-script-in-visual-studio-code-part-2/
[editing-part1]:          https://devblogs.microsoft.com/scripting/visual-studio-code-editing-features-for-powershell-development-part-1/
[editing-part2]:          https://devblogs.microsoft.com/scripting/visual-studio-code-editing-features-for-powershell-development-part-2/
[getting-started]:        https://devblogs.microsoft.com/scripting/get-started-with-powershell-development-in-visual-studio-code/
[psdbgblog]:              https://johnpapa.net/debugging-with-visual-studio-code/
[psdbg-gh]:               https://github.com/PowerShell/vscode-powershell/tree/master/examples
[pscdn]:                  https://blogs.msdn.microsoft.com/cdndevs/2015/12/11/visual-studio-code-powershell-extension/

<!-- issues -->
[GitHub 문제]:          https://github.com/PowerShell/vscode-powershell/issues
[i1310]:                  https://github.com/PowerShell/vscode-powershell/issues/1310
[i606]:                   https://github.com/PowerShell/vscode-powershell/issues/606

<!-- product links -->
[Visual Studio]:          https://visualstudio.microsoft.com/
[vscode]:                 https://code.visualstudio.com/
[psext]:                  https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell
[vsc-settings]:           https://code.visualstudio.com/docs/getstarted/settings
[vsc-setup]:              https://code.visualstudio.com/Docs/setup/setup-overview
[vsc-setup-win]:          https://code.visualstudio.com/docs/setup/windows
[vsc-setup-macos]:        https://code.visualstudio.com/docs/setup/mac
[vsc-setup-linux]:        https://code.visualstudio.com/docs/setup/linux
[psext-src]:              https://github.com/PowerShell/vscode-powershell
[troubleshooting]:        https://github.com/PowerShell/vscode-powershell/blob/master/docs/troubleshooting.md
[dev-docs]:               https://github.com/PowerShell/vscode-powershell/blob/master/docs/development.md
