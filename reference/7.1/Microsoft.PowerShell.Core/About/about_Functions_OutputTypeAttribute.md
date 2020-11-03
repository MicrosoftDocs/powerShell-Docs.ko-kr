---
description: 함수가 반환하는 개체의 형식을 보고하는 특성에 대해 설명합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_functions_outputtypeattribute?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Functions_OutputTypeAttribute
ms.openlocfilehash: 7cd7f04941077d823bb15d0fa393ca241f38ae3b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93220466"
---
# <a name="about-functions-outputtypeattribute"></a>함수 OutputTypeAttribute 정보

## <a name="short-description"></a>간단한 설명
함수가 반환하는 개체의 형식을 보고하는 특성에 대해 설명합니다.

## <a name="long-description"></a>자세한 설명

OutputType 특성은 함수가 반환 하는 .NET 형식의 개체를 나열 합니다. 선택적 ParameterSetName 매개 변수를 사용 하 여 각 매개 변수 집합에 대해 서로 다른 출력 형식을 나열할 수 있습니다.

OutputType 특성은 단순 함수와 고급 함수에서 지원 됩니다. CmdletBinding 특성에 독립적입니다.

OutputType 특성은 cmdlet이 반환 하는 **system.object** 개체의 OutputType 속성 값을 제공 합니다 `Get-Command` .

OutputType 특성 값은 문서 참고일뿐입니다. 함수 코드에서 파생 되거나 실제 함수 출력과 비교 되지 않습니다. 따라서 값이 정확 하지 않을 수 있습니다.

## <a name="syntax"></a>SYNTAX

함수의 OutputType 특성에는 다음 구문이 있습니다.

```
[OutputType([<TypeLiteral>], ParameterSetName="<Name>")]
[OutputType("<TypeNameString>", ParameterSetName="<Name>")]
```

**ParameterSetName** 매개 변수는 선택 사항입니다.

OutputType 특성에 여러 형식을 나열할 수 있습니다.

```
[OutputType([<Type1>],[<Type2>],[<Type3>])]
```

**ParameterSetName** 매개 변수를 사용 하 여 서로 다른 매개 변수 집합이 다른 형식을 반환 함을 나타낼 수 있습니다.

```
[OutputType([<Type1>], ParameterSetName=("<Set1>","<Set2>"))]
[OutputType([<Type2>], ParameterSetName="<Set3>")]
```

문 앞에 오는 특성 목록에 OutputType 특성 문을 추가 `Param` 합니다.

다음 예에서는 간단한 함수에서 OutputType 특성을 배치 하는 방법을 보여 줍니다.

```powershell
function SimpleFunction2
{
  [OutputType([<Type>])]
  Param ($Parameter1)

  <function body>
}
```

다음 예에서는 고급 함수에서 OutputType 특성을 배치 하는 방법을 보여 줍니다.

```powershell
function AdvancedFunction1
{
  [OutputType([<Type>])]
  Param (
    [parameter(Mandatory=$true)]
    [String[]]
    $Parameter1
  )

  <function body>
}

function AdvancedFunction2
{
  [CmdletBinding(SupportsShouldProcess=<Boolean>)]
  [OutputType([<Type>])]
  Param (
    [parameter(Mandatory=$true)]
    [String[]]
    $Parameter1
  )

  <function body>
}
```

## <a name="examples"></a>예제

### <a name="example-1-create-a-function-that-has-the-outputtype-of-string"></a>예제 1: 문자열의 OutputType을 포함 하는 함수 만들기

```powershell
function Send-Greeting
{
  [OutputType([String])]
  Param ($Name)

  "Hello, $Name"
}
```

결과 출력 형식 속성을 보려면 cmdlet을 사용 합니다 `Get-Command` .

```powershell
(Get-Command Send-Greeting).OutputType
```

```Output
Name                                               Type
----                                               ----
System.String                                      System.String
```

### <a name="example-2-use-the-output-attribute-to-indicate-dynamic-output-types"></a>예제 2: 출력 특성을 사용 하 여 동적 출력 형식 표시

다음 고급 함수는 OutputType 특성을 사용 하 여 함수가 함수 명령에 사용 되는 매개 변수 집합에 따라 다른 형식을 반환 함을 표시 합니다.

```powershell
function Get-User
{
  [CmdletBinding(DefaultParameterSetName="ID")]

  [OutputType("System.Int32", ParameterSetName="ID")]
  [OutputType([String], ParameterSetName="Name")]

  Param (
    [parameter(Mandatory=$true, ParameterSetName="ID")]
    [Int[]]
    $UserID,

    [parameter(Mandatory=$true, ParameterSetName="Name")]
    [String[]]
    $UserName
  )

  <function body>
}
```

### <a name="example-3-shows-when-an-actual-output-differs-from-the-outputtype"></a>예제 3: 실제 출력이 OutputType과 다를 때 표시

다음 예에서는 출력 유형 속성 값이 잘못 된 경우에도 OutputType 특성의 값을 표시 하는 방법을 보여 줍니다.

`Get-Time`함수는 DateTime 개체의 짧은 시간 형식을 포함 하는 문자열을 반환 합니다. 그러나 OutputType 특성은 **system.web** 개체를 반환 한다는 것을 보고 합니다.

```powershell
function Get-Time
{
  [OutputType([DateTime])]
  Param (
    [parameter(Mandatory=$true)]
    [Datetime]$DateTime
  )

  $DateTime.ToShortTimeString()
}
```

`GetType()`메서드는 함수가 문자열을 반환 하는지 확인 합니다.

```powershell
(Get-Time -DateTime (Get-Date)).GetType().FullName
```

```Output
System.String
```

그러나 outputtype 특성에서 값을 가져오는 OutputType 속성은 함수가 **DateTime** 개체를 반환 하는지 보고 합니다.

```powershell
(Get-Command Get-Time).OutputType
```

```Output
Name                                      Type
----                                      ----
System.DateTime                           System.DateTime
```

### <a name="example-4-a-function--that-shouldnt-have-output"></a>예제 4: 출력이 없어야 하는 함수

다음 예제에서는 및 동작을 수행 하지만 아무것도 반환 하지 않는 사용자 지정 함수를 보여 줍니다.

```powershell
function Invoke-Notepad
{
  [OutputType([System.Void])]
  Param ()
  & notepad.exe | Out-Null
}
```

## <a name="notes"></a>참고

**Functioninfo** 개체의 OutputType 속성 값은 각각 Name 및 Type 속성을 가지는 **PSTypeName** 개체의 배열입니다.

각 출력 형식의 이름만 가져오려면 다음 형식의 명령을 사용 합니다.

```powershell
(Get-Command Get-Time).OutputType | ForEach {$_.Name}
```

OutputType 속성의 값은 null 일 수 있습니다. **WMI** 개체 또는 개체의 형식이 지정 된 뷰와 같이 출력이 .net 형식이 아닌 경우 null 값을 사용 합니다.

## <a name="see-also"></a>참고 항목

[about_Functions](about_Functions.md)

[about_Functions_Advanced](about_Functions_Advanced.md)

[about_Functions_Advanced_Methods](about_Functions_Advanced_Methods.md)

[about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)

[about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md)

