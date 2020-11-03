---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/23/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/export-csv?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-Csv
ms.openlocfilehash: 5a76f8ec454ad8144f193d8927f913b89a429fec
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93214041"
---
# <span data-ttu-id="28e23-103">Export-Csv</span><span class="sxs-lookup"><span data-stu-id="28e23-103">Export-Csv</span></span>

## <span data-ttu-id="28e23-104">개요</span><span class="sxs-lookup"><span data-stu-id="28e23-104">SYNOPSIS</span></span>
<span data-ttu-id="28e23-105">개체를 일련의 쉼표로 구분 된 값 (CSV) 문자열로 변환 하 고 문자열을 파일에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-105">Converts objects into a series of comma-separated value (CSV) strings and saves the strings to a file.</span></span>

## <span data-ttu-id="28e23-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="28e23-106">SYNTAX</span></span>

### <span data-ttu-id="28e23-107">구분 기호 (기본값)</span><span class="sxs-lookup"><span data-stu-id="28e23-107">Delimiter (Default)</span></span>

```
Export-Csv [[-Path] <string>] [[-Delimiter] <char>] -InputObject <psobject> [-LiteralPath <string>]
 [-Force] [-NoClobber] [-Encoding <string>] [-Append] [-NoTypeInformation] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="28e23-108">UseCulture</span><span class="sxs-lookup"><span data-stu-id="28e23-108">UseCulture</span></span>

```
Export-Csv [[-Path] <string>] -InputObject <psobject> [-LiteralPath <string>] [-Force] [-NoClobber]
 [-Encoding <string>] [-Append] [-UseCulture] [-NoTypeInformation] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="28e23-109">설명</span><span class="sxs-lookup"><span data-stu-id="28e23-109">DESCRIPTION</span></span>

<span data-ttu-id="28e23-110">`Export-CSV`Cmdlet은 제출한 개체의 CSV 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-110">The `Export-CSV` cmdlet creates a CSV file of the objects that you submit.</span></span> <span data-ttu-id="28e23-111">각 개체는 개체의 속성 값에 대 한 쉼표로 구분 된 목록을 포함 하는 행입니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-111">Each object is a row that includes a comma-separated list of the object's property values.</span></span> <span data-ttu-id="28e23-112">Cmdlet을 사용 `Export-CSV` 하 여 CSV 파일을 입력으로 수락 하는 프로그램을 사용 하 여 스프레드시트를 만들고 데이터를 공유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-112">You can use the `Export-CSV` cmdlet to create spreadsheets and share data with programs that accept CSV files as input.</span></span>

<span data-ttu-id="28e23-113">개체를 cmdlet으로 보내기 전에 서식을 지정 하지 마십시오 `Export-CSV` .</span><span class="sxs-lookup"><span data-stu-id="28e23-113">Do not format objects before sending them to the `Export-CSV` cmdlet.</span></span> <span data-ttu-id="28e23-114">`Export-CSV`에서 형식이 지정 된 개체를 받으면 CSV 파일에 개체 속성이 아닌 형식 속성이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-114">If `Export-CSV` receives formatted objects the CSV file contains the format properties rather than the object properties.</span></span> <span data-ttu-id="28e23-115">개체의 선택 된 속성만 내보내려면 cmdlet을 사용 `Select-Object` 합니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-115">To export only selected properties of an object, use the `Select-Object` cmdlet.</span></span>

## <span data-ttu-id="28e23-116">예제</span><span class="sxs-lookup"><span data-stu-id="28e23-116">EXAMPLES</span></span>

### <span data-ttu-id="28e23-117">예제 1: CSV 파일로 프로세스 속성 내보내기</span><span class="sxs-lookup"><span data-stu-id="28e23-117">Example 1: Export process properties to a CSV file</span></span>

<span data-ttu-id="28e23-118">이 예제에서는 특정 속성을 사용 하 여 개체 **처리** 를 선택 하 고 개체를 CSV 파일로 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-118">This example selects **Process** objects with specific properties, exports the objects to a CSV file.</span></span>

```powershell
Get-Process -Name WmiPrvSE | Select-Object -Property BasePriority,Id,SessionId,WorkingSet |
  Export-Csv -Path .\WmiData.csv -NoTypeInformation
Import-Csv -Path .\WmiData.csv
```

```Output
BasePriority Id    SessionId WorkingSet
------------ --    --------- ----------
8            976   0         20267008
8            2292  0         36786176
8            3816  0         30351360
8            8604  0         15011840
8            10008 0         8830976
8            11764 0         14237696
8            54632 0         9502720
```

<span data-ttu-id="28e23-119">`Get-Process`Cmdlet은 **프로세스** 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-119">The `Get-Process` cmdlet gets the **Process** objects.</span></span> <span data-ttu-id="28e23-120">**Name** 매개 변수는 WmiPrvSE process 개체만 포함 하도록 출력을 필터링 합니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-120">The **Name** parameter filters the output to include only the WmiPrvSE process objects.</span></span> <span data-ttu-id="28e23-121">프로세스 개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="28e23-121">The process objects are sent down the pipeline to the `Select-Object` cmdlet.</span></span> <span data-ttu-id="28e23-122">`Select-Object`**Property** 매개 변수를 사용 하 여 프로세스 개체 속성의 하위 집합을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-122">`Select-Object` uses the **Property** parameter to select a subset of process object properties.</span></span> <span data-ttu-id="28e23-123">프로세스 개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Export-Csv` .</span><span class="sxs-lookup"><span data-stu-id="28e23-123">The process objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="28e23-124">`Export-Csv` 프로세스 개체를 일련의 CSV 문자열로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-124">`Export-Csv` converts the process objects to a series of CSV strings.</span></span> <span data-ttu-id="28e23-125">**Path** 매개 변수는 WmiData.csv 파일이 현재 디렉터리에 저장 되도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-125">The **Path** parameter specifies that the WmiData.csv file is saved in the current directory.</span></span> <span data-ttu-id="28e23-126">**Notypeinformation** 매개 변수는 CSV 출력에서 **#TYPE** information 헤더를 제거 하며 PowerShell 6에서는 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-126">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="28e23-127">`Import-Csv`Cmdlet은 **Path** 매개 변수를 사용 하 여 현재 디렉터리에 있는 파일을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-127">The `Import-Csv` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

