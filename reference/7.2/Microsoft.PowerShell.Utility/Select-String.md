---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/select-string?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Select-String
ms.openlocfilehash: 339afab9c817b54a79e2f1b33b7021ecb4fe6a6e
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603059"
---
# <span data-ttu-id="e8487-102">Select-String</span><span class="sxs-lookup"><span data-stu-id="e8487-102">Select-String</span></span>

## <span data-ttu-id="e8487-103">개요</span><span class="sxs-lookup"><span data-stu-id="e8487-103">SYNOPSIS</span></span>
<span data-ttu-id="e8487-104">문자열 및 파일에서 텍스트를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-104">Finds text in strings and files.</span></span>

## <span data-ttu-id="e8487-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e8487-105">SYNTAX</span></span>

### <span data-ttu-id="e8487-106">File (기본값)</span><span class="sxs-lookup"><span data-stu-id="e8487-106">File (Default)</span></span>

```
Select-String [-Culture <String>] [-Pattern] <String[]> [-Path] <String[]> [-SimpleMatch]
 [-CaseSensitive] [-Quiet] [-List] [-NoEmphasis] [-Include <String[]>] [-Exclude <String[]>]
 [-NotMatch] [-AllMatches] [-Encoding <Encoding>] [-Context <Int32[]>] [<CommonParameters>]
```

### <span data-ttu-id="e8487-107">ObjectRaw</span><span class="sxs-lookup"><span data-stu-id="e8487-107">ObjectRaw</span></span>

```
Select-String [-Culture <String>] -InputObject <PSObject> [-Pattern] <String[]> -Raw [-SimpleMatch]
 [-CaseSensitive] [-List] [-NoEmphasis] [-Include <String[]>] [-Exclude <String[]>] [-NotMatch]
 [-AllMatches] [-Encoding <Encoding>] [-Context <Int32[]>] [<CommonParameters>]
```

### <span data-ttu-id="e8487-108">Object</span><span class="sxs-lookup"><span data-stu-id="e8487-108">Object</span></span>

```
Select-String [-Culture <String>] -InputObject <PSObject> [-Pattern] <String[]> [-SimpleMatch]
 [-CaseSensitive] [-Quiet] [-List] [-NoEmphasis] [-Include <String[]>] [-Exclude <String[]>]
 [-NotMatch] [-AllMatches] [-Encoding <Encoding>] [-Context <Int32[]>] [<CommonParameters>]
```

### <span data-ttu-id="e8487-109">FileRaw</span><span class="sxs-lookup"><span data-stu-id="e8487-109">FileRaw</span></span>

```
Select-String [-Culture <String>] [-Pattern] <String[]> [-Path] <String[]> -Raw [-SimpleMatch]
 [-CaseSensitive] [-List] [-NoEmphasis] [-Include <String[]>] [-Exclude <String[]>] [-NotMatch]
 [-AllMatches] [-Encoding <Encoding>] [-Context <Int32[]>] [<CommonParameters>]
```

### <span data-ttu-id="e8487-110">LiteralFileRaw</span><span class="sxs-lookup"><span data-stu-id="e8487-110">LiteralFileRaw</span></span>

```
Select-String [-Culture <String>] [-Pattern] <String[]> -LiteralPath <String[]> -Raw [-SimpleMatch]
 [-CaseSensitive] [-List] [-NoEmphasis] [-Include <String[]>] [-Exclude <String[]>] [-NotMatch]
 [-AllMatches] [-Encoding <Encoding>] [-Context <Int32[]>] [<CommonParameters>]
```

### <span data-ttu-id="e8487-111">LiteralFile</span><span class="sxs-lookup"><span data-stu-id="e8487-111">LiteralFile</span></span>

```
Select-String [-Culture <String>] [-Pattern] <String[]> -LiteralPath <String[]> [-SimpleMatch]
 [-CaseSensitive] [-Quiet] [-List] [-NoEmphasis] [-Include <String[]>] [-Exclude <String[]>]
 [-NotMatch] [-AllMatches] [-Encoding <Encoding>] [-Context <Int32[]>] [<CommonParameters>]
```

## <span data-ttu-id="e8487-112">설명</span><span class="sxs-lookup"><span data-stu-id="e8487-112">DESCRIPTION</span></span>

<span data-ttu-id="e8487-113">`Select-String`Cmdlet은 입력 문자열 및 파일에서 텍스트 및 텍스트 패턴을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-113">The `Select-String` cmdlet searches for text and text patterns in input strings and files.</span></span> <span data-ttu-id="e8487-114">`Select-String`UNIX의 경우 또는 Windows  에서 **findstr.exe** 와 비슷하게를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-114">You can use `Select-String` similar to **grep** in UNIX or **findstr.exe** in Windows.</span></span>

<span data-ttu-id="e8487-115">`Select-String` 는 텍스트 줄을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-115">`Select-String` is based on lines of text.</span></span> <span data-ttu-id="e8487-116">기본적으로 `Select-String` 는 각 줄에서 첫 번째 일치 항목을 찾은 다음 일치 하는 항목을 포함 하는 줄에 파일 이름, 줄 번호 및 모든 텍스트를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-116">By default, `Select-String` finds the first match in each line and, for each match, it displays the file name, line number, and all text in the line containing the match.</span></span> <span data-ttu-id="e8487-117">을 (를 `Select-String` ) 지정 하 여 줄 당 여러 개의 일치 항목을 찾거나, 일치 항목 앞뒤 텍스트를 표시 하거나, 일치 하는 항목이 있는지 여부를 나타내는 부울 값 (True 또는 False)을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-117">You can direct `Select-String` to find multiple matches per line, display text before and after the match, or display a Boolean value (True or False) that indicates whether a match is found.</span></span>

<span data-ttu-id="e8487-118">`Select-String` 정규식 일치를 사용 하지만 지정 된 텍스트에 대 한 입력을 검색 하는 일치를 수행할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-118">`Select-String` uses regular expression matching, but it can also perform a match that searches the input for the text that you specify.</span></span>

<span data-ttu-id="e8487-119">`Select-String` 각 입력 파일의 첫 번째 일치 항목 뒤에 나오는 모든 텍스트 일치 항목을 표시 하거나 중지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-119">`Select-String` can display all the text matches or stop after the first match in each input file.</span></span>
<span data-ttu-id="e8487-120">`Select-String` 지정 된 패턴과 일치 하지 않는 모든 텍스트를 표시 하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-120">`Select-String` can be used to display all text that doesn't match the specified pattern.</span></span>

<span data-ttu-id="e8487-121">`Select-String`유니코드 텍스트 파일을 검색 하는 경우와 같이 특정 문자 인코딩을 필요로 하도록 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-121">You can also specify that `Select-String` should expect a particular character encoding, such as when you're searching files of Unicode text.</span></span> <span data-ttu-id="e8487-122">`Select-String` 는 BOM (바이트 순서 표시)을 사용 하 여 파일의 인코딩 형식을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-122">`Select-String` uses the byte-order-mark (BOM) to detect the encoding format of the file.</span></span> <span data-ttu-id="e8487-123">파일에 BOM이 없으면 인코딩이 UTF8 이라고 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-123">If the file has no BOM, it assumes the encoding is UTF8.</span></span>

## <span data-ttu-id="e8487-124">예제</span><span class="sxs-lookup"><span data-stu-id="e8487-124">EXAMPLES</span></span>

### <span data-ttu-id="e8487-125">예 1: 대/소문자를 구분 하는 일치 찾기</span><span class="sxs-lookup"><span data-stu-id="e8487-125">Example 1: Find a case-sensitive match</span></span>

<span data-ttu-id="e8487-126">이 예에서는 파이프라인을 통해 cmdlet에 전송 된 텍스트와 대/소문자를 구분 하는 일치를 수행 합니다 `Select-String` .</span><span class="sxs-lookup"><span data-stu-id="e8487-126">This example does a case-sensitive match of the text that was sent down the pipeline to the `Select-String` cmdlet.</span></span>

```powershell
'Hello', 'HELLO' | Select-String -Pattern 'HELLO' -CaseSensitive -SimpleMatch
```

