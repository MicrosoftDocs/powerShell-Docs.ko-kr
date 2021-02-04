---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/18/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-content?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Content
ms.openlocfilehash: b6a8d0f68717849711a794c9482e03d4ea081e1d
ms.sourcegitcommit: bf07cffb2a66dec94bf3576e197090f958701f18
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/19/2020
ms.locfileid: "97692654"
---
# <span data-ttu-id="ecccf-102">Get-Content</span><span class="sxs-lookup"><span data-stu-id="ecccf-102">Get-Content</span></span>

## <span data-ttu-id="ecccf-103">개요</span><span class="sxs-lookup"><span data-stu-id="ecccf-103">SYNOPSIS</span></span>
<span data-ttu-id="ecccf-104">지정된 위치에 있는 항목의 내용을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-104">Gets the content of the item at the specified location.</span></span>

## <span data-ttu-id="ecccf-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ecccf-105">SYNTAX</span></span>

### <span data-ttu-id="ecccf-106">Path (기본값)</span><span class="sxs-lookup"><span data-stu-id="ecccf-106">Path (Default)</span></span>

```
Get-Content [-ReadCount <Int64>] [-TotalCount <Int64>] [-Tail <Int32>] [-Path] <String[]>
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Force] [-Credential <PSCredential>]
 [-Delimiter <String>] [-Wait] [-Raw] [-Encoding <Encoding>] [-AsByteStream] [-Stream <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="ecccf-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="ecccf-107">LiteralPath</span></span>

```
Get-Content [-ReadCount <Int64>] [-TotalCount <Int64>] [-Tail <Int32>] -LiteralPath <String[]>
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Force] [-Credential <PSCredential>]
 [-Delimiter <String>] [-Wait] [-Raw] [-Encoding <Encoding>] [-AsByteStream] [-Stream <String>]
 [<CommonParameters>]
