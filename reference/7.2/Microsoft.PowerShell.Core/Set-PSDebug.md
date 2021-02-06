---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 08/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/set-psdebug?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSDebug
ms.openlocfilehash: 45764b09bfa1f632fe5c36ca76b32b4a1b54874c
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99602448"
---
# <span data-ttu-id="90281-102">Set-PSDebug</span><span class="sxs-lookup"><span data-stu-id="90281-102">Set-PSDebug</span></span>

## <span data-ttu-id="90281-103">개요</span><span class="sxs-lookup"><span data-stu-id="90281-103">SYNOPSIS</span></span>
<span data-ttu-id="90281-104">스크립트 디버깅 기능을 설정/해제하고 추적 수준을 설정하며 Strict 모드를 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="90281-104">Turns script debugging features on and off, sets the trace level, and toggles strict mode.</span></span>

## <span data-ttu-id="90281-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="90281-105">SYNTAX</span></span>

### <span data-ttu-id="90281-106">on</span><span class="sxs-lookup"><span data-stu-id="90281-106">on</span></span>

```
Set-PSDebug [-Trace <Int32>] [-Step] [-Strict] [<CommonParameters>]
```

### <span data-ttu-id="90281-107">끄기</span><span class="sxs-lookup"><span data-stu-id="90281-107">off</span></span>

```
Set-PSDebug [-Off] [<CommonParameters>]
```

## <span data-ttu-id="90281-108">설명</span><span class="sxs-lookup"><span data-stu-id="90281-108">DESCRIPTION</span></span>

<span data-ttu-id="90281-109">`Set-PSDebug`Cmdlet은 스크립트 디버깅 기능을 설정 및 해제 하 고 추적 수준을 설정 하며 strict 모드를 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="90281-109">The `Set-PSDebug` cmdlet turns script debugging features on and off, sets the trace level, and toggles strict mode.</span></span> <span data-ttu-id="90281-110">기본적으로 PowerShell 디버그 기능은 해제 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90281-110">By default, the PowerShell debug features are off.</span></span>

<span data-ttu-id="90281-111">**Trace** 매개 변수의 값이 `1` 이면 스크립트의 각 줄이 실행 될 때 추적 됩니다.</span><span class="sxs-lookup"><span data-stu-id="90281-111">When the **Trace** parameter has a value of `1`, each line of script is traced as it runs.</span></span> <span data-ttu-id="90281-112">매개 변수에 값 `2` , 변수 할당, 함수 호출 및 스크립트 호출도 추적 됩니다.</span><span class="sxs-lookup"><span data-stu-id="90281-112">When the parameter has a value of `2`, variable assignments, function calls, and script calls are also traced.</span></span> <span data-ttu-id="90281-113">**Step** 매개 변수를 지정 하면 스크립트의 각 줄이 실행 되기 전에 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="90281-113">If the **Step** parameter is specified, you're prompted before each line of the script runs.</span></span>

## <span data-ttu-id="90281-114">예제</span><span class="sxs-lookup"><span data-stu-id="90281-114">EXAMPLES</span></span>

### <span data-ttu-id="90281-115">예제 1: 추적 수준 설정</span><span class="sxs-lookup"><span data-stu-id="90281-115">Example 1: Set the trace level</span></span>

<span data-ttu-id="90281-116">이 예에서는 추적 수준을으로 설정한 `2` 다음 숫자 1, 2 및를 표시 하는 스크립트를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="90281-116">This example sets the trace level to `2`, and then runs a script that displays the numbers 1, 2, and</span></span>
3.

```powershell
Set-PSDebug -Trace 2; foreach ($i in 1..3) {$i}
```

```Output
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ($i in  >>>> 1..3) {$i}
DEBUG:     ! SET $foreach = 'IEnumerator'.
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ( >>>> $i in 1..3) {$i}
DEBUG:     ! SET $i = '1'.
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ($i in 1..3) { >>>> $i}
1
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ( >>>> $i in 1..3) {$i}
DEBUG:     ! SET $i = '2'.
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ($i in 1..3) { >>>> $i}
2
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ( >>>> $i in 1..3) {$i}
DEBUG:     ! SET $i = '3'.
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ($i in 1..3) { >>>> $i}
3
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ( >>>> $i in 1..3) {$i}
DEBUG:     ! SET $foreach = ''.
```

