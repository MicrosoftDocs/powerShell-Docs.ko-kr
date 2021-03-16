---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 05/20/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-command?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Command
ms.openlocfilehash: 1d54082ee313c0e8d4ee7911f89da150aeba9d55
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599340"
---
# <span data-ttu-id="1f095-102">Get-Command</span><span class="sxs-lookup"><span data-stu-id="1f095-102">Get-Command</span></span>

## <span data-ttu-id="1f095-103">개요</span><span class="sxs-lookup"><span data-stu-id="1f095-103">SYNOPSIS</span></span>
<span data-ttu-id="1f095-104">모든 명령을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-104">Gets all commands.</span></span>

## <span data-ttu-id="1f095-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="1f095-105">SYNTAX</span></span>

### <span data-ttu-id="1f095-106">CmdletSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="1f095-106">CmdletSet (Default)</span></span>

```
Get-Command [-Verb <String[]>] [-Noun <String[]>] [-Module <String[]>]
 [-FullyQualifiedModule <ModuleSpecification[]>] [-TotalCount <Int32>] [-Syntax] [-ShowCommandInfo]
 [[-ArgumentList] <Object[]>] [-All] [-ListImported] [-ParameterName <String[]>]
 [-ParameterType <PSTypeName[]>] [<CommonParameters>]
```

### <span data-ttu-id="1f095-107">AllCommandSet</span><span class="sxs-lookup"><span data-stu-id="1f095-107">AllCommandSet</span></span>

```
Get-Command [[-Name] <String[]>] [-Module <String[]>]
 [-FullyQualifiedModule <ModuleSpecification[]>] [-CommandType <CommandTypes>] [-TotalCount <Int32>]
 [-Syntax] [-ShowCommandInfo] [[-ArgumentList] <Object[]>] [-All] [-ListImported]
 [-ParameterName <String[]>] [-ParameterType <PSTypeName[]>] [-UseFuzzyMatching]
 [-UseAbbreviationExpansion] [<CommonParameters>]
```

## <span data-ttu-id="1f095-108">설명</span><span class="sxs-lookup"><span data-stu-id="1f095-108">DESCRIPTION</span></span>

<span data-ttu-id="1f095-109">`Get-Command`Cmdlet은 cmdlet, 별칭, 함수, 필터, 스크립트 및 응용 프로그램을 포함 하 여 컴퓨터에 설치 된 모든 명령을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-109">The `Get-Command` cmdlet gets all commands that are installed on the computer, including cmdlets, aliases, functions, filters, scripts, and applications.</span></span> <span data-ttu-id="1f095-110">`Get-Command` 다른 세션에서 가져온 명령 및 PowerShell 모듈에서 명령을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-110">`Get-Command` gets the commands from PowerShell modules and commands that were imported from other sessions.</span></span> <span data-ttu-id="1f095-111">현재 세션으로 가져온 명령만 가져오려면 **ListImported** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-111">To get only commands that have been imported into the current session, use the **ListImported** parameter.</span></span>

<span data-ttu-id="1f095-112">매개 변수가 없으면 `Get-Command` 컴퓨터에 설치 된 모든 cmdlet, 함수 및 별칭을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-112">Without parameters, `Get-Command` gets all of the cmdlets, functions, and aliases installed on the computer.</span></span> <span data-ttu-id="1f095-113">`Get-Command *``$env:Path`응용 프로그램 명령 유형에 나열 되는 Path 환경 변수 ()에 있는 모든 비 PowerShell 파일을 포함 하는 모든 명령 유형을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-113">`Get-Command *` gets all types of commands, including all of the non-PowerShell files in the Path environment variable (`$env:Path`), which it lists in the Application command type.</span></span>

