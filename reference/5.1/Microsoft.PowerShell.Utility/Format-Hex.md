---
external help file: Microsoft.PowerShell.Utility-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 01/17/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-hex?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-Hex
ms.openlocfilehash: 514a66ebee3827de998622a738c75d4f8e0c7279
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93214026"
---
# <span data-ttu-id="8ab40-103">Format-Hex</span><span class="sxs-lookup"><span data-stu-id="8ab40-103">Format-Hex</span></span>

## <span data-ttu-id="8ab40-104">개요</span><span class="sxs-lookup"><span data-stu-id="8ab40-104">SYNOPSIS</span></span>

<span data-ttu-id="8ab40-105">파일이 나 기타 입력을 16 진수로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab40-105">Displays a file or other input as hexadecimal.</span></span>

## <span data-ttu-id="8ab40-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="8ab40-106">SYNTAX</span></span>

### <span data-ttu-id="8ab40-107">Path (기본값)</span><span class="sxs-lookup"><span data-stu-id="8ab40-107">Path (Default)</span></span>

```
Format-Hex [-Path] <string[]> [<CommonParameters>]
```

### <span data-ttu-id="8ab40-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="8ab40-108">LiteralPath</span></span>

```
Format-Hex -LiteralPath <string[]> [<CommonParameters>]
```

### <span data-ttu-id="8ab40-109">ByInputObject</span><span class="sxs-lookup"><span data-stu-id="8ab40-109">ByInputObject</span></span>

```
Format-Hex -InputObject <Object> [-Encoding <string>] [-Raw] [<CommonParameters>]
```

## <span data-ttu-id="8ab40-110">설명</span><span class="sxs-lookup"><span data-stu-id="8ab40-110">DESCRIPTION</span></span>

<span data-ttu-id="8ab40-111">`Format-Hex`Cmdlet은 파일 또는 기타 입력을 16 진수 값으로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab40-111">The `Format-Hex` cmdlet displays a file or other input as hexadecimal values.</span></span> <span data-ttu-id="8ab40-112">출력에서 문자의 오프셋을 확인 하려면 행의 맨 왼쪽에 있는 숫자를 해당 문자의 열 위쪽에 있는 숫자에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab40-112">To determine the offset of a character from the output, add the number at the leftmost of the row to the number at the top of the column for that character.</span></span>

<span data-ttu-id="8ab40-113">Cmdlet을 통해 `Format-Hex` 손상 된 파일이 나 파일 이름 확장명을 가질 수 없는 파일의 파일 형식을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ab40-113">The `Format-Hex` cmdlet can help you determine the file type of a corrupted file or a file that might not have a filename extension.</span></span> <span data-ttu-id="8ab40-114">이 cmdlet을 실행 한 다음 16 진수 출력을 읽어 파일 정보를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ab40-114">You can run this cmdlet, and then read the hexadecimal output to get file information.</span></span>

<span data-ttu-id="8ab40-115">파일에서를 사용 하 `Format-Hex` 는 경우이 cmdlet은 줄 바꿈 문자를 무시 하 고 파일의 전체 내용을 줄 바꿈 문자가 유지 된 한 문자열로 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab40-115">When using `Format-Hex` on a file, the cmdlet ignores newline characters and returns the entire contents of a file in one string with the newline characters preserved.</span></span>

## <span data-ttu-id="8ab40-116">예제</span><span class="sxs-lookup"><span data-stu-id="8ab40-116">EXAMPLES</span></span>

### <span data-ttu-id="8ab40-117">예제 1: 문자열의 16 진수 표현 가져오기</span><span class="sxs-lookup"><span data-stu-id="8ab40-117">Example 1: Get the hexadecimal representation of a string</span></span>

<span data-ttu-id="8ab40-118">이 명령은 문자열의 16 진수 값을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab40-118">This command returns the hexadecimal values of a string.</span></span>

```powershell
'Hello World' | Format-Hex
```

```Output
           00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F

00000000   48 65 6C 6C 6F 20 57 6F 72 6C 64                 Hello World
```

<span data-ttu-id="8ab40-119">**Hello World** 문자열은 파이프라인에서 cmdlet으로 전송 됩니다 `Format-Hex` .</span><span class="sxs-lookup"><span data-stu-id="8ab40-119">The string **Hello World** is sent down the pipeline to the `Format-Hex` cmdlet.</span></span> <span data-ttu-id="8ab40-120">의 16 진수 출력은 `Format-Hex` 문자열의 각 문자 값을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab40-120">The hexadecimal output from `Format-Hex` shows the values of each character in the string.</span></span>

### <span data-ttu-id="8ab40-121">예 2:16 진수 출력에서 파일 형식 찾기</span><span class="sxs-lookup"><span data-stu-id="8ab40-121">Example 2: Find a file type from hexadecimal output</span></span>

