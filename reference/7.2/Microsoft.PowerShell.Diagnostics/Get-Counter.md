---
external help file: Microsoft.PowerShell.Commands.Diagnostics.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Diagnostics
ms.date: 11/06/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.diagnostics/get-counter?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Counter
ms.openlocfilehash: 4aed8db557b2d623aba4cd7218524af9957674c9
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99605217"
---
# <span data-ttu-id="79fef-102">Get-Counter</span><span class="sxs-lookup"><span data-stu-id="79fef-102">Get-Counter</span></span>

## <span data-ttu-id="79fef-103">개요</span><span class="sxs-lookup"><span data-stu-id="79fef-103">SYNOPSIS</span></span>
<span data-ttu-id="79fef-104">로컬 및 원격 컴퓨터에서 성능 카운터 데이터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-104">Gets performance counter data from local and remote computers.</span></span>

## <span data-ttu-id="79fef-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="79fef-105">SYNTAX</span></span>

### <span data-ttu-id="79fef-106">GetCounterSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="79fef-106">GetCounterSet (Default)</span></span>

```
Get-Counter [[-Counter] <String[]>] [-SampleInterval <Int32>] [-MaxSamples <Int64>] [-Continuous]
 [-ComputerName <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="79fef-107">ListSetSet</span><span class="sxs-lookup"><span data-stu-id="79fef-107">ListSetSet</span></span>

```
Get-Counter [-ListSet] <String[]> [-ComputerName <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="79fef-108">설명</span><span class="sxs-lookup"><span data-stu-id="79fef-108">DESCRIPTION</span></span>

<span data-ttu-id="79fef-109">`Get-Counter`Cmdlet은 Windows 운영 체제 제품군의 성능 모니터링 계측에서 직접 성능 카운터 데이터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-109">The `Get-Counter` cmdlet gets performance counter data directly from the performance monitoring instrumentation in the Windows family of operating systems.</span></span> <span data-ttu-id="79fef-110">`Get-Counter` 로컬 컴퓨터 또는 원격 컴퓨터에서 성능 데이터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-110">`Get-Counter` gets performance data from a local computer or remote computers.</span></span>

<span data-ttu-id="79fef-111">매개 변수를 사용 `Get-Counter` 하 여 하나 이상의 컴퓨터를 지정 하 고, 성능 카운터 집합과 여기에 포함 된 인스턴스를 나열 하 고, 샘플 간격을 설정 하 고, 최대 샘플 수를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-111">You can use the `Get-Counter` parameters to specify one or more computers, list the performance counter sets and the instances they contain, set the sample intervals, and specify the maximum number of samples.</span></span> <span data-ttu-id="79fef-112">매개 변수가 없는 경우 `Get-Counter` 시스템 카운터 집합에 대 한 성능 카운터 데이터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-112">Without parameters, `Get-Counter` gets performance counter data for a set of system counters.</span></span>

<span data-ttu-id="79fef-113">많은 카운터 집합은 ACL (액세스 제어 목록)에 의해 보호 됩니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-113">Many counter sets are protected by access control lists (ACL).</span></span> <span data-ttu-id="79fef-114">모든 카운터 집합을 보려면 **관리자 권한으로 실행** 옵션을 사용 하 여 PowerShell을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-114">To see all counter sets, open PowerShell with the **Run as administrator** option.</span></span>

<span data-ttu-id="79fef-115">이 cmdlet은 PowerShell 7에서 다시 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-115">This cmdlet was reintroduced in PowerShell 7.</span></span>

## <span data-ttu-id="79fef-116">예제</span><span class="sxs-lookup"><span data-stu-id="79fef-116">EXAMPLES</span></span>

### <span data-ttu-id="79fef-117">예제 1: 카운터 집합 목록 가져오기</span><span class="sxs-lookup"><span data-stu-id="79fef-117">Example 1: Get the counter set list</span></span>

<span data-ttu-id="79fef-118">이 예제에서는 로컬 컴퓨터의 카운터 집합 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-118">This example gets the local computer's list of counter sets.</span></span>

```powershell
Get-Counter -ListSet *
```

```Output
CounterSetName     : Processor
MachineName        : .
CounterSetType     : MultiInstance
Description        : The Processor performance object consists of counters that measure aspects ...
                     computer that performs arithmetic and logical computations, initiates ...
                     computer can have multiple processors.  The processor object represents ...
Paths              : {\Processor(*)\% Processor Time, \Processor(*)\% User Time, ...
PathsWithInstances : {\Processor(0)\% Processor Time, \Processor(1)\% Processor Time, ...
Counter            : {\Processor(*)\% Processor Time, \Processor(*)\% User Time, ...
```

<span data-ttu-id="79fef-119">`Get-Counter`**listset** 매개 변수를 별표 ()와 함께 사용 `*` 하 여 카운터 집합 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-119">`Get-Counter` uses the **ListSet** parameter with an asterisk (`*`) to get the list of counter sets.</span></span>
<span data-ttu-id="79fef-120">`.` **MachineName** 열의 점 ()은 로컬 컴퓨터를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-120">The dot (`.`) in the **MachineName** column represents the local computer.</span></span>

### <span data-ttu-id="79fef-121">예제 2: SampleInterval 및 MaxSamples 지정</span><span class="sxs-lookup"><span data-stu-id="79fef-121">Example 2: Specify the SampleInterval and MaxSamples</span></span>

<span data-ttu-id="79fef-122">이 예에서는 로컬 컴퓨터의 모든 프로세서에 대 한 카운터 데이터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-122">This examples gets the counter data for all processors on the local computer.</span></span> <span data-ttu-id="79fef-123">데이터는 세 개의 샘플이 있을 때까지 2 초 간격으로 수집 됩니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-123">Data is collected at two-second intervals until there are three samples.</span></span>

```powershell
Get-Counter -Counter "\Processor(_Total)\% Processor Time" -SampleInterval 2 -MaxSamples 3
```

```Output
Timestamp                 CounterSamples
---------                 --------------
6/18/2019 14:39:56        \\Computer01\processor(_total)\% processor time :
                          20.7144271584086

6/18/2019 14:39:58        \\Computer01\processor(_total)\% processor time :
                          10.4391790575511

6/18/2019 14:40:01        \\Computer01\processor(_total)\% processor time :
                          37.5968799396998
```

<span data-ttu-id="79fef-124">`Get-Counter`**counter 매개 변수** 를 사용 하 여 카운터 경로를 지정 합니다 `\Processor(_Total)\% Processor Time` .</span><span class="sxs-lookup"><span data-stu-id="79fef-124">`Get-Counter` uses the **Counter** parameter to specify the counter path `\Processor(_Total)\% Processor Time`.</span></span> <span data-ttu-id="79fef-125">**SampleInterval** 매개 변수는 카운터를 확인 하는 2 초 간격을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-125">The **SampleInterval** parameter sets a two-second interval to check the counter.</span></span> <span data-ttu-id="79fef-126">**Maxsamples** 는 카운터가 카운터를 확인할 수 있는 최대 횟수를 3 개 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-126">**MaxSamples** determines that three is the maximum number of times to check the counter.</span></span>

### <span data-ttu-id="79fef-127">예제 3: 카운터의 연속 샘플 가져오기</span><span class="sxs-lookup"><span data-stu-id="79fef-127">Example 3: Get continuous samples of a counter</span></span>

<span data-ttu-id="79fef-128">이 예에서는 초 마다 카운터에 대 한 연속 샘플을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-128">This examples gets continuous samples for a counter every second.</span></span> <span data-ttu-id="79fef-129">명령을 중지 하려면 <kbd>ctrl</kbd> + <kbd>C</kbd>를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-129">To stop the command, press <kbd>CTRL</kbd>+<kbd>C</kbd>.</span></span> <span data-ttu-id="79fef-130">샘플 사이에 더 긴 간격을 지정 하려면 **SampleInterval** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-130">To specify a longer interval between samples, use the **SampleInterval** parameter.</span></span>

```powershell
Get-Counter -Counter "\Processor(_Total)\% Processor Time" -Continuous
```

```Output
Timestamp                 CounterSamples
---------                 --------------
6/19/2019 15:35:03        \\Computer01\processor(_total)\% processor time :
                          43.8522842937022

6/19/2019 15:35:04        \\Computer01\processor(_total)\% processor time :
                          29.7896844697383

6/19/2019 15:35:05        \\Computer01\processor(_total)\% processor time :
                          29.4962645638135

6/19/2019 15:35:06        \\Computer01\processor(_total)\% processor time :
                          25.5901500127408
```

<span data-ttu-id="79fef-131">`Get-Counter`**counter 매개 변수** 를 사용 하 여 카운터를 지정 합니다 `\Processor\% Processor Time` .</span><span class="sxs-lookup"><span data-stu-id="79fef-131">`Get-Counter` uses the **Counter** parameter to specify the `\Processor\% Processor Time` counter.</span></span>
<span data-ttu-id="79fef-132">**연속** 매개 변수는 명령이 <kbd>CTRL</kbd>C를 사용 하 여 중지 될 때까지 초 마다 샘플을 가져오도록 지정 합니다 + <kbd></kbd>.</span><span class="sxs-lookup"><span data-stu-id="79fef-132">The **Continuous** parameter specifies to get samples every second until the command is stopped with <kbd>CTRL</kbd>+<kbd>C</kbd>.</span></span>

### <span data-ttu-id="79fef-133">예제 4: 카운터 집합의 사전순 목록</span><span class="sxs-lookup"><span data-stu-id="79fef-133">Example 4: Alphabetical list of counter sets</span></span>

<span data-ttu-id="79fef-134">이 예제에서는 파이프라인을 사용 하 여 카운터 목록 집합을 가져온 다음 목록을 사전순으로 정렬 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-134">This example uses the pipeline to get the counter list set and then sort the list in alphabetical order.</span></span>

```powershell
Get-Counter -ListSet * |
  Sort-Object -Property CounterSetName |
    Format-Table CounterSetName, CounterSetType -AutoSize
```

```Output
CounterSetName                        CounterSetType
--------------                        --------------
.NET CLR Data                         SingleInstance
.NET Data Provider for SqlServer      SingleInstance
AppV Client Streamed Data Percentage  SingleInstance
Authorization Manager Applications    SingleInstance
BitLocker                             MultiInstance
Bluetooth Device                      SingleInstance
Cache                                 SingleInstance
Client Side Caching                   SingleInstance
```

<span data-ttu-id="79fef-135">`Get-Counter`**Listset** 매개 변수를 별표 ()와 함께 사용 `*` 하 여 전체 카운터 집합 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-135">`Get-Counter` uses the **ListSet** parameter with an asterisk (`*`) to get a complete list of counter sets.</span></span> <span data-ttu-id="79fef-136">**CounterSet** 개체는 파이프라인으로 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-136">The **CounterSet** objects are sent down the pipeline.</span></span> <span data-ttu-id="79fef-137">`Sort-Object`**Property** 매개 변수를 사용 하 여 **CounterSetName** 를 기준으로 개체를 정렬 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-137">`Sort-Object` uses the **Property** parameter to specify that the objects are sorted by **CounterSetName**.</span></span> <span data-ttu-id="79fef-138">개체는 파이프라인에서로 전송 됩니다 `Format-Table` .</span><span class="sxs-lookup"><span data-stu-id="79fef-138">The objects are sent down the pipeline to `Format-Table`.</span></span> <span data-ttu-id="79fef-139">**AutoSize** 매개 변수는 잘림을 최소화 하도록 열 너비를 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-139">The **AutoSize** parameter adjusts the column widths to minimize truncation.</span></span>

<span data-ttu-id="79fef-140">`.` **MachineName** 열의 점 ()은 로컬 컴퓨터를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-140">The dot (`.`) in the **MachineName** column represents the local computer.</span></span>

### <span data-ttu-id="79fef-141">예 5: 백그라운드 작업을 실행 하 여 카운터 데이터 가져오기</span><span class="sxs-lookup"><span data-stu-id="79fef-141">Example 5: Run a background job to get counter data</span></span>

<span data-ttu-id="79fef-142">이 예에서는 `Start-Job` `Get-Counter` 로컬 컴퓨터에서 명령을 백그라운드 작업으로 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-142">In this example, `Start-Job` runs a `Get-Counter` command as a background job on the local computer.</span></span>
<span data-ttu-id="79fef-143">작업에서 성능 카운터 출력을 보려면 cmdlet을 사용 합니다 `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="79fef-143">To view the performance counter output from the job, use the `Receive-Job` cmdlet.</span></span>

```powershell
Start-Job -ScriptBlock {Get-Counter -Counter "\LogicalDisk(_Total)\% Free Space" -MaxSamples 1000}
```

```Output
Id     Name  PSJobTypeName   State    HasMoreData  Location   Command
--     ----  -------------   -----    -----------  --------   -------
1      Job1  BackgroundJob   Running  True         localhost  Get-Counter -Counter
```

<span data-ttu-id="79fef-144">`Start-Job`**ScriptBlock** 매개 변수를 사용 하 여 `Get-Counter` 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-144">`Start-Job` uses the **ScriptBlock** parameter to run a `Get-Counter` command.</span></span> <span data-ttu-id="79fef-145">`Get-Counter`**counter 매개 변수** 를 사용 하 여 카운터 경로를 지정 합니다 `\LogicalDisk(_Total)\% Free Space` .</span><span class="sxs-lookup"><span data-stu-id="79fef-145">`Get-Counter` uses the **Counter** parameter to specify the counter path `\LogicalDisk(_Total)\% Free Space`.</span></span> <span data-ttu-id="79fef-146">**Maxsamples** 매개 변수는 카운터의 1000 샘플을 가져오도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-146">The **MaxSamples** parameter specifies to get 1000 samples of the counter.</span></span>

### <span data-ttu-id="79fef-147">예제 6: 여러 컴퓨터에서 카운터 데이터 가져오기</span><span class="sxs-lookup"><span data-stu-id="79fef-147">Example 6: Get counter data from multiple computers</span></span>

<span data-ttu-id="79fef-148">이 예에서는 변수를 사용 하 여 두 컴퓨터에서 성능 카운터 데이터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-148">This example uses a variable to get performance counter data from two computers.</span></span>

```powershell
$DiskReads = "\LogicalDisk(C:)\Disk Reads/sec"
$DiskReads | Get-Counter -ComputerName Server01, Server02 -MaxSamples 10
```

```Output
Timestamp                 CounterSamples
---------                 --------------
6/21/2019 10:51:04        \\Server01\logicaldisk(c:)\disk reads/sec :
                          0

                          \\Server02\logicaldisk(c:)\disk reads/sec :
                          0.983050344269146
```

<span data-ttu-id="79fef-149">`$DiskReads`변수는 카운터 경로를 저장 합니다 `\LogicalDisk(C:)\Disk Reads/sec` .</span><span class="sxs-lookup"><span data-stu-id="79fef-149">The `$DiskReads` variable stores the `\LogicalDisk(C:)\Disk Reads/sec` counter path.</span></span> <span data-ttu-id="79fef-150">`$DiskReads`변수가 파이프라인에서로 전송 됩니다 `Get-Counter` .</span><span class="sxs-lookup"><span data-stu-id="79fef-150">The `$DiskReads` variable is sent down the pipeline to `Get-Counter`.</span></span> <span data-ttu-id="79fef-151">**Counter** 는 첫 번째 위치 매개 변수 이며에 저장 된 경로를 허용 합니다 `$DiskReads` .</span><span class="sxs-lookup"><span data-stu-id="79fef-151">**Counter** is the first position parameter and accepts the path stored in `$DiskReads`.</span></span> <span data-ttu-id="79fef-152">**ComputerName** 은 두 컴퓨터를 지정 하 고 **maxsamples** 는 각 컴퓨터에서 10 개의 샘플을 가져오도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-152">**ComputerName** specifies the two computers and **MaxSamples** specifies to get 10 samples from each computer.</span></span>

### <span data-ttu-id="79fef-153">예 7: 여러 임의의 컴퓨터에서 카운터의 인스턴스 값 가져오기</span><span class="sxs-lookup"><span data-stu-id="79fef-153">Example 7: Get a counter's instance values from multiple random computers</span></span>

<span data-ttu-id="79fef-154">이 예제에서는 엔터프라이즈의 원격 컴퓨터 50 대 한 성능 카운터 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-154">This example gets the value of a performance counter on 50 random, remote computers in the enterprise.</span></span> <span data-ttu-id="79fef-155">**ComputerName** 매개 변수는 변수에 저장 된 임의의 컴퓨터 이름을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-155">The **ComputerName** parameter uses random computer names stored in a variable.</span></span> <span data-ttu-id="79fef-156">변수의 컴퓨터 이름을 업데이트 하려면 변수를 다시 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-156">To update the computer names in the variable, recreate the variable.</span></span>

<span data-ttu-id="79fef-157">**ComputerName** 매개 변수의 서버 이름에 대 한 대안은 텍스트 파일을 사용 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-157">An alternative for the server names in the **ComputerName** parameter is to use a text file.</span></span> <span data-ttu-id="79fef-158">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="79fef-158">For example:</span></span>

`-ComputerName (Get-Random (Get-Content -Path C:\Servers.txt) -Count 50)`

<span data-ttu-id="79fef-159">카운터 경로에는 `*` 각 원격 컴퓨터의 프로세서에 대 한 데이터를 가져오기 위해 인스턴스 이름에 별표 ()가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-159">The counter path includes an asterisk (`*`) in the instance name to get the data for each of the remote computer's processors.</span></span>

```powershell
$Servers = Get-Random (Get-Content -Path C:\Servers.txt) -Count 50
$Counter = "\Processor(*)\% Processor Time"
Get-Counter -Counter $Counter -ComputerName $Servers
```

```Output
Timestamp                 CounterSamples
---------                 --------------
6/20/2019 12:20:35        \\Server01\processor(0)\% processor time :
                          6.52610319637854

                          \\Server01\processor(1)\% processor time :
                          3.41030663625782

                          \\Server01\processor(2)\% processor time :
                          9.64189975649925

                          \\Server01\processor(3)\% processor time :
                          1.85240835619747

                          \\Server01\processor(_total)\% processor time :
                          5.35768447160776
```

<span data-ttu-id="79fef-160">`Get-Random`Cmdlet은 `Get-Content` 를 사용 하 여 파일에서 50 임의의 컴퓨터 이름을 선택 `Servers.txt` 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-160">The `Get-Random` cmdlet uses `Get-Content` to select 50 random computer names from the `Servers.txt` file.</span></span> <span data-ttu-id="79fef-161">원격 컴퓨터 이름은 변수에 저장 됩니다 `$Servers` .</span><span class="sxs-lookup"><span data-stu-id="79fef-161">The remote computer names are stored in the `$Servers` variable.</span></span> <span data-ttu-id="79fef-162">`\Processor(*)\% Processor Time`카운터의 경로는 변수에 저장 됩니다 `$Counter` .</span><span class="sxs-lookup"><span data-stu-id="79fef-162">The `\Processor(*)\% Processor Time` counter's path is stored in the `$Counter` variable.</span></span> <span data-ttu-id="79fef-163">`Get-Counter`**Counter** 매개 변수를 사용 하 여 변수의 카운터를 지정 `$Counter` 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-163">`Get-Counter` uses the **Counter** parameter to specify the counters in the `$Counter` variable.</span></span> <span data-ttu-id="79fef-164">**ComputerName** 매개 변수는 변수의 컴퓨터 이름을 지정 합니다 `$Servers` .</span><span class="sxs-lookup"><span data-stu-id="79fef-164">The **ComputerName** parameter specifies the computer names in the `$Servers` variable.</span></span>

### <span data-ttu-id="79fef-165">예 8: 경로 속성을 사용 하 여 형식이 지정 된 경로 이름 가져오기</span><span class="sxs-lookup"><span data-stu-id="79fef-165">Example 8: Use the Path property to get formatted path names</span></span>

<span data-ttu-id="79fef-166">이 예제에서는 카운터 집합의 **path** 속성을 사용 하 여 성능 카운터에 대해 형식이 지정 된 경로 이름을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-166">This example uses the **Path** property of a counter set to find the formatted path names for the performance counters.</span></span>

<span data-ttu-id="79fef-167">파이프라인은 cmdlet과 함께 `Where-Object` 경로 이름의 하위 집합을 찾는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-167">The pipeline is used with the `Where-Object` cmdlet to find a subset of the path names.</span></span> <span data-ttu-id="79fef-168">카운터 집합의 전체 목록을 검색 하려면 파이프라인 ( `|` ) 및 명령을 제거 합니다 `Where-Object` .</span><span class="sxs-lookup"><span data-stu-id="79fef-168">To find a counter sets complete list of counter paths, remove the pipeline (`|`) and `Where-Object` command.</span></span>

<span data-ttu-id="79fef-169">는 `$_` 파이프라인의 현재 개체에 대 한 자동 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-169">The `$_` is an automatic variable for the current object in the pipeline.</span></span>
<span data-ttu-id="79fef-170">자세한 내용은 [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="79fef-170">For more information, see [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md).</span></span>

```powershell
(Get-Counter -ListSet Memory).Paths | Where-Object { $_ -like "*Cache*" }
```

```Output
\Memory\Cache Faults/sec
\Memory\Cache Bytes
\Memory\Cache Bytes Peak
\Memory\System Cache Resident Bytes
\Memory\Standby Cache Reserve Bytes
\Memory\Standby Cache Normal Priority Bytes
\Memory\Standby Cache Core Bytes
\Memory\Long-Term Average Standby Cache Lifetime (s)
```

<span data-ttu-id="79fef-171">`Get-Counter`**listset** 매개 변수를 사용 하 여 **메모리** 카운터 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-171">`Get-Counter` uses the **ListSet** parameter to specify the **Memory** counter set.</span></span> <span data-ttu-id="79fef-172">**경로** 속성이 각 경로를 문자열로 반환 하도록 명령이 괄호로 묶여 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-172">The command is enclosed in parentheses so that the **Paths** property returns each path as a string.</span></span> <span data-ttu-id="79fef-173">개체는 파이프라인에서로 전송 됩니다 `Where-Object` .</span><span class="sxs-lookup"><span data-stu-id="79fef-173">The objects are sent down the pipeline to `Where-Object`.</span></span> <span data-ttu-id="79fef-174">`Where-Object` 변수를 사용 하 여 `$_` 각 개체를 처리 하 고 연산자를 사용 하 여 `-like` 문자열에 대 한 일치 항목을 찾습니다 `*Cache*` .</span><span class="sxs-lookup"><span data-stu-id="79fef-174">`Where-Object` uses the variable `$_` to process each object and uses the `-like` operator to find matches for the string `*Cache*`.</span></span> <span data-ttu-id="79fef-175">별표 ( `*` )는 모든 문자에 대 한 와일드 카드입니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-175">The asterisks (`*`) are wildcards for any characters.</span></span>

### <span data-ttu-id="79fef-176">예 9: PathsWithInstances 속성을 사용 하 여 형식이 지정 된 경로 이름 가져오기</span><span class="sxs-lookup"><span data-stu-id="79fef-176">Example 9: Use the PathsWithInstances property to get formatted path names</span></span>

<span data-ttu-id="79fef-177">이 예제에서는 **PhysicalDisk** 성능 카운터에 대 한 인스턴스를 포함 하는 형식이 지정 된 경로 이름을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-177">This example gets the formatted path names that include the instances for the **PhysicalDisk** performance counters.</span></span>

```powershell
(Get-Counter -ListSet PhysicalDisk).PathsWithInstances
```

```Output
\PhysicalDisk(0 C:)\Current Disk Queue Length
\PhysicalDisk(_Total)\Current Disk Queue Length
\PhysicalDisk(0 C:)\% Disk Time
\PhysicalDisk(_Total)\% Disk Time
\PhysicalDisk(0 C:)\Avg. Disk Queue Length
\PhysicalDisk(_Total)\Avg. Disk Queue Length
\PhysicalDisk(0 C:)\% Disk Read Time
\PhysicalDisk(_Total)\% Disk Read Time
```

<span data-ttu-id="79fef-178">`Get-Counter`**listset** 매개 변수를 사용 하 여 **PhysicalDisk** 카운터 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-178">`Get-Counter` uses the **ListSet** parameter to specify the **PhysicalDisk** counter set.</span></span> <span data-ttu-id="79fef-179">**Pathswithinstances** 속성이 각 경로 인스턴스를 문자열로 반환 하도록 명령이 괄호로 묶여 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-179">The command is enclosed in parentheses so that the **PathsWithInstances** property returns each path instance as a string.</span></span>

### <span data-ttu-id="79fef-180">예 10: 카운터 집합의 각 카운터에 대 한 단일 값 가져오기</span><span class="sxs-lookup"><span data-stu-id="79fef-180">Example 10: Get a single value for each counter in a counter set</span></span>

<span data-ttu-id="79fef-181">이 예제에서는 로컬 컴퓨터의 **메모리** 카운터 집합에 있는 각 성능 카운터에 대해 단일 값이 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-181">In this example, a single value is returned for each performance counter in the local computer's **Memory** counter set.</span></span>

```powershell
$MemCounters = (Get-Counter -ListSet Memory).Paths
Get-Counter -Counter $MemCounters
```

```Output
Timestamp                 CounterSamples
---------                 --------------
6/19/2019 12:05:00        \\Computer01\memory\page faults/sec :
                          868.772077545597

                          \\Computer01\memory\available bytes :
                          9031176192

                          \\Computer01\memory\committed bytes :
                          8242982912

                          \\Computer01\memory\commit limit :
                          19603333120
```

<span data-ttu-id="79fef-182">`Get-Counter`**listset** 매개 변수를 사용 하 여 **메모리** 카운터 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-182">`Get-Counter` uses the **ListSet** parameter to specify the **Memory** counter set.</span></span> <span data-ttu-id="79fef-183">**경로** 속성이 각 경로를 문자열로 반환 하도록 명령이 괄호로 묶여 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-183">The command is enclosed in parentheses so that the **Paths** property returns each path as a string.</span></span> <span data-ttu-id="79fef-184">경로는 변수에 저장 됩니다 `$MemCounters` .</span><span class="sxs-lookup"><span data-stu-id="79fef-184">The paths are stored in the `$MemCounters` variable.</span></span> <span data-ttu-id="79fef-185">`Get-Counter`**counter** 매개 변수를 사용 하 여 변수의 카운터 경로를 지정 `$MemCounters` 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-185">`Get-Counter` uses the **Counter** parameter to specify the counter paths in the `$MemCounters` variable.</span></span>

### <span data-ttu-id="79fef-186">예 11: 개체의 속성 값 표시</span><span class="sxs-lookup"><span data-stu-id="79fef-186">Example 11: Display an object's property values</span></span>

<span data-ttu-id="79fef-187">**Microsoft.powershell.commands.getcounter.performancecountersample** 개체의 속성 값은 각 데이터 샘플을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-187">The property values in the **PerformanceCounterSample** object represent each data sample.</span></span> <span data-ttu-id="79fef-188">이 예제에서는 **Countersamples** 개체의 속성을 사용 하 여 데이터를 검사, 선택, 정렬 및 그룹화 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-188">In this example we use the properties of the **CounterSamples** object to examine, select, sort, and group the data.</span></span>

```powershell
$Counter = "\\Server01\Process(Idle)\% Processor Time"
$Data = Get-Counter $Counter
$Data.CounterSamples | Format-List -Property *
```

```Output
Path             : \\Server01\process(idle)\% processor time
InstanceName     : idle
CookedValue      : 198.467899571389
RawValue         : 14329160321003
SecondValue      : 128606459528326201
MultipleCount    : 1
CounterType      : Timer100Ns
Timestamp        : 6/19/2019 12:20:49
Timestamp100NSec : 128606207528320000
Status           : 0
DefaultScale     : 0
TimeBase         : 10000000
```

<span data-ttu-id="79fef-189">카운터 경로는 변수에 저장 됩니다 `$Counter` .</span><span class="sxs-lookup"><span data-stu-id="79fef-189">The counter path is stored in the `$Counter` variable.</span></span> <span data-ttu-id="79fef-190">`Get-Counter` 카운터 값의 샘플 하나를 가져오고 결과를 `$Data` 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-190">`Get-Counter` gets one sample of the counter values and stores the results in the `$Data` variable.</span></span> <span data-ttu-id="79fef-191">`$Data`변수는 **countersamples** 속성을 사용 하 여 개체의 속성을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-191">The `$Data` variable uses the **CounterSamples** property to get the object's properties.</span></span> <span data-ttu-id="79fef-192">개체는 파이프라인에서로 전송 됩니다 `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="79fef-192">The object is sent down the pipeline to `Format-List`.</span></span> <span data-ttu-id="79fef-193">**Property** 매개 변수는 별표 ( `*` ) 와일드 카드를 사용 하 여 모든 속성을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-193">The **Property** parameter uses an asterisk (`*`) wildcard to select all the properties.</span></span>

### <span data-ttu-id="79fef-194">예 12: 성능 카운터 배열 값</span><span class="sxs-lookup"><span data-stu-id="79fef-194">Example 12: Performance counter array values</span></span>

<span data-ttu-id="79fef-195">이 예제에서 변수는 각 성능 카운터를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-195">In this example, a variable stores each performance counter.</span></span> <span data-ttu-id="79fef-196">**Countersamples** 속성은 특정 카운터 값을 표시할 수 있는 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-196">The **CounterSamples** property is an array that can display specific counter values.</span></span>

<span data-ttu-id="79fef-197">각 카운터 샘플을 표시 하려면를 사용 `$Counter.CounterSamples` 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-197">To display each counter sample, use `$Counter.CounterSamples`.</span></span>

```powershell
$Counter = Get-Counter -Counter "\Processor(*)\% Processor Time"
$Counter.CounterSamples[0]
```

```Output
Path                                         InstanceName        CookedValue
----                                         ------------        -----------
\\Computer01\processor(0)\% processor time   0              1.33997091699662
```

<span data-ttu-id="79fef-198">`Get-Counter`**counter 매개 변수** 를 사용 하 여 카운터를 지정 합니다 `\Processor(*)\% Processor Time` .</span><span class="sxs-lookup"><span data-stu-id="79fef-198">`Get-Counter` uses the **Counter** parameter to specify the counter `\Processor(*)\% Processor Time`.</span></span> <span data-ttu-id="79fef-199">값은 변수에 저장 됩니다 `$Counter` .</span><span class="sxs-lookup"><span data-stu-id="79fef-199">The values are stored in the `$Counter` variable.</span></span>
<span data-ttu-id="79fef-200">`$Counter.CounterSamples[0]` 첫 번째 카운터 값의 배열 값을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-200">`$Counter.CounterSamples[0]` displays the array value for the first counter value.</span></span>

### <span data-ttu-id="79fef-201">예 13: 성능 카운터 값 비교</span><span class="sxs-lookup"><span data-stu-id="79fef-201">Example 13: Compare performance counter values</span></span>

<span data-ttu-id="79fef-202">이 예에서는 로컬 컴퓨터의 각 프로세서에서 사용 하는 프로세서 시간 크기를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-202">This example finds the amount of processor time used by each processor on the local computer.</span></span> <span data-ttu-id="79fef-203">**Countersamples** 속성은 카운터 데이터를 지정 된 값과 비교 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-203">The **CounterSamples** property is used to compare the counter data against a specified value.</span></span>

<span data-ttu-id="79fef-204">각 카운터 샘플을 표시 하려면를 사용 `$Counter.CounterSamples` 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-204">To display each counter sample, use `$Counter.CounterSamples`.</span></span>

```powershell
$Counter = Get-Counter -Counter "\Processor(*)\% Processor Time"
$Counter.CounterSamples | Where-Object { $_.CookedValue -lt "20" }
```

```Output
Path                                         InstanceName        CookedValue
----                                         ------------        -----------
\\Computer01\processor(0)\% processor time   0              12.6398025240208
\\Computer01\processor(1)\% processor time   1              15.7598095767344
```

<span data-ttu-id="79fef-205">`Get-Counter`**counter 매개 변수** 를 사용 하 여 카운터를 지정 합니다 `\Processor(*)\% Processor Time` .</span><span class="sxs-lookup"><span data-stu-id="79fef-205">`Get-Counter` uses the **Counter** parameter to specify the counter `\Processor(*)\% Processor Time`.</span></span> <span data-ttu-id="79fef-206">값은 변수에 저장 됩니다 `$Counter` .</span><span class="sxs-lookup"><span data-stu-id="79fef-206">The values are stored in the `$Counter` variable.</span></span> <span data-ttu-id="79fef-207">에 저장 된 개체는 `$Counter.CounterSamples` 파이프라인으로 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-207">The objects stored in `$Counter.CounterSamples` are sent down the pipeline.</span></span> <span data-ttu-id="79fef-208">`Where-Object` 는 스크립트 블록을 사용 하 여 각 개체 값을 지정 된 값 20과 비교 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-208">`Where-Object` uses a script block to compare each objects value against a specified value of 20.</span></span> <span data-ttu-id="79fef-209">는 `$_.CookedValue` 파이프라인의 현재 개체에 대 한 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-209">The `$_.CookedValue` is a variable for the current object in the pipeline.</span></span> <span data-ttu-id="79fef-210">**CookedValue** 가 20 미만인 카운터가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-210">Counters with a **CookedValue** that is less than 20 are displayed.</span></span>

### <span data-ttu-id="79fef-211">예 14: 성능 카운터 데이터 정렬</span><span class="sxs-lookup"><span data-stu-id="79fef-211">Example 14: Sort performance counter data</span></span>

<span data-ttu-id="79fef-212">이 예제에서는 성능 카운터 데이터를 정렬 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-212">This example shows how to sort performance counter data.</span></span> <span data-ttu-id="79fef-213">이 예제에서는 샘플 중 프로세서 시간을 가장 많이 사용 하는 컴퓨터에서 프로세스를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-213">The example finds the processes on the computer that are using the most processor time during the sample.</span></span>

```powershell
$Procs = Get-Counter -Counter "\Process(*)\% Processor Time"
$Procs.CounterSamples | Sort-Object -Property CookedValue -Descending |
   Format-Table -Property Path, InstanceName, CookedValue -AutoSize
```

```Output
Path                                                         InstanceName             CookedValue
----                                                         ------------             -----------
\\Computer01\process(_total)\% processor time                _total              395.464129650573
\\Computer01\process(idle)\% processor time                  idle                389.356575524695
\\Computer01\process(mssense)\% processor time               mssense             3.05377706293879
\\Computer01\process(csrss#1)\% processor time               csrss               1.52688853146939
\\Computer01\process(microsoftedgecp#10)\% processor time    microsoftedgecp     1.52688853146939
\\Computer01\process(runtimebroker#5)\% processor time       runtimebroker                      0
\\Computer01\process(settingsynchost)\% processor time       settingsynchost                    0
\\Computer01\process(microsoftedgecp#16)\% processor time    microsoftedgecp                    0
```

<span data-ttu-id="79fef-214">`Get-Counter`**counter** 매개 변수를 사용 하 여 `\Process(*)\% Processor Time` 로컬 컴퓨터의 모든 프로세스에 대 한 카운터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-214">`Get-Counter` uses the **Counter** parameter to specify the `\Process(*)\% Processor Time` counter for all the processes on the local computer.</span></span> <span data-ttu-id="79fef-215">결과는 변수에 저장 됩니다 `$Procs` .</span><span class="sxs-lookup"><span data-stu-id="79fef-215">The result is stored in the `$Procs` variable.</span></span> <span data-ttu-id="79fef-216">`$Procs` **Countersamples** 속성이 있는 변수는 **microsoft.powershell.commands.getcounter.performancecountersample** 개체를 파이프라인으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-216">The `$Procs` variable with the **CounterSamples** property sends the **PerformanceCounterSample** objects down the pipeline.</span></span> <span data-ttu-id="79fef-217">`Sort-Object`**Property** 매개 변수를 사용 하 여 **CookedValue** 를 기준으로 개체를 **내림차순** 으로 정렬 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-217">`Sort-Object` uses the **Property** parameter to sort the objects by **CookedValue** in **Descending** order.</span></span> <span data-ttu-id="79fef-218">`Format-Table`**Property** 매개 변수를 사용 하 여 출력에 대 한 열을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-218">`Format-Table` uses the **Property** parameter to select the columns for the output.</span></span> <span data-ttu-id="79fef-219">**AutoSize** 매개 변수는 잘림을 최소화 하도록 열 너비를 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-219">The **AutoSize** parameter adjusts the column widths to minimize truncation.</span></span>

## <span data-ttu-id="79fef-220">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="79fef-220">PARAMETERS</span></span>

### <span data-ttu-id="79fef-221">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="79fef-221">-ComputerName</span></span>

<span data-ttu-id="79fef-222">단일 컴퓨터 이름 또는 쉼표로 구분 된 **원격** 컴퓨터 이름 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-222">Specifies one computer name or a comma-separated array of **remote** computer names.</span></span> <span data-ttu-id="79fef-223">NetBIOS 이름, IP 주소 또는 컴퓨터의 정규화 된 도메인 이름을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-223">Use the NetBIOS name, an IP address, or the computer's fully qualified domain name.</span></span>

<span data-ttu-id="79fef-224">**로컬** 컴퓨터에서 성능 카운터 데이터를 가져오려면 **ComputerName** 매개 변수를 제외 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-224">To get performance counter data from the **local** computer, exclude the **ComputerName** parameter.</span></span>
<span data-ttu-id="79fef-225">**MachineName** 열을 포함 하는 **listset** 과 같은 출력의 경우 점 ( `.` )은 로컬 컴퓨터를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-225">For output such as a **ListSet** that contains the **MachineName** column, a dot (`.`) indicates the local computer.</span></span>

<span data-ttu-id="79fef-226">`Get-Counter` 은 PowerShell 원격을 사용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-226">`Get-Counter` doesn't rely on PowerShell remoting.</span></span> <span data-ttu-id="79fef-227">컴퓨터에서 원격 명령을 실행 하도록 구성 되지 않은 경우에도 **ComputerName** 매개 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-227">You can use the **ComputerName** parameter even if your computer isn't configured to run remote commands.</span></span>

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

### <span data-ttu-id="79fef-228">-Continuous</span><span class="sxs-lookup"><span data-stu-id="79fef-228">-Continuous</span></span>

<span data-ttu-id="79fef-229">**연속** 이 지정 된 경우 `Get-Counter` <kbd>ctrl</kbd>C를 누를 때까지 샘플을 가져옵니다 + <kbd></kbd>.</span><span class="sxs-lookup"><span data-stu-id="79fef-229">When the **Continuous** is specified, `Get-Counter` gets samples until you press <kbd>CTRL</kbd>+<kbd>C</kbd>.</span></span> <span data-ttu-id="79fef-230">지정 된 각 성능 카운터에 대해 매 초 마다 샘플이 얻어집니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-230">Samples are obtained every second for each specified performance counter.</span></span> <span data-ttu-id="79fef-231">연속 샘플 간 간격을 늘리려면 **SampleInterval** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-231">Use the **SampleInterval** parameter to increase the interval between continuous samples.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GetCounterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="79fef-232">-Counter</span><span class="sxs-lookup"><span data-stu-id="79fef-232">-Counter</span></span>

<span data-ttu-id="79fef-233">하나 이상의 카운터 경로에 대 한 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-233">Specifies the path to one or more counter paths.</span></span> <span data-ttu-id="79fef-234">경로는 쉼표로 구분 된 배열, 변수 또는 텍스트 파일의 값으로 입력 됩니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-234">Paths are input as a comma-separated array, a variable, or values from a text file.</span></span> <span data-ttu-id="79fef-235">파이프라인에서로 카운터 경로 문자열을 보낼 수 있습니다 `Get-Counter` .</span><span class="sxs-lookup"><span data-stu-id="79fef-235">You can send counter path strings down the pipeline to `Get-Counter`.</span></span>

<span data-ttu-id="79fef-236">카운터 경로는 다음 구문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-236">Counter paths use the following syntax:</span></span>

`\\ComputerName\CounterSet(Instance)\CounterName`

`\CounterSet(Instance)\CounterName`

<span data-ttu-id="79fef-237">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="79fef-237">For example:</span></span>

`\\Server01\Processor(*)\% User Time`

`\Processor(*)\% User Time`

<span data-ttu-id="79fef-238">는 `\\ComputerName` 성능 카운터 경로에서 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-238">The `\\ComputerName` is optional in a performance counter path.</span></span> <span data-ttu-id="79fef-239">카운터 경로에 컴퓨터 이름이 포함 되지 않은 경우는 `Get-Counter` 로컬 컴퓨터를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-239">If the counter path doesn't include the computer name, `Get-Counter` uses the local computer.</span></span>

<span data-ttu-id="79fef-240">인스턴스의 별표 ( `*` )는 카운터의 모든 인스턴스를 가져오기 위한 와일드 카드 문자입니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-240">An asterisk (`*`) in the instance is a wildcard character to get all instances of the counter.</span></span>

```yaml
Type: System.String[]
Parameter Sets: GetCounterSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="79fef-241">-ListSet</span><span class="sxs-lookup"><span data-stu-id="79fef-241">-ListSet</span></span>

<span data-ttu-id="79fef-242">컴퓨터에 대 한 성능 카운터 집합을 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-242">Lists the performance counter sets on the computers.</span></span> <span data-ttu-id="79fef-243">별표 ( `*` )를 사용 하 여 모든 카운터 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-243">Use an asterisk (`*`) to specify all counter sets.</span></span> <span data-ttu-id="79fef-244">이름 또는 쉼표로 구분 된 카운터 집합 이름 문자열을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-244">Enter one name or a comma-separated string of counter set names.</span></span> <span data-ttu-id="79fef-245">파이프라인에서 카운터 집합 이름을 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-245">You can send counter set names down the pipeline.</span></span>

<span data-ttu-id="79fef-246">카운터 집합 형식의 카운터 경로를 가져오려면 **Listset** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-246">To get a counter sets formatted counter paths, use the **ListSet** parameter.</span></span> <span data-ttu-id="79fef-247">각 카운터 집합의 **Paths** 및 **Pathswithinstances** 속성은 문자열로 형식이 지정 된 개별 카운터 경로를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-247">The **Paths** and **PathsWithInstances** properties of each counter set contain the individual counter paths formatted as a string.</span></span>

<span data-ttu-id="79fef-248">카운터 경로 문자열을 변수에 저장 하거나 파이프라인을 사용 하 여 문자열을 다른 명령으로 보낼 수 있습니다 `Get-Counter` .</span><span class="sxs-lookup"><span data-stu-id="79fef-248">You can save the counter path strings in a variable or use the pipeline to send the string to another `Get-Counter` command.</span></span>

<span data-ttu-id="79fef-249">예를 들어 각 **프로세서** 카운터 경로를로 보내려면 `Get-Counter` 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-249">For example to send each **Processor** counter path to `Get-Counter`:</span></span>

`Get-Counter -ListSet Processor | Get-Counter`

> [!NOTE]
> <span data-ttu-id="79fef-250">PowerShell 7에서 `Get-Counter` 카운터 집합의 **Description** 속성을 검색할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-250">In PowerShell 7, `Get-Counter` can't retrieve the **Description** property of the counter set.</span></span> <span data-ttu-id="79fef-251">**설명은** 로 설정 됩니다 `$null` .</span><span class="sxs-lookup"><span data-stu-id="79fef-251">The **Description** is set to `$null`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ListSetSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="79fef-252">-MaxSamples</span><span class="sxs-lookup"><span data-stu-id="79fef-252">-MaxSamples</span></span>

<span data-ttu-id="79fef-253">지정 된 각 성능 카운터에서 가져올 샘플 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-253">Specifies the number of samples to get from each specified performance counter.</span></span> <span data-ttu-id="79fef-254">샘플의 상수 스트림을 가져오려면 **연속** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-254">To get a constant stream of samples, use the **Continuous** parameter.</span></span>

<span data-ttu-id="79fef-255">**Maxsamples** 매개 변수를 지정 하지 않으면 `Get-Counter` 지정 된 각 카운터에 대해 하나의 샘플만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-255">If the **MaxSamples** parameter isn't specified, `Get-Counter` only gets one sample for each specified counter.</span></span>

<span data-ttu-id="79fef-256">대량 데이터 집합을 수집 하려면를 `Get-Counter` PowerShell 백그라운드 작업으로 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-256">To collect a large data set, run `Get-Counter` as a PowerShell background job.</span></span> <span data-ttu-id="79fef-257">자세한 내용은 [about_Jobs](../Microsoft.PowerShell.Core/About/about_Jobs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="79fef-257">For more information, see [about_Jobs](../Microsoft.PowerShell.Core/About/about_Jobs.md).</span></span>

```yaml
Type: System.Int64
Parameter Sets: GetCounterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="79fef-258">-SampleInterval</span><span class="sxs-lookup"><span data-stu-id="79fef-258">-SampleInterval</span></span>

<span data-ttu-id="79fef-259">지정 된 각 성능 카운터에 대 한 샘플 사이의 시간 (초)을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-259">Specifies the number of seconds between samples for each specified performance counter.</span></span> <span data-ttu-id="79fef-260">**SampleInterval** 매개 변수가 지정 되지 않은 경우는 `Get-Counter` 1 초 간격을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-260">If the **SampleInterval** parameter isn't specified, `Get-Counter` uses a one-second interval.</span></span>

```yaml
Type: System.Int32
Parameter Sets: GetCounterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="79fef-261">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="79fef-261">CommonParameters</span></span>

<span data-ttu-id="79fef-262">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="79fef-262">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="79fef-263">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="79fef-263">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="79fef-264">입력</span><span class="sxs-lookup"><span data-stu-id="79fef-264">INPUTS</span></span>

### <span data-ttu-id="79fef-265">System.String[]</span><span class="sxs-lookup"><span data-stu-id="79fef-265">System.String[]</span></span>

<span data-ttu-id="79fef-266">`Get-Counter` 카운터 경로 및 카운터 집합 이름에 대 한 파이프라인 입력을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-266">`Get-Counter` accepts pipeline input for counter paths and counter set names.</span></span>

## <span data-ttu-id="79fef-267">출력</span><span class="sxs-lookup"><span data-stu-id="79fef-267">OUTPUTS</span></span>

### <span data-ttu-id="79fef-268">PerformanceCounterSampleSet, Microsoft.powershell.commands.getcounter.performancecountersample,. m a. m a.. m a.. m a..</span><span class="sxs-lookup"><span data-stu-id="79fef-268">Microsoft.PowerShell.Commands.GetCounter.CounterSet, Microsoft.PowerShell.Commands.GetCounter.PerformanceCounterSampleSet, Microsoft.PowerShell.Commands.GetCounter.PerformanceCounterSample</span></span>

<span data-ttu-id="79fef-269">개체의 속성을 보려면 출력을 파이프라인에서로 보냅니다 `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="79fef-269">To view an object's properties, send the output down the pipeline to `Get-Member`.</span></span> <span data-ttu-id="79fef-270">출력 되는 개체 유형은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-270">The object types that are output are as follows:</span></span>

<span data-ttu-id="79fef-271">**Listset** 매개 변수: **Microsoft. PowerShell** .</span><span class="sxs-lookup"><span data-stu-id="79fef-271">**ListSet** parameter: **Microsoft.PowerShell.Commands.GetCounter.CounterSet**</span></span>

<span data-ttu-id="79fef-272">**Counter** 매개 변수: **PerformanceCounterSampleSet.**</span><span class="sxs-lookup"><span data-stu-id="79fef-272">**Counter** parameter: **Microsoft.PowerShell.Commands.GetCounter.PerformanceCounterSampleSet**</span></span>

<span data-ttu-id="79fef-273">**Countersamples** 속성은 **microsoft.powershell.commands.getcounter.performancecountersample** 입니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-273">**CounterSamples** property: **Microsoft.PowerShell.Commands.GetCounter.PerformanceCounterSample**</span></span>

## <span data-ttu-id="79fef-274">참고</span><span class="sxs-lookup"><span data-stu-id="79fef-274">NOTES</span></span>

<span data-ttu-id="79fef-275">매개 변수를 지정 하지 않으면 `Get-Counter` 지정 된 각 성능 카운터에 대해 하나의 샘플을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-275">If no parameters are specified, `Get-Counter` gets one sample for each specified performance counter.</span></span> <span data-ttu-id="79fef-276">**Maxsamples** 및 **연속** 매개 변수를 사용 하 여 더 많은 샘플을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-276">Use the **MaxSamples** and **Continuous** parameters to get more samples.</span></span>

<span data-ttu-id="79fef-277">`Get-Counter` 샘플 사이에 1 초 간격을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-277">`Get-Counter` uses a one-second interval between samples.</span></span> <span data-ttu-id="79fef-278">**SampleInterval** 매개 변수를 사용 하 여 간격을 늘립니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-278">Use the **SampleInterval** parameter to increase the interval.</span></span>

<span data-ttu-id="79fef-279">**Maxsamples** 및 **SampleInterval** 값은 명령에서 각 컴퓨터의 모든 카운터에 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-279">The **MaxSamples** and **SampleInterval** values apply to all the counters on each computer in the command.</span></span> <span data-ttu-id="79fef-280">다른 카운터에 대해 다른 값을 설정 하려면 별도의 `Get-Counter` 명령을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-280">To set different values for different counters, enter separate `Get-Counter` commands.</span></span>

<span data-ttu-id="79fef-281">PowerShell 7에서 **listset** 매개 변수를 사용 하는 경우에서 `Get-Counter` 카운터 집합의 **Description** 속성을 검색할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="79fef-281">In PowerShell 7, when using the **ListSet** parameter, `Get-Counter` can't retrieve the **Description** property of the counter set.</span></span> <span data-ttu-id="79fef-282">**설명은** 로 설정 됩니다 `$null` .</span><span class="sxs-lookup"><span data-stu-id="79fef-282">The **Description** is set to `$null`.</span></span>

## <span data-ttu-id="79fef-283">관련 링크</span><span class="sxs-lookup"><span data-stu-id="79fef-283">RELATED LINKS</span></span>

[<span data-ttu-id="79fef-284">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="79fef-284">about_Automatic_Variables</span></span>](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

[<span data-ttu-id="79fef-285">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="79fef-285">about_Jobs</span></span>](../Microsoft.PowerShell.Core/About/about_Jobs.md)

[<span data-ttu-id="79fef-286">Format-List</span><span class="sxs-lookup"><span data-stu-id="79fef-286">Format-List</span></span>](../Microsoft.PowerShell.Utility/Format-List.md)

[<span data-ttu-id="79fef-287">Format-Table</span><span class="sxs-lookup"><span data-stu-id="79fef-287">Format-Table</span></span>](../Microsoft.PowerShell.Utility/Format-Table.md)

[<span data-ttu-id="79fef-288">Get-Member</span><span class="sxs-lookup"><span data-stu-id="79fef-288">Get-Member</span></span>](../Microsoft.PowerShell.Utility/Get-Member.md)

[<span data-ttu-id="79fef-289">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="79fef-289">Receive-Job</span></span>](../Microsoft.PowerShell.Core/Receive-Job.md)

[<span data-ttu-id="79fef-290">Start-Job</span><span class="sxs-lookup"><span data-stu-id="79fef-290">Start-Job</span></span>](../Microsoft.PowerShell.Core/Start-Job.md)

[<span data-ttu-id="79fef-291">Where-Object</span><span class="sxs-lookup"><span data-stu-id="79fef-291">Where-Object</span></span>](..//Microsoft.PowerShell.Core/Where-Object.md)

