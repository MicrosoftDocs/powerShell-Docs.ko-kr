---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertto-html?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-Html
ms.openlocfilehash: ffe7fe7c44258435c7ec9ddd2bab9ebeb9f6c465
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99600444"
---
# <span data-ttu-id="a528f-102">ConvertTo-Html</span><span class="sxs-lookup"><span data-stu-id="a528f-102">ConvertTo-Html</span></span>

## <span data-ttu-id="a528f-103">개요</span><span class="sxs-lookup"><span data-stu-id="a528f-103">SYNOPSIS</span></span>
<span data-ttu-id="a528f-104">.NET 개체를 웹 브라우저에 표시할 수 있는 HTML로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-104">Converts .NET objects into HTML that can be displayed in a Web browser.</span></span>

## <span data-ttu-id="a528f-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a528f-105">SYNTAX</span></span>

### <span data-ttu-id="a528f-106">페이지 (기본값)</span><span class="sxs-lookup"><span data-stu-id="a528f-106">Page (Default)</span></span>

```
ConvertTo-Html [-InputObject <PSObject>] [[-Property] <Object[]>] [[-Body] <String[]>]
 [[-Head] <String[]>] [[-Title] <String>] [-As <String>] [-CssUri <Uri>] [-PostContent <String[]>]
 [-PreContent <String[]>] [-Meta <Hashtable>] [-Charset <String>] [-Transitional]
 [<CommonParameters>]
```

### <span data-ttu-id="a528f-107">Fragment</span><span class="sxs-lookup"><span data-stu-id="a528f-107">Fragment</span></span>

