---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/24/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-pssessionconfigurationfile?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSSessionConfigurationFile
ms.openlocfilehash: a41c52bf163aa0a73b54e75b5192389a14da82bb
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99604990"
---
# <span data-ttu-id="7cf53-102">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="7cf53-102">New-PSSessionConfigurationFile</span></span>

## <span data-ttu-id="7cf53-103">개요</span><span class="sxs-lookup"><span data-stu-id="7cf53-103">SYNOPSIS</span></span>
<span data-ttu-id="7cf53-104">세션 구성을 정의하는 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-104">Creates a file that defines a session configuration.</span></span>

## <span data-ttu-id="7cf53-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="7cf53-105">SYNTAX</span></span>

```
New-PSSessionConfigurationFile [-Path] <String> [-SchemaVersion <Version>] [-Guid <Guid>]
 [-Author <String>] [-Description <String>] [-CompanyName <String>] [-Copyright <String>]
 [-SessionType <SessionType>] [-TranscriptDirectory <String>] [-RunAsVirtualAccount]
 [-RunAsVirtualAccountGroups <String[]>] [-MountUserDrive] [-UserDriveMaximumSize <Int64>]
 [-GroupManagedServiceAccount <String>] [-ScriptsToProcess <String[]>]
 [-RoleDefinitions <IDictionary>] [-RequiredGroups <IDictionary>] [-LanguageMode <PSLanguageMode>]
 [-ExecutionPolicy <ExecutionPolicy>] [-PowerShellVersion <Version>] [-ModulesToImport <Object[]>]
 [-VisibleAliases <String[]>] [-VisibleCmdlets <Object[]>] [-VisibleFunctions <Object[]>]
 [-VisibleExternalCommands <String[]>] [-VisibleProviders <String[]>]
 [-AliasDefinitions <IDictionary[]>] [-FunctionDefinitions <IDictionary[]>]
 [-VariableDefinitions <Object>] [-EnvironmentVariables <IDictionary>] [-TypesToProcess <String[]>]
 [-FormatsToProcess <String[]>] [-AssembliesToLoad <String[]>] [-Full] [<CommonParameters>]
```

## <span data-ttu-id="7cf53-106">설명</span><span class="sxs-lookup"><span data-stu-id="7cf53-106">DESCRIPTION</span></span>

<span data-ttu-id="7cf53-107">Cmdlet은 세션 구성 `New-PSSessionConfigurationFile` 및 세션 구성을 사용 하 여 만든 세션의 환경을 정의 하는 설정 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-107">The `New-PSSessionConfigurationFile` cmdlet creates a file of settings that define a session configuration and the environment of sessions that are created by using the session configuration.</span></span>
<span data-ttu-id="7cf53-108">세션 구성에서이 파일을 사용 하려면 또는 cmdlet의 **Path** 매개 변수를 사용 합니다 `Register-PSSessionConfiguration` `Set-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="7cf53-108">To use the file in a session configuration, use the **Path** parameter of the `Register-PSSessionConfiguration` or `Set-PSSessionConfiguration` cmdlets.</span></span>

<span data-ttu-id="7cf53-109">에서 만드는 세션 구성 파일은 `New-PSSessionConfigurationFile` 세션 구성 속성 및 값의 해시 테이블을 포함 하는 사람이 읽을 수 있는 텍스트 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-109">The session configuration file that `New-PSSessionConfigurationFile` creates is a human-readable text file that contains a hash table of the session configuration properties and values.</span></span> <span data-ttu-id="7cf53-110">파일에는 파일 `.pssc` 이름 확장명이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-110">The file has a `.pssc` filename extension.</span></span>

<span data-ttu-id="7cf53-111">`New-PSSessionConfigurationFile` **Path** 매개 변수를 제외 하 고의 모든 매개 변수는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-111">All parameters of `New-PSSessionConfigurationFile` are optional, except for the **Path** parameter.</span></span>
<span data-ttu-id="7cf53-112">매개 변수를 생략하면 매개 변수 설명에 표시된 경우를 제외하고 세션 구성 파일의 해당 키가 주석으로 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-112">If you omit a parameter, the corresponding key in the session configuration file is commented-out, except where noted in the parameter description.</span></span>

<span data-ttu-id="7cf53-113">끝점 이라고 하는 세션 구성은 컴퓨터에 연결 하는 PowerShell **세션 (pssession**)에 대 한 환경을 정의 하는 로컬 컴퓨터의 설정 모음입니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-113">A session configuration, also known as an endpoint, is a collection of settings on the local computer that define the environment for PowerShell sessions (**PSSessions**) that connect to the computer.</span></span> <span data-ttu-id="7cf53-114">모든 **pssession은 세션 구성을** 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-114">All **PSSessions** use a session configuration.</span></span> <span data-ttu-id="7cf53-115">특정 세션 구성을 지정 하려면 cmdlet과 같이 세션을 만드는 cmdlet의 **ConfigurationName** 매개 변수를 사용 합니다 `New-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="7cf53-115">To specify a particular session configuration, use the **ConfigurationName** parameter of cmdlets that create a session, such as the `New-PSSession` cmdlet.</span></span>

<span data-ttu-id="7cf53-116">session configuration file을 사용하면 복잡한 스크립트나 코드 어셈블리 없이 세션 구성을 쉽게 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-116">A session configuration file makes it easy to define a session configuration without complex scripts or code assemblies.</span></span> <span data-ttu-id="7cf53-117">파일의 설정은 세션 구성의 선택적 시작 스크립트 및 어셈블리와 함께 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-117">The settings in the file are used with the optional startup script and any assemblies in the session configuration.</span></span>

