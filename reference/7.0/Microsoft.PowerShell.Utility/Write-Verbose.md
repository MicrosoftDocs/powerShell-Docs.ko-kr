---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-verbose?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Verbose
ms.openlocfilehash: 34e8d6edd7199921254a3835a9f13b6331c2d26e
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2020
ms.locfileid: "93224385"
---
# Write-Verbose

## 개요
자세한 정보 메시지 스트림에 텍스트를 씁니다.

## SYNTAX

```
Write-Verbose [-Message] <String> [<CommonParameters>]
```

## 설명

`Write-Verbose`Cmdlet은 PowerShell의 자세한 정보 메시지 스트림에 텍스트를 씁니다. 일반적으로 자세한 정보 메시지 스트림은 명령 처리에 대 한 자세한 정보를 제공 하는 데 사용 됩니다.

기본적으로 자세한 정보 메시지 스트림은 표시 되지 않지만, 변수 값을 변경 `$VerbosePreference` 하거나 임의의 명령에서 **verbose** 일반 매개 변수를 사용 하 여 표시할 수 있습니다.

## 예제

### 예제 1: 상태 메시지 작성

```powershell
Write-Verbose -Message "Searching the Application Event Log."
Write-Verbose -Message "Searching the Application Event Log." -Verbose
```

이러한 명령은 cmdlet을 사용 `Write-Verbose` 하 여 상태 메시지를 표시 합니다. 이 메시지는 기본적으로 표시되지 않습니다.

두 번째 명령은 **verbose** 일반 매개 변수를 사용 합니다 .이 매개 변수는 변수의 값에 관계 없이 자세한 정보 메시지를 표시 합니다 `$VerbosePreference` .

### 예제 2: $VerbosePreference 설정 및 상태 메시지 작성

```powershell
$VerbosePreference = "Continue"
Write-Verbose "Copying file $filename"
```

이러한 명령은 cmdlet을 사용 `Write-Verbose` 하 여 상태 메시지를 표시 합니다. 이 메시지는 기본적으로 표시되지 않습니다.

첫 번째 명령은 기본 설정 변수에 Continue 값을 할당 합니다 `$VerbosePreference` . 기본값인는 `SilentlyContinue` 자세한 정보 표시 메시지를 표시 하지 않습니다. 두 번째 명령은 자세한 정보 메시지를 씁니다.

## PARAMETERS

### -메시지

표시할 메시지를 지정합니다. 이 매개 변수는 필수적 요소입니다. 메시지 문자열을로 파이프 할 수도 있습니다 `Write-Verbose` .

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Msg

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.

## 입력

### System.String

메시지를 포함 하는 문자열을로 파이프 할 수 있습니다 `Write-Verbose` .

## 출력

### None

`Write-Verbose` 자세한 정보 메시지 스트림에만 씁니다.

## 참고

- 자세한 정보 메시지는 명령에서 **Verbose** 일반 매개 변수를 사용하는 경우에만 반환됩니다. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.
- Windows PowerShell 백그라운드 작업 및 원격 명령에서 `$VerbosePreference` 작업 세션 및 원격 세션의 변수는 자세한 정보 표시 메시지를 기본적으로 표시할지 여부를 결정 합니다.
  변수에 대 한 자세한 내용은 `$VerbosePreference` [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)를 참조 하세요.

## 관련 링크

[about_Output_Streams](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[about_Redirection](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[Write-Debug](Write-Debug.md)

[쓰기 오류](Write-Error.md)

[Write-Host](Write-Host.md)

[Write-Information](Write-Information.md)

[Write-Output](Write-Output.md)

[Write-Progress](Write-Progress.md)

[Write-Warning](Write-Warning.md)
