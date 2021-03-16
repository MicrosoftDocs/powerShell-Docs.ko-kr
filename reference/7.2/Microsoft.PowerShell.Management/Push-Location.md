---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 02/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/push-location?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Push-Location
ms.openlocfilehash: eaa7622e29680de4228579f8b77a6c829a586bf8
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599768"
---
# <span data-ttu-id="69861-102">Push-Location</span><span class="sxs-lookup"><span data-stu-id="69861-102">Push-Location</span></span>

## <span data-ttu-id="69861-103">개요</span><span class="sxs-lookup"><span data-stu-id="69861-103">SYNOPSIS</span></span>
<span data-ttu-id="69861-104">현재 위치를 위치 스택의 맨 위에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="69861-104">Adds the current location to the top of a location stack.</span></span>

## <span data-ttu-id="69861-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="69861-105">SYNTAX</span></span>

### <span data-ttu-id="69861-106">Path (기본값)</span><span class="sxs-lookup"><span data-stu-id="69861-106">Path (Default)</span></span>

```
Push-Location [[-Path] <String>] [-PassThru] [-StackName <String>] [<CommonParameters>]
```

### <span data-ttu-id="69861-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="69861-107">LiteralPath</span></span>

```
Push-Location [-LiteralPath <String>] [-PassThru] [-StackName <String>] [<CommonParameters>]
```

## <span data-ttu-id="69861-108">설명</span><span class="sxs-lookup"><span data-stu-id="69861-108">DESCRIPTION</span></span>

<span data-ttu-id="69861-109">`Push-Location`Cmdlet은 현재 위치를 위치 스택에 추가 ("푸시") 합니다.</span><span class="sxs-lookup"><span data-stu-id="69861-109">The `Push-Location` cmdlet adds ("pushes") the current location onto a location stack.</span></span> <span data-ttu-id="69861-110">경로를 지정 하는 경우는 현재 위치를 `Push-Location` 위치 스택에 푸시한 다음 현재 위치를 경로에 지정 된 위치로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="69861-110">If you specify a path, `Push-Location` pushes the current location onto a location stack and then changes the current location to the location specified by the path.</span></span> <span data-ttu-id="69861-111">Cmdlet을 사용 `Pop-Location` 하 여 위치 스택에서 위치를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69861-111">You can use the `Pop-Location` cmdlet to get locations from the location stack.</span></span>

<span data-ttu-id="69861-112">기본적으로이 cmdlet은 현재 위치를 `Push-Location` 현재 위치 스택에 푸시한 다음 **stackname** 매개 변수를 사용 하 여 대체 위치 스택을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69861-112">By default, the `Push-Location` cmdlet pushes the current location onto the current location stack, but you can use the **StackName** parameter to specify an alternate location stack.</span></span> <span data-ttu-id="69861-113">스택이 없으면에서 `Push-Location` 해당 스택을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="69861-113">If the stack does not exist, `Push-Location` creates it.</span></span>

