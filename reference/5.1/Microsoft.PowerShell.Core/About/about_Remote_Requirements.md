---
description: PowerShell에서 원격 명령을 실행 하기 위한 시스템 요구 사항 및 구성 요구 사항에 대해 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_requirements?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Requirements
ms.openlocfilehash: 63971aeaa92eb10a745f2a02e0c7cf00dbf65d8f
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93223266"
---
# <a name="about-remote-requirements"></a>원격 요구 사항 정보

## <a name="short-description"></a>간단한 설명

PowerShell에서 원격 명령을 실행 하기 위한 시스템 요구 사항 및 구성 요구 사항에 대해 설명 합니다.

## <a name="long-description"></a>자세한 설명

이 항목에서는 원격 연결을 설정 하 고 PowerShell에서 원격 명령을 실행 하기 위한 시스템 요구 사항, 사용자 요구 사항 및 리소스 요구 사항에 대해 설명 합니다. 또한 원격 작업을 구성 하는 방법에 대 한 지침을 제공 합니다.

참고: 대부분의 cmdlet (Get-wmiobject, get-Process, Get-EventLog 및 Get-WinEvent cmdlet 포함)은 Microsoft .NET Framework 메서드를 사용 하 여 개체를 검색 함으로써 원격 컴퓨터에서 개체를 가져옵니다. PowerShell 원격 인프라를 사용 하지 않습니다. 이 문서의 요구 사항은 이러한 cmdlet에는 적용 되지 않습니다.

ComputerName 매개 변수가 있지만 Windows PowerShell 원격을 사용 하지 않는 cmdlet을 찾으려면 cmdlet의 ComputerName 매개 변수에 대 한 설명을 참조 하세요.

## <a name="system-requirements"></a>시스템 요구 사항

Windows PowerShell 3.0에서 원격 세션을 실행 하려면 로컬 컴퓨터와 원격 컴퓨터에 다음이 있어야 합니다.

- Windows PowerShell 3.0 이상
- Microsoft .NET Framework 4 이상
- Windows 원격 관리 3.0

Windows PowerShell 2.0에서 원격 세션을 실행 하려면 로컬 컴퓨터와 원격 컴퓨터에 다음이 있어야 합니다.

- Windows PowerShell 2.0 이상
- Microsoft .NET Framework 2.0 이상
- Windows 원격 관리 2.0

Windows PowerShell 2.0 및 Windows PowerShell 3.0을 실행 하는 컴퓨터 간에 원격 세션을 만들 수 있습니다. 그러나 Windows PowerShell 3.0 에서만 실행 되는 기능 (예: 세션 연결을 끊고 다시 연결 하는 기능)은 두 컴퓨터에서 모두 Windows PowerShell 3.0을 실행 하는 경우에만 사용할 수 있습니다.

설치 된 PowerShell 버전의 버전 번호를 찾으려면 $PSVersionTable 자동 변수를 사용 합니다.

Windows 원격 관리 (WinRM) 3.0 및 Microsoft .NET Framework 4는 windows 8, Windows Server 2012 및 최신 버전의 Windows 운영 체제에 포함 되어 있습니다. WinRM 3.0은 이전 운영 체제용 Windows Management Framework 3.0에 포함 되어 있습니다. 컴퓨터에 필요한 WinRM 또는 Microsoft .NET Framework 버전이 없는 경우 설치에 실패 합니다.

## <a name="user-permissions"></a>사용자 권한

원격 세션을 만들고 원격 명령을 실행 하려면 기본적으로 현재 사용자가 원격 컴퓨터에서 Administrators 그룹의 구성원 이거나 관리자의 자격 증명을 제공 해야 합니다. 그러지 않으면 명령이 실패합니다.

세션을 만들고 원격 컴퓨터 (또는 로컬 컴퓨터의 원격 세션)에서 명령을 실행 하는 데 필요한 권한은 세션이 연결 되는 원격 컴퓨터에서 세션 구성 ("끝점"이 라고도 함)에 의해 설정 됩니다. 특히 세션 구성에 대 한 보안 설명자는 세션 구성에 대 한 액세스 권한이 있는 사용자와 연결 하는 데 사용할 수 있는 사람을 결정 합니다.

기본 세션 구성의 보안 설명자 (Microsoft.powershell32, microsoft. PowerShell, Microsoft. powershell)는 Administrators 그룹의 구성원 에게만 액세스를 허용 합니다.

