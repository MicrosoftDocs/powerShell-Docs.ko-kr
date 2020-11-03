---
description: 세션 구성 ("끝점"이 라고도 함)에서 세션 구성을 사용 하는 세션 환경을 정의 하는 데 사용 되는 세션 구성 파일에 대해 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_session_configuration_files?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Session_Configuration_Files
ms.openlocfilehash: 113c068022f37b22cbcc5dae61a6a5edf26187d8
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93220593"
---
# <a name="about-session-configuration-files"></a><span data-ttu-id="1e568-104">세션 구성 파일 정보</span><span class="sxs-lookup"><span data-stu-id="1e568-104">About Session Configuration Files</span></span>

## <a name="short-description"></a><span data-ttu-id="1e568-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="1e568-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="1e568-106">세션 구성 ("끝점"이 라고도 함)에서 세션 구성을 사용 하는 세션 환경을 정의 하는 데 사용 되는 세션 구성 파일에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e568-106">Describes session configuration files, which are used in a session configuration (also known as an "endpoint") to define the environment of sessions that use the session configuration.</span></span>

## <a name="long-description"></a><span data-ttu-id="1e568-107">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="1e568-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="1e568-108">"세션 구성 파일"은 세션 구성 속성 및 값의 해시 테이블을 포함 하는 .psc 파일 이름 확장명을 포함 하는 텍스트 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="1e568-108">A "session configuration file" is a text file with a .pssc file name extension that contains a hash table of session configuration properties and values.</span></span> <span data-ttu-id="1e568-109">세션 구성 파일을 사용 하 여 세션 구성의 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e568-109">You can use a session configuration file to set the properties of a session configuration.</span></span> <span data-ttu-id="1e568-110">이렇게 하면 해당 세션 구성을 사용 하는 PowerShell 세션의 환경이 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e568-110">Doing so defines the environment of any PowerShell sessions that use that session configuration.</span></span>

<span data-ttu-id="1e568-111">세션 구성 파일을 사용 하면 복잡 한 c # 어셈블리나 스크립트를 사용 하지 않고 사용자 지정 세션 구성을 쉽게 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e568-111">Session configuration files make it easy to create custom session configurations without using complex C# assemblies or scripts.</span></span>

<span data-ttu-id="1e568-112">"세션 구성" 또는 "엔드포인트"는 사용자가 컴퓨터에서 세션을 만들 수 있는 작업을 결정 하는 로컬 컴퓨터 설정의 컬렉션입니다. 사용자가 해당 세션에서 실행할 수 있는 명령 세션을 권한 있는 가상 계정으로 실행할지 여부를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e568-112">A "session configuration" or "endpoint" is a collection of local computer settings that determine such things as which users can create sessions on the computer; which commands users can run in those sessions; and whether the session should run as a privileged virtual account.</span></span> <span data-ttu-id="1e568-113">세션 구성에 대 한 자세한 내용은 [about_Session_Configurations](about_Session_Configurations.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1e568-113">For more information about session configurations, see [about_Session_Configurations](about_Session_Configurations.md).</span></span>

<span data-ttu-id="1e568-114">세션 구성은 Windows PowerShell 2.0에서 도입 되었으며 세션 구성 파일은 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1e568-114">Session configurations were introduced in Windows PowerShell 2.0, and session configuration files were introduced in Windows PowerShell 3.0.</span></span> <span data-ttu-id="1e568-115">세션 구성에 세션 구성 파일을 포함 하려면 Windows PowerShell 3.0을 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e568-115">You must use Windows PowerShell 3.0 to include a session configuration file in a session configuration.</span></span> <span data-ttu-id="1e568-116">그러나 Windows PowerShell 2.0 (이상)의 사용자는 세션 구성의 설정에 영향을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="1e568-116">However, users of Windows PowerShell 2.0 (and later) are affected by the settings in the session configuration.</span></span>

## <a name="creating-custom-sessions"></a><span data-ttu-id="1e568-117">사용자 지정 세션 만들기</span><span class="sxs-lookup"><span data-stu-id="1e568-117">Creating Custom Sessions</span></span>

