---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 02/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-location?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Location
ms.openlocfilehash: e1432a8ae6826e7f2c47f35c9cc01df20edde85c
ms.sourcegitcommit: fe1e20f8523e3663d68546093aaf3670182337b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/14/2020
ms.locfileid: "93219561"
---
# <span data-ttu-id="19501-103">Set-Location</span><span class="sxs-lookup"><span data-stu-id="19501-103">Set-Location</span></span>

## <span data-ttu-id="19501-104">개요</span><span class="sxs-lookup"><span data-stu-id="19501-104">SYNOPSIS</span></span>
<span data-ttu-id="19501-105">현재 작업 위치를 지정된 위치로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="19501-105">Sets the current working location to a specified location.</span></span>

## <span data-ttu-id="19501-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="19501-106">SYNTAX</span></span>

### <span data-ttu-id="19501-107">Path (기본값)</span><span class="sxs-lookup"><span data-stu-id="19501-107">Path (Default)</span></span>

```
Set-Location [[-Path] <String>] [-PassThru] [<CommonParameters>]
```

### <span data-ttu-id="19501-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="19501-108">LiteralPath</span></span>

```
Set-Location -LiteralPath <String> [-PassThru] [<CommonParameters>]
```

### <span data-ttu-id="19501-109">스택</span><span class="sxs-lookup"><span data-stu-id="19501-109">Stack</span></span>

```
Set-Location [-PassThru] [-StackName <String>] [<CommonParameters>]
```

## <span data-ttu-id="19501-110">설명</span><span class="sxs-lookup"><span data-stu-id="19501-110">DESCRIPTION</span></span>

<span data-ttu-id="19501-111">`Set-Location`Cmdlet은 작업 위치를 지정 된 위치로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="19501-111">The `Set-Location` cmdlet sets the working location to a specified location.</span></span> <span data-ttu-id="19501-112">해당 위치는 디렉터리, 하위 디렉터리, 레지스트리 위치 또는 공급자 경로일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19501-112">That location could be a directory, a subdirectory, a registry location, or any provider path.</span></span>

<span data-ttu-id="19501-113">PowerShell 6.2 `-` `+` 은 **Path** 매개 변수의 값으로 및에 대 한 지원을 추가 했습니다.</span><span class="sxs-lookup"><span data-stu-id="19501-113">PowerShell 6.2 added support for `-` and `+` as a values for the **Path** parameter.</span></span> <span data-ttu-id="19501-114">PowerShell은 및를 사용 하 여 액세스할 수 있는 최근 20 개 위치의 기록을 유지 관리 `-` `+` 합니다.</span><span class="sxs-lookup"><span data-stu-id="19501-114">PowerShell maintains a history of the last 20 locations that can be accessed with `-` and `+`.</span></span> <span data-ttu-id="19501-115">이 목록은 **Stackname** 매개 변수를 사용 하 여 액세스 하는 위치 스택과는 독립적입니다.</span><span class="sxs-lookup"><span data-stu-id="19501-115">This list is independent from the location stack that is accessed using the **StackName** parameter.</span></span>

## <span data-ttu-id="19501-116">예제</span><span class="sxs-lookup"><span data-stu-id="19501-116">EXAMPLES</span></span>

### <span data-ttu-id="19501-117">예제 1: 현재 위치 설정</span><span class="sxs-lookup"><span data-stu-id="19501-117">Example 1: Set the current location</span></span>

```
PS C:\> Set-Location -Path "HKLM:\"
PS HKLM:\>
```

<span data-ttu-id="19501-118">이 명령은 현재 위치를 드라이브의 루트로 설정 합니다 `HKLM:` .</span><span class="sxs-lookup"><span data-stu-id="19501-118">This command sets the current location to the root of the `HKLM:` drive.</span></span>

### <span data-ttu-id="19501-119">예 2: 현재 위치를 설정 하 고 해당 위치를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="19501-119">Example 2: Set the current location and display that location</span></span>

```
PS C:\> Set-Location -Path "Env:\" -PassThru
```

