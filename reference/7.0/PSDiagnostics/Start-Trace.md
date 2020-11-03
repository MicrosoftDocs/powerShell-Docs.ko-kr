---
external help file: PSDiagnostics-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/start-trace?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Trace
ms.openlocfilehash: 646d186b34e31aa2572aeefa12cc73d941076a13
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93210217"
---
# <span data-ttu-id="b616e-103">Start-Trace</span><span class="sxs-lookup"><span data-stu-id="b616e-103">Start-Trace</span></span>

## <span data-ttu-id="b616e-104">개요</span><span class="sxs-lookup"><span data-stu-id="b616e-104">SYNOPSIS</span></span>
<span data-ttu-id="b616e-105">이벤트 추적 로깅 세션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="b616e-105">Start an Event Trace logging session.</span></span>

## <span data-ttu-id="b616e-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b616e-106">SYNTAX</span></span>

```
Start-Trace [-SessionName] <String> [[-OutputFilePath] <String>] [[-ProviderFilePath] <String>]
 [-ETS] [-Format <String>] [-MinBuffers <Int32>] [-MaxBuffers <Int32>]
 [-BufferSizeInKB <Int32>] [-MaxLogFileSizeInMB <Int32>] [<CommonParameters>]
```

## <span data-ttu-id="b616e-107">설명</span><span class="sxs-lookup"><span data-stu-id="b616e-107">DESCRIPTION</span></span>
<span data-ttu-id="b616e-108">이 cmdlet은 Windows 이벤트 추적 로깅 세션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="b616e-108">This cmdlet starts a Windows Event Trace logging session.</span></span>

<span data-ttu-id="b616e-109">이 cmdlet은 다음 cmdlet에서 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b616e-109">This cmdlet is used by the following cmdlets:</span></span>

- `Enable-PSWSManCombinedTrace`
- `Enable-WSManTrace`

<span data-ttu-id="b616e-110">관리자 권한 PowerShell 세션에서이 cmdlet을 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b616e-110">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="b616e-111">예제</span><span class="sxs-lookup"><span data-stu-id="b616e-111">EXAMPLES</span></span>

### <span data-ttu-id="b616e-112">예제 1: WSMan 추적 로깅 세션 시작</span><span class="sxs-lookup"><span data-stu-id="b616e-112">Example 1: Start a WSMan Trace logging session</span></span>

```powershell
Start-Trace -SessionName 'wsmlog' -ETS -OutputFilePath "$env:windir\system32\wsmtraces.log" -Format 'bincirc' -MinBuffers 16 -MaxBuffers 256 -BufferSizeInKb 64 -MaxLogFileSizeInMB 256 -ProviderFilePath "$env:windir\system32\wsmtraceproviders.txt"
```

## <span data-ttu-id="b616e-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b616e-113">PARAMETERS</span></span>

### <span data-ttu-id="b616e-114">-BufferSizeInKB</span><span class="sxs-lookup"><span data-stu-id="b616e-114">-BufferSizeInKB</span></span>
<span data-ttu-id="b616e-115">이벤트 추적 세션 버퍼 크기 (kb)입니다.</span><span class="sxs-lookup"><span data-stu-id="b616e-115">Event Trace Session buffer size in kilobytes (KB).</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 0
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b616e-116">-%</span><span class="sxs-lookup"><span data-stu-id="b616e-116">-ETS</span></span>
<span data-ttu-id="b616e-117">이벤트 추적 세션 명령을 저장 하거나 예약 하지 않고 직접 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="b616e-117">Send commands to Event Trace Sessions directly without saving or scheduling.</span></span>

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

### <span data-ttu-id="b616e-118">-형식</span><span class="sxs-lookup"><span data-stu-id="b616e-118">-Format</span></span>
<span data-ttu-id="b616e-119">데이터 수집기에 대 한 로그 형식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b616e-119">Specifies the log format for the data collector.</span></span> <span data-ttu-id="b616e-120">SQL database 형식의 경우 명령줄에서 값을 사용 하 여 **Outputfilepath** 옵션을 사용 해야 합니다 `dsn!log` .</span><span class="sxs-lookup"><span data-stu-id="b616e-120">For SQL database format, you must use the **OutputFilePath** option in the command line with the `dsn!log` value.</span></span> <span data-ttu-id="b616e-121">기본값은 binary (bin)입니다.</span><span class="sxs-lookup"><span data-stu-id="b616e-121">The default is binary (bin).</span></span> <span data-ttu-id="b616e-122">가능한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b616e-122">The possible values are:</span></span>

- <span data-ttu-id="b616e-123">bin-이진</span><span class="sxs-lookup"><span data-stu-id="b616e-123">bin - binary</span></span>
- <span data-ttu-id="b616e-124">bincirc-순환 로깅을 사용 하는 이진 파일</span><span class="sxs-lookup"><span data-stu-id="b616e-124">bincirc - binary with circular logging</span></span>
- <span data-ttu-id="b616e-125">csv-쉼표로 구분 된 값</span><span class="sxs-lookup"><span data-stu-id="b616e-125">csv - Comma-separated values</span></span>
- <span data-ttu-id="b616e-126">tsv-탭으로 구분 된 값</span><span class="sxs-lookup"><span data-stu-id="b616e-126">tsv - Tab-separated values</span></span>
- <span data-ttu-id="b616e-127">sql-SQL 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="b616e-127">sql - SQL database</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:
Accepted values: bin, bincirc, csv, tsv, sql