<span data-ttu-id="1e568-118">세션 구성에서 세션 속성을 지정 하 여 PowerShell 세션의 여러 기능을 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e568-118">You can customize many features of a PowerShell session by specifying session properties in a session configuration.</span></span> <span data-ttu-id="1e568-119">사용자 지정 runspace를 정의 하는 c # 프로그램을 작성 하 여 세션을 사용자 지정 하거나 세션 구성 파일을 사용 하 여 세션 구성을 사용 하 여 만든 세션의 속성을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e568-119">You can customize a session by writing a C# program that defines a custom runspace, or you can use a session configuration file to define the properties of sessions created by using the session configuration.</span></span> <span data-ttu-id="1e568-120">일반적으로 c # 프로그램을 작성 하는 것 보다 세션 구성 파일을 사용 하는 것이 더 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="1e568-120">As a general rule, it is easier to use the session configuration file than to write a C# program.</span></span>

<span data-ttu-id="1e568-121">세션 구성 파일을 사용 하 여 신뢰할 수 있는 사용자에 대해 완전히 작동 하는 세션과 같은 항목을 만들 수 있습니다. 최소한의 액세스를 허용 하는 잠긴 세션 특별히 설계 되었으며 해당 작업에 필요한 모듈만 포함 하는 세션 권한 없는 사용자가 권한 있는 계정으로 특정 명령만 실행할 수 있는 세션입니다.</span><span class="sxs-lookup"><span data-stu-id="1e568-121">You can use a session configuration file to create items such as fully-functioning sessions for highly trusted users; locked-down sessions that allow minimal access; sessions designed for particular and that contain only the modules required for those tasks; and sessions where unprivileged users can only run specific commands as a privileged account.</span></span>

<span data-ttu-id="1e568-122">그 외에도 세션의 사용자가 스크립트 블록 등의 PowerShell 언어 요소를 사용할 수 있는지 여부 또는 명령을 실행할 수 있는지 여부를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e568-122">In addition to that, you can manage whether users of the session can use PowerShell language elements such as script blocks, or whether they can only run commands.</span></span> <span data-ttu-id="1e568-123">세션에서 실행할 수 있는 PowerShell 사용자의 버전을 관리할 수 있습니다. 세션으로 가져올 모듈을 관리 합니다. 그리고 사용자가 실행할 수 있는 cmdlet, 함수 및 별칭 세션을 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e568-123">You can manage the version of PowerShell users can run in the session; manage which modules are imported into the session; and manage which cmdlets, functions, and aliases session users can run.</span></span> <span data-ttu-id="1e568-124">RoleDefinitions 필드를 사용 하는 경우 그룹 멤버 자격을 기반으로 세션에서 사용자에 게 다른 기능을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e568-124">When using the RoleDefinitions field, you can give users different capabilities in the session based on group membership.</span></span>

<span data-ttu-id="1e568-125">RoleDefinitions이 값을 정의 하는 방법에 대 한 자세한 내용은 New-PSRoleCapabilityFile Cmdlet에 대 한 도움말 항목을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1e568-125">For more information about RoleDefinitions and how to define this Value, see the help topic for the New-PSRoleCapabilityFile Cmdlet.</span></span>

## <a name="creating-a-session-configuration-file"></a><span data-ttu-id="1e568-126">세션 구성 파일 만들기</span><span class="sxs-lookup"><span data-stu-id="1e568-126">Creating a Session Configuration File</span></span>

<span data-ttu-id="1e568-127">세션 구성 파일을 만드는 가장 쉬운 방법은 New-PSSessionConfigurationFile cmdlet을 사용 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="1e568-127">The easiest way to create a session configuration file is by using the New-PSSessionConfigurationFile cmdlet.</span></span> <span data-ttu-id="1e568-128">이 cmdlet은 올바른 구문과 형식을 사용 하며 많은 구성 파일 속성 값을 자동으로 확인 하는 파일을 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e568-128">This cmdlet generates a file that uses the correct syntax and format, and that automatically verifies many of the configuration file property values.</span></span>

<span data-ttu-id="1e568-129">세션 구성 파일에서 설정할 수 있는 속성에 대 한 자세한 설명은 New-PSSessionConfigurationFile cmdlet에 대 한 도움말 항목을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1e568-129">For detailed descriptions of the properties that you can set in a session configuration file, see the help topic for the New-PSSessionConfigurationFile cmdlet.</span></span>

