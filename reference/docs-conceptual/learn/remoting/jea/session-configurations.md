---
ms.date: 07/10/2019
keywords: jea,powershell,security
title: JEA 세션 구성
description: 세션 구성은 JEA 엔드포인트를 사용할 수 있는 사용자 및 해당 사용자가 액세스할 수 있는 역할을 정의합니다.
ms.openlocfilehash: b616d5bf260bbdfe89b6422fd4a8b4866f7fdc67
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/24/2020
ms.locfileid: "92501561"
---
# <a name="jea-session-configurations"></a><span data-ttu-id="f5e0e-104">JEA 세션 구성</span><span class="sxs-lookup"><span data-stu-id="f5e0e-104">JEA Session Configurations</span></span>

<span data-ttu-id="f5e0e-105">JEA 엔드포인트는 PowerShell 세션 구성 파일을 만들고 등록하여 시스템에 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-105">A JEA endpoint is registered on a system by creating and registering a PowerShell session configuration file.</span></span> <span data-ttu-id="f5e0e-106">세션 구성은 JEA 엔드포인트를 사용할 수 있는 사용자 및 해당 사용자가 액세스할 수 있는 역할을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-106">Session configurations define who can use the JEA endpoint and which roles they have access to.</span></span> <span data-ttu-id="f5e0e-107">또한 JEA 세션의 모든 사용자에게 적용되는 글로벌 설정을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-107">They also define global settings that apply to all users of the JEA session.</span></span>

## <a name="create-a-session-configuration-file"></a><span data-ttu-id="f5e0e-108">세션 구성 파일 만들기</span><span class="sxs-lookup"><span data-stu-id="f5e0e-108">Create a session configuration file</span></span>

<span data-ttu-id="f5e0e-109">JEA 엔드포인트를 등록하려면 해당 엔드포인트가 구성되는 방법을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-109">To register a JEA endpoint, you must specify how that endpoint is configured.</span></span> <span data-ttu-id="f5e0e-110">고려해야 할 많은 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-110">There are many options to consider.</span></span> <span data-ttu-id="f5e0e-111">가장 중요한 옵션은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-111">The most important options are:</span></span>

- <span data-ttu-id="f5e0e-112">JEA 엔드포인트에 액세스할 수 있는 사용자</span><span class="sxs-lookup"><span data-stu-id="f5e0e-112">Who has access to the JEA endpoint</span></span>
- <span data-ttu-id="f5e0e-113">할당된 역할</span><span class="sxs-lookup"><span data-stu-id="f5e0e-113">Which roles they be assigned</span></span>
- <span data-ttu-id="f5e0e-114">JEA가 내부적으로 사용하는 ID</span><span class="sxs-lookup"><span data-stu-id="f5e0e-114">Which identity JEA uses under the covers</span></span>
- <span data-ttu-id="f5e0e-115">JEA 엔드포인트의 이름</span><span class="sxs-lookup"><span data-stu-id="f5e0e-115">The name of the JEA endpoint</span></span>

<span data-ttu-id="f5e0e-116">이러한 옵션은 PowerShell 세션 구성 파일로 알려진 확장명이 `.pssc`인 PowerShell 데이터 파일에 정의되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-116">These options are defined in a PowerShell data file with a `.pssc` extension known as a PowerShell session configuration file.</span></span> <span data-ttu-id="f5e0e-117">세션 구성 파일은 임의의 텍스트 편집기를 사용하여 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-117">The session configuration file can be edited using any text editor.</span></span>

