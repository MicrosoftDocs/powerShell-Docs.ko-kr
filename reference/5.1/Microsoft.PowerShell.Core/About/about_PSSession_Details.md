---
description: Windows PowerShell 세션과 원격 명령에서 수행 하는 역할에 대 한 자세한 정보를 제공 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pssession_details?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PSSession_Details
ms.openlocfilehash: bc07c1de294a05cd93dd9338d798fcaf24fb0ae4
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93223401"
---
# <a name="about-pssession-details"></a>PSSession 정보 정보

## <a name="short-description"></a>간단한 설명

Windows PowerShell 세션과 원격 명령에서 수행 하는 역할에 대 한 자세한 정보를 제공 합니다.

## <a name="long-description"></a>자세한 설명

세션은 Windows PowerShell을 실행 하는 환경입니다. Windows PowerShell을 시작할 때마다 세션이 만들어집니다. 컴퓨터 또는 다른 컴퓨터에서 "Windows PowerShell 세션" 또는 "PSSessions" 라는 추가 세션을 만들 수 있습니다.

Windows PowerShell에서 만드는 세션과 달리 사용자가 만든 pssession을 제어 하 고 관리 합니다.

PSSessions는 원격 컴퓨팅에서 중요 한 역할을 합니다. 원격 컴퓨터에 연결 된 PSSession을 만드는 경우 Windows PowerShell은 PSSession을 지원 하기 위해 원격 컴퓨터에 대 한 영구 연결을 설정 합니다. PSSession을 사용 하 여 데이터를 공유 하는 일련의 명령, 함수 및 스크립트를 실행할 수 있습니다.

이 항목에서는 Windows PowerShell의 세션 및 pssession에 대 한 자세한 정보를 제공 합니다. 세션에서 수행할 수 있는 작업에 대 한 기본 정보는 [about_PSSessions](about_PSSessions.md)를 참조 하세요.

## <a name="about-sessions"></a>세션 정보

기술적으로 세션은 Windows PowerShell을 실행 하는 실행 환경입니다. 각 세션에는 Windows PowerShell을 실행 하는 호스트 프로그램 및 System.object의 인스턴스가 포함 됩니다. 호스트는 친숙 한 Windows PowerShell 콘솔 또는 명령 (예: Windows powershell ISE (통합 스크립팅 환경)을 호스트 하도록 빌드된 프로그램)을 실행 하는 다른 프로그램 (예: Cmd.exe)이 될 수 있습니다. Windows 관점에서 세션은 대상 컴퓨터의 Windows 프로세스입니다.

각 세션은 독립적으로 구성 됩니다. 자체 속성, 자체 실행 정책 및 자체 프로필을 포함 합니다. 세션을 만들 때 존재 하는 환경은 컴퓨터에서 환경을 변경 하는 경우에도 수명 동안 지속 됩니다. 모든 세션은 스크립트에서 만든 세션을 비롯 하 여 전역 범위에 생성 됩니다.

한 번에 하나의 명령 (또는 명령 파이프라인)만 세션에서 실행할 수 있습니다. 두 번째 명령은 동기적으로 (한 번에 하나씩) 실행 되며, 첫 번째 명령이 완료 될 때까지 최대 4 분이 대기 합니다. 두 번째 명령은 비동기적으로 (동시에) 실행 되지 않습니다.

## <a name="about-pssessions"></a>PSSessions 정보

Windows PowerShell을 시작할 때마다 세션이 생성 됩니다. 그리고 Windows PowerShell은 개별 명령을 실행할 임시 세션을 만듭니다.
그러나 사용자가 제어 하 고 관리 하는 세션 ("Windows PowerShell 세션" 또는 "PSSessions")을 만들 수도 있습니다.

PSSessions는 원격 명령에 중요 합니다. 또는 cmdlet의 **ComputerName** 매개 변수를 사용 하는 경우 `Invoke-Command` `Enter-PSSession` Windows PowerShell에서 명령을 실행 하는 임시 세션을 설정 하 고 명령이 나 대화형 세션이 완료 되는 즉시 세션을 닫습니다.

