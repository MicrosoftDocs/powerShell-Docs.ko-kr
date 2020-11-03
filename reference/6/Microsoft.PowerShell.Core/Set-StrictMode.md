---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/09/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/set-strictmode?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-StrictMode
ms.openlocfilehash: d28ff57c864847658072c9b7a1979b2b513c04b3
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93217169"
---
# <span data-ttu-id="d9dbf-103">Set-StrictMode</span><span class="sxs-lookup"><span data-stu-id="d9dbf-103">Set-StrictMode</span></span>

## <span data-ttu-id="d9dbf-104">개요</span><span class="sxs-lookup"><span data-stu-id="d9dbf-104">SYNOPSIS</span></span>
<span data-ttu-id="d9dbf-105">식, 스크립트 및 스크립트 블록에서 코딩 규칙을 설정하고 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="d9dbf-105">Establishes and enforces coding rules in expressions, scripts, and script blocks.</span></span>

## <span data-ttu-id="d9dbf-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d9dbf-106">SYNTAX</span></span>

### <span data-ttu-id="d9dbf-107">Version (기본값)</span><span class="sxs-lookup"><span data-stu-id="d9dbf-107">Version (Default)</span></span>

```
Set-StrictMode -Version <Version> [<CommonParameters>]
```

### <span data-ttu-id="d9dbf-108">끄기</span><span class="sxs-lookup"><span data-stu-id="d9dbf-108">Off</span></span>

```
Set-StrictMode [-Off] [<CommonParameters>]
```

## <span data-ttu-id="d9dbf-109">설명</span><span class="sxs-lookup"><span data-stu-id="d9dbf-109">DESCRIPTION</span></span>

<span data-ttu-id="d9dbf-110">`Set-StrictMode`Cmdlet은 현재 범위와 모든 자식 범위에 대해 strict 모드를 구성 하 고 설정 및 해제 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9dbf-110">The `Set-StrictMode` cmdlet configures strict mode for the current scope and all child scopes, and turns it on and off.</span></span> <span data-ttu-id="d9dbf-111">Strict 모드가 on 인 경우 식, 스크립트 또는 스크립트 블록의 내용이 기본 모범 사례 코딩 규칙을 위반 하면 PowerShell에서 종료 오류를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9dbf-111">When strict mode is on, PowerShell generates a terminating error when the content of an expression, script, or script block violates basic best-practice coding rules.</span></span>

<span data-ttu-id="d9dbf-112">**Version** 매개 변수를 사용 하 여 적용 되는 코딩 규칙을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9dbf-112">Use the **Version** parameter to determine which coding rules are enforced.</span></span>

<span data-ttu-id="d9dbf-113">`Set-PSDebug -Strict` cmdlet은 전역 범위에 대해 strict 모드를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9dbf-113">`Set-PSDebug -Strict` cmdlet turns on strict mode for the global scope.</span></span> <span data-ttu-id="d9dbf-114">`Set-StrictMode` 현재 범위와 해당 하위 범위에만 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d9dbf-114">`Set-StrictMode` affects only the current scope and its child scopes.</span></span> <span data-ttu-id="d9dbf-115">따라서 스크립트나 함수에서이 함수를 사용 하 여 전역 범위에서 상속 된 설정을 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9dbf-115">Therefore, you can use it in a script or function to override the setting inherited from the global scope.</span></span>

<span data-ttu-id="d9dbf-116">`Set-StrictMode`가 off 인 경우 PowerShell은 다음과 같은 동작을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9dbf-116">When `Set-StrictMode` is off, PowerShell has the following behaviors:</span></span>

- <span data-ttu-id="d9dbf-117">초기화 되지 않은 변수는 `$Null` 형식에 따라 0 또는 값을 갖는 것으로 간주 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9dbf-117">Uninitialized variables are assumed to have a value of 0 (zero) or `$Null`, depending on type</span></span>
- <span data-ttu-id="d9dbf-118">존재 하지 않는 속성에 대 한 참조가 반환 됩니다. `$Null`</span><span class="sxs-lookup"><span data-stu-id="d9dbf-118">References to non-existent properties return `$Null`</span></span>
- <span data-ttu-id="d9dbf-119">잘못 된 함수 구문의 결과는 오류 조건에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="d9dbf-119">Results of improper function syntax vary with the error conditions</span></span>
- <span data-ttu-id="d9dbf-120">배열의 잘못 된 인덱스를 사용 하 여 값을 검색 하려고 하면이 반환 됩니다. `$Null`</span><span class="sxs-lookup"><span data-stu-id="d9dbf-120">Attempting to retrieve a value using an invalid index in an array returns `$Null`</span></span>

