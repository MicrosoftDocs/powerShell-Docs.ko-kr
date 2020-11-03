---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 09/11/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-psrolecapabilityfile?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSRoleCapabilityFile
ms.openlocfilehash: 3dca5f922f31690bb78ccc610b4ed44b7423ca47
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93212857"
---
# <span data-ttu-id="f9fad-103">New-PSRoleCapabilityFile</span><span class="sxs-lookup"><span data-stu-id="f9fad-103">New-PSRoleCapabilityFile</span></span>

## <span data-ttu-id="f9fad-104">개요</span><span class="sxs-lookup"><span data-stu-id="f9fad-104">SYNOPSIS</span></span>
<span data-ttu-id="f9fad-105">세션 구성을 통해 노출할 기능 집합을 정의 하는 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-105">Creates a file that defines a set of capabilities to be exposed through a session configuration.</span></span>

## <span data-ttu-id="f9fad-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f9fad-106">SYNTAX</span></span>

```
New-PSRoleCapabilityFile [-Path] <String> [-Guid <Guid>] [-Author <String>] [-Description <String>]
 [-CompanyName <String>] [-Copyright <String>] [-ModulesToImport <Object[]>] [-VisibleAliases <String[]>]
 [-VisibleCmdlets <Object[]>] [-VisibleFunctions <Object[]>] [-VisibleExternalCommands <String[]>]
 [-VisibleProviders <String[]>] [-ScriptsToProcess <String[]>] [-AliasDefinitions <IDictionary[]>]
 [-FunctionDefinitions <IDictionary[]>] [-VariableDefinitions <Object>] [-EnvironmentVariables <IDictionary>]
 [-TypesToProcess <String[]>] [-FormatsToProcess <String[]>] [-AssembliesToLoad <String[]>]
 [<CommonParameters>]
```

## <span data-ttu-id="f9fad-107">설명</span><span class="sxs-lookup"><span data-stu-id="f9fad-107">DESCRIPTION</span></span>

<span data-ttu-id="f9fad-108">`New-PSRoleCapabilityFile`Cmdlet은 세션 구성 파일을 통해 노출 될 수 있는 사용자 기능 집합을 정의 하는 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-108">The `New-PSRoleCapabilityFile` cmdlet creates a file that defines a set of user capabilities that can be exposed through session configuration files.</span></span> <span data-ttu-id="f9fad-109">여기에는 사용자가 사용할 수 있는 cmdlet, 함수 및 스크립트를 결정 하는 작업이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-109">This includes determining which cmdlets, functions, and scripts are available to users.</span></span> <span data-ttu-id="f9fad-110">기능 파일은 세션 구성 속성 및 값의 해시 테이블을 포함 하는 사람이 읽을 수 있는 텍스트 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-110">The capability file is a human-readable text file that contains a hash table of session configuration properties and values.</span></span> <span data-ttu-id="f9fad-111">파일은 .psrc 파일 이름 확장명을 가지 며 둘 이상의 세션 구성에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-111">The file has a .psrc file name extension, and can be used by more than one session configuration.</span></span>

<span data-ttu-id="f9fad-112">의 모든 매개 변수는 `New-PSRoleCapabilityFile` 파일의 파일 경로를 지정 하는 **Path** 매개 변수를 제외 하 고는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-112">All the parameters of `New-PSRoleCapabilityFile` are optional except for the **Path** parameter, which specifies the file path for the file.</span></span> <span data-ttu-id="f9fad-113">Cmdlet을 실행할 때 매개 변수를 포함 하지 않는 경우에는 매개 변수 설명에 명시 된 경우를 제외 하 고 세션 구성 파일의 해당 키가 주석으로 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-113">If you do not include a parameter when you run the cmdlet, the corresponding key in the session configuration file is commented-out, except where noted in the parameter description.</span></span> <span data-ttu-id="f9fad-114">예를 들어 **AssembliesToLoad** 매개 변수를 포함 하지 않는 경우 세션 구성 파일의 해당 섹션은 주석으로 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-114">For example, if you do not include the **AssembliesToLoad** parameter then that section of the session configuration file is commented out.</span></span>

