---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertto-html?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-Html
ms.openlocfilehash: 21ef51476ccee8efc5c7c13d273ef8a7811f33c4
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/10/2020
ms.locfileid: "93219265"
---
# ConvertTo-Html

## 개요
.NET 개체를 웹 브라우저에 표시할 수 있는 HTML로 변환합니다.

## SYNTAX

### 페이지 (기본값)

```
ConvertTo-Html [-InputObject <PSObject>] [[-Property] <Object[]>] [[-Body] <String[]>]
 [[-Head] <String[]>] [[-Title] <String>] [-As <String>] [-CssUri <Uri>] [-PostContent <String[]>]
 [-PreContent <String[]>] [-Meta <Hashtable>] [-Charset <String>] [-Transitional]
 [<CommonParameters>]
```

### Fragment

```
ConvertTo-Html [-InputObject <PSObject>] [[-Property] <Object[]>] [-As <String>] [-Fragment]
 [-PostContent <String[]>] [-PreContent <String[]>] [<CommonParameters>]
```

## 설명

`ConvertTo-Html`Cmdlet은 .net 개체를 웹 브라우저에 표시할 수 있는 HTML로 변환 합니다. 이 cmdlet을 사용하여 명령 출력을 웹 페이지에 표시할 수 있습니다.

의 매개 변수를 사용 하 여 `ConvertTo-Html` 개체 속성을 선택 하 고, 테이블 또는 목록 형식을 지정 하 고, HTML 페이지 제목을 지정 하 고, 개체 앞뒤에 텍스트를 추가 하 고, STRICT DTD 페이지 대신 테이블 또는 목록 조각만 반환할 수 있습니다.

에 여러 개체를 제출 하는 경우 `ConvertTo-Html` PowerShell은 제출한 첫 번째 개체의 속성을 기반으로 테이블 (또는 목록)을 만듭니다. 나머지 개체에 지정한 속성이 하나도 없을 경우 해당 개체의 속성 값은 빈 셀이 됩니다. 나머지 개체에 추가 속성이 있을 경우 이러한 속성 값은 파일에 포함되지 않습니다.

## 예제

### 예제 1: 날짜를 표시 하는 웹 페이지 만들기

```powershell
ConvertTo-Html -InputObject (Get-Date)
```

이 명령은 현재 날짜의 속성을 표시하는 HTML 페이지를 만듭니다. **InputObject** 매개 변수를 사용 하 여 명령의 결과를 `Get-Date` cmdlet에 제출 `ConvertTo-Html` 합니다.

### 예제 2: PowerShell 별칭을 표시 하는 웹 페이지 만들기

```powershell
Get-Alias | ConvertTo-Html | Out-File aliases.htm
Invoke-Item aliases.htm
```

이 명령은 현재 콘솔의 PowerShell 별칭을 나열 하는 HTML 페이지를 만듭니다.

이 명령은 cmdlet을 사용 하 여 `Get-Alias` 별칭을 가져옵니다. 파이프라인 연산자 ()를 사용 하 여 `|` 별칭을 cmdlet으로 보내면이 `ConvertTo-Html` CMDLET이 HTML 페이지를 만듭니다. 또한이 명령은 cmdlet을 사용 하 여 `Out-File` HTML 코드를 파일에 보냅니다 `aliases.htm` .

### 예제 3: PowerShell 이벤트를 표시 하는 웹 페이지 만들기

```powershell
`Get-EventLog` -LogName "Windows PowerShell" | ConvertTo-Html | Out-File pslog.htm
```

이 명령은 `pslog.htm` 로컬 컴퓨터의 Windows PowerShell 이벤트 로그에 이벤트를 표시 하는 이라는 HTML 페이지를 만듭니다.

Cmdlet을 사용 하 여 `Get-EventLog` Windows PowerShell 로그의 이벤트를 가져온 다음 파이프라인 연산자 ()를 사용 하 여 `|` 이벤트를 cmdlet으로 보냅니다 `ConvertTo-Html` . 또한이 명령은 cmdlet을 사용 하 여 `Out-File` HTML 코드를 파일에 보냅니다 `pslog.htm` .

또한이 명령은 cmdlet을 사용 하 여 `Out-File` HTML 코드를 파일에 보냅니다 `pslog.htm` .

### 예제 4: 프로세스를 표시 하는 웹 페이지 만들기

```powershell
Get-Process |
  ConvertTo-Html -Property Name, Path, Company -Title "Process Information" |
    Out-File proc.htm
Invoke-Item proc.htm
```

