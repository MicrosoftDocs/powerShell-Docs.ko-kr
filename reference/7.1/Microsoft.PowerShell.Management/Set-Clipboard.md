---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-clipboard?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Clipboard
ms.openlocfilehash: 1ee55dfaf4ecd3e46bedd8f356b1f677180c9c62
ms.sourcegitcommit: 7b376314e7640c39a53aac9f0db8bb935514a960
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2020
ms.locfileid: "96564557"
---
# Set-Clipboard

## 개요
클립보드의 내용을 설정 합니다.

## SYNTAX

```
Set-Clipboard -Value <String[]> [-Append] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명

`Set-Clipboard`Cmdlet은 클립보드의 내용을 설정 합니다.

> [!NOTE]
> Linux에서이 cmdlet을 사용 `xclip` 하려면 유틸리티가 경로에 있어야 합니다.

## 예제

### 예제 1: 텍스트를 클립보드로 복사

```powershell
Set-Clipboard -Value "This is a test string"
```

### 예제 2: 파일 내용을 클립보드에 복사

이 예제에서는 파일 내용을 클립보드로 파이프 합니다. 이 예제에서는 GitHub와 같은 다른 응용 프로그램에 붙여 넣을 수 있도록 공용 ssh 키를 가져옵니다.

```powershell
Get-Content C:\Users\user1\.ssh\id_ed25519.pub | Set-Clipboard
```

## PARAMETERS

### -추가

Cmdlet에서 클립보드를 지우지 않고 내용을 추가 함을 나타냅니다.

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

### -Value

클립보드에 추가할 문자열 값입니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.String[]

## 출력

## 참고

드문 경우 지만 루프와 같이 신속 하 게 많은 값을 사용 하 여를 사용 하는 경우 `Set-Clipboard` 클립보드에서 빈 값을 얻을 수 있습니다. 루프에서를 사용 하 여이 문제를 해결할 수 있습니다 `Start-Sleep -Milliseconds 1` .

## 관련 링크

[Get-Clipboard](Get-Clipboard.md)
