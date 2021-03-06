---
description: PowerShell에서 원격 명령을 실행 하는 방법에 대 한 질문과 대답이 포함 되어 있습니다.
Locale: en-US
ms.date: 07/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_faq?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_FAQ
ms.openlocfilehash: da3516697c58e3273538ed2ed93a7a54fcd9bb49
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99601045"
---
# <a name="about-remote-faq"></a>원격 FAQ 정보

## <a name="short-description"></a>간단한 설명
PowerShell에서 원격 명령을 실행 하는 방법에 대 한 질문과 대답이 포함 되어 있습니다.

## <a name="long-description"></a>자세한 설명입니다.

원격으로 작업 하는 경우 한 컴퓨터 ("로컬 컴퓨터" 라고도 함)의 PowerShell에 명령을 입력 하지만 명령이 다른 컴퓨터에서 실행 됩니다 ("원격 컴퓨터" 라고도 함). 원격으로 작업 하는 환경은 가능 하면 원격 컴퓨터에서 직접 작업 하는 것과 매우 비슷합니다.

참고: PowerShell 원격을 사용 하려면 원격 컴퓨터를 원격으로 구성 해야 합니다. 자세한 내용은 [about_Remote_Requirements](about_Remote_Requirements.md)을 참조하세요.

### <a name="must-both-computers-have-powershell-installed"></a>두 컴퓨터 모두에 PowerShell이 설치 되어 있어야 하나요?

예. 원격으로 작업 하려면 로컬 및 원격 컴퓨터에 PowerShell, Microsoft .NET 프레임 워크 및 WS-MANAGEMENT (Web Services for Management) 프로토콜이 있어야 합니다. 특정 명령을 실행 하는 데 필요한 모든 파일 및 기타 리소스는 원격 컴퓨터에 있어야 합니다.

Windows PowerShell 3.0 및 Windows PowerShell 2.0을 실행 하는 컴퓨터를 실행 하는 컴퓨터는 원격으로 연결 하 고 원격 명령을 실행할 수 있습니다.
그러나 세션에서 연결을 끊고 다시 연결 하는 기능과 같은 일부 기능은 두 컴퓨터에서 모두 Windows PowerShell 3.0를 실행 하는 경우에만 작동 합니다.

원격 컴퓨터에 연결할 수 있는 권한, PowerShell을 실행할 수 있는 권한 및 원격 컴퓨터의 데이터 저장소 (예: 파일 및 폴더)에 대 한 액세스 권한이 있어야 합니다.

자세한 내용은 [about_Remote_Requirements](about_Remote_Requirements.md)을 참조하세요.

### <a name="how-does-remoting-work"></a>Remoting은 어떻게 작동 하나요?

원격 명령을 제출 하면 명령이 네트워크를 통해 원격 컴퓨터의 PowerShell 엔진에 전송 되 고 원격 컴퓨터의 PowerShell 클라이언트에서 실행 됩니다. 명령 결과는 로컬 컴퓨터에 다시 전송 되 고 로컬 컴퓨터의 PowerShell 세션에 표시 됩니다.

명령을 전송 하 고 출력을 수신 하기 위해 PowerShell은 WS-Management 프로토콜을 사용 합니다. WS-Management 프로토콜에 대 한 자세한 내용은 Windows 설명서의 [WS-Management 프로토콜](/windows/win32/winrm/ws-management-protocol) 를 참조 하십시오.

Windows PowerShell 3.0부터 원격 세션은 원격 컴퓨터에 저장 됩니다. 이렇게 하면 세션에서 연결을 끊고 다른 세션이 나 다른 컴퓨터에서 다시 연결 하 여 명령을 중단 하거나 상태를 손실할 수 있습니다.

### <a name="is-powershell-remoting-secure"></a>PowerShell remoting은 안전 한가요?

원격 컴퓨터에 연결 하는 경우 시스템은 로컬 컴퓨터의 사용자 이름 및 암호 자격 증명을 사용 하거나 명령에서 제공 하는 자격 증명을 사용 하 여 원격 컴퓨터에 로그인 합니다. 자격 증명과 전송의 나머지는 암호화 됩니다.

