---
external help file: PSDiagnostics-help.xml
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/enable-pstrace?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSTrace
ms.openlocfilehash: 231c2e3d2e28463be35ff1c9d5dab5a5d958f430
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99602056"
---
# Enable-PSTrace

## 개요
Microsoft-Windows PowerShell 이벤트 공급자 로그를 사용 하도록 설정 합니다.

## SYNTAX

```
Enable-PSTrace [-Force] [-AnalyticOnly] [<CommonParameters>]
```

## 설명

이 cmdlet은 Microsoft-Windows PowerShell 이벤트 공급자의 운영 및 분석 이벤트 로그를 사용 하도록 설정 합니다.

관리자 권한 PowerShell 세션에서이 cmdlet을 실행 해야 합니다.

## 예제

### 예제 1: PowerShell에 대 한 분석 이벤트 로그 사용

다음 예에서는 Microsoft-Windows PowerShell 공급자의 분석 이벤트 로그만 사용 하도록 설정 합니다.

```powershell
Enable-PSTrace -AnalyticOnly
```

## PARAMETERS

### -AnalyticOnly

이 매개 변수를 사용 하는 경우 cmdlet은 Microsoft-Windows PowerShell 공급자의 분석 이벤트 로그를 사용 하도록 설정 합니다. 운영 이벤트 로그는 변경 되지 않습니다.

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

### -Force

메시지를 표시 하지 않고 강제로 변경 하는 데 사용 됩니다.

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

이 cmdlet은 `Get-LogProperties` 및 cmdlet을 사용 `Set-LogProperties` 합니다.

관리자 권한 PowerShell 세션에서이 cmdlet을 실행 해야 합니다.

## 관련 링크

[Get-LogProperties](Get-LogProperties.md)

[Set-LogProperties](Set-LogProperties.md)

[Disable-PSTrace](Disable-PSTrace.md)

