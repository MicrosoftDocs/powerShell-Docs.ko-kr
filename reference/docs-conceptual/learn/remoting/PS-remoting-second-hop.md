---
ms.date: 04/15/2020
keywords: powershell,cmdlet
title: PowerShell 원격에서 두 번째 홉 만들기
ms.openlocfilehash: 7819058bd8118ba44e66ec658017f536076609b5
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81527625"
---
# <a name="making-the-second-hop-in-powershell-remoting"></a><span data-ttu-id="a12a8-103">PowerShell 원격에서 두 번째 홉 만들기</span><span class="sxs-lookup"><span data-stu-id="a12a8-103">Making the second hop in PowerShell Remoting</span></span>

<span data-ttu-id="a12a8-104">"두 번째 홉 문제"는 다음과 같은 상황을 말합니다.</span><span class="sxs-lookup"><span data-stu-id="a12a8-104">The "second hop problem" refers to a situation like the following:</span></span>

1. <span data-ttu-id="a12a8-105">_ServerA_에 로그인되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a12a8-105">You are logged in to _ServerA_.</span></span>
2. <span data-ttu-id="a12a8-106">_ServerA_에서 원격 PowerShell 세션을 시작하여 _ServerB_에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="a12a8-106">From _ServerA_, you start a remote PowerShell session to connect to _ServerB_.</span></span>
3. <span data-ttu-id="a12a8-107">PowerShell 원격 세션을 통해 _ServerB_에서 실행하는 명령이 _ServerC_에 있는 리소스에 액세스하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="a12a8-107">A command you run on _ServerB_ via your PowerShell Remoting session attempts to access a resource on _ServerC_.</span></span>
4. <span data-ttu-id="a12a8-108">PowerShell 원격 세션을 만드는 데 사용한 자격 증명이 _ServerB_에서 _ServerC_로 전달되지 않았으므로 _ServerC_에 있는 리소스에 대한 액세스가 거부됩니다.</span><span class="sxs-lookup"><span data-stu-id="a12a8-108">Access to the resource on _ServerC_ is denied, because the credentials you used to create the PowerShell Remoting session are not passed from _ServerB_ to _ServerC_.</span></span>

<span data-ttu-id="a12a8-109">이 문제를 해결하는 방법은 여러 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a12a8-109">There are several ways to address this problem.</span></span> <span data-ttu-id="a12a8-110">이 항목에서는 두 번째 홉 문제에 대한 가장 인기 있는 해결 방법 몇 가지를 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="a12a8-110">In this topic, we'll look at several of the most popular solutions to the second hop problem.</span></span>

## <a name="credssp"></a><span data-ttu-id="a12a8-111">CredSSP</span><span class="sxs-lookup"><span data-stu-id="a12a8-111">CredSSP</span></span>

<span data-ttu-id="a12a8-112">인증에 [Credential Security Support Provider (CredSSP)](/windows/win32/secauthn/credential-security-support-provider)(CredSSP(자격 증명 보안 지원 공급자))를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a12a8-112">You can use the [Credential Security Support Provider (CredSSP)](/windows/win32/secauthn/credential-security-support-provider) for authentication.</span></span> <span data-ttu-id="a12a8-113">CredSSP는 원격 서버(_ServerB_)에 자격 증명을 캐시하므로, 이를 사용하면 자격 증명 도난 공격을 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a12a8-113">CredSSP caches credentials on the remote server (_ServerB_), so using it opens you up to credential theft attacks.</span></span> <span data-ttu-id="a12a8-114">원격 컴퓨터의 보안이 손상되면 공격자가 사용자의 자격 증명에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a12a8-114">If the remote computer is compromised, the attacker has access to the user's credentials.</span></span> <span data-ttu-id="a12a8-115">기본적으로 CredSSP는 클라이언트 및 서버 컴퓨터 모두에서 사용하지 않도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="a12a8-115">CredSSP is disabled by default on both client and server computers.</span></span> <span data-ttu-id="a12a8-116">가장 신뢰할 수 있는 환경에서만 CredSSP를 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a12a8-116">You should enable CredSSP only in the most trusted environments.</span></span> <span data-ttu-id="a12a8-117">예를 들어 도메인 컨트롤러는 매우 신뢰할 수 있으므로 도메인 관리자는 도메인 컨트롤러에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="a12a8-117">For example, a domain administrator connecting to a domain controller because the domain controller is highly trusted.</span></span>

