---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/18/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/add-content?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-Content
ms.openlocfilehash: 70ef5033c3c5d37ed00a88abfb0d1353f5d10854
ms.sourcegitcommit: bf07cffb2a66dec94bf3576e197090f958701f18
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/19/2020
ms.locfileid: "99605493"
---
# Add-Content

## 개요
파일에 단어를 추가하는 것과 같이 지정된 항목에 내용을 추가합니다.

## SYNTAX

### Path (기본값)

```
Add-Content [-Path] <string[]> [-Value] <Object[]> [-PassThru] [-Filter <string>]
 [-Include <string[]>] [-Exclude <string[]>] [-Force] [-Credential <pscredential>] [-WhatIf]
 [-Confirm] [-NoNewline] [-Encoding <Encoding>] [-AsByteStream] [-Stream <string>]
 [<CommonParameters>]
```

### LiteralPath

```
Add-Content [-Value] <Object[]> -LiteralPath <string[]> [-PassThru] [-Filter <string>]
 [-Include <string[]>] [-Exclude <string[]>] [-Force] [-Credential <pscredential>] [-WhatIf]
 [-Confirm] [-NoNewline] [-Encoding <Encoding>] [-AsByteStream] [-Stream <string>]
 [<CommonParameters>]
```

## 설명

`Add-Content`Cmdlet은 지정 된 항목 또는 파일에 콘텐츠를 추가 합니다. 명령에 내용을 입력하거나 해당 내용이 포함된 개체를 지정하여 내용을 지정할 수 있습니다.

다음 예제를 위해 파일이 나 디렉터리를 만들어야 하는 경우에는 [새 항목](New-Item.md)을 참조 하세요.

## 예제

### 예제 1: 예외를 사용 하 여 모든 텍스트 파일에 문자열 추가

이 예제에서는 현재 디렉터리에 있는 텍스트 파일에 값을 추가 하지만 파일 이름에 따라 파일을 제외 합니다.

```powershell
Add-Content -Path .\*.txt -Exclude help* -Value 'End of file'
```

**Path** 매개 변수는 `.txt` 현재 디렉터리에 있는 모든 파일을 지정 하지만 **제외** 매개 변수는 지정 된 패턴과 일치 하는 파일 이름을 무시 합니다. **값** 매개 변수는 파일에 기록 되는 텍스트 문자열을 지정 합니다.

### 예제 2: 지정 된 파일의 끝에 날짜 추가

이 예에서는 현재 디렉터리에 있는 파일에 날짜를 추가 하 고 PowerShell 콘솔에 해당 날짜를 표시 합니다.

```powershell
Add-Content -Path .\DateTimeFile1.log, .\DateTimeFile2.log -Value (Get-Date) -PassThru
Get-Content -Path .\DateTimeFile1.log
```

```Output
Tuesday, May 14, 2019 8:24:27 AM
Tuesday, May 14, 2019 8:24:27 AM
5/14/2019 8:24:27 AM
```

`Add-Content`Cmdlet은 현재 디렉터리에 두 개의 새 파일을 만듭니다. **값** 매개 변수는 cmdlet의 출력을 포함 합니다 `Get-Date` . **PassThru** 매개 변수는 추가 된 내용을 파이프라인에 출력 합니다.
출력을 받을 다른 cmdlet이 없으므로 PowerShell 콘솔에 표시 됩니다.
`Get-Content`Cmdlet은 업데이트 된 파일인를 표시 합니다 `DateTimeFile1.log` .

### 예제 3: 지정 된 파일의 내용을 다른 파일에 추가

이 예제에서는 파일에서 콘텐츠를 가져와서 변수에 저장 합니다. 변수는 다른 파일에 콘텐츠를 추가 하는 데 사용 됩니다.

```powershell
$From = Get-Content -Path .\CopyFromFile.txt
Add-Content -Path .\CopyToFile.txt -Value $From
Get-Content -Path .\CopyToFile.txt
```

- `Get-Content`Cmdlet은의 내용을 가져오고 `CopyFromFile.txt` 해당 내용을 변수에 저장 합니다 `$From` .
- `Add-Content`Cmdlet은 `CopyToFile.txt` 변수의 내용을 사용 하 여 파일을 업데이트 합니다 `$From` .
- 이 `Get-Content` cmdlet은 CopyToFile.txt를 표시 합니다.

### 예제 4: 파이프라인을 사용 하 여 지정 된 파일의 내용을 다른 파일에 추가

이 예제에서는 파일에서 콘텐츠를 가져와 cmdlet으로 파이프 `Add-Content` 합니다.

```powershell
Get-Content -Path .\CopyFromFile.txt | Add-Content -Path .\CopyToFile.txt
Get-Content -Path .\CopyToFile.txt
```

`Get-Content`Cmdlet은의 내용을 가져옵니다 `CopyFromFile.txt` . 결과는를 업데이트 하는 cmdlet으로 파이프 됩니다 `Add-Content` `CopyToFile.txt` .
마지막 `Get-Content` cmdlet이 표시 됩니다 `CopyToFile.txt` .

