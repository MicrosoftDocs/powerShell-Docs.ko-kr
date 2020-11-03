---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/09/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/trace-command?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Trace-Command
ms.openlocfilehash: c26e1c46db8f7c6eeeb5c970bc17921622cd023e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93211746"
---
# <span data-ttu-id="43a39-103">Trace-Command</span><span class="sxs-lookup"><span data-stu-id="43a39-103">Trace-Command</span></span>

## <span data-ttu-id="43a39-104">개요</span><span class="sxs-lookup"><span data-stu-id="43a39-104">SYNOPSIS</span></span>
<span data-ttu-id="43a39-105">지정된 식 또는 명령의 추적을 구성하고 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="43a39-105">Configures and starts a trace of the specified expression or command.</span></span>

## <span data-ttu-id="43a39-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="43a39-106">SYNTAX</span></span>

### <span data-ttu-id="43a39-107">expressionSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="43a39-107">expressionSet (Default)</span></span>

```
Trace-Command [-InputObject <PSObject>] [-Name] <String[]> [[-Option] <PSTraceSourceOptions>]
 [-Expression] <ScriptBlock> [-ListenerOption <TraceOptions>] [-FilePath <String>] [-Force] [-Debugger]
 [-PSHost] [<CommonParameters>]
```

### <span data-ttu-id="43a39-108">commandSet</span><span class="sxs-lookup"><span data-stu-id="43a39-108">commandSet</span></span>

```
Trace-Command [-InputObject <PSObject>] [-Name] <String[]> [[-Option] <PSTraceSourceOptions>]
 [-Command] <String> [-ArgumentList <Object[]>] [-ListenerOption <TraceOptions>] [-FilePath <String>] [-Force]
 [-Debugger] [-PSHost] [<CommonParameters>]
```

## <span data-ttu-id="43a39-109">설명</span><span class="sxs-lookup"><span data-stu-id="43a39-109">DESCRIPTION</span></span>
<span data-ttu-id="43a39-110">`Trace-Command`Cmdlet은 지정 된 식 또는 명령의 추적을 구성 하 고 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="43a39-110">The `Trace-Command` cmdlet configures and starts a trace of the specified expression or command.</span></span>
<span data-ttu-id="43a39-111">지정한 명령에만 적용된다는 점을 제외하고 Set-TraceSource와 동일하게 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="43a39-111">It works like Set-TraceSource, except that it applies only to the specified command.</span></span>

## <span data-ttu-id="43a39-112">예제</span><span class="sxs-lookup"><span data-stu-id="43a39-112">EXAMPLES</span></span>

### <span data-ttu-id="43a39-113">예제 1: 추적 메타 데이터 처리, 매개 변수 바인딩 및 식</span><span class="sxs-lookup"><span data-stu-id="43a39-113">Example 1: Trace metadata processing, parameter binding, and an expression</span></span>

<span data-ttu-id="43a39-114">이 예에서는 메타 데이터 처리, 매개 변수 바인딩 및 식의 생성 및 소멸에 대 한 추적을 시작 `Get-Process Notepad` 합니다.</span><span class="sxs-lookup"><span data-stu-id="43a39-114">This example starts a trace of metadata processing, parameter binding, and cmdlet creation and destruction of the `Get-Process Notepad` expression.</span></span>

```powershell
Trace-Command -Name metadata,parameterbinding,cmdlet -Expression {Get-Process Notepad} -PSHost
```

<span data-ttu-id="43a39-115">**Name** 매개 변수를 사용 하 여 추적 원본을 지정 하 고, **Expression** 매개 변수를 사용 하 여 명령을 지정 하 고, **PSHost** 매개 변수를 사용 하 여 출력을 콘솔로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="43a39-115">It uses the **Name** parameter to specify the trace sources, the **Expression** parameter to specify the command, and the **PSHost** parameter to send the output to the console.</span></span> <span data-ttu-id="43a39-116">이 명령은 추적 옵션이 나 수신기 옵션을 지정 하지 않으므로 기본값을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="43a39-116">Because it does not specify any tracing options or listener options, the command uses the defaults:</span></span>

- <span data-ttu-id="43a39-117">모든 추적 옵션</span><span class="sxs-lookup"><span data-stu-id="43a39-117">All for the tracing options</span></span>
- <span data-ttu-id="43a39-118">수신기 옵션의 경우 없음</span><span class="sxs-lookup"><span data-stu-id="43a39-118">None for the listener options</span></span>

