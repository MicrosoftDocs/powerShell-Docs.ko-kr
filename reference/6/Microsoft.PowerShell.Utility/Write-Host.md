---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-host?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Host
ms.openlocfilehash: f0b7542d551fa0dbbdec186980dcdb7ac600b60c
ms.sourcegitcommit: 758e6dbb428295698d4852b3e19f5d03deade037
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/15/2020
ms.locfileid: "93219937"
---
# <span data-ttu-id="9cba5-103">Write-Host</span><span class="sxs-lookup"><span data-stu-id="9cba5-103">Write-Host</span></span>

## <span data-ttu-id="9cba5-104">개요</span><span class="sxs-lookup"><span data-stu-id="9cba5-104">SYNOPSIS</span></span>

<span data-ttu-id="9cba5-105">사용자 지정된 출력을 호스트에 씁니다.</span><span class="sxs-lookup"><span data-stu-id="9cba5-105">Writes customized output to a host.</span></span>

## <span data-ttu-id="9cba5-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9cba5-106">SYNTAX</span></span>

```
Write-Host [[-Object] <Object>] [-NoNewline] [-Separator <Object>] [-ForegroundColor <ConsoleColor>]
 [-BackgroundColor <ConsoleColor>] [<CommonParameters>]
```

## <span data-ttu-id="9cba5-107">설명</span><span class="sxs-lookup"><span data-stu-id="9cba5-107">DESCRIPTION</span></span>

<span data-ttu-id="9cba5-108">`Write-Host`Cmdlet의 기본 용도는 사용자에 게 [읽기 호스트](Read-Host.md)와의 입력을 요청 하는 경우 처럼 컬러 텍스트 인쇄와 같이-(호스트)-표시 전용 출력을 생성 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="9cba5-108">The `Write-Host` cmdlet's primary purpose is to produce for-(host)-display-only output, such as printing colored text like when prompting the user for input in conjunction with [Read-Host](Read-Host.md).</span></span>
<span data-ttu-id="9cba5-109">`Write-Host`[ToString ()](/dotnet/api/system.object.tostring) 메서드를 사용 하 여 출력을 작성 합니다.</span><span class="sxs-lookup"><span data-stu-id="9cba5-109">`Write-Host` uses the [ToString()](/dotnet/api/system.object.tostring) method to write the output.</span></span> <span data-ttu-id="9cba5-110">반대로 데이터를 파이프라인으로 출력 하려면 [쓰기 출력](Write-Output.md) 또는 암시적 출력을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9cba5-110">By contrast, to output data to the pipeline, use [Write-Output](Write-Output.md) or implicit output.</span></span>

<span data-ttu-id="9cba5-111">매개 변수를 사용 하 여 텍스트 색을 지정 하 `ForegroundColor` 고, 매개 변수를 사용 하 여 배경색을 지정할 수 있습니다 `BackgroundColor` .</span><span class="sxs-lookup"><span data-stu-id="9cba5-111">You can specify the color of text by using the `ForegroundColor` parameter, and you can specify the background color by using the `BackgroundColor` parameter.</span></span> <span data-ttu-id="9cba5-112">Separator 매개 변수를 사용하면 표시된 개체를 구분하는 데 사용할 문자열을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9cba5-112">The Separator parameter lets you specify a string to use to separate displayed objects.</span></span> <span data-ttu-id="9cba5-113">특정 결과는 PowerShell을 호스트 하는 프로그램에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="9cba5-113">The particular result depends on the program that is hosting PowerShell.</span></span>