```
ConvertTo-Html [-InputObject <PSObject>] [[-Property] <Object[]>] [-As <String>] [-Fragment]
 [-PostContent <String[]>] [-PreContent <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="a528f-108">설명</span><span class="sxs-lookup"><span data-stu-id="a528f-108">DESCRIPTION</span></span>

<span data-ttu-id="a528f-109">`ConvertTo-Html`Cmdlet은 .net 개체를 웹 브라우저에 표시할 수 있는 HTML로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-109">The `ConvertTo-Html` cmdlet converts .NET objects into HTML that can be displayed in a Web browser.</span></span> <span data-ttu-id="a528f-110">이 cmdlet을 사용하여 명령 출력을 웹 페이지에 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-110">You can use this cmdlet to display the output of a command in a Web page.</span></span>

<span data-ttu-id="a528f-111">의 매개 변수를 사용 하 여 `ConvertTo-Html` 개체 속성을 선택 하 고, 테이블 또는 목록 형식을 지정 하 고, HTML 페이지 제목을 지정 하 고, 개체 앞뒤에 텍스트를 추가 하 고, STRICT DTD 페이지 대신 테이블 또는 목록 조각만 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-111">You can use the parameters of `ConvertTo-Html` to select object properties, to specify a table or list format, to specify the HTML page title, to add text before and after the object, and to return only the table or list fragment, instead of a strict DTD page.</span></span>

<span data-ttu-id="a528f-112">에 여러 개체를 제출 하는 경우 `ConvertTo-Html` PowerShell은 제출한 첫 번째 개체의 속성을 기반으로 테이블 (또는 목록)을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-112">When you submit multiple objects to `ConvertTo-Html`, PowerShell creates the table (or list) based on the properties of the first object that you submit.</span></span> <span data-ttu-id="a528f-113">나머지 개체에 지정한 속성이 하나도 없을 경우 해당 개체의 속성 값은 빈 셀이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-113">If the remaining objects do not have one of the specified properties, the property value of that object is an empty cell.</span></span> <span data-ttu-id="a528f-114">나머지 개체에 추가 속성이 있을 경우 이러한 속성 값은 파일에 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-114">If the remaining objects have additional properties, those property values are not included in the file.</span></span>

## <span data-ttu-id="a528f-115">예제</span><span class="sxs-lookup"><span data-stu-id="a528f-115">EXAMPLES</span></span>

### <span data-ttu-id="a528f-116">예제 1: 날짜를 표시 하는 웹 페이지 만들기</span><span class="sxs-lookup"><span data-stu-id="a528f-116">Example 1: Create a web page to display the date</span></span>

```powershell
ConvertTo-Html -InputObject (Get-Date)
```

<span data-ttu-id="a528f-117">이 명령은 현재 날짜의 속성을 표시하는 HTML 페이지를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-117">This command creates an HTML page that displays the properties of the current date.</span></span> <span data-ttu-id="a528f-118">**InputObject** 매개 변수를 사용 하 여 명령의 결과를 `Get-Date` cmdlet에 제출 `ConvertTo-Html` 합니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-118">It uses the **InputObject** parameter to submit the results of a `Get-Date` command to the `ConvertTo-Html` cmdlet.</span></span>

### <span data-ttu-id="a528f-119">예제 2: PowerShell 별칭을 표시 하는 웹 페이지 만들기</span><span class="sxs-lookup"><span data-stu-id="a528f-119">Example 2: Create a web page to display PowerShell aliases</span></span>

```powershell
Get-Alias | ConvertTo-Html | Out-File aliases.htm
Invoke-Item aliases.htm
```

<span data-ttu-id="a528f-120">이 명령은 현재 콘솔의 PowerShell 별칭을 나열 하는 HTML 페이지를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-120">This command creates an HTML page that lists the PowerShell aliases in the current console.</span></span>

<span data-ttu-id="a528f-121">이 명령은 cmdlet을 사용 하 여 `Get-Alias` 별칭을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-121">The command uses the `Get-Alias` cmdlet to get the aliases.</span></span> <span data-ttu-id="a528f-122">파이프라인 연산자 ()를 사용 하 여 `|` 별칭을 cmdlet으로 보내면이 `ConvertTo-Html` CMDLET이 HTML 페이지를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-122">It uses the pipeline operator (`|`) to send the aliases to the `ConvertTo-Html` cmdlet, which creates the HTML page.</span></span> <span data-ttu-id="a528f-123">또한이 명령은 cmdlet을 사용 하 여 `Out-File` HTML 코드를 파일에 보냅니다 `aliases.htm` .</span><span class="sxs-lookup"><span data-stu-id="a528f-123">The command also uses the `Out-File` cmdlet to send the HTML code to the `aliases.htm` file.</span></span>

### <span data-ttu-id="a528f-124">예제 3: PowerShell 이벤트를 표시 하는 웹 페이지 만들기</span><span class="sxs-lookup"><span data-stu-id="a528f-124">Example 3: Create a web page to display PowerShell events</span></span>

```powershell
`Get-EventLog` -LogName "Windows PowerShell" | ConvertTo-Html | Out-File pslog.htm
```

<span data-ttu-id="a528f-125">이 명령은 `pslog.htm` 로컬 컴퓨터의 Windows PowerShell 이벤트 로그에 이벤트를 표시 하는 이라는 HTML 페이지를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-125">This command creates an HTML page called `pslog.htm` that displays the events in the Windows PowerShell event log on the local computer.</span></span>

<span data-ttu-id="a528f-126">Cmdlet을 사용 하 여 `Get-EventLog` Windows PowerShell 로그의 이벤트를 가져온 다음 파이프라인 연산자 ()를 사용 하 여 `|` 이벤트를 cmdlet으로 보냅니다 `ConvertTo-Html` .</span><span class="sxs-lookup"><span data-stu-id="a528f-126">It uses the `Get-EventLog` cmdlet to get the events in the Windows PowerShell log and then uses the pipeline operator (`|`) to send the events to the `ConvertTo-Html` cmdlet.</span></span> <span data-ttu-id="a528f-127">또한이 명령은 cmdlet을 사용 하 여 `Out-File` HTML 코드를 파일에 보냅니다 `pslog.htm` .</span><span class="sxs-lookup"><span data-stu-id="a528f-127">The command also uses the `Out-File` cmdlet to send the HTML code to the `pslog.htm` file.</span></span>

<span data-ttu-id="a528f-128">또한이 명령은 cmdlet을 사용 하 여 `Out-File` HTML 코드를 파일에 보냅니다 `pslog.htm` .</span><span class="sxs-lookup"><span data-stu-id="a528f-128">The command also uses the `Out-File` cmdlet to send the HTML code to the `pslog.htm` file.</span></span>

### <span data-ttu-id="a528f-129">예제 4: 프로세스를 표시 하는 웹 페이지 만들기</span><span class="sxs-lookup"><span data-stu-id="a528f-129">Example 4: Create a web page to display processes</span></span>

```powershell
Get-Process |
  ConvertTo-Html -Property Name, Path, Company -Title "Process Information" |
    Out-File proc.htm
