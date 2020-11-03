---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 01/17/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-hex?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-Hex
ms.openlocfilehash: 64275e72f8c21942179431b3aed4a17d328aa2e9
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93216722"
---
# <span data-ttu-id="821e3-103">Format-Hex</span><span class="sxs-lookup"><span data-stu-id="821e3-103">Format-Hex</span></span>

## <span data-ttu-id="821e3-104">개요</span><span class="sxs-lookup"><span data-stu-id="821e3-104">SYNOPSIS</span></span>

<span data-ttu-id="821e3-105">파일이 나 기타 입력을 16 진수로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="821e3-105">Displays a file or other input as hexadecimal.</span></span>

## <span data-ttu-id="821e3-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="821e3-106">SYNTAX</span></span>

### <span data-ttu-id="821e3-107">Path (기본값)</span><span class="sxs-lookup"><span data-stu-id="821e3-107">Path (Default)</span></span>

```
Format-Hex [-Path] <string[]> [-Count <long>] [-Offset <long>] [<CommonParameters>]
```

### <span data-ttu-id="821e3-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="821e3-108">LiteralPath</span></span>

```
Format-Hex -LiteralPath <string[]> [-Count <long>] [-Offset <long>] [<CommonParameters>]
```

### <span data-ttu-id="821e3-109">InputObject</span><span class="sxs-lookup"><span data-stu-id="821e3-109">InputObject</span></span>

```
Format-Hex -InputObject <psobject> [-Encoding <Encoding>] [-Count <long>] [-Offset <long>] [-Raw] [<CommonParameters>]
```

## <span data-ttu-id="821e3-110">설명</span><span class="sxs-lookup"><span data-stu-id="821e3-110">DESCRIPTION</span></span>

<span data-ttu-id="821e3-111">`Format-Hex`Cmdlet은 파일 또는 기타 입력을 16 진수 값으로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="821e3-111">The `Format-Hex` cmdlet displays a file or other input as hexadecimal values.</span></span> <span data-ttu-id="821e3-112">출력에서 문자의 오프셋을 확인 하려면 행의 맨 왼쪽에 있는 숫자를 해당 문자의 열 위쪽에 있는 숫자에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="821e3-112">To determine the offset of a character from the output, add the number at the leftmost of the row to the number at the top of the column for that character.</span></span>

<span data-ttu-id="821e3-113">Cmdlet을 통해 `Format-Hex` 손상 된 파일이 나 파일 이름 확장명을 가질 수 없는 파일의 파일 형식을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="821e3-113">The `Format-Hex` cmdlet can help you determine the file type of a corrupted file or a file that might not have a filename extension.</span></span> <span data-ttu-id="821e3-114">이 cmdlet을 실행 한 다음 16 진수 출력을 읽어 파일 정보를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="821e3-114">You can run this cmdlet, and then read the hexadecimal output to get file information.</span></span>

<span data-ttu-id="821e3-115">파일에서를 사용 하 `Format-Hex` 는 경우이 cmdlet은 줄 바꿈 문자를 무시 하 고 파일의 전체 내용을 줄 바꿈 문자가 유지 된 한 문자열로 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="821e3-115">When using `Format-Hex` on a file, the cmdlet ignores newline characters and returns the entire contents of a file in one string with the newline characters preserved.</span></span>

## <span data-ttu-id="821e3-116">예제</span><span class="sxs-lookup"><span data-stu-id="821e3-116">EXAMPLES</span></span>

### <span data-ttu-id="821e3-117">예제 1: 문자열의 16 진수 표현 가져오기</span><span class="sxs-lookup"><span data-stu-id="821e3-117">Example 1: Get the hexadecimal representation of a string</span></span>

<span data-ttu-id="821e3-118">이 명령은 문자열의 16 진수 값을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="821e3-118">This command returns the hexadecimal values of a string.</span></span>

```powershell
'Hello World' | Format-Hex
```

```Output
           00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F

00000000   48 65 6C 6C 6F 20 57 6F 72 6C 64                 Hello World
```

