---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 5/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-variable?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Variable
ms.openlocfilehash: f544a33a4d2aa2cabd330ce7cc30c5270eeff897
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93213009"
---
# <span data-ttu-id="8498b-103">Get-Variable</span><span class="sxs-lookup"><span data-stu-id="8498b-103">Get-Variable</span></span>

## <span data-ttu-id="8498b-104">개요</span><span class="sxs-lookup"><span data-stu-id="8498b-104">SYNOPSIS</span></span>
<span data-ttu-id="8498b-105">현재 콘솔에 있는 변수를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8498b-105">Gets the variables in the current console.</span></span>

## <span data-ttu-id="8498b-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="8498b-106">SYNTAX</span></span>

```
Get-Variable [[-Name] <String[]>] [-ValueOnly] [-Include <String[]>] [-Exclude <String[]>] [-Scope <String>]
 [<CommonParameters>]
```

## <span data-ttu-id="8498b-107">설명</span><span class="sxs-lookup"><span data-stu-id="8498b-107">DESCRIPTION</span></span>

<span data-ttu-id="8498b-108">`Get-Variable`Cmdlet은 현재 콘솔의 PowerShell 변수를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8498b-108">The `Get-Variable` cmdlet gets the PowerShell variables in the current console.</span></span>
<span data-ttu-id="8498b-109">**ValueOnly** 매개 변수를 지정하여 변수 값만 검색할 수 있으며 이름을 기준으로 반환되는 변수를 필터링할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8498b-109">You can retrieve just the values of the variables by specifying the **ValueOnly** parameter, and you can filter the variables returned by name.</span></span>

## <span data-ttu-id="8498b-110">예제</span><span class="sxs-lookup"><span data-stu-id="8498b-110">EXAMPLES</span></span>

### <span data-ttu-id="8498b-111">예제 1: 문자별 변수 가져오기</span><span class="sxs-lookup"><span data-stu-id="8498b-111">Example 1: Get variables by letter</span></span>

<span data-ttu-id="8498b-112">이 명령은 이름이 m 문자로 시작 하는 변수를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8498b-112">This command gets variables with names that begin with the letter m.</span></span>
<span data-ttu-id="8498b-113">변수 값도 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8498b-113">The command also gets the value of the variables.</span></span>

```powershell
Get-Variable m*
```

### <span data-ttu-id="8498b-114">예제 2: 문자별로 변수 값 가져오기</span><span class="sxs-lookup"><span data-stu-id="8498b-114">Example 2: Get variable values by letter</span></span>

<span data-ttu-id="8498b-115">이 명령은 이름이 m으로 시작 하는 변수의 값만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8498b-115">This command gets only the values of the variables that have names that begin with m.</span></span>

```powershell
Get-Variable m* -ValueOnly
```

### <span data-ttu-id="8498b-116">예 3: 두 문자로 변수 가져오기</span><span class="sxs-lookup"><span data-stu-id="8498b-116">Example 3: Get variables by two letters</span></span>

<span data-ttu-id="8498b-117">이 명령은 문자 M 또는 문자 P로 시작 하는 변수에 대 한 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8498b-117">This command gets information about the variables that begin with either the letter M or the letter P.</span></span>

```powershell
Get-Variable -Include M*,P*
```

### <span data-ttu-id="8498b-118">예제 4: 범위로 변수 가져오기</span><span class="sxs-lookup"><span data-stu-id="8498b-118">Example 4: Get variables by scope</span></span>

<span data-ttu-id="8498b-119">첫 번째 명령은 로컬 범위에 정의되어 있는 변수만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8498b-119">The first command gets only the variables that are defined in the local scope.</span></span>
<span data-ttu-id="8498b-120">와 같으며로 `Get-Variable -Scope Local` 약식 일 수 있습니다 `gv -s 0` .</span><span class="sxs-lookup"><span data-stu-id="8498b-120">It is equivalent to `Get-Variable -Scope Local` and can be abbreviated as `gv -s 0`.</span></span>

