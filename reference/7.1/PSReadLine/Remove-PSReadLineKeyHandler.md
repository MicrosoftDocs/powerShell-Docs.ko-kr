---
external help file: Microsoft.PowerShell.PSReadLine2.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSReadLine
ms.date: 12/07/2018
online version: https://docs.microsoft.com/powershell/module/psreadline/remove-psreadlinekeyhandler?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-PSReadLineKeyHandler
ms.openlocfilehash: a13677035581a081df51917bc6b82efec0ff2156
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/21/2020
ms.locfileid: "93225025"
---
# Remove-PSReadLineKeyHandler

## 개요
키 바인딩을 제거 합니다.

## SYNTAX

```
Remove-PSReadLineKeyHandler [-Chord] <String[]> [-ViMode <ViMode>] [<CommonParameters>]
```

## 설명

`Remove-PSReadLineKeyHandler`Cmdlet은 지정 된 키 바인딩을 제거 합니다.

## 예제

### 예제 1: 바인딩 제거

```powershell
Remove-PSReadLineKeyHandler -Chord Ctrl+B
```

이 명령은 키 조합 또는 동시에서 바인딩을 제거 합니다 `Ctrl+B` . `Ctrl+B`이 문서에는 현가 만들어집니다 `Set-PSReadLineKeyHandler` .

## PARAMETERS

### -현

제거할 키의 배열이 나 시퀀스를 지정 합니다. 단일 바인딩은 단일 문자열을 사용 하 여 지정 됩니다. 바인딩이 키 시퀀스 인 경우 다음 예제와 같이 키를 쉼표로 구분 합니다.

`Ctrl+x,Ctrl+l`

이 매개 변수는 문자열 배열을 허용 합니다. 각 문자열은 단일 바인딩의 키 시퀀스가 아닌 별도의 바인딩입니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Key

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ViMode

바인딩이 적용 되는 vi 모드를 지정 합니다. 가능한 값은 Insert, Command입니다.

```yaml
Type: Microsoft.PowerShell.ViMode
Parameter Sets: (All)
Aliases:
Accepted values: Insert, Command

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### 없음

이 cmdlet에 개체를 파이프할 수 없습니다.

## 출력

### 없음

## 참고

## 관련 링크

[Get-PSReadLineKeyHandler](Get-PSReadLineKeyHandler.md)

[Get-PSReadLineOption](Get-PSReadLineOption.md)

[Set-PSReadLineOption](Set-PSReadLineOption.md)

[Set-PSReadLineKeyHandler](Set-PSReadLineKeyHandler.md)