<span data-ttu-id="1e568-130">다음 명령은 기본값을 사용 하는 세션 구성 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1e568-130">The following command creates a session configuration file that uses the default values.</span></span> <span data-ttu-id="1e568-131">파일 경로를 지정 하는 경로 매개 변수 이외의 매개 변수가 포함 되어 있지 않기 때문에 결과 구성 파일은 기본값을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e568-131">The resulting configuration file uses only the default values because no parameters other than the Path parameter (which specifies the file path) are included:</span></span>

```powershell
New-PSSessionConfigurationFile -Path .\Defaults.pssc
```

<span data-ttu-id="1e568-132">기본 텍스트 편집기에서 새 구성 파일을 보려면 다음 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e568-132">To view the new configuration file in your default text editor, use the following command:</span></span>

```powershell
Invoke-Item -Path .\Defaults.pssc
```

<span data-ttu-id="1e568-133">사용자가 명령을 실행할 수 있지만 PowerShell 언어의 다른 요소를 사용 하지 않는 세션에 대 한 세션 구성을 만들려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e568-133">To create a session configuration for sessions in which user can run commands, but not use other elements of the PowerShell language, type:</span></span>

```powershell
New-PSSessionConfigurationFile -LanguageMode NoLanguage
-Path .\NoLanguage.pssc
```

<span data-ttu-id="1e568-134">이전 명령에서 LanguageMode 매개 변수를 NoLanguage로 설정 하면 사용자가 스크립트를 작성 하거나 실행 하거나 변수를 사용 하는 등의 작업을 수행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1e568-134">In the preceding command, setting the LanguageMode parameter to NoLanguage prevents users from doing such things as writing or running scripts, or using variables.</span></span>

<span data-ttu-id="1e568-135">사용자가 Get cmdlet만 사용할 수 있는 세션에 대 한 세션 구성을 만들려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e568-135">To create a session configuration for sessions in which users can use only Get cmdlets, type:</span></span>

```powershell
New-PSSessionConfigurationFile -VisibleCmdlets Get-*
-Path .\GetSessions.pssc
```

<span data-ttu-id="1e568-136">앞의 예제에서 VisibleCmdlets 매개 변수를 Get-\*로 설정 하면 이름이 문자열 값 "Get-"으로 시작 하는 cmdlet으로 제한 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e568-136">In the preceding example, setting the VisibleCmdlets parameter to Get-\* limits users to cmdlets that have names that start with the string value "Get-".</span></span>

<span data-ttu-id="1e568-137">사용자의 자격 증명 대신 권한 있는 가상 계정으로 실행 되는 세션에 대 한 세션 구성을 만들려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e568-137">To create a session configuration for sessions that run under a privileged virtual account instead of the user's credentials, type:</span></span>

```powershell
New-PSSessionConfigurationFile -RunAsVirtualAccount
-Path .\VirtualAccount.pssc
```

<span data-ttu-id="1e568-138">사용자에 게 표시 되는 명령이 역할 기능 파일에 지정 된 세션에 대 한 세션 구성을 만들려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e568-138">To create a session configuration for sessions in which the commands visible to the user are specified in a role capabilities file, type:</span></span>

```powershell
New-PSSessionConfigurationFile -RoleDefinitions
@{ 'CONTOSO\User' = @{ RoleCapabilities = 'Maintenance' }}
-Path .\Maintenance.pssc
```

### <a name="using-a-session-configuration-file"></a><span data-ttu-id="1e568-139">세션 구성 파일 사용</span><span class="sxs-lookup"><span data-stu-id="1e568-139">Using a Session Configuration File</span></span>

<span data-ttu-id="1e568-140">세션 구성 파일을 포함할 수 있습니다. 세션 구성 파일을 추가 하거나 추가 하 여 나중에 세션 구성에 파일을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e568-140">You can include a session configuration file when you create a session configuration or add you can add a file to the session configuration at a later time.</span></span>

<span data-ttu-id="1e568-141">세션 구성을 만들 때 세션 구성 파일을 포함 하려면 Register-PSSessionConfiguration cmdlet의 Path 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e568-141">To include a session configuration file when creating a session configuration, use the Path parameter of the Register-PSSessionConfiguration cmdlet.</span></span>

