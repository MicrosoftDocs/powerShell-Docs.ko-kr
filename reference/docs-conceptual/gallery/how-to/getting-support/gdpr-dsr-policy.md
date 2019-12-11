---
ms.date: 03/27/2018
contributor: JKeithB
keywords: gallery,powershell,psgallery,GDPR
title: PowerShell 갤러리 GDPR 준수
ms.openlocfilehash: fb1191d8a1cd12d5994e41238c384eb504d0c261
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "71328324"
---
# <a name="powershell-gallery-gdpr-compliance"></a><span data-ttu-id="c644e-103">PowerShell 갤러리 GDPR 준수</span><span class="sxs-lookup"><span data-stu-id="c644e-103">PowerShell Gallery GDPR compliance</span></span>

## <a name="overview"></a><span data-ttu-id="c644e-104">개요</span><span class="sxs-lookup"><span data-stu-id="c644e-104">Overview</span></span>

<span data-ttu-id="c644e-105">2018년 5월부터 유럽 개인 정보 보호법인 GDPR(General Data Protection Regulation)이 시행되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c644e-105">In May 2018, a European privacy law, the General Data Protection Regulation (GDPR), took effect.</span></span>
<span data-ttu-id="c644e-106">GDPR은 기업, 정부 기관, 비영리 단체, 그리고 EU(유럽 연합)의 사람들에게 물품과 서비스를 제공하거나 EU 거주자와 관련된 데이터를 수집하고 분석하는 기타 조직에 새로운 규칙을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="c644e-106">The GDPR imposes new rules on companies, government agencies, non-profits, and other organizations that offer goods and services to people in the European Union (EU), or that collect and analyze data tied to EU residents.</span></span>
<span data-ttu-id="c644e-107">GDPR은 귀하가 어디에 있든 관계없이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c644e-107">The GDPR applies no matter where you are located.</span></span>

> [!NOTE]
> <span data-ttu-id="c644e-108">이 문서는 PowerShell 갤러리에서 개인 데이터를 삭제하는 방법에 대한 단계를 제공하며 GDPR 하에서 의무를 이행하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c644e-108">This article provides steps for how to delete personal data from the PowerShell Gallery and can be used to support your obligations under the GDPR.</span></span> <span data-ttu-id="c644e-109">GDPR에 대한 일반적인 정보는 [서비스 신뢰 포털의 GDPR 섹션](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c644e-109">If you’re looking for general info about GDPR, see the [GDPR section of the Service Trust portal](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted).</span></span>

## <a name="personally-identifiable-data"></a><span data-ttu-id="c644e-110">개인 식별 데이터</span><span class="sxs-lookup"><span data-stu-id="c644e-110">Personally identifiable data</span></span>

<span data-ttu-id="c644e-111">PowerShell 갤러리에는 개인 정보가 포함되어 있고 사용자가 제공할 수 있는 다음 정보가 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="c644e-111">The PowerShell Gallery stores the following information that may be provided by users, which may contain personal information:</span></span>

- <span data-ttu-id="c644e-112">PowerShell 갤러리 계정</span><span class="sxs-lookup"><span data-stu-id="c644e-112">PowerShell Gallery account</span></span>
- <span data-ttu-id="c644e-113">PowerShell 갤러리에 게시된 패키지</span><span class="sxs-lookup"><span data-stu-id="c644e-113">Packages published to the PowerShell Gallery</span></span>
- <span data-ttu-id="c644e-114">PowerShell 갤러리 팀과 이메일 서신</span><span class="sxs-lookup"><span data-stu-id="c644e-114">Email correspondence with the PowerShell Gallery team</span></span>

