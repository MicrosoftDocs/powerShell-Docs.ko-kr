---
title: 확장 형식 시스템 형식 변환기
ms.date: 07/09/2020
ms.openlocfilehash: 0d04293fffde9901ed2e33a9bab21e6612ce9cd5
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786189"
---
# <a name="ets-type-converters"></a>형식 변환기

작업은 메서드를 호출할 때 두 가지 기본 형식의 형식 변환기를 사용 `LanguagePrimitives.ConvertTo(System.Object, System.Type)` 합니다. 이 메서드가 호출 되 면 PowerShell은 표준 PowerShell 언어 변환기 또는 사용자 지정 변환기를 사용 하 여 형식 변환을 수행 하려고 합니다. PowerShell에서 변환을 수행할 수 없는 경우 **PSInvalidCastException** 예외가 throw 됩니다.

## <a name="standard-windows-powershell-language-converters"></a>표준 Windows PowerShell 언어 변환기

이러한 표준 변환은 사용자 지정 변환을 수행 하기 전에 확인 되며 재정의할 수 없습니다. 다음 표에서는 메서드가 호출 될 때 PowerShell에서 수행 하는 형식 변환을 보여 줍니다 `ConvertTo(System.Object, System.Type)` . **Valuetoconvert** 및 **resultType** 매개 변수에 대 한 참조는 메서드의 매개 변수를 참조 합니다 `ConvertTo(System.Object,System.Type)` .

| From (valueToConvert) |  대상 (resultType)  |                                                                               반환                                                                               |
| --------------------- | ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Null                  | String            | ""                                                                                                                                                                  |
| Null                  | Char              | '\0'                                                                                                                                                                |
| Null                  | 숫자           | `0`**resultType** 매개 변수에 지정 된 형식의입니다.                                                                                                          |
| Null                  | 부울           | 메서드에 대 한 호출의 결과입니다 `IsTrue(System.Object)(Null)` .                                                                                                        |
| Null                  | PSObject          | **PSObject**형식의 새 개체입니다.                                                                                                                                    |
| Null                  | 값이 아닌 형식    | N.                                                                                                                                                               |
| Null                  | Nullable &lt; T&gt; | N.                                                                                                                                                               |
| 파생 클래스         | 기본 클래스        | **valueToConvert**                                                                                                                                                  |
| 방해가              | Void              | **AutomationNull. 값**                                                                                                                                            |
| 방해가              | String            | `ToString`메커니즘을 호출 합니다.                                                                                                                                         |
| 방해가              | 부울           | `IsTrue(System.Object) (valueToConvert)`                                                                                                                            |
| 방해가              | PSObject          | 메서드에 대 한 호출의 결과입니다 `AsPSObject(System.Object) (valueToConvert)` .                                                                                         |
| 방해가              | Xml 문서      | **Valuetoconvert** 를 문자열로 변환 하 고 **XMLDocument** 생성자를 호출 합니다.                                                                                      |
| Array                 | Array             | 배열의 각 요소를 변환 하려고 시도 합니다.                                                                                                                      |
| Singleton             | Array             | `Array[0]`배열의 요소 형식으로 변환 **되는 요소 형식으로 변환** 됩니다.                                                                            |
| IDictionary           | 해시 테이블        | Hashtable (valueToConvert) 호출의 결과입니다.                                                                                                                       |
| String                | Char[]            | `valueToConvert.ToCharArray`                                                                                                                                        |
| String                | RegEx             | 에 대 한 호출의 결과입니다 `Regx(valueToConvert)` .                                                                                                                          |
| String                | 형식              | **RunspaceConfiguration**를 검색 하기 위해 **valuetoconvert** 매개 변수를 사용 하 여 적절 한 형식을 반환 합니다.                                                 |
| String                | 숫자           | **Valuetoconvert** 가 "" 인 경우 resultType을 반환 합니다 `0` . **resultType** 그렇지 않으면 문화권 "문화권 고정"을 사용 하 여 숫자 값을 생성 합니다.                       |
| 정수               | System.Enum       | 열거형에서 정수를 정의한 경우 정수를 상수로 변환 합니다. 정수가 정의 되지 않은 경우 **PSInvalidCastException** 예외가 throw 됩니다. |

## <a name="custom-conversions"></a>사용자 지정 변환

