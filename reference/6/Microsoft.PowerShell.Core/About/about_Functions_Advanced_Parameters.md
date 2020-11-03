---
description: 고급 함수에 매개 변수를 추가 하는 방법을 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_functions_advanced_parameters?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Functions_Advanced_Parameters
ms.openlocfilehash: 1d33fcd6ccb665ceae1db91783542385fd49b9cc
ms.sourcegitcommit: 3b1779890f828130a9d73aebf17ebffae511728f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/28/2020
ms.locfileid: "93225257"
---
# <a name="about-functions-advanced-parameters"></a>함수 고급 매개 변수 정보

## <a name="short-description"></a>간단한 설명

고급 함수에 매개 변수를 추가 하는 방법을 설명 합니다.

## <a name="long-description"></a>자세한 설명입니다.

작성 하는 고급 함수에 매개 변수를 추가 하 고 매개 변수 특성 및 인수를 사용 하 여 함수 사용자가 매개 변수를 사용 하 여 제출 하는 매개 변수 값을 제한할 수 있습니다.

함수에 추가 하는 매개 변수는 PowerShell이 모든 cmdlet 및 고급 기능에 자동으로 추가 하는 일반 매개 변수 외에도 사용자가 사용할 수 있습니다. PowerShell 일반 매개 변수에 대 한 자세한 내용은 [about_CommonParameters](about_CommonParameters.md)를 참조 하세요.

PowerShell 3.0 부터는에서 스 플랫를 사용 `@Args` 하 여 명령에 매개 변수를 나타낼 수 있습니다. 스 플랫은 단순 및 고급 함수에서 유효 합니다. 자세한 내용은 [about_Functions](about_Functions.md) 및 [about_Splatting](about_Splatting.md)를 참조 하세요.

## <a name="type-conversion-of-parameter-values"></a>매개 변수 값의 형식 변환

다른 형식을 필요로 하는 매개 변수에 대 한 인수로 문자열을 제공 하면 PowerShell에서 암시적으로 문자열을 매개 변수 대상 형식으로 변환 합니다.
고급 함수는 매개 변수 값의 문화권 고정 구문 분석을 수행 합니다.

이와 대조적으로, 컴파일된 cmdlet에 대 한 매개 변수를 바인딩하는 동안 문화권 구분 변환이 수행 됩니다.

이 예에서는 매개 변수를 사용 하는 cmdlet 및 스크립트 함수를 만듭니다 `[datetime]` . 현재 문화권이 독일어 설정을 사용 하도록 변경 되었습니다.
독일어 형식 날짜는 매개 변수로 전달 됩니다.

```powershell
# Create a cmdlet that accepts a [datetime] argument.
Add-Type @'
  using System;
  using System.Management.Automation;
  [Cmdlet("Get", "Date_Cmdlet")]
  public class GetFooCmdlet : Cmdlet {

    [Parameter(Position=0)]
    public DateTime Date { get; set; }

    protected override void ProcessRecord() {
      WriteObject(Date);
    }
  }
'@ -PassThru | % Assembly | Import-Module

[cultureinfo]::CurrentCulture = 'de-DE'
$dateStr = '19-06-2018'

Get-Date_Cmdlet $dateStr
```

```Output
Dienstag, 19. Juni 2018 00:00:00
```

위와 같이 cmdlet은 문화권 구분 구문 분석을 사용 하 여 문자열을 변환 합니다.

```powershell
# Define an equivalent function.
function Get-Date_Func {
  param(
    [DateTime] $Date
  )
  process {
    $Date
  }
}

[cultureinfo]::CurrentCulture = 'de-DE'

# This German-format date string doesn't work with the invariant culture.
# E.g., [datetime] '19-06-2018' breaks.
$dateStr = '19-06-2018'

Get-Date_Func $dateStr
```

고급 함수는 문화권 고정 구문 분석을 사용 하며,이로 인해 다음 오류가 발생 합니다.

```Output
Get-Date_Func : Cannot process argument transformation on parameter 'Date'. Cannot convert
 value "19-06-2018" to type "System.DateTime". Error: "String was not recognized as a valid
 DateTime."
At line:13 char:15
+ Get-Date_Func $dateStr
+               ~~~~~~~~
    + CategoryInfo          : InvalidData: (:) [Get-Date_Func], ParameterBindingArgumentTransformationException
    + FullyQualifiedErrorId : ParameterArgumentTransformationError,Get-Date_Func
```

## <a name="static-parameters"></a>정적 매개 변수

정적 매개 변수는 함수에서 항상 사용할 수 있는 매개 변수입니다.
PowerShell cmdlet 및 스크립트의 대부분의 매개 변수는 정적 매개 변수입니다.

다음 예제에서는 다음과 같은 특징이 있는 **ComputerName** 매개 변수를 선언 하는 방법을 보여 줍니다.

- 필수 (필수)입니다.
- 파이프라인에서 입력을 가져옵니다.
- 문자열 배열을 입력으로 사용 합니다.

```powershell
Param(
    [Parameter(Mandatory=$true,
    ValueFromPipeline=$true)]
    [String[]]
    $ComputerName
)
```

## <a name="attributes-of-parameters"></a>매개 변수의 특성

이 섹션에서는 함수 매개 변수에 추가할 수 있는 특성에 대해 설명 합니다.

