---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/sort-object?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Sort-Object
ms.openlocfilehash: 2a8e3aada4afc1cffa85db4df6bd5f559bdc80b4
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/10/2020
ms.locfileid: "93219458"
---
# <span data-ttu-id="c70a2-103">Sort-Object</span><span class="sxs-lookup"><span data-stu-id="c70a2-103">Sort-Object</span></span>

## <span data-ttu-id="c70a2-104">개요</span><span class="sxs-lookup"><span data-stu-id="c70a2-104">SYNOPSIS</span></span>
<span data-ttu-id="c70a2-105">속성 값에 따라 개체를 정렬합니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-105">Sorts objects by property values.</span></span>

## <span data-ttu-id="c70a2-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c70a2-106">SYNTAX</span></span>

### <span data-ttu-id="c70a2-107">Default (기본값)</span><span class="sxs-lookup"><span data-stu-id="c70a2-107">Default (Default)</span></span>

```
Sort-Object [-Stable] [-Descending] [-Unique] [-InputObject <PSObject>] [[-Property] <Object[]>]
 [-Culture <String>] [-CaseSensitive] [<CommonParameters>]
```

### <span data-ttu-id="c70a2-108">상위</span><span class="sxs-lookup"><span data-stu-id="c70a2-108">Top</span></span>

```
Sort-Object [-Descending] [-Unique] -Top <Int32> [-InputObject <PSObject>] [[-Property] <Object[]>]
 [-Culture <String>] [-CaseSensitive] [<CommonParameters>]
```

### <span data-ttu-id="c70a2-109">아래쪽</span><span class="sxs-lookup"><span data-stu-id="c70a2-109">Bottom</span></span>

```
Sort-Object [-Descending] [-Unique] -Bottom <Int32> [-InputObject <PSObject>] [[-Property] <Object[]>]
 [-Culture <String>] [-CaseSensitive] [<CommonParameters>]
```

## <span data-ttu-id="c70a2-110">설명</span><span class="sxs-lookup"><span data-stu-id="c70a2-110">DESCRIPTION</span></span>

