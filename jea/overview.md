---
ms.date: 06/12/2017
keywords: jea,powershell,security
title: Just Enough Administration 개요
ms.openlocfilehash: c097838fb25a63d42502eebf751c64c537bdd077
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55681023"
---
# <a name="just-enough-administration"></a><span data-ttu-id="0aad6-103">JEA(Just Enough Administration)</span><span class="sxs-lookup"><span data-stu-id="0aad6-103">Just Enough Administration</span></span>

<span data-ttu-id="0aad6-104">JEA(Just Enough Administration)는 PowerShell로 관리할 수 있는 모든 것에 대한 위임된 관리를 가능하게 하는 보안 기술입니다.</span><span class="sxs-lookup"><span data-stu-id="0aad6-104">Just Enough Administration (JEA) is a security technology that enables delegated administration for anything that can be managed with PowerShell.</span></span>
<span data-ttu-id="0aad6-105">JEA를 사용하면 다음이 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="0aad6-105">With JEA, you can:</span></span>

- <span data-ttu-id="0aad6-106">**컴퓨터의 관리자 수 감소**: 일반 사용자를 대신하여 권한 있는 작업을 수행하는 가상 계정 또는 그룹 관리 서비스 계정을 활용합니다.</span><span class="sxs-lookup"><span data-stu-id="0aad6-106">**Reduce the number of administrators on your machines** by leveraging virtual accounts or group managed service accounts that perform privileged actions on behalf of regular users.</span></span>
- <span data-ttu-id="0aad6-107">**사용자가 수행할 수 있는 작업 제한**: 사용자가 실행할 수 있는 cmdlet, 함수 및 외부 명령을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0aad6-107">**Limit what users can do** by specifying which cmdlets, functions, and external commands they can run.</span></span>
- <span data-ttu-id="0aad6-108">**사용자가 수행하고 있는 작업을 보다 효과적으로 이해**: 사용자가 해당 세션 중에 실행한 명령을 정확하게 보여 주는 기록 및 로그를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0aad6-108">**Better understand what your users are doing** with transcripts and logs that show you exactly which commands a user executed during their session.</span></span>

<span data-ttu-id="0aad6-109">**JEA가 중요한 이유는 무엇일까요?**</span><span class="sxs-lookup"><span data-stu-id="0aad6-109">**Why is this important?**</span></span>

