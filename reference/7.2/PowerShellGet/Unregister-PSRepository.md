---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/unregister-psrepository?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unregister-PSRepository
ms.openlocfilehash: 908a43506bfbff964cfbdd8eea270b1fa42c3e77
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99601438"
---
# Unregister-PSRepository

## 개요
리포지토리 등록을 취소합니다.

## SYNTAX

```
Unregister-PSRepository [-Name] <String[]> [<CommonParameters>]
```

## 설명

`Unregister-PSRepository`Cmdlet은 현재 사용자의 리포지토리 등록을 취소 합니다.

## 예제

### 예제 1: 리포지토리 등록 취소

이 예제에서는 myNuGetSource 이라는 리포지토리의 등록을 취소 합니다.

```powershell
Unregister-PSRepository -Name "myNuGetSource"
```

### 예제 2: 모든 리포지토리 등록 취소

이 예제에서는 `Get-PSRepository` 를 사용 하 여 등록 된 모든 리포지토리를 가져온 다음 파이프라인 연산자를 사용 하 여이를 `Unregister-PSRepository` 등록 취소 하기 위해 전달 합니다.

```powershell
Get-PSRepository | Unregister-PSRepository
```

## PARAMETERS

### -Name

제거할 리포지토리의 이름 배열을 지정 합니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.String[]

## 출력

### System.Object

## 참고

## 관련 링크

[Get-PSRepository](Get-PSRepository.md)

[Register-PSRepository](Register-PSRepository.md)

[Set-PSRepository](Set-PSRepository.md)
