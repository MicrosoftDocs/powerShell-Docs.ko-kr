---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-pscallstack?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSCallStack
ms.openlocfilehash: 45c2ea5bc166e2d21153ae8b19c1c0afe4ca0640
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/02/2020
ms.locfileid: "93209016"
---
# Get-PSCallStack

## 개요
현재 호출 스택을 표시합니다.

## SYNTAX

```
Get-PSCallStack [<CommonParameters>]
```

## 설명
**Get PSCallStack** cmdlet은 현재 호출 스택을 표시 합니다.

이 cmdlet은 Windows PowerShell 디버거와 함께 사용하기 위한 것이지만, 디버거 외부의 스크립트 또는 함수에 호출 스택을 표시하는 데 사용할 수도 있습니다.

디버거에서 **Get PSCallStack** 명령을 실행 하려면 또는를 입력 `k` `Get-PSCallStack` 합니다.

## 예제

### 예제 1: 함수에 대 한 호출 스택 가져오기

```
PS C:\> function my-alias {
$p = $args[0]
Get-Alias | where {$_.definition -like "*$p"} | format-table definition, name -auto
}
PS C:\ps-test> Set-PSBreakpoint -Command my-alias
Command    : my-alias
Action     :
Enabled    : True
HitCount   : 0
Id         : 0
Script     : prompt PS C:\> my-alias Get-Content

Entering debug mode. Use h or ? for help.
Hit Command breakpoint on 'prompt:my-alias'
my-alias get-content
[DBG]: PS C:\ps-test> s
$p = $args[0]
DEBUG: Stepped to ':    $p = $args[0]    '
[DBG]: PS C:\ps-test> s
get-alias | Where {$_.Definition -like "*$p*"} | format-table Definition,
[DBG]: PS C:\ps-test>get-pscallstack

Name        CommandLineParameters         UnboundArguments              Location
----        ---------------------         ----------------              --------
prompt      {}                            {}                            prompt
my-alias    {}                            {get-content}                 prompt
prompt      {}                            {}                            prompt PS C:\> [DBG]: PS C:\ps-test> o
Definition  Name
----------  ----
Get-Content gc
Get-Content cat
Get-Content type
```

이 명령은 **Get PSCallStack** cmdlet을 사용 하 여 cmdlet 이름의 별칭을 가져오는 간단한 함수인 내 별칭에 대 한 호출 스택을 표시 합니다.

첫 번째 명령은 Windows PowerShell 프롬프트에 함수를 입력합니다.
두 번째 명령은 Set-PSBreakpoint cmdlet을 사용하여 My-Alias 함수에 중단점을 설정합니다.
세 번째 명령은 My-Alias 함수를 사용하여 Get-Content cmdlet에 대해 현재 세션의 모든 별칭을 가져옵니다.

디버거는 함수 호출 시 중단됩니다.
연속하는 두 step-into 명령이 함수를 한 줄씩 실행하기 시작합니다.
그런 다음 **Get PSCallStack** 명령이 호출 스택을 검색 하는 데 사용 됩니다.

최종 명령은 디버거를 종료하고 스크립트를 완료될 때까지 계속 실행하는 Step-Out 명령(o)입니다.

## PARAMETERS

### CommonParameters
이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### 없음
이 cmdlet에 개체를 파이프할 수 없습니다.

## 출력

### System.web. CallStackFrame
**Get PSCallStack** 은 호출 스택의 항목을 나타내는 개체를 반환 합니다.

## 참고

## 관련 링크

[Disable-PSBreakpoint](Disable-PSBreakpoint.md)

[Enable-PSBreakpoint](Enable-PSBreakpoint.md)

[Format-Table](Format-Table.md)

[Get-PSBreakpoint](Get-PSBreakpoint.md)

[Remove-PSBreakpoint](Remove-PSBreakpoint.md)

[Set-PSBreakpoint](Set-PSBreakpoint.md)
