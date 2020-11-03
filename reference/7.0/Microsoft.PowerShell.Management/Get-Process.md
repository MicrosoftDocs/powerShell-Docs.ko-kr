---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-process?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Process
ms.openlocfilehash: 1880651719d030bd015a6f431fce60527b56aae5
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93210225"
---
# <span data-ttu-id="836ff-103">Get-Process</span><span class="sxs-lookup"><span data-stu-id="836ff-103">Get-Process</span></span>

## <span data-ttu-id="836ff-104">개요</span><span class="sxs-lookup"><span data-stu-id="836ff-104">SYNOPSIS</span></span>
<span data-ttu-id="836ff-105">로컬 컴퓨터에서 실행 중인 프로세스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="836ff-105">Gets the processes that are running on the local computer.</span></span>

## <span data-ttu-id="836ff-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="836ff-106">SYNTAX</span></span>

### <span data-ttu-id="836ff-107">이름 (기본값)</span><span class="sxs-lookup"><span data-stu-id="836ff-107">Name (Default)</span></span>

```
Get-Process [[-Name] <String[]>] [-Module] [-FileVersionInfo] [<CommonParameters>]
```

### <span data-ttu-id="836ff-108">NameWithUserName</span><span class="sxs-lookup"><span data-stu-id="836ff-108">NameWithUserName</span></span>

```
Get-Process [[-Name] <String[]>] -IncludeUserName [<CommonParameters>]
```

### <span data-ttu-id="836ff-109">Id</span><span class="sxs-lookup"><span data-stu-id="836ff-109">Id</span></span>

```
Get-Process -Id <Int32[]> [-Module] [-FileVersionInfo] [<CommonParameters>]
```

### <span data-ttu-id="836ff-110">IdWithUserName</span><span class="sxs-lookup"><span data-stu-id="836ff-110">IdWithUserName</span></span>

```
Get-Process -Id <Int32[]> -IncludeUserName [<CommonParameters>]
```

### <span data-ttu-id="836ff-111">InputObject</span><span class="sxs-lookup"><span data-stu-id="836ff-111">InputObject</span></span>

```
Get-Process -InputObject <Process[]> [-Module] [-FileVersionInfo] [<CommonParameters>]
```

### <span data-ttu-id="836ff-112">InputObjectWithUserName</span><span class="sxs-lookup"><span data-stu-id="836ff-112">InputObjectWithUserName</span></span>

```
Get-Process -InputObject <Process[]> -IncludeUserName [<CommonParameters>]
```

## <span data-ttu-id="836ff-113">설명</span><span class="sxs-lookup"><span data-stu-id="836ff-113">DESCRIPTION</span></span>

<span data-ttu-id="836ff-114">`Get-Process`Cmdlet은 로컬 컴퓨터의 프로세스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="836ff-114">The `Get-Process` cmdlet gets the processes on a local computer.</span></span>

<span data-ttu-id="836ff-115">매개 변수가 없는 경우이 cmdlet은 로컬 컴퓨터의 모든 프로세스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="836ff-115">Without parameters, this cmdlet gets all of the processes on the local computer.</span></span>
<span data-ttu-id="836ff-116">프로세스 이름 또는 PID (프로세스 ID)로 특정 프로세스를 지정 하거나 파이프라인을 통해 프로세스 개체를이 cmdlet으로 전달할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="836ff-116">You can also specify a particular process by process name or process ID (PID) or pass a process object through the pipeline to this cmdlet.</span></span>

<span data-ttu-id="836ff-117">기본적으로이 cmdlet은 프로세스에 대 한 자세한 정보가 있고 프로세스를 시작 및 중지할 수 있는 메서드를 지 원하는 프로세스 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="836ff-117">By default, this cmdlet returns a process object that has detailed information about the process and supports methods that let you start and stop the process.</span></span>
<span data-ttu-id="836ff-118">또한 cmdlet의 매개 변수를 사용 `Get-Process` 하 여 프로세스에서 실행 되는 프로그램에 대 한 파일 버전 정보를 가져오고 프로세스에서 로드 된 모듈을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="836ff-118">You can also use the parameters of the `Get-Process` cmdlet to get file version information for the program that runs in the process and to get the modules that the process loaded.</span></span>

## <span data-ttu-id="836ff-119">예제</span><span class="sxs-lookup"><span data-stu-id="836ff-119">EXAMPLES</span></span>

