---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-hex?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-Hex
ms.openlocfilehash: a45e7919b5a24189ca7f50661795ff035c38a037
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99602662"
---
# <span data-ttu-id="435b0-102">Format-Hex</span><span class="sxs-lookup"><span data-stu-id="435b0-102">Format-Hex</span></span>

## <span data-ttu-id="435b0-103">개요</span><span class="sxs-lookup"><span data-stu-id="435b0-103">SYNOPSIS</span></span>

<span data-ttu-id="435b0-104">파일이 나 기타 입력을 16 진수로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="435b0-104">Displays a file or other input as hexadecimal.</span></span>

## <span data-ttu-id="435b0-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="435b0-105">SYNTAX</span></span>

### <span data-ttu-id="435b0-106">경로</span><span class="sxs-lookup"><span data-stu-id="435b0-106">Path</span></span>

```
Format-Hex [-Path] <String[]> [-Count <Int64>] [-Offset <Int64>] [<CommonParameters>]
```

### <span data-ttu-id="435b0-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="435b0-107">LiteralPath</span></span>

```
Format-Hex -LiteralPath <String[]> [-Count <Int64>] [-Offset <Int64>] [<CommonParameters>]
```

### <span data-ttu-id="435b0-108">ByInputObject</span><span class="sxs-lookup"><span data-stu-id="435b0-108">ByInputObject</span></span>

```
Format-Hex -InputObject <PSObject> [-Encoding <Encoding>] [-Count <Int64>] [-Offset <Int64>] [-Raw]
 [<CommonParameters>]
```

## <span data-ttu-id="435b0-109">설명</span><span class="sxs-lookup"><span data-stu-id="435b0-109">DESCRIPTION</span></span>

<span data-ttu-id="435b0-110">`Format-Hex`Cmdlet은 파일 또는 기타 입력을 16 진수 값으로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="435b0-110">The `Format-Hex` cmdlet displays a file or other input as hexadecimal values.</span></span> <span data-ttu-id="435b0-111">출력에서 문자의 오프셋을 확인 하려면 행의 맨 왼쪽에 있는 숫자를 해당 문자의 열 위쪽에 있는 숫자에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="435b0-111">To determine the offset of a character from the output, add the number at the leftmost of the row to the number at the top of the column for that character.</span></span>

<span data-ttu-id="435b0-112">Cmdlet을 통해 `Format-Hex` 손상 된 파일이 나 파일 이름 확장명을 가질 수 없는 파일의 파일 형식을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="435b0-112">The `Format-Hex` cmdlet can help you determine the file type of a corrupted file or a file that might not have a filename extension.</span></span> <span data-ttu-id="435b0-113">이 cmdlet을 실행 한 다음 16 진수 출력을 읽어 파일 정보를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="435b0-113">You can run this cmdlet, and then read the hexadecimal output to get file information.</span></span>

<span data-ttu-id="435b0-114">파일에서를 사용 하 `Format-Hex` 는 경우이 cmdlet은 줄 바꿈 문자를 무시 하 고 파일의 전체 내용을 줄 바꿈 문자가 유지 된 한 문자열로 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="435b0-114">When using `Format-Hex` on a file, the cmdlet ignores newline characters and returns the entire contents of a file in one string with the newline characters preserved.</span></span>

## <span data-ttu-id="435b0-115">예제</span><span class="sxs-lookup"><span data-stu-id="435b0-115">EXAMPLES</span></span>

### <span data-ttu-id="435b0-116">예제 1: 문자열의 16 진수 표현 가져오기</span><span class="sxs-lookup"><span data-stu-id="435b0-116">Example 1: Get the hexadecimal representation of a string</span></span>

<span data-ttu-id="435b0-117">이 명령은 문자열의 16 진수 값을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="435b0-117">This command returns the hexadecimal values of a string.</span></span>

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

