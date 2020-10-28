---
ms.date: 10/19/2020
keywords: powershell,cmdlet,디버그
title: Visual Studio Code를 사용하여 컴파일된 cmdlet 디버그
description: .NET Core에서 PSModule 프로젝트에 대한 빌드 작업을 설정하고 구성을 시작하는 방법
ms.openlocfilehash: b51a69110c64b386f5c3ccf2527d1e184ef89257
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/24/2020
ms.locfileid: "92501646"
---
# <a name="using-visual-studio-code-to-debug-compiled-cmdlets"></a>Visual Studio Code를 사용하여 컴파일된 cmdlet 디버그

이 가이드에서는 VS Code(Visual Studio Code) 및 C# 확장을 사용하여 컴파일된 PowerShell 모듈의 소스 코드를 대화형으로 디버그하는 방법을 보여줍니다.

여러분이 Visual Studio Code 디버거에 대해 어느 정도 알고 있는 것으로 가정합니다.

- VS Code 디버거에 대한 일반적인 소개는 [Visual Studio Code에서 디버깅][]을 참조하세요.

- PowerShell 스크립트 파일 및 모듈을 디버깅하는 예제는 [Visual Studio Code를 사용하여 원격 편집 및 디버깅][]을 참조하세요.

이 가이드에서는 여러분이 [이식 가능한 모듈 작성][] 가이드의 지침을 읽고 수행했다고 가정합니다.

## <a name="creating-a-build-task"></a>빌드 작업 만들기

디버깅 세션을 시작하기 전에 프로젝트를 자동으로 빌드합니다. 다시 빌드하면 최신 버전의 코드를 디버그합니다.

다음과 같이 빌드 작업을 구성합니다.

1. **명령 팔레트** 에서 **기본 빌드 작업 구성** 명령을 실행합니다.

   ![기본 빌드 작업 구성 실행](media/using-vscode-for-debugging-compiled-cmdlets/configure-default-build-task.png)

1. **구성할 작업 선택** 대화 상자에서 **템플릿에서 tasks.json 파일 만들기** 를 선택합니다.

1. **작업 템플릿 선택** 대화 상자에서 **.NET Core** 를 선택합니다.

`tasks.json` 파일이 없는 경우 새로 만들어집니다.

빌드 작업을 테스트하려면 다음을 수행합니다.

1. **명령 팔레트** 에서 **빌드 작업 실행** 명령을 실행합니다.

1. **실행할 빌드 작업 선택** 대화 상자에서 **빌드** 를 선택합니다.

### <a name="information-about-dll-files-being-locked"></a>잠겨 있는 DLL 파일에 대한 정보

기본적으로 빌드가 성공하면 터미널 창에 출력이 표시되지 않습니다. **프로젝트 파일이 없습니다** 텍스트가 포함된 출력이 보이면 `tasks.json` 파일을 편집해야 합니다. `"${workspaceFolder}/myModule"`로 표현되는 C# 프로젝트의 명시적 경로를 포함합니다. 이 예제에서 `myModule`은 프로젝트 폴더의 이름입니다. 이 항목은 다음과 같이 `args` 목록에서 `build` 항목 뒤에 와야 합니다.

```json
    {
        "label": "build",
        "command": "dotnet",
        "type": "shell",
        "args": [
            "build",
            "${workspaceFolder}/myModule",
            // Ask dotnet build to generate full paths for file names.
            "/property:GenerateFullPaths=true",
            // Do not generate summary otherwise it leads to duplicate errors in Problems panel
            "/consoleloggerparameters:NoSummary",
        ],
        "group": "build",
        "presentation": {
            "reveal": "silent"
        },
        "problemMatcher": "$msCompile"
    }
```

디버깅할 때 VS Code 터미널의 PowerShell 세션으로 모듈 DLL을 가져옵니다. DLL이 잠깁니다. 터미널 세션을 닫지 않고 빌드 작업을 실행하면 다음 메시지가 표시됩니다.

