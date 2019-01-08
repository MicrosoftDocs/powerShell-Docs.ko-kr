---
ms.date: 08/23/2017
keywords: powershell,cmdlet
title: Windows PowerShell 웹 액세스의 액세스 문제 해결
ms.openlocfilehash: c9b98c7a1685679eb88b718de0351154cb84e92e
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402532"
---
# <a name="troubleshooting-access-problems-in-windows-powershell-web-access"></a><span data-ttu-id="da438-103">Windows PowerShell 웹 액세스의 액세스 문제 해결</span><span class="sxs-lookup"><span data-stu-id="da438-103">Troubleshooting Access Problems in Windows PowerShell Web Access</span></span>

<span data-ttu-id="da438-104">업데이트됨: 2013 년 6 월 24, (2017 년 8 월 23 일 수정)</span><span class="sxs-lookup"><span data-stu-id="da438-104">Updated: June 24, 2013 (revised August 23, 2017)</span></span>

<span data-ttu-id="da438-105">적용 대상: Windows Server 2012 R2, Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="da438-105">Applies To: Windows Server 2012 R2, Windows Server 2012</span></span>

<span data-ttu-id="da438-106">다음 섹션에는 Windows PowerShell 웹 액세스를 사용하여 원격 컴퓨터에 연결할 때 발생할 수 있는 몇 가지 일반적인 문제와 이러한 문제에 대한 해결 방안이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="da438-106">The following sections identify some common problems when attempting to connect to a remote computer by using Windows PowerShell Web Access, and includes suggestions for resolving the problems.</span></span>

## <a name="sign-in-failure"></a><span data-ttu-id="da438-107">로그인 오류</span><span class="sxs-lookup"><span data-stu-id="da438-107">Sign-in failure</span></span>

<span data-ttu-id="da438-108">다음과 같은 이유로 인해 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="da438-108">Failure could occur because of any of the following.</span></span>

