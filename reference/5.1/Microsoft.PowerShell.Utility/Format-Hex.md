---
external help file: Microsoft.PowerShell.Utility-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 01/17/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-hex?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-Hex
ms.openlocfilehash: 514a66ebee3827de998622a738c75d4f8e0c7279
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93214026"
---
# Format-Hex

## 개요

파일이 나 기타 입력을 16 진수로 표시 합니다.

## SYNTAX

### Path (기본값)

```
Format-Hex [-Path] <string[]> [<CommonParameters>]
```

### LiteralPath

```
Format-Hex -LiteralPath <string[]> [<CommonParameters>]
```

### ByInputObject

```
Format-Hex -InputObject <Object> [-Encoding <string>] [-Raw] [<CommonParameters>]
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

다음 명령을 테스트 하려면 로컬 컴퓨터에서 기존 PDF 파일의 복사본을 만들고 복사한 파일의 이름을 **t7f** 로 바꿉니다.

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

`Format-Hex`Cmdlet은 **Path** 매개 변수를 사용 하 여 현재 디렉터리의 파일 이름을 지정 `File.t7f` 합니다. 파일 확장명은 `.t7f` 일반적이 지 않지만 16 진수 출력은 `%PDF` PDF 파일 임을 보여 줍니다.

### 예제 3: 원시 16 진수 출력 표시

기본적으로 `Format-Hex` opts는 숫자 데이터 형식의 압축 출력에 사용 됩니다. 값이 충분히 작은 경우 싱글바이트 또는 더블 바이트 시퀀스가 사용 됩니다. **Raw** 매개 변수는이 동작을 비활성화 합니다.

```
PS> 1,2,3,1000 | Format-Hex

           Path:

           00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F

00000000   01 02 03 E8 03                                   ...è.


PS> 1,2,3,1000 | Format-Hex -Raw

           Path:

           00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F

00000000   01 00 00 00 02 00 00 00 03 00 00 00 E8 03 00 00  ............è...
```

출력의 차이점을 확인 합니다. **원시** 매개 변수는 숫자를 4 바이트 값으로 표시 하 고 해당 **Int32** 형식에 true를 표시 합니다.

## PARAMETERS

### -Encoding

출력의 인코딩을 지정 합니다. 이는 입력에만 적용 됩니다 `[string]` . 매개 변수는 숫자 형식에는 영향을 주지 않습니다. 기본값은 `ASCII`입니다.

이 매개 변수에 허용 되는 값은 다음과 같습니다.

- `Ascii` ASCII (7 비트) 문자 집합을 사용 합니다.
- `BigEndianUnicode` 에서는 u t f-16을 빅 endian 바이트 순서로 사용 합니다.
- `Unicode` 는 u t f-16을 약간 endian 바이트 순서로 사용 합니다.
- `UTF7` 는 u t f-7을 사용 합니다.
- `UTF8` 는 u t f-8을 사용 합니다.
- `UTF32` 는 u t f-32을 작은 endian 바이트 순서로 사용 합니다.

입력의 ASCII가 아닌 문자는 리터럴 문자로 출력 되어 `?` 정보 손실이 발생 합니다.

```yaml
Type: System.String
Parameter Sets: ByInputObject
Aliases:
Accepted values: ASCII, BigEndianUnicode, Unicode, UTF7, UTF8, UTF32

Required: False
Position: Named
Default value: ASCII
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

파이프라인 입력에 사용 됩니다. 파이프라인 입력은 `[system.io.fileinfo]` 에서 파이프에 대 한 특정 스칼라 형식 및 인스턴스만 지원 `Get-ChildItem` 합니다.

지원 되는 스칼라 형식은 다음과 같습니다.

- `[string]`
- `[byte]`
- `[int]`, `[int32]`
- `[long]`, `[int64]`

```yaml
Type: System.Object
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
Aliases: PSPath

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

기본적으로 `Format-Hex` opts는 숫자 데이터 형식의 압축 출력에 사용 됩니다. 값이 충분히 작은 경우 싱글바이트 또는 더블 바이트 시퀀스가 사용 됩니다. **Raw** 매개 변수는이 동작을 비활성화 합니다.

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

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.String

이 cmdlet에 문자열을 파이프 하 여 지정할 수 있습니다.

## 출력

### ByteCollection.

이 cmdlet은 **ByteCollection** 를 반환 합니다. 이 개체는 바이트 컬렉션을 나타냅니다. 바이트 컬렉션을에서 반환 하는 출력의 각 줄 처럼 형식이 지정 된 문자열로 변환 하는 메서드를 포함 `Format-Hex` 합니다. **Path** 또는 **LiteralPath** 매개 변수를 지정 하는 경우 개체에는 각 바이트를 포함 하는 파일의 경로도 포함 됩니다.

## 참고

출력의 맨 오른쪽 열은 바이트를 문자로 렌더링 하려고 시도 합니다.

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
