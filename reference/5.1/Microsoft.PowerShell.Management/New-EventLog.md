---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 01/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-eventlog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-EventLog
ms.openlocfilehash: 61fafc0670a24fd6ca057e4cf0c7179d90446b07
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93214618"
---
# <span data-ttu-id="d0d2b-103">New-EventLog</span><span class="sxs-lookup"><span data-stu-id="d0d2b-103">New-EventLog</span></span>

## <span data-ttu-id="d0d2b-104">개요</span><span class="sxs-lookup"><span data-stu-id="d0d2b-104">SYNOPSIS</span></span>
<span data-ttu-id="d0d2b-105">로컬 또는 원격 컴퓨터에 새 이벤트 로그 및 새 이벤트 원본을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d0d2b-105">Creates a new event log and a new event source on a local or remote computer.</span></span>

## <span data-ttu-id="d0d2b-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d0d2b-106">SYNTAX</span></span>

```
New-EventLog [-LogName] <string> [-Source] <string[]> [[-ComputerName] <string[]>]
  [-CategoryResourceFile <string>] [-MessageResourceFile <string>] [-ParameterResourceFile <string>]
  [<CommonParameters>]
```

## <span data-ttu-id="d0d2b-107">설명</span><span class="sxs-lookup"><span data-stu-id="d0d2b-107">DESCRIPTION</span></span>

<span data-ttu-id="d0d2b-108">이 cmdlet은 로컬 또는 원격 컴퓨터에 새 기본 이벤트 로그를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d0d2b-108">This cmdlet creates a new classic event log on a local or remote computer.</span></span> <span data-ttu-id="d0d2b-109">새 로그나 기존 로그에 항목을 기록하는 이벤트 원본을 등록할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0d2b-109">It can also register an event source that writes to the new log or to an existing log.</span></span>

<span data-ttu-id="d0d2b-110">EventLog 명사(이벤트 로그 cmdlet)를 포함하는 cmdlet은 기본 이벤트 로그에서만 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="d0d2b-110">The cmdlets that contain the EventLog noun (the Event log cmdlets) work only on classic event logs.</span></span>
<span data-ttu-id="d0d2b-111">Windows Vista 이상 버전의 windows 이벤트 로그 기술을 사용 하는 로그에서 이벤트를 가져오려면를 사용 `Get-WinEvent` 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0d2b-111">To get events from logs that use the Windows Event Log technology in Windows Vista and later versions of Windows, use `Get-WinEvent`.</span></span>

## <span data-ttu-id="d0d2b-112">예제</span><span class="sxs-lookup"><span data-stu-id="d0d2b-112">EXAMPLES</span></span>

### <span data-ttu-id="d0d2b-113">예 1-새 이벤트 로그 만들기</span><span class="sxs-lookup"><span data-stu-id="d0d2b-113">Example 1 - create a new event log</span></span>

<span data-ttu-id="d0d2b-114">이 명령은 로컬 컴퓨터에 TestLog 이벤트 로그를 만들고 이 이벤트 로그에 대한 새 원본을 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="d0d2b-114">This command creates the TestLog event log on the local computer and registers a new source for it.</span></span>

```powershell
New-EventLog -source TestApp -LogName TestLog -MessageResourceFile C:\Test\TestApp.dll
```

### <span data-ttu-id="d0d2b-115">예 2-기존 로그에 새 이벤트 원본 추가</span><span class="sxs-lookup"><span data-stu-id="d0d2b-115">Example 2 - add a new event source to an existing log</span></span>

<span data-ttu-id="d0d2b-116">이 명령은 NewTestApp라는 새 이벤트 원본을 Server01 원격 컴퓨터의 Application 로그에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="d0d2b-116">This command adds a new event source, NewTestApp, to the Application log on the Server01 remote computer.</span></span>

```powershell
$file = "C:\Program Files\TestApps\NewTestApp.dll"
New-EventLog -ComputerName Server01 -Source NewTestApp -LogName Application -MessageResourceFile $file -CategoryResourceFile $file
```

<span data-ttu-id="d0d2b-117">이 명령을 실행하려면 Server01 컴퓨터에 NewTestApp.dll 파일이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0d2b-117">The command requires that the NewTestApp.dll file is located on the Server01 computer.</span></span>

## <span data-ttu-id="d0d2b-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d0d2b-118">PARAMETERS</span></span>

### <span data-ttu-id="d0d2b-119">-CategoryResourceFile</span><span class="sxs-lookup"><span data-stu-id="d0d2b-119">-CategoryResourceFile</span></span>

<span data-ttu-id="d0d2b-120">원본 이벤트에 대한 범주 문자열이 포함된 파일의 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d0d2b-120">Specifies the path to the file that contains category strings for the source events.</span></span> <span data-ttu-id="d0d2b-121">이 파일을 범주 메시지 파일이라고도 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0d2b-121">This file is also known as the Category Message File.</span></span>

