---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/remove-module?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Module
ms.openlocfilehash: 2954bbec68b837a73e5365ab6a1e8ecb501d4898
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599355"
---
# <span data-ttu-id="70454-102">Remove-Module</span><span class="sxs-lookup"><span data-stu-id="70454-102">Remove-Module</span></span>

## <span data-ttu-id="70454-103">개요</span><span class="sxs-lookup"><span data-stu-id="70454-103">SYNOPSIS</span></span>
<span data-ttu-id="70454-104">현재 세션에서 모듈을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="70454-104">Removes modules from the current session.</span></span>

## <span data-ttu-id="70454-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="70454-105">SYNTAX</span></span>

### <span data-ttu-id="70454-106">name</span><span class="sxs-lookup"><span data-stu-id="70454-106">name</span></span>

```
Remove-Module [-Name] <String[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="70454-107">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="70454-107">FullyQualifiedName</span></span>

```
Remove-Module [-FullyQualifiedName] <ModuleSpecification[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="70454-108">ModuleInfo</span><span class="sxs-lookup"><span data-stu-id="70454-108">ModuleInfo</span></span>

```
Remove-Module [-ModuleInfo] <PSModuleInfo[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="70454-109">설명</span><span class="sxs-lookup"><span data-stu-id="70454-109">DESCRIPTION</span></span>

<span data-ttu-id="70454-110">**Remove-Module** cmdlet은 cmdlet 및 함수와 같은 모듈의 멤버를 현재 세션에서 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="70454-110">The **Remove-Module** cmdlet removes the members of a module, such as cmdlets and functions, from the current session.</span></span>

<span data-ttu-id="70454-111">모듈에 어셈블리(.dll)가 포함되어 있을 경우 어셈블리를 통해 구현된 모든 멤버가 제거되지만 어셈블리는 언로드되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="70454-111">If the module includes an assembly (.dll), all members that are implemented by the assembly are removed, but the assembly is not unloaded.</span></span>

<span data-ttu-id="70454-112">이 cmdlet은 모듈을 제거하거나 컴퓨터에서 삭제하지 않고</span><span class="sxs-lookup"><span data-stu-id="70454-112">This cmdlet does not uninstall the module or delete it from the computer.</span></span>
<span data-ttu-id="70454-113">현재 PowerShell 세션에만 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="70454-113">It affects only the current PowerShell session.</span></span>

## <span data-ttu-id="70454-114">예제</span><span class="sxs-lookup"><span data-stu-id="70454-114">EXAMPLES</span></span>

### <span data-ttu-id="70454-115">예제 1: 모듈 제거</span><span class="sxs-lookup"><span data-stu-id="70454-115">Example 1: Remove a module</span></span>

```powershell
Remove-Module -Name "BitsTransfer"
```

<span data-ttu-id="70454-116">이 명령은 현재 세션에서 BitsTransfer 모듈을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="70454-116">This command removes the BitsTransfer module from the current session.</span></span>

### <span data-ttu-id="70454-117">예제 2: 모든 모듈 제거</span><span class="sxs-lookup"><span data-stu-id="70454-117">Example 2: Remove all modules</span></span>

```powershell
Get-Module | Remove-Module
```

<span data-ttu-id="70454-118">이 명령은 현재 세션에서 모든 모듈을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="70454-118">This command removes all modules from the current session.</span></span>

### <span data-ttu-id="70454-119">예제 3: 파이프라인을 사용 하 여 모듈 제거</span><span class="sxs-lookup"><span data-stu-id="70454-119">Example 3: Remove modules by using the pipeline</span></span>

```powershell
"FileTransfer", "PSDiagnostics" | Remove-Module -Verbose
```

```Output
VERBOSE: Performing operation "Remove-Module" on Target "filetransfer (Path: 'C:\Windows\system32\WindowsPowerShell\v1.0\Modules\filetransfer\filetransfer.psd1')".
VERBOSE: Performing operation "Remove-Module" on Target "Microsoft.BackgroundIntelligentTransfer.Management (Path: 'C:\Windows\assembly\GAC_MSIL\Microsoft.BackgroundIntelligentTransfer.Management\1.0.0.0__31bf3856ad364e35\Microsoft.BackgroundIntelligentTransfe
r.Management.dll')".
VERBOSE: Performing operation "Remove-Module" on Target "psdiagnostics (Path: 'C:\Windows\system32\WindowsPowerShell\v1.0\Modules\psdiagnostics\psdiagnostics.psd1')".
VERBOSE: Removing imported function 'Start-Trace'.
VERBOSE: Removing imported function 'Stop-Trace'.
VERBOSE: Removing imported function 'Enable-WSManTrace'.
VERBOSE: Removing imported function 'Disable-WSManTrace'.
VERBOSE: Removing imported function 'Enable-PSWSManCombinedTrace'.
VERBOSE: Removing imported function 'Disable-PSWSManCombinedTrace'.
VERBOSE: Removing imported function 'Set-LogProperties'.
VERBOSE: Removing imported function 'Get-LogProperties'.
VERBOSE: Removing imported function 'Enable-PSTrace'.
VERBOSE: Removing imported function 'Disable-PSTrace'.
VERBOSE: Performing operation "Remove-Module" on Target "PSDiagnostics (Path: 'C:\Windows\system32\WindowsPowerShell\v1.0\Modules\psdiagnostics\PSDiagnostics.psm1')".
```

<span data-ttu-id="70454-120">이 명령은 현재 세션에서 BitsTransfer 및 PSDiagnostics 모듈을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="70454-120">This command removes the BitsTransfer and PSDiagnostics modules from the current session.</span></span>

<span data-ttu-id="70454-121">파이프라인 연산자(|)를 사용하여 모듈 이름을 **Remove-Module** 로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="70454-121">The command uses a pipeline operator (|) to send the module names to **Remove-Module**.</span></span>
<span data-ttu-id="70454-122">또한 *Verbose* 일반 매개 변수를 사용하여 제거된 멤버에 대한 자세한 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="70454-122">It uses the *Verbose* common parameter to get detailed information about the members that are removed.</span></span>

<span data-ttu-id="70454-123">*자세한 정보* 메시지는 제거 된 항목을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="70454-123">The *Verbose* messages show the items that are removed.</span></span>
<span data-ttu-id="70454-124">BitsTransfer 모듈은 해당 cmdlet을 구현하는 어셈블리와 자체 어셈블리가 있는 중첩 모듈을 포함하기 때문에 메시지가 서로 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="70454-124">The messages differ because the BitsTransfer module includes an assembly that implements its cmdlets and a nested module with its own assembly.</span></span>
<span data-ttu-id="70454-125">PSDiagnostics 모듈에는 함수를 내보내는 모듈 스크립트 파일(.psm1)이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="70454-125">The PSDiagnostics module includes a module script file (.psm1) that exports functions.</span></span>

### <span data-ttu-id="70454-126">예제 4: ModuleInfo를 사용 하 여 모듈 제거</span><span class="sxs-lookup"><span data-stu-id="70454-126">Example 4: Remove a module by using ModuleInfo</span></span>

```powershell
$a = Get-Module BitsTransfer
Remove-Module -ModuleInfo $a
```

<span data-ttu-id="70454-127">이 명령은 *Moduleinfo* 매개 변수를 사용 하 여 BitsTransfer 모듈을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="70454-127">This command uses the *ModuleInfo* parameter to remove the BitsTransfer module.</span></span>

## <span data-ttu-id="70454-128">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="70454-128">PARAMETERS</span></span>

### <span data-ttu-id="70454-129">-Force</span><span class="sxs-lookup"><span data-stu-id="70454-129">-Force</span></span>

<span data-ttu-id="70454-130">이 cmdlet이 읽기 전용 모듈을 제거 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="70454-130">Indicates that this cmdlet removes read-only modules.</span></span>
<span data-ttu-id="70454-131">기본적으로 **Remove-Module** 은 읽기-쓰기 모듈만 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="70454-131">By default, **Remove-Module** removes only read-write modules.</span></span>

<span data-ttu-id="70454-132">**ReadOnly** 및 **ReadWrite** 값은 모듈의 **AccessMode** 속성에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="70454-132">The **ReadOnly** and **ReadWrite** values are stored in **AccessMode** property of a module.</span></span>

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

### <span data-ttu-id="70454-133">-FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="70454-133">-FullyQualifiedName</span></span>

<span data-ttu-id="70454-134">제거할 모듈의 정규화 된 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="70454-134">Specifies the fully qualified names of modules to remove.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification[]
Parameter Sets: FullyQualifiedName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="70454-135">-ModuleInfo</span><span class="sxs-lookup"><span data-stu-id="70454-135">-ModuleInfo</span></span>

<span data-ttu-id="70454-136">제거할 모듈 개체를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="70454-136">Specifies the module objects to remove.</span></span>
<span data-ttu-id="70454-137">모듈 개체 (**Psmoduleinfo**)를 포함 하는 변수를 입력 하거나 모듈 개체를 가져오는 명령 (예: Get-Module 명령)을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="70454-137">Enter a variable that contains a module object (**PSModuleInfo**) or a command that gets a module object, such as a Get-Module command.</span></span>
<span data-ttu-id="70454-138">모듈 개체를 **Remove-Module** 로 파이프할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="70454-138">You can also pipe module objects to **Remove-Module**.</span></span>

```yaml
Type: System.Management.Automation.PSModuleInfo[]
Parameter Sets: ModuleInfo
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="70454-139">-Name</span><span class="sxs-lookup"><span data-stu-id="70454-139">-Name</span></span>

<span data-ttu-id="70454-140">제거할 모듈의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="70454-140">Specifies the names of modules to remove.</span></span>
<span data-ttu-id="70454-141">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="70454-141">Wildcard characters are permitted.</span></span>
<span data-ttu-id="70454-142">이름 문자열을 **Remove-Module** 로 파이프할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="70454-142">You can also pipe name strings to **Remove-Module**.</span></span>

```yaml
Type: System.String[]
Parameter Sets: name
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="70454-143">-Confirm</span><span class="sxs-lookup"><span data-stu-id="70454-143">-Confirm</span></span>

<span data-ttu-id="70454-144">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="70454-144">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="70454-145">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="70454-145">-WhatIf</span></span>

<span data-ttu-id="70454-146">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="70454-146">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="70454-147">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="70454-147">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="70454-148">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="70454-148">CommonParameters</span></span>

<span data-ttu-id="70454-149">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="70454-149">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="70454-150">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="70454-150">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="70454-151">입력</span><span class="sxs-lookup"><span data-stu-id="70454-151">INPUTS</span></span>

### <span data-ttu-id="70454-152">System.string, System.web. a p a.</span><span class="sxs-lookup"><span data-stu-id="70454-152">System.String, System.Management.Automation.PSModuleInfo</span></span>

<span data-ttu-id="70454-153">모듈 이름 및 모듈 개체를 **제거** 로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="70454-153">You can pipe module names and module objects to **Remove-Module**.</span></span>

## <span data-ttu-id="70454-154">출력</span><span class="sxs-lookup"><span data-stu-id="70454-154">OUTPUTS</span></span>

### <span data-ttu-id="70454-155">없음</span><span class="sxs-lookup"><span data-stu-id="70454-155">None</span></span>

<span data-ttu-id="70454-156">이 cmdlet은 어떠한 출력도 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="70454-156">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="70454-157">참고</span><span class="sxs-lookup"><span data-stu-id="70454-157">NOTES</span></span>

<span data-ttu-id="70454-158">모듈을 제거 하는 경우 모듈에 실행 되는 이벤트가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="70454-158">When removing a module, there is an event on the module that will execute.</span></span>
<span data-ttu-id="70454-159">이 이벤트를 사용 하면 모듈이 제거 될 때 반응할 수 있으며 리소스 해제와 같은 일부 정리 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="70454-159">This event allows a module to react to being removed and perform some cleanup such as freeing up resources.</span></span> <span data-ttu-id="70454-160">예제:</span><span class="sxs-lookup"><span data-stu-id="70454-160">Example:</span></span>

<span data-ttu-id="70454-161">$OnRemoveScript = {</span><span class="sxs-lookup"><span data-stu-id="70454-161">$OnRemoveScript = {</span></span>

  <span data-ttu-id="70454-162">\# 정리 수행</span><span class="sxs-lookup"><span data-stu-id="70454-162">\# perform cleanup</span></span>

  <span data-ttu-id="70454-163">$cachedSessions | Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="70454-163">$cachedSessions | Remove-PSSession</span></span>

<span data-ttu-id="70454-164">}</span><span class="sxs-lookup"><span data-stu-id="70454-164">}</span></span>

<span data-ttu-id="70454-165">$ExecutionContext SessionState + = $OnRemoveScript</span><span class="sxs-lookup"><span data-stu-id="70454-165">$ExecutionContext.SessionState.Module.OnRemove += $OnRemoveScript</span></span>

<span data-ttu-id="70454-166">전체 일관성을 위해 PowerShell 프로세스를 닫을 때에도 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="70454-166">For full consistency, it might be also useful to react to the closing of the PowerShell process:</span></span>

<span data-ttu-id="70454-167">Register-EngineEvent-SourceIdentifier ([PsEngineEvent]:: 종료)-Action $OnRemoveScript</span><span class="sxs-lookup"><span data-stu-id="70454-167">Register-EngineEvent -SourceIdentifier ([System.Management.Automation.PsEngineEvent]::Exiting) -Action $OnRemoveScript</span></span>

## <span data-ttu-id="70454-168">관련 링크</span><span class="sxs-lookup"><span data-stu-id="70454-168">RELATED LINKS</span></span>

[<span data-ttu-id="70454-169">Get-Module</span><span class="sxs-lookup"><span data-stu-id="70454-169">Get-Module</span></span>](Get-Module.md)

[<span data-ttu-id="70454-170">모듈 가져오기</span><span class="sxs-lookup"><span data-stu-id="70454-170">Import-Module</span></span>](Import-Module.md)
