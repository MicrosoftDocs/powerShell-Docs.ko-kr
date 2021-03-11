---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/10/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/set-strictmode?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-StrictMode
ms.openlocfilehash: 007c2cd044ac91a29b40f5a49e84482d7523d3ca
ms.sourcegitcommit: 925819a5ad5799650c14944bd3e50fb309a7e6c4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/11/2021
ms.locfileid: "102771463"
---
# <span data-ttu-id="f853c-102">Set-StrictMode</span><span class="sxs-lookup"><span data-stu-id="f853c-102">Set-StrictMode</span></span>

## <span data-ttu-id="f853c-103">개요</span><span class="sxs-lookup"><span data-stu-id="f853c-103">SYNOPSIS</span></span>
<span data-ttu-id="f853c-104">식, 스크립트 및 스크립트 블록에서 코딩 규칙을 설정하고 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="f853c-104">Establishes and enforces coding rules in expressions, scripts, and script blocks.</span></span>

## <span data-ttu-id="f853c-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f853c-105">SYNTAX</span></span>

### <span data-ttu-id="f853c-106">Version (기본값)</span><span class="sxs-lookup"><span data-stu-id="f853c-106">Version (Default)</span></span>

```
Set-StrictMode -Version <Version> [<CommonParameters>]
```

### <span data-ttu-id="f853c-107">끄기</span><span class="sxs-lookup"><span data-stu-id="f853c-107">Off</span></span>

```
Set-StrictMode [-Off] [<CommonParameters>]
```

## <span data-ttu-id="f853c-108">설명</span><span class="sxs-lookup"><span data-stu-id="f853c-108">DESCRIPTION</span></span>

<span data-ttu-id="f853c-109">`Set-StrictMode`Cmdlet은 현재 범위와 모든 자식 범위에 대해 strict 모드를 구성 하 고 설정 및 해제 합니다.</span><span class="sxs-lookup"><span data-stu-id="f853c-109">The `Set-StrictMode` cmdlet configures strict mode for the current scope and all child scopes, and turns it on and off.</span></span> <span data-ttu-id="f853c-110">Strict 모드가 on 인 경우 식, 스크립트 또는 스크립트 블록의 내용이 기본 모범 사례 코딩 규칙을 위반 하면 PowerShell에서 종료 오류를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="f853c-110">When strict mode is on, PowerShell generates a terminating error when the content of an expression, script, or script block violates basic best-practice coding rules.</span></span>

<span data-ttu-id="f853c-111">**Version** 매개 변수를 사용 하 여 적용 되는 코딩 규칙을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f853c-111">Use the **Version** parameter to determine which coding rules are enforced.</span></span>

<span data-ttu-id="f853c-112">`Set-PSDebug -Strict` cmdlet은 전역 범위에 대해 strict 모드를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f853c-112">`Set-PSDebug -Strict` cmdlet turns on strict mode for the global scope.</span></span> <span data-ttu-id="f853c-113">`Set-StrictMode` 현재 범위와 해당 하위 범위에만 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f853c-113">`Set-StrictMode` affects only the current scope and its child scopes.</span></span> <span data-ttu-id="f853c-114">따라서 스크립트나 함수에서이 함수를 사용 하 여 전역 범위에서 상속 된 설정을 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f853c-114">Therefore, you can use it in a script or function to override the setting inherited from the global scope.</span></span>

<span data-ttu-id="f853c-115">`Set-StrictMode`가 off 인 경우 PowerShell은 다음과 같은 동작을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="f853c-115">When `Set-StrictMode` is off, PowerShell has the following behaviors:</span></span>

- <span data-ttu-id="f853c-116">초기화 되지 않은 변수는 `$Null` 형식에 따라 0 또는 값을 갖는 것으로 간주 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f853c-116">Uninitialized variables are assumed to have a value of 0 (zero) or `$Null`, depending on type</span></span>
- <span data-ttu-id="f853c-117">존재 하지 않는 속성에 대 한 참조가 반환 됩니다. `$Null`</span><span class="sxs-lookup"><span data-stu-id="f853c-117">References to non-existent properties return `$Null`</span></span>
- <span data-ttu-id="f853c-118">잘못 된 함수 구문의 결과는 오류 조건에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="f853c-118">Results of improper function syntax vary with the error conditions</span></span>
- <span data-ttu-id="f853c-119">배열의 잘못 된 인덱스를 사용 하 여 값을 검색 하려고 하면이 반환 됩니다. `$Null`</span><span class="sxs-lookup"><span data-stu-id="f853c-119">Attempting to retrieve a value using an invalid index in an array returns `$Null`</span></span>