<span data-ttu-id="821e3-119">**Hello World** 문자열은 파이프라인에서 cmdlet으로 전송 됩니다 `Format-Hex` .</span><span class="sxs-lookup"><span data-stu-id="821e3-119">The string **Hello World** is sent down the pipeline to the `Format-Hex` cmdlet.</span></span> <span data-ttu-id="821e3-120">의 16 진수 출력은 `Format-Hex` 문자열의 각 문자 값을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="821e3-120">The hexadecimal output from `Format-Hex` shows the values of each character in the string.</span></span>

### <span data-ttu-id="821e3-121">예 2:16 진수 출력에서 파일 형식 찾기</span><span class="sxs-lookup"><span data-stu-id="821e3-121">Example 2: Find a file type from hexadecimal output</span></span>

<span data-ttu-id="821e3-122">이 예제에서는 16 진수 출력을 사용 하 여 파일 형식을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="821e3-122">This example uses the hexadecimal output to determine the file type.</span></span> <span data-ttu-id="821e3-123">Cmdlet은 파일의 전체 경로와 16 진수 값을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="821e3-123">The cmdlet displays the file's full path and the hexadecimal values.</span></span>

<span data-ttu-id="821e3-124">다음 명령을 테스트 하려면 로컬 컴퓨터에 기존 PDF 파일의 복사본을 만들고 복사한 파일의 이름을로 바꿉니다 `File.t7f` .</span><span class="sxs-lookup"><span data-stu-id="821e3-124">To test the following command, make a copy of an existing PDF file on your local computer and rename the copied file to `File.t7f`.</span></span>

```powershell
Format-Hex -Path .\File.t7f
```

```Output
           Path: C:\Test\File.t7f

           00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F

00000000   25 50 44 46 2D 31 2E 35 0D 0A 25 B5 B5 B5 B5 0D  %PDF-1.5..%????.
00000010   0A 31 20 30 20 6F 62 6A 0D 0A 3C 3C 2F 54 79 70  .1 0 obj..<</Typ
00000020   65 2F 43 61 74 61 6C 6F 67 2F 50 61 67 65 73 20  e/Catalog/Pages
```

<span data-ttu-id="821e3-125">`Format-Hex`Cmdlet은 **Path** 매개 변수를 사용 하 여 t7f의 현재 디렉터리에 **파일** 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="821e3-125">The `Format-Hex` cmdlet uses the **Path** parameter to specify a filename in the current directory, **File.t7f**.</span></span> <span data-ttu-id="821e3-126">**T7f** 파일 확장명은 일반적이 지 않지만 16 진수 출력 **% pdf** 는 pdf 파일 임을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="821e3-126">The file extension **.t7f** is uncommon, but the hexadecimal output **%PDF** shows that it is a PDF file.</span></span>

## <span data-ttu-id="821e3-127">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="821e3-127">PARAMETERS</span></span>

### <span data-ttu-id="821e3-128">-Encoding</span><span class="sxs-lookup"><span data-stu-id="821e3-128">-Encoding</span></span>

<span data-ttu-id="821e3-129">출력의 인코딩을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="821e3-129">Specifies the encoding of the output.</span></span> <span data-ttu-id="821e3-130">이는 입력에만 적용 됩니다 `[string]` .</span><span class="sxs-lookup"><span data-stu-id="821e3-130">This only applies to `[string]` input.</span></span> <span data-ttu-id="821e3-131">매개 변수는 숫자 형식에는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="821e3-131">The parameter has no effect on numeric types.</span></span> <span data-ttu-id="821e3-132">기본값은 `utf8NoBOM`입니다.</span><span class="sxs-lookup"><span data-stu-id="821e3-132">The default value is `utf8NoBOM`.</span></span>

