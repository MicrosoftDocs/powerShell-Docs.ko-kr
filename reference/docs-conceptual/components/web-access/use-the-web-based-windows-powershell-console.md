---
ms.date: 08/23/2017
keywords: powershell,cmdlet
title: 웹 기반 Windows PowerShell 콘솔 사용
ms.openlocfilehash: 2bb9c6ef486ef32012a15f9890997cf2fa6a3a0b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55681313"
---
# <a name="use-the-web-based-windows-powershell-console"></a>Use the Web-based Windows PowerShell Console

업데이트됨: 2013년 6월 24일

적용 대상: Windows Server 2012 R2, Windows Server 2012

Windows PowerShell 웹 액세스를 사용하면 보안 웹 사이트에 로그인하여 Windows PowerShell 세션, cmdlet 및 스크립트를 사용하여 원격 컴퓨터를 관리할 수 있습니다.

Windows PowerShell 콘솔은 웹 브라우저에서 실행되므로 다양한 클라이언트 디바이스에서 열 수 있습니다. 웹 브라우저가 작동하는 디바이스라면 대부분 가능합니다.

웹 기반 Windows PowerShell 콘솔은 로그인 프로세스의 일부로 사용자가 지정한 원격 컴퓨터를 대상으로 합니다.

이 항목에서는 Windows PowerShell 웹 액세스 웹 기반 콘솔을 사용하여 로그인하고 시작하는 방법을 설명합니다.