<span data-ttu-id="1e568-142">예를 들어 다음 명령은 nolanguage. pssc 파일을 사용 하 여 NoLanguage 세션 구성을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1e568-142">For example, the following command uses the NoLanguage.pssc file when it creates a NoLanguage session configuration.</span></span>

```powershell
Register-PSSessionConfiguration -Name NoLanguage
-Path .\NoLanguage.pssc
```

<span data-ttu-id="1e568-143">새 NoLanguage 세션이 시작 되 면 사용자는 PowerShell 명령에만 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e568-143">When a new NoLanguage session starts, users will only have access to PowerShell commands.</span></span>

<span data-ttu-id="1e568-144">기존 세션 구성에 세션 구성 파일을 추가 하려면 Set-PSSessionConfiguration cmdlet 및 Path 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e568-144">To add a session configuration file to an existing session configuration, use the Set-PSSessionConfiguration cmdlet and the Path parameter.</span></span> <span data-ttu-id="1e568-145">이는 지정 된 세션 구성을 사용 하 여 만든 모든 새 세션에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1e568-145">This affects any new sessions created with the specified session configuration.</span></span> <span data-ttu-id="1e568-146">Set-PSSessionConfiguration cmdlet은 세션 자체를 변경 하 고 세션 구성 파일을 수정 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1e568-146">Note that the Set-PSSessionConfiguration cmdlet changes the session itself and does not modify the session configuration file.</span></span>

<span data-ttu-id="1e568-147">예를 들어 다음 명령은 NoLanguage .pssc 파일을 LockedDown 세션 구성에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e568-147">For example, the following command adds the NoLanguage.pssc file to the LockedDown session configuration.</span></span>

```powershell
Set-PSSessionConfiguration -Name LockedDown
-Path .\NoLanguage.pssc
```

<span data-ttu-id="1e568-148">사용자가 LockedDown 세션 구성을 사용 하 여 세션을 만드는 경우 cmdlet을 실행할 수는 있지만 변수를 만들거나 사용 하거나 값을 할당 하거나 다른 PowerShell 언어 요소를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1e568-148">When users use the LockedDown session configuration to create a session, they will be able to run cmdlets but they will not be able to create or use variables, assign values, or use other PowerShell language elements.</span></span>

<span data-ttu-id="1e568-149">다음 명령은 New-PSSession cmdlet을 사용 하 여 LockedDown 세션 구성을 사용 하는 Srv01 컴퓨터에서 세션을 만들고 $s 변수에 세션에 대 한 개체 참조를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e568-149">The following command uses the New-PSSession cmdlet to create a session on the computer Srv01 that uses the LockedDown session configuration, saving an object reference to the session in the $s variable.</span></span> <span data-ttu-id="1e568-150">세션 구성의 ACL (액세스 제어 목록)은이를 사용 하 여 세션을 만들 수 있는 사용자를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e568-150">The ACL (access control list) of the session configuration determines who can use it to create a session.</span></span>

```powershell
$s = New-PSSession -ComputerName Srv01
-ConfigurationName LockedDown
```

<span data-ttu-id="1e568-151">NoLanguage 제약 조건이 LockedDown 세션 구성에 추가 되었으므로 LockedDown 세션의 사용자는 PowerShell 명령 및 cmdlet만 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e568-151">Because the NoLanguage constraints were added to the LockedDown session configuration, users in LockedDown sessions will only be able to run PowerShell commands and cmdlets.</span></span> <span data-ttu-id="1e568-152">예를 들어 다음 두 명령은 Invoke-Command cmdlet을 사용 하 여 $s 변수에 참조 된 세션에서 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e568-152">For example, the following two commands use the Invoke-Command cmdlet to run commands in the session referenced in the $s variable.</span></span> <span data-ttu-id="1e568-153">Get-UICulture cmdlet을 실행 하 고 변수를 사용 하지 않는 첫 번째 명령은 성공 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e568-153">The first command, which runs the Get-UICulture cmdlet and does not use any variables, succeeds.</span></span> <span data-ttu-id="1e568-154">$PSUICulture 변수의 값을 가져오는 두 번째 명령은 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e568-154">The second command, which gets the value of the $PSUICulture variable, fails.</span></span>

