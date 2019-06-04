---
title: PowerShell 개발에 Visual Studio 코드 사용
description: PowerShell 개발에 Visual Studio 코드 사용
ms.date: 08/06/2018
ms.openlocfilehash: 5badffd49252e0d72ae2c20d3147ad4b1e92d5ed
ms.sourcegitcommit: cf1a281cce9f7239c440c90f8b2798d32a13778d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65882566"
---
# <a name="using-visual-studio-code-for-powershell-development"></a>PowerShell 개발에 Visual Studio 코드 사용

[PowerShell ISE][ise] 외에 PowerShell도 Visual Studio Code에서 원활하게 지원됩니다.
또한 ISE는 PowerShell Core에 지원되지 않지만 Visual Studio Code는 모든 플랫폼(Windows, macOS 및 Linux)의 PowerShell Core에 지원됩니다.

Windows 10을 사용하거나 하위 수준의 Windows OS(예: Windows 8.1 등)에 [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395)을 설치하여 PowerShell 버전 5와 Windows의 Visual Studio Code를 함께 사용할 수 있습니다.

시작하기 전에 시스템에 PowerShell이 있는지 확인하시기 바랍니다.
Windows, macOS 및 Linux의 현대식 워크로드의 경우 다음을 참조하세요.

- [Linux에서 PowerShell Core 설치][install-pscore-linux]
- [macOS에서 PowerShell Core 설치][install-pscore-macos]
- [Windows에서 PowerShell Core 설치][install-pscore-windows]

기존 Windows PowerShell 워크로드의 경우 [Windows PowerShell 설치][install-winps]를 참조하세요.

## <a name="editing-with-visual-studio-code"></a>Visual Studio Code로 편집

### <a name="1-installing-visual-studio-codehttpscodevisualstudiocomdocssetupsetup-overview"></a>[1. Visual Studio Code 설치](https://code.visualstudio.com/Docs/setup/setup-overview)