### <span data-ttu-id="43a39-119">예제 2: ParameterBinding 작업의 동작 추적</span><span class="sxs-lookup"><span data-stu-id="43a39-119">Example 2: Trace the actions of ParameterBinding operations</span></span>

<span data-ttu-id="43a39-120">이 예제에서는 파이프라인의 입력을 사용 하는 식을 처리 하는 동안 PowerShell의 **Parameterbinding** 작업 동작을 추적 합니다 `Get-Alias` .</span><span class="sxs-lookup"><span data-stu-id="43a39-120">This example traces the actions of the **ParameterBinding** operations of PowerShell while it processes a `Get-Alias` expression that takes input from the pipeline.</span></span>

```powershell
$A = "i*"
Trace-Command ParameterBinding {Get-Alias $Input} -PSHost -InputObject $A
```

<span data-ttu-id="43a39-121">에서 `Trace-Command` **InputObject** 매개 변수는 추적 하는 동안 처리 되는 식에 개체를 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="43a39-121">In `Trace-Command`, the **InputObject** parameter passes an object to the expression that is being processed during the trace.</span></span>

<span data-ttu-id="43a39-122">첫 번째 명령은 문자열을 `i*` 변수에 저장 합니다 `$A` .</span><span class="sxs-lookup"><span data-stu-id="43a39-122">The first command stores the string `i*` in the `$A` variable.</span></span> <span data-ttu-id="43a39-123">두 번째 명령은 `Trace-Command` ParameterBinding 추적 원본과 함께 cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="43a39-123">The second command uses the `Trace-Command` cmdlet with the ParameterBinding trace source.</span></span> <span data-ttu-id="43a39-124">**PSHost** 매개 변수는 출력을 콘솔로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="43a39-124">The **PSHost** parameter sends the output to the console.</span></span>

<span data-ttu-id="43a39-125">처리 되는 식은 이며 `Get-Alias $Input` , 여기서 `$Input` 변수는 **InputObject** 매개 변수와 연결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="43a39-125">The expression being processed is `Get-Alias $Input`, where the `$Input` variable is associated with the **InputObject** parameter.</span></span> <span data-ttu-id="43a39-126">**InputObject** 매개 변수는 변수를 `$A` 식으로 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="43a39-126">The **InputObject** parameter passes the variable `$A` to the expression.</span></span> <span data-ttu-id="43a39-127">실제로 추적 하는 동안 처리 되는 명령은 `Get-Alias -InputObject $A" or "$A | Get-Alias` 입니다.</span><span class="sxs-lookup"><span data-stu-id="43a39-127">In effect, the command being processed during the trace is `Get-Alias -InputObject $A" or "$A | Get-Alias`.</span></span>

## <span data-ttu-id="43a39-128">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="43a39-128">PARAMETERS</span></span>

### <span data-ttu-id="43a39-129">-ArgumentList</span><span class="sxs-lookup"><span data-stu-id="43a39-129">-ArgumentList</span></span>

<span data-ttu-id="43a39-130">추적되는 명령의 매개 변수 및 매개 변수 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="43a39-130">Specifies the parameters and parameter values for the command being traced.</span></span> <span data-ttu-id="43a39-131">**ArgumentList** 의 별칭은 **Args** 입니다.</span><span class="sxs-lookup"><span data-stu-id="43a39-131">The alias for **ArgumentList** is **Args** .</span></span> <span data-ttu-id="43a39-132">이 기능은 동적 매개 변수를 디버그하는 데 특히 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="43a39-132">This feature is especially useful for debugging dynamic parameters.</span></span>

