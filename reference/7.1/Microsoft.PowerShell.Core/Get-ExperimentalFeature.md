---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/01/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-experimentalfeature?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ExperimentalFeature
ms.openlocfilehash: cd023cb91dd7ae15b2b10954920d133089b7d05c
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/12/2021
ms.locfileid: "103196261"
---
# Get-ExperimentalFeature

## 개요
실험적 기능을 가져옵니다.

## SYNTAX

```
Get-ExperimentalFeature [[-Name] <String[]>] [<CommonParameters>]
```

## 설명

`Get-ExperimentalFeature`Cmdlet은 PowerShell에서 검색 된 모든 실험적 기능을 반환 합니다.
실험적 기능은 모듈 또는 PowerShell 엔진에서 가져올 수 있습니다. 사용자는 실험적 기능을 사용 하 여 새로운 기능을 안전 하 게 테스트 하 고, 일반적으로 GitHub를 통해 피드백을 제공할 수 있습니다.

## 예제

### 예 1

현재 등록 된 실험적 기능 목록과 현재 상태를 가져옵니다.

```powershell
Get-ExperimentalFeature
```

```Output
Name                         Enabled Source      Description
----                         ------- ------      -----------
PSImplicitRemotingBatching   False PSEngine      Batch implicit remoting proxy commands to improve performance
```

## PARAMETERS

### -Name

반환할 특정 실험적 기능의 이름 또는 이름입니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.String[]

반환할 실험적 기능의 이름 또는 이름입니다.

## 출력

### ExperimentalFeature

지정 된 이름이 없는 경우 요청 된 이름이 나 모든 실험적 기능과 일치 하는 인스턴스를 반환 합니다.

## 관련 링크

[Disable-ExperimentalFeature](Disable-ExperimentalFeature.md)

[Enable-ExperimentalFeature](Enable-ExperimentalFeature.md)

