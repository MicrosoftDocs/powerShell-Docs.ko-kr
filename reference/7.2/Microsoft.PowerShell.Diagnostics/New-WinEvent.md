---
external help file: Microsoft.PowerShell.Commands.Diagnostics.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Diagnostics
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.diagnostics/new-winevent?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-WinEvent
ms.openlocfilehash: 5b4b150a1c02e5d0689b44db9b2a984e297db766
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99600165"
---
# New-WinEvent

## 개요
지정된 이벤트 공급자에 대한 Windows 이벤트 새로 만듭니다.

## SYNTAX

```
New-WinEvent [-ProviderName] <String> [-Id] <Int32> [-Version <Byte>] [[-Payload] <Object[]>]
 [<CommonParameters>]
```

## 설명

**New-WinEvent** cmdlet은 이벤트 공급자에 대해 ETW(Windows용 이벤트 추적) 이벤트를 만듭니다.
이 cmdlet을 사용 하 여 PowerShell에서 ETW 채널에 이벤트를 추가할 수 있습니다.

## 예제

### 예제 1

```powershell
PS C:\> New-WinEvent -ProviderName Microsoft-Windows-PowerShell -Id 45090 -Payload @("Workflow", "Running")
```

이 명령은 **New-WinEvent** cmdlet을 사용하여 Microsoft-Windows-PowerShell 공급자에 대해 이벤트 45090을 만듭니다.

## PARAMETERS

### -Id

계측 매니페스트를 통해 등록된 이벤트 ID를 지정합니다.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -페이로드

이벤트에 대한 메시지를 지정합니다. 이벤트 로그에 이벤트를 기록하면 페이로드가 이벤트 개체의 **Message** 속성에 저장됩니다.

지정 된 페이로드가 이벤트 정의의 페이로드와 일치 하지 않으면 PowerShell에서 경고를 생성 하지만 명령은 여전히 성공 합니다.

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProviderName

"Microsoft-Windows-PowerShell"과 같이 이벤트를 이벤트 로그에 기록하는 이벤트 공급자를 지정합니다. ETW 이벤트 공급자는 이벤트를 ETW 세션에 기록하는 논리적 엔터티입니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Version

이벤트의 버전 번호를 지정합니다. 이벤트 번호를 입력합니다. PowerShell은 숫자를 필요한 바이트 형식으로 변환 합니다.

이 매개 변수를 사용하면 동일한 이벤트의 다른 버전이 정의될 때 이벤트를 지정할 수 있습니다.

```yaml
Type: System.Byte
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

이 cmdlet은 파이프라인에서 입력을 가져오지 않습니다.

## 출력

### 없음

이 cmdlet은 아무 출력도 생성되지 않습니다.

## 참고

* 공급자가 이벤트 로그에도 기록 하면 Get-WinEvent cmdlet을 사용 하 여 이벤트 로그에서 이벤트를 가져올 수 있습니다.

## 관련 링크

[Get-WinEvent](Get-WinEvent.md)