### <span data-ttu-id="28e23-128">예제 2: 쉼표로 구분 된 파일로 프로세스 내보내기</span><span class="sxs-lookup"><span data-stu-id="28e23-128">Example 2: Export processes to a comma-delimited file</span></span>

<span data-ttu-id="28e23-129">이 예제에서는 **프로세스** 개체를 가져오고 개체를 CSV 파일로 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-129">This example gets **Process** objects and exports the objects to a CSV file.</span></span>

```powershell
Get-Process | Export-Csv -Path .\Processes.csv -NoTypeInformation
Get-Content -Path .\Processes.csv
```

```Output
"Name","SI","Handles","VM","WS","PM","NPM","Path","Parent","Company","CPU","FileVersion", ...
"ApplicationFrameHost","4","511","2203597099008","35364864","21979136","30048", ...
```

<span data-ttu-id="28e23-130">`Get-Process`Cmdlet은 **프로세스** 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-130">The `Get-Process` cmdlet gets **Process** objects.</span></span> <span data-ttu-id="28e23-131">프로세스 개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Export-Csv` .</span><span class="sxs-lookup"><span data-stu-id="28e23-131">The process objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="28e23-132">`Export-Csv` 프로세스 개체를 일련의 CSV 문자열로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-132">`Export-Csv` converts the process objects to a series of CSV strings.</span></span>
<span data-ttu-id="28e23-133">**Path** 매개 변수는 Processes.csv 파일이 현재 디렉터리에 저장 되도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-133">The **Path** parameter specifies that the Processes.csv file is saved in the current directory.</span></span> <span data-ttu-id="28e23-134">**Notypeinformation** 매개 변수는 CSV 출력에서 **#TYPE** information 헤더를 제거 하며 PowerShell 6에서는 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-134">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="28e23-135">`Get-Content`Cmdlet은 **Path** 매개 변수를 사용 하 여 현재 디렉터리에 있는 파일을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-135">The `Get-Content` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

### <span data-ttu-id="28e23-136">예제 3: 세미콜론으로 구분 된 파일로 프로세스 내보내기</span><span class="sxs-lookup"><span data-stu-id="28e23-136">Example 3: Export processes to a semicolon delimited file</span></span>

<span data-ttu-id="28e23-137">이 예제에서는 **프로세스** 개체를 가져오고 세미콜론 구분 기호를 사용 하 여 개체를 파일로 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-137">This example gets **Process** objects and exports the objects to a file with a semicolon delimiter.</span></span>

```powershell
Get-Process | Export-Csv -Path .\Processes.csv -Delimiter ';' -NoTypeInformation
Get-Content -Path .\Processes.csv
```

```Output
"Name";"SI";"Handles";"VM";"WS";"PM";"NPM";"Path";"Parent";"Company";"CPU";"FileVersion"; ...
"ApplicationFrameHost";"4";"509";"2203595321344";"34807808";"21770240";"29504"; ...
```

<span data-ttu-id="28e23-138">`Get-Process`Cmdlet은 **프로세스** 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-138">The `Get-Process` cmdlet gets **Process** objects.</span></span> <span data-ttu-id="28e23-139">프로세스 개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Export-Csv` .</span><span class="sxs-lookup"><span data-stu-id="28e23-139">The process objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="28e23-140">`Export-Csv` 프로세스 개체를 일련의 CSV 문자열로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-140">`Export-Csv` converts the process objects to a series of CSV strings.</span></span>
<span data-ttu-id="28e23-141">**Path** 매개 변수는 Processes.csv 파일이 현재 디렉터리에 저장 되도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-141">The **Path** parameter specifies that the Processes.csv file is saved in the current directory.</span></span> <span data-ttu-id="28e23-142">**Delimiter** 매개 변수는 문자열 값을 구분 하기 위해 세미콜론을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-142">The **Delimiter** parameter specifies a semicolon to separate the string values.</span></span> <span data-ttu-id="28e23-143">**Notypeinformation** 매개 변수는 CSV 출력에서 **#TYPE** information 헤더를 제거 하며 PowerShell 6에서는 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-143">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="28e23-144">`Get-Content`Cmdlet은 **Path** 매개 변수를 사용 하 여 현재 디렉터리에 있는 파일을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-144">The `Get-Content` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

### <span data-ttu-id="28e23-145">예제 4: 현재 문화권의 목록 구분 기호를 사용 하 여 프로세스 내보내기</span><span class="sxs-lookup"><span data-stu-id="28e23-145">Example 4: Export processes using the current culture's list separator</span></span>

<span data-ttu-id="28e23-146">이 예제에서는 **프로세스** 개체를 가져오고 개체를 파일로 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-146">This example gets **Process** objects and exports the objects to a file.</span></span> <span data-ttu-id="28e23-147">구분 기호는 현재 문화권의 목록 구분 기호입니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-147">The delimiter is the current culture's list separator.</span></span>

```powershell
(Get-Culture).TextInfo.ListSeparator
Get-Process | Export-Csv -Path .\Processes.csv -UseCulture -NoTypeInformation
Get-Content -Path .\Processes.csv
```

```Output
"Name","SI","Handles","VM","WS","PM","NPM","Path","Parent","Company","CPU","FileVersion", ...
"ApplicationFrameHost","4","511","2203597099008","35364864","21979136","30048", ...
```

