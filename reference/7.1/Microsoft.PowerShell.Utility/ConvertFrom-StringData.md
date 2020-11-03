---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/21/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertfrom-stringdata?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-StringData
ms.openlocfilehash: 256807079f8ef47baf20cd70df326298e4ce9ed0
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93215906"
---
# ConvertFrom-StringData

## 개요
키와 값 쌍이 하나 이상 포함된 문자열을 해시 테이블로 변환합니다.

## SYNTAX

### 모두

```
ConvertFrom-StringData [-StringData] <String> [[-Delimiter] <Char>] [<CommonParameters>]
```

## 설명

`ConvertFrom-StringData`Cmdlet은 하나 이상의 키와 값 쌍을 포함 하는 문자열을 해시 테이블로 변환 합니다. 각 키-값 쌍이 별도의 줄에 있어야 하기 때문에 문자열은 일반적으로 입력 형식으로 사용 됩니다. 기본적으로 **키** 는 등호 () 문자로 **값** 과 구분 되어야 합니다 `=` .

`ConvertFrom-StringData`Cmdlet은 `DATA` 스크립트 또는 함수의 섹션에서 사용할 수 있는 safe cmdlet으로 간주 됩니다. 섹션에서 사용 하는 경우 `DATA` 문자열의 내용이 데이터 섹션의 규칙을 준수 해야 합니다. 자세한 내용은 [about_Data_Sections](../Microsoft.PowerShell.Core/About/about_Data_Sections.md)를 참조 하세요.

`ConvertFrom-StringData` 에서는 기존 기계 번역 도구에서 허용 하는 이스케이프 문자 시퀀스를 지원 합니다. 즉, cmdlet은 `\` 일반적으로 스크립트의 줄 끝에 신호를 보내는 PowerShell 억음 문자 () 대신 [Unescape 메서드](/dotnet/api/system.text.regularexpressions.regex.unescape)를 사용 하 여 문자열 데이터에서 백슬래시 ()를 이스케이프 문자로 해석할 수 있습니다 \` . here-string 내에서 억음 문자는 작동하지 않습니다. 다음과 같이 앞의 백슬래시로 이스케이프 하 여 결과에서 리터럴 백슬래시를 유지할 수도 있습니다 `\\` . 이스케이프되지 않은 백슬래시 문자(예: 일반적으로 파일 경로에 사용되는 문자)는 결과에서 잘못된 이스케이프 시퀀스로 렌더링될 수 있습니다.

PowerShell 7은 **구분 기호** 매개 변수를 추가 합니다.

## 예제

### 예제 1: 작은따옴표로 묶은 단일 문자열을 해시 테이블로 변환

이 예에서는 사용자 메시지의 작은따옴표로 묶은 문자열을 해시 테이블로 변환 합니다. 작은따옴표로 묶인 문자열에서 값은 변수로 대체되지 않으며 식은 평가되지 않습니다.
`ConvertFrom-StringData`Cmdlet은 변수의 값을 `$Here` 해시 테이블로 변환 합니다.

```powershell
$Here = @'
Msg1 = The string parameter is required.
Msg2 = Credentials are required for this command.
Msg3 = The specified variable does not exist.
'@
ConvertFrom-StringData -StringData $Here
```

```Output
Name                           Value
----                           -----
Msg3                           The specified variable does not exist.
Msg2                           Credentials are required for this command.
Msg1                           The string parameter is required.
```

### 예 2: 다른 구분 기호를 사용 하 여 문자열 데이터 변환

이 예에서는 다른 문자를 구분 기호로 사용 하는 문자열 데이터를 변환 하는 방법을 보여 줍니다. 이 예제에서 문자열 데이터는 구분 기호로 파이프 문자 ()를 사용 합니다 `|` .

```powershell
$StringData = @'
color|red
model|coupe
year|1965
condition|mint
'@
$carData = ConvertFrom-StringData -StringData $StringData -Delimiter '|'
$carData
```

```Output
Name                           Value
----                           -----
condition                      mint
model                          coupe
color                          red
year                           1965
```

### 예제 3: 주석을 포함 하는 문자열로 변환

이 예에서는 주석과 여러 키-값 쌍을 포함 하는 여기 문자열을 해시 테이블로 변환 합니다.

```powershell
ConvertFrom-StringData -StringData @'
Name = Disks.ps1

