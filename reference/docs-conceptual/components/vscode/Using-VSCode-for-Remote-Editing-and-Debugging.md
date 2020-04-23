---
title: Visual Studio Code를 사용하여 원격 편집 및 디버깅
description: Visual Studio Code를 사용하여 원격 편집 및 디버깅
ms.date: 06/13/2019
ms.openlocfilehash: 5ce7f575d90ff47fd6b8a0a2b567e972ec3a9fef
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2020
ms.locfileid: "78279168"
---
# <a name="using-visual-studio-code-for-remote-editing-and-debugging"></a>Visual Studio Code를 사용하여 원격 편집 및 디버깅

ISE에 친숙한 사용자는 통합 콘솔에서 `psedit file.ps1`을 실행하여 ISE에서 바로 로컬 또는 원격 파일을 열 수 있다는 것을 기억할 것입니다.

이 기능은 VSCode용 PowerShell 확장에서도 사용할 수 있습니다. 이 가이드에서는 수행 방법을 보여 줍니다.

## <a name="prerequisites"></a>사전 요구 사항

이 가이드에서는 다음이 준비되어 있다고 가정합니다.

- 액세스할 수 있는 원격 리소스(예: VM, 컨테이너)
- 해당 리소스를 실행하는 PowerShell 및 호스트 머신
- VSCode 및 VSCode용 PowerShell 확장

이 기능은 Windows PowerShell 및 PowerShell Core에서 작동합니다.

이 기능은 WinRM, PowerShell Direct 또는 SSH를 통해 원격 컴퓨터에 연결할 경우에도 작동합니다. Windows를 사용 중이지만 SSH를 사용하려면 [Win32 버전의 SSH](https://github.com/PowerShell/Win32-OpenSSH)를 확인합니다.

> [!IMPORTANT]
> `Open-EditorFile` 및 `psedit` 명령은 VSCode용 PowerShell 확장으로 만든 **PowerShell 통합 콘솔**에서만 작동합니다.

## <a name="usage-examples"></a>사용 예

이 예제에서는 Azure에서 실행되는 Ubuntu VM에 대한 내 MacBook Pro의 원격 편집 및 디버깅을 보여줍니다. 프로세스는 Windows와 동일합니다.

### <a name="local-file-editing-with-open-editorfile"></a>Open-EditorFile을 사용한 로컬 파일 편집

VSCode용 PowerShell 확장을 시작하고 PowerShell 통합 콘솔을 연 상태에서 `Open-EditorFile foo.ps1` 또는 `psedit foo.ps1`을 입력하여 편집기에서 바로 로컬 foo.ps1 파일을 열 수 있습니다.

![Open-EditorFile foo.ps1은 로컬에서 작동함](media/Using-VSCode-for-Remote-Editing-and-Debugging/1-open-local-file.png)

>[!NOTE]
> `foo.ps1` 파일이 이미 있어야 합니다.

이 상태에서 다음을 수행할 수 있습니다.

- 여백에 중단점 추가

  ![여백에 중단점 추가](media/Using-VSCode-for-Remote-Editing-and-Debugging/2-adding-breakpoint-gutter.png)

- F5 키를 눌러 PowerShell 스크립트를 디버깅합니다.

  ![PowerShell 로컬 스크립트 디버깅](media/Using-VSCode-for-Remote-Editing-and-Debugging/3-local-debug.png)

디버깅하는 동안 디버그 콘솔을 조작하고, 왼쪽 범위의 변수 및 모든 기타 표준 디버깅 도구를 확인할 수 있습니다.

### <a name="remote-file-editing-with-open-editorfile"></a>Open-EditorFile을 사용한 원격 파일 편집

이제 원격 파일 편집 및 디버깅을 살펴보겠습니다. 단계는 거의 동일하고, 먼저 수행해야 하는 하나의 작업은 원격 서버에 대한 PowerShell 세션을 시작하는 것뿐입니다.

이 작업을 수행할 cmdlet이 있습니다. 이 cmdlet을 `Enter-PSSession`라고 합니다.

cmdlet에 대한 간략한 설명은 다음과 같습니다.

- `Enter-PSSession -ComputerName foo`는 WinRM을 통해 세션을 시작함
- `Enter-PSSession -ContainerId foo` 및 `Enter-PSSession -VmId foo`는 PowerShell Direct를 통해 세션을 시작함
- `Enter-PSSession -HostName foo`는 SSH를 통해 세션을 시작함

자세한 내용은 [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession)의 설명서를 참조하세요.

macOS에서 Azure의 Ubuntu VM로 이동 중이므로 원격에 SSH를 사용합니다.

첫째, 통합 콘솔에서 `Enter-PSSession`을 실행합니다. `[<hostname>]`이 프롬프트 왼쪽에 표시되면 원격 세션에 연결된 것입니다.

![Enter-PSSession 호출](media/Using-VSCode-for-Remote-Editing-and-Debugging/4-enter-pssession.png)

이제 로컬 스크립트를 편집하는 것처럼 같은 단계를 수행할 수 있습니다.

1. `Open-EditorFile test.ps1` 또는 `psedit test.ps1`을 실행하여 원격 `test.ps1` 파일을 엽니다.

  ![Open-EditorFile test.ps1 파일](media/Using-VSCode-for-Remote-Editing-and-Debugging/5-open-remote-file.png)

1. 파일 편집/중단점 설정

   ![중단점 편집 및 설정](media/Using-VSCode-for-Remote-Editing-and-Debugging/6-set-breakpoints.png)

1. 원격 파일 디버그 시작(F5)

   ![원격 파일 디버깅](media/Using-VSCode-for-Remote-Editing-and-Debugging/7-start-debugging.png)

문제가 있는 경우 [GitHub 리포지토리](https://github.com/powershell/vscode-powershell)에서 문제를 시작할 수 있습니다.