<span data-ttu-id="f9fad-115">세션 구성에서 역할 기능 파일을 사용 하려면 먼저 올바른 PowerShell 모듈 폴더의 **RoleCapabilities** 하위 폴더에 파일을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-115">To use the role capability file in a session configuration, first place the file in a **RoleCapabilities** subfolder of a valid PowerShell module folder.</span></span> <span data-ttu-id="f9fad-116">그런 다음 PowerShell 세션 구성 파일 (.psc)의 **Roledefinitions** 필드에서 이름을 기준으로 파일을 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-116">Then reference the file by name in the **RoleDefinitions** field in a PowerShell Session Configuration (.pssc) file.</span></span>

<span data-ttu-id="f9fad-117">이 cmdlet은 Windows PowerShell 5.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-117">This cmdlet was introduced in Windows PowerShell 5.0.</span></span>

## <span data-ttu-id="f9fad-118">예제</span><span class="sxs-lookup"><span data-stu-id="f9fad-118">EXAMPLES</span></span>

### <span data-ttu-id="f9fad-119">예 1: 빈 역할 기능 파일 만들기</span><span class="sxs-lookup"><span data-stu-id="f9fad-119">Example 1: Create a blank role capability file</span></span>

<span data-ttu-id="f9fad-120">이 예제에서는 기본 (공백) 값을 사용 하는 새 역할 기능 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-120">This example creates a new role capability file that uses the default (blank) values.</span></span> <span data-ttu-id="f9fad-121">나중에 텍스트 편집기에서 파일을 편집 하 여 이러한 구성 설정을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-121">The file can later be edited in a text editor to change these configuration settings.</span></span>

```powershell
New-PSRoleCapabilityFile -Path ".\ExampleFile.psrc"
```

### <span data-ttu-id="f9fad-122">예제 2: 사용자가 서비스 및 VDI 컴퓨터를 다시 시작할 수 있도록 하는 역할 기능 파일 만들기</span><span class="sxs-lookup"><span data-stu-id="f9fad-122">Example 2: Create a role capability file allowing users to restart services and any VDI computer</span></span>

<span data-ttu-id="f9fad-123">이 예제에서는 사용자가 특정 이름 패턴과 일치 하는 서비스 및 컴퓨터를 다시 시작할 수 있도록 하는 샘플 역할 기능 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-123">This example creates a sample role capability file that enables users to restart services and computers that match a specific name pattern.</span></span> <span data-ttu-id="f9fad-124">이름 필터링은 **ValidatePattern** 매개 변수를 정규식으로 설정 하 여 정의 됩니다 `VDI\d+` .</span><span class="sxs-lookup"><span data-stu-id="f9fad-124">Name filtering is defined by setting the **ValidatePattern** parameter to the regular expression `VDI\d+`.</span></span>

```powershell
$roleParameters = @{
    Path = ".\Maintenance.psrc"
    Author = "User01"
    CompanyName = "Fabrikam Corporation"
    Description = "This role enables users to restart any service and restart any VDI computer."
    ModulesToImport = "Microsoft.PowerShell.Core"
    VisibleCmdlets = "Restart-Service", @{
                      Name = "Restart-Computer"
                      Parameters = @{ Name = "ComputerName"; ValidatePattern = "VDI\d+" }
    }
}
New-PSRoleCapabilityFile @roleParameters
```

## <span data-ttu-id="f9fad-125">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f9fad-125">PARAMETERS</span></span>

### <span data-ttu-id="f9fad-126">-AliasDefinitions</span><span class="sxs-lookup"><span data-stu-id="f9fad-126">-AliasDefinitions</span></span>

<span data-ttu-id="f9fad-127">역할 기능 파일을 사용 하는 세션에 지정 된 별칭을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-127">Adds the specified aliases to sessions that use the role capability file.</span></span> <span data-ttu-id="f9fad-128">다음 키를 사용하여 해시 테이블을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-128">Enter a hash table with the following keys:</span></span>