<span data-ttu-id="7cf53-118">세션 구성 및 세션 구성 파일에 대 한 자세한 내용은 [about_Session_Configurations](About/about_Session_Configurations.md) 및 [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7cf53-118">For more information about session configurations and session configuration files, see [about_Session_Configurations](About/about_Session_Configurations.md) and [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md).</span></span>

<span data-ttu-id="7cf53-119">이 cmdlet은 PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-119">This cmdlet was introduced in PowerShell 3.0.</span></span>

## <span data-ttu-id="7cf53-120">예제</span><span class="sxs-lookup"><span data-stu-id="7cf53-120">EXAMPLES</span></span>

### <span data-ttu-id="7cf53-121">예제 1: NoLanguage 세션 만들기 및 사용</span><span class="sxs-lookup"><span data-stu-id="7cf53-121">Example 1: Creating and using a NoLanguage session</span></span>

<span data-ttu-id="7cf53-122">이 예제에서는를 만들고 언어 세션이 없는 세션을 사용 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-122">This example show how to create and the effects of using a no-language session.</span></span>

<span data-ttu-id="7cf53-123">단계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-123">The steps include:</span></span>

1. <span data-ttu-id="7cf53-124">새 구성 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-124">Create a new configuration file.</span></span>
1. <span data-ttu-id="7cf53-125">구성을 등록 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-125">Register the configuration.</span></span>
1. <span data-ttu-id="7cf53-126">구성을 사용 하는 새 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-126">Create a new session that uses the configuration.</span></span>
1. <span data-ttu-id="7cf53-127">해당 새 세션에서 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-127">Run commands in that new session.</span></span>

<span data-ttu-id="7cf53-128">이 예제의 명령을 실행 하려면 관리자 권한으로 실행 옵션을 사용 하 여 PowerShell을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-128">To run the commands in this example, start PowerShell by using the Run as administrator option.</span></span> <span data-ttu-id="7cf53-129">Cmdlet을 실행 하려면이 옵션을 선택 해야 `Register-PSSessionConfiguration` 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-129">This option is required to run the `Register-PSSessionConfiguration` cmdlet.</span></span>

```powershell
New-PSSessionConfigurationFile -Path .\NoLanguage.pssc -LanguageMode NoLanguage
Register-PSSessionConfiguration -Path .\NoLanguage.pssc -Name NoLanguage -Force
$NoLanguageSession = New-PSSession -ComputerName Srv01 -ConfigurationName NoLanguage
Invoke-Command -Session $NoLanguageSession -ScriptBlock {
  if ((Get-Date) -lt '1January2099') {'Before'} else {'After'}
}
```

```Output
The syntax is not supported by this runspace. This might be because it is in no-language mode.
    + CategoryInfo          : ParserError: (if ((Get-Date) ...') {'Before'}  :String) [], ParseException
    + FullyQualifiedErrorId : ScriptsNotAllowed
    + PSComputerName        : localhost
```

<span data-ttu-id="7cf53-130">이 예에서는 `Invoke-Command` **LanguageMode** 이 **nolanguage** 로 설정 되어 있으므로이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-130">In this example, the `Invoke-Command` fails because the **LanguageMode** is set to **NoLanguage**.</span></span>

### <span data-ttu-id="7cf53-131">예제 2: RestrictedLanguage 세션 만들기 및 사용</span><span class="sxs-lookup"><span data-stu-id="7cf53-131">Example 2: Creating and using a RestrictedLanguage session</span></span>

<span data-ttu-id="7cf53-132">이 예제에서는를 만들고 언어 세션이 없는 세션을 사용 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-132">This example show how to create and the effects of using a no-language session.</span></span>

<span data-ttu-id="7cf53-133">단계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-133">The steps include:</span></span>

1. <span data-ttu-id="7cf53-134">새 구성 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-134">Create a new configuration file.</span></span>
1. <span data-ttu-id="7cf53-135">구성을 등록 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-135">Register the configuration.</span></span>
1. <span data-ttu-id="7cf53-136">구성을 사용 하는 새 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-136">Create a new session that uses the configuration.</span></span>
1. <span data-ttu-id="7cf53-137">해당 새 세션에서 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-137">Run commands in that new session.</span></span>

<span data-ttu-id="7cf53-138">이 예제의 명령을 실행 하려면 관리자 권한으로 실행 옵션을 사용 하 여 PowerShell을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-138">To run the commands in this example, start PowerShell by using the Run as administrator option.</span></span> <span data-ttu-id="7cf53-139">Cmdlet을 실행 하려면이 옵션을 선택 해야 `Register-PSSessionConfiguration` 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-139">This option is required to run the `Register-PSSessionConfiguration` cmdlet.</span></span>

```powershell
New-PSSessionConfigurationFile -Path .\NoLanguage.pssc -LanguageMode RestrictedLanguage
Register-PSSessionConfiguration -Path .\NoLanguage.pssc -Name RestrictedLanguage -Force
$RestrictedSession = New-PSSession -ComputerName Srv01 -ConfigurationName RestrictedLanguage
Invoke-Command -Session $RestrictedSession -ScriptBlock {
  if ((Get-Date) -lt '1January2099') {'Before'} else {'After'}
}
```

```Output
Before
```

<span data-ttu-id="7cf53-140">이 예제에서 LanguageMode는 `Invoke-Command` **RestrictedLanguage** 로 설정  되어 있으므로 성공 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-140">In this example, the `Invoke-Command` succeeds because the **LanguageMode** is set to **RestrictedLanguage**.</span></span>

### <span data-ttu-id="7cf53-141">예 3: 세션 구성 파일 변경</span><span class="sxs-lookup"><span data-stu-id="7cf53-141">Example 3: Changing a Session Configuration File</span></span>

<span data-ttu-id="7cf53-142">이 예에서는 "ITTasks" 라는 기존 세션에서 사용 되는 세션 구성 파일을 변경 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-142">This example shows how to change the session configuration file that is used in an existing session named "ITTasks".</span></span> <span data-ttu-id="7cf53-143">이전에는 이러한 세션에 핵심 모듈과 내부 **Ittasks** 모듈도 있었습니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-143">Previously, these sessions had only the core modules and an internal **ITTasks** module.</span></span> <span data-ttu-id="7cf53-144">관리자는 ITTasks 세션 구성을 사용 하 여 만든 세션에 **PSScheduledJob** 모듈을 추가 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-144">The administrator wants to add the **PSScheduledJob** module to sessions created by using the ITTasks session configuration.</span></span>

```powershell
New-PSSessionConfigurationFile -Path .\New-ITTasks.pssc -ModulesToImport Microsoft*, ITTasks, PSScheduledJob
Set-PSSessionConfiguration -Name ITTasks -Path .\New-ITTasks.pssc
```

<span data-ttu-id="7cf53-145">Cmdlet을 통해 `New-PSSessionConfigurationFile` 필요한 모듈을 가져오는 세션 구성 파일을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-145">The `New-PSSessionConfigurationFile` cmdlet to create a session configuration file that imports the required modules.</span></span> <span data-ttu-id="7cf53-146">`Set-PSSessionConfiguration`Cmdlet은 현재 구성 파일을 새 구성 파일로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-146">The `Set-PSSessionConfiguration` cmdlet replaces the current configuration file with the new one.</span></span> <span data-ttu-id="7cf53-147">이 새 구성은 변경 후에 생성 된 새 세션에만 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-147">This new configuration only affects new sessions created after the change.</span></span>
<span data-ttu-id="7cf53-148">기존 "ITTasks" 세션에는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-148">Existing "ITTasks" sessions are not affected.</span></span>

### <span data-ttu-id="7cf53-149">예제 4: 세션 구성 파일 편집</span><span class="sxs-lookup"><span data-stu-id="7cf53-149">Example 4: Editing a Session Configuration File</span></span>

<span data-ttu-id="7cf53-150">이 예제에서는 구성 파일의 활성 세션 구성 사본을 편집하여 세션 구성을 변경하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-150">This example shows how to change a session configuration by editing the active session configuration copy of the configuration file.</span></span> <span data-ttu-id="7cf53-151">구성 파일의 세션 구성 복사본을 수정 하려면 파일에 대 한 모든 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-151">To modify the session configuration copy of the configuration file, you must have full control access to the file.</span></span> <span data-ttu-id="7cf53-152">이 경우 파일에 대 한 사용 권한을 변경 해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-152">This may require you to change the permissions on the file.</span></span>

<span data-ttu-id="7cf53-153">이 시나리오에서는 `Select-String` 활성 구성 파일을 편집 하 여 cmdlet에 대 한 새 별칭을 추가 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-153">In this scenario, we want to add a new alias for the `Select-String` cmdlet by editing the active configuration file.</span></span>

<span data-ttu-id="7cf53-154">아래 예제 코드는 다음 단계를 수행 하 여 이러한 변경을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-154">The example code below performs the following steps to make this change:</span></span>

1. <span data-ttu-id="7cf53-155">ITConfig 세션의 구성 파일 경로를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-155">Get the configuration file path for the ITConfig session.</span></span>
1. <span data-ttu-id="7cf53-156">사용자는 **Notepad.exe** 를 사용 하 여 구성 파일을 편집 하 여 **AliasDefinitions** 값을 다음과 같이 변경 합니다 `AliasDefinitions = @(@{Name='slst';Value='Select-String'})` .</span><span class="sxs-lookup"><span data-stu-id="7cf53-156">The user edits the configuration file using **Notepad.exe** to change the **AliasDefinitions** value as follows: `AliasDefinitions = @(@{Name='slst';Value='Select-String'})`.</span></span>
1. <span data-ttu-id="7cf53-157">업데이트 된 구성 파일을 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-157">Test the updated configuration file.</span></span>

```powershell
$ITConfig = Get-PSSessionConfiguration -Name ITConfig
notepad.exe $ITConfig.ConfigFilePath
Test-PSSessionConfigurationFile -Path $ITConfig.ConfigFilePath
```

```Output
True
```

<span data-ttu-id="7cf53-158">에서 **Verbose** 매개 변수를 사용 `Test-PSSessionConfigurationFile` 하 여 검색 된 오류를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-158">Use the **Verbose** parameter with `Test-PSSessionConfigurationFile` to display any errors that are detected.</span></span> <span data-ttu-id="7cf53-159">Cmdlet은 `$True` 파일에서 오류가 검색 되지 않으면를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-159">The cmdlet returns `$True` if no errors are detected in the file.</span></span>

### <span data-ttu-id="7cf53-160">예제 5: 샘플 구성 파일 만들기</span><span class="sxs-lookup"><span data-stu-id="7cf53-160">Example 5: Create a sample configuration file</span></span>

<span data-ttu-id="7cf53-161">이 예에서는 `New-PSSessionConfigurationFile` 모든 cmdlet 매개 변수를 사용 하는 명령을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-161">This example shows a `New-PSSessionConfigurationFile` command that uses all the cmdlet parameters.</span></span>
<span data-ttu-id="7cf53-162">이 명령은 각 매개 변수의 올바른 입력 형식을 보여 주기 위해 포함되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-162">It is included to show the correct input format for each parameter.</span></span>

<span data-ttu-id="7cf53-163">결과 SampleFile.pssc가 출력에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-163">The resulting SampleFile.pssc is displayed in the output.</span></span>

```powershell
$configSettings = @{
    Path = '.\SampleFile.pssc'
    SchemaVersion = '1.0.0.0'
    Author = 'User01'
    Copyright = '(c) Fabrikam Corporation. All rights reserved.'
    CompanyName = 'Fabrikam Corporation'
    Description = 'This is a sample file.'
    ExecutionPolicy = 'AllSigned'
    PowerShellVersion = '3.0'
    LanguageMode = 'FullLanguage'
    SessionType = 'Default'
    EnvironmentVariables = @{TESTSHARE='\\Test2\Test'}
    ModulesToImport = @{ModuleName='PSScheduledJob'; ModuleVersion='1.0.0.0'; GUID='50cdb55f-5ab7-489f-9e94-4ec21ff51e59'},'PSDiagnostics'
    AssembliesToLoad = 'System.Web.Services','FSharp.Compiler.CodeDom.dll'
    TypesToProcess = 'Types1.ps1xml','Types2.ps1xml'
    FormatsToProcess = 'CustomFormats.ps1xml'
    ScriptsToProcess = 'Get-Inputs.ps1'
    AliasDefinitions = @{Name='hlp';Value='Get-Help';Description='Gets help.';Options='AllScope'},
        @{Name='Update';Value='Update-Help';Description='Updates help';Options='ReadOnly'}
    FunctionDefinitions = @{Name='Get-Function';ScriptBlock={Get-Command -CommandType Function};Options='ReadOnly'}
    VariableDefinitions = @{Name='WarningPreference';Value='SilentlyContinue'}
    VisibleAliases = 'c*','g*','i*','s*'
    VisibleCmdlets = 'Get*'
    VisibleFunctions = 'Get*'
    VisibleProviders = 'FileSystem','Function','Variable'
    RunAsVirtualAccount = $true
    RunAsVirtualAccountGroups = 'Backup Operators'
}
New-PSSessionConfigurationFile @configSettings
Get-Content SampleFile.pssc
```

```Output
@{

# Version number of the schema used for this document
SchemaVersion = '1.0.0.0'

# ID used to uniquely identify this document
GUID = '1caeff7f-27ca-4360-97cf-37846f594235'

# Author of this document
Author = 'User01'

# Description of the functionality provided by these settings
Description = 'This is a sample file.'

# Company associated with this document
CompanyName = 'Fabrikam Corporation'

# Copyright statement for this document
Copyright = '(c) Fabrikam Corporation. All rights reserved.'

# Session type defaults to apply for this session configuration. Can be 'RestrictedRemoteServer' (recommended), 'Empty', or 'Default'
SessionType = 'Default'

# Directory to place session transcripts for this session configuration
# TranscriptDirectory = 'C:\Transcripts\'

# Whether to run this session configuration as the machine's (virtual) administrator account
RunAsVirtualAccount = $true

# Groups associated with machine's (virtual) administrator account
RunAsVirtualAccountGroups = 'Backup Operators'

# Scripts to run when applied to a session
ScriptsToProcess = 'Get-Inputs.ps1'

# User roles (security groups), and the role capabilities that should be applied to them when applied to a session
# RoleDefinitions = @{ 'CONTOSO\SqlAdmins' = @{ RoleCapabilities = 'SqlAdministration' }; 'CONTOSO\SqlManaged' = @{ RoleCapabilityFiles = 'C:\RoleCapability\SqlManaged.psrc' }; 'CONTOSO\ServerMonitors' = @{ VisibleCmdlets = 'Get-Process' } }

# Language mode to apply when applied to a session. Can be 'NoLanguage' (recommended), 'RestrictedLanguage', 'ConstrainedLanguage', or 'FullLanguage'
LanguageMode = 'FullLanguage'

# Execution policy to apply when applied to a session
ExecutionPolicy = 'AllSigned'

# Version of the PowerShell engine to use when applied to a session
PowerShellVersion = '3.0'

# Modules to import when applied to a session
ModulesToImport = @{
    'GUID' = '50cdb55f-5ab7-489f-9e94-4ec21ff51e59'
    'ModuleName' = 'PSScheduledJob'
    'ModuleVersion' = '1.0.0.0' }, 'PSDiagnostics'

# Aliases to make visible when applied to a session
VisibleAliases = 'c*', 'g*', 'i*', 's*'

# Cmdlets to make visible when applied to a session
VisibleCmdlets = 'Get*'

# Functions to make visible when applied to a session
VisibleFunctions = 'Get*'

# Providers to make visible when applied to a session
VisibleProviders = 'FileSystem', 'Function', 'Variable'

# Aliases to be defined when applied to a session
AliasDefinitions = @{
    'Description' = 'Gets help.'
    'Name' = 'hlp'
    'Options' = 'AllScope'
    'Value' = 'Get-Help' }, @{
    'Description' = 'Updates help'
    'Name' = 'Update'
    'Options' = 'ReadOnly'
    'Value' = 'Update-Help' }

# Functions to define when applied to a session
FunctionDefinitions = @{
    'Name' = 'Get-Function'
    'Options' = 'ReadOnly'
    'ScriptBlock' = {Get-Command -CommandType Function} }

# Variables to define when applied to a session
VariableDefinitions = @{
    'Name' = 'WarningPreference'
    'Value' = 'SilentlyContinue' }

# Environment variables to define when applied to a session
EnvironmentVariables = @{
    'TESTSHARE' = '\\Test2\Test' }

# Type files (.ps1xml) to load when applied to a session
TypesToProcess = 'Types1.ps1xml', 'Types2.ps1xml'

# Format files (.ps1xml) to load when applied to a session
FormatsToProcess = 'CustomFormats.ps1xml'

# Assemblies to load when applied to a session
AssembliesToLoad = 'System.Web.Services', 'FSharp.Compiler.CodeDom.dll'

}
```

## <span data-ttu-id="7cf53-164">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="7cf53-164">PARAMETERS</span></span>

### <span data-ttu-id="7cf53-165">-AliasDefinitions</span><span class="sxs-lookup"><span data-stu-id="7cf53-165">-AliasDefinitions</span></span>

<span data-ttu-id="7cf53-166">세션 구성을 사용하는 세션에 지정된 별칭을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-166">Adds the specified aliases to sessions that use the session configuration.</span></span> <span data-ttu-id="7cf53-167">다음 키를 사용하여 해시 테이블을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-167">Enter a hash table with the following keys:</span></span>

- <span data-ttu-id="7cf53-168">이름-별칭의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-168">Name - Name of the alias.</span></span> <span data-ttu-id="7cf53-169">이 키는 필수입니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-169">This key is required.</span></span>
- <span data-ttu-id="7cf53-170">Value-별칭이 나타내는 명령입니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-170">Value - The command that the alias represents.</span></span> <span data-ttu-id="7cf53-171">이 키는 필수입니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-171">This key is required.</span></span>
- <span data-ttu-id="7cf53-172">Description-별칭을 설명 하는 텍스트 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-172">Description - A text string that describes the alias.</span></span> <span data-ttu-id="7cf53-173">이 키는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-173">This key is optional.</span></span>
- <span data-ttu-id="7cf53-174">옵션-별칭 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-174">Options - Alias options.</span></span> <span data-ttu-id="7cf53-175">이 키는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-175">This key is optional.</span></span> <span data-ttu-id="7cf53-176">기본값은 **None** 입니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-176">The default value is **None**.</span></span> <span data-ttu-id="7cf53-177">이 매개 변수에 허용 되는 값은 None, ReadOnly, Constant, Private 또는 AllScope입니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-177">The acceptable values for this parameter are: None, ReadOnly, Constant, Private, or AllScope.</span></span>

<span data-ttu-id="7cf53-178">예: `@{Name='hlp';Value='Get-Help';Description='Gets help';Options='ReadOnly'}`</span><span class="sxs-lookup"><span data-stu-id="7cf53-178">For example: `@{Name='hlp';Value='Get-Help';Description='Gets help';Options='ReadOnly'}`</span></span>

```yaml
Type: System.Collections.IDictionary[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7cf53-179">-AssembliesToLoad</span><span class="sxs-lookup"><span data-stu-id="7cf53-179">-AssembliesToLoad</span></span>

<span data-ttu-id="7cf53-180">세션 구성을 사용하는 세션에 로드할 어셈블리를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-180">Specifies the assemblies to load into the sessions that use the session configuration.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7cf53-181">-작성자</span><span class="sxs-lookup"><span data-stu-id="7cf53-181">-Author</span></span>

<span data-ttu-id="7cf53-182">세션 구성 또는 구성 파일의 작성자를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-182">Specifies the author of the session configuration or the configuration file.</span></span> <span data-ttu-id="7cf53-183">기본값은 현재 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-183">The default is the current user.</span></span> <span data-ttu-id="7cf53-184">이 매개 변수 값은 세션 구성 파일에 표시되지만 세션 구성 개체의 속성이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-184">The value of this parameter is visible in the session configuration file, but it is not a property of the session configuration object.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7cf53-185">-CompanyName</span><span class="sxs-lookup"><span data-stu-id="7cf53-185">-CompanyName</span></span>

<span data-ttu-id="7cf53-186">세션 구성 또는 구성 파일을 만든 회사를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-186">Specifies the company that created the session configuration or the configuration file.</span></span> <span data-ttu-id="7cf53-187">기본값은 **알 수 없음** 입니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-187">The default value is **Unknown**.</span></span> <span data-ttu-id="7cf53-188">이 매개 변수 값은 세션 구성 파일에 표시되지만 세션 구성 개체의 속성이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-188">The value of this parameter is visible in the session configuration file, but it is not a property of the session configuration object.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Unknown
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7cf53-189">-저작권</span><span class="sxs-lookup"><span data-stu-id="7cf53-189">-Copyright</span></span>

<span data-ttu-id="7cf53-190">세션 구성 파일의 저작권을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-190">Specifies a copyright the session configuration file.</span></span> <span data-ttu-id="7cf53-191">이 매개 변수 값은 세션 구성 파일에 표시되지만 세션 구성 개체의 속성이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-191">The value of this parameter is visible in the session configuration file, but it is not a property of the session configuration object.</span></span>

<span data-ttu-id="7cf53-192">이 매개 변수를 생략 하면은 `New-PSSessionConfigurationFile` **Author** 매개 변수 값을 사용 하 여 저작권 설명을 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-192">If you omit this parameter, `New-PSSessionConfigurationFile` generates a copyright statement by using the value of the **Author** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7cf53-193">-Description</span><span class="sxs-lookup"><span data-stu-id="7cf53-193">-Description</span></span>

<span data-ttu-id="7cf53-194">세션 구성 또는 세션 구성 파일에 대 한 설명을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-194">Specifies a description of the session configuration or the session configuration file.</span></span> <span data-ttu-id="7cf53-195">이 매개 변수 값은 세션 구성 파일에 표시되지만 세션 구성 개체의 속성이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-195">The value of this parameter is visible in the session configuration file, but it is not a property of the session configuration object.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7cf53-196">-환경 변수</span><span class="sxs-lookup"><span data-stu-id="7cf53-196">-EnvironmentVariables</span></span>

<span data-ttu-id="7cf53-197">세션에 환경 변수를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-197">Adds environment variables to the session.</span></span> <span data-ttu-id="7cf53-198">키가 환경 변수 이름이고 값이 환경 변수 값인 해시 테이블을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-198">Enter a hash table in which the keys are the environment variable names and the values are the environment variable values.</span></span>

<span data-ttu-id="7cf53-199">예: `EnvironmentVariables=@{TestShare='\\Server01\TestShare'}`</span><span class="sxs-lookup"><span data-stu-id="7cf53-199">For example: `EnvironmentVariables=@{TestShare='\\Server01\TestShare'}`</span></span>

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7cf53-200">-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="7cf53-200">-ExecutionPolicy</span></span>

<span data-ttu-id="7cf53-201">세션 구성을 사용하는 세션의 실행 정책을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-201">Specifies the execution policy of sessions that use the session configuration.</span></span> <span data-ttu-id="7cf53-202">이 매개 변수를 생략 하면 세션 구성 파일의 **set-executionpolicy** 키 값이 **제한** 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-202">If you omit this parameter, the value of the **ExecutionPolicy** key in the session configuration file is **Restricted**.</span></span> <span data-ttu-id="7cf53-203">PowerShell의 실행 정책에 대 한 자세한 내용은 [about_Execution_Policies](about/about_Execution_Policies.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7cf53-203">For information about execution policies in PowerShell, see [about_Execution_Policies](about/about_Execution_Policies.md).</span></span>

```yaml
Type: Microsoft.PowerShell.ExecutionPolicy
Parameter Sets: (All)
Aliases:
Accepted values: Unrestricted, RemoteSigned, AllSigned, Restricted, Default, Bypass, Undefined

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7cf53-204">-FormatsToProcess</span><span class="sxs-lookup"><span data-stu-id="7cf53-204">-FormatsToProcess</span></span>

<span data-ttu-id="7cf53-205">세션 구성을 사용하는 세션에서 실행되는 형식 지정 파일(.ps1xml)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-205">Specifies the formatting files (.ps1xml) that run in sessions that use the session configuration.</span></span>
<span data-ttu-id="7cf53-206">이 매개 변수 값은 형식 지정 파일의 전체 또는 절대 경로 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-206">The value of this parameter must be a full or absolute path of the formatting files.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7cf53-207">-Full</span><span class="sxs-lookup"><span data-stu-id="7cf53-207">-Full</span></span>

<span data-ttu-id="7cf53-208">이 작업에 세션 구성 파일의 가능한 모든 구성 속성이 포함 되어 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-208">Indicates that this operation includes all possible configuration properties in the session configuration file.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7cf53-209">-FunctionDefinitions</span><span class="sxs-lookup"><span data-stu-id="7cf53-209">-FunctionDefinitions</span></span>

<span data-ttu-id="7cf53-210">세션 구성을 사용하는 세션에 지정된 함수를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-210">Adds the specified functions to sessions that use the session configuration.</span></span> <span data-ttu-id="7cf53-211">다음 키를 사용하여 해시 테이블을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-211">Enter a hash table with the following keys:</span></span>

- <span data-ttu-id="7cf53-212">이름-함수의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-212">Name - Name of the function.</span></span> <span data-ttu-id="7cf53-213">이 키는 필수입니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-213">This key is required.</span></span>
- <span data-ttu-id="7cf53-214">ScriptBlock-함수 본문.</span><span class="sxs-lookup"><span data-stu-id="7cf53-214">ScriptBlock - Function body.</span></span> <span data-ttu-id="7cf53-215">스크립트 블록을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-215">Enter a script block.</span></span> <span data-ttu-id="7cf53-216">이 키는 필수입니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-216">This key is required.</span></span>
- <span data-ttu-id="7cf53-217">옵션-함수 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-217">Options - Function options.</span></span> <span data-ttu-id="7cf53-218">이 키는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-218">This key is optional.</span></span> <span data-ttu-id="7cf53-219">기본값은 **None** 입니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-219">The default value is **None**.</span></span> <span data-ttu-id="7cf53-220">이 매개 변수에 허용 되는 값은 None, ReadOnly, Constant, Private 또는 AllScope입니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-220">The acceptable values for this parameter are: None, ReadOnly, Constant, Private, or AllScope.</span></span>

<span data-ttu-id="7cf53-221">예: `@{Name='Get-PowerShellProcess';ScriptBlock={Get-Process PowerShell};Options='AllScope'}`</span><span class="sxs-lookup"><span data-stu-id="7cf53-221">For example: `@{Name='Get-PowerShellProcess';ScriptBlock={Get-Process PowerShell};Options='AllScope'}`</span></span>

```yaml
Type: System.Collections.IDictionary[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7cf53-222">-Msds-groupmanagedserviceaccount</span><span class="sxs-lookup"><span data-stu-id="7cf53-222">-GroupManagedServiceAccount</span></span>

<span data-ttu-id="7cf53-223">지정 된 그룹 관리 서비스 계정의 컨텍스트에서 실행 되도록이 세션 구성을 사용 하 여 세션을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-223">Configures sessions using this session configuration to run under the context of the specified Group Managed Service Account.</span></span> <span data-ttu-id="7cf53-224">세션을 성공적으로 만들려면이 세션 구성이 등록 된 컴퓨터에 gMSA 암호를 요청할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-224">The machine where this session configuration is registered must have permission to request the gMSA password in order for sessions to be created successfully.</span></span> <span data-ttu-id="7cf53-225">이 필드는 **RunAsVirtualAccount** 매개 변수와 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-225">This field cannot be used with the **RunAsVirtualAccount** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7cf53-226">-Guid</span><span class="sxs-lookup"><span data-stu-id="7cf53-226">-Guid</span></span>

<span data-ttu-id="7cf53-227">세션 구성 파일의 고유 식별자를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-227">Specifies a unique identifier for the session configuration file.</span></span> <span data-ttu-id="7cf53-228">이 매개 변수를 생략 하면는 `New-PSSessionConfigurationFile` 파일에 대 한 GUID를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-228">If you omit this parameter, `New-PSSessionConfigurationFile` generates a GUID for the file.</span></span> <span data-ttu-id="7cf53-229">PowerShell에서 새 GUID를 만들려면를 입력 `New-Guid` 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-229">To create a new GUID in PowerShell, type `New-Guid`.</span></span>

```yaml
Type: System.Guid
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7cf53-230">-LanguageMode</span><span class="sxs-lookup"><span data-stu-id="7cf53-230">-LanguageMode</span></span>

<span data-ttu-id="7cf53-231">이 세션 구성을 사용 하는 세션에서 허용 되는 PowerShell 언어 요소를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-231">Determines which elements of the PowerShell language are permitted in sessions that use this session configuration.</span></span> <span data-ttu-id="7cf53-232">이 매개 변수를 사용하여 특정 사용자가 컴퓨터에서 실행할 수 있는 명령을 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-232">You can use this parameter to restrict the commands that particular users can run on the computer.</span></span>

<span data-ttu-id="7cf53-233">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-233">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="7cf53-234">FullLanguage-모든 언어 요소가 허용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-234">FullLanguage - All language elements are permitted.</span></span>
- <span data-ttu-id="7cf53-235">ConstrainedLanguage-평가할 스크립트가 포함 된 명령은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-235">ConstrainedLanguage - Commands that contain scripts to be evaluated are not allowed.</span></span> <span data-ttu-id="7cf53-236">ConstrainedLanguage 모드는 Microsoft .NET Framework 형식, 개체 또는 메서드에 대한 사용자 액세스를 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-236">The ConstrainedLanguage mode restricts user access to Microsoft .NET Framework types, objects, or methods.</span></span>
- <span data-ttu-id="7cf53-237">NoLanguage-사용자는 cmdlet 및 함수를 실행할 수 있지만 스크립트 블록, 변수 또는 연산자와 같은 언어 요소는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-237">NoLanguage - Users may run cmdlets and functions, but are not permitted to use any language elements, such as script blocks, variables, or operators.</span></span>
- <span data-ttu-id="7cf53-238">RestrictedLanguage-사용자는 cmdlet 및 함수를 실행할 수 있지만,,, `$PSCulture` `$PSUICulture` `$True` `$False` 및의 허용 되는 변수를 제외 하 고는 스크립트 블록이 나 변수를 사용할 `$Null` 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-238">RestrictedLanguage - Users may run cmdlets and functions, but are not permitted to use script blocks or variables except for the following permitted variables: `$PSCulture`, `$PSUICulture`, `$True`, `$False`, and `$Null`.</span></span> <span data-ttu-id="7cf53-239">사용자는 기본 비교 연산자 ( `-eq` ,,)만 사용할 수 있습니다 `-gt` `-lt` .</span><span class="sxs-lookup"><span data-stu-id="7cf53-239">Users may use only the basic comparison operators (`-eq`, `-gt`, `-lt`).</span></span> <span data-ttu-id="7cf53-240">대입문, 속성 참조 및 메서드 호출은 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-240">Assignment statements, property references, and method calls are not permitted.</span></span>

<span data-ttu-id="7cf53-241">**LanguageMode** 매개 변수의 기본값은 **SessionType** 매개 변수 값에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-241">The default value of the **LanguageMode** parameter depends on the value of the **SessionType** parameter.</span></span>

- <span data-ttu-id="7cf53-242">Empty-NoLanguage</span><span class="sxs-lookup"><span data-stu-id="7cf53-242">Empty - NoLanguage</span></span>
- <span data-ttu-id="7cf53-243">RestrictedRemoteServer-NoLanguage</span><span class="sxs-lookup"><span data-stu-id="7cf53-243">RestrictedRemoteServer - NoLanguage</span></span>
- <span data-ttu-id="7cf53-244">기본값-FullLanguage</span><span class="sxs-lookup"><span data-stu-id="7cf53-244">Default - FullLanguage</span></span>

```yaml
Type: System.Management.Automation.PSLanguageMode
Parameter Sets: (All)
Aliases:
Accepted values: FullLanguage, RestrictedLanguage, NoLanguage, ConstrainedLanguage

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7cf53-245">-ModulesToImport</span><span class="sxs-lookup"><span data-stu-id="7cf53-245">-ModulesToImport</span></span>

<span data-ttu-id="7cf53-246">세션 구성을 사용하는 세션에 자동으로 가져오는 모듈 및 스냅인을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-246">Specifies the modules and snap-ins that are automatically imported into sessions that use the session configuration.</span></span>

<span data-ttu-id="7cf53-247">기본적으로는 **Microsoft. PowerShell. 코어** 스냅인만 원격 세션으로 가져올 수 있지만 cmdlet을 제외 하지 않는 한 사용자는 및 cmdlet을 사용 하 여 `Import-Module` `Add-PSSnapin` 모듈 및 스냅인을 세션에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-247">By default, only the **Microsoft.PowerShell.Core** snap-in is imported into remote sessions, but unless the cmdlets are excluded, users can use the `Import-Module` and `Add-PSSnapin` cmdlets to add modules and snap-ins to the session.</span></span>

<span data-ttu-id="7cf53-248">이 매개 변수 값의 각 모듈이나 스냅인을 문자열 또는 해시 테이블로 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-248">Each module or snap-in in the value of this parameter can be represented by a string or as a hash table.</span></span> <span data-ttu-id="7cf53-249">모듈 문자열은 모듈이 나 스냅인의 이름 으로만 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-249">A module string consists only of the name of the module or snap-in.</span></span> <span data-ttu-id="7cf53-250">모듈 해시 테이블에는 **ModuleName**, **ModuleVersion** 및 **GUID** 키가 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-250">A module hash table can include **ModuleName**, **ModuleVersion**, and **GUID** keys.</span></span> <span data-ttu-id="7cf53-251">**ModuleName** 키만 필수입니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-251">Only the **ModuleName** key is required.</span></span>

<span data-ttu-id="7cf53-252">예를 들어 다음 값은 문자열과 해시 테이블로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-252">For example, the following value consists of a string and a hash table.</span></span> <span data-ttu-id="7cf53-253">순서와 관계없이 문자열과 해시 테이블의 모든 조합이 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-253">Any combination of strings and hash tables, in any order, is valid.</span></span>

`'TroubleshootingPack', @{ModuleName='PSDiagnostics'; ModuleVersion='1.0.0.0';GUID='c61d6278-02a3-4618-ae37-a524d40a7f44'}`

<span data-ttu-id="7cf53-254">Cmdlet의 **ModulesToImport** 매개 변수 값은 `Register-PSSessionConfiguration` 세션 구성 파일에 있는 **ModulesToImport** 키의 값 보다 우선 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-254">The value of the **ModulesToImport** parameter of the `Register-PSSessionConfiguration` cmdlet takes precedence over the value of the **ModulesToImport** key in the session configuration file.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7cf53-255">-MountUserDrive</span><span class="sxs-lookup"><span data-stu-id="7cf53-255">-MountUserDrive</span></span>

<span data-ttu-id="7cf53-256">PSDrive를 노출 하기 위해이 세션 구성을 사용 하는 세션을 구성 `User:` 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-256">Configures sessions that use this session configuration to expose the `User:` PSDrive.</span></span> <span data-ttu-id="7cf53-257">사용자 드라이브는 연결 하는 각 사용자에 대해 고유 하며, 파일 시스템 공급자가 노출 되지 않은 경우에도 사용자가 PowerShell 끝점 간에 데이터를 복사할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-257">User drives are unique for each connecting user and allow users to copy data to and from PowerShell endpoints even if the File System provider is not exposed.</span></span> <span data-ttu-id="7cf53-258">사용자 드라이브 루트는 아래에 생성 됩니다 `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\DriveRoots\` .</span><span class="sxs-lookup"><span data-stu-id="7cf53-258">User drive roots are created under `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\DriveRoots\`.</span></span> <span data-ttu-id="7cf53-259">엔드포인트에 연결하는 각 사용자에 대해 `$env:USERDOMAIN_$env:USERNAME`이라는 이름으로 폴더가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-259">For each user connecting to the endpoint, a folder is created with the name `$env:USERDOMAIN_$env:USERNAME`.</span></span>

<span data-ttu-id="7cf53-260">사용자 드라이브의 콘텐츠는 사용자 세션에서 유지 되며 자동으로 제거 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-260">Contents in the user drive persist across user sessions and are not automatically removed.</span></span> <span data-ttu-id="7cf53-261">기본적으로 사용자는 사용자 드라이브에 최대 50MB의 데이터를 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-261">By default, users can only store up to 50MB of data in the user drive.</span></span> <span data-ttu-id="7cf53-262">**UserDriveMaximumSize** 매개 변수를 사용 하 여 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-262">This can be customized with the **UserDriveMaximumSize** parameter.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7cf53-263">-Path</span><span class="sxs-lookup"><span data-stu-id="7cf53-263">-Path</span></span>

<span data-ttu-id="7cf53-264">세션 구성 파일의 경로와 파일 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-264">Specifies the path and filename of the session configuration file.</span></span> <span data-ttu-id="7cf53-265">파일에는 `.pssc` 파일 이름 확장명이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-265">The file must have a `.pssc` file name extension.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7cf53-266">-PowerShellVersion</span><span class="sxs-lookup"><span data-stu-id="7cf53-266">-PowerShellVersion</span></span>

<span data-ttu-id="7cf53-267">세션 구성을 사용 하는 세션의 PowerShell 엔진 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-267">Specifies the version of the PowerShell engine in sessions that use the session configuration.</span></span> <span data-ttu-id="7cf53-268">이 매개 변수에 허용 되는 값은 2.0 및 3.0입니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-268">The acceptable values for this parameter are: 2.0 and 3.0.</span></span> <span data-ttu-id="7cf53-269">이 매개 변수를 생략 하면 **PowerShellVersion** 키가 주석으로 처리 되 고 최신 버전의 PowerShell이 세션에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-269">If you omit this parameter, the **PowerShellVersion** key is commented-out and newest version of PowerShell runs in the session.</span></span>

<span data-ttu-id="7cf53-270">Cmdlet의 **PSVersion** 매개 변수 값은 `Register-PSSessionConfiguration` 세션 구성 파일에 있는 **PowerShellVersion** 키의 값 보다 우선 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-270">The value of the **PSVersion** parameter of the `Register-PSSessionConfiguration` cmdlet takes precedence over the value of the **PowerShellVersion** key in the session configuration file.</span></span>

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7cf53-271">-RequiredGroups</span><span class="sxs-lookup"><span data-stu-id="7cf53-271">-RequiredGroups</span></span>

<span data-ttu-id="7cf53-272">이 세션 구성을 사용 하는 세션에 연결 하는 사용자에 대 한 조건부 액세스 규칙을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-272">Specifies conditional access rules for users connecting to sessions that use this session configuration.</span></span>

<span data-ttu-id="7cf53-273">해시 테이블을 입력 하 여 해시 테이블, ' And ' 또는 ' Or ' 당 1 개의 키만 사용 하 여 규칙 목록을 작성 하 고, 값을 보안 그룹 이름 또는 추가 해시 테이블으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-273">Enter a hashtable to compose your list of rules using only 1 key per hashtable, 'And' or 'Or', and set the value to an array of security group names or additional hashtables.</span></span>

<span data-ttu-id="7cf53-274">사용자를 단일 그룹의 구성원으로 연결 해야 하는 예는 다음과 같습니다. `@{ And = 'MyRequiredGroup' }`</span><span class="sxs-lookup"><span data-stu-id="7cf53-274">Example requiring connecting users to be members of a single group: `@{ And = 'MyRequiredGroup' }`</span></span>

<span data-ttu-id="7cf53-275">끝점에 액세스 하려면 사용자가 그룹 A 또는 그룹 B와 C 모두에 속해야 하는 예입니다. `@{ Or = 'GroupA', @{ And = 'GroupB', 'GroupC' } }`</span><span class="sxs-lookup"><span data-stu-id="7cf53-275">Example requiring users to belong to group A, or both groups B and C, to access the endpoint: `@{ Or = 'GroupA', @{ And = 'GroupB', 'GroupC' } }`</span></span>

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7cf53-276">-RoleDefinitions</span><span class="sxs-lookup"><span data-stu-id="7cf53-276">-RoleDefinitions</span></span>

<span data-ttu-id="7cf53-277">보안 그룹 (또는 사용자)과 역할 기능 간의 매핑을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-277">Specifies the mapping between security groups (or users) and role capabilities.</span></span> <span data-ttu-id="7cf53-278">사용자에 게는 세션이 만들어질 때 그룹 구성원 자격에 적용 되는 모든 역할 기능에 대 한 액세스 권한이 부여 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-278">Users will be granted access to all role capabilities which apply to their group membership at the time the session is created.</span></span>

<span data-ttu-id="7cf53-279">키가 보안 그룹의 이름이 고 값은 보안 그룹에 사용할 수 있는 역할 기능 목록을 포함 하는 해시 테이블인 해시 테이블을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-279">Enter a hash table in which the keys are the name of the security group and the values are hash tables that contain a list of role capabilities that should be made available to the security group.</span></span>

<span data-ttu-id="7cf53-280">예: `@{'Contoso\Level 2 Helpdesk Users' = @{ RoleCapabilities = 'Maintenance', 'ADHelpDesk' }}`</span><span class="sxs-lookup"><span data-stu-id="7cf53-280">For example: `@{'Contoso\Level 2 Helpdesk Users' = @{ RoleCapabilities = 'Maintenance', 'ADHelpDesk' }}`</span></span>

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7cf53-281">-RunAsVirtualAccount</span><span class="sxs-lookup"><span data-stu-id="7cf53-281">-RunAsVirtualAccount</span></span>

<span data-ttu-id="7cf53-282">컴퓨터의 (가상) 관리자 계정으로 실행 되도록이 세션 구성을 사용 하 여 세션을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-282">Configures sessions using this session configuration to be run as the computer's (virtual) administrator account.</span></span> <span data-ttu-id="7cf53-283">이 필드는 **msds-groupmanagedserviceaccount** 매개 변수와 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-283">This field cannot be used with the **GroupManagedServiceAccount** parameter.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7cf53-284">-RunAsVirtualAccountGroups</span><span class="sxs-lookup"><span data-stu-id="7cf53-284">-RunAsVirtualAccountGroups</span></span>

<span data-ttu-id="7cf53-285">세션 구성을 사용 하는 세션이 가상 계정으로 실행 되는 경우 가상 계정과 연결 될 보안 그룹을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-285">Specifies the security groups to be associated with the virtual account when a session that uses the session configuration is run as a virtual account.</span></span> <span data-ttu-id="7cf53-286">생략 하는 경우 가상 계정은 다른 모든 컴퓨터의 도메인 컨트롤러 및 관리자 도메인 관리자에 속합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-286">If omitted, the virtual account belongs to Domain Admins on domain controllers and Administrators on all other computers.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7cf53-287">-SchemaVersion</span><span class="sxs-lookup"><span data-stu-id="7cf53-287">-SchemaVersion</span></span>

<span data-ttu-id="7cf53-288">세션 구성 파일 스키마의 버전을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-288">Specifies the version of the session configuration file schema.</span></span> <span data-ttu-id="7cf53-289">기본값은 "1.0.0.0"입니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-289">The default value is "1.0.0.0".</span></span>

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7cf53-290">-ScriptsToProcess</span><span class="sxs-lookup"><span data-stu-id="7cf53-290">-ScriptsToProcess</span></span>

<span data-ttu-id="7cf53-291">세션 구성을 사용하는 세션에 지정된 스크립트를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-291">Adds the specified scripts to sessions that use the session configuration.</span></span> <span data-ttu-id="7cf53-292">스크립트의 경로와 파일 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-292">Enter the path and file names of the scripts.</span></span> <span data-ttu-id="7cf53-293">이 매개 변수 값은 스크립트 파일 이름의 전체 또는 절대 경로 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-293">The value of this parameter must be a full or absolute path of script file names.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7cf53-294">-SessionType</span><span class="sxs-lookup"><span data-stu-id="7cf53-294">-SessionType</span></span>

<span data-ttu-id="7cf53-295">세션 구성을 사용하여 만들어진 세션의 유형을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-295">Specifies the type of session that is created by using the session configuration.</span></span> <span data-ttu-id="7cf53-296">기본값은 Default입니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-296">The default value is Default.</span></span> <span data-ttu-id="7cf53-297">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-297">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="7cf53-298">Empty-기본적으로 세션에 모듈을 추가 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-298">Empty - No modules are added to session by default.</span></span> <span data-ttu-id="7cf53-299">이 cmdlet의 매개 변수를 사용하여 모듈, 함수, 스크립트 및 기타 기능을 세션에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-299">Use the parameters of this cmdlet to add modules, functions, scripts, and other features to the session.</span></span> <span data-ttu-id="7cf53-300">이 옵션은 선택한 명령을 추가 하 여 사용자 지정 세션을 만들 수 있도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-300">This option is designed for you to create custom sessions by adding selected commands.</span></span> <span data-ttu-id="7cf53-301">빈 세션에 명령을 추가하지 않을 경우 세션이 식으로 제한되며 세션을 사용하지 못할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-301">If you do not add commands to an empty session, the session is limited to expressions and might not be usable.</span></span>
- <span data-ttu-id="7cf53-302">기본값-세션에 Microsoft. PowerShell 핵심 모듈을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-302">Default - Adds the Microsoft.PowerShell.Core module to the session.</span></span> <span data-ttu-id="7cf53-303">이 모듈에는 `Import-Module` 이 cmdlet을 명시적으로 금지 하지 않는 한 사용자가 다른 모듈을 가져오는 데 사용할 수 있는 cmdlet이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-303">This module includes the `Import-Module` cmdlet that users can use to import other modules unless you explicitly prohibit this cmdlet.</span></span>
- <span data-ttu-id="7cf53-304">RestrictedRemoteServer.</span><span class="sxs-lookup"><span data-stu-id="7cf53-304">RestrictedRemoteServer.</span></span> <span data-ttu-id="7cf53-305">에는,,,,, `Exit-PSSession` `Get-Command` `Get-FormatData` `Get-Help` `Measure-Object` `Out-Default` 및와 `Select-Object` 같은 프록시 함수만 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-305">Includes only the following proxy functions: `Exit-PSSession`, `Get-Command`, `Get-FormatData`, `Get-Help`, `Measure-Object`, `Out-Default`, and `Select-Object`.</span></span>
  <span data-ttu-id="7cf53-306">이 cmdlet의 매개 변수를 사용하여 모듈, 함수, 스크립트 및 기타 기능을 세션에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-306">Use the parameters of this cmdlet to add modules, functions, scripts, and other features to the session.</span></span>

```yaml
Type: System.Management.Automation.Remoting.SessionType
Parameter Sets: (All)
Aliases:
Accepted values: Empty, RestrictedRemoteServer, Default

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7cf53-307">-TranscriptDirectory</span><span class="sxs-lookup"><span data-stu-id="7cf53-307">-TranscriptDirectory</span></span>

<span data-ttu-id="7cf53-308">이 세션 구성을 사용 하 여 세션에 대 한 세션 기록을 저장할 디렉터리를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-308">Specifies the directory to place session transcripts for sessions using this session configuration.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7cf53-309">-TypesToProcess</span><span class="sxs-lookup"><span data-stu-id="7cf53-309">-TypesToProcess</span></span>

<span data-ttu-id="7cf53-310">`.ps1xml`세션 구성을 사용 하는 세션에 지정 된 형식 파일을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-310">Adds the specified `.ps1xml` type files to sessions that use the session configuration.</span></span> <span data-ttu-id="7cf53-311">유형 파일 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-311">Enter the type filenames.</span></span> <span data-ttu-id="7cf53-312">이 매개 변수 값은 형식 파일 이름의 전체 또는 절대 경로 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-312">The value of this parameter must be a full or absolute path to type filenames.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7cf53-313">-UserDriveMaximumSize</span><span class="sxs-lookup"><span data-stu-id="7cf53-313">-UserDriveMaximumSize</span></span>

<span data-ttu-id="7cf53-314">이 세션 구성을 사용 하는 세션에 노출 되는 사용자 드라이브의 최대 크기를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-314">Specifies the maximum size for user drives exposed in sessions that use this session configuration.</span></span>
<span data-ttu-id="7cf53-315">생략 하는 경우 각 드라이브 루트의 기본 크기는 `User:` 50MB입니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-315">When omitted, the default size of each `User:` drive root is 50MB.</span></span>

<span data-ttu-id="7cf53-316">이 매개 변수는 **MountUserDrive** 와 함께 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-316">This parameter should be used with **MountUserDrive**.</span></span>

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7cf53-317">-VariableDefinitions</span><span class="sxs-lookup"><span data-stu-id="7cf53-317">-VariableDefinitions</span></span>

<span data-ttu-id="7cf53-318">세션 구성을 사용하는 세션에 지정된 변수를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-318">Adds the specified variables to sessions that use the session configuration.</span></span> <span data-ttu-id="7cf53-319">다음 키를 사용하여 해시 테이블을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-319">Enter a hash table with the following keys:</span></span>

- <span data-ttu-id="7cf53-320">이름-변수의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-320">Name - Name of the variable.</span></span> <span data-ttu-id="7cf53-321">이 키는 필수입니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-321">This key is required.</span></span>
- <span data-ttu-id="7cf53-322">값-변수 값입니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-322">Value - Variable value.</span></span> <span data-ttu-id="7cf53-323">이 키는 필수입니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-323">This key is required.</span></span>
- <span data-ttu-id="7cf53-324">옵션-변수 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-324">Options - Variable options.</span></span> <span data-ttu-id="7cf53-325">이 키는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-325">This key is optional.</span></span> <span data-ttu-id="7cf53-326">기본값은 **None** 입니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-326">The default value is **None**.</span></span> <span data-ttu-id="7cf53-327">이 매개 변수에 허용 되는 값은 None, ReadOnly, Constant, Private 또는 AllScope입니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-327">The acceptable values for this parameter are: None, ReadOnly, Constant, Private, or AllScope.</span></span>

<span data-ttu-id="7cf53-328">예: `@{Name='WarningPreference';Value='SilentlyContinue';Options='AllScope'}`</span><span class="sxs-lookup"><span data-stu-id="7cf53-328">For example: `@{Name='WarningPreference';Value='SilentlyContinue';Options='AllScope'}`</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7cf53-329">-VisibleAliases</span><span class="sxs-lookup"><span data-stu-id="7cf53-329">-VisibleAliases</span></span>

<span data-ttu-id="7cf53-330">세션의 별칭을 이 매개 변수 값에 지정된 별칭 및 **AliasDefinition** 매개 변수에 정의한 별칭으로 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-330">Limits the aliases in the session to those specified in the value of this parameter, plus any aliases that you define in the **AliasDefinition** parameter.</span></span> <span data-ttu-id="7cf53-331">와일드카드 문자가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-331">Wildcard characters are supported.</span></span> <span data-ttu-id="7cf53-332">기본적으로 PowerShell 엔진에서 정의한 모든 별칭과 모듈에서 내보낸 모든 별칭이 세션에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-332">By default, all aliases that are defined by the PowerShell engine and all aliases that modules export are visible in the session.</span></span>

<span data-ttu-id="7cf53-333">예: `VisibleAliases='gcm', 'gp'`</span><span class="sxs-lookup"><span data-stu-id="7cf53-333">For example: `VisibleAliases='gcm', 'gp'`</span></span>

<span data-ttu-id="7cf53-334">**표시** 되는 매개 변수가 세션 구성 파일에 포함 된 경우 PowerShell은 `Import-Module` 세션에서 cmdlet 및 해당 ipmo 별칭을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-334">When any **Visible** parameter is included in the session configuration file, PowerShell removes the `Import-Module` cmdlet and its ipmo alias from the session.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="7cf53-335">-VisibleCmdlets</span><span class="sxs-lookup"><span data-stu-id="7cf53-335">-VisibleCmdlets</span></span>

<span data-ttu-id="7cf53-336">세션의 cmdlet을 이 매개 변수 값에 지정된 cmdlet으로 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-336">Limits the cmdlets in the session to those specified in the value of this parameter.</span></span> <span data-ttu-id="7cf53-337">와일드 카드 문자 및 모듈 정규화 된 이름이 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-337">Wildcard characters and Module Qualified Names are supported.</span></span>

<span data-ttu-id="7cf53-338">기본적으로 세션의 모듈에서 내보낸 모든 cmdlet이 세션에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-338">By default, all cmdlets that modules in the session export are visible in the session.</span></span> <span data-ttu-id="7cf53-339">**SessionType** 및 **ModulesToImport** 매개 변수를 사용하여 세션으로 가져올 모듈과 스냅인을 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-339">Use the **SessionType** and **ModulesToImport** parameters to determine which modules and snap-ins are imported into the session.</span></span> <span data-ttu-id="7cf53-340">**ModulesToImport** 에서 cmdlet을 노출 하는 모듈이 없으면 적절 한 모듈이 자동 로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-340">If no modules in **ModulesToImport** expose the cmdlet, the appropriate module will attempt to be autoloaded.</span></span>

<span data-ttu-id="7cf53-341">**표시** 되는 매개 변수가 세션 구성 파일에 포함 된 경우 PowerShell은 `Import-Module` 세션에서 cmdlet 및 해당 ipmo 별칭을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-341">When any **Visible** parameter is included in the session configuration file, PowerShell removes the `Import-Module` cmdlet and its ipmo alias from the session.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7cf53-342">-VisibleExternalCommands</span><span class="sxs-lookup"><span data-stu-id="7cf53-342">-VisibleExternalCommands</span></span>

<span data-ttu-id="7cf53-343">세션에서 실행할 수 있는 외부 이진 파일, 스크립트 및 명령을이 매개 변수 값에 지정 된 것으로 제한 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-343">Limits the external binaries, scripts, and commands that can be executed in the session to those specified in the value of this parameter.</span></span> <span data-ttu-id="7cf53-344">와일드카드 문자가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-344">Wildcard characters are supported.</span></span>

<span data-ttu-id="7cf53-345">기본적으로 세션에는 외부 명령이 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-345">By default, no external commands are visible in the session.</span></span>

<span data-ttu-id="7cf53-346">**표시** 되는 매개 변수가 세션 구성 파일인 PowerShell에 포함 된 경우 `Import-Module` 세션에서 cmdlet 및 해당 ipmo 별칭을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-346">When any **Visible** parameter is included in the session configuration file, PowerShell, removes the `Import-Module` cmdlet and its ipmo alias from the session.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="7cf53-347">-VisibleFunctions</span><span class="sxs-lookup"><span data-stu-id="7cf53-347">-VisibleFunctions</span></span>

<span data-ttu-id="7cf53-348">세션의 함수를 이 매개 변수 값에 지정된 함수 및 **FunctionDefinition** 매개 변수에 정의한 함수로 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-348">Limits the functions in the session to those specified in the value of this parameter, plus any functions that you define in the **FunctionDefinition** parameter.</span></span> <span data-ttu-id="7cf53-349">와일드카드 문자가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-349">Wildcard characters are supported.</span></span>

<span data-ttu-id="7cf53-350">기본적으로 세션의 모듈에서 내보낸 모든 함수가 세션에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-350">By default, all functions that modules in the session export are visible in the session.</span></span> <span data-ttu-id="7cf53-351">**SessionType** 및 **ModulesToImport** 매개 변수를 사용하여 세션으로 가져올 모듈과 스냅인을 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-351">Use the **SessionType** and **ModulesToImport** parameters to determine which modules and snap-ins are imported into the session.</span></span>

<span data-ttu-id="7cf53-352">**표시** 되는 매개 변수가 세션 구성 파일에 포함 된 경우 PowerShell은 `Import-Module` 세션에서 cmdlet 및 해당 ipmo 별칭을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-352">When any **Visible** parameter is included in the session configuration file, PowerShell removes the `Import-Module` cmdlet and its ipmo alias from the session.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="7cf53-353">-VisibleProviders</span><span class="sxs-lookup"><span data-stu-id="7cf53-353">-VisibleProviders</span></span>

<span data-ttu-id="7cf53-354">세션의 PowerShell 공급자를이 매개 변수 값에 지정 된 공급자로 제한 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-354">Limits the PowerShell providers in the session to those specified in the value of this parameter.</span></span>
<span data-ttu-id="7cf53-355">와일드카드 문자가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-355">Wildcard characters are supported.</span></span>

<span data-ttu-id="7cf53-356">기본적으로 세션의 모듈에서 내보낸 모든 공급자가 세션에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-356">By default, all providers that modules in the session export are visible in the session.</span></span> <span data-ttu-id="7cf53-357">**SessionType** 및 **ModulesToImport** 매개 변수를 사용 하 여 세션으로 가져올 모듈을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-357">Use the **SessionType** and **ModulesToImport** parameters to determine which modules are imported into the session.</span></span>

<span data-ttu-id="7cf53-358">**표시** 되는 매개 변수가 세션 구성 파일에 포함 된 경우 PowerShell은 `Import-Module` 세션에서 cmdlet 및 해당 별칭을 제거 합니다 `ipmo` .</span><span class="sxs-lookup"><span data-stu-id="7cf53-358">When any **Visible** parameter is included in the session configuration file, PowerShell removes the `Import-Module` cmdlet and its `ipmo` alias from the session.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="7cf53-359">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7cf53-359">CommonParameters</span></span>

<span data-ttu-id="7cf53-360">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="7cf53-360">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7cf53-361">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7cf53-361">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7cf53-362">입력</span><span class="sxs-lookup"><span data-stu-id="7cf53-362">INPUTS</span></span>

### <span data-ttu-id="7cf53-363">없음</span><span class="sxs-lookup"><span data-stu-id="7cf53-363">None</span></span>

<span data-ttu-id="7cf53-364">개체를이 cmdlet으로 파이프 할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-364">You cannot pipe any objects to this cmdlet.</span></span>

## <span data-ttu-id="7cf53-365">출력</span><span class="sxs-lookup"><span data-stu-id="7cf53-365">OUTPUTS</span></span>

### <span data-ttu-id="7cf53-366">없음</span><span class="sxs-lookup"><span data-stu-id="7cf53-366">None</span></span>

<span data-ttu-id="7cf53-367">이 cmdlet은 어떠한 출력도 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-367">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="7cf53-368">참고</span><span class="sxs-lookup"><span data-stu-id="7cf53-368">NOTES</span></span>

<span data-ttu-id="7cf53-369">이 cmdlet은 Windows 플랫폼 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-369">This cmdlet is only available on Windows platforms.</span></span>

- <span data-ttu-id="7cf53-370">**VisibleCmdlets** 및 **VisibleProviders** 와 같은 매개 변수는 항목을 세션으로 가져오지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-370">Parameters, such as **VisibleCmdlets** and **VisibleProviders**, do not import items into the session.</span></span> <span data-ttu-id="7cf53-371">대신, 세션으로 가져온 항목 중에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-371">Instead, they select from among the items imported into the session.</span></span> <span data-ttu-id="7cf53-372">예를 들어 **VisibleProviders** 매개 변수 값이 인증서 공급자 이지만 **ModulesToImport** 매개 변수는 인증서 공급자를 포함 하는 **Microsoft. PowerShell. Security** 모듈을 지정 하지 않으면 세션에 인증서 공급자가 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-372">For example, if the value of the **VisibleProviders** parameter is the Certificate provider, but the **ModulesToImport** parameter does not specify the **Microsoft.PowerShell.Security** module that contains the Certificate provider, the Certificate provider is not visible in the session.</span></span>
- <span data-ttu-id="7cf53-373">`New-PSSessionConfigurationFile`**path** 매개 변수에 지정 하는 경로에 .psc 파일 이름 확장명을 가진 세션 구성 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-373">`New-PSSessionConfigurationFile` creates a session configuration file that has a .pssc file name extension in the path that you specify in the **Path** parameter.</span></span> <span data-ttu-id="7cf53-374">세션 구성 파일을 사용 하 여 세션 구성을 만드는 경우 `Register-PSSessionConfiguration` cmdlet은 구성 파일을 복사 하 고 파일의 활성 복사본을 디렉터리의 **sessionconfig** 하위 디렉터리에 저장 `$PSHOME` 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-374">When you use the session configuration file to create a session configuration, the `Register-PSSessionConfiguration` cmdlet copies the configuration file and saves an active copy of the file in the **SessionConfig** subdirectory of the `$PSHOME` directory.</span></span>

  <span data-ttu-id="7cf53-375">세션 구성의 **Configfilepath** 속성에는 활성 세션 구성 파일의 정규화 된 경로가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-375">The **ConfigFilePath** property of the session configuration contains the fully qualified path of the active session configuration file.</span></span> <span data-ttu-id="7cf53-376">언제 든 `$PSHOME` 지 모든 텍스트 편집기를 사용 하 여 디렉터리의 활성 구성 파일을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-376">You can modify the active configuration file in the `$PSHOME` directory at any time using any text editor.</span></span> <span data-ttu-id="7cf53-377">변경 내용은 세션 구성을 사용하는 모든 새 세션에 영향을 주지만 기존 세션에는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-377">The changes that you make affect all new sessions that use the session configuration, but not existing sessions.</span></span>

  <span data-ttu-id="7cf53-378">편집 된 세션 구성 파일을 사용 하기 전에 cmdlet을 사용 `Test-PSSessionConfigurationFile` 하 여 구성 파일 항목이 유효한 지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cf53-378">Before using an edited session configuration file, use the `Test-PSSessionConfigurationFile` cmdlet to verify that the configuration file entries are valid.</span></span>

## <span data-ttu-id="7cf53-379">관련 링크</span><span class="sxs-lookup"><span data-stu-id="7cf53-379">RELATED LINKS</span></span>

[<span data-ttu-id="7cf53-380">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="7cf53-380">Disable-PSSessionConfiguration</span></span>](Disable-PSSessionConfiguration.md)

[<span data-ttu-id="7cf53-381">Enable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="7cf53-381">Enable-PSSessionConfiguration</span></span>](Enable-PSSessionConfiguration.md)

[<span data-ttu-id="7cf53-382">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="7cf53-382">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="7cf53-383">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="7cf53-383">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="7cf53-384">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="7cf53-384">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

[<span data-ttu-id="7cf53-385">Test-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="7cf53-385">Test-PSSessionConfigurationFile</span></span>](Test-PSSessionConfigurationFile.md)

[<span data-ttu-id="7cf53-386">Unregister-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="7cf53-386">Unregister-PSSessionConfiguration</span></span>](Unregister-PSSessionConfiguration.md)

[<span data-ttu-id="7cf53-387">WSMan 공급자</span><span class="sxs-lookup"><span data-stu-id="7cf53-387">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[<span data-ttu-id="7cf53-388">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="7cf53-388">about_Session_Configurations</span></span>](About/about_Session_Configurations.md)

[<span data-ttu-id="7cf53-389">about_Session_Configuration_Files</span><span class="sxs-lookup"><span data-stu-id="7cf53-389">about_Session_Configuration_Files</span></span>](About/about_Session_Configuration_Files.md)