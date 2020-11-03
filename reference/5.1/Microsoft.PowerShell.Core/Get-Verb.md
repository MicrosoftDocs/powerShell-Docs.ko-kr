---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
ms.date: 09/07/2018
Module Name: Microsoft.PowerShell.Core
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/functions/get-verb?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Verb
ms.openlocfilehash: 4474bb50c2bf3be10e72d2554190208e956f9040
ms.sourcegitcommit: 7d052985c20761fdf4c6d7ce4e04df4c551c36a3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/11/2020
ms.locfileid: "93219497"
---
# Get-Verb

## 개요
승인 된 PowerShell 동사를 가져옵니다.

## SYNTAX

```
Get-Verb [[-verb] <String[]>] [<CommonParameters>]
```

## 설명

`Get-Verb`함수는 PowerShell 명령에서 사용 하도록 승인 된 동사를 가져옵니다.

PowerShell에서는 cmdlet 및 함수 이름에 Verb-Noun 형식을 지정 하 고 승인 된 동사를 포함 하는 것이 좋습니다. 이 방법을 사용 하면 명령 이름을 보다 일관 되 고 예측 가능 하며 더 쉽게 사용할 수 있습니다.

승인 되지 않은 동사를 사용 하는 명령은 PowerShell에서 실행 됩니다. 그러나 이름에 승인 되지 않은 동사가 포함 된 명령이 있는 모듈을 가져올 경우이 `Import-Module` 명령은 경고 메시지를 표시 합니다.

> [!NOTE]
> 에서 반환 하는 동사 목록이 `Get-Verb` 불완전할 수 있습니다. 설명으로 승인 된 PowerShell 동사의 업데이트 된 목록은 Microsoft Docs에서 [승인 된 동사](../../docs-conceptual/developer/cmdlet/approved-verbs-for-windows-powershell-commands.md) 를 참조 하세요.

## 예제

### 예 1-모든 동사의 목록 가져오기

```powershell
Get-Verb
```

### 예 2-"un"으로 시작 하는 승인 된 동사 목록 가져오기

```powershell
Get-Verb un*
```

```Output
Verb                 Group
----                 -----
Undo                 Common
Unlock               Common
Unpublish            Data
Uninstall            Lifecycle
Unregister           Lifecycle
Unblock              Security
Unprotect            Security
```

### 예 3-보안 그룹에서 승인 된 모든 동사 가져오기

```powershell
Get-Verb | Where-Object Group -EQ Security
```

```Output
Verb      Group
----      -----
Block     Security
Grant     Security
Protect   Security
Revoke    Security
Unblock   Security
Unprotect Security
```

### 예제 4-승인 되지 않은 동사가 있는 모듈의 모든 명령을 찾습니다.

```powershell
Get-Command -Module Microsoft.PowerShell.Utility | Where-Object Verb -NotIn (Get-Verb).Verb
```

```Output
CommandType     Name            Version    Source
-----------     ----            -------    ------
Cmdlet          Sort-Object     3.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Tee-Object      3.1.0.0    Microsoft.PowerShell.Utility
```

## PARAMETERS

### -동사

지정된 동사만 가져옵니다.
동사의 이름 또는 이름 패턴을 입력하세요.
와일드카드를 사용할 수 있습니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: All verbs
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
```

## 입력

### 없음

## 출력

### Selected.Microsoft.PowerShell.Commands.MemberDefinition

## 참고

`Get-Verb` Microsoft. PowerShell. MemberDefinition 개체의 수정 된 버전을 반환 합니다.
이 개체에 MemberDefinition 개체의 표준 속성이 없습니다. 대신 이 개체는 Verb 및 Group 속성을 갖습니다. Verb 속성에는 동사 이름의 문자열이 포함됩니다. Group 속성에는 동사 그룹의 문자열이 포함됩니다.

PowerShell 동사는 가장 일반적인 용도에 따라 그룹에 할당 됩니다. 그룹은 동사의 용도를 제한하지 않으면서 쉽게 찾고 비교할 수 있게 합니다. 모든 유형의 명령에 대해 승인된 모든 동사를 사용할 수 있습니다.

각 PowerShell 동사는 다음 그룹 중 하나에 할당 됩니다.

- Common: 추가와 같은 거의 모든 cmdlet에 적용할 수 있는 일반 동작을 정의 합니다.
- 통신: Connect와 같은 통신에 적용 되는 작업을 정의 합니다.
- 데이터: 백업 등의 데이터 처리에 적용 되는 동작을 정의 합니다.
- 진단: 디버그와 같은 진단에 적용 되는 작업을 정의 합니다.
- 수명 주기: cmdlet의 수명 주기 (예: Complete)에 적용 되는 작업을 정의 합니다.
- 보안: Revoke와 같은 보안에 적용 되는 작업을 정의 합니다.
- 기타: 다른 유형의 작업을 정의 합니다.

PowerShell과 함께 설치 되는 일부 cmdlet (예: 및)은 승인 되지 않은 `Tee-Object` `Where-Object` 동사를 사용 합니다. 이러한 cmdlet은 기록 예외 이며 해당 동사는 **예약** 된 것으로 분류 됩니다.

## 관련 링크

[모듈 가져오기](import-module.md)
