---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-pstransportoption?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSTransportOption
ms.openlocfilehash: 9257c0a1829cc9cc85029f7c6fdc8e61b0ed7e56
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/23/2020
ms.locfileid: "93218169"
---
# New-PSTransportOption

## 개요

세션 구성에 대한 고급 옵션을 포함하는 개체를 만듭니다.

## SYNTAX

```
New-PSTransportOption [-MaxIdleTimeoutSec <Int32>] [-ProcessIdleTimeoutSec <Int32>] [-MaxSessions <Int32>]
 [-MaxConcurrentCommandsPerSession <Int32>] [-MaxSessionsPerUser <Int32>] [-MaxMemoryPerSessionMB <Int32>]
 [-MaxProcessesPerSession <Int32>] [-MaxConcurrentUsers <Int32>] [-IdleTimeoutSec <Int32>]
 [-OutputBufferingMode <OutputBufferingMode>] [<CommonParameters>]
```

## 설명

**New-PSTransportOption** cmdlet은 세션 구성에 대한 전송 옵션을 포함하는 개체를 만듭니다.
Register-PSSessionConfiguration 및 Set-PSSessionConfiguration cmdlet과 같은 세션 구성을 만들거나 변경 *TransportOption* 하는 cmdlet의 값으로 개체를 사용할 수 있습니다.

WSMan: 드라이브에서 세션 구성 속성 값을 편집하여 전송 옵션 설정을 변경할 수도 있습니다.
자세한 내용은 WSMan 공급자를 참조 하세요.

세션 구성 옵션은 서버 쪽 또는 원격 연결의 수신 끝에서 설정 된 세션 값을 나타냅니다.
세션을 만들 때 또는 클라이언트에서 세션의 연결을 끊거나 세션에 다시 연결할 때 클라이언트 쪽 또는 연결의 송신 끝에서 세션 옵션 값을 설정할 수 있습니다.
달리 명시되지 않은 한 설정 값이 충돌할 경우 클라이언트 쪽 값이 우선합니다.
그러나 클라이언트 쪽 값은 세션 구성에서 설정된 최대값 및 할당량을 위반할 수 없습니다.

매개 변수가 없으면 **new-pstransportoption** 는 모든 옵션에 대해 null 값을 갖는 전송 옵션 개체를 생성 합니다.
매개 변수를 생략하면 해당 매개 변수가 나타내는 개체의 속성 값은 null이 됩니다.
Null 값은 세션 구성에 영향을 주지 않습니다.

세션 옵션에 대 한 자세한 내용은 New-PSSessionOption을 참조 하세요.
세션 구성에 대 한 자세한 내용은 [about_Session_Configurations](About/about_Session_Configurations.md)를 참조 하세요.

이 cmdlet은 Windows PowerShell 3.0에서 도입되었습니다.

## 예제

### 예제 1: 기본 전송 옵션 생성

```
PS C:\> New-PSTransportOption
ProcessIdleTimeoutSec           :
MaxIdleTimeoutSec               :
MaxSessions                     :
MaxConcurrentCommandsPerSession :
MaxSessionsPerUser              :
MaxMemoryPerSessionMB           :
MaxProcessesPerSession          :
MaxConcurrentUsers              :
IdleTimeoutSec                  :
OutputBufferingMode             :
```

이 명령은 매개 변수 없이 **new-pstransportoption** 를 실행 합니다.
출력은 cmdlet에서 모든 속성에 대해 null 값을 갖는 전송 옵션 개체를 생성 함을 보여 줍니다.

### 예제 2: 세션 구성 옵션 가져오기

```
The first command uses the **New-PSTransportOption** cmdlet to create a transport options object, which it saves in the $t variable. The command uses the *MaxSessions* parameter to increase the maximum number of sessions to 40.
PS C:\> $t = New-PSTransportOption -MaxSessions 40

The second command uses the **Register-PSSessionConfiguration** cmdlet create the ITTasks session configuration. The command uses the *TransportOption* parameter to specify the transport options object in the $t variable.
PS C:\> Register-PSSessionConfiguration -Name ITTasks -TransportOption $t

The third command uses the Get-PSSessionConfiguration cmdlet to get the ITTasks session configurations and the Format-List cmdlet to display all of the properties of the session configuration object in a list. The output shows that the value of the **MaxShells** property of the session configuration is 40.
PS C:\> Get-PSSessionConfiguration -Name ITTasks | Format-List -Property *
Architecture                  : 64
Filename                      : %windir%\system32\pwrshplugin.dll
ResourceUri                   : http://schemas.microsoft.com/powershell/ITTasks
MaxConcurrentCommandsPerShell : 1000
UseSharedProcess              : false
ProcessIdleTimeoutSec         : 0
xmlns                         : http://schemas.microsoft.com/wbem/wsman/1/config/PluginConfiguration
MaxConcurrentUsers            : 5
lang                          : en-US
SupportsOptions               : true
ExactMatch                    : true
RunAsUser                     :
IdleTimeoutms                 : 7200000
PSVersion                     : 3.0
OutputBufferingMode           : Block
AutoRestart                   : false
MaxShells                     : 40
MaxMemoryPerShellMB           : 1024
MaxIdleTimeoutms              : 43200000
SDKVersion                    : 2
Name                          : ITTasks
XmlRenderingType              : text
Capability                    : {Shell}
RunAsPassword                 :
MaxProcessesPerShell          : 15
Enabled                       : True
MaxShellsPerUser              : 25
Permission                    :
```

