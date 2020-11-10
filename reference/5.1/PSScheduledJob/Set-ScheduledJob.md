---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/set-scheduledjob?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-ScheduledJob
ms.openlocfilehash: 6144d9f19b86727bc09d07e94f4bcf158e3b7071
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94387909"
---
# Set-ScheduledJob

## 개요
예약된 작업을 변경합니다.

## SYNTAX

### ScriptBlock (기본값)

```
Set-ScheduledJob [-Name <String>] [-ScriptBlock <ScriptBlock>] [-Trigger <ScheduledJobTrigger[]>]
 [-InitializationScript <ScriptBlock>] [-RunAs32] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-ScheduledJobOption <ScheduledJobOptions>]
 [-InputObject] <ScheduledJobDefinition> [-MaxResultCount <Int32>] [-PassThru] [-ArgumentList <Object[]>]
 [-RunNow] [-RunEvery <TimeSpan>] [<CommonParameters>]
```

### FilePath

```
Set-ScheduledJob [-Name <String>] [-FilePath <String>] [-Trigger <ScheduledJobTrigger[]>]
 [-InitializationScript <ScriptBlock>] [-RunAs32] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-ScheduledJobOption <ScheduledJobOptions>]
 [-InputObject] <ScheduledJobDefinition> [-MaxResultCount <Int32>] [-PassThru] [-ArgumentList <Object[]>]
 [-RunNow] [-RunEvery <TimeSpan>] [<CommonParameters>]
```

### 실행

```
Set-ScheduledJob [-InputObject] <ScheduledJobDefinition> [-ClearExecutionHistory] [-PassThru]
 [<CommonParameters>]
```

## 설명
**Set-ScheduledJob** cmdlet은 작업이 실행하는 명령 또는 작업을 실행하는 데 필요한 자격 증명과 같은 예약된 작업의 속성을 변경합니다.
이 cmdlet을 사용하여 예약된 작업의 실행 기록을 지울 수도 있습니다.

이 cmdlet을 사용 하려면 먼저 Get-ScheduledJob cmdlet을 사용 하 여 예약 된 작업을 가져옵니다.
그런 다음 예약 된 작업을 **set-scheduledjob** 로 파이프 하거나 작업을 변수에 저장 하 고 *InputObject* 매개 변수를 사용 하 여 작업을 식별 합니다.
**Set-ScheduledJob** 의 나머지 매개 변수를 사용하여 작업 속성을 변경하거나 실행 기록을 지울 수 있습니다.

**Set-scheduledjob** 를 사용 하 여 예약 된 작업의 트리거 및 옵션을 변경할 수 있지만 추가 Jobtrigger, Set-jobtrigger 및 Set-ScheduledJobOption cmdlet을 사용 하면 이러한 작업을 보다 쉽게 수행할 수 있습니다.
새 예약 된 작업을 만들려면 Register-ScheduledJob cmdlet을 사용 합니다.

**Set-scheduledjob** 의 *Trigger* 매개 변수는 작업을 시작 하는 하나 이상의 작업 트리거를 추가 합니다.
*Trigger* 매개 변수는 선택 사항 이므로 예약 된 작업을 만들고, 나중에 작업 트리거를 추가 하 고, *runnow* 매개 변수를 추가 하 여 즉시 작업을 시작 하거나, Start-Job cmdlet을 사용 하 여 언제 든 지 작업을 즉시 시작 하거나, 트리거된 예약 되지 않은 작업을 다른 작업의 템플릿으로 저장할 수 있습니다.

**Set-scheduledjob** 는 Windows PowerShell에 포함 된 PSScheduledJob 모듈의 작업 예약 cmdlet 컬렉션 중 하나입니다.

예약된 작업에 대한 자세한 내용은 PSScheduledJob 모듈의 정보 항목을 참조하세요.
PSScheduledJob 모듈을 가져온 다음를 입력 `Get-Help about_Scheduled*` 하거나 about_Scheduled_Jobs를 참조 하세요.

