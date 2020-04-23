---
ms.date: 08/14/2018
keywords: powershell,cmdlet
title: 원격 명령 실행
ms.openlocfilehash: d6609deafd8dec4f34a8412439d87dacd20d46f1
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2020
ms.locfileid: "67030322"
---
# <a name="running-remote-commands"></a>원격 명령 실행

단일 PowerShell 명령으로 한 대 이상의 컴퓨터에서 명령을 실행할 수 있습니다. Windows PowerShell에서는 WMI, RPC, WS-Management 등과 같은 다양한 기술을 사용하여 원격 컴퓨팅을 지원합니다.

PowerShell Core는 WMI, WS-Management 및 SSH 원격 기능을 지원합니다. RPC는 더 이상 지원되지 않습니다.

PowerShell Core의 원격 작업에 대한 자세한 내용은 다음 문서를 참조하세요.

- [PowerShell Core에서의 SSH 원격 작업][ssh-remoting]
- [PowerShell Core에서의 WSMan 원격 작업][wsman-remoting]

## <a name="windows-powershell-remoting-without-configuration"></a>구성 없이 Windows PowerShell 원격 작업

많은 Windows PowerShell cmdlet에서는 데이터를 수집하고 하나 이상의 원격 컴퓨터에서 설정을 변경할 수 있는 ComputerName 매개 변수를 사용합니다. 이러한 cmdlet은 다양한 통신 프로토콜을 사용하고, 특별한 구성 없이도 모든 Windows 운영 체제에서 작동합니다.

이러한 cmdlet은 다음과 같습니다.

- [Restart-Computer](/powershell/module/microsoft.powershell.management/restart-computer)
- [Test-Connection](/powershell/module/microsoft.powershell.management/test-connection)
- [Clear-EventLog](/powershell/module/microsoft.powershell.management/clear-eventlog)
- [Get-EventLog](/powershell/module/microsoft.powershell.management/get-eventlog)
- [Get-HotFix](/powershell/module/microsoft.powershell.management/get-hotfix)
- [Get-Process](/powershell/module/microsoft.powershell.management/get-process)
- [Get-Service](/powershell/module/microsoft.powershell.management/get-service)
- [Set-Service](/powershell/module/microsoft.powershell.management/set-service)
- [Get-WinEvent](/powershell/module/microsoft.powershell.diagnostics/get-winevent)
- [Get-WmiObject](/powershell/module/microsoft.powershell.management/get-wmiobject)

일반적으로 특별한 구성 없이 원격 작업을 지원하는 cmdlet에는 ComputerName 매개 변수는 있지만 Session 매개 변수는 없습니다. 세션에서 이러한 cmdlet을 찾으려면 다음과 같이 입력합니다.

```powershell
Get-Command | where { $_.parameters.keys -contains "ComputerName" -and $_.parameters.keys -notcontains "Session"}
```

## <a name="windows-powershell-remoting"></a>Windows PowerShell 원격 작업

WS-Management 프로토콜에서 Windows PowerShell 원격 작업을 사용하면 한 대 이상의 원격 컴퓨터에서 Windows PowerShell 명령을 실행할 수 있습니다. 원격 컴퓨터에서 영구 연결을 설정하고, 대화형 세션을 시작하고, 스크립트를 실행할 수 있습니다.

Windows PowerShell 원격 작업을 사용하려면 원격 관리를 위해 원격 컴퓨터를 구성해야 합니다.
자세한 내용과 지침은 [원격 요구 사항 정보](/powershell/module/microsoft.powershell.core/about/about_remote_requirements)를 참조하세요.

Windows PowerShell 원격 작업을 구성한 후 다양한 원격 전략을 사용할 수 있습니다.
이 문서에는 이러한 전략 중 일부만 나와 있습니다. 자세한 내용은 [원격 기능 정보](/powershell/module/microsoft.powershell.core/about/about_remote)를 참조하세요.

### <a name="start-an-interactive-session"></a>대화형 세션 시작

단일 원격 컴퓨터와 대화형 세션을 시작하려면 [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) cmdlet을 사용합니다.
예를 들어 Server01 원격 컴퓨터와 대화형 세션을 시작하려면 다음과 같이 입력합니다.

```powershell
Enter-PSSession Server01
```

명령 프롬프트가 변경되어 원격 컴퓨터의 이름이 표시됩니다. 프롬프트에 입력하는 명령이 원격 컴퓨터에서 실행되고 그 결과가 로컬 컴퓨터에 표시됩니다.

대화형 세션을 종료하려면 다음을 입력합니다.

```powershell
Exit-PSSession
```

Enter\-PSSession 및 Exit\-PSSession cmdlet에 대한 자세한 내용은 다음을 참조하세요.

- [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession)
- [Exit-PSSession](/powershell/module/microsoft.powershell.core/exit-pssession)

### <a name="run-a-remote-command"></a>원격 명령 실행

한 대 이상의 컴퓨터에서 명령을 실행하려면 [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) cmdlet을 사용합니다. 예를 들어 Server01 및 Server02 원격 컴퓨터에서 [Get-UICulture](/powershell/module/microsoft.powershell.utility/get-uiculture) 명령을 실행하려면 다음과 같이 입력합니다.

```powershell
Invoke-Command -ComputerName Server01, Server02 -ScriptBlock {Get-UICulture}
```

출력은 사용자의 컴퓨터에 반환됩니다.