### 예 5: 새 파일 만들기 및 콘텐츠 복사

이 예에서는 새 파일을 만들고 기존 파일의 내용을 새 파일에 복사 합니다.

```powershell
Add-Content -Path .\NewFile.txt -Value (Get-Content -Path .\CopyFromFile.txt)
Get-Content -Path .\NewFile.txt
```

- `Add-Content`Cmdlet은 **Path** 및 **Value** 매개 변수를 사용 하 여 현재 디렉터리에 새 파일을 만듭니다.
- `Get-Content`Cmdlet은 기존 파일의 내용을 가져와 `CopyFromFile.txt` **Value** 매개 변수에 전달 합니다. Cmdlet 주위의 괄호는 명령이 `Get-Content` 시작 되기 전에 명령이 완료 되도록 합니다 `Add-Content` .
- `Get-Content`Cmdlet은 새 파일의 내용을 표시 합니다 `NewFile.txt` .

### 예제 6: 읽기 전용 파일에 콘텐츠 추가

이 명령은 **IsReadOnly** File 특성이 **True** 로 설정 된 경우에도 파일에 값을 추가 합니다.
읽기 전용 파일을 만드는 단계는 예제에 포함 되어 있습니다.

```powershell
New-Item -Path .\IsReadOnlyTextFile.txt -ItemType File
Set-ItemProperty -Path .\IsReadOnlyTextFile.txt -Name IsReadOnly -Value $True
Get-ChildItem -Path .\IsReadOnlyTextFile.txt
Add-Content -Path .\IsReadOnlyTextFile.txt -Value 'Add value to read-only text file' -Force
Get-Content -Path .\IsReadOnlyTextFile.txt
```

```Output
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-ar--         1/28/2019     13:35              0 IsReadOnlyTextFile.txt
```

- `New-Item`Cmdlet은 **Path** 및 **ItemType** 매개 변수를 사용 하 여 `IsReadOnlyTextFile.txt` 현재 디렉터리에 파일을 만듭니다.
- `Set-ItemProperty`Cmdlet은 **Name** 및 **Value** 매개 변수를 사용 하 여 파일의 **IsReadOnly** 속성을 True로 변경 합니다.
- `Get-ChildItem`이 cmdlet은 파일이 비어 있고 (0) 읽기 전용 특성 ()을 포함 하 고 있는 것을 보여 줍니다 `r` .
- `Add-Content`Cmdlet은 **Path** 매개 변수를 사용 하 여 파일을 지정 합니다. **값** 매개 변수는 파일에 추가할 텍스트 문자열을 포함 합니다. **Force** 매개 변수는 읽기 전용 파일에 텍스트를 씁니다.
- `Get-Content`Cmdlet은 **Path** 매개 변수를 사용 하 여 파일의 내용을 표시 합니다.

읽기 전용 특성을 제거 하려면 `Set-ItemProperty` **값** 매개 변수를로 설정 하 여 명령을 사용 `False` 합니다.

### 예 7: Add-Content에서 필터 사용

Cmdlet에 대 한 필터를 지정할 수 있습니다 `Add-Content` . 필터를 사용 하 여 **path** 매개 변수를 한 정하는 경우 후행 별표 ()를 포함 하 여 `*` 경로의 내용을 나타내야 합니다.

다음 명령은 디렉터리에 있는 모든 파일의 내용을 "Done" 이라는 단어를 추가 합니다 `*.txt` `C:\Temp` .

```powershell
Add-Content -Path C:\Temp\* -Filter *.txt -Value "Done"
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

Encoding은 파일 시스템 공급자가 cmdlet에 추가 하는 동적 매개 변수입니다 `Add-Content` . 이 매개 변수는 파일 시스템 드라이브에만 작동합니다.

이 매개 변수에 허용 되는 값은 다음과 같습니다.

- `ascii`: ASCII (7 비트) 문자 집합에 대 한 인코딩을 사용 합니다.
- `bigendianunicode`: 빅 endian 바이트 순서를 사용 하 여 UTF-16 형식으로 인코딩합니다.
- `bigendianutf32`: 빅 endian 바이트 순서를 사용 하 여 u t f-32 형식으로 인코딩합니다.
- `oem`: MS-DOS 및 콘솔 프로그램에 기본 인코딩을 사용 합니다.
- `unicode`: 작은 endian 바이트 순서를 사용 하 여 UTF-16 형식으로 인코딩합니다.
- `utf7`: UTF-7 형식으로 인코딩합니다.
- `utf8`: UTF-8 형식으로 인코딩합니다.
- `utf8BOM`: 바이트 순서 표시 (BOM)를 사용 하 여 UTF-8 형식으로 인코딩합니다.
- `utf8NoBOM`: BOM (바이트 순서 표시) 없이 UTF-8 형식으로 인코딩합니다.
- `utf32`: U t f-32 형식으로 인코딩합니다.

PowerShell 6.2부터 **Encoding** 매개 변수를 사용 하 여 등록 된 코드 페이지의 숫자 id (예: `-Encoding 1251` ) 또는 등록 된 코드 페이지의 문자열 이름을 사용할 수도 있습니다 (예: `-Encoding "windows-1251"` ). 자세한 내용은 [인코딩에](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2)대 한 .net 설명서를 참조 하세요.

> [!NOTE]
> **U t f-7** _은 더 이상 사용 하지 않는 것이 좋습니다. PowerShell 7.1에서는 `utf7` _ *Encoding** 매개 변수에 대해를 지정 하는 경우 경고가 기록 됩니다.

```yaml
Type: System.Text.Encoding
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, BigEndianUTF32, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

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