<span data-ttu-id="e8487-127">텍스트 문자열 **Hello** 및 **hello** 는 파이프라인에서 cmdlet으로 전송 됩니다 `Select-String` .</span><span class="sxs-lookup"><span data-stu-id="e8487-127">The text strings **Hello** and **HELLO** are sent down the pipeline to the `Select-String` cmdlet.</span></span>
<span data-ttu-id="e8487-128">`Select-String`**Pattern** 매개 변수를 사용 하 여 **HELLO** 를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-128">`Select-String` uses the **Pattern** parameter to specify **HELLO**.</span></span> <span data-ttu-id="e8487-129">**CaseSensitive** 매개 변수는 사례가 대문자 패턴만 일치 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-129">The **CaseSensitive** parameter specifies that the case must match only the upper-case pattern.</span></span> <span data-ttu-id="e8487-130">**SimpleMatch** 은 선택적 매개 변수 이며 패턴의 문자열이 정규식으로 해석 되지 않도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-130">**SimpleMatch** is an optional parameter and specifies that the string in the pattern isn't interpreted as a regular expression.</span></span>
<span data-ttu-id="e8487-131">`Select-String` PowerShell 콘솔에 **HELLO** 를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-131">`Select-String` displays **HELLO** in the PowerShell console.</span></span>

### <span data-ttu-id="e8487-132">예제 2: 텍스트 파일에서 일치 항목 찾기</span><span class="sxs-lookup"><span data-stu-id="e8487-132">Example 2: Find matches in text files</span></span>

<span data-ttu-id="e8487-133">이 명령은 `.txt` 현재 디렉터리에 있는 파일 이름 확장명을 가진 모든 파일을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-133">This command searches all files with the `.txt` file name extension in the current directory.</span></span> <span data-ttu-id="e8487-134">출력은 지정 된 문자열을 포함 하는 해당 파일의 줄을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-134">The output displays the lines in those files that include the specified string.</span></span>

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

<span data-ttu-id="e8487-135">이 예제에서는 `Get-Alias` 및를 `Get-Command` cmdlet과 함께 사용 `Out-File` 하 여 현재 디렉터리에 두 개의 텍스트 파일 **Alias.txt** 및 **Command.txt** 를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-135">In this example, `Get-Alias` and `Get-Command` are used with the `Out-File` cmdlet to create two text files in the current directory, **Alias.txt** and **Command.txt**.</span></span>

<span data-ttu-id="e8487-136">`Select-String` 는 **Path** 매개 변수를 별표 ( `*` ) 와일드 카드와 함께 사용 하 여 현재 디렉터리에서 파일 이름 확장명을 가진 모든 파일을 검색 `.txt` 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-136">`Select-String` uses the **Path** parameter with the asterisk (`*`) wildcard to search all files in the current directory with the file name extension `.txt`.</span></span> <span data-ttu-id="e8487-137">**Pattern** 매개 변수는 **Get-** 과 일치 하는 텍스트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-137">The **Pattern** parameter specifies the text to match **Get-**.</span></span> <span data-ttu-id="e8487-138">`Select-String` PowerShell 콘솔에 출력을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-138">`Select-String` displays the output in the PowerShell console.</span></span> <span data-ttu-id="e8487-139">파일 이름과 줄 번호는 **패턴** 매개 변수와 일치 하는 항목을 포함 하는 각 내용의 줄 앞에 옵니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-139">The file name and line number precede each line of content that contains a match for the **Pattern** parameter.</span></span>

### <span data-ttu-id="e8487-140">예제 3: 패턴 일치 찾기</span><span class="sxs-lookup"><span data-stu-id="e8487-140">Example 3: Find a pattern match</span></span>

