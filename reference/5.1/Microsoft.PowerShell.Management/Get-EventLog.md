---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 3/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-eventlog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-EventLog
ms.openlocfilehash: ab1a97dc3c78bbfdcc239fd573ef3b1f839e2b21
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93215466"
---
# <span data-ttu-id="1a20f-103">Get-EventLog</span><span class="sxs-lookup"><span data-stu-id="1a20f-103">Get-EventLog</span></span>

## <span data-ttu-id="1a20f-104">개요</span><span class="sxs-lookup"><span data-stu-id="1a20f-104">SYNOPSIS</span></span>
<span data-ttu-id="1a20f-105">로컬 컴퓨터 또는 원격 컴퓨터에 있는 이벤트 로그의 이벤트 또는 이벤트 로그 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-105">Gets the events in an event log, or a list of the event logs, on the local computer or remote computers.</span></span>

## <span data-ttu-id="1a20f-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="1a20f-106">SYNTAX</span></span>

### <span data-ttu-id="1a20f-107">LogName (기본값)</span><span class="sxs-lookup"><span data-stu-id="1a20f-107">LogName (Default)</span></span>

```
Get-EventLog [-LogName] <String> [-ComputerName <String[]>] [-Newest <Int32>] [-After <DateTime>]
 [-Before <DateTime>] [-UserName <String[]>] [[-InstanceId] <Int64[]>] [-Index <Int32[]>]
 [-EntryType <String[]>] [-Source <String[]>] [-Message <String>] [-AsBaseObject]
 [<CommonParameters>]
```

### <span data-ttu-id="1a20f-108">목록</span><span class="sxs-lookup"><span data-stu-id="1a20f-108">List</span></span>

```
Get-EventLog [-ComputerName <String[]>] [-List] [-AsString] [<CommonParameters>]
```

## <span data-ttu-id="1a20f-109">설명</span><span class="sxs-lookup"><span data-stu-id="1a20f-109">DESCRIPTION</span></span>

<span data-ttu-id="1a20f-110">`Get-EventLog`Cmdlet은 로컬 및 원격 컴퓨터에서 이벤트 및 이벤트 로그를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-110">The `Get-EventLog` cmdlet gets events and event logs from local and remote computers.</span></span> <span data-ttu-id="1a20f-111">기본적으로 `Get-EventLog` 는 로컬 컴퓨터에서 로그를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-111">By default, `Get-EventLog` gets logs from the local computer.</span></span> <span data-ttu-id="1a20f-112">원격 컴퓨터에서 로그를 가져오려면 **ComputerName** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-112">To get logs from remote computers, use the **ComputerName** parameter.</span></span>

<span data-ttu-id="1a20f-113">`Get-EventLog`매개 변수 및 속성 값을 사용 하 여 이벤트를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-113">You can use the `Get-EventLog` parameters and property values to search for events.</span></span> <span data-ttu-id="1a20f-114">Cmdlet은 지정 된 속성 값과 일치 하는 이벤트를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-114">The cmdlet gets events that match the specified property values.</span></span>

<span data-ttu-id="1a20f-115">명사를 포함 하는 PowerShell cmdlet은 `EventLog` 응용 프로그램, 시스템 또는 보안과 같은 Windows 클래식 이벤트 로그 에서만 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-115">PowerShell cmdlets that contain the `EventLog` noun work only on Windows classic event logs such as Application, System, or Security.</span></span> <span data-ttu-id="1a20f-116">Windows Vista 이상 버전의 windows 이벤트 로그 기술을 사용 하는 로그를 가져오려면를 사용 `Get-WinEvent` 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-116">To get logs that use the Windows Event Log technology in Windows Vista and later Windows versions, use `Get-WinEvent`.</span></span>

> [!NOTE]
> <span data-ttu-id="1a20f-117">`Get-EventLog` 는 사용 되지 않는 Win32 API를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-117">`Get-EventLog` uses a Win32 API that is deprecated.</span></span> <span data-ttu-id="1a20f-118">결과가 정확 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-118">The results may not be accurate.</span></span> <span data-ttu-id="1a20f-119">`Get-WinEvent`대신 cmdlet을 사용 하십시오.</span><span class="sxs-lookup"><span data-stu-id="1a20f-119">Use the `Get-WinEvent` cmdlet instead.</span></span>

## <span data-ttu-id="1a20f-120">예제</span><span class="sxs-lookup"><span data-stu-id="1a20f-120">EXAMPLES</span></span>

### <span data-ttu-id="1a20f-121">예 1: 로컬 컴퓨터에서 이벤트 로그 가져오기</span><span class="sxs-lookup"><span data-stu-id="1a20f-121">Example 1: Get event logs on the local computer</span></span>

<span data-ttu-id="1a20f-122">이 예에서는 로컬 컴퓨터에서 사용할 수 있는 이벤트 로그 목록을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-122">This example displays the list of event logs that are available on the local computer.</span></span> <span data-ttu-id="1a20f-123">로그 열의 이름은 이벤트를 검색 하는 로그를 지정 하기 위해 **LogName** 매개 변수와 함께 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-123">The names in the Log column are used with the **LogName** parameter to specify which log is searched for events.</span></span>