> [!NOTE]
> <span data-ttu-id="9cba5-114">Windows PowerShell 5.0부터 `Write-Host` 은이에 대 한 래퍼로,를 사용 하 여 `Write-Information` 출력을 `Write-Host` 정보 스트림으로 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9cba5-114">Starting in Windows PowerShell 5.0, `Write-Host` is a wrapper for `Write-Information` This allows you to use `Write-Host` to emit output to the information stream.</span></span> <span data-ttu-id="9cba5-115">이를 통해 이전 버전과의 호환성을 유지 하면서 **를 사용** 하 여 작성 된 데이터를 **캡처하거나** 제거할 수 있습니다 `Write-Host` .</span><span class="sxs-lookup"><span data-stu-id="9cba5-115">This enables the **capture** or **suppression** of data written using `Write-Host` while preserving backwards compatibility.</span></span>
>
> <span data-ttu-id="9cba5-116">`$InformationPreference`기본 설정 변수 및 `InformationAction` 일반 매개 변수는 메시지에 영향을 주지 않습니다 `Write-Host` .</span><span class="sxs-lookup"><span data-stu-id="9cba5-116">The `$InformationPreference` preference variable and `InformationAction` common parameter do not affect `Write-Host` messages.</span></span> <span data-ttu-id="9cba5-117">이 규칙의 예외는 효과적으로 출력을 억제 하는입니다 `-InformationAction Ignore` `Write-Host` .</span><span class="sxs-lookup"><span data-stu-id="9cba5-117">The exception to this rule is `-InformationAction Ignore`, which effectively suppresses `Write-Host` output.</span></span> <span data-ttu-id="9cba5-118">("예제 5" 참조)</span><span class="sxs-lookup"><span data-stu-id="9cba5-118">(see "Example 5")</span></span>

## <span data-ttu-id="9cba5-119">예제</span><span class="sxs-lookup"><span data-stu-id="9cba5-119">EXAMPLES</span></span>

### <span data-ttu-id="9cba5-120">예제 1: 새 줄을 추가 하지 않고 콘솔에 쓰기</span><span class="sxs-lookup"><span data-stu-id="9cba5-120">Example 1: Write to the console without adding a new line</span></span>

```powershell
Write-Host "no newline test " -NoNewline
Write-Host "second string"
```

```output
no newline test second string
```

<span data-ttu-id="9cba5-121">이 명령은 매개 변수를 사용 하 여 ' 줄 바꿈 테스트 없음 ' 문자열을 표시 합니다 `NoNewline` .</span><span class="sxs-lookup"><span data-stu-id="9cba5-121">This command displays the string 'no newline test' with the `NoNewline` parameter.</span></span>

<span data-ttu-id="9cba5-122">두 번째 문자열이 작성 되지만 문자열을 구분 하는 줄 바꿈이 없기 때문에 첫 번째 문자열이 첫 번째 문자열과 같은 줄에 끝납니다.</span><span class="sxs-lookup"><span data-stu-id="9cba5-122">A second string is written, but it ends up on the same line as the first due to the absence of a newline separating the strings.</span></span>

### <span data-ttu-id="9cba5-123">예제 2: 콘솔에 쓰기 및 구분 기호 포함</span><span class="sxs-lookup"><span data-stu-id="9cba5-123">Example 2: Write to the console and include a separator</span></span>

```powershell
Write-Host (2,4,6,8,10,12) -Separator ", +2= "
```

```output
2, +2= 4, +2= 6, +2= 8, +2= 10, +2= 12
```

이 명령은 2에서 12 사이의 짝수를 표시 합니다. <span data-ttu-id="9cba5-125">**구분 기호** 매개 변수는 문자열 `, +2= ` (쉼표, 공백,, `+` `2` , `=` , 공백)을 추가 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9cba5-125">The **Separator** parameter is used to add the string `, +2= ` (comma, space, `+`, `2`, `=`, space).</span></span>

### <span data-ttu-id="9cba5-126">예제 3: 다른 텍스트 및 배경색으로 쓰기</span><span class="sxs-lookup"><span data-stu-id="9cba5-126">Example 3: Write with different text and background colors</span></span>

```powershell
Write-Host (2,4,6,8,10,12) -Separator ", -> " -ForegroundColor DarkGreen -BackgroundColor White
```