## <span data-ttu-id="d9dbf-121">예제</span><span class="sxs-lookup"><span data-stu-id="d9dbf-121">EXAMPLES</span></span>

### <span data-ttu-id="d9dbf-122">예제 1: strict 모드를 버전 1.0로 설정</span><span class="sxs-lookup"><span data-stu-id="d9dbf-122">Example 1: Turn on strict mode as version 1.0</span></span>

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
The variable $a cannot be retrieved because it has not been set yet.

At line:1 char:3
+ $a <<<<  -gt 5
+ CategoryInfo          : InvalidOperation: (a:Token) [], RuntimeException
+ FullyQualifiedErrorId : VariableIsUndefined
```

<span data-ttu-id="d9dbf-123">Strict 모드를 버전 1.0로 설정 하면 초기화 되지 않은 변수를 참조 하려는 시도가 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9dbf-123">With strict mode set to version 1.0, attempts to reference variables that are not initialized fail.</span></span>

### <span data-ttu-id="d9dbf-124">예제 2: strict 모드를 버전 2.0로 설정</span><span class="sxs-lookup"><span data-stu-id="d9dbf-124">Example 2: Turn on strict mode as version 2.0</span></span>

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
The function or command was called like a method. Parameters should be separated by spaces,
as described in 'Get-Help about_Parameter.'
At line:1 char:4
+ add <<<< (3,4)
+ CategoryInfo          : InvalidOperation: (:) [], RuntimeException
+ FullyQualifiedErrorId : StrictModeFunctionCallWithParens
```

```powershell
Set-StrictMode -Off
$string = "This is a string."
$string.Month -eq $null
```

```Output
True
```

```powershell
Set-StrictMode -Version 2.0
$string = "This is a string."
$string.Month -eq $null
```

```Output
Property 'Month' cannot be found on this object; make sure it exists.
At line:1 char:9
+ $string. <<<< month
+ CategoryInfo          : InvalidOperation: (.:OperatorToken) [], RuntimeException
+ FullyQualifiedErrorId : PropertyNotFoundStrict
```

<span data-ttu-id="d9dbf-125">이 명령은 strict 모드를 켜고 버전 2.0으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="d9dbf-125">This command turns strict mode on and sets it to version 2.0.</span></span> <span data-ttu-id="d9dbf-126">따라서 함수 호출에 대해 괄호와 쉼표를 사용 하는 메서드 구문을 사용 하거나 초기화 되지 않은 변수나 존재 하지 않는 속성을 참조 하는 경우 PowerShell에서 오류를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9dbf-126">As a result, PowerShell returns an error if you use method syntax, which uses parentheses and commas, for a function call or reference uninitialized variables or non-existent properties.</span></span>

<span data-ttu-id="d9dbf-127">샘플 출력은 버전 2.0 strict 모드의 결과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d9dbf-127">The sample output shows the effect of version 2.0 strict mode.</span></span>

<span data-ttu-id="d9dbf-128">버전 2.0 strict 모드를 사용하지 않으면 "(3,4)" 값은 아무것도 추가되지 않은 단일 배열 개체로 해석됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9dbf-128">Without version 2.0 strict mode, the "(3,4)" value is interpreted as a single array object to which nothing is added.</span></span> <span data-ttu-id="d9dbf-129">버전 2.0 strict 모드를 사용 하면 두 값을 제출 하는 잘못 된 구문으로 올바르게 해석 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9dbf-129">By using version 2.0 strict mode, it is correctly interpreted as faulty syntax for submitting two values.</span></span>

<span data-ttu-id="d9dbf-130">버전 2.0을 사용 하지 않으면 문자열의 존재 하지 않는 **Month** 속성에 대 한 참조는만 반환 `$Null` 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9dbf-130">Without version 2.0, the reference to the non-existent **Month** property of a string returns only `$Null`.</span></span> <span data-ttu-id="d9dbf-131">버전 2.0을 사용 하면 참조 오류로 올바르게 해석 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9dbf-131">By using version 2.0, it is interpreted correctly as a reference error.</span></span>

### <span data-ttu-id="d9dbf-132">예제 3: strict 모드를 버전 3.0로 설정</span><span class="sxs-lookup"><span data-stu-id="d9dbf-132">Example 3: Turn on strict mode as version 3.0</span></span>