PowerShell에서 표준 PowerShell 언어 변환기를 사용 하 여 형식을 변환할 수 없는 경우 사용자 지정 변환기를 확인 합니다. PowerShell은이 섹션에 설명 된 순서 대로 여러 유형의 사용자 지정 변환기를 찾습니다. **Valuetoconvert** 및 **resultType** 매개 변수에 대 한 참조는 메서드의 매개 변수를 참조 합니다 `ConvertTo(System.Object, System.Type)` . 사용자 지정 변환기에서 예외를 throw 하는 경우에는 더 이상 개체를 변환 하지 않고 해당 예외가 **PSInvalidCastException** 예외에 래핑되어 throw 됩니다.

## <a name="powershell-type-converter"></a>PowerShell 유형 변환기

PowerShell 형식 변환기는 **system.enum** 클래스에서 파생 되는 모든 형식과 같이 단일 형식 또는 형식 패밀리를 변환 하는 데 사용 됩니다. PowerShell 형식 변환기를 만들려면 Pstypeconverter와 클래스를 구현 하 고 해당 구현을 대상 클래스와 연결 해야 합니다. PowerShell 형식 변환기를 대상 클래스와 연결 하는 방법에는 두 가지가 있습니다.

- 유형 구성 파일을 통해
- 대상 클래스에 **TypeConverterAttribute** 특성을 적용 하 여

[Pstypeconverter와](/dotnet/api/system.management.automation.pstypeconverter) 추상 클래스에서 파생 된 PowerShell 형식 변환기는 개체를 특정 형식이 나 특정 형식으로 변환 하기 위한 메서드를 제공 합니다. **Valuetoconvert** 매개 변수에 powershell 유형 변환기가 연결 된 개체가 포함 되어 있으면 powershell에서`PSTypeConverter.ConvertTo(System.Object, System.Type,System.IFormatProvider, System.Boolean)`
개체를 **resultType** 매개 변수로 지정 된 형식으로 변환 하는 연결 된 변환기의 메서드입니다. **ResultType** 매개 변수가 powershell 유형 변환기가 연결 된 유형을 참조 하는 경우 powershell은 다음을 호출 합니다.`PSTypeConverter.ConvertFrom(System.Object,System.Type, System.IFormatProvider, System.Boolean)`
**resultType** 매개 변수로 지정 된 형식에서 개체를 변환 하는 연결 된 변환기의 메서드입니다.

## <a name="system-type-converter"></a>시스템 형식 변환기

시스템 형식 변환기는 특정 대상 클래스를 변환 하는 데 사용 됩니다. 이 유형의 변환기는 클래스 패밀리를 변환 하는 데 사용할 수 없습니다. 시스템 형식 변환기를 만들려면 [TypeConverter](/dotnet/api/system.management.automation.runspaces.typedata.typeconverter#System_Management_Automation_Runspaces_TypeData_TypeConverter) 클래스를 구현 하 고 해당 구현을 대상 클래스와 연결 해야 합니다. 시스템 형식 변환기를 대상 클래스와 연결 하는 방법에는 두 가지가 있습니다.

- 유형 구성 파일을 통해
- 대상 클래스에 TypeConverterAttribute 특성을 적용 하 여

## <a name="parse-converter"></a>구문 분석 변환기

**Valuetoconvert** 매개 변수가 문자열이 고 **resultType** 매개 변수의 개체 형식에 `Parse` 메서드가 있으면 메서드를 `Parse` 호출 하 여 문자열을 변환 합니다.

## <a name="constructor-converter"></a>생성자 변환기

**ResultType** 매개 변수의 개체 형식에 **valuetoconvert** 매개 변수의 개체와 동일한 형식의 단일 매개 변수를 포함 하는 생성자가 있는 경우이 생성자가 호출 됩니다.

## <a name="implicit-cast-operator-converter"></a>암시적 캐스트 연산자 변환기

**Valuetoconvert** 매개 변수에 **resultType**으로 변환 되는 암시적 캐스트 연산자가 있는 경우 해당 캐스트 연산자가 호출 됩니다. **ResultType** 매개 변수에 **valuetoconvert**에서 변환 하는 암시적 캐스트 연산자가 있는 경우 해당 캐스트 연산자가 호출 됩니다.

## <a name="explicit-cast-operator-converter"></a>명시적 캐스트 연산자 변환기

**Valuetoconvert** 매개 변수에 **resultType**으로 변환 하는 명시적 캐스트 연산자가 있는 경우 해당 캐스트 연산자가 호출 됩니다. **ResultType** 매개 변수에 **valuetoconvert**에서 변환 하는 명시적 캐스트 연산자가 있는 경우 해당 cast 연산자가 호출 됩니다.
