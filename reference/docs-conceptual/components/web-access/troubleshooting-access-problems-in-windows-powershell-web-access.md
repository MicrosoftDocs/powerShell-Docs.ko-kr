---
ms.date: 08/23/2017
keywords: powershell,cmdlet
title: Windows PowerShell 웹 액세스의 액세스 문제 해결
ms.openlocfilehash: 314e4a8098988111739705d55b68ff5ed2f5eff3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086598"
---
# <a name="troubleshooting-access-problems-in-windows-powershell-web-access"></a>Windows PowerShell 웹 액세스의 액세스 문제 해결

업데이트 날짜: 2013년 6월 24일(2017년 8월 23일 수정됨)

적용 대상: Windows Server 2012 R2, Windows Server 2012

다음 섹션에는 Windows PowerShell 웹 액세스를 사용하여 원격 컴퓨터에 연결할 때 발생할 수 있는 몇 가지 일반적인 문제와 이러한 문제에 대한 해결 방안이 나와 있습니다.

## <a name="sign-in-failure"></a>로그인 오류

다음과 같은 이유로 인해 오류가 발생할 수 있습니다.

- 원격 컴퓨터에 특정 세션 구성이나 컴퓨터에 대한 사용자 액세스를 허용하는 권한 부여 규칙이 없습니다.

  Windows PowerShell 웹 액세스 보안이 제한적이므로 권한 부여 규칙을 사용하여 명시적으로 사용자에게 원격 컴퓨터에 대한 액세스를 허용해야 합니다.

  권한 부여 규칙을 만드는 방법에 대한 자세한 내용은 [Windows PowerShell 웹 액세스의 권한 부여 규칙 및 보안 기능](authorization-rules-and-security-features-of-windows-powershell-web-access.md)을 참조하세요.

