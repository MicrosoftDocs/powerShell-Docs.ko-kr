---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-host?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Host
ms.openlocfilehash: 47a4d9bb66e3e6c3267bbdf18f41c8af8e5448f0
ms.sourcegitcommit: 758e6dbb428295698d4852b3e19f5d03deade037
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/15/2020
ms.locfileid: "93219946"
---
# Write-Host

## 개요

사용자 지정된 출력을 호스트에 씁니다.

## SYNTAX

```
Write-Host [[-Object] <Object>] [-NoNewline] [-Separator <Object>] [-ForegroundColor <ConsoleColor>]
 [-BackgroundColor <ConsoleColor>] [<CommonParameters>]
```

## 설명

`Write-Host`Cmdlet의 기본 용도는 사용자에 게 [읽기 호스트](Read-Host.md)와의 입력을 요청 하는 경우 처럼 컬러 텍스트 인쇄와 같이-(호스트)-표시 전용 출력을 생성 하는 것입니다.
`Write-Host`[ToString ()](/dotnet/api/system.object.tostring) 메서드를 사용 하 여 출력을 작성 합니다. 반대로 데이터를 파이프라인으로 출력 하려면 [쓰기 출력](Write-Output.md) 또는 암시적 출력을 사용 합니다.

매개 변수를 사용 하 여 텍스트 색을 지정 하 `ForegroundColor` 고, 매개 변수를 사용 하 여 배경색을 지정할 수 있습니다 `BackgroundColor` . Separator 매개 변수를 사용하면 표시된 개체를 구분하는 데 사용할 문자열을 지정할 수 있습니다. 특정 결과는 PowerShell을 호스트 하는 프로그램에 따라 달라 집니다.

> [!NOTE]
> Windows PowerShell 5.0부터 `Write-Host` 은이에 대 한 래퍼로,를 사용 하 여 `Write-Information` 출력을 `Write-Host` 정보 스트림으로 내보낼 수 있습니다. 이를 통해 이전 버전과의 호환성을 유지 하면서 **를 사용** 하 여 작성 된 데이터를 **캡처하거나** 제거할 수 있습니다 `Write-Host` .
>
> `$InformationPreference`기본 설정 변수 및 `InformationAction` 일반 매개 변수는 메시지에 영향을 주지 않습니다 `Write-Host` . 이 규칙의 예외는 효과적으로 출력을 억제 하는입니다 `-InformationAction Ignore` `Write-Host` . ("예제 5" 참조)

## 예제

### 예제 1: 새 줄을 추가 하지 않고 콘솔에 쓰기

```powershell
Write-Host "no newline test " -NoNewline
Write-Host "second string"
```

```output
no newline test second string
```

이 명령은 매개 변수를 사용 하 여 ' 줄 바꿈 테스트 없음 ' 문자열을 표시 합니다 `NoNewline` .

두 번째 문자열이 작성 되지만 문자열을 구분 하는 줄 바꿈이 없기 때문에 첫 번째 문자열이 첫 번째 문자열과 같은 줄에 끝납니다.

### 예제 2: 콘솔에 쓰기 및 구분 기호 포함

```powershell
Write-Host (2,4,6,8,10,12) -Separator ", +2= "
```

```output
2, +2= 4, +2= 6, +2= 8, +2= 10, +2= 12
```

이 명령은 2에서 12 사이의 짝수를 표시 합니다. **구분 기호** 매개 변수는 문자열 `, +2= ` (쉼표, 공백,, `+` `2` , `=` , 공백)을 추가 하는 데 사용 됩니다.

### 예제 3: 다른 텍스트 및 배경색으로 쓰기

```powershell
Write-Host (2,4,6,8,10,12) -Separator ", -> " -ForegroundColor DarkGreen -BackgroundColor White
```

```output
2, -> 4, -> 6, -> 8, -> 10, -> 12
```

이 명령은 2에서 12 사이의 짝수를 표시 합니다. 매개 변수를 사용 하 여 `ForegroundColor` 진한 녹색 텍스트를 출력 하 고 매개 변수를 사용 하 여 `BackgroundColor` 흰색 배경을 표시 합니다.

### 예제 4: 다른 텍스트 및 배경색으로 쓰기

```powershell
Write-Host "Red on white text." -ForegroundColor red -BackgroundColor white
```

```output
Red on white text.
```