모든 특성은 선택 사항입니다. 그러나 **Cmdletbinding** 특성을 생략 하 고 고급 함수로 인식 되는 경우 함수는 **매개 변수** 특성을 포함 해야 합니다.

각 매개 변수 선언에서 하나 이상의 특성을 추가할 수 있습니다. 매개 변수 선언에 추가할 수 있는 특성의 수에는 제한이 없습니다.

### <a name="parameter-attribute"></a>매개 변수 특성

**Parameter** 특성은 함수 매개 변수의 특성을 선언 하는 데 사용 됩니다.

**매개 변수** 특성은 선택 사항이 며, 함수 매개 변수에 특성이 필요 하지 않은 경우 생략할 수 있습니다. 그러나 간단한 함수 대신 고급 함수로 인식 되려면 함수는 **Cmdletbinding** 특성 또는 **Parameter** 특성 중 하나 또는 둘 다가 있어야 합니다.

Parameter **특성에** 는 매개 변수의 특징을 정의 하는 인수 (예: 매개 변수가 필수 인지 또는 선택 사항)가 있습니다.

다음 구문을 사용 하 여 **매개 변수** 특성, 인수 및 인수 값을 선언 합니다. 인수 및 해당 값을 묶는 괄호는 중간에 공백이 없는 **매개 변수** 다음에와 야 합니다.

```powershell
Param(
    [Parameter(Argument=value)]
    $ParameterName
)
```

괄호 안에 쉼표를 사용 하 여 인수를 구분 합니다. 다음 구문을 사용 하 여 **매개 변수** 특성의 두 인수를 선언 합니다.

```powershell
Param(
    [Parameter(Argument1=value1,
    Argument2=value2)]
)
```

Parameter **특성의** 부울 인수 형식은 **매개 변수** 특성에서 생략 될 경우 기본적으로 **False로 설정** 됩니다. 인수 값을로 설정 `$true` 하거나 인수를 이름으로 나열 합니다. 예를 들어 다음 **매개 변수** 특성은 동일 합니다.

```powershell
Param(
    [Parameter(Mandatory=$true)]
)

# Boolean arguments can be defined using this shorthand syntax

Param(
    [Parameter(Mandatory)]
)
```

**Cmdletbinding** 특성을 사용 하는 대신 **매개 변수** 특성을 인수 없이 사용 하는 경우 특성 이름 다음에 오는 괄호는 여전히 필요 합니다.

```powershell
Param(
    [Parameter()]
    $ParameterName
)
```

#### <a name="mandatory-argument"></a>필수 인수

`Mandatory`인수는 매개 변수가 필요 함을 나타냅니다. 이 인수를 지정 하지 않으면 매개 변수는 선택 사항입니다.

