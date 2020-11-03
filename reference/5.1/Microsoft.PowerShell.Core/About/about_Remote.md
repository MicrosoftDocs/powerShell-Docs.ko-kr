---
description: Windows PowerShell에서 원격 명령을 실행 하는 방법을 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote
ms.openlocfilehash: ce75863c616bebcdb4a8273c287271b9feea3396
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93223313"
---
# <a name="about-remote"></a>원격 정보

## <a name="short-description"></a>간단한 설명

Windows PowerShell에서 원격 명령을 실행 하는 방법을 설명 합니다.

## <a name="long-description"></a>자세한 설명

임시 또는 영구 연결을 사용 하 여 단일 컴퓨터 또는 여러 컴퓨터에서 원격 명령을 실행할 수 있습니다. 단일 원격 컴퓨터를 사용 하 여 대화형 세션을 시작할 수도 있습니다.

이 항목에서는 다양 한 유형의 원격 명령을 실행 하는 방법을 보여 주는 일련의 예제를 제공 합니다. 이러한 기본 명령을 시도한 후에는 이러한 명령에 사용 되는 각 cmdlet에 대해 설명 하는 도움말 항목을 참조 하세요. 항목에서는 세부 정보를 제공 하 고 요구 사항에 맞게 명령을 수정 하는 방법을 설명 합니다.

참고: Windows PowerShell 원격을 사용 하려면 원격 컴퓨터에서 원격 컴퓨터를 구성 해야 합니다. 자세한 내용은 [about_Remote_Requirements](about_Remote_Requirements.md)을 참조하세요.

## <a name="how-to-start-an-interactive-session-enter-pssession"></a>대화형 세션을 시작 하는 방법 (입력-PSSESSION)

원격 명령을 실행 하는 가장 쉬운 방법은 원격 컴퓨터와의 대화형 세션을 시작 하는 것입니다.

세션이 시작 되 면 입력 하는 명령은 원격 컴퓨터에서 직접 입력 한 것 처럼 원격 컴퓨터에서 실행 됩니다. 각 대화형 세션에서 한 대의 컴퓨터에만 연결할 수 있습니다.

대화형 세션을 시작 하려면 Enter-PSSession cmdlet을 사용 합니다. 다음 명령은 Server01 컴퓨터와 대화형 세션을 시작 합니다.

```powershell
Enter-PSSession Server01
```

명령 프롬프트가 변경 되어 Server01 컴퓨터에 연결 되어 있음을 표시 합니다.

```
Server01\PS>
```

이제 Server01 컴퓨터에 명령을 입력할 수 있습니다.

대화형 세션을 종료하려면 다음을 입력합니다.

```powershell
Exit-PSSession
```

자세한 내용은 Enter-PSSession을 참조 하세요.

## <a name="how-to-use-cmdlets-that-have-a-computername-parameter-to-get-remote-data"></a>COMPUTERNAME 매개 변수를 사용 하 여 원격 데이터를 가져오는 CMDLET을 사용 하는 방법

여러 cmdlet에는 원격 컴퓨터에서 개체를 가져올 수 있도록 하는 ComputerName 매개 변수가 있습니다.

이러한 cmdlet은 WS-MANAGEMENT 기반 Windows PowerShell 원격 기능을 사용 하지 않으므로 Windows PowerShell을 실행 하는 모든 컴퓨터에서 이러한 cmdlet의 ComputerName 매개 변수를 사용할 수 있습니다. Windows PowerShell 원격을 위해 컴퓨터를 구성 하지 않아도 되며, 컴퓨터가 원격 기능을 위한 시스템 요구 사항을 충족 하지 않아도 됩니다.

다음 cmdlet에는 ComputerName 매개 변수가 있습니다.

```
Clear-EventLog    Limit-EventLog
Get-Counter       New-EventLog
Get-EventLog      Remove-EventLog
Get-HotFix        Restart-Computer
Get-Process       Show-EventLog
Get-Service       Stop-Computer
Get-WinEvent      Test-Connection
Get-WmiObject     Write-EventLog
```

예를 들어 다음 명령은 Server01 원격 컴퓨터의 서비스를 가져옵니다.

```powershell
Get-Service -ComputerName Server01
```

일반적으로 특별 한 구성 없이 원격 작업을 지 원하는 cmdlet에는 **ComputerName** 매개 변수가 있으며 **Session** 매개 변수는 없습니다. 세션에서 이러한 cmdlet을 찾으려면 다음과 같이 입력합니다.

```powershell
Get-Command | Where-Object {
  $_.Parameters.Keys -contains 'ComputerName' -and
  $_.Parameters.Keys -notcontains 'Session'
}
```

## <a name="how-to-run-a-remote-command"></a>원격 명령을 실행 하는 방법

원격 컴퓨터에서 다른 명령을 실행 하려면 Invoke-Command cmdlet을 사용 합니다.

단일 명령이 나 몇 가지 관련 되지 않은 명령을 실행 하려면 Invoke-Command의 ComputerName 매개 변수를 사용 하 여 원격 컴퓨터를 지정 합니다. ScriptBlock 매개 변수를 사용 하 여 명령을 지정 합니다.

예를 들어 다음 명령은 Server01 컴퓨터에서 Get-Culture 명령을 실행 합니다.

```powershell
Invoke-Command -ComputerName Server01 -ScriptBlock {Get-Culture}
```

ComputerName 매개 변수는 하나 이상의 컴퓨터에서 단일 명령 또는 관련 되지 않은 여러 명령을 실행 하는 상황을 위해 설계 되었습니다. 원격 컴퓨터에 대 한 영구 연결을 설정 하려면 Session 매개 변수를 사용 합니다.

