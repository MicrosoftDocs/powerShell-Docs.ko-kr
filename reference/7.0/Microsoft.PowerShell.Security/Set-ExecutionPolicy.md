---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 3/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/set-executionpolicy?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-ExecutionPolicy
ms.openlocfilehash: d3724c79f5864295c70d5addd46a8a133862d0ec
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93211225"
---
# Set-ExecutionPolicy

## 개요
Windows 컴퓨터에 대 한 PowerShell 실행 정책을 설정 합니다.

## SYNTAX

### 모두

```
Set-ExecutionPolicy [-ExecutionPolicy] <ExecutionPolicy> [[-Scope] <ExecutionPolicyScope>] [-Force]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명

`Set-ExecutionPolicy`Cmdlet은 Windows 컴퓨터에 대 한 PowerShell 실행 정책을 변경 합니다. 자세한 내용은 [about_Execution_Policies](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md)를 참조하세요.

Windows 이외의 컴퓨터에 대 한 PowerShell 6.0부터 기본 실행 정책은 **무제한** 이며 변경할 수 없습니다. `Set-ExecutionPolicy`Cmdlet을 사용할 수 있지만 PowerShell에서 지원 되지 않는 콘솔 메시지를 표시 합니다.

실행 정책은 PowerShell 보안 전략의 일부입니다. 실행 정책은 PowerShell 프로필과 같은 구성 파일을 로드 하거나 스크립트를 실행할 수 있는지 여부를 결정 합니다. 스크립트를 실행 하기 전에 디지털로 서명 해야 하는지 여부를 지정 합니다.

`Set-ExecutionPolicy`Cmdlet의 기본 범위는 **LocalMachine** 이며이는 컴퓨터를 사용 하는 모든 사용자에 게 영향을 줍니다. **LocalMachine** 에 대 한 실행 정책을 변경 하려면 **관리자 권한으로 실행** 을 사용 하 여 PowerShell을 시작 합니다.

각 범위에 대 한 실행 정책을 우선 순위에 따라 표시 하려면를 사용 `Get-ExecutionPolicy -List` 합니다. PowerShell 세션의 유효 실행 정책을 매개 변수 없이 사용 하는 것을 확인 합니다 `Get-ExecutionPolicy` .

## 예제

### 예제 1: 실행 정책 설정

이 예제에서는 로컬 컴퓨터에 대 한 실행 정책을 설정 하는 방법을 보여 줍니다.

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope LocalMachine
Get-ExecutionPolicy -List
```

```Output
        Scope ExecutionPolicy
        ----- ---------------
MachinePolicy       Undefined
   UserPolicy       Undefined
      Process       Undefined
  CurrentUser    RemoteSigned
 LocalMachine    RemoteSigned
```

`Set-ExecutionPolicy`Cmdlet은 **set-executionpolicy** 매개 변수를 사용 하 여 **RemoteSigned** 정책을 지정 합니다. **범위** 매개 변수는 기본 범위 값인 **LocalMachine** 를 지정 합니다. 실행 정책 설정을 보려면 `Get-ExecutionPolicy` **List** 매개 변수와 함께 cmdlet을 사용 합니다.

### 예 2: 그룹 정책와 충돌 하는 실행 정책 설정

이 명령은 **LocalMachine** 범위의 실행 정책을 **제한** 으로 설정 하려고 시도 합니다.
**LocalMachine** 는 더 제한적 이지만 그룹 정책와 충돌 하기 때문에 효과적인 정책이 아닙니다. **제한** 된 정책은 레지스트리 hive **HKEY_LOCAL_MACHINE** 에 기록 됩니다.

```
PS> Set-ExecutionPolicy -ExecutionPolicy Restricted -Scope LocalMachine

Set-ExecutionPolicy : PowerShell updated your local preference successfully, but the setting is
overridden by the Group Policy applied to your system. Due to the override, your shell will retain
its current effective execution policy of "AllSigned". Contact your Group Policy administrator for
more information. At line:1 char:20 + Set-ExecutionPolicy <<<< restricted

PS> Get-ChildItem -Path HKLM:\SOFTWARE\Microsoft\PowerShell\1\ShellIds

    Hive: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\PowerShell\1\ShellIds

Name                    Property
----                    --------
Microsoft.PowerShell    Path            : C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe
                        ExecutionPolicy : Restricted
ScriptedDiagnostics     ExecutionPolicy : Unrestricted
```