```
Invoke-Command -Session $s {Get-UICulture}
en-US

Invoke-Command -Session $s {$PSUICulture}
The syntax is not supported by this runspace. This might be
because it is in no-language mode.
+ CategoryInfo          : ParserError: ($PSUICulture:String) [],
ParseException
+ FullyQualifiedErrorId : ScriptsNotAllowed
```

## <a name="editing-a-session-configuration-file"></a><span data-ttu-id="1e568-155">세션 구성 파일 편집</span><span class="sxs-lookup"><span data-stu-id="1e568-155">Editing a Session Configuration File</span></span>

<span data-ttu-id="1e568-156">RunAsVirtualAccount 및 RunAsVirtualAccountGroups를 제외한 세션 구성의 모든 설정은 세션 구성에서 사용 하는 세션 구성 파일을 편집 하 여 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e568-156">All settings in a session configuration except for RunAsVirtualAccount and RunAsVirtualAccountGroups can be modified by editing the session configuration file used by the session configuration.</span></span> <span data-ttu-id="1e568-157">이렇게 하려면 먼저 세션 구성 파일의 활성 복사본을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="1e568-157">To do this, begin by locating the active copy of the session configuration file.</span></span>

<span data-ttu-id="1e568-158">세션 구성에서 세션 구성 파일을 사용 하는 경우 PowerShell은 세션 구성 파일의 활성 복사본을 만들고 \$ \\ 로컬 컴퓨터의 pshome sessionconfig 디렉터리에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e568-158">When you use a session configuration file in a session configuration, PowerShell creates an active copy of the session configuration file and stores it in the \$pshome\\SessionConfig directory on the local computer.</span></span>

<span data-ttu-id="1e568-159">세션 구성 파일의 활성 복사본 위치는 세션 구성 개체의 ConfigFilePath 속성에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e568-159">The location of the active copy of a session configuration file is stored in the ConfigFilePath property of the session configuration object.</span></span>

<span data-ttu-id="1e568-160">다음 명령은 NoLanguage 세션 구성에 대 한 세션 구성 파일의 위치를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1e568-160">The following command gets the location of the session configuration file for the NoLanguage session configuration.</span></span>

```powershell
(Get-PSSessionConfiguration -Name NoLanguage).ConfigFilePath
```

<span data-ttu-id="1e568-161">이 명령은 다음과 비슷한 파일 경로를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e568-161">That command returns a file path similar to the following:</span></span>

```
C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\
NoLanguage_0c115179-ff2a-4f66-a5eb-e56e5692ba22.pssc
```

<span data-ttu-id="1e568-162">텍스트 편집기에서 .psc 파일을 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e568-162">You can edit the .pssc file in any text editor.</span></span> <span data-ttu-id="1e568-163">파일이 저장 되 면 세션 구성을 사용 하는 모든 새 세션에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e568-163">After the file is saved it will be employed by any new sessions that use the session configuration.</span></span>

<span data-ttu-id="1e568-164">RunAsVirtualAccount 또는 RunAsVirtualAccountGroups 설정을 수정 해야 하는 경우 세션 구성의 등록을 취소 하 고 편집 된 값을 포함 하는 세션 구성 파일을 다시 등록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e568-164">If you need to modify the RunAsVirtualAccount or the RunAsVirtualAccountGroups settings, you must un-register the session configuration and re-register a session configuration file that includes the edited values.</span></span>

## <a name="testing-a-session-configuration-file"></a><span data-ttu-id="1e568-165">세션 구성 파일 테스트</span><span class="sxs-lookup"><span data-stu-id="1e568-165">Testing a Session Configuration File</span></span>

<span data-ttu-id="1e568-166">Test-PSSessionConfigurationFile cmdlet을 사용 하 여 수동으로 편집한 세션 구성 파일을 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e568-166">Use the Test-PSSessionConfigurationFile cmdlet to test manually edited session configuration files.</span></span> <span data-ttu-id="1e568-167">이는 중요 합니다. 파일 구문 및 값이 유효 하지 않으면 사용자가 세션 구성을 사용 하 여 세션을 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1e568-167">That's important: if the file syntax and values are not valid users will not be able to use the session configuration to create a session.</span></span>