보호를 추가 하려면 WinRM (Windows 원격 관리) 요청을 수신 대기 하도록 원격 컴퓨터에서 HTTP 대신 SSL(Secure Sockets Layer) (SSL)를 사용 하도록 구성할 수 있습니다. 그런 다음 사용자는 연결을  `Invoke-Command` `New-PSSession` 설정할 때, 및 cmdlet의 UseSSL 매개 변수를 사용할 수 있습니다 `Enter-PSSession` . 이 옵션은 HTTP 대신 보다 안전한 HTTPS 채널을 사용 합니다.

### <a name="do-all-remote-commands-require-powershell-remoting"></a>모든 원격 명령에 PowerShell 원격이 필요 한가요?

아니요. 여러 cmdlet에는 원격 컴퓨터에서 개체를 가져올 수 있도록 하는 **ComputerName** 매개 변수가 있습니다.

이러한 cmdlet은 PowerShell 원격을 사용 하지 않습니다. 따라서 powershell 원격에 대해 컴퓨터를 구성 하지 않은 경우 또는 컴퓨터가 PowerShell 원격을 위한 요구 사항을 충족 하지 않는 경우에도 PowerShell을 실행 하는 모든 컴퓨터에서이 파일을 사용할 수 있습니다.

이러한 cmdlet에는 다음이 포함 됩니다.

- `Get-Process`
- `Get-Service`
- `Get-WinEvent`
- `Get-EventLog`
- `Test-Connection`

**ComputerName** 매개 변수를 사용 하 여 모든 cmdlet을 찾으려면 다음을 입력 합니다.

```powershell
Get-Help * -Parameter ComputerName
# or
Get-Command -ParameterName ComputerName
```

특정 cmdlet의 **ComputerName** 매개 변수가 PowerShell 원격을 사용 해야 하는지 여부를 확인 하려면 매개 변수 설명을 참조 하세요. 매개 변수 설명을 표시 하려면 다음을 입력 합니다.

```powershell
Get-Help <cmdlet-name> -Parameter ComputerName
```

다음은 그 예입니다. 

```powershell
Get-Help Get-Process -Parameter ComputerName
```

다른 모든 명령의 경우 cmdlet을 사용 `Invoke-Command` 합니다.

### <a name="how-do-i-run-a-command-on-a-remote-computer"></a>원격 컴퓨터에서 명령을 실행 어떻게 할까요??

원격 컴퓨터에서 명령을 실행 하려면 cmdlet을 사용 `Invoke-Command` 합니다.

명령을 중괄호 ()로 묶어 `{}` 스크립트 블록으로 만듭니다. 의 **ScriptBlock** 매개 변수를 사용 `Invoke-Command` 하 여 명령을 지정 합니다.

의 **ComputerName** 매개 변수를 사용 `Invoke-Command` 하 여 원격 컴퓨터를 지정할 수 있습니다. 또는 원격 컴퓨터에 대 한 영구 연결 (세션)을 만든 다음의 **session** 매개 변수를 사용 `Invoke-Command` 하 여 세션에서 명령을 실행할 수 있습니다.

예를 들어 다음 명령은 `Get-Process` 명령을 원격으로 실행 합니다.

```powershell
Invoke-Command -ComputerName Server01, Server02 -ScriptBlock {Get-Process}

#  - OR -

Invoke-Command -Session $s -ScriptBlock {Get-Process}
```

원격 명령을 중단 하려면 <kbd>CTRL</kbd> + <kbd>C</kbd>를 입력 합니다. 중단 요청은 원격 컴퓨터에 전달 되 고 원격 컴퓨터는 원격 명령을 종료 합니다.

원격 명령에 대 한 자세한 내용은 about_Remote 및 원격 기능을 지 원하는 cmdlet에 대 한 도움말 항목을 참조 하세요.

### <a name="can-i-just-telnet-into-a-remote-computer"></a>원격 컴퓨터에 텔넷으로 텔넷으로 사용할 수 있나요?

Cmdlet을 사용 `Enter-PSSession` 하 여 원격 컴퓨터와의 대화형 세션을 시작할 수 있습니다.

PowerShell 프롬프트에서 다음을 입력 합니다.

```powershell
Enter-PSSession <ComputerName>
```

명령 프롬프트가 변경 되어 원격 컴퓨터에 연결 되어 있음을 표시 합니다.

