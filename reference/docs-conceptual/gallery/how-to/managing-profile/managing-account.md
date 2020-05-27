---
ms.date: 09/05/2018
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: PowerShell 갤러리 계정 설정
ms.openlocfilehash: 7f67311b42123f247a00a9c7a5bf775685b64d48
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83560460"
---
# <a name="powershell-gallery-account-settings"></a><span data-ttu-id="9f5dd-103">PowerShell 갤러리 계정 설정</span><span class="sxs-lookup"><span data-stu-id="9f5dd-103">PowerShell Gallery Account Settings</span></span>

<span data-ttu-id="9f5dd-104">PowerShell 갤러리 계정은 ID에 연결되어 공개적으로 표시되는 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="9f5dd-104">Your PowerShell Gallery account is a publicly visible name that is linked to an identity.</span></span> <span data-ttu-id="9f5dd-105">해당 ID는 Microsoft ID(예: `user@hotmail.com` 또는 `user@outlook.com`)이거나 AAD(Azure Active Directory) 계정입니다.</span><span class="sxs-lookup"><span data-stu-id="9f5dd-105">That identity is either a Microsoft ID, like `user@hotmail.com` or `user@outlook.com`, or an Azure Active Directory (AAD) account.</span></span>

<span data-ttu-id="9f5dd-106">PowerShell 갤러리에서 제공하는 계정 설정은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9f5dd-106">The PowerShell Gallery provides the following account settings:</span></span>

- <span data-ttu-id="9f5dd-107">PowerShell 갤러리 계정과 연결된 이메일 계정</span><span class="sxs-lookup"><span data-stu-id="9f5dd-107">The email account associated with your PowerShell Gallery account</span></span>
- <span data-ttu-id="9f5dd-108">PowerShell 갤러리에서 보낸 이메일 알림에 대한 옵션</span><span class="sxs-lookup"><span data-stu-id="9f5dd-108">Options for email notifications sent from the PowerShell Gallery</span></span>
- <span data-ttu-id="9f5dd-109">PowerShell 갤러리 계정과 연결된 사용자 계정</span><span class="sxs-lookup"><span data-stu-id="9f5dd-109">The user account associated with your PowerShell Gallery account</span></span>
- <span data-ttu-id="9f5dd-110">PowerShell 갤러리 계정과 연결된 그림</span><span class="sxs-lookup"><span data-stu-id="9f5dd-110">The picture associated with your PowerShell Gallery account</span></span>

## <a name="email-address"></a><span data-ttu-id="9f5dd-111">메일 주소</span><span class="sxs-lookup"><span data-stu-id="9f5dd-111">Email address</span></span>

<span data-ttu-id="9f5dd-112">이메일 주소는 PowerShell 갤러리 알림의 대상입니다.</span><span class="sxs-lookup"><span data-stu-id="9f5dd-112">The email address is the destination for PowerShell Gallery notifications.</span></span> <span data-ttu-id="9f5dd-113">로그인 계정과 일치할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9f5dd-113">It does not have to match the login account.</span></span> <span data-ttu-id="9f5dd-114">액세스할 수 있는 이메일 계정을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9f5dd-114">You may use any email account you have access to.</span></span> <span data-ttu-id="9f5dd-115">이메일 주소는 PowerShell 갤러리에서 다른 사용자에게 직접 제공하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9f5dd-115">Your email address is never directly provided by the PowerShell Gallery to other users.</span></span>

![이메일 주소 변경](media/managing-account/PSGallery_AcccountEmailAddress.png)

<span data-ttu-id="9f5dd-117">새 이메일 주소를 입력하면 PowerShell 갤러리에서 해당 주소로 확인 메일을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="9f5dd-117">When you enter a new email address, the PowerShell Gallery sends a verification mail to that address.</span></span> <span data-ttu-id="9f5dd-118">확인 메일에는 변경 프로세스를 완료하기 위해 PowerShell 갤러리에 다시 연결되는 링크가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9f5dd-118">The verification mail contains a link back to the PowerShell Gallery to complete the change process.</span></span> <span data-ttu-id="9f5dd-119">확인 프로세스가 완료될 때까지 모든 알림은 이전 주소로 보내집니다.</span><span class="sxs-lookup"><span data-stu-id="9f5dd-119">Until you complete the verification process, all notifications are sent to the previous address.</span></span>