## <span data-ttu-id="f853c-120">예제</span><span class="sxs-lookup"><span data-stu-id="f853c-120">EXAMPLES</span></span>

### <span data-ttu-id="f853c-121">예제 1: strict 모드를 버전 1.0로 설정</span><span class="sxs-lookup"><span data-stu-id="f853c-121">Example 1: Turn on strict mode as version 1.0</span></span>

```powershell
# Strict mode is off by default.
$a -gt 5
```

```Output
False
```

```powershell
Set-StrictMode -Version 1.0
$a -gt 5
```

```Output
InvalidOperation: The variable '$a' cannot be retrieved because it has not been set.
```

<span data-ttu-id="f853c-122">Strict 모드를 버전 1.0로 설정 하면 초기화 되지 않은 변수를 참조 하려는 시도가 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="f853c-122">With strict mode set to version 1.0, attempts to reference variables that are not initialized fail.</span></span>

### <span data-ttu-id="f853c-123">예제 2: strict 모드를 버전 2.0로 설정</span><span class="sxs-lookup"><span data-stu-id="f853c-123">Example 2: Turn on strict mode as version 2.0</span></span>

```powershell
# Strict mode is off by default.
function add ($a, $b) {
    '$a = ' + $a
    '$b = ' + $b
    '$a+$b = ' + ($a + $b)
}
add 3 4
```

```Output
$a = 3
$b = 4
$a+$b = 7
```

```powershell
add(3,4)
```

```Output
$a = 3 4
$b =
$a+$b = 3 4
```

```powershell
Set-StrictMode -Version 2.0
add(3,4)
```

```Output
InvalidOperation: The function or command was called as if it were a method. Parameters should be separated by spaces. For information about parameters, see the about_Parameters Help topic.
```

```powershell
Set-StrictMode -Off
$string = "This is a string."
$null -eq $string.Month
```

```Output
True
```

```powershell
Set-StrictMode -Version 2.0
$string = "This is a string."
$null -eq $string.Month
```

```Output
PropertyNotFoundException: The property 'Month' cannot be found on this object. Verify that the property exists.
```

<span data-ttu-id="f853c-124">이 명령은 strict 모드를 켜고 버전 2.0으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f853c-124">This command turns strict mode on and sets it to version 2.0.</span></span> <span data-ttu-id="f853c-125">따라서 함수 호출에 대해 괄호와 쉼표를 사용 하는 메서드 구문을 사용 하거나 초기화 되지 않은 변수나 존재 하지 않는 속성을 참조 하는 경우 PowerShell에서 오류를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="f853c-125">As a result, PowerShell returns an error if you use method syntax, which uses parentheses and commas, for a function call or reference uninitialized variables or non-existent properties.</span></span>

<span data-ttu-id="f853c-126">샘플 출력은 버전 2.0 strict 모드의 결과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f853c-126">The sample output shows the effect of version 2.0 strict mode.</span></span>

<span data-ttu-id="f853c-127">버전 2.0 strict 모드를 사용하지 않으면 "(3,4)" 값은 아무것도 추가되지 않은 단일 배열 개체로 해석됩니다.</span><span class="sxs-lookup"><span data-stu-id="f853c-127">Without version 2.0 strict mode, the "(3,4)" value is interpreted as a single array object to which nothing is added.</span></span> <span data-ttu-id="f853c-128">버전 2.0 strict 모드를 사용 하면 두 값을 제출 하는 잘못 된 구문으로 올바르게 해석 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f853c-128">By using version 2.0 strict mode, it is correctly interpreted as faulty syntax for submitting two values.</span></span>

<span data-ttu-id="f853c-129">버전 2.0을 사용 하지 않으면 문자열의 존재 하지 않는 **Month** 속성에 대 한 참조는만 반환 `$Null` 합니다.</span><span class="sxs-lookup"><span data-stu-id="f853c-129">Without version 2.0, the reference to the non-existent **Month** property of a string returns only `$Null`.</span></span> <span data-ttu-id="f853c-130">버전 2.0을 사용 하면 참조 오류로 올바르게 해석 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f853c-130">By using version 2.0, it is interpreted correctly as a reference error.</span></span>

### <span data-ttu-id="f853c-131">예제 3: strict 모드를 버전 3.0로 설정</span><span class="sxs-lookup"><span data-stu-id="f853c-131">Example 3: Turn on strict mode as version 3.0</span></span>

<span data-ttu-id="f853c-132">Strict 모드가 **Off** 로 설정 된 경우 범위를 벗어난 인덱스 결과는 null 값을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="f853c-132">With strict mode set to **Off**, invalid or out of bounds indexes result return null values.</span></span>

