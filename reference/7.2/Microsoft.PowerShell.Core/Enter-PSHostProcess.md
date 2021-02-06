---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 07/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enter-pshostprocess?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enter-PSHostProcess
ms.openlocfilehash: 85cbc9d012781873dddaf2a7d220a0e478dcbda2
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599760"
---
# Enter-PSHostProcess

## 개요
에 연결 하 고 로컬 프로세스를 사용 하 여 대화형 세션으로 전환 합니다.

## SYNTAX

### ProcessIdParameterSet (기본값)

```
Enter-PSHostProcess [-Id] <Int32> [[-AppDomainName] <String>] [<CommonParameters>]
```

### ProcessParameterSet

```
Enter-PSHostProcess [-Process] <Process> [[-AppDomainName] <String>] [<CommonParameters>]
```

### ProcessNameParameterSet

```
Enter-PSHostProcess [-Name] <String> [[-AppDomainName] <String>] [<CommonParameters>]
```

### PSHostProcessInfoParameterSet

```
Enter-PSHostProcess [-HostProcessInfo] <PSHostProcessInfo> [[-AppDomainName] <String>]
 [<CommonParameters>]
```

### PipeNameParameterSet

```
Enter-PSHostProcess -CustomPipeName <String> [<CommonParameters>]
```

## 설명

`Enter-PSHostProcess`Cmdlet은에 연결 하 여 로컬 프로세스와의 대화형 세션으로 전환 합니다. PowerShell 6.2부터이 cmdlet은 Windows 이외의 플랫폼에서 지원 됩니다.

PowerShell을 호스트 하 고 원격 세션을 실행 하는 새 프로세스를 만드는 대신 PowerShell을 이미 실행 하 고 있는 기존 프로세스에서 원격 대화형 세션이 실행 됩니다. 지정 된 프로세스에서 원격 세션과 상호 작용 하는 경우 실행 중인 runspace를 열거 하 고 또는를 실행 하 여 디버그할 runspace를 선택할 수 있습니다 `Debug-Runspace` `Enable-RunspaceDebug` .

입력 하려는 프로세스는 PowerShell (System.Management.Automation.dll)을 호스팅해야 합니다.
프로세스가 있는 컴퓨터에서 Administrators 그룹의 구성원 이거나 프로세스를 시작 하는 스크립트를 실행 하는 사용자 여야 합니다.

디버깅할 runspace를 선택한 후 현재 명령을 실행 중이거나 디버거에서 중지 된 경우 runspace에 대 한 원격 디버그 세션이 열립니다. 그런 다음 다른 원격 세션 스크립트를 디버깅 하는 것과 같은 방법으로 runspace 스크립트를 디버그할 수 있습니다.

종료를 두 번 실행 하 여 디버깅 세션에서 프로세스와 대화형 세션을 분리 하거나 기존 디버거 quit 명령을 실행 하 여 스크립트 실행을 중지 합니다.

**Name** 매개 변수를 사용 하 여 프로세스를 지정 하 고 지정 된 이름의 프로세스가 하나만 있는 경우 프로세스가 입력 됩니다. 지정 된 이름을 가진 프로세스가 둘 이상 발견 되 면 PowerShell에서 오류를 반환 하 고 지정 된 이름의 모든 프로세스를 나열 합니다.

원격 컴퓨터의 프로세스에 대 한 연결을 지원 하기 위해 `Enter-PSHostProcess` 지정 된 원격 컴퓨터에서 cmdlet을 사용 하도록 설정 하 여 원격 PowerShell 세션 내에서 로컬 프로세스에 연결할 수 있습니다.

## 예제

### 예제 1: PowerShell ISE 프로세스 내에서 runspace 디버깅 시작

이 예에서는 powershell `Enter-PSHostProcess` 콘솔 내에서를 실행 하 여 POWERSHELL ISE 프로세스를 시작 합니다. 결과 대화형 세션에서를 실행 하 여 디버깅 하려는 runspace를 찾은 `Get-Runspace` 다음 runspace를 디버그할 수 있습니다.