## <a name="how-to-create-a-persistent-connection-pssession"></a>영구 연결 (PSSESSION)을 만드는 방법

Invoke-Command cmdlet의 ComputerName 매개 변수를 사용 하는 경우 Windows PowerShell은 명령에 대 한 연결을 설정 합니다. 명령이 완료될 때 연결을 닫습니다. 명령에 정의 된 변수나 함수는 모두 손실 됩니다.

원격 컴퓨터에 대 한 영구 연결을 만들려면 New-PSSession cmdlet을 사용 합니다. 예를 들어 다음 명령은 Server01 및 Server02 컴퓨터에 pssession을 만든 다음 $s 변수에 pssession을 저장 합니다.

```powershell
$s = New-PSSession -ComputerName Server01, Server02
```

## <a name="how-to-run-commands-in-a-pssession"></a>PSSESSION에서 명령을 실행 하는 방법

PSSession을 사용 하 여 함수, 별칭 및 변수 값과 같은 데이터를 공유 하는 일련의 원격 명령을 실행할 수 있습니다. PSSession에서 명령을 실행 하려면 Invoke-Command cmdlet의 Session 매개 변수를 사용 합니다.

예를 들어 다음 명령은 Invoke-Command cmdlet을 사용 하 여 Server01 및 Server02 컴퓨터의 PSSessions에서 Get-Process 명령을 실행 합니다.
이 명령은 각 PSSession의 $p 변수에 프로세스를 저장 합니다.

```powershell
Invoke-Command -Session $s -ScriptBlock {$p = Get-Process}
```

PSSession에서 영구 연결을 사용 하기 때문에 $p 변수를 사용 하는 동일한 PSSession에서 다른 명령을 실행할 수 있습니다. 다음 명령은 $p에 저장 된 프로세스의 수를 계산 합니다.

```powershell
Invoke-Command -Session $s -ScriptBlock {$p.count}
```

## <a name="how-to-run-a-remote-command-on-multiple-computers"></a>여러 컴퓨터에서 원격 명령을 실행 하는 방법

여러 컴퓨터에서 원격 명령을 실행 하려면 ComputerName 매개 변수 값에 모든 컴퓨터 이름을 입력 합니다. 이름을 쉼표로 구분 합니다.

예를 들어 다음 명령은 3 대의 컴퓨터에서 Get-Culture 명령을 실행 합니다.

```powershell
Invoke-Command -ComputerName S1, S2, S3 -ScriptBlock {Get-Culture}
```

여러 PSSessions에서 명령을 실행할 수도 있습니다. 다음 명령은 Server01, Server02 및 Server03 컴퓨터에서 pssession을 만든 다음 각 PSSessions에서 Get-Culture 명령을 실행 합니다.

```powershell
$s = New-PSSession -ComputerName S1, S2, S3
Invoke-Command -Session $s -ScriptBlock {Get-Culture}
```

컴퓨터의 로컬 컴퓨터 목록을 포함 하려면 로컬 컴퓨터의 이름을 입력 하 고 점 (.)을 입력 하거나 "localhost"를 입력 합니다.

```powershell
Invoke-Command -ComputerName S1, S2, S3, localhost -ScriptBlock {Get-Culture}
```

## <a name="how-to-run-a-script-on-remote-computers"></a>원격 컴퓨터에서 스크립트를 실행 하는 방법

원격 컴퓨터에서 로컬 스크립트를 실행 하려면 Invoke 명령의 FilePath 매개 변수를 사용 합니다.

예를 들어 다음 명령은 S1 및 S2 컴퓨터에서 Sample.ps1 스크립트를 실행 합니다.

```powershell
Invoke-Command -ComputerName S1, S2 -FilePath C:\Test\Sample.ps1
```

스크립트의 결과는 로컬 컴퓨터에 반환 됩니다. 모든 파일을 복사할 필요는 없습니다.

## <a name="how-to-stop-a-remote-command"></a>원격 명령을 중지 하는 방법

명령을 중단 하려면 CTRL + C를 누릅니다. 원격 명령을 종료 하는 원격 컴퓨터에 인터럽트 요청이 전달 됩니다.

## <a name="for-more-information"></a>상세 설명

- 원격 기능에 대 한 시스템 요구 사항에 대 한 자세한 내용은 [about_Remote_Requirements](about_Remote_Requirements.md)를 참조 하세요.

- 원격 출력 서식 지정에 대 한 도움말은 [about_Remote_Output](about_Remote_Output.md)를 참조 하세요.

- 원격 작업 방식, 원격 데이터 관리 방법, 특수 구성, 보안 문제 및 기타 질문과 대답에 대 한 자세한 내용은 [about_Remote_FAQ](about_Remote_FAQ.md)을 참조 하세요.

- 원격 오류 해결에 대 한 도움말은 about_Remote_Troubleshooting를 참조 하세요.

- PSSessions 및 영구 연결에 대 한 자세한 내용은 [about_PSSessions](about_PSSessions.md)를 참조 하세요.

- Windows PowerShell 백그라운드 작업에 대 한 자세한 내용은 [about_Jobs](about_Jobs.md)를 참조 하세요.

## <a name="keywords"></a>어

about_Remoting

## <a name="see-also"></a>참고 항목

[about_PSSessions](about_PSSessions.md)

[about_Remote_Disconnected_Sessions](about_Remote_Disconnected_Sessions.md)

[about_Remote_Requirements](about_Remote_Requirements.md)

[about_Remote_FAQ](about_Remote_FAQ.md)

[about_Remote_TroubleShooting](about_Remote_TroubleShooting.md)

[about_Remote_Variables](about_Remote_Variables.md)

[Enter-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession)

[Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command)

[New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession)
