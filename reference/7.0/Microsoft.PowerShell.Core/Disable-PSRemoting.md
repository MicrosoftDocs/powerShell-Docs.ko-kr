---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 01/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/disable-psremoting?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSRemoting
ms.openlocfilehash: b51d5c2d21734a8db31a6e257579cca68809ebc5
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93210994"
---
# Disable-PSRemoting

## 개요
PowerShell 끝점이 원격 연결을 받지 못하도록 합니다.

## SYNTAX

```
Disable-PSRemoting [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명

`Disable-PSRemoting`Cmdlet은 로컬 컴퓨터의 모든 PowerShell 버전 6 및 더 큰 세션 끝점 구성에 대 한 원격 액세스를 차단 합니다. Windows PowerShell 끝점 구성에는 영향을 주지 않습니다. Windows PowerShell 세션 끝점 구성을 사용 하지 않도록 설정 하려면 `Disable-PSRemoting` Windows powershell 세션 내에서 명령을 실행 합니다.

모든 PowerShell 버전 6 및 더 큰 세션 끝점 구성에 대 한 원격 액세스를 다시 사용 하도록 설정 하려면 cmdlet을 사용 `Enable-PSRemoting` 합니다. 모든 Windows PowerShell 세션 끝점 구성에 대 한 원격 액세스를 다시 사용 하도록 설정 하려면 `Enable-PSRemoting` Windows powershell 세션 내에서를 실행 합니다.

> [!NOTE]
> 로컬 Windows 컴퓨터에 대 한 모든 PowerShell 원격 액세스를 사용 하지 않도록 설정 하려면 PowerShell 버전 6 이상의 세션 내에서 또는 Windows PowerShell 세션 내에서이 명령을 실행 해야 합니다. Windows PowerShell은 기본적으로 모든 Windows 컴퓨터에 설치 됩니다.

특정 세션 끝점 구성에 대 한 원격 액세스를 사용 하지 않도록 설정 하 고 다시 사용 하도록 설정 하려면 `Enable-PSSessionConfiguration` 및 cmdlet을 사용 `Disable-PSSessionConfiguration` 합니다. 개별 끝점의 특정 액세스 구성을 설정 하려면 `Set-PSSessionConfiguration` **accessmode** 매개 변수와 함께 cmdlet을 사용 합니다. 세션 구성에 대 한 자세한 내용은 [about_Session_Configurations](About/about_Session_Configurations.md)를 참조 하세요.

> [!NOTE]
> 실행 후 `Disable-PSRemoting` 에도 로컬 컴퓨터에서 루프백 연결을 설정할 수 있습니다. 루프백 연결은 동일한 로컬 컴퓨터에서 시작 하 여 연결 하는 PowerShell 원격 세션입니다. 외부 원본의 원격 세션은 차단 된 상태로 유지 됩니다. 루프백 연결의 경우 **EnableNetworkAccess** 매개 변수를 따라 암시적 자격 증명을 사용 해야 합니다. 루프백 연결에 대 한 자세한 내용은 [새 PSSession](New-PSSession.md)을 참조 하세요.

이 cmdlet은 Windows 플랫폼 에서만 사용할 수 있습니다. Linux 또는 macOS 버전의 PowerShell에서는 사용할 수 없습니다. 이 cmdlet을 실행 하려면 **관리자 권한으로 실행** 옵션을 사용 하 여 PowerShell을 시작 합니다.

## 예제

### 예 1: 모든 PowerShell 세션 구성에 대 한 원격 액세스 방지

이 예제에서는 컴퓨터의 모든 PowerShell 세션 끝점 구성에 대 한 원격 액세스를 방지 합니다.

```powershell
Disable-PSRemoting
```

```Output
WARNING: PowerShell remoting has been disabled only for PowerShell 6+ configurations and does not affect
 Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect all PowerShell
 remoting configurations.

WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.
```

### 예 2: 확인 메시지 없이 모든 PowerShell 세션 구성에 대 한 원격 액세스 방지

이 예제에서는 메시지를 표시 하지 않고 컴퓨터의 모든 PowerShell 세션 끝점 구성에 대 한 원격 액세스를 방지 합니다.

```powershell
Disable-PSRemoting -Force
```

```Output
WARNING: PowerShell remoting has been disabled only for PowerShell 6+ configurations and does not affect
 Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect all PowerShell
 remoting configurations.

WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.
```

### 예 3:이 cmdlet을 실행 한 결과

이 예에서는 cmdlet을 사용 하는 경우의 결과를 보여 줍니다 `Disable-PSRemoting` . 이 명령 시퀀스를 실행 하려면 **관리자 권한으로 실행** 옵션을 사용 하 여 PowerShell을 시작 합니다.

세션 구성을 사용 하지 않도록 설정 하면 `New-PSSession` cmdlet이 로컬 컴퓨터 ("루프백"이 라고도 함)에 대 한 원격 세션을 만들려고 시도 합니다. 로컬 컴퓨터에서 원격 액세스를 사용할 수 없으므로 명령이 실패 합니다.

```powershell
Disable-PSRemoting -Force
New-PSSession -ComputerName localhost -ConfigurationName PowerShell.6
```

```Output
WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.

New-PSSession : [localhost] Connecting to remote server localhost failed with the following error
 message : Access is denied. For more information, see the about_Remote_Troubleshooting Help topic.
At line:1 char:1
+ New-PSSession -ComputerName localhost -ConfigurationName PowerShell.6
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : OpenError: (System.Management.A\u2026tion.RemoteRunspace:RemoteRunspace)
 [New-PSSession], PSRemotingTransportException
+ FullyQualifiedErrorId : AccessDenied,PSSessionOpenFailed
```

### 예제 4:이 cmdlet을 실행 한 결과 및 Enable-PSRemoting

이 예에서는 및 cmdlet을 사용 하는의 세션 구성에 미치는 영향을 보여 줍니다 `Disable-PSRemoting` `Enable-PSRemoting` .

`Disable-PSRemoting` 모든 PowerShell 세션 끝점 구성에 대 한 원격 액세스를 사용 하지 않도록 설정 하는 데 사용 됩니다. **Force** 매개 변수는 모든 사용자 프롬프트를 표시하지 않습니다. `Get-PSSessionConfiguration`및 `Format-Table` cmdlet은 컴퓨터에 세션 구성을 표시 합니다.

출력은 네트워크 토큰이 있는 모든 원격 사용자가 끝점 구성에 대 한 액세스를 거부 한다는 것을 보여 줍니다. 로컬 컴퓨터의 Administrators 그룹은 로컬로 (루프백이 라고도 함) 연결 되 고 암시적 자격 증명을 사용 하는 동안 끝점 구성에 대 한 액세스를 허용 합니다.

```powershell
Disable-PSRemoting -force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto

Enable-PSRemoting -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto
```

```Output
Name               Permission
----               ----------
PowerShell.6       NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed ...
PowerShell.6.2.0   NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed ...

Name               Permission
----               ----------
PowerShell.6       NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed ...
PowerShell.6.2.0   NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed ...
```

`Enable-PSRemoting`Cmdlet은 컴퓨터의 모든 PowerShell 세션 끝점 구성에 대 한 원격 액세스를 다시 사용 하도록 설정 합니다. **Force** 매개 변수는 모든 사용자 프롬프트를 표시 하지 않고 WinRM 서비스를 다시 시작 합니다. 새 출력은 **Accessdenied** 된 보안 설명자가 모든 세션 구성에서 제거 되었음을 보여 줍니다.

### 예 5: 비활성화 된 세션 끝점 구성을 사용 하는 루프백 연결

이 예제에서는 끝점 구성을 사용 하지 않도록 설정 하는 방법을 보여 주고 사용 하지 않는 끝점에 대 한 루프백 연결을 설정 하는 방법을 보여 줍니다. `Disable-PSRemoting` 모든 PowerShell 세션 끝점 구성을 사용 하지 않도록 설정 합니다.

```powershell
Disable-PSRemoting -Force
```

```Output
WARNING: PowerShell remoting has been disabled only for PowerShell 6+ configurations and does not affect
 Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect all PowerShell
 remoting configurations.

WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.
```

```powershell
New-PSSession -ComputerName localhost -ConfigurationName powershell.6 -Credential (Get-Credential)
```

```Output
PowerShell credential request
Enter your credentials.
User: UserName
Password for user UserName: ************

New-PSSession: [localhost] Connecting to remote server localhost failed with the following error message
 : Access is denied. For more information, see the about_Remote_Troubleshooting Help topic.
```

```powershell
New-PSSession -ComputerName localhost -ConfigurationName powershell.6 -EnableNetworkAccess
```

```Output
 Id Name       Transport ComputerName  ComputerType   State   ConfigurationName   Availability
 -- ----       --------- ------------  ------------   -----   -----------------   ------------
 1  Runspace1  WSMan     localhost     RemoteMachine  Opened  powershell.6           Available
