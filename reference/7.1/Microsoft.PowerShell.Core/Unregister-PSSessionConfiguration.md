---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/unregister-pssessionconfiguration?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unregister-PSSessionConfiguration
ms.openlocfilehash: 0ee32b680aee940df36d3219e4b24ab594e79284
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94345819"
---
# Unregister-PSSessionConfiguration

## 개요
컴퓨터에서 등록된 세션 구성을 삭제합니다.

## SYNTAX

```
Unregister-PSSessionConfiguration [-Name] <String> [-Force] [-NoServiceRestart] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## 설명

`Unregister-PSSessionConfiguration`Cmdlet은 컴퓨터에서 등록 된 세션 구성을 삭제 합니다. 이 cmdlet은 시스템 관리자가 사용자에 대 한 사용자 지정 세션 구성을 관리 하도록 설계 되었습니다.

변경 내용을 적용 하려면에서 `Unregister-PSSessionConfiguration` **WinRM** 서비스를 다시 시작 합니다. 다시 시작을 방지 하려면 **NoServiceRestart** 매개 변수를 지정 합니다.

기본 **microsoft.powershell32** 세션 구성을 실수로 삭제 **Microsoft.PowerShell** 한 경우 cmdlet을 사용 `Enable-PSRemoting` 하 여 복원 합니다. 자세한 내용은 [about_Session_Configurations](About/about_Session_Configurations.md)를 참조 하세요.

## 예제

### 예 1: 세션 구성 삭제

이 예에서는 컴퓨터에서 **MaintenanceShell** 세션 구성을 삭제 합니다.

```powershell
Unregister-PSSessionConfiguration -Name "MaintenanceShell"
```

### 예 2: 세션 구성을 삭제 하 고 WinRM 서비스를 다시 시작 합니다.

이 예제에서는 **MaintenanceShell** 구성을 삭제 하 고 WinRM 서비스를 다시 시작 합니다. **Force** 매개 변수는 메시지를 표시 하지 않고 **WinRM** 서비스를 다시 시작 하는 모든 사용자 메시지를 표시 하지 않습니다.

```powershell
Unregister-PSSessionConfiguration -Name MaintenanceShell -Force
```

### 예 3: 모든 세션 구성 삭제

이 예에서는 컴퓨터의 모든 세션 구성을 삭제 하는 두 가지 방법을 보여 줍니다. 두 명령 모두 동일한 효과를 가지 며 서로 바꿔 사용할 수 있습니다.

```
Unregister-PSSessionConfiguration -Name *
Get-PSSessionConfiguration -Name * | Unregister-PSSessionConfiguration
```

### 예제 4: 다시 시작 하지 않고 등록 취소

이 예제에서는 **NoServiceRestart** 매개 변수를 사용 하 여 컴퓨터의 모든 세션이 중단 되는 서비스 다시 시작을 방지 하는 결과를 보여 줍니다.

```
PS> Unregister-PSSessionConfiguration -Name "MaintenanceShell" -NoServiceRestart
PS> Get-PSSessionConfiguration -Name "MaintenanceShell"

Get-PSSessionConfiguration -Name MaintenanceShell : No Session Configuration matches criteria "MaintenanceShell".
+ CategoryInfo          : NotSpecified: (:) [Write-Error], WriteErrorException
+ FullyQualifiedErrorId : Microsoft.PowerShell.Commands.WriteErrorException

PS> New-PSSession -ConfigurationName "MaintenanceShell"

Id Name      ComputerName    State    Configuration         Availability
-- ----      ------------    -----    -------------         ------------
1 Session1  localhost       Opened   MaintenanceShell      Available

PS> Restart-Service winrm
PS> New-PSSession -ConfigurationName MaintenanceShell