```output
LCID    Name     DisplayName               PSComputerName
----    ----     -----------               --------------
1033    en-US    English (United States)   server01.corp.fabrikam.com
1033    en-US    English (United States)   server02.corp.fabrikam.com
```

### <a name="run-a-script"></a>스크립트 실행

한 대 이상의 원격 컴퓨터에서 스크립트를 실행하려면 `Invoke-Command` cmdlet의 FilePath 매개 변수를 사용합니다. 스크립트는 로컬 컴퓨터에 있거나 로컬 컴퓨터에 액세스할 수 있어야 합니다. 결과는 로컬 컴퓨터에 반환됩니다.

예를 들어 다음 명령은 Server01 및 Server02 원격 컴퓨터에서 DiskCollect.ps1 스크립트를 실행합니다.

```powershell
Invoke-Command -ComputerName Server01, Server02 -FilePath c:\Scripts\DiskCollect.ps1
```

### <a name="establish-a-persistent-connection"></a>영구 연결 설정

`New-PSSession` cmdlet을 사용하여 원격 컴퓨터에서 영구 세션을 만듭니다. 다음 예제에서는 Server01 및 Server02에 원격 세션을 만듭니다. 세션 개체는 `$s` 변수에 저장됩니다.

```powershell
$s = New-PSSession -ComputerName Server01, Server02
```

세션을 설정했으므로 이제 해당 세션에서 명령을 실행할 수 있습니다. 세션이 영구 세션이므로 명령을 실행하여 데이터를 수집하고 다른 명령에서 해당 데이터를 사용할 수 있습니다.

예를 들어 다음 명령은 $s 변수의 세션에서 Get-Hotfix 명령을 실행하고 결과를 $h 변수에 저장합니다. $h 변수는 $s의 각 세션에서 생성되지만 로컬 세션에는 없습니다.

```powershell
Invoke-Command -Session $s {$h = Get-HotFix}
```

이제 동일한 세션에서 다른 명령에 `$h` 변수의 데이터를 사용할 수 있습니다. 결과는 로컬 컴퓨터에 표시됩니다. 다음은 그 예입니다.

```powershell
Invoke-Command -Session $s {$h | where {$_.InstalledBy -ne "NTAUTHORITY\SYSTEM"}}
```

### <a name="advanced-remoting"></a>고급 원격 작업

Windows PowerShell 원격 관리가 여기에서 시작됩니다. Windows PowerShell과 함께 설치되는 cmdlet을 사용하여 로컬 끝점과 원격 끝점 모두에서 원격 세션을 설정하여 구성하고, 사용자 지정되고 제한된 세션을 만들고, 사용자가 원격 세션에서 암시적으로 실행되는 명령을 원격 세션에서 가져오도록 허용하고, 원격 세션의 보안을 구성하는 등과 같은 작업을 수행할 수 있습니다.

Windows PowerShell에는 WSMan 공급자가 포함됩니다. 공급자는 로컬 컴퓨터와 원격 컴퓨터에서 구성 설정 계층을 탐색할 수 있는 `WSMAN:` 드라이브를 만듭니다.

WSMan 공급자에 대한 자세한 내용을 보려면 [WSMan 공급자](https://technet.microsoft.com/library/dd819476.aspx) 및 [WS-Management Cmdlet 정보](/powershell/module/microsoft.powershell.core/about/about_ws-management_cmdlets)를 참조하거나 Windows PowerShell 콘솔에서 "`Get-Help wsman`"을 입력하세요.

자세한 내용은 다음을 참조하세요.

- [원격 FAQ 정보](https://technet.microsoft.com/library/dd315359.aspx)
- [Register-PSSessionConfiguration](https://go.microsoft.com/fwlink/?LinkId=821508)
- [Import-PSSession](https://go.microsoft.com/fwlink/?LinkId=821821)

원격 오류에 대한 도움이 필요한 경우 [about_Remote_Troubleshooting](https://technet.microsoft.com/library/dd347642.aspx)을 참조하세요.

## <a name="see-also"></a>참고 항목

- [about_Remote](https://technet.microsoft.com/library/9b4a5c87-9162-4adf-bdfe-fbc80b9b8970)
- [about_Remote_FAQ](https://technet.microsoft.com/library/e23702fd-9415-4a98-9975-390a4d3adc42)
- [about_Remote_Requirements](https://technet.microsoft.com/library/da213949-134c-4741-b307-81f4492ba1bd)
- [about_Remote_Troubleshooting](https://technet.microsoft.com/library/2f890148-8578-49ed-85ea-79a489dd6317)
- [about_PSSessions](https://technet.microsoft.com/library/7a9b4e0e-fa1b-47b0-92f6-6e2995d70acb)
- [about_WS-Management_Cmdlets](https://technet.microsoft.com/library/6ed3370a-ea10-45a5-9493-696aeace27ed)
- [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command)
- [Import-PSSession](https://go.microsoft.com/fwlink/?LinkId=821821)
- [New-PSSession](https://go.microsoft.com/fwlink/?LinkId=821498)
- [Register-PSSessionConfiguration](https://go.microsoft.com/fwlink/?LinkId=821508)
- [WSMan 공급자](https://technet.microsoft.com/library/66fe1241-e08f-49ca-832f-a84c33ca8735)

[wsman-remoting]: WSMan-Remoting-in-PowerShell-Core.md
[ssh-remoting]: SSH-Remoting-in-PowerShell-Core.md
