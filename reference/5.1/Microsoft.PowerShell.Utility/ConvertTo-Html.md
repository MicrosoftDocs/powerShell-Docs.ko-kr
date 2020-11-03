---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertto-html?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-Html
ms.openlocfilehash: 618308bb03f47659b8fa932ac0bb029972546755
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/10/2020
ms.locfileid: "93219218"
---
# <span data-ttu-id="10835-103">ConvertTo-Html</span><span class="sxs-lookup"><span data-stu-id="10835-103">ConvertTo-Html</span></span>

## <span data-ttu-id="10835-104">개요</span><span class="sxs-lookup"><span data-stu-id="10835-104">SYNOPSIS</span></span>
<span data-ttu-id="10835-105">.NET 개체를 웹 브라우저에 표시할 수 있는 HTML로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="10835-105">Converts .NET objects into HTML that can be displayed in a Web browser.</span></span>

## <span data-ttu-id="10835-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="10835-106">SYNTAX</span></span>

### <span data-ttu-id="10835-107">페이지 (기본값)</span><span class="sxs-lookup"><span data-stu-id="10835-107">Page (Default)</span></span>

```
ConvertTo-Html [-InputObject <PSObject>] [[-Property] <Object[]>] [[-Body] <String[]>]
 [[-Head] <String[]>] [[-Title] <String>] [-As <String>] [-CssUri <Uri>] [-PostContent <String[]>]
 [-PreContent <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="10835-108">Fragment</span><span class="sxs-lookup"><span data-stu-id="10835-108">Fragment</span></span>

```
ConvertTo-Html [-InputObject <PSObject>] [[-Property] <Object[]>] [-As <String>] [-Fragment]
 [-PostContent <String[]>] [-PreContent <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="10835-109">설명</span><span class="sxs-lookup"><span data-stu-id="10835-109">DESCRIPTION</span></span>

<span data-ttu-id="10835-110">`ConvertTo-Html`Cmdlet은 .net 개체를 웹 브라우저에 표시할 수 있는 HTML로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="10835-110">The `ConvertTo-Html` cmdlet converts .NET objects into HTML that can be displayed in a Web browser.</span></span> <span data-ttu-id="10835-111">이 cmdlet을 사용하여 명령 출력을 웹 페이지에 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10835-111">You can use this cmdlet to display the output of a command in a Web page.</span></span>

<span data-ttu-id="10835-112">의 매개 변수를 사용 하 여 `ConvertTo-Html` 개체 속성을 선택 하 고, 테이블 또는 목록 형식을 지정 하 고, HTML 페이지 제목을 지정 하 고, 개체 앞뒤에 텍스트를 추가 하 고, STRICT DTD 페이지 대신 테이블 또는 목록 조각만 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10835-112">You can use the parameters of `ConvertTo-Html` to select object properties, to specify a table or list format, to specify the HTML page title, to add text before and after the object, and to return only the table or list fragment, instead of a strict DTD page.</span></span>

<span data-ttu-id="10835-113">에 여러 개체를 제출 하는 경우 `ConvertTo-Html` PowerShell은 제출한 첫 번째 개체의 속성을 기반으로 테이블 (또는 목록)을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="10835-113">When you submit multiple objects to `ConvertTo-Html`, PowerShell creates the table (or list) based on the properties of the first object that you submit.</span></span> <span data-ttu-id="10835-114">나머지 개체에 지정한 속성이 하나도 없을 경우 해당 개체의 속성 값은 빈 셀이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10835-114">If the remaining objects do not have one of the specified properties, the property value of that object is an empty cell.</span></span> <span data-ttu-id="10835-115">나머지 개체에 추가 속성이 있을 경우 이러한 속성 값은 파일에 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="10835-115">If the remaining objects have additional properties, those property values are not included in the file.</span></span>

## <span data-ttu-id="10835-116">예제</span><span class="sxs-lookup"><span data-stu-id="10835-116">EXAMPLES</span></span>

### <span data-ttu-id="10835-117">예제 1: 날짜를 표시 하는 웹 페이지 만들기</span><span class="sxs-lookup"><span data-stu-id="10835-117">Example 1: Create a web page to display the date</span></span>

```powershell
ConvertTo-Html -InputObject (Get-Date)
```

<span data-ttu-id="10835-118">이 명령은 현재 날짜의 속성을 표시하는 HTML 페이지를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="10835-118">This command creates an HTML page that displays the properties of the current date.</span></span> <span data-ttu-id="10835-119">**InputObject** 매개 변수를 사용 하 여 명령의 결과를 `Get-Date` cmdlet에 제출 `ConvertTo-Html` 합니다.</span><span class="sxs-lookup"><span data-stu-id="10835-119">It uses the **InputObject** parameter to submit the results of a `Get-Date` command to the `ConvertTo-Html` cmdlet.</span></span>

### <span data-ttu-id="10835-120">예제 2: PowerShell 별칭을 표시 하는 웹 페이지 만들기</span><span class="sxs-lookup"><span data-stu-id="10835-120">Example 2: Create a web page to display PowerShell aliases</span></span>

```powershell
Get-Alias | ConvertTo-Html | Out-File aliases.htm
Invoke-Item aliases.htm
```

<span data-ttu-id="10835-121">이 명령은 현재 콘솔의 PowerShell 별칭을 나열 하는 HTML 페이지를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="10835-121">This command creates an HTML page that lists the PowerShell aliases in the current console.</span></span>

<span data-ttu-id="10835-122">이 명령은 cmdlet을 사용 하 여 `Get-Alias` 별칭을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="10835-122">The command uses the `Get-Alias` cmdlet to get the aliases.</span></span> <span data-ttu-id="10835-123">파이프라인 연산자 ()를 사용 하 여 `|` 별칭을 cmdlet으로 보내면이 `ConvertTo-Html` CMDLET이 HTML 페이지를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="10835-123">It uses the pipeline operator (`|`) to send the aliases to the `ConvertTo-Html` cmdlet, which creates the HTML page.</span></span> <span data-ttu-id="10835-124">또한이 명령은 cmdlet을 사용 하 여 `Out-File` HTML 코드를 파일에 보냅니다 `aliases.htm` .</span><span class="sxs-lookup"><span data-stu-id="10835-124">The command also uses the `Out-File` cmdlet to send the HTML code to the `aliases.htm` file.</span></span>

### <span data-ttu-id="10835-125">예제 3: PowerShell 이벤트를 표시 하는 웹 페이지 만들기</span><span class="sxs-lookup"><span data-stu-id="10835-125">Example 3: Create a web page to display PowerShell events</span></span>

```powershell
`Get-EventLog` -LogName "Windows PowerShell" | ConvertTo-Html | Out-File pslog.htm
```

<span data-ttu-id="10835-126">이 명령은 `pslog.htm` 로컬 컴퓨터의 Windows PowerShell 이벤트 로그에 이벤트를 표시 하는 이라는 HTML 페이지를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="10835-126">This command creates an HTML page called `pslog.htm` that displays the events in the Windows PowerShell event log on the local computer.</span></span>

<span data-ttu-id="10835-127">Cmdlet을 사용 하 여 `Get-EventLog` Windows PowerShell 로그의 이벤트를 가져온 다음 파이프라인 연산자 ()를 사용 하 여 `|` 이벤트를 cmdlet으로 보냅니다 `ConvertTo-Html` .</span><span class="sxs-lookup"><span data-stu-id="10835-127">It uses the `Get-EventLog` cmdlet to get the events in the Windows PowerShell log and then uses the pipeline operator (`|`) to send the events to the `ConvertTo-Html` cmdlet.</span></span> <span data-ttu-id="10835-128">또한이 명령은 cmdlet을 사용 하 여 `Out-File` HTML 코드를 파일에 보냅니다 `pslog.htm` .</span><span class="sxs-lookup"><span data-stu-id="10835-128">The command also uses the `Out-File` cmdlet to send the HTML code to the `pslog.htm` file.</span></span>

<span data-ttu-id="10835-129">또한이 명령은 cmdlet을 사용 하 여 `Out-File` HTML 코드를 파일에 보냅니다 `pslog.htm` .</span><span class="sxs-lookup"><span data-stu-id="10835-129">The command also uses the `Out-File` cmdlet to send the HTML code to the `pslog.htm` file.</span></span>

### <span data-ttu-id="10835-130">예제 4: 프로세스를 표시 하는 웹 페이지 만들기</span><span class="sxs-lookup"><span data-stu-id="10835-130">Example 4: Create a web page to display processes</span></span>

```powershell
Get-Process |
  ConvertTo-Html -Property Name, Path, Company -Title "Process Information" |
    Out-File proc.htm
Invoke-Item proc.htm
```

<span data-ttu-id="10835-131">이 명령은 로컬 컴퓨터에 있는 프로세스의 이름, 경로 및 회사를 나열하는 HTML 페이지를 만들어서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="10835-131">These commands create and open an HTML page that lists the name, path, and company of the processes on the local computer.</span></span>

<span data-ttu-id="10835-132">첫 번째 명령은 cmdlet을 사용 하 여 `Get-Process` 컴퓨터에서 실행 중인 프로세스를 나타내는 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="10835-132">The first command uses the `Get-Process` cmdlet to get objects that represent the processes running on the computer.</span></span> <span data-ttu-id="10835-133">이 명령은 파이프라인 연산자 ()를 사용 하 여 `|` 프로세스 개체를 cmdlet으로 보냅니다 `ConvertTo-Html` .</span><span class="sxs-lookup"><span data-stu-id="10835-133">The command uses the pipeline operator (`|`) to send the process objects to the `ConvertTo-Html` cmdlet.</span></span>

<span data-ttu-id="10835-134">이 명령은 **Property** 매개 변수를 사용 하 여 테이블에 포함할 프로세스 개체의 세 가지 속성을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="10835-134">The command uses the **Property** parameter to select three properties of the process objects to be included in the table.</span></span> <span data-ttu-id="10835-135">이 명령은 **title** 매개 변수를 사용 하 여 HTML 페이지의 제목을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="10835-135">The command uses the **Title** parameter to specify a title for the HTML page.</span></span> <span data-ttu-id="10835-136">또한이 명령은 cmdlet을 사용 하 여 `Out-File` 결과 HTML을 Proc.htm 이라는 파일로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="10835-136">The command also uses the `Out-File` cmdlet to send the resulting HTML to a file named Proc.htm.</span></span>

<span data-ttu-id="10835-137">두 번째 명령은 cmdlet을 사용 하 여 `Invoke-Item` 를 `Proc.htm` 기본 브라우저에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="10835-137">The second command uses the `Invoke-Item` cmdlet to open the `Proc.htm` in the default browser.</span></span>

### <span data-ttu-id="10835-138">예 5: 서비스 개체를 표시 하는 웹 페이지 만들기</span><span class="sxs-lookup"><span data-stu-id="10835-138">Example 5: Create a web page to display service objects</span></span>

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

<span data-ttu-id="10835-139">이 명령은 cmdlet이 반환 하는 서비스 개체의 HTML 페이지를 만듭니다 `Get-Service` .</span><span class="sxs-lookup"><span data-stu-id="10835-139">This command creates an HTML page of the service objects that the `Get-Service` cmdlet returns.</span></span> <span data-ttu-id="10835-140">이 명령은 **CssUri** 매개 변수를 사용 하 여 HTML 페이지의 css 스타일 시트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="10835-140">The command uses the **CssUri** parameter to specify a cascading style sheet for the HTML page.</span></span>

<span data-ttu-id="10835-141">**CssUri** 매개 변수는 `<link rel="stylesheet" type="text/css" href="test.css">` 결과 HTML에 추가 태그를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="10835-141">The **CssUri** parameter adds an additional `<link rel="stylesheet" type="text/css" href="test.css">` tag to the resulting HTML.</span></span> <span data-ttu-id="10835-142">태그의 HREF 특성에는 스타일시트의 이름이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="10835-142">The HREF attribute in the tag contains the name of the style sheet.</span></span>

### <span data-ttu-id="10835-143">예제 6: 서비스 개체를 표시 하는 웹 페이지 만들기</span><span class="sxs-lookup"><span data-stu-id="10835-143">Example 6: Create a web page to display service objects</span></span>

```powershell
Get-Service | ConvertTo-Html -As LIST | Out-File services.htm
```

<span data-ttu-id="10835-144">이 명령은 cmdlet이 반환 하는 서비스 개체의 HTML 페이지를 만듭니다 `Get-Service` .</span><span class="sxs-lookup"><span data-stu-id="10835-144">This command creates an HTML page of the service objects that the `Get-Service` cmdlet returns.</span></span> <span data-ttu-id="10835-145">이 명령은 **As** 매개 변수를 사용 하 여 목록 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="10835-145">The command uses the **As** parameter to specify a list format.</span></span> <span data-ttu-id="10835-146">Cmdlet은 `Out-File` 결과 HTML을 파일에 보냅니다 `Services.htm` .</span><span class="sxs-lookup"><span data-stu-id="10835-146">The cmdlet `Out-File` sends the resulting HTML to the `Services.htm` file.</span></span>

### <span data-ttu-id="10835-147">예 7: 현재 날짜에 대 한 웹 테이블 만들기</span><span class="sxs-lookup"><span data-stu-id="10835-147">Example 7: Create a web table for the current date</span></span>

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

<span data-ttu-id="10835-148">이 명령은 `ConvertTo-Html` 를 사용 하 여 현재 날짜의 HTML 테이블을 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="10835-148">This command uses `ConvertTo-Html` to generate an HTML table of the current date.</span></span> <span data-ttu-id="10835-149">이 명령은 cmdlet을 사용 하 여 `Get-Date` 현재 날짜를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="10835-149">The command uses the `Get-Date` cmdlet to get the current date.</span></span> <span data-ttu-id="10835-150">파이프라인 연산자 (|)를 사용 하 여 결과를 cmdlet으로 보냅니다 `ConvertTo-Html` .</span><span class="sxs-lookup"><span data-stu-id="10835-150">It uses a pipeline operator (|) to send the results to the `ConvertTo-Html` cmdlet.</span></span>

<span data-ttu-id="10835-151">이 `ConvertTo-Html` 명령은 출력을 HTML 테이블로 제한 하는 **Fragment** 매개 변수를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="10835-151">The `ConvertTo-Html` command includes the **Fragment** parameter, which limits the output to an HTML table.</span></span> <span data-ttu-id="10835-152">따라서 `<HEAD>` 및 `<BODY>` 태그와 같은 HTML 페이지의 다른 요소는 생략됩니다.</span><span class="sxs-lookup"><span data-stu-id="10835-152">As a result, the other elements of an HTML page, such as the `<HEAD>` and `<BODY>` tags, are omitted.</span></span>

### <span data-ttu-id="10835-153">예 8: PowerShell 이벤트를 표시 하는 웹 페이지 만들기</span><span class="sxs-lookup"><span data-stu-id="10835-153">Example 8: Create a web page to display PowerShell events</span></span>

```powershell
Get-EventLog -Log "Windows PowerShell" | ConvertTo-Html -Property id, level, task
```

<span data-ttu-id="10835-154">이 명령은 cmdlet을 사용 하 여 `Get-EventLog` Windows PowerShell 이벤트 로그에서 이벤트를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="10835-154">This command uses the `Get-EventLog` cmdlet to get events from the Windows PowerShell event log.</span></span>

<span data-ttu-id="10835-155">파이프라인 연산자 ()를 사용 하 여 `|` 이벤트를 cmdlet으로 보내면이 `ConvertTo-Html` cmdlet이 이벤트를 HTML 형식으로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="10835-155">It uses a pipeline operator (`|`) to send the events to the `ConvertTo-Html` cmdlet, which converts the events to HTML format.</span></span>

<span data-ttu-id="10835-156">`ConvertTo-Html`이 명령은 **Property** 매개 변수를 사용 하 여 이벤트의 **ID** , **Level** 및 **Task** 속성만 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="10835-156">The `ConvertTo-Html` command uses the **Property** parameter to select only the **ID** , **Level** , and **Task** properties of the event.</span></span>

### <span data-ttu-id="10835-157">예 9: 지정 된 서비스를 표시 하는 웹 페이지 만들기</span><span class="sxs-lookup"><span data-stu-id="10835-157">Example 9: Create a web page to display specified services</span></span>

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

<span data-ttu-id="10835-158">이 명령은로 시작 하는 컴퓨터의 서비스를 표시 하는 웹 페이지를 만들고 엽니다. 의 **Title** , **Body** , **precontent** 및 **postcontent** 매개 변수를 사용 하 여 `ConvertTo-Html` 출력을 사용자 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="10835-158">This command creates and opens a Web page that displays the services on the computer that begin with A. It uses the **Title** , **Body** , **PreContent** , and **PostContent** parameters of `ConvertTo-Html` to customize the output.</span></span>

<span data-ttu-id="10835-159">명령의 첫 번째 부분에서는 cmdlet을 사용 하 여 `Get-Service` 로 시작 하는 컴퓨터의 서비스를 가져옵니다. 이 명령은 파이프라인 연산자 ()를 사용 하 여 `|` 결과를 cmdlet으로 보냅니다 `ConvertTo-Html` .</span><span class="sxs-lookup"><span data-stu-id="10835-159">The first part of the command uses the `Get-Service` cmdlet to get the services on the computer that begin with A. The command uses a pipeline operator (`|`) to send the results to the `ConvertTo-Html` cmdlet.</span></span> <span data-ttu-id="10835-160">또한이 명령은 cmdlet을 사용 하 여 `Out-File` 출력을 Services.htm 파일로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="10835-160">The command also uses the `Out-File` cmdlet to send the output to the Services.htm file.</span></span>

<span data-ttu-id="10835-161">세미콜론 ( `;` )을 사용 하면 첫 번째 명령이 끝나고 두 번째 명령이 시작 됩니다 .이 명령은 cmdlet을 사용 하 여 `Invoke-Item` `Services.htm` 기본 브라우저에서 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="10835-161">A semicolon (`;`) ends the first command and starts a second command, which uses the `Invoke-Item` cmdlet to open the `Services.htm` file in the default browser.</span></span>

## <span data-ttu-id="10835-162">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="10835-162">PARAMETERS</span></span>

### <span data-ttu-id="10835-163">-As</span><span class="sxs-lookup"><span data-stu-id="10835-163">-As</span></span>

<span data-ttu-id="10835-164">개체를 테이블 형식으로 지정할지, 아니면 목록 형식으로 지정할지 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="10835-164">Determines whether the object is formatted as a table or a list.</span></span> <span data-ttu-id="10835-165">유효한 값은 **Table** 및 **List** 입니다.</span><span class="sxs-lookup"><span data-stu-id="10835-165">Valid values are **Table** and **List**.</span></span> <span data-ttu-id="10835-166">기본값은 **Table** 입니다.</span><span class="sxs-lookup"><span data-stu-id="10835-166">The default value is **Table**.</span></span>

<span data-ttu-id="10835-167">**테이블** 값은 PowerShell 테이블 형식과 유사한 HTML 테이블을 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="10835-167">The **Table** value generates an HTML table that resembles the PowerShell table format.</span></span> <span data-ttu-id="10835-168">머리글 행은 속성 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="10835-168">The header row displays the property names.</span></span> <span data-ttu-id="10835-169">각 테이블 행은 개체를 나타내고 개체의 각 속성 값을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="10835-169">Each table row represents an object and displays the object's values for each property.</span></span>

<span data-ttu-id="10835-170">**목록** 값은 PowerShell 목록 형식과 유사한 각 개체에 대해 2 열 HTML 테이블을 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="10835-170">The **List** value generates a two-column HTML table for each object that resembles the PowerShell list format.</span></span> <span data-ttu-id="10835-171">첫 번째 열에는 속성 이름이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10835-171">The first column displays the property name.</span></span> <span data-ttu-id="10835-172">두 번째 열에는 속성 값이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10835-172">The second column displays the property value.</span></span>

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

### <span data-ttu-id="10835-173">-본문</span><span class="sxs-lookup"><span data-stu-id="10835-173">-Body</span></span>

<span data-ttu-id="10835-174">여는 `<BODY>` 태그 뒤에 추가할 텍스트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="10835-174">Specifies the text to add after the opening `<BODY>` tag.</span></span> <span data-ttu-id="10835-175">기본적으로 해당 위치에는 텍스트가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="10835-175">By default, there is no text in that position.</span></span>

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

### <span data-ttu-id="10835-176">-CssUri</span><span class="sxs-lookup"><span data-stu-id="10835-176">-CssUri</span></span>

<span data-ttu-id="10835-177">HTML 파일에 적용되는 CSS 스타일시트의 URI(Uniform Resource Identifier)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="10835-177">Specifies the Uniform Resource Identifier (URI) of the cascading style sheet (CSS) that is applied to the HTML file.</span></span> <span data-ttu-id="10835-178">이 URI는 출력의 스타일시트 링크에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="10835-178">The URI is included in a style sheet link in the output.</span></span>

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

### <span data-ttu-id="10835-179">-조각</span><span class="sxs-lookup"><span data-stu-id="10835-179">-Fragment</span></span>

<span data-ttu-id="10835-180">HTML 테이블만 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="10835-180">Generates only an HTML table.</span></span> <span data-ttu-id="10835-181">HTML, HEAD, TITLE 및 BODY 태그는 생략됩니다.</span><span class="sxs-lookup"><span data-stu-id="10835-181">The HTML, HEAD, TITLE, and BODY tags are omitted.</span></span>

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

### <span data-ttu-id="10835-182">-Head</span><span class="sxs-lookup"><span data-stu-id="10835-182">-Head</span></span>

<span data-ttu-id="10835-183">`<HEAD>` 태그의 내용을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="10835-183">Specifies the content of the `<HEAD>` tag.</span></span> <span data-ttu-id="10835-184">기본값은 `<title\>HTML TABLE</title>`입니다.</span><span class="sxs-lookup"><span data-stu-id="10835-184">The default is `<title\>HTML TABLE</title>`.</span></span> <span data-ttu-id="10835-185">**Head** 매개 변수를 사용 하는 경우 **Title** 매개 변수는 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10835-185">If you use the **Head** parameter, the **Title** parameter is ignored.</span></span>

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

### <span data-ttu-id="10835-186">-InputObject</span><span class="sxs-lookup"><span data-stu-id="10835-186">-InputObject</span></span>

<span data-ttu-id="10835-187">HTML로 표시할 개체를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="10835-187">Specifies the objects to be represented in HTML.</span></span> <span data-ttu-id="10835-188">개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="10835-188">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span>

<span data-ttu-id="10835-189">이 매개 변수를 사용 하 여 컴퓨터의 모든 서비스와 같은 여러 개체를 전송 하는 경우 `ConvertTo-Html` 컬렉션 또는 개체 배열의 속성을 표시 하는 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="10835-189">If you use this parameter to submit multiple objects, such as all of the services on a computer, `ConvertTo-Html` creates a table that displays the properties of a collection or of an array of objects.</span></span> <span data-ttu-id="10835-190">개별 개체의 테이블을 만들려면 파이프라인 연산자를 사용 하 여 개체를로 파이프 합니다 `ConvertTo-Html` .</span><span class="sxs-lookup"><span data-stu-id="10835-190">To create a table of the individual objects, use the pipeline operator to pipe the objects to `ConvertTo-Html`.</span></span>

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

### <span data-ttu-id="10835-191">-PostContent</span><span class="sxs-lookup"><span data-stu-id="10835-191">-PostContent</span></span>

<span data-ttu-id="10835-192">닫는 `</TABLE>` 태그 뒤에 추가할 텍스트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="10835-192">Specifies text to add after the closing `</TABLE>` tag.</span></span> <span data-ttu-id="10835-193">기본적으로 해당 위치에는 텍스트가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="10835-193">By default, there is no text in that position.</span></span>

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

### <span data-ttu-id="10835-194">-PreContent</span><span class="sxs-lookup"><span data-stu-id="10835-194">-PreContent</span></span>

<span data-ttu-id="10835-195">여는 `<TABLE>` 태그 앞에 추가할 텍스트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="10835-195">Specifies text to add before the opening `<TABLE>` tag.</span></span> <span data-ttu-id="10835-196">기본적으로 해당 위치에는 텍스트가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="10835-196">By default, there is no text in that position.</span></span>

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

### <span data-ttu-id="10835-197">-속성</span><span class="sxs-lookup"><span data-stu-id="10835-197">-Property</span></span>

<span data-ttu-id="10835-198">지정한 개체 속성을 HTML에 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="10835-198">Includes the specified properties of the objects in the HTML.</span></span> <span data-ttu-id="10835-199">**Property** 매개 변수 값은 새 계산 된 속성 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10835-199">The value of the **Property** parameter can be a new calculated property.</span></span> <span data-ttu-id="10835-200">계산 된 속성은 스크립트 블록이 나 해시 테이블 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10835-200">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="10835-201">유효한 키-값 쌍은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="10835-201">Valid key-value pairs are:</span></span>

- <span data-ttu-id="10835-202">식 `<string>` 또는 `<script block>`</span><span class="sxs-lookup"><span data-stu-id="10835-202">Expression - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="10835-203">FormatString `<string>`</span><span class="sxs-lookup"><span data-stu-id="10835-203">FormatString - `<string>`</span></span>
- <span data-ttu-id="10835-204">Width- `<int32>` -다음 보다 커야 함 `0`</span><span class="sxs-lookup"><span data-stu-id="10835-204">Width - `<int32>` - must be greater than `0`</span></span>
- <span data-ttu-id="10835-205">맞춤-값은 `Left` , `Center` 또는 일 수 있습니다. `Right`</span><span class="sxs-lookup"><span data-stu-id="10835-205">Alignment - value can be `Left`, `Center`, or `Right`</span></span>

<span data-ttu-id="10835-206">자세한 내용은 [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="10835-206">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

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

### <span data-ttu-id="10835-207">-Title</span><span class="sxs-lookup"><span data-stu-id="10835-207">-Title</span></span>

<span data-ttu-id="10835-208">`<TITLE>` 태그 사이에 표시되는 텍스트인 HTML 파일의 제목을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="10835-208">Specifies a title for the HTML file, that is, the text that appears between the `<TITLE>` tags.</span></span>

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

### <span data-ttu-id="10835-209">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="10835-209">CommonParameters</span></span>

<span data-ttu-id="10835-210">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="10835-210">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="10835-211">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="10835-211">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="10835-212">입력</span><span class="sxs-lookup"><span data-stu-id="10835-212">INPUTS</span></span>

### <span data-ttu-id="10835-213">System.web. PSObject</span><span class="sxs-lookup"><span data-stu-id="10835-213">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="10835-214">모든 .NET 개체를로 파이프 할 수 있습니다 `ConvertTo-Html` .</span><span class="sxs-lookup"><span data-stu-id="10835-214">You can pipe any .NET object to `ConvertTo-Html`.</span></span>

## <span data-ttu-id="10835-215">출력</span><span class="sxs-lookup"><span data-stu-id="10835-215">OUTPUTS</span></span>

### <span data-ttu-id="10835-216">System.string 또는 System.Xml.Xml문서</span><span class="sxs-lookup"><span data-stu-id="10835-216">System.String or System.Xml.XmlDocument</span></span>

<span data-ttu-id="10835-217">`ConvertTo-Html` 유효한 HTML을 구성 하는 일련의 문자열을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="10835-217">`ConvertTo-Html` returns series of strings that comprise valid HTML.</span></span>

## <span data-ttu-id="10835-218">참고</span><span class="sxs-lookup"><span data-stu-id="10835-218">NOTES</span></span>

<span data-ttu-id="10835-219">이 cmdlet을 사용 하려면 하나 이상의 개체를 cmdlet으로 파이프 하거나 **InputObject** 매개 변수를 사용 하 여 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="10835-219">To use this cmdlet, pipe one or more objects to the cmdlet or use the **InputObject** parameter to specify the object.</span></span> <span data-ttu-id="10835-220">입력이 여러 개체로 구성된 경우에는 이 두 방법의 출력이 전혀 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="10835-220">When the input consists of multiple objects, the output of these two methods is quite different.</span></span>

- <span data-ttu-id="10835-221">여러 개체를 cmdlet으로 파이프 하면 PowerShell은 개체를 한 번에 하나씩 cmdlet으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="10835-221">When you pipe multiple objects to a cmdlet, PowerShell sends the objects to the cmdlet one at a time.</span></span> <span data-ttu-id="10835-222">따라서는 `ConvertTo-Html` 개별 개체를 표시 하는 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="10835-222">As a result, `ConvertTo-Html` creates a table that displays the individual objects.</span></span> <span data-ttu-id="10835-223">예를 들어 컴퓨터의 프로세스를로 파이프 하는 경우 `ConvertTo-Html` 결과 테이블에 모든 프로세스가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10835-223">For example, if you pipe the processes on a computer to `ConvertTo-Html`, the resulting table displays all of the processes.</span></span>

- <span data-ttu-id="10835-224">**InputObject** 매개 변수를 사용 하 여 여러 개체를 전송 하는 경우는 `ConvertTo-Html` 이러한 개체를 컬렉션 또는 배열로 받습니다.</span><span class="sxs-lookup"><span data-stu-id="10835-224">When you use the **InputObject** parameter to submit multiple objects, `ConvertTo-Html` receives these objects as a collection or as an array.</span></span> <span data-ttu-id="10835-225">따라서 배열의 항목이 아니라 배열과 해당 속성을 표시하는 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="10835-225">As a result, it creates a table that displays the array and its properties, not the items in the array.</span></span> <span data-ttu-id="10835-226">예를 들어 **InputObject** 를 사용 하 여 컴퓨터의 프로세스를로 전송 하 `ConvertTo-Html` 는 경우 결과 테이블에 개체 배열 및 해당 속성이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10835-226">For example, if you use **InputObject** to submit the processes on a computer to `ConvertTo-Html`, the resulting table displays an object array and its properties.</span></span>

  <span data-ttu-id="10835-227">XHTML Strict DTD를 준수 하기 위해 DOCTYPE 태그가 적절 하 게 수정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10835-227">To comply with the XHTML Strict DTD, the DOCTYPE tag is modified accordingly:</span></span>

   `<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"   "https://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd"\>`

## <span data-ttu-id="10835-228">관련 링크</span><span class="sxs-lookup"><span data-stu-id="10835-228">RELATED LINKS</span></span>

[<span data-ttu-id="10835-229">about_Calculated_Properties</span><span class="sxs-lookup"><span data-stu-id="10835-229">about_Calculated_Properties</span></span>](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[<span data-ttu-id="10835-230">ConvertTo-Csv</span><span class="sxs-lookup"><span data-stu-id="10835-230">ConvertTo-Csv</span></span>](ConvertTo-Csv.md)

[<span data-ttu-id="10835-231">ConvertTo-Json</span><span class="sxs-lookup"><span data-stu-id="10835-231">ConvertTo-Json</span></span>](ConvertTo-Json.md)

[<span data-ttu-id="10835-232">ConvertTo-Xml</span><span class="sxs-lookup"><span data-stu-id="10835-232">ConvertTo-Xml</span></span>](ConvertTo-Xml.md)

[<span data-ttu-id="10835-233">Export-Clixml</span><span class="sxs-lookup"><span data-stu-id="10835-233">Export-Clixml</span></span>](Export-Clixml.md)

[<span data-ttu-id="10835-234">Import-Clixml</span><span class="sxs-lookup"><span data-stu-id="10835-234">Import-Clixml</span></span>](Import-Clixml.md)
