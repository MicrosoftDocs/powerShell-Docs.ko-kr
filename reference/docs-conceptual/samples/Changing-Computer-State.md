---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 컴퓨터 상태 변경
ms.openlocfilehash: 80692ad7c56aa13e55d4997cfec289ffb3605458
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030288"
---
# <a name="changing-computer-state"></a>컴퓨터 상태 변경

Windows PowerShell에서 컴퓨터를 다시 설정하려면 표준 명령줄 도구 또는 WMI 클래스를 사용합니다. 도구를 실행하기 위해서만 Windows PowerShell을 사용하는 경우에도 Windows PowerShell에서 컴퓨터의 전원 상태를 변경하는 방법을 알면 Windows PowerShell에서 외부 도구를 사용하는 방법에 대한 몇 가지 중요한 세부 정보를 얻을 수 있습니다.

## <a name="locking-a-computer"></a>컴퓨터 잠금

사용 가능한 표준 도구를 통해 직접 컴퓨터를 잠그는 유일한 방법은 **user32.dll**에서 **LockWorkstation()** 함수를 호출하는 것입니다.

```
rundll32.exe user32.dll,LockWorkStation
```

이 명령은 워크스테이션을 즉시 잠급니다. Windows Dll을 실행(및 반복 사용을 위해 해당 라이브러리 저장)하여 Windows 관리 함수 라이브러리인 user32.dll을 실행하는 *rundll32.exe*가 사용됩니다.

Windows XP 등에서 빠른 사용자 전환이 사용되는 동안 워크스테이션을 잠그면 컴퓨터는 현재 사용자의 화면 보호기를 시작하지 않고 사용자 로그온 화면을 표시합니다.

터미널 서버에서 특정 세션을 종료하려면 **tsshutdn.exe** 명령줄 도구를 사용합니다.

## <a name="logging-off-the-current-session"></a>현재 세션 로그오프

여러 가지 방법을 사용하여 로컬 시스템에서 세션을 로그오프할 수 있습니다. 가장 간단한 방법은 원격 데스크톱/터미널 서비스 명령줄 도구인 **logoff.exe**를 사용하는 것입니다. 자세한 내용을 보려면 Windows PowerShell 프롬프트에서 **logoff /?** 를 입력합니다. 현재 활성 세션을 로그오프하려면 인수 없이 **logoff**를 입력합니다.

**shutdown.exe** 도구와 해당 로그오프 옵션을 사용할 수도 있습니다.

```
shutdown.exe -l
```

세 번째 옵션은 WMI를 사용하는 것입니다. Win32_OperatingSystem 클래스에는 Win32Shutdown 메서드가 있습니다. 0 플래그로 메서드를 호출하면 로그오프가 시작됩니다.

```powershell
(Get-WmiObject -Class Win32_OperatingSystem -ComputerName .).Win32Shutdown(0)
```

자세한 내용을 보고 Win32Shutdown 메서드의 다른 기능을 찾으려면 MSDN에서 "Win32_OperatingSystem 클래스의 Win32Shutdown 메서드"를 참조하세요.

## <a name="shutting-down-or-restarting-a-computer"></a>컴퓨터 종료 또는 다시 시작

컴퓨터 종료 및 다시 시작은 일반적으로 동일한 유형의 작업입니다. 컴퓨터를 종료하는 도구는 일반적으로 다시 시작하며, 그 반대의 경우도 마찬가지입니다. Windows PowerShell에서 컴퓨터를 다시 시작하는 두 가지 간단한 옵션이 있습니다. Tsshutdn.exe 또는 Shutdown.exe 중 하나와 적절한 인수를 사용합니다. **tsshutdn.exe /?** 또는 **shutdown.exe /?** 를 통해 자세한 사용 정보를 얻을 수 있습니다.

Windows PowerShell에서 직접 종료 및 다시 시작 작업을 수행할 수도 있습니다.

컴퓨터를 종료하려면 Stop-Computer 명령을 사용합니다.

```powershell
Stop-Computer
```

운영 체제를 다시 시작하려면 Restart-Computer 명령을 사용합니다.

```powershell
Restart-Computer
```

컴퓨터를 강제로 즉시 다시 시작하려면 -Force 매개 변수를 사용합니다.

```powershell
Restart-Computer -Force
```