<span data-ttu-id="a12a8-118">PowerShell 원격에 CredSSP 사용 시의 보안 우려 사항에 대한 자세한 내용은 [Accidental Sabotage: Beware of CredSSP](https://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp)(고의적 파괴: CredSSP 조심)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a12a8-118">For more information about security concerns when using CredSSP for PowerShell Remoting, see [Accidental Sabotage: Beware of CredSSP](https://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp).</span></span>

<span data-ttu-id="a12a8-119">자격 증명 도난 공격에 대한 자세한 내용은 [PtH(Pass-the-Hash) 공격 및 기타 자격 증명 도난 완화](https://www.microsoft.com/en-us/download/details.aspx?id=36036)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a12a8-119">For more information about credential theft attacks, see [Mitigating Pass-the-Hash (PtH) Attacks and Other Credential Theft](https://www.microsoft.com/en-us/download/details.aspx?id=36036).</span></span>

<span data-ttu-id="a12a8-120">PowerShell 원격에 대해 CredSSP를 사용하도록 설정하고 사용하는 방법의 예는 [Enable PowerShell "Second-Hop" Functionality with CredSSP(CredSSP를 사용하여 PowerShell "두 번째 홉" 기능 사용)](https://devblogs.microsoft.com/scripting/enable-powershell-second-hop-functionality-with-credssp/)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a12a8-120">For an example of how to enable and use CredSSP for PowerShell remoting, see [Enable PowerShell "Second-Hop" Functionality with CredSSP](https://devblogs.microsoft.com/scripting/enable-powershell-second-hop-functionality-with-credssp/).</span></span>

### <a name="pros"></a><span data-ttu-id="a12a8-121">장점</span><span class="sxs-lookup"><span data-stu-id="a12a8-121">Pros</span></span>

- <span data-ttu-id="a12a8-122">Windows Server 2008 이상이 설치된 모든 서버에 대해 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="a12a8-122">It works for all servers with Windows Server 2008 or later.</span></span>

### <a name="cons"></a><span data-ttu-id="a12a8-123">단점</span><span class="sxs-lookup"><span data-stu-id="a12a8-123">Cons</span></span>

- <span data-ttu-id="a12a8-124">보안 취약성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a12a8-124">Has security vulnerabilities.</span></span>
- <span data-ttu-id="a12a8-125">클라이언트 역할과 서버 역할을 둘 다 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a12a8-125">Requires configuration of both client and server roles.</span></span>

## <a name="kerberos-delegation-unconstrained"></a><span data-ttu-id="a12a8-126">Kerberos 위임(비제한)</span><span class="sxs-lookup"><span data-stu-id="a12a8-126">Kerberos delegation (unconstrained)</span></span>

<span data-ttu-id="a12a8-127">Kerberos 비제한 위임을 사용하여 두 번째 홉을 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a12a8-127">You can also used Kerberos unconstrained delegation to make the second hop.</span></span> <span data-ttu-id="a12a8-128">그러나 이 방법을 사용할 경우 위임된 자격 증명이 사용되는 위치를 제어할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a12a8-128">However, this method provides no control of where delegated credentials are used.</span></span>

> [!NOTE]
> <span data-ttu-id="a12a8-129">**계정이 민감하여 위임할 수 없음** 속성이 설정된 Active Directory 계정은 위임할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a12a8-129">Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="a12a8-130">자세한 내용은 [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](/archive/blogs/poshchap/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts)(보안 초점: 권한 있는 계정에 대한 '계정이 민감하여 위임할 수 없음' 분석) 및 [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)(Kerberos 인증 도구 및 설정)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a12a8-130">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](/archive/blogs/poshchap/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts) and [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx).</span></span>

### <a name="pros"></a><span data-ttu-id="a12a8-131">장점</span><span class="sxs-lookup"><span data-stu-id="a12a8-131">Pros</span></span>

- <span data-ttu-id="a12a8-132">특수 코딩이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a12a8-132">Requires no special coding.</span></span>

### <a name="cons"></a><span data-ttu-id="a12a8-133">단점</span><span class="sxs-lookup"><span data-stu-id="a12a8-133">Cons</span></span>

- <span data-ttu-id="a12a8-134">WinRM에 대한 두 번째 홉을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a12a8-134">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="a12a8-135">자격 증명이 사용되는 위치를 제어할 수 없어 보안 취약성이 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="a12a8-135">Provides no control over where credentials are used, creating a security vulnerability.</span></span>

## <a name="kerberos-constrained-delegation"></a><span data-ttu-id="a12a8-136">Kerberos 제한 위임</span><span class="sxs-lookup"><span data-stu-id="a12a8-136">Kerberos constrained delegation</span></span>

<span data-ttu-id="a12a8-137">레거시 제한 위임(리소스 기반 아님)을 사용하여 두 번째 홉을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a12a8-137">You can use legacy constrained delegation (not resource-based) to make the second hop.</span></span> <span data-ttu-id="a12a8-138">"모든 인증 프로토콜 사용" 옵션을 사용하여 프로토콜 전환을 허용하도록 Kerberos 제한 위임을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="a12a8-138">Configure Kerberos constrained delegation with the option "Use any authentication protocol" to allow protocol transition.</span></span>

> [!NOTE]
> <span data-ttu-id="a12a8-139">**계정이 민감하여 위임할 수 없음** 속성이 설정된 Active Directory 계정은 위임할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a12a8-139">Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="a12a8-140">자세한 내용은 [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](/archive/blogs/poshchap/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts)(보안 초점: 권한 있는 계정에 대한 '계정이 민감하여 위임할 수 없음' 분석) 및 [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)(Kerberos 인증 도구 및 설정)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a12a8-140">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](/archive/blogs/poshchap/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts) and [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span></span>

### <a name="pros"></a><span data-ttu-id="a12a8-141">장점</span><span class="sxs-lookup"><span data-stu-id="a12a8-141">Pros</span></span>

- <span data-ttu-id="a12a8-142">특수 코딩이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a12a8-142">Requires no special coding</span></span>

### <a name="cons"></a><span data-ttu-id="a12a8-143">단점</span><span class="sxs-lookup"><span data-stu-id="a12a8-143">Cons</span></span>

- <span data-ttu-id="a12a8-144">WinRM에 대한 두 번째 홉을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a12a8-144">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="a12a8-145">원격 서버(_ServerB_)의 Active Directory 개체에 대해 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a12a8-145">Must be configured on the Active Directory object of the remote server (_ServerB_).</span></span>
- <span data-ttu-id="a12a8-146">도메인 하나로 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="a12a8-146">Limited to one domain.</span></span> <span data-ttu-id="a12a8-147">도메인 또는 포리스트를 벗어날 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a12a8-147">Cannot cross domains or forests.</span></span>
- <span data-ttu-id="a12a8-148">개체 및 SPN(서비스 사용자 이름)을 업데이트할 수 있는 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="a12a8-148">Requires rights to update objects and Service Principal Names (SPNs).</span></span>

## <a name="resource-based-kerberos-constrained-delegation"></a><span data-ttu-id="a12a8-149">리소스 기반 Kerberos 제한 위임</span><span class="sxs-lookup"><span data-stu-id="a12a8-149">Resource-based Kerberos constrained delegation</span></span>

<span data-ttu-id="a12a8-150">리소스 기반 Kerberos 제한 위임(Windows Server 2012에 도입됨)을 사용하여 리소스가 있는 서버 개체에 대한 자격 증명 위임을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="a12a8-150">Using resource-based Kerberos constrained delegation (introduced in Windows Server 2012), you configure credential delegation on the server object where resources reside.</span></span> <span data-ttu-id="a12a8-151">위에서 설명한 두 번째 홉 시나리오에서 위임된 자격 증명을 허용할 위치를 지정하도록 _ServerC_를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="a12a8-151">In the second hop scenario described above, you configure _ServerC_ to specify from where it will accept delegated credentials.</span></span>

> [!NOTE]
> <span data-ttu-id="a12a8-152">**계정이 민감하여 위임할 수 없음** 속성이 설정된 Active Directory 계정은 위임할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a12a8-152">Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="a12a8-153">자세한 내용은 [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](/archive/blogs/poshchap/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts)(보안 초점: 권한 있는 계정에 대한 '계정이 민감하여 위임할 수 없음' 분석) 및 [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)(Kerberos 인증 도구 및 설정)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a12a8-153">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](/archive/blogs/poshchap/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts) and [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span></span>

### <a name="pros"></a><span data-ttu-id="a12a8-154">장점</span><span class="sxs-lookup"><span data-stu-id="a12a8-154">Pros</span></span>

- <span data-ttu-id="a12a8-155">자격 증명이 저장되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a12a8-155">Credentials are not stored.</span></span>
- <span data-ttu-id="a12a8-156">PowerShell cmdlet을 사용하여 비교적 쉽게 구성할 수 있으며 특수 코딩이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a12a8-156">Relatively easy to configure by using PowerShell cmdlets--no special coding required.</span></span>
- <span data-ttu-id="a12a8-157">특별 도메인 액세스가 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a12a8-157">No special domain access is required.</span></span>
- <span data-ttu-id="a12a8-158">도메인 및 포리스트에서 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="a12a8-158">Works across domains and forests.</span></span>
- <span data-ttu-id="a12a8-159">PowerShell 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="a12a8-159">PowerShell code.</span></span>

### <a name="cons"></a><span data-ttu-id="a12a8-160">단점</span><span class="sxs-lookup"><span data-stu-id="a12a8-160">Cons</span></span>

- <span data-ttu-id="a12a8-161">Windows Server 2012 이상이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="a12a8-161">Requires Windows Server 2012 or later.</span></span>
- <span data-ttu-id="a12a8-162">WinRM에 대한 두 번째 홉을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a12a8-162">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="a12a8-163">개체 및 SPN(서비스 사용자 이름)을 업데이트할 수 있는 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="a12a8-163">Requires rights to update objects and Service Principal Names (SPNs).</span></span>

### <a name="example"></a><span data-ttu-id="a12a8-164">예제</span><span class="sxs-lookup"><span data-stu-id="a12a8-164">Example</span></span>

<span data-ttu-id="a12a8-165">_ServerB_의 위임된 자격 증명을 허용하도록 _ServerC_에 대해 리소스 기반 제한 위임을 구성하는 PowerShell 예제를 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="a12a8-165">Let's look at a PowerShell example that configures resource based constrained delegation on _ServerC_ to allow delegated credentials from a _ServerB_.</span></span> <span data-ttu-id="a12a8-166">이 예제에서는 모든 서버가 Windows Server 2012 이상을 실행하고 있으며 서버가 속하는 각 도메인에 하나 이상의 Windows Server 2012 도메인 컨트롤러가 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="a12a8-166">This example assumes that all servers are running Windows Server 2012 or later, and that there is at least one Windows Server 2012 domain controller each domain to which any of the servers belong.</span></span>

<span data-ttu-id="a12a8-167">제한 위임을 구성하기 전에 먼저 `RSAT-AD-PowerShell` 기능을 추가하여 Active Directory PowerShell 모듈을 설치한 다음 해당 모듈을 세션으로 가져와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a12a8-167">Before you can configure constrained delegation, you must add the `RSAT-AD-PowerShell` feature to install the Active Directory PowerShell module, and then import that module into your session:</span></span>

```powershell
PS C:\> Add-WindowsFeature RSAT-AD-PowerShell
PS C:\> Import-Module ActiveDirectory
```

<span data-ttu-id="a12a8-168">이제 사용할 수 있는 여러 cmdlet에 **PrincipalsAllowedToDelegateToAccount** 매개 변수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a12a8-168">Several available cmdlets now have a **PrincipalsAllowedToDelegateToAccount** parameter:</span></span>

```powershell
PS C:\> Get-Command -ParameterName PrincipalsAllowedToDelegateToAccount

CommandType Name                 ModuleName
----------- ----                 ----------
Cmdlet      New-ADComputer       ActiveDirectory
Cmdlet      New-ADServiceAccount ActiveDirectory
Cmdlet      New-ADUser           ActiveDirectory
Cmdlet      Set-ADComputer       ActiveDirectory
Cmdlet      Set-ADServiceAccount ActiveDirectory
Cmdlet      Set-ADUser           ActiveDirectory
```

<span data-ttu-id="a12a8-169">**PrincipalsAllowedToDelegateToAccount** 매개 변수는 Active Directory 개체 특성 **msDS-AllowedToActOnBehalfOfOtherIdentity**를 설정합니다. 이 특성은 자격 증명을 연결된 계정(이 예제에서는 _Server_의 컴퓨터 계정이 됨)에 위임할 수 있는 권한이 있는 계정을 지정하는 ACL(액세스 제어 목록)을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="a12a8-169">The **PrincipalsAllowedToDelegateToAccount** parameter sets the Active Directory object attribute **msDS-AllowedToActOnBehalfOfOtherIdentity**, which contains an access control list (ACL) that specifies which accounts have permission to delegate credentials to the associated account (in our example, it will be the machine account for _Server_).</span></span>

<span data-ttu-id="a12a8-170">이제 서버를 나타내는 데 사용할 변수를 설정하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="a12a8-170">Now let's set up the variables we'll use to represent the servers:</span></span>

```powershell
# Set up variables for reuse
$ServerA = $env:COMPUTERNAME
$ServerB = Get-ADComputer -Identity ServerB
$ServerC = Get-ADComputer -Identity ServerC
```

<span data-ttu-id="a12a8-171">WinRM(및 따라서 PowerShell 원격)은 기본적으로 컴퓨터 계정으로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="a12a8-171">WinRM (and therefore PowerShell remoting) runs as the computer account by default.</span></span> <span data-ttu-id="a12a8-172">`winrm` 서비스의 **StartName** 속성을 살펴보아 이를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a12a8-172">You can see this by looking at the **StartName** property of the `winrm` service:</span></span>

```powershell
PS C:\> Get-WmiObject win32_service -filter 'name="winrm"' | Format-List StartName

StartName : NT AUTHORITY\NetworkService
```

<span data-ttu-id="a12a8-173">_ServerC_가 _ServerB_의 PowerShell 원격 세션으로부터의 위임을 허용하도록 _ServerC_에 대한 **PrincipalsAllowedToDelegateToAccount** 매개 변수를 _ServerB_의 컴퓨터 개체로 설정하여 액세스 권한을 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="a12a8-173">For _ServerC_ to allow delegation from a PowerShell remoting session on _ServerB_, we will grant access by setting the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to the computer object of _ServerB_:</span></span>

```powershell
# Grant resource-based Kerberos constrained delegation
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB

# Check the value of the attribute directly
$x = Get-ADComputer -Identity $ServerC -Properties msDS-AllowedToActOnBehalfOfOtherIdentity
$x.'msDS-AllowedToActOnBehalfOfOtherIdentity'.Access

# Check the value of the attribute indirectly
Get-ADComputer -Identity $ServerC -Properties PrincipalsAllowedToDelegateToAccount
```

<span data-ttu-id="a12a8-174">Kerberos [Key Distribution Center (KDC)](/windows/win32/secauthn/key-distribution-center)KDC(키 배포 센터)는 15분마다 거부된 액세스 시도(부정 캐시)를 캐시합니다.</span><span class="sxs-lookup"><span data-stu-id="a12a8-174">The Kerberos [Key Distribution Center (KDC)](/windows/win32/secauthn/key-distribution-center) caches denied access attempts (negative cache) for 15 minutes.</span></span> <span data-ttu-id="a12a8-175">_ServerB_가 이전에 _ServerC_에 액세스하려고 시도한 경우 다음 명령을 호출하여 _ServerB_의 캐시를 지워야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a12a8-175">If _ServerB_ has previously attempted to access _ServerC_, you will need to clear the cache on _ServerB_ by invoking the following command:</span></span>

```powershell
Invoke-Command -ComputerName $ServerB.Name -Credential $cred -ScriptBlock {
    klist purge -li 0x3e7
}
```

<span data-ttu-id="a12a8-176">캐시를 지우기 위해 컴퓨터를 다시 시작하거나 15분 이상 기다려야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a12a8-176">You could also restart the computer, or wait at least 15 minutes to clear the cache.</span></span>

<span data-ttu-id="a12a8-177">캐시를 지운 후 _ServerA_에서 _ServerB_를 거쳐 _ServerC_까지 코드를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a12a8-177">After clearing the cache, you can successfully run code from _ServerA_ through _ServerB_ to _ServerC_:</span></span>

```powershell
# Capture a credential
$cred = Get-Credential Contoso\Alice

# Test kerberos double hop
Invoke-Command -ComputerName $ServerB.Name -Credential $cred -ScriptBlock {
    Test-Path \\$($using:ServerC.Name)\C$
    Get-Process lsass -ComputerName $($using:ServerC.Name)
    Get-EventLog -LogName System -Newest 3 -ComputerName $($using:ServerC.Name)
}
```

<span data-ttu-id="a12a8-178">이 예제에서 `$using` 변수는 `$ServerC` 변수가 _ServerB_에 표시되도록 하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="a12a8-178">In this example, the `$using` variable is used to make the `$ServerC` variable visible to _ServerB_.</span></span>
<span data-ttu-id="a12a8-179">`$using` 변수에 대한 자세한 내용은 [about_Remote_Variables](https://technet.microsoft.com/library/jj149005.aspx)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a12a8-179">For more information about the `$using` variable, see [about_Remote_Variables](https://technet.microsoft.com/library/jj149005.aspx).</span></span>

<span data-ttu-id="a12a8-180">여러 서버가 _ServerC_에 자격 증명을 위임할 수 있도록 하려면 _ServerC_에 대한 **PrincipalsAllowedToDelegateToAccount** 매개 변수 값을 배열로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="a12a8-180">To allow multiple servers to delegate credentials to _ServerC_, set the value of the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to an array:</span></span>

```powershell
# Set up variables for each server
$ServerB1 = Get-ADComputer -Identity ServerB1
$ServerB2 = Get-ADComputer -Identity ServerB2
$ServerB3 = Get-ADComputer -Identity ServerB3
$ServerC  = Get-ADComputer -Identity ServerC

# Grant resource-based Kerberos constrained delegation
Set-ADComputer -Identity $ServerC `
    -PrincipalsAllowedToDelegateToAccount @($ServerB1,$ServerB2,$ServerB3)
```

<span data-ttu-id="a12a8-181">도메인에 걸쳐 두 번째 홉을 만들려는 경우 _ServerB_가 속하는 도메인의 도메인 컨트롤러에 대한 FQDN(정규화된 도메인 이름)을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="a12a8-181">If you want to make the second hop across domains, add fully-qualified domain name (FQDN) of the domain controller of the domain to which _ServerB_ belongs:</span></span>

```powershell
# For ServerC in Contoso domain and ServerB in other domain
$ServerB = Get-ADComputer -Identity ServerB -Server dc1.alpineskihouse.com
$ServerC = Get-ADComputer -Identity ServerC
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB
```

<span data-ttu-id="a12a8-182">ServerC에 자격 증명을 위임하는 기능을 제거하려면 _ServerC_에 대한 **PrincipalsAllowedToDelegateToAccount** 매개 변수 값을 `$null`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="a12a8-182">To remove the ability to delegate credentials to ServerC, set the value of the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to `$null`:</span></span>

```powershell
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $null
```

### <a name="information-on-resource-based-kerberos-constrained-delegation"></a><span data-ttu-id="a12a8-183">리소스 기반 Kerberos 제한 위임에 대한 정보</span><span class="sxs-lookup"><span data-stu-id="a12a8-183">Information on resource-based Kerberos constrained delegation</span></span>

- <span data-ttu-id="a12a8-184">[Kerberos 인증의 새로운 기능](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831747(v=ws.11))</span><span class="sxs-lookup"><span data-stu-id="a12a8-184">[What's New in Kerberos Authentication](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831747(v=ws.11))</span></span>
- <span data-ttu-id="a12a8-185">[How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 1](https://www.itprotoday.com/windows-server/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-1)(Windows Server 2012에서 Kerberos 제한 위임의 불편을 줄이는 방법, 1부)</span><span class="sxs-lookup"><span data-stu-id="a12a8-185">[How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 1](https://www.itprotoday.com/windows-server/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-1)</span></span>
- <span data-ttu-id="a12a8-186">[How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 2](https://www.itprotoday.com/windows-server/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-2)(Windows Server 2012에서 Kerberos 제한 위임의 불편을 줄이는 방법, 2부)</span><span class="sxs-lookup"><span data-stu-id="a12a8-186">[How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 2](https://www.itprotoday.com/windows-server/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-2)</span></span>
- <span data-ttu-id="a12a8-187">[Understanding Kerberos Constrained Delegation for Azure Active Directory Application Proxy Deployments with Integrated Windows Authentication](https://aka.ms/kcdpaper)(Windows 통합 인증을 사용한 Azure Active Directory 애플리케이션 프록시 배포에 대한 Kerberos 제한 인증 이해)</span><span class="sxs-lookup"><span data-stu-id="a12a8-187">[Understanding Kerberos Constrained Delegation for Azure Active Directory Application Proxy Deployments with Integrated Windows Authentication](https://aka.ms/kcdpaper)</span></span>
- <span data-ttu-id="a12a8-188">[[MS-ADA2]: Active Directory Schema Attributes M2.210 Attribute msDS-AllowedToActOnBehalfOfOtherIdentity](/openspecs/windows_protocols/ms-ada2/cea4ac11-a4b2-4f2d-84cc-aebb4a4ad405)([MS-ADA2]: Active Directory 스키마 특성 M2.210 특성 msDS-AllowedToActOnBehalfOfOtherIdentity)</span><span class="sxs-lookup"><span data-stu-id="a12a8-188">[[MS-ADA2]: Active Directory Schema Attributes M2.210 Attribute msDS-AllowedToActOnBehalfOfOtherIdentity](/openspecs/windows_protocols/ms-ada2/cea4ac11-a4b2-4f2d-84cc-aebb4a4ad405)</span></span>
- <span data-ttu-id="a12a8-189">[[MS-SFU]: Kerberos 프로토콜 확장: Service for User and Constrained Delegation Protocol 1.3.2 S4U2proxy](/openspecs/windows_protocols/ms-sfu/bde93b0e-f3c9-4ddf-9f44-e1453be7af5a)([MS-SFU]: Kerberos 프로토콜 확장: 사용자 서비스 및 제한 위임 프로토콜 1.3.2 S4U2proxy)</span><span class="sxs-lookup"><span data-stu-id="a12a8-189">[[MS-SFU]: Kerberos Protocol Extensions: Service for User and Constrained Delegation Protocol 1.3.2 S4U2proxy](/openspecs/windows_protocols/ms-sfu/bde93b0e-f3c9-4ddf-9f44-e1453be7af5a)</span></span>
- <span data-ttu-id="a12a8-190">[Remote Administration Without Constrained Delegation Using PrincipalsAllowedToDelegateToAccount](/archive/blogs/taylorb/remote-administration-without-constrained-delegation-using-principalsallowedtodelegatetoaccount)(PrincipalsAllowedToDelegateToAccount를 사용한 제한 위임 없는 원격 관리)</span><span class="sxs-lookup"><span data-stu-id="a12a8-190">[Remote Administration Without Constrained Delegation Using PrincipalsAllowedToDelegateToAccount](/archive/blogs/taylorb/remote-administration-without-constrained-delegation-using-principalsallowedtodelegatetoaccount)</span></span>

## <a name="pssessionconfiguration-using-runas"></a><span data-ttu-id="a12a8-191">RunAs를 사용한 PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="a12a8-191">PSSessionConfiguration using RunAs</span></span>

<span data-ttu-id="a12a8-192">_ServerB_에 대한 세션 구성을 만들고 해당 **RunAsCredential** 매개 변수를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a12a8-192">You can create a session configuration on _ServerB_ and set its **RunAsCredential** parameter.</span></span>

<span data-ttu-id="a12a8-193">PSSessionConfiguration 및 RunAs를 사용하여 두 번째 홉 문제를 해결하는 방법에 대한 자세한 내용은 [Another solution to multi-hop PowerShell remoting](/archive/blogs/sergey_babkins_blog/another-solution-to-multi-hop-powershell-remoting)(다중 홉 PowerShell 원격에 대한 다른 해결 방법)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a12a8-193">For information about using PSSessionConfiguration and RunAs to solve the second hop problem, see [Another solution to multi-hop PowerShell remoting](/archive/blogs/sergey_babkins_blog/another-solution-to-multi-hop-powershell-remoting).</span></span>

### <a name="pros"></a><span data-ttu-id="a12a8-194">장점</span><span class="sxs-lookup"><span data-stu-id="a12a8-194">Pros</span></span>

- <span data-ttu-id="a12a8-195">WMF 3.0 이상이 설치된 모든 서버에서 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="a12a8-195">Works with any server with WMF 3.0 or later.</span></span>

### <a name="cons"></a><span data-ttu-id="a12a8-196">단점</span><span class="sxs-lookup"><span data-stu-id="a12a8-196">Cons</span></span>

- <span data-ttu-id="a12a8-197">모든 중간 서버(_ServerB_)에 대해 **PSSessionConfiguration** 및 **RunAs**를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a12a8-197">Requires configuration of **PSSessionConfiguration** and **RunAs** on every intermediate server (_ServerB_).</span></span>
- <span data-ttu-id="a12a8-198">도메인 **RunAs** 계정을 사용할 경우 암호를 유지 관리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a12a8-198">Requires password maintenance when using a domain **RunAs** account</span></span>

## <a name="just-enough-administration-jea"></a><span data-ttu-id="a12a8-199">JEA(Just Enough Administration)</span><span class="sxs-lookup"><span data-stu-id="a12a8-199">Just Enough Administration (JEA)</span></span>

<span data-ttu-id="a12a8-200">JEA를 사용하여 PowerShell 세션 동안 관리자가 실행할 수 있는 명령을 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a12a8-200">JEA allows you to restrict what commands an administrator can run during a PowerShell session.</span></span> <span data-ttu-id="a12a8-201">두 번째 홉 문제를 해결하는 데 JEA를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a12a8-201">It can be used to solve the second hop problem.</span></span>

<span data-ttu-id="a12a8-202">JEA에 대한 자세한 내용은 [Just Enough Administration](/powershell/scripting/learn/remoting/jea/overview)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a12a8-202">For information about JEA, see [Just Enough Administration](/powershell/scripting/learn/remoting/jea/overview).</span></span>

### <a name="pros"></a><span data-ttu-id="a12a8-203">장점</span><span class="sxs-lookup"><span data-stu-id="a12a8-203">Pros</span></span>

- <span data-ttu-id="a12a8-204">가상 계정을 사용할 경우 암호를 유지 관리할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a12a8-204">No password maintenance when using a virtual account.</span></span>

### <a name="cons"></a><span data-ttu-id="a12a8-205">단점</span><span class="sxs-lookup"><span data-stu-id="a12a8-205">Cons</span></span>

- <span data-ttu-id="a12a8-206">WMF 5.0 이상이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="a12a8-206">Requires WMF 5.0 or later.</span></span>
- <span data-ttu-id="a12a8-207">모든 중간 서버(_ServerB_)에 대한 구성이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="a12a8-207">Requires configuration on every intermediate server (_ServerB_).</span></span>

## <a name="pass-credentials-inside-an-invoke-command-script-block"></a><span data-ttu-id="a12a8-208">Invoke-Command 스크립트 블록 내에 자격 증명 전달</span><span class="sxs-lookup"><span data-stu-id="a12a8-208">Pass credentials inside an Invoke-Command script block</span></span>

<span data-ttu-id="a12a8-209">[Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) cmdlet 호출의 **ScriptBlock** 매개 변수 내에 자격 증명을 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a12a8-209">You can pass credentials inside the **ScriptBlock** parameter of a call to the [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) cmdlet.</span></span>

### <a name="pros"></a><span data-ttu-id="a12a8-210">장점</span><span class="sxs-lookup"><span data-stu-id="a12a8-210">Pros</span></span>

- <span data-ttu-id="a12a8-211">특별한 서버 구성이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a12a8-211">Does not require special server configuration.</span></span>
- <span data-ttu-id="a12a8-212">WMF 2.0 이상을 실행하는 모든 서버에서 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="a12a8-212">Works on any server running WMF 2.0 or later.</span></span>

### <a name="cons"></a><span data-ttu-id="a12a8-213">단점</span><span class="sxs-lookup"><span data-stu-id="a12a8-213">Cons</span></span>

- <span data-ttu-id="a12a8-214">불편한 코드 기법이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="a12a8-214">Requires an awkward code technique.</span></span>
- <span data-ttu-id="a12a8-215">WMF 2.0을 실행하는 경우 원격 세션으로 인수를 전달하는 데 서로 다른 구문이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="a12a8-215">If running WMF 2.0, requires different syntax for passing arguments to a remote session.</span></span>

### <a name="example"></a><span data-ttu-id="a12a8-216">예제</span><span class="sxs-lookup"><span data-stu-id="a12a8-216">Example</span></span>

<span data-ttu-id="a12a8-217">다음 예제에서는 **Invoke-Command** 스크립트 블록으로 자격 증명을 전달하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a12a8-217">The following example shows how to pass credentials in an **Invoke-Command** script block:</span></span>

```powershell
# This works without delegation, passing fresh creds
# Note $Using:Cred in nested request
$cred = Get-Credential Contoso\Administrator
Invoke-Command -ComputerName ServerB -Credential $cred -ScriptBlock {
    hostname
    Invoke-Command -ComputerName ServerC -Credential $Using:cred -ScriptBlock {hostname}
}
```

## <a name="see-also"></a><span data-ttu-id="a12a8-218">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a12a8-218">See also</span></span>

[<span data-ttu-id="a12a8-219">PowerShell Remoting 보안 고려 사항</span><span class="sxs-lookup"><span data-stu-id="a12a8-219">PowerShell Remoting Security Considerations</span></span>](WinRMSecurity.md)
