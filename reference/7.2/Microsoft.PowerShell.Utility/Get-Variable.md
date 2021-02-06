---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 05/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-variable?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Variable
ms.openlocfilehash: 6cd7a4611f6118ed1f0846d9c11a8fe8edc69ef0
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99601258"
---
# <span data-ttu-id="6c7bb-102">Get-Variable</span><span class="sxs-lookup"><span data-stu-id="6c7bb-102">Get-Variable</span></span>

## <span data-ttu-id="6c7bb-103">개요</span><span class="sxs-lookup"><span data-stu-id="6c7bb-103">SYNOPSIS</span></span>
<span data-ttu-id="6c7bb-104">현재 콘솔에 있는 변수를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="6c7bb-104">Gets the variables in the current console.</span></span>

## <span data-ttu-id="6c7bb-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="6c7bb-105">SYNTAX</span></span>

```
Get-Variable [[-Name] <String[]>] [-ValueOnly] [-Include <String[]>] [-Exclude <String[]>] [-Scope <String>]
 [<CommonParameters>]
```

## <span data-ttu-id="6c7bb-106">설명</span><span class="sxs-lookup"><span data-stu-id="6c7bb-106">DESCRIPTION</span></span>

<span data-ttu-id="6c7bb-107">`Get-Variable`Cmdlet은 현재 콘솔의 PowerShell 변수를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="6c7bb-107">The `Get-Variable` cmdlet gets the PowerShell variables in the current console.</span></span>
<span data-ttu-id="6c7bb-108">**ValueOnly** 매개 변수를 지정하여 변수 값만 검색할 수 있으며 이름을 기준으로 반환되는 변수를 필터링할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c7bb-108">You can retrieve just the values of the variables by specifying the **ValueOnly** parameter, and you can filter the variables returned by name.</span></span>

## <span data-ttu-id="6c7bb-109">예제</span><span class="sxs-lookup"><span data-stu-id="6c7bb-109">EXAMPLES</span></span>

### <span data-ttu-id="6c7bb-110">예제 1: 문자별 변수 가져오기</span><span class="sxs-lookup"><span data-stu-id="6c7bb-110">Example 1: Get variables by letter</span></span>

<span data-ttu-id="6c7bb-111">이 명령은 이름이 m 문자로 시작 하는 변수를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="6c7bb-111">This command gets variables with names that begin with the letter m.</span></span>
<span data-ttu-id="6c7bb-112">변수 값도 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="6c7bb-112">The command also gets the value of the variables.</span></span>

```powershell
Get-Variable m*
```

### <span data-ttu-id="6c7bb-113">예제 2: 문자별로 변수 값 가져오기</span><span class="sxs-lookup"><span data-stu-id="6c7bb-113">Example 2: Get variable values by letter</span></span>

<span data-ttu-id="6c7bb-114">이 명령은 이름이 m으로 시작 하는 변수의 값만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="6c7bb-114">This command gets only the values of the variables that have names that begin with m.</span></span>

```powershell
Get-Variable m* -ValueOnly
```

### <span data-ttu-id="6c7bb-115">예 3: 두 문자로 변수 가져오기</span><span class="sxs-lookup"><span data-stu-id="6c7bb-115">Example 3: Get variables by two letters</span></span>

<span data-ttu-id="6c7bb-116">이 명령은 문자 M 또는 문자 P로 시작 하는 변수에 대 한 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="6c7bb-116">This command gets information about the variables that begin with either the letter M or the letter P.</span></span>

```powershell
Get-Variable -Include M*,P*
```

### <span data-ttu-id="6c7bb-117">예제 4: 범위로 변수 가져오기</span><span class="sxs-lookup"><span data-stu-id="6c7bb-117">Example 4: Get variables by scope</span></span>

<span data-ttu-id="6c7bb-118">첫 번째 명령은 로컬 범위에 정의되어 있는 변수만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="6c7bb-118">The first command gets only the variables that are defined in the local scope.</span></span>
<span data-ttu-id="6c7bb-119">와 같으며로 `Get-Variable -Scope Local` 약식 일 수 있습니다 `gv -s 0` .</span><span class="sxs-lookup"><span data-stu-id="6c7bb-119">It is equivalent to `Get-Variable -Scope Local` and can be abbreviated as `gv -s 0`.</span></span>

