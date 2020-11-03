---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-eventlog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-EventLog
ms.openlocfilehash: 4cf29146727c9a54715459a2d56e47a27c5bacc0
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93214554"
---
# <span data-ttu-id="25775-103">Remove-EventLog</span><span class="sxs-lookup"><span data-stu-id="25775-103">Remove-EventLog</span></span>

## <span data-ttu-id="25775-104">개요</span><span class="sxs-lookup"><span data-stu-id="25775-104">SYNOPSIS</span></span>
<span data-ttu-id="25775-105">이벤트 로그를 삭제하거나 이벤트 원본의 등록을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="25775-105">Deletes an event log or unregisters an event source.</span></span>

## <span data-ttu-id="25775-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="25775-106">SYNTAX</span></span>

### <span data-ttu-id="25775-107">Default (기본값)</span><span class="sxs-lookup"><span data-stu-id="25775-107">Default (Default)</span></span>

```
Remove-EventLog [[-ComputerName] <String[]>] [-LogName] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="25775-108">원본</span><span class="sxs-lookup"><span data-stu-id="25775-108">Source</span></span>

```
Remove-EventLog [[-ComputerName] <String[]>] [-Source <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="25775-109">설명</span><span class="sxs-lookup"><span data-stu-id="25775-109">DESCRIPTION</span></span>
<span data-ttu-id="25775-110">EventLog cmdlet은 로컬 또는 원격 컴퓨터에서 이벤트 로그 파일을 삭제 하 고 로그에 대 한 모든 이벤트 원본의 등록을 **취소** 합니다.</span><span class="sxs-lookup"><span data-stu-id="25775-110">The **Remove-EventLog** cmdlet deletes an event log file from a local or remote computer and unregisters all its event sources for the log.</span></span>
<span data-ttu-id="25775-111">이 cmdlet을 사용하면 이벤트 로그를 삭제하지 않고 이벤트 원본의 등록을 취소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25775-111">You can also use this cmdlet to unregister event sources without deleting any event logs.</span></span>

<span data-ttu-id="25775-112">**Eventlog 명사 인** **eventlog** cmdlet은 클래식 이벤트 로그 에서만 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="25775-112">The cmdlets that contain the **EventLog** noun, the **EventLog** cmdlets, work only on classic event logs.</span></span>
<span data-ttu-id="25775-113">Windows Vista 이상 버전의 windows 운영 체제에서 Windows 이벤트 로그 기술을 사용 하는 로그에서 이벤트를 가져오려면 WinEvent를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="25775-113">To get events from logs that use the Windows Event Log technology in Windows Vista and later versions of the Windows operating system, use Get-WinEvent.</span></span>

<span data-ttu-id="25775-114">주의:이 cmdlet은 운영 체제 이벤트 로그를 삭제할 수 있으며,이로 인해 응용 프로그램 오류 및 예기치 않은 시스템 동작이 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25775-114">CAUTION: This cmdlet can delete operating system event logs, which might cause application failures and unexpected system behavior.</span></span>

## <span data-ttu-id="25775-115">예제</span><span class="sxs-lookup"><span data-stu-id="25775-115">EXAMPLES</span></span>

### <span data-ttu-id="25775-116">예 1: 로컬 컴퓨터에서 이벤트 로그 제거</span><span class="sxs-lookup"><span data-stu-id="25775-116">Example 1: Remove an event log from the local computer</span></span>

```
PS C:\> Remove-EventLog -LogName "MyLog"
```

<span data-ttu-id="25775-117">이 명령은 로컬 컴퓨터에서 MyLog 이벤트 로그를 삭제하고 해당 이벤트 원본의 등록을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="25775-117">This command deletes the MyLog event log from the local computer and unregisters its event sources.</span></span>

### <span data-ttu-id="25775-118">예 2: 여러 컴퓨터에서 이벤트 로그 제거</span><span class="sxs-lookup"><span data-stu-id="25775-118">Example 2: Remove an event log from several computers</span></span>

```
PS C:\> Remove-EventLog -LogName "MyLog", "TestLog" -ComputerName "Server01", "Server02", "localhost"
```

<span data-ttu-id="25775-119">이 명령은 로컬 컴퓨터와 Server01 및 Server02 원격 컴퓨터에서 MyLog 및 TestLog 이벤트 로그를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="25775-119">This command deletes the MyLog and TestLog event logs from the local computer and the Server01 and Server02 remote computers.</span></span>
<span data-ttu-id="25775-120">이러한 로그에 대한 이벤트 원본의 등록을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="25775-120">The command also unregisters the event sources for these logs.</span></span>

### <span data-ttu-id="25775-121">예제 3: 이벤트 소스 삭제</span><span class="sxs-lookup"><span data-stu-id="25775-121">Example 3: Delete an event source</span></span>

```
PS C:\> Remove-EventLog -Source "MyApp"
```

<span data-ttu-id="25775-122">이 명령은 로컬 컴퓨터의 로그에서 MyApp 이벤트 원본을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="25775-122">This command deletes the MyApp event source from the logs on the local computer.</span></span>
<span data-ttu-id="25775-123">명령이 완료 되 면 MyApp 프로그램은 이벤트 로그에 쓸 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="25775-123">When the command finishes, the MyApp program cannot write to any event logs.</span></span>

### <span data-ttu-id="25775-124">예제 4: 이벤트 로그 제거 및 작업 확인</span><span class="sxs-lookup"><span data-stu-id="25775-124">Example 4: Remove an event log and confirm the action</span></span>

```
The first command lists the event logs on the local computer.
PS C:\> Get-EventLog -List
Max(K) Retain OverflowAction        Entries Log
------ ------ --------------        ------- ---
15,168      0 OverwriteAsNeeded      22,923 Application
15,168      0 OverwriteAsNeeded          53 DFS Replication
15,168      7 OverwriteOlder              0 Hardware Events
512      7 OverwriteOlder              0 Internet Explorer
20,480      0 OverwriteAsNeeded           0 Key Management Service
30,016      0 OverwriteAsNeeded      50,060 Security
15,168      0 OverwriteAsNeeded      27,592 System
15,360      0 OverwriteAsNeeded      18,355 Windows PowerShell
15,168      7 OverwriteAsNeeded          12 ZapLog

The second command deletes the ZapLog event log.
PS C:\> Remove-EventLog -LogName "ZapLog"

The third command lists the event logs again. The ZapLog event log no longer appears in the list.
PS C:\> Get-EventLog -List
Max(K) Retain OverflowAction        Entries Log
------ ------ --------------        ------- ---
15,168      0 OverwriteAsNeeded      22,923 Application
15,168      0 OverwriteAsNeeded          53 DFS Replication
15,168      7 OverwriteOlder              0 Hardware Events
512      7 OverwriteOlder              0 Internet Explorer
20,480      0 OverwriteAsNeeded           0 Key Management Service
30,016      0 OverwriteAsNeeded      50,060 Security
15,168      0 OverwriteAsNeeded      27,592 System
15,360      0 OverwriteAsNeeded      18,355 Windows PowerShell
```

<span data-ttu-id="25775-125">이 명령은 컴퓨터의 이벤트 로그를 나열 하 고 이벤트 로그 **제거** 명령이 성공적으로 수행 되었는지 확인 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="25775-125">These commands show how to list the event logs on a computer and verify that a **Remove-EventLog** command was successful.</span></span>

### <span data-ttu-id="25775-126">예 5: 이벤트 소스 제거 및 작업 확인</span><span class="sxs-lookup"><span data-stu-id="25775-126">Example 5: Remove an event source and confirm the action</span></span>

```
PS C:\> Get-WmiObject win32_nteventlogfile -Filter "logfilename='TestLog'" | foreach {$_.sources}
MyApp
TestApp
PS C:\> Remove-Eventlog -Source "MyApp"
PS C:\> Get-WmiObject win32_nteventlogfile -Filter "logfilename='TestLog'"} | foreach {$_.sources}
TestApp
```

<span data-ttu-id="25775-127">이 명령은 Get-WmiObject cmdlet을 사용하여 로컬 컴퓨터의 이벤트 원본을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="25775-127">These commands use the Get-WmiObject cmdlet to list the event sources on the local computer.</span></span>
<span data-ttu-id="25775-128">이 명령을 사용하면 명령이 성공적으로 실행되었는지 확인하거나 이벤트 원본을 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25775-128">You can these commands to verify the success of a command or to delete an event source.</span></span>

<span data-ttu-id="25775-129">첫 번째 명령은 로컬 컴퓨터에 있는 TestLog 이벤트 로그의 이벤트 원본을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="25775-129">The first command gets the event sources of the TestLog event log on the local computer.</span></span>
<span data-ttu-id="25775-130">MyApp도 원본 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="25775-130">MyApp is one of the sources.</span></span>

<span data-ttu-id="25775-131">두 번째 명령은 **Remove EventLog** 의 *Source* 매개 변수를 사용 하 여 MyApp 이벤트 원본을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="25775-131">The second command uses the *Source* parameter of **Remove-EventLog** to delete the MyApp event source.</span></span>

<span data-ttu-id="25775-132">세 번째 명령은 첫 번째 명령과 동일하며</span><span class="sxs-lookup"><span data-stu-id="25775-132">The third command is identical to the first.</span></span>
<span data-ttu-id="25775-133">MyApp 이벤트 원본이 삭제되었음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="25775-133">It shows that the MyApp event source was deleted.</span></span>

## <span data-ttu-id="25775-134">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="25775-134">PARAMETERS</span></span>

### <span data-ttu-id="25775-135">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="25775-135">-ComputerName</span></span>
<span data-ttu-id="25775-136">원격 컴퓨터를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="25775-136">Specifies a remote computer.</span></span>
<span data-ttu-id="25775-137">기본값은 로컬 컴퓨터입니다.</span><span class="sxs-lookup"><span data-stu-id="25775-137">The default is the local computer.</span></span>

<span data-ttu-id="25775-138">원격 컴퓨터의 NetBIOS 이름, IP 주소 또는 정규화된 도메인 이름을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="25775-138">Type the NetBIOS name, an IP address, or a fully qualified domain name of a remote computer.</span></span>
<span data-ttu-id="25775-139">로컬 컴퓨터를 지정 하려면 컴퓨터 이름, 점 (.) 또는 localhost를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="25775-139">To specify the local computer, type the computer name, a dot (.), or localhost.</span></span>

<span data-ttu-id="25775-140">이 매개 변수는 Windows PowerShell 원격 기능을 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="25775-140">This parameter does not rely on Windows PowerShell remoting.</span></span>
<span data-ttu-id="25775-141">컴퓨터에서 원격 명령을 실행 하도록 구성 되지 않은 경우에도 **제거 이벤트** 의 *ComputerName* 매개 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25775-141">You can use the *ComputerName* parameter of **Remove-EventLog** even if your computer is not configured to run remote commands.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="25775-142">-LogName</span><span class="sxs-lookup"><span data-stu-id="25775-142">-LogName</span></span>
<span data-ttu-id="25775-143">이벤트 로그를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="25775-143">Specifies the event logs.</span></span>
<span data-ttu-id="25775-144">하나 이상의 이벤트 로그에 대 한 로그 이름을 쉼표로 구분 하 여 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="25775-144">Enter the log name of one or more event logs, separated by commas.</span></span>
<span data-ttu-id="25775-145">로그 이름은 *Logdisplayname* 이 아닌 **log** 속성의 값입니다. 와일드 카드 문자는 허용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="25775-145">The log name is the value of the **Log** property, not the *LogDisplayName* , Wildcard characters are not permitted.</span></span>
<span data-ttu-id="25775-146">이 매개 변수는 필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="25775-146">This parameter is required.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases: LN

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="25775-147">-Source</span><span class="sxs-lookup"><span data-stu-id="25775-147">-Source</span></span>
<span data-ttu-id="25775-148">이 cmdlet의 등록을 취소 하는 이벤트 원본을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="25775-148">Specifies the event sources that this cmdlet unregisters.</span></span>
<span data-ttu-id="25775-149">실행 파일 이름이 아닌 원본 이름을 쉼표로 구분 하 여 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="25775-149">Enter the source names, not the executable name, separated by commas.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Source
Aliases: SRC

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="25775-150">-Confirm</span><span class="sxs-lookup"><span data-stu-id="25775-150">-Confirm</span></span>
<span data-ttu-id="25775-151">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="25775-151">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="25775-152">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="25775-152">-WhatIf</span></span>
<span data-ttu-id="25775-153">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="25775-153">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="25775-154">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="25775-154">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="25775-155">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="25775-155">CommonParameters</span></span>
<span data-ttu-id="25775-156">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="25775-156">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="25775-157">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="25775-157">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="25775-158">입력</span><span class="sxs-lookup"><span data-stu-id="25775-158">INPUTS</span></span>

### <span data-ttu-id="25775-159">없음</span><span class="sxs-lookup"><span data-stu-id="25775-159">None</span></span>
<span data-ttu-id="25775-160">이 cmdlet에 입력을 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="25775-160">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="25775-161">출력</span><span class="sxs-lookup"><span data-stu-id="25775-161">OUTPUTS</span></span>

### <span data-ttu-id="25775-162">없음</span><span class="sxs-lookup"><span data-stu-id="25775-162">None</span></span>
<span data-ttu-id="25775-163">이 cmdlet은 어떠한 출력도 반환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="25775-163">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="25775-164">참고</span><span class="sxs-lookup"><span data-stu-id="25775-164">NOTES</span></span>

* <span data-ttu-id="25775-165">Windows Vista 및 이후 버전의 Windows 운영 체제에서 **제거 이벤트** 를 사용 하려면 관리자 권한으로 실행 옵션을 사용 하 여 windows PowerShell을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="25775-165">To use **Remove-EventLog** on Windows Vista and later versions of the Windows operating system, start Windows PowerShell by using the Run as administrator option.</span></span>

  <span data-ttu-id="25775-166">이벤트 로그를 제거한 다음 다시 만들면 같은 이벤트 원본을 등록할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="25775-166">If you remove an event log and then re-create the log, you will not be able to register the same event sources.</span></span>
<span data-ttu-id="25775-167">이벤트 원본을 사용하여 원래 로그에 항목을 기록했던 애플리케이션에서 새 로그에 항목을 기록할 수 없게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="25775-167">Applications that used the events sources to write entries to the original log will not be able to write to the new log.</span></span>

* <span data-ttu-id="25775-168">특정 로그에 대한 이벤트 원본의 등록을 취소할 경우 이벤트 원본에서 다른 이벤트 로그에 항목을 기록하지 못하게 될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25775-168">When you unregister an event source for a particular log, the event source might be prevented from writing entries in other event logs.</span></span>

## <span data-ttu-id="25775-169">관련 링크</span><span class="sxs-lookup"><span data-stu-id="25775-169">RELATED LINKS</span></span>

[<span data-ttu-id="25775-170">Clear-EventLog</span><span class="sxs-lookup"><span data-stu-id="25775-170">Clear-EventLog</span></span>](Clear-EventLog.md)

[<span data-ttu-id="25775-171">Get-EventLog</span><span class="sxs-lookup"><span data-stu-id="25775-171">Get-EventLog</span></span>](Get-EventLog.md)

[<span data-ttu-id="25775-172">Limit-EventLog</span><span class="sxs-lookup"><span data-stu-id="25775-172">Limit-EventLog</span></span>](Limit-EventLog.md)

[<span data-ttu-id="25775-173">New-EventLog</span><span class="sxs-lookup"><span data-stu-id="25775-173">New-EventLog</span></span>](New-EventLog.md)

[<span data-ttu-id="25775-174">Remove-EventLog</span><span class="sxs-lookup"><span data-stu-id="25775-174">Remove-EventLog</span></span>](Remove-EventLog.md)

[<span data-ttu-id="25775-175">Show-EventLog</span><span class="sxs-lookup"><span data-stu-id="25775-175">Show-EventLog</span></span>](Show-EventLog.md)

[<span data-ttu-id="25775-176">Write-EventLog</span><span class="sxs-lookup"><span data-stu-id="25775-176">Write-EventLog</span></span>](Write-EventLog.md)
