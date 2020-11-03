---
external help file: Microsoft.PowerShell.Operation.Validation-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Operation.Validation
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.operation.validation/get-operationvalidation?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-OperationValidation
ms.openlocfilehash: 22ff12848fb7aefaa7f684ee5d8723cc723a5879
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93214289"
---
# Get-OperationValidation

## 개요
작업 유효성 검사 프레임 워크 테스트를 가져옵니다.

## SYNTAX

```
Get-OperationValidation [[-ModuleName] <String[]>] [-TestType <String[]>] [<CommonParameters>]
```

## 설명
**가져오기 operationvalidation** cmdlet은 설치 된 모듈에 대 한 작업 유효성 검사 프레임 워크 테스트를 가져옵니다.

진단 폴더를 포함 하는 모듈은 단순 또는 포괄적인 하위 폴더 또는 둘 다에서 Pester 테스트에 대해 검사 됩니다.

## 예제

### 예제 1: 작업 유효성 검사 테스트 가져오기

```
PS C:\> Get-OperationValidation -ModuleName "C:\temp\modules\AddNumbers"
    Type:     Simple
    File:     addnum.tests.ps1
    FilePath: C:\temp\modules\AddNumbers\Diagnostics\Simple\addnum.tests.ps1
    Name:
        Add-Em
        Subtract em
        Add-Numbers
    Type:     Comprehensive
    File:     Comp.Adding.Tests.ps1
    FilePath: C:\temp\modules\AddNumbers\Diagnostics\Comprehensive\Comp.Adding.Tests.ps1
    Name:
        Comprehensive Adding Tests
        Comprehensive Subtracting Tests
        Comprehensive Examples
```

이 명령은 C:\temp\modules 폴더의 AddNumbers 이라는 모듈에서 유효성 검사 테스트를 가져옵니다.

## PARAMETERS

### -ModuleName
모듈의 이름 배열을 지정 합니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TestType
테스트 형식의 배열을 지정 합니다.
유효한 값은 Simple, 포괄적 또는 both입니다.
기본값은 "Simple, 포괄적"입니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:
Accepted values: Simple, Comprehensive

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### 없음
이 cmdlet에 대 한 입력을 파이프 할 수 없습니다.

## 출력

### PSCustomObject
**PSCustomObject** 유효성 검사에 대해 설명 합니다.

## 참고

## 관련 링크

[Invoke-OperationValidation](Invoke-OperationValidation.md)