현재 사용자에 게 세션 구성을 사용할 수 있는 권한이 없는 경우 명령을 실행 (임시 세션 사용) 하거나 원격 컴퓨터에서 영구 세션을 만드는 명령이 실패 합니다. 사용자는 세션을 만드는 cmdlet의 ConfigurationName 매개 변수를 사용 하 여 다른 세션 구성을 선택할 수 있습니다 (사용할 수 있는 경우).

컴퓨터에서 Administrators 그룹의 구성원은 기본 세션 구성의 보안 설명자를 변경 하 고 다른 보안 설명자를 사용 하 여 새 세션 구성을 만들어 원격으로 컴퓨터에 연결할 수 있는 권한을 가진 사용자를 결정할 수 있습니다.

세션 구성에 대 한 자세한 내용은 [about_Session_Configurations](about_Session_Configurations.md)를 참조 하세요.

## <a name="windows-network-locations"></a>WINDOWS 네트워크 위치

Windows PowerShell 3.0부터 Enable-PSRemoting cmdlet은 개인, 도메인 및 공용 네트워크에서 Windows의 클라이언트 및 서버 버전에 대 한 원격 기능을 사용 하도록 설정할 수 있습니다.

개인 및 도메인 네트워크가 포함 된 Windows의 서버 버전에서 Enable-PSRemoting cmdlet은 무제한 원격 액세스를 허용 하는 방화벽 규칙을 만듭니다. 또한 동일한 로컬 서브넷에 있는 컴퓨터의 원격 액세스만 허용 하는 공용 네트워크에 대 한 방화벽 규칙을 만듭니다. 이 로컬 서브넷 방화벽 규칙은 공용 네트워크의 Windows 서버 버전에서 기본적으로 사용 하도록 설정 되지만 Enable-PSRemoting 변경 되거나 삭제 된 경우에는 규칙을 다시 적용 합니다.

개인 및 도메인 네트워크가 포함 된 Windows 클라이언트 버전에서 기본적으로 Enable-PSRemoting cmdlet은 무제한 원격 액세스를 허용 하는 방화벽 규칙을 만듭니다.

공용 네트워크를 사용 하 여 Windows 클라이언트 버전에서 원격 기능을 사용 하도록 설정 하려면 Enable-PSRemoting cmdlet의 SkipNetworkProfileCheck 매개 변수를 사용 합니다. 동일한 로컬 서브넷에 있는 컴퓨터의 원격 액세스만 허용 하는 방화벽 규칙을 만듭니다.

공용 네트워크에 대 한 로컬 서브넷 제한을 제거 하 고 Windows의 클라이언트 및 서버 버전의 모든 위치에서 원격 액세스를 허용 하려면 NetSecurity 모듈의 Set-NetFirewallRule cmdlet을 사용 합니다. 다음 명령을 실행합니다.

```powershell
Set-NetFirewallRule -Name "WINRM-HTTP-In-TCP-PUBLIC" -RemoteAddress Any
```

Windows PowerShell 2.0에서는 Windows server 버전의 Enable-PSRemoting 모든 네트워크에서 원격 액세스를 허용 하는 방화벽 규칙을 만듭니다.

Windows PowerShell 2.0의 클라이언트 버전 Windows에서 Enable-PSRemoting 개인 및 도메인 네트워크에만 방화벽 규칙을 만듭니다. 네트워크 위치가 공용 인 경우 Enable-PSRemoting 실패 합니다.

## <a name="run-as-administrator"></a>관리자 권한으로 실행

다음 원격 작업을 수행 하려면 관리자 권한이 필요 합니다.

- 로컬 컴퓨터에 대 한 원격 연결 설정 이를 일반적으로 "루프백" 시나리오 라고 합니다.

- 로컬 컴퓨터의 세션 구성 관리

- 로컬 컴퓨터에서 WS-Management 설정 보기 및 변경 다음은 WSMAN: 드라이브의 LocalHost 노드에 있는 설정입니다.

이러한 작업을 수행 하려면 로컬 컴퓨터에서 Administrators 그룹의 구성원 인 경우에도 "관리자 권한으로 실행" 옵션을 사용 하 여 PowerShell을 시작 해야 합니다.

Windows 7 및 Windows Server 2008 R2에서 "관리자 권한으로 실행" 옵션을 사용 하 여 Windows PowerShell을 시작 합니다.

1. 시작, 모든 프로그램, 보조 프로그램을 차례로 클릭 한 다음 Windows PowerShell 폴더를 클릭 합니다.
2. Windows PowerShell을 마우스 오른쪽 단추로 클릭 한 다음 "관리자 권한으로 실행"을 클릭 합니다.