```
<ComputerName>\C:>
```

이제 입력 하는 명령은 원격 컴퓨터에서 직접 입력 한 것 처럼 원격 컴퓨터에서 실행 됩니다.

대화형 세션을 종료하려면 다음을 입력합니다.

```powershell
Exit-PSSession
```

대화형 세션은 WS-Management 프로토콜을 사용 하는 영구 세션입니다. 이는 Telnet을 사용 하는 것과는 동일 하지만 유사한 환경을 제공 합니다.

자세한 내용은 `Enter-PSSession`를 참조하세요.

### <a name="can-i-create-a-persistent-connection"></a>영구 연결을 만들 수 있나요?

예. 원격 컴퓨터의 이름, NetBIOS 이름 또는 IP 주소를 지정 하 여 원격 명령을 실행할 수 있습니다. 또는 원격 컴퓨터에 연결 된 PowerShell 세션 (PSSession)을 지정 하 여 원격 명령을 실행할 수 있습니다.

또는의 **ComputerName** 매개 변수를 사용 하는 경우 `Invoke-Command` `Enter-PSSession` PowerShell에서 임시 연결을 설정 합니다. PowerShell은 연결을 사용 하 여 현재 명령만 실행 한 다음 연결을 닫습니다. 이 방법은 여러 원격 컴퓨터 에서도 단일 명령 또는 관련 되지 않은 여러 명령을 실행 하는 매우 효율적인 방법입니다.

Cmdlet을 사용 하 여 `New-PSSession` pssession을 만드는 경우 PowerShell은 pssession에 대 한 영구 연결을 설정 합니다. 그런 다음 데이터를 공유 하는 명령을 포함 하 여 PSSession에서 여러 명령을 실행할 수 있습니다.

일반적으로 데이터를 공유 하는 일련의 관련 명령을 실행 하려면 PSSession을 만듭니다. 그렇지 않으면 **ComputerName** 매개 변수로 만든 임시 연결 만으로도 대부분의 명령을 사용할 수 있습니다.

세션에 대 한 자세한 내용은 about_PSSessions를 참조 하세요.

### <a name="can-i-run-commands-on-more-than-one-computer-at-a-time"></a>한 번에 두 대 이상의 컴퓨터에서 명령을 실행할 수 있나요?

예. Cmdlet의 **ComputerName** 매개 변수는 `Invoke-Command` 여러 컴퓨터 이름을 허용 하 고 **Session** 매개 변수는 여러 개의 pssession을 허용 합니다.

명령을 실행 하면 `Invoke-Command` PowerShell에서 지정 된 모든 컴퓨터 또는 지정 된 모든 pssession에서 명령을 실행 합니다.

PowerShell은 수백 개의 동시 원격 연결을 관리할 수 있습니다. 그러나 전송할 수 있는 원격 명령의 수는 컴퓨터의 리소스 및 여러 네트워크 연결을 설정 하 고 유지 관리 하는 용량에 의해 제한 될 수 있습니다.

자세한 내용은 도움말 항목의 예제를 참조 `Invoke-Command` 하세요.

### <a name="where-are-my-profiles"></a>내 프로필은 어디에 있나요?

PowerShell 프로필은 원격 세션에서 자동으로 실행 되지 않으므로 프로필이 추가 하는 명령은 세션에 표시 되지 않습니다. 또한 `$profile` 자동 변수는 원격 세션에서 채워지지 않습니다.

세션에서 프로필을 실행 하려면 cmdlet을 사용 `Invoke-Command` 합니다.

