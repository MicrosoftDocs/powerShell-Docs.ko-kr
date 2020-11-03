---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/select-string?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Select-String
ms.openlocfilehash: 95601a4f5f42700c4de7d6ad721ee898b22bab84
ms.sourcegitcommit: 9a8bb1b459b5939c95e1f6d9499fcb13d01a58c4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/25/2020
ms.locfileid: "93219641"
---
# <span data-ttu-id="a8007-103">Select-String</span><span class="sxs-lookup"><span data-stu-id="a8007-103">Select-String</span></span>

## <span data-ttu-id="a8007-104">개요</span><span class="sxs-lookup"><span data-stu-id="a8007-104">SYNOPSIS</span></span>
<span data-ttu-id="a8007-105">문자열 및 파일에서 텍스트를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-105">Finds text in strings and files.</span></span>

## <span data-ttu-id="a8007-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a8007-106">SYNTAX</span></span>

### <span data-ttu-id="a8007-107">File (기본값)</span><span class="sxs-lookup"><span data-stu-id="a8007-107">File (Default)</span></span>

```
Select-String [-Pattern] <String[]> [-Path] <String[]> [-SimpleMatch] [-CaseSensitive] [-Quiet]
 [-List] [-Include <String[]>] [-Exclude <String[]>] [-NotMatch] [-AllMatches] [-Encoding <String>]
 [-Context <Int32[]>] [<CommonParameters>]
```

### <span data-ttu-id="a8007-108">Object</span><span class="sxs-lookup"><span data-stu-id="a8007-108">Object</span></span>

```
Select-String -InputObject <PSObject> [-Pattern] <String[]> [-SimpleMatch] [-CaseSensitive] [-Quiet]
 [-List] [-Include <String[]>] [-Exclude <String[]>] [-NotMatch] [-AllMatches] [-Encoding <String>]
 [-Context <Int32[]>] [<CommonParameters>]
```

### <span data-ttu-id="a8007-109">LiteralFile</span><span class="sxs-lookup"><span data-stu-id="a8007-109">LiteralFile</span></span>

```
Select-String [-Pattern] <String[]> -LiteralPath <String[]> [-SimpleMatch] [-CaseSensitive] [-Quiet]
 [-List] [-Include <String[]>] [-Exclude <String[]>] [-NotMatch] [-AllMatches] [-Encoding <String>]
 [-Context <Int32[]>] [<CommonParameters>]
```

## <span data-ttu-id="a8007-110">설명</span><span class="sxs-lookup"><span data-stu-id="a8007-110">DESCRIPTION</span></span>

<span data-ttu-id="a8007-111">`Select-String`Cmdlet은 입력 문자열 및 파일에서 텍스트 및 텍스트 패턴을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-111">The `Select-String` cmdlet searches for text and text patterns in input strings and files.</span></span> <span data-ttu-id="a8007-112">`Select-String`UNIX의 경우 또는 Windows **grep** 에서 **findstr.exe** 와 비슷하게를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-112">You can use `Select-String` similar to **grep** in UNIX or **findstr.exe** in Windows.</span></span>

<span data-ttu-id="a8007-113">`Select-String` 는 텍스트 줄을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-113">`Select-String` is based on lines of text.</span></span> <span data-ttu-id="a8007-114">기본적으로 `Select-String` 는 각 줄에서 첫 번째 일치 항목을 찾은 다음 일치 하는 항목을 포함 하는 줄에 파일 이름, 줄 번호 및 모든 텍스트를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-114">By default, `Select-String` finds the first match in each line and, for each match, it displays the file name, line number, and all text in the line containing the match.</span></span> <span data-ttu-id="a8007-115">을 (를 `Select-String` ) 지정 하 여 줄 당 여러 개의 일치 항목을 찾거나, 일치 항목 앞뒤 텍스트를 표시 하거나, 일치 하는 항목이 있는지 여부를 나타내는 부울 값 (True 또는 False)을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-115">You can direct `Select-String` to find multiple matches per line, display text before and after the match, or display a Boolean value (True or False) that indicates whether a match is found.</span></span>

<span data-ttu-id="a8007-116">`Select-String` 정규식 일치를 사용 하지만 지정 된 텍스트에 대 한 입력을 검색 하는 일치를 수행할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-116">`Select-String` uses regular expression matching, but it can also perform a match that searches the input for the text that you specify.</span></span>

<span data-ttu-id="a8007-117">`Select-String` 각 입력 파일의 첫 번째 일치 항목 뒤에 나오는 모든 텍스트 일치 항목을 표시 하거나 중지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-117">`Select-String` can display all the text matches or stop after the first match in each input file.</span></span>
<span data-ttu-id="a8007-118">`Select-String` 지정 된 패턴과 일치 하지 않는 모든 텍스트를 표시 하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-118">`Select-String` can be used to display all text that doesn't match the specified pattern.</span></span>

<span data-ttu-id="a8007-119">`Select-String`유니코드 텍스트 파일을 검색 하는 경우와 같이 특정 문자 인코딩을 필요로 하도록 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-119">You can also specify that `Select-String` should expect a particular character encoding, such as when you're searching files of Unicode text.</span></span> <span data-ttu-id="a8007-120">`Select-String` 는 BOM (바이트 순서 표시)을 사용 하 여 파일의 인코딩 형식을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-120">`Select-String` uses the byte-order-mark (BOM) to detect the encoding format of the file.</span></span> <span data-ttu-id="a8007-121">파일에 BOM이 없으면 인코딩이 UTF8 이라고 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-121">If the file has no BOM, it assumes the encoding is UTF8.</span></span>

## <span data-ttu-id="a8007-122">예제</span><span class="sxs-lookup"><span data-stu-id="a8007-122">EXAMPLES</span></span>

### <span data-ttu-id="a8007-123">예 1: 대/소문자를 구분 하는 일치 찾기</span><span class="sxs-lookup"><span data-stu-id="a8007-123">Example 1: Find a case-sensitive match</span></span>

<span data-ttu-id="a8007-124">이 예에서는 파이프라인을 통해 cmdlet에 전송 된 텍스트와 대/소문자를 구분 하는 일치를 수행 합니다 `Select-String` .</span><span class="sxs-lookup"><span data-stu-id="a8007-124">This example does a case-sensitive match of the text that was sent down the pipeline to the `Select-String` cmdlet.</span></span>

```powershell
'Hello', 'HELLO' | Select-String -Pattern 'HELLO' -CaseSensitive -SimpleMatch
```

<span data-ttu-id="a8007-125">텍스트 문자열 **Hello** 및 **hello** 는 파이프라인에서 cmdlet으로 전송 됩니다 `Select-String` .</span><span class="sxs-lookup"><span data-stu-id="a8007-125">The text strings **Hello** and **HELLO** are sent down the pipeline to the `Select-String` cmdlet.</span></span>
<span data-ttu-id="a8007-126">`Select-String`**Pattern** 매개 변수를 사용 하 여 **HELLO** 를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-126">`Select-String` uses the **Pattern** parameter to specify **HELLO**.</span></span> <span data-ttu-id="a8007-127">**CaseSensitive** 매개 변수는 사례가 대문자 패턴만 일치 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-127">The **CaseSensitive** parameter specifies that the case must match only the upper-case pattern.</span></span> <span data-ttu-id="a8007-128">**SimpleMatch** 은 선택적 매개 변수 이며 패턴의 문자열이 정규식으로 해석 되지 않도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-128">**SimpleMatch** is an optional parameter and specifies that the string in the pattern isn't interpreted as a regular expression.</span></span>
<span data-ttu-id="a8007-129">`Select-String` PowerShell 콘솔에 **HELLO** 를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-129">`Select-String` displays **HELLO** in the PowerShell console.</span></span>