"관리자 권한으로 실행" 옵션을 사용 하 여 Windows PowerShell을 시작 하려면:

1. 시작, 모든 프로그램을 차례로 클릭 한 다음 Windows PowerShell 폴더를 클릭 합니다.
2. Windows PowerShell을 마우스 오른쪽 단추로 클릭 한 다음 "관리자 권한으로 실행"을 클릭 합니다.

"관리자 권한으로 실행" 옵션은 바로 가기를 포함 하 여 Windows PowerShell에 대 한 다른 Windows 탐색기 항목 에서도 사용할 수 있습니다. 항목을 마우스 오른쪽 단추로 클릭 한 다음 "관리자 권한으로 실행"을 클릭 하면 됩니다.

Cmd.exe와 같은 다른 프로그램에서 Windows PowerShell을 시작 하는 경우 "관리자 권한으로 실행" 옵션을 사용 하 여 프로그램을 시작 합니다.

## <a name="how-to-configure-your-computer-for-remoting"></a>원격 기능을 사용할 수 있도록 컴퓨터를 구성 하는 방법

지원 되는 모든 버전의 Windows를 실행 하는 컴퓨터는 구성 없이 PowerShell에서 원격 연결을 설정 하 고 원격 명령을 실행할 수 있습니다. 그러나 연결을 수신 하 고 사용자가 로컬 및 원격 사용자 관리 PowerShell 세션 ("PSSessions")을 만들고 로컬 컴퓨터에서 명령을 실행 하도록 허용 하려면 컴퓨터에서 PowerShell 원격 기능을 사용 하도록 설정 해야 합니다.

Windows server 2012 이상 버전의 Windows Server는 기본적으로 PowerShell 원격 기능을 사용 하도록 설정 됩니다. 설정이 변경 되 면 Enable-PSRemoting cmdlet을 실행 하 여 기본 설정을 복원할 수 있습니다.

지원 되는 다른 모든 Windows 버전에서 PowerShell 원격을 사용 하도록 설정 하려면 Enable-PSRemoting cmdlet을 실행 해야 합니다.

PowerShell의 원격 기능은 WS-MANAGEMENT (Web Services for Management) 프로토콜의 Microsoft 구현인 WinRM 서비스에서 지원 됩니다. PowerShell 원격을 사용 하도록 설정 하는 경우 WS-Management의 기본 구성을 변경 하 고 사용자가 WS-MANAGEMENT에 연결할 수 있도록 하는 시스템 구성을 추가 합니다.

원격 명령을 받도록 PowerShell을 구성 하려면:

1. "관리자 권한으로 실행" 옵션을 사용 하 여 PowerShell을 시작 합니다.
2. 명령 프롬프트에 다음을 입력합니다. `Enable-PSRemoting`

원격 서비스가 올바르게 구성 되었는지 확인 하려면 로컬 컴퓨터에서 원격 세션을 만드는 다음 명령과 같은 테스트 명령을 실행 합니다.

```powershell
New-PSSession
```

원격 구성이 올바르게 구성 된 경우이 명령은 로컬 컴퓨터에서 세션을 만들고 세션을 나타내는 개체를 반환 합니다. 출력은 다음 샘플 출력과 유사 합니다.

```output
Id Name        ComputerName    State    ConfigurationName
-- ----        ------------    -----    -----
1  Session1    localhost       Opened   Microsoft.PowerShell
```

명령이 실패 하는 경우 도움이 필요 하면 [about_Remote_Troubleshooting](about_Remote_Troubleshooting.md)를 참조 하세요.

## <a name="understand-policies"></a>정책 이해

원격으로 작업 하는 경우 로컬 컴퓨터와 원격 컴퓨터에 하나씩 PowerShell의 두 인스턴스를 사용 합니다. 따라서 작업은 로컬 및 원격 컴퓨터의 Windows 정책 및 PowerShell 정책의 영향을 받습니다.

일반적으로 연결을 설정할 때와 연결 하기 전에 로컬 컴퓨터의 정책이 적용 됩니다. 연결을 사용 하는 경우 원격 컴퓨터의 정책이 적용 됩니다.

## <a name="see-also"></a>참고 항목

[about_Remote](about_Remote.md)

[about_Remote_Variables](about_Remote_Variables.md)

[about_PSSessions](about_PSSessions.md)

[Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command)

[Enter-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession)

[New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession)