`Set-ExecutionPolicy`Cmdlet은 **set-executionpolicy** 매개 변수를 사용 하 여 **제한** 된 정책을 지정 합니다. **범위** 매개 변수는 기본 범위 값인 **LocalMachine** 를 지정 합니다.
`Get-ChildItem`Cmdlet은 **HKLM** 공급자에 **Path** 매개 변수를 사용 하 여 레지스트리 위치를 지정 합니다.

### 예 3: 로컬 컴퓨터에 원격 컴퓨터의 실행 정책 적용

이 명령은 원격 컴퓨터에서 실행 정책 개체를 가져오고 로컬 컴퓨터에 정책을 설정 합니다. `Get-ExecutionPolicy` 파이프라인을 통해 **Microsoft.PowerShell.Exe된 정책** 개체를 보냅니다. `Set-ExecutionPolicy` 파이프라인 입력을 허용 하며 **set-executionpolicy** 매개 변수가 필요 하지 않습니다.

```
PS> Invoke-Command -ComputerName Server01 -ScriptBlock { Get-ExecutionPolicy } | Set-ExecutionPolicy
```

`Invoke-Command`이 cmdlet은 로컬 컴퓨터에서 실행 되 고 **ScriptBlock** 을 원격 컴퓨터로 보냅니다. **ComputerName** 매개 변수는 원격 컴퓨터 **Server01** 를 지정 합니다. **ScriptBlock** 매개 변수는 `Get-ExecutionPolicy` 원격 컴퓨터에서 실행 됩니다. `Get-ExecutionPolicy`개체는 파이프라인에서로 전송 됩니다 `Set-ExecutionPolicy` .
`Set-ExecutionPolicy` 실행 정책을 로컬 컴퓨터의 기본 범위인 **LocalMachine** 에 적용 합니다.

### 예제 4: 실행 정책에 대 한 범위 설정

이 예제에서는 지정 된 범위 **CurrentUser** 에 대 한 실행 정책을 설정 하는 방법을 보여 줍니다. **CurrentUser** 범위는이 범위를 설정 하는 사용자 에게만 영향을 줍니다.

```powershell
Set-ExecutionPolicy -ExecutionPolicy AllSigned -Scope CurrentUser
Get-ExecutionPolicy -List
```

```Output
        Scope ExecutionPolicy
        ----- ---------------
MachinePolicy       Undefined
   UserPolicy       Undefined
      Process       Undefined
  CurrentUser       AllSigned
 LocalMachine    RemoteSigned
```

`Set-ExecutionPolicy`**set-executionpolicy** 매개 변수를 사용 하 여 **AllSigned** 정책을 지정 합니다.
**Scope** 매개 변수는 **CurrentUser** 를 지정 합니다. 실행 정책 설정을 보려면 `Get-ExecutionPolicy` **List** 매개 변수와 함께 cmdlet을 사용 합니다.

사용자에 대 한 유효 실행 정책이 **AllSigned** 됩니다.

### 예 5: 현재 사용자에 대 한 실행 정책 제거

이 예에서는 **정의 되지 않은** 실행 정책을 사용 하 여 지정 된 범위에 대 한 실행 정책을 제거 하는 방법을 보여 줍니다.

```powershell
Set-ExecutionPolicy -ExecutionPolicy Undefined -Scope CurrentUser
Get-ExecutionPolicy -List
```

```Output
        Scope ExecutionPolicy
        ----- ---------------
MachinePolicy       Undefined
   UserPolicy       Undefined
      Process       Undefined
  CurrentUser       Undefined
 LocalMachine    RemoteSigned
```

`Set-ExecutionPolicy`**set-executionpolicy** 매개 변수를 사용 하 여 **정의 되지 않은** 정책을 지정 합니다.
**Scope** 매개 변수는 **CurrentUser** 를 지정 합니다. 실행 정책 설정을 보려면 `Get-ExecutionPolicy` **List** 매개 변수와 함께 cmdlet을 사용 합니다.

### 예 6: 현재 PowerShell 세션에 대 한 실행 정책 설정

**프로세스** 범위는 현재 PowerShell 세션에만 영향을 줍니다. 실행 정책은 환경 변수에 저장 되며 `$env:PSExecutionPolicyPreference` 세션을 닫을 때 삭제 됩니다.

```powershell
Set-ExecutionPolicy -ExecutionPolicy AllSigned -Scope Process
```

```Output
        Scope ExecutionPolicy
        ----- ---------------
MachinePolicy       Undefined
   UserPolicy       Undefined
      Process       AllSigned
  CurrentUser    RemoteSigned
 LocalMachine    RemoteSigned
```

