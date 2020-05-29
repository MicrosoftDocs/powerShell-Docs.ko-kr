---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: JEA(Just Enough Administration)에 대한 개선 사항
ms.openlocfilehash: 9bb45ad2ddd459b99fc58610dfd8145992093624
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/23/2020
ms.locfileid: "83808919"
---
# <a name="improvements-to-just-enough-administration-jea"></a><span data-ttu-id="5f7fa-103">JEA(Just Enough Administration)에 대한 개선 사항</span><span class="sxs-lookup"><span data-stu-id="5f7fa-103">Improvements to Just Enough Administration (JEA)</span></span>

<span data-ttu-id="5f7fa-104">충분한 관리는 PowerShell 원격을 통해 역할 기반 관리를 가능하게 하는 WMF 5.0의 새로운 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-104">Just Enough Administration is a new feature in WMF 5.0 that enables role-based administration through PowerShell remoting.</span></span> <span data-ttu-id="5f7fa-105">이 기능은 관리자가 아닌 사용자가 특정 명령, 스크립트 및 실행 파일을 관리자 권한으로 실행할 수 있도록 허용하여 기존의 제한된 엔드포인트 인프라를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-105">It extends the existing constrained endpoint infrastructure by allowing non-administrators to run specific commands, scripts, and executables as an administrator.</span></span> <span data-ttu-id="5f7fa-106">또한 사용자 환경의 전체 관리자 수는 줄이고 보안은 향상시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-106">This enables you to reduce the number of full administrators in your environment and improve security.</span></span>

## <a name="constrained-file-copy-tofrom-jea-endpoints"></a><span data-ttu-id="5f7fa-107">JEA 엔드포인트와의 파일 복사 제한</span><span class="sxs-lookup"><span data-stu-id="5f7fa-107">Constrained file copy to/from JEA endpoints</span></span>

<span data-ttu-id="5f7fa-108">이제 원격으로 JEA 엔드포인트로나 JEA 엔드포인트에서 파일을 복사할 수 있으며 연결하는 사용자는 시스템에서 ‘어떤’ 파일도 복사할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-108">You can now remotely copy files to/from a JEA endpoint and be assured that the connecting user can't copy just *any* file on your system.</span></span> <span data-ttu-id="5f7fa-109">이것이 가능하려면 연결하는 사용자에 대해 사용자 드라이브를 탑재하도록 PSSC 파일을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-109">This is possible by configuring your PSSC file to mount a user drive for connecting users.</span></span> <span data-ttu-id="5f7fa-110">사용자 드라이브는 연결하는 각 사용자에게 고유하고 세션 간에 유지되는 새 PSDrive입니다.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-110">The user drive is a new PSDrive that is unique to each connecting user and persists across sessions.</span></span> <span data-ttu-id="5f7fa-111">`Copy-Item`을 사용하여 JEA 세션으로나 JEA 세센에서 파일을 복사하는 경우에는 사용자 드라이브에만 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-111">When `Copy-Item` is used to copy files to or from a JEA session, it is constrained to only allow access to the user drive.</span></span> <span data-ttu-id="5f7fa-112">다른 PSDrive로 파일을 복사하려고 하면 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-112">Attempts to copy files to any other PSDrive will fail.</span></span>

<span data-ttu-id="5f7fa-113">JEA 세션 구성 파일에서 사용자 드라이브를 설정하려면 다음과 같은 새 필드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-113">To set up the user drive in your JEA session configuration file, use the following new fields:</span></span>

```powershell
MountUserDrive = $true
UserDriveMaximumSize = 10485760    # 10 MB
```

<span data-ttu-id="5f7fa-114">사용자 드라이브를 지원하는 폴더가 생성되는 위치`$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\DriveRoots\`</span><span class="sxs-lookup"><span data-stu-id="5f7fa-114">The folder backing the user drive is created at `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\DriveRoots\`.</span></span> <span data-ttu-id="5f7fa-115">엔드포인트에 연결하는 각 사용자에 대해 `$env:USERDOMAIN_$env:USERNAME`이라는 이름으로 폴더가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-115">For each user connecting to the endpoint, a folder is created with the name `$env:USERDOMAIN_$env:USERNAME`.</span></span>

<span data-ttu-id="5f7fa-116">사용자 드라이브를 활용하고 사용자 드라이브를 노출하도록 구성된 JEA 엔드포인트로 또는 JEA 엔드포인트에서 파일을 복사하려면 `Copy-Item`에서 `-ToSession` 및 `-FromSession` 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-116">To utilize the user drive and copy files to/from a JEA endpoint configured to expose the User drive, use the `-ToSession` and `-FromSession` parameters on `Copy-Item`.</span></span>

```powershell
# Connect to the JEA endpoint
$jeasession = New-PSSession -ComputerName 'srv01' -ConfigurationName 'UserDemo'

