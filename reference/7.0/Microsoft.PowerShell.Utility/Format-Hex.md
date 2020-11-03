---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 01/17/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-hex?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-Hex
ms.openlocfilehash: 6cb02f1c6f2583ce4146356fac3553e99a54c7c2
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93211033"
---
# <span data-ttu-id="83f5a-103">Format-Hex</span><span class="sxs-lookup"><span data-stu-id="83f5a-103">Format-Hex</span></span>

## <span data-ttu-id="83f5a-104">개요</span><span class="sxs-lookup"><span data-stu-id="83f5a-104">SYNOPSIS</span></span>

<span data-ttu-id="83f5a-105">파일이 나 기타 입력을 16 진수로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="83f5a-105">Displays a file or other input as hexadecimal.</span></span>

## <span data-ttu-id="83f5a-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="83f5a-106">SYNTAX</span></span>

### <span data-ttu-id="83f5a-107">Path (기본값)</span><span class="sxs-lookup"><span data-stu-id="83f5a-107">Path (Default)</span></span>

```
Format-Hex [-Path] <String[]> [-Count <Int64>] [-Offset <Int64>] [<CommonParameters>]
```

### <span data-ttu-id="83f5a-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="83f5a-108">LiteralPath</span></span>

```
Format-Hex -LiteralPath <String[]> [-Count <Int64>] [-Offset <Int64>] [<CommonParameters>]
```

### <span data-ttu-id="83f5a-109">ByInputObject</span><span class="sxs-lookup"><span data-stu-id="83f5a-109">ByInputObject</span></span>
```
Format-Hex -InputObject <PSObject> [-Encoding <Encoding>] [-Count <Int64>] [-Offset <Int64>] [-Raw]
 [<CommonParameters>]
```

## <span data-ttu-id="83f5a-110">설명</span><span class="sxs-lookup"><span data-stu-id="83f5a-110">DESCRIPTION</span></span>

<span data-ttu-id="83f5a-111">`Format-Hex`Cmdlet은 파일 또는 기타 입력을 16 진수 값으로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="83f5a-111">The `Format-Hex` cmdlet displays a file or other input as hexadecimal values.</span></span> <span data-ttu-id="83f5a-112">출력에서 문자의 오프셋을 확인 하려면 행의 맨 왼쪽에 있는 숫자를 해당 문자의 열 위쪽에 있는 숫자에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="83f5a-112">To determine the offset of a character from the output, add the number at the leftmost of the row to the number at the top of the column for that character.</span></span>

<span data-ttu-id="83f5a-113">Cmdlet을 통해 `Format-Hex` 손상 된 파일이 나 파일 이름 확장명을 가질 수 없는 파일의 파일 형식을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83f5a-113">The `Format-Hex` cmdlet can help you determine the file type of a corrupted file or a file that might not have a filename extension.</span></span> <span data-ttu-id="83f5a-114">이 cmdlet을 실행 한 다음 16 진수 출력을 읽어 파일 정보를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83f5a-114">You can run this cmdlet, and then read the hexadecimal output to get file information.</span></span>

<span data-ttu-id="83f5a-115">파일에서를 사용 하 `Format-Hex` 는 경우이 cmdlet은 줄 바꿈 문자를 무시 하 고 파일의 전체 내용을 줄 바꿈 문자가 유지 된 한 문자열로 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="83f5a-115">When using `Format-Hex` on a file, the cmdlet ignores newline characters and returns the entire contents of a file in one string with the newline characters preserved.</span></span>

## <span data-ttu-id="83f5a-116">예제</span><span class="sxs-lookup"><span data-stu-id="83f5a-116">EXAMPLES</span></span>

### <span data-ttu-id="83f5a-117">예제 1: 문자열의 16 진수 표현 가져오기</span><span class="sxs-lookup"><span data-stu-id="83f5a-117">Example 1: Get the hexadecimal representation of a string</span></span>

<span data-ttu-id="83f5a-118">이 명령은 문자열의 16 진수 값을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="83f5a-118">This command returns the hexadecimal values of a string.</span></span>

```powershell
'Hello World' | Format-Hex
```

```Output
   Label: String (System.String) <2944BEC3>

          Offset Bytes                                           Ascii
                 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
          ------ ----------------------------------------------- -----
0000000000000000 48 65 6C 6C 6F 20 57 6F 72 6C 64                Hello World
```

