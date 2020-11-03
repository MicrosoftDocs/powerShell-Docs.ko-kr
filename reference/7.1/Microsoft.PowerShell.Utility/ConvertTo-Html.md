---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertto-html?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-Html
ms.openlocfilehash: 27a1d2994dee46b9e5bfd54132ff4a665330c2b4
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/10/2020
ms.locfileid: "93219417"
---
# <span data-ttu-id="46622-103">ConvertTo-Html</span><span class="sxs-lookup"><span data-stu-id="46622-103">ConvertTo-Html</span></span>

## <span data-ttu-id="46622-104">개요</span><span class="sxs-lookup"><span data-stu-id="46622-104">SYNOPSIS</span></span>
<span data-ttu-id="46622-105">.NET 개체를 웹 브라우저에 표시할 수 있는 HTML로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="46622-105">Converts .NET objects into HTML that can be displayed in a Web browser.</span></span>

## <span data-ttu-id="46622-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="46622-106">SYNTAX</span></span>

### <span data-ttu-id="46622-107">페이지 (기본값)</span><span class="sxs-lookup"><span data-stu-id="46622-107">Page (Default)</span></span>

```
ConvertTo-Html [-InputObject <PSObject>] [[-Property] <Object[]>] [[-Body] <String[]>]
 [[-Head] <String[]>] [[-Title] <String>] [-As <String>] [-CssUri <Uri>] [-PostContent <String[]>]
 [-PreContent <String[]>] [-Meta <Hashtable>] [-Charset <String>] [-Transitional]
 [<CommonParameters>]
```

### <span data-ttu-id="46622-108">Fragment</span><span class="sxs-lookup"><span data-stu-id="46622-108">Fragment</span></span>