이 명령은 로컬 컴퓨터에 있는 프로세스의 이름, 경로 및 회사를 나열하는 HTML 페이지를 만들어서 엽니다.

첫 번째 명령은 cmdlet을 사용 하 여 `Get-Process` 컴퓨터에서 실행 중인 프로세스를 나타내는 개체를 가져옵니다. 이 명령은 파이프라인 연산자 ()를 사용 하 여 `|` 프로세스 개체를 cmdlet으로 보냅니다 `ConvertTo-Html` .

이 명령은 **Property** 매개 변수를 사용 하 여 테이블에 포함할 프로세스 개체의 세 가지 속성을 선택 합니다. 이 명령은 **title** 매개 변수를 사용 하 여 HTML 페이지의 제목을 지정 합니다. 또한이 명령은 cmdlet을 사용 하 여 `Out-File` 결과 HTML을 Proc.htm 이라는 파일로 보냅니다.

두 번째 명령은 cmdlet을 사용 하 여 `Invoke-Item` 를 `Proc.htm` 기본 브라우저에서 엽니다.

### 예 5: 서비스 개체를 표시 하는 웹 페이지 만들기

```powershell
Get-Service | ConvertTo-Html -CssUri "test.css"
```

```Output
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"  "https://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html>
<head>
<title>HTML TABLE</title>
<link rel="stylesheet" type="text/css" href="test.css" />
...
```

이 명령은 cmdlet이 반환 하는 서비스 개체의 HTML 페이지를 만듭니다 `Get-Service` . 이 명령은 **CssUri** 매개 변수를 사용 하 여 HTML 페이지의 css 스타일 시트를 지정 합니다.

**CssUri** 매개 변수는 `<link rel="stylesheet" type="text/css" href="test.css">` 결과 HTML에 추가 태그를 추가 합니다. 태그의 HREF 특성에는 스타일시트의 이름이 포함됩니다.

### 예제 6: 서비스 개체를 표시 하는 웹 페이지 만들기

```powershell
Get-Service | ConvertTo-Html -As LIST | Out-File services.htm
```

이 명령은 cmdlet이 반환 하는 서비스 개체의 HTML 페이지를 만듭니다 `Get-Service` . 이 명령은 **As** 매개 변수를 사용 하 여 목록 형식을 지정 합니다. Cmdlet은 `Out-File` 결과 HTML을 파일에 보냅니다 `Services.htm` .

### 예 7: 현재 날짜에 대 한 웹 테이블 만들기

```powershell
Get-Date | ConvertTo-Html -Fragment
```

```Output
<table>
<colgroup>...</colgroup>
<tr><th>DisplayHint</th><th>DateTime</th><th>Date</th><th>Day</th><th>DayOfWeek</th><th>DayOfYear</th><th>Hour</th>
<th>Kind</th><th>Millisecond</th><th>Minute</th><th>Month</th><th>Second</th><th>Ticks</th><th>TimeOfDay</th><th>Year</th></tr>
<tr><td>DateTime</td><td>Monday, May 05, 2008 10:40:04 AM</td><td>5/5/2008 12:00:00 AM</td><td>5</td><td>Monday</td>
<td>126</td><td>10</td><td>Local</td><td>123</td><td>40</td><td>5</td><td>4</td><td>633455808041237213</td><td>10:40:04.12
37213</td><td>2008</td></tr>
</table>
```

이 명령은 `ConvertTo-Html` 를 사용 하 여 현재 날짜의 HTML 테이블을 생성 합니다. 이 명령은 cmdlet을 사용 하 여 `Get-Date` 현재 날짜를 가져옵니다. 파이프라인 연산자 (|)를 사용 하 여 결과를 cmdlet으로 보냅니다 `ConvertTo-Html` .

이 `ConvertTo-Html` 명령은 출력을 HTML 테이블로 제한 하는 **Fragment** 매개 변수를 포함 합니다. 따라서 `<HEAD>` 및 `<BODY>` 태그와 같은 HTML 페이지의 다른 요소는 생략됩니다.

### 예 8: PowerShell 이벤트를 표시 하는 웹 페이지 만들기

```powershell
Get-EventLog -Log "Windows PowerShell" | ConvertTo-Html -Property id, level, task
```

이 명령은 cmdlet을 사용 하 여 `Get-EventLog` Windows PowerShell 이벤트 로그에서 이벤트를 가져옵니다.

