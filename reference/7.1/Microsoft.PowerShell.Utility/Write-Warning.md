---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-warning?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Warning
ms.openlocfilehash: 7e74e53bd056a452917d2f2380b817fc6925f0fe
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2020
ms.locfileid: "93224361"
---
# Write-Warning

## 개요
경고 메시지를 씁니다.

## SYNTAX

```
Write-Warning [-Message] <String> [<CommonParameters>]
```

## 설명

`Write-Warning`Cmdlet은 PowerShell 호스트에 경고 메시지를 기록 합니다. 경고에 대 한 응답은 사용자의 `$WarningPreference` 변수 값 및 **WarningAction** 일반 매개 변수 사용에 따라 달라 집니다.

## 예제

### 예제 1: 경고 메시지 작성

이 명령은 "경고: 테스트 경고만입니다." 라는 메시지를 표시 합니다.

```powershell
Write-Warning "This is only a test warning."
```

### 예제 2: Write-Warning에 문자열 전달

이 명령은 파이프라인 연산자 ()를 사용 하 여 `|` 에 문자열을 보낼 수 있음을 보여 줍니다 `Write-Warning` .
이 명령에 표시 된 대로 문자열을 변수에 저장 하거나로 직접 파이프 할 수 있습니다 `Write-Warning` .

```powershell
$w = "This is only a test warning."
$w | Write-Warning
```

### 예 3: $WarningPreference 변수를 설정 하 고 경고를 작성 합니다.

이 예에서는 명령에 대 한 변수 값의 영향을 보여 줍니다 `$WarningPreference` `Write-Warning` .

```powershell
PS> $WarningPreference
Continue
PS> Write-Warning "This is only a test warning."
This is only a test warning.
PS> $WarningPreference = "SilentlyContinue"
PS> Write-Warning "This is only a test warning."
PS> $WarningPreference = "Stop"
PS> Write-Warning "This is only a test warning."
WARNING: This is only a test message.
Write-Warning : Command execution stopped because the shell variable "WarningPreference" is set to Stop.
At line:1 char:14
     + Write-Warning <<<<  "This is only a test message."
```

첫 번째 명령은 변수의 기본값을 표시 합니다 `$WarningPreference` `Continue` . 따라서 경고를 작성할 때 경고 메시지가 표시되고 실행이 계속됩니다.

변수의 값을 변경 하면 `$WarningPreference` `Write-Warning` 명령의 영향이 다시 변경 됩니다. 값이 이면 `SilentlyContinue` 경고를 표시 하지 않습니다. 값은 `Stop` 경고를 표시 한 다음 명령 실행을 중지 합니다.

변수에 대 한 자세한 내용은 `$WarningPreference` [about_Preference_Variables](../Microsoft.Powershell.Core/About/about_Preference_Variables.md)를 참조 하세요.

### 예 4: WarningAction 매개 변수를 설정 하 고 경고를 작성 합니다.

이 예에서는 명령에 **WarningAction** common 매개 변수의 효과를 보여 줍니다 `Write-Warning` . **WarningAction** 일반 매개 변수를 cmdlet과 함께 사용 하 여 PowerShell이 해당 명령으로 인해 발생 하는 경고에 응답 하는 방법을 결정할 수 있습니다. **WarningAction** 일반 매개 변수는 `$WarningPreference` 특정 명령에 대해서만 값을 재정의 합니다.

```powershell
PS> Write-Warning "This is only a test warning." -WarningAction Inquire
WARNING: This is only a test warning.
Confirm
Continue with this operation?
 [Y] Yes  [A] Yes to All  [H] Halt Command  [S] Suspend  [?] Help (default is "Y"):
```

이 명령은 cmdlet을 사용 하 여 `Write-Warning` 경고를 표시 합니다. **WarningAction** 일반 매개 변수는 명령에 경고가 표시 될 때 시스템에서 사용자에 게 메시지를 표시 하도록 지시 합니다.

**WarningAction** 일반 매개 변수에 대 한 자세한 내용은 [about_CommonParameters](../Microsoft.Powershell.Core/About/about_CommonParameters.md)를 참조 하세요.

## PARAMETERS

### -메시지
경고 메시지를 지정합니다.

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

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.String

경고가 포함 된 문자열을로 파이프 할 수 있습니다 `Write-Warning` .

## 출력

### None

`Write-Warning` 경고 스트림에만 씁니다. 다른 출력은 생성하지 않습니다.

## 참고

변수의 기본값은 경고를 `$WarningPreference` 표시 하 `Continue` 고 명령을 계속 실행 하는입니다. 와 같은 기본 설정 변수에 대 한 유효한 값을 확인 하려면 `$WarningPreference` "abc"와 같은 임의의 문자 문자열로 설정 합니다. 결과 오류 메시지에는 유효한 값이 나열 됩니다.

## 관련 링크

[about_Output_Streams](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[about_Redirection](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[Write-Debug](Write-Debug.md)

[쓰기 오류](Write-Error.md)

[Write-Host](Write-Host.md)

[Write-Information](Write-Information.md)

[Write-Output](Write-Output.md)

[Write-Progress](Write-Progress.md)

[Write-Verbose](Write-Verbose.md)
