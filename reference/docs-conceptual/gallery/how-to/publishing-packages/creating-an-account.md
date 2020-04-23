---
ms.date: 09/11/2018
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: PowerShell 갤러리 계정 만들기
ms.openlocfilehash: f43d7e65bb8bf9a9bbdda9790cc622786377fa38
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2020
ms.locfileid: "78278786"
---
# <a name="creating-a-powershell-gallery-account"></a>PowerShell 갤러리 계정 만들기

PowerShell 갤러리 계정은 PowerShell 갤러리에 게시하기 전에 만들어야 합니다.
PowerShell 갤러리 계정은 이메일을 사용하도록 설정된 로그인 계정에 연결해야 합니다. 이 계정은 Azure Active Directory 계정 또는 Microsoft ID(예: outlook.com 또는 hotmail.com의 이메일 계정)일 수 있습니다.

PowerShell 갤러리 계정을 만들려면 [https://PowerShellGallery.com](https://PowerShellGallery.com)으로 이동하고, 다음 이미지와 같이 **로그인**을 클릭합니다.

![새 계정 등록](media/creating-an-account/CreateAccount-Register.png)

Azure Active Directory 계정을 사용하려면 **회사 또는 학교 계정**을 선택하고 자신의 계정으로 로그인합니다. Microsoft ID를 사용하려면 **개인 계정**을 선택하고 로그인합니다.

다음으로, PowerShell 갤러리에 대한 사용자 이름을 만들라는 메시지가 표시됩니다. 사용 약관 및 개인 정보 처리 방침을 검토하고, 사용자 이름을 입력한 다음, **등록**을 클릭합니다.

> [!NOTE]
> 계정 이름은 만들고 나면 변경할 수 없습니다. 자세한 내용은 [패키지 소유자 관리](managing-package-owners.md)를 참조하세요.

## <a name="recommended-practices-for-powershell-gallery-accounts"></a>PowerShell 갤러리 계정에 권장되는 사례

PowerShell 갤러리 계정에 사용되는 이메일 계정은 적극적으로 모니터링해야 합니다. PowerShell 갤러리 패키지 소유자와의 모든 커뮤니케이션은 이 메일 주소를 통해 이루어집니다. PowerShell 갤러리 운영 팀에서 패키지 소유자에게 연락할 수 없는 경우 Microsoft에서 패키지를 삭제해야 할 수 있습니다.

PowerShell 갤러리에 게시하는 조직에서는 이러한 목적을 위해 고유한 외부 계정을 만드는 경우가 많습니다. 이메일 전달을 사용하여 조직 내 주소로 알림을 전달하는 것이 좋습니다.

여러 소유자가 패키지와 연결된 경우 모든 PowerShell 갤러리 알림이 모든 소유자에게 전송됩니다. 자세한 내용은 [패키지 소유자 관리](managing-package-owners.md)를 참조하세요.
