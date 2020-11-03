---
description: PowerShell은 엔진, 공급자 및 cmdlet에서 내부 작업을 기록 합니다.
keywords: PowerShell
Locale: en-US
ms.date: 03/30/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_logging_non-windows?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Logging_Non-Windows
ms.openlocfilehash: 5face386a479a0264f5ff2ba3f6665cb1e218a4a
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93220458"
---
# <a name="about-logging-non-windows"></a><span data-ttu-id="5b644-104">비 Windows 로깅 정보</span><span class="sxs-lookup"><span data-stu-id="5b644-104">About Logging Non-Windows</span></span>

## <a name="short-description"></a><span data-ttu-id="5b644-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="5b644-105">Short description</span></span>

<span data-ttu-id="5b644-106">PowerShell은 엔진, 공급자 및 cmdlet에서 내부 작업을 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b644-106">PowerShell logs internal operations from the engine, providers, and cmdlets.</span></span>

## <a name="long-description"></a><span data-ttu-id="5b644-107">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="5b644-107">Long description</span></span>

<span data-ttu-id="5b644-108">Powershell 작업에 대 한 세부 정보를 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b644-108">PowerShell logs details of PowerShell operations.</span></span> <span data-ttu-id="5b644-109">예를 들어 PowerShell은 엔진을 시작 및 중지 하 고 공급자를 시작 및 중지 하는 등의 작업을 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b644-109">For example, PowerShell will log operations such as starting and stopping the engine and starting and stopping providers.</span></span> <span data-ttu-id="5b644-110">PowerShell 명령에 대 한 세부 정보도 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b644-110">It will also log details about PowerShell commands.</span></span>

