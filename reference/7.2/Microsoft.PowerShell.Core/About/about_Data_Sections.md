---
description: 스크립트 논리에서 텍스트 문자열과 기타 읽기 전용 데이터를 격리 하는 데이터 섹션에 대해 설명 합니다.
Locale: en-US
ms.date: 04/23/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_data_sections?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Data_Sections
ms.openlocfilehash: 1f2a0bae0721bc9adf5b3ba92d5be32d21306a46
ms.sourcegitcommit: 04faa7dc1122bce839295d4891bd8b2f0ecb06ef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/05/2021
ms.locfileid: "99600162"
---
# <a name="about-data-sections"></a><span data-ttu-id="f4498-103">데이터 섹션 정보</span><span class="sxs-lookup"><span data-stu-id="f4498-103">About Data Sections</span></span>

## <a name="short-description"></a><span data-ttu-id="f4498-104">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="f4498-104">Short Description</span></span>
<span data-ttu-id="f4498-105">스크립트 논리에서 텍스트 문자열과 기타 읽기 전용 데이터를 격리 하는 데이터 섹션에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4498-105">Explains Data sections, which isolate text strings and other read-only data from script logic.</span></span>

## <a name="long-description"></a><span data-ttu-id="f4498-106">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="f4498-106">Long Description</span></span>

<span data-ttu-id="f4498-107">PowerShell 용으로 설계 된 스크립트에는 데이터만 포함 된 하나 이상의 데이터 섹션이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4498-107">Scripts that are designed for PowerShell can have one or more Data sections that contain only data.</span></span> <span data-ttu-id="f4498-108">모든 스크립트, 함수 또는 고급 함수에 하나 이상의 데이터 섹션을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4498-108">You can include one or more Data sections in any script, function, or advanced function.</span></span> <span data-ttu-id="f4498-109">데이터 섹션의 내용은 PowerShell 스크립트 언어의 지정 된 하위 집합으로 제한 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4498-109">The content of the Data section is restricted to a specified subset of the PowerShell scripting language.</span></span>

<span data-ttu-id="f4498-110">코드 논리에서 데이터를 분리 하면 논리와 데이터를 더 쉽게 식별 하 고 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4498-110">Separating data from code logic makes it easier to identify and manage both logic and data.</span></span> <span data-ttu-id="f4498-111">오류 메시지 및 도움말 문자열과 같은 텍스트에 대 한 별도의 문자열 리소스 파일을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4498-111">It lets you have separate string resource files for text, such as error messages and Help strings.</span></span> <span data-ttu-id="f4498-112">또한 보안 및 유효성 검사 테스트를 용이 하 게 하는 코드 논리를 격리 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4498-112">It also isolates the code logic, which facilitates security and validation tests.</span></span>

<span data-ttu-id="f4498-113">PowerShell에서 데이터 섹션은 스크립트 국제화를 지 원하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4498-113">In PowerShell, the Data section is used to support script internationalization.</span></span>
<span data-ttu-id="f4498-114">데이터 섹션을 사용 하 여 여러 UI (사용자 인터페이스) 언어로 변환 되는 문자열을 보다 쉽게 격리 하 고 찾고 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4498-114">You can use Data sections to make it easier to isolate, locate, and process strings that will be translated into many user interface (UI) languages.</span></span>

<span data-ttu-id="f4498-115">데이터 섹션은 PowerShell 2.0 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="f4498-115">The Data section is a PowerShell 2.0 feature.</span></span> <span data-ttu-id="f4498-116">데이터 섹션이 포함 된 스크립트는 수정 없이 PowerShell 1.0에서 실행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f4498-116">Scripts with Data sections will not run in PowerShell 1.0 without revision.</span></span>

### <a name="syntax"></a><span data-ttu-id="f4498-117">Syntax</span><span class="sxs-lookup"><span data-stu-id="f4498-117">Syntax</span></span>

