---
description: PowerShell 프로필을 만들고 사용 하는 방법을 설명 합니다.
Locale: en-US
ms.date: 11/30/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_profiles?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Profiles
ms.openlocfilehash: 65920fd9f11a1d9206ba3dbe899831ffe2ced5be
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/12/2021
ms.locfileid: "103194154"
---
# <a name="about-profiles"></a><span data-ttu-id="9d165-103">프로필 정보</span><span class="sxs-lookup"><span data-stu-id="9d165-103">About Profiles</span></span>

## <a name="short-description"></a><span data-ttu-id="9d165-104">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="9d165-104">Short Description</span></span>
<span data-ttu-id="9d165-105">PowerShell 프로필을 만들고 사용 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d165-105">Describes how to create and use a PowerShell profile.</span></span>

## <a name="long-description"></a><span data-ttu-id="9d165-106">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="9d165-106">Long Description</span></span>

<span data-ttu-id="9d165-107">PowerShell 프로필을 만들어 환경을 사용자 지정하고 시작하는 모든 PowerShell 세션에 세션별 요소를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d165-107">You can create a PowerShell profile to customize your environment and to add session-specific elements to every PowerShell session that you start.</span></span>

<span data-ttu-id="9d165-108">PowerShell 프로필은 PowerShell이 시작될 때 실행되는 스크립트입니다.</span><span class="sxs-lookup"><span data-stu-id="9d165-108">A PowerShell profile is a script that runs when PowerShell starts.</span></span> <span data-ttu-id="9d165-109">프로필을 로그온 스크립트로 사용 하 여 환경을 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d165-109">You can use the profile as a logon script to customize the environment.</span></span> <span data-ttu-id="9d165-110">명령, 별칭, 함수, 변수, 스냅인, 모듈 및 PowerShell 드라이브를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d165-110">You can add commands, aliases, functions, variables, snap-ins, modules, and PowerShell drives.</span></span> <span data-ttu-id="9d165-111">또한 다른 세션 관련 요소를 프로필에 추가 하 여 해당 요소를 가져오거나 다시 만들지 않고도 모든 세션에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d165-111">You can also add other session-specific elements to your profile so they are available in every session without having to import or re-create them.</span></span>

<span data-ttu-id="9d165-112">PowerShell은 사용자 및 호스트 프로그램에 대해 여러 프로필을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d165-112">PowerShell supports several profiles for users and host programs.</span></span> <span data-ttu-id="9d165-113">그러나 프로필을 만들지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9d165-113">However, it does not create the profiles for you.</span></span> <span data-ttu-id="9d165-114">이 항목에서는 프로필에 대해 설명 하 고 컴퓨터에서 프로필을 만들고 유지 관리 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d165-114">This topic describes the profiles, and it describes how to create and maintain profiles on your computer.</span></span>

<span data-ttu-id="9d165-115">PowerShell 콘솔 (PowerShell.exe)의 **Noprofile** 매개 변수를 사용 하 여 프로필 없이 powershell을 시작 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d165-115">It explains how to use the **NoProfile** parameter of the PowerShell console (PowerShell.exe) to start PowerShell without any profiles.</span></span> <span data-ttu-id="9d165-116">또한 프로필에 대 한 PowerShell 실행 정책의 영향을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d165-116">And, it explains the effect of the PowerShell execution policy on profiles.</span></span>

## <a name="the-profile-files"></a><span data-ttu-id="9d165-117">프로필 파일</span><span class="sxs-lookup"><span data-stu-id="9d165-117">The Profile Files</span></span>

<span data-ttu-id="9d165-118">PowerShell은 여러 프로필 파일을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d165-118">PowerShell supports several profile files.</span></span> <span data-ttu-id="9d165-119">또한 PowerShell 호스트 프로그램은 고유한 호스트 특정 프로필을 지원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d165-119">Also, PowerShell host programs can support their own host-specific profiles.</span></span>

