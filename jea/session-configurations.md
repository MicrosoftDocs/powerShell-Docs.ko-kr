---
ms.date: 06/12/2017
keywords: jea,powershell,security
title: JEA 세션 구성
ms.openlocfilehash: 1b598522d43b2c1a26a739a67cee5181b21a7c32
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55683198"
---
# <a name="jea-session-configurations"></a><span data-ttu-id="9b984-103">JEA 세션 구성</span><span class="sxs-lookup"><span data-stu-id="9b984-103">JEA Session Configurations</span></span>

> <span data-ttu-id="9b984-104">적용 대상: Windows Powershell 5.0</span><span class="sxs-lookup"><span data-stu-id="9b984-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="9b984-105">JEA 엔드포인트는 특정한 방법으로 PowerShell 세션 구성 파일을 만들고 등록하여 시스템에 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-105">A JEA endpoint is registered on a system by creating and registering a PowerShell session configuration file in a specific way.</span></span>
<span data-ttu-id="9b984-106">세션 구성은 JEA 엔드포인트를 사용할 수 있는 *사용자* 및 해당 사용자가 액세스할 수 있는 역할을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-106">Session configurations determine *who* can use the JEA endpoint, and which role(s) they will have access to.</span></span>
<span data-ttu-id="9b984-107">또한 JEA 세션에서 모든 역할의 사용자에게 적용되는 전역 설정을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-107">They also define global settings that apply to users of any role in the JEA session.</span></span>

<span data-ttu-id="9b984-108">이 항목에서는 PowerShell 세션 구성 파일을 만들고 JEA 엔드포인트를 등록하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-108">This topic describes how to create a PowerShell session configuration file and register a JEA endpoint.</span></span>

## <a name="create-a-session-configuration-file"></a><span data-ttu-id="9b984-109">세션 구성 파일 만들기</span><span class="sxs-lookup"><span data-stu-id="9b984-109">Create a session configuration file</span></span>

<span data-ttu-id="9b984-110">JEA 엔드포인트를 등록하려면 해당 엔드포인트가 구성되는 방법을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-110">In order to register a JEA endpoint, you need to specify how that endpoint should be configured.</span></span>
<span data-ttu-id="9b984-111">여기서 고려해야 할 옵션은 많지만, 그중 가장 중요한 옵션은 JEA 엔드포인트에 대한 액세스 권한을 가져야 하는 사용자, 해당 사용자에게 할당할 역할, JEA를 사용할 ID 및 JEA 엔드포인트의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-111">There are many options to consider here, the most important of which being who should have access to the JEA endpoint, which roles will they be assigned, which identity will JEA use under the covers, and what will be the name of the JEA endpoint.</span></span>
<span data-ttu-id="9b984-112">이러한 내용은 모두 PowerShell 세션 구성 파일(확장명 .pssc로 끝나는 PowerShell 데이터 파일)에 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-112">These are all defined in a PowerShell session configuration file, which is a PowerShell data file ending with a .pssc extension.</span></span>

