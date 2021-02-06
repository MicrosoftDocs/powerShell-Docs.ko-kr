---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-wide?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-Wide
ms.openlocfilehash: ba61c2d24d85256c55a7409fc368de4407aad5a9
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99602438"
---
# <span data-ttu-id="49214-102">Format-Wide</span><span class="sxs-lookup"><span data-stu-id="49214-102">Format-Wide</span></span>

## <span data-ttu-id="49214-103">개요</span><span class="sxs-lookup"><span data-stu-id="49214-103">SYNOPSIS</span></span>
<span data-ttu-id="49214-104">개체를 각 개체의 한 속성만을 표시하는 넓은 표 형식으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="49214-104">Formats objects as a wide table that displays only one property of each object.</span></span>

## <span data-ttu-id="49214-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="49214-105">SYNTAX</span></span>

```
Format-Wide [[-Property] <Object>] [-AutoSize] [-Column <int>] [-GroupBy <Object>] [-View <string>]
  [-ShowError] [-DisplayError] [-Force] [-Expand <string>] [-InputObject <psobject>]
  [<CommonParameters>]
```

## <span data-ttu-id="49214-106">설명</span><span class="sxs-lookup"><span data-stu-id="49214-106">DESCRIPTION</span></span>

<span data-ttu-id="49214-107">`Format-Wide`Cmdlet은 각 개체의 속성을 하나만 표시 하는 넓은 테이블로 개체의 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="49214-107">The `Format-Wide` cmdlet formats objects as a wide table that displays only one property of each object.</span></span> <span data-ttu-id="49214-108">**Property** 매개 변수를 사용 하 여 표시 되는 속성을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49214-108">You can use the **Property** parameter to determine which property is displayed.</span></span>

## <span data-ttu-id="49214-109">예제</span><span class="sxs-lookup"><span data-stu-id="49214-109">EXAMPLES</span></span>

### <span data-ttu-id="49214-110">예 1: 현재 디렉터리에 있는 파일의 형식 이름</span><span class="sxs-lookup"><span data-stu-id="49214-110">Example 1: Format names of files in the current directory</span></span>

<span data-ttu-id="49214-111">이 명령은 화면 전체의 세 열에 현재 디렉터리의 파일 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="49214-111">This command displays the names of files in the current directory in three columns across the screen.</span></span>

```powershell
Get-ChildItem | Format-Wide -Column 3
```

<span data-ttu-id="49214-112">Get-ChildItem cmdlet은 디렉터리의 각 파일을 나타내는 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="49214-112">The Get-ChildItem cmdlet gets objects representing each file in the directory.</span></span> <span data-ttu-id="49214-113">파이프라인 연산자 (|)가 파이프라인을 통해 파일 개체를에 전달 하 여 `Format-Wide` 출력 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="49214-113">The pipeline operator (|) passes the file objects through the pipeline to `Format-Wide`, which formats them for output.</span></span> <span data-ttu-id="49214-114">**Column** 매개 변수는 열 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="49214-114">The **Column** parameter specifies the number of columns.</span></span>

### <span data-ttu-id="49214-115">예제 2: 레지스트리 키의 형식 이름</span><span class="sxs-lookup"><span data-stu-id="49214-115">Example 2: Format names of registry keys</span></span>

<span data-ttu-id="49214-116">이 명령은 HKEY_CURRENT_USER\Software\Microsoft 키에 레지스트리 키의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="49214-116">This command displays the names of registry keys in the HKEY_CURRENT_USER\Software\Microsoft key.</span></span>

```powershell
Get-ChildItem HKCU:\software\microsoft | Format-Wide -Property pschildname -AutoSize
```