```output
2, -> 4, -> 6, -> 8, -> 10, -> 12
```

<span data-ttu-id="9cba5-127">이 명령은 2에서 12 사이의 짝수를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="9cba5-127">This command displays the even numbers from two through twelve.</span></span> <span data-ttu-id="9cba5-128">매개 변수를 사용 하 여 `ForegroundColor` 진한 녹색 텍스트를 출력 하 고 매개 변수를 사용 하 여 `BackgroundColor` 흰색 배경을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="9cba5-128">It uses the `ForegroundColor` parameter to output dark green text and the `BackgroundColor` parameter to display a white background.</span></span>

### <span data-ttu-id="9cba5-129">예제 4: 다른 텍스트 및 배경색으로 쓰기</span><span class="sxs-lookup"><span data-stu-id="9cba5-129">Example 4: Write with different text and background colors</span></span>

```powershell
Write-Host "Red on white text." -ForegroundColor red -BackgroundColor white
```

```output
Red on white text.
```

<span data-ttu-id="9cba5-130">이 명령은 "Red on white text" 문자열을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="9cba5-130">This command displays the string "Red on white text."</span></span> <span data-ttu-id="9cba5-131">매개 변수에 정의 된 대로 텍스트가 빨간색으로 바뀝니다 `ForegroundColor` .</span><span class="sxs-lookup"><span data-stu-id="9cba5-131">The text is red, as defined by the `ForegroundColor` parameter.</span></span> <span data-ttu-id="9cba5-132">배경은 매개 변수로 정의 된 흰색입니다 `BackgroundColor` .</span><span class="sxs-lookup"><span data-stu-id="9cba5-132">The background is white, as defined by the `BackgroundColor` parameter.</span></span>

### <span data-ttu-id="9cba5-133">예 5: Write-Host 출력 표시 안 함</span><span class="sxs-lookup"><span data-stu-id="9cba5-133">Example 5: Suppress output from Write-Host</span></span>

```powershell
# The following two statements can be used to effectively suppress output from Write-Host
Write-Host "I won't print" -InformationAction Ignore
Write-Host "I won't print" 6>$null
```

```output

```

<span data-ttu-id="9cba5-134">이러한 명령은 cmdlet의 출력을 효과적으로 표시 하지 않습니다 `Write-Host` .</span><span class="sxs-lookup"><span data-stu-id="9cba5-134">These commands effectively suppress output of the `Write-Host` cmdlet.</span></span> <span data-ttu-id="9cba5-135">첫 번째 `InformationAction` 매개 변수는 값과 함께 매개 변수를 사용 하 여 `Ignore` 정보 스트림에 대 한 출력을 표시 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9cba5-135">The first one uses the `InformationAction` parameter with the `Ignore` Value to suppress output to the information stream.</span></span>
<span data-ttu-id="9cba5-136">두 번째 예제에서는 명령의 정보 스트림을 변수로 리디렉션하여이를 표시 하지 `$null` 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9cba5-136">The second example redirects the information stream of the command to the `$null` variable and thereby suppresses it.</span></span>

## <span data-ttu-id="9cba5-137">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9cba5-137">PARAMETERS</span></span>

### <span data-ttu-id="9cba5-138">-BackgroundColor</span><span class="sxs-lookup"><span data-stu-id="9cba5-138">-BackgroundColor</span></span>