# Copy a file in the local folder to the remote machine.
# Note: you cannot specify the file name or subfolder on the remote machine.
# You must exactly type "User:"
Copy-Item -Path .\SampleFile.txt -Destination User: -ToSession $jeasession

# Copy the file back from the remote machine to your local machine
Copy-Item -Path User:\SampleFile.txt -Destination . -FromSession $jeasession
```

<span data-ttu-id="5f7fa-117">그런 다음 사용자 드라이브에 저장된 데이터를 처리하는 사용자 지정 함수를 작성하고 역할 기능 파일에서 이러한 함수를 사용자가 사용할 수 있도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-117">You can then write custom functions to process the data stored in the user drive and make those available to users in your Role Capability file.</span></span>

## <a name="support-for-group-managed-service-accounts"></a><span data-ttu-id="5f7fa-118">그룹 관리 서비스 계정 지원</span><span class="sxs-lookup"><span data-stu-id="5f7fa-118">Support for Group Managed Service Accounts</span></span>

<span data-ttu-id="5f7fa-119">경우에 따라 사용자가 JEA 세션에서 수행해야 하는 작업을 위해 로컬 컴퓨터에 없는 리소스에 액세스해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-119">In some cases, a task a user needs to perform in a JEA session may need to access resources beyond the local machine.</span></span> <span data-ttu-id="5f7fa-120">JEA 세션이 가상 계정을 사용하도록 구성된 경우 이러한 리소스에 연결하려는 시도는 가상 계정이나 연결된 사용자가 아니라 로컬 컴퓨터의 ID가 하는 것으로 보입니다.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-120">When a JEA session is configured to use a virtual account, any attempt to reach such resources will appear to come from the local machine's identity, not the virtual account or connected user.</span></span> <span data-ttu-id="5f7fa-121">TP5에서는 [그룹 관리 서비스 계정](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj128431\(v=ws.11\))의 컨텍스트에서 JEA를 실행할 수 있도록 설정되어 있으므로 도메인 ID를 사용하여 네트워크 리소스에 훨씬 더 쉽게 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-121">In TP5, we have enabled support for running JEA under the context of a [Group Managed Service Account](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj128431\(v=ws.11\)), making it much easier to access network resources by using a domain identity.</span></span>

<span data-ttu-id="5f7fa-122">gMSA 계정으로 실행되도록 JEA 세션을 구성하려면 PSSC 파일에서 다음과 같은 새 키를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-122">To configure a JEA session to run under a gMSA account, use the following new key in your PSSC file:</span></span>

```powershell
# Provide the name of your gMSA account here (don't include a trailing $)
# The local machine must be privileged to use this gMSA in Active Directory
GroupManagedServiceAccount = 'myGMSAforJEA'