<span data-ttu-id="1e568-168">예를 들어 다음 명령은 NoLanguage 세션 구성의 활성 세션 구성 파일을 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e568-168">For example, the following command tests the active session configuration file of the NoLanguage session configuration.</span></span>

```powershell
Test-PSSessionConfigurationFile -Path C:\WINDOWS\System32\
WindowsPowerShell\v1.0\SessionConfig\
NoLanguage_0c115179-ff2a-4f66-a5eb-e56e5692ba22.pssc
```

<span data-ttu-id="1e568-169">구성 파일의 구문과 값이 유효한 경우 Test-PSSessionConfigurationFile True를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e568-169">If the syntax and values in the configuration file are valid Test-PSSessionConfigurationFile returns True.</span></span> <span data-ttu-id="1e568-170">구문과 값이 유효 하지 않은 경우에는 cmdlet이 False를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e568-170">If the syntax and values are not valid then the cmdlet returns False.</span></span>

<span data-ttu-id="1e568-171">Test-PSSessionConfigurationFile를 사용 하 여 New-PSSessionConfiguration cmdlet이 만드는 파일을 비롯 한 모든 세션 구성 파일을 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e568-171">You can use Test-PSSessionConfigurationFile to test any session configuration file, including files that the New-PSSessionConfiguration cmdlet creates.</span></span> <span data-ttu-id="1e568-172">자세한 내용은 Test-PSSessionConfigurationFile cmdlet에 대 한 도움말 항목을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1e568-172">For more information, see the help topic for the Test-PSSessionConfigurationFile cmdlet.</span></span>

## <a name="removing-a-session-configuration-file"></a><span data-ttu-id="1e568-173">세션 구성 파일 제거</span><span class="sxs-lookup"><span data-stu-id="1e568-173">Removing a Session Configuration File</span></span>

<span data-ttu-id="1e568-174">세션 구성에서 세션 구성 파일을 제거할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1e568-174">You cannot remove a session configuration file from a session configuration.</span></span>
<span data-ttu-id="1e568-175">그러나 기본 설정을 사용 하는 새 파일로 파일을 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e568-175">However, you can replace the file with a new file that uses the default settings.</span></span> <span data-ttu-id="1e568-176">이렇게 하면 원래 구성 파일에 사용 되는 설정이 효율적으로 취소 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e568-176">This effectively cancels the settings used by the original configuration file.</span></span>

<span data-ttu-id="1e568-177">세션 구성 파일을 바꾸려면 기본 설정을 사용 하는 새 세션 구성 파일을 만든 다음 Set-PSSessionConfiguration cmdlet을 사용 하 여 사용자 지정 세션 구성 파일을 새 파일로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="1e568-177">To replace a session configuration file, create a new session configuration file that uses the default settings, then use the Set-PSSessionConfiguration cmdlet to replace the custom session configuration file with the new file.</span></span>

<span data-ttu-id="1e568-178">예를 들어 다음 명령은 기본 세션 구성 파일을 만든 다음 NoLanguage 세션 구성에서 활성 세션 구성 파일을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="1e568-178">For example, the following commands create a Default session configuration file and then replace the active session configuration file in the NoLanguage session configuration.</span></span>

```powershell
New-PSSessionConfigurationFile -Path .\Default.pssc
Set-PSSessionConfiguration -Name NoLanguage
-Path .\Default.pssc
```

<span data-ttu-id="1e568-179">이 명령이 완료 되 면 NoLanguage 세션 구성은 실제로 해당 세션 구성을 사용 하 여 만든 모든 세션에 대 한 완전 한 언어 지원 (기본 설정)을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e568-179">When these commands finish, the NoLanguage session configuration will actually provide full language support (the default setting) for all sessions created with that session configuration.</span></span>