<span data-ttu-id="9cba5-139">배경색을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9cba5-139">Specifies the background color.</span></span> <span data-ttu-id="9cba5-140">기본값은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9cba5-140">There is no default.</span></span> <span data-ttu-id="9cba5-141">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9cba5-141">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="9cba5-142">검정</span><span class="sxs-lookup"><span data-stu-id="9cba5-142">Black</span></span>
- <span data-ttu-id="9cba5-143">진한 파랑</span><span class="sxs-lookup"><span data-stu-id="9cba5-143">DarkBlue</span></span>
- <span data-ttu-id="9cba5-144">진한 녹색</span><span class="sxs-lookup"><span data-stu-id="9cba5-144">DarkGreen</span></span>
- <span data-ttu-id="9cba5-145">진한 녹청</span><span class="sxs-lookup"><span data-stu-id="9cba5-145">DarkCyan</span></span>
- <span data-ttu-id="9cba5-146">진한 빨강</span><span class="sxs-lookup"><span data-stu-id="9cba5-146">DarkRed</span></span>
- <span data-ttu-id="9cba5-147">진한 자홍</span><span class="sxs-lookup"><span data-stu-id="9cba5-147">DarkMagenta</span></span>
- <span data-ttu-id="9cba5-148">진한 노랑</span><span class="sxs-lookup"><span data-stu-id="9cba5-148">DarkYellow</span></span>
- <span data-ttu-id="9cba5-149">회색</span><span class="sxs-lookup"><span data-stu-id="9cba5-149">Gray</span></span>
- <span data-ttu-id="9cba5-150">진한 회색</span><span class="sxs-lookup"><span data-stu-id="9cba5-150">DarkGray</span></span>
- <span data-ttu-id="9cba5-151">파랑</span><span class="sxs-lookup"><span data-stu-id="9cba5-151">Blue</span></span>
- <span data-ttu-id="9cba5-152">녹색</span><span class="sxs-lookup"><span data-stu-id="9cba5-152">Green</span></span>
- <span data-ttu-id="9cba5-153">녹청</span><span class="sxs-lookup"><span data-stu-id="9cba5-153">Cyan</span></span>
- <span data-ttu-id="9cba5-154">빨간색</span><span class="sxs-lookup"><span data-stu-id="9cba5-154">Red</span></span>
- <span data-ttu-id="9cba5-155">자홍</span><span class="sxs-lookup"><span data-stu-id="9cba5-155">Magenta</span></span>
- <span data-ttu-id="9cba5-156">노란색</span><span class="sxs-lookup"><span data-stu-id="9cba5-156">Yellow</span></span>
- <span data-ttu-id="9cba5-157">흰색</span><span class="sxs-lookup"><span data-stu-id="9cba5-157">White</span></span>