<span data-ttu-id="8498b-121">두 번째 명령은 cmdlet을 사용 하 여 `Compare-Object` 부모 범위 (범위 1)에 정의 되어 있지만 로컬 범위 (범위 0) 에서만 표시 되는 변수를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="8498b-121">The second command uses the `Compare-Object` cmdlet to find the variables that are defined in the parent scope (Scope 1) but are visible only in the local scope (Scope 0).</span></span>

```powershell
Get-Variable -Scope 0
Compare-Object (Get-Variable -Scope 0) (Get-Variable -Scope 1)
```

## <span data-ttu-id="8498b-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="8498b-122">PARAMETERS</span></span>

### <span data-ttu-id="8498b-123">-제외</span><span class="sxs-lookup"><span data-stu-id="8498b-123">-Exclude</span></span>

<span data-ttu-id="8498b-124">이 cmdlet이 작업에서 제외 하는 항목의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8498b-124">Specifies an array of items that this cmdlet excludes from the operation.</span></span>
<span data-ttu-id="8498b-125">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="8498b-125">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="8498b-126">-포함</span><span class="sxs-lookup"><span data-stu-id="8498b-126">-Include</span></span>

<span data-ttu-id="8498b-127">다른 모든 항목을 제외 하 고 cmdlet이 동작 하는 항목의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8498b-127">Specifies an array of items upon which the cmdlet will act, excluding all others.</span></span>
<span data-ttu-id="8498b-128">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="8498b-128">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="8498b-129">-Name</span><span class="sxs-lookup"><span data-stu-id="8498b-129">-Name</span></span>

<span data-ttu-id="8498b-130">변수의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8498b-130">Specifies the name of the variable.</span></span>
<span data-ttu-id="8498b-131">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="8498b-131">Wildcards are permitted.</span></span>
<span data-ttu-id="8498b-132">변수 이름을로 파이프 할 수도 있습니다 `Get-Variable` .</span><span class="sxs-lookup"><span data-stu-id="8498b-132">You can also pipe a variable name to `Get-Variable`.</span></span>

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

### <span data-ttu-id="8498b-133">-범위</span><span class="sxs-lookup"><span data-stu-id="8498b-133">-Scope</span></span>

<span data-ttu-id="8498b-134">범위에 있는 변수를 지정 합니다. 이 매개 변수에 허용 되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8498b-134">Specifies the variables in the scope.The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="8498b-135">**Global**</span><span class="sxs-lookup"><span data-stu-id="8498b-135">**Global**</span></span>
- <span data-ttu-id="8498b-136">**로컬**</span><span class="sxs-lookup"><span data-stu-id="8498b-136">**Local**</span></span>
- <span data-ttu-id="8498b-137">**스크립트**</span><span class="sxs-lookup"><span data-stu-id="8498b-137">**Script**</span></span>
- <span data-ttu-id="8498b-138">현재 범위를 기준으로 하는 숫자 (0부터 범위 수까지, 여기서 0은 현재 범위이 고 1은 부모)</span><span class="sxs-lookup"><span data-stu-id="8498b-138">A number relative to the current scope (0 through the number of scopes, where 0 is the current scope and 1 is its parent)</span></span>

