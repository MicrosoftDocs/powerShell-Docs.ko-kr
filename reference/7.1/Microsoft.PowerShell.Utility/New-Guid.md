---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Guid
ms.openlocfilehash: 2a289500020f069231023fbabaa5401ee0759697
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/02/2020
ms.locfileid: "93209293"
---
# New-Guid

## 개요
GUID를 만듭니다.

## SYNTAX

```
New-Guid [<CommonParameters>]
```

## 설명

**새 guid** cmdlet은 임의의 guid (globally unique identifier)를 만듭니다.
스크립트에 고유 ID가 필요한 경우 필요에 따라 GUID를 만들 수 있습니다.

## 예제

### 예제 1: GUID 만들기

```
PS C:\> New-Guid
Guid
----
0352cf0f-2e7a-4aee-801d-7f27f8344c77
```

이 명령은 임의의 GUID를 만듭니다.
또는 스크립트의 다른 곳에서 사용 하기 위해이 cmdlet의 출력을 변수에 저장할 수 있습니다.

## PARAMETERS

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

## 출력

### System.Guid

이 cmdlet은 GUID를 반환 합니다.

## 참고

## 관련 링크

