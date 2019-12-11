---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Windows PowerShell ISE에서 프로필을 사용하는 방법
ms.openlocfilehash: 28354f39aaaa577cec69c1b3f62cfe16ef091218
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030614"
---
# <a name="how-to-use-profiles-in-windows-powershell-ise"></a><span data-ttu-id="c69b5-103">Windows PowerShell ISE에서 프로필을 사용하는 방법</span><span class="sxs-lookup"><span data-stu-id="c69b5-103">How to Use Profiles in Windows PowerShell ISE</span></span>

<span data-ttu-id="c69b5-104">이 항목에서는 Windows PowerShell® ISE(통합 스크립팅 환경)에서 프로필을 사용하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c69b5-104">This topic explains how to use Profiles in Windows PowerShell® Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="c69b5-105">이 섹션의 작업을 수행하기 전에 [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles)를 검토하거나, 콘솔 창에서 `Get-Help about_Profiles`를 입력하고 **Enter** 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="c69b5-105">We recommend that before performing the tasks in this section, you review [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles), or in the Console Pane, type, `Get-Help about_Profiles` and press **ENTER**.</span></span>

<span data-ttu-id="c69b5-106">프로필은 새 세션을 시작할 때 자동으로 실행되는 Windows PowerShell ISE 스크립트입니다.</span><span class="sxs-lookup"><span data-stu-id="c69b5-106">A profile is a Windows PowerShell ISE script that runs automatically when you start a new session.</span></span>  <span data-ttu-id="c69b5-107">Windows PowerShell ISE용 Windows PowerShell 프로필을 하나 이상 만든 다음 이 프로필을 사용하여 제공하려는 변수, 별칭, 함수, 색 및 글꼴 기본 설정으로 Windows PowerShell 또는 Windows PowerShell ISE 환경을 구성하고 사용하도록 준비할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c69b5-107">You can create one or more Windows PowerShell profiles for Windows PowerShell ISE and use them to add the configure the Windows PowerShell or Windows PowerShell ISE environment, preparing it for your use, with variables, aliases, functions, and color and font preferences that you want available.</span></span> <span data-ttu-id="c69b5-108">프로필은 시작하는 모든 Windows PowerShell ISE 세션에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c69b5-108">A profile affects every Windows PowerShell ISE session that you start.</span></span>

