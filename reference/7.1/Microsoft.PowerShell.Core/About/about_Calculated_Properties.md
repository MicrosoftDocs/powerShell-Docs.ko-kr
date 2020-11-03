---
description: PowerShell은 새 속성을 동적으로 추가 하 고 파이프라인에 대 한 개체 출력의 형식을 변경 하는 기능을 제공 합니다.
Locale: en-US
ms.date: 08/07/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_calculated_properties?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Calculated_Properties
ms.openlocfilehash: 1ecc621d05cb340f6792481df483249095ed63a2
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93224145"
---
# <a name="about-calculated-properties"></a>계산 된 속성 정보

## <a name="short-description"></a>간단한 설명

PowerShell은 새 속성을 동적으로 추가 하 고 파이프라인에 대 한 개체 출력의 형식을 변경 하는 기능을 제공 합니다.

## <a name="long-description"></a>자세한 설명

많은 PowerShell cmdlet이 출력 개체에 새 속성을 추가할 수 있는 매개 변수를 사용 하 여 입력 개체를 출력 개체로 변환, 집계 또는 처리 합니다. 이러한 매개 변수를 사용 하 여 입력 개체의 값을 기반으로 출력 개체에서 계산 된 새 속성을 생성할 수 있습니다.
계산 된 속성은 새 속성의 이름, 값을 계산 하는 식 및 선택적 형식 지정 정보를 지정 하는 키-값 쌍을 포함 하는 [해시 테이블](about_hash_tables.md) 에 의해 정의 됩니다.

## <a name="supported-cmdlets"></a>지원되는 cmdlet

다음 cmdlet은 **property** 매개 변수에 대해 계산 된 속성 값을 지원 합니다. `Format-*`또한이 cmdlet은 **GroupBy** 매개 변수에 대해 계산 된 값을 지원 합니다.

다음 목록에서는 각 cmdlet에서 지 원하는 계산 된 속성 및 키-값 쌍을 지 원하는 cmdlet을 항목별로 요약 합니다.

- `Compare-Object`
  - `expression`

- `ConvertTo-Html`
  - `name`/`label` -선택 사항 (PowerShell 6.x에 추가 됨)
  - `expression`
  - `width` -선택 사항
  - `alignment` -선택 사항

- `Format-Custom`
  - `expression`
  - `depth` -선택 사항

- `Format-List`
  - `name`/`label` -선택 사항
  - `expression`
  - `formatstring` -선택 사항

  이 동일한 키-값 쌍 집합은 모든 cmdlet에 대해 **GroupBy** 매개 변수에 전달 된 계산 된 속성 값에도 적용 `Format-*` 됩니다.

- `Format-Table`
  - `name`/`label` -선택 사항
  - `expression`
  - `formatstring` -선택 사항
  - `width` -선택 사항
  - `alignment` -선택 사항

- `Format-Wide`
  - `expression`
  - `formatstring` -선택 사항

- `Group-Object`
  - `expression`

- `Measure-Object`
  - 는 해시 테이블이 아닌 식에 대 한 스크립트 블록만 지원 합니다.
  - PowerShell 5.1 이상에서는 지원 되지 않습니다.

- `Select-Object`
  - `name`/`label` -선택 사항
  - `expression`

- `Sort-Object`
  - `expression`
  - `ascending`/`descending` -선택 사항

> [!NOTE]
> 의 값은 `expression` hashtable 대신 스크립트 블록이 될 수 있습니다. 자세한 내용은 [참고](#notes) 섹션을 참조 하세요.

## <a name="hashtable-key-definitions"></a>Hashtable 키 정의

- `name`/`label` -만들려는 속성의 이름을 지정 합니다. 또는 해당 별칭 ()을 사용할 수 있습니다 `name` `label` .
- `expression` -새 속성의 값을 계산 하는 데 사용 되는 스크립트 블록입니다.
- `alignment` -열에 값이 표시 되는 방식을 정의 하는 테이블 형식 출력을 생성 하는 cmdlet에서 사용 됩니다. 값은 `'left'` , 또는 여야 합니다 `'center'` `'right'` .
- `formatstring` -출력에 대 한 값의 형식을 지정 하는 방법을 정의 하는 형식 문자열을 지정 합니다. 서식 문자열에 대 한 자세한 내용은 [.net의 서식 형식](/dotnet/standard/base-types/formatting-types)을 참조 하세요.
- `width` -값이 표시 될 때 테이블의 최대 너비 열 수를 지정 합니다. 값은 보다 커야 합니다 `0` .
- `depth` -의 **depth** 매개 변수는 `Format-Custom` 모든 속성에 대 한 확장 수준을 지정 합니다. 키를 사용 하 여 `depth` 속성 당 확장의 깊이를 지정할 수 있습니다.
- `ascending` / `descending` -하나 이상의 속성에 대 한 정렬 순서를 지정할 수 있습니다. 이러한 값은 부울 값입니다.

지정 된 이름 접두사가 명확 하지 않으면 해시 테이블 키의 철자를 지정할 필요가 없습니다. 예를 들어,는 대신 사용할 수 있으며 대신 사용할 수 있습니다 `n` `Name` `e` `Expression` .

## <a name="examples"></a>예

### <a name="compare-object"></a>Compare-Object

계산 된 속성을 사용 하 여 입력 개체의 속성을 비교 하는 방법을 제어할 수 있습니다. 이 예제에서 값을 직접 비교 하는 대신 값을 산술 연산 (2 모듈러스)의 결과와 비교 합니다.

```powershell
Compare-Object @{p=1} @{p=2} -property @{ Expression = { $_.p % 2 } }
```

```Output
 $_.p % 2  SideIndicator
---------- -------------
         0 =>
         1 <=
```

### <a name="convertto-html"></a>ConvertTo-Html

`ConvertTo-Html` 개체의 컬렉션을 HTML 테이블로 변환할 수 있습니다.
계산 된 속성을 사용 하면 테이블이 표시 되는 방식을 제어할 수 있습니다.

```powershell
Get-Alias |
  ConvertTo-Html Name,
                 Definition,
                 @{
                    name='ParameterCount'
                    expr={$_.Parameters.Keys.Count}
                    align='center'
                 } |
    Out-File .\aliases.htm -Force
```

이 예에서는 각 별칭 지정 된 명령에 대 한 PowerShell 별칭 목록과 숫자 매개 변수를 포함 하는 HTML 테이블을 만듭니다. **Parametercount** 열의 값이 가운데에 있습니다.

### <a name="format-custom"></a>Format-Custom

`Format-Custom` 클래스 정의와 유사한 형식으로 개체의 사용자 지정 뷰를 제공 합니다. 더 복잡 한 개체는 복합 형식으로 깊게 중첩 된 멤버를 포함할 수 있습니다. 의 **depth** 매개 변수는 `Format-Custom` 모든 속성에 대 한 확장 수준을 지정 합니다. 키를 사용 하 여 `depth` 속성 당 확장의 깊이를 지정할 수 있습니다.

이 예제에서 `depth` 키는 cmdlet에 대 한 사용자 지정 출력을 단순화 합니다 `Get-Date` . `Get-Date`**DateTime** 개체를 반환 합니다. 또한이 개체의 **Date** 속성은 **DateTime** 개체 이므로 개체가 중첩 됩니다.

```powershell
Get-Date | Format-Custom @{expr={$_.Date};depth=1},TimeOfDay
```

```Output
class DateTime
{
  $_.Date =
    class DateTime
    {
      Date = 8/7/2020 12:00:00 AM
      Day = 7
      DayOfWeek = Friday
      DayOfYear = 220
      Hour = 0
      Kind = Local
      Millisecond = 0
      Minute = 0
      Month = 8
      Second = 0
      Ticks = 637323552000000000
      TimeOfDay = 00:00:00
      Year = 2020
      DateTime = Friday, August 07, 2020 12:00:00 AM
    }
  TimeOfDay =
    class TimeSpan
    {
      Ticks = 435031592302
      Days = 0
      Hours = 12
      Milliseconds = 159
      Minutes = 5
      Seconds = 3
      TotalDays = 0.503508787386574
      TotalHours = 12.0842108972778
      TotalMilliseconds = 43503159.2302
      TotalMinutes = 725.052653836667
      TotalSeconds = 43503.1592302
    }
}
```

### <a name="format-list"></a>Format-List

이 예에서는 계산 된 속성을 사용 하 여 출력의 이름과 형식을 변경 `Get-ChildItem` 합니다.

```powershell
Get-ChildItem *.json -File |
  Format-List Fullname,
              @{
                 name='Modified'
                 expression={$_.LastWriteTime}
                 formatstring='O'
              },
              @{
                 name='Size'
                 expression={$_.Length/1KB}
                 formatstring='N2'
              }
```

```Output
FullName : C:\Git\PS-Docs\PowerShell-Docs\.markdownlint.json
Modified : 2020-07-23T10:26:28.4092457-07:00
Size     : 2.40

FullName : C:\Git\PS-Docs\PowerShell-Docs\.openpublishing.publish.config.json
Modified : 2020-07-23T10:26:28.4092457-07:00
Size     : 2.25

FullName : C:\Git\PS-Docs\PowerShell-Docs\.openpublishing.redirection.json
Modified : 2020-07-27T13:05:24.3887629-07:00
Size     : 324.60
```

### <a name="format-table"></a>Format-Table

이 예제에서 계산 된 속성은 콘텐츠 형식으로 파일을 분류 하는 데 사용 되는 **형식** 속성을 추가 합니다.

```powershell
Get-ChildItem -File |
  Sort-Object extension |
    Format-Table Name, Length -GroupBy @{
      name='Type'
      expression={
        switch ($_.extension) {
          '.md'   {'Content'}
          ''      {'Metacontent'}
          '.ps1'  {'Automation'}
          '.yml'  {'Automation'}
          default {'Configuration'}
        }
      }
    }
```

```Output
   Type: Metacontent

Name              Length
----              ------
ThirdPartyNotices   1229
LICENSE-CODE        1106
LICENSE            19047

   Type: Configuration

Name                                Length
----                                ------
.editorconfig                          183
.gitattributes                         419
.gitignore                             228
.markdownlint.json                    2456
.openpublishing.publish.config.json   2306
.openpublishing.redirection.json    332394
.localization-config                   232

   Type: Content

Name            Length
----            ------
README.md         3355
CONTRIBUTING.md    247

   Type: Automation

Name                      Length
----                      ------
.openpublishing.build.ps1    796
build.ps1                   7495
ci.yml                       645
ci-steps.yml                2035
daily.yml                   1271
```

### <a name="format-wide"></a>Format-Wide

`Format-Wide`Cmdlet을 사용 하면 컬렉션의 개체에 대 한 하나의 속성 값을 여러 열 목록으로 표시할 수 있습니다.

이 예에서는 파일 이름 및 크기 (kb)를 광범위 한 목록으로 표시 하려고 합니다. `Format-Wide`에는 두 개 이상의 속성이 표시 되지 않으므로 계산 된 속성을 사용 하 여 두 속성의 값을 단일 값으로 결합 합니다.

```powershell
Get-ChildItem -File |
  Format-Wide -Property @{e={'{0} ({1:N2}kb)' -f $_.name,($_.length/1kb)}}
```

```Output
.editorconfig (0.18kb)                          .gitattributes (0.41kb)
.gitignore (0.22kb)                             .localization-config (0.23kb)
.markdownlint.json (2.40kb)                     .openpublishing.build.ps1 (0.78kb)
.openpublishing.publish.config.json (2.25kb)    .openpublishing.redirection.json (324.60kb)
build.ps1 (7.32kb)                              ci.yml (0.63kb)
ci-steps.yml (1.99kb)                           CONTRIBUTING.md (0.24kb)
daily.yml (1.24kb)                              LICENSE (18.60kb)
LICENSE-CODE (1.08kb)                           README.md (3.28kb)
ThirdPartyNotices (1.20kb)
```

### <a name="group-object"></a>Group-Object

`Group-Object`Cmdlet은 지정 된 속성의 값을 기준으로 개체를 그룹으로 표시 합니다. 이 예제에서 계산 된 속성은 각 콘텐츠 형식의 파일 수를 계산 합니다.

```powershell
Get-ChildItem -File |
  Sort-Object extension |
    Group-Object -NoElement -Property @{
      expression={
        switch ($_.extension) {
          '.md'   {'Content'}
          ''      {'Metacontent'}
          '.ps1'  {'Automation'}
          '.yml'  {'Automation'}
          default {'Configuration'}
        }
      }
    }
```

```Output
Count Name
----- ----
    5 Automation
    7 Configuration
    2 Content
    3 Metacontent
```

### <a name="measure-object"></a>Measure-Object

`Measure-Object`Cmdlet은 개체의 숫자 속성을 계산 합니다. 이 예에서는 계산 된 속성을 사용 하 여 3으로 균등 하 게 나눌 수 있는 숫자 ( **합계** )를 1에서 10 사이에서 가져옵니다.

```powershell
1..10 | Measure-Object -Property {($_ % 3) -eq 0} -Sum
```

```Output
Count             : 10
Average           :
Sum               : 3
Maximum           :
Minimum           :
StandardDeviation :
Property          : ($_ % 3) -eq 0
```

> [!NOTE]
> 다른 cmdlet과 달리는 `Measure-Object` 계산 된 속성에 대 한 해시 테이블을 허용 하지 않습니다. 스크립트 블록을 사용 해야 합니다.

### <a name="select-object"></a>Select-Object

계산 된 속성을 사용 하 여 cmdlet을 통해 개체 출력에 멤버를 더 추가할 수 있습니다 `Select-Object` . 이 예제에서는 문자로 시작 하는 PowerShell 별칭을 나열 합니다 `C` . 를 사용 하 여 `Select-Object` 별칭, 별칭이 매핑된 cmdlet 및 cmdlet에 대해 정의 된 매개 변수의 개수를 출력 합니다. 계산 된 속성을 사용 하 여 **Parametercount** 속성을 만들 수 있습니다.

```powershell
$aliases = Get-Alias c* |
  Select-Object Name,
                Definition,
                @{
                    name='ParameterCount'
                    expr={$_.Parameters.Keys.Count}
                }
$aliases | Get-Member
$aliases
```

```Output
   TypeName: Selected.System.Management.Automation.AliasInfo

Name           MemberType   Definition
----           ----------   ----------
Equals         Method       bool Equals(System.Object obj)
GetHashCode    Method       int GetHashCode()
GetType        Method       type GetType()
ToString       Method       string ToString()
Definition     NoteProperty string Definition=Get-Content
Name           NoteProperty string Name=cat
ParameterCount NoteProperty System.Int32 ParameterCount=21

Name    Definition         ParameterCount
----    ----------         --------------
cat     Get-Content                    21
cd      Set-Location                   15
cdd     Push-MyLocation                 1
chdir   Set-Location                   15
clc     Clear-Content                  20
clear   Clear-Host                      0
clhy    Clear-History                  17
cli     Clear-Item                     20
clp     Clear-ItemProperty             22
cls     Clear-Host                      0
clv     Clear-Variable                 19
cnsn    Connect-PSSession              29
compare Compare-Object                 20
copy    Copy-Item                      24
cp      Copy-Item                      24
cpi     Copy-Item                      24
cpp     Copy-ItemProperty              23
cvpa    Convert-Path                   13
```

### <a name="sort-object"></a>Sort-Object

계산 된 속성을 사용 하 여 속성 마다 다른 순서로 데이터를 정렬할 수 있습니다. 이 예에서는 CSV 파일의 데이터를 **날짜별** 로 오름차순으로 정렬 합니다. 그러나 각 날짜 내에서 행을 **UnitsSold** 기준으로 내림차순으로 정렬 합니다.

```powershell
Import-Csv C:\temp\sales-data.csv |
  Sort-Object Date, @{expr={$_.UnitsSold}; desc=$true}, Salesperson  |
    Select-Object Date, Salesperson, UnitsSold
```

```Output
Date       Salesperson UnitsSold
----       ----------- ---------
2020-08-01 Sally       3
2020-08-01 Anne        2
2020-08-01 Fred        1
2020-08-02 Anne        6
2020-08-02 Fred        2
2020-08-02 Sally       0
2020-08-03 Anne        5
2020-08-03 Sally       3
2020-08-03 Fred        1
2020-08-04 Anne        2
2020-08-04 Fred        2
2020-08-04 Sally       2
```

## <a name="notes"></a>메모

- 식 스크립트 블록을 _directly_ `Expression` 해시 테이블의 항목으로 지정 하는 대신 인수로 직접 지정할 수 있습니다. 다음은 그 예입니다. 

  ```powershell
  '1', '10', '2' | Sort-Object { [int] $_ }
  ```

  이 예제는,, 등의 키를 통해 속성 이름을 지정 하지 않거나 지원 하지 않는 cmdlet에 편리 `Name` `Sort-Object` `Group-Object` `Measure-Object` 합니다.

  속성 이름 지정을 지 원하는 cmdlet의 경우 스크립트 블록은 문자열로 변환 되 고 출력에서 속성의 이름으로 사용 됩니다.

- `Expression` 스크립트 블록은 _자식_ 범위에서 실행 됩니다. 즉, 호출자의 변수를 직접 수정할 수 없습니다.

- 파이프라인 논리는 스크립트 블록의 출력에 적용 됩니다 `Expression` . 즉, 단일 요소 배열을 출력 하면 해당 배열이 래핑 해제 됩니다.

- 대부분의 cmdlet에서 식 스크립트 블록 내의 오류는 자동으로 무시 됩니다.
  `Sort-Object`에서 문 종료 및 스크립트 종료 오류는 _출력_ 이지만 문을 종료 하지 않습니다.

## <a name="see-also"></a>참고 항목

[about_Hash_Tables](about_hash_tables.md)

[Compare-Object](xref:Microsoft.PowerShell.Utility.Compare-Object)

[ConvertTo-Html](xref:Microsoft.PowerShell.Utility.ConvertTo-Html)

[Format-Custom](xref:Microsoft.PowerShell.Utility.Format-Custom)

[Format-List](xref:Microsoft.PowerShell.Utility.Format-List)

[Format-Table](xref:Microsoft.PowerShell.Utility.Format-Table)

[Format-Wide](xref:Microsoft.PowerShell.Utility.Format-Wide)

[Group-Object](xref:Microsoft.PowerShell.Utility.Group-Object)

[Measure-Object](xref:Microsoft.PowerShell.Utility.Measure-Object)

[Select-Object](xref:Microsoft.PowerShell.Utility.Select-Object)

[Sort-Object](xref:Microsoft.PowerShell.Utility.Sort-Object)

[.NET의 형식 유형](/dotnet/standard/base-types/formatting-types)
