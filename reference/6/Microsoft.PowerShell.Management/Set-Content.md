---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-content?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Content
ms.openlocfilehash: 33ed166b4e467d5c1054c936414a6628370f69d8
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93212290"
---
# Set-Content

## 개요
새 콘텐츠를 쓰거나 파일의 기존 내용을 바꿉니다.

## SYNTAX

### Path (기본값)

```
Set-Content [-Path] <string[]> [-Value] <Object[]> [-PassThru] [-Filter <string>]
 [-Include <string[]>] [-Exclude <string[]>] [-Force] [-Credential <pscredential>]
 [-WhatIf] [-Confirm] [-NoNewline] [-Encoding <Encoding>] [-AsByteStream] [-Stream <string>]
 [<CommonParameters>]
```

### LiteralPath

```
Set-Content [-Value] <Object[]> -LiteralPath <string[]> [-PassThru] [-Filter <string>]
 [-Include <string[]>] [-Exclude <string[]>] [-Force] [-Credential <pscredential>]
 [-WhatIf] [-Confirm] [-NoNewline] [-Encoding <Encoding>] [-AsByteStream] [-Stream <string>]
 [<CommonParameters>]
```

## 설명

`Set-Content` 는 새 콘텐츠를 쓰거나 파일의 내용을 바꾸는 문자열 처리 cmdlet입니다. `Set-Content` 기존 콘텐츠를 대체 하며 `Add-Content` 파일에 콘텐츠를 추가 하는 cmdlet과 다릅니다. 로 콘텐츠를 보내려면 `Set-Content` 명령줄에서 **Value** 매개 변수를 사용 하거나 파이프라인을 통해 콘텐츠를 보낼 수 있습니다.

다음 예제를 위해 파일이 나 디렉터리를 만들어야 하는 경우에는 [새 항목](New-Item.md)을 참조 하세요.

## 예제

### 예제 1: 디렉터리에서 여러 파일의 내용 바꾸기

이 예제에서는 현재 디렉터리에 있는 여러 파일의 콘텐츠를 대체 합니다.

```powershell
Get-ChildItem -Path .\Test*.txt
```

```Output
Test1.txt
Test2.txt
Test3.txt
```

```powershell
Set-Content -Path .\Test*.txt -Value 'Hello, World'
Get-Content -Path .\Test*.txt
```

```Output
Hello, World
Hello, World
Hello, World
```

`Get-ChildItem`Cmdlet은 **Path** 매개 변수를 사용 하 여 현재 디렉터리에서로 시작 하는 **.txt** 파일을 나열 합니다. `Test*` `Set-Content`Cmdlet은 **Path** 매개 변수를 사용 하 여 파일을 지정 합니다 `Test*.txt` . **Value** 매개 변수는 각 파일의 기존 내용을 대체 하는 텍스트 문자열 **Hello를** 제공 합니다. `Get-Content`Cmdlet은 **Path** 매개 변수를 사용 하 여 파일을 지정 하 `Test*.txt` 고 PowerShell 콘솔에 각 파일의 콘텐츠를 표시 합니다.

### 예제 2: 새 파일 만들기 및 콘텐츠 작성

이 예에서는 새 파일을 만들고 현재 날짜와 시간을 파일에 씁니다.

```powershell
Set-Content -Path .\DateTime.txt -Value (Get-Date)
Get-Content -Path .\DateTime.txt
```

```Output
1/30/2019 09:55:08
```

`Set-Content`**Path** 및 **Value** 매개 변수를 사용 하 여 현재 디렉터리에 **DateTime.txt** 라는 새 파일을 만듭니다. **값** 매개 변수는 `Get-Date` 를 사용 하 여 현재 날짜와 시간을 가져옵니다.
`Set-Content`**DateTime** 개체를 문자열로 파일에 씁니다. `Get-Content`Cmdlet은 **Path** 매개 변수를 사용 하 여 PowerShell 콘솔에 **DateTime.txt** 의 내용을 표시 합니다.

### 예제 3: 파일에서 텍스트 바꾸기

이 명령은 기존 파일 내에 있는 모든 word 인스턴스를 바꿉니다.

```powershell
Get-Content -Path .\Notice.txt
```

```Output
Warning
Replace Warning with a new word.
The word Warning was replaced.
```

```powershell
(Get-Content -Path .\Notice.txt) |
    ForEach-Object {$_ -Replace 'Warning', 'Caution'} |
        Set-Content -Path .\Notice.txt
Get-Content -Path .\Notice.txt
```

```Output
Caution
Replace Caution with a new word.
The word Caution was replaced.
```