<span data-ttu-id="e8487-141">이 예제에서는 지정 된 패턴과 일치 하는 항목을 찾기 위해 여러 파일을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-141">In this example, multiple files are searched to find matches for the specified pattern.</span></span> <span data-ttu-id="e8487-142">패턴은 정규식 수량자를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-142">The pattern uses a regular expression quantifier.</span></span> <span data-ttu-id="e8487-143">자세한 내용은 [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/About_Regular_Expressions.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e8487-143">For more information, see [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/About_Regular_Expressions.md).</span></span>

```powershell
Select-String -Path "$PSHOME\en-US\*.txt" -Pattern '\?'
```

```Output
C:\Program Files\PowerShell\6\en-US\default.help.txt:27:    beginning at https://go.microsoft.com/fwlink/?LinkID=108518.
C:\Program Files\PowerShell\6\en-US\default.help.txt:50:    or go to: https://go.microsoft.com/fwlink/?LinkID=210614
```

<span data-ttu-id="e8487-144">`Select-String`Cmdlet은 **경로** 와 **패턴** 의 두 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-144">The `Select-String` cmdlet uses two parameters, **Path** and **Pattern**.</span></span> <span data-ttu-id="e8487-145">**Path** 매개 변수는 `$PSHOME` PowerShell 디렉터리를 지정 하는 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-145">The **Path** parameter uses the variable `$PSHOME` that specifies the PowerShell directory.</span></span> <span data-ttu-id="e8487-146">경로의 나머지 부분에는 **en-us** 하위 디렉터리가 포함 되 고 디렉터리의 각 파일을 지정 합니다 `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="e8487-146">The remainder of the path includes the subdirectory **en-US** and specifies each `*.txt` file in the directory.</span></span> <span data-ttu-id="e8487-147">**패턴** 매개 변수는 각 파일에서 물음표 ()와 일치 하도록 지정 합니다 `?` .</span><span class="sxs-lookup"><span data-stu-id="e8487-147">The **Pattern** parameter specifies to match a question mark (`?`) in each file.</span></span> <span data-ttu-id="e8487-148">백슬래시 ( `\` )는 이스케이프 문자로 사용 되며 물음표 ( `?` )는 정규식 수량자 이므로 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-148">A backslash (`\`) is used as an escape character and is necessary because the question mark (`?`) is a regular expression quantifier.</span></span> <span data-ttu-id="e8487-149">`Select-String` PowerShell 콘솔에 출력을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-149">`Select-String` displays the output in the PowerShell console.</span></span> <span data-ttu-id="e8487-150">파일 이름과 줄 번호는 **패턴** 매개 변수와 일치 하는 항목을 포함 하는 각 내용의 줄 앞에 옵니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-150">The file name and line number precede each line of content that contains a match for the **Pattern** parameter.</span></span>

### <span data-ttu-id="e8487-151">예제 4: 함수에서 Select-String 사용</span><span class="sxs-lookup"><span data-stu-id="e8487-151">Example 4: Use Select-String in a function</span></span>

<span data-ttu-id="e8487-152">이 예에서는 PowerShell 도움말 파일에서 패턴을 검색 하는 함수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-152">This example creates a function to search for a pattern in the PowerShell help files.</span></span> <span data-ttu-id="e8487-153">이 예에서는 함수가 PowerShell 세션에만 존재 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-153">For this example, the function only exists in the PowerShell session.</span></span> <span data-ttu-id="e8487-154">PowerShell 세션이 닫히면 함수는 삭제 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-154">When the PowerShell session is closed, the function is deleted.</span></span> <span data-ttu-id="e8487-155">자세한 내용은 [about_Functions](../Microsoft.PowerShell.Core/About/about_Functions.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e8487-155">For more information, see [about_Functions](../Microsoft.PowerShell.Core/About/about_Functions.md).</span></span>

```
PS> Function Search-Help
>> {
>> $PSHelp = "$PSHOME\en-US\*.txt"
>> Select-String -Path $PSHelp -Pattern 'About_'
>> }
PS>

PS> Search-Help

C:\Program Files\PowerShell\6\en-US\default.help.txt:67:    The titles of conceptual topics begin with "About_".
C:\Program Files\PowerShell\6\en-US\default.help.txt:70:    Get-Help About_<topic-name>
C:\Program Files\PowerShell\6\en-US\default.help.txt:93:    Get-Help About_Modules : Displays help about PowerShell modules.
C:\Program Files\PowerShell\6\en-US\default.help.txt:97:    about_Updatable_Help
```

<span data-ttu-id="e8487-156">함수가 PowerShell 명령줄에 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-156">The function is created on the PowerShell command line.</span></span> <span data-ttu-id="e8487-157">이 `Function` 명령은 **Search Help** 이름을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-157">The `Function` command uses the name **Search-Help**.</span></span> <span data-ttu-id="e8487-158">**Enter** 키를 눌러 함수에 문을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-158">Press **Enter** to begin adding statements to the function.</span></span> <span data-ttu-id="e8487-159">프롬프트에서 `>>` 각 문을 추가 하 고 예제와 같이 **enter** 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-159">From the `>>` prompt, add each statement and press **Enter** as shown in the example.</span></span> <span data-ttu-id="e8487-160">닫는 대괄호가 추가 되 면 PowerShell 프롬프트로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-160">After the closing bracket is added, you're returned to a PowerShell prompt.</span></span>

<span data-ttu-id="e8487-161">함수는 두 개의 명령을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-161">The function contains two commands.</span></span> <span data-ttu-id="e8487-162">`$PSHelp`변수는 PowerShell 도움말 파일에 대 한 경로를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-162">The `$PSHelp` variable stores the path to the PowerShell help files.</span></span> <span data-ttu-id="e8487-163">`$PSHOME` 는 디렉터리의 각 파일을 지정 하는 디렉터리 **en-us** 를 사용 하는 PowerShell 설치 디렉터리입니다 `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="e8487-163">`$PSHOME` is the PowerShell installation directory with the subdirectory **en-US** that specifies each `*.txt` file in the directory.</span></span>

<span data-ttu-id="e8487-164">`Select-String`함수의 명령은 **Path** 및 **Pattern** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-164">The `Select-String` command in the function uses the **Path** and **Pattern** parameters.</span></span> <span data-ttu-id="e8487-165">**Path** 매개 변수는 변수를 사용 하 여 `$PSHelp` 경로를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-165">The **Path** parameter uses the `$PSHelp` variable to get the path.</span></span> <span data-ttu-id="e8487-166">**패턴** 매개 변수는 **About_** 문자열을 검색 조건으로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-166">The **Pattern** parameter uses the string **About_** as the search criteria.</span></span>

<span data-ttu-id="e8487-167">함수를 실행 하려면를 입력 `Search-Help` 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-167">To run the function, type `Search-Help`.</span></span> <span data-ttu-id="e8487-168">함수의 `Select-String` 명령은 PowerShell 콘솔에 출력을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-168">The function's `Select-String` command displays the output in the PowerShell console.</span></span>

### <span data-ttu-id="e8487-169">예 5: Windows 이벤트 로그에서 문자열 검색</span><span class="sxs-lookup"><span data-stu-id="e8487-169">Example 5: Search for a string in a Windows event log</span></span>

<span data-ttu-id="e8487-170">이 예에서는 Windows 이벤트 로그에서 문자열을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-170">This example searches for a string in a Windows event log.</span></span> <span data-ttu-id="e8487-171">변수는 `$_` 파이프라인의 현재 개체를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-171">The variable `$_` represents the current object in the pipeline.</span></span> <span data-ttu-id="e8487-172">자세한 내용은 [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e8487-172">For more information, see [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md).</span></span>

```powershell
$Events = Get-WinEvent -LogName Application -MaxEvents 50
$Events | Select-String -InputObject {$_.message} -Pattern 'Failed'
```

<span data-ttu-id="e8487-173">`Get-WinEvent`Cmdlet은 **LogName** 매개 변수를 사용 하 여 응용 프로그램 로그를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-173">The `Get-WinEvent` cmdlet uses the **LogName** parameter to specify the Application log.</span></span> <span data-ttu-id="e8487-174">**Maxevents** 매개 변수는 로그에서 50의 최신 이벤트를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-174">The **MaxEvents** parameter gets the 50 most recent events from the log.</span></span> <span data-ttu-id="e8487-175">로그 콘텐츠는 라는 변수에 저장 됩니다 `$Events` .</span><span class="sxs-lookup"><span data-stu-id="e8487-175">The log content is stored in the variable named `$Events`.</span></span>

<span data-ttu-id="e8487-176">`$Events`변수가 파이프라인에서 cmdlet으로 전송 됩니다 `Select-String` .</span><span class="sxs-lookup"><span data-stu-id="e8487-176">The `$Events` variable is sent down the pipeline to the `Select-String` cmdlet.</span></span> <span data-ttu-id="e8487-177">`Select-String`**InputObject** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-177">`Select-String` uses the **InputObject** parameter.</span></span> <span data-ttu-id="e8487-178">`$_`변수는 현재 개체를 나타내고 `message` 는 이벤트의 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-178">The `$_` variable represents the current object and `message` is a property of the event.</span></span> <span data-ttu-id="e8487-179">**패턴** 매개 변수는 **실패** 문자열을,에서 일치 하는 항목을 검색 합니다 `$_.message` .</span><span class="sxs-lookup"><span data-stu-id="e8487-179">The **Pattern** parameter species the string **Failed** and searches for matches in `$_.message`.</span></span> <span data-ttu-id="e8487-180">`Select-String` PowerShell 콘솔에 출력을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-180">`Select-String` displays the output in the PowerShell console.</span></span>

### <span data-ttu-id="e8487-181">예제 6: 하위 디렉터리에서 문자열 찾기</span><span class="sxs-lookup"><span data-stu-id="e8487-181">Example 6: Find a string in subdirectories</span></span>

<span data-ttu-id="e8487-182">이 예에서는 디렉터리와 모든 하위 디렉터리에서 특정 텍스트 문자열을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-182">This example searches a directory and all of its subdirectories for a specific text string.</span></span>

```powershell
Get-ChildItem -Path C:\Windows\System32\*.txt -Recurse | Select-String -Pattern 'Microsoft' -CaseSensitive
```

<span data-ttu-id="e8487-183">`Get-ChildItem`**Path** 매개 변수를 사용 하 여 **를 \* 지정 합니다.**</span><span class="sxs-lookup"><span data-stu-id="e8487-183">`Get-ChildItem` uses the **Path** parameter to specify **C:\Windows\System32\*.txt**.</span></span> <span data-ttu-id="e8487-184">**재귀** 매개 변수는 하위 디렉터리를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-184">The **Recurse** parameter includes the subdirectories.</span></span> <span data-ttu-id="e8487-185">개체는 파이프라인에서로 전송 됩니다 `Select-String` .</span><span class="sxs-lookup"><span data-stu-id="e8487-185">The objects are sent down the pipeline to `Select-String`.</span></span>

<span data-ttu-id="e8487-186">`Select-String` 는 **Pattern** 매개 변수를 사용 하 고 **Microsoft** 문자열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-186">`Select-String` uses the **Pattern** parameter and specifies the string **Microsoft**.</span></span> <span data-ttu-id="e8487-187">**CaseSensitive** 매개 변수는 문자열의 정확한 대/소문자를 비교 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-187">The **CaseSensitive** parameter is used to match the exact case of the string.</span></span> <span data-ttu-id="e8487-188">`Select-String` PowerShell 콘솔에 출력을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-188">`Select-String` displays the output in the PowerShell console.</span></span>

> [!NOTE]
> <span data-ttu-id="e8487-189">사용 권한에 따라 출력에 **액세스 거부** 메시지가 표시 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-189">Dependent upon your permissions, you might see **Access denied** messages in the output.</span></span>

### <span data-ttu-id="e8487-190">예 7: 패턴과 일치 하지 않는 문자열 찾기</span><span class="sxs-lookup"><span data-stu-id="e8487-190">Example 7: Find strings that do not match a pattern</span></span>

<span data-ttu-id="e8487-191">이 예제에서는 패턴과 일치 하지 않는 데이터 줄을 제외 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-191">This example shows how to exclude lines of data that don't match a pattern.</span></span>

```powershell
Get-Command | Out-File -FilePath .\Command.txt
Select-String -Path .\Command.txt -Pattern 'Get', 'Set'  -NotMatch
```

<span data-ttu-id="e8487-192">Cmdlet은 개체를에 `Get-Command` 파이프라인으로 보내 `Out-File` 현재 디렉터리에 **Command.txt** 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-192">The `Get-Command` cmdlet sends objects down the pipeline to the `Out-File` to create the **Command.txt** file in the current directory.</span></span> <span data-ttu-id="e8487-193">`Select-String`**Path** 매개 변수를 사용 하 여 **Command.txt** 파일을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-193">`Select-String` uses the **Path** parameter to specify the **Command.txt** file.</span></span> <span data-ttu-id="e8487-194">**Pattern** 매개 변수는 **Get** 및 **Set** 을 검색 패턴으로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-194">The **Pattern** parameter specifies **Get** and **Set** as the search pattern.</span></span> <span data-ttu-id="e8487-195">**Notmatch** 매개 변수는 **Get** 및 **Set** 을 결과에서 제외 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-195">The **NotMatch** parameter excludes **Get** and **Set** from the results.</span></span>
<span data-ttu-id="e8487-196">`Select-String`**Get** 또는 **Set** 을 포함 하지 않는 PowerShell 콘솔의 출력을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-196">`Select-String` displays the output in the PowerShell console that doesn't include **Get** or **Set**.</span></span>

### <span data-ttu-id="e8487-197">예 8: 일치 전후 줄 찾기</span><span class="sxs-lookup"><span data-stu-id="e8487-197">Example 8: Find lines before and after a match</span></span>

<span data-ttu-id="e8487-198">이 예제에서는 일치 하는 패턴 앞뒤의 줄을 가져오는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-198">This example shows how to get the lines before and after the matched pattern.</span></span>

```powershell
Get-Command | Out-File -FilePath .\Command.txt
Select-String -Path .\Command.txt -Pattern 'Get-Computer' -Context 2, 3
```

```Output
  Command.txt:986:Cmdlet          Get-CmsMessage           6.1.0.0    Microsoft.PowerShell.Security
  Command.txt:987:Cmdlet          Get-Command              6.1.2.0    Microsoft.PowerShell.Core
> Command.txt:988:Cmdlet          Get-ComputerInfo         6.1.0.0    Microsoft.PowerShell.Management
  Command.txt:990:Cmdlet          Get-Content              6.1.0.0    Microsoft.PowerShell.Management
  Command.txt:991:Cmdlet          Get-ControlPanelItem     3.1.0.0    Microsoft.PowerShell.Management
  Command.txt:992:Cmdlet          Get-Credential           6.1.0.0    Microsoft.PowerShell.Security
```

<span data-ttu-id="e8487-199">Cmdlet은 개체를에 `Get-Command` 파이프라인으로 보내 `Out-File` 현재 디렉터리에 **Command.txt** 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-199">The `Get-Command` cmdlet sends objects down the pipeline to the `Out-File` to create the **Command.txt** file in the current directory.</span></span> <span data-ttu-id="e8487-200">`Select-String`**Path** 매개 변수를 사용 하 여 **Command.txt** 파일을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-200">`Select-String` uses the **Path** parameter to specify the **Command.txt** file.</span></span> <span data-ttu-id="e8487-201">**Pattern** 매개 변수는 **가져오기 컴퓨터** 를 검색 패턴으로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-201">The **Pattern** parameter specifies **Get-Computer** as the search pattern.</span></span> <span data-ttu-id="e8487-202">**컨텍스트** 매개 변수는 앞과 뒤에 두 개의 값을 사용 하 고 출력에서 패턴 일치를 꺾쇠 괄호 ( `>` )로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-202">The **Context** parameter uses two values, before and after, and marks pattern matches in the output with an angle bracket (`>`).</span></span> <span data-ttu-id="e8487-203">**Context** 매개 변수는 첫 번째 패턴 일치 앞에 두 줄을 출력 하 고, 마지막 패턴 일치 후에 세 줄을 출력 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-203">The **Context** parameter outputs the two lines before the first pattern match and three lines after the last pattern match.</span></span>

### <span data-ttu-id="e8487-204">예 9: 모든 패턴 일치 찾기</span><span class="sxs-lookup"><span data-stu-id="e8487-204">Example 9: Find all pattern matches</span></span>

<span data-ttu-id="e8487-205">이 예제에서는 **Allmatches** 매개 변수가 텍스트 줄에서 각 패턴 일치 항목을 찾는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-205">This example shows how the **AllMatches** parameter finds each pattern match in a line of text.</span></span> <span data-ttu-id="e8487-206">기본적으로는 `Select-String` 텍스트 줄에서 첫 번째로 나타나는 패턴을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-206">By default, `Select-String` only finds the first occurrence of a pattern in a line of text.</span></span> <span data-ttu-id="e8487-207">이 예에서는 cmdlet에서 발견 된 개체 속성을 사용 `Get-Member` 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-207">This example uses object properties that are found with the `Get-Member` cmdlet.</span></span>

```
PS> $A = Get-ChildItem -Path "$PSHOME\en-US\*.txt" | Select-String -Pattern 'PowerShell'

PS> $A

C:\Program Files\PowerShell\6\en-US\default.help.txt:3:    PowerShell Help System
C:\Program Files\PowerShell\6\en-US\default.help.txt:6:    Displays help about PowerShell cmdlets and concepts.
C:\Program Files\PowerShell\6\en-US\default.help.txt:9:    PowerShell Help describes PowerShell cmdlets

PS> $A.Matches

Groups   : {0}
Success  : True
Name     : 0
Captures : {0}
Index    : 4
Length   : 10
Value    : PowerShell

PS> $A.Matches.Length

8

PS> $B = Get-ChildItem -Path "$PSHOME\en-US\*.txt" | Select-String -Pattern 'PowerShell' -AllMatches

PS> $B.Matches.Length

9
```

<span data-ttu-id="e8487-208">`Get-ChildItem`Cmdlet은 **Path** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-208">The `Get-ChildItem` cmdlet uses the **Path** parameter.</span></span> <span data-ttu-id="e8487-209">**Path** 매개 변수는 `$PSHOME` PowerShell 디렉터리를 지정 하는 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-209">The **Path** parameter uses the variable `$PSHOME` that specifies the PowerShell directory.</span></span> <span data-ttu-id="e8487-210">경로의 나머지 부분에는 **en-us** 하위 디렉터리가 포함 되 고 디렉터리의 각 파일을 지정 합니다 `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="e8487-210">The remainder of the path includes the subdirectory **en-US** and specifies each `*.txt` file in the directory.</span></span> <span data-ttu-id="e8487-211">`Get-ChildItem`개체는 변수에 저장 됩니다 `$A` .</span><span class="sxs-lookup"><span data-stu-id="e8487-211">The `Get-ChildItem` objects are stored in the `$A` variable.</span></span> <span data-ttu-id="e8487-212">`$A`변수가 파이프라인에서 cmdlet으로 전송 됩니다 `Select-String` .</span><span class="sxs-lookup"><span data-stu-id="e8487-212">The `$A` variable is sent down the pipeline to the `Select-String` cmdlet.</span></span> <span data-ttu-id="e8487-213">`Select-String` 는 **Pattern** 매개 변수를 사용 하 여 각 파일에서 문자열 **PowerShell** 을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-213">`Select-String` uses the **Pattern** parameter to search each file for the string **PowerShell**.</span></span>

<span data-ttu-id="e8487-214">PowerShell 명령줄에서 `$A` 변수 내용이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-214">From the PowerShell command line, the `$A` variable contents are displayed.</span></span> <span data-ttu-id="e8487-215">두 번의 문자열 **PowerShell** 이 포함 된 줄이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-215">There's a line that contains two occurrences of the string **PowerShell**.</span></span>

<span data-ttu-id="e8487-216">`$A.Matches`속성은 각 줄에서 처음 발견 되는 패턴 **PowerShell** 을 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-216">The `$A.Matches` property lists the first occurrence of the pattern **PowerShell** on each line.</span></span>

<span data-ttu-id="e8487-217">`$A.Matches.Length`속성은 각 줄에서 처음 발견 되는 패턴 **PowerShell** 수를 계산 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-217">The `$A.Matches.Length` property counts the first occurrence of the pattern **PowerShell** on each line.</span></span>

<span data-ttu-id="e8487-218">`$B`변수는 동일한 `Get-ChildItem` 및 `Select-String` cmdlet을 사용 하지만 **allmatches** 매개 변수를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-218">The `$B` variable uses the same `Get-ChildItem` and `Select-String` cmdlets, but adds the **AllMatches** parameter.</span></span> <span data-ttu-id="e8487-219">**Allmatches** 는 각 줄에서 각 패턴 **PowerShell** 의 발생을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-219">**AllMatches** finds each occurrence of the pattern **PowerShell** on each line.</span></span> <span data-ttu-id="e8487-220">및 변수에 저장 된 개체 `$A` 는 `$B` 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-220">The objects stored in the `$A` and `$B` variables are identical.</span></span>

<span data-ttu-id="e8487-221">`$B.Matches.Length`각 줄에 대해 패턴 **PowerShell** 의 모든 발생이 계산 되기 때문에 속성은 늘어납니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-221">The `$B.Matches.Length` property increases because for each line, every occurrence of the pattern **PowerShell** is counted.</span></span>

## <span data-ttu-id="e8487-222">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e8487-222">PARAMETERS</span></span>

### <span data-ttu-id="e8487-223">-AllMatches</span><span class="sxs-lookup"><span data-stu-id="e8487-223">-AllMatches</span></span>

<span data-ttu-id="e8487-224">Cmdlet이 각 텍스트 줄에서 일치 하는 항목을 두 개 이상 검색 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-224">Indicates that the cmdlet searches for more than one match in each line of text.</span></span> <span data-ttu-id="e8487-225">이 매개 변수를 사용 하지 않으면는 `Select-String` 각 텍스트 줄에서 첫 번째 일치 항목만 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-225">Without this parameter, `Select-String` finds only the first match in each line of text.</span></span>

<span data-ttu-id="e8487-226">가 `Select-String` 텍스트 줄에서 일치 하는 항목을 여러 개 찾은 경우에도 해당 줄에 대해 하나의 **matchinfo** 개체만 가져오지만 개체의 **matches** 속성은 모든 일치 항목을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-226">When `Select-String` finds more than one match in a line of text, it still emits only one **MatchInfo** object for the line, but the **Matches** property of the object contains all the matches.</span></span>

> [!NOTE]
> <span data-ttu-id="e8487-227">이 매개 변수는 **SimpleMatch** 매개 변수와 함께 사용 하면 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-227">This parameter is ignored when used in combination with the **SimpleMatch** parameter.</span></span> <span data-ttu-id="e8487-228">모든 일치 항목을 반환 하려는 경우 검색 하는 패턴에 정규식 문자가 포함 되어 있으면 **SimpleMatch** 를 사용 하는 대신 해당 문자를 이스케이프 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-228">If you wish to return all matches and the pattern that you are searching for contains regular expression characters, you must escape those characters rather than using **SimpleMatch**.</span></span> <span data-ttu-id="e8487-229">정규식 이스케이프에 대 한 자세한 내용은 [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e8487-229">See [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md) for more information about escaping regular expressions.</span></span>

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

### <span data-ttu-id="e8487-230">-CaseSensitive</span><span class="sxs-lookup"><span data-stu-id="e8487-230">-CaseSensitive</span></span>

<span data-ttu-id="e8487-231">Cmdlet이 대/소문자를 구분 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-231">Indicates that the cmdlet matches are case-sensitive.</span></span> <span data-ttu-id="e8487-232">기본적으로 일치는 대/소문자를 구분 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-232">By default, matches aren't case-sensitive.</span></span>

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

### <span data-ttu-id="e8487-233">-Context</span><span class="sxs-lookup"><span data-stu-id="e8487-233">-Context</span></span>

<span data-ttu-id="e8487-234">패턴과 일치 하는 줄의 앞과 뒤에 지정 된 수의 줄을 캡처합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-234">Captures the specified number of lines before and after the line that matches the pattern.</span></span>

<span data-ttu-id="e8487-235">이 매개 변수 값으로 하나의 숫자를 입력하면 해당 숫자가 일치하는 항목이 있는 줄 앞뒤로 캡처할 줄 수를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-235">If you enter one number as the value of this parameter, that number determines the number of lines captured before and after the match.</span></span> <span data-ttu-id="e8487-236">값으로 숫자를 두 개 입력하면 첫 번째 숫자는 일치 항목 앞의 줄 수를 결정하고 두 번째 숫자는 일치 항목 뒤의 줄 수를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-236">If you enter two numbers as the value, the first number determines the number of lines before the match and the second number determines the number of lines after the match.</span></span> <span data-ttu-id="e8487-237">예를 들어 `-Context 2,3`입니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-237">For example, `-Context 2,3`.</span></span>

<span data-ttu-id="e8487-238">기본 표시에서 일치 하는 줄이 `>` 표시의 첫 번째 열에 오른쪽 꺾쇠 괄호 () (ASCII 62)로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-238">In the default display, lines with a match are indicated by a right angle bracket (`>`) (ASCII 62) in the first column of the display.</span></span> <span data-ttu-id="e8487-239">표시되지 않은 줄은 컨텍스트입니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-239">Unmarked lines are the context.</span></span>

<span data-ttu-id="e8487-240">**컨텍스트** 매개 변수는에 의해 생성 된 개체의 수를 변경 하지 않습니다 `Select-String` .</span><span class="sxs-lookup"><span data-stu-id="e8487-240">The **Context** parameter doesn't change the number of objects generated by `Select-String`.</span></span>
<span data-ttu-id="e8487-241">`Select-String` 각 일치 항목에 대해 하나의 [Matchinfo](/dotnet/api/microsoft.powershell.commands.matchinfo) 개체를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-241">`Select-String` generates one [MatchInfo](/dotnet/api/microsoft.powershell.commands.matchinfo) object for each match.</span></span> <span data-ttu-id="e8487-242">컨텍스트는 개체의 **컨텍스트** 속성에 문자열 배열로 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-242">The context is stored as an array of strings in the **Context** property of the object.</span></span>

<span data-ttu-id="e8487-243">`Select-String`명령의 출력이 파이프라인에서 다른 명령으로 전송 되 면 `Select-String` 수신 명령은 일치 하는 줄의 텍스트만 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-243">When the output of a `Select-String` command is sent down the pipeline to another `Select-String` command, the receiving command searches only the text in the matched line.</span></span> <span data-ttu-id="e8487-244">일치 하는 줄은 컨텍스트 줄의 텍스트가 아니라 **Matchinfo** 개체의 **line** 속성 값입니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-244">The matched line is the value of the **Line** property of the **MatchInfo** object, not the text in the context lines.</span></span> <span data-ttu-id="e8487-245">결과적으로 **컨텍스트** 매개 변수는 수신 명령에서 유효 하지 않습니다 `Select-String` .</span><span class="sxs-lookup"><span data-stu-id="e8487-245">As a result, the **Context** parameter isn't valid on the receiving `Select-String` command.</span></span>

<span data-ttu-id="e8487-246">컨텍스트에 일치 항목이 포함 된 경우 각 일치 항목에 대 한 **Matchinfo** 개체에는 모든 컨텍스트 줄이 포함 되지만 겹치는 줄은 표시에 한 번만 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-246">When the context includes a match, the **MatchInfo** object for each match includes all the context lines, but the overlapping lines appear only once in the display.</span></span>

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

### <span data-ttu-id="e8487-247">-문화권</span><span class="sxs-lookup"><span data-stu-id="e8487-247">-Culture</span></span>

<span data-ttu-id="e8487-248">지정 된 패턴과 일치 하는 문화권 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-248">Specifies a culture name to match the specified pattern.</span></span> <span data-ttu-id="e8487-249">**Culture** 매개 변수는 **SimpleMatch** 매개 변수와 함께 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-249">The **Culture** parameter must be used with the **SimpleMatch** parameter.</span></span> <span data-ttu-id="e8487-250">기본 동작은 현재 PowerShell runspace (세션)의 문화권을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-250">The default behavior uses the culture of the current PowerShell runspace (session).</span></span>

<span data-ttu-id="e8487-251">지원 되는 모든 문화권 목록을 가져오려면 command를 사용 `Get-Culture -ListAvailable` 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-251">To get a list of all supported cultures, use `Get-Culture -ListAvailable` command.</span></span>

<span data-ttu-id="e8487-252">또한이 매개 변수는 다음 인수를 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-252">In addition, this parameter accepts the following arguments:</span></span>

- <span data-ttu-id="e8487-253">기본값은 CurrentCulture입니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-253">CurrentCulture, that is default;</span></span>
- <span data-ttu-id="e8487-254">비 언어적 이진 비교 인 서 수입니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-254">Ordinal, that is non-linguistic binary comparison;</span></span>
- <span data-ttu-id="e8487-255">고정 이며이는 문화권 독립적 비교입니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-255">Invariant, that is culture independent comparison.</span></span>

<span data-ttu-id="e8487-256">`Select-String -Culture Ordinal -CaseSensitive -SimpleMatch`명령을 사용 하 여 가장 빠른 이진 비교를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-256">With `Select-String -Culture Ordinal -CaseSensitive -SimpleMatch` command you gets fastest binary comparison.</span></span>

<span data-ttu-id="e8487-257">**Culture** 매개 변수는 탭 완성 기능을 사용 하 여 사용 가능한 문화권을 지정 하는 인수 목록을 스크롤합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-257">The **Culture** parameter uses tab completion to scroll through the list of arguments that specify the available cultures.</span></span> <span data-ttu-id="e8487-258">사용 가능한 모든 인수를 나열 하려면 다음 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-258">To list all available arguments, use the following command:</span></span>

`(Get-Command Select-String).Parameters.Culture.Attributes.ValidValues`

<span data-ttu-id="e8487-259">.NET CultureInfo.Name 속성에 대 한 자세한 내용은 [CultureInfo.Name](/dotnet/api//system.globalization.cultureinfo.name)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e8487-259">For more information about .NET CultureInfo.Name property, see [CultureInfo.Name](/dotnet/api//system.globalization.cultureinfo.name).</span></span>

<span data-ttu-id="e8487-260">**Culture** 매개 변수는 PowerShell 7에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-260">The **Culture** parameter was introduced in PowerShell 7.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Culture of the current PowerShell session
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e8487-261">-Encoding</span><span class="sxs-lookup"><span data-stu-id="e8487-261">-Encoding</span></span>

<span data-ttu-id="e8487-262">대상 파일의 인코딩 유형을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-262">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="e8487-263">기본값은 `utf8NoBOM`입니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-263">The default value is `utf8NoBOM`.</span></span>

<span data-ttu-id="e8487-264">이 매개 변수에 허용 되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-264">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="e8487-265">`ascii`: ASCII (7 비트) 문자 집합에 대 한 인코딩을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-265">`ascii`: Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="e8487-266">`bigendianunicode`: 빅 endian 바이트 순서를 사용 하 여 UTF-16 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-266">`bigendianunicode`: Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="e8487-267">`bigendianutf32`: 빅 endian 바이트 순서를 사용 하 여 u t f-32 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-267">`bigendianutf32`: Encodes in UTF-32 format using the big-endian byte order.</span></span>
- <span data-ttu-id="e8487-268">`oem`: MS-DOS 및 콘솔 프로그램에 기본 인코딩을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-268">`oem`: Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="e8487-269">`unicode`: 작은 endian 바이트 순서를 사용 하 여 UTF-16 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-269">`unicode`: Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="e8487-270">`utf7`: UTF-7 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-270">`utf7`: Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="e8487-271">`utf8`: UTF-8 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-271">`utf8`: Encodes in UTF-8 format.</span></span>
- <span data-ttu-id="e8487-272">`utf8BOM`: 바이트 순서 표시 (BOM)를 사용 하 여 UTF-8 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-272">`utf8BOM`: Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="e8487-273">`utf8NoBOM`: BOM (바이트 순서 표시) 없이 UTF-8 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-273">`utf8NoBOM`: Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="e8487-274">`utf32`: U t f-32 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-274">`utf32`: Encodes in UTF-32 format.</span></span>

<span data-ttu-id="e8487-275">PowerShell 6.2부터 **Encoding** 매개 변수를 사용 하 여 등록 된 코드 페이지의 숫자 id (예: `-Encoding 1251` ) 또는 등록 된 코드 페이지의 문자열 이름을 사용할 수도 있습니다 (예: `-Encoding "windows-1251"` ).</span><span class="sxs-lookup"><span data-stu-id="e8487-275">Beginning with PowerShell 6.2, the **Encoding** parameter also allows numeric IDs of registered code pages (like `-Encoding 1251`) or string names of registered code pages (like `-Encoding "windows-1251"`).</span></span> <span data-ttu-id="e8487-276">자세한 내용은 [인코딩에](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2)대 한 .net 설명서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e8487-276">For more information, see the .NET documentation for [Encoding.CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span></span>

> [!NOTE]
> <span data-ttu-id="e8487-277">**U t f-7** _은 더 이상 사용 하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-277">**UTF-7** _ is no longer recommended to use.</span></span> <span data-ttu-id="e8487-278">PowerShell 7.1에서는 `utf7` _ *Encoding*\* 매개 변수에 대해를 지정 하는 경우 경고가 기록 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-278">In PowerShell 7.1, a warning is written if you specify `utf7` for the _ *Encoding*\* parameter.</span></span>

```yaml
Type: System.Text.Encoding
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, BigEndianUTF32, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: Named
Default value: UTF8NoBOM
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e8487-279">-제외</span><span class="sxs-lookup"><span data-stu-id="e8487-279">-Exclude</span></span>

<span data-ttu-id="e8487-280">지정된 항목을 제외합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-280">Exclude the specified items.</span></span> <span data-ttu-id="e8487-281">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-281">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="e8487-282">경로 요소 또는 패턴 (예:)을 입력 `*.txt` 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-282">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="e8487-283">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-283">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="e8487-284">-포함</span><span class="sxs-lookup"><span data-stu-id="e8487-284">-Include</span></span>

<span data-ttu-id="e8487-285">지정한 항목을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-285">Includes the specified items.</span></span> <span data-ttu-id="e8487-286">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-286">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="e8487-287">경로 요소 또는 패턴 (예:)을 입력 `*.txt` 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-287">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="e8487-288">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-288">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="e8487-289">-InputObject</span><span class="sxs-lookup"><span data-stu-id="e8487-289">-InputObject</span></span>

<span data-ttu-id="e8487-290">검색할 텍스트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-290">Specifies the text to be searched.</span></span> <span data-ttu-id="e8487-291">텍스트가 포함된 변수를 입력하거나 텍스트를 가져오는 명령 또는 식을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="e8487-291">Enter a variable that contains the text, or type a command or expression that gets the text.</span></span>

<span data-ttu-id="e8487-292">**InputObject** 매개 변수를 사용 하는 것은 파이프라인에서로 문자열을 보내는 것과는 다릅니다 `Select-String` .</span><span class="sxs-lookup"><span data-stu-id="e8487-292">Using the **InputObject** parameter isn't the same as sending strings down the pipeline to `Select-String`.</span></span>

<span data-ttu-id="e8487-293">둘 이상의 문자열을 cmdlet에 파이프 하면 `Select-String` 각 문자열에서 지정 된 텍스트를 검색 하 고 검색 텍스트가 포함 된 각 문자열을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-293">When you pipe more than one string to the `Select-String` cmdlet, it searches for the specified text in each string and returns each string that contains the search text.</span></span>

<span data-ttu-id="e8487-294">**InputObject** 매개 변수를 사용 하 여 문자열 컬렉션을 전송 하는 경우는 `Select-String` 컬렉션을 결합 된 단일 문자열로 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-294">When you use the **InputObject** parameter to submit a collection of strings, `Select-String` treats the collection as a single combined string.</span></span> <span data-ttu-id="e8487-295">`Select-String` 문자열에서 검색 텍스트를 찾은 경우 해당 문자열을 하나의 단위로 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-295">`Select-String` returns the strings as a unit if it finds the search text in any string.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: Object, ObjectRaw
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="e8487-296">-목록</span><span class="sxs-lookup"><span data-stu-id="e8487-296">-List</span></span>

<span data-ttu-id="e8487-297">일치 하는 텍스트의 첫 번째 인스턴스만 각 입력 파일에서 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-297">Only the first instance of matching text is returned from each input file.</span></span> <span data-ttu-id="e8487-298">이는 정규식과 일치 하는 내용이 있는 파일 목록을 검색 하는 가장 효율적인 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-298">This is the most efficient way to retrieve a list of files that have contents matching the regular expression.</span></span>

<span data-ttu-id="e8487-299">기본적으로는 `Select-String` 찾은 각 일치 항목에 대해 **matchinfo** 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-299">By default, `Select-String` returns a **MatchInfo** object for each match it finds.</span></span>

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

### <span data-ttu-id="e8487-300">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="e8487-300">-LiteralPath</span></span>

<span data-ttu-id="e8487-301">검색할 파일의 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-301">Specifies the path to the files to be searched.</span></span> <span data-ttu-id="e8487-302">**LiteralPath** 매개 변수의 값은 입력 한 대로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-302">The value of the **LiteralPath** parameter is used exactly as it's typed.</span></span> <span data-ttu-id="e8487-303">어떠한 문자도 와일드카드로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-303">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="e8487-304">이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요.</span><span class="sxs-lookup"><span data-stu-id="e8487-304">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="e8487-305">작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-305">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span> <span data-ttu-id="e8487-306">자세한 내용은 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e8487-306">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralFileRaw, LiteralFile
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="e8487-307">-NoEmphasis</span><span class="sxs-lookup"><span data-stu-id="e8487-307">-NoEmphasis</span></span>

<span data-ttu-id="e8487-308">기본적으로는 `Select-String` **패턴** 매개 변수를 사용 하 여 검색 한 패턴과 일치 하는 문자열을 강조 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-308">By default, `Select-String` highlights the string that matches the pattern you searched for with the **Pattern** parameter.</span></span> <span data-ttu-id="e8487-309">**Noemphasis** 매개 변수는 강조 표시를 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-309">The **NoEmphasis** parameter disables the highlighting.</span></span>

<span data-ttu-id="e8487-310">강조은 PowerShell 배경 및 텍스트 색에 따라 음수 색을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-310">The emphasis uses negative colors based on your PowerShell background and text colors.</span></span> <span data-ttu-id="e8487-311">예를 들어 PowerShell 색이 흰색 텍스트가 있는 검정색 배경 인 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-311">For example, if your PowerShell colors are a black background with white text.</span></span> <span data-ttu-id="e8487-312">강조는 검정색 텍스트가 있는 흰색 배경입니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-312">The emphasis is a white background with black text.</span></span>

<span data-ttu-id="e8487-313">이 매개 변수는 PowerShell 7에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-313">This parameter was introduced in PowerShell 7.</span></span>

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

### <span data-ttu-id="e8487-314">-NotMatch</span><span class="sxs-lookup"><span data-stu-id="e8487-314">-NotMatch</span></span>

<span data-ttu-id="e8487-315">**Notmatch** 매개 변수는 지정 된 패턴과 일치 하지 않는 텍스트를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-315">The **NotMatch** parameter finds text that doesn't match the specified pattern.</span></span>

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

### <span data-ttu-id="e8487-316">-Path</span><span class="sxs-lookup"><span data-stu-id="e8487-316">-Path</span></span>

<span data-ttu-id="e8487-317">검색할 파일의 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-317">Specifies the path to the files to search.</span></span> <span data-ttu-id="e8487-318">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-318">Wildcards are permitted.</span></span> <span data-ttu-id="e8487-319">기본 위치는 로컬 디렉터리입니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-319">The default location is the local directory.</span></span>

<span data-ttu-id="e8487-320">디렉터리의 파일 (예:, 또는)을 지정 `log1.txt` `*.doc` `*.*` 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-320">Specify files in the directory, such as `log1.txt`, `*.doc`, or `*.*`.</span></span> <span data-ttu-id="e8487-321">디렉터리만 지정하면 명령이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-321">If you specify only a directory, the command fails.</span></span>

```yaml
Type: System.String[]
Parameter Sets: File, FileRaw
Aliases:

Required: True
Position: 1
Default value: Local directory
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="e8487-322">-패턴</span><span class="sxs-lookup"><span data-stu-id="e8487-322">-Pattern</span></span>

<span data-ttu-id="e8487-323">각 줄에서 찾을 텍스트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-323">Specifies the text to find on each line.</span></span> <span data-ttu-id="e8487-324">패턴 값은 정규식으로 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-324">The pattern value is treated as a regular expression.</span></span>

<span data-ttu-id="e8487-325">정규식에 대 한 자세한 내용은 [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e8487-325">To learn about regular expressions, see [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md).</span></span>

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

### <span data-ttu-id="e8487-326">-Quiet</span><span class="sxs-lookup"><span data-stu-id="e8487-326">-Quiet</span></span>

<span data-ttu-id="e8487-327">Cmdlet이 **Matchinfo** 개체 대신 부울 값 (True 또는 False)을 반환 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-327">Indicates that the cmdlet returns a Boolean value (True or False), instead of a **MatchInfo** object.</span></span> <span data-ttu-id="e8487-328">패턴을 찾은 경우 값은 True입니다. 그렇지 않으면 False입니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-328">The value is True if the pattern is found; otherwise the value is False.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: File, Object, LiteralFile
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e8487-329">-Raw</span><span class="sxs-lookup"><span data-stu-id="e8487-329">-Raw</span></span>

<span data-ttu-id="e8487-330">Cmdlet이 **Matchinfo** 개체 대신 일치 하는 문자열만 출력 하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-330">Causes the cmdlet to output only the matching strings, rather than **MatchInfo** objects.</span></span> <span data-ttu-id="e8487-331">이것은 Unix **grep** 또는 Windows **findstr.exe** 명령과 가장 유사한 동작의 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-331">This is the results in behavior that's the most similar to the Unix **grep** or Windows **findstr.exe** commands.</span></span>

<span data-ttu-id="e8487-332">이 매개 변수는 PowerShell 7에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-332">This parameter was introduced in PowerShell 7.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ObjectRaw, FileRaw, LiteralFileRaw
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e8487-333">-SimpleMatch</span><span class="sxs-lookup"><span data-stu-id="e8487-333">-SimpleMatch</span></span>

<span data-ttu-id="e8487-334">Cmdlet이 정규식 일치 대신 단순 일치를 사용 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-334">Indicates that the cmdlet uses a simple match rather than a regular expression match.</span></span> <span data-ttu-id="e8487-335">단순 일치에서는 `Select-String` **패턴** 매개 변수에서 텍스트의 입력을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-335">In a simple match, `Select-String` searches the input for the text in the **Pattern** parameter.</span></span> <span data-ttu-id="e8487-336">**패턴** 매개 변수의 값을 정규식 문으로 해석 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-336">It doesn't interpret the value of the **Pattern** parameter as a regular expression statement.</span></span>

<span data-ttu-id="e8487-337">또한 **SimpleMatch** 를 사용 하면 반환 된 **Matchinfo** 개체의 **Matches** 속성이 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-337">Also, when **SimpleMatch** is used, the **Matches** property of the **MatchInfo** object returned is empty.</span></span>

> [!NOTE]
> <span data-ttu-id="e8487-338">**Allmatches** 매개 변수와 함께이 매개 변수를 사용 하는 경우 **allmatches** 는 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-338">When this parameter is used with the **AllMatches** parameter, the **AllMatches** is ignored.</span></span>

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

### <span data-ttu-id="e8487-339">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e8487-339">CommonParameters</span></span>

<span data-ttu-id="e8487-340">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e8487-340">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e8487-341">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e8487-341">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e8487-342">입력</span><span class="sxs-lookup"><span data-stu-id="e8487-342">INPUTS</span></span>

### <span data-ttu-id="e8487-343">System.web. PSObject</span><span class="sxs-lookup"><span data-stu-id="e8487-343">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="e8487-344">**ToString** 메서드가 있는 개체를로 파이프 할 수 있습니다 `Select-String` .</span><span class="sxs-lookup"><span data-stu-id="e8487-344">You can pipe any object that has a **ToString** method to `Select-String`.</span></span>

## <span data-ttu-id="e8487-345">출력</span><span class="sxs-lookup"><span data-stu-id="e8487-345">OUTPUTS</span></span>

### <span data-ttu-id="e8487-346">Microsoft.. MatchInfo, System.string, System.string</span><span class="sxs-lookup"><span data-stu-id="e8487-346">Microsoft.PowerShell.Commands.MatchInfo, System.Boolean, System.String</span></span>

<span data-ttu-id="e8487-347">기본적으로 출력은 찾은 각 일치 항목에 대해 하나의 **Matchinfo** 개체 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-347">By default, the output is a set of **MatchInfo** objects with one for each match found.</span></span> <span data-ttu-id="e8487-348">**Quiet** 매개 변수를 사용 하는 경우 출력은 패턴을 찾을 수 있는지 여부를 나타내는 **부울** 값입니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-348">If you use the **Quiet** parameter, the output is a **Boolean** value indicating whether the pattern was found.</span></span>
<span data-ttu-id="e8487-349">**Raw** 매개 변수를 사용 하는 경우 출력은 패턴과 일치 하는 **문자열** 개체 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-349">If you use the **Raw** parameter, the output is a set of **String** objects that match the pattern.</span></span>

## <span data-ttu-id="e8487-350">참고</span><span class="sxs-lookup"><span data-stu-id="e8487-350">NOTES</span></span>

<span data-ttu-id="e8487-351">`Select-String` UNIX의 **grep** 또는 Windows의 **findstr.exe** 와 유사 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-351">`Select-String` is similar to **grep** in UNIX or **findstr.exe** in Windows.</span></span>

<span data-ttu-id="e8487-352">Cmdlet에 대 한 **sls** 별칭은 `Select-String` PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-352">The **sls** alias for the `Select-String` cmdlet was introduced in PowerShell 3.0.</span></span>

> [!NOTE]
> <span data-ttu-id="e8487-353">[PowerShell 명령에 대해 승인 된 동사](/powershell/scripting/developer/cmdlet/approved-verbs-for-windows-powershell-commands)에 따라 cmdlet에 대 한 공식 별칭 접두사는 `Select-*` 가 `sc` 아니라입니다 `sl` .</span><span class="sxs-lookup"><span data-stu-id="e8487-353">According to [Approved Verbs for PowerShell Commands](/powershell/scripting/developer/cmdlet/approved-verbs-for-windows-powershell-commands), the official alias prefix for `Select-*` cmdlets is `sc`, not `sl`.</span></span> <span data-ttu-id="e8487-354">따라서에 대 한 적절 한 별칭은 `Select-String` `scs` 가 아니라 여야 합니다 `sls` .</span><span class="sxs-lookup"><span data-stu-id="e8487-354">Therefore, the proper alias for `Select-String` should be `scs`, not `sls`.</span></span> <span data-ttu-id="e8487-355">이 규칙의 예외입니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-355">This is an exception to this rule.</span></span>

<span data-ttu-id="e8487-356">을 사용 하려면 `Select-String` **패턴** 매개 변수의 값으로 찾을 텍스트를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-356">To use `Select-String`, type the text that you want to find as the value of the **Pattern** parameter.</span></span> <span data-ttu-id="e8487-357">검색할 텍스트를 지정 하려면 다음 조건을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-357">To specify the text to be searched, use the following criteria:</span></span>

- <span data-ttu-id="e8487-358">따옴표 붙은 문자열에 텍스트를 입력 하 고로 파이프 `Select-String` 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-358">Type the text in a quoted string, and then pipe it to `Select-String`.</span></span>
- <span data-ttu-id="e8487-359">텍스트 문자열을 변수에 저장 한 다음이 변수를 **InputObject** 매개 변수의 값으로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-359">Store a text string in a variable, and then specify the variable as the value of the **InputObject** parameter.</span></span>
- <span data-ttu-id="e8487-360">텍스트를 파일에 저장 하는 경우 **path** 매개 변수를 사용 하 여 파일 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-360">If the text is stored in files, use the **Path** parameter to specify the path to the files.</span></span>

<span data-ttu-id="e8487-361">기본적으로는 `Select-String` **패턴** 매개 변수의 값을 정규식으로 해석 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-361">By default, `Select-String` interprets the value of the **Pattern** parameter as a regular expression.</span></span> <span data-ttu-id="e8487-362">자세한 내용은 [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e8487-362">For more information, see [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md).</span></span> <span data-ttu-id="e8487-363">**SimpleMatch** 매개 변수를 사용 하 여 정규식 일치를 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-363">You can use the **SimpleMatch** parameter to override the regular expression matching.</span></span> <span data-ttu-id="e8487-364">**SimpleMatch** 매개 변수는 입력에서 **Pattern** 매개 변수 값의 인스턴스를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-364">The **SimpleMatch** parameter finds instances of the value of the **Pattern** parameter in the input.</span></span>

<span data-ttu-id="e8487-365">의 기본 출력은 `Select-String` 일치 항목에 대 한 자세한 정보를 포함 하는 **matchinfo** 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-365">The default output of `Select-String` is a **MatchInfo** object, which includes detailed information about the matches.</span></span> <span data-ttu-id="e8487-366">**Matchinfo** 개체에는 **Filename** 및 **Line** 과 같은 속성이 있으므로이 개체의 정보는 파일에서 텍스트를 검색 하는 경우에 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-366">The information in the object is useful when you're searching for text in files, because **MatchInfo** objects have properties such as **Filename** and **Line**.</span></span> <span data-ttu-id="e8487-367">입력이 파일이 아닌 경우이 매개 변수의 값은 **InputStream** 입니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-367">When the input isn't from the file, the value of these parameters is **InputStream**.</span></span>

<span data-ttu-id="e8487-368">**Matchinfo** 개체의 정보가 필요 하지 않은 경우에는 **Quiet** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-368">If you don't need the information in the **MatchInfo** object, use the **Quiet** parameter.</span></span> <span data-ttu-id="e8487-369">**Quiet** 매개 변수는 **matchinfo** 개체 대신 일치 하는 항목이 있는지 여부를 나타내는 부울 값 (True 또는 False)을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-369">The **Quiet** parameter returns a Boolean value (True or False) to indicate whether it found a match, instead of a **MatchInfo** object.</span></span>

<span data-ttu-id="e8487-370">구를 일치 시키는 경우는 `Select-String` 시스템에 대해 설정 된 현재 문화권을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-370">When matching phrases, `Select-String` uses the current culture that is set for the system.</span></span> <span data-ttu-id="e8487-371">현재 문화권을 찾으려면 cmdlet을 사용 합니다 `Get-Culture` .</span><span class="sxs-lookup"><span data-stu-id="e8487-371">To find the current culture, use the `Get-Culture` cmdlet.</span></span>

<span data-ttu-id="e8487-372">**Matchinfo** 개체의 속성을 찾으려면 다음 명령을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8487-372">To find the properties of a **MatchInfo** object, type the following command:</span></span>

`Select-String -Path test.txt -Pattern 'test' | Get-Member | Format-List -Property *`

## <span data-ttu-id="e8487-373">관련 링크</span><span class="sxs-lookup"><span data-stu-id="e8487-373">RELATED LINKS</span></span>

[<span data-ttu-id="e8487-374">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="e8487-374">about_Automatic_Variables</span></span>](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

[<span data-ttu-id="e8487-375">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="e8487-375">about_Comparison_Operators</span></span>](../Microsoft.PowerShell.Core/About/about_Comparison_Operators.md)

[<span data-ttu-id="e8487-376">about_Functions</span><span class="sxs-lookup"><span data-stu-id="e8487-376">about_Functions</span></span>](../Microsoft.PowerShell.Core/About/about_Functions.md)

[<span data-ttu-id="e8487-377">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="e8487-377">about_Quoting_Rules</span></span>](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)

[<span data-ttu-id="e8487-378">about_Regular_Expressions</span><span class="sxs-lookup"><span data-stu-id="e8487-378">about_Regular_Expressions</span></span>](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md)

[<span data-ttu-id="e8487-379">Get-Alias</span><span class="sxs-lookup"><span data-stu-id="e8487-379">Get-Alias</span></span>](Get-Alias.md)

[<span data-ttu-id="e8487-380">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="e8487-380">Get-ChildItem</span></span>](../Microsoft.PowerShell.Management/Get-ChildItem.md)

[<span data-ttu-id="e8487-381">Get-Command</span><span class="sxs-lookup"><span data-stu-id="e8487-381">Get-Command</span></span>](../Microsoft.PowerShell.Core/Get-Command.md)

[<span data-ttu-id="e8487-382">Get-Member</span><span class="sxs-lookup"><span data-stu-id="e8487-382">Get-Member</span></span>](Get-Member.md)

[<span data-ttu-id="e8487-383">Get-WinEvent</span><span class="sxs-lookup"><span data-stu-id="e8487-383">Get-WinEvent</span></span>](../Microsoft.PowerShell.Diagnostics/Get-WinEvent.md)

[<span data-ttu-id="e8487-384">Out-File</span><span class="sxs-lookup"><span data-stu-id="e8487-384">Out-File</span></span>](Out-File.md)