- <span data-ttu-id="f9fad-129">이름.</span><span class="sxs-lookup"><span data-stu-id="f9fad-129">Name.</span></span> <span data-ttu-id="f9fad-130">별칭의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-130">Name of the alias.</span></span> <span data-ttu-id="f9fad-131">이 키는 필수입니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-131">This key is required.</span></span>
- <span data-ttu-id="f9fad-132">값.</span><span class="sxs-lookup"><span data-stu-id="f9fad-132">Value.</span></span> <span data-ttu-id="f9fad-133">별칭이 나타내는 명령입니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-133">The command that the alias represents.</span></span> <span data-ttu-id="f9fad-134">이 키는 필수입니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-134">This key is required.</span></span>
- <span data-ttu-id="f9fad-135">설명</span><span class="sxs-lookup"><span data-stu-id="f9fad-135">Description.</span></span> <span data-ttu-id="f9fad-136">별칭을 설명하는 텍스트 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-136">A text string that describes the alias.</span></span> <span data-ttu-id="f9fad-137">이 키는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-137">This key is optional.</span></span>
- <span data-ttu-id="f9fad-138">옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-138">Options.</span></span> <span data-ttu-id="f9fad-139">별칭 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-139">Alias options.</span></span> <span data-ttu-id="f9fad-140">이 키는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-140">This key is optional.</span></span> <span data-ttu-id="f9fad-141">기본값은 None입니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-141">The default value is None.</span></span> <span data-ttu-id="f9fad-142">이 매개 변수에 허용 되는 값은 None, ReadOnly, Constant, Private 또는 AllScope입니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-142">The acceptable values for this parameter are: None, ReadOnly, Constant, Private, or AllScope.</span></span>

<span data-ttu-id="f9fad-143">`@{Name="hlp";Value="Get-Help";Description="Gets help";Options="ReadOnly"}`</span><span class="sxs-lookup"><span data-stu-id="f9fad-143">For example: `@{Name="hlp";Value="Get-Help";Description="Gets help";Options="ReadOnly"}`</span></span>

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

### <span data-ttu-id="f9fad-144">-AssembliesToLoad</span><span class="sxs-lookup"><span data-stu-id="f9fad-144">-AssembliesToLoad</span></span>

<span data-ttu-id="f9fad-145">역할 기능 파일을 사용 하는 세션에 로드할 어셈블리를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-145">Specifies the assemblies to load into the sessions that use the role capability file.</span></span>

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

### <span data-ttu-id="f9fad-146">-작성자</span><span class="sxs-lookup"><span data-stu-id="f9fad-146">-Author</span></span>

<span data-ttu-id="f9fad-147">역할 기능 파일을 만든 사용자를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-147">Specifies the user that created the role capability file.</span></span>

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

### <span data-ttu-id="f9fad-148">-CompanyName</span><span class="sxs-lookup"><span data-stu-id="f9fad-148">-CompanyName</span></span>

<span data-ttu-id="f9fad-149">역할 기능 파일을 만든 회사를 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-149">Identifies the company that created the role capability file.</span></span>
<span data-ttu-id="f9fad-150">기본값은 알 수 없음입니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-150">The default value is Unknown.</span></span>

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

### <span data-ttu-id="f9fad-151">-저작권</span><span class="sxs-lookup"><span data-stu-id="f9fad-151">-Copyright</span></span>

<span data-ttu-id="f9fad-152">역할 기능 파일의 저작권을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-152">Specifies a copyright for the role capability file.</span></span> <span data-ttu-id="f9fad-153">이 매개 변수를 생략 하면은 `New-PSRoleCapabilityFile` **Author** 매개 변수 값을 사용 하 여 저작권 설명을 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-153">If you omit this parameter, `New-PSRoleCapabilityFile` generates a copyright statement by using the value of the **Author** parameter.</span></span>

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

### <span data-ttu-id="f9fad-154">-Description</span><span class="sxs-lookup"><span data-stu-id="f9fad-154">-Description</span></span>