그러나 cmdlet을 사용 하 여 `New-PSSession` PSSession을 만드는 경우 Windows PowerShell은 여러 명령 또는 대화형 세션을 실행할 수 있는 원격 컴퓨터에 영구 세션을 설정 합니다. 사용자가 만든 pssession은 열어 둔 후 삭제할 때까지 또는 해당 세션이 만들어진 세션을 닫을 때까지 사용할 수 있습니다.

원격 컴퓨터에서 PSSession을 만들 때 시스템은 원격 컴퓨터에서 PowerShell 프로세스를 만들고 로컬 컴퓨터에서 원격 컴퓨터의 프로세스에 대 한 연결을 설정 합니다. 로컬 컴퓨터에서 PSSession을 만들 때 새 프로세스와 연결이 모두 로컬 컴퓨터에 만들어집니다.

## <a name="when-do-i-need-a-pssession"></a>PSSession은 언제 필요 한가요?

`Invoke-Command`및 cmdlet에는 `Enter-PSSession` **ComputerName** 및 **Session** 매개 변수가 모두 있습니다. 둘 중 하나를 사용 하 여 원격 명령을 실행할 수 있습니다.

**ComputerName** 매개 변수를 사용 하 여 하나 이상의 컴퓨터에서 단일 명령이 나 일련의 관련 되지 않은 명령을 실행 합니다.

데이터를 공유 하는 명령을 실행 하려면 원격 컴퓨터에 대 한 영구 연결이 필요 합니다. 이 경우 PSSession을 만든 다음 **Session** 매개 변수를 사용 하 여 pssession에서 명령을 실행 합니다.

,, 및와 같은 원격 컴퓨터에서 데이터를 가져오는 다른 많은 cmdlet에 `Get-Process` `Get-Service` `Get-EventLog` `Get-WmiObject` 는 **ComputerName** 매개 변수만 있습니다. Windows PowerShell remoting 이외의 기술을 사용 하 여 데이터를 원격으로 수집 합니다. 이러한 cmdlet에는 **Session** 매개 변수가 없지만 cmdlet을 사용 `Invoke-Command` 하 여 PSSession에서 이러한 명령을 실행할 수 있습니다.

## <a name="how-do-i-create-a-pssession"></a>PSSession을 만들려면 어떻게 하나요?

PSSession을 만들려면 cmdlet을 사용 `New-PSSession` 합니다. `New-PSSession`를 사용 하 여 로컬 또는 원격 컴퓨터에서 PSSession을 만들 수 있습니다.

## <a name="can-i-create-a-pssession-on-any-computer"></a>모든 컴퓨터에서 PSSession을 만들 수 있나요?

원격 컴퓨터에 연결 된 PSSession을 만들려면 Windows PowerShell에서 원격 기능을 사용할 수 있도록 컴퓨터를 구성 해야 합니다. 현재 사용자는 원격 컴퓨터에서 Administrators 그룹의 구성원 이거나, 현재 사용자가 Administrators 그룹의 구성원 자격 증명을 제공할 수 있어야 합니다. 자세한 내용은 [about_Remote_Requirements](about_Remote_Requirements.md)을 참조하세요.

## <a name="can-i-see-my-pssessions-in-other-sessions"></a>다른 세션에서 내 pssession을 볼 수 있나요?

Windows PowerShell 3.0부터 cmdlet의 **ComputerName** 매개 변수는 `Get-PSSession` 지정 된 원격 컴퓨터에서 만든 pssessions를 가져옵니다.

활성 pssession은 원격 컴퓨터 (연결의 "서버 쪽")에서 유지 관리 되며 모든 컴퓨터의 모든 세션에서 가져올 수 있습니다.

예를 들어 Server01 컴퓨터에서 Server02 컴퓨터로 PSSession을 만든 다음 Server03 컴퓨터로 전환 하는 경우 다음과 같은 명령을 사용 하 여 세션을 가져올 수 있습니다.

```powershell
Get-PSSession -ComputerName Server02
```

세션에서 연결을 끊는 경우에도 세션은 사용자가 삭제 하거나 시간 초과 될 때까지 원격 컴퓨터에서 유지 관리 됩니다.

Windows PowerShell 2.0에서는 현재 세션에서 만든 pssession만 가져올 수 있습니다. 다른 세션에서 만든 pssession은 가져올 수 없습니다.