<span data-ttu-id="9d165-120">예를 들어 PowerShell 콘솔은 다음과 같은 기본 프로필 파일을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d165-120">For example, the PowerShell console supports the following basic profile files.</span></span> <span data-ttu-id="9d165-121">프로필은 우선 순위에 따라 나열 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d165-121">The profiles are listed in precedence order.</span></span> <span data-ttu-id="9d165-122">첫 번째 프로필은 우선 순위가 가장 높습니다.</span><span class="sxs-lookup"><span data-stu-id="9d165-122">The first profile has the highest precedence.</span></span>

|<span data-ttu-id="9d165-123">설명</span><span class="sxs-lookup"><span data-stu-id="9d165-123">Description</span></span>               | <span data-ttu-id="9d165-124">경로</span><span class="sxs-lookup"><span data-stu-id="9d165-124">Path</span></span>                                          |
|--------------------------|-----------------------------------------------|
|<span data-ttu-id="9d165-125">모든 사용자, 모든 호스트</span><span class="sxs-lookup"><span data-stu-id="9d165-125">All Users, All Hosts</span></span>      |<span data-ttu-id="9d165-126">$PSHOME \\Profile.ps1</span><span class="sxs-lookup"><span data-stu-id="9d165-126">$PSHOME\\Profile.ps1</span></span>                           |
|<span data-ttu-id="9d165-127">모든 사용자, 현재 호스트</span><span class="sxs-lookup"><span data-stu-id="9d165-127">All Users, Current Host</span></span>   |<span data-ttu-id="9d165-128">$PSHOME \\Microsoft.PowerShell_profile.ps1</span><span class="sxs-lookup"><span data-stu-id="9d165-128">$PSHOME\\Microsoft.PowerShell_profile.ps1</span></span>      |
|<span data-ttu-id="9d165-129">현재 사용자, 모든 호스트</span><span class="sxs-lookup"><span data-stu-id="9d165-129">Current User, All Hosts</span></span>   |<span data-ttu-id="9d165-130">$Home \\ [My] 문서 \\ WindowsPowerShell \\Profile.ps1</span><span class="sxs-lookup"><span data-stu-id="9d165-130">$Home\\[My ]Documents\\WindowsPowerShell\\Profile.ps1</span></span> |
|<span data-ttu-id="9d165-131">현재 사용자, 현재 호스트</span><span class="sxs-lookup"><span data-stu-id="9d165-131">Current user, Current Host</span></span>|<span data-ttu-id="9d165-132">$Home \\ [My] 문서 \\ WindowsPowerShell</span><span class="sxs-lookup"><span data-stu-id="9d165-132">$Home\\[My ]Documents\\WindowsPowerShell</span></span>\\<br><span data-ttu-id="9d165-133">Microsoft.PowerShell_profile.ps1</span><span class="sxs-lookup"><span data-stu-id="9d165-133">Microsoft.PowerShell_profile.ps1</span></span> |

<span data-ttu-id="9d165-134">프로필 경로에는 다음 변수가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d165-134">The profile paths include the following variables:</span></span>

- <span data-ttu-id="9d165-135">`$PSHOME`PowerShell의 설치 디렉터리를 저장 하는 변수</span><span class="sxs-lookup"><span data-stu-id="9d165-135">The `$PSHOME` variable, which stores the installation directory for PowerShell</span></span>
- <span data-ttu-id="9d165-136">`$Home`현재 사용자의 홈 디렉터리를 저장 하는 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="9d165-136">The `$Home` variable, which stores the current user's home directory</span></span>

<span data-ttu-id="9d165-137">또한 PowerShell을 호스트 하는 다른 프로그램은 자신의 프로필을 지원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d165-137">In addition, other programs that host PowerShell can support their own profiles.</span></span> <span data-ttu-id="9d165-138">예를 들어 PowerShell ISE (통합 스크립팅 환경)는 다음과 같은 호스트 특정 프로필을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d165-138">For example, PowerShell Integrated Scripting Environment (ISE) supports the following host-specific profiles.</span></span>