<span data-ttu-id="28e23-148">이 `Get-Culture` cmdlet은 중첩 된 속성 **System.globalization.cultureinfo.installeduiculture.textinfo.oemcodepage** 및 **listseparator** 를 사용 하 고 현재 문화권의 기본 목록 구분 기호를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-148">The `Get-Culture` cmdlet uses the nested properties **TextInfo** and **ListSeparator** and displays the current culture's default list separator.</span></span> <span data-ttu-id="28e23-149">`Get-Process`Cmdlet은 **프로세스** 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-149">The `Get-Process` cmdlet gets **Process** objects.</span></span>
<span data-ttu-id="28e23-150">프로세스 개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Export-Csv` .</span><span class="sxs-lookup"><span data-stu-id="28e23-150">The process objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="28e23-151">`Export-Csv` 프로세스 개체를 일련의 CSV 문자열로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-151">`Export-Csv` converts the process objects to a series of CSV strings.</span></span> <span data-ttu-id="28e23-152">**Path** 매개 변수는 Processes.csv 파일이 현재 디렉터리에 저장 되도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-152">The **Path** parameter specifies that the Processes.csv file is saved in the current directory.</span></span> <span data-ttu-id="28e23-153">**UseCulture** 매개 변수는 현재 문화권의 기본 목록 구분 기호를 구분 기호로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-153">The **UseCulture** parameter uses the current culture's default list separator as the delimiter.</span></span> <span data-ttu-id="28e23-154">**Notypeinformation** 매개 변수는 CSV 출력에서 **#TYPE** information 헤더를 제거 하며 PowerShell 6에서는 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-154">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="28e23-155">`Get-Content`Cmdlet은 **Path** 매개 변수를 사용 하 여 현재 디렉터리에 있는 파일을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-155">The `Get-Content` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

### <span data-ttu-id="28e23-156">예 5: 형식 정보를 사용 하 여 프로세스 내보내기</span><span class="sxs-lookup"><span data-stu-id="28e23-156">Example 5: Export processes with type information</span></span>

<span data-ttu-id="28e23-157">이 예제에서는 **#TYPE** 헤더 정보를 CSV 파일에 포함 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-157">This example explains how to include the **#TYPE** header information in a CSV file.</span></span> <span data-ttu-id="28e23-158">**#TYPE** 헤더는 PowerShell 6.0 이전 버전의 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-158">The **#TYPE** header is the default in versions prior to PowerShell 6.0.</span></span>

```powershell
Get-Process | Export-Csv -Path .\Processes.csv
Get-Content -Path .\Processes.csv
```

```Output
#TYPE System.Diagnostics.Process
"Name","SI","Handles","VM","WS","PM","NPM","Path","Company","CPU","FileVersion", ...
"ApplicationFrameHost","4","507","2203595001856","35139584","20934656","29504", ...
```

<span data-ttu-id="28e23-159">`Get-Process`Cmdlet은 **프로세스** 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-159">The `Get-Process` cmdlet gets **Process** objects.</span></span> <span data-ttu-id="28e23-160">프로세스 개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Export-Csv` .</span><span class="sxs-lookup"><span data-stu-id="28e23-160">The process objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="28e23-161">`Export-Csv` 프로세스 개체를 일련의 CSV 문자열로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-161">`Export-Csv` converts the process objects to a series of CSV strings.</span></span>
<span data-ttu-id="28e23-162">**Path** 매개 변수는 Processes.csv 파일이 현재 디렉터리에 저장 되도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-162">The **Path** parameter specifies that the Processes.csv file is saved in the current directory.</span></span> <span data-ttu-id="28e23-163">`Get-Content`Cmdlet은 **Path** 매개 변수를 사용 하 여 현재 디렉터리에 있는 파일을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-163">The `Get-Content` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

### <span data-ttu-id="28e23-164">예제 6: CSV 파일에 개체 내보내기 및 추가</span><span class="sxs-lookup"><span data-stu-id="28e23-164">Example 6: Export and append objects to a CSV file</span></span>

<span data-ttu-id="28e23-165">이 예제에서는 개체를 CSV 파일로 내보내고 **Append** 매개 변수를 사용 하 여 기존 파일에 개체를 추가 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-165">This example describes how to export objects to a CSV file and use the **Append** parameter to add objects to an existing file.</span></span>

```powershell
$AppService = (Get-Service -DisplayName *Application* | Select-Object -Property DisplayName, Status)
$AppService | Export-Csv -Path .\Services.Csv -NoTypeInformation
Get-Content -Path .\Services.Csv
$WinService = (Get-Service -DisplayName *Windows* | Select-Object -Property DisplayName, Status)
$WinService | Export-Csv -Path ./Services.csv -NoTypeInformation -Append
Get-Content -Path .\Services.Csv
```

```Output
"DisplayName","Status"
"Application Layer Gateway Service","Stopped"
"Application Identity","Running"
"Windows Audio Endpoint Builder","Running"
"Windows Audio","Running"
"Windows Event Log","Running"
```

<span data-ttu-id="28e23-166">`Get-Service`Cmdlet은 서비스 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-166">The `Get-Service` cmdlet gets service objects.</span></span> <span data-ttu-id="28e23-167">**DisplayName** 매개 변수는 Word 응용 프로그램을 포함 하는 서비스를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-167">The **DisplayName** parameter returns services that contain the word Application.</span></span> <span data-ttu-id="28e23-168">Service 개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="28e23-168">The service objects are sent down the pipeline to the `Select-Object` cmdlet.</span></span> <span data-ttu-id="28e23-169">`Select-Object`**Property** 매개 변수를 사용 하 여 **DisplayName** 및 **Status** 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-169">`Select-Object` uses the **Property** parameter to specify the **DisplayName** and **Status** properties.</span></span> <span data-ttu-id="28e23-170">`$AppService`변수는 개체를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-170">The `$AppService` variable stores the objects.</span></span>

