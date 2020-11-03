---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertfrom-string?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-String
ms.openlocfilehash: 665a0ca8332c4052b59362c7947e408ba811c5f2
ms.sourcegitcommit: c4906f4c9fa4ef1a16dcd6dd00ff960d19446d71
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/01/2020
ms.locfileid: "93219794"
---
# ConvertFrom-String

## 개요
문자열 콘텐츠에서 구조화 된 속성을 추출 하 고 구문 분석 합니다.

## SYNTAX

### ByDelimiter (기본값)

```
ConvertFrom-String [-Delimiter <String>] [-PropertyNames <String[]>] [-InputObject] <String>
 [<CommonParameters>]
```

### 템플릿 구문 분석

```
ConvertFrom-String [-TemplateFile <String[]>] [-TemplateContent <String[]>] [-IncludeExtent] [-UpdateTemplate]
 [-InputObject] <String> [<CommonParameters>]
```

## 설명

**Convertfrom-csv** cmdlet은 문자열 콘텐츠에서 구조화 된 속성을 추출 하 고 구문 분석 합니다.
이 cmdlet은 기존 텍스트 스트림에서 텍스트를 구문 분석 하 여 개체를 생성 합니다.
파이프라인의 각 문자열에 대해 cmdlet은 구분 기호 또는 구문 분석 식으로 입력을 분할 한 다음 각 결과 분할 요소에 속성 이름을 할당 합니다.
이러한 속성 이름을 제공할 수 있습니다. 그렇지 않은 경우 자동으로 생성 됩니다.

Cmdlet의 기본 매개 변수 집합 **Bydelimiter** 는 정규식 구분 기호에서 정확 하 게 분할 됩니다.
Cmdlet에서와 같이 따옴표 일치 또는 구분 기호 이스케이프를 수행 하지 않습니다 `Import-Csv` .

Cmdlet의 대체 매개 변수 집합 인 템플릿 **구문 분석** 은 정규식에 의해 캡처된 그룹에서 요소를 생성 합니다. 정규식에 대 한 자세한 내용은 [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md)를 참조 하세요.

이 cmdlet은 기본 구분 구문 분석 및 자동 생성 된 예제 기반 구문 분석의 두 가지 모드를 지원 합니다.

기본적으로 구분 구문 분석에서는 입력을 공백으로 분할하고 결과 그룹에 속성 이름을 할당합니다.

결과를 cmdlet 중 하나로 파이프 하 여 구분 기호를 사용자 지정 `ConvertFrom-String` `Format-*` 하거나 **구분 기호** 매개 변수를 사용할 수 있습니다.