# Category is optional.

Category = Storage
Cost = Free
'@
```

```Output
Name                           Value
----                           -----
Cost                           Free
Category                       Storage
Name                           Disks.ps1
```

**Stringdata** 매개 변수 값은 여기에 문자열이 포함 된 변수가 아니라 여기에 포함 된 문자열입니다. 두 형식은 모두 유효합니다. 이 here-string에는 문자열 중 하나에 대한 주석이 포함되어 있습니다.
`ConvertFrom-StringData` 한 줄로 된 주석을 무시 하지만 `#` 문자는 줄에서 공백이 아닌 첫 번째 문자 여야 합니다. 뒤의 줄에 있는 모든 문자는 `#` 무시 됩니다.

### 예제 4: 문자열을 해시 테이블로 변환

이 예에서는 일반 이중 따옴표 붙은 문자열 (여기 문자열 아님)을 해시 테이블로 변환 하 고 `$A` 변수에 저장 합니다.

```powershell
$A = ConvertFrom-StringData -StringData "Top = Red `n Bottom = Blue"
$A
```

```Output
Name             Value
----             -----
Bottom           Blue
Top              Red
```

각 키-값 쌍이 별도의 줄에 있어야 하는 조건을 충족 하기 위해 문자열은 PowerShell 줄 바꿈 문자 ( \` n)를 사용 하 여 쌍을 구분 합니다.

### 예 5: 스크립트의 데이터 섹션에서 ConvertFrom-StringData 사용

이 예에서는 `ConvertFrom-StringData` 스크립트의 데이터 섹션에 사용 되는 명령을 보여 줍니다.
DATA 섹션 아래에 있는 문은 사용자에게 텍스트를 표시합니다.

```powershell
$TextMsgs = DATA {
ConvertFrom-StringData @'
Text001 = The $Notebook variable contains the name of the user's system notebook.
Text002 = The $MyNotebook variable contains the name of the user's private notebook.
'@
}
$TextMsgs
```

```Output
Name             Value
----             -----
Text001          The $Notebook variable contains the name of the user's system notebook.
Text002          The $MyNotebook variable contains the name of the user's private notebook.
```

텍스트에 변수 이름이 포함되어 있으므로 변수를 확장하지 않고 문자 그대로 해석하기 위해 텍스트를 작은따옴표로 묶어야 합니다. **데이터** 섹션에는 변수가 허용 되지 않습니다.

### 예제 6: 파이프라인 연산자를 사용 하 여 문자열 전달

이 예제에서는 파이프라인 연산자 ()를 사용 하 여 `|` 에 문자열을 보낼 수 있음을 보여 줍니다 `ConvertFrom-StringData` . 변수의 값은 `$Here` 로 파이프 되 `ConvertFrom-StringData` 고 결과는 변수로 전달 됩니다 `$Hash` .

```powershell
$Here = @'
Msg1 = The string parameter is required.
Msg2 = Credentials are required for this command.
Msg3 = The specified variable does not exist.
'@
$Hash = $Here | ConvertFrom-StringData
$Hash
```

```Output
Name     Value
----     -----
Msg3     The specified variable does not exist.
Msg2     Credentials are required for this command.
Msg1     The string parameter is required.
```

### 예 7: 이스케이프 문자를 사용 하 여 새 줄 및 반환 문자 추가

이 예제에서는 이스케이프 문자를 사용 하 여 소스 데이터에 새 줄을 만들고 문자를 반환 하는 방법을 보여 줍니다. 이스케이프 시퀀스는 `\n` 결과 해시 테이블의 이름이 나 항목과 연결 된 텍스트 블록 내에 새 줄을 만드는 데 사용 됩니다.

```powershell
ConvertFrom-StringData @"
Vincentio = Heaven doth with us as we with torches do,\nNot light them for themselves; for if our virtues\nDid not go forth of us, 'twere all alike\nAs if we had them not.
Angelo = Let there be some more test made of my metal,\nBefore so noble and so great a figure\nBe stamp'd upon it.
"@ | Format-List
```

```Output
Name  : Angelo
Value : Let there be some more test made of my metal,
        Before so noble and so great a figure
        Be stamp'd upon it.

