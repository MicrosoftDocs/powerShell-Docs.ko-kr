---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/wait-process?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Wait-Process
ms.openlocfilehash: 97b29f13fd1106a04204f97f02d82e9760fa41ae
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93212202"
---
# <span data-ttu-id="c4697-103">Wait-Process</span><span class="sxs-lookup"><span data-stu-id="c4697-103">Wait-Process</span></span>

## <span data-ttu-id="c4697-104">개요</span><span class="sxs-lookup"><span data-stu-id="c4697-104">SYNOPSIS</span></span>
<span data-ttu-id="c4697-105">프로세스가 중지될 때까지 대기한 후 추가 입력을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="c4697-105">Waits for the processes to be stopped before accepting more input.</span></span>

## <span data-ttu-id="c4697-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c4697-106">SYNTAX</span></span>

### <span data-ttu-id="c4697-107">이름 (기본값)</span><span class="sxs-lookup"><span data-stu-id="c4697-107">Name (Default)</span></span>

```
Wait-Process [-Name] <String[]> [[-Timeout] <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="c4697-108">Id</span><span class="sxs-lookup"><span data-stu-id="c4697-108">Id</span></span>

```
Wait-Process [-Id] <Int32[]> [[-Timeout] <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="c4697-109">InputObject</span><span class="sxs-lookup"><span data-stu-id="c4697-109">InputObject</span></span>

```
Wait-Process [[-Timeout] <Int32>] -InputObject <Process[]> [<CommonParameters>]
```

## <span data-ttu-id="c4697-110">설명</span><span class="sxs-lookup"><span data-stu-id="c4697-110">DESCRIPTION</span></span>

<span data-ttu-id="c4697-111">**대기 프로세스** cmdlet은 실행 중인 하나 이상의 프로세스가 중지 될 때까지 대기한 후 입력을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4697-111">The **Wait-Process** cmdlet waits for one or more running processes to be stopped before accepting input.</span></span>
<span data-ttu-id="c4697-112">PowerShell 콘솔에서이 cmdlet은 프로세스가 중지 될 때까지 명령 프롬프트를 표시 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c4697-112">In the PowerShell console, this cmdlet suppresses the command prompt until the processes are stopped.</span></span>
<span data-ttu-id="c4697-113">프로세스 이름 또는 프로세스 ID (PID)로 프로세스를 지정 하거나 프로세스 개체를 **대기 프로세스로** 파이프 하 여 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4697-113">You can specify a process by process name or process ID (PID), or pipe a process object to **Wait-Process** .</span></span>

<span data-ttu-id="c4697-114">**대기 프로세스** 는 로컬 컴퓨터에서 실행 중인 프로세스 에서만 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4697-114">**Wait-Process** works only on processes running on the local computer.</span></span>

## <span data-ttu-id="c4697-115">예제</span><span class="sxs-lookup"><span data-stu-id="c4697-115">EXAMPLES</span></span>

### <span data-ttu-id="c4697-116">예 1: 프로세스를 중지 하 고 대기</span><span class="sxs-lookup"><span data-stu-id="c4697-116">Example 1: Stop a process and wait</span></span>

```
PS C:\> $nid = (Get-Process notepad).id
PS C:\> Stop-Process -Id $nid
PS C:\> Wait-Process -Id $nid
```

<span data-ttu-id="c4697-117">이 예제에서는 메모장 프로세스를 중지 하 고 프로세스가 중지 될 때까지 기다린 후 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4697-117">This example stops the Notepad process and then waits for the process to be stopped before it continues with the next command.</span></span>

<span data-ttu-id="c4697-118">첫 번째 명령은 **Get process** cmdlet을 사용 하 여 메모장 프로세스의 ID를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c4697-118">The first command uses the **Get-Process** cmdlet to get the ID of the Notepad process.</span></span>
<span data-ttu-id="c4697-119">$Nid 변수에 ID를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4697-119">It stores the ID in the $nid variable.</span></span>

<span data-ttu-id="c4697-120">두 번째 명령은 Stop-Process cmdlet을 사용 하 여 $nid에 저장 된 ID를 사용 하 여 프로세스를 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4697-120">The second command uses the Stop-Process cmdlet to stop the process with the ID stored in $nid.</span></span>

<span data-ttu-id="c4697-121">세 번째 명령은 **대기 프로세스** 를 사용 하 여 Notepad 프로세스가 중지 될 때까지 대기 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4697-121">The third command uses **Wait-Process** to wait until the Notepad process is stopped.</span></span>
<span data-ttu-id="c4697-122">**대기 프로세스** 의 *Id* 매개 변수를 사용 하 여 프로세스를 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4697-122">It uses the *Id* parameter of **Wait-Process** to identify the process.</span></span>

### <span data-ttu-id="c4697-123">예제 2: 프로세스 지정</span><span class="sxs-lookup"><span data-stu-id="c4697-123">Example 2: Specifying a process</span></span>

```
PS C:\> $p = Get-Process notepad
PS C:\> Wait-Process -Id $p.id
PS C:\> Wait-Process -Name "notepad"
PS C:\> Wait-Process -InputObject $p
```

<span data-ttu-id="c4697-124">이러한 명령은 프로세스를 **대기 프로세스로** 지정 하는 세 가지 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c4697-124">These commands show three different methods of specifying a process to **Wait-Process** .</span></span>
<span data-ttu-id="c4697-125">첫 번째 명령은 메모장 프로세스를 가져와 $p 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4697-125">The first command gets the Notepad process and stores it in the $p variable.</span></span>

<span data-ttu-id="c4697-126">두 번째 명령은 *Id* 매개 변수를 사용 하 고, 세 번째 명령은 *Name* 매개 변수를 사용 하며, 네 번째 명령은 *InputObject* 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4697-126">The second command uses the *Id* parameter, the third command uses the *Name* parameter, and the fourth command uses the *InputObject* parameter.</span></span>

<span data-ttu-id="c4697-127">이 세 명령의 결과는 동일하며 상호 교환적으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4697-127">These commands have the same results and can be used interchangeably.</span></span>

### <span data-ttu-id="c4697-128">예제 3: 지정 된 시간 동안 프로세스 대기</span><span class="sxs-lookup"><span data-stu-id="c4697-128">Example 3: Wait for processes for a specified time</span></span>

```
PS C:\> Wait-Process -Name outlook, winword -Timeout 30
```

<span data-ttu-id="c4697-129">이 명령은 Outlook 및 Winword 프로세스가 중지될 때까지 30초 동안 대기합니다.</span><span class="sxs-lookup"><span data-stu-id="c4697-129">This command waits 30 seconds for the Outlook and Winword processes to stop.</span></span>
<span data-ttu-id="c4697-130">두 프로세스 모두 중지되지 않으면 종료되지 않는 오류와 명령 프롬프트를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="c4697-130">If both processes are not stopped, the cmdlet displays a non-terminating error and the command prompt.</span></span>

## <span data-ttu-id="c4697-131">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c4697-131">PARAMETERS</span></span>

### <span data-ttu-id="c4697-132">-Id</span><span class="sxs-lookup"><span data-stu-id="c4697-132">-Id</span></span>

<span data-ttu-id="c4697-133">프로세스의 프로세스 ID를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c4697-133">Specifies the process IDs of the processes.</span></span>
<span data-ttu-id="c4697-134">여러 ID를 지정하려면 쉼표를 사용하여 ID를 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="c4697-134">To specify multiple IDs, use commas to separate the IDs.</span></span>
<span data-ttu-id="c4697-135">프로세스의 PID를 찾으려면를 입력 `Get-Process` 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4697-135">To find the PID of a process, type `Get-Process`.</span></span>

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

### <span data-ttu-id="c4697-136">-InputObject</span><span class="sxs-lookup"><span data-stu-id="c4697-136">-InputObject</span></span>

<span data-ttu-id="c4697-137">프로세스 개체를 전송하여 프로세스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c4697-137">Specifies the processes by submitting process objects.</span></span>
<span data-ttu-id="c4697-138">프로세스 개체가 포함 된 변수를 입력 하거나 프로세스 개체를 가져오는 명령 또는 식 (예: Get-Process cmdlet)을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4697-138">Enter a variable that contains the process objects, or type a command or expression that gets the process objects, such as the Get-Process cmdlet.</span></span>

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

### <span data-ttu-id="c4697-139">-Name</span><span class="sxs-lookup"><span data-stu-id="c4697-139">-Name</span></span>

<span data-ttu-id="c4697-140">프로세스의 프로세스 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c4697-140">Specifies the process names of the processes.</span></span>
<span data-ttu-id="c4697-141">여러 이름을 지정하려면 쉼표를 사용하여 이름을 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="c4697-141">To specify multiple names, use commas to separate the names.</span></span>
<span data-ttu-id="c4697-142">와일드카드 문자는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c4697-142">Wildcard characters are not supported.</span></span>

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

### <span data-ttu-id="c4697-143">-시간 제한</span><span class="sxs-lookup"><span data-stu-id="c4697-143">-Timeout</span></span>

<span data-ttu-id="c4697-144">지정 된 프로세스가 중지 될 때까지이 cmdlet이 대기 하는 최대 시간 (초)을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4697-144">Specifies the maximum time, in seconds, that this cmdlet waits for the specified processes to stop.</span></span>
<span data-ttu-id="c4697-145">이 간격이 만료되면 명령은 여전히 실행되고 있는 프로세스를 나열하는 종료되지 않은 오류를 표시하고 대기를 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="c4697-145">When this interval expires, the command displays a non-terminating error that lists the processes that are still running, and ends the wait.</span></span>
<span data-ttu-id="c4697-146">기본적으로 시간 제한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c4697-146">By default, there is no time-out.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: TimeoutSec

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c4697-147">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c4697-147">CommonParameters</span></span>

<span data-ttu-id="c4697-148">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c4697-148">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c4697-149">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c4697-149">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c4697-150">입력</span><span class="sxs-lookup"><span data-stu-id="c4697-150">INPUTS</span></span>

### <span data-ttu-id="c4697-151">System.Diagnostics.Process</span><span class="sxs-lookup"><span data-stu-id="c4697-151">System.Diagnostics.Process</span></span>

<span data-ttu-id="c4697-152">프로세스 개체를이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4697-152">You can pipe a process object to this cmdlet.</span></span>

## <span data-ttu-id="c4697-153">출력</span><span class="sxs-lookup"><span data-stu-id="c4697-153">OUTPUTS</span></span>

### <span data-ttu-id="c4697-154">없음</span><span class="sxs-lookup"><span data-stu-id="c4697-154">None</span></span>

<span data-ttu-id="c4697-155">이 cmdlet은 어떠한 출력도 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c4697-155">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="c4697-156">참고</span><span class="sxs-lookup"><span data-stu-id="c4697-156">NOTES</span></span>

* <span data-ttu-id="c4697-157">이 cmdlet은 System.object 클래스의 **Waitforexit** 메서드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4697-157">This cmdlet uses the **WaitForExit** method of the System.Diagnostics.Process class.</span></span> <span data-ttu-id="c4697-158">이 메서드에 대한 자세한 내용은 Microsoft .NET Framework SDK를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c4697-158">For more information about this method, see the Microsoft .NET Framework SDK.</span></span>

*

## <span data-ttu-id="c4697-159">관련 링크</span><span class="sxs-lookup"><span data-stu-id="c4697-159">RELATED LINKS</span></span>

[<span data-ttu-id="c4697-160">Debug-Process</span><span class="sxs-lookup"><span data-stu-id="c4697-160">Debug-Process</span></span>](Debug-Process.md)

[<span data-ttu-id="c4697-161">Get-Process</span><span class="sxs-lookup"><span data-stu-id="c4697-161">Get-Process</span></span>](Get-Process.md)

[<span data-ttu-id="c4697-162">Start-Process</span><span class="sxs-lookup"><span data-stu-id="c4697-162">Start-Process</span></span>](Start-Process.md)

[<span data-ttu-id="c4697-163">Stop-Process</span><span class="sxs-lookup"><span data-stu-id="c4697-163">Stop-Process</span></span>](Stop-Process.md)

[<span data-ttu-id="c4697-164">Wait-Process</span><span class="sxs-lookup"><span data-stu-id="c4697-164">Wait-Process</span></span>](Wait-Process.md)