다음 예에서는 **ComputerName** 매개 변수를 선언 합니다. 인수를 사용 하 여 `Mandatory` 매개 변수를 필수로 만듭니다.

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [String[]]
    $ComputerName
)
```

#### <a name="position-argument"></a>Position 인수

`Position`인수는 매개 변수를 명령에 사용할 때 매개 변수 이름이 필요한 지 여부를 결정 합니다. 매개 변수 선언에 인수가 포함 된 경우 `Position` 매개 변수 이름을 생략할 수 있으며, PowerShell에서 명명 되지 않은 매개 변수 값을 명령의 명명 되지 않은 매개 변수 값 목록에서 해당 위치나 순서로 식별할 수 있습니다.

인수를 지정 하지 않으면 매개 변수가 명령에 사용 될 때마다 매개 변수 이름 또는 매개 변수 이름 또는 약어는 매개 변수 `Position` 값 앞에와 야 합니다.

기본적으로 모든 함수 매개 변수는 위치입니다. PowerShell은 함수에서 매개 변수가 선언 된 순서 대로 매개 변수에 위치 번호를 할당 합니다. 이 기능을 사용 하지 않도록 설정 하려면 `PositionalBinding` **cmdletbinding** 특성의 인수 값을로 설정 합니다 `$False` . `Position`인수는 `PositionalBinding` **cmdletbinding** 특성의 인수 값 보다 우선적으로 적용 됩니다. 자세한 내용은 about_Functions_CmdletBindingAttribute을 참조 `PositionalBinding` 하세요 [about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md).

인수의 값은 `Position` 정수로 지정 됩니다. Position 값 **0** 은 명령의 첫 번째 위치를 나타내고, position 값 **1** 은 명령의 두 번째 위치를 나타냅니다.

함수에 위치 매개 변수가 없으면 PowerShell은 매개 변수가 선언 된 순서에 따라 각 매개 변수에 위치를 할당 합니다.
그러나이 할당을 사용 하지 않는 것이 좋습니다. 매개 변수를 위치 하려면 인수를 사용 `Position` 합니다.

다음 예에서는 **ComputerName** 매개 변수를 선언 합니다. `Position`값이 **0** 인 인수를 사용 합니다. 결과적으로 `-ComputerName` 명령에서을 생략 하면 해당 값은 명령의 첫 번째 또는 유일한 명명 되지 않은 매개 변수 값 이어야 합니다.

```powershell
Param(
    [Parameter(Position=0)]
    [String[]]
    $ComputerName
)
```

#### <a name="parametersetname-argument"></a>ParameterSetName 인수

`ParameterSetName`인수는 매개 변수가 속하는 매개 변수 집합을 지정 합니다. 매개 변수 집합이 지정 되지 않은 경우 매개 변수는 함수에 정의 된 모든 매개 변수 집합에 속합니다. 따라서 고유 하려면 각 매개 변수 집합에 다른 매개 변수 집합의 멤버가 아닌 매개 변수가 하나 이상 있어야 합니다.

> [!NOTE]
> Cmdlet 또는 함수의 경우 매개 변수 집합은 32 개로 제한 됩니다.

다음 예에서는 매개 변수 집합에서 **ComputerName** 매개 변수 `Computer` , 매개 변수 집합의 **UserName** 매개 변수 `User` 및 두 매개 변수 집합 모두에 **요약** 매개 변수를 선언 합니다.

```powershell
Param(
    [Parameter(Mandatory=$true,
    ParameterSetName="Computer")]
    [String[]]
    $ComputerName,

    [Parameter(Mandatory=$true,
    ParameterSetName="User")]
    [String[]]
    $UserName,

    [Parameter(Mandatory=$false)]
    [Switch]
    $Summary
)
```

각 인수에는 값을 하나만 지정할 수 있으며 `ParameterSetName` `ParameterSetName` 각 **매개 변수** 특성에는 하나의 인수만 지정할 수 있습니다. 매개 변수가 둘 이상의 매개 변수 집합에 표시 되도록 지정 하려면 **매개 변수** 특성을 추가 합니다.

다음 예제에서는 **Summary** `Computer` 및 `User` 매개 변수 집합에 요약 매개 변수를 명시적으로 추가 합니다. **요약** 매개 변수는 매개 변수 집합에서 선택 사항이 며 `Computer` `User` 매개 변수 집합에서 필수입니다.

```powershell
Param(
    [Parameter(Mandatory=$true,
    ParameterSetName="Computer")]
    [String[]]
    $ComputerName,

    [Parameter(Mandatory=$true,
    ParameterSetName="User")]
    [String[]]
    $UserName,

    [Parameter(Mandatory=$false, ParameterSetName="Computer")]
    [Parameter(Mandatory=$true, ParameterSetName="User")]
    [Switch]
    $Summary
)
```

매개 변수 집합에 대 한 자세한 내용은 [매개 변수 집합](about_parameter_sets.md)정보를 참조 하세요.

#### <a name="valuefrompipeline-argument"></a>ValueFromPipeline 인수

`ValueFromPipeline`인수는 매개 변수가 파이프라인 개체의 입력을 허용 함을 나타냅니다. 함수가 개체의 속성 뿐만 아니라 전체 개체를 허용 하는 경우이 인수를 지정 합니다.

다음 예제에서는 필수 이며 파이프라인에서 함수로 전달 되는 개체를 허용 하는 **ComputerName** 매개 변수를 선언 합니다.

```powershell
Param(
    [Parameter(Mandatory=$true,
    ValueFromPipeline=$true)]
    [String[]]
    $ComputerName
)
```

#### <a name="valuefrompipelinebypropertyname-argument"></a>ValueFromPipelineByPropertyName 인수

`ValueFromPipelineByPropertyName`인수는 매개 변수가 파이프라인 개체의 속성에서 입력을 허용 함을 나타냅니다. 개체 속성의 이름 또는 별칭이 매개 변수와 같아야 합니다.

예를 들어 함수에 **computername** 매개 변수가 있고 파이프 된 개체에 **computername** 속성이 있는 경우 **computername** 속성의 값은 함수의 **computername** 매개 변수에 할당 됩니다.

다음 예제에서는 필수 이며 파이프라인을 통해 함수에 전달 되는 개체의 **computername** 속성의 입력을 허용 하는 **computername** 매개 변수를 선언 합니다.

```powershell
Param(
    [Parameter(Mandatory=$true,
    ValueFromPipelineByPropertyName=$true)]
    [String[]]
    $ComputerName
)
```

> [!NOTE]
> 파이프라인 입력 () 또는 ()를 허용 하는 형식화 된 매개 변수는 `by Value` `by PropertyName` 매개 변수에 대해 _지연 바인딩_ 스크립트 블록을 사용할 수 있도록 합니다.
>
> _지연 바인드_ 스크립트 블록은 **parameterbinding** 중에 자동으로 실행 됩니다. 결과는 매개 변수에 바인딩됩니다. 또는 형식으로 정의 된 매개 변수에 대해서는 지연 바인딩이 작동 하지 않습니다 `ScriptBlock` `System.Object` . 스크립트 블록은 호출 되지 _않고_ 를 통해 전달 됩니다.
>
> About_Script_Blocks _에서 지연 바인딩_ 스크립트 블록을 읽을 수 있습니다 [.](about_Script_Blocks.md)

#### <a name="valuefromremainingarguments-argument"></a>ValueFromRemainingArguments 인수

`ValueFromRemainingArguments`인수는 매개 변수가 함수의 다른 매개 변수에 할당 되지 않은 명령의 모든 매개 변수 값을 허용 함을 나타냅니다.

다음 예제에서는 필수 매개 **변수 및** 함수에 전송 된 나머지 모든 매개 변수 값을 허용 하는 **나머지** 매개 변수를 선언 합니다.

```powershell
function Test-Remainder
{
     param(
         [string]
         [Parameter(Mandatory = $true, Position=0)]
         $Value,
         [string[]]
         [Parameter(Position=1, ValueFromRemainingArguments)]
         $Remaining)
     "Found $($Remaining.Count) elements"
     for ($i = 0; $i -lt $Remaining.Count; $i++)
     {
        "${i}: $($Remaining[$i])"
     }
}
Test-Remainder first one,two
```

```Output
Found 2 elements
0: one
1: two
```

> [!NOTE]
> PowerShell 6.2 이전에는 **ValueFromRemainingArguments** 컬렉션이 인덱스 **0** 에서 단일 엔터티로 조인 되었습니다.

#### <a name="helpmessage-argument"></a>HelpMessage 인수

`HelpMessage`인수는 매개 변수 또는 해당 값에 대 한 간략 한 설명을 포함 하는 문자열을 지정 합니다. PowerShell은 명령에 필수 매개 변수 값이 없을 때 표시 되는 프롬프트에이 메시지를 표시 합니다. 이 인수는 선택적 매개 변수에는 영향을 주지 않습니다.

다음 예제에서는 필요한 매개 변수 값을 설명 하는 필수 **ComputerName** 매개 변수와 도움말 메시지를 선언 합니다.

함수에 대 한 다른 [주석 기반 도움말](./about_comment_based_help.md) 구문이 없는 경우 (예: `.SYNOPSIS` )이 메시지는 출력에도 표시 됩니다 `Get-Help` .

```powershell
Param(
    [Parameter(Mandatory=$true,
    HelpMessage="Enter one or more computer names separated by commas.")]
    [String[]]
    $ComputerName
)
```

### <a name="alias-attribute"></a>Alias 특성

**Alias** 특성은 매개 변수에 대 한 대체 이름을 설정 합니다.
매개 변수에 할당할 수 있는 별칭의 수에는 제한이 없습니다.

다음 예제에서는 필수 **ComputerName** 매개 변수에 **CN** 및 **MachineName** 별칭을 추가 하는 매개 변수 선언을 보여 줍니다.

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [Alias("CN","MachineName")]
    [String[]]
    $ComputerName
)
```