<span data-ttu-id="83f5a-119">**Hello World** 문자열은 파이프라인에서 cmdlet으로 전송 됩니다 `Format-Hex` .</span><span class="sxs-lookup"><span data-stu-id="83f5a-119">The string **Hello World** is sent down the pipeline to the `Format-Hex` cmdlet.</span></span> <span data-ttu-id="83f5a-120">의 16 진수 출력은 `Format-Hex` 문자열의 각 문자 값을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="83f5a-120">The hexadecimal output from `Format-Hex` shows the values of each character in the string.</span></span>

### <span data-ttu-id="83f5a-121">예 2:16 진수 출력에서 파일 형식 찾기</span><span class="sxs-lookup"><span data-stu-id="83f5a-121">Example 2: Find a file type from hexadecimal output</span></span>

<span data-ttu-id="83f5a-122">이 예제에서는 16 진수 출력을 사용 하 여 파일 형식을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="83f5a-122">This example uses the hexadecimal output to determine the file type.</span></span> <span data-ttu-id="83f5a-123">Cmdlet은 파일의 전체 경로와 16 진수 값을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="83f5a-123">The cmdlet displays the file's full path and the hexadecimal values.</span></span>

<span data-ttu-id="83f5a-124">다음 명령을 테스트 하려면 로컬 컴퓨터에 기존 PDF 파일의 복사본을 만들고 복사한 파일의 이름을로 바꿉니다 `File.t7f` .</span><span class="sxs-lookup"><span data-stu-id="83f5a-124">To test the following command, make a copy of an existing PDF file on your local computer and rename the copied file to `File.t7f`.</span></span>

```powershell
Format-Hex -Path .\File.t7f -Count 48
```

```Output
   Label: C:\Test\File.t7f

          Offset Bytes                                           Ascii
                 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
          ------ ----------------------------------------------- -----
0000000000000000 25 50 44 46 2D 31 2E 35 0D 0A 25 B5 B5 B5 B5 0D %PDF-1.5..%????.
0000000000000010 0A 31 20 30 20 6F 62 6A 0D 0A 3C 3C 2F 54 79 70 .1 0 obj..<</Typ
0000000000000020 65 2F 43 61 74 61 6C 6F 67 2F 50 61 67 65 73 20 e/Catalog/Pages
```

<span data-ttu-id="83f5a-125">`Format-Hex`Cmdlet은 **Path** 매개 변수를 사용 하 여 현재 디렉터리의 파일 이름을 지정 `File.t7f` 합니다.</span><span class="sxs-lookup"><span data-stu-id="83f5a-125">The `Format-Hex` cmdlet uses the **Path** parameter to specify a filename in the current directory, `File.t7f`.</span></span> <span data-ttu-id="83f5a-126">파일 확장명은 `.t7f` 일반적이 지 않지만 16 진수 출력은 `%PDF` PDF 파일 임을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="83f5a-126">The file extension `.t7f` is uncommon, but the hexadecimal output `%PDF` shows that it is a PDF file.</span></span> <span data-ttu-id="83f5a-127">이 예에서는 **Count** 매개 변수를 사용 하 여 출력을 파일의 처음 48 바이트로 제한 합니다.</span><span class="sxs-lookup"><span data-stu-id="83f5a-127">In this example, the **Count** parameter is used to limit the output to the first 48 bytes of the file.</span></span>

### <span data-ttu-id="83f5a-128">예제 3: 다른 데이터 형식의 배열 서식 지정</span><span class="sxs-lookup"><span data-stu-id="83f5a-128">Example 3: Format an array of different data types</span></span>

<span data-ttu-id="83f5a-129">이 예제에서는 다양 한 데이터 형식의 배열을 사용 하 여가 파이프라인에서 처리 하는 방법을 강조 표시 `Format-Hex` 합니다.</span><span class="sxs-lookup"><span data-stu-id="83f5a-129">This example uses an array of different data types to highlight how `Format-Hex` handles them in the Pipeline.</span></span>

