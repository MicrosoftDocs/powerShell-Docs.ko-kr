---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 02/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-location?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Location
ms.openlocfilehash: 06b1596366c9c9e20857b55aa9a17342bab07028
ms.sourcegitcommit: fe1e20f8523e3663d68546093aaf3670182337b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/14/2020
ms.locfileid: "93219553"
---
# <span data-ttu-id="73573-103">Set-Location</span><span class="sxs-lookup"><span data-stu-id="73573-103">Set-Location</span></span>

## <span data-ttu-id="73573-104">개요</span><span class="sxs-lookup"><span data-stu-id="73573-104">SYNOPSIS</span></span>
<span data-ttu-id="73573-105">현재 작업 위치를 지정된 위치로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="73573-105">Sets the current working location to a specified location.</span></span>

## <span data-ttu-id="73573-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="73573-106">SYNTAX</span></span>

### <span data-ttu-id="73573-107">Path (기본값)</span><span class="sxs-lookup"><span data-stu-id="73573-107">Path (Default)</span></span>

```
Set-Location [[-Path] <String>] [-PassThru] [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="73573-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="73573-108">LiteralPath</span></span>

```
Set-Location -LiteralPath <String> [-PassThru] [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="73573-109">스택</span><span class="sxs-lookup"><span data-stu-id="73573-109">Stack</span></span>

```
Set-Location [-PassThru] [-StackName <String>] [-UseTransaction] [<CommonParameters>]
```

## <span data-ttu-id="73573-110">설명</span><span class="sxs-lookup"><span data-stu-id="73573-110">DESCRIPTION</span></span>

<span data-ttu-id="73573-111">`Set-Location`Cmdlet은 작업 위치를 지정 된 위치로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="73573-111">The `Set-Location` cmdlet sets the working location to a specified location.</span></span> <span data-ttu-id="73573-112">해당 위치는 디렉터리, 하위 디렉터리, 레지스트리 위치 또는 공급자 경로일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73573-112">That location could be a directory, a subdirectory, a registry location, or any provider path.</span></span>

<span data-ttu-id="73573-113">**Stackname** 매개 변수를 사용 하 여 명명 된 위치 스택을 현재 위치 스택으로 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73573-113">You can also use the **StackName** parameter to make a named location stack the current location stack.</span></span> <span data-ttu-id="73573-114">위치 스택에 대한 자세한 내용은 참고를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="73573-114">For more information about location stacks, see the Notes.</span></span>

## <span data-ttu-id="73573-115">예제</span><span class="sxs-lookup"><span data-stu-id="73573-115">EXAMPLES</span></span>

### <span data-ttu-id="73573-116">예제 1: 현재 위치 설정</span><span class="sxs-lookup"><span data-stu-id="73573-116">Example 1: Set the current location</span></span>

```powershell
PS C:\> Set-Location -Path "HKLM:\"
```

```output
PS HKLM:\>
```

<span data-ttu-id="73573-117">이 명령은 현재 위치를 드라이브의 루트로 설정 합니다 `HKLM:` .</span><span class="sxs-lookup"><span data-stu-id="73573-117">This command sets the current location to the root of the `HKLM:` drive.</span></span>

### <span data-ttu-id="73573-118">예 2: 현재 위치를 설정 하 고 해당 위치를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="73573-118">Example 2: Set the current location and display that location</span></span>

```powershell
PS C:\> Set-Location -Path "Env:\" -PassThru
```

```output
Path
----
Env:\

PS Env:\>
```

<span data-ttu-id="73573-119">이 명령은 현재 위치를 드라이브의 루트로 설정 합니다 `Env:` .</span><span class="sxs-lookup"><span data-stu-id="73573-119">This command sets the current location to the root of the `Env:` drive.</span></span> <span data-ttu-id="73573-120">**PassThru** 매개 변수를 사용 하 여 PowerShell에서 위치를 나타내는 **pathinfo** 개체를 반환 하도록 지시 합니다 `Env:\` .</span><span class="sxs-lookup"><span data-stu-id="73573-120">It uses the **PassThru** parameter to direct PowerShell to return a **PathInfo** object that represents the `Env:\` location.</span></span>

### <span data-ttu-id="73573-121">예 3: 위치를 C: 드라이브의 현재 위치로 설정</span><span class="sxs-lookup"><span data-stu-id="73573-121">Example 3: Set location to the current location in the C: drive</span></span>

```powershell
PS C:\Windows\> Set-Location HKLM:\
PS HKLM:\> Set-Location C:
PS C:\Windows\>
```

<span data-ttu-id="73573-122">첫 번째 명령은 `HKLM:` 레지스트리 공급자에 있는 드라이브의 루트로 위치를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="73573-122">The first command sets the location to the root of the `HKLM:` drive in the Registry provider.</span></span>
<span data-ttu-id="73573-123">두 번째 명령은 `C:` 파일 시스템 공급자에서 드라이브의 현재 위치로 위치를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="73573-123">The second command sets the location to the current location of the `C:` drive in the FileSystem provider.</span></span>
<span data-ttu-id="73573-124">드라이브 이름이 백슬래시 없이 형식으로 지정 된 경우 `<DriveName>:` cmdlet은 PSDrive의 현재 위치로 위치를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="73573-124">When the drive name is specified in the form `<DriveName>:` (without backslash), the cmdlet sets the location to the current location in the PSDrive.</span></span>
<span data-ttu-id="73573-125">PSDrive use 명령에서 현재 위치를 가져옵니다 `Get-Location -PSDrive <DriveName>` .</span><span class="sxs-lookup"><span data-stu-id="73573-125">To get the current location in the PSDrive use `Get-Location -PSDrive <DriveName>` command.</span></span>

### <span data-ttu-id="73573-126">예제 4: 현재 위치를 명명 된 스택으로 설정</span><span class="sxs-lookup"><span data-stu-id="73573-126">Example 4: Set the current location to a named stack</span></span>

```powershell
PS C:\> Push-Location -Path 'C:\Program Files\PowerShell\' -StackName "Paths"
PS C:\Program Files\PowerShell\> Set-Location -StackName "Paths"
PS C:\Program Files\PowerShell\> Get-Location -Stack
```

```Output
Path
----
C:\
```

<span data-ttu-id="73573-127">첫 번째 명령은 현재 위치를 경로 스택에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="73573-127">The first command adds the current location to the Paths stack.</span></span>
<span data-ttu-id="73573-128">두 번째 명령은 경로 위치 스택을 현재 위치 스택으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="73573-128">The second command makes the Paths location stack the current location stack.</span></span>
<span data-ttu-id="73573-129">세 번째 명령은 현재 위치 스택의 위치를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="73573-129">The third command displays the locations in the current location stack.</span></span>

<span data-ttu-id="73573-130">`*-Location`명령에 다른 위치 스택이 지정 되지 않은 경우 cmdlet은 현재 위치 스택을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="73573-130">The `*-Location` cmdlets use the current location stack unless a different location stack is specified in the command.</span></span> <span data-ttu-id="73573-131">위치 스택에 대 한 자세한 [내용은 참고를 참조 하세요.](#notes)</span><span class="sxs-lookup"><span data-stu-id="73573-131">For information about location stacks, see the [Notes](#notes).</span></span>

## <span data-ttu-id="73573-132">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="73573-132">PARAMETERS</span></span>

### <span data-ttu-id="73573-133">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="73573-133">-LiteralPath</span></span>

<span data-ttu-id="73573-134">위치의 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="73573-134">Specifies a path of the location.</span></span> <span data-ttu-id="73573-135">**LiteralPath** 매개 변수 값은 입력 한 대로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="73573-135">The value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="73573-136">어떠한 문자도 와일드카드 문자로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="73573-136">No characters are interpreted as wildcard characters.</span></span> <span data-ttu-id="73573-137">이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요.</span><span class="sxs-lookup"><span data-stu-id="73573-137">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="73573-138">작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="73573-138">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="73573-139">작은따옴표는 Windows PowerShell이 어떤 문자도 이스케이프 시퀀스로 해석하지 않도록 지시합니다.</span><span class="sxs-lookup"><span data-stu-id="73573-139">Single quotation marks tell Windows PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="73573-140">-PassThru</span><span class="sxs-lookup"><span data-stu-id="73573-140">-PassThru</span></span>

<span data-ttu-id="73573-141">위치를 나타내는 **Pathinfo** 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="73573-141">Returns a **PathInfo** object that represents the location.</span></span> <span data-ttu-id="73573-142">기본적으로 이 cmdlet은 출력을 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="73573-142">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="73573-143">-Path</span><span class="sxs-lookup"><span data-stu-id="73573-143">-Path</span></span>

<span data-ttu-id="73573-144">새 작업 위치의 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="73573-144">Specify the path of a new working location.</span></span> <span data-ttu-id="73573-145">경로를 제공 하지 않으면 기본적으로 `Set-Location` 현재 사용자의 홈 디렉터리를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="73573-145">If no path is provided, `Set-Location` defaults to the current user's home directory.</span></span> <span data-ttu-id="73573-146">와일드 카드를 사용 하는 경우 cmdlet은 와일드 카드 패턴과 일치 하는 첫 번째 경로를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="73573-146">When wildcards are used, the cmdlet chooses the first path that matches the wildcard pattern.</span></span>

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

### <span data-ttu-id="73573-147">-StackName</span><span class="sxs-lookup"><span data-stu-id="73573-147">-StackName</span></span>

<span data-ttu-id="73573-148">이 cmdlet이 현재 위치 스택을 만드는 기존 위치 스택 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="73573-148">Specifies the existing location stack name that this cmdlet makes the current location stack.</span></span> <span data-ttu-id="73573-149">위치 스택 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="73573-149">Enter a location stack name.</span></span> <span data-ttu-id="73573-150">이름 없는 기본 위치 스택을 나타내려면 `$null` 또는 빈 문자열 ()을 입력 `""` 합니다.</span><span class="sxs-lookup"><span data-stu-id="73573-150">To indicate the unnamed default location stack, type `$null` or an empty string (`""`).</span></span>

<span data-ttu-id="73573-151">`*-Location` **Stackname** 매개 변수를 사용 하 여 다른 스택을 지정 하지 않는 한 cmdlet은 현재 스택에서 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="73573-151">The `*-Location` cmdlets act on the current stack unless you use the **StackName** parameter to specify a different stack.</span></span>

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

### <span data-ttu-id="73573-152">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="73573-152">-UseTransaction</span></span>

<span data-ttu-id="73573-153">활성 트랜잭션에 명령을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="73573-153">Includes the command in the active transaction.</span></span>
<span data-ttu-id="73573-154">이 매개 변수는 트랜잭션이 진행 중인 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73573-154">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="73573-155">자세한 내용은 about_Transactions를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="73573-155">For more information, see about_Transactions.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: usetx

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="73573-156">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="73573-156">CommonParameters</span></span>

<span data-ttu-id="73573-157">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="73573-157">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="73573-158">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="73573-158">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="73573-159">입력</span><span class="sxs-lookup"><span data-stu-id="73573-159">INPUTS</span></span>

### <span data-ttu-id="73573-160">System.String</span><span class="sxs-lookup"><span data-stu-id="73573-160">System.String</span></span>

<span data-ttu-id="73573-161">경로를 포함 하지만 리터럴 경로를 포함 하지 않는 문자열을이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73573-161">You can pipe a string that contains a path, but not a literal path, to this cmdlet.</span></span>

## <span data-ttu-id="73573-162">출력</span><span class="sxs-lookup"><span data-stu-id="73573-162">OUTPUTS</span></span>

### <span data-ttu-id="73573-163">None, System.web. PathInfo, System.web. PathInfoStack</span><span class="sxs-lookup"><span data-stu-id="73573-163">None, System.Management.Automation.PathInfo, System.Management.Automation.PathInfoStack</span></span>

<span data-ttu-id="73573-164">**PassThru** 매개 변수를 지정 하지 않으면이 cmdlet은 출력을 생성 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="73573-164">This cmdlet does not generate any output unless you specify the **PassThru** parameter.</span></span> <span data-ttu-id="73573-165">**PassThru** 와 **Path** 또는 **LiteralPath** 를 함께 사용 하면 새 위치를 나타내는 **pathinfo** 개체가 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="73573-165">Using **PassThru** with **Path** or **LiteralPath** generates a **PathInfo** object that represents the new location.</span></span> <span data-ttu-id="73573-166">**Stackname** 과 함께 **PassThru** 를 사용 하면 새 스택 컨텍스트를 나타내는 **pathinfostack** 개체가 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="73573-166">Using **PassThru** with **StackName** generates a **PathInfoStack** object representing the new stack context.</span></span>

## <span data-ttu-id="73573-167">참고</span><span class="sxs-lookup"><span data-stu-id="73573-167">NOTES</span></span>

<span data-ttu-id="73573-168">PowerShell은 프로세스 당 여러 runspace를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="73573-168">PowerShell supports multiple runspaces per process.</span></span> <span data-ttu-id="73573-169">각 runspace에는 자체의 _현재 디렉터리가_ 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73573-169">Each runspace has its own _current directory_.</span></span>
<span data-ttu-id="73573-170">와는 다릅니다 `[System.Environment]::CurrentDirectory` .</span><span class="sxs-lookup"><span data-stu-id="73573-170">This is not the same as `[System.Environment]::CurrentDirectory`.</span></span> <span data-ttu-id="73573-171">이 동작은 명시적 디렉터리 경로를 제공 하지 않고 .NET Api를 호출 하거나 네이티브 응용 프로그램을 실행할 때 문제가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73573-171">This behavior can be an issue when calling .NET APIs or running native applications without providing explicit directory paths.</span></span>

<span data-ttu-id="73573-172">Location cmdlet이 프로세스 차원의 현재 디렉터리를 설정 했더라도 다른 runspace가 언제 든 지 변경 될 수 있으므로이를 종속 시킬 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="73573-172">Even if the location cmdlets did set the process-wide current directory, you can't depend on it because another runspace might change it at any time.</span></span> <span data-ttu-id="73573-173">현재 runspace와 관련 된 현재 작업 디렉터리를 사용 하 여 경로 기반 작업을 수행 하려면 location cmdlet을 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="73573-173">You should use the location cmdlets to perform path-based operations using the current working directory specific to the current runspace.</span></span>

<span data-ttu-id="73573-174">`Set-Location`Cmdlet은 모든 공급자가 제공 하는 데이터에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73573-174">The `Set-Location` cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="73573-175">세션에서 사용할 수 있는 공급자를 나열 하려면을 입력 `Get-PSProvider` 합니다.</span><span class="sxs-lookup"><span data-stu-id="73573-175">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="73573-176">자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/about/about_Providers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="73573-176">For more information, see [about_Providers](../Microsoft.PowerShell.Core/about/about_Providers.md).</span></span>

<span data-ttu-id="73573-177">스택은 가장 최근에 추가한 항목만 액세스할 수 있는 마지막으로 시작 된 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="73573-177">A stack is a last-in, first-out list in which only the most recently added item can be accessed.</span></span> <span data-ttu-id="73573-178">사용하는 순서대로 스택에 항목을 추가한 다음 사용을 위해 역순으로 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="73573-178">You add items to a stack in the order that you use them, and then retrieve them for use in the reverse order.</span></span> <span data-ttu-id="73573-179">PowerShell을 사용 하 여 공급자 위치를 위치 스택에 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73573-179">PowerShell lets you store provider locations in location stacks.</span></span> <span data-ttu-id="73573-180">PowerShell은 이름 없는 기본 위치 스택을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="73573-180">PowerShell creates an unnamed default location stack.</span></span> <span data-ttu-id="73573-181">명명 된 위치 스택을 여러 개 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73573-181">You can create multiple named location stacks.</span></span> <span data-ttu-id="73573-182">스택 이름을 지정 하지 않으면 PowerShell은 현재 위치 스택을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="73573-182">If you do not specify a stack name, PowerShell uses the current location stack.</span></span> <span data-ttu-id="73573-183">기본적으로 이름 없는 기본 위치는 현재 위치 스택입니다. 하지만 cmdlet을 사용 `Set-Location` 하 여 현재 위치 스택을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73573-183">By default, the unnamed default location is the current location stack, but you can use the `Set-Location` cmdlet to change the current location stack.</span></span>

<span data-ttu-id="73573-184">위치 스택을 관리 하려면 다음과 `*-Location` 같이 cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="73573-184">To manage location stacks, use the `*-Location` cmdlets, as follows:</span></span>

- <span data-ttu-id="73573-185">위치 스택에 위치를 추가 하려면 cmdlet을 사용 `Push-Location` 합니다.</span><span class="sxs-lookup"><span data-stu-id="73573-185">To add a location to a location stack, use the `Push-Location` cmdlet.</span></span>

- <span data-ttu-id="73573-186">위치 스택에서 위치를 가져오려면 cmdlet을 사용 `Pop-Location` 합니다.</span><span class="sxs-lookup"><span data-stu-id="73573-186">To get a location from a location stack, use the `Pop-Location` cmdlet.</span></span>

- <span data-ttu-id="73573-187">현재 위치 스택의 위치를 표시 하려면 cmdlet의 **stack** 매개 변수를 사용 합니다 `Get-Location` .</span><span class="sxs-lookup"><span data-stu-id="73573-187">To display the locations in the current location stack, use the **Stack** parameter of the `Get-Location` cmdlet.</span></span> <span data-ttu-id="73573-188">명명 된 위치 스택의 위치를 표시 하려면의 **Stackname** 매개 변수를 사용 `Get-Location` 합니다.</span><span class="sxs-lookup"><span data-stu-id="73573-188">To display the locations in a named location stack, use the **StackName** parameter of `Get-Location`.</span></span>

- <span data-ttu-id="73573-189">새 위치 스택을 만들려면의 **Stackname** 매개 변수를 사용 `Push-Location` 합니다.</span><span class="sxs-lookup"><span data-stu-id="73573-189">To create a new location stack, use the **StackName** parameter of `Push-Location`.</span></span> <span data-ttu-id="73573-190">존재 하지 않는 스택을 지정 하면에서 `Push-Location` 스택을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="73573-190">If you specify a stack that does not exist, `Push-Location` creates the stack.</span></span>

- <span data-ttu-id="73573-191">위치 스택을 현재 위치 스택으로 설정 하려면의 **Stackname** 매개 변수를 사용 `Set-Location` 합니다.</span><span class="sxs-lookup"><span data-stu-id="73573-191">To make a location stack the current location stack, use the **StackName** parameter of `Set-Location`.</span></span>

<span data-ttu-id="73573-192">이름 없는 기본 위치 스택은 현재 위치 스택인 경우에만 완전히 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73573-192">The unnamed default location stack is fully accessible only when it is the current location stack.</span></span>
<span data-ttu-id="73573-193">명명 된 위치 스택을 현재 위치 스택으로 만들면 `Push-Location` 또는 cmdlet을 사용 `Pop-Location` 하 여 기본 스택에서 항목을 추가 하거나 가져올 수 없으며 cmdlet을 사용 하 여 `Get-Location` 명명 되지 않은 스택의 위치를 표시할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="73573-193">If you make a named location stack the current location stack, you can no longer use the `Push-Location` or `Pop-Location` cmdlets to add or get items from the default stack or use the `Get-Location` cmdlet to display the locations in the unnamed stack.</span></span> <span data-ttu-id="73573-194">명명 되지 않은 스택을 현재 스택으로 만들려면 cmdlet의 **Stackname** 매개 변수를 `Set-Location` 값 `$null` 이나 빈 문자열 ()로 사용 `""` 합니다.</span><span class="sxs-lookup"><span data-stu-id="73573-194">To make the unnamed stack the current stack, use the **StackName** parameter of the `Set-Location` cmdlet with a value of `$null` or an empty string (`""`).</span></span>

## <span data-ttu-id="73573-195">관련 링크</span><span class="sxs-lookup"><span data-stu-id="73573-195">RELATED LINKS</span></span>

[<span data-ttu-id="73573-196">Get-Location</span><span class="sxs-lookup"><span data-stu-id="73573-196">Get-Location</span></span>](Get-Location.md)

[<span data-ttu-id="73573-197">Pop-Location</span><span class="sxs-lookup"><span data-stu-id="73573-197">Pop-Location</span></span>](Pop-Location.md)

[<span data-ttu-id="73573-198">Push-Location</span><span class="sxs-lookup"><span data-stu-id="73573-198">Push-Location</span></span>](Push-Location.md)
