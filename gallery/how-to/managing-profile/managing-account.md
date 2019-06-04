---
ms.date: 09/05/2018
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: PowerShell 갤러리 계정 설정
ms.openlocfilehash: ebe784ec5aae5ff3a4d444d12a168ef38aaef65f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084523"
---
# <a name="powershell-gallery-account-settings"></a>PowerShell 갤러리 계정 설정

PowerShell 갤러리 계정은 ID에 연결되어 공개적으로 표시되는 이름입니다. 해당 ID는 Microsoft ID(예: `user@hotmail.com` 또는 `user@outlook.com`)이거나 AAD(Azure Active Directory) 계정입니다.

PowerShell 갤러리에서 제공하는 계정 설정은 다음과 같습니다.

- PowerShell 갤러리 계정과 연결된 이메일 계정
- PowerShell 갤러리에서 보낸 이메일 알림에 대한 옵션
- PowerShell 갤러리 계정과 연결된 사용자 계정
- PowerShell 갤러리 계정과 연결된 그림

## <a name="email-address"></a>메일 주소

이메일 주소는 PowerShell 갤러리 알림의 대상입니다. 로그인 계정과 일치할 필요가 없습니다. 액세스할 수 있는 이메일 계정을 사용할 수 있습니다. 이메일 주소는 PowerShell 갤러리에서 다른 사용자에게 직접 제공하지 않습니다.

![이메일 주소 변경](../../Images/PSGallery_AcccountEmailAddress.png)

새 이메일 주소를 입력하면 PowerShell 갤러리에서 해당 주소로 확인 메일을 보냅니다. 확인 메일에는 변경 프로세스를 완료하기 위해 PowerShell 갤러리에 다시 연결되는 링크가 포함되어 있습니다. 확인 프로세스가 완료될 때까지 모든 알림은 이전 주소로 보내집니다.

## <a name="email-notifications"></a>이메일 알림

PowerShell 갤러리에서 제공하는 알림 옵션은 다음과 같습니다.

- 사용자가 PowerShell 갤러리를 통해 연락할 수 있음
- 내 계정을 사용하여 PowerShell 갤러리에 패키지를 푸시할 때 알림

![이메일 주소 변경](../../Images/PSGallery_AccountEmailOptions.png)

페이지에서 설명한 대로 PowerShell 갤러리의 중요 알림은 해제할 수 없습니다.
몇 가지 작업이 있습니다.

- 보안 알림
- PowerShell 갤러리 관리자의 계정 관리 알림
- 만든 제출에 대해 PowerShell 갤러리에서 실행한 테스트와 관련된 알림

## <a name="change-your-login-account"></a>로그인 계정 변경

로그인 계정을 변경하려면 현재 계정으로 로그인해야 합니다. 변경을 완료하려면 다음 단계를 사용합니다.

![로그인 계정 설정](../../Images/PSGallery_LoginAccountSettings.png)

1. **계정 변경**을 클릭합니다. 팝업 창에서 로그인 계정을 변경하면 PowerShell 갤러리에 있는 해당 계정의 모든 사용에 적용된다고 설명합니다. 정보를 검토한 다음, **확인**을 클릭하여 계속합니다.

   ![로그인 계정 설정](../../Images/PSGallery_LoginAccountChange-1.png)

2. 그런 다음, _새 계정_을 사용하여 로그인하라는 메시지가 표시됩니다.

   ![로그인 계정 설정](../../Images/PSGallery_LoginAccountChange-2.png)

3. **다음**을 클릭하면 현재 계정을 사용하여 로그인했다는 메시지가 표시됩니다.
   **다른 계정으로 로그아웃 및 로그인**을 클릭합니다.

   ![로그인 계정 설정](../../Images/PSGallery_LoginAccountChange-3.png)

4. 새 계정의 암호를 입력합니다. 암호가 입력되면 로그인 계정이 업데이트되었음을 보여 주는 [계정 설정] 페이지로 돌아갑니다.


## <a name="enable-two-factor-authentication-2fa"></a>2FA(2단계 인증) 사용

2단계 인증은 PowerShell 갤러리에 수동으로 게시하는 모든 사용자에게 권장됩니다. 2단계 인증을 사용하려면 로그인 계정에 둘 이상의 인증 양식이 등록되어 있어야 합니다. 한 양식은 암호이고, 그 밖의 다른 양식은 다음과 같습니다.

- 문자 메시지를 받을 수 있는 전화 번호
- 휴대폰용 등록된 인증자 애플리케이션(예: Microsoft Authenticator)

이러한 인증 양식은 AAD 계정 정보 또는 Microsoft ID 계정 보안 설정에서 구성해야 합니다.

2FA를 사용하도록 설정되면 PowerShell 갤러리에 로그인할 때마다 구성된 인증 양식을 사용하여 인증해야 합니다.

> [!IMPORTANT]
> PowerShell 갤러리 사이트에 대해 2단계 인증을 사용하도록 설정하는 경우 로그인 계정의 모든 사용에 대해 2FA를 사용하도록 설정할 필요가 없습니다. 자세한 내용은 [2단계 인증 정보](https://support.microsoft.com/help/12408/microsoft-account-about-two-step-verification)를 참조하세요.

## <a name="change-your-profile-picture"></a>프로필 사진 변경

PowerShell 갤러리는 Gravatar를 사용하여 프로필과 연결된 그림을 저장하고 표시합니다. 프로필 이미지를 업데이트하려면 [Gravatar.com](http://www.gravatar.com/)을 방문하세요.
