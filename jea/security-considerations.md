---
ms.date: 06/12/2017
keywords: jea,powershell,security
title: JEA 보안 고려 사항
ms.openlocfilehash: ede727f0f30412d520712d6ba855ba2008375d9a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55681853"
---
# <a name="jea-security-considerations"></a><span data-ttu-id="8e356-103">JEA 보안 고려 사항</span><span class="sxs-lookup"><span data-stu-id="8e356-103">JEA Security Considerations</span></span>

> <span data-ttu-id="8e356-104">적용 대상: Windows Powershell 5.0</span><span class="sxs-lookup"><span data-stu-id="8e356-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="8e356-105">JEA를 사용하면 컴퓨터의 영구 관리자 수를 줄여 보안 상태를 개선할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e356-105">JEA helps you improve your security posture by reducing the number of permanent administrators on your machines.</span></span>
<span data-ttu-id="8e356-106">오용을 방지하기 위해 기본적으로 단단히 잠긴 시스템을 사용자가 관리하기 위한 진입점(PowerShell 세션 구성)을 만들어 이렇게 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e356-106">It does so by creating a new entry point for users to manage the system (a PowerShell session configuration) which is tightly locked down by default to prevent misuse.</span></span>
<span data-ttu-id="8e356-107">관리 작업을 수행하기 위해 컴퓨터에 대한 일부(그러나 제한되지는 않은) 액세스 권한이 필요한 사용자에게 JEA 엔드포인트에 대한 액세스 권한을 부여할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e356-107">Users who need some, but not unlimited, access to the machine to perform administrative tasks can be granted access to the JEA endpoint.</span></span>
<span data-ttu-id="8e356-108">JEA를 통해 사용자는 직접 관리자 액세스 권한을 갖지 않고도 관리 명령을 실행할 수 있으므로 높은 권한이 있는 보안 그룹에서 해당 사용자를 제거할 수 있습니다(해당 사용자를 표준 사용자로 만듦).</span><span class="sxs-lookup"><span data-stu-id="8e356-108">Because JEA allows them to run admin commands without directly having admin access, you can then remove those users from highly privileged security groups (make them standard users).</span></span>

<span data-ttu-id="8e356-109">이 항목에서는 JEA 보안 모델 및 모범 사례를 더 자세히 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="8e356-109">This topic describes the JEA security model and best practices in more detail.</span></span>

## <a name="run-as-account"></a><span data-ttu-id="8e356-110">실행 계정</span><span class="sxs-lookup"><span data-stu-id="8e356-110">Run As account</span></span>

<span data-ttu-id="8e356-111">각 JEA 엔드포인트에는 지정된 "실행 계정"이 있으며, 이 계정은 연결하는 사용자의 작업이 수행되는 계정입니다.</span><span class="sxs-lookup"><span data-stu-id="8e356-111">Each JEA endpoint has a designated "run as" account, which is the account under which the connecting user's actions are performed.</span></span>
<span data-ttu-id="8e356-112">이 계정은 [세션 구성 파일](session-configurations.md)에서 구성할 수 있으며, 선택한 계정은 엔드포인트의 보안에 상당한 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8e356-112">This account is configurable in the [session configuration file](session-configurations.md), and the account you choose has a significant bearing on the security of your endpoint.</span></span>

<span data-ttu-id="8e356-113">**가상 계정**은 실행 계정을 구성하는 권장 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="8e356-113">**Virtual accounts** are the recommended way of configuring the run as account.</span></span>
<span data-ttu-id="8e356-114">가상 계정은 연결하는 사용자가 JEA 세션 기간 동안 사용하도록 만들어지는 일회성 임시 로컬 계정입니다.</span><span class="sxs-lookup"><span data-stu-id="8e356-114">Virtual accounts are one-time, temporary local accounts that are created for the connecting user to use during the duration of their JEA session.</span></span>
<span data-ttu-id="8e356-115">해당 세션이 종료되는 즉시 가상 계정은 제거되고 더 이상 사용될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8e356-115">As soon as their session is terminated, the virtual account will be destroyed and cannot be used anymore.</span></span>
<span data-ttu-id="8e356-116">연결하는 사용자는 가상 계정의 자격 증명을 알지 못하므로 원격 데스크톱 또는 비제한 PowerShell 엔드포인트와 같은 다른 방법을 통해 가상 계정을 사용하여 시스템에 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8e356-116">The connecting user does not know the credentials for the virtual account and cannot use the virtual account to access the system via other means, such as Remote Desktop or an unconstrained PowerShell endpoint.</span></span>