이 cmdlet은 Windows PowerShell 3.0에서 도입되었습니다.

## 예제

### 예제 1: 작업이 실행 하는 스크립트 변경

```
PS C:\> Get-ScheduledJob -Name "Inventory"
Id         Name            Triggers        Command                                  Enabled
--         ----            --------        -------                                  -------
1          Inventory       {1}             C:\Scripts\Get-Inventory.ps1             True

The second command uses the Get-ScheduledJob cmdlet to get the Inventory scheduled job. A pipeline operator (|) sends the scheduled job to the **Set-ScheduledJob** cmdlet. The **Set-ScheduledJob** cmdlet uses the *Script* parameter to specify a new script, Get-FullInventory.ps1. The command uses the *Passthru* parameter to return the scheduled job after the change.
PS C:\> Get-ScheduledJob -Name "Inventory" | Set-ScheduledJob -FilePath "C:\Scripts\Get-FullInventory.ps1" -Passthru
Id         Name            Triggers        Command                                  Enabled
--         ----            --------        -------                                  -------
1          Inventory       {1}             C:\Scripts\Get-FullInventory.ps1         True
```

이 예제에서는 예약된 작업에서 실행되는 스크립트를 변경하는 방법을 보여 줍니다.

첫 번째 명령은 Get-ScheduledJob cmdlet을 사용 하 여 Inventory 예약 된 작업을 가져옵니다.
출력은 작업에서 Get-Inventory.ps1 스크립트를 실행함을 보여 줍니다.

이 명령은 필수가 아닙니다. 단지 스크립트 변경의 결과를 보여 주기 위해 포함되었습니다.

### 예 2: 예약 된 작업의 실행 기록 삭제

```
PS C:\> Get-ScheduledJob BackupArchive | Set-ScheduledJob -ClearExecutionHistory
```

이 명령은 BackupArchive 예약된 작업의 현재 실행 기록과 저장된 작업 결과를 삭제합니다.

이 명령은 Get-ScheduledJob cmdlet을 사용 하 여 BackupArchive 예약 된 작업을 가져옵니다.
파이프라인 연산자(|)가 작업을 **Set-ScheduledJob** cmdlet으로 보내 변경합니다.
**Set-scheduledjob** Cmdlet은 *ClearExecutionHistory* 매개 변수를 사용 하 여 실행 기록과 저장 된 결과를 삭제 합니다.

예약된 작업의 실행 기록과 저장된 작업 결과에 대한 자세한 내용은 about_Scheduled_Jobs를 참조하세요.

### 예 3: 원격 컴퓨터에서 예약 된 작업 변경

```
PS C:\> Invoke-Command -Computer "Server01, Server02" -ScriptBlock {Get-ScheduledJob | Set-ScheduledJob -InitializationScript \\SrvA\Scripts\SetForRun.ps1}
```

이 명령은 Server01 및 Server02 컴퓨터에 있는 모든 예약된 작업의 초기화 스크립트를 변경합니다.

이 명령은 Invoke-Command cmdlet을 사용 하 여 Server01 및 Server02 컴퓨터에서 명령을 실행 합니다.

원격 명령은 컴퓨터의 모든 예약 된 작업을 가져오는 Get-ScheduledJob 명령으로 시작 합니다.
예약 된 작업은 **set-scheduledjob** cmdlet으로 파이프 되며,이 cmdlet은 초기화 스크립트를 SetForRun.ps1 변경 합니다.

## PARAMETERS

### -ArgumentList
*FilePath* 매개 변수에 지정된 스크립트의 매개 변수 값이나 *ScriptBlock* 매개 변수에 지정된 명령의 값을 지정합니다.