```powershell
Get-EventLog -List
```

```Output
Max(K)   Retain   OverflowAction      Entries  Log
------   ------   --------------      -------  ---
15,168        0   OverwriteAsNeeded   20,792   Application
15,168        0   OverwriteAsNeeded   12,559   System
15,360        0   OverwriteAsNeeded   11,173   Windows PowerShell
```

<span data-ttu-id="1a20f-124">`Get-EventLog`Cmdlet은 **List** 매개 변수를 사용 하 여 사용 가능한 로그를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-124">The `Get-EventLog` cmdlet uses the **List** parameter to display the available logs.</span></span>

### <span data-ttu-id="1a20f-125">예 2: 로컬 컴퓨터의 이벤트 로그에서 최근 항목 가져오기</span><span class="sxs-lookup"><span data-stu-id="1a20f-125">Example 2: Get recent entries from an event log on the local computer</span></span>

<span data-ttu-id="1a20f-126">이 예제에서는 시스템 이벤트 로그에서 최근 항목을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-126">This example gets recent entries from the System event log.</span></span>

```powershell
Get-EventLog -LogName System -Newest 5
```

```Output
Index   Time          EntryType    Source              InstanceID   Message
-----   ----          ---------    ------              ----------   -------
13820   Jan 17 19:16  Error        DCOM                     10016   The description for Event...
13819   Jan 17 19:08  Error        DCOM                     10016   The description for Event...
13818   Jan 17 19:06  Information  Service Control...  1073748864   The start type of the Back...
13817   Jan 17 19:05  Error        DCOM                     10016   The description for Event...
13815   Jan 17 19:03  Information  Microsoft-Windows...        35   The time service is now sync...
```

<span data-ttu-id="1a20f-127">`Get-EventLog`Cmdlet은 **LogName** 매개 변수를 사용 하 여 시스템 이벤트 로그를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-127">The `Get-EventLog` cmdlet uses the **LogName** parameter to specify the System event log.</span></span> <span data-ttu-id="1a20f-128">**최신** 매개 변수는 최근 5 개의 이벤트를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-128">The **Newest** parameter returns the five most recent events.</span></span>

### <span data-ttu-id="1a20f-129">예 3: 이벤트 로그의 특정 항목 수에 대 한 모든 소스 찾기</span><span class="sxs-lookup"><span data-stu-id="1a20f-129">Example 3: Find all sources for a specific number of entries in an event log</span></span>

<span data-ttu-id="1a20f-130">이 예제에서는 시스템 이벤트 로그에서 가장 최근 1000 항목에 포함 된 모든 원본을 찾는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-130">This example shows how to find all of the sources that are included in the 1000 most recent entries in the System event log.</span></span>

```powershell
$Events = Get-EventLog -LogName System -Newest 1000
$Events | Group-Object -Property Source -NoElement | Sort-Object -Property Count -Descending
```

```Output
Count   Name
-----   ----
  110   DCOM
   65   Service Control Manager
   51   Microsoft-Windows-Kern...
   14   EventLog
   14   BTHUSB
   13   Win32k
```

