---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 01/17/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-hex?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-Hex
ms.openlocfilehash: 64275e72f8c21942179431b3aed4a17d328aa2e9
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93216722"
---
# Format-Hex

## 개요

파일이 나 기타 입력을 16 진수로 표시 합니다.

## SYNTAX

### Path (기본값)

```
Format-Hex [-Path] <string[]> [-Count <long>] [-Offset <long>] [<CommonParameters>]
```

### LiteralPath

```
Format-Hex -LiteralPath <string[]> [-Count <long>] [-Offset <long>] [<CommonParameters>]
```

### InputObject

```
Format-Hex -InputObject <psobject> [-Encoding <Encoding>] [-Count <long>] [-Offset <long>] [-Raw] [<CommonParameters>]
```

## 설명

`Format-Hex`Cmdlet은 파일 또는 기타 입력을 16 진수 값으로 표시 합니다. 출력에서 문자의 오프셋을 확인 하려면 행의 맨 왼쪽에 있는 숫자를 해당 문자의 열 위쪽에 있는 숫자에 추가 합니다.

Cmdlet을 통해 `Format-Hex` 손상 된 파일이 나 파일 이름 확장명을 가질 수 없는 파일의 파일 형식을 확인할 수 있습니다. 이 cmdlet을 실행 한 다음 16 진수 출력을 읽어 파일 정보를 가져올 수 있습니다.

파일에서를 사용 하 `Format-Hex` 는 경우이 cmdlet은 줄 바꿈 문자를 무시 하 고 파일의 전체 내용을 줄 바꿈 문자가 유지 된 한 문자열로 반환 합니다.

## 예제

### 예제 1: 문자열의 16 진수 표현 가져오기

이 명령은 문자열의 16 진수 값을 반환 합니다.

```powershell
'Hello World' | Format-Hex
```

```Output
           00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F

00000000   48 65 6C 6C 6F 20 57 6F 72 6C 64                 Hello World
```

**Hello World** 문자열은 파이프라인에서 cmdlet으로 전송 됩니다 `Format-Hex` . 의 16 진수 출력은 `Format-Hex` 문자열의 각 문자 값을 표시 합니다.

### 예 2:16 진수 출력에서 파일 형식 찾기

이 예제에서는 16 진수 출력을 사용 하 여 파일 형식을 확인 합니다. Cmdlet은 파일의 전체 경로와 16 진수 값을 표시 합니다.

다음 명령을 테스트 하려면 로컬 컴퓨터에 기존 PDF 파일의 복사본을 만들고 복사한 파일의 이름을로 바꿉니다 `File.t7f` .

```powershell
Format-Hex -Path .\File.t7f
```

```Output
           Path: C:\Test\File.t7f

           00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F

00000000   25 50 44 46 2D 31 2E 35 0D 0A 25 B5 B5 B5 B5 0D  %PDF-1.5..%????.
00000010   0A 31 20 30 20 6F 62 6A 0D 0A 3C 3C 2F 54 79 70  .1 0 obj..<</Typ
00000020   65 2F 43 61 74 61 6C 6F 67 2F 50 61 67 65 73 20  e/Catalog/Pages
```

`Format-Hex`Cmdlet은 **Path** 매개 변수를 사용 하 여 t7f의 현재 디렉터리에 **파일** 이름을 지정 합니다. **T7f** 파일 확장명은 일반적이 지 않지만 16 진수 출력 **% pdf** 는 pdf 파일 임을 보여 줍니다.

## PARAMETERS

### -Encoding

출력의 인코딩을 지정 합니다. 이는 입력에만 적용 됩니다 `[string]` . 매개 변수는 숫자 형식에는 영향을 주지 않습니다. 기본값은 `utf8NoBOM`입니다.

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
Type: Encoding
Parameter Sets: ByInputObject
Aliases:
Accepted values: ASCII, BigEndianUnicode, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: Named
Default value: UTF8NoBOM
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

