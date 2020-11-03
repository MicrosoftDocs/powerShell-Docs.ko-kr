---
external help file: PSDiagnostics-help.xml
Module Name: PSDiagnostics
Locale: en-US
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/get-logproperties?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-LogProperties
ms.openlocfilehash: 08638749b7a5bb57bee804fccf9de17f50fd6736
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93210705"
---
# Get-LogProperties

## 개요
Windows 이벤트 로그의 속성을 검색 합니다.

## SYNTAX

```
Get-LogProperties [-Name] <Object> [<CommonParameters>]
```

## 설명

이 cmdlet은 Windows 이벤트 로그의 구성 설정을 가져옵니다. 이 cmdlet은 및 cmdlet에 사용 됩니다 `Enable-PSTrace` `Disable-PSTrace` .

## 예제

### 예 1: Windows PowerShell 이벤트 로그의 구성 설정 가져오기

```powershell
Get-LogProperties 'Windows PowerShell'
```

```Output
Name       : Windows PowerShell
Enabled    : True
Type       : Admin
Retention  : False
AutoBackup : False
MaxLogSize : 15728640
```

## PARAMETERS

### -Name

이벤트 공급자의 이름입니다.

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.String

## 출력

### Microsoft. PowerShell. LogDetails

**Psdiagnostics** 모듈은 네임 스페이스에 **logdetails** 클래스를 추가 합니다 `Microsoft.PowerShell.Diagnostics` .

## 참고

## 관련 링크

[Set-LogProperties](Set-LogProperties.md)

[Enable-PSTrace](Enable-PSTrace.md)

[Disable-PSTrace](Disable-PSTrace.md)