```
ConvertTo-Html [-InputObject <PSObject>] [[-Property] <Object[]>] [-As <String>] [-Fragment]
 [-PostContent <String[]>] [-PreContent <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="46622-109">설명</span><span class="sxs-lookup"><span data-stu-id="46622-109">DESCRIPTION</span></span>

<span data-ttu-id="46622-110">`ConvertTo-Html`Cmdlet은 .net 개체를 웹 브라우저에 표시할 수 있는 HTML로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="46622-110">The `ConvertTo-Html` cmdlet converts .NET objects into HTML that can be displayed in a Web browser.</span></span> <span data-ttu-id="46622-111">이 cmdlet을 사용하여 명령 출력을 웹 페이지에 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46622-111">You can use this cmdlet to display the output of a command in a Web page.</span></span>

<span data-ttu-id="46622-112">의 매개 변수를 사용 하 여 `ConvertTo-Html` 개체 속성을 선택 하 고, 테이블 또는 목록 형식을 지정 하 고, HTML 페이지 제목을 지정 하 고, 개체 앞뒤에 텍스트를 추가 하 고, STRICT DTD 페이지 대신 테이블 또는 목록 조각만 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46622-112">You can use the parameters of `ConvertTo-Html` to select object properties, to specify a table or list format, to specify the HTML page title, to add text before and after the object, and to return only the table or list fragment, instead of a strict DTD page.</span></span>

<span data-ttu-id="46622-113">에 여러 개체를 제출 하는 경우 `ConvertTo-Html` PowerShell은 제출한 첫 번째 개체의 속성을 기반으로 테이블 (또는 목록)을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="46622-113">When you submit multiple objects to `ConvertTo-Html`, PowerShell creates the table (or list) based on the properties of the first object that you submit.</span></span> <span data-ttu-id="46622-114">나머지 개체에 지정한 속성이 하나도 없을 경우 해당 개체의 속성 값은 빈 셀이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="46622-114">If the remaining objects do not have one of the specified properties, the property value of that object is an empty cell.</span></span> <span data-ttu-id="46622-115">나머지 개체에 추가 속성이 있을 경우 이러한 속성 값은 파일에 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="46622-115">If the remaining objects have additional properties, those property values are not included in the file.</span></span>

## <span data-ttu-id="46622-116">예제</span><span class="sxs-lookup"><span data-stu-id="46622-116">EXAMPLES</span></span>

### <span data-ttu-id="46622-117">예제 1: 날짜를 표시 하는 웹 페이지 만들기</span><span class="sxs-lookup"><span data-stu-id="46622-117">Example 1: Create a web page to display the date</span></span>

```powershell
ConvertTo-Html -InputObject (Get-Date)
```

<span data-ttu-id="46622-118">이 명령은 현재 날짜의 속성을 표시하는 HTML 페이지를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="46622-118">This command creates an HTML page that displays the properties of the current date.</span></span> <span data-ttu-id="46622-119">**InputObject** 매개 변수를 사용 하 여 명령의 결과를 `Get-Date` cmdlet에 제출 `ConvertTo-Html` 합니다.</span><span class="sxs-lookup"><span data-stu-id="46622-119">It uses the **InputObject** parameter to submit the results of a `Get-Date` command to the `ConvertTo-Html` cmdlet.</span></span>

### <span data-ttu-id="46622-120">예제 2: PowerShell 별칭을 표시 하는 웹 페이지 만들기</span><span class="sxs-lookup"><span data-stu-id="46622-120">Example 2: Create a web page to display PowerShell aliases</span></span>

```powershell
Get-Alias | ConvertTo-Html | Out-File aliases.htm
Invoke-Item aliases.htm
```

<span data-ttu-id="46622-121">이 명령은 현재 콘솔의 PowerShell 별칭을 나열 하는 HTML 페이지를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="46622-121">This command creates an HTML page that lists the PowerShell aliases in the current console.</span></span>

<span data-ttu-id="46622-122">이 명령은 cmdlet을 사용 하 여 `Get-Alias` 별칭을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="46622-122">The command uses the `Get-Alias` cmdlet to get the aliases.</span></span> <span data-ttu-id="46622-123">파이프라인 연산자 ()를 사용 하 여 `|` 별칭을 cmdlet으로 보내면이 `ConvertTo-Html` CMDLET이 HTML 페이지를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="46622-123">It uses the pipeline operator (`|`) to send the aliases to the `ConvertTo-Html` cmdlet, which creates the HTML page.</span></span> <span data-ttu-id="46622-124">또한이 명령은 cmdlet을 사용 하 여 `Out-File` HTML 코드를 파일에 보냅니다 `aliases.htm` .</span><span class="sxs-lookup"><span data-stu-id="46622-124">The command also uses the `Out-File` cmdlet to send the HTML code to the `aliases.htm` file.</span></span>

### <span data-ttu-id="46622-125">예제 3: PowerShell 이벤트를 표시 하는 웹 페이지 만들기</span><span class="sxs-lookup"><span data-stu-id="46622-125">Example 3: Create a web page to display PowerShell events</span></span>

```powershell
`Get-EventLog` -LogName "Windows PowerShell" | ConvertTo-Html | Out-File pslog.htm
```

<span data-ttu-id="46622-126">이 명령은 `pslog.htm` 로컬 컴퓨터의 Windows PowerShell 이벤트 로그에 이벤트를 표시 하는 이라는 HTML 페이지를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="46622-126">This command creates an HTML page called `pslog.htm` that displays the events in the Windows PowerShell event log on the local computer.</span></span>

<span data-ttu-id="46622-127">Cmdlet을 사용 하 여 `Get-EventLog` Windows PowerShell 로그의 이벤트를 가져온 다음 파이프라인 연산자 ()를 사용 하 여 `|` 이벤트를 cmdlet으로 보냅니다 `ConvertTo-Html` .</span><span class="sxs-lookup"><span data-stu-id="46622-127">It uses the `Get-EventLog` cmdlet to get the events in the Windows PowerShell log and then uses the pipeline operator (`|`) to send the events to the `ConvertTo-Html` cmdlet.</span></span> <span data-ttu-id="46622-128">또한이 명령은 cmdlet을 사용 하 여 `Out-File` HTML 코드를 파일에 보냅니다 `pslog.htm` .</span><span class="sxs-lookup"><span data-stu-id="46622-128">The command also uses the `Out-File` cmdlet to send the HTML code to the `pslog.htm` file.</span></span>

<span data-ttu-id="46622-129">또한이 명령은 cmdlet을 사용 하 여 `Out-File` HTML 코드를 파일에 보냅니다 `pslog.htm` .</span><span class="sxs-lookup"><span data-stu-id="46622-129">The command also uses the `Out-File` cmdlet to send the HTML code to the `pslog.htm` file.</span></span>

### <span data-ttu-id="46622-130">예제 4: 프로세스를 표시 하는 웹 페이지 만들기</span><span class="sxs-lookup"><span data-stu-id="46622-130">Example 4: Create a web page to display processes</span></span>

```powershell
Get-Process |
  ConvertTo-Html -Property Name, Path, Company -Title "Process Information" |
    Out-File proc.htm