<span data-ttu-id="8ab40-122">이 예제에서는 16 진수 출력을 사용 하 여 파일 형식을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab40-122">This example uses the hexadecimal output to determine the file type.</span></span> <span data-ttu-id="8ab40-123">Cmdlet은 파일의 전체 경로와 16 진수 값을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab40-123">The cmdlet displays the file's full path and the hexadecimal values.</span></span>

<span data-ttu-id="8ab40-124">다음 명령을 테스트 하려면 로컬 컴퓨터에서 기존 PDF 파일의 복사본을 만들고 복사한 파일의 이름을 **t7f** 로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="8ab40-124">To test the following command, make a copy of an existing PDF file on your local computer and rename the copied file to **File.t7f** .</span></span>

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

<span data-ttu-id="8ab40-125">`Format-Hex`Cmdlet은 **Path** 매개 변수를 사용 하 여 현재 디렉터리의 파일 이름을 지정 `File.t7f` 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab40-125">The `Format-Hex` cmdlet uses the **Path** parameter to specify a filename in the current directory, `File.t7f`.</span></span> <span data-ttu-id="8ab40-126">파일 확장명은 `.t7f` 일반적이 지 않지만 16 진수 출력은 `%PDF` PDF 파일 임을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8ab40-126">The file extension `.t7f` is uncommon, but the hexadecimal output `%PDF` shows that it is a PDF file.</span></span>

### <span data-ttu-id="8ab40-127">예제 3: 원시 16 진수 출력 표시</span><span class="sxs-lookup"><span data-stu-id="8ab40-127">Example 3: Display raw hexadecimal output</span></span>

<span data-ttu-id="8ab40-128">기본적으로 `Format-Hex` opts는 숫자 데이터 형식의 압축 출력에 사용 됩니다. 값이 충분히 작은 경우 싱글바이트 또는 더블 바이트 시퀀스가 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ab40-128">By default `Format-Hex` opts for compact output of numeric data types: single-byte or double-byte sequences are used if the value is small enough.</span></span> <span data-ttu-id="8ab40-129">**Raw** 매개 변수는이 동작을 비활성화 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab40-129">The **Raw** parameter deactivates this behavior.</span></span>

```
PS> 1,2,3,1000 | Format-Hex

           Path:

           00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F

00000000   01 02 03 E8 03                                   ...è.


PS> 1,2,3,1000 | Format-Hex -Raw

           Path:

           00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F

00000000   01 00 00 00 02 00 00 00 03 00 00 00 E8 03 00 00  ............è...
```

<span data-ttu-id="8ab40-130">출력의 차이점을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab40-130">Notice the difference in output.</span></span> <span data-ttu-id="8ab40-131">**원시** 매개 변수는 숫자를 4 바이트 값으로 표시 하 고 해당 **Int32** 형식에 true를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab40-131">The **Raw** parameter displays the numbers as 4-byte values, true to their **Int32** types.</span></span>

## <span data-ttu-id="8ab40-132">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="8ab40-132">PARAMETERS</span></span>

### <span data-ttu-id="8ab40-133">-Encoding</span><span class="sxs-lookup"><span data-stu-id="8ab40-133">-Encoding</span></span>

<span data-ttu-id="8ab40-134">출력의 인코딩을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab40-134">Specifies the encoding of the output.</span></span> <span data-ttu-id="8ab40-135">이는 입력에만 적용 됩니다 `[string]` .</span><span class="sxs-lookup"><span data-stu-id="8ab40-135">This only applies to `[string]` input.</span></span> <span data-ttu-id="8ab40-136">매개 변수는 숫자 형식에는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8ab40-136">The parameter has no effect on numeric types.</span></span> <span data-ttu-id="8ab40-137">기본값은 `ASCII`입니다.</span><span class="sxs-lookup"><span data-stu-id="8ab40-137">The default value is `ASCII`.</span></span>

<span data-ttu-id="8ab40-138">이 매개 변수에 허용 되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8ab40-138">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="8ab40-139">`Ascii` ASCII (7 비트) 문자 집합을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab40-139">`Ascii` Uses ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="8ab40-140">`BigEndianUnicode` 에서는 u t f-16을 빅 endian 바이트 순서로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab40-140">`BigEndianUnicode` Uses UTF-16 with the big-endian byte order.</span></span>
- <span data-ttu-id="8ab40-141">`Unicode` 는 u t f-16을 약간 endian 바이트 순서로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab40-141">`Unicode` Uses UTF-16 with the little-endian byte order.</span></span>
- <span data-ttu-id="8ab40-142">`UTF7` 는 u t f-7을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab40-142">`UTF7` Uses UTF-7.</span></span>
- <span data-ttu-id="8ab40-143">`UTF8` 는 u t f-8을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab40-143">`UTF8` Uses UTF-8.</span></span>
- <span data-ttu-id="8ab40-144">`UTF32` 는 u t f-32을 작은 endian 바이트 순서로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab40-144">`UTF32` Uses UTF-32 with the little-endian byte order.</span></span>

