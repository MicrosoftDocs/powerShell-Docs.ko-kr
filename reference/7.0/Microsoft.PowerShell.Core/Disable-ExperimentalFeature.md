---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/06/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/disable-experimentalfeature?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-ExperimentalFeature
ms.openlocfilehash: 4407784b6e7e2897610991dbd449997143471134
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93214762"
---
# Disable-ExperimentalFeature

## 개요
PowerShell의 새 인스턴스를 시작할 때 실험적 기능을 사용 하지 않도록 설정 합니다.

## SYNTAX

```
Disable-ExperimentalFeature [-Name] <String[]> [-Scope <ConfigScope>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명

`Disable-ExperimentalFeature`Cmdlet은 `powershell.config.json` PowerShell 시작 시 읽은 설정 파일에서 명명 된 실험적 기능을 제거 하 여 실험적 기능을 사용 하지 않도록 설정 합니다.

이 cmdlet은 PowerShell 6.2에서 도입 되었습니다.

> [!NOTE]
> 실험적 기능 상태에 대 한 변경 내용은 PowerShell을 다시 시작 하는 경우에만 적용 됩니다.

## 예제

### 예제 1: 실험적 기능 사용 안 함

이 예에서는 이전에이 실험적 기능을 사용 하도록 설정한 경우 `powershell.config.json` PowerShell이 다시 시작 되 면 사용자가 해당 기능을 사용 하도록 설정 하지 않도록 파일이 업데이트 됩니다.
성공 하면 파이프라인이 파이프라인으로 출력 되지 않고 경고 메시지만 표시 됩니다.

```powershell
PS C:\> Disable-ExperimentalFeature PSImplicitRemotingBatching
```

```Output
WARNING: Enabling and disabling experimental features do not take effect until next start of PowerShell.
```

## PARAMETERS

### -Confirm

cmdlet을 실행하기 전에 확인을 요청합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

사용 하지 않도록 설정할 실험적 기능의 이름입니다.

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

### -범위

`powershell.config.json`모든 사용자에 게 영향을 주는지 아니면 현재 사용자 에게만 영향을 주는지 여부를 업데이트 합니다.

```yaml
Type: System.Management.Automation.Configuration.ConfigScope
Parameter Sets: (All)
Aliases:
Accepted values: AllUsers, CurrentUser

Required: False
Position: Named
Default value: CurrentUser
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

cmdlet을 실행할 경우 발생하는 일을 표시합니다.
cmdlet은 실행되지 않습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### ExperimentalFeature

Cmdlet에서 ExperimentalFeature의 파이프 인스턴스 `Get-ExperimentalFeature` 를 사용 하지 않도록 설정 합니다.

## 출력

### 없음

이 cmdlet은 어떠한 출력도 반환되지 않습니다.

## 참고

실험적 기능의 상태 변경은 PowerShell을 다시 시작 하는 경우에만 적용 됩니다.

## 관련 링크

[Enable-ExperimentalFeature](Enable-ExperimentalFeature.md)

[Get-ExperimentalFeature](Get-ExperimentalFeature.md)