<span data-ttu-id="28e23-171">`$AppService`개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Export-Csv` .</span><span class="sxs-lookup"><span data-stu-id="28e23-171">The `$AppService` objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="28e23-172">`Export-Csv` 서비스 개체를 일련의 CSV 문자열로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-172">`Export-Csv` converts the service objects to a series of CSV strings.</span></span> <span data-ttu-id="28e23-173">**Path** 매개 변수는 Services.csv 파일이 현재 디렉터리에 저장 되도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-173">The **Path** parameter specifies that the Services.csv file is saved in the current directory.</span></span> <span data-ttu-id="28e23-174">**Notypeinformation** 매개 변수는 CSV 출력에서 **#TYPE** information 헤더를 제거 하며 PowerShell 6에서는 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-174">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="28e23-175">`Get-Content`Cmdlet은 **Path** 매개 변수를 사용 하 여 현재 디렉터리에 있는 파일을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-175">The `Get-Content` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

<span data-ttu-id="28e23-176">`Get-Service`및 `Select-Object` Cmdlet은 Windows 라는 단어를 포함 하는 서비스에 대해 반복 됩니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-176">The `Get-Service` and `Select-Object` cmdlets are repeated for services that contain the word Windows.</span></span> <span data-ttu-id="28e23-177">`$WinService`변수는 서비스 개체를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-177">The `$WinService` variable stores the service objects.</span></span> <span data-ttu-id="28e23-178">`Export-Csv`Cmdlet은 **추가** 매개 변수를 사용 하 여 `$WinService` 개체가 기존 Services.csv 파일에 추가 되도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-178">The `Export-Csv` cmdlet uses the **Append** parameter to specify that the `$WinService` objects are added to the existing Services.csv file.</span></span> <span data-ttu-id="28e23-179">`Get-Content`추가 된 데이터가 포함 된 업데이트 된 파일을 표시 하기 위해 cmdlet이 반복 됩니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-179">The `Get-Content` cmdlet is repeated to display the updated file that includes the appended data.</span></span>

### <span data-ttu-id="28e23-180">예 7: 파이프라인 내의 Format cmdlet은 예기치 않은 결과를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-180">Example 7: Format cmdlet within a pipeline creates unexpected results</span></span>

<span data-ttu-id="28e23-181">이 예제에서는 파이프라인 내에서 format cmdlet을 사용 하지 않는 것이 중요 한 이유를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-181">This example shows why it is important not to use a format cmdlet within a pipeline.</span></span> <span data-ttu-id="28e23-182">예기치 않은 출력이 수신 되 면 파이프라인 구문 문제를 해결 합니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-182">When unexpected output is received, troubleshoot the pipeline syntax.</span></span>

```powershell
Get-Date | Select-Object -Property DateTime, Day, DayOfWeek, DayOfYear |
 Export-Csv -Path .\DateTime.csv -NoTypeInformation
Get-Content -Path .\DateTime.csv
```

```Output
"DateTime","Day","DayOfWeek","DayOfYear"
"Wednesday, January 2, 2019 14:59:34","2","Wednesday","2"
```

```powershell
Get-Date | Format-Table -Property DateTime, Day, DayOfWeek, DayOfYear |
 Export-Csv -Path .\FTDateTime.csv -NoTypeInformation
Get-Content -Path .\FTDateTime.csv
```

```Output
"ClassId2e4f51ef21dd47e99d3c952918aff9cd","pageHeaderEntry","pageFooterEntry","autosizeInfo", ...
"033ecb2bc07a4d43b5ef94ed5a35d280",,,,"Microsoft.PowerShell.Commands.Internal.Format. ...
"9e210fe47d09416682b841769c78b8a3",,,,,
"27c87ef9bbda4f709f6b4002fa4af63c",,,,,
"4ec4f0187cb04f4cb6973460dfe252df",,,,,
"cf522b78d86c486691226b40aa69e95c",,,,,
```

<span data-ttu-id="28e23-183">`Get-Date`Cmdlet은 **DateTime** 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-183">The `Get-Date` cmdlet gets the **DateTime** object.</span></span> <span data-ttu-id="28e23-184">개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="28e23-184">The object is sent down the pipeline to the `Select-Object` cmdlet.</span></span> <span data-ttu-id="28e23-185">`Select-Object`**Property** 매개 변수를 사용 하 여 개체 속성의 하위 집합을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-185">`Select-Object` uses the **Property** parameter to select a subset of object properties.</span></span> <span data-ttu-id="28e23-186">개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Export-Csv` .</span><span class="sxs-lookup"><span data-stu-id="28e23-186">The object is sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="28e23-187">`Export-Csv` 개체를 CSV 형식으로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-187">`Export-Csv` converts the object to a CSV format.</span></span> <span data-ttu-id="28e23-188">**Path** 매개 변수는 DateTime.csv 파일이 현재 디렉터리에 저장 되도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-188">The **Path** parameter specifies that the DateTime.csv file is saved in the current directory.</span></span> <span data-ttu-id="28e23-189">**Notypeinformation** 매개 변수는 CSV 출력에서 **#TYPE** information 헤더를 제거 하며 PowerShell 6에서는 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-189">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="28e23-190">`Get-Content`Cmdlet은 **Path** 매개 변수를 사용 하 여 현재 디렉터리에 있는 CSV 파일을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-190">The `Get-Content` cmdlet uses the **Path** parameter to display the CSV file located in the current directory.</span></span>

<span data-ttu-id="28e23-191">`Format-Table`파이프라인 내에서 cmdlet을 사용 하 여 속성을 선택 하면 예기치 않은 결과가 수신 됩니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-191">When the `Format-Table` cmdlet is used within the pipeline to select properties unexpected results are received.</span></span> <span data-ttu-id="28e23-192">`Format-Table` 테이블 형식 개체를 파이프라인에서 `Export-Csv` **DateTime** 개체가 아닌 cmdlet으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-192">`Format-Table` sends table format objects down the pipeline to the `Export-Csv` cmdlet rather than the **DateTime** object.</span></span> <span data-ttu-id="28e23-193">`Export-Csv` 테이블 형식 개체를 일련의 CSV 문자열로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-193">`Export-Csv` converts the table format objects to a series of CSV strings.</span></span> <span data-ttu-id="28e23-194">`Get-Content`Cmdlet은 테이블 형식 개체를 포함 하는 CSV 파일을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-194">The `Get-Content` cmdlet displays the CSV file which contains the table format objects.</span></span>

### <span data-ttu-id="28e23-195">예 8: Force 매개 변수를 사용 하 여 읽기 전용 파일 덮어쓰기</span><span class="sxs-lookup"><span data-stu-id="28e23-195">Example 8: Using the Force parameter to overwrite read-only files</span></span>

<span data-ttu-id="28e23-196">이 예제에서는 비어 있는 읽기 전용 파일을 만들고 **Force** 매개 변수를 사용 하 여 파일을 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-196">This example creates an empty, read-only file and uses the **Force** parameter to update the file.</span></span>

