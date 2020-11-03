---
external help file: PSReadLine-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSReadLine
ms.date: 12/07/2018
online version: https://docs.microsoft.com/powershell/module/psreadline/psconsolehostreadline?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: PSConsoleHostReadLine
ms.openlocfilehash: 2dee8287558e9d5c001000fc5a57a859febee1a3
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/21/2020
ms.locfileid: "93224729"
---
# PSConsoleHostReadLine

## 개요
이 함수는 PSReadLine의 주 진입점입니다.

## SYNTAX

```
PSConsoleHostReadLine
```

## 설명

`PSConsoleHostReadLine` 는 PSReadLine 모듈에 대 한 주 진입점입니다. PowerShell 콘솔 호스트는 PSReadLine 모듈을 자동으로 로드 하 고이 함수를 호출 합니다. 정상적인 운영 조건에서이 함수는 명령줄에서 사용 하기 위한 것이 아닙니다.

확장 지점은 `PSConsoleHostReadLine` 콘솔 호스트에서 특수 합니다. 호스트는이 이름을 사용 하 여 별칭, 함수 또는 스크립트를 호출 합니다. PSReadLine은 콘솔 호스트에서 호출 되도록이 함수를 정의 합니다.

## 예제

### 예 1

이 함수는 명령줄에서 사용 하기 위한 것이 아닙니다.

## PARAMETERS

## 입력

### 없음

## 출력

### 없음

## 참고

## 관련 링크

[about_PSReadLine](./About/about_PSReadLine.md)
