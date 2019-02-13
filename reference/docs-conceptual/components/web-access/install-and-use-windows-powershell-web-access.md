---
ms.date: 08/23/2017
keywords: powershell,cmdlet
title: Windows PowerShell 웹 액세스 설치 및 사용
ms.openlocfilehash: 5517347560b25f032baa77ecc2d769fb1e74ba4f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55679646"
---
# <a name="install-and-use-windows-powershell-web-access"></a>Install and Use Windows PowerShell Web Access(Windows PowerShell 웹 액세스 설치 및 사용)

업데이트됨: 2013 년 11 월 5 일, (편집: 2017년 8월

적용 대상: Windows Server 2012 R2, Windows Server 2012

## <a name="introduction"></a>소개

Windows Server 2012에 처음 도입된 Windows PowerShell 웹 액세스는 Windows PowerShell 게이트웨이로 사용되며 원격 컴퓨터를 대상으로 하는 웹 기반 Windows PowerShell 콘솔을 제공합니다. 이 기능을 사용하면 IT 전문가가 클라이언트 디바이스에 Windows PowerShell, 원격 관리 소프트웨어 또는 브라우저 플러그 인을 설치하지 않고도 웹 브라우저의 Windows PowerShell 콘솔에서 Windows PowerShell 명령과 스크립트를 실행할 수 있습니다. 웹 기반 Windows PowerShell 콘솔을 실행하려면 올바르게 구성된 Windows PowerShell 웹 액세스 게이트웨이와 JavaScript를 지원하고 쿠키를 적용하는 클라이언트 디바이스 브라우저만 있으면 됩니다.

클라이언트 디바이스에는 랩톱, 정지 상태의 개인 컴퓨터, 대여된 컴퓨터, 태블릿 컴퓨터, 웹 키오스크, Windows 기반 운영 체제를 실행 중인 컴퓨터 및 이동 전화 브라우저 등이 포함됩니다. IT 전문가는 인터넷 연결과 웹 브라우저에 대한 권한을 지닌 디바이스에서 원격 Windows 기반 서버의 주요 관리 작업을 수행할 수 있습니다.

사용자는 게이트웨이를 설치 및 구성하고 나서 웹 브라우저를 사용하여 Windows PowerShell 콘솔에 액세스할 수 있습니다. 사용자가 안전한 Windows PowerShell 웹 액세스 웹 사이트를 열면 인증을 거친 후 웹 기반 Windows PowerShell 콘솔을 실행할 수 있습니다.

Windows PowerShell 웹 액세스 설치 및 구성은 다음의 세 단계로 구성됩니다.

1. [Windows PowerShell 웹 액세스 설치](#install-windows-powershell-web-access-using-powershell-cmdlets)
1. [게이트웨이 구성](#configure-the-gateway)
1. [제한적인 권한 부여 규칙 구성](#configure-a-restrictive-authorization-rule)

Windows PowerShell 웹 액세스를 설치 및 구성하기 전에 Windows PowerShell 웹 액세스를 설치, 보호 및 제거하는 방법에 대한 지침이 포함된 이 전체 가이드를 읽는 것이 좋습니다. [웹 기반 Windows PowerShell 콘솔 사용](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831417(v=ws.11)) 항목에서는 사용자가 웹 기반 콘솔에 로그인하는 방법을 설명하고 웹 기반 Windows PowerShell 콘솔과 **powershell.exe** 콘솔 간의 제한 사항과 차이점을 다룹니다. 웹 기반 콘솔의 최종 사용자라면 [웹 기반 Windows PowerShell 콘솔 사용](use-the-web-based-windows-powershell-console.md)을 읽어야 하지만, 이 가이드의 나머지 부분은 읽을 필요가 없습니다.

이 항목에서는 심층 IIS 웹 서버 작업 지침을 제공하지 않으며, 이 항목에 설명된 Windows PowerShell 웹 액세스 게이트웨이를 구성하는 데 필요한 단계만 제공합니다. IIS에서의 웹 사이트 구성 및 보안에 대한 자세한 내용은 참고 항목 섹션의 IIS 설명서 리소스를 참조하세요.

다음 그림에는 Windows PowerShell 웹 액세스 작동 방식이 나와 있습니다.

![Windows PowerShell 웹 액세스 다이어그램](images/Windows-PowerShell-Web-Access-diagram.jpg)

## <a name="requirements-for-running-windows-powershell-web-access"></a>Windows PowerShell 웹 액세스 실행에 필요한 요구 사항

Windows PowerShell 웹 액세스에는 웹 서버(IIS), .NET Framework 4.5, 그리고 게이트웨이를 실행할 서버에서 실행되는 Windows PowerShell 3.0 또는 Windows PowerShell 4.0이 필요합니다. 서버 관리자의 역할 및 기능 추가 마법사 또는 서버 관리자용 Windows PowerShell 배포 cmdlet을 사용하여 Windows Server 2012 R2 또는 Windows Server 2012가 실행되고 있는 서버에 Windows PowerShell 웹 액세스를 설치할 수 있습니다. 서버 관리자 또는 서버 관리자의 배포 cmdlet을 사용하여 Windows PowerShell 웹 액세스를 설치하면 필수 역할 및 기능이 설치 과정의 일부분으로 자동 추가됩니다.

Windows PowerShell 웹 액세스를 통해 원격 사용자는 웹 브라우저의 Windows PowerShell을 사용하여 조직 내 컴퓨터에 액세스할 수 있습니다. Windows PowerShell 웹 액세스가 편리하고 강력한 관리 도구이기는 하지만 웹 기반 액세스로 인해 보안 위험에 노출될 수 있으므로 가급적 안전하게 구성해야 합니다. 따라서 Windows PowerShell 웹 액세스 게이트웨이를 구성하는 관리자는 사용 가능한 보안 계층, 즉 Windows PowerShell 웹 액세스에 포함된 cmdlet 기반의 권한 부여 규칙과 웹 서버(IIS) 및 타사 애플리케이션에서 제공되는 보안 계층을 모두 사용하는 것이 좋습니다. 이 설명서에는 테스트 환경용으로만 권장되는 보안되지 않은 예와, 안전한 배포용으로 권장되는 예가 모두 포함되어 있습니다.

## <a name="browser-and-client-device-support"></a>브라우저 및 클라이언트 디바이스 지원

Windows PowerShell 웹 액세스에서는 다음과 같은 인터넷 브라우저를 지원합니다. 모바일 브라우저는 공식적으로는 지원되지 않지만 대부분 웹 기반 Windows PowerShell 콘솔을 실행할 수 있습니다.
쿠키를 적용하고 JavaScript 및 HTTPS 웹 사이트를 실행하는 다른 브라우저도 사용할 수 있지만 공식 테스트를 거치지는 않았습니다.

### <a name="supported-desktop-computer-browsers"></a>지원되는 데스크톱 컴퓨터 브라우저

- Microsoft Windows 8.0, 9.0, 10.0 및 11.0용 Windows Internet Explorer
- Mozilla Firefox 10.0.2
- Windows용 Google Chrome 17.0.963.56m
- Windows용 Apple Safari 5.1.2
- Mac OS용 Apple Safari 5.1.2

### <a name="minimally-tested-mobile-devices-or-browsers"></a>최소한의 테스트를 거친 모바일 디바이스 또는 브라우저

- Windows Phone 7 및 7.5
- Google Android WebKit 3.1 Browser Android 2.2.1(커널 2.6)
- iPhone 운영 체제 5.0.1용 Apple Safari
- iPad 2 운영 체제 5.0.1용 Apple Safari

### <a name="browser-requirements"></a>브라우저 요구 사항

Windows PowerShell 웹 액세스 웹 기반 콘솔을 사용하려면 브라우저에서 다음을 수행해야 합니다.

- Windows PowerShell 웹 액세스 게이트웨이 웹 사이트의 쿠키를 허용합니다.
- HTTPS 페이지를 열고 읽을 수 있습니다.
- JavaScript가 사용되는 웹 사이트를 열고 실행합니다.

## <a name="recommended-quick-deployment"></a>권장 빠른 배포

Windows PowerShell cmdlet을 사용하거나 서버 관리자 내에서 열린 역할 및 기능 추가 마법사를 사용하여 Windows Server 2012 R2 또는 Windows Server 2012를 실행하는 서버에서 Windows PowerShell 웹 액세스 게이트웨이를 설치할 수 있습니다. 빠른 설치 및 구성을 위해 이 섹션에 설명된 대로 Windows PowerShell cmdlet을 사용합니다.

1. [Windows PowerShell 웹 액세스 설치](#install-windows-powershell-web-access-using-powershell-cmdlets)
1. [게이트웨이 구성](#configure-the-gateway)
1. [제한적인 권한 부여 규칙 구성](#configure-a-restrictive-authorization-rule)

### <a name="install-windows-powershell-web-access-using-powershell-cmdlets"></a>PowerShell cmdlet을 사용하여 Windows PowerShell 웹 액세스 설치

#### <a name="to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets"></a>Windows PowerShell cmdlet을 사용하여 Windows PowerShell 웹 액세스를 설치하려면

1. 다음 중 하나를 수행하여 관리자 권한으로 Windows PowerShell 세션을 엽니다.

   - Windows 바탕 화면의 작업 표시줄에서 **Windows PowerShell**을 마우스 오른쪽 단추로 클릭한 다음 **관리자 권한으로 실행**을 클릭합니다.
   - Windows **시작** 화면에서 **Windows PowerShell**을 마우스 오른쪽 단추로 클릭한 다음 **관리자 권한으로 실행**을 클릭합니다.

   > [!NOTE]
   > Windows PowerShell 3.0 및 4.0에서는 서버 관리자 cmdlet 모듈의 일부인 cmdlet을 실행하기 전에 해당 모듈을 Windows PowerShell 세션으로 가져올 필요가 없습니다. 모듈의 일부인 cmdlet을 처음으로 실행하면 모듈을 자동으로 가져옵니다.
   > 또한 Windows PowerShell cmdlet은 대/소문자를 구분하지 않습니다.

1. 다음을 입력하고 **Enter** 키를 누릅니다. 여기서 *computer_name*은 Windows PowerShell 웹 액세스를 설치할 원격 컴퓨터를 나타냅니다(해당되는 경우). 필요에 따라 `-Restart` 매개 변수를 사용하여 대상 서버를 자동으로 다시 시작합니다.

   `Install-WindowsFeature -Name WindowsPowerShellWebAccess -ComputerName <computer_name> -IncludeManagementTools -Restart`

   > [!NOTE]
   > Windows PowerShell cmdlet을 사용하여 Windows PowerShell 웹 액세스를 설치하면 웹 서버(IIS) 관리 도구가 기본적으로 추가되지 않습니다. 관리 도구를 Windows PowerShell 웹 액세스 게이트웨이와 동일한 서버에 설치하려면 이 단계에서와 같이 설치 명령에 `-IncludeManagementTools` 매개 변수를 추가합니다. 원격 컴퓨터에서 Windows PowerShell 웹 액세스 웹 사이트를 관리하려면 게이트웨이를 관리하려는 컴퓨터에서 [Windows 8.1용 원격 서버 관리 도구](https://www.microsoft.com/en-us/download/details.aspx?id=39296) 또는 [Windows 8용 원격 서버 관리 도구](https://www.microsoft.com/en-us/download/details.aspx?id=28972)를 설치하여 IIS 관리자 스냅인을 설치합니다.

   역할 및 기능을 오프라인 VHD에 설치하려면 `-ComputerName` 매개 변수와 `-VHD` 매개 변수를 모두 추가해야 합니다. `-ComputerName` 매개 변수에는 VHD를 탑재할 서버의 이름이 포함되며, `-VHD` 매개 변수에는 지정된 서버에서의 VHD 파일 경로가 포함됩니다.

   `Install-WindowsFeature -Name WindowsPowerShellWebAccess -VHD <path> -ComputerName <computer_name> -IncludeManagementTools -Restart`

1. 설치가 완료되면 관리자 권한으로 열린 Windows PowerShell 콘솔에서 대상 서버에 대한 `Get-WindowsFeature` cmdlet을 실행하여 Windows PowerShell 웹 액세스가 대상 서버에 설치되었는지 확인합니다. 서버 관리자 콘솔에서도 **모든 서버** 페이지에서 대상 서버를 선택한 다음 해당 서버의 **역할 및 기능** 타일을 살펴보면 Windows PowerShell 웹 액세스가 설치되었는지 확인할 수 있습니다. Windows PowerShell 웹 액세스의 추가 정보 파일을 살펴볼 수도 있습니다.

1. Windows PowerShell 웹 액세스가 설치되고 나면 게이트웨이에 필요한 기본 설치 지침이 포함된 추가 정보 파일을 검토하라는 메시지가 표시됩니다. 이러한 설치 지침은 다음 섹션인 [게이트웨이 구성](#configure-the-gateway)에도 나와 있습니다. 추가 정보 파일의 경로는 `C:\Windows\Web\PowerShellWebAccess\wwwroot\README.txt`입니다.

### <a name="configure-the-gateway"></a>게이트웨이 구성

**Install-PswaWebApplication** cmdlet을 사용하면 Windows PowerShell 웹 액세스를 가장 빨리 구성할 수 있습니다. `UseTestCertificate` 매개 변수를 `Install-PswaWebApplication` cmdlet에 추가하여 자체 서명된 테스트용 SSL 인증서를 설치할 수 있지만 안전하지 않으므로, 안전한 프로덕션 환경을 위해서는 항상 CA(인증 기관)에서 서명된 올바른 SSL 인증서를 사용해야 합니다. 관리자는 IIS 관리자 콘솔을 사용하여 자신이 선택한 서명된 인증서로 테스트 인증서를 바꿀 수 있습니다.

`Install-PswaWebApplication` cmdlet을 실행하거나 IIS 관리자에서 GUI 기반의 구성 단계를 수행하여 Windows PowerShell 웹 액세스 웹 애플리케이션 구성을 완료할 수 있습니다.
기본적으로 이 cmdlet은 IIS 관리자에 표시된 바와 같이 **기본 웹 사이트** 컨테이너에 웹 애플리케이션인 **pswa**(및 해당 애플리케이션 풀인 **pswa_pool**)를 설치합니다. 필요에 따라 웹 애플리케이션의 기본 사이트 컨테이너를 변경하는 명령을 이 cmdlet에 추가할 수 있습니다. IIS 관리자는 웹 애플리케이션에서 사용 가능한 구성 옵션(예: SSL(Secure Sockets Layer) 인증서의 포트 번호 변경)을 제공합니다.

> **![보안 정보](images/securitynote.jpeg) 보안 정보** 관리자는 반드시 CA에서 서명된 유효한 인증서를 사용하도록 게이트웨이를 구성하는 것이 좋습니다.

#### <a name="to-configure-the-windows-powershell-web-access-gateway-with-a-test-certificate-by-using-install-pswawebapplication"></a>Install-PswaWebApplication을 사용하여 테스트 인증서가 사용된 Windows PowerShell 웹 액세스 게이트웨이를 구성하려면

1. 다음 중 하나를 수행하여 Windows PowerShell 세션을 엽니다.

   - Windows 바탕 화면의 작업 표시줄에서 **Windows PowerShell**을 마우스 오른쪽 단추로 클릭합니다.
   - Windows **시작** 화면에서 **Windows PowerShell**을 클릭합니다.

2. 다음을 입력하고 **Enter** 키를 누릅니다.

   `Install-PswaWebApplication -UseTestCertificate`

   > **![보안 정보](images/securitynote.jpeg) 보안 정보** `UseTestCertificate`매개 변수는 개인 테스트 환경에서만 사용되어야 합니다. 안전한 프로덕션 환경을 위해 CA에서 서명된 유효한 인증서를 사용하는 것이 좋습니다.

   이 cmdlet을 실행하면 Windows PowerShell 웹 액세스 웹 애플리케이션이 IIS 기본 웹 사이트 컨테이너에 설치됩니다. 이 cmdlet은 기본 웹 사이트인 `https://<server_name>/pswa`에서 Windows PowerShell 웹 액세스를 실행하는 데 필요한 인프라를 만듭니다. 웹 애플리케이션을 다른 웹 사이트에 설치하려면 `WebSiteName` 매개 변수를 추가하여 웹 사이트 이름을 입력합니다. 웹 애플리케이션의 이름을 변경하려면(기본 이름: `pswa`) `WebApplicationName` 매개 변수를 추가합니다.

   이 cmdlet을 실행하면 다음과 같은 설정이 구성됩니다. 필요에 따라 IIS 관리자 콘솔에서 이러한 설정을 수동으로 변경할 수 있습니다.

   - Path: /pswa
   - ApplicationPool: pswa_pool
   - EnabledProtocols: http
   - PhysicalPath: %windir%/Web/PowerShellWebAccess/wwwroot

   **예**: `Install-PswaWebApplication -webApplicationName myWebApp -useTestCertificate`

   이 예에서 결과로 표시되는 Windows PowerShell 웹 액세스의 웹 사이트는 `https://<server_name>/myWebApp`입니다.

   > [!NOTE]
   > 권한 부여 규칙을 추가하여 사용자에게 웹 사이트에 대한 액세스가 허용될 때까지는 로그인할 수 없습니다. 자세한 내용은 [제한적인 권한 부여 규칙 구성](#configure-a-restrictive-authorization-rule) 및 [Windows PowerShell 웹 액세스의 권한 부여 규칙 및 보안 기능](authorization-rules-and-security-features-of-windows-powershell-web-access.md)을 참조하세요.

#### <a name="to-configure-the-windows-powershell-web-access-gateway-with-a-genuine-certificate-by-using-install-pswawebapplication-and-iis-manager"></a>Install-PswaWebApplication 및 IIS 관리자를 사용하여 정품 인증서가 사용된 Windows PowerShell 웹 액세스 게이트웨이를 구성하려면

1. 다음 중 하나를 수행하여 Windows PowerShell 세션을 엽니다.

   - Windows 바탕 화면의 작업 표시줄에서 **Windows PowerShell**을 마우스 오른쪽 단추로 클릭합니다.
   - Windows **시작** 화면에서 **Windows PowerShell**을 클릭합니다.

2. 다음을 입력하고 **Enter** 키를 누릅니다.

   `Install-PswaWebApplication`

   이 cmdlet을 실행하면 다음과 같은 게이트웨이 설정이 구성됩니다. 필요에 따라 IIS 관리자 콘솔에서 이러한 설정을 수동으로 변경할 수 있습니다. `WebsiteName` cmdlet의 `WebApplicationName` 및 `Install-PswaWebApplication` 매개 변수에 대한 값을 지정할 수도 있습니다.

   - Path: /pswa
   - ApplicationPool: pswa_pool
   - EnabledProtocols: http
   - PhysicalPath: %windir%/Web/PowerShellWebAccess/wwwroot

3. 다음 중 한 가지를 수행하여 IIS 관리자 콘솔을 엽니다.

   - Windows 바탕 화면에서 Windows 작업 표시줄의 **서버 관리자**를 클릭하여 서버 관리자를 시작합니다. 서버 관리자의 **도구** 메뉴에서 **IIS(인터넷 정보 서비스) 관리자**를 클릭합니다.
   - Windows **시작** 화면에서 **서버 관리자**를 클릭합니다.

4. IIS 관리자 트리 창에서 **사이트** 폴더가 표시될 때까지 Windows PowerShell 웹 액세스가 설치된 서버의 노드를 확장합니다. **사이트** 폴더를 확장합니다.

5. Windows PowerShell 웹 액세스 웹 애플리케이션이 설치된 웹 사이트를 선택합니다.
   **작업** 창에서 **바인딩**을 클릭합니다.

6. **사이트 바인딩** 대화 상자에서 **추가**를 클릭합니다.

7. **사이트 바인딩 추가** 대화 상자의 **유형** 필드에서 **https**를 선택합니다.

8. **SSL 인증서** 필드의 드롭다운 메뉴에서 서명된 인증서를 선택합니다.
   **확인**을 클릭합니다. 인증서를 얻는 방법에 대한 자세한 내용은 이 항목의 [IIS 관리자로 SSL 인증서를 구성하려면](#to-configure-an-ssl-certificate-in-iis-Manager)을 참조하세요.

   이제 Windows PowerShell 웹 액세스 웹 애플리케이션이 서명된 SSL 인증서를 사용하도록 구성됩니다.

   브라우저 창에서 `https://<server_name>/pswa`를 열어 Windows PowerShell 웹 액세스에 액세스할 수 있습니다.

   > [!NOTE]
   > 권한 부여 규칙을 추가하여 사용자에게 웹 사이트에 대한 액세스가 허용될 때까지는 로그인할 수 없습니다. 자세한 내용은 이 항목의 [제한적인 권한 부여 규칙 구성](#configure-a-restrictive-authorization-rule) 및 [Windows PowerShell 웹 액세스의 권한 부여 규칙 및 보안 기능](authorization-rules-and-security-features-of-windows-powershell-web-access.md)을 참조하세요.

### <a name="configure-a-restrictive-authorization-rule"></a>제한적인 권한 부여 규칙 구성

Windows PowerShell Web Access가 설치되고 게이트웨이가 구성되고 나면 사용자는 로그인 페이지를 브라우저에서 열 수 있지만 Windows PowerShell 웹 액세스 관리자가 사용자에게 액세스를 명시적으로 허용할 때까지는 로그인할 수 없습니다. Windows PowerShell 웹 액세스의 액세스 제어는 다음 표에 설명된 여러 Windows PowerShell cmdlet을 통해 관리할 수 있습니다. 권한 부여 규칙을 추가하거나 관리하는 작업에 해당하는 GUI는 없습니다. Windows PowerShell 웹 액세스 cmdlet에 대한 자세한 내용은 참조 항목 [Windows PowerShell 웹 액세스 Cmdlet](/powershell/module/powershellwebaccess/?view=winserver2012r2-ps)을 참조하세요.

Windows PowerShell 웹 액세스 권한 부여 규칙 및 보안에 대한 자세한 내용은 [Windows PowerShell 웹 액세스의 권한 부여 규칙 및 보안 기능](authorization-rules-and-security-features-of-windows-powershell-web-access.md)을 참조하세요.

#### <a name="to-add-a-restrictive-authorization-rule"></a>제한적인 권한 부여 규칙을 추가하려면

1. 다음 중 하나를 수행하여 관리자 권한으로 Windows PowerShell 세션을 엽니다.

   - Windows 바탕 화면의 작업 표시줄에서 **Windows PowerShell**을 마우스 오른쪽 단추로 클릭한 다음 **관리자 권한으로 실행**을 클릭합니다.
   - Windows **시작** 화면에서 **Windows PowerShell**을 마우스 오른쪽 단추로 클릭한 다음 **관리자 권한으로 실행**을 클릭합니다.

2. 세션 구성을 사용하여 사용자 액세스를 제한하는 단계(옵션): 규칙에 사용할 세션 구성이 이미 있는지 확인합니다. 해당 구성을 아직 만들지 않은 경우 [about_Session_Configuration_Files](/powershell/module/microsoft.powershell.core/about/about_session_configurations)에서 세션 구성을 만드는 방법에 대한 지침을 따르세요.

3. 다음을 입력하고 **Enter** 키를 누릅니다.

   `Add-PswaAuthorizationRule -UserName <domain\user | computer\user> -ComputerName <computer_name> -ConfigurationName <session_configuration_name>`

   이 권한 부여 규칙을 통해 특정 사용자는 일반적으로 액세스 권한을 갖고 있는 네트워크상의 한 컴퓨터에만 액세스할 수 있으며, 일반적인 스크립팅 및 cmdlet 환경에 해당하는 특정 세션 구성에 액세스할 수 있습니다.

   다음 예에서는 `JSmith` 도메인의 `Contoso` 라는 사용자에게 `Contoso_214`컴퓨터를 관리하고, `NewAdminsOnly`라는 세션 구성을 사용할 수 있는 액세스 권한이 부여됩니다

   `Add-PswaAuthorizationRule -UserName Contoso\JSmith -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly`

4. `Get-PswaAuthorizationRule` cmdlet 또는 `Test-PswaAuthorizationRule -UserName <domain\user> -ComputerName <computer-name>`을 실행하여 규칙이 생성되어 있는지 확인합니다.

   정의합니다(예: `Test-PswaAuthorizationRule -UserName 'Contoso\JSmith' -ComputerName Contoso_214`).

권한 부여 규칙을 구성하고 나면 권한이 부여된 사용자가 웹 기반 콘솔에 로그인하고 Windows PowerShell 웹 액세스를 사용할 준비가 됩니다.

## <a name="custom-deployment"></a>사용자 지정 배포

서버 관리자의 역할 및 기능 추가 마법사를 사용하여 Windows Server 2012 R2 또는 Windows Server 2012를 실행하는 서버에서 Windows PowerShell 웹 액세스 게이트웨이를 설치할 수 있습니다.
Windows PowerShell 웹 액세스가 설치되면 IIS 관리자에서 게이트웨이 구성을 사용자 지정할 수 있습니다.

### <a name="install-windows-powershell-web-access-using-the-add-roles-and-features-wizard"></a>역할 및 기능 추가 마법사를 사용하여 Windows PowerShell 웹 액세스 설치

1. 서버 관리자가 이미 열려 있으면 다음 단계로 이동합니다. 서버 관리자가 아직 열려 있지 않으면 다음 중 하나를 수행하여 엽니다.

   - Windows 바탕 화면에서 Windows 작업 표시줄의 **서버 관리자**를 클릭하여 서버 관리자를 시작합니다.
   - Windows **시작** 화면에서 **서버 관리자**를 클릭합니다.

2. **관리** 메뉴에서 **역할 및 기능 추가**를 클릭합니다.

3. **설치 유형 선택** 페이지에서 **역할 기반 또는 기능 기반 설치**를 선택합니다.
   **다음**을 클릭합니다.

4. **대상 서버 선택** 페이지에서 서버 풀의 서버를 선택하거나 오프라인 VHD를 선택합니다. 오프라인 VHD를 대상 서버로 선택하려면 먼저 VHD가 탑재될 서버를 선택한 다음 VHD 파일을 선택합니다. 서버를 서버 풀에 추가하는 방법에 대한 자세한 내용은 서버 관리자 도움말을 참조하세요. 대상 서버를 선택하고 나면 **다음**을 클릭합니다.

5. 마법사의 **기능 선택** 페이지에서 **Windows PowerShell**을 확장한 다음 **Windows PowerShell 웹 액세스**를 선택합니다.

6. .NET Framework 4.5와 웹 서버(IIS)의 역할 서비스 등 필수 기능을 추가하라는 메시지가 표시됩니다. 필수 기능을 추가하고 계속합니다.

   > [!NOTE]
   > 역할 및 기능 추가 마법사를 사용하여 Windows PowerShell 웹 액세스를 설치하는 경우 IIS 관리자 스냅인을 포함한 웹 서버(IIS)도 설치합니다. 스냅인과 기타 IIS 관리 도구는 역할 및 기능 추가 마법사를 사용하면 기본적으로 설치됩니다. 하지만 다음 절차에 설명된 대로 Windows PowerShell cmdlet을 사용하여 Windows PowerShell 웹 액세스를 설치하는 경우에는 관리 도구가 기본적으로 추가되지 않습니다.

7. **설치 선택 확인** 페이지에서는 Windows PowerShell 웹 액세스의 기능 파일을 4단계에서 선택한 대상 서버에 저장하지 않을 경우 **대체 원본 경로 지정**을 클릭하고 기능 파일에 대한 경로를 제공합니다. 그렇지 않으면 **설치**를 클릭합니다.

8. **설치**를 클릭하고 나면 설치 진행률, 결과 및 메시지(경고, 오류 또는 Windows PowerShell 웹 액세스에 필요한 설치 후 구성 단계 등)가 **설치 진행률** 페이지에 표시됩니다. Windows PowerShell 웹 액세스가 설치되고 나면 게이트웨이에 필요한 기본 설치 지침이 포함된 추가 정보 파일을 검토하라는 메시지가 표시됩니다. 이러한 지침은 이 항목에도 포함되어 있습니다. 추가 정보 파일의 경로는 `C:\Windows\Web\PowerShellWebAccess\wwwroot\README.txt`입니다.

### <a name="configure-the-gateway"></a>게이트웨이 구성

이 섹션의 지침에는 Windows PowerShell 웹 액세스 웹 애플리케이션을 웹 사이트의 루트 디렉터리가 아닌 하위 디렉터리에 설치하는 방법이 포함되어 있습니다. 이 절차는 `Install-PswaWebApplication` cmdlet에서 수행된 작업에 해당하는 GUI 기반 작업입니다. 이 섹션에는 IIS 관리자를 사용하여 Windows PowerShell 웹 액세스 게이트웨이를 루트 웹 사이트로 구성하는 방법도 포함되어 있습니다.

#### <a name="to-use-iis-manager-to-configure-the-gateway-in-an-existing-website"></a>IIS 관리자를 사용하여 기존 웹 사이트에 게이트웨이를 구성하려면

1. 다음 중 한 가지를 수행하여 IIS 관리자 콘솔을 엽니다.

   - Windows 바탕 화면에서 Windows 작업 표시줄의 **서버 관리자**를 클릭하여 서버 관리자를 시작합니다. 서버 관리자의 **도구** 메뉴에서 **IIS(인터넷 정보 서비스) 관리자**를 클릭합니다.
   - Windows **시작** 화면에서 **IIS(인터넷 정보 서비스) 관리자** 이름의 일부를 입력합니다. **응용 프로그램** 결과에 바로 가기가 표시되면 이를 클릭합니다.

2. Windows PowerShell 웹 액세스의 새로운 애플리케이션 풀을 만듭니다. IIS 관리자 트리 창에서 게이트웨이 서버의 노드를 확장한 다음 **애플리케이션 풀**을 선택하고 **작업** 창에서 **애플리케이션 풀 추가**를 클릭합니다.

3. 이름이 **pswa_pool**인 새로운 애플리케이션 풀을 추가하거나 다른 이름을 입력합니다. **확인**을 클릭합니다.

4. IIS 관리자 트리 창에서 **사이트** 폴더가 표시될 때까지 Windows PowerShell 웹 액세스가 설치된 서버의 노드를 확장합니다. **사이트** 폴더를 선택합니다.

5. Windows PowerShell 웹 액세스 웹 사이트를 추가할 웹 사이트(예: **기본 웹 사이트**)를 마우스 오른쪽 단추로 클릭한 다음 **애플리케이션 추가**를 클릭합니다.

6. **별칭** 필드에 pswa를 입력하거나 다른 별칭을 제공합니다. 이 별칭은 가상 디렉터리 이름이 됩니다. 예를 들어 URL `https://<server-name>/pswa`의 **pswa**는 이 단계에서 지정된 별칭을 나타냅니다.

7. **애플리케이션 풀** 필드에서는 3단계에서 만든 애플리케이션 풀을 선택합니다.

8. **실제 경로** 필드에서 애플리케이션의 위치를 검색합니다. 기본 위치 `$env:windir/Web/PowerShellWebAccess/wwwroot`를 사용할 수 있습니다. **확인**을 클릭합니다.

9. 이 항목에서 [IIS 관리자로 SSL 인증서를 구성하려면](#to-configure-an-ssl-certificate-in-iis-Manager) 절차의 단계를 따릅니다.

10. ![](images/SecurityNote.jpeg)선택적 보안 단계:

    트리 창에서 웹 사이트를 선택한 상태에서 내용 창의 **SSL 설정**을 두 번 클릭합니다.
    **SSL 필요**를 선택한 다음 **작업** 창에서 **적용**을 클릭합니다. 필요에 따라 **SSL 설정** 창에서 Windows PowerShell 웹 액세스 웹 사이트에 연결하는 사용자에게는 클라이언트 인증서가 있어야 할 수 있습니다. 클라이언트 인증서를 통해 클라이언트 디바이스 사용자의 신분을 확인할 수 있습니다. 클라이언트 인증서를 요구하여 Windows PowerShell 웹 액세스의 보안을 강화하는 방법에 대한 자세한 내용은 이 가이드의 [Windows PowerShell 웹 액세스의 권한 부여 규칙 및 보안 기능](authorization-rules-and-security-features-of-windows-powershell-web-access.md)을 참조하세요.

11. 클라이언트 디바이스에서 브라우저 세션을 엽니다. 지원되는 브라우저와 디바이스에 대한 자세한 내용은 이 항목의 [브라우저 및 클라이언트 디바이스 지원](#browser-and-client-device-support)을 참조하세요.

12. 새로운 Windows PowerShell 웹 액세스 웹 사이트인 **https://\<*gateway-server-name*\>/pswa**를 엽니다.

    브라우저에 Windows PowerShell 웹 액세스 콘솔 로그인 페이지가 표시됩니다.

    > [!NOTE]
    > 권한 부여 규칙을 추가하여 사용자에게 웹 사이트에 대한 액세스가 허용될 때까지는 로그인할 수 없습니다. 자세한 내용은 이 항목의 [제한적인 권한 부여 규칙 구성](#configure-a-restrictive-authorization-rule) 및 [Windows PowerShell 웹 액세스의 권한 부여 규칙 및 보안 기능](authorization-rules-and-security-features-of-windows-powershell-web-access.md)을 참조하세요.

13. 관리자 권한(관리자 권한으로 실행)을 사용하여 열린 Windows PowerShell 세션에서 다음 스크립트(여기서 *application_pool_name*은 3단계에서 만든 애플리케이션 풀의 이름을 나타냄)를 실행하여 권한 부여 파일에 대한 액세스 권한을 애플리케이션 풀에 제공합니다.

    ```powershell
    $applicationPoolName = "<application_pool_name>"
    $authorizationFile = "C:\windows\web\powershellwebaccess\data\AuthorizationRules.xml"
    c:\windows\system32\icacls.exe $authorizationFile /grant ('"' + "IIS AppPool\$applicationPoolName" + '":R') > $null
    ```

    권한 부여 파일에 대한 기존 액세스 권한을 확인하려면 다음 명령을 실행합니다.

    ```powershell
    c:\windows\system32\icacls.exe $authorizationFile
    ```

#### <a name="to-use-iis-manager-to-configure-the-gateway-as-a-root-website-with-a-test-certificate"></a>IIS 관리자를 사용하여 테스트 인증서를 사용하는 루트 웹 사이트로 게이트웨이를 구성하려면

1. 다음 중 한 가지를 수행하여 IIS 관리자 콘솔을 엽니다.

   - Windows 바탕 화면에서 Windows 작업 표시줄의 **서버 관리자**를 클릭하여 서버 관리자를 시작합니다. 서버 관리자의 **도구** 메뉴에서 **IIS(인터넷 정보 서비스) 관리자**를 클릭합니다.
   - Windows **시작** 화면에서 **IIS(인터넷 정보 서비스) 관리자** 이름의 일부를 입력합니다. **응용 프로그램** 결과에 바로 가기가 표시되면 이를 클릭합니다.

1. IIS 관리자 트리 창에서 **사이트** 폴더가 표시될 때까지 Windows PowerShell 웹 액세스가 설치된 서버의 노드를 확장합니다. **사이트** 폴더를 선택합니다.

1. **작업** 창에서 **웹 사이트 추가**를 클릭합니다.

1. **Windows PowerShell 웹 액세스**와 같은 웹 사이트의 이름을 입력합니다.

1. 새 웹 사이트의 애플리케이션 풀이 자동으로 만들어집니다. 다른 애플리케이션 풀을 사용하려면 **선택**을 클릭하여 새 웹 사이트와 연결될 애플리케이션 풀을 선택합니다. **애플리케이션 풀 선택** 대화 상자에서 다른 애플리케이션 풀을 선택한 다음 **확인**을 클릭합니다.

1. 에 **실제 경로** 텍스트 상자에서 %windir%/Web/PowerShellWebAccess/wwwroot 이동 합니다.

1. **바인딩** 영역의 **유형** 필드에서 **https**를 선택합니다.

1. 다른 사이트나 애플리케이션에서 사용하고 있지 않은 웹 사이트에 포트 번호를 할당합니다.
   열린 포트를 찾으려면 명령 프롬프트 창에서 **netstat** 명령을 실행합니다. 기본 포트 번호는 443입니다.

   다른 웹 사이트에서 443을 이미 사용하고 있거나 이 포트 번호를 변경해야 할 다른 보안상의 이유가 있는 경우, 기본 포트 번호를 변경합니다. 선택한 포트를 게이트웨이 서버에서 실행 중인 다른 웹 사이트에서 사용하고 있을 경우 **웹 사이트 추가** 대화 상자에서 **확인**을 클릭하면 경고가 표시됩니다. Windows PowerShell 웹 액세스를 실행하려면 미사용 포트를 사용해야 합니다.

1. 조직에 필요한 경우에는 선택적으로 **`www.contoso.com`** 과 같이 조직과 사용자가 쉽게 알아볼 수 있는 호스트 이름을 지정합니다. **확인**을 클릭합니다.

1. 보다 안전한 프로덕션 환경을 위해 반드시 CA에서 서명된 유효한 인증서를 제공하는 것이 좋습니다. 사용자는 HTTPS 웹 사이트를 통해서만 Windows PowerShell 웹 액세스에 연결할 수 있으므로, SSL 인증서를 제공해야 합니다. 인증서를 얻는 방법에 대한 자세한 내용은 이 항목의 [IIS 관리자로 SSL 인증서를 구성하려면](#to-configure-an-ssl-certificate-in-iis-Manager)을 참조하세요.

1. **확인**을 클릭하여 **웹 사이트 추가** 대화 상자를 닫습니다.

1. 관리자 권한(관리자 권한으로 실행)을 사용하여 열린 Windows PowerShell 세션에서 다음 스크립트(여기서 _application_pool_name_은 4단계에서 만든 애플리케이션 풀의 이름을 나타냄)를 실행하여 권한 부여 파일에 대한 액세스 권한을 애플리케이션 풀에 제공합니다.

   ```powershell
   $applicationPoolName = "<application_pool_name>"
   $authorizationFile = "C:\windows\web\powershellwebaccess\data\AuthorizationRules.xml"
   c:\windows\system32\icacls.exe $authorizationFile /grant ('"' + "IIS AppPool\$applicationPoolName" + '":R') > $null
   ```

   권한 부여 파일에 대한 기존 액세스 권한을 확인하려면 다음 명령을 실행합니다.

   ```powershell
   c:\windows\system32\icacls.exe $authorizationFile
   ```

1. IIS 관리자 트리 창에서 새 웹 사이트가 선택된 상태에서 **작업** 창의 **시작** 을 클릭하여 웹 사이트를 시작합니다.

1. 클라이언트 디바이스에서 브라우저 세션을 엽니다. 지원되는 브라우저와 디바이스에 대한 자세한 내용은 이 문서의 [브라우저 및 클라이언트 디바이스 지원](#browser-and-client-device-support)을 참조하세요.

1. 새로운 Windows PowerShell 웹 액세스 웹 사이트를 엽니다.

   루트 웹 사이트가 Windows PowerShell 웹 액세스 폴더를 가리키므로, `https://<gateway_server_name>`을 열면 Windows PowerShell 웹 액세스 로그인 페이지가 브라우저에 표시됩니다. URL에는 **/pswa**를 추가하지 않아도 됩니다.

   > [!NOTE]
   > 권한 부여 규칙을 추가하여 사용자에게 웹 사이트에 대한 액세스가 허용될 때까지는 로그인할 수 없습니다. 자세한 내용은 이 항목의 [제한적인 권한 부여 규칙 구성](#configure-a-restrictive-authorization-rule) 및 [Windows PowerShell 웹 액세스의 권한 부여 규칙 및 보안 기능](authorization-rules-and-security-features-of-windows-powershell-web-access.md)을 참조하세요.

### <a name="configuring-a-restrictive-authorization-rule"></a>제한적인 권한 부여 규칙 구성

Windows PowerShell Web Access가 설치되고 게이트웨이가 구성되고 나면 사용자는 로그인 페이지를 브라우저에서 열 수 있지만 Windows PowerShell 웹 액세스 관리자가 사용자에게 액세스를 명시적으로 허용할 때까지는 로그인할 수 없습니다. Windows PowerShell 웹 액세스의 액세스 제어는 다음 표에 설명된 여러 Windows PowerShell cmdlet을 통해 관리할 수 있습니다. 권한 부여 규칙을 추가하거나 관리하는 작업에 해당하는 GUI는 없습니다. Windows PowerShell 웹 액세스 cmdlet에 대한 자세한 내용은 참조 항목 [Windows PowerShell 웹 액세스 Cmdlet](/powershell/module/powershellwebaccess/?view=winserver2012r2-ps)을 참조하세요.

Windows PowerShell 웹 액세스 권한 부여 규칙 및 보안에 대한 자세한 내용은 [Windows PowerShell 웹 액세스의 권한 부여 규칙 및 보안 기능](authorization-rules-and-security-features-of-windows-powershell-web-access.md)을 참조하세요.

#### <a name="adding-a-restrictive-authorization-rule"></a>제한적인 권한 부여 규칙 추가

1. 다음 중 하나를 수행하여 관리자 권한으로 Windows PowerShell 세션을 엽니다.

   - Windows 바탕 화면의 작업 표시줄에서 **Windows PowerShell**을 마우스 오른쪽 단추로 클릭한 다음 **관리자 권한으로 실행**을 클릭합니다.
   - Windows **시작** 화면에서 **Windows PowerShell**을 마우스 오른쪽 단추로 클릭한 다음 **관리자 권한으로 실행**을 클릭합니다.

1. ![보안 정보](images/SecurityNote.jpeg) 세션 구성을 사용하여 사용자 액세스를 제한하는 단계(옵션):

   규칙에 사용할 세션 구성이 이미 있는지 확인합니다. 해당 구성을 아직 만들지 않은 경우 [about_Session_Configuration_Files](/powershell/module/microsoft.powershell.core/about/about_session_configurations)에서 세션 구성을 만드는 방법에 대한 지침을 따르세요.

1. 다음을 입력하고 **Enter** 키를 누릅니다.

   `Add-PswaAuthorizationRule -UserName <domain\user | computer\user> -ComputerName <computer_name> -ConfigurationName <session_configuration_name>`

   이 권한 부여 규칙을 통해 특정 사용자는 일반적으로 액세스 권한을 갖고 있는 네트워크상의 한 컴퓨터에만 액세스할 수 있으며, 일반적인 스크립팅 및 cmdlet 환경에 해당하는 특정 세션 구성에 액세스할 수 있습니다.

   다음 예에서는 `JSmith` 도메인의 `Contoso` 라는 사용자에게 `Contoso_214`컴퓨터를 관리하고, `NewAdminsOnly`라는 세션 구성을 사용할 수 있는 액세스 권한이 부여됩니다

   `Add-PswaAuthorizationRule -UserName 'Contoso\JSmith' -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly`

1. `Get-PswaAuthorizationRule` cmdlet 또는 `Test-PswaAuthorizationRule -UserName '<domain\user>' -ComputerName <computer-name>`을 실행하여 규칙이 생성되어 있는지 확인합니다.

   정의합니다(예: `Test-PswaAuthorizationRule -UserName 'Contoso\JSmith' -ComputerName Contoso_214`).

   권한 부여 규칙을 구성하고 나면 권한이 부여된 사용자가 웹 기반 콘솔에 로그인하고 Windows PowerShell 웹 액세스를 사용할 준비가 됩니다.

## <a name="configure-a-genuine-certificate"></a>정품 인증서 구성

안전한 프로덕션 환경을 위해 항상 CA(인증 기관)에서 서명된 유효한 SSL 인증서를 사용하세요. 이 섹션의 절차에서는 CA에서 유효한 SSL 인증서를 얻고 적용하는 방법을 설명합니다.

### <a name="to-configure-an-ssl-certificate-in-iis-manager"></a>IIS 관리자로 SSL 인증서를 구성하려면

1. IIS 관리자 트리 창에서 Windows PowerShell 웹 액세스가 설치되어 있는 서버를 선택합니다.

1. 내용 창에서 **서버 인증서**를 두 번 클릭합니다.

1. **작업** 창에서 다음 중 하나를 수행합니다. IIS에서 서버 인증서를 구성하는 방법에 대한 자세한 내용은 [IIS 7에서 서버 인증서 구성](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732230(v=ws.10))을 참조하세요.

   - 네트워크 위치에서 기존의 유효한 인증서를 가져오려면 **가져오기**를 클릭합니다.
   - CA에서 [VeriSign](https://www.verisign.com/), [Thawte](https://www.thawte.com/) 또는 [GeoTrust](https://www.geotrust.com/) 등의 인증서를 요청하려면 **인증서 요청 만들기**를 클릭합니다. 인증서의 일반 이름은 요청의 호스트 헤더와 일치해야 합니다.

     예를 들어 클라이언트 브라우저에서 `http://www.contoso.com/`을 요청하면 일반 이름도 `http://www.contoso.com/`이어야 합니다. 이 방법이 Windows PowerShell 웹 액세스 게이트웨이에 인증서를 제공하는 가장 안전한 방법입니다.

   - 곧바로 사용할 수 있는 인증서를 만든 다음 나중에 필요할 때 CA에서 서명을 받아 사용하려면 **자체 서명된 인증서 만들기**를 클릭합니다. **Windows PowerShell 웹 액세스**와 같이 자체 서명된 인증서에 알기 쉬운 이름을 지정합니다. 이 방법은 안전하지 않으므로 개인 테스트 환경용으로만 사용하는 것이 좋습니다.

1. 인증서를 만들거나 구한 다음, IIS 관리자 트리 창에서 인증서가 적용될 웹 사이트(예: **기본 웹 사이트**)를 IIS 관리자 트리 창에서 선택한 다음 **작업** 창에서 **바인딩**을 클릭합니다.

1. 해당 사이트의 바인딩이 표시되지 않은 경우, **사이트 바인딩 추가** 대화 상자에서 사이트의 **https** 바인딩을 추가합니다. 자체 서명된 인증서를 사용하지 않을 경우에는 이 절차의 3단계에서 설명된 호스트 이름을 지정합니다. 자체 서명된 인증서를 사용할 경우에는 이 단계가 필요하지 않습니다.

1. 이 절차의 3단계에서 얻거나 만든 인증서를 선택한 다음 **확인**을 클릭합니다.

## <a name="using-the-web-based-windows-powershell-console"></a>웹 기반 Windows PowerShell 콘솔 사용

이 항목에 설명된 대로 Windows PowerShell 웹 액세스가 설치되고 게이트웨이 구성이 완료된 다음에는 Windows PowerShell 웹 기반 콘솔을 사용할 수 있습니다. 웹 기반 콘솔에서 시작하는 방법에 대한 자세한 내용은 [웹 기반 Windows PowerShell 콘솔 사용](use-the-web-based-windows-powershell-console.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[Internet Information Services (IIS) 7.0 Documentation](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc753433(v=ws.10))(IIS(인터넷 정보 서비스) 7.0 설명서)

[IIS 관리자 7.0 도움말](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732664(v=ws.11))

[Configure Web Server Security (IIS 7)](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731278(v=ws.10))(웹 서버 보안 구성(IIS 7))

[IPsec Deployment Resources](/previous-versions/windows/it-pro/windows-server-2003/cc776369(v=ws.10))(IPsec 배포 리소스)
