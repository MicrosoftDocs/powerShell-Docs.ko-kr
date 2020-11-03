---
external help file: Microsoft.PowerShell.ConsoleHost.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Host
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.host/stop-transcript?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Transcript
ms.openlocfilehash: 86903ca648ff3ee58ec939143b7881741827f453
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/02/2020
ms.locfileid: "93209343"
---
# Stop-Transcript

## 개요
기록을 중지합니다.

## SYNTAX

```
Stop-Transcript [<CommonParameters>]
```

## 설명

Cmdlet은 `Stop-Transcript` cmdlet에 의해 시작 된 기록을 중지 합니다 `Start-Transcript` .
또는 세션을 종료 하 여 기록을 중지할 수 있습니다.

## 예제

### 예제 1: 모든 기록을 중지 합니다.

```powershell
Stop-Transcript
```

이 명령은 모든 기록을 중지 합니다.

## PARAMETERS

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### 없음

이 cmdlet에 입력을 파이프할 수 없습니다.

## 출력

### System.String

이 cmdlet은 상태 메시지와 출력 파일의 경로를 포함 하는 문자열을 반환 합니다.

## 참고

* 기록이 시작되지 않은 경우에는 명령이 실행되지 않습니다.

*

## 관련 링크

[Start-Transcript](Start-Transcript.md)

