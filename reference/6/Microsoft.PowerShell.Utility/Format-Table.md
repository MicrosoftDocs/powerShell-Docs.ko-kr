---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-table?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-Table
ms.openlocfilehash: 06f0573496f04d6790d7899afa5809ede720adee
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/10/2020
ms.locfileid: "93219402"
---
# <span data-ttu-id="fa6a6-103">Format-Table</span><span class="sxs-lookup"><span data-stu-id="fa6a6-103">Format-Table</span></span>

## <span data-ttu-id="fa6a6-104">개요</span><span class="sxs-lookup"><span data-stu-id="fa6a6-104">SYNOPSIS</span></span>
<span data-ttu-id="fa6a6-105">출력 형식을 테이블로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-105">Formats the output as a table.</span></span>

## <span data-ttu-id="fa6a6-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="fa6a6-106">SYNTAX</span></span>

### <span data-ttu-id="fa6a6-107">모두</span><span class="sxs-lookup"><span data-stu-id="fa6a6-107">All</span></span>

```
Format-Table [-AutoSize] [-RepeatHeader] [-HideTableHeaders] [-Wrap] [[-Property] <Object[]>]
 [-GroupBy <Object>] [-View <String>] [-ShowError] [-DisplayError] [-Force] [-Expand <String>]
 [-InputObject <PSObject>] [<CommonParameters>]
```

## <span data-ttu-id="fa6a6-108">설명</span><span class="sxs-lookup"><span data-stu-id="fa6a6-108">DESCRIPTION</span></span>

<span data-ttu-id="fa6a6-109">`Format-Table`Cmdlet은 각 열에서 개체의 선택 된 속성을 사용 하 여 명령 출력의 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-109">The `Format-Table` cmdlet formats the output of a command as a table with the selected properties of the object in each column.</span></span> <span data-ttu-id="fa6a6-110">개체 유형은 각 열에 표시 되는 기본 레이아웃 및 속성을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-110">The object type determines the default layout and properties that are displayed in each column.</span></span> <span data-ttu-id="fa6a6-111">**Property** 매개 변수를 사용 하 여 표시할 속성을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-111">You can use the **Property** parameter to select the properties that you want to display.</span></span>

<span data-ttu-id="fa6a6-112">PowerShell은 기본 포맷터를 사용 하 여 개체 유형을 표시 하는 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-112">PowerShell uses default formatters to define how object types are displayed.</span></span> <span data-ttu-id="fa6a6-113">파일을 사용 하 여 `.ps1xml` 지정 된 속성의 출력 테이블을 표시 하는 사용자 지정 보기를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-113">You can use `.ps1xml` files to create custom views that display an output table with specified properties.</span></span> <span data-ttu-id="fa6a6-114">사용자 지정 뷰를 만든 후 **view** 매개 변수를 사용 하 여 사용자 지정 보기와 함께 테이블을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-114">After a custom view is created, use the **View** parameter to display the table with your custom view.</span></span> <span data-ttu-id="fa6a6-115">보기에 대 한 자세한 내용은 [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-115">For more information about views, see [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md).</span></span>