```yaml
Type: System.Object[]
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -인증
사용자 자격 증명을 인증하는 데 사용되는 메커니즘을 지정합니다.
이 매개 변수에 허용되는 값은 다음과 같습니다.

- 기본값
- Basic
- Credssp
- 다이제스트
- Kerberos
- Negotiate
- NegotiateWithImplicitCredential

기본값은 Default입니다. 이 매개 변수 값에 대 한 자세한 내용은 PowerShell SDK에서 [Authenticationmechanism 열거](/dotnet/api/system.management.automation.runspaces.authenticationmechanism) 를 참조 하세요.

주의: 사용자의 자격 증명이 인증을 위해 원격 컴퓨터에 전달 되는 CredSSP (자격 증명 보안 지원 공급자) 인증은 원격 네트워크 공유에 액세스 하는 것과 같이 둘 이상의 리소스에서 인증이 필요한 명령에 대해 설계 되었습니다.
이렇게 하면 원격 작업의 보안 위험이 커집니다.
원격 컴퓨터가 손상된 경우 이 컴퓨터로 전달된 자격 증명을 사용하여 네트워크 세션을 제어할 수 있습니다.

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ScriptBlock, FilePath
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ClearExecutionHistory
예약된 작업의 현재 실행 기록과 저장된 결과를 삭제합니다.

작업 실행 기록과 작업 결과는 예약된 작업과 함께 작업이 만들어진 컴퓨터의 $home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs 디렉터리에 저장됩니다.
실행 기록을 보려면 Get-Job cmdlet을 사용 합니다.
작업 결과를 가져오려면 Receive-Job cmdlet을 사용하세요.

이 매개 변수는 작업 스케줄러가 Windows 이벤트 로그에 쓰는 이벤트에 영향을 주지 않으며 Windows PowerShell에서 작업 결과를 저장하도록 허용합니다.
저장되는 작업 결과 수를 관리하려면 *MaxResultCount* 매개 변수를 사용합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Execution
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential
예약된 작업을 실행할 권한이 있는 사용자 계정을 지정합니다.
기본값은 현재 사용자입니다.

User01 또는 Domain01\User01과 같은 사용자 이름을 입력 하거나 **PSCredential** 개체 (예: Get-Credential cmdlet의 개체)를 입력 합니다.
사용자 이름만 입력하면 암호를 묻는 메시지가 표시됩니다.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilePath
예약된 작업이 실행하는 스크립트를 지정합니다.
로컬 컴퓨터에 있는 .ps1 파일의 경로를 입력합니다.
스크립트 매개 변수의 기본값을 지정하려면 *ArgumentList* 매개 변수를 사용합니다.
각 예약된 작업에 *ScriptBlock* 또는 *FilePath* 값이 있어야 합니다.

```yaml
Type: System.String
Parameter Sets: FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -또한 initializationscript
Windows PowerShell 스크립트(.ps1)에 대한 정규화된 경로를 지정합니다.
초기화 스크립트는 백그라운드 작업에 대해 만들어진 세션에서 *ScriptBlock* 매개 변수에 지정된 명령이나 *FilePath* 매개 변수에 지정된 스크립트보다 먼저 실행됩니다.
초기화 스크립트를 사용하여 파일, 함수 또는 별칭 추가, 디렉터리 만들기, 필수 조건 확인 등 세션을 구성할 수 있습니다.

주요 작업 명령을 실행하는 스크립트를 지정하려면 *FilePath* 매개 변수를 사용합니다.

초기화 스크립트에서 종료 되지 않는 오류를 포함 하 여 오류를 생성 하는 경우 예약 된 작업의 현재 인스턴스가 실행 되지 않으며 상태는 실패입니다.

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject
변경할 예약된 작업을 지정합니다.
**ScheduledJobDefinition** 개체가 포함 된 변수를 입력 하거나 **ScheduledJobDefinition** 개체를 가져오는 명령 또는 식 (예: Get-ScheduledJob 명령)을 입력 합니다.
**ScheduledJobDefinition** 개체를 **set-scheduledjob** 로 파이프 할 수도 있습니다.

