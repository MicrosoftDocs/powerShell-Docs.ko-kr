---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Module Name: Microsoft.PowerShell.Utility
ms.date: 12/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/join-string?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Join-String
ms.openlocfilehash: bae6b8558a3e12bf161d8f0ec12037841a20cc04
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93211194"
---
# <span data-ttu-id="1cf19-102">Join-String</span><span class="sxs-lookup"><span data-stu-id="1cf19-102">Join-String</span></span>

## <span data-ttu-id="1cf19-103">개요</span><span class="sxs-lookup"><span data-stu-id="1cf19-103">SYNOPSIS</span></span>
<span data-ttu-id="1cf19-104">파이프라인의 개체를 단일 문자열로 결합 합니다.</span><span class="sxs-lookup"><span data-stu-id="1cf19-104">Combines objects from the pipeline into a single string.</span></span>

## <span data-ttu-id="1cf19-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="1cf19-105">SYNTAX</span></span>

### <span data-ttu-id="1cf19-106">Default (기본값)</span><span class="sxs-lookup"><span data-stu-id="1cf19-106">Default (Default)</span></span>

```
Join-String [[-Property] <PSPropertyExpression>] [[-Separator] <String>] [-OutputPrefix <String>]
 [-OutputSuffix <String>] [-UseCulture] [-InputObject <PSObject[]>] [<CommonParameters>]
```

### <span data-ttu-id="1cf19-107">SingleQuote</span><span class="sxs-lookup"><span data-stu-id="1cf19-107">SingleQuote</span></span>