Invoke-Item proc.htm
```

<span data-ttu-id="a528f-130">이 명령은 로컬 컴퓨터에 있는 프로세스의 이름, 경로 및 회사를 나열하는 HTML 페이지를 만들어서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-130">These commands create and open an HTML page that lists the name, path, and company of the processes on the local computer.</span></span>

<span data-ttu-id="a528f-131">첫 번째 명령은 cmdlet을 사용 하 여 `Get-Process` 컴퓨터에서 실행 중인 프로세스를 나타내는 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-131">The first command uses the `Get-Process` cmdlet to get objects that represent the processes running on the computer.</span></span> <span data-ttu-id="a528f-132">이 명령은 파이프라인 연산자 ()를 사용 하 여 `|` 프로세스 개체를 cmdlet으로 보냅니다 `ConvertTo-Html` .</span><span class="sxs-lookup"><span data-stu-id="a528f-132">The command uses the pipeline operator (`|`) to send the process objects to the `ConvertTo-Html` cmdlet.</span></span>

<span data-ttu-id="a528f-133">이 명령은 **Property** 매개 변수를 사용 하 여 테이블에 포함할 프로세스 개체의 세 가지 속성을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-133">The command uses the **Property** parameter to select three properties of the process objects to be included in the table.</span></span> <span data-ttu-id="a528f-134">이 명령은 **title** 매개 변수를 사용 하 여 HTML 페이지의 제목을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-134">The command uses the **Title** parameter to specify a title for the HTML page.</span></span> <span data-ttu-id="a528f-135">또한이 명령은 cmdlet을 사용 하 여 `Out-File` 결과 HTML을 Proc.htm 이라는 파일로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-135">The command also uses the `Out-File` cmdlet to send the resulting HTML to a file named Proc.htm.</span></span>

<span data-ttu-id="a528f-136">두 번째 명령은 cmdlet을 사용 하 여 `Invoke-Item` 를 `Proc.htm` 기본 브라우저에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-136">The second command uses the `Invoke-Item` cmdlet to open the `Proc.htm` in the default browser.</span></span>

### <span data-ttu-id="a528f-137">예 5: 서비스 개체를 표시 하는 웹 페이지 만들기</span><span class="sxs-lookup"><span data-stu-id="a528f-137">Example 5: Create a web page to display service objects</span></span>

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

<span data-ttu-id="a528f-138">이 명령은 cmdlet이 반환 하는 서비스 개체의 HTML 페이지를 만듭니다 `Get-Service` .</span><span class="sxs-lookup"><span data-stu-id="a528f-138">This command creates an HTML page of the service objects that the `Get-Service` cmdlet returns.</span></span> <span data-ttu-id="a528f-139">이 명령은 **CssUri** 매개 변수를 사용 하 여 HTML 페이지의 css 스타일 시트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-139">The command uses the **CssUri** parameter to specify a cascading style sheet for the HTML page.</span></span>

<span data-ttu-id="a528f-140">**CssUri** 매개 변수는 `<link rel="stylesheet" type="text/css" href="test.css">` 결과 HTML에 추가 태그를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-140">The **CssUri** parameter adds an additional `<link rel="stylesheet" type="text/css" href="test.css">` tag to the resulting HTML.</span></span> <span data-ttu-id="a528f-141">태그의 HREF 특성에는 스타일시트의 이름이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-141">The HREF attribute in the tag contains the name of the style sheet.</span></span>

### <span data-ttu-id="a528f-142">예제 6: 서비스 개체를 표시 하는 웹 페이지 만들기</span><span class="sxs-lookup"><span data-stu-id="a528f-142">Example 6: Create a web page to display service objects</span></span>

```powershell
Get-Service | ConvertTo-Html -As LIST | Out-File services.htm
```

<span data-ttu-id="a528f-143">이 명령은 cmdlet이 반환 하는 서비스 개체의 HTML 페이지를 만듭니다 `Get-Service` .</span><span class="sxs-lookup"><span data-stu-id="a528f-143">This command creates an HTML page of the service objects that the `Get-Service` cmdlet returns.</span></span> <span data-ttu-id="a528f-144">이 명령은 **As** 매개 변수를 사용 하 여 목록 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-144">The command uses the **As** parameter to specify a list format.</span></span> <span data-ttu-id="a528f-145">Cmdlet은 `Out-File` 결과 HTML을 파일에 보냅니다 `Services.htm` .</span><span class="sxs-lookup"><span data-stu-id="a528f-145">The cmdlet `Out-File` sends the resulting HTML to the `Services.htm` file.</span></span>

### <span data-ttu-id="a528f-146">예 7: 현재 날짜에 대 한 웹 테이블 만들기</span><span class="sxs-lookup"><span data-stu-id="a528f-146">Example 7: Create a web table for the current date</span></span>

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

<span data-ttu-id="a528f-147">이 명령은 `ConvertTo-Html` 를 사용 하 여 현재 날짜의 HTML 테이블을 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-147">This command uses `ConvertTo-Html` to generate an HTML table of the current date.</span></span> <span data-ttu-id="a528f-148">이 명령은 cmdlet을 사용 하 여 `Get-Date` 현재 날짜를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-148">The command uses the `Get-Date` cmdlet to get the current date.</span></span> <span data-ttu-id="a528f-149">파이프라인 연산자 (|)를 사용 하 여 결과를 cmdlet으로 보냅니다 `ConvertTo-Html` .</span><span class="sxs-lookup"><span data-stu-id="a528f-149">It uses a pipeline operator (|) to send the results to the `ConvertTo-Html` cmdlet.</span></span>

<span data-ttu-id="a528f-150">이 `ConvertTo-Html` 명령은 출력을 HTML 테이블로 제한 하는 **Fragment** 매개 변수를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-150">The `ConvertTo-Html` command includes the **Fragment** parameter, which limits the output to an HTML table.</span></span> <span data-ttu-id="a528f-151">따라서 `<HEAD>` 및 `<BODY>` 태그와 같은 HTML 페이지의 다른 요소는 생략됩니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-151">As a result, the other elements of an HTML page, such as the `<HEAD>` and `<BODY>` tags, are omitted.</span></span>

### <span data-ttu-id="a528f-152">예 8: PowerShell 이벤트를 표시 하는 웹 페이지 만들기</span><span class="sxs-lookup"><span data-stu-id="a528f-152">Example 8: Create a web page to display PowerShell events</span></span>

```powershell
Get-EventLog -Log "Windows PowerShell" | ConvertTo-Html -Property id, level, task
```

<span data-ttu-id="a528f-153">이 명령은 cmdlet을 사용 하 여 `Get-EventLog` Windows PowerShell 이벤트 로그에서 이벤트를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-153">This command uses the `Get-EventLog` cmdlet to get events from the Windows PowerShell event log.</span></span>

<span data-ttu-id="a528f-154">파이프라인 연산자 ()를 사용 하 여 `|` 이벤트를 cmdlet으로 보내면이 `ConvertTo-Html` cmdlet이 이벤트를 HTML 형식으로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-154">It uses a pipeline operator (`|`) to send the events to the `ConvertTo-Html` cmdlet, which converts the events to HTML format.</span></span>

<span data-ttu-id="a528f-155">`ConvertTo-Html`이 명령은 **Property** 매개 변수를 사용 하 여 이벤트의 **ID**, **Level** 및 **Task** 속성만 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-155">The `ConvertTo-Html` command uses the **Property** parameter to select only the **ID**, **Level**, and **Task** properties of the event.</span></span>

### <span data-ttu-id="a528f-156">예 9: 지정 된 서비스를 표시 하는 웹 페이지 만들기</span><span class="sxs-lookup"><span data-stu-id="a528f-156">Example 9: Create a web page to display specified services</span></span>

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

<span data-ttu-id="a528f-157">이 명령은로 시작 하는 컴퓨터의 서비스를 표시 하는 웹 페이지를 만들고 엽니다. 의 **Title**, **Body**, **precontent** 및 **postcontent** 매개 변수를 사용 하 여 `ConvertTo-Html` 출력을 사용자 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-157">This command creates and opens a Web page that displays the services on the computer that begin with A. It uses the **Title**, **Body**, **PreContent**, and **PostContent** parameters of `ConvertTo-Html` to customize the output.</span></span>

<span data-ttu-id="a528f-158">명령의 첫 번째 부분에서는 cmdlet을 사용 하 여 `Get-Service` 로 시작 하는 컴퓨터의 서비스를 가져옵니다. 이 명령은 파이프라인 연산자 ()를 사용 하 여 `|` 결과를 cmdlet으로 보냅니다 `ConvertTo-Html` .</span><span class="sxs-lookup"><span data-stu-id="a528f-158">The first part of the command uses the `Get-Service` cmdlet to get the services on the computer that begin with A. The command uses a pipeline operator (`|`) to send the results to the `ConvertTo-Html` cmdlet.</span></span> <span data-ttu-id="a528f-159">또한이 명령은 cmdlet을 사용 하 여 `Out-File` 출력을 Services.htm 파일로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-159">The command also uses the `Out-File` cmdlet to send the output to the Services.htm file.</span></span>

<span data-ttu-id="a528f-160">세미콜론 ( `;` )을 사용 하면 첫 번째 명령이 끝나고 두 번째 명령이 시작 됩니다 .이 명령은 cmdlet을 사용 하 여 `Invoke-Item` `Services.htm` 기본 브라우저에서 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-160">A semicolon (`;`) ends the first command and starts a second command, which uses the `Invoke-Item` cmdlet to open the `Services.htm` file in the default browser.</span></span>

### <span data-ttu-id="a528f-161">예 10: HTML의 Meta 속성 및 문자 집합 설정</span><span class="sxs-lookup"><span data-stu-id="a528f-161">Example 10: Set the Meta properties and Charset of the HTML</span></span>

```powershell
Get-Service | ConvertTo-HTML -Meta @{
  refresh=10
  author="Author's Name"
  keywords="PowerShell, HTML, ConvertTo-HTML"
} -Charset "UTF-8"
```

<span data-ttu-id="a528f-162">이 명령은 새로 고침, 만든이 및 키워드에 대 한 메타 태그를 사용 하 여 웹 페이지에 대 한 HTML을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-162">This command creates the HTML for a webpage with the meta tags for refresh, author, and keywords.</span></span>
<span data-ttu-id="a528f-163">페이지의 문자 집합은 u t f-8로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-163">The charset for the page is set to UTF-8</span></span>

### <span data-ttu-id="a528f-164">예 11: HTML을 XHTML 전환 DTD로 설정</span><span class="sxs-lookup"><span data-stu-id="a528f-164">Example 11: Set the HTML to XHTML Transitional DTD</span></span>

```powershell
Get-Service | ConvertTo-HTML -Transitional
```

<span data-ttu-id="a528f-165">이 명령은 반환 된 HTML의 DOCTYPE을 XHTML 전환 DTD로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-165">This command sets the DOCTYPE of the returned HTML to XHTML Transitional DTD</span></span>

## <span data-ttu-id="a528f-166">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a528f-166">PARAMETERS</span></span>

### <span data-ttu-id="a528f-167">-As</span><span class="sxs-lookup"><span data-stu-id="a528f-167">-As</span></span>

<span data-ttu-id="a528f-168">개체를 테이블 형식으로 지정할지, 아니면 목록 형식으로 지정할지 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-168">Determines whether the object is formatted as a table or a list.</span></span> <span data-ttu-id="a528f-169">유효한 값은 **Table** 및 **List** 입니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-169">Valid values are **Table** and **List**.</span></span> <span data-ttu-id="a528f-170">기본값은 **Table** 입니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-170">The default value is **Table**.</span></span>

<span data-ttu-id="a528f-171">**테이블** 값은 PowerShell 테이블 형식과 유사한 HTML 테이블을 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-171">The **Table** value generates an HTML table that resembles the PowerShell table format.</span></span> <span data-ttu-id="a528f-172">머리글 행은 속성 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-172">The header row displays the property names.</span></span> <span data-ttu-id="a528f-173">각 테이블 행은 개체를 나타내고 개체의 각 속성 값을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-173">Each table row represents an object and displays the object's values for each property.</span></span>

<span data-ttu-id="a528f-174">**목록** 값은 PowerShell 목록 형식과 유사한 각 개체에 대해 2 열 HTML 테이블을 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-174">The **List** value generates a two-column HTML table for each object that resembles the PowerShell list format.</span></span> <span data-ttu-id="a528f-175">첫 번째 열에는 속성 이름이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-175">The first column displays the property name.</span></span> <span data-ttu-id="a528f-176">두 번째 열에는 속성 값이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-176">The second column displays the property value.</span></span>

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

### <span data-ttu-id="a528f-177">-본문</span><span class="sxs-lookup"><span data-stu-id="a528f-177">-Body</span></span>

<span data-ttu-id="a528f-178">여는 `<BODY>` 태그 뒤에 추가할 텍스트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-178">Specifies the text to add after the opening `<BODY>` tag.</span></span> <span data-ttu-id="a528f-179">기본적으로 해당 위치에는 텍스트가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-179">By default, there is no text in that position.</span></span>

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

### <span data-ttu-id="a528f-180">-Charset</span><span class="sxs-lookup"><span data-stu-id="a528f-180">-Charset</span></span>

<span data-ttu-id="a528f-181">여는 태그에 추가할 텍스트를 지정 합니다 `<charset>` .</span><span class="sxs-lookup"><span data-stu-id="a528f-181">Specifies text to add to the opening `<charset>` tag.</span></span> <span data-ttu-id="a528f-182">기본적으로 해당 위치에는 텍스트가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-182">By default, there is no text in that position.</span></span>

<span data-ttu-id="a528f-183">이 매개 변수는 PowerShell 6.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-183">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="a528f-184">-CssUri</span><span class="sxs-lookup"><span data-stu-id="a528f-184">-CssUri</span></span>

<span data-ttu-id="a528f-185">HTML 파일에 적용되는 CSS 스타일시트의 URI(Uniform Resource Identifier)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-185">Specifies the Uniform Resource Identifier (URI) of the cascading style sheet (CSS) that is applied to the HTML file.</span></span> <span data-ttu-id="a528f-186">이 URI는 출력의 스타일시트 링크에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-186">The URI is included in a style sheet link in the output.</span></span>

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

### <span data-ttu-id="a528f-187">-조각</span><span class="sxs-lookup"><span data-stu-id="a528f-187">-Fragment</span></span>

<span data-ttu-id="a528f-188">HTML 테이블만 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-188">Generates only an HTML table.</span></span> <span data-ttu-id="a528f-189">HTML, HEAD, TITLE 및 BODY 태그는 생략됩니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-189">The HTML, HEAD, TITLE, and BODY tags are omitted.</span></span>

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

### <span data-ttu-id="a528f-190">-Head</span><span class="sxs-lookup"><span data-stu-id="a528f-190">-Head</span></span>

<span data-ttu-id="a528f-191">`<HEAD>` 태그의 내용을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-191">Specifies the content of the `<HEAD>` tag.</span></span> <span data-ttu-id="a528f-192">기본값은 `<title\>HTML TABLE</title>`입니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-192">The default is `<title\>HTML TABLE</title>`.</span></span> <span data-ttu-id="a528f-193">**Head** 매개 변수를 사용 하는 경우 **Title** 매개 변수는 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-193">If you use the **Head** parameter, the **Title** parameter is ignored.</span></span>

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

### <span data-ttu-id="a528f-194">-InputObject</span><span class="sxs-lookup"><span data-stu-id="a528f-194">-InputObject</span></span>

<span data-ttu-id="a528f-195">HTML로 표시할 개체를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-195">Specifies the objects to be represented in HTML.</span></span> <span data-ttu-id="a528f-196">개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="a528f-196">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span>

<span data-ttu-id="a528f-197">이 매개 변수를 사용 하 여 컴퓨터의 모든 서비스와 같은 여러 개체를 전송 하는 경우 `ConvertTo-Html` 컬렉션 또는 개체 배열의 속성을 표시 하는 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-197">If you use this parameter to submit multiple objects, such as all of the services on a computer, `ConvertTo-Html` creates a table that displays the properties of a collection or of an array of objects.</span></span> <span data-ttu-id="a528f-198">개별 개체의 테이블을 만들려면 파이프라인 연산자를 사용 하 여 개체를로 파이프 합니다 `ConvertTo-Html` .</span><span class="sxs-lookup"><span data-stu-id="a528f-198">To create a table of the individual objects, use the pipeline operator to pipe the objects to `ConvertTo-Html`.</span></span>

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

### <span data-ttu-id="a528f-199">-Meta</span><span class="sxs-lookup"><span data-stu-id="a528f-199">-Meta</span></span>

<span data-ttu-id="a528f-200">여는 태그에 추가할 텍스트를 지정 합니다 `<meta>` .</span><span class="sxs-lookup"><span data-stu-id="a528f-200">Specifies text to add to the opening `<meta>` tag.</span></span> <span data-ttu-id="a528f-201">기본적으로 해당 위치에는 텍스트가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-201">By default, there is no text in that position.</span></span>

<span data-ttu-id="a528f-202">이 매개 변수는 PowerShell 6.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-202">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="a528f-203">-PostContent</span><span class="sxs-lookup"><span data-stu-id="a528f-203">-PostContent</span></span>

<span data-ttu-id="a528f-204">닫는 `</TABLE>` 태그 뒤에 추가할 텍스트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-204">Specifies text to add after the closing `</TABLE>` tag.</span></span> <span data-ttu-id="a528f-205">기본적으로 해당 위치에는 텍스트가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-205">By default, there is no text in that position.</span></span>

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

### <span data-ttu-id="a528f-206">-PreContent</span><span class="sxs-lookup"><span data-stu-id="a528f-206">-PreContent</span></span>

<span data-ttu-id="a528f-207">여는 `<TABLE>` 태그 앞에 추가할 텍스트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-207">Specifies text to add before the opening `<TABLE>` tag.</span></span> <span data-ttu-id="a528f-208">기본적으로 해당 위치에는 텍스트가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-208">By default, there is no text in that position.</span></span>

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

### <span data-ttu-id="a528f-209">-속성</span><span class="sxs-lookup"><span data-stu-id="a528f-209">-Property</span></span>

<span data-ttu-id="a528f-210">지정한 개체 속성을 HTML에 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-210">Includes the specified properties of the objects in the HTML.</span></span> <span data-ttu-id="a528f-211">**Property** 매개 변수 값은 새 계산 된 속성 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-211">The value of the **Property** parameter can be a new calculated property.</span></span> <span data-ttu-id="a528f-212">계산 된 속성은 스크립트 블록이 나 해시 테이블 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-212">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="a528f-213">유효한 키-값 쌍은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-213">Valid key-value pairs are:</span></span>

- <span data-ttu-id="a528f-214">이름 (또는 레이블)- `<string>` (PowerShell 6.x에 추가 됨)</span><span class="sxs-lookup"><span data-stu-id="a528f-214">Name (or label) - `<string>` (added in PowerShell 6.x)</span></span>
- <span data-ttu-id="a528f-215">식 `<string>` 또는 `<script block>`</span><span class="sxs-lookup"><span data-stu-id="a528f-215">Expression - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="a528f-216">FormatString `<string>`</span><span class="sxs-lookup"><span data-stu-id="a528f-216">FormatString - `<string>`</span></span>
- <span data-ttu-id="a528f-217">Width- `<int32>` -다음 보다 커야 함 `0`</span><span class="sxs-lookup"><span data-stu-id="a528f-217">Width - `<int32>` - must be greater than `0`</span></span>
- <span data-ttu-id="a528f-218">맞춤-값은 `Left` , `Center` 또는 일 수 있습니다. `Right`</span><span class="sxs-lookup"><span data-stu-id="a528f-218">Alignment - value can be `Left`, `Center`, or `Right`</span></span>

<span data-ttu-id="a528f-219">자세한 내용은 [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a528f-219">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

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

### <span data-ttu-id="a528f-220">-Title</span><span class="sxs-lookup"><span data-stu-id="a528f-220">-Title</span></span>

<span data-ttu-id="a528f-221">`<TITLE>` 태그 사이에 표시되는 텍스트인 HTML 파일의 제목을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-221">Specifies a title for the HTML file, that is, the text that appears between the `<TITLE>` tags.</span></span>

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

### <span data-ttu-id="a528f-222">-전환</span><span class="sxs-lookup"><span data-stu-id="a528f-222">-Transitional</span></span>

<span data-ttu-id="a528f-223">**Doctype** 을 **xhtml 전환 dtd** 로 변경 하 고, 기본 **doctype** 은 **xhtml Strict dtd** 입니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-223">Changes the **DOCTYPE** to **XHTML Transitional DTD**, Default **DOCTYPE** is **XHTML Strict DTD**.</span></span>

<span data-ttu-id="a528f-224">이 매개 변수는 PowerShell 6.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-224">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="a528f-225">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a528f-225">CommonParameters</span></span>

<span data-ttu-id="a528f-226">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a528f-226">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a528f-227">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a528f-227">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a528f-228">입력</span><span class="sxs-lookup"><span data-stu-id="a528f-228">INPUTS</span></span>

### <span data-ttu-id="a528f-229">System.web. PSObject</span><span class="sxs-lookup"><span data-stu-id="a528f-229">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="a528f-230">모든 .NET 개체를로 파이프 할 수 있습니다 `ConvertTo-Html` .</span><span class="sxs-lookup"><span data-stu-id="a528f-230">You can pipe any .NET object to `ConvertTo-Html`.</span></span>

## <span data-ttu-id="a528f-231">출력</span><span class="sxs-lookup"><span data-stu-id="a528f-231">OUTPUTS</span></span>

### <span data-ttu-id="a528f-232">System.string 또는 System.Xml.Xml문서</span><span class="sxs-lookup"><span data-stu-id="a528f-232">System.String or System.Xml.XmlDocument</span></span>

<span data-ttu-id="a528f-233">`ConvertTo-Html` 유효한 HTML을 구성 하는 일련의 문자열을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-233">`ConvertTo-Html` returns series of strings that comprise valid HTML.</span></span>

## <span data-ttu-id="a528f-234">참고</span><span class="sxs-lookup"><span data-stu-id="a528f-234">NOTES</span></span>

<span data-ttu-id="a528f-235">이 cmdlet을 사용 하려면 하나 이상의 개체를 cmdlet으로 파이프 하거나 **InputObject** 매개 변수를 사용 하 여 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-235">To use this cmdlet, pipe one or more objects to the cmdlet or use the **InputObject** parameter to specify the object.</span></span> <span data-ttu-id="a528f-236">입력이 여러 개체로 구성된 경우에는 이 두 방법의 출력이 전혀 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-236">When the input consists of multiple objects, the output of these two methods is quite different.</span></span>

- <span data-ttu-id="a528f-237">여러 개체를 cmdlet으로 파이프 하면 PowerShell은 개체를 한 번에 하나씩 cmdlet으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-237">When you pipe multiple objects to a cmdlet, PowerShell sends the objects to the cmdlet one at a time.</span></span> <span data-ttu-id="a528f-238">따라서는 `ConvertTo-Html` 개별 개체를 표시 하는 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-238">As a result, `ConvertTo-Html` creates a table that displays the individual objects.</span></span> <span data-ttu-id="a528f-239">예를 들어 컴퓨터의 프로세스를로 파이프 하는 경우 `ConvertTo-Html` 결과 테이블에 모든 프로세스가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-239">For example, if you pipe the processes on a computer to `ConvertTo-Html`, the resulting table displays all of the processes.</span></span>

- <span data-ttu-id="a528f-240">**InputObject** 매개 변수를 사용 하 여 여러 개체를 전송 하는 경우는 `ConvertTo-Html` 이러한 개체를 컬렉션 또는 배열로 받습니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-240">When you use the **InputObject** parameter to submit multiple objects, `ConvertTo-Html` receives these objects as a collection or as an array.</span></span> <span data-ttu-id="a528f-241">따라서 배열의 항목이 아니라 배열과 해당 속성을 표시하는 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-241">As a result, it creates a table that displays the array and its properties, not the items in the array.</span></span> <span data-ttu-id="a528f-242">예를 들어 **InputObject** 를 사용 하 여 컴퓨터의 프로세스를로 전송 하 `ConvertTo-Html` 는 경우 결과 테이블에 개체 배열 및 해당 속성이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-242">For example, if you use **InputObject** to submit the processes on a computer to `ConvertTo-Html`, the resulting table displays an object array and its properties.</span></span>

  <span data-ttu-id="a528f-243">XHTML Strict DTD를 준수 하기 위해 DOCTYPE 태그가 적절 하 게 수정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a528f-243">To comply with the XHTML Strict DTD, the DOCTYPE tag is modified accordingly:</span></span>

   `<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"   "https://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd"\>`

