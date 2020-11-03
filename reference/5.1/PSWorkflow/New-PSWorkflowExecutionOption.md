---
external help file: Microsoft.Powershell.Workflow.ServiceCore.dll-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSWorkflow
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflow/new-psworkflowexecutionoption?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSWorkflowExecutionOption
ms.openlocfilehash: db5d19396f555a41ad14552823c57f3b11c79321
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/23/2020
ms.locfileid: "93218289"
---
# New-PSWorkflowExecutionOption

## 개요

워크플로 세션에 대한 세션 구성 옵션을 포함하는 개체를 만듭니다.

## SYNTAX

```
New-PSWorkflowExecutionOption [-PersistencePath <String>] [-MaxPersistenceStoreSizeGB <Int64>]
 [-PersistWithEncryption] [-MaxRunningWorkflows <Int32>] [-AllowedActivity <String[]>]
 [-OutOfProcessActivity <String[]>] [-EnableValidation] [-MaxDisconnectedSessions <Int32>]
 [-MaxConnectedSessions <Int32>] [-MaxSessionsPerWorkflow <Int32>] [-MaxSessionsPerRemoteNode <Int32>]
 [-MaxActivityProcesses <Int32>] [-ActivityProcessIdleTimeoutSec <Int32>]
 [-RemoteNodeSessionIdleTimeoutSec <Int32>] [-SessionThrottleLimit <Int32>]
 [-WorkflowShutdownTimeoutMSec <Int32>] [<CommonParameters>]
```

## 설명

`New-PSWorkflowExecutionOption`Cmdlet은 Windows PowerShell 워크플로 워크플로를 실행 하도록 설계 된 세션 구성 인 워크플로 세션 구성에 대 한 고급 옵션을 포함 하는 개체를 만듭니다.

**PSWorkflowExecutionOption** `New-PSWorkflowExecutionOption` 및 cmdlet과 같은 세션 구성을 만들거나 변경 하는 Cmdlet의 **sessiontypeoption** 매개 변수 값으로 생성 되는 psworkflowexecutionoption 개체를 사용할 수 있습니다 `Register-PSSessionConfiguration` `Set-PSSessionConfiguration` .

Cmdlet의 각 매개 변수는 `New-PSWorkflowExecutionOption` cmdlet이 반환 하는 워크플로 세션 구성 옵션 개체의 속성을 나타냅니다. 매개 변수를 생략하면 이 cmdlet은 속성의 기본값으로 개체를 만듭니다.

`New-PSWorkflowExecutionOption`이 cmdlet은 Windows PowerShell 워크플로 기능의 일부입니다.

또한 이 명령에 워크플로 일반 매개 변수를 추가할 수 있습니다. 워크플로 일반 매개 변수에 대 한 자세한 내용은 [about_WorkflowCommonParameters](About/about_WorkflowCommonParameters.md)를 참조 하세요.

이 cmdlet은 Windows PowerShell 3.0에서 도입되었습니다.

## 예제

### 예제 1: 워크플로 옵션 개체 만들기

```powershell
New-PSWorkflowExecutionOption -MaxSessionsPerWorkflow 10 -MaxDisconnectedSessions 200
```

```Output
SessionThrottleLimit                       : 100
PersistencePath                            : C:\Users\User01\AppData\Local\Microsoft\Windows\PowerShell\WF\PS
MaxPersistenceStoreSizeGB                  : 10
PersistWithEncryption                      : False
MaxRunningWorkflows                        : 30
AllowedActivity                            : {PSDefaultActivities}
OutOfProcessActivity                       : {InlineScript}
EnableValidation                           : True
MaxDisconnectedSessions                    : 200
MaxConnectedSessions                       : 100
MaxSessionsPerWorkflow                     : 10
MaxSessionsPerRemoteNode                   : 5
MaxActivityProcesses                       : 5
ActivityProcessIdleTimeoutSec              : 60
RemoteNodeSessionIdleTimeoutSec            : 60
WorkflowShutdownTimeoutMSec                : 500
```

이 명령은 cmdlet을 사용 하 여 `New-PSWorkflowExecutionOption` **Maxsessionsperworkflow** 값을 10으로 늘리고 **MaxDisconnectedSessions** 값을 200로 줄입니다.

출력은 이 cmdlet에서 반환하는 개체를 보여 줍니다.

### 예제 2: 워크플로 옵션 개체 사용

```powershell
# Create a Workflow Options object and save it in a variable
$wo = New-PSWorkflowExecutionOption -MaxSessionsPerWorkflow 10 -MaxDisconnectedSessions 200
# Create the ITWorkflow session configuration
Register-PSSessionConfiguration -Name ITWorkflows -SessionTypeOption $wo -Force
```

