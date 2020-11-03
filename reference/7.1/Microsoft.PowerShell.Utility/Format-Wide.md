---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-wide?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-Wide
ms.openlocfilehash: eed3ba1982792cc5675b7343525e1182f9e6a420
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/10/2020
ms.locfileid: "93219457"
---
# <span data-ttu-id="37910-103">Format-Wide</span><span class="sxs-lookup"><span data-stu-id="37910-103">Format-Wide</span></span>

## <span data-ttu-id="37910-104">개요</span><span class="sxs-lookup"><span data-stu-id="37910-104">SYNOPSIS</span></span>
<span data-ttu-id="37910-105">개체를 각 개체의 한 속성만을 표시하는 넓은 표 형식으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="37910-105">Formats objects as a wide table that displays only one property of each object.</span></span>

## <span data-ttu-id="37910-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="37910-106">SYNTAX</span></span>

```
Format-Wide [[-Property] <Object>] [-AutoSize] [-Column <int>] [-GroupBy <Object>] [-View <string>]
  [-ShowError] [-DisplayError] [-Force] [-Expand <string>] [-InputObject <psobject>]
  [<CommonParameters>]
```

## <span data-ttu-id="37910-107">설명</span><span class="sxs-lookup"><span data-stu-id="37910-107">DESCRIPTION</span></span>

<span data-ttu-id="37910-108">`Format-Wide`Cmdlet은 각 개체의 속성을 하나만 표시 하는 넓은 테이블로 개체의 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="37910-108">The `Format-Wide` cmdlet formats objects as a wide table that displays only one property of each object.</span></span> <span data-ttu-id="37910-109">**Property** 매개 변수를 사용 하 여 표시 되는 속성을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37910-109">You can use the **Property** parameter to determine which property is displayed.</span></span>

## <span data-ttu-id="37910-110">예제</span><span class="sxs-lookup"><span data-stu-id="37910-110">EXAMPLES</span></span>

### <span data-ttu-id="37910-111">예 1: 현재 디렉터리에 있는 파일의 형식 이름</span><span class="sxs-lookup"><span data-stu-id="37910-111">Example 1: Format names of files in the current directory</span></span>

<span data-ttu-id="37910-112">이 명령은 화면 전체의 세 열에 현재 디렉터리의 파일 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="37910-112">This command displays the names of files in the current directory in three columns across the screen.</span></span>

```powershell
Get-ChildItem | Format-Wide -Column 3
```

<span data-ttu-id="37910-113">Get-ChildItem cmdlet은 디렉터리의 각 파일을 나타내는 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="37910-113">The Get-ChildItem cmdlet gets objects representing each file in the directory.</span></span> <span data-ttu-id="37910-114">파이프라인 연산자 (|)가 파이프라인을 통해 파일 개체를에 전달 하 여 `Format-Wide` 출력 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="37910-114">The pipeline operator (|) passes the file objects through the pipeline to `Format-Wide`, which formats them for output.</span></span> <span data-ttu-id="37910-115">**Column** 매개 변수는 열 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="37910-115">The **Column** parameter specifies the number of columns.</span></span>

### <span data-ttu-id="37910-116">예제 2: 레지스트리 키의 형식 이름</span><span class="sxs-lookup"><span data-stu-id="37910-116">Example 2: Format names of registry keys</span></span>

<span data-ttu-id="37910-117">이 명령은 HKEY_CURRENT_USER\Software\Microsoft 키에 레지스트리 키의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="37910-117">This command displays the names of registry keys in the HKEY_CURRENT_USER\Software\Microsoft key.</span></span>

```powershell
Get-ChildItem HKCU:\software\microsoft | Format-Wide -Property pschildname -AutoSize
```