### <a name="supportswildcards-attribute"></a>SupportsWildcards 특성

**SupportsWildcards** 특성은 매개 변수가 와일드 카드 값을 허용 함을 나타내는 데 사용 됩니다. 다음 예에서는 와일드 카드 값을 지 원하는 필수 **Path** 매개 변수에 대 한 매개 변수 선언을 보여 줍니다.

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [SupportsWildcards()]
    [String[]]
    $Path
)
```

이 특성을 사용 해도 와일드 카드 지원이 자동으로 사용 되지 않습니다. Cmdlet 개발자는 와일드 카드 입력을 처리 하는 코드를 구현 해야 합니다. 지원 되는 와일드 카드는 기본 API 또는 PowerShell 공급자에 따라 달라질 수 있습니다. 자세한 내용은 [about_Wildcards](about_Wildcards.md)를 참조 하세요.

### <a name="parameter-and-variable-validation-attributes"></a>매개 변수 및 변수 유효성 검사 특성

유효성 검사 특성 PowerShell을 통해 사용자가 고급 함수를 호출할 때 제출 하는 매개 변수 값을 테스트할 수 있습니다. 매개 변수 값이 테스트에 실패 하면 오류가 발생 하 고 함수가 호출 되지 않습니다. 매개 변수 유효성 검사는 제공 된 입력에만 적용 되며 기본값 등의 다른 값은 유효성이 검사 되지 않습니다.

유효성 검사 특성을 사용 하 여 사용자가 변수에 지정할 수 있는 값을 제한할 수도 있습니다. 유효성 검사 특성과 함께 형식 변환기를 사용 하는 경우 특성 앞에 형식 변환기를 정의 해야 합니다.

```powershell
[int32][AllowNull()] $number = 7
```

### <a name="allownull-validation-attribute"></a>AllowNull 유효성 검사 특성

**Allownull** 특성을 사용 하면 필수 매개 변수의 값이가 됩니다 `$null` . 다음 예에서는 **null** 값을 가질 수 있는 Hashtable **computerinfo** 매개 변수를 선언 합니다.

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [AllowNull()]
    [hashtable]
    $ComputerInfo
)
```

> [!NOTE]
> 문자열 형식에서 null 값을 허용 하지 않으므로 형식 변환기가 string으로 설정 된 경우 **Allownull** 특성은 작동 하지 않습니다. 이 시나리오에는 **AllowEmptyString** 특성을 사용할 수 있습니다.

### <a name="allowemptystring-validation-attribute"></a>AllowEmptyString validation 특성

**AllowEmptyString** 특성을 사용 하면 필수 매개 변수의 값이 빈 문자열 ()이 될 수 있습니다 `""` . 다음 예에서는 빈 문자열 값을 가질 수 있는 **ComputerName** 매개 변수를 선언 합니다.

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [AllowEmptyString()]
    [String]
    $ComputerName
)
```

### <a name="allowemptycollection-validation-attribute"></a>AllowEmptyCollection validation 특성

**AllowEmptyCollection** 특성을 사용 하면 필수 매개 변수의 값이 빈 컬렉션이 될 수 있습니다 `@()` . 다음 예제에서는 빈 컬렉션 값을 가질 수 있는 **ComputerName** 매개 변수를 선언 합니다.

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [AllowEmptyCollection()]
    [String[]]
    $ComputerName
)
```

### <a name="validatecount-validation-attribute"></a>ValidateCount 유효성 검사 특성