<span data-ttu-id="1a20f-131">`Get-EventLog`Cmdlet은 **LogName** 매개 변수를 사용 하 여 시스템 로그를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-131">The `Get-EventLog` cmdlet uses the **LogName** parameter to specify the System log.</span></span> <span data-ttu-id="1a20f-132">**최신** 매개 변수는 1000 최신 이벤트를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-132">The **Newest** parameter selects the 1000 most recent events.</span></span> <span data-ttu-id="1a20f-133">이벤트 개체는 변수에 저장 됩니다 `$Events` .</span><span class="sxs-lookup"><span data-stu-id="1a20f-133">The event objects are stored in the `$Events` variable.</span></span> <span data-ttu-id="1a20f-134">`$Events`개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Group-Object` .</span><span class="sxs-lookup"><span data-stu-id="1a20f-134">The `$Events` objects are sent down the pipeline to the `Group-Object` cmdlet.</span></span>
<span data-ttu-id="1a20f-135">`Group-Object`**Property** 매개 변수를 사용 하 여 개체를 원본 별로 그룹화 하 고 각 원본에 대 한 개체 수를 계산 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-135">`Group-Object` uses the **Property** parameter to group the objects by source and counts the number of objects for each source.</span></span> <span data-ttu-id="1a20f-136">**Noelement** 매개 변수는 출력에서 그룹 멤버를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-136">The **NoElement** parameter removes the group members from the output.</span></span>
<span data-ttu-id="1a20f-137">이 `Sort-Object` cmdlet은 **Property** 매개 변수를 사용 하 여 각 소스 이름의 수를 기준으로 정렬 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-137">The `Sort-Object` cmdlet uses the **Property** parameter to sort by the count of each source name.</span></span>
<span data-ttu-id="1a20f-138">**내림차순** 매개 변수는 목록을 순서 대로 오름차순으로 정렬 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-138">The **Descending** parameter sorts the list in order by count from highest to lowest.</span></span>

### <span data-ttu-id="1a20f-139">예 4: 특정 이벤트 로그에서 오류 이벤트 가져오기</span><span class="sxs-lookup"><span data-stu-id="1a20f-139">Example 4: Get error events from a specific event log</span></span>

<span data-ttu-id="1a20f-140">이 예제에서는 시스템 이벤트 로그에서 오류 이벤트를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-140">This example gets error events from the System event log.</span></span>

```powershell
Get-EventLog -LogName System -EntryType Error
```

```Output
Index Time          EntryType   Source  InstanceID Message
----- ----          ---------   ------  ---------- -------
13296 Jan 16 13:53  Error       DCOM    10016 The description for Event ID '10016' in Source...
13291 Jan 16 13:51  Error       DCOM    10016 The description for Event ID '10016' in Source...
13245 Jan 16 11:45  Error       DCOM    10016 The description for Event ID '10016' in Source...
13230 Jan 16 11:07  Error       DCOM    10016 The description for Event ID '10016' in Source...
```

<span data-ttu-id="1a20f-141">`Get-EventLog`Cmdlet은 **LogName** 매개 변수를 사용 하 여 시스템 로그를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-141">The `Get-EventLog` cmdlet uses the **LogName** parameter to specify the System log.</span></span> <span data-ttu-id="1a20f-142">**Entrytype 관련이** 매개 변수는 이벤트를 필터링 하 여 오류 이벤트만 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-142">The **EntryType** parameter filters the events to show only Error events.</span></span>

### <span data-ttu-id="1a20f-143">예 5: InstanceId 및 Source 값을 사용 하 여 이벤트 로그에서 이벤트 가져오기</span><span class="sxs-lookup"><span data-stu-id="1a20f-143">Example 5: Get events from an event log with an InstanceId and Source value</span></span>

<span data-ttu-id="1a20f-144">이 예에서는 시스템 로그에서 특정 InstanceId 및 원본에 대 한 이벤트를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-144">This example gets events from the System log for a specific InstanceId and Source.</span></span>

```powershell
Get-EventLog -LogName System -InstanceId 10016 -Source DCOM
```

```Output
Index Time          EntryType  Source  InstanceID  Message
----- ----          ---------  ------  ----------  -------
13245 Jan 16 11:45  Error      DCOM         10016  The description for Event ID '10016' in Source...
13230 Jan 16 11:07  Error      DCOM         10016  The description for Event ID '10016' in Source...
13219 Jan 16 10:00  Error      DCOM         10016  The description for Event ID '10016' in Source...
```

<span data-ttu-id="1a20f-145">`Get-EventLog`Cmdlet은 **LogName** 매개 변수를 사용 하 여 시스템 로그를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-145">The `Get-EventLog` cmdlet uses the **LogName** parameter to specify the System log.</span></span> <span data-ttu-id="1a20f-146">**InstanceID** 매개 변수는 지정 된 인스턴스 ID를 가진 이벤트를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-146">The **InstanceID** parameter selects the events with the specified Instance ID.</span></span> <span data-ttu-id="1a20f-147">**Source** 매개 변수는 이벤트 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-147">The **Source** parameter specifies the event property.</span></span>

### <span data-ttu-id="1a20f-148">예제 6: 여러 컴퓨터에서 이벤트 가져오기</span><span class="sxs-lookup"><span data-stu-id="1a20f-148">Example 6: Get events from multiple computers</span></span>

<span data-ttu-id="1a20f-149">이 명령은 Server01, Server02 및 Server03 컴퓨터의 시스템 이벤트 로그에서 이벤트를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-149">This command gets the events from the System event log on three computers: Server01, Server02, and Server03.</span></span>

```powershell
Get-EventLog -LogName System -ComputerName Server01, Server02, Server03
```

<span data-ttu-id="1a20f-150">`Get-EventLog`Cmdlet은 **LogName** 매개 변수를 사용 하 여 시스템 로그를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-150">The `Get-EventLog` cmdlet uses the **LogName** parameter to specify the System log.</span></span> <span data-ttu-id="1a20f-151">**ComputerName** 매개 변수는 쉼표로 구분 된 문자열을 사용 하 여 이벤트 로그를 가져오려는 컴퓨터를 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-151">The **ComputerName** parameter uses a comma-separated string to list the computers from which you want to get the event logs.</span></span>

### <span data-ttu-id="1a20f-152">예 7: 메시지에 특정 단어가 포함 된 모든 이벤트 가져오기</span><span class="sxs-lookup"><span data-stu-id="1a20f-152">Example 7: Get all events that include a specific word in the message</span></span>

<span data-ttu-id="1a20f-153">이 명령은 이벤트 메시지의 특정 단어가 포함 된 시스템 이벤트 로그의 모든 이벤트를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-153">This command gets all the events in the System event log that contain a specific word in the event's message.</span></span> <span data-ttu-id="1a20f-154">지정 된 **메시지** 매개 변수의 값이 메시지의 콘텐츠에 포함 되지만 PowerShell 콘솔에는 표시 되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-154">It's possible that your specified **Message** parameter's value is included in the message's content but isn't displayed on the PowerShell console.</span></span>

```powershell
Get-EventLog -LogName System -Message *description*
```

```Output
Index Time          EntryType   Source       InstanceID   Message
----- ----          ---------   ------       ----------   -------
13821 Jan 17 19:17  Error       DCOM              10016   The description for Event ID '10016'...
13820 Jan 17 19:16  Error       DCOM              10016   The description for Event ID '10016'...
13819 Jan 17 19:08  Error       DCOM              10016   The description for Event ID '10016'...
```

<span data-ttu-id="1a20f-155">`Get-EventLog`Cmdlet은 **LogName** 매개 변수를 사용 하 여 시스템 이벤트 로그를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-155">The `Get-EventLog` cmdlet uses the **LogName** parameter to specify the System event log.</span></span> <span data-ttu-id="1a20f-156">**메시지** 매개 변수는 각 이벤트의 메시지 필드에서 검색할 단어를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-156">The **Message** parameter specifies a word to search for in the message field of each event.</span></span>

### <span data-ttu-id="1a20f-157">예 8: 이벤트의 속성 값 표시</span><span class="sxs-lookup"><span data-stu-id="1a20f-157">Example 8: Display the property values of an event</span></span>

<span data-ttu-id="1a20f-158">이 예제에서는 이벤트의 모든 속성 및 값을 표시 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-158">This example shows how to display all of an event's properties and values.</span></span>

```powershell
$A = Get-EventLog -LogName System -Newest 1
$A | Select-Object -Property *
```

```Output
EventID            : 10016
MachineName        : localhost
Data               : {}
Index              : 13821
Category           : (0)
CategoryNumber     : 0
EntryType          : Error
Message            : The description for Event ID '10016' in Source 'DCOM'...
Source             : DCOM
ReplacementStrings : {Local,...}
InstanceId         : 10016
TimeGenerated      : 1/17/2019 19:17:23
TimeWritten        : 1/17/2019 19:17:23
UserName           : username
Site               :
Container          :
```

<span data-ttu-id="1a20f-159">`Get-EventLog`Cmdlet은 **LogName** 매개 변수를 사용 하 여 시스템 이벤트 로그를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-159">The `Get-EventLog` cmdlet uses the **LogName** parameter to specify the System event log.</span></span> <span data-ttu-id="1a20f-160">**최신** 매개 변수는 가장 최근 이벤트 개체를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-160">The **Newest** parameter selects the most recent event object.</span></span> <span data-ttu-id="1a20f-161">개체는 변수에 저장 됩니다 `$A` .</span><span class="sxs-lookup"><span data-stu-id="1a20f-161">The object is stored in the `$A` variable.</span></span> <span data-ttu-id="1a20f-162">변수의 개체는 `$A` 파이프라인에서 cmdlet으로 전송 됩니다 `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="1a20f-162">The object in the `$A` variable is sent down the pipeline to the `Select-Object` cmdlet.</span></span>
<span data-ttu-id="1a20f-163">`Select-Object` 별표 ()와 함께 **Property** 매개 변수를 사용 `*` 하 여 개체의 모든 속성을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-163">`Select-Object` uses the **Property** parameter with an asterisk (`*`) to select all of the object's properties.</span></span>