```

## <span data-ttu-id="ecccf-108">설명</span><span class="sxs-lookup"><span data-stu-id="ecccf-108">DESCRIPTION</span></span>

<span data-ttu-id="ecccf-109">`Get-Content`Cmdlet은 파일의 텍스트 또는 함수의 내용과 같이 경로에 지정 된 위치에 있는 항목의 내용을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-109">The `Get-Content` cmdlet gets the content of the item at the location specified by the path, such as the text in a file or the content of a function.</span></span> <span data-ttu-id="ecccf-110">파일의 경우 콘텐츠는 한 번에 한 줄씩 읽고 개체의 컬렉션을 반환 하며, 각 개체는 내용 줄을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-110">For files, the content is read one line at a time and returns a collection of objects, each of which represents a line of content.</span></span>

<span data-ttu-id="ecccf-111">PowerShell 3.0부터는 `Get-Content` 항목의 시작 또는 끝에서 지정 된 개수의 줄을 가져올 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-111">Beginning in PowerShell 3.0, `Get-Content` can also get a specified number of lines from the beginning or end of an item.</span></span>

## <span data-ttu-id="ecccf-112">예제</span><span class="sxs-lookup"><span data-stu-id="ecccf-112">EXAMPLES</span></span>

### <span data-ttu-id="ecccf-113">예제 1: 텍스트 파일의 내용 가져오기</span><span class="sxs-lookup"><span data-stu-id="ecccf-113">Example 1: Get the content of a text file</span></span>

<span data-ttu-id="ecccf-114">이 예제에서는 현재 디렉터리에 있는 파일의 내용을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-114">This example gets the content of a file in the current directory.</span></span> <span data-ttu-id="ecccf-115">`LineNumbers.txt`파일의 형식에 100 줄이 포함 되어 있습니다 .이 줄은 **X** 이며 여러 예제에서 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-115">The `LineNumbers.txt` file contains 100 lines in the format, **This is Line X** and is used in several examples.</span></span>

```powershell
1..100 | ForEach-Object { Add-Content -Path .\LineNumbers.txt -Value "This is line $_." }
Get-Content -Path .\LineNumbers.txt
```

```Output
This is Line 1
This is Line 2
...
This is line 99.
This is line 100.
```

<span data-ttu-id="ecccf-116">배열 값 1-100은 파이프라인에서 cmdlet으로 전송 됩니다 `ForEach-Object` .</span><span class="sxs-lookup"><span data-stu-id="ecccf-116">The array values 1-100 are sent down the pipeline to the `ForEach-Object` cmdlet.</span></span> <span data-ttu-id="ecccf-117">`ForEach-Object` cmdlet과 함께 스크립트 블록을 사용 하 여 `Add-Content` 파일을 만듭니다 `LineNumbers.txt` .</span><span class="sxs-lookup"><span data-stu-id="ecccf-117">`ForEach-Object` uses a script block with the `Add-Content` cmdlet to create the `LineNumbers.txt` file.</span></span> <span data-ttu-id="ecccf-118">변수는 `$_` 각 개체가 파이프라인 아래로 전송 될 때 배열 값을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-118">The variable `$_` represents the array values as each object is sent down the pipeline.</span></span> <span data-ttu-id="ecccf-119">`Get-Content`Cmdlet은 **Path** 매개 변수를 사용 하 여 파일을 지정 하 `LineNumbers.txt` 고 PowerShell 콘솔에 콘텐츠를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-119">The `Get-Content` cmdlet uses the **Path** parameter to specify the `LineNumbers.txt` file and displays the content in the PowerShell console.</span></span>

### <span data-ttu-id="ecccf-120">예 2: 반환 Get-Content 줄 수 제한</span><span class="sxs-lookup"><span data-stu-id="ecccf-120">Example 2: Limit the number of lines Get-Content returns</span></span>

<span data-ttu-id="ecccf-121">이 명령은 파일의 처음 5 개 줄을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-121">This command gets the first five lines of a file.</span></span> <span data-ttu-id="ecccf-122">**TotalCount** 매개 변수는 처음 5 개 줄의 콘텐츠를 가져오는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-122">The **TotalCount** parameter is used to gets the first five lines of content.</span></span> <span data-ttu-id="ecccf-123">이 예에서는 `LineNumbers.txt` 예 1에서 만든 파일을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-123">This example uses the `LineNumbers.txt` file that was created in Example 1.</span></span>

```powershell
Get-Content -Path .\LineNumbers.txt -TotalCount 5
```

```Output
This is Line 1
This is Line 2
This is Line 3
This is Line 4
This is Line 5
```

### <span data-ttu-id="ecccf-124">예제 3: 텍스트 파일에서 특정 콘텐츠 줄 가져오기</span><span class="sxs-lookup"><span data-stu-id="ecccf-124">Example 3: Get a specific line of content from a text file</span></span>

<span data-ttu-id="ecccf-125">이 명령은 파일에서 특정 개수의 줄을 가져온 다음 해당 콘텐츠의 마지막 줄만 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-125">This command gets a specific number of lines from a file and then displays only the last line of that content.</span></span> <span data-ttu-id="ecccf-126">**TotalCount** 매개 변수는 처음 25 줄의 콘텐츠를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-126">The **TotalCount** parameter gets the first 25 lines of content.</span></span> <span data-ttu-id="ecccf-127">이 예에서는 `LineNumbers.txt` 예 1에서 만든 파일을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-127">This example uses the `LineNumbers.txt` file that was created in Example 1.</span></span>

```powershell
(Get-Content -Path .\LineNumbers.txt -TotalCount 25)[-1]
```

```Output
This is Line 25
```

<span data-ttu-id="ecccf-128">`Get-Content`다음 단계로 이동 하기 전에 명령이 완료 되도록 괄호 안에 명령이 래핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-128">The `Get-Content` command is wrapped in parentheses so that the command completes before going to the next step.</span></span> <span data-ttu-id="ecccf-129">`Get-Content`줄의 배열을 반환 합니다 .이를 통해 괄호 뒤에 인덱스 표기법을 추가 하 여 특정 줄 번호를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-129">`Get-Content`returns an array of lines, this allows you to add the index notation after the parenthesis to retrieve a specific line number.</span></span> <span data-ttu-id="ecccf-130">이 경우 `[-1]` 인덱스는 검색 된 줄 25 개 줄의 반환 된 배열에서 마지막 인덱스를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-130">In this case, the `[-1]` index specifies the last index in the returned array of 25 retrieved lines.</span></span>

### <span data-ttu-id="ecccf-131">예제 4: 텍스트 파일의 마지막 줄 가져오기</span><span class="sxs-lookup"><span data-stu-id="ecccf-131">Example 4: Get the last line of a text file</span></span>

<span data-ttu-id="ecccf-132">이 명령은 파일의 첫 번째 줄과 마지막 내용의 줄을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-132">This command gets the first line and last line of content from a file.</span></span> <span data-ttu-id="ecccf-133">이 예에서는 `LineNumbers.txt` 예 1에서 만든 파일을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-133">This example uses the `LineNumbers.txt` file that was created in Example 1.</span></span>

```powershell
Get-Item -Path .\LineNumbers.txt | Get-Content -Tail 1
```

```Output
This is Line 100
```

<span data-ttu-id="ecccf-134">이 예제에서는 cmdlet을 사용 하 여 `Get-Item` 파일을 매개 변수로 파이프 할 수 있음을 보여 줍니다 `Get-Content` .</span><span class="sxs-lookup"><span data-stu-id="ecccf-134">This example uses the `Get-Item` cmdlet to demonstrate that you can pipe files into the `Get-Content` parameter.</span></span> <span data-ttu-id="ecccf-135">**Tail** 매개 변수는 파일의 마지막 줄을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-135">The **Tail** parameter gets the last line of the file.</span></span> <span data-ttu-id="ecccf-136">이 메서드는 모든 줄을 검색 하 고 인덱스 표기법을 사용 하는 것 보다 빠릅니다 `[-1]` .</span><span class="sxs-lookup"><span data-stu-id="ecccf-136">This method is faster than retrieving all of the lines and using the `[-1]` index notation.</span></span>

### <span data-ttu-id="ecccf-137">예 5: 대체 데이터 스트림의 내용 가져오기</span><span class="sxs-lookup"><span data-stu-id="ecccf-137">Example 5: Get the content of an alternate data stream</span></span>

<span data-ttu-id="ecccf-138">이 예에서는 **Stream** 매개 변수를 사용 하 여 Windows NTFS 볼륨에 저장 된 파일에 대 한 대체 데이터 스트림의 내용을 가져오는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-138">This example describes how to use the **Stream** parameter to get the content of an alternate data stream for files stored on a Windows NTFS volume.</span></span> <span data-ttu-id="ecccf-139">이 예제에서는 cmdlet을 `Set-Content` 사용 하 여 라는 파일에 샘플 콘텐츠를 만듭니다 `Stream.txt` .</span><span class="sxs-lookup"><span data-stu-id="ecccf-139">In this example, the `Set-Content` cmdlet is used to create sample content in a file named `Stream.txt`.</span></span>

```powershell
Set-Content -Path .\Stream.txt -Value 'This is the content of the Stream.txt file'
# Specify a wildcard to the Stream parameter to display all streams of the recently created file.
Get-Item -Path .\Stream.txt -Stream *
```

```Output
PSPath        : Microsoft.PowerShell.Core\FileSystem::C:\Test\Stream.txt::$DATA
PSParentPath  : Microsoft.PowerShell.Core\FileSystem::C:\Test
PSChildName   : Stream.txt::$DATA
PSDrive       : C
PSProvider    : Microsoft.PowerShell.Core\FileSystem
PSIsContainer : False
FileName      : C:\Test\Stream.txt
Stream        : :$DATA
Length        : 44
```

```powershell
# Retrieve the content of the primary, or $DATA stream.
Get-Content -Path .\Stream.txt -Stream $DATA
```

```Output
This is the content of the Stream.txt file
```

```powershell
# Use the Stream parameter of Add-Content to create a new Stream containing sample content.
Add-Content -Path .\Stream.txt -Stream NewStream -Value 'Added a stream named NewStream to Stream.txt'
# Use Get-Item to verify the stream was created.
Get-Item -Path .\Stream.txt -Stream *
```

```Output
PSPath        : Microsoft.PowerShell.Core\FileSystem::C:\Test\Stream.txt::$DATA
PSParentPath  : Microsoft.PowerShell.Core\FileSystem::C:\Test
PSChildName   : Stream.txt::$DATA
PSDrive       : C
PSProvider    : Microsoft.PowerShell.Core\FileSystem
PSIsContainer : False
FileName      : C:\Test\Stream.txt
Stream        : :$DATA
Length        : 44