읽기 전용 특성을 재정의하여 읽기 전용 파일에 내용을 추가할 수 있도록 합니다. 예를 들어 **Force** 는 읽기 전용 특성을 재정의하거나, 디렉터리를 만들어 파일 경로를 완성할 수 있지만 파일 사용 권한을 변경하지는 못합니다.

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

이 cmdlet이 콘텐츠에 새 줄 또는 캐리지 리턴을 추가 하지 않음을 나타냅니다.

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

추가된 내용을 나타내는 개체를 반환합니다. 기본적으로 이 cmdlet은 출력을 생성하지 않습니다.

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

추가 내용을 받는 항목의 경로를 지정합니다.
와일드카드 문자를 사용할 수 있습니다.
경로는 컨테이너가 아니라 항목의 경로여야 합니다.
예를 들어 디렉터리의 경로가 아니라 하나 이상의 파일 경로를 지정해야 합니다.
여러 경로를 지정하는 경우 쉼표를 사용하여 경로를 구분합니다.

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

> [!NOTE]
> 이 매개 변수는 Windows 에서만 사용할 수 있습니다.

콘텐츠에 대 한 대체 데이터 스트림을 지정 합니다. 스트림이 없는 경우이 cmdlet은이를 만듭니다. 와일드카드 문자는 지원되지 않습니다.

**스트림은** 파일 시스템 공급자가에 추가 하는 동적 매개 변수입니다 `Add-Content` . 이 매개 변수는 파일 시스템 드라이브에만 작동합니다.

Cmdlet을 사용 하 여 `Add-Content` 와 같은 대체 데이터 스트림의 콘텐츠를 변경할 수 있습니다 `Zone.Identifier` . 그러나이 방법은 인터넷에서 다운로드 된 파일을 차단 하는 보안 검사를 제거 하는 방법으로 권장 되지 않습니다. 다운로드 한 파일이 안전한 지 확인 하려면 cmdlet을 사용 `Unblock-File` 합니다.

이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.  PowerShell 7.2을 기준으로는 `Add-Content` 파일 및 디렉터리에서 대체 데이터 스트림을 대상으로 지정할 수 있습니다.


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

추가할 내용을 지정합니다. **이 데이터는 내부용 으로만 사용 되** 는 따옴표로 묶인 문자열을 입력 하거나를 생성 하는 **DateTime** 개체와 같이 콘텐츠가 포함 된 개체를 지정 `Get-Date` 합니다.

경로는 단지 문자열 이므로 경로를 입력 하 여 파일의 내용을 지정할 수 없습니다.
명령을 사용 하 여 `Get-Content` 콘텐츠를 가져와서 **Value** 매개 변수에 전달할 수 있습니다.

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

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.object, System.web. PSCredential

값, 경로 또는 자격 증명을로 파이프 할 수 있습니다 `Set-Content` .

## 출력

### 없음 또는 System.String

**PassThru** 매개 변수를 사용 하는 경우는 `Add-Content` 콘텐츠를 나타내는 **system.string** 개체를 생성 합니다. 그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.

## 참고

- 개체를로 파이프 하면 `Add-Content` 개체가 항목에 추가 되기 전에 문자열로 변환 됩니다. 개체 유형에 따라 문자열 형식이 결정되지만 형식이 개체의 기본 표시 형식과 다를 수도 있습니다. 문자열 형식을 제어하려면 보내는 cmdlet의 형식 지정 매개 변수를 사용합니다.
- 의 기본 제공 별칭인를 참조할 수도 있습니다 `Add-Content` `ac` . 자세한 내용은 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)를 참조 하세요.
- `Add-Content`Cmdlet은 모든 공급자가 제공 하는 데이터에 사용할 수 있습니다. 세션에서 사용할 수 있는 공급자를 나열 하려면을 입력 `Get-PSProvider` 합니다. 자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.

## 관련 링크

[about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

[Clear-Content](Clear-Content.md)

[Get-Content](Get-Content.md)

[Get-Item](Get-Item.md)

[New-Item](New-Item.md)

[Set-Content](Set-Content.md)