<span data-ttu-id="f5e0e-118">다음 명령을 실행하여 빈 템플릿 구성 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-118">Run the following command to create a blank template configuration file.</span></span>

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\MyJEAEndpoint.pssc
```

> [!TIP]
> <span data-ttu-id="f5e0e-119">템플릿 파일에는 기본적으로 가장 일반적인 구성 옵션만 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-119">Only the most common configuration options are included in the template file by default.</span></span> <span data-ttu-id="f5e0e-120">생성된 PSSC에 적용 가능한 모든 설정을 포함하려면 `-Full` 스위치를 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-120">Use the `-Full` switch to include all applicable settings in the generated PSSC.</span></span>

<span data-ttu-id="f5e0e-121">`-SessionType RestrictedRemoteServer` 필드는 세션 구성이 보안 관리를 위해 JEA에서 사용됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-121">The `-SessionType RestrictedRemoteServer` field indicates that the session configuration is used by JEA for secure management.</span></span> <span data-ttu-id="f5e0e-122">이 유형의 세션은 **NoLanguage** 모드에서 작동하며 다음과 같은 기본 명령(및 별칭)에만 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-122">Sessions of this type operate in **NoLanguage** mode and only have access to the following default commands (and aliases):</span></span>

- <span data-ttu-id="f5e0e-123">Clear-Host(cls, clear)</span><span class="sxs-lookup"><span data-stu-id="f5e0e-123">Clear-Host (cls, clear)</span></span>
- <span data-ttu-id="f5e0e-124">Exit-PSSession(exsn, exit)</span><span class="sxs-lookup"><span data-stu-id="f5e0e-124">Exit-PSSession (exsn, exit)</span></span>
- <span data-ttu-id="f5e0e-125">Get-Command(gcm)</span><span class="sxs-lookup"><span data-stu-id="f5e0e-125">Get-Command (gcm)</span></span>
- <span data-ttu-id="f5e0e-126">Get-FormatData</span><span class="sxs-lookup"><span data-stu-id="f5e0e-126">Get-FormatData</span></span>
- <span data-ttu-id="f5e0e-127">Get-Help</span><span class="sxs-lookup"><span data-stu-id="f5e0e-127">Get-Help</span></span>
- <span data-ttu-id="f5e0e-128">Measure-Object(measure)</span><span class="sxs-lookup"><span data-stu-id="f5e0e-128">Measure-Object (measure)</span></span>
- <span data-ttu-id="f5e0e-129">Out-Default</span><span class="sxs-lookup"><span data-stu-id="f5e0e-129">Out-Default</span></span>
- <span data-ttu-id="f5e0e-130">Select-Object(select)</span><span class="sxs-lookup"><span data-stu-id="f5e0e-130">Select-Object (select)</span></span>

<span data-ttu-id="f5e0e-131">PowerShell 공급자와 외부 프로그램(실행 파일 또는 스크립트)은 모두 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-131">No PowerShell providers are available, nor are any external programs (executables or scripts).</span></span>

<span data-ttu-id="f5e0e-132">언어 모드에 대한 자세한 내용은 [about_Language_modes](/powershell/module/microsoft.powershell.core/about/about_language_modes)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-132">For more information about language modes, see [about_Language_modes](/powershell/module/microsoft.powershell.core/about/about_language_modes).</span></span>

### <a name="choose-the-jea-identity"></a><span data-ttu-id="f5e0e-133">JEA ID 선택</span><span class="sxs-lookup"><span data-stu-id="f5e0e-133">Choose the JEA identity</span></span>

<span data-ttu-id="f5e0e-134">백그라운드에서 JEA에는 연결된 사용자의 명령을 실행할 때 사용할 ID(계정)가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-134">Behind the scenes, JEA needs an identity (account) to use when running a connected user's commands.</span></span>
<span data-ttu-id="f5e0e-135">세션 구성 파일에서 JEA가 사용하는 ID를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-135">You define which identity JEA uses in the session configuration file.</span></span>

#### <a name="local-virtual-account"></a><span data-ttu-id="f5e0e-136">로컬 가상 계정</span><span class="sxs-lookup"><span data-stu-id="f5e0e-136">Local Virtual Account</span></span>

<span data-ttu-id="f5e0e-137">로컬 가상 계정은 JEA 엔드포인트에 대해 정의된 모든 역할이 로컬 머신을 관리하는 데 사용되고 로컬 관리자 계정으로 명령을 성공적으로 실행할 수 있는 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-137">Local virtual accounts are useful when all roles defined for the JEA endpoint are used to manage the local machine and a local administrator account is sufficient to run the commands successfully.</span></span>
<span data-ttu-id="f5e0e-138">가상 계정은 특정 사용자에게 고유하고 해당 PowerShell 세션 기간 동안만 지속하는 임시 계정입니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-138">Virtual accounts are temporary accounts that are unique to a specific user and only last for the duration of their PowerShell session.</span></span> <span data-ttu-id="f5e0e-139">구성원 서버 또는 워크스테이션에서 가상 계정은 로컬 컴퓨터의 **Administrators** 그룹에 속합니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-139">On a member server or workstation, virtual accounts belong to the local computer's **Administrators** group.</span></span> <span data-ttu-id="f5e0e-140">Active Directory 도메인 컨트롤러에서 가상 계정은 도메인의 **Domain Admins** 그룹에 속합니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-140">On an Active Directory Domain Controller, virtual accounts belong to the domain's **Domain Admins** group.</span></span>

```powershell
# Setting the session to use a virtual account
RunAsVirtualAccount = $true
```

<span data-ttu-id="f5e0e-141">세션 구성에서 정의된 역할에 전체 관리 권한이 필요하지 않는 경우 가상 계정이 속할 보안 그룹을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-141">If the roles defined by the session configuration don't require full administrative privilege, you can specify the security groups to which the virtual account will belong.</span></span> <span data-ttu-id="f5e0e-142">구성원 서버 또는 워크스테이션에서 지정된 보안 그룹은 도메인의 그룹이 아니라 로컬 그룹이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-142">On a member server or workstation, the specified security groups must be local groups, not groups from a domain.</span></span>

<span data-ttu-id="f5e0e-143">하나 이상의 보안 그룹을 지정하면 가상 계정이 로컬 또는 도메인 관리자 그룹에 할당되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-143">When one or more security groups are specified, the virtual account isn't assigned to the local or domain administrators group.</span></span>

```powershell
# Setting the session to use a virtual account that only belongs to the NetworkOperator and NetworkAuditor local groups
RunAsVirtualAccount = $true
RunAsVirtualAccountGroups = 'NetworkOperator', 'NetworkAuditor'
```

> [!NOTE]
> <span data-ttu-id="f5e0e-144">가상 계정에는 일시적으로 로컬 서버 보안 정책에서 서비스 권한으로 로그온 권한이 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-144">Virtual accounts are temporarily granted the Logon as a service right in the local server security policy.</span></span> <span data-ttu-id="f5e0e-145">정책에서 지정된 VirtualAccountGroups 중 하나에 이 권한이 이미 부여된 경우 개별 가상 계정은 더 이상 추가되지 않고 정책에서 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-145">If one of the VirtualAccountGroups specified has already been granted this right in the policy, the individual virtual account will no longer be added and removed from the policy.</span></span> <span data-ttu-id="f5e0e-146">도메인 컨트롤러와 같이 도메인 컨트롤러 보안 정책에 대한 수정 버전을 긴밀히 감사하는 시나리오에 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-146">This can be useful in scenarios such as domain controllers where revisions to the domain controller security policy are closely audited.</span></span> <span data-ttu-id="f5e0e-147">2018년 11월 이후 롤업을 포함한 Windows Server 2016 또는 2019년 1월 이후 롤업을 포함한 Windows Server 2019에서만 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-147">This is only available in Windows Server 2016 with the November 2018 or later rollup and Windows Server 2019 with the January 2019 or later rollup.</span></span>

#### <a name="group-managed-service-account"></a><span data-ttu-id="f5e0e-148">그룹 관리 서비스 계정</span><span class="sxs-lookup"><span data-stu-id="f5e0e-148">Group-managed service account</span></span>

<span data-ttu-id="f5e0e-149">GMSA(그룹 관리 서비스 계정)는 JEA 사용자가 파일 공유 및 웹 서비스 등의 네트워크 리소스에 액세스해야 하는 경우 사용하기에 적합한 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-149">A group-managed service account (GMSA) is the appropriate identity to use when JEA users need to access network resources such as file shares and web services.</span></span> <span data-ttu-id="f5e0e-150">GMSA는 도메인 내의 모든 머신에 있는 리소스를 인증하는 데 사용되는 도메인 ID를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-150">GMSAs give you a domain identity that is used to authenticate with resources on any machine within the domain.</span></span> <span data-ttu-id="f5e0e-151">GMSA가 제공하는 권한은 액세스 중인 리소스에 의해 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-151">The rights that a GMSA provides are determined by the resources you're accessing.</span></span> <span data-ttu-id="f5e0e-152">머신 또는 서비스 관리자가 GMSA에 대한 권한을 명시적으로 부여하지 않는 한, 모든 머신 또는 서비스에 대한 관리자 권한도 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-152">You don't have admin rights on any machines or services unless the machine or service administrator has explicitly granted those rights to the GMSA.</span></span>

```powershell
# Configure JEA sessions to use the GMSA in the local computer's domain
# with the sAMAccountName of 'MyJEAGMSA'
GroupManagedServiceAccount = 'Domain\MyJEAGMSA'
```

<span data-ttu-id="f5e0e-153">GMSA는 필요한 경우에만 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-153">GMSAs should only be used when necessary:</span></span>

- <span data-ttu-id="f5e0e-154">GMSA를 사용할 때 사용자에 대한 작업을 거슬러 올라가서 추적하는 것은 어렵습니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-154">It's difficult to trace back actions to a user when using a GMSA.</span></span> <span data-ttu-id="f5e0e-155">모든 사용자는 동일한 실행 ID를 공유합니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-155">Every user shares the same run-as identity.</span></span> <span data-ttu-id="f5e0e-156">PowerShell 세션 기록 및 로그를 검토하여 개별 사용자와 해당 작업 간의 상관 관계를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-156">You must review PowerShell session transcripts and logs to correlate individual users with their actions.</span></span>

- <span data-ttu-id="f5e0e-157">GMSA는 연결하는 사용자가 액세스할 필요가 없는 많은 네트워크 리소스에 대한 액세스 권한을 가질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-157">The GMSA may have access to many network resources that the connecting user doesn't need access to.</span></span> <span data-ttu-id="f5e0e-158">항상 JEA 세션에서 유효 권한을 제한하여 최소 권한 원칙을 따르도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-158">Always try to limit effective permissions in a JEA session to follow the principle of least privilege.</span></span>

> [!NOTE]
> <span data-ttu-id="f5e0e-159">그룹 관리 서비스 계정은 PowerShell 5.1 이상을 사용하는 도메인 조인 머신에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-159">Group managed service accounts are only available on domain-joined machines using PowerShell 5.1 or newer.</span></span>

<span data-ttu-id="f5e0e-160">JEA 세션 보안에 대한 자세한 내용은 [보안 고려 사항](security-considerations.md) 문서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-160">For more information about securing a JEA session, see the [security considerations](security-considerations.md) article.</span></span>

### <a name="session-transcripts"></a><span data-ttu-id="f5e0e-161">세션 기록</span><span class="sxs-lookup"><span data-stu-id="f5e0e-161">Session transcripts</span></span>

<span data-ttu-id="f5e0e-162">사용자의 세션의 기록을 자동으로 기록하도록 JEA 엔드포인트를 구성하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-162">It's recommended that you configure a JEA endpoint to automatically record transcripts of users' sessions.</span></span> <span data-ttu-id="f5e0e-163">PowerShell 세션 기록은 연결하는 사용자, 사용자에게 할당된 실행 ID 및 사용자가 실행한 명령에 대한 정보를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-163">PowerShell session transcripts contain information about the connecting user, the run as identity assigned to them, and the commands run by the user.</span></span> <span data-ttu-id="f5e0e-164">이러한 기록은 시스템에 대한 특정 변경 내용을 수행한 사용자를 파악해야 하는 감사 팀에게 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-164">They can be useful to an auditing team who needs to understand who made a specific change to a system.</span></span>

<span data-ttu-id="f5e0e-165">세션 구성 파일에서 자동 기록을 구성하려면 기록이 저장되는 폴더의 경로를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-165">To configure automatic transcription in the session configuration file, provide a path to a folder where the transcripts should be stored.</span></span>

```powershell
TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
```

<span data-ttu-id="f5e0e-166">기록은 디렉터리에 대한 읽기 및 쓰기 권한이 필요한 **로컬 시스템** 계정에 의해 폴더에 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-166">Transcripts are written to the folder by the **Local System** account, which requires read and write access to the directory.</span></span> <span data-ttu-id="f5e0e-167">표준 사용자는 폴더에 대한 액세스 권한이 없어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-167">Standard users should have no access to the folder.</span></span> <span data-ttu-id="f5e0e-168">기록을 감사할 수 있는 액세스 권한이 있는 보안 관리자의 수를 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-168">Limit the number of security administrators that have access to audit the transcripts.</span></span>

### <a name="user-drive"></a><span data-ttu-id="f5e0e-169">사용자 드라이브</span><span class="sxs-lookup"><span data-stu-id="f5e0e-169">User drive</span></span>

<span data-ttu-id="f5e0e-170">연결하는 사용자가 JEA 엔드포인트간에 파일을 복사해야 하는 경우 세션 구성 파일에서 사용자 드라이브를 사용하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-170">If your connecting users need to copy files to or from the JEA endpoint, you can enable the user drive in the session configuration file.</span></span> <span data-ttu-id="f5e0e-171">사용자 드라이브는 각 연결하는 사용자에 대해 고유한 폴더에 매핑되는 **PSDrive** 입니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-171">The user drive is a **PSDrive** that is mapped to a unique folder for each connecting user.</span></span> <span data-ttu-id="f5e0e-172">이 폴더를 통해 사용자는 전체 파일 시스템에 대한 액세스 권한을 부여하거나 FileSystem 공급자를 노출하지 않고 시스템으로 간에 파일을 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-172">This folder allows users to copy files to or from the system without giving them access to the full file system or exposing the FileSystem provider.</span></span> <span data-ttu-id="f5e0e-173">사용자 드라이브 콘텐츠는 세션 전체에서 유지되어 네트워크 연결이 중단될 수 있는 상황을 수용합니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-173">The user drive contents are persistent across sessions to accommodate situations where network connectivity may be interrupted.</span></span>

```powershell
MountUserDrive = $true
```

<span data-ttu-id="f5e0e-174">기본적으로 사용자 드라이브를 사용하여 사용자당 최대 50MB의 데이터를 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-174">By default, the user drive allows you to store a maximum of 50MB of data per user.</span></span> <span data-ttu-id="f5e0e-175">*UserDriveMaximumSize* 필드를 사용하여 사용자가 사용할 수 있는 데이터의 양을 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-175">You can limit the amount of data a user can consume with the *UserDriveMaximumSize* field.</span></span>

```powershell
# Enables the user drive with a per-user limit of 500MB (524288000 bytes)
MountUserDrive = $true
UserDriveMaximumSize = 524288000
```

<span data-ttu-id="f5e0e-176">사용자 드라이브의 데이터가 유지되지 않게 하려는 경우 매일 밤 자동으로 폴더를 정리하도록 시스템에 대한 예약된 작업을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-176">If you don't want data in the user drive to be persistent, you can configure a scheduled task on the system to automatically clean up the folder every night.</span></span>

> [!NOTE]
> <span data-ttu-id="f5e0e-177">사용자 드라이브는 PowerShell 5.1 이상에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-177">The user drive is only available in PowerShell 5.1 or newer.</span></span>

<span data-ttu-id="f5e0e-178">PSDrives에 대한 자세한 내용은 [PowerShell 드라이브 관리](/powershell/scripting/samples/managing-windows-powershell-drives)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-178">For more information about PSDrives, see [Managing PowerShell drives](/powershell/scripting/samples/managing-windows-powershell-drives).</span></span>

### <a name="role-definitions"></a><span data-ttu-id="f5e0e-179">역할 정의</span><span class="sxs-lookup"><span data-stu-id="f5e0e-179">Role definitions</span></span>

<span data-ttu-id="f5e0e-180">세션 구성 파일의 역할 정의는 **역할** 에 대한 **사용자** 의 매핑을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-180">Role definitions in a session configuration file define the mapping of **users** to **roles** .</span></span> <span data-ttu-id="f5e0e-181">이 필드에 포함된 모든 사용자 또는 그룹은 등록될 때 JEA 엔드포인트에 대한 사용 권한이 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-181">Every user or group included in this field is granted permission to the JEA endpoint when it's registered.</span></span>
<span data-ttu-id="f5e0e-182">각 사용자 또는 그룹은 해시 테이블의 키로 한 번만 포함될 수 있지만, 역할은 여러 개가 할당될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-182">Each user or group can be included as a key in the hashtable only once, but can be assigned multiple roles.</span></span> <span data-ttu-id="f5e0e-183">역할 기능의 이름은 `.psrc` 확장명이 없는 역할 기능 파일의 이름이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-183">The name of the role capability should be the name of the role capability file, without the `.psrc` extension.</span></span>

```powershell
RoleDefinitions = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}
```

<span data-ttu-id="f5e0e-184">사용자가 역할 정의에서 둘 이상의 그룹에 속하는 경우 각 역할에 대한 액세스 권한을 얻게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-184">If a user belongs to more than one group in the role definition, they get access to the roles of each.</span></span> <span data-ttu-id="f5e0e-185">두 역할이 같은 cmdlet에 대한 액세스 권한을 부여하는 경우 사용자에게 최대로 허용되는 매개 변수 집합이 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-185">When two roles grant access to the same cmdlets, the most permissive parameter set is granted to the user.</span></span>

<span data-ttu-id="f5e0e-186">역할 정의 필드에서 로컬 사용자 또는 그룹을 지정할 때는 **localhost** 또는 와일드카드가 아닌 컴퓨터 이름을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-186">When specifying local users or groups in the role definitions field, be sure to use the computer name, not **localhost** or wildcards.</span></span> <span data-ttu-id="f5e0e-187">`$env:COMPUTERNAME` 변수를 검사하여 컴퓨터 이름을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-187">You can check the computer name by inspecting the `$env:COMPUTERNAME` variable.</span></span>

```powershell
RoleDefinitions = @{
    'MyComputerName\MyLocalGroup' = @{ RoleCapabilities = 'DnsAuditor' }
}
```

### <a name="role-capability-search-order"></a><span data-ttu-id="f5e0e-188">역할 기능 검색 순서</span><span class="sxs-lookup"><span data-stu-id="f5e0e-188">Role capability search order</span></span>

<span data-ttu-id="f5e0e-189">위의 예제에 표시된 것처럼 역할 기능은 역할 기능 파일의 기본 이름으로 참조됩니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-189">As shown in the example above, role capabilities are referenced by the base name of the role capability file.</span></span> <span data-ttu-id="f5e0e-190">파일의 기본 이름은 확장명이 없는 파일 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-190">The base name of a file is the filename without the extension.</span></span> <span data-ttu-id="f5e0e-191">시스템에서 동일한 이름의 여러 역할 기능을 사용할 수 있는 경우 PowerShell은 암시적 검색 순서를 사용하여 유효 역할 기능 파일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-191">If multiple role capabilities are available on the system with the same name, PowerShell uses its implicit search order to select the effective role capability file.</span></span> <span data-ttu-id="f5e0e-192">JEA는 이름이 같은 모든 역할 기능 파일에 대한 액세스 권한을 부여하지 **않습니다** .</span><span class="sxs-lookup"><span data-stu-id="f5e0e-192">JEA does **not** give access to all role capability files with the same name.</span></span>

<span data-ttu-id="f5e0e-193">JEA에서는 `$env:PSModulePath` 환경 변수를 사용하여 역할 기능 파일을 검색할 경로를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-193">JEA uses the `$env:PSModulePath` environment variable to determine which paths to scan for role capability files.</span></span> <span data-ttu-id="f5e0e-194">JEA는 이러한 경로 각각에서 "RoleCapabilities" 하위 폴더가 포함된 유효한 PowerShell 모듈을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-194">Within each of those paths, JEA looks for valid PowerShell modules that contain a "RoleCapabilities" subfolder.</span></span> <span data-ttu-id="f5e0e-195">모듈을 가져오는 경우와 마찬가지로, JEA는 같은 이름의 사용자 지정 역할 기능보다 Windows와 함께 제공되는 역할 기능을 선호합니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-195">As with importing modules, JEA prefers role capabilities that are shipped with Windows to custom role capabilities with the same name.</span></span>

<span data-ttu-id="f5e0e-196">명명에 관한 다른 모든 충돌의 경우는 Windows에서 디렉터리의 파일을 열거하는 순서에 따라 우선순위가 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-196">For all other naming conflicts, precedence is determined by the order in which Windows enumerates the files in the directory.</span></span> <span data-ttu-id="f5e0e-197">순서는 알파벳순으로 보장되지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-197">The order isn't guaranteed to be alphabetical.</span></span> <span data-ttu-id="f5e0e-198">지정된 이름과 일치하는 첫 번째 역할 기능으로 검색된 것이 연결 사용자에게 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-198">The first role capability file found that matches the specified name is used for the connecting user.</span></span> <span data-ttu-id="f5e0e-199">역할 기능 검색 순서가 결정적이지 않으므로 역할 기능에는 고유한 파일 이름이 있는 것이 **좋습니다** .</span><span class="sxs-lookup"><span data-stu-id="f5e0e-199">Since the role capability search order isn't deterministic, it's **strongly recommended** that role capabilities have unique filenames.</span></span>

### <a name="conditional-access-rules"></a><span data-ttu-id="f5e0e-200">조건부 액세스 규칙</span><span class="sxs-lookup"><span data-stu-id="f5e0e-200">Conditional access rules</span></span>

<span data-ttu-id="f5e0e-201">**RoleDefinitions** 필드에 포함된 모든 사용자 및 그룹에는 자동으로 JEA 엔드포인트에 대한 액세스 권한이 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-201">All users and groups included in the **RoleDefinitions** field are automatically granted access to JEA endpoints.</span></span> <span data-ttu-id="f5e0e-202">조건부 액세스 규칙을 사용하면 이 액세스 권한을 구체화하고 사용자가 할당된 역할에 영향을 주지 않는 추가 보안 그룹에 속하도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-202">Conditional access rules allow you to refine this access and require users to belong to additional security groups that don't impact the roles to which they're assigned.</span></span> <span data-ttu-id="f5e0e-203">이 기능은 Just In Time 권한 있는 액세스 권한 관리 솔루션, 스마트 카드 인증 또는 기타 다단계 인증 솔루션을 JEA와 통합하려는 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-203">This is useful when you want to integrate a just-in-time privileged access management solution, smartcard authentication, or other multifactor authentication solution with JEA.</span></span>

<span data-ttu-id="f5e0e-204">조건부 액세스 규칙은 세션 구성 파일에서 RequiredGroups 필드에 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-204">Conditional access rules are defined in the RequiredGroups field in a session configuration file.</span></span>
<span data-ttu-id="f5e0e-205">여기서 'And' 및 'Or' 키를 사용하여 규칙을 구성하는 해시 테이블(필요에 따라 중첩됨)을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-205">There, you can provide a hashtable (optionally nested) that uses 'And' and 'Or' keys to construct your rules.</span></span> <span data-ttu-id="f5e0e-206">다음은 이 필드를 사용하는 방법의 몇 가지 예입니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-206">Here are some examples of how to use this field:</span></span>

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
> <span data-ttu-id="f5e0e-207">조건부 액세스 규칙은 PowerShell 5.1 이상에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-207">Conditional access rules are only available in PowerShell 5.1 or newer.</span></span>

### <a name="other-properties"></a><span data-ttu-id="f5e0e-208">기타 속성</span><span class="sxs-lookup"><span data-stu-id="f5e0e-208">Other properties</span></span>

<span data-ttu-id="f5e0e-209">세션 구성 파일도 역할 기능 파일이 수행할 수 있는 모든 작업을 수행할 수 있지만, 연결하는 사용자에게 다른 명령에 대한 액세스 권한을 부여하는 기능은 제외됩니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-209">Session configuration files can also do everything a role capability file can do, just without the ability to give connecting users access to different commands.</span></span> <span data-ttu-id="f5e0e-210">모든 사용자가 특정 cmdlet, 함수 또는 공급자에 액세스할 수 있게 하려는 경우 세션 구성 파일에서 직접 이렇게 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-210">If you want to allow all users access to specific cmdlets, functions, or providers, you can do so right in the session configuration file.</span></span>
<span data-ttu-id="f5e0e-211">세션 구성 파일에서 지원되는 속성의 전체 목록을 보려면 `Get-Help New-PSSessionConfigurationFile -Full`을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-211">For a full list of supported properties in the session configuration file, run `Get-Help New-PSSessionConfigurationFile -Full`.</span></span>

## <a name="testing-a-session-configuration-file"></a><span data-ttu-id="f5e0e-212">세션 구성 파일 테스트</span><span class="sxs-lookup"><span data-stu-id="f5e0e-212">Testing a session configuration file</span></span>

<span data-ttu-id="f5e0e-213">[Test-PSSessionConfigurationFile](/powershell/module/microsoft.powershell.core/test-pssessionconfigurationfile) cmdlet을 사용하여 세션 구성 파일을 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-213">You can test a session configuration using the [Test-PSSessionConfigurationFile](/powershell/module/microsoft.powershell.core/test-pssessionconfigurationfile) cmdlet.</span></span> <span data-ttu-id="f5e0e-214">`.pssc` 파일을 수동으로 편집한 경우 세션 구성 파일을 테스트하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-214">It's recommended that you test your session configuration file if you've manually edited the `.pssc` file.</span></span> <span data-ttu-id="f5e0e-215">테스트를 통해 구문이 올바른지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-215">Testing ensures the syntax is correct.</span></span> <span data-ttu-id="f5e0e-216">세션 구성 파일이 이 테스트에 실패하면 시스템에 등록할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-216">If a session configuration file fails this test, it can't be registered on the system.</span></span>

## <a name="sample-session-configuration-file"></a><span data-ttu-id="f5e0e-217">샘플 세션 구성 파일</span><span class="sxs-lookup"><span data-stu-id="f5e0e-217">Sample session configuration file</span></span>

<span data-ttu-id="f5e0e-218">다음 예제에서는 JEA에 대한 세션 구성을 만들고 유효성을 검사하는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-218">The following example shows how to create and validate a session configuration for JEA.</span></span> <span data-ttu-id="f5e0e-219">역할 정의는 편의성과 가독성을 위해 생성되어 `$roles` 변수에 저장되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-219">The role definitions are created and stored in the `$roles` variable for convenience and readability.</span></span> <span data-ttu-id="f5e0e-220">이는 작업을 수행하기 위한 요구 사항은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-220">It isn't a requirement to do so.</span></span>

```powershell
$roles = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}

