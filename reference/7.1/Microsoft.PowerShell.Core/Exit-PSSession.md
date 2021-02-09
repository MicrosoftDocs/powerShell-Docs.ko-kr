---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 02/08/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/exit-pssession?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Exit-PSSession
ms.openlocfilehash: b764aadc28d175f08fdcbaf56e904ff9310eb35b
ms.sourcegitcommit: 3a1d80e27438976101f216b8c3d623c61b868db8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/09/2021
ms.locfileid: "99975076"
---
# Exit-PSSession

## 개요
원격 컴퓨터와의 대화형 세션을 종료합니다.

## SYNTAX

```
Exit-PSSession [<CommonParameters>]
```

## Description

`Exit-PSSession`Cmdlet은 cmdlet을 사용 하 여 시작한 대화형 세션을 종료 합니다 `Enter-PSSession` .

키워드를 사용 하 여 `exit` 대화형 세션을 종료할 수도 있습니다. 효과는를 사용 하는 것과 같습니다 `Exit-PSSession` .

## 예

### 예제 1: 대화형 세션 시작 및 중지

```powershell
PS> Enter-PSSession -ComputerName Server01
Server01\PS> Exit-PSSession
PS>
```

이 명령은 Server01 원격 컴퓨터와 대화형 세션을 시작한 다음 중지합니다.

### 예제 2: PSSession 개체를 사용 하 여 대화형 세션 시작 및 중지

```powershell
PS> $s = New-PSSession -ComputerName Server01
PS> Enter-PSSession -Session $s
Server01\PS> Exit-PSSession
PS> $s
Id Name            ComputerName    State    ConfigurationName
-- ----            ------------    -----    -----------------
1  Session1        Server01        Opened   Microsoft.PowerShell
```

이러한 명령은 PowerShell 세션 (**PSSession**)을 사용 하는 Server01 컴퓨터와 대화형 세션을 시작 하 고 중지 합니다.

대화형 세션은 PowerShell 세션을 사용 하 여 시작 되었기 때문에 대화형 세션이 종료 되어도 **PSSession** 을 계속 사용할 수 있습니다. _ComputerName_ 매개 변수를 사용 하는 경우는 `Enter-PSSession` 대화형 세션이 종료 될 때 종료 되는 임시 세션을 만듭니다.

첫 번째 명령은 cmdlet을 사용 하 여 `New-PSSession` Server01 컴퓨터에 **PSSession** 을 만듭니다. 이 명령은 **PSSession** 을 변수에 저장 합니다 `$s` .

두 번째 명령은를 사용 하 여 `Enter-PSSession` 의 **PSSession** 을 사용 하 여 대화형 세션을 시작 `$s` 합니다.

세 번째 명령은 `Exit-PSSession` 를 사용 하 여 대화형 세션을 중지 합니다.

마지막 명령은 변수에 **PSSession** 을 표시 합니다 `$s` . **상태** 속성은 **PSSession** 이 여전히 열려 있고 사용할 수 있는 것을 보여 줍니다.

### 예 3: Exit 키워드를 사용 하 여 세션 중지

```powershell
PS> Enter-PSSession -ComputerName Server01
Server01\PS> exit
PS>
```

이 예제에서는 키워드를 사용 하 여 `exit` 를 사용 하 여 시작 된 대화형 세션을 중지 `Enter-PSSession` 합니다. 키워드는를 `exit` 사용 하는 것과 동일한 효과를 가집니다 `Exit-PSSession` .

## 매개 변수

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### None

이 cmdlet에 개체를 파이프할 수 없습니다.

## 출력

### None

이 cmdlet은 어떠한 출력도 반환되지 않습니다.

## 참고

이 cmdlet은 일반 매개 변수만 사용합니다.

## 관련 링크

[Connect-PSSession](Connect-PSSession.md)

[Disconnect-PSSession](Disconnect-PSSession.md)

[Enter-PSSession](Enter-PSSession.md)

[Get-PSSession](Get-PSSession.md)

[Invoke-Command](Invoke-Command.md)

[New-PSSession](New-PSSession.md)

[Receive-PSSession](Receive-PSSession.md)

[Remove-PSSession](Remove-PSSession.md)