<span data-ttu-id="f4498-118">데이터 섹션의 구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f4498-118">The syntax for a Data section is as follows:</span></span>

```
DATA [<variable-name>] [-supportedCommand <cmdlet-name>] {
    <Permitted content>
}
```

<span data-ttu-id="f4498-119">Data 키워드가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4498-119">The Data keyword is required.</span></span> <span data-ttu-id="f4498-120">대/소문자를 구분하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f4498-120">It is not case-sensitive.</span></span> <span data-ttu-id="f4498-121">허용 되는 콘텐츠는 다음 요소로 제한 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4498-121">The permitted content is limited to the following elements:</span></span>

- <span data-ttu-id="f4498-122">모든 PowerShell 연산자 (제외) `-match`</span><span class="sxs-lookup"><span data-stu-id="f4498-122">All PowerShell operators, except `-match`</span></span>
- <span data-ttu-id="f4498-123">`If`, `Else` 및 `ElseIf` 문</span><span class="sxs-lookup"><span data-stu-id="f4498-123">`If`, `Else`, and `ElseIf` statements</span></span>
- <span data-ttu-id="f4498-124">자동 변수는,, `$PsCulture` `$PsUICulture` `$True` , `$False` 및입니다. `$Null`</span><span class="sxs-lookup"><span data-stu-id="f4498-124">The following automatic variables: `$PsCulture`, `$PsUICulture`, `$True`, `$False`, and `$Null`</span></span>
- <span data-ttu-id="f4498-125">설명</span><span class="sxs-lookup"><span data-stu-id="f4498-125">Comments</span></span>
- <span data-ttu-id="f4498-126">파이프라인</span><span class="sxs-lookup"><span data-stu-id="f4498-126">Pipelines</span></span>
- <span data-ttu-id="f4498-127">세미콜론 ()으로 구분 된 문 `;`</span><span class="sxs-lookup"><span data-stu-id="f4498-127">Statements separated by semicolons (`;`)</span></span>
- <span data-ttu-id="f4498-128">다음과 같은 리터럴입니다.</span><span class="sxs-lookup"><span data-stu-id="f4498-128">Literals, such as the following:</span></span>

  ```powershell
  a
  1
  1,2,3
  "PowerShell 2.0"
  @( "red", "green", "blue" )
  @{ a = 0x1; b = "great"; c ="script" }
  [XML] @'
  <p> Hello, World </p>
  '@
  ```

- <span data-ttu-id="f4498-129">데이터 섹션에서 허용 되는 cmdlet입니다.</span><span class="sxs-lookup"><span data-stu-id="f4498-129">Cmdlets that are permitted in a Data section.</span></span> <span data-ttu-id="f4498-130">기본적으로 `ConvertFrom-StringData` cmdlet만 허용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4498-130">By default, only the `ConvertFrom-StringData` cmdlet is permitted.</span></span>
- <span data-ttu-id="f4498-131">매개 변수를 사용 하 여 데이터 섹션에서 허용 하는 cmdlet입니다 `-SupportedCommand` .</span><span class="sxs-lookup"><span data-stu-id="f4498-131">Cmdlets that you permit in a Data section by using the `-SupportedCommand` parameter.</span></span>

<span data-ttu-id="f4498-132">데이터 섹션에서 cmdlet을 사용 하는 경우 `ConvertFrom-StringData` 키-값 쌍을 작은따옴표 또는 큰따옴표로 묶은 문자열이 나 작은따옴표로 묶은 작은따옴표 또는 큰따옴표로 묶을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4498-132">When you use the `ConvertFrom-StringData` cmdlet in a Data section, you can enclose the key-value pairs in single-quoted or double-quoted strings or in single-quoted or double-quoted here-strings.</span></span> <span data-ttu-id="f4498-133">그러나 변수와 부분식을 포함 하는 문자열은 변수가 확장 되지 않고 하위 식이 실행 되지 않도록 작은따옴표로 묶은 문자열 또는 작은따옴표로 묶은 작은따옴표로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4498-133">However, strings that contain variables and subexpressions must be enclosed in single-quoted strings or in single-quoted here-strings so that the variables are not expanded and the subexpressions are not executable.</span></span>