### <span data-ttu-id="a8007-130">예제 2: 텍스트 파일에서 일치 항목 찾기</span><span class="sxs-lookup"><span data-stu-id="a8007-130">Example 2: Find matches in text files</span></span>

<span data-ttu-id="a8007-131">이 명령은 `.txt` 현재 디렉터리에 있는 파일 이름 확장명을 가진 모든 파일을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-131">This command searches all files with the `.txt` file name extension in the current directory.</span></span> <span data-ttu-id="a8007-132">출력은 지정 된 문자열을 포함 하는 해당 파일의 줄을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-132">The output displays the lines in those files that include the specified string.</span></span>

```powershell
Get-Alias | Out-File -FilePath .\Alias.txt
Get-Command | Out-File -FilePath .\Command.txt
Select-String -Path .\*.txt -Pattern 'Get-'
```

```Output
Alias.txt:8:Alias            cat -> Get-Content
Alias.txt:28:Alias           dir -> Get-ChildItem
Alias.txt:43:Alias           gal -> Get-Alias
Command.txt:966:Cmdlet       Get-Acl
Command.txt:967:Cmdlet       Get-Alias
```

<span data-ttu-id="a8007-133">이 예제에서는 `Get-Alias` 및를 `Get-Command` cmdlet과 함께 사용 `Out-File` 하 여 현재 디렉터리에 두 개의 텍스트 파일 **Alias.txt** 및 **Command.txt** 를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-133">In this example, `Get-Alias` and `Get-Command` are used with the `Out-File` cmdlet to create two text files in the current directory, **Alias.txt** and **Command.txt**.</span></span>

<span data-ttu-id="a8007-134">`Select-String` 는 **Path** 매개 변수를 별표 ( `*` ) 와일드 카드와 함께 사용 하 여 현재 디렉터리에서 파일 이름 확장명을 가진 모든 파일을 검색 `.txt` 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-134">`Select-String` uses the **Path** parameter with the asterisk (`*`) wildcard to search all files in the current directory with the file name extension `.txt`.</span></span> <span data-ttu-id="a8007-135">**Pattern** 매개 변수는 **Get-** 과 일치 하는 텍스트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-135">The **Pattern** parameter specifies the text to match **Get-**.</span></span> <span data-ttu-id="a8007-136">`Select-String` PowerShell 콘솔에 출력을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-136">`Select-String` displays the output in the PowerShell console.</span></span> <span data-ttu-id="a8007-137">파일 이름과 줄 번호는 **패턴** 매개 변수와 일치 하는 항목을 포함 하는 각 내용의 줄 앞에 옵니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-137">The file name and line number precede each line of content that contains a match for the **Pattern** parameter.</span></span>

### <span data-ttu-id="a8007-138">예제 3: 패턴 일치 찾기</span><span class="sxs-lookup"><span data-stu-id="a8007-138">Example 3: Find a pattern match</span></span>

