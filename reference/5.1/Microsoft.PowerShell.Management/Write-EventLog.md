---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/write-eventlog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-EventLog
ms.openlocfilehash: 051f02b00144805569d5130686a51a0f42b64b00
ms.sourcegitcommit: f5986121386c81acddcf324eb0526d7d092bcc8f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98584630"
---
# <span data-ttu-id="b97c8-103">Write-EventLog</span><span class="sxs-lookup"><span data-stu-id="b97c8-103">Write-EventLog</span></span>

## <span data-ttu-id="b97c8-104">개요</span><span class="sxs-lookup"><span data-stu-id="b97c8-104">SYNOPSIS</span></span>
<span data-ttu-id="b97c8-105">이벤트 로그에 이벤트를 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="b97c8-105">Writes an event to an event log.</span></span>

## <span data-ttu-id="b97c8-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b97c8-106">SYNTAX</span></span>

```
Write-EventLog [-LogName] <String> [-Source] <String> [[-EntryType] <EventLogEntryType>] [-Category <Int16>]
 [-EventId] <Int32> [-Message] <String> [-RawData <Byte[]>] [-ComputerName <String>] [<CommonParameters>]
```

## <span data-ttu-id="b97c8-107">설명</span><span class="sxs-lookup"><span data-stu-id="b97c8-107">DESCRIPTION</span></span>

<span data-ttu-id="b97c8-108">Cmdlet은 이벤트 `Write-EventLog` 로그에 이벤트를 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="b97c8-108">The `Write-EventLog` cmdlet writes an event to an event log.</span></span>

<span data-ttu-id="b97c8-109">이벤트 로그에 이벤트를 쓰려면 컴퓨터에 이벤트 로그가 있어야 하고 이벤트 로그의 원본이 등록되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b97c8-109">To write an event to an event log, the event log must exist on the computer and the source must be registered for the event log.</span></span>

<span data-ttu-id="b97c8-110">**Eventlog** 명사를 포함 하는 Cmdlet ( **eventlog** cmdlet)은 클래식 이벤트 로그 에서만 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="b97c8-110">The cmdlets that contain the **EventLog** noun (the **EventLog** cmdlets) work only on classic event logs.</span></span> <span data-ttu-id="b97c8-111">Windows Vista 이상 버전의 windows 운영 체제에서 Windows 이벤트 로그 기술을 사용 하는 로그에서 이벤트를 가져오려면 cmdlet을 사용 `Get-WinEvent` 합니다.</span><span class="sxs-lookup"><span data-stu-id="b97c8-111">To get events from logs that use the Windows Event Log technology in Windows Vista and later versions of the Windows operating system, use the `Get-WinEvent` cmdlet.</span></span>

## <span data-ttu-id="b97c8-112">예제</span><span class="sxs-lookup"><span data-stu-id="b97c8-112">EXAMPLES</span></span>

### <span data-ttu-id="b97c8-113">예제 1: 응용 프로그램 이벤트 로그에 이벤트 쓰기</span><span class="sxs-lookup"><span data-stu-id="b97c8-113">Example 1: Write an event to the Application event log</span></span>

```
PS C:\> Write-EventLog -LogName "Application" -Source "MyApp" -EventID 3001 -EntryType Information -Message "MyApp added a user-requested feature to the display." -Category 1 -RawData 10,20
```

<span data-ttu-id="b97c8-114">이 명령은 MyApp 원본의 이벤트를 애플리케이션 이벤트 로그에 씁니다.</span><span class="sxs-lookup"><span data-stu-id="b97c8-114">This command writes an event from the MyApp source to the Application event log.</span></span>

### <span data-ttu-id="b97c8-115">예제 2: 원격 컴퓨터의 응용 프로그램 이벤트 로그에 이벤트 쓰기</span><span class="sxs-lookup"><span data-stu-id="b97c8-115">Example 2: Write an event to the Application event log of a remote computer</span></span>

```
PS C:\> Write-EventLog -ComputerName "Server01" -LogName Application -Source "MyApp" -EventID 3001 -Message "MyApp added a user-requested feature to the display."
```

<span data-ttu-id="b97c8-116">이 명령은 MyApp 원본의 이벤트를 Server01 원격 컴퓨터의 애플리케이션 이벤트 로그에 씁니다.</span><span class="sxs-lookup"><span data-stu-id="b97c8-116">This command writes an event from the MyApp source to the Application event log on the Server01 remote computer.</span></span>

## <span data-ttu-id="b97c8-117">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b97c8-117">PARAMETERS</span></span>