<span data-ttu-id="83f5a-130">파이프라인 및 프로세스를 통해 각 개체를 개별적으로 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="83f5a-130">It will pass each object through the Pipeline and process individually.</span></span> <span data-ttu-id="83f5a-131">그러나 숫자 데이터이 고 인접 개체도 숫자인 경우 단일 출력 블록으로 그룹화 합니다.</span><span class="sxs-lookup"><span data-stu-id="83f5a-131">However, if it's numeric data, and the adjacent object is also numeric, it will group them into a single output block.</span></span>

```powershell
'Hello world!', 1, 1138, 'foo', 'bar', 0xdeadbeef, 1gb, 0b1101011100 , $true, $false | Format-Hex
```

```Output
   Label: String (System.String) <24F1F0A3>

          Offset Bytes                                           Ascii
                 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
          ------ ----------------------------------------------- -----
0000000000000000 48 65 6C 6C 6F 20 77 6F 72 6C 64 21             Hello world!

   Label: Int32 (System.Int32) <2EB933C5>

          Offset Bytes                                           Ascii
                 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
          ------ ----------------------------------------------- -----
0000000000000000 01 00 00 00 72 04 00 00                         �   r�

   Label: String (System.String) <4078B66C>

          Offset Bytes                                           Ascii
                 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
          ------ ----------------------------------------------- -----
0000000000000000 66 6F 6F                                        foo

   Label: String (System.String) <51E4A317>

          Offset Bytes                                           Ascii
                 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
          ------ ----------------------------------------------- -----
0000000000000000 62 61 72                                        bar

   Label: Int32 (System.Int32) <5ADF167B>

          Offset Bytes                                           Ascii
                 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
          ------ ----------------------------------------------- -----
0000000000000000 EF BE AD DE 00 00 00 40 5C 03 00 00             ï¾­Þ   @\�

   Label: Boolean (System.Boolean) <7D8C4C1D>

          Offset Bytes                                           Ascii
                 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
          ------ ----------------------------------------------- -----
0000000000000000 01 00 00 00 00 00 00 00                         �
```

## <span data-ttu-id="83f5a-132">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="83f5a-132">PARAMETERS</span></span>

### <span data-ttu-id="83f5a-133">-Encoding</span><span class="sxs-lookup"><span data-stu-id="83f5a-133">-Encoding</span></span>

<span data-ttu-id="83f5a-134">입력 문자열의 인코딩을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="83f5a-134">Specifies the encoding of the input strings.</span></span> <span data-ttu-id="83f5a-135">이는 입력에만 적용 됩니다 `[string]` .</span><span class="sxs-lookup"><span data-stu-id="83f5a-135">This only applies to `[string]` input.</span></span> <span data-ttu-id="83f5a-136">매개 변수는 숫자 형식에는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="83f5a-136">The parameter has no effect on numeric types.</span></span> <span data-ttu-id="83f5a-137">출력 값은 항상 `utf8NoBOM` 입니다.</span><span class="sxs-lookup"><span data-stu-id="83f5a-137">The output value is always `utf8NoBOM`.</span></span>

<span data-ttu-id="83f5a-138">이 매개 변수에 허용 되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="83f5a-138">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="83f5a-139">`ascii`: ASCII (7 비트) 문자 집합에 대 한 인코딩을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="83f5a-139">`ascii`: Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="83f5a-140">`bigendianunicode`: 빅 endian 바이트 순서를 사용 하 여 UTF-16 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="83f5a-140">`bigendianunicode`: Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="83f5a-141">`oem`: MS-DOS 및 콘솔 프로그램에 기본 인코딩을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="83f5a-141">`oem`: Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="83f5a-142">`unicode`: 작은 endian 바이트 순서를 사용 하 여 UTF-16 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="83f5a-142">`unicode`: Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="83f5a-143">`utf7`: UTF-7 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="83f5a-143">`utf7`: Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="83f5a-144">`utf8`: UTF-8 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="83f5a-144">`utf8`: Encodes in UTF-8 format.</span></span>
- <span data-ttu-id="83f5a-145">`utf8BOM`: 바이트 순서 표시 (BOM)를 사용 하 여 UTF-8 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="83f5a-145">`utf8BOM`: Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="83f5a-146">`utf8NoBOM`: BOM (바이트 순서 표시) 없이 UTF-8 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="83f5a-146">`utf8NoBOM`: Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="83f5a-147">`utf32`: U t f-32 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="83f5a-147">`utf32`: Encodes in UTF-32 format.</span></span>