Required: False
Position: Named
Default value: bin
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b616e-128">-MaxBuffers</span><span class="sxs-lookup"><span data-stu-id="b616e-128">-MaxBuffers</span></span>
<span data-ttu-id="b616e-129">이벤트 추적 세션 버퍼의 최대 수를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b616e-129">Sets the maximum number of Event Trace Session buffers.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 256
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b616e-130">-MaxLogFileSizeInMB</span><span class="sxs-lookup"><span data-stu-id="b616e-130">-MaxLogFileSizeInMB</span></span>
<span data-ttu-id="b616e-131">SQL 로그의 최대 로그 파일 크기 (MB) 또는 레코드 수를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b616e-131">Sets the maximum log file size in megabytes (MB) or number of records for SQL logs.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 0 (no limit)
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b616e-132">-MinBuffers</span><span class="sxs-lookup"><span data-stu-id="b616e-132">-MinBuffers</span></span>
<span data-ttu-id="b616e-133">이벤트 추적 세션 버퍼의 최소 수를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b616e-133">Sets the minimum number of Event Trace Session buffers.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 0
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b616e-134">-OutputFilePath</span><span class="sxs-lookup"><span data-stu-id="b616e-134">-OutputFilePath</span></span>
<span data-ttu-id="b616e-135">SQL 데이터베이스에 있는 출력 로그 파일의 경로 또는 DSN 및 로그 집합 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="b616e-135">Path of the output log file or the DSN and log set name in a SQL database.</span></span> <span data-ttu-id="b616e-136">기본 경로는 `$env:systemdrive\PerfLogs\Admin`입니다.</span><span class="sxs-lookup"><span data-stu-id="b616e-136">The default path is `$env:systemdrive\PerfLogs\Admin`.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: $env:systemdrive\PerfLogs\Admin
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b616e-137">-ProviderFilePath</span><span class="sxs-lookup"><span data-stu-id="b616e-137">-ProviderFilePath</span></span>
<span data-ttu-id="b616e-138">사용할 여러 이벤트 추적 공급자를 나열 하는 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="b616e-138">File listing multiple Event Trace providers to enable.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b616e-139">-세션 이름</span><span class="sxs-lookup"><span data-stu-id="b616e-139">-SessionName</span></span>
<span data-ttu-id="b616e-140">이벤트 추적 세션의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="b616e-140">The name of the Event Trace session.</span></span> <span data-ttu-id="b616e-141">추적 세션을 중지 하려면 세션 이름을 알아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b616e-141">To stop a trace session you must know the session name.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b616e-142">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b616e-142">CommonParameters</span></span>

<span data-ttu-id="b616e-143">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b616e-143">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b616e-144">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b616e-144">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b616e-145">입력</span><span class="sxs-lookup"><span data-stu-id="b616e-145">INPUTS</span></span>

### <span data-ttu-id="b616e-146">없음</span><span class="sxs-lookup"><span data-stu-id="b616e-146">None</span></span>

## <span data-ttu-id="b616e-147">출력</span><span class="sxs-lookup"><span data-stu-id="b616e-147">OUTPUTS</span></span>

### <span data-ttu-id="b616e-148">없음</span><span class="sxs-lookup"><span data-stu-id="b616e-148">None</span></span>

## <span data-ttu-id="b616e-149">참고</span><span class="sxs-lookup"><span data-stu-id="b616e-149">NOTES</span></span>

## <span data-ttu-id="b616e-150">관련 링크</span><span class="sxs-lookup"><span data-stu-id="b616e-150">RELATED LINKS</span></span>

[<span data-ttu-id="b616e-151">이벤트 추적</span><span class="sxs-lookup"><span data-stu-id="b616e-151">Event Tracing</span></span>](/windows/desktop/ETW/event-tracing-portal)

[<span data-ttu-id="b616e-152">Stop-Trace</span><span class="sxs-lookup"><span data-stu-id="b616e-152">Stop-Trace</span></span>](stop-trace.md)

[<span data-ttu-id="b616e-153">Disable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="b616e-153">Disable-PSWSManCombinedTrace</span></span>](Disable-PSWSManCombinedTrace.md)

[<span data-ttu-id="b616e-154">Disable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="b616e-154">Disable-WSManTrace</span></span>](Disable-WSManTrace.md)

[<span data-ttu-id="b616e-155">Enable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="b616e-155">Enable-PSWSManCombinedTrace</span></span>](Enable-PSWSManCombinedTrace.md)

[<span data-ttu-id="b616e-156">Enable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="b616e-156">Enable-WSManTrace</span></span>](Enable-WSManTrace.md)