<span data-ttu-id="49214-117">Get-ChildItem cmdlet은 키를 나타내는 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="49214-117">The Get-ChildItem cmdlet gets objects representing the keys.</span></span> <span data-ttu-id="49214-118">경로는 HKCU:, PowerShell 레지스트리 공급자에 의해 노출 되는 드라이브 중 하나인 키 경로로 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="49214-118">The path is specified as HKCU:, one of the drives exposed by the PowerShell Registry provider, followed by the key path.</span></span> <span data-ttu-id="49214-119">파이프라인 연산자 (|)가 파이프라인을 통해 레지스트리 키 개체를에 전달 하 여 `Format-Wide` 출력 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="49214-119">The pipeline operator (|) passes the registry key objects through the pipeline to `Format-Wide`, which formats them for output.</span></span> <span data-ttu-id="49214-120">**Property** 매개 변수는 속성의 이름을 지정 하 고 **AutoSize** 매개 변수는 가독성을 위해 열을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="49214-120">The **Property** parameter specifies the name of the property, and the **AutoSize** parameter adjusts the columns for readability.</span></span>

### <span data-ttu-id="49214-121">예 3: 형식 오류 문제 해결</span><span class="sxs-lookup"><span data-stu-id="49214-121">Example 3: Troubleshooting format errors</span></span>

<span data-ttu-id="49214-122">다음 예에서는 식을 사용 하 여 **displayerror** 또는 **showerror** 매개 변수를 추가 하는 결과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="49214-122">The following examples show of the results of adding the **DisplayError** or **ShowError** parameters with an expression.</span></span>

```powershell
PS /> Get-Date | Format-Wide { $_ / $null } -DisplayError


#ERR

PS /> Get-Date | Format-Wide { $_ / $null } -ShowError


Failed to evaluate expression " $_ / $null ".
+ CategoryInfo          : InvalidArgument: (12/21/2018 8:18:01 AM:PSObject) [], RuntimeException
+ FullyQualifiedErrorId : PSPropertyExpressionError
```

## <span data-ttu-id="49214-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="49214-123">PARAMETERS</span></span>

### <span data-ttu-id="49214-124">-AutoSize</span><span class="sxs-lookup"><span data-stu-id="49214-124">-AutoSize</span></span>

<span data-ttu-id="49214-125">데이터의 너비에 따라 열 크기 및 열 수를 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="49214-125">Adjusts the column size and number of columns based on the width of the data.</span></span> <span data-ttu-id="49214-126">기본적으로 열 크기 및 수는 뷰에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="49214-126">By default, the column size and number are determined by the view.</span></span> <span data-ttu-id="49214-127">**AutoSize** 및 **Column** 매개 변수는 동일한 명령에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="49214-127">You cannot use the **AutoSize** and **Column** parameters in the same command.</span></span>

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

### <span data-ttu-id="49214-128">-열</span><span class="sxs-lookup"><span data-stu-id="49214-128">-Column</span></span>

<span data-ttu-id="49214-129">표시에서 열의 개수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="49214-129">Specifies the number of columns in the display.</span></span> <span data-ttu-id="49214-130">**AutoSize** 및 **Column** 매개 변수는 동일한 명령에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="49214-130">You cannot use the **AutoSize** and **Column** parameters in the same command.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="49214-131">-DisplayError</span><span class="sxs-lookup"><span data-stu-id="49214-131">-DisplayError</span></span>

<span data-ttu-id="49214-132">명령줄에 오류를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="49214-132">Displays errors at the command line.</span></span> <span data-ttu-id="49214-133">이 매개 변수는 거의 사용 되지 않지만 명령에서 식의 형식을 지정할 때 식이 작동 하지 않는 것으로 표시 되는 경우 디버깅 도구로 사용할 수 있습니다 `Format-Wide` .</span><span class="sxs-lookup"><span data-stu-id="49214-133">This parameter is rarely used, but can be used as a debugging aid when you are formatting expressions in a `Format-Wide` command, and the expressions do not appear to be working.</span></span>

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

### <span data-ttu-id="49214-134">-확장</span><span class="sxs-lookup"><span data-stu-id="49214-134">-Expand</span></span>