```Output
Path
----
Env:\

PS Env:\>
```

<span data-ttu-id="19501-120">이 명령은 현재 위치를 드라이브의 루트로 설정 합니다 `Env:` .</span><span class="sxs-lookup"><span data-stu-id="19501-120">This command sets the current location to the root of the `Env:` drive.</span></span> <span data-ttu-id="19501-121">**PassThru** 매개 변수를 사용 하 여 PowerShell에서 위치를 나타내는 **pathinfo** 개체를 반환 하도록 지시 합니다 `Env:\` .</span><span class="sxs-lookup"><span data-stu-id="19501-121">It uses the **PassThru** parameter to direct PowerShell to return a **PathInfo** object that represents the `Env:\` location.</span></span>

### <span data-ttu-id="19501-122">예 3: 위치를 C: 드라이브의 현재 위치로 설정</span><span class="sxs-lookup"><span data-stu-id="19501-122">Example 3: Set location to the current location in the C: drive</span></span>

```powershell
PS C:\Windows\> Set-Location HKLM:\
PS HKLM:\> Set-Location C:
PS C:\Windows\>
```

<span data-ttu-id="19501-123">첫 번째 명령은 `HKLM:` 레지스트리 공급자에 있는 드라이브의 루트로 위치를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="19501-123">The first command sets the location to the root of the `HKLM:` drive in the Registry provider.</span></span>
<span data-ttu-id="19501-124">두 번째 명령은 `C:` 파일 시스템 공급자에서 드라이브의 현재 위치로 위치를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="19501-124">The second command sets the location to the current location of the `C:` drive in the FileSystem provider.</span></span>
<span data-ttu-id="19501-125">드라이브 이름이 백슬래시 없이 형식으로 지정 된 경우 `<DriveName>:` cmdlet은 PSDrive의 현재 위치로 위치를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="19501-125">When the drive name is specified in the form `<DriveName>:` (without backslash), the cmdlet sets the location to the current location in the PSDrive.</span></span>
<span data-ttu-id="19501-126">PSDrive use 명령에서 현재 위치를 가져옵니다 `Get-Location -PSDrive <DriveName>` .</span><span class="sxs-lookup"><span data-stu-id="19501-126">To get the current location in the PSDrive use `Get-Location -PSDrive <DriveName>` command.</span></span>

### <span data-ttu-id="19501-127">예제 4: 현재 위치를 명명 된 스택으로 설정</span><span class="sxs-lookup"><span data-stu-id="19501-127">Example 4: Set the current location to a named stack</span></span>

```
PS C:\> Push-Location -Path 'C:\Program Files\PowerShell\' -StackName "Paths"
PS C:\Program Files\PowerShell\> Set-Location -StackName "Paths"
PS C:\Program Files\PowerShell\> Get-Location -Stack
```

```Output
Path
----
C:\
```

<span data-ttu-id="19501-128">첫 번째 명령은 현재 위치를 경로 스택에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="19501-128">The first command adds the current location to the Paths stack.</span></span>
<span data-ttu-id="19501-129">두 번째 명령은 경로 위치 스택을 현재 위치 스택으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="19501-129">The second command makes the Paths location stack the current location stack.</span></span>
<span data-ttu-id="19501-130">세 번째 명령은 현재 위치 스택의 위치를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="19501-130">The third command displays the locations in the current location stack.</span></span>

<span data-ttu-id="19501-131">`*-Location`명령에 다른 위치 스택이 지정 되지 않은 경우 cmdlet은 현재 위치 스택을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="19501-131">The `*-Location` cmdlets use the current location stack unless a different location stack is specified in the command.</span></span> <span data-ttu-id="19501-132">위치 스택에 대 한 자세한 [내용은 참고를 참조 하세요.](#notes)</span><span class="sxs-lookup"><span data-stu-id="19501-132">For information about location stacks, see the [Notes](#notes).</span></span>

### <span data-ttu-id="19501-133">예 5: 또는를 사용 하 여 위치 기록 탐색 `+``-`</span><span class="sxs-lookup"><span data-stu-id="19501-133">Example 5: Navigate location history using `+` or `-`</span></span>

```
PS C:\> Set-Location -Path $env:SystemRoot
PS C:\Windows> Set-Location -Path Cert:\
PS Cert:\> Set-Location -Path HKLM:\
PS HKLM:\>

