---
external help file: Get-DSCConfiguration.cdxml-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/get-dscconfiguration?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-DscConfiguration
ms.openlocfilehash: 42b24e72de4c4bcc9326d52861c08a05853b18e0
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93215354"
---
# Get-DscConfiguration

## 개요
노드의 현재 구성을 가져옵니다.

## SYNTAX

```
Get-DscConfiguration [-CimSession <CimSession[]>] [-ThrottleLimit <Int32>] [-AsJob] [<CommonParameters>]
```

## 설명
Start-dscconfiguration cmdlet은 노드의 현재 구성 (구성이 있는 경우 **)** 을 가져옵니다.
CIM(Common Information Model) 세션을 사용하여 컴퓨터를 지정합니다.
대상 컴퓨터를 지정하지 않으면 cmdlet이 로컬 컴퓨터의 구성을 가져옵니다.

## 예제

### 예 1: 로컬 컴퓨터에 대 한 구성 가져오기

```
PS C:\> Get-DscConfiguration
```

이 명령은 로컬 컴퓨터의 현재 상태를 가져옵니다.

### 예 2: 지정 된 컴퓨터에 대 한 구성 가져오기

```
PS C:\> $Session = New-CimSession -ComputerName "Server01" -Credential ACCOUNTS\PattiFuller
PS C:\> Get-DscConfiguration -CimSession $Session
```

이 예제에서는 CIM 세션에 지정 된 컴퓨터에서 현재 상태를 가져옵니다.
또한 cmdlet에 사용하기 위해 이름이 Server01인 컴퓨터에 대한 CIM 세션을 만듭니다.
또는 지정한 여러 컴퓨터에 cmdlet을 적용하기 위해 CIM 세션 배열을 만듭니다.

첫 번째 명령은 **New-CimSession** cmdlet을 사용하여 CIM 세션을 만든 다음 **CimSession** 개체를 **$Session** 변수에 저장합니다.
또한 암호를 입력하라는 메시지를 표시합니다.
자세한 내용을 보려면 `Get-Help New-CimSession`를 입력하십시오.

두 번째 명령은 **$Session** 변수에 저장된 **CimSession** 개체로 식별된 컴퓨터(이 경우 이름이 $Server01인 컴퓨터)의 현재 구성을 가져옵니다.

## PARAMETERS

### -AsJob
이 cmdlet이 명령을 백그라운드 작업으로 실행 함을 나타냅니다.

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

### -CimSession
원격 세션에서 또는 원격 컴퓨터에서 cmdlet을 실행합니다.
[CimSession](/powershell/module/cimcmdlets/new-cimsession) 또는 [CimSession](/powershell/module/cimcmdlets/get-cimsession) cmdlet의 출력과 같은 컴퓨터 이름 또는 세션 개체를 입력 합니다.
기본값은 로컬 컴퓨터의 현재 세션입니다.

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: (All)
Aliases: Session

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit
cmdlet을 실행하도록 설정할 수 있는 최대 동시 작업 수를 지정합니다.
이 매개 변수를 생략 하거나 값을 `0` 입력 하면 Windows PowerShell은 컴퓨터에서 실행 되는 CIM cmdlet의 수에 따라 cmdlet에 대 한 최적의 스로틀 제한을 계산 합니다.
스로틀 제한은 현재 cmdlet에만 적용되며 세션이나 컴퓨터에는 적용되지 않습니다.

```yaml
Type: System.Int32
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

## 출력

## 참고

## 관련 링크

[Windows PowerShell Desired State Configuration 개요](/powershell/scripting/dsc/overview/dscforengineers)

[Get-DscConfigurationStatus](Get-DscConfigurationStatus.md)

[Restore-DscConfiguration](Restore-DscConfiguration.md)

[Start-DscConfiguration](Start-DscConfiguration.md)

[Test-DscConfiguration](Test-DscConfiguration.md)
