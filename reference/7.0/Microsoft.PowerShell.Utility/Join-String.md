---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Module Name: Microsoft.PowerShell.Utility
ms.date: 12/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/join-string?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Join-String
ms.openlocfilehash: bae6b8558a3e12bf161d8f0ec12037841a20cc04
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93211194"
---
# Join-String

## 개요
파이프라인의 개체를 단일 문자열로 결합 합니다.

## SYNTAX

### Default (기본값)

```
Join-String [[-Property] <PSPropertyExpression>] [[-Separator] <String>] [-OutputPrefix <String>]
 [-OutputSuffix <String>] [-UseCulture] [-InputObject <PSObject[]>] [<CommonParameters>]
```

### SingleQuote

```
Join-String [[-Property] <PSPropertyExpression>] [[-Separator] <String>] [-OutputPrefix <String>]
 [-OutputSuffix <String>] [-SingleQuote] [-UseCulture] [-InputObject <PSObject[]>]
 [<CommonParameters>]
```

### DoubleQuote

```
Join-String [[-Property] <PSPropertyExpression>] [[-Separator] <String>] [-OutputPrefix <String>]
 [-OutputSuffix <String>] [-DoubleQuote] [-UseCulture] [-InputObject <PSObject[]>]
 [<CommonParameters>]
```

### 서식

```
Join-String [[-Property] <PSPropertyExpression>] [[-Separator] <String>] [-OutputPrefix <String>]
 [-OutputSuffix <String>] [-FormatString <String>] [-UseCulture] [-InputObject <PSObject[]>]
 [<CommonParameters>]
```

## 설명

`Join-String`Cmdlet은 파이프라인 개체의 텍스트를 단일 문자열로 결합 하거나 결합 합니다.

매개 변수를 지정 하지 않으면 파이프라인 개체가 문자열로 변환 되 고 기본 구분 기호와 조인 됩니다 `$OFS` .

속성 이름을 지정 하 여 속성의 값을 문자열로 변환 하 고 문자열에 조인 합니다.

속성 이름 대신 스크립트 블록을 사용할 수 있습니다. 결과를 형성 하기 위해 스크립트 블록의 결과가 조인 되기 전에 문자열로 변환 됩니다. 개체의 속성 텍스트 또는 문자열로 변환 된 개체의 결과를 결합할 수 있습니다.

이 cmdlet은 PowerShell 6.2에서 도입 되었습니다.

## 예제

### 예 1: 디렉터리 이름 조인

<!-- markdownlint-disable MD038 -->
이 예에서는 디렉터리 이름을 조인 하 고, 출력을 큰따옴표로 래핑하고, 디렉터리 이름을 쉼표와 공백 ()으로 구분 `, ` 합니다. 출력은 문자열 개체입니다.

```powershell
Get-ChildItem -Directory C:\ | Join-String -Property Name -DoubleQuote -Separator ', '
```

```Output
"PerfLogs", "Program Files", "Program Files (x86)", "Users", "Windows"
```

`Get-ChildItem`**directory** 매개 변수를 사용 하 여 드라이브에 대 한 모든 디렉터리 이름을 가져옵니다 `C:\` .
개체는 파이프라인에서로 전송 됩니다 `Join-String` . **Property** 매개 변수는 디렉터리 이름을 지정 합니다. **DoubleQuote** 매개 변수는 따옴표를 사용 하 여 디렉터리 이름을 래핑합니다.
**구분 기호** 매개 변수는 쉼표와 공백 ()을 사용 하 여 `, ` 디렉터리 이름을 구분 하도록 지정 합니다.

`Get-ChildItem`개체는 **system.io.directoryinfo** 이며 `Join-String` 개체를 **system.string** 로 변환 합니다.

### 예제 2: 속성 하위 문자열을 사용 하 여 디렉터리 이름에 조인

이 예제에서는 부분 문자열 메서드를 사용 하 여 디렉터리 이름의 처음 4 개 문자를 가져오고, 출력을 작은따옴표로 래핑하고, 디렉터리 이름을 세미콜론 ()으로 구분 합니다 `;` .

```powershell
Get-ChildItem -Directory C:\ | Join-String -Property {$_.Name.SubString(0,4)} -SingleQuote -Separator ';'
```

```Output
'Perf';'Prog';'Prog';'User';'Wind'
```

`Get-ChildItem`**directory** 매개 변수를 사용 하 여 드라이브에 대 한 모든 디렉터리 이름을 가져옵니다 `C:\` .
개체는 파이프라인에서로 전송 됩니다 `Join-String` .

**속성** 매개 변수 스크립트 블록은 자동 변수 ( `$_` )를 사용 하 여 각 개체의 **Name** 속성 하위 문자열을 지정 합니다. 부분 문자열은 각 디렉터리 이름의 처음 4 개 문자를 가져옵니다. 부분 문자열은 문자 시작 및 끝 위치를 지정 합니다. **Singlequote** 매개 변수는 작은따옴표를 사용 하 여 디렉터리 이름을 래핑합니다. **구분 기호** 매개 변수는 세미콜론 ()을 사용 하 여 `;` 디렉터리 이름을 구분 하도록 지정 합니다.

자동 변수 및 부분 문자열에 대 한 자세한 내용은 [about_Automatic_Variables](../microsoft.powershell.core/about/about_automatic_variables.md) 및 하위 [문자열](/dotnet/api/system.string.substring)을 참조 하세요.

### 예제 3: 별도의 줄에 조인 출력 표시

이 예제에서는 서비스 이름을 각 서비스와 별도의 줄에 조인 하 고 탭으로 들여씁니다.

```powershell
Get-Service -Name se* | Join-String -Property Name -Separator "`r`n`t" -OutputPrefix "Services:`n`t"
```

```Output
Services:
    seclogon
    SecurityHealthService
    SEMgrSvc
    SENS
    Sense
    SensorDataService
    SensorService
    SensrSvc
    SessionEnv