<span data-ttu-id="d0d2b-122">이 파일은 이벤트 로그가 작성되는 컴퓨터에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0d2b-122">The file must be present on the computer on which the event log is being created.</span></span> <span data-ttu-id="d0d2b-123">이 매개 변수는 파일을 만들거나 이동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d0d2b-123">This parameter does not create or move files.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: CRF

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d0d2b-124">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="d0d2b-124">-ComputerName</span></span>

<span data-ttu-id="d0d2b-125">지정된 컴퓨터에 새 이벤트 로그를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d0d2b-125">Creates the new event logs on the specified computers.</span></span> <span data-ttu-id="d0d2b-126">기본값은 로컬 컴퓨터입니다.</span><span class="sxs-lookup"><span data-stu-id="d0d2b-126">The default is the local computer.</span></span>

<span data-ttu-id="d0d2b-127">원격 컴퓨터의 NetBIOS 이름, IP 주소 또는 정규화 된 도메인 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="d0d2b-127">The NetBIOS name, IP address, or fully qualified domain name of a remote computer.</span></span>
<span data-ttu-id="d0d2b-128">로컬 컴퓨터를 지정하려면 컴퓨터 이름, 점(.) 또는 "localhost"를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="d0d2b-128">To specify the local computer, type the computer name, a dot (.), or "localhost".</span></span>

<span data-ttu-id="d0d2b-129">이 매개 변수는 PowerShell 원격을 사용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d0d2b-129">This parameter does not rely on PowerShell remoting.</span></span> <span data-ttu-id="d0d2b-130">**ComputerName** `Get-EventLog` 컴퓨터가 원격 명령을 실행 하도록 구성 되지 않은 경우에도의 ComputerName 매개 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0d2b-130">You can use the **ComputerName** parameter of `Get-EventLog` even if your computer is not configured to run remote commands.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN

Required: False
Position: 3
Default value: Local computer
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d0d2b-131">-LogName</span><span class="sxs-lookup"><span data-stu-id="d0d2b-131">-LogName</span></span>

<span data-ttu-id="d0d2b-132">이벤트 로그의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d0d2b-132">Specifies the name of the event log.</span></span>

<span data-ttu-id="d0d2b-133">로그가 없으면에서 `New-EventLog` 로그를 만들고 새 이벤트 로그의 **Log** 및 **logdisplayname** 속성에이 값을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0d2b-133">If the log does not exist, `New-EventLog` creates the log and uses this value for the **Log** and **LogDisplayName** properties of the new event log.</span></span> <span data-ttu-id="d0d2b-134">로그가 있으면에서 `New-EventLog` 이벤트 로그에 대 한 새 원본을 등록 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0d2b-134">If the log exists, `New-EventLog` registers a new source for the event log.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: LN

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d0d2b-135">-MessageResourceFile</span><span class="sxs-lookup"><span data-stu-id="d0d2b-135">-MessageResourceFile</span></span>

<span data-ttu-id="d0d2b-136">원본 이벤트에 대한 메시지 형식 지정 문자열이 포함된 파일의 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d0d2b-136">Specifies the path to the file that contains message formatting strings for the source events.</span></span>
<span data-ttu-id="d0d2b-137">이 파일을 이벤트 메시지 파일이라고도 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0d2b-137">This file is also known as the Event Message File.</span></span>

<span data-ttu-id="d0d2b-138">이 파일은 이벤트 로그가 작성되는 컴퓨터에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0d2b-138">The file must be present on the computer on which the event log is being created.</span></span>
<span data-ttu-id="d0d2b-139">이 매개 변수는 파일을 만들거나 이동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d0d2b-139">This parameter does not create or move files.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: MRF

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d0d2b-140">-ParameterResourceFile</span><span class="sxs-lookup"><span data-stu-id="d0d2b-140">-ParameterResourceFile</span></span>

<span data-ttu-id="d0d2b-141">이벤트 설명에서 매개 변수 대체에 사용되는 문자열이 포함된 파일의 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d0d2b-141">Specifies the path to the file that contains strings used for parameter substitutions in event descriptions.</span></span> <span data-ttu-id="d0d2b-142">이 파일을 매개 변수 메시지 파일이라고도 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0d2b-142">This file is also known as the Parameter Message File.</span></span>

<span data-ttu-id="d0d2b-143">이 파일은 이벤트 로그가 작성되는 컴퓨터에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0d2b-143">The file must be present on the computer on which the event log is being created.</span></span>
<span data-ttu-id="d0d2b-144">이 매개 변수는 파일을 만들거나 이동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d0d2b-144">This parameter does not create or move files.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PRF

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d0d2b-145">-Source</span><span class="sxs-lookup"><span data-stu-id="d0d2b-145">-Source</span></span>

<span data-ttu-id="d0d2b-146">이벤트 로그에 기록하는 애플리케이션과 같은 이벤트 로그 원본의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d0d2b-146">Specifies the names of the event log sources, such as application programs that write to the event log.</span></span> <span data-ttu-id="d0d2b-147">이 매개 변수는 필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="d0d2b-147">This parameter is required.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: SRC