<span data-ttu-id="1f095-114">`Get-Command` 와일드 카드 문자 없이 명령의 정확한 이름을 사용 하면 명령을 즉시 사용할 수 있도록 명령이 포함 된 모듈을 자동으로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-114">`Get-Command` that uses the exact name of the command, without wildcard characters, automatically imports the module that contains the command so that you can use the command immediately.</span></span> <span data-ttu-id="1f095-115">모듈 자동 가져오기를 사용 하거나 사용 하지 않도록 설정 하 고 구성 하려면 `$PSModuleAutoLoadingPreference` 기본 설정 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-115">To enable, disable, and configure automatic importing of modules, use the `$PSModuleAutoLoadingPreference` preference variable.</span></span> <span data-ttu-id="1f095-116">자세한 내용은 [about_Preference_Variables](About/about_Preference_Variables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1f095-116">For more information, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="1f095-117">`Get-Command` 도움말 항목에서 정보를 가져오는와는 달리 명령 코드에서 직접 데이터를 가져옵니다 `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="1f095-117">`Get-Command` gets its data directly from the command code, unlike `Get-Help`, which gets its information from help topics.</span></span>

<span data-ttu-id="1f095-118">Windows PowerShell 5.0부터 cmdlet의 결과에는 `Get-Command` 기본적으로 **버전** 열이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-118">Starting in Windows PowerShell 5.0, results of the `Get-Command` cmdlet display a **Version** column by default.</span></span> <span data-ttu-id="1f095-119">새 **버전** 속성이 **commandinfo** 클래스에 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-119">A new **Version** property has been added to the **CommandInfo** class.</span></span>

## <span data-ttu-id="1f095-120">예제</span><span class="sxs-lookup"><span data-stu-id="1f095-120">EXAMPLES</span></span>

### <span data-ttu-id="1f095-121">예제 1: cmdlet, 함수 및 별칭 가져오기</span><span class="sxs-lookup"><span data-stu-id="1f095-121">Example 1: Get cmdlets, functions, and aliases</span></span>

<span data-ttu-id="1f095-122">이 명령은 컴퓨터에 설치 된 PowerShell cmdlet, 함수 및 별칭을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-122">This command gets the PowerShell cmdlets, functions, and aliases that are installed on the computer.</span></span>

```powershell
Get-Command
```

### <span data-ttu-id="1f095-123">예 2: 현재 세션의 명령 가져오기</span><span class="sxs-lookup"><span data-stu-id="1f095-123">Example 2: Get commands in the current session</span></span>

<span data-ttu-id="1f095-124">이 명령은 **ListImported** 매개 변수를 사용하여 현재 세션의 명령만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-124">This command uses the **ListImported** parameter to get only the commands in the current session.</span></span>

```powershell
Get-Command -ListImported
```

### <span data-ttu-id="1f095-125">예제 3: cmdlet 가져오기 및 순서 대로 표시</span><span class="sxs-lookup"><span data-stu-id="1f095-125">Example 3: Get cmdlets and display them in order</span></span>

<span data-ttu-id="1f095-126">이 명령은 모든 cmdlet을 가져오고 cmdlet 이름에 포함된 명사의 사전순으로 정렬한 다음 명사 기반 그룹으로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-126">This command gets all of the cmdlets, sorts them alphabetically by the noun in the cmdlet name, and then displays them in noun-based groups.</span></span> <span data-ttu-id="1f095-127">이 표시를 사용하여 특정 작업에 대한 cmdlet을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-127">This display can help you find the cmdlets for a task.</span></span>

```powershell
Get-Command -Type Cmdlet | Sort-Object -Property Noun | Format-Table -GroupBy Noun
```

### <span data-ttu-id="1f095-128">예제 4: 모듈의 명령 가져오기</span><span class="sxs-lookup"><span data-stu-id="1f095-128">Example 4: Get commands in a module</span></span>

<span data-ttu-id="1f095-129">이 명령은 **Module** 매개 변수를 사용 하 여 microsoft Powershell. Security 및 Microsoft. powershell 모듈에서 명령을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-129">This command uses the **Module** parameter to get the commands in the Microsoft.PowerShell.Security and Microsoft.PowerShell.Utility modules.</span></span>

```powershell
Get-Command -Module Microsoft.PowerShell.Security, Microsoft.PowerShell.Utility
```

### <span data-ttu-id="1f095-130">예 5: cmdlet에 대 한 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="1f095-130">Example 5: Get information about a cmdlet</span></span>

<span data-ttu-id="1f095-131">이 명령은 cmdlet에 대 한 정보를 가져옵니다 `Get-AppLockerPolicy` .</span><span class="sxs-lookup"><span data-stu-id="1f095-131">This command gets information about the `Get-AppLockerPolicy` cmdlet.</span></span> <span data-ttu-id="1f095-132">또한 **AppLocker** 모듈의 모든 명령을 현재 세션에 추가하는 **AppLocker** 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-132">It also imports the **AppLocker** module, which adds all of the commands in the **AppLocker** module to the current session.</span></span>

```powershell
Get-Command Get-AppLockerPolicy
```

<span data-ttu-id="1f095-133">모듈을 자동으로 가져올 때 효과는 Import-Module cmdlet을 사용 하는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-133">When a module is imported automatically, the effect is the same as using the Import-Module cmdlet.</span></span>
<span data-ttu-id="1f095-134">모듈은 세션에서 명령, 유형 및 형식 지정 파일을 추가하고 스크립트를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-134">The module can add commands, types and formatting files, and run scripts in the session.</span></span> <span data-ttu-id="1f095-135">모듈 자동 가져오기를 사용 하거나 사용 하지 않도록 설정 하 고 구성 하려면 `$PSModuleAutoLoadingPreference` 기본 설정 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-135">To enable, disable, and configuration automatic importing of modules, use the `$PSModuleAutoLoadingPreference` preference variable.</span></span> <span data-ttu-id="1f095-136">자세한 내용은 [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1f095-136">For more information, see [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span></span>

### <span data-ttu-id="1f095-137">예제 6: cmdlet의 구문 가져오기</span><span class="sxs-lookup"><span data-stu-id="1f095-137">Example 6: Get the syntax of a cmdlet</span></span>

<span data-ttu-id="1f095-138">이 명령은 **Argumentlist** 및 **구문** 매개 변수를 사용 하 여 `Get-ChildItem` Cert: 드라이브에서 사용 되는 cmdlet의 구문을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-138">This command uses the **ArgumentList** and **Syntax** parameters to get the syntax of the `Get-ChildItem` cmdlet when it is used in the Cert: drive.</span></span> <span data-ttu-id="1f095-139">Cert: 드라이브는 인증서 공급자가 세션에 추가 하는 PowerShell 드라이브입니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-139">The Cert: drive is a PowerShell drive that the Certificate Provider adds to the session.</span></span>

```powershell
Get-Command  -Name Get-Childitem -Args Cert: -Syntax
```

<span data-ttu-id="1f095-140">출력에 표시 된 구문과 **Args** (**argumentlist**) 매개 변수를 생략할 때 표시 되는 구문을 비교 하면 **인증서 공급자** 가 동적 매개 변수 **codesigningcert** 를 cmdlet에 추가 하는 것을 알 수 있습니다 `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="1f095-140">When you compare the syntax displayed in the output with the syntax that is displayed when you omit the **Args** (**ArgumentList**) parameter, you'll see that the **Certificate provider** adds a dynamic parameter, **CodeSigningCert**, to the `Get-ChildItem` cmdlet.</span></span>

<span data-ttu-id="1f095-141">인증서 공급자에 대 한 자세한 내용은 [about_Certificate_Provider](../Microsoft.PowerShell.Security/About/about_Certificate_Provider.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1f095-141">For more information about the Certificate provider, see [about_Certificate_Provider](../Microsoft.PowerShell.Security/About/about_Certificate_Provider.md).</span></span>

### <span data-ttu-id="1f095-142">예 7: 동적 매개 변수 가져오기</span><span class="sxs-lookup"><span data-stu-id="1f095-142">Example 7: Get dynamic parameters</span></span>

<span data-ttu-id="1f095-143">이 예제의 명령은 함수를 사용 하 여 `Get-DynamicParameters` Certificate `Get-ChildItem` : 드라이브에서 사용 되는 경우 인증서 공급자가 cmdlet에 추가 하는 동적 매개 변수를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-143">The command in the example uses the `Get-DynamicParameters` function to get the dynamic parameters that the Certificate provider adds to the `Get-ChildItem` cmdlet when it is used in the Cert: drive.</span></span>

```powershell
function Get-DynamicParameters
{
    param ($Cmdlet, $PSDrive)
    (Get-Command -Name $Cmdlet -ArgumentList $PSDrive).ParameterSets | ForEach-Object {$_.Parameters} | Where-Object { $_.IsDynamic } | Select-Object -Property Name -Unique
}
Get-DynamicParameters -Cmdlet Get-ChildItem -PSDrive Cert:
```

```Output
Name
----
CodeSigningCert
```

<span data-ttu-id="1f095-144">`Get-DynamicParameters`이 예제의 함수는 cmdlet의 동적 매개 변수를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-144">The `Get-DynamicParameters` function in this example gets the dynamic parameters of a cmdlet.</span></span> <span data-ttu-id="1f095-145">이전 예의 방법 대신 이 방법을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-145">This is an alternative to the method used in the previous example.</span></span> <span data-ttu-id="1f095-146">다른 cmdlet 또는 공급자가 동적 매개 변수를 cmdlet에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-146">Dynamic parameter can be added to a cmdlet by another cmdlet or a provider.</span></span>

### <span data-ttu-id="1f095-147">예 8: 모든 형식의 모든 명령 가져오기</span><span class="sxs-lookup"><span data-stu-id="1f095-147">Example 8: Get all commands of all types</span></span>

<span data-ttu-id="1f095-148">이 명령은 **Path** 환경 변수 ()의 경로에 있는 실행 파일을 포함 하 여 로컬 컴퓨터에 있는 모든 형식의 명령을 모두 가져옵니다 `$env:path` .</span><span class="sxs-lookup"><span data-stu-id="1f095-148">This command gets all commands of all types on the local computer, including executable files in the paths of the **Path** environment variable (`$env:path`).</span></span>

```powershell
Get-Command *
```

<span data-ttu-id="1f095-149">각 파일에 대한 **FileInfo** 개체(System.IO.FileInfo)가 아니라 **ApplicationInfo** 개체(System.Management.Automation.ApplicationInfo)를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-149">It returns an **ApplicationInfo** object (System.Management.Automation.ApplicationInfo) for each file, not a **FileInfo** object (System.IO.FileInfo).</span></span>

### <span data-ttu-id="1f095-150">예제 9: 매개 변수 이름 및 유형을 사용 하 여 cmdlet 가져오기</span><span class="sxs-lookup"><span data-stu-id="1f095-150">Example 9: Get cmdlets by using a parameter name and type</span></span>

<span data-ttu-id="1f095-151">이 명령은 이름이 Auth를 포함 하 고 형식이 **Authenticationmechanism** 인 매개 변수가 있는 cmdlet을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-151">This command gets cmdlets that have a parameter whose name includes Auth and whose type is **AuthenticationMechanism**.</span></span>

```powershell
Get-Command -ParameterName *Auth* -ParameterType AuthenticationMechanism
```

<span data-ttu-id="1f095-152">이러한 명령을 사용하여 사용자 인증에 사용되는 메서드를 지정할 수 있는 cmdlet을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-152">You can use a command like this one to find cmdlets that let you specify the method that is used to authenticate the user.</span></span>

<span data-ttu-id="1f095-153">**ParameterType** 매개 변수는 이름이 유사한 경우에도 **AuthenticationMechanism** 값을 사용하는 매개 변수와 **AuthenticationLevel** 매개 변수를 사용하는 매개 변수를 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-153">The **ParameterType** parameter distinguishes parameters that take an **AuthenticationMechanism** value from those that take an **AuthenticationLevel** parameter, even when they have similar names.</span></span>

### <span data-ttu-id="1f095-154">예 10: 별칭 가져오기</span><span class="sxs-lookup"><span data-stu-id="1f095-154">Example 10: Get an alias</span></span>

<span data-ttu-id="1f095-155">이 예에서는 별칭과 함께 cmdlet을 사용 하는 방법을 보여 줍니다 `Get-Command` .</span><span class="sxs-lookup"><span data-stu-id="1f095-155">This example shows how to use the `Get-Command` cmdlet with an alias.</span></span>

```powershell
Get-Command Name dir
```

```Output
CommandType     Name                                               ModuleName
-----------     ----                                               ----------
Alias           dir -> Get-ChildItem
```

<span data-ttu-id="1f095-156">일반적으로 cmdlet 및 함수에 사용 되지만은 `Get-Command` 스크립트, 함수, 별칭 및 실행 파일도 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-156">Although it is typically used on cmdlets and functions, `Get-Command` also gets scripts, functions, aliases, and executable files.</span></span>

<span data-ttu-id="1f095-157">이 명령의 출력은 별칭에 대한 **Name** 속성 값의 특수 보기를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-157">The output of the command shows the special view of the **Name** property value for aliases.</span></span> <span data-ttu-id="1f095-158">보기에는 별칭과 전체 명령 이름이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-158">The view shows the alias and the full command name.</span></span>

### <span data-ttu-id="1f095-159">예 11: 별칭에서 구문 가져오기</span><span class="sxs-lookup"><span data-stu-id="1f095-159">Example 11: Get Syntax from an alias</span></span>

<span data-ttu-id="1f095-160">이 예제에서는 별칭의 표준 이름과 함께 구문을 가져오는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-160">This example shows how to get the syntax along with the standard name of an alias.</span></span>

<span data-ttu-id="1f095-161">명령의 출력에는 표준 이름과 구문을 차례로 표시 하는 레이블이 지정 된 별칭이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-161">The output of the command shows the labeled alias with the standard name, followed by the syntax.</span></span>

```powershell
Get-Command -Name dir -Syntax
```

```Output
dir (alias) -> Get-ChildItem

dir [[-Path] <string[]>] [[-Filter] <string>] [-Include <string[]>] [-Exclude <string[]>] [-Recurse] [-Depth <uint>] [-Force] [-Name] [-Attributes <FlagsExpression[FileAttributes]>] [-FollowSymlink] [-Directory] [-File] [-Hidden] [-ReadOnly] [-System] [<CommonParameters>]

dir [[-Filter] <string>] -LiteralPath <string[]> [-Include <string[]>] [-Exclude <string[]>] [-Recurse] [-Depth <uint>] [-Force] [-Name] [-Attributes <FlagsExpression[FileAttributes]>] [-FollowSymlink] [-Directory] [-File] [-Hidden] [-ReadOnly] [-System] [<CommonParameters>]
```

### <span data-ttu-id="1f095-162">예 12: 메모장 명령의 모든 인스턴스 가져오기</span><span class="sxs-lookup"><span data-stu-id="1f095-162">Example 12: Get all instances of the Notepad command</span></span>

<span data-ttu-id="1f095-163">이 예에서는 cmdlet의 **all** 매개 변수 `Get-Command` 를 사용 하 여 `Notepad` 로컬 컴퓨터에 있는 명령의 모든 인스턴스를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-163">This example uses the **All** parameter of the `Get-Command` cmdlet to show all instances of the `Notepad` command on the local computer.</span></span>

```powershell
Get-Command Notepad -All | Format-Table CommandType, Name, Definition
```

```Output
CommandType     Name           Definition
-----------     ----           ----------
Application     notepad.exe    C:\WINDOWS\system32\notepad.exe
Application     NOTEPAD.EXE    C:\WINDOWS\NOTEPAD.EXE
```

<span data-ttu-id="1f095-164">**All** 매개 변수는 세션에 동일한 이름을 가진 명령이 두 개 이상 있는 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-164">The **All** parameter is useful when there is more than one command with the same name in the session.</span></span>

<span data-ttu-id="1f095-165">Windows PowerShell 3.0부터 기본적으로 세션에 동일한 이름의 명령이 여러 개 포함 된 경우는 `Get-Command` 명령 이름을 입력할 때 실행 되는 명령만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-165">Beginning in Windows PowerShell 3.0, by default, when the session includes multiple commands with the same name, `Get-Command` gets only the command that runs when you type the command name.</span></span> <span data-ttu-id="1f095-166">**All** 매개 변수를 사용 하 여 `Get-Command` 지정 된 이름의 모든 명령을 가져오고 실행 우선 순위에 따라 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-166">With the **All** parameter, `Get-Command` gets all commands with the specified name and returns them in execution precedence order.</span></span> <span data-ttu-id="1f095-167">목록의 첫 번째 명령이 아닌 명령을 실행하려면 명령의 정규화된 경로를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-167">To run a command other than the first one in the list, type the fully qualified path to the command.</span></span>

<span data-ttu-id="1f095-168">명령 우선 순위에 대 한 자세한 내용은 [about_Command_Precedence](About/about_Command_Precedence.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1f095-168">For more information about command precedence, see [about_Command_Precedence](About/about_Command_Precedence.md).</span></span>

### <span data-ttu-id="1f095-169">예제 13: cmdlet이 포함 된 모듈의 이름 가져오기</span><span class="sxs-lookup"><span data-stu-id="1f095-169">Example 13: Get the name of a module that contains a cmdlet</span></span>

<span data-ttu-id="1f095-170">이 명령은 cmdlet이 시작 된 모듈의 이름을 가져옵니다 `Get-Date` .</span><span class="sxs-lookup"><span data-stu-id="1f095-170">This command gets the name of the module in which the `Get-Date` cmdlet originated.</span></span>
<span data-ttu-id="1f095-171">명령에서 모든 명령의 **ModuleName** 속성을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-171">The command uses the **ModuleName** property of all commands.</span></span>

```powershell
(Get-Command Get-Date).ModuleName
```

```Output
Microsoft.PowerShell.Utility
```

<span data-ttu-id="1f095-172">이 명령 형식은 세션으로 가져오지 않은 경우에도 PowerShell 모듈의 명령에 대해 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-172">This command format works on commands in PowerShell modules, even if they are not imported into the session.</span></span>

### <span data-ttu-id="1f095-173">예제 14: 출력 형식이 있는 cmdlet 및 함수 가져오기</span><span class="sxs-lookup"><span data-stu-id="1f095-173">Example 14: Get cmdlets and functions that have an output type</span></span>

```powershell
Get-Command -Type Cmdlet | Where-Object OutputType | Format-List -Property Name, OutputType
```

<span data-ttu-id="1f095-174">이 명령은 출력 유형이 있는 cmdlet 및 함수와 반환하는 개체 유형을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-174">This command gets the cmdlets and functions that have an output type and the type of objects that they return.</span></span>

<span data-ttu-id="1f095-175">명령의 첫 번째 부분에서 모든 cmdlet을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-175">The first part of the command gets all cmdlets.</span></span> <span data-ttu-id="1f095-176">파이프라인 연산자 ()는 cmdlet에 cmdlet을 보냅니다 .이 cmdlet은 `|` `Where-Object` **OutputType** 속성이 채워지는 항목만 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-176">A pipeline operator (`|`) sends the cmdlets to the `Where-Object` cmdlet, which selects only the ones in which the **OutputType** property is populated.</span></span> <span data-ttu-id="1f095-177">다른 파이프라인 연산자는 선택한 cmdlet 개체를 cmdlet으로 전송 합니다 `Format-List` . 그러면이 cmdlet에서 각 cmdlet의 이름과 출력 유형을 목록으로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-177">Another pipeline operator sends the selected cmdlet objects to the `Format-List` cmdlet, which displays the name and output type of each cmdlet in a list.</span></span>

<span data-ttu-id="1f095-178">cmdlet 코드에서 cmdlet의 **OutputType** 특성을 정의하는 경우에만 **CommandInfo** 개체의 **OutputType** 속성에 null이 아닌 값이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-178">The **OutputType** property of a **CommandInfo** object has a non-null value only when the cmdlet code defines the **OutputType** attribute for the cmdlet.</span></span>

### <span data-ttu-id="1f095-179">예 15: 특정 개체 유형을 입력으로 사용 하는 cmdlet 가져오기</span><span class="sxs-lookup"><span data-stu-id="1f095-179">Example 15: Get cmdlets that take a specific object type as input</span></span>

```powershell
Get-Command -ParameterType (((Get-NetAdapter)[0]).PSTypeNames)
```

```Output
CommandType     Name                                               ModuleName
-----------     ----                                               ----------
Function        Disable-NetAdapter                                 NetAdapter
Function        Enable-NetAdapter                                  NetAdapter
Function        Rename-NetAdapter                                  NetAdapter
Function        Restart-NetAdapter                                 NetAdapter
Function        Set-NetAdapter                                     NetAdapter
```

<span data-ttu-id="1f095-180">이 명령은 네트워크 어댑터 개체를 입력으로 사용하는 cmdlet을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-180">This command finds cmdlets that take net adapter objects as input.</span></span> <span data-ttu-id="1f095-181">이 명령을 사용하여 임의 명령이 반환하는 개체 유형을 허용하는 cmdlet을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-181">You can use this command format to find the cmdlets that accept the type of objects that any command returns.</span></span>

<span data-ttu-id="1f095-182">명령에서 모든 개체의 **PSTypeNames** 내부 속성을 사용합니다. 이 속성은 개체를 설명하는 유형을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-182">The command uses the **PSTypeNames** intrinsic property of all objects, which gets the types that describe the object.</span></span> <span data-ttu-id="1f095-183">네트워크 어댑터 컬렉션의 **PSTypeNames** 속성이 아니라 네트워크 어댑터의 **PSTypeNames** 속성을 가져오기 위해 명령에서 배열 표기법을 사용하여 cmdlet이 반환하는 첫 번째 네트워크 어댑터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-183">To get the **PSTypeNames** property of a net adapter, and not the **PSTypeNames** property of a collection of net adapters, the command uses array notation to get the first net adapter that the cmdlet returns.</span></span>

### <span data-ttu-id="1f095-184">예제 16: 유사 항목 일치를 사용 하 여 명령 가져오기</span><span class="sxs-lookup"><span data-stu-id="1f095-184">Example 16: Get commands using a fuzzy match</span></span>

<span data-ttu-id="1f095-185">이 예제에서 명령 이름에는 의도적으로 오타가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-185">In this example, the name of the command deliberately has a typo as 'get-commnd'.</span></span>
<span data-ttu-id="1f095-186">이 cmdlet은 스위치를 사용 하 여 가장 일치 하는 `-UseFuzzyMatching` 항목이 `Get-Command` 시스템의 다른 기본 명령 뒤에 나오는 것으로 확인 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-186">Using the `-UseFuzzyMatching` switch, the cmdlet determined that the best match was `Get-Command` followed by other native commands on the system that were a similar match.</span></span>

```powershell
Get-Command get-commnd -UseFuzzyMatching
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Cmdlet          Get-Command                                        6.2.0.0    Microsoft.PowerShell.Core
Application     getconf                                            0.0.0.0    /usr/bin/getconf
Application     command                                            0.0.0.0    /usr/bin/command
```

## <span data-ttu-id="1f095-187">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1f095-187">PARAMETERS</span></span>

### <span data-ttu-id="1f095-188">-All</span><span class="sxs-lookup"><span data-stu-id="1f095-188">-All</span></span>

<span data-ttu-id="1f095-189">이 cmdlet은 이름이 같은 동일한 형식의 명령을 포함 하 여 모든 명령을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-189">Indicates that this cmdlet gets all commands, including commands of the same type that have the same name.</span></span> <span data-ttu-id="1f095-190">기본적으로는 `Get-Command` 명령 이름을 입력할 때 실행 되는 명령만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-190">By default, `Get-Command` gets only the commands that run when you type the command name.</span></span>

<span data-ttu-id="1f095-191">PowerShell에서 여러 명령의 이름이 동일한 경우 실행할 명령을 선택 하는 데 사용 하는 방법에 대 한 자세한 내용은 [about_Command_Precedence](About/about_Command_Precedence.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1f095-191">For more information about the method that PowerShell uses to select the command to run when multiple commands have the same name, see [about_Command_Precedence](About/about_Command_Precedence.md).</span></span>
<span data-ttu-id="1f095-192">이름 충돌로 인해 기본적으로 실행 되지 않는 모듈의 정규화 된 명령 이름 및 실행 명령에 대 한 자세한 내용은 [about_Modules](About/about_Modules.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1f095-192">For information about module-qualified command names and running commands that do not run by default because of a name conflict, see [about_Modules](About/about_Modules.md).</span></span>

<span data-ttu-id="1f095-193">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-193">This parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="1f095-194">Windows PowerShell 2.0에서는 `Get-Command` 기본적으로 모든 명령을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-194">In Windows PowerShell 2.0, `Get-Command` gets all commands by default.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="1f095-195">-ArgumentList</span><span class="sxs-lookup"><span data-stu-id="1f095-195">-ArgumentList</span></span>

<span data-ttu-id="1f095-196">인수의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-196">Specifies an array of arguments.</span></span> <span data-ttu-id="1f095-197">이 cmdlet은 지정 된 매개 변수 ("인수")와 함께 사용할 경우 cmdlet 또는 함수에 대 한 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-197">This cmdlet gets information about a cmdlet or function when it is used with the specified parameters ("arguments").</span></span> <span data-ttu-id="1f095-198">**ArgumentList** 의 별칭은 **Args** 입니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-198">The alias for **ArgumentList** is **Args**.</span></span>

<span data-ttu-id="1f095-199">다른 특정 매개 변수가 사용 되는 경우에만 사용할 수 있는 동적 매개 변수를 검색 하려면 **Argumentlist** 값을 동적 매개 변수를 트리거하는 매개 변수로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-199">To detect dynamic parameters that are available only when certain other parameters are used, set the value of **ArgumentList** to the parameters that trigger the dynamic parameters.</span></span>

<span data-ttu-id="1f095-200">공급자가 cmdlet에 추가 하는 동적 매개 변수를 검색 하려면 **Argumentlist** 매개 변수의 값을 공급자 드라이브의 경로 (예: WSMan:, HKLM: 또는 Cert:)로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-200">To detect the dynamic parameters that a provider adds to a cmdlet, set the value of the **ArgumentList** parameter to a path in the provider drive, such as WSMan:, HKLM:, or Cert:.</span></span> <span data-ttu-id="1f095-201">명령이 PowerShell 공급자 cmdlet 인 경우 각 명령에 하나의 경로만 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-201">When the command is a PowerShell provider cmdlet, enter only one path in each command.</span></span> <span data-ttu-id="1f095-202">공급자 cmdlet은 **Argumentlist** 값의 첫 번째 경로에 대 한 동적 매개 변수만 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-202">The provider cmdlets return only the dynamic parameters for the first path the value of **ArgumentList**.</span></span> <span data-ttu-id="1f095-203">공급자 cmdlet에 대 한 자세한 내용은 [about_Providers](About/about_Providers.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1f095-203">For information about the provider cmdlets, see [about_Providers](About/about_Providers.md).</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases: Args

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1f095-204">-CommandType</span><span class="sxs-lookup"><span data-stu-id="1f095-204">-CommandType</span></span>

<span data-ttu-id="1f095-205">이 cmdlet이 가져오는 명령의 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-205">Specifies the types of commands that this cmdlet gets.</span></span> <span data-ttu-id="1f095-206">명령 유형을 하나 이상 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-206">Enter one or more command types.</span></span> <span data-ttu-id="1f095-207">**CommandType** 또는 별칭 **Type** 을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-207">Use **CommandType** or its alias, **Type**.</span></span> <span data-ttu-id="1f095-208">기본적으로 `Get-Command` 모든 cmdlet, 함수 및 별칭을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-208">By default, `Get-Command` gets all cmdlets, functions, and aliases.</span></span>

<span data-ttu-id="1f095-209">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-209">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="1f095-210">앤티앨리어스.</span><span class="sxs-lookup"><span data-stu-id="1f095-210">Alias.</span></span> <span data-ttu-id="1f095-211">모든 PowerShell 명령의 별칭을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-211">Gets the aliases of all PowerShell commands.</span></span> <span data-ttu-id="1f095-212">자세한 내용은 [about_Aliases](About/about_Aliases.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1f095-212">For more information, see [about_Aliases](About/about_Aliases.md).</span></span>
- <span data-ttu-id="1f095-213">모두.</span><span class="sxs-lookup"><span data-stu-id="1f095-213">All.</span></span> <span data-ttu-id="1f095-214">모든 명령 유형을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-214">Gets all command types.</span></span> <span data-ttu-id="1f095-215">이 매개 변수 값은에 해당 합니다 `Get-Command *` .</span><span class="sxs-lookup"><span data-stu-id="1f095-215">This parameter value is the equivalent of `Get-Command *`.</span></span>
- <span data-ttu-id="1f095-216">애플리케이션을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-216">Application.</span></span> <span data-ttu-id="1f095-217">.Txt, .exe 및 .dll 파일을 비롯 하 여 **Path** 환경 변수 ($env:p a)에 나열 된 경로에서 PowerShell이 아닌 파일을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-217">Gets non-PowerShell files in paths listed in the **Path** environment variable ($env:path), including .txt, .exe, and .dll files.</span></span> <span data-ttu-id="1f095-218">**Path** 환경 변수에 대 한 자세한 내용은 about_Environment_Variables를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1f095-218">For more information about the **Path** environment variable, see about_Environment_Variables.</span></span>
- <span data-ttu-id="1f095-219">#A0.</span><span class="sxs-lookup"><span data-stu-id="1f095-219">Cmdlet.</span></span> <span data-ttu-id="1f095-220">모든 cmdlet을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-220">Gets all cmdlets.</span></span>
- <span data-ttu-id="1f095-221">ExternalScript.</span><span class="sxs-lookup"><span data-stu-id="1f095-221">ExternalScript.</span></span> <span data-ttu-id="1f095-222">**Path** 환경 변수($env:path)에 나열된 경로에 있는 모든 .ps1 파일을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-222">Gets all .ps1 files in the paths listed in the **Path** environment variable ($env:path).</span></span>
- <span data-ttu-id="1f095-223">필터 및 함수</span><span class="sxs-lookup"><span data-stu-id="1f095-223">Filter and Function.</span></span> <span data-ttu-id="1f095-224">모든 PowerShell 고급 및 단순 함수와 필터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-224">Gets all PowerShell advanced and simple functions and filters.</span></span>
- <span data-ttu-id="1f095-225">스크립트.</span><span class="sxs-lookup"><span data-stu-id="1f095-225">Script.</span></span> <span data-ttu-id="1f095-226">모든 스크립트 블록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-226">Gets all script blocks.</span></span> <span data-ttu-id="1f095-227">PowerShell 스크립트 (ps1 파일)를 가져오려면 ExternalScript 값을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-227">To get PowerShell scripts (.ps1 files), use the ExternalScript value.</span></span>

```yaml
Type: System.Management.Automation.CommandTypes
Parameter Sets: AllCommandSet
Aliases: Type
Accepted values: Alias, Function, Filter, Cmdlet, ExternalScript, Application, Script, Workflow, Configuration, All

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="1f095-228">-변수인 fullyqualifiedmodule</span><span class="sxs-lookup"><span data-stu-id="1f095-228">-FullyQualifiedModule</span></span>

<span data-ttu-id="1f095-229">[ModuleSpecification 생성자 (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_)의 **설명** 섹션에서 설명 하는 **ModuleSpecification** 개체 형식으로 지정 된 이름을 사용 하 여 모듈을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-229">Specifies modules with names that are specified in the form of **ModuleSpecification** objects, described in the **Remarks** section of [ModuleSpecification Constructor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span></span>
<span data-ttu-id="1f095-230">예를 들어 **변수인 fullyqualifiedmodule** 매개 변수는 다음 형식 중 하나로 지정 된 모듈 이름을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-230">For example, the **FullyQualifiedModule** parameter accepts a module name that is specified in one of the following formats:</span></span>

- `@{ModuleName = "modulename"; ModuleVersion = "version_number"}`
- `@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}`

<span data-ttu-id="1f095-231">**ModuleName** 및 **ModuleVersion** 은 필수이지만 **Guid** 는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-231">**ModuleName** and **ModuleVersion** are required, but **Guid** is optional.</span></span>

<span data-ttu-id="1f095-232">**모듈** 매개 변수와 동일한 명령에 **변수인 fullyqualifiedmodule** 매개 변수를 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-232">You cannot specify the **FullyQualifiedModule** parameter in the same command as a **Module** parameter.</span></span> <span data-ttu-id="1f095-233">두 매개 변수는 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-233">The two parameters are mutually exclusive.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="1f095-234">-ListImported</span><span class="sxs-lookup"><span data-stu-id="1f095-234">-ListImported</span></span>

<span data-ttu-id="1f095-235">이 cmdlet은 현재 세션의 명령만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-235">Indicates that this cmdlet gets only commands in the current session.</span></span>

<span data-ttu-id="1f095-236">PowerShell 3.0부터 시작 하 여 기본적으로 `Get-Command` 현재 세션의 명령을 포함 하 여 모든 설치 된 명령을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-236">Starting in PowerShell 3.0, by default, `Get-Command` gets all installed commands, including, but not limited to, the commands in the current session.</span></span> <span data-ttu-id="1f095-237">PowerShell 2.0에서는 현재 세션의 명령만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-237">In PowerShell 2.0, it gets only commands in the current session.</span></span>

<span data-ttu-id="1f095-238">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-238">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="1f095-239">-모듈</span><span class="sxs-lookup"><span data-stu-id="1f095-239">-Module</span></span>

<span data-ttu-id="1f095-240">모듈의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-240">Specifies an array of modules.</span></span> <span data-ttu-id="1f095-241">이 cmdlet은 지정 된 모듈에서 가져온 명령을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-241">This cmdlet gets the commands that came from the specified modules.</span></span>
<span data-ttu-id="1f095-242">모듈 또는 모듈 개체의 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-242">Enter the names of modules or module objects.</span></span>

<span data-ttu-id="1f095-243">이 매개 변수는 문자열 값을 사용 하지만이 매개 변수의 값은 및 cmdlet이 반환 하는 개체와 같은 **Psmoduleinfo** 개체 일 수도 있습니다 `Get-Module` `Import-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="1f095-243">This parameter takes string values, but the value of this parameter can also be a **PSModuleInfo** object, such as the objects that the `Get-Module` and `Import-PSSession` cmdlets return.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSSnapin

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="1f095-244">-Name</span><span class="sxs-lookup"><span data-stu-id="1f095-244">-Name</span></span>

<span data-ttu-id="1f095-245">이름 배열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-245">Specifies an array of names.</span></span> <span data-ttu-id="1f095-246">이 cmdlet은 지정 된 이름의 명령만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-246">This cmdlet gets only commands that have the specified name.</span></span> <span data-ttu-id="1f095-247">이름 또는 이름 패턴을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-247">Enter a name or name pattern.</span></span> <span data-ttu-id="1f095-248">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-248">Wildcard characters are permitted.</span></span>

<span data-ttu-id="1f095-249">동일한 이름을 가진 명령을 가져오려면 **All** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-249">To get commands that have the same name, use the **All** parameter.</span></span> <span data-ttu-id="1f095-250">두 명령의 이름이 같은 경우 기본적으로 `Get-Command` 명령 이름을 입력할 때 실행 되는 명령을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-250">When two commands have the same name, by default, `Get-Command` gets the command that runs when you type the command name.</span></span>

```yaml
Type: System.String[]
Parameter Sets: AllCommandSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="1f095-251">-명사</span><span class="sxs-lookup"><span data-stu-id="1f095-251">-Noun</span></span>

<span data-ttu-id="1f095-252">명령 명사 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-252">Specifies an array of command nouns.</span></span> <span data-ttu-id="1f095-253">이 cmdlet은 지정 된 명사를 포함 하는 이름을 가진 cmdlet, 함수 및 별칭을 포함 하는 명령을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-253">This cmdlet gets commands, which include cmdlets, functions, and aliases, that have names that include the specified noun.</span></span> <span data-ttu-id="1f095-254">명사 또는 명사 패턴을 하나 이상 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-254">Enter one or more nouns or noun patterns.</span></span> <span data-ttu-id="1f095-255">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-255">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: CmdletSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="1f095-256">-ParameterName</span><span class="sxs-lookup"><span data-stu-id="1f095-256">-ParameterName</span></span>

<span data-ttu-id="1f095-257">매개 변수 이름 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-257">Specifies an array of parameter names.</span></span> <span data-ttu-id="1f095-258">이 cmdlet은 세션에서 지정 된 매개 변수가 있는 명령을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-258">This cmdlet gets commands in the session that have the specified parameters.</span></span> <span data-ttu-id="1f095-259">매개 변수 이름 또는 매개 변수 별칭을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-259">Enter parameter names or parameter aliases.</span></span> <span data-ttu-id="1f095-260">와일드카드 문자가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-260">Wildcard characters are supported.</span></span>

<span data-ttu-id="1f095-261">**ParameterName** 및 **ParameterType** 매개 변수는 현재 세션의 명령만 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-261">The **ParameterName** and **ParameterType** parameters search only commands in the current session.</span></span>

<span data-ttu-id="1f095-262">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-262">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="1f095-263">-ParameterType</span><span class="sxs-lookup"><span data-stu-id="1f095-263">-ParameterType</span></span>

<span data-ttu-id="1f095-264">매개 변수 이름 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-264">Specifies an array of parameter names.</span></span> <span data-ttu-id="1f095-265">이 cmdlet은 세션에서 지정 된 유형의 매개 변수가 있는 명령을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-265">This cmdlet gets commands in the session that have parameters of the specified type.</span></span> <span data-ttu-id="1f095-266">매개 변수 유형의 전체 이름이나 부분 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-266">Enter the full name or partial name of a parameter type.</span></span> <span data-ttu-id="1f095-267">와일드카드 문자가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-267">Wildcard characters are supported.</span></span>

<span data-ttu-id="1f095-268">**ParameterName** 및 **ParameterType** 매개 변수는 현재 세션의 명령만 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-268">The **ParameterName** and **ParameterType** parameters search only commands in the current session.</span></span>

<span data-ttu-id="1f095-269">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-269">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.PSTypeName[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="1f095-270">-ShowCommandInfo</span><span class="sxs-lookup"><span data-stu-id="1f095-270">-ShowCommandInfo</span></span>

<span data-ttu-id="1f095-271">이 cmdlet이 명령 정보를 표시 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-271">Indicates that this cmdlet displays command information.</span></span>

<span data-ttu-id="1f095-272">이 매개 변수는 Windows PowerShell 5.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-272">This parameter was introduced in Windows PowerShell 5.0.</span></span>

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

### <span data-ttu-id="1f095-273">-구문</span><span class="sxs-lookup"><span data-stu-id="1f095-273">-Syntax</span></span>

<span data-ttu-id="1f095-274">이 cmdlet은 명령에 대해 다음과 같은 지정 된 데이터만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-274">Indicates that this cmdlet gets only the following specified data about the command:</span></span>

- <span data-ttu-id="1f095-275">별칭.</span><span class="sxs-lookup"><span data-stu-id="1f095-275">Aliases.</span></span> <span data-ttu-id="1f095-276">표준 이름과 구문을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-276">Gets the standard name and syntax.</span></span>
- <span data-ttu-id="1f095-277">Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1f095-277">Cmdlets.</span></span> <span data-ttu-id="1f095-278">구문을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-278">Gets the syntax.</span></span>
- <span data-ttu-id="1f095-279">함수 및 필터.</span><span class="sxs-lookup"><span data-stu-id="1f095-279">Functions and filters.</span></span> <span data-ttu-id="1f095-280">함수 정의를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-280">Gets the function definition.</span></span>
- <span data-ttu-id="1f095-281">스크립트 및 응용 프로그램 또는 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-281">Scripts and applications or files.</span></span> <span data-ttu-id="1f095-282">경로와 파일 이름을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-282">Gets the path and filename.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="1f095-283">-TotalCount</span><span class="sxs-lookup"><span data-stu-id="1f095-283">-TotalCount</span></span>

<span data-ttu-id="1f095-284">가져올 명령 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-284">Specifies the number of commands to get.</span></span> <span data-ttu-id="1f095-285">이 매개 변수를 사용하여 명령의 출력을 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-285">You can use this parameter to limit the output of a command.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="1f095-286">-UseAbbreviationExpansion</span><span class="sxs-lookup"><span data-stu-id="1f095-286">-UseAbbreviationExpansion</span></span>

<span data-ttu-id="1f095-287">명령에서 문자 일치를 사용 하 여 명령에서 대문자를 찾는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-287">Indicates using matching of the characters in the command to find with uppercase characters in a command.</span></span> <span data-ttu-id="1f095-288">예를 들어는 `i-psdf` `Import-PowerShellDataFile` 찾으려는 각 문자가 결과에서 대문자와 일치 하는 것과 일치 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-288">For example, `i-psdf` would match `Import-PowerShellDataFile` as each of the characters to find matches an uppercase character in the result.</span></span> <span data-ttu-id="1f095-289">이 유형의 일치를 사용 하는 경우 와일드 카드를 사용 하면 일치 항목이 발생 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-289">When using this type of match, any wildcards will result in no matches.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AllCommandSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="1f095-290">-UseFuzzyMatching</span><span class="sxs-lookup"><span data-stu-id="1f095-290">-UseFuzzyMatching</span></span>

<span data-ttu-id="1f095-291">명령을 찾을 때 유사 일치 알고리즘을 사용 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-291">Indicates using a fuzzy matching algorithm when finding commands.</span></span> <span data-ttu-id="1f095-292">가장 일치 하는 항목에서 가장 일치 하는 항목으로 출력 순서가 가장 큽니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-292">The order of the output is from closest match to least likely match.</span></span> <span data-ttu-id="1f095-293">와일드 카드 문자를 포함할 수 있는 명령을 일치 시 키 려 고 하므로 유사 항목 일치에 와일드 카드를 사용 하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-293">Wildcards should not be used with fuzzy matching as it will attempt to match commands that may contain those wildcard characters.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AllCommandSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1f095-294">-동사</span><span class="sxs-lookup"><span data-stu-id="1f095-294">-Verb</span></span>

<span data-ttu-id="1f095-295">명령 동사의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-295">Specifies an array of command verbs.</span></span> <span data-ttu-id="1f095-296">이 cmdlet은 지정 된 동사가 포함 된 이름을 가진 cmdlet, 함수 및 별칭을 포함 하는 명령을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-296">This cmdlet gets commands, which include cmdlets, functions, and aliases, that have names that include the specified verb.</span></span> <span data-ttu-id="1f095-297">동사 또는 동사 패턴을 하나 이상 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-297">Enter one or more verbs or verb patterns.</span></span> <span data-ttu-id="1f095-298">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-298">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: CmdletSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="1f095-299">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1f095-299">CommonParameters</span></span>

<span data-ttu-id="1f095-300">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1f095-300">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1f095-301">자세한 내용은 [about_CommonParameters](About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1f095-301">For more information, see [about_CommonParameters](About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="1f095-302">입력</span><span class="sxs-lookup"><span data-stu-id="1f095-302">INPUTS</span></span>

### <span data-ttu-id="1f095-303">System.String</span><span class="sxs-lookup"><span data-stu-id="1f095-303">System.String</span></span>

<span data-ttu-id="1f095-304">이 cmdlet에 명령 이름을 파이프 하 여 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-304">You can pipe command names to this cmdlet.</span></span>

## <span data-ttu-id="1f095-305">출력</span><span class="sxs-lookup"><span data-stu-id="1f095-305">OUTPUTS</span></span>

### <span data-ttu-id="1f095-306">System.web. CommandInfo</span><span class="sxs-lookup"><span data-stu-id="1f095-306">System.Management.Automation.CommandInfo</span></span>

<span data-ttu-id="1f095-307">이 cmdlet은 **Commandinfo** 클래스에서 파생 된 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-307">This cmdlet returns objects derived from the **CommandInfo** class.</span></span> <span data-ttu-id="1f095-308">반환 되는 개체의 유형은 가져오는 명령의 유형에 따라 달라 집니다 `Get-Command` .</span><span class="sxs-lookup"><span data-stu-id="1f095-308">The type of object that is returned depends on the type of command that `Get-Command` gets.</span></span>

### <span data-ttu-id="1f095-309">System.management.automation.aliasinfo.</span><span class="sxs-lookup"><span data-stu-id="1f095-309">System.Management.Automation.AliasInfo</span></span>

<span data-ttu-id="1f095-310">별칭을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-310">Represents aliases.</span></span>

### <span data-ttu-id="1f095-311">System.object 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-311">System.Management.Automation.ApplicationInfo</span></span>

<span data-ttu-id="1f095-312">응용 프로그램 및 파일을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-312">Represents applications and files.</span></span>

### <span data-ttu-id="1f095-313">System.object..</span><span class="sxs-lookup"><span data-stu-id="1f095-313">System.Management.Automation.CmdletInfo</span></span>

<span data-ttu-id="1f095-314">cmdlet을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-314">Represents cmdlets.</span></span>

### <span data-ttu-id="1f095-315">System.object를 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-315">System.Management.Automation.FunctionInfo</span></span>

<span data-ttu-id="1f095-316">함수와 필터를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-316">Represents functions and filters.</span></span>

## <span data-ttu-id="1f095-317">참고</span><span class="sxs-lookup"><span data-stu-id="1f095-317">NOTES</span></span>

* <span data-ttu-id="1f095-318">세션에서 이름이 같은 명령을 둘 이상 사용할 수 있는 경우 `Get-Command` 명령 이름을 입력할 때 실행 되는 명령을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-318">When more than one command that has the same name is available to the session, `Get-Command` returns the command that runs when you type the command name.</span></span> <span data-ttu-id="1f095-319">실행 순서에 나열 된 것과 동일한 이름을 가진 명령을 가져오려면 **All** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-319">To get commands that have the same name, listed in run order, use the **All** parameter.</span></span> <span data-ttu-id="1f095-320">자세한 내용은 [about_Command_Precedence](../Microsoft.PowerShell.Core/About/about_Command_Precedence.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1f095-320">For more information, see [about_Command_Precedence](../Microsoft.PowerShell.Core/About/about_Command_Precedence.md).</span></span>
* <span data-ttu-id="1f095-321">모듈을 자동으로 가져올 때 효과는 cmdlet을 사용 하는 것과 같습니다 `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="1f095-321">When a module is imported automatically, the effect is the same as using the `Import-Module` cmdlet.</span></span> <span data-ttu-id="1f095-322">모듈은 세션에서 명령, 유형 및 형식 지정 파일을 추가하고 스크립트를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-322">The module can add commands, types and formatting files, and run scripts in the session.</span></span>
  <span data-ttu-id="1f095-323">모듈 자동 가져오기를 사용 하거나 사용 하지 않도록 설정 하 고 구성 하려면 `$PSModuleAutoLoadingPreference` 기본 설정 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f095-323">To enable, disable, and configuration automatic importing of modules, use the `$PSModuleAutoLoadingPreference` preference variable.</span></span> <span data-ttu-id="1f095-324">자세한 내용은 [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1f095-324">For more information, see [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span></span>

## <span data-ttu-id="1f095-325">관련 링크</span><span class="sxs-lookup"><span data-stu-id="1f095-325">RELATED LINKS</span></span>

[<span data-ttu-id="1f095-326">Export-PSSession</span><span class="sxs-lookup"><span data-stu-id="1f095-326">Export-PSSession</span></span>](../Microsoft.PowerShell.Utility/Export-PSSession.md)

[<span data-ttu-id="1f095-327">Get-Help</span><span class="sxs-lookup"><span data-stu-id="1f095-327">Get-Help</span></span>](Get-Help.md)

[<span data-ttu-id="1f095-328">Get-Member</span><span class="sxs-lookup"><span data-stu-id="1f095-328">Get-Member</span></span>](../Microsoft.PowerShell.Utility/Get-Member.md)

[<span data-ttu-id="1f095-329">Get-PSDrive</span><span class="sxs-lookup"><span data-stu-id="1f095-329">Get-PSDrive</span></span>](../Microsoft.PowerShell.Management/Get-PSDrive.md)

[<span data-ttu-id="1f095-330">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="1f095-330">Import-PSSession</span></span>](../Microsoft.PowerShell.Utility/Import-PSSession.md)

[<span data-ttu-id="1f095-331">about_Command_Precedence</span><span class="sxs-lookup"><span data-stu-id="1f095-331">about_Command_Precedence</span></span>](About/about_Command_Precedence.md)
