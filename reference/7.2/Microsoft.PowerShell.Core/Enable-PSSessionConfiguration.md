---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enable-pssessionconfiguration?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSSessionConfiguration
ms.openlocfilehash: 86650f33f376ccb7d1428836c9d0070e749cf0ee
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99604996"
---
# Enable-PSSessionConfiguration

## 개요
로컬 컴퓨터의 세션 구성을 사용하도록 설정합니다.

## SYNTAX

```
Enable-PSSessionConfiguration [[-Name] <String[]>] [-Force] [-SecurityDescriptorSddl <String>]
 [-SkipNetworkProfileCheck] [-NoServiceRestart] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명

`Enable-PSSessionConfiguration`Cmdlet을 사용 하면 `Disable-PSSessionConfiguration` 또는 `Disable-PSRemoting` Cmdlet 또는의 **accessmode** 매개 변수를 사용 하는 등 사용 하지 않도록 설정 된 등록 된 세션 구성을 사용할 수 있습니다 `Register-PSSessionConfiguration` . 이 cmdlet은 시스템 관리자가 사용자에 대한 사용자 지정 세션을 관리하는 데 사용할 수 있는 고급 cmdlet입니다.

매개 변수가 없으면 `Enable-PSSessionConfiguration` 세션에 사용 되는 기본 구성 인 **Microsoft. PowerShell** 구성을 사용 하도록 설정 합니다.

`Enable-PSSessionConfiguration` 영향을 받는 세션 구성의 보안 설명자에서 **Deny_All** 설정을 제거 하 고, 모든 IP 주소에서 요청을 수락 하는 수신기를 설정 하 고, WinRM 서비스를 다시 시작 합니다. PowerShell 3.0 부터는에서 `Enable-PSSessionConfiguration` 세션 구성의 **Enabled** 속성 값 ( `WSMan:\<computer>\PlugIn\<SessionConfigurationName>\Enabled` )을 True로 설정 합니다. 그러나는 `Enable-PSSessionConfiguration`  `AccessMode=Local` 로컬 컴퓨터의 사용자만 세션 구성에 사용할 수 있도록 하는 Network_Deny_All () 보안 설명자 설정을 제거 하거나 변경 하지 않습니다.

## 예제

### 예제 1: 기본 세션 다시 사용

이 예제에서는 컴퓨터에서 **Microsoft. PowerShell** 기본 세션 구성을 다시 사용 하도록 설정 합니다.

```powershell
Enable-PSSessionConfiguration
```

### 예제 2: 지정 된 세션 다시 사용

이 예제에서는 컴퓨터에서 **MaintenanceShell** 및 **adminshell** 세션 구성을 다시 사용 하도록 설정 합니다.

```powershell
Enable-PSSessionConfiguration -Name MaintenanceShell, AdminShell
```

### 예제 3: 모든 세션 다시 사용

이 예에서는 컴퓨터의 모든 세션 구성을 다시 사용 하도록 설정 합니다. 이러한 명령은 동일 합니다.
따라서 둘 중 하나를 사용할 수 있습니다.

```powershell
Enable-PSSessionConfiguration -Name *
Get-PSSessionConfiguration | Enable-PSSessionConfiguration
```

`Enable-PSSessionConfiguration` 이미 사용 하도록 설정 된 세션 구성을 사용 하도록 설정 하면에서 오류를 생성 하지 않습니다.

### 예제 4: 세션을 다시 사용 하도록 설정 하 고 새 보안 설명자 지정

이 예에서는 **MaintenanceShell** 세션 구성을 다시 사용 하도록 설정 하 고 구성에 대 한 새 보안 설명자를 지정 합니다.

```powershell
$sddl = "O:NSG:BAD:P(A;;GXGWGR;;;BA)(A;;GAGR;;;S-1-5-21-123456789-188441444-3100496)S:P"
Enable-PSSessionConfiguration -Name MaintenanceShell -SecurityDescriptorSDDL $sddl
```

## PARAMETERS

### -Force

Cmdlet에서 확인 메시지를 표시 하지 않고 WinRM 서비스를 다시 시작 하 라는 메시지를 표시 하지 않습니다. 서비스를 다시 시작하면 구성 변경 내용이 적용됩니다.

다시 시작하지 않고 다시 시작 프롬프트를 표시하지 않으려면 **NoServiceRestart** 매개 변수를 사용합니다.

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

### -Name

사용하도록 설정할 세션 구성의 이름을 지정합니다. 구성 이름을 하나 이상 입력합니다.
와일드카드 문자를 사용할 수 있습니다.

구성 이름이 나 세션 구성 개체를 포함 하는 문자열을로 파이프 할 수도 있습니다 `Enable-PSSessionConfiguration` .

이 매개 변수를 생략 하면에서 `Enable-PSSessionConfiguration` **Microsoft. PowerShell** 세션 구성을 사용 하도록 설정 합니다.

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

### -NoServiceRestart

Cmdlet에서 서비스를 다시 시작 하지 않음을 나타냅니다.

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

### -SecurityDescriptorSddl

이 cmdlet이 세션 구성에 대 한 보안 설명자를 대체 하는 보안 설명자를 지정 합니다.

이 매개 변수를 생략 하면는 `Enable-PSSessionConfiguration` 보안 설명자에서 모두 거부 항목만 삭제 합니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SkipNetworkProfileCheck

이 cmdlet은 컴퓨터가 공용 네트워크에 있을 때 세션 구성을 사용 하도록 지정 합니다. 이 매개 변수는 동일한 로컬 서브넷에 있는 컴퓨터의 원격 액세스만 허용하는 방화벽 규칙을 공용 네트워크에 사용하도록 설정합니다. 기본적으로는 `Enable-PSSessionConfiguration` 공용 네트워크에서 실패 합니다.

이 매개 변수는 Windows 운영 체제의 클라이언트 버전용으로 설계 되었습니다. 서버 버전의 Windows 운영 체제에는 공용 네트워크에 대 한 로컬 서브넷 방화벽 규칙이 있습니다. 그러나 서버 버전의 Windows 운영 체제에서 로컬 서브넷 방화벽 규칙을 사용 하지 않도록 설정한 경우이 매개 변수는 다시 사용 하도록 설정 합니다.

로컬 서브넷 제한을 제거 하 고 공용 네트워크의 모든 위치에서 원격 액세스를 사용 하도록 설정 하려면 `Set-NetFirewallRule` NetSecurity 모듈에서 cmdlet을 사용 합니다. 자세한 내용은 `Enable-PSRemoting`를 참조하세요.

이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.

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

### -WhatIf

cmdlet을 실행할 경우 발생하는 일을 표시합니다. cmdlet은 실행되지 않습니다.

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

### Microsoft. PowerShell. PSSessionConfigurationCommands # Register-pssessionconfiguration, System.string

세션 구성 개체 또는 세션 구성의 이름을 포함 하는 문자열을이 cmdlet으로 파이프 할 수 있습니다.

## 출력

### 없음

이 cmdlet은 개체를 반환하지 않습니다.

## 참고

이 cmdlet은 Windows 플랫폼 에서만 사용할 수 있습니다.

이 cmdlet을 사용 하려면 **관리자 권한으로 실행** 옵션을 사용 하 여 PowerShell을 시작 해야 합니다.

## 관련 링크

[Disable-PSSessionConfiguration](Disable-PSSessionConfiguration.md)

[Get-PSSessionConfiguration](Get-PSSessionConfiguration.md)

[New-PSSessionConfigurationFile](New-PSSessionConfigurationFile.md)

[New-PSSessionOption](New-PSSessionOption.md)

[Register-PSSessionConfiguration](Register-PSSessionConfiguration.md)

[Set-PSSessionConfiguration](Set-PSSessionConfiguration.md)

[Test-PSSessionConfigurationFile](Test-PSSessionConfigurationFile.md)

[Unregister-PSSessionConfiguration](Unregister-PSSessionConfiguration.md)

[WSMan 공급자](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[about_Session_Configurations](About/about_Session_Configurations.md)

[about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)
