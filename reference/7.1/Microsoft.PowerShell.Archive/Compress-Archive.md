---
external help file: Microsoft.PowerShell.Archive-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Archive
ms.date: 02/20/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.archive/compress-archive?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Compress-Archive
ms.openlocfilehash: 3bfa1db6d8ad14a5681e22f2708d6c69dc165d3d
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93217785"
---
# Compress-Archive

## 개요
지정 된 파일 및 디렉터리에서 압축 된 보관 파일 또는 압축 된 파일을 만듭니다.

## SYNTAX

### Path (기본값)

```
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-CompressionLevel <String>]
 [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### PathWithUpdate

```
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-CompressionLevel <String>] -Update
 [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### PathWithForce

```
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-CompressionLevel <String>] -Force
 [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### LiteralPathWithUpdate

```
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-CompressionLevel <String>]
 -Update [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### LiteralPathWithForce

```
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-CompressionLevel <String>]
 -Force [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### LiteralPath

```
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-CompressionLevel <String>]
 [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명

`Compress-Archive`Cmdlet은 하나 이상의 지정 된 파일 또는 디렉터리에서 압축 되거나 압축 된 보관 파일을 만듭니다. 아카이브는 배포 및 저장을 용이 하 게 하기 위해 선택적 압축을 사용 하 여 여러 파일을 단일 zip 파일로 패키지 합니다. **CompressionLevel** 매개 변수로 지정 된 압축 알고리즘을 사용 하 여 보관 파일을 압축할 수 있습니다.

`Compress-Archive`Cmdlet은 MICROSOFT .NET API [System.IO.Compression.Zip보관](/dotnet/api/system.io.compression.ziparchive) 을 사용 하 여 파일을 압축 합니다.
기본 API의 제한이 있으므로 최대 파일 크기는 2gb입니다.

일부 예제에서는 스 플랫를 사용 하 여 코드 샘플의 줄 길이를 줄입니다. 자세한 내용은 [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md)를 참조 하세요.

## 예제

### 예 1: 파일을 압축 하 여 보관 파일 만들기

이 예에서는 다른 디렉터리의 파일을 압축 하 여 보관 파일을 만듭니다. 와일드 카드는 특정 파일 확장명을 가진 모든 파일을 가져오는 데 사용 됩니다. **경로** 에 파일 이름만 지정 되므로 보관 파일에 디렉터리 구조가 없습니다.

```powershell
$compress = @{
  Path = "C:\Reference\Draftdoc.docx", "C:\Reference\Images\*.vsd"
  CompressionLevel = "Fastest"
  DestinationPath = "C:\Archives\Draft.Zip"
}
Compress-Archive @compress
```

**Path** 매개 변수는 와일드 카드를 사용 하 여 특정 파일 이름 및 파일 이름을 허용 `*.vsd` 합니다. **경로** 는 쉼표로 구분 된 목록을 사용 하 여 다른 디렉터리에서 파일을 가져옵니다. 압축 수준이 **가장 빠르게** 처리 시간을 단축 합니다. **DestinationPath** 매개 변수는 파일의 위치를 지정 합니다 `Draft.zip` . `Draft.zip`파일에는 `Draftdoc.docx` 및 확장명이 있는 모든 파일이 포함 되어 있습니다 `.vsd` .

### 예제 2: LiteralPath를 사용 하 여 파일 압축

이 예에서는 명명 된 특정 파일을 압축 하 고 새 보관 파일을 만듭니다. **경로** 에 파일 이름만 지정 되므로 보관 파일에 디렉터리 구조가 없습니다.

```powershell
$compress = @{
LiteralPath= "C:\Reference\Draft Doc.docx", "C:\Reference\Images\diagram2.vsd"
CompressionLevel = "Fastest"
DestinationPath = "C:\Archives\Draft.Zip"
}
Compress-Archive @compress
```

**LiteralPath** 매개 변수는 와일드 카드를 허용 하지 않으므로 절대 경로 및 파일 이름이 사용 됩니다. **경로** 는 쉼표로 구분 된 목록을 사용 하 여 다른 디렉터리에서 파일을 가져옵니다. 압축 수준이 **가장 빠르게** 처리 시간을 단축 합니다. **DestinationPath** 매개 변수는 파일의 위치를 지정 합니다 `Draft.zip` . 파일에는 `Draft.zip` 및만 포함 `Draftdoc.docx` `diagram2.vsd` 됩니다.

### 예 3: 루트 디렉터리를 포함 하는 디렉터리 압축

이 예제에서는 디렉터리를 압축 하 고 루트 디렉터리와 모든 파일 및 하위 디렉터리를 **포함** 하는 보관 파일을 만듭니다. **경로** 에서 루트 디렉터리를 지정 하기 때문에 보관 파일에는 디렉터리 구조가 있습니다.

```powershell
Compress-Archive -Path C:\Reference -DestinationPath C:\Archives\Draft.zip
```

`Compress-Archive`**Path** 매개 변수를 사용 하 여 루트 디렉터리를 지정 `C:\Reference` 합니다. **DestinationPath** 매개 변수는 보관 파일의 위치를 지정 합니다. `Draft.zip`보관 파일에는 `Reference` 루트 디렉터리와 모든 파일 및 하위 디렉터리가 포함 됩니다.

### 예 4: 루트 디렉터리를 제외 하는 디렉터리 압축

이 예에서는 **경로** 에서 별표 () 와일드 카드를 사용 하기 때문에 디렉터리를 압축 하 고 루트 디렉터리를 **제외** 하는 보관 파일을 만듭니다 `*` . 보관 파일에는 루트 디렉터리의 파일 및 하위 디렉터리를 포함 하는 디렉터리 구조가 포함 됩니다.

```powershell
Compress-Archive -Path C:\Reference\* -DestinationPath C:\Archives\Draft.zip
```

`Compress-Archive`**Path** 매개 변수를 사용 하 여 `C:\Reference` 별표 () 와일드 카드를 사용 하 여 루트 디렉터리를 지정 `*` 합니다. **DestinationPath** 매개 변수는 보관 파일의 위치를 지정 합니다. `Draft.zip`보관 파일에는 루트 디렉터리의 파일 및 하위 디렉터리가 포함 되어 있습니다. `Reference`루트 디렉터리는 보관 파일에서 제외 됩니다.

### 예 5: 루트 디렉터리의 파일만 압축

이 예제에서는 루트 디렉터리의 파일만 압축 하 고 보관 파일을 만듭니다. 파일만 압축 되므로 아카이브에는 디렉터리 구조가 없습니다.

```powershell
Compress-Archive -Path C:\Reference\*.* -DestinationPath C:\Archives\Draft.zip
```

`Compress-Archive`**Path** 매개 변수를 사용 하 여 `C:\Reference` 스타 별 **점 별** () 와일드 카드를 사용 하 여 루트 디렉터리를 지정 합니다 `*.*` . **DestinationPath** 매개 변수는 보관 파일의 위치를 지정 합니다. `Draft.zip`보관 파일에는 `Reference` 루트 디렉터리의 파일만 포함 되 고 루트 디렉터리는 제외 됩니다.

### 예제 6: 파이프라인을 사용 하 여 파일 보관

이 예제에서는 파일을 파이프라인으로 전송 하 여 보관 파일을 만듭니다. **경로** 에 파일 이름만 지정 되므로 보관 파일에 디렉터리 구조가 없습니다.

```powershell
Get-ChildItem -Path C:\Reference\Afile.txt, C:\Reference\Images\Bfile.txt |
  Compress-Archive -DestinationPath C:\Archives\PipelineFiles.zip
```

`Get-ChildItem`**Path** 매개 변수를 사용 하 여 다른 디렉터리에서 두 개의 파일을 지정 합니다. 각 파일은 **FileInfo** 개체로 표시 되며 파이프라인에서로 전송 됩니다 `Compress-Archive` .
지정 된 두 파일은에 보관 되어 `PipelineFiles.zip` 있습니다.

### 예 7: 파이프라인을 사용 하 여 디렉터리 보관

이 예에서는 파이프라인에서 디렉터리를 전송 하 여 보관 파일을 만듭니다. 파일은 **system.io.directoryinfo** 개체로 서 **FileInfo** 개체와 디렉터리로 보내집니다. 보관 디렉터리 구조는 루트 디렉터리를 포함 하지 않지만 해당 파일 및 하위 디렉터리는 보관 파일에 포함 됩니다.

```powershell
Get-ChildItem -Path C:\LogFiles | Compress-Archive -DestinationPath C:\Archives\PipelineDir.zip
```

`Get-ChildItem`**Path** 매개 변수를 사용 하 여 `C:\LogFiles` 루트 디렉터리를 지정 합니다. 각 **FileInfo** 및 **system.io.directoryinfo** 개체는 파이프라인으로 전송 됩니다.

`Compress-Archive` 각 개체를 `PipelineDir.zip` 보관 파일에 추가 합니다. 파이프라인 개체가 매개 변수 위치 0으로 수신 되기 때문에 **Path** 매개 변수를 지정 하지 않았습니다.

### 예 8: 재귀가 보관에 영향을 줄 수 있는 방법

이 예제에서는 재귀가 보관 파일의 파일을 중복 하는 방법을 보여 줍니다. 예를 들어를 `Get-ChildItem` **재귀** 매개 변수와 함께 사용 하는 경우입니다. 재귀 프로세스에서 각 **FileInfo** 및 **system.io.directoryinfo** 개체는 파이프라인으로 전송 되어 보관에 추가 됩니다.

```powershell
Get-ChildItem -Path C:\TestLog -Recurse |
  Compress-Archive -DestinationPath C:\Archives\PipelineRecurse.zip
```

`C:\TestLog`디렉터리에 파일이 없습니다. 파일이 포함 된 라는 하위 디렉터리를 포함 `testsub` `testlog.txt` 합니다.

`Get-ChildItem`**Path** 매개 변수를 사용 하 여 루트 디렉터리를 지정 `C:\TestLog` 합니다. **재귀** 매개 변수는 파일 및 디렉터리를 처리 합니다. 및 FileInfo 개체에 대해 **system.io.directoryinfo** 개체가 생성 됩니다 `testsub` **FileInfo** `testlog.txt` .

각 개체는 파이프라인에서로 전송 됩니다 `Compress-Archive` . **DestinationPath** 는 보관 파일의 위치를 지정 합니다. 파이프라인 개체가 매개 변수 위치 0으로 수신 되기 때문에 **Path** 매개 변수를 지정 하지 않았습니다.

다음 요약에서는 `PipelineRecurse.zip` 중복 파일을 포함 하는 보관 파일의 내용에 대해 설명 합니다.

- **System.io.directoryinfo** 개체는 디렉터리를 만들고 `testsub` `testlog.txt` 원래 디렉터리 구조를 반영 하는 파일을 포함 합니다.
- **FileInfo** 개체는 `testlog.txt` 아카이브의 루트에 중복을 만듭니다. 재귀가 파일 개체를로 보내기 때문에 중복 된 파일이 생성 됩니다 `Compress-Archive` . 파이프라인으로 전송 된 각 개체가 보관에 추가 되기 때문에이 동작이 예상 됩니다.

### 예 9: 기존 보관 파일 업데이트

이 예에서는 디렉터리에서 기존 보관 파일인 `Draft.Zip` 를 업데이트 `C:\Archives` 합니다. 이 예에서 기존 보관 파일에는 루트 디렉터리와 해당 파일 및 하위 디렉터리가 포함 되어 있습니다.

```powershell
Compress-Archive -Path C:\Reference -Update -DestinationPath C:\Archives\Draft.Zip
```

명령은 `Draft.Zip` `C:\Reference` 디렉터리와 해당 하위 디렉터리에 있는 기존 파일의 최신 버전으로 업데이트 합니다. 또는 해당 하위 디렉터리에 추가 된 새 파일 `C:\Reference` 은 업데이트 된 보관 파일에 포함 됩니다 `Draft.Zip` .

## PARAMETERS

### -CompressionLevel

보관 파일을 만들 때 적용할 압축 크기를 지정 합니다. 더 빠른 압축을 사용 하면 파일을 만드는 데 시간이 더 소요 되지만 파일 크기가 커질 수 있습니다.

이 매개 변수를 지정 하지 않으면 명령에서 기본값인 **최적** 을 사용 합니다.

이 매개 변수에 허용 되는 값은 다음과 같습니다.

- **가장 빠름**. 가장 빠른 압축 방법을 사용 하 여 처리 시간을 줄일 수 있습니다. 더 빠른 압축으로 인해 파일 크기가 커질 수 있습니다.
- **Nocompression**. 원본 파일을 압축 하지 않습니다.
- **최적**. 처리 시간은 파일 크기에 따라 달라 집니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Optimal, NoCompression, Fastest

Required: False
Position: Named
Default value: Optimal
Accept pipeline input: False
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

### -DestinationPath

이 매개 변수는 필수 이며 보관 출력 파일의 경로를 지정 합니다. **DestinationPath** 에는 압축 된 파일의 이름, 압축 된 파일에 대 한 절대 경로 또는 상대 경로를 포함 해야 합니다.

**DestinationPath** 의 파일 이름에 파일 이름 확장명이 없는 경우 `.zip` cmdlet은 `.zip` 파일 이름 확장명을 추가 합니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

사용자 확인을 요청하지 않고 명령을 강제 실행합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PathWithForce, LiteralPathWithForce
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -LiteralPath

아카이브 압축 파일에 추가 하려는 파일의 경로를 지정 합니다. **Path** 매개 변수와 달리 **LiteralPath** 의 값은 입력 한 대로 사용 됩니다. 어떠한 문자도 와일드카드로 해석되지 않습니다. 경로에 이스케이프 문자가 포함 된 경우 각 이스케이프 문자를 작은따옴표로 묶어 PowerShell에서 문자를 이스케이프 시퀀스로 해석 하지 않도록 합니다.
여러 경로를 지정 하 고 출력 압축 파일의 여러 위치에 파일을 포함 하려면 쉼표를 사용 하 여 경로를 구분 합니다.

```yaml
Type: System.String[]
Parameter Sets: LiteralPathWithUpdate, LiteralPathWithForce, LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PassThru

Cmdlet이 생성 된 보관 파일을 나타내는 파일 개체를 출력 하도록 합니다.

이 매개 변수는 PowerShell 6.0에서 도입 되었습니다.

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

### -Path

아카이브 압축 파일에 추가 하려는 파일의 경로를 지정 합니다. 여러 경로를 지정 하 고 여러 위치에 파일을 포함 하려면 쉼표를 사용 하 여 경로를 구분 합니다.

이 매개 변수는 와일드 카드 문자를 허용 합니다. 와일드 카드 문자를 사용 하 여 디렉터리의 모든 파일을 보관 파일에 추가할 수 있습니다.

루트 디렉터리와 함께 와일드 카드를 사용 하면 보관 파일의 내용에 영향을 줍니다.

- 루트 디렉터리와 모든 파일 및 하위 디렉터리를 **포함** 하는 보관 파일을 만들려면 **경로** 에 와일드 카드 없이 루트 디렉터리를 지정 합니다. `-Path C:\Reference`
- 루트 디렉터리를 **제외** 하 고 모든 파일 및 하위 디렉터리를 zips 보관 파일을 만들려면 별표 ( `*` ) 와일드 카드를 사용 합니다. `-Path C:\Reference\*`
- 루트 디렉터리의 파일만 zips 보관 파일을 만들려면 **star-점선** ( `*.*` ) 와일드 카드를 사용 합니다. 루트의 하위 디렉터리는 보관 파일에 포함 되지 않습니다. `-Path C:\Reference\*.*`

```yaml
Type: System.String[]
Parameter Sets: Path, PathWithUpdate, PathWithForce
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -업데이트

보관의 이전 파일 버전을 이름이 같은 최신 파일 버전으로 바꿔 지정 된 보관 파일을 업데이트 합니다. 이 매개 변수를 추가 하 여 기존 보관 파일에 파일을 추가할 수도 있습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PathWithUpdate, LiteralPathWithUpdate
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

cmdlet을 실행할 경우 발생하는 일을 표시합니다. Cmdlet이 실행 되지 않습니다.

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

### System.String

하나 이상의 파일에 대 한 경로가 포함 된 문자열을 파이프 할 수 있습니다.

## 출력

### System.object

이 cmdlet은 **PassThru** 매개 변수를 사용 하는 경우에만 **FileInfo** 개체를 반환 합니다.

## 참고

재귀를 사용 하 여 개체를 아래로 보내면 보관 파일의 파일이 중복 될 수 있습니다. 예를 들어를 `Get-ChildItem` **재귀** 매개 변수와 함께 사용 하는 경우 파이프라인으로 전송 된 각 **FileInfo** 및 **system.io.directoryinfo** 개체가 보관에 추가 됩니다.

[ZIP 파일 사양은](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) ASCII가 아닌 문자를 포함 하는 파일 이름을 인코딩 하는 표준 방법을 지정 하지 않습니다. `Compress-Archive`Cmdlet은 utf-8 인코딩을 사용 합니다. 다른 ZIP 보관 도구는 다른 인코딩 체계를 사용할 수 있습니다. UTF-8 인코딩을 사용 하 여 저장 되지 않은 파일 이름을 가진 파일을 추출할 때는 `Expand-Archive` 보관 파일에 있는 원시 값을 사용 합니다. 이로 인해 보관 파일에 저장 된 원본 파일 이름과 다른 파일 이름을 사용할 수 있습니다.

## 관련 링크

[Expand-Archive](Expand-Archive.md)

[Get-ChildItem](../Microsoft.PowerShell.Management/Get-ChildItem.md)