Invoke-Item proc.htm
```

<span data-ttu-id="46622-131">이 명령은 로컬 컴퓨터에 있는 프로세스의 이름, 경로 및 회사를 나열하는 HTML 페이지를 만들어서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="46622-131">These commands create and open an HTML page that lists the name, path, and company of the processes on the local computer.</span></span>

<span data-ttu-id="46622-132">첫 번째 명령은 cmdlet을 사용 하 여 `Get-Process` 컴퓨터에서 실행 중인 프로세스를 나타내는 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="46622-132">The first command uses the `Get-Process` cmdlet to get objects that represent the processes running on the computer.</span></span> <span data-ttu-id="46622-133">이 명령은 파이프라인 연산자 ()를 사용 하 여 `|` 프로세스 개체를 cmdlet으로 보냅니다 `ConvertTo-Html` .</span><span class="sxs-lookup"><span data-stu-id="46622-133">The command uses the pipeline operator (`|`) to send the process objects to the `ConvertTo-Html` cmdlet.</span></span>

<span data-ttu-id="46622-134">이 명령은 **Property** 매개 변수를 사용 하 여 테이블에 포함할 프로세스 개체의 세 가지 속성을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="46622-134">The command uses the **Property** parameter to select three properties of the process objects to be included in the table.</span></span> <span data-ttu-id="46622-135">이 명령은 **title** 매개 변수를 사용 하 여 HTML 페이지의 제목을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="46622-135">The command uses the **Title** parameter to specify a title for the HTML page.</span></span> <span data-ttu-id="46622-136">또한이 명령은 cmdlet을 사용 하 여 `Out-File` 결과 HTML을 Proc.htm 이라는 파일로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="46622-136">The command also uses the `Out-File` cmdlet to send the resulting HTML to a file named Proc.htm.</span></span>

<span data-ttu-id="46622-137">두 번째 명령은 cmdlet을 사용 하 여 `Invoke-Item` 를 `Proc.htm` 기본 브라우저에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="46622-137">The second command uses the `Invoke-Item` cmdlet to open the `Proc.htm` in the default browser.</span></span>

### <span data-ttu-id="46622-138">예 5: 서비스 개체를 표시 하는 웹 페이지 만들기</span><span class="sxs-lookup"><span data-stu-id="46622-138">Example 5: Create a web page to display service objects</span></span>

```powershell
Get-Service | ConvertTo-Html -CssUri "test.css"
```

```Output
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"  "https://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html>
<head>
<title>HTML TABLE</title>
<link rel="stylesheet" type="text/css" href="test.css" />
...
```

<span data-ttu-id="46622-139">이 명령은 cmdlet이 반환 하는 서비스 개체의 HTML 페이지를 만듭니다 `Get-Service` .</span><span class="sxs-lookup"><span data-stu-id="46622-139">This command creates an HTML page of the service objects that the `Get-Service` cmdlet returns.</span></span> <span data-ttu-id="46622-140">이 명령은 **CssUri** 매개 변수를 사용 하 여 HTML 페이지의 css 스타일 시트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="46622-140">The command uses the **CssUri** parameter to specify a cascading style sheet for the HTML page.</span></span>

<span data-ttu-id="46622-141">**CssUri** 매개 변수는 `<link rel="stylesheet" type="text/css" href="test.css">` 결과 HTML에 추가 태그를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="46622-141">The **CssUri** parameter adds an additional `<link rel="stylesheet" type="text/css" href="test.css">` tag to the resulting HTML.</span></span> <span data-ttu-id="46622-142">태그의 HREF 특성에는 스타일시트의 이름이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="46622-142">The HREF attribute in the tag contains the name of the style sheet.</span></span>

### <span data-ttu-id="46622-143">예제 6: 서비스 개체를 표시 하는 웹 페이지 만들기</span><span class="sxs-lookup"><span data-stu-id="46622-143">Example 6: Create a web page to display service objects</span></span>

```powershell
Get-Service | ConvertTo-Html -As LIST | Out-File services.htm
```

<span data-ttu-id="46622-144">이 명령은 cmdlet이 반환 하는 서비스 개체의 HTML 페이지를 만듭니다 `Get-Service` .</span><span class="sxs-lookup"><span data-stu-id="46622-144">This command creates an HTML page of the service objects that the `Get-Service` cmdlet returns.</span></span> <span data-ttu-id="46622-145">이 명령은 **As** 매개 변수를 사용 하 여 목록 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="46622-145">The command uses the **As** parameter to specify a list format.</span></span> <span data-ttu-id="46622-146">Cmdlet은 `Out-File` 결과 HTML을 파일에 보냅니다 `Services.htm` .</span><span class="sxs-lookup"><span data-stu-id="46622-146">The cmdlet `Out-File` sends the resulting HTML to the `Services.htm` file.</span></span>

### <span data-ttu-id="46622-147">예 7: 현재 날짜에 대 한 웹 테이블 만들기</span><span class="sxs-lookup"><span data-stu-id="46622-147">Example 7: Create a web table for the current date</span></span>

```powershell
Get-Date | ConvertTo-Html -Fragment
```

```Output
<table>
<colgroup>...</colgroup>
<tr><th>DisplayHint</th><th>DateTime</th><th>Date</th><th>Day</th><th>DayOfWeek</th><th>DayOfYear</th><th>Hour</th>
<th>Kind</th><th>Millisecond</th><th>Minute</th><th>Month</th><th>Second</th><th>Ticks</th><th>TimeOfDay</th><th>Year</th></tr>
<tr><td>DateTime</td><td>Monday, May 05, 2008 10:40:04 AM</td><td>5/5/2008 12:00:00 AM</td><td>5</td><td>Monday</td>
<td>126</td><td>10</td><td>Local</td><td>123</td><td>40</td><td>5</td><td>4</td><td>633455808041237213</td><td>10:40:04.12
37213</td><td>2008</td></tr>
</table>
```

<span data-ttu-id="46622-148">이 명령은 `ConvertTo-Html` 를 사용 하 여 현재 날짜의 HTML 테이블을 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="46622-148">This command uses `ConvertTo-Html` to generate an HTML table of the current date.</span></span> <span data-ttu-id="46622-149">이 명령은 cmdlet을 사용 하 여 `Get-Date` 현재 날짜를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="46622-149">The command uses the `Get-Date` cmdlet to get the current date.</span></span> <span data-ttu-id="46622-150">파이프라인 연산자 (|)를 사용 하 여 결과를 cmdlet으로 보냅니다 `ConvertTo-Html` .</span><span class="sxs-lookup"><span data-stu-id="46622-150">It uses a pipeline operator (|) to send the results to the `ConvertTo-Html` cmdlet.</span></span>

<span data-ttu-id="46622-151">이 `ConvertTo-Html` 명령은 출력을 HTML 테이블로 제한 하는 **Fragment** 매개 변수를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="46622-151">The `ConvertTo-Html` command includes the **Fragment** parameter, which limits the output to an HTML table.</span></span> <span data-ttu-id="46622-152">따라서 `<HEAD>` 및 `<BODY>` 태그와 같은 HTML 페이지의 다른 요소는 생략됩니다.</span><span class="sxs-lookup"><span data-stu-id="46622-152">As a result, the other elements of an HTML page, such as the `<HEAD>` and `<BODY>` tags, are omitted.</span></span>

### <span data-ttu-id="46622-153">예 8: PowerShell 이벤트를 표시 하는 웹 페이지 만들기</span><span class="sxs-lookup"><span data-stu-id="46622-153">Example 8: Create a web page to display PowerShell events</span></span>

```powershell
Get-EventLog -Log "Windows PowerShell" | ConvertTo-Html -Property id, level, task
```

<span data-ttu-id="46622-154">이 명령은 cmdlet을 사용 하 여 `Get-EventLog` Windows PowerShell 이벤트 로그에서 이벤트를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="46622-154">This command uses the `Get-EventLog` cmdlet to get events from the Windows PowerShell event log.</span></span>

<span data-ttu-id="46622-155">파이프라인 연산자 ()를 사용 하 여 `|` 이벤트를 cmdlet으로 보내면이 `ConvertTo-Html` cmdlet이 이벤트를 HTML 형식으로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="46622-155">It uses a pipeline operator (`|`) to send the events to the `ConvertTo-Html` cmdlet, which converts the events to HTML format.</span></span>

<span data-ttu-id="46622-156">`ConvertTo-Html`이 명령은 **Property** 매개 변수를 사용 하 여 이벤트의 **ID** , **Level** 및 **Task** 속성만 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="46622-156">The `ConvertTo-Html` command uses the **Property** parameter to select only the **ID** , **Level** , and **Task** properties of the event.</span></span>

### <span data-ttu-id="46622-157">예 9: 지정 된 서비스를 표시 하는 웹 페이지 만들기</span><span class="sxs-lookup"><span data-stu-id="46622-157">Example 9: Create a web page to display specified services</span></span>

```powershell
$htmlParams = @{
  Title = "Windows Services: Server01"
  Body = Get-Date
  PreContent = "<P>Generated by Corporate IT</P>"
  PostContent = "For details, contact Corporate IT."
}
Get-Service A* |
  ConvertTo-Html @htmlParams |
    Out-File Services.htm
