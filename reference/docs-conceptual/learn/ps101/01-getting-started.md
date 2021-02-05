---
title: PowerShell 시작
description: 신규 사용자에게 PowerShell을 찾고 실행하는 방법을 알려줍니다.
ms.date: 06/02/2020
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: 8b9fee222347970df4e35f9ba0841232952a292d
ms.sourcegitcommit: df5e6f032ee2d4b556d50406832732d2f7dc2502
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/14/2021
ms.locfileid: "99599326"
---
# <a name="chapter-1---getting-started-with-powershell"></a>1장 - PowerShell 시작

필자는 회의와 사용자 그룹 모임에서 발표자가 초보자용 프레젠테이션을 시작할 때 PowerShell을 실행하는 모습을 자주 목격합니다. 이 책은 PowerShell을 사용해 본 적 없는 참석자들이 세션에서 한 질문에 대답하는 것으로 시작합니다.

특히 이 장에서는 PowerShell을 찾아 실행하고, PowerShell을 처음 사용하는 사용자가 초반에 겪는 문제를 해결하는 방법을 중점적으로 설명합니다. Windows 10 랩 환경 컴퓨터에서 이 장에 나오는 예제를 따라 하시기 바랍니다.

## <a name="what-do-i-need-to-get-started-with-powershell"></a>PowerShell을 시작하려면 무엇이 필요하나요?

모든 Windows 운영 체제 최신 버전에는 PowerShell이 설치되어 있습니다. 5\.1 미만 버전을 실행한다면 최신 버전을 설치해야 합니다.

- PowerShell 5.1로 업그레이드하는 방법은 [기존 Windows PowerShell 업그레이드][]를 참조하세요.
- PowerShell 최신 버전을 설치하는 자세한 방법은 [PowerShell 설치][]를 참조하세요.

## <a name="where-do-i-find-powershell"></a>PowerShell은 어디서 찾을 수 있나요?

Windows 10에서 PowerShell을 찾는 가장 쉬운 방법은 그림 1-1처럼 검색 창에 **PowerShell** 를 입력하는 것입니다.

![그림 1-1 - 시작 메뉴에서 PowerShell 검색](media/figure1-1.png)

그림 1-1에는 PowerShell을 여는 네 가지 바로 가기가 있습니다. 이 책에서 시연 목적으로 사용하는 컴퓨터는 Windows 10 64비트 버전을 실행하고 있습니다. 따라서 64비트 버전의 PowerShell 콘솔과 PowerShell ISE(통합 스크립팅 환경)가 있으며, 각 항목의 32비트 버전은 바로 가기에 (x86) 접미사가 붙습니다. Windows 10 32비트 버전을 실행해야 한다면 두 가지 바로 가기만 사용할 수 있습니다. 두 바로 가기는 (x86) 접미사가 없지만 32비트 버전입니다. 64비트 운영 체제를 이용한다면, 32비트 버전을 실행해야 하는 특별한 이유가 없는 한 PowerShell 64비트 버전을 실행하는 것이 좋습니다.

다른 Windows 버전에서 PowerShell을 시작하는 자세한 방법은 [Windows PowerShell 시작][]을 참조하세요.

## <a name="how-do-i-launch-powershell"></a>PowerShell을 실행하려면 어떻게 할까요?

필자가 지원하는 프로덕션 엔터프라이즈 환경에서 필자는 세 가지 Active Directory 사용자 계정을 사용합니다. 이 책에서 사용하는 랩 환경에는 이 계정 미러링되었습니다. 필자는 Windows 10 컴퓨터에 도메인 또는 로컬 관리자가 아닌 도메인 사용자로 로그인했습니다.

그리고 그림 1-1처럼 "Windows PowerShell" 바로 가기를 클릭하여 PowerShell 콘솔을 시작했습니다.

![그림 1-4 - PowerShell 창의 제목 표시줄](media/figure1-4.png)