New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\JEAConfig.pssc -RunAsVirtualAccount -TranscriptDirectory 'C:\ProgramData\JEAConfiguration\Transcripts' -RoleDefinitions $roles -RequiredGroups @{ Or = '2FA-logon', 'smartcard-logon' }
Test-PSSessionConfigurationFile -Path .\JEAConfig.pssc # should yield True
```

## <a name="updating-session-configuration-files"></a><span data-ttu-id="f5e0e-221">세션 구성 파일 업데이트</span><span class="sxs-lookup"><span data-stu-id="f5e0e-221">Updating session configuration files</span></span>

<span data-ttu-id="f5e0e-222">역할에 대한 사용자의 매핑을 비롯한 JEA 세션 구성의 속성을 변경하려면 JEA 세션 구성을 [등록 취소](register-jea.md#unregistering-jea-configurations)해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-222">To change the properties of a JEA session configuration, including the mapping of users to roles, you must [unregister](register-jea.md#unregistering-jea-configurations).</span></span> <span data-ttu-id="f5e0e-223">그런 다음, 업데이트된 세션 구성 파일을 사용하여 JEA 세션 구성을 [다시 등록](register-jea.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="f5e0e-223">Then, [re-register](register-jea.md) the JEA session configuration using an updated session configuration file.</span></span>

## <a name="next-steps"></a><span data-ttu-id="f5e0e-224">다음 단계</span><span class="sxs-lookup"><span data-stu-id="f5e0e-224">Next steps</span></span>

- [<span data-ttu-id="f5e0e-225">JEA 구성 등록</span><span class="sxs-lookup"><span data-stu-id="f5e0e-225">Register a JEA configuration</span></span>](register-jea.md)
- [<span data-ttu-id="f5e0e-226">JEA 역할 작성</span><span class="sxs-lookup"><span data-stu-id="f5e0e-226">Author JEA roles</span></span>](role-capabilities.md)