<span data-ttu-id="fa6a6-116">해시 테이블을 사용 하 여 개체를 표시 하기 전에 개체에 계산 된 속성을 추가 하 고 테이블에 열 머리글을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-116">You can use a hash table to add calculated properties to an object before displaying it and to specify the column headings in the table.</span></span> <span data-ttu-id="fa6a6-117">계산 된 속성을 추가 하려면 **property** 또는 **GroupBy** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-117">To add a calculated property, use the **Property** or **GroupBy** parameter.</span></span> <span data-ttu-id="fa6a6-118">해시 테이블에 대한 자세한 내용은 [about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-118">For more information about hash tables, see [about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md).</span></span>

## <span data-ttu-id="fa6a6-119">예제</span><span class="sxs-lookup"><span data-stu-id="fa6a6-119">EXAMPLES</span></span>

### <span data-ttu-id="fa6a6-120">예제 1: PowerShell 호스트 포맷</span><span class="sxs-lookup"><span data-stu-id="fa6a6-120">Example 1: Format PowerShell host</span></span>

<span data-ttu-id="fa6a6-121">이 예에서는 테이블의 PowerShell에 대 한 호스트 프로그램 정보를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-121">This example displays information about the host program for PowerShell in a table.</span></span>

```powershell
Get-Host | Format-Table -AutoSize
```

<span data-ttu-id="fa6a6-122">`Get-Host`Cmdlet은 호스트를 나타내는 **system.web** .. n a m.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-122">The `Get-Host` cmdlet gets **System.Management.Automation.Internal.Host.InternalHost** objects that represent the host.</span></span> <span data-ttu-id="fa6a6-123">개체는 파이프라인에서로 전송 되 `Format-Table` 고 테이블에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-123">The objects are sent down the pipeline to `Format-Table` and displayed in a table.</span></span> <span data-ttu-id="fa6a6-124">**AutoSize** 매개 변수는 잘림을 최소화 하도록 열 너비를 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-124">The **AutoSize** parameter adjusts the column widths to minimize truncation.</span></span>

### <span data-ttu-id="fa6a6-125">예제 2: BasePriority로 프로세스 서식 지정</span><span class="sxs-lookup"><span data-stu-id="fa6a6-125">Example 2: Format processes by BasePriority</span></span>

<span data-ttu-id="fa6a6-126">이 예제에서는 동일한 **Basepriority** 속성이 있는 그룹에 프로세스를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-126">In this example, processes are displayed in groups that have the same **BasePriority** property.</span></span>

```powershell
Get-Process | Sort-Object -Property BasePriority | Format-Table -GroupBy BasePriority -Wrap
```

<span data-ttu-id="fa6a6-127">`Get-Process`Cmdlet은 컴퓨터의 각 프로세스를 나타내는 개체를 가져와 파이프라인에서로 보냅니다 `Sort-Object` .</span><span class="sxs-lookup"><span data-stu-id="fa6a6-127">The `Get-Process` cmdlet gets objects that represent each process on the computer and sends them down the pipeline to `Sort-Object`.</span></span> <span data-ttu-id="fa6a6-128">개체는 **Basepriority** 속성의 순서 대로 정렬 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-128">The objects are sorted in the order of their **BasePriority** property.</span></span>

<span data-ttu-id="fa6a6-129">정렬 된 개체는 파이프라인에서로 전송 됩니다 `Format-Table` .</span><span class="sxs-lookup"><span data-stu-id="fa6a6-129">The sorted objects are sent down the pipeline to `Format-Table`.</span></span> <span data-ttu-id="fa6a6-130">**GroupBy** 매개 변수는 **basepriority** 속성의 값을 기준으로 프로세스 데이터를 그룹으로 정렬 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-130">The **GroupBy** parameter arranges the process data into groups based on their **BasePriority** property's value.</span></span> <span data-ttu-id="fa6a6-131">**Wrap** 매개 변수는 데이터가 잘리지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-131">The **Wrap** parameter ensures that data isn't truncated.</span></span>

### <span data-ttu-id="fa6a6-132">예 3: 시작 날짜별로 프로세스 서식 지정</span><span class="sxs-lookup"><span data-stu-id="fa6a6-132">Example 3: Format processes by start date</span></span>

<span data-ttu-id="fa6a6-133">이 예에서는 컴퓨터에서 실행 중인 프로세스에 대 한 정보를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-133">This example displays information about the processes running on the computer.</span></span> <span data-ttu-id="fa6a6-134">개체는 정렬 되 고 `Format-Table` 뷰를 사용 하 여 개체를 시작 날짜별로 그룹화 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-134">The objects are sorted and `Format-Table` uses a view to group the objects by their start date.</span></span>

```powershell
Get-Process | Sort-Object StartTime | Format-Table -View StartTime
```

<span data-ttu-id="fa6a6-135">`Get-Process` 컴퓨터에서 실행 중인 프로세스를 나타내는 **시스템 진단** 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-135">`Get-Process` gets the **System.Diagnostics.Process** objects that represent the processes running on the computer.</span></span> <span data-ttu-id="fa6a6-136">개체는 파이프라인에서로 전송 되 `Sort-Object` 고 **StartTime** 속성을 기준으로 정렬 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-136">The objects are sent down the pipeline to `Sort-Object`, and are sorted based on the **StartTime** property.</span></span>

<span data-ttu-id="fa6a6-137">정렬 된 개체는 파이프라인에서로 전송 됩니다 `Format-Table` .</span><span class="sxs-lookup"><span data-stu-id="fa6a6-137">The sorted objects are sent down the pipeline to `Format-Table`.</span></span> <span data-ttu-id="fa6a6-138">**View** 매개 변수는 PowerShell 파일에서 system.object에 대해 정의 된 **StartTime** 뷰를 지정 합니다. `DotNetTypes.format.ps1xml` **System.Diagnostics.Process**</span><span class="sxs-lookup"><span data-stu-id="fa6a6-138">The **View** parameter specifies the **StartTime** view that's defined in the PowerShell `DotNetTypes.format.ps1xml` file for **System.Diagnostics.Process** objects.</span></span> <span data-ttu-id="fa6a6-139">**StartTime** 보기는 각 프로세스 시작 시간을 간단한 날짜로 변환한 다음 시작 날짜별로 프로세스를 그룹화 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-139">The **StartTime** view converts each processes start time to a short date and then groups the processes by the start date.</span></span>

<span data-ttu-id="fa6a6-140">파일에는 `DotNetTypes.format.ps1xml` 프로세스에 대 한 **우선 순위** 보기가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-140">The `DotNetTypes.format.ps1xml` file contains a **Priority** view for processes.</span></span> <span data-ttu-id="fa6a6-141">`format.ps1xml`사용자 지정 보기를 사용 하 여 파일을 직접 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-141">You can create your own `format.ps1xml` files with customized views.</span></span>

### <span data-ttu-id="fa6a6-142">예 4: 테이블 출력에 사용자 지정 보기 사용</span><span class="sxs-lookup"><span data-stu-id="fa6a6-142">Example 4: Use a custom view for table output</span></span>

<span data-ttu-id="fa6a6-143">이 예제에서 사용자 지정 보기에는 디렉터리의 내용이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-143">In this example, a custom view displays a directory's contents.</span></span> <span data-ttu-id="fa6a6-144">사용자 지정 뷰는에서 만든 **system.io.directoryinfo** 및 CreationTime 개체에 **대 한 테이블** 출력에 **CreationTime** 열을 추가 합니다 `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="fa6a6-144">The custom view adds the **CreationTime** column to the table output for **System.IO.DirectoryInfo** and **System.IO.FileInfo** objects created by `Get-ChildItem`.</span></span>

<span data-ttu-id="fa6a6-145">이 예제의 사용자 지정 보기는 PowerShell 소스 코드에 정의 된 뷰에서 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-145">The custom view in this example was created from the view defined in PowerShell source code.</span></span> <span data-ttu-id="fa6a6-146">이 예제의 뷰를 만드는 데 사용 되는 뷰 및 코드에 대 한 자세한 내용은 [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md#sample-xml-for-a-format-table-custom-view)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-146">For more information about views and the code used to create this example's view, see [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md#sample-xml-for-a-format-table-custom-view).</span></span>

```powershell
Get-ChildItem  -Path C:\Test | Format-Table -View mygciview
```

```Output
    Directory: C:\Test

Mode                LastWriteTime              CreationTime         Length Name
----                -------------              ------------         ------ ----
d-----        11/4/2019     15:54       9/24/2019     15:54                Archives
d-----        8/27/2019     14:22       8/27/2019     14:22                Drawings
d-----       10/23/2019     09:38       2/25/2019     09:38                Files
-a----        11/7/2019     11:07       11/7/2019     11:07          11345 Alias.txt
-a----        2/27/2019     15:15       2/27/2019     15:15            258 alias_out.txt
-a----        2/27/2019     15:16       2/27/2019     15:16            258 alias_out2.txt
```

<span data-ttu-id="fa6a6-147">`Get-ChildItem` 현재 디렉터리의 콘텐츠를 가져옵니다 `C:\Test` .</span><span class="sxs-lookup"><span data-stu-id="fa6a6-147">`Get-ChildItem` gets the contents of the current directory, `C:\Test`.</span></span> <span data-ttu-id="fa6a6-148">**System.io.directoryinfo** 및 **system.object** 개체는 파이프라인으로 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-148">The **System.IO.DirectoryInfo** and **System.IO.FileInfo** objects are sent down the pipeline.</span></span>
<span data-ttu-id="fa6a6-149">`Format-Table`**view** 매개 변수를 사용 하 여 **CreationTime** 열을 포함 하는 사용자 지정 뷰 **mygciview** 를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-149">`Format-Table` uses the **View** parameter to specify the custom view **mygciview** that includes the **CreationTime** column.</span></span>

<span data-ttu-id="fa6a6-150">`Format-Table`에 대 한 기본 출력에는 `Get-ChildItem` **CreationTime** 열이 포함 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-150">The default `Format-Table` output for `Get-ChildItem` doesn't include the **CreationTime** column.</span></span>

### <span data-ttu-id="fa6a6-151">예 5: 테이블 출력에 속성 사용</span><span class="sxs-lookup"><span data-stu-id="fa6a6-151">Example 5: Use properties for table output</span></span>

<span data-ttu-id="fa6a6-152">이 예에서는 **Property** 매개 변수를 사용 하 여 **Name** 및 **DependentServices** 속성을 표시 하는 두 열로 된 테이블에 모든 컴퓨터의 서비스를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-152">This example uses the **Property** parameter to display all the computer's services in a two-column table that shows the properties **Name** and **DependentServices**.</span></span>

```powershell
Get-Service | Format-Table -Property Name, DependentServices
```

<span data-ttu-id="fa6a6-153">`Get-Service` 컴퓨터의 모든 서비스를 가져오고 **ServiceController** 개체를 파이프라인 아래로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-153">`Get-Service` gets all the services on the computer and sends the **System.ServiceProcess.ServiceController** objects down the pipeline.</span></span> <span data-ttu-id="fa6a6-154">`Format-Table`**Property** 매개 변수를 사용 하 여 **Name** 및 **DependentServices** 속성이 테이블에 표시 되도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-154">`Format-Table` uses the **Property** parameter to specify that the **Name** and **DependentServices** properties are displayed in the table.</span></span>

<span data-ttu-id="fa6a6-155">**Name** 및 **DependentServices** 는 개체 형식의 속성 중 두 가지입니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-155">**Name** and **DependentServices** are two of the object type's properties.</span></span> <span data-ttu-id="fa6a6-156">모든 `Get-Service | Get-Member -MemberType Properties` 속성을 보려면:</span><span class="sxs-lookup"><span data-stu-id="fa6a6-156">To view all the properties: `Get-Service | Get-Member -MemberType Properties`.</span></span>

### <span data-ttu-id="fa6a6-157">예제 6: 프로세스의 형식을 지정 하 고 실행 시간 계산</span><span class="sxs-lookup"><span data-stu-id="fa6a6-157">Example 6: Format a process and calculate its running time</span></span>

<span data-ttu-id="fa6a6-158">이 예에서는 로컬 컴퓨터의 **메모장** 프로세스에 대 한 프로세스 이름과 총 실행 시간이 있는 테이블을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-158">This example displays a table with the process name and total running time for the local computer's **notepad** processes.</span></span> <span data-ttu-id="fa6a6-159">총 실행 시간은 현재 시간에서 각 프로세스의 시작 시간을 빼서 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-159">The total running time is calculated by subtracting the start time of each process from the current time.</span></span>

```powershell
Get-Process notepad |
  Format-Table ProcessName, @{Label="TotalRunningTime"; Expression={(Get-Date) - $_.StartTime}}
```

```Output
ProcessName TotalRunningTime
----------- ----------------
notepad     03:20:00.2751767
notepad     00:00:16.7710520
```

<span data-ttu-id="fa6a6-160">`Get-Process` 모든 로컬 컴퓨터의 **메모장** 프로세스를 가져오고 개체를 파이프라인으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-160">`Get-Process` gets all the local computer's **notepad** processes and sends the objects down the pipeline.</span></span> <span data-ttu-id="fa6a6-161">`Format-Table`**ProcessName** , `Get-Process` 속성 및 **TotalRunningTime** (계산 된 속성)의 두 열이 포함 된 테이블을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-161">`Format-Table` displays a table with two columns: **ProcessName** , a `Get-Process` property, and **TotalRunningTime** , a calculated property.</span></span>

<span data-ttu-id="fa6a6-162">**TotalRunningTime** 속성은 **Label** 과 **Expression** 이라는 두 개의 키가 있는 해시 테이블에 의해 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-162">The **TotalRunningTime** property is specified by a hash table with two keys, **Label** and **Expression**.</span></span> <span data-ttu-id="fa6a6-163">**레이블** 키는 속성 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-163">The **Label** key specifies the property name.</span></span> <span data-ttu-id="fa6a6-164">**식** 키는 계산을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-164">The **Expression** key specifies the calculation.</span></span> <span data-ttu-id="fa6a6-165">식은 각 프로세스 개체의 **StartTime** 속성을 가져온 다음 `Get-Date` 현재 날짜 및 시간을 가져오는 명령의 결과에서 뺍니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-165">The expression gets the **StartTime** property of each process object and subtracts it from the result of a `Get-Date` command, which gets the current date and time.</span></span>

### <span data-ttu-id="fa6a6-166">예 7: 메모장 프로세스 서식 지정</span><span class="sxs-lookup"><span data-stu-id="fa6a6-166">Example 7: Format Notepad processes</span></span>

<span data-ttu-id="fa6a6-167">이 예에서는 `Get-CimInstance` 를 사용 하 여 로컬 컴퓨터에 있는 모든 **메모장** 프로세스의 실행 시간을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-167">This example uses `Get-CimInstance` to get the running time for all **notepad** processes on the local computer.</span></span> <span data-ttu-id="fa6a6-168">`Get-CimInstance` **ComputerName** 매개 변수와 함께를 사용 하 여 원격 컴퓨터에서 정보를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-168">You can use `Get-CimInstance` with the **ComputerName** parameter to get information from remote computers.</span></span>

```powershell
$Processes = Get-CimInstance -Class win32_process -Filter "name='notepad.exe'"
$Processes | Format-Table ProcessName, @{ Label = "Total Running Time"; Expression={(Get-Date) - $_.CreationDate}}
```

```Output
ProcessName Total Running Time
----------- ------------------
notepad.exe 03:39:39.6260693
notepad.exe 00:19:56.1376922
```

<span data-ttu-id="fa6a6-169">`Get-CimInstance`**notepad.exe** 이라는 모든 로컬 컴퓨터의 프로세스를 설명 하는 WMI **Win32_Process** 클래스의 인스턴스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-169">`Get-CimInstance` gets instances of the WMI **Win32_Process** class that describes all the local computer's processes named **notepad.exe**.</span></span> <span data-ttu-id="fa6a6-170">프로세스 개체는 변수에 저장 됩니다 `$Processes` .</span><span class="sxs-lookup"><span data-stu-id="fa6a6-170">The process objects are stored in the `$Processes` variable.</span></span>

<span data-ttu-id="fa6a6-171">변수의 프로세스 개체는 `$Processes` `Format-Table` **ProcessName** 속성 및 새 계산 된 속성 ( **총 실행 시간** )을 표시 하는 파이프라인으로 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-171">The process objects in the `$Processes` variable are sent down the pipeline to `Format-Table`, which displays the **ProcessName** property and a new calculated property, **Total Running Time**.</span></span>

<span data-ttu-id="fa6a6-172">이 명령은 새 계산 속성의 이름 ( **총 실행 시간** )을 **레이블** 키에 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-172">The command assigns the name of the new calculated property, **Total Running Time** , to the **Label** key.</span></span> <span data-ttu-id="fa6a6-173">**식** 키의 스크립트 블록은 현재 날짜에서 프로세스 만든 날짜를 빼서 프로세스 실행 시간을 계산 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-173">The **Expression** key's script block calculates how long the process has been running by subtracting the processes creation date from the current date.</span></span> <span data-ttu-id="fa6a6-174">`Get-Date`Cmdlet은 현재 날짜를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-174">The `Get-Date` cmdlet gets the current date.</span></span> <span data-ttu-id="fa6a6-175">만든 날짜를 현재 날짜에서 뺍니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-175">The creation date is subtracted from the current date.</span></span> <span data-ttu-id="fa6a6-176">결과는 **총 실행 시간** 값입니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-176">The result is the value of **Total Running Time**.</span></span>

### <span data-ttu-id="fa6a6-177">예 8: 형식 오류 문제 해결</span><span class="sxs-lookup"><span data-stu-id="fa6a6-177">Example 8: Troubleshooting format errors</span></span>

<span data-ttu-id="fa6a6-178">다음 예에서는 식을 사용 하 여 **displayerror** 또는 **showerror** 매개 변수를 추가 하는 결과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-178">The following examples show the results of adding the **DisplayError** or **ShowError** parameters with an expression.</span></span>

```powershell
Get-Date | Format-Table DayOfWeek,{ $_ / $null } -DisplayError
```

```Output
DayOfWeek  $_ / $null
--------- ------------
Wednesday #ERR
```

```powershell
Get-Date | Format-Table DayOfWeek,{ $_ / $null } -ShowError
```

```Output
DayOfWeek  $_ / $null
--------- ------------
Wednesday
Failed to evaluate expression " $_ / $null ".
+ CategoryInfo          : InvalidArgument: (11/27/2019 12:52:38:PSObject) [], RuntimeException
+ FullyQualifiedErrorId : PSPropertyExpressionError
```

## <span data-ttu-id="fa6a6-179">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="fa6a6-179">PARAMETERS</span></span>

### <span data-ttu-id="fa6a6-180">-AutoSize</span><span class="sxs-lookup"><span data-stu-id="fa6a6-180">-AutoSize</span></span>

<span data-ttu-id="fa6a6-181">Cmdlet이 데이터의 너비에 따라 열 크기 및 열 수를 조정 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-181">Indicates that the cmdlet adjusts the column size and number of columns based on the width of the data.</span></span> <span data-ttu-id="fa6a6-182">기본적으로 열 크기 및 수는 뷰에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-182">By default, the column size and number are determined by the view.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fa6a6-183">-DisplayError</span><span class="sxs-lookup"><span data-stu-id="fa6a6-183">-DisplayError</span></span>

<span data-ttu-id="fa6a6-184">Cmdlet이 명령줄에 오류를 표시 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-184">Indicates that the cmdlet displays errors on the command line.</span></span> <span data-ttu-id="fa6a6-185">이 매개 변수는 명령에서 식의 형식을 지정할 때 `Format-Table` 식의 문제를 해결 해야 하는 경우 디버깅 도구로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-185">This parameter can be used as a debugging aid when you're formatting expressions in a `Format-Table` command and need to troubleshoot the expressions.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fa6a6-186">-확장</span><span class="sxs-lookup"><span data-stu-id="fa6a6-186">-Expand</span></span>

<span data-ttu-id="fa6a6-187">컬렉션 개체의 형식 및 컬렉션의 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-187">Specifies the format of the collection object and the objects in the collection.</span></span> <span data-ttu-id="fa6a6-188">이 매개 변수는 [ICollection](/dotnet/api/system.collections.icollection) ([system.object](/dotnet/api/system.collections)) 인터페이스를 지 원하는 개체의 형식을 지정 하도록 디자인 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-188">This parameter is designed to format objects that support the [ICollection](/dotnet/api/system.collections.icollection) ([System.Collections](/dotnet/api/system.collections)) interface.</span></span> <span data-ttu-id="fa6a6-189">기본값은 **Enumonly** 입니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-189">The default value is **EnumOnly**.</span></span>
<span data-ttu-id="fa6a6-190">이 매개 변수에 허용 되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-190">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="fa6a6-191">**Enumonly** : 컬렉션에 있는 개체의 속성을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-191">**EnumOnly** : Displays the properties of the objects in the collection.</span></span>
- <span data-ttu-id="fa6a6-192">**CoreOnly** : 컬렉션 개체의 속성을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-192">**CoreOnly** : Displays the properties of the collection object.</span></span>
- <span data-ttu-id="fa6a6-193">**Both** : 컬렉션 개체의 속성과 컬렉션에 있는 개체의 속성을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-193">**Both** : Displays the properties of the collection object and the properties of objects in the collection.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: CoreOnly, EnumOnly, Both

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fa6a6-194">-Force</span><span class="sxs-lookup"><span data-stu-id="fa6a6-194">-Force</span></span>

<span data-ttu-id="fa6a6-195">Cmdlet이 모든 오류 정보를 표시 하도록 cmdlet에 지시 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-195">Indicates that the cmdlet directs the cmdlet to display all the error information.</span></span> <span data-ttu-id="fa6a6-196">**Displayerror** 또는 **showerror** 매개 변수와 함께 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-196">Use with the **DisplayError** or **ShowError** parameter.</span></span> <span data-ttu-id="fa6a6-197">기본적으로 오류 또는 표시 스트림에 오류 개체를 쓰는 경우 일부 오류 정보만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-197">By default, when an error object is written to the error or display streams, only some of the error information is displayed.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fa6a6-198">-GroupBy</span><span class="sxs-lookup"><span data-stu-id="fa6a6-198">-GroupBy</span></span>

<span data-ttu-id="fa6a6-199">속성 값에 따라 별도의 테이블에 정렬 된 출력을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-199">Specifies sorted output in separate tables based on a property value.</span></span> <span data-ttu-id="fa6a6-200">예를 들어 **GroupBy** 를 사용 하 여 해당 상태에 따라 별도의 테이블에 서비스를 나열할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-200">For example, you can use **GroupBy** to list services in separate tables based on their status.</span></span>

<span data-ttu-id="fa6a6-201">식 또는 속성을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-201">Enter an expression or a property.</span></span> <span data-ttu-id="fa6a6-202">**GroupBy** 매개 변수는 개체가 정렬 되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-202">The **GroupBy** parameter expects that the objects are sorted.</span></span>
<span data-ttu-id="fa6a6-203">`Sort-Object`를 사용 하기 전에 cmdlet을 사용 하 여 `Format-Table` 개체를 그룹화 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-203">Use the `Sort-Object` cmdlet before using `Format-Table` to group the objects.</span></span>

<span data-ttu-id="fa6a6-204">**GroupBy** 매개 변수 값은 새 계산 된 속성 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-204">The value of the **GroupBy** parameter can be a new calculated property.</span></span> <span data-ttu-id="fa6a6-205">계산 된 속성은 스크립트 블록이 나 해시 테이블 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-205">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="fa6a6-206">유효한 키-값 쌍은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-206">Valid key-value pairs are:</span></span>

- <span data-ttu-id="fa6a6-207">이름 (또는 레이블)- `<string>`</span><span class="sxs-lookup"><span data-stu-id="fa6a6-207">Name (or Label) - `<string>`</span></span>
- <span data-ttu-id="fa6a6-208">식 `<string>` 또는 `<script block>`</span><span class="sxs-lookup"><span data-stu-id="fa6a6-208">Expression - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="fa6a6-209">FormatString `<string>`</span><span class="sxs-lookup"><span data-stu-id="fa6a6-209">FormatString - `<string>`</span></span>

<span data-ttu-id="fa6a6-210">자세한 내용은 [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-210">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fa6a6-211">-HideTableHeaders</span><span class="sxs-lookup"><span data-stu-id="fa6a6-211">-HideTableHeaders</span></span>

<span data-ttu-id="fa6a6-212">테이블에서 열 머리글을 생략합니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-212">Omits the column headings from the table.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fa6a6-213">-InputObject</span><span class="sxs-lookup"><span data-stu-id="fa6a6-213">-InputObject</span></span>

<span data-ttu-id="fa6a6-214">형식을 지정할 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-214">Specifies the objects to format.</span></span> <span data-ttu-id="fa6a6-215">개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-215">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="fa6a6-216">-속성</span><span class="sxs-lookup"><span data-stu-id="fa6a6-216">-Property</span></span>

<span data-ttu-id="fa6a6-217">표시에 나타나는 개체 속성 및 표시되는 순서를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-217">Specifies the object properties that appear in the display and the order in which they appear.</span></span> <span data-ttu-id="fa6a6-218">하나 이상의 속성 이름을 쉼표로 구분 하 여 입력 하거나 해시 테이블을 사용 하 여 계산 된 속성을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-218">Type one or more property names, separated by commas, or use a hash table to display a calculated property.</span></span> <span data-ttu-id="fa6a6-219">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-219">Wildcards are permitted.</span></span>

<span data-ttu-id="fa6a6-220">이 매개 변수를 생략 하는 경우 표시에 표시 되는 속성은 첫 번째 개체의 속성에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-220">If you omit this parameter, the properties that appear in the display depend on the first object's properties.</span></span> <span data-ttu-id="fa6a6-221">예를 들어 첫 번째 개체에 **propertya** 및 **propertya** 가 있지만 후속 개체에 **propertya** , **propertya** 및 **propertya** 가 있는 경우 **propertya** 및 **propertya** 머리글만 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-221">For example, if the first object has **PropertyA** and **PropertyB** but subsequent objects have **PropertyA** , **PropertyB** , and **PropertyC** , then only the **PropertyA** and **PropertyB** headers will display.</span></span>

<span data-ttu-id="fa6a6-222">**Property** 매개 변수는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-222">The **Property** parameter is optional.</span></span> <span data-ttu-id="fa6a6-223">동일한 명령에서 **Property** 및 **View** 매개 변수를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-223">You can't use the **Property** and **View** parameters in the same command.</span></span>

<span data-ttu-id="fa6a6-224">**Property** 매개 변수 값은 새 계산 된 속성 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-224">The value of the **Property** parameter can be a new calculated property.</span></span> <span data-ttu-id="fa6a6-225">계산 된 속성은 스크립트 블록이 나 해시 테이블 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-225">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="fa6a6-226">유효한 키-값 쌍은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-226">Valid key-value pairs are:</span></span>

- <span data-ttu-id="fa6a6-227">이름 (또는 레이블) `<string>`</span><span class="sxs-lookup"><span data-stu-id="fa6a6-227">Name (or Label) `<string>`</span></span>
- <span data-ttu-id="fa6a6-228">식 `<string>` 또는 `<script block>`</span><span class="sxs-lookup"><span data-stu-id="fa6a6-228">Expression - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="fa6a6-229">FormatString `<string>`</span><span class="sxs-lookup"><span data-stu-id="fa6a6-229">FormatString - `<string>`</span></span>
- <span data-ttu-id="fa6a6-230">Width- `<int32>` -다음 보다 커야 함 `0`</span><span class="sxs-lookup"><span data-stu-id="fa6a6-230">Width - `<int32>` - must be greater than `0`</span></span>
- <span data-ttu-id="fa6a6-231">맞춤-값은 `Left` , `Center` 또는 일 수 있습니다. `Right`</span><span class="sxs-lookup"><span data-stu-id="fa6a6-231">Alignment - value can be `Left`, `Center`, or `Right`</span></span>

<span data-ttu-id="fa6a6-232">자세한 내용은 [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-232">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="fa6a6-233">-RepeatHeader</span><span class="sxs-lookup"><span data-stu-id="fa6a6-233">-RepeatHeader</span></span>

<span data-ttu-id="fa6a6-234">모든 화면이 가득 찬 후 테이블의 머리글을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-234">Repeats displaying the header of a table after every screen full.</span></span> <span data-ttu-id="fa6a6-235">반복 되는 헤더는 출력이 `less` 또는 `more` 화면 판독기를 사용 하 여 페이징과 같이 페이저에 파이프 되는 경우에 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-235">The repeated header is useful when the output is piped to a pager such as `less` or `more` or paging with a screen reader.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fa6a6-236">-ShowError</span><span class="sxs-lookup"><span data-stu-id="fa6a6-236">-ShowError</span></span>

<span data-ttu-id="fa6a6-237">이 매개 변수는 파이프라인을 통해 오류를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-237">This parameter sends errors through the pipeline.</span></span> <span data-ttu-id="fa6a6-238">이 매개 변수는 명령에서 식의 형식을 지정할 때 `Format-Table` 식의 문제를 해결 해야 하는 경우 디버깅 도구로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-238">This parameter can be used as a debugging aid when you're formatting expressions in a `Format-Table` command and need to troubleshoot the expressions.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fa6a6-239">-보기</span><span class="sxs-lookup"><span data-stu-id="fa6a6-239">-View</span></span>

<span data-ttu-id="fa6a6-240">PowerShell 6 부터는 기본 보기가 PowerShell 소스 코드에 정의 되어 `C#` 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-240">Beginning in PowerShell 6, the default views are defined in PowerShell `C#` source code.</span></span> <span data-ttu-id="fa6a6-241">Powershell `*.format.ps1xml` 5.1 이전 버전의 파일은 powershell 6 이상 버전에 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-241">The `*.format.ps1xml` files from PowerShell 5.1 and earlier versions don't exist in PowerShell 6 and later versions.</span></span>

<span data-ttu-id="fa6a6-242">**View** 매개 변수를 사용 하 여 테이블에 대 한 대체 형식 또는 사용자 지정 뷰를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-242">The **View** parameter lets you specify an alternate format or custom view for the table.</span></span> <span data-ttu-id="fa6a6-243">기본 PowerShell 뷰를 사용 하거나 사용자 지정 보기를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-243">You can use the default PowerShell views or create custom views.</span></span> <span data-ttu-id="fa6a6-244">사용자 지정 보기를 만드는 방법에 대 한 자세한 내용은 [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-244">For more information about how to create a custom view, see [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md).</span></span>

<span data-ttu-id="fa6a6-245">**View** 매개 변수에 대 한 대체 및 사용자 지정 뷰에서는 테이블 형식을 사용 해야 합니다. 그렇지 않으면이 `Format-Table` 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-245">The alternate and custom views for the **View** parameter must use the table format, otherwise, `Format-Table` fails.</span></span> <span data-ttu-id="fa6a6-246">대체 뷰가 목록이 면 cmdlet을 사용 합니다 `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="fa6a6-246">If the alternate view is a list, use the `Format-List` cmdlet.</span></span> <span data-ttu-id="fa6a6-247">대체 뷰가 목록이 나 테이블이 아닌 경우 cmdlet을 사용 합니다 `Format-Custom` .</span><span class="sxs-lookup"><span data-stu-id="fa6a6-247">If the alternate view isn't a list or a table, use the `Format-Custom` cmdlet.</span></span>

<span data-ttu-id="fa6a6-248">동일한 명령에서 **Property** 및 **View** 매개 변수를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-248">You can't use the **Property** and **View** parameters in the same command.</span></span>

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

### <span data-ttu-id="fa6a6-249">-Wrap</span><span class="sxs-lookup"><span data-stu-id="fa6a6-249">-Wrap</span></span>

<span data-ttu-id="fa6a6-250">다음 줄에 열 너비를 초과하는 텍스트를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-250">Displays text that exceeds the column width on the next line.</span></span> <span data-ttu-id="fa6a6-251">기본적으로 열 너비를 초과하는 텍스트는 잘립니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-251">By default, text that exceeds the column width is truncated.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fa6a6-252">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="fa6a6-252">CommonParameters</span></span>

<span data-ttu-id="fa6a6-253">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-253">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="fa6a6-254">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-254">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="fa6a6-255">입력</span><span class="sxs-lookup"><span data-stu-id="fa6a6-255">INPUTS</span></span>

### <span data-ttu-id="fa6a6-256">System.web. PSObject</span><span class="sxs-lookup"><span data-stu-id="fa6a6-256">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="fa6a6-257">파이프라인에서 모든 개체를로 보낼 수 있습니다 `Format-Table` .</span><span class="sxs-lookup"><span data-stu-id="fa6a6-257">You can send any object down the pipeline to `Format-Table`.</span></span>

## <span data-ttu-id="fa6a6-258">출력</span><span class="sxs-lookup"><span data-stu-id="fa6a6-258">OUTPUTS</span></span>

### <span data-ttu-id="fa6a6-259">Microsoft. PowerShell. Internal. Format</span><span class="sxs-lookup"><span data-stu-id="fa6a6-259">Microsoft.PowerShell.Commands.Internal.Format</span></span>

<span data-ttu-id="fa6a6-260">`Format-Table` 테이블을 나타내는 형식 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa6a6-260">`Format-Table` returns format objects that represent the table.</span></span>

## <span data-ttu-id="fa6a6-261">참고</span><span class="sxs-lookup"><span data-stu-id="fa6a6-261">NOTES</span></span>

## <span data-ttu-id="fa6a6-262">관련 링크</span><span class="sxs-lookup"><span data-stu-id="fa6a6-262">RELATED LINKS</span></span>

[<span data-ttu-id="fa6a6-263">about_Calculated_Properties</span><span class="sxs-lookup"><span data-stu-id="fa6a6-263">about_Calculated_Properties</span></span>](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[<span data-ttu-id="fa6a6-264">about_Format.ps1xml</span><span class="sxs-lookup"><span data-stu-id="fa6a6-264">about_Format.ps1xml</span></span>](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md)

[<span data-ttu-id="fa6a6-265">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="fa6a6-265">about_Hash_Tables</span></span>](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md)

[<span data-ttu-id="fa6a6-266">Export-FormatData</span><span class="sxs-lookup"><span data-stu-id="fa6a6-266">Export-FormatData</span></span>](Export-FormatData.md)

[<span data-ttu-id="fa6a6-267">Format-Custom</span><span class="sxs-lookup"><span data-stu-id="fa6a6-267">Format-Custom</span></span>](Format-Custom.md)

[<span data-ttu-id="fa6a6-268">Format-Hex</span><span class="sxs-lookup"><span data-stu-id="fa6a6-268">Format-Hex</span></span>](Format-Hex.md)

[<span data-ttu-id="fa6a6-269">Format-List</span><span class="sxs-lookup"><span data-stu-id="fa6a6-269">Format-List</span></span>](Format-List.md)

[<span data-ttu-id="fa6a6-270">Format-Wide</span><span class="sxs-lookup"><span data-stu-id="fa6a6-270">Format-Wide</span></span>](Format-Wide.md)

[<span data-ttu-id="fa6a6-271">Get-FormatData</span><span class="sxs-lookup"><span data-stu-id="fa6a6-271">Get-FormatData</span></span>](Get-FormatData.md)

[<span data-ttu-id="fa6a6-272">Get-Member</span><span class="sxs-lookup"><span data-stu-id="fa6a6-272">Get-Member</span></span>](Get-Member.md)

[<span data-ttu-id="fa6a6-273">Get-CimInstance</span><span class="sxs-lookup"><span data-stu-id="fa6a6-273">Get-CimInstance</span></span>](../CimCmdlets/Get-CimInstance.md)

[<span data-ttu-id="fa6a6-274">Update-FormatData</span><span class="sxs-lookup"><span data-stu-id="fa6a6-274">Update-FormatData</span></span>](Update-FormatData.md)
