---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/disable-pssessionconfiguration?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSSessionConfiguration
ms.openlocfilehash: 9970c21748d49d258c1704f4a550d0a997a92af8
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94346618"
---
# Disable-PSSessionConfiguration

## 개요
로컬 컴퓨터의 세션 구성을 사용하지 않도록 설정합니다.

## SYNTAX

```
Disable-PSSessionConfiguration [[-Name] <String[]>] [-Force] [-NoServiceRestart] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## 설명

`Disable-PSSessionConfiguration`Cmdlet은 로컬 컴퓨터에서 세션 구성을 사용 하지 않도록 설정 하므로 모든 사용자가 세션 구성을 사용 하 여 로컬 컴퓨터에 사용자 관리 세션 ( **PSSessions** pssession)을 만들 수 없습니다. 이 cmdlet은 시스템 관리자가 사용자에 대한 사용자 지정 세션을 관리하는 데 사용할 수 있는 고급 cmdlet입니다.

PowerShell 3.0부터 `Disable-PSSessionConfiguration` cmdlet은 세션 구성의 설정 **Enabled** 된 설정 ()을 `WSMan:\localhost\Plugins\<SessionConfiguration>\Enabled` False로 설정 합니다.

PowerShell 2.0에서 cmdlet은 `Disable-PSSessionConfiguration` 하나 이상의 등록 된 세션 구성의 보안 설명자에 **Deny_All** 항목을 추가 합니다.

매개 변수가 없으면 `Disable-PSSessionConfiguration` 세션에 사용 되는 기본 구성 인 **Microsoft. PowerShell** 구성을 사용 하지 않도록 설정 합니다. 사용자가 다른 구성을 지정하지 않으면 로컬 및 원격 사용자 모두 컴퓨터에 연결되는 세션을 효과적으로 만들 수 없습니다.

컴퓨터의 모든 세션 구성을 사용 하지 않도록 설정 하려면를 사용 `Disable-PSRemoting` 합니다.

## 예제

### 예 1: 기본 구성을 사용 하지 않도록 설정

이 예제에서는 Microsoft. PowerShell 세션 구성을 사용 하지 않도록 설정 합니다.

```powershell
Disable-PSSessionConfiguration
```

### 예 2: 등록 된 모든 세션 구성을 사용 하지 않도록 설정

이 예에서는 컴퓨터에 등록 된 모든 세션 구성을 사용 하지 않도록 설정 합니다.

```powershell
Disable-PSSessionConfiguration -Name *
```

### 예제 3: 이름으로 세션 구성 비활성화

이 예에서는 이름이 Microsoft로 시작 하는 모든 세션 구성을 사용 하지 않도록 설정 합니다. **Force** 매개 변수는 cmdlet에서 모든 사용자 프롬프트를 표시 하지 않습니다.

```powershell
Disable-PSSessionConfiguration -Name Microsoft* -Force
```

### 예제 4: 파이프라인을 사용 하 여 세션 구성 비활성화

이 예에서는 **MaintenanceShell** 및 **adminshell** 세션 구성을 사용 하지 않도록 설정 합니다. 파이프라인 연산자 (|)가의 결과를로 보냅니다 `Get-PSSessionConfiguration` `Disable-PSSessionConfiguration` .

```powershell
Get-PSSessionConfiguration -Name MaintenanceShell, AdminShell | Disable-PSSessionConfiguration
```

### 예 5: 세션 구성을 사용 하지 않도록 설정 하는 효과

이 예에서는 실행 전후 사용 권한과 `Disable-PSSessionConfiguration` 세션 구성을 사용 하지 않도록 설정 하는 효과를 보여 줍니다.

```
PS> Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto

Name                   Permission
----                   ----------
MaintenanceShell       BUILTIN\Administrators AccessAllowed
microsoft.powershell   BUILTIN\Administrators AccessAllowed
microsoft.powershell32 BUILTIN\Administrators AccessAllowed

PS> Disable-PSSessionConfiguration -Name MaintenanceShell -Force
PS> Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto

Name                   Permission
----                   ----------
MaintenanceShell       Everyone AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.powershell   BUILTIN\Administrators AccessAllowed
microsoft.powershell32 BUILTIN\Administrators AccessAllowed

PS> New-PSSession -ComputerName localhost -ConfigurationName MaintenanceShell

[localhost] Connecting to remote server failed with the following error message : Access is denied.
For more information, see the about_Remote_Troubleshooting Help topic.
+ CategoryInfo          : OpenError: (System.Manageme....RemoteRunspace:RemoteRunspace) [], PSRemotingTransportException
+ FullyQualifiedErrorId : PSSessionOpenFailed
```

> [!NOTE]
> 구성을 사용 하지 않도록 설정 해도 cmdlet을 사용 하 여 구성을 변경할 수 있습니다 `Set-PSSessionConfiguration` . 구성을 사용할 수 없습니다.

## PARAMETERS

### -Force

사용자 확인을 요청하지 않고 명령을 강제 실행합니다.

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

사용 하지 않도록 설정할 세션 구성의 이름 배열을 지정 합니다. 구성 이름을 하나 이상 입력합니다. 와일드카드 문자를 사용할 수 있습니다. 구성 이름이 나 세션 구성 개체를 포함 하는 문자열을로 파이프 할 수도 있습니다 `Disable-PSSessionConfiguration` .

이 매개 변수를 생략 하면에서 `Disable-PSSessionConfiguration` Microsoft. PowerShell 세션 구성을 사용 하지 않도록 설정 합니다.

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

WSMan 서비스의 다시 시작을 방지 하는 데 사용 됩니다. 구성을 사용 하지 않도록 설정 하기 위해 서비스를 다시 시작할 필요는 없습니다.

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

이 cmdlet을 실행 하려면 **관리자 권한으로 실행** 옵션을 사용 하 여 PowerShell을 시작 해야 합니다.

## 관련 링크

[Enable-PSSessionConfiguration](Enable-PSSessionConfiguration.md)

[Get-PSSessionConfiguration](Get-PSSessionConfiguration.md)

[New-PSSessionConfigurationFile](New-PSSessionConfigurationFile.md)

[Register-PSSessionConfiguration](Register-PSSessionConfiguration.md)

[Set-PSSessionConfiguration](Set-PSSessionConfiguration.md)

[Test-PSSessionConfigurationFile](Test-PSSessionConfigurationFile.md)

[Unregister-PSSessionConfiguration](Unregister-PSSessionConfiguration.md)

[WSMan 공급자](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[about_Session_Configurations](About/about_Session_Configurations.md)

[about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)
