---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/stop-process?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Process
ms.openlocfilehash: a2f340f0119823ddc0876d86fc38e49edc51fe5d
ms.sourcegitcommit: 11abf355ac545531c2b04217a08ebe6be609c0bb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2020
ms.locfileid: "93220001"
---
# <span data-ttu-id="77d05-103">Stop-Process</span><span class="sxs-lookup"><span data-stu-id="77d05-103">Stop-Process</span></span>

## <span data-ttu-id="77d05-104">개요</span><span class="sxs-lookup"><span data-stu-id="77d05-104">SYNOPSIS</span></span>
<span data-ttu-id="77d05-105">실행 중인 하나 이상의 프로세스를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="77d05-105">Stops one or more running processes.</span></span>

## <span data-ttu-id="77d05-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="77d05-106">SYNTAX</span></span>

### <span data-ttu-id="77d05-107">Id (기본값)</span><span class="sxs-lookup"><span data-stu-id="77d05-107">Id (Default)</span></span>

```
Stop-Process [-Id] <Int32[]> [-PassThru] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="77d05-108">속성</span><span class="sxs-lookup"><span data-stu-id="77d05-108">Name</span></span>

```
Stop-Process -Name <String[]> [-PassThru] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="77d05-109">InputObject</span><span class="sxs-lookup"><span data-stu-id="77d05-109">InputObject</span></span>

