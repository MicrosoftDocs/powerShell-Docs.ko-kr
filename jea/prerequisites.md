---
ms.date: 06/12/2017
keywords: jea,powershell,security
title: JEA 필수 조건
ms.openlocfilehash: acc16c0c7eec357b621c0706a66b8752ae5578cd
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55682648"
---
# <a name="prerequisites"></a>필수 구성 요소

> 적용 대상: Windows Powershell 5.0

Just Enough Administration은 Windows PowerShell 5.0 이상에 포함된 기능입니다.
이 항목에서는 JEA 사용을 시작하기 위해 충족해야 하는 필수 조건을 설명합니다.

## <a name="install-jea"></a>JEA 설치

JEA는 Windows PowerShell 5.0 이상에서 사용할 수 있지만, 전체 기능을 사용하려면 시스템에 사용할 수 있는 최신 버전의 PowerShell을 설치하는 것이 좋습니다.
다음 표에는 Windows Server에 대한 JEA의 가용성이 설명되어 있습니다.

서버 운영 체제   | JEA 가용성
--------------------------|--------------------------------
Windows Server 2016       | 사전 설치됨
Windows Server 2012 R2    | WMF 5.1이 있는 경우 전체 기능
Windows Server 2012       | WMF 5.1이 있는 경우 전체 기능
Windows Server 2008 R2    | WMF 5.1에서 축소된 기능<sup>1</sup>

다음과 같은 가정용 또는 업무용 컴퓨터에서도 JEA를 사용할 수 있습니다.

클라이언트 운영 체제   | JEA 가용성
--------------------------|-----------------------------------------------------
Windows 10 1607+          | 사전 설치됨
Windows 10 1603, 1511     | 기능이 축소된 상태로 사전 설치됨<sup>2</sup>
Windows 10 1507           | 사용할 수 없음
Windows 8, 8.1            | WMF 5.1이 있는 경우 전체 기능
Windows 7                 | WMF 5.1에서 축소된 기능<sup>1</sup>

<sup>1</sup> Windows Server 2008 R2 또는 Windows 7에서 관리되는 서비스 계정을 사용하도록 JEA를 구성할 수 없습니다.
가상 계정 및 기타 JEA 기능이 *지원됩니다*.

<sup>2</sup> Windows 10 버전 1511 및 1603은 그룹 관리 서비스 계정으로 실행, 세션 구성의 조건부 액세스 규칙, 사용자 드라이브 및 로컬 사용자 계정에 대한 액세스 권한 부여 JEA 기능을 지원하지 않습니다.
이러한 기능에 대한 지원을 받으려면 Windows를 버전 1607(1주년 업데이트) 이상으로 업데이트합니다.

### <a name="check-which-version-of-powershell-is-installed"></a>설치된 PowerShell 버전 확인

시스템에 설치된 PowerShell 버전을 확인하려면 Windows PowerShell 프롬프트에서 `$PSVersionTable` 변수를 확인합니다.

```powershell
$PSVersionTable.PSVersion
```

```output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  1000
```

*주* 버전이 **5**보다 크거나 같으면 JEA를 사용할 준비가 된 것입니다.
최상의 환경을 구축하고 모든 최신 기능에 액세스하려면 가능한 경우 PowerShell 버전 **5.1**로 업그레이드하는 것이 좋습니다.

### <a name="install-windows-management-framework"></a>Windows Management Framework 설치

이전 버전의 PowerShell을 실행 중인 경우 최신 WMF(Windows Management Framework) 업데이트로 시스템을 업데이트해야 합니다.
업데이트 패키지 및 최신 WMF 릴리스 정보 링크는 [다운로드 센터](https://blogs.msdn.microsoft.com/powershell/2016/02/24/windows-management-framework-wmf-5-0-rtm-packages-has-been-republished/)에서 제공됩니다.

모든 서버를 업그레이드하기 전에 WMF와의 워크로드 호환성을 테스트하는 것이 좋습니다.

Windows 10 사용자는 최신 기능 업데이트를 설치하여 현재 버전의 Windows PowerShell을 얻어야 합니다.

## <a name="enable-powershell-remoting"></a>PowerShell 원격 사용

PowerShell 원격은 JEA가 작성된 기반을 제공합니다.
따라서 JEA를 사용하기 전에 먼저 시스템에서 PowerShell 원격을 사용하도록 설정하고 [올바르게 보안을 설정](/powershell/scripting/setup/winrmsecurity)해야 합니다.

Windows Server 2012, 2012 R2 및 2016에서는 PowerShell 원격이 기본적으로 사용하도록 설정됩니다.
관리자 권한 PowerShell 창에서 다음 명령을 실행하여 PowerShell 원격을 사용하도록 설정할 수 있습니다.

```powershell
Enable-PSRemoting
```

## <a name="enable-powershell-module-and-script-block-logging-optional"></a>PowerShell 모듈 및 스크립트 블록 로깅 사용(선택 사항)

다음 단계에서는 시스템에서 모든 PowerShell 작업에 대한 로깅을 사용하도록 설정합니다.
PowerShell 모듈 로깅이 JEA에 필요하지는 않지만, 사용자가 실행한 명령이 중앙 위치에 기록되도록 PowerShell 모듈 로깅을 켜는 것이 좋습니다.

그룹 정책을 사용하여 PowerShell 모듈 로깅 정책을 구성할 수 있습니다.

1. 워크스테이션에서 로컬 그룹 정책 편집기를 열거나 Active Directory 도메인 컨트롤러의 그룹 정책 관리 콘솔에서 그룹 정책 개체를 엽니다.
2. **컴퓨터 구성\\관리 템플릿\\Windows 구성 요소\\Windows PowerShell**로 이동합니다.
3. **모듈 로깅 켜기**를 두 번 클릭합니다.
4. **사용**을 클릭합니다.
5. [옵션] 섹션에서 [모듈 이름] 옆의 **표시**를 클릭합니다.
6. 팝업 창에 `\*`를 입력합니다. 이렇게 하면 PowerShell에서 모든 모듈의 명령을 기록합니다.
7. **확인**을 클릭하여 정책을 설정합니다.
8. **PowerShell 스크립트 블록 로깅 켜기**를 두 번 클릭합니다.
9. **사용**을 클릭합니다.
10. **확인**을 클릭하여 정책을 설정합니다.
11. (도메인에 가입된 컴퓨터만 해당) `gpupdate`를 실행하거나 그룹 정책에서 업데이트된 정책을 처리하고 설정을 적용할 때까지 기다립니다.

그룹 정책을 통해 시스템 차원의 PowerShell 기록을 사용하도록 설정할 수도 있습니다.

## <a name="next-steps"></a>다음 단계

[역할 기능 파일 만들기](role-capabilities.md)

[세션 구성 파일 만들기](session-configurations.md)

## <a name="see-also"></a>참고 항목

[PowerShell 원격 및 WinRM 보안에 대한 추가 정보](/powershell/scripting/setup/winrmsecurity)

[보안에 관한 *PowerShell ♥ the Blue Team*(PowerShell ♥ Blue Team) 블로그 게시물](https://blogs.msdn.microsoft.com/powershell/2015/06/09/powershell-the-blue-team/)