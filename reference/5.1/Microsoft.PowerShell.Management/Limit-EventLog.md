---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/limit-eventlog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Limit-EventLog
ms.openlocfilehash: 3ec3214103dc6151e148f7482b0be8b821871e3c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93214665"
---
# <span data-ttu-id="0242a-103">Limit-EventLog</span><span class="sxs-lookup"><span data-stu-id="0242a-103">Limit-EventLog</span></span>

## <span data-ttu-id="0242a-104">개요</span><span class="sxs-lookup"><span data-stu-id="0242a-104">SYNOPSIS</span></span>
<span data-ttu-id="0242a-105">이벤트 로그의 크기와 로그 항목의 보관 기간을 제한하는 이벤트 로그 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="0242a-105">Sets the event log properties that limit the size of the event log and the age of its entries.</span></span>

## <span data-ttu-id="0242a-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="0242a-106">SYNTAX</span></span>

```
Limit-EventLog [-LogName] <String[]> [-ComputerName <String[]>] [-RetentionDays <Int32>]
 [-OverflowAction <OverflowAction>] [-MaximumSize <Int64>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="0242a-107">설명</span><span class="sxs-lookup"><span data-stu-id="0242a-107">DESCRIPTION</span></span>
<span data-ttu-id="0242a-108">**Limit EventLog** cmdlet은 클래식 이벤트 로그의 최대 크기, 각 이벤트를 보존 해야 하는 기간 및 로그가 최대 크기에 도달할 때 발생 하는 결과를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0242a-108">The **Limit-EventLog** cmdlet sets the maximum size of a classic event log, how long each event must be retained, and what happens when the log reaches its maximum size.</span></span>
<span data-ttu-id="0242a-109">이 cmdlet을 사용하여 로컬 또는 원격 컴퓨터의 이벤트 로그를 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0242a-109">You can use it to limit the event logs on local or remote computers.</span></span>

<span data-ttu-id="0242a-110">EventLog 명사를 포함하는 cmdlet(EventLog cmdlet)은 클래식 이벤트 로그에서만 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="0242a-110">The cmdlets that contain the EventLog noun (the EventLog cmdlets) work only on classic event logs.</span></span>
<span data-ttu-id="0242a-111">Windows Vista 이상에서 Windows 이벤트 로그 기술을 사용하는 로그의 이벤트를 가져오려면 Get-WinEvent를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0242a-111">To get events from logs that use the Windows Event Log technology in Windows Vista and later versions of Windows, use Get-WinEvent.</span></span>

## <span data-ttu-id="0242a-112">예제</span><span class="sxs-lookup"><span data-stu-id="0242a-112">EXAMPLES</span></span>

### <span data-ttu-id="0242a-113">예제 1: 이벤트 로그 크기 늘리기</span><span class="sxs-lookup"><span data-stu-id="0242a-113">Example 1: Increase the size of an event log</span></span>

```
PS C:\> Limit-EventLog -LogName "Windows PowerShell" -MaximumSize 20KB
```

<span data-ttu-id="0242a-114">이 명령은 로컬 컴퓨터에 있는 Windows PowerShell 이벤트 로그의 최대 크기를 20480바이트(20KB)로 늘립니다.</span><span class="sxs-lookup"><span data-stu-id="0242a-114">This command increases the maximum size of the Windows PowerShell event log on the local computer to 20480 bytes (20 KB).</span></span>

### <span data-ttu-id="0242a-115">예 2: 지정 된 기간 동안 이벤트 로그 유지</span><span class="sxs-lookup"><span data-stu-id="0242a-115">Example 2: Retain an event log for a specified duration</span></span>

```
PS C:\> Limit-EventLog -LogName Security -ComputerName "Server01", "Server02" -RetentionDays 7
```

<span data-ttu-id="0242a-116">이 명령은 Server01 및 Server02 컴퓨터의 보안 로그에 있는 이벤트를 7일 이상 보관하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="0242a-116">This command ensures that events in the Security log on the Server01 and Server02 computers are retained for at least 7 days.</span></span>

### <span data-ttu-id="0242a-117">예 3: 모든 이벤트 로그의 오버플로 작업 변경</span><span class="sxs-lookup"><span data-stu-id="0242a-117">Example 3: Change the overflow action of all event logs</span></span>

```
PS C:\> $Logs = Get-EventLog -List | ForEach {$_.log}
PS C:\> Limit-EventLog -OverflowAction OverwriteOlder -LogName $Logs
PS C:\> Get-EventLog -List