### <span data-ttu-id="b97c8-118">-범주</span><span class="sxs-lookup"><span data-stu-id="b97c8-118">-Category</span></span>

<span data-ttu-id="b97c8-119">이벤트의 작업 범주를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b97c8-119">Specifies a task category for the event.</span></span> <span data-ttu-id="b97c8-120">이벤트 로그에 대한 범주 메시지 파일의 문자열과 연결된 정수를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b97c8-120">Enter an integer that is associated with the strings in the category message file for the event log.</span></span>

```yaml
Type: System.Int16
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b97c8-121">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="b97c8-121">-ComputerName</span></span>

<span data-ttu-id="b97c8-122">원격 컴퓨터를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b97c8-122">Specifies a remote computer.</span></span> <span data-ttu-id="b97c8-123">기본값은 로컬 컴퓨터입니다.</span><span class="sxs-lookup"><span data-stu-id="b97c8-123">The default is the local computer.</span></span>

<span data-ttu-id="b97c8-124">원격 컴퓨터의 NetBIOS 이름, IP 주소 또는 정규화된 도메인 이름을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="b97c8-124">Type the NetBIOS name, an IP address, or a fully qualified domain name of a remote computer.</span></span>

<span data-ttu-id="b97c8-125">이 매개 변수는 Windows PowerShell 원격 기능을 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b97c8-125">This parameter does not rely on Windows PowerShell remoting.</span></span> <span data-ttu-id="b97c8-126"> `Get-EventLog` 컴퓨터에서 원격 명령을 실행 하도록 구성 되지 않은 경우에도 cmdlet의 ComputerName 매개 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b97c8-126">You can use the **ComputerName** parameter of the `Get-EventLog` cmdlet even if your computer is not configured to run remote commands.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: CN

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b97c8-127">-Entrytype 관련이</span><span class="sxs-lookup"><span data-stu-id="b97c8-127">-EntryType</span></span>

<span data-ttu-id="b97c8-128">이벤트의 항목 유형을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b97c8-128">Specifies the entry type of the event.</span></span> <span data-ttu-id="b97c8-129">이 매개 변수에 허용 되는 값은 Error, Warning, Information, SuccessAudit 및 FailureAudit입니다.</span><span class="sxs-lookup"><span data-stu-id="b97c8-129">The acceptable values for this parameter are: Error, Warning, Information, SuccessAudit, and FailureAudit.</span></span> <span data-ttu-id="b97c8-130">기본값은 Information입니다.</span><span class="sxs-lookup"><span data-stu-id="b97c8-130">The default value is Information.</span></span>

<span data-ttu-id="b97c8-131">값에 대 한 설명은 [EventLogEntryType 열거](/dotnet/api/system.diagnostics.eventlogentrytype)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b97c8-131">For a description of the values, see [EventLogEntryType Enumeration](/dotnet/api/system.diagnostics.eventlogentrytype).</span></span>

```yaml
Type: System.Diagnostics.EventLogEntryType
Parameter Sets: (All)
Aliases: ET
Accepted values: Error, Information, FailureAudit, SuccessAudit, Warning

Required: False
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b97c8-132">-EventId</span><span class="sxs-lookup"><span data-stu-id="b97c8-132">-EventId</span></span>

<span data-ttu-id="b97c8-133">이벤트 식별자를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b97c8-133">Specifies the event identifier.</span></span> <span data-ttu-id="b97c8-134">이 매개 변수는 필수입니다.</span><span class="sxs-lookup"><span data-stu-id="b97c8-134">This parameter is required.</span></span> <span data-ttu-id="b97c8-135">**EventId** 매개 변수의 최대값은 65535입니다.</span><span class="sxs-lookup"><span data-stu-id="b97c8-135">The maximum value for the **EventId** parameter is 65535.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: ID, EID

Required: True
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b97c8-136">-LogName</span><span class="sxs-lookup"><span data-stu-id="b97c8-136">-LogName</span></span>

<span data-ttu-id="b97c8-137">이벤트가 기록되는 로그의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b97c8-137">Specifies the name of the log to which the event is written.</span></span> <span data-ttu-id="b97c8-138">로그 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="b97c8-138">Enter the log name.</span></span> <span data-ttu-id="b97c8-139">로그 이름은 **Logdisplayname** 이 아닌 **log** 속성의 값입니다.</span><span class="sxs-lookup"><span data-stu-id="b97c8-139">The log name is the value of the **Log** property, not the **LogDisplayName**.</span></span> <span data-ttu-id="b97c8-140">와일드카드 문자는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b97c8-140">Wildcard characters are not permitted.</span></span>
<span data-ttu-id="b97c8-141">이 매개 변수는 필수입니다.</span><span class="sxs-lookup"><span data-stu-id="b97c8-141">This parameter is required.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: LN

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b97c8-142">-메시지</span><span class="sxs-lookup"><span data-stu-id="b97c8-142">-Message</span></span>

