---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/30/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-service?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Service
ms.openlocfilehash: c27dac11cdd8ebbf1705ac3bba0c0aa5147d4fa8
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99602236"
---
# Get-Service

## 개요
컴퓨터의 서비스를 가져옵니다.

## SYNTAX

### Default (기본값)

```
Get-Service [[-Name] <String[]>] [-DependentServices] [-RequiredServices] [-Include <String[]>]
 [-Exclude <String[]>] [<CommonParameters>]
```

### DisplayName

```
Get-Service [-DependentServices] [-RequiredServices] -DisplayName <String[]> [-Include <String[]>]
 [-Exclude <String[]>] [<CommonParameters>]
```

### InputObject

```
Get-Service [-DependentServices] [-RequiredServices] [-Include <String[]>] [-Exclude <String[]>]
 [-InputObject <ServiceController[]>] [<CommonParameters>]
```

## 설명

`Get-Service`Cmdlet은 실행 중인 서비스와 중지 된 서비스를 포함 하 여 컴퓨터의 서비스를 나타내는 개체를 가져옵니다. 기본적으로 `Get-Service` 매개 변수 없이를 실행 하면 모든 로컬 컴퓨터의 서비스가 반환 됩니다.

서비스의 서비스 이름 또는 표시 이름을 지정 하 여 특정 서비스만 가져오도록이 cmdlet을 지시 하거나, 서비스 개체를이 cmdlet으로 파이프 할 수 있습니다.

## 예제

### 예 1: 컴퓨터의 모든 서비스 가져오기

이 예제에서는 컴퓨터의 모든 서비스를 가져옵니다. 입력 한 것 처럼 동작 `Get-Service *` 합니다. 기본 표시에서는 각 서비스의 상태, 서비스 이름 및 표시 이름을 보여 줍니다.

```powershell
Get-Service
```

### 예제 2: 검색 문자열로 시작 하는 서비스 가져오기

이 예제에서는 WMI (WMI(Windows Management Instrumentation))로 시작 하는 서비스 이름을 사용 하 여 서비스를 검색 합니다.

```powershell
Get-Service "wmi*"
```

### 예제 3: 검색 문자열을 포함 하는 서비스 표시

이 예에서는 단어 네트워크를 포함 하는 표시 이름을 포함 하는 서비스를 표시 합니다. 표시 이름을 검색 하면 서비스 이름에 네트워크 프로 비전 서비스와 같은 네트워크 (예: xmlprov)가 포함 되지 않은 경우에도 네트워크 관련 서비스가 검색 됩니다.

```powershell
Get-Service -Displayname "*network*"
```

### 예제 4: 검색 문자열과 제외로 시작 하는 서비스 가져오기

이 예제에서는 WinRM 서비스를 제외 하 고 서비스 이름이 **win** 으로 시작 하는 서비스만 가져옵니다.

```powershell
Get-Service -Name "win*" -Exclude "WinRM"
```

### 예 5: 현재 활성화 된 서비스 표시

이 예에서는 실행 중 상태의 서비스만 표시 합니다.

```powershell
Get-Service | Where-Object {$_.Status -eq "Running"}
```

`Get-Service` 컴퓨터의 모든 서비스를 가져오고 개체를 파이프라인으로 보냅니다. `Where-Object`Cmdlet은 실행 중인 **상태** 속성의 서비스만 선택 합니다.

Status는 서비스 개체의 속성 중 하나에 불과합니다. 모든 속성을 보려면를 입력 `Get-Service | Get-Member` 합니다.

### 예 6: 종속 서비스가 있는 컴퓨터의 서비스 나열

이 예제에서는 종속 서비스가 있는 서비스를 가져옵니다.

```powershell
Get-Service |
  Where-Object {$_.DependentServices} |
    Format-List -Property Name, DependentServices, @{
      Label="NoOfDependentServices"; Expression={$_.dependentservices.count}
    }
```

```Output
Name                  : AudioEndpointBuilder
DependentServices     : {AudioSrv}
NoOfDependentServices : 1

Name                  : Dhcp
DependentServices     : {WinHttpAutoProxySvc}
NoOfDependentServices : 1
...
```

`Get-Service`Cmdlet은 컴퓨터의 모든 서비스를 가져오고 개체를 파이프라인으로 보냅니다. `Where-Object`Cmdlet은 **DependentServices** 속성이 null이 아닌 서비스를 선택 합니다.

결과는 파이프라인에서 cmdlet으로 전송 됩니다 `Format-List` . **Property** 매개 변수는 서비스의 이름, 종속 된 서비스의 이름 및 각 서비스에 대 한 종속 서비스의 수를 표시 하는 계산 된 속성을 표시 합니다.

### 예제 7: 속성 값으로 서비스 정렬

이 예에서는 서비스를 해당 **상태** 속성 값으로 오름차순으로 정렬 하는 경우 서비스를 실행 하기 전에 중지 된 서비스를 표시 하는 방법을 보여 줍니다. 그 이유는 **Status** 값이 열거형 이며,이는 중지 된 값이 1이 고 실행의 값은 4 이기 때문입니다. 자세한 내용은 [ServiceControllerStatus](/dotnet/api/system.serviceprocess.servicecontrollerstatus)를 참조 하세요.

실행 중인 서비스를 먼저 나열 하려면 cmdlet의 **내림차순** 매개 변수를 사용 합니다 `Sort-Object` .