# Navigate back through the history using "-"
PS HKLM:\> Set-Location -Path -
PS Cert:\> Set-Location -Path -
PS C:\Windows>

# Navigate using the Set-Location alias "cd" and the implicit positional Path parameter
PS C:\Windows> cd -
PS C:\> cd +
PS C:\Windows> cd +
PS Cert:\>
```

<span data-ttu-id="19501-134">별칭을 사용 하 여 `cd -` 또는 `cd +` 터미널에서 위치 기록을 탐색 하는 쉬운 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="19501-134">Using the alias, `cd -` or `cd +` is an easy way to navigate through your location history while in your terminal.</span></span> <span data-ttu-id="19501-135">로 이동 하는 방법에 대 한 자세한 내용은 `-` / `+` **Path** 매개 변수를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="19501-135">For more information on navigating with `-`/`+`, see the **Path** parameter.</span></span>

## <span data-ttu-id="19501-136">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="19501-136">PARAMETERS</span></span>

### <span data-ttu-id="19501-137">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="19501-137">-LiteralPath</span></span>

<span data-ttu-id="19501-138">위치의 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="19501-138">Specifies a path of the location.</span></span> <span data-ttu-id="19501-139">**LiteralPath** 매개 변수 값은 입력 한 대로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="19501-139">The value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="19501-140">어떠한 문자도 와일드카드 문자로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="19501-140">No characters are interpreted as wildcard characters.</span></span> <span data-ttu-id="19501-141">이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요.</span><span class="sxs-lookup"><span data-stu-id="19501-141">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="19501-142">작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="19501-142">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="19501-143">-PassThru</span><span class="sxs-lookup"><span data-stu-id="19501-143">-PassThru</span></span>

<span data-ttu-id="19501-144">위치를 나타내는 **Pathinfo** 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="19501-144">Returns a **PathInfo** object that represents the location.</span></span> <span data-ttu-id="19501-145">기본적으로 이 cmdlet은 출력을 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="19501-145">By default, this cmdlet does not generate any output.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="19501-146">-Path</span><span class="sxs-lookup"><span data-stu-id="19501-146">-Path</span></span>

<span data-ttu-id="19501-147">새 작업 위치의 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="19501-147">Specify the path of a new working location.</span></span> <span data-ttu-id="19501-148">경로를 제공 하지 않으면 기본적으로 `Set-Location` 현재 사용자의 홈 디렉터리를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="19501-148">If no path is provided, `Set-Location` defaults to the current user's home directory.</span></span> <span data-ttu-id="19501-149">와일드 카드를 사용 하는 경우 cmdlet은 와일드 카드 패턴과 일치 하는 첫 번째 경로를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="19501-149">When wildcards are used, the cmdlet chooses the first path that matches the wildcard pattern.</span></span>

<span data-ttu-id="19501-150">PowerShell은 사용자가 설정한 최근 20 개 위치의 기록을 보관 합니다.</span><span class="sxs-lookup"><span data-stu-id="19501-150">PowerShell keeps a history of the last 20 locations you have set.</span></span> <span data-ttu-id="19501-151">**Path** 매개 변수 값이 문자 이면 `-` 새 작업 위치가 기록의 이전 작업 위치 (있는 경우)가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="19501-151">If the **Path** parameter value is the `-` character, then the new working location will be the previous working location in history (if it exists).</span></span> <span data-ttu-id="19501-152">마찬가지로 값이 `+` 문자인 경우 새 작업 위치가 기록의 다음 작업 위치가 됩니다 (있는 경우).</span><span class="sxs-lookup"><span data-stu-id="19501-152">Similarly, if the value is the `+` character, then the new working location will be the next working location in history (if it exists).</span></span> <span data-ttu-id="19501-153">이는 `Pop-Location` `Push-Location` 기록이 스택을 제외 하 고 암시적으로 추적 되며 수동으로 제어 되지 않는다는 점을 제외 하 고는 및를 사용 하는 것과 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="19501-153">This is similar to using `Pop-Location` and `Push-Location` except that the history is a list, not a stack, and is implicitly tracked, not manually controlled.</span></span> <span data-ttu-id="19501-154">현재 기록 목록을 볼 수 있는 방법은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="19501-154">Currently, there is no way to view the history list.</span></span>

```yaml
Type: System.String
Parameter Sets: Path
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="19501-155">-StackName</span><span class="sxs-lookup"><span data-stu-id="19501-155">-StackName</span></span>