그림 1-4처럼 PowerShell 콘솔의 제목 표시줄에 "Windows PowerShell"이 표시된다는 점에 주목하세요. 일부 명령은 정상적으로 실행되지만 PowerShell은 UAC(사용자 계정 컨트롤)에는 참여할 수 없습니다. 관리자의 승인이 필요한 작업에 대해 권한 승격을 요청할 수 없다는 뜻입니다.
다음 오류 메시지가 생성됩니다.

```powershell
Get-Service -Name W32Time | Stop-Service
```

```Output
Stop-Service : Service 'Windows Time (W32Time)' cannot be stopped due to the following
error: Cannot open W32Time service on computer '.'.
At line:1 char:29
+ Get-Service -Name W32Time | Stop-Service
+
    + CategoryInfo          : CloseError: (System.ServiceProcess.ServiceController:ServiceController)
     [Stop-Service], ServiceCommandException
    + FullyQualifiedErrorId : CouldNotStopService,Microsoft.PowerShell.Commands.StopServiceCommand
```

이 문제를 해결 방법은 PowerShell을 로컬 관리자인 도메인 사용자로 실행하는 것입니다.
필자는 두 번째 도메인 사용자 계정을 이 방법으로 구성합니다. 최소 권한 원칙에 따라 이 계정은 도메인 관리자가 아니거나 도메인에서 승격된 권한을 가져야 합니다.

PowerShell을 닫습니다. PowerShell 콘솔을 다시 실행합니다. 이번에는 **Windows PowerShell** 바로 가기를 마우스 오른쪽 단추로 클릭하고 그림 1-5처럼 **관리자 권한으로 실행** 을 선택합니다.

![그림 1-5 - 상황에 맞는 메뉴 - 관리자 권한으로 실행](media/figure1-5.png)

일반 사용자로 Windows에 로그인했다면 자격 증명을 입력하라는 메시지가 표시됩니다. 그림 1-6처럼 도메인 사용자이자 로컬 관리자인 필자 사용자 계정의 자격 증명을 입력하겠습니다.

![그림 1-6](media/figure1-6.png)

PowerShell을 관리자 권한으로 다시 실행하면 그림 1-7처럼 제목 표시줄에 "Administrator: Windows PowerShell"이라고 표시됩니다.

![그림 1-7](media/figure1-7.png)

이제 PowerShell이 로컬 관리자 권한으로 승격되어 실행되며, 일반적으로 승격 메시지를 표시하는 로컬 컴퓨터에서 명령을 실행할 때는 UAC가 문제가 되지 않습니다. 하지만 이 승격된 PowerShell 콘솔에서 실행하는 모든 명령이 승격된 상태로 실행된다는 점을 명심하세요.

관리자 권한으로 PowerShell을 쉽게 찾고 실행할 수 있도록, 작업 표시줄에 고정하고 실행될 때마다 관리자 권한으로 자동으로 시작되도록 설정하는 방법을 추천합니다.

PowerShell을 다시 검색하되, 이번에는 마우스 오른쪽 단추로 클릭한 다음 그림 1-8처럼 "작업 표시줄에 고정"을 선택합니다.

![그림 1-8](media/figure1-8.png)

작업 표시줄에 고정된 PowerShell 바로 가기를 마우스 오른쪽 단추로 클릭하고 그림 1-9처럼 속성을 선택합니다.

![그림 1-9 - 사용자 계정 컨트롤 - 자격 증명 입력](media/figure1-9.png)

그림 1-10에 #1로 표시된 “고급”을 클릭하고 그림 1-10에 #2로 표시된 “관리자 권한으로 실행” 확인란을 선택한 다음, 확인을 두 번 클릭하여 변경사항을 수락하고 대화 상자 2개를 모두 종료합니다.

![그림 1-10 - “관리자”를 표시하는 제목 표시줄](media/figure1-10.png)