```yaml
Type: System.ConsoleColor
Parameter Sets: (All)
Aliases:
Accepted values: Black, DarkBlue, DarkGreen, DarkCyan, DarkRed, DarkMagenta, DarkYellow, Gray, DarkGray, Blue, Green, Cyan, Red, Magenta, Yellow, White

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9cba5-158">-ForegroundColor</span><span class="sxs-lookup"><span data-stu-id="9cba5-158">-ForegroundColor</span></span>

<span data-ttu-id="9cba5-159">텍스트 색을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9cba5-159">Specifies the text color.</span></span> <span data-ttu-id="9cba5-160">기본값은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9cba5-160">There is no default.</span></span> <span data-ttu-id="9cba5-161">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9cba5-161">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="9cba5-162">검정</span><span class="sxs-lookup"><span data-stu-id="9cba5-162">Black</span></span>
- <span data-ttu-id="9cba5-163">진한 파랑</span><span class="sxs-lookup"><span data-stu-id="9cba5-163">DarkBlue</span></span>
- <span data-ttu-id="9cba5-164">진한 녹색</span><span class="sxs-lookup"><span data-stu-id="9cba5-164">DarkGreen</span></span>
- <span data-ttu-id="9cba5-165">진한 녹청</span><span class="sxs-lookup"><span data-stu-id="9cba5-165">DarkCyan</span></span>
- <span data-ttu-id="9cba5-166">진한 빨강</span><span class="sxs-lookup"><span data-stu-id="9cba5-166">DarkRed</span></span>
- <span data-ttu-id="9cba5-167">진한 자홍</span><span class="sxs-lookup"><span data-stu-id="9cba5-167">DarkMagenta</span></span>
- <span data-ttu-id="9cba5-168">진한 노랑</span><span class="sxs-lookup"><span data-stu-id="9cba5-168">DarkYellow</span></span>
- <span data-ttu-id="9cba5-169">회색</span><span class="sxs-lookup"><span data-stu-id="9cba5-169">Gray</span></span>
- <span data-ttu-id="9cba5-170">진한 회색</span><span class="sxs-lookup"><span data-stu-id="9cba5-170">DarkGray</span></span>
- <span data-ttu-id="9cba5-171">파랑</span><span class="sxs-lookup"><span data-stu-id="9cba5-171">Blue</span></span>
- <span data-ttu-id="9cba5-172">녹색</span><span class="sxs-lookup"><span data-stu-id="9cba5-172">Green</span></span>
- <span data-ttu-id="9cba5-173">녹청</span><span class="sxs-lookup"><span data-stu-id="9cba5-173">Cyan</span></span>
- <span data-ttu-id="9cba5-174">빨간색</span><span class="sxs-lookup"><span data-stu-id="9cba5-174">Red</span></span>
- <span data-ttu-id="9cba5-175">자홍</span><span class="sxs-lookup"><span data-stu-id="9cba5-175">Magenta</span></span>
- <span data-ttu-id="9cba5-176">노란색</span><span class="sxs-lookup"><span data-stu-id="9cba5-176">Yellow</span></span>
- <span data-ttu-id="9cba5-177">흰색</span><span class="sxs-lookup"><span data-stu-id="9cba5-177">White</span></span>

```yaml
Type: System.ConsoleColor
Parameter Sets: (All)
Aliases:
Accepted values: Black, DarkBlue, DarkGreen, DarkCyan, DarkRed, DarkMagenta, DarkYellow, Gray, DarkGray, Blue, Green, Cyan, Red, Magenta, Yellow, White

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9cba5-178">-NoNewline</span><span class="sxs-lookup"><span data-stu-id="9cba5-178">-NoNewline</span></span>

<span data-ttu-id="9cba5-179">입력 개체의 문자열 표현은 연결 되어 출력을 형성 합니다.</span><span class="sxs-lookup"><span data-stu-id="9cba5-179">The string representations of the input objects are concatenated to form the output.</span></span> <span data-ttu-id="9cba5-180">출력 문자열 사이에 공백이 나 줄바꿈 삽입 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9cba5-180">No spaces or newlines are inserted between the output strings.</span></span> <span data-ttu-id="9cba5-181">마지막 출력 문자열 뒤에는 줄 바꿈이 추가 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9cba5-181">No newline is added after the last output string.</span></span>

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

### <span data-ttu-id="9cba5-182">-개체</span><span class="sxs-lookup"><span data-stu-id="9cba5-182">-Object</span></span>

<span data-ttu-id="9cba5-183">호스트에 표시할 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="9cba5-183">Objects to display in the host.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases: Msg, Message

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="9cba5-184">-구분 기호</span><span class="sxs-lookup"><span data-stu-id="9cba5-184">-Separator</span></span>

<span data-ttu-id="9cba5-185">호스트에서 표시 하는 개체 사이에 삽입할 구분 기호 문자열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9cba5-185">Specifies a separator string to insert between objects displayed by the host.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9cba5-186">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9cba5-186">CommonParameters</span></span>
<span data-ttu-id="9cba5-187">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9cba5-187">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9cba5-188">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9cba5-188">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9cba5-189">입력</span><span class="sxs-lookup"><span data-stu-id="9cba5-189">INPUTS</span></span>

### <span data-ttu-id="9cba5-190">System.Object</span><span class="sxs-lookup"><span data-stu-id="9cba5-190">System.Object</span></span>

<span data-ttu-id="9cba5-191">호스트에 쓸 개체를 파이프할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9cba5-191">You can pipe objects to be written to the host.</span></span>