<span data-ttu-id="9b984-113">JEA 엔드포인트에 대한 기본 세션 구성 파일을 만들려면 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-113">To create a skeleton session configuration file for JEA endpoints, run the following command.</span></span>

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\MyJEAEndpoint.pssc
```

> [!TIP]
> <span data-ttu-id="9b984-114">가장 일반적인 구성 옵션만 기본 파일에 기본적으로 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-114">Only the most common configuration options are included in the skeleton file by default.</span></span>
> <span data-ttu-id="9b984-115">생성된 PSSC에 적용 가능한 모든 설정을 포함하려면 `-Full` 스위치를 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="9b984-115">Use the `-Full` switch to include all applicable settings in the generated PSSC.</span></span>

<span data-ttu-id="9b984-116">세션 구성 파일은 모든 텍스트 편집기에서 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-116">You can open the session configuration file in any text editor.</span></span>
<span data-ttu-id="9b984-117">`-SessionType RestrictedRemoteServer` 필드는 세션 구성이 안전한 관리를 위해 JEA에서 사용됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-117">The `-SessionType RestrictedRemoteServer` field indicates that the session configuration will be used by JEA for secure management.</span></span>
<span data-ttu-id="9b984-118">이 방법으로 구성된 세션은 [NoLanguage 모드](https://technet.microsoft.com/library/dn433292.aspx)에서 작동하며 다음과 같은 8가지 기본 명령(및 별칭)만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-118">Sessions configured this way will operate in [NoLanguage mode](https://technet.microsoft.com/library/dn433292.aspx) and only have the following 8 default commands (and aliases) available:</span></span>

- <span data-ttu-id="9b984-119">Clear-Host(cls, clear)</span><span class="sxs-lookup"><span data-stu-id="9b984-119">Clear-Host (cls, clear)</span></span>
- <span data-ttu-id="9b984-120">Exit-PSSession(exsn, exit)</span><span class="sxs-lookup"><span data-stu-id="9b984-120">Exit-PSSession (exsn, exit)</span></span>
- <span data-ttu-id="9b984-121">Get-Command(gcm)</span><span class="sxs-lookup"><span data-stu-id="9b984-121">Get-Command (gcm)</span></span>
- <span data-ttu-id="9b984-122">Get-FormatData</span><span class="sxs-lookup"><span data-stu-id="9b984-122">Get-FormatData</span></span>
- <span data-ttu-id="9b984-123">Get-Help</span><span class="sxs-lookup"><span data-stu-id="9b984-123">Get-Help</span></span>
- <span data-ttu-id="9b984-124">Measure-Object(measure)</span><span class="sxs-lookup"><span data-stu-id="9b984-124">Measure-Object (measure)</span></span>
- <span data-ttu-id="9b984-125">Out-Default</span><span class="sxs-lookup"><span data-stu-id="9b984-125">Out-Default</span></span>
- <span data-ttu-id="9b984-126">Select-Object(select)</span><span class="sxs-lookup"><span data-stu-id="9b984-126">Select-Object (select)</span></span>

<span data-ttu-id="9b984-127">PowerShell 공급자와 외부 프로그램(실행 파일, 스크립트 등)은 모두 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-127">No PowerShell providers are available, nor are any external programs (executables, scripts, etc.).</span></span>

<span data-ttu-id="9b984-128">JEA 세션에 대해 구성할 다른 여러 가지 필드도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-128">There are several other fields you will want to configure for the JEA session.</span></span>
<span data-ttu-id="9b984-129">이러한 필드는 다음 섹션에 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-129">They are covered in the following sections.</span></span>

### <a name="choose-the-jea-identity"></a><span data-ttu-id="9b984-130">JEA ID 선택</span><span class="sxs-lookup"><span data-stu-id="9b984-130">Choose the JEA identity</span></span>

<span data-ttu-id="9b984-131">백그라운드에서 JEA에는 연결된 사용자의 명령을 실행할 때 사용할 ID(계정)가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-131">Behind the scenes, JEA needs an identity (account) to use when running a connected user's commands.</span></span>
<span data-ttu-id="9b984-132">세션 구성 파일에서 JEA가 사용할 ID를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-132">You decide which identity JEA will use in the session configuration file.</span></span>

#### <a name="local-virtual-account"></a><span data-ttu-id="9b984-133">로컬 가상 계정</span><span class="sxs-lookup"><span data-stu-id="9b984-133">Local Virtual Account</span></span>

<span data-ttu-id="9b984-134">이 JEA 엔드포인트에서 지원하는 역할이 모두 로컬 컴퓨터를 관리하는 데 사용되고 명령을 실행하는 데 로컬 관리자 계정으로 충분하다면 로컬 가상 계정을 사용하도록 JEA를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-134">If the roles supported by this JEA endpoint are all used to manage the local machine, and a local administrator account is sufficient to run the commands succesfully, you should configure JEA to use a local virtual account.</span></span>
<span data-ttu-id="9b984-135">가상 계정은 특정 사용자에게 고유하고 해당 PowerShell 세션 기간 동안만 지속하는 임시 계정입니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-135">Virtual accounts are temporary accounts that are unique to a specific user and only last for the duration of their PowerShell session.</span></span>
<span data-ttu-id="9b984-136">구성원 서버 또는 워크스테이션에서 가상 계정은 로컬 컴퓨터의 **Administrators** 그룹에 속하고 대부분의 시스템 리소스에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-136">On a member server or workstation, virtual accounts belong to the local computer's **Administrators** group, and have access to most system resources.</span></span>
<span data-ttu-id="9b984-137">Active Directory 도메인 컨트롤러에서 가상 계정은 도메인의 **Domain Admins** 그룹에 속합니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-137">On an Active Directory Domain Controller, virtual accounts belong to the domain's **Domain Admins** group.</span></span>

```powershell
# Setting the session to use a virtual account
RunAsVirtualAccount = $true
```

<span data-ttu-id="9b984-138">세션 구성에서 지원하는 역할에 광범위한 권한이 필요하지 않으면 필요에 따라 가상 계정이 속할 보안 그룹을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-138">If the roles supported by the session configuration do not require such broad privileges, you can optionally specify the security groups to which the virtual account will belong.</span></span>
<span data-ttu-id="9b984-139">구성원 서버 또는 워크스테이션에서 지정된 보안 그룹은 도메인의 그룹이 아니라 로컬 그룹이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-139">On a member server or workstation, the specified security groups must be local groups, not groups from a domain.</span></span>

<span data-ttu-id="9b984-140">하나 이상의 보안 그룹을 지정한 경우 가상 계정은 더 이상 로컬 또는 도메인 관리자 그룹에 속하지 않게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-140">When one or more security groups is specified, the virtual account will no longer belong to the local or domain administrators group.</span></span>

```powershell
# Setting the session to use a virtual account that only belongs to the NetworkOperator and NetworkAuditor local groups
RunAsVirtualAccount = $true
RunAsVirtualAccountGroups = 'NetworkOperator', 'NetworkAuditor'
```
> [!NOTE]
> <span data-ttu-id="9b984-141">일시적으로 가상 계정은 로컬 서버 보안 정책에서 서비스 권한 로그온을 부여 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-141">Virtual accounts are temporarily granted the Logon as a service right in the local server security policy.</span></span>  <span data-ttu-id="9b984-142">지정한 VirtualAccountGroups 중 하나가 이미 부여 된 경우 정책에서이 권한을, 개별 가상 계정은 더 이상 추가 되며 정책에서 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-142">If one of the VirtualAccountGroups specified has already been granted this right in the policy, the individual virtual account will no longer be added and removed from the policy.</span></span>  <span data-ttu-id="9b984-143">이 도메인 컨트롤러 보안 정책에 대 한 수정 버전 감사 밀접 하 게 되는 도메인 컨트롤러와 같은 시나리오에서 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-143">This can be useful in scenarios such as domain controllers where revisions to the domain controller security policy are closely audited.</span></span>  <span data-ttu-id="9b984-144">2018 년 11 월을 사용 하 여 Windows Server 2016 또는 이후 롤업 및 Windows Server 2019 년 1 월 2019를 사용 하 여 최신 롤업을 제공만 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-144">This is only available in Windows Server 2016 with the November 2018 or later rollup and Windows Server 2019 with the January 2019 or later rollup.</span></span>

#### <a name="group-managed-service-account"></a><span data-ttu-id="9b984-145">그룹 관리 서비스 계정</span><span class="sxs-lookup"><span data-stu-id="9b984-145">Group Managed Service Account</span></span>


<span data-ttu-id="9b984-146">JEA 사용자가 다른 컴퓨터 또는 웹 서비스와 같은 네트워크 리소스에 액세스해야 하는 시나리오의 경우 gMSA(그룹 관리 서비스 계정)가 사용하기 더 적합한 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-146">For scenarios requiring the JEA user to access network resources such as other machines or web services, a group managed service account (gMSA) is a more appropriate identity to use.</span></span>
<span data-ttu-id="9b984-147">gMSA 계정은 도메인 내의 모든 컴퓨터에 있는 리소스에 대해 인증하는 데 사용할 수 있는 도메인 ID를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-147">gMSA accounts give you a domain identity which can be used to authenticate against resources on any machine within the domain.</span></span>
<span data-ttu-id="9b984-148">gMSA 계정이 제공하는 권한은 액세스하는 리소스에 의해 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-148">The rights the gMSA account gives you is determined by the resources you are accessing.</span></span>
<span data-ttu-id="9b984-149">컴퓨터/서비스 관리자가 명시적으로 gMSA 계정 관리자 권한을 부여하지 않은 한, 자동으로 컴퓨터 또는 서비스에 대한 관리자 권한이 부여되지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-149">You will not automatically have admin rights on any machines or services unless the machine/service administrator has explicitly granted the gMSA account admin privileges.</span></span>

```powershell
# Configure JEA sessions to use the gMSA account in the local computer's domain with the sAMAccountName of 'MyJEAgMSA'
GroupManagedServiceAccount = 'Domain\MyJEAgMSA'
```

<span data-ttu-id="9b984-150">gMSA 계정은 다음과 같은 몇 가지 이유로 네트워크 리소스에 액세스해야 하는 경우에만 사용되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-150">gMSA accounts should only be used when access to network resources are required for a few reasons:</span></span>

- <span data-ttu-id="9b984-151">모든 사용자가 같은 실행 ID를 공유하므로 gMSA 계정을 사용할 경우 사용자까지 거슬러 올라가 작업을 추적하기가 어렵습니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-151">It is harder to trace back actions to a user when using a gMSA account since every user shares the same run-as identity.</span></span> <span data-ttu-id="9b984-152">PowerShell 세션 기록 및 로그를 확인하여 사용자와 해당 작업의 상관 관계를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-152">You will need to consult PowerShell session transcripts and logs to correlate users with their actions.</span></span>

- <span data-ttu-id="9b984-153">gMSA 계정은 연결하는 사용자가 액세스할 필요가 없는 많은 네트워크 리소스에 대한 액세스 권한을 가질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-153">The gMSA account may have access to many network resources which the connecting user does not need access to.</span></span> <span data-ttu-id="9b984-154">항상 JEA 세션에서 유효 권한을 제한하여 최소 권한 원칙을 따르도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-154">Always try to limit effective permissions in a JEA session to follow the principle of least privilege.</span></span>

> [!NOTE]
> <span data-ttu-id="9b984-155">그룹 관리 서비스 계정은 Windows PowerShell 5.1 이상 및 도메인에 가입된 컴퓨터에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-155">Group managed service accounts are only available in Windows PowerShell 5.1 or newer and on domain-joined machines.</span></span>


#### <a name="more-information-about-run-as-users"></a><span data-ttu-id="9b984-156">실행 사용자에 대한 자세한 내용</span><span class="sxs-lookup"><span data-stu-id="9b984-156">More information about run as users</span></span>

<span data-ttu-id="9b984-157">실행 ID 및 실행 ID가 JEA 세션의 보안에 어떤 영향을 주는지에 대한 자세한 내용은 [보안 고려 사항](security-considerations.md) 문서에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-157">Additional information about run as identities and how they factor into the security of a JEA session can be found in the [security considerations](security-considerations.md) article.</span></span>

### <a name="session-transcripts"></a><span data-ttu-id="9b984-158">세션 기록</span><span class="sxs-lookup"><span data-stu-id="9b984-158">Session transcripts</span></span>

<span data-ttu-id="9b984-159">사용자의 세션 기록을 자동으로 기록하려면 JEA 세션 구성 파일을 구성하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-159">It is recommended that you configure a JEA session configuration file to automatically record transcripts of users' sessions.</span></span>
<span data-ttu-id="9b984-160">PowerShell 세션 기록은 연결하는 사용자, 사용자에게 할당된 실행 ID 및 사용자가 실행한 명령에 대한 정보를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-160">PowerShell session transcripts contain information about the connecting user, the run as identity assigned to them, and the commands run by the user.</span></span>
<span data-ttu-id="9b984-161">이러한 기록은 시스템에 대한 특정 변경 내용을 수행한 사용자를 파악해야 하는 감사 팀에 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-161">They can be useful to an auditing team who needs to understand who performed a specific change to a system.</span></span>

<span data-ttu-id="9b984-162">세션 구성 파일에서 자동 기록을 구성하려면 기록이 저장되는 폴더의 경로를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-162">To configure automatic transcription in the session configuration file, provide a path to a folder where the transcripts should be stored.</span></span>

```powershell
TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
```

<span data-ttu-id="9b984-163">지정된 폴더는 사용자가 폴더 내의 데이터를 수정하거나 삭제하지 못하도록 구성되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-163">The specified folder should be configured to prevent users from modifying or deleting any data in it.</span></span>
<span data-ttu-id="9b984-164">기록은 디렉터리에 대한 읽기 및 쓰기 권한이 필요한 로컬 시스템 계정에 의해 폴더에 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-164">Transcripts are written to the folder by the Local System account, which requires read and write access to the directory.</span></span>
<span data-ttu-id="9b984-165">표준 사용자는 폴더에 대한 액세스 권한이 없어야 하고, 제한된 보안 관리자 집합은 기록을 감사하기 위한 액세스 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-165">Standard users should have no access to the folder, and a limited set of security administrators should have access to audit the transcripts.</span></span>

### <a name="user-drive"></a><span data-ttu-id="9b984-166">사용자 드라이브</span><span class="sxs-lookup"><span data-stu-id="9b984-166">User drive</span></span>

<span data-ttu-id="9b984-167">연결하는 사용자가 명령을 실행하기 위해 JEA 엔드포인트로/에서 파일을 복사해야 할 경우 세션 구성 파일에서 사용자 드라이브를 사용하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-167">If your connecting users will need to copy files to/from the JEA endpoint in order to run a command, you can enable the user drive in the session configuration file.</span></span>
<span data-ttu-id="9b984-168">사용자 드라이브는 각 연결하는 사용자에 대해 고유한 폴더에 매핑되는 [PSDrive](https://msdn.microsoft.com/powershell/scripting/getting-started/cookbooks/managing-windows-powershell-drives)입니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-168">The user drive is a [PSDrive](https://msdn.microsoft.com/powershell/scripting/getting-started/cookbooks/managing-windows-powershell-drives) that is mapped to a unique folder for each connecting user.</span></span>
<span data-ttu-id="9b984-169">이 폴더는 전체 파일 시스템에 대한 액세스 권한을 제공하거나 FileSystem 공급자를 노출하지 않고 각 연결하는 사용자가 시스템으로/에서 파일을 복사할 수 있는 공간 역할을 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-169">This folder serves as a space for them to copy files to/from the system, without giving them access to the full file system or exposing the FileSystem provider.</span></span>
<span data-ttu-id="9b984-170">사용자 드라이브 콘텐츠는 세션 전체에서 유지되어 네트워크 연결이 중단될 수 있는 상황을 수용합니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-170">The user drive contents are persistent across sessions to accommodate situations where network connectivity may be interrupted.</span></span>

```powershell
MountUserDrive = $true
```

<span data-ttu-id="9b984-171">기본적으로 사용자 드라이브를 사용하여 사용자당 최대 50MB의 데이터를 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-171">By default, the user drive allows you to store a maximum of 50MB of data per user.</span></span>
<span data-ttu-id="9b984-172">*UserDriveMaximumSize* 필드를 사용하여 사용자가 사용할 수 있는 데이터의 양을 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-172">You can limit the amount of data a user can consume with the *UserDriveMaximumSize* field.</span></span>

```powershell
# Enables the user drive with a per-user limit of 500MB (524288000 bytes)
MountUserDrive = $true
UserDriveMaximumSize = 524288000
```

<span data-ttu-id="9b984-173">사용자 드라이브의 데이터가 유지되지 않게 하려는 경우 매일 밤 자동으로 폴더를 정리하도록 시스템에 대한 예약된 작업을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-173">If you do not want data in the user drive to be persistent, you can configure a scheduled task on the system to automatically clean up the folder every night.</span></span>

> [!NOTE]
> <span data-ttu-id="9b984-174">사용자 드라이브는 Windows PowerShell 5.1 이상에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-174">The user drive is only available in Windows PowerShell 5.1 or newer.</span></span>

### <a name="role-definitions"></a><span data-ttu-id="9b984-175">역할 정의</span><span class="sxs-lookup"><span data-stu-id="9b984-175">Role definitions</span></span>

<span data-ttu-id="9b984-176">세션 구성 파일의 역할 정의는 *역할*에 대한 *사용자*의 매핑을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-176">Role definitions in a session configuration file define the mapping of *users* to *roles*.</span></span>
<span data-ttu-id="9b984-177">JEA 엔드포인트가 등록되면 이 필드에 포함된 모든 사용자 또는 그룹에 자동으로 해당 JEA 엔드포인트에 대한 사용 권한이 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-177">Every user or group included in this field will automatically be granted permission to the JEA endpoint when it is registered.</span></span>
<span data-ttu-id="9b984-178">각 사용자 또는 그룹은 해시 테이블의 키로 한 번만 포함될 수 있지만, 역할은 여러 개가 할당될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-178">Each user or group can be included as a key in the hashtable only once, but can be assigned multiple roles.</span></span>
<span data-ttu-id="9b984-179">역할 기능의 이름은 .psrc 확장명이 없는 역할 기능 파일의 이름이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-179">The name of the role capability should be the name of the role capability file, without the .psrc extension.</span></span>

```powershell
RoleDefinitions = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}
```

<span data-ttu-id="9b984-180">사용자가 역할 정의에서 둘 이상의 그룹에 속하는 경우 각 역할에 대한 액세스 권한을 얻게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-180">If a user belongs to more than one group in the role definition, they will get access to the roles of each.</span></span>
<span data-ttu-id="9b984-181">두 역할이 같은 cmdlet에 대한 액세스 권한을 부여하는 경우 사용자에게 최대로 허용되는 매개 변수 집합이 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-181">If two roles grant access to the same cmdlets, the most permissive parameter set will be granted to the user.</span></span>

<span data-ttu-id="9b984-182">역할 정의 필드에서 로컬 사용자 또는 그룹을 지정할 경우 백슬래시 앞에 컴퓨터 이름을 사용해야 합니다(*localhost* 또는 *.* 제외).</span><span class="sxs-lookup"><span data-stu-id="9b984-182">When specifying local users or groups in the role definitions field, be sure to use the computer name (not *localhost* or *.*) before the backslash.</span></span>
<span data-ttu-id="9b984-183">`$env:computername` 변수를 검사하여 컴퓨터 이름을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-183">You can check the computer name by inspecting the `$env:computername` variable.</span></span>

```powershell
RoleDefinitions = @{
    'MyComputerName\MyLocalGroup' = @{ RoleCapabilities = 'DnsAuditor' }
}
```

### <a name="role-capability-search-order"></a><span data-ttu-id="9b984-184">역할 기능 검색 순서</span><span class="sxs-lookup"><span data-stu-id="9b984-184">Role capability search order</span></span>
<span data-ttu-id="9b984-185">위의 예제에 표시된 것처럼 역할 기능은 역할 기능 파일의 일반 이름(확장명이 없는 파일 이름)으로 참조됩니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-185">As shown in the example above, role capabilities are referenced by the flat name (filename without the extension) of the role capability file.</span></span>
<span data-ttu-id="9b984-186">시스템에서 일반 이름이 같은 역할 기능을 여러 개 사용할 수 있는 경우 PowerShell에서는 암시적 검색 순서를 사용하여 유효 역할 기능 파일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-186">If multiple role capabilities are available on the system with the same flat name, PowerShell will use its implicit search order to select the effective role capability file.</span></span>
<span data-ttu-id="9b984-187">이름이 같은 모든 역할 기능 파일에 대한 액세스 권한을 부여하지는 **않습니다**.</span><span class="sxs-lookup"><span data-stu-id="9b984-187">It will **not** give access to all role capability files with the same name.</span></span>

<span data-ttu-id="9b984-188">JEA에서는 `$env:PSModulePath` 환경 변수를 사용하여 역할 기능 파일을 검색할 경로를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-188">JEA uses the `$env:PSModulePath` environment variable to determine which paths to scan for role capability files.</span></span>
<span data-ttu-id="9b984-189">JEA는 이러한 경로 각각에서 "RoleCapabilities" 하위 폴더가 포함된 유효한 PowerShell 모듈을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-189">Within each of those paths, JEA will look for valid PowerShell modules that contain a "RoleCapabilities" subfolder.</span></span>
<span data-ttu-id="9b984-190">모듈을 가져오는 경우와 마찬가지로, JEA는 같은 이름의 사용자 지정 역할 기능보다 Windows와 함께 제공되는 역할 기능을 선호합니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-190">As with importing modules, JEA prefers role capabilities that are shipped with Windows to custom role capabilities with the same name.</span></span>
<span data-ttu-id="9b984-191">명명에 관한 다른 모든 충돌의 경우는 Windows에서 디렉터리의 파일을 열거하는 순서에 따라 우선순위가 결정됩니다(사전 순이 아닐 수 있음).</span><span class="sxs-lookup"><span data-stu-id="9b984-191">For all other naming conflicts, precedence is determined by the order in which Windows enumerates the files in the directory (not guaranteed to be alphabetically).</span></span>
<span data-ttu-id="9b984-192">원하는 이름과 일치하는 첫 번째 역할 기능으로 검색된 것이 연결 사용자에게 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-192">The first role capability file found that matches the desired name will be used for the connecting user.</span></span>

<span data-ttu-id="9b984-193">같은 이름의 역할 기능이 두 개 이상 있는 경우 역할 기능의 검색 순서를 장담할 수 없으므로, 컴퓨터에서 역할 기능의 이름이 고유한지 확인할 것을 **강력하게 권장합니다**.</span><span class="sxs-lookup"><span data-stu-id="9b984-193">Since the role capability search order is not deterministic when two or more role capabilities share the same name, it is **strongly recommended** that you ensure role capabilities have unique names on your machine.</span></span>

### <a name="conditional-access-rules"></a><span data-ttu-id="9b984-194">조건부 액세스 규칙</span><span class="sxs-lookup"><span data-stu-id="9b984-194">Conditional access rules</span></span>

<span data-ttu-id="9b984-195">RoleDefinitions 필드에 포함된 모든 사용자 및 그룹에는 자동으로 JEA 엔드포인트에 대한 액세스 권한이 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-195">All users and groups included in the RoleDefinitions field are automatically granted access to JEA endpoints.</span></span>
<span data-ttu-id="9b984-196">조건부 액세스 규칙을 사용하여 이 액세스 권한을 구체화하고 사용자가 사용자에게 할당된 역할에 영향을 주지 않는 추가 보안 그룹에 속해야 하도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-196">Conditional access rules allow you to refine this access and require users to belong to additional security groups which do not impact the roles which they are assigned.</span></span>
<span data-ttu-id="9b984-197">이 기능은 "Just In Time" 권한 있는 액세스 권한 관리 솔루션, 스마트 카드 인증 또는 다른 다단계 인증 솔루션을 JEA와 통합하려는 경우 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-197">This can be useful if you want to integrate a "just in time" privileged access management solution, smartcard authentication, or other multifactor authentication solution with JEA.</span></span>

<span data-ttu-id="9b984-198">조건부 액세스 규칙은 세션 구성 파일에서 RequiredGroups 필드에 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-198">Conditional access rules are defined in the RequiredGroups field in a session configuration file.</span></span>
<span data-ttu-id="9b984-199">여기서 'And' 및 'Or' 키를 사용하여 규칙을 구성하는 해시 테이블(필요에 따라 중첩됨)을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-199">There, you can provide a hashtable (optionally nested) that uses 'And' and 'Or' keys to construct your rules.</span></span>
<span data-ttu-id="9b984-200">다음은 이 필드를 사용하는 방법의 몇 가지 예입니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-200">Here are some examples of how to leverage this field:</span></span>

```powershell
# Example 1: Connecting users must belong to a security group called "elevated-jea"
RequiredGroups = @{ And = 'elevated-jea' }

