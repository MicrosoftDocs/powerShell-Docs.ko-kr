---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertfrom-string?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-String
ms.openlocfilehash: 665a0ca8332c4052b59362c7947e408ba811c5f2
ms.sourcegitcommit: c4906f4c9fa4ef1a16dcd6dd00ff960d19446d71
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/01/2020
ms.locfileid: "93219794"
---
# <span data-ttu-id="040ca-103">ConvertFrom-String</span><span class="sxs-lookup"><span data-stu-id="040ca-103">ConvertFrom-String</span></span>

## <span data-ttu-id="040ca-104">개요</span><span class="sxs-lookup"><span data-stu-id="040ca-104">SYNOPSIS</span></span>
<span data-ttu-id="040ca-105">문자열 콘텐츠에서 구조화 된 속성을 추출 하 고 구문 분석 합니다.</span><span class="sxs-lookup"><span data-stu-id="040ca-105">Extracts and parses structured properties from string content.</span></span>

## <span data-ttu-id="040ca-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="040ca-106">SYNTAX</span></span>

### <span data-ttu-id="040ca-107">ByDelimiter (기본값)</span><span class="sxs-lookup"><span data-stu-id="040ca-107">ByDelimiter (Default)</span></span>

```
ConvertFrom-String [-Delimiter <String>] [-PropertyNames <String[]>] [-InputObject] <String>
 [<CommonParameters>]
```

### <span data-ttu-id="040ca-108">템플릿 구문 분석</span><span class="sxs-lookup"><span data-stu-id="040ca-108">TemplateParsing</span></span>

```
ConvertFrom-String [-TemplateFile <String[]>] [-TemplateContent <String[]>] [-IncludeExtent] [-UpdateTemplate]
 [-InputObject] <String> [<CommonParameters>]
```

## <span data-ttu-id="040ca-109">설명</span><span class="sxs-lookup"><span data-stu-id="040ca-109">DESCRIPTION</span></span>

<span data-ttu-id="040ca-110">**Convertfrom-csv** cmdlet은 문자열 콘텐츠에서 구조화 된 속성을 추출 하 고 구문 분석 합니다.</span><span class="sxs-lookup"><span data-stu-id="040ca-110">The **ConvertFrom-String** cmdlet extracts and parses structured properties from string content.</span></span>
<span data-ttu-id="040ca-111">이 cmdlet은 기존 텍스트 스트림에서 텍스트를 구문 분석 하 여 개체를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="040ca-111">This cmdlet generates an object by parsing text from a traditional text stream.</span></span>
<span data-ttu-id="040ca-112">파이프라인의 각 문자열에 대해 cmdlet은 구분 기호 또는 구문 분석 식으로 입력을 분할 한 다음 각 결과 분할 요소에 속성 이름을 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="040ca-112">For each string in the pipeline, the cmdlet splits the input by either a delimiter or a parse expression, and then assigns property names to each of the resulting split elements.</span></span>
<span data-ttu-id="040ca-113">이러한 속성 이름을 제공할 수 있습니다. 그렇지 않은 경우 자동으로 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="040ca-113">You can provide these property names; if you do not, they are automatically generated for you.</span></span>

<span data-ttu-id="040ca-114">Cmdlet의 기본 매개 변수 집합 **Bydelimiter** 는 정규식 구분 기호에서 정확 하 게 분할 됩니다.</span><span class="sxs-lookup"><span data-stu-id="040ca-114">The cmdlet's default parameter set, **ByDelimiter** , splits exactly on the regular expression delimiter.</span></span>
<span data-ttu-id="040ca-115">Cmdlet에서와 같이 따옴표 일치 또는 구분 기호 이스케이프를 수행 하지 않습니다 `Import-Csv` .</span><span class="sxs-lookup"><span data-stu-id="040ca-115">It does not perform quote matching or delimiter escaping as the `Import-Csv` cmdlet does.</span></span>

<span data-ttu-id="040ca-116">Cmdlet의 대체 매개 변수 집합 인 템플릿 **구문 분석** 은 정규식에 의해 캡처된 그룹에서 요소를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="040ca-116">The cmdlet's alternate parameter set, **TemplateParsing** , generates elements from the groups that are captured by a regular expression.</span></span> <span data-ttu-id="040ca-117">정규식에 대 한 자세한 내용은 [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="040ca-117">For more information on regular expressions, see [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md).</span></span>