<span data-ttu-id="435b0-118">**헬로 월드** 문자열은 파이프라인에서 cmdlet으로 전송 됩니다 `Format-Hex` .</span><span class="sxs-lookup"><span data-stu-id="435b0-118">The string **Hello World** is sent down the pipeline to the `Format-Hex` cmdlet.</span></span> <span data-ttu-id="435b0-119">의 16 진수 출력은 `Format-Hex` 문자열의 각 문자 값을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="435b0-119">The hexadecimal output from `Format-Hex` shows the values of each character in the string.</span></span>

### <span data-ttu-id="435b0-120">예 2:16 진수 출력에서 파일 형식 찾기</span><span class="sxs-lookup"><span data-stu-id="435b0-120">Example 2: Find a file type from hexadecimal output</span></span>

<span data-ttu-id="435b0-121">이 예제에서는 16 진수 출력을 사용 하 여 파일 형식을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="435b0-121">This example uses the hexadecimal output to determine the file type.</span></span> <span data-ttu-id="435b0-122">Cmdlet은 파일의 전체 경로와 16 진수 값을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="435b0-122">The cmdlet displays the file's full path and the hexadecimal values.</span></span>

<span data-ttu-id="435b0-123">다음 명령을 테스트 하려면 로컬 컴퓨터에 기존 PDF 파일의 복사본을 만들고 복사한 파일의 이름을로 바꿉니다 `File.t7f` .</span><span class="sxs-lookup"><span data-stu-id="435b0-123">To test the following command, make a copy of an existing PDF file on your local computer and rename the copied file to `File.t7f`.</span></span>

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

<span data-ttu-id="435b0-124">`Format-Hex`Cmdlet은 **Path** 매개 변수를 사용 하 여 현재 디렉터리의 파일 이름을 지정 `File.t7f` 합니다.</span><span class="sxs-lookup"><span data-stu-id="435b0-124">The `Format-Hex` cmdlet uses the **Path** parameter to specify a filename in the current directory, `File.t7f`.</span></span> <span data-ttu-id="435b0-125">파일 확장명은 `.t7f` 일반적이 지 않지만 16 진수 출력은 `%PDF` PDF 파일 임을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="435b0-125">The file extension `.t7f` is uncommon, but the hexadecimal output `%PDF` shows that it is a PDF file.</span></span> <span data-ttu-id="435b0-126">이 예에서는 **Count** 매개 변수를 사용 하 여 출력을 파일의 처음 48 바이트로 제한 합니다.</span><span class="sxs-lookup"><span data-stu-id="435b0-126">In this example, the **Count** parameter is used to limit the output to the first 48 bytes of the file.</span></span>

### <span data-ttu-id="435b0-127">예제 3: 다른 데이터 형식의 배열 서식 지정</span><span class="sxs-lookup"><span data-stu-id="435b0-127">Example 3: Format an array of different data types</span></span>

<span data-ttu-id="435b0-128">이 예제에서는 다양 한 데이터 형식의 배열을 사용 하 여가 파이프라인에서 처리 하는 방법을 강조 표시 `Format-Hex` 합니다.</span><span class="sxs-lookup"><span data-stu-id="435b0-128">This example uses an array of different data types to highlight how `Format-Hex` handles them in the Pipeline.</span></span>

<span data-ttu-id="435b0-129">파이프라인 및 프로세스를 통해 각 개체를 개별적으로 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="435b0-129">It will pass each object through the Pipeline and process individually.</span></span> <span data-ttu-id="435b0-130">그러나 숫자 데이터이 고 인접 개체도 숫자인 경우 단일 출력 블록으로 그룹화 합니다.</span><span class="sxs-lookup"><span data-stu-id="435b0-130">However, if it's numeric data, and the adjacent object is also numeric, it will group them into a single output block.</span></span>

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
0000000000000000 EF BE AD DE 00 00 00 40 5C 03 00 00             ï¾-Þ   @\�

   Label: Boolean (System.Boolean) <7D8C4C1D>

          Offset Bytes                                           Ascii
                 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
          ------ ----------------------------------------------- -----