<span data-ttu-id="83f5a-148">PowerShell 6.2부터 **Encoding** 매개 변수를 사용 하 여 등록 된 코드 페이지의 숫자 id (예: `-Encoding 1251` ) 또는 등록 된 코드 페이지의 문자열 이름을 사용할 수도 있습니다 (예: `-Encoding "windows-1251"` ).</span><span class="sxs-lookup"><span data-stu-id="83f5a-148">Beginning with PowerShell 6.2, the **Encoding** parameter also allows numeric IDs of registered code pages (like `-Encoding 1251`) or string names of registered code pages (like `-Encoding "windows-1251"`).</span></span> <span data-ttu-id="83f5a-149">자세한 내용은 [인코딩에](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2)대 한 .net 설명서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="83f5a-149">For more information, see the .NET documentation for [Encoding.CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span></span>

```yaml
Type: System.Text.Encoding
Parameter Sets: ByInputObject
Aliases:
Accepted values: ASCII, BigEndianUnicode, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: Named
Default value: UTF8NoBOM
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="83f5a-150">-InputObject</span><span class="sxs-lookup"><span data-stu-id="83f5a-150">-InputObject</span></span>

<span data-ttu-id="83f5a-151">파이프라인 입력에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="83f5a-151">Used for pipeline input.</span></span> <span data-ttu-id="83f5a-152">파이프라인 입력은 `[system.io.fileinfo]` 에서 파이프에 대 한 특정 스칼라 형식 및 인스턴스만 지원 `Get-ChildItem` 합니다.</span><span class="sxs-lookup"><span data-stu-id="83f5a-152">Pipeline input supports only certain scalar types and `[system.io.fileinfo]` instances for piping from `Get-ChildItem`.</span></span>

<span data-ttu-id="83f5a-153">지원 되는 스칼라 형식은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="83f5a-153">The supported scalar types are:</span></span>

- <span data-ttu-id="83f5a-154">`[string]`, `[char]`</span><span class="sxs-lookup"><span data-stu-id="83f5a-154">`[string]`, `[char]`</span></span>
- <span data-ttu-id="83f5a-155">`[byte]`, `[sbyte]`</span><span class="sxs-lookup"><span data-stu-id="83f5a-155">`[byte]`, `[sbyte]`</span></span>
- <span data-ttu-id="83f5a-156">`[int16]`, `[uint16]`, `[short]`, `[ushort]`</span><span class="sxs-lookup"><span data-stu-id="83f5a-156">`[int16]`, `[uint16]`, `[short]`, `[ushort]`</span></span>
- <span data-ttu-id="83f5a-157">`[int]`, `[uint]`, `[int32]`, `[uint32]`,</span><span class="sxs-lookup"><span data-stu-id="83f5a-157">`[int]`, `[uint]`, `[int32]`, `[uint32]`,</span></span>
- <span data-ttu-id="83f5a-158">`[long]`, `[ulong]`, `[int64]`, `[uint64]`</span><span class="sxs-lookup"><span data-stu-id="83f5a-158">`[long]`, `[ulong]`, `[int64]`, `[uint64]`</span></span>
- <span data-ttu-id="83f5a-159">`[single]`, `[float]`, `[double]`</span><span class="sxs-lookup"><span data-stu-id="83f5a-159">`[single]`, `[float]`, `[double]`</span></span>
- `[boolean]`

<span data-ttu-id="83f5a-160">PowerShell 6.2 이전에 `Format-Hex` 는와 같은 모든 개체를 함께 그룹화 하 여 여러 입력 형식의 파이프라인 입력을 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="83f5a-160">Prior to PowerShell 6.2, `Format-Hex` would handle a Pipeline input with multiple input types by grouping all like objects together.</span></span> <span data-ttu-id="83f5a-161">이제는 파이프라인을 통과 하는 각 개별 개체를 처리 하 고, 개체가 인접 하지 않는 한 개체를 그룹화 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="83f5a-161">Now, it handles each individual object as it passes through the Pipeline and won't group objects together unless like objects are adjacent.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: ByInputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="83f5a-162">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="83f5a-162">-LiteralPath</span></span>

<span data-ttu-id="83f5a-163">파일의 전체 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="83f5a-163">Specifies the complete path to a file.</span></span> <span data-ttu-id="83f5a-164">**LiteralPath** 의 값은 입력 한 대로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="83f5a-164">The value of **LiteralPath** is used exactly as it is typed.</span></span>
<span data-ttu-id="83f5a-165">이 매개 변수는 와일드 카드 문자를 허용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="83f5a-165">This parameter does not accept wildcard characters.</span></span> <span data-ttu-id="83f5a-166">파일에 대 한 여러 경로를 지정 하려면 경로를 쉼표로 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="83f5a-166">To specify multiple paths to files, separate the paths with a comma.</span></span> <span data-ttu-id="83f5a-167">**LiteralPath** 매개 변수에 이스케이프 문자가 포함 되어 있으면 경로를 작은따옴표로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="83f5a-167">If the **LiteralPath** parameter includes escape characters, enclose the path in single quotation marks.</span></span> <span data-ttu-id="83f5a-168">PowerShell에서는 따옴표 붙은 단일 문자열의 문자를 이스케이프 시퀀스로 해석 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="83f5a-168">PowerShell does not interpret any characters in a single quoted string as escape sequences.</span></span> <span data-ttu-id="83f5a-169">자세한 내용은 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="83f5a-169">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="83f5a-170">-Path</span><span class="sxs-lookup"><span data-stu-id="83f5a-170">-Path</span></span>

<span data-ttu-id="83f5a-171">파일의 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="83f5a-171">Specifies the path to files.</span></span> <span data-ttu-id="83f5a-172">점 ()을 사용 `.` 하 여 현재 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="83f5a-172">Use a dot (`.`) to specify the current location.</span></span> <span data-ttu-id="83f5a-173">와일드 카드 문자 ( `*` )가 허용 되며, 위치에 있는 모든 항목을 지정 하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83f5a-173">The wildcard character (`*`) is accepted and can be used to specify all the items in a location.</span></span> <span data-ttu-id="83f5a-174">**Path** 매개 변수에 이스케이프 문자가 포함 되어 있으면 경로를 작은따옴표로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="83f5a-174">If the **Path** parameter includes escape characters, enclose the path in single quotation marks.</span></span> <span data-ttu-id="83f5a-175">파일에 대 한 여러 경로를 지정 하려면 경로를 쉼표로 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="83f5a-175">To specify multiple paths to files, separate the paths with a comma.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="83f5a-176">-Raw</span><span class="sxs-lookup"><span data-stu-id="83f5a-176">-Raw</span></span>

<span data-ttu-id="83f5a-177">이 매개 변수는 더 이상 아무 작업도 수행 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="83f5a-177">This parameter no longer does anything.</span></span> <span data-ttu-id="83f5a-178">스크립트 호환성을 위해 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="83f5a-178">It is retained for script compatibility.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="83f5a-179">-오프셋</span><span class="sxs-lookup"><span data-stu-id="83f5a-179">-Offset</span></span>

<span data-ttu-id="83f5a-180">이는 16 진수 출력의 일부에서 건너뛸 바이트 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="83f5a-180">This represents the number of bytes to skip from being part of the hex output.</span></span>

<span data-ttu-id="83f5a-181">이 매개 변수는 PowerShell 6.2에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="83f5a-181">This parameter was introduced in PowerShell 6.2.</span></span>

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 0
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="83f5a-182">-개수</span><span class="sxs-lookup"><span data-stu-id="83f5a-182">-Count</span></span>

<span data-ttu-id="83f5a-183">이 값은 16 진수 출력에 포함할 바이트 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="83f5a-183">This represents the number of bytes to include in the hex output.</span></span>

<span data-ttu-id="83f5a-184">이 매개 변수는 PowerShell 6.2에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="83f5a-184">This parameter was introduced in PowerShell 6.2.</span></span>

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Int64.MaxValue
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="83f5a-185">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="83f5a-185">CommonParameters</span></span>

<span data-ttu-id="83f5a-186">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="83f5a-186">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="83f5a-187">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="83f5a-187">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="83f5a-188">입력</span><span class="sxs-lookup"><span data-stu-id="83f5a-188">INPUTS</span></span>

### <span data-ttu-id="83f5a-189">System.String</span><span class="sxs-lookup"><span data-stu-id="83f5a-189">System.String</span></span>

<span data-ttu-id="83f5a-190">이 cmdlet에 문자열을 파이프 하 여 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83f5a-190">You can pipe a string to this cmdlet.</span></span>

## <span data-ttu-id="83f5a-191">출력</span><span class="sxs-lookup"><span data-stu-id="83f5a-191">OUTPUTS</span></span>

### <span data-ttu-id="83f5a-192">ByteCollection.</span><span class="sxs-lookup"><span data-stu-id="83f5a-192">Microsoft.PowerShell.Commands.ByteCollection</span></span>

<span data-ttu-id="83f5a-193">이 cmdlet은 **ByteCollection** 를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="83f5a-193">This cmdlet returns a **ByteCollection**.</span></span> <span data-ttu-id="83f5a-194">이 개체는 바이트 컬렉션을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="83f5a-194">This object represents a collection of bytes.</span></span> <span data-ttu-id="83f5a-195">바이트 컬렉션을에서 반환 하는 출력의 각 줄 처럼 형식이 지정 된 문자열로 변환 하는 메서드를 포함 `Format-Hex` 합니다.</span><span class="sxs-lookup"><span data-stu-id="83f5a-195">It includes methods that convert the collection of bytes to a string formatted like each line of output returned by `Format-Hex`.</span></span> <span data-ttu-id="83f5a-196">출력에는 처리 중인 바이트의 형식이 명시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="83f5a-196">The output also states they type of bytes being processed.</span></span> <span data-ttu-id="83f5a-197">**Path** 또는 **LiteralPath** 매개 변수를 지정 하는 경우 개체는 각 바이트를 포함 하는 파일의 경로를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="83f5a-197">If you specify the **Path** or **LiteralPath** parameter, the object contains the path of the file that contains each byte.</span></span> <span data-ttu-id="83f5a-198">문자열, 부울, 정수 등을 전달 하는 경우 적절 하 게 레이블이 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="83f5a-198">If you pass a string, boolean, integer, etc, it will be labeled appropriately.</span></span>

## <span data-ttu-id="83f5a-199">참고</span><span class="sxs-lookup"><span data-stu-id="83f5a-199">NOTES</span></span>

<span data-ttu-id="83f5a-200">출력의 맨 오른쪽 열은 바이트를 ASCII 문자로 렌더링 하려고 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="83f5a-200">The right-most column of output tries to render the bytes as ASCII characters:</span></span>

<span data-ttu-id="83f5a-201">일반적으로 각 바이트는 유니코드 코드 포인트로 해석 됩니다 .이는 다음을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="83f5a-201">Generally, each byte is interpreted as a Unicode code point, which means that:</span></span>

- <span data-ttu-id="83f5a-202">인쇄 가능한 ASCII 문자는 항상 올바르게 렌더링 됩니다.</span><span class="sxs-lookup"><span data-stu-id="83f5a-202">Printable ASCII characters are always rendered correctly</span></span>
- <span data-ttu-id="83f5a-203">멀티 바이트 UTF-8 문자는 올바르게 렌더링 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="83f5a-203">Multi-byte UTF-8 characters never render correctly</span></span>
- <span data-ttu-id="83f5a-204">UTF-16 문자는 상위 바이트가 발생 하는 경우에만 올바르게 렌더링 됩니다 `NUL` .</span><span class="sxs-lookup"><span data-stu-id="83f5a-204">UTF-16 characters render correctly only if their high-order byte happens be `NUL`.</span></span>

## <span data-ttu-id="83f5a-205">관련 링크</span><span class="sxs-lookup"><span data-stu-id="83f5a-205">RELATED LINKS</span></span>

[<span data-ttu-id="83f5a-206">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="83f5a-206">about_Quoting_Rules</span></span>](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)

[<span data-ttu-id="83f5a-207">Format-Custom</span><span class="sxs-lookup"><span data-stu-id="83f5a-207">Format-Custom</span></span>](Format-Custom.md)

[<span data-ttu-id="83f5a-208">Format-List</span><span class="sxs-lookup"><span data-stu-id="83f5a-208">Format-List</span></span>](Format-List.md)

[<span data-ttu-id="83f5a-209">Format-Table</span><span class="sxs-lookup"><span data-stu-id="83f5a-209">Format-Table</span></span>](Format-Table.md)

[<span data-ttu-id="83f5a-210">Format-Wide</span><span class="sxs-lookup"><span data-stu-id="83f5a-210">Format-Wide</span></span>](Format-Wide.md)
