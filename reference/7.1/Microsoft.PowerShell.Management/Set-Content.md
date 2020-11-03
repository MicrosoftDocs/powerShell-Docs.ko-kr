---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 08/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-content?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Content
ms.openlocfilehash: bb9345470aa58dac7c14e1443c0fe4c12e7563a6
ms.sourcegitcommit: 9a8bb1b459b5939c95e1f6d9499fcb13d01a58c4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/25/2020
ms.locfileid: "93219705"
---
# <span data-ttu-id="9903c-103">Set-Content</span><span class="sxs-lookup"><span data-stu-id="9903c-103">Set-Content</span></span>

## <span data-ttu-id="9903c-104">개요</span><span class="sxs-lookup"><span data-stu-id="9903c-104">SYNOPSIS</span></span>
<span data-ttu-id="9903c-105">새 콘텐츠를 쓰거나 파일의 기존 내용을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-105">Writes new content or replaces existing content in a file.</span></span>

## <span data-ttu-id="9903c-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9903c-106">SYNTAX</span></span>

### <span data-ttu-id="9903c-107">Path (기본값)</span><span class="sxs-lookup"><span data-stu-id="9903c-107">Path (Default)</span></span>

```
Set-Content [-Path] <string[]> [-Value] <Object[]> [-PassThru] [-Filter <string>]
 [-Include <string[]>] [-Exclude <string[]>] [-Force] [-Credential <pscredential>]
 [-WhatIf] [-Confirm] [-NoNewline] [-Encoding <Encoding>] [-AsByteStream] [-Stream <string>]
 [<CommonParameters>]
```

### <span data-ttu-id="9903c-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="9903c-108">LiteralPath</span></span>

```
Set-Content [-Value] <Object[]> -LiteralPath <string[]> [-PassThru] [-Filter <string>]
 [-Include <string[]>] [-Exclude <string[]>] [-Force] [-Credential <pscredential>]
 [-WhatIf] [-Confirm] [-NoNewline] [-Encoding <Encoding>] [-AsByteStream] [-Stream <string>]
 [<CommonParameters>]
```

## <span data-ttu-id="9903c-109">설명</span><span class="sxs-lookup"><span data-stu-id="9903c-109">DESCRIPTION</span></span>

<span data-ttu-id="9903c-110">`Set-Content` 는 새 콘텐츠를 쓰거나 파일의 내용을 바꾸는 문자열 처리 cmdlet입니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-110">`Set-Content` is a string-processing cmdlet that writes new content or replaces the content in a file.</span></span> <span data-ttu-id="9903c-111">`Set-Content` 기존 콘텐츠를 대체 하며 `Add-Content` 파일에 콘텐츠를 추가 하는 cmdlet과 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-111">`Set-Content` replaces the existing content and differs from the `Add-Content` cmdlet that appends content to a file.</span></span> <span data-ttu-id="9903c-112">로 콘텐츠를 보내려면 `Set-Content` 명령줄에서 **Value** 매개 변수를 사용 하거나 파이프라인을 통해 콘텐츠를 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-112">To send content to `Set-Content` you can use the **Value** parameter on the command line or send content through the pipeline.</span></span>