<span data-ttu-id="a8007-139">이 예제에서는 지정 된 패턴과 일치 하는 항목을 찾기 위해 여러 파일을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-139">In this example, multiple files are searched to find matches for the specified pattern.</span></span> <span data-ttu-id="a8007-140">패턴은 정규식 수량자를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-140">The pattern uses a regular expression quantifier.</span></span> <span data-ttu-id="a8007-141">자세한 내용은 [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/About_Regular_Expressions.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a8007-141">For more information, see [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/About_Regular_Expressions.md).</span></span>

```powershell
Select-String -Path "$PSHOME\en-US\*.txt" -Pattern '\?'
```

```Output
C:\Program Files\PowerShell\6\en-US\default.help.txt:27:    beginning at https://go.microsoft.com/fwlink/?LinkID=108518.
C:\Program Files\PowerShell\6\en-US\default.help.txt:50:    or go to: https://go.microsoft.com/fwlink/?LinkID=210614
```

<span data-ttu-id="a8007-142">`Select-String`Cmdlet은 **경로** 와 **패턴** 의 두 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-142">The `Select-String` cmdlet uses two parameters, **Path** and **Pattern**.</span></span> <span data-ttu-id="a8007-143">**Path** 매개 변수는 `$PSHOME` PowerShell 디렉터리를 지정 하는 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-143">The **Path** parameter uses the variable `$PSHOME` that specifies the PowerShell directory.</span></span> <span data-ttu-id="a8007-144">경로의 나머지 부분에는 **en-us** 하위 디렉터리가 포함 되 고 디렉터리의 각 파일을 지정 합니다 `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="a8007-144">The remainder of the path includes the subdirectory **en-US** and specifies each `*.txt` file in the directory.</span></span> <span data-ttu-id="a8007-145">**패턴** 매개 변수는 각 파일에서 물음표 ()와 일치 하도록 지정 합니다 `?` .</span><span class="sxs-lookup"><span data-stu-id="a8007-145">The **Pattern** parameter specifies to match a question mark (`?`) in each file.</span></span> <span data-ttu-id="a8007-146">백슬래시 ( `\` )는 이스케이프 문자로 사용 되며 물음표 ( `?` )는 정규식 수량자 이므로 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-146">A backslash (`\`) is used as an escape character and is necessary because the question mark (`?`) is a regular expression quantifier.</span></span> <span data-ttu-id="a8007-147">`Select-String` PowerShell 콘솔에 출력을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-147">`Select-String` displays the output in the PowerShell console.</span></span> <span data-ttu-id="a8007-148">파일 이름과 줄 번호는 **패턴** 매개 변수와 일치 하는 항목을 포함 하는 각 내용의 줄 앞에 옵니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-148">The file name and line number precede each line of content that contains a match for the **Pattern** parameter.</span></span>

### <span data-ttu-id="a8007-149">예제 4: 함수에서 Select-String 사용</span><span class="sxs-lookup"><span data-stu-id="a8007-149">Example 4: Use Select-String in a function</span></span>

<span data-ttu-id="a8007-150">이 예에서는 PowerShell 도움말 파일에서 패턴을 검색 하는 함수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-150">This example creates a function to search for a pattern in the PowerShell help files.</span></span> <span data-ttu-id="a8007-151">이 예에서는 함수가 PowerShell 세션에만 존재 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-151">For this example, the function only exists in the PowerShell session.</span></span> <span data-ttu-id="a8007-152">PowerShell 세션이 닫히면 함수는 삭제 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-152">When the PowerShell session is closed, the function is deleted.</span></span> <span data-ttu-id="a8007-153">자세한 내용은 [about_Functions](../Microsoft.PowerShell.Core/About/about_Functions.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a8007-153">For more information, see [about_Functions](../Microsoft.PowerShell.Core/About/about_Functions.md).</span></span>

```
PS> Function Search-Help
>> {
>> $PSHelp = "$PSHOME\en-US\*.txt"
>> Select-String -Path $PSHelp -Pattern 'About_'
>> }
PS>

PS> Search-Help

C:\Windows\System32\WindowsPowerShell\v1.0\en-US\about_ActivityCommonParameters.help.txt:2:   about_ActivityCommonParameters
C:\Windows\System32\WindowsPowerShell\v1.0\en-US\about_ActivityCommonParameters.help.txt:31:  see about_WorkflowCommonParameters.
C:\Windows\System32\WindowsPowerShell\v1.0\en-US\about_ActivityCommonParameters.help.txt:33:  about_CommonParameters.
```

<span data-ttu-id="a8007-154">함수가 PowerShell 명령줄에 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-154">The function is created on the PowerShell command line.</span></span> <span data-ttu-id="a8007-155">이 `Function` 명령은 **Search Help** 이름을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-155">The `Function` command uses the name **Search-Help**.</span></span> <span data-ttu-id="a8007-156">**Enter** 키를 눌러 함수에 문을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-156">Press **Enter** to begin adding statements to the function.</span></span> <span data-ttu-id="a8007-157">프롬프트에서 `>>` 각 문을 추가 하 고 예제와 같이 **enter** 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-157">From the `>>` prompt, add each statement and press **Enter** as shown in the example.</span></span> <span data-ttu-id="a8007-158">닫는 대괄호가 추가 되 면 PowerShell 프롬프트로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-158">After the closing bracket is added, you're returned to a PowerShell prompt.</span></span>

<span data-ttu-id="a8007-159">함수는 두 개의 명령을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-159">The function contains two commands.</span></span> <span data-ttu-id="a8007-160">`$PSHelp`변수는 PowerShell 도움말 파일에 대 한 경로를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-160">The `$PSHelp` variable stores the path to the PowerShell help files.</span></span> <span data-ttu-id="a8007-161">`$PSHOME` 는 디렉터리의 각 파일을 지정 하는 디렉터리 **en-us** 를 사용 하는 PowerShell 설치 디렉터리입니다 `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="a8007-161">`$PSHOME` is the PowerShell installation directory with the subdirectory **en-US** that specifies each `*.txt` file in the directory.</span></span>

<span data-ttu-id="a8007-162">`Select-String`함수의 명령은 **Path** 및 **Pattern** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-162">The `Select-String` command in the function uses the **Path** and **Pattern** parameters.</span></span> <span data-ttu-id="a8007-163">**Path** 매개 변수는 변수를 사용 하 여 `$PSHelp` 경로를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-163">The **Path** parameter uses the `$PSHelp` variable to get the path.</span></span> <span data-ttu-id="a8007-164">**패턴** 매개 변수는 **About_** 문자열을 검색 조건으로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-164">The **Pattern** parameter uses the string **About_** as the search criteria.</span></span>

<span data-ttu-id="a8007-165">함수를 실행 하려면를 입력 `Search-Help` 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-165">To run the function, type `Search-Help`.</span></span> <span data-ttu-id="a8007-166">함수의 `Select-String` 명령은 PowerShell 콘솔에 출력을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-166">The function's `Select-String` command displays the output in the PowerShell console.</span></span>

### <span data-ttu-id="a8007-167">예 5: Windows 이벤트 로그에서 문자열 검색</span><span class="sxs-lookup"><span data-stu-id="a8007-167">Example 5: Search for a string in a Windows event log</span></span>

<span data-ttu-id="a8007-168">이 예에서는 Windows 이벤트 로그에서 문자열을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-168">This example searches for a string in a Windows event log.</span></span> <span data-ttu-id="a8007-169">변수는 `$_` 파이프라인의 현재 개체를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-169">The variable `$_` represents the current object in the pipeline.</span></span> <span data-ttu-id="a8007-170">자세한 내용은 [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a8007-170">For more information, see [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md).</span></span>

```powershell
$Events = Get-WinEvent -LogName Application -MaxEvents 50
$Events | Select-String -InputObject {$_.message} -Pattern 'Failed'
```

<span data-ttu-id="a8007-171">`Get-WinEvent`Cmdlet은 **LogName** 매개 변수를 사용 하 여 응용 프로그램 로그를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-171">The `Get-WinEvent` cmdlet uses the **LogName** parameter to specify the Application log.</span></span> <span data-ttu-id="a8007-172">**Maxevents** 매개 변수는 로그에서 50의 최신 이벤트를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-172">The **MaxEvents** parameter gets the 50 most recent events from the log.</span></span> <span data-ttu-id="a8007-173">로그 콘텐츠는 라는 변수에 저장 됩니다 `$Events` .</span><span class="sxs-lookup"><span data-stu-id="a8007-173">The log content is stored in the variable named `$Events`.</span></span>

<span data-ttu-id="a8007-174">`$Events`변수가 파이프라인에서 cmdlet으로 전송 됩니다 `Select-String` .</span><span class="sxs-lookup"><span data-stu-id="a8007-174">The `$Events` variable is sent down the pipeline to the `Select-String` cmdlet.</span></span> <span data-ttu-id="a8007-175">`Select-String`**InputObject** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-175">`Select-String` uses the **InputObject** parameter.</span></span> <span data-ttu-id="a8007-176">`$_`변수는 현재 개체를 나타내고 `message` 는 이벤트의 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-176">The `$_` variable represents the current object and `message` is a property of the event.</span></span> <span data-ttu-id="a8007-177">**패턴** 매개 변수는 **실패** 문자열을,에서 일치 하는 항목을 검색 합니다 `$_.message` .</span><span class="sxs-lookup"><span data-stu-id="a8007-177">The **Pattern** parameter species the string **Failed** and searches for matches in `$_.message`.</span></span> <span data-ttu-id="a8007-178">`Select-String` PowerShell 콘솔에 출력을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-178">`Select-String` displays the output in the PowerShell console.</span></span>

### <span data-ttu-id="a8007-179">예제 6: 하위 디렉터리에서 문자열 찾기</span><span class="sxs-lookup"><span data-stu-id="a8007-179">Example 6: Find a string in subdirectories</span></span>

<span data-ttu-id="a8007-180">이 예에서는 디렉터리와 모든 하위 디렉터리에서 특정 텍스트 문자열을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-180">This example searches a directory and all of its subdirectories for a specific text string.</span></span>

```powershell
Get-ChildItem -Path C:\Windows\System32\*.txt -Recurse | Select-String -Pattern 'Microsoft' -CaseSensitive
```

<span data-ttu-id="a8007-181">`Get-ChildItem`**Path** 매개 변수를 사용 하 여 **를 \* 지정 합니다.**</span><span class="sxs-lookup"><span data-stu-id="a8007-181">`Get-ChildItem` uses the **Path** parameter to specify **C:\Windows\System32\*.txt**.</span></span> <span data-ttu-id="a8007-182">**재귀** 매개 변수는 하위 디렉터리를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-182">The **Recurse** parameter includes the subdirectories.</span></span> <span data-ttu-id="a8007-183">개체는 파이프라인에서로 전송 됩니다 `Select-String` .</span><span class="sxs-lookup"><span data-stu-id="a8007-183">The objects are sent down the pipeline to `Select-String`.</span></span>

<span data-ttu-id="a8007-184">`Select-String` 는 **Pattern** 매개 변수를 사용 하 고 **Microsoft** 문자열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-184">`Select-String` uses the **Pattern** parameter and specifies the string **Microsoft**.</span></span> <span data-ttu-id="a8007-185">**CaseSensitive** 매개 변수는 문자열의 정확한 대/소문자를 비교 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-185">The **CaseSensitive** parameter is used to match the exact case of the string.</span></span> <span data-ttu-id="a8007-186">`Select-String` PowerShell 콘솔에 출력을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-186">`Select-String` displays the output in the PowerShell console.</span></span>

> [!NOTE]
> <span data-ttu-id="a8007-187">사용 권한에 따라 출력에 **액세스 거부** 메시지가 표시 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-187">Dependent upon your permissions, you might see **Access denied** messages in the output.</span></span>

### <span data-ttu-id="a8007-188">예 7: 패턴과 일치 하지 않는 문자열 찾기</span><span class="sxs-lookup"><span data-stu-id="a8007-188">Example 7: Find strings that do not match a pattern</span></span>

<span data-ttu-id="a8007-189">이 예제에서는 패턴과 일치 하지 않는 데이터 줄을 제외 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-189">This example shows how to exclude lines of data that don't match a pattern.</span></span>

```powershell
Get-Command | Out-File -FilePath .\Command.txt
Select-String -Path .\Command.txt -Pattern 'Get', 'Set'  -NotMatch
```

<span data-ttu-id="a8007-190">Cmdlet은 개체를에 `Get-Command` 파이프라인으로 보내 `Out-File` 현재 디렉터리에 **Command.txt** 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-190">The `Get-Command` cmdlet sends objects down the pipeline to the `Out-File` to create the **Command.txt** file in the current directory.</span></span> <span data-ttu-id="a8007-191">`Select-String`**Path** 매개 변수를 사용 하 여 **Command.txt** 파일을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-191">`Select-String` uses the **Path** parameter to specify the **Command.txt** file.</span></span> <span data-ttu-id="a8007-192">**Pattern** 매개 변수는 **Get** 및 **Set** 을 검색 패턴으로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-192">The **Pattern** parameter specifies **Get** and **Set** as the search pattern.</span></span> <span data-ttu-id="a8007-193">**Notmatch** 매개 변수는 **Get** 및 **Set** 을 결과에서 제외 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-193">The **NotMatch** parameter excludes **Get** and **Set** from the results.</span></span>
<span data-ttu-id="a8007-194">`Select-String`**Get** 또는 **Set** 을 포함 하지 않는 PowerShell 콘솔의 출력을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-194">`Select-String` displays the output in the PowerShell console that doesn't include **Get** or **Set**.</span></span>

### <span data-ttu-id="a8007-195">예 8: 일치 전후 줄 찾기</span><span class="sxs-lookup"><span data-stu-id="a8007-195">Example 8: Find lines before and after a match</span></span>

<span data-ttu-id="a8007-196">이 예제에서는 일치 하는 패턴 앞뒤의 줄을 가져오는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-196">This example shows how to get the lines before and after the matched pattern.</span></span>

```powershell
Get-Command | Out-File -FilePath .\Command.txt
Select-String -Path .\Command.txt -Pattern 'Get-Computer' -Context 2, 3
```

```Output
  Command.txt:1186:Cmdlet          Get-CmsMessage            3.0.0.0    Microsoft.PowerShell.Security
  Command.txt:1187:Cmdlet          Get-Command               3.0.0.0    Microsoft.PowerShell.Core
> Command.txt:1188:Cmdlet          Get-ComputerInfo          3.1.0.0    Microsoft.PowerShell.Management
> Command.txt:1189:Cmdlet          Get-ComputerRestorePoint  3.1.0.0    Microsoft.PowerShell.Management
  Command.txt:1190:Cmdlet          Get-Content               3.1.0.0    Microsoft.PowerShell.Management
  Command.txt:1191:Cmdlet          Get-ControlPanelItem      3.1.0.0    Microsoft.PowerShell.Management
  Command.txt:1192:Cmdlet          Get-Counter               3.0.0.0    Microsoft.PowerShell.Diagnostics
```

<span data-ttu-id="a8007-197">Cmdlet은 개체를에 `Get-Command` 파이프라인으로 보내 `Out-File` 현재 디렉터리에 **Command.txt** 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-197">The `Get-Command` cmdlet sends objects down the pipeline to the `Out-File` to create the **Command.txt** file in the current directory.</span></span> <span data-ttu-id="a8007-198">`Select-String`**Path** 매개 변수를 사용 하 여 **Command.txt** 파일을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-198">`Select-String` uses the **Path** parameter to specify the **Command.txt** file.</span></span> <span data-ttu-id="a8007-199">**Pattern** 매개 변수는 **가져오기 컴퓨터** 를 검색 패턴으로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-199">The **Pattern** parameter specifies **Get-Computer** as the search pattern.</span></span> <span data-ttu-id="a8007-200">**컨텍스트** 매개 변수는 앞과 뒤에 두 개의 값을 사용 하 고 출력에서 패턴 일치를 꺾쇠 괄호 ( `>` )로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-200">The **Context** parameter uses two values, before and after, and marks pattern matches in the output with an angle bracket (`>`).</span></span> <span data-ttu-id="a8007-201">**Context** 매개 변수는 첫 번째 패턴 일치 앞에 두 줄을 출력 하 고, 마지막 패턴 일치 후에 세 줄을 출력 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-201">The **Context** parameter outputs the two lines before the first pattern match and three lines after the last pattern match.</span></span>

### <span data-ttu-id="a8007-202">예 9: 모든 패턴 일치 찾기</span><span class="sxs-lookup"><span data-stu-id="a8007-202">Example 9: Find all pattern matches</span></span>

<span data-ttu-id="a8007-203">이 예제에서는 **Allmatches** 매개 변수가 텍스트 줄에서 각 패턴 일치 항목을 찾는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-203">This example shows how the **AllMatches** parameter finds each pattern match in a line of text.</span></span> <span data-ttu-id="a8007-204">기본적으로는 `Select-String` 텍스트 줄에서 첫 번째로 나타나는 패턴을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-204">By default, `Select-String` only finds the first occurrence of a pattern in a line of text.</span></span> <span data-ttu-id="a8007-205">이 예에서는 cmdlet에서 발견 된 개체 속성을 사용 `Get-Member` 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-205">This example uses object properties that are found with the `Get-Member` cmdlet.</span></span>

```
PS> $A = Get-ChildItem -Path "$PSHOME\en-US\*.txt" | Select-String -Pattern 'PowerShell'

PS> $A

C:\Windows\System32\WindowsPowerShell\v1.0\en-US\about_ActivityCommonParameters.help.txt:5:    Describes the parameters that Windows PowerShell
C:\Windows\System32\WindowsPowerShell\v1.0\en-US\about_ActivityCommonParameters.help.txt:9:    Windows PowerShell Workflow adds the activity common

PS> $A.Matches

Groups   : {0}
Success  : True
Name     : 0
Captures : {0}
Index    : 4
Length   : 10
Value    : PowerShell

PS> $A.Matches.Length

2073

PS> $B = Get-ChildItem -Path "$PSHOME\en-US\*.txt" | Select-String -Pattern 'PowerShell' -AllMatches

PS> $B.Matches.Length

2200
```

<span data-ttu-id="a8007-206">`Get-ChildItem`Cmdlet은 **Path** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-206">The `Get-ChildItem` cmdlet uses the **Path** parameter.</span></span> <span data-ttu-id="a8007-207">**Path** 매개 변수는 `$PSHOME` PowerShell 디렉터리를 지정 하는 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-207">The **Path** parameter uses the variable `$PSHOME` that specifies the PowerShell directory.</span></span> <span data-ttu-id="a8007-208">경로의 나머지 부분에는 **en-us** 하위 디렉터리가 포함 되 고 디렉터리의 각 파일을 지정 합니다 `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="a8007-208">The remainder of the path includes the subdirectory **en-US** and specifies each `*.txt` file in the directory.</span></span> <span data-ttu-id="a8007-209">`Get-ChildItem`개체는 변수에 저장 됩니다 `$A` .</span><span class="sxs-lookup"><span data-stu-id="a8007-209">The `Get-ChildItem` objects are stored in the `$A` variable.</span></span> <span data-ttu-id="a8007-210">`$A`변수가 파이프라인에서 cmdlet으로 전송 됩니다 `Select-String` .</span><span class="sxs-lookup"><span data-stu-id="a8007-210">The `$A` variable is sent down the pipeline to the `Select-String` cmdlet.</span></span> <span data-ttu-id="a8007-211">`Select-String` 는 **Pattern** 매개 변수를 사용 하 여 각 파일에서 문자열 **PowerShell** 을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-211">`Select-String` uses the **Pattern** parameter to search each file for the string **PowerShell**.</span></span>

<span data-ttu-id="a8007-212">PowerShell 명령줄에서 `$A` 변수 내용이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-212">From the PowerShell command line, the `$A` variable contents are displayed.</span></span> <span data-ttu-id="a8007-213">두 번의 문자열 **PowerShell** 이 포함 된 줄이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-213">There's a line that contains two occurrences of the string **PowerShell**.</span></span>

<span data-ttu-id="a8007-214">`$A.Matches`속성은 각 줄에서 처음 발견 되는 패턴 **PowerShell** 을 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-214">The `$A.Matches` property lists the first occurrence of the pattern **PowerShell** on each line.</span></span>

<span data-ttu-id="a8007-215">`$A.Matches.Length`속성은 각 줄에서 처음 발견 되는 패턴 **PowerShell** 수를 계산 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-215">The `$A.Matches.Length` property counts the first occurrence of the pattern **PowerShell** on each line.</span></span>

<span data-ttu-id="a8007-216">`$B`변수는 동일한 `Get-ChildItem` 및 `Select-String` cmdlet을 사용 하지만 **allmatches** 매개 변수를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-216">The `$B` variable uses the same `Get-ChildItem` and `Select-String` cmdlets, but adds the **AllMatches** parameter.</span></span> <span data-ttu-id="a8007-217">**Allmatches** 는 각 줄에서 각 패턴 **PowerShell** 의 발생을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-217">**AllMatches** finds each occurrence of the pattern **PowerShell** on each line.</span></span> <span data-ttu-id="a8007-218">및 변수에 저장 된 개체 `$A` 는 `$B` 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-218">The objects stored in the `$A` and `$B` variables are identical.</span></span>

<span data-ttu-id="a8007-219">`$B.Matches.Length`각 줄에 대해 패턴 **PowerShell** 의 모든 발생이 계산 되기 때문에 속성은 늘어납니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-219">The `$B.Matches.Length` property increases because for each line, every occurrence of the pattern **PowerShell** is counted.</span></span>

## <span data-ttu-id="a8007-220">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a8007-220">PARAMETERS</span></span>

### <span data-ttu-id="a8007-221">-AllMatches</span><span class="sxs-lookup"><span data-stu-id="a8007-221">-AllMatches</span></span>

<span data-ttu-id="a8007-222">Cmdlet이 각 텍스트 줄에서 일치 하는 항목을 두 개 이상 검색 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-222">Indicates that the cmdlet searches for more than one match in each line of text.</span></span> <span data-ttu-id="a8007-223">이 매개 변수를 사용 하지 않으면는 `Select-String` 각 텍스트 줄에서 첫 번째 일치 항목만 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-223">Without this parameter, `Select-String` finds only the first match in each line of text.</span></span>

<span data-ttu-id="a8007-224">가 `Select-String` 텍스트 줄에서 일치 하는 항목을 여러 개 찾은 경우에도 해당 줄에 대해 하나의 **matchinfo** 개체만 가져오지만 개체의 **matches** 속성은 모든 일치 항목을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-224">When `Select-String` finds more than one match in a line of text, it still emits only one **MatchInfo** object for the line, but the **Matches** property of the object contains all the matches.</span></span>

> [!NOTE]
> <span data-ttu-id="a8007-225">이 매개 변수는 **SimpleMatch** 매개 변수와 함께 사용 하면 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-225">This parameter is ignored when used in combination with the **SimpleMatch** parameter.</span></span> <span data-ttu-id="a8007-226">모든 일치 항목을 반환 하려는 경우 검색 하는 패턴에 정규식 문자가 포함 되어 있으면 **SimpleMatch** 를 사용 하는 대신 해당 문자를 이스케이프 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-226">If you wish to return all matches and the pattern that you are searching for contains regular expression characters, you must escape those characters rather than using **SimpleMatch**.</span></span> <span data-ttu-id="a8007-227">정규식 이스케이프에 대 한 자세한 내용은 [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a8007-227">See [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md) for more information about escaping regular expressions.</span></span>

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

### <span data-ttu-id="a8007-228">-CaseSensitive</span><span class="sxs-lookup"><span data-stu-id="a8007-228">-CaseSensitive</span></span>

<span data-ttu-id="a8007-229">Cmdlet이 대/소문자를 구분 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-229">Indicates that the cmdlet matches are case-sensitive.</span></span> <span data-ttu-id="a8007-230">기본적으로 일치는 대/소문자를 구분 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-230">By default, matches aren't case-sensitive.</span></span>

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

### <span data-ttu-id="a8007-231">-Context</span><span class="sxs-lookup"><span data-stu-id="a8007-231">-Context</span></span>

<span data-ttu-id="a8007-232">패턴과 일치 하는 줄의 앞과 뒤에 지정 된 수의 줄을 캡처합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-232">Captures the specified number of lines before and after the line that matches the pattern.</span></span>

<span data-ttu-id="a8007-233">이 매개 변수 값으로 하나의 숫자를 입력하면 해당 숫자가 일치하는 항목이 있는 줄 앞뒤로 캡처할 줄 수를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-233">If you enter one number as the value of this parameter, that number determines the number of lines captured before and after the match.</span></span> <span data-ttu-id="a8007-234">값으로 숫자를 두 개 입력하면 첫 번째 숫자는 일치 항목 앞의 줄 수를 결정하고 두 번째 숫자는 일치 항목 뒤의 줄 수를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-234">If you enter two numbers as the value, the first number determines the number of lines before the match and the second number determines the number of lines after the match.</span></span> <span data-ttu-id="a8007-235">예들 들어 `-Context 2,3`입니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-235">For example, `-Context 2,3`.</span></span>

<span data-ttu-id="a8007-236">기본 표시에서 일치 하는 줄이 `>` 표시의 첫 번째 열에 오른쪽 꺾쇠 괄호 () (ASCII 62)로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-236">In the default display, lines with a match are indicated by a right angle bracket (`>`) (ASCII 62) in the first column of the display.</span></span> <span data-ttu-id="a8007-237">표시되지 않은 줄은 컨텍스트입니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-237">Unmarked lines are the context.</span></span>

<span data-ttu-id="a8007-238">**컨텍스트** 매개 변수는에 의해 생성 된 개체의 수를 변경 하지 않습니다 `Select-String` .</span><span class="sxs-lookup"><span data-stu-id="a8007-238">The **Context** parameter doesn't change the number of objects generated by `Select-String`.</span></span>
<span data-ttu-id="a8007-239">`Select-String` 각 일치 항목에 대해 하나의 [Matchinfo](/dotnet/api/microsoft.powershell.commands.matchinfo) 개체를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-239">`Select-String` generates one [MatchInfo](/dotnet/api/microsoft.powershell.commands.matchinfo) object for each match.</span></span> <span data-ttu-id="a8007-240">컨텍스트는 개체의 **컨텍스트** 속성에 문자열 배열로 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-240">The context is stored as an array of strings in the **Context** property of the object.</span></span>

<span data-ttu-id="a8007-241">`Select-String`명령의 출력이 파이프라인에서 다른 명령으로 전송 되 면 `Select-String` 수신 명령은 일치 하는 줄의 텍스트만 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-241">When the output of a `Select-String` command is sent down the pipeline to another `Select-String` command, the receiving command searches only the text in the matched line.</span></span> <span data-ttu-id="a8007-242">일치 하는 줄은 컨텍스트 줄의 텍스트가 아니라 **Matchinfo** 개체의 **line** 속성 값입니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-242">The matched line is the value of the **Line** property of the **MatchInfo** object, not the text in the context lines.</span></span> <span data-ttu-id="a8007-243">결과적으로 **컨텍스트** 매개 변수는 수신 명령에서 유효 하지 않습니다 `Select-String` .</span><span class="sxs-lookup"><span data-stu-id="a8007-243">As a result, the **Context** parameter isn't valid on the receiving `Select-String` command.</span></span>

<span data-ttu-id="a8007-244">컨텍스트에 일치 항목이 포함 된 경우 각 일치 항목에 대 한 **Matchinfo** 개체에는 모든 컨텍스트 줄이 포함 되지만 겹치는 줄은 표시에 한 번만 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-244">When the context includes a match, the **MatchInfo** object for each match includes all the context lines, but the overlapping lines appear only once in the display.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a8007-245">-Encoding</span><span class="sxs-lookup"><span data-stu-id="a8007-245">-Encoding</span></span>

<span data-ttu-id="a8007-246">대상 파일의 인코딩 유형을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-246">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="a8007-247">기본값은 `default`입니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-247">The default value is `default`.</span></span>

<span data-ttu-id="a8007-248">이 매개 변수에 허용 되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-248">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="a8007-249">`ascii` ASCII (7 비트) 문자 집합을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-249">`ascii` Uses ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="a8007-250">`bigendianunicode` 에서는 u t f-16을 빅 endian 바이트 순서로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-250">`bigendianunicode` Uses UTF-16 with the big-endian byte order.</span></span>
- <span data-ttu-id="a8007-251">`default` 시스템의 활성 코드 페이지에 해당 하는 인코딩을 사용 합니다 (일반적으로 ANSI).</span><span class="sxs-lookup"><span data-stu-id="a8007-251">`default` Uses the encoding that corresponds to the system's active code page (usually ANSI).</span></span>
- <span data-ttu-id="a8007-252">`oem` 시스템의 현재 OEM 코드 페이지에 해당 하는 인코딩을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-252">`oem` Uses the encoding that corresponds to the system's current OEM code page.</span></span>
- <span data-ttu-id="a8007-253">`unicode` 는 u t f-16을 약간 endian 바이트 순서로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-253">`unicode` Uses UTF-16 with the little-endian byte order.</span></span>
- <span data-ttu-id="a8007-254">`utf7` 는 u t f-7을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-254">`utf7` Uses UTF-7.</span></span>
- <span data-ttu-id="a8007-255">`utf8` 는 u t f-8을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-255">`utf8` Uses UTF-8.</span></span>
- <span data-ttu-id="a8007-256">`utf32` 는 u t f-32을 작은 endian 바이트 순서로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-256">`utf32` Uses UTF-32 with the little-endian byte order.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, Default, OEM, Unicode, UTF7, UTF8, UTF32

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a8007-257">-제외</span><span class="sxs-lookup"><span data-stu-id="a8007-257">-Exclude</span></span>

<span data-ttu-id="a8007-258">지정된 항목을 제외합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-258">Exclude the specified items.</span></span> <span data-ttu-id="a8007-259">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-259">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="a8007-260">경로 요소 또는 패턴 (예:)을 입력 `*.txt` 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-260">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="a8007-261">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-261">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="a8007-262">-포함</span><span class="sxs-lookup"><span data-stu-id="a8007-262">-Include</span></span>

<span data-ttu-id="a8007-263">지정한 항목을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-263">Includes the specified items.</span></span> <span data-ttu-id="a8007-264">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-264">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="a8007-265">경로 요소 또는 패턴 (예:)을 입력 `*.txt` 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-265">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="a8007-266">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-266">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="a8007-267">-InputObject</span><span class="sxs-lookup"><span data-stu-id="a8007-267">-InputObject</span></span>

<span data-ttu-id="a8007-268">검색할 텍스트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-268">Specifies the text to be searched.</span></span> <span data-ttu-id="a8007-269">텍스트가 포함된 변수를 입력하거나 텍스트를 가져오는 명령 또는 식을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="a8007-269">Enter a variable that contains the text, or type a command or expression that gets the text.</span></span>

<span data-ttu-id="a8007-270">**InputObject** 매개 변수를 사용 하는 것은 파이프라인에서로 문자열을 보내는 것과는 다릅니다 `Select-String` .</span><span class="sxs-lookup"><span data-stu-id="a8007-270">Using the **InputObject** parameter isn't the same as sending strings down the pipeline to `Select-String`.</span></span>

<span data-ttu-id="a8007-271">둘 이상의 문자열을 cmdlet에 파이프 하면 `Select-String` 각 문자열에서 지정 된 텍스트를 검색 하 고 검색 텍스트가 포함 된 각 문자열을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-271">When you pipe more than one string to the `Select-String` cmdlet, it searches for the specified text in each string and returns each string that contains the search text.</span></span>

<span data-ttu-id="a8007-272">**InputObject** 매개 변수를 사용 하 여 문자열 컬렉션을 전송 하는 경우는 `Select-String` 컬렉션을 결합 된 단일 문자열로 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-272">When you use the **InputObject** parameter to submit a collection of strings, `Select-String` treats the collection as a single combined string.</span></span> <span data-ttu-id="a8007-273">`Select-String` 문자열에서 검색 텍스트를 찾은 경우 해당 문자열을 하나의 단위로 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-273">`Select-String` returns the strings as a unit if it finds the search text in any string.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: Object
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="a8007-274">-목록</span><span class="sxs-lookup"><span data-stu-id="a8007-274">-List</span></span>

<span data-ttu-id="a8007-275">일치 하는 텍스트의 첫 번째 인스턴스만 각 입력 파일에서 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-275">Only the first instance of matching text is returned from each input file.</span></span> <span data-ttu-id="a8007-276">이는 정규식과 일치 하는 내용이 있는 파일 목록을 검색 하는 가장 효율적인 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-276">This is the most efficient way to retrieve a list of files that have contents matching the regular expression.</span></span>

<span data-ttu-id="a8007-277">기본적으로는 `Select-String` 찾은 각 일치 항목에 대해 **matchinfo** 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-277">By default, `Select-String` returns a **MatchInfo** object for each match it finds.</span></span>

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

### <span data-ttu-id="a8007-278">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="a8007-278">-LiteralPath</span></span>

<span data-ttu-id="a8007-279">검색할 파일의 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-279">Specifies the path to the files to be searched.</span></span> <span data-ttu-id="a8007-280">**LiteralPath** 매개 변수의 값은 입력 한 대로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-280">The value of the **LiteralPath** parameter is used exactly as it's typed.</span></span> <span data-ttu-id="a8007-281">어떠한 문자도 와일드카드로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-281">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="a8007-282">이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요.</span><span class="sxs-lookup"><span data-stu-id="a8007-282">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="a8007-283">작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-283">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span> <span data-ttu-id="a8007-284">자세한 내용은 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a8007-284">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralFile
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a8007-285">-NotMatch</span><span class="sxs-lookup"><span data-stu-id="a8007-285">-NotMatch</span></span>

<span data-ttu-id="a8007-286">**Notmatch** 매개 변수는 지정 된 패턴과 일치 하지 않는 텍스트를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-286">The **NotMatch** parameter finds text that doesn't match the specified pattern.</span></span>

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

### <span data-ttu-id="a8007-287">-Path</span><span class="sxs-lookup"><span data-stu-id="a8007-287">-Path</span></span>

<span data-ttu-id="a8007-288">검색할 파일의 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-288">Specifies the path to the files to search.</span></span> <span data-ttu-id="a8007-289">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-289">Wildcards are permitted.</span></span> <span data-ttu-id="a8007-290">기본 위치는 로컬 디렉터리입니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-290">The default location is the local directory.</span></span>

<span data-ttu-id="a8007-291">디렉터리의 파일 (예:, 또는)을 지정 `log1.txt` `*.doc` `*.*` 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-291">Specify files in the directory, such as `log1.txt`, `*.doc`, or `*.*`.</span></span> <span data-ttu-id="a8007-292">디렉터리만 지정하면 명령이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-292">If you specify only a directory, the command fails.</span></span>

```yaml
Type: System.String[]
Parameter Sets: File
Aliases:

Required: True
Position: 1
Default value: Local directory
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="a8007-293">-패턴</span><span class="sxs-lookup"><span data-stu-id="a8007-293">-Pattern</span></span>

<span data-ttu-id="a8007-294">각 줄에서 찾을 텍스트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-294">Specifies the text to find on each line.</span></span> <span data-ttu-id="a8007-295">패턴 값은 정규식으로 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-295">The pattern value is treated as a regular expression.</span></span>

<span data-ttu-id="a8007-296">정규식에 대 한 자세한 내용은 [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a8007-296">To learn about regular expressions, see [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a8007-297">-Quiet</span><span class="sxs-lookup"><span data-stu-id="a8007-297">-Quiet</span></span>

<span data-ttu-id="a8007-298">Cmdlet이 **Matchinfo** 개체 대신 부울 값 (True 또는 False)을 반환 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-298">Indicates that the cmdlet returns a Boolean value (True or False), instead of a **MatchInfo** object.</span></span> <span data-ttu-id="a8007-299">패턴을 찾은 경우 값은 True입니다. 그렇지 않으면 False입니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-299">The value is True if the pattern is found; otherwise the value is False.</span></span>

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

### <span data-ttu-id="a8007-300">-SimpleMatch</span><span class="sxs-lookup"><span data-stu-id="a8007-300">-SimpleMatch</span></span>

<span data-ttu-id="a8007-301">Cmdlet이 정규식 일치 대신 단순 일치를 사용 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-301">Indicates that the cmdlet uses a simple match rather than a regular expression match.</span></span> <span data-ttu-id="a8007-302">단순 일치에서는 `Select-String` **패턴** 매개 변수에서 텍스트의 입력을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-302">In a simple match, `Select-String` searches the input for the text in the **Pattern** parameter.</span></span> <span data-ttu-id="a8007-303">**패턴** 매개 변수의 값을 정규식 문으로 해석 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-303">It doesn't interpret the value of the **Pattern** parameter as a regular expression statement.</span></span>

<span data-ttu-id="a8007-304">또한 **SimpleMatch** 를 사용 하면 반환 된 **Matchinfo** 개체의 **Matches** 속성이 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-304">Also, when **SimpleMatch** is used, the **Matches** property of the **MatchInfo** object returned is empty.</span></span>

> [!NOTE]
> <span data-ttu-id="a8007-305">**Allmatches** 매개 변수와 함께이 매개 변수를 사용 하는 경우 **allmatches** 는 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-305">When this parameter is used with the **AllMatches** parameter, the **AllMatches** is ignored.</span></span>

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

### <span data-ttu-id="a8007-306">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a8007-306">CommonParameters</span></span>

<span data-ttu-id="a8007-307">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a8007-307">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a8007-308">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a8007-308">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a8007-309">입력</span><span class="sxs-lookup"><span data-stu-id="a8007-309">INPUTS</span></span>

### <span data-ttu-id="a8007-310">System.web. PSObject</span><span class="sxs-lookup"><span data-stu-id="a8007-310">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="a8007-311">**ToString** 메서드가 있는 개체를로 파이프 할 수 있습니다 `Select-String` .</span><span class="sxs-lookup"><span data-stu-id="a8007-311">You can pipe any object that has a **ToString** method to `Select-String`.</span></span>

## <span data-ttu-id="a8007-312">출력</span><span class="sxs-lookup"><span data-stu-id="a8007-312">OUTPUTS</span></span>

### <span data-ttu-id="a8007-313">Microsoft.. MatchInfo 또는 system.string</span><span class="sxs-lookup"><span data-stu-id="a8007-313">Microsoft.PowerShell.Commands.MatchInfo or System.Boolean</span></span>

<span data-ttu-id="a8007-314">기본적으로 출력은 찾은 각 일치 항목에 대해 하나의 **Matchinfo** 개체 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-314">By default, the output is a set of **MatchInfo** objects with one for each match found.</span></span> <span data-ttu-id="a8007-315">**Quiet** 매개 변수를 사용 하는 경우 출력은 패턴을 찾을 수 있는지 여부를 나타내는 부울 값입니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-315">If you use the **Quiet** parameter, the output is a Boolean value indicating whether the pattern was found.</span></span>

## <span data-ttu-id="a8007-316">참고</span><span class="sxs-lookup"><span data-stu-id="a8007-316">NOTES</span></span>

<span data-ttu-id="a8007-317">`Select-String` UNIX의 **grep** 또는 Windows의 **findstr.exe** 와 유사 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-317">`Select-String` is similar to **grep** in UNIX or **findstr.exe** in Windows.</span></span>

<span data-ttu-id="a8007-318">Cmdlet에 대 한 **sls** 별칭은 `Select-String` PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-318">The **sls** alias for the `Select-String` cmdlet was introduced in PowerShell 3.0.</span></span>

> [!NOTE]
> <span data-ttu-id="a8007-319">[PowerShell 명령에 대해 승인 된 동사](/powershell/scripting/developer/cmdlet/approved-verbs-for-windows-powershell-commands)에 따라 cmdlet에 대 한 공식 별칭 접두사는 `Select-*` 가 `sc` 아니라입니다 `sl` .</span><span class="sxs-lookup"><span data-stu-id="a8007-319">According to [Approved Verbs for PowerShell Commands](/powershell/scripting/developer/cmdlet/approved-verbs-for-windows-powershell-commands), the official alias prefix for `Select-*` cmdlets is `sc`, not `sl`.</span></span> <span data-ttu-id="a8007-320">따라서에 대 한 적절 한 별칭은 `Select-String` `scs` 가 아니라 여야 합니다 `sls` .</span><span class="sxs-lookup"><span data-stu-id="a8007-320">Therefore, the proper alias for `Select-String` should be `scs`, not `sls`.</span></span> <span data-ttu-id="a8007-321">이 규칙의 예외입니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-321">This is an exception to this rule.</span></span>

<span data-ttu-id="a8007-322">을 사용 하려면 `Select-String` **패턴** 매개 변수의 값으로 찾을 텍스트를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-322">To use `Select-String`, type the text that you want to find as the value of the **Pattern** parameter.</span></span> <span data-ttu-id="a8007-323">검색할 텍스트를 지정 하려면 다음 조건을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-323">To specify the text to be searched, use the following criteria:</span></span>

- <span data-ttu-id="a8007-324">따옴표 붙은 문자열에 텍스트를 입력 하 고로 파이프 `Select-String` 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-324">Type the text in a quoted string, and then pipe it to `Select-String`.</span></span>
- <span data-ttu-id="a8007-325">텍스트 문자열을 변수에 저장 한 다음이 변수를 **InputObject** 매개 변수의 값으로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-325">Store a text string in a variable, and then specify the variable as the value of the **InputObject** parameter.</span></span>
- <span data-ttu-id="a8007-326">텍스트를 파일에 저장 하는 경우 **path** 매개 변수를 사용 하 여 파일 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-326">If the text is stored in files, use the **Path** parameter to specify the path to the files.</span></span>

<span data-ttu-id="a8007-327">기본적으로는 `Select-String` **패턴** 매개 변수의 값을 정규식으로 해석 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-327">By default, `Select-String` interprets the value of the **Pattern** parameter as a regular expression.</span></span> <span data-ttu-id="a8007-328">자세한 내용은 [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a8007-328">For more information, see [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md).</span></span> <span data-ttu-id="a8007-329">**SimpleMatch** 매개 변수를 사용 하 여 정규식 일치를 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-329">You can use the **SimpleMatch** parameter to override the regular expression matching.</span></span> <span data-ttu-id="a8007-330">**SimpleMatch** 매개 변수는 입력에서 **Pattern** 매개 변수 값의 인스턴스를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-330">The **SimpleMatch** parameter finds instances of the value of the **Pattern** parameter in the input.</span></span>

<span data-ttu-id="a8007-331">의 기본 출력은 `Select-String` 일치 항목에 대 한 자세한 정보를 포함 하는 **matchinfo** 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-331">The default output of `Select-String` is a **MatchInfo** object, which includes detailed information about the matches.</span></span> <span data-ttu-id="a8007-332">**Matchinfo** 개체에는 **Filename** 및 **Line** 과 같은 속성이 있으므로이 개체의 정보는 파일에서 텍스트를 검색 하는 경우에 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-332">The information in the object is useful when you're searching for text in files, because **MatchInfo** objects have properties such as **Filename** and **Line**.</span></span> <span data-ttu-id="a8007-333">입력이 파일이 아닌 경우이 매개 변수의 값은 **InputStream** 입니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-333">When the input isn't from the file, the value of these parameters is **InputStream**.</span></span>

<span data-ttu-id="a8007-334">**Matchinfo** 개체의 정보가 필요 하지 않은 경우에는 **Quiet** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-334">If you don't need the information in the **MatchInfo** object, use the **Quiet** parameter.</span></span> <span data-ttu-id="a8007-335">**Quiet** 매개 변수는 **matchinfo** 개체 대신 일치 하는 항목이 있는지 여부를 나타내는 부울 값 (True 또는 False)을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-335">The **Quiet** parameter returns a Boolean value (True or False) to indicate whether it found a match, instead of a **MatchInfo** object.</span></span>

<span data-ttu-id="a8007-336">구를 일치 시키는 경우는 `Select-String` 시스템에 대해 설정 된 현재 문화권을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-336">When matching phrases, `Select-String` uses the current culture that is set for the system.</span></span> <span data-ttu-id="a8007-337">현재 문화권을 찾으려면 cmdlet을 사용 합니다 `Get-Culture` .</span><span class="sxs-lookup"><span data-stu-id="a8007-337">To find the current culture, use the `Get-Culture` cmdlet.</span></span>

<span data-ttu-id="a8007-338">**Matchinfo** 개체의 속성을 찾으려면 다음 명령을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8007-338">To find the properties of a **MatchInfo** object, type the following command:</span></span>

`Select-String -Path test.txt -Pattern 'test' | Get-Member | Format-List -Property *`

## <span data-ttu-id="a8007-339">관련 링크</span><span class="sxs-lookup"><span data-stu-id="a8007-339">RELATED LINKS</span></span>

[<span data-ttu-id="a8007-340">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="a8007-340">about_Automatic_Variables</span></span>](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

[<span data-ttu-id="a8007-341">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="a8007-341">about_Comparison_Operators</span></span>](../Microsoft.PowerShell.Core/About/about_Comparison_Operators.md)

[<span data-ttu-id="a8007-342">about_Functions</span><span class="sxs-lookup"><span data-stu-id="a8007-342">about_Functions</span></span>](../Microsoft.PowerShell.Core/About/about_Functions.md)

[<span data-ttu-id="a8007-343">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="a8007-343">about_Quoting_Rules</span></span>](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)

[<span data-ttu-id="a8007-344">about_Regular_Expressions</span><span class="sxs-lookup"><span data-stu-id="a8007-344">about_Regular_Expressions</span></span>](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md)

[<span data-ttu-id="a8007-345">Get-Alias</span><span class="sxs-lookup"><span data-stu-id="a8007-345">Get-Alias</span></span>](Get-Alias.md)

[<span data-ttu-id="a8007-346">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="a8007-346">Get-ChildItem</span></span>](../Microsoft.PowerShell.Management/Get-ChildItem.md)

[<span data-ttu-id="a8007-347">Get-Command</span><span class="sxs-lookup"><span data-stu-id="a8007-347">Get-Command</span></span>](../Microsoft.PowerShell.Core/Get-Command.md)

[<span data-ttu-id="a8007-348">Get-Member</span><span class="sxs-lookup"><span data-stu-id="a8007-348">Get-Member</span></span>](Get-Member.md)

[<span data-ttu-id="a8007-349">Get-WinEvent</span><span class="sxs-lookup"><span data-stu-id="a8007-349">Get-WinEvent</span></span>](../Microsoft.PowerShell.Diagnostics/Get-WinEvent.md)

[<span data-ttu-id="a8007-350">Out-File</span><span class="sxs-lookup"><span data-stu-id="a8007-350">Out-File</span></span>](Out-File.md)