**Validatecount** 특성은 매개 변수가 허용 하는 매개 변수 값의 최소 및 최대 수를 지정 합니다. 함수를 호출 하는 명령의 매개 변수 값 수가 범위를 벗어나면 PowerShell에서 오류를 생성 합니다.

다음 매개 변수 선언은 1 ~ 5 개의 매개 변수 값을 사용 하는 **ComputerName** 매개 변수를 만듭니다.

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateCount(1,5)]
    [String[]]
    $ComputerName
)
```

### <a name="validatelength-validation-attribute"></a>ValidateLength validation 특성

**ValidateLength** 특성은 매개 변수 또는 변수 값의 최소 및 최대 문자 수를 지정 합니다. 매개 변수 또는 변수에 지정 된 값의 길이가 범위를 벗어나면 PowerShell에서 오류를 생성 합니다.

다음 예제에서 각 컴퓨터 이름은 1 자에서 10 자 사이 여야 합니다.

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateLength(1,10)]
    [String[]]
    $ComputerName
)
```

다음 예에서는 변수 값이 최소 1 자에서 `$number` 최대 10 자 사이 여야 합니다.

```powershell
[Int32][ValidateLength(1,10)]$number = '01'
```

> [!NOTE]
> 이 예제에서의 값은 `01` 작은따옴표로 래핑됩니다. **ValidateLength** 특성은 따옴표로 래핑되지 않고 숫자를 허용 하지 않습니다.

### <a name="validatepattern-validation-attribute"></a>ValidatePattern validation 특성

**ValidatePattern** 특성은 매개 변수 또는 변수 값과 비교 되는 정규식을 지정 합니다. 값이 정규식 패턴과 일치 하지 않으면 PowerShell에서 오류를 생성 합니다.

다음 예제에서 매개 변수 값은 네 자리 숫자를 포함 해야 하며 각 숫자는 0에서 9 사이의 숫자 여야 합니다.

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidatePattern("[0-9][0-9][0-9][0-9]")]
    [String[]]
    $ComputerName
)
```

다음 예에서는 변수 값 `$number` 이 정확히 4 자리 숫자 여야 하며 각 숫자는 0에서 9 사이의 숫자 여야 합니다.

```powershell
[Int32][ValidatePattern("^[0-9][0-9][0-9][0-9]$")]$number = 1111
```

### <a name="validaterange-validation-attribute"></a>ValidateRange validation 특성

**ValidateRange** 특성은 각 매개 변수 또는 변수 값에 대해 숫자 범위 또는 **ValidateRangeKind** 열거형 값을 지정 합니다.
값이 범위를 벗어나면 PowerShell에서 오류를 생성 합니다.

**ValidateRangeKind** 열거형은 다음 값을 허용 합니다.

- **양수** -0 보다 큰 숫자입니다.
- **음수** -0 보다 작은 숫자입니다.
- **Nonpositive** 아닙니다. 0 보다 작거나 같은 숫자입니다.
- **음수가** 아닌-0 보다 크거나 같은 숫자입니다.

다음 예에서는 **시도** 매개 변수의 값이 0에서 10 사이 여야 합니다.

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateRange(0,10)]
    [Int]
    $Attempts
)
```

다음 예에서는 변수 값 `$number` 이 0에서 10 사이 여야 합니다.

```powershell
[Int32][ValidateRange(0,10)]$number = 5
```

다음 예에서는 변수 값 `$number` 이 0 보다 커야 합니다.

```powershell
[Int32][ValidateRange("Positive")]$number = 1
```

### <a name="validatescript-validation-attribute"></a>ValidateScript validation 특성

**ValidateScript** 특성은 매개 변수 또는 변수 값의 유효성을 검사 하는 데 사용 되는 스크립트를 지정 합니다. PowerShell은 스크립트에 값을 파이프 하 고 스크립트가를 반환 하거나 스크립트가 예외를 throw 하는 경우 오류를 생성 합니다 `$false` .

**ValidateScript** 특성을 사용 하는 경우 유효성을 검사할 값이 `$_` 변수에 매핑됩니다. 변수를 사용 `$_` 하 여 스크립트의 값을 참조할 수 있습니다.

다음 예에서는 **eventdate** 매개 변수 값이 현재 날짜 보다 크거나 같아야 합니다.

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateScript({$_ -ge (Get-Date)})]
    [DateTime]
    $EventDate
)
```

다음 예에서는 변수 값이 `$date` 현재 날짜 및 시간 보다 크거나 같아야 합니다.

```powershell
[DateTime][ValidateScript({$_ -ge (Get-Date)})]$date = (Get-Date)
```

> [!NOTE]
> **ValidateScript** 를 사용 하는 경우 매개 변수에 값을 전달할 수 없습니다 `$null` . Null 값을 전달 하는 경우 **ValidateScript** 는 인수의 유효성을 검사할 수 없습니다.

### <a name="validateset-attribute"></a>ValidateSet 특성

**ValidateSet** 특성은 매개 변수 또는 변수에 대 한 유효한 값 집합을 지정 하 고 탭 완성 기능을 활성화 합니다. 매개 변수 또는 변수 값이 집합의 값과 일치 하지 않는 경우 PowerShell에서 오류를 생성 합니다. 다음 예제에서 **Detail** 매개 변수의 값은 Low, Average 또는 High만 가능 합니다.

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateSet("Low", "Average", "High")]
    [String[]]
    $Detail
)
```

다음 예에서는 변수 값이 `$flavor` 초콜릿, Strawberry 또는 바닐라 이어야 합니다.

