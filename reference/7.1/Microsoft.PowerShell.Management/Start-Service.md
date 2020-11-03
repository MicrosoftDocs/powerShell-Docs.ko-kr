---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/start-service?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Service
ms.openlocfilehash: 71b9ac57b2ab27e26f3a7454662f231b6e1dd764
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93216169"
---
# Start-Service

## 개요
하나 이상의 중지된 서비스를 시작합니다.

## SYNTAX

### InputObject (기본값)

```
Start-Service [-InputObject] <ServiceController[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### 기본값

```
Start-Service [-Name] <String[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### DisplayName

```
Start-Service [-PassThru] -DisplayName <String[]> [-Include <String[]>] [-Exclude <String[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## 설명

`Start-Service`Cmdlet은 지정 된 각 서비스에 대 한 시작 메시지를 Windows 서비스 컨트롤러로 보냅니다. 서비스가 이미 실행 중인 경우에는 오류 없이 메시지가 무시됩니다. 서비스 이름 또는 표시 이름으로 서비스를 지정 하거나 **InputObject** 매개 변수를 사용 하 여 시작 하려는 서비스를 나타내는 서비스 개체를 제공할 수 있습니다.

## 예제

### 예제 1: 이름을 사용 하 여 서비스 시작

이 예에서는 로컬 컴퓨터에서 EventLog 서비스를 시작 합니다. **Name** 매개 변수는 서비스 이름으로 서비스를 식별 합니다.

```powershell
Start-Service -Name "eventlog"
```

### 예제 2: 서비스를 시작 하지 않고 정보 표시

이 예에서는 "remote"를 포함 하는 표시 이름이 있는 서비스를 시작한 경우 발생 하는 상황을 보여 줍니다.

```powershell
Start-Service -DisplayName *remote* -WhatIf
```

**DisplayName** 매개 변수는 서비스 이름 대신 표시 이름으로 서비스를 식별 합니다. **WhatIf** 매개 변수를 사용 하면 cmdlet에서 명령을 실행할 때 발생 하는 작업을 표시 하지만 변경 하지는 않습니다.

### 예 3: 서비스를 시작 하 고 텍스트 파일에 작업 기록

이 예에서는 컴퓨터에서 WMI (WMI(Windows Management Instrumentation)) 서비스를 시작 하 고 services.txt 파일에 작업 레코드를 추가 합니다.

```powershell
$s = Get-Service wmi
Start-Service -InputObject $s -PassThru | Format-List >> services.txt
```

먼저를 사용 `Get-Service` 하 여 WMI 서비스를 나타내는 개체를 가져온 다음 `$s` 변수에 저장 합니다. 다음으로 서비스를 시작 합니다. **PassThru** 매개 변수를 사용 하지 않으면에서 `Start-Service` 출력을 생성 하지 않습니다. 파이프라인 연산자 (|)는 개체 출력을 `Start-Service` cmdlet에 전달 `Format-List` 하 여 개체를 속성 목록으로 지정 합니다. 추가 리디렉션 연산자 ( \> \> )는 출력을 services.txt 파일로 리디렉션합니다. 출력은 기존 파일의 끝에 추가 됩니다.

### 예제 4: 비활성화 된 서비스 시작

이 예제에서는 서비스의 시작 유형이 **사용 하지 않도록 설정** 된 경우 서비스를 시작 하는 방법을 보여 줍니다.

```
PS> Start-Service tlntsvr
Start-Service : Service 'Telnet (TlntSvr)' cannot be started due to the following error: Cannot start service TlntSvr on computer '.'.
At line:1 char:14
+ Start-Service  <<<< tlntsvr

PS> Get-CimInstance win32_service | Where-Object Name -eq "tlntsvr"
ExitCode  : 0
Name      : TlntSvr
ProcessId : 0
StartMode : Disabled
State     : Stopped
Status    : OK

PS> Set-Service tlntsvr -StartupType manual
PS> Start-Service tlntsvr
```

텔넷 서비스 (tlntsvr)를 시작 하려는 첫 번째 시도가 실패 합니다. `Get-CimInstance`명령은 Tlntsvr 서비스의 **StartMode** 속성을 **사용할 수** 없다는 것을 보여 줍니다. `Set-Service`Cmdlet은 시작 유형을 **수동으로** 변경 합니다. 이제 명령을 다시 제출할 수 있습니다 `Start-Service` . 명령이 성공적으로 실행됩니다. 명령이 성공 했는지 확인 하려면를 실행 `Get-Service` 합니다.

## PARAMETERS

### -DisplayName

시작할 서비스의 표시 이름을 지정 합니다. 와일드카드 문자를 사용할 수 있습니다.

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

이 cmdlet이 생략 하는 서비스를 지정 합니다. 이 매개 변수 값은 **Name** 매개 변수를 한정 합니다. 이름 요소 또는 패턴 (예:)을 입력 `s*` 합니다. 와일드카드 문자를 사용할 수 있습니다.

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

이 cmdlet이 시작 되는 서비스를 지정 합니다. 이 매개 변수 값은 **Name** 매개 변수를 한정 합니다. 이름 요소 또는 패턴 (예:)을 입력 `s*` 합니다. 와일드카드 문자를 사용할 수 있습니다.

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

시작할 서비스를 나타내는 **ServiceController** 개체를 지정 합니다. 개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요.

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

시작할 서비스의 서비스 이름을 지정합니다.

매개 변수 이름은 선택 사항입니다. **이름** 또는 별칭, **ServiceName** 을 사용 하거나 매개 변수 이름을 생략할 수 있습니다.

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

서비스 또는 서비스 이름이 포함 된 문자열을 나타내는 개체를이 cmdlet으로 파이프 할 수 있습니다.

## 출력

### None, ServiceController

이 cmdlet은 **PassThru** 를 지정 하는 경우 서비스를 나타내는 **ServiceController** 개체를 생성 합니다. 그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.

## 참고

* 의 기본 제공 별칭인를 참조할 수도 있습니다 `Start-Service` `sasv` . 자세한 내용은 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)를 참조 하세요.
* `Start-Service` 현재 사용자에 게이 작업을 수행할 수 있는 권한이 있는 경우에만 서비스를 제어할 수 있습니다. 따라서 명령이 제대로 작동하지 않는 경우 필요한 권한이 없을 수 있습니다.
* 시스템에서 서비스의 서비스 이름 및 표시 이름을 찾으려면를 입력 `Get-Service` 합니다.
  서비스 이름은 **Name** 열에 나타나고 표시 이름은 **DisplayName** 열에 나타납니다.
* 시작 유형이 수동, 자동 또는 자동 (지연 된 시작) 인 서비스만 시작할 수 있습니다. 시작 유형이 Disabled 인 서비스는 시작할 수 없습니다. `Start-Service`메시지와 함께 명령이 실패 하는 경우를 `Cannot start service \<service-name\> on computer` 사용 `Get-CimInstance` 하 여 서비스의 시작 유형을 찾고, 필요 하면 cmdlet을 사용 하 여 `Set-Service` 서비스의 시작 유형을 변경 합니다.
* 성능 로그 및 경고 (SysmonLog)와 같은 일부 서비스는 수행할 작업이 없는 경우 자동으로 중지 됩니다. PowerShell이 거의 즉시 중지 하는 서비스를 시작 하면 다음과 같은 메시지가 표시 됩니다. `Service \<display-name\> start failed.`

## 관련 링크

[Get-Service](Get-Service.md)

[New-Service](New-Service.md)

[Restart-Service](Restart-Service.md)

[Resume-Service](Resume-Service.md)

[Set-Service](Set-Service.md)

[Stop-Service](Stop-Service.md)

[Suspend-Service](Suspend-Service.md)

[Remove-Service](Remove-Service.md)

