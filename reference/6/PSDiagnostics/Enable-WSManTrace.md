---
external help file: PSDiagnostics-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/29/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/enable-wsmantrace?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-WSManTrace
ms.openlocfilehash: 70ce4849e78262fc3553502d307e1df4e9ecfcf3
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/02/2020
ms.locfileid: "93209075"
---
# Enable-WSManTrace

## 개요
WSMan 공급자가 사용 하도록 설정 된 로깅 세션을 시작 합니다.

## SYNTAX

```
Enable-WSManTrace [<CommonParameters>]
```

## 설명
이 cmdlet은 WSMan 공급자가 사용 하도록 설정 된 로깅 세션을 시작 합니다. 다음 이벤트 공급자를 사용할 수 있습니다.

- 이벤트 전달
- IpmiDrv
- IPMIPrv
- WinRM
- WinrsCmd
- WinrsExe
- WinrsMgr
- WSManProvHost

세션의 이름은 ' wsmlog '입니다.

이 cmdlet은 cmdlet을 사용 합니다 `Start-Trace` .

관리자 권한 PowerShell 세션에서이 cmdlet을 실행 해야 합니다.

## 예제

### 예 1: WSMan 로깅 세션을 시작 합니다.

```powershell
Enable-WSManTrace
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

[Start-Trace](start-trace.md)

[Disable-WSManTrace](Disable-WSManTrace.md)