```powershell
[ValidateSet("Chocolate", "Strawberry", "Vanilla")]
[String]$flavor = "Strawberry"
```

유효성 검사는 스크립트 내 에서도 변수가 할당 될 때마다 발생 합니다. 예를 들어 다음과 같은 경우 런타임에 오류가 발생 합니다.

```powershell
Param(
    [ValidateSet("hello", "world")]
    [String]$Message
)

$Message = "bye"
```

#### <a name="dynamic-validateset-values"></a>동적 validateSet 값

**클래스** 를 사용 하 여 런타임에 **ValidateSet** 에 대 한 값을 동적으로 생성할 수 있습니다. 다음 예제에서는 `$Sound` 사용 가능한 사운드 파일에 대 한 세 개의 filesystem 경로를 확인 하는 **SoundNames** 라는 **클래스** 를 통해 변수에 대 한 유효한 값을 생성 합니다.

```powershell
Class SoundNames : System.Management.Automation.IValidateSetValuesGenerator {
    [String[]] GetValidValues() {
        $SoundPaths = '/System/Library/Sounds/',
            '/Library/Sounds','~/Library/Sounds'
        $SoundNames = ForEach ($SoundPath in $SoundPaths) {
            If (Test-Path $SoundPath) {
                (Get-ChildItem $SoundPath).BaseName
            }
        }
        return [String[]] $SoundNames
    }
}
```

`[SoundNames]`그런 다음 클래스는 다음과 같이 동적 **ValidateSet** 값으로 구현 됩니다.

```powershell
Param(
    [ValidateSet([SoundNames])]
    [String]$Sound
)
```

### <a name="validatenotnull-validation-attribute"></a>ValidateNotNull validation 특성

**ValidateNotNull** 특성은 매개 변수 값이이 될 수 없도록 지정 합니다 `$null` . 매개 변수 값이 인 경우 PowerShell에서 오류를 생성 `$null` 합니다.

**ValidateNotNull** 특성은 매개 변수가 선택 사항이 고 형식이 정의 되지 않았거나 null 값을 암시적으로 **개체** 와 같은 형식 변환기를 포함 하는 경우에 사용 하도록 설계 되었습니다. **문자열과** 같은 null 값을 암시적으로 변환 하는 형식을 지정 하는 경우 **ValidateNotNull** 특성을 사용 하는 경우에도 null 값이 빈 문자열로 변환 됩니다. 이 시나리오의 경우 **ValidateNotNullOrEmpty** 를 사용 합니다.

다음 예에서는 **ID** 매개 변수의 값이 일 수 없습니다 `$null` .

```powershell
Param(
    [Parameter(Mandatory=$false)]
    [ValidateNotNull()]
    $ID
)
```

### <a name="validatenotnullorempty-validation-attribute"></a>ValidateNotNullOrEmpty validation 특성

**ValidateNotNullOrEmpty** 특성은 매개 변수 값이이 될 수 없으며 `$null` 빈 문자열 ()이 될 수 없도록 지정 합니다 `""` . 함수 호출에 매개 변수를 사용 하지만 해당 값이 `$null` , 빈 문자열 ( `""` ) 또는 빈 배열인 경우 PowerShell에서 오류를 생성 `@()` 합니다.

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateNotNullOrEmpty()]
    [String[]]
    $UserName
)
```

### <a name="validatedrive-validation-attribute"></a>ValidateDrive validation 특성

**ValidateDrive** 특성은 매개 변수 값이 경로를 나타내야 하며,이는 허용 된 드라이브만 참조 합니다. 매개 변수 값이 허용 되는 이외의 드라이브를 참조 하는 경우 PowerShell에서 오류를 생성 합니다. 드라이브 자체를 제외한 경로 존재는 확인 되지 않습니다.

상대 경로를 사용 하는 경우 현재 드라이브가 허용 되는 드라이브 목록에 있어야 합니다.

```powershell
Param(
    [ValidateDrive("C", "D", "Variable", "Function")]
    [String]$Path
)
```

### <a name="validateuserdrive-validation-attribute"></a>ValidateUserDrive 유효성 검사 특성

**Validateuserdrive** 특성은 매개 변수 값이 드라이브를 참조 하는 경로를 나타내야 함을 지정 합니다 `User` . 경로가 다른 드라이브를 참조 하는 경우 PowerShell에서 오류를 생성 합니다. 유효성 검사 특성은 경로의 드라이브 부분만 있는지를 테스트 합니다.

상대 경로를 사용 하는 경우 현재 드라이브가 이어야 합니다 `User` .

```powershell
function Test-UserDrivePath{
    [OutputType([bool])]
    Param(
      [Parameter(Mandatory=, Position=0)][ValidateUserDrive()][String]$Path
      )
    $True
}

Test-UserDrivePath -Path C:\
```

```Output
Test-UserDrivePath: Cannot validate argument on parameter 'Path'. The path
argument drive C does not belong to the set of approved drives: User.
Supply a path argument with an approved drive.
```

```powershell
Test-UserDrivePath -Path 'User:\A_folder_that_does_not_exist'
```

```Output
Test-UserDrivePath: Cannot validate argument on parameter 'Path'. Cannot
find drive. A drive with the name 'User' does not exist.
```

`User`충분 한 관리 (JEA) 세션 구성으로 드라이브를 정의할 수 있습니다. 이 예에서는 사용자: 드라이브를 만듭니다.

```powershell
New-PSDrive -Name 'User' -PSProvider FileSystem -Root $env:HOMEPATH
```

```Output
Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
User               75.76         24.24 FileSystem    C:\Users\ExampleUser