- 사용자에게는 대상 컴퓨터에 대해 허가받은 권한이 없습니다. 이 권한은 ACL(액세스 제어 목록)에서 결정됩니다.

  자세한 내용은 [Windows PowerShell 웹 액세스 로그인](use-the-web-based-windows-powershell-console.md#signing-in-to-windows-powershell-web-access) 또는 Windows PowerShell 팀 블로그를 참조하세요.

- Windows PowerShell 원격 관리 기능이 대상 컴퓨터에서 사용되지 않는 상태일 수 있습니다.

  사용자가 연결하려는 컴퓨터에서 원격 관리가 사용되는지 확인합니다.

  자세한 내용은 [How to Configure Your Computer for Remoting](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_requirements#how-to-configure-your-computer-for-remoting)(컴퓨터를 원격으로 사용할 수 있도록 구성하는 방법)을 참조하세요.

## <a name="internal-server-error"></a>내부 서버 오류

사용자가 Internet Explorer 창에서 Windows PowerShell 웹 액세스에 로그인하려고 하면 **내부 서버 오류** 페이지가 표시되거나 *Internet Explorer*의 응답이 중지됩니다.

이 문제는 Internet Explorer에서만 발생합니다.

### <a name="possible-cause"></a>가능한 원인

이 문제는 사용자가 한자를 포함한 도메인 이름으로 로그인한 경우 또는 게이트웨이 서버 이름의 일부로 한자가 두 개 이상 포함된 경우에 발생할 수 있습니다.

#### <a name="workaround"></a>해결 방법

1. [Internet Explorer 10을 설치하고 실행합니다.](https://ie.microsoft.com/testdrive/info/downloads/Default.html)
1. Internet Explorer **문서 모드** 설정을 *IE10 표준*으로 변경합니다.
   1. **F12** 키를 눌러 개발자 도구 콘솔을 엽니다.
   1. Internet Explorer 10에서 **브라우저 모드**를 클릭한 후 *Internet Explorer 10*을 선택합니다.
   1. **문서 모드**를 클릭한 후 *IE10 표준*을 클릭합니다.
   1. **F12** 키를 다시 눌러 개발자 도구 콘솔을 선택합니다.
1. Internet Explorer 10에서 자동 프록시 구성을 사용하지 않도록 설정합니다.
   1. **도구**를 클릭한 다음 **인터넷 옵션**을 클릭합니다.
   1. **인터넷 옵션** 대화 상자의 **연결** 탭에서 **LAN 설정**을 클릭합니다.
   1. **자동으로 설정 검색** 확인란을 선택 취소합니다. **확인**을 클릭한 후 다시 **확인**을 클릭하여 *인터넷 옵션* 대화 상자를 닫습니다.

## <a name="cannot-connect-to-a-remote-workgroup-computer"></a>원격 작업 그룹 컴퓨터에 연결할 수 없는 경우

대상 컴퓨터가 작업 그룹의 구성원인 경우에는 `<workgroup_name>\<user_name>` 등의 구문을 이용하여 사용자 이름을 입력하고 컴퓨터에 로그인합니다.

## <a name="cannot-find-web-server-iis-management-tools-even-though-the-role-was-installed"></a>웹 서버(IIS) 역할이 설치되어 있는데도 웹 서버(IIS) 관리 도구를 찾을 수 없는 경우

`Install-WindowsFeature` cmdlet을 사용하여 Windows PowerShell 웹 액세스를 설치한 경우 `-IncludeManagementTools` 매개 변수를 cmdlet에 추가하지 않으면 관리 도구가 설치되지 않습니다.

이에 해당하는 예는 [Windows PowerShell cmdlet을 사용하여 Windows PowerShell 웹 액세스를 설치하려면](install-and-use-windows-powershell-web-access.md#to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets)을 참조하세요.

IIS 관리자 콘솔 및 기타 IIS 관리 도구가 필요한 경우 게이트웨이 서버를 대상으로 하는 **역할 및 기능 추가 마법사** 세션에서 해당 도구를 선택하여 추가할 수 있습니다.
역할 및 기능 추가 마법사는 서버 관리자 내에서 열립니다.

## <a name="windows-powershell-web-access-website-is-not-accessible"></a>Windows PowerShell 웹 액세스 웹 사이트에 액세스할 수 없는 경우

Internet Explorer에서 보안 강화 구성(IE ESC)이 사용되는 경우 신뢰할 수 있는 사이트 목록에 Windows PowerShell 웹 액세스 웹 사이트를 추가합니다.

IE ESC를 사용하지 않도록 설정할 수도 있지만 보안 위험 때문에 사용하지 않는 것이 좋습니다.
IE ESC는 서버 관리자의 [로컬 서버] 페이지에 있는 [속성] 타일에서 사용하지 않도록 설정할 수 있습니다.

## <a name="an-authorization-failure-occurred-verify-that-you-are-authorized-to-connect-to-the-destination-computer"></a>권한 부여 오류가 발생했습니다. 대상 컴퓨터에 연결할 권한이 있는지 검증하세요.

위 오류 메시지는 게이트웨이 서버가 대상 컴퓨터이고 작업 그룹에 있을 때 연결하려고 하면 표시됩니다.

또한 게이트웨이 서버가 대상 서버이며 작업 그룹에 속해 있는 경우 사용자 이름, 컴퓨터 이름 및 사용자 그룹 이름을 지정합니다.
컴퓨터 이름을 나타내는 데에는 점(.)을 단독으로 사용하면 안 됩니다.

### <a name="scenarios-and-proper-values"></a>시나리오 및 적절한 값

#### <a name="all-cases"></a>모든 사례

매개 변수 | Value
-- | --
UserName | Server\_name\\user\_name<br/>Localhost\\user\_name<br/>.\\user\_name
UserGroup | Server\_name\\user\_group<br/>Localhost\\user\_group<br/>.\\user\_group
ComputerGroup | Server\_name\\computer\_group<br/>Localhost\\computer\_group<br/>.\\computer\_group

#### <a name="gateway-server-is-in-a-domain"></a>도메인의 게이트웨이 서버

매개 변수 | Value
-- | --
ComputerName | 정규화된 게이트웨이 서버의 이름 또는 Localhost

#### <a name="gateway-server-is-in-a-workgroup"></a>작업 그룹의 게이트웨이 서버

매개 변수 | Value
-- | --
ComputerName | 서버 이름

### <a name="gateway-credentials"></a>게이트웨이 자격 증명

다음 중 하나로 형식화된 자격 증명을 사용하여 게이트웨이 서버에 대상 컴퓨터로 로그인합니다.

- Server\_name\\user\_name
- Localhost\\user\_name
- .\\user\_name

## <a name="a-security-identifier-sid-is-displayed-in-an-authorization-rule"></a>권한 부여 규칙에 SID(보안 식별자)가 표시되지 않는 경우

SID(보안 식별자)는 구문 user\_name/computer\_name 대신 권한 부여 규칙에 표시됩니다.

규칙이 더 이상 유효하지 않거나, Active Directory 도메인 서비스를 쿼리하지 못했습니다.
권한 부여 규칙은 게이트웨이 서버가 이전에는 작업 그룹에 있었지만 나중에 도메인에 가입한 시나리오에서는 항상 유효하지 않습니다.

## <a name="cannot-sign-in-with-rule-as-an-ipv6-address-with-a-domain"></a>규칙을 사용하여 도메인의 IPv6 주소로 로그인할 수 없는 경우

권한 부여 규칙에 지정된 대상 컴퓨터에는 도메인의 IPv6 주소로 로그인할 수 없습니다.

권한 부여 규칙은 도메인 이름 형식의 IPv6 주소를 지원하지 않습니다.

IPv6 주소를 사용하여 대상 컴퓨터를 지정하려면 권한 부여 규칙의 원래 IPv6 주소(콜론 포함)를 사용하십시오.
도메인과 숫자(콜론 포함)가 모두 포함된 IPv6 주소는 Windows PowerShell 웹 액세스 로그인 페이지에서 대상 컴퓨터 이름으로 사용할 수는 있지만 권한 부여 규칙에서는 사용할 수 없습니다.

IPv6 주소에 대한 자세한 내용은 [IPv6 작동 방법](https://technet.microsoft.com/library/cc781672(v=ws.10).aspx)을 참조하세요.

## <a name="see-also"></a>참고 항목

- [Windows PowerShell 웹 액세스의 권한 부여 규칙 및 보안 기능](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx)
- [웹 기반 Windows PowerShell 콘솔 사용](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)
- [about_Remote_Requirements](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_requirements)