---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/clear-eventlog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-EventLog
ms.openlocfilehash: 695a13d4fbbf60caadeed994c1aa9c36432be917
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93215562"
---
# <span data-ttu-id="34b03-103">Clear-EventLog</span><span class="sxs-lookup"><span data-stu-id="34b03-103">Clear-EventLog</span></span>

## <span data-ttu-id="34b03-104">개요</span><span class="sxs-lookup"><span data-stu-id="34b03-104">SYNOPSIS</span></span>
<span data-ttu-id="34b03-105">로컬 또는 원격 컴퓨터의 지정 된 이벤트 로그에서 모든 항목을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="34b03-105">Clears all entries from specified event logs on the local or remote computers.</span></span>

## <span data-ttu-id="34b03-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="34b03-106">SYNTAX</span></span>

```
Clear-EventLog [-LogName] <String[]> [[-ComputerName] <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="34b03-107">설명</span><span class="sxs-lookup"><span data-stu-id="34b03-107">DESCRIPTION</span></span>

<span data-ttu-id="34b03-108">`Clear-EventLog`Cmdlet은 로컬 컴퓨터 또는 원격 컴퓨터의 지정 된 이벤트 로그에서 모든 항목을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="34b03-108">The `Clear-EventLog` cmdlet deletes all of the entries from the specified event logs on the local computer or on remote computers.</span></span>
<span data-ttu-id="34b03-109">를 사용 하려면 `Clear-EventLog` 영향을 받는 컴퓨터에서 Administrators 그룹의 구성원 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="34b03-109">To use `Clear-EventLog`, you must be a member of the Administrators group on the affected computer.</span></span>

<span data-ttu-id="34b03-110">**Eventlog** 명사를 포함 하는 Cmdlet (eventlog cmdlet)은 클래식 이벤트 로그 에서만 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="34b03-110">The cmdlets that contain the **EventLog** noun (the EventLog cmdlets) work only on classic event logs.</span></span>
<span data-ttu-id="34b03-111">Windows Vista 이상 버전의 windows 이벤트 로그 기술을 사용 하는 로그에서 이벤트를 가져오려면 Get-WinEvent cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="34b03-111">To get events from logs that use the Windows Event Log technology in Windows Vista and later versions of Windows, use the Get-WinEvent cmdlet.</span></span>

## <span data-ttu-id="34b03-112">예제</span><span class="sxs-lookup"><span data-stu-id="34b03-112">EXAMPLES</span></span>

### <span data-ttu-id="34b03-113">예 1: 로컬 컴퓨터에서 특정 이벤트 로그 유형 지우기</span><span class="sxs-lookup"><span data-stu-id="34b03-113">Example 1: Clear specific event log types from the local computer</span></span>

```powershell
Clear-EventLog "Windows PowerShell"
```

<span data-ttu-id="34b03-114">이 명령은 로컬 컴퓨터의 Windows PowerShell 이벤트 로그에서 항목을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="34b03-114">This command clears the entries from the Windows PowerShell event log on the local computer.</span></span>

### <span data-ttu-id="34b03-115">예 2: 로컬 및 원격 컴퓨터에서 특정 다중 로그 형식 지우기</span><span class="sxs-lookup"><span data-stu-id="34b03-115">Example 2: Clear specific multiple log types from the local and remote computers</span></span>

```powershell
Clear-EventLog -LogName ODiag, OSession -ComputerName localhost, Server02
```

<span data-ttu-id="34b03-116">이 명령은 로컬 컴퓨터와 Server02 원격 컴퓨터의 ODiag (Microsoft Office 진단) 및 Microsoft Office 세션 (Odiag) 로그에 있는 모든 항목을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="34b03-116">This command clears all of the entries in the Microsoft Office Diagnostics (ODiag) and Microsoft Office Sessions (OSession) logs on the local computer and the Server02 remote computer.</span></span>

### <span data-ttu-id="34b03-117">예 3: 지정 된 컴퓨터의 모든 로그를 지우고 이벤트 로그 목록을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="34b03-117">Example 3: Clear all logs on the specified computers then display the event log list</span></span>

```powershell
Clear-EventLog -LogName application, system -confirm
```

<span data-ttu-id="34b03-118">이 명령은 지정된 이벤트 로그의 항목을 삭제하기 전에 사용자에게 확인 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="34b03-118">This command prompts you for confirmation before deleting the entries in the specified event logs.</span></span>

### <span data-ttu-id="34b03-119">예 4: 지정 된 컴퓨터의 모든 로그를 지우고 이벤트 로그 목록을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="34b03-119">Example 4: Clear all logs on the specified computers then display the event log list</span></span>

```powershell
function clear-all-event-logs ($computerName="localhost")
{
   $logs = Get-EventLog -ComputerName $computername -List | ForEach-Object {$_.Log}
   $logs | ForEach-Object {Clear-EventLog -ComputerName $computername -LogName $_ }
   Get-EventLog -ComputerName $computername -list
}

