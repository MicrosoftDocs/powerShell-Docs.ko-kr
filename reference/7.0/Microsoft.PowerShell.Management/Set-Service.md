---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/25/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-service?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Service
ms.openlocfilehash: d58d26a93e9b785bcba425537ea570feeffa1606
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93210625"
---
# Set-Service

## 개요
서비스를 시작, 중지 및 일시 중단하고 해당 속성을 변경합니다.

## SYNTAX

### 이름 (기본값)

```
Set-Service [-Name] <String> [-DisplayName <String>] [-Credential <PSCredential>]
 [-Description <String>] [-StartupType <ServiceStartupType>] [-Status <String>]
 [-SecurityDescriptorSddl <String>] [-Force] [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InputObject

```
Set-Service [-InputObject] <ServiceController> [-DisplayName <String>] [-Credential <PSCredential>]
 [-Description <String>] [-StartupType <ServiceStartupType>] [-SecurityDescriptorSddl <String>]
 [-Status <String>] [-Force] [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명

`Set-Service`Cmdlet은 **상태** , **설명** , **DisplayName** , **startuptype** 등의 서비스 속성을 변경 합니다. `Set-Service` 서비스를 시작, 중지, 일시 중지 또는 일시 중지할 수 있습니다. 서비스를 식별 하려면 해당 서비스 이름을 입력 하거나 서비스 개체를 제출 합니다. 또는 파이프라인에서 서비스 이름 또는 서비스 개체를로 보냅니다 `Set-Service` .

## 예제

### 예제 1: 표시 이름 변경

이 예제에서는 서비스의 표시 이름이 변경 됩니다. 원래 표시 이름을 보려면를 사용 `Get-Service` 합니다.

```powershell
Set-Service -Name LanmanWorkstation -DisplayName "LanMan Workstation"
```

`Set-Service`**name** 매개 변수를 사용 하 여 서비스의 이름인 **LanmanWorkstation** 를 지정 합니다. **DisplayName** 매개 변수는 새 표시 이름인 **LanMan Workstation** 을 지정 합니다.

### 예 2: 서비스의 시작 유형 변경

이 예제에서는 서비스의 시작 유형을 변경 하는 방법을 보여 줍니다.

```powershell
Set-Service -Name BITS -StartupType Automatic
Get-Service BITS | Select-Object -Property Name, StartType, Status
```

```Output
Name  StartType   Status
----  ---------   ------
BITS  Automatic  Running
```

`Set-Service`**name** 매개 변수를 사용 하 여 서비스의 이름 ( **비트** )을 지정 합니다. **Startuptype** 매개 변수는 서비스를 **자동** 으로 설정 합니다.

`Get-Service`**Name** 매개 변수를 사용 하 여 **BITS** 서비스를 지정 하 고 개체를 파이프라인으로 보냅니다. `Select-Object`**Property** 매개 변수를 사용 하 여 **BITS** 서비스의 상태를 표시 합니다.

### 예 3: 서비스에 대 한 설명 변경

이 예에서는 BITS 서비스의 설명을 변경 하 고 결과를 표시 합니다.

`Get-CimInstance`Cmdlet은 서비스의 **설명을** 포함 하는 **Win32_Service** 개체를 반환 하기 때문에 사용 됩니다.

```powershell
Get-CimInstance Win32_Service -Filter 'Name = "BITS"'  | Format-List  Name, Description
```

```Output
Name        : BITS
Description : Transfers files in the background using idle network bandwidth. If the service is
              disabled, then any applications that depend on BITS, such as Windows Update or MSN
              Explorer, will be unable to automatically download programs and other information.
```

```powershell
Set-Service -Name BITS -Description "Transfers files in the background using idle network bandwidth."
Get-CimInstance Win32_Service -Filter 'Name = "BITS"' | Format-List  Name, Description
```

```Output
Name        : BITS
Description : Transfers files in the background using idle network bandwidth.
```

`Get-CimInstance` 개체를 파이프라인에서 아래로 보내고 `Format-List` 서비스의 이름과 설명을 표시 합니다. 비교를 위해이 명령은 설명이 업데이트 되기 전후에 실행 됩니다.

`Set-Service`**Name** 매개 변수를 사용 하 여 **BITS** 서비스를 지정 합니다. **Description** 매개 변수는 서비스 설명에 대 한 업데이트 된 텍스트를 지정 합니다.

### 예제 4: 서비스 시작

이 예제에서는 서비스가 시작 됩니다.

```powershell
Set-Service -Name WinRM -Status Running -PassThru
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  WinRM              Windows Remote Management (WS-Manag...
```

`Set-Service`**Name** 매개 변수를 사용 하 여 **WinRM** 서비스를 지정 합니다. **Status** 매개 변수는 **실행** 값을 사용 하 여 서비스를 시작 합니다. **PassThru** 매개 변수는 결과를 표시 하는 **ServiceController** 개체를 출력 합니다.

### 예 5: 서비스 일시 중단

이 예제에서는 파이프라인을 사용 하 여 서비스를 일시 중지 합니다.

```powershell
Get-Service -Name Schedule | Set-Service -Status Paused
```

`Get-Service`**Name** 매개 변수를 사용 하 여 **일정** 서비스를 지정 하 고 개체를 파이프라인으로 보냅니다. `Set-Service`**Status** 매개 변수를 사용 하 여 서비스를 **일시 중지 됨으로** 설정 합니다.

### 예 6: 서비스 중지

이 예에서는 변수를 사용 하 여 서비스를 중지 합니다.

```powershell
$S = Get-Service -Name Schedule
Set-Service -InputObject $S -Status Stopped
```

`Get-Service`**Name** 매개 변수를 사용 하 여 서비스, **예약** 을 지정 합니다. 개체는 변수에 저장 됩니다 `$S` . `Set-Service`**InputObject** 매개 변수를 사용 하 고 저장 된 개체를 지정 합니다 `$S` . **상태** 매개 변수는 서비스를 **중지 됨** 으로 설정 합니다.

### 예 7: 원격 시스템에서 서비스 중지

이 예제에서는 원격 컴퓨터에서 서비스를 중지 합니다.
자세한 내용은 [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md)를 참조 하세요.

```powershell
$Cred = Get-Credential
$S = Get-Service -Name Schedule
Invoke-Command -ComputerName server01.contoso.com -Credential $Cred -ScriptBlock {
  Set-Service -InputObject $S -Status Stopped
}
```

`Get-Credential` 사용자 이름 및 암호를 묻는 메시지를 표시 하 고 변수에 자격 증명을 저장 `$Cred` 합니다. `Get-Service`**Name** 매개 변수를 사용 하 여 **일정** 서비스를 지정 합니다. 개체는 변수에 저장 됩니다 `$S` .

`Invoke-Command`**ComputerName** 매개 변수를 사용 하 여 원격 컴퓨터를 지정 합니다. **Credential** 매개 변수는 변수를 사용 하 여 컴퓨터에 로그온 `$Cred` 합니다. **ScriptBlock** 은를 호출 `Set-Service` 합니다. **InputObject** 매개 변수는 저장 된 서비스 개체를 지정 합니다 `$S` . **상태** 매개 변수는 서비스를 **중지 됨** 으로 설정 합니다.

### 예 8: 서비스의 자격 증명 변경

이 예에서는 서비스를 관리 하는 데 사용 되는 자격 증명을 변경 합니다.

```powershell
$credential = Get-Credential
Set-Service -Name Schedule -Credential $credential
```

`Get-Credential` 사용자 이름 및 암호를 묻는 메시지를 표시 하 고 변수에 자격 증명을 저장 `$credential` 합니다. `Set-Service`**Name** 매개 변수를 사용 하 여 **일정** 서비스를 지정 합니다. **Credential** 매개 변수는 변수를 사용 하 `$credential` 고 **일정** 서비스를 업데이트 합니다.

### 예 9: 서비스의 SecurityDescriptor 변경

이 예에서는 서비스의 **SecurityDescriptor** 를 변경 합니다.

```powershell
$SDDL = "D:(A;;CCLCSWRPWPDTLOCRRC;;;SY)(A;;CCDCLCSWRPWPDTLOCRSDRCWDWO;;;BA)(A;;CCLCSWLOCRRC;;;SU)"
Set-Service -Name "BITS" -SecurityDescriptorSddl $SDDL
```

**SecurityDescriptor** 은 변수에 저장 됩니다 `$SDDL` . `Set-Service`**Name** 매개 변수를 사용 하 여 **BITS** 서비스를 지정 합니다. **SecurityDescriptorSddl** 매개 변수는 `$SDDL` 를 사용 하 여 **BITS** 서비스의 **SecurityDescriptor** 을 변경 합니다.

## PARAMETERS

### -Confirm

실행 하기 전에 확인 메시지를 표시 `Set-Service` 합니다.

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

### -Credential

서비스에서 [서비스 로그온 계정](/windows/desktop/ad/about-service-logon-accounts)으로 사용 하는 계정을 지정 합니다.

**User01** 또는 **Domain01\User01** 과 같은 사용자 이름을 입력 하거나, cmdlet에 의해 생성 된 것과 같은 **PSCredential** 개체를 입력 합니다 `Get-Credential` . 사용자 이름을 입력 하는 경우이 cmdlet은 암호를 묻는 메시지를 표시 합니다.

자격 증명은 [PSCredential](/dotnet/api/system.management.automation.pscredential) 개체에 저장 되 고 암호는 [SecureString](/dotnet/api/system.security.securestring)으로 저장 됩니다.

> [!NOTE]
> **Securestring** 데이터 보호에 대 한 자세한 [내용은 참조 하십시오](/dotnet/api/system.security.securestring#how-secure-is-securestring).

이 매개 변수는 PowerShell 6.0에서 도입 되었습니다.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Description

서비스에 대한 새 설명을 지정합니다.

서비스 설명은 **컴퓨터 관리, 서비스** 에 표시 됩니다. **설명은** `Get-Service` **ServiceController** 개체의 속성이 아닙니다. 서비스 설명을 보려면 `Get-CimInstance` 서비스를 나타내는 **Win32_Service** 개체를 반환 하는를 사용 합니다.

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

### -DisplayName

서비스의 새 표시 이름을 지정합니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: DN

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

서비스의 중지 모드를 지정 합니다. 이 매개 변수는가 사용 되는 경우에만 작동 `-Status Stopped` 합니다. 사용 하도록 설정 하면 `Set-Service` 대상 서비스가 중지 되기 전에 종속 서비스를 중지 합니다. 기본적으로 실행 중인 다른 서비스가 대상 서비스에 종속 되는 경우 예외가 발생 합니다.

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

### -InputObject

변경할 서비스를 나타내는 **ServiceController** 개체를 지정 합니다. 개체를 포함 하는 변수를 입력 하거나 개체를 가져오는 명령 또는 식 (예: 명령)을 입력 합니다 `Get-Service` . 파이프라인을 사용 하 여 서비스 개체를로 보낼 수 있습니다 `Set-Service` .

```yaml
Type: System.ServiceProcess.ServiceController
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name

변경할 서비스의 서비스 이름을 지정합니다. 와일드 카드 문자는 허용 되지 않습니다. 파이프라인을 사용 하 여 서비스 이름을로 보낼 수 있습니다 `Set-Service` .

```yaml
Type: System.String
Parameter Sets: Name
Aliases: ServiceName, SN

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -PassThru

변경 된 서비스를 나타내는 **ServiceController** 개체를 반환 합니다. 기본적으로는 `Set-Service` 출력을 생성 하지 않습니다.

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

### -StartupType

서비스의 시작 모드를 지정합니다.

이 매개 변수에 허용 되는 값은 다음과 같습니다.

- **자동** -시스템이 시작 되거나 운영 체제에서 서비스를 시작 합니다.
  자동으로 시작된 서비스가 수동으로 시작된 서비스에 따라 달라지는 경우, 시스템 시작 시 수동으로 시작된 서비스도 자동으로 시작됩니다.
- 자동 **Delayedstart** -시스템이 부팅 된 후 바로 시작 됩니다.
- **사용 안 함** -서비스를 사용할 수 없으며 사용자 또는 응용 프로그램에서 시작할 수 없습니다.
- **Invalidvalue** -적용 되지 않습니다. 이 cmdlet은 오류를 반환 하지 않지만 서비스의 StartupType은 변경 되지 않습니다.
- **수동** -서비스 제어 관리자 또는 응용 프로그램을 사용 하 여 수동으로 또는 사용자가 서비스를 시작 합니다.

```yaml
Type: Microsoft.PowerShell.Commands.ServiceStartupType
Parameter Sets: (All)
Aliases: StartMode, SM, ST, StartType
Accepted values: Automatic, AutomaticDelayedStart, Disabled, InvalidValue, Manual

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -상태

서비스의 상태를 지정 합니다.

이 매개 변수에 허용 되는 값은 다음과 같습니다.

- **일시 중지 됨** . 서비스를 일시 중단합니다.
- **실행 중** . 서비스를 시작합니다.
- **중지 됨** . 서비스를 중지합니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Paused, Running, Stopped

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SecurityDescriptorSddl

**Sddl** 형식으로 서비스에 대 한 **SecurityDescriptor** 를 지정 합니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: sd

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

가 실행 될 경우 발생 하는 상황을 보여 줍니다 `Set-Service` . Cmdlet이 실행 되지 않습니다.

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

### ServiceController, System.string입니다.

파이프라인을 사용 하 여 서비스 개체 또는 서비스 이름이 포함 된 문자열을로 보낼 수 있습니다 `Set-Service` .

## 출력

### System.ServiceProcess.ServiceController

기본적으로는 `Set-Service` 개체를 반환 하지 않습니다. **PassThru** 매개 변수를 사용 하 여 **ServiceController** 개체를 출력 합니다.

## 참고

`Set-Service` 높은 권한이 필요 합니다. **관리자 권한으로 실행** 옵션을 사용 합니다.

`Set-Service` 현재 사용자에 게 서비스를 관리할 수 있는 권한이 있는 경우에만 서비스를 제어할 수 있습니다. 명령이 제대로 작동 하지 않는 경우 필요한 권한이 없을 수 있습니다.

서비스의 서비스 이름 또는 표시 이름을 찾으려면를 사용 `Get-Service` 합니다. 서비스 이름은 **Name** 열에 있고 표시 이름은 **DisplayName** 열에 있습니다.

## 관련 링크

[Get-Service](Get-Service.md)

[New-Service](New-Service.md)

[Restart-Service](Restart-Service.md)

[Resume-Service](Resume-Service.md)

[Start-Service](Start-Service.md)

[Stop-Service](Stop-Service.md)

[Suspend-Service](Suspend-Service.md)

[Remove-Service](Remove-Service.md)
