---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/debug-process?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Debug-Process
ms.openlocfilehash: 1cc0b0f51d84f3471bc3f54a91daba10f3528a8a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93215537"
---
# <span data-ttu-id="c2b62-103">Debug-Process</span><span class="sxs-lookup"><span data-stu-id="c2b62-103">Debug-Process</span></span>

## <span data-ttu-id="c2b62-104">개요</span><span class="sxs-lookup"><span data-stu-id="c2b62-104">SYNOPSIS</span></span>
<span data-ttu-id="c2b62-105">로컬 컴퓨터에서 실행 중인 하나 이상의 프로세스를 디버그합니다.</span><span class="sxs-lookup"><span data-stu-id="c2b62-105">Debugs one or more processes running on the local computer.</span></span>

## <span data-ttu-id="c2b62-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c2b62-106">SYNTAX</span></span>

### <span data-ttu-id="c2b62-107">이름 (기본값)</span><span class="sxs-lookup"><span data-stu-id="c2b62-107">Name (Default)</span></span>

```
Debug-Process [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="c2b62-108">Id</span><span class="sxs-lookup"><span data-stu-id="c2b62-108">Id</span></span>

```
Debug-Process [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="c2b62-109">InputObject</span><span class="sxs-lookup"><span data-stu-id="c2b62-109">InputObject</span></span>

```
Debug-Process -InputObject <Process[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="c2b62-110">설명</span><span class="sxs-lookup"><span data-stu-id="c2b62-110">DESCRIPTION</span></span>
<span data-ttu-id="c2b62-111">**디버그 프로세스** cmdlet은 로컬 컴퓨터에서 실행 중인 하나 이상의 프로세스에 디버거를 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2b62-111">The **Debug-Process** cmdlet attaches a debugger to one or more running processes on a local computer.</span></span>
<span data-ttu-id="c2b62-112">프로세스 이름 또는 프로세스 ID (PID)로 프로세스를 지정 하거나 프로세스 개체를이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2b62-112">You can specify the processes by their process name or process ID (PID), or you can pipe process objects to this cmdlet.</span></span>

<span data-ttu-id="c2b62-113">이 cmdlet은 프로세스에 대해 현재 등록 된 디버거를 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2b62-113">This cmdlet attaches the debugger that is currently registered for the process.</span></span>
<span data-ttu-id="c2b62-114">이 cmdlet을 사용하기 전에 디버거가 다운로드되었으며 올바르게 구성되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="c2b62-114">Before using this cmdlet, verify that a debugger is downloaded and correctly configured.</span></span>

## <span data-ttu-id="c2b62-115">예제</span><span class="sxs-lookup"><span data-stu-id="c2b62-115">EXAMPLES</span></span>

### <span data-ttu-id="c2b62-116">예제 1: 컴퓨터의 프로세스에 디버거 연결</span><span class="sxs-lookup"><span data-stu-id="c2b62-116">Example 1: Attach a debugger to a process on the computer</span></span>

```
PS C:\> Debug-Process -Name "Windows Powershell"
```

<span data-ttu-id="c2b62-117">이 명령은 컴퓨터의 Windows PowerShell 프로세스에 디버거를 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2b62-117">This command attaches a debugger to the Windows PowerShell process on the computer.</span></span>

### <span data-ttu-id="c2b62-118">예제 2: 지정 된 문자열로 시작 하는 모든 프로세스에 디버거 연결</span><span class="sxs-lookup"><span data-stu-id="c2b62-118">Example 2: Attach a debugger to all processes that begin with the specified string</span></span>

```
PS C:\> Debug-Process -Name "SQL*"
```

<span data-ttu-id="c2b62-119">이 명령은 이름이 SQL로 시작 하는 모든 프로세스에 디버거를 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2b62-119">This command attaches a debugger to all processes that have names that begin with SQL.</span></span>

### <span data-ttu-id="c2b62-120">예제 3: 여러 프로세스에 디버거 연결</span><span class="sxs-lookup"><span data-stu-id="c2b62-120">Example 3: Attach a debugger to multiple processes</span></span>

```
PS C:\> Debug-Process "Winlogon", "Explorer", "Outlook"
```

<span data-ttu-id="c2b62-121">이 명령은 Winlogon, Explorer 및 Outlook 프로세스에 디버거를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="c2b62-121">This command attaches a debugger to the Winlogon, Explorer, and Outlook processes.</span></span>

### <span data-ttu-id="c2b62-122">예제 4: 여러 프로세스 Id에 디버거 연결</span><span class="sxs-lookup"><span data-stu-id="c2b62-122">Example 4: Attach a debugger to multiple process IDs</span></span>

```
PS C:\> Debug-Process -Id 1132, 2028
```

<span data-ttu-id="c2b62-123">이 명령은 프로세스 ID가 1132 및 2028인 프로세스에 디버거를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="c2b62-123">This command attaches a debugger to the processes that have process IDs 1132 and 2028.</span></span>

### <span data-ttu-id="c2b62-124">예 5: Get-Process을 사용 하 여 프로세스를 가져온 다음 디버거를 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2b62-124">Example 5: Use Get-Process to get a process then attach a debugger to it</span></span>

```
PS C:\> Get-Process "Windows PowerShell" | Debug-Process
```

<span data-ttu-id="c2b62-125">이 명령은 컴퓨터의 Windows PowerShell 프로세스에 디버거를 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2b62-125">This command attaches a debugger to the Windows PowerShell processes on the computer.</span></span>
<span data-ttu-id="c2b62-126">이 cmdlet은 **Get Process** cmdlet을 사용 하 여 컴퓨터의 Windows PowerShell 프로세스를 가져온 다음 파이프라인 연산자 (|)를 사용 하 여 프로세스를 **디버그 프로세스** cmdlet으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="c2b62-126">It uses the **Get-Process** cmdlet to get the Windows PowerShell processes on the computer, and it uses a pipeline operator (|) to send the processes to the **Debug-Process** cmdlet.</span></span>

<span data-ttu-id="c2b62-127">특정 PowerShell 프로세스를 지정 하려면 **Get process** 의 ID 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2b62-127">To specify a particular PowerShell process, use the ID parameter of **Get-Process** .</span></span>

### <span data-ttu-id="c2b62-128">예제 6: 로컬 컴퓨터의 현재 프로세스에 디버거 연결</span><span class="sxs-lookup"><span data-stu-id="c2b62-128">Example 6: Attach a debugger to a current process on the local computer</span></span>

```
PS C:\> $PID | Debug-Process
```

<span data-ttu-id="c2b62-129">이 명령은 컴퓨터의 현재 Windows PowerShell 프로세스에 디버거를 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2b62-129">This command attaches a debugger to the current Windows PowerShell processes on the computer.</span></span>

<span data-ttu-id="c2b62-130">이 명령은 현재 Windows PowerShell 프로세스의 프로세스 ID를 포함 하는 $PID 자동 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2b62-130">The command uses the $PID automatic variable, which contains the process ID of the current Windows PowerShell process.</span></span>
<span data-ttu-id="c2b62-131">그런 다음 파이프라인 연산자 (|)를 사용 하 여 프로세스 ID를 **디버그 프로세스** cmdlet으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="c2b62-131">Then, it uses a pipeline operator (|) to send the process ID to the **Debug-Process** cmdlet.</span></span>

<span data-ttu-id="c2b62-132">$PID 자동 변수에 대 한 자세한 내용은 about_Automatic_Variables을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c2b62-132">For more information about the $PID automatic variable, see about_Automatic_Variables.</span></span>

### <span data-ttu-id="c2b62-133">예제 7: 여러 컴퓨터의 지정 된 프로세스에 디버거 연결</span><span class="sxs-lookup"><span data-stu-id="c2b62-133">Example 7: Attach a debugger to the specified process on multiple computers</span></span>

```
PS C:\> Get-Process -ComputerName "Server01", "Server02" -Name "MyApp" | Debug-Process
```

<span data-ttu-id="c2b62-134">이 명령은 Server01 및 Server02 컴퓨터의 MyApp 프로세스에 디버거를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="c2b62-134">This command attaches a debugger to the MyApp processes on the Server01 and Server02 computers.</span></span>

<span data-ttu-id="c2b62-135">이 명령은 Server01 및 Server02 컴퓨터의 MyApp 프로세스를 가져오기 위해 **Get Process** cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2b62-135">The command uses the **Get-Process** cmdlet to get the MyApp processes on the Server01 and Server02 computers.</span></span>
<span data-ttu-id="c2b62-136">파이프라인 연산자를 사용하여 프로세스를 Debug-Process cmdlet으로 보내면 이 cmdlet이 디버거를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="c2b62-136">It uses a pipeline operator to send the processes to the Debug-Process cmdlet, which attaches the debuggers.</span></span>

### <span data-ttu-id="c2b62-137">예 8: InputObject 매개 변수를 사용 하는 프로세스에 디버거 연결</span><span class="sxs-lookup"><span data-stu-id="c2b62-137">Example 8: Attach a debugger to a process that uses the InputObject parameter</span></span>

```
PS C:\> $P = Get-Process "Windows PowerShell"
PS C:\> Debug-Process -InputObject $P
```

<span data-ttu-id="c2b62-138">이 명령은 로컬 컴퓨터의 Windows PowerShell 프로세스에 디버거를 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2b62-138">This command attaches a debugger to the Windows PowerShell processes on the local computer.</span></span>

<span data-ttu-id="c2b62-139">첫 번째 명령은 **Get Process** cmdlet을 사용 하 여 컴퓨터의 Windows PowerShell 프로세스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c2b62-139">The first command uses the **Get-Process** cmdlet to get the Windows PowerShell processes on the computer.</span></span>
<span data-ttu-id="c2b62-140">결과 프로세스 개체를 $P 라는 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2b62-140">It saves the resulting process object in the variable named $P.</span></span>

<span data-ttu-id="c2b62-141">두 번째 명령은 **디버그 프로세스** Cmdlet의 *InputObject* 매개 변수를 사용 하 여 $P 변수에 프로세스 개체를 제출 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2b62-141">The second command uses the *InputObject* parameter of the **Debug-Process** cmdlet to submit the process object in the $P variable.</span></span>

## <span data-ttu-id="c2b62-142">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c2b62-142">PARAMETERS</span></span>

### <span data-ttu-id="c2b62-143">-Id</span><span class="sxs-lookup"><span data-stu-id="c2b62-143">-Id</span></span>
<span data-ttu-id="c2b62-144">디버그할 프로세스의 프로세스 ID를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c2b62-144">Specifies the process IDs of the processes to be debugged.</span></span>
<span data-ttu-id="c2b62-145">*Id* 매개 변수 이름은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="c2b62-145">The *Id* parameter name is optional.</span></span>

<span data-ttu-id="c2b62-146">프로세스의 프로세스 ID를 찾으려면를 입력 `Get-Process` 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2b62-146">To find the process ID of a process, type `Get-Process`.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases: PID, ProcessId

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c2b62-147">-InputObject</span><span class="sxs-lookup"><span data-stu-id="c2b62-147">-InputObject</span></span>
<span data-ttu-id="c2b62-148">디버그할 프로세스를 나타내는 프로세스 개체를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c2b62-148">Specifies the process objects that represent processes to be debugged.</span></span>
<span data-ttu-id="c2b62-149">프로세스 개체가 포함 된 변수를 입력 하거나 프로세스 개체를 가져오는 명령 (예: Get-Process cmdlet)을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2b62-149">Enter a variable that contains the process objects or a command that gets the process objects, such as the Get-Process cmdlet.</span></span>
<span data-ttu-id="c2b62-150">프로세스 개체를이 cmdlet으로 파이프 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2b62-150">You can also pipe process objects to this cmdlet.</span></span>

```yaml
Type: System.Diagnostics.Process[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="c2b62-151">-Name</span><span class="sxs-lookup"><span data-stu-id="c2b62-151">-Name</span></span>
<span data-ttu-id="c2b62-152">디버그할 프로세스의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c2b62-152">Specifies the names of the processes to be debugged.</span></span>
<span data-ttu-id="c2b62-153">이름이 같은 프로세스가 둘 이상 있는 경우이 cmdlet은 해당 이름을 가진 모든 프로세스에 디버거를 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2b62-153">If there is more than one process with the same name, this cmdlet attaches a debugger to all processes with that name.</span></span>
<span data-ttu-id="c2b62-154">*Name* 매개 변수는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="c2b62-154">The *Name* parameter is optional.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases: ProcessName

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c2b62-155">-Confirm</span><span class="sxs-lookup"><span data-stu-id="c2b62-155">-Confirm</span></span>
<span data-ttu-id="c2b62-156">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="c2b62-156">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="c2b62-157">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="c2b62-157">-WhatIf</span></span>
<span data-ttu-id="c2b62-158">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="c2b62-158">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="c2b62-159">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c2b62-159">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="c2b62-160">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c2b62-160">CommonParameters</span></span>
<span data-ttu-id="c2b62-161">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c2b62-161">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c2b62-162">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c2b62-162">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c2b62-163">입력</span><span class="sxs-lookup"><span data-stu-id="c2b62-163">INPUTS</span></span>

### <span data-ttu-id="c2b62-164">System.string, system.web. Process, System.string</span><span class="sxs-lookup"><span data-stu-id="c2b62-164">System.Int32, System.Diagnostics.Process, System.String</span></span>
<span data-ttu-id="c2b62-165">프로세스 ID (Int32), 프로세스 개체 (System.web) 또는 프로세스 이름 (문자열)을이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2b62-165">You can pipe a process ID (Int32), a process object (System.Diagnostics.Process), or a process name (String) to this cmdlet.</span></span>

## <span data-ttu-id="c2b62-166">출력</span><span class="sxs-lookup"><span data-stu-id="c2b62-166">OUTPUTS</span></span>

### <span data-ttu-id="c2b62-167">없음</span><span class="sxs-lookup"><span data-stu-id="c2b62-167">None</span></span>
<span data-ttu-id="c2b62-168">이 cmdlet은 어떠한 출력도 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c2b62-168">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="c2b62-169">참고</span><span class="sxs-lookup"><span data-stu-id="c2b62-169">NOTES</span></span>

* <span data-ttu-id="c2b62-170">이 cmdlet은 WMI(Windows Management Instrumentation) Win32_Process 클래스의 AttachDebugger 메서드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c2b62-170">This cmdlet uses the AttachDebugger method of the Windows Management Instrumentation (WMI) Win32_Process class.</span></span> <span data-ttu-id="c2b62-171">이 메서드에 대 한 자세한 내용은 MSDN library에서 [AttachDebugger 메서드](https://go.microsoft.com/fwlink/?LinkId=143640) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c2b62-171">For more information about this method, see [AttachDebugger method](https://go.microsoft.com/fwlink/?LinkId=143640) in the MSDN library.</span></span>

## <span data-ttu-id="c2b62-172">관련 링크</span><span class="sxs-lookup"><span data-stu-id="c2b62-172">RELATED LINKS</span></span>

[<span data-ttu-id="c2b62-173">Debug-Process</span><span class="sxs-lookup"><span data-stu-id="c2b62-173">Debug-Process</span></span>](Debug-Process.md)

[<span data-ttu-id="c2b62-174">Get-Process</span><span class="sxs-lookup"><span data-stu-id="c2b62-174">Get-Process</span></span>](Get-Process.md)

[<span data-ttu-id="c2b62-175">Start-Process</span><span class="sxs-lookup"><span data-stu-id="c2b62-175">Start-Process</span></span>](Start-Process.md)

[<span data-ttu-id="c2b62-176">Stop-Process</span><span class="sxs-lookup"><span data-stu-id="c2b62-176">Stop-Process</span></span>](Stop-Process.md)

[<span data-ttu-id="c2b62-177">Wait-Process</span><span class="sxs-lookup"><span data-stu-id="c2b62-177">Wait-Process</span></span>](Wait-Process.md)
