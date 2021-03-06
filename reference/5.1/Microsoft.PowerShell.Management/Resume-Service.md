---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/resume-service?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Resume-Service
ms.openlocfilehash: 0902e944f2976bbdbc35fd051926422c5ae6f8c5
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94342640"
---
# Resume-Service

## 개요
하나 이상의 일시 중단(일시 중지)된 서비스를 다시 시작합니다.

## SYNTAX

### InputObject (기본값)

```
Resume-Service [-InputObject] <ServiceController[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### 기본값

```
Resume-Service [-Name] <String[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### DisplayName

```
Resume-Service [-PassThru] -DisplayName <String[]> [-Include <String[]>] [-Exclude <String[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## 설명

`Resume-Service`Cmdlet은 지정 된 각 서비스에 대 한 다시 시작 메시지를 Windows 서비스 컨트롤러로 보냅니다. 일시 중단 된 서비스는 다시 시작 됩니다. 현재 실행 중인 경우에는 메시지가 무시 됩니다. 서비스 이름 또는 표시 이름으로 서비스를 지정 하거나 **InputObject** 매개 변수를 사용 하 여 다시 시작할 서비스를 나타내는 서비스 개체를 전달할 수 있습니다.

## 예제

### 예 1: 로컬 컴퓨터에서 서비스를 다시 시작 합니다.

```
PS C:\> Resume-Service "sens"
```

이 명령은 로컬 컴퓨터에서 시스템 이벤트 알림 서비스를 다시 시작 합니다. 서비스 이름은 sens으로 명령에 표시 됩니다. 이 명령은 **name** 매개 변수를 사용 하 여 서비스의 서비스 이름을 지정 합니다. 그러나 매개 변수 이름은 선택 사항 이므로이 명령은 매개 변수 이름을 생략 합니다.

### 예제 2: 모든 일시 중단 된 서비스 다시 시작

```
PS C:\> Get-Service | Where-Object {$_.Status -eq "Paused"} | Resume-Service
```

이 명령은 컴퓨터에서 일시 중단 된 모든 서비스를 다시 시작 합니다. `Get-Service`Cmdlet 명령은 컴퓨터의 모든 서비스를 가져옵니다. 파이프라인 연산자 ( `|` )는 결과를 cmdlet으로 전달 합니다 `Where-Object` .이 Cmdlet은 **상태** 속성이 일시 중지 됨 인 서비스를 선택 합니다. 다음 파이프라인 연산자는 `Resume-Service` 일시 중지 된 서비스를 다시 시작 하는에 결과를 보냅니다.

실제로 **WhatIf** 매개 변수를 사용 하 여 명령 실행 전에 명령 효과를 확인 합니다.

## PARAMETERS

### -DisplayName

다시 시작할 서비스의 표시 이름을 지정합니다.
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

### -포함

다시 시작할 서비스를 지정 합니다. 이 매개 변수 값은 **Name** 매개 변수를 한정 합니다. 이름 요소 또는 패턴 (예: s *)을 입력 합니다. 와일드카드 문자를 사용할 수 있습니다.

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

다시 시작할 서비스를 나타내는 **ServiceController** 개체를 지정 합니다. 개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요.

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

다시 시작할 서비스의 서비스 이름을 지정합니다.

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases: ServiceName

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
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

이 cmdlet은 **PassThru** 매개 변수를 지정 하는 경우 다시 시작 된 서비스를 나타내는 **ServiceController** 개체를 생성 합니다. 그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.

## 참고

- 일시 중단 된 서비스의 상태가 일시 중지 됩니다. 서비스가 다시 시작 되 면 상태는 실행 중입니다.
- `Resume-Service` 현재 사용자에 게이 작업을 수행할 수 있는 권한이 있는 경우에만 서비스를 제어할 수 있습니다. 따라서 명령이 제대로 작동하지 않는 경우 필요한 권한이 없을 수 있습니다.
- 시스템에서 서비스의 서비스 이름 및 표시 이름을 찾으려면를 입력 `Get-Service` 합니다.
  서비스 이름은 **Name** 열에 나타나고 표시 이름은 **DisplayName** 열에 나타납니다.

## 관련 링크

[Get-Service](Get-Service.md)

[New-Service](New-Service.md)

[Restart-Service](Restart-Service.md)

[Set-Service](Set-Service.md)

[Start-Service](Start-Service.md)

[Stop-Service](Stop-Service.md)

[Suspend-Service](Suspend-Service.md)
