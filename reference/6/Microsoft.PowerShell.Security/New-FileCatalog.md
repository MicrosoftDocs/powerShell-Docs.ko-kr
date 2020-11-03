---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 11/02/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/new-filecatalog?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-FileCatalog
ms.openlocfilehash: 861733acd34523ae0d0065f6923948aa45f66f04
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93216897"
---
# New-FileCatalog

## 개요
`New-FileCatalog` 파일의 신뢰성을 확인 하는 데 사용할 수 있는 파일 해시의 카탈로그 파일을 만듭니다.

## SYNTAX

```
New-FileCatalog [-CatalogVersion <Int32>] [-CatalogFilePath] <String> [[-Path] <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## 설명

`New-FileCatalog` 폴더 및 파일 집합에 대 한 [Windows 카탈로그 파일](/windows-hardware/drivers/install/catalog-files) 을 만듭니다.
이 카탈로그 파일에는 제공 된 경로에 있는 모든 파일에 대 한 해시가 포함 되어 있습니다.
사용자는 카탈로그를 만든 시간 이후 폴더가 변경 되었는지 여부를 확인할 수 있도록 해당 파일을 사용 하 여 카탈로그를 배포할 수 있습니다.

카탈로그 버전 1과 2가 지원됩니다. 버전 1은 (사용 되지 않음) SHA1 해시 알고리즘을 사용 하 여 파일 해시를 만들고 버전 2는 s h a 1을 사용 합니다.
Windows Server 2008 R2 또는 Windows 7에서는 카탈로그 버전 2가 지원되지 않습니다.
Windows 8, Windows Server 2012 및 이후 운영 체제에서는 카탈로그 버전 2를 사용해야 합니다.

## 예제

### 예제 1:에 대 한 파일 카탈로그 만들기 `Microsoft.PowerShell.Utility`

```powershell
New-FileCatalog -Path $PSHOME\Modules\Microsoft.PowerShell.Utility -CatalogFilePath \temp\Microsoft.PowerShell.Utility.cat -CatalogVersion 2.0
```

```Output
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----         11/2/2018 11:58 AM            950 Microsoft.PowerShell.Utility.cat
```

## PARAMETERS

### -CatalogFilePath

카탈로그 파일 (.cat)을 배치 해야 하는 파일이 나 폴더에 대 한 경로입니다.
폴더 경로를 지정 하는 경우 기본 파일 이름이 `catalog.cat` 사용 됩니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -CatalogVersion

`1.0` `2.0` 카탈로그 버전을 지정 하기 위해 또는 가능한 값을 허용 합니다.
`1.0` 가능 하면 안전 하지 않은 SHA-1 해시 알고리즘을 사용 하 고 `2.0` 보안 sha-256 알고리즘을 사용 하지만 `1.0` Windows 7 및 Server 2008 r 2에서 유일 하 게 지원 되는 알고리즘을 사용 해야 합니다.

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

### -Path

카탈로그 파일에 포함 되어야 하는 파일이 나 폴더에 대 한 경로 또는 경로 배열을 허용 합니다.
폴더를 지정 하면 폴더의 모든 파일도 포함 됩니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
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

cmdlet을 실행할 경우 발생하는 일을 표시합니다.
cmdlet은 실행되지 않습니다.

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

파이프라인은 카탈로그 파일 이름으로 사용 되는 문자열을 사용 합니다.

## 출력

### System.object

## 참고

## 관련 링크

[Test-FileCatalog](Test-FileCatalog.md)

[PowerShellGet](/powerShell/module/powershellget)