<span data-ttu-id="821e3-133">이 매개 변수에 허용 되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="821e3-133">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="821e3-134">`ascii`: ASCII (7 비트) 문자 집합에 대 한 인코딩을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="821e3-134">`ascii`: Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="821e3-135">`bigendianunicode`: 빅 endian 바이트 순서를 사용 하 여 UTF-16 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="821e3-135">`bigendianunicode`: Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="821e3-136">`oem`: MS-DOS 및 콘솔 프로그램에 기본 인코딩을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="821e3-136">`oem`: Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="821e3-137">`unicode`: 작은 endian 바이트 순서를 사용 하 여 UTF-16 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="821e3-137">`unicode`: Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="821e3-138">`utf7`: UTF-7 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="821e3-138">`utf7`: Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="821e3-139">`utf8`: UTF-8 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="821e3-139">`utf8`: Encodes in UTF-8 format.</span></span>
- <span data-ttu-id="821e3-140">`utf8BOM`: 바이트 순서 표시 (BOM)를 사용 하 여 UTF-8 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="821e3-140">`utf8BOM`: Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="821e3-141">`utf8NoBOM`: BOM (바이트 순서 표시) 없이 UTF-8 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="821e3-141">`utf8NoBOM`: Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="821e3-142">`utf32`: U t f-32 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="821e3-142">`utf32`: Encodes in UTF-32 format.</span></span>