```

`Get-Service` 에서는 **Name** 매개 변수를 사용 하 여로 시작 하는 서비스를 지정 합니다 `se*` . 별표 ( `*` )는 모든 문자에 대 한 와일드 카드입니다.

개체는 `Join-String` **속성** 매개 변수를 사용 하 여 서비스 이름을 지정 하는 파이프라인에서로 전송 됩니다. **Separator** 매개 변수는 캐리지 리턴 ( `` `r `` ), 줄 바꿈 ( `` `n `` ) 및 탭 ()을 나타내는 세 가지 특수 문자를 지정 합니다 `` `t `` . **Outputprefix** 는 첫 번째 출력 줄 앞에 새 줄과 탭을 사용 하 여 레이블 **서비스** 를 삽입 합니다.

특수 문자에 대 한 자세한 내용은 [about_Special_Characters](..//microsoft.powershell.core/about/about_special_characters.md)를 참조 하세요.

### 예제 4: 개체에서 클래스 정의 만들기

이 예에서는 기존 개체를 템플릿으로 사용 하 여 PowerShell 클래스 정의를 생성 합니다.

이 코드 샘플에서는 스 플랫을 사용 하 여 줄 길이를 줄이고 가독성을 향상 시킵니다. 자세한 내용은 [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md)를 참조 하세요.

```powershell
$obj = [pscustomobject] @{Name = "Joe"; Age = 42}
$parms = @{
  Property = "Name"
  FormatString = '  ${0}'
  OutputPrefix = "class {`n"
  OutputSuffix = "`n}`n"
  Separator = "`n"
}
$obj.PSObject.Properties | Join-String @parms
```

```Output
class {
  $Name
  $Age
}
```

## PARAMETERS

### -DoubleQuote

각 파이프라인 개체의 문자열 값을 큰따옴표로 래핑합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DoubleQuote
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -FormatString

각 항목의 형식을 지정 하는 방법을 지정 하는 서식 문자열입니다.

```yaml
Type: System.String
Parameter Sets: Format
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

조인할 텍스트를 지정 합니다. 텍스트를 포함 하는 변수를 입력 하거나 문자열에 조인할 개체를 가져오는 명령 또는 식을 입력 합니다.

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -OutputPrefix

출력 문자열 앞에 삽입 되는 텍스트입니다. 문자열에는 캐리지 리턴 ( `` `r `` ), 줄 바꿈 ( `` `n `` ) 및 tab ()과 같은 특수 문자가 포함 될 수 있습니다 `` `t `` .

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: op

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -OutputSuffix

출력 문자열에 추가 되는 텍스트입니다. 문자열에는 캐리지 리턴 ( `` `r `` ), 줄 바꿈 ( `` `n `` ) 및 tab ()과 같은 특수 문자가 포함 될 수 있습니다 `` `t `` .

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: os

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -속성

파이프라인 개체를 텍스트로 프로젝션 하는 속성 또는 속성의 이름입니다.

```yaml
Type: Microsoft.PowerShell.Commands.PSPropertyExpression
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -구분 기호

각 파이프라인 개체의 텍스트 사이에 삽입 되는 쉼표나 세미콜론 등의 텍스트 또는 문자입니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SingleQuote

각 파이프라인 개체의 문자열 값을 작은따옴표로 래핑합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: SingleQuote
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseCulture

현재 문화권의 목록 구분 기호를 항목 구분 기호로 사용 합니다. 문화권에 대 한 목록 구분 기호를 찾으려면 다음 명령을 사용 합니다. `(Get-Culture).TextInfo.ListSeparator`

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.web. PSObject

## 출력

### System.String

## 참고

## 관련 링크

[about_Automatic_Variables](../microsoft.powershell.core/about/about_automatic_variables.md)

[about_Special_Characters](..//microsoft.powershell.core/about/about_special_characters.md)

[부분](/dotnet/api/system.string.substring)