<span data-ttu-id="19501-156">이 cmdlet이 현재 위치 스택을 만드는 기존 위치 스택 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="19501-156">Specifies the existing location stack name that this cmdlet makes the current location stack.</span></span> <span data-ttu-id="19501-157">위치 스택 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="19501-157">Enter a location stack name.</span></span> <span data-ttu-id="19501-158">이름 없는 기본 위치 스택을 나타내려면 `$null` 또는 빈 문자열 ()을 입력 `""` 합니다.</span><span class="sxs-lookup"><span data-stu-id="19501-158">To indicate the unnamed default location stack, type `$null` or an empty string (`""`).</span></span>

<span data-ttu-id="19501-159">`*-Location` **Stackname** 매개 변수를 사용 하 여 다른 스택을 지정 하지 않는 한 cmdlet은 현재 스택에서 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="19501-159">The `*-Location` cmdlets act on the current stack unless you use the **StackName** parameter to specify a different stack.</span></span> <span data-ttu-id="19501-160">위치 스택에 대 한 자세한 내용은 참고를 참조 [하세요.](#notes)</span><span class="sxs-lookup"><span data-stu-id="19501-160">For more information about location stacks, see the [Notes](#notes).</span></span>

```yaml
Type: System.String
Parameter Sets: Stack
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="19501-161">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="19501-161">CommonParameters</span></span>

<span data-ttu-id="19501-162">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="19501-162">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="19501-163">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="19501-163">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="19501-164">입력</span><span class="sxs-lookup"><span data-stu-id="19501-164">INPUTS</span></span>

### <span data-ttu-id="19501-165">System.String</span><span class="sxs-lookup"><span data-stu-id="19501-165">System.String</span></span>

<span data-ttu-id="19501-166">경로를 포함 하지만 리터럴 경로를 포함 하지 않는 문자열을이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19501-166">You can pipe a string that contains a path, but not a literal path, to this cmdlet.</span></span>

## <span data-ttu-id="19501-167">출력</span><span class="sxs-lookup"><span data-stu-id="19501-167">OUTPUTS</span></span>

### <span data-ttu-id="19501-168">None, System.web. PathInfo, System.web. PathInfoStack</span><span class="sxs-lookup"><span data-stu-id="19501-168">None, System.Management.Automation.PathInfo, System.Management.Automation.PathInfoStack</span></span>

<span data-ttu-id="19501-169">**PassThru** 매개 변수를 지정 하지 않으면이 cmdlet은 출력을 생성 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="19501-169">This cmdlet does not generate any output unless you specify the **PassThru** parameter.</span></span> <span data-ttu-id="19501-170">**PassThru** 와 **Path** 또는 **LiteralPath** 를 함께 사용 하면 새 위치를 나타내는 **pathinfo** 개체가 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="19501-170">Using **PassThru** with **Path** or **LiteralPath** generates a **PathInfo** object that represents the new location.</span></span> <span data-ttu-id="19501-171">**Stackname** 과 함께 **PassThru** 를 사용 하면 새 스택 컨텍스트를 나타내는 **pathinfostack** 개체가 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="19501-171">Using **PassThru** with **StackName** generates a **PathInfoStack** object representing the new stack context.</span></span>

## <span data-ttu-id="19501-172">참고</span><span class="sxs-lookup"><span data-stu-id="19501-172">NOTES</span></span>

<span data-ttu-id="19501-173">PowerShell은 프로세스 당 여러 runspace를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="19501-173">PowerShell supports multiple runspaces per process.</span></span> <span data-ttu-id="19501-174">각 runspace에는 자체의 _현재 디렉터리가_ 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19501-174">Each runspace has its own _current directory_.</span></span>
<span data-ttu-id="19501-175">와는 다릅니다 `[System.Environment]::CurrentDirectory` .</span><span class="sxs-lookup"><span data-stu-id="19501-175">This is not the same as `[System.Environment]::CurrentDirectory`.</span></span> <span data-ttu-id="19501-176">이 동작은 명시적 디렉터리 경로를 제공 하지 않고 .NET Api를 호출 하거나 네이티브 응용 프로그램을 실행할 때 문제가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19501-176">This behavior can be an issue when calling .NET APIs or running native applications without providing explicit directory paths.</span></span>

<span data-ttu-id="19501-177">Location cmdlet이 프로세스 차원의 현재 디렉터리를 설정 했더라도 다른 runspace가 언제 든 지 변경 될 수 있으므로이를 종속 시킬 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="19501-177">Even if the location cmdlets did set the process-wide current directory, you can't depend on it because another runspace might change it at any time.</span></span> <span data-ttu-id="19501-178">현재 runspace와 관련 된 현재 작업 디렉터리를 사용 하 여 경로 기반 작업을 수행 하려면 location cmdlet을 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="19501-178">You should use the location cmdlets to perform path-based operations using the current working directory specific to the current runspace.</span></span>

<span data-ttu-id="19501-179">`Set-Location`Cmdlet은 모든 공급자가 제공 하는 데이터에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19501-179">The `Set-Location` cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="19501-180">세션에서 사용할 수 있는 공급자를 나열 하려면을 입력 `Get-PSProvider` 합니다.</span><span class="sxs-lookup"><span data-stu-id="19501-180">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="19501-181">자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/about/about_Providers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="19501-181">For more information, see [about_Providers](../Microsoft.PowerShell.Core/about/about_Providers.md).</span></span>

<span data-ttu-id="19501-182">스택은 가장 최근에 추가한 항목만 액세스할 수 있는 마지막으로 시작 된 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="19501-182">A stack is a last-in, first-out list in which only the most recently added item can be accessed.</span></span> <span data-ttu-id="19501-183">사용하는 순서대로 스택에 항목을 추가한 다음 사용을 위해 역순으로 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="19501-183">You add items to a stack in the order that you use them, and then retrieve them for use in the reverse order.</span></span> <span data-ttu-id="19501-184">PowerShell을 사용 하 여 공급자 위치를 위치 스택에 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19501-184">PowerShell lets you store provider locations in location stacks.</span></span> <span data-ttu-id="19501-185">PowerShell은 이름 없는 기본 위치 스택을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="19501-185">PowerShell creates an unnamed default location stack.</span></span> <span data-ttu-id="19501-186">명명 된 위치 스택을 여러 개 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19501-186">You can create multiple named location stacks.</span></span> <span data-ttu-id="19501-187">스택 이름을 지정 하지 않으면 PowerShell은 현재 위치 스택을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="19501-187">If you do not specify a stack name, PowerShell uses the current location stack.</span></span> <span data-ttu-id="19501-188">기본적으로 이름 없는 기본 위치는 현재 위치 스택입니다. 하지만 cmdlet을 사용 `Set-Location` 하 여 현재 위치 스택을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19501-188">By default, the unnamed default location is the current location stack, but you can use the `Set-Location` cmdlet to change the current location stack.</span></span>

<span data-ttu-id="19501-189">위치 스택을 관리 하려면 다음과 `*-Location` 같이 cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="19501-189">To manage location stacks, use the `*-Location` cmdlets, as follows:</span></span>

- <span data-ttu-id="19501-190">위치 스택에 위치를 추가 하려면 cmdlet을 사용 `Push-Location` 합니다.</span><span class="sxs-lookup"><span data-stu-id="19501-190">To add a location to a location stack, use the `Push-Location` cmdlet.</span></span>

- <span data-ttu-id="19501-191">위치 스택에서 위치를 가져오려면 cmdlet을 사용 `Pop-Location` 합니다.</span><span class="sxs-lookup"><span data-stu-id="19501-191">To get a location from a location stack, use the `Pop-Location` cmdlet.</span></span>

- <span data-ttu-id="19501-192">현재 위치 스택의 위치를 표시 하려면 cmdlet의 **stack** 매개 변수를 사용 합니다 `Get-Location` .</span><span class="sxs-lookup"><span data-stu-id="19501-192">To display the locations in the current location stack, use the **Stack** parameter of the `Get-Location` cmdlet.</span></span> <span data-ttu-id="19501-193">명명 된 위치 스택의 위치를 표시 하려면의 **Stackname** 매개 변수를 사용 `Get-Location` 합니다.</span><span class="sxs-lookup"><span data-stu-id="19501-193">To display the locations in a named location stack, use the **StackName** parameter of `Get-Location`.</span></span>

- <span data-ttu-id="19501-194">새 위치 스택을 만들려면의 **Stackname** 매개 변수를 사용 `Push-Location` 합니다.</span><span class="sxs-lookup"><span data-stu-id="19501-194">To create a new location stack, use the **StackName** parameter of `Push-Location`.</span></span> <span data-ttu-id="19501-195">존재 하지 않는 스택을 지정 하면에서 `Push-Location` 스택을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="19501-195">If you specify a stack that does not exist, `Push-Location` creates the stack.</span></span>

- <span data-ttu-id="19501-196">위치 스택을 현재 위치 스택으로 설정 하려면의 **Stackname** 매개 변수를 사용 `Set-Location` 합니다.</span><span class="sxs-lookup"><span data-stu-id="19501-196">To make a location stack the current location stack, use the **StackName** parameter of `Set-Location`.</span></span>

<span data-ttu-id="19501-197">이름 없는 기본 위치 스택은 현재 위치 스택인 경우에만 완전히 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19501-197">The unnamed default location stack is fully accessible only when it is the current location stack.</span></span>
<span data-ttu-id="19501-198">명명 된 위치 스택을 현재 위치 스택으로 만들면 `Push-Location` 또는 cmdlet을 사용 `Pop-Location` 하 여 기본 스택에서 항목을 추가 하거나 가져올 수 없으며 cmdlet을 사용 하 여 `Get-Location` 명명 되지 않은 스택의 위치를 표시할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="19501-198">If you make a named location stack the current location stack, you can no longer use the `Push-Location` or `Pop-Location` cmdlets to add or get items from the default stack or use the `Get-Location` cmdlet to display the locations in the unnamed stack.</span></span> <span data-ttu-id="19501-199">명명 되지 않은 스택을 현재 스택으로 만들려면 cmdlet의 **Stackname** 매개 변수를 `Set-Location` 값 `$null` 이나 빈 문자열 ()로 사용 `""` 합니다.</span><span class="sxs-lookup"><span data-stu-id="19501-199">To make the unnamed stack the current stack, use the **StackName** parameter of the `Set-Location` cmdlet with a value of `$null` or an empty string (`""`).</span></span>

## <span data-ttu-id="19501-200">관련 링크</span><span class="sxs-lookup"><span data-stu-id="19501-200">RELATED LINKS</span></span>

[<span data-ttu-id="19501-201">Get-Location</span><span class="sxs-lookup"><span data-stu-id="19501-201">Get-Location</span></span>](Get-Location.md)

[<span data-ttu-id="19501-202">Pop-Location</span><span class="sxs-lookup"><span data-stu-id="19501-202">Pop-Location</span></span>](Pop-Location.md)

[<span data-ttu-id="19501-203">Push-Location</span><span class="sxs-lookup"><span data-stu-id="19501-203">Push-Location</span></span>](Push-Location.md)
