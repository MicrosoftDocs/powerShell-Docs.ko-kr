---
external help file: Microsoft.PowerShell.ConsoleHost.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Host
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.host/stop-transcript?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Transcript
ms.openlocfilehash: 16b41711e98276fee37d56f77f57e7372daa4cf3
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99605494"
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