## <span data-ttu-id="a528f-244">관련 링크</span><span class="sxs-lookup"><span data-stu-id="a528f-244">RELATED LINKS</span></span>

[<span data-ttu-id="a528f-245">about_Calculated_Properties</span><span class="sxs-lookup"><span data-stu-id="a528f-245">about_Calculated_Properties</span></span>](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[<span data-ttu-id="a528f-246">ConvertTo-Csv</span><span class="sxs-lookup"><span data-stu-id="a528f-246">ConvertTo-Csv</span></span>](ConvertTo-Csv.md)

[<span data-ttu-id="a528f-247">ConvertTo-Json</span><span class="sxs-lookup"><span data-stu-id="a528f-247">ConvertTo-Json</span></span>](ConvertTo-Json.md)

[<span data-ttu-id="a528f-248">ConvertTo-Xml</span><span class="sxs-lookup"><span data-stu-id="a528f-248">ConvertTo-Xml</span></span>](ConvertTo-Xml.md)

[<span data-ttu-id="a528f-249">Export-Clixml</span><span class="sxs-lookup"><span data-stu-id="a528f-249">Export-Clixml</span></span>](Export-Clixml.md)

[<span data-ttu-id="a528f-250">Import-Clixml</span><span class="sxs-lookup"><span data-stu-id="a528f-250">Import-Clixml</span></span>](Import-Clixml.md)