Name  : Vincentio
Value : Heaven doth with us as we with torches do,
        Not light them for themselves; for if our virtues
        Did not go forth of us, 'twere all alike
        As if we had them not.
```

### 예 8: 백슬래시 이스케이프 문자를 사용 하 여 파일 경로 올바르게 렌더링

이 예제에서는 문자열 데이터에서 백슬래시 이스케이프 문자를 사용 하 여 결과 해시 테이블에서 파일 경로가 올바르게 렌더링 되도록 하는 방법을 보여 줍니다 `ConvertFrom-StringData` . 이중 백슬래시는 리터럴 백슬래시가 해시 테이블 출력에 제대로 렌더링되게 합니다.

```powershell
ConvertFrom-StringData "Message=Look in c:\\Windows\\System32"
```

```Output
Name                           Value
----                           -----
Message                        Look in c:\Windows\System32
```

## PARAMETERS

### -StringData

변환할 문자열을 지정합니다. 이 매개 변수를 사용 하거나 문자열을로 파이프 할 수 있습니다 `ConvertFrom-StringData` . 매개 변수 이름은 선택 사항입니다.

이 매개 변수 값은 하나 이상의 키-값 쌍을 포함 하는 문자열 이어야 합니다. 각 키-값 쌍은 별도의 줄에 있어야 하며, 각 쌍은 줄 바꿈 문자 (n)로 구분 해야 합니다 \` .

문자열에 주석을 포함할 수 있지만 주석은 키-값 쌍과 같은 줄에 있을 수 없습니다. `ConvertFrom-StringData` 한 줄로 이루어진 주석을 무시 합니다. `#`문자는 줄에서 공백이 아닌 첫 번째 문자 여야 합니다. 뒤의 줄에 있는 모든 문자는 `#` 무시 됩니다. 주석은 해시 테이블에 포함되지 않습니다.

여기에 있는 문자열은 하나 이상의 줄로 구성 된 문자열입니다. 여기에 표시 되는 문자열 내의 따옴표는 문자열 데이터의 일부로 문자 그대로 해석 됩니다. 자세한 내용은 [about_Quoting_Rules](../Microsoft.PowerShell.Core/About/about_Quoting_Rules.md)를 참조 하세요.

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

### -구분 기호

변환 되는 문자열의 **값** 데이터에서 **키** 를 구분 하는 데 사용 되는 문자입니다.
기본 구분 기호는 등호 ( `=` ) 문자입니다. 이 매개 변수는 PowerShell 7에서 추가 되었습니다.

```yaml
Type: System.Char
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: '='
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.

## 입력

### System.String

키-값 쌍을 포함 하는 문자열을로 파이프 할 수 있습니다 `ConvertFrom-StringData` .

## 출력

### System.Collections.Hashtable

이 cmdlet은 키-값 쌍에서 만든 해시 테이블을 반환 합니다.

## 참고

here-string은 하나 이상의 줄로 이루어진 문자열로, 이 문자열 내에서 따옴표는 문자 그대로 해석됩니다.

이 cmdlet은 여러 음성 언어로 사용자 메시지를 표시 하는 스크립트에서 유용할 수 있습니다. 사전 스타일의 해시 테이블을 사용하여 리소스 파일에서처럼 코드에서 텍스트 문자열을 분리하고 번역 도구에서 사용하도록 텍스트 문자열의 형식을 지정할 수 있습니다.

## 관련 링크