여러 개의 예약된 작업을 지정할 경우 **Set-ScheduledJob** 은 모든 작업에 동일한 변경을 수행합니다.

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -MaxResultCount
예약된 작업에 대해 유지 관리할 작업 결과 항목 수를 지정합니다.
기본값은 32입니다.

Windows PowerShell은 트리거된 각 예약된 작업 인스턴스의 실행 기록과 결과를 디스크에 저장합니다.
이 매개 변수 값은 이 예약된 작업에 대해 저장되는 작업 인스턴스 결과 수를 결정합니다.
작업 인스턴스 결과 수가 이 값을 초과할 경우 Windows PowerShell은 가장 오래된 작업 인스턴스 결과를 삭제하여 최신 작업 인스턴스 결과를 저장할 공간을 확보합니다.

작업 실행 기록과 작업 결과는 \\ \<JobName\> \\ \<Timestamp\> 작업이 만들어진 컴퓨터의 $home \appdata\local\microsoft\windows\powershell\scheduledjobs \\output 디렉터리에 저장 됩니다.
실행 기록을 보려면 Get-Job cmdlet을 사용 합니다.
작업 결과를 가져오려면 Receive-Job cmdlet을 사용하세요.

*MaxResultCount* 매개 변수는 예약된 작업의 ExecutionHistoryLength 속성 값을 설정합니다.

현재 실행 기록과 작업 결과를 삭제하려면 *ClearExecutionHistory* 매개 변수를 사용합니다.

```yaml
Type: System.Int32
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name
예약된 작업 및 예약된 작업 인스턴스의 새 이름을 지정합니다.
이름은 로컬 컴퓨터에서 고유해야 합니다.

변경할 예약 된 작업을 식별 하려면 *InputObject* 매개 변수를 사용 하거나 예약 된 작업을 Get-ScheduledJob에서 **set-scheduledjob** 로 파이프 합니다.

이 매개 변수는 디스크에 있는 작업 인스턴스의 이름을 변경하지 않습니다.
이 명령이 완료된 후 시작되는 작업 인스턴스에만 영향을 줍니다.

```yaml
Type: System.String
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
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

### -체제가 있어도 runas32
32비트 프로세스로 예약된 작업을 실행합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RunEvery

작업 실행 빈도를 지정 하는 데 사용 됩니다. 예를 들어이 옵션을 사용 하 여 15 분 마다 작업을 실행할 수 있습니다.