Invoke-Item Services.htm
```

<span data-ttu-id="46622-158">이 명령은로 시작 하는 컴퓨터의 서비스를 표시 하는 웹 페이지를 만들고 엽니다. 의 **Title** , **Body** , **precontent** 및 **postcontent** 매개 변수를 사용 하 여 `ConvertTo-Html` 출력을 사용자 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="46622-158">This command creates and opens a Web page that displays the services on the computer that begin with A. It uses the **Title** , **Body** , **PreContent** , and **PostContent** parameters of `ConvertTo-Html` to customize the output.</span></span>

<span data-ttu-id="46622-159">명령의 첫 번째 부분에서는 cmdlet을 사용 하 여 `Get-Service` 로 시작 하는 컴퓨터의 서비스를 가져옵니다. 이 명령은 파이프라인 연산자 ()를 사용 하 여 `|` 결과를 cmdlet으로 보냅니다 `ConvertTo-Html` .</span><span class="sxs-lookup"><span data-stu-id="46622-159">The first part of the command uses the `Get-Service` cmdlet to get the services on the computer that begin with A. The command uses a pipeline operator (`|`) to send the results to the `ConvertTo-Html` cmdlet.</span></span> <span data-ttu-id="46622-160">또한이 명령은 cmdlet을 사용 하 여 `Out-File` 출력을 Services.htm 파일로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="46622-160">The command also uses the `Out-File` cmdlet to send the output to the Services.htm file.</span></span>

<span data-ttu-id="46622-161">세미콜론 ( `;` )을 사용 하면 첫 번째 명령이 끝나고 두 번째 명령이 시작 됩니다 .이 명령은 cmdlet을 사용 하 여 `Invoke-Item` `Services.htm` 기본 브라우저에서 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="46622-161">A semicolon (`;`) ends the first command and starts a second command, which uses the `Invoke-Item` cmdlet to open the `Services.htm` file in the default browser.</span></span>

### <span data-ttu-id="46622-162">예 10: HTML의 Meta 속성 및 문자 집합 설정</span><span class="sxs-lookup"><span data-stu-id="46622-162">Example 10: Set the Meta properties and Charset of the HTML</span></span>

```powershell
Get-Service | ConvertTo-HTML -Meta @{
  refresh=10
  author="Author's Name"
  keywords="PowerShell, HTML, ConvertTo-HTML"
} -Charset "UTF-8"
```

<span data-ttu-id="46622-163">이 명령은 새로 고침, 만든이 및 키워드에 대 한 메타 태그를 사용 하 여 웹 페이지에 대 한 HTML을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="46622-163">This command creates the HTML for a webpage with the meta tags for refresh, author, and keywords.</span></span>
<span data-ttu-id="46622-164">페이지의 문자 집합은 u t f-8로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="46622-164">The charset for the page is set to UTF-8</span></span>

### <span data-ttu-id="46622-165">예 11: HTML을 XHTML 전환 DTD로 설정</span><span class="sxs-lookup"><span data-stu-id="46622-165">Example 11: Set the HTML to XHTML Transitional DTD</span></span>

```powershell
Get-Service | ConvertTo-HTML -Transitional
```

<span data-ttu-id="46622-166">이 명령은 반환 된 HTML의 DOCTYPE을 XHTML 전환 DTD로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="46622-166">This command sets the DOCTYPE of the returned HTML to XHTML Transitional DTD</span></span>

## <span data-ttu-id="46622-167">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="46622-167">PARAMETERS</span></span>

### <span data-ttu-id="46622-168">-As</span><span class="sxs-lookup"><span data-stu-id="46622-168">-As</span></span>

<span data-ttu-id="46622-169">개체를 테이블 형식으로 지정할지, 아니면 목록 형식으로 지정할지 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="46622-169">Determines whether the object is formatted as a table or a list.</span></span> <span data-ttu-id="46622-170">유효한 값은 **Table** 및 **List** 입니다.</span><span class="sxs-lookup"><span data-stu-id="46622-170">Valid values are **Table** and **List**.</span></span> <span data-ttu-id="46622-171">기본값은 **Table** 입니다.</span><span class="sxs-lookup"><span data-stu-id="46622-171">The default value is **Table**.</span></span>

<span data-ttu-id="46622-172">**테이블** 값은 PowerShell 테이블 형식과 유사한 HTML 테이블을 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="46622-172">The **Table** value generates an HTML table that resembles the PowerShell table format.</span></span> <span data-ttu-id="46622-173">머리글 행은 속성 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="46622-173">The header row displays the property names.</span></span> <span data-ttu-id="46622-174">각 테이블 행은 개체를 나타내고 개체의 각 속성 값을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="46622-174">Each table row represents an object and displays the object's values for each property.</span></span>

<span data-ttu-id="46622-175">**목록** 값은 PowerShell 목록 형식과 유사한 각 개체에 대해 2 열 HTML 테이블을 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="46622-175">The **List** value generates a two-column HTML table for each object that resembles the PowerShell list format.</span></span> <span data-ttu-id="46622-176">첫 번째 열에는 속성 이름이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="46622-176">The first column displays the property name.</span></span> <span data-ttu-id="46622-177">두 번째 열에는 속성 값이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="46622-177">The second column displays the property value.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Table, List

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="46622-178">-본문</span><span class="sxs-lookup"><span data-stu-id="46622-178">-Body</span></span>

<span data-ttu-id="46622-179">여는 `<BODY>` 태그 뒤에 추가할 텍스트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="46622-179">Specifies the text to add after the opening `<BODY>` tag.</span></span> <span data-ttu-id="46622-180">기본적으로 해당 위치에는 텍스트가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="46622-180">By default, there is no text in that position.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Page
Aliases:

Required: False
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="46622-181">-Charset</span><span class="sxs-lookup"><span data-stu-id="46622-181">-Charset</span></span>

<span data-ttu-id="46622-182">여는 태그에 추가할 텍스트를 지정 합니다 `<charset>` .</span><span class="sxs-lookup"><span data-stu-id="46622-182">Specifies text to add to the opening `<charset>` tag.</span></span> <span data-ttu-id="46622-183">기본적으로 해당 위치에는 텍스트가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="46622-183">By default, there is no text in that position.</span></span>

<span data-ttu-id="46622-184">이 매개 변수는 PowerShell 6.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="46622-184">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.String
Parameter Sets: Page
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="46622-185">-CssUri</span><span class="sxs-lookup"><span data-stu-id="46622-185">-CssUri</span></span>

<span data-ttu-id="46622-186">HTML 파일에 적용되는 CSS 스타일시트의 URI(Uniform Resource Identifier)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="46622-186">Specifies the Uniform Resource Identifier (URI) of the cascading style sheet (CSS) that is applied to the HTML file.</span></span> <span data-ttu-id="46622-187">이 URI는 출력의 스타일시트 링크에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="46622-187">The URI is included in a style sheet link in the output.</span></span>

```yaml
Type: System.Uri
Parameter Sets: Page
Aliases: cu, uri

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="46622-188">-조각</span><span class="sxs-lookup"><span data-stu-id="46622-188">-Fragment</span></span>