|<span data-ttu-id="9d165-139">설명</span><span class="sxs-lookup"><span data-stu-id="9d165-139">Description</span></span>               | <span data-ttu-id="9d165-140">경로</span><span class="sxs-lookup"><span data-stu-id="9d165-140">Path</span></span>                                       |
|--------------------------|--------------------------------------------|
|<span data-ttu-id="9d165-141">모든 사용자, 현재 호스트</span><span class="sxs-lookup"><span data-stu-id="9d165-141">All users, Current Host</span></span>   |<span data-ttu-id="9d165-142">$PSHOME \\Microsoft.PowerShellISE_profile.ps1</span><span class="sxs-lookup"><span data-stu-id="9d165-142">$PSHOME\\Microsoft.PowerShellISE_profile.ps1</span></span>|
|<span data-ttu-id="9d165-143">현재 사용자, 현재 호스트</span><span class="sxs-lookup"><span data-stu-id="9d165-143">Current user, Current Host</span></span>|<span data-ttu-id="9d165-144">$Home \\ [My] 문서 \\ WindowsPowerShell</span><span class="sxs-lookup"><span data-stu-id="9d165-144">$Home\\[My ]Documents\\WindowsPowerShell</span></span>\\<br><span data-ttu-id="9d165-145">Microsoft.PowerShellISE_profile.ps1</span><span class="sxs-lookup"><span data-stu-id="9d165-145">Microsoft.PowerShellISE_profile.ps1</span></span> |

<span data-ttu-id="9d165-146">PowerShell 도움말에서 "CurrentUser, Current Host" 프로필은 가장 흔히 "PowerShell 프로필" 이라고 하는 프로필입니다.</span><span class="sxs-lookup"><span data-stu-id="9d165-146">In PowerShell Help, the "CurrentUser, Current Host" profile is the profile most often referred to as "your PowerShell profile".</span></span>

## <a name="the-profile-variable"></a><span data-ttu-id="9d165-147">$PROFILE 변수</span><span class="sxs-lookup"><span data-stu-id="9d165-147">The $PROFILE variable</span></span>

<span data-ttu-id="9d165-148">`$PROFILE`자동 변수는 현재 세션에서 사용할 수 있는 PowerShell 프로필에 대 한 경로를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d165-148">The `$PROFILE` automatic variable stores the paths to the PowerShell profiles that are available in the current session.</span></span>

<span data-ttu-id="9d165-149">프로필 경로를 보려면 변수 값을 표시 `$PROFILE` 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d165-149">To view a profile path, display the value of the `$PROFILE` variable.</span></span> <span data-ttu-id="9d165-150">`$PROFILE`명령에서 변수를 사용 하 여 경로를 나타낼 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d165-150">You can also use the `$PROFILE` variable in a command to represent a path.</span></span>

<span data-ttu-id="9d165-151">`$PROFILE`변수는 "현재 사용자, 현재 호스트" 프로필에 대 한 경로를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d165-151">The `$PROFILE` variable stores the path to the "Current User, Current Host" profile.</span></span> <span data-ttu-id="9d165-152">다른 프로필은 변수의 메모 속성에 저장 됩니다 `$PROFILE` .</span><span class="sxs-lookup"><span data-stu-id="9d165-152">The other profiles are saved in note properties of the `$PROFILE` variable.</span></span>

<span data-ttu-id="9d165-153">예를 들어 `$PROFILE` 변수는 Windows PowerShell 콘솔에서 다음 값을 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="9d165-153">For example, the `$PROFILE` variable has the following values in the Windows PowerShell console.</span></span>