### <span data-ttu-id="1a20f-164">예 9: 원본 및 이벤트 ID를 사용 하 여 이벤트 로그에서 이벤트 가져오기</span><span class="sxs-lookup"><span data-stu-id="1a20f-164">Example 9: Get events from an event log using a source and event ID</span></span>

<span data-ttu-id="1a20f-165">이 예제에서는 지정 된 원본 및 이벤트 ID에 대 한 이벤트를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-165">This example gets events for a specified Source and Event ID.</span></span>

```powershell
Get-EventLog -LogName Application -Source Outlook | Where-Object {$_.EventID -eq 63} |
              Select-Object -Property Source, EventID, InstanceId, Message
```

```Output
Source   EventID   InstanceId   Message
------   -------   ----------   -------
Outlook       63   1073741887   The Exchange web service request succeeded.
Outlook       63   1073741887   Outlook detected a change notification.
Outlook       63   1073741887   The Exchange web service request succeeded.
```

<span data-ttu-id="1a20f-166">`Get-EventLog`Cmdlet은 **LogName** 매개 변수를 사용 하 여 응용 프로그램 이벤트 로그를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-166">The `Get-EventLog` cmdlet uses the **LogName** parameter to specify the Application event log.</span></span> <span data-ttu-id="1a20f-167">**원본** 매개 변수는 응용 프로그램 이름인 Outlook을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-167">The **Source** parameter specifies the application name, Outlook.</span></span> <span data-ttu-id="1a20f-168">개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Where-Object` .</span><span class="sxs-lookup"><span data-stu-id="1a20f-168">The objects are sent down the pipeline to the `Where-Object` cmdlet.</span></span> <span data-ttu-id="1a20f-169">Cmdlet은 파이프라인의 각 개체에 대해 `Where-Object` 변수를 사용 하 여 `$_.EventID` 이벤트 ID 속성을 지정 된 값과 비교 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-169">For each object in the pipeline, the `Where-Object` cmdlet uses the variable `$_.EventID` to compare the Event ID property to the specified value.</span></span> <span data-ttu-id="1a20f-170">개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="1a20f-170">The objects are sent down the pipeline to the `Select-Object` cmdlet.</span></span> <span data-ttu-id="1a20f-171">`Select-Object`**Property** 매개 변수를 사용 하 여 PowerShell 콘솔에 표시할 속성을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-171">`Select-Object` uses the **Property** parameter to select the properties to display in the PowerShell console.</span></span>

### <span data-ttu-id="1a20f-172">예제 10: 속성으로 이벤트 및 그룹 가져오기</span><span class="sxs-lookup"><span data-stu-id="1a20f-172">Example 10: Get events and group by a property</span></span>

```powershell
Get-EventLog -LogName System -UserName NT* | Group-Object -Property UserName -NoElement |
              Select-Object -Property Count, Name