```

을 처음 사용 하는 경우 `New-PSSession` 로컬 컴퓨터에 대 한 원격 세션을 만들려고 시도 합니다. **ConfigurationName** 매개 변수는 비활성화 된 PowerShell 끝점을 지정 하는 데 사용 됩니다. 자격 증명은 자격 **증명 매개 변수를 통해** 명령에 명시적으로 전달 됩니다. 이 유형의 연결은 네트워크 스택을 통과 하며 루프백이 아닙니다. 따라서 **액세스 거부** 오류가 발생 하 여 비활성화 된 끝점에 대 한 연결 시도가 실패 합니다.

두 번째를 사용 하는 경우에 `New-PSSession` 도 로컬 컴퓨터에 대 한 원격 세션을 만들려고 시도 합니다.
이 경우 네트워크 스택을 우회 하는 루프백 연결 이기 때문에 성공 합니다.

다음 조건이 충족 되 면 루프백 연결이 생성 됩니다.

- 연결할 컴퓨터 이름은 ' localhost '입니다.
- 자격 증명은 전달 되지 않습니다. 현재 로그인 한 사용자 (암시적 자격 증명)가 연결에 사용 됩니다.
- **EnableNetworkAccess** 스위치 매개 변수가 사용 됩니다.

루프백 연결에 대 한 자세한 내용은 [새 PSSession](New-PSSession.md) 문서를 참조 하세요.

### 예 6: 모든 PowerShell 원격 끝점 구성 비활성화

이 예제에서는 `Disable-PSRemoting` 명령을 실행 해도 Windows PowerShell 끝점 구성에 영향을 주지 않는 방법을 보여 줍니다. `Get-PSSessionConfiguration` Windows PowerShell 내에서 실행은 모든 끝점 구성을 표시 합니다. Windows PowerShell 끝점 구성은 사용 하지 않도록 설정 되어 있는 것을 볼 수 있습니다.

```powershell
Disable-PSRemoting -Force
powershell.exe -command 'Get-PSSessionConfiguration'
```

```Output
WARNING: PowerShell remoting has been disabled only for PowerShell 6+ configurations and does not affect
 Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect all PowerShell
 remoting configurations.

WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.

Name          : microsoft.powershell
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote
                Management Users AccessAllowed

Name          : microsoft.powershell.workflow
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : microsoft.powershell32
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote
                Management Users AccessAllowed

Name          : PowerShell.6
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators
                AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : PowerShell.6.2.2
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators
                AccessAllowed, BUILTIN\Remote Management Users AccessAllowed
```

```powershell
powershell.exe -command 'Disable-PSRemoting -Force'
powershell.exe -command 'Get-PSSessionConfiguration'
```

```Output
WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting or
Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to members of the
Administrators group on the computer.

Name          : microsoft.powershell
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators
                AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : microsoft.powershell.workflow
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management
                Users AccessAllowed

Name          : microsoft.powershell32
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators
                AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : PowerShell.6
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators
                AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : PowerShell.6.2.2
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators
                AccessAllowed, BUILTIN\Remote Management Users AccessAllowed
```

이러한 끝점 구성을 사용 하지 않도록 설정 하려면 `Disable-PSRemoting` Windows PowerShell 세션 내에서 명령을 실행 해야 합니다. 이제 `Get-PSSessionConfiguration` Windows PowerShell 내에서를 실행 하면 모든 끝점 구성이 사용 하지 않도록 설정 된 것을 볼 수 있습니다.

### 예 7: 사용자 지정 보안 설명자가 있는 세션 구성에 대 한 원격 액세스 방지

이 예제에서는 cmdlet이 `Disable-PSRemoting` 사용자 지정 보안 설명자를 사용 하 여 세션 구성을 포함 하는 모든 세션 구성에 대 한 원격 액세스를 사용 하지 않도록 설정 합니다

`Register-PSSessionConfiguration`**테스트** 세션 구성을 만듭니다. **FilePath** 매개 변수는 세션을 사용자 지정 하는 세션 구성 파일을 지정 합니다. **ShowSecurityDescriptorUI** 매개 변수는 세션 구성에 대 한 사용 권한을 설정 하는 대화 상자를 표시 합니다. 권한 대화 상자에서 표시 된 사용자에 대 한 사용자 지정 전체 액세스 권한을 만듭니다.

`Get-PSSessionConfiguration`및 `Format-Table` cmdlet은 세션 구성과 해당 속성을 표시 합니다. 출력은 **테스트** 세션 구성에서 표시 된 사용자에 대 한 대화형 액세스 및 특별 한 사용 권한을 허용 한다는 것을 보여 줍니다.

`Disable-PSRemoting` 모든 세션 구성에 대 한 원격 액세스를 사용 하지 않도록 설정 합니다.

```powershell
Register-PSSessionConfiguration -Name Test -FilePath .\TestEndpoint.pssc -ShowSecurityDescriptorUI -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Wrap

Disable-PSRemoting -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Wrap
New-PSSession -ComputerName localhost -ConfigurationName Test
```

```Output
Name               Permission
----               ----------
PowerShell.6       NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed,
                   BUILTIN\Remote Management Users AccessAllowed