<span data-ttu-id="37910-118">Get-ChildItem cmdlet은 키를 나타내는 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="37910-118">The Get-ChildItem cmdlet gets objects representing the keys.</span></span> <span data-ttu-id="37910-119">경로는 HKCU:, PowerShell 레지스트리 공급자에 의해 노출 되는 드라이브 중 하나인 키 경로로 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="37910-119">The path is specified as HKCU:, one of the drives exposed by the PowerShell Registry provider, followed by the key path.</span></span> <span data-ttu-id="37910-120">파이프라인 연산자 (|)가 파이프라인을 통해 레지스트리 키 개체를에 전달 하 여 `Format-Wide` 출력 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="37910-120">The pipeline operator (|) passes the registry key objects through the pipeline to `Format-Wide`, which formats them for output.</span></span> <span data-ttu-id="37910-121">**Property** 매개 변수는 속성의 이름을 지정 하 고 **AutoSize** 매개 변수는 가독성을 위해 열을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="37910-121">The **Property** parameter specifies the name of the property, and the **AutoSize** parameter adjusts the columns for readability.</span></span>

### <span data-ttu-id="37910-122">예 3: 형식 오류 문제 해결</span><span class="sxs-lookup"><span data-stu-id="37910-122">Example 3: Troubleshooting format errors</span></span>

<span data-ttu-id="37910-123">다음 예에서는 식을 사용 하 여 **displayerror** 또는 **showerror** 매개 변수를 추가 하는 결과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="37910-123">The following examples show of the results of adding the **DisplayError** or **ShowError** parameters with an expression.</span></span>

```powershell
PS /> Get-Date | Format-Wide { $_ / $null } -DisplayError


#ERR

PS /> Get-Date | Format-Wide { $_ / $null } -ShowError


Failed to evaluate expression " $_ / $null ".
+ CategoryInfo          : InvalidArgument: (12/21/2018 8:18:01 AM:PSObject) [], RuntimeException
+ FullyQualifiedErrorId : PSPropertyExpressionError
```

## <span data-ttu-id="37910-124">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="37910-124">PARAMETERS</span></span>

### <span data-ttu-id="37910-125">-AutoSize</span><span class="sxs-lookup"><span data-stu-id="37910-125">-AutoSize</span></span>

<span data-ttu-id="37910-126">데이터의 너비에 따라 열 크기 및 열 수를 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="37910-126">Adjusts the column size and number of columns based on the width of the data.</span></span> <span data-ttu-id="37910-127">기본적으로 열 크기 및 수는 뷰에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="37910-127">By default, the column size and number are determined by the view.</span></span> <span data-ttu-id="37910-128">**AutoSize** 및 **Column** 매개 변수는 동일한 명령에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="37910-128">You cannot use the **AutoSize** and **Column** parameters in the same command.</span></span>

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

### <span data-ttu-id="37910-129">-열</span><span class="sxs-lookup"><span data-stu-id="37910-129">-Column</span></span>

<span data-ttu-id="37910-130">표시에서 열의 개수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="37910-130">Specifies the number of columns in the display.</span></span> <span data-ttu-id="37910-131">**AutoSize** 및 **Column** 매개 변수는 동일한 명령에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="37910-131">You cannot use the **AutoSize** and **Column** parameters in the same command.</span></span>

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

### <span data-ttu-id="37910-132">-DisplayError</span><span class="sxs-lookup"><span data-stu-id="37910-132">-DisplayError</span></span>

<span data-ttu-id="37910-133">명령줄에 오류를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="37910-133">Displays errors at the command line.</span></span> <span data-ttu-id="37910-134">이 매개 변수는 거의 사용 되지 않지만 명령에서 식의 형식을 지정할 때 식이 작동 하지 않는 것으로 표시 되는 경우 디버깅 도구로 사용할 수 있습니다 `Format-Wide` .</span><span class="sxs-lookup"><span data-stu-id="37910-134">This parameter is rarely used, but can be used as a debugging aid when you are formatting expressions in a `Format-Wide` command, and the expressions do not appear to be working.</span></span>

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