<span data-ttu-id="c644e-115">대부분의 사용자는 PowerShell 갤러리 계정을 만들지 않습니다</span><span class="sxs-lookup"><span data-stu-id="c644e-115">Most users do not create a PowerShell Gallery account.</span></span>
<span data-ttu-id="c644e-116">PowerShell 갤러리에서 패키지를 게시하거나 "소유자에게 문의"기능을 사용하지 않는 한 계정이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c644e-116">An account is not required unless you are going to publish a package or use the "Contact Owner" feature in the PowerShell Gallery.</span></span>
<span data-ttu-id="c644e-117">PowerShell 갤러리는 사용자가 시작한 이메일 서신을 제외하고 계정을 만들지 않은 사용자의 개인 식별 데이터를 저장하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c644e-117">Other than email correspondence initiated by the user, the PowerShell Gallery does not store personally identifiable data for users who have not created an account.</span></span>

<span data-ttu-id="c644e-118">PowerShell 갤러리 계정을 만든 사용자는 PowerShell 갤러리에 패키지를 게시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c644e-118">Users who create a PowerShell Gallery account can publish packages to the PowerShell Gallery.</span></span>
<span data-ttu-id="c644e-119">이러한 패키지는 PowerShell 코드이며, 추가로 개인 정보를 비롯한 기타 정보가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c644e-119">Those packages are expected to be PowerShell code, but may contain other information including personal information.</span></span>
<span data-ttu-id="c644e-120">아래에서는 PowerShell 갤러리에 게시한 모든 패키지를 가져오는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c644e-120">The information below will show how you can get all the packages you have published to the PowerShell Gallery.</span></span>

## <a name="dsr-export-of-powershell-gallery-data"></a><span data-ttu-id="c644e-121">PowerShell 갤러리 데이터의 DSR 내보내기</span><span class="sxs-lookup"><span data-stu-id="c644e-121">DSR Export of PowerShell Gallery Data</span></span>

<span data-ttu-id="c644e-122">다음 절에서는 PowerShell 갤러리가 데이터 주체 요청(DSR)을 지원하는 방법과 PowerShell 갤러리에 저장된 정보를 내보내는 방법, 그리고 이 정보를 삭제하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c644e-122">The following sections describe how the PowerShell Gallery supports data subject requests (DSR), by explaining how to export information stored in the PowerShell Gallery, and how to request deletion of this information.</span></span>

### <a name="email"></a><span data-ttu-id="c644e-123">메일</span><span class="sxs-lookup"><span data-stu-id="c644e-123">Email</span></span>

<span data-ttu-id="c644e-124">이메일 서신에는 다음 중 하나가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c644e-124">Email correspondence may include any of the following:</span></span>

- <span data-ttu-id="c644e-125">코드 분석 검색에서 PowerShell 갤러리에 게시한 패키지와 관련된 문제가 감지된 경우 PowerShell 갤러리 패키지 소유자에게 발송되는 메일</span><span class="sxs-lookup"><span data-stu-id="c644e-125">Email sent to the owners of PowerShell Gallery packages if the code analysis scans detected an issue with any package they have published to the PowerShell Gallery</span></span>
- <span data-ttu-id="c644e-126">"문의처" 페이지([cgadmin@microsoft.com](mailto:cgadmin@microsoft.com))에서 이메일 주소를 사용하여 누군가가 PowerShell 갤러리 팀에 보낸 이메일</span><span class="sxs-lookup"><span data-stu-id="c644e-126">Email sent by anyone to the PowerShell Gallery team using the email address in the "Contact Us" page [cgadmin@microsoft.com](mailto:cgadmin@microsoft.com)</span></span>
- <span data-ttu-id="c644e-127">PowerShell 갤러리에서 "소유자에게 문의" 기능을 사용하여 PowerShell 갤러리의 패키지 소유자에게 메일을 보내는 등록된 사용자</span><span class="sxs-lookup"><span data-stu-id="c644e-127">Registered users who use the "Contact Owner" feature in the PowerShell Gallery to send email to the owner of a package in the PowerShell Gallery</span></span>

<span data-ttu-id="c644e-128">PowerShell 갤러리에서 보내거나 PowerShell 갤러리로 보낸 이메일에는 PowerShell 갤러리에서 악성 코드 발견 시 보안 조사를 수행하기 위해 90일 보존 정책이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c644e-128">Emails sent by or to the PowerShell Gallery have a retention policy of 90 days to support possible security investigations should malicious code be discovered on the PowerShell Gallery.</span></span>
<span data-ttu-id="c644e-129">이메일은 90일 후에 정책에 의해 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="c644e-129">Emails are deleted by policy after 90 days.</span></span>