|<span data-ttu-id="9d165-154">설명</span><span class="sxs-lookup"><span data-stu-id="9d165-154">Description</span></span>                |<span data-ttu-id="9d165-155">Name</span><span class="sxs-lookup"><span data-stu-id="9d165-155">Name</span></span>                              |
|---------------------------|----------------------------------|
|<span data-ttu-id="9d165-156">현재 사용자, 현재 호스트</span><span class="sxs-lookup"><span data-stu-id="9d165-156">Current User, Current Host</span></span> |`$PROFILE`                        |
|<span data-ttu-id="9d165-157">현재 사용자, 현재 호스트</span><span class="sxs-lookup"><span data-stu-id="9d165-157">Current User, Current Host</span></span> |`$PROFILE.CurrentUserCurrentHost` |
|<span data-ttu-id="9d165-158">현재 사용자, 모든 호스트</span><span class="sxs-lookup"><span data-stu-id="9d165-158">Current User, All Hosts</span></span>    |`$PROFILE.CurrentUserAllHosts`    |
|<span data-ttu-id="9d165-159">모든 사용자, 현재 호스트</span><span class="sxs-lookup"><span data-stu-id="9d165-159">All Users, Current Host</span></span>    |`$PROFILE.AllUsersCurrentHost`    |
|<span data-ttu-id="9d165-160">모든 사용자, 모든 호스트</span><span class="sxs-lookup"><span data-stu-id="9d165-160">All Users, All Hosts</span></span>       |`$PROFILE.AllUsersAllHosts`       |

<span data-ttu-id="9d165-161">변수의 값이 `$PROFILE` 각 사용자와 각 호스트 응용 프로그램에 대해 변경 되기 때문에 사용 하는 각 PowerShell 호스트 응용 프로그램에 프로필 변수의 값을 표시 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d165-161">Because the values of the `$PROFILE` variable change for each user and in each host application, ensure that you display the values of the profile variables in each PowerShell host application that you use.</span></span>

<span data-ttu-id="9d165-162">변수의 현재 값을 확인 하려면 `$PROFILE` 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d165-162">To see the current values of the `$PROFILE` variable, type:</span></span>

```powershell
$PROFILE | Get-Member -Type NoteProperty
```

<span data-ttu-id="9d165-163">`$PROFILE`많은 명령에서 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d165-163">You can use the `$PROFILE` variable in many commands.</span></span> <span data-ttu-id="9d165-164">예를 들어 다음 명령은 메모장에서 "현재 사용자, 현재 호스트" 프로필을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="9d165-164">For example, the following command opens the "Current User, Current Host" profile in Notepad:</span></span>

```powershell
notepad $PROFILE
```

<span data-ttu-id="9d165-165">다음 명령은 로컬 컴퓨터에서 "모든 사용자, 모든 호스트" 프로필을 만들었는지 여부를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d165-165">The following command determines whether an "All Users, All Hosts" profile has been created on the local computer:</span></span>

```powershell
Test-Path -Path $PROFILE.AllUsersAllHosts
```

## <a name="how-to-create-a-profile"></a><span data-ttu-id="9d165-166">프로필을 만드는 방법</span><span class="sxs-lookup"><span data-stu-id="9d165-166">How to create a profile</span></span>

<span data-ttu-id="9d165-167">PowerShell 프로필을 만들려면 다음 명령 형식을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d165-167">To create a PowerShell profile, use the following command format:</span></span>

```powershell
if (!(Test-Path -Path <profile-name>)) {
  New-Item -ItemType File -Path <profile-name> -Force
}
```