## <a name="email-notifications"></a><span data-ttu-id="9f5dd-120">이메일 알림</span><span class="sxs-lookup"><span data-stu-id="9f5dd-120">Email notifications</span></span>

<span data-ttu-id="9f5dd-121">PowerShell 갤러리에서 제공하는 알림 옵션은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9f5dd-121">PowerShell Gallery provides the following notification options:</span></span>

- <span data-ttu-id="9f5dd-122">사용자가 PowerShell 갤러리를 통해 연락할 수 있음</span><span class="sxs-lookup"><span data-stu-id="9f5dd-122">Users can contact me through the PowerShell Gallery</span></span>
- <span data-ttu-id="9f5dd-123">내 계정을 사용하여 PowerShell 갤러리에 패키지를 푸시할 때 알림</span><span class="sxs-lookup"><span data-stu-id="9f5dd-123">Notify me when an package is pushed to the PowerShell Gallery using my account</span></span>

![이메일 주소 변경](media/managing-account/PSGallery_AccountEmailOptions.png)

<span data-ttu-id="9f5dd-125">페이지에서 설명한 대로 PowerShell 갤러리의 중요 알림은 해제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9f5dd-125">As noted on the page, critical notifications from the PowerShell Gallery can't be disabled.</span></span>
<span data-ttu-id="9f5dd-126">이러한 개체는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9f5dd-126">These include:</span></span>

- <span data-ttu-id="9f5dd-127">보안 알림</span><span class="sxs-lookup"><span data-stu-id="9f5dd-127">Security notifications</span></span>
- <span data-ttu-id="9f5dd-128">PowerShell 갤러리 관리자의 계정 관리 알림</span><span class="sxs-lookup"><span data-stu-id="9f5dd-128">Account management notifications from PowerShell Gallery administrators</span></span>
- <span data-ttu-id="9f5dd-129">만든 제출에 대해 PowerShell 갤러리에서 실행한 테스트와 관련된 알림</span><span class="sxs-lookup"><span data-stu-id="9f5dd-129">Notifications about the tests run by the PowerShell Gallery for submissions you have made</span></span>

## <a name="change-your-login-account"></a><span data-ttu-id="9f5dd-130">로그인 계정 변경</span><span class="sxs-lookup"><span data-stu-id="9f5dd-130">Change your login account</span></span>

<span data-ttu-id="9f5dd-131">로그인 계정을 변경하려면 현재 계정으로 로그인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f5dd-131">To change the login account, you must be signed in with the current account.</span></span> <span data-ttu-id="9f5dd-132">변경을 완료하려면 다음 단계를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9f5dd-132">Use the following steps to complete the change.</span></span>

![로그인 계정 설정](media/managing-account/PSGallery_LoginAccountSettings.png)

1. <span data-ttu-id="9f5dd-134">**계정 변경**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9f5dd-134">Click on **Change Account**.</span></span> <span data-ttu-id="9f5dd-135">팝업 창에서 로그인 계정을 변경하면 PowerShell 갤러리에 있는 해당 계정의 모든 사용에 적용된다고 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="9f5dd-135">A pop-up window explains that changing the login account applies to all uses of that account in the PowerShell Gallery.</span></span> <span data-ttu-id="9f5dd-136">정보를 검토한 다음, **확인**을 클릭하여 계속합니다.</span><span class="sxs-lookup"><span data-stu-id="9f5dd-136">Review the information, then click **OK** to continue.</span></span>

   ![로그인 계정 설정](media/managing-account/PSGallery_LoginAccountChange-1.png)

2. <span data-ttu-id="9f5dd-138">그런 다음, _새 계정_을 사용하여 로그인하라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="9f5dd-138">You are then prompted to sign in using the _new account_.</span></span>

   ![로그인 계정 설정](media/managing-account/PSGallery_LoginAccountChange-2.png)

3. <span data-ttu-id="9f5dd-140">**다음**을 클릭하면 현재 계정을 사용하여 로그인했다는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="9f5dd-140">When you click **Next**, you see a message that you are signed in using the current account.</span></span>
   <span data-ttu-id="9f5dd-141">**다른 계정으로 로그아웃 및 로그인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9f5dd-141">Click **Sign out and sign in with a different account**.</span></span>

   ![로그인 계정 설정](media/managing-account/PSGallery_LoginAccountChange-3.png)