```

```Output
Count  Name
-----  ----
6031   NT AUTHORITY\SYSTEM
  42   NT AUTHORITY\LOCAL SERVICE
   4   NT AUTHORITY\NETWORK SERVICE
```

<span data-ttu-id="1a20f-173">`Get-EventLog`Cmdlet은 **LogName** 매개 변수를 사용 하 여 시스템 로그를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-173">The `Get-EventLog` cmdlet uses the **LogName** parameter to specify the System log.</span></span> <span data-ttu-id="1a20f-174">**UserName** 매개 변수는 별표 ( `*` ) 와일드 카드를 포함 하 여 사용자 이름의 일부를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-174">The **UserName** parameter includes the asterisk (`*`) wildcard to specify a portion of the user name.</span></span> <span data-ttu-id="1a20f-175">이벤트 개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Group-Object` .</span><span class="sxs-lookup"><span data-stu-id="1a20f-175">The event objects are sent down the pipeline to the `Group-Object` cmdlet.</span></span> <span data-ttu-id="1a20f-176">`Group-Object`**property** 매개 변수를 사용 하 **여 사용자 이름 속성을** 사용 하 여 개체를 그룹화 하 고 각 사용자 이름에 대 한 개체 수를 계산 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-176">`Group-Object` uses the **Property** parameter to specify that the **UserName** property is used to group the objects and count the number of objects for each user name.</span></span> <span data-ttu-id="1a20f-177">**Noelement** 매개 변수는 출력에서 그룹 멤버를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-177">The **NoElement** parameter removes the group members from the output.</span></span> <span data-ttu-id="1a20f-178">개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="1a20f-178">The objects are sent down the pipeline to the `Select-Object` cmdlet.</span></span>
<span data-ttu-id="1a20f-179">`Select-Object`**Property** 매개 변수를 사용 하 여 PowerShell 콘솔에 표시할 속성을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-179">`Select-Object` uses the **Property** parameter to select the properties to display in the PowerShell console.</span></span>

### <span data-ttu-id="1a20f-180">예 11: 특정 날짜 및 시간 범위 동안 발생 한 이벤트 가져오기</span><span class="sxs-lookup"><span data-stu-id="1a20f-180">Example 11: Get events that occurred during a specific date and time range</span></span>

<span data-ttu-id="1a20f-181">이 예에서는 지정 된 날짜 및 시간 범위에 대 한 시스템 이벤트 로그에서 오류 이벤트를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-181">This example gets Error events from the System event log for a specified date and time range.</span></span> <span data-ttu-id="1a20f-182">**Before** 및 **After** 매개 변수는 날짜 및 시간 범위를 설정 하지만 출력에서 제외 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-182">The **Before** and **After** parameters set the date and time range but are excluded from the output.</span></span>

```powershell
$Begin = Get-Date -Date '1/17/2019 08:00:00'
$End = Get-Date -Date '1/17/2019 17:00:00'
Get-EventLog -LogName System -EntryType Error -After $Begin -Before $End
```

```Output
Index Time          EntryType   Source   InstanceID  Message
----- ----          ---------   ------   ----------  -------
13821 Jan 17 13:40  Error       DCOM          10016  The description for Event ID...
13820 Jan 17 13:11  Error       DCOM          10016  The description for Event ID...
...
12372 Jan 17 10:08  Error       DCOM          10016  The description for Event ID...
12371 Jan 17 09:04  Error       DCOM          10016  The description for Event ID...
```

<span data-ttu-id="1a20f-183">이 `Get-Date` cmdlet은 **date** 매개 변수를 사용 하 여 날짜 및 시간을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-183">The `Get-Date` cmdlet uses the **Date** parameter to specify a date and time.</span></span> <span data-ttu-id="1a20f-184">**DateTime** 개체는 및 변수에 저장 됩니다 `$Begin` `$End` .</span><span class="sxs-lookup"><span data-stu-id="1a20f-184">The **DateTime** objects are stored in the `$Begin` and `$End` variables.</span></span> <span data-ttu-id="1a20f-185">`Get-EventLog`Cmdlet은 **LogName** 매개 변수를 사용 하 여 시스템 로그를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-185">The `Get-EventLog` cmdlet uses the **LogName** parameter to specify the System log.</span></span> <span data-ttu-id="1a20f-186">**Entrytype 관련이** 매개 변수는 Error 이벤트 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-186">The **EntryType** parameter specifies the Error event type.</span></span> <span data-ttu-id="1a20f-187">날짜 및 시간 범위는 **이후** 매개 변수 및 `$Begin` 변수와 **Before** 매개 변수 및 변수에 의해 설정 됩니다 `$End` .</span><span class="sxs-lookup"><span data-stu-id="1a20f-187">The date and time range is set by the **After** parameter and `$Begin` variable and the **Before** parameter and `$End` variable.</span></span>