예를 들어 다음 명령은의 세션에서 로컬 컴퓨터의 (예: 프로필을 실행 합니다 `$s` .

```
Invoke-Command -Session $s -FilePath $profile
```

다음 명령은의 세션에 있는 원격 컴퓨터에서 (예: 프로필을 실행 합니다 `$s` . `$profile`변수가 채워지지 않으므로 명령은 프로필에 대 한 명시적 경로를 사용 합니다.

```powershell
Invoke-Command -Session $s {
  . "$home\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1"
}
```

이 명령을 실행 한 후 프로필을 세션에 추가 하는 명령은에서 사용할 수 있습니다 `$s` .

세션 구성에서 시작 스크립트를 사용 하 여 세션 구성을 사용 하는 모든 원격 세션에서 프로필을 실행할 수도 있습니다.

PowerShell 프로필에 대 한 자세한 내용은 about_Profiles를 참조 하세요.
세션 구성에 대 한 자세한 내용은을 참조 하십시오 `Register-PSSessionConfiguration` .

### <a name="how-does-throttling-work-on-remote-commands"></a>원격 명령에 대 한 제한은 어떻게 작동 하나요?

PowerShell에는 로컬 컴퓨터의 리소스를 관리 하는 데 도움이 되도록 각 명령에 대해 설정 되는 동시 원격 연결 수를 제한할 수 있는 명령 당 제한 기능이 포함 되어 있습니다.

기본값은 32 동시 연결 이지만 cmdlet의 **ThrottleLimit** 매개 변수를 사용 하 여 특정 명령에 대 한 사용자 지정 스로틀 제한을 설정할 수 있습니다.

제한 기능을 사용 하는 경우 전체 세션이 아닌 컴퓨터에 적용 되는 것이 아니라 각 명령에 적용 됩니다. 여러 세션이 나 pssession에서 동시에 명령을 실행 하는 경우 동시 연결 수는 모든 세션에서 동시 연결의 합계입니다.

**ThrottleLimit** 매개 변수를 사용 하 여 cmdlet을 찾으려면 다음을 입력 합니다.

```
Get-Help * -Parameter ThrottleLimit
-or-
Get-Command -ParameterName ThrottleLimit
```

### <a name="is-the-output-of-remote-commands-different-from-local-output"></a>원격 명령의 출력이 로컬 출력과 다릅니다.

PowerShell을 로컬로 사용 하는 경우 "live" .NET Framework 개체를 보내고 받습니다. "라이브" 개체는 실제 프로그램 또는 시스템 구성 요소와 연결 된 개체입니다. 메서드를 호출 하거나 라이브 개체의 속성을 변경 하면 변경 내용이 실제 프로그램이 나 구성 요소에 영향을 줍니다. 또한 프로그램 또는 구성 요소의 속성을 변경 하면 해당 속성을 나타내는 개체의 속성도 변경 됩니다.

그러나 대부분의 라이브 개체는 네트워크를 통해 전송할 수 없으므로 PowerShell에서 원격 명령에 전송 된 대부분의 개체를 "serialize" 합니다. 즉, 각 개체를 전송에 대 한 일련의 XML (XML [Export-clixml]) 데이터 요소로 변환 합니다.

PowerShell은 직렬화 된 개체를 받을 때 XML을 deserialize 된 개체 형식으로 변환 합니다. Deserialize 된 개체는 이전에 프로그램 또는 구성 요소의 속성에 대 한 정확한 레코드 이지만 더 이상 "라이브"가 아닙니다. 즉, 더 이상 구성 요소에 직접 연결 되지 않습니다. 그리고 메서드는 더 이상 유효 하지 않기 때문에 제거 됩니다.

일반적으로 라이브 개체를 사용 하는 것 처럼 deserialize 된 개체를 사용할 수 있지만 제한 사항을 알고 있어야 합니다. 또한 cmdlet에서 반환 되는 개체에는 `Invoke-Command` 명령의 원본을 결정 하는 데 도움이 되는 추가 속성이 있습니다.

System.io.directoryinfo 개체 및 Guid와 같은 일부 개체 유형은 수신 될 때 라이브 개체로 다시 변환 됩니다. 이러한 개체는 특별 한 처리 나 서식 지정이 필요 하지 않습니다.

원격 출력을 해석 하 고 형식을 지정 하는 방법에 대 한 자세한 내용은 [about_Remote_Output](about_Remote_Output.md)를 참조 하세요.

### <a name="can-i-run-background-jobs-remotely"></a>백그라운드 작업을 원격으로 실행할 수 있나요?

예. PowerShell 백그라운드 작업은 세션과 상호 작용 하지 않고 비동기적으로 실행 되는 PowerShell 명령입니다. 백그라운드 작업을 시작 하는 경우 명령 프롬프트가 즉시 반환 되며, 오랜 시간 동안 실행 되는 경우에도 작업이 실행 되는 동안 세션에서 계속 작업할 수 있습니다.

백그라운드 작업은 항상 임시 세션에서 비동기적으로 실행 되므로 다른 명령이 실행 되는 동안에도 백그라운드 작업을 시작할 수 있습니다.

로컬 또는 원격 컴퓨터에서 백그라운드 작업을 실행할 수 있습니다. 기본적으로 백그라운드 작업은 로컬 컴퓨터에서 실행 됩니다. 그러나 cmdlet의 **AsJob** 매개 변수를 사용 하 여 `Invoke-Command` 모든 원격 명령을 백그라운드 작업으로 실행할 수 있습니다. 를 사용 `Invoke-Command` 하 여 `Start-Job` 명령을 원격으로 실행할 수 있습니다.

PowerShell의 백그라운드 작업에 대 한 자세한 내용은 [about_Jobs (about_Jobs)] 및 [about_Remote_Jobs (about_Remote_Jobs)]를 참조 하세요.

### <a name="can-i-run-windows-programs-on-a-remote-computer"></a>원격 컴퓨터에서 windows 프로그램을 실행할 수 있습니까?

PowerShell 원격 명령을 사용 하 여 원격 컴퓨터에서 Windows 기반 프로그램을 실행할 수 있습니다. 예를 들어 `Shutdown.exe` 원격 컴퓨터에서 또는를 실행할 수 있습니다 `Ipconfig.exe` .

그러나 PowerShell 명령을 사용 하 여 원격 컴퓨터의 프로그램에 대 한 사용자 인터페이스를 열 수는 없습니다.

원격 컴퓨터에서 Windows 프로그램을 시작 하면 명령이 완료 되지 않으며, 프로그램이 완료 되거나 <kbd>CTRL</kbd> + <kbd>C</kbd> 를 눌러 명령을 중단할 때까지 PowerShell 명령 프롬프트가 반환 되지 않습니다. 예를 들어 원격 컴퓨터에서 프로그램을 실행 하는 경우 `Ipconfig.exe` 이 완료 될 때까지 명령 프롬프트가 반환 되지 않습니다 `Ipconfig.exe` .

원격 명령을 사용 하 여 사용자 인터페이스를 포함 하는 프로그램을 시작 하면 프로그램 프로세스가 시작 되지만 사용자 인터페이스가 나타나지 않습니다. PowerShell 명령이 완료 되지 않고 프로그램 프로세스를 중지 하거나 <kbd>ctrl</kbd>C를 누를 때까지 명령 프롬프트가 반환 되지 않습니다 .이 경우 + <kbd></kbd>명령이 중단 되 고 프로세스가 중지 됩니다.

예를 들어 PowerShell 명령을 사용 하 여 원격 컴퓨터에서 실행 하는 경우 `Notepad` 메모장 프로세스가 원격 컴퓨터에서 시작 되지만 메모장 사용자 인터페이스가 나타나지 않습니다. 명령을 중단 하 고 명령 프롬프트를 복원 하려면 <kbd>ctrl</kbd> + <kbd>C</kbd>를 누릅니다.

### <a name="can-i-limit-the-commands-that-users-can-run-remotely-on-my-computer"></a>사용자가 컴퓨터에서 원격으로 실행할 수 있는 명령을 제한할 수 있나요?

예. 모든 원격 세션은 원격 컴퓨터의 세션 구성 중 하나를 사용 해야 합니다. 컴퓨터의 세션 구성 및 해당 세션 구성에 대 한 권한을 관리 하 여 컴퓨터에서 원격으로 명령을 실행할 수 있는 사용자와 실행할 수 있는 명령을 확인할 수 있습니다.

세션 구성은 세션에 대 한 환경을 구성 합니다. 새 구성 클래스를 구현 하는 어셈블리를 사용 하거나 세션에서 실행 되는 스크립트를 사용 하 여 구성을 정의할 수 있습니다. 구성에 따라 세션에서 사용할 수 있는 명령이 결정 될 수 있습니다.
그리고 구성에는 세션이 단일 개체나 명령에서 원격으로 받을 수 있는 데이터 양을 제한 하는 설정과 같이 컴퓨터를 보호 하는 설정이 포함 될 수 있습니다. 구성을 사용 하는 데 필요한 사용 권한을 결정 하는 보안 설명자를 지정할 수도 있습니다.

`Enable-PSRemoting`이 cmdlet은 컴퓨터에 microsoft.powershell32 (64 비트 운영 체제에만 해당)의 기본 세션 구성을 생성 합니다. `Enable-PSRemoting` 컴퓨터에서 Administrators 그룹의 구성원만 사용할 수 있도록 구성의 보안 설명자를 설정 합니다.

세션 구성 cmdlet을 사용 하 여 기본 세션 구성을 편집 하 고, 새 세션 구성을 만들고, 모든 세션 구성의 보안 설명자를 변경할 수 있습니다.

Windows PowerShell 3.0부터 `New-PSSessionConfigurationFile` cmdlet을 사용 하면 텍스트 파일을 사용 하 여 사용자 지정 세션 구성을 만들 수 있습니다. 이 파일에는 언어 모드를 설정 하 고 세션 구성을 사용 하는 세션에서 사용 가능한 cmdlet 및 모듈을 지정 하는 옵션이 포함 되어 있습니다.

사용자가, 또는 cmdlet을 사용 하는 경우 `Invoke-Command` `New-PSSession` `Enter-PSSession` **ConfigurationName** 매개 변수를 사용 하 여 세션에 사용 되는 세션 구성을 지정할 수 있습니다. 또한 세션의 기본 설정 변수 값을 변경 하 여 해당 세션에서 사용 하는 기본 구성을 변경할 수 있습니다 `$PSSessionConfigurationName` .

세션 구성에 대 한 자세한 내용은 세션 구성 cmdlet에 대 한 도움말을 참조 하세요. 세션 구성 cmdlet을 찾으려면 다음을 입력 합니다.

```powershell
Get-Command *PSSessionConfiguration
```

### <a name="what-are-fan-in-and-fan-out-configurations"></a>팬 및 팬 구성 이란?

여러 컴퓨터를 포함 하는 가장 일반적인 PowerShell 원격 시나리오는 일 대 다 구성으로, 하나의 로컬 컴퓨터 (관리자 컴퓨터)가 여러 원격 컴퓨터에서 PowerShell 명령을 실행 합니다. 이를 "팬 아웃" 시나리오 라고 합니다.

그러나 일부 기업에서는 많은 클라이언트 컴퓨터가 PowerShell을 실행 하는 단일 원격 컴퓨터 (예: 파일 서버 또는 키오스크)에 연결 하는 다 대 일 구성입니다. 이를 "팬" 구성 이라고 합니다.

PowerShell remoting은 팬 아웃 및 팬 인 구성을 모두 지원 합니다.

팬 아웃 구성의 경우 PowerShell은 ws-management (Web Services for Management) 프로토콜 및 WS-MANAGEMENT의 Microsoft 구현을 지 원하는 WinRM 서비스를 사용 합니다. 로컬 컴퓨터가 원격 컴퓨터에 연결 하는 경우 WS-Management 연결을 설정 하 고 PowerShell 용 플러그 인을 사용 하 여 원격 컴퓨터에서 PowerShell 호스트 프로세스 (Wsmprovhost.exe)를 시작 합니다. 사용자는 대체 포트, 대체 세션 구성 및 기타 기능을 지정 하 여 원격 연결을 사용자 지정할 수 있습니다.

"팬 인" 구성을 지원 하기 위해 PowerShell은 IIS (인터넷 정보 서비스)를 사용 하 여 WS 관리를 호스팅하고 PowerShell 플러그 인을 로드 하 고 PowerShell을 시작 합니다. 이 시나리오에서는 별도의 프로세스에서 각 PowerShell 세션을 시작 하는 대신 모든 PowerShell 세션이 동일한 호스트 프로세스에서 실행 됩니다.

Windows XP 또는 Windows Server 2003에서는 IIS 호스팅 및 팬 인 원격 관리가 지원 되지 않습니다.

사용자는 팬 인 구성에서 전송, 컴퓨터 이름, 포트 및 응용 프로그램 이름을 포함 하 여 연결 URI 및 HTTP 끝점을 지정할 수 있습니다.
IIS는 지정 된 응용 프로그램 이름을 가진 모든 요청을 응용 프로그램에 전달 합니다. 기본값은 PowerShell을 호스트할 수 있는 WS-MANAGEMENT입니다.

인증 메커니즘을 지정 하 고 HTTP 및 HTTPS 끝점에서 리디렉션을 허용 하거나 허용 하지 않도록 할 수도 있습니다.

### <a name="can-i-test-remoting-on-a-single-computer-not-in-a-domain"></a>도메인에 없는 단일 컴퓨터에서 원격을 테스트할 수 있나요?

예. 로컬 컴퓨터가 도메인에 있지 않은 경우에도 PowerShell 원격 기능을 사용할 수 있습니다. 원격 기능을 사용 하 여 세션에 연결 하 고 동일한 컴퓨터에 세션을 만들 수 있습니다. 기능은 원격 컴퓨터에 연결할 때와 동일 하 게 작동 합니다.

작업 그룹의 컴퓨터에서 원격 명령을 실행 하려면 컴퓨터에서 다음 Windows 설정을 변경 합니다.

주의: 이러한 설정은 시스템의 모든 사용자에 게 영향을 주며 시스템이 악의적인 공격에 더 취약 해질 수 있습니다. 이러한 변경을 수행 하는 경우 주의 해야 합니다.

- Windows Vista, Windows 7, Windows 8:

  다음 레지스트리 항목을 만들고 해당 값을 1: LocalAccountTokenFilterPolicy in으로 설정 합니다. ` HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System`

  다음 PowerShell 명령을 사용 하 여이 항목을 추가할 수 있습니다.

    ```powershell
    $parameters = @{
      Path='HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System'
      Name='LocalAccountTokenFilterPolicy'
      propertyType='DWord'
      Value=1
    }
    New-ItemProperty @parameters
    ```

- Windows Server 2003, Windows Server 2008, Windows Server 2012, Windows Server 2012 R2:

  "네트워크 액세스: 로컬 계정에 대 한 공유 및 보안 모델" 정책의 기본 설정이 "클래식" 이므로 변경이 필요 하지 않습니다. 변경 된 경우 설정을 확인 합니다.

### <a name="can-i-run-remote-commands-on-a-computer-in-another-domain"></a>다른 도메인의 컴퓨터에서 원격 명령을 실행할 수 있나요?

예. 일반적으로 명령은 오류 없이 실행 되지만, 또는 cmdlet의 **Credential** 매개 변수를 사용 하 여 `Invoke-Command` `New-PSSession` `Enter-PSSession` 원격 컴퓨터의 Administrators 그룹 구성원에 대 한 자격 증명을 제공 해야 할 수도 있습니다. 현재 사용자가 로컬 및 원격 컴퓨터에서 Administrators 그룹의 구성원 인 경우에도이 과정이 필요할 수 있습니다.

그러나 원격 컴퓨터가 로컬 컴퓨터가 신뢰 하는 도메인에 있지 않은 경우에는 원격 컴퓨터가 사용자의 자격 증명을 인증 하지 못할 수 있습니다.

인증을 사용 하도록 설정 하려면 다음 명령을 사용 하 여 WinRM의 로컬 컴퓨터에 대 한 신뢰할 수 있는 호스트 목록에 원격 컴퓨터를 추가 합니다. PowerShell 프롬프트에서 명령을 입력 합니다.

```powershell
Set-Item WSMan:\localhost\Client\TrustedHosts -Value <Remote-computer-name>
```

예를 들어 로컬 컴퓨터의 신뢰할 수 있는 호스트 목록에 Server01 컴퓨터를 추가 하려면 PowerShell 프롬프트에서 다음 명령을 입력 합니다.

```powershell
Set-Item WSMan:\localhost\Client\TrustedHosts -Value Server01
```

### <a name="does-powershell-support-remoting-over-ssh"></a>PowerShell에서 SSH를 통한 원격 지원을 지원 하나요?

예. 자세한 내용은 [SSH를 통한 PowerShell 원격](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[about_Remote](about_Remote.md)

[about_Profiles](about_Profiles.md)

[about_PSSessions](about_PSSessions.md)

[about_Remote_Jobs](about_Remote_Jobs.md)

[about_Remote_Variables](about_Remote_Variables.md)

[Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command)

[New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession)