clear-all-event-logs -ComputerName Server01
```

```Output
Max(K) Retain OverflowAction        Entries Log
------ ------ --------------        ------- ---
15,168      0 OverwriteAsNeeded           0 Application
15,168      0 OverwriteAsNeeded           0 DFS Replication
512         7 OverwriteOlder              0 DxStudio
20,480      0 OverwriteAsNeeded           0 Hardware Events
512         7 OverwriteOlder              0 Internet Explorer
20,480      0 OverwriteAsNeeded           0 Key Management Service
16,384      0 OverwriteAsNeeded           0 Microsoft Office Diagnostics
16,384      0 OverwriteAsNeeded           0 Microsoft Office Sessions
30,016      0 OverwriteAsNeeded           1 Security
15,168      0 OverwriteAsNeeded           2 System
15,360      0 OverwriteAsNeeded           0 Windows PowerShell
```

<span data-ttu-id="34b03-120">이 함수는 지정된 컴퓨터의 모든 이벤트 로그를 지운 다음 결과 이벤트 로그 목록을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="34b03-120">This function clears all event logs on the specified computers and then displays the resulting event log list.</span></span>

<span data-ttu-id="34b03-121">로그를 지운 후 표시하기 전에 시스템 로그 및 보안 로그에 몇 개의 항목이 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="34b03-121">Notice that a few entries were added to the System and Security logs after the logs were cleared but before they were displayed.</span></span>

## <span data-ttu-id="34b03-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="34b03-122">PARAMETERS</span></span>

### <span data-ttu-id="34b03-123">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="34b03-123">-ComputerName</span></span>

<span data-ttu-id="34b03-124">원격 컴퓨터를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="34b03-124">Specifies a remote computer.</span></span>
<span data-ttu-id="34b03-125">기본값은 로컬 컴퓨터입니다.</span><span class="sxs-lookup"><span data-stu-id="34b03-125">The default is the local computer.</span></span>

<span data-ttu-id="34b03-126">원격 컴퓨터의 NetBIOS 이름, IP(인터넷 프로토콜) 주소 또는 정규화된 도메인 이름을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="34b03-126">Type the NetBIOS name, an Internet Protocol (IP) address, or a fully qualified domain name of a remote computer.</span></span>
<span data-ttu-id="34b03-127">로컬 컴퓨터를 지정하려면 컴퓨터 이름, 점(.) 또는 "localhost"를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="34b03-127">To specify the local computer, type the computer name, a dot (.), or "localhost".</span></span>

<span data-ttu-id="34b03-128">이 매개 변수는 Windows PowerShell 원격 기능을 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="34b03-128">This parameter does not rely on Windows PowerShell remoting.</span></span>
<span data-ttu-id="34b03-129">**ComputerName** `Get-EventLog` 컴퓨터가 원격 명령을 실행 하도록 구성 되지 않은 경우에도의 ComputerName 매개 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34b03-129">You can use the **ComputerName** parameter of `Get-EventLog` even if your computer is not configured to run remote commands.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Cn

Required: False
Position: 1
Default value: Local computer
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="34b03-130">-LogName</span><span class="sxs-lookup"><span data-stu-id="34b03-130">-LogName</span></span>

<span data-ttu-id="34b03-131">이벤트 로그를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="34b03-131">Specifies the event logs.</span></span>
<span data-ttu-id="34b03-132">하나 이상 이벤트 로그의 로그 이름(Log 표시 이름이 아닌 Log 속성의 값)을 쉼표로 구분하여 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="34b03-132">Enter the log name (the value of the Log property; not the LogDisplayName) of one or more event logs, separated by commas.</span></span>
<span data-ttu-id="34b03-133">와일드카드 문자는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="34b03-133">Wildcard characters are not permitted.</span></span>
<span data-ttu-id="34b03-134">이 매개 변수는 필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="34b03-134">This parameter is required.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: LN

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="34b03-135">-Confirm</span><span class="sxs-lookup"><span data-stu-id="34b03-135">-Confirm</span></span>

<span data-ttu-id="34b03-136">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="34b03-136">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="34b03-137">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="34b03-137">-WhatIf</span></span>

<span data-ttu-id="34b03-138">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="34b03-138">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="34b03-139">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="34b03-139">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="34b03-140">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="34b03-140">CommonParameters</span></span>

<span data-ttu-id="34b03-141">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="34b03-141">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="34b03-142">자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="34b03-142">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="34b03-143">입력</span><span class="sxs-lookup"><span data-stu-id="34b03-143">INPUTS</span></span>

### <span data-ttu-id="34b03-144">없음</span><span class="sxs-lookup"><span data-stu-id="34b03-144">None</span></span>

<span data-ttu-id="34b03-145">개체를에 연결할 수 없습니다 `Clear-EventLog` .</span><span class="sxs-lookup"><span data-stu-id="34b03-145">You cannot pipe objects to `Clear-EventLog`.</span></span>

## <span data-ttu-id="34b03-146">출력</span><span class="sxs-lookup"><span data-stu-id="34b03-146">OUTPUTS</span></span>

### <span data-ttu-id="34b03-147">없음</span><span class="sxs-lookup"><span data-stu-id="34b03-147">None</span></span>

<span data-ttu-id="34b03-148">이 cmdlet은 어떠한 출력도 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="34b03-148">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="34b03-149">참고</span><span class="sxs-lookup"><span data-stu-id="34b03-149">NOTES</span></span>

- <span data-ttu-id="34b03-150">Windows `Clear-EventLog` Vista 이상 버전에서을 사용 하려면 "관리자 권한으로 실행" 옵션을 사용 하 여 Windows PowerShell을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="34b03-150">To use `Clear-EventLog` on Windows Vista and later versions of Windows, start Windows PowerShell with the "Run as administrator" option.</span></span>

## <span data-ttu-id="34b03-151">관련 링크</span><span class="sxs-lookup"><span data-stu-id="34b03-151">RELATED LINKS</span></span>

[<span data-ttu-id="34b03-152">Get-EventLog</span><span class="sxs-lookup"><span data-stu-id="34b03-152">Get-EventLog</span></span>](Get-EventLog.md)

[<span data-ttu-id="34b03-153">Limit-EventLog</span><span class="sxs-lookup"><span data-stu-id="34b03-153">Limit-EventLog</span></span>](Limit-EventLog.md)

[<span data-ttu-id="34b03-154">New-EventLog</span><span class="sxs-lookup"><span data-stu-id="34b03-154">New-EventLog</span></span>](New-EventLog.md)

[<span data-ttu-id="34b03-155">Remove-EventLog</span><span class="sxs-lookup"><span data-stu-id="34b03-155">Remove-EventLog</span></span>](Remove-EventLog.md)

[<span data-ttu-id="34b03-156">Show-EventLog</span><span class="sxs-lookup"><span data-stu-id="34b03-156">Show-EventLog</span></span>](Show-EventLog.md)

[<span data-ttu-id="34b03-157">Write-EventLog</span><span class="sxs-lookup"><span data-stu-id="34b03-157">Write-EventLog</span></span>](Write-EventLog.md)