<span data-ttu-id="9d165-168">예를 들어 현재 PowerShell 호스트 응용 프로그램에서 현재 사용자에 대 한 프로필을 만들려면 다음 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d165-168">For example, to create a profile for the current user in the current PowerShell host application, use the following command:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE)) {
  New-Item -ItemType File -Path $PROFILE -Force
}
```

<span data-ttu-id="9d165-169">이 명령에서 `If` 문은 기존 프로필을 덮어쓰는 것을 방지 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d165-169">In this command, the `If` statement prevents you from overwriting an existing profile.</span></span> <span data-ttu-id="9d165-170">자리 표시자의 값을 \<profile-path\> 만들려는 프로필 파일의 경로로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="9d165-170">Replace the value of the \<profile-path\> placeholder with the path to the profile file that you want to create.</span></span>

> [!NOTE]
> <span data-ttu-id="9d165-171">Windows Vista 및 이후 버전의 Windows에서 "모든 사용자" 프로필을 만들려면 **관리자 권한으로 실행** 옵션을 사용 하 여 PowerShell을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d165-171">To create "All Users" profiles in Windows Vista and later versions of Windows, start PowerShell with the **Run as administrator** option.</span></span>

## <a name="how-to-edit-a-profile"></a><span data-ttu-id="9d165-172">프로필을 편집 하는 방법</span><span class="sxs-lookup"><span data-stu-id="9d165-172">How to edit a profile</span></span>

<span data-ttu-id="9d165-173">메모장과 같은 텍스트 편집기에서 PowerShell 프로필을 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d165-173">You can open any PowerShell profile in a text editor, such as Notepad.</span></span>

<span data-ttu-id="9d165-174">메모장의 현재 PowerShell 호스트 응용 프로그램에서 현재 사용자의 프로필을 열려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d165-174">To open the profile of the current user in the current PowerShell host application in Notepad, type:</span></span>

```powershell
notepad $PROFILE
```

<span data-ttu-id="9d165-175">다른 프로필을 열려면 프로필 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d165-175">To open other profiles, specify the profile name.</span></span> <span data-ttu-id="9d165-176">예를 들어 모든 호스트 응용 프로그램의 모든 사용자에 대 한 프로필을 열려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d165-176">For example, to open the profile for all the users of all the host applications, type:</span></span>

```powershell
notepad $PROFILE.AllUsersAllHosts
```

<span data-ttu-id="9d165-177">변경 내용을 적용 하려면 프로필 파일을 저장 한 다음 PowerShell을 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d165-177">To apply the changes, save the profile file, and then restart PowerShell.</span></span>

## <a name="how-to-choose-a-profile"></a><span data-ttu-id="9d165-178">프로필을 선택 하는 방법</span><span class="sxs-lookup"><span data-stu-id="9d165-178">How to choose a profile</span></span>

<span data-ttu-id="9d165-179">여러 호스트 응용 프로그램을 사용 하는 경우 모든 호스트 응용 프로그램에서 사용 하는 항목을 프로필에 저장 `$PROFILE.CurrentUserAllHosts` 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d165-179">If you use multiple host applications, put the items that you use in all the host applications into your `$PROFILE.CurrentUserAllHosts` profile.</span></span> <span data-ttu-id="9d165-180">호스트 응용 프로그램에 대 한 배경색을 설정 하는 명령 (예: 호스트 응용 프로그램에 해당 하는 프로필)에서 호스트 응용 프로그램과 관련 된 항목을 배치 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d165-180">Put items that are specific to a host application, such as a command that sets the background color for a host application, in a profile that is specific to that host application.</span></span>

<span data-ttu-id="9d165-181">여러 사용자를 위해 PowerShell을 사용자 지정 하는 관리자의 경우 다음 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="9d165-181">If you are an administrator who is customizing PowerShell for many users, follow these guidelines:</span></span>

- <span data-ttu-id="9d165-182">프로필에 공통 항목 저장 `$PROFILE.AllUsersAllHosts`</span><span class="sxs-lookup"><span data-stu-id="9d165-182">Store the common items in the `$PROFILE.AllUsersAllHosts` profile</span></span>
- <span data-ttu-id="9d165-183">호스트 응용 프로그램과 관련 된 프로필의 호스트 응용 프로그램과 관련 된 항목을 저장 `$PROFILE.AllUsersCurrentHost` 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d165-183">Store items that are specific to a host application in `$PROFILE.AllUsersCurrentHost` profiles that are specific to the host application</span></span>
- <span data-ttu-id="9d165-184">특정 사용자에 대 한 항목을 사용자 특정 프로필에 저장</span><span class="sxs-lookup"><span data-stu-id="9d165-184">Store items for particular users in the user-specific profiles</span></span>

<span data-ttu-id="9d165-185">PowerShell 프로필의 특별 한 구현에 대해서는 호스트 응용 프로그램 설명서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9d165-185">Be sure to check the host application documentation for any special implementation of PowerShell profiles.</span></span>

## <a name="how-to-use-a-profile"></a><span data-ttu-id="9d165-186">프로필을 사용 하는 방법</span><span class="sxs-lookup"><span data-stu-id="9d165-186">How to use a profile</span></span>

<span data-ttu-id="9d165-187">PowerShell에서 만드는 대부분의 항목과 대부분의 명령은 현재 세션에만 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9d165-187">Many of the items that you create in PowerShell and most commands that you run affect only the current session.</span></span> <span data-ttu-id="9d165-188">세션을 종료 하면 항목이 삭제 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d165-188">When you end the session, the items are deleted.</span></span>

<span data-ttu-id="9d165-189">세션 관련 명령 및 항목에는 변수, 기본 설정 변수, 별칭, 함수, 명령 ( [set-executionpolicy](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)제외) 및 세션에 추가 하는 PowerShell 모듈이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d165-189">The session-specific commands and items include variables, preference variables, aliases, functions, commands (except for [Set-ExecutionPolicy](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)), and PowerShell modules that you add to the session.</span></span>

<span data-ttu-id="9d165-190">이러한 항목을 저장 하 고 이후의 모든 세션에서 사용할 수 있게 하려면 PowerShell 프로필에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d165-190">To save these items and make them available in all future sessions, add them to a PowerShell profile.</span></span>

<span data-ttu-id="9d165-191">프로필의 또 다른 일반적인 용도는 자주 사용 하는 함수, 별칭 및 변수를 저장 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="9d165-191">Another common use for profiles is to save frequently-used functions, aliases, and variables.</span></span> <span data-ttu-id="9d165-192">프로필에 항목을 저장 하는 경우 해당 항목을 다시 만들지 않고 해당 세션에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d165-192">When you save the items in a profile, you can use them in any applicable session without recreating them.</span></span>

## <a name="how-to-start-a-profile"></a><span data-ttu-id="9d165-193">프로필을 시작 하는 방법</span><span class="sxs-lookup"><span data-stu-id="9d165-193">How to start a profile</span></span>

<span data-ttu-id="9d165-194">프로필 파일을 열면 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d165-194">When you open the profile file, it is blank.</span></span> <span data-ttu-id="9d165-195">그러나 자주 사용 하는 변수, 별칭 및 명령으로 채울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d165-195">However, you can fill it with the variables, aliases, and commands that you use frequently.</span></span>

<span data-ttu-id="9d165-196">다음은 시작 하기 위한 몇 가지 제안 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="9d165-196">Here are a few suggestions to get you started.</span></span>

### <a name="add-commands-that-make-it-easy-to-open-your-profile"></a><span data-ttu-id="9d165-197">프로필을 쉽게 열 수 있도록 하는 명령 추가</span><span class="sxs-lookup"><span data-stu-id="9d165-197">Add commands that make it easy to open your profile</span></span>

<span data-ttu-id="9d165-198">"현재 사용자, 현재 호스트" 프로필 이외의 프로필을 사용 하는 경우 특히 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d165-198">This is especially useful if you use a profile other than the "Current User, Current Host" profile.</span></span> <span data-ttu-id="9d165-199">예를 들어 다음 명령을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d165-199">For example, add the following command:</span></span>

```powershell
function Pro {notepad $PROFILE.CurrentUserAllHosts}
```

### <a name="add-a-function-that-lists-the-aliases-for-any-cmdlet"></a><span data-ttu-id="9d165-200">모든 cmdlet에 대 한 별칭을 나열 하는 함수를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d165-200">Add a function that lists the aliases for any cmdlet</span></span>

```powershell
function Get-CmdletAlias ($cmdletname) {
  Get-Alias |
    Where-Object -FilterScript {$_.Definition -like "$cmdletname"} |
      Format-Table -Property Definition, Name -AutoSize
}
```

### <a name="customize-your-console"></a><span data-ttu-id="9d165-201">콘솔 사용자 지정</span><span class="sxs-lookup"><span data-stu-id="9d165-201">Customize your console</span></span>

```powershell
function Color-Console {
  $Host.ui.rawui.backgroundcolor = "white"
  $Host.ui.rawui.foregroundcolor = "black"
  $hosttime = (Get-ChildItem -Path $PSHOME\PowerShell.exe).CreationTime
  $hostversion="$($Host.Version.Major)`.$($Host.Version.Minor)"
  $Host.UI.RawUI.WindowTitle = "PowerShell $hostversion ($hosttime)"
  Clear-Host
}
Color-Console
```

### <a name="add-a-customized-powershell-prompt"></a><span data-ttu-id="9d165-202">사용자 지정 된 PowerShell 프롬프트 추가</span><span class="sxs-lookup"><span data-stu-id="9d165-202">Add a customized PowerShell prompt</span></span>

```powershell
function Prompt
{
$env:COMPUTERNAME + "\" + (Get-Location) + "> "
}
```

<span data-ttu-id="9d165-203">PowerShell 프롬프트에 대 한 자세한 내용은 [about_Prompts](about_Prompts.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9d165-203">For more information about the PowerShell prompt, see [about_Prompts](about_Prompts.md).</span></span>

## <a name="the-noprofile-parameter"></a><span data-ttu-id="9d165-204">NoProfile 매개 변수</span><span class="sxs-lookup"><span data-stu-id="9d165-204">The NoProfile parameter</span></span>

<span data-ttu-id="9d165-205">프로필 없이 PowerShell을 시작 하려면 PowerShell을 시작 하는 프로그램인 **PowerShell.exe** 의 **noprofile** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d165-205">To start PowerShell without profiles, use the **NoProfile** parameter of **PowerShell.exe**, the program that starts PowerShell.</span></span>

<span data-ttu-id="9d165-206">시작 하려면 PowerShell을 시작할 수 있는 프로그램 (예: Cmd.exe 또는 PowerShell)을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="9d165-206">To begin, open a program that can start PowerShell, such as Cmd.exe or PowerShell itself.</span></span> <span data-ttu-id="9d165-207">Windows에서 실행 대화 상자를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d165-207">You can also use the Run dialog box in Windows.</span></span>

<span data-ttu-id="9d165-208">유형:</span><span class="sxs-lookup"><span data-stu-id="9d165-208">Type:</span></span>

```
PowerShell -NoProfile
```

<span data-ttu-id="9d165-209">PowerShell.exe 매개 변수의 전체 목록을 보려면 다음을 입력 하십시오.</span><span class="sxs-lookup"><span data-stu-id="9d165-209">For a complete list of the parameters of PowerShell.exe, type:</span></span>

```
PowerShell -?
```

## <a name="profiles-and-execution-policy"></a><span data-ttu-id="9d165-210">프로필 및 실행 정책</span><span class="sxs-lookup"><span data-stu-id="9d165-210">Profiles and Execution Policy</span></span>

<span data-ttu-id="9d165-211">PowerShell 실행 정책은 프로필을 포함 하 여 스크립트를 실행 하 고 구성 파일을 로드할 수 있는지 여부를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d165-211">The PowerShell execution policy determines, in part, whether you can run scripts and load configuration files, including the profiles.</span></span> <span data-ttu-id="9d165-212">**제한** 된 실행 정책이 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="9d165-212">The **Restricted** execution policy is the default.</span></span> <span data-ttu-id="9d165-213">프로필을 포함 하 여 모든 스크립트가 실행 되지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d165-213">It prevents all scripts from running, including the profiles.</span></span> <span data-ttu-id="9d165-214">"제한 됨" 정책을 사용 하는 경우 프로필이 실행 되지 않으며 해당 콘텐츠가 적용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9d165-214">If you use the "Restricted" policy, the profile does not run, and its contents are not applied.</span></span>

<span data-ttu-id="9d165-215">`Set-ExecutionPolicy`명령은 실행 정책을 설정 하 고 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d165-215">A `Set-ExecutionPolicy` command sets and changes your execution policy.</span></span> <span data-ttu-id="9d165-216">이 값은 레지스트리에 저장 되기 때문에 모든 PowerShell 세션에서 적용 되는 몇 가지 명령 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="9d165-216">It is one of the few commands that applies in all PowerShell sessions because the value is saved in the registry.</span></span> <span data-ttu-id="9d165-217">콘솔을 열 때 설정할 필요는 없으며, `Set-ExecutionPolicy` 프로필에 명령을 저장할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9d165-217">You do not have to set it when you open the console, and you do not have to store a `Set-ExecutionPolicy` command in your profile.</span></span>

## <a name="profiles-and-remote-sessions"></a><span data-ttu-id="9d165-218">프로필 및 원격 세션</span><span class="sxs-lookup"><span data-stu-id="9d165-218">Profiles and remote sessions</span></span>

<span data-ttu-id="9d165-219">PowerShell 프로필은 원격 세션에서 자동으로 실행 되지 않으므로 프로필이 추가 하는 명령이 원격 세션에 존재 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9d165-219">PowerShell profiles are not run automatically in remote sessions, so the commands that the profiles add are not present in the remote session.</span></span> <span data-ttu-id="9d165-220">또한 `$PROFILE` 자동 변수는 원격 세션에서 채워지지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9d165-220">In addition, the `$PROFILE` automatic variable is not populated in remote sessions.</span></span>

<span data-ttu-id="9d165-221">세션에서 프로필을 실행 하려면 [Invoke Command](xref:Microsoft.PowerShell.Core.Invoke-Command) cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d165-221">To run a profile in a session, use the [Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command) cmdlet.</span></span>

<span data-ttu-id="9d165-222">예를 들어 다음 명령은의 세션에서 로컬 컴퓨터의 "현재 사용자, 현재 호스트" 프로필을 실행 합니다 `$s` .</span><span class="sxs-lookup"><span data-stu-id="9d165-222">For example, the following command runs the "Current user, Current Host" profile from the local computer in the session in `$s`.</span></span>

```powershell
Invoke-Command -Session $s -FilePath $PROFILE
```

<span data-ttu-id="9d165-223">다음 명령은의 세션에 있는 원격 컴퓨터에서 "현재 사용자, 현재 호스트" 프로필을 실행 합니다 `$s` .</span><span class="sxs-lookup"><span data-stu-id="9d165-223">The following command runs the "Current user, Current Host" profile from the remote computer in the session in `$s`.</span></span> <span data-ttu-id="9d165-224">`$PROFILE`변수가 채워지지 않으므로 명령은 프로필에 대 한 명시적 경로를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d165-224">Because the `$PROFILE` variable is not populated, the command uses the explicit path to the profile.</span></span> <span data-ttu-id="9d165-225">사용자의 범위가 아니라 원격 컴퓨터의 현재 범위에서 프로필이 실행 되도록 점 소싱 연산자를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d165-225">We use dot sourcing operator so that the profile executes in the current scope on the remote computer and not in its own scope.</span></span>

```powershell
Invoke-Command -Session $s -ScriptBlock {
  . "$HOME\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1"
}
```

<span data-ttu-id="9d165-226">이 명령을 실행 한 후 프로필을 세션에 추가 하는 명령은에서 사용할 수 있습니다 `$s` .</span><span class="sxs-lookup"><span data-stu-id="9d165-226">After running this command, the commands that the profile adds to the session are available in `$s`.</span></span>

## <a name="see-also"></a><span data-ttu-id="9d165-227">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9d165-227">See Also</span></span>

[<span data-ttu-id="9d165-228">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="9d165-228">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)

[<span data-ttu-id="9d165-229">about_Functions</span><span class="sxs-lookup"><span data-stu-id="9d165-229">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="9d165-230">about_Prompts</span><span class="sxs-lookup"><span data-stu-id="9d165-230">about_Prompts</span></span>](about_Prompts.md)

[<span data-ttu-id="9d165-231">about_Execution_Policies</span><span class="sxs-lookup"><span data-stu-id="9d165-231">about_Execution_Policies</span></span>](about_Execution_Policies.md)

[<span data-ttu-id="9d165-232">about_Signing</span><span class="sxs-lookup"><span data-stu-id="9d165-232">about_Signing</span></span>](about_Signing.md)

[<span data-ttu-id="9d165-233">about_Remote</span><span class="sxs-lookup"><span data-stu-id="9d165-233">about_Remote</span></span>](about_Remote.md)

[<span data-ttu-id="9d165-234">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="9d165-234">about_Scopes</span></span>](about_Scopes.md)

[<span data-ttu-id="9d165-235">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="9d165-235">Set-ExecutionPolicy</span></span>](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)