```
Join-String [[-Property] <PSPropertyExpression>] [[-Separator] <String>] [-OutputPrefix <String>]
 [-OutputSuffix <String>] [-SingleQuote] [-UseCulture] [-InputObject <PSObject[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="1cf19-108">DoubleQuote</span><span class="sxs-lookup"><span data-stu-id="1cf19-108">DoubleQuote</span></span>

```
Join-String [[-Property] <PSPropertyExpression>] [[-Separator] <String>] [-OutputPrefix <String>]
 [-OutputSuffix <String>] [-DoubleQuote] [-UseCulture] [-InputObject <PSObject[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="1cf19-109">서식</span><span class="sxs-lookup"><span data-stu-id="1cf19-109">Format</span></span>

```
Join-String [[-Property] <PSPropertyExpression>] [[-Separator] <String>] [-OutputPrefix <String>]
 [-OutputSuffix <String>] [-FormatString <String>] [-UseCulture] [-InputObject <PSObject[]>]
 [<CommonParameters>]
```

## <span data-ttu-id="1cf19-110">설명</span><span class="sxs-lookup"><span data-stu-id="1cf19-110">DESCRIPTION</span></span>

<span data-ttu-id="1cf19-111">`Join-String`Cmdlet은 파이프라인 개체의 텍스트를 단일 문자열로 결합 하거나 결합 합니다.</span><span class="sxs-lookup"><span data-stu-id="1cf19-111">The `Join-String` cmdlet joins, or combines, text from pipeline objects into a single string.</span></span>

<span data-ttu-id="1cf19-112">매개 변수를 지정 하지 않으면 파이프라인 개체가 문자열로 변환 되 고 기본 구분 기호와 조인 됩니다 `$OFS` .</span><span class="sxs-lookup"><span data-stu-id="1cf19-112">If no parameters are specified, the pipeline objects are converted to a string and joined with the default separator `$OFS`.</span></span>

<span data-ttu-id="1cf19-113">속성 이름을 지정 하 여 속성의 값을 문자열로 변환 하 고 문자열에 조인 합니다.</span><span class="sxs-lookup"><span data-stu-id="1cf19-113">By specifying a property name, the property's value is converted to a string and joined into a string.</span></span>

<span data-ttu-id="1cf19-114">속성 이름 대신 스크립트 블록을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1cf19-114">Instead of a property name, a script block can be used.</span></span> <span data-ttu-id="1cf19-115">결과를 형성 하기 위해 스크립트 블록의 결과가 조인 되기 전에 문자열로 변환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1cf19-115">The script block's result is converted to a string before it's joined to form the result.</span></span> <span data-ttu-id="1cf19-116">개체의 속성 텍스트 또는 문자열로 변환 된 개체의 결과를 결합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1cf19-116">It can either combine the text of an object's property or the result of the object that was converted to a string.</span></span>

<span data-ttu-id="1cf19-117">이 cmdlet은 PowerShell 6.2에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1cf19-117">This cmdlet was introduced in PowerShell 6.2.</span></span>

## <span data-ttu-id="1cf19-118">예제</span><span class="sxs-lookup"><span data-stu-id="1cf19-118">EXAMPLES</span></span>

### <span data-ttu-id="1cf19-119">예 1: 디렉터리 이름 조인</span><span class="sxs-lookup"><span data-stu-id="1cf19-119">Example 1: Join directory names</span></span>

<!-- markdownlint-disable MD038 -->
<span data-ttu-id="1cf19-120">이 예에서는 디렉터리 이름을 조인 하 고, 출력을 큰따옴표로 래핑하고, 디렉터리 이름을 쉼표와 공백 ()으로 구분 `, ` 합니다.</span><span class="sxs-lookup"><span data-stu-id="1cf19-120">This example joins directory names, wraps the output in double-quotes, and separates the directory names with a comma and space (`, `).</span></span> <span data-ttu-id="1cf19-121">출력은 문자열 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="1cf19-121">The output is a string object.</span></span>

```powershell
Get-ChildItem -Directory C:\ | Join-String -Property Name -DoubleQuote -Separator ', '
```

```Output
"PerfLogs", "Program Files", "Program Files (x86)", "Users", "Windows"
```

<span data-ttu-id="1cf19-122">`Get-ChildItem`**directory** 매개 변수를 사용 하 여 드라이브에 대 한 모든 디렉터리 이름을 가져옵니다 `C:\` .</span><span class="sxs-lookup"><span data-stu-id="1cf19-122">`Get-ChildItem` uses the **Directory** parameter to get all the directory names for the `C:\` drive.</span></span>
<span data-ttu-id="1cf19-123">개체는 파이프라인에서로 전송 됩니다 `Join-String` .</span><span class="sxs-lookup"><span data-stu-id="1cf19-123">The objects are sent down the pipeline to `Join-String`.</span></span> <span data-ttu-id="1cf19-124">**Property** 매개 변수는 디렉터리 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1cf19-124">The **Property** parameter specifies the directory names.</span></span> <span data-ttu-id="1cf19-125">**DoubleQuote** 매개 변수는 따옴표를 사용 하 여 디렉터리 이름을 래핑합니다.</span><span class="sxs-lookup"><span data-stu-id="1cf19-125">The **DoubleQuote** parameter wraps the directory names with double-quote marks.</span></span>
<span data-ttu-id="1cf19-126">**구분 기호** 매개 변수는 쉼표와 공백 ()을 사용 하 여 `, ` 디렉터리 이름을 구분 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1cf19-126">The **Separator** parameter specifies to use a comma and space (`, `) to separate the directory names.</span></span>

<span data-ttu-id="1cf19-127">`Get-ChildItem`개체는 **system.io.directoryinfo** 이며 `Join-String` 개체를 **system.string** 로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="1cf19-127">The `Get-ChildItem` objects are **System.IO.DirectoryInfo** and `Join-String` converts the objects to **System.String** .</span></span>

### <span data-ttu-id="1cf19-128">예제 2: 속성 하위 문자열을 사용 하 여 디렉터리 이름에 조인</span><span class="sxs-lookup"><span data-stu-id="1cf19-128">Example 2: Use a property substring to join directory names</span></span>

<span data-ttu-id="1cf19-129">이 예제에서는 부분 문자열 메서드를 사용 하 여 디렉터리 이름의 처음 4 개 문자를 가져오고, 출력을 작은따옴표로 래핑하고, 디렉터리 이름을 세미콜론 ()으로 구분 합니다 `;` .</span><span class="sxs-lookup"><span data-stu-id="1cf19-129">This example uses a substring method to get the first four letters of directory names, wraps the output in single-quotes, and separates the directory names with a semicolon (`;`).</span></span>

```powershell
Get-ChildItem -Directory C:\ | Join-String -Property {$_.Name.SubString(0,4)} -SingleQuote -Separator ';'
```

```Output
'Perf';'Prog';'Prog';'User';'Wind'
```

<span data-ttu-id="1cf19-130">`Get-ChildItem`**directory** 매개 변수를 사용 하 여 드라이브에 대 한 모든 디렉터리 이름을 가져옵니다 `C:\` .</span><span class="sxs-lookup"><span data-stu-id="1cf19-130">`Get-ChildItem` uses the **Directory** parameter to get all the directory names for the `C:\` drive.</span></span>
<span data-ttu-id="1cf19-131">개체는 파이프라인에서로 전송 됩니다 `Join-String` .</span><span class="sxs-lookup"><span data-stu-id="1cf19-131">The objects are sent down the pipeline to `Join-String`.</span></span>

<span data-ttu-id="1cf19-132">**속성** 매개 변수 스크립트 블록은 자동 변수 ( `$_` )를 사용 하 여 각 개체의 **Name** 속성 하위 문자열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1cf19-132">The **Property** parameter script block uses automatic variable (`$_`) to specify each object's **Name** property substring.</span></span> <span data-ttu-id="1cf19-133">부분 문자열은 각 디렉터리 이름의 처음 4 개 문자를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1cf19-133">The substring gets the first four letters of each directory name.</span></span> <span data-ttu-id="1cf19-134">부분 문자열은 문자 시작 및 끝 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1cf19-134">The substring specifies the character start and end positions.</span></span> <span data-ttu-id="1cf19-135">**Singlequote** 매개 변수는 작은따옴표를 사용 하 여 디렉터리 이름을 래핑합니다.</span><span class="sxs-lookup"><span data-stu-id="1cf19-135">The **SingleQuote** parameter wraps the directory names with single-quote marks.</span></span> <span data-ttu-id="1cf19-136">**구분 기호** 매개 변수는 세미콜론 ()을 사용 하 여 `;` 디렉터리 이름을 구분 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1cf19-136">The **Separator** parameter specifies to use a semicolon (`;`) to separate the directory names.</span></span>

<span data-ttu-id="1cf19-137">자동 변수 및 부분 문자열에 대 한 자세한 내용은 [about_Automatic_Variables](../microsoft.powershell.core/about/about_automatic_variables.md) 및 하위 [문자열](/dotnet/api/system.string.substring)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1cf19-137">For more information about automatic variables and substrings, see [about_Automatic_Variables](../microsoft.powershell.core/about/about_automatic_variables.md) and [Substring](/dotnet/api/system.string.substring).</span></span>

### <span data-ttu-id="1cf19-138">예제 3: 별도의 줄에 조인 출력 표시</span><span class="sxs-lookup"><span data-stu-id="1cf19-138">Example 3: Display join output on a separate line</span></span>

<span data-ttu-id="1cf19-139">이 예제에서는 서비스 이름을 각 서비스와 별도의 줄에 조인 하 고 탭으로 들여씁니다.</span><span class="sxs-lookup"><span data-stu-id="1cf19-139">This example joins service names with each service on a separate line and indented by a tab.</span></span>

```powershell
Get-Service -Name se* | Join-String -Property Name -Separator "`r`n`t" -OutputPrefix "Services:`n`t"
```

```Output
Services:
    seclogon
    SecurityHealthService
    SEMgrSvc
    SENS
    Sense
    SensorDataService
    SensorService
    SensrSvc
    SessionEnv
```

<span data-ttu-id="1cf19-140">`Get-Service` 에서는 **Name** 매개 변수를 사용 하 여로 시작 하는 서비스를 지정 합니다 `se*` .</span><span class="sxs-lookup"><span data-stu-id="1cf19-140">`Get-Service` uses the **Name** parameter with to specify services that begin with `se*`.</span></span> <span data-ttu-id="1cf19-141">별표 ( `*` )는 모든 문자에 대 한 와일드 카드입니다.</span><span class="sxs-lookup"><span data-stu-id="1cf19-141">The asterisk (`*`) is a wildcard for any character.</span></span>

<span data-ttu-id="1cf19-142">개체는 `Join-String` **속성** 매개 변수를 사용 하 여 서비스 이름을 지정 하는 파이프라인에서로 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1cf19-142">The objects are sent down the pipeline to `Join-String` that uses the **Property** parameter to specify the service names.</span></span> <span data-ttu-id="1cf19-143">**Separator** 매개 변수는 캐리지 리턴 ( `` `r `` ), 줄 바꿈 ( `` `n `` ) 및 탭 ()을 나타내는 세 가지 특수 문자를 지정 합니다 `` `t `` .</span><span class="sxs-lookup"><span data-stu-id="1cf19-143">The **Separator** parameter specifies three special characters that represent a carriage return (`` `r ``), newline (`` `n ``), and tab (`` `t ``).</span></span> <span data-ttu-id="1cf19-144">**Outputprefix** 는 첫 번째 출력 줄 앞에 새 줄과 탭을 사용 하 여 레이블 **서비스** 를 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="1cf19-144">The **OutputPrefix** inserts a label **Services:** with a new line and tab before the first line of output.</span></span>

<span data-ttu-id="1cf19-145">특수 문자에 대 한 자세한 내용은 [about_Special_Characters](..//microsoft.powershell.core/about/about_special_characters.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1cf19-145">For more information about special characters, see [about_Special_Characters](..//microsoft.powershell.core/about/about_special_characters.md).</span></span>

### <span data-ttu-id="1cf19-146">예제 4: 개체에서 클래스 정의 만들기</span><span class="sxs-lookup"><span data-stu-id="1cf19-146">Example 4: Create a class definition from an object</span></span>

<span data-ttu-id="1cf19-147">이 예에서는 기존 개체를 템플릿으로 사용 하 여 PowerShell 클래스 정의를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="1cf19-147">This example generates a PowerShell class definition using an existing object as a template.</span></span>

<span data-ttu-id="1cf19-148">이 코드 샘플에서는 스 플랫을 사용 하 여 줄 길이를 줄이고 가독성을 향상 시킵니다.</span><span class="sxs-lookup"><span data-stu-id="1cf19-148">This code sample uses splatting to reduce the line length and improve readability.</span></span> <span data-ttu-id="1cf19-149">자세한 내용은 [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1cf19-149">For more information, see [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md).</span></span>

```powershell
$obj = [pscustomobject] @{Name = "Joe"; Age = 42}
$parms = @{
  Property = "Name"
  FormatString = '  ${0}'
  OutputPrefix = "class {`n"
  OutputSuffix = "`n}`n"
  Separator = "`n"
}
$obj.PSObject.Properties | Join-String @parms
```

```Output
class {
  $Name
  $Age
}
```

## <span data-ttu-id="1cf19-150">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1cf19-150">PARAMETERS</span></span>

### <span data-ttu-id="1cf19-151">-DoubleQuote</span><span class="sxs-lookup"><span data-stu-id="1cf19-151">-DoubleQuote</span></span>

<span data-ttu-id="1cf19-152">각 파이프라인 개체의 문자열 값을 큰따옴표로 래핑합니다.</span><span class="sxs-lookup"><span data-stu-id="1cf19-152">Wraps the string value of each pipeline object in double-quotes.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DoubleQuote
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1cf19-153">-FormatString</span><span class="sxs-lookup"><span data-stu-id="1cf19-153">-FormatString</span></span>

<span data-ttu-id="1cf19-154">각 항목의 형식을 지정 하는 방법을 지정 하는 서식 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="1cf19-154">A format string that specifies how each item should be formatted.</span></span>

```yaml
Type: System.String
Parameter Sets: Format
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1cf19-155">-InputObject</span><span class="sxs-lookup"><span data-stu-id="1cf19-155">-InputObject</span></span>

<span data-ttu-id="1cf19-156">조인할 텍스트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1cf19-156">Specifies the text to be joined.</span></span> <span data-ttu-id="1cf19-157">텍스트를 포함 하는 변수를 입력 하거나 문자열에 조인할 개체를 가져오는 명령 또는 식을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="1cf19-157">Enter a variable that contains the text, or type a command or expression that gets the objects to join into strings.</span></span>

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="1cf19-158">-OutputPrefix</span><span class="sxs-lookup"><span data-stu-id="1cf19-158">-OutputPrefix</span></span>

<span data-ttu-id="1cf19-159">출력 문자열 앞에 삽입 되는 텍스트입니다.</span><span class="sxs-lookup"><span data-stu-id="1cf19-159">Text that's inserted before the output string.</span></span> <span data-ttu-id="1cf19-160">문자열에는 캐리지 리턴 ( `` `r `` ), 줄 바꿈 ( `` `n `` ) 및 tab ()과 같은 특수 문자가 포함 될 수 있습니다 `` `t `` .</span><span class="sxs-lookup"><span data-stu-id="1cf19-160">The string can contain special characters such as carriage return (`` `r ``), newline (`` `n ``), and tab (`` `t ``).</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: op

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1cf19-161">-OutputSuffix</span><span class="sxs-lookup"><span data-stu-id="1cf19-161">-OutputSuffix</span></span>

<span data-ttu-id="1cf19-162">출력 문자열에 추가 되는 텍스트입니다.</span><span class="sxs-lookup"><span data-stu-id="1cf19-162">Text that's appended to the output string.</span></span> <span data-ttu-id="1cf19-163">문자열에는 캐리지 리턴 ( `` `r `` ), 줄 바꿈 ( `` `n `` ) 및 tab ()과 같은 특수 문자가 포함 될 수 있습니다 `` `t `` .</span><span class="sxs-lookup"><span data-stu-id="1cf19-163">The string can contain special characters such as carriage return (`` `r ``), newline (`` `n ``), and tab (`` `t ``).</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: os

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1cf19-164">-속성</span><span class="sxs-lookup"><span data-stu-id="1cf19-164">-Property</span></span>

<span data-ttu-id="1cf19-165">파이프라인 개체를 텍스트로 프로젝션 하는 속성 또는 속성의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="1cf19-165">The name of a property, or a property expression, that will project the pipeline object to text.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.PSPropertyExpression
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1cf19-166">-구분 기호</span><span class="sxs-lookup"><span data-stu-id="1cf19-166">-Separator</span></span>

<span data-ttu-id="1cf19-167">각 파이프라인 개체의 텍스트 사이에 삽입 되는 쉼표나 세미콜론 등의 텍스트 또는 문자입니다.</span><span class="sxs-lookup"><span data-stu-id="1cf19-167">Text or characters such as a comma or semicolon that's inserted between the text for each pipeline object.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1cf19-168">-SingleQuote</span><span class="sxs-lookup"><span data-stu-id="1cf19-168">-SingleQuote</span></span>

<span data-ttu-id="1cf19-169">각 파이프라인 개체의 문자열 값을 작은따옴표로 래핑합니다.</span><span class="sxs-lookup"><span data-stu-id="1cf19-169">Wraps the string value of each pipeline object in single quotes.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: SingleQuote
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1cf19-170">-UseCulture</span><span class="sxs-lookup"><span data-stu-id="1cf19-170">-UseCulture</span></span>

<span data-ttu-id="1cf19-171">현재 문화권의 목록 구분 기호를 항목 구분 기호로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1cf19-171">Uses the list separator for the current culture as the item delimiter.</span></span> <span data-ttu-id="1cf19-172">문화권에 대 한 목록 구분 기호를 찾으려면 다음 명령을 사용 합니다. `(Get-Culture).TextInfo.ListSeparator`</span><span class="sxs-lookup"><span data-stu-id="1cf19-172">To find the list separator for a culture, use the following command: `(Get-Culture).TextInfo.ListSeparator`.</span></span>

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

### <span data-ttu-id="1cf19-173">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1cf19-173">CommonParameters</span></span>

<span data-ttu-id="1cf19-174">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1cf19-174">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1cf19-175">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1cf19-175">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1cf19-176">입력</span><span class="sxs-lookup"><span data-stu-id="1cf19-176">INPUTS</span></span>

### <span data-ttu-id="1cf19-177">System.web. PSObject</span><span class="sxs-lookup"><span data-stu-id="1cf19-177">System.Management.Automation.PSObject</span></span>

## <span data-ttu-id="1cf19-178">출력</span><span class="sxs-lookup"><span data-stu-id="1cf19-178">OUTPUTS</span></span>

### <span data-ttu-id="1cf19-179">System.String</span><span class="sxs-lookup"><span data-stu-id="1cf19-179">System.String</span></span>

## <span data-ttu-id="1cf19-180">참고</span><span class="sxs-lookup"><span data-stu-id="1cf19-180">NOTES</span></span>

## <span data-ttu-id="1cf19-181">관련 링크</span><span class="sxs-lookup"><span data-stu-id="1cf19-181">RELATED LINKS</span></span>

[<span data-ttu-id="1cf19-182">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="1cf19-182">about_Automatic_Variables</span></span>](../microsoft.powershell.core/about/about_automatic_variables.md)

[<span data-ttu-id="1cf19-183">about_Special_Characters</span><span class="sxs-lookup"><span data-stu-id="1cf19-183">about_Special_Characters</span></span>](..//microsoft.powershell.core/about/about_special_characters.md)

[<span data-ttu-id="1cf19-184">부분</span><span class="sxs-lookup"><span data-stu-id="1cf19-184">Substring</span></span>](/dotnet/api/system.string.substring)