<span data-ttu-id="f9fad-155">역할 기능 파일에 대 한 설명을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-155">Specifies a description for the role capability file.</span></span>

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

### <span data-ttu-id="f9fad-156">-환경 변수</span><span class="sxs-lookup"><span data-stu-id="f9fad-156">-EnvironmentVariables</span></span>

<span data-ttu-id="f9fad-157">이 역할 기능 파일을 노출 하는 세션에 대 한 환경 변수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-157">Specifies the environment variables for sessions that expose this role capability file.</span></span> <span data-ttu-id="f9fad-158">키가 환경 변수 이름이고 값이 환경 변수 값인 해시 테이블을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-158">Enter a hash table in which the keys are the environment variable names and the values are the environment variable values.</span></span>

<span data-ttu-id="f9fad-159">`EnvironmentVariables=@{TestShare="\\\\Server01\TestShare"}`</span><span class="sxs-lookup"><span data-stu-id="f9fad-159">For example: `EnvironmentVariables=@{TestShare="\\\\Server01\TestShare"}`</span></span>

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

### <span data-ttu-id="f9fad-160">-FormatsToProcess</span><span class="sxs-lookup"><span data-stu-id="f9fad-160">-FormatsToProcess</span></span>

<span data-ttu-id="f9fad-161">역할 기능 파일을 사용 하는 세션에서 실행 되는 형식 지정 파일 (. types.ps1xml)을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-161">Specifies the formatting files (.ps1xml) that run in sessions that use the role capability file.</span></span> <span data-ttu-id="f9fad-162">이 매개 변수 값은 형식 지정 파일의 전체 또는 절대 경로 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-162">The value of this parameter must be a full or absolute path of the formatting files.</span></span>

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

### <span data-ttu-id="f9fad-163">-FunctionDefinitions</span><span class="sxs-lookup"><span data-stu-id="f9fad-163">-FunctionDefinitions</span></span>

<span data-ttu-id="f9fad-164">역할 기능을 노출 하는 세션에 지정 된 함수를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-164">Adds the specified functions to sessions that expose the role capability.</span></span> <span data-ttu-id="f9fad-165">다음 키를 사용하여 해시 테이블을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-165">Enter a hash table with the following keys:</span></span>

- <span data-ttu-id="f9fad-166">이름.</span><span class="sxs-lookup"><span data-stu-id="f9fad-166">Name.</span></span> <span data-ttu-id="f9fad-167">함수의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-167">Name of the function.</span></span> <span data-ttu-id="f9fad-168">이 키는 필수입니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-168">This key is required.</span></span>
- <span data-ttu-id="f9fad-169">ScriptBlock.</span><span class="sxs-lookup"><span data-stu-id="f9fad-169">ScriptBlock.</span></span> <span data-ttu-id="f9fad-170">함수 본문입니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-170">Function body.</span></span> <span data-ttu-id="f9fad-171">스크립트 블록을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-171">Enter a script block.</span></span> <span data-ttu-id="f9fad-172">이 키는 필수입니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-172">This key is required.</span></span>
- <span data-ttu-id="f9fad-173">옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-173">Options.</span></span> <span data-ttu-id="f9fad-174">함수 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-174">Function options.</span></span> <span data-ttu-id="f9fad-175">이 키는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-175">This key is optional.</span></span> <span data-ttu-id="f9fad-176">기본값은 None입니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-176">The default value is None.</span></span> <span data-ttu-id="f9fad-177">이 매개 변수에 허용 되는 값은 None, ReadOnly, Constant, Private 또는 AllScope입니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-177">The acceptable values for this parameter are: are None, ReadOnly, Constant, Private, or AllScope.</span></span>

<span data-ttu-id="f9fad-178">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="f9fad-178">For example:</span></span>

`@{Name="Get-PowerShellProcess";ScriptBlock={Get-Process PowerShell};Options="AllScope"}`

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

### <span data-ttu-id="f9fad-179">-Guid</span><span class="sxs-lookup"><span data-stu-id="f9fad-179">-Guid</span></span>