> [!NOTE]
> <span data-ttu-id="c69b5-109">Windows PowerShell 실행 정책은 스크립트를 실행하고 프로필을 로드할 수 있는지 여부를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="c69b5-109">The Windows PowerShell execution policy determines whether you can run scripts and load a profile.</span></span> <span data-ttu-id="c69b5-110">기본 실행 정책인 "Restricted"는 프로필을 비롯한 모든 스크립트가 실행되지 못하게 합니다.</span><span class="sxs-lookup"><span data-stu-id="c69b5-110">The default execution policy, “Restricted,” prevents all scripts from running, including profiles.</span></span> <span data-ttu-id="c69b5-111">"Restricted" 정책을 사용하는 경우 프로필을 로드할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c69b5-111">If you use the “Restricted” policy, the profile cannot load.</span></span> <span data-ttu-id="c69b5-112">실행 정책에 대한 자세한 내용은 [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c69b5-112">For more information about execution policy, see [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span></span>

## <a name="selecting-a-profile-to-use-in-the-windows-powershell-ise"></a><span data-ttu-id="c69b5-113">Windows PowerShell ISE에서 사용할 프로필 선택</span><span class="sxs-lookup"><span data-stu-id="c69b5-113">Selecting a profile to use in the Windows PowerShell ISE</span></span>

<span data-ttu-id="c69b5-114">Windows PowerShell ISE는 현재 사용자와 모든 사용자의 프로필을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="c69b5-114">Windows PowerShell ISE supports profiles for the current user and all users.</span></span> <span data-ttu-id="c69b5-115">또한 모든 호스트에 적용되는 Windows PowerShell 프로필을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="c69b5-115">It also supports the Windows PowerShell profiles that apply to all hosts.</span></span>

<span data-ttu-id="c69b5-116">사용하는 프로필은 Windows PowerShell 및 Windows PowerShell ISE를 사용하는 방법에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="c69b5-116">The profile that you use is determined by how you use Windows PowerShell and Windows PowerShell ISE.</span></span>

- <span data-ttu-id="c69b5-117">Windows PowerShell ISE만 사용하여 Windows PowerShell을 실행하는 경우 모든 항목을 ISE 관련 프로필(예: Windows PowerShell ISE용 CurrentUserCurrentHost 프로필 또는 Windows PowerShell ISE용 AllUsersCurrentHost 프로필) 중 하나에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="c69b5-117">If you use only Windows PowerShell ISE to run Windows PowerShell, then save all your items in one of the ISE-specific profiles, such as the CurrentUserCurrentHost profile for Windows PowerShell ISE or the AllUsersCurrentHost profile for Windows PowerShell ISE.</span></span>

- <span data-ttu-id="c69b5-118">여러 호스트 프로그램을 사용하여 Windows PowerShell을 실행하는 경우에는 함수, 별칭, 변수 및 명령은 모든 호스트 프로그램에 영향을 주는 프로필(예: CurrentUserAllHosts 또는 AllUsersAllHosts 프로필)에 저장하고 색 및 글꼴 사용자 지정과 같은 ISE 관련 기능은 Windows PowerShell ISE용 CurrentUserCurrentHost 프로필 또는 Windows PowerShell ISE용 AllUsersCurrentHost 프로필에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="c69b5-118">If you use multiple host programs to run Windows PowerShell, save your functions, aliases, variables, and commands in a profile that affects all host programs, such as the CurrentUserAllHosts or the AllUsersAllHosts profile, and save ISE-specific features, like color and font customization in the CurrentUserCurrentHost profile for Windows PowerShell ISE profile or the AllUsersCurrentHost profile for Windows PowerShell ISE.</span></span>

<span data-ttu-id="c69b5-119">다음은 Windows PowerShell ISE에서 만들고 사용할 수 있는 프로필입니다.</span><span class="sxs-lookup"><span data-stu-id="c69b5-119">The following are profiles that can be created and used in Windows PowerShell ISE.</span></span> <span data-ttu-id="c69b5-120">각 프로필은 고유한 특정 경로에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="c69b5-120">Each profile is saved to its own specific path.</span></span>

| <span data-ttu-id="c69b5-121">프로필 유형</span><span class="sxs-lookup"><span data-stu-id="c69b5-121">Profile Type</span></span> | <span data-ttu-id="c69b5-122">프로필 경로</span><span class="sxs-lookup"><span data-stu-id="c69b5-122">Profile Path</span></span> |
| --- | --- |
| <span data-ttu-id="c69b5-123">**현재 사용자, PowerShell ISE**</span><span class="sxs-lookup"><span data-stu-id="c69b5-123">**Current user, PowerShell ISE**</span></span>| <span data-ttu-id="c69b5-124">`$PROFILE.CurrentUserCurrentHost` 또는 `$PROFILE`</span><span class="sxs-lookup"><span data-stu-id="c69b5-124">`$PROFILE.CurrentUserCurrentHost`, or `$PROFILE`</span></span> |
| <span data-ttu-id="c69b5-125">**모든 사용자, PowerShell ISE**</span><span class="sxs-lookup"><span data-stu-id="c69b5-125">**All users, PowerShell ISE**</span></span>| `$PROFILE.AllUsersCurrentHost` |
| <span data-ttu-id="c69b5-126">**현재 사용자, 모든 호스트**</span><span class="sxs-lookup"><span data-stu-id="c69b5-126">**Current user, All hosts**</span></span>| `$PROFILE.CurrentUserAllHosts` |
| <span data-ttu-id="c69b5-127">**모든 사용자, 모든 호스트**</span><span class="sxs-lookup"><span data-stu-id="c69b5-127">**All users, All hosts**</span></span> | `$PROFILE.AllUsersAllHosts` |

## <a name="to-create-a-new-profile"></a><span data-ttu-id="c69b5-128">새 프로필을 만들려면</span><span class="sxs-lookup"><span data-stu-id="c69b5-128">To create a new profile</span></span>

<span data-ttu-id="c69b5-129">새 "현재 사용자, Windows PowerShell ISE" 프로필을 만들려면 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c69b5-129">To create a new “Current user, Windows PowerShell ISE” profile, run this command:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE ))
{ New-Item -Type File -Path $PROFILE -Force }
```

<span data-ttu-id="c69b5-130">새 "모든 사용자, Windows PowerShell ISE" 프로필을 만들려면 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c69b5-130">To create a new “All users, Windows PowerShell ISE” profile, run this command:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE.AllUsersCurrentHost))
{ New-Item -Type File -Path $PROFILE.AllUsersCurrentHost -Force }
```

<span data-ttu-id="c69b5-131">새 "현재 사용자, 모든 호스트" 프로필을 만들려면 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c69b5-131">To create a new “Current user, All Hosts” profile, run this command:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE.CurrentUserAllHosts))
{ New-Item -Type File -Path $PROFILE.CurrentUserAllHosts -Force }
```

<span data-ttu-id="c69b5-132">새 "모든 사용자, 모든 호스트" 프로필을 만들려면 다음과 같이 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c69b5-132">To create a new “All users, All Hosts” profile, type:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE.AllUsersAllHosts))
{ New-Item -Type File -Path $PROFILE.AllUsersAllHosts -Force }
```

## <a name="to-edit-a-profile"></a><span data-ttu-id="c69b5-133">프로필을 편집하려면</span><span class="sxs-lookup"><span data-stu-id="c69b5-133">To edit a profile</span></span>

1. <span data-ttu-id="c69b5-134">프로필을 열려면 편집할 프로필을 지정하는 변수와 함께 psedit 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c69b5-134">To open the profile, run the command psedit with the variable that specifies the profile you want to edit.</span></span> <span data-ttu-id="c69b5-135">예를 들어 "현재 사용자, Windows PowerShell ISE" 프로필을 열려면 다음과 같이 입력합니다. `psEdit $PROFILE`</span><span class="sxs-lookup"><span data-stu-id="c69b5-135">For example, to open the “Current user, Windows PowerShell ISE” profile, type: `psEdit $PROFILE`</span></span>

2. <span data-ttu-id="c69b5-136">프로필에 몇 개의 항목을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="c69b5-136">Add some items to your profile.</span></span> <span data-ttu-id="c69b5-137">다음은 시작하기 위한 몇 가지 예입니다.</span><span class="sxs-lookup"><span data-stu-id="c69b5-137">The following are a few examples to get you started:</span></span>

   - <span data-ttu-id="c69b5-138">콘솔 창의 기본 배경색을 파란색으로 변경하려면 프로필 파일에서 다음과 같이 입력합니다. `$psISE.Options.OutputPaneBackground = 'blue'`.</span><span class="sxs-lookup"><span data-stu-id="c69b5-138">To change the default background color of the Console Pane to blue, in the profile file type: `$psISE.Options.OutputPaneBackground = 'blue'` .</span></span> <span data-ttu-id="c69b5-139">$psISE 변수에 대한 자세한 내용은 [Windows PowerShell ISE 개체 모델 참조](object-model/The-ISE-Object-Model-Hierarchy.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c69b5-139">For more information about the $psISE variable, see [Windows PowerShell ISE Object Model Reference](object-model/The-ISE-Object-Model-Hierarchy.md).</span></span>

   - <span data-ttu-id="c69b5-140">글꼴 크기를 20으로 변경하려면 프로필 파일에서 다음과 같이 입력합니다. `$psISE.Options.FontSize =20`</span><span class="sxs-lookup"><span data-stu-id="c69b5-140">To change font size to 20, in the profile file type: `$psISE.Options.FontSize =20`</span></span>

3. <span data-ttu-id="c69b5-141">프로필 파일을 저장하려면 **파일** 메뉴에서 **저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c69b5-141">To save your profile file, on the **File** menu, click **Save**.</span></span> <span data-ttu-id="c69b5-142">다음에 Windows PowerShell ISE를 열면 사용자 지정이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c69b5-142">Next time you open the Windows PowerShell ISE, your customizations are applied.</span></span>

## <a name="see-also"></a><span data-ttu-id="c69b5-143">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c69b5-143">See Also</span></span>

- [<span data-ttu-id="c69b5-144">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="c69b5-144">about_Profiles</span></span>](/powershell/module/microsoft.powershell.core/about/about_profiles)
- [<span data-ttu-id="c69b5-145">Windows PowerShell ISE 소개</span><span class="sxs-lookup"><span data-stu-id="c69b5-145">Introducing the Windows PowerShell ISE</span></span>](Introducing-the-Windows-PowerShell-ISE.md)
