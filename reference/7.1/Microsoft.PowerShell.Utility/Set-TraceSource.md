---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-tracesource?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-TraceSource
ms.openlocfilehash: 00e9b3bc18d24fe252aee20eb77af0b5ad99468e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93211802"
---
# <span data-ttu-id="23764-103">Set-TraceSource</span><span class="sxs-lookup"><span data-stu-id="23764-103">Set-TraceSource</span></span>

## <span data-ttu-id="23764-104">개요</span><span class="sxs-lookup"><span data-stu-id="23764-104">SYNOPSIS</span></span>
<span data-ttu-id="23764-105">PowerShell 구성 요소의 추적을 구성, 시작 및 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="23764-105">Configures, starts, and stops a trace of PowerShell components.</span></span>

## <span data-ttu-id="23764-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="23764-106">SYNTAX</span></span>

### <span data-ttu-id="23764-107">기본 설정 (기본값)</span><span class="sxs-lookup"><span data-stu-id="23764-107">optionsSet (Default)</span></span>

```
Set-TraceSource [-Name] <String[]> [[-Option] <PSTraceSourceOptions>] [-ListenerOption <TraceOptions>]
 [-FilePath <String>] [-Force] [-Debugger] [-PSHost] [-PassThru] [<CommonParameters>]
```

### <span data-ttu-id="23764-108">removeAllListenersSet</span><span class="sxs-lookup"><span data-stu-id="23764-108">removeAllListenersSet</span></span>