PSPath        : Microsoft.PowerShell.Core\FileSystem::C:\Test\Stream.txt:NewStream
PSParentPath  : Microsoft.PowerShell.Core\FileSystem::C:\Test
PSChildName   : Stream.txt:NewStream
PSDrive       : C
PSProvider    : Microsoft.PowerShell.Core\FileSystem
PSIsContainer : False
FileName      : C:\Test\Stream.txt
Stream        : NewStream
Length        : 46
```

```powershell
# Retrieve the content of your newly created Stream.
Get-Content -Path .\Stream.txt -Stream NewStream
```

```Output
Added a stream named NewStream to Stream.txt
```

<span data-ttu-id="ecccf-140">**Stream** 매개 변수는 [FileSystem 공급자](../microsoft.powershell.core/about/about_filesystem_provider.md#stream-systemstring)의 동적 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-140">The **Stream** parameter is a dynamic parameter of the [FileSystem provider](../microsoft.powershell.core/about/about_filesystem_provider.md#stream-systemstring).</span></span>
<span data-ttu-id="ecccf-141">기본적으로는 `Get-Content` 기본 또는 스트림에서 데이터만 검색 `:$DATA` 합니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-141">By default `Get-Content` only retrieves data from the default, or `:$DATA` stream.</span></span> <span data-ttu-id="ecccf-142">**스트림은** 특성, 보안 설정 또는 기타 데이터와 같은 숨겨진 데이터를 저장 하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-142">**Streams** can be used to store hidden data such as attributes, security settings, or other data.</span></span> <span data-ttu-id="ecccf-143">자식 항목을 포함 하지 않고 디렉터리에 저장할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-143">They can also be stored on directories without being child items.</span></span>

### <span data-ttu-id="ecccf-144">예제 6: 원시 콘텐츠 가져오기</span><span class="sxs-lookup"><span data-stu-id="ecccf-144">Example 6: Get raw content</span></span>

<span data-ttu-id="ecccf-145">이 예제의 명령은 문자열 배열 대신 파일의 내용을 하나의 문자열로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-145">The commands in this example get the contents of a file as one string, instead of an array of strings.</span></span> <span data-ttu-id="ecccf-146">기본적으로 **원시** 동적 매개 변수를 사용 하지 않으면 콘텐츠는 줄 바꿈 구분 문자열의 배열로 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-146">By default, without the **Raw** dynamic parameter, content is returned as an array of newline-delimited strings.</span></span> <span data-ttu-id="ecccf-147">이 예제에서는 `LineNumbers.txt` 예제에서 만든 파일을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-147">This example uses the `LineNumbers.txt` file that was created in Example</span></span>
1.

```powershell
$raw = Get-Content -Path .\LineNumbers.txt -Raw
$lines = Get-Content -Path .\LineNumbers.txt
Write-Host "Raw contains $($raw.Count) lines."
Write-Host "Lines contains $($lines.Count) lines."
```

```Output
Raw contains 1 lines.
Lines contains 100 lines.
```

### <span data-ttu-id="ecccf-148">예 7: Get-Content에서 필터 사용</span><span class="sxs-lookup"><span data-stu-id="ecccf-148">Example 7: Use Filters with Get-Content</span></span>

<span data-ttu-id="ecccf-149">Cmdlet에 대 한 필터를 지정할 수 있습니다 `Get-Content` .</span><span class="sxs-lookup"><span data-stu-id="ecccf-149">You can specify a filter to the `Get-Content` cmdlet.</span></span> <span data-ttu-id="ecccf-150">필터를 사용 하 여 **path** 매개 변수를 한 정하는 경우 후행 별표 ()를 포함 하 여 `*` 경로의 내용을 나타내야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-150">When using filters to qualify the **Path** parameter, you need to include a trailing asterisk (`*`) to indicate the contents of the path.</span></span>

<span data-ttu-id="ecccf-151">다음 명령은 `*.log` 디렉터리에 있는 모든 파일의 내용을 가져옵니다 `C:\Temp` .</span><span class="sxs-lookup"><span data-stu-id="ecccf-151">The following command gets the content of all `*.log` files in the `C:\Temp` directory.</span></span>

```powershell
Get-Content -Path C:\Temp\* -Filter *.log
```

### <span data-ttu-id="ecccf-152">예 8: 파일 콘텐츠를 바이트 배열로 가져오기</span><span class="sxs-lookup"><span data-stu-id="ecccf-152">Example 8: Get file contents as a byte array</span></span>

<span data-ttu-id="ecccf-153">이 예제에서는 파일의 내용을 단일 개체로 가져오는 방법을 보여 줍니다 `[byte[]]` .</span><span class="sxs-lookup"><span data-stu-id="ecccf-153">This example demonstrates how to get the contents of a file as a `[byte[]]` as a single object.</span></span>

```powershell
$byteArray = Get-Content -Path C:\temp\test.txt -AsByteStream -Raw
Get-Member -InputObject $bytearray
```

```Output
   TypeName: System.Byte[]