<span data-ttu-id="43a39-133">**Argumentlist** 의 동작에 대 한 자세한 내용은 [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md#splatting-with-arrays)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="43a39-133">For more information about the behavior of **ArgumentList** , see [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md#splatting-with-arrays).</span></span>

```yaml
Type: System.Object[]
Parameter Sets: commandSet
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="43a39-134">-Command</span><span class="sxs-lookup"><span data-stu-id="43a39-134">-Command</span></span>

<span data-ttu-id="43a39-135">추적하는 동안 처리되는 명령을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="43a39-135">Specifies a command that is being processed during the trace.</span></span>

```yaml
Type: System.String
Parameter Sets: commandSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="43a39-136">-디버거</span><span class="sxs-lookup"><span data-stu-id="43a39-136">-Debugger</span></span>

<span data-ttu-id="43a39-137">Cmdlet이 추적 출력을 디버거로 보낼지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="43a39-137">Indicates that the cmdlet sends the trace output to the debugger.</span></span> <span data-ttu-id="43a39-138">사용자 모드 또는 커널 모드 디버거나 Visual Studio에서 출력을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="43a39-138">You can view the output in any user-mode or kernel mode debugger or in Visual Studio.</span></span> <span data-ttu-id="43a39-139">이 매개 변수는 기본 추적 수신기도 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="43a39-139">This parameter also selects the default trace listener.</span></span>

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

### <span data-ttu-id="43a39-140">-식</span><span class="sxs-lookup"><span data-stu-id="43a39-140">-Expression</span></span>

<span data-ttu-id="43a39-141">추적하는 동안 처리되는 식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="43a39-141">Specifies the expression that is being processed during the trace.</span></span> <span data-ttu-id="43a39-142">식을 중괄호 ()로 묶습니다 `{}` .</span><span class="sxs-lookup"><span data-stu-id="43a39-142">Enclose the expression in braces (`{}`).</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: expressionSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="43a39-143">-FilePath</span><span class="sxs-lookup"><span data-stu-id="43a39-143">-FilePath</span></span>

<span data-ttu-id="43a39-144">Cmdlet이 추적 출력을 전송 하는 파일을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="43a39-144">Specifies a file that the cmdlet sends the trace output to.</span></span> <span data-ttu-id="43a39-145">이 매개 변수는 파일 추적 수신기도 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="43a39-145">This parameter also selects the file trace listener.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSPath, Path

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="43a39-146">-Force</span><span class="sxs-lookup"><span data-stu-id="43a39-146">-Force</span></span>

<span data-ttu-id="43a39-147">사용자 확인을 요청하지 않고 명령을 강제 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="43a39-147">Forces the command to run without asking for user confirmation.</span></span> <span data-ttu-id="43a39-148">**FilePath** 매개 변수와 함께 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="43a39-148">Used with the **FilePath** parameter.</span></span> <span data-ttu-id="43a39-149">**Force** 매개 변수를 사용 하는 경우에도 cmdlet은 보안 제한을 재정의할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="43a39-149">Even using the **Force** parameter, the cmdlet cannot override security restrictions.</span></span>

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

### <span data-ttu-id="43a39-150">-InputObject</span><span class="sxs-lookup"><span data-stu-id="43a39-150">-InputObject</span></span>

<span data-ttu-id="43a39-151">추적 하는 동안 처리 되는 식에 대 한 입력을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="43a39-151">Specifies input to the expression that is being processed during the trace.</span></span> <span data-ttu-id="43a39-152">식에서 허용하는 입력을 나타내는 변수를 입력하거나 파이프라인을 통해 개체를 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="43a39-152">You can enter a variable that represents the input that the expression accepts, or pass an object through the pipeline.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="43a39-153">-ListenerOption</span><span class="sxs-lookup"><span data-stu-id="43a39-153">-ListenerOption</span></span>

<span data-ttu-id="43a39-154">출력에서 각 추적 메시지의 접두사에 대 한 선택적 데이터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="43a39-154">Specifies optional data to the prefix of each trace message in the output.</span></span> <span data-ttu-id="43a39-155">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="43a39-155">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="43a39-156">없음</span><span class="sxs-lookup"><span data-stu-id="43a39-156">None</span></span>
- <span data-ttu-id="43a39-157">LogicalOperationStack</span><span class="sxs-lookup"><span data-stu-id="43a39-157">LogicalOperationStack</span></span>
- <span data-ttu-id="43a39-158">DateTime</span><span class="sxs-lookup"><span data-stu-id="43a39-158">DateTime</span></span>
- <span data-ttu-id="43a39-159">타임스탬프</span><span class="sxs-lookup"><span data-stu-id="43a39-159">Timestamp</span></span>
- <span data-ttu-id="43a39-160">ProcessId</span><span class="sxs-lookup"><span data-stu-id="43a39-160">ProcessId</span></span>
- <span data-ttu-id="43a39-161">스레드 Id</span><span class="sxs-lookup"><span data-stu-id="43a39-161">ThreadId</span></span>
- <span data-ttu-id="43a39-162">호출 스택</span><span class="sxs-lookup"><span data-stu-id="43a39-162">Callstack</span></span>

<span data-ttu-id="43a39-163">기본값은 **없음** 입니다.</span><span class="sxs-lookup"><span data-stu-id="43a39-163">**None** is the default.</span></span>

<span data-ttu-id="43a39-164">여러 옵션을 지정하려면 "ProcessID,ThreadID"와 같이 공백 없이 쉼표로 구분하고 따옴표로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="43a39-164">To specify multiple options, separate them with commas, but with no spaces, and enclose them in quotation marks, such as "ProcessID,ThreadID".</span></span>

```yaml
Type: System.Diagnostics.TraceOptions
Parameter Sets: (All)
Aliases:
Accepted values: None, LogicalOperationStack, DateTime, Timestamp, ProcessId, ThreadId, Callstack

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="43a39-165">-Name</span><span class="sxs-lookup"><span data-stu-id="43a39-165">-Name</span></span>

<span data-ttu-id="43a39-166">추적할 PowerShell 구성 요소의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="43a39-166">Specifies an array of PowerShell components that are traced.</span></span> <span data-ttu-id="43a39-167">각 구성 요소의 추적 원본 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="43a39-167">Enter the name of the trace source of each component.</span></span> <span data-ttu-id="43a39-168">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="43a39-168">Wildcards are permitted.</span></span> <span data-ttu-id="43a39-169">컴퓨터에서 추적 소스를 찾으려면를 입력 `Get-TraceSource` 합니다.</span><span class="sxs-lookup"><span data-stu-id="43a39-169">To find the trace sources on your computer, type `Get-TraceSource`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="43a39-170">-옵션</span><span class="sxs-lookup"><span data-stu-id="43a39-170">-Option</span></span>

<span data-ttu-id="43a39-171">추적할 이벤트 유형을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="43a39-171">Determines the type of events that are traced.</span></span> <span data-ttu-id="43a39-172">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="43a39-172">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="43a39-173">없음</span><span class="sxs-lookup"><span data-stu-id="43a39-173">None</span></span>
- <span data-ttu-id="43a39-174">생성자</span><span class="sxs-lookup"><span data-stu-id="43a39-174">Constructor</span></span>
- <span data-ttu-id="43a39-175">Dispose</span><span class="sxs-lookup"><span data-stu-id="43a39-175">Dispose</span></span>
- <span data-ttu-id="43a39-176">Finalizer</span><span class="sxs-lookup"><span data-stu-id="43a39-176">Finalizer</span></span>
- <span data-ttu-id="43a39-177">메서드</span><span class="sxs-lookup"><span data-stu-id="43a39-177">Method</span></span>
- <span data-ttu-id="43a39-178">속성</span><span class="sxs-lookup"><span data-stu-id="43a39-178">Property</span></span>
- <span data-ttu-id="43a39-179">대리자</span><span class="sxs-lookup"><span data-stu-id="43a39-179">Delegates</span></span>
- <span data-ttu-id="43a39-180">이벤트</span><span class="sxs-lookup"><span data-stu-id="43a39-180">Events</span></span>
- <span data-ttu-id="43a39-181">예외</span><span class="sxs-lookup"><span data-stu-id="43a39-181">Exception</span></span>
- <span data-ttu-id="43a39-182">잠금</span><span class="sxs-lookup"><span data-stu-id="43a39-182">Lock</span></span>
- <span data-ttu-id="43a39-183">오류</span><span class="sxs-lookup"><span data-stu-id="43a39-183">Error</span></span>
- <span data-ttu-id="43a39-184">오류</span><span class="sxs-lookup"><span data-stu-id="43a39-184">Errors</span></span>
- <span data-ttu-id="43a39-185">경고</span><span class="sxs-lookup"><span data-stu-id="43a39-185">Warning</span></span>
- <span data-ttu-id="43a39-186">자세히</span><span class="sxs-lookup"><span data-stu-id="43a39-186">Verbose</span></span>
- <span data-ttu-id="43a39-187">WriteLine</span><span class="sxs-lookup"><span data-stu-id="43a39-187">WriteLine</span></span>
- <span data-ttu-id="43a39-188">데이터</span><span class="sxs-lookup"><span data-stu-id="43a39-188">Data</span></span>
- <span data-ttu-id="43a39-189">Scope</span><span class="sxs-lookup"><span data-stu-id="43a39-189">Scope</span></span>
- <span data-ttu-id="43a39-190">ExecutionFlow</span><span class="sxs-lookup"><span data-stu-id="43a39-190">ExecutionFlow</span></span>
- <span data-ttu-id="43a39-191">Assert</span><span class="sxs-lookup"><span data-stu-id="43a39-191">Assert</span></span>
- <span data-ttu-id="43a39-192">모두</span><span class="sxs-lookup"><span data-stu-id="43a39-192">All</span></span>

<span data-ttu-id="43a39-193">All이 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="43a39-193">All is the default.</span></span>

<span data-ttu-id="43a39-194">다음 값은 다른 값의 조합입니다.</span><span class="sxs-lookup"><span data-stu-id="43a39-194">The following values are combinations of other values:</span></span>

- <span data-ttu-id="43a39-195">ExecutionFlow: (Constructor, Dispose, Finalizer, Method, 대리자, 이벤트 및 범위)</span><span class="sxs-lookup"><span data-stu-id="43a39-195">ExecutionFlow: (Constructor, Dispose, Finalizer, Method, Delegates, Events, and Scope)</span></span>
- <span data-ttu-id="43a39-196">데이터: (Constructor, Dispose, Finalizer, Property, Verbose 및 WriteLine)</span><span class="sxs-lookup"><span data-stu-id="43a39-196">Data: (Constructor, Dispose, Finalizer, Property, Verbose, and WriteLine)</span></span>
- <span data-ttu-id="43a39-197">오류: (오류 및 예외).</span><span class="sxs-lookup"><span data-stu-id="43a39-197">Errors: (Error and Exception).</span></span>

<span data-ttu-id="43a39-198">여러 옵션을 지정하려면 "Constructor,Dispose"와 같이 공백 없이 쉼표로 구분하고 따옴표로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="43a39-198">To specify multiple options, separate them with commas, but with no spaces, and enclose them in quotation marks, such as "Constructor,Dispose".</span></span>

```yaml
Type: System.Management.Automation.PSTraceSourceOptions
Parameter Sets: (All)
Aliases:
Accepted values: None, Constructor, Dispose, Finalizer, Method, Property, Delegates, Events, Exception, Lock, Error, Errors, Warning, Verbose, WriteLine, Data, Scope, ExecutionFlow, Assert, All

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="43a39-199">-PSHost</span><span class="sxs-lookup"><span data-stu-id="43a39-199">-PSHost</span></span>

<span data-ttu-id="43a39-200">Cmdlet이 추적 출력을 PowerShell 호스트로 보내도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="43a39-200">Indicates that the cmdlet sends the trace output to the PowerShell host.</span></span> <span data-ttu-id="43a39-201">이 매개 변수는 PSHost 추적 수신기도 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="43a39-201">This parameter also selects the PSHost trace listener.</span></span>

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

### <span data-ttu-id="43a39-202">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="43a39-202">CommonParameters</span></span>

<span data-ttu-id="43a39-203">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="43a39-203">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="43a39-204">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="43a39-204">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="43a39-205">입력</span><span class="sxs-lookup"><span data-stu-id="43a39-205">INPUTS</span></span>

### <span data-ttu-id="43a39-206">System.web. PSObject</span><span class="sxs-lookup"><span data-stu-id="43a39-206">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="43a39-207">식에 대 한 입력을 나타내는 개체를로 파이프 할 수 있습니다 `Trace-Command` .</span><span class="sxs-lookup"><span data-stu-id="43a39-207">You can pipe objects that represent input to the expression to `Trace-Command`.</span></span>

## <span data-ttu-id="43a39-208">출력</span><span class="sxs-lookup"><span data-stu-id="43a39-208">OUTPUTS</span></span>

### <span data-ttu-id="43a39-209">System.web. PSObject</span><span class="sxs-lookup"><span data-stu-id="43a39-209">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="43a39-210">명령 추적을 디버그 스트림으로 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="43a39-210">Returns the command trace in the debug stream.</span></span>

## <span data-ttu-id="43a39-211">참고</span><span class="sxs-lookup"><span data-stu-id="43a39-211">NOTES</span></span>

- <span data-ttu-id="43a39-212">추적은 개발자가 디버깅하고 프로그램을 다듬는 데 사용하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="43a39-212">Tracing is a method that developers use to debug and refine programs.</span></span> <span data-ttu-id="43a39-213">추적하면 프로그램에서 내부 프로세스의 각 단계에 대한 세부 메시지를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="43a39-213">When tracing, the program generates detailed messages about each step in its internal processing.</span></span>

- <span data-ttu-id="43a39-214">Powershell 추적 cmdlet은 PowerShell 개발자를 돕기 위해 설계 되었지만 모든 사용자가 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="43a39-214">The PowerShell tracing cmdlets are designed to help PowerShell developers, but they are available to all users.</span></span> <span data-ttu-id="43a39-215">이 cmdlet을 사용하면 셸 기능의 거의 모든 측면을 모니터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="43a39-215">They let you monitor nearly every aspect of the functionality of the shell.</span></span>

- <span data-ttu-id="43a39-216">추적할 수 있는 PowerShell 구성 요소를 찾으려면를 입력 `Get-Help Get-TraceSource` 합니다.</span><span class="sxs-lookup"><span data-stu-id="43a39-216">To find the PowerShell components that are enabled for tracing, type `Get-Help Get-TraceSource`.</span></span>

  <span data-ttu-id="43a39-217">추적 소스는 추적을 관리 하 고 구성 요소에 대 한 추적 메시지를 생성 하는 각 PowerShell 구성 요소의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="43a39-217">A trace source is the part of each PowerShell component that manages tracing and generates trace messages for the component.</span></span> <span data-ttu-id="43a39-218">구성 요소를 추적하려면 추적 원본을 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="43a39-218">To trace a component, you identify its trace source.</span></span>

  <span data-ttu-id="43a39-219">추적 수신기는 추적의 출력을 받아 사용자에 게 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="43a39-219">A trace listener receives the output of the trace and displays it to the user.</span></span> <span data-ttu-id="43a39-220">사용자 모드 또는 커널 모드 디버거, 호스트 또는 콘솔, 파일 또는 **TraceListener** 클래스에서 파생 된 사용자 지정 수신기로 추적 데이터를 보내도록 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="43a39-220">You can elect to send the trace data to a user-mode or kernel-mode debugger, to the host or console, to a file, or to a custom listener derived from the **System.Diagnostics.TraceListener** class.</span></span>

- <span data-ttu-id="43a39-221">CommandSet 매개 변수 집합을 사용 하는 경우 PowerShell은 파이프라인에서 처리 되는 것과 동일한 방식으로 명령을 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="43a39-221">When you use the commandSet parameter set, PowerShell processes the command just as it would be processed in a pipeline.</span></span> <span data-ttu-id="43a39-222">예를 들어 들어오는 개체마다 명령 검색을 반복하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="43a39-222">For example, command discovery is not repeated for each incoming object.</span></span>

- <span data-ttu-id="43a39-223">**Name** , **Expression** , **Option** 및 **Command** 매개 변수의 이름은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="43a39-223">The names of the **Name** , **Expression** , **Option** , and **Command** parameters are optional.</span></span> <span data-ttu-id="43a39-224">매개 변수 이름을 생략 하는 경우 명명 되지 않은 매개 변수 값은 **Name** , **Expression** , **option** 또는 **name** , **Command** , **option** 순서로 표시 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="43a39-224">If you omit the parameter names, the unnamed parameter values must appear in this order: **Name** , **Expression** , **Option** or **Name** , **Command** , **Option** .</span></span> <span data-ttu-id="43a39-225">매개 변수 이름을 포함할 경우 원하는 순서대로 매개 변수를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="43a39-225">If you include the parameter names, the parameters can appear in any order.</span></span>

## <span data-ttu-id="43a39-226">관련 링크</span><span class="sxs-lookup"><span data-stu-id="43a39-226">RELATED LINKS</span></span>

[<span data-ttu-id="43a39-227">Get-TraceSource</span><span class="sxs-lookup"><span data-stu-id="43a39-227">Get-TraceSource</span></span>](Get-TraceSource.md)

[<span data-ttu-id="43a39-228">Measure-Command</span><span class="sxs-lookup"><span data-stu-id="43a39-228">Measure-Command</span></span>](Measure-Command.md)

[<span data-ttu-id="43a39-229">Set-TraceSource</span><span class="sxs-lookup"><span data-stu-id="43a39-229">Set-TraceSource</span></span>](Set-TraceSource.md)