```powershell
New-Item -Path .\ReadOnly.csv -ItemType File
Set-ItemProperty -Path .\ReadOnly.csv -Name IsReadOnly -Value $true
Get-Process | Export-Csv -Path .\ReadOnly.csv -NoTypeInformation
```

```Output
Export-Csv : Access to the path 'C:\ReadOnly.csv' is denied.
At line:1 char:15
+ Get-Process | Export-Csv -Path .\ReadOnly.csv -NoTypeInformation
+               ~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : OpenError: (:) [Export-Csv], UnauthorizedAccessException
+ FullyQualifiedErrorId : FileOpenFailure,Microsoft.PowerShell.Commands.ExportCsvCommand
```

```powershell
Get-Process | Export-Csv -Path .\ReadOnly.csv -NoTypeInformation -Force
Get-Content -Path .\ReadOnly.csv
```

```Output
"Name";"SI";"Handles";"VM";"WS";"PM";"NPM";"Path";"Parent";"Company";"CPU";"FileVersion"; ...
"ApplicationFrameHost";"4";"509";"2203595321344";"34807808";"21770240";"29504"; ...
```

<span data-ttu-id="28e23-197">`New-Item`Cmdlet은 **Path** 및 **ItemType** 매개 변수를 사용 하 여 현재 디렉터리에 ReadOnly.csv 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-197">The `New-Item` cmdlet uses the **Path** and **ItemType** parameters to create the ReadOnly.csv file in the current directory.</span></span> <span data-ttu-id="28e23-198">`Set-ItemProperty`Cmdlet은 **Name** 및 **Value** 매개 변수를 사용 하 여 파일의 **IsReadOnly** 속성을 true로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-198">The `Set-ItemProperty` cmdlet uses the **Name** and **Value** parameters to change the file's **IsReadOnly** property to true.</span></span> <span data-ttu-id="28e23-199">`Get-Process`Cmdlet은 **프로세스** 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-199">The `Get-Process` cmdlet gets **Process** objects.</span></span> <span data-ttu-id="28e23-200">프로세스 개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Export-Csv` .</span><span class="sxs-lookup"><span data-stu-id="28e23-200">The process objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="28e23-201">`Export-Csv` 프로세스 개체를 일련의 CSV 문자열로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-201">`Export-Csv` converts the process objects to a series of CSV strings.</span></span> <span data-ttu-id="28e23-202">**Path** 매개 변수는 ReadOnly.csv 파일이 현재 디렉터리에 저장 되도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-202">The **Path** parameter specifies that the ReadOnly.csv file is saved in the current directory.</span></span> <span data-ttu-id="28e23-203">**Notypeinformation** 매개 변수는 CSV 출력에서 **#TYPE** information 헤더를 제거 하며 PowerShell 6에서는 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-203">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="28e23-204">이 출력은 액세스가 거부 되었기 때문에 파일이 작성 되지 않은 것을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-204">The output shows that the file is not written because access is denied.</span></span>

<span data-ttu-id="28e23-205">**Force** 매개 변수를 cmdlet에 추가 하 여 `Export-Csv` 내보내기를 강제로 파일에 쓰도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-205">The **Force** parameter is added to the `Export-Csv` cmdlet to force the export to write to the file.</span></span> <span data-ttu-id="28e23-206">`Get-Content`Cmdlet은 **Path** 매개 변수를 사용 하 여 현재 디렉터리에 있는 파일을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-206">The `Get-Content` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

### <span data-ttu-id="28e23-207">예 9: Append에 Force 매개 변수 사용</span><span class="sxs-lookup"><span data-stu-id="28e23-207">Example 9: Using the Force parameter with Append</span></span>

<span data-ttu-id="28e23-208">이 예제에서는 **Force** 매개 변수를 사용 하 여 매개 변수를 **추가** 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-208">This example shows how to use the **Force** and **Append** parameters.</span></span> <span data-ttu-id="28e23-209">이러한 매개 변수를 결합 하면 일치 하지 않는 개체 속성을 CSV 파일에 쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-209">When these parameters are combined, mismatched object properties can be written to a CSV file.</span></span>

```powershell
$Content = [PSCustomObject]@{Name = 'PowerShell Core'; Version = '6.0'}
$Content | Export-Csv -Path .\ParmFile.csv -NoTypeInformation
$AdditionalContent = [PSCustomObject]@{Name = 'Windows PowerShell'; Edition = 'Desktop'}
$AdditionalContent | Export-Csv -Path .\ParmFile.csv -NoTypeInformation -Append
```

```Output
Export-Csv : Cannot append CSV content to the following file: ParmFile.csv.
The appended object does not have a property that corresponds to the following column:
Version. To continue with mismatched properties, add the -Force parameter, and then retry
 the command.
At line:1 char:22
+ $AdditionalContent | Export-Csv -Path .\ParmFile.csv -NoTypeInformation -Append
+                      ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : InvalidData: (Version:String) [Export-Csv], InvalidOperationException
+ FullyQualifiedErrorId : CannotAppendCsvWithMismatchedPropertyNames,Microsoft.PowerShell. ...
```

```powershell
$AdditionalContent | Export-Csv -Path .\ParmFile.csv -NoTypeInformation -Append -Force
Import-Csv -Path .\ParmFile.csv
```

```Output
Name               Version
----               -------
PowerShell Core    6.0
Windows PowerShell
```

<span data-ttu-id="28e23-210">식은 **Name** 및 **Version** 속성을 사용 하 여 **PSCustomObject** 를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-210">An expression creates the **PSCustomObject** with **Name** and **Version** properties.</span></span> <span data-ttu-id="28e23-211">값은 변수에 저장 됩니다 `$Content` .</span><span class="sxs-lookup"><span data-stu-id="28e23-211">The values are stored in the `$Content` variable.</span></span> <span data-ttu-id="28e23-212">`$Content`변수가 파이프라인에서 cmdlet으로 전송 됩니다 `Export-Csv` .</span><span class="sxs-lookup"><span data-stu-id="28e23-212">The `$Content` variable is sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="28e23-213">`Export-Csv`**Path** 매개 변수를 사용 하 여 현재 디렉터리에 ParmFile.csv 파일을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-213">`Export-Csv` uses the **Path** parameter and saves the ParmFile.csv file in the current directory.</span></span> <span data-ttu-id="28e23-214">**Notypeinformation** 매개 변수는 CSV 출력에서 **#TYPE** information 헤더를 제거 하며 PowerShell 6에서는 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-214">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span>