```powershell
# Strict mode is off by default.
$a = @(1)
$null -eq $a[2]
$null -eq $a['abc']
```

```Output
True
True
```

```powershell
Set-StrictMode -Version 3
$a = @(1)
$null -eq $a[2]
$null -eq $a['abc']
```

```Output
OperationStopped: Index was outside the bounds of the array.

InvalidArgument: Cannot convert value "abc" to type "System.Int32". Error: "Input string was not in a correct format."
```

<span data-ttu-id="f853c-133">Strict 모드가 버전 3 이상으로 설정 되 면 범위를 잘못 되었거나 범위를 벗어난 인덱스에서 오류가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="f853c-133">With strict mode set to version 3 or higher, invalid or out of bounds indexes result in errors.</span></span>

## <span data-ttu-id="f853c-134">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f853c-134">PARAMETERS</span></span>

### <span data-ttu-id="f853c-135">-꺼짐</span><span class="sxs-lookup"><span data-stu-id="f853c-135">-Off</span></span>

<span data-ttu-id="f853c-136">이 cmdlet이 현재 범위와 모든 자식 범위에 대해 strict 모드를 해제 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f853c-136">Indicates that this cmdlet turns strict mode off for the current scope and all child scopes.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Off
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f853c-137">-Version</span><span class="sxs-lookup"><span data-stu-id="f853c-137">-Version</span></span>

<span data-ttu-id="f853c-138">strict 모드에서 오류를 발생시키는 조건을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f853c-138">Specifies the conditions that cause an error in strict mode.</span></span> <span data-ttu-id="f853c-139">이 매개 변수는 유효한 PowerShell 버전 번호를 모두 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f853c-139">This parameter accepts any valid PowerShell version number.</span></span> <span data-ttu-id="f853c-140">3 보다 큰 숫자는 모두 **최신** 으로 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f853c-140">Any number higher than 3 is treated as **Latest**.</span></span>

<span data-ttu-id="f853c-141">이 매개 변수에 유효한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f853c-141">The effective values for this parameter are:</span></span>

- <span data-ttu-id="f853c-142">1.0</span><span class="sxs-lookup"><span data-stu-id="f853c-142">1.0</span></span>
  - <span data-ttu-id="f853c-143">문자열에서 초기화 되지 않은 변수를 제외 하 고 초기화 되지 않은 변수에 대 한 참조를 금지 합니다.</span><span class="sxs-lookup"><span data-stu-id="f853c-143">Prohibits references to uninitialized variables, except for uninitialized variables in strings.</span></span>
- <span data-ttu-id="f853c-144">2.0</span><span class="sxs-lookup"><span data-stu-id="f853c-144">2.0</span></span>
  - <span data-ttu-id="f853c-145">초기화 되지 않은 변수에 대 한 참조를 금지 합니다.</span><span class="sxs-lookup"><span data-stu-id="f853c-145">Prohibits references to uninitialized variables.</span></span> <span data-ttu-id="f853c-146">여기에는 문자열에 초기화 되지 않은 변수가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f853c-146">This includes uninitialized variables in strings.</span></span>
  - <span data-ttu-id="f853c-147">개체의 존재 하지 않는 속성에 대 한 참조를 금지 합니다.</span><span class="sxs-lookup"><span data-stu-id="f853c-147">Prohibits references to non-existent properties of an object.</span></span>
  - <span data-ttu-id="f853c-148">메서드를 호출 하는 구문을 사용 하는 함수 호출을 금지 합니다.</span><span class="sxs-lookup"><span data-stu-id="f853c-148">Prohibits function calls that use the syntax for calling methods.</span></span>
- <span data-ttu-id="f853c-149">3.0</span><span class="sxs-lookup"><span data-stu-id="f853c-149">3.0</span></span>
  - <span data-ttu-id="f853c-150">초기화 되지 않은 변수에 대 한 참조를 금지 합니다.</span><span class="sxs-lookup"><span data-stu-id="f853c-150">Prohibits references to uninitialized variables.</span></span> <span data-ttu-id="f853c-151">여기에는 문자열에 초기화 되지 않은 변수가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f853c-151">This includes uninitialized variables in strings.</span></span>
  - <span data-ttu-id="f853c-152">개체의 존재 하지 않는 속성에 대 한 참조를 금지 합니다.</span><span class="sxs-lookup"><span data-stu-id="f853c-152">Prohibits references to non-existent properties of an object.</span></span>
  - <span data-ttu-id="f853c-153">메서드를 호출 하는 구문을 사용 하는 함수 호출을 금지 합니다.</span><span class="sxs-lookup"><span data-stu-id="f853c-153">Prohibits function calls that use the syntax for calling methods.</span></span>
  - <span data-ttu-id="f853c-154">범위를 벗어났거나 확인할 수가 없는 배열 인덱스를 금지 합니다.</span><span class="sxs-lookup"><span data-stu-id="f853c-154">Prohibit out of bounds or unresolvable array indexes.</span></span>