<span data-ttu-id="8e356-117">기본적으로 가상 계정은 컴퓨터의 로컬 관리자 그룹에 속합니다.</span><span class="sxs-lookup"><span data-stu-id="8e356-117">By default, virtual accounts belong to the local administrators group on the machine.</span></span>
<span data-ttu-id="8e356-118">따라서 시스템의 모든 항목을 관리할 수 있는 모든 권한은 있지만, 네트워크의 리소스를 관리할 수 있는 권한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8e356-118">This gives them full rights to manage anything on the system, but no rights to manage resources on the network.</span></span>
<span data-ttu-id="8e356-119">다른 컴퓨터에서 인증할 때 사용자 컨텍스트는 가상 계정이 아니라 로컬 컴퓨터 계정이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8e356-119">When authenticating with other machines, the user context will be that of the local computer account, not the virtual account.</span></span>

<span data-ttu-id="8e356-120">도메인 컨트롤러는 로컬 관리자 그룹이라는 개념이 없으므로 특수한 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="8e356-120">Domain controllers are a special case since there is no concept of a local administrators group.</span></span>
<span data-ttu-id="8e356-121">대신, Domain Admins에 속한 가상 계정으로 도메인 컨트롤러에서 디렉터리 서비스를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e356-121">Instead, virtual accounts belong to Domain Admins instead and can manage the directory services on the domain controller.</span></span>
<span data-ttu-id="8e356-122">도메인 ID는 여전히 JEA 세션이 인스턴스화된 도메인 컨트롤러에서 사용하도록 제한되며, 모든 네트워크 액세스는 대신 도메인 컨트롤러 컴퓨터 개체에서 오는 것처럼 보입니다.</span><span class="sxs-lookup"><span data-stu-id="8e356-122">The domain identity is still restricted to use on the domain controller where the JEA session was instantiated, and any network access will appear to come from the domain controller computer object instead.</span></span>

<span data-ttu-id="8e356-123">두 경우 모두 가상 계정이 속해야 하는 보안 그룹을 명시적으로 정의할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e356-123">In both cases, you can also explicitly define which security groups the virtual account should belong to.</span></span>
<span data-ttu-id="8e356-124">수행하는 작업이 로컬/도메인 관리자 권한 없이 수행될 수 있는 작업인 경우 이렇게 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8e356-124">This is a good practice when the task you are performing can be done without local/domain admin privileges.</span></span>
<span data-ttu-id="8e356-125">이미 관리자에 대해 정의된 보안 그룹이 있는 경우 필요한 권한을 부여하려면 해당 그룹에 가상 계정 구성원 자격을 부여하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8e356-125">If you already have a security group defined for your admins, you can simply grant the virtual account membership to that group to give it the permissions it needs.</span></span>
<span data-ttu-id="8e356-126">가상 계정 그룹 구성원 자격은 워크스테이션 및 구성원 서버에서 로컬 보안 그룹으로 제한되지만, 도메인 컨트롤러에서는 도메인 보안 그룹의 구성원일 수만 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e356-126">Virtual account group membership is limited to local security groups on workstation and member servers, but on a domain controller they can only be members of domain security groups.</span></span>
<span data-ttu-id="8e356-127">가상 계정이 속하는 보안 그룹을 하나 이상 지정하고 나면 가상 계정이 더 이상 기본 그룹(로컬 관리자 또는 도메인 관리자)에 속하지 않게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8e356-127">Once you specify one or more security groups for the virtual account to belong to, it will no longer belong to the default groups (local admin or domain admin).</span></span>