<span data-ttu-id="69861-114">위치 스택에 대 한 자세한 내용은 참고를 참조 [하세요.](#notes)</span><span class="sxs-lookup"><span data-stu-id="69861-114">For more information about location stacks, see the [Notes](#notes).</span></span>

## <span data-ttu-id="69861-115">예제</span><span class="sxs-lookup"><span data-stu-id="69861-115">EXAMPLES</span></span>

### <span data-ttu-id="69861-116">예제 1</span><span class="sxs-lookup"><span data-stu-id="69861-116">Example 1</span></span>

<span data-ttu-id="69861-117">이 예제에서는 현재 위치를 기본 위치 스택에 푸시한 다음 위치를로 변경 합니다 `C:\Windows` .</span><span class="sxs-lookup"><span data-stu-id="69861-117">This example pushes the current location onto the default location stack and then changes the location to `C:\Windows`.</span></span>

```
PS C:\> Push-Location C:\Windows
```

### <span data-ttu-id="69861-118">예 2</span><span class="sxs-lookup"><span data-stu-id="69861-118">Example 2</span></span>

<span data-ttu-id="69861-119">이 예제에서는 현재 위치를 RegFunction 스택에 푸시하고 현재 위치를 `HKLM:\Software\Policies` 위치로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="69861-119">This example pushes the current location onto the RegFunction stack and changes the current location to the `HKLM:\Software\Policies` location.</span></span>

```
PS C:\> Push-Location HKLM:\Software\Policies -StackName RegFunction
```

<span data-ttu-id="69861-120">모든 PowerShell 드라이브 (PSDrive)에서 Location cmdlet을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69861-120">You can use the Location cmdlets in any PowerShell drive (PSDrive).</span></span>

### <span data-ttu-id="69861-121">예제 3</span><span class="sxs-lookup"><span data-stu-id="69861-121">Example 3</span></span>

<span data-ttu-id="69861-122">이 명령은 현재 위치를 기본 스택에 밀어 넣지만</span><span class="sxs-lookup"><span data-stu-id="69861-122">This command pushes the current location onto the default stack.</span></span> <span data-ttu-id="69861-123">위치를 변경하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="69861-123">It does not change the location.</span></span>

```
PS C:\> Push-Location
```

### <span data-ttu-id="69861-124">예제 4-명명 된 스택 만들기 및 사용</span><span class="sxs-lookup"><span data-stu-id="69861-124">Example 4 - Create and use a named stack</span></span>

<span data-ttu-id="69861-125">이 명령은 명명된 위치 스택을 만들고 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="69861-125">These commands show how to create and use a named location stack.</span></span>

```
PS C:\> Push-Location ~ -StackName Stack2
PS C:\Users\User01> Pop-Location -StackName Stack2
PS C:\>
```

<span data-ttu-id="69861-126">첫 번째 명령은 현재 위치를 Stack2 라는 새 스택으로 푸시하고, 현재 위치를 물결표 기호 ()로 표시 되는 홈 디렉터리로 변경 합니다 .이는 FileSystem 기호 ()로 표시 `~` 됩니다 .이는 FileSystem 기호 ()를 사용 하는 경우와 동일 합니다 `$HOME` `$env:USERPROFILE` .</span><span class="sxs-lookup"><span data-stu-id="69861-126">The first command pushes the current location onto a new stack named Stack2, and then changes the current location to the home directory, represented in the command by the tilde symbol (`~`), which when used on a FileSystem provider drives is equivalent to `$HOME` and `$env:USERPROFILE`.</span></span>

<span data-ttu-id="69861-127">Stack2가 세션에 아직 없는 경우에서 `Push-Location` 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="69861-127">If Stack2 does not already exist in the session, `Push-Location` creates it.</span></span> <span data-ttu-id="69861-128">두 번째 명령은 cmdlet을 사용 하 여 `Pop-Location` Stack2 stack에서 원래 위치 ()를 팝 합니다 `C:\` .</span><span class="sxs-lookup"><span data-stu-id="69861-128">The second command uses the `Pop-Location` cmdlet to pop the original location (`C:\`) from the Stack2 stack.</span></span> <span data-ttu-id="69861-129">**Stackname** 매개 변수를 사용 하지 않으면는 `Pop-Location` 명명 되지 않은 기본 스택의 위치를 팝 합니다.</span><span class="sxs-lookup"><span data-stu-id="69861-129">Without the **StackName** parameter, `Pop-Location` would pop the location from the unnamed default stack.</span></span>

<span data-ttu-id="69861-130">위치 스택에 대 한 자세한 내용은 참고를 참조 [하세요.](#notes)</span><span class="sxs-lookup"><span data-stu-id="69861-130">For more information about location stacks, see the [Notes](#notes).</span></span>

## <span data-ttu-id="69861-131">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="69861-131">PARAMETERS</span></span>

### <span data-ttu-id="69861-132">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="69861-132">-LiteralPath</span></span>

<span data-ttu-id="69861-133">새 위치의 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="69861-133">Specifies the path to the new location.</span></span> <span data-ttu-id="69861-134">**Path** 매개 변수와 달리 **LiteralPath** 매개 변수 값은 입력한 대로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="69861-134">Unlike the **Path** parameter, the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="69861-135">어떠한 문자도 와일드카드로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="69861-135">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="69861-136">이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요.</span><span class="sxs-lookup"><span data-stu-id="69861-136">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="69861-137">작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="69861-137">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="69861-138">-PassThru</span><span class="sxs-lookup"><span data-stu-id="69861-138">-PassThru</span></span>

<span data-ttu-id="69861-139">위치를 나타내는 개체를 파이프라인으로 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="69861-139">Passes an object representing the location to the pipeline.</span></span> <span data-ttu-id="69861-140">기본적으로 이 cmdlet은 출력을 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="69861-140">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="69861-141">-Path</span><span class="sxs-lookup"><span data-stu-id="69861-141">-Path</span></span>

<span data-ttu-id="69861-142">현재 위치를 스택의 맨 위에 추가한(밀어 넣은) 다음 사용자 위치를 이 경로에서 지정하는 위치로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="69861-142">Changes your location to the location specified by this path after it adds (pushes) the current location onto the top of the stack.</span></span> <span data-ttu-id="69861-143">이 cmdlet을 지원하는 공급자의 위치 경로를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="69861-143">Enter a path to any location whose provider supports this cmdlet.</span></span> <span data-ttu-id="69861-144">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="69861-144">Wildcards are permitted.</span></span> <span data-ttu-id="69861-145">매개 변수 이름은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="69861-145">The parameter name is optional.</span></span>

```yaml
Type: System.String
Parameter Sets: Path
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="69861-146">-StackName</span><span class="sxs-lookup"><span data-stu-id="69861-146">-StackName</span></span>

<span data-ttu-id="69861-147">현재 위치가 추가되는 위치 스택을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="69861-147">Specifies the location stack to which the current location is added.</span></span> <span data-ttu-id="69861-148">위치 스택 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="69861-148">Enter a location stack name.</span></span>
<span data-ttu-id="69861-149">스택이 없으면에서 `Push-Location` 해당 스택을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="69861-149">If the stack does not exist, `Push-Location` creates it.</span></span>

<span data-ttu-id="69861-150">이 매개 변수를 사용 하지 않으면 `Push-Location` 현재 위치 스택에 위치를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="69861-150">Without this parameter, `Push-Location` adds the location to the current location stack.</span></span> <span data-ttu-id="69861-151">기본적으로 현재 위치 스택은 PowerShell에서 만드는 이름 없는 기본 위치 스택입니다.</span><span class="sxs-lookup"><span data-stu-id="69861-151">By default, the current location stack is the unnamed default location stack that PowerShell creates.</span></span>
<span data-ttu-id="69861-152">위치 스택을 현재 위치 스택으로 만들려면 cmdlet의 **Stackname** 매개 변수를 사용 합니다 `Set-Location` .</span><span class="sxs-lookup"><span data-stu-id="69861-152">To make a location stack the current location stack, use the **StackName** parameter of the `Set-Location` cmdlet.</span></span> <span data-ttu-id="69861-153">위치 스택에 대 한 자세한 내용은 참고를 참조 [하세요.](#notes)</span><span class="sxs-lookup"><span data-stu-id="69861-153">For more information about location stacks, see the [Notes](#notes).</span></span>

> [!NOTE]
> <span data-ttu-id="69861-154">`Push-Location` 현재 위치 스택이 아닌 경우 이름 없는 기본 스택에 위치를 추가할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="69861-154">`Push-Location` cannot add a location to the unnamed default stack unless it is the current location stack.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Default stack
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="69861-155">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="69861-155">CommonParameters</span></span>

<span data-ttu-id="69861-156">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="69861-156">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="69861-157">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="69861-157">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="69861-158">입력</span><span class="sxs-lookup"><span data-stu-id="69861-158">INPUTS</span></span>

### <span data-ttu-id="69861-159">System.String</span><span class="sxs-lookup"><span data-stu-id="69861-159">System.String</span></span>

<span data-ttu-id="69861-160">경로 (리터럴 경로 아님)가 포함 된 문자열을로 파이프 할 수 있습니다 `Push-Location` .</span><span class="sxs-lookup"><span data-stu-id="69861-160">You can pipe a string that contains a path (but not a literal path) to `Push-Location`.</span></span>

## <span data-ttu-id="69861-161">출력</span><span class="sxs-lookup"><span data-stu-id="69861-161">OUTPUTS</span></span>

### <span data-ttu-id="69861-162">없음 또는 System.web. PathInfo</span><span class="sxs-lookup"><span data-stu-id="69861-162">None or System.Management.Automation.PathInfo</span></span>

<span data-ttu-id="69861-163">**PassThru** 매개 변수를 사용 하는 경우는 `Push-Location` 위치를 나타내는 **system.web. pathinfo** 개체를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="69861-163">When you use the **PassThru** parameter, `Push-Location` generates a **System.Management.Automation.PathInfo** object that represents the location.</span></span> <span data-ttu-id="69861-164">그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="69861-164">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="69861-165">참고</span><span class="sxs-lookup"><span data-stu-id="69861-165">NOTES</span></span>

<span data-ttu-id="69861-166">PowerShell은 프로세스 당 여러 runspace를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="69861-166">PowerShell supports multiple runspaces per process.</span></span> <span data-ttu-id="69861-167">각 runspace에는 자체의 _현재 디렉터리가_ 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69861-167">Each runspace has its own _current directory_.</span></span>
<span data-ttu-id="69861-168">와는 다릅니다 `[System.Environment]::CurrentDirectory` .</span><span class="sxs-lookup"><span data-stu-id="69861-168">This is not the same as `[System.Environment]::CurrentDirectory`.</span></span> <span data-ttu-id="69861-169">이 동작은 명시적 디렉터리 경로를 제공 하지 않고 .NET Api를 호출 하거나 네이티브 응용 프로그램을 실행할 때 문제가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69861-169">This behavior can be an issue when calling .NET APIs or running native applications without providing explicit directory paths.</span></span>

<span data-ttu-id="69861-170">Location cmdlet이 프로세스 차원의 현재 디렉터리를 설정 했더라도 다른 runspace가 언제 든 지 변경 될 수 있으므로이를 종속 시킬 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="69861-170">Even if the location cmdlets did set the process-wide current directory, you can't depend on it because another runspace might change it at any time.</span></span> <span data-ttu-id="69861-171">현재 runspace와 관련 된 현재 작업 디렉터리를 사용 하 여 경로 기반 작업을 수행 하려면 location cmdlet을 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="69861-171">You should use the location cmdlets to perform path-based operations using the current working directory specific to the current runspace.</span></span>

<span data-ttu-id="69861-172">스택은 가장 최근에 추가 된 항목만 액세스할 수 있는 마지막으로 시작 된 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="69861-172">A stack is a last-in, first-out list in which only the most recently added item is accessible.</span></span>
<span data-ttu-id="69861-173">사용하는 순서대로 스택에 항목을 추가한 다음 사용을 위해 역순으로 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="69861-173">You add items to a stack in the order that you use them, and then retrieve them for use in the reverse order.</span></span> <span data-ttu-id="69861-174">PowerShell을 사용 하 여 공급자 위치를 위치 스택에 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69861-174">PowerShell lets you store provider locations in location stacks.</span></span>

<span data-ttu-id="69861-175">PowerShell은 이름 없는 기본 위치 스택을 만들고 여러 개의 명명 된 위치 스택을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69861-175">PowerShell creates an unnamed default location stack and you can create multiple named location stacks.</span></span> <span data-ttu-id="69861-176">스택 이름을 지정 하지 않으면 PowerShell은 현재 위치 스택을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="69861-176">If you do not specify a stack name, PowerShell uses the current location stack.</span></span> <span data-ttu-id="69861-177">기본적으로 이름 없는 기본 위치는 현재 위치 스택입니다. 하지만 cmdlet을 사용 `Set-Location` 하 여 현재 위치 스택을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69861-177">By default, the unnamed default location is the current location stack, but you can use the `Set-Location` cmdlet to change the current location stack.</span></span>

<span data-ttu-id="69861-178">위치 스택을 관리 하려면 다음과 같이 PowerShell 위치 cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="69861-178">To manage location stacks, use the PowerShell Location cmdlets, as follows.</span></span>

- <span data-ttu-id="69861-179">위치 스택에 위치를 추가 하려면 cmdlet을 사용 `Push-Location` 합니다.</span><span class="sxs-lookup"><span data-stu-id="69861-179">To add a location to a location stack, use the `Push-Location` cmdlet.</span></span>

- <span data-ttu-id="69861-180">위치 스택에서 위치를 가져오려면 cmdlet을 사용 `Pop-Location` 합니다.</span><span class="sxs-lookup"><span data-stu-id="69861-180">To get a location from a location stack, use the `Pop-Location` cmdlet.</span></span>

- <span data-ttu-id="69861-181">현재 위치 스택의 위치를 표시 하려면 cmdlet의 **stack** 매개 변수를 사용 합니다 `Get-Location` .</span><span class="sxs-lookup"><span data-stu-id="69861-181">To display the locations in the current location stack, use the **Stack** parameter of the `Get-Location` cmdlet.</span></span>

- <span data-ttu-id="69861-182">명명 된 위치 스택의 위치를 표시 하려면 cmdlet의 **Stackname** 매개 변수를 사용 합니다 `Get-Location` .</span><span class="sxs-lookup"><span data-stu-id="69861-182">To display the locations in a named location stack, use the **StackName** parameter of the `Get-Location` cmdlet.</span></span>

- <span data-ttu-id="69861-183">새 위치 스택을 만들려면 cmdlet의 StackName 매개 변수를 사용 `Push-Location` 합니다.</span><span class="sxs-lookup"><span data-stu-id="69861-183">To create a new location stack, use the StackName parameter of the `Push-Location` cmdlet.</span></span> <span data-ttu-id="69861-184">존재 하지 않는 스택을 지정 하면에서 `Push-Location` 스택을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="69861-184">If you specify a stack that does not exist, `Push-Location` creates the stack.</span></span>

- <span data-ttu-id="69861-185">위치 스택을 현재 위치 스택으로 만들려면 cmdlet의 StackName 매개 변수를 사용 합니다 `Set-Location` .</span><span class="sxs-lookup"><span data-stu-id="69861-185">To make a location stack the current location stack, use the StackName parameter of the `Set-Location` cmdlet.</span></span>

<span data-ttu-id="69861-186">이름 없는 기본 위치 스택은 현재 위치 스택인 경우에만 완전히 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69861-186">The unnamed default location stack is fully accessible only when it is the current location stack.</span></span>
<span data-ttu-id="69861-187">명명 된 위치 스택을 현재 위치 스택으로 만들면 `Push-Location` 또는 cmdlet을 사용 `Pop-Location` 하 여 기본 스택에서 항목을 추가 하거나 가져올 수 없으며 cmdlet을 사용 하 여 `Get-Location` 명명 되지 않은 스택의 위치를 표시할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="69861-187">If you make a named location stack the current location stack, you can no longer use the `Push-Location` or `Pop-Location` cmdlets to add or get items from the default stack or use the `Get-Location` cmdlet to display the locations in the unnamed stack.</span></span> <span data-ttu-id="69861-188">명명 되지 않은 스택을 현재 스택으로 만들려면 cmdlet의 **Stackname** 매개 변수를 `Set-Location` 값 `$null` 이나 빈 문자열 ()로 사용 `""` 합니다.</span><span class="sxs-lookup"><span data-stu-id="69861-188">To make the unnamed stack the current stack, use the **StackName** parameter of the `Set-Location` cmdlet with a value of `$null` or an empty string (`""`).</span></span>

<span data-ttu-id="69861-189">의 기본 제공 별칭인를 참조할 수도 있습니다 `Push-Location` `pushd` .</span><span class="sxs-lookup"><span data-stu-id="69861-189">You can also refer to `Push-Location` by its built-in alias, `pushd`.</span></span> <span data-ttu-id="69861-190">자세한 내용은 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="69861-190">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

<span data-ttu-id="69861-191">`Push-Location`Cmdlet은 모든 공급자가 제공 하는 데이터에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69861-191">The `Push-Location` cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="69861-192">세션에서 사용할 수 있는 공급자를 나열 하려면을 입력 `Get-PSProvider` 합니다.</span><span class="sxs-lookup"><span data-stu-id="69861-192">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="69861-193">자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="69861-193">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="69861-194">관련 링크</span><span class="sxs-lookup"><span data-stu-id="69861-194">RELATED LINKS</span></span>

[<span data-ttu-id="69861-195">Get-Location</span><span class="sxs-lookup"><span data-stu-id="69861-195">Get-Location</span></span>](Get-Location.md)

[<span data-ttu-id="69861-196">Pop-Location</span><span class="sxs-lookup"><span data-stu-id="69861-196">Pop-Location</span></span>](Pop-Location.md)

[<span data-ttu-id="69861-197">Set-Location</span><span class="sxs-lookup"><span data-stu-id="69861-197">Set-Location</span></span>](Set-Location.md)

[<span data-ttu-id="69861-198">about_Aliases</span><span class="sxs-lookup"><span data-stu-id="69861-198">about_Aliases</span></span>](../Microsoft.PowerShell.Core/About/about_Aliases.md)

[<span data-ttu-id="69861-199">about_Providers</span><span class="sxs-lookup"><span data-stu-id="69861-199">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)