<span data-ttu-id="46622-189">HTML 테이블만 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="46622-189">Generates only an HTML table.</span></span> <span data-ttu-id="46622-190">HTML, HEAD, TITLE 및 BODY 태그는 생략됩니다.</span><span class="sxs-lookup"><span data-stu-id="46622-190">The HTML, HEAD, TITLE, and BODY tags are omitted.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Fragment
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="46622-191">-Head</span><span class="sxs-lookup"><span data-stu-id="46622-191">-Head</span></span>

<span data-ttu-id="46622-192">`<HEAD>` 태그의 내용을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="46622-192">Specifies the content of the `<HEAD>` tag.</span></span> <span data-ttu-id="46622-193">기본값은 `<title\>HTML TABLE</title>`입니다.</span><span class="sxs-lookup"><span data-stu-id="46622-193">The default is `<title\>HTML TABLE</title>`.</span></span> <span data-ttu-id="46622-194">**Head** 매개 변수를 사용 하는 경우 **Title** 매개 변수는 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="46622-194">If you use the **Head** parameter, the **Title** parameter is ignored.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Page
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="46622-195">-InputObject</span><span class="sxs-lookup"><span data-stu-id="46622-195">-InputObject</span></span>

<span data-ttu-id="46622-196">HTML로 표시할 개체를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="46622-196">Specifies the objects to be represented in HTML.</span></span> <span data-ttu-id="46622-197">개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="46622-197">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span>

