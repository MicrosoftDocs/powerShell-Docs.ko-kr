---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 07/21/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/remove-variable?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Variable
ms.openlocfilehash: 2e0e9388c592cb83dd7609fed663ae220e380750
ms.sourcegitcommit: 84fcc90bd018ab76ac4e964d53e7c9c2b5a7b6c6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/23/2020
ms.locfileid: "93218890"
---
# <span data-ttu-id="bb690-103">Remove-Variable</span><span class="sxs-lookup"><span data-stu-id="bb690-103">Remove-Variable</span></span>

## <span data-ttu-id="bb690-104">개요</span><span class="sxs-lookup"><span data-stu-id="bb690-104">SYNOPSIS</span></span>
<span data-ttu-id="bb690-105">변수와 그 값을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="bb690-105">Deletes a variable and its value.</span></span>

## <span data-ttu-id="bb690-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="bb690-106">SYNTAX</span></span>

```
Remove-Variable [-Name] <String[]> [-Include <String[]>] [-Exclude <String[]>] [-Force] [-Scope <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="bb690-107">설명</span><span class="sxs-lookup"><span data-stu-id="bb690-107">DESCRIPTION</span></span>

<span data-ttu-id="bb690-108">`Remove-Variable`Cmdlet은 변수가 정의 된 범위 (예: 현재 세션)에서 변수와 그 값을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb690-108">The `Remove-Variable` cmdlet deletes a variable and its value from the scope in which it is defined, such as the current session.</span></span> <span data-ttu-id="bb690-109">이 cmdlet을 사용하여 상수로 설정된 변수나 시스템에서 소유한 변수를 삭제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bb690-109">You cannot use this cmdlet to delete variables that are set as constants or those that are owned by the system.</span></span>

## <span data-ttu-id="bb690-110">예제</span><span class="sxs-lookup"><span data-stu-id="bb690-110">EXAMPLES</span></span>

### <span data-ttu-id="bb690-111">예제 1: 변수 제거</span><span class="sxs-lookup"><span data-stu-id="bb690-111">Example 1: Remove a variable</span></span>

```powershell
Remove-Variable Smp
```

<span data-ttu-id="bb690-112">이 명령은 변수를 삭제 `$Smp` 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb690-112">This command deletes the `$Smp` variable.</span></span>

## <span data-ttu-id="bb690-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="bb690-113">PARAMETERS</span></span>

### <span data-ttu-id="bb690-114">-제외</span><span class="sxs-lookup"><span data-stu-id="bb690-114">-Exclude</span></span>

<span data-ttu-id="bb690-115">이 cmdlet이 작업에서 생략 하는 항목의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb690-115">Specifies an array of items that this cmdlet omits from the operation.</span></span> <span data-ttu-id="bb690-116">이 매개 변수 값은 **Name** 매개 변수를 한정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb690-116">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="bb690-117">이름 요소 또는 패턴(예: "*s*")을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="bb690-117">Enter a name element or pattern, such as "s\*".</span></span> <span data-ttu-id="bb690-118">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="bb690-118">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="bb690-119">-Force</span><span class="sxs-lookup"><span data-stu-id="bb690-119">-Force</span></span>

<span data-ttu-id="bb690-120">변수가 읽기 전용인 경우에도 cmdlet이 해당 변수를 제거 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="bb690-120">Indicates that the cmdlet removes a variable even if it is read-only.</span></span> <span data-ttu-id="bb690-121">**Force** 매개 변수를 사용 해도 cmdlet은 상수를 제거할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bb690-121">Even using the **Force** parameter, the cmdlet cannot remove a constant.</span></span>

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

### <span data-ttu-id="bb690-122">-포함</span><span class="sxs-lookup"><span data-stu-id="bb690-122">-Include</span></span>

<span data-ttu-id="bb690-123">작업에서이 cmdlet이 삭제 하는 항목의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb690-123">Specifies an array of items that this cmdlet deletes in the operation.</span></span> <span data-ttu-id="bb690-124">이 매개 변수 값은 **Name** 매개 변수를 한정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb690-124">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="bb690-125">이름 요소 또는 패턴 (예: s \*)을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb690-125">Enter a name element or pattern, such as s\*.</span></span> <span data-ttu-id="bb690-126">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="bb690-126">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="bb690-127">-Name</span><span class="sxs-lookup"><span data-stu-id="bb690-127">-Name</span></span>

<span data-ttu-id="bb690-128">제거할 변수의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bb690-128">Specifies the name of the variable to be removed.</span></span> <span data-ttu-id="bb690-129">매개 변수 이름 ( **name** )은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="bb690-129">The parameter name ( **Name** ) is optional.</span></span>
<span data-ttu-id="bb690-130">와일드 카드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb690-130">Wildcards are permitted</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="bb690-131">-범위</span><span class="sxs-lookup"><span data-stu-id="bb690-131">-Scope</span></span>

<span data-ttu-id="bb690-132">지정한 범위의 변수만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="bb690-132">Gets only the variables in the specified scope.</span></span> <span data-ttu-id="bb690-133">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="bb690-133">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="bb690-134">전역</span><span class="sxs-lookup"><span data-stu-id="bb690-134">Global</span></span>
- <span data-ttu-id="bb690-135">로컬</span><span class="sxs-lookup"><span data-stu-id="bb690-135">Local</span></span>
- <span data-ttu-id="bb690-136">스크립트</span><span class="sxs-lookup"><span data-stu-id="bb690-136">Script</span></span>
- <span data-ttu-id="bb690-137">현재 범위를 기준으로 하는 숫자 (0부터 범위 수까지, 여기서 0은 현재 범위이 고 1은 부모)</span><span class="sxs-lookup"><span data-stu-id="bb690-137">A number relative to the current scope (0 through the number of scopes, where 0 is the current scope and 1 is its parent)</span></span>

<span data-ttu-id="bb690-138">Local이 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="bb690-138">Local is the default.</span></span> <span data-ttu-id="bb690-139">자세한 내용은 [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bb690-139">For more information, see [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).</span></span>

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

### <span data-ttu-id="bb690-140">-Confirm</span><span class="sxs-lookup"><span data-stu-id="bb690-140">-Confirm</span></span>

<span data-ttu-id="bb690-141">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="bb690-141">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bb690-142">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="bb690-142">-WhatIf</span></span>

<span data-ttu-id="bb690-143">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="bb690-143">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="bb690-144">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bb690-144">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bb690-145">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="bb690-145">CommonParameters</span></span>

<span data-ttu-id="bb690-146">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="bb690-146">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="bb690-147">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bb690-147">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="bb690-148">입력</span><span class="sxs-lookup"><span data-stu-id="bb690-148">INPUTS</span></span>

### <span data-ttu-id="bb690-149">System.object입니다.</span><span class="sxs-lookup"><span data-stu-id="bb690-149">System.Management.Automation.PSVariable</span></span>

<span data-ttu-id="bb690-150">변수 개체를로 파이프 할 수 있습니다 `Remove-Variable` .</span><span class="sxs-lookup"><span data-stu-id="bb690-150">You can pipe a variable object to `Remove-Variable`.</span></span>

## <span data-ttu-id="bb690-151">출력</span><span class="sxs-lookup"><span data-stu-id="bb690-151">OUTPUTS</span></span>

### <span data-ttu-id="bb690-152">없음</span><span class="sxs-lookup"><span data-stu-id="bb690-152">None</span></span>

<span data-ttu-id="bb690-153">이 cmdlet은 어떠한 출력도 반환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bb690-153">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="bb690-154">참고</span><span class="sxs-lookup"><span data-stu-id="bb690-154">NOTES</span></span>

- <span data-ttu-id="bb690-155">변경 내용은 세션과 같은 현재 범위에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="bb690-155">Changes affect only the current scope, such as a session.</span></span> <span data-ttu-id="bb690-156">모든 세션에서 변수를 삭제 하려면 `Remove-Variable` PowerShell 프로필에 명령을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb690-156">To delete a variable from all sessions, add a `Remove-Variable` command to your PowerShell profile.</span></span>

- <span data-ttu-id="bb690-157">의 기본 제공 별칭인를 참조할 수도 있습니다 `Remove-Variable` `rv` .</span><span class="sxs-lookup"><span data-stu-id="bb690-157">You can also refer to `Remove-Variable` by its built-in alias, `rv`.</span></span> <span data-ttu-id="bb690-158">자세한 내용은 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bb690-158">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

## <span data-ttu-id="bb690-159">관련 링크</span><span class="sxs-lookup"><span data-stu-id="bb690-159">RELATED LINKS</span></span>

[<span data-ttu-id="bb690-160">Clear-Variable</span><span class="sxs-lookup"><span data-stu-id="bb690-160">Clear-Variable</span></span>](Clear-Variable.md)

[<span data-ttu-id="bb690-161">Get-Variable</span><span class="sxs-lookup"><span data-stu-id="bb690-161">Get-Variable</span></span>](Get-Variable.md)

[<span data-ttu-id="bb690-162">New-Variable</span><span class="sxs-lookup"><span data-stu-id="bb690-162">New-Variable</span></span>](New-Variable.md)

[<span data-ttu-id="bb690-163">Set-Variable</span><span class="sxs-lookup"><span data-stu-id="bb690-163">Set-Variable</span></span>](Set-Variable.md)