### <a name="-supportedcommand"></a><span data-ttu-id="f4498-134">-SupportedCommand</span><span class="sxs-lookup"><span data-stu-id="f4498-134">-SupportedCommand</span></span>

<span data-ttu-id="f4498-135">`-SupportedCommand`매개 변수를 사용 하 여 cmdlet 또는 함수에서 데이터만 생성 하도록 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4498-135">The `-SupportedCommand` parameter allows you to indicate that a cmdlet or function generates only data.</span></span> <span data-ttu-id="f4498-136">사용자가 작성 하거나 테스트 한 데이터 섹션에 cmdlet 및 함수를 포함할 수 있도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f4498-136">It is designed to allow users to include cmdlets and functions in a data section that they have written or tested.</span></span>

<span data-ttu-id="f4498-137">값은 `-SupportedCommand` 하나 이상의 cmdlet 또는 함수 이름의 쉼표로 구분 된 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="f4498-137">The value of `-SupportedCommand` is a comma-separated list of one or more cmdlet or function names.</span></span>

<span data-ttu-id="f4498-138">예를 들어 다음 데이터 섹션에는 `Format-Xml` XML 파일의 데이터 형식을 지정 하는 사용자 작성 cmdlet이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4498-138">For example, the following data section includes a user-written cmdlet, `Format-Xml`, that formats data in an XML file:</span></span>

```powershell
DATA -supportedCommand Format-Xml
{
    Format-Xml -Strings string1, string2, string3
}
```

### <a name="using-a-data-section"></a><span data-ttu-id="f4498-139">데이터 섹션 사용</span><span class="sxs-lookup"><span data-stu-id="f4498-139">Using a Data Section</span></span>

<span data-ttu-id="f4498-140">데이터 섹션의 내용을 사용 하려면 변수를 변수에 할당 하 고 변수 표기법을 사용 하 여 콘텐츠에 액세스 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4498-140">To use the content of a Data section, assign it to a variable and use variable notation to access the content.</span></span>

<span data-ttu-id="f4498-141">예를 들어 다음 데이터 섹션에는 `ConvertFrom-StringData` 문자열을 해시 테이블로 변환 하는 명령이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4498-141">For example, the following data section contains a `ConvertFrom-StringData` command that converts the here-string into a hash table.</span></span> <span data-ttu-id="f4498-142">해시 테이블은 변수에 할당 됩니다 `$TextMsgs` .</span><span class="sxs-lookup"><span data-stu-id="f4498-142">The hash table is assigned to the `$TextMsgs` variable.</span></span>

<span data-ttu-id="f4498-143">`$TextMsgs`변수가 데이터 섹션의 일부가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="f4498-143">The `$TextMsgs` variable is not part of the data section.</span></span>

```powershell
$TextMsgs = DATA {
    ConvertFrom-StringData -StringData @'
Text001 = Windows 7
Text002 = Windows Server 2008 R2
'@
}
```

<span data-ttu-id="f4498-144">에서 해시 테이블의 키 및 값에 액세스 하려면 `$TextMsgs` 다음 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4498-144">To access the keys and values in hash table in `$TextMsgs`, use the following commands.</span></span>

```powershell
$TextMsgs.Text001
$TextMsgs.Text002
```

<span data-ttu-id="f4498-145">또는 변수 이름을 데이터 섹션의 정의에 배치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4498-145">Alternately, you can put the variable name in the definition of the Data section.</span></span> <span data-ttu-id="f4498-146">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="f4498-146">For example:</span></span>

```powershell
DATA TextMsgs {
    ConvertFrom-StringData -StringData @'
Text001 = Windows 7
Text002 = Windows Server 2008 R2
'@
}

$TextMsgs
```