<span data-ttu-id="8e356-128">아래 표에는 가상 계정에 대한 가능한 구성 옵션 및 해당 사용 권한이 요약되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e356-128">The table below summarizes the possible configuration options and resulting permissions for virtual accounts</span></span>

<span data-ttu-id="8e356-129">컴퓨터 유형</span><span class="sxs-lookup"><span data-stu-id="8e356-129">Computer type</span></span>                | <span data-ttu-id="8e356-130">가상 계정 그룹 구성</span><span class="sxs-lookup"><span data-stu-id="8e356-130">Virtual account group configuration</span></span> | <span data-ttu-id="8e356-131">로컬 사용자 컨텍스트</span><span class="sxs-lookup"><span data-stu-id="8e356-131">Local user context</span></span>                                      | <span data-ttu-id="8e356-132">네트워크 사용자 컨텍스트</span><span class="sxs-lookup"><span data-stu-id="8e356-132">Network user context</span></span>
-----------------------------|-------------------------------------|---------------------------------------------------------|--------------------------------------------------
<span data-ttu-id="8e356-133">도메인 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="8e356-133">Domain controller</span></span>            | <span data-ttu-id="8e356-134">Default</span><span class="sxs-lookup"><span data-stu-id="8e356-134">Default</span></span>                             | <span data-ttu-id="8e356-135">도메인 사용자, '*DOMAIN*\Domain Admins'의 구성원</span><span class="sxs-lookup"><span data-stu-id="8e356-135">Domain user, member of '*DOMAIN*\Domain Admins'</span></span>         | <span data-ttu-id="8e356-136">컴퓨터 계정</span><span class="sxs-lookup"><span data-stu-id="8e356-136">Computer account</span></span>
<span data-ttu-id="8e356-137">도메인 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="8e356-137">Domain controller</span></span>            | <span data-ttu-id="8e356-138">도메인 그룹 A 및 B</span><span class="sxs-lookup"><span data-stu-id="8e356-138">Domain groups A and B</span></span>               | <span data-ttu-id="8e356-139">도메인 사용자, '*DOMAIN*\A', '*DOMAIN*\B'의 구성원</span><span class="sxs-lookup"><span data-stu-id="8e356-139">Domain user, member of '*DOMAIN*\A', '*DOMAIN*\B'</span></span>       | <span data-ttu-id="8e356-140">컴퓨터 계정</span><span class="sxs-lookup"><span data-stu-id="8e356-140">Computer account</span></span>
<span data-ttu-id="8e356-141">구성원 서버 또는 워크스테이션</span><span class="sxs-lookup"><span data-stu-id="8e356-141">Member server or workstation</span></span> | <span data-ttu-id="8e356-142">Default</span><span class="sxs-lookup"><span data-stu-id="8e356-142">Default</span></span>                             | <span data-ttu-id="8e356-143">로컬 사용자, '*BUILTIN*\Administrators'의 구성원</span><span class="sxs-lookup"><span data-stu-id="8e356-143">Local user, member of '*BUILTIN*\Administrators'</span></span>        | <span data-ttu-id="8e356-144">컴퓨터 계정</span><span class="sxs-lookup"><span data-stu-id="8e356-144">Computer account</span></span>
<span data-ttu-id="8e356-145">구성원 서버 또는 워크스테이션</span><span class="sxs-lookup"><span data-stu-id="8e356-145">Member server or workstation</span></span> | <span data-ttu-id="8e356-146">로컬 그룹 C 및 D</span><span class="sxs-lookup"><span data-stu-id="8e356-146">Local groups C and D</span></span>                | <span data-ttu-id="8e356-147">로컬 사용자, '*COMPUTER*\C' 및 '*COMPUTER*\D'의 구성원</span><span class="sxs-lookup"><span data-stu-id="8e356-147">Local user, member of '*COMPUTER*\C' and '*COMPUTER*\D'</span></span> | <span data-ttu-id="8e356-148">컴퓨터 계정</span><span class="sxs-lookup"><span data-stu-id="8e356-148">Computer account</span></span>

