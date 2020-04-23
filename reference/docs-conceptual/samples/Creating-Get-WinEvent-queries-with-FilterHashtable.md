---
ms.date: 09/13/2019
title: FilterHashtable를 사용하여 Get-WinEvent 쿼리 만들기
ms.openlocfilehash: 35d18dc894d90e698b38395b79ff4cf395515909
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2020
ms.locfileid: "73444393"
---
# <a name="creating-get-winevent-queries-with-filterhashtable"></a>FilterHashtable를 사용하여 Get-WinEvent 쿼리 만들기

2014년 6월 3일 자 원본 **Scripting Guy** 블로그 게시물을 읽으려면 [FilterHashTable을 사용하여 PowerShell을 통해 이벤트 로그 필터링](https://devblogs.microsoft.com/scripting/use-filterhashtable-to-filter-event-log-with-powershell/)을 참조하세요.

이 문서는 원래 블로그 게시물의 일부로, `Get-WinEvent` cmdlet의 **FilterHashtable** 매개 변수를 사용하여 이벤트 로그를 필터링하는 방법을 설명합니다. PowerShell의 `Get-WinEvent` cmdlet은 Windows 이벤트 및 진단 로그를 필터링하는 강력한 방법입니다. `Get-WinEvent` 쿼리가 **FilterHashtable** 매개 변수를 사용하면 성능이 개선됩니다.

대규모 이벤트 로그를 사용할 경우 개체를 파이프라인 아래로 보내 `Where-Object` 명령으로 전달하는 것은 효율적이지 않습니다. PowerShell 6 이전에는 `Get-EventLog` cmdlet이 로그 데이터를 가져오는 또 다른 옵션으로 사용되었습니다. 예를 들어, 다음 명령은 **Microsoft-Windows-Defrag** 로그를 필터링하는 데 비효율적입니다.

```powershell
Get-EventLog -LogName Application | Where-Object Source -Match defrag

Get-WinEvent -LogName Application | Where-Object { $_.ProviderName -Match 'defrag' }
```

다음 명령은 성능을 향상시키는 해시 테이블을 사용합니다.

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='*defrag'
}
```

## <a name="blog-posts-about-enumeration"></a>열거형에 관한 블로그 게시물

이 문서에서는 해시 테이블의 열거된 값을 사용하는 방법에 대한 정보를 제공합니다. 열거형에 대한 자세한 내용은 **Scripting Guy** 블로그 게시물을 읽어보세요. 열거된 값을 반환하는 함수를 만들려면 [열거형 및 값](https://devblogs.microsoft.com/scripting/hey-scripting-guy-weekend-scripter-enumerations-and-values)을 참조하세요.
자세한 내용은 [열거형에 대한 Scripting Guy 블로그 게시물 시리즈](https://devblogs.microsoft.com/scripting/?s=about+enumeration)를 참조하세요.

## <a name="hash-table-key-value-pairs"></a>해시 테이블 키-값 쌍

효율적인 쿼리를 작성하려면 `Get-WinEvent` cmdlet과 **FilterHashtable** 매개 변수를 함께 사용합니다.
**FilterHashtable**은 Windows 이벤트 로그에서 특정 정보를 가져오기 위한 필터로 해시 테이블을 사용합니다. 해시 테이블은 **키-값** 쌍을 사용합니다. 해시 테이블에 대한 자세한 내용은 [about_Hash_Tables](/powershell/module/microsoft.powershell.core/about/about_hash_tables)를 참조하세요.

**키-값** 쌍이 같은 줄에 있으면 세미콜론으로 구분해야 합니다. 각 **키-값** 쌍이 서로 다른 줄에 있으면 세미콜론이 필요하지 않습니다. 예를 들어 이 문서에서는 **키-값** 쌍을 서로 다른 줄에 배치하며 세미콜론을 사용하지 않습니다.

이 샘플에서는 몇 가지 **FilterHashtable** 매개 변수의 **키-값** 쌍을 사용합니다. 완료된 쿼리에는 **LogName**, **ProviderName**, **Keywords**, **ID** 및 **Level**이 포함됩니다.

허용되는 **키-값** 쌍은 다음 표에 표시되며 [Get-WinEvent](/powershell/module/microsoft.powershell.diagnostics/Get-WinEvent)
**FilterHashtable** 매개 변수에 대한 설명서에 포함되어 있습니다.

다음 표는 키 이름, 데이터 형식, 데이터 값에 대해 와일드카드 문자가 허용되는지 여부를 표시합니다.

|    키 이름    | 값 데이터 형식 | 와일드카드 문자 허용 여부 |
| -------------- | --------------- | ---------------------------- |
| LogName        | `<String[]>`    | 예                          |
| ProviderName   | `<String[]>`    | 예                          |
| 경로           | `<String[]>`    | 예                           |
| 키워드       | `<Long[]>`      | 예                           |
| ID             | `<Int32[]>`     | 예                           |
| Level          | `<Int32[]>`     | 예                           |
| StartTime      | `<DateTime>`    | 예                           |
| EndTime        | `<DateTime>`    | 예                           |
| UserID         | `<SID>`         | 예                           |
| 데이터           | `<String[]>`    | 예                           |
| `<named-data>` | `<String[]>`    | 예                           |

`<named-data>` 키는 명명된 이벤트 데이터 필드를 나타냅니다. 예를 들어, Perflib 이벤트 1008은 다음 이벤트 데이터를 포함할 수 있습니다.

```xml
<EventData>
  <Data Name="Service">BITS</Data>
  <Data Name="Library">C:\Windows\System32\bitsperf.dll</Data>
  <Data Name="Win32Error">2</Data>
