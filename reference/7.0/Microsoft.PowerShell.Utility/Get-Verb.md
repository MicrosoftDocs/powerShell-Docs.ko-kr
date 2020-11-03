---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/07/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-verb?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Verb
ms.openlocfilehash: a1459c276d8d6b2d031bc4b4f7ab521f7582a4cb
ms.sourcegitcommit: 7d052985c20761fdf4c6d7ce4e04df4c551c36a3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/11/2020
ms.locfileid: "93219505"
---
# Get-Verb

## 개요
승인 된 PowerShell 동사를 가져옵니다.

## SYNTAX

```
Get-Verb [[-Verb] <String[]>] [[-Group] <String[]>] [<CommonParameters>]
```

## 설명

`Get-Verb`함수는 PowerShell 명령에서 사용 하도록 승인 된 동사를 가져옵니다.

PowerShell cmdlet 및 함수 이름은 형식이 며 승인 된 동사를 포함 하는 것이 좋습니다 `Verb-Noun` . 이 방법을 사용 하면 명령 이름을 보다 일관 되 고 예측 가능 하며 더 쉽게 사용할 수 있습니다.

승인 되지 않은 동사를 사용 하는 명령이 PowerShell에서 계속 실행 됩니다. 그러나 이름에 승인 되지 않은 동사가 포함 된 명령이 있는 모듈을 가져올 경우이 `Import-Module` 명령은 경고 메시지를 표시 합니다.

> [!NOTE]
> 에서 반환 하는 동사 목록이 `Get-Verb` 불완전할 수 있습니다. 설명으로 승인 된 PowerShell 동사의 업데이트 된 목록은 Microsoft Docs에서 [승인 된 동사](../../docs-conceptual/developer/cmdlet/approved-verbs-for-windows-powershell-commands.md) 를 참조 하세요.

## 예

### 예 1-모든 동사의 목록 가져오기

```powershell
Get-Verb
```

### 예 2-"un"으로 시작 하는 승인 된 동사 목록 가져오기

```powershell
Get-Verb un*
```

```Output
Verb       AliasPrefix Group     Description
----       ----------- -----     -----------
Undo       un          Common    Sets a resource to its previous state
Unlock     uk          Common    Releases a resource that was locked
Unpublish  ub          Data      Makes a resource unavailable to others
Uninstall  us          Lifecycle Removes a resource from an indicated location
Unregister ur          Lifecycle Removes the entry for a resource from a repository
Unblock    ul          Security  Removes restrictions to a resource
Unprotect  up          Security  Removes safeguards from a resource that were added to prevent it from attack or loss
```

### 예 3-보안 그룹에서 승인 된 모든 동사 가져오기

```powershell
Get-Verb -Group Security
```

```Output
Verb      AliasPrefix Group    Description
----      ----------- -----    -----------
Block     bl          Security Restricts access to a resource
Grant     gr          Security Allows access to a resource
Protect   pt          Security Safeguards a resource from attack or loss
Revoke    rk          Security Specifies an action that does not allow access to a resource
Unblock   ul          Security Removes restrictions to a resource
Unprotect up          Security Removes safeguards from a resource that were added to prevent it from attack or loss
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

지정된 동사만 가져옵니다. 동사의 이름 또는 이름 패턴을 입력하세요. 와일드카드를 사용할 수 있습니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:
Accepted values: Common, Communications, Data, Diagnostic, Lifecycle, Other, Security

Required: False
Position: 1
Default value: All groups
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -그룹

지정 된 그룹만 가져옵니다. 그룹의 이름을 입력 합니다. 와일드 카드는 사용할 수 없습니다.

이 매개 변수는 PowerShell 6.0에서 도입 되었습니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: All verbs
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### 없음

## 출력

### VerbInfo.

## 참고

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

[모듈 가져오기](../microsoft.powershell.core/import-module.md)