Max(K) Retain OverflowAction     Entries  Log
------ ------ --------------     -------  ---
15,168      0 OverwriteOlder       3,412  Application
512         0 OverwriteOlder           0  DFS Replication
512         0 OverwriteOlder          17  DxStudio
10,240      7 OverwriteOlder           0  HardwareEvents
512         0 OverwriteOlder           0  Internet Explorer
512         0 OverwriteOlder           0  Key Management Service
16,384      0 OverwriteOlder           4  ODiag
16,384      0 OverwriteOlder         389  OSession Security
15,168      0 OverwriteOlder      19,360  System
15,360      0 OverwriteOlder      15,828  Windows PowerShell
```

<span data-ttu-id="0242a-118">이 예에서는 로컬 컴퓨터에 있는 모든 이벤트 로그의 오버플로 작업을 OverwriteOlder로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="0242a-118">This example changes the overflow action of all event logs on the local computer to OverwriteOlder.</span></span>

<span data-ttu-id="0242a-119">첫 번째 명령은 로컬 컴퓨터에 있는 모든 로그의 로그 이름을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0242a-119">The first command gets the log names of all of the logs on the local computer.</span></span>
<span data-ttu-id="0242a-120">두 번째 명령은 오버플로 작업을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="0242a-120">The second command sets the overflow action.</span></span>
<span data-ttu-id="0242a-121">세 번째 명령은 결과를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="0242a-121">The third command displays the results.</span></span>

## <span data-ttu-id="0242a-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="0242a-122">PARAMETERS</span></span>

### <span data-ttu-id="0242a-123">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="0242a-123">-ComputerName</span></span>
<span data-ttu-id="0242a-124">원격 컴퓨터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0242a-124">Specifies remote computers.</span></span>
<span data-ttu-id="0242a-125">기본값은 로컬 컴퓨터입니다.</span><span class="sxs-lookup"><span data-stu-id="0242a-125">The default is the local computer.</span></span>

<span data-ttu-id="0242a-126">원격 컴퓨터의 NetBIOS 이름, IP (인터넷 프로토콜) 주소 또는 FQDN (정규화 된 도메인 이름)을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="0242a-126">Type the NetBIOS name, an Internet Protocol (IP) address, or a fully qualified domain name (FQDN) of a remote computer.</span></span>
<span data-ttu-id="0242a-127">로컬 컴퓨터를 지정 하려면 컴퓨터 이름, 점 (.) 또는 localhost를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="0242a-127">To specify the local computer, type the computer name, a dot (.), or localhost.</span></span>

<span data-ttu-id="0242a-128">이 매개 변수는 Windows PowerShell 원격 기능을 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0242a-128">This parameter does not rely on Windows PowerShell remoting.</span></span>
<span data-ttu-id="0242a-129">원격 명령을 실행 하도록 컴퓨터를 구성 하지 않은 경우에도 **Limit 이벤트 로그** 의 *ComputerName* 매개 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0242a-129">You can use the *ComputerName* parameter of **Limit-EventLog** even if your computer is not configured to run remote commands.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0242a-130">-LogName</span><span class="sxs-lookup"><span data-stu-id="0242a-130">-LogName</span></span>
<span data-ttu-id="0242a-131">이벤트 로그를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0242a-131">Specifies the event logs.</span></span>
<span data-ttu-id="0242a-132">하나 이상 이벤트 로그의 로그 이름(Log 표시 이름이 아닌 Log 속성의 값)을 쉼표로 구분하여 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="0242a-132">Enter the log name (the value of the Log property; not the LogDisplayName) of one or more event logs, separated by commas.</span></span>
<span data-ttu-id="0242a-133">와일드카드 문자는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0242a-133">Wildcard characters are not permitted.</span></span>
<span data-ttu-id="0242a-134">이 매개 변수는 필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="0242a-134">This parameter is required.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: LN

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0242a-135">-MaximumSize</span><span class="sxs-lookup"><span data-stu-id="0242a-135">-MaximumSize</span></span>
<span data-ttu-id="0242a-136">이벤트 로그의 최대 크기를 바이트 단위로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0242a-136">Specifies the maximum size of the event logs in bytes.</span></span>
<span data-ttu-id="0242a-137">64KB에서 4GB 사이의 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="0242a-137">Enter a value between 64 kilobytes (KB) and 4 gigabytes (GB).</span></span>
<span data-ttu-id="0242a-138">64KB(65536)로 나눌 수 있는 값이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0242a-138">The value must be divisible by 64 KB (65536).</span></span>

<span data-ttu-id="0242a-139">이 매개 변수는 클래식 이벤트 로그를 나타내는 **system.web. EventLog** 개체의 **maximumkilobytes** 속성 값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0242a-139">This parameter specifies the value of the **MaximumKilobytes** property of the **System.Diagnostics.EventLog** object that represents a classic event log.</span></span>

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0242a-140">-OverflowAction</span><span class="sxs-lookup"><span data-stu-id="0242a-140">-OverflowAction</span></span>
<span data-ttu-id="0242a-141">이벤트 로그가 최대 크기에 도달할 경우 수행할 작업을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0242a-141">Specifies what happens when the event log reaches its maximum size.</span></span>

<span data-ttu-id="0242a-142">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="0242a-142">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="0242a-143">DoNotOverwrite: 기존 항목은 유지 되 고 새 항목은 삭제 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0242a-143">DoNotOverwrite:  Existing entries are retained and new entries are discarded.</span></span>
- <span data-ttu-id="0242a-144">OverwriteAsNeeded: 각각의 새 항목이 가장 오래 된 항목을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="0242a-144">OverwriteAsNeeded:  Each new entry overwrites the oldest entry.</span></span>
- <span data-ttu-id="0242a-145">OverwriteOlder: 새 이벤트는 새 **이벤트는이 속성에** 지정 된 값 보다 오래 된 이벤트를 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="0242a-145">OverwriteOlder:  New events overwrite events older than the value specified by the **MinimumRetentionDays** property.</span></span> <span data-ttu-id="0242a-146">이 **속성 값에 지정 된 것** 보다 오래 된 이벤트가 없는 경우 새 이벤트가 삭제 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0242a-146">If there are no events older than specified by the **MinimumRetentionDays** property value, new events are discarded.</span></span>

<span data-ttu-id="0242a-147">이 매개 변수는 클래식 이벤트 로그를 나타내는 **OverflowAction** 개체 **의** 속성 값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0242a-147">This parameter specifies the value of the **OverflowAction** property of the **System.Diagnostics.EventLog** object that represents a classic event log.</span></span>

```yaml
Type: System.Diagnostics.OverflowAction
Parameter Sets: (All)
Aliases: OFA
Accepted values: OverwriteOlder, OverwriteAsNeeded, DoNotOverwrite

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0242a-148">-보존 기간 (일)</span><span class="sxs-lookup"><span data-stu-id="0242a-148">-RetentionDays</span></span>
<span data-ttu-id="0242a-149">이벤트 로그에서 이벤트를 유지해야 할 최소 일수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0242a-149">Specifies the minimum number of days that an event must remain in the event log.</span></span>