자세한 내용은 [get-help](xref:Microsoft.PowerShell.Core.Get-PSSession)를 참조 하세요.

## <a name="can-i-see-the-pssessions-that-others-have-created-on-my-computer"></a>다른 사용자가 내 컴퓨터에서 만든 pssession을 볼 수 있나요?

PSSession을 만든 사용자의 자격 증명을 제공 하거나 PSSession에서 사용 하는 세션 구성에 RunAs 자격 증명을 포함 하는 경우에만 다른 사용자가 만든 pssession을 가져오고 관리할 수 있습니다. 그렇지 않으면 만든 pssession만 가져오고, 연결 하 고, 사용 하 고, 관리할 수 있습니다.

## <a name="can-i-connect-to-a-pssession-from-a-different-computer"></a>다른 컴퓨터에서 PSSession에 연결할 수 있나요?

Windows PowerShell 3.0부터 pssession은 생성 된 세션과는 독립적입니다. 활성 pssession은 원격 또는 "서버 쪽" 연결의 컴퓨터에서 유지 관리 됩니다.

Cmdlet을 사용 `Disconnect-PSSession` 하 여 PSSession에서 연결을 끊을 수 있습니다. PSSession은 로컬 세션에서 연결이 끊어져 원격 컴퓨터에서 유지 관리 됩니다.
명령은 연결 되지 않은 PSSession에서 계속 실행 됩니다. Windows PowerShell을 닫고, PSSession을 중단 하지 않고 원래 컴퓨터를 종료할 수 있습니다.

그런 다음 나중에 cmdlet을 사용 하 여 PSSession을 가져오고 cmdlet을 사용 하 여 `Get-PSSession` `Connect-PSSession` 다른 컴퓨터의 새 세션에서 pssession에 연결할 수 있습니다.

자세한 내용은 [about_Remote_Disconnected_Sessions](about_Remote_Disconnected_Sessions.md)를 참조 하세요.

## <a name="what-happens-to-my-pssession-if-my-computer-stops"></a>내 컴퓨터 중지 되 면 PSSession이 어떻게 되나요?

연결 되지 않은 pssession은 자신이 만들어진 세션과는 독립적입니다. PSSession의 연결을 끊은 다음 원래 컴퓨터를 닫으면 PSSession이 원격 컴퓨터에 유지 됩니다.

또한 Windows PowerShell은 컴퓨터를 다시 부팅 하는 경우와 같이 실수로 연결 되지 않은 활성 pssession을 복구 하려고 시도 합니다. Windows PowerShell은 PSSession을 열린 상태로 유지 하거나 (원래 세션을 계속 사용할 수 있는 경우), 연결이 끊어진 상태가 아닌 경우에는 PSSession을 유지 하려고 합니다.

"활성" PSSession은 명령을 실행 하는 PSSession입니다. PSSession이 연결 되어 있고 (연결이 끊어져 있지 않음), 연결 된 세션이 닫힐 때 PSSession에서 명령이 실행 되는 경우 Windows PowerShell은 원격 컴퓨터에서 PSSession을 유지 관리 하려고 시도 합니다. 그러나 PSSession에서 실행 중인 명령이 없으면 연결 된 세션이 닫힐 때 Windows PowerShell에서 PSSession을 닫습니다.

자세한 내용은 [about_Remote_Disconnected_Sessions](about_Remote_Disconnected_Sessions.md)를 참조 하세요.

## <a name="can-i-run-a-background-job-in-a-pssession"></a>PSSession에서 백그라운드 작업을 실행할 수 있나요?

예. 백그라운드 작업은 현재 세션과 상호 작용 하지 않고 백그라운드에서 비동기적으로 실행 되는 명령입니다. 작업을 시작 하는 명령을 제출할 때이 명령은 작업 개체를 반환 하지만 완료 될 때까지 백그라운드에서 작업을 계속 실행 합니다.

로컬 컴퓨터에서 백그라운드 작업을 시작 하려면 `Start-Job` 명령을 사용 합니다.
**ComputerName** 매개 변수를 사용 하 여 임시 연결에서 또는 **세션** 매개 변수를 사용 하 여 PSSession에서 백그라운드 작업을 실행할 수 있습니다.

