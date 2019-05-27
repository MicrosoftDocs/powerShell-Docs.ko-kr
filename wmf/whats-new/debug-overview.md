---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: PowerShell 스크립트 디버깅의 향상된 기능
ms.openlocfilehash: f1771a451ba671da2371fcfc95374e6131573ddc
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855448"
---
# <a name="improvements-in-powershell-script-debugging"></a>PowerShell 스크립트 디버깅의 향상된 기능

PowerShell 5.0에는 디버깅 환경을 개선하는 여러 향상된 기능이 포함됩니다.

## <a name="break-all"></a>모두 중단

이제 PowerShell 콘솔 및 PowerShell ISE를 사용하면 스크립트를 실행하기 위해 디버거를 중단할 수 있습니다. 이 기능은 로컬 및 원격 세션에서 작동합니다.

콘솔에서 <kbd>Ctrl</kbd>+<kbd>Break</kbd>를 누릅니다.

ISE에서 <kbd>Ctrl</kbd>+<kbd>B</kbd>를 누르거나 **디버그 -> 모두 중단** 메뉴 명령을 사용합니다.

## <a name="remote-debugging-and-remote-file-editing-in-powershell-ise"></a>PowerShell ISE에서 원격 디버깅 및 원격 파일 편집

PowerShell ISE를 사용하면 PSEdit 명령을 실행하여 원격 세션에서 파일을 열고 편집할 수 있습니다.
예를 들어 다음과 같이 원격 세션의 명령줄에서 파일을 열어 편집할 수 있습니다.

```powershell
[RemoteComputer1]: PS C:\> PSEdit C:\DebugDemoScripts\Test-GetMutex.ps1
```

또한 중단점을 누르면 PowerShell ISE에서 자동으로 열리는 원격 파일에서 편집하고 변경 내용을 저장할 수 있습니다. 이제 원격 컴퓨터에서 실행되는 스크립트 파일을 디버그하고 파일을 편집하여 오류를 해결한 다음 수정된 스크립트를 다시 실행할 수 있습니다.

## <a name="advanced-script-debugging"></a>고급 스크립트 디버깅

PowerShell을 로드한 로컬 컴퓨터 프로세스에 연결하고 해당 프로세스에서 임의 runspace를 디버그할 수 있는 새로운 고급 디버깅 기능이 있습니다.

### <a name="runspace-debugging"></a>Runspace 디버깅

프로세스의 현재 runspace를 나열하고 스크립트 디버깅을 위해 해당 runspace에 PowerShell 콘솔이나 PowerShell ISE 디버거를 연결할 수 있는 새로운 cmdlet이 추가되었습니다.

- Get-Runspace
- Debug-Runspace
- Enable-RunspaceDebug
- Disable-RunspaceDebug
- Get-RunspaceDebug

### <a name="attach-to-process-hosting-powershell"></a>PowerShell을 호스트하는 프로세스에 연결

이제 PowerShell이 로드된 모든 컴퓨터 프로세스에 연결할 수 있습니다. 호스트 프로세스를 통해 대화형 세션을 시작하여 이 작업을 수행합니다. 자세한 내용은 다음을 참조하세요.

- [Enter-PSHostProcess](/powershell/module/Microsoft.PowerShell.Core/Enter-PSHostProcess)
- [Exit-PSHostProcess](/powershell/module/Microsoft.PowerShell.Core/Exit-PSHostProcess)