<span data-ttu-id="6c7bb-120">두 번째 명령은 cmdlet을 사용 하 여 `Compare-Object` 부모 범위 (범위 1)에 정의 되어 있지만 로컬 범위 (범위 0) 에서만 표시 되는 변수를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="6c7bb-120">The second command uses the `Compare-Object` cmdlet to find the variables that are defined in the parent scope (Scope 1) but are visible only in the local scope (Scope 0).</span></span>

```powershell
Get-Variable -Scope 0
Compare-Object (Get-Variable -Scope 0) (Get-Variable -Scope 1)
```

## <span data-ttu-id="6c7bb-121">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6c7bb-121">PARAMETERS</span></span>

### <span data-ttu-id="6c7bb-122">-제외</span><span class="sxs-lookup"><span data-stu-id="6c7bb-122">-Exclude</span></span>

<span data-ttu-id="6c7bb-123">이 cmdlet이 작업에서 제외 하는 항목의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c7bb-123">Specifies an array of items that this cmdlet excludes from the operation.</span></span>
<span data-ttu-id="6c7bb-124">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c7bb-124">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="6c7bb-125">-포함</span><span class="sxs-lookup"><span data-stu-id="6c7bb-125">-Include</span></span>

<span data-ttu-id="6c7bb-126">다른 모든 항목을 제외 하 고 cmdlet이 동작 하는 항목의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c7bb-126">Specifies an array of items upon which the cmdlet will act, excluding all others.</span></span>
<span data-ttu-id="6c7bb-127">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c7bb-127">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="6c7bb-128">-Name</span><span class="sxs-lookup"><span data-stu-id="6c7bb-128">-Name</span></span>

<span data-ttu-id="6c7bb-129">변수의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6c7bb-129">Specifies the name of the variable.</span></span>
<span data-ttu-id="6c7bb-130">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c7bb-130">Wildcards are permitted.</span></span>
<span data-ttu-id="6c7bb-131">변수 이름을로 파이프 할 수도 있습니다 `Get-Variable` .</span><span class="sxs-lookup"><span data-stu-id="6c7bb-131">You can also pipe a variable name to `Get-Variable`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="6c7bb-132">-범위</span><span class="sxs-lookup"><span data-stu-id="6c7bb-132">-Scope</span></span>

<span data-ttu-id="6c7bb-133">범위에 있는 변수를 지정 합니다. 이 매개 변수에 허용 되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="6c7bb-133">Specifies the variables in the scope.The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="6c7bb-134">**Global**</span><span class="sxs-lookup"><span data-stu-id="6c7bb-134">**Global**</span></span>
- <span data-ttu-id="6c7bb-135">**로컬**</span><span class="sxs-lookup"><span data-stu-id="6c7bb-135">**Local**</span></span>
- <span data-ttu-id="6c7bb-136">**스크립트**</span><span class="sxs-lookup"><span data-stu-id="6c7bb-136">**Script**</span></span>
- <span data-ttu-id="6c7bb-137">현재 범위를 기준으로 하는 숫자 (0부터 범위 수까지, 여기서 0은 현재 범위이 고 1은 부모)</span><span class="sxs-lookup"><span data-stu-id="6c7bb-137">A number relative to the current scope (0 through the number of scopes, where 0 is the current scope and 1 is its parent)</span></span>