원격 컴퓨터에서 백그라운드 작업을 시작 하려면 `Invoke-Command` cmdlet을 **AsJob** 매개 변수와 함께 사용 하거나 cmdlet을 사용 하 여 `Invoke-Command` `Start-Job` 원격 컴퓨터에서 명령을 실행 합니다. **AsJob** 매개 변수를 사용 하는 경우 **ComputerName** 또는 **Session** 매개 변수를 사용할 수 있습니다.

를 사용 하 여 명령을 실행 하는 경우 `Invoke-Command` `Start-Job` PSSession에서 명령을 실행 해야 합니다. **ComputerName** 매개 변수를 사용 하는 경우 작업 개체가 반환 될 때 Windows PowerShell에서 연결을 종료 하 고 작업이 중단 됩니다.

자세한 내용은 [about_Jobs](about_Jobs.md)를 참조하세요.

## <a name="can-i-run-an-interactive-session"></a>대화형 세션을 실행할 수 있나요?

예. 원격 컴퓨터와의 대화형 세션을 시작 하려면 cmdlet을 사용 `Enter-PSSession` 합니다. 대화형 세션에서 입력 하는 명령은 원격 컴퓨터에서 직접 입력 하는 것 처럼 원격 컴퓨터에서 실행 됩니다.

**ComputerName** 매개 변수를 사용 하 여 임시 세션에서 또는 **세션** 매개 변수를 사용 하 여 PSSession에서 대화형 세션을 실행할 수 있습니다.
PSSession을 사용 하는 경우 PSSession은 이전 명령의 데이터를 유지 하 고, PSSession은 대화형 세션 중에 생성 된 모든 데이터를 이후 명령에서 사용할 수 있도록 유지 합니다.

대화형 세션을 종료 하면 PSSession이 열려 있고 사용할 수 있게 됩니다.

자세한 내용은 [Enter-pssession](xref:Microsoft.PowerShell.Core.Enter-PSSession) 및 [종료-pssession](xref:Microsoft.PowerShell.Core.Exit-PSSession)을 참조 하세요.

## <a name="must-i-delete-the-pssessions"></a>PSSessions를 삭제 해야 하나요?

예. PSSession은 사용 하지 않는 경우에도 메모리 및 기타 리소스를 사용 하는 자체 포함 환경인 프로세스입니다. PSSession이 완료 되 면 삭제 합니다. 여러 pssession을 만드는 경우 사용 하지 않는 pssession을 닫고 현재 사용 중인 파일만 유지 관리 합니다.

Pssession을 삭제 하려면 cmdlet을 사용 `Remove-PSSession` 합니다. 이 명령은 pssession을 삭제 하 고 사용 하 던 모든 리소스를 해제 합니다.

의 **IdleTimeOut** 매개 변수를 사용 하 여 `New-PSSessionOption` 지정한 간격 후에 유휴 PSSession을 닫을 수도 있습니다. 자세한 내용은 [New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption)을 참조 하세요.

PSSession 개체를 변수에 저장 하 고 PSSession을 삭제 하거나 시간 초과를 허용 하는 경우 변수에는 PSSession 개체가 계속 포함 되지만 PSSession은 활성화 되지 않으며 사용 하거나 복구할 수 없습니다.

## <a name="are-all-sessions-and-pssessions-alike"></a>모든 세션과 pssession이 동일 한가요?

아니요. 개발자는 선택한 공급자 및 cmdlet만 포함 하는 사용자 지정 세션을 만들 수 있습니다. 한 세션에서 명령이 작동 하지만 다른 세션에서는 작동 하지 않는 경우이는 세션이 제한 되기 때문일 수 있습니다.

## <a name="see-also"></a>참고 항목

[about_Jobs](about_Jobs.md)

[about_PSSessions](about_PSSessions.md)

[about_Remote](about_Remote.md)

[about_Remote_Disconnected_Sessions](about_Remote_Disconnected_Sessions.md)

[about_Remote_Requirements](about_Remote_Requirements.md)

[Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command)

[Enter-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession)

[Exit-PSSession](xref:Microsoft.PowerShell.Core.Exit-PSSession)

[Get-PSSession](xref:Microsoft.PowerShell.Core.Get-PSSession)

[New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession)

[Remove-PSSession](xref:Microsoft.PowerShell.Core.Remove-PSSession)
