---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/add-content?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-Content
ms.openlocfilehash: 86702f16683c6710b498a23c072ea9d862868694
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93211154"
---
# <span data-ttu-id="a8037-103">Add-Content</span><span class="sxs-lookup"><span data-stu-id="a8037-103">Add-Content</span></span>

## <span data-ttu-id="a8037-104">개요</span><span class="sxs-lookup"><span data-stu-id="a8037-104">SYNOPSIS</span></span>
<span data-ttu-id="a8037-105">파일에 단어를 추가하는 것과 같이 지정된 항목에 내용을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-105">Adds content to the specified items, such as adding words to a file.</span></span>

## <span data-ttu-id="a8037-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a8037-106">SYNTAX</span></span>

### <span data-ttu-id="a8037-107">Path (기본값)</span><span class="sxs-lookup"><span data-stu-id="a8037-107">Path (Default)</span></span>

```
Add-Content [-Path] <string[]> [-Value] <Object[]> [-PassThru] [-Filter <string>]
 [-Include <string[]>] [-Exclude <string[]>] [-Force] [-Credential <pscredential>] [-WhatIf]
 [-Confirm] [-NoNewline] [-Encoding <Encoding>] [-AsByteStream] [-Stream <string>]
 [<CommonParameters>]
```

### <span data-ttu-id="a8037-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="a8037-108">LiteralPath</span></span>

```
Add-Content [-Value] <Object[]> -LiteralPath <string[]> [-PassThru] [-Filter <string>]
 [-Include <string[]>] [-Exclude <string[]>] [-Force] [-Credential <pscredential>] [-WhatIf]
 [-Confirm] [-NoNewline] [-Encoding <Encoding>] [-AsByteStream] [-Stream <string>]
 [<CommonParameters>]
```

## <span data-ttu-id="a8037-109">설명</span><span class="sxs-lookup"><span data-stu-id="a8037-109">DESCRIPTION</span></span>

<span data-ttu-id="a8037-110">`Add-Content`Cmdlet은 지정 된 항목 또는 파일에 콘텐츠를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-110">The `Add-Content` cmdlet appends content to a specified item or file.</span></span> <span data-ttu-id="a8037-111">명령에 내용을 입력하거나 해당 내용이 포함된 개체를 지정하여 내용을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-111">You can specify the content by typing the content in the command or by specifying an object that contains the content.</span></span>