[localhost] Connecting to remote server failed with the following error message :
 The WS-Management service cannot process the request.
 The resource URI (http://schemas.microsoft.com/powershell/MaintenanceShell) was not found in the WS-Management catalog.
 The catalog contains the metadata that describes resources, or logical endpoints.
 For more information, see the about_Remote_Troubleshooting Help topic.
 + CategoryInfo          : OpenError: (System.Manageme....RemoteRunspace:RemoteRunspace) [], PSRemotingTransportException
 + FullyQualifiedErrorId : PSSessionOpenFailed
```

는 `Unregister-PSSessionConfiguration` **MaintenanceShell** 세션 구성을 삭제 합니다.
그러나이 명령은 **NoServiceRestart** 매개 변수를 사용 하므로 **WinRM** 서비스가 다시 시작 되지 않고 변경 내용이 아직 완전히 적용 되지 않습니다.

다음으로는 `Get-PSSessionConfiguration` **MaintenanceShell** 세션을 가져오려고 시도 합니다. WS-Management 리소스 테이블에서 세션이 제거 되었으므로에서 해당 세션을 `Get-PSSessionConfiguration` 반환할 수 없습니다.

`New-PSSession`Cmdlet은 **MaintenanceShell** 구성을 사용 하 여 세션을 만듭니다. 명령이 성공합니다. 다음으로, **WinRM** 서비스를 다시 시작 합니다.

마지막으로 `New-PSSession` cmdlet은 **MaintenanceShell** 구성을 사용 하는 세션을 만들려고 합니다. 이번에는 WinRM 서비스가 다시 시작 될 때 **MaintenanceShell** 구성이 삭제 되었으므로 세션이 실패 합니다.

## PARAMETERS

### -Force

Cmdlet에서 확인 메시지를 표시 하지 않고 **WinRM** 서비스를 다시 시작 하 라는 메시지를 표시 하지 않습니다. 서비스를 다시 시작하면 구성 변경 내용이 적용됩니다.

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

삭제할 세션 구성의 이름을 지정합니다. 세션 구성 이름 또는 구성 이름 패턴을 입력합니다. 와일드카드 문자를 사용할 수 있습니다. 이 매개 변수는 필수적 요소입니다.

세션 구성을로 파이프 할 수도 있습니다 `Unregister-PSSessionConfiguration` .

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -NoServiceRestart

이 cmdlet은 **WinRM** 서비스를 다시 시작 하지 않고 서비스를 다시 시작 하 라는 메시지를 표시 하지 않음을 나타냅니다.

기본적으로 명령을 실행 하면 `Unregister-PSSessionConfiguration` **WinRM** 서비스를 다시 시작 하 여 변경 내용을 적용 하 라는 메시지가 표시 됩니다. **WinRM** 서비스가 다시 시작 될 때까지 사용자는 아직 등록 되지 않은 세션 구성을 사용할 수 있습니다. 단,이를 찾지 못하는 경우에도 마찬가지 `Get-PSSessionConfiguration` 입니다.

메시지를 표시 하지 않고 **WinRM** 서비스를 다시 시작 하려면 **Force** 매개 변수를 지정 합니다. **WinRM** 서비스를 수동으로 다시 시작 하려면 cmdlet을 사용 합니다 `Restart-Service` .

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

### Microsoft. PowerShell. PSSessionConfigurationCommands # Register-pssessionconfiguration

세션 구성 개체를에서이 cmdlet으로 파이프 할 수 있습니다 `Get-PSSessionConfiguration` .

## 출력

### 없음

이 cmdlet은 개체를 반환하지 않습니다.

## 참고

이 cmdlet은 Windows 플랫폼 에서만 사용할 수 있습니다.

이 cmdlet을 실행 하려면 **관리자 권한으로 실행** 옵션을 사용 하 여 PowerShell을 시작 해야 합니다.

## 관련 링크

[Disable-PSSessionConfiguration](Disable-PSSessionConfiguration.md)

[Enable-PSSessionConfiguration](Enable-PSSessionConfiguration.md)

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
