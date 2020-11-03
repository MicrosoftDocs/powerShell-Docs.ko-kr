---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/test-computersecurechannel?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-ComputerSecureChannel
ms.openlocfilehash: 20ea76e725a8ab53d7090078dc819a6297a639ff
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93214345"
---
# Test-ComputerSecureChannel

## 개요
로컬 컴퓨터와 해당 도메인 간의 보안 채널을 테스트 및 복구합니다.

## SYNTAX

```
Test-ComputerSecureChannel [-Repair] [-Server <String>] [-Credential <PSCredential>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## 설명
**테스트 ComputerSecureChannel** cmdlet은 트러스트 관계의 상태를 확인 하 여 로컬 컴퓨터와 해당 도메인 간의 채널이 제대로 작동 하는지 확인 합니다.
연결에 실패 하면 *Repair* 매개 변수를 사용 하 여 복원을 시도할 수 있습니다.

**테스트-ComputerSecureChannel** 은 채널이 제대로 작동 하는 경우 $True을 반환 하 고, 그렇지 않은 경우 $False 합니다.
이 결과를 통해 함수와 스크립트의 조건문에서 cmdlet을 사용할 수 있습니다.
자세한 테스트 결과를 얻으려면 *Verbose* 매개 변수를 사용 합니다.

이 cmdlet은 NetDom.exe와 비슷하게 작동합니다.
NetDom 및 **Test ComputerSecureChannel** 은 모두 **NetLogon** 서비스를 사용 하 여 작업을 수행 합니다.

## 예제

### 예제 1: 로컬 컴퓨터와 해당 도메인 간의 채널 테스트

```
PS C:\> Test-ComputerSecureChannel
True
```

이 명령은 로컬 컴퓨터와 해당 컴퓨터가 가입 된 도메인 간의 채널을 테스트 합니다.

### 예 2: 로컬 컴퓨터와 도메인 컨트롤러 간의 채널 테스트

```
PS C:\> Test-ComputerSecureChannel -Server "DCName.fabrikam.com"
True
```

이 명령은 테스트에 사용할 선호 도메인 컨트롤러를 지정합니다.

### 예제 3: 로컬 컴퓨터와 해당 도메인 간의 채널 다시 설정

```
PS C:\> Test-ComputerSecureChannel -Repair
True
```

이 명령은 로컬 컴퓨터와 해당 도메인 간의 채널을 다시 설정 합니다.

### 예제 4: 테스트에 대 한 자세한 정보 표시

```
PS C:\> Test-ComputerSecureChannel -verbose
VERBOSE: Performing operation "Test-ComputerSecureChannel" on Target "SERVER01".
True
VERBOSE: "The secure channel between 'SERVER01' and 'net.fabrikam.com' is alive and working correctly."
```

이 명령은 *Verbose* 일반 매개 변수를 사용 하 여 작업에 대 한 자세한 메시지를 요청 합니다.
자세한 정보에 대 *한 자세한 내용은 about_CommonParameters를 참조* 하세요.

### 예 5: 스크립트를 실행 하기 전에 연결 테스트

```
PS C:\> Set-Alias tcsc Test-ComputerSecureChannel
if (!(tcsc))
{Write-Host "Connection failed. Reconnect and retry."}
else { &(.\Get-Servers.ps1) }
```

이 예제에서는 연결을 요구 하는 스크립트를 실행 하기 전에 **테스트 ComputerSecureChannel** 을 사용 하 여 연결을 테스트 하는 방법을 보여 줍니다.

첫 번째 명령은 Set-Alias cmdlet을 사용하여 cmdlet 이름의 별칭을 만들어
공간을 저장하고 입력 오류를 방지합니다.

**If** 문은 스크립트를 실행 하기 전에 **테스트-computersecurechannel** 이 반환 하는 값을 확인 합니다.

## PARAMETERS

### -Credential
이 작업을 수행할 권한이 있는 사용자 계정을 지정합니다.
User01 또는 Domain01\User01과 같은 사용자 이름을 입력 하거나 **PSCredential** 개체 (예: Get-Credential cmdlet이 반환 하는 개체)를 입력 합니다.
기본적으로 이 cmdlet은 현재 사용자의 자격 증명을 사용합니다.

*Credential* 매개 변수는 *repair* 매개 변수를 사용 하 여 컴퓨터와 도메인 간의 채널을 복구 하는 명령에 사용 하도록 설계 되었습니다.

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

### -복구
이 cmdlet이 NetLogon 서비스에 의해 설정 된 채널을 제거한 다음 다시 작성 함을 나타냅니다.
테스트에 실패 한 연결을 복원 하려면이 매개 변수를 사용 합니다.

이 매개 변수를 사용하려면 현재 사용자가 로컬 컴퓨터 Administrators 그룹의 멤버여야 합니다.

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

### -Server
명령을 실행할 도메인 컨트롤러를 지정 합니다.
이 매개 변수를 지정 하지 않으면이 cmdlet은 작업에 대 한 기본 도메인 컨트롤러를 선택 합니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

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

### -WhatIf
cmdlet을 실행할 경우 발생하는 일을 표시합니다.
cmdlet은 실행되지 않습니다.

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
이 cmdlet에 입력을 파이프할 수 없습니다.

## 출력

### System.Boolean
이 cmdlet은 연결이 올바르게 작동 하면 $True을 반환 하 고, 그렇지 않으면 $False 합니다.

## 참고

* Windows Vista 이상 버전의 windows 운영 체제에서 **테스트 컴퓨터 Securechannel** 명령을 실행 하려면 관리자 권한으로 실행 옵션을 사용 하 여 windows PowerShell을 엽니다.
* **테스트 ComputerSecureChannel** 은 Netlogon 서비스의 다양 한 측면을 제어 하는 **I_NetLogonControl2** 함수를 사용 하 여 구현 됩니다.

## 관련 링크

[Checkpoint-Computer](Checkpoint-Computer.md)

[ComputerMachinePassword 재설정](Reset-ComputerMachinePassword.md)

[Restart-Computer](Restart-Computer.md)

[Stop-Computer](Stop-Computer.md)