<span data-ttu-id="8e356-149">보안 감사 이벤트 및 애플리케이션 이벤트 로그를 보면 각 JEA 사용자 세션에 고유 가상 계정이 있는 것을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e356-149">When you look at security audit events and application event logs, you will see that each JEA user session has a unique virtual account.</span></span>
<span data-ttu-id="8e356-150">이는 JEA 엔드포인트에서 사용자 작업을 추적할 때 명령을 실행한 원래 사용자까지 거슬러 올라가 추적하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8e356-150">This helps you track user actions in a JEA endpoint back to the original user who ran the command.</span></span>
<span data-ttu-id="8e356-151">가상 계정 이름은 "WinRM Virtual Users\\WinRM\_VA\_*ACCOUNTNUMBER*\_*DOMAIN*\_*sAMAccountName*" 형식을 따릅니다. 예를 들어 도메인 "Contoso"의 사용자 "Alice"가 JEA 엔드포인트에서 서비스를 다시 시작하면 모든 서비스 제어 관리자 이벤트와 연결된 사용자 이름은 "WinRM Virtual Users\\WinRM\_VA\_1\_contoso\_alice"가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8e356-151">Virtual account names follow the format "WinRM Virtual Users\\WinRM\_VA\_*ACCOUNTNUMBER*\_*DOMAIN*\_*sAMAccountName*" For example, if user "Alice" in domain "Contoso" restarts a service in a JEA endpoint, the username associated with any service control manager events would be "WinRM Virtual Users\\WinRM\_VA\_1\_contoso\_alice".</span></span>


<span data-ttu-id="8e356-152">**gMSA(그룹 관리 서비스 계정)** 는 구성원 서버가 JEA 세션에서 네트워크 리소스에 대한 액세스 권한을 가져야 할 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="8e356-152">**Group managed service accounts (gMSAs)** are useful when a member server needs to have access to network resources in the JEA session.</span></span>
<span data-ttu-id="8e356-153">이 경우에 대한 예제 사용 사례는 다른 컴퓨터에서 호스트되는 REST API에 대한 액세스를 제어하는 데 사용되는 JEA 엔드포인트입니다.</span><span class="sxs-lookup"><span data-stu-id="8e356-153">An example use case for this is a JEA endpoint that is used to control access to a REST API hosted on a different machine.</span></span>
<span data-ttu-id="8e356-154">REST API에 대한 원하는 호출을 만드는 함수를 작성하기는 쉽지만, API로 인증하려면 네트워크 ID가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="8e356-154">It is easy to write functions to make the desired invocations on the REST API, but in order to authenticate with the API you need a network identity.</span></span>
<span data-ttu-id="8e356-155">그룹 관리 서비스 계정을 사용하면 계정을 사용할 수 있는 컴퓨터를 여전히 제어하면서도 "두 번째 홉"을 가능하게 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e356-155">Using a group managed service account makes the "second hop" possible while still having control over which computers can use the account.</span></span>
<span data-ttu-id="8e356-156">gMSA의 유효 권한은 gMSA 계정이 속하는 보안 그룹(로컬 또는 도메인)에 의해 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="8e356-156">The effective permissions of the gMSA are defined by the security groups (local or domain) to which the gMSA account belongs.</span></span>

<span data-ttu-id="8e356-157">JEA 엔드포인트가 gMSA 계정을 사용하도록 구성된 경우 모든 JEA 사용자의 작업은 같은 그룹 관리 서비스 계정에서 온 것으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8e356-157">When a JEA endpoint is configured to use a gMSA account, the actions of all JEA users will appear to come from the same group managed service account.</span></span>
<span data-ttu-id="8e356-158">특정 사용자까지 거슬러 올라가 작업을 추적할 수 있는 유일한 방법은 PowerShell 세션 기록에서 실행된 명령 집합을 식별하는 것뿐입니다.</span><span class="sxs-lookup"><span data-stu-id="8e356-158">The only way you can trace actions back to a specific user is to identify the set of commands run in a PowerShell session transcript.</span></span>