Name           MemberType            Definition
----           ----------            ----------
Count          AliasProperty         Count = Length
Add            Method                int IList.Add(System.Object value)
```

<span data-ttu-id="ecccf-154">첫 번째 명령은 **AsByteStream** 매개 변수를 사용 하 여 파일에서 바이트 스트림을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-154">The first command uses the **AsByteStream** parameter to get the stream of bytes from the file.</span></span>
<span data-ttu-id="ecccf-155">**원시** 매개 변수는 바이트가로 반환 되도록 `[System.Byte[]]` 합니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-155">The **Raw** parameter ensures that the bytes are returned as a `[System.Byte[]]`.</span></span> <span data-ttu-id="ecccf-156">**원시** 매개 변수가 없는 경우 반환 값은 바이트 스트림으로 서 PowerShell에서로 해석 됩니다 `[System.Object[]]` .</span><span class="sxs-lookup"><span data-stu-id="ecccf-156">If the **Raw** parameter was absent, the return value is a stream of bytes, which is interpreted by PowerShell as `[System.Object[]]`.</span></span>

## <span data-ttu-id="ecccf-157">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ecccf-157">PARAMETERS</span></span>

### <span data-ttu-id="ecccf-158">-Path</span><span class="sxs-lookup"><span data-stu-id="ecccf-158">-Path</span></span>

<span data-ttu-id="ecccf-159">가 콘텐츠를 가져오는 항목의 경로를 지정 합니다 `Get-Content` .</span><span class="sxs-lookup"><span data-stu-id="ecccf-159">Specifies the path to an item where `Get-Content` gets the content.</span></span> <span data-ttu-id="ecccf-160">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-160">Wildcard characters are permitted.</span></span> <span data-ttu-id="ecccf-161">경로는 컨테이너가 아니라 항목의 경로여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-161">The paths must be paths to items, not to containers.</span></span> <span data-ttu-id="ecccf-162">예를 들어 디렉터리의 경로가 아니라 하나 이상의 파일 경로를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-162">For example, you must specify a path to one or more files, not a path to a directory.</span></span>

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

### <span data-ttu-id="ecccf-163">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="ecccf-163">-LiteralPath</span></span>

<span data-ttu-id="ecccf-164">하나 이상의 위치에 대한 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-164">Specifies a path to one or more locations.</span></span> <span data-ttu-id="ecccf-165">**LiteralPath** 의 값은 입력 한 대로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-165">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="ecccf-166">어떠한 문자도 와일드카드로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-166">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="ecccf-167">이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요.</span><span class="sxs-lookup"><span data-stu-id="ecccf-167">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="ecccf-168">작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-168">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="ecccf-169">자세한 내용은 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ecccf-169">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="ecccf-170">-ReadCount</span><span class="sxs-lookup"><span data-stu-id="ecccf-170">-ReadCount</span></span>

<span data-ttu-id="ecccf-171">파이프라인을 통해 한 번에 보낼 내용의 줄 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-171">Specifies how many lines of content are sent through the pipeline at a time.</span></span> <span data-ttu-id="ecccf-172">기본값은 1입니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-172">The default value is 1.</span></span>
<span data-ttu-id="ecccf-173">값 0은 한 번에 모든 내용을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-173">A value of 0 (zero) sends all of the content at one time.</span></span>

<span data-ttu-id="ecccf-174">이 매개 변수는 표시되는 내용을 변경하는 대신 내용을 표시하는 데 걸리는 시간에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-174">This parameter does not change the content displayed, but it does affect the time it takes to display the content.</span></span> <span data-ttu-id="ecccf-175">**ReadCount** 값이 증가하면 첫 번째 줄을 반환하는 데 걸리는 시간이 증가하지만 전체 작업 시간은 감소합니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-175">As the value of **ReadCount** increases, the time it takes to return the first line increases, but the total time for the operation decreases.</span></span> <span data-ttu-id="ecccf-176">이렇게 하면 큰 항목에 크게 차이가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-176">This can make a perceptible difference in large items.</span></span>

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 1
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ecccf-177">-TotalCount</span><span class="sxs-lookup"><span data-stu-id="ecccf-177">-TotalCount</span></span>

<span data-ttu-id="ecccf-178">파일이 나 다른 항목의 시작 부분에서 줄 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-178">Specifies the number of lines from the beginning of a file or other item.</span></span> <span data-ttu-id="ecccf-179">기본값은 -1(모든 줄)입니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-179">The default is -1 (all lines).</span></span>

<span data-ttu-id="ecccf-180">**TotalCount** 매개 변수 이름 또는 해당 별칭 ( **First** 또는 **Head**)을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-180">You can use the **TotalCount** parameter name or its aliases, **First** or **Head**.</span></span>

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases: First, Head

Required: False
Position: Named
Default value: -1
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ecccf-181">-Tail</span><span class="sxs-lookup"><span data-stu-id="ecccf-181">-Tail</span></span>

<span data-ttu-id="ecccf-182">파일이 나 다른 항목의 끝에서 줄 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-182">Specifies the number of lines from the end of a file or other item.</span></span> <span data-ttu-id="ecccf-183">**Tail** 매개 변수 이름 또는 해당 별칭 ( **Last**)을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-183">You can use the **Tail** parameter name or its alias, **Last**.</span></span> <span data-ttu-id="ecccf-184">이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-184">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: Last

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ecccf-185">-Filter</span><span class="sxs-lookup"><span data-stu-id="ecccf-185">-Filter</span></span>

<span data-ttu-id="ecccf-186">**Path** 매개 변수를 한정 하는 필터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-186">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="ecccf-187">[FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) 공급자는 필터 사용을 지 원하는 유일한 설치 된 PowerShell 공급자입니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-187">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="ecccf-188">[About_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)에서 **FileSystem** 필터 언어의 구문을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-188">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="ecccf-189">필터는 다른 매개 변수 보다 더 효율적입니다. cmdlet이 개체가 검색 된 후 개체를 필터링 하는 대신 개체를 가져올 때 해당 개체를 적용 하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-189">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="ecccf-190">-포함</span><span class="sxs-lookup"><span data-stu-id="ecccf-190">-Include</span></span>

<span data-ttu-id="ecccf-191">이 cmdlet이 작업에 포함 하는 항목 또는 항목을 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-191">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="ecccf-192">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-192">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="ecccf-193">경로 요소 또는 패턴 (예:)을 입력 `"*.txt"` 합니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-193">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="ecccf-194">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-194">Wildcard characters are permitted.</span></span> <span data-ttu-id="ecccf-195">**Include** 매개 변수는 명령에와 같이 항목의 내용이 포함 된 경우에만 적용 됩니다 `C:\Windows\*` . 여기서 와일드 카드 문자는 디렉터리의 내용을 지정 합니다 `C:\Windows` .</span><span class="sxs-lookup"><span data-stu-id="ecccf-195">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="ecccf-196">-제외</span><span class="sxs-lookup"><span data-stu-id="ecccf-196">-Exclude</span></span>

<span data-ttu-id="ecccf-197">이 cmdlet이 작업에서 제외 하는 항목을 문자열 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-197">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span>
<span data-ttu-id="ecccf-198">이 매개 변수 값은 **Path** 매개 변수를 한정합니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-198">The value of this parameter qualifies the **Path** parameter.</span></span>

<span data-ttu-id="ecccf-199">경로 요소 또는 패턴 (예:)을 입력 `*.txt` 합니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-199">Enter a path element or pattern, such as `*.txt`.</span></span>
<span data-ttu-id="ecccf-200">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-200">Wildcard characters are permitted.</span></span>

<span data-ttu-id="ecccf-201">**Exclude** 매개 변수는 명령에와 같이 항목의 내용이 포함 된 경우에만 적용 됩니다 `C:\Windows\*` . 여기서 와일드 카드 문자는 디렉터리의 내용을 지정 합니다 `C:\Windows` .</span><span class="sxs-lookup"><span data-stu-id="ecccf-201">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="ecccf-202">-Force</span><span class="sxs-lookup"><span data-stu-id="ecccf-202">-Force</span></span>

<span data-ttu-id="ecccf-203">**Force** 는 읽기 전용 특성을 재정의 하거나 디렉터리를 만들어 파일 경로를 완성 합니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-203">**Force** will override a read-only attribute or create directories to complete a file path.</span></span> <span data-ttu-id="ecccf-204">**Force** 매개 변수는 파일 사용 권한을 변경 하거나 보안 제한을 재정의 하려고 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-204">The **Force** parameter does not attempt to change file permissions or override security restrictions.</span></span>

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

### <span data-ttu-id="ecccf-205">-Credential</span><span class="sxs-lookup"><span data-stu-id="ecccf-205">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="ecccf-206">이 매개 변수는 PowerShell과 함께 설치 된 모든 공급자에서 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-206">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="ecccf-207">이 cmdlet을 실행할 때 다른 사용자를 가장 하거나 자격 증명을 상승 시키려면 [Invoke 명령을](../Microsoft.PowerShell.Core/Invoke-Command.md)사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-207">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ecccf-208">-구분 기호</span><span class="sxs-lookup"><span data-stu-id="ecccf-208">-Delimiter</span></span>

<span data-ttu-id="ecccf-209">`Get-Content`에서 읽는 동안 파일을 개체로 나누는 데 사용 하는 구분 기호를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-209">Specifies the delimiter that `Get-Content` uses to divide the file into objects while it reads.</span></span> <span data-ttu-id="ecccf-210">기본값은 `\n` 줄 끝 문자입니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-210">The default is `\n`, the end-of-line character.</span></span> <span data-ttu-id="ecccf-211">텍스트 파일을 읽을 때는 `Get-Content` 각각 줄 끝 문자로 끝나는 문자열 개체의 컬렉션을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-211">When reading a text file, `Get-Content` returns a collection of string objects, each of which ends with an end-of-line character.</span></span> <span data-ttu-id="ecccf-212">파일에 존재 하지 않는 구분 기호를 입력 하면는 `Get-Content` 전체 파일을 구분 되지 않은 단일 개체로 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-212">When you enter a delimiter that does not exist in the file, `Get-Content` returns the entire file as a single, undelimited object.</span></span>

<span data-ttu-id="ecccf-213">이 매개 변수를 사용 하 여 파일 구분 기호를 구분 기호로 지정 하 여 많은 파일을 더 작은 파일로 분할할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-213">You can use this parameter to split a large file into smaller files by specifying a file separator, as the delimiter.</span></span> <span data-ttu-id="ecccf-214">구분 기호는 보존되고(삭제되지 않음) 각 파일 섹션의 마지막 항목이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-214">The delimiter is preserved (not discarded) and becomes the last item in each file section.</span></span>

<span data-ttu-id="ecccf-215">**Delimiter** 는 **파일 시스템** 공급자가 cmdlet에 추가 하는 동적 매개 변수입니다 `Get-Content` .</span><span class="sxs-lookup"><span data-stu-id="ecccf-215">**Delimiter** is a dynamic parameter that the **FileSystem** provider adds to the `Get-Content` cmdlet.</span></span> <span data-ttu-id="ecccf-216">이 매개 변수는 파일 시스템 드라이브에만 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-216">This parameter works only in file system drives.</span></span>

> [!NOTE]
> <span data-ttu-id="ecccf-217">현재 **구분 기호** 매개 변수 값이 빈 문자열인 경우는 `Get-Content` 아무것도 반환 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-217">Currently, when the value of the **Delimiter** parameter is an empty string, `Get-Content` does not return anything.</span></span> <span data-ttu-id="ecccf-218">이것은 알려진 문제입니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-218">This is a known issue.</span></span> <span data-ttu-id="ecccf-219">를 적용 하 여 `Get-Content` 전체 파일을 구분 되지 않은 단일 문자열로 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-219">To force `Get-Content` to return the entire file as a single, undelimited string.</span></span> <span data-ttu-id="ecccf-220">파일에 존재 하지 않는 값을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-220">Enter a value that does not exist in the file.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: End-of-line character
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ecccf-221">-Wait</span><span class="sxs-lookup"><span data-stu-id="ecccf-221">-Wait</span></span>

<span data-ttu-id="ecccf-222">모든 기존 줄이 출력 된 후 파일을 열어 둡니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-222">Keeps the file open after all existing lines have been output.</span></span> <span data-ttu-id="ecccf-223">대기 하는 동안는 `Get-Content` 초당 파일을 확인 하 고 새 줄 (있는 경우)을 출력 합니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-223">While waiting, `Get-Content` checks the file once each second and outputs new lines if present.</span></span> <span data-ttu-id="ecccf-224">**Ctrl + C** 를 눌러 **Wait** 를 중단할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-224">You can interrupt **Wait** by pressing **CTRL+C**.</span></span> <span data-ttu-id="ecccf-225">파일이 삭제 되 면 대기가 종료 되 고,이 경우 종료 되지 않는 오류가 보고 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-225">Waiting also ends if the file gets deleted, in which case a non-terminating error is reported.</span></span>

<span data-ttu-id="ecccf-226">**Wait** 는 파일 시스템 공급자가 cmdlet에 추가 하는 동적 매개 변수입니다 `Get-Content` .</span><span class="sxs-lookup"><span data-stu-id="ecccf-226">**Wait** is a dynamic parameter that the FileSystem provider adds to the `Get-Content` cmdlet.</span></span> <span data-ttu-id="ecccf-227">이 매개 변수는 파일 시스템 드라이브에만 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-227">This parameter works only in file system drives.</span></span> <span data-ttu-id="ecccf-228">**Wait** 는 **Raw** 와 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-228">**Wait** cannot be combined with **Raw**.</span></span>

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

### <span data-ttu-id="ecccf-229">-Raw</span><span class="sxs-lookup"><span data-stu-id="ecccf-229">-Raw</span></span>

<span data-ttu-id="ecccf-230">줄 바꿈 문자를 무시 하 고 줄바꿈가 유지 된 상태로 파일의 전체 내용을 하나의 문자열로 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-230">Ignores newline characters and returns the entire contents of a file in one string with the newlines preserved.</span></span> <span data-ttu-id="ecccf-231">기본적으로 파일의 줄 바꿈 문자는 입력을 문자열 배열로 구분 하는 구분 기호로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-231">By default, newline characters in a file are used as delimiters to separate the input into an array of strings.</span></span> <span data-ttu-id="ecccf-232">이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-232">This parameter was introduced in PowerShell 3.0.</span></span>

<span data-ttu-id="ecccf-233">**Raw** 는 **FileSystem** 공급자가 cmdlet에 추가 하는 동적 매개 변수입니다 `Get-Content` .이 매개 변수는 파일 시스템 드라이브 에서만 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-233">**Raw** is a dynamic parameter that the **FileSystem** provider adds to the `Get-Content` cmdlet This parameter works only in file system drives.</span></span>

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

### <span data-ttu-id="ecccf-234">-Encoding</span><span class="sxs-lookup"><span data-stu-id="ecccf-234">-Encoding</span></span>

<span data-ttu-id="ecccf-235">대상 파일의 인코딩 유형을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-235">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="ecccf-236">기본값은 `utf8NoBOM`입니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-236">The default value is `utf8NoBOM`.</span></span>

<span data-ttu-id="ecccf-237">이 매개 변수에 허용 되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-237">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="ecccf-238">`ascii`: ASCII (7 비트) 문자 집합에 대 한 인코딩을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-238">`ascii`: Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="ecccf-239">`bigendianunicode`: 빅 endian 바이트 순서를 사용 하 여 UTF-16 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-239">`bigendianunicode`: Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="ecccf-240">`bigendianutf32`: 빅 endian 바이트 순서를 사용 하 여 u t f-32 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-240">`bigendianutf32`: Encodes in UTF-32 format using the big-endian byte order.</span></span>
- <span data-ttu-id="ecccf-241">`oem`: MS-DOS 및 콘솔 프로그램에 기본 인코딩을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-241">`oem`: Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="ecccf-242">`unicode`: 작은 endian 바이트 순서를 사용 하 여 UTF-16 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-242">`unicode`: Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="ecccf-243">`utf7`: UTF-7 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-243">`utf7`: Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="ecccf-244">`utf8`: UTF-8 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-244">`utf8`: Encodes in UTF-8 format.</span></span>
- <span data-ttu-id="ecccf-245">`utf8BOM`: 바이트 순서 표시 (BOM)를 사용 하 여 UTF-8 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-245">`utf8BOM`: Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="ecccf-246">`utf8NoBOM`: BOM (바이트 순서 표시) 없이 UTF-8 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-246">`utf8NoBOM`: Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="ecccf-247">`utf32`: U t f-32 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-247">`utf32`: Encodes in UTF-32 format.</span></span>

<span data-ttu-id="ecccf-248">Encoding은 **파일 시스템** 공급자가 cmdlet에 추가 하는 동적 매개 변수입니다 `Get-Content` .</span><span class="sxs-lookup"><span data-stu-id="ecccf-248">Encoding is a dynamic parameter that the **FileSystem** provider adds to the `Get-Content` cmdlet.</span></span>
<span data-ttu-id="ecccf-249">이 매개 변수는 파일 시스템 드라이브 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-249">This parameter is available only in file system drives.</span></span>

<span data-ttu-id="ecccf-250">이진 파일을 읽고 이진 파일에 쓸 때 **AsByteStream** 매개 변수를 사용 하 고 **readcount** 매개 변수에 0 값을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-250">When reading from and writing to binary files, use the **AsByteStream** parameter and a value of 0 for the **ReadCount** parameter.</span></span> <span data-ttu-id="ecccf-251">**Readcount** 값이 0 이면 단일 읽기 작업에서 전체 파일을 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-251">A **ReadCount** value of 0 reads the entire file in a single read operation.</span></span> <span data-ttu-id="ecccf-252">기본 **Readcount** 값인 1은 각 읽기 작업에서 1 바이트를 읽고 각 바이트를 별도의 개체로 변환 합니다. 이렇게 하면 `Set-Content` **AsByteStream** 매개 변수를 사용 하지 않는 한 cmdlet을 사용 하 여 파일에 바이트를 쓸 때 오류가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-252">The default **ReadCount** value, 1, reads one byte in each read operation and converts each byte into a separate object, which causes errors when you use the `Set-Content` cmdlet to write the bytes to a file unless you use **AsByteStream** parameter.</span></span>

<span data-ttu-id="ecccf-253">PowerShell 6.2부터 **Encoding** 매개 변수를 사용 하 여 등록 된 코드 페이지의 숫자 id (예: `-Encoding 1251` ) 또는 등록 된 코드 페이지의 문자열 이름을 사용할 수도 있습니다 (예: `-Encoding "windows-1251"` ).</span><span class="sxs-lookup"><span data-stu-id="ecccf-253">Beginning with PowerShell 6.2, the **Encoding** parameter also allows numeric IDs of registered code pages (like `-Encoding 1251`) or string names of registered code pages (like `-Encoding "windows-1251"`).</span></span> <span data-ttu-id="ecccf-254">자세한 내용은 [인코딩에](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2)대 한 .net 설명서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ecccf-254">For more information, see the .NET documentation for [Encoding.CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span></span>

> [!NOTE]
> <span data-ttu-id="ecccf-255">**U t f-7** _은 더 이상 사용 하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-255">**UTF-7** _ is no longer recommended to use.</span></span> <span data-ttu-id="ecccf-256">PowerShell 7.1에서는 `utf7` _ *Encoding*\* 매개 변수에 대해를 지정 하는 경우 경고가 기록 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-256">In PowerShell 7.1, a warning is written if you specify `utf7` for the _ *Encoding*\* parameter.</span></span>

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

### <span data-ttu-id="ecccf-257">-스트림</span><span class="sxs-lookup"><span data-stu-id="ecccf-257">-Stream</span></span>

> [!NOTE]
> <span data-ttu-id="ecccf-258">이 매개 변수는 Windows 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-258">This Parameter is only available on Windows.</span></span>

<span data-ttu-id="ecccf-259">파일에서 지정된 대체 NTFS 파일 스트림의 내용을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-259">Gets the contents of the specified alternate NTFS file stream from the file.</span></span> <span data-ttu-id="ecccf-260">스트림 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-260">Enter the stream name.</span></span>
<span data-ttu-id="ecccf-261">와일드카드는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-261">Wildcards are not supported.</span></span>

<span data-ttu-id="ecccf-262">**스트림은** **파일 시스템** 공급자가 cmdlet에 추가 하는 동적 매개 변수입니다 `Get-Content` .</span><span class="sxs-lookup"><span data-stu-id="ecccf-262">**Stream** is a dynamic parameter that the **FileSystem** provider adds to the `Get-Content` cmdlet.</span></span>
<span data-ttu-id="ecccf-263">이 매개 변수는 Windows 시스템의 파일 시스템 드라이브 에서만 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-263">This parameter works only in file system drives on Windows systems.</span></span> <span data-ttu-id="ecccf-264">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-264">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="ecccf-265">-AsByteStream</span><span class="sxs-lookup"><span data-stu-id="ecccf-265">-AsByteStream</span></span>

<span data-ttu-id="ecccf-266">콘텐츠를 바이트 스트림으로 읽도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-266">Specifies that the content should be read as a stream of bytes.</span></span> <span data-ttu-id="ecccf-267">**AsByteStream** 매개 변수는 Windows PowerShell 6.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-267">The **AsByteStream** parameter was introduced in Windows PowerShell 6.0.</span></span>

<span data-ttu-id="ecccf-268">**AsByteStream** 매개 변수를 **Encoding** 매개 변수와 함께 사용 하는 경우 경고가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-268">A warning occurs when you use the **AsByteStream** parameter with the **Encoding** parameter.</span></span> <span data-ttu-id="ecccf-269">**AsByteStream** 매개 변수는 인코딩을 무시 하 고 출력은 바이트 스트림으로 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-269">The **AsByteStream** parameter ignores any encoding and the output is returned as a stream of bytes.</span></span>

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

### <span data-ttu-id="ecccf-270">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ecccf-270">CommonParameters</span></span>

<span data-ttu-id="ecccf-271">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ecccf-271">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ecccf-272">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ecccf-272">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ecccf-273">입력</span><span class="sxs-lookup"><span data-stu-id="ecccf-273">INPUTS</span></span>

### <span data-ttu-id="ecccf-274">System.Int64, System.String[], System.Management.Automation.PSCredential</span><span class="sxs-lookup"><span data-stu-id="ecccf-274">System.Int64, System.String[], System.Management.Automation.PSCredential</span></span>

<span data-ttu-id="ecccf-275">읽기 수, 총 개수, 경로 또는 자격 증명을로 파이프 할 수 있습니다 `Get-Content` .</span><span class="sxs-lookup"><span data-stu-id="ecccf-275">You can pipe the read count, total count, paths, or credentials to `Get-Content`.</span></span>

## <span data-ttu-id="ecccf-276">출력</span><span class="sxs-lookup"><span data-stu-id="ecccf-276">OUTPUTS</span></span>

### <span data-ttu-id="ecccf-277">System.string, System.string</span><span class="sxs-lookup"><span data-stu-id="ecccf-277">System.Byte, System.String</span></span>

<span data-ttu-id="ecccf-278">`Get-Content` 문자열 또는 바이트를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-278">`Get-Content` returns strings or bytes.</span></span> <span data-ttu-id="ecccf-279">출력 형식은 입력으로 지정 하는 콘텐츠 형식에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-279">The output type depends upon the type of content that you specify as input.</span></span>

## <span data-ttu-id="ecccf-280">참고</span><span class="sxs-lookup"><span data-stu-id="ecccf-280">NOTES</span></span>

<span data-ttu-id="ecccf-281">`Get-Content`Cmdlet은 모든 공급자가 제공 하는 데이터에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ecccf-281">The `Get-Content` cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="ecccf-282">세션에서 공급자를 가져오려면 cmdlet을 사용 합니다 `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="ecccf-282">To get the providers in your session, use the `Get-PSProvider` cmdlet.</span></span> <span data-ttu-id="ecccf-283">자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ecccf-283">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="ecccf-284">관련 링크</span><span class="sxs-lookup"><span data-stu-id="ecccf-284">RELATED LINKS</span></span>

[<span data-ttu-id="ecccf-285">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="ecccf-285">about_Automatic_Variables</span></span>](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

[<span data-ttu-id="ecccf-286">about_Providers</span><span class="sxs-lookup"><span data-stu-id="ecccf-286">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="ecccf-287">Add-Content</span><span class="sxs-lookup"><span data-stu-id="ecccf-287">Add-Content</span></span>](Add-Content.md)

[<span data-ttu-id="ecccf-288">Clear-Content</span><span class="sxs-lookup"><span data-stu-id="ecccf-288">Clear-Content</span></span>](Clear-Content.md)

[<span data-ttu-id="ecccf-289">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="ecccf-289">ForEach-Object</span></span>](../Microsoft.PowerShell.Core/ForEach-Object.md)

[<span data-ttu-id="ecccf-290">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="ecccf-290">Get-PSProvider</span></span>](Get-PSProvider.md)

[<span data-ttu-id="ecccf-291">Set-Content</span><span class="sxs-lookup"><span data-stu-id="ecccf-291">Set-Content</span></span>](Set-Content.md)