</EventData>
```

이러한 이벤트를 다음 명령을 사용하여 쿼리할 수 있습니다.

```powershell
Get-WinEvent -FilterHashtable @{LogName='Application'; 'Service'='Bits'}
```

> [!NOTE]
> `<named-data>`를 쿼리할 수 있는 기능이 PowerShell 6에 추가되었습니다.

## <a name="building-a-query-with-a-hash-table"></a>해시 테이블을 사용하여 쿼리 작성

결과를 확인하고 문제를 해결하려는 경우 **키-값** 쌍을 한 번에 하나씩 사용해서 해시 테이블을 빌드하는 것이 좋습니다. 쿼리는 **애플리케이션** 로그에서 데이터를 가져옵니다. 해시 테이블은 `Get-WinEvent –LogName Application`과 같습니다.

시작하려면 `Get-WinEvent` 쿼리를 만듭니다. **FilterHashtable** 매개 변수의 **키-값** 쌍(키: **LogName**, 값: **Application**)을 사용합니다.

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
}
```

**ProviderName** 키를 사용해서 해시 테이블을 계속 작성합니다. **ProviderName**은 **Windows 이벤트 뷰어**의 **원본** 필드에 표시되는 이름입니다. 예를 들어, 다음 스크린샷에서 **.NET Runtime**입니다.

![Windows 이벤트 뷰어 원본 이미지](./media/creating-get-winEvent-queries-with-filterhashtable/providername.png)

해시 테이블을 업데이트하고 **키-값** 쌍(키: **ProviderName, 값: **.NET Runtime**)을 포함합니다.

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
}
```

보관된 이벤트 로그에서 데이터를 가져오는 쿼리가 필요한 경우 **Path** 키를 사용합니다. **Path** 값은 로그 파일에 전체 경로를 지정합니다. 자세한 내용은 **Scripting Guy** 블로그 게시물, [PowerShell을 사용하여 저장된 이벤트 로그에 오류가 있는지 구문 분석](https://devblogs.microsoft.com/scripting/use-powershell-to-parse-saved-event-logs-for-errors)을 참조하세요.

## <a name="using-enumerated-values-in-a-hash-table"></a>해시 테이블에서 열거된 값 사용

**Keywords**는 해시 테이블의 다음 키입니다. **Keywords** 데이터 형식은 큰 숫자를 포함하는 `[long]` 값 형식의 배열입니다. 다음 명령을 사용하여 `[long]`의 최대 값을 찾습니다.

```powershell
[long]::MaxValue
```

```Output
9223372036854775807
```

**Keywords** 키의 경우 PowerShell은 **Security**와 같은 문자열이 아니라 숫자를 사용합니다. **Windows 이벤트 뷰어**는 **Keywords**를 문자열로 표시하지만 열거형 값입니다. 해시 테이블에서 문자열 값에 **Keywords** 키를 사용하면 오류 메시지가 표시됩니다.

**Windows 이벤트 뷰어**를 열고 **작업** 창에서 **현재 로그 필터링**을 클릭합니다.
**Keywords** 드롭다운 메뉴는 다음 스크린샷에 표시된 것처럼 사용할 수 있는 키워드를 표시합니다.

![Windows 이벤트 뷰어 Keywords의 이미지입니다.](./media/creating-get-winEvent-queries-with-filterhashtable/keywords.png)

다음 명령을 사용하여 `StandardEventKeywords` 속성 이름을 표시합니다.

```powershell
[System.Diagnostics.Eventing.Reader.StandardEventKeywords] | Get-Member -Static -MemberType Property
```

```Output
   TypeName: System.Diagnostics.Eventing.Reader.StandardEventKeywords