<span data-ttu-id="49214-135">컬렉션의 개체와 함께 컬렉션 개체의 형식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="49214-135">Formats the collection object, as well as the objects in the collection.</span></span> <span data-ttu-id="49214-136">이 매개 변수는 ICollection(System.Collections) 인터페이스를 지원하는 개체의 형식을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49214-136">This parameter is designed to format objects that support the ICollection (System.Collections) interface.</span></span> <span data-ttu-id="49214-137">기본값은 **Enumonly** 입니다.</span><span class="sxs-lookup"><span data-stu-id="49214-137">The default value is **EnumOnly**.</span></span>

<span data-ttu-id="49214-138">유효한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="49214-138">Valid values are:</span></span>

- <span data-ttu-id="49214-139">EnumOnly: 컬렉션에 있는 개체의 속성을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="49214-139">EnumOnly: Displays the properties of the objects in the collection.</span></span>
- <span data-ttu-id="49214-140">CoreOnly: 컬렉션 개체의 속성을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="49214-140">CoreOnly: Displays the properties of the collection object.</span></span>
- <span data-ttu-id="49214-141">Both: 컬렉션 개체의 속성과 컬렉션에 있는 개체의 속성을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="49214-141">Both: Displays the properties of the collection object and the properties of objects in the collection.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: CoreOnly, EnumOnly, Both

Required: False
Position: Named
Default value: EnumOnly
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="49214-142">-Force</span><span class="sxs-lookup"><span data-stu-id="49214-142">-Force</span></span>

<span data-ttu-id="49214-143">이 cmdlet은 명령이 성공 하는 것을 방해 하는 제한을 무시 하므로 변경 내용이 보안을 손상 시 키 지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="49214-143">Indicates that this cmdlet overrides restrictions that prevent the command from succeeding, just so the changes do not compromise security.</span></span> <span data-ttu-id="49214-144">예를 들어 **Force** 는 읽기 전용 특성을 재정의하거나, 디렉터리를 만들어 파일 경로를 완성할 수 있지만 파일 사용 권한을 변경하지는 못합니다.</span><span class="sxs-lookup"><span data-stu-id="49214-144">For example, **Force** will override the read-only attribute or create directories to complete a file path, but it will not attempt to change file permissions.</span></span>

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

### <span data-ttu-id="49214-145">-GroupBy</span><span class="sxs-lookup"><span data-stu-id="49214-145">-GroupBy</span></span>

<span data-ttu-id="49214-146">공유 속성이나 값에 따라 그룹으로 출력 형식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="49214-146">Formats the output in groups based on a shared property or value.</span></span> <span data-ttu-id="49214-147">출력의 식이나 속성을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="49214-147">Enter an expression or a property of the output.</span></span>

<span data-ttu-id="49214-148">**GroupBy** 매개 변수 값은 새 계산 된 속성 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49214-148">The value of the **GroupBy** parameter can be a new calculated property.</span></span> <span data-ttu-id="49214-149">계산 된 속성은 스크립트 블록이 나 해시 테이블 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49214-149">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="49214-150">유효한 키-값 쌍은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="49214-150">Valid key-value pairs are:</span></span>

- <span data-ttu-id="49214-151">이름 (또는 레이블)- `<string>`</span><span class="sxs-lookup"><span data-stu-id="49214-151">Name (or Label) - `<string>`</span></span>
- <span data-ttu-id="49214-152">식 `<string>` 또는 `<script block>`</span><span class="sxs-lookup"><span data-stu-id="49214-152">Expression - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="49214-153">FormatString `<string>`</span><span class="sxs-lookup"><span data-stu-id="49214-153">FormatString - `<string>`</span></span>