0000000000000000 01 00 00 00 00 00 00 00                         �
```

## <span data-ttu-id="435b0-131">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="435b0-131">PARAMETERS</span></span>

### <span data-ttu-id="435b0-132">-Encoding</span><span class="sxs-lookup"><span data-stu-id="435b0-132">-Encoding</span></span>

<span data-ttu-id="435b0-133">입력 문자열의 인코딩을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="435b0-133">Specifies the encoding of the input strings.</span></span> <span data-ttu-id="435b0-134">이는 입력에만 적용 됩니다 `[string]` .</span><span class="sxs-lookup"><span data-stu-id="435b0-134">This only applies to `[string]` input.</span></span> <span data-ttu-id="435b0-135">매개 변수는 숫자 형식에는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="435b0-135">The parameter has no effect on numeric types.</span></span> <span data-ttu-id="435b0-136">출력 값은 항상 `utf8NoBOM` 입니다.</span><span class="sxs-lookup"><span data-stu-id="435b0-136">The output value is always `utf8NoBOM`.</span></span>

<span data-ttu-id="435b0-137">이 매개 변수에 허용 되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="435b0-137">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="435b0-138">`ascii`: ASCII (7 비트) 문자 집합에 대 한 인코딩을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="435b0-138">`ascii`: Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="435b0-139">`bigendianunicode`: 빅 endian 바이트 순서를 사용 하 여 UTF-16 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="435b0-139">`bigendianunicode`: Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="435b0-140">`bigendianutf32`: 빅 endian 바이트 순서를 사용 하 여 u t f-32 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="435b0-140">`bigendianutf32`: Encodes in UTF-32 format using the big-endian byte order.</span></span>
- <span data-ttu-id="435b0-141">`oem`: MS-DOS 및 콘솔 프로그램에 기본 인코딩을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="435b0-141">`oem`: Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="435b0-142">`unicode`: 작은 endian 바이트 순서를 사용 하 여 UTF-16 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="435b0-142">`unicode`: Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="435b0-143">`utf7`: UTF-7 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="435b0-143">`utf7`: Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="435b0-144">`utf8`: UTF-8 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="435b0-144">`utf8`: Encodes in UTF-8 format.</span></span>
- <span data-ttu-id="435b0-145">`utf8BOM`: 바이트 순서 표시 (BOM)를 사용 하 여 UTF-8 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="435b0-145">`utf8BOM`: Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="435b0-146">`utf8NoBOM`: BOM (바이트 순서 표시) 없이 UTF-8 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="435b0-146">`utf8NoBOM`: Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="435b0-147">`utf32`: U t f-32 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="435b0-147">`utf32`: Encodes in UTF-32 format.</span></span>

<span data-ttu-id="435b0-148">PowerShell 6.2부터 **Encoding** 매개 변수를 사용 하 여 등록 된 코드 페이지의 숫자 id (예: `-Encoding 1251` ) 또는 등록 된 코드 페이지의 문자열 이름을 사용할 수도 있습니다 (예: `-Encoding "windows-1251"` ).</span><span class="sxs-lookup"><span data-stu-id="435b0-148">Beginning with PowerShell 6.2, the **Encoding** parameter also allows numeric IDs of registered code pages (like `-Encoding 1251`) or string names of registered code pages (like `-Encoding "windows-1251"`).</span></span> <span data-ttu-id="435b0-149">자세한 내용은 [인코딩에](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2)대 한 .net 설명서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="435b0-149">For more information, see the .NET documentation for [Encoding.CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span></span>

> [!NOTE]
> <span data-ttu-id="435b0-150">**U t f-7** _은 더 이상 사용 하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="435b0-150">**UTF-7** _ is no longer recommended to use.</span></span> <span data-ttu-id="435b0-151">PowerShell 7.1에서는 `utf7` _ *Encoding*\* 매개 변수에 대해를 지정 하는 경우 경고가 기록 됩니다.</span><span class="sxs-lookup"><span data-stu-id="435b0-151">In PowerShell 7.1, a warning is written if you specify `utf7` for the _ *Encoding*\* parameter.</span></span>

```yaml
Type: System.Text.Encoding
Parameter Sets: ByInputObject
Aliases:
Accepted values: ASCII, BigEndianUnicode, BigEndianUTF32, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: Named
Default value: UTF8NoBOM
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="435b0-152">-InputObject</span><span class="sxs-lookup"><span data-stu-id="435b0-152">-InputObject</span></span>

