---
external help file: PSDiagnostics-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/29/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/disable-pswsmancombinedtrace?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSWSManCombinedTrace
ms.openlocfilehash: 4a00b843e5e4ec73cf98f4c924ca24a3e1ee0700
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/02/2020
ms.locfileid: "93209366"
---
# Disable-PSWSManCombinedTrace

## 개요
PSWSManCombinedTrace를 사용 하 여 시작 된 로깅 세션을 중지 합니다.

## SYNTAX

```
Disable-PSWSManCombinedTrace [<CommonParameters>]
```

## 설명

이 cmdlet은에 의해 시작 된 로깅 세션을 중지 `Enable-PSWSManCombinedTrace` 합니다.

이 cmdlet은 cmdlet을 사용 합니다 `Stop-Trace` .

관리자 권한 PowerShell 세션에서이 cmdlet을 실행 해야 합니다.

## 예제

### 예제 1: 결합 된 로깅 세션 사용 안 함

```powershell
Disable-PSWSManCombinedTrace
```

## PARAMETERS

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### 없음

## 출력

### 없음

## 참고

## 관련 링크

[이벤트 추적](/windows/desktop/ETW/event-tracing-portal)

[Stop-Trace](stop-trace.md)

[Enable-PSWSManCombinedTrace](Enable-PSWSManCombinedTrace.md)