### <span data-ttu-id="37910-135">-확장</span><span class="sxs-lookup"><span data-stu-id="37910-135">-Expand</span></span>

<span data-ttu-id="37910-136">컬렉션의 개체와 함께 컬렉션 개체의 형식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="37910-136">Formats the collection object, as well as the objects in the collection.</span></span> <span data-ttu-id="37910-137">이 매개 변수는 ICollection(System.Collections) 인터페이스를 지원하는 개체의 형식을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37910-137">This parameter is designed to format objects that support the ICollection (System.Collections) interface.</span></span> <span data-ttu-id="37910-138">기본값은 **Enumonly** 입니다.</span><span class="sxs-lookup"><span data-stu-id="37910-138">The default value is **EnumOnly**.</span></span>

<span data-ttu-id="37910-139">유효한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="37910-139">Valid values are:</span></span>

- <span data-ttu-id="37910-140">EnumOnly: 컬렉션에 있는 개체의 속성을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="37910-140">EnumOnly: Displays the properties of the objects in the collection.</span></span>
- <span data-ttu-id="37910-141">CoreOnly: 컬렉션 개체의 속성을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="37910-141">CoreOnly: Displays the properties of the collection object.</span></span>
- <span data-ttu-id="37910-142">Both: 컬렉션 개체의 속성과 컬렉션에 있는 개체의 속성을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="37910-142">Both: Displays the properties of the collection object and the properties of objects in the collection.</span></span>

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

### <span data-ttu-id="37910-143">-Force</span><span class="sxs-lookup"><span data-stu-id="37910-143">-Force</span></span>

<span data-ttu-id="37910-144">이 cmdlet은 명령이 성공 하는 것을 방해 하는 제한을 무시 하므로 변경 내용이 보안을 손상 시 키 지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="37910-144">Indicates that this cmdlet overrides restrictions that prevent the command from succeeding, just so the changes do not compromise security.</span></span> <span data-ttu-id="37910-145">예를 들어 **Force** 는 읽기 전용 특성을 재정의하거나, 디렉터리를 만들어 파일 경로를 완성할 수 있지만 파일 사용 권한을 변경하지는 못합니다.</span><span class="sxs-lookup"><span data-stu-id="37910-145">For example, **Force** will override the read-only attribute or create directories to complete a file path, but it will not attempt to change file permissions.</span></span>

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

### <span data-ttu-id="37910-146">-GroupBy</span><span class="sxs-lookup"><span data-stu-id="37910-146">-GroupBy</span></span>

<span data-ttu-id="37910-147">공유 속성이나 값에 따라 그룹으로 출력 형식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="37910-147">Formats the output in groups based on a shared property or value.</span></span> <span data-ttu-id="37910-148">출력의 식이나 속성을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="37910-148">Enter an expression or a property of the output.</span></span>

<span data-ttu-id="37910-149">**GroupBy** 매개 변수 값은 새 계산 된 속성 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37910-149">The value of the **GroupBy** parameter can be a new calculated property.</span></span> <span data-ttu-id="37910-150">계산 된 속성은 스크립트 블록이 나 해시 테이블 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37910-150">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="37910-151">유효한 키-값 쌍은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="37910-151">Valid key-value pairs are:</span></span>

- <span data-ttu-id="37910-152">이름 (또는 레이블)- `<string>`</span><span class="sxs-lookup"><span data-stu-id="37910-152">Name (or Label) - `<string>`</span></span>
- <span data-ttu-id="37910-153">식 `<string>` 또는 `<script block>`</span><span class="sxs-lookup"><span data-stu-id="37910-153">Expression - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="37910-154">FormatString `<string>`</span><span class="sxs-lookup"><span data-stu-id="37910-154">FormatString - `<string>`</span></span>

<span data-ttu-id="37910-155">자세한 내용은 [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="37910-155">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

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

### <span data-ttu-id="37910-156">-InputObject</span><span class="sxs-lookup"><span data-stu-id="37910-156">-InputObject</span></span>

<span data-ttu-id="37910-157">형식을 지정할 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="37910-157">Specifies the objects to format.</span></span> <span data-ttu-id="37910-158">개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="37910-158">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="37910-159">-속성</span><span class="sxs-lookup"><span data-stu-id="37910-159">-Property</span></span>

<span data-ttu-id="37910-160">표시에 나타나는 개체 속성 및 표시되는 순서를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="37910-160">Specifies the object properties that appear in the display and the order in which they appear.</span></span>
<span data-ttu-id="37910-161">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="37910-161">Wildcards are permitted.</span></span>

<span data-ttu-id="37910-162">이 매개 변수를 생략할 경우 표시에 나타나는 속성은 표시되는 개체에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="37910-162">If you omit this parameter, the properties that appear in the display depend on the object being displayed.</span></span> <span data-ttu-id="37910-163">"Property" 매개 변수 이름은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="37910-163">The parameter name "Property" is optional.</span></span> <span data-ttu-id="37910-164">동일한 명령에서 **Property** 및 **View** 매개 변수를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="37910-164">You cannot use the **Property** and **View** parameters in the same command.</span></span>

<span data-ttu-id="37910-165">**Property** 매개 변수 값은 새 계산 된 속성 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37910-165">The value of the **Property** parameter can be a new calculated property.</span></span> <span data-ttu-id="37910-166">계산 된 속성은 스크립트 블록이 나 해시 테이블 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37910-166">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="37910-167">유효한 키-값 쌍은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="37910-167">Valid key-value pairs are:</span></span>

- <span data-ttu-id="37910-168">식 `<string>` 또는 `<script block>`</span><span class="sxs-lookup"><span data-stu-id="37910-168">Expression - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="37910-169">FormatString `<string>`</span><span class="sxs-lookup"><span data-stu-id="37910-169">FormatString - `<string>`</span></span>

<span data-ttu-id="37910-170">자세한 내용은 [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="37910-170">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

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

### <span data-ttu-id="37910-171">-ShowError</span><span class="sxs-lookup"><span data-stu-id="37910-171">-ShowError</span></span>

<span data-ttu-id="37910-172">파이프라인을 통해 오류를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="37910-172">Sends errors through the pipeline.</span></span> <span data-ttu-id="37910-173">이 매개 변수는 거의 사용 되지 않지만 명령에서 식의 형식을 지정할 때 식이 작동 하지 않는 것으로 표시 되는 경우 디버깅 도구로 사용할 수 있습니다 `Format-Wide` .</span><span class="sxs-lookup"><span data-stu-id="37910-173">This parameter is rarely used, but can be used as a debugging aid when you are formatting expressions in a `Format-Wide` command, and the expressions do not appear to be working.</span></span>

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

### <span data-ttu-id="37910-174">-보기</span><span class="sxs-lookup"><span data-stu-id="37910-174">-View</span></span>

<span data-ttu-id="37910-175">대체 테이블 형식 또는 뷰의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="37910-175">Specifies the name of an alternate table format or view.</span></span> <span data-ttu-id="37910-176">동일한 명령에서 **Property** 및 **View** 매개 변수를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="37910-176">You cannot use the **Property** and **View** parameters in the same command.</span></span>

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

### <span data-ttu-id="37910-177">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="37910-177">CommonParameters</span></span>

<span data-ttu-id="37910-178">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="37910-178">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="37910-179">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="37910-179">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="37910-180">입력</span><span class="sxs-lookup"><span data-stu-id="37910-180">INPUTS</span></span>

### <span data-ttu-id="37910-181">System.web. PSObject</span><span class="sxs-lookup"><span data-stu-id="37910-181">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="37910-182">모든 개체를로 파이프 할 수 있습니다 `Format-Wide` .</span><span class="sxs-lookup"><span data-stu-id="37910-182">You can pipe any object to `Format-Wide`.</span></span>

## <span data-ttu-id="37910-183">출력</span><span class="sxs-lookup"><span data-stu-id="37910-183">OUTPUTS</span></span>

### <span data-ttu-id="37910-184">Microsoft. PowerShell. Internal. Format</span><span class="sxs-lookup"><span data-stu-id="37910-184">Microsoft.PowerShell.Commands.Internal.Format</span></span>

<span data-ttu-id="37910-185">`Format-Wide` 테이블을 나타내는 형식 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="37910-185">`Format-Wide` returns format objects that represent the table.</span></span>

## <span data-ttu-id="37910-186">참고</span><span class="sxs-lookup"><span data-stu-id="37910-186">NOTES</span></span>

<span data-ttu-id="37910-187">의 기본 제공 별칭인를 참조할 수도 있습니다 `Format-Wide` `fw` .</span><span class="sxs-lookup"><span data-stu-id="37910-187">You can also refer to `Format-Wide` by its built-in alias, `fw`.</span></span> <span data-ttu-id="37910-188">자세한 내용은 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="37910-188">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

<span data-ttu-id="37910-189">**GroupBy** 매개 변수는 개체가 정렬 되어 있다고 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="37910-189">The **GroupBy** parameter assumes that the objects are sorted.</span></span> <span data-ttu-id="37910-190">를 사용 하 여 `Sort-Object` 개체를 그룹화 하기 전에 `Format-Custom` 를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="37910-190">Use `Sort-Object` before using `Format-Custom` to group the objects.</span></span>

<span data-ttu-id="37910-191">**View** 매개 변수를 사용 하 여 테이블에 대 한 대체 형식을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37910-191">The **View** parameter lets you specify an alternate format for the table.</span></span> <span data-ttu-id="37910-192">PowerShell 디렉터리의 파일에 정의 된 보기를 사용 `*.format.PS1XML` 하거나 새 types.ps1xml 파일에서 고유한 뷰를 만들고 `Update-FormatData` cmdlet을 사용 하 여 powershell에 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37910-192">You can use the views defined in the `*.format.PS1XML` files in the PowerShell directory or you can create your own views in new PS1XML files and use the `Update-FormatData` cmdlet to include them in PowerShell.</span></span>

<span data-ttu-id="37910-193">**View** 매개 변수의 대체 뷰에서는 테이블 형식을 사용 해야 합니다. 그렇지 않으면 명령이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="37910-193">The alternate view for the **View** parameter must use table format; if it does not, the command fails.</span></span> <span data-ttu-id="37910-194">대체 뷰가 목록이 면를 사용 `Format-List` 합니다.</span><span class="sxs-lookup"><span data-stu-id="37910-194">If the alternate view is a list, use `Format-List`.</span></span> <span data-ttu-id="37910-195">대체 뷰가 목록이나 테이블이 아니면 Format-Custom을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="37910-195">If the alternate view is neither a list nor a table, use Format-Custom.</span></span>

## <span data-ttu-id="37910-196">관련 링크</span><span class="sxs-lookup"><span data-stu-id="37910-196">RELATED LINKS</span></span>

[<span data-ttu-id="37910-197">about_Calculated_Properties</span><span class="sxs-lookup"><span data-stu-id="37910-197">about_Calculated_Properties</span></span>](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[<span data-ttu-id="37910-198">Format-Custom</span><span class="sxs-lookup"><span data-stu-id="37910-198">Format-Custom</span></span>](Format-Custom.md)

[<span data-ttu-id="37910-199">Format-Hex</span><span class="sxs-lookup"><span data-stu-id="37910-199">Format-Hex</span></span>](Format-Hex.md)

[<span data-ttu-id="37910-200">Format-List</span><span class="sxs-lookup"><span data-stu-id="37910-200">Format-List</span></span>](Format-List.md)

[<span data-ttu-id="37910-201">Format-Table</span><span class="sxs-lookup"><span data-stu-id="37910-201">Format-Table</span></span>](Format-Table.md)