PowerShell을 찾거나 관리자 권한으로 다시 실행하는 일은 걱정하지 않아도 됩니다.

관리자 권한으로 PowerShell을 실행하여 UAC 관련 문제를 방지하는 작업은 로컬 컴퓨터를 대상으로 실행하는 명령에만 영향을 줍니다. 원격 컴퓨터를 대상으로 하는 명령에는 영향을 주지 않습니다.

## <a name="what-version-of-powershell-am-i-running"></a>제가 실행하는 PowerShell 버전은 무엇인가요?

PowerShell에는 상태 정보를 저장하는 여러 자동 변수가 있습니다. 이러한 변수 중 하나인 `$PSVersionTable`에는 관련 PowerShell 버전 정보를 표시하는 해시 테이블이 있습니다.

```powershell
$PSVersionTable
```

```Output
Name                           Value
----                           -----
PSVersion                      5.1.19041.1
PSEdition                      Desktop
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}
BuildVersion                   10.0.19041.1
CLRVersion                     4.0.30319.42000
WSManStackVersion              3.0
PSRemotingProtocolVersion      2.3
SerializationVersion           1.1.0.1
```

최신 버전의 Windows PowerShell은 WMF(Windows Management Framework)의 구성요소로 배포됩니다. WMF 버전에 따라 특정 버전의 .NET Framework가 필요합니다. PowerShell 5.1로 업그레이드하는 방법은 [기존 Windows PowerShell 업그레이드][]를 참조하세요.

## <a name="execution-policy"></a>실행 정책

통념과는 달리 PowerShell의 실행 정책은 보안 경계가 아닙니다. 사용자가 자신도 모르게 스크립트를 실행하는 일이 없도록 설계되었습니다. 사용자는 마음만 먹으면 PowerShell에서 실행 정책을 쉽게 무시할 수 있습니다. 표 1-2는 현재 Windows 운영 체제에 대한 기본 실행 정책을 보여줍니다.

| 서버 운영 체제 버전 | 기본 실행 정책 |
| -------------------------------- | ------------------------ |
| Server 2019                      | 원격 서명됨            |
| Server 2016                      | 원격 서명됨            |
| 윈도우 10                       | 제한               |

실행 정책 설정에 관계없이 모든 PowerShell 명령은 대화형으로 실행할 수 있습니다. 실행 정책은 스크립트에서 실행하는 명령에만 영향을 줍니다. `Get-ExecutionPolicy` cmdlet은 현재 실행 정책 설정을 확인하는 데 사용하고 `Set-ExecutionPolicy` cmdlet은 실행 정책을 변경하는 데 사용합니다. **RemoteSigned** 정책 사용을 추천합니다. 이 정책을 실행하려면 다운로드한 스크립트에 신뢰할 수 있는 게시자가 서명해야 합니다.

현재 실행 정책을 확인하세요.

```powershell
Get-ExecutionPolicy
```

```Output
Restricted
```

실행 정책을 **제한됨** 으로 설정하면 PowerShell 스크립트를 실행할 수 없습니다. 이것은 모든 Windows 클라이언트 운영 체제의 기본 설정입니다. 문제를 확인하고 싶다면 다음 코드를 `Stop-TimeService.ps1`이라는 `.ps1` 파일로 저장하세요.

```powershell
Get-Service -Name W32Time | Stop-Service -PassThru
```

이 명령은 PowerShell을 관리자 권한으로 실행하는 한 오류 없이 대화형으로 실행됩니다. 하지만 스크립트 파일로 저장한 후 스크립트를 실행하면 오류가 생성됩니다.

```powershell
.\Stop-TimeService.ps1
```

```Output
.\Stop-TimeService.ps1 : File C:\demo\Stop-TimeService.ps1 cannot be loaded because
running scripts is disabled on this system. For more information, see
about_Execution_Policies at http://go.microsoft.com/fwlink/?LinkID=135170.
At line:1 char:1
+ .\Stop-TimeService.ps1
+
    + CategoryInfo          : SecurityError: (:) [], PSSecurityException
    + FullyQualifiedErrorId : UnauthorizedAccess
```

