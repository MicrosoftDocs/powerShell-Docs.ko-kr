---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 3/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-executionpolicy?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ExecutionPolicy
ms.openlocfilehash: 347ffa733068d4e7f4896eb18358c7a852c88d0a
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94347281"
---
# Get-ExecutionPolicy

## 개요
현재 세션에 대한 실행 정책을 가져옵니다.

## SYNTAX

### 모두

```
Get-ExecutionPolicy [[-Scope] <ExecutionPolicyScope>] [-List] [<CommonParameters>]
```

## 설명

각 범위에 대 한 실행 정책을 우선 순위에 따라 표시 하려면를 사용 `Get-ExecutionPolicy -List` 합니다. PowerShell 세션의 유효 실행 정책을 매개 변수 없이 사용 하는 것을 확인 합니다 `Get-ExecutionPolicy` .

유효 실행 정책은에 의해 설정 되 고 설정 그룹 정책 하는 실행 정책에 의해 결정 됩니다 `Set-ExecutionPolicy` .

자세한 내용은 [about_Execution_Policies](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md)를 참조하세요.

## 예제

### 예제 1: 모든 실행 정책 가져오기

이 명령은 각 범위에 대 한 실행 정책을 우선 순위에 따라 표시 합니다.

```powershell
Get-ExecutionPolicy -List
```

```Output
Scope          ExecutionPolicy
-----          ---------------
MachinePolicy  Undefined
UserPolicy     Undefined
Process        Undefined
CurrentUser    AllSigned
LocalMachine   Undefined
```

`Get-ExecutionPolicy`Cmdlet은 **List** 매개 변수를 사용 하 여 각 범위의 실행 정책을 표시 합니다.

### 예제 2: 실행 정책 설정

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
  CurrentUser       AllSigned
 LocalMachine    RemoteSigned
```

`Set-ExecutionPolicy`Cmdlet은 **set-executionpolicy** 매개 변수를 사용 하 여 **RemoteSigned** 정책을 지정 합니다. **범위** 매개 변수는 기본 범위 값인 **LocalMachine** 를 지정 합니다. 실행 정책 설정을 보려면 `Get-ExecutionPolicy` **List** 매개 변수와 함께 cmdlet을 사용 합니다.

### 예 3: 유효 실행 정책 가져오기

이 예에서는 PowerShell 세션의 유효 실행 정책을 표시 하는 방법을 보여 줍니다.

```
PS> Get-ExecutionPolicy -List

        Scope ExecutionPolicy
        ----- ---------------
MachinePolicy       Undefined
   UserPolicy       Undefined
      Process       Undefined
  CurrentUser       AllSigned
 LocalMachine    RemoteSigned

PS> Get-ExecutionPolicy

AllSigned
```

`Get-ExecutionPolicy`Cmdlet은 **List** 매개 변수를 사용 하 여 각 범위의 실행 정책을 표시 합니다. `Get-ExecutionPolicy`매개 변수 없이 cmdlet을 실행 하 여 유효 실행 정책 **AllSigned** 를 표시 합니다.

### 예제 4: 실행 정책을 변경 하지 않고 실행 하는 스크립트 차단 해제

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

### -목록

우선 순위대로 나열된, 세션에 대한 모든 실행 정책 값을 가져옵니다. 기본적으로는 `Get-ExecutionPolicy` 유효 실행 정책만 가져옵니다.

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

### -범위

실행 정책의 영향을 받는 범위를 지정 합니다.

유효한 실행 정책은 다음과 같이 우선 순위에 따라 결정 됩니다.

- **MachinePolicy**. 컴퓨터의 모든 사용자에 대해 그룹 정책 설정 합니다.
- **Userpolicy**. 컴퓨터의 현재 사용자에 대 한 그룹 정책 설정 합니다.
- **프로세스**. 현재 PowerShell 세션에만 영향을 줍니다.
- **CurrentUser**. 현재 사용자 에게만 영향을 줍니다.
- **LocalMachine**. 컴퓨터의 모든 사용자에 게 영향을 주는 기본 범위입니다.

```yaml
Type: Microsoft.PowerShell.ExecutionPolicyScope
Parameter Sets: (All)
Aliases:
Accepted values: CurrentUser, LocalMachine, MachinePolicy, Process, UserPolicy

Required: False
Position: 0
Default value: Effective execution policy
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### 없음

`Get-ExecutionPolicy` 파이프라인의 입력을 허용 하지 않습니다.

## 출력

### Microsoft.PowerShell.Exe이상 정책

Cmdlet은 항상 Linux 및 macOS 플랫폼에서 **무제한** 을 반환 합니다.

## 참고

실행 정책은 PowerShell 보안 전략의 일부입니다. 실행 정책은 PowerShell 프로필과 같은 구성 파일을 로드 하거나 스크립트를 실행할 수 있는지 여부를 결정 합니다. 스크립트를 실행 하기 전에 디지털로 서명 해야 하는지 여부를 지정 합니다.

## 관련 링크

[about_Execution_Policies](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md)

[about_Group_Policy_Settings](../Microsoft.PowerShell.Core/About/about_Group_Policy_Settings.md)

[Get-AuthenticodeSignature](Get-AuthenticodeSignature.md)

[Set-AuthenticodeSignature](Set-AuthenticodeSignature.md)

[Set-ExecutionPolicy](Set-ExecutionPolicy.md)