<span data-ttu-id="46622-198">이 매개 변수를 사용 하 여 컴퓨터의 모든 서비스와 같은 여러 개체를 전송 하는 경우 `ConvertTo-Html` 컬렉션 또는 개체 배열의 속성을 표시 하는 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="46622-198">If you use this parameter to submit multiple objects, such as all of the services on a computer, `ConvertTo-Html` creates a table that displays the properties of a collection or of an array of objects.</span></span> <span data-ttu-id="46622-199">개별 개체의 테이블을 만들려면 파이프라인 연산자를 사용 하 여 개체를로 파이프 합니다 `ConvertTo-Html` .</span><span class="sxs-lookup"><span data-stu-id="46622-199">To create a table of the individual objects, use the pipeline operator to pipe the objects to `ConvertTo-Html`.</span></span>

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

### <span data-ttu-id="46622-200">-Meta</span><span class="sxs-lookup"><span data-stu-id="46622-200">-Meta</span></span>

<span data-ttu-id="46622-201">여는 태그에 추가할 텍스트를 지정 합니다 `<meta>` .</span><span class="sxs-lookup"><span data-stu-id="46622-201">Specifies text to add to the opening `<meta>` tag.</span></span> <span data-ttu-id="46622-202">기본적으로 해당 위치에는 텍스트가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="46622-202">By default, there is no text in that position.</span></span>