<span data-ttu-id="435b0-153">파이프라인 입력에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="435b0-153">Used for pipeline input.</span></span> <span data-ttu-id="435b0-154">파이프라인 입력은 `[system.io.fileinfo]` 에서 파이프에 대 한 특정 스칼라 형식 및 인스턴스만 지원 `Get-ChildItem` 합니다.</span><span class="sxs-lookup"><span data-stu-id="435b0-154">Pipeline input supports only certain scalar types and `[system.io.fileinfo]` instances for piping from `Get-ChildItem`.</span></span>

<span data-ttu-id="435b0-155">지원 되는 스칼라 형식은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="435b0-155">The supported scalar types are:</span></span>

- <span data-ttu-id="435b0-156">`[string]`, `[char]`</span><span class="sxs-lookup"><span data-stu-id="435b0-156">`[string]`, `[char]`</span></span>
- <span data-ttu-id="435b0-157">`[byte]`, `[sbyte]`</span><span class="sxs-lookup"><span data-stu-id="435b0-157">`[byte]`, `[sbyte]`</span></span>
- <span data-ttu-id="435b0-158">`[int16]`, `[uint16]`, `[short]`, `[ushort]`</span><span class="sxs-lookup"><span data-stu-id="435b0-158">`[int16]`, `[uint16]`, `[short]`, `[ushort]`</span></span>
- <span data-ttu-id="435b0-159">`[int]`, `[uint]`, `[int32]`, `[uint32]`,</span><span class="sxs-lookup"><span data-stu-id="435b0-159">`[int]`, `[uint]`, `[int32]`, `[uint32]`,</span></span>
- <span data-ttu-id="435b0-160">`[long]`, `[ulong]`, `[int64]`, `[uint64]`</span><span class="sxs-lookup"><span data-stu-id="435b0-160">`[long]`, `[ulong]`, `[int64]`, `[uint64]`</span></span>
- <span data-ttu-id="435b0-161">`[single]`, `[float]`, `[double]`</span><span class="sxs-lookup"><span data-stu-id="435b0-161">`[single]`, `[float]`, `[double]`</span></span>
- `[boolean]`

<span data-ttu-id="435b0-162">PowerShell 6.2 이전에 `Format-Hex` 는와 같은 모든 개체를 함께 그룹화 하 여 여러 입력 형식의 파이프라인 입력을 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="435b0-162">Prior to PowerShell 6.2, `Format-Hex` would handle a Pipeline input with multiple input types by grouping all like objects together.</span></span> <span data-ttu-id="435b0-163">이제는 파이프라인을 통과 하는 각 개별 개체를 처리 하 고, 개체가 인접 하지 않는 한 개체를 그룹화 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="435b0-163">Now, it handles each individual object as it passes through the Pipeline and won't group objects together unless like objects are adjacent.</span></span>

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

### <span data-ttu-id="435b0-164">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="435b0-164">-LiteralPath</span></span>

<span data-ttu-id="435b0-165">파일의 전체 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="435b0-165">Specifies the complete path to a file.</span></span> <span data-ttu-id="435b0-166">**LiteralPath** 의 값은 입력 한 대로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="435b0-166">The value of **LiteralPath** is used exactly as it is typed.</span></span>
<span data-ttu-id="435b0-167">이 매개 변수는 와일드 카드 문자를 허용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="435b0-167">This parameter does not accept wildcard characters.</span></span> <span data-ttu-id="435b0-168">파일에 대 한 여러 경로를 지정 하려면 경로를 쉼표로 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="435b0-168">To specify multiple paths to files, separate the paths with a comma.</span></span> <span data-ttu-id="435b0-169">**LiteralPath** 매개 변수에 이스케이프 문자가 포함 되어 있으면 경로를 작은따옴표로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="435b0-169">If the **LiteralPath** parameter includes escape characters, enclose the path in single quotation marks.</span></span> <span data-ttu-id="435b0-170">PowerShell에서는 따옴표 붙은 단일 문자열의 문자를 이스케이프 시퀀스로 해석 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="435b0-170">PowerShell does not interpret any characters in a single quoted string as escape sequences.</span></span> <span data-ttu-id="435b0-171">자세한 내용은 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="435b0-171">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="435b0-172">-Path</span><span class="sxs-lookup"><span data-stu-id="435b0-172">-Path</span></span>