- <span data-ttu-id="f853c-155">가장 늦은 날짜</span><span class="sxs-lookup"><span data-stu-id="f853c-155">Latest</span></span>
  - <span data-ttu-id="f853c-156">사용 가능한 최신 버전을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f853c-156">Selects the latest version available.</span></span> <span data-ttu-id="f853c-157">최신 버전은 가장 엄격 합니다.</span><span class="sxs-lookup"><span data-stu-id="f853c-157">The latest version is the most strict.</span></span> <span data-ttu-id="f853c-158">새 버전이 PowerShell에 추가 되는 경우에도 스크립트에서 사용 가능한 가장 엄격한 버전을 사용 하는지 확인 하려면이 값을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f853c-158">Use this value to make sure that scripts use the strictest available version, even when new versions are added to PowerShell.</span></span>

> [!CAUTION]
> <span data-ttu-id="f853c-159">스크립트에서 **최신** **버전** 을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f853c-159">Using a **Version** of **Latest** in scripts.</span></span> <span data-ttu-id="f853c-160">**최신** 의 의미는 PowerShell의 새 릴리스에서 변경 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f853c-160">The meaning of **Latest** can change in new releases of PowerShell.</span></span> <span data-ttu-id="f853c-161">따라서를 사용 하는 이전 버전의 PowerShell 용으로 작성 된 스크립트는 `Set-StrictMode -Version Latest` 최신 버전의 powershell에서 실행 될 때 더 제한적인 규칙이 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f853c-161">Therefore, a script written for an older version of PowerShell that uses `Set-StrictMode -Version Latest` is subject to more restrictive rules when run in a newer version of PowerShell.</span></span>

```yaml
Type: System.Version
Parameter Sets: Version
Aliases: v

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f853c-162">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f853c-162">CommonParameters</span></span>

<span data-ttu-id="f853c-163">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f853c-163">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f853c-164">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f853c-164">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f853c-165">입력</span><span class="sxs-lookup"><span data-stu-id="f853c-165">INPUTS</span></span>

### <span data-ttu-id="f853c-166">없음</span><span class="sxs-lookup"><span data-stu-id="f853c-166">None</span></span>

<span data-ttu-id="f853c-167">이 cmdlet에 입력을 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f853c-167">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="f853c-168">출력</span><span class="sxs-lookup"><span data-stu-id="f853c-168">OUTPUTS</span></span>

### <span data-ttu-id="f853c-169">없음</span><span class="sxs-lookup"><span data-stu-id="f853c-169">None</span></span>

<span data-ttu-id="f853c-170">이 cmdlet은 어떠한 출력도 반환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f853c-170">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="f853c-171">참고</span><span class="sxs-lookup"><span data-stu-id="f853c-171">NOTES</span></span>

<span data-ttu-id="f853c-172">`Set-StrictMode` **Version** 매개 변수는 보다 큰 값 `3.0` 을 허용 하지만, 현재 보다 높은 항목에 대해 정의 된 추가 규칙은 없습니다 `3.0` .</span><span class="sxs-lookup"><span data-stu-id="f853c-172">While `Set-StrictMode` **Version** parameter will accept values greater than `3.0`, currently there are no additional rules defined for anything higher than `3.0`.</span></span>

<span data-ttu-id="f853c-173">`Set-StrictMode` 는 설정 된 범위와 해당 하위 범위에만 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f853c-173">`Set-StrictMode` is effective only in the scope in which it is set and in its child scopes.</span></span> <span data-ttu-id="f853c-174">PowerShell의 범위에 대 한 자세한 내용은 [about_Scopes](about/about_Scopes.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f853c-174">For more information about scopes in PowerShell, see [about_Scopes](about/about_Scopes.md).</span></span>

## <span data-ttu-id="f853c-175">관련 링크</span><span class="sxs-lookup"><span data-stu-id="f853c-175">RELATED LINKS</span></span>

[<span data-ttu-id="f853c-176">Set-PSDebug</span><span class="sxs-lookup"><span data-stu-id="f853c-176">Set-PSDebug</span></span>](Set-PSDebug.md)