<span data-ttu-id="49214-154">자세한 내용은 [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="49214-154">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

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

### <span data-ttu-id="49214-155">-InputObject</span><span class="sxs-lookup"><span data-stu-id="49214-155">-InputObject</span></span>

<span data-ttu-id="49214-156">형식을 지정할 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="49214-156">Specifies the objects to format.</span></span> <span data-ttu-id="49214-157">개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="49214-157">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="49214-158">-속성</span><span class="sxs-lookup"><span data-stu-id="49214-158">-Property</span></span>

<span data-ttu-id="49214-159">표시에 나타나는 개체 속성 및 표시되는 순서를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="49214-159">Specifies the object properties that appear in the display and the order in which they appear.</span></span>
<span data-ttu-id="49214-160">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="49214-160">Wildcards are permitted.</span></span>

<span data-ttu-id="49214-161">이 매개 변수를 생략할 경우 표시에 나타나는 속성은 표시되는 개체에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="49214-161">If you omit this parameter, the properties that appear in the display depend on the object being displayed.</span></span> <span data-ttu-id="49214-162">"Property" 매개 변수 이름은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="49214-162">The parameter name "Property" is optional.</span></span> <span data-ttu-id="49214-163">동일한 명령에서 **Property** 및 **View** 매개 변수를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="49214-163">You cannot use the **Property** and **View** parameters in the same command.</span></span>

<span data-ttu-id="49214-164">**Property** 매개 변수 값은 새 계산 된 속성 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49214-164">The value of the **Property** parameter can be a new calculated property.</span></span> <span data-ttu-id="49214-165">계산 된 속성은 스크립트 블록이 나 해시 테이블 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49214-165">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="49214-166">유효한 키-값 쌍은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="49214-166">Valid key-value pairs are:</span></span>

- <span data-ttu-id="49214-167">식 `<string>` 또는 `<script block>`</span><span class="sxs-lookup"><span data-stu-id="49214-167">Expression - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="49214-168">FormatString `<string>`</span><span class="sxs-lookup"><span data-stu-id="49214-168">FormatString - `<string>`</span></span>

<span data-ttu-id="49214-169">자세한 내용은 [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="49214-169">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="49214-170">-ShowError</span><span class="sxs-lookup"><span data-stu-id="49214-170">-ShowError</span></span>

<span data-ttu-id="49214-171">파이프라인을 통해 오류를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="49214-171">Sends errors through the pipeline.</span></span> <span data-ttu-id="49214-172">이 매개 변수는 거의 사용 되지 않지만 명령에서 식의 형식을 지정할 때 식이 작동 하지 않는 것으로 표시 되는 경우 디버깅 도구로 사용할 수 있습니다 `Format-Wide` .</span><span class="sxs-lookup"><span data-stu-id="49214-172">This parameter is rarely used, but can be used as a debugging aid when you are formatting expressions in a `Format-Wide` command, and the expressions do not appear to be working.</span></span>

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

### <span data-ttu-id="49214-173">-보기</span><span class="sxs-lookup"><span data-stu-id="49214-173">-View</span></span>

<span data-ttu-id="49214-174">대체 테이블 형식 또는 뷰의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="49214-174">Specifies the name of an alternate table format or view.</span></span> <span data-ttu-id="49214-175">동일한 명령에서 **Property** 및 **View** 매개 변수를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="49214-175">You cannot use the **Property** and **View** parameters in the same command.</span></span>

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

### <span data-ttu-id="49214-176">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="49214-176">CommonParameters</span></span>

<span data-ttu-id="49214-177">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="49214-177">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="49214-178">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="49214-178">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="49214-179">입력</span><span class="sxs-lookup"><span data-stu-id="49214-179">INPUTS</span></span>

### <span data-ttu-id="49214-180">System.web. PSObject</span><span class="sxs-lookup"><span data-stu-id="49214-180">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="49214-181">모든 개체를로 파이프 할 수 있습니다 `Format-Wide` .</span><span class="sxs-lookup"><span data-stu-id="49214-181">You can pipe any object to `Format-Wide`.</span></span>

## <span data-ttu-id="49214-182">출력</span><span class="sxs-lookup"><span data-stu-id="49214-182">OUTPUTS</span></span>

### <span data-ttu-id="49214-183">Microsoft. PowerShell. Internal. Format</span><span class="sxs-lookup"><span data-stu-id="49214-183">Microsoft.PowerShell.Commands.Internal.Format</span></span>

<span data-ttu-id="49214-184">`Format-Wide` 테이블을 나타내는 형식 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="49214-184">`Format-Wide` returns format objects that represent the table.</span></span>

## <span data-ttu-id="49214-185">참고</span><span class="sxs-lookup"><span data-stu-id="49214-185">NOTES</span></span>

<span data-ttu-id="49214-186">의 기본 제공 별칭인를 참조할 수도 있습니다 `Format-Wide` `fw` .</span><span class="sxs-lookup"><span data-stu-id="49214-186">You can also refer to `Format-Wide` by its built-in alias, `fw`.</span></span> <span data-ttu-id="49214-187">자세한 내용은 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="49214-187">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

<span data-ttu-id="49214-188">**GroupBy** 매개 변수는 개체가 정렬 되어 있다고 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="49214-188">The **GroupBy** parameter assumes that the objects are sorted.</span></span> <span data-ttu-id="49214-189">를 사용 하 여 `Sort-Object` 개체를 그룹화 하기 전에 `Format-Custom` 를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="49214-189">Use `Sort-Object` before using `Format-Custom` to group the objects.</span></span>

<span data-ttu-id="49214-190">**View** 매개 변수를 사용 하 여 테이블에 대 한 대체 형식을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49214-190">The **View** parameter lets you specify an alternate format for the table.</span></span> <span data-ttu-id="49214-191">PowerShell 디렉터리의 파일에 정의 된 보기를 사용 `*.format.PS1XML` 하거나 새 types.ps1xml 파일에서 고유한 뷰를 만들고 `Update-FormatData` cmdlet을 사용 하 여 powershell에 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49214-191">You can use the views defined in the `*.format.PS1XML` files in the PowerShell directory or you can create your own views in new PS1XML files and use the `Update-FormatData` cmdlet to include them in PowerShell.</span></span>

<span data-ttu-id="49214-192">**View** 매개 변수의 대체 뷰에서는 테이블 형식을 사용 해야 합니다. 그렇지 않으면 명령이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="49214-192">The alternate view for the **View** parameter must use table format; if it does not, the command fails.</span></span> <span data-ttu-id="49214-193">대체 뷰가 목록이 면를 사용 `Format-List` 합니다.</span><span class="sxs-lookup"><span data-stu-id="49214-193">If the alternate view is a list, use `Format-List`.</span></span> <span data-ttu-id="49214-194">대체 뷰가 목록이나 테이블이 아니면 Format-Custom을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="49214-194">If the alternate view is neither a list nor a table, use Format-Custom.</span></span>

## <span data-ttu-id="49214-195">관련 링크</span><span class="sxs-lookup"><span data-stu-id="49214-195">RELATED LINKS</span></span>

[<span data-ttu-id="49214-196">about_Calculated_Properties</span><span class="sxs-lookup"><span data-stu-id="49214-196">about_Calculated_Properties</span></span>](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[<span data-ttu-id="49214-197">Format-Custom</span><span class="sxs-lookup"><span data-stu-id="49214-197">Format-Custom</span></span>](Format-Custom.md)

[<span data-ttu-id="49214-198">Format-Hex</span><span class="sxs-lookup"><span data-stu-id="49214-198">Format-Hex</span></span>](Format-Hex.md)

[<span data-ttu-id="49214-199">Format-List</span><span class="sxs-lookup"><span data-stu-id="49214-199">Format-List</span></span>](Format-List.md)

[<span data-ttu-id="49214-200">Format-Table</span><span class="sxs-lookup"><span data-stu-id="49214-200">Format-Table</span></span>](Format-Table.md)