## <span data-ttu-id="9cba5-192">출력</span><span class="sxs-lookup"><span data-stu-id="9cba5-192">OUTPUTS</span></span>

### <span data-ttu-id="9cba5-193">없음</span><span class="sxs-lookup"><span data-stu-id="9cba5-193">None</span></span>

<span data-ttu-id="9cba5-194">`Write-Host` 호스트에 개체를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="9cba5-194">`Write-Host` sends the objects to the host.</span></span> <span data-ttu-id="9cba5-195">개체를 반환하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9cba5-195">It does not return any objects.</span></span> <span data-ttu-id="9cba5-196">그러나 호스트는로 보내는 개체를 표시 합니다 `Write-Host` .</span><span class="sxs-lookup"><span data-stu-id="9cba5-196">However, the host displays the objects that `Write-Host` sends to it.</span></span>

## <span data-ttu-id="9cba5-197">참고</span><span class="sxs-lookup"><span data-stu-id="9cba5-197">NOTES</span></span>

- <span data-ttu-id="9cba5-198">호스트에 컬렉션을 작성 하는 경우 컬렉션의 요소는 단일 공백으로 구분 된 동일한 줄에 인쇄 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9cba5-198">When writing a collection to the host, elements of the collection are printed on the same line separated by a single space.</span></span> <span data-ttu-id="9cba5-199">**구분 기호** 매개 변수를 사용 하 여이를 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9cba5-199">This can be overridden with the **Separator** parameter.</span></span>

- <span data-ttu-id="9cba5-200">속성이 있는 개체와 같은 기본이 아닌 데이터 형식은 예기치 않은 결과를 발생 시킬 수 있으며 의미 있는 출력을 제공 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9cba5-200">Non-primitive data types such as objects with properties can cause unexpected results and not provide meaningful output.</span></span> <span data-ttu-id="9cba5-201">예를 들어는 `Write-Host @{a = 1; b = 2}` `System.Collections.DictionaryEntry System.Collections.DictionaryEntry` 호스트에 인쇄 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9cba5-201">For example, `Write-Host @{a = 1; b = 2}` will print `System.Collections.DictionaryEntry System.Collections.DictionaryEntry` to the host.</span></span>

## <span data-ttu-id="9cba5-202">관련 링크</span><span class="sxs-lookup"><span data-stu-id="9cba5-202">RELATED LINKS</span></span>

[<span data-ttu-id="9cba5-203">Clear-Host</span><span class="sxs-lookup"><span data-stu-id="9cba5-203">Clear-Host</span></span>](../Microsoft.PowerShell.Core/Clear-Host.md)

[<span data-ttu-id="9cba5-204">Out-Host</span><span class="sxs-lookup"><span data-stu-id="9cba5-204">Out-Host</span></span>](../Microsoft.PowerShell.Core/Out-Host.md)

[<span data-ttu-id="9cba5-205">Write-Debug</span><span class="sxs-lookup"><span data-stu-id="9cba5-205">Write-Debug</span></span>](Write-Debug.md)

[<span data-ttu-id="9cba5-206">쓰기 오류</span><span class="sxs-lookup"><span data-stu-id="9cba5-206">Write-Error</span></span>](Write-Error.md)

[<span data-ttu-id="9cba5-207">Write-Output</span><span class="sxs-lookup"><span data-stu-id="9cba5-207">Write-Output</span></span>](Write-Output.md)

[<span data-ttu-id="9cba5-208">Write-Progress</span><span class="sxs-lookup"><span data-stu-id="9cba5-208">Write-Progress</span></span>](Write-Progress.md)

[<span data-ttu-id="9cba5-209">Write-Verbose</span><span class="sxs-lookup"><span data-stu-id="9cba5-209">Write-Verbose</span></span>](Write-Verbose.md)

[<span data-ttu-id="9cba5-210">Write-Warning</span><span class="sxs-lookup"><span data-stu-id="9cba5-210">Write-Warning</span></span>](Write-Warning.md)
