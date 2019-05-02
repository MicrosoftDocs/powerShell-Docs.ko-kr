---
title: Visual Studio Code를 사용하여 원격 편집 및 디버깅
description: Visual Studio Code를 사용하여 원격 편집 및 디버깅
ms.date: 08/06/2018
ms.openlocfilehash: fbc1ee3556e822b4afb2b37111d0688dc89fdab3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086677"
---
# <a name="using-visual-studio-code-for-remote-editing-and-debugging"></a>Visual Studio Code를 사용하여 원격 편집 및 디버깅

ISE에 친숙한 사용자는 통합 콘솔에서 `psedit file.ps1`을 실행하여 ISE에서 바로 로컬 또는 원격 파일을 열 수 있다는 것을 기억할 것입니다.

결과적으로 이 기능은 VSCode용 PowerShell 확장에서도 사용할 수 있습니다. 이 가이드에서는 사용 방법을 보여 줍니다.

## <a name="prerequisites"></a>필수 구성 요소

이 가이드에서는 다음이 준비되어 있다고 가정합니다.

- 액세스할 수 있는 원격 리소스(예: VM, 컨테이너)
- 해당 리소스를 실행하는 PowerShell 및 호스트 머신
- VSCode 및 VSCode용 PowerShell 확장

이 기능은 Windows PowerShell 및 PowerShell Core에서 작동합니다.

이 기능은 WinRM, PowerShell Direct 또는 SSH를 통해 원격 컴퓨터에 연결할 경우에도 작동합니다. Windows를 사용 중이지만 SSH를 사용하려면 [Win32 버전의 SSH](https://github.com/PowerShell/Win32-OpenSSH)를 확인합니다.

## <a name="lets-go"></a>다음

이 섹션에서는 Azure에서 실행되는 Ubuntu VM에 대한 내 MacBook Pro의 원격 편집 및 디버깅을 살펴보겠습니다. Windows를 사용하지 않을 수 있지만 **프로세스는 동일합니다**.

### <a name="local-file-editing-with-open-editorfile"></a>Open-EditorFile을 사용한 로컬 파일 편집

VSCode용 PowerShell 확장을 시작하고 PowerShell 통합 콘솔을 연 상태에서 `Open-EditorFile foo.ps1` 또는 `psedit foo.ps1`을 입력하여 편집기에서 바로 로컬 foo.ps1 파일을 열 수 있습니다.

![Open-EditorFile foo.ps1은 로컬에서 작동함](https://user-images.githubusercontent.com/2644648/34895897-7c2c46ac-f79c-11e7-9410-a252aff52f13.png)

>[!NOTE]
> 기존 foo.ps1이 있어야 합니다.

이 상태에서 다음을 수행할 수 있습니다.

여백에 중단점을 추가하고 ![여백에 중단점 추가](https://user-images.githubusercontent.com/2644648/34895893-7bdc38e2-f79c-11e7-8026-8ad53f9a1bad.png)

F5 키를 눌러 PowerShell 스크립트를 디버그합니다.
![PowerShell 로컬 스크립트 디버그](https://user-images.githubusercontent.com/2644648/34895894-7bedb874-f79c-11e7-9180-7e0dc2d02af8.png)

디버깅하는 동안 디버그 콘솔을 조작하고, 왼쪽 범위의 변수 및 모든 기타 표준 디버깅 도구를 확인할 수 있습니다.

### <a name="remote-file-editing-with-open-editorfile"></a>Open-EditorFile을 사용한 원격 파일 편집

이제 원격 파일 편집 및 디버깅을 살펴보겠습니다. 단계는 거의 동일하고, 먼저 수행해야 하는 하나의 작업은 원격 서버에 대한 PowerShell 세션을 시작하는 것뿐입니다.

이 작업을 수행할 cmdlet이 있습니다. 이 cmdlet을 `Enter-PSSession`라고 합니다.

cmdlet에 대한 간략한 설명은 다음과 같습니다.

- `Enter-PSSession -ComputerName foo`는 WinRM을 통해 세션을 시작함
- `Enter-PSSession -ContainerId foo` 및 `Enter-PSSession -VmId foo`는 PowerShell Direct를 통해 세션을 시작함
- `Enter-PSSession -HostName foo`는 SSH를 통해 세션을 시작함

`Enter-PSSession`에 대한 자세한 내용은 [여기서](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enter-pssession?view=powershell-6) 문서를 확인하세요.

macOS에서 Azure의 Ubuntu VM로 이동 중이므로 원격에 SSH를 사용하겠습니다.

먼저, 통합 콘솔에서 Enter-PSSession을 실행하겠습니다. `[something]`이 프롬프트의 왼쪽에 표시되므로 해당 세션에 있음을 알 수 있습니다.

![Enter-PSSession 호출](https://user-images.githubusercontent.com/2644648/34895896-7c18e0bc-f79c-11e7-9b36-6f4bd0e9b0db.png)

여기에서 로컬 스크립트를 편집하는 것처럼 정확한 단계를 수행할 수 있습니다.

1. `Open-EditorFile test.ps1` 또는 `psedit test.ps1`을 실행하여 원격 `test.ps1` 파일 ![Open-EditorFile test.ps1 파일](https://user-images.githubusercontent.com/2644648/34895898-7c3e6a12-f79c-11e7-8bdf-549b591ecbcb.png)을 엽니다.
2. 파일 편집/중단점 설정 ![중단점 편집 및 설정](https://user-images.githubusercontent.com/2644648/34895892-7bb68246-f79c-11e7-8c0a-c2121773afbb.png)
3. 원격 파일 디버그 시작(F5)

![원격 파일 디버깅](https://user-images.githubusercontent.com/2644648/34895895-7c040782-f79c-11e7-93ea-47724fa5c10d.png)

이것이 전부입니다. 이 가이드가 VSCode에서 PowerShell을 원격 디버깅 및 편집하는 작업에 관련된 모든 질문을 해결하는 데 도움이 되었기를 바랍니다.

문제가 있는 경우 [GitHub 리포지토리](http://github.com/powershell/vscode-powershell)에서 자유롭게 문제를 시작하세요.