<span data-ttu-id="821e3-143">PowerShell 6.2부터 **Encoding** 매개 변수를 사용 하 여 등록 된 코드 페이지의 숫자 id (예: `-Encoding 1251` ) 또는 등록 된 코드 페이지의 문자열 이름을 사용할 수도 있습니다 (예: `-Encoding "windows-1251"` ).</span><span class="sxs-lookup"><span data-stu-id="821e3-143">Beginning with PowerShell 6.2, the **Encoding** parameter also allows numeric IDs of registered code pages (like `-Encoding 1251`) or string names of registered code pages (like `-Encoding "windows-1251"`).</span></span> <span data-ttu-id="821e3-144">자세한 내용은 [인코딩에](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2)대 한 .net 설명서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="821e3-144">For more information, see the .NET documentation for [Encoding.CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span></span>

```yaml
Type: Encoding
Parameter Sets: ByInputObject
Aliases:
Accepted values: ASCII, BigEndianUnicode, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: Named
Default value: UTF8NoBOM
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="821e3-145">-InputObject</span><span class="sxs-lookup"><span data-stu-id="821e3-145">-InputObject</span></span>

<span data-ttu-id="821e3-146">파이프라인 입력에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="821e3-146">Used for pipeline input.</span></span> <span data-ttu-id="821e3-147">파이프라인 입력은 `[system.io.fileinfo]` 에서 파이프에 대 한 특정 스칼라 형식 및 인스턴스만 지원 `Get-ChildItem` 합니다.</span><span class="sxs-lookup"><span data-stu-id="821e3-147">Pipeline input supports only certain scalar types and `[system.io.fileinfo]` instances for piping from `Get-ChildItem`.</span></span>

<span data-ttu-id="821e3-148">지원 되는 스칼라 형식은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="821e3-148">The supported scalar types are:</span></span>

- <span data-ttu-id="821e3-149">`[string]`, `[char]`</span><span class="sxs-lookup"><span data-stu-id="821e3-149">`[string]`, `[char]`</span></span>
- <span data-ttu-id="821e3-150">`[byte]`, `[sbyte]`</span><span class="sxs-lookup"><span data-stu-id="821e3-150">`[byte]`, `[sbyte]`</span></span>
- <span data-ttu-id="821e3-151">`[int16]`, `[uint16]`, `[short]`, `[ushort]`</span><span class="sxs-lookup"><span data-stu-id="821e3-151">`[int16]`, `[uint16]`, `[short]`, `[ushort]`</span></span>
- <span data-ttu-id="821e3-152">`[int]`, `[uint]`, `[int32]`, `[uint32]`,</span><span class="sxs-lookup"><span data-stu-id="821e3-152">`[int]`, `[uint]`, `[int32]`, `[uint32]`,</span></span>
- <span data-ttu-id="821e3-153">`[long]`, `[ulong]`, `[int64]`, `[uint64]`</span><span class="sxs-lookup"><span data-stu-id="821e3-153">`[long]`, `[ulong]`, `[int64]`, `[uint64]`</span></span>
- <span data-ttu-id="821e3-154">`[single]`, `[float]`, `[double]`</span><span class="sxs-lookup"><span data-stu-id="821e3-154">`[single]`, `[float]`, `[double]`</span></span>

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

### <span data-ttu-id="821e3-155">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="821e3-155">-LiteralPath</span></span>

<span data-ttu-id="821e3-156">파일의 전체 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="821e3-156">Specifies the complete path to a file.</span></span> <span data-ttu-id="821e3-157">**LiteralPath** 의 값은 입력 한 대로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="821e3-157">The value of **LiteralPath** is used exactly as it is typed.</span></span>
<span data-ttu-id="821e3-158">이 매개 변수는 와일드 카드 문자를 허용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="821e3-158">This parameter does not accept wildcard characters.</span></span> <span data-ttu-id="821e3-159">파일에 대 한 여러 경로를 지정 하려면 경로를 쉼표로 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="821e3-159">To specify multiple paths to files, separate the paths with a comma.</span></span> <span data-ttu-id="821e3-160">**LiteralPath** 매개 변수에 이스케이프 문자가 포함 되어 있으면 경로를 작은따옴표로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="821e3-160">If the **LiteralPath** parameter includes escape characters, enclose the path in single quotation marks.</span></span> <span data-ttu-id="821e3-161">PowerShell에서는 따옴표 붙은 단일 문자열의 문자를 이스케이프 시퀀스로 해석 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="821e3-161">PowerShell does not interpret any characters in a single quoted string as escape sequences.</span></span> <span data-ttu-id="821e3-162">자세한 내용은 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="821e3-162">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="821e3-163">-Path</span><span class="sxs-lookup"><span data-stu-id="821e3-163">-Path</span></span>

<span data-ttu-id="821e3-164">파일의 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="821e3-164">Specifies the path to files.</span></span> <span data-ttu-id="821e3-165">점 ()을 사용 `.` 하 여 현재 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="821e3-165">Use a dot (`.`) to specify the current location.</span></span> <span data-ttu-id="821e3-166">와일드 카드 문자 ( `*` )가 허용 되며, 위치에 있는 모든 항목을 지정 하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="821e3-166">The wildcard character (`*`) is accepted and can be used to specify all the items in a location.</span></span> <span data-ttu-id="821e3-167">**Path** 매개 변수에 이스케이프 문자가 포함 되어 있으면 경로를 작은따옴표로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="821e3-167">If the **Path** parameter includes escape characters, enclose the path in single quotation marks.</span></span> <span data-ttu-id="821e3-168">파일에 대 한 여러 경로를 지정 하려면 경로를 쉼표로 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="821e3-168">To specify multiple paths to files, separate the paths with a comma.</span></span>

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

### <span data-ttu-id="821e3-169">-Raw</span><span class="sxs-lookup"><span data-stu-id="821e3-169">-Raw</span></span>

<span data-ttu-id="821e3-170">이 매개 변수는 더 이상 아무 작업도 수행 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="821e3-170">This parameter no longer does anything.</span></span> <span data-ttu-id="821e3-171">스크립트 호환성을 위해 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="821e3-171">It is retained for script compatibility.</span></span>

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

### <span data-ttu-id="821e3-172">-오프셋</span><span class="sxs-lookup"><span data-stu-id="821e3-172">-Offset</span></span>

<span data-ttu-id="821e3-173">이는 16 진수 출력의 일부에서 건너뛸 바이트 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="821e3-173">This represents the number of bytes to skip from being part of the hex output.</span></span>

<span data-ttu-id="821e3-174">이 매개 변수는 PowerShell 6.2에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="821e3-174">This parameter was introduced in PowerShell 6.2.</span></span>

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

### <span data-ttu-id="821e3-175">-개수</span><span class="sxs-lookup"><span data-stu-id="821e3-175">-Count</span></span>

<span data-ttu-id="821e3-176">이 값은 16 진수 출력에 포함할 바이트 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="821e3-176">This represents the number of bytes to include in the hex output.</span></span>

<span data-ttu-id="821e3-177">이 매개 변수는 PowerShell 6.2에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="821e3-177">This parameter was introduced in PowerShell 6.2.</span></span>

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

### <span data-ttu-id="821e3-178">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="821e3-178">CommonParameters</span></span>

<span data-ttu-id="821e3-179">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="821e3-179">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="821e3-180">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="821e3-180">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="821e3-181">입력</span><span class="sxs-lookup"><span data-stu-id="821e3-181">INPUTS</span></span>

### <span data-ttu-id="821e3-182">System.String</span><span class="sxs-lookup"><span data-stu-id="821e3-182">System.String</span></span>

<span data-ttu-id="821e3-183">이 cmdlet에 문자열을 파이프 하 여 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="821e3-183">You can pipe a string to this cmdlet.</span></span>

## <span data-ttu-id="821e3-184">출력</span><span class="sxs-lookup"><span data-stu-id="821e3-184">OUTPUTS</span></span>

### <span data-ttu-id="821e3-185">ByteCollection.</span><span class="sxs-lookup"><span data-stu-id="821e3-185">Microsoft.PowerShell.Commands.ByteCollection</span></span>

<span data-ttu-id="821e3-186">이 cmdlet은 **ByteCollection** 를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="821e3-186">This cmdlet returns a **ByteCollection**.</span></span> <span data-ttu-id="821e3-187">이 개체는 바이트 컬렉션을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="821e3-187">This object represents a collection of bytes.</span></span> <span data-ttu-id="821e3-188">바이트 컬렉션을에서 반환 하는 출력의 각 줄 처럼 형식이 지정 된 문자열로 변환 하는 메서드를 포함 `Format-Hex` 합니다.</span><span class="sxs-lookup"><span data-stu-id="821e3-188">It includes methods that convert the collection of bytes to a string formatted like each line of output returned by `Format-Hex`.</span></span> <span data-ttu-id="821e3-189">**Path** 또는 **LiteralPath** 매개 변수를 지정 하는 경우 개체에는 각 바이트를 포함 하는 파일의 경로도 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="821e3-189">If you specify the **Path** or **LiteralPath** parameter, the object also contains the path of the file that contains each byte.</span></span>

## <span data-ttu-id="821e3-190">참고</span><span class="sxs-lookup"><span data-stu-id="821e3-190">NOTES</span></span>

<span data-ttu-id="821e3-191">출력의 맨 오른쪽 열은 바이트를 ASCII 문자로 렌더링 하려고 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="821e3-191">The right-most column of output tries to render the bytes as ASCII characters:</span></span>

<span data-ttu-id="821e3-192">일반적으로 각 바이트는 유니코드 코드 포인트로 해석 됩니다 .이는 다음을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="821e3-192">Generally, each byte is interpreted as a Unicode code point, which means that:</span></span>

- <span data-ttu-id="821e3-193">인쇄 가능한 ASCII 문자는 항상 올바르게 렌더링 됩니다.</span><span class="sxs-lookup"><span data-stu-id="821e3-193">Printable ASCII characters are always rendered correctly</span></span>
- <span data-ttu-id="821e3-194">멀티 바이트 UTF-8 문자는 올바르게 렌더링 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="821e3-194">Multi-byte UTF-8 characters never render correctly</span></span>
- <span data-ttu-id="821e3-195">UTF-16 문자는 상위 바이트가 발생 하는 경우에만 올바르게 렌더링 됩니다 `NUL` .</span><span class="sxs-lookup"><span data-stu-id="821e3-195">UTF-16 characters render correctly only if their high-order byte happens be `NUL`.</span></span>

## <span data-ttu-id="821e3-196">관련 링크</span><span class="sxs-lookup"><span data-stu-id="821e3-196">RELATED LINKS</span></span>

[<span data-ttu-id="821e3-197">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="821e3-197">about_Quoting_Rules</span></span>](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)

[<span data-ttu-id="821e3-198">Format-Custom</span><span class="sxs-lookup"><span data-stu-id="821e3-198">Format-Custom</span></span>](Format-Custom.md)

[<span data-ttu-id="821e3-199">Format-List</span><span class="sxs-lookup"><span data-stu-id="821e3-199">Format-List</span></span>](Format-List.md)

[<span data-ttu-id="821e3-200">Format-Table</span><span class="sxs-lookup"><span data-stu-id="821e3-200">Format-Table</span></span>](Format-Table.md)

[<span data-ttu-id="821e3-201">Format-Wide</span><span class="sxs-lookup"><span data-stu-id="821e3-201">Format-Wide</span></span>](Format-Wide.md)
