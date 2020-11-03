---
external help file: Stop-DscConfiguration.cdxml-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 08/19/2019
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/stop-dscconfiguration?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-DscConfiguration
ms.openlocfilehash: 93c8585ae948dfa360a2ae8e2563670de8fd6e93
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93213601"
---
# Stop-DscConfiguration

## 개요
실행 중인 구성 작업을 중지 합니다.

## SYNTAX

### 모두

```
Stop-DscConfiguration [-Force] [-CimSession <CimSession[]>] [-ThrottleLimit <Int32>] [-AsJob]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명

Cmdlet은를 `Stop-DscConfiguration` 실행 하는 구성 작업을 중지 합니다. CIM(Common Information Model) (CIM) 세션을 사용 하 여이 cmdlet이 적용 되는 컴퓨터를 지정 합니다. 실행 중인 구성 작업이 없는 경우이 cmdlet은 경고 메시지를 반환 합니다.

`Stop-DscConfiguration` 는 Microsoft 지원 라이브러리에서 [WINDOWS RT 8.1, Windows 8.1 및 Windows Server 2012 r 2에 대 한 11 월 2014 업데이트 롤업의](https://support.microsoft.com/kb/3000850) 일부로만 사용할 수 있습니다. 이 cmdlet을 사용 하기 전에 [Windows PowerShell 5.0의 새로운 기능](/powershell/scripting/whats-new/What-s-New-in-Windows-PowerShell-50) 정보를 검토 하십시오.

## 예제

### 예제 1: 구성 작업 중지

이 예제에서는 cmdlet을 사용 하 여 CIM 세션을 만듭니다 `New-CimSession` . **CimSession** 개체는 실행 중인 구성 작업을 중지 하는 데 사용 됩니다.

```powershell
$Session = New-CimSession -ComputerName Server01 -Credential ACCOUNTS\User01
Stop-DscConfiguration -CimSession $Session
```

`New-CimSession`**ComputerName** 매개 변수를 사용 하 여 Server01 컴퓨터를 지정 합니다. **Credential** 매개 변수는 사용자 계정을 지정 합니다. **CimSession** 개체는 변수에 저장 됩니다 `$Session` . 명령이 실행 되 면 사용자 계정의 암호를 입력 하 라는 메시지가 표시 됩니다.

`Stop-DscConfiguration` 는 **CimSession** 매개 변수 및에 저장 된 개체를 사용 하 여 `$Session` 구성 작업을 중지 합니다.

## PARAMETERS

### -AsJob

이 cmdlet이 명령을 백그라운드 작업으로 실행 함을 나타냅니다. PowerShell 백그라운드 작업에 대 한 자세한 내용은 [about_Jobs](../Microsoft.PowerShell.Core/About/about_Jobs.md) 및 [about_Remote_Jobs](../Microsoft.PowerShell.Core/About/about_Remote_Jobs.md)를 참조 하세요.

**AsJob** 매개 변수를 사용 하려면 원격 컴퓨터에 대 한 로컬 및 원격 컴퓨터를 구성 해야 합니다. Windows Vista 이상 버전의 Windows 운영 체제에서는 **관리자 권한으로 실행** 옵션을 사용 하 여 PowerShell을 열어야 합니다. 자세한 내용은 [about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md)을 참조하세요.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -CimSession

원격 세션에서 또는 원격 컴퓨터에서 cmdlet을 실행합니다. 컴퓨터 이름 또는 세션 개체 (예: 또는의 출력)를 입력 `New-CimSession` 합니다 `Get-CimSession` .

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

### -Confirm

`Stop-DscConfiguration` 는 **Confirm** 매개 변수를 지원 하지 않습니다. **Confirm** 매개 변수를 사용 하면 오류가 표시 됩니다.

**확인** 을 지 원하는 PowerShell cmdlet의 경우 매개 변수를 사용 하 여 명령을 실행 하기 전에 확인 메시지를 표시 합니다.

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

사용자 확인을 요청하지 않고 명령을 강제 실행합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit

cmdlet을 실행하도록 설정할 수 있는 최대 동시 작업 수를 지정합니다.

이 매개 변수를 생략 하거나 값을 `0` 입력 하면 PowerShell은 컴퓨터에서 실행 되는 CIM cmdlet의 수에 따라 최적 스로틀 제한을 계산 합니다. 스로틀 제한은 현재 cmdlet에만 적용되며 세션이나 컴퓨터에는 적용되지 않습니다.

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

### -WhatIf

cmdlet을 실행할 경우 발생하는 일을 표시합니다. Cmdlet이 실행 되지 않습니다.

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

### 없음

## 참고

## 관련 링크

[Get-CimSession](../CimCmdlets/Get-CimSession.md)

[Get-DscConfiguration](Get-DscConfiguration.md)

[Get-DscConfigurationStatus](Get-DscConfigurationStatus.md)

[New-CimSession](../CimCmdlets/New-CimSession.md)

[Restore-DscConfiguration](Restore-DscConfiguration.md)

[Start-DscConfiguration](Start-DscConfiguration.md)

[Test-DscConfiguration](Test-DscConfiguration.md)

[Update-DscConfiguration](Update-DscConfiguration.md)

[Windows PowerShell Desired State Configuration 개요](/powershell/scripting/dsc/overview/overview)