```powershell
Get-Service "s*" | Sort-Object status
```

```Output
Status   Name               DisplayName
------   ----               -----------
Stopped  stisvc             Windows Image Acquisition (WIA)
Stopped  SwPrv              MS Software Shadow Copy Provider
Stopped  SysmonLog          Performance Logs and Alerts
Running  Spooler            Print Spooler
Running  srservice          System Restore Service
Running  SSDPSRV            SSDP Discovery Service
Running  ShellHWDetection   Shell Hardware Detection
Running  Schedule           Task Scheduler
Running  SCardSvr           Smart Card
Running  SamSs              Security Accounts Manager
Running  SharedAccess       Windows Firewall/Internet Connectio...
Running  SENS               System Event Notification
Running  seclogon           Secondary Logon
```

### 예 8: 서비스의 종속 서비스 가져오기

이 예제에서는 WinRM 서비스에 필요한 서비스를 가져옵니다. 서비스의 **ServicesDependedOn** 속성 값이 반환 됩니다.

```powershell
Get-Service "WinRM" -RequiredServices
```

### 예 9: 파이프라인 연산자를 통해 서비스 가져오기

이 예제에서는 로컬 컴퓨터의 WinRM 서비스를 가져옵니다. 따옴표로 묶인 서비스 이름 문자열은 파이프라인에서로 전송 됩니다 `Get-Service` .

```powershell
"WinRM" | Get-Service
```

## PARAMETERS

### -DependentServices

이 cmdlet은 지정 된 서비스에 종속 된 서비스만 가져옵니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: DS

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -DisplayName

검색할 서비스의 표시 이름을 문자열 배열로 지정 합니다. 와일드카드가 지원됩니다.

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

이 cmdlet이 작업에서 제외 하는 서비스 또는 서비스를 문자열 배열로 지정 합니다.
이 매개 변수 값은 **Name** 매개 변수를 한정 합니다. 이름 요소 또는 패턴 (예:)을 입력 `s*` 합니다. 와일드카드가 지원됩니다.

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

이 cmdlet이 작업에 포함 하는 서비스 또는 서비스를 문자열 배열로 지정 합니다. 이 매개 변수 값은 **Name** 매개 변수를 한정 합니다. 이름 요소 또는 패턴 (예:)을 입력 `s*` 합니다. 와일드카드가 지원됩니다.

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

검색할 서비스를 나타내는 **ServiceController** 개체를 지정 합니다. 개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요. 서비스 개체를이 cmdlet으로 파이프 할 수 있습니다.

```yaml
Type: System.ServiceProcess.ServiceController[]
Parameter Sets: InputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name

검색할 서비스의 표시 이름을 지정합니다. 와일드카드가 지원됩니다.

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases: ServiceName

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -RequiredServices

이 cmdlet은이 서비스에 필요한 서비스만 가져옵니다. 이 매개 변수는 서비스의 **ServicesDependedOn** 속성 값을 가져옵니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: SDO, ServicesDependedOn

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: True
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### ServiceController, System.string입니다.

서비스 개체 또는 서비스 이름을이 cmdlet으로 파이프 할 수 있습니다.

## 출력

### System.ServiceProcess.ServiceController

이 cmdlet은 컴퓨터의 서비스를 나타내는 개체를 반환 합니다.

## 참고

이 cmdlet은 Windows 플랫폼 에서만 사용할 수 있습니다.

PowerShell 6.0부터 다음 속성이 **ServiceController** 개체에 추가 됩니다. **사용자 이름**, **설명**, **Delayedautostart** 시작, **BinaryPathName** 및 **startuptype** .

의 기본 제공 별칭인를 참조할 수도 있습니다 `Get-Service` `gsv` . 자세한 내용은 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)를 참조 하세요.

이 cmdlet은 현재 사용자가 해당 서비스를 볼 수 있는 권한을 가진 경우에만 서비스를 표시할 수 있습니다. 이 cmdlet이 서비스를 표시 하지 않는 경우 해당 서비스를 볼 수 있는 권한이 없을 수 있습니다.

시스템에 있는 각 서비스의 서비스 이름 및 표시 이름을 찾으려면를 입력 `Get-Service` 합니다. 서비스 이름은 Name 열에 나타나고 표시 이름은 **DisplayName** 열에 나타납니다.

**상태** 속성의 값을 기준으로 오름차순으로 정렬 하는 경우 서비스를 실행 하기 전에 중지 된 서비스가 표시 됩니다. 서비스의 **status** 속성은 열거형 값이 고 상태 이름은 정수 값을 나타냅니다. 정렬 순서는 이름이 아니라 정수 값을 기준으로 합니다. 중지 됨은의 값이 1이 고 실행의 값은 4 이기 때문에 중지 된 것으로 나타납니다. 자세한 내용은 [ServiceControllerStatus](/dotnet/api/system.serviceprocess.servicecontrollerstatus)를 참조 하세요.

## 관련 링크

[New-Service](New-Service.md)

[Restart-Service](Restart-Service.md)

[Resume-Service](Resume-Service.md)

[Set-Service](Set-Service.md)

[Start-Service](Start-Service.md)

[Stop-Service](Stop-Service.md)

[Suspend-Service](Suspend-Service.md)

[Remove-Service](Remove-Service.md)