는 `Set-ExecutionPolicy` **set-executionpolicy** 매개 변수를 사용 하 여 **AllSigned** 정책을 지정 합니다. **범위** 매개 변수는 값 **프로세스** 를 지정 합니다. 실행 정책 설정을 보려면 `Get-ExecutionPolicy` **List** 매개 변수와 함께 cmdlet을 사용 합니다.

### 예 7: 실행 정책을 변경 하지 않고 실행 하는 스크립트 차단 해제

이 예에서는 **RemoteSigned** 실행 정책으로 서명 되지 않은 스크립트를 실행 하지 못하게 하는 방법을 보여 줍니다.

Cmdlet을 사용 **하기 전에** 스크립트의 코드를 읽고 안전 하 게 확인 하는 것이 가장 좋습니다 `Unblock-File` . `Unblock-File`Cmdlet은 실행할 수 있도록 스크립트를 차단 해제 하지만 실행 정책을 변경 하지는 않습니다.

```
PS> Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope LocalMachine

PS> Get-ExecutionPolicy

RemoteSigned

PS> .\Start-ActivityTracker.ps1

.\Start-ActivityTracker.ps1 : File .\Start-ActivityTracker.ps1 cannot be loaded.
The file .\Start-ActivityTracker.ps1 is not digitally signed.
The script will not execute on the system.
For more information, see about_Execution_Policies at https://go.microsoft.com/fwlink/?LinkID=135170.
At line:1 char:1
+ .\Start-ActivityTracker.ps1
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : NotSpecified: (:) [], PSSecurityException
+ FullyQualifiedErrorId : UnauthorizedAccess

PS> Unblock-File -Path .\Start-ActivityTracker.ps1

PS> Get-ExecutionPolicy

RemoteSigned

PS> .\Start-ActivityTracker.ps1

Task 1:
```

는 `Set-ExecutionPolicy` **set-executionpolicy** 매개 변수를 사용 하 여 **RemoteSigned** 정책을 지정 합니다. 정책은 기본 범위인 **LocalMachine** 에 대해 설정 됩니다.

`Get-ExecutionPolicy`이 cmdlet은 **RemoteSigned** 가 현재 PowerShell 세션에 대 한 유효한 실행 정책 임을 보여 줍니다.

현재 디렉터리에서 **Start-ActivityTracker.ps1** 스크립트가 실행 됩니다. 스크립트가 디지털 서명 되지 않았기 때문에 **RemoteSigned** 에 의해 스크립트가 차단 됩니다.

이 예제에서는 스크립트의 코드를 검토 하 고 실행 해도 안전한 지 확인 했습니다. `Unblock-File`Cmdlet은 **Path** 매개 변수를 사용 하 여 스크립트를 차단 해제 합니다.

`Unblock-File`에서 실행 정책이 변경 되지 않았는지 확인 하려면는 `Get-ExecutionPolicy` 유효한 실행 정책 **RemoteSigned** 를 표시 합니다.

현재 디렉터리에서 **Start-ActivityTracker.ps1** 스크립트가 실행 됩니다. 스크립트가 cmdlet에 의해 차단이 해제 되었기 때문에 스크립트가 실행 되기 시작 합니다 `Unblock-File` .

## PARAMETERS

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

### -ExecutionPolicy

실행 정책을 지정 합니다. 그룹 정책이 없고 각 범위의 실행 정책이 **Undefined** 로 설정 된 경우 **제한** 된 모든 사용자에 대 한 유효 정책이 됩니다.

허용 되는 실행 정책 값은 다음과 같습니다.