<span data-ttu-id="a8037-112">다음 예제를 위해 파일이 나 디렉터리를 만들어야 하는 경우에는 [새 항목](New-Item.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a8037-112">If you need to create files or directories for the following examples, see [New-Item](New-Item.md).</span></span>

## <span data-ttu-id="a8037-113">예제</span><span class="sxs-lookup"><span data-stu-id="a8037-113">EXAMPLES</span></span>

### <span data-ttu-id="a8037-114">예제 1: 예외를 사용 하 여 모든 텍스트 파일에 문자열 추가</span><span class="sxs-lookup"><span data-stu-id="a8037-114">Example 1: Add a string to all text files with an exception</span></span>

<span data-ttu-id="a8037-115">이 예제에서는 현재 디렉터리에 있는 텍스트 파일에 값을 추가 하지만 파일 이름에 따라 파일을 제외 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-115">This example appends a value to text files in the current directory but excludes files based on their file name.</span></span>

```powershell
Add-Content -Path .\*.txt -Exclude help* -Value 'End of file'
```

<span data-ttu-id="a8037-116">**Path** 매개 변수는 `.txt` 현재 디렉터리에 있는 모든 파일을 지정 하지만 **제외** 매개 변수는 지정 된 패턴과 일치 하는 파일 이름을 무시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-116">The **Path** parameter specifies all `.txt` files in the current directory, but the **Exclude** parameter ignores file names that match the specified pattern.</span></span> <span data-ttu-id="a8037-117">**값** 매개 변수는 파일에 기록 되는 텍스트 문자열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-117">The **Value** parameter specifies the text string that is written to the files.</span></span>

### <span data-ttu-id="a8037-118">예제 2: 지정 된 파일의 끝에 날짜 추가</span><span class="sxs-lookup"><span data-stu-id="a8037-118">Example 2: Add a date to the end of the specified files</span></span>

<span data-ttu-id="a8037-119">이 예에서는 현재 디렉터리에 있는 파일에 날짜를 추가 하 고 PowerShell 콘솔에 해당 날짜를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-119">This example appends the date to files in the current directory and displays the date in the PowerShell console.</span></span>

```powershell
Add-Content -Path .\DateTimeFile1.log, .\DateTimeFile2.log -Value (Get-Date) -PassThru
Get-Content -Path .\DateTimeFile1.log
```

```Output
Tuesday, May 14, 2019 8:24:27 AM
Tuesday, May 14, 2019 8:24:27 AM
5/14/2019 8:24:27 AM
```

<span data-ttu-id="a8037-120">`Add-Content`Cmdlet은 현재 디렉터리에 두 개의 새 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-120">The `Add-Content` cmdlet creates two new files in the current directory.</span></span> <span data-ttu-id="a8037-121">**값** 매개 변수는 cmdlet의 출력을 포함 합니다 `Get-Date` .</span><span class="sxs-lookup"><span data-stu-id="a8037-121">The **Value** parameter contains the output of the `Get-Date` cmdlet.</span></span> <span data-ttu-id="a8037-122">**PassThru** 매개 변수는 추가 된 내용을 파이프라인에 출력 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-122">The **PassThru** parameter outputs the added contents to the pipeline.</span></span>
<span data-ttu-id="a8037-123">출력을 받을 다른 cmdlet이 없으므로 PowerShell 콘솔에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-123">Because there is no other cmdlet to receive the output, it is displayed in the PowerShell console.</span></span>
<span data-ttu-id="a8037-124">`Get-Content`Cmdlet은 업데이트 된 파일인를 표시 합니다 `DateTimeFile1.log` .</span><span class="sxs-lookup"><span data-stu-id="a8037-124">The `Get-Content` cmdlet displays the updated file, `DateTimeFile1.log`.</span></span>

### <span data-ttu-id="a8037-125">예제 3: 지정 된 파일의 내용을 다른 파일에 추가</span><span class="sxs-lookup"><span data-stu-id="a8037-125">Example 3: Add the contents of a specified file to another file</span></span>

<span data-ttu-id="a8037-126">이 예제에서는 파일에서 콘텐츠를 가져와서 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-126">This example gets the content from a file and stores the content in a variable.</span></span> <span data-ttu-id="a8037-127">변수는 다른 파일에 콘텐츠를 추가 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-127">The variable is used to append the content into another file.</span></span>

```powershell
$From = Get-Content -Path .\CopyFromFile.txt
Add-Content -Path .\CopyToFile.txt -Value $From
Get-Content -Path .\CopyToFile.txt
```

- <span data-ttu-id="a8037-128">`Get-Content`Cmdlet은의 내용을 가져오고 `CopyFromFile.txt` 해당 내용을 변수에 저장 합니다 `$From` .</span><span class="sxs-lookup"><span data-stu-id="a8037-128">The `Get-Content` cmdlet gets the contents of `CopyFromFile.txt` and stores the contents in the `$From` variable.</span></span>
- <span data-ttu-id="a8037-129">`Add-Content`Cmdlet은 `CopyToFile.txt` 변수의 내용을 사용 하 여 파일을 업데이트 합니다 `$From` .</span><span class="sxs-lookup"><span data-stu-id="a8037-129">The `Add-Content` cmdlet updates the `CopyToFile.txt` file using the contents of the `$From` variable.</span></span>
- <span data-ttu-id="a8037-130">이 `Get-Content` cmdlet은 CopyToFile.txt를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-130">The `Get-Content` cmdlet displays CopyToFile.txt.</span></span>

### <span data-ttu-id="a8037-131">예제 4: 파이프라인을 사용 하 여 지정 된 파일의 내용을 다른 파일에 추가</span><span class="sxs-lookup"><span data-stu-id="a8037-131">Example 4: Add the contents of a specified file to another file using the pipeline</span></span>

<span data-ttu-id="a8037-132">이 예제에서는 파일에서 콘텐츠를 가져와 cmdlet으로 파이프 `Add-Content` 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-132">This example gets the content from a file and pipes it to the `Add-Content` cmdlet.</span></span>

```powershell
Get-Content -Path .\CopyFromFile.txt | Add-Content -Path .\CopyToFile.txt
Get-Content -Path .\CopyToFile.txt
```

<span data-ttu-id="a8037-133">`Get-Content`Cmdlet은의 내용을 가져옵니다 `CopyFromFile.txt` .</span><span class="sxs-lookup"><span data-stu-id="a8037-133">The `Get-Content` cmdlet gets the contents of `CopyFromFile.txt`.</span></span> <span data-ttu-id="a8037-134">결과는를 업데이트 하는 cmdlet으로 파이프 됩니다 `Add-Content` `CopyToFile.txt` .</span><span class="sxs-lookup"><span data-stu-id="a8037-134">The results are piped to the `Add-Content` cmdlet, which updates the `CopyToFile.txt`.</span></span>
<span data-ttu-id="a8037-135">마지막 `Get-Content` cmdlet이 표시 됩니다 `CopyToFile.txt` .</span><span class="sxs-lookup"><span data-stu-id="a8037-135">The last `Get-Content` cmdlet displays `CopyToFile.txt`.</span></span>

### <span data-ttu-id="a8037-136">예 5: 새 파일 만들기 및 콘텐츠 복사</span><span class="sxs-lookup"><span data-stu-id="a8037-136">Example 5: Create a new file and copy content</span></span>

<span data-ttu-id="a8037-137">이 예에서는 새 파일을 만들고 기존 파일의 내용을 새 파일에 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-137">This example creates a new file and copies an existing file's content into the new file.</span></span>

```powershell
Add-Content -Path .\NewFile.txt -Value (Get-Content -Path .\CopyFromFile.txt)
Get-Content -Path .\NewFile.txt
```

- <span data-ttu-id="a8037-138">`Add-Content`Cmdlet은 **Path** 및 **Value** 매개 변수를 사용 하 여 현재 디렉터리에 새 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-138">The `Add-Content` cmdlet uses the **Path** and **Value** parameters to create a new file in the current directory.</span></span>
- <span data-ttu-id="a8037-139">`Get-Content`Cmdlet은 기존 파일의 내용을 가져와 `CopyFromFile.txt` **Value** 매개 변수에 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-139">The `Get-Content` cmdlet gets the contents of an existing file, `CopyFromFile.txt` and passes it to the **Value** parameter.</span></span> <span data-ttu-id="a8037-140">Cmdlet 주위의 괄호는 명령이 `Get-Content` 시작 되기 전에 명령이 완료 되도록 합니다 `Add-Content` .</span><span class="sxs-lookup"><span data-stu-id="a8037-140">The parentheses around the `Get-Content` cmdlet ensure that the command finishes before the `Add-Content` command begins.</span></span>
- <span data-ttu-id="a8037-141">`Get-Content`Cmdlet은 새 파일의 내용을 표시 합니다 `NewFile.txt` .</span><span class="sxs-lookup"><span data-stu-id="a8037-141">The `Get-Content` cmdlet displays the contents of the new file, `NewFile.txt`.</span></span>

### <span data-ttu-id="a8037-142">예제 6: 읽기 전용 파일에 콘텐츠 추가</span><span class="sxs-lookup"><span data-stu-id="a8037-142">Example 6: Add content to a read-only file</span></span>

<span data-ttu-id="a8037-143">이 명령은 **IsReadOnly** File 특성이 **True** 로 설정 된 경우에도 파일에 값을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-143">This command adds a value to the file even if the **IsReadOnly** file attribute is set to **True** .</span></span>
<span data-ttu-id="a8037-144">읽기 전용 파일을 만드는 단계는 예제에 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-144">The steps to create a read-only file are included in the example.</span></span>

```powershell
New-Item -Path .\IsReadOnlyTextFile.txt -ItemType File
Set-ItemProperty -Path .\IsReadOnlyTextFile.txt -Name IsReadOnly -Value $True
Get-ChildItem -Path .\IsReadOnlyTextFile.txt
Add-Content -Path .\IsReadOnlyTextFile.txt -Value 'Add value to read-only text file' -Force
Get-Content -Path .\IsReadOnlyTextFile.txt
```

```Output
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-ar--         1/28/2019     13:35              0 IsReadOnlyTextFile.txt
```

- <span data-ttu-id="a8037-145">`New-Item`Cmdlet은 **Path** 및 **ItemType** 매개 변수를 사용 하 여 `IsReadOnlyTextFile.txt` 현재 디렉터리에 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-145">The `New-Item` cmdlet uses the **Path** and **ItemType** parameters to create the file `IsReadOnlyTextFile.txt` in the current directory.</span></span>
- <span data-ttu-id="a8037-146">`Set-ItemProperty`Cmdlet은 **Name** 및 **Value** 매개 변수를 사용 하 여 파일의 **IsReadOnly** 속성을 True로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-146">The `Set-ItemProperty` cmdlet uses the **Name** and **Value** parameters to change the file's **IsReadOnly** property to True.</span></span>
- <span data-ttu-id="a8037-147">`Get-ChildItem`이 cmdlet은 파일이 비어 있고 (0) 읽기 전용 특성 ()을 포함 하 고 있는 것을 보여 줍니다 `r` .</span><span class="sxs-lookup"><span data-stu-id="a8037-147">The `Get-ChildItem` cmdlet shows the file is empty (0) and has the read-only attribute (`r`).</span></span>
- <span data-ttu-id="a8037-148">`Add-Content`Cmdlet은 **Path** 매개 변수를 사용 하 여 파일을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-148">The `Add-Content` cmdlet uses the **Path** parameter to specify the file.</span></span> <span data-ttu-id="a8037-149">**값** 매개 변수는 파일에 추가할 텍스트 문자열을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-149">The **Value** parameter includes the text string to append to the file.</span></span> <span data-ttu-id="a8037-150">**Force** 매개 변수는 읽기 전용 파일에 텍스트를 씁니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-150">The **Force** parameter writes the text to the read-only file.</span></span>
- <span data-ttu-id="a8037-151">`Get-Content`Cmdlet은 **Path** 매개 변수를 사용 하 여 파일의 내용을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-151">The `Get-Content` cmdlet uses the **Path** parameter to display the file's contents.</span></span>

<span data-ttu-id="a8037-152">읽기 전용 특성을 제거 하려면 `Set-ItemProperty` **값** 매개 변수를로 설정 하 여 명령을 사용 `False` 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-152">To remove the read-only attribute, use the `Set-ItemProperty` command with the **Value** parameter set to `False`.</span></span>

### <span data-ttu-id="a8037-153">예 7: Add-Content에서 필터 사용</span><span class="sxs-lookup"><span data-stu-id="a8037-153">Example 7: Use Filters with Add-Content</span></span>

<span data-ttu-id="a8037-154">Cmdlet에 대 한 필터를 지정할 수 있습니다 `Add-Content` .</span><span class="sxs-lookup"><span data-stu-id="a8037-154">You can specify a filter to the `Add-Content` cmdlet.</span></span> <span data-ttu-id="a8037-155">필터를 사용 하 여 **path** 매개 변수를 한 정하는 경우 후행 별표 ()를 포함 하 여 `*` 경로의 내용을 나타내야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-155">When using filters to qualify the **Path** parameter, you need to include a trailing asterisk (`*`) to indicate the contents of the path.</span></span>

<span data-ttu-id="a8037-156">다음 명령은 디렉터리에 있는 모든 파일의 내용을 "Done" 이라는 단어를 추가 합니다 `*.txt` `C:\Temp` .</span><span class="sxs-lookup"><span data-stu-id="a8037-156">The following command adds the word "Done" the content of all `*.txt` files in the `C:\Temp` directory.</span></span>

```powershell
Add-Content -Path C:\Temp\* -Filter *.txt -Value "Done"
```

## <span data-ttu-id="a8037-157">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a8037-157">PARAMETERS</span></span>

### <span data-ttu-id="a8037-158">-AsByteStream</span><span class="sxs-lookup"><span data-stu-id="a8037-158">-AsByteStream</span></span>

<span data-ttu-id="a8037-159">콘텐츠를 바이트 스트림으로 읽도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-159">Specifies that the content should be read as a stream of bytes.</span></span> <span data-ttu-id="a8037-160">이 매개 변수는 PowerShell 6.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-160">This parameter was introduced in PowerShell 6.0.</span></span>

<span data-ttu-id="a8037-161">**AsByteStream** 매개 변수를 **Encoding** 매개 변수와 함께 사용 하는 경우 경고가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-161">A warning occurs when you use the **AsByteStream** parameter with the **Encoding** parameter.</span></span> <span data-ttu-id="a8037-162">**AsByteStream** 매개 변수는 인코딩을 무시 하 고 출력은 바이트 스트림으로 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-162">The **AsByteStream** parameter ignores any encoding and the output is returned as a stream of bytes.</span></span>

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

### <span data-ttu-id="a8037-163">-Credential</span><span class="sxs-lookup"><span data-stu-id="a8037-163">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="a8037-164">이 매개 변수는 PowerShell과 함께 설치 된 모든 공급자에서 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-164">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="a8037-165">이 cmdlet을 실행할 때 다른 사용자를 가장 하거나 자격 증명을 상승 시키려면 [Invoke 명령을](../Microsoft.PowerShell.Core/Invoke-Command.md)사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-165">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a8037-166">-Encoding</span><span class="sxs-lookup"><span data-stu-id="a8037-166">-Encoding</span></span>

<span data-ttu-id="a8037-167">대상 파일의 인코딩 유형을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-167">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="a8037-168">기본값은 `utf8BOM`입니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-168">The default value is `utf8BOM`.</span></span>

<span data-ttu-id="a8037-169">Encoding은 파일 시스템 공급자가 cmdlet에 추가 하는 동적 매개 변수입니다 `Add-Content` .</span><span class="sxs-lookup"><span data-stu-id="a8037-169">Encoding is a dynamic parameter that the FileSystem provider adds to the `Add-Content` cmdlet.</span></span> <span data-ttu-id="a8037-170">이 매개 변수는 파일 시스템 드라이브에만 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-170">This parameter works only in file system drives.</span></span>

<span data-ttu-id="a8037-171">이 매개 변수에 허용 되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-171">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="a8037-172">`ascii`: ASCII (7 비트) 문자 집합에 대 한 인코딩을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-172">`ascii`: Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="a8037-173">`bigendianunicode`: 빅 endian 바이트 순서를 사용 하 여 UTF-16 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-173">`bigendianunicode`: Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="a8037-174">`oem`: MS-DOS 및 콘솔 프로그램에 기본 인코딩을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-174">`oem`: Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="a8037-175">`unicode`: 작은 endian 바이트 순서를 사용 하 여 UTF-16 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-175">`unicode`: Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="a8037-176">`utf7`: UTF-7 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-176">`utf7`: Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="a8037-177">`utf8`: UTF-8 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-177">`utf8`: Encodes in UTF-8 format.</span></span>
- <span data-ttu-id="a8037-178">`utf8BOM`: 바이트 순서 표시 (BOM)를 사용 하 여 UTF-8 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-178">`utf8BOM`: Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="a8037-179">`utf8NoBOM`: BOM (바이트 순서 표시) 없이 UTF-8 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-179">`utf8NoBOM`: Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="a8037-180">`utf32`: U t f-32 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-180">`utf32`: Encodes in UTF-32 format.</span></span>

<span data-ttu-id="a8037-181">PowerShell 6.2부터 **Encoding** 매개 변수를 사용 하 여 등록 된 코드 페이지의 숫자 id (예: `-Encoding 1251` ) 또는 등록 된 코드 페이지의 문자열 이름을 사용할 수도 있습니다 (예: `-Encoding "windows-1251"` ).</span><span class="sxs-lookup"><span data-stu-id="a8037-181">Beginning with PowerShell 6.2, the **Encoding** parameter also allows numeric IDs of registered code pages (like `-Encoding 1251`) or string names of registered code pages (like `-Encoding "windows-1251"`).</span></span> <span data-ttu-id="a8037-182">자세한 내용은 [인코딩에](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2)대 한 .net 설명서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a8037-182">For more information, see the .NET documentation for [Encoding.CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span></span>

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

### <span data-ttu-id="a8037-183">-제외</span><span class="sxs-lookup"><span data-stu-id="a8037-183">-Exclude</span></span>

<span data-ttu-id="a8037-184">이 cmdlet이 작업에서 제외 하는 항목을 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-184">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="a8037-185">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-185">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="a8037-186">경로 요소 또는 패턴 (예:)을 입력 `*.txt` 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-186">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="a8037-187">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-187">Wildcard characters are permitted.</span></span> <span data-ttu-id="a8037-188">**Exclude** 매개 변수는 명령에와 같이 항목의 내용이 포함 된 경우에만 적용 됩니다 `C:\Windows\*` . 여기서 와일드 카드 문자는 디렉터리의 내용을 지정 합니다 `C:\Windows` .</span><span class="sxs-lookup"><span data-stu-id="a8037-188">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="a8037-189">-Filter</span><span class="sxs-lookup"><span data-stu-id="a8037-189">-Filter</span></span>

<span data-ttu-id="a8037-190">**Path** 매개 변수를 한정 하는 필터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-190">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="a8037-191">[FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) 공급자는 필터 사용을 지 원하는 유일한 설치 된 PowerShell 공급자입니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-191">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="a8037-192">[About_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)에서 **FileSystem** 필터 언어의 구문을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-192">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="a8037-193">필터는 다른 매개 변수 보다 더 효율적입니다. cmdlet이 개체가 검색 된 후 개체를 필터링 하는 대신 개체를 가져올 때 해당 개체를 적용 하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-193">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="a8037-194">-Force</span><span class="sxs-lookup"><span data-stu-id="a8037-194">-Force</span></span>

<span data-ttu-id="a8037-195">읽기 전용 특성을 재정의하여 읽기 전용 파일에 내용을 추가할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-195">Overrides the read-only attribute, allowing you to add content to a read-only file.</span></span> <span data-ttu-id="a8037-196">예를 들어 **Force** 는 읽기 전용 특성을 재정의하거나, 디렉터리를 만들어 파일 경로를 완성할 수 있지만 파일 사용 권한을 변경하지는 못합니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-196">For example, **Force** will override the read-only attribute or create directories to complete a file path, but it will not attempt to change file permissions.</span></span>

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

### <span data-ttu-id="a8037-197">-포함</span><span class="sxs-lookup"><span data-stu-id="a8037-197">-Include</span></span>

<span data-ttu-id="a8037-198">이 cmdlet이 작업에 포함 하는 항목 또는 항목을 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-198">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="a8037-199">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-199">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="a8037-200">경로 요소 또는 패턴 (예:)을 입력 `"*.txt"` 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-200">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="a8037-201">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-201">Wildcard characters are permitted.</span></span> <span data-ttu-id="a8037-202">**Include** 매개 변수는 명령에와 같이 항목의 내용이 포함 된 경우에만 적용 됩니다 `C:\Windows\*` . 여기서 와일드 카드 문자는 디렉터리의 내용을 지정 합니다 `C:\Windows` .</span><span class="sxs-lookup"><span data-stu-id="a8037-202">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="a8037-203">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="a8037-203">-LiteralPath</span></span>

<span data-ttu-id="a8037-204">하나 이상의 위치에 대한 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-204">Specifies a path to one or more locations.</span></span> <span data-ttu-id="a8037-205">**LiteralPath** 의 값은 입력 한 대로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-205">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="a8037-206">어떠한 문자도 와일드카드로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-206">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="a8037-207">이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요.</span><span class="sxs-lookup"><span data-stu-id="a8037-207">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="a8037-208">작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-208">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="a8037-209">자세한 내용은 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a8037-209">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a8037-210">-NoNewline</span><span class="sxs-lookup"><span data-stu-id="a8037-210">-NoNewline</span></span>

<span data-ttu-id="a8037-211">이 cmdlet이 콘텐츠에 새 줄 또는 캐리지 리턴을 추가 하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-211">Indicates that this cmdlet does not add a new line or carriage return to the content.</span></span>

<span data-ttu-id="a8037-212">입력 개체의 문자열 표현은 연결 되어 출력을 형성 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-212">The string representations of the input objects are concatenated to form the output.</span></span> <span data-ttu-id="a8037-213">출력 문자열 사이에 공백이 나 줄바꿈 삽입 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-213">No spaces or newlines are inserted between the output strings.</span></span> <span data-ttu-id="a8037-214">마지막 출력 문자열 뒤에는 줄 바꿈이 추가 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-214">No newline is added after the last output string.</span></span>

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

### <span data-ttu-id="a8037-215">-PassThru</span><span class="sxs-lookup"><span data-stu-id="a8037-215">-PassThru</span></span>

<span data-ttu-id="a8037-216">추가된 내용을 나타내는 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-216">Returns an object representing the added content.</span></span> <span data-ttu-id="a8037-217">기본적으로 이 cmdlet은 출력을 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-217">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="a8037-218">-Path</span><span class="sxs-lookup"><span data-stu-id="a8037-218">-Path</span></span>

<span data-ttu-id="a8037-219">추가 내용을 받는 항목의 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-219">Specifies the path to the items that receive the additional content.</span></span>
<span data-ttu-id="a8037-220">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-220">Wildcard characters are permitted.</span></span>
<span data-ttu-id="a8037-221">경로는 컨테이너가 아니라 항목의 경로여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-221">The paths must be paths to items, not to containers.</span></span>
<span data-ttu-id="a8037-222">예를 들어 디렉터리의 경로가 아니라 하나 이상의 파일 경로를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-222">For example, you must specify a path to one or more files, not a path to a directory.</span></span>
<span data-ttu-id="a8037-223">여러 경로를 지정하는 경우 쉼표를 사용하여 경로를 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-223">If you specify multiple paths, use commas to separate the paths.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="a8037-224">-스트림</span><span class="sxs-lookup"><span data-stu-id="a8037-224">-Stream</span></span>

<span data-ttu-id="a8037-225">콘텐츠에 대 한 대체 데이터 스트림을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-225">Specifies an alternative data stream for content.</span></span> <span data-ttu-id="a8037-226">스트림이 없는 경우이 cmdlet은이를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-226">If the stream does not exist, this cmdlet creates it.</span></span> <span data-ttu-id="a8037-227">와일드카드 문자는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-227">Wildcard characters are not supported.</span></span>

<span data-ttu-id="a8037-228">**스트림은** 파일 시스템 공급자가에 추가 하는 동적 매개 변수입니다 `Add-Content` .</span><span class="sxs-lookup"><span data-stu-id="a8037-228">**Stream** is a dynamic parameter that the FileSystem provider adds to `Add-Content`.</span></span> <span data-ttu-id="a8037-229">이 매개 변수는 파일 시스템 드라이브에만 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-229">This parameter works only in file system drives.</span></span>

<span data-ttu-id="a8037-230">Cmdlet을 사용 하 여 `Add-Content` 영역의 콘텐츠를 변경할 수 있습니다 **. 식별자** 대체 데이터 스트림입니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-230">You can use the `Add-Content` cmdlet to change the content of the **Zone.Identifier** alternate data stream.</span></span> <span data-ttu-id="a8037-231">그러나이 방법은 인터넷에서 다운로드 된 파일을 차단 하는 보안 검사를 제거 하는 방법으로 권장 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-231">However, we do not recommend this as a way to eliminate security checks that block files that are downloaded from the Internet.</span></span> <span data-ttu-id="a8037-232">다운로드 한 파일이 안전한 지 확인 하려면 cmdlet을 사용 `Unblock-File` 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-232">If you verify that a downloaded file is safe, use the `Unblock-File` cmdlet.</span></span>

<span data-ttu-id="a8037-233">이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-233">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="a8037-234">-Value</span><span class="sxs-lookup"><span data-stu-id="a8037-234">-Value</span></span>

<span data-ttu-id="a8037-235">추가할 내용을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-235">Specifies the content to be added.</span></span> <span data-ttu-id="a8037-236">**이 데이터는 내부용 으로만 사용 되** 는 따옴표로 묶인 문자열을 입력 하거나를 생성 하는 **DateTime** 개체와 같이 콘텐츠가 포함 된 개체를 지정 `Get-Date` 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-236">Type a quoted string, such as **This data is for internal use only** , or specify an object that contains content, such as the **DateTime** object that `Get-Date` generates.</span></span>

<span data-ttu-id="a8037-237">경로는 단지 문자열 이므로 경로를 입력 하 여 파일의 내용을 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-237">You cannot specify the contents of a file by typing its path, because the path is just a string.</span></span>
<span data-ttu-id="a8037-238">명령을 사용 하 여 `Get-Content` 콘텐츠를 가져와서 **Value** 매개 변수에 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-238">You can use a `Get-Content` command to get the content and pass it to the **Value** parameter.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="a8037-239">-Confirm</span><span class="sxs-lookup"><span data-stu-id="a8037-239">-Confirm</span></span>

<span data-ttu-id="a8037-240">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-240">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="a8037-241">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="a8037-241">-WhatIf</span></span>

<span data-ttu-id="a8037-242">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-242">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="a8037-243">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-243">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="a8037-244">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a8037-244">CommonParameters</span></span>

<span data-ttu-id="a8037-245">이 cmdlet은,,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` 및 `-WarningVariable` 등의 일반 매개 변수를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-245">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="a8037-246">자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a8037-246">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="a8037-247">입력</span><span class="sxs-lookup"><span data-stu-id="a8037-247">INPUTS</span></span>

### <span data-ttu-id="a8037-248">System.object, System.web. PSCredential</span><span class="sxs-lookup"><span data-stu-id="a8037-248">System.Object, System.Management.Automation.PSCredential</span></span>

<span data-ttu-id="a8037-249">값, 경로 또는 자격 증명을로 파이프 할 수 있습니다 `Set-Content` .</span><span class="sxs-lookup"><span data-stu-id="a8037-249">You can pipe values, paths, or credentials to `Set-Content`.</span></span>

## <span data-ttu-id="a8037-250">출력</span><span class="sxs-lookup"><span data-stu-id="a8037-250">OUTPUTS</span></span>

### <span data-ttu-id="a8037-251">없음 또는 System.String</span><span class="sxs-lookup"><span data-stu-id="a8037-251">None or System.String</span></span>

<span data-ttu-id="a8037-252">**PassThru** 매개 변수를 사용 하는 경우는 `Add-Content` 콘텐츠를 나타내는 **system.string** 개체를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-252">When you use the **PassThru** parameter, `Add-Content` generates a **System.String** object that represents the content.</span></span> <span data-ttu-id="a8037-253">그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-253">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="a8037-254">참고</span><span class="sxs-lookup"><span data-stu-id="a8037-254">NOTES</span></span>

- <span data-ttu-id="a8037-255">개체를로 파이프 하면 `Add-Content` 개체가 항목에 추가 되기 전에 문자열로 변환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-255">When you pipe an object to `Add-Content`, the object is converted to a string before it is added to the item.</span></span> <span data-ttu-id="a8037-256">개체 유형에 따라 문자열 형식이 결정되지만 형식이 개체의 기본 표시 형식과 다를 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-256">The object type determines the string format, but the format might be different than the default display of the object.</span></span> <span data-ttu-id="a8037-257">문자열 형식을 제어하려면 보내는 cmdlet의 형식 지정 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-257">To control the string format, use the formatting parameters of the sending cmdlet.</span></span>
- <span data-ttu-id="a8037-258">의 기본 제공 별칭인를 참조할 수도 있습니다 `Add-Content` `ac` .</span><span class="sxs-lookup"><span data-stu-id="a8037-258">You can also refer to `Add-Content` by its built-in alias, `ac`.</span></span> <span data-ttu-id="a8037-259">자세한 내용은 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a8037-259">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>
- <span data-ttu-id="a8037-260">`Add-Content`Cmdlet은 모든 공급자가 제공 하는 데이터에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-260">The `Add-Content` cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="a8037-261">세션에서 사용할 수 있는 공급자를 나열 하려면을 입력 `Get-PSProvider` 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8037-261">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="a8037-262">자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a8037-262">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="a8037-263">관련 링크</span><span class="sxs-lookup"><span data-stu-id="a8037-263">RELATED LINKS</span></span>

[<span data-ttu-id="a8037-264">about_Aliases</span><span class="sxs-lookup"><span data-stu-id="a8037-264">about_Aliases</span></span>](../Microsoft.PowerShell.Core/About/about_Aliases.md)

[<span data-ttu-id="a8037-265">about_Providers</span><span class="sxs-lookup"><span data-stu-id="a8037-265">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="a8037-266">Clear-Content</span><span class="sxs-lookup"><span data-stu-id="a8037-266">Clear-Content</span></span>](Clear-Content.md)

[<span data-ttu-id="a8037-267">Get-Content</span><span class="sxs-lookup"><span data-stu-id="a8037-267">Get-Content</span></span>](Get-Content.md)

[<span data-ttu-id="a8037-268">Get-Item</span><span class="sxs-lookup"><span data-stu-id="a8037-268">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="a8037-269">New-Item</span><span class="sxs-lookup"><span data-stu-id="a8037-269">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="a8037-270">Set-Content</span><span class="sxs-lookup"><span data-stu-id="a8037-270">Set-Content</span></span>](Set-Content.md)