<span data-ttu-id="435b0-173">파일의 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="435b0-173">Specifies the path to files.</span></span> <span data-ttu-id="435b0-174">점 ()을 사용 `.` 하 여 현재 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="435b0-174">Use a dot (`.`) to specify the current location.</span></span> <span data-ttu-id="435b0-175">와일드 카드 문자 ( `*` )가 허용 되며, 위치에 있는 모든 항목을 지정 하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="435b0-175">The wildcard character (`*`) is accepted and can be used to specify all the items in a location.</span></span> <span data-ttu-id="435b0-176">**Path** 매개 변수에 이스케이프 문자가 포함 되어 있으면 경로를 작은따옴표로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="435b0-176">If the **Path** parameter includes escape characters, enclose the path in single quotation marks.</span></span> <span data-ttu-id="435b0-177">파일에 대 한 여러 경로를 지정 하려면 경로를 쉼표로 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="435b0-177">To specify multiple paths to files, separate the paths with a comma.</span></span>

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

### <span data-ttu-id="435b0-178">-Raw</span><span class="sxs-lookup"><span data-stu-id="435b0-178">-Raw</span></span>

<span data-ttu-id="435b0-179">이 매개 변수는 더 이상 아무 작업도 수행 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="435b0-179">This parameter no longer does anything.</span></span> <span data-ttu-id="435b0-180">스크립트 호환성을 위해 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="435b0-180">It is retained for script compatibility.</span></span>

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

### <span data-ttu-id="435b0-181">-오프셋</span><span class="sxs-lookup"><span data-stu-id="435b0-181">-Offset</span></span>

<span data-ttu-id="435b0-182">이는 16 진수 출력의 일부에서 건너뛸 바이트 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="435b0-182">This represents the number of bytes to skip from being part of the hex output.</span></span>

<span data-ttu-id="435b0-183">이 매개 변수는 PowerShell 6.2에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="435b0-183">This parameter was introduced in PowerShell 6.2.</span></span>

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

### <span data-ttu-id="435b0-184">-개수</span><span class="sxs-lookup"><span data-stu-id="435b0-184">-Count</span></span>

<span data-ttu-id="435b0-185">이 값은 16 진수 출력에 포함할 바이트 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="435b0-185">This represents the number of bytes to include in the hex output.</span></span>

<span data-ttu-id="435b0-186">이 매개 변수는 PowerShell 6.2에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="435b0-186">This parameter was introduced in PowerShell 6.2.</span></span>

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

### <span data-ttu-id="435b0-187">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="435b0-187">CommonParameters</span></span>

<span data-ttu-id="435b0-188">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="435b0-188">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="435b0-189">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="435b0-189">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="435b0-190">입력</span><span class="sxs-lookup"><span data-stu-id="435b0-190">INPUTS</span></span>

### <span data-ttu-id="435b0-191">System.String</span><span class="sxs-lookup"><span data-stu-id="435b0-191">System.String</span></span>

<span data-ttu-id="435b0-192">이 cmdlet에 문자열을 파이프 하 여 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="435b0-192">You can pipe a string to this cmdlet.</span></span>

## <span data-ttu-id="435b0-193">출력</span><span class="sxs-lookup"><span data-stu-id="435b0-193">OUTPUTS</span></span>