<span data-ttu-id="28e23-215">다른 식은 **Name** 및 **Edition** 속성을 사용 하 여 **PSCustomObject** 를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-215">Another expression creates a **PSCustomObject** with the **Name** and **Edition** properties.</span></span> <span data-ttu-id="28e23-216">값은 변수에 저장 됩니다 `$AdditionalContent` .</span><span class="sxs-lookup"><span data-stu-id="28e23-216">The values are stored in the `$AdditionalContent` variable.</span></span> <span data-ttu-id="28e23-217">`$AdditionalContent`변수가 파이프라인에서 cmdlet으로 전송 됩니다 `Export-Csv` .</span><span class="sxs-lookup"><span data-stu-id="28e23-217">The `$AdditionalContent` variable is sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="28e23-218">**추가** 매개 변수는 파일에 데이터를 추가 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-218">The **Append** parameter is used to add the data to the file.</span></span> <span data-ttu-id="28e23-219">**버전** 및 버전 간에 속성 이름이 일치 하지 않으므로 추가 작업이 **실패 합니다.**</span><span class="sxs-lookup"><span data-stu-id="28e23-219">The append fails because there is a property name mismatch between **Version** and **Edition** .</span></span>

<span data-ttu-id="28e23-220">`Export-Csv`Cmdlet **force** 매개 변수를 사용 하 여 내보내기를 강제로 파일에 쓰도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-220">The `Export-Csv` cmdlet **Force** parameter is used to force the export to write to the file.</span></span> <span data-ttu-id="28e23-221">**Edition** 속성이 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-221">The **Edition** property is discarded.</span></span> <span data-ttu-id="28e23-222">`Import-Csv`Cmdlet은 **Path** 매개 변수를 사용 하 여 현재 디렉터리에 있는 파일을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-222">The `Import-Csv` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

## <span data-ttu-id="28e23-223">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="28e23-223">PARAMETERS</span></span>

### <span data-ttu-id="28e23-224">-추가</span><span class="sxs-lookup"><span data-stu-id="28e23-224">-Append</span></span>

<span data-ttu-id="28e23-225">이 매개 변수를 사용 하 여 `Export-CSV` 지정 된 파일의 끝에 CSV 출력을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-225">Use this parameter so that `Export-CSV` adds CSV output to the end of the specified file.</span></span> <span data-ttu-id="28e23-226">이 매개 변수를 사용 하지 않으면 `Export-CSV` 는 경고 없이 파일 내용을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-226">Without this parameter, `Export-CSV` replaces the file contents without warning.</span></span>

<span data-ttu-id="28e23-227">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-227">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="28e23-228">-구분 기호</span><span class="sxs-lookup"><span data-stu-id="28e23-228">-Delimiter</span></span>

<span data-ttu-id="28e23-229">속성 값을 구분하는 구분 기호를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-229">Specifies a delimiter to separate the property values.</span></span> <span data-ttu-id="28e23-230">기본값은 쉼표 ()입니다 `,` .</span><span class="sxs-lookup"><span data-stu-id="28e23-230">The default is a comma (`,`).</span></span> <span data-ttu-id="28e23-231">콜론 ()과 같은 문자를 입력 `:` 합니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-231">Enter a character, such as a colon (`:`).</span></span> <span data-ttu-id="28e23-232">세미콜론 ()을 지정 하려면 `;` 따옴표로 묶으십시오.</span><span class="sxs-lookup"><span data-stu-id="28e23-232">To specify a semicolon (`;`), enclose it in quotation marks.</span></span>