<span data-ttu-id="1e568-180">세션 구성의 속성 보기 세션 구성 파일을 사용 하 여 세션 구성을 나타내는 세션 구성 개체에는 세션 구성을 쉽게 검색 하 고 분석할 수 있도록 하는 추가 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e568-180">Viewing the Properties of a Session Configuration The session configuration objects that represent session configurations using session configuration files have additional properties that make it easy to discover and analyze the session configuration.</span></span> <span data-ttu-id="1e568-181">아래에 표시 된 형식 이름에는 서식이 지정 된 뷰 정의가 포함 되어 있습니다. Get-PSSessionConfiguration cmdlet을 실행 하 고 반환 된 데이터를 Get-Member cmdlet에 파이프 하 여 속성을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e568-181">(Note that the type name shown below includes a formatted view definition.) You can view the properties by running the Get-PSSessionConfiguration cmdlet and piping the returned data to the Get-Member cmdlet:</span></span>

```powershell
Get-PSSessionConfiguration NoLanguage | Get-Member
```

```output
TypeName: Microsoft.PowerShell.Commands.PSSessionConfigurationCommands
#PSSessionConfiguration

Name                          MemberType     Definition
----                          ----------     ----------
Equals                        Method         bool Equals(System.O...
GetHashCode                   Method         int GetHashCode()
GetType                       Method         type GetType()
ToString                      Method         string ToString()
Architecture                  NoteProperty   System.String Archit...
Author                        NoteProperty   System.String Author...
AutoRestart                   NoteProperty   System.String AutoRe...
Capability                    NoteProperty   System.Object[] Capa...
CompanyName                   NoteProperty   System.String Compan...
configfilepath                NoteProperty   System.String config...
Copyright                     NoteProperty   System.String Copyri...
Enabled                       NoteProperty   System.String Enable...
ExactMatch                    NoteProperty   System.String ExactM...
ExecutionPolicy               NoteProperty   System.String Execut...
Filename                      NoteProperty   System.String Filena...
GUID                          NoteProperty   System.String GUID=0...
ProcessIdleTimeoutSec         NoteProperty   System.String Proces...
IdleTimeoutms                 NoteProperty   System.String IdleTi...
lang                          NoteProperty   System.String lang=e...
LanguageMode                  NoteProperty   System.String Langua...
MaxConcurrentCommandsPerShell NoteProperty   System.String MaxCon...
MaxConcurrentUsers            NoteProperty   System.String MaxCon...
MaxIdleTimeoutms              NoteProperty   System.String MaxIdl...
MaxMemoryPerShellMB           NoteProperty   System.String MaxMem...
MaxProcessesPerShell          NoteProperty   System.String MaxPro...
MaxShells                     NoteProperty   System.String MaxShells
MaxShellsPerUser              NoteProperty   System.String MaxShe...
Name                          NoteProperty   System.String Name=N...
PSVersion                     NoteProperty   System.String PSVersion
ResourceUri                   NoteProperty   System.String Resour...
RunAsPassword                 NoteProperty   System.String RunAsP...
RunAsUser                     NoteProperty   System.String RunAsUser
SchemaVersion                 NoteProperty   System.String Schema...
SDKVersion                    NoteProperty   System.String SDKVer...
OutputBufferingMode           NoteProperty   System.String Output...
SessionType                   NoteProperty   System.String Sessio...
UseSharedProcess              NoteProperty   System.String UseSha...
SupportsOptions               NoteProperty   System.String Suppor...
xmlns                         NoteProperty   System.String xmlns=...
XmlRenderingType              NoteProperty   System.String XmlRen...
Permission                    ScriptProperty System.Object Permis...
```

<span data-ttu-id="1e568-182">이러한 속성을 통해 특정 세션 구성을 쉽게 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e568-182">These properties make it easy to search for specific session configurations.</span></span>
<span data-ttu-id="1e568-183">예를 들어 Set-executionpolicy 속성을 사용 하 여 RemoteSigned 실행 정책을 통해 세션을 지 원하는 세션 구성을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e568-183">For example, you can use the ExecutionPolicy property to find a session configuration that supports sessions with the RemoteSigned execution policy.</span></span>
<span data-ttu-id="1e568-184">Set-executionpolicy 속성은 세션 구성 파일을 사용 하는 세션에만 존재 하기 때문에 명령은 정규화 된 세션 구성을 모두 반환 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e568-184">Note that, because the ExecutionPolicy property exists only on sessions that use session configuration files, the command might not return all qualifying session configurations.</span></span>