<span data-ttu-id="f9fad-180">역할 기능 파일의 고유 식별자를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-180">Specifies a unique identifier for the role capability file.</span></span> <span data-ttu-id="f9fad-181">이 매개 변수를 생략 하면는 `New-PSRoleCapabilityFile` 파일에 대 한 GUID를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-181">If you omit this parameter, `New-PSRoleCapabilityFile` generates a GUID for the file.</span></span> <span data-ttu-id="f9fad-182">PowerShell에서 새 GUID를 만들려면를 입력 `[guid]::NewGuid()` 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-182">To create a new GUID in PowerShell, type `[guid]::NewGuid()`.</span></span>

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

### <span data-ttu-id="f9fad-183">-ModulesToImport</span><span class="sxs-lookup"><span data-stu-id="f9fad-183">-ModulesToImport</span></span>

<span data-ttu-id="f9fad-184">역할 기능 파일을 사용 하는 세션에 자동으로 가져오는 모듈을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-184">Specifies the modules that are automatically imported into sessions that use the role capability file.</span></span> <span data-ttu-id="f9fad-185">기본적으로 나열 된 모듈의 모든 명령이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-185">By default, all the commands in listed modules are visible.</span></span> <span data-ttu-id="f9fad-186">**VisibleCmdlets** 또는 **VisibleFunctions** 와 함께 사용 하는 경우 지정 된 모듈에서 표시 되는 명령을 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-186">When used with **VisibleCmdlets** or **VisibleFunctions** , the commands visible from the specified modules can be restricted.</span></span>

<span data-ttu-id="f9fad-187">이 매개 변수 값에 사용 되는 각 모듈은 문자열 또는 해시 테이블로 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-187">Each module used in the value of this parameter can be represented by a string or by a hash table.</span></span> <span data-ttu-id="f9fad-188">모듈 문자열은 모듈의 이름 으로만 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-188">A module string consists only of the name of the module.</span></span> <span data-ttu-id="f9fad-189">모듈 해시 테이블에는 **ModuleName** , **ModuleVersion** 및 **GUID** 키가 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-189">A module hash table can include **ModuleName** , **ModuleVersion** , and **GUID** keys.</span></span> <span data-ttu-id="f9fad-190">**ModuleName** 키만 필수입니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-190">Only the **ModuleName** key is required.</span></span>

<span data-ttu-id="f9fad-191">예를 들어 다음 값은 문자열과 해시 테이블로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-191">For example, the following value consists of a string and a hash table.</span></span> <span data-ttu-id="f9fad-192">순서와 관계없이 문자열과 해시 테이블의 모든 조합이 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-192">Any combination of strings and hash tables, in any order, is valid.</span></span>

`"TroubleshootingPack", @{ModuleName="PSDiagnostics"; ModuleVersion="1.0.0.0";GUID="c61d6278-02a3-4618-ae37-a524d40a7f44"}`

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

### <span data-ttu-id="f9fad-193">-Path</span><span class="sxs-lookup"><span data-stu-id="f9fad-193">-Path</span></span>

<span data-ttu-id="f9fad-194">역할 기능 파일의 경로와 파일 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-194">Specifies the path and filename of the role capability file.</span></span> <span data-ttu-id="f9fad-195">파일에는 파일 `.psrc` 이름 확장명이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-195">The file must have a `.psrc` filename extension.</span></span>

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

### <span data-ttu-id="f9fad-196">-ScriptsToProcess</span><span class="sxs-lookup"><span data-stu-id="f9fad-196">-ScriptsToProcess</span></span>

<span data-ttu-id="f9fad-197">역할 기능 파일을 사용 하는 세션에 추가할 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-197">Specifies scripts to add to sessions that use the role capability file.</span></span> <span data-ttu-id="f9fad-198">스크립트의 경로와 파일 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-198">Enter the path and file names of the scripts.</span></span> <span data-ttu-id="f9fad-199">이 매개 변수 값은 스크립트 파일 이름의 전체 또는 절대 경로 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-199">The value of this parameter must be a full or absolute path of the script file names.</span></span>

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