```powershell
Test-UserDrivePath -Path 'User:\A_folder_that_does_not_exist'
```

```Output
True
```

### <a name="validatetrusteddata-validation-attribute"></a>ValidateTrustedData validation 특성

이 특성은 PowerShell 6.1.1에서 추가 되었습니다.

현재 특성은 PowerShell 자체에서 내부적으로 사용 되며 외부 사용을 위한 것이 아닙니다.

## <a name="dynamic-parameters"></a>동적 매개 변수

동적 매개 변수는 특정 조건 에서만 사용할 수 있는 cmdlet, 함수 또는 스크립트의 매개 변수입니다.

예를 들어 공급자 드라이브 또는 공급자 드라이브의 특정 경로에서 cmdlet을 사용 하는 경우에만 사용할 수 있는 매개 변수가 여러 공급자 cmdlet에 있습니다. 예를 들어 **Encoding** 매개 변수는 `Add-Content` `Get-Content` `Set-Content` 파일 시스템 드라이브에서 사용 되는 경우에만, 및 cmdlet에서 사용할 수 있습니다.

또한 함수 명령에 다른 매개 변수를 사용 하거나 다른 매개 변수에 특정 값이 있는 경우에만 표시 되는 매개 변수를 만들 수 있습니다.

동적 매개 변수는 유용할 수 있지만 필요한 경우에만 사용할 수 있으므로 사용자가 검색 하기 어려울 수 있습니다. 동적 매개 변수를 찾으려면 사용자가 공급자 경로에 있어야 하 고, cmdlet의 **Argumentlist** 매개 변수를 사용 `Get-Command` 하거나,의 **path** 매개 변수를 사용 해야 합니다 `Get-Help` .

함수 또는 스크립트에 대 한 동적 매개 변수를 만들려면 키워드를 사용 `DynamicParam` 합니다.

구문은 다음과 같습니다.

`DynamicParam {<statement-list>}`

문 목록에서 문을 사용 하 여 `If` 함수에서 매개 변수를 사용할 수 있는 조건을 지정 합니다.

Cmdlet을 사용 하 여 `New-Object` 매개 변수를 나타내는 **RuntimeDefinedParameter** 개체를 만들고 해당 이름을 지정 합니다.

명령을 사용 하 여 `New-Object` 매개 변수의 특성 (예: **필수** , **위치** 또는 **ValueFromPipeline** 또는 해당 매개 변수 집합)을 나타내는 **system.object** 를 만들 수 있습니다.

다음 예에서는 **이름** 및 **경로** 라는 표준 매개 변수와 **DP1** 이라는 선택적 동적 매개 변수를 사용 하는 샘플 함수를 보여 줍니다. **DP1** 매개 변수는 `PSet1` 매개 변수 집합에 있고 형식이입니다 `Int32` .
**DP1** 매개 변수는 `Get-Sample` **Path** 매개 변수 값이로 시작 하는 경우에만 함수에서 사용할 수 있으며 `HKLM:` ,이는 레지스트리 드라이브에서 사용 중임을 나타냅니다 `HKEY_LOCAL_MACHINE` .

```powershell
function Get-Sample {
  [CmdletBinding()]
  Param([String]$Name, [String]$Path)

  DynamicParam
  {
    if ($Path.StartsWith("HKLM:"))
    {
      $attributes = New-Object -Type `
        System.Management.Automation.ParameterAttribute
      $attributes.ParameterSetName = "PSet1"
      $attributes.Mandatory = $false
      $attributeCollection = New-Object `
        -Type System.Collections.ObjectModel.Collection[System.Attribute]
      $attributeCollection.Add($attributes)

      $dynParam1 = New-Object -Type `
        System.Management.Automation.RuntimeDefinedParameter("DP1", [Int32],
          $attributeCollection)

      $paramDictionary = New-Object `
        -Type System.Management.Automation.RuntimeDefinedParameterDictionary
      $paramDictionary.Add("DP1", $dynParam1)
      return $paramDictionary
    }
  }
}
```

자세한 내용은 [RuntimeDefinedParameter](/dotnet/api/system.management.automation.runtimedefinedparameter)를 참조 하세요.

## <a name="switch-parameters"></a>Switch 매개 변수

스위치 매개 변수는 매개 변수 값이 없는 매개 변수입니다. 사용 되는 경우에만 적용 되며 효과가 하나만 있는 경우에 적용 됩니다.

예를 들어 **powershell.exe** 의 **noprofile** 매개 변수는 스위치 매개 변수입니다.

함수에서 스위치 매개 변수를 만들려면 `Switch` 매개 변수 정의에 유형을 지정 합니다.

다음은 그 예입니다. 

```powershell
Param([Switch]<ParameterName>)
```

또는 다른 방법을 사용할 수 있습니다.

```powershell
Param(
    [Parameter(Mandatory=$false)]
    [Switch]
    $<ParameterName>
)
```

스위치 매개 변수는 쉽게 사용할 수 있으며 더 어려운 구문을 사용 하는 부울 매개 변수 보다 우선적으로 사용 됩니다.

예를 들어 스위치 매개 변수를 사용 하기 위해 사용자는 명령에 매개 변수를 입력 합니다.