이 예제에서는 전송 옵션 개체를 사용 하 여 세션 구성 옵션을 설정 하는 방법을 보여 줍니다.

### 예 3: 전송 옵션 설정

```
The first command uses the **New-PSTransportOption** cmdlet to create a transport option object. The command uses the *IdleTimeoutSec* parameter to set the **IdleTimeoutSec** property value of the object to one hour (3600 seconds). The command saves the transport objects object in the $t variable.
PS C:\> $t = New-PSTransportOption -IdleTimeoutSec 3600

The second command uses the Set-PSSessionConfiguration cmdlet to change the transport options of the ITTasks session configuration. The command uses the *TransportOption* parameter to specify the transport options object in the $t variable.
PS C:\> Set-PSSessionConfiguration -Name ITTasks -TransportOption $t

The third command uses the New-PSSession cmdlet to create the MyITTasks session on the local computer. The command uses the **ConfigurationName** property to specify the ITTasks session configuration. The command saves the session in the $s variable.Notice that the command does not use the *SessionOption* parameter of **New-PSSession** to set a custom idle time-out for the session. If it did, the idle time-out value set in the session option would take precedence over the idle time-out set in the session configuration.
PS C:\> $s = New-PSSession -Name MyITTasks -ConfigurationName ITTasks

The fourth command uses the Format-List cmdlet to display all properties of the session in the $s variable in a list. The output shows that the session has an idle time-out of one hour (360,000 milliseconds).
PS C:\> $s | Format-List -Property *
State                  : Opened
IdleTimeout            : 3600000
OutputBufferingMode    : Block
ComputerName           : localhost
ConfigurationName      : ITTasks
InstanceId             : 4110c3f5-68ea-40fa-9bbf-04a433dbb02d
Id                     : 1
Name                   : MyITTasks
Availability           : Available
ApplicationPrivateData : {PSVersionTable}
Runspace               : System.Management.Automation.RemoteRunspace
```

이 명령은 세션 구성에서 전송 옵션을 설정할 경우 세션 구성을 사용하는 세션에 미치는 영향을 보여 줍니다.

## PARAMETERS

### -IdleTimeoutSec

원격 컴퓨터가 로컬 컴퓨터의 통신을 받지 못하는 경우 각 세션이 열려 있는 기간을 결정 합니다.
하트 비트 신호를 포함 합니다.
간격이 만료되면 세션이 닫힙니다.

유휴 시간 제한 값은 사용자가 세션에서 연결을 끊고 다시 연결 하려는 경우에 매우 중요 합니다.
사용자는 세션이 시간 초과되지 않은 경우에만 다시 연결할 수 있습니다.

*IdleTimeoutSec* 매개 변수는 세션 구성의 **IdleTimeoutMs** 속성에 해당합니다.

값을 초 단위로 입력하세요.
기본값은 7200(2시간)입니다.
최소값은 60 (1 분)입니다.
Maximum은 WSMan 구성에서 Shell 개체의 **IdleTimeout** 속성 값 ( `WSMan:\\\<ComputerName\>\Shell\IdleTimeout` )입니다.
기본값은 7200000밀리초(2시간)입니다.

세션 옵션 및 세션 구성에 유휴 시간 제한 값이 설정 된 경우 세션 옵션에 설정 된 값이 우선 하지만 세션 구성의 **MaxIdleTimeoutMs** 속성 값을 초과할 수 없습니다.
**MaxIdleTimeoutMs** 속성 값을 설정하려면 *MaxIdleTimeoutSec* 매개 변수를 사용합니다.

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Idletimeoutsec