이 명령은 "Red on white text" 문자열을 표시합니다. 매개 변수에 정의 된 대로 텍스트가 빨간색으로 바뀝니다 `ForegroundColor` . 배경은 매개 변수로 정의 된 흰색입니다 `BackgroundColor` .

### 예 5: Write-Host 출력 표시 안 함

```powershell
# The following two statements can be used to effectively suppress output from Write-Host
Write-Host "I won't print" -InformationAction Ignore
Write-Host "I won't print" 6>$null
```

```output

```

이러한 명령은 cmdlet의 출력을 효과적으로 표시 하지 않습니다 `Write-Host` . 첫 번째 `InformationAction` 매개 변수는 값과 함께 매개 변수를 사용 하 여 `Ignore` 정보 스트림에 대 한 출력을 표시 하지 않습니다.
두 번째 예제에서는 명령의 정보 스트림을 변수로 리디렉션하여이를 표시 하지 `$null` 않습니다.

## PARAMETERS

### -BackgroundColor

배경색을 지정합니다. 기본값은 없습니다. 이 매개 변수에 허용되는 값은 다음과 같습니다.

- 검정
- 진한 파랑
- 진한 녹색
- 진한 녹청
- 진한 빨강
- 진한 자홍
- 진한 노랑
- 회색
- 진한 회색
- 파랑
- 녹색
- 녹청
- 빨간색
- 자홍
- 노란색
- 흰색

```yaml
Type: System.ConsoleColor
Parameter Sets: (All)
Aliases:
Accepted values: Black, DarkBlue, DarkGreen, DarkCyan, DarkRed, DarkMagenta, DarkYellow, Gray, DarkGray, Blue, Green, Cyan, Red, Magenta, Yellow, White

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ForegroundColor

텍스트 색을 지정합니다. 기본값은 없습니다. 이 매개 변수에 허용되는 값은 다음과 같습니다.

- 검정
- 진한 파랑
- 진한 녹색
- 진한 녹청
- 진한 빨강
- 진한 자홍
- 진한 노랑
- 회색
- 진한 회색
- 파랑
- 녹색
- 녹청
- 빨간색
- 자홍
- 노란색
- 흰색

```yaml
Type: System.ConsoleColor
Parameter Sets: (All)
Aliases:
Accepted values: Black, DarkBlue, DarkGreen, DarkCyan, DarkRed, DarkMagenta, DarkYellow, Gray, DarkGray, Blue, Green, Cyan, Red, Magenta, Yellow, White

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NoNewline

입력 개체의 문자열 표현은 연결 되어 출력을 형성 합니다. 출력 문자열 사이에 공백이 나 줄바꿈 삽입 되지 않습니다. 마지막 출력 문자열 뒤에는 줄 바꿈이 추가 되지 않습니다.

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

### -개체

호스트에 표시할 개체입니다.

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases: Msg, Message

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -구분 기호

호스트에서 표시 하는 개체 사이에 삽입할 구분 기호 문자열을 지정 합니다.

```yaml
Type: System.Object
Parameter Sets: (All)
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

### System.Object

호스트에 쓸 개체를 파이프할 수 있습니다.

## 출력

### 없음

`Write-Host` 호스트에 개체를 보냅니다. 개체를 반환하지 않습니다. 그러나 호스트는로 보내는 개체를 표시 합니다 `Write-Host` .

## 참고

- 호스트에 컬렉션을 작성 하는 경우 컬렉션의 요소는 단일 공백으로 구분 된 동일한 줄에 인쇄 됩니다. **구분 기호** 매개 변수를 사용 하 여이를 재정의할 수 있습니다.

- 속성이 있는 개체와 같은 기본이 아닌 데이터 형식은 예기치 않은 결과를 발생 시킬 수 있으며 의미 있는 출력을 제공 하지 않습니다. 예를 들어는 `Write-Host @{a = 1; b = 2}` `System.Collections.DictionaryEntry System.Collections.DictionaryEntry` 호스트에 인쇄 됩니다.

## 관련 링크

[Clear-Host](../Microsoft.PowerShell.Core/Clear-Host.md)

[Out-Host](../Microsoft.PowerShell.Core/Out-Host.md)

[Write-Debug](Write-Debug.md)

[쓰기 오류](Write-Error.md)

[Write-Output](Write-Output.md)

[Write-Progress](Write-Progress.md)

[Write-Verbose](Write-Verbose.md)

[Write-Warning](Write-Warning.md)