<span data-ttu-id="c644e-130">지난 90일 이내에 자신의 이메일 주소와 PowerShell 갤러리에서 보내거나 받은 모든 이메일의 사본을 요청할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c644e-130">You may request copies of all emails sent to or from your email address and the PowerShell Gallery within the previous 90 days.</span></span>
<span data-ttu-id="c644e-131">이 서신을 요청하려면 [cgadmin@microsoft.com](mailto:cgadmin@microsoft.com)으로 “이 계정과 관련된 메일에 대한 DSR 요청”이라는 제목으로 메일을 보내세요.</span><span class="sxs-lookup"><span data-stu-id="c644e-131">To request this correspondence, send an email to [cgadmin@microsoft.com](mailto:cgadmin@microsoft.com), with the title: "DSR Request for emails relating to this account".</span></span>
<span data-ttu-id="c644e-132">메시지 본문에 요청하려는 정보를 기재하세요(예: 이 메일 주소와 주고 받은 모든 메일을 보내주세요). 요청 후 90일 이내에 이메일 주소와 관련된 모든 이메일은 영업일 기준 7일 이내에 발송됩니다.</span><span class="sxs-lookup"><span data-stu-id="c644e-132">In the body of the message, state what information you are requesting (for example: Please send all emails sent to or received from this email address.) All emails involving your email address within 90 days of the request will be sent within 7 business days.</span></span>

### <a name="powershell-gallery-account-information"></a><span data-ttu-id="c644e-133">PowerShell 갤러리 계정 정보</span><span class="sxs-lookup"><span data-stu-id="c644e-133">PowerShell Gallery Account Information</span></span>

<span data-ttu-id="c644e-134">PowerShell 갤러리 계정을 만든 경우 다음 단계를 수행하여 PowerShell 갤러리에 저장된 모든 개인 정보를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c644e-134">If you have created a PowerShell Gallery account, you can find all personal information that has been stored in PowerShell Gallery by taking the following steps:</span></span>

1. <span data-ttu-id="c644e-135">PowerShell 갤러리에 로그인한 후 사용자 이름을 클릭</span><span class="sxs-lookup"><span data-stu-id="c644e-135">Sign in to the PowerShell Gallery, then click on your username</span></span>
2. <span data-ttu-id="c644e-136">표시된 다음 페이지는 PowerShell 갤러리 계정에 사용된 이메일 주소를 보여주는 계정 페이지임</span><span class="sxs-lookup"><span data-stu-id="c644e-136">The next page displayed is the Account page, which shows the email address used for the PowerShell Gallery account</span></span>

<span data-ttu-id="c644e-137">PowerShell 갤러리에서 둘 이상의 계정을 만든 경우 각 계정에 대해 이 단계를 반복해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c644e-137">If you have created more than one account in the PowerShell Gallery, you will need to repeat these steps for each account.</span></span>

### <a name="packages-in-the-powershell-gallery"></a><span data-ttu-id="c644e-138">PowerShell 갤러리에 있는 패키지</span><span class="sxs-lookup"><span data-stu-id="c644e-138">Packages in the PowerShell Gallery</span></span>

<span data-ttu-id="c644e-139">PowerShell 갤러리에 게시된 패키지를 쉽게 내보낼 수 있도록 "GetPSGalleryItemsForAuthor" 스크립트를 PowerShell 갤러리에 게시했습니다.</span><span class="sxs-lookup"><span data-stu-id="c644e-139">To facilitate exporting packages published to the PowerShell Gallery, we have published the script "GetPSGalleryItemsForAuthor" to the PowerShell Gallery.</span></span>
<span data-ttu-id="c644e-140">이 스크립트는 패키지에 저장된 작성자 정보를 기반으로 PowerShell 갤러리에 있는 모든 패키지의 모든 버전의 복사본을 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="c644e-140">This script exports a copy of every version of every package put into the PowerShell Gallery based on the author information stored in the package.</span></span>

