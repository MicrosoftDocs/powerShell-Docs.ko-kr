---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-service?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Service
ms.openlocfilehash: 0c007f1becd7364806cfd47e18cf05995b81e0f7
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93215402"
---
# Get-Service

## 개요
로컬 또는 원격 컴퓨터의 서비스를 가져옵니다.

## SYNTAX

### Default (기본값)

```
Get-Service [[-Name] <String[]>] [-ComputerName <String[]>] [-DependentServices] [-RequiredServices]
 [-Include <String[]>] [-Exclude <String[]>] [<CommonParameters>]
```

### DisplayName

```
Get-Service [-ComputerName <String[]>] [-DependentServices] [-RequiredServices] -DisplayName <String[]>
 [-Include <String[]>] [-Exclude <String[]>] [<CommonParameters>]
```

### InputObject

```
Get-Service [-ComputerName <String[]>] [-DependentServices] [-RequiredServices] [-Include <String[]>]
 [-Exclude <String[]>] [-InputObject <ServiceController[]>] [<CommonParameters>]
```

## 설명

**Get-help** cmdlet은 실행 중인 서비스와 중지 된 서비스를 포함 하 여 로컬 컴퓨터 또는 원격 컴퓨터의 서비스를 나타내는 개체를 가져옵니다.

서비스의 서비스 이름 또는 표시 이름을 지정 하 여 특정 서비스만 가져오도록이 cmdlet을 지시 하거나, 서비스 개체를이 cmdlet으로 파이프 할 수 있습니다.

## 예제

### 예 1: 컴퓨터의 모든 서비스 가져오기

```powershell
Get-Service
```

이 명령은 컴퓨터의 모든 서비스를 가져옵니다.
입력 한 것 처럼 동작 `Get-Service *` 합니다.
기본 표시에서는 각 서비스의 상태, 서비스 이름 및 표시 이름을 보여 줍니다.

### 예제 2: 검색 문자열로 시작 하는 서비스 가져오기

```powershell
Get-Service "wmi*"
```

이 명령은 WMI (WMI(Windows Management Instrumentation)의 머리글자어)로 시작 하는 서비스 이름을 사용 하 여 서비스를 검색 합니다.

### 예제 3: 검색 문자열을 포함 하는 서비스 표시

```powershell
Get-Service -Displayname "*network*"
```

이 명령은 단어 네트워크를 포함 하는 표시 이름을 포함 하는 서비스를 표시 합니다.
표시 이름을 검색하면 xmlprov(Network Provisioning Service)와 같이 서비스 이름에 "Net"이 없는 경우에도 네트워크 관련 서비스를 찾을 수 있습니다.

### 예제 4: 검색 문자열과 제외로 시작 하는 서비스 가져오기

```powershell
Get-Service -Name "win*" -Exclude "WinRM"
```

이러한 명령은 WinRM 서비스를 제외 하 고 서비스 이름이 win으로 시작 하는 서비스만 가져옵니다.

### 예 5: 현재 활성화 된 서비스 표시

```powershell
Get-Service | Where-Object {$_.Status -eq "Running"}
```

이 명령은 현재 활성화 된 서비스만 표시 합니다.
이 cmdlet은 **get-Service** cmdlet을 사용 하 여 컴퓨터의 모든 서비스를 가져옵니다.
파이프라인 연산자 (|)가 결과를 Where-Object cmdlet으로 전달 합니다 .이 cmdlet은 실행 중인 상태 속성의 서비스만 선택 합니다.

Status는 서비스 개체의 속성 중 하나에 불과합니다.
모든 속성을 보려면를 입력 `Get-Service | Get-Member` 합니다.

### 예 6: 원격 컴퓨터에서 서비스 가져오기

```powershell
Get-Service -ComputerName "Server02"
```

이 명령은 Server02 원격 컴퓨터의 서비스를 가져옵니다.

**서비스** 의 *ComputerName* 매개 변수는 windows powershell 원격을 사용 하지 않으므로 windows powershell에서 원격 기능을 사용 하도록 구성 되지 않은 경우에도이 매개 변수를 사용할 수 있습니다.

### 예 7: 종속 서비스가 있는 로컬 컴퓨터의 서비스 나열

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

첫 번째 명령은 **get-help** cmdlet을 사용 하 여 컴퓨터의 서비스를 가져옵니다.
파이프라인 연산자 (|)가 DependentServices cmdlet으로 서비스를 보냅니다 .이 **cmdlet은 해당** **DependentServices** 속성이 null이 아닌 서비스를 선택 합니다.

다른 파이프라인 연산자(|)는 결과를 Format-List cmdlet으로 보냅니다.
이 명령은 해당 *Property* 매개 변수를 사용 하 여 서비스의 이름, 종속 된 서비스의 이름 및 각 서비스에 포함 된 종속 서비스의 수를 표시 하는 계산 된 속성을 표시 합니다.

### 예 8: 속성 값으로 서비스 정렬

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

이 명령은 **상태** 속성의 값을 기준으로 오름차순으로 서비스를 정렬 하는 경우 서비스를 실행 하기 전에 중지 된 서비스를 표시 함을 보여 줍니다.
Status 값이 열거형 이며,이는 중지 된 값이 1이 고 실행 값이 4 인 경우에 발생 합니다.

실행 중인 서비스를 먼저 나열 하려면 Sort-Object cmdlet의 *내림차순* 매개 변수를 사용 합니다.

### 예 9: 여러 컴퓨터에서 서비스 가져오기

```powershell
Get-Service -Name "WinRM" -ComputerName "localhost", "Server01", "Server02" |
 Format-Table -Property MachineName, Status, Name, DisplayName -auto
```