<span data-ttu-id="0242a-150">이 매개 변수는 클래식 이벤트 로그를 나타내는 **system.object** **속성의 값을 지정** 합니다.</span><span class="sxs-lookup"><span data-stu-id="0242a-150">This parameter specifies the value of the **MinimumRetentionDays** property of the **System.Diagnostics.EventLog** object that represents a classic event log.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: MRD

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0242a-151">-Confirm</span><span class="sxs-lookup"><span data-stu-id="0242a-151">-Confirm</span></span>
<span data-ttu-id="0242a-152">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="0242a-152">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="0242a-153">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="0242a-153">-WhatIf</span></span>
<span data-ttu-id="0242a-154">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="0242a-154">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="0242a-155">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0242a-155">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="0242a-156">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0242a-156">CommonParameters</span></span>
<span data-ttu-id="0242a-157">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="0242a-157">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0242a-158">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0242a-158">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="0242a-159">입력</span><span class="sxs-lookup"><span data-stu-id="0242a-159">INPUTS</span></span>

### <span data-ttu-id="0242a-160">없음</span><span class="sxs-lookup"><span data-stu-id="0242a-160">None</span></span>
<span data-ttu-id="0242a-161">이 cmdlet에 입력을 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0242a-161">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="0242a-162">출력</span><span class="sxs-lookup"><span data-stu-id="0242a-162">OUTPUTS</span></span>