`-IncludeAll`

부울 매개 변수를 사용 하기 위해 사용자는 매개 변수와 부울 값을 입력 합니다.

`-IncludeAll:$true`

스위치 매개 변수를 만들 때 매개 변수 이름을 신중 하 게 선택 합니다. 매개 변수 이름은 매개 변수의 효과를 사용자에 게 전달 해야 합니다.
값을 암시 하는 **필터** 또는 **최대값과** 같은 모호한 용어를 사용 하지 마십시오.

## <a name="argumentcompleter-attribute"></a>ArgumentCompleter 특성

**ArgumentCompleter** 특성을 사용 하면 특정 매개 변수에 탭 완성 값을 추가할 수 있습니다. 탭 완성이 필요한 각 매개 변수에 대해 **ArgumentCompleter** 특성을 정의 해야 합니다. **Dynamicparameters** 와 마찬가지로, 사용자가 매개 변수 이름 뒤에 <kbd>tab</kbd> 키를 누르면 런타임에 사용 가능한 값이 계산 됩니다.

**ArgumentCompleter** 특성을 추가 하려면 값을 결정 하는 스크립트 블록을 정의 해야 합니다. 스크립트 블록은 아래 지정 된 순서 대로 다음 매개 변수를 사용 해야 합니다. 값이 메서드에 액세스할 제공 되므로 매개 변수의 이름은 중요 하지 않습니다.

구문은 다음과 같습니다.

```powershell
Param(
    [Parameter(Mandatory)]
    [ArgumentCompleter({
        param ( $commandName,
                $parameterName,
                $wordToComplete,
                $commandAst,
                $fakeBoundParameters )
        # Perform calculation of tab completed values here.
    })]
)
```

### <a name="argumentcompleter-script-block"></a>ArgumentCompleter 스크립트 블록

스크립트 블록 매개 변수는 다음 값으로 설정 됩니다.

- `$commandName` (위치 0)-이 매개 변수는 스크립트 블록에서 탭 완성 기능을 제공 하는 명령 이름으로 설정 됩니다.
- `$parameterName` (위치 1)-이 매개 변수는 값이 탭 완성이 필요한 매개 변수로 설정 됩니다.
- `$wordToComplete` (위치 2)-이 매개 변수는 <kbd>Tab</kbd>키를 누를 때 사용자가 제공한 값으로 설정 됩니다. 스크립트 블록은이 값을 사용 하 여 탭 완성 값을 결정 해야 합니다.
- `$commandAst` (위치 3)-이 매개 변수는 현재 입력 줄에 대 한 AST (추상 구문 트리)로 설정 됩니다. 자세한 내용은 [Ast 클래스](/dotnet/api/system.management.automation.language.ast)를 참조 하세요.
- `$fakeBoundParameters` (위치 4)-이 매개 변수는 `$PSBoundParameters` 사용자가 <kbd>Tab</kbd>키를 눌러 cmdlet에 대 한를 포함 하는 해시 테이블로 설정 됩니다. 자세한 내용은 [about_Automatic_Variables](about_Automatic_Variables.md)를 참조 하세요.

**ArgumentCompleter** 스크립트 블록은 `ForEach-Object` , `Where-Object` 또는 다른 적합 한 메서드와 같이 파이프라인을 사용 하 여 값을 언 롤 해야 합니다.
값의 배열을 반환 하면 PowerShell에서 전체 배열을 **하나의** 탭 완성 값으로 처리 합니다.

다음 예에서는 **값** 매개 변수에 탭 완성 기능을 추가 합니다. **값** 매개 변수만 지정 된 경우 **값** 에 대 한 모든 가능한 값 또는 인수가 표시 됩니다. **형식** 매개 변수를 지정 하면 **값** 매개 변수는 해당 형식에 대 한 가능한 값만 표시 합니다.

또한 `-like` 연산자는 사용자가 다음 명령을 입력 하 고 <kbd>탭</kbd> 완성 기능을 사용 하는 경우에는 **Apple** 만 반환 되도록 합니다.

`Test-ArgumentCompleter -Type Fruits -Value A`

```powershell
function Test-ArgumentCompleter {
[CmdletBinding()]
 param (
        [Parameter(Mandatory=$true)]
        [ValidateSet('Fruits', 'Vegetables')]
        $Type,
        [Parameter(Mandatory=$true)]
        [ArgumentCompleter( {
            param ( $commandName,
                    $parameterName,
                    $wordToComplete,
                    $commandAst,
                    $fakeBoundParameters )

            $possibleValues = @{
                Fruits = @('Apple', 'Orange', 'Banana')
                Vegetables = @('Tomato', 'Squash', 'Corn')
            }
            if ($fakeBoundParameters.ContainsKey('Type'))
            {
                $possibleValues[$fakeBoundParameters.Type] | Where-Object {
                    $_ -like "$wordToComplete*"
                }
            }
            else
            {
                $possibleValues.Values | ForEach-Object {$_}
            }
        } )]
        $Value
      )
}
```

## <a name="see-also"></a>참고 항목

[about_Automatic_Variables](about_Automatic_Variables.md)

[about_Functions](about_Functions.md)

[about_Functions_Advanced](about_Functions_Advanced.md)

[about_Functions_Advanced_Methods](about_Functions_Advanced_Methods.md)

[about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md)

[about_Functions_OutputTypeAttribute](about_Functions_OutputTypeAttribute.md)