```Output
    WSManConfig: Microsoft.WSMan.Management\WSMan::localhost\Plugin

Type            Keys                                Name
----            ----                                ----
Container       {Name=ITWorkflows}                  ITWorkflows
```

```powershell
Get-PSSessionConfiguration ITWorkflows | Format-List -Property *
```

```Output
Architecture                  : 64
Filename                      : %windir%\system32\pwrshplugin.dll
ResourceUri                   : http://schemas.microsoft.com/powershell/ITWorkflows
MaxConcurrentCommandsPerShell : 1000
allowedactivity               : PSDefaultActivities
UseSharedProcess              : false
ProcessIdleTimeoutSec         : 0
xmlns                         : http://schemas.microsoft.com/wbem/wsman/1/config/PluginConfiguration
MaxConcurrentUsers            : 5
maxsessionsperworkflow        : 10
lang                          : en-US
sessionconfigurationdata      : <SessionConfigurationData>
                                    <Param Name='PrivateData'>
                                        <PrivateData>
                                            <ParamName='enablevalidation' Value='True'/>
                                            <Param Name='allowedactivity'Value='PSDefaultActivities' />
                                            <Param Name='outofprocessactivity' Value='InlineScript'/>
                                            <Param Name='maxdisconnectedsessions' Value='200' />
                                            <ParamName='maxsessionsperworkflow' Value='10'/>
                                        </PrivateData>
                                    </Param>
                                </SessionConfigurationData>
SupportsOptions               : true
ExactMatch                    : true
RunAsUser                     :
IdleTimeoutms                 : 7200000
PSVersion                     : 3.0
OutputBufferingMode           : Block
AutoRestart                   : false
MaxShells                     : 25
MaxMemoryPerShellMB           : 1024
MaxIdleTimeoutms              : 43200000
outofprocessactivity          : InlineScript
SDKVersion                    : 2
Name                          : ITWorkflows
XmlRenderingType              : text
Capability                    : {Shell}
RunAsPassword                 :
MaxProcessesPerShell          : 15
enablevalidation              : True
Enabled                       : True
maxdisconnectedsessions       : 200
MaxShellsPerUser              : 25
Permission                    :
```

처음 두 명령은 새 세션 구성 개체를 만들어 등록 합니다.

세 번째 명령은이 cmdlet을 사용 하 여 `Get-PSSessionConfiguration` ITWorkflows 세션 구성 가져오기 및를 사용 하 여 `Format-List` 세션 구성의 모든 속성을 목록으로 표시 합니다. 출력은 세션 구성의 워크플로 옵션을 보여 줍니다. 특히, 세션 구성에는 **MaxSessionsPerWorkflow** 속성의 값이 10으로 설정되어 있고 **MaxDisconnectedSessions** 속성의 값이 200으로 설정되어 있습니다.

## PARAMETERS

### -ActivityProcessIdleTimeoutSec

각 활동 호스트 프로세스가 유휴 상태가 된 후 유지되는 기간을 결정합니다. 간격이 만료되면 프로세스가 닫힙니다.

값을 초 단위로 입력하세요. 기본값은 60입니다.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 60
Accept pipeline input: False
Accept wildcard characters: False
```

### -AllowedActivity

세션에서 실행이 허용된 활동을 지정합니다.

네임 스페이스의 정규화 된 활동 이름 (예:)을 입력 `Microsoft.Powershell.HyperV.Activities.*` 합니다.
와일드카드 문자가 지원됩니다. 기본값 **PSDefaultActivities** 는 기본 제공 Windows Workflow Foundation 활동 및 Windows PowerShell 핵심 cmdlet을 나타내는 활동을 포함합니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: PSDefaultActivities
Accept pipeline input: False
Accept wildcard characters: False
```

### -EnableValidation

세션의 모든 워크플로 활동이 허용된 활동 목록에 포함되는지 확인합니다.

기본값은 True입니다. 유효성 검사를 사용 하지 않도록 설정 하려면 다음 명령 형식을 사용 `-EnableValidation:$false` 합니다..

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: True
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaxActivityProcesses

워크플로 활동을 지원하기 위해 세션에서 만들 수 있는 최대 프로세스 수를 지정합니다. 기본값은 5입니다.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 5
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaxConnectedSessions

작동 상태인 원격 세션의 최대 수를 지정합니다. 이 할당량은 모든 원격 노드(대상 컴퓨터)에 연결된 세션에 적용됩니다. 기본값은 100입니다.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 100
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaxDisconnectedSessions

연결이 끊어진 상태인 원격 세션의 최대 수를 지정합니다. 이 할당량은 모든 원격 노드(대상 컴퓨터)에 연결된 세션에 적용됩니다. 기본값은 1000입니다.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 1000
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaxPersistenceStoreSizeGB

세션에서 실행되는 워크플로에 할당된 지속성 저장소의 최대 크기(GB)를 지정합니다. 크기를 초과하면 지속성 저장소가 확장되어 모든 영구 데이터를 저장하지만 경고가 표시되고 워크플로 이벤트 로그에 메시지가 기록됩니다. 기본값은 10입니다.

지속성 저장소는 모든 워크플로 작업의 데이터를 포함합니다. 데이터를 저장할 수 있는 기능을 통해 작업이 상태 손실 없이 다시 시작될 수 있습니다.

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 10
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaxRunningWorkflows

세션에서 동시에 실행될 수 있는 최대 워크플로 수를 지정합니다.
기본값은 30입니다.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 30
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaxSessionsPerRemoteNode

각 원격 노드(대상 컴퓨터)에 연결할 수 있는 최대 세션 수를 지정합니다. 기본값은 5입니다.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 5
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaxSessionsPerWorkflow

각 워크플로를 지원하기 위해 만들 수 있는 최대 세션 수를 지정합니다. 기본값은 5입니다.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 5
Accept pipeline input: False
Accept wildcard characters: False
```

### -OutOfProcessActivity

out-of-process를 실행한 허용된 활동( **AllowedActivities** 매개 변수로 지정됨)을 확인합니다. 기본값은 **InlineScript** 입니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: InlineScript
Accept pipeline input: False
Accept wildcard characters: False
```

### -PersistencePath

워크플로 상태 및 데이터를 저장할 디스크의 위치를 지정합니다. 워크플로 상태 및 데이터를 저장하면 워크플로를 일시 중단했다가 다시 시작하고, 중단 및 네트워크 오류에서 워크플로를 복구할 수 있습니다.

기본값은 `$env:LocalAppData\Microsoft\Windows\PowerShell\WF\PS`입니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -PersistWithEncryption

워크플로가 지 속성 저장소의 데이터를 암호화 함을 나타냅니다. 네트워크 공유에 지속성 데이터를 저장할 때 이 기능 사용을 고려하세요.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: $env:LocalAppData\Microsoft\Windows\PowerShell\WF\PS
Accept pipeline input: False
Accept wildcard characters: False
```

### -RemoteNodeSessionIdleTimeoutSec

원격 노드(대상 컴퓨터)에 연결된 세션이 유지되는 기간을 지정합니다(유휴 상태인 경우).

값을 초 단위로 입력하세요. 기본값은 60입니다.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 60
Accept pipeline input: False
Accept wildcard characters: False
```

### -SessionThrottleLimit

세션에서 시작된 모든 워크플로를 지원하기 위해 만드는 작업 수를 지정합니다. 기본값은 100입니다.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 100
Accept pipeline input: False
Accept wildcard characters: False
```

### -WorkflowShutdownTimeoutMSec

세션의 모든 워크플로가 강제로 일시 중단된 후 세션이 유지되는 기간을 지정합니다. 시간 제한이 만료되면 모든 워크플로가 아직 일시 중단되지 않은 경우에도 Windows PowerShell에서 세션을 닫습니다.

값을 밀리초 단위로 입력하세요.
기본값은 500입니다.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 500
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.

## 입력

### 없음

이 cmdlet에 입력을 파이프할 수 없습니다.

## 출력

### Microsoft. PowerShell. PSWorkflowExecutionOption

## 참고

옵션으로 설정된 최대값을 초과하면 매개 변수 설명에 다른 설명이 없는 한 세션에 다른 인스턴스를 만드는 명령은 실패합니다. 예를 들어 **MaxConnectedSessions** 값이 100이라고 가정합니다. 그러면 원격 노드(대상 컴퓨터)에 대한 101번째 세션을 만드는 명령은 실패합니다.

세션 구성 개체의 속성은 세션 구성에 대해 설정된 옵션과 해당 옵션 값에 따라 달라집니다. 또한 세션 구성 파일을 사용하는 세션 구성에는 추가 속성이 있습니다.

특히, **PSWorkflowExecutionOptions** 개체가 포함된 세션 구성의 속성은 워크플로 옵션 값에 따라 달라집니다. 예를 들어 세션 구성에 **SessionThrottleLimit** 속성에 대해 기본값이 아닌 값을 설정하는 **PSWorkflowExecutionOptions** 개체가 포함된 경우 세션 구성에 **SessionThrottleLimit** 속성이 포함됩니다. 그러지 않으면 이러한 속성을 포함하지 않습니다.

## 관련 링크

[New-PSWorkflowSession](New-PSWorkflowSession.md)

[about_Workflows](../PSWorkflow/About/about_Workflows.md)

[about_WorkflowCommonParameters](About/about_WorkflowCommonParameters.md)