- <span data-ttu-id="da438-109">원격 컴퓨터에 특정 세션 구성이나 컴퓨터에 대한 사용자 액세스를 허용하는 권한 부여 규칙이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="da438-109">An authorization rule that allows the user access to the computer, or a specific session configuration on the remote computer, does not exist.</span></span>

  <span data-ttu-id="da438-110">Windows PowerShell 웹 액세스 보안이 제한적이므로 권한 부여 규칙을 사용하여 명시적으로 사용자에게 원격 컴퓨터에 대한 액세스를 허용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="da438-110">Windows PowerShell Web Access security is restrictive; users must be granted explicit access to remote computers by using authorization rules.</span></span>

  <span data-ttu-id="da438-111">권한 부여 규칙을 만드는 방법에 대한 자세한 내용은 [Windows PowerShell 웹 액세스의 권한 부여 규칙 및 보안 기능](authorization-rules-and-security-features-of-windows-powershell-web-access.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="da438-111">For more information about creating authorization rules, see [Authorization Rules and Security Features of Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md).</span></span>

- <span data-ttu-id="da438-112">사용자에게는 대상 컴퓨터에 대해 허가받은 권한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="da438-112">The user does not have authorized access to the destination computer.</span></span> <span data-ttu-id="da438-113">이 권한은 ACL(액세스 제어 목록)에서 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="da438-113">This is determined by access control lists (ACLs).</span></span>

  <span data-ttu-id="da438-114">자세한 내용은 [Windows PowerShell 웹 액세스 로그인](use-the-web-based-windows-powershell-console.md#signing-in-to-windows-powershell-web-access) 또는 Windows PowerShell 팀 블로그를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="da438-114">For more information, see [Signing in to Windows PowerShell Web Access](use-the-web-based-windows-powershell-console.md#signing-in-to-windows-powershell-web-access), or the Windows PowerShell Team Blog.</span></span>

- <span data-ttu-id="da438-115">Windows PowerShell 원격 관리 기능이 대상 컴퓨터에서 사용되지 않는 상태일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="da438-115">Windows PowerShell remote management might not be enabled on the destination computer.</span></span>

  <span data-ttu-id="da438-116">사용자가 연결하려는 컴퓨터에서 원격 관리가 사용되는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="da438-116">Verify remote management is enabled on the computer to which the user is trying to connect.</span></span>

  <span data-ttu-id="da438-117">자세한 내용은 [How to Configure Your Computer for Remoting](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_requirements#how-to-configure-your-computer-for-remoting)(컴퓨터를 원격으로 사용할 수 있도록 구성하는 방법)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="da438-117">For more information, see [How to Configure Your Computer for Remoting](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_requirements#how-to-configure-your-computer-for-remoting).</span></span>

## <a name="internal-server-error"></a><span data-ttu-id="da438-118">내부 서버 오류</span><span class="sxs-lookup"><span data-stu-id="da438-118">Internal Server Error</span></span>

<span data-ttu-id="da438-119">사용자가 Internet Explorer 창에서 Windows PowerShell 웹 액세스에 로그인하려고 하면 **내부 서버 오류** 페이지가 표시되거나 *Internet Explorer*의 응답이 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="da438-119">When users try to sign in to Windows PowerShell Web Access in an Internet Explorer window, they are shown an **Internal Server Error** page, or *Internet Explorer* stops responding.</span></span>

<span data-ttu-id="da438-120">이 문제는 Internet Explorer에서만 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="da438-120">This issue is specific to Internet Explorer.</span></span>

### <a name="possible-cause"></a><span data-ttu-id="da438-121">가능한 원인</span><span class="sxs-lookup"><span data-stu-id="da438-121">Possible cause</span></span>

<span data-ttu-id="da438-122">이 문제는 사용자가 한자를 포함한 도메인 이름으로 로그인한 경우 또는 게이트웨이 서버 이름의 일부로 한자가 두 개 이상 포함된 경우에 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="da438-122">This can occur for users who have signed in with a domain name that contains Chinese characters, or if one or more Chinese characters are part of the gateway server name.</span></span>

#### <a name="workaround"></a><span data-ttu-id="da438-123">해결 방법</span><span class="sxs-lookup"><span data-stu-id="da438-123">Workaround</span></span>

1. [<span data-ttu-id="da438-124">Internet Explorer 10을 설치하고 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="da438-124">Install and run Internet Explorer 10</span></span>](https://ie.microsoft.com/testdrive/info/downloads/Default.html)
1. <span data-ttu-id="da438-125">Internet Explorer **문서 모드** 설정을 *IE10 표준*으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="da438-125">Change Internet Explorer **Document Mode** setting to *IE10* standards.</span></span>
   1. <span data-ttu-id="da438-126">**F12** 키를 눌러 개발자 도구 콘솔을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="da438-126">Press **F12** to open the Developer Tools console</span></span>
   1. <span data-ttu-id="da438-127">Internet Explorer 10에서 **브라우저 모드**를 클릭한 후 *Internet Explorer 10*을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="da438-127">In Internet Explorer 10, click **Browser Mode**, and then select *Internet Explorer 10*.</span></span>
   1. <span data-ttu-id="da438-128">**문서 모드**를 클릭한 후 *IE10 표준*을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="da438-128">Click **Document Mode**, and then click *IE10* standards.</span></span>
   1. <span data-ttu-id="da438-129">**F12** 키를 다시 눌러 개발자 도구 콘솔을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="da438-129">Press **F12** again to close the Developer Tools console.</span></span>
1. <span data-ttu-id="da438-130">Internet Explorer 10에서 자동 프록시 구성을 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="da438-130">Disable automatic proxy configuration in Internet Explorer 10.</span></span>
   1. <span data-ttu-id="da438-131">**도구**를 클릭한 다음 **인터넷 옵션**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="da438-131">Click **Tools**, and then click **Internet Options**.</span></span>
   1. <span data-ttu-id="da438-132">**인터넷 옵션** 대화 상자의 **연결** 탭에서 **LAN 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="da438-132">In the **Internet Options** dialog box, on the **Connections** tab, click **LAN settings**.</span></span>
   1. <span data-ttu-id="da438-133">**자동으로 설정 검색** 확인란을 선택 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="da438-133">Clear the **Automatically detect settings** check box.</span></span> <span data-ttu-id="da438-134">**확인**을 클릭한 후 다시 **확인**을 클릭하여 *인터넷 옵션* 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="da438-134">Click **OK**, and then click **OK** again to close the *Internet Options* dialog box.</span></span>

## <a name="cannot-connect-to-a-remote-workgroup-computer"></a><span data-ttu-id="da438-135">원격 작업 그룹 컴퓨터에 연결할 수 없는 경우</span><span class="sxs-lookup"><span data-stu-id="da438-135">Cannot connect to a remote workgroup computer</span></span>

<span data-ttu-id="da438-136">대상 컴퓨터가 작업 그룹의 구성원인 경우에는 `<workgroup_name>\<user_name>` 등의 구문을 이용하여 사용자 이름을 입력하고 컴퓨터에 로그인합니다.</span><span class="sxs-lookup"><span data-stu-id="da438-136">If the destination computer is a member of a workgroup, use the following syntax to provide your user name and sign in to the computer: `<workgroup_name>\<user_name>`</span></span>

## <a name="cannot-find-web-server-iis-management-tools-even-though-the-role-was-installed"></a><span data-ttu-id="da438-137">웹 서버(IIS) 역할이 설치되어 있는데도 웹 서버(IIS) 관리 도구를 찾을 수 없는 경우</span><span class="sxs-lookup"><span data-stu-id="da438-137">Cannot find Web Server (IIS) management tools, even though the role was installed</span></span>

<span data-ttu-id="da438-138">`Install-WindowsFeature` cmdlet을 사용하여 Windows PowerShell 웹 액세스를 설치한 경우 `-IncludeManagementTools` 매개 변수를 cmdlet에 추가하지 않으면 관리 도구가 설치되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="da438-138">If you installed Windows PowerShell Web Access by using the `Install-WindowsFeature` cmdlet, management tools are not installed unless the `-IncludeManagementTools` parameter is added to the cmdlet.</span></span>

<span data-ttu-id="da438-139">이에 해당하는 예는 [Windows PowerShell cmdlet을 사용하여 Windows PowerShell 웹 액세스를 설치하려면](install-and-use-windows-powershell-web-access.md#to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="da438-139">For an example, see [To install Windows PowerShell Web Access by using Windows PowerShell cmdlets](install-and-use-windows-powershell-web-access.md#to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets).</span></span>

<span data-ttu-id="da438-140">IIS 관리자 콘솔 및 기타 IIS 관리 도구가 필요한 경우 게이트웨이 서버를 대상으로 하는 **역할 및 기능 추가 마법사** 세션에서 해당 도구를 선택하여 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="da438-140">You can add the IIS Manager console, and other IIS management tools that you need, by selecting the tools in an **Add Roles and Features Wizard** session that is targeted at the gateway server.</span></span>
<span data-ttu-id="da438-141">역할 및 기능 추가 마법사는 서버 관리자 내에서 열립니다.</span><span class="sxs-lookup"><span data-stu-id="da438-141">The Add Roles and Features Wizard is opened from within Server Manager.</span></span>

## <a name="windows-powershell-web-access-website-is-not-accessible"></a><span data-ttu-id="da438-142">Windows PowerShell 웹 액세스 웹 사이트에 액세스할 수 없는 경우</span><span class="sxs-lookup"><span data-stu-id="da438-142">Windows PowerShell Web Access website is not accessible</span></span>

<span data-ttu-id="da438-143">Internet Explorer에서 보안 강화 구성(IE ESC)이 사용되는 경우 신뢰할 수 있는 사이트 목록에 Windows PowerShell 웹 액세스 웹 사이트를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="da438-143">If Enhanced Security Configuration is enabled in Internet Explorer (IE ESC), you can add the Windows PowerShell Web Access website to the list of trusted sites.</span></span>

<span data-ttu-id="da438-144">IE ESC를 사용하지 않도록 설정할 수도 있지만 보안 위험 때문에 사용하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="da438-144">A less recommended approach, due to security risks, is to disable IE ESC.</span></span>
<span data-ttu-id="da438-145">IE ESC는 서버 관리자의 [로컬 서버] 페이지에 있는 [속성] 타일에서 사용하지 않도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="da438-145">You can disable IE ESC in the Properties tile on the Local Server page in Server Manager.</span></span>

## <a name="an-authorization-failure-occurred-verify-that-you-are-authorized-to-connect-to-the-destination-computer"></a><span data-ttu-id="da438-146">권한 부여 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="da438-146">An authorization failure occurred.</span></span> <span data-ttu-id="da438-147">대상 컴퓨터에 연결할 권한이 있는지 검증하세요.</span><span class="sxs-lookup"><span data-stu-id="da438-147">Verify that you are authorized to connect to the destination computer.</span></span>

<span data-ttu-id="da438-148">위 오류 메시지는 게이트웨이 서버가 대상 컴퓨터이고 작업 그룹에 있을 때 연결하려고 하면 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="da438-148">The above error message is displayed while trying to connect when the gateway server is the destination computer, and is also in a workgroup.</span></span>

<span data-ttu-id="da438-149">또한 게이트웨이 서버가 대상 서버이며 작업 그룹에 속해 있는 경우 사용자 이름, 컴퓨터 이름 및 사용자 그룹 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="da438-149">When the gateway server is also the destination server, and it is in a workgroup, specify the user name, computer name, and user group name.</span></span>
<span data-ttu-id="da438-150">컴퓨터 이름을 나타내는 데에는 점(.)을 단독으로 사용하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="da438-150">Do not use a dot (.) by itself to represent the computer name.</span></span>

### <a name="scenarios-and-proper-values"></a><span data-ttu-id="da438-151">시나리오 및 적절한 값</span><span class="sxs-lookup"><span data-stu-id="da438-151">Scenarios and proper values</span></span>

#### <a name="all-cases"></a><span data-ttu-id="da438-152">모든 사례</span><span class="sxs-lookup"><span data-stu-id="da438-152">All cases</span></span>

<span data-ttu-id="da438-153">매개 변수</span><span class="sxs-lookup"><span data-stu-id="da438-153">Parameter</span></span> | <span data-ttu-id="da438-154">Value</span><span class="sxs-lookup"><span data-stu-id="da438-154">Value</span></span>
-- | --
<span data-ttu-id="da438-155">UserName</span><span class="sxs-lookup"><span data-stu-id="da438-155">UserName</span></span> | <span data-ttu-id="da438-156">Server\_name\\user\_name</span><span class="sxs-lookup"><span data-stu-id="da438-156">Server\_name\\user\_name</span></span><br/><span data-ttu-id="da438-157">Localhost\\user\_name</span><span class="sxs-lookup"><span data-stu-id="da438-157">Localhost\\user\_name</span></span><br/><span data-ttu-id="da438-158">.\\user\_name</span><span class="sxs-lookup"><span data-stu-id="da438-158">.\\user\_name</span></span>
<span data-ttu-id="da438-159">UserGroup</span><span class="sxs-lookup"><span data-stu-id="da438-159">UserGroup</span></span> | <span data-ttu-id="da438-160">Server\_name\\user\_group</span><span class="sxs-lookup"><span data-stu-id="da438-160">Server\_name\\user\_group</span></span><br/><span data-ttu-id="da438-161">Localhost\\user\_group</span><span class="sxs-lookup"><span data-stu-id="da438-161">Localhost\\user\_group</span></span><br/><span data-ttu-id="da438-162">.\\user\_group</span><span class="sxs-lookup"><span data-stu-id="da438-162">.\\user\_group</span></span>
<span data-ttu-id="da438-163">ComputerGroup</span><span class="sxs-lookup"><span data-stu-id="da438-163">ComputerGroup</span></span> | <span data-ttu-id="da438-164">Server\_name\\computer\_group</span><span class="sxs-lookup"><span data-stu-id="da438-164">Server\_name\\computer\_group</span></span><br/><span data-ttu-id="da438-165">Localhost\\computer\_group</span><span class="sxs-lookup"><span data-stu-id="da438-165">Localhost\\computer\_group</span></span><br/><span data-ttu-id="da438-166">.\\computer\_group</span><span class="sxs-lookup"><span data-stu-id="da438-166">.\\computer\_group</span></span>

#### <a name="gateway-server-is-in-a-domain"></a><span data-ttu-id="da438-167">도메인의 게이트웨이 서버</span><span class="sxs-lookup"><span data-stu-id="da438-167">Gateway server is in a domain</span></span>

<span data-ttu-id="da438-168">매개 변수</span><span class="sxs-lookup"><span data-stu-id="da438-168">Parameter</span></span> | <span data-ttu-id="da438-169">Value</span><span class="sxs-lookup"><span data-stu-id="da438-169">Value</span></span>
-- | --
<span data-ttu-id="da438-170">ComputerName</span><span class="sxs-lookup"><span data-stu-id="da438-170">ComputerName</span></span> | <span data-ttu-id="da438-171">정규화된 게이트웨이 서버의 이름 또는 Localhost</span><span class="sxs-lookup"><span data-stu-id="da438-171">Fully qualified name of gateway server, or Localhost</span></span>

#### <a name="gateway-server-is-in-a-workgroup"></a><span data-ttu-id="da438-172">작업 그룹의 게이트웨이 서버</span><span class="sxs-lookup"><span data-stu-id="da438-172">Gateway server is in a workgroup</span></span>

<span data-ttu-id="da438-173">매개 변수</span><span class="sxs-lookup"><span data-stu-id="da438-173">Parameter</span></span> | <span data-ttu-id="da438-174">Value</span><span class="sxs-lookup"><span data-stu-id="da438-174">Value</span></span>
-- | --
<span data-ttu-id="da438-175">ComputerName</span><span class="sxs-lookup"><span data-stu-id="da438-175">ComputerName</span></span> | <span data-ttu-id="da438-176">서버 이름</span><span class="sxs-lookup"><span data-stu-id="da438-176">Server name</span></span>

### <a name="gateway-credentials"></a><span data-ttu-id="da438-177">게이트웨이 자격 증명</span><span class="sxs-lookup"><span data-stu-id="da438-177">Gateway credentials</span></span>

<span data-ttu-id="da438-178">다음 중 하나로 형식화된 자격 증명을 사용하여 게이트웨이 서버에 대상 컴퓨터로 로그인합니다.</span><span class="sxs-lookup"><span data-stu-id="da438-178">Sign in to a gateway server as target computer by using credentials formatted as one of the following.</span></span>

- <span data-ttu-id="da438-179">Server\_name\\user\_name</span><span class="sxs-lookup"><span data-stu-id="da438-179">Server\_name\\user\_name</span></span>
- <span data-ttu-id="da438-180">Localhost\\user\_name</span><span class="sxs-lookup"><span data-stu-id="da438-180">Localhost\\user\_name</span></span>
- <span data-ttu-id="da438-181">.\\user\_name</span><span class="sxs-lookup"><span data-stu-id="da438-181">.\\user\_name</span></span>

## <a name="a-security-identifier-sid-is-displayed-in-an-authorization-rule"></a><span data-ttu-id="da438-182">권한 부여 규칙에 SID(보안 식별자)가 표시되지 않는 경우</span><span class="sxs-lookup"><span data-stu-id="da438-182">A security identifier (SID) is displayed in an authorization rule</span></span>

<span data-ttu-id="da438-183">SID(보안 식별자)는 구문 user\_name/computer\_name 대신 권한 부여 규칙에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="da438-183">A security identifier (SID) is displayed in an authorization rule instead of the syntax user\_name/computer\_name.</span></span>

<span data-ttu-id="da438-184">규칙이 더 이상 유효하지 않거나, Active Directory 도메인 서비스를 쿼리하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="da438-184">Either the rule is no longer valid, or the Active Directory Domain Services query failed.</span></span>
<span data-ttu-id="da438-185">권한 부여 규칙은 게이트웨이 서버가 이전에는 작업 그룹에 있었지만 나중에 도메인에 가입한 시나리오에서는 항상 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="da438-185">An authorization rule is usually not valid in scenarios where the gateway server was at one time in a workgroup, but was later joined to a domain</span></span>

## <a name="cannot-sign-in-with-rule-as-an-ipv6-address-with-a-domain"></a><span data-ttu-id="da438-186">규칙을 사용하여 도메인의 IPv6 주소로 로그인할 수 없는 경우</span><span class="sxs-lookup"><span data-stu-id="da438-186">Cannot sign in with rule as an IPv6 address with a domain</span></span>

<span data-ttu-id="da438-187">권한 부여 규칙에 지정된 대상 컴퓨터에는 도메인의 IPv6 주소로 로그인할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="da438-187">Cannot sign in to a target computer that has been specified in authorization rules as an IPv6 address with a domain.</span></span>

<span data-ttu-id="da438-188">권한 부여 규칙은 도메인 이름 형식의 IPv6 주소를 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="da438-188">Authorization rules do not support an IPv6 address in form of a domain name.</span></span>

<span data-ttu-id="da438-189">IPv6 주소를 사용하여 대상 컴퓨터를 지정하려면 권한 부여 규칙의 원래 IPv6 주소(콜론 포함)를 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="da438-189">To specify a destination computer by using an IPv6 address, use the original IPv6 address (that contains colons) in the authorization rule.</span></span>
<span data-ttu-id="da438-190">도메인과 숫자(콜론 포함)가 모두 포함된 IPv6 주소는 Windows PowerShell 웹 액세스 로그인 페이지에서 대상 컴퓨터 이름으로 사용할 수는 있지만 권한 부여 규칙에서는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="da438-190">Both domain and numerical (with colons) IPv6 addresses are supported as the target computer name on the Windows PowerShell Web Access sign-in page, but not in authorization rules.</span></span>

<span data-ttu-id="da438-191">IPv6 주소에 대한 자세한 내용은 [IPv6 작동 방법](https://technet.microsoft.com/library/cc781672(v=ws.10).aspx)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="da438-191">For more information about IPv6 addresses, see [How IPv6 Works](https://technet.microsoft.com/library/cc781672(v=ws.10).aspx).</span></span>

## <a name="see-also"></a><span data-ttu-id="da438-192">참고 항목</span><span class="sxs-lookup"><span data-stu-id="da438-192">See Also</span></span>

- <span data-ttu-id="da438-193">[Windows PowerShell 웹 액세스의 권한 부여 규칙 및 보안 기능](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx)</span><span class="sxs-lookup"><span data-stu-id="da438-193">[Authorization Rules and Security Features of Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx)</span></span>
- <span data-ttu-id="da438-194">[웹 기반 Windows PowerShell 콘솔 사용](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)</span><span class="sxs-lookup"><span data-stu-id="da438-194">[Use the Web-based Windows PowerShell Console](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)</span></span>
- [<span data-ttu-id="da438-195">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="da438-195">about_Remote_Requirements</span></span>](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_remote_requirements)