---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/exit-pshostprocess?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Exit-PSHostProcess
ms.openlocfilehash: 381d7d9cb32ed4682729ad304e82bb994a21190d
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/02/2020
ms.locfileid: "93209243"
---
# Exit-PSHostProcess

## 개요
로컬 프로세스를 사용 하 여 대화형 세션을 닫습니다.

## SYNTAX

```
Exit-PSHostProcess [<CommonParameters>]
```

## 설명

**PSHostProcess** cmdlet은 Enter-PSHostProcess cmdlet을 실행 하 여 연 로컬 프로세스와의 대화형 세션을 닫습니다. 프로세스 내에서 실행 중인 스크립트에 대 한 디버깅 또는 문제 해결이 완료 되 면 프로세스 내에서 **PSHostProcess** cmdlet을 실행 합니다.

## 예제

### 예제 1: 프로세스 종료

```
[Process:1520]: PS>  Exit-PSHostProcess
PS>
```

이 예제에서는 PSHostProcess에 설명 된 대로 프로세스의 runspace에서 실행 되는 스크립트를 디버깅 하기 위해 활성 프로세스로 작업 하 고 있습니다. **끝내기** 명령을 입력 하 여 디버거를 종료 한 후 **PSHostProcess** cmdlet을 실행 하 여 프로세스와의 대화형 세션을 닫습니다.
Cmdlet은 프로세스에서 세션을 닫고 PS C: \\ \> 프롬프트로 돌아갑니다.

## PARAMETERS

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

## 출력

## 참고

## 관련 링크

[Enter-PSHostProcess](Enter-PSHostProcess.md)
