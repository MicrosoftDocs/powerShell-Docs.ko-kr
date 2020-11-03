---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/export-alias?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-Alias
ms.openlocfilehash: 4ddc9af276f1d24cc687652d96ffba77897305f0
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93210202"
---
# Export-Alias

## 개요
현재 정의된 별칭에 대한 정보를 파일로 내보냅니다.

## SYNTAX

### ByPath (기본값)

```
Export-Alias [-Path] <String> [[-Name] <String[]>] [-PassThru] [-As <ExportAliasFormat>] [-Append] [-Force]
 [-NoClobber] [-Description <String>] [-Scope <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByLiteralPath

```
Export-Alias -LiteralPath <String> [[-Name] <String[]>] [-PassThru] [-As <ExportAliasFormat>] [-Append]
 [-Force] [-NoClobber] [-Description <String>] [-Scope <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명

`Export-Alias`Cmdlet은 현재 세션의 별칭을 파일로 내보냅니다.
출력 파일이 없으면 cmdlet에서 출력 파일을 만듭니다.

`Export-Alias` 는 특정 범위 또는 모든 범위의 별칭을 내보낼 수 있습니다. 또한 CSV 형식으로 데이터를 생성 하거나, 세션 또는 PowerShell 프로필에 추가할 수 있는 일련의 Set-Alias 명령으로 데이터를 생성할 수 있습니다.

## 예제

### 예제 1: 별칭 내보내기

```powershell
Export-Alias -Path "alias.csv"
```

이 명령은 현재 별칭 정보를 현재 디렉터리의 Alias.csv 파일로 내보냅니다.

### 예 2: 내보내기 파일이 이미 존재 하지 않는 경우 별칭 내보내기

```powershell
Export-Alias -Path "alias.csv" -NoClobber
```

이 명령은 현재 세션의 별칭을 Alias.csv 파일로 내보냅니다.

**NoClobber** 매개 변수를 지정 하기 때문에 현재 디렉터리에 Alias.csv 파일이 이미 있으면 명령이 실패 합니다.

### 예제 3: 파일에 별칭 추가

```powershell
Export-Alias -Path "alias.csv" -Append -Description "Appended Aliases" -Force
```

이 명령은 현재 세션의 별칭을 Alias.csv 파일에 추가합니다.

이 명령은 **description** 매개 변수를 사용 하 여 파일의 맨 위에 있는 주석에 설명을 추가 합니다.

또한이 명령은 읽기 전용 특성이 있는 경우에도 **Force** 매개 변수를 사용 하 여 기존 Alias.csv 파일을 덮어씁니다.

### 예 4: 스크립트로 별칭 내보내기

```powershell
Export-Alias -Path "alias.ps1" -As Script
Add-Content -Path $Profile -Value (Get-Content alias.ps1)
$S = New-PSSession -ComputerName Server01
Invoke-Command -Session $S -FilePath .\alias.ps1
```

이 예에서는을 생성 하는 스크립트 파일 형식을 사용 하는 방법을 보여 줍니다 `Export-Alias` .

첫 번째 명령은 세션의 별칭을 Alias.ps1 파일로 내보냅니다.
스크립트 값을 사용 하 여 **As** 매개 변수를 사용 하 여 각 별칭에 대해 Set-Alias 명령을 포함 하는 파일을 생성 합니다.

두 번째 명령은 Alias.ps1 파일의 별칭을 CurrentUser-CurrentHost 프로필에 추가합니다.
프로필에 대 한 경로는 변수에 저장 됩니다 `$Profile` .
이 명령은 cmdlet을 사용 하 여 `Get-Content` Alias.ps1 파일에서 별칭을 가져오고 cmdlet을 사용 하 여 `Add-Content` 프로필에 추가 합니다.
자세한 내용은 about_Profiles를 참조하세요.

세 번째 및 네 번째 명령은 Alias.ps1 파일의 별칭을 Server01 컴퓨터의 원격 세션에 추가 합니다.
세 번째 명령은 cmdlet을 사용 하 여 `New-PSSession` 세션을 만듭니다.
네 번째 명령은 cmdlet의 **FilePath** 매개 변수를 사용 하 여 `Invoke-Command` 새 세션에서 Alias.ps1 파일을 실행 합니다.

## PARAMETERS

### -추가

이 cmdlet이 해당 파일의 기존 내용을 덮어쓰지 않고 지정 된 파일에 출력을 추가 함을 나타냅니다.

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

### -As

출력 형식을 지정합니다.
기본값은 CSV입니다.
이 매개 변수에 허용되는 값은 다음과 같습니다.

- CSV입니다.
CSV(쉼표로 구분된 값) 형식입니다.
- 스크립트.
`Set-Alias`내보낸 각 별칭에 대 한 명령을 만듭니다.
출력 파일 이름 확장명을 .ps1으로 지정하면 별칭을 세션에 추가하는 스크립트로 실행할 수 있습니다.

```yaml
Type: Microsoft.PowerShell.Commands.ExportAliasFormat
Parameter Sets: (All)
Aliases:
Accepted values: Csv, Script

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Description

내보낸 파일에 대 한 설명을 지정 합니다.
설명은 파일의 위쪽 머리글 정보 다음에 주석으로 나타납니다.

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

### -Force

사용자 확인을 요청하지 않고 명령을 강제 실행합니다.

파일에 읽기 전용 특성이 설정되어 있는 경우에도 출력 파일을 덮어씁니다.

기본적으로는 `Export-Alias` 읽기 전용 또는 숨김 특성이 설정 되어 있지 않거나 명령에 **NoClobber** 매개 변수가 사용 되는 경우를 제외 하 고는 경고 없이 파일을 덮어씁니다.
명령에 사용 되는 경우 **NoClobber** 매개 변수는 Force 매개 변수 보다 우선적으로 **적용** 됩니다.

**Force** 매개 변수는 `Export-Alias` hidden 특성을 가진 파일을 강제로 덮어쓸 수 없습니다.

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

출력 파일의 경로를 지정합니다.
**Path** 와 달리 **LiteralPath** 매개 변수 값은 입력한 대로 사용됩니다.
어떠한 문자도 와일드카드로 해석되지 않습니다.
이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요.
작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

이름을 내보낼 별칭의 배열로 지정 합니다.
와일드카드가 지원됩니다.

기본적으로는 `Export-Alias` 세션 또는 범위의 모든 별칭을 내보냅니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -NoClobber

`Export-Alias`명령에 **Force** 매개 변수가 사용 되는 경우에도이 cmdlet이 파일을 덮어쓰지 않도록 지정 합니다.

**NoClobber** 매개 변수를 생략 하면는 `Export-Alias` 파일에 읽기 전용 특성이 설정 되어 있지 않은 경우 경고 없이 기존 파일을 덮어씁니다.
*NoClobber* 은 읽기 전용 **Force** `Export-Alias` 특성으로 파일을 덮어쓸 수 있도록 하는 Force 매개 변수 보다 우선적으로 적용 됩니다.

*NoClobber* 를 설정 해도 **Append** 매개 변수는 기존 파일에 내용을 추가할 수 있습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NoOverwrite

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PassThru

작업 중인 항목을 나타내는 개체를 반환합니다.
기본적으로 이 cmdlet은 출력을 생성하지 않습니다.

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

출력 파일의 경로를 지정합니다.
와일드카드를 사용할 수는 있지만 결과 경로 값은 하나의 파일 이름을 도출해야 합니다.

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -범위

별칭을 내보낼 범위를 지정합니다.
이 매개 변수에 허용되는 값은 다음과 같습니다.

- 전역
- 로컬
- 스크립트
- 현재 범위를 기준으로 하는 숫자 (0부터 범위 수까지, 여기서 0은 현재 범위이 고 1은 부모)입니다.

기본값은 Local입니다.
자세한 내용은 about_Scopes를 참조하세요.

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

### 없음

이 cmdlet에 개체를 파이프할 수 없습니다.

## 출력

### 없음 또는 System.management.automation.aliasinfo

**Passthru** 매개 변수를 사용 하는 경우는 `Export-Alias` 별칭을 나타내는 **system.management.automation.aliasinfo** 개체를 반환 합니다.
그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.

## 참고

* 파일로만 Export-Alias를 수행할 수 있습니다.

## 관련 링크

[Get-Alias](Get-Alias.md)

[Import-Alias](Import-Alias.md)

[New-Alias](New-Alias.md)

[Set-Alias](Set-Alias.md)