<span data-ttu-id="f4498-147">결과는 이전 예제와 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4498-147">The result is the same as the previous example.</span></span>

```Output
Name                           Value
----                           -----
Text001                        Windows 7
Text002                        Windows Server 2008 R2
```

### <a name="examples"></a><span data-ttu-id="f4498-148">예</span><span class="sxs-lookup"><span data-stu-id="f4498-148">Examples</span></span>

<span data-ttu-id="f4498-149">단순 데이터 문자열.</span><span class="sxs-lookup"><span data-stu-id="f4498-149">Simple data strings.</span></span>

```powershell
DATA {
    "Thank you for using my PowerShell Organize.pst script."
    "It is provided free of charge to the community."
    "I appreciate your comments and feedback."
}
```

<span data-ttu-id="f4498-150">허용 된 변수를 포함 하는 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="f4498-150">Strings that include permitted variables.</span></span>

```powershell
DATA {
    if ($null) {
        "To get help for this cmdlet, type get-help new-dictionary."
    }
}
```

<span data-ttu-id="f4498-151">Cmdlet을 사용 하는 작은따옴표로 묶은 문자열입니다 `ConvertFrom-StringData` .</span><span class="sxs-lookup"><span data-stu-id="f4498-151">A single-quoted here-string that uses the `ConvertFrom-StringData` cmdlet:</span></span>

```powershell
DATA {
    ConvertFrom-StringData -stringdata @'
Text001 = Windows 7
Text002 = Windows Server 2008 R2
'@
}
```

<span data-ttu-id="f4498-152">Cmdlet을 사용 하는 큰따옴표로 묶인 문자열입니다 `ConvertFrom-StringData` .</span><span class="sxs-lookup"><span data-stu-id="f4498-152">A double-quoted here-string that uses the `ConvertFrom-StringData` cmdlet:</span></span>

```powershell
DATA  {
    ConvertFrom-StringData -stringdata @"
Msg1 = To start, press any key.
Msg2 = To exit, type "quit".
"@
}
```

<span data-ttu-id="f4498-153">데이터를 생성 하는 사용자 작성 cmdlet을 포함 하는 데이터 섹션:</span><span class="sxs-lookup"><span data-stu-id="f4498-153">A data section that includes a user-written cmdlet that generates data:</span></span>

```powershell
DATA -supportedCommand Format-XML {
    Format-Xml -strings string1, string2, string3
}
```

## <a name="see-also"></a><span data-ttu-id="f4498-154">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f4498-154">See Also</span></span>

[<span data-ttu-id="f4498-155">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="f4498-155">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)

[<span data-ttu-id="f4498-156">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="f4498-156">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="f4498-157">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="f4498-157">about_Hash_Tables</span></span>](about_Hash_Tables.md)

[<span data-ttu-id="f4498-158">about_If</span><span class="sxs-lookup"><span data-stu-id="f4498-158">about_If</span></span>](about_If.md)

[<span data-ttu-id="f4498-159">about_Operators</span><span class="sxs-lookup"><span data-stu-id="f4498-159">about_Operators</span></span>](about_Operators.md)

[<span data-ttu-id="f4498-160">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="f4498-160">about_Quoting_Rules</span></span>](about_Quoting_Rules.md)

[<span data-ttu-id="f4498-161">about_Script_Internationalization</span><span class="sxs-lookup"><span data-stu-id="f4498-161">about_Script_Internationalization</span></span>](about_Script_Internationalization.md)

[<span data-ttu-id="f4498-162">ConvertFrom-StringData</span><span class="sxs-lookup"><span data-stu-id="f4498-162">ConvertFrom-StringData</span></span>](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData)

[<span data-ttu-id="f4498-163">Import-LocalizedData</span><span class="sxs-lookup"><span data-stu-id="f4498-163">Import-LocalizedData</span></span>](xref:Microsoft.PowerShell.Utility.Import-LocalizedData)