### <span data-ttu-id="0242a-163">없음</span><span class="sxs-lookup"><span data-stu-id="0242a-163">None</span></span>
<span data-ttu-id="0242a-164">이 cmdlet은 어떠한 출력도 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0242a-164">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="0242a-165">참고</span><span class="sxs-lookup"><span data-stu-id="0242a-165">NOTES</span></span>

* <span data-ttu-id="0242a-166">Windows Vista 이상 버전에서이 cmdlet을 사용 하려면 관리자 권한으로 실행 옵션을 사용 하 여 Windows PowerShell을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="0242a-166">To use this cmdlet on Windows Vista and later versions of Windows, open Windows PowerShell with the Run as administrator option.</span></span>

  <span data-ttu-id="0242a-167">이 cmdlet은 클래식 이벤트 로그를 나타내는 **system.web** 이벤트 로그 개체의 속성을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="0242a-167">This cmdlet changes the properties of the **System.Diagnostics.EventLog** object that represents a classic event log.</span></span>
<span data-ttu-id="0242a-168">이벤트 로그 속성의 현재 설정을 보려면을 입력 `Get-EventLog -List` 합니다.</span><span class="sxs-lookup"><span data-stu-id="0242a-168">To see the current settings of the event log properties, type `Get-EventLog -List`.</span></span>

*

## <span data-ttu-id="0242a-169">관련 링크</span><span class="sxs-lookup"><span data-stu-id="0242a-169">RELATED LINKS</span></span>

[<span data-ttu-id="0242a-170">Clear-EventLog</span><span class="sxs-lookup"><span data-stu-id="0242a-170">Clear-EventLog</span></span>](Clear-EventLog.md)

[<span data-ttu-id="0242a-171">Get-EventLog</span><span class="sxs-lookup"><span data-stu-id="0242a-171">Get-EventLog</span></span>](Get-EventLog.md)

[<span data-ttu-id="0242a-172">Limit-EventLog</span><span class="sxs-lookup"><span data-stu-id="0242a-172">Limit-EventLog</span></span>](Limit-EventLog.md)

[<span data-ttu-id="0242a-173">New-EventLog</span><span class="sxs-lookup"><span data-stu-id="0242a-173">New-EventLog</span></span>](New-EventLog.md)

[<span data-ttu-id="0242a-174">Remove-EventLog</span><span class="sxs-lookup"><span data-stu-id="0242a-174">Remove-EventLog</span></span>](Remove-EventLog.md)

[<span data-ttu-id="0242a-175">Show-EventLog</span><span class="sxs-lookup"><span data-stu-id="0242a-175">Show-EventLog</span></span>](Show-EventLog.md)

[<span data-ttu-id="0242a-176">Write-EventLog</span><span class="sxs-lookup"><span data-stu-id="0242a-176">Write-EventLog</span></span>](Write-EventLog.md)