### <span data-ttu-id="836ff-120">예 1: 로컬 컴퓨터의 모든 활성 프로세스 목록 가져오기</span><span class="sxs-lookup"><span data-stu-id="836ff-120">Example 1: Get a list of all active processes on the local computer</span></span>

```powershell
Get-Process
```

<span data-ttu-id="836ff-121">이 명령은 로컬 컴퓨터에서 실행 중인 모든 활성 프로세스 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="836ff-121">This command gets a list of all active processes running on the local computer.</span></span>
<span data-ttu-id="836ff-122">각 열에 대 한 정의는 [참고](#notes) 섹션을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="836ff-122">For a definition of each column, see the [Notes](#notes) section.</span></span>

### <span data-ttu-id="836ff-123">예제 2: 하나 이상의 프로세스에 대해 사용 가능한 모든 데이터 가져오기</span><span class="sxs-lookup"><span data-stu-id="836ff-123">Example 2: Get all available data about one or more processes</span></span>

```powershell
Get-Process winword, explorer | Format-List *
```

<span data-ttu-id="836ff-124">이 명령은 컴퓨터의 Winword 및 Explorer 프로세스에 대해 사용 가능한 모든 데이터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="836ff-124">This command gets all available data about the Winword and Explorer processes on the computer.</span></span>
<span data-ttu-id="836ff-125">**Name** 매개 변수를 사용 하 여 프로세스를 지정 하지만 선택적 매개 변수 이름은 생략 합니다.</span><span class="sxs-lookup"><span data-stu-id="836ff-125">It uses the **Name** parameter to specify the processes, but it omits the optional parameter name.</span></span>
<span data-ttu-id="836ff-126">파이프라인 연산자는 `|` 데이터를 cmdlet으로 전달 합니다 `Format-List` .이 Cmdlet은 `*` winword.exe 및 Explorer 프로세스 개체의 사용 가능한 모든 속성을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="836ff-126">The pipeline operator `|` passes the data to the `Format-List` cmdlet, which displays all available properties `*` of the Winword and Explorer process objects.</span></span>

<span data-ttu-id="836ff-127">프로세스 ID로 프로세스를 식별할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="836ff-127">You can also identify the processes by their process IDs.</span></span>
<span data-ttu-id="836ff-128">예를 들면 `Get-Process -Id 664, 2060` 입니다.</span><span class="sxs-lookup"><span data-stu-id="836ff-128">For instance, `Get-Process -Id 664, 2060`.</span></span>

### <span data-ttu-id="836ff-129">예제 3: 작업 집합이 지정 된 크기 보다 큰 모든 프로세스 가져오기</span><span class="sxs-lookup"><span data-stu-id="836ff-129">Example 3: Get all processes with a working set greater than a specified size</span></span>

```powershell
Get-Process | Where-Object {$_.WorkingSet -gt 20000000}
```

<span data-ttu-id="836ff-130">이 명령은 작업 집합이 20MB보다 큰 프로세스를 모두 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="836ff-130">This command gets all processes that have a working set greater than 20 MB.</span></span>
<span data-ttu-id="836ff-131">Cmdlet을 사용 하 여 `Get-Process`  실행 중인 모든 프로세스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="836ff-131">It uses the `Get-Process`  cmdlet to get all running processes.</span></span>
<span data-ttu-id="836ff-132">파이프라인 연산자는 `|` 프로세스 개체를 cmdlet으로 전달 합니다 `Where-Object` .이 Cmdlet은 **WorkingSet** 속성의 값이 2000만 바이트 보다 큰 개체만 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="836ff-132">The pipeline operator `|` passes the process objects to the `Where-Object` cmdlet, which selects only the object with a value greater than 20,000,000 bytes for the **WorkingSet** property.</span></span>

<span data-ttu-id="836ff-133">**WorkingSet** 는 프로세스 개체의 많은 속성 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="836ff-133">**WorkingSet** is one of many properties of process objects.</span></span>
<span data-ttu-id="836ff-134">모든 속성을 보려면를 입력 `Get-Process | Get-Member` 합니다.</span><span class="sxs-lookup"><span data-stu-id="836ff-134">To see all of the properties, type `Get-Process | Get-Member`.</span></span>
<span data-ttu-id="836ff-135">모든 수량 속성 값은 기본 표시에 킬로바이트 및 메가바이트 단위로 나열되더라도 기본적으로 바이트 단위입니다.</span><span class="sxs-lookup"><span data-stu-id="836ff-135">By default, the values of all amount properties are in bytes, even though the default display lists them in kilobytes and megabytes.</span></span>

### <span data-ttu-id="836ff-136">예 4: 우선 순위에 따라 그룹의 컴퓨터에 프로세스 나열</span><span class="sxs-lookup"><span data-stu-id="836ff-136">Example 4: List processes on the computer in groups based on priority</span></span>

```powershell
$A = Get-Process
$A | Get-Process | Format-Table -View priority
```

<span data-ttu-id="836ff-137">이러한 명령은 우선 순위 클래스를 기준으로 컴퓨터의 프로세스를 그룹으로 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="836ff-137">These commands list the processes on the computer in groups based on their priority class.</span></span>
<span data-ttu-id="836ff-138">첫 번째 명령은 컴퓨터의 모든 프로세스를 가져온 다음 변수에 저장 합니다 `$A` .</span><span class="sxs-lookup"><span data-stu-id="836ff-138">The first command gets all the processes on the computer and then stores them in the `$A` variable.</span></span>

<span data-ttu-id="836ff-139">두 번째 명령은 변수에 저장 된 **프로세스** 개체를 cmdlet으로 파이프 `$A` `Get-Process` 한 다음 cmdlet에 파이프 하 여 `Format-Table` **우선 순위** 보기를 사용 하 여 프로세스 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="836ff-139">The second command pipes the **Process** object stored in the `$A` variable to the `Get-Process` cmdlet, then to the `Format-Table` cmdlet, which formats the processes by using the **Priority** view.</span></span>

<span data-ttu-id="836ff-140">**우선 순위** 보기 및 다른 보기는 PowerShell 홈 디렉터리 ()의 types.ps1xml 형식 파일에 정의 되어 `$pshome` 있습니다.</span><span class="sxs-lookup"><span data-stu-id="836ff-140">The **Priority** view, and other views, are defined in the PS1XML format files in the PowerShell home directory (`$pshome`).</span></span>

### <span data-ttu-id="836ff-141">예 5: 표준 Get-Process 출력 표시에 속성 추가</span><span class="sxs-lookup"><span data-stu-id="836ff-141">Example 5: Add a property to the standard Get-Process output display</span></span>

```powershell
Get-Process pwsh | Format-Table `
    @{Label = "NPM(K)"; Expression = {[int]($_.NPM / 1024)}},
    @{Label = "PM(K)"; Expression = {[int]($_.PM / 1024)}},
    @{Label = "WS(K)"; Expression = {[int]($_.WS / 1024)}},
    @{Label = "VM(M)"; Expression = {[int]($_.VM / 1MB)}},
    @{Label = "CPU(s)"; Expression = {if ($_.CPU) {$_.CPU.ToString("N")}}},
    Id, MachineName, ProcessName -AutoSize
```

```Output
NPM(K) PM(K) WS(K) VM(M) CPU(s)   Id MachineName ProcessName
------ ----- ----- ----- ------   -- ----------- -----------
     6 23500 31340   142 1.70   1980 .           pwsh
     6 23500 31348   142 2.75   4016 .           pwsh
    27 54572 54520   576 5.52   4428 .           pwsh
```

<span data-ttu-id="836ff-142">이 예제에서는 `Format-Table` 표준 출력 표시에 **MachineName** 속성을 추가 하는 명령을 제공 합니다 `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="836ff-142">This example provides a `Format-Table` command that adds the **MachineName** property to the standard `Get-Process` output display.</span></span>

### <span data-ttu-id="836ff-143">예 6: 프로세스에 대 한 버전 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="836ff-143">Example 6: Get version information for a process</span></span>

```powershell
Get-Process pwsh -FileVersionInfo
```

```Output
ProductVersion   FileVersion      FileName
--------------   -----------      --------
6.1.2            6.1.2            C:\Program Files\PowerShell\6\pwsh.exe
```

<span data-ttu-id="836ff-144">이 명령은 **FileVersionInfo** 매개 변수를 사용 하 여 PowerShell 프로세스의 주 모듈인 pwsh.exe 파일에 대 한 버전 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="836ff-144">This command uses the **FileVersionInfo** parameter to get the version information for the pwsh.exe file that is the main module for the PowerShell process.</span></span>

<span data-ttu-id="836ff-145">Windows Vista 이상에서 소유 하지 않은 프로세스를 사용 하 여이 명령을 실행 하려면 관리자 권한으로 실행 옵션을 사용 하 여 PowerShell을 열어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="836ff-145">To run this command with processes that you do not own on Windows Vista and later versions of Windows, you must open PowerShell with the Run as administrator option.</span></span>

### <span data-ttu-id="836ff-146">예 7: 지정 된 프로세스를 사용 하 여 로드 된 모듈 가져오기</span><span class="sxs-lookup"><span data-stu-id="836ff-146">Example 7: Get modules loaded with the specified process</span></span>

```powershell
Get-Process SQL* -Module
```

<span data-ttu-id="836ff-147">이 명령은 **Module** 매개 변수를 사용 하 여 프로세스에 의해 로드 된 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="836ff-147">This command uses the **Module** parameter to get the modules that have been loaded by the process.</span></span>
<span data-ttu-id="836ff-148">이 명령은 이름이 SQL로 시작 하는 프로세스에 대 한 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="836ff-148">This command gets the modules for the processes that have names that begin with SQL.</span></span>

<span data-ttu-id="836ff-149">사용자가 소유 하지 않은 프로세스를 사용 하 여 Windows Vista 및 이후 버전의 Windows에서이 명령을 실행 하려면 관리자 권한으로 실행 옵션을 사용 하 여 PowerShell을 시작 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="836ff-149">To run this command on Windows Vista and later versions of Windows with processes that you do not own, you must start PowerShell with the Run as administrator option.</span></span>

### <span data-ttu-id="836ff-150">예 8: 프로세스의 소유자 찾기</span><span class="sxs-lookup"><span data-stu-id="836ff-150">Example 8: Find the owner of a process</span></span>

```powershell
Get-Process pwsh -IncludeUserName
```

```Output
Handles      WS(K)   CPU(s)     Id UserName            ProcessName
-------      -----   ------     -- --------            -----------
    782     132080     2.08   2188 DOMAIN01\user01     pwsh
```

<span data-ttu-id="836ff-151">이 명령은 프로세스의 소유자를 찾는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="836ff-151">This command shows how to find the owner of a process.</span></span>
<span data-ttu-id="836ff-152">Windows에서는 **Includeusername** 매개 변수에 관리자 권한 (관리자 권한으로 실행)이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="836ff-152">On Windows, the **IncludeUserName** parameter requires elevated user rights (Run as Administrator).</span></span>
<span data-ttu-id="836ff-153">출력은 소유자가 Domain01\user01.을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="836ff-153">The output reveals that the owner is Domain01\user01.</span></span>

### <span data-ttu-id="836ff-154">예 9: 자동 변수를 사용 하 여 현재 세션을 호스트 하는 프로세스 식별</span><span class="sxs-lookup"><span data-stu-id="836ff-154">Example 9: Use an automatic variable to identify the process hosting the current session</span></span>

```powershell
Get-Process pwsh
```

```Output
NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
------    -----      -----     ------      --  -- -----------
    83    96.21     105.95       4.33    1192  10 pwsh
    79    83.81     117.61       2.16   10580  10 pwsh
```

```powershell
Get-Process -Id $PID
```

```Output
NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
------    -----      -----     ------      --  -- -----------
    83    96.21      77.53       4.39    1192  10 pwsh
```

<span data-ttu-id="836ff-155">이러한 명령은 자동 변수를 사용 하 여 현재 PowerShell 세션을 호스트 하는 프로세스를 식별 하는 방법을 보여 줍니다 `$PID` .</span><span class="sxs-lookup"><span data-stu-id="836ff-155">These commands show how to use the `$PID` automatic variable to identify the process that is hosting the current PowerShell session.</span></span>
<span data-ttu-id="836ff-156">이 방법을 사용 하 여 중지 하거나 닫을 수 있는 다른 PowerShell 프로세스와 호스트 프로세스를 구분할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="836ff-156">You can use this method to distinguish the host process from other PowerShell processes that you might want to stop or close.</span></span>

<span data-ttu-id="836ff-157">첫 번째 명령은 현재 세션의 모든 PowerShell 프로세스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="836ff-157">The first command gets all of the PowerShell processes in the current session.</span></span>

<span data-ttu-id="836ff-158">두 번째 명령은 현재 세션을 호스트 하는 PowerShell 프로세스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="836ff-158">The second command gets the PowerShell process that is hosting the current session.</span></span>

### <span data-ttu-id="836ff-159">예 10: 주 창 제목이 있는 모든 프로세스를 가져와 테이블에 표시</span><span class="sxs-lookup"><span data-stu-id="836ff-159">Example 10: Get all processes that have a main window title and display them in a table</span></span>

```powershell
Get-Process | Where-Object {$_.mainWindowTitle} | Format-Table Id, Name, mainWindowtitle -AutoSize
```

<span data-ttu-id="836ff-160">이 명령은 주 창 제목이 있는 모든 프로세스를 가져온 다음 프로세스 ID 및 프로세스 이름과 함께 테이블에 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="836ff-160">This command gets all the processes that have a main window title, and it displays them in a table with the process ID and the process name.</span></span>

<span data-ttu-id="836ff-161">**MainWindowTitle** 속성은가 반환 하는 **프로세스** 개체의 여러 유용한 속성 중 하나일 뿐입니다 `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="836ff-161">The **mainWindowTitle** property is just one of many useful properties of the **Process** object that `Get-Process` returns.</span></span>
<span data-ttu-id="836ff-162">모든 속성을 보려면 명령의 결과를 `Get-Process` cmdlet에 파이프 `Get-Member` `Get-Process | Get-Member` 합니다.</span><span class="sxs-lookup"><span data-stu-id="836ff-162">To view all of the properties, pipe the results of a `Get-Process` command to the `Get-Member` cmdlet `Get-Process | Get-Member`.</span></span>

## <span data-ttu-id="836ff-163">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="836ff-163">PARAMETERS</span></span>

### <span data-ttu-id="836ff-164">-FileVersionInfo</span><span class="sxs-lookup"><span data-stu-id="836ff-164">-FileVersionInfo</span></span>

<span data-ttu-id="836ff-165">이 cmdlet이 프로세스에서 실행 되는 프로그램에 대 한 파일 버전 정보를 가져오는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="836ff-165">Indicates that this cmdlet gets the file version information for the program that runs in the process.</span></span>

<span data-ttu-id="836ff-166">Windows Vista 이상 버전에서 소유 하지 않은 프로세스에 대해이 매개 변수를 사용 하려면 관리자 권한으로 실행 옵션을 사용 하 여 PowerShell을 열어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="836ff-166">On Windows Vista and later versions of Windows, you must open PowerShell with the Run as administrator option to use this parameter on processes that you do not own.</span></span>

<span data-ttu-id="836ff-167">원격 컴퓨터의 프로세스에 대 한 파일 버전 정보를 가져오려면 cmdlet을 사용 `Invoke-Command` 합니다.</span><span class="sxs-lookup"><span data-stu-id="836ff-167">To get file version information for a process on a remote computer, use the `Invoke-Command` cmdlet.</span></span>

<span data-ttu-id="836ff-168">이 매개 변수를 사용 하는 것은 각 프로세스 개체의 **FileVersionInfo** 속성을 가져오는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="836ff-168">Using this parameter is equivalent to getting the **MainModule.FileVersionInfo** property of each process object.</span></span>
<span data-ttu-id="836ff-169">이 매개 변수를 사용 하는 경우는 `Get-Process` 프로세스 개체가 아닌 **FileVersionInfo** 개체 **FileVersionInfo** 를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="836ff-169">When you use this parameter, `Get-Process` returns a **FileVersionInfo** object **System.Diagnostics.FileVersionInfo** , not a process object.</span></span>
<span data-ttu-id="836ff-170">따라서와 같이 프로세스 개체가 필요한 cmdlet으로 명령의 출력을 파이프 할 수 없습니다 `Stop-Process` .</span><span class="sxs-lookup"><span data-stu-id="836ff-170">So, you cannot pipe the output of the command to a cmdlet that expects a process object, such as `Stop-Process`.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Name, Id, InputObject
Aliases: FV, FVI

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="836ff-171">-Id</span><span class="sxs-lookup"><span data-stu-id="836ff-171">-Id</span></span>

<span data-ttu-id="836ff-172">PID(프로세스 ID)로 프로세스를 하나 이상 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="836ff-172">Specifies one or more processes by process ID (PID).</span></span>
<span data-ttu-id="836ff-173">여러 ID를 지정하려면 쉼표를 사용하여 ID를 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="836ff-173">To specify multiple IDs, use commas to separate the IDs.</span></span>
<span data-ttu-id="836ff-174">프로세스의 PID를 찾으려면를 입력 `Get-Process` 합니다.</span><span class="sxs-lookup"><span data-stu-id="836ff-174">To find the PID of a process, type `Get-Process`.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: Id, IdWithUserName
Aliases: PID

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="836ff-175">-IncludeUserName</span><span class="sxs-lookup"><span data-stu-id="836ff-175">-IncludeUserName</span></span>

<span data-ttu-id="836ff-176">명령의 결과와 함께 **Process** 개체의 UserName 값이 반환 됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="836ff-176">Indicates that the UserName value of the **Process** object is returned with results of the command.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NameWithUserName, IdWithUserName, InputObjectWithUserName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="836ff-177">-InputObject</span><span class="sxs-lookup"><span data-stu-id="836ff-177">-InputObject</span></span>

<span data-ttu-id="836ff-178">프로세스 개체를 하나 이상 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="836ff-178">Specifies one or more process objects.</span></span>
<span data-ttu-id="836ff-179">개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="836ff-179">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

```yaml
Type: System.Diagnostics.Process[]
Parameter Sets: InputObject, InputObjectWithUserName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="836ff-180">-모듈</span><span class="sxs-lookup"><span data-stu-id="836ff-180">-Module</span></span>

<span data-ttu-id="836ff-181">이 cmdlet은 프로세스에 의해 로드 된 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="836ff-181">Indicates that this cmdlet gets the modules that have been loaded by the processes.</span></span>

<span data-ttu-id="836ff-182">Windows Vista 이상 버전에서 소유 하지 않은 프로세스에 대해이 매개 변수를 사용 하려면 관리자 권한으로 실행 옵션을 사용 하 여 PowerShell을 열어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="836ff-182">On Windows Vista and later versions of Windows, you must open PowerShell with the Run as administrator option to use this parameter on processes that you do not own.</span></span>

<span data-ttu-id="836ff-183">원격 컴퓨터의 프로세스에서 로드 된 모듈을 가져오려면 cmdlet을 사용 합니다 `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="836ff-183">To get the modules that have been loaded by a process on a remote computer, use the `Invoke-Command` cmdlet.</span></span>

<span data-ttu-id="836ff-184">이 매개 변수는 각 프로세스 개체의 **Modules** 속성을 가져오는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="836ff-184">This parameter is equivalent to getting the **Modules** property of each process object.</span></span>
<span data-ttu-id="836ff-185">이 매개 변수를 사용 하는 경우이 cmdlet은 프로세스 개체가 아닌 **processmodule** 개체 **system.object** 를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="836ff-185">When you use this parameter, this cmdlet returns a **ProcessModule** object **System.Diagnostics.ProcessModule** , not a process object.</span></span>
<span data-ttu-id="836ff-186">따라서와 같이 프로세스 개체가 필요한 cmdlet으로 명령의 출력을 파이프 할 수 없습니다 `Stop-Process` .</span><span class="sxs-lookup"><span data-stu-id="836ff-186">So, you cannot pipe the output of the command to a cmdlet that expects a process object, such as `Stop-Process`.</span></span>

<span data-ttu-id="836ff-187">동일한 명령에서 *Module* 및 **FileVersionInfo** 매개 변수를 모두 사용 하는 경우이 cmdlet은 모든 모듈의 파일 버전에 대 한 정보가 포함 된 **FileVersionInfo** 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="836ff-187">When you use both the *Module* and **FileVersionInfo** parameters in the same command, this cmdlet returns a **FileVersionInfo** object with information about the file version of all modules.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Name, Id, InputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="836ff-188">-Name</span><span class="sxs-lookup"><span data-stu-id="836ff-188">-Name</span></span>

<span data-ttu-id="836ff-189">프로세스 이름으로 프로세스를 하나 이상 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="836ff-189">Specifies one or more processes by process name.</span></span>
<span data-ttu-id="836ff-190">쉼표로 구분하여 여러 프로세스 이름을 입력하고 와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="836ff-190">You can type multiple process names (separated by commas) and use wildcard characters.</span></span>
<span data-ttu-id="836ff-191">매개 변수 이름("Name")은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="836ff-191">The parameter name ("Name") is optional.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Name, NameWithUserName
Aliases: ProcessName

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="836ff-192">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="836ff-192">CommonParameters</span></span>

<span data-ttu-id="836ff-193">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="836ff-193">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="836ff-194">자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="836ff-194">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="836ff-195">입력</span><span class="sxs-lookup"><span data-stu-id="836ff-195">INPUTS</span></span>

### <span data-ttu-id="836ff-196">System.Diagnostics.Process</span><span class="sxs-lookup"><span data-stu-id="836ff-196">System.Diagnostics.Process</span></span>

<span data-ttu-id="836ff-197">프로세스 개체를이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="836ff-197">You can pipe a process object to this cmdlet.</span></span>

## <span data-ttu-id="836ff-198">출력</span><span class="sxs-lookup"><span data-stu-id="836ff-198">OUTPUTS</span></span>

### <span data-ttu-id="836ff-199">FileVersionInfo, 시스템. i a. m a.</span><span class="sxs-lookup"><span data-stu-id="836ff-199">System.Diagnostics.Process, System.Diagnostics.FileVersionInfo, System.Diagnostics.ProcessModule</span></span>

<span data-ttu-id="836ff-200">기본적으로이 cmdlet은 **system.web. Process** 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="836ff-200">By default, this cmdlet returns a **System.Diagnostics.Process** object.</span></span>
<span data-ttu-id="836ff-201">**FileVersionInfo** 매개 변수를 사용 하는 경우 **FileVersionInfo** 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="836ff-201">If you use the **FileVersionInfo** parameter, it returns a **System.Diagnostics.FileVersionInfo** object.</span></span>
<span data-ttu-id="836ff-202">**FileVersionInfo** 매개 변수 없이 **Module** 매개 변수를 사용 하는 경우에는 **system.object** 개체가 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="836ff-202">If you use the **Module** parameter, without the **FileVersionInfo** parameter, it returns a **System.Diagnostics.ProcessModule** object.</span></span>

## <span data-ttu-id="836ff-203">참고</span><span class="sxs-lookup"><span data-stu-id="836ff-203">NOTES</span></span>

- <span data-ttu-id="836ff-204">이 cmdlet을 기본 제공 별칭인 ps 및 gps로 참조할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="836ff-204">You can also refer to this cmdlet by its built-in aliases, ps and gps.</span></span> <span data-ttu-id="836ff-205">자세한 내용은 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="836ff-205">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>
- <span data-ttu-id="836ff-206">64 비트 버전의 Windows를 실행 하는 컴퓨터에서 64 비트 버전의 PowerShell은 64 비트 프로세스 모듈만 가져오고, 32 비트 버전의 PowerShell은 32 비트 프로세스 모듈만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="836ff-206">On computers that are running a 64-bit version of Windows, the 64-bit version of PowerShell gets only 64-bit process modules and the 32-bit version of PowerShell gets only 32-bit process modules.</span></span>
- <span data-ttu-id="836ff-207">PowerShell에서 WMI (WMI(Windows Management Instrumentation)) Win32_Process 개체의 속성 및 메서드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="836ff-207">You can use the properties and methods of the Windows Management Instrumentation (WMI) Win32_Process object in PowerShell.</span></span> <span data-ttu-id="836ff-208">자세한 내용은 `Get-WmiObject` 및 WMI SDK를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="836ff-208">For information, see `Get-WmiObject` and the WMI SDK.</span></span>
- <span data-ttu-id="836ff-209">프로세스의 기본 표시는 다음 열을 포함하는 테이블입니다.</span><span class="sxs-lookup"><span data-stu-id="836ff-209">The default display of a process is a table that includes the following columns.</span></span> <span data-ttu-id="836ff-210">프로세스 개체의 모든 속성에 대 한 설명은 MSDN library의 [프로세스 속성](/dotnet/api/system.diagnostics.process) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="836ff-210">For a description of all of the properties of process objects, see [Process Properties](/dotnet/api/system.diagnostics.process) in the MSDN library.</span></span>
  - <span data-ttu-id="836ff-211">Handles: 프로세스에서 연 핸들 수입니다.</span><span class="sxs-lookup"><span data-stu-id="836ff-211">Handles: The number of handles that the process has opened.</span></span>
  - <span data-ttu-id="836ff-212">NPM (K): 프로세스에서 사용 하는 비페이징 메모리의 양 (킬로바이트)입니다.</span><span class="sxs-lookup"><span data-stu-id="836ff-212">NPM(K): The amount of non-paged memory that the process is using, in kilobytes.</span></span>
  - <span data-ttu-id="836ff-213">PM (K): 프로세스에서 사용 중인 페이징 가능한 메모리의 양 (킬로바이트)입니다.</span><span class="sxs-lookup"><span data-stu-id="836ff-213">PM(K): The amount of pageable memory that the process is using, in kilobytes.</span></span>
  - <span data-ttu-id="836ff-214">WS (K): 프로세스의 작업 집합 크기 (kb)입니다.</span><span class="sxs-lookup"><span data-stu-id="836ff-214">WS(K): The size of the working set of the process, in kilobytes.</span></span>
    <span data-ttu-id="836ff-215">작업 집합은 프로세스에서 최근에 참조한 메모리 페이지로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="836ff-215">The working set consists of the pages of memory that were recently referenced by the process.</span></span>
  - <span data-ttu-id="836ff-216">VM (M): 프로세스에서 사용 하는 가상 메모리의 양 (메가바이트 단위)입니다.</span><span class="sxs-lookup"><span data-stu-id="836ff-216">VM(M): The amount of virtual memory that the process is using, in megabytes.</span></span>
    <span data-ttu-id="836ff-217">가상 메모리에는 디스크 페이징 파일의 스토리지가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="836ff-217">Virtual memory includes storage in the paging files on disk.</span></span>
  - <span data-ttu-id="836ff-218">CPU (s): 프로세스가 모든 프로세서에서 사용한 프로세서 시간의 양 (초)입니다.</span><span class="sxs-lookup"><span data-stu-id="836ff-218">CPU(s): The amount of processor time that the process has used on all processors, in seconds.</span></span>
  - <span data-ttu-id="836ff-219">ID: 프로세스의 PID (프로세스 ID)입니다.</span><span class="sxs-lookup"><span data-stu-id="836ff-219">ID: The process ID (PID) of the process.</span></span>
  - <span data-ttu-id="836ff-220">ProcessName: 프로세스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="836ff-220">ProcessName: The name of the process.</span></span>
    <span data-ttu-id="836ff-221">프로세스와 관련된 개념에 대한 설명은 도움말 및 지원 센터의 용어집 및 작업 관리자에 대한 도움말을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="836ff-221">For explanations of the concepts related to processes, see the Glossary in Help and Support Center and the Help for Task Manager.</span></span>
- <span data-ttu-id="836ff-222">에서 사용할 수 있는 프로세스의 기본 제공 대체 보기 `Format-Table` (예: **StartTime** 및 **Priority** )를 사용 하 고 고유한 보기를 디자인할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="836ff-222">You can also use the built-in alternate views of the processes available with `Format-Table`, such as **StartTime** and **Priority** , and you can design your own views.</span></span>

## <span data-ttu-id="836ff-223">관련 링크</span><span class="sxs-lookup"><span data-stu-id="836ff-223">RELATED LINKS</span></span>

[<span data-ttu-id="836ff-224">Debug-Process</span><span class="sxs-lookup"><span data-stu-id="836ff-224">Debug-Process</span></span>](Debug-Process.md)

[<span data-ttu-id="836ff-225">Get-Process</span><span class="sxs-lookup"><span data-stu-id="836ff-225">Get-Process</span></span>](Get-Process.md)

[<span data-ttu-id="836ff-226">Start-Process</span><span class="sxs-lookup"><span data-stu-id="836ff-226">Start-Process</span></span>](Start-Process.md)

[<span data-ttu-id="836ff-227">Stop-Process</span><span class="sxs-lookup"><span data-stu-id="836ff-227">Stop-Process</span></span>](Stop-Process.md)

[<span data-ttu-id="836ff-228">Wait-Process</span><span class="sxs-lookup"><span data-stu-id="836ff-228">Wait-Process</span></span>](Wait-Process.md)