<span data-ttu-id="5b644-111">PowerShell 로그의 위치는 대상 플랫폼에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="5b644-111">The location of PowerShell logs is dependent on the target platform.</span></span> <span data-ttu-id="5b644-112">**Linux** 에서는 **syslog** 및 **rsyslog** 에 PowerShell 로그를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b644-112">On **Linux** , PowerShell logs to **syslog** and **rsyslog.conf** can be used.</span></span> <span data-ttu-id="5b644-113">자세한 내용은 Linux 컴퓨터의 로컬 페이지를 참조 `man` 하세요.</span><span class="sxs-lookup"><span data-stu-id="5b644-113">For more information, refer to the Linux computer's local `man` pages.</span></span> <span data-ttu-id="5b644-114">**Macos** 에서 **os_log** 로깅 시스템이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b644-114">On **macOS** , the **os_log** logging system is used.</span></span> <span data-ttu-id="5b644-115">자세한 내용은 [os_log 개발자 설명서](https://developer.apple.com/documentation/os/os_log)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5b644-115">For more information, see [os_log developer documentation](https://developer.apple.com/documentation/os/os_log).</span></span>

## <a name="viewing-powershell-log-output-on-linux"></a><span data-ttu-id="5b644-116">Linux에서 PowerShell 로그 출력 보기</span><span class="sxs-lookup"><span data-stu-id="5b644-116">Viewing PowerShell log output on Linux</span></span>

<span data-ttu-id="5b644-117">Linux의 **syslog** 에 대 한 PowerShell 로그 및 **syslog** 콘텐츠를 보는 데 일반적으로 사용 되는 모든 도구를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b644-117">PowerShell logs to **syslog** on Linux and any of the tools commonly used to view **syslog** contents may be used.</span></span>

<span data-ttu-id="5b644-118">로그 항목의 형식은 다음 템플릿을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b644-118">The format of the log entries uses the following template:</span></span>

```
TIMESTAMP MACHINENAME powershell[PID]: (COMMITID:TID:CID)
  [EVENTID:TASK.OPCODE.LEVEL] MESSAGE
```

|<span data-ttu-id="5b644-119">필드</span><span class="sxs-lookup"><span data-stu-id="5b644-119">Field</span></span>        |<span data-ttu-id="5b644-120">Description</span><span class="sxs-lookup"><span data-stu-id="5b644-120">Description</span></span>                                             |
|-------------|--------------------------------------------------------|
|`TIMESTAMP`  |<span data-ttu-id="5b644-121">로그 항목이 생성 된 날짜/시간입니다.</span><span class="sxs-lookup"><span data-stu-id="5b644-121">A date/time when the log entry was produced.</span></span>            |
|`MACHINENAME`|<span data-ttu-id="5b644-122">로그가 생성 된 시스템의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="5b644-122">The name of the system where the log was produced.</span></span>      |
|`PID`        |<span data-ttu-id="5b644-123">로그 항목을 작성 한 프로세스의 프로세스 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="5b644-123">The process ID of the process that wrote the log entry.</span></span> |
|`COMMITID`   |<span data-ttu-id="5b644-124">`git commit`빌드를 생성 하는 데 사용 되는 ID 또는 태그입니다.</span><span class="sxs-lookup"><span data-stu-id="5b644-124">The `git commit` ID or tag used to produce the build.</span></span>   |
|`TID`        |<span data-ttu-id="5b644-125">로그 항목을 쓴 스레드의 스레드 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="5b644-125">The thread ID of the thread that wrote the log entry.</span></span>   |
|`CID`        |<span data-ttu-id="5b644-126">로그 항목의 16 진수 채널 식별자입니다.</span><span class="sxs-lookup"><span data-stu-id="5b644-126">The hex channel identifier of the log entry.</span></span>            |
|             |<span data-ttu-id="5b644-127">10 = 작동, 11 = 분석</span><span class="sxs-lookup"><span data-stu-id="5b644-127">10 = Operational, 11 = Analytic</span></span>                         |
|`EVENTID`    |<span data-ttu-id="5b644-128">로그 항목의 이벤트 식별자입니다.</span><span class="sxs-lookup"><span data-stu-id="5b644-128">The event identifier of the log entry.</span></span>                  |
|`TASK`       |<span data-ttu-id="5b644-129">이벤트 항목에 대 한 작업 식별자입니다.</span><span class="sxs-lookup"><span data-stu-id="5b644-129">The task identifier for the event entry</span></span>                 |
|`OPCODE`     |<span data-ttu-id="5b644-130">이벤트 엔트리의 opcode입니다.</span><span class="sxs-lookup"><span data-stu-id="5b644-130">The opcode for the event entry</span></span>                          |
|`LEVEL`      |<span data-ttu-id="5b644-131">이벤트 항목의 로그 수준입니다.</span><span class="sxs-lookup"><span data-stu-id="5b644-131">The log level for the event entry</span></span>                       |
|`MESSAGE`    |<span data-ttu-id="5b644-132">이벤트 항목과 연결 된 메시지입니다.</span><span class="sxs-lookup"><span data-stu-id="5b644-132">The message associated with the event entry</span></span>             |

> [!NOTE]
> <span data-ttu-id="5b644-133">`EVENTID`, `TASK` , `OPCODE` 및는 `LEVEL` Windows 이벤트 로그에 로깅할 때 사용 되는 것과 동일한 값입니다.</span><span class="sxs-lookup"><span data-stu-id="5b644-133">`EVENTID`, `TASK`, `OPCODE`, and `LEVEL` are the same values as used when logging to the Windows event log.</span></span>

### <a name="filtering-powershell-log-entries-using-rsyslog"></a><span data-ttu-id="5b644-134">Rsyslog를 사용 하 여 PowerShell 로그 항목 필터링</span><span class="sxs-lookup"><span data-stu-id="5b644-134">Filtering PowerShell log entries using rsyslog</span></span>

<span data-ttu-id="5b644-135">일반적으로 PowerShell 로그 항목은 syslog의 기본값에 기록 됩니다 `location/file` . **syslog**</span><span class="sxs-lookup"><span data-stu-id="5b644-135">Normally, PowerShell log entries are written to the default `location/file` for **syslog**.</span></span> <span data-ttu-id="5b644-136">그러나 항목을 사용자 지정 파일로 리디렉션할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b644-136">However, it's possible to redirect the entries to a custom file.</span></span>

1. <span data-ttu-id="5b644-137">PowerShell 로그 구성에 대 한 회의를 만들고와 같이 50 보다 작은 숫자를 제공 `50-default.conf` `40-powershell.conf` 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b644-137">Create a conf for PowerShell log configuration and provide a number that's less than 50 (for `50-default.conf`), such as `40-powershell.conf`.</span></span> <span data-ttu-id="5b644-138">파일은 아래에 배치 해야 합니다 `/etc/rsyslog.d` .</span><span class="sxs-lookup"><span data-stu-id="5b644-138">The file should be placed under `/etc/rsyslog.d`.</span></span>

1. <span data-ttu-id="5b644-139">파일에 다음 항목을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b644-139">Add the following entry to the file:</span></span>

   ```
   :syslogtag, contains, "powershell[" /var/log/powershell.log
   & stop
   ```

1. <span data-ttu-id="5b644-140">`/etc/rsyslog.conf`새 파일이 포함 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b644-140">Make sure `/etc/rsyslog.conf` includes the new file.</span></span> <span data-ttu-id="5b644-141">종종 다음과 같은 구성 처럼 일반 include 문을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b644-141">Often, it will have a generic include statement that looks like following configuration:</span></span>

   `$IncludeConfig /etc/rsyslog.d/*.conf`

   <span data-ttu-id="5b644-142">그렇지 않은 경우 include 문을 수동으로 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b644-142">If it doesn't, you'll need to add an include statement manually.</span></span>

1. <span data-ttu-id="5b644-143">특성 및 사용 권한이 적절 하 게 설정 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b644-143">Make sure attributes and permissions are set appropriately.</span></span>

   ```
   -rw-r--r-- 1 root root   67 Nov 28 12:51 40-powershell.conf
   ```

1. <span data-ttu-id="5b644-144">소유권을 **root** 로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b644-144">Set ownership to **root**.</span></span>

   ```
   chown root:root /etc/rsyslog.d/40-powershell.conf
   ```

1. <span data-ttu-id="5b644-145">액세스 권한 설정: **루트** 에 읽기/쓰기 권한이 있으며 **사용자** 는 읽기 권한이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b644-145">Set access permissions: **root** has read/write, **users** have read.</span></span>

   ```
   chmod 644 /etc/rsyslog.d/40-powershell.conf
   ```

## <a name="viewing-powershell-log-output-on-macos"></a><span data-ttu-id="5b644-146">MacOS에서 PowerShell 로그 출력 보기</span><span class="sxs-lookup"><span data-stu-id="5b644-146">Viewing PowerShell log output on macOS</span></span>

<span data-ttu-id="5b644-147">MacOS에서 PowerShell 로그 출력을 보는 가장 쉬운 방법은 **콘솔** 응용 프로그램을 사용 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="5b644-147">The easiest method for viewing PowerShell log output on macOS is using the **Console** application.</span></span>

1. <span data-ttu-id="5b644-148">**콘솔** 응용 프로그램을 검색 하 여 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b644-148">Search for the **Console** application and launch it.</span></span>
1. <span data-ttu-id="5b644-149">**장치** 에서 컴퓨터 이름을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b644-149">Select the Machine name under **Devices**.</span></span>
1. <span data-ttu-id="5b644-150">**Search** `pwsh` PowerShell 주 이진에 대해 검색 필드에를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b644-150">In the **Search** field, enter `pwsh` for the PowerShell main binary.</span></span>
1. <span data-ttu-id="5b644-151">검색 필터를에서로 변경 합니다 `Any` `Process` .</span><span class="sxs-lookup"><span data-stu-id="5b644-151">Change the search filter from `Any` to `Process`.</span></span>
1. <span data-ttu-id="5b644-152">작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b644-152">Perform the operations.</span></span>
1. <span data-ttu-id="5b644-153">필요에 따라 나중에 사용 하기 위해 검색을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b644-153">Optionally, save the search for future use.</span></span>

<span data-ttu-id="5b644-154">**콘솔** 에서 PowerShell의 특정 프로세스 인스턴스를 필터링 하기 위해 변수는 `$pid` 프로세스 ID를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b644-154">To filter on a specific process instance of PowerShell in the **Console** , the variable `$pid` contains the process ID.</span></span>

1. <span data-ttu-id="5b644-155">**검색** 필드에 **PID** (프로세스 ID)를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b644-155">Enter the **pid** (Process ID) in the **Search** field.</span></span>
1. <span data-ttu-id="5b644-156">검색 필터를로 변경 `PID` 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b644-156">Change the search filter to `PID`.</span></span>
1. <span data-ttu-id="5b644-157">작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b644-157">Perform the operations.</span></span>

### <a name="viewing-powershell-log-output-from-a-command-line"></a><span data-ttu-id="5b644-158">명령줄에서 PowerShell 로그 출력 보기</span><span class="sxs-lookup"><span data-stu-id="5b644-158">Viewing PowerShell log output from a command line</span></span>

<span data-ttu-id="5b644-159">명령을 `log` 사용 하 여 명령줄에서 PowerShell 로그 항목을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b644-159">The `log` command can be used to view PowerShell log entries from the command line.</span></span>

```
sudo log stream --predicate 'process == "pwsh"' --info
```

### <a name="persisting-powershell-log-output"></a><span data-ttu-id="5b644-160">PowerShell 로그 출력 유지</span><span class="sxs-lookup"><span data-stu-id="5b644-160">Persisting PowerShell log output</span></span>

<span data-ttu-id="5b644-161">기본적으로 PowerShell은 macOS에서 기본 메모리 전용 로깅을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b644-161">By default, PowerShell uses the default memory-only logging on macOS.</span></span> <span data-ttu-id="5b644-162">명령을 사용 하 여 지 속성을 사용 하도록 설정 하면이 동작을 변경할 수 있습니다 `log config` .</span><span class="sxs-lookup"><span data-stu-id="5b644-162">This behavior can be changed to enable persistence using the `log config` command.</span></span>

<span data-ttu-id="5b644-163">다음 스크립트는 정보 수준 로깅 및 지 속성을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b644-163">The following script enables info level logging and persistence:</span></span>

```
log config --subsystem com.microsoft.powershell --mode=persist:info,level:info
```

<span data-ttu-id="5b644-164">다음 명령은 PowerShell 로깅을 기본 상태로 되돌립니다.</span><span class="sxs-lookup"><span data-stu-id="5b644-164">The following command reverts PowerShell logging to the default state:</span></span>

```
log config --subsystem com.microsoft.powershell --mode=persist:default,level:default
```

<span data-ttu-id="5b644-165">지 속성을 사용 하도록 설정한 후에는 `log show` 명령을 사용 하 여 로그 항목을 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b644-165">After persistence is enabled, the `log show` command can be used to export log items.</span></span> <span data-ttu-id="5b644-166">명령은 마지막 N 개 항목, 지정 된 시간 이후의 항목 또는 지정 된 시간 범위 내의 항목을 내보내기 위한 옵션을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b644-166">The command provides options for exporting the last N items, items since a given time, or items within a given time span.</span></span>

<span data-ttu-id="5b644-167">예를 들어 다음 명령은 이후 항목을 내보냅니다 `9am on April 5 of 2018` .</span><span class="sxs-lookup"><span data-stu-id="5b644-167">For example, the following command exports items since `9am on April 5 of 2018`:</span></span>

```
log show --info --start "2018-04-05 09:00:00" --predicate "process = 'pwsh'"
```

<span data-ttu-id="5b644-168">`log`추가 정보는를 실행 하 여에 대 한 도움말을 볼 수 있습니다 `log show --help` .</span><span class="sxs-lookup"><span data-stu-id="5b644-168">You can get help for `log` by running `log show --help` for additional details.</span></span>

> [!TIP]
> <span data-ttu-id="5b644-169">PowerShell 프롬프트 또는 스크립트에서 로그 명령을 실행할 때 전체 조건자 문자열과 작은따옴표를 큰따옴표로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="5b644-169">When executing any of the log commands from a PowerShell prompt or script, use double quotes around the entire predicate string and single quotes within.</span></span> <span data-ttu-id="5b644-170">이렇게 하면 조건자 문자열 내에서 큰따옴표 문자를 이스케이프 하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b644-170">This avoids the need to escape double quote characters within the predicate string.</span></span>

<span data-ttu-id="5b644-171">또한 이벤트 로그를 중앙 이벤트 로그 수집기 또는 [Siem][] 집계와 같은 보다 안전한 위치에 저장 하는 것을 고려할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b644-171">You may also want to consider saving the event logs to a more secure location such as a central event log collector, or [SIEM][] aggregator.</span></span> <span data-ttu-id="5b644-172">Azure에서 SIEM을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b644-172">You can set up SIEM in Azure.</span></span> <span data-ttu-id="5b644-173">자세한 내용은 [일반 SIEM 통합](/cloud-app-security/siem)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5b644-173">For more information, see [Generic SIEM integration](/cloud-app-security/siem).</span></span>

## <a name="configuring-logging-on-a-non-windows-system"></a><span data-ttu-id="5b644-174">비 Windows 시스템에 대 한 로깅 구성</span><span class="sxs-lookup"><span data-stu-id="5b644-174">Configuring logging on a non-Windows system</span></span>

<span data-ttu-id="5b644-175">Windows에서는 ETW 추적 수신기를 만들거나 이벤트 뷰어를 사용 하 여 분석 로깅을 사용 하도록 설정 하 여 로깅을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b644-175">On Windows, logging is configured by creating ETW trace listeners or by using the Event Viewer to enable Analytic logging.</span></span> <span data-ttu-id="5b644-176">Linux 및 macOS에서 로깅은 파일을 사용 하 여 구성 됩니다 `powershell.config.json` .</span><span class="sxs-lookup"><span data-stu-id="5b644-176">On Linux and macOS, logging is configured using the file `powershell.config.json`.</span></span> <span data-ttu-id="5b644-177">이 섹션의 나머지 부분에서는 비 Windows 시스템에 대 한 PowerShell 로깅을 구성 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b644-177">The rest of this section will discuss configuring PowerShell logging on a non-Windows system.</span></span>

<span data-ttu-id="5b644-178">기본적으로 PowerShell은 작업 채널에 대 한 정보 로깅을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b644-178">By default, PowerShell enables informational logging to the operational channel.</span></span> <span data-ttu-id="5b644-179">즉, 작업으로 표시 되 고 정보 보다 더 높은 로그 (추적) 수준을 기록 하는 PowerShell에서 생성 되는 로그 출력을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b644-179">What this means is any log output produced by PowerShell that is marked as operational and has a log (trace) level greater than informational will be logged.</span></span> <span data-ttu-id="5b644-180">때로는 진단에 자세한 로그 출력과 같은 추가 로그 출력이 필요 하거나 분석 로그 출력을 사용 하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b644-180">Occasionally, diagnoses may require additional log output, such as verbose log output or enabling analytic log output.</span></span>

<span data-ttu-id="5b644-181">이 파일은 `powershell.config.json` PowerShell 디렉터리에 상주 하는 **JSON** 형식의 파일입니다 `$PSHOME` .</span><span class="sxs-lookup"><span data-stu-id="5b644-181">The file `powershell.config.json` is a **JSON** formatted file residing in the PowerShell `$PSHOME` directory.</span></span> <span data-ttu-id="5b644-182">PowerShell을 설치할 때마다이 파일의 복사본을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b644-182">Each installation of PowerShell uses its own copy of this file.</span></span> <span data-ttu-id="5b644-183">일반 작업의 경우이 파일은 변경 되지 않고 그대로 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b644-183">For normal operation, this file is left unchanged.</span></span> <span data-ttu-id="5b644-184">파일의 일부 설정을 변경 하는 것이 유용할 수 있지만, 동일한 시스템 또는 동일한 버전의 여러 복사본 (아래 표 참조)에 대 한 여러 PowerShell 버전을 진단 하거나 구분 하기 위해 파일의 일부 설정을 변경 하는 것이 유용할 수 있습니다 `LogIdentity` .</span><span class="sxs-lookup"><span data-stu-id="5b644-184">Although it can be useful, to change some of the settings in the file, for diagnosis or for distinguishing between multiple PowerShell versions on the same system or even multiple copies of the same version (See `LogIdentity` in the table below).</span></span>

<span data-ttu-id="5b644-185">다음 코드는 구성의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="5b644-185">The following code is an example configuration:</span></span>

```json
{
  "Microsoft.PowerShell:ExecutionPolicy": "RemoteSigned",
  "PowerShellPolicies": {
    "ScriptExecution": {
      "ExecutionPolicy": "RemoteSigned",
      "EnableScripts": true
    },
    "ScriptBlockLogging": {
      "EnableScriptBlockInvocationLogging": true,
      "EnableScriptBlockLogging": true
    },
    "ModuleLogging": {
      "EnableModuleLogging": false,
      "ModuleNames": [
        "PSReadline",
        "PowerShellGet"
      ]
    },
    "ProtectedEventLogging": {
      "EnableProtectedEventLogging": false,
      "EncryptionCertificate": [
        "Joe"
      ]
    },
    "Transcription": {
      "EnableTranscripting": true,
      "EnableInvocationHeader": true,
      "OutputDirectory": "F:\\tmp\\new"
    },
    "UpdatableHelp": {
      "DefaultSourcePath": "f:\\temp"
    },
    "ConsoleSessionConfiguration": {
      "EnableConsoleSessionConfiguration": false,
      "ConsoleSessionConfigurationName": "name"
    }
  },
  "LogLevel": "verbose"
}
```

<span data-ttu-id="5b644-186">PowerShell 로깅 구성에 대 한 속성은 다음 표에 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b644-186">The properties for configuring PowerShell logging are listed in the following table.</span></span> <span data-ttu-id="5b644-187">와 같이 별표가 표시 된 값 `Operational*` 은 파일에 값이 제공 되지 않은 경우 기본값을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b644-187">Values marked with an asterisk, such as `Operational*`, indicate the default value when no value is provided in the file.</span></span>

|<span data-ttu-id="5b644-188">속성</span><span class="sxs-lookup"><span data-stu-id="5b644-188">Property</span></span>   |<span data-ttu-id="5b644-189">값</span><span class="sxs-lookup"><span data-stu-id="5b644-189">Values</span></span>        |<span data-ttu-id="5b644-190">Description</span><span class="sxs-lookup"><span data-stu-id="5b644-190">Description</span></span>                                  |
|-----------|--------------|---------------------------------------------|
|`LogIdentity`|<span data-ttu-id="5b644-191">(문자열 이름)</span><span class="sxs-lookup"><span data-stu-id="5b644-191">(string name)</span></span> |<span data-ttu-id="5b644-192">로깅할 때 사용할 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="5b644-192">The name to use when logging.</span></span> <span data-ttu-id="5b644-193">기본적으로</span><span class="sxs-lookup"><span data-stu-id="5b644-193">By default,</span></span>  |
|           |<span data-ttu-id="5b644-194">슬래시</span><span class="sxs-lookup"><span data-stu-id="5b644-194">powershell\*</span></span>   |<span data-ttu-id="5b644-195">powershell은 id입니다.</span><span class="sxs-lookup"><span data-stu-id="5b644-195">powershell is the identity.</span></span> <span data-ttu-id="5b644-196">이 값은 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b644-196">This value can be</span></span>|
|           |              |<span data-ttu-id="5b644-197">두의 차이를 알리는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b644-197">used to tell the difference between two</span></span>      |
|           |              |<span data-ttu-id="5b644-198">PowerShell 설치 인스턴스 (예:)</span><span class="sxs-lookup"><span data-stu-id="5b644-198">instances of a PowerShell installation, such</span></span> |
|           |              |<span data-ttu-id="5b644-199">릴리스 및 베타 버전으로</span><span class="sxs-lookup"><span data-stu-id="5b644-199">as a release and beta version.</span></span> <span data-ttu-id="5b644-200">이 값은</span><span class="sxs-lookup"><span data-stu-id="5b644-200">This value is</span></span> |
|           |              |<span data-ttu-id="5b644-201">로그 출력을로 리디렉션하는 데도 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b644-201">also used to redirect log output to a</span></span>        |
|           |              |<span data-ttu-id="5b644-202">Linux에서 파일을 분리 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b644-202">separate file on Linux.</span></span> <span data-ttu-id="5b644-203">다음에 대 한 설명을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5b644-203">See the discussion of</span></span>|
|           |              |<span data-ttu-id="5b644-204">위의 **rsyslog**</span><span class="sxs-lookup"><span data-stu-id="5b644-204">**rsyslog** above.</span></span>                           |
|`LogChannels`|<span data-ttu-id="5b644-205">주기와</span><span class="sxs-lookup"><span data-stu-id="5b644-205">Operational\*</span></span>  |<span data-ttu-id="5b644-206">사용할 채널입니다.</span><span class="sxs-lookup"><span data-stu-id="5b644-206">The channels to enable.</span></span> <span data-ttu-id="5b644-207">값 구분</span><span class="sxs-lookup"><span data-stu-id="5b644-207">Separate the values</span></span>|
|           |<span data-ttu-id="5b644-208">Analytic</span><span class="sxs-lookup"><span data-stu-id="5b644-208">Analytic</span></span>      |<span data-ttu-id="5b644-209">하나 이상의을 지정할 때 쉼표를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b644-209">with a comma when specifying more than one.</span></span>  |
|`LogLevel`   |<span data-ttu-id="5b644-210">Always</span><span class="sxs-lookup"><span data-stu-id="5b644-210">Always</span></span>        |<span data-ttu-id="5b644-211">단일 값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b644-211">Specify a single value.</span></span> <span data-ttu-id="5b644-212">이 값을 사용 하면</span><span class="sxs-lookup"><span data-stu-id="5b644-212">The value enables</span></span>  |
|           |<span data-ttu-id="5b644-213">중요</span><span class="sxs-lookup"><span data-stu-id="5b644-213">Critical</span></span>      |<span data-ttu-id="5b644-214">그리고 그 위에 있는 모든 값은</span><span class="sxs-lookup"><span data-stu-id="5b644-214">itself and all values above it in the</span></span>        |
|           |<span data-ttu-id="5b644-215">오류</span><span class="sxs-lookup"><span data-stu-id="5b644-215">Error</span></span>         |<span data-ttu-id="5b644-216">왼쪽에 나열 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b644-216">list to the left.</span></span>                            |
|           |<span data-ttu-id="5b644-217">경고</span><span class="sxs-lookup"><span data-stu-id="5b644-217">Warning</span></span>       |                                             |
|           |<span data-ttu-id="5b644-218">위해서</span><span class="sxs-lookup"><span data-stu-id="5b644-218">Informational\*</span></span>|                                             |
|           |<span data-ttu-id="5b644-219">자세히</span><span class="sxs-lookup"><span data-stu-id="5b644-219">Verbose</span></span>       |                                             |
|           |<span data-ttu-id="5b644-220">디버그</span><span class="sxs-lookup"><span data-stu-id="5b644-220">Debug</span></span>         |                                             |
|`LogKeywords`|<span data-ttu-id="5b644-221">Runspace</span><span class="sxs-lookup"><span data-stu-id="5b644-221">Runspace</span></span>      |<span data-ttu-id="5b644-222">키워드는 로깅을 제한 하는 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b644-222">Keywords provide the ability to limit logging</span></span>|
|           |<span data-ttu-id="5b644-223">파이프라인</span><span class="sxs-lookup"><span data-stu-id="5b644-223">Pipeline</span></span>      |<span data-ttu-id="5b644-224">PowerShell 내의 특정 구성 요소에 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b644-224">to specific components within PowerShell.</span></span> <span data-ttu-id="5b644-225">기준</span><span class="sxs-lookup"><span data-stu-id="5b644-225">By</span></span> |
|           |<span data-ttu-id="5b644-226">프로토콜</span><span class="sxs-lookup"><span data-stu-id="5b644-226">Protocol</span></span>      |<span data-ttu-id="5b644-227">기본값, 모든 키워드를 사용 하도록 설정 및 변경</span><span class="sxs-lookup"><span data-stu-id="5b644-227">default, all keywords are enabled and change</span></span> |
|           |<span data-ttu-id="5b644-228">전송</span><span class="sxs-lookup"><span data-stu-id="5b644-228">Transport</span></span>     |<span data-ttu-id="5b644-229">이 값은 매우 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b644-229">this value is only useful for very</span></span>           |
|           |<span data-ttu-id="5b644-230">호스트</span><span class="sxs-lookup"><span data-stu-id="5b644-230">Host</span></span>          |<span data-ttu-id="5b644-231">특수 한 문제 해결.</span><span class="sxs-lookup"><span data-stu-id="5b644-231">specialized troubleshooting.</span></span>                |
|           |<span data-ttu-id="5b644-232">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5b644-232">Cmdlets</span></span>       |                                             |
|           |<span data-ttu-id="5b644-233">serializer</span><span class="sxs-lookup"><span data-stu-id="5b644-233">Serializer</span></span>    |                                             |
|           |<span data-ttu-id="5b644-234">세션</span><span class="sxs-lookup"><span data-stu-id="5b644-234">Session</span></span>       |                                             |
|           |<span data-ttu-id="5b644-235">ManagedPlugin</span><span class="sxs-lookup"><span data-stu-id="5b644-235">ManagedPlugin</span></span> |                                             |

## <a name="see-also"></a><span data-ttu-id="5b644-236">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5b644-236">See also</span></span>

<span data-ttu-id="5b644-237">Linux **syslog** 및 **Rsyslog** 의 경우 linux 컴퓨터의 로컬 페이지를 참조 하세요 `man` .</span><span class="sxs-lookup"><span data-stu-id="5b644-237">For Linux **syslog** and **rsyslog.conf** information, refer to the Linux computer's local `man` pages.</span></span>

<span data-ttu-id="5b644-238">MacOS **os_log** 내용은 [os_log 개발자 설명서](https://developer.apple.com/documentation/os/os_log)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5b644-238">For macOS **os_log** information, see [os_log developer documentation](https://developer.apple.com/documentation/os/os_log).</span></span>

[<span data-ttu-id="5b644-239">about_Logging_Windows</span><span class="sxs-lookup"><span data-stu-id="5b644-239">about_Logging_Windows</span></span>](about_Logging_Windows.md)

[<span data-ttu-id="5b644-240">일반 SIEM 통합</span><span class="sxs-lookup"><span data-stu-id="5b644-240">Generic SIEM integration</span></span>](/cloud-app-security/siem)

<!-- link references -->
[SIEM]: https://wikipedia.org/wiki/Security_information_and_event_management