### <span data-ttu-id="90281-117">예제 2: 단계별 실행 설정</span><span class="sxs-lookup"><span data-stu-id="90281-117">Example 2: Turn on stepping</span></span>

<span data-ttu-id="90281-118">이 예에서는 단계별 실행을 설정한 다음 숫자 1, 2, 3을 표시 하는 스크립트를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="90281-118">This example turns on stepping, and then runs a script that displays the numbers 1, 2, and 3.</span></span>

```powershell
Set-PSDebug -Step; foreach ($i in 1..3) {$i}
```

```Output
Continue with this operation?
   1+ Set-PSDebug -Step; foreach ($i in  >>>> 1..3) {$i}
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): A
DEBUG:    1+ Set-PSDebug -Step; foreach ($i in  >>>> 1..3) {$i}
1
2
3
```

### <span data-ttu-id="90281-119">예제 3: strict 모드 사용</span><span class="sxs-lookup"><span data-stu-id="90281-119">Example 3: Use strict mode</span></span>

<span data-ttu-id="90281-120">이 예에서는 PowerShell을 strict 모드로 전환 하 고 할당 된 값이 없는 변수에 액세스 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="90281-120">This example puts PowerShell in strict mode and attempts to access a variable that doesn't have an assigned value.</span></span>

```powershell
Set-PSDebug -Strict; $NewVar
```

```Output
The variable '$NewVar' cannot be retrieved because it has not been set.
At line:1 char:22
+ Set-PSDebug -Strict; $NewVar
```

### <span data-ttu-id="90281-121">예제 4: 디버그 기능 해제</span><span class="sxs-lookup"><span data-stu-id="90281-121">Example 4: Turn off debug features</span></span>

<span data-ttu-id="90281-122">이 예제에서는 모든 디버깅 기능을 해제 한 다음 숫자 1, 2, 3을 표시 하는 스크립트를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="90281-122">This example turns off all debugging features, and then runs a script that displays the numbers 1, 2, and 3.</span></span>

```powershell
Set-PSDebug -Off; foreach ($i in 1..3) {$i}
```

```Output
1
2
3
```

## <span data-ttu-id="90281-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="90281-123">PARAMETERS</span></span>

### <span data-ttu-id="90281-124">-꺼짐</span><span class="sxs-lookup"><span data-stu-id="90281-124">-Off</span></span>

<span data-ttu-id="90281-125">모든 스크립트 디버깅 기능을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="90281-125">Turns off all script debugging features.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: off
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="90281-126">-단계</span><span class="sxs-lookup"><span data-stu-id="90281-126">-Step</span></span>

<span data-ttu-id="90281-127">단계별 스크립트 실행을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="90281-127">Turns on script stepping.</span></span> <span data-ttu-id="90281-128">PowerShell은 각 줄을 실행 하기 전에 스크립트의 상태를 검사 하기 위해 새 인터프리터 수준을 중지 하거나, 계속 하거나, 입력 하 라는 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="90281-128">Before each line runs, PowerShell prompts you to stop, continue, or enter a new interpreter level to inspect the state of the script.</span></span>

<span data-ttu-id="90281-129">**Step** 매개 변수를 지정 하면의 추적 수준이 자동으로 설정 `1` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="90281-129">Specifying the **Step** parameter automatically sets a trace level of `1`.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: on
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="90281-130">-Strict</span><span class="sxs-lookup"><span data-stu-id="90281-130">-Strict</span></span>

