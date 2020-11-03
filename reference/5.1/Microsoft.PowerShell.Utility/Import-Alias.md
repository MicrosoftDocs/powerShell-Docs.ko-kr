---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-alias?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-Alias
ms.openlocfilehash: f501768990c4381841fbf1402dab6cf633e7ea40
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93213898"
---
# Import-Alias

## 개요
파일에서 별칭 목록을 가져옵니다.

## SYNTAX

### ByPath (기본값)

```
Import-Alias [-Path] <String> [-Scope <String>] [-PassThru] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByLiteralPath

```
Import-Alias -LiteralPath <String> [-Scope <String>] [-PassThru] [-Force] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## 설명

`Import-Alias`Cmdlet은 파일에서 별칭 목록을 가져옵니다.

Windows PowerShell 3.0부터 보안 기능부터 `Import-Alias` 은 기본적으로 기존 별칭을 덮어쓰지 않습니다.
기존 별칭을 덮어쓰려면 별칭 파일의 내용이 안전한지 확인한 후 **Force** 매개 변수를 사용합니다.

## 예제

### 예제 1: 파일에서 별칭 가져오기

```powershell
Import-Alias test.txt
```

이 명령은 test.txt라는 파일에서 별칭 정보를 가져옵니다.

## PARAMETERS

### -Force

cmdlet이 이미 정의되어 있거나 읽기 전용인 별칭을 가져올 수 있게 합니다.
다음 명령을 사용하여 현재 정의된 별칭에 대한 정보를 표시할 수 있습니다.

`Get-Alias | Select-Object Name, Options`

해당 별칭이 읽기 전용인 경우 **Options** 속성 값에 표시됩니다.

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

내보낸 별칭 정보가 포함된 파일의 경로를 지정합니다.
**Path** 매개 변수와 달리 **LiteralPath** 매개 변수 값은 입력한 대로 사용됩니다.
어떠한 문자도 와일드카드로 해석되지 않습니다.
이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요.
작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
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

내보낸 별칭 정보가 포함된 파일의 경로를 지정합니다.
와일드카드를 사용할 수 있지만 하나의 이름으로 확인되어야 합니다.

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -범위

별칭을 가져올 범위를 지정합니다.
이 매개 변수에 허용되는 값은 다음과 같습니다.

- 전역
- 로컬
- 스크립트
- 현재 범위를 기준으로 하는 숫자 (0부터 범위 수까지, 여기서 0은 현재 범위이 고 1은 부모)

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

### System.String

경로를 포함 하는 문자열을로 파이프 할 수 있습니다 `Import-Alias` .

## 출력

### 없음 또는 System.management.automation.aliasinfo

**Passthru** 매개 변수를 사용 하는 경우는 `Import-Alias` 별칭을 나타내는 **system.management.automation.aliasinfo** 개체를 반환 합니다.
그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.

## 참고

## 관련 링크

[Export-Alias](Export-Alias.md)

[Get-Alias](Get-Alias.md)

[New-Alias](New-Alias.md)

[Set-Alias](Set-Alias.md)