<span data-ttu-id="9903c-113">다음 예제를 위해 파일이 나 디렉터리를 만들어야 하는 경우에는 [새 항목](New-Item.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9903c-113">If you need to create files or directories for the following examples, see [New-Item](New-Item.md).</span></span>

## <span data-ttu-id="9903c-114">예제</span><span class="sxs-lookup"><span data-stu-id="9903c-114">EXAMPLES</span></span>

### <span data-ttu-id="9903c-115">예제 1: 디렉터리에서 여러 파일의 내용 바꾸기</span><span class="sxs-lookup"><span data-stu-id="9903c-115">Example 1: Replace the contents of multiple files in a directory</span></span>

<span data-ttu-id="9903c-116">이 예제에서는 현재 디렉터리에 있는 여러 파일의 콘텐츠를 대체 합니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-116">This example replaces the content for multiple files in the current directory.</span></span>

```powershell
Get-ChildItem -Path .\Test*.txt
```

```Output
Test1.txt
Test2.txt
Test3.txt
```

```powershell
Set-Content -Path .\Test*.txt -Value 'Hello, World'
Get-Content -Path .\Test*.txt
```

```Output
Hello, World
Hello, World
Hello, World
```

<span data-ttu-id="9903c-117">`Get-ChildItem`Cmdlet은 **Path** 매개 변수를 사용 하 여 현재 디렉터리에서로 시작 하는 **.txt** 파일을 나열 합니다. `Test*`</span><span class="sxs-lookup"><span data-stu-id="9903c-117">The `Get-ChildItem` cmdlet uses the **Path** parameter to list **.txt** files that begin with `Test*` in the current directory.</span></span> <span data-ttu-id="9903c-118">`Set-Content`Cmdlet은 **Path** 매개 변수를 사용 하 여 파일을 지정 합니다 `Test*.txt` .</span><span class="sxs-lookup"><span data-stu-id="9903c-118">The `Set-Content` cmdlet uses the **Path** parameter to specify the `Test*.txt` files.</span></span> <span data-ttu-id="9903c-119">**Value** 매개 변수는 각 파일의 기존 내용을 대체 하는 텍스트 문자열 **Hello를** 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-119">The **Value** parameter provides the text string **Hello, World** that replaces the existing content in each file.</span></span> <span data-ttu-id="9903c-120">`Get-Content`Cmdlet은 **Path** 매개 변수를 사용 하 여 파일을 지정 하 `Test*.txt` 고 PowerShell 콘솔에 각 파일의 콘텐츠를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-120">The `Get-Content` cmdlet uses the **Path** parameter to specify the `Test*.txt` files and displays each file's content in the PowerShell console.</span></span>

### <span data-ttu-id="9903c-121">예제 2: 새 파일 만들기 및 콘텐츠 작성</span><span class="sxs-lookup"><span data-stu-id="9903c-121">Example 2: Create a new file and write content</span></span>

<span data-ttu-id="9903c-122">이 예에서는 새 파일을 만들고 현재 날짜와 시간을 파일에 씁니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-122">This example creates a new file and writes the current date and time to the file.</span></span>

```powershell
Set-Content -Path .\DateTime.txt -Value (Get-Date)
Get-Content -Path .\DateTime.txt
```

```Output
1/30/2019 09:55:08
```

<span data-ttu-id="9903c-123">`Set-Content`**Path** 및 **Value** 매개 변수를 사용 하 여 현재 디렉터리에 **DateTime.txt** 라는 새 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-123">`Set-Content` uses the **Path** and **Value** parameters to create a new file named **DateTime.txt** in the current directory.</span></span> <span data-ttu-id="9903c-124">**값** 매개 변수는 `Get-Date` 를 사용 하 여 현재 날짜와 시간을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-124">The **Value** parameter uses `Get-Date` to get the current date and time.</span></span>
<span data-ttu-id="9903c-125">`Set-Content`**DateTime** 개체를 문자열로 파일에 씁니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-125">`Set-Content` writes the **DateTime** object to the file as a string.</span></span> <span data-ttu-id="9903c-126">`Get-Content`Cmdlet은 **Path** 매개 변수를 사용 하 여 PowerShell 콘솔에 **DateTime.txt** 의 내용을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-126">The `Get-Content` cmdlet uses the **Path** parameter to display the content of **DateTime.txt** in the PowerShell console.</span></span>

### <span data-ttu-id="9903c-127">예제 3: 파일에서 텍스트 바꾸기</span><span class="sxs-lookup"><span data-stu-id="9903c-127">Example 3: Replace text in a file</span></span>

<span data-ttu-id="9903c-128">이 명령은 기존 파일 내에 있는 모든 word 인스턴스를 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-128">This command replaces all instances of word within an existing file.</span></span>

```powershell
Get-Content -Path .\Notice.txt
```

```Output
Warning
Replace Warning with a new word.
The word Warning was replaced.
```

```powershell
(Get-Content -Path .\Notice.txt) |
    ForEach-Object {$_ -Replace 'Warning', 'Caution'} |
        Set-Content -Path .\Notice.txt
Get-Content -Path .\Notice.txt
```

```Output
Caution
Replace Caution with a new word.
The word Caution was replaced.
```

<span data-ttu-id="9903c-129">`Get-Content`Cmdlet은 **Path** 매개 변수를 사용 하 여 현재 디렉터리에 있는 **Notice.txt** 파일을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-129">The `Get-Content` cmdlet uses the **Path** parameter to specify the **Notice.txt** file in the current directory.</span></span> <span data-ttu-id="9903c-130">명령이 `Get-Content` 파이프라인으로 전송 되기 전에 명령이 완료 되도록 괄호를 사용 하 여 명령이 래핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-130">The `Get-Content` command is wrapped with parentheses so that the command finishes before being sent down the pipeline.</span></span>

<span data-ttu-id="9903c-131">**Notice.txt** 파일의 내용이 파이프라인에서 cmdlet으로 전송 됩니다 `ForEach-Object` .</span><span class="sxs-lookup"><span data-stu-id="9903c-131">The contents of the **Notice.txt** file are sent down the pipeline to the `ForEach-Object` cmdlet.</span></span>
<span data-ttu-id="9903c-132">`ForEach-Object` 자동 변수를 사용 하 `$_` 고 **경고** 를 발생 하는 각 항목을 **주의** 하 여 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-132">`ForEach-Object` uses the automatic variable `$_` and replaces each occurrence of **Warning** with **Caution**.</span></span> <span data-ttu-id="9903c-133">개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Set-Content` .</span><span class="sxs-lookup"><span data-stu-id="9903c-133">The objects are sent down the pipeline to the `Set-Content` cmdlet.</span></span> <span data-ttu-id="9903c-134">`Set-Content`**Path** 매개 변수를 사용 하 여 **Notice.txt** 파일을 지정 하 고 업데이트 된 콘텐츠를 파일에 씁니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-134">`Set-Content` uses the **Path** parameter to specify the **Notice.txt** file and writes the updated content to the file.</span></span>

<span data-ttu-id="9903c-135">마지막 `Get-Content` cmdlet은 PowerShell 콘솔에 업데이트 된 파일 콘텐츠를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-135">The last `Get-Content` cmdlet displays the updated file content in the PowerShell console.</span></span>

### <span data-ttu-id="9903c-136">예제 4: Set-Content에서 필터 사용</span><span class="sxs-lookup"><span data-stu-id="9903c-136">Example 4: Use Filters with Set-Content</span></span>

<span data-ttu-id="9903c-137">Cmdlet에 대 한 필터를 지정할 수 있습니다 `Set-Content` .</span><span class="sxs-lookup"><span data-stu-id="9903c-137">You can specify a filter to the `Set-Content` cmdlet.</span></span> <span data-ttu-id="9903c-138">필터를 사용 하 여 **path** 매개 변수를 한 정하는 경우 후행 별표 ()를 포함 하 여 `*` 경로의 내용을 나타내야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-138">When using filters to qualify the **Path** parameter, you need to include a trailing asterisk (`*`) to indicate the contents of the path.</span></span>

<span data-ttu-id="9903c-139">다음 명령은 `*.txt` 디렉터리에 있는 모든 파일의 내용을 `C:\Temp` 비어 있는 **값** 으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-139">The following command set the content all `*.txt` files in the `C:\Temp` directory to the **Value** empty.</span></span>

```powershell
Set-Content -Path C:\Temp\* -Filter *.txt -Value "Empty"
```

## <span data-ttu-id="9903c-140">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9903c-140">PARAMETERS</span></span>

### <span data-ttu-id="9903c-141">-AsByteStream</span><span class="sxs-lookup"><span data-stu-id="9903c-141">-AsByteStream</span></span>

<span data-ttu-id="9903c-142">콘텐츠를 바이트 스트림으로 읽도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-142">Specifies that the content should be read as a stream of bytes.</span></span> <span data-ttu-id="9903c-143">이 매개 변수는 PowerShell 6.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-143">This parameter was introduced in PowerShell 6.0.</span></span>

<span data-ttu-id="9903c-144">**AsByteStream** 매개 변수를 **Encoding** 매개 변수와 함께 사용 하는 경우 경고가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-144">A warning occurs when you use the **AsByteStream** parameter with the **Encoding** parameter.</span></span> <span data-ttu-id="9903c-145">**AsByteStream** 매개 변수는 인코딩을 무시 하 고 출력은 바이트 스트림으로 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-145">The **AsByteStream** parameter ignores any encoding and the output is returned as a stream of bytes.</span></span>

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

### <span data-ttu-id="9903c-146">-Credential</span><span class="sxs-lookup"><span data-stu-id="9903c-146">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="9903c-147">이 매개 변수는 PowerShell과 함께 설치 된 모든 공급자에서 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-147">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="9903c-148">이 cmdlet을 실행할 때 다른 사용자를 가장 하거나 자격 증명을 상승 시키려면 [Invoke 명령을](../Microsoft.PowerShell.Core/Invoke-Command.md)사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-148">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="9903c-149">-Encoding</span><span class="sxs-lookup"><span data-stu-id="9903c-149">-Encoding</span></span>

<span data-ttu-id="9903c-150">대상 파일의 인코딩 유형을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-150">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="9903c-151">기본값은 `utf8NoBOM`입니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-151">The default value is `utf8NoBOM`.</span></span>

<span data-ttu-id="9903c-152">Encoding은 파일 시스템 공급자가에 추가 하는 동적 매개 변수입니다 `Set-Content` .</span><span class="sxs-lookup"><span data-stu-id="9903c-152">Encoding is a dynamic parameter that the FileSystem provider adds to `Set-Content`.</span></span> <span data-ttu-id="9903c-153">이 매개 변수는 파일 시스템 드라이브에만 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-153">This parameter works only in file system drives.</span></span>

<span data-ttu-id="9903c-154">이 매개 변수에 허용 되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-154">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="9903c-155">`ascii`: ASCII (7 비트) 문자 집합에 대 한 인코딩을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-155">`ascii`: Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="9903c-156">`bigendianunicode`: 빅 endian 바이트 순서를 사용 하 여 UTF-16 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-156">`bigendianunicode`: Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="9903c-157">`bigendianutf32`: 빅 endian 바이트 순서를 사용 하 여 u t f-32 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-157">`bigendianutf32`: Encodes in UTF-32 format using the big-endian byte order.</span></span>
- <span data-ttu-id="9903c-158">`oem`: MS-DOS 및 콘솔 프로그램에 기본 인코딩을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-158">`oem`: Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="9903c-159">`unicode`: 작은 endian 바이트 순서를 사용 하 여 UTF-16 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-159">`unicode`: Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="9903c-160">`utf7`: UTF-7 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-160">`utf7`: Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="9903c-161">`utf8`: UTF-8 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-161">`utf8`: Encodes in UTF-8 format.</span></span>
- <span data-ttu-id="9903c-162">`utf8BOM`: 바이트 순서 표시 (BOM)를 사용 하 여 UTF-8 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-162">`utf8BOM`: Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="9903c-163">`utf8NoBOM`: BOM (바이트 순서 표시) 없이 UTF-8 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-163">`utf8NoBOM`: Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="9903c-164">`utf32`: U t f-32 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-164">`utf32`: Encodes in UTF-32 format.</span></span>

<span data-ttu-id="9903c-165">PowerShell 6.2부터 **Encoding** 매개 변수를 사용 하 여 등록 된 코드 페이지의 숫자 id (예: `-Encoding 1251` ) 또는 등록 된 코드 페이지의 문자열 이름을 사용할 수도 있습니다 (예: `-Encoding "windows-1251"` ).</span><span class="sxs-lookup"><span data-stu-id="9903c-165">Beginning with PowerShell 6.2, the **Encoding** parameter also allows numeric IDs of registered code pages (like `-Encoding 1251`) or string names of registered code pages (like `-Encoding "windows-1251"`).</span></span> <span data-ttu-id="9903c-166">자세한 내용은 [인코딩에](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2)대 한 .net 설명서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9903c-166">For more information, see the .NET documentation for [Encoding.CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span></span>

> [!NOTE]
> <span data-ttu-id="9903c-167">**U t f-7** \*은 더 이상 사용 하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-167">**UTF-7** \* is no longer recommended to use.</span></span> <span data-ttu-id="9903c-168">PowerShell 7.1에서는 `utf7` **인코딩** 매개 변수에 대해를 지정 하는 경우 경고가 기록 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-168">In PowerShell 7.1, a warning is written if you specify `utf7` for the **Encoding** parameter.</span></span>

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

### <span data-ttu-id="9903c-169">-제외</span><span class="sxs-lookup"><span data-stu-id="9903c-169">-Exclude</span></span>

<span data-ttu-id="9903c-170">이 cmdlet이 작업에서 제외 하는 항목을 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-170">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="9903c-171">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-171">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="9903c-172">경로 요소 또는 패턴 (예:)을 입력 `*.txt` 합니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-172">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="9903c-173">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-173">Wildcard characters are permitted.</span></span> <span data-ttu-id="9903c-174">**Exclude** 매개 변수는 명령에와 같이 항목의 내용이 포함 된 경우에만 적용 됩니다 `C:\Windows\*` . 여기서 와일드 카드 문자는 디렉터리의 내용을 지정 합니다 `C:\Windows` .</span><span class="sxs-lookup"><span data-stu-id="9903c-174">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="9903c-175">-Filter</span><span class="sxs-lookup"><span data-stu-id="9903c-175">-Filter</span></span>

<span data-ttu-id="9903c-176">**Path** 매개 변수를 한정 하는 필터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-176">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="9903c-177">[FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) 공급자는 필터 사용을 지 원하는 유일한 설치 된 PowerShell 공급자입니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-177">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="9903c-178">[About_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)에서 **FileSystem** 필터 언어의 구문을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-178">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="9903c-179">필터는 다른 매개 변수 보다 더 효율적입니다. cmdlet이 개체가 검색 된 후 개체를 필터링 하는 대신 개체를 가져올 때 해당 개체를 적용 하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-179">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="9903c-180">-Force</span><span class="sxs-lookup"><span data-stu-id="9903c-180">-Force</span></span>

<span data-ttu-id="9903c-181">파일이 읽기 전용인 경우에도 cmdlet이 파일의 콘텐츠를 설정 하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-181">Forces the cmdlet to set the contents of a file, even if the file is read-only.</span></span> <span data-ttu-id="9903c-182">구현은 공급자에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-182">Implementation varies from provider to provider.</span></span> <span data-ttu-id="9903c-183">자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9903c-183">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>
<span data-ttu-id="9903c-184">**Force** 매개 변수는 보안 제한을 재정의 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-184">The **Force** parameter does not override security restrictions.</span></span>

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

### <span data-ttu-id="9903c-185">-포함</span><span class="sxs-lookup"><span data-stu-id="9903c-185">-Include</span></span>

<span data-ttu-id="9903c-186">이 cmdlet이 작업에 포함 하는 항목 또는 항목을 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-186">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="9903c-187">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-187">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="9903c-188">경로 요소 또는 패턴 (예:)을 입력 `"*.txt"` 합니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-188">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="9903c-189">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-189">Wildcard characters are permitted.</span></span> <span data-ttu-id="9903c-190">**Include** 매개 변수는 명령에와 같이 항목의 내용이 포함 된 경우에만 적용 됩니다 `C:\Windows\*` . 여기서 와일드 카드 문자는 디렉터리의 내용을 지정 합니다 `C:\Windows` .</span><span class="sxs-lookup"><span data-stu-id="9903c-190">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="9903c-191">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="9903c-191">-LiteralPath</span></span>

<span data-ttu-id="9903c-192">하나 이상의 위치에 대한 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-192">Specifies a path to one or more locations.</span></span> <span data-ttu-id="9903c-193">**LiteralPath** 의 값은 입력 한 대로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-193">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="9903c-194">어떠한 문자도 와일드카드로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-194">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="9903c-195">이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요.</span><span class="sxs-lookup"><span data-stu-id="9903c-195">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="9903c-196">작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-196">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="9903c-197">자세한 내용은 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9903c-197">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="9903c-198">-NoNewline</span><span class="sxs-lookup"><span data-stu-id="9903c-198">-NoNewline</span></span>

<span data-ttu-id="9903c-199">입력 개체의 문자열 표현은 연결 되어 출력을 형성 합니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-199">The string representations of the input objects are concatenated to form the output.</span></span> <span data-ttu-id="9903c-200">출력 문자열 사이에 공백이 나 줄바꿈 삽입 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-200">No spaces or newlines are inserted between the output strings.</span></span> <span data-ttu-id="9903c-201">마지막 출력 문자열 뒤에는 줄 바꿈이 추가 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-201">No newline is added after the last output string.</span></span>

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

### <span data-ttu-id="9903c-202">-PassThru</span><span class="sxs-lookup"><span data-stu-id="9903c-202">-PassThru</span></span>

<span data-ttu-id="9903c-203">콘텐츠를 나타내는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-203">Returns an object that represents the content.</span></span> <span data-ttu-id="9903c-204">기본적으로 이 cmdlet은 출력을 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-204">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="9903c-205">-Path</span><span class="sxs-lookup"><span data-stu-id="9903c-205">-Path</span></span>

<span data-ttu-id="9903c-206">콘텐츠를 받는 항목의 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-206">Specifies the path of the item that receives the content.</span></span>
<span data-ttu-id="9903c-207">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-207">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="9903c-208">-스트림</span><span class="sxs-lookup"><span data-stu-id="9903c-208">-Stream</span></span>

<span data-ttu-id="9903c-209">콘텐츠에 대 한 대체 데이터 스트림을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-209">Specifies an alternative data stream for content.</span></span> <span data-ttu-id="9903c-210">스트림이 없는 경우이 cmdlet은이를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-210">If the stream does not exist, this cmdlet creates it.</span></span> <span data-ttu-id="9903c-211">와일드카드 문자는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-211">Wildcard characters are not supported.</span></span>

<span data-ttu-id="9903c-212">**스트림은** **파일 시스템** 공급자가에 추가 하는 동적 매개 변수입니다 `Set-Content` .</span><span class="sxs-lookup"><span data-stu-id="9903c-212">**Stream** is a dynamic parameter that the **FileSystem** provider adds to `Set-Content`.</span></span> <span data-ttu-id="9903c-213">이 매개 변수는 파일 시스템 드라이브에만 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-213">This parameter works only in file system drives.</span></span>

<span data-ttu-id="9903c-214">Cmdlet을 사용 하 여 `Set-Content` 영역의 콘텐츠를 변경할 수 있습니다 **. 식별자** 대체 데이터 스트림입니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-214">You can use the `Set-Content` cmdlet to change the content of the **Zone.Identifier** alternate data stream.</span></span> <span data-ttu-id="9903c-215">그러나이 방법은 인터넷에서 다운로드 된 파일을 차단 하는 보안 검사를 제거 하는 방법으로 권장 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-215">However, we do not recommend this as a way to eliminate security checks that block files that are downloaded from the Internet.</span></span> <span data-ttu-id="9903c-216">다운로드 한 파일이 안전한 지 확인 하려면 cmdlet을 사용 `Unblock-File` 합니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-216">If you verify that a downloaded file is safe, use the `Unblock-File` cmdlet.</span></span>

<span data-ttu-id="9903c-217">이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-217">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="9903c-218">-Value</span><span class="sxs-lookup"><span data-stu-id="9903c-218">-Value</span></span>

<span data-ttu-id="9903c-219">항목의 새 내용을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-219">Specifies the new content for the item.</span></span>

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

### <span data-ttu-id="9903c-220">-Confirm</span><span class="sxs-lookup"><span data-stu-id="9903c-220">-Confirm</span></span>

<span data-ttu-id="9903c-221">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-221">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="9903c-222">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="9903c-222">-WhatIf</span></span>

<span data-ttu-id="9903c-223">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-223">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="9903c-224">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-224">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="9903c-225">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9903c-225">CommonParameters</span></span>

<span data-ttu-id="9903c-226">이 cmdlet은,,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` 및 `-WarningVariable` 등의 일반 매개 변수를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-226">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span>
<span data-ttu-id="9903c-227">자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9903c-227">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="9903c-228">입력</span><span class="sxs-lookup"><span data-stu-id="9903c-228">INPUTS</span></span>

### <span data-ttu-id="9903c-229">System.Object</span><span class="sxs-lookup"><span data-stu-id="9903c-229">System.Object</span></span>

<span data-ttu-id="9903c-230">항목의 새 값을 포함 하는 개체를로 파이프 할 수 있습니다 `Set-Content` .</span><span class="sxs-lookup"><span data-stu-id="9903c-230">You can pipe an object that contains the new value for the item to `Set-Content`.</span></span>

## <span data-ttu-id="9903c-231">출력</span><span class="sxs-lookup"><span data-stu-id="9903c-231">OUTPUTS</span></span>

### <span data-ttu-id="9903c-232">없음 또는 System.String</span><span class="sxs-lookup"><span data-stu-id="9903c-232">None or System.String</span></span>

<span data-ttu-id="9903c-233">**PassThru** 매개 변수를 사용 하는 경우는 `Set-Content` 콘텐츠를 나타내는 **system.string** 개체를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-233">When you use the **PassThru** parameter, `Set-Content` generates a **System.String** object that represents the content.</span></span> <span data-ttu-id="9903c-234">그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-234">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="9903c-235">참고</span><span class="sxs-lookup"><span data-stu-id="9903c-235">NOTES</span></span>

- <span data-ttu-id="9903c-236">의 기본 제공 별칭인를 참조할 수도 있습니다 `Set-Content` `sc` .</span><span class="sxs-lookup"><span data-stu-id="9903c-236">You can also refer to `Set-Content` by its built-in alias, `sc`.</span></span>
  <span data-ttu-id="9903c-237">자세한 내용은 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9903c-237">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>
- <span data-ttu-id="9903c-238">`Set-Content` 는 문자열 처리를 위해 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-238">`Set-Content` is designed for string processing.</span></span> <span data-ttu-id="9903c-239">문자열이 아닌 개체를에 파이프 하면 `Set-Content` 개체를 쓰기 전에 문자열로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-239">If you pipe non-string objects to `Set-Content`, it converts the object to a string before writing it.</span></span> <span data-ttu-id="9903c-240">개체를 파일에 쓰려면를 사용 `Out-File` 합니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-240">To write objects to files, use `Out-File`.</span></span>
- <span data-ttu-id="9903c-241">`Set-Content`Cmdlet은 모든 공급자가 제공 하는 데이터에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-241">The `Set-Content` cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="9903c-242">세션에서 사용할 수 있는 공급자를 나열 하려면을 입력 `Get-PsProvider` 합니다.</span><span class="sxs-lookup"><span data-stu-id="9903c-242">To list the providers available in your session, type `Get-PsProvider`.</span></span> <span data-ttu-id="9903c-243">자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9903c-243">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="9903c-244">관련 링크</span><span class="sxs-lookup"><span data-stu-id="9903c-244">RELATED LINKS</span></span>

[<span data-ttu-id="9903c-245">about_Aliases</span><span class="sxs-lookup"><span data-stu-id="9903c-245">about_Aliases</span></span>](../Microsoft.PowerShell.Core/About/about_Aliases.md)

[<span data-ttu-id="9903c-246">about_Automatic_Variables. md</span><span class="sxs-lookup"><span data-stu-id="9903c-246">about_Automatic_Variables.md</span></span>](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

[<span data-ttu-id="9903c-247">about_Providers</span><span class="sxs-lookup"><span data-stu-id="9903c-247">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="9903c-248">Add-Content</span><span class="sxs-lookup"><span data-stu-id="9903c-248">Add-Content</span></span>](Add-Content.md)

[<span data-ttu-id="9903c-249">Clear-Content</span><span class="sxs-lookup"><span data-stu-id="9903c-249">Clear-Content</span></span>](Clear-Content.md)

[<span data-ttu-id="9903c-250">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="9903c-250">Get-ChildItem</span></span>](Get-ChildItem.md)

[<span data-ttu-id="9903c-251">Get-Content</span><span class="sxs-lookup"><span data-stu-id="9903c-251">Get-Content</span></span>](Get-Content.md)

[<span data-ttu-id="9903c-252">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="9903c-252">ForEach-Object</span></span>](../Microsoft.PowerShell.Core/ForEach-Object.md)

[<span data-ttu-id="9903c-253">New-Item</span><span class="sxs-lookup"><span data-stu-id="9903c-253">New-Item</span></span>](New-Item.md)