<span data-ttu-id="90281-131">변수에 값을 할당 하 여 스크립트에서 참조 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="90281-131">Specifies that variables must be assigned a value before being referenced in a script.</span></span> <span data-ttu-id="90281-132">값이 할당 되기 전에 변수가 참조 되는 경우 PowerShell은 예외 오류를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="90281-132">If a variable is referenced before a value is assigned, PowerShell returns an exception error.</span></span> <span data-ttu-id="90281-133">`Set-StrictMode -Version 1`와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="90281-133">This is equivalent to `Set-StrictMode -Version 1`.</span></span> <span data-ttu-id="90281-134">자세한 내용은 [set-strictmode](Set-StrictMode.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="90281-134">For more information, see [Set-StrictMode](Set-StrictMode.md).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: on
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="90281-135">-Trace</span><span class="sxs-lookup"><span data-stu-id="90281-135">-Trace</span></span>

<span data-ttu-id="90281-136">스크립트의 각 줄에 대 한 추적 수준을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="90281-136">Specifies the trace level for each line in a script.</span></span> <span data-ttu-id="90281-137">각 줄은 실행 될 때 추적 됩니다.</span><span class="sxs-lookup"><span data-stu-id="90281-137">Each line is traced as it's run.</span></span>

<span data-ttu-id="90281-138">이 매개 변수에 허용 되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="90281-138">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="90281-139">0: 스크립트 추적을 해제 합니다.</span><span class="sxs-lookup"><span data-stu-id="90281-139">0: Turn script tracing off.</span></span>
- <span data-ttu-id="90281-140">1: 실행 되는 스크립트 줄을 추적 합니다.</span><span class="sxs-lookup"><span data-stu-id="90281-140">1: Trace script lines as they run.</span></span>
- <span data-ttu-id="90281-141">2: 스크립트 줄, 변수 할당, 함수 호출 및 스크립트를 추적 합니다.</span><span class="sxs-lookup"><span data-stu-id="90281-141">2: Trace script lines, variable assignments, function calls, and scripts.</span></span>

```yaml
Type: System.Int32
Parameter Sets: on
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="90281-142">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="90281-142">CommonParameters</span></span>

<span data-ttu-id="90281-143">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="90281-143">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="90281-144">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="90281-144">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="90281-145">입력</span><span class="sxs-lookup"><span data-stu-id="90281-145">INPUTS</span></span>

### <span data-ttu-id="90281-146">없음</span><span class="sxs-lookup"><span data-stu-id="90281-146">None</span></span>

<span data-ttu-id="90281-147">이 cmdlet에 대 한 입력을 파이프라인으로 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="90281-147">You can't pipeline input to this cmdlet.</span></span>

## <span data-ttu-id="90281-148">출력</span><span class="sxs-lookup"><span data-stu-id="90281-148">OUTPUTS</span></span>

### <span data-ttu-id="90281-149">없음</span><span class="sxs-lookup"><span data-stu-id="90281-149">None</span></span>

<span data-ttu-id="90281-150">이 cmdlet은 출력을 반환 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="90281-150">This cmdlet doesn't return any output.</span></span>

## <span data-ttu-id="90281-151">참고</span><span class="sxs-lookup"><span data-stu-id="90281-151">NOTES</span></span>

## <span data-ttu-id="90281-152">관련 링크</span><span class="sxs-lookup"><span data-stu-id="90281-152">RELATED LINKS</span></span>

[<span data-ttu-id="90281-153">about_Debuggers</span><span class="sxs-lookup"><span data-stu-id="90281-153">about_Debuggers</span></span>](./About/about_Debuggers.md)

[<span data-ttu-id="90281-154">Debug-Process</span><span class="sxs-lookup"><span data-stu-id="90281-154">Debug-Process</span></span>](../Microsoft.PowerShell.Management/Debug-Process.md)

[<span data-ttu-id="90281-155">Set-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="90281-155">Set-PSBreakpoint</span></span>](../Microsoft.PowerShell.Utility/Set-PSBreakpoint.md)

[<span data-ttu-id="90281-156">Set-StrictMode</span><span class="sxs-lookup"><span data-stu-id="90281-156">Set-StrictMode</span></span>](Set-StrictMode.md)

[<span data-ttu-id="90281-157">Write-Debug</span><span class="sxs-lookup"><span data-stu-id="90281-157">Write-Debug</span></span>](../Microsoft.PowerShell.Utility/Write-Debug.md)

