---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 01/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-formatdata?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-FormatData
ms.openlocfilehash: 28eab1709de12ec5d391009aacccfd4e973a8b9b
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99601439"
---
# Get-FormatData

## 개요
현재 세션에 있는 형식 지정 데이터를 가져옵니다.

## SYNTAX

```
Get-FormatData [[-TypeName] <String[]>] [-PowerShellVersion <Version>] [<CommonParameters>]
```

## 설명

`Get-FormatData`Cmdlet은 현재 세션의 형식 지정 데이터를 가져옵니다.

세션의 형식 지정 데이터에는 디렉터리에 있는 형식 지정 파일의 형식 지정, `Format.ps1xml` `$PSHOME` 세션으로 가져오는 모듈의 데이터 형식 지정, cmdlet을 사용 하 여 세션으로 가져오는 명령의 데이터 서식 지정 등이 포함 됩니다 `Import-PSSession` .

이 cmdlet을 사용하여 형식 지정 데이터를 검사할 수 있습니다. 그런 다음 cmdlet을 사용 `Export-FormatData` 하 여 개체를 serialize 하 고 XML로 변환 하 여 파일에 저장할 수 있습니다 `Format.ps1xml` .

PowerShell에서 파일의 형식을 지정 하는 방법에 대 한 자세한 내용은 [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md)을 참조 하세요.

## 예제

### 예제 1: 모든 형식 지정 데이터 가져오기

이 예에서는 세션의 모든 형식 지정 데이터를 가져옵니다.

```powershell
Get-FormatData
```

### 예제 2: 형식 이름으로 형식 지정 데이터 가져오기

이 예제에서는 이름이로 시작 하는 형식 지정 데이터 항목을 가져옵니다 `System.Management.Automation.Cmd` .

```powershell
Get-FormatData -TypeName 'System.Management.Automation.Cmd*'
```

### 예제 3: 형식 지정 데이터 개체 검사

이 예제에서는 형식 지정 데이터 개체를 가져오고 해당 속성을 검사하는 방법을 보여 줍니다.

```powershell
$F = Get-FormatData -TypeName 'System.Management.Automation.Cmd*'
$F
```

```Output
TypeName        FormatViewDefinition
--------        --------------------
HelpInfoShort   {help , TableControl}
```

```powershell
$F.FormatViewDefinition[0].control
```

```Output
Headers          : {System.Management.Automation.TableControlColumnHeader,
                   System.Management.Automation.TableControlColumnHeader,
                   System.Management.Automation.TableControlColumnHeader,
                   System.Management.Automation.TableControlColumnHeader}
Rows             : {System.Management.Automation.TableControlRow}
AutoSize         : False
HideTableHeaders : False
GroupBy          :
OutOfBand        : False
```

```powershell
$F.FormatViewDefinition[0].control.Headers
```

```Output
Label       Alignment Width
-----       --------- -----
CommandType Undefined    15
Name        Undefined    50
Version     Undefined    10
Source      Undefined     0
```

### 예제 4: 형식 지정 데이터 가져오기 및 내보내기

이 예제에서는 및를 사용 하 여 `Get-FormatData` `Export-FormatData` 모듈에 의해 추가 된 서식 지정 데이터를 내보내는 방법을 보여 줍니다.

```powershell
$A = Get-FormatData
Import-Module bitstransfer
$B = Get-FormatData
Compare-Object $A $B
```

```Output
InputObject                                                SideIndicator
-----------                                                -------------
Microsoft.BackgroundIntelligentTransfer.Management.BitsJob =>
```

```powershell
Get-FormatData *bits* | Export-FormatData -FilePath c:\test\bits.format.ps1xml
Get-Content c:\test\bits.format.ps1xml
```

```Output
<?xml version="1.0" encoding="utf-8"?><Configuration><ViewDefinitions>
<View><Name>Microsoft.BackgroundIntelligentTransfer.Management.BitsJob</Name>
...
```

처음 4 개 명령은 `Get-FormatData` , `Import-Module` 및 cmdlet을 사용 `Compare-Object` 하 여 **BitsTransfer** 모듈이 세션에 추가 하는 형식 유형을 식별 합니다.

다섯 번째 명령은 cmdlet을 사용 하 여 `Get-FormatData` **BitsTransfer** 모듈이 추가 하는 형식 유형을 가져옵니다. 파이프라인 연산자 ()를 사용 하 여 `|` 형식 형식 개체를 cmdlet으로 보냅니다 `Export-FormatData` .이 cmdlet은 다시 XML로 변환 하 여 지정 된 파일에 저장 `format.ps1xml` 합니다.

마지막 명령은 파일 내용의 발췌를 표시 합니다 `format.ps1xml` .

### 예 5: 지정 된 버전의 PowerShell을 기반으로 하 여 형식 지정 데이터 가져오기

이 예제에서는를 사용 하 여 `Get-FormatData` 지정 된 **TypeName** 및 PowerShell 버전에 대 한 형식 데이터를 가져오는 방법을 보여 줍니다.

```powershell
Get-FormatData -TypeName 'Microsoft.Powershell.Utility.FileHash' -PowerShellVersion $PSVersionTable.PSVersion

TypeNames                               FormatViewDefinition
---------                               --------------------
{Microsoft.Powershell.Utility.FileHash} {Microsoft.Powershell.Utility.FileHash}
```

## PARAMETERS

### -PowerShellVersion

이 cmdlet이 형식 지정 데이터에 대해 가져오는 PowerShell 버전을 지정 합니다. 마침표로 구분 된 두 자리 숫자를 입력 합니다.

이 매개 변수는 이전 버전의 PowerShell을 실행 하는 원격 컴퓨터에서 호환성을 개선 하기 위해 PowerShell 5.1에 추가 되었습니다.

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TypeName

이 cmdlet이 형식 지정 데이터에 대해 가져오는 형식 이름을 지정 합니다.
유형 이름을 입력합니다.
와일드카드가 지원됩니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### 없음

이 cmdlet에 입력을 파이프할 수 없습니다.

## 출력

### System.web. ExtendedTypeDefinition

## 참고

## 관련 링크

[Export-FormatData](Export-FormatData.md)

[Update-FormatData](Update-FormatData.md)