```
Stop-Process [-InputObject] <Process[]> [-PassThru] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="77d05-110">설명</span><span class="sxs-lookup"><span data-stu-id="77d05-110">DESCRIPTION</span></span>

<span data-ttu-id="77d05-111">**Stop Process** cmdlet은 실행 중인 하나 이상의 프로세스를 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="77d05-111">The **Stop-Process** cmdlet stops one or more running processes.</span></span>
<span data-ttu-id="77d05-112">프로세스 이름 또는 프로세스 ID (PID)로 프로세스를 지정 하거나 프로세스 개체를 전달 하 여 프로세스를 **중단할** 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77d05-112">You can specify a process by process name or process ID (PID), or pass a process object to **Stop-Process**.</span></span>
<span data-ttu-id="77d05-113">**중지-프로세스** 는 로컬 컴퓨터에서 실행 중인 프로세스 에서만 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="77d05-113">**Stop-Process** works only on processes running on the local computer.</span></span>

<span data-ttu-id="77d05-114">Windows Vista 이상 버전의 Windows 운영 체제에서 현재 사용자가 소유 하지 않은 프로세스를 중지 하려면 관리자 권한으로 실행 옵션을 사용 하 여 PowerShell을 시작 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="77d05-114">On Windows Vista and later versions of the Windows operating system, to stop a process that is not owned by the current user, you must start PowerShell by using the Run as administrator option.</span></span>
<span data-ttu-id="77d05-115">또한 *Confirm* 매개 변수를 지정 하지 않으면 확인 메시지가 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="77d05-115">Also, you are not prompted for confirmation unless you specify the *Confirm* parameter.</span></span>

## <span data-ttu-id="77d05-116">예제</span><span class="sxs-lookup"><span data-stu-id="77d05-116">EXAMPLES</span></span>

### <span data-ttu-id="77d05-117">예제 1: 프로세스의 모든 인스턴스 중지</span><span class="sxs-lookup"><span data-stu-id="77d05-117">Example 1: Stop all instances of a process</span></span>

```
PS C:\> Stop-Process -Name "notepad"
```

<span data-ttu-id="77d05-118">이 명령은 컴퓨터의 Notepad 프로세스의 모든 인스턴스를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="77d05-118">This command stops all instances of the Notepad process on the computer.</span></span>
<span data-ttu-id="77d05-119">각 메모장 인스턴스는 자체 프로세스에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="77d05-119">Each instance of Notepad runs in its own process.</span></span>
<span data-ttu-id="77d05-120">*Name* 매개 변수를 사용 하 여 프로세스를 지정 합니다 .이는 모두 동일한 이름을 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="77d05-120">It uses the *Name* parameter to specify the processes, all of which have the same name.</span></span>
<span data-ttu-id="77d05-121">*Id* 매개 변수를 사용 하 여 동일한 프로세스를 중지 하는 경우 각 Notepad 인스턴스의 프로세스 id를 나열 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="77d05-121">If you were to use the *Id* parameter to stop the same processes, you would have to list the process IDs of each instance of Notepad.</span></span>

### <span data-ttu-id="77d05-122">예 2: 특정 프로세스 인스턴스 중지</span><span class="sxs-lookup"><span data-stu-id="77d05-122">Example 2: Stop a specific instance of a process</span></span>

```
PS C:\> Stop-Process -Id 3952 -Confirm -PassThru
Confirm
Are you sure you want to perform this action?
Performing operation "Stop-Process" on Target "notepad (3952)".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):y
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
41       2      996       3212    31            3952 notepad
```

<span data-ttu-id="77d05-123">이 명령은 Notepad 프로세스의 특정 인스턴스를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="77d05-123">This command stops a particular instance of the Notepad process.</span></span>
<span data-ttu-id="77d05-124">먼저 프로세스 ID, 3952를 사용하여 프로세스를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="77d05-124">It uses the process ID, 3952, to identify the process.</span></span>
<span data-ttu-id="77d05-125">*Confirm* 매개 변수는 프로세스를 중지 하기 전에 사용자에 게 메시지를 표시 하도록 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="77d05-125">The *Confirm* parameter directs PowerShell to prompt you before it stops the process.</span></span>
<span data-ttu-id="77d05-126">프롬프트에는 ID 외에 프로세스 이름이 포함 되어 있으므로이 방법이 가장 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="77d05-126">Because the prompt includes the process namein addition to its ID, this is best practice.</span></span>
<span data-ttu-id="77d05-127">*PassThru* 매개 변수는 표시를 위해 프로세스 개체를 포맷터로 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="77d05-127">The *PassThru* parameter passes the process object to the formatter for display.</span></span>
<span data-ttu-id="77d05-128">이 매개 변수를 사용 하지 않으면 **중지-처리** 명령 후에는 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="77d05-128">Without this parameter, there would be no display after a **Stop-Process** command.</span></span>

### <span data-ttu-id="77d05-129">예 3: 프로세스를 중지 하 고 중지 되었음을 감지</span><span class="sxs-lookup"><span data-stu-id="77d05-129">Example 3: Stop a process and detect that it has stopped</span></span>

```
PS C:\> calc
PS C:\> $p = Get-Process -Name "calc"
PS C:\> Stop-Process -InputObject $p
PS C:\> Get-Process | Where-Object {$_.HasExited}
```

<span data-ttu-id="77d05-130">이 일련의 명령은 계산 프로세스를 시작 및 중지 한 다음 중지 된 프로세스를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="77d05-130">This series of commands starts and stops the Calc process, and then detects processes that have stopped.</span></span>

<span data-ttu-id="77d05-131">첫 번째 명령은 계산기의 인스턴스를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="77d05-131">The first command starts an instance of the calculator.</span></span>

<span data-ttu-id="77d05-132">두 번째 명령은 **Get process** 를 사용 하 여 Calc 프로세스를 나타내는 개체를 가져온 다음 $p 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="77d05-132">The second command uses **Get-Process** gets an object that represents the Calc process, and then stores it in the $p variable.</span></span>

<span data-ttu-id="77d05-133">세 번째 명령은 Calc 프로세스를 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="77d05-133">The third command stops the Calc process.</span></span>
<span data-ttu-id="77d05-134">*InputObject* 매개 변수를 사용 하 여 개체를 **중지 프로세스** 에 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="77d05-134">It uses the *InputObject* parameter to pass the object to **Stop-Process**.</span></span>

<span data-ttu-id="77d05-135">마지막 명령은 이전에 실행되었지만 지금은 중지된 컴퓨터의 모든 프로세스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="77d05-135">The last command gets all of the processes on the computer that were running but that are now stopped.</span></span>
<span data-ttu-id="77d05-136">**Get Process** 를 사용 하 여 컴퓨터의 모든 프로세스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="77d05-136">It uses **Get-Process** to get all of the processes on the computer.</span></span>
<span data-ttu-id="77d05-137">파이프라인 연산자 (|)는 결과를 Where-Object cmdlet으로 전달 합니다 .이 cmdlet은 **HasExited** 속성 값이 $True 되는 항목을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="77d05-137">The pipeline operator (|) passes the results to the Where-Object cmdlet, which selects the ones where the value of the **HasExited** property is $True.</span></span>
<span data-ttu-id="77d05-138">**HasExited** 는 프로세스 개체의 속성 중 하나에 불과합니다.</span><span class="sxs-lookup"><span data-stu-id="77d05-138">**HasExited** is just one property of process objects.</span></span>
<span data-ttu-id="77d05-139">모든 속성을 찾으려면를 입력 `Get-Process | Get-Member` 합니다.</span><span class="sxs-lookup"><span data-stu-id="77d05-139">To find all the properties, type `Get-Process | Get-Member`.</span></span>

### <span data-ttu-id="77d05-140">예제 4: 현재 사용자가 소유 하지 않은 프로세스 중지</span><span class="sxs-lookup"><span data-stu-id="77d05-140">Example 4: Stop a process not owned by the current user</span></span>

```
PS C:\> Get-Process -Name "lsass" | Stop-Process