`Get-Content`Cmdlet은 **Path** 매개 변수를 사용 하 여 현재 디렉터리에 있는 **Notice.txt** 파일을 지정 합니다. 명령이 `Get-Content` 파이프라인으로 전송 되기 전에 명령이 완료 되도록 괄호를 사용 하 여 명령이 래핑됩니다.

**Notice.txt** 파일의 내용이 파이프라인에서 cmdlet으로 전송 됩니다 `ForEach-Object` .
`ForEach-Object` 자동 변수를 사용 하 `$_` 고 **경고** 를 발생 하는 각 항목을 **주의** 하 여 바꿉니다. 개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Set-Content` . `Set-Content`**Path** 매개 변수를 사용 하 여 **Notice.txt** 파일을 지정 하 고 업데이트 된 콘텐츠를 파일에 씁니다.

마지막 `Get-Content` cmdlet은 PowerShell 콘솔에 업데이트 된 파일 콘텐츠를 표시 합니다.

### 예제 4: Set-Content에서 필터 사용

Cmdlet에 대 한 필터를 지정할 수 있습니다 `Set-Content` . 필터를 사용 하 여 **path** 매개 변수를 한 정하는 경우 후행 별표 ()를 포함 하 여 `*` 경로의 내용을 나타내야 합니다.

다음 명령은 `*.txt` 디렉터리에 있는 모든 파일의 내용을 `C:\Temp` 비어 있는 **값** 으로 설정 합니다.

```powershell
Set-Content -Path C:\Temp\* -Filter *.txt -Value "Empty"
```

## PARAMETERS

### -AsByteStream

콘텐츠를 바이트 스트림으로 읽도록 지정 합니다. 이 매개 변수는 PowerShell 6.0에서 도입 되었습니다.

**AsByteStream** 매개 변수를 **Encoding** 매개 변수와 함께 사용 하는 경우 경고가 발생 합니다. **AsByteStream** 매개 변수는 인코딩을 무시 하 고 출력은 바이트 스트림으로 반환 됩니다.

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

### -Credential

> [!NOTE]
> 이 매개 변수는 PowerShell과 함께 설치 된 모든 공급자에서 지원 되지 않습니다.
> 이 cmdlet을 실행할 때 다른 사용자를 가장 하거나 자격 증명을 상승 시키려면 [Invoke 명령을](../Microsoft.PowerShell.Core/Invoke-Command.md)사용 합니다.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Encoding

대상 파일의 인코딩 유형을 지정합니다. 기본값은 `utf8NoBOM`입니다.

Encoding은 파일 시스템 공급자가에 추가 하는 동적 매개 변수입니다 `Set-Content` . 이 매개 변수는 파일 시스템 드라이브에만 작동합니다.

이 매개 변수에 허용 되는 값은 다음과 같습니다.

- `ascii`: ASCII (7 비트) 문자 집합에 대 한 인코딩을 사용 합니다.
- `bigendianunicode`: 빅 endian 바이트 순서를 사용 하 여 UTF-16 형식으로 인코딩합니다.
- `oem`: MS-DOS 및 콘솔 프로그램에 기본 인코딩을 사용 합니다.
- `unicode`: 작은 endian 바이트 순서를 사용 하 여 UTF-16 형식으로 인코딩합니다.
- `utf7`: UTF-7 형식으로 인코딩합니다.
- `utf8`: UTF-8 형식으로 인코딩합니다.
- `utf8BOM`: 바이트 순서 표시 (BOM)를 사용 하 여 UTF-8 형식으로 인코딩합니다.
- `utf8NoBOM`: BOM (바이트 순서 표시) 없이 UTF-8 형식으로 인코딩합니다.
- `utf32`: U t f-32 형식으로 인코딩합니다.

PowerShell 6.2부터 **Encoding** 매개 변수를 사용 하 여 등록 된 코드 페이지의 숫자 id (예: `-Encoding 1251` ) 또는 등록 된 코드 페이지의 문자열 이름을 사용할 수도 있습니다 (예: `-Encoding "windows-1251"` ). 자세한 내용은 [인코딩에](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2)대 한 .net 설명서를 참조 하세요.

```yaml
Type: System.Text.Encoding
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: Named
Default value: UTF8NoBOM
Accept pipeline input: False
Accept wildcard characters: False
```

### -제외

이 cmdlet이 작업에서 제외 하는 항목을 문자열 배열로 지정 합니다. 이 매개 변수 값은 **Path** 매개 변수를 한정합니다. 경로 요소 또는 패턴 (예:)을 입력 `*.txt` 합니다. 와일드카드 문자를 사용할 수 있습니다. **Exclude** 매개 변수는 명령에와 같이 항목의 내용이 포함 된 경우에만 적용 됩니다 `C:\Windows\*` . 여기서 와일드 카드 문자는 디렉터리의 내용을 지정 합니다 `C:\Windows` .

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Filter

**Path** 매개 변수를 한정 하는 필터를 지정 합니다. [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) 공급자는 필터 사용을 지 원하는 유일한 설치 된 PowerShell 공급자입니다. [About_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)에서 **FileSystem** 필터 언어의 구문을 찾을 수 있습니다.
필터는 다른 매개 변수 보다 더 효율적입니다. cmdlet이 개체가 검색 된 후 개체를 필터링 하는 대신 개체를 가져올 때 해당 개체를 적용 하기 때문입니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Force

파일이 읽기 전용인 경우에도 cmdlet이 파일의 콘텐츠를 설정 하도록 합니다. 구현은 공급자에 따라 다릅니다. 자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.
**Force** 매개 변수는 보안 제한을 재정의 하지 않습니다.

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

### -포함

이 cmdlet이 작업에 포함 하는 항목 또는 항목을 문자열 배열로 지정 합니다. 이 매개 변수 값은 **Path** 매개 변수를 한정합니다. 경로 요소 또는 패턴 (예:)을 입력 `"*.txt"` 합니다. 와일드카드 문자를 사용할 수 있습니다. **Include** 매개 변수는 명령에와 같이 항목의 내용이 포함 된 경우에만 적용 됩니다 `C:\Windows\*` . 여기서 와일드 카드 문자는 디렉터리의 내용을 지정 합니다 `C:\Windows` .

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -LiteralPath

하나 이상의 위치에 대한 경로를 지정합니다. **LiteralPath** 의 값은 입력 한 대로 사용 됩니다. 어떠한 문자도 와일드카드로 해석되지 않습니다. 이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요. 작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.

자세한 내용은 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)를 참조 하세요.

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
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

### -PassThru

콘텐츠를 나타내는 개체를 반환 합니다. 기본적으로 이 cmdlet은 출력을 생성하지 않습니다.

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

### -Path

콘텐츠를 받는 항목의 경로를 지정 합니다.
와일드카드 문자를 사용할 수 있습니다.

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -스트림

콘텐츠에 대 한 대체 데이터 스트림을 지정 합니다. 스트림이 없는 경우이 cmdlet은이를 만듭니다. 와일드카드 문자는 지원되지 않습니다.

**스트림은** **파일 시스템** 공급자가에 추가 하는 동적 매개 변수입니다 `Set-Content` . 이 매개 변수는 파일 시스템 드라이브에만 작동합니다.

Cmdlet을 사용 하 여 `Set-Content` 영역의 콘텐츠를 변경할 수 있습니다 **. 식별자** 대체 데이터 스트림입니다. 그러나이 방법은 인터넷에서 다운로드 된 파일을 차단 하는 보안 검사를 제거 하는 방법으로 권장 되지 않습니다. 다운로드 한 파일이 안전한 지 확인 하려면 cmdlet을 사용 `Unblock-File` 합니다.

이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Value

항목의 새 내용을 지정합니다.

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Confirm

cmdlet을 실행하기 전에 확인을 요청합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

cmdlet을 실행할 경우 발생하는 일을 표시합니다. cmdlet은 실행되지 않습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet은,,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` 및 `-WarningVariable` 등의 일반 매개 변수를 지원 합니다.
자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.