- **Linux**: [Linux에서 VS Code 실행](https://code.visualstudio.com/docs/setup/linux) 페이지의 설치 지침을 따릅니다.

- **macOS**: [macOS에서 VS Code 실행](https://code.visualstudio.com/docs/setup/mac) 페이지의 설치 지침을 따릅니다.

  > [!IMPORTANT]
  > macOS에서 PowerShell 확장이 제대로 작동하려면 OpenSSL을 설치해야 합니다.
  > 이를 위한 가장 쉬운 방법은 [Homebrew](https://brew.sh/)를 설치한 후 `brew install openssl`을 실행하는 것입니다.
  > 이제 VS Code는 PowerShell 확장을 로드할 수 있습니다.

- **Windows**: [Windows에서 VS Code 실행](https://code.visualstudio.com/docs/setup/windows) 페이지의 설치 지침을 따릅니다.

### <a name="2-installing-powershell-extension"></a>2. PowerShell 확장 설치

- 다음과 같은 방법으로 Visual Studio Code 앱을 시작합니다.
  - **Windows**: PowerShell 세션에서 `code` 입력
  - **Linux**: 터미널에서 `code` 입력
  - **macOS**: 터미널에서 `code` 입력

- **Ctrl+P**(Mac에서는 **Cmd+P**)를 눌러 **Quick Open**을 시작합니다.
- Quick Open에서 `ext install powershell`을 입력하고 **Enter** 키를 누릅니다.
- 사이드바에 **확장** 보기가 열립니다. Microsoft의 PowerShell 확장을 선택합니다.
  아래와 비슷한 결과가 나타납니다.

  ![VSCode](../../images/vscode.png)

- Microsoft의 PowerShell 확장에서 **설치** 단추를 클릭합니다.
- 설치 후 **설치** 단추가 **다시 로드**로 바뀌는 것을 볼 수 있습니다.
  **다시 로드**를 클릭합니다.
- Visual Studio Code가 다시 로드되면 편집할 준비가 된 것입니다.

예를 들어 새 파일을 만들려면 **파일->새로 만들기**를 클릭합니다.
저장하려면 **파일->저장**을 클릭한 후 파일 이름을 지정합니다(예: `HelloWorld.ps1`).
파일을 닫으려면 파일 이름 옆에 있는 "x"를 클릭합니다.
Visual Studio Code를 종료하려면 **파일->종료**를 누릅니다.

### <a name="installing-the-powershell-extension-on-restricted-systems"></a>제한된 시스템에 PowerShell 확장 설치

일부 시스템은 모든 코드 서명을 확인하여 시스템에서 실행될 PowerShell Editor Services를 수동으로 승인해야 하는 방식으로 설정됩니다.
PowerShell 확장을 설치했지만 다음과 같은 오류에 도달하는 경우 실행 정책을 변경하는 그룹 정책 업데이트가 원인일 수 있습니다.

```
Language server startup failed.
```

PowerShell Editor Services를 수동으로 승인하여 VSCode용 PowerShell 확장을 수동으로 승인하려면 PowerShell 프롬프트를 열고 다음을 실행합니다.

```powershell
Import-Module $HOME\.vscode\extensions\ms-vscode.powershell*\modules\PowerShellEditorServices\PowerShellEditorServices.psd1
```

"이 신뢰되지 않은 게시자가 서명한 소프트웨어를 실행하시겠습니까?"가 포함된 메시지가 표시됩니다.
`R`을 입력하여 파일을 실행합니다. 그런 다음, Visual Studio Code를 열고 PowerShell 확장이 제대로 작동하는지 확인합니다. 그래도 시작하는 데 문제가 있으면 [GitHub](https://github.com/PowerShell/vscode-powershell/issues)에서 알려 주세요.

#### <a name="choosing-a-version-of-powershell-to-use-with-the-extension"></a>확장과 함께 사용할 PowerShell 버전 선택

Windows PowerShell과 함께 PowerShell Core를 side-by-side 설치하면 PowerShell 확장과 함께 특정 버전의 PowerShell을 사용할 수 있습니다. 다음 단계에 따라 해당 버전을 선택합니다.

1. 명령 팔레트를 엽니다(Windows 및 Linux의 경우 <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>, macOS의 경우 <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>).
1. "세션"을 검색합니다.
1. "PowerShell: 세션 메뉴 표시"를 클릭합니다.
1. 목록에서 사용하려는 PowerShell 버전을 선택합니다(예: “PowerShell Core”).

>[!IMPORTANT]
> 이 기능은 운영 체제별로 몇 가지 잘 알려진 경로를 확인하여 PowerShell의 설치 위치를 검색합니다. 일반적이지 않은 위치에 PowerShell을 설치한 경우 처음에 PowerShell이 세션 메뉴에 표시되지 않을 수 있습니다. 아래 설명된 대로 [사용자 지정 경로를 추가](#adding-your-own-powershell-paths-to-the-session-menu)하여 세션 메뉴를 확장할 수 있습니다.

>[!NOTE]
> 세션 메뉴에 액세스하는 또 다른 방법이 있습니다. PowerShell 파일이 편집기에서 열리면 오른쪽 아래에 녹색 버전 번호가 표시됩니다. 이 버전 번호를 클릭하면 세션 메뉴로 이동됩니다.

##### <a name="adding-your-own-powershell-paths-to-the-session-menu"></a>세션 메뉴에 고유한 PowerShell 경로 추가

VS Code 설정을 통해 세션 메뉴에 다른 PowerShell 실행 파일 경로를 추가할 수 있습니다.

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

* `exePath`: `pwsh` 또는 `powershell` 실행 파일의 경로입니다.
* `versionName`: 세션 메뉴에 표시되는 텍스트입니다.

`powershell.powerShellDefaultVersion` 설정을 세션 메뉴에 표시되는 텍스트(마지막 설정의 `versionName`)로 설정하여 이 설정을 통해 사용하도록 기본 PowerShell 버전을 설정할 수 있습니다.

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

이 설정을 지정한 후 Visual Studio Code를 다시 시작하거나 "개발자: 창 다시 로드" 명령 팔레트 작업을 사용하여 현재 vscode 창을 다시 로드합니다.

세션 메뉴를 열면 이제 추가 PowerShell 버전이 표시됩니다.

> [!NOTE]
> 원본에서 PowerShell을 빌드하는 경우 이 방법은 PowerShell의 로컬 빌드를 테스트하는 좋은 방법입니다.

#### <a name="configuration-settings-for-visual-studio-code"></a>Visual Studio Code에 대한 구성 파일

이전 단락의 단계를 따라 `settings.json`에 구성 설정을 추가할 수 있습니다.

Visual Studio Code에는 다음 구성 설정을 권장합니다.

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

이러한 설정이 모든 파일 형식에 영향을 주지 않으려는 경우 VSCode에서 언어별 구성을 허용할 수도 있습니다. `[<language-name>]` 필드에서 설정을 지정하여 언어별 설정을 만듭니다. 예:

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

VS Code의 파일 인코딩에 대한 자세한 내용은 [파일 인코딩 이해](understanding-file-encoding.md)를 참조하세요.

## <a name="debugging-with-visual-studio-code"></a>Visual Studio Code 디버깅

### <a name="no-workspace-debugging"></a>작업 공간 없이 디버깅

Visual Studio Code 버전 1.9부터 PowerShell 스크립트가 포함된 폴더를 열지 않고도 PowerShell 스크립트를 디버깅할 수 있습니다. **파일->파일 열기...** 로 PowerShell 스크립트 파일을 열고 특정 줄에 중단점을 설정한 후(F9 키 누름) F5 키를 눌러 디버깅을 시작합니다. 디버거, 단계, 디버깅 다시 시작 및 중지로 나눌 수 있는 디버그 작업 창이 표시됩니다.

### <a name="workspace-debugging"></a>작업 영역에서 디버깅

작업 영역에서 디버깅은 Visual Studio Code의 **파일** 메뉴에서 **폴더 열기...** 를 사용하여 연 폴더의 컨텍스트에서 디버깅하는 것을 말합니다.
사용자가 여는 폴더는 일반적으로 PowerShell 프로젝트 폴더 및/또는 Git 리포지토리의 루트입니다.

이 모드에서도 간단히 F5 키만 눌러 현재 선택된 PowerShell 스크립트의 디버깅을 시작할 수 있습니다.
그러나 작업 영역에서 디버깅을 사용하면 현재 열려 있는 파일만 디버깅하는 것이 아니라 여러 디버그 구성도 정의할 수 있습니다.
예를 들어 다음을 위한 구성을 추가할 수 있습니다.

- 디버거에서 Pester 테스트 시작
- 디버거에서 인수를 갖는 특정 파일 시작
- 디버거에서 대화형 세션 시작
- PowerShell 호스트 프로세스에 디버거 연결

디버그 구성 파일을 만들려면 다음 단계를 수행합니다.

  1. **Ctrl+Shift+D**(Mac에서는 **Cmd+Shift+D**)를 눌러 **디버그** 보기를 엽니다.
  2. 도구 모음에서 **구성** 기어 아이콘을 누릅니다.
  3. Visual Studio Code에서 **환경 선택**에 대한 메시지가 표시됩니다. **PowerShell**을 선택합니다.

  그러면 Visual Studio Code에서 작업 영역 폴더의 루트에 ".vscode\launch.json"이라는 파일과 디렉터리를 만듭니다.
  여기에 디버그 구성이 저장됩니다. 파일이 Git 리포지토리에 있을 경우 일반적으로 launch.json 파일을 커밋하는 것이 좋습니다.
  launch.json 파일의 내용은 다음과 같습니다.

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

  이는 일반적인 디버그 시나리오를 나타냅니다.
  그러나 편집기에서 이 파일을 열면 **구성 추가...** 단추가 표시됩니다.
  이 단추를 눌러 더 많은 PowerShell 디버그 구성을 추가할 수 있습니다. 한 가지 간편한 구성은 **PowerShell: 스크립트 시작**입니다.
  이 구성을 사용하면 편집기에서 현재 어떤 파일이 활성화되어 있는지 관계없이 F5 키를 누를 때마다 시작되어야 하는 선택적 인수를 갖는 특정 파일을 지정할 수 있습니다.

  디버그 구성이 설정되면 **디버그** 보기의 도구 모음에 있는 디버그 구성 드롭다운에서 항목을 선택하여 디버그 세션 중에 사용할 구성을 선택할 수 있습니다.

Visual Studio Code에 대한 PowerShell 확장 사용을 시작하는 데 도움이 되는 몇 가지 블로그가 있습니다.

- [PowerShell 확장][ps-extension]
- [Visual Studio Code에서 PowerShell 스크립트 작성 및 디버깅][debug]
- [Visual Studio Code 디버깅 지침][vscode-guide]
- [Visual Studio Code에서 PowerShell 디버깅][ps-vscode]
- [Visual Studio Code에서 PowerShell 개발 시작][getting-started]
- [PowerShell 개발을 위한 Visual Studio Code 편집 기능 – 1부][editing-part1]
- [PowerShell 개발을 위한 Visual Studio Code 편집 기능 – 2부][editing-part2]
- [Visual Studio Code에서 PowerShell 스크립트 디버깅 – 1부][debugging-part1]
- [Visual Studio Code에서 PowerShell 스크립트 디버깅 – 2부][debugging-part2]

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

## <a name="powershell-extension-for-visual-studio-code"></a>Visual Studio Code용 PowerShell 확장

PowerShell 확장의 소스 코드는 [GitHub](https://github.com/PowerShell/vscode-powershell)에서 확인할 수 있습니다.