Stop-Process : Cannot stop process 'lsass (596)' because of the following error: Access is denied
At line:1 char:34
+ Get-Process -Name "lsass" | Stop-Process <<<<

[ADMIN]: PS C:\> Get-Process -Name "lsass" | Stop-Process

Warning!
Are you sure you want to perform this action?
Performing operation 'Stop-Process' on Target 'lsass(596)'
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
[ADMIN]: PS C:\> Get-Process -Name "lsass" | Stop-Process -Force
[ADMIN]: PS C:\>
```

<span data-ttu-id="77d05-141">이러한 명령은 *Force* 를 사용 하 여 사용자가 소유 하지 않은 프로세스를 중지 하는 경우의 결과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="77d05-141">These commands show the effect of using *Force* to stop a process that is not owned by the user.</span></span>

<span data-ttu-id="77d05-142">첫 번째 명령은 **Get process** 를 사용 하 여 Lsass 프로세스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="77d05-142">The first command uses **Get-Process** to get the Lsass process.</span></span>
<span data-ttu-id="77d05-143">파이프라인 연산자는 프로세스를 **중지** 하는 프로세스를 전송 하 여 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="77d05-143">A pipeline operator sends the process to **Stop-Process** to stop it.</span></span>
<span data-ttu-id="77d05-144">샘플 출력에 표시 된 것 처럼 첫 번째 명령은 액세스 거부 메시지와 함께 실패 합니다 .이 프로세스는 컴퓨터의 Administrator 그룹 구성원만 중지할 수 있기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="77d05-144">As shown in the sample output, the first command fails with an Access denied message, because this process can be stopped only by a member of the Administrator group on the computer.</span></span>

<span data-ttu-id="77d05-145">관리자 권한으로 실행 옵션을 사용 하 여 PowerShell을 열고 명령이 반복 되 면 PowerShell에서 확인 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="77d05-145">When PowerShell is opened by using the Run as administrator option, and the command is repeated, PowerShell prompts you for confirmation.</span></span>

<span data-ttu-id="77d05-146">두 번째 명령은 *Force* 를 지정 하 여 프롬프트를 표시 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="77d05-146">The second command specifies *Force* to suppress the prompt.</span></span>
<span data-ttu-id="77d05-147">그 결과 확인 메시지 없이 프로세스가 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="77d05-147">As a result, the process is stopped without confirmation.</span></span>

## <span data-ttu-id="77d05-148">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="77d05-148">PARAMETERS</span></span>

### <span data-ttu-id="77d05-149">-Force</span><span class="sxs-lookup"><span data-stu-id="77d05-149">-Force</span></span>

<span data-ttu-id="77d05-150">확인 메시지 없이 지정된 프로세스를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="77d05-150">Stops the specified processes without prompting for confirmation.</span></span>
<span data-ttu-id="77d05-151">기본적으로 **중지 프로세스** 는 현재 사용자가 소유 하지 않은 프로세스를 중지 하기 전에 확인 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="77d05-151">By default, **Stop-Process** prompts for confirmation before stopping any process that is not owned by the current user.</span></span>

<span data-ttu-id="77d05-152">프로세스의 소유자를 찾으려면 cmdlet을 사용 하 여 `Get-CimInstance` 프로세스를 나타내는 **Win32_Process** 개체를 가져온 다음 개체의 **getowner** 메서드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="77d05-152">To find the owner of a process, use the `Get-CimInstance` cmdlet to get a **Win32_Process** object that represents the process, and then use the **GetOwner** method of the object.</span></span>

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

### <span data-ttu-id="77d05-153">-Id</span><span class="sxs-lookup"><span data-stu-id="77d05-153">-Id</span></span>

<span data-ttu-id="77d05-154">중지할 프로세스의 프로세스 Id를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="77d05-154">Specifies the process IDs of the processes to stop.</span></span>
<span data-ttu-id="77d05-155">여러 ID를 지정하려면 쉼표를 사용하여 ID를 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="77d05-155">To specify multiple IDs, use commas to separate the IDs.</span></span>
<span data-ttu-id="77d05-156">프로세스의 PID를 찾으려면를 입력 `Get-Process` 합니다.</span><span class="sxs-lookup"><span data-stu-id="77d05-156">To find the PID of a process, type `Get-Process`.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="77d05-157">-InputObject</span><span class="sxs-lookup"><span data-stu-id="77d05-157">-InputObject</span></span>

<span data-ttu-id="77d05-158">중지할 프로세스 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="77d05-158">Specifies the process objects to stop.</span></span>
<span data-ttu-id="77d05-159">개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="77d05-159">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

```yaml
Type: System.Diagnostics.Process[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="77d05-160">-Name</span><span class="sxs-lookup"><span data-stu-id="77d05-160">-Name</span></span>

<span data-ttu-id="77d05-161">중지할 프로세스의 프로세스 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="77d05-161">Specifies the process names of the processes to stop.</span></span>
<span data-ttu-id="77d05-162">쉼표로 구분 된 여러 프로세스 이름을 입력 하거나 와일드 카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77d05-162">You can type multiple process names, separated by commas, or use wildcard characters.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases: ProcessName

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="77d05-163">-PassThru</span><span class="sxs-lookup"><span data-stu-id="77d05-163">-PassThru</span></span>

<span data-ttu-id="77d05-164">프로세스를 나타내는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="77d05-164">Returns an object that represents the process.</span></span>
<span data-ttu-id="77d05-165">기본적으로 이 cmdlet은 출력을 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="77d05-165">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="77d05-166">-Confirm</span><span class="sxs-lookup"><span data-stu-id="77d05-166">-Confirm</span></span>

<span data-ttu-id="77d05-167">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="77d05-167">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="77d05-168">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="77d05-168">-WhatIf</span></span>

<span data-ttu-id="77d05-169">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="77d05-169">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="77d05-170">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="77d05-170">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="77d05-171">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="77d05-171">CommonParameters</span></span>

<span data-ttu-id="77d05-172">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="77d05-172">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="77d05-173">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="77d05-173">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="77d05-174">입력</span><span class="sxs-lookup"><span data-stu-id="77d05-174">INPUTS</span></span>

### <span data-ttu-id="77d05-175">System.Diagnostics.Process</span><span class="sxs-lookup"><span data-stu-id="77d05-175">System.Diagnostics.Process</span></span>

<span data-ttu-id="77d05-176">프로세스 개체를이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77d05-176">You can pipe a process object to this cmdlet.</span></span>

## <span data-ttu-id="77d05-177">출력</span><span class="sxs-lookup"><span data-stu-id="77d05-177">OUTPUTS</span></span>

### <span data-ttu-id="77d05-178">없음, 시스템 진단 프로세스</span><span class="sxs-lookup"><span data-stu-id="77d05-178">None, System.Diagnostics.Process</span></span>

<span data-ttu-id="77d05-179">이 cmdlet은 *PassThru* 매개 변수를 지정 하는 경우 중지 된 프로세스를 나타내는 **system.object** 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="77d05-179">This cmdlet returns a **System.Diagnostics.Process** object that represents the stopped process, if you specify the *PassThru* parameter.</span></span>
<span data-ttu-id="77d05-180">그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="77d05-180">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="77d05-181">참고</span><span class="sxs-lookup"><span data-stu-id="77d05-181">NOTES</span></span>

* <span data-ttu-id="77d05-182">기본 제공 별칭, **kill** 및 **spps** 를 기준으로 **중지 프로세스** 를 참조할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77d05-182">You can also refer to **Stop-Process** by its built-in aliases, **kill** and **spps**.</span></span> <span data-ttu-id="77d05-183">자세한 내용은 about_Aliases를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="77d05-183">For more information, see about_Aliases.</span></span>

  <span data-ttu-id="77d05-184">Windows PowerShell에서 WMI (WMI(Windows Management Instrumentation)) **Win32_Process** 개체의 속성 및 메서드를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77d05-184">You can also use the properties and methods of the Windows Management Instrumentation (WMI) **Win32_Process** object in Windows PowerShell.</span></span>
<span data-ttu-id="77d05-185">자세한 내용은 `Get-CimInstance` 및 WMI SDK를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="77d05-185">For more information, see `Get-CimInstance` and the WMI SDK.</span></span>

* <span data-ttu-id="77d05-186">프로세스를 중지 하면 프로세스를 중지 하 고 프로세스에 의존 하는 서비스가 중지 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77d05-186">When stopping processes, realize that stopping a process can stop process and services that depend on the process.</span></span>
<span data-ttu-id="77d05-187">극히 드문 경우이지만 프로세스를 중지하면 Windows가 중지될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77d05-187">In an extreme case, stopping a process can stop Windows.</span></span>

## <span data-ttu-id="77d05-188">관련 링크</span><span class="sxs-lookup"><span data-stu-id="77d05-188">RELATED LINKS</span></span>

[<span data-ttu-id="77d05-189">Debug-Process</span><span class="sxs-lookup"><span data-stu-id="77d05-189">Debug-Process</span></span>](Debug-Process.md)

[<span data-ttu-id="77d05-190">Get-Process</span><span class="sxs-lookup"><span data-stu-id="77d05-190">Get-Process</span></span>](Get-Process.md)

[<span data-ttu-id="77d05-191">Start-Process</span><span class="sxs-lookup"><span data-stu-id="77d05-191">Start-Process</span></span>](Start-Process.md)

[<span data-ttu-id="77d05-192">Stop-Process</span><span class="sxs-lookup"><span data-stu-id="77d05-192">Stop-Process</span></span>](Stop-Process.md)

[<span data-ttu-id="77d05-193">Wait-Process</span><span class="sxs-lookup"><span data-stu-id="77d05-193">Wait-Process</span></span>](Wait-Process.md)
