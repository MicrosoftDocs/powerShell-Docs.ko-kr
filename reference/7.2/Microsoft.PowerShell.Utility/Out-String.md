---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 01/20/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/out-string?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-String
ms.openlocfilehash: 59e5b728604ce37f27b56ebe62e1a22d6af8a966
ms.sourcegitcommit: 94d597c4fb38793bc49ca7610e2c9973b1e577c2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/21/2021
ms.locfileid: "99603078"
---
# Out-String

## 개요
입력 개체를 문자열로 출력 합니다.

## Syntax

### NoNewLineFormatting 지정 (기본값)

```
Out-String [-Width <Int32>] [-NoNewline] [-InputObject <PSObject>] [<CommonParameters>]
```

### StreamFormatting 지정

```
Out-String [-Stream] [-Width <Int32>] [-InputObject <PSObject>] [<CommonParameters>]
```

## 설명

`Out-String`Cmdlet은 입력 개체를 문자열로 변환 합니다. 기본적으로는 `Out-String` 문자열을 누적 하 고이를 단일 문자열로 반환 하지만 **Stream** 매개 변수를 사용 하 여 한 `Out-String` 번에 한 줄씩 반환 하거나 문자열을 만들어 배열을 만들 수 있습니다. 이 cmdlet을 사용하면 개체를 편하게 조작할 수 없을 경우 기존 셸과 동일한 방식으로 문자열 출력을 검색하고 조작할 수 있습니다.

## 예

### 예 1: 현재 문화권을 가져오고 데이터를 문자열로 변환

이 예에서는 현재 사용자의 국가별 설정을 가져오고 개체 데이터를 문자열로 변환 합니다.

```powershell
$C = Get-Culture | Select-Object -Property *
Out-String -InputObject $C -Width 100
```

```Output
Parent                         : en
LCID                           : 1033
KeyboardLayoutId               : 1033
Name                           : en-US
IetfLanguageTag                : en-US
DisplayName                    : English (United States)
NativeName                     : English (United States)
EnglishName                    : English (United States)
TwoLetterISOLanguageName       : en
ThreeLetterISOLanguageName     : eng
ThreeLetterWindowsLanguageName : ENU
CompareInfo                    : CompareInfo - en-US
TextInfo                       : TextInfo - en-US
IsNeutralCulture               : False
CultureTypes                   : SpecificCultures, InstalledWin32Cultures, FrameworkCultures
NumberFormat                   : System.Globalization.NumberFormatInfo
DateTimeFormat                 : System.Globalization.DateTimeFormatInfo
Calendar                       : System.Globalization.GregorianCalendar
OptionalCalendars              : {System.Globalization.GregorianCalendar,
                                 System.Globalization.GregorianCalendar}
UseUserOverride                : True
IsReadOnly                     : False
```

`$C`변수는 **Selected.System를 저장 합니다. 세계화. CultureInfo** 개체입니다. 개체는 `Get-Culture` 출력을 파이프라인에서로 보낸 결과입니다 `Select-Object` . **Property** 매개 변수는 별표 ( `*` ) 와일드 카드를 사용 하 여 개체에 포함 된 모든 속성을 지정 합니다.

`Out-String`**InputObject** 매개 변수를 사용 하 여 변수에 저장 된 **CultureInfo** 개체를 지정 합니다 `$C` . 의 개체는 `$C` 문자열로 변환 됩니다.

> [!NOTE]
> `Out-String`배열을 보려면 출력을 변수에 저장 하 고 배열 인덱스를 사용 하 여 요소를 확인 합니다. 배열 인덱스에 대 한 자세한 내용은 [about_Arrays](../microsoft.powershell.core/about/about_arrays.md)를 참조 하세요.
>
> `$str = Out-String -InputObject $C -Width 100`

### 예제 2: 개체 작업

이 예제에서는 개체 작업과 문자열 작업 간의 차이점을 보여 줍니다. 명령은 **gcm** 텍스트,에 대 한 별칭을 포함 하는 별칭을 표시 합니다 `Get-Command` .