각 세션에서 동시에 실행할 수 있는 명령 수를 지정 된 값으로 제한 합니다.
기본값은 1000입니다.

*Idletimeoutsec* 매개 변수는 세션 구성의 **idletimeoutms** 속성에 해당 합니다.

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -MaxConcurrentUsers

각 세션에서 동시에 명령을 실행할 수 있는 사용자 수를 지정 된 값으로 제한 합니다.
기본값은 5입니다.

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -MaxIdleTimeoutSec

각 세션에 대 한 유휴 제한 시간 집합을 지정 된 값으로 제한 합니다.
기본값은 \[ Int \] :: int32.maxvalue (~ 25 일)입니다.

유휴 시간 제한 값은 사용자가 세션에서 연결을 끊고 다시 연결 하려는 경우에 매우 중요 합니다.
사용자는 세션이 시간 초과되지 않은 경우에만 다시 연결할 수 있습니다.

*MaxIdleTimeoutSec* 매개 변수는 세션 구성의 **MaxIdleTimeoutMs** 속성에 해당 합니다.

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -MaxMemoryPerSessionMB

각 세션에서 사용하는 메모리를 지정된 값으로 제한합니다.
값을 메가바이트 단위로 입력합니다.
기본값은 1024메가바이트(1GB)입니다.

*&lt;system&gt;IdleTimeoutSec&lt;/system&gt;* 매개 변수는 세션 구성의 **&lt;system&gt;IdleTimeoutMs&lt;/system&gt;** 속성에 해당합니다.

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -MaxProcessesPerSession

각 세션에서 실행되는 프로세스 수를 지정된 값으로 제한합니다.
기본값은 15입니다.

*MaxProcessesPerSession* 매개 변수는 세션 구성의 **MaxProcessesPerShell** 속성에 해당 합니다.

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -MaxSessions

세션 구성을 사용하는 세션 수를 제한합니다.
기본값은 25입니다.

*MaxSessions* 매개 변수는 세션 구성의 **maxshells** 속성에 해당 합니다.

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -MaxSessionsPerUser

세션 구성을 사용하고 지정된 사용자의 자격 증명으로 실행되는 세션 수를 지정된 값으로 제한합니다.
기본값은 25입니다.

이 값을 지정 하는 경우 많은 사용자가 실행 사용자의 자격 증명을 사용 하 고 있을 수 있습니다.

*Maxsessionsperuser* 매개 변수는 세션 구성의 **maxsessionsperuser** 속성에 해당 합니다.

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -OutputBufferingMode

출력 버퍼가 가득 찰 경우 연결이 끊긴 세션에서 명령 출력을 관리하는 방법을 결정합니다.
이 매개 변수에 허용되는 값은 다음과 같습니다.

- 차단.
출력 버퍼가 가득 찰 경우 버퍼를 지울 때까지 실행이 일시 중단됩니다.
- Drop.
출력 버퍼가 가득 차도 실행이 계속됩니다.
새 출력이 저장되면 가장 오래된 출력을 버립니다.
- 없음
출력 버퍼링 모드를 지정하지 않습니다.

Sessions의 **OutputBufferingMode** 속성 기본값은 Block입니다.

```yaml
Type: System.Nullable`1[System.Management.Automation.Runspaces.OutputBufferingMode]
Parameter Sets: (All)
Aliases:
Accepted values: None, Drop, Block

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ProcessIdleTimeoutSec

각 호스트 프로세스에 대 한 제한 시간을 지정 된 값으로 제한 합니다.
기본값 0은 프로세스에 대 한 시간 제한 값이 없음을 의미 합니다.

다른 세션 구성에는 프로세스별 시간 제한 값이 있습니다.
예를 들어, **Microsoft PowerShell 워크플로** 세션 구성에는 프로세스별 시간 제한 값 28800 초 (8 시간)가 있습니다.

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters
이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### 없음

이 cmdlet에 입력을 파이프할 수 없습니다.

## 출력

### Microsoft. PowerShell. WSManConfigurationOption

## 참고

- 세션 구성 개체의 속성은 세션 구성에 대해 설정된 옵션과 해당 옵션 값에 따라 달라집니다. 또한 세션 구성 파일을 사용하는 세션 구성에는 추가 속성이 있습니다.

## 관련 링크

[New-PSSession](New-PSSession.md)

[New-PSSessionOption](New-PSSessionOption.md)

[Register-PSSessionConfiguration](Register-PSSessionConfiguration.md)

[Set-PSSessionConfiguration](Set-PSSessionConfiguration.md)