# Example 2: Connecting users must have signed on with 2 factor authentication or a smart card
# The 2 factor authentication group name is "2FA-logon" and the smart card group name is "smartcard-logon"
RequiredGroups = @{ Or = '2FA-logon', 'smartcard-logon' }

# Example 3: Connecting users must elevate into "elevated-jea" with their JIT system and have logged on with 2FA or a smart card
RequiredGroups = @{ And = 'elevated-jea', @{ Or = '2FA-logon', 'smartcard-logon' }}
```

> [!NOTE]
> <span data-ttu-id="9b984-201">조건부 액세스 규칙은 Windows PowerShell 5.1 이상에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-201">Conditional access rules are only available in Windows PowerShell 5.1 or newer.</span></span>

### <a name="other-properties"></a><span data-ttu-id="9b984-202">기타 속성</span><span class="sxs-lookup"><span data-stu-id="9b984-202">Other properties</span></span>
<span data-ttu-id="9b984-203">세션 구성 파일도 역할 기능 파일이 수행할 수 있는 모든 작업을 수행할 수 있지만, 연결하는 사용자에게 다른 명령에 대한 액세스 권한을 부여하는 기능은 제외됩니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-203">Session configuration files can also do everything a role capability file can do, just without the ability to give connecting users access to different commands.</span></span>
<span data-ttu-id="9b984-204">모든 사용자가 특정 cmdlet, 함수 또는 공급자에 액세스할 수 있게 하려는 경우 세션 구성 파일에서 직접 이렇게 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-204">If you want to allow all users access to specific cmdlets, functions, or providers, you can do so right in the session configuration file.</span></span>
<span data-ttu-id="9b984-205">세션 구성 파일에서 지원되는 속성의 전체 목록을 보려면 `Get-Help New-PSSessionConfigurationFile -Full`을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-205">For a full list of supported properties in the session configuration file, run `Get-Help New-PSSessionConfigurationFile -Full`.</span></span>

## <a name="testing-a-session-configuration-file"></a><span data-ttu-id="9b984-206">세션 구성 파일 테스트</span><span class="sxs-lookup"><span data-stu-id="9b984-206">Testing a session configuration file</span></span>

<span data-ttu-id="9b984-207">[Test-PSSessionConfigurationFile](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/test-pssessionconfigurationfile) cmdlet을 사용하여 세션 구성 파일을 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-207">You can test a session configuration using the [Test-PSSessionConfigurationFile](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/test-pssessionconfigurationfile) cmdlet.</span></span>
<span data-ttu-id="9b984-208">구문이 올바른지 확인하기 위해 텍스트 편집기를 사용하여 수동으로 pssc 파일을 편집한 경우 세션 구성 파일을 테스트하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-208">It is strongly recommended that you test your session configuration file if you have edited the pssc file manually using a text editor to ensure the syntax is correct.</span></span>
<span data-ttu-id="9b984-209">세션 구성 파일이 이 테스트를 통과하지 못하면 시스템에 등록될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-209">If a session configuration file does not pass this test, it will not be able to be successfully registered on the system.</span></span>

## <a name="sample-session-configuration-file"></a><span data-ttu-id="9b984-210">샘플 세션 구성 파일</span><span class="sxs-lookup"><span data-stu-id="9b984-210">Sample session configuration file</span></span>

<span data-ttu-id="9b984-211">다음은 JEA에 대한 세션 구성을 만들고 유효성을 검사하는 방법을 보여 주는 전체 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-211">Below is a complete example showing how to create and validate a session configuration for JEA.</span></span>
<span data-ttu-id="9b984-212">역할 정의는 편의성과 가독성을 위해 생성되어 `$roles` 변수에 저장되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-212">Note that the role definitions are created and stored in the `$roles` variable for convenience and readability.</span></span>
<span data-ttu-id="9b984-213">이는 작업을 수행하기 위한 요구 사항은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-213">It is not a requirement to do so.</span></span>

```powershell
$roles = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}