Name             MemberType Definition
—-             ———- ———-
AuditFailure     Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
AuditSuccess     Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
CorrelationHint  Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
CorrelationHint2 Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
EventLogClassic  Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
None             Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
ResponseTime     Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
Sqm              Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
WdiContext       Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
WdiDiagnostic    Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
```

열거형 값은 **.NET Framework**에 설명되어 있습니다. 자세한 내용은 [StandardEventKeywords 열거형](/dotnet/api/system.diagnostics.eventing.reader.standardeventkeywords?redirectedfrom=MSDN&view=netframework-4.7.2)을 참조하세요.

**Keywords** 이름 및 열거형 값은 다음과 같습니다.

| 속성             |  값            |
| ---------------- | ------------------|
| AuditFailure     | 4503599627370496  |
| AuditSuccess     | 9007199254740992  |
| CorrelationHint2 | 18014398509481984 |
| EventLogClassic  | 36028797018963968 |
| Sqm              | 2251799813685248  |
| WdiDiagnostic    | 1125899906842624  |
| WdiContext       | 562949953421312   |
| ResponseTime     | 281474976710656   |
| None             | 0                 |

해시 테이블을 업데이트하고 **키-값** 쌍(키: **Keywords** 및 **EventLogClassic** 열거형 값, **36028797018963968** )을 포함합니다.

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
}
```

### <a name="keywords-static-property-value-optional"></a>Keywords 정적 속성 값(선택 사항)

**Keywords** 키는 열거형이지만 해시 테이블 쿼리에서 정적 속성 이름을 사용할 수 있습니다.
반환된 문자열을 사용하는 대신, 속성 이름을 **Value__** 속성을 갖는 값으로 변환해야 합니다.

예를 들어, 다음 스크립트는 **Value__** 속성을 사용합니다.

```powershell
$C = [System.Diagnostics.Eventing.Reader.StandardEventKeywords]::EventLogClassic
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=$C.Value__
}
```

## <a name="filtering-by-event-id"></a>이벤트 ID 기준으로 필터링

보다 구체적인 데이터를 가져오기 위해 쿼리 결과가 **이벤트 ID**를 기준으로 필터링됩니다. **이벤트 ID**는 해시 테이블에서 키 **ID**로 참조되고 해당 값은 특정 **이벤트 ID**입니다. **Windows 이벤트 뷰어**는 **이벤트 ID**를 표시합니다. 이 예제에서는 **이벤트 ID 1023**을 사용합니다.

해시 테이블을 업데이트하고 **키-값** 쌍(키: **ID**, 값: **1023**)을 포함합니다.

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
}
```

## <a name="filtering-by-level"></a>수준 기준 필터링

결과를 구체화하고 오류가 있는 이벤트만 포함하려면 **Level** 키를 사용합니다.
**Windows 이벤트 뷰어**는 **Level**을 문자열 값으로 표시하지만, 열거형 값입니다. 해시 테이블에서 문자열 값에 **Level** 키를 사용하면 오류 메시지가 표시됩니다.

**Level**에는 **Error**, **Warning** 또는 **Informational**과 같은 값이 지정됩니다. 다음 명령을 사용하여 `StandardEventLevel` 속성 이름을 표시합니다.

```powershell
[System.Diagnostics.Eventing.Reader.StandardEventLevel] | Get-Member -Static -MemberType Property
```

```Output
   TypeName: System.Diagnostics.Eventing.Reader.StandardEventLevel

Name          MemberType Definition
----          ---------- ----------
Critical      Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Critical {get;}
Error         Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Error {get;}
Informational Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Informational {get;}
LogAlways     Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel LogAlways {get;}
Verbose       Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Verbose {get;}
Warning       Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Warning {get;}
```

열거형 값은 **.NET Framework**에 설명되어 있습니다. 자세한 내용은 [StandardEventLevel 열거형](/dotnet/api/system.diagnostics.eventing.reader.standardeventlevel?redirectedfrom=MSDN&view=netframework-4.7.2)을 참조하세요.

**Level** 키의 이름 및 열거형 값은 다음과 같습니다.

| 속성           | 값 |
| -------------- | ----- |
| 자세히        |   5   |
| 정보 제공  |   4   |
| Warning        |   3   |
| Error          |   2   |
| 위험       |   1   |
| LogAlways      |   0   |

완료된 쿼리에 대한 해시 테이블은 키, **Level** 및 값, **2**를 포함합니다.

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
   Level=2
}
```

### <a name="level-static-property-in-enumeration-optional"></a>열거형의 Level 정적 속성(선택 사항)

**Level** 키는 열거형이지만 해시 테이블 쿼리에서 정적 속성 이름을 사용할 수 있습니다.
반환된 문자열을 사용하는 대신, 속성 이름을 **Value__** 속성을 갖는 값으로 변환해야 합니다.

예를 들어, 다음 스크립트는 **Value__** 속성을 사용합니다.

```powershell
$C = [System.Diagnostics.Eventing.Reader.StandardEventLevel]::Informational
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
   Level=$C.Value__
}
```