<span data-ttu-id="d9dbf-133">Strict 모드가 **Off** 로 설정 된 경우 범위를 벗어난 인덱스 결과는 null 값을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9dbf-133">With strict mode set to **Off** , invalid or out of bounds indexes result return null values.</span></span>

```powershell
# Strict mode is off by default.
$a = @(1)
$a[2] -eq $null
$a['abc'] -eq $null
```

```Output
True
True
```

```powershell
Set-StrictMode -Version 3
$a = @(1)
$a[2] -eq $null
$a['abc'] -eq $null
```

```Output
Index was outside the bounds of the array.
At line:1 char:1
+ $a[2] -eq $null
+ ~~~~~~~~~~~~~~~
    + CategoryInfo          : OperationStopped: (:) [], IndexOutOfRangeException
    + FullyQualifiedErrorId : System.IndexOutOfRangeException

Cannot convert value "abc" to type "System.Int32". Error: "Input string was not in a correct format."
At line:1 char:1
+ $a['abc'] -eq $null
+ ~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [], RuntimeException
    + FullyQualifiedErrorId : InvalidCastFromStringToInteger
```

<span data-ttu-id="d9dbf-134">Strict 모드가 버전 3 이상으로 설정 되 면 범위를 잘못 되었거나 범위를 벗어난 인덱스에서 오류가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9dbf-134">With strict mode set to version 3 or higher, invalid or out of bounds indexes result in errors.</span></span>

## <span data-ttu-id="d9dbf-135">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d9dbf-135">PARAMETERS</span></span>

### <span data-ttu-id="d9dbf-136">-꺼짐</span><span class="sxs-lookup"><span data-stu-id="d9dbf-136">-Off</span></span>

<span data-ttu-id="d9dbf-137">이 cmdlet이 현재 범위와 모든 자식 범위에 대해 strict 모드를 해제 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d9dbf-137">Indicates that this cmdlet turns strict mode off for the current scope and all child scopes.</span></span>

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

### <span data-ttu-id="d9dbf-138">-Version</span><span class="sxs-lookup"><span data-stu-id="d9dbf-138">-Version</span></span>

<span data-ttu-id="d9dbf-139">strict 모드에서 오류를 발생시키는 조건을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d9dbf-139">Specifies the conditions that cause an error in strict mode.</span></span> <span data-ttu-id="d9dbf-140">이 매개 변수는 유효한 PowerShell 버전 번호를 모두 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9dbf-140">This parameter accepts any valid PowerShell version number.</span></span> <span data-ttu-id="d9dbf-141">3 보다 큰 숫자는 모두 **최신** 으로 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9dbf-141">Any number higher than 3 is treated as **Latest**.</span></span>

<span data-ttu-id="d9dbf-142">이 매개 변수에 유효한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d9dbf-142">The effective values for this parameter are:</span></span>

- <span data-ttu-id="d9dbf-143">1.0</span><span class="sxs-lookup"><span data-stu-id="d9dbf-143">1.0</span></span>
  - <span data-ttu-id="d9dbf-144">문자열에서 초기화 되지 않은 변수를 제외 하 고 초기화 되지 않은 변수에 대 한 참조를 금지 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9dbf-144">Prohibits references to uninitialized variables, except for uninitialized variables in strings.</span></span>
- <span data-ttu-id="d9dbf-145">2.0</span><span class="sxs-lookup"><span data-stu-id="d9dbf-145">2.0</span></span>
  - <span data-ttu-id="d9dbf-146">초기화 되지 않은 변수에 대 한 참조를 금지 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9dbf-146">Prohibits references to uninitialized variables.</span></span> <span data-ttu-id="d9dbf-147">여기에는 문자열에 초기화 되지 않은 변수가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9dbf-147">This includes uninitialized variables in strings.</span></span>
  - <span data-ttu-id="d9dbf-148">개체의 존재 하지 않는 속성에 대 한 참조를 금지 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9dbf-148">Prohibits references to non-existent properties of an object.</span></span>
  - <span data-ttu-id="d9dbf-149">메서드를 호출 하는 구문을 사용 하는 함수 호출을 금지 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9dbf-149">Prohibits function calls that use the syntax for calling methods.</span></span>