<span data-ttu-id="46622-203">이 매개 변수는 PowerShell 6.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="46622-203">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Collections.Hashtable
Parameter Sets: Page
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="46622-204">-PostContent</span><span class="sxs-lookup"><span data-stu-id="46622-204">-PostContent</span></span>

<span data-ttu-id="46622-205">닫는 `</TABLE>` 태그 뒤에 추가할 텍스트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="46622-205">Specifies text to add after the closing `</TABLE>` tag.</span></span> <span data-ttu-id="46622-206">기본적으로 해당 위치에는 텍스트가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="46622-206">By default, there is no text in that position.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="46622-207">-PreContent</span><span class="sxs-lookup"><span data-stu-id="46622-207">-PreContent</span></span>

<span data-ttu-id="46622-208">여는 `<TABLE>` 태그 앞에 추가할 텍스트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="46622-208">Specifies text to add before the opening `<TABLE>` tag.</span></span> <span data-ttu-id="46622-209">기본적으로 해당 위치에는 텍스트가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="46622-209">By default, there is no text in that position.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="46622-210">-속성</span><span class="sxs-lookup"><span data-stu-id="46622-210">-Property</span></span>

<span data-ttu-id="46622-211">지정한 개체 속성을 HTML에 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="46622-211">Includes the specified properties of the objects in the HTML.</span></span> <span data-ttu-id="46622-212">**Property** 매개 변수 값은 새 계산 된 속성 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46622-212">The value of the **Property** parameter can be a new calculated property.</span></span> <span data-ttu-id="46622-213">계산 된 속성은 스크립트 블록이 나 해시 테이블 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46622-213">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="46622-214">유효한 키-값 쌍은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="46622-214">Valid key-value pairs are:</span></span>

- <span data-ttu-id="46622-215">이름 (또는 레이블)- `<string>` (PowerShell 6.x에 추가 됨)</span><span class="sxs-lookup"><span data-stu-id="46622-215">Name (or label) - `<string>` (added in PowerShell 6.x)</span></span>
- <span data-ttu-id="46622-216">식 `<string>` 또는 `<script block>`</span><span class="sxs-lookup"><span data-stu-id="46622-216">Expression - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="46622-217">FormatString `<string>`</span><span class="sxs-lookup"><span data-stu-id="46622-217">FormatString - `<string>`</span></span>
- <span data-ttu-id="46622-218">Width- `<int32>` -다음 보다 커야 함 `0`</span><span class="sxs-lookup"><span data-stu-id="46622-218">Width - `<int32>` - must be greater than `0`</span></span>
- <span data-ttu-id="46622-219">맞춤-값은 `Left` , `Center` 또는 일 수 있습니다. `Right`</span><span class="sxs-lookup"><span data-stu-id="46622-219">Alignment - value can be `Left`, `Center`, or `Right`</span></span>