### <span data-ttu-id="f9fad-200">-TypesToProcess</span><span class="sxs-lookup"><span data-stu-id="f9fad-200">-TypesToProcess</span></span>

<span data-ttu-id="f9fad-201">역할 기능 파일을 사용 하는 세션에 추가할 형식 파일 (types.ps1xml)을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-201">Specifies type files (.ps1xml) to add to sessions that use the role capability file.</span></span> <span data-ttu-id="f9fad-202">유형 파일 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-202">Enter the type filenames.</span></span> <span data-ttu-id="f9fad-203">이 매개 변수 값은 형식 파일 이름의 전체 또는 절대 경로 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-203">The value of this parameter must be a full or absolute path of the type filenames.</span></span>

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

### <span data-ttu-id="f9fad-204">-VariableDefinitions</span><span class="sxs-lookup"><span data-stu-id="f9fad-204">-VariableDefinitions</span></span>

<span data-ttu-id="f9fad-205">역할 기능 파일을 사용 하는 세션에 추가할 변수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-205">Specifies variables to add to sessions that use the role capability file.</span></span> <span data-ttu-id="f9fad-206">다음 키를 사용하여 해시 테이블을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-206">Enter a hash table with the following keys:</span></span>

- <span data-ttu-id="f9fad-207">이름.</span><span class="sxs-lookup"><span data-stu-id="f9fad-207">Name.</span></span> <span data-ttu-id="f9fad-208">변수의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-208">Name of the variable.</span></span> <span data-ttu-id="f9fad-209">이 키는 필수입니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-209">This key is required.</span></span>
- <span data-ttu-id="f9fad-210">값.</span><span class="sxs-lookup"><span data-stu-id="f9fad-210">Value.</span></span> <span data-ttu-id="f9fad-211">변수 값입니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-211">Variable value.</span></span> <span data-ttu-id="f9fad-212">이 키는 필수입니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-212">This key is required.</span></span>
- <span data-ttu-id="f9fad-213">옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-213">Options.</span></span> <span data-ttu-id="f9fad-214">변수 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-214">Variable options.</span></span> <span data-ttu-id="f9fad-215">이 키는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-215">This key is optional.</span></span> <span data-ttu-id="f9fad-216">기본값은 None입니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-216">The default value is None.</span></span> <span data-ttu-id="f9fad-217">이 매개 변수에 허용 되는 값은 None, ReadOnly, Constant, Private 또는 AllScope입니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-217">The acceptable values for this parameter are: are None, ReadOnly, Constant, Private, or AllScope.</span></span>

<span data-ttu-id="f9fad-218">`@{Name="WarningPreference";Value="SilentlyContinue";Options="AllScope"}`</span><span class="sxs-lookup"><span data-stu-id="f9fad-218">For example: `@{Name="WarningPreference";Value="SilentlyContinue";Options="AllScope"}`</span></span>

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

### <span data-ttu-id="f9fad-219">-VisibleAliases</span><span class="sxs-lookup"><span data-stu-id="f9fad-219">-VisibleAliases</span></span>

<span data-ttu-id="f9fad-220">세션의 별칭을이 매개 변수 값에 지정 된 별칭 및 **AliasDefinition** 매개 변수에서 정의 하는 별칭으로 제한 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-220">Limits the aliases in the session to those aliases specified in the value of this parameter, plus any aliases that you define in the **AliasDefinition** parameter.</span></span> <span data-ttu-id="f9fad-221">와일드카드 문자가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-221">Wildcard characters are supported.</span></span>
<span data-ttu-id="f9fad-222">기본적으로 PowerShell 엔진에서 정의한 모든 별칭과 모듈에서 내보낸 모든 별칭이 세션에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-222">By default, all aliases that are defined by the PowerShell engine and all aliases that modules export are visible in the session.</span></span>

<span data-ttu-id="f9fad-223">예를 들어, 사용 가능한 별칭을 gm 및 gcm으로 제한 하려면 다음 구문을 사용 합니다. `VisibleAliases="gcm", "gp"`</span><span class="sxs-lookup"><span data-stu-id="f9fad-223">For example, to limit the available aliases to gm and gcm use this syntax: `VisibleAliases="gcm", "gp"`</span></span>