## <span data-ttu-id="1a20f-188">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1a20f-188">PARAMETERS</span></span>

### <span data-ttu-id="1a20f-189">-이후</span><span class="sxs-lookup"><span data-stu-id="1a20f-189">-After</span></span>

<span data-ttu-id="1a20f-190">지정 된 날짜 및 시간 이후에 발생 한 이벤트를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-190">Gets events that occurred after a specified date and time.</span></span> <span data-ttu-id="1a20f-191">**이후** 매개 변수 날짜 및 시간이 출력에서 제외 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-191">The **After** parameter date and time are excluded from the output.</span></span> <span data-ttu-id="1a20f-192">Cmdlet에서 반환 되는 값과 같은 **DateTime** 개체를 입력 합니다 `Get-Date` .</span><span class="sxs-lookup"><span data-stu-id="1a20f-192">Enter a **DateTime** object, such as the value returned by the `Get-Date` cmdlet.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: LogName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1a20f-193">-AsBaseObject</span><span class="sxs-lookup"><span data-stu-id="1a20f-193">-AsBaseObject</span></span>

<span data-ttu-id="1a20f-194">이 cmdlet이 각 이벤트에 대 한 표준 **EventLogEntry** 개체를 반환 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-194">Indicates that this cmdlet returns a standard **System.Diagnostics.EventLogEntry** object for each event.</span></span> <span data-ttu-id="1a20f-195">이 매개 변수가 없으면는 `Get-EventLog` 추가 **eventlogname** , **Source** 및 **InstanceId** 속성이 있는 확장 된 **PSObject** 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-195">Without this parameter, `Get-EventLog` returns an extended **PSObject** object with additional **EventLogName** , **Source** , and **InstanceId** properties.</span></span>

<span data-ttu-id="1a20f-196">이 매개 변수의 효과를 확인 하려면 이벤트를 cmdlet으로 파이프 하 `Get-Member` 고 결과의 **TypeName** 값을 검사 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-196">To see the effect of this parameter, pipe the events to the `Get-Member` cmdlet and examine the **TypeName** value in the result.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LogName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1a20f-197">-AsString</span><span class="sxs-lookup"><span data-stu-id="1a20f-197">-AsString</span></span>

<span data-ttu-id="1a20f-198">이 cmdlet은 개체가 아닌 문자열로 출력을 반환 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-198">Indicates that this cmdlet returns the output as strings, instead of objects.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: List
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1a20f-199">-이전</span><span class="sxs-lookup"><span data-stu-id="1a20f-199">-Before</span></span>

<span data-ttu-id="1a20f-200">지정 된 날짜 및 시간 이전에 발생 한 이벤트를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-200">Gets events that occurred before a specified date and time.</span></span> <span data-ttu-id="1a20f-201">매개 **변수** 날짜 및 시간이 출력에서 제외 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-201">The **Before** parameter date and time are excluded from the output.</span></span> <span data-ttu-id="1a20f-202">Cmdlet에서 반환 되는 값과 같은 **DateTime** 개체를 입력 합니다 `Get-Date` .</span><span class="sxs-lookup"><span data-stu-id="1a20f-202">Enter a **DateTime** object, such as the value returned by the `Get-Date` cmdlet.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: LogName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1a20f-203">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="1a20f-203">-ComputerName</span></span>

<span data-ttu-id="1a20f-204">이 매개 변수는 원격 컴퓨터의 NetBIOS 이름, IP (인터넷 프로토콜) 주소 또는 FQDN (정규화 된 도메인 이름)을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-204">This parameter specifies a remote computer's NetBIOS name, Internet Protocol (IP) address, or a fully qualified domain name (FQDN).</span></span>

<span data-ttu-id="1a20f-205">**ComputerName** 매개 변수가 지정 되지 않은 경우 `Get-EventLog` 기본값은 로컬 컴퓨터입니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-205">If the **ComputerName** parameter isn't specified, `Get-EventLog` defaults to the local computer.</span></span> <span data-ttu-id="1a20f-206">또한 매개 변수는 점 ()을 허용 `.` 하 여 로컬 컴퓨터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-206">The parameter also accepts a dot (`.`) to specify the local computer.</span></span>

<span data-ttu-id="1a20f-207">**ComputerName** 매개 변수는 Windows PowerShell 원격을 사용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-207">The **ComputerName** parameter doesn't rely on Windows PowerShell remoting.</span></span> <span data-ttu-id="1a20f-208">`Get-EventLog`컴퓨터에서 원격 명령을 실행 하도록 구성 되지 않은 경우에도 **ComputerName** 매개 변수와 함께를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-208">You can use `Get-EventLog` with the **ComputerName** parameter even if your computer is not configured to run remote commands.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Cn

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1a20f-209">-Entrytype 관련이</span><span class="sxs-lookup"><span data-stu-id="1a20f-209">-EntryType</span></span>