<span data-ttu-id="8ab40-145">입력의 ASCII가 아닌 문자는 리터럴 문자로 출력 되어 `?` 정보 손실이 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab40-145">Non-ASCII characters in the input are output as literal `?` characters resulting in a loss of information.</span></span>

```yaml
Type: System.String
Parameter Sets: ByInputObject
Aliases:
Accepted values: ASCII, BigEndianUnicode, Unicode, UTF7, UTF8, UTF32

Required: False
Position: Named
Default value: ASCII
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8ab40-146">-InputObject</span><span class="sxs-lookup"><span data-stu-id="8ab40-146">-InputObject</span></span>

<span data-ttu-id="8ab40-147">파이프라인 입력에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ab40-147">Used for pipeline input.</span></span> <span data-ttu-id="8ab40-148">파이프라인 입력은 `[system.io.fileinfo]` 에서 파이프에 대 한 특정 스칼라 형식 및 인스턴스만 지원 `Get-ChildItem` 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab40-148">Pipeline input supports only certain scalar types and `[system.io.fileinfo]` instances for piping from `Get-ChildItem`.</span></span>

<span data-ttu-id="8ab40-149">지원 되는 스칼라 형식은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8ab40-149">The supported scalar types are:</span></span>

- `[string]`
- `[byte]`
- <span data-ttu-id="8ab40-150">`[int]`, `[int32]`</span><span class="sxs-lookup"><span data-stu-id="8ab40-150">`[int]`, `[int32]`</span></span>
- <span data-ttu-id="8ab40-151">`[long]`, `[int64]`</span><span class="sxs-lookup"><span data-stu-id="8ab40-151">`[long]`, `[int64]`</span></span>

```yaml
Type: System.Object
Parameter Sets: ByInputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="8ab40-152">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="8ab40-152">-LiteralPath</span></span>

<span data-ttu-id="8ab40-153">파일의 전체 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab40-153">Specifies the complete path to a file.</span></span> <span data-ttu-id="8ab40-154">**LiteralPath** 의 값은 입력 한 대로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ab40-154">The value of **LiteralPath** is used exactly as it is typed.</span></span>
<span data-ttu-id="8ab40-155">이 매개 변수는 와일드 카드 문자를 허용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8ab40-155">This parameter does not accept wildcard characters.</span></span> <span data-ttu-id="8ab40-156">파일에 대 한 여러 경로를 지정 하려면 경로를 쉼표로 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab40-156">To specify multiple paths to files, separate the paths with a comma.</span></span> <span data-ttu-id="8ab40-157">**LiteralPath** 매개 변수에 이스케이프 문자가 포함 되어 있으면 경로를 작은따옴표로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="8ab40-157">If the **LiteralPath** parameter includes escape characters, enclose the path in single quotation marks.</span></span> <span data-ttu-id="8ab40-158">PowerShell에서는 따옴표 붙은 단일 문자열의 문자를 이스케이프 시퀀스로 해석 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8ab40-158">PowerShell does not interpret any characters in a single quoted string as escape sequences.</span></span> <span data-ttu-id="8ab40-159">자세한 내용은 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8ab40-159">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8ab40-160">-Path</span><span class="sxs-lookup"><span data-stu-id="8ab40-160">-Path</span></span>

<span data-ttu-id="8ab40-161">파일의 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab40-161">Specifies the path to files.</span></span> <span data-ttu-id="8ab40-162">점 ()을 사용 `.` 하 여 현재 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab40-162">Use a dot (`.`) to specify the current location.</span></span> <span data-ttu-id="8ab40-163">와일드 카드 문자 ( `*` )가 허용 되며, 위치에 있는 모든 항목을 지정 하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ab40-163">The wildcard character (`*`) is accepted and can be used to specify all the items in a location.</span></span> <span data-ttu-id="8ab40-164">**Path** 매개 변수에 이스케이프 문자가 포함 되어 있으면 경로를 작은따옴표로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="8ab40-164">If the **Path** parameter includes escape characters, enclose the path in single quotation marks.</span></span> <span data-ttu-id="8ab40-165">파일에 대 한 여러 경로를 지정 하려면 경로를 쉼표로 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab40-165">To specify multiple paths to files, separate the paths with a comma.</span></span>

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

### <span data-ttu-id="8ab40-166">-Raw</span><span class="sxs-lookup"><span data-stu-id="8ab40-166">-Raw</span></span>

