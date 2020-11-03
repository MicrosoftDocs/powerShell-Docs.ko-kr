---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/25/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-powershelldatafile?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-PowerShellDataFile
ms.openlocfilehash: f83718f56a3c01ca59fcda697201ff4a3598b54a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93212962"
---
# Import-PowerShellDataFile

## 개요
`.PSD1`파일의 내용을 호출 하지 않고 파일에서 값을 가져옵니다.

## SYNTAX

### ByPath (기본값)

```
Import-PowerShellDataFile [-Path] <String[]> [<CommonParameters>]
```

### ByLiteralPath

```
Import-PowerShellDataFile [-LiteralPath] <String[]> [<CommonParameters>]
```

## 설명

`Import-PowerShellDataFile`Cmdlet은 파일에 정의 된 해시 테이블에서 키-값 쌍을 안전 하 게 가져옵니다 `.PSD1` . 파일의 내용에 따라를 사용 하 여 값을 가져올 수 있습니다 `Invoke-Expression` .
그러나는 `Invoke-Expression` 파일에 포함 된 모든 코드를 실행 합니다. 이렇게 하면 원치 않는 결과가 생성 되거나 안전 하지 않은 코드가 실행 될 수 있습니다. `Import-PowerShellDataFile` 코드를 호출 하지 않고 데이터를 가져옵니다.

## 예제

### 예제 1: PSD1에서 값 검색

이 예에서는 파일 내에 보관 된 해시 테이블에 저장 된 키-값 쌍을 검색 합니다 `Configuration.psd1` . `Get-Content` 는 파일의 내용을 표시 하는 데 사용 됩니다 `Configuration.psd1` .

```powershell
Get-Content .\Configuration.psd1
$config = Import-PowerShellDataFile .\Configuration.psd1
$config.AllNodes
```

```Output
@{
    AllNodes = @(
        @{
            NodeName = 'DSC-01'
        }
        @{
            NodeName = 'DSC-02'
        }
    )
}

Name                           Value
----                           -----
NodeName                       DSC-01
NodeName                       DSC-02
```

## PARAMETERS

### -LiteralPath

가져올 파일의 경로입니다. 경로의 모든 문자는 리터럴 값으로 처리 됩니다.
와일드 카드 문자는 처리 되지 않습니다.

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path

가져올 파일의 경로입니다. 와일드 카드를 사용할 수 있지만 첫 번째 일치 하는 파일만 가져옵니다.

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.

## 입력

## 출력

### System.Collections.Hashtable

## 참고

## 관련 링크

[Invoke-Expression](Invoke-Expression.md)

[Import-LocalizedData](Import-LocalizedData.md)