파이프라인 연산자 ()를 사용 하 여 `|` 이벤트를 cmdlet으로 보내면이 `ConvertTo-Html` cmdlet이 이벤트를 HTML 형식으로 변환 합니다.

`ConvertTo-Html`이 명령은 **Property** 매개 변수를 사용 하 여 이벤트의 **ID** , **Level** 및 **Task** 속성만 선택 합니다.

### 예 9: 지정 된 서비스를 표시 하는 웹 페이지 만들기

```powershell
$htmlParams = @{
  Title = "Windows Services: Server01"
  Body = Get-Date
  PreContent = "<P>Generated by Corporate IT</P>"
  PostContent = "For details, contact Corporate IT."
}
Get-Service A* |
  ConvertTo-Html @htmlParams |
    Out-File Services.htm
Invoke-Item Services.htm
```

이 명령은로 시작 하는 컴퓨터의 서비스를 표시 하는 웹 페이지를 만들고 엽니다. 의 **Title** , **Body** , **precontent** 및 **postcontent** 매개 변수를 사용 하 여 `ConvertTo-Html` 출력을 사용자 지정 합니다.

명령의 첫 번째 부분에서는 cmdlet을 사용 하 여 `Get-Service` 로 시작 하는 컴퓨터의 서비스를 가져옵니다. 이 명령은 파이프라인 연산자 ()를 사용 하 여 `|` 결과를 cmdlet으로 보냅니다 `ConvertTo-Html` . 또한이 명령은 cmdlet을 사용 하 여 `Out-File` 출력을 Services.htm 파일로 보냅니다.

세미콜론 ( `;` )을 사용 하면 첫 번째 명령이 끝나고 두 번째 명령이 시작 됩니다 .이 명령은 cmdlet을 사용 하 여 `Invoke-Item` `Services.htm` 기본 브라우저에서 파일을 엽니다.

### 예 10: HTML의 Meta 속성 및 문자 집합 설정

```powershell
Get-Service | ConvertTo-HTML -Meta @{
  refresh=10
  author="Author's Name"
  keywords="PowerShell, HTML, ConvertTo-HTML"
} -Charset "UTF-8"
```

이 명령은 새로 고침, 만든이 및 키워드에 대 한 메타 태그를 사용 하 여 웹 페이지에 대 한 HTML을 만듭니다.
페이지의 문자 집합은 u t f-8로 설정 됩니다.

### 예 11: HTML을 XHTML 전환 DTD로 설정

```powershell
Get-Service | ConvertTo-HTML -Transitional
```

이 명령은 반환 된 HTML의 DOCTYPE을 XHTML 전환 DTD로 설정 합니다.

## PARAMETERS

### -As

개체를 테이블 형식으로 지정할지, 아니면 목록 형식으로 지정할지 결정합니다. 유효한 값은 **Table** 및 **List** 입니다. 기본값은 **Table** 입니다.

**테이블** 값은 PowerShell 테이블 형식과 유사한 HTML 테이블을 생성 합니다. 머리글 행은 속성 이름을 표시합니다. 각 테이블 행은 개체를 나타내고 개체의 각 속성 값을 표시합니다.

**목록** 값은 PowerShell 목록 형식과 유사한 각 개체에 대해 2 열 HTML 테이블을 생성 합니다. 첫 번째 열에는 속성 이름이 표시 됩니다. 두 번째 열에는 속성 값이 표시 됩니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Table, List

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -본문

여는 `<BODY>` 태그 뒤에 추가할 텍스트를 지정합니다. 기본적으로 해당 위치에는 텍스트가 없습니다.

```yaml
Type: System.String[]
Parameter Sets: Page
Aliases:

Required: False
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Charset

여는 태그에 추가할 텍스트를 지정 합니다 `<charset>` . 기본적으로 해당 위치에는 텍스트가 없습니다.

이 매개 변수는 PowerShell 6.0에서 도입 되었습니다.

```yaml
Type: System.String
Parameter Sets: Page
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CssUri

HTML 파일에 적용되는 CSS 스타일시트의 URI(Uniform Resource Identifier)를 지정합니다. 이 URI는 출력의 스타일시트 링크에 포함됩니다.

```yaml
Type: System.Uri
Parameter Sets: Page
Aliases: cu, uri

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -조각

HTML 테이블만 생성합니다. HTML, HEAD, TITLE 및 BODY 태그는 생략됩니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Fragment
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Head

`<HEAD>` 태그의 내용을 지정합니다. 기본값은 `<title\>HTML TABLE</title>`입니다. **Head** 매개 변수를 사용 하는 경우 **Title** 매개 변수는 무시 됩니다.

```yaml
Type: System.String[]
Parameter Sets: Page
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