<span data-ttu-id="8ab40-167">기본적으로 `Format-Hex` opts는 숫자 데이터 형식의 압축 출력에 사용 됩니다. 값이 충분히 작은 경우 싱글바이트 또는 더블 바이트 시퀀스가 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ab40-167">By default `Format-Hex` opts for compact output of numeric data types: single-byte or double-byte sequences are used if the value is small enough.</span></span> <span data-ttu-id="8ab40-168">**Raw** 매개 변수는이 동작을 비활성화 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab40-168">The **Raw** parameter deactivates this behavior.</span></span>

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

### <span data-ttu-id="8ab40-169">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8ab40-169">CommonParameters</span></span>

<span data-ttu-id="8ab40-170">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="8ab40-170">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8ab40-171">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8ab40-171">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8ab40-172">입력</span><span class="sxs-lookup"><span data-stu-id="8ab40-172">INPUTS</span></span>

### <span data-ttu-id="8ab40-173">System.String</span><span class="sxs-lookup"><span data-stu-id="8ab40-173">System.String</span></span>

<span data-ttu-id="8ab40-174">이 cmdlet에 문자열을 파이프 하 여 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ab40-174">You can pipe a string to this cmdlet.</span></span>

## <span data-ttu-id="8ab40-175">출력</span><span class="sxs-lookup"><span data-stu-id="8ab40-175">OUTPUTS</span></span>

### <span data-ttu-id="8ab40-176">ByteCollection.</span><span class="sxs-lookup"><span data-stu-id="8ab40-176">Microsoft.PowerShell.Commands.ByteCollection</span></span>

<span data-ttu-id="8ab40-177">이 cmdlet은 **ByteCollection** 를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab40-177">This cmdlet returns a **ByteCollection** .</span></span> <span data-ttu-id="8ab40-178">이 개체는 바이트 컬렉션을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8ab40-178">This object represents a collection of bytes.</span></span> <span data-ttu-id="8ab40-179">바이트 컬렉션을에서 반환 하는 출력의 각 줄 처럼 형식이 지정 된 문자열로 변환 하는 메서드를 포함 `Format-Hex` 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab40-179">It includes methods that convert the collection of bytes to a string formatted like each line of output returned by `Format-Hex`.</span></span> <span data-ttu-id="8ab40-180">**Path** 또는 **LiteralPath** 매개 변수를 지정 하는 경우 개체에는 각 바이트를 포함 하는 파일의 경로도 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ab40-180">If you specify the **Path** or **LiteralPath** parameter, the object also contains the path of the file that contains each byte.</span></span>

## <span data-ttu-id="8ab40-181">참고</span><span class="sxs-lookup"><span data-stu-id="8ab40-181">NOTES</span></span>

<span data-ttu-id="8ab40-182">출력의 맨 오른쪽 열은 바이트를 문자로 렌더링 하려고 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab40-182">The right-most column of output tries to render the bytes as characters:</span></span>

<span data-ttu-id="8ab40-183">일반적으로 각 바이트는 유니코드 코드 포인트로 해석 됩니다 .이는 다음을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab40-183">Generally, each byte is interpreted as a Unicode code point, which means that:</span></span>

- <span data-ttu-id="8ab40-184">인쇄 가능한 ASCII 문자는 항상 올바르게 렌더링 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ab40-184">Printable ASCII characters are always rendered correctly</span></span>
- <span data-ttu-id="8ab40-185">멀티 바이트 UTF-8 문자는 올바르게 렌더링 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8ab40-185">Multi-byte UTF-8 characters never render correctly</span></span>
- <span data-ttu-id="8ab40-186">UTF-16 문자는 상위 바이트가 발생 하는 경우에만 올바르게 렌더링 됩니다 `NUL` .</span><span class="sxs-lookup"><span data-stu-id="8ab40-186">UTF-16 characters render correctly only if their high-order byte happens be `NUL`.</span></span>

## <span data-ttu-id="8ab40-187">관련 링크</span><span class="sxs-lookup"><span data-stu-id="8ab40-187">RELATED LINKS</span></span>

[<span data-ttu-id="8ab40-188">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="8ab40-188">about_Quoting_Rules</span></span>](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)

[<span data-ttu-id="8ab40-189">Format-Custom</span><span class="sxs-lookup"><span data-stu-id="8ab40-189">Format-Custom</span></span>](Format-Custom.md)

[<span data-ttu-id="8ab40-190">Format-List</span><span class="sxs-lookup"><span data-stu-id="8ab40-190">Format-List</span></span>](Format-List.md)

[<span data-ttu-id="8ab40-191">Format-Table</span><span class="sxs-lookup"><span data-stu-id="8ab40-191">Format-Table</span></span>](Format-Table.md)

[<span data-ttu-id="8ab40-192">Format-Wide</span><span class="sxs-lookup"><span data-stu-id="8ab40-192">Format-Wide</span></span>](Format-Wide.md)