New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\JEAConfig.pssc -RunAsVirtualAccount -TranscriptDirectory 'C:\ProgramData\JEAConfiguration\Transcripts' -RoleDefinitions $roles -RequiredGroups @{ Or = '2FA-logon', 'smartcard-logon' }
Test-PSSessionConfigurationFile -Path .\JEAConfig.pssc # should yield True
```

## <a name="updating-session-configuration-files"></a><span data-ttu-id="9b984-214">세션 구성 파일 업데이트</span><span class="sxs-lookup"><span data-stu-id="9b984-214">Updating session configuration files</span></span>

<span data-ttu-id="9b984-215">역할에 대한 사용자의 매핑을 비롯한 JEA 세션 구성의 속성을 변경해야 하는 경우 JEA 세션 구성을 [등록 취소](register-jea.md#unregistering-jea-configurations)한 후 [다시 등록](register-jea.md)해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-215">If you need to change properties of a JEA session configuration, including the mapping of users to roles, you must [unregister](register-jea.md#unregistering-jea-configurations) and [re-register](register-jea.md) the JEA session configuration.</span></span>
<span data-ttu-id="9b984-216">JEA 세션 구성을 다시 등록할 때 원하는 변경 내용을 포함하는 업데이트된 PowerShell 세션 구성 파일을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9b984-216">When you re-register the JEA session configuration, use an updated PowerShell session configuration file that includes your desired changes.</span></span>

## <a name="next-steps"></a><span data-ttu-id="9b984-217">다음 단계</span><span class="sxs-lookup"><span data-stu-id="9b984-217">Next steps</span></span>

- [<span data-ttu-id="9b984-218">JEA 구성 등록</span><span class="sxs-lookup"><span data-stu-id="9b984-218">Register a JEA configuration</span></span>](register-jea.md)
- [<span data-ttu-id="9b984-219">JEA 역할 작성</span><span class="sxs-lookup"><span data-stu-id="9b984-219">Author JEA roles</span></span>](role-capabilities.md)