<span data-ttu-id="1a20f-210">이 cmdlet이 가져오는 이벤트의 항목 형식을 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-210">Specifies, as a string array, the entry type of the events that this cmdlet gets.</span></span>

<span data-ttu-id="1a20f-211">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-211">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="1a20f-212">오류</span><span class="sxs-lookup"><span data-stu-id="1a20f-212">Error</span></span>
- <span data-ttu-id="1a20f-213">정보</span><span class="sxs-lookup"><span data-stu-id="1a20f-213">Information</span></span>
- <span data-ttu-id="1a20f-214">FailureAudit</span><span class="sxs-lookup"><span data-stu-id="1a20f-214">FailureAudit</span></span>
- <span data-ttu-id="1a20f-215">SuccessAudit</span><span class="sxs-lookup"><span data-stu-id="1a20f-215">SuccessAudit</span></span>
- <span data-ttu-id="1a20f-216">경고</span><span class="sxs-lookup"><span data-stu-id="1a20f-216">Warning</span></span>

```yaml
Type: System.String[]
Parameter Sets: LogName
Aliases: ET
Accepted values: Error, Information, FailureAudit, SuccessAudit, Warning

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1a20f-217">-인덱스</span><span class="sxs-lookup"><span data-stu-id="1a20f-217">-Index</span></span>

<span data-ttu-id="1a20f-218">이벤트 로그에서 가져올 인덱스 값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-218">Specifies the index values to get from the event log.</span></span> <span data-ttu-id="1a20f-219">매개 변수는 쉼표로 구분 된 값 문자열을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-219">The parameter accepts a comma-separated string of values.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: LogName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1a20f-220">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="1a20f-220">-InstanceId</span></span>

<span data-ttu-id="1a20f-221">이벤트 로그에서 가져올 인스턴스 Id를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-221">Specifies the Instance IDs to get from the event log.</span></span> <span data-ttu-id="1a20f-222">매개 변수는 쉼표로 구분 된 값 문자열을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-222">The parameter accepts a comma-separated string of values.</span></span>

```yaml
Type: System.Int64[]
Parameter Sets: LogName
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1a20f-223">-목록</span><span class="sxs-lookup"><span data-stu-id="1a20f-223">-List</span></span>

<span data-ttu-id="1a20f-224">컴퓨터에 있는 이벤트 로그 목록을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-224">Displays the list of event logs on the computer.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: List
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1a20f-225">-LogName</span><span class="sxs-lookup"><span data-stu-id="1a20f-225">-LogName</span></span>

<span data-ttu-id="1a20f-226">하나의 이벤트 로그 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-226">Specifies the name of one event log.</span></span> <span data-ttu-id="1a20f-227">로그 이름을 찾으려면를 사용 `Get-EventLog -List` 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-227">To find the log names use `Get-EventLog -List`.</span></span> <span data-ttu-id="1a20f-228">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-228">Wildcard characters are permitted.</span></span> <span data-ttu-id="1a20f-229">이 매개 변수는 필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-229">This parameter is required.</span></span>

```yaml
Type: System.String
Parameter Sets: LogName
Aliases: LN

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="1a20f-230">-메시지</span><span class="sxs-lookup"><span data-stu-id="1a20f-230">-Message</span></span>

<span data-ttu-id="1a20f-231">이벤트 메시지의 문자열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-231">Specifies a string in the event message.</span></span> <span data-ttu-id="1a20f-232">이 매개 변수를 사용 하 여 특정 단어나 구가 포함 된 메시지를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-232">You can use this parameter to search for messages that contain certain words or phrases.</span></span> <span data-ttu-id="1a20f-233">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-233">Wildcards are permitted.</span></span>

```yaml
Type: System.String
Parameter Sets: LogName
Aliases: MSG

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="1a20f-234">-최신</span><span class="sxs-lookup"><span data-stu-id="1a20f-234">-Newest</span></span>

<span data-ttu-id="1a20f-235">최신 이벤트로 시작 하 고 지정 된 수의 이벤트를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-235">Begins with the newest events and gets the specified number of events.</span></span> <span data-ttu-id="1a20f-236">예를 들어 이벤트 수가 필요 `-Newest 100` 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-236">The number of events is required, for example `-Newest 100`.</span></span> <span data-ttu-id="1a20f-237">반환 되는 최대 이벤트 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-237">Specifies the maximum number of events that are returned.</span></span>