```powershell
Get-PSSessionConfiguration |
where {$_.ExecutionPolicy -eq "RemoteSigned"}
```

<span data-ttu-id="1e568-185">다음 명령은 RunAsUser가 Exchange 관리자 인 세션 구성을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1e568-185">The following command gets session configurations in which the RunAsUser is the Exchange administrator.</span></span>

```powershell
 Get-PSSessionConfiguration |
where {$_.RunAsUser -eq "Exchange01\Admin01"}
```

<span data-ttu-id="1e568-186">구성과 관련 된 역할 정의에 대 한 정보를 보려면 Get-PSSessionCapability cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e568-186">To view information about the role definitions associated with a configuration use the Get-PSSessionCapability cmdlet.</span></span> <span data-ttu-id="1e568-187">이 cmdlet을 사용 하면 특정 끝점의 특정 사용자가 사용할 수 있는 명령 및 환경을 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e568-187">This cmdlet enables you to determine the commands and environment available to specific users in specific endpoints.</span></span>

## <a name="notes"></a><span data-ttu-id="1e568-188">참고</span><span class="sxs-lookup"><span data-stu-id="1e568-188">NOTES</span></span>

<span data-ttu-id="1e568-189">세션 구성은 "빈" 세션 이라는 유형의 세션도 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e568-189">Session configurations also support a type of session known as an "empty" session.</span></span> <span data-ttu-id="1e568-190">빈 세션 유형을 사용 하면 선택한 명령을 사용 하 여 사용자 지정 세션을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e568-190">An Empty session type enables you to create custom sessions with selected commands.</span></span> <span data-ttu-id="1e568-191">빈 세션에 모듈, 함수 또는 스크립트를 추가 하지 않으면 세션은 식으로 제한 되며 실용적으로 사용 되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e568-191">If you do not add modules, functions, or scripts to an empty session, the session is limited to expressions and might not be of any practical use.</span></span> <span data-ttu-id="1e568-192">SessionType 속성은 빈 세션으로 작업 하 고 있는지 여부를 알려 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1e568-192">The SessionType property tells you whether or not you are working with an empty session.</span></span>

## <a name="see-also"></a><span data-ttu-id="1e568-193">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1e568-193">SEE ALSO</span></span>

[<span data-ttu-id="1e568-194">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="1e568-194">about_Session_Configurations</span></span>](about_Session_Configurations.md)

[<span data-ttu-id="1e568-195">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="1e568-195">New-PSSession</span></span>](xref:Microsoft.PowerShell.Core.New-PSSession)

[<span data-ttu-id="1e568-196">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="1e568-196">Disable-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Disable-PSSessionConfiguration)

[<span data-ttu-id="1e568-197">Enable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="1e568-197">Enable-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Enable-PSSessionConfiguration)

[<span data-ttu-id="1e568-198">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="1e568-198">Get-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Get-PSSessionConfiguration)

[<span data-ttu-id="1e568-199">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="1e568-199">New-PSSessionConfigurationFile</span></span>](xref:Microsoft.PowerShell.Core.New-PSSessionConfigurationFile)

[<span data-ttu-id="1e568-200">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="1e568-200">Register-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Register-PSSessionConfiguration)

[<span data-ttu-id="1e568-201">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="1e568-201">Set-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Set-PSSessionConfiguration)

[<span data-ttu-id="1e568-202">Test-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="1e568-202">Test-PSSessionConfigurationFile</span></span>](xref:Microsoft.PowerShell.Core.Test-PSSessionConfigurationFile)

[<span data-ttu-id="1e568-203">Unregister-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="1e568-203">Unregister-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Unregister-PSSessionConfiguration)

[<span data-ttu-id="1e568-204">Get-PSSessionCapability</span><span class="sxs-lookup"><span data-stu-id="1e568-204">Get-PSSessionCapability</span></span>](xref:Microsoft.PowerShell.Core.Get-PSSessionCapability)

[<span data-ttu-id="1e568-205">New-PSRoleCapabilityFile</span><span class="sxs-lookup"><span data-stu-id="1e568-205">New-PSRoleCapabilityFile</span></span>](xref:Microsoft.PowerShell.Core.New-PSRoleCapabilityFile)
