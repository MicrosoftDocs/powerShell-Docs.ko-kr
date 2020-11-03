---
external help file: PSDiagnostics-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/29/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/enable-pswsmancombinedtrace?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSWSManCombinedTrace
ms.openlocfilehash: cfe73dea98cdf858f1364e1daf434334b57a62cd
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93217082"
---
# Enable-PSWSManCombinedTrace

## 개요
WSMan 및 PowerShell 공급자를 사용 하 여 로깅 세션을 시작 합니다.

## SYNTAX

```
Enable-PSWSManCombinedTrace [-DoNotOverwriteExistingTrace] [<CommonParameters>]
```

## 설명

이 cmdlet은 다음 PowerShell 공급자를 사용 하 여 로깅 세션을 시작 합니다.

- Microsoft-Windows-PowerShell
- Microsoft-Windows-WinRM

세션의 이름은 ' PSTrace '입니다.

이 cmdlet은 cmdlet을 사용 합니다 `Start-Trace` .

관리자 권한 PowerShell 세션에서이 cmdlet을 실행 해야 합니다.

## 예제

### 예제 1: 결합 된 로깅 세션 시작

```powershell
Enable-PSWSManCombinedTrace
```

## PARAMETERS

### -DoNotOverwriteExistingTrace

기본적으로 이벤트는 "$pshome \Traces\PSTrace.etl"에 기록 됩니다. 이 매개 변수를 사용 하는 경우 cmdlet은 "$pshome \Traces\ PSTrace_ {guid} .etl"의 고유한 파일 이름을 만듭니다.

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

### 없음

## 출력

### 없음

## 참고

## 관련 링크

[이벤트 추적](/windows/desktop/ETW/event-tracing-portal)

[Start-Trace](start-trace.md)

[Disable-PSWSManCombinedTrace](Disable-PSWSManCombinedTrace.md)
