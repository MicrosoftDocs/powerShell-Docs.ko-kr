---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 10/25/2019
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/register-scheduledjob?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-ScheduledJob
ms.openlocfilehash: 89887474142490a71d372577576fb0059b4ff12e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93213417"
---
# Register-ScheduledJob

## 개요
예약 된 작업을 만듭니다.

## SYNTAX

### ScriptBlock (기본값)

```
Register-ScheduledJob [-ScriptBlock] <ScriptBlock> [-Name] <String>
 [-Trigger <ScheduledJobTrigger[]>] [-InitializationScript <ScriptBlock>] [-RunAs32]
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-ScheduledJobOption <ScheduledJobOptions>] [-ArgumentList <Object[]>] [-MaxResultCount <Int32>]
 [-RunNow] [-RunEvery <TimeSpan>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### FilePath

```
Register-ScheduledJob [-FilePath] <String> [-Name] <String> [-Trigger <ScheduledJobTrigger[]>]
 [-InitializationScript <ScriptBlock>] [-RunAs32] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-ScheduledJobOption <ScheduledJobOptions>]
 [-ArgumentList <Object[]>] [-MaxResultCount <Int32>] [-RunNow] [-RunEvery <TimeSpan>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## 설명

`Register-ScheduledJob`Cmdlet은 로컬 컴퓨터에 예약 된 작업을 만듭니다.

예약 된 작업은 일회성 또는 되풀이 일정에 따라 자동으로 시작 될 수 있는 Windows PowerShell 백그라운드 작업입니다. 예약 된 작업은 디스크에 저장 되 고 작업 스케줄러에 등록 됩니다.
작업은 작업 스케줄러에서 관리 하거나 Windows PowerShell에서 예약 된 작업 cmdlet을 사용 하 여 관리할 수 있습니다.

예약 된 작업이 시작 되 면 예약 된 작업의 인스턴스를 만듭니다. 예약된 작업 인스턴스는 결과가 디스크에 저장된다는 점을 제외하고 Windows PowerShell 백그라운드 작업과 같습니다. 작업 cmdlet (예:, 및)을 사용 `Start-Job` `Get-Job` 하 여 `Receive-Job` 작업 인스턴스의 결과를 시작, 확인 및 가져올 수 있습니다.

`Register-ScheduledJob`를 사용 하 여 새 예약 된 작업을 만듭니다. 예약 된 작업이 실행 하는 명령을 지정 하려면 **ScriptBlock** 매개 변수를 사용 합니다. 작업이 실행 하는 스크립트를 지정 하려면 **FilePath** 매개 변수를 사용 합니다.

Windows PowerShell-예약 된 작업은 작업 스케줄러에서 예약 된 작업에 사용 하는 것과 동일한 작업 트리거 및 작업 옵션을 사용 합니다.

의 **Trigger** 매개 변수는 `Register-ScheduledJob` 작업을 시작 하는 하나 이상의 작업 트리거를 추가 합니다. **Trigger** 매개 변수는 선택 사항 이므로 예약 된 작업을 만들고, 나중에 작업 트리거를 추가 하 고, **runnow** 매개 변수를 추가 하 여 즉시 작업을 시작 하거나, cmdlet을 사용 하 여 `Start-Job` 언제 든 지 작업을 즉시 시작 하거나, instead of 트리거된 예약 된 작업을 다른 작업의 템플릿으로 저장할 수 있습니다.

**Options** 매개 변수를 사용하면 예약된 작업에 대한 옵션 설정을 사용자 지정할 수 있습니다. **옵션** 매개 변수는 선택 사항 이므로 예약 된 작업을 만들 때 작업 옵션을 설정 하거나 언제 든 지 변경할 수 있습니다. 작업 옵션 설정에 따라 예약된 작업이 실행되지 않을 수 있으므로 작업 옵션을 검토하여 신중하게 설정합니다.

`Register-ScheduledJob` 는 Windows PowerShell에 포함 된 **PSScheduledJob** 모듈의 작업 예약 cmdlet 컬렉션 중 하나입니다.

예약 된 작업에 대 한 자세한 내용은 **PSScheduledJob** 모듈의 about 문서를 참조 하세요.
**PSScheduledJob** 모듈을 가져온 다음를 입력 `Get-Help about_Scheduled*` 하거나 [about_Scheduled_Jobs](./about/about_scheduled_jobs.md)를 참조 하세요.

이 cmdlet은 Windows PowerShell 3.0에서 도입되었습니다.

## 예제

### 예제 1: 예약 된 작업 만들기

이 예에서는 로컬 컴퓨터에 예약 된 작업을 만듭니다.

```powershell
Register-ScheduledJob -Name "Archive-Scripts" -ScriptBlock {
  Get-ChildItem $home\*.ps1 -Recurse |
    Copy-Item -Destination "\\Server\Share\PSScriptArchive"
}
```

`Register-ScheduledJob`**Name** 매개 변수를 사용 하 여 **보관-스크립트** 예약 된 작업을 만듭니다.
**ScriptBlock** 매개 변수는 `Get-ChildItem` `$home` 디렉터리에서 파일을 재귀적으로 검색 하는를 실행 합니다 `.ps1` . `Copy-Item`Cmdlet은 **Destination** 매개 변수로 지정 된 디렉터리에 파일을 복사 합니다.

예약 된 작업은 트리거를 포함 하지 않으므로 자동으로 시작 되지 않습니다. 를 사용 하 여 작업 트리거 `Add-JobTrigger` 를 추가 하거나, cmdlet을 사용 `Start-Job` 하 여 요청 시 작업을 시작 하거나, 예약 된 작업을 다른 예약 된 작업의 템플릿으로 사용할 수 있습니다.

### 예 2: 트리거와 사용자 지정 옵션을 사용 하 여 예약 된 작업 만들기

이 예제에서는 작업 트리거와 사용자 지정 작업 옵션이 있는 예약된 작업을 만드는 방법을 보여 줍니다.

```powershell
$O = New-ScheduledJobOption -WakeToRun -StartIfIdle -MultipleInstancePolicy Queue
$T = New-JobTrigger -Weekly -At "9:00 PM" -DaysOfWeek Monday -WeeksInterval 2
$path = "\\Srv01\Scripts\UpdateVersion.ps1"
Register-ScheduledJob -Name "UpdateVersion" -FilePath $path -ScheduledJobOption $O -Trigger $T
```

`$O`변수는 cmdlet이 만든 작업 옵션 개체를 저장 `New-ScheduledJobOption` 합니다. 옵션은 컴퓨터가 유휴 상태가 아닌 경우에도 예약 된 작업을 시작 하 고, 필요한 경우 작업을 실행 하기 위해 컴퓨터의 절전 모드를 해제 하 고, 작업의 여러 인스턴스를 일련의 작업으로 실행할 수 있도록 허용 합니다.

`$T`변수는 cmdlet의 결과를 저장 `New-JobTrigger` 하 여 월요일부터 오후 9:00 마다 작업을 시작 하는 작업 트리거를 만듭니다.

`$path`변수는 스크립트 파일에 대 한 경로를 저장 `UpdateVersion.ps1` 합니다.

`Register-ScheduledJob`**Name** 매개 변수를 사용 하 여 예약 된 **updateversion** 작업을 만듭니다.
**FilePath** 매개 변수는를 사용 하 여 `$path` 작업이 실행 하는 스크립트를 지정 합니다. **Set-scheduledjoboption** 매개 변수는에 저장 된 작업 옵션을 사용 합니다 `$O` . **Trigger** 매개 변수는에 저장 된 작업 트리거를 사용 합니다 `$T` .

### 예 3: 해시 테이블을 사용 하 여 트리거 및 예약 된 작업 옵션 지정

이 예는 예제 2의 명령과 동일한 결과를 가집니다. **트리거** 및 **set-scheduledjoboption** 매개 변수의 값을 지정 하는 해시 테이블을 사용 하 여 예약 된 작업을 만듭니다. `$O` `$T` 예 2에 정의 된 및 변수가 해시 테이블로 바뀝니다.

```powershell
$T = @{
  Frequency="Weekly"
  At="9:00PM"
  DaysOfWeek="Monday"
  Interval=2
}
$O = @{
  WakeToRun=$true
  StartIfNotIdle=$false
  MultipleInstancePolicy="Queue"
}
Register-ScheduledJob -Trigger $T -ScheduledJobOption $O -Name UpdateVersion -FilePath "\\Srv01\Scripts\Update-Version.ps1"
```

### 예제 4: 원격 컴퓨터에서 예약 된 작업 만들기

이 예제에서는 **energydata.ps1** 예약 된 작업이 여러 원격 컴퓨터에 만들어집니다. 예약 된 작업은 원시 데이터를 수집 하 여 원격 컴퓨터의 실행 중인 로그에 저장 하는 스크립트를 실행 합니다.

```powershell
$Cred = Get-Credential
$O = New-ScheduledJobOption -WakeToRun -StartIfIdle -MultipleInstancePolicy Queue
$T = New-JobTrigger -Weekly -At "9:00 PM" -DaysOfWeek Monday -WeeksInterval 2
Invoke-Command -ComputerName (Get-Content Servers.txt) -Credential $Cred -ScriptBlock {
  $params = @{
      Name = "Get-EnergyData"
      FilePath = "\\Srv01\Scripts\Get-EnergyData.ps1"
      ScheduledJobOption = $using:O
      Trigger = $using:T
  }
  Register-ScheduledJob @params
}
```

`$Cred`변수는 예약 된 작업을 만들 수 있는 권한이 있는 사용자에 대해 **PSCredential** 개체에 자격 증명을 저장 합니다. `$O`변수는를 사용 하 여 만든 작업 옵션을 저장 `New-ScheduledJobOption` 합니다. `$T`변수는를 사용 하 여 만든 작업 트리거를 저장 `New-JobTrigger` 합니다.

`Invoke-Command`Cmdlet은 **ComputerName** 매개 변수를 사용 하 여 파일에서 서버 이름 목록을 가져옵니다 `Servers.txt` . **Credential** 매개 변수는에 저장 된 자격 증명 개체를 가져옵니다 `$Cred` .
**ScriptBlock** 매개 변수는 `Register-ScheduledJob` 파일의 컴퓨터에서 명령을 실행 합니다 `Servers.txt` .

에 대 한 매개 변수는에 `Register-ScheduledJob` 의해 정의 됩니다 `$params` . **Name** 매개 변수는 각 원격 컴퓨터에서 작업 이름을 **energydata.ps1** 로 지정 합니다. **FilePath** 는 스크립트의 위치를 제공 합니다 `EnergyData.ps1` . 스크립트는 모든 참여 컴퓨터에서 사용할 수 있는 파일 서버에 있습니다. 작업은의 작업 트리거와의 작업 옵션에 지정 된 일정에 따라 실행 됩니다 `$T` `$O` .

이 `Register-ScheduledJob @params` 명령은 스크립트 블록에서 매개 변수를 사용 하 여 예약 된 작업을 만듭니다.

### 예 5: 원격 컴퓨터에서 스크립트를 실행 하는 예약 된 작업 만들기

이 예에서는 로컬 컴퓨터에 **CollectEnergyData** 예약 된 작업을 만듭니다. 작업은 여러 원격 컴퓨터에서 실행 됩니다.

```powershell
$Admin = Get-Credential
$T = New-JobTrigger -Weekly -At "9:00 PM" -DaysOfWeek Monday -WeeksInterval 2
Register-ScheduledJob -Name "CollectEnergyData" -Trigger $T -MaxResultCount 99 -ScriptBlock {
  $params = @{
    AsJob = $true
    ComputerName = (Get-Content Servers.txt)
    FilePath = '\\Srv01\Scripts\Get-EnergyData.ps1'
    Credential = $using:Admin
    Authentication = 'CredSSP'
  }
  Invoke-Command @params
}
```

`$Admin`변수는 **PSCredential** 개체에서 명령을 실행할 수 있는 권한이 있는 사용자에 대 한 자격 증명을 저장 합니다. `$T`변수는를 사용 하 여 만든 작업 트리거를 저장 `New-JobTrigger` 합니다.

이 `Register-ScheduledJob` cmdlet은 **Name** 매개 변수를 사용 하 여 로컬 컴퓨터에서 **CollectEnergyData** 예약 된 작업을 만듭니다. **Trigger** 매개 변수는의 작업 트리거를 지정 하 `$T` 고 **MaxResultCount** 매개 변수는 저장 된 결과의 수를 99로 늘립니다.

**ScriptBlock** 매개 변수는 `Invoke-Command` 를 사용 하 여 매개 변수를 정의 합니다 `$params` . **AsJob** 매개 변수는 `Energydata.ps1` 원격 컴퓨터에서 스크립트가 실행 되는 경우에도 로컬 컴퓨터에 백그라운드 작업 개체를 만듭니다. **ComputerName** 매개 변수는 파일에서 서버 이름 목록을 가져옵니다 `Servers.txt` . **Credential** 매개 변수는 원격 컴퓨터에서 스크립트를 실행할 수 있는 권한을 가진 사용자 계정을 지정 합니다. 그리고 **인증** 매개 변수는 위임 된 자격 증명을 허용 하는 **CredSSP** 값을 지정 합니다.

는 `Invoke-Command @params` 스크립트 블록에서 매개 변수를 사용 하 여 명령을 실행 합니다.

## PARAMETERS

### -ArgumentList

**FilePath** 매개 변수에 지정된 스크립트의 매개 변수 값이나 **ScriptBlock** 매개 변수에 지정된 명령의 값을 지정합니다.

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -인증

사용자 자격 증명을 인증하는 데 사용되는 메커니즘을 지정합니다. 기본값은 Default입니다.

이 매개 변수에 허용되는 값은 다음과 같습니다.

- 기본값
- Basic
- Credssp
- 다이제스트
- Kerberos
- Negotiate
- NegotiateWithImplicitCredential

이 매개 변수 값에 대 한 자세한 내용은 [Authenticationmechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)을 참조 하십시오.

> [!CAUTION]
> 사용자 자격 증명이 인증할 원격 컴퓨터로 전달되는 CredSSP(Credential Security Service Provider) 인증은 원격 네트워크 공유 액세스 등 두 개 이상의 리소스에서 인증이 필요한 명령에 사용됩니다. 이렇게 하면 원격 작업의 보안 위험이 커집니다. 원격 컴퓨터가 손상된 경우 이 컴퓨터로 전달된 자격 증명을 사용하여 네트워크 세션을 제어할 수 있습니다.

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: (All)
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

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

### -Credential

예약된 작업을 실행할 권한이 있는 사용자 계정을 지정합니다. 기본값은 현재 사용자입니다.

**User01** 또는 **Domain01\User01** 과 같은 사용자 이름을 입력 하거나, cmdlet의 개체와 같은 **PSCredential** 개체를 입력 합니다 `Get-Credential` . 사용자 이름만 입력 하면 암호를 입력 하 라는 메시지가 표시 됩니다.

자격 증명은 [PSCredential](/dotnet/api/system.management.automation.pscredential) 개체에 저장 되 고 암호는 [SecureString](/dotnet/api/system.security.securestring)으로 저장 됩니다.

> [!NOTE]
> **Securestring** 데이터 보호에 대 한 자세한 [내용은 참조 하십시오](/dotnet/api/system.security.securestring#how-secure-is-securestring).

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

### -FilePath

예약된 작업이 실행하는 스크립트를 지정합니다. 로컬 컴퓨터에 있는 파일의 경로를 입력 `.ps1` 합니다. 스크립트 매개 변수의 기본값을 지정하려면 **ArgumentList** 매개 변수를 사용합니다.
모든 `Register-ScheduledJob` 명령은 **ScriptBlock** 또는 **FilePath** 매개 변수를 사용 해야 합니다.

```yaml
Type: System.String
Parameter Sets: FilePath
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -또한 initializationscript

Windows PowerShell 스크립트에 대 한 정규화 된 경로를 지정 합니다 ( `.ps1` ). 초기화 스크립트는 백그라운드 작업에 대해 만들어진 세션에서 **ScriptBlock** 매개 변수에 지정된 명령이나 **FilePath** 매개 변수에 지정된 스크립트보다 먼저 실행됩니다. 초기화 스크립트를 사용하여 파일, 함수 또는 별칭 추가, 디렉터리 만들기, 필수 조건 확인 등 세션을 구성할 수 있습니다.

주요 작업 명령을 실행하는 스크립트를 지정하려면 **FilePath** 매개 변수를 사용합니다.

초기화 스크립트에서 종료 되지 않는 오류가 발생 해도 오류가 발생 하면 예약 된 작업의 현재 인스턴스가 실행 되지 않으며 상태는 **실패** 입니다.

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaxResultCount

예약된 작업에 대해 유지 관리할 작업 결과 항목 수를 지정합니다. 기본값은 32입니다.

Windows PowerShell은 트리거된 각 예약된 작업 인스턴스의 실행 기록과 결과를 디스크에 저장합니다. 이 매개 변수 값은 이 예약된 작업에 대해 저장되는 작업 인스턴스 결과 수를 결정합니다. 작업 인스턴스 결과 수가 이 값을 초과할 경우 Windows PowerShell은 가장 오래된 작업 인스턴스 결과를 삭제하여 최신 작업 인스턴스 결과를 저장할 공간을 확보합니다.

작업 실행 기록과 작업 결과는 `$home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs\<JobName>\Output\<Timestamp>`
작업이 생성 된 컴퓨터의 디렉터리입니다. 실행 기록을 보려면 cmdlet을 사용 합니다 `Get-Job` . 작업 결과를 가져오려면 cmdlet을 사용 합니다 `Receive-Job` .

**MaxResultCount** 매개 변수는 예약된 작업의 ExecutionHistoryLength 속성 값을 설정합니다.

현재 실행 기록과 작업 결과를 삭제 하려면 cmdlet의 **ClearExecutionHistory** 매개 변수를 사용 합니다 `Set-ScheduledJob` .

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 32
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

예약된 작업의 이름을 지정합니다. 이 이름은 시작된 모든 예약된 작업 인스턴스에도 사용됩니다. 이름은 컴퓨터에서 고유해야 합니다. 이 매개 변수는 필수적 요소입니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -체제가 있어도 runas32

32비트 프로세스로 예약된 작업을 실행합니다.

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

### -RunEvery

작업 실행 빈도를 지정 하는 데 사용 됩니다. 예를 들어이 옵션을 사용 하 여 15 분 마다 작업을 실행할 수 있습니다.

```yaml
Type: System.TimeSpan
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RunNow

Cmdlet이 실행 되는 즉시 작업을 시작 `Register-ScheduledJob` 합니다. 이 매개 변수는 등록 후 즉시 Windows PowerShell 스크립트를 실행 하기 위해 작업 스케줄러를 트리거할 필요가 없으며 사용자가 시작 날짜 및 시간을 지정 하는 트리거를 만들 필요가 없습니다.

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

### -Set-scheduledjoboption

예약된 작업에 대한 옵션을 설정합니다. Cmdlet을 사용 하 여 만든 개체 또는 해시 테이블 값과 같은 **ScheduledJobOptions** 개체를 입력 `New-ScheduledJobOption` 합니다.

예약 작업을 등록할 때 예약 된 작업에 대 한 옵션을 설정 하거나 또는 cmdlet을 사용 하 여 옵션을 변경할 수 있습니다 `Set-ScheduledJobOption` `Set-ScheduledJob` .

많은 옵션과 해당 기본값은 예약된 작업의 실행 여부와 시기를 결정합니다. 작업을 예약하기 전에 이러한 옵션을 검토해야 합니다. 기본 값을 포함 하 여 예약 된 작업 옵션에 대 한 설명은를 참조 하십시오 `New-ScheduledJobOption` .

해시 테이블을 제출하려면 다음 키를 사용합니다. 다음 해시 테이블에 키와 해당 기본값이 나와 있습니다.

`@{StartIfOnBattery=$False; StopIfGoingOnBattery=$True; WakeToRun=$False; StartIfNotIdle=$False; IdleDuration="00:10:00"; IdleTimeout="01:00:00"; StopIfGoingOffIdle=$True; RestartOnIdleResume=$False; ShowInTaskScheduler=$True; RunElevated=$False; RunWithoutNetwork=$False; DoNotAllowDemandStart=$False; MultipleInstancePolicy="IgnoreNew"}`

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobOptions
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ScriptBlock

예약된 작업이 실행하는 명령을 지정합니다. 명령을 중괄호 ()로 묶어 `{}` 스크립트 블록을 만듭니다. 명령 매개 변수의 기본값을 지정하려면 **ArgumentList** 매개 변수를 사용합니다.

모든 `Register-ScheduledJob` 명령은 **ScriptBlock** 또는 **FilePath** 매개 변수를 사용 해야 합니다.

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlock
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -트리거

예약된 작업의 트리거를 지정합니다. Cmdlet이 반환 하 **ScheduledJobTrigger** 는 개체 `New-JobTrigger` 또는 작업 트리거 키 및 값의 해시 테이블 같은 ScheduledJobTrigger 개체를 하나 이상 입력 합니다.

작업 트리거는 일정 작업을 시작 합니다. 트리거는 사용자가 로그온하거나 Windows가 시작되는 경우와 같은 이벤트나 일회성 또는 되풀이 일정을 지정할 수 있습니다.

**Trigger** 매개 변수는 선택 사항입니다. 예약 된 작업을 만들 때 트리거를 추가 `Add-JobTrigger` 하거나,, `Set-JobTrigger` 또는 cmdlet을 사용 하 여 `Set-ScheduledJob` 나중에 작업 트리거를 추가 하거나 변경 하거나, cmdlet을 사용 하 여 `Start-Job` 예약 된 작업을 즉시 시작할 수 있습니다. 템플릿으로 사용되는 트리거 없는 예약된 작업을 만들어 유지 관리할 수도 있습니다.

해시 테이블을 제출 하려면 다음 키를 사용 합니다.

- **빈도** : 매일, 매주, Atstartup, atstartup
- **At** : 모든 유효한 시간 문자열
- **DaysOfWeek** -요일 이름 조합
- **Interval** -유효한 모든 빈도 간격
- **RandomDelay** : 모든 유효한 timespan 문자열
- **사용자** : 모든 유효한 사용자입니다. AtLogon 빈도 값에만 사용 됩니다.

다음은 그 예입니다. 

`@{Frequency="Once"; At="3am"; DaysOfWeek="Monday", "Wednesday"; Interval=2; RandomDelay="30minutes"; User="Domain1\User01"}`

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

cmdlet을 실행할 경우 발생하는 일을 표시합니다. Cmdlet이 실행 되지 않습니다.

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

### 없음

파이프라인에서이 cmdlet에 대 한 입력을 보낼 수 없습니다.

## 출력

### Set-scheduledjob. ScheduledJobDefinition

## 참고

각 예약 된 작업은 로컬 컴퓨터에 있는 디렉터리의 하위 디렉터리에 저장 됩니다 `$home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs` .
하위 디렉터리는 예약 된 작업에 대해 이름이 지정 되며 예약 된 작업에 대 한 XML 파일과 실행 기록 레코드를 포함 합니다. 디스크의 예약 된 작업에 대 한 자세한 내용은 [about_Scheduled_Jobs_Advanced](./about/about_scheduled_jobs_advanced.md)를 참조 하세요.

Windows PowerShell에서 만든 예약 된 작업은 작업 스케줄러 폴더의 작업 스케줄러에 나타납니다 `Library\Microsoft\Windows\PowerShell\ScheduledJobs` . 작업 스케줄러를 사용하여 예약된 작업을 보고 편집할 수 있습니다.

작업 스케줄러, **schtasks.exe** 명령줄 도구 및 작업 스케줄러 cmdlet을 사용 하 여 예약 된 작업 cmdlet으로 만든 예약 된 작업을 관리할 수 있습니다. 그러나 작업 스케줄러에서 만든 작업은 예약 된 작업 cmdlet을 사용 하 여 관리할 수 없습니다.

예약된 작업 명령이 실패할 경우 Windows PowerShell에서 오류 메시지를 반환합니다. 그러나 작업 스케줄러 실행 하려고 할 때 작업이 실패 하면 Windows PowerShell에서 오류를 사용할 수 없습니다.

예약 된 작업이 실행 되지 않으면 다음 방법을 사용 하 여 이유를 확인 합니다.

- 작업 트리거가 제대로 설정 되었는지 확인 합니다.
  - 작업 옵션에 설정 된 조건이 충족 되는지 확인 합니다.
- 작업이 실행 되는 사용자 계정에 작업의 명령 또는 스크립트를 실행할 수 있는 권한이 있는지 확인 합니다.
- 작업 스케줄러 기록에서 오류를 확인 합니다.
- 작업 스케줄러 이벤트 로그에서 오류를 확인 하십시오.

자세한 내용은 [about_Scheduled_Jobs_Troubleshooting](./about/about_scheduled_jobs_troubleshooting.md)를 참조 하세요.

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