<span data-ttu-id="6c7bb-138">**Local** 이 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="6c7bb-138">**Local** is the default.</span></span>
<span data-ttu-id="6c7bb-139">자세한 내용은 [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6c7bb-139">For more information, see [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).</span></span>

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

### <span data-ttu-id="6c7bb-140">-ValueOnly</span><span class="sxs-lookup"><span data-stu-id="6c7bb-140">-ValueOnly</span></span>

<span data-ttu-id="6c7bb-141">이 cmdlet은 변수의 값만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="6c7bb-141">Indicates that this cmdlet gets only the value of the variable.</span></span>

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

### <span data-ttu-id="6c7bb-142">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6c7bb-142">CommonParameters</span></span>

<span data-ttu-id="6c7bb-143">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="6c7bb-143">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6c7bb-144">자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6c7bb-144">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="6c7bb-145">입력</span><span class="sxs-lookup"><span data-stu-id="6c7bb-145">INPUTS</span></span>

### <span data-ttu-id="6c7bb-146">System.String</span><span class="sxs-lookup"><span data-stu-id="6c7bb-146">System.String</span></span>

<span data-ttu-id="6c7bb-147">변수 이름이 포함 된 문자열을로 파이프 할 수 있습니다 `Get-Variable` .</span><span class="sxs-lookup"><span data-stu-id="6c7bb-147">You can pipe a string that contains the variable name to `Get-Variable`.</span></span>

## <span data-ttu-id="6c7bb-148">출력</span><span class="sxs-lookup"><span data-stu-id="6c7bb-148">OUTPUTS</span></span>

### <span data-ttu-id="6c7bb-149">System.object입니다.</span><span class="sxs-lookup"><span data-stu-id="6c7bb-149">System.Management.Automation.PSVariable</span></span>

<span data-ttu-id="6c7bb-150">이 cmdlet은 가져온 각 변수에 대해 **system.object** 를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c7bb-150">This cmdlet returns a **System.Management.AutomationPSVariable** object for each variable that it gets.</span></span> <span data-ttu-id="6c7bb-151">개체 유형은 변수에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="6c7bb-151">The object type depends on the variable.</span></span>

### <span data-ttu-id="6c7bb-152">System.object []</span><span class="sxs-lookup"><span data-stu-id="6c7bb-152">System.Object[]</span></span>

<span data-ttu-id="6c7bb-153">**Valueonly** 매개 변수를 지정 하는 경우 지정 된 변수의 값이 컬렉션인 경우는를 `Get-Variable` 반환 `[System.Object[]]` 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c7bb-153">When you specify the **ValueOnly** parameter, if the specified variable's value is a collection, `Get-Variable` returns a `[System.Object[]]`.</span></span> <span data-ttu-id="6c7bb-154">이 동작은 일반 파이프라인 작업에서 변수의 값을 한 번에 하나씩 처리 하는 것을 방지 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c7bb-154">This behavior prevents normal pipeline operation from processing the variable's values one at a time.</span></span> <span data-ttu-id="6c7bb-155">컬렉션 열거를 강제 적용 하는 방법은 명령을 괄호로 묶는 것입니다 `Get-Variable` .</span><span class="sxs-lookup"><span data-stu-id="6c7bb-155">A workaround to force collection enumeration is to enclose the `Get-Variable` command in parenthesis.</span></span>

## <span data-ttu-id="6c7bb-156">참고</span><span class="sxs-lookup"><span data-stu-id="6c7bb-156">NOTES</span></span>

- <span data-ttu-id="6c7bb-157">이 명령은 환경 변수를 관리하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6c7bb-157">This cmdlet does not manage environment variables.</span></span> <span data-ttu-id="6c7bb-158">환경 변수를 관리하기 위해 환경 변수 공급자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c7bb-158">To manage environment variables, you can use the environment variable provider.</span></span>

## <span data-ttu-id="6c7bb-159">관련 링크</span><span class="sxs-lookup"><span data-stu-id="6c7bb-159">RELATED LINKS</span></span>

[<span data-ttu-id="6c7bb-160">Clear-Variable</span><span class="sxs-lookup"><span data-stu-id="6c7bb-160">Clear-Variable</span></span>](Clear-Variable.md)

[<span data-ttu-id="6c7bb-161">New-Variable</span><span class="sxs-lookup"><span data-stu-id="6c7bb-161">New-Variable</span></span>](New-Variable.md)

[<span data-ttu-id="6c7bb-162">Remove-Variable</span><span class="sxs-lookup"><span data-stu-id="6c7bb-162">Remove-Variable</span></span>](Remove-Variable.md)

[<span data-ttu-id="6c7bb-163">Set-Variable</span><span class="sxs-lookup"><span data-stu-id="6c7bb-163">Set-Variable</span></span>](Set-Variable.md)