```yaml
Type: System.Int32
Parameter Sets: LogName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1a20f-238">-Source</span><span class="sxs-lookup"><span data-stu-id="1a20f-238">-Source</span></span>

<span data-ttu-id="1a20f-239">이 cmdlet이 가져오는 로그에 기록 된 원본 (문자열 배열)을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-239">Specifies, as a string array, sources that were written to the log that this cmdlet gets.</span></span> <span data-ttu-id="1a20f-240">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-240">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LogName
Aliases: ABO

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="1a20f-241">-UserName</span><span class="sxs-lookup"><span data-stu-id="1a20f-241">-UserName</span></span>

<span data-ttu-id="1a20f-242">이벤트와 연결 된 사용자 이름을 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-242">Specifies, as a string array, user names that are associated with events.</span></span> <span data-ttu-id="1a20f-243">이름 또는 이름 패턴 (예:, 또는)을 입력 `User01` `User*` `Domain01\User*` 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-243">Enter names or name patterns, such as `User01`, `User*`, or `Domain01\User*`.</span></span> <span data-ttu-id="1a20f-244">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-244">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LogName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="1a20f-245">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1a20f-245">CommonParameters</span></span>

<span data-ttu-id="1a20f-246">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1a20f-246">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1a20f-247">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1a20f-247">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1a20f-248">입력</span><span class="sxs-lookup"><span data-stu-id="1a20f-248">INPUTS</span></span>

### <span data-ttu-id="1a20f-249">없음</span><span class="sxs-lookup"><span data-stu-id="1a20f-249">None</span></span>

<span data-ttu-id="1a20f-250">입력을로 파이프 할 수 없습니다 `Get-EventLog` .</span><span class="sxs-lookup"><span data-stu-id="1a20f-250">You cannot pipe input to `Get-EventLog`.</span></span>

## <span data-ttu-id="1a20f-251">출력</span><span class="sxs-lookup"><span data-stu-id="1a20f-251">OUTPUTS</span></span>

### <span data-ttu-id="1a20f-252">EventLogEntry.</span><span class="sxs-lookup"><span data-stu-id="1a20f-252">System.Diagnostics.EventLogEntry.</span></span> <span data-ttu-id="1a20f-253">System.web. EventLog.</span><span class="sxs-lookup"><span data-stu-id="1a20f-253">System.Diagnostics.EventLog.</span></span> <span data-ttu-id="1a20f-254">System.String</span><span class="sxs-lookup"><span data-stu-id="1a20f-254">System.String</span></span>

<span data-ttu-id="1a20f-255">**LogName** 매개 변수가 지정 된 경우 출력은 **EventLogEntry** 개체의 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-255">If the **LogName** parameter is specified, the output is a collection of **System.Diagnostics.EventLogEntry** objects.</span></span>

<span data-ttu-id="1a20f-256">**List** 매개 변수만 지정 된 경우 출력은 **system.web** 개체의 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-256">If only the **List** parameter is specified, the output is a collection of **System.Diagnostics.EventLog** objects.</span></span>

<span data-ttu-id="1a20f-257">**List** 및 **asstring** 매개 변수를 모두 지정 하는 경우 출력은 **system.string** 개체의 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-257">If both the **List** and **AsString** parameters are specified, the output is a collection of **System.String** objects.</span></span>

## <span data-ttu-id="1a20f-258">참고</span><span class="sxs-lookup"><span data-stu-id="1a20f-258">NOTES</span></span>

<span data-ttu-id="1a20f-259">Cmdlet `Get-EventLog` 및는 `Get-WinEvent` Windows 사전 설치 환경 (Windows PE)에서 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1a20f-259">The cmdlets `Get-EventLog` and `Get-WinEvent` are not supported in the Windows Preinstallation Environment (Windows PE).</span></span>

## <span data-ttu-id="1a20f-260">관련 링크</span><span class="sxs-lookup"><span data-stu-id="1a20f-260">RELATED LINKS</span></span>

[<span data-ttu-id="1a20f-261">Clear-EventLog</span><span class="sxs-lookup"><span data-stu-id="1a20f-261">Clear-EventLog</span></span>](Clear-EventLog.md)

[<span data-ttu-id="1a20f-262">Get-WinEvent</span><span class="sxs-lookup"><span data-stu-id="1a20f-262">Get-WinEvent</span></span>](../Microsoft.PowerShell.Diagnostics/Get-WinEvent.md)

[<span data-ttu-id="1a20f-263">Group-Object</span><span class="sxs-lookup"><span data-stu-id="1a20f-263">Group-Object</span></span>](../Microsoft.PowerShell.Utility/Group-Object.md)

[<span data-ttu-id="1a20f-264">Limit-EventLog</span><span class="sxs-lookup"><span data-stu-id="1a20f-264">Limit-EventLog</span></span>](Limit-EventLog.md)

[<span data-ttu-id="1a20f-265">New-EventLog</span><span class="sxs-lookup"><span data-stu-id="1a20f-265">New-EventLog</span></span>](New-EventLog.md)

[<span data-ttu-id="1a20f-266">Remove-EventLog</span><span class="sxs-lookup"><span data-stu-id="1a20f-266">Remove-EventLog</span></span>](Remove-EventLog.md)

[<span data-ttu-id="1a20f-267">Select-Object</span><span class="sxs-lookup"><span data-stu-id="1a20f-267">Select-Object</span></span>](../Microsoft.PowerShell.Utility/Select-Object.md)

[<span data-ttu-id="1a20f-268">Show-EventLog</span><span class="sxs-lookup"><span data-stu-id="1a20f-268">Show-EventLog</span></span>](Show-EventLog.md)

[<span data-ttu-id="1a20f-269">Write-EventLog</span><span class="sxs-lookup"><span data-stu-id="1a20f-269">Write-EventLog</span></span>](Write-EventLog.md)