이전 결과 모음에 표시된 오류를 확인하면 정확한 문제를 파악할 수 있습니다(이 시스템에서 스크립트 실행이 비활성화됨). PowerShell에서 오류 메시지를 생성하는 명령을 실행할 때는 명령을 다시 실행하고 성공하길 바라는 대신 오류 메시지를 읽어야 합니다.

PowerShell 실행 정책을 원격 서명으로 변경합니다.

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned
```

```Output
Execution Policy Change
The execution policy helps protect you from scripts that you do not trust. Changing the execution
policy might expose you to the security risks described in the about_Execution_Policies help topic
at http://go.microsoft.com/fwlink/?LinkID=135170. Do you want to change the execution policy?
[Y] Yes [A] Yes to All [N] No [L] No to All [S] Suspend [?] Help (default is "N"):y
```

실행 정책을 변경할 때 표시되는 경고를 반드시 읽어 보세요. [about_Execution_Policies][] 도움말 항목을 확인해 정책 보안 변경이 보안에 미치는 영향을 알아보는 것도 도움이 됩니다.

이제 실행 정책이 **RemoteSigned** 로 설정되었으므로 `Stop-TimeService.ps1` 스크립트가 오류 없이 실행됩니다.

```powershell
.\Stop-TimeService.ps1
```

```Output
Status   Name               DisplayName
------   ----               -----------
Stopped  W32Time            Windows Time
```

계속하기 전에 Windows 시간 서비스를 시작해야 합니다. 그렇지 않으면 예기치 않은 문제가 발생할 수 있습니다.

```powershell
Start-Service -Name w32time
```

## <a name="summary"></a>요약

이 장에서는 PowerShell을 찾고 시작하는 방법과 관리자 권한으로 PowerShell을 시작하는 바로 가기를 만드는 방법을 알아보았습니다. 기본 실행 정책과 이를 변경하는 방법도 알아보았습니다.

## <a name="review"></a>검토

1. 컴퓨터에서 실행 중인 PowerShell 버전을 확인하려면 어떻게 해야 하나요?
1. 관리자 권한으로 PowerShell을 실행해야 하는 이유는 무엇인가요?
1. 현재 PowerShell 실행 정책을 확인하려면 어떻게 해야 하나요?
1. 기본 PowerShell 실행 정책이 Windows 클라이언트 컴퓨터에서 방지하는 일은 무엇인가요?
1. PowerShell 실행 정책을 변경하려면 어떻게 해야 하나요?

## <a name="recommended-reading"></a>권장 참조 항목

이 장에서 다루는 항목에 대한 자세한 정보를 확인하려면 다음 PowerShell 도움말 항목을 참조하세요.

- [about_Automatic_Variables][]
- [about_Hash_Tables][]
- [about_Execution_Policies][]

다음 장에서는 PowerShell 명령의 검색 기능을 알아봅니다. 대표적인 주제는 PowerShell을 업데이트하여 이러한 도움말 항목을 인터넷이 아닌 PowerShell에서 바로 확인하는 방법입니다.

<!-- link references -->
[about_Automatic_Variables]: /powershell/module/microsoft.powershell.core/about/about_automatic_variables
[about_Hash_Tables]: /powershell/module/microsoft.powershell.core/about/about_hash_tables
[about_Execution_Policies]: /powershell/module/microsoft.powershell.core/about/about_execution_policies
[기존 Windows PowerShell 업그레이드]: /powershell/scripting/windows-powershell/install/installing-windows-powershell#upgrading-existing-windows-powershell
[PowerShell 설치]: /powershell/scripting/install/installing-powershell
[Windows PowerShell 시작]: /powershell/scripting/windows-powershell/starting-windows-powershell
