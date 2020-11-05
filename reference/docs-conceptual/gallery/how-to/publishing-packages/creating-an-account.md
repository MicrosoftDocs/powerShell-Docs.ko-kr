---
ms.date: 09/11/2018
title: PowerShell 갤러리 계정 만들기
description: 이 문서에서는 PowerShell 갤러리의 사용자 계정 요구 사항을 설명합니다.
ms.openlocfilehash: 24c7531e61128415a284d1b438b43f3af0d1053a
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92662610"
---
# <a name="creating-a-powershell-gallery-account"></a><span data-ttu-id="30512-103">PowerShell 갤러리 계정 만들기</span><span class="sxs-lookup"><span data-stu-id="30512-103">Creating a PowerShell Gallery account</span></span>

<span data-ttu-id="30512-104">PowerShell 갤러리 계정은 PowerShell 갤러리에 게시하기 전에 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="30512-104">You must create a PowerShell Gallery account before publishing anything to the PowerShell Gallery.</span></span>
<span data-ttu-id="30512-105">PowerShell 갤러리 계정은 이메일을 사용하도록 설정된 로그인 계정에 연결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="30512-105">PowerShell Gallery accounts must be linked to an email-enabled login account.</span></span> <span data-ttu-id="30512-106">이 계정은 Azure Active Directory 계정 또는 Microsoft ID(예: outlook.com 또는 hotmail.com의 이메일 계정)일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30512-106">This account can be an Azure Active Directory account or a Microsoft ID, like an email account from outlook.com or hotmail.com.</span></span>

<span data-ttu-id="30512-107">PowerShell 갤러리 계정을 만들려면 [https://PowerShellGallery.com](https://PowerShellGallery.com)으로 이동하고, 다음 이미지와 같이 **로그인** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="30512-107">To create a PowerShell Gallery account, go to [https://PowerShellGallery.com](https://PowerShellGallery.com) and click on **Sign in** as shown in the following image.</span></span>

![새 계정 등록](media/creating-an-account/CreateAccount-Register.png)

<span data-ttu-id="30512-109">Azure Active Directory 계정을 사용하려면 **회사 또는 학교 계정** 을 선택하고 자신의 계정으로 로그인합니다.</span><span class="sxs-lookup"><span data-stu-id="30512-109">To use an Azure Active Directory account, select **Work or School Account** , and sign in with your account.</span></span> <span data-ttu-id="30512-110">Microsoft ID를 사용하려면 **개인 계정** 을 선택하고 로그인합니다.</span><span class="sxs-lookup"><span data-stu-id="30512-110">To use a Microsoft ID, choose **Personal Account** and sign in.</span></span>

<span data-ttu-id="30512-111">다음으로, PowerShell 갤러리에 대한 사용자 이름을 만들라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="30512-111">Next, you are prompted to create a username for the PowerShell Gallery.</span></span> <span data-ttu-id="30512-112">사용 약관 및 개인 정보 처리 방침을 검토하고, 사용자 이름을 입력한 다음, **등록** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="30512-112">Review the Terms of Use and Privacy Policy, enter a username, and then click **Register**.</span></span>

> [!NOTE]
> <span data-ttu-id="30512-113">계정 이름은 만들고 나면 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="30512-113">The account name cannot be changed once it is created.</span></span> <span data-ttu-id="30512-114">자세한 내용은 [패키지 소유자 관리](managing-package-owners.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="30512-114">For more information, see [Managing Package Owners](managing-package-owners.md).</span></span>

## <a name="recommended-practices-for-powershell-gallery-accounts"></a><span data-ttu-id="30512-115">PowerShell 갤러리 계정에 권장되는 사례</span><span class="sxs-lookup"><span data-stu-id="30512-115">Recommended practices for PowerShell Gallery accounts</span></span>

<span data-ttu-id="30512-116">PowerShell 갤러리 계정에 사용되는 이메일 계정은 적극적으로 모니터링해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="30512-116">It's important to actively monitor the email account used with your PowerShell Gallery account.</span></span> <span data-ttu-id="30512-117">PowerShell 갤러리 패키지 소유자와의 모든 커뮤니케이션은 이 메일 주소를 통해 이루어집니다.</span><span class="sxs-lookup"><span data-stu-id="30512-117">All communication with owners of PowerShell Gallery packages is through this email address.</span></span> <span data-ttu-id="30512-118">PowerShell 갤러리 운영 팀에서 패키지 소유자에게 연락할 수 없는 경우 Microsoft에서 패키지를 삭제해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30512-118">If the PowerShell Gallery Operations team is unable to contact a package owner, we may be required to delete a package.</span></span>

<span data-ttu-id="30512-119">PowerShell 갤러리에 게시하는 조직에서는 이러한 목적을 위해 고유한 외부 계정을 만드는 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="30512-119">Organizations that publish to the PowerShell Gallery often create a unique external account for that purpose.</span></span> <span data-ttu-id="30512-120">이메일 전달을 사용하여 조직 내 주소로 알림을 전달하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="30512-120">We recommend you use email forwarding to forward notifications to an address within your organization.</span></span>

<span data-ttu-id="30512-121">여러 소유자가 패키지와 연결된 경우 모든 PowerShell 갤러리 알림이 모든 소유자에게 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="30512-121">When multiple owners are associated with a package, all PowerShell Gallery notifications are sent to all owners.</span></span> <span data-ttu-id="30512-122">자세한 내용은 [패키지 소유자 관리](managing-package-owners.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="30512-122">For more information, see [Managing Package Owners](managing-package-owners.md).</span></span>
