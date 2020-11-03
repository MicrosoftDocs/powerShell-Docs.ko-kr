---
external help file: Microsoft.PowerShell.Archive-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Archive
ms.date: 07/17/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.archive/expand-archive?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Expand-Archive
ms.openlocfilehash: 3775cea92ee32a54921bd9441de2c3e0f5915d1d
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/18/2020
ms.locfileid: "93218057"
---
# Expand-Archive

## 개요
지정 된 보관 파일 (zip)에서 파일을 추출 합니다.

## SYNTAX

### Path (기본값)

```
Expand-Archive [-Path] <String> [[-DestinationPath] <String>] [-Force] [-PassThru] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### LiteralPath

```
Expand-Archive -LiteralPath <String> [[-DestinationPath] <String>] [-Force] [-PassThru] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## 설명

Cmdlet은 지정 된 `Expand-Archive` 압축 된 보관 파일에서 지정 된 대상 폴더로 파일을 추출 합니다. 보관 파일을 사용 하면 여러 파일을 패키지 하 고 필요에 따라 압축 하 여 보다 쉽게 배포 하 고 저장할 수 있습니다.

## 예제

### 예제 1: 보관 파일의 콘텐츠 추출

이 예제에서는 **DestinationPath** 매개 변수로 지정 된 폴더로 기존 보관 파일의 콘텐츠를 추출 합니다.

```powershell
Expand-Archive -LiteralPath 'C:\Archives\Draft[v1].Zip' -DestinationPath C:\Reference
```

이 예에서는 **LiteralPath** 매개 변수를 사용 합니다 .이 경우 파일 이름에는 와일드 카드로 해석 될 수 있는 문자가 포함 됩니다.

### 예 2: 현재 폴더에서 보관 파일의 압축 풀기

이 예제에서는 현재 폴더에 있는 기존 보관 파일의 콘텐츠를 **DestinationPath** 매개 변수로 지정 된 폴더로 추출 합니다.

```powershell
Expand-Archive -Path Draftv2.Zip -DestinationPath C:\Reference
```

## PARAMETERS

### -DestinationPath

기본적으로는 `Expand-Archive` ZIP 파일과 동일한 이름의 폴더를 현재 위치에 만듭니다. 매개 변수를 사용 하 여 다른 폴더에 대 한 경로를 지정할 수 있습니다. 대상 폴더가 없으면 만들어집니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: A folder in the current location
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

사용자 확인을 요청하지 않고 명령을 강제 실행합니다.

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

### -LiteralPath

보관 파일의 경로를 지정 합니다. **Path** 매개 변수와 달리 **LiteralPath** 값은 입력한 대로 사용됩니다. 와일드카드 문자는 지원되지 않습니다. 경로에 이스케이프 문자가 포함 된 경우 각 이스케이프 문자를 작은따옴표로 묶어 PowerShell에서 문자를 이스케이프 시퀀스로 해석 하지 않도록 합니다.

```yaml
Type: System.String
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PassThru

Cmdlet이 보관 파일에서 확장 된 파일 목록을 출력 하도록 합니다.

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

보관 파일의 경로를 지정 합니다.

```yaml
Type: System.String
Parameter Sets: Path
Aliases:

Required: True
Position: 0
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

### System.String

기존 보관 파일에 대 한 경로가 포함 된 문자열을 파이프 할 수 있습니다.

## 출력

### FileSystemInfo

`-PassThru`매개 변수를 사용 하는 경우 cmdlet은 보관 파일에서 확장 된 파일 목록을 출력 합니다.

## 참고

[ZIP 파일 사양은](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) ASCII가 아닌 문자를 포함 하는 파일 이름을 인코딩 하는 표준 방법을 지정 하지 않습니다. `Compress-Archive`Cmdlet은 utf-8 인코딩을 사용 합니다. 다른 ZIP 보관 도구는 다른 인코딩 체계를 사용할 수 있습니다. UTF-8 인코딩을 사용 하 여 저장 되지 않은 파일 이름을 가진 파일을 추출할 때는 `Expand-Archive` 보관 파일에 있는 원시 값을 사용 합니다. 이로 인해 보관 파일에 저장 된 원본 파일 이름과 다른 파일 이름을 사용할 수 있습니다.

## 관련 링크

[Compress-Archive](compress-archive.md)