# You cannot configure a JEA endpoint to use both a gMSA and virtual account
# You can leave the RunAsVirtualAccount field commented out or explicitly set it to false
RunAsVirtualAccount = $false
```

> [!NOTE]
> <span data-ttu-id="5f7fa-123">그룹 관리 서비스 계정은 격리나 제한된 범위의 가상 계정을 제공하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-123">Group Managed Service Accounts do not afford the isolation or limited scope of virtual accounts.</span></span>
> <span data-ttu-id="5f7fa-124">연결하는 모든 사용자는 동일한 gMSA ID를 공유하므로 기업 전체에서 권한이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-124">Every connecting user will share the same gMSA identity, which may have permissions across your entire enterprise.</span></span> <span data-ttu-id="5f7fa-125">gMSA를 사용할 때는 주의해야 하며 항상 가능한 경우 로컬 컴퓨터로 제한된 가상 계정을 선택하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-125">Be very careful when selecting to use a gMSA, and always prefer virtual accounts which are limited to the local machine when possible.</span></span>

## <a name="conditional-access-policies"></a><span data-ttu-id="5f7fa-126">조건부 액세스 정책</span><span class="sxs-lookup"><span data-stu-id="5f7fa-126">Conditional access policies</span></span>

<span data-ttu-id="5f7fa-127">JEA는 사용자가 JEA를 관리할 시스템에 연결된 경우 수행할 수 있는 작업을 제한하는 데 유용하지만, 사용자가 JEA를 사용할 수 있는 *시기*도 제한하려면 어떻게 하나요?</span><span class="sxs-lookup"><span data-stu-id="5f7fa-127">JEA is great at limiting what someone can do when they've connected to a system to manage it, but what if you also want to limit *when* someone can use JEA?</span></span> <span data-ttu-id="5f7fa-128">사용자가 JEA 세션을 설정하려면 속해 있어야 하는 보안 그룹을 지정할 수 있는 구성 옵션이 세션 구성 파일(.pssc)에 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-128">We have added configuration options into the session configuration files (.pssc) to let you specify security groups to which a user must belong in order to establish a JEA session.</span></span> <span data-ttu-id="5f7fa-129">이 옵션은 환경에 JIT(Just In Time) 시스템이 있고 사용자가 높은 권한의 JEA 엔드포인트에 액세스하기 전에 권한을 높이도록 하려는 경우에 특히 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-129">This is especially helpful if you have a Just In Time (JIT) system in your environment, and want to make your users elevate their privileges before accessing a highly-privileged JEA endpoint.</span></span>

<span data-ttu-id="5f7fa-130">PSSC 파일의 새 *RequiredGroups* 필드를 사용하여 사용자가 JEA에 연결할 수 있는지 여부를 결정하는 논리를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-130">The new *RequiredGroups* field in the PSSC file allows you to specify the logic to determine if a user can connect to JEA.</span></span> <span data-ttu-id="5f7fa-131">이를 위해서는 'And' 및 'Or' 키를 사용하는 해시테이블(필요에 따라 중첩됨)을 지정하여 규칙을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-131">It consists of specifying a hashtable (optionally nested) that uses the 'And' and 'Or' keys to construct your rules.</span></span> <span data-ttu-id="5f7fa-132">다음은 이 필드를 사용하는 방법의 몇 가지 예입니다.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-132">Here are some examples of how to use this field:</span></span>

```powershell
# Example 1: Connecting users must belong to a security group called "elevated-jea"
RequiredGroups = @{ And = 'elevated-jea' }

# Example 2: Connecting users must have signed on with 2 factor authentication or a smart card
# The 2 factor authentication group name is "2FA-logon" and the smart card group name is "smartcard-logon"
RequiredGroups = @{ Or = '2FA-logon', 'smartcard-logon' }

# Example 3: Connecting users must elevate into "elevated-jea" with their JIT system and have logged on with 2FA or a smart card
RequiredGroups = @{ And = 'elevated-jea', @{ Or = '2FA-logon', 'smartcard-logon' }}
```

## <a name="fixed-virtual-accounts-are-now-supported-on-windows-server-2008-r2"></a><span data-ttu-id="5f7fa-133">수정됨: 이제 Windows Server 2008 R2에서 가상 계정이 지원됨</span><span class="sxs-lookup"><span data-stu-id="5f7fa-133">Fixed: Virtual accounts are now supported on Windows Server 2008 R2</span></span>

<span data-ttu-id="5f7fa-134">WMF 5.1에서는 이제 Windows Server 2008 R2에서 가상 계정을 사용할 수 있으므로 Windows Server 2008 R2부터 2016까지, 구성 및 기능 패리티를 일관되게 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-134">In WMF 5.1, you are now able to use virtual accounts on Windows Server 2008 R2, enabling consistent configurations and feature parity across Windows Server 2008 R2 - 2016.</span></span> <span data-ttu-id="5f7fa-135">Windows 7에서 JEA를 사용할 경우에는 가상 계정이 계속 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-135">Virtual accounts remain unsupported when using JEA on Windows 7.</span></span>