```
PS C:\> Enter-PSHostProcess -Name powershell_ise
[Process:1520]: PS C:\Test\Documents>

Next, get available runspaces within the process you have entered.
PS C:\> [Process:1520]: PS C:\>  Get-Runspace
Id    Name          InstanceId                               State           Availability
--    -------       -----------                              ------          -------------
1     Runspace1     2d91211d-9cce-42f0-ab0e-71ac258b32b5     Opened          Available
2     Runspace2     a3855043-cb16-424a-a616-685360c3763b     Opened          RemoteDebug
3     MyLocalRS     2236dbd8-2105-4dec-a15a-a27d0bfaacb5     Opened          LocalDebug
4     MyRunspace    771356e9-8c44-4b70-9de5-dd17cb41e48e     Opened          Busy
5     Runspace8     3e517382-a97a-49ba-9c3c-fd21f6664288     Broken          None

The runspace objects returned by Get-Runspace also have a NoteProperty called ScriptStackTrace of
the running command stack, if available.Next, debug runspace ID 4, that is running another user's
long-running script. From the list returned from Get-Runspace, note that the runspace state is
Opened, and Availability is Busy, meaning that the runspace is still running the long-running
script.

PS C:\> [Process:1520]: PS C:\>  (Get-Runspace -Id 4).ScriptStackTrace
Command                    Arguments                           Location
-------                    ---------                           --------
MyModuleWorkflowF1         {}                                  TestNoFile3.psm1: line 6
WFTest1                    {}                                  TestNoFile2.ps1: line 14
TestNoFile2.ps1            {}                                  TestNoFile2.ps1: line 22
<ScriptBlock>              {}                                  <No file>

Start an interactive debugging session with this runspace by running the Debug-Runspace cmdlet.

PS C:\> [Process: 1520]: PS C:\>  Debug-Runspace -Id 4
Hit Line breakpoint on 'C:\TestWFVar1.ps1:83'

At C:\TestWFVar1.ps1:83 char:1
+ $scriptVar = "Script Variable"
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[Process: 1520]: [RSDBG: 4]: PS C:\> >

After you are finished debugging, allow the script to continue running without the debugger attached
by running the exit debugger command. Alternatively, you can quit the debugger with the q or Stop
commands.

PS C:\> [Process:346]: [RSDBG: 3]: PS C:\> > exit
[Process:1520]: PS C:\>

When you are finished working in the process, exit the process by running the Exit-PSHostProcess
cmdlet. This returns you to the PS C:\> prompt.

PS C:\> [Process:1520]: PS C:\>  Exit-PSHostProcess
PS C:\>
```

## PARAMETERS

### -AppDomainName

생략 된 경우 연결할 응용 프로그램 도메인 이름을 지정 합니다. **Defaultappdomain** 을 사용 합니다. `Get-PSHostProcessInfo`응용 프로그램 도메인 이름을 표시 하는 데 사용 합니다.

```yaml
Type: System.String
Parameter Sets: ProcessIdParameterSet, ProcessParameterSet, ProcessNameParameterSet, PSHostProcessInfoParameterSet
Aliases:

Required: False
Position: 1
Default value: DefaultAppDomain
Accept pipeline input: False
Accept wildcard characters: False
```

### -HostProcessInfo

PowerShell을 사용 하 여 연결할 수 있는 **exit-pshostprocessinfo** 개체를 지정 합니다. `Get-PSHostProcessInfo`를 사용 하 여 개체를 가져옵니다.

```yaml
Type: Microsoft.PowerShell.Commands.PSHostProcessInfo
Parameter Sets: PSHostProcessInfoParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Id

프로세스 ID로 프로세스를 지정 합니다. 프로세스 ID를 가져오려면 cmdlet을 실행 `Get-Process` 합니다.

```yaml
Type: System.Int32
Parameter Sets: ProcessIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

프로세스 이름으로 프로세스를 지정 합니다. 프로세스 이름을 가져오려면 cmdlet을 실행 `Get-Process` 합니다. 작업 관리자의 프로세스에 대 한 속성 대화 상자에서 프로세스 이름을 가져올 수도 있습니다.

```yaml
Type: System.String
Parameter Sets: ProcessNameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Process

프로세스 개체의 프로세스를 지정 합니다. 이 매개 변수를 사용 하는 가장 간단한 방법은 `Get-Process` 변수에 입력 하려는 프로세스를 반환 하는 명령의 결과를 저장 한 다음이 매개 변수의 값으로 변수를 지정 하는 것입니다.

```yaml
Type: System.Diagnostics.Process
Parameter Sets: ProcessParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -CustomPipeName

연결할 사용자 지정 명명 된 파이프 이름을 가져오거나 설정 합니다. 이는 일반적으로와 함께 사용 됩니다 `pwsh -CustomPipeName` .

이 매개 변수는 PowerShell 6.2에서 도입 되었습니다.

```yaml
Type: System.String
Parameter Sets: PipeNameParameterSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.Diagnostics.Process

## 출력

## 참고

`Enter-PSHostProcess` 명령을 실행 하는 PowerShell 세션의 프로세스를 시작할 수 없습니다. 그러나 실행 중인 세션과 동시에 실행 되는 다른 PowerShell 세션 또는 PowerShell ISE 세션의 프로세스를 입력할 수 있습니다 `Enter-PSHostProcess` .

`Enter-PSHostProcess` PowerShell을 호스트 하는 프로세스만 입력할 수 있습니다. 즉, PowerShell 엔진을 로드 했습니다.

프로세스 내에서 프로세스를 종료 하려면 **exit** 를 입력 한 다음 <kbd>enter</kbd>키를 누릅니다.

PowerShell 7.1 이전에는 SSH를 통한 원격 기능이 두 번째 홉 원격 세션을 지원하지 않았습니다. 해당 기능은 WinRM을 사용하는 세션으로 제한되었습니다. PowerShell 7.1을 사용하면 `Enter-PSSession` 및 `Enter-PSHostProcess`가 대화형 원격 세션 내에서 작동할 수 있습니다.

## 관련 링크

[Exit-PSHostProcess](Exit-PSHostProcess.md)

[Get-PSHostProcessInfo](Get-PSHostProcessInfo.md)