Required: True
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d0d2b-148">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d0d2b-148">CommonParameters</span></span>

<span data-ttu-id="d0d2b-149">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d0d2b-149">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d0d2b-150">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d0d2b-150">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d0d2b-151">입력</span><span class="sxs-lookup"><span data-stu-id="d0d2b-151">INPUTS</span></span>

### <span data-ttu-id="d0d2b-152">없음</span><span class="sxs-lookup"><span data-stu-id="d0d2b-152">None</span></span>

<span data-ttu-id="d0d2b-153">이 cmdlet에 입력을 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d0d2b-153">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="d0d2b-154">출력</span><span class="sxs-lookup"><span data-stu-id="d0d2b-154">OUTPUTS</span></span>

### <span data-ttu-id="d0d2b-155">EventLogEntry</span><span class="sxs-lookup"><span data-stu-id="d0d2b-155">System.Diagnostics.EventLogEntry</span></span>

## <span data-ttu-id="d0d2b-156">참고</span><span class="sxs-lookup"><span data-stu-id="d0d2b-156">NOTES</span></span>

<span data-ttu-id="d0d2b-157">`New-EventLog`Windows Vista 이상 버전에서을 사용 하려면 "관리자 권한으로 실행" 옵션을 사용 하 여 PowerShell을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="d0d2b-157">To use `New-EventLog` on Windows Vista and later versions of Windows, open PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="d0d2b-158">Windows Vista, Windows XP Professional 또는 Windows Server 2003에서 이벤트 원본을 만들려면 해당 컴퓨터의 관리자 그룹 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0d2b-158">To create an event source in Windows Vista, Windows XP Professional, or Windows Server 2003, you must be a member of the Administrators group on the computer.</span></span>

<span data-ttu-id="d0d2b-159">새 이벤트 로그 및 새 이벤트 원본을 만들면 새 로그에 대한 새 원본이 시스템에 등록되지만 로그에 첫 번째 항목이 기록되기 전까지는 로그가 만들어지지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d0d2b-159">When you create a new event log and a new event source, the system registers the new source for the new log, but the log is not created until the first entry is written to it.</span></span>

<span data-ttu-id="d0d2b-160">이벤트 로그는 운영 체제에 파일로 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="d0d2b-160">The operating system stores event logs as files.</span></span>

<span data-ttu-id="d0d2b-161">새 이벤트 로그를 만들 때 연결 된 파일은 `$env:SystemRoot\System32\Config` 지정 된 컴퓨터의 디렉터리에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d0d2b-161">When you create a new event log, the associated file is stored in the `$env:SystemRoot\System32\Config` directory on the specified computer.</span></span>

<span data-ttu-id="d0d2b-162">파일 이름은 **Log** 속성의 처음 8 자와 .evt 파일 이름 확장명을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0d2b-162">The file name is the first eight characters of the **Log** property with an .evt file name extension.</span></span>

## <span data-ttu-id="d0d2b-163">관련 링크</span><span class="sxs-lookup"><span data-stu-id="d0d2b-163">RELATED LINKS</span></span>

[<span data-ttu-id="d0d2b-164">Clear-EventLog</span><span class="sxs-lookup"><span data-stu-id="d0d2b-164">Clear-EventLog</span></span>](Clear-EventLog.md)

[<span data-ttu-id="d0d2b-165">Get-EventLog</span><span class="sxs-lookup"><span data-stu-id="d0d2b-165">Get-EventLog</span></span>](Get-EventLog.md)

[<span data-ttu-id="d0d2b-166">Get-WinEvent</span><span class="sxs-lookup"><span data-stu-id="d0d2b-166">Get-WinEvent</span></span>](../Microsoft.PowerShell.Diagnostics/Get-WinEvent.md)

[<span data-ttu-id="d0d2b-167">Limit-EventLog</span><span class="sxs-lookup"><span data-stu-id="d0d2b-167">Limit-EventLog</span></span>](Limit-EventLog.md)

[<span data-ttu-id="d0d2b-168">New-EventLog</span><span class="sxs-lookup"><span data-stu-id="d0d2b-168">New-EventLog</span></span>](New-EventLog.md)

[<span data-ttu-id="d0d2b-169">Remove-EventLog</span><span class="sxs-lookup"><span data-stu-id="d0d2b-169">Remove-EventLog</span></span>](Remove-EventLog.md)

[<span data-ttu-id="d0d2b-170">Show-EventLog</span><span class="sxs-lookup"><span data-stu-id="d0d2b-170">Show-EventLog</span></span>](Show-EventLog.md)

[<span data-ttu-id="d0d2b-171">Write-EventLog</span><span class="sxs-lookup"><span data-stu-id="d0d2b-171">Write-EventLog</span></span>](Write-EventLog.md)
