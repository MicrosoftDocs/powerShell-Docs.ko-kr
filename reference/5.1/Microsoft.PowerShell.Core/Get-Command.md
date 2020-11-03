---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-command?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Command
ms.openlocfilehash: daa58a732dafb11fa8f6ce3c20965aebcce55844
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93212057"
---
# <span data-ttu-id="38ad8-103">Get-Command</span><span class="sxs-lookup"><span data-stu-id="38ad8-103">Get-Command</span></span>

## <span data-ttu-id="38ad8-104">개요</span><span class="sxs-lookup"><span data-stu-id="38ad8-104">SYNOPSIS</span></span>
<span data-ttu-id="38ad8-105">모든 명령을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-105">Gets all commands.</span></span>

## <span data-ttu-id="38ad8-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="38ad8-106">SYNTAX</span></span>

### <span data-ttu-id="38ad8-107">CmdletSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="38ad8-107">CmdletSet (Default)</span></span>

```
Get-Command [-Verb <String[]>] [-Noun <String[]>] [-Module <String[]>] [-FullyQualifiedModule <ModuleSpecification[]>]
 [-TotalCount <Int32>] [-Syntax] [-ShowCommandInfo] [[-ArgumentList] <Object[]>] [-All] [-ListImported]
 [-ParameterName <String[]>] [-ParameterType <PSTypeName[]>] [<CommonParameters>]
```

### <span data-ttu-id="38ad8-108">AllCommandSet</span><span class="sxs-lookup"><span data-stu-id="38ad8-108">AllCommandSet</span></span>

```
Get-Command [[-Name] <String[]>] [-Module <String[]>] [-FullyQualifiedModule <ModuleSpecification[]>]
 [-CommandType <CommandTypes>] [-TotalCount <Int32>] [-Syntax] [-ShowCommandInfo] [[-ArgumentList] <Object[]>]
 [-All] [-ListImported] [-ParameterName <String[]>] [-ParameterType <PSTypeName[]>] [<CommonParameters>]
```

## <span data-ttu-id="38ad8-109">설명</span><span class="sxs-lookup"><span data-stu-id="38ad8-109">DESCRIPTION</span></span>

<span data-ttu-id="38ad8-110">`Get-Command`Cmdlet은 cmdlet, 별칭, 함수, 필터, 스크립트 및 응용 프로그램을 포함 하 여 컴퓨터에 설치 된 모든 명령을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-110">The `Get-Command` cmdlet gets all commands that are installed on the computer, including cmdlets, aliases, functions, filters, scripts, and applications.</span></span> <span data-ttu-id="38ad8-111">`Get-Command` 다른 세션에서 가져온 명령 및 PowerShell 모듈에서 명령을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-111">`Get-Command` gets the commands from PowerShell modules and commands that were imported from other sessions.</span></span> <span data-ttu-id="38ad8-112">현재 세션으로 가져온 명령만 가져오려면 **ListImported** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-112">To get only commands that have been imported into the current session, use the **ListImported** parameter.</span></span>

<span data-ttu-id="38ad8-113">매개 변수가 없으면 `Get-Command` 컴퓨터에 설치 된 모든 cmdlet, 함수 및 별칭을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-113">Without parameters, `Get-Command` gets all of the cmdlets, functions, and aliases installed on the computer.</span></span> <span data-ttu-id="38ad8-114">`Get-Command *``$env:Path`응용 프로그램 명령 유형에 나열 되는 Path 환경 변수 ()에 있는 모든 비 PowerShell 파일을 포함 하는 모든 명령 유형을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-114">`Get-Command *` gets all types of commands, including all of the non-PowerShell files in the Path environment variable (`$env:Path`), which it lists in the Application command type.</span></span>

