---
external help file: PSDesiredStateConfiguration-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/new-dscchecksum?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-DscChecksum
ms.openlocfilehash: 2637cc092d3be2bb3bff051268ef288c81ef3ad7
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93212481"
---
# New-DscChecksum

## 개요
DSC 문서 및 DSC 리소스에 대 한 체크섬 파일을 만듭니다.

## SYNTAX

```
New-DscChecksum [-Path] <String[]> [[-OutPath] <String>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명

**새-dscchecksum** Cmdlet은 PowerShell Dsc (필요한 상태 구성) 문서 및 압축 된 dsc 리소스에 대 한 체크섬 파일을 생성 합니다.
이 cmdlet은 끌어오기 모드에서 사용할 각 구성 및 리소스에 대 한 체크섬 파일을 생성 합니다.
DSC 서비스는 체크섬을 사용 하 여 대상 노드에 올바른 구성 및 리소스가 있는지 확인 합니다.
DSC 서비스 저장소에서 연결 된 DSC 문서와 압축 된 DSC 리소스와 함께 체크섬을 저장 합니다.

## 예제

### 예 1: 특정 경로의 모든 구성에 대 한 체크섬 파일 만들기

```
PS C:\> New-DscCheckSum -Path "C:\DSC\Configurations\"
```

이 명령은 C:\DSC\Configurations 경로에 모든 구성에 대한 체크섬 파일을 만듭니다.
이미 있는 체크섬 파일은 모두 건너뜁니다.

### 예 2: 특정 경로의 모든 구성에 대 한 체크섬 파일을 만들고 기존 체크섬 파일을 덮어씁니다.

```
PS C:\> New-DscCheckSum -Path "C:\DSC\Configurations\" -Force
```

이 명령은 C:\DSC\Configurations 경로에 모든 구성에 대한 새 체크섬 파일을 만듭니다.
*Force* 매개 변수를 지정 하면 명령이 이미 있는 체크섬 파일을 덮어씁니다.

## PARAMETERS

### -Confirm

cmdlet을 실행하기 전에 확인을 요청합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

cmdlet이 지정한 출력 파일을 덮어씀을 나타냅니다(파일이 이미 있는 경우).

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

### -OutPath

체크섬 출력 파일의 경로 및 파일 이름을 지정합니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

입력 파일의 경로를 지정 합니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: ConfigurationPath

Required: True
Position: 0
Default value: None
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
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### 없음

## 출력

### System.Object

## 참고

## 관련 링크

[Windows PowerShell Desired State Configuration 개요](/powershell/scripting/dsc/overview/dscforengineers)