<span data-ttu-id="0aad6-110">서버를 관리하는 데 사용된 높은 권한이 있는 계정은 심각한 보안 위험을 일으킵니다.</span><span class="sxs-lookup"><span data-stu-id="0aad6-110">Highly privileged accounts used to administer your servers pose a serious security risk.</span></span>
<span data-ttu-id="0aad6-111">공격자가 이러한 계정 중 하나를 손상시키면 조직 전체에서 [lateral attacks](http://aka.ms/pth)(측면 공격)를 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0aad6-111">Should an attacker compromise one of these accounts, they could launch [lateral attacks](http://aka.ms/pth) across your organization.</span></span>
<span data-ttu-id="0aad6-112">손상된 각 계정은 더 많은 계정 및 리소스에 대한 액세스 권한을 공격자에게 부여하여 공격자가 회사 기밀을 훔치거나 서비스 거부 공격을 시작하는 등을 하는데 한 걸음 더 다가서게 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0aad6-112">Each account they compromise can give them access to even more accounts and resources, putting them one step closer to stealing company secrets, launching a denial-of-service attack, and more.</span></span>

<span data-ttu-id="0aad6-113">그러나 관리 권한을 제거하기가 항상 쉽지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0aad6-113">It is not always easy to remove administrative privileges, either.</span></span>
<span data-ttu-id="0aad6-114">Active Directory 도메인 컨트롤러와 같은 컴퓨터에 DNS 역할이 설치되어 있는 일반적인 시나리오를 생각해 봅니다.</span><span class="sxs-lookup"><span data-stu-id="0aad6-114">Consider the common scenario where the DNS role is installed on the same machine as your Active Directory Domain Controller.</span></span>
<span data-ttu-id="0aad6-115">DNS 관리자는 DNS 서버의 문제를 해결하기 위해 로컬 관리자 권한이 필요하지만, 이를 위해서는 DNS 관리자를 높은 권한이 있는 "Domain Admins" 보안 그룹의 구성원으로 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0aad6-115">Your DNS administrators require local administrator privileges to fix issues with the DNS server, but in order to do so you have to make them members of the highly privileged "Domain Admins" security group.</span></span>
<span data-ttu-id="0aad6-116">이 접근 방식을 통해 DNS 관리자는 효과적으로 전체 도메인을 제어하고 해당 컴퓨터의 모든 리소스에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0aad6-116">This approach effectively gives DNS Administrators control over your whole domain and access to all resources on that machine.</span></span>

<span data-ttu-id="0aad6-117">JEA는 *최소 권한* 원칙을 채택하는 데 도움을 제공하여 이 문제를 해결할 수 있게 해줍니다.</span><span class="sxs-lookup"><span data-stu-id="0aad6-117">JEA helps address this problem by helping you adopt the principle of *Least Privilege*.</span></span>
<span data-ttu-id="0aad6-118">JEA를 통해 작업을 수행하는 데 필요한 모든 PowerShell 명령에 대한 액세스 권한만 부여하는 관리 엔드포인트를 DNS 관리자에 대해 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0aad6-118">With JEA, you can configure a management endpoint for DNS administrators that gives them access to all the PowerShell commands they need to get their job done, but nothing more.</span></span>
<span data-ttu-id="0aad6-119">즉, 의도치 않게 Active Directory에 대한 권한이나 파일 시스템을 검색하거나 잠재적으로 위험한 스크립트를 실행할 수 있는 권한을 부여하는 일 없이 손상된 DNS 캐시를 복구하거나 DNS 서버를 다시 시작하는 데 적합한 액세스 권한을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0aad6-119">This means you can provide the appropriate access to repair a poisoned DNS cache or restart the DNS server without unintentionally giving them rights to Active Directory, or to browse the file system, or run potentially dangerous scripts.</span></span>
<span data-ttu-id="0aad6-120">더 좋은 점은 JEA 세션이 임시 권한 있는 가상 계정을 사용하도록 구성된 경우 DNS 관리자는 *관리자가 아닌 사용자* 자격 증명을 사용하여 서버에 연결하고 일반적으로 관리자 권한이 필요한 명령을 계속 실행할 수 있다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="0aad6-120">Better yet, when the JEA session is configured to use temporary privileged virtual accounts, your DNS administrators can connect to the server using *non-admin* credentials and still be able to run commands which typically require admin privileges.</span></span>
<span data-ttu-id="0aad6-121">이 기능을 사용하면 광범위한 권한이 있는 로컬/도메인 관리자 역할에서 사용자를 제거하고 대신 사용자가 각 컴퓨터에서 수행할 수 있는 작업을 신중하게 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0aad6-121">This capability enables you to remove users from widely-privileged local/domain administrator roles and instead carefully control what they are able to do on each machine.</span></span>

## <a name="get-started-with-jea"></a><span data-ttu-id="0aad6-122">JEA 시작</span><span class="sxs-lookup"><span data-stu-id="0aad6-122">Get Started with JEA</span></span>

<span data-ttu-id="0aad6-123">지금 Windows Server 2016 또는 Windows 10을 실행하는 모든 컴퓨터에서 JEA 사용을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0aad6-123">You can start using JEA today on any machine running Windows Server 2016 or Windows 10.</span></span>
<span data-ttu-id="0aad6-124">Windows Management Framework 업데이트가 설치된 이전 운영 체제에서도 JEA를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0aad6-124">You can also run JEA on older operating systems with a Windows Management Framework update.</span></span>
<span data-ttu-id="0aad6-125">JEA를 사용하기 위한 요구 사항에 대해 자세히 알아보고 JEA 엔드포인트를 만들고 사용하고 감사하는 방법을 알아보려면 다음 항목을 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="0aad6-125">To learn more about the requirements to use JEA and to learn how to create, use, and audit a JEA endpoint, check out the following topics:</span></span>

- <span data-ttu-id="0aad6-126">[필수 조건](prerequisites.md) - JEA를 사용하도록 환경을 설정하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="0aad6-126">[Prerequisites](prerequisites.md) - explains how to set up your environment to use JEA.</span></span>
- <span data-ttu-id="0aad6-127">[역할 기능](role-capabilities.md) - 사용자가 JEA 세션에서 수행할 수 있는 작업을 결정하는 역할을 만드는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="0aad6-127">[Role Capabilities](role-capabilities.md) - explains how to create roles which determine what a user is allowed to do in a JEA session.</span></span>
- <span data-ttu-id="0aad6-128">[세션 구성](session-configurations.md) - 사용자를 역할에 매핑하는 JEA 엔드포인트를 구성하고 JEA ID를 설정하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="0aad6-128">[Session Configurations](session-configurations.md) - explains how to configure JEA endpoints that map users to roles and set the JEA identity</span></span>
- <span data-ttu-id="0aad6-129">[JEA 등록](register-jea.md) - JEA 엔드포인트를 만들고 사용자가 연결하는 데 이러한 엔드포인트를 사용할 수 있게 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0aad6-129">[Registering JEA](register-jea.md) - create a JEA endpoint and make it available for users to connect to.</span></span>
- <span data-ttu-id="0aad6-130">[JEA 사용](using-jea.md) - JEA를 사용할 수 있는 다양한 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="0aad6-130">[Using JEA](using-jea.md) - learn the various ways you can use JEA.</span></span>
- <span data-ttu-id="0aad6-131">[보안 고려 사항](security-considerations.md) - 보안 모범 사례 및 JEA 구성 옵션의 의미를 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="0aad6-131">[Security Considerations](security-considerations.md) - review security best practices and implications of JEA configuration options.</span></span>
- <span data-ttu-id="0aad6-132">[JEA에 대한 감사 및 보고](audit-and-report.md) - JEA 엔드포인트에 대해 감사하고 보고하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="0aad6-132">[Audit and Report on JEA](audit-and-report.md) - learn how to audit and report on JEA endpoints.</span></span>

## <a name="samples-and-dsc-resource"></a><span data-ttu-id="0aad6-133">샘플 및 DSC 리소스</span><span class="sxs-lookup"><span data-stu-id="0aad6-133">Samples and DSC resource</span></span>

<span data-ttu-id="0aad6-134">샘플 JEA 구성 및 JEA DSC 리소스는 [JEA GitHub 리포지토리](https://github.com/PowerShell/JEA)에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0aad6-134">Sample JEA configurations and the JEA DSC resource can be found in the [JEA GitHub repository](https://github.com/PowerShell/JEA).</span></span>