<span data-ttu-id="f9fad-224">**표시** 되는 매개 변수가 역할 기능 파일에 포함 된 경우 PowerShell은 `Import-Module` 세션에서 cmdlet 및 해당 별칭을 제거 합니다 `ipmo` .</span><span class="sxs-lookup"><span data-stu-id="f9fad-224">When any **Visible** parameter is included in the role capability file, PowerShell removes the `Import-Module` cmdlet and its `ipmo` alias from the session.</span></span>

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

### <span data-ttu-id="f9fad-225">-VisibleCmdlets</span><span class="sxs-lookup"><span data-stu-id="f9fad-225">-VisibleCmdlets</span></span>

<span data-ttu-id="f9fad-226">세션의 cmdlet을 이 매개 변수 값에 지정된 cmdlet으로 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-226">Limits the cmdlets in the session to those specified in the value of this parameter.</span></span> <span data-ttu-id="f9fad-227">와일드 카드 문자 및 모듈 정규화 된 이름이 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-227">Wildcard characters and Module Qualified Names are supported.</span></span>

<span data-ttu-id="f9fad-228">기본적으로 세션 내보내기의 모듈이 세션에 표시 되는 모든 cmdlet입니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-228">By default, all cmdlets that the modules in the session export are visible in the session.</span></span> <span data-ttu-id="f9fad-229">**SessionType** 및 **ModulesToImport** 매개 변수를 사용하여 세션으로 가져올 모듈과 스냅인을 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-229">Use the **SessionType** and **ModulesToImport** parameters to determine which modules and snap-ins are imported into the session.</span></span> <span data-ttu-id="f9fad-230">**ModulesToImport** 에서 cmdlet을 노출 하는 모듈이 없으면에서 `New-PSRoleCapabilityFile` 적절 한 모듈을 로드 하려고 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-230">If no modules in **ModulesToImport** expose the cmdlet, `New-PSRoleCapabilityFile` tries to load the appropriate module.</span></span>

<span data-ttu-id="f9fad-231">**표시** 되는 매개 변수가 세션 구성 파일에 포함 된 경우 PowerShell은 `Import-Module` 세션에서 cmdlet 및 해당 별칭을 제거 합니다 `ipmo` .</span><span class="sxs-lookup"><span data-stu-id="f9fad-231">When any **Visible** parameter is included in the session configuration file, PowerShell removes the `Import-Module` cmdlet and its `ipmo` alias from the session.</span></span>

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

### <span data-ttu-id="f9fad-232">-VisibleExternalCommands</span><span class="sxs-lookup"><span data-stu-id="f9fad-232">-VisibleExternalCommands</span></span>

<span data-ttu-id="f9fad-233">세션에서 실행할 수 있는 외부 이진 파일, 스크립트 및 명령을이 매개 변수 값에 지정 된 것으로 제한 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-233">Limits the external binaries, scripts and commands that can be executed in the session to those specified in the value of this parameter.</span></span>

<span data-ttu-id="f9fad-234">기본적으로이 세션에는 외부 명령이 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-234">By default, no external commands are visible in this session.</span></span>

<span data-ttu-id="f9fad-235">**표시** 되는 매개 변수가 세션 구성 파일에 포함 된 경우 PowerShell은 `Import-Module` 세션에서 cmdlet 및 해당 별칭을 제거 합니다 `ipmo` .</span><span class="sxs-lookup"><span data-stu-id="f9fad-235">When any **Visible** parameter is included in the session configuration file, PowerShell removes the `Import-Module` cmdlet and its `ipmo` alias from the session.</span></span>

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

### <span data-ttu-id="f9fad-236">-VisibleFunctions</span><span class="sxs-lookup"><span data-stu-id="f9fad-236">-VisibleFunctions</span></span>

