---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-uiculture?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-UICulture
ms.openlocfilehash: 098e98dec6733af036795e4decb633f59d40c633
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/02/2020
ms.locfileid: "93209048"
---
# Get-UICulture

## 개요
운영 체제의 현재 UI 문화권 설정을 가져옵니다.

## SYNTAX

```
Get-UICulture [<CommonParameters>]
```

## 설명
**UICulture** Cmdlet은 Windows의 현재 UI (사용자 인터페이스) 문화권 설정에 대 한 정보를 가져옵니다.
UI 문화권에 따라 메뉴, 메시지 등의 사용자 인터페이스 요소에 사용되는 텍스트 문자열이 결정됩니다.

시스템의 현재 문화권을 가져오는 Get-Culture cmdlet을 사용할 수도 있습니다.
문화권에 따라 숫자, 통화, 날짜 등의 항목 표시 형식이 결정됩니다.

## 예제

### 예제 1: UI 문화권 가져오기

```
PS C:\> Get-UICulture
```

이 명령은 현재 UI 문화권 정보를 가져옵니다.

### 예제 2: UI 문화권 가져오기 및 결과 서식 지정

```
PS C:\> Get-UICulture | Format-List *
```

이 명령은 현재 UI 문화권의 모든 속성에 대한 값을 목록에 표시합니다.

### 예 3: Calendar 속성 값 가져오기

```
PS C:\> (Get-UICulture).Calendar
```

이 명령은 현재 UI 문화권의 Calendar 속성에 대한 현재 값을 표시합니다.
Calendar는 UI 문화권의 한 속성입니다.
모든 속성을 보려면를 입력 `Get-UICulture | Get-Member` 합니다.

### 예제 4: 간단한 날짜 패턴 가져오기

```
PS C:\> (Get-UICulture).DateTimeFormat.ShortDatePattern
```

이 명령은 현재 UI 문화권의 간단한 날짜 표기 패턴을 표시합니다.
UI 문화권의 DateTimeFormat 속성에 대 한 모든 하위 속성을 보려면를 입력 `(Get-UICulture).DateTimeFormat | gm` 합니다.

## PARAMETERS

### CommonParameters
이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### 없음
이 cmdlet에 입력을 파이프할 수 없습니다.

## 출력

### VistaCultureInfo, Microsoft. PowerShell.
**UICulture** 는 현재 UI 문화권을 나타내는 개체를 반환 합니다.
Windows PowerShell 3.0에서는 **CultureInfo** 개체를 반환 합니다.
Windows PowerShell 2.0에서는 **VistaCultureInfo** 개체를 반환 합니다.

## 참고

* $PsCulture 및 $PsUICulture 변수를 사용할 수도 있습니다. $PsCulture 변수는 현재 문화권의 이름을 저장하고 $PsUICulture 변수는 현재 UI 문화권의 이름을 저장합니다.

*

## 관련 링크

## 관련 링크
