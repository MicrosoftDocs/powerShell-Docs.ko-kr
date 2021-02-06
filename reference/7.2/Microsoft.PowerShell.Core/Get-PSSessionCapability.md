---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-pssessioncapability?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSSessionCapability
ms.openlocfilehash: e81302a442294a7eeab81c6e8e1c6b7fd0cfb5fe
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603302"
---
# Get-PSSessionCapability

## 개요
제한 된 세션 구성에 대 한 특정 사용자의 기능을 가져옵니다.

## SYNTAX

```
Get-PSSessionCapability [-ConfigurationName] <String> [-Username] <String> [-Full] [<CommonParameters>]
```

## 설명

**Get PSSessionCapability** cmdlet은 제한 된 세션 구성에 대 한 특정 사용자의 기능을 가져옵니다.
이 cmdlet을 사용 하 여 사용자에 대 한 사용자 지정 세션 구성을 감사 합니다.

Windows PowerShell 5.0부터 세션 구성 파일 (.psc)의 **Roledefinitions** 속성을 사용할 수 있습니다.
이 속성을 사용 하면 그룹 멤버 자격에 따라 제한 된 단일 끝점에 대 한 다양 한 기능을 사용자에 게 부여할 수 있습니다.
**Get PSSessionCapability** cmdlet은 사용자에 게 부여 된 정확한 기능을 확인할 수 있도록 허용 하 여 이러한 끝점을 감사할 때 복잡성을 줄입니다.

기본적으로 **Get PSSessionCapability** cmdlet은 지정 된 사용자가 지정 된 끝점에서 실행할 수 있는 명령 목록을 반환 합니다.
이는 지정 된 끝점에서 **Get 명령을** 실행 하는 사용자와 동일 합니다.
*Full* 매개 변수를 사용 하 여 실행 하는 경우이 Cmdlet은 **InitialSessionState** 개체를 반환 합니다.
이 개체에는 지정 된 끝점에 대해 지정 된 사용자가 상호 작용 하는 PowerShell runspace에 대 한 세부 정보가 포함 됩니다.
여기에는 언어 모드, 실행 정책, 환경 변수 등의 정보가 포함 됩니다.

## 예제

### 예제 1: 사용자에 대해 사용할 수 있는 명령 가져오기

```powershell
Get-PSSessionCapability -ConfigurationName Endpoint1 -Username 'CONTOSO\User'
```

이 예에서는 로컬 컴퓨터의 Endpoint1 제약 된 끝점에 연결할 때 사용자 CONTOSO\User에 사용할 수 있는 명령을 반환 합니다.

### 예제 2: 사용자에 대 한 runspace에 대 한 세부 정보 가져오기

```powershell
Get-PSSessionCapability -ConfigurationName Endpoint1 -Username 'CONTOSO\User' -Full
```

이 예에서는 Endpoint1 제약 된 끝점에 연결할 때 사용자 CONTOSO\User가 상호 작용 하는 runspace에 대 한 세부 정보를 반환 합니다.

## PARAMETERS

### -ConfigurationName

검사 하 고 있는 제한 된 세션 구성 (끝점)을 지정 합니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Full

이 cmdlet이 지정 된 제한 된 끝점에서 지정 된 사용자에 대 한 전체 초기 세션 상태를 반환 함을 나타냅니다.

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

### -Username

검사 하 고 있는 기능의 사용자를 지정 합니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

## 출력

### System.management.automation.aliasinfo.

### System.object를 관리 합니다.

### System.Management.Automation.Runspaces.InitialSessionState

## 참고

## 관련 링크

[New-PSRoleCapabilityFile](New-PSRoleCapabilityFile.md)