PowerShell.6.2.0   NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed,
                   BUILTIN\Remote Management Users AccessAllowed
Test               NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed,
                   User01 AccessAllowed

WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.

Name               Permission
----               ----------
PowerShell.6       NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed,
                   BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed
PowerShell.6.2.0   NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed,
                   BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed
Test               NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed,
                   BUILTIN\Administrators AccessAllowed, User01 AccessAllowed

New-PSSession : [localhost] Connecting to remote server localhost failed with the following error message
 : Access is denied. For more information, see the about_Remote_Troubleshooting Help topic.
At line:1 char:1
+ New-PSSession -ComputerName localhost -ConfigurationName Test
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : OpenError: (System.Management.A\u2026tion.RemoteRunspace:RemoteRunspace)
 [New-PSSession], PSRemotingTransportException
+ FullyQualifiedErrorId : AccessDenied,PSSessionOpenFailed
```

이제 `Get-PSSessionConfiguration` 및 `Format-Table` cmdlet은 모든 네트워크 사용자에 대 한 **accessdenied** 보안 설명자가 **테스트** 세션 구성을 비롯 한 모든 세션 구성에 추가 됨을 보여 줍니다. 다른 보안 설명자는 변경 되지 않지만 "network_deny_all" 보안 설명자가 우선적으로 적용 됩니다. 이는를 사용 하 여 `New-PSSession` **테스트** 세션 구성에 연결 하려고 할 때 표시 됩니다.

### 예 8: 선택한 세션 구성에 대 한 원격 액세스 다시 사용

이 예제에서는 선택한 세션 구성에 대해서만 원격 액세스를 사용하도록 다시 설정하는 방법을 보여 줍니다. 모든 세션 구성을 사용 하지 않도록 설정한 후 특정 세션을 다시 사용 하도록 설정 합니다.

`Set-PSSessionConfiguration`Cmdlet은 **PowerShell. 6** 세션 구성을 변경 하는 데 사용 됩니다. 값이 **remote** 인 **accessmode** 매개 변수는 구성에 대 한 원격 액세스를 다시 사용 하도록 설정 합니다.

```powershell
Disable-PSRemoting -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto

Set-PSSessionConfiguration -Name PowerShell.6 -AccessMode Remote -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto
```

```Output
WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.

Name                 Permission
----                 ----------
PowerShell.6         NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Adm ...
PowerShell.6.2.0     NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Adm ...

Name                 Permission
----                 ----------
PowerShell.6         NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\ ...
PowerShell.6.2.0     NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Adm ...
```

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

### -Force

사용자 확인을 요청하지 않고 명령을 강제 실행합니다.

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

### 없음

개체를이 cmdlet으로 파이프 할 수는 없습니다.

## 출력

### 없음

이 cmdlet은 어떠한 출력도 생성하지 않습니다.

## 참고

- 세션 구성을 사용 하지 않도록 설정 해도 또는 cmdlet에서 수행한 모든 변경 내용은 실행 취소 되지 않습니다 `Enable-PSRemoting` `Enable-PSSessionConfiguration` . 다음 변경 작업을 수동으로 실행 취소해야 할 수 있습니다.

  1. WinRM 서비스를 중지하고 사용하지 않도록 설정합니다.
  2. 모든 IP 주소에서 요청을 수락하는 수신기를 삭제합니다.
  3. WS-Management 통신에 대해 방화벽 예외를 사용하지 않도록 설정합니다.
  4. LocalAccountTokenFilterPolicy 값을 0으로 복원하여 컴퓨터에서 Administrators 그룹의 구성원에 대한 원격 액세스를 제한합니다.

- 세션 끝점 구성은 세션의 환경을 정의 하는 설정 그룹입니다.
  컴퓨터에 연결 되는 모든 세션은 컴퓨터에 등록 된 세션 끝점 구성 중 하나를 사용 해야 합니다. 모든 세션 끝점 구성에 대 한 원격 액세스를 거부 하면 원격 사용자가 컴퓨터에 연결 하는 세션을 설정 하는 것을 효과적으로 방지할 수 있습니다.

## 관련 링크

[Disable-PSSessionConfiguration](Disable-PSSessionConfiguration.md)

[Enable-PSRemoting](Enable-PSRemoting.md)

[Get-PSSessionConfiguration](Get-PSSessionConfiguration.md)

[New-PSSession](New-PSSession.md)

[Register-PSSessionConfiguration](Register-PSSessionConfiguration.md)

[Set-PSSessionConfiguration](Set-PSSessionConfiguration.md)

[Unregister-PSSessionConfiguration](Unregister-PSSessionConfiguration.md)

[WSMan 공급자](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)
