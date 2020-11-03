---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 1/7/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/export-csv?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-Csv
ms.openlocfilehash: cb58276c8582f9cd1f88a114baae2ce5d0039f45
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93211049"
---
# <span data-ttu-id="8a66d-103">Export-Csv</span><span class="sxs-lookup"><span data-stu-id="8a66d-103">Export-Csv</span></span>

## <span data-ttu-id="8a66d-104">개요</span><span class="sxs-lookup"><span data-stu-id="8a66d-104">SYNOPSIS</span></span>
<span data-ttu-id="8a66d-105">개체를 일련의 쉼표로 구분 된 값 (CSV) 문자열로 변환 하 고 문자열을 파일에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-105">Converts objects into a series of comma-separated value (CSV) strings and saves the strings to a file.</span></span>

## <span data-ttu-id="8a66d-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="8a66d-106">SYNTAX</span></span>

### <span data-ttu-id="8a66d-107">구분 기호 (기본값)</span><span class="sxs-lookup"><span data-stu-id="8a66d-107">Delimiter (Default)</span></span>

```
Export-Csv -InputObject <PSObject> [[-Path] <String>] [-LiteralPath <String>] [-Force] [-NoClobber]
 [-Encoding <Encoding>] [-Append] [[-Delimiter] <Char>] [-IncludeTypeInformation]
 [-NoTypeInformation] [-QuoteFields <String[]>] [-UseQuotes <QuoteKind>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="8a66d-108">UseCulture</span><span class="sxs-lookup"><span data-stu-id="8a66d-108">UseCulture</span></span>

```
Export-Csv -InputObject <PSObject> [[-Path] <String>] [-LiteralPath <String>] [-Force] [-NoClobber]
 [-Encoding <Encoding>] [-Append] [-UseCulture] [-IncludeTypeInformation] [-NoTypeInformation]
 [-QuoteFields <String[]>] [-UseQuotes <QuoteKind>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="8a66d-109">설명</span><span class="sxs-lookup"><span data-stu-id="8a66d-109">DESCRIPTION</span></span>

<span data-ttu-id="8a66d-110">`Export-CSV`Cmdlet은 제출한 개체의 CSV 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-110">The `Export-CSV` cmdlet creates a CSV file of the objects that you submit.</span></span> <span data-ttu-id="8a66d-111">각 개체는 개체의 속성 값에 대 한 쉼표로 구분 된 목록을 포함 하는 행입니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-111">Each object is a row that includes a comma-separated list of the object's property values.</span></span> <span data-ttu-id="8a66d-112">Cmdlet을 사용 `Export-CSV` 하 여 CSV 파일을 입력으로 수락 하는 프로그램을 사용 하 여 스프레드시트를 만들고 데이터를 공유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-112">You can use the `Export-CSV` cmdlet to create spreadsheets and share data with programs that accept CSV files as input.</span></span>

<span data-ttu-id="8a66d-113">개체를 cmdlet으로 보내기 전에 서식을 지정 하지 마십시오 `Export-CSV` .</span><span class="sxs-lookup"><span data-stu-id="8a66d-113">Do not format objects before sending them to the `Export-CSV` cmdlet.</span></span> <span data-ttu-id="8a66d-114">`Export-CSV`에서 형식이 지정 된 개체를 받으면 CSV 파일에 개체 속성이 아닌 형식 속성이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-114">If `Export-CSV` receives formatted objects the CSV file contains the format properties rather than the object properties.</span></span> <span data-ttu-id="8a66d-115">개체의 선택 된 속성만 내보내려면 cmdlet을 사용 `Select-Object` 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-115">To export only selected properties of an object, use the `Select-Object` cmdlet.</span></span>

## <span data-ttu-id="8a66d-116">예제</span><span class="sxs-lookup"><span data-stu-id="8a66d-116">EXAMPLES</span></span>

### <span data-ttu-id="8a66d-117">예제 1: CSV 파일로 프로세스 속성 내보내기</span><span class="sxs-lookup"><span data-stu-id="8a66d-117">Example 1: Export process properties to a CSV file</span></span>

<span data-ttu-id="8a66d-118">이 예제에서는 특정 속성을 사용 하 여 개체 **처리** 를 선택 하 고 개체를 CSV 파일로 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-118">This example selects **Process** objects with specific properties, exports the objects to a CSV file.</span></span>

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

<span data-ttu-id="8a66d-119">`Get-Process`Cmdlet은 **프로세스** 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-119">The `Get-Process` cmdlet gets the **Process** objects.</span></span> <span data-ttu-id="8a66d-120">**Name** 매개 변수는 WmiPrvSE process 개체만 포함 하도록 출력을 필터링 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-120">The **Name** parameter filters the output to include only the WmiPrvSE process objects.</span></span> <span data-ttu-id="8a66d-121">프로세스 개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="8a66d-121">The process objects are sent down the pipeline to the `Select-Object` cmdlet.</span></span> <span data-ttu-id="8a66d-122">`Select-Object`**Property** 매개 변수를 사용 하 여 프로세스 개체 속성의 하위 집합을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-122">`Select-Object` uses the **Property** parameter to select a subset of process object properties.</span></span> <span data-ttu-id="8a66d-123">프로세스 개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Export-Csv` .</span><span class="sxs-lookup"><span data-stu-id="8a66d-123">The process objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="8a66d-124">`Export-Csv` 프로세스 개체를 일련의 CSV 문자열로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-124">`Export-Csv` converts the process objects to a series of CSV strings.</span></span> <span data-ttu-id="8a66d-125">**Path** 매개 변수는 WmiData.csv 파일이 현재 디렉터리에 저장 되도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-125">The **Path** parameter specifies that the WmiData.csv file is saved in the current directory.</span></span> <span data-ttu-id="8a66d-126">**Notypeinformation** 매개 변수는 CSV 출력에서 **#TYPE** information 헤더를 제거 하며 PowerShell 6에서는 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-126">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="8a66d-127">`Import-Csv`Cmdlet은 **Path** 매개 변수를 사용 하 여 현재 디렉터리에 있는 파일을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-127">The `Import-Csv` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

### <span data-ttu-id="8a66d-128">예제 2: 쉼표로 구분 된 파일로 프로세스 내보내기</span><span class="sxs-lookup"><span data-stu-id="8a66d-128">Example 2: Export processes to a comma-delimited file</span></span>

<span data-ttu-id="8a66d-129">이 예제에서는 **프로세스** 개체를 가져오고 개체를 CSV 파일로 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-129">This example gets **Process** objects and exports the objects to a CSV file.</span></span>

```powershell
Get-Process | Export-Csv -Path .\Processes.csv -NoTypeInformation
Get-Content -Path .\Processes.csv
```

```Output
"Name","SI","Handles","VM","WS","PM","NPM","Path","Parent","Company","CPU","FileVersion", ...
"ApplicationFrameHost","4","511","2203597099008","35364864","21979136","30048", ...
```

<span data-ttu-id="8a66d-130">`Get-Process`Cmdlet은 **프로세스** 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-130">The `Get-Process` cmdlet gets **Process** objects.</span></span> <span data-ttu-id="8a66d-131">프로세스 개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Export-Csv` .</span><span class="sxs-lookup"><span data-stu-id="8a66d-131">The process objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="8a66d-132">`Export-Csv` 프로세스 개체를 일련의 CSV 문자열로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-132">`Export-Csv` converts the process objects to a series of CSV strings.</span></span>
<span data-ttu-id="8a66d-133">**Path** 매개 변수는 Processes.csv 파일이 현재 디렉터리에 저장 되도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-133">The **Path** parameter specifies that the Processes.csv file is saved in the current directory.</span></span> <span data-ttu-id="8a66d-134">**Notypeinformation** 매개 변수는 CSV 출력에서 **#TYPE** information 헤더를 제거 하며 PowerShell 6에서는 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-134">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="8a66d-135">`Get-Content`Cmdlet은 **Path** 매개 변수를 사용 하 여 현재 디렉터리에 있는 파일을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-135">The `Get-Content` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

### <span data-ttu-id="8a66d-136">예제 3: 세미콜론으로 구분 된 파일로 프로세스 내보내기</span><span class="sxs-lookup"><span data-stu-id="8a66d-136">Example 3: Export processes to a semicolon delimited file</span></span>

<span data-ttu-id="8a66d-137">이 예제에서는 **프로세스** 개체를 가져오고 세미콜론 구분 기호를 사용 하 여 개체를 파일로 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-137">This example gets **Process** objects and exports the objects to a file with a semicolon delimiter.</span></span>

```powershell
Get-Process | Export-Csv -Path .\Processes.csv -Delimiter ';' -NoTypeInformation
Get-Content -Path .\Processes.csv
```

```Output
"Name";"SI";"Handles";"VM";"WS";"PM";"NPM";"Path";"Parent";"Company";"CPU";"FileVersion"; ...
"ApplicationFrameHost";"4";"509";"2203595321344";"34807808";"21770240";"29504"; ...
```

<span data-ttu-id="8a66d-138">`Get-Process`Cmdlet은 **프로세스** 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-138">The `Get-Process` cmdlet gets **Process** objects.</span></span> <span data-ttu-id="8a66d-139">프로세스 개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Export-Csv` .</span><span class="sxs-lookup"><span data-stu-id="8a66d-139">The process objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="8a66d-140">`Export-Csv` 프로세스 개체를 일련의 CSV 문자열로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-140">`Export-Csv` converts the process objects to a series of CSV strings.</span></span>
<span data-ttu-id="8a66d-141">**Path** 매개 변수는 Processes.csv 파일이 현재 디렉터리에 저장 되도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-141">The **Path** parameter specifies that the Processes.csv file is saved in the current directory.</span></span> <span data-ttu-id="8a66d-142">**Delimiter** 매개 변수는 문자열 값을 구분 하기 위해 세미콜론을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-142">The **Delimiter** parameter specifies a semicolon to separate the string values.</span></span> <span data-ttu-id="8a66d-143">**Notypeinformation** 매개 변수는 CSV 출력에서 **#TYPE** information 헤더를 제거 하며 PowerShell 6에서는 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-143">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="8a66d-144">`Get-Content`Cmdlet은 **Path** 매개 변수를 사용 하 여 현재 디렉터리에 있는 파일을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-144">The `Get-Content` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

### <span data-ttu-id="8a66d-145">예제 4: 현재 문화권의 목록 구분 기호를 사용 하 여 프로세스 내보내기</span><span class="sxs-lookup"><span data-stu-id="8a66d-145">Example 4: Export processes using the current culture's list separator</span></span>

<span data-ttu-id="8a66d-146">이 예제에서는 **프로세스** 개체를 가져오고 개체를 파일로 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-146">This example gets **Process** objects and exports the objects to a file.</span></span> <span data-ttu-id="8a66d-147">구분 기호는 현재 문화권의 목록 구분 기호입니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-147">The delimiter is the current culture's list separator.</span></span>

```powershell
(Get-Culture).TextInfo.ListSeparator
Get-Process | Export-Csv -Path .\Processes.csv -UseCulture -NoTypeInformation
Get-Content -Path .\Processes.csv
```

```Output
"Name","SI","Handles","VM","WS","PM","NPM","Path","Parent","Company","CPU","FileVersion", ...
"ApplicationFrameHost","4","511","2203597099008","35364864","21979136","30048", ...
```

<span data-ttu-id="8a66d-148">이 `Get-Culture` cmdlet은 중첩 된 속성 **System.globalization.cultureinfo.installeduiculture.textinfo.oemcodepage** 및 **listseparator** 를 사용 하 고 현재 문화권의 기본 목록 구분 기호를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-148">The `Get-Culture` cmdlet uses the nested properties **TextInfo** and **ListSeparator** and displays the current culture's default list separator.</span></span> <span data-ttu-id="8a66d-149">`Get-Process`Cmdlet은 **프로세스** 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-149">The `Get-Process` cmdlet gets **Process** objects.</span></span>
<span data-ttu-id="8a66d-150">프로세스 개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Export-Csv` .</span><span class="sxs-lookup"><span data-stu-id="8a66d-150">The process objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="8a66d-151">`Export-Csv` 프로세스 개체를 일련의 CSV 문자열로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-151">`Export-Csv` converts the process objects to a series of CSV strings.</span></span> <span data-ttu-id="8a66d-152">**Path** 매개 변수는 Processes.csv 파일이 현재 디렉터리에 저장 되도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-152">The **Path** parameter specifies that the Processes.csv file is saved in the current directory.</span></span> <span data-ttu-id="8a66d-153">**UseCulture** 매개 변수는 현재 문화권의 기본 목록 구분 기호를 구분 기호로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-153">The **UseCulture** parameter uses the current culture's default list separator as the delimiter.</span></span> <span data-ttu-id="8a66d-154">**Notypeinformation** 매개 변수는 CSV 출력에서 **#TYPE** information 헤더를 제거 하며 PowerShell 6에서는 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-154">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="8a66d-155">`Get-Content`Cmdlet은 **Path** 매개 변수를 사용 하 여 현재 디렉터리에 있는 파일을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-155">The `Get-Content` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

### <span data-ttu-id="8a66d-156">예 5: 형식 정보를 사용 하 여 프로세스 내보내기</span><span class="sxs-lookup"><span data-stu-id="8a66d-156">Example 5: Export processes with type information</span></span>

<span data-ttu-id="8a66d-157">이 예제에서는 **#TYPE** 헤더 정보를 CSV 파일에 포함 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-157">This example explains how to include the **#TYPE** header information in a CSV file.</span></span> <span data-ttu-id="8a66d-158">**#TYPE** 헤더는 PowerShell 6.0 이전 버전의 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-158">The **#TYPE** header is the default in versions prior to PowerShell 6.0.</span></span>

```powershell
Get-Process | Export-Csv -Path .\Processes.csv -IncludeTypeInformation
Get-Content -Path .\Processes.csv
```

```Output
#TYPE System.Diagnostics.Process
"Name","SI","Handles","VM","WS","PM","NPM","Path","Company","CPU","FileVersion", ...
"ApplicationFrameHost","4","507","2203595001856","35139584","20934656","29504", ...
```

<span data-ttu-id="8a66d-159">`Get-Process`Cmdlet은 **프로세스** 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-159">The `Get-Process` cmdlet gets **Process** objects.</span></span> <span data-ttu-id="8a66d-160">프로세스 개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Export-Csv` .</span><span class="sxs-lookup"><span data-stu-id="8a66d-160">The process objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="8a66d-161">`Export-Csv` 프로세스 개체를 일련의 CSV 문자열로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-161">`Export-Csv` converts the process objects to a series of CSV strings.</span></span>
<span data-ttu-id="8a66d-162">**Path** 매개 변수는 Processes.csv 파일이 현재 디렉터리에 저장 되도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-162">The **Path** parameter specifies that the Processes.csv file is saved in the current directory.</span></span> <span data-ttu-id="8a66d-163">**Includetypeinformation** 에는 CSV 출력의 **#TYPE** 정보 헤더가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-163">The **IncludeTypeInformation** includes the **#TYPE** information header in the CSV output.</span></span> <span data-ttu-id="8a66d-164">`Get-Content`Cmdlet은 **Path** 매개 변수를 사용 하 여 현재 디렉터리에 있는 파일을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-164">The `Get-Content` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

### <span data-ttu-id="8a66d-165">예제 6: CSV 파일에 개체 내보내기 및 추가</span><span class="sxs-lookup"><span data-stu-id="8a66d-165">Example 6: Export and append objects to a CSV file</span></span>

<span data-ttu-id="8a66d-166">이 예제에서는 개체를 CSV 파일로 내보내고 **Append** 매개 변수를 사용 하 여 기존 파일에 개체를 추가 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-166">This example describes how to export objects to a CSV file and use the **Append** parameter to add objects to an existing file.</span></span>

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

<span data-ttu-id="8a66d-167">`Get-Service`Cmdlet은 서비스 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-167">The `Get-Service` cmdlet gets service objects.</span></span> <span data-ttu-id="8a66d-168">**DisplayName** 매개 변수는 Word 응용 프로그램을 포함 하는 서비스를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-168">The **DisplayName** parameter returns services that contain the word Application.</span></span> <span data-ttu-id="8a66d-169">Service 개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="8a66d-169">The service objects are sent down the pipeline to the `Select-Object` cmdlet.</span></span> <span data-ttu-id="8a66d-170">`Select-Object`**Property** 매개 변수를 사용 하 여 **DisplayName** 및 **Status** 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-170">`Select-Object` uses the **Property** parameter to specify the **DisplayName** and **Status** properties.</span></span> <span data-ttu-id="8a66d-171">`$AppService`변수는 개체를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-171">The `$AppService` variable stores the objects.</span></span>

<span data-ttu-id="8a66d-172">`$AppService`개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Export-Csv` .</span><span class="sxs-lookup"><span data-stu-id="8a66d-172">The `$AppService` objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="8a66d-173">`Export-Csv` 서비스 개체를 일련의 CSV 문자열로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-173">`Export-Csv` converts the service objects to a series of CSV strings.</span></span> <span data-ttu-id="8a66d-174">**Path** 매개 변수는 Services.csv 파일이 현재 디렉터리에 저장 되도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-174">The **Path** parameter specifies that the Services.csv file is saved in the current directory.</span></span> <span data-ttu-id="8a66d-175">**Notypeinformation** 매개 변수는 CSV 출력에서 **#TYPE** information 헤더를 제거 하며 PowerShell 6에서는 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-175">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="8a66d-176">`Get-Content`Cmdlet은 **Path** 매개 변수를 사용 하 여 현재 디렉터리에 있는 파일을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-176">The `Get-Content` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

<span data-ttu-id="8a66d-177">`Get-Service`및 `Select-Object` Cmdlet은 Windows 라는 단어를 포함 하는 서비스에 대해 반복 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-177">The `Get-Service` and `Select-Object` cmdlets are repeated for services that contain the word Windows.</span></span> <span data-ttu-id="8a66d-178">`$WinService`변수는 서비스 개체를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-178">The `$WinService` variable stores the service objects.</span></span> <span data-ttu-id="8a66d-179">`Export-Csv`Cmdlet은 **추가** 매개 변수를 사용 하 여 `$WinService` 개체가 기존 Services.csv 파일에 추가 되도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-179">The `Export-Csv` cmdlet uses the **Append** parameter to specify that the `$WinService` objects are added to the existing Services.csv file.</span></span> <span data-ttu-id="8a66d-180">`Get-Content`추가 된 데이터가 포함 된 업데이트 된 파일을 표시 하기 위해 cmdlet이 반복 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-180">The `Get-Content` cmdlet is repeated to display the updated file that includes the appended data.</span></span>

### <span data-ttu-id="8a66d-181">예 7: 파이프라인 내의 Format cmdlet은 예기치 않은 결과를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-181">Example 7: Format cmdlet within a pipeline creates unexpected results</span></span>

<span data-ttu-id="8a66d-182">이 예제에서는 파이프라인 내에서 format cmdlet을 사용 하지 않는 것이 중요 한 이유를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-182">This example shows why it is important not to use a format cmdlet within a pipeline.</span></span> <span data-ttu-id="8a66d-183">예기치 않은 출력이 수신 되 면 파이프라인 구문 문제를 해결 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-183">When unexpected output is received, troubleshoot the pipeline syntax.</span></span>

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

<span data-ttu-id="8a66d-184">`Get-Date`Cmdlet은 **DateTime** 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-184">The `Get-Date` cmdlet gets the **DateTime** object.</span></span> <span data-ttu-id="8a66d-185">개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="8a66d-185">The object is sent down the pipeline to the `Select-Object` cmdlet.</span></span> <span data-ttu-id="8a66d-186">`Select-Object`**Property** 매개 변수를 사용 하 여 개체 속성의 하위 집합을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-186">`Select-Object` uses the **Property** parameter to select a subset of object properties.</span></span> <span data-ttu-id="8a66d-187">개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Export-Csv` .</span><span class="sxs-lookup"><span data-stu-id="8a66d-187">The object is sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="8a66d-188">`Export-Csv` 개체를 CSV 형식으로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-188">`Export-Csv` converts the object to a CSV format.</span></span> <span data-ttu-id="8a66d-189">**Path** 매개 변수는 DateTime.csv 파일이 현재 디렉터리에 저장 되도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-189">The **Path** parameter specifies that the DateTime.csv file is saved in the current directory.</span></span> <span data-ttu-id="8a66d-190">**Notypeinformation** 매개 변수는 CSV 출력에서 **#TYPE** information 헤더를 제거 하며 PowerShell 6에서는 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-190">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="8a66d-191">`Get-Content`Cmdlet은 **Path** 매개 변수를 사용 하 여 현재 디렉터리에 있는 CSV 파일을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-191">The `Get-Content` cmdlet uses the **Path** parameter to display the CSV file located in the current directory.</span></span>

<span data-ttu-id="8a66d-192">`Format-Table`파이프라인 내에서 cmdlet을 사용 하 여 속성을 선택 하면 예기치 않은 결과가 수신 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-192">When the `Format-Table` cmdlet is used within the pipeline to select properties unexpected results are received.</span></span> <span data-ttu-id="8a66d-193">`Format-Table` 테이블 형식 개체를 파이프라인에서 `Export-Csv` **DateTime** 개체가 아닌 cmdlet으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-193">`Format-Table` sends table format objects down the pipeline to the `Export-Csv` cmdlet rather than the **DateTime** object.</span></span> <span data-ttu-id="8a66d-194">`Export-Csv` 테이블 형식 개체를 일련의 CSV 문자열로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-194">`Export-Csv` converts the table format objects to a series of CSV strings.</span></span> <span data-ttu-id="8a66d-195">`Get-Content`Cmdlet은 테이블 형식 개체를 포함 하는 CSV 파일을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-195">The `Get-Content` cmdlet displays the CSV file which contains the table format objects.</span></span>

### <span data-ttu-id="8a66d-196">예 8: Force 매개 변수를 사용 하 여 읽기 전용 파일 덮어쓰기</span><span class="sxs-lookup"><span data-stu-id="8a66d-196">Example 8: Using the Force parameter to overwrite read-only files</span></span>

<span data-ttu-id="8a66d-197">이 예제에서는 비어 있는 읽기 전용 파일을 만들고 **Force** 매개 변수를 사용 하 여 파일을 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-197">This example creates an empty, read-only file and uses the **Force** parameter to update the file.</span></span>

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

<span data-ttu-id="8a66d-198">`New-Item`Cmdlet은 **Path** 및 **ItemType** 매개 변수를 사용 하 여 현재 디렉터리에 ReadOnly.csv 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-198">The `New-Item` cmdlet uses the **Path** and **ItemType** parameters to create the ReadOnly.csv file in the current directory.</span></span> <span data-ttu-id="8a66d-199">`Set-ItemProperty`Cmdlet은 **Name** 및 **Value** 매개 변수를 사용 하 여 파일의 **IsReadOnly** 속성을 true로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-199">The `Set-ItemProperty` cmdlet uses the **Name** and **Value** parameters to change the file's **IsReadOnly** property to true.</span></span> <span data-ttu-id="8a66d-200">`Get-Process`Cmdlet은 **프로세스** 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-200">The `Get-Process` cmdlet gets **Process** objects.</span></span> <span data-ttu-id="8a66d-201">프로세스 개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Export-Csv` .</span><span class="sxs-lookup"><span data-stu-id="8a66d-201">The process objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="8a66d-202">`Export-Csv` 프로세스 개체를 일련의 CSV 문자열로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-202">`Export-Csv` converts the process objects to a series of CSV strings.</span></span> <span data-ttu-id="8a66d-203">**Path** 매개 변수는 ReadOnly.csv 파일이 현재 디렉터리에 저장 되도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-203">The **Path** parameter specifies that the ReadOnly.csv file is saved in the current directory.</span></span> <span data-ttu-id="8a66d-204">**Notypeinformation** 매개 변수는 CSV 출력에서 **#TYPE** information 헤더를 제거 하며 PowerShell 6에서는 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-204">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="8a66d-205">이 출력은 액세스가 거부 되었기 때문에 파일이 작성 되지 않은 것을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-205">The output shows that the file is not written because access is denied.</span></span>

<span data-ttu-id="8a66d-206">**Force** 매개 변수를 cmdlet에 추가 하 여 `Export-Csv` 내보내기를 강제로 파일에 쓰도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-206">The **Force** parameter is added to the `Export-Csv` cmdlet to force the export to write to the file.</span></span> <span data-ttu-id="8a66d-207">`Get-Content`Cmdlet은 **Path** 매개 변수를 사용 하 여 현재 디렉터리에 있는 파일을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-207">The `Get-Content` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

### <span data-ttu-id="8a66d-208">예 9: Append에 Force 매개 변수 사용</span><span class="sxs-lookup"><span data-stu-id="8a66d-208">Example 9: Using the Force parameter with Append</span></span>

<span data-ttu-id="8a66d-209">이 예제에서는 **Force** 매개 변수를 사용 하 여 매개 변수를 **추가** 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-209">This example shows how to use the **Force** and **Append** parameters.</span></span> <span data-ttu-id="8a66d-210">이러한 매개 변수를 결합 하면 일치 하지 않는 개체 속성을 CSV 파일에 쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-210">When these parameters are combined, mismatched object properties can be written to a CSV file.</span></span>

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

<span data-ttu-id="8a66d-211">식은 **Name** 및 **Version** 속성을 사용 하 여 **PSCustomObject** 를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-211">An expression creates the **PSCustomObject** with **Name** and **Version** properties.</span></span> <span data-ttu-id="8a66d-212">값은 변수에 저장 됩니다 `$Content` .</span><span class="sxs-lookup"><span data-stu-id="8a66d-212">The values are stored in the `$Content` variable.</span></span> <span data-ttu-id="8a66d-213">`$Content`변수가 파이프라인에서 cmdlet으로 전송 됩니다 `Export-Csv` .</span><span class="sxs-lookup"><span data-stu-id="8a66d-213">The `$Content` variable is sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="8a66d-214">`Export-Csv`**Path** 매개 변수를 사용 하 여 현재 디렉터리에 ParmFile.csv 파일을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-214">`Export-Csv` uses the **Path** parameter and saves the ParmFile.csv file in the current directory.</span></span> <span data-ttu-id="8a66d-215">**Notypeinformation** 매개 변수는 CSV 출력에서 **#TYPE** information 헤더를 제거 하며 PowerShell 6에서는 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-215">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span>

<span data-ttu-id="8a66d-216">다른 식은 **Name** 및 **Edition** 속성을 사용 하 여 **PSCustomObject** 를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-216">Another expression creates a **PSCustomObject** with the **Name** and **Edition** properties.</span></span> <span data-ttu-id="8a66d-217">값은 변수에 저장 됩니다 `$AdditionalContent` .</span><span class="sxs-lookup"><span data-stu-id="8a66d-217">The values are stored in the `$AdditionalContent` variable.</span></span> <span data-ttu-id="8a66d-218">`$AdditionalContent`변수가 파이프라인에서 cmdlet으로 전송 됩니다 `Export-Csv` .</span><span class="sxs-lookup"><span data-stu-id="8a66d-218">The `$AdditionalContent` variable is sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="8a66d-219">**추가** 매개 변수는 파일에 데이터를 추가 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-219">The **Append** parameter is used to add the data to the file.</span></span> <span data-ttu-id="8a66d-220">**버전** 및 버전 간에 속성 이름이 일치 하지 않으므로 추가 작업이 **실패 합니다.**</span><span class="sxs-lookup"><span data-stu-id="8a66d-220">The append fails because there is a property name mismatch between **Version** and **Edition** .</span></span>

<span data-ttu-id="8a66d-221">`Export-Csv`Cmdlet **force** 매개 변수를 사용 하 여 내보내기를 강제로 파일에 쓰도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-221">The `Export-Csv` cmdlet **Force** parameter is used to force the export to write to the file.</span></span> <span data-ttu-id="8a66d-222">**Edition** 속성이 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-222">The **Edition** property is discarded.</span></span> <span data-ttu-id="8a66d-223">`Import-Csv`Cmdlet은 **Path** 매개 변수를 사용 하 여 현재 디렉터리에 있는 파일을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-223">The `Import-Csv` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

### <span data-ttu-id="8a66d-224">예 10: 두 열 주위에 따옴표를 사용 하 여 CSV로 내보내기</span><span class="sxs-lookup"><span data-stu-id="8a66d-224">Example 10: Export to CSV with quotes around two columns</span></span>

<span data-ttu-id="8a66d-225">이 예제에서는 **DateTime** 개체를 CSV 문자열로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-225">This example converts a **DateTime** object to a CSV string.</span></span>

```powershell
Get-Date | Export-Csv  -QuoteFields "DateTime","Date" -Path .\FTDateTime.csv
Get-Content -Path .\FTDateTime.csv
```

```Output
DisplayHint,"DateTime","Date",Day,DayOfWeek,DayOfYear,Hour,Kind,Millisecond,Minute,Month,Second,Ticks,TimeOfDay,Year
DateTime,"Thursday, August 22, 2019 11:27:34 AM","8/22/2019 12:00:00 AM",22,Thursday,234,11,Local,569,27,8,34,637020700545699784,11:27:34.5699784,2019
```

### <span data-ttu-id="8a66d-226">예 11: 필요한 경우에만 따옴표를 사용 하 여 CSV로 내보내기</span><span class="sxs-lookup"><span data-stu-id="8a66d-226">Example 11: Export to CSV with quotes only when needed</span></span>

<span data-ttu-id="8a66d-227">이 예제에서는 **DateTime** 개체를 CSV 문자열로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-227">This example converts a **DateTime** object to a CSV string.</span></span>

```powershell
Get-Date | Export-Csv  -UseQuotes AsNeeded -Path .\FTDateTime.csv
Get-Content -Path .\FTDateTime.csv
```

```Output
DisplayHint,DateTime,Date,Day,DayOfWeek,DayOfYear,Hour,Kind,Millisecond,Minute,Month,Second,Ticks,TimeOfDay,Year
DateTime,"Thursday, August 22, 2019 11:31:00 AM",8/22/2019 12:00:00 AM,22,Thursday,234,11,Local,713,31,8,0,637020702607132640,11:31:00.7132640,2019
```

## <span data-ttu-id="8a66d-228">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="8a66d-228">PARAMETERS</span></span>

### <span data-ttu-id="8a66d-229">-추가</span><span class="sxs-lookup"><span data-stu-id="8a66d-229">-Append</span></span>

<span data-ttu-id="8a66d-230">이 매개 변수를 사용 하 여 `Export-CSV` 지정 된 파일의 끝에 CSV 출력을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-230">Use this parameter so that `Export-CSV` adds CSV output to the end of the specified file.</span></span> <span data-ttu-id="8a66d-231">이 매개 변수를 사용 하지 않으면 `Export-CSV` 는 경고 없이 파일 내용을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-231">Without this parameter, `Export-CSV` replaces the file contents without warning.</span></span>

<span data-ttu-id="8a66d-232">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-232">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="8a66d-233">-구분 기호</span><span class="sxs-lookup"><span data-stu-id="8a66d-233">-Delimiter</span></span>

<span data-ttu-id="8a66d-234">속성 값을 구분하는 구분 기호를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-234">Specifies a delimiter to separate the property values.</span></span> <span data-ttu-id="8a66d-235">기본값은 쉼표 ()입니다 `,` .</span><span class="sxs-lookup"><span data-stu-id="8a66d-235">The default is a comma (`,`).</span></span> <span data-ttu-id="8a66d-236">콜론 ()과 같은 문자를 입력 `:` 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-236">Enter a character, such as a colon (`:`).</span></span> <span data-ttu-id="8a66d-237">세미콜론 ()을 지정 하려면 `;` 따옴표로 묶으십시오.</span><span class="sxs-lookup"><span data-stu-id="8a66d-237">To specify a semicolon (`;`), enclose it in quotation marks.</span></span>

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

### <span data-ttu-id="8a66d-238">-Encoding</span><span class="sxs-lookup"><span data-stu-id="8a66d-238">-Encoding</span></span>

<span data-ttu-id="8a66d-239">내보낸 CSV 파일의 인코딩을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-239">Specifies the encoding for the exported CSV file.</span></span> <span data-ttu-id="8a66d-240">기본값은 `utf8NoBOM`입니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-240">The default value is `utf8NoBOM`.</span></span>

<span data-ttu-id="8a66d-241">이 매개 변수에 허용 되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-241">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="8a66d-242">`ascii`: ASCII (7 비트) 문자 집합에 대 한 인코딩을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-242">`ascii`: Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="8a66d-243">`bigendianunicode`: 빅 endian 바이트 순서를 사용 하 여 UTF-16 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-243">`bigendianunicode`: Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="8a66d-244">`oem`: MS-DOS 및 콘솔 프로그램에 기본 인코딩을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-244">`oem`: Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="8a66d-245">`unicode`: 작은 endian 바이트 순서를 사용 하 여 UTF-16 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-245">`unicode`: Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="8a66d-246">`utf7`: UTF-7 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-246">`utf7`: Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="8a66d-247">`utf8`: UTF-8 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-247">`utf8`: Encodes in UTF-8 format.</span></span>
- <span data-ttu-id="8a66d-248">`utf8BOM`: 바이트 순서 표시 (BOM)를 사용 하 여 UTF-8 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-248">`utf8BOM`: Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="8a66d-249">`utf8NoBOM`: BOM (바이트 순서 표시) 없이 UTF-8 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-249">`utf8NoBOM`: Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="8a66d-250">`utf32`: U t f-32 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-250">`utf32`: Encodes in UTF-32 format.</span></span>

<span data-ttu-id="8a66d-251">PowerShell 6.2부터 **Encoding** 매개 변수를 사용 하 여 등록 된 코드 페이지의 숫자 id (예: `-Encoding 1251` ) 또는 등록 된 코드 페이지의 문자열 이름을 사용할 수도 있습니다 (예: `-Encoding "windows-1251"` ).</span><span class="sxs-lookup"><span data-stu-id="8a66d-251">Beginning with PowerShell 6.2, the **Encoding** parameter also allows numeric IDs of registered code pages (like `-Encoding 1251`) or string names of registered code pages (like `-Encoding "windows-1251"`).</span></span> <span data-ttu-id="8a66d-252">자세한 내용은 [인코딩에](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2)대 한 .net 설명서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8a66d-252">For more information, see the .NET documentation for [Encoding.CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span></span>

```yaml
Type: System.Text.Encoding
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: Named
Default value: UTF8NoBOM
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8a66d-253">-Force</span><span class="sxs-lookup"><span data-stu-id="8a66d-253">-Force</span></span>

<span data-ttu-id="8a66d-254">이 매개 변수 `Export-Csv` 를 사용 하면 **읽기 전용** 특성으로 파일을 덮어쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-254">This parameter allows `Export-Csv` to overwrite files with the **Read Only** attribute.</span></span>

<span data-ttu-id="8a66d-255">**Force** 및 **Append** 매개 변수를 결합 하면 일치 하지 않는 속성을 포함 하는 개체를 CSV 파일에 쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-255">When **Force** and **Append** parameters are combined, objects that contain mismatched properties can be written to a CSV file.</span></span> <span data-ttu-id="8a66d-256">일치 하는 속성만 파일에 기록 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-256">Only the properties that match are written to the file.</span></span> <span data-ttu-id="8a66d-257">일치 하지 않는 속성은 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-257">The mismatched properties are discarded.</span></span>

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

### <span data-ttu-id="8a66d-258">-IncludeTypeInformation</span><span class="sxs-lookup"><span data-stu-id="8a66d-258">-IncludeTypeInformation</span></span>

<span data-ttu-id="8a66d-259">이 매개 변수를 사용 하면 CSV 출력의 첫 번째 줄에 **#TYPE** 와 개체 형식의 정규화 된 이름이 차례로 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-259">When this parameter is used the first line of the CSV output contains **#TYPE** followed by the fully qualified name of the object type.</span></span> <span data-ttu-id="8a66d-260">예를 들어, **#TYPE를 처리** 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-260">For example, **#TYPE System.Diagnostics.Process** .</span></span>

<span data-ttu-id="8a66d-261">이 매개 변수는 PowerShell 6.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-261">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: ITI

Required: False
Position: Named
Default value: #TYPE <Object>
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8a66d-262">-InputObject</span><span class="sxs-lookup"><span data-stu-id="8a66d-262">-InputObject</span></span>

<span data-ttu-id="8a66d-263">CSV 문자열로 내보낼 개체를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-263">Specifies the objects to export as CSV strings.</span></span> <span data-ttu-id="8a66d-264">개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="8a66d-264">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span> <span data-ttu-id="8a66d-265">개체를로 파이프 할 수도 있습니다 `Export-CSV` .</span><span class="sxs-lookup"><span data-stu-id="8a66d-265">You can also pipe objects to `Export-CSV`.</span></span>

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

### <span data-ttu-id="8a66d-266">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="8a66d-266">-LiteralPath</span></span>

<span data-ttu-id="8a66d-267">CSV 출력 파일의 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-267">Specifies the path to the CSV output file.</span></span> <span data-ttu-id="8a66d-268">**Path** 와 달리 **LiteralPath** 매개 변수 값은 입력한 대로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-268">Unlike **Path** , the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="8a66d-269">어떠한 문자도 와일드카드로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-269">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="8a66d-270">경로에 이스케이프 문자가 포함 된 경우 작은따옴표를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-270">If the path includes escape characters, use single quotation marks.</span></span> <span data-ttu-id="8a66d-271">작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-271">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSPath, LP

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8a66d-272">-NoClobber</span><span class="sxs-lookup"><span data-stu-id="8a66d-272">-NoClobber</span></span>

<span data-ttu-id="8a66d-273">이 매개 변수를 사용 하 여 `Export-CSV` 기존 파일을 덮어쓰지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-273">Use this parameter so that `Export-CSV` does not overwrite an existing file.</span></span> <span data-ttu-id="8a66d-274">기본적으로 지정 된 경로에 파일이 있으면는 `Export-CSV` 경고 없이 파일을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-274">By default, if the file exists in the specified path, `Export-CSV` overwrites the file without warning.</span></span>

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

### <span data-ttu-id="8a66d-275">-NoTypeInformation</span><span class="sxs-lookup"><span data-stu-id="8a66d-275">-NoTypeInformation</span></span>

<span data-ttu-id="8a66d-276">출력에서 **#TYPE** 정보 헤더를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-276">Removes the **#TYPE** information header from the output.</span></span> <span data-ttu-id="8a66d-277">이 매개 변수는 PowerShell 6.0의 기본값이 며 이전 버전과의 호환성을 위해 포함 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-277">This parameter became the default in PowerShell 6.0 and is included for backwards compatibility.</span></span>

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

### <span data-ttu-id="8a66d-278">-Path</span><span class="sxs-lookup"><span data-stu-id="8a66d-278">-Path</span></span>

<span data-ttu-id="8a66d-279">CSV 출력 파일을 저장할 위치를 지정 하는 필수 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-279">A required parameter that specifies the location to save the CSV output file.</span></span>

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

### <span data-ttu-id="8a66d-280">-UseCulture</span><span class="sxs-lookup"><span data-stu-id="8a66d-280">-UseCulture</span></span>

<span data-ttu-id="8a66d-281">현재 문화권의 목록 구분 기호를 항목 구분 기호로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-281">Uses the list separator for the current culture as the item delimiter.</span></span> <span data-ttu-id="8a66d-282">문화권에 대 한 목록 구분 기호를 찾으려면 다음 명령을 사용 합니다. `(Get-Culture).TextInfo.ListSeparator`</span><span class="sxs-lookup"><span data-stu-id="8a66d-282">To find the list separator for a culture, use the following command: `(Get-Culture).TextInfo.ListSeparator`.</span></span>

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

### <span data-ttu-id="8a66d-283">-Confirm</span><span class="sxs-lookup"><span data-stu-id="8a66d-283">-Confirm</span></span>

<span data-ttu-id="8a66d-284">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-284">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="8a66d-285">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="8a66d-285">-WhatIf</span></span>

<span data-ttu-id="8a66d-286">Cmdlet이 처리 되지 않거나 변경 되지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-286">Prevents the cmdlet from being processed or making changes.</span></span> <span data-ttu-id="8a66d-287">출력은 cmdlet이 실행 될 때 발생 하는 상황을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-287">The output shows what would happen if the cmdlet were run.</span></span>

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

### <span data-ttu-id="8a66d-288">-QuoteFields</span><span class="sxs-lookup"><span data-stu-id="8a66d-288">-QuoteFields</span></span>

<span data-ttu-id="8a66d-289">따옴표로 묶을 열의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-289">Specifies the names of the columns that should be quoted.</span></span> <span data-ttu-id="8a66d-290">이 매개 변수를 사용 하면 지정 된 열만 따옴표로 묶여 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-290">When this parameter is used, only the specified columns are quoted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: QF

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8a66d-291">-UseQuotes 기술</span><span class="sxs-lookup"><span data-stu-id="8a66d-291">-UseQuotes</span></span>

<span data-ttu-id="8a66d-292">CSV 파일에서 따옴표를 사용 하는 경우를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-292">Specifies when quotes are used in the CSV files.</span></span> <span data-ttu-id="8a66d-293">가능한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-293">Possible values are:</span></span>

- <span data-ttu-id="8a66d-294">안 함-아무것도 인용 하지 않음</span><span class="sxs-lookup"><span data-stu-id="8a66d-294">Never - don't quote anything</span></span>
- <span data-ttu-id="8a66d-295">항상 따옴표 모든 항목 (기본 동작)</span><span class="sxs-lookup"><span data-stu-id="8a66d-295">Always - quote everything (default behavior)</span></span>
- <span data-ttu-id="8a66d-296">AsNeeded-구분 문자를 포함 하는 견적 필드만</span><span class="sxs-lookup"><span data-stu-id="8a66d-296">AsNeeded - only quote fields that contain a delimiter character</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.BaseCsvWritingCommand+QuoteKind
Parameter Sets: (All)
Aliases: UQ

Required: False
Position: Named
Default value: Always
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8a66d-297">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8a66d-297">CommonParameters</span></span>

<span data-ttu-id="8a66d-298">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="8a66d-298">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8a66d-299">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8a66d-299">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8a66d-300">입력</span><span class="sxs-lookup"><span data-stu-id="8a66d-300">INPUTS</span></span>

### <span data-ttu-id="8a66d-301">System.web. PSObject</span><span class="sxs-lookup"><span data-stu-id="8a66d-301">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="8a66d-302">Any (확장 형식 시스템) 어댑터를 사용 하 여 개체를로 파이프 할 수 있습니다 `Export-CSV` .</span><span class="sxs-lookup"><span data-stu-id="8a66d-302">You can pipe any object with an Extended Type System (ETS) adapter to `Export-CSV`.</span></span>

## <span data-ttu-id="8a66d-303">출력</span><span class="sxs-lookup"><span data-stu-id="8a66d-303">OUTPUTS</span></span>

### <span data-ttu-id="8a66d-304">System.String</span><span class="sxs-lookup"><span data-stu-id="8a66d-304">System.String</span></span>

<span data-ttu-id="8a66d-305">CSV 목록이 Path 매개 변수에 지정된 파일로 보내집니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-305">The CSV list is sent to the file designated in the Path parameter.</span></span>

## <span data-ttu-id="8a66d-306">참고</span><span class="sxs-lookup"><span data-stu-id="8a66d-306">NOTES</span></span>

<span data-ttu-id="8a66d-307">`Export-CSV`Cmdlet은 제출한 개체를 일련의 CSV 문자열로 변환 하 고 지정 된 텍스트 파일에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-307">The `Export-CSV` cmdlet converts the objects that you submit into a series of CSV strings and saves them in the specified text file.</span></span> <span data-ttu-id="8a66d-308">`Export-CSV -IncludeTypeInformation`를 사용 하 여 개체를 csv 파일에 저장 한 다음 cmdlet을 사용 하 여 `Import-Csv` csv 파일의 텍스트에서 개체를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-308">You can use `Export-CSV -IncludeTypeInformation` to save objects in a CSV file and then use the `Import-Csv` cmdlet to create objects from the text in the CSV file.</span></span>

<span data-ttu-id="8a66d-309">CSV 파일에서 각 개체는 쉼표로 구분된 개체 속성 값 목록으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-309">In the CSV file, each object is represented by a comma-separated list of the property values of the object.</span></span> <span data-ttu-id="8a66d-310">속성 값은 **ToString ()** 메서드를 사용 하 여 문자열로 변환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-310">The property values are converted to strings using the **ToString()** method.</span></span> <span data-ttu-id="8a66d-311">문자열은 속성 값 이름으로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-311">The strings are represented by the property value name.</span></span> <span data-ttu-id="8a66d-312">`Export-CSV -IncludeTypeInformation` 는 개체의 메서드를 내보내지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-312">`Export-CSV -IncludeTypeInformation` does not export the methods of the object.</span></span>

<span data-ttu-id="8a66d-313">CSV 문자열은 다음과 같이 출력 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-313">The CSV strings are output as follows:</span></span>

- <span data-ttu-id="8a66d-314">**Includetypeinformation** 이 사용 되는 경우 첫 번째 문자열에는 **#TYPE** information 헤더와 개체 형식의 정규화 된 이름이 차례로 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-314">If **IncludeTypeInformation** is used, the first string contains the **#TYPE** information header followed by the object type's fully qualified name.</span></span>
  <span data-ttu-id="8a66d-315">예를 들어, **#TYPE를 처리** 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-315">For example, **#TYPE System.Diagnostics.Process** .</span></span>
- <span data-ttu-id="8a66d-316">**Includetypeinformation** 을 사용 하지 않으면 첫 번째 문자열에 열 머리글이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-316">If **IncludeTypeInformation** is not used the first string includes the column headers.</span></span> <span data-ttu-id="8a66d-317">헤더는 첫 번째 개체의 속성 이름을 쉼표로 구분 된 목록으로 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-317">The headers contain the first object's property names as a comma-separated list.</span></span>
- <span data-ttu-id="8a66d-318">나머지 문자열은 각 개체의 속성 값에 대 한 쉼표로 구분 된 목록을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-318">The remaining strings contain comma-separated lists of each object's property values.</span></span>

<span data-ttu-id="8a66d-319">PowerShell 6.0부터의 기본 동작은 `Export-CSV` CSV에 **#TYPE** 정보를 포함 하지 않는 것이 고 **notypeinformation** 이 암시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-319">Beginning with PowerShell 6.0 the default behavior of `Export-CSV` is to not include the **#TYPE** information in the CSV and **NoTypeInformation** is implied.</span></span> <span data-ttu-id="8a66d-320">**Includetypeinformation** 은 **#TYPE** 정보를 포함 하 고 PowerShell 6.0 이전의 기본 동작을 에뮬레이트하는 데 사용할 수 있습니다 `Export-CSV` .</span><span class="sxs-lookup"><span data-stu-id="8a66d-320">**IncludeTypeInformation** can be used to include the **#TYPE** Information and emulate the default behavior of `Export-CSV` prior to PowerShell 6.0.</span></span>

<span data-ttu-id="8a66d-321">여러 개체를에 제출할 때 `Export-CSV` 는 `Export-CSV` 제출한 첫 번째 개체의 속성을 기반으로 파일을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-321">When you submit multiple objects to `Export-CSV`, `Export-CSV` organizes the file based on the properties of the first object that you submit.</span></span> <span data-ttu-id="8a66d-322">나머지 개체에 지정된 속성 중 하나가 없는 경우 해당 개체의 속성 값은 null이며, 두 개의 연속된 쉼표로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-322">If the remaining objects do not have one of the specified properties, the property value of that object is null, as represented by two consecutive commas.</span></span> <span data-ttu-id="8a66d-323">나머지 개체에 추가 속성이 있을 경우 이러한 속성 값은 파일에 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-323">If the remaining objects have additional properties, those property values are not included in the file.</span></span>

<span data-ttu-id="8a66d-324">Cmdlet을 사용 `Import-Csv` 하 여 파일에 있는 CSV 문자열에서 개체를 다시 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-324">You can use the `Import-Csv` cmdlet to recreate objects from the CSV strings in the files.</span></span> <span data-ttu-id="8a66d-325">결과 개체는 속성 값(메서드는 포함 안 됨)의 문자열 표시로 이루어진 원래 개체의 CSV 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-325">The resulting objects are CSV versions of the original objects that consist of string representations of the property values and no methods.</span></span>

<span data-ttu-id="8a66d-326">및 cmdlet은 개체를 csv 문자열과 csv 문자열로 `ConvertTo-Csv` `ConvertFrom-Csv` 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-326">The `ConvertTo-Csv` and `ConvertFrom-Csv` cmdlets convert objects to CSV strings and from CSV strings.</span></span> <span data-ttu-id="8a66d-327">`Export-CSV` 은 `ConvertTo-CSV` CSV 문자열을 파일에 저장 한다는 점을 제외 하 고와 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a66d-327">`Export-CSV` is the same as `ConvertTo-CSV`, except that it saves the CSV strings in a file.</span></span>

## <span data-ttu-id="8a66d-328">관련 링크</span><span class="sxs-lookup"><span data-stu-id="8a66d-328">RELATED LINKS</span></span>

[<span data-ttu-id="8a66d-329">ConvertFrom-Csv</span><span class="sxs-lookup"><span data-stu-id="8a66d-329">ConvertFrom-Csv</span></span>](ConvertFrom-Csv.md)

[<span data-ttu-id="8a66d-330">ConvertTo-Csv</span><span class="sxs-lookup"><span data-stu-id="8a66d-330">ConvertTo-Csv</span></span>](ConvertTo-Csv.md)

[<span data-ttu-id="8a66d-331">Format-Table</span><span class="sxs-lookup"><span data-stu-id="8a66d-331">Format-Table</span></span>](Format-Table.md)

[<span data-ttu-id="8a66d-332">Import-Csv</span><span class="sxs-lookup"><span data-stu-id="8a66d-332">Import-Csv</span></span>](Import-Csv.md)

[<span data-ttu-id="8a66d-333">Select-Object</span><span class="sxs-lookup"><span data-stu-id="8a66d-333">Select-Object</span></span>](Select-Object.md)
