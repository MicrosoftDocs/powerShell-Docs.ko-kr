---
external help file: PSDesiredStateConfiguration-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 07/23/2020
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/get-dscresource?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-DscResource
ms.openlocfilehash: 7eba6a561ff0220d0624c49b109f1558822f1064
ms.sourcegitcommit: 9dddf1d2e91ebcd347fcfb7bf6ef670d49a12ab7
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/24/2020
ms.locfileid: "93218993"
---
# Get-DscResource

## 개요
컴퓨터에 있는 DSC (Desired State Configuration) 리소스를 가져옵니다.

## SYNTAX

```
Get-DscResource [[-Name] <String[]>] [[-Module] <Object>] [-Syntax] [<CommonParameters>]
```

## 설명

`Get-DscResource`Cmdlet은 컴퓨터에 있는 POWERSHELL DSC 리소스를 검색 합니다. 이 cmdlet은 PSModulePath에 설치 된 리소스만 검색 합니다. 사용자가 만든 기본 제공 및 사용자 지정 공급자에 대 한 세부 정보를 표시 합니다. 또한이 cmdlet은 모듈로 패키지 되거나 런타임에 생성 되는 다른 구성 인 복합 리소스에 대 한 세부 정보를 표시 합니다.

## 예제

### 예제 1: 로컬 컴퓨터의 모든 리소스 가져오기

```powershell
 Get-DscResource
```

이 명령은 로컬 컴퓨터의 모든 리소스를 가져옵니다.

### 예제 2: 이름을 지정 하 여 리소스 가져오기

```powershell
Get-DscResource -Name "WindowsFeature"
```

이 명령은 WindowsFeature 리소스를 가져옵니다.

### 예제 3: 모듈에서 모든 리소스 가져오기

```powershell
Get-DscResource -Module "xHyper-V"
```

이 명령은 xHyper 모듈에서 모든 리소스를 가져옵니다.

### 예제 4: 와일드 카드 문자를 사용 하 여 리소스 가져오기

```powershell
Get-DscResource -Name P*,r*
```

이 명령은 **Name** 매개 변수로 지정 된 와일드 카드 패턴과 일치 하는 모든 리소스를 가져옵니다.

### 예 5: 리소스 구문 가져오기

```powershell
Get-DscResource -Name "WindowsFeature" -Syntax
```

이 명령은 WindowsFeature 리소스를 가져오고 리소스에 대한 구문을 보여 줍니다.

### 예제 6: 리소스에 대 한 모든 속성 가져오기

```powershell
Get-DscResource -Name "User" | Select-Object -ExpandProperty Properties
```

이 명령은 사용자 리소스를 가져온 다음 파이프라인 연산자를 사용하여 사용자 리소스의 모든 속성을 반환합니다.

### 예 7: 지정 된 버전의 지정 된 모듈에서 모든 리소스 가져오기

```powershell
Get-DscResource -Module @{ModuleName='xHyper-V';RequiredVersion='3.0.0.0'}
```

이 명령은 3.0.0.0 버전의 xHyper 모듈에서 모든 리소스를 가져옵니다.

## PARAMETERS

### -모듈

DSC 리소스를 볼 모듈의 이름 또는 정규화 된 이름을 지정 합니다.

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Name

보려는 DSC 리소스의 이름 배열을 지정 합니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -구문

Cmdlet이 지정 된 DSC 리소스의 구문 보기를 반환 함을 나타냅니다. 반환 된 구문은 PowerShell 스크립트에서 리소스를 사용 하는 방법을 보여 줍니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.String[]

### System.Object

## 출력

### DesiredStateConfiguration. DscResourceInfo []

### string[]

## 참고

- `Get-DscResource` 7.0 미만의 PowerShell 버전에서 클래스 기반 DSC 리소스를 찾을 수 없습니다.

## 관련 링크

[PowerShell 필요한 상태 구성 개요](/powershell/scripting/dsc/overview/overview)

[Invoke-DscResource](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource)