### <span data-ttu-id="435b0-194">ByteCollection.</span><span class="sxs-lookup"><span data-stu-id="435b0-194">Microsoft.PowerShell.Commands.ByteCollection</span></span>

<span data-ttu-id="435b0-195">이 cmdlet은 **ByteCollection** 를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="435b0-195">This cmdlet returns a **ByteCollection**.</span></span> <span data-ttu-id="435b0-196">이 개체는 바이트 컬렉션을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="435b0-196">This object represents a collection of bytes.</span></span> <span data-ttu-id="435b0-197">바이트 컬렉션을에서 반환 하는 출력의 각 줄 처럼 형식이 지정 된 문자열로 변환 하는 메서드를 포함 `Format-Hex` 합니다.</span><span class="sxs-lookup"><span data-stu-id="435b0-197">It includes methods that convert the collection of bytes to a string formatted like each line of output returned by `Format-Hex`.</span></span> <span data-ttu-id="435b0-198">출력에는 처리 중인 바이트의 형식이 명시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="435b0-198">The output also states they type of bytes being processed.</span></span> <span data-ttu-id="435b0-199">**Path** 또는 **LiteralPath** 매개 변수를 지정 하는 경우 개체는 각 바이트를 포함 하는 파일의 경로를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="435b0-199">If you specify the **Path** or **LiteralPath** parameter, the object contains the path of the file that contains each byte.</span></span> <span data-ttu-id="435b0-200">문자열, 부울, 정수 등을 전달 하는 경우 적절 하 게 레이블이 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="435b0-200">If you pass a string, boolean, integer, etc, it will be labeled appropriately.</span></span>

## <span data-ttu-id="435b0-201">참고</span><span class="sxs-lookup"><span data-stu-id="435b0-201">NOTES</span></span>

<span data-ttu-id="435b0-202">출력의 맨 오른쪽 열은 바이트를 ASCII 문자로 렌더링 하려고 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="435b0-202">The right-most column of output tries to render the bytes as ASCII characters:</span></span>

<span data-ttu-id="435b0-203">일반적으로 각 바이트는 유니코드 코드 포인트로 해석 됩니다 .이는 다음을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="435b0-203">Generally, each byte is interpreted as a Unicode code point, which means that:</span></span>

- <span data-ttu-id="435b0-204">인쇄 가능한 ASCII 문자는 항상 올바르게 렌더링 됩니다.</span><span class="sxs-lookup"><span data-stu-id="435b0-204">Printable ASCII characters are always rendered correctly</span></span>
- <span data-ttu-id="435b0-205">멀티 바이트 UTF-8 문자는 올바르게 렌더링 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="435b0-205">Multi-byte UTF-8 characters never render correctly</span></span>
- <span data-ttu-id="435b0-206">UTF-16 문자는 상위 바이트가 발생 하는 경우에만 올바르게 렌더링 됩니다 `NUL` .</span><span class="sxs-lookup"><span data-stu-id="435b0-206">UTF-16 characters render correctly only if their high-order byte happens be `NUL`.</span></span>

## <span data-ttu-id="435b0-207">관련 링크</span><span class="sxs-lookup"><span data-stu-id="435b0-207">RELATED LINKS</span></span>

[<span data-ttu-id="435b0-208">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="435b0-208">about_Quoting_Rules</span></span>](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)

[<span data-ttu-id="435b0-209">Format-Custom</span><span class="sxs-lookup"><span data-stu-id="435b0-209">Format-Custom</span></span>](Format-Custom.md)

[<span data-ttu-id="435b0-210">Format-List</span><span class="sxs-lookup"><span data-stu-id="435b0-210">Format-List</span></span>](Format-List.md)

[<span data-ttu-id="435b0-211">Format-Table</span><span class="sxs-lookup"><span data-stu-id="435b0-211">Format-Table</span></span>](Format-Table.md)

[<span data-ttu-id="435b0-212">Format-Wide</span><span class="sxs-lookup"><span data-stu-id="435b0-212">Format-Wide</span></span>](Format-Wide.md)

