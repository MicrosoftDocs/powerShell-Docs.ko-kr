---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/10/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/start-sleep?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Sleep
ms.openlocfilehash: 1a107b2e4c7414250154d576d6dc9554cb9d800b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93216217"
---
# Start-Sleep

## 개요
지정한 기간 동안 스크립트 또는 세션의 활동을 일시 중단합니다.

## SYNTAX

### 초 (기본값)

```
Start-Sleep [-Seconds] <Double> [<CommonParameters>]
```

### 밀리초

```
Start-Sleep -Milliseconds <Int32> [<CommonParameters>]
```

## 설명

`Start-Sleep`Cmdlet은 지정 된 기간 동안 스크립트나 세션의 작업을 일시 중단 합니다. 작업이 완료될 때까지 대기, 작업을 반복하기 전에 일시 중지 등의 많은 작업에 이 cmdlet을 사용할 수 있습니다.

## 예제

### 예제 1:15 초 동안 모든 명령 중지

```powershell
Start-Sleep -s 15
```

### 예제 2:1.5 초 동안 모든 명령 중지

이 예제에서는 세션의 모든 명령을 1 초 동안 절전 모드로 설정 합니다.

```powershell
Start-Sleep -Seconds 1.5
```

## PARAMETERS

### -밀리초

리소스가 일시 중단되는 기간(밀리초)을 지정합니다. 매개 변수는 **m** 으로 축약 될 수 있습니다.

```yaml
Type: System.Int32
Parameter Sets: Milliseconds
Aliases: ms

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -초

리소스가 일시 중단되는 기간(초)을 지정합니다. 매개 변수 이름을 생략 **하거나로 약어를 지정할** 수 있습니다. PowerShell 6.2.0부터이 매개 변수는 이제 소수 자릿수 값을 허용 합니다.

```yaml
Type: System.Double
Parameter Sets: Seconds
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.

## 입력

### System.Int32

초 수를로 파이프 할 수 있습니다 `Start-Sleep` .

## 출력

### 없음

이 cmdlet은 어떠한 출력도 반환되지 않습니다.

## 참고

- 의 기본 제공 별칭인를 참조할 수도 있습니다 `Start-Sleep` `sleep` . 자세한 내용은 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)를 참조 하세요.
- `Ctrl+C` 에서 중단 `Start-Sleep` 됩니다.
  - `Ctrl+C` 는 중단 되지 않습니다 `[Threading.Thread]::Sleep` . 자세한 내용은 [Sleep 메서드](/dotnet/api/system.threading.thread.sleep)를 참조 하세요.

## 관련 링크