<span data-ttu-id="8498b-139">**Local** 이 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="8498b-139">**Local** is the default.</span></span>
<span data-ttu-id="8498b-140">자세한 내용은 [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8498b-140">For more information, see [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).</span></span>

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

### <span data-ttu-id="8498b-141">-ValueOnly</span><span class="sxs-lookup"><span data-stu-id="8498b-141">-ValueOnly</span></span>

<span data-ttu-id="8498b-142">이 cmdlet은 변수의 값만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8498b-142">Indicates that this cmdlet gets only the value of the variable.</span></span>

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

### <span data-ttu-id="8498b-143">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8498b-143">CommonParameters</span></span>

<span data-ttu-id="8498b-144">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="8498b-144">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8498b-145">자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8498b-145">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="8498b-146">입력</span><span class="sxs-lookup"><span data-stu-id="8498b-146">INPUTS</span></span>

### <span data-ttu-id="8498b-147">System.String</span><span class="sxs-lookup"><span data-stu-id="8498b-147">System.String</span></span>

<span data-ttu-id="8498b-148">변수 이름이 포함 된 문자열을로 파이프 할 수 있습니다 `Get-Variable` .</span><span class="sxs-lookup"><span data-stu-id="8498b-148">You can pipe a string that contains the variable name to `Get-Variable`.</span></span>

## <span data-ttu-id="8498b-149">출력</span><span class="sxs-lookup"><span data-stu-id="8498b-149">OUTPUTS</span></span>

### <span data-ttu-id="8498b-150">System.object입니다.</span><span class="sxs-lookup"><span data-stu-id="8498b-150">System.Management.Automation.PSVariable</span></span>

<span data-ttu-id="8498b-151">이 cmdlet은 가져온 각 변수에 대해 **system.object** 를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="8498b-151">This cmdlet returns a **System.Management.AutomationPSVariable** object for each variable that it gets.</span></span> <span data-ttu-id="8498b-152">개체 유형은 변수에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="8498b-152">The object type depends on the variable.</span></span>

### <span data-ttu-id="8498b-153">System.object []</span><span class="sxs-lookup"><span data-stu-id="8498b-153">System.Object[]</span></span>

<span data-ttu-id="8498b-154">**Valueonly** 매개 변수를 지정 하는 경우 지정 된 변수의 값이 컬렉션인 경우는를 `Get-Variable` 반환 `[System.Object[]]` 합니다.</span><span class="sxs-lookup"><span data-stu-id="8498b-154">When you specify the **ValueOnly** parameter, if the specified variable's value is a collection, `Get-Variable` returns a `[System.Object[]]`.</span></span> <span data-ttu-id="8498b-155">이 동작은 일반 파이프라인 작업에서 변수의 값을 한 번에 하나씩 처리 하는 것을 방지 합니다.</span><span class="sxs-lookup"><span data-stu-id="8498b-155">This behavior prevents normal pipeline operation from processing the variable's values one at a time.</span></span> <span data-ttu-id="8498b-156">컬렉션 열거를 강제 적용 하는 방법은 명령을 괄호로 묶는 것입니다 `Get-Variable` .</span><span class="sxs-lookup"><span data-stu-id="8498b-156">A workaround to force collection enumeration is to enclose the `Get-Variable` command in parenthesis.</span></span>

## <span data-ttu-id="8498b-157">참고</span><span class="sxs-lookup"><span data-stu-id="8498b-157">NOTES</span></span>

- <span data-ttu-id="8498b-158">이 명령은 환경 변수를 관리하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8498b-158">This cmdlet does not manage environment variables.</span></span> <span data-ttu-id="8498b-159">환경 변수를 관리하기 위해 환경 변수 공급자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8498b-159">To manage environment variables, you can use the environment variable provider.</span></span>

## <span data-ttu-id="8498b-160">관련 링크</span><span class="sxs-lookup"><span data-stu-id="8498b-160">RELATED LINKS</span></span>

[<span data-ttu-id="8498b-161">Clear-Variable</span><span class="sxs-lookup"><span data-stu-id="8498b-161">Clear-Variable</span></span>](Clear-Variable.md)

[<span data-ttu-id="8498b-162">New-Variable</span><span class="sxs-lookup"><span data-stu-id="8498b-162">New-Variable</span></span>](New-Variable.md)

[<span data-ttu-id="8498b-163">Remove-Variable</span><span class="sxs-lookup"><span data-stu-id="8498b-163">Remove-Variable</span></span>](Remove-Variable.md)

[<span data-ttu-id="8498b-164">Set-Variable</span><span class="sxs-lookup"><span data-stu-id="8498b-164">Set-Variable</span></span>](Set-Variable.md)