파이프라인 입력에 사용 됩니다. 파이프라인 입력은 `[system.io.fileinfo]` 에서 파이프에 대 한 특정 스칼라 형식 및 인스턴스만 지원 `Get-ChildItem` 합니다.

지원 되는 스칼라 형식은 다음과 같습니다.

- `[string]`, `[char]`
- `[byte]`, `[sbyte]`
- `[int16]`, `[uint16]`, `[short]`, `[ushort]`
- `[int]`, `[uint]`, `[int32]`, `[uint32]`,
- `[long]`, `[ulong]`, `[int64]`, `[uint64]`
- `[single]`, `[float]`, `[double]`

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: ByInputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -LiteralPath

파일의 전체 경로를 지정 합니다. **LiteralPath** 의 값은 입력 한 대로 사용 됩니다.
이 매개 변수는 와일드 카드 문자를 허용 하지 않습니다. 파일에 대 한 여러 경로를 지정 하려면 경로를 쉼표로 구분 합니다. **LiteralPath** 매개 변수에 이스케이프 문자가 포함 되어 있으면 경로를 작은따옴표로 묶습니다. PowerShell에서는 따옴표 붙은 단일 문자열의 문자를 이스케이프 시퀀스로 해석 하지 않습니다. 자세한 내용은 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)를 참조 하세요.

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

파일의 경로를 지정 합니다. 점 ()을 사용 `.` 하 여 현재 위치를 지정 합니다. 와일드 카드 문자 ( `*` )가 허용 되며, 위치에 있는 모든 항목을 지정 하는 데 사용할 수 있습니다. **Path** 매개 변수에 이스케이프 문자가 포함 되어 있으면 경로를 작은따옴표로 묶습니다. 파일에 대 한 여러 경로를 지정 하려면 경로를 쉼표로 구분 합니다.

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Raw

이 매개 변수는 더 이상 아무 작업도 수행 하지 않습니다. 스크립트 호환성을 위해 유지 됩니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -오프셋

이는 16 진수 출력의 일부에서 건너뛸 바이트 수를 나타냅니다.

이 매개 변수는 PowerShell 6.2에서 도입 되었습니다.

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 0
Accept pipeline input: False
Accept wildcard characters: False
```

### -개수

이 값은 16 진수 출력에 포함할 바이트 수를 나타냅니다.

이 매개 변수는 PowerShell 6.2에서 도입 되었습니다.

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Int64.MaxValue
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.String

이 cmdlet에 문자열을 파이프 하 여 지정할 수 있습니다.

## 출력

### ByteCollection.

이 cmdlet은 **ByteCollection** 를 반환 합니다. 이 개체는 바이트 컬렉션을 나타냅니다. 바이트 컬렉션을에서 반환 하는 출력의 각 줄 처럼 형식이 지정 된 문자열로 변환 하는 메서드를 포함 `Format-Hex` 합니다. **Path** 또는 **LiteralPath** 매개 변수를 지정 하는 경우 개체에는 각 바이트를 포함 하는 파일의 경로도 포함 됩니다.

## 참고

출력의 맨 오른쪽 열은 바이트를 ASCII 문자로 렌더링 하려고 시도 합니다.

일반적으로 각 바이트는 유니코드 코드 포인트로 해석 됩니다 .이는 다음을 의미 합니다.

- 인쇄 가능한 ASCII 문자는 항상 올바르게 렌더링 됩니다.
- 멀티 바이트 UTF-8 문자는 올바르게 렌더링 되지 않습니다.
- UTF-16 문자는 상위 바이트가 발생 하는 경우에만 올바르게 렌더링 됩니다 `NUL` .

## 관련 링크

[about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)

[Format-Custom](Format-Custom.md)

[Format-List](Format-List.md)

[Format-Table](Format-Table.md)

[Format-Wide](Format-Wide.md)