> [!NOTE]
> <span data-ttu-id="c644e-141">작성자는 패키지를 게시할 때 패키지 매니페스트에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="c644e-141">The Author is stored in the package manifest when you publish your package.</span></span>
> <span data-ttu-id="c644e-142">작성자가 PowerShell 갤러리에서 사용하는 계정과 동일한 ID라는 보장은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c644e-142">There is no guarantee that the Author is the same identity as the account you use in the PowerShell Gallery.</span></span>
> <span data-ttu-id="c644e-143">작성자 필드에서 다른 값을 사용하는 경우 이 스크립트를 사용할 때 해당 값을 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c644e-143">If you use some other value in the Author field, you will need to supply that value when using this script.</span></span>

<span data-ttu-id="c644e-144">다음 PowerShell 명령을 사용하여 스크립트를 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c644e-144">You may download the script by using the following PowerShell command:</span></span>

```powershell
Save-Script Get-repository psgallery
```

<span data-ttu-id="c644e-145">다음 PowerShell 명령을 실행하여 스크립트를 직접 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c644e-145">You can then run the script directly, by running the following PowerShell commands:</span></span>

```powershell
# cd <local folder location>
.\GetPSGalleryItemsForAuthor.ps1
```

<span data-ttu-id="c644e-146">패키지를 저장하려는 시스템에 작성자와 폴더를 입력하라는 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="c644e-146">You will be prompted to supply the Author and a folder on your system where you want the packages to be saved.</span></span>

## <a name="deleting-personal-data-from-the-powershell-gallery"></a><span data-ttu-id="c644e-147">PowerShell 갤러리에서 개인 데이터 삭제</span><span class="sxs-lookup"><span data-stu-id="c644e-147">Deleting Personal Data From The PowerShell Gallery</span></span>

<span data-ttu-id="c644e-148">PowerShell 갤러리 계정이나 PowerShell 갤러리에서 소유하고 있는 패키지를 삭제하려면 cgadmin@microsoft.com으로 "이 계정과 관련된 항목에 대한 GDPR 요청"이라는 제목으로 메일을 보내세요.</span><span class="sxs-lookup"><span data-stu-id="c644e-148">To delete your PowerShell Gallery account or any package you own in the PowerShell Gallery, send email to cgadmin@microsoft.com with the title: "GDPR Request for items relating to this account".</span></span>
<span data-ttu-id="c644e-149">메시지 본문에는 삭제할 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c644e-149">In the body of the message state what information you want deleted.</span></span> <span data-ttu-id="c644e-150">예:</span><span class="sxs-lookup"><span data-stu-id="c644e-150">For example:</span></span>

- <span data-ttu-id="c644e-151">내 패키지의 "패키지 이름"에서 버전 x.y.z를 삭제하세요.</span><span class="sxs-lookup"><span data-stu-id="c644e-151">Please delete version x.y.z of my package "package name"</span></span>
- <span data-ttu-id="c644e-152">내 패키지의 "패키지 이름"에서 버전을 모두 삭제하세요.</span><span class="sxs-lookup"><span data-stu-id="c644e-152">Please delete all versions of my package "package name"</span></span>
- <span data-ttu-id="c644e-153">PowerShell 갤러리 계정을 삭제하세요.</span><span class="sxs-lookup"><span data-stu-id="c644e-153">Please delete my PowerShell Gallery account</span></span>

<span data-ttu-id="c644e-154">PowerShell 갤러리 관리자는 영업일 기준 7일 이내에 회신합니다.</span><span class="sxs-lookup"><span data-stu-id="c644e-154">The PowerShell Gallery administrators will reply within 7 business days.</span></span>
<span data-ttu-id="c644e-155">지정된 패키지는 요청이 전송된 후 30일 이내에 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="c644e-155">The packages specified will be deleted within 30 days after the request is sent.</span></span>
