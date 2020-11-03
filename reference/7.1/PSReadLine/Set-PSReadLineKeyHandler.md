---
external help file: Microsoft.PowerShell.PSReadLine2.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSReadLine
ms.date: 12/07/2018
online version: https://docs.microsoft.com/powershell/module/psreadline/set-psreadlinekeyhandler?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSReadLineKeyHandler
ms.openlocfilehash: 97d342d9f5d7227fb831794055c2cfa75b8cf765
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/21/2020
ms.locfileid: "93225002"
---
# Set-PSReadLineKeyHandler

## 개요
키를 사용자 정의 또는 PSReadLine 키 처리기 함수에 바인딩합니다.

## SYNTAX

### ScriptBlock

```
Set-PSReadLineKeyHandler [-ScriptBlock] <ScriptBlock> [-BriefDescription <String>]
 [-Description <String>] [-Chord] <String[]> [-ViMode <ViMode>] [<CommonParameters>]
```

### 함수

```
Set-PSReadLineKeyHandler [-Chord] <String[]> [-ViMode <ViMode>] [-Function] <String>
 [<CommonParameters>]
```

## 설명

`Set-PSReadLineKeyHandler`Cmdlet은 키 또는 키 시퀀스를 누를 때 결과를 사용자 지정 합니다. 사용자 정의 키 바인딩을 사용 하면 PowerShell 스크립트 내에서 가능한 거의 모든 작업을 수행할 수 있습니다.

## 예제

### 예제 1: 화살표 키를 함수에 바인딩

이 명령은 위쪽 화살표 키를 **HistorySearchBackward** 함수에 바인딩합니다. 이 함수는 명령줄의 현재 내용으로 시작 하는 명령줄에 대 한 명령 기록을 검색 합니다.

```powershell
Set-PSReadLineKeyHandler -Chord UpArrow -Function HistorySearchBackward
```

### 예제 2: 스크립트 블록에 키 바인딩

이 예제에서는 단일 키를 사용 하 여 명령을 실행 하는 방법을 보여 줍니다. 명령은 `Ctrl+B` 줄을 지우고 "build" 라는 단어를 삽입 한 다음 줄을 허용 하는 스크립트 블록에 키를 바인딩합니다.

```powershell
Set-PSReadLineKeyHandler -Chord Ctrl+B -ScriptBlock {
    [Microsoft.PowerShell.PSConsoleReadLine]::RevertLine()
    [Microsoft.PowerShell.PSConsoleReadLine]::Insert('build')
    [Microsoft.PowerShell.PSConsoleReadLine]::AcceptLine()
}
```

## PARAMETERS

### -BriefDescription

키 바인딩에 대 한 간단한 설명입니다. 이 설명은 cmdlet에 의해 표시 됩니다 `Get-PSReadLineKeyHandler` .

```yaml
Type: System.String
Parameter Sets: ScriptBlock
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -현

함수 또는 스크립트 블록에 바인딩할 키 또는 키 시퀀스입니다. 단일 바인딩을 지정 하려면 단일 문자열을 사용 합니다. 바인딩이 키 시퀀스 인 경우 다음 예제와 같이 키를 쉼표로 구분 합니다.

`Ctrl+X,Ctrl+L`

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

### -Description

Cmdlet의 출력에 표시 되는 키 바인딩에 대 한 자세한 설명을 지정 합니다 `Get-PSReadLineKeyHandler` .

```yaml
Type: System.String
Parameter Sets: ScriptBlock
Aliases: LongDescription

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -함수

PSReadLine에서 제공 하는 기존 키 처리기의 이름을 지정 합니다. 이 매개 변수를 사용 하면 기존 키 바인딩을 다시 바인딩하거나 현재 바인딩되지 않은 처리기를 바인딩할 수 있습니다.

```yaml
Type: System.String
Parameter Sets: Function
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ScriptBlock

동시에 입력 될 때 실행할 스크립트 블록 값을 지정 합니다. PSReadLine은이 스크립트 블록에 하나 또는 두 개의 매개 변수를 전달 합니다. 첫 번째 매개 변수는 누른 키를 나타내는 **ConsoleKeyInfo** 개체입니다. 두 번째 인수는 컨텍스트에 따라 모든 개체가 될 수 있습니다.

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlock
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ViMode

바인딩이 적용 되는 vi 모드를 지정 합니다.

유효한 값은 다음과 같습니다.

- 삽입
- 명령

```yaml
Type: Microsoft.PowerShell.ViMode
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

### 없음

이 cmdlet에 개체를 파이프할 수 없습니다.

## 출력

### 없음

이 cmdlet은 어떠한 출력도 생성하지 않습니다.

## 참고

## 관련 링크

[Get-PSReadLineKeyHandler](Get-PSReadLineKeyHandler.md)

[Remove-PSReadLineKeyHandler](Remove-PSReadLineKeyHandler.md)

[Get-PSReadLineOption](Get-PSReadLineOption.md)

[Set-PSReadLineOption](Set-PSReadLineOption.md)