<span data-ttu-id="f9fad-237">세션의 함수를이 매개 변수 값에 지정 된 것으로 제한 하 고 **functiondefinitions** 매개 변수에서 정의한 함수를 제한 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-237">Limits the functions in the session to those specified in the value of this parameter, plus any functions that you define in the **FunctionDefinitions** parameter.</span></span> <span data-ttu-id="f9fad-238">와일드카드 문자가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-238">Wildcard characters are supported.</span></span>

<span data-ttu-id="f9fad-239">기본적으로 세션의 모듈에서 내보낸 모든 함수는 해당 세션에서 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-239">By default, all functions exported by modules in the session are visible in that session.</span></span> <span data-ttu-id="f9fad-240">**SessionType** 및 **ModulesToImport** 매개 변수를 사용 하 여 세션으로 가져올 모듈을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-240">Use the **SessionType** and **ModulesToImport** parameters to determine which modules are imported into the session.</span></span>

<span data-ttu-id="f9fad-241">**표시** 되는 매개 변수가 세션 구성 파일에 포함 된 경우 PowerShell은 `Import-Module` 세션에서 cmdlet 및 해당 별칭을 제거 합니다 `ipmo` .</span><span class="sxs-lookup"><span data-stu-id="f9fad-241">When any **Visible** parameter is included in the session configuration file, PowerShell removes the `Import-Module` cmdlet and its `ipmo` alias from the session.</span></span>

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

### <span data-ttu-id="f9fad-242">-VisibleProviders</span><span class="sxs-lookup"><span data-stu-id="f9fad-242">-VisibleProviders</span></span>

<span data-ttu-id="f9fad-243">세션의 PowerShell 공급자를이 매개 변수 값에 지정 된 공급자로 제한 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-243">Limits the PowerShell providers in the session to those specified in the value of this parameter.</span></span>
<span data-ttu-id="f9fad-244">와일드카드 문자가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-244">Wildcard characters are supported.</span></span>

<span data-ttu-id="f9fad-245">기본적으로 세션의 모듈에서 내보낸 모든 공급자가 세션에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-245">By default, all providers exported by a module in the session are visible in the session.</span></span> <span data-ttu-id="f9fad-246">**SessionType** 및 **ModulesToImport** 매개 변수를 사용 하 여 세션으로 가져올 모듈을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9fad-246">Use the **SessionType** and **ModulesToImport** parameters to determine which modules are imported into the session.</span></span>

<span data-ttu-id="f9fad-247">**표시** 되는 매개 변수가 세션 구성 파일에 포함 된 경우 PowerShell은 `Import-Module` 세션에서 cmdlet 및 해당 별칭을 제거 합니다 `ipmo` .</span><span class="sxs-lookup"><span data-stu-id="f9fad-247">When any **Visible** parameter is included in the session configuration file, PowerShell removes the `Import-Module` cmdlet and its `ipmo` alias from the session.</span></span>

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

### <span data-ttu-id="f9fad-248">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f9fad-248">CommonParameters</span></span>

<span data-ttu-id="f9fad-249">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f9fad-249">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f9fad-250">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f9fad-250">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f9fad-251">입력</span><span class="sxs-lookup"><span data-stu-id="f9fad-251">INPUTS</span></span>

## <span data-ttu-id="f9fad-252">출력</span><span class="sxs-lookup"><span data-stu-id="f9fad-252">OUTPUTS</span></span>

## <span data-ttu-id="f9fad-253">참고</span><span class="sxs-lookup"><span data-stu-id="f9fad-253">NOTES</span></span>

## <span data-ttu-id="f9fad-254">관련 링크</span><span class="sxs-lookup"><span data-stu-id="f9fad-254">RELATED LINKS</span></span>

[<span data-ttu-id="f9fad-255">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="f9fad-255">New-PSSessionConfigurationFile</span></span>](New-PSSessionConfigurationFile.md)

[<span data-ttu-id="f9fad-256">Get-PSSessionCapability</span><span class="sxs-lookup"><span data-stu-id="f9fad-256">Get-PSSessionCapability</span></span>](Get-PSSessionCapability.md)