4. <span data-ttu-id="9f5dd-143">새 계정의 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="9f5dd-143">Enter the password of the new account.</span></span> <span data-ttu-id="9f5dd-144">암호가 입력되면 로그인 계정이 업데이트되었음을 보여 주는 [계정 설정] 페이지로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="9f5dd-144">After entering the password, you are returned to the Account Settings page showing you that the login account has been updated.</span></span>

## <a name="enable-two-factor-authentication-2fa"></a><span data-ttu-id="9f5dd-145">2FA(2단계 인증) 사용</span><span class="sxs-lookup"><span data-stu-id="9f5dd-145">Enable Two-Factor Authentication (2FA)</span></span>

<span data-ttu-id="9f5dd-146">2단계 인증은 PowerShell 갤러리에 수동으로 게시하는 모든 사용자에게 권장됩니다.</span><span class="sxs-lookup"><span data-stu-id="9f5dd-146">Two-factor authentication is recommended for all users who publish manually to the PowerShell Gallery.</span></span> <span data-ttu-id="9f5dd-147">2단계 인증을 사용하려면 로그인 계정에 둘 이상의 인증 양식이 등록되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f5dd-147">To enable two-factor authentication, the login account must have at least two forms of authentication registered.</span></span> <span data-ttu-id="9f5dd-148">한 양식은 암호이고, 그 밖의 다른 양식은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9f5dd-148">One is a password and the other forms can be:</span></span>

- <span data-ttu-id="9f5dd-149">문자 메시지를 받을 수 있는 전화 번호</span><span class="sxs-lookup"><span data-stu-id="9f5dd-149">A phone number that can receive text messages</span></span>
- <span data-ttu-id="9f5dd-150">휴대폰용 등록된 인증자 애플리케이션(예: Microsoft Authenticator)</span><span class="sxs-lookup"><span data-stu-id="9f5dd-150">A registered authenticator application, such as Microsoft Authenticator for your mobile phone</span></span>

<span data-ttu-id="9f5dd-151">이러한 인증 양식은 AAD 계정 정보 또는 Microsoft ID 계정 보안 설정에서 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f5dd-151">These forms of authentication must be configured in your AAD account information or in your Microsoft ID Account Security settings.</span></span>

<span data-ttu-id="9f5dd-152">2FA를 사용하도록 설정되면 PowerShell 갤러리에 로그인할 때마다 구성된 인증 양식을 사용하여 인증해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f5dd-152">Once 2FA is enabled, you are required to authenticate using the configured forms of authentication every time you sign in to the PowerShell Gallery.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9f5dd-153">PowerShell 갤러리 사이트에 대해 2단계 인증을 사용하도록 설정하는 경우 로그인 계정의 모든 사용에 대해 2FA를 사용하도록 설정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9f5dd-153">Enabling two-factor authentication for the PowerShell Gallery site does not require you to enable 2FA for all uses of your login account.</span></span> <span data-ttu-id="9f5dd-154">자세한 내용은 [2단계 인증 정보](https://support.microsoft.com/help/12408/microsoft-account-about-two-step-verification)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9f5dd-154">For more information, see [About two-step verification](https://support.microsoft.com/help/12408/microsoft-account-about-two-step-verification).</span></span>

## <a name="change-your-profile-picture"></a><span data-ttu-id="9f5dd-155">프로필 사진 변경</span><span class="sxs-lookup"><span data-stu-id="9f5dd-155">Change your profile picture</span></span>

<span data-ttu-id="9f5dd-156">PowerShell 갤러리는 Gravatar를 사용하여 프로필과 연결된 그림을 저장하고 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="9f5dd-156">The PowerShell Gallery relies on Gravatar to store and display the picture associated with your profile.</span></span> <span data-ttu-id="9f5dd-157">프로필 이미지를 업데이트하려면 [Gravatar.com](http://www.gravatar.com/)을 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="9f5dd-157">To update your profile image, visit [Gravatar.com](http://www.gravatar.com/).</span></span>