- **AllSigned** . 로컬 컴퓨터에 작성 된 스크립트를 포함 하 여 모든 스크립트와 구성 파일에 신뢰할 수 있는 게시자가 서명 해야 합니다.
- **바이패스** . 아무것도 차단되지 않으며 경고 또는 프롬프트가 없습니다.
- **Default** 입니다. 기본 실행 정책을 설정 합니다. Windows 클라이언트 또는 Windows server **RemoteSigned** 에 대해 **제한** 됩니다.
- **RemoteSigned** . 인터넷에서 다운로드 한 모든 스크립트와 구성 파일에 신뢰할 수 있는 게시자가 서명 해야 합니다. Windows server 컴퓨터에 대 한 기본 실행 정책입니다.
- **제한** 됨. 구성 파일을 로드 하거나 스크립트를 실행 하지 않습니다. 기본 실행 정책 Windows 클라이언트 컴퓨터입니다.
- **정의 되지 않았습니다** . 범위에 대해 설정 된 실행 정책이 없습니다. 그룹 정책에 의해 설정 되지 않은 범위에서 할당 된 실행 정책을 제거 합니다. 모든 범위의 실행 정책이 **정의** 되지 않은 경우 유효 실행 정책이 **제한** 됩니다.
- **무제한** . PowerShell 6.0부터이는 비 Windows 컴퓨터에 대 한 기본 실행 정책이 며 변경할 수 없습니다. 모든 구성 파일을 로드하고 모든 스크립트를 실행합니다. 인터넷에서 다운로드 한 서명 되지 않은 스크립트를 실행할 경우 실행 하기 전에 사용 권한을 묻는 메시지가 표시 됩니다.

```yaml
Type: Microsoft.PowerShell.ExecutionPolicy
Parameter Sets: (All)
Aliases:
Accepted values: AllSigned, Bypass, Default, RemoteSigned, Restricted, Undefined, Unrestricted

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Force

모든 확인 메시지를 표시하지 않습니다. 예기치 않은 결과를 방지 하려면이 매개 변수에 주의 해야 합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -범위

실행 정책의 영향을 받는 범위를 지정 합니다. 기본 범위는 **LocalMachine** 입니다.

유효한 실행 정책은 다음과 같이 우선 순위에 따라 결정 됩니다.

- **MachinePolicy** . 컴퓨터의 모든 사용자에 대해 그룹 정책 설정 합니다.
- **Userpolicy** . 컴퓨터의 현재 사용자에 대 한 그룹 정책 설정 합니다.
- **프로세스** . 현재 PowerShell 세션에만 영향을 줍니다.
- **CurrentUser** . 현재 사용자 에게만 영향을 줍니다.
- **LocalMachine** . 컴퓨터의 모든 사용자에 게 영향을 주는 기본 범위입니다.

**프로세스** 범위는 현재 PowerShell 세션에만 영향을 줍니다. 실행 정책은 레지스트리가 아닌 환경 변수에 저장 됩니다 `$env:PSExecutionPolicyPreference` . PowerShell 세션이 닫히면 변수와 값이 삭제 됩니다.

**CurrentUser** 범위에 대 한 실행 정책은 레지스트리 hive **HKEY_LOCAL_USER** 에 기록 됩니다.

**LocalMachine** 범위에 대 한 실행 정책은 레지스트리 hive **HKEY_LOCAL_MACHINE** 에 기록 됩니다.

```yaml
Type: Microsoft.PowerShell.ExecutionPolicyScope
Parameter Sets: (All)
Aliases:
Accepted values: CurrentUser, LocalMachine, MachinePolicy, Process, UserPolicy

Required: False
Position: 1
Default value: LocalMachine
Accept pipeline input: True (ByPropertyName)
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

### Microsoft.PowerShell.Exe, System.string

실행 정책 개체 또는 실행 정책의 이름을 포함 하는 문자열을로 파이프 할 수 있습니다 `Set-ExecutionPolicy` .

## 출력

### 없음

`Set-ExecutionPolicy` 는 출력을 반환 하지 않습니다.

## 참고

`Set-ExecutionPolicy` 는 그룹 정책에 의해 설정 되므로 **MachinePolicy** 및 **userpolicy** 범위를 변경 하지 않습니다.

`Set-ExecutionPolicy` 사용자 기본 설정이 정책 보다 더 제한적 이더라도는 그룹 정책를 재정의 하지 않습니다.

컴퓨터 또는 사용자에 대 한 **스크립트 실행 설정** 그룹 정책 사용 하도록 설정 된 경우 사용자 기본 설정이 저장 되지만 적용 되지 않습니다. PowerShell은 충돌을 설명 하는 메시지를 표시 합니다.

## 관련 링크

[about_Execution_Policies](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)

[about_Group_Policy_Settings](../Microsoft.PowerShell.Core/About/about_Group_Policy_Settings.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

[Get-AuthenticodeSignature](Get-AuthenticodeSignature.md)

[Get-ChildItem](../Microsoft.PowerShell.Management/Get-ChildItem.md)

[Get-ExecutionPolicy](Get-ExecutionPolicy.md)

[Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md)

[Set-AuthenticodeSignature](Set-AuthenticodeSignature.md)

[Unblock-File](../Microsoft.PowerShell.Utility/Unblock-File.md)