```Output
Could not copy "obj\Debug\netstandard2.0\myModule.dll" to "bin\Debug\netstandard2.0\myModule.dll"`.
```

다시 빌드하기 전에 터미널 세션을 닫아야 합니다.

## <a name="setting-up-the-debugger"></a>디버거 설정

PowerShell cmdlet을 디버그하려면 사용자 지정 시작 구성을 설정해야 합니다. 이 구성은 다음 작업에 사용됩니다.

- 소스 코드 빌드
- 로드된 모듈을 사용하여 PowerShell 시작
- 터미널 창에서 PowerShell을 열어 두기

터미널 세션에서 cmdlet을 호출하면 소스 코드에 설정된 중단점에서 디버거가 중지됩니다.

### <a name="configuring-launchjson-for-powershell-core"></a>PowerShell Core에 대한 launch.json 구성

1. [C# for Visual Studio Code][] 확장을 설치합니다.

1. [디버그] 창에서 디버그 구성을 추가합니다.

1. `Select environment` 대화 상자에서 `.NET Core`를 선택합니다.

1. `launch.json` 파일이 편집기에서 열립니다. 커서가 `configurations` 배열 내에 있으면 `configuration` 선택기가 표시됩니다. 이 목록이 표시되지 않으면 **구성 추가** 를 선택합니다.

1. 기본 디버그 구성을 만들려면 **.NET Core 콘솔 앱 시작** 을 선택합니다.

   ![.NET Core 콘솔 앱 시작](media/using-vscode-for-debugging-compiled-cmdlets/add-configuration-dialog.png)

1. 다음과 같이 `name`, `program`, `args` 및 `console` 필드를 채웁니다.

   ```json
    {
        "name": "PowerShell cmdlets: pwsh",
        "type": "coreclr",
        "request": "launch",
        "preLaunchTask": "build",
        "program": "pwsh",
        "args": [
            "-NoExit",
            "-NoProfile",
            "-Command",
            "Import-Module ${workspaceFolder}/myModule/bin/Debug/netstandard2.0/myModule.dll",
        ],
        "cwd": "${workspaceFolder}",
        "stopAtEntry": false,
        "console": "integratedTerminal"
    }
   ```

`program` 필드는 디버깅 중인 cmdlet을 실행할 수 있도록 `pwsh`를 시작하는 데 사용됩니다. `-NoExit` 인수는 모듈을 가져오는 즉시 PowerShell 세션이 종료되는 것을 방지합니다.
[이식 가능한 모듈 작성][] 가이드를 수행한 경우 `Import-Module` 인수의 경로가 기본 빌드 출력 경로입니다. 모듈 매니페스트(`.psd1` 파일)를 만든 경우 해당 경로를 대신 사용해야 합니다. `/` 경로 구분 기호는 Windows, Linux 및 macOS에서 작동합니다. 디버그할 PowerShell 명령을 실행하려면 통합 터미널을 사용해야 합니다.

> [!NOTE]
> 디버거가 중단점에서 중지되지 않으면 Visual Studio Code 디버그 콘솔에서 다음과 같은 줄을 찾습니다.
>
> ```
> Loaded '/path/to/myModule.dll'. Skipped loading symbols. Module is optimized and the debugger option 'Just My Code' is enabled.
> ```
>
> 이 메시지가 보이면 `"console": "integratedTerminal"`과 동일한 수준에서 시작 구성에 `"justMyCode": false`를 추가합니다.

### <a name="configuring-launchjson-for-windows-powershell"></a>Windows PowerShell에 대한 launch.json 구성

이 시작 구성은 Windows PowerShell에서 cmdlet(`powershell.exe`)을 테스트할 때 작동합니다.
다음과 같이 변경하여 두 번째 시작 구성을 만듭니다.

1. `name`는 `PowerShell cmdlets: powershell`여야 합니다.

1. `type`는 `clr`여야 합니다.

1. `program`는 `powershell`여야 합니다.

   다음과 같이 표시됩니다.

   ```json
    {
        "name": "PowerShell cmdlets: powershell",
        "type": "clr",
        "request": "launch",
        "preLaunchTask": "build",
        "program": "powershell",
        "args": [
            "-NoExit",
            "-NoProfile",
            "-Command",
            "Import-Module ${workspaceFolder}/myModule/bin/Debug/netstandard2.0/myModule.dll",
        ],
        "cwd": "${workspaceFolder}",
        "stopAtEntry": false,
        "console": "integratedTerminal"
    }
   ```

## <a name="launching-a-debugging-session"></a>디버깅 세션 시작

이제 디버깅을 시작할 준비가 되었습니다.

- 디버그할 cmdlet의 소스 코드에 중단점을 배치합니다.

  ![중단점은 여백에 빨간색 점으로 표시](media/using-vscode-for-debugging-compiled-cmdlets/set-breakpoint.png)

- **디버그** 보기의 구성 드롭다운 메뉴에서 관련 **PowerShell cmdlet** 구성을 선택했는지 확인합니다.

  ![시작 구성 선택](media/using-vscode-for-debugging-compiled-cmdlets/select-launch-configuration.png)

- <kbd>F5</kbd> 키를 누르거나 **디버깅 시작** 단추를 클릭합니다.

- 터미널 창으로 전환하여 cmdlet을 호출합니다.

  ![cmdlet 호출](media/using-vscode-for-debugging-compiled-cmdlets/invoke-the-cmdlet.png)

- 중단점에서 실행이 중지됩니다.

  ![중단점에서 실행이 중지됨](media/using-vscode-for-debugging-compiled-cmdlets/stopped-at-breakpoint.png)

소스 코드를 단계별로 실행하고, 변수를 검사하고, 호출 스택을 검사할 수 있습니다.

디버깅을 종료하려면 디버그 도구 모음에서 **중지** 를 클릭하거나 <kbd>Shift</kbd>-<kbd>F5</kbd> 키를 누릅니다. 디버깅에 사용한 셸이 종료되고 컴파일된 DLL 파일의 잠금이 해제됩니다.

<!-- reference links -->
[Visual Studio Code의 디버깅]: https://code.visualstudio.com/docs/editor/debugging
[Visual Studio Code를 사용하여 원격 편집 및 디버깅]: using-vscode-for-remote-editing-and-debugging.md
[이식 가능한 모듈 작성]: ../writing-portable-modules.md
[Visual Studio Code용 C#]: https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp
