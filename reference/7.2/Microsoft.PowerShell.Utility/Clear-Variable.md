---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/clear-variable?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-Variable
ms.openlocfilehash: 0381b48097f75d3195a82a67225cd8d6759e7433
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99604989"
---
# <span data-ttu-id="ef568-102">Clear-Variable</span><span class="sxs-lookup"><span data-stu-id="ef568-102">Clear-Variable</span></span>

## <span data-ttu-id="ef568-103">개요</span><span class="sxs-lookup"><span data-stu-id="ef568-103">SYNOPSIS</span></span>
<span data-ttu-id="ef568-104">변수 값을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="ef568-104">Deletes the value of a variable.</span></span>

## <span data-ttu-id="ef568-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ef568-105">SYNTAX</span></span>

```
Clear-Variable [-Name] <String[]> [-Include <String[]>] [-Exclude <String[]>] [-Force] [-PassThru]
 [-Scope <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="ef568-106">설명</span><span class="sxs-lookup"><span data-stu-id="ef568-106">DESCRIPTION</span></span>

<span data-ttu-id="ef568-107">**Clear 변수** cmdlet은 변수에 저장 된 데이터를 삭제 하지만 변수는 삭제 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ef568-107">The **Clear-Variable** cmdlet deletes the data stored in a variable, but it does not delete the variable.</span></span>
<span data-ttu-id="ef568-108">따라서 변수의 값은 NULL(비어 있음)입니다.</span><span class="sxs-lookup"><span data-stu-id="ef568-108">As a result, the value of the variable is NULL (empty).</span></span>
<span data-ttu-id="ef568-109">변수에 지정 된 데이터 또는 개체 형식이 있는 경우이 cmdlet은 변수에 저장 된 개체의 형식을 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef568-109">If the variable has a specified data or object type, this cmdlet preserves the type of the object stored in the variable.</span></span>

## <span data-ttu-id="ef568-110">예제</span><span class="sxs-lookup"><span data-stu-id="ef568-110">EXAMPLES</span></span>

### <span data-ttu-id="ef568-111">예제 1: 검색 문자열로 시작 하는 전역 변수 값 제거</span><span class="sxs-lookup"><span data-stu-id="ef568-111">Example 1: Remove the value of global variables that begin with a search string</span></span>

```
PS C:\> Clear-Variable my* -Scope Global
```

<span data-ttu-id="ef568-112">이 명령은 이름이 my로 시작 하는 전역 변수의 값을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef568-112">This command removes the value of global variables that have names that begin with my.</span></span>

### <span data-ttu-id="ef568-113">예 2: 자식 범위에서 변수를 지우고 부모 범위는 해제</span><span class="sxs-lookup"><span data-stu-id="ef568-113">Example 2: Clear a variable in a child scope but not the parent scope</span></span>

```
PS C:\> $a=3
PS C:\> &{ Clear-Variable a }
PS C:\> $a
3
```

<span data-ttu-id="ef568-114">이 명령은 하위 범위의 변수를 삭제해도 상위 범위의 값이 삭제되지 않음을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ef568-114">These commands demonstrate that clearing a variable in a child scope does not clear the value in the parent scope.</span></span>
<span data-ttu-id="ef568-115">첫 번째 명령은 $A 변수의 값을 3으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef568-115">The first command sets the value of the variable $A to 3.</span></span>
<span data-ttu-id="ef568-116">두 번째 명령은 invoke 연산자 (&)를 사용 하 여 새 범위에서 **Clear Variable** 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef568-116">The second command uses the invoke operator (&) to run the **Clear-Variable** command in a new scope.</span></span>
<span data-ttu-id="ef568-117">하위 범위에서는 변수가 지워지지만 로컬 범위에서는 지워지지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ef568-117">The variable is cleared in the child scope (although it did not exist), but it is not cleared in the local scope.</span></span>
<span data-ttu-id="ef568-118">$A 값을 가져오는 세 번째 명령은 값 3이 영향을 받지 않았음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ef568-118">The third command, which gets the value of $A, shows that the value 3 is unaffected.</span></span>

### <span data-ttu-id="ef568-119">예 3: 지정 된 변수의 값을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef568-119">Example 3: Delete the value of the specified variable</span></span>

```
PS C:\> Clear-Variable -Name "Processes"
```

<span data-ttu-id="ef568-120">이 명령은 명명 된 프로세스 변수의 값을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef568-120">This command deletes the value of the variable named Processes.</span></span>
<span data-ttu-id="ef568-121">Cmdlet이 작업을 완료 한 후에는 명명 된 프로세스 변수가 여전히 존재 하지만 값은 null입니다.</span><span class="sxs-lookup"><span data-stu-id="ef568-121">After the cmdlet completes the operation, the variable named Processes still exists, but the value is null.</span></span>

## <span data-ttu-id="ef568-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ef568-122">PARAMETERS</span></span>

### <span data-ttu-id="ef568-123">-제외</span><span class="sxs-lookup"><span data-stu-id="ef568-123">-Exclude</span></span>

<span data-ttu-id="ef568-124">이 cmdlet이 작업에서 생략 하는 항목의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef568-124">Specifies an array of items that this cmdlet omits in the operation.</span></span>
<span data-ttu-id="ef568-125">이 매개 변수 값은 *Name* 매개 변수를 한정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef568-125">The value of this parameter qualifies the *Name* parameter.</span></span>
<span data-ttu-id="ef568-126">이름 요소 또는 패턴(예: "*s*")을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ef568-126">Enter a name element or pattern, such as "s\*".</span></span>
<span data-ttu-id="ef568-127">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef568-127">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="ef568-128">-Force</span><span class="sxs-lookup"><span data-stu-id="ef568-128">-Force</span></span>

<span data-ttu-id="ef568-129">변수가 읽기 전용인 경우에도 cmdlet이 해당 변수를 지울 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef568-129">Allows the cmdlet to clear a variable even if it is read-only.</span></span>
<span data-ttu-id="ef568-130">Force 매개 변수를 사용해도 cmdlet은 상수를 지울 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ef568-130">Even using the Force parameter, the cmdlet cannot clear constants.</span></span>

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

### <span data-ttu-id="ef568-131">-포함</span><span class="sxs-lookup"><span data-stu-id="ef568-131">-Include</span></span>

<span data-ttu-id="ef568-132">이 cmdlet이 작업에 포함 하는 항목의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef568-132">Specifies an array of items that this cmdlet includes in the operation.</span></span>
<span data-ttu-id="ef568-133">이 매개 변수 값은 *Name* 매개 변수를 한정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef568-133">The value of this parameter qualifies the *Name* parameter.</span></span>
<span data-ttu-id="ef568-134">이름 요소 또는 패턴(예: "*s*")을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ef568-134">Enter a name element or pattern, such as "s\*".</span></span>
<span data-ttu-id="ef568-135">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef568-135">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="ef568-136">-Name</span><span class="sxs-lookup"><span data-stu-id="ef568-136">-Name</span></span>

<span data-ttu-id="ef568-137">지울 변수의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ef568-137">Specifies the name of the variable to be cleared.</span></span>
<span data-ttu-id="ef568-138">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef568-138">Wildcards are permitted.</span></span>
<span data-ttu-id="ef568-139">이 매개 변수는 필수이지만 매개 변수 이름("Name")은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="ef568-139">This parameter is required, but the parameter name ("Name") is optional.</span></span>

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

### <span data-ttu-id="ef568-140">-PassThru</span><span class="sxs-lookup"><span data-stu-id="ef568-140">-PassThru</span></span>

<span data-ttu-id="ef568-141">작업 중인 항목을 나타내는 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="ef568-141">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="ef568-142">기본적으로 이 cmdlet은 출력을 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ef568-142">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="ef568-143">-범위</span><span class="sxs-lookup"><span data-stu-id="ef568-143">-Scope</span></span>

<span data-ttu-id="ef568-144">이 별칭이 유효한 범위를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ef568-144">Specifies the scope in which this alias is valid.</span></span>

<span data-ttu-id="ef568-145">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ef568-145">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="ef568-146">전역</span><span class="sxs-lookup"><span data-stu-id="ef568-146">Global</span></span>
- <span data-ttu-id="ef568-147">로컬</span><span class="sxs-lookup"><span data-stu-id="ef568-147">Local</span></span>
- <span data-ttu-id="ef568-148">스크립트</span><span class="sxs-lookup"><span data-stu-id="ef568-148">Script</span></span>

<span data-ttu-id="ef568-149">현재 범위 (0부터 범위 수까지, 여기서 0은 현재 범위이 고 1은 부모)를 기준으로 하는 숫자를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef568-149">You can also use a number relative to the current scope (0 through the number of scopes, where 0 is the current scope and 1 is its parent).</span></span>
<span data-ttu-id="ef568-150">Local이 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="ef568-150">Local is the default.</span></span>
<span data-ttu-id="ef568-151">자세한 내용은 about_Scopes를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ef568-151">For more information, see about_Scopes.</span></span>

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

### <span data-ttu-id="ef568-152">-Confirm</span><span class="sxs-lookup"><span data-stu-id="ef568-152">-Confirm</span></span>

<span data-ttu-id="ef568-153">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="ef568-153">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="ef568-154">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="ef568-154">-WhatIf</span></span>

<span data-ttu-id="ef568-155">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ef568-155">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="ef568-156">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ef568-156">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="ef568-157">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ef568-157">CommonParameters</span></span>

<span data-ttu-id="ef568-158">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ef568-158">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ef568-159">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ef568-159">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ef568-160">입력</span><span class="sxs-lookup"><span data-stu-id="ef568-160">INPUTS</span></span>

### <span data-ttu-id="ef568-161">없음</span><span class="sxs-lookup"><span data-stu-id="ef568-161">None</span></span>

<span data-ttu-id="ef568-162">이 cmdlet에 개체를 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ef568-162">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="ef568-163">출력</span><span class="sxs-lookup"><span data-stu-id="ef568-163">OUTPUTS</span></span>

### <span data-ttu-id="ef568-164">None 또는 System.object입니다.</span><span class="sxs-lookup"><span data-stu-id="ef568-164">None or System.Management.Automation.PSVariable</span></span>

<span data-ttu-id="ef568-165">*PassThru* 매개 변수를 사용 하는 경우이 cmdlet은 지워진 변수를 나타내는 **system.object** 를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef568-165">When you use the *PassThru* parameter, this cmdlet generates a **System.Management.Automation.PSVariable** object representing the cleared variable.</span></span>
<span data-ttu-id="ef568-166">그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ef568-166">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="ef568-167">참고</span><span class="sxs-lookup"><span data-stu-id="ef568-167">NOTES</span></span>

* <span data-ttu-id="ef568-168">변수와 변수 값을 함께 삭제하려면 Remove-Variable 또는 Remove-Item을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ef568-168">To delete a variable, along with its value, use Remove-Variable or Remove-Item.</span></span>

  <span data-ttu-id="ef568-169">이 cmdlet은 *Force* 매개 변수를 사용 하는 경우에도 상수로 설정 되거나 시스템에서 소유 하는 변수의 값을 삭제 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ef568-169">This cmdlet does not delete the values of variables that are set as constants or owned by the system, even if you use the *Force* parameter.</span></span>

  <span data-ttu-id="ef568-170">삭제하려는 변수가 없는 경우 cmdlet의 영향을 받지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ef568-170">If the variable that you are clearing does not exist, the cmdlet has no effect.</span></span>
<span data-ttu-id="ef568-171">값이 Null인 변수는 만들지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ef568-171">It does not create a variable with a null value.</span></span>

  <span data-ttu-id="ef568-172">기본 제공 별칭인 clv로 **Clear 변수** 를 참조할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef568-172">You can also refer to **Clear-Variable** by its built-in alias, clv.</span></span>
<span data-ttu-id="ef568-173">자세한 내용은 about_Aliases를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ef568-173">For more information, see about_Aliases.</span></span>

*

## <span data-ttu-id="ef568-174">관련 링크</span><span class="sxs-lookup"><span data-stu-id="ef568-174">RELATED LINKS</span></span>

[<span data-ttu-id="ef568-175">Get-Variable</span><span class="sxs-lookup"><span data-stu-id="ef568-175">Get-Variable</span></span>](Get-Variable.md)

[<span data-ttu-id="ef568-176">New-Variable</span><span class="sxs-lookup"><span data-stu-id="ef568-176">New-Variable</span></span>](New-Variable.md)

[<span data-ttu-id="ef568-177">Remove-Variable</span><span class="sxs-lookup"><span data-stu-id="ef568-177">Remove-Variable</span></span>](Remove-Variable.md)

[<span data-ttu-id="ef568-178">Set-Variable</span><span class="sxs-lookup"><span data-stu-id="ef568-178">Set-Variable</span></span>](Set-Variable.md)