- <span data-ttu-id="d9dbf-150">3.0</span><span class="sxs-lookup"><span data-stu-id="d9dbf-150">3.0</span></span>
  - <span data-ttu-id="d9dbf-151">초기화 되지 않은 변수에 대 한 참조를 금지 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9dbf-151">Prohibits references to uninitialized variables.</span></span> <span data-ttu-id="d9dbf-152">여기에는 문자열에 초기화 되지 않은 변수가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9dbf-152">This includes uninitialized variables in strings.</span></span>
  - <span data-ttu-id="d9dbf-153">개체의 존재 하지 않는 속성에 대 한 참조를 금지 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9dbf-153">Prohibits references to non-existent properties of an object.</span></span>
  - <span data-ttu-id="d9dbf-154">메서드를 호출 하는 구문을 사용 하는 함수 호출을 금지 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9dbf-154">Prohibits function calls that use the syntax for calling methods.</span></span>
  - <span data-ttu-id="d9dbf-155">범위를 벗어났거나 확인할 수가 없는 배열 인덱스를 금지 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9dbf-155">Prohibit out of bounds or unresolvable array indexes.</span></span>
- <span data-ttu-id="d9dbf-156">최신</span><span class="sxs-lookup"><span data-stu-id="d9dbf-156">Latest</span></span>
  - <span data-ttu-id="d9dbf-157">사용 가능한 최신 버전을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9dbf-157">Selects the latest version available.</span></span> <span data-ttu-id="d9dbf-158">최신 버전은 가장 엄격 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9dbf-158">The latest version is the most strict.</span></span> <span data-ttu-id="d9dbf-159">새 버전이 PowerShell에 추가 되는 경우에도 스크립트에서 사용 가능한 가장 엄격한 버전을 사용 하는지 확인 하려면이 값을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9dbf-159">Use this value to make sure that scripts use the strictest available version, even when new versions are added to PowerShell.</span></span>

> [!CAUTION]
> <span data-ttu-id="d9dbf-160">스크립트에서 **최신** **버전** 을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9dbf-160">Using a **Version** of **Latest** in scripts.</span></span> <span data-ttu-id="d9dbf-161">**최신** 의 의미는 PowerShell의 새 릴리스에서 변경 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9dbf-161">The meaning of **Latest** can change in new releases of PowerShell.</span></span> <span data-ttu-id="d9dbf-162">따라서를 사용 하는 이전 버전의 PowerShell 용으로 작성 된 스크립트는 `Set-StrictMode -Version Latest` 최신 버전의 powershell에서 실행 될 때 더 제한적인 규칙이 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9dbf-162">Therefore, a script written for an older version of PowerShell that uses `Set-StrictMode -Version Latest` is subject to more restrictive rules when run in a newer version of PowerShell.</span></span>

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

### <span data-ttu-id="d9dbf-163">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d9dbf-163">CommonParameters</span></span>

<span data-ttu-id="d9dbf-164">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d9dbf-164">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d9dbf-165">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d9dbf-165">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d9dbf-166">입력</span><span class="sxs-lookup"><span data-stu-id="d9dbf-166">INPUTS</span></span>

### <span data-ttu-id="d9dbf-167">없음</span><span class="sxs-lookup"><span data-stu-id="d9dbf-167">None</span></span>

<span data-ttu-id="d9dbf-168">이 cmdlet에 입력을 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d9dbf-168">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="d9dbf-169">출력</span><span class="sxs-lookup"><span data-stu-id="d9dbf-169">OUTPUTS</span></span>

### <span data-ttu-id="d9dbf-170">없음</span><span class="sxs-lookup"><span data-stu-id="d9dbf-170">None</span></span>

<span data-ttu-id="d9dbf-171">이 cmdlet은 어떠한 출력도 반환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d9dbf-171">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="d9dbf-172">참고</span><span class="sxs-lookup"><span data-stu-id="d9dbf-172">NOTES</span></span>

<span data-ttu-id="d9dbf-173">`Set-StrictMode` 는 설정 된 범위와 해당 하위 범위에만 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9dbf-173">`Set-StrictMode` is effective only in the scope in which it is set and in its child scopes.</span></span> <span data-ttu-id="d9dbf-174">PowerShell의 범위에 대 한 자세한 내용은 [about_Scopes](about/about_Scopes.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d9dbf-174">For more information about scopes in PowerShell, see [about_Scopes](about/about_Scopes.md).</span></span>

## <span data-ttu-id="d9dbf-175">관련 링크</span><span class="sxs-lookup"><span data-stu-id="d9dbf-175">RELATED LINKS</span></span>

[<span data-ttu-id="d9dbf-176">Set-PSDebug</span><span class="sxs-lookup"><span data-stu-id="d9dbf-176">Set-PSDebug</span></span>](Set-PSDebug.md)