<span data-ttu-id="46622-220">자세한 내용은 [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="46622-220">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="46622-221">-Title</span><span class="sxs-lookup"><span data-stu-id="46622-221">-Title</span></span>

<span data-ttu-id="46622-222">`<TITLE>` 태그 사이에 표시되는 텍스트인 HTML 파일의 제목을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="46622-222">Specifies a title for the HTML file, that is, the text that appears between the `<TITLE>` tags.</span></span>

```yaml
Type: System.String
Parameter Sets: Page
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="46622-223">-전환</span><span class="sxs-lookup"><span data-stu-id="46622-223">-Transitional</span></span>

<span data-ttu-id="46622-224">**Doctype** 을 **xhtml 전환 dtd** 로 변경 하 고, 기본 **doctype** 은 **xhtml Strict dtd** 입니다.</span><span class="sxs-lookup"><span data-stu-id="46622-224">Changes the **DOCTYPE** to **XHTML Transitional DTD** , Default **DOCTYPE** is **XHTML Strict DTD**.</span></span>

<span data-ttu-id="46622-225">이 매개 변수는 PowerShell 6.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="46622-225">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Page
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="46622-226">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="46622-226">CommonParameters</span></span>

<span data-ttu-id="46622-227">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="46622-227">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="46622-228">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="46622-228">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="46622-229">입력</span><span class="sxs-lookup"><span data-stu-id="46622-229">INPUTS</span></span>

### <span data-ttu-id="46622-230">System.web. PSObject</span><span class="sxs-lookup"><span data-stu-id="46622-230">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="46622-231">모든 .NET 개체를로 파이프 할 수 있습니다 `ConvertTo-Html` .</span><span class="sxs-lookup"><span data-stu-id="46622-231">You can pipe any .NET object to `ConvertTo-Html`.</span></span>

## <span data-ttu-id="46622-232">출력</span><span class="sxs-lookup"><span data-stu-id="46622-232">OUTPUTS</span></span>

### <span data-ttu-id="46622-233">System.string 또는 System.Xml.Xml문서</span><span class="sxs-lookup"><span data-stu-id="46622-233">System.String or System.Xml.XmlDocument</span></span>

<span data-ttu-id="46622-234">`ConvertTo-Html` 유효한 HTML을 구성 하는 일련의 문자열을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="46622-234">`ConvertTo-Html` returns series of strings that comprise valid HTML.</span></span>

## <span data-ttu-id="46622-235">참고</span><span class="sxs-lookup"><span data-stu-id="46622-235">NOTES</span></span>

<span data-ttu-id="46622-236">이 cmdlet을 사용 하려면 하나 이상의 개체를 cmdlet으로 파이프 하거나 **InputObject** 매개 변수를 사용 하 여 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="46622-236">To use this cmdlet, pipe one or more objects to the cmdlet or use the **InputObject** parameter to specify the object.</span></span> <span data-ttu-id="46622-237">입력이 여러 개체로 구성된 경우에는 이 두 방법의 출력이 전혀 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="46622-237">When the input consists of multiple objects, the output of these two methods is quite different.</span></span>

- <span data-ttu-id="46622-238">여러 개체를 cmdlet으로 파이프 하면 PowerShell은 개체를 한 번에 하나씩 cmdlet으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="46622-238">When you pipe multiple objects to a cmdlet, PowerShell sends the objects to the cmdlet one at a time.</span></span> <span data-ttu-id="46622-239">따라서는 `ConvertTo-Html` 개별 개체를 표시 하는 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="46622-239">As a result, `ConvertTo-Html` creates a table that displays the individual objects.</span></span> <span data-ttu-id="46622-240">예를 들어 컴퓨터의 프로세스를로 파이프 하는 경우 `ConvertTo-Html` 결과 테이블에 모든 프로세스가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="46622-240">For example, if you pipe the processes on a computer to `ConvertTo-Html`, the resulting table displays all of the processes.</span></span>

- <span data-ttu-id="46622-241">**InputObject** 매개 변수를 사용 하 여 여러 개체를 전송 하는 경우는 `ConvertTo-Html` 이러한 개체를 컬렉션 또는 배열로 받습니다.</span><span class="sxs-lookup"><span data-stu-id="46622-241">When you use the **InputObject** parameter to submit multiple objects, `ConvertTo-Html` receives these objects as a collection or as an array.</span></span> <span data-ttu-id="46622-242">따라서 배열의 항목이 아니라 배열과 해당 속성을 표시하는 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="46622-242">As a result, it creates a table that displays the array and its properties, not the items in the array.</span></span> <span data-ttu-id="46622-243">예를 들어 **InputObject** 를 사용 하 여 컴퓨터의 프로세스를로 전송 하 `ConvertTo-Html` 는 경우 결과 테이블에 개체 배열 및 해당 속성이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="46622-243">For example, if you use **InputObject** to submit the processes on a computer to `ConvertTo-Html`, the resulting table displays an object array and its properties.</span></span>

  <span data-ttu-id="46622-244">XHTML Strict DTD를 준수 하기 위해 DOCTYPE 태그가 적절 하 게 수정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="46622-244">To comply with the XHTML Strict DTD, the DOCTYPE tag is modified accordingly:</span></span>

   `<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"   "https://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd"\>`

## <span data-ttu-id="46622-245">관련 링크</span><span class="sxs-lookup"><span data-stu-id="46622-245">RELATED LINKS</span></span>

[<span data-ttu-id="46622-246">about_Calculated_Properties</span><span class="sxs-lookup"><span data-stu-id="46622-246">about_Calculated_Properties</span></span>](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[<span data-ttu-id="46622-247">ConvertTo-Csv</span><span class="sxs-lookup"><span data-stu-id="46622-247">ConvertTo-Csv</span></span>](ConvertTo-Csv.md)

[<span data-ttu-id="46622-248">ConvertTo-Json</span><span class="sxs-lookup"><span data-stu-id="46622-248">ConvertTo-Json</span></span>](ConvertTo-Json.md)

[<span data-ttu-id="46622-249">ConvertTo-Xml</span><span class="sxs-lookup"><span data-stu-id="46622-249">ConvertTo-Xml</span></span>](ConvertTo-Xml.md)

[<span data-ttu-id="46622-250">Export-Clixml</span><span class="sxs-lookup"><span data-stu-id="46622-250">Export-Clixml</span></span>](Export-Clixml.md)

[<span data-ttu-id="46622-251">Import-Clixml</span><span class="sxs-lookup"><span data-stu-id="46622-251">Import-Clixml</span></span>](Import-Clixml.md)