```powershell
Get-Alias | Out-String -Stream | Select-String -Pattern "gcm"
```

```Output
Alias           gcm -> Get-Command
```

`Get-Alias` 각 별칭에 대해 하나씩 **system.management.automation.aliasinfo** 개체를 가져오고 개체를 파이프라인으로 보냅니다. `Out-String`**Stream** 매개 변수를 사용 하 여 모든 개체를 단일 문자열로 연결 하는 대신 각 개체를 문자열로 변환 합니다. **System.string** 개체는 파이프라인으로 전송 되 고 `Select-String` **Pattern** 매개 변수를 사용 하 여 **gcm** 텍스트와 일치 하는 항목을 찾습니다.

> [!NOTE]
> **Stream** 매개 변수를 생략 하면에서 `Select-String` 반환 하는 단일 문자열에서 **gcm** 텍스트를 찾기 때문에 명령은 모든 별칭을 표시 합니다 `Out-String` .

### 예 3: Width 매개 변수를 사용 하 여 잘림 방지

의 출력 대부분 `Out-String` 은 다음 줄로 래핑되어,에 전달 되기 전에 형식 지정 시스템에 의해 출력이 잘리는 시나리오는 있습니다 `Out-String` . **Width** 매개 변수를 사용 하 여 잘림을 방지할 수 있습니다.

```powershell
PS> @{TestKey = ('x' * 200)} | Out-String
Name                           Value
----                           -----
TestKey                        xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx...

PS> @{TestKey = ('x' * 200)} | Out-String -Width 250

Name                           Value
----                           -----
TestKey                        xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

## PARAMETERS

### -InputObject

문자열에 기록할 개체를 지정합니다. 개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요.

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

### -NoNewline

PowerShell 포맷터에 의해 생성 된 출력에서 모든 줄바꿈를 제거 합니다. 문자열 개체의 일부인 줄바꿈은 유지 됩니다.

이 매개 변수는 PowerShell 6.0에서 도입 되었습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NoNewLineFormatting
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -스트림

기본적으로는 `Out-String` 빈 머리글이 나 후행 줄바꿈를 포함 하 여 콘솔에서 볼 수 있는 것 처럼 형식이 지정 된 단일 문자열을 출력 합니다. **Stream** 매개 변수는 `Out-String` 를 사용 하 여 각 줄을 하나씩 출력 합니다. 이에 대 한 유일한 예외는 여러 줄 문자열입니다. 이 경우는 `Out-String` 계속 해 서 문자열을 한 줄로 된 단일 문자열로 출력 합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: StreamFormatting
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -너비

출력의 각 줄에 포함되는 문자 수를 지정합니다. 추가 문자는 사용 된 포맷터 cmdlet에 따라 다음 줄로 래핑되어 잘립니다. **Width** 매개 변수는 형식이 지정 된 개체에만 적용 됩니다. 이 매개 변수를 생략할 경우 호스트 프로그램의 특성에 따라 너비가 결정됩니다. 터미널 (콘솔) 창에서 현재 창 너비가 기본값으로 사용 됩니다. PowerShell 콘솔 windows의 기본값은 설치 시 80 자입니다.

```yaml
Type: System.Int32
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

### System.web. PSObject

파이프라인에서로 개체를 보낼 수 있습니다 `Out-String` .

## 출력

### System.String

`Out-String` 입력 개체에서 만든 문자열을 반환 합니다.

## 참고

동사를 포함 하는 cmdlet은 `Out` 개체의 형식을 지정 하지 않습니다. `Out`Cmdlet은 지정 된 표시 대상에 대 한 포맷터에 개체를 보냅니다.

## 관련 링크

[about_Formatting](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md)

[Out-Default](../Microsoft.PowerShell.Core/Out-Default.md)

[Out-File](Out-File.md)

[Out-Host](../Microsoft.PowerShell.Core/Out-Host.md)

[Out-Null](../Microsoft.PowerShell.Core/Out-Null.md)

[Out-GridView](Out-GridView.md)

[Out-Printer](Out-Printer.md)