## 입력

### System.Object

항목의 새 값을 포함 하는 개체를로 파이프 할 수 있습니다 `Set-Content` .

## 출력

### 없음 또는 System.String

**PassThru** 매개 변수를 사용 하는 경우는 `Set-Content` 콘텐츠를 나타내는 **system.string** 개체를 생성 합니다. 그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.

## 참고

- 의 기본 제공 별칭인를 참조할 수도 있습니다 `Set-Content` `sc` .
  자세한 내용은 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)를 참조 하세요.
- `Set-Content` 는 문자열 처리를 위해 설계 되었습니다. 문자열이 아닌 개체를에 파이프 하면 `Set-Content` 개체를 쓰기 전에 문자열로 변환 합니다. 개체를 파일에 쓰려면를 사용 `Out-File` 합니다.
- `Set-Content`Cmdlet은 모든 공급자가 제공 하는 데이터에 사용할 수 있습니다. 세션에서 사용할 수 있는 공급자를 나열 하려면을 입력 `Get-PsProvider` 합니다. 자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.

## 관련 링크

[about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)

[about_Automatic_Variables. md](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

[Add-Content](Add-Content.md)

[Clear-Content](Clear-Content.md)

[Get-ChildItem](Get-ChildItem.md)

[Get-Content](Get-Content.md)

[ForEach-Object](../Microsoft.PowerShell.Core/ForEach-Object.md)

[New-Item](New-Item.md)