<span data-ttu-id="b97c8-143">이벤트 메시지를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b97c8-143">Specifies the event message.</span></span> <span data-ttu-id="b97c8-144">이 매개 변수는 필수입니다.</span><span class="sxs-lookup"><span data-stu-id="b97c8-144">This parameter is required.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: MSG

Required: True
Position: 4
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b97c8-145">-RawData</span><span class="sxs-lookup"><span data-stu-id="b97c8-145">-RawData</span></span>

<span data-ttu-id="b97c8-146">이벤트와 연결된 이진 데이터를 바이트 단위로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b97c8-146">Specifies the binary data that is associated with the event, in bytes.</span></span>

```yaml
Type: System.Byte[]
Parameter Sets: (All)
Aliases: RD

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b97c8-147">-Source</span><span class="sxs-lookup"><span data-stu-id="b97c8-147">-Source</span></span>

<span data-ttu-id="b97c8-148">이벤트 원본을 지정합니다. 일반적으로 로그에 이벤트를 쓰는 애플리케이션의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="b97c8-148">Specifies the event source, which is typically the name of the application that is writing the event to the log.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: SRC

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b97c8-149">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b97c8-149">CommonParameters</span></span>

<span data-ttu-id="b97c8-150">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b97c8-150">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b97c8-151">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b97c8-151">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b97c8-152">입력</span><span class="sxs-lookup"><span data-stu-id="b97c8-152">INPUTS</span></span>

### <span data-ttu-id="b97c8-153">None</span><span class="sxs-lookup"><span data-stu-id="b97c8-153">None</span></span>

<span data-ttu-id="b97c8-154">이 cmdlet에 입력을 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b97c8-154">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="b97c8-155">출력</span><span class="sxs-lookup"><span data-stu-id="b97c8-155">OUTPUTS</span></span>

### <span data-ttu-id="b97c8-156">EventLogEntry</span><span class="sxs-lookup"><span data-stu-id="b97c8-156">System.Diagnostics.EventLogEntry</span></span>

<span data-ttu-id="b97c8-157">이 cmdlet은 로그의 이벤트를 나타내는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="b97c8-157">This cmdlet returns objects that represents the events in the logs.</span></span>

## <span data-ttu-id="b97c8-158">참고</span><span class="sxs-lookup"><span data-stu-id="b97c8-158">NOTES</span></span>

<span data-ttu-id="b97c8-159">일부 Windows 이벤트 로그의 경우 이벤트를 기록 하려면 관리자 권한이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="b97c8-159">For some Windows event logs, writing events requires administrator rights.</span></span> <span data-ttu-id="b97c8-160">**관리자 권한으로 실행** 옵션을 사용 하 여 PowerShell을 시작 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b97c8-160">You must start PowerShell using the **Run as Administrator** option.</span></span>

## <span data-ttu-id="b97c8-161">관련 링크</span><span class="sxs-lookup"><span data-stu-id="b97c8-161">RELATED LINKS</span></span>

[<span data-ttu-id="b97c8-162">Clear-EventLog</span><span class="sxs-lookup"><span data-stu-id="b97c8-162">Clear-EventLog</span></span>](Clear-EventLog.md)

[<span data-ttu-id="b97c8-163">Get-EventLog</span><span class="sxs-lookup"><span data-stu-id="b97c8-163">Get-EventLog</span></span>](Get-EventLog.md)

[<span data-ttu-id="b97c8-164">Limit-EventLog</span><span class="sxs-lookup"><span data-stu-id="b97c8-164">Limit-EventLog</span></span>](Limit-EventLog.md)

[<span data-ttu-id="b97c8-165">New-EventLog</span><span class="sxs-lookup"><span data-stu-id="b97c8-165">New-EventLog</span></span>](New-EventLog.md)

[<span data-ttu-id="b97c8-166">Remove-EventLog</span><span class="sxs-lookup"><span data-stu-id="b97c8-166">Remove-EventLog</span></span>](Remove-EventLog.md)

[<span data-ttu-id="b97c8-167">Show-EventLog</span><span class="sxs-lookup"><span data-stu-id="b97c8-167">Show-EventLog</span></span>](Show-EventLog.md)

[<span data-ttu-id="b97c8-168">Write-EventLog</span><span class="sxs-lookup"><span data-stu-id="b97c8-168">Write-EventLog</span></span>](Write-EventLog.md)