<span data-ttu-id="38ad8-115">`Get-Command` 와일드 카드 문자 없이 명령의 정확한 이름을 사용 하면 명령을 즉시 사용할 수 있도록 명령이 포함 된 모듈을 자동으로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-115">`Get-Command` that uses the exact name of the command, without wildcard characters, automatically imports the module that contains the command so that you can use the command immediately.</span></span> <span data-ttu-id="38ad8-116">모듈 자동 가져오기를 사용 하거나 사용 하지 않도록 설정 하 고 구성 하려면 `$PSModuleAutoLoadingPreference` 기본 설정 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-116">To enable, disable, and configure automatic importing of modules, use the `$PSModuleAutoLoadingPreference` preference variable.</span></span> <span data-ttu-id="38ad8-117">자세한 내용은 [about_Preference_Variables](About/about_Preference_Variables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="38ad8-117">For more information, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="38ad8-118">`Get-Command` 도움말 항목에서 정보를 가져오는와는 달리 명령 코드에서 직접 데이터를 가져옵니다 `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="38ad8-118">`Get-Command` gets its data directly from the command code, unlike `Get-Help`, which gets its information from help topics.</span></span>

<span data-ttu-id="38ad8-119">Windows PowerShell 5.0부터 cmdlet의 결과에는 `Get-Command` 기본적으로 **버전** 열이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-119">Starting in Windows PowerShell 5.0, results of the `Get-Command` cmdlet display a **Version** column by default.</span></span> <span data-ttu-id="38ad8-120">새 **버전** 속성이 **commandinfo** 클래스에 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-120">A new **Version** property has been added to the **CommandInfo** class.</span></span>

## <span data-ttu-id="38ad8-121">예제</span><span class="sxs-lookup"><span data-stu-id="38ad8-121">EXAMPLES</span></span>

### <span data-ttu-id="38ad8-122">예제 1: cmdlet, 함수 및 별칭 가져오기</span><span class="sxs-lookup"><span data-stu-id="38ad8-122">Example 1: Get cmdlets, functions, and aliases</span></span>

<span data-ttu-id="38ad8-123">이 명령은 컴퓨터에 설치 된 PowerShell cmdlet, 함수 및 별칭을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-123">This command gets the PowerShell cmdlets, functions, and aliases that are installed on the computer.</span></span>

```powershell
Get-Command
```

### <span data-ttu-id="38ad8-124">예 2: 현재 세션의 명령 가져오기</span><span class="sxs-lookup"><span data-stu-id="38ad8-124">Example 2: Get commands in the current session</span></span>

<span data-ttu-id="38ad8-125">이 명령은 **ListImported** 매개 변수를 사용하여 현재 세션의 명령만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-125">This command uses the **ListImported** parameter to get only the commands in the current session.</span></span>

```powershell
Get-Command -ListImported
```

### <span data-ttu-id="38ad8-126">예제 3: cmdlet 가져오기 및 순서 대로 표시</span><span class="sxs-lookup"><span data-stu-id="38ad8-126">Example 3: Get cmdlets and display them in order</span></span>

<span data-ttu-id="38ad8-127">이 명령은 모든 cmdlet을 가져오고 cmdlet 이름에 포함된 명사의 사전순으로 정렬한 다음 명사 기반 그룹으로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-127">This command gets all of the cmdlets, sorts them alphabetically by the noun in the cmdlet name, and then displays them in noun-based groups.</span></span> <span data-ttu-id="38ad8-128">이 표시를 사용하여 특정 작업에 대한 cmdlet을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-128">This display can help you find the cmdlets for a task.</span></span>

```powershell
Get-Command -Type Cmdlet | Sort-Object -Property Noun | Format-Table -GroupBy Noun
```

### <span data-ttu-id="38ad8-129">예제 4: 모듈의 명령 가져오기</span><span class="sxs-lookup"><span data-stu-id="38ad8-129">Example 4: Get commands in a module</span></span>

<span data-ttu-id="38ad8-130">이 명령은 **Module** 매개 변수를 사용 하 여 microsoft Powershell. Security 및 Microsoft. powershell 모듈에서 명령을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-130">This command uses the **Module** parameter to get the commands in the Microsoft.PowerShell.Security and Microsoft.PowerShell.Utility modules.</span></span>

```powershell
Get-Command -Module Microsoft.PowerShell.Security, Microsoft.PowerShell.Utility
```

### <span data-ttu-id="38ad8-131">예 5: cmdlet에 대 한 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="38ad8-131">Example 5: Get information about a cmdlet</span></span>

<span data-ttu-id="38ad8-132">이 명령은 cmdlet에 대 한 정보를 가져옵니다 `Get-AppLockerPolicy` .</span><span class="sxs-lookup"><span data-stu-id="38ad8-132">This command gets information about the `Get-AppLockerPolicy` cmdlet.</span></span> <span data-ttu-id="38ad8-133">또한 **AppLocker** 모듈의 모든 명령을 현재 세션에 추가하는 **AppLocker** 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-133">It also imports the **AppLocker** module, which adds all of the commands in the **AppLocker** module to the current session.</span></span>

```powershell
Get-Command Get-AppLockerPolicy
```

<span data-ttu-id="38ad8-134">모듈을 자동으로 가져올 때 효과는 Import-Module cmdlet을 사용 하는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-134">When a module is imported automatically, the effect is the same as using the Import-Module cmdlet.</span></span>
<span data-ttu-id="38ad8-135">모듈은 세션에서 명령, 유형 및 형식 지정 파일을 추가하고 스크립트를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-135">The module can add commands, types and formatting files, and run scripts in the session.</span></span> <span data-ttu-id="38ad8-136">모듈 자동 가져오기를 사용 하거나 사용 하지 않도록 설정 하 고 구성 하려면 `$PSModuleAutoLoadingPreference` 기본 설정 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-136">To enable, disable, and configuration automatic importing of modules, use the `$PSModuleAutoLoadingPreference` preference variable.</span></span> <span data-ttu-id="38ad8-137">자세한 내용은 [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="38ad8-137">For more information, see [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span></span>

### <span data-ttu-id="38ad8-138">예제 6: cmdlet의 구문 가져오기</span><span class="sxs-lookup"><span data-stu-id="38ad8-138">Example 6: Get the syntax of a cmdlet</span></span>

<span data-ttu-id="38ad8-139">이 명령은 **Argumentlist** 및 **구문** 매개 변수를 사용 하 여 `Get-ChildItem` Cert: 드라이브에서 사용 되는 cmdlet의 구문을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-139">This command uses the **ArgumentList** and **Syntax** parameters to get the syntax of the `Get-ChildItem` cmdlet when it is used in the Cert: drive.</span></span> <span data-ttu-id="38ad8-140">Cert: 드라이브는 인증서 공급자가 세션에 추가 하는 PowerShell 드라이브입니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-140">The Cert: drive is a PowerShell drive that the Certificate Provider adds to the session.</span></span>

```powershell
Get-Command Get-Childitem -Args Cert: -Syntax
```

<span data-ttu-id="38ad8-141">출력에 표시 된 구문과 **Args** ( **argumentlist** ) 매개 변수를 생략할 때 표시 되는 구문을 비교 하면 **인증서 공급자** 가 동적 매개 변수 **codesigningcert** 를 cmdlet에 추가 하는 것을 알 수 있습니다 `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="38ad8-141">When you compare the syntax displayed in the output with the syntax that is displayed when you omit the **Args** ( **ArgumentList** ) parameter, you'll see that the **Certificate provider** adds a dynamic parameter, **CodeSigningCert** , to the `Get-ChildItem` cmdlet.</span></span>

<span data-ttu-id="38ad8-142">인증서 공급자에 대 한 자세한 내용은 [about_Certificate_Provider](../Microsoft.PowerShell.Security/About/about_Certificate_Provider.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="38ad8-142">For more information about the Certificate provider, see [about_Certificate_Provider](../Microsoft.PowerShell.Security/About/about_Certificate_Provider.md).</span></span>

### <span data-ttu-id="38ad8-143">예 7: 동적 매개 변수 가져오기</span><span class="sxs-lookup"><span data-stu-id="38ad8-143">Example 7: Get dynamic parameters</span></span>

<span data-ttu-id="38ad8-144">이 예제의 명령은 함수를 사용 하 여 `Get-DynamicParameters` Certificate `Get-ChildItem` : 드라이브에서 사용 되는 경우 인증서 공급자가 cmdlet에 추가 하는 동적 매개 변수를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-144">The command in the example uses the `Get-DynamicParameters` function to get the dynamic parameters that the Certificate provider adds to the `Get-ChildItem` cmdlet when it is used in the Cert: drive.</span></span>

```powershell
function Get-DynamicParameters
{
    param ($Cmdlet, $PSDrive)
    (Get-Command $Cmdlet -ArgumentList $PSDrive).ParameterSets | ForEach-Object {$_.Parameters} | Where-Object { $_.IsDynamic } | Select-Object -Property Name -Unique
}
Get-DynamicParameters -Cmdlet Get-ChildItem -PSDrive Cert:
```

```Output
Name
----
CodeSigningCert
```

<span data-ttu-id="38ad8-145">`Get-DynamicParameters`이 예제의 함수는 cmdlet의 동적 매개 변수를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-145">The `Get-DynamicParameters` function in this example gets the dynamic parameters of a cmdlet.</span></span> <span data-ttu-id="38ad8-146">이전 예의 방법 대신 이 방법을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-146">This is an alternative to the method used in the previous example.</span></span> <span data-ttu-id="38ad8-147">다른 cmdlet 또는 공급자가 동적 매개 변수를 cmdlet에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-147">Dynamic parameter can be added to a cmdlet by another cmdlet or a provider.</span></span>

### <span data-ttu-id="38ad8-148">예 8: 모든 형식의 모든 명령 가져오기</span><span class="sxs-lookup"><span data-stu-id="38ad8-148">Example 8: Get all commands of all types</span></span>

<span data-ttu-id="38ad8-149">이 명령은 **Path** 환경 변수 ()의 경로에 있는 실행 파일을 포함 하 여 로컬 컴퓨터에 있는 모든 형식의 명령을 모두 가져옵니다 `$env:path` .</span><span class="sxs-lookup"><span data-stu-id="38ad8-149">This command gets all commands of all types on the local computer, including executable files in the paths of the **Path** environment variable (`$env:path`).</span></span>

```powershell
Get-Command *
```

<span data-ttu-id="38ad8-150">각 파일에 대한 **FileInfo** 개체(System.IO.FileInfo)가 아니라 **ApplicationInfo** 개체(System.Management.Automation.ApplicationInfo)를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-150">It returns an **ApplicationInfo** object (System.Management.Automation.ApplicationInfo) for each file, not a **FileInfo** object (System.IO.FileInfo).</span></span>

### <span data-ttu-id="38ad8-151">예제 9: 매개 변수 이름 및 유형을 사용 하 여 cmdlet 가져오기</span><span class="sxs-lookup"><span data-stu-id="38ad8-151">Example 9: Get cmdlets by using a parameter name and type</span></span>

<span data-ttu-id="38ad8-152">이 명령은 이름이 Auth를 포함 하 고 형식이 **Authenticationmechanism** 인 매개 변수가 있는 cmdlet을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-152">This command gets cmdlets that have a parameter whose name includes Auth and whose type is **AuthenticationMechanism** .</span></span>

```powershell
Get-Command -ParameterName *Auth* -ParameterType AuthenticationMechanism
```

<span data-ttu-id="38ad8-153">이러한 명령을 사용하여 사용자 인증에 사용되는 메서드를 지정할 수 있는 cmdlet을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-153">You can use a command like this one to find cmdlets that let you specify the method that is used to authenticate the user.</span></span>

<span data-ttu-id="38ad8-154">**ParameterType** 매개 변수는 이름이 유사한 경우에도 **AuthenticationMechanism** 값을 사용하는 매개 변수와 **AuthenticationLevel** 매개 변수를 사용하는 매개 변수를 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-154">The **ParameterType** parameter distinguishes parameters that take an **AuthenticationMechanism** value from those that take an **AuthenticationLevel** parameter, even when they have similar names.</span></span>

### <span data-ttu-id="38ad8-155">예 10: 별칭 가져오기</span><span class="sxs-lookup"><span data-stu-id="38ad8-155">Example 10: Get an alias</span></span>

<span data-ttu-id="38ad8-156">이 예에서는 별칭과 함께 cmdlet을 사용 하는 방법을 보여 줍니다 `Get-Command` .</span><span class="sxs-lookup"><span data-stu-id="38ad8-156">This example shows how to use the `Get-Command` cmdlet with an alias.</span></span>

```powershell
Get-Command dir
```

```Output
CommandType     Name                                               ModuleName
-----------     ----                                               ----------
Alias           dir -> Get-ChildItem
```

<span data-ttu-id="38ad8-157">일반적으로 cmdlet 및 함수에 사용 되지만은 `Get-Command` 스크립트, 함수, 별칭 및 실행 파일도 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-157">Although it is typically used on cmdlets and functions, `Get-Command` also gets scripts, functions, aliases, and executable files.</span></span>

<span data-ttu-id="38ad8-158">이 명령의 출력은 별칭에 대한 **Name** 속성 값의 특수 보기를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-158">The output of the command shows the special view of the **Name** property value for aliases.</span></span> <span data-ttu-id="38ad8-159">보기에는 별칭과 전체 명령 이름이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-159">The view shows the alias and the full command name.</span></span>

### <span data-ttu-id="38ad8-160">예 11: 메모장 명령의 모든 인스턴스 가져오기</span><span class="sxs-lookup"><span data-stu-id="38ad8-160">Example 11: Get all instances of the Notepad command</span></span>

<span data-ttu-id="38ad8-161">이 예에서는 cmdlet의 **all** 매개 변수를 사용 하 여 `Get-Command` 로컬 컴퓨터에 있는 "Notepad" 명령의 모든 인스턴스를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-161">This example uses the **All** parameter of the `Get-Command` cmdlet to show all instances of the "Notepad" command on the local computer.</span></span>

```powershell
Get-Command Notepad -All | Format-Table CommandType, Name, Definition
```

```Output
CommandType     Name           Definition
-----------     ----           ----------
Application     notepad.exe    C:\WINDOWS\system32\notepad.exe
Application     NOTEPAD.EXE    C:\WINDOWS\NOTEPAD.EXE
```

<span data-ttu-id="38ad8-162">**All** 매개 변수는 세션에 동일한 이름을 가진 명령이 두 개 이상 있는 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-162">The **All** parameter is useful when there is more than one command with the same name in the session.</span></span>

<span data-ttu-id="38ad8-163">Windows PowerShell 3.0부터 기본적으로 세션에 동일한 이름의 명령이 여러 개 포함 된 경우는 `Get-Command` 명령 이름을 입력할 때 실행 되는 명령만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-163">Beginning in Windows PowerShell 3.0, by default, when the session includes multiple commands with the same name, `Get-Command` gets only the command that runs when you type the command name.</span></span> <span data-ttu-id="38ad8-164">**All** 매개 변수를 사용 하 여 `Get-Command` 지정 된 이름의 모든 명령을 가져오고 실행 우선 순위에 따라 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-164">With the **All** parameter, `Get-Command` gets all commands with the specified name and returns them in execution precedence order.</span></span> <span data-ttu-id="38ad8-165">목록의 첫 번째 명령이 아닌 명령을 실행하려면 명령의 정규화된 경로를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-165">To run a command other than the first one in the list, type the fully qualified path to the command.</span></span>

<span data-ttu-id="38ad8-166">명령 우선 순위에 대 한 자세한 내용은 [about_Command_Precedence](About/about_Command_Precedence.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="38ad8-166">For more information about command precedence, see [about_Command_Precedence](About/about_Command_Precedence.md).</span></span>

### <span data-ttu-id="38ad8-167">예 12: cmdlet이 포함 된 모듈의 이름 가져오기</span><span class="sxs-lookup"><span data-stu-id="38ad8-167">Example 12: Get the name of a module that contains a cmdlet</span></span>

<span data-ttu-id="38ad8-168">이 명령은 cmdlet이 시작 된 모듈의 이름을 가져옵니다 `Get-Date` .</span><span class="sxs-lookup"><span data-stu-id="38ad8-168">This command gets the name of the module in which the `Get-Date` cmdlet originated.</span></span>
<span data-ttu-id="38ad8-169">명령에서 모든 명령의 **ModuleName** 속성을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-169">The command uses the **ModuleName** property of all commands.</span></span>

```powershell
(Get-Command Get-Date).ModuleName
```

```Output
Microsoft.PowerShell.Utility
```

<span data-ttu-id="38ad8-170">이 명령 형식은 세션으로 가져오지 않은 경우에도 PowerShell 모듈의 명령에 대해 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-170">This command format works on commands in PowerShell modules, even if they are not imported into the session.</span></span>

### <span data-ttu-id="38ad8-171">예제 13: 출력 형식이 있는 cmdlet 및 함수 가져오기</span><span class="sxs-lookup"><span data-stu-id="38ad8-171">Example 13: Get cmdlets and functions that have an output type</span></span>

```powershell
Get-Command -Type Cmdlet | Where-Object OutputType | Format-List -Property Name, OutputType
```

<span data-ttu-id="38ad8-172">이 명령은 출력 유형이 있는 cmdlet 및 함수와 반환하는 개체 유형을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-172">This command gets the cmdlets and functions that have an output type and the type of objects that they return.</span></span>

<span data-ttu-id="38ad8-173">명령의 첫 번째 부분에서 모든 cmdlet을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-173">The first part of the command gets all cmdlets.</span></span>
<span data-ttu-id="38ad8-174">파이프라인 연산자 (|)가 cmdlet에 cmdlet을 보냅니다 .이 cmdlet은 `Where-Object` **OutputType** 속성이 채워지는 항목만 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-174">A pipeline operator (|) sends the cmdlets to the `Where-Object` cmdlet, which selects only the ones in which the **OutputType** property is populated.</span></span>
<span data-ttu-id="38ad8-175">다른 파이프라인 연산자는 선택한 cmdlet 개체를 cmdlet으로 전송 합니다 `Format-List` . 그러면이 cmdlet에서 각 cmdlet의 이름과 출력 유형을 목록으로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-175">Another pipeline operator sends the selected cmdlet objects to the `Format-List` cmdlet, which displays the name and output type of each cmdlet in a list.</span></span>

<span data-ttu-id="38ad8-176">cmdlet 코드에서 cmdlet의 **OutputType** 특성을 정의하는 경우에만 **CommandInfo** 개체의 **OutputType** 속성에 null이 아닌 값이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-176">The **OutputType** property of a **CommandInfo** object has a non-null value only when the cmdlet code defines the **OutputType** attribute for the cmdlet.</span></span>

### <span data-ttu-id="38ad8-177">예 14: 특정 개체 유형을 입력으로 사용 하는 cmdlet 가져오기</span><span class="sxs-lookup"><span data-stu-id="38ad8-177">Example 14: Get cmdlets that take a specific object type as input</span></span>

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

<span data-ttu-id="38ad8-178">이 명령은 네트워크 어댑터 개체를 입력으로 사용하는 cmdlet을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-178">This command finds cmdlets that take net adapter objects as input.</span></span> <span data-ttu-id="38ad8-179">이 명령을 사용하여 임의 명령이 반환하는 개체 유형을 허용하는 cmdlet을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-179">You can use this command format to find the cmdlets that accept the type of objects that any command returns.</span></span>

<span data-ttu-id="38ad8-180">명령에서 모든 개체의 **PSTypeNames** 내부 속성을 사용합니다. 이 속성은 개체를 설명하는 유형을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-180">The command uses the **PSTypeNames** intrinsic property of all objects, which gets the types that describe the object.</span></span> <span data-ttu-id="38ad8-181">네트워크 어댑터 컬렉션의 **PSTypeNames** 속성이 아니라 네트워크 어댑터의 **PSTypeNames** 속성을 가져오기 위해 명령에서 배열 표기법을 사용하여 cmdlet이 반환하는 첫 번째 네트워크 어댑터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-181">To get the **PSTypeNames** property of a net adapter, and not the **PSTypeNames** property of a collection of net adapters, the command uses array notation to get the first net adapter that the cmdlet returns.</span></span>
<span data-ttu-id="38ad8-182">네트워크 어댑터 컬렉션의 **PSTypeNames** 속성이 아니라 네트워크 어댑터의 **PSTypeNames** 속성을 가져오기 위해 명령에서 배열 표기법을 사용하여 cmdlet이 반환하는 첫 번째 네트워크 어댑터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-182">To get the **PSTypeNames** property of a net adapter, and not the **PSTypeNames** property of a collection of net adapters, the command uses array notation to get the first net adapter that the cmdlet returns.</span></span>

## <span data-ttu-id="38ad8-183">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="38ad8-183">PARAMETERS</span></span>

### <span data-ttu-id="38ad8-184">-All</span><span class="sxs-lookup"><span data-stu-id="38ad8-184">-All</span></span>

<span data-ttu-id="38ad8-185">이 cmdlet은 이름이 같은 동일한 형식의 명령을 포함 하 여 모든 명령을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-185">Indicates that this cmdlet gets all commands, including commands of the same type that have the same name.</span></span> <span data-ttu-id="38ad8-186">기본적으로는 `Get-Command` 명령 이름을 입력할 때 실행 되는 명령만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-186">By default, `Get-Command` gets only the commands that run when you type the command name.</span></span>

<span data-ttu-id="38ad8-187">PowerShell에서 여러 명령의 이름이 동일한 경우 실행할 명령을 선택 하는 데 사용 하는 방법에 대 한 자세한 내용은 [about_Command_Precedence](About/about_Command_Precedence.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="38ad8-187">For more information about the method that PowerShell uses to select the command to run when multiple commands have the same name, see [about_Command_Precedence](About/about_Command_Precedence.md).</span></span>
<span data-ttu-id="38ad8-188">이름 충돌로 인해 기본적으로 실행 되지 않는 모듈의 정규화 된 명령 이름 및 실행 명령에 대 한 자세한 내용은 [about_Modules](About/about_Modules.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="38ad8-188">For information about module-qualified command names and running commands that do not run by default because of a name conflict, see [about_Modules](About/about_Modules.md).</span></span>

<span data-ttu-id="38ad8-189">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-189">This parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="38ad8-190">Windows PowerShell 2.0에서는 `Get-Command` 기본적으로 모든 명령을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-190">In Windows PowerShell 2.0, `Get-Command` gets all commands by default.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="38ad8-191">-ArgumentList</span><span class="sxs-lookup"><span data-stu-id="38ad8-191">-ArgumentList</span></span>

<span data-ttu-id="38ad8-192">인수의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-192">Specifies an array of arguments.</span></span> <span data-ttu-id="38ad8-193">이 cmdlet은 지정 된 매개 변수 ("인수")와 함께 사용할 경우 cmdlet 또는 함수에 대 한 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-193">This cmdlet gets information about a cmdlet or function when it is used with the specified parameters ("arguments").</span></span> <span data-ttu-id="38ad8-194">**ArgumentList** 의 별칭은 **Args** 입니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-194">The alias for **ArgumentList** is **Args** .</span></span>

<span data-ttu-id="38ad8-195">다른 특정 매개 변수가 사용 되는 경우에만 사용할 수 있는 동적 매개 변수를 검색 하려면 **Argumentlist** 값을 동적 매개 변수를 트리거하는 매개 변수로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-195">To detect dynamic parameters that are available only when certain other parameters are used, set the value of **ArgumentList** to the parameters that trigger the dynamic parameters.</span></span>

<span data-ttu-id="38ad8-196">공급자가 cmdlet에 추가 하는 동적 매개 변수를 검색 하려면 **Argumentlist** 매개 변수의 값을 공급자 드라이브의 경로 (예: WSMan:, HKLM: 또는 Cert:)로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-196">To detect the dynamic parameters that a provider adds to a cmdlet, set the value of the **ArgumentList** parameter to a path in the provider drive, such as WSMan:, HKLM:, or Cert:.</span></span> <span data-ttu-id="38ad8-197">명령이 PowerShell 공급자 cmdlet 인 경우 각 명령에 하나의 경로만 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-197">When the command is a PowerShell provider cmdlet, enter only one path in each command.</span></span> <span data-ttu-id="38ad8-198">공급자 cmdlet은 **Argumentlist** 값의 첫 번째 경로에 대 한 동적 매개 변수만 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-198">The provider cmdlets return only the dynamic parameters for the first path the value of **ArgumentList** .</span></span> <span data-ttu-id="38ad8-199">공급자 cmdlet에 대 한 자세한 내용은 [about_Providers](About/about_Providers.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="38ad8-199">For information about the provider cmdlets, see [about_Providers](About/about_Providers.md).</span></span>

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

### <span data-ttu-id="38ad8-200">-CommandType</span><span class="sxs-lookup"><span data-stu-id="38ad8-200">-CommandType</span></span>

<span data-ttu-id="38ad8-201">이 cmdlet이 가져오는 명령의 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-201">Specifies the types of commands that this cmdlet gets.</span></span> <span data-ttu-id="38ad8-202">명령 유형을 하나 이상 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-202">Enter one or more command types.</span></span> <span data-ttu-id="38ad8-203">**CommandType** 또는 별칭 **Type** 을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-203">Use **CommandType** or its alias, **Type** .</span></span> <span data-ttu-id="38ad8-204">기본적으로 `Get-Command` 모든 cmdlet, 함수 및 별칭을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-204">By default, `Get-Command` gets all cmdlets, functions, and aliases.</span></span>

<span data-ttu-id="38ad8-205">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-205">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="38ad8-206">앤티앨리어스.</span><span class="sxs-lookup"><span data-stu-id="38ad8-206">Alias.</span></span> <span data-ttu-id="38ad8-207">모든 PowerShell 명령의 별칭을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-207">Gets the aliases of all PowerShell commands.</span></span> <span data-ttu-id="38ad8-208">자세한 내용은 [about_Aliases](About/about_Aliases.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="38ad8-208">For more information, see [about_Aliases](About/about_Aliases.md).</span></span>
- <span data-ttu-id="38ad8-209">모두.</span><span class="sxs-lookup"><span data-stu-id="38ad8-209">All.</span></span> <span data-ttu-id="38ad8-210">모든 명령 유형을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-210">Gets all command types.</span></span> <span data-ttu-id="38ad8-211">이 매개 변수 값은에 해당 합니다 `Get-Command *` .</span><span class="sxs-lookup"><span data-stu-id="38ad8-211">This parameter value is the equivalent of `Get-Command *`.</span></span>
- <span data-ttu-id="38ad8-212">애플리케이션을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-212">Application.</span></span> <span data-ttu-id="38ad8-213">.Txt, .exe 및 .dll 파일을 비롯 하 여 **Path** 환경 변수 ($env:p a)에 나열 된 경로에서 PowerShell이 아닌 파일을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-213">Gets non-PowerShell files in paths listed in the **Path** environment variable ($env:path), including .txt, .exe, and .dll files.</span></span> <span data-ttu-id="38ad8-214">**Path** 환경 변수에 대 한 자세한 내용은 about_Environment_Variables를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="38ad8-214">For more information about the **Path** environment variable, see about_Environment_Variables.</span></span>
- <span data-ttu-id="38ad8-215">#A0.</span><span class="sxs-lookup"><span data-stu-id="38ad8-215">Cmdlet.</span></span> <span data-ttu-id="38ad8-216">모든 cmdlet을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-216">Gets all cmdlets.</span></span>
- <span data-ttu-id="38ad8-217">ExternalScript.</span><span class="sxs-lookup"><span data-stu-id="38ad8-217">ExternalScript.</span></span> <span data-ttu-id="38ad8-218">**Path** 환경 변수($env:path)에 나열된 경로에 있는 모든 .ps1 파일을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-218">Gets all .ps1 files in the paths listed in the **Path** environment variable ($env:path).</span></span>
- <span data-ttu-id="38ad8-219">필터 및 함수</span><span class="sxs-lookup"><span data-stu-id="38ad8-219">Filter and Function.</span></span> <span data-ttu-id="38ad8-220">모든 PowerShell 고급 및 단순 함수와 필터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-220">Gets all PowerShell advanced and simple functions and filters.</span></span>
- <span data-ttu-id="38ad8-221">스크립트.</span><span class="sxs-lookup"><span data-stu-id="38ad8-221">Script.</span></span> <span data-ttu-id="38ad8-222">모든 스크립트 블록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-222">Gets all script blocks.</span></span> <span data-ttu-id="38ad8-223">PowerShell 스크립트 (ps1 파일)를 가져오려면 ExternalScript 값을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-223">To get PowerShell scripts (.ps1 files), use the ExternalScript value.</span></span>
- <span data-ttu-id="38ad8-224">워크플로.</span><span class="sxs-lookup"><span data-stu-id="38ad8-224">Workflow.</span></span> <span data-ttu-id="38ad8-225">모든 워크플로를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-225">Gets all workflows.</span></span> <span data-ttu-id="38ad8-226">워크플로에 대한 자세한 내용은 Introducing Windows PowerShell Workflow를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="38ad8-226">For more information about workflows, see Introducing Windows PowerShell Workflow.</span></span>

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

### <span data-ttu-id="38ad8-227">-변수인 fullyqualifiedmodule</span><span class="sxs-lookup"><span data-stu-id="38ad8-227">-FullyQualifiedModule</span></span>

<span data-ttu-id="38ad8-228">[ModuleSpecification 생성자 (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_)의 **설명** 섹션에서 설명 하는 **ModuleSpecification** 개체 형식으로 지정 된 이름을 사용 하 여 모듈을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-228">Specifies modules with names that are specified in the form of **ModuleSpecification** objects, described in the **Remarks** section of [ModuleSpecification Constructor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span></span>
<span data-ttu-id="38ad8-229">예를 들어 **변수인 fullyqualifiedmodule** 매개 변수는 다음 형식 중 하나로 지정 된 모듈 이름을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-229">For example, the **FullyQualifiedModule** parameter accepts a module name that is specified in one of the following formats:</span></span>

- `@{ModuleName = "modulename"; ModuleVersion = "version_number"}`
- `@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}`

<span data-ttu-id="38ad8-230">**ModuleName** 및 **ModuleVersion** 은 필수이지만 **Guid** 는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-230">**ModuleName** and **ModuleVersion** are required, but **Guid** is optional.</span></span>

<span data-ttu-id="38ad8-231">**모듈** 매개 변수와 동일한 명령에 **변수인 fullyqualifiedmodule** 매개 변수를 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-231">You cannot specify the **FullyQualifiedModule** parameter in the same command as a **Module** parameter.</span></span> <span data-ttu-id="38ad8-232">두 매개 변수는 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-232">The two parameters are mutually exclusive.</span></span>

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

### <span data-ttu-id="38ad8-233">-ListImported</span><span class="sxs-lookup"><span data-stu-id="38ad8-233">-ListImported</span></span>

<span data-ttu-id="38ad8-234">이 cmdlet은 현재 세션의 명령만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-234">Indicates that this cmdlet gets only commands in the current session.</span></span>

<span data-ttu-id="38ad8-235">PowerShell 3.0부터 시작 하 여 기본적으로 `Get-Command` 현재 세션의 명령을 포함 하 여 모든 설치 된 명령을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-235">Starting in PowerShell 3.0, by default, `Get-Command` gets all installed commands, including, but not limited to, the commands in the current session.</span></span> <span data-ttu-id="38ad8-236">PowerShell 2.0에서는 현재 세션의 명령만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-236">In PowerShell 2.0, it gets only commands in the current session.</span></span>

<span data-ttu-id="38ad8-237">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-237">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="38ad8-238">-모듈</span><span class="sxs-lookup"><span data-stu-id="38ad8-238">-Module</span></span>

<span data-ttu-id="38ad8-239">모듈의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-239">Specifies an array of modules.</span></span> <span data-ttu-id="38ad8-240">이 cmdlet은 지정 된 모듈 또는 스냅인에서 가져온 명령을 가져옵니다. 모듈 또는 스냅인의 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-240">This cmdlet gets the commands that came from the specified modules or snap-ins. Enter the names of modules or snap-ins.</span></span>

<span data-ttu-id="38ad8-241">이 매개 변수는 문자열 값을 사용 하지만이 매개 변수의 값은 **PSSnapinInfo** , 및 cmdlet이 반환 하는 개체와 같은 **psmoduleinfo** 또는 PSSnapinInfo 개체 일 수도 있습니다 `Get-Module` `Get-PSSnapin` `Import-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="38ad8-241">This parameter takes string values, but the value of this parameter can also be a **PSModuleInfo** or **PSSnapinInfo** object, such as the objects that the `Get-Module`, `Get-PSSnapin`, and `Import-PSSession` cmdlets return.</span></span>

<span data-ttu-id="38ad8-242">이름( **Module** ) 또는 별칭( **PSSnapin** )으로 이 매개 변수를 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-242">You can refer to this parameter by its name, **Module** , or by its alias, **PSSnapin** .</span></span>
<span data-ttu-id="38ad8-243">선택한 매개 변수 이름은 명령 출력에 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-243">The parameter name that you choose has no effect on the command output.</span></span>

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

### <span data-ttu-id="38ad8-244">-Name</span><span class="sxs-lookup"><span data-stu-id="38ad8-244">-Name</span></span>

<span data-ttu-id="38ad8-245">이름 배열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-245">Specifies an array of names.</span></span> <span data-ttu-id="38ad8-246">이 cmdlet은 지정 된 이름의 명령만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-246">This cmdlet gets only commands that have the specified name.</span></span> <span data-ttu-id="38ad8-247">이름 또는 이름 패턴을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-247">Enter a name or name pattern.</span></span> <span data-ttu-id="38ad8-248">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-248">Wildcard characters are permitted.</span></span>

<span data-ttu-id="38ad8-249">동일한 이름을 가진 명령을 가져오려면 **All** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-249">To get commands that have the same name, use the **All** parameter.</span></span> <span data-ttu-id="38ad8-250">두 명령의 이름이 같은 경우 기본적으로 `Get-Command` 명령 이름을 입력할 때 실행 되는 명령을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-250">When two commands have the same name, by default, `Get-Command` gets the command that runs when you type the command name.</span></span>

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

### <span data-ttu-id="38ad8-251">-명사</span><span class="sxs-lookup"><span data-stu-id="38ad8-251">-Noun</span></span>

<span data-ttu-id="38ad8-252">명령 명사 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-252">Specifies an array of command nouns.</span></span> <span data-ttu-id="38ad8-253">이 cmdlet은 지정 된 명사를 포함 하는 이름을 가진 cmdlet, 함수 및 별칭을 포함 하는 명령을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-253">This cmdlet gets commands, which include cmdlets, functions, and aliases, that have names that include the specified noun.</span></span> <span data-ttu-id="38ad8-254">명사 또는 명사 패턴을 하나 이상 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-254">Enter one or more nouns or noun patterns.</span></span> <span data-ttu-id="38ad8-255">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-255">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="38ad8-256">-ParameterName</span><span class="sxs-lookup"><span data-stu-id="38ad8-256">-ParameterName</span></span>

<span data-ttu-id="38ad8-257">매개 변수 이름 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-257">Specifies an array of parameter names.</span></span> <span data-ttu-id="38ad8-258">이 cmdlet은 세션에서 지정 된 매개 변수가 있는 명령을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-258">This cmdlet gets commands in the session that have the specified parameters.</span></span> <span data-ttu-id="38ad8-259">매개 변수 이름 또는 매개 변수 별칭을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-259">Enter parameter names or parameter aliases.</span></span> <span data-ttu-id="38ad8-260">와일드카드 문자가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-260">Wildcard characters are supported.</span></span>

<span data-ttu-id="38ad8-261">**ParameterName** 및 **ParameterType** 매개 변수는 현재 세션의 명령만 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-261">The **ParameterName** and **ParameterType** parameters search only commands in the current session.</span></span>

<span data-ttu-id="38ad8-262">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-262">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="38ad8-263">-ParameterType</span><span class="sxs-lookup"><span data-stu-id="38ad8-263">-ParameterType</span></span>

<span data-ttu-id="38ad8-264">매개 변수 이름 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-264">Specifies an array of parameter names.</span></span> <span data-ttu-id="38ad8-265">이 cmdlet은 세션에서 지정 된 유형의 매개 변수가 있는 명령을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-265">This cmdlet gets commands in the session that have parameters of the specified type.</span></span> <span data-ttu-id="38ad8-266">매개 변수 유형의 전체 이름이나 부분 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-266">Enter the full name or partial name of a parameter type.</span></span> <span data-ttu-id="38ad8-267">와일드카드 문자가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-267">Wildcard characters are supported.</span></span>

<span data-ttu-id="38ad8-268">**ParameterName** 및 **ParameterType** 매개 변수는 현재 세션의 명령만 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-268">The **ParameterName** and **ParameterType** parameters search only commands in the current session.</span></span>

<span data-ttu-id="38ad8-269">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-269">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="38ad8-270">-ShowCommandInfo</span><span class="sxs-lookup"><span data-stu-id="38ad8-270">-ShowCommandInfo</span></span>

<span data-ttu-id="38ad8-271">이 cmdlet이 명령 정보를 표시 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-271">Indicates that this cmdlet displays command information.</span></span>

<span data-ttu-id="38ad8-272">이 매개 변수는 Windows PowerShell 5.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-272">This parameter was introduced in Windows PowerShell 5.0.</span></span>

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

### <span data-ttu-id="38ad8-273">-구문</span><span class="sxs-lookup"><span data-stu-id="38ad8-273">-Syntax</span></span>

<span data-ttu-id="38ad8-274">이 cmdlet은 명령에 대해 다음과 같은 지정 된 데이터만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-274">Indicates that this cmdlet gets only the following specified data about the command:</span></span>

- <span data-ttu-id="38ad8-275">별칭.</span><span class="sxs-lookup"><span data-stu-id="38ad8-275">Aliases.</span></span> <span data-ttu-id="38ad8-276">표준 이름을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-276">Gets the standard name.</span></span>
- <span data-ttu-id="38ad8-277">Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="38ad8-277">Cmdlets.</span></span> <span data-ttu-id="38ad8-278">구문을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-278">Gets the syntax.</span></span>
- <span data-ttu-id="38ad8-279">함수 및 필터.</span><span class="sxs-lookup"><span data-stu-id="38ad8-279">Functions and filters.</span></span> <span data-ttu-id="38ad8-280">함수 정의를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-280">Gets the function definition.</span></span>
- <span data-ttu-id="38ad8-281">스크립트 및 응용 프로그램 또는 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-281">Scripts and applications or files.</span></span> <span data-ttu-id="38ad8-282">경로와 파일 이름을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-282">Gets the path and filename.</span></span>

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

### <span data-ttu-id="38ad8-283">-TotalCount</span><span class="sxs-lookup"><span data-stu-id="38ad8-283">-TotalCount</span></span>

<span data-ttu-id="38ad8-284">가져올 명령 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-284">Specifies the number of commands to get.</span></span> <span data-ttu-id="38ad8-285">이 매개 변수를 사용하여 명령의 출력을 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-285">You can use this parameter to limit the output of a command.</span></span>

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

### <span data-ttu-id="38ad8-286">-동사</span><span class="sxs-lookup"><span data-stu-id="38ad8-286">-Verb</span></span>

<span data-ttu-id="38ad8-287">명령 동사의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-287">Specifies an array of command verbs.</span></span> <span data-ttu-id="38ad8-288">이 cmdlet은 지정 된 동사가 포함 된 이름을 가진 cmdlet, 함수 및 별칭을 포함 하는 명령을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-288">This cmdlet gets commands, which include cmdlets, functions, and aliases, that have names that include the specified verb.</span></span> <span data-ttu-id="38ad8-289">동사 또는 동사 패턴을 하나 이상 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-289">Enter one or more verbs or verb patterns.</span></span> <span data-ttu-id="38ad8-290">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-290">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="38ad8-291">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="38ad8-291">CommonParameters</span></span>

<span data-ttu-id="38ad8-292">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="38ad8-292">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="38ad8-293">자세한 내용은 [about_CommonParameters](About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="38ad8-293">For more information, see [about_CommonParameters](About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="38ad8-294">입력</span><span class="sxs-lookup"><span data-stu-id="38ad8-294">INPUTS</span></span>

### <span data-ttu-id="38ad8-295">System.String</span><span class="sxs-lookup"><span data-stu-id="38ad8-295">System.String</span></span>

<span data-ttu-id="38ad8-296">이 cmdlet에 명령 이름을 파이프 하 여 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-296">You can pipe command names to this cmdlet.</span></span>

## <span data-ttu-id="38ad8-297">출력</span><span class="sxs-lookup"><span data-stu-id="38ad8-297">OUTPUTS</span></span>

### <span data-ttu-id="38ad8-298">System.web. CommandInfo</span><span class="sxs-lookup"><span data-stu-id="38ad8-298">System.Management.Automation.CommandInfo</span></span>

<span data-ttu-id="38ad8-299">이 cmdlet은 **Commandinfo** 클래스에서 파생 된 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-299">This cmdlet returns objects derived from the **CommandInfo** class.</span></span> <span data-ttu-id="38ad8-300">반환 되는 개체의 유형은 가져오는 명령의 유형에 따라 달라 집니다 `Get-Command` .</span><span class="sxs-lookup"><span data-stu-id="38ad8-300">The type of object that is returned depends on the type of command that `Get-Command` gets.</span></span>

### <span data-ttu-id="38ad8-301">System.management.automation.aliasinfo.</span><span class="sxs-lookup"><span data-stu-id="38ad8-301">System.Management.Automation.AliasInfo</span></span>

<span data-ttu-id="38ad8-302">별칭을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-302">Represents aliases.</span></span>

### <span data-ttu-id="38ad8-303">System.object 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-303">System.Management.Automation.ApplicationInfo</span></span>

<span data-ttu-id="38ad8-304">응용 프로그램 및 파일을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-304">Represents applications and files.</span></span>

### <span data-ttu-id="38ad8-305">System.object..</span><span class="sxs-lookup"><span data-stu-id="38ad8-305">System.Management.Automation.CmdletInfo</span></span>

<span data-ttu-id="38ad8-306">cmdlet을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-306">Represents cmdlets.</span></span>

### <span data-ttu-id="38ad8-307">System.object를 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-307">System.Management.Automation.FunctionInfo</span></span>

<span data-ttu-id="38ad8-308">함수와 필터를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-308">Represents functions and filters.</span></span>

### <span data-ttu-id="38ad8-309">System.web. WorkflowInfo</span><span class="sxs-lookup"><span data-stu-id="38ad8-309">System.Management.Automation.WorkflowInfo</span></span>

<span data-ttu-id="38ad8-310">워크플로를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-310">Represents workflows.</span></span>

## <span data-ttu-id="38ad8-311">참고</span><span class="sxs-lookup"><span data-stu-id="38ad8-311">NOTES</span></span>

* <span data-ttu-id="38ad8-312">세션에서 이름이 같은 명령을 둘 이상 사용할 수 있는 경우 `Get-Command` 명령 이름을 입력할 때 실행 되는 명령을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-312">When more than one command that has the same name is available to the session, `Get-Command` returns the command that runs when you type the command name.</span></span> <span data-ttu-id="38ad8-313">실행 순서에 나열 된 것과 동일한 이름을 가진 명령을 가져오려면 **All** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-313">To get commands that have the same name, listed in run order, use the **All** parameter.</span></span> <span data-ttu-id="38ad8-314">자세한 내용은 [about_Command_Precedence](../Microsoft.PowerShell.Core/About/about_Command_Precedence.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="38ad8-314">For more information, see [about_Command_Precedence](../Microsoft.PowerShell.Core/About/about_Command_Precedence.md).</span></span>
* <span data-ttu-id="38ad8-315">모듈을 자동으로 가져올 때 효과는 cmdlet을 사용 하는 것과 같습니다 `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="38ad8-315">When a module is imported automatically, the effect is the same as using the `Import-Module` cmdlet.</span></span> <span data-ttu-id="38ad8-316">모듈은 세션에서 명령, 유형 및 형식 지정 파일을 추가하고 스크립트를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-316">The module can add commands, types and formatting files, and run scripts in the session.</span></span>
  <span data-ttu-id="38ad8-317">모듈 자동 가져오기를 사용 하거나 사용 하지 않도록 설정 하 고 구성 하려면 `$PSModuleAutoLoadingPreference` 기본 설정 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="38ad8-317">To enable, disable, and configuration automatic importing of modules, use the `$PSModuleAutoLoadingPreference` preference variable.</span></span> <span data-ttu-id="38ad8-318">자세한 내용은 [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="38ad8-318">For more information, see [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span></span>

## <span data-ttu-id="38ad8-319">관련 링크</span><span class="sxs-lookup"><span data-stu-id="38ad8-319">RELATED LINKS</span></span>

[<span data-ttu-id="38ad8-320">Export-PSSession</span><span class="sxs-lookup"><span data-stu-id="38ad8-320">Export-PSSession</span></span>](../Microsoft.PowerShell.Utility/Export-PSSession.md)

[<span data-ttu-id="38ad8-321">Get-Help</span><span class="sxs-lookup"><span data-stu-id="38ad8-321">Get-Help</span></span>](Get-Help.md)

[<span data-ttu-id="38ad8-322">Get-Member</span><span class="sxs-lookup"><span data-stu-id="38ad8-322">Get-Member</span></span>](../Microsoft.PowerShell.Utility/Get-Member.md)

[<span data-ttu-id="38ad8-323">Get-PSDrive</span><span class="sxs-lookup"><span data-stu-id="38ad8-323">Get-PSDrive</span></span>](../Microsoft.PowerShell.Management/Get-PSDrive.md)

[<span data-ttu-id="38ad8-324">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="38ad8-324">Import-PSSession</span></span>](../Microsoft.PowerShell.Utility/Import-PSSession.md)

[<span data-ttu-id="38ad8-325">about_Command_Precedence</span><span class="sxs-lookup"><span data-stu-id="38ad8-325">about_Command_Precedence</span></span>](About/about_Command_Precedence.md)