그러나 Windows PowerShell 사용 방법이나 cmdlet 또는 스크립트 실행 방법에 대해서는 설명하지 않습니다.
Windows PowerShell 사용 방법과 스크립트 관련 리소스에 대한 내용은 본 항목의 끝 부분에 있는 [참고 항목](#see-also) 섹션을 참조하세요.

## <a name="supported-browsers-and-client-devices"></a>지원되는 브라우저 및 클라이언트 디바이스

Windows PowerShell 웹 액세스에서는 다음과 같은 인터넷 브라우저를 지원합니다.
모바일 브라우저는 공식적으로는 지원되지 않지만 대부분 웹 기반 Windows PowerShell 콘솔을 실행할 수 있습니다.
쿠키를 적용하고 JavaScript 및 HTTPS 웹 사이트를 실행하는 다른 브라우저도 사용할 수 있지만 공식 테스트를 거치지는 않았습니다.

### <a name="supported-desktop-computer-browsers"></a>지원되는 데스크톱 컴퓨터 브라우저

- Microsoft Windows 8.0, 9.0, 10.0 및 11.0용 Windows Internet Explorer
- Mozilla Firefox 10.0.2
- Windows용 Google Chrome 17.0.963.56m
- Windows용 Apple Safari 5.1.2
- Mac OS용 Apple Safari 5.1.2

### <a name="minimally-tested-mobile-devices-or-browsers"></a>최소한의 테스트를 거친 모바일 디바이스 또는 브라우저

- Windows Phone 7 및 7.5
- Google Android WebKit 3.1 Browser Android 2.2.1(커널 2.6)
- iPhone 운영 체제 5.0.1용 Apple Safari
- iPad 2 운영 체제 5.0.1용 Apple Safari

### <a name="browser-requirements"></a>브라우저 요구 사항

Windows PowerShell 웹 액세스 웹 기반 콘솔을 사용하려면 브라우저에서 다음을 수행해야 합니다.

- Windows PowerShell 웹 액세스 게이트웨이 웹 사이트의 쿠키를 허용합니다.
- HTTPS 페이지를 열고 읽을 수 있습니다.
- JavaScript가 사용되는 웹 사이트를 열고 실행합니다.

## <a name="signing-in-to-windows-powershell-web-access"></a>Windows PowerShell 웹 액세스 로그인

Windows PowerShell 웹 액세스 관리자는 조직의 Windows PowerShell 웹 액세스 게이트웨이 웹 사이트 주소에 해당하는 URL을 제공해야 합니다.
기본적으로 이 웹 사이트의 주소는 *https://\<server_name\>/pswa*입니다.

Windows PowerShell 웹 액세스에 로그인하기 전에 관리하려는 원격 컴퓨터의 이름이나 IP 주소를 알고 있어야 합니다.
사용자는 원격 컴퓨터에 대한 권한이 있어야 하고 원격 컴퓨터는 원격 관리를 허용하도록 구성되어 있어야 합니다.
원격 관리를 허용하도록 컴퓨터를 구성하는 방법에 대한 자세한 내용은 [Enable and Use Remote Commands in Windows PowerShell(Windows PowerShell에서 원격 명령 설정 및 사용)](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enable-psremoting)을 참조하세요.

원격 관리를 허용하도록 컴퓨터를 구성하는 가장 간단한 방법은 관리자 권한(**관리자 권한으로 실행**)을 사용하여 열린 Windows PowerShell 세션에서 컴퓨터의 **Enable-PSRemoting -force** cmdlet을 실행하는 것입니다.

### <a name="to-sign-in-to-windows-powershell-web-access"></a>Windows PowerShell 웹 액세스에 로그인하려면

1. 인터넷 브라우저 창이나 탭에서 Windows PowerShell 웹 액세스 웹 사이트를 엽니다.

1. Windows PowerShell 웹 액세스 로그인 페이지에서 네트워크 사용자 이름과 암호 및 관리하려는 컴퓨터의 이름을 제공합니다(사용자는 해당 컴퓨터에 대한 권한이 있는 사용자임). Windows PowerShell 웹 액세스 관리자가 사용자에게 컴퓨터 이름 대신 사용자 지정 사이트나 프록시 서버의 URI를 사용하도록 지침을 내린 경우 **연결 유형** 필드에서 **연결 URI**를 선택한 다음 URI를 입력합니다.

    > ![참고](images/Note.jpeg) **참고**:
    >
    > - 대상 컴퓨터가 작업 그룹에 있는 경우 `<workgroup_name>\<user_name>` 등의 구문을 이용하여 사용자 이름을 입력하고 컴퓨터에 로그인합니다.
    > - 대상 컴퓨터가 게이트웨이 서버인 경우 [컴퓨터 이름] 필드에 `localhost`를 지정할 수 있습니다.
    > - 대상 컴퓨터가 게이트웨이 서버이며 게이트웨이 서버가 작업 그룹에 있는 경우 [사용자 이름] 필드에 `<workgroup name>\<user_name>`을 사용해야 합니다. [컴퓨터 이름] 필드에는 `localhost`를 사용할 수 있습니다.

1. **옵션 연결 설정** 섹션은 관리하려는 원격 컴퓨터의 권한 부여 요구 사항과 관련된 부분입니다. 옵션 연결 설정에 해당하는 매개 변수에 대한 자세한 내용은 [Enter-PSSession](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enter-pssession) cmdlet 도움말을 참조하세요.

    대개 Windows PowerShell 웹 액세스 게이트웨이를 통한 전달에 사용하는 자격 증명은 관리하려는 원격 컴퓨터에서 인식되는 자격 증명과 같습니다. 하지만 2단계에서 지정된 원격 컴퓨터를 관리하는 데 다른 자격 증명을 사용하려면 **옵션 연결 설정** 섹션을 확장하여 대체 자격 증명을 제공합니다. 그렇지 않을 경우 6단계로 건너뜁니다.

1. Windows PowerShell 웹 액세스 관리자가 Windows PowerShell 웹 액세스 사용자를 위해 사용자 지정 세션 구성을 만든 경우 **구성 이름** 필드에 세션 구성의 이름을 입력합니다. 세션 구성에 대한 자세한 내용은 [about_Session_Configurations](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_session_configurations)를 참조하세요.

1. 달리 Windows PowerShell 웹 액세스 관리자의 지침이 없는 한, **기본값**으로 설정된 **인증 유형**을 그대로 유지합니다.

1. **로그인**을 클릭합니다.

## <a name="signing-out-and-timing-out"></a>로그아웃 및 시간 초과

다음 중 하나를 수행하여 웹 기반 Windows PowerShell 세션에서 로그아웃합니다.

- 콘솔의 오른쪽 상단 모서리에 있는 **로그아웃**을 클릭합니다. (Windows Server 2012만 해당)

- 콘솔의 오른쪽 아래에 있는 **저장** 또는 **끝내기**를 클릭합니다(Windows Server 2012 R2만 해당). **저장**을 클릭하면 Windows PowerShell 웹 액세스 세션이 저장되고 닫힙니다. 나중에 세션에 다시 연결할 수 있습니다. Windows PowerShell 웹 액세스에 다시 로그인하면 Windows PowerShell 웹 액세스에서 저장된 세션 목록을 표시합니다. 저장된 세션을 선택하고 다시 연결하거나 새 세션을 시작할 수 있습니다. 사용자에게 허용되는 최대 열린 세션 수(저장 및 활성)는 게이트웨이 관리자가 구성합니다.

    **끝내기**를 클릭하면 저장하지 않고 Windows PowerShell 웹 액세스 세션에서 로그아웃됩니다.

- 동일한 브라우저 세션이나 동일한 브라우저 세션의 새 탭에서 다른 원격 컴퓨터를 관리하기 위해 로그인을 시도합니다. 게이트웨이 서버가 Windows Server 2012 R2를 실행하는 경우에는 적용되지 않습니다. Windows Server 2012 R2에서 실행되는 Windows PowerShell 웹 액세스는 동일한 브라우저 세션의 새 탭에서 여러 사용자 세션을 허용하지 않습니다. 동일한 컴퓨터에서 둘 이상의 활성 세션을 사용하는 방법에 대한 자세한 내용은 이 항목의 [웹 기반 콘솔의 제한 사항](#limitations-of-the-web-based-console) 섹션에 있는 동시에 여러 대상 컴퓨터에 연결을 참조하세요.

- 세션 비활성 시간 제한은 20분입니다. 게이트웨이 관리자는 비활성 시간 제한값을 사용자 지정할 수 있습니다. 자세한 내용은 [session management](authorization-rules-and-security-features-of-windows-powershell-web-access.md#session-management)(세션 관리)를 참조하세요.

    - 직접 세션을 닫았기 때문이 아니라 네트워크 오류나 기타 계획되지 않은 종료 또는 오류로 인해 웹 기반 콘솔에서 세션 연결이 끊어진 경우 클라이언트 쪽의 시간 제한 기간이 경과할 때까지 Windows PowerShell 웹 액세스 세션이 대상 컴퓨터에 연결된 상태로 계속 실행됩니다. 기본적으로,이 시간 제한 기간은 20분이며 게이트웨이 관리자가 구성합니다. 기본값인 20분 또는 게이트웨이 관리자가 지정한 시간 제한 기간 중 더 짧은 시간 후에 세션 연결이 끊어집니다.

        게이트웨이 서버가 Windows Server 2012 R2를 실행하는 경우 Windows PowerShell 웹 액세스를 통해 사용자가 나중에 저장된 세션에 다시 연결할 수 있지만 게이트웨이 관리자가 지정한 시간 제한 기간이 경과할 때까지 저장된 세션을 보거나 다시 연결할 수 없습니다.

- 브라우저 창이나 탭을 닫습니다.

- 브라우저가 실행 중인 클라이언트 디바이스를 끄거나 네트워크와의 연결을 끊습니다.

- 웹 콘솔에서 **끝내기** 명령을 실행합니다. 연결하려는 세션의 구성이 [NoLanguage](https://msdn.microsoft.com/library/windows/desktop/system.management.automation.pslanguagemode.aspx) 모드를 지원하도록 구성되어 있거나 제한된 runspace에 있는 경우에는 이 명령이 작동되지 않습니다.

다시 로그인하려면 Windows PowerShell 웹 액세스 웹 페이지를 다시 열고 이 항목의 [Windows PowerShell 웹 액세스에 로그인](#signing-in-to-windows-powershell-web-access)에 설명된 단계를 수행하여 로그인합니다.

## <a name="differences-in-the-web-based-windows-powershell-console"></a>웹 기반 Windows PowerShell 콘솔의 차이점

Windows PowerShell 웹 액세스에 로그인하고 나면 웹 기반 Windows PowerShell 콘솔이 브라우저 창이나 탭으로 열립니다. 이 콘솔은 로그인 과정에서 지정된 원격 컴퓨터와 연결되므로 원격 컴퓨터에서 사용 가능한 Windows PowerShell cmdlet 또는 스크립트만 콘솔에서 사용할 수 있습니다. 이 섹션에서는 Windows PowerShell 웹 액세스 콘솔의 제한 사항 및 Windows PowerShell 웹 액세스 콘솔과 설치된 **PowerShell.exe** 콘솔 간의 차이점에 대해 설명합니다.

### <a name="functional-disparity-with-powershellexe"></a>PowerShell.exe를 사용하여 얻는 기능상의 차이점

대부분의 Windows PowerShell 호스트 기능은 Windows PowerShell 웹 액세스 웹 기반 콘솔에서도 사용할 수 있지만, 일부 기능은 사용할 수 없습니다.

- 중첩된 진행률 표시.

  Windows PowerShell 웹 액세스에서도 cmdlet의 진행 상황을 보고하는 진행률 GUI가 표시되지만, 최상위 수준의 진행률 정보만 표시됩니다.

- 입력 색 수정.

  입력 색(전경/배경 둘 다)을 변경할 수 없습니다. 출력, 경고, 자세한 정보 및 오류 메시지의 스타일은 모두 스크립트를 실행하여 변경할 수 있습니다.

- PSHostRawUserInterface.

  Windows PowerShell 웹 액세스는 Windows PowerShell 원격 관리를 통해 구현되며 원격 runspace가 사용됩니다. 그러나 Windows PowerShell 웹 액세스는 이 인터페이스에서 일부 메서드(예: Windows 콘솔에 작성하는 모든 명령)를 구현하지 않습니다. **PowerTab** 등의 명령은 Windows PowerShell에서 작동되지 않습니다.

- 기능 키.

  일부 기능 키는 대부분의 경우 브라우저에서 명령이 예약되어 있으므로 Windows PowerShell 웹 액세스에서는 지원하지 않습니다.

### <a name="unsupported-shortcut-keys"></a>지원되지 않는 바로 가기 키

기능 키 | 작업
-- | --
Ctrl+C | Windows PowerShell 웹 액세스에서 **Ctrl+C**는 브라우저에서 내용을 복사하는 데 사용됩니다. 이 콘솔에서는 **취소** 단추를 사용할 수 있으며, **Ctrl+Q** 를 사용해 명령을 취소할 수도 있습니다.
Alt-space, e, l | 화면 버퍼를 통해 스크롤
Alt+Space, e, f | 화면 버퍼에서 텍스트 검색
Alt+Space, e, k | 화면 버퍼에서 복사할 텍스트 선택
Alt+Space, e, p | Windows PowerShell 콘솔에 클립보드 내용 붙여넣기
Alt+Space, c | Windows PowerShell 콘솔 닫기
Ctrl+Break | 강제로 Windows PowerShell 창 닫기
Ctrl+Home | 현재 명령줄의 처음부터 삭제
Ctrl+End | 명령줄의 끝까지 삭제
F1 | 명령줄에서 커서 위치의 한 문자를 오른쪽으로 이동
F2 | 마지막으로 실행한 명령을 입력된 문자로 복사하여 새로운 명령 만들기
F3 | 마지막 명령줄의 내용으로 명령줄 완성
F4 | 커서 위치의 문자 삭제
F5 | 명령 기록을 역방향으로 검사 Windows PowerShell 웹 액세스에서 명령 기록의 명령에 액세스하려면 웹 기반 콘솔에서 **기록** 스크롤 단추를 클릭합니다.
F7 | 명령 기록에서 대화형으로 명령 선택
F8 | 기록을 스캔하여 현재 텍스트와 일치하는 명령 표시
F9 | 히스토리의 명령 중 특정 번호가 매겨진 명령을 실행합니다.
Page Up | 기록의 첫 번째 명령 실행
Page Down | 히스토리의 마지막 명령 실행
Alt+F7 | 명령 기록 목록 지우기

### <a name="limitations-of-the-web-based-console"></a>웹 기반 콘솔의 제한 사항

- 더블 홉

    Windows PowerShell 웹 액세스를 사용하여 새로운 세션을 만들거나 새로운 세션에서 작업하려고 할 때 더블 홉(즉, 첫 번째 연결로 두 번째 컴퓨터에 연결) 제한 문제가 발생할 수 있습니다. Windows PowerShell 웹 액세스에서는 원격 runspace를 사용하는데, 현재 **PowerShell.exe**는 원격 runspace에서 두 번째 컴퓨터에 대한 원격 연결을 지원하지 않습니다. **Enter-PSSession** cmdlet을 사용하여 기존 연결을 통해 두 번째 원격 컴퓨터에 연결하려고 하면 “네트워크 리소스를 가져올 수 없습니다.”와 같은 다양한 오류 메시지가 표시됩니다.

    이러한 더블 홉 오류를 방지하려면 관리자가 조직의 네트워크 환경에 CredSSP 인증을 구성해야 합니다. CredSSP 인증 구성에 대한 자세한 내용은 Microsoft 웹 사이트의 [두 번째 홉 원격 제어를 위한 CredSSP](https://blogs.msdn.com/b/powershell/archive/2008/06/05/credssp-for-second-hop-remoting-part-i-domain-account.aspx)를 참조하세요. 두 번째 원격 컴퓨터를 관리하려는 경우 명시적 자격 증명을 제공할 수도 있지만, 암시적 자격 증명으로는 두 번째 홉이 허용되지 않을 수 있습니다.

- 원격

    Windows PowerShell 웹 액세스에는 원격 Windows PowerShell 세션과 동일한 제약이 있습니다. 콘솔 기반 편집기나 텍스트 기반 메뉴 프로그램 같은 Windows 콘솔 API를 직접 호출하는 명령은 표준 입력, 출력 및 오류 파이프를 읽거나 쓸 수 없으므로 작동되지 않습니다. 따라서 **notepad.exe** 등의 실행 파일을 시작하는 명령이나 `OpenGridView` 또는 `ogv` 같이 GUI를 표시하는 명령은 작동되지 않습니다. 이러한 동작은 사용자의 작업 환경에 반영되므로 Windows PowerShell 웹 액세스가 사용자의 명령에 응답하지 않는 것처럼 보일 수 있습니다.

- 탭 완성

    제한된 runspace가 지원되거나 **NoLanguage** 모드 상태인 세션 구성에서는 탭 완성이 작동되지 않습니다. 관리자가 탭 완성이 지원되도록 세션을 구성할 수 있지만 그럴 경우 다음과 같은 정보가 권한이 없는 사용자에게 노출될 수 있으므로 권장되지 않습니다.

    - 내부 파일 시스템 경로

    - 내부 컴퓨터의 공유 폴더

    - runspace의 변수

    - 로드된 유형 또는 .NET Framework 네임스페이스

    - 환경 변수

- **NoLanguage** 세션 또는 제한된 runspace

    Windows PowerShell 웹 액세스에서 **NoLanguage** 세션 구성이나 제한된 runspace에 로그인한 사용자는 **끝내기** 명령을 실행하여 세션을 종료할 수 없습니다. 로그아웃하려면 콘솔 페이지에서 **로그아웃**을 클릭해야 합니다.

- 동시에 여러 대상 컴퓨터에 연결.

    게이트웨이 서버가 Windows Server 2012를 실행하는 경우 Windows PowerShell 웹 액세스에서는 브라우저 세션당 하나의 원격 컴퓨터만 연결할 수 있으며, 사용자가 한 번 로그인한 다음 별도의 브라우저 탭을 사용하여 여러 원격 컴퓨터에 연결하는 것은 허용되지 않습니다. 새 탭이나 새 브라우저 창을 열면 Windows PowerShell 웹 액세스에서 현재 세션을 끊고 새 세션을 시작하라는 메시지가 표시되므로 새로운(또는 동일한) 원격 컴퓨터에 연결할 수 있습니다. 하지만 서로 다른 원격 컴퓨터에 두 개 이상의 별도 세션을 원하는 경우 Internet Explorer의 기능을 사용하여 새 세션을 만들 수 있습니다. Internet Explorer에서 새 브라우저 세션을 시작하려면 **ALT** 키를 눌러 **파일** 메뉴를 열고 **새 세션**을 선택합니다. 그런 다음 Windows PowerShell 웹 액세스 웹 사이트를 새 세션에서 열고 다른 원격 컴퓨터로 로그인하여 액세스합니다.

    Windows PowerShell 웹 액세스 게이트웨이가 Windows Server 2012 R2에서 실행되는 경우 사용자는 다른 브라우저 탭에서 원격 컴퓨터에 대한 연결을 여러 개 열 수 있습니다. 웹 기반 Windows PowerShell 콘솔을 사용하여 원격 컴퓨터에 대한 연결을 두 개 이상 열려는 경우 Windows PowerShell 웹 액세스 게이트웨이 관리자에게 문의하여 이 기능이 게이트웨이 서버에서 지원되는지 확인합니다.

- 영구 Windows PowerShell 세션(다시 연결).

    Windows PowerShell 웹 액세스 게이트웨이의 시간이 초과된 후에는 게이트웨이와 대상 컴퓨터 간의 원격 연결이 닫힙니다. 이로 인해 현재 처리되고 있는 cmdlet 또는 스크립트가 중지됩니다. 따라서 시간이 오래 걸리는 작업을 수행할 때는 작업을 시작하고, 컴퓨터와의 연결을 끊은 다음, 나중에 다시 연결하고, 작업을 지속할 수 있는 Windows PowerShell **-Job** 인프라를 사용하는 것이 좋습니다. 또한 **-Job** cmdlet을 사용하면 Windows PowerShell 웹 액세스를 사용하여 작업을 시작한 다음 Windows PowerShell 웹 액세스 또는 다른 호스트(예: Windows PowerShell ISE(통합 스크립팅 환경))를 실행하여 로그아웃하고 나중에 다시 연결할 수 있습니다.

- 콘솔 크기 조정.

    **PowerShell.exe** 콘솔 창의 크기는 다음과 같은 세 가지 방법으로 조정할 수 있습니다.

    - 마우스를 사용하여 콘솔 창을 끌어 크기 조정

    - 콘솔 속성 GUI를 사용하여 높이 및 폭 속성 변경

    - cmdlet을 사용하여 콘솔 창의 높이와 폭 변경

        Windows PowerShell 웹 액세스의 콘솔 창은 다음의 cmdlet을 사용하여 구성할 수 있습니다. 다음 예에서는 Windows PowerShell 웹 액세스 콘솔의 폭을 **20**으로 변경합니다.

            $newSize = $Host.UI.RawUI.WindowSize
            $newSize.Width = $newSize.Width - 20

            $oldSize = $Host.UI.RawUI.WindowSize

            $Host.UI.RawUI.WindowSize = $newSize

        이와 비슷한 방법으로 콘솔 높이를 변경할 수 있습니다.

        콘솔 표시를 사용자 지정할 수 있는 추가적인 예가 [Windows PowerShell 팀 블로그](https://blogs.msdn.com/b/powershell/)에 나와 있습니다.

## <a name="see-also"></a>참고 항목

- [Windows PowerShell Cmdlet Reference](https://technet.microsoft.com/library/ee407531(ws.10).aspx)(Windows PowerShell Cmdlet 참조)
- [Microsoft TechNet의 Windows PowerShell](https://technet.microsoft.com/library/bb978526.aspx)
- [TechNet 스크립트 센터 리포지토리](https://gallery.technet.microsoft.com/scriptcenter)
- [스크립트 센터 - 스크립팅 이용자 여러분!](https://technet.microsoft.com/scriptcenter)
- [Windows PowerShell Team Blog](https://blogs.msdn.com/b/powershell/)(Windows PowerShell 팀 블로그)