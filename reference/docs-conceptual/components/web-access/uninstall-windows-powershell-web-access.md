---
ms.date: 08/23/2017
keywords: powershell,cmdlet
title: Windows PowerShell 웹 액세스 제거
ms.openlocfilehash: 22c874d766445dccedd8494097daf16c30fa66ff
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55682508"
---
# <a name="uninstall-windows-powershell-web-access"></a>Windows PowerShell 웹 액세스 제거

업데이트됨: 2013년 6월 24일

적용 대상: Windows Server 2012 R2, Windows Server 2012

이 항목의 단계에서는 Windows PowerShell 웹 액세스 웹 사이트 및 해당 애플리케이션을 설치된 게이트웨이 서버에서 제거합니다.

## <a name="notify-users"></a>사용자에게 알림

시작하기 전에 웹 기반 콘솔의 사용자에게 웹 사이트가 제거됨을 알립니다.

자동으로 설치된 IIS나 기타 기능은 Windows PowerShell 웹 액세스에서 실행되어야 하므로, Windows PowerShell 웹 액세스를 제거해도 제거되지 않습니다.
제거 프로세스에서는 Windows PowerShell 웹 액세스가 종속된 기능을 설치된 상태로 남겨 두기 때문에 필요한 경우 이러한 기능을 별도로 제거할 수 있습니다.

## <a name="recommended-quick-uninstallation"></a>권장(빠른) 제거

이 섹션의 절차에서는 Windows PowerShell cmdlet을 사용하여

- Windows PowerShell 웹 액세스 웹 애플리케이션 및
- Windows PowerShell 웹 액세스 기능을

모두 제거할 수 있습니다.

### <a name="step-1-delete-the-web-application-using-cmdlets"></a>1단계: Cmdlet을 사용 하 여 웹 응용 프로그램 삭제

1. 다음 중 하나를 수행하여 Windows PowerShell 세션을 엽니다.

    -   Windows 바탕 화면의 작업 표시줄에서 **Windows PowerShell**을 마우스 오른쪽 단추로 클릭합니다.

    -   Windows **시작** 화면에서 **Windows PowerShell**을 클릭합니다.

2. `Uninstall-PswaWebApplication`을 입력하고 **Enter** 키를 누릅니다.
   1. 고유의 사용자 지정 웹 사이트 이름을 지정한 경우 `-WebsiteName` 매개 변수를 명령에 추가하고 웹 사이트 이름을 지정합니다.

        `Uninstall-PswaWebApplication -WebsiteName <web-site-name>`
   1. 기본 애플리케이션(**pswa**)이 아닌 사용자 지정 웹 애플리케이션을 사용한 경우 `-WebApplicationName` 매개 변수를 명령에 추가하고 웹 애플리케이션의 이름을 지정합니다.

        `Uninstall-PswaWebApplication -WebApplicationName <web-application-name>`
   1. 테스트 인증서를 사용하는 경우, 다음 예에서와 같이 cmdlet에 `DeleteTestCertificate` 매개 변수를 추가합니다.

        `Uninstall-PswaWebApplication -DeleteTestCertificate`

### <a name="step-2-uninstall-windows-powershell-web-access-using-cmdlets"></a>2단계: Cmdlet을 사용 하 여 Windows PowerShell 웹 액세스 제거

1. 다음 중 하나를 수행하여 관리자 권한으로 Windows PowerShell 세션을 엽니다. 세션이가 이미 열려 있으면 다음 단계로 이동합니다.

    -   Windows 바탕 화면의 작업 표시줄에서 **Windows PowerShell**을 마우스 오른쪽 단추로 클릭한 다음 **관리자 권한으로 실행**을 클릭합니다.

    -   Windows **시작** 화면에서 **Windows PowerShell**을 마우스 오른쪽 단추로 클릭한 다음 **관리자 권한으로 실행**을 클릭합니다.

1. 다음을 입력하고 **Enter** 키를 누릅니다. 여기서 *computer_name*은 Windows PowerShell 웹 액세스를 제거할 원격 서버를 나타냅니다. 제거 작업에 필요한 경우 `-Restart` 매개 변수를 추가하여 대상 서버를 자동으로 다시 시작할 수 있습니다.

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -ComputerName <computer_name> -Restart

    역할 및 기능을 오프라인 VHD에서 제거하려는 경우에는 `-ComputerName` 매개 변수와 `-VHD` 매개 변수를 모두 추가해야 합니다. `-ComputerName` 매개 변수에는 VHD를 탑재할 서버의 이름이 포함되며, `-VHD` 매개 변수에는 지정된 서버에서의 VHD 파일 경로가 포함됩니다.

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -VHD <path> -ComputerName <computer_name> -Restart

1. 제거가 완료되면 서버 관리자에서 **모든 서버** 페이지를 열고 기능을 제거한 서버를 선택한 후 선택한 서버 페이지에서 **역할 및 기능** 타일을 확인하여 Windows PowerShell 웹 액세스가 제거되었는지 확인합니다.

    또한 선택한 서버(Get-WindowsFeature -ComputerName &lt;*computer_name*&gt;)를 대상으로 `Get-WindowsFeature` cmdlet을 실행하여 서버에 설치된 역할 및 기능 목록을 볼 수 있습니다.

## <a name="custom-uninstallation"></a>사용자 지정 제거

이 섹션의 절차를 따라서 서버 관리자의 역할 및 기능 제거 마법사 및 IIS 관리자 콘솔을 사용하여 Windows PowerShell 웹 액세스 웹 애플리케이션 및 Windows PowerShell 웹 액세스 기능을 모두 제거할 수 있습니다.

### <a name="step-1-delete-the-web-application-using-iis-manager"></a>1단계: IIS 관리자를 사용 하 여 웹 응용 프로그램 삭제


1. 다음 중 한 가지를 수행하여 IIS 관리자 콘솔을 엽니다. 콘솔이 이미 열려 있으면 다음 단계로 이동합니다.

    -   Windows 바탕 화면에서 Windows 작업 표시줄의 **서버 관리자**를 클릭하여 서버 관리자를 시작합니다. 서버 관리자의 **도구** 메뉴에서 **IIS(인터넷 정보 서비스) 관리자**를 클릭합니다.

    -   Windows **시작** 화면에서 **IIS(인터넷 정보 서비스) 관리자** 이름의 일부를 입력합니다. **응용 프로그램** 결과에 바로 가기가 표시되면 이를 클릭합니다.

1. IIS 관리자의 트리 창에서 Windows PowerShell 웹 액세스 웹 애플리케이션이 실행 중인 웹 사이트를 선택합니다.

1. **작업** 창의 **웹 사이트 관리**에서 **중지**를 클릭합니다.

1. 트리 창에서 Windows PowerShell 웹 액세스 웹 애플리케이션이 실행 중인 웹 사이트의 웹 애플리케이션을 마우스 오른쪽 단추로 클릭한 다음 **제거**를 클릭합니다.

1. 트리 창에서 **애플리케이션 풀**을 선택하고 Windows PowerShell 웹 액세스 애플리케이션 폴더를 선택한 후 **작업** 창에서 **중지**를 선택하고 내용 창에서 **제거**를 클릭합니다.

1. IIS 관리자를 닫습니다.

> ![경고](images/SecurityNote.jpeg)**참고**:
>
> 인증서는 제거 과정에서 제거되지 않습니다.
>
> 자체 서명된 인증서를 만들었거나 테스트 인증서를 사용한 경우에 이 인증서를 제거하려면 IIS 관리자에서 해당 인증서를 삭제합니다.

### <a name="step-2-uninstall-windows-powershell-web-access-using-the-remove-roles-and-features-wizard"></a>2단계: 역할 제거 및 기능 마법사를 사용 하 여 Windows PowerShell 웹 액세스 제거

1. 서버 관리자가 이미 열려 있으면 다음 단계로 이동합니다. 서버 관리자가 아직 열려 있지 않으면 다음 중 하나를 수행하여 엽니다.

    -   Windows 바탕 화면에서 Windows 작업 표시줄의 **서버 관리자**를 클릭하여 서버 관리자를 시작합니다.

    -   Windows **시작** 화면에서 **서버 관리자**를 클릭합니다.

1. **관리** 메뉴에서 **역할 및 기능 제거**를 클릭합니다.

1. **대상 서버 선택** 페이지에서 기능을 제거할 서버나 오프라인 VHD를 선택합니다. 오프라인 VHD를 선택하려면 먼저 VHD가 탑재될 서버를 선택한 다음 VHD 파일을 선택합니다. 대상 서버를 선택하고 나면 **다음**을 클릭합니다.

1. 다시 **다음** 을 클릭하여 **기능 제거** 페이지로 이동합니다.

1. **Windows PowerShell 웹 액세스**확인란의 선택을 취소하고 **다음**을 클릭합니다.

1. **제거 선택 확인** 페이지에서 **제거**를 클릭합니다.

## <a name="see-also"></a>참고 항목

- [Windows PowerShell 웹 액세스 설치 및 사용](install-and-use-windows-powershell-web-access.md)
- [IIS 관리자 7.0 도움말](https://technet.microsoft.com/library/cc732664.aspx)