또한이 cmdlet은 [FlashExtract, Microsoft research의 연구 작업](https://www.microsoft.com/research/publication/flashextract-framework-data-extraction-examples/)을 기반으로 자동 생성 된 예제 기반 구문 분석도 지원 합니다.

## 예제

### 예제 1: 기본 속성 이름을 사용 하 여 개체 생성

```powershell
"Hello World" | ConvertFrom-String
```

```Output
P1    P2
--    --
Hello World
```

이 명령은 기본 속성 이름 **P1** 및 **P2** 를 사용 하 여 개체를 생성 합니다.

### 예 1A: 생성 된 개체를 알려면 가져오기

이 명령은 속성이 **P1** , **P2** 인 개체를 하나 생성 합니다. 기본적으로 두 속성은 모두 **문자열** 유형입니다.

```powershell
"Hello World" | ConvertFrom-String | Get-Member
```

```Output

   TypeName: System.Management.Automation.PSCustomObject

Name        MemberType   Definition
----        ----------   ----------
Equals      Method       bool Equals(System.Object obj)
GetHashCode Method       int GetHashCode()
GetType     Method       type GetType()
ToString    Method       string ToString()
P1          NoteProperty string P1=Hello
P2          NoteProperty string P2=World
```

### 예제 2: 구분 기호를 사용 하 여 기본 속성 이름으로 개체 생성

이 명령은 백슬래시 ()를 구분 기호로 사용 하 여 도메인과 사용자 이름을 사용 하 여 개체를 생성 `\` 합니다. 정규식을 사용할 때 백슬래시 문자는 다른 백슬래시로 이스케이프 해야 합니다.

```powershell
"Contoso\Administrator" | ConvertFrom-String -Delimiter "\\"
```

```Output
P1      P2
--      --
Contoso Administrator
```

### 예제 3: 두 개의 명명 된 속성을 포함 하는 개체 생성

다음 예제에서는 Windows 호스트 파일 항목에서 개체를 만듭니다.

```powershell
$content = Get-Content C:\Windows\System32\drivers\etc\hosts
$content = $content -match "^[^#]"
$content | ConvertFrom-String -PropertyNames IP, Server
```

```Output
IP             Server
--             ------
192.168.7.10   W2012R2
192.168.7.20   W2016
192.168.7.101  WIN8
192.168.7.102  WIN10
```

`Get-Content`Cmdlet은에 Windows 호스트 파일의 콘텐츠를 저장 합니다 `$content` . 두 번째 명령은 ()로 시작 하지 않는 줄과 일치 하는 정규식을 사용 하 여 호스트 파일의 시작 부분에 있는 모든 주석을 제거 합니다 `#` . 마지막 명령은 나머지 텍스트를 **서버** 및 **IP** 속성이 있는 개체로 변환 합니다.

### 예 4: 식을 TemplateContent 매개 변수 값으로 사용 하 여 결과를 변수에 저장 합니다.

이 명령은 **TemplateContent** 매개 변수 값으로 식을 사용 합니다.
식은 편의상 변수에 저장 됩니다.
Windows PowerShell은 이제 파이프라인에서 사용 되는 문자열에 `ConvertFrom-String` 세 개의 속성이 있음을 이해 합니다.

- **이름**
- **내선**
- **발전할**

```powershell
$template = @'
{Name*:Phoebe Cat}, {phone:425-123-6789}, {age:6}
{Name*:Lucky Shot}, {phone:(206) 987-4321}, {age:12}
'@

$testText = @'
Phoebe Cat, 425-123-6789, 6
Lucky Shot, (206) 987-4321, 12
Elephant Wise, 425-888-7766, 87
Wild Shrimp, (111)  222-3333, 1
'@

$PersonalData = $testText | ConvertFrom-String -TemplateContent $template
Write-output ("Pet items found: " + ($PersonalData.Count))
$PersonalData
```

```Output
Pet items found: 4

Name          phone           age
----          -----           ---
Phoebe Cat    425-123-6789    6
Lucky Shot    (206) 987-4321  12
Elephant Wise 425-888-7766    87
Wild Shrimp   (111)  222-3333 1
```

입력의 각 줄은 샘플 일치 항목에 의해 평가 됩니다. 줄이 패턴에 지정 된 예제와 일치 하는 경우 값이 추출 되 고 출력 변수에 전달 됩니다.

샘플 데이터는 `$template` 두 가지 다른 전화 형식을 제공 합니다.

- `425-123-6789`
- `(206) 987-4321`

또한 샘플 데이터는 다음과 같은 두 가지 age 형식을 제공 합니다.

- `6`
- `12`

이는 `(206) 987 4321` 하이픈이 없으므로 해당 패턴과 일치 하는 샘플 데이터가 없으므로 전화와 같은 전화를 인식할 수 없음을 의미 합니다.

### 예 5: 생성 된 속성에 데이터 형식 지정

위의 예는 위의 예제 4와 같습니다.
차이점은 패턴 문자열에는 원하는 각 속성에 대 한 데이터 형식이 포함 된다는 것입니다.

```powershell
$template = @'
{[string]Name*:Phoebe Cat}, {[string]phone:425-123-6789}, {[int]age:6}
{[string]Name*:Lucky Shot}, {[string]phone:(206) 987-4321}, {[int]age:12}
'@

$testText = @'
Phoebe Cat, 425-123-6789, 6
Lucky Shot, (206) 987-4321, 12
Elephant Wise, 425-888-7766, 87
Wild Shrimp, (111)  222-3333, 1
'@

$PersonalData = $testText | ConvertFrom-String -TemplateContent $template
Write-output ("Pet items found: " + ($PersonalData.Count))
$PersonalData
```

```Output
Pet items found: 4

Name          phone           age
----          -----           ---
Phoebe Cat    425-123-6789      6
Lucky Shot    (206) 987-4321   12
Elephant Wise 425-888-7766     87
Wild Shrimp   (111)  222-3333   1
```

```powershell
$PersonalData | Get-Member
```

```Output
   TypeName: System.Management.Automation.PSCustomObject

Name        MemberType   Definition
----        ----------   ----------
Equals      Method       bool Equals(System.Object obj)
GetHashCode Method       int GetHashCode()
GetType     Method       type GetType()
ToString    Method       string ToString()
age         NoteProperty int age=6
Name        NoteProperty string Name=Phoebe Cat
phone       NoteProperty string phone=425-123-6789
```

`Get-Member`Cmdlet은 **age** 속성이 정수인 것을 표시 하는 데 사용 됩니다.

## PARAMETERS

### -구분 기호

요소 간의 경계를 식별 하는 정규식을 지정 합니다.
분할에 의해 생성 되는 요소는 결과 개체의 속성이 됩니다.
구분 기호는 궁극적으로 형식의 **Split** 메서드 호출에 사용 됩니다 `[System.Text.RegularExpressions.RegularExpression]` .

```yaml
Type: System.String
Parameter Sets: ByDelimiter
Aliases: DEL

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -IncludeExtent

이 cmdlet은 기본적으로 제거 되는 익스텐트 텍스트 속성을 포함 함을 나타냅니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: TemplateParsing
Aliases: IE

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

파이프라인에서 받은 문자열 또는 문자열 개체를 포함 하는 변수를 지정 합니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -PropertyNames

결과 개체에서 분할 된 값을 할당할 속성 이름의 배열을 지정 합니다.
분할 하거나 구문 분석 하는 모든 텍스트 줄은 속성 값을 나타내는 요소를 생성 합니다.
요소가 캡처 그룹의 결과일 때 해당 캡처 그룹의 이름이 인 경우 (예: `(?<name>)` 또는 `(?'name')` ) 해당 캡처 그룹의 이름이 속성에 할당 됩니다.

**PropertyName** 배열의 요소를 제공 하는 경우 해당 이름이 아직 명명 되지 않은 속성에 할당 됩니다.

필드 수보다 많은 속성 이름을 제공 하는 경우 PowerShell은 추가 속성 이름을 무시 합니다. 모든 필드의 이름을 지정 하는 데 충분 한 속성 이름을 지정 하지 않으면 PowerShell에서 이름이 지정 되지 않은 속성 ( **P1** , **P2** 등)에 숫자 속성 이름을 자동으로 할당 합니다.

```yaml
Type: System.String[]
Parameter Sets: ByDelimiter
Aliases: PN

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TemplateContent

이 cmdlet이 문자열을 할당 하는 속성을 설명 하는 식 또는 변수로 저장 된 식을 지정 합니다. 템플릿 필드 사양의 구문은 `{[optional-typecast]<name>:<example-value>}` 다음과 같습니다.

```yaml
Type: System.String[]
Parameter Sets: TemplateParsing
Aliases: TC

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TemplateFile

문자열의 원하는 구문 분석을 위한 템플릿을 포함 하는 파일을 배열로 지정 합니다.
템플릿 파일에서 속성과 해당 값은 아래와 같이 대괄호로 묶여 있습니다.
속성 (예: **Name** 속성 및 연결 된 다른 속성)이 여러 번 표시 되는 경우 별표 ()를 추가 하 여 `*` 여러 레코드가 생성 되는 것을 나타낼 수 있습니다. 이렇게 하면 여러 속성을 단일 레코드로 추출 하지 않습니다.

```
{Name*:David Chew}
{City:Redmond}, {State:WA}
{Name*:Evan Narvaez}    {Name*:Antonio Moreno}
{City:Issaquah}, {State:WA}
```

```yaml
Type: System.String[]
Parameter Sets: TemplateParsing
Aliases: TF

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UpdateTemplate

이 cmdlet이 학습 알고리즘의 결과를 템플릿 파일의 설명에 저장 함을 나타냅니다.
이렇게 하면 알고리즘 학습 프로세스를 더 빠르게 수행할 수 있습니다.
이 매개 변수를 사용 하려면 템플릿 **파일 매개 변수를 사용** 하 여 템플릿 파일도 지정 해야 합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: TemplateParsing
Aliases: UT

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet은,,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` 및 `-WarningVariable` 등의 일반 매개 변수를 지원 합니다. 자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.

## 입력

### System.String

## 출력

## 참고

## 관련 링크

[Convertfrom-csv-문자열: 예제 기반 텍스트 구문 분석](https://devblogs.microsoft.com/powershell/convertfrom-string-example-based-text-parsing/)

[ConvertFrom-StringData](ConvertFrom-StringData.md)

[ConvertFrom-Csv](ConvertFrom-Csv.md)

[ConvertTo-Xml](ConvertTo-Xml.md)
