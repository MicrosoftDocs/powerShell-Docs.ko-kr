---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 08/23/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-help?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Help
ms.openlocfilehash: 691709fe3f5e4908ab3203df73f636981adf560c
ms.sourcegitcommit: b7ff031a12afd04910aeb98345ebee92f5845b0c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/28/2020
ms.locfileid: "93219025"
---
# <span data-ttu-id="2da13-103">Get-Help</span><span class="sxs-lookup"><span data-stu-id="2da13-103">Get-Help</span></span>

## <span data-ttu-id="2da13-104">개요</span><span class="sxs-lookup"><span data-stu-id="2da13-104">SYNOPSIS</span></span>
<span data-ttu-id="2da13-105">PowerShell 명령 및 개념에 대 한 정보를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-105">Displays information about PowerShell commands and concepts.</span></span>

## <span data-ttu-id="2da13-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2da13-106">SYNTAX</span></span>

### <span data-ttu-id="2da13-107">AllUsersView (기본값)</span><span class="sxs-lookup"><span data-stu-id="2da13-107">AllUsersView (Default)</span></span>

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Full] [-Component <String[]>]
 [-Functionality <String[]>] [-Role <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="2da13-108">DetailedView</span><span class="sxs-lookup"><span data-stu-id="2da13-108">DetailedView</span></span>

```
Get-Help [[-Name] <String>] -Detailed [-Path <String>] [-Category <String[]>]
 [-Component <String[]>] [-Functionality <String[]>] [-Role <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="2da13-109">예</span><span class="sxs-lookup"><span data-stu-id="2da13-109">Examples</span></span>

```
Get-Help [[-Name] <String>] -Examples [-Path <String>] [-Category <String[]>]
 [-Component <String[]>] [-Functionality <String[]>] [-Role <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="2da13-110">매개 변수</span><span class="sxs-lookup"><span data-stu-id="2da13-110">Parameters</span></span>

```
Get-Help [[-Name] <String>] -Parameter <String[]> [-Path <String>] [-Category <String[]>]
 [-Component <String[]>] [-Functionality <String[]>] [-Role <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="2da13-111">온라인</span><span class="sxs-lookup"><span data-stu-id="2da13-111">Online</span></span>

```
Get-Help [[-Name] <String>] -Online [-Path <String>] [-Category <String[]>] [-Component <String[]>]
 [-Functionality <String[]>] [-Role <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="2da13-112">설명</span><span class="sxs-lookup"><span data-stu-id="2da13-112">DESCRIPTION</span></span>

<span data-ttu-id="2da13-113">`Get-Help`Cmdlet은 cmdlet, 함수, CIM(Common Information Model) (CIM) 명령, 워크플로, 공급자, 별칭 및 스크립트를 포함 하 여 PowerShell 개념 및 명령에 대 한 정보를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-113">The `Get-Help` cmdlet displays information about PowerShell concepts and commands, including cmdlets, functions, Common Information Model (CIM) commands, workflows, providers, aliases, and scripts.</span></span>

<span data-ttu-id="2da13-114">PowerShell cmdlet에 대 한 도움말을 보려면을 입력 하 고 `Get-Help` cmdlet 이름 (예:)을 입력 `Get-Help Get-Process` 합니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-114">To get help for a PowerShell cmdlet, type `Get-Help` followed by the cmdlet name, such as: `Get-Help Get-Process`.</span></span>

<span data-ttu-id="2da13-115">PowerShell의 개념 도움말 문서는 **about_Comparison_Operators** 와 같은 **about_** 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-115">Conceptual help articles in PowerShell begin with **about_** , such as **about_Comparison_Operators**.</span></span> <span data-ttu-id="2da13-116">모든 **about_** 문서를 보려면을 입력 `Get-Help about_*` 합니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-116">To see all **about_** articles, type `Get-Help about_*`.</span></span> <span data-ttu-id="2da13-117">특정 아티클을 보려면 `Get-Help about_<article-name>` 와 같은를 입력 `Get-Help about_Comparison_Operators` 합니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-117">To see a particular article, type `Get-Help about_<article-name>`, such as `Get-Help about_Comparison_Operators`.</span></span>

<span data-ttu-id="2da13-118">PowerShell 공급자에 대 한 도움말을 보려면를 입력 한 `Get-Help` 다음 공급자 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-118">To get help for a PowerShell provider, type `Get-Help` followed by the provider name.</span></span> <span data-ttu-id="2da13-119">예를 들어 인증서 공급자에 대 한 도움말을 보려면을 입력 `Get-Help Certificate` 합니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-119">For example, to get help for the Certificate provider, type `Get-Help Certificate`.</span></span>

<span data-ttu-id="2da13-120">`help` `man` 한 번에 하나의 텍스트 화면을 표시 하는 또는를 입력할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-120">You can also type `help` or `man`, which displays one screen of text at a time.</span></span> <span data-ttu-id="2da13-121">와 `<cmdlet-name> -?` 동일 `Get-Help` 하지만 cmdlet에 대해서만 작동 하는 또는입니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-121">Or, `<cmdlet-name> -?`, that is identical to `Get-Help`, but only works for cmdlets.</span></span>

<span data-ttu-id="2da13-122">`Get-Help` 컴퓨터의 도움말 파일에서 표시 하는 도움말 콘텐츠를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-122">`Get-Help` gets the help content that it displays from help files on your computer.</span></span> <span data-ttu-id="2da13-123">도움말 파일이 없으면에는 `Get-Help` cmdlet에 대 한 기본 정보만 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-123">Without the help files, `Get-Help` displays only basic information about cmdlets.</span></span> <span data-ttu-id="2da13-124">일부 PowerShell 모듈에는 도움말 파일이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-124">Some PowerShell modules include help files.</span></span> <span data-ttu-id="2da13-125">PowerShell 3.0 부터는 Windows 운영 체제와 함께 제공 되는 모듈에 도움말 파일이 포함 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-125">Beginning in PowerShell 3.0, the modules that come with the Windows operating system don't include help files.</span></span> <span data-ttu-id="2da13-126">PowerShell 3.0의 모듈에 대 한 도움말 파일을 다운로드 하거나 업데이트 하려면 cmdlet을 사용 합니다 `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="2da13-126">To download or update the help files for a module in PowerShell 3.0, use the `Update-Help` cmdlet.</span></span>

<span data-ttu-id="2da13-127">Microsoft Docs에서 PowerShell 도움말 문서를 온라인으로 볼 수도 있습니다. 온라인 버전의 도움말 파일을 가져오려면와 같은 **online** 매개 변수를 사용 `Get-Help Get-Process -Online` 합니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-127">You can also view the PowerShell help documents online in the Microsoft Docs. To get the online version of a help file, use the **Online** parameter, such as: `Get-Help Get-Process -Online`.</span></span> <span data-ttu-id="2da13-128">모든 PowerShell 설명서를 읽으려면 Microsoft Docs [Powershell 설명서](/powershell)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2da13-128">To read all the PowerShell documentation, see the Microsoft Docs [PowerShell Documentation](/powershell).</span></span>

<span data-ttu-id="2da13-129">`Get-Help`다음에 도움말 아티클의 정확한 이름을 입력 하거나 도움말 문서에 고유한 단어를 입력 하는 경우 `Get-Help` 문서 내용이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-129">If you type `Get-Help` followed by the exact name of a help article, or by a word unique to a help article, `Get-Help` displays the article's content.</span></span> <span data-ttu-id="2da13-130">명령 별칭의 정확한 이름을 지정 하는 경우는 `Get-Help` 원래 명령에 대 한 도움말을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-130">If you specify the exact name of a command alias, `Get-Help` displays the help for the original command.</span></span> <span data-ttu-id="2da13-131">여러 도움말 문서 제목에 표시 되는 단어 또는 단어 패턴을 입력 하는 경우 `Get-Help` 일치 하는 타이틀의 목록이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-131">If you enter a word or word pattern that appears in several help article titles, `Get-Help` displays a list of the matching titles.</span></span> <span data-ttu-id="2da13-132">도움말 문서 제목에 표시 되지 않는 텍스트를 입력 하면에서 해당 `Get-Help` 텍스트를 포함 하는 문서 목록을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-132">If you enter any text that doesn't appear in any help article titles, `Get-Help` displays a list of articles that include that text in their contents.</span></span>

<span data-ttu-id="2da13-133">`Get-Help` 지원 되는 모든 언어 및 로캘에 대 한 도움말 문서를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-133">`Get-Help` can get help articles for all supported languages and locales.</span></span> <span data-ttu-id="2da13-134">`Get-Help` 는 먼저 Windows에 대해 설정 된 로캘, 부모 로캘 (예: pt의 경우 **pt** **-BR** )에서 도움말 파일을 찾은 다음 대체 (fallback) 로캘로 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-134">`Get-Help` first looks for help files in the locale set for Windows, then in the parent locale, such as **pt** for **pt-BR** , and then in a fallback locale.</span></span> <span data-ttu-id="2da13-135">PowerShell 3.0부터 `Get-Help` 대체 로캘에 대 한 도움말을 찾을 수 없는 경우는 오류 메시지를 반환 하거나 자동 생성 된 도움말을 표시 하기 전에 영어, **en-us** 에서 도움말 문서를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-135">Beginning in PowerShell 3.0, if `Get-Help` doesn't find help in the fallback locale, it looks for help articles in English, **en-US** , before it returns an error message or displaying autogenerated help.</span></span>

<span data-ttu-id="2da13-136">명령 구문 다이어그램에 표시 되는 기호에 대 한 자세한 내용은 `Get-Help` [about_Command_Syntax](./About/about_Command_Syntax.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2da13-136">For information about the symbols that `Get-Help` displays in the command syntax diagram, see [about_Command_Syntax](./About/about_Command_Syntax.md).</span></span>
<span data-ttu-id="2da13-137">**필수** 및 **위치** 와 같은 매개 변수 특성에 대 한 자세한 내용은 [about_Parameters](./About/about_Parameters.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2da13-137">For information about parameter attributes, such as **Required** and **Position** , see [about_Parameters](./About/about_Parameters.md).</span></span>

>[!NOTE]
> <span data-ttu-id="2da13-138">PowerShell 3.0 및 PowerShell 4.0에서는 `Get-Help` 모듈을 현재 세션으로 가져오지 않은 경우 모듈의 문서 **에 대 한 정보** 를 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-138">In PowerShell 3.0 and PowerShell 4.0, `Get-Help` can't find **About** articles in modules unless the module is imported into the current session.</span></span> <span data-ttu-id="2da13-139">이것은 알려진 문제입니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-139">This is a known issue.</span></span> <span data-ttu-id="2da13-140">모듈의 문서 **에 대 한 자세한** 내용을 보려면 cmdlet을 사용 `Import-Module` 하거나 모듈에 포함 된 cmdlet을 실행 하 여 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-140">To get **About** articles in a module, import the module, either by using the `Import-Module` cmdlet or by running a cmdlet that's included in the module.</span></span>

## <span data-ttu-id="2da13-141">예제</span><span class="sxs-lookup"><span data-stu-id="2da13-141">EXAMPLES</span></span>

### <span data-ttu-id="2da13-142">예제 1: cmdlet에 대 한 기본 도움말 정보 표시</span><span class="sxs-lookup"><span data-stu-id="2da13-142">Example 1: Display basic help information about a cmdlet</span></span>

<span data-ttu-id="2da13-143">이 예에서는 cmdlet에 대 한 기본 도움말 정보를 표시 `Format-Table` 합니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-143">These examples display basic help information about the `Format-Table` cmdlet.</span></span>

```powershell
Get-Help Format-Table
Get-Help -Name Format-Table
Format-Table -?
```

<span data-ttu-id="2da13-144">`Get-Help <cmdlet-name>` 는 cmdlet의 가장 간단 하 고 기본적인 구문입니다 `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="2da13-144">`Get-Help <cmdlet-name>` is the simplest and default syntax of `Get-Help` cmdlet.</span></span> <span data-ttu-id="2da13-145">**Name** 매개 변수를 생략할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-145">You can omit the **Name** parameter.</span></span>

<span data-ttu-id="2da13-146">구문은 `<cmdlet-name> -?` cmdlet에 대해서만 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-146">The syntax `<cmdlet-name> -?` works only for cmdlets.</span></span>

### <span data-ttu-id="2da13-147">예제 2: 한 번에 한 페이지씩 기본 정보 표시</span><span class="sxs-lookup"><span data-stu-id="2da13-147">Example 2: Display basic information one page at a time</span></span>

<span data-ttu-id="2da13-148">이 예에서는 cmdlet에 대 한 기본 도움말 정보 `Format-Table` 를 한 번에 한 페이지씩 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-148">These examples display basic help information about the `Format-Table` cmdlet one page at a time.</span></span>

```powershell
help Format-Table
man Format-Table
Get-Help Format-Table | Out-Host -Paging
```

<span data-ttu-id="2da13-149">`help` 는 `Get-Help` 내부적으로 cmdlet을 실행 하 고 결과를 한 번에 한 페이지씩 표시 하는 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-149">`help` is a function that runs `Get-Help` cmdlet internally and displays the result one page at a time.</span></span>

<span data-ttu-id="2da13-150">`man` 는 함수에 대 한 별칭입니다 `help` .</span><span class="sxs-lookup"><span data-stu-id="2da13-150">`man` is an alias for the `help` function.</span></span>

<span data-ttu-id="2da13-151">`Get-Help Format-Table` 개체를 파이프라인 아래로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-151">`Get-Help Format-Table` sends the object down the pipeline.</span></span> <span data-ttu-id="2da13-152">`Out-Host -Paging` 파이프라인에서 출력을 수신 하 고 한 번에 한 페이지씩 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-152">`Out-Host -Paging` receives the output from the pipeline and displays it one page at a time.</span></span> <span data-ttu-id="2da13-153">자세한 내용은 [Out-Host](Out-Host.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2da13-153">For more information, see [Out-Host](Out-Host.md).</span></span>

### <span data-ttu-id="2da13-154">예제 3: cmdlet에 대 한 추가 정보 표시</span><span class="sxs-lookup"><span data-stu-id="2da13-154">Example 3: Display more information for a cmdlet</span></span>

<span data-ttu-id="2da13-155">이 예에서는 cmdlet에 대 한 자세한 도움말 정보 `Format-Table` 를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-155">These examples display more detailed help information about the `Format-Table` cmdlet.</span></span>

```powershell
Get-Help Format-Table -Detailed
Get-Help Format-Table -Full
```

<span data-ttu-id="2da13-156">**Detailed** 매개 변수는 매개 변수 설명 및 예제를 포함 하는 도움말 문서의 자세히 보기를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-156">The **Detailed** parameter displays the help article's detailed view that includes parameter descriptions and examples.</span></span>

<span data-ttu-id="2da13-157">**Full** 매개 변수는 매개 변수 설명, 예제, 입력 및 출력 개체 형식, 추가 메모를 포함 하는 도움말 문서 전체 보기를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-157">The **Full** parameter displays the help article's full view that includes parameter descriptions, examples, input and output object types, and additional notes.</span></span>

<span data-ttu-id="2da13-158">**자세히** 및 **전체** 매개 변수는 컴퓨터에 도움말 파일이 설치 된 명령에만 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-158">The **Detailed** and **Full** parameters are effective only for the commands that have help files installed on the computer.</span></span> <span data-ttu-id="2da13-159">이 매개 변수는 개념 ( **about_** ) 도움말 문서에는 적용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-159">The parameters aren't effective for the conceptual ( **about_** ) help articles.</span></span>

### <span data-ttu-id="2da13-160">예제 4: 매개 변수를 사용 하 여 cmdlet의 선택 된 부분 표시</span><span class="sxs-lookup"><span data-stu-id="2da13-160">Example 4: Display selected parts of a cmdlet by using parameters</span></span>

<span data-ttu-id="2da13-161">이 예에서는 cmdlet 도움말의 선택 된 부분을 표시 `Format-Table` 합니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-161">These examples display selected portions of the `Format-Table` cmdlet help.</span></span>

```powershell
Get-Help Format-Table -Examples
Get-Help Format-Table -Parameter *
Get-Help Format-Table -Parameter GroupBy
```

<span data-ttu-id="2da13-162">**예제** 매개 변수는 도움말 파일의 **NAME** 및 **개요** 섹션과 모든 예제를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-162">The **Examples** parameter displays the help file's **NAME** and **SYNOPSIS** sections, and all the Examples.</span></span> <span data-ttu-id="2da13-163">예제 **매개 변수는 스위치** 매개 변수 이므로 예제 번호를 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-163">You can't specify an Example number because the **Examples** parameter is a switch parameter.</span></span>

<span data-ttu-id="2da13-164">**매개** 변수 매개 변수는 지정 된 매개 변수에 대 한 설명만 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-164">The **Parameter** parameter displays only the descriptions of the specified parameters.</span></span> <span data-ttu-id="2da13-165">별표 ( `*` ) 와일드 카드 문자만 지정 하면 모든 매개 변수에 대 한 설명이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-165">If you specify only the asterisk (`*`) wildcard character, it displays the descriptions of all parameters.</span></span>
<span data-ttu-id="2da13-166">**매개** 변수가 **GroupBy** 와 같은 매개 변수 이름을 지정 하는 경우 해당 매개 변수에 대 한 정보가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-166">When **Parameter** specifies a parameter name such as **GroupBy** , information about that parameter is shown.</span></span>

<span data-ttu-id="2da13-167">이러한 매개 변수는 개념 ( **about_** ) 도움말 문서에는 적용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-167">These parameters aren't effective for the conceptual ( **about_** ) help articles.</span></span>

### <span data-ttu-id="2da13-168">예 5: 온라인 버전의 도움말 표시</span><span class="sxs-lookup"><span data-stu-id="2da13-168">Example 5: Display online version of help</span></span>

<span data-ttu-id="2da13-169">이 예에서는 `Format-Table` 기본 웹 브라우저에서 cmdlet에 대 한 도움말 문서의 온라인 버전을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-169">This example displays the online version of the help article for the `Format-Table` cmdlet in your default web browser.</span></span>

```powershell
Get-Help Format-Table -Online
```

### <span data-ttu-id="2da13-170">예 6: 도움말 시스템에 대 한 도움말 표시</span><span class="sxs-lookup"><span data-stu-id="2da13-170">Example 6: Display help about the help system</span></span>

<span data-ttu-id="2da13-171">`Get-Help`매개 변수가 없는 cmdlet은 PowerShell 도움말 시스템에 대 한 정보를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-171">The `Get-Help` cmdlet without parameters displays information about the PowerShell help system.</span></span>

```powershell
Get-Help
```

### <span data-ttu-id="2da13-172">예 7: 사용 가능한 도움말 문서 표시</span><span class="sxs-lookup"><span data-stu-id="2da13-172">Example 7: Display available help articles</span></span>

<span data-ttu-id="2da13-173">이 예제에서는 컴퓨터에서 사용할 수 있는 모든 도움말 문서의 목록을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-173">This example displays a list of all help articles available on your computer.</span></span>

```powershell
Get-Help *
```

### <span data-ttu-id="2da13-174">예 8: 개념 문서 목록 표시</span><span class="sxs-lookup"><span data-stu-id="2da13-174">Example 8: Display a list of conceptual articles</span></span>

<span data-ttu-id="2da13-175">이 예제에서는 PowerShell 도움말에 포함 된 개념 문서의 목록을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-175">This example displays a list of the conceptual articles included in PowerShell help.</span></span> <span data-ttu-id="2da13-176">이러한 모든 문서는 **about_** 문자로 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-176">All these articles begin with the characters **about_**.</span></span> <span data-ttu-id="2da13-177">특정 도움말 파일을 표시 하려면를 입력 `Get-Help \<about_article-name\>` 합니다 (예:) `Get-Help about_Signing` .</span><span class="sxs-lookup"><span data-stu-id="2da13-177">To display a particular help file, type `Get-Help \<about_article-name\>`, for example, `Get-Help about_Signing`.</span></span>

<span data-ttu-id="2da13-178">컴퓨터에 도움말 파일이 설치 된 개념 문서만 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-178">Only the conceptual articles that have help files installed on your computer are displayed.</span></span> <span data-ttu-id="2da13-179">PowerShell 3.0에서 도움말 파일을 다운로드 하 고 설치 하는 방법에 대 한 자세한 내용은 [update-help](Update-Help.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2da13-179">For information about downloading and installing help files in PowerShell 3.0, see [Update-Help](Update-Help.md).</span></span>

```powershell
Get-Help about_*
```

### <span data-ttu-id="2da13-180">예 9: cmdlet 도움말에서 단어 검색</span><span class="sxs-lookup"><span data-stu-id="2da13-180">Example 9: Search for a word in cmdlet help</span></span>

<span data-ttu-id="2da13-181">이 예제에서는 cmdlet 도움말 문서에서 단어를 검색 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-181">This example shows how to search for a word in a cmdlet help article.</span></span>

```powershell
Get-Help Add-Member -Full | Out-String -Stream | Select-String -Pattern Clixml
```

```Output
the Export-Clixml cmdlet to save the instance of the object, including the additional members...
can use the Import-Clixml cmdlet to re-create the instance of the object from the information...
Export-Clixml
Import-Clixml
```

<span data-ttu-id="2da13-182">`Get-Help` 는 **전체** 매개 변수를 사용 하 여에 대 한 도움말 정보를 가져옵니다 `Add-Member` .</span><span class="sxs-lookup"><span data-stu-id="2da13-182">`Get-Help` uses the **Full** parameter to get help information for `Add-Member`.</span></span> <span data-ttu-id="2da13-183">**MamlCommandHelpInfo** 개체가 파이프라인으로 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-183">The **MamlCommandHelpInfo** object is sent down the pipeline.</span></span> <span data-ttu-id="2da13-184">`Out-String`**Stream** 매개 변수를 사용 하 여 개체를 문자열로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-184">`Out-String` uses the **Stream** parameter to convert the object into a string.</span></span> <span data-ttu-id="2da13-185">`Select-String`**Pattern** 매개 변수를 사용 하 여 **export-clixml** 에 대 한 문자열을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-185">`Select-String` uses the **Pattern** parameter to search the string for **Clixml**.</span></span>

### <span data-ttu-id="2da13-186">예 10: 단어를 포함 하는 문서 목록 표시</span><span class="sxs-lookup"><span data-stu-id="2da13-186">Example 10: Display a list of articles that include a word</span></span>

<span data-ttu-id="2da13-187">이 예에서는 **remoting** 이라는 단어를 포함 하는 문서의 목록을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-187">This example displays a list of articles that include the word **remoting**.</span></span>

<span data-ttu-id="2da13-188">문서 제목에 나타나지 않는 단어를 입력 하면에 `Get-Help` 해당 단어가 포함 된 문서 목록이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-188">When you enter a word that doesn't appear in any article title, `Get-Help` displays a list of articles that include that word.</span></span>

```powershell
Get-Help -Name remoting
```

```Output
Name                              Category  Module                    Synopsis
----                              --------  ------                    --------
Install-PowerShellRemoting.ps1    External                            Install-PowerShellRemoting.ps1
Disable-PSRemoting                Cmdlet    Microsoft.PowerShell.Core Prevents remote users...
Enable-PSRemoting                 Cmdlet    Microsoft.PowerShell.Core Configures the computer...
```

### <span data-ttu-id="2da13-189">예 11: 공급자별 도움말 표시</span><span class="sxs-lookup"><span data-stu-id="2da13-189">Example 11: Display provider-specific help</span></span>

<span data-ttu-id="2da13-190">이 예제에서는에 대 한 공급자별 도움말을 가져오는 두 가지 방법을 보여 줍니다 `Get-Item` .</span><span class="sxs-lookup"><span data-stu-id="2da13-190">This example shows two ways of getting the provider-specific help for `Get-Item`.</span></span> <span data-ttu-id="2da13-191">이러한 명령은 `Get-Item` PowerShell SQL Server 공급자의 **DataCollection** 노드에서 cmdlet을 사용 하는 방법을 설명 하는 도움말을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-191">These commands get help that explains how to use the `Get-Item` cmdlet in the PowerShell SQL Server provider's **DataCollection** node.</span></span>

<span data-ttu-id="2da13-192">첫 번째 예에서는 `Get-Help` **path** 매개 변수를 사용 하 여 SQL Server 공급자의 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-192">The first example uses the `Get-Help` **Path** parameter to specify the SQL Server provider's path.</span></span>
<span data-ttu-id="2da13-193">공급자의 경로가 지정 되었으므로 모든 경로 위치에서 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-193">Because the provider's path is specified, you can run the command from any path location.</span></span>

<span data-ttu-id="2da13-194">두 번째 예제에서는를 사용 하 여 `Set-Location` SQL Server 공급자의 경로로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-194">The second example uses `Set-Location` to navigate to the SQL Server provider's path.</span></span> <span data-ttu-id="2da13-195">해당 위치에서 **경로** 매개 변수는 `Get-Help` 공급자 관련 도움말을 가져오는 데 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-195">From that location, the **Path** parameter isn't needed for `Get-Help` to get the provider-specific help.</span></span>

```powershell
Get-Help Get-Item -Path SQLSERVER:\DataCollection
```

```Output
NAME

    Get-Item

SYNOPSIS

    Gets a collection of Server objects for the local computer and any computers

    to which you have made a SQL Server PowerShell connection.
    ...
```

```powershell
Set-Location SQLSERVER:\DataCollection
SQLSERVER:\DataCollection> Get-Help Get-Item
```

```Output
NAME

    Get-Item

SYNOPSIS

    Gets a collection of Server objects for the local computer and any computers

    to which you have made a SQL Server PowerShell connection.
    ...
```

### <span data-ttu-id="2da13-196">예 12: 스크립트에 대 한 도움말 표시</span><span class="sxs-lookup"><span data-stu-id="2da13-196">Example 12: Display help for a script</span></span>

<span data-ttu-id="2da13-197">이 예제에서는에 대 한 도움말을 가져옵니다 `MyScript.ps1 script` .</span><span class="sxs-lookup"><span data-stu-id="2da13-197">This example gets help for the `MyScript.ps1 script`.</span></span> <span data-ttu-id="2da13-198">함수 및 스크립트에 대 한 도움말을 작성 하는 방법에 대 한 자세한 내용은 [about_Comment_Based_Help](./About/about_Comment_Based_Help.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2da13-198">For information about how to write help for your functions and scripts, see [about_Comment_Based_Help](./About/about_Comment_Based_Help.md).</span></span>

```powershell
Get-Help -Name C:\PS-Test\MyScript.ps1
```

## <span data-ttu-id="2da13-199">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2da13-199">PARAMETERS</span></span>

### <span data-ttu-id="2da13-200">-범주</span><span class="sxs-lookup"><span data-stu-id="2da13-200">-Category</span></span>

<span data-ttu-id="2da13-201">지정된 범주 및 해당 별칭의 항목에 대한 도움말만 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-201">Displays help only for items in the specified category and their aliases.</span></span> <span data-ttu-id="2da13-202">개념 문서는 **HelpFile** 범주에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-202">Conceptual articles are in the **HelpFile** category.</span></span>

<span data-ttu-id="2da13-203">이 매개 변수에 허용 되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-203">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="2da13-204">Alias</span><span class="sxs-lookup"><span data-stu-id="2da13-204">Alias</span></span>
- <span data-ttu-id="2da13-205">cmdlet</span><span class="sxs-lookup"><span data-stu-id="2da13-205">Cmdlet</span></span>
- <span data-ttu-id="2da13-206">공급자</span><span class="sxs-lookup"><span data-stu-id="2da13-206">Provider</span></span>
- <span data-ttu-id="2da13-207">일반</span><span class="sxs-lookup"><span data-stu-id="2da13-207">General</span></span>
- <span data-ttu-id="2da13-208">FAQ</span><span class="sxs-lookup"><span data-stu-id="2da13-208">FAQ</span></span>
- <span data-ttu-id="2da13-209">용어</span><span class="sxs-lookup"><span data-stu-id="2da13-209">Glossary</span></span>
- <span data-ttu-id="2da13-210">HelpFile</span><span class="sxs-lookup"><span data-stu-id="2da13-210">HelpFile</span></span>
- <span data-ttu-id="2da13-211">ScriptCommand</span><span class="sxs-lookup"><span data-stu-id="2da13-211">ScriptCommand</span></span>
- <span data-ttu-id="2da13-212">함수</span><span class="sxs-lookup"><span data-stu-id="2da13-212">Function</span></span>
- <span data-ttu-id="2da13-213">Assert</span><span class="sxs-lookup"><span data-stu-id="2da13-213">Filter</span></span>
- <span data-ttu-id="2da13-214">ExternalScript</span><span class="sxs-lookup"><span data-stu-id="2da13-214">ExternalScript</span></span>
- <span data-ttu-id="2da13-215">모두</span><span class="sxs-lookup"><span data-stu-id="2da13-215">All</span></span>
- <span data-ttu-id="2da13-216">DefaultHelp</span><span class="sxs-lookup"><span data-stu-id="2da13-216">DefaultHelp</span></span>
- <span data-ttu-id="2da13-217">워크플로</span><span class="sxs-lookup"><span data-stu-id="2da13-217">Workflow</span></span>
- <span data-ttu-id="2da13-218">DscResource</span><span class="sxs-lookup"><span data-stu-id="2da13-218">DscResource</span></span>
- <span data-ttu-id="2da13-219">클래스</span><span class="sxs-lookup"><span data-stu-id="2da13-219">Class</span></span>
- <span data-ttu-id="2da13-220">Configuration</span><span class="sxs-lookup"><span data-stu-id="2da13-220">Configuration</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:
Accepted values: Alias, Cmdlet, Provider, General, FAQ, Glossary, HelpFile, ScriptCommand, Function, Filter, ExternalScript, All, DefaultHelp, Workflow, DscResource, Class, Configuration

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2da13-221">-구성 요소</span><span class="sxs-lookup"><span data-stu-id="2da13-221">-Component</span></span>

<span data-ttu-id="2da13-222">지정 된 구성 요소 값 (예: **Exchange** )을 사용 하 여 명령을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-222">Displays commands with the specified component value, such as **Exchange**.</span></span> <span data-ttu-id="2da13-223">구성 요소 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-223">Enter a component name.</span></span>
<span data-ttu-id="2da13-224">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-224">Wildcard characters are permitted.</span></span> <span data-ttu-id="2da13-225">이 매개 변수는 개념 ( **About_** ) 도움말의 표시에 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-225">This parameter has no effect on displays of conceptual ( **About_** ) help.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="2da13-226">-Detailed</span><span class="sxs-lookup"><span data-stu-id="2da13-226">-Detailed</span></span>

<span data-ttu-id="2da13-227">매개 변수 설명과 예를 기본 도움말 표시에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-227">Adds parameter descriptions and examples to the basic help display.</span></span> <span data-ttu-id="2da13-228">이 매개 변수는 도움말 파일이 컴퓨터에 설치 된 경우에만 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-228">This parameter is effective only when the help files are installed on the computer.</span></span> <span data-ttu-id="2da13-229">개념 ( **About_** ) 도움말의 표시에는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-229">It has no effect on displays of conceptual ( **About_** ) help.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DetailedView
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2da13-230">-Examples</span><span class="sxs-lookup"><span data-stu-id="2da13-230">-Examples</span></span>

<span data-ttu-id="2da13-231">이름, 개요 및 예만 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-231">Displays only the name, synopsis, and examples.</span></span> <span data-ttu-id="2da13-232">예제만 표시 하려면을 입력 `(Get-Help \<cmdlet-name\>).Examples` 합니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-232">To display only the examples, type `(Get-Help \<cmdlet-name\>).Examples`.</span></span>

<span data-ttu-id="2da13-233">이 매개 변수는 도움말 파일이 컴퓨터에 설치 된 경우에만 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-233">This parameter is effective only when the help files are installed on the computer.</span></span> <span data-ttu-id="2da13-234">개념 ( **About_** ) 도움말의 표시에는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-234">It has no effect on displays of conceptual ( **About_** ) help.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Examples
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2da13-235">-Full</span><span class="sxs-lookup"><span data-stu-id="2da13-235">-Full</span></span>

<span data-ttu-id="2da13-236">Cmdlet에 대 한 전체 도움말 문서를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-236">Displays the entire help article for a cmdlet.</span></span> <span data-ttu-id="2da13-237">**전체** 에는 매개 변수 설명 및 특성, 예제, 입력 및 출력 개체 형식, 추가 참고 사항이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-237">**Full** includes parameter descriptions and attributes, examples, input and output object types, and additional notes.</span></span>

<span data-ttu-id="2da13-238">이 매개 변수는 도움말 파일이 컴퓨터에 설치 된 경우에만 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-238">This parameter is effective only when the help files are installed on the computer.</span></span> <span data-ttu-id="2da13-239">개념 ( **About_** ) 도움말의 표시에는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-239">It has no effect on displays of conceptual ( **About_** ) help.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AllUsersView
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2da13-240">-기능</span><span class="sxs-lookup"><span data-stu-id="2da13-240">-Functionality</span></span>

<span data-ttu-id="2da13-241">지정된 기능이 있는 항목에 대한 도움말을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-241">Displays help for items with the specified functionality.</span></span> <span data-ttu-id="2da13-242">기능을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="2da13-242">Enter the functionality.</span></span> <span data-ttu-id="2da13-243">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-243">Wildcard characters are permitted.</span></span> <span data-ttu-id="2da13-244">이 매개 변수는 개념 ( **About_** ) 도움말의 표시에 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-244">This parameter has no effect on displays of conceptual ( **About_** ) help.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="2da13-245">-Name</span><span class="sxs-lookup"><span data-stu-id="2da13-245">-Name</span></span>

<span data-ttu-id="2da13-246">지정된 명령 또는 개념에 대한 도움말을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-246">Gets help about the specified command or concept.</span></span> <span data-ttu-id="2da13-247">Cmdlet, 함수, 공급자, 스크립트 또는 워크플로의 이름을 입력 합니다 (예:). 예를 들어와 같은 `Get-Member` 개념 문서 이름 `about_Objects` 또는 별칭을 입력 `ls` 합니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-247">Enter the name of a cmdlet, function, provider, script, or workflow, such as `Get-Member`, a conceptual article name, such as `about_Objects`, or an alias, such as `ls`.</span></span> <span data-ttu-id="2da13-248">Cmdlet 및 공급자 이름에 와일드 카드 문자를 사용할 수 있지만 와일드 카드 문자를 사용 하 여 함수 도움말 및 스크립트 도움말 문서의 이름을 찾을 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-248">Wildcard characters are permitted in cmdlet and provider names, but you can't use wildcard characters to find the names of function help and script help articles.</span></span>

<span data-ttu-id="2da13-249">환경 변수에 나열 된 경로에 없는 스크립트에 대 한 도움말을 보려면 `$env:Path` 스크립트의 경로와 파일 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-249">To get help for a script that isn't located in a path that's listed in the `$env:Path` environment variable, type the script's path and file name.</span></span>

<span data-ttu-id="2da13-250">도움말 아티클의 정확한 이름을 입력 하면에서 `Get-Help` 문서 내용을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-250">If you enter the exact name of a help article, `Get-Help` displays the article contents.</span></span>

<span data-ttu-id="2da13-251">여러 도움말 문서 제목에 표시 되는 단어 또는 단어 패턴을 입력 하는 경우 `Get-Help` 일치 하는 타이틀의 목록이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-251">If you enter a word or word pattern that appears in several help article titles, `Get-Help` displays a list of the matching titles.</span></span>

<span data-ttu-id="2da13-252">도움말 문서 제목과 일치 하지 않는 텍스트를 입력 하면에서 해당 `Get-Help` 텍스트를 포함 하는 문서 목록을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-252">If you enter any text that doesn't match any help article titles, `Get-Help` displays a list of articles that include that text in their contents.</span></span>

<span data-ttu-id="2da13-253">과 같은 개념 문서의 이름은 영어가 `about_Objects` 아닌 PowerShell 버전 에서도 영어로 입력 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-253">The names of conceptual articles, such as `about_Objects`, must be entered in English, even in non-English versions of PowerShell.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="2da13-254">-Online</span><span class="sxs-lookup"><span data-stu-id="2da13-254">-Online</span></span>

<span data-ttu-id="2da13-255">온라인 버전의 도움말 문서를 기본 브라우저에 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-255">Displays the online version of a help article in the default browser.</span></span> <span data-ttu-id="2da13-256">이 매개 변수는 cmdlet, 함수, 워크플로 및 스크립트 도움말 문서에 대해서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-256">This parameter is valid only for cmdlet, function, workflow, and script help articles.</span></span> <span data-ttu-id="2da13-257">**Online** 매개 변수는 `Get-Help` 원격 세션에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-257">You can't use the **Online** parameter with `Get-Help` in a remote session.</span></span>

<span data-ttu-id="2da13-258">작성 하는 도움말 문서에서이 기능을 지 원하는 방법에 대 한 자세한 내용은 [about_Comment_Based_Help](./About/about_Comment_Based_Help.md)및 [온라인 도움말 지원](/powershell/scripting/developer/module/supporting-online-help)및 [PowerShell Cmdlet에 대 한 도움말 작성](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2da13-258">For information about supporting this feature in help articles that you write, see [about_Comment_Based_Help](./About/about_Comment_Based_Help.md), and [Supporting Online Help](/powershell/scripting/developer/module/supporting-online-help), and [Writing Help for PowerShell Cmdlets](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Online
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2da13-259"> 매개 변수</span><span class="sxs-lookup"><span data-stu-id="2da13-259">-Parameter</span></span>

<span data-ttu-id="2da13-260">지정된 매개 변수에 대한 자세한 설명만 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-260">Displays only the detailed descriptions of the specified parameters.</span></span> <span data-ttu-id="2da13-261">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-261">Wildcards are permitted.</span></span> <span data-ttu-id="2da13-262">이 매개 변수는 개념 ( **About_** ) 도움말의 표시에 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-262">This parameter has no effect on displays of conceptual ( **About_** ) help.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Parameters
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="2da13-263">-Path</span><span class="sxs-lookup"><span data-stu-id="2da13-263">-Path</span></span>

<span data-ttu-id="2da13-264">지정된 공급자 경로에서 cmdlet이 작동하는 방식을 설명하는 도움말을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-264">Gets help that explains how the cmdlet works in the specified provider path.</span></span> <span data-ttu-id="2da13-265">PowerShell 공급자 경로를 입력 하십시오.</span><span class="sxs-lookup"><span data-stu-id="2da13-265">Enter a PowerShell provider path.</span></span>

<span data-ttu-id="2da13-266">이 매개 변수는 지정 된 PowerShell 공급자 경로에서 cmdlet이 작동 하는 방식을 설명 하는 cmdlet 도움말 아티클의 사용자 지정 된 버전을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-266">This parameter gets a customized version of a cmdlet help article that explains how the cmdlet works in the specified PowerShell provider path.</span></span> <span data-ttu-id="2da13-267">이 매개 변수는 공급자 cmdlet에 대 한 도움말과 공급자가 해당 도움말 파일에 공급자 cmdlet 도움말 아티클의 사용자 지정 버전을 포함 하는 경우에만 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-267">This parameter is effective only for help about a provider cmdlet and only when the provider includes a custom version of the provider cmdlet help article in its help file.</span></span> <span data-ttu-id="2da13-268">이 매개 변수를 사용하려면 공급자를 포함하는 모듈에 대한 도움말 파일을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-268">To use this parameter, install the help file for the module that includes the provider.</span></span>

<span data-ttu-id="2da13-269">공급자 경로에 대 한 사용자 지정 cmdlet 도움말을 보려면 공급자 경로 위치로 이동 하 여 `Get-Help` 명령을 입력 하거나 경로 위치에서의 **path** 매개 변수를 사용 `Get-Help` 하 여 공급자 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-269">To see the custom cmdlet help for a provider path, go to the provider path location and enter a `Get-Help` command or, from any path location, use the **Path** parameter of `Get-Help` to specify the provider path.</span></span> <span data-ttu-id="2da13-270">도움말 문서의 공급자 도움말 섹션에서 온라인으로 사용자 지정 cmdlet 도움말을 찾을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-270">You can also find custom cmdlet help online in the provider help section of the help articles.</span></span>

<span data-ttu-id="2da13-271">PowerShell 공급자에 대 한 자세한 내용은 [about_Providers](./About/about_Providers.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2da13-271">For more information about PowerShell providers, see [about_Providers](./About/about_Providers.md).</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="2da13-272">-Role</span><span class="sxs-lookup"><span data-stu-id="2da13-272">-Role</span></span>

<span data-ttu-id="2da13-273">지정된 사용자 역할에 맞게 사용자 지정된 도움말을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-273">Displays help customized for the specified user role.</span></span> <span data-ttu-id="2da13-274">역할을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="2da13-274">Enter a role.</span></span> <span data-ttu-id="2da13-275">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-275">Wildcard characters are permitted.</span></span>

<span data-ttu-id="2da13-276">사용자가 조직에서 수행하는 역할을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-276">Enter the role that the user plays in an organization.</span></span> <span data-ttu-id="2da13-277">일부 cmdlet은 이 매개 변수 값을 기반으로 해당 도움말 파일에서 서로 다른 텍스트를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-277">Some cmdlets display different text in their help files based on the value of this parameter.</span></span> <span data-ttu-id="2da13-278">이 매개 변수는 핵심 cmdlet의 도움말에는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-278">This parameter has no effect on help for the core cmdlets.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="2da13-279">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2da13-279">CommonParameters</span></span>

<span data-ttu-id="2da13-280">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="2da13-280">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2da13-281">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2da13-281">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2da13-282">입력</span><span class="sxs-lookup"><span data-stu-id="2da13-282">INPUTS</span></span>

### <span data-ttu-id="2da13-283">없음</span><span class="sxs-lookup"><span data-stu-id="2da13-283">None</span></span>

<span data-ttu-id="2da13-284">파이프라인에서로 개체를 보낼 수 없습니다 `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="2da13-284">You can't send objects down the pipeline to `Get-Help`.</span></span>

## <span data-ttu-id="2da13-285">출력</span><span class="sxs-lookup"><span data-stu-id="2da13-285">OUTPUTS</span></span>

### <span data-ttu-id="2da13-286">ExtendedCmdletHelpInfo</span><span class="sxs-lookup"><span data-stu-id="2da13-286">ExtendedCmdletHelpInfo</span></span>

<span data-ttu-id="2da13-287">`Get-Help`도움말 파일이 없는 명령에서를 실행 하는 경우는 자동 `Get-Help` 생성 된 도움말을 나타내는 **ExtendedCmdletHelpInfo** 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-287">If you run `Get-Help` on a command that doesn't have a help file, `Get-Help` returns an **ExtendedCmdletHelpInfo** object that represents autogenerated help.</span></span>

### <span data-ttu-id="2da13-288">System.String</span><span class="sxs-lookup"><span data-stu-id="2da13-288">System.String</span></span>

<span data-ttu-id="2da13-289">개념 도움말 문서를 가져오는 경우이를 `Get-Help` 문자열로 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-289">If you get a conceptual help article, `Get-Help` returns it as a string.</span></span>

### <span data-ttu-id="2da13-290">MamlCommandHelpInfo</span><span class="sxs-lookup"><span data-stu-id="2da13-290">MamlCommandHelpInfo</span></span>

<span data-ttu-id="2da13-291">도움말 파일이 있는 명령이 표시 되 면는 `Get-Help` **MamlCommandHelpInfo** 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-291">If you get a command that has a help file, `Get-Help` returns a **MamlCommandHelpInfo** object.</span></span>

## <span data-ttu-id="2da13-292">참고</span><span class="sxs-lookup"><span data-stu-id="2da13-292">NOTES</span></span>

<span data-ttu-id="2da13-293">PowerShell 3.0에는 도움말 파일이 포함 되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-293">PowerShell 3.0 doesn't include help files.</span></span> <span data-ttu-id="2da13-294">에서 읽는 도움말 파일을 다운로드 하 여 설치 하려면 `Get-Help` cmdlet을 사용 합니다 `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="2da13-294">To download and install the help files that `Get-Help` reads, use the `Update-Help` cmdlet.</span></span> <span data-ttu-id="2da13-295">Cmdlet을 사용 하 여 `Update-Help` PowerShell과 함께 제공 되는 핵심 명령과 설치 하는 모듈에 대 한 도움말 파일을 다운로드 하 고 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-295">You can use the `Update-Help` cmdlet to download and install help files for the core commands that come with PowerShell and for any modules that you install.</span></span> <span data-ttu-id="2da13-296">또한 이 cmdlet으로 도움말 파일을 업데이트하여 컴퓨터의 도움말이 오래되지 않도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-296">You can also use it to update the help files so that the help on your computer is never outdated.</span></span>

<span data-ttu-id="2da13-297">[Windows Powershell 시작](/powershell/scripting/getting-started/getting-started-with-windows-powershell)부터 powershell 온라인에서 제공 되는 명령에 대 한 도움말 문서를 읽을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-297">You can also read the help articles about the commands that come with PowerShell online starting at [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

<span data-ttu-id="2da13-298">`Get-Help` Windows 운영 체제에 대해 설정 된 로캘 또는 해당 로캘의 대체 언어로 도움말을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-298">`Get-Help` displays help in the locale set for the Windows operating system or in the fallback language for that locale.</span></span> <span data-ttu-id="2da13-299">기본 또는 대체 로캘에 대 한 도움말 파일이 없는 경우는 `Get-Help` 컴퓨터에 도움말 파일이 없는 것 처럼 동작 합니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-299">If you don't have help files for the primary or fallback locale, `Get-Help` behaves as if there are no help files on the computer.</span></span> <span data-ttu-id="2da13-300">다른 로캘에 대 한 도움말을 보려면 제어판의 **국가** 및 **언어** 를 사용 하 여 설정을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-300">To get help for a different locale, use **Region** and **Language** in Control Panel to change the settings.</span></span> <span data-ttu-id="2da13-301">Windows 10, **설정** , **시간 & 언어** 입니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-301">On Windows 10, **Settings** , **Time & Language**.</span></span>

<span data-ttu-id="2da13-302">도움말의 전체 보기에는 매개 변수에 대 한 정보 테이블이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-302">The full view of help includes a table of information about the parameters.</span></span> <span data-ttu-id="2da13-303">이 테이블에는 다음 필드가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-303">The table includes the following fields:</span></span>

- <span data-ttu-id="2da13-304">**필수**.</span><span class="sxs-lookup"><span data-stu-id="2da13-304">**Required**.</span></span> <span data-ttu-id="2da13-305">매개 변수가 필수(true)인지 선택 사항(false)인지를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-305">Indicates whether the parameter is required (true) or optional (false).</span></span>

- <span data-ttu-id="2da13-306">**위치**.</span><span class="sxs-lookup"><span data-stu-id="2da13-306">**Position**.</span></span> <span data-ttu-id="2da13-307">매개 변수의 이름이 지정 되었는지 아니면 위치 (숫자) 인지를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-307">Indicates whether the parameter is named or positional (numeric).</span></span> <span data-ttu-id="2da13-308">위치 매개 변수는 명령에서 지정된 위치에 표시해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-308">Positional parameters must appear in a specified place in the command.</span></span>

- <span data-ttu-id="2da13-309">**명명** 됨은 매개 변수 이름이 필요 하지만 매개 변수가 명령의 아무 곳에 나 나타날 수 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-309">**Named** indicates that the parameter name is required, but that the parameter can appear anywhere in the command.</span></span>

- <span data-ttu-id="2da13-310">**Numeric** 은 매개 변수 이름이 선택 사항 이지만 이름을 생략 하면 숫자에 지정 된 자리에 매개 변수가 있어야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-310">**Numeric** indicates that the parameter name is optional, but when the name is omitted, the parameter must be in the place specified by the number.</span></span> <span data-ttu-id="2da13-311">예를 들어는 `2` 매개 변수 이름이 생략 된 경우 매개 변수가 명령에서 두 번째 또는 유일한 명명 되지 않은 매개 변수 여야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-311">For example, `2` indicates that when the parameter name is omitted, the parameter must be the second or only unnamed parameter in the command.</span></span> <span data-ttu-id="2da13-312">매개 변수 이름을 사용할 경우에는 해당 매개 변수를 명령에서 어느 위치에든 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-312">When the parameter name is used, the parameter can appear anywhere in the command.</span></span>

- <span data-ttu-id="2da13-313">**기본값** 입니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-313">**Default value**.</span></span> <span data-ttu-id="2da13-314">명령에 매개 변수를 포함 하지 않는 경우 PowerShell에서 사용 하는 매개 변수 값 또는 기본 동작입니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-314">The parameter value or default behavior that PowerShell uses if you don't include the parameter in the command.</span></span>

- <span data-ttu-id="2da13-315">파이프라인 입력을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-315">Accepts pipeline input.</span></span> <span data-ttu-id="2da13-316">파이프라인을 통해 매개 변수에 개체를 보낼 수 있는지 (true) 또는 불가능 (false) 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-316">Indicates whether you can (true) or can't (false) send objects to the parameter through a pipeline.</span></span> <span data-ttu-id="2da13-317">**속성 이름으로** 파이프라인 개체에 매개 변수 이름과 이름이 같은 속성이 있어야 함을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-317">**By Property Name** means that the pipelined object must have a property that has the same name as the parameter name.</span></span>

- <span data-ttu-id="2da13-318">**와일드 카드 문자를 허용** 합니다.</span><span class="sxs-lookup"><span data-stu-id="2da13-318">**Accepts wildcard characters**.</span></span> <span data-ttu-id="2da13-319">매개 변수 값에 별표 ( `*` ) 또는 물음표 ()와 같은 와일드 카드 문자를 포함할 수 있는지 여부를 나타냅니다 `?` .</span><span class="sxs-lookup"><span data-stu-id="2da13-319">Indicates whether the value of a parameter can include wildcard characters, such as an asterisk (`*`) or question mark (`?`).</span></span>

## <span data-ttu-id="2da13-320">관련 링크</span><span class="sxs-lookup"><span data-stu-id="2da13-320">RELATED LINKS</span></span>

[<span data-ttu-id="2da13-321">about_Command_Syntax</span><span class="sxs-lookup"><span data-stu-id="2da13-321">about_Command_Syntax</span></span>](About/about_Command_Syntax.md)

[<span data-ttu-id="2da13-322">about_Comment_Based_Help</span><span class="sxs-lookup"><span data-stu-id="2da13-322">about_Comment_Based_Help</span></span>](./About/about_Comment_Based_Help.md)

[<span data-ttu-id="2da13-323">Get-Command</span><span class="sxs-lookup"><span data-stu-id="2da13-323">Get-Command</span></span>](Get-Command.md)

[<span data-ttu-id="2da13-324">업데이트 가능한 도움말 지원</span><span class="sxs-lookup"><span data-stu-id="2da13-324">Supporting Updatable Help</span></span>](/powershell/scripting/developer/module/supporting-updatable-help)

[<span data-ttu-id="2da13-325">Update-Help</span><span class="sxs-lookup"><span data-stu-id="2da13-325">Update-Help</span></span>](Update-Help.md)

[<span data-ttu-id="2da13-326">설명 기반 도움말 항목 작성</span><span class="sxs-lookup"><span data-stu-id="2da13-326">Writing Comment-Based Help Topics</span></span>](/powershell/scripting/developer/help/writing-comment-based-help-topics)

[<span data-ttu-id="2da13-327">PowerShell cmdlet에 대한 도움말 작성</span><span class="sxs-lookup"><span data-stu-id="2da13-327">Writing Help for PowerShell Cmdlets</span></span>](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets)