```yaml
Type: System.Char
Parameter Sets: Delimiter
Aliases:

Required: False
Position: 1
Default value: comma (,)
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="28e23-233">-Encoding</span><span class="sxs-lookup"><span data-stu-id="28e23-233">-Encoding</span></span>

<span data-ttu-id="28e23-234">대상 파일의 인코딩 유형을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-234">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="28e23-235">기본값은 `ASCII`입니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-235">The default value is `ASCII`.</span></span>

<span data-ttu-id="28e23-236">이 매개 변수에 허용 되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-236">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="28e23-237">`ASCII` ASCII (7 비트) 문자 집합을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-237">`ASCII` Uses ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="28e23-238">`BigEndianUnicode` 에서는 u t f-16을 빅 endian 바이트 순서로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-238">`BigEndianUnicode` Uses UTF-16 with the big-endian byte order.</span></span>
- <span data-ttu-id="28e23-239">`Default` 시스템의 활성 코드 페이지에 해당 하는 인코딩을 사용 합니다 (일반적으로 ANSI).</span><span class="sxs-lookup"><span data-stu-id="28e23-239">`Default` Uses the encoding that corresponds to the system's active code page (usually ANSI).</span></span>
- <span data-ttu-id="28e23-240">`OEM` 시스템의 현재 OEM 코드 페이지에 해당 하는 인코딩을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-240">`OEM` Uses the encoding that corresponds to the system's current OEM code page.</span></span>
- <span data-ttu-id="28e23-241">`Unicode` 는 u t f-16을 약간 endian 바이트 순서로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-241">`Unicode` Uses UTF-16 with the little-endian byte order.</span></span>
- <span data-ttu-id="28e23-242">`UTF7` 는 u t f-7을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-242">`UTF7` Uses UTF-7.</span></span>
- <span data-ttu-id="28e23-243">`UTF8` 는 u t f-8을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-243">`UTF8` Uses UTF-8.</span></span>
- <span data-ttu-id="28e23-244">`UTF32` 는 u t f-32을 작은 endian 바이트 순서로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-244">`UTF32` Uses UTF-32 with the little-endian byte order.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, Default, OEM, Unicode, UTF7, UTF8, UTF32

Required: False
Position: Named
Default value: ASCII
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="28e23-245">-Force</span><span class="sxs-lookup"><span data-stu-id="28e23-245">-Force</span></span>

<span data-ttu-id="28e23-246">이 매개 변수 `Export-Csv` 를 사용 하면 **읽기 전용** 특성으로 파일을 덮어쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-246">This parameter allows `Export-Csv` to overwrite files with the **Read Only** attribute.</span></span>

<span data-ttu-id="28e23-247">**Force** 및 **Append** 매개 변수를 결합 하면 일치 하지 않는 속성을 포함 하는 개체를 CSV 파일에 쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-247">When **Force** and **Append** parameters are combined, objects that contain mismatched properties can be written to a CSV file.</span></span> <span data-ttu-id="28e23-248">일치 하는 속성만 파일에 기록 됩니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-248">Only the properties that match are written to the file.</span></span> <span data-ttu-id="28e23-249">일치 하지 않는 속성은 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-249">The mismatched properties are discarded.</span></span>

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

### <span data-ttu-id="28e23-250">-InputObject</span><span class="sxs-lookup"><span data-stu-id="28e23-250">-InputObject</span></span>

<span data-ttu-id="28e23-251">CSV 문자열로 내보낼 개체를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-251">Specifies the objects to export as CSV strings.</span></span> <span data-ttu-id="28e23-252">개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="28e23-252">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span> <span data-ttu-id="28e23-253">개체를로 파이프 할 수도 있습니다 `Export-CSV` .</span><span class="sxs-lookup"><span data-stu-id="28e23-253">You can also pipe objects to `Export-CSV`.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="28e23-254">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="28e23-254">-LiteralPath</span></span>

<span data-ttu-id="28e23-255">CSV 출력 파일의 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-255">Specifies the path to the CSV output file.</span></span> <span data-ttu-id="28e23-256">**Path** 와 달리 **LiteralPath** 매개 변수 값은 입력한 대로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-256">Unlike **Path** , the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="28e23-257">어떠한 문자도 와일드카드로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-257">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="28e23-258">경로에 이스케이프 문자가 포함 된 경우 작은따옴표를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-258">If the path includes escape characters, use single quotation marks.</span></span> <span data-ttu-id="28e23-259">작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-259">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSPath

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="28e23-260">-NoClobber</span><span class="sxs-lookup"><span data-stu-id="28e23-260">-NoClobber</span></span>

<span data-ttu-id="28e23-261">이 매개 변수를 사용 하 여 `Export-CSV` 기존 파일을 덮어쓰지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-261">Use this parameter so that `Export-CSV` does not overwrite an existing file.</span></span> <span data-ttu-id="28e23-262">기본적으로 지정 된 경로에 파일이 있으면는 `Export-CSV` 경고 없이 파일을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-262">By default, if the file exists in the specified path, `Export-CSV` overwrites the file without warning.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NoOverwrite

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="28e23-263">-NoTypeInformation</span><span class="sxs-lookup"><span data-stu-id="28e23-263">-NoTypeInformation</span></span>

<span data-ttu-id="28e23-264">출력에서 **#TYPE** 정보 헤더를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-264">Removes the **#TYPE** information header from the output.</span></span> <span data-ttu-id="28e23-265">이 매개 변수는 PowerShell 6.0의 기본값이 며 이전 버전과의 호환성을 위해 포함 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-265">This parameter became the default in PowerShell 6.0 and is included for backwards compatibility.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NTI

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="28e23-266">-Path</span><span class="sxs-lookup"><span data-stu-id="28e23-266">-Path</span></span>

<span data-ttu-id="28e23-267">CSV 출력 파일을 저장할 위치를 지정 하는 필수 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-267">A required parameter that specifies the location to save the CSV output file.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="28e23-268">-UseCulture</span><span class="sxs-lookup"><span data-stu-id="28e23-268">-UseCulture</span></span>

<span data-ttu-id="28e23-269">현재 문화권의 목록 구분 기호를 항목 구분 기호로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-269">Uses the list separator for the current culture as the item delimiter.</span></span> <span data-ttu-id="28e23-270">문화권에 대 한 목록 구분 기호를 찾으려면 다음 명령을 사용 합니다. `(Get-Culture).TextInfo.ListSeparator`</span><span class="sxs-lookup"><span data-stu-id="28e23-270">To find the list separator for a culture, use the following command: `(Get-Culture).TextInfo.ListSeparator`.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: UseCulture
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="28e23-271">-Confirm</span><span class="sxs-lookup"><span data-stu-id="28e23-271">-Confirm</span></span>

<span data-ttu-id="28e23-272">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-272">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="28e23-273">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="28e23-273">-WhatIf</span></span>

<span data-ttu-id="28e23-274">Cmdlet이 처리 되지 않거나 변경 되지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-274">Prevents the cmdlet from being processed or making changes.</span></span> <span data-ttu-id="28e23-275">출력은 cmdlet이 실행 될 때 발생 하는 상황을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-275">The output shows what would happen if the cmdlet were run.</span></span>

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

### <span data-ttu-id="28e23-276">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="28e23-276">CommonParameters</span></span>

<span data-ttu-id="28e23-277">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="28e23-277">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="28e23-278">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="28e23-278">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="28e23-279">입력</span><span class="sxs-lookup"><span data-stu-id="28e23-279">INPUTS</span></span>

### <span data-ttu-id="28e23-280">System.web. PSObject</span><span class="sxs-lookup"><span data-stu-id="28e23-280">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="28e23-281">Any (확장 형식 시스템) 어댑터를 사용 하 여 개체를로 파이프 할 수 있습니다 `Export-CSV` .</span><span class="sxs-lookup"><span data-stu-id="28e23-281">You can pipe any object with an Extended Type System (ETS) adapter to `Export-CSV`.</span></span>

## <span data-ttu-id="28e23-282">출력</span><span class="sxs-lookup"><span data-stu-id="28e23-282">OUTPUTS</span></span>

### <span data-ttu-id="28e23-283">System.String</span><span class="sxs-lookup"><span data-stu-id="28e23-283">System.String</span></span>

<span data-ttu-id="28e23-284">CSV 목록이 Path 매개 변수에 지정된 파일로 보내집니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-284">The CSV list is sent to the file designated in the Path parameter.</span></span>

## <span data-ttu-id="28e23-285">참고</span><span class="sxs-lookup"><span data-stu-id="28e23-285">NOTES</span></span>

<span data-ttu-id="28e23-286">`Export-CSV`Cmdlet은 제출한 개체를 일련의 CSV 문자열로 변환 하 고 지정 된 텍스트 파일에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-286">The `Export-CSV` cmdlet converts the objects that you submit into a series of CSV strings and saves them in the specified text file.</span></span> <span data-ttu-id="28e23-287">`Export-CSV`를 사용 하 여 개체를 csv 파일에 저장 한 다음 cmdlet을 사용 하 여 `Import-Csv` csv 파일에서 개체를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-287">You can use `Export-CSV` to save objects in a CSV file and then use the `Import-Csv` cmdlet to create objects from the CSV file.</span></span>

<span data-ttu-id="28e23-288">CSV 파일에서 각 개체는 쉼표로 구분된 개체 속성 값 목록으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-288">In the CSV file, each object is represented by a comma-separated list of the property values of the object.</span></span> <span data-ttu-id="28e23-289">속성 값은 **ToString ()** 메서드를 사용 하 여 문자열로 변환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-289">The property values are converted to strings using the **ToString()** method.</span></span> <span data-ttu-id="28e23-290">문자열은 속성 값 이름으로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-290">The strings are represented by the property value name.</span></span> <span data-ttu-id="28e23-291">' Export-CSV는 개체의 메서드를 내보내지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-291">\`Export-CSV does not export the methods of the object.</span></span>

<span data-ttu-id="28e23-292">CSV 문자열은 다음과 같이 출력 됩니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-292">The CSV strings are output as follows:</span></span>

- <span data-ttu-id="28e23-293">기본적으로 첫 번째 문자열에는 **#TYPE** 정보 헤더와 개체 형식의 정규화 된 이름이 차례로 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-293">By default the first string contains the **#TYPE** information header followed by the object type's fully qualified name.</span></span> <span data-ttu-id="28e23-294">예를 들어, **#TYPE를 처리** 합니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-294">For example, **#TYPE System.Diagnostics.Process** .</span></span>
- <span data-ttu-id="28e23-295">**Notypeinformation** 이 사용 되는 경우 첫 번째 문자열에는 열 머리글이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-295">If **NoTypeInformation** is used the first string includes the column headers.</span></span> <span data-ttu-id="28e23-296">헤더는 첫 번째 개체의 속성 이름을 쉼표로 구분 된 목록으로 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-296">The headers contain the first object's property names as a comma-separated list.</span></span>
- <span data-ttu-id="28e23-297">나머지 문자열은 각 개체의 속성 값에 대 한 쉼표로 구분 된 목록을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-297">The remaining strings contain comma-separated lists of each object's property values.</span></span>

<span data-ttu-id="28e23-298">여러 개체를에 제출할 때 `Export-CSV` 는 `Export-CSV` 제출한 첫 번째 개체의 속성을 기반으로 파일을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-298">When you submit multiple objects to `Export-CSV`, `Export-CSV` organizes the file based on the properties of the first object that you submit.</span></span> <span data-ttu-id="28e23-299">나머지 개체에 지정된 속성 중 하나가 없는 경우 해당 개체의 속성 값은 null이며, 두 개의 연속된 쉼표로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-299">If the remaining objects do not have one of the specified properties, the property value of that object is null, as represented by two consecutive commas.</span></span> <span data-ttu-id="28e23-300">나머지 개체에 추가 속성이 있을 경우 이러한 속성 값은 파일에 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-300">If the remaining objects have additional properties, those property values are not included in the file.</span></span>

<span data-ttu-id="28e23-301">Cmdlet을 사용 `Import-Csv` 하 여 파일에 있는 CSV 문자열에서 개체를 다시 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-301">You can use the `Import-Csv` cmdlet to recreate objects from the CSV strings in the files.</span></span> <span data-ttu-id="28e23-302">결과 개체는 속성 값(메서드는 포함 안 됨)의 문자열 표시로 이루어진 원래 개체의 CSV 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-302">The resulting objects are CSV versions of the original objects that consist of string representations of the property values and no methods.</span></span>

<span data-ttu-id="28e23-303">및 cmdlet은 개체를 csv 문자열과 csv 문자열로 `ConvertTo-Csv` `ConvertFrom-Csv` 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-303">The `ConvertTo-Csv` and `ConvertFrom-Csv` cmdlets convert objects to CSV strings and from CSV strings.</span></span> <span data-ttu-id="28e23-304">`Export-CSV` 은 `ConvertTo-CSV` CSV 문자열을 파일에 저장 한다는 점을 제외 하 고와 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="28e23-304">`Export-CSV` is the same as `ConvertTo-CSV`, except that it saves the CSV strings in a file.</span></span>

## <span data-ttu-id="28e23-305">관련 링크</span><span class="sxs-lookup"><span data-stu-id="28e23-305">RELATED LINKS</span></span>

[<span data-ttu-id="28e23-306">ConvertFrom-Csv</span><span class="sxs-lookup"><span data-stu-id="28e23-306">ConvertFrom-Csv</span></span>](ConvertFrom-Csv.md)

[<span data-ttu-id="28e23-307">ConvertTo-Csv</span><span class="sxs-lookup"><span data-stu-id="28e23-307">ConvertTo-Csv</span></span>](ConvertTo-Csv.md)

[<span data-ttu-id="28e23-308">Format-Table</span><span class="sxs-lookup"><span data-stu-id="28e23-308">Format-Table</span></span>](Format-Table.md)

[<span data-ttu-id="28e23-309">Import-Csv</span><span class="sxs-lookup"><span data-stu-id="28e23-309">Import-Csv</span></span>](Import-Csv.md)

[<span data-ttu-id="28e23-310">Select-Object</span><span class="sxs-lookup"><span data-stu-id="28e23-310">Select-Object</span></span>](Select-Object.md)