HTML로 표시할 개체를 지정합니다. 개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요.

이 매개 변수를 사용 하 여 컴퓨터의 모든 서비스와 같은 여러 개체를 전송 하는 경우 `ConvertTo-Html` 컬렉션 또는 개체 배열의 속성을 표시 하는 테이블을 만듭니다. 개별 개체의 테이블을 만들려면 파이프라인 연산자를 사용 하 여 개체를로 파이프 합니다 `ConvertTo-Html` .

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Meta

여는 태그에 추가할 텍스트를 지정 합니다 `<meta>` . 기본적으로 해당 위치에는 텍스트가 없습니다.

이 매개 변수는 PowerShell 6.0에서 도입 되었습니다.

```yaml
Type: System.Collections.Hashtable
Parameter Sets: Page
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PostContent

닫는 `</TABLE>` 태그 뒤에 추가할 텍스트를 지정합니다. 기본적으로 해당 위치에는 텍스트가 없습니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PreContent

여는 `<TABLE>` 태그 앞에 추가할 텍스트를 지정합니다. 기본적으로 해당 위치에는 텍스트가 없습니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -속성

지정한 개체 속성을 HTML에 포함합니다. **Property** 매개 변수 값은 새 계산 된 속성 일 수 있습니다. 계산 된 속성은 스크립트 블록이 나 해시 테이블 일 수 있습니다. 유효한 키-값 쌍은 다음과 같습니다.

- 이름 (또는 레이블)- `<string>` (PowerShell 6.x에 추가 됨)
- 식 `<string>` 또는 `<script block>`
- FormatString `<string>`
- Width- `<int32>` -다음 보다 커야 함 `0`
- 맞춤-값은 `Left` , `Center` 또는 일 수 있습니다. `Right`

자세한 내용은 [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)를 참조 하세요.

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Title

`<TITLE>` 태그 사이에 표시되는 텍스트인 HTML 파일의 제목을 지정합니다.

```yaml
Type: System.String
Parameter Sets: Page
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -전환

**Doctype** 을 **xhtml 전환 dtd** 로 변경 하 고, 기본 **doctype** 은 **xhtml Strict dtd** 입니다.

이 매개 변수는 PowerShell 6.0에서 도입 되었습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Page
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.web. PSObject

모든 .NET 개체를로 파이프 할 수 있습니다 `ConvertTo-Html` .

## 출력

### System.string 또는 System.Xml.Xml문서

`ConvertTo-Html` 유효한 HTML을 구성 하는 일련의 문자열을 반환 합니다.

## 참고

이 cmdlet을 사용 하려면 하나 이상의 개체를 cmdlet으로 파이프 하거나 **InputObject** 매개 변수를 사용 하 여 개체를 지정 합니다. 입력이 여러 개체로 구성된 경우에는 이 두 방법의 출력이 전혀 다릅니다.

- 여러 개체를 cmdlet으로 파이프 하면 PowerShell은 개체를 한 번에 하나씩 cmdlet으로 보냅니다. 따라서는 `ConvertTo-Html` 개별 개체를 표시 하는 테이블을 만듭니다. 예를 들어 컴퓨터의 프로세스를로 파이프 하는 경우 `ConvertTo-Html` 결과 테이블에 모든 프로세스가 표시 됩니다.

- **InputObject** 매개 변수를 사용 하 여 여러 개체를 전송 하는 경우는 `ConvertTo-Html` 이러한 개체를 컬렉션 또는 배열로 받습니다. 따라서 배열의 항목이 아니라 배열과 해당 속성을 표시하는 테이블을 만듭니다. 예를 들어 **InputObject** 를 사용 하 여 컴퓨터의 프로세스를로 전송 하 `ConvertTo-Html` 는 경우 결과 테이블에 개체 배열 및 해당 속성이 표시 됩니다.

  XHTML Strict DTD를 준수 하기 위해 DOCTYPE 태그가 적절 하 게 수정 됩니다.

   `<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"   "https://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd"\>`

## 관련 링크

[about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[ConvertTo-Csv](ConvertTo-Csv.md)

[ConvertTo-Json](ConvertTo-Json.md)

[ConvertTo-Xml](ConvertTo-Xml.md)

[Export-Clixml](Export-Clixml.md)

[Import-Clixml](Import-Clixml.md)