<span data-ttu-id="c70a2-111">`Sort-Object`Cmdlet은 개체 속성 값을 기준으로 개체를 오름차순 또는 내림차순으로 정렬 합니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-111">The `Sort-Object` cmdlet sorts objects in ascending or descending order based on object property values.</span></span> <span data-ttu-id="c70a2-112">명령에 정렬 속성이 포함 되지 않은 경우 PowerShell은 첫 번째 입력 개체의 기본 정렬 속성을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-112">If sort properties are not included in a command, PowerShell uses default sort properties of the first input object.</span></span> <span data-ttu-id="c70a2-113">입력 개체의 형식에 기본 정렬 속성이 없으면 PowerShell에서 개체 자체를 비교 하려고 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-113">If the type of the input object has no default sort properties, PowerShell attempts to compare the objects themselves.</span></span> <span data-ttu-id="c70a2-114">자세한 내용은 [참고](#notes) 섹션을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c70a2-114">For more information, see the [Notes](#notes) section.</span></span>

<span data-ttu-id="c70a2-115">단일 속성 또는 여러 속성을 기준으로 개체를 정렬할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-115">You can sort objects by a single property or multiple properties.</span></span> <span data-ttu-id="c70a2-116">여러 속성은 해시 테이블을 사용 하 여 오름차순, 내림차순 또는 정렬 주문의 조합을 정렬 합니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-116">Multiple properties use hash tables to sort in ascending order, descending order, or a combination of sort orders.</span></span> <span data-ttu-id="c70a2-117">속성이 대/소문자를 구분 하거나 대/소문자를 구분 하지 않고 정렬 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-117">Properties are sorted as case-sensitive or case-insensitive.</span></span> <span data-ttu-id="c70a2-118">**Unique** 매개 변수를 사용 하 여 출력에서 중복 항목을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-118">Use the **Unique** parameter to eliminate duplicates from the output.</span></span>

## <span data-ttu-id="c70a2-119">예제</span><span class="sxs-lookup"><span data-stu-id="c70a2-119">EXAMPLES</span></span>

### <span data-ttu-id="c70a2-120">예제 1: 이름을 기준으로 현재 디렉터리 정렬</span><span class="sxs-lookup"><span data-stu-id="c70a2-120">Example 1: Sort the current directory by name</span></span>

<span data-ttu-id="c70a2-121">이 예에서는 디렉터리의 파일 및 하위 디렉터리를 정렬 합니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-121">This example sorts the files and subdirectories in a directory.</span></span>

```
PS> Get-ChildItem -Path C:\Test | Sort-Object

    Directory: C:\Test

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/13/2019     08:55             26 anotherfile.txt
-a----        2/13/2019     13:26             20 Bfile.txt
-a----        2/12/2019     15:40         118014 Command.txt
-a----         2/1/2019     08:43            183 CreateTestFile.ps1
d-----        2/25/2019     18:25                Files
d-----        2/25/2019     18:24                Logs
-ar---        2/12/2019     14:31             27 ReadOnlyFile.txt
-a----        2/12/2019     16:24             23 Zsystemlog.log
```

<span data-ttu-id="c70a2-122">`Get-ChildItem`Cmdlet은 **Path** 매개 변수 **C:\Test** 로 지정 된 디렉터리에서 파일 및 하위 디렉터리를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-122">The `Get-ChildItem` cmdlet gets the files and subdirectories from the directory specified by the **Path** parameter, **C:\Test**.</span></span> <span data-ttu-id="c70a2-123">개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Sort-Object` .</span><span class="sxs-lookup"><span data-stu-id="c70a2-123">The objects are sent down the pipeline to the `Sort-Object` cmdlet.</span></span>
<span data-ttu-id="c70a2-124">`Sort-Object` 는 속성을 지정 하지 않으므로 출력은 기본 정렬 속성인 **Name** 을 기준으로 정렬 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-124">`Sort-Object` does not specify a property so the output is sorted by the default sort property, **Name**.</span></span>

### <span data-ttu-id="c70a2-125">예제 2: 파일 길이를 기준으로 현재 디렉터리 정렬</span><span class="sxs-lookup"><span data-stu-id="c70a2-125">Example 2: Sort the current directory by file length</span></span>

<span data-ttu-id="c70a2-126">이 명령은 현재 디렉터리의 파일 길이를 오름차순으로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-126">This command displays the files in the current directory by length in ascending order.</span></span>

```
PS> Get-ChildItem -Path C:\Test -File | Sort-Object -Property Length

    Directory: C:\Test

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/13/2019     13:26             20 Bfile.txt
-a----        2/12/2019     16:24             23 Zsystemlog.log
-a----        2/13/2019     08:55             26 anotherfile.txt
-ar---        2/12/2019     14:31             27 ReadOnlyFile.txt
-a----         2/1/2019     08:43            183 CreateTestFile.ps1
-a----        2/12/2019     15:40         118014 Command.txt
```

<span data-ttu-id="c70a2-127">`Get-ChildItem`Cmdlet은 **Path** 매개 변수로 지정 된 디렉터리에서 파일을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-127">The `Get-ChildItem` cmdlet gets the files from the directory specified by the **Path** parameter.</span></span>
<span data-ttu-id="c70a2-128">**File** 매개 변수는에서 파일 개체만을 가져오기로 지정 합니다 `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="c70a2-128">The **File** parameter specifies that `Get-ChildItem` only gets file objects.</span></span> <span data-ttu-id="c70a2-129">개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Sort-Object` .</span><span class="sxs-lookup"><span data-stu-id="c70a2-129">The objects are sent down the pipeline to the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="c70a2-130">`Sort-Object`**길이** 매개 변수를 사용 하 여 파일을 오름차순으로 정렬 합니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-130">`Sort-Object` uses the **Length** parameter to sort the files by length in ascending order.</span></span>

### <span data-ttu-id="c70a2-131">예제 3: 메모리 사용량을 기준으로 프로세스 정렬</span><span class="sxs-lookup"><span data-stu-id="c70a2-131">Example 3: Sort processes by memory usage</span></span>

<span data-ttu-id="c70a2-132">이 예제에서는 WS (작업 집합) 크기를 기준으로 메모리 사용량이 가장 높은 프로세스를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-132">This example displays processes with the highest memory usage based on their working set (WS) size.</span></span>

```
PS> Get-Process | Sort-Object -Property WS | Select-Object -Last 5

 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
    136   193.92     217.11     889.16   87492   8 OUTLOOK
    112   347.73     297.02      95.19  106908   8 Teams
    206   266.54     323.71      37.17   60620   8 MicrosoftEdgeCP
     35   552.19     549.94     131.66    6552   8 Code
      0     1.43     595.12       0.00    2780   0 Memory Compression
```

<span data-ttu-id="c70a2-133">`Get-Process`Cmdlet은 컴퓨터에서 실행 중인 프로세스 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-133">The `Get-Process` cmdlet gets the list of processes running on the computer.</span></span> <span data-ttu-id="c70a2-134">프로세스 개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Sort-Object` .</span><span class="sxs-lookup"><span data-stu-id="c70a2-134">The process objects are sent down the pipeline to the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="c70a2-135">`Sort-Object`**Property** 매개 변수를 사용 하 여 **WS** 를 기준으로 개체를 정렬 합니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-135">`Sort-Object` uses the **Property** parameter to sort the objects by **WS**.</span></span> <span data-ttu-id="c70a2-136">개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="c70a2-136">The objects are sent down the pipeline to the `Select-Object` cmdlet.</span></span>
<span data-ttu-id="c70a2-137">`Select-Object`**마지막** 매개 변수를 사용 하 여 가장 높은 **WS** 사용을 가진 개체인 마지막 5 개 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-137">`Select-Object` uses the **Last** parameter to specify the last five objects, which are the objects with the highest **WS** usage.</span></span>

<span data-ttu-id="c70a2-138">PowerShell 6에서 `Sort-Object` **아래쪽** 매개 변수는 대신 사용할 수 `Select-Object` 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-138">In PowerShell 6, the `Sort-Object` parameter **Bottom** is an alternative to `Select-Object`.</span></span> <span data-ttu-id="c70a2-139">예들 들어 `Get-Process | Sort-Object -Property WS -Bottom 5`입니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-139">For example, `Get-Process | Sort-Object -Property WS -Bottom 5`.</span></span>

### <span data-ttu-id="c70a2-140">예제 4: Id 별 HistoryInfo 개체 정렬</span><span class="sxs-lookup"><span data-stu-id="c70a2-140">Example 4: Sort HistoryInfo objects by Id</span></span>

<span data-ttu-id="c70a2-141">이 명령은 **Id** 속성을 사용 하 여 PowerShell 세션의 **HistoryInfo** 개체를 정렬 합니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-141">This command sorts the PowerShell session's **HistoryInfo** objects using the **Id** property.</span></span> <span data-ttu-id="c70a2-142">각 PowerShell 세션에는 자체 명령 기록이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-142">Each PowerShell session has its own command history.</span></span>

```
PS> Get-History | Sort-Object -Property Id -Descending

  Id CommandLine
  -- -----------
  10 Get-Command Sort-Object -Syntax
   9 $PSVersionTable
   8 Get-Command Sort-Object -Syntax
   7 Get-Command Sort-Object -ShowCommandInfo
   6 Get-ChildItem -Path C:\Test | Sort-Object -Property Length
   5 Get-Help Clear-History -online
   4 Get-Help Clear-History -full
   3 Get-ChildItem | Get-Member
   2 Get-Command Sort-Object -Syntax
   1 Set-Location C:\Test\
```

<span data-ttu-id="c70a2-143">`Get-History`Cmdlet은 현재 PowerShell 세션에서 기록 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-143">The `Get-History` cmdlet gets the history objects from the current PowerShell session.</span></span> <span data-ttu-id="c70a2-144">개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Sort-Object` .</span><span class="sxs-lookup"><span data-stu-id="c70a2-144">The objects are sent down the pipeline to the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="c70a2-145">`Sort-Object`**Property** 매개 변수를 사용 하 여 **Id** 를 기준으로 개체를 정렬 합니다. **내림차순** 매개 변수는 명령 기록을 최신에서 가장 오래 된 순서로 정렬 합니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-145">`Sort-Object` uses the **Property** parameter to sort the objects by **Id**. The **Descending** parameter sorts the command history from newest to oldest.</span></span>

### <span data-ttu-id="c70a2-146">예 5: 해시 테이블을 사용 하 여 속성을 오름차순 및 내림차순으로 정렬</span><span class="sxs-lookup"><span data-stu-id="c70a2-146">Example 5: Use a hash table to sort properties in ascending and descending order</span></span>

<span data-ttu-id="c70a2-147">이 예제에서는 두 가지 속성을 사용 하 여 개체, **상태** 및 **DisplayName** 을 정렬 합니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-147">This example uses two properties to sort the objects, **Status** and **DisplayName**.</span></span> <span data-ttu-id="c70a2-148">**상태** 는 내림차순으로 정렬 되 고 **DisplayName** 은 오름차순으로 정렬 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-148">**Status** is sorted in descending order and **DisplayName** is sorted in ascending order.</span></span>

<span data-ttu-id="c70a2-149">해시 테이블은 **속성** 매개 변수의 값을 지정 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-149">A hash table is used to specify the **Property** parameter's value.</span></span> <span data-ttu-id="c70a2-150">해시 테이블은 식을 사용 하 여 속성 이름과 정렬 순서를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-150">The hash table uses an expression to specify the property names and sort orders.</span></span> <span data-ttu-id="c70a2-151">해시 테이블에 대한 자세한 내용은 [about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c70a2-151">For more information about hash tables, see [about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md).</span></span>

<span data-ttu-id="c70a2-152">해시 테이블에 사용 되는 **Status** 속성은 열거 된 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-152">The **Status** property used in the hash table is an enumerated property.</span></span>
<span data-ttu-id="c70a2-153">자세한 내용은 [ServiceControllerStatus](/dotnet/api/system.serviceprocess.servicecontrollerstatus)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c70a2-153">For more information, see [ServiceControllerStatus](/dotnet/api/system.serviceprocess.servicecontrollerstatus).</span></span>

```
PS C:\> Get-Service | Sort-Object -Property @{Expression = "Status"; Descending = $True}, @{Expression = "DisplayName"; Descending = $False}

Status   Name               DisplayName
------   ----               -----------
Running  Appinfo            Application Information
Running  BthAvctpSvc        AVCTP service
Running  BrokerInfrastru... Background Tasks Infrastructure Ser...
Running  BDESVC             BitLocker Drive Encryption Service
Running  CoreMessagingRe... CoreMessaging
Running  VaultSvc           Credential Manager
Running  DsSvc              Data Sharing Service
Running  Dhcp               DHCP Client
...
Stopped  ALG                Application Layer Gateway Service
Stopped  AppMgmt            Application Management
Stopped  BITS               Background Intelligent Transfer Ser...
Stopped  wbengine           Block Level Backup Engine Service
Stopped  BluetoothUserSe... Bluetooth User Support Service_14fb...
Stopped  COMSysApp          COM+ System Application
Stopped  smstsmgr           ConfigMgr Task Sequence Agent
Stopped  DeviceInstall      Device Install Service
Stopped  MSDTC              Distributed Transaction Coordinator
```

<span data-ttu-id="c70a2-154">`Get-Service`Cmdlet은 컴퓨터의 서비스 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-154">The `Get-Service` cmdlet gets the list of services on the computer.</span></span> <span data-ttu-id="c70a2-155">Service 개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Sort-Object` .</span><span class="sxs-lookup"><span data-stu-id="c70a2-155">The service objects are sent down the pipeline to the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="c70a2-156">`Sort-Object`**property 매개 변수** 를 해시 테이블에 사용 하 여 속성 이름과 정렬 순서를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-156">`Sort-Object` uses the **Property** parameter with a hash table to specify the property names and sort orders.</span></span> <span data-ttu-id="c70a2-157">**Property** 매개 변수는 **상태** 를 내림차순으로, **DisplayName** 을 오름차순으로 정렬 하 여 두 개의 속성을 기준으로 정렬 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-157">The **Property** parameter is sorted by two properties, **Status** in descending order and **DisplayName** in ascending order.</span></span>

<span data-ttu-id="c70a2-158">**Status** 는 열거 된 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-158">**Status** is an enumerated property.</span></span> <span data-ttu-id="c70a2-159">**중지 됨** 의 값은 **1** 이 고 **실행** 값은 **4** 입니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-159">**Stopped** has a value of **1** and **Running** has a value of **4**.</span></span> <span data-ttu-id="c70a2-160">중지 **Descending** 된 `$True` 프로세스 전에 **실행 중인** 프로세스가 표시 되도록 내림차순 매개 변수가로 **Stopped** 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-160">The **Descending** parameter is set to `$True` so that **Running** processes are displayed before **Stopped** processes.</span></span> <span data-ttu-id="c70a2-161">**DisplayName** 은 **내림차순** 매개 변수를로 설정 `$False` 하 여 표시 이름을 알파벳 순서로 정렬 합니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-161">**DisplayName** sets the **Descending** parameter to `$False` to sort the display names in alphabetical order.</span></span>

### <span data-ttu-id="c70a2-162">예제 6: 시간 범위를 기준으로 텍스트 파일 정렬</span><span class="sxs-lookup"><span data-stu-id="c70a2-162">Example 6: Sort text files by time span</span></span>

<span data-ttu-id="c70a2-163">이 명령은 **CreationTime** 와 **LastWriteTime** 사이의 시간 간격에 따라 텍스트 파일을 내림차순으로 정렬 합니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-163">This command sorts text files in descending order by the time span between **CreationTime** and **LastWriteTime**.</span></span>

```
PS> Get-ChildItem -Path C:\Test\*.txt | Sort-Object -Property @{Expression = {$_.CreationTime - $_.LastWriteTime}; Descending = $False} | Format-Table CreationTime, LastWriteTime, FullName

CreationTime          LastWriteTime        FullName
------------          -------------        --------
11/21/2018 12:39:01   2/26/2019 08:59:36   C:\Test\test2.txt
12/4/2018 08:29:41    2/26/2019 08:57:05   C:\Test\powershell_list.txt
2/20/2019 08:15:59    2/26/2019 12:09:43   C:\Test\CreateTestFile.txt
2/20/2019 08:15:59    2/26/2019 12:07:41   C:\Test\Command.txt
2/20/2019 08:15:59    2/26/2019 08:57:52   C:\Test\ReadOnlyFile.txt
11/29/2018 15:16:50   12/4/2018 16:16:24   C:\Test\LogData.txt
2/25/2019 18:25:11    2/26/2019 12:08:47   C:\Test\Zsystemlog.txt
2/25/2019 18:25:11    2/26/2019 08:55:33   C:\Test\Bfile.txt
2/26/2019 08:46:59    2/26/2019 12:12:19   C:\Test\LogFile3.txt
```

<span data-ttu-id="c70a2-164">`Get-ChildItem`Cmdlet은 **Path** 매개 변수를 사용 하 여 **C:\Test** 및 모든 파일 디렉터리를 지정 합니다 `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="c70a2-164">The `Get-ChildItem` cmdlet uses the **Path** parameter to specify the directory **C:\Test** and all of the `*.txt` files.</span></span> <span data-ttu-id="c70a2-165">개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Sort-Object` .</span><span class="sxs-lookup"><span data-stu-id="c70a2-165">The objects are sent down the pipeline to the `Sort-Object` cmdlet.</span></span>
<span data-ttu-id="c70a2-166">`Sort-Object` 는 해시 테이블에 **Property** 매개 변수를 사용 하 여 **CreationTime** 와 **LastWriteTime** 사이의 각 파일 시간 범위를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-166">`Sort-Object` uses the **Property** parameter with a hash table to determine each files time span between **CreationTime** and **LastWriteTime**.</span></span> <span data-ttu-id="c70a2-167">**내림차순** 매개 변수가로 설정 되어 가장 `$False` 긴 시간 범위에서 가장 짧은 시간 범위 순으로 정렬 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-167">The **Descending** parameter is set to `$False` to sort in the order of longest to shortest time span.</span></span>

### <span data-ttu-id="c70a2-168">예 7: 텍스트 파일에서 이름 정렬</span><span class="sxs-lookup"><span data-stu-id="c70a2-168">Example 7: Sort names in a text file</span></span>

<span data-ttu-id="c70a2-169">이 예제에서는 텍스트 파일에서 목록을 정렬 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-169">This example shows how to sort a list from a text file.</span></span> <span data-ttu-id="c70a2-170">원본 파일은 정렬 되지 않은 목록으로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-170">The original file is displayed as an unsorted list.</span></span> <span data-ttu-id="c70a2-171">`Sort-Object` 내용을 정렬 하 고 중복 항목을 제거 하는 **고유한** 매개 변수를 사용 하 여 내용을 정렬 합니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-171">`Sort-Object` sorts the contents and then sorts the contents with the **Unique** parameter that removes duplicates.</span></span>

```
PS> Get-Content -Path C:\Test\ServerNames.txt
localhost
server01
server25
LOCALHOST
Server19
server3
localhost

PS> Get-Content -Path C:\Test\ServerNames.txt | Sort-Object
localhost
LOCALHOST
localhost
server01
Server19
server25
server3

PS> Get-Content -Path C:\Test\ServerNames.txt | Sort-Object -Unique
localhost
server01
Server19
server25
server3
```

<span data-ttu-id="c70a2-172">`Get-Content`Cmdlet은 **Path** 매개 변수를 사용 하 여 디렉터리 및 파일 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-172">The `Get-Content` cmdlet uses the **Path** parameter to specify the directory and file name.</span></span> <span data-ttu-id="c70a2-173">파일 **ServerNames.txt** 에는 정렬 되지 않은 컴퓨터 이름 목록이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-173">The file **ServerNames.txt** contains an unsorted list of computer names.</span></span>

<span data-ttu-id="c70a2-174">`Get-Content`Cmdlet은 **Path** 매개 변수를 사용 하 여 디렉터리 및 파일 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-174">The `Get-Content` cmdlet uses the **Path** parameter to specify the directory and file name.</span></span> <span data-ttu-id="c70a2-175">파일 **ServerNames.txt** 에는 정렬 되지 않은 컴퓨터 이름 목록이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-175">The file **ServerNames.txt** contains an unsorted list of computer names.</span></span> <span data-ttu-id="c70a2-176">개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Sort-Object` .</span><span class="sxs-lookup"><span data-stu-id="c70a2-176">The objects are sent down the pipeline to the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="c70a2-177">`Sort-Object` 목록을 기본 순서 오름차순으로 정렬 합니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-177">`Sort-Object` sorts the list in the default order, ascending.</span></span>

<span data-ttu-id="c70a2-178">`Get-Content`Cmdlet은 **Path** 매개 변수를 사용 하 여 디렉터리 및 파일 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-178">The `Get-Content` cmdlet uses the **Path** parameter to specify the directory and file name.</span></span> <span data-ttu-id="c70a2-179">파일 **ServerNames.txt** 에는 정렬 되지 않은 컴퓨터 이름 목록이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-179">The file **ServerNames.txt** contains an unsorted list of computer names.</span></span> <span data-ttu-id="c70a2-180">개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Sort-Object` .</span><span class="sxs-lookup"><span data-stu-id="c70a2-180">The objects are sent down the pipeline to the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="c70a2-181">`Sort-Object`**Unique** 매개 변수를 사용 하 여 중복 된 컴퓨터 이름을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-181">`Sort-Object` uses the **Unique** parameter to remove duplicate computer names.</span></span> <span data-ttu-id="c70a2-182">목록은 기본 순서 오름차순으로 정렬 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-182">The list is sorted in the default order, ascending.</span></span>

### <span data-ttu-id="c70a2-183">예 8: 문자열을 정수로 정렬</span><span class="sxs-lookup"><span data-stu-id="c70a2-183">Example 8: Sort a string as an integer</span></span>

<span data-ttu-id="c70a2-184">이 예제에서는 문자열 개체를 포함 하는 텍스트 파일을 정수로 정렬 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-184">This example shows how to sort a text file that contains string objects as integers.</span></span> <span data-ttu-id="c70a2-185">각 명령을 파이프라인에서로 보내고 `Get-Member` 개체가 정수 대신 문자열 인지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-185">You can send each command down the pipeline to `Get-Member` and verify that the objects are strings instead of integers.</span></span> <span data-ttu-id="c70a2-186">이러한 예제에서 파일에는 `ProductId.txt` 정렬 되지 않은 제품 번호 목록이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-186">For these examples, the `ProductId.txt` file contains an unsorted list of product numbers.</span></span>

<span data-ttu-id="c70a2-187">첫 번째 예제에서 `Get-Content` 파일의 내용을 가져오고 해당 줄을 cmdlet으로 파이프 합니다 `Sort-Object` .</span><span class="sxs-lookup"><span data-stu-id="c70a2-187">In the first example, `Get-Content` gets the contents of the file and pipes lines to the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="c70a2-188">`Sort-Object` 문자열 개체를 오름차순으로 정렬 합니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-188">`Sort-Object` sorts the string objects in ascending order.</span></span>

```
PS> Get-Content -Path C:\Test\ProductId.txt | Sort-Object
0
1
12345
1500
2
2800
3500
4100
500
6200
77
88
99999

PS> Get-Content -Path C:\Test\ProductId.txt | Sort-Object {[int]$_}
0
1
2
77
88
500
1500
2800
3500
4100
6200
12345
99999
```

<span data-ttu-id="c70a2-189">두 번째 예제에서는 `Get-Content` 파일의 내용을 가져오고이를 cmdlet으로 파이프 합니다 `Sort-Object` .</span><span class="sxs-lookup"><span data-stu-id="c70a2-189">In the second example, `Get-Content` gets the contents of the file and pipes lines to the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="c70a2-190">`Sort-Object` 는 스크립트 블록을 사용 하 여 문자열을 정수로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-190">`Sort-Object` uses a script block to convert the strings to integers.</span></span> <span data-ttu-id="c70a2-191">샘플 코드에서는 `[int]` 문자열을 정수로 변환 하 고 `$_` 파이프라인에서 제공 되는 각 문자열을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-191">In the sample code, `[int]` converts the string to an integer and `$_` represents each string as it comes down the pipeline.</span></span> <span data-ttu-id="c70a2-192">정수 개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Sort-Object` .</span><span class="sxs-lookup"><span data-stu-id="c70a2-192">The integer objects are sent down the pipeline to the `Sort-Object` cmdlet.</span></span>
<span data-ttu-id="c70a2-193">`Sort-Object` 정수 개체를 숫자 순서로 정렬 합니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-193">`Sort-Object` sorts the integer objects in numeric order.</span></span>

### <span data-ttu-id="c70a2-194">예 9: 안정적인 정렬 사용</span><span class="sxs-lookup"><span data-stu-id="c70a2-194">Example 9: Using stable sorts</span></span>

<span data-ttu-id="c70a2-195">**Top** , **Bottom** 또는 **안정** 된 매개 변수를 사용할 경우 정렬 된 개체는 `Sort-Object` 정렬 기준이 같을 때에서 받은 순서 대로 배달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-195">When you use the **Top** , **Bottom** , or **Stable** parameters, the sorted objects are delivered in the order they were received by `Sort-Object` when the sort criteria are equal.</span></span> <span data-ttu-id="c70a2-196">이 예제에서는 값 ' 모듈로 3 '을 기준으로 1부터 20 까지의 숫자를 정렬 합니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-196">In this example, we are sorting the numbers one through 20 by the their value 'modulo 3'.</span></span> <span data-ttu-id="c70a2-197">모듈로 값의 범위는 0에서 2 사이입니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-197">The modulo value ranges from zero to two.</span></span>

```powershell
PS> 1..20 |Sort-Object {$_ % 3}
18
3
15
6
12
9
1
16
13
10
7
4
19
11
8
14
5
17
2
20

PS> 1..20 |Sort-Object {$_ % 3} -Stable
3
6
9
12
15
18
1
4
7
10
13
16
19
2
5
8
11
14
17
20
```

<span data-ttu-id="c70a2-198">첫 번째 정렬의 출력은 모듈러스 값에 의해 올바르게 그룹화 되지만 개별 항목은 모듈러스 범위 내에서 정렬 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-198">The output from the first sort is correctly grouped by the modulus value but the individual items are not sorted within the modulus range.</span></span> <span data-ttu-id="c70a2-199">두 번째 정렬은 **안정** 된 옵션을 사용 하 여 안정적인 정렬을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-199">The second sort uses the **Stable** option to return a stable sort.</span></span>

## <span data-ttu-id="c70a2-200">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c70a2-200">PARAMETERS</span></span>

### <span data-ttu-id="c70a2-201">-아래쪽</span><span class="sxs-lookup"><span data-stu-id="c70a2-201">-Bottom</span></span>

<span data-ttu-id="c70a2-202">정렬 된 개체 배열의 끝에서 가져올 개체 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-202">Specifies the number of objects to get from the end of a sorted object array.</span></span> <span data-ttu-id="c70a2-203">이로 인해 안정적으로 정렬 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-203">This results in a stable sort.</span></span>

<span data-ttu-id="c70a2-204">이 매개 변수는 PowerShell 6.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-204">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: Bottom
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c70a2-205">-CaseSensitive</span><span class="sxs-lookup"><span data-stu-id="c70a2-205">-CaseSensitive</span></span>

<span data-ttu-id="c70a2-206">정렬에서 대/소문자를 구분 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-206">Indicates that the sort is case-sensitive.</span></span> <span data-ttu-id="c70a2-207">기본적으로 정렬은 대/소문자를 구분 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-207">By default, sorts are not case-sensitive.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Case-insensitive
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c70a2-208">-문화권</span><span class="sxs-lookup"><span data-stu-id="c70a2-208">-Culture</span></span>

<span data-ttu-id="c70a2-209">정렬에 사용할 문화권 구성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-209">Specifies the cultural configuration to use for sorts.</span></span> <span data-ttu-id="c70a2-210">`Get-Culture`를 사용 하 여 시스템의 문화권 구성을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-210">Use `Get-Culture` to display the system's culture configuration.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c70a2-211">-내림차순</span><span class="sxs-lookup"><span data-stu-id="c70a2-211">-Descending</span></span>

<span data-ttu-id="c70a2-212">`Sort-Object`에서 개체를 내림차순으로 정렬 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-212">Indicates that `Sort-Object` sorts the objects in descending order.</span></span> <span data-ttu-id="c70a2-213">기본값은 오름차순입니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-213">The default is ascending order.</span></span>

<span data-ttu-id="c70a2-214">여러 정렬 순서를 사용 하 여 여러 속성을 정렬 하려면 해시 테이블을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-214">To sort multiple properties with different sort orders, use a hash table.</span></span> <span data-ttu-id="c70a2-215">예를 들어 해시 테이블을 사용 하면 한 속성을 오름차순으로 정렬 하 고 다른 속성은 내림차순으로 정렬할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-215">For example, with a hash table you can sort one property in ascending order and another property in descending order.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Ascending
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c70a2-216">-InputObject</span><span class="sxs-lookup"><span data-stu-id="c70a2-216">-InputObject</span></span>

<span data-ttu-id="c70a2-217">개체를 정렬 하려면 파이프라인에서로 보냅니다 `Sort-Object` .</span><span class="sxs-lookup"><span data-stu-id="c70a2-217">To sort objects, send them down the pipeline to `Sort-Object`.</span></span> <span data-ttu-id="c70a2-218">**InputObject** 매개 변수를 사용 하 여 항목 컬렉션을 전송 하는 경우는 `Sort-Object` 컬렉션을 나타내는 개체 하나를 수신 합니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-218">If you use the **InputObject** parameter to submit a collection of items, `Sort-Object` receives one object that represents the collection.</span></span> <span data-ttu-id="c70a2-219">하나의 개체를 정렬할 수 없기 때문에에서 `Sort-Object` 전체 컬렉션을 변경 하지 않고 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-219">Because one object cannot be sorted, `Sort-Object` returns the entire collection unchanged.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="c70a2-220">-속성</span><span class="sxs-lookup"><span data-stu-id="c70a2-220">-Property</span></span>

<span data-ttu-id="c70a2-221">`Sort-Object`에서 개체를 정렬 하는 데 사용 하는 속성 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-221">Specifies the property names that `Sort-Object` uses to sort the objects.</span></span> <span data-ttu-id="c70a2-222">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-222">Wildcards are permitted.</span></span>
<span data-ttu-id="c70a2-223">개체는 속성 값을 기준으로 정렬 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-223">Objects are sorted based on the property values.</span></span> <span data-ttu-id="c70a2-224">속성을 지정 하지 않을 경우는 `Sort-Object` 개체 형식 또는 개체 자체에 대 한 기본 속성을 기준으로 정렬 합니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-224">If you do not specify a property, `Sort-Object` sorts based on default properties for the object type or the objects themselves.</span></span>

<span data-ttu-id="c70a2-225">여러 속성을 오름차순, 내림차순 또는 정렬 순서의 조합으로 정렬할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-225">Multiple properties can be sorted in ascending order, descending order, or a combination of sort orders.</span></span> <span data-ttu-id="c70a2-226">여러 속성을 지정 하는 경우 개체는 첫 번째 속성을 기준으로 정렬 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-226">When you specify multiple properties, the objects are sorted by the first property.</span></span> <span data-ttu-id="c70a2-227">여러 개체가 첫 번째 속성에 대해 동일한 값을 가지는 경우 해당 개체는 두 번째 속성에 따라 정렬 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-227">If multiple objects have the same value for the first property, those objects are sorted by the second property.</span></span> <span data-ttu-id="c70a2-228">지정된 속성이나 개체 그룹이 더 이상 없을 때까지 이 프로세스가 계속됩니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-228">This process continues until there are no more specified properties or no groups of objects.</span></span>

<span data-ttu-id="c70a2-229">**속성** 매개 변수의 값은 계산 된 속성 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-229">The **Property** parameter's value can be a calculated property.</span></span> <span data-ttu-id="c70a2-230">계산된 속성을 만들려면 해시 테이블을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="c70a2-230">To create a calculated property, use a hash table.</span></span>

<span data-ttu-id="c70a2-231">해시 테이블에 대 한 유효한 키는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-231">Valid keys for a hash table are as follows:</span></span>

- <span data-ttu-id="c70a2-232">`expression` - `<string>` 또는 `<script block>`</span><span class="sxs-lookup"><span data-stu-id="c70a2-232">`expression` - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="c70a2-233">`ascending` 디스크나 `descending` - `<boolean>`</span><span class="sxs-lookup"><span data-stu-id="c70a2-233">`ascending` or `descending` - `<boolean>`</span></span>

<span data-ttu-id="c70a2-234">자세한 내용은 [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c70a2-234">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: Default properties
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="c70a2-235">-상단</span><span class="sxs-lookup"><span data-stu-id="c70a2-235">-Top</span></span>

<span data-ttu-id="c70a2-236">정렬 된 개체 배열의 시작 부분에서 가져올 개체 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-236">Specifies the number of objects to get from the start of a sorted object array.</span></span> <span data-ttu-id="c70a2-237">이로 인해 안정적으로 정렬 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-237">This results in a stable sort.</span></span>

<span data-ttu-id="c70a2-238">이 매개 변수는 PowerShell 6.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-238">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: Top
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c70a2-239">-고유</span><span class="sxs-lookup"><span data-stu-id="c70a2-239">-Unique</span></span>

<span data-ttu-id="c70a2-240">에서 `Sort-Object` 중복을 제거 하 고 컬렉션의 고유한 멤버만 반환 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-240">Indicates that `Sort-Object` eliminates duplicates and returns only the unique members of the collection.</span></span> <span data-ttu-id="c70a2-241">고유 값의 첫 번째 인스턴스는 정렬 된 출력에 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-241">The first instance of a unique value is included in the sorted output.</span></span>

<span data-ttu-id="c70a2-242">**Unique** 는 대/소문자를 구분 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-242">**Unique** is case-insensitive.</span></span> <span data-ttu-id="c70a2-243">문자 대/소문자만 다른 문자열은 동일한 것으로 간주 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-243">Strings that only differ by character case are considered the same.</span></span>
<span data-ttu-id="c70a2-244">예를 들면 문자 및 문자입니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-244">For example, character and CHARACTER.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: All
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c70a2-245">-안정적인</span><span class="sxs-lookup"><span data-stu-id="c70a2-245">-Stable</span></span>

<span data-ttu-id="c70a2-246">정렬 된 개체는 정렬 기준이 같을 때 받은 순서 대로 배달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-246">The sorted objects are delivered in the order they were received when the sort criteria are equal.</span></span>

<span data-ttu-id="c70a2-247">이 매개 변수는 PowerShell v 6.2.0에서 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-247">This parameter was added in PowerShell v6.2.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Default
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c70a2-248">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c70a2-248">CommonParameters</span></span>

<span data-ttu-id="c70a2-249">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c70a2-249">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c70a2-250">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c70a2-250">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c70a2-251">입력</span><span class="sxs-lookup"><span data-stu-id="c70a2-251">INPUTS</span></span>

### <span data-ttu-id="c70a2-252">System.web. PSObject</span><span class="sxs-lookup"><span data-stu-id="c70a2-252">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="c70a2-253">정렬할 개체를 파이프 할 수 있습니다 `Sort-Object` .</span><span class="sxs-lookup"><span data-stu-id="c70a2-253">You can pipe the objects to be sorted to `Sort-Object`.</span></span>

## <span data-ttu-id="c70a2-254">출력</span><span class="sxs-lookup"><span data-stu-id="c70a2-254">OUTPUTS</span></span>

### <span data-ttu-id="c70a2-255">System.web. PSObject</span><span class="sxs-lookup"><span data-stu-id="c70a2-255">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="c70a2-256">`Sort-Object` 정렬 된 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-256">`Sort-Object` returns the sorted objects.</span></span>

## <span data-ttu-id="c70a2-257">참고</span><span class="sxs-lookup"><span data-stu-id="c70a2-257">NOTES</span></span>

<span data-ttu-id="c70a2-258">`Sort-Object`Cmdlet은 명령에 지정 된 속성 또는 개체 유형에 대 한 기본 정렬 속성을 기준으로 개체를 정렬 합니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-258">The `Sort-Object` cmdlet sorts objects based on properties specified in the command or the default sort properties for the object type.</span></span> <span data-ttu-id="c70a2-259">기본 정렬 속성은 `PropertySet` 파일의 명명 된를 사용 하 여 정의 됩니다 `DefaultKeyPropertySet` `types.ps1xml` .</span><span class="sxs-lookup"><span data-stu-id="c70a2-259">Default sort properties are defined using the `PropertySet` named `DefaultKeyPropertySet` in a `types.ps1xml` file.</span></span> <span data-ttu-id="c70a2-260">자세한 내용은 [about_Types.ps1xml](/powershell/module/Microsoft.PowerShell.Core/About/about_Types.ps1xml)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c70a2-260">For more information, see [about_Types.ps1xml](/powershell/module/Microsoft.PowerShell.Core/About/about_Types.ps1xml).</span></span>

<span data-ttu-id="c70a2-261">개체에 지정 된 속성 중 하나가 없는 경우 해당 개체의 속성 값은에서 `Sort-Object` **Null** 로 해석 되 고 정렬 순서의 끝에 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-261">If an object does not have one of the specified properties, the property value for that object is interpreted by `Sort-Object` as **Null** and placed at the end of the sort order.</span></span>

<span data-ttu-id="c70a2-262">사용할 수 있는 정렬 속성이 없으면 PowerShell에서 개체 자체를 비교 하려고 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-262">When no sort properties are available, PowerShell attempts to compare the objects themselves.</span></span>
<span data-ttu-id="c70a2-263">`Sort-Object` 각 속성에 대해 **Compare** 메서드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-263">`Sort-Object` uses the **Compare** method for each property.</span></span> <span data-ttu-id="c70a2-264">속성이 **IComparable** 을 구현 하지 않는 경우 cmdlet은 속성 값을 문자열로 변환 하 **고 System.string에 대해** **Compare** 메서드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-264">If a property does not implement **IComparable** , the cmdlet converts the property value to a string and uses the **Compare** method for **System.String**.</span></span> <span data-ttu-id="c70a2-265">자세한 내용은 [PSObject. CompareTo (Object) 메서드](/dotnet/api/system.management.automation.psobject.compareto)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c70a2-265">For more information, see [PSObject.CompareTo(Object) Method](/dotnet/api/system.management.automation.psobject.compareto).</span></span>

<span data-ttu-id="c70a2-266">**상태** 와 같은 열거 된 속성을 기준으로 정렬 하는 경우 `Sort-Object` 열거형 값을 기준으로 정렬 합니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-266">If you sort on an enumerated property such as **Status** , `Sort-Object` sorts by the enumeration values.</span></span> <span data-ttu-id="c70a2-267">Windows 서비스의 경우 **중지** 됨의 값은 **1** 이 고 **실행** 값은 **4** 입니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-267">For Windows services, **Stopped** has a value of **1** and **Running** has a value of **4**.</span></span>
<span data-ttu-id="c70a2-268">열거 된 값 때문에 **중지** 됨이 **실행** 되기 전에 정렬 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-268">**Stopped** is sorted before **Running** because of the enumerated values.</span></span> <span data-ttu-id="c70a2-269">자세한 내용은 [ServiceControllerStatus](/dotnet/api/system.serviceprocess.servicecontrollerstatus)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c70a2-269">For more information, see [ServiceControllerStatus](/dotnet/api/system.serviceprocess.servicecontrollerstatus).</span></span>

<span data-ttu-id="c70a2-270">안정적인 정렬을 수행할 때 정렬 알고리즘의 성능이 느려집니다.</span><span class="sxs-lookup"><span data-stu-id="c70a2-270">The performance of the sorting algorithm is slower when doing a stable sort.</span></span>

## <span data-ttu-id="c70a2-271">관련 링크</span><span class="sxs-lookup"><span data-stu-id="c70a2-271">RELATED LINKS</span></span>

[<span data-ttu-id="c70a2-272">about_Calculated_Properties</span><span class="sxs-lookup"><span data-stu-id="c70a2-272">about_Calculated_Properties</span></span>](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[<span data-ttu-id="c70a2-273">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="c70a2-273">about_Hash_Tables</span></span>](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md)

[<span data-ttu-id="c70a2-274">about_Types.ps1xml</span><span class="sxs-lookup"><span data-stu-id="c70a2-274">about_Types.ps1xml</span></span>](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md)

[<span data-ttu-id="c70a2-275">Compare-Object</span><span class="sxs-lookup"><span data-stu-id="c70a2-275">Compare-Object</span></span>](Compare-Object.md)

[<span data-ttu-id="c70a2-276">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="c70a2-276">ForEach-Object</span></span>](../Microsoft.PowerShell.Core/ForEach-Object.md)

[<span data-ttu-id="c70a2-277">Group-Object</span><span class="sxs-lookup"><span data-stu-id="c70a2-277">Group-Object</span></span>](Group-Object.md)

[<span data-ttu-id="c70a2-278">Measure-Object</span><span class="sxs-lookup"><span data-stu-id="c70a2-278">Measure-Object</span></span>](Measure-Object.md)

[<span data-ttu-id="c70a2-279">New-Object</span><span class="sxs-lookup"><span data-stu-id="c70a2-279">New-Object</span></span>](New-Object.md)

[<span data-ttu-id="c70a2-280">Select-Object</span><span class="sxs-lookup"><span data-stu-id="c70a2-280">Select-Object</span></span>](Select-Object.md)

[<span data-ttu-id="c70a2-281">Tee-Object</span><span class="sxs-lookup"><span data-stu-id="c70a2-281">Tee-Object</span></span>](Tee-Object.md)
