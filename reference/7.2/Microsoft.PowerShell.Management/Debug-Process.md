---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/debug-process?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Debug-Process
ms.openlocfilehash: 660d2b4845df8091ff8b69b28c4e7695af557122
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599757"
---
# <span data-ttu-id="0b25f-102">Debug-Process</span><span class="sxs-lookup"><span data-stu-id="0b25f-102">Debug-Process</span></span>

## <span data-ttu-id="0b25f-103">개요</span><span class="sxs-lookup"><span data-stu-id="0b25f-103">SYNOPSIS</span></span>
<span data-ttu-id="0b25f-104">로컬 컴퓨터에서 실행 중인 하나 이상의 프로세스를 디버그합니다.</span><span class="sxs-lookup"><span data-stu-id="0b25f-104">Debugs one or more processes running on the local computer.</span></span>

## <span data-ttu-id="0b25f-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="0b25f-105">SYNTAX</span></span>

### <span data-ttu-id="0b25f-106">이름 (기본값)</span><span class="sxs-lookup"><span data-stu-id="0b25f-106">Name (Default)</span></span>

```
Debug-Process [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="0b25f-107">Id</span><span class="sxs-lookup"><span data-stu-id="0b25f-107">Id</span></span>

```
Debug-Process [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="0b25f-108">InputObject</span><span class="sxs-lookup"><span data-stu-id="0b25f-108">InputObject</span></span>

```
Debug-Process -InputObject <Process[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="0b25f-109">설명</span><span class="sxs-lookup"><span data-stu-id="0b25f-109">DESCRIPTION</span></span>

<span data-ttu-id="0b25f-110">`Debug-Process`Cmdlet은 로컬 컴퓨터에서 실행 중인 하나 이상의 프로세스에 디버거를 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b25f-110">The `Debug-Process` cmdlet attaches a debugger to one or more running processes on a local computer.</span></span>
<span data-ttu-id="0b25f-111">프로세스 이름 또는 프로세스 ID (PID)로 프로세스를 지정 하거나 프로세스 개체를이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b25f-111">You can specify the processes by their process name or process ID (PID), or you can pipe process objects to this cmdlet.</span></span>

<span data-ttu-id="0b25f-112">이 cmdlet은 프로세스에 대해 현재 등록 된 디버거를 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b25f-112">This cmdlet attaches the debugger that is currently registered for the process.</span></span> <span data-ttu-id="0b25f-113">이 cmdlet을 사용하기 전에 디버거가 다운로드되었으며 올바르게 구성되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="0b25f-113">Before using this cmdlet, verify that a debugger is downloaded and correctly configured.</span></span>

## <span data-ttu-id="0b25f-114">예제</span><span class="sxs-lookup"><span data-stu-id="0b25f-114">EXAMPLES</span></span>

### <span data-ttu-id="0b25f-115">예제 1: 컴퓨터의 프로세스에 디버거 연결</span><span class="sxs-lookup"><span data-stu-id="0b25f-115">Example 1: Attach a debugger to a process on the computer</span></span>

```
PS C:\> Debug-Process -Name "Windows Powershell"
```

<span data-ttu-id="0b25f-116">이 명령은 컴퓨터의 PowerShell 프로세스에 디버거를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="0b25f-116">This command attaches a debugger to the PowerShell process on the computer.</span></span>

### <span data-ttu-id="0b25f-117">예제 2: 지정 된 문자열로 시작 하는 모든 프로세스에 디버거 연결</span><span class="sxs-lookup"><span data-stu-id="0b25f-117">Example 2: Attach a debugger to all processes that begin with the specified string</span></span>

```
PS C:\> Debug-Process -Name "SQL*"
```

<span data-ttu-id="0b25f-118">이 명령은 이름이 SQL로 시작 하는 모든 프로세스에 디버거를 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b25f-118">This command attaches a debugger to all processes that have names that begin with SQL.</span></span>

### <span data-ttu-id="0b25f-119">예제 3: 여러 프로세스에 디버거 연결</span><span class="sxs-lookup"><span data-stu-id="0b25f-119">Example 3: Attach a debugger to multiple processes</span></span>

```
PS C:\> Debug-Process "Winlogon", "Explorer", "Outlook"
```

<span data-ttu-id="0b25f-120">이 명령은 Winlogon, Explorer 및 Outlook 프로세스에 디버거를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="0b25f-120">This command attaches a debugger to the Winlogon, Explorer, and Outlook processes.</span></span>

### <span data-ttu-id="0b25f-121">예제 4: 여러 프로세스 Id에 디버거 연결</span><span class="sxs-lookup"><span data-stu-id="0b25f-121">Example 4: Attach a debugger to multiple process IDs</span></span>

```
PS C:\> Debug-Process -Id 1132, 2028
```

<span data-ttu-id="0b25f-122">이 명령은 프로세스 ID가 1132 및 2028인 프로세스에 디버거를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="0b25f-122">This command attaches a debugger to the processes that have process IDs 1132 and 2028.</span></span>

### <span data-ttu-id="0b25f-123">예 5: Get-Process을 사용 하 여 프로세스를 가져온 다음 디버거를 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b25f-123">Example 5: Use Get-Process to get a process then attach a debugger to it</span></span>

```
PS C:\> Get-Process "Windows PowerShell" | Debug-Process
```

<span data-ttu-id="0b25f-124">이 명령은 컴퓨터의 PowerShell 프로세스에 디버거를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="0b25f-124">This command attaches a debugger to the PowerShell processes on the computer.</span></span> <span data-ttu-id="0b25f-125">Cmdlet을 사용 하 여 `Get-Process` 컴퓨터의 PowerShell 프로세스를 가져온 다음 파이프라인 연산자 ()를 사용 하 여 `|` 프로세스를 cmdlet으로 보냅니다 `Debug-Process` .</span><span class="sxs-lookup"><span data-stu-id="0b25f-125">It uses the `Get-Process` cmdlet to get the PowerShell processes on the computer, and it uses a pipeline operator (`|`) to send the processes to the `Debug-Process` cmdlet.</span></span>

<span data-ttu-id="0b25f-126">특정 PowerShell 프로세스를 지정 하려면의 ID 매개 변수를 사용 `Get-Process` 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b25f-126">To specify a particular PowerShell process, use the ID parameter of `Get-Process`.</span></span>

### <span data-ttu-id="0b25f-127">예제 6: 로컬 컴퓨터의 현재 프로세스에 디버거 연결</span><span class="sxs-lookup"><span data-stu-id="0b25f-127">Example 6: Attach a debugger to a current process on the local computer</span></span>

```
PS C:\> $PID | Debug-Process
```

<span data-ttu-id="0b25f-128">이 명령은 컴퓨터의 현재 PowerShell 프로세스에 디버거를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="0b25f-128">This command attaches a debugger to the current PowerShell processes on the computer.</span></span>

<span data-ttu-id="0b25f-129">`$PID`이 명령은 현재 PowerShell 프로세스의 프로세스 ID가 포함 된 자동 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b25f-129">The command uses the `$PID` automatic variable, which contains the process ID of the current PowerShell process.</span></span> <span data-ttu-id="0b25f-130">그런 다음 파이프라인 연산자 ()를 사용 하 여 `|` 프로세스 ID를 cmdlet으로 보냅니다 `Debug-Process` .</span><span class="sxs-lookup"><span data-stu-id="0b25f-130">Then, it uses a pipeline operator (`|`) to send the process ID to the `Debug-Process` cmdlet.</span></span>

<span data-ttu-id="0b25f-131">자동 변수에 대 한 자세한 내용은 `$PID` about_Automatic_Variables를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0b25f-131">For more information about the `$PID` automatic variable, see about_Automatic_Variables.</span></span>

### <span data-ttu-id="0b25f-132">예 7: InputObject 매개 변수를 사용 하는 프로세스에 디버거 연결</span><span class="sxs-lookup"><span data-stu-id="0b25f-132">Example 7: Attach a debugger to a process that uses the InputObject parameter</span></span>

```
PS C:\> $P = Get-Process "Windows PowerShell"
PS C:\> Debug-Process -InputObject $P
```

<span data-ttu-id="0b25f-133">이 명령은 로컬 컴퓨터의 PowerShell 프로세스에 디버거를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="0b25f-133">This command attaches a debugger to the PowerShell processes on the local computer.</span></span>

<span data-ttu-id="0b25f-134">첫 번째 명령은 cmdlet을 사용 하 여 `Get-Process` 컴퓨터의 PowerShell 프로세스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0b25f-134">The first command uses the `Get-Process` cmdlet to get the PowerShell processes on the computer.</span></span> <span data-ttu-id="0b25f-135">결과 프로세스 개체를 이라는 변수에 저장 `$P` 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b25f-135">It saves the resulting process object in the variable named `$P`.</span></span>

<span data-ttu-id="0b25f-136">두 번째 명령은 cmdlet의 **InputObject** 매개 변수를 사용 하 여 `Debug-Process` 변수의 프로세스 개체를 제출 `$P` 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b25f-136">The second command uses the **InputObject** parameter of the `Debug-Process` cmdlet to submit the process object in the `$P` variable.</span></span>

## <span data-ttu-id="0b25f-137">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="0b25f-137">PARAMETERS</span></span>

### <span data-ttu-id="0b25f-138">-Id</span><span class="sxs-lookup"><span data-stu-id="0b25f-138">-Id</span></span>

<span data-ttu-id="0b25f-139">디버그할 프로세스의 프로세스 ID를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0b25f-139">Specifies the process IDs of the processes to be debugged.</span></span> <span data-ttu-id="0b25f-140">**Id** 매개 변수 이름은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="0b25f-140">The **Id** parameter name is optional.</span></span>

<span data-ttu-id="0b25f-141">프로세스의 프로세스 ID를 찾으려면를 입력 `Get-Process` 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b25f-141">To find the process ID of a process, type `Get-Process`.</span></span>

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

### <span data-ttu-id="0b25f-142">-InputObject</span><span class="sxs-lookup"><span data-stu-id="0b25f-142">-InputObject</span></span>

<span data-ttu-id="0b25f-143">디버그할 프로세스를 나타내는 프로세스 개체를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0b25f-143">Specifies the process objects that represent processes to be debugged.</span></span> <span data-ttu-id="0b25f-144">프로세스 개체가 포함 된 변수를 입력 하거나 프로세스 개체를 가져오는 명령 (예: cmdlet)을 입력 합니다 `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="0b25f-144">Enter a variable that contains the process objects or a command that gets the process objects, such as the `Get-Process` cmdlet.</span></span> <span data-ttu-id="0b25f-145">프로세스 개체를이 cmdlet으로 파이프 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b25f-145">You can also pipe process objects to this cmdlet.</span></span>

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

### <span data-ttu-id="0b25f-146">-Name</span><span class="sxs-lookup"><span data-stu-id="0b25f-146">-Name</span></span>

<span data-ttu-id="0b25f-147">디버그할 프로세스의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0b25f-147">Specifies the names of the processes to be debugged.</span></span> <span data-ttu-id="0b25f-148">이름이 같은 프로세스가 둘 이상 있는 경우이 cmdlet은 해당 이름을 가진 모든 프로세스에 디버거를 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b25f-148">If there is more than one process with the same name, this cmdlet attaches a debugger to all processes with that name.</span></span> <span data-ttu-id="0b25f-149">**Name** 매개 변수는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="0b25f-149">The **Name** parameter is optional.</span></span>

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

### <span data-ttu-id="0b25f-150">-Confirm</span><span class="sxs-lookup"><span data-stu-id="0b25f-150">-Confirm</span></span>

<span data-ttu-id="0b25f-151">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="0b25f-151">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="0b25f-152">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="0b25f-152">-WhatIf</span></span>

<span data-ttu-id="0b25f-153">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="0b25f-153">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="0b25f-154">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0b25f-154">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="0b25f-155">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0b25f-155">CommonParameters</span></span>

<span data-ttu-id="0b25f-156">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="0b25f-156">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0b25f-157">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0b25f-157">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="0b25f-158">입력</span><span class="sxs-lookup"><span data-stu-id="0b25f-158">INPUTS</span></span>

### <span data-ttu-id="0b25f-159">System.string, system.web. Process, System.string</span><span class="sxs-lookup"><span data-stu-id="0b25f-159">System.Int32, System.Diagnostics.Process, System.String</span></span>

<span data-ttu-id="0b25f-160">프로세스 ID (Int32), 프로세스 개체 (System.web) 또는 프로세스 이름 (문자열)을이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b25f-160">You can pipe a process ID (Int32), a process object (System.Diagnostics.Process), or a process name (String) to this cmdlet.</span></span>

## <span data-ttu-id="0b25f-161">출력</span><span class="sxs-lookup"><span data-stu-id="0b25f-161">OUTPUTS</span></span>

### <span data-ttu-id="0b25f-162">없음</span><span class="sxs-lookup"><span data-stu-id="0b25f-162">None</span></span>

<span data-ttu-id="0b25f-163">이 cmdlet은 어떠한 출력도 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0b25f-163">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="0b25f-164">참고</span><span class="sxs-lookup"><span data-stu-id="0b25f-164">NOTES</span></span>

<span data-ttu-id="0b25f-165">이 cmdlet은 WMI(Windows Management Instrumentation) Win32_Process 클래스의 AttachDebugger 메서드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0b25f-165">This cmdlet uses the AttachDebugger method of the Windows Management Instrumentation (WMI) Win32_Process class.</span></span> <span data-ttu-id="0b25f-166">이 메서드에 대 한 자세한 내용은 MSDN library에서 [AttachDebugger 메서드](https://go.microsoft.com/fwlink/?LinkId=143640) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0b25f-166">For more information about this method, see [AttachDebugger method](https://go.microsoft.com/fwlink/?LinkId=143640) in the MSDN library.</span></span>

## <span data-ttu-id="0b25f-167">관련 링크</span><span class="sxs-lookup"><span data-stu-id="0b25f-167">RELATED LINKS</span></span>

[<span data-ttu-id="0b25f-168">Debug-Process</span><span class="sxs-lookup"><span data-stu-id="0b25f-168">Debug-Process</span></span>](Debug-Process.md)

[<span data-ttu-id="0b25f-169">Get-Process</span><span class="sxs-lookup"><span data-stu-id="0b25f-169">Get-Process</span></span>](Get-Process.md)

[<span data-ttu-id="0b25f-170">Start-Process</span><span class="sxs-lookup"><span data-stu-id="0b25f-170">Start-Process</span></span>](Start-Process.md)

[<span data-ttu-id="0b25f-171">Stop-Process</span><span class="sxs-lookup"><span data-stu-id="0b25f-171">Stop-Process</span></span>](Stop-Process.md)

[<span data-ttu-id="0b25f-172">Wait-Process</span><span class="sxs-lookup"><span data-stu-id="0b25f-172">Wait-Process</span></span>](Wait-Process.md)