```yaml
Type: System.TimeSpan
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RunNow
**Set-scheduledjob** cmdlet이 실행 되는 즉시 작업을 시작 합니다.
이 매개 변수를 사용할 경우 등록 후 즉시 Windows PowerShell스크립트를 실행하기 위해 작업 스케줄러를 트리거할 필요가 없으며 사용자가 시작 날짜 및 시간을 지정하는 트리거를 만들지 않아도 됩니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Set-scheduledjoboption
예약된 작업에 대한 옵션을 설정합니다.
New-ScheduledJobOption cmdlet을 사용 하 여 만든 개체 또는 해시 테이블 값과 같은 **ScheduledJobOptions** 개체를 입력 합니다.

예약 된 작업을 등록할 때 예약 된 작업에 대 한 옵션을 설정 하거나 Set-ScheduledJobOption 또는 **set-scheduledjob** cmdlet을 사용 하 여 옵션을 설정 하거나 변경할 수 있습니다.

많은 옵션과 해당 기본값은 예약된 작업의 실행 여부와 시기를 결정합니다.
작업을 예약하기 전에 이러한 옵션을 검토해야 합니다.
기본 값을 포함 하 여 예약 된 작업 옵션에 대 한 자세한 내용은 Set-scheduledjoboption를 참조 하세요.

해시 테이블을 제출하려면 다음 키를 사용합니다.
다음 해시 테이블에 키와 해당 기본값이 나와 있습니다.

`@{# Power SettingsStartIfOnBattery=$False;StopIfGoingOnBattery=$True; WakeToRun=$False; # Idle SettingsStartIfNotIdle=$False; IdleDuration="00:10:00"; IdleTimeout="01:00:00"; StopIfGoingOffIdle=$True; RestartOnIdleResume=$False;# Security settingsShowInTaskScheduler=$TrueRunElevated=$False;# MiscRunWithoutNetwork=$False;DoNotAllowDemandStart=$False;MultipleInstancePolicy=IgnoreNew# Can be IgnoreNew, Parallel, Queue, StopExisting}`

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobOptions
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ScriptBlock
예약된 작업이 실행하는 명령을 지정합니다.
명령을 중괄호( { } )로 묶어 스크립트 블록을 만드세요.
명령 매개 변수의 기본값을 지정하려면 *ArgumentList* 매개 변수를 사용합니다.

모든 Register-ScheduledJob 명령은 *ScriptBlock* 또는 *FilePath* 매개 변수를 사용 해야 합니다.

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlock
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -트리거
예약된 작업의 트리거를 지정합니다.
New-JobTrigger cmdlet이 반환 하는 개체 또는 작업 트리거 키 및 값의 해시 테이블 같은 **ScheduledJobTrigger** 개체를 하나 이상 입력 합니다.

작업 트리거는 일회성 또는 되풀이 일정에 따라 또는 이벤트가 발생 하는 경우 예약 된 작업을 자동으로 시작 합니다.

작업 트리거는 선택 사항입니다.
예약 된 작업을 만들 때 트리거를 추가 하거나, Add-JobTrigger 또는 **set-scheduledjob** cmdlet을 사용 하 여 나중에 트리거를 추가 하거나, Start-Job cmdlet을 사용 하 여 예약 된 작업을 즉시 시작할 수 있습니다.
작업 트리거 없는 예약된 작업을 만들어 유지 관리할 수도 있습니다.

해시 테이블을 제출하려면 다음 키를 사용합니다.

`@{Frequency="Once" (or Daily, Weekly, AtStartup, AtLogon);At="3am"` 또는 유효한 시간 문자열입니다. `DaysOfWeek="Monday", "Wednesday"` (또는 요일 이름의 조합) `Interval=2` (또는 유효한 빈도 간격); `RandomDelay="30minutes"` (또는 유효한 timespan 문자열) `User="Domain1\User01"` 또는 모든 유효한 사용자 (AtLogon frequency 값 에서만 사용)

}

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger[]
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### Set-scheduledjob. ScheduledJobDefinition
예약된 작업을 **Set-ScheduledJob** 으로 파이프할 수 있습니다.

## 출력

### None 또는 Set-scheduledjob. ScheduledJobDefinition
*Passthru* 매개 변수를 사용할 경우 **Set-ScheduledJob** 은 변경된 예약된 작업을 반환합니다.
그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.

## 참고

## 관련 링크

[Add-JobTrigger](Add-JobTrigger.md)

[Disable-JobTrigger](Disable-JobTrigger.md)

[Disable-ScheduledJob](Disable-ScheduledJob.md)

[Enable-JobTrigger](Enable-JobTrigger.md)

[Enable-ScheduledJob](Enable-ScheduledJob.md)

[Get-JobTrigger](Get-JobTrigger.md)

[Get-ScheduledJob](Get-ScheduledJob.md)

[Get-ScheduledJobOption](Get-ScheduledJobOption.md)

[New-JobTrigger](New-JobTrigger.md)

[New-ScheduledJobOption](New-ScheduledJobOption.md)

[Register-ScheduledJob](Register-ScheduledJob.md)

[Remove-JobTrigger](Remove-JobTrigger.md)

[Set-JobTrigger](Set-JobTrigger.md)

[Set-ScheduledJob](Set-ScheduledJob.md)

[Set-ScheduledJobOption](Set-ScheduledJobOption.md)

[Unregister-ScheduledJob](Unregister-ScheduledJob.md)
