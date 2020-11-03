---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/suspend-service?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Suspend-Service
ms.openlocfilehash: 8455592f6b919da04603470262c134593f74877c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93212185"
---
# Suspend-Service

## 개요
실행 중인 하나 이상의 서비스를 일시 중단(일시 중지)합니다.

## SYNTAX

### InputObject (기본값)

```
Suspend-Service [-InputObject] <ServiceController[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### 기본값

```
Suspend-Service [-Name] <String[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### DisplayName

```
Suspend-Service [-PassThru] -DisplayName <String[]> [-Include <String[]>] [-Exclude <String[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## 설명

**Suspend-service** cmdlet은 지정 된 각 서비스에 대 한 일시 중단 메시지를 Windows 서비스 컨트롤러로 보냅니다.
일시 중단 된 동안 서비스는 계속 실행 되지만 사용 Resume-Service cmdlet 등의 작업은 다시 시작할 때까지 중지 됩니다.
서비스 이름 또는 표시 이름으로 서비스를 지정 하거나 *InputObject* 매개 변수를 사용 하 여 일시 중단할 서비스를 나타내는 서비스 개체를 전달할 수 있습니다.

## 예제

### 예제 1: 서비스 일시 중단

```
PS C:\> Suspend-Service -DisplayName "Telnet"
```

이 명령은 로컬 컴퓨터의 텔넷 서비스(Tlntsvr)를 일시 중단합니다.

### 예 2: 서비스를 일시 중단할 경우 발생 하는 상황 표시

```
PS C:\> Suspend-Service -Name lanman* -WhatIf
```

이 명령은 서비스 이름이 lanman로 시작 하는 서비스를 일시 중지 한 경우 발생 하는 상황을 알려 줍니다.
서비스를 일시 중단 하려면 *WhatIf* 매개 변수 없이 명령을 다시 실행 합니다.

### 예제 3: 서비스 가져오기 및 일시 중단

```
PS C:\> Get-Service schedule | Suspend-Service
```

이 명령은 **get-help** cmdlet을 사용 하 여 컴퓨터의 작업 스케줄러 (Schedule) 서비스를 나타내는 개체를 가져옵니다.
파이프라인 연산자 (|)가 결과를 **일시 중단 서비스** 에 전달 하 여 서비스를 일시 중단 합니다.

### 예제 4: 일시 중단할 수 있는 모든 서비스 일시 중단

```
PS C:\> Get-Service | Where-Object {$_.CanPauseAndContinue -eq "True"} | Suspend-Service -Confirm
```

이 명령은 일시 중단할 수 있는 컴퓨터의 모든 서비스를 일시 중단합니다.
**서비스** 를 사용 하 여 컴퓨터의 서비스를 나타내는 개체를 가져옵니다.
파이프라인 연산자는 결과를 Where-Object cmdlet으로 전달 합니다 .이 cmdlet은 **Canpauseandcontinue** 속성의 $True 값이 있는 서비스만 선택 합니다.
다른 파이프라인 연산자가 결과를 **일시 중단 서비스** 에 전달 합니다.
*Confirm* 매개 변수는 각 서비스를 일시 중단 하기 전에 확인 메시지를 표시 합니다.

## PARAMETERS

### -DisplayName

일시 중단할 서비스의 표시 이름을 지정합니다.
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

지정 된 서비스에서 생략 하는 서비스를 지정 합니다.
이 매개 변수 값은 *Name* 매개 변수를 한정 합니다.
이름 요소 또는 패턴(예: "*s*")을 입력합니다.
와일드카드 문자를 사용할 수 있습니다.

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

### -포함

일시 중단할 서비스를 지정 합니다.
이 매개 변수 값은 *Name* 매개 변수를 한정 합니다.
이름 요소 또는 패턴(예: "*s*")을 입력합니다.
와일드카드 문자를 사용할 수 있습니다.

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

일시 중단할 서비스를 나타내는 **ServiceController** 개체를 지정 합니다.
개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요.

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

일시 중단할 서비스의 서비스 이름을 지정 합니다.
와일드카드 문자를 사용할 수 있습니다.

매개 변수 이름은 선택 사항입니다.
*이름* 또는 별칭, *ServiceName* 을 사용 하거나 매개 변수 이름을 생략할 수 있습니다.

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

### -PassThru

작업 중인 항목을 나타내는 개체를 반환합니다.
기본적으로 이 cmdlet은 출력을 생성하지 않습니다.

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

### ServiceController, System.string입니다.

서비스 개체 또는 서비스 이름이 포함 된 문자열을이 cmdlet으로 파이프 할 수 있습니다.

## 출력

### None, ServiceController

이 cmdlet은 *PassThru* 매개 변수를 지정 하는 경우 서비스를 나타내는 **ServiceController** 개체를 생성 합니다.
그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.

## 참고

* **일시 중단-** 현재 사용자에 게이 작업을 수행할 수 있는 권한이 있는 경우에만 서비스를 제어할 수 있습니다. 따라서 명령이 제대로 작동하지 않는 경우 필요한 권한이 없을 수 있습니다.
* **일시 중단-서비스** 는 일시 중단 및 다시 시작을 지 원하는 서비스만 일시 중단할 수 있습니다. 특정 서비스를 일시 중단할 수 있는지 확인 하려면 **Canpauseandcontinue** 속성과 함께 Get-Service cmdlet을 사용 합니다. 예들 들어 `Get-Service wmi | Format-List Name, CanPauseAndContinue`입니다. 일시 중단할 수 있는 컴퓨터의 모든 서비스를 찾으려면를 입력 `Get-Service | Where-Object {$_.CanPauseAndContinue -eq $true}` 합니다.
* 시스템에서 서비스의 서비스 이름 및 표시 이름을 찾으려면 **get-help** 를 입력 합니다. 서비스 이름은 **Name** 열에 나타나고 표시 이름은 **DisplayName** 열에 나타납니다.

## 관련 링크

[Get-Service](Get-Service.md)

[New-Service](New-Service.md)

[Restart-Service](Restart-Service.md)

[Resume-Service](Resume-Service.md)

[Set-Service](Set-Service.md)

[Start-Service](Start-Service.md)

[Stop-Service](Stop-Service.md)

[Remove-Service](Remove-Service.md)