<span data-ttu-id="040ca-118">이 cmdlet은 기본 구분 구문 분석 및 자동 생성 된 예제 기반 구문 분석의 두 가지 모드를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="040ca-118">This cmdlet supports two modes: basic delimited parsing, and automatically-generated, example-driven parsing.</span></span>

<span data-ttu-id="040ca-119">기본적으로 구분 구문 분석에서는 입력을 공백으로 분할하고 결과 그룹에 속성 이름을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="040ca-119">Delimited parsing, by default, splits the input at white space, and assigns property names to the resulting groups.</span></span>

<span data-ttu-id="040ca-120">결과를 cmdlet 중 하나로 파이프 하 여 구분 기호를 사용자 지정 `ConvertFrom-String` `Format-*` 하거나 **구분 기호** 매개 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="040ca-120">You can customize the delimiter by piping the `ConvertFrom-String` results into one of the `Format-*` cmdlets, or you can use the **Delimiter** parameter.</span></span>

<span data-ttu-id="040ca-121">또한이 cmdlet은 [FlashExtract, Microsoft research의 연구 작업](https://www.microsoft.com/research/publication/flashextract-framework-data-extraction-examples/)을 기반으로 자동 생성 된 예제 기반 구문 분석도 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="040ca-121">The cmdlet also supports automatically-generated, example-driven parsing based on the [FlashExtract, research work by Microsoft Research](https://www.microsoft.com/research/publication/flashextract-framework-data-extraction-examples/).</span></span>

## <span data-ttu-id="040ca-122">예제</span><span class="sxs-lookup"><span data-stu-id="040ca-122">EXAMPLES</span></span>

### <span data-ttu-id="040ca-123">예제 1: 기본 속성 이름을 사용 하 여 개체 생성</span><span class="sxs-lookup"><span data-stu-id="040ca-123">Example 1: Generate an object with default property names</span></span>

```powershell
"Hello World" | ConvertFrom-String
```

```Output
P1    P2
--    --
Hello World
```

<span data-ttu-id="040ca-124">이 명령은 기본 속성 이름 **P1** 및 **P2** 를 사용 하 여 개체를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="040ca-124">This command generates an object with default property names, **P1** and **P2**.</span></span>

### <span data-ttu-id="040ca-125">예 1A: 생성 된 개체를 알려면 가져오기</span><span class="sxs-lookup"><span data-stu-id="040ca-125">Example 1A: Get to know the generated object</span></span>

<span data-ttu-id="040ca-126">이 명령은 속성이 **P1** , **P2** 인 개체를 하나 생성 합니다. 기본적으로 두 속성은 모두 **문자열** 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="040ca-126">This command generates one object with properties **P1** , **P2** ; both properties are of **String** type, by default.</span></span>

```powershell
"Hello World" | ConvertFrom-String | Get-Member
```

```Output

   TypeName: System.Management.Automation.PSCustomObject

Name        MemberType   Definition
----        ----------   ----------
Equals      Method       bool Equals(System.Object obj)
GetHashCode Method       int GetHashCode()
GetType     Method       type GetType()
ToString    Method       string ToString()
P1          NoteProperty string P1=Hello
P2          NoteProperty string P2=World
```

### <span data-ttu-id="040ca-127">예제 2: 구분 기호를 사용 하 여 기본 속성 이름으로 개체 생성</span><span class="sxs-lookup"><span data-stu-id="040ca-127">Example 2: Generate an object with default property names using a delimiter</span></span>

<span data-ttu-id="040ca-128">이 명령은 백슬래시 ()를 구분 기호로 사용 하 여 도메인과 사용자 이름을 사용 하 여 개체를 생성 `\` 합니다.</span><span class="sxs-lookup"><span data-stu-id="040ca-128">This command generates an object with a domain and username using the backslash (`\`) as the delimiter.</span></span> <span data-ttu-id="040ca-129">정규식을 사용할 때 백슬래시 문자는 다른 백슬래시로 이스케이프 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="040ca-129">The backslash character must be escaped with another backslash when using regular expressions.</span></span>

```powershell
"Contoso\Administrator" | ConvertFrom-String -Delimiter "\\"
```

```Output
P1      P2
--      --
Contoso Administrator
```

### <span data-ttu-id="040ca-130">예제 3: 두 개의 명명 된 속성을 포함 하는 개체 생성</span><span class="sxs-lookup"><span data-stu-id="040ca-130">Example 3: Generate an object that contains two named properties</span></span>

<span data-ttu-id="040ca-131">다음 예제에서는 Windows 호스트 파일 항목에서 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="040ca-131">The following example creates objects from Windows hosts file entries.</span></span>

```powershell
$content = Get-Content C:\Windows\System32\drivers\etc\hosts
$content = $content -match "^[^#]"
$content | ConvertFrom-String -PropertyNames IP, Server
```

```Output
IP             Server
--             ------
192.168.7.10   W2012R2
192.168.7.20   W2016
192.168.7.101  WIN8
192.168.7.102  WIN10
```

<span data-ttu-id="040ca-132">`Get-Content`Cmdlet은에 Windows 호스트 파일의 콘텐츠를 저장 합니다 `$content` .</span><span class="sxs-lookup"><span data-stu-id="040ca-132">The `Get-Content` cmdlet stores the content of a Windows hosts file in `$content`.</span></span> <span data-ttu-id="040ca-133">두 번째 명령은 ()로 시작 하지 않는 줄과 일치 하는 정규식을 사용 하 여 호스트 파일의 시작 부분에 있는 모든 주석을 제거 합니다 `#` .</span><span class="sxs-lookup"><span data-stu-id="040ca-133">The second command removes any comments at the beginning of the hosts file using a regular expression that matches any line that does not start with (`#`).</span></span> <span data-ttu-id="040ca-134">마지막 명령은 나머지 텍스트를 **서버** 및 **IP** 속성이 있는 개체로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="040ca-134">The last command converts the remaining text into objects with **Server** and **IP** properties.</span></span>

### <span data-ttu-id="040ca-135">예 4: 식을 TemplateContent 매개 변수 값으로 사용 하 여 결과를 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="040ca-135">Example 4: Use an expression as the value of the TemplateContent parameter, save the results in a variable.</span></span>

<span data-ttu-id="040ca-136">이 명령은 **TemplateContent** 매개 변수 값으로 식을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="040ca-136">This command uses an expression as the value of the **TemplateContent** parameter.</span></span>
<span data-ttu-id="040ca-137">식은 편의상 변수에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="040ca-137">The expression is saved in a variable for simplicity.</span></span>
<span data-ttu-id="040ca-138">Windows PowerShell은 이제 파이프라인에서 사용 되는 문자열에 `ConvertFrom-String` 세 개의 속성이 있음을 이해 합니다.</span><span class="sxs-lookup"><span data-stu-id="040ca-138">Windows PowerShell understands now that the string that is used on the pipeline to `ConvertFrom-String` has three properties:</span></span>

- <span data-ttu-id="040ca-139">**이름**</span><span class="sxs-lookup"><span data-stu-id="040ca-139">**Name**</span></span>
- <span data-ttu-id="040ca-140">**내선**</span><span class="sxs-lookup"><span data-stu-id="040ca-140">**phone**</span></span>
- <span data-ttu-id="040ca-141">**발전할**</span><span class="sxs-lookup"><span data-stu-id="040ca-141">**age**</span></span>

```powershell
$template = @'
{Name*:Phoebe Cat}, {phone:425-123-6789}, {age:6}
{Name*:Lucky Shot}, {phone:(206) 987-4321}, {age:12}
'@

$testText = @'
Phoebe Cat, 425-123-6789, 6
Lucky Shot, (206) 987-4321, 12
Elephant Wise, 425-888-7766, 87
Wild Shrimp, (111)  222-3333, 1
'@

$PersonalData = $testText | ConvertFrom-String -TemplateContent $template
Write-output ("Pet items found: " + ($PersonalData.Count))
$PersonalData
```

```Output
Pet items found: 4

Name          phone           age
----          -----           ---
Phoebe Cat    425-123-6789    6
Lucky Shot    (206) 987-4321  12
Elephant Wise 425-888-7766    87
Wild Shrimp   (111)  222-3333 1
```

<span data-ttu-id="040ca-142">입력의 각 줄은 샘플 일치 항목에 의해 평가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="040ca-142">Each line in the input is evaluated by the sample matches.</span></span> <span data-ttu-id="040ca-143">줄이 패턴에 지정 된 예제와 일치 하는 경우 값이 추출 되 고 출력 변수에 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="040ca-143">If the line matches the examples given in the pattern, values are extracted and passed to the output variable.</span></span>

<span data-ttu-id="040ca-144">샘플 데이터는 `$template` 두 가지 다른 전화 형식을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="040ca-144">The sample data, `$template`, provides two different phone formats:</span></span>

- `425-123-6789`
- `(206) 987-4321`

<span data-ttu-id="040ca-145">또한 샘플 데이터는 다음과 같은 두 가지 age 형식을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="040ca-145">The sample data also provides two different age formats:</span></span>

- `6`
- `12`

<span data-ttu-id="040ca-146">이는 `(206) 987 4321` 하이픈이 없으므로 해당 패턴과 일치 하는 샘플 데이터가 없으므로 전화와 같은 전화를 인식할 수 없음을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="040ca-146">This implies that phones like `(206) 987 4321` will not be recognized, because there's no sample data that matches that pattern because there are no hyphens.</span></span>

### <span data-ttu-id="040ca-147">예 5: 생성 된 속성에 데이터 형식 지정</span><span class="sxs-lookup"><span data-stu-id="040ca-147">Example 5: Specifying data types to the generated properties</span></span>

<span data-ttu-id="040ca-148">위의 예는 위의 예제 4와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="040ca-148">This is the same example as Example 4, above.</span></span>
<span data-ttu-id="040ca-149">차이점은 패턴 문자열에는 원하는 각 속성에 대 한 데이터 형식이 포함 된다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="040ca-149">The difference is that the pattern string includes a data type for each desired property.</span></span>

```powershell
$template = @'
{[string]Name*:Phoebe Cat}, {[string]phone:425-123-6789}, {[int]age:6}
{[string]Name*:Lucky Shot}, {[string]phone:(206) 987-4321}, {[int]age:12}
'@

$testText = @'
Phoebe Cat, 425-123-6789, 6
Lucky Shot, (206) 987-4321, 12
Elephant Wise, 425-888-7766, 87
Wild Shrimp, (111)  222-3333, 1
'@

$PersonalData = $testText | ConvertFrom-String -TemplateContent $template
Write-output ("Pet items found: " + ($PersonalData.Count))
$PersonalData
```

```Output
Pet items found: 4

Name          phone           age
----          -----           ---
Phoebe Cat    425-123-6789      6
Lucky Shot    (206) 987-4321   12
Elephant Wise 425-888-7766     87
Wild Shrimp   (111)  222-3333   1
```

```powershell
$PersonalData | Get-Member
```

```Output
   TypeName: System.Management.Automation.PSCustomObject

Name        MemberType   Definition
----        ----------   ----------
Equals      Method       bool Equals(System.Object obj)
GetHashCode Method       int GetHashCode()
GetType     Method       type GetType()
ToString    Method       string ToString()
age         NoteProperty int age=6
Name        NoteProperty string Name=Phoebe Cat
phone       NoteProperty string phone=425-123-6789
```

<span data-ttu-id="040ca-150">`Get-Member`Cmdlet은 **age** 속성이 정수인 것을 표시 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="040ca-150">The `Get-Member` cmdlet is used to show that the **age** property is an integer.</span></span>

## <span data-ttu-id="040ca-151">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="040ca-151">PARAMETERS</span></span>

### <span data-ttu-id="040ca-152">-구분 기호</span><span class="sxs-lookup"><span data-stu-id="040ca-152">-Delimiter</span></span>

<span data-ttu-id="040ca-153">요소 간의 경계를 식별 하는 정규식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="040ca-153">Specifies a regular expression that identifies the boundary between elements.</span></span>
<span data-ttu-id="040ca-154">분할에 의해 생성 되는 요소는 결과 개체의 속성이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="040ca-154">Elements that are created by the split become properties in the resulting object.</span></span>
<span data-ttu-id="040ca-155">구분 기호는 궁극적으로 형식의 **Split** 메서드 호출에 사용 됩니다 `[System.Text.RegularExpressions.RegularExpression]` .</span><span class="sxs-lookup"><span data-stu-id="040ca-155">The delimiter is ultimately used in a call to the **Split** method of the type `[System.Text.RegularExpressions.RegularExpression]`.</span></span>

```yaml
Type: System.String
Parameter Sets: ByDelimiter
Aliases: DEL

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="040ca-156">-IncludeExtent</span><span class="sxs-lookup"><span data-stu-id="040ca-156">-IncludeExtent</span></span>

<span data-ttu-id="040ca-157">이 cmdlet은 기본적으로 제거 되는 익스텐트 텍스트 속성을 포함 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="040ca-157">Indicates that this cmdlet includes an extent text property that is removed by default.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: TemplateParsing
Aliases: IE

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="040ca-158">-InputObject</span><span class="sxs-lookup"><span data-stu-id="040ca-158">-InputObject</span></span>

<span data-ttu-id="040ca-159">파이프라인에서 받은 문자열 또는 문자열 개체를 포함 하는 변수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="040ca-159">Specifies strings received from the pipeline, or a variable that contains a string object.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="040ca-160">-PropertyNames</span><span class="sxs-lookup"><span data-stu-id="040ca-160">-PropertyNames</span></span>

<span data-ttu-id="040ca-161">결과 개체에서 분할 된 값을 할당할 속성 이름의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="040ca-161">Specifies an array of property names to which to assign split values in the resulting object.</span></span>
<span data-ttu-id="040ca-162">분할 하거나 구문 분석 하는 모든 텍스트 줄은 속성 값을 나타내는 요소를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="040ca-162">Every line of text that you split or parse generates elements that represent property values.</span></span>
<span data-ttu-id="040ca-163">요소가 캡처 그룹의 결과일 때 해당 캡처 그룹의 이름이 인 경우 (예: `(?<name>)` 또는 `(?'name')` ) 해당 캡처 그룹의 이름이 속성에 할당 됩니다.</span><span class="sxs-lookup"><span data-stu-id="040ca-163">If the element is the result of a capture group, and that capture group is named (for example, `(?<name>)` or `(?'name')` ), then the name of that capture group is assigned to the property.</span></span>

<span data-ttu-id="040ca-164">**PropertyName** 배열의 요소를 제공 하는 경우 해당 이름이 아직 명명 되지 않은 속성에 할당 됩니다.</span><span class="sxs-lookup"><span data-stu-id="040ca-164">If you provide any elements in the **PropertyName** array, those names are assigned to properties that have not yet been named.</span></span>

<span data-ttu-id="040ca-165">필드 수보다 많은 속성 이름을 제공 하는 경우 PowerShell은 추가 속성 이름을 무시 합니다.</span><span class="sxs-lookup"><span data-stu-id="040ca-165">If you provide more property names than there are fields, PowerShell ignores the extra property names.</span></span> <span data-ttu-id="040ca-166">모든 필드의 이름을 지정 하는 데 충분 한 속성 이름을 지정 하지 않으면 PowerShell에서 이름이 지정 되지 않은 속성 ( **P1** , **P2** 등)에 숫자 속성 이름을 자동으로 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="040ca-166">If you do not specify enough property names to name all fields, PowerShell automatically assigns numerical property names to any properties that are not named: **P1** , **P2** , etc.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByDelimiter
Aliases: PN

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="040ca-167">-TemplateContent</span><span class="sxs-lookup"><span data-stu-id="040ca-167">-TemplateContent</span></span>

<span data-ttu-id="040ca-168">이 cmdlet이 문자열을 할당 하는 속성을 설명 하는 식 또는 변수로 저장 된 식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="040ca-168">Specifies an expression, or an expression saved as a variable, that describes the properties to which this cmdlet assigns strings.</span></span> <span data-ttu-id="040ca-169">템플릿 필드 사양의 구문은 `{[optional-typecast]<name>:<example-value>}` 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="040ca-169">The syntax of a template field specification is the following: `{[optional-typecast]<name>:<example-value>}`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: TemplateParsing
Aliases: TC

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="040ca-170">-TemplateFile</span><span class="sxs-lookup"><span data-stu-id="040ca-170">-TemplateFile</span></span>

<span data-ttu-id="040ca-171">문자열의 원하는 구문 분석을 위한 템플릿을 포함 하는 파일을 배열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="040ca-171">Specifies a file, as an array, that contains a template for the desired parsing of the string.</span></span>
<span data-ttu-id="040ca-172">템플릿 파일에서 속성과 해당 값은 아래와 같이 대괄호로 묶여 있습니다.</span><span class="sxs-lookup"><span data-stu-id="040ca-172">In the template file, properties and their values are enclosed in brackets, as shown below.</span></span>
<span data-ttu-id="040ca-173">속성 (예: **Name** 속성 및 연결 된 다른 속성)이 여러 번 표시 되는 경우 별표 ()를 추가 하 여 `*` 여러 레코드가 생성 되는 것을 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="040ca-173">If a property, such as the **Name** property and its associated other properties, appears multiple times, you can add an asterisk (`*`) to indicate that this results in multiple records.</span></span> <span data-ttu-id="040ca-174">이렇게 하면 여러 속성을 단일 레코드로 추출 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="040ca-174">This avoids extracting multiple properties into a single record.</span></span>

```
{Name*:David Chew}
{City:Redmond}, {State:WA}
{Name*:Evan Narvaez}    {Name*:Antonio Moreno}
{City:Issaquah}, {State:WA}
```

```yaml
Type: System.String[]
Parameter Sets: TemplateParsing
Aliases: TF

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="040ca-175">-UpdateTemplate</span><span class="sxs-lookup"><span data-stu-id="040ca-175">-UpdateTemplate</span></span>

<span data-ttu-id="040ca-176">이 cmdlet이 학습 알고리즘의 결과를 템플릿 파일의 설명에 저장 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="040ca-176">Indicates that this cmdlet saves the results of a learning algorithm into a comment in the template file.</span></span>
<span data-ttu-id="040ca-177">이렇게 하면 알고리즘 학습 프로세스를 더 빠르게 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="040ca-177">This makes the algorithm learning process faster.</span></span>
<span data-ttu-id="040ca-178">이 매개 변수를 사용 하려면 템플릿 **파일 매개 변수를 사용** 하 여 템플릿 파일도 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="040ca-178">To use this parameter, you must also specify a template file with the **TemplateFile** parameter.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: TemplateParsing
Aliases: UT

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="040ca-179">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="040ca-179">CommonParameters</span></span>

<span data-ttu-id="040ca-180">이 cmdlet은,,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` 및 `-WarningVariable` 등의 일반 매개 변수를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="040ca-180">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="040ca-181">자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="040ca-181">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="040ca-182">입력</span><span class="sxs-lookup"><span data-stu-id="040ca-182">INPUTS</span></span>

### <span data-ttu-id="040ca-183">System.String</span><span class="sxs-lookup"><span data-stu-id="040ca-183">System.String</span></span>

## <span data-ttu-id="040ca-184">출력</span><span class="sxs-lookup"><span data-stu-id="040ca-184">OUTPUTS</span></span>

## <span data-ttu-id="040ca-185">참고</span><span class="sxs-lookup"><span data-stu-id="040ca-185">NOTES</span></span>

## <span data-ttu-id="040ca-186">관련 링크</span><span class="sxs-lookup"><span data-stu-id="040ca-186">RELATED LINKS</span></span>

[<span data-ttu-id="040ca-187">Convertfrom-csv-문자열: 예제 기반 텍스트 구문 분석</span><span class="sxs-lookup"><span data-stu-id="040ca-187">ConvertFrom-String: Example-based text parsing</span></span>](https://devblogs.microsoft.com/powershell/convertfrom-string-example-based-text-parsing/)

[<span data-ttu-id="040ca-188">ConvertFrom-StringData</span><span class="sxs-lookup"><span data-stu-id="040ca-188">ConvertFrom-StringData</span></span>](ConvertFrom-StringData.md)

[<span data-ttu-id="040ca-189">ConvertFrom-Csv</span><span class="sxs-lookup"><span data-stu-id="040ca-189">ConvertFrom-Csv</span></span>](ConvertFrom-Csv.md)

[<span data-ttu-id="040ca-190">ConvertTo-Xml</span><span class="sxs-lookup"><span data-stu-id="040ca-190">ConvertTo-Xml</span></span>](ConvertTo-Xml.md)
