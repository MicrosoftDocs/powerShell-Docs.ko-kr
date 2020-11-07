---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/stop-service?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Service
ms.openlocfilehash: ed62e60e18594624c4c7aa940cc90bd09a1aa83c
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94345071"
---
# Stop-Service

## 개요
실행 중인 하나 이상의 서비스를 중지합니다.

## SYNTAX

### InputObject (기본값)

```
Stop-Service [-Force] [-NoWait] [-InputObject] <ServiceController[]> [-PassThru] [-Include <String[]>]
 [-Exclude <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### 기본값

```
Stop-Service [-Force] [-NoWait] [-Name] <String[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### DisplayName

```
Stop-Service [-Force] [-NoWait] [-PassThru] -DisplayName <String[]> [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명

`Stop-Service`Cmdlet은 지정 된 각 서비스에 대 한 중지 메시지를 Windows 서비스 컨트롤러로 보냅니다. 서비스 이름 또는 표시 이름으로 서비스를 지정 하거나 **InputObject** 매개 변수를 사용 하 여 중지할 서비스를 나타내는 서비스 개체를 전달할 수 있습니다.

## 예제

### 예 1: 로컬 컴퓨터에서 서비스 중지

```
PS C:\> Stop-Service -Name "sysmonlog"
```

이 명령은 로컬 컴퓨터의 성능 로그 및 알림(SysmonLog) 서비스를 중지합니다.

### 예 2: 표시 이름을 사용 하 여 서비스 중지

```
PS C:\> Get-Service -DisplayName "telnet" | Stop-Service
```

이 명령은 로컬 컴퓨터의 텔넷 서비스를 중지합니다. 명령은를 사용 `Get-Service` 하 여 텔넷 서비스를 나타내는 개체를 가져옵니다. 파이프라인 연산자 ( `|` )는 개체를로 파이프 하 여 `Stop-Service` 서비스를 중지 합니다.

### 예 3: 종속 서비스를 포함 하는 서비스 중지

```
PS C:\> Get-Service -Name "iisadmin" | Format-List -Property Name, DependentServices
PS C:\> Stop-Service -Name "iisadmin" -Force -Confirm
```

이 예에서는 로컬 컴퓨터의 IISAdmin 서비스를 중지 합니다. 이 서비스를 중지 하면 IISAdmin 서비스에 종속 된 서비스도 중지 되므로 `Stop-Service` iisadmin 서비스에 종속 된 서비스를 나열 하는 명령 앞에를 사용 하는 것이 가장 좋습니다.

첫 번째 명령은 IISAdmin에 종속된 서비스를 나열합니다. 을 사용 `Get-Service` 하 여 IISAdmin 서비스를 나타내는 개체를 가져옵니다. 파이프라인 연산자 ( `|` )는 결과를 cmdlet으로 전달 합니다 `Format-List` . 이 명령은의 **Property** 매개 변수를 사용 하 여 `Format-List` 서비스의 **Name** 및 **DependentServices** 속성만 나열 합니다.

두 번째 명령은 IISAdmin 서비스를 중지합니다. **Force** 매개 변수는 종속 서비스가 있는 서비스를 중지 하는 데 필요 합니다. 이 명령은 **Confirm** 매개 변수를 사용 하 여 각 서비스를 중지 하기 전에 사용자의 확인을 요청 합니다.

## PARAMETERS

### -DisplayName

중지할 서비스의 표시 이름을 지정 합니다.
와일드카드 문자를 사용할 수 있습니다.

```yaml
Type: System.String[]
Parameter Sets: DisplayName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -제외

이 cmdlet이 생략 하는 서비스를 지정 합니다. 이 매개 변수 값은 **Name** 매개 변수를 한정 합니다. 이름 요소 또는 패턴 (예: s *)을 입력 합니다. 와일드카드 문자를 사용할 수 있습니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Force

서비스가 종속 된 서비스를 포함 하는 경우에도 cmdlet이 서비스를 중지 하도록 합니다.

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

### -포함

이 cmdlet이 중지 하는 서비스를 지정 합니다. 이 매개 변수 값은 **Name** 매개 변수를 한정 합니다. 이름 요소 또는 패턴 (예: s *)을 입력 합니다. 와일드카드 문자를 사용할 수 있습니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -InputObject

중지할 서비스를 나타내는 **ServiceController** 개체를 지정 합니다. 개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요.

```yaml
Type: System.ServiceProcess.ServiceController[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name

중지할 서비스의 서비스 이름을 지정 합니다. 와일드카드 문자를 사용할 수 있습니다.

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases: ServiceName

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -NoWait

이 cmdlet이 대기 안 함 옵션을 사용 함을 나타냅니다.

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

### -PassThru

서비스를 나타내는 개체를 반환합니다. 기본적으로 이 cmdlet은 출력을 생성하지 않습니다.

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

### ServiceController, System.string입니다.

서비스 개체 또는 서비스 이름이 포함 된 문자열을이 cmdlet으로 파이프 할 수 있습니다.

## 출력

### None, ServiceController

이 cmdlet은 **PassThru** 매개 변수를 사용 하는 경우 서비스를 나타내는 **ServiceController** 개체를 생성 합니다. 그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.

## 참고

이 cmdlet은 Windows 플랫폼 에서만 사용할 수 있습니다.

`Stop-Service`기본 제공 별칭인 **spsv** 로 참조할 수도 있습니다. 자세한 내용은 about_Aliases를 참조하세요.

`Stop-Service` 현재 사용자에 게이 작업을 수행할 수 있는 권한이 있는 경우에만 서비스를 제어할 수 있습니다. 따라서 명령이 제대로 작동하지 않는 경우 필요한 권한이 없을 수 있습니다.

시스템에서 서비스의 서비스 이름 및 표시 이름을 찾으려면를 입력 `Get-Service` 합니다. 서비스 이름은 **Name** 열에 나타나고 표시 이름은 **DisplayName** 열에 나타납니다.

## 관련 링크

[Get-Service](Get-Service.md)

[New-Service](New-Service.md)

[Restart-Service](Restart-Service.md)

[Resume-Service](Resume-Service.md)

[Set-Service](Set-Service.md)

[Start-Service](Start-Service.md)

[Suspend-Service](Suspend-Service.md)

[Remove-Service](Remove-Service.md)