```
Set-TraceSource [-Name] <String[]> [-RemoveListener <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="23764-109">removeFileListenersSet</span><span class="sxs-lookup"><span data-stu-id="23764-109">removeFileListenersSet</span></span>

```
Set-TraceSource [-Name] <String[]> [-RemoveFileListener <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="23764-110">설명</span><span class="sxs-lookup"><span data-stu-id="23764-110">DESCRIPTION</span></span>

<span data-ttu-id="23764-111">**TraceSource** Cmdlet은 PowerShell 구성 요소의 추적을 구성, 시작 및 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="23764-111">The **Set-TraceSource** cmdlet configures, starts, and stops a trace of a PowerShell component.</span></span>
<span data-ttu-id="23764-112">이 cmdlet을 사용하면 추적할 구성 요소 및 추적한 출력을 보낼 위치를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23764-112">You can use it to specify which components will be traced and where the tracing output is sent.</span></span>

## <span data-ttu-id="23764-113">예제</span><span class="sxs-lookup"><span data-stu-id="23764-113">EXAMPLES</span></span>

### <span data-ttu-id="23764-114">예제 1: ParameterBinding 구성 요소 추적</span><span class="sxs-lookup"><span data-stu-id="23764-114">Example 1: Trace the ParameterBinding component</span></span>

```
PS C:\> Set-TraceSource -Name "ParameterBinding" -Option ExecutionFlow -PSHost -ListenerOption "ProcessId,TimeStamp"
```

<span data-ttu-id="23764-115">이 명령은 PowerShell의 ParameterBinding 구성 요소에 대 한 추적을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="23764-115">This command starts tracing for the ParameterBinding component of PowerShell.</span></span>
<span data-ttu-id="23764-116">*Name* 매개 변수를 사용 하 여 추적 원본을 지정 하 고 *Option* 매개 변수를 사용 하 여 executionflow 추적 이벤트를 선택 하 고 *PSHost* 매개 변수를 사용 하 여 출력을 콘솔로 보내는 PowerShell 호스트 수신기를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="23764-116">It uses the *Name* parameter to specify the trace source, the *Option* parameter to select the ExecutionFlow trace events, and the *PSHost* parameter to select the PowerShell host listener, which sends the output to the console.</span></span>
<span data-ttu-id="23764-117">*ListenerOption* 매개 변수는 추적 메시지 접두사에 ProcessID 및 TimeStamp 값을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="23764-117">The *ListenerOption* parameter adds the ProcessID and TimeStamp values to the trace message prefix.</span></span>

### <span data-ttu-id="23764-118">예 2: 추적 중지</span><span class="sxs-lookup"><span data-stu-id="23764-118">Example 2: Stop a trace</span></span>

```
PS C:\> Set-TraceSource -Name "ParameterBinding" -RemoveListener "Host"
```

<span data-ttu-id="23764-119">이 명령은 PowerShell의 ParameterBinding 구성 요소에 대 한 추적을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="23764-119">This command stops the trace of the ParameterBinding component of PowerShell.</span></span>
<span data-ttu-id="23764-120">*Name* 매개 변수를 사용 하 여 추적 중인 구성 요소를 식별 하 고 *RemoveListener* 매개 변수를 사용 하 여 추적 수신기를 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="23764-120">It uses the *Name* parameter to identify the component that was being traced and the *RemoveListener* parameter to identify the trace listener.</span></span>

## <span data-ttu-id="23764-121">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="23764-121">PARAMETERS</span></span>

### <span data-ttu-id="23764-122">-디버거</span><span class="sxs-lookup"><span data-stu-id="23764-122">-Debugger</span></span>

<span data-ttu-id="23764-123">Cmdlet이 추적 출력을 디버거로 보낼지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="23764-123">Indicates that the cmdlet sends the trace output to the debugger.</span></span>
<span data-ttu-id="23764-124">사용자 모드 또는 커널 모드 디버거나 Microsoft Visual Studio에서 출력을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23764-124">You can view the output in any user-mode or kernel mode debugger or in Microsoft Visual Studio.</span></span>
<span data-ttu-id="23764-125">이 매개 변수는 기본 추적 수신기도 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="23764-125">This parameter also selects the default trace listener.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: optionsSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="23764-126">-FilePath</span><span class="sxs-lookup"><span data-stu-id="23764-126">-FilePath</span></span>

<span data-ttu-id="23764-127">이 cmdlet이 추적 출력을 전송 하는 파일을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="23764-127">Specifies a file that this cmdlet sends the trace output to.</span></span>
<span data-ttu-id="23764-128">이 매개 변수는 파일 추적 수신기도 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="23764-128">This parameter also selects the file trace listener.</span></span>
<span data-ttu-id="23764-129">이 매개 변수를 사용 하 여 추적을 시작 하는 경우 *Removefilelistener* 매개 변수를 사용 하 여 추적을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="23764-129">If you use this parameter to start the trace, use the *RemoveFileListener* parameter to stop the trace.</span></span>

```yaml
Type: System.String
Parameter Sets: optionsSet
Aliases: PSPath, Path

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="23764-130">-Force</span><span class="sxs-lookup"><span data-stu-id="23764-130">-Force</span></span>

<span data-ttu-id="23764-131">Cmdlet이 읽기 전용 파일을 덮어쓰도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="23764-131">Indicates that the cmdlet overwrites a read-only file.</span></span>
<span data-ttu-id="23764-132">*FilePath* 매개 변수와 함께 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="23764-132">Use with the *FilePath* parameter.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: optionsSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="23764-133">-ListenerOption</span><span class="sxs-lookup"><span data-stu-id="23764-133">-ListenerOption</span></span>

<span data-ttu-id="23764-134">출력에서 각 추적 메시지의 접두사에 대 한 선택적 데이터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="23764-134">Specifies optional data to the prefix of each trace message in the output.</span></span>
<span data-ttu-id="23764-135">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="23764-135">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="23764-136">없음</span><span class="sxs-lookup"><span data-stu-id="23764-136">None</span></span>
- <span data-ttu-id="23764-137">LogicalOperationStack</span><span class="sxs-lookup"><span data-stu-id="23764-137">LogicalOperationStack</span></span>
- <span data-ttu-id="23764-138">DateTime</span><span class="sxs-lookup"><span data-stu-id="23764-138">DateTime</span></span>
- <span data-ttu-id="23764-139">타임스탬프</span><span class="sxs-lookup"><span data-stu-id="23764-139">Timestamp</span></span>
- <span data-ttu-id="23764-140">ProcessId</span><span class="sxs-lookup"><span data-stu-id="23764-140">ProcessId</span></span>
- <span data-ttu-id="23764-141">스레드 Id</span><span class="sxs-lookup"><span data-stu-id="23764-141">ThreadId</span></span>
- <span data-ttu-id="23764-142">호출 스택</span><span class="sxs-lookup"><span data-stu-id="23764-142">Callstack</span></span>

<span data-ttu-id="23764-143">기본값은 없음입니다.</span><span class="sxs-lookup"><span data-stu-id="23764-143">None is the default.</span></span>

<span data-ttu-id="23764-144">여러 옵션을 지정하려면 "ProcessID,ThreadID"와 같이 공백 없이 쉼표로 구분하고 따옴표로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="23764-144">To specify multiple options, separate them with commas, but with no spaces, and enclose them in quotation marks, such as "ProcessID,ThreadID".</span></span>

```yaml
Type: System.Diagnostics.TraceOptions
Parameter Sets: optionsSet
Aliases:
Accepted values: None, LogicalOperationStack, DateTime, Timestamp, ProcessId, ThreadId, Callstack

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="23764-145">-Name</span><span class="sxs-lookup"><span data-stu-id="23764-145">-Name</span></span>

<span data-ttu-id="23764-146">추적할 구성 요소를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="23764-146">Specifies which components are traced.</span></span>
<span data-ttu-id="23764-147">각 구성 요소의 추적 원본 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="23764-147">Enter the name of the trace source of each component.</span></span>
<span data-ttu-id="23764-148">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="23764-148">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="23764-149">-옵션</span><span class="sxs-lookup"><span data-stu-id="23764-149">-Option</span></span>

<span data-ttu-id="23764-150">추적 되는 이벤트의 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="23764-150">Specifies the type of events that are traced.</span></span>
<span data-ttu-id="23764-151">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="23764-151">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="23764-152">없음</span><span class="sxs-lookup"><span data-stu-id="23764-152">None</span></span>
- <span data-ttu-id="23764-153">생성자</span><span class="sxs-lookup"><span data-stu-id="23764-153">Constructor</span></span>
- <span data-ttu-id="23764-154">Dispose</span><span class="sxs-lookup"><span data-stu-id="23764-154">Dispose</span></span>
- <span data-ttu-id="23764-155">Finalizer</span><span class="sxs-lookup"><span data-stu-id="23764-155">Finalizer</span></span>
- <span data-ttu-id="23764-156">메서드</span><span class="sxs-lookup"><span data-stu-id="23764-156">Method</span></span>
- <span data-ttu-id="23764-157">속성</span><span class="sxs-lookup"><span data-stu-id="23764-157">Property</span></span>
- <span data-ttu-id="23764-158">대리자</span><span class="sxs-lookup"><span data-stu-id="23764-158">Delegates</span></span>
- <span data-ttu-id="23764-159">이벤트</span><span class="sxs-lookup"><span data-stu-id="23764-159">Events</span></span>
- <span data-ttu-id="23764-160">예외</span><span class="sxs-lookup"><span data-stu-id="23764-160">Exception</span></span>
- <span data-ttu-id="23764-161">잠금</span><span class="sxs-lookup"><span data-stu-id="23764-161">Lock</span></span>
- <span data-ttu-id="23764-162">오류</span><span class="sxs-lookup"><span data-stu-id="23764-162">Error</span></span>
- <span data-ttu-id="23764-163">오류</span><span class="sxs-lookup"><span data-stu-id="23764-163">Errors</span></span>
- <span data-ttu-id="23764-164">경고</span><span class="sxs-lookup"><span data-stu-id="23764-164">Warning</span></span>
- <span data-ttu-id="23764-165">자세히</span><span class="sxs-lookup"><span data-stu-id="23764-165">Verbose</span></span>
- <span data-ttu-id="23764-166">WriteLine</span><span class="sxs-lookup"><span data-stu-id="23764-166">WriteLine</span></span>
- <span data-ttu-id="23764-167">데이터</span><span class="sxs-lookup"><span data-stu-id="23764-167">Data</span></span>
- <span data-ttu-id="23764-168">Scope</span><span class="sxs-lookup"><span data-stu-id="23764-168">Scope</span></span>
- <span data-ttu-id="23764-169">ExecutionFlow</span><span class="sxs-lookup"><span data-stu-id="23764-169">ExecutionFlow</span></span>
- <span data-ttu-id="23764-170">Assert</span><span class="sxs-lookup"><span data-stu-id="23764-170">Assert</span></span>
- <span data-ttu-id="23764-171">모두</span><span class="sxs-lookup"><span data-stu-id="23764-171">All</span></span>

<span data-ttu-id="23764-172">All이 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="23764-172">All is the default.</span></span>

<span data-ttu-id="23764-173">다음 값은 다른 값의 조합입니다.</span><span class="sxs-lookup"><span data-stu-id="23764-173">The following values are combinations of other values:</span></span>

- <span data-ttu-id="23764-174">ExecutionFlow: (Constructor, Dispose, Finalizer, Method, 대리자, 이벤트 및 범위)</span><span class="sxs-lookup"><span data-stu-id="23764-174">ExecutionFlow: (Constructor, Dispose, Finalizer, Method, Delegates, Events, and Scope)</span></span>
- <span data-ttu-id="23764-175">데이터: (Constructor, Dispose, Finalizer, Property, Verbose 및 WriteLine)</span><span class="sxs-lookup"><span data-stu-id="23764-175">Data: (Constructor, Dispose, Finalizer, Property, Verbose, and WriteLine)</span></span>
- <span data-ttu-id="23764-176">오류: (오류 및 예외).</span><span class="sxs-lookup"><span data-stu-id="23764-176">Errors: (Error and Exception).</span></span>

<span data-ttu-id="23764-177">여러 옵션을 지정하려면 "Constructor,Dispose"와 같이 공백 없이 쉼표로 구분하고 따옴표로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="23764-177">To specify multiple options, separate them with commas, but with no spaces, and enclose them in quotation marks, such as "Constructor,Dispose".</span></span>

```yaml
Type: System.Management.Automation.PSTraceSourceOptions
Parameter Sets: optionsSet
Aliases:
Accepted values: None, Constructor, Dispose, Finalizer, Method, Property, Delegates, Events, Exception, Lock, Error, Errors, Warning, Verbose, WriteLine, Data, Scope, ExecutionFlow, Assert, All

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="23764-178">-PassThru</span><span class="sxs-lookup"><span data-stu-id="23764-178">-PassThru</span></span>

<span data-ttu-id="23764-179">작업 중인 항목을 나타내는 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="23764-179">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="23764-180">기본적으로 이 cmdlet은 출력을 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="23764-180">By default, this cmdlet does not generate any output.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: optionsSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="23764-181">-PSHost</span><span class="sxs-lookup"><span data-stu-id="23764-181">-PSHost</span></span>

<span data-ttu-id="23764-182">이 cmdlet은 PowerShell 호스트로 추적 출력을 ndicates 합니다.</span><span class="sxs-lookup"><span data-stu-id="23764-182">ndicates that this cmdlet sends the trace output to the PowerShell host.</span></span>
<span data-ttu-id="23764-183">이 매개 변수는 PSHost 추적 수신기도 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="23764-183">This parameter also selects the PSHost trace listener.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: optionsSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="23764-184">-RemoveFileListener</span><span class="sxs-lookup"><span data-stu-id="23764-184">-RemoveFileListener</span></span>

<span data-ttu-id="23764-185">지정된 파일과 연결된 파일 추적 수신기를 제거하여 추적을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="23764-185">Stops the trace by removing the file trace listener associated with the specified file.</span></span>
<span data-ttu-id="23764-186">추적 출력 파일의 경로와 파일 이름을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="23764-186">Enter the path and file name of the trace output file.</span></span>

```yaml
Type: System.String[]
Parameter Sets: removeFileListenersSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="23764-187">-RemoveListener</span><span class="sxs-lookup"><span data-stu-id="23764-187">-RemoveListener</span></span>

<span data-ttu-id="23764-188">추적 수신기를 제거하여 추적을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="23764-188">Stops the trace by removing the trace listener.</span></span>

<span data-ttu-id="23764-189">*RemoveListener* 에 다음 값을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="23764-189">Use the following values with *RemoveListener* :</span></span>

- <span data-ttu-id="23764-190">PSHost (콘솔)를 제거 하려면을 입력 `Host` 합니다.</span><span class="sxs-lookup"><span data-stu-id="23764-190">To remove PSHost (console), type `Host`.</span></span>
- <span data-ttu-id="23764-191">디버거를 제거 하려면을 입력 `Debug` 합니다.</span><span class="sxs-lookup"><span data-stu-id="23764-191">To remove Debugger, type `Debug`.</span></span>
- <span data-ttu-id="23764-192">모든 추적 수신기를 제거 하려면을 입력 `*` 합니다.</span><span class="sxs-lookup"><span data-stu-id="23764-192">To remove all trace listeners, type `*`.</span></span>

<span data-ttu-id="23764-193">파일 추적 수신기를 제거 하려면 *Removefilelistener* 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="23764-193">To remove the file trace listener, use the *RemoveFileListener* parameter.</span></span>

```yaml
Type: System.String[]
Parameter Sets: removeAllListenersSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="23764-194">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="23764-194">CommonParameters</span></span>

<span data-ttu-id="23764-195">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="23764-195">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="23764-196">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="23764-196">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="23764-197">입력</span><span class="sxs-lookup"><span data-stu-id="23764-197">INPUTS</span></span>

### <span data-ttu-id="23764-198">System.String</span><span class="sxs-lookup"><span data-stu-id="23764-198">System.String</span></span>

<span data-ttu-id="23764-199">이름이 포함 된 문자열을 **TraceSource** 로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23764-199">You can pipe a string that contains a name to **Set-TraceSource** .</span></span>

## <span data-ttu-id="23764-200">출력</span><span class="sxs-lookup"><span data-stu-id="23764-200">OUTPUTS</span></span>

### <span data-ttu-id="23764-201">None 또는 System.object입니다.</span><span class="sxs-lookup"><span data-stu-id="23764-201">None or System.Management.Automation.PSTraceSource</span></span>

<span data-ttu-id="23764-202">*PassThru* 매개 변수를 사용 하는 경우 **TraceSource** 는 추적 세션을 나타내는 **system.object** 를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="23764-202">When you use the *PassThru* parameter, **Set-TraceSource** generates a **System.Management.Automation.PSTraceSource** object representing the trace session.</span></span>
<span data-ttu-id="23764-203">그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="23764-203">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="23764-204">참고</span><span class="sxs-lookup"><span data-stu-id="23764-204">NOTES</span></span>

* <span data-ttu-id="23764-205">추적은 개발자가 디버깅하고 프로그램을 다듬는 데 사용하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="23764-205">Tracing is a method that developers use to debug and refine programs.</span></span> <span data-ttu-id="23764-206">추적하면 프로그램에서 내부 프로세스의 각 단계에 대한 세부 메시지를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="23764-206">When tracing, the program generates detailed messages about each step in its internal processing.</span></span>

  <span data-ttu-id="23764-207">Powershell 추적 cmdlet은 PowerShell 개발자를 돕기 위해 설계 되었지만 모든 사용자가 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23764-207">The PowerShell tracing cmdlets are designed to help PowerShell developers, but they are available to all users.</span></span>
<span data-ttu-id="23764-208">이를 통해 PowerShell 기능의 거의 모든 측면을 모니터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23764-208">They let you monitor nearly every aspect of the functionality of PowerShell.</span></span>

  <span data-ttu-id="23764-209">추적 소스는 추적을 관리 하 고 구성 요소에 대 한 추적 메시지를 생성 하는 각 PowerShell 구성 요소의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="23764-209">A trace source is the part of each PowerShell component that manages tracing and generates trace messages for the component.</span></span>
<span data-ttu-id="23764-210">구성 요소를 추적하려면 추적 원본을 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="23764-210">To trace a component, you identify its trace source.</span></span>

  <span data-ttu-id="23764-211">추적 수신기는 추적의 출력을 받아 사용자에 게 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="23764-211">A trace listener receives the output of the trace and displays it to the user.</span></span>
<span data-ttu-id="23764-212">사용자 모드 또는 커널 모드 디버거, 콘솔, 파일 또는 **TraceListener** 클래스에서 파생 된 사용자 지정 수신기로 추적 데이터를 보내도록 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23764-212">You can elect to send the trace data to a user-mode or kernel-mode debugger, to the console, to a file, or to a custom listener derived from the **System.Diagnostics.TraceListener** class.</span></span>

* <span data-ttu-id="23764-213">추적을 시작 하려면 *Name* 매개 변수를 사용 하 여 추적 소스를 지정 하 고 *FilePath* , *Debugger* 또는 *PSHost* 매개 변수를 사용 하 여 수신기 (출력의 대상)를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="23764-213">To start a trace, use the *Name* parameter to specify a trace source and the *FilePath* , *Debugger* , or *PSHost* parameters to specify a listener (a destination for the output).</span></span> <span data-ttu-id="23764-214">*Options* 매개 변수를 사용 하 여 추적 되는 이벤트 유형을 확인 하 고 *ListenerOption* 매개 변수를 사용 하 여 추적 출력을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="23764-214">Use the *Options* parameter to determine the types of events that are traced and the *ListenerOption* parameter to configure the trace output.</span></span>
* <span data-ttu-id="23764-215">추적의 구성을 변경 하려면 **TraceSource** 명령을 입력 하 여 추적을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="23764-215">To change the configuration of a trace, enter a **Set-TraceSource** command as you would to start a trace.</span></span> <span data-ttu-id="23764-216">PowerShell에서 추적 원본이 이미 추적 되 고 있음을 인식 합니다.</span><span class="sxs-lookup"><span data-stu-id="23764-216">PowerShell recognizes that the trace source is already being traced.</span></span> <span data-ttu-id="23764-217">그다음 추적을 중지하고 새 구성을 추가한 다음 추적을 시작하거나 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="23764-217">It stops the trace, adds the new configuration, and starts or restarts the trace.</span></span>
* <span data-ttu-id="23764-218">추적을 중지 하려면 *RemoveListener* 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="23764-218">To stop a trace, use the *RemoveListener* parameter.</span></span> <span data-ttu-id="23764-219">파일 수신기를 사용 하는 추적 ( *FilePath* 매개 변수를 사용 하 여 시작 된 추적)을 중지 하려면 *removefilelistener* 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="23764-219">To stop a trace that uses the file listener (a trace started by using the *FilePath* parameter), use the *RemoveFileListener* parameter.</span></span> <span data-ttu-id="23764-220">수신기를 제거하면 추적이 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="23764-220">When you remove the listener, the trace stops.</span></span>
* <span data-ttu-id="23764-221">추적할 수 있는 구성 요소를 확인하려면 Get-TraceSource를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="23764-221">To determine which components can be traced, use Get-TraceSource.</span></span> <span data-ttu-id="23764-222">각 모듈에 대 한 추적 소스는 구성 요소가 사용 중일 때 자동으로 로드 되며 **TraceSource** 의 출력에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="23764-222">The trace sources for each module are loaded automatically when the component is in use, and they appear in the output of **Get-TraceSource** .</span></span>

## <span data-ttu-id="23764-223">관련 링크</span><span class="sxs-lookup"><span data-stu-id="23764-223">RELATED LINKS</span></span>

[<span data-ttu-id="23764-224">Get-TraceSource</span><span class="sxs-lookup"><span data-stu-id="23764-224">Get-TraceSource</span></span>](Get-TraceSource.md)

[<span data-ttu-id="23764-225">Trace-Command</span><span class="sxs-lookup"><span data-stu-id="23764-225">Trace-Command</span></span>](Trace-Command.md)