```Output
MachineName    Status  Name  DisplayName
------------   ------  ----  -----------
localhost      Running WinRM Windows Remote Management (WS-Management)
Server01       Running WinRM Windows Remote Management (WS-Management)
Server02       Running WinRM Windows Remote Management (WS-Management)
```

이 명령은 **Get Service** cmdlet을 사용 하 여 두 원격 컴퓨터와 로컬 컴퓨터 ("localhost")에서 Get-Service Winrm 명령을 실행 합니다.

이 명령은 원격 컴퓨터에서 실행 되 고 결과는 로컬 컴퓨터에 반환 됩니다.
파이프라인 연산자 (|)가 결과를 **형식 테이블** cmdlet으로 보내면이 cmdlet이 서비스를 테이블로 포맷 합니다.
**Format-table** 명령은 *Property* 매개 변수를 사용 하 여 **MachineName** 속성을 포함 하 여 테이블에 표시 되는 속성을 지정 합니다.

### 예 10: 서비스의 종속 서비스 가져오기

```powershell
Get-Service "WinRM" -RequiredServices
```

이 명령은 WinRM 서비스에 필요한 서비스를 가져오고,

이 명령은 서비스의 **ServicesDependedOn** 속성 값을 반환 합니다.

### 예 11: 파이프라인 연산자를 통해 서비스 가져오기

```powershell
"WinRM" | Get-Service
```

이 명령은 로컬 컴퓨터의 WinRM 서비스를 가져옵니다.
이 예제에서는 서비스 이름 문자열 (따옴표 안에 포함 됨)을 **service** 로 파이프 하는 것을 보여 줍니다.

## PARAMETERS

### -ComputerName

지정된 컴퓨터에서 실행 중인 서비스를 가져옵니다.
기본값은 로컬 컴퓨터입니다.

원격 컴퓨터의 NetBIOS 이름, IP 주소 또는 FQDN (정규화 된 도메인 이름)을 입력 합니다.
로컬 컴퓨터를 지정 하려면 컴퓨터 이름, 점 (.) 또는 localhost를 입력 합니다.

이 매개 변수는 Windows PowerShell 원격 기능을 사용하지 않습니다.
컴퓨터가 원격 명령을 실행 하도록 구성 되지 않은 경우 **에도** *ComputerName* 매개 변수를 사용할 수 있습니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Cn

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -DependentServices

이 cmdlet은 지정 된 서비스에 종속 된 서비스만 가져옵니다.

기본적으로이 cmdlet은 모든 서비스를 가져옵니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: DS

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DisplayName

검색할 서비스의 표시 이름을 문자열 배열로 지정 합니다.
와일드카드가 지원됩니다.
기본적으로이 cmdlet은 컴퓨터의 모든 서비스를 가져옵니다.

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
이 매개 변수 값은 *Name* 매개 변수를 한정 합니다.
이름 요소 또는 패턴(예: "*s*")을 입력합니다.
와일드카드가 지원됩니다.

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

이 cmdlet이 작업에 포함 하는 서비스 또는 서비스를 문자열 배열로 지정 합니다.
이 매개 변수 값은 *Name* 매개 변수를 한정 합니다.
이름 요소 또는 패턴(예: "*s*")을 입력합니다.
와일드카드가 지원됩니다.

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

검색할 서비스를 나타내는 **ServiceController** 개체를 지정 합니다.
개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요.
서비스 개체를이 cmdlet으로 파이프 할 수도 있습니다.

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

검색할 서비스의 표시 이름을 지정합니다.
와일드카드가 지원됩니다.
기본적으로이 cmdlet은 컴퓨터의 모든 서비스를 가져옵니다.

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

이 cmdlet은이 서비스에 필요한 서비스만 가져옵니다.

이 매개 변수는 서비스의 **ServicesDependedOn** 속성 값을 가져옵니다.
기본적으로이 cmdlet은 모든 서비스를 가져옵니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: SDO, ServicesDependedOn

Required: False
Position: Named
Default value: None
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

또한 해당 기본 제공 별칭 ("gsv")으로 **서비스** 를 참조할 수 있습니다. 자세한 내용은 about_Aliases를 참조하세요.

이 cmdlet은 현재 사용자가 해당 서비스를 볼 수 있는 권한을 가진 경우에만 서비스를 표시할 수 있습니다.
이 cmdlet이 서비스를 표시 하지 않는 경우 해당 서비스를 볼 수 있는 권한이 없을 수 있습니다.

시스템에 있는 각 서비스의 서비스 이름 및 표시 이름을 찾으려면를 입력 `Get-Service` 합니다.
서비스 이름은 Name 열에 나타나고 표시 이름은 DisplayName 열에 나타납니다.

상태 값을 기준으로 오름차순으로 정렬하는 경우 상태가 "Stopped"인 서비스가 상태가 "Running"인 서비스보다 앞에 나타납니다.
서비스의 Status 속성은 상태 이름이 정수 값으로 나타나는 열거형 값입니다.
정렬 작업은 이름이 아니라 정수 값을 기준으로 수행됩니다.
"Stopped"는 값이 "1"이고 "Running"은 값이 "4"이기 때문에 "Running"이 "Stopped"보다 앞에 나타납니다.

## 관련 링크

[New-Service](New-Service.md)

[Restart-Service](Restart-Service.md)

[Resume-Service](Resume-Service.md)

[Set-Service](Set-Service.md)

[Start-Service](Start-Service.md)

[Stop-Service](Stop-Service.md)

[Suspend-Service](Suspend-Service.md)
