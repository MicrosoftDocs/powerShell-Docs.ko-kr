---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 09/21/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-clipboard?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Clipboard
ms.openlocfilehash: ed56dc5655f640dae1d80c66850581ff12dbb7ee
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94347604"
---
# Get-Clipboard

## 개요
클립보드의 내용을 가져옵니다.

## SYNTAX

```
Get-Clipboard [-Raw] [<CommonParameters>]
```

## 설명

`Get-Clipboard`Cmdlet은 클립보드의 내용을 텍스트로 가져옵니다. 텍스트의 여러 줄은와 유사한 문자열 배열로 반환 됩니다 `Get-Content` .

> [!NOTE]
> Linux에서이 cmdlet을 사용 `xclip` 하려면 유틸리티가 경로에 있어야 합니다. 이 cmdlet은 macOS에서 지원 되지 않습니다.

## 예제

### 예제 1: 클립보드의 내용 가져오기 및 명령줄에 표시

이 예제에서는 "hello" 텍스트를 클립보드에 복사 했습니다.

```powershell
Get-Clipboard
```

```Output
hello
```

## PARAMETERS

### -Raw

클립보드의 전체 내용을 가져옵니다. 여러 줄 텍스트는 문자열 배열이 아니라 단일 여러 줄 문자열로 반환 됩니다.

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

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

## 출력

### System.String

## 참고

## 관련 링크

[Set-Clipboard](Set-Clipboard.md)