<span data-ttu-id="8e356-159">**Pass-thru 자격 증명**은 실행 계정을 지정하지 않은 상태로 PowerShell에서 연결 사용자의 자격 증명을 원격 서버의 실행 명령에 연결하려 할 때 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8e356-159">**Pass-thru credentials** are used when you do not specify a run as account and want PowerShell to use the connecting user's credential to run commands on the remote server.</span></span>
<span data-ttu-id="8e356-160">이 구성은 연결하는 사용자에게 권한 있는 관리 그룹에 대한 직접 액세스 권한을 부여해야 하므로 JEA에는 권장되지 *않습니다*.</span><span class="sxs-lookup"><span data-stu-id="8e356-160">This configuration is *not* recommended for JEA as it would require you to grant the connecting user direct access to privileged management groups.</span></span>
<span data-ttu-id="8e356-161">연결하는 사용자에게 이미 관리자 권한이 있으면 JEA를 전부 피하고 다른 비제한 방법을 통해 시스템을 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e356-161">If the connecting user already has admin privileges, they can avoid JEA altogether and manage the system via other, unconstrained means.</span></span>
<span data-ttu-id="8e356-162">자세한 내용은 [JEA는 관리자로부터 보호하지 않음](#jea-does-not-protect-against-admins) 방법에 대한 아래 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8e356-162">See the section below on how [JEA does not protect against admins](#jea-does-not-protect-against-admins) for more information.</span></span>

<span data-ttu-id="8e356-163">**표준 실행 계정**을 사용하여 전체 PowerShell 세션이 실행될 사용자 계정을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e356-163">**Standard run as accounts** allow you to specify any user account under which the entire PowerShell session will run.</span></span>
<span data-ttu-id="8e356-164">고정 실행 계정을 사용하도록 설정된 세션 구성(`-RunAsCredential` 매개 변수 사용)은 JEA를 인식하지 않으므로 이는 중요한 구분입니다.</span><span class="sxs-lookup"><span data-stu-id="8e356-164">This is an important distinction, because a session configuration set to use a fixed run as account (with the `-RunAsCredential` parameter) is not JEA-aware.</span></span>
<span data-ttu-id="8e356-165">즉, 역할 정의가 더 이상 예상대로 작동하지 않고 엔드포인트에 액세스할 수 있는 권한이 있는 모든 사용자에게 같은 역할이 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="8e356-165">That means that role definitions no longer function as expected, and every user authorized to access the endpoint will be assigned the same role.</span></span>

<span data-ttu-id="8e356-166">특정 사용자까지 거슬러 올라가 작업을 추적하는 어려움이 있고 사용자를 역할에 매핑하는 지원이 없으므로 JEA 엔드포인트에는 RunAsCredential을 사용하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8e356-166">You should not use a RunAsCredential on a JEA endpoint because of the difficulty in tracing actions back to specific users and the lack of support for mapping users to roles.</span></span>

## <a name="winrm-endpoint-acl"></a><span data-ttu-id="8e356-167">WinRM 엔드포인트 ACL</span><span class="sxs-lookup"><span data-stu-id="8e356-167">WinRM Endpoint ACL</span></span>

<span data-ttu-id="8e356-168">일반 PowerShell 원격 엔드포인트와 마찬가지로 WinRM 구성에는 JEA 엔드포인트에서 인증할 수 있는 사용자를 제어하는 별도의 ACL(액세스 제어 목록)이 JEA 엔드포인트별로 설정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e356-168">As with regular PowerShell remoting endpoints, each JEA endpoint has a separate access control list (ACL) set in the WinRM configuration that controls who can authenticate with the JEA endpoint.</span></span>
<span data-ttu-id="8e356-169">잘못 구성된 경우 신뢰할 수 있는 사용자가 JEA 엔드포인트에 액세스할 수 없거나 신뢰할 수 없는 사용자가 액세스 권한을 얻을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e356-169">If improperly configured, trusted users may not be able to access the JEA endpoint and/or untrusted users may gain access.</span></span>
<span data-ttu-id="8e356-170">그러나 WinRM ACL이 사용자를 JEA 역할에 매핑하는 것에 영향을 주지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8e356-170">The WinRM ACL does not, however, affect the mapping of users to JEA roles.</span></span>
<span data-ttu-id="8e356-171">이러한 매핑은 시스템에 등록된 세션 구성 파일의 *RoleDefinitions* 필드에 의해 제어됩니다.</span><span class="sxs-lookup"><span data-stu-id="8e356-171">That is controlled by the *RoleDefinitions* field in the session configuration file that was registered on the system.</span></span>

<span data-ttu-id="8e356-172">기본적으로 세션 구성 파일 및 하나 이상의 역할 기능을 사용하여 JEA 엔드포인트를 등록하면 WinRM ACL은 하나 이상의 역할에 대한 모든 사용자 매핑이 엔드포인트에 액세스할 수 있도록 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="8e356-172">By default, when you register a JEA endpoint using a session configuration file and one or more role capabilities, the WinRM ACL will be configured to allow all users mapping to one or more roles access to the endpoint.</span></span>
<span data-ttu-id="8e356-173">예를 들어 다음 명령을 사용하여 구성된 JEA 세션은 *CONTOSO\JEA\_Lev1* 및 *CONTOSO\JEA\_Lev2*에 대한 모든 권한을 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="8e356-173">For example, a JEA session configured using the following commands will grant full access to *CONTOSO\JEA\_Lev1* and *CONTOSO\JEA\_Lev2*.</span></span>

```powershell
$roles = @{ 'CONTOSO\JEA_Lev1' = 'Lev1Role'; 'CONTOSO\JEA_Lev2' = 'Lev2Role' }
New-PSSessionConfigurationFile -Path '.\jea.pssc' -SessionType RestrictedRemoteServer -RoleDefinitions $roles -RunAsVirtualAccount
Register-PSSessionConfiguration -Path '.\jea.pssc' -Name 'MyJEAEndpoint'
```

<span data-ttu-id="8e356-174">[Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet을 사용하여 사용자 권한을 감사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e356-174">You can audit user permissions with the [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet.</span></span>

```powershell
PS C:\> Get-PSSessionConfiguration -Name 'MyJEAEndpoint' | Select-Object Permission

Permission
----------
CONTOSO\JEA_Lev1 AccessAllowed
CONTOSO\JEA_Lev2 AccessAllowed
```

<span data-ttu-id="8e356-175">액세스 권한을 갖는 사용자를 변경하려면 `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -ShowSecurityDescriptorUI`를 실행하여 대화형 프롬프트를 사용하거나 `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -SecurityDescriptorSddl <SDDL string>`을 실행하여 사용 권한을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="8e356-175">To change which users have access, run either `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -ShowSecurityDescriptorUI` for an interactive prompt or `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -SecurityDescriptorSddl <SDDL string>` to update the permissions.</span></span>
<span data-ttu-id="8e356-176">JEA 엔드포인트에 액세스하려면 사용자에게 최소한 *Invoke* 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e356-176">Users need at least *Invoke* rights to access the JEA endpoint.</span></span>

<span data-ttu-id="8e356-177">추가 사용자가 JEA 엔드포인트에 대한 액세스 권한을 부여받았지만 세션 구성 파일에 정의된 어떠한 역할에도 속하지 않는 경우 JEA 세션을 시작할 수는 있지만 기본 cmdlet에만 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e356-177">If additional users are granted access to the JEA endpoint but do not fall into any of the roles defined in the session configuration file, they will be able to start a JEA session but only have access to the default cmdlets.</span></span>
<span data-ttu-id="8e356-178">`Get-PSSessionCapability`를 실행하여 JEA 엔드포인트의 사용자 권한을 감사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e356-178">You can audit user permissions in a JEA endpoint by running `Get-PSSessionCapability`.</span></span>
<span data-ttu-id="8e356-179">JEA 엔드포인트에서 사용자가 액세스할 수 있는 명령 감사에 대한 자세한 내용은 [JEA에 대한 감사 및 보고](audit-and-report.md) 문서를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="8e356-179">Check out the [Auditing and Reporting on JEA](audit-and-report.md) article for more information about auditing which commands a user has access to in a JEA endpoint.</span></span>

## <a name="least-privilege-roles"></a><span data-ttu-id="8e356-180">최소 권한 역할</span><span class="sxs-lookup"><span data-stu-id="8e356-180">Least privilege roles</span></span>

<span data-ttu-id="8e356-181">JEA 역할을 디자인할 때는 백그라운드에서 실행되는 가상 또는 그룹 관리 서비스 계정이 흔히 로컬 컴퓨터를 관리할 수 있는 무제한 액세스 권한을 가진다는 사실을 기억해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e356-181">When designing JEA roles, it is important to remember that the virtual or group managed service account running behind the scenes often has unrestricted access to manage the local machine.</span></span>
<span data-ttu-id="8e356-182">JEA 역할 기능은 해당 권한 있는 컨텍스트를 사용하여 실행될 수 있는 명령 및 애플리케이션을 제한하여 사용될 수 있는 계정을 제한하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8e356-182">JEA role capabilities help restrict what that account can be used for by limiting the commands and applications that can be run using that privileged context.</span></span>
<span data-ttu-id="8e356-183">잘못 디자인된 역할은 사용자가 JEA 경계를 벗어나거나 중요 정보에 대한 액세스 권한을 획득할 수 있는 위험한 명령이 실행되게 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e356-183">Improperly designed roles can allow dangerous commands to run that may allow a user to break out of the JEA boundaries or obtain access to sensitive information.</span></span>

<span data-ttu-id="8e356-184">예를 들어 다음과 같은 역할 기능 항목을 생각해 봅니다.</span><span class="sxs-lookup"><span data-stu-id="8e356-184">For example, consider the following role capability entry:</span></span>

```powershell
@{
    VisibleCmdlets = 'Microsoft.PowerShell.Management\*-Process'
}
```

<span data-ttu-id="8e356-185">이 역할 기능을 통해 사용자는 Microsoft.PowerShell.Management 모듈에서 명사 "Process"를 사용하여 모든 PowerShell cmdlet을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e356-185">This role capability allows users to run any PowerShell cmdlet with the noun "Process" from the Microsoft.PowerShell.Management module.</span></span>
<span data-ttu-id="8e356-186">사용자는 `Get-Process`와 같은 cmdlet에 액세스하여 시스템에서 실행되고 있는 애플리케이션을 파악하고 `Stop-Process`에 액세스하여 응답 없는 애플리케이션을 종료해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e356-186">Users may need to access cmdlets like `Get-Process` to understand what applications are running on the system and `Stop-Process` to kill any hung applications.</span></span>
<span data-ttu-id="8e356-187">그러나 이 항목은 전체 관리자 권한으로 임의 프로그램을 시작하는 데 사용될 수 있는 `Start-Process`도 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="8e356-187">However, this entry also allows `Start-Process`, which can be used to start up an arbitrary program with full administrator permissions.</span></span>
<span data-ttu-id="8e356-188">프로그램이 시스템에 로컬로 설치될 필요가 없으므로 악의적 사용자가 연결하는 사용자에게 로컬 관리자 권한을 부여하고 맬웨어를 실행하는 등의 작업을 수행하는 프로그램을 파일 공유에서 손쉽게 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e356-188">The program doesn't need to be installed locally on the system, so an adversary could simply start a program on a file share that gives the connecting user local admin privileges, runs malware, and more.'</span></span>

<span data-ttu-id="8e356-189">이 역할 기능의 더 안전한 버전은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8e356-189">A more secure version of this same role capability would look like:</span></span>

```powershell
@{
    VisibleCmdlets = 'Microsoft.PowerShell.Management\Get-Process', 'Microsoft.PowerShell.Management\Stop-Process'
}
```

<span data-ttu-id="8e356-190">역할 기능에 와일드카드를 사용하지 말고 정기적으로 [유효 사용자 권한을 감사](audit-and-report.md#check-effective-rights-for-a-specific-user)하여 사용자가 액세스할 수 있는 명령을 파악해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e356-190">Avoid using wildcards in role capabilities, and be sure to [audit effective user permissions](audit-and-report.md#check-effective-rights-for-a-specific-user) regularly to understand which commands a user has access to.</span></span>

## <a name="jea-does-not-protect-against-admins"></a><span data-ttu-id="8e356-191">JEA는 관리자로부터 보호하지 않음</span><span class="sxs-lookup"><span data-stu-id="8e356-191">JEA does not protect against admins</span></span>

<span data-ttu-id="8e356-192">JEA의 핵심 원칙 중 하나는 관리자가 아닌 사용자가 *일부* 관리 작업을 수행할 수 있도록 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="8e356-192">One of the core principles of JEA is that it allows non-admins to perform *some* admin tasks.</span></span>
<span data-ttu-id="8e356-193">JEA는 이미 관리자 권한이 있는 사용자로부터 보호하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8e356-193">JEA does not protect against those who already have administrator privileges.</span></span>
<span data-ttu-id="8e356-194">환경의 "도메인 관리자", "로컬 관리자" 또는 기타 높은 권한이 있는 그룹에 속하는 사용자는 다른 방법을 통해 컴퓨터에 로그인하여 여전히 JEA의 보호를 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e356-194">Users who belong "domain admins," "local admins," or other highly privileged groups in your environment will still be able to get around JEA's protections by signing into the machine via another means.</span></span>
<span data-ttu-id="8e356-195">예를 들어 RDP를 사용하여 로그인하거나 원격 MMC 콘솔을 사용하거나 비제한 PowerShell 엔드포인트에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e356-195">They could, for example, sign in with RDP, use remote MMC consoles, or connect to unconstrained PowerShell endpoints.</span></span>
<span data-ttu-id="8e356-196">시스템의 로컬 관리자는 추가 사용자가 시스템을 관리할 수 있도록 하거나 역할 기능을 변경하여 사용자가 해당 JEA 세션에서 수행할 수 있는 작업의 범위를 확장할 수 있도록 JEA 구성을 수정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e356-196">Local admins on the system can also modify JEA configurations to allow additional users to manage the system or change a role capability to extend the scope of what a user can do in their JEA session.</span></span>
<span data-ttu-id="8e356-197">따라서 JEA 사용자의 확장된 사용 권한을 평가하여 시스템에 대한 권한 있는 액세스 권한을 얻을 수 있는 다른 방법이 있는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e356-197">It is therefore important to evaluate your JEA users' extended permissions to see if there are other ways they could gain privileged access to the system.</span></span>

<span data-ttu-id="8e356-198">일반적인 방법은 정기적인 일상 유지 관리에는 JEA를 사용하고 비상 상황에서 사용자가 일시적으로 로컬 관리자가 될 수 있도록 하는 "Just In Time" 권한 있는 액세스 권한 관리 솔루션을 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="8e356-198">A common practice is to use JEA for regular day-to-day maintenance and have a "just in time" privileged access management solution allow users to temporarily become local admins in emergency situations.</span></span>
<span data-ttu-id="8e356-199">이렇게 하면 사용자가 시스템에서 영구 관리자가 아니지만, 해당 사용 권한 사용을 문서화하는 워크플로를 완료하는 경우에만 해당 권한을 얻을 수 있도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e356-199">This helps ensure users are not permanent admins on the system, but can get those rights if, and only when, they complete a workflow that documents their use of those permissions.</span></span>