---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 04/04/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-computer?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Computer
ms.openlocfilehash: 89e43220a8d5ac675ea232db09cf3edec2ca2b97
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93214561"
---
# Remove-Computer

## 개요
도메인에서 로컬 및 원격 컴퓨터를 제거합니다.

## SYNTAX

### Local (기본값)

```
Remove-Computer [[-UnjoinDomainCredential] <PSCredential>] [-Restart] [-Force] [-PassThru]
 [-WorkgroupName <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### 원격

```
Remove-Computer -UnjoinDomainCredential <PSCredential> [-LocalCredential <PSCredential>] [-Restart]
 [-ComputerName <String[]>] [-Force] [-PassThru] [-WorkgroupName <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## 설명

`Remove-Computer`Cmdlet은 현재 도메인에서 로컬 컴퓨터와 원격 컴퓨터를 제거 합니다.

도메인에서 컴퓨터를 제거 하면에서 `Remove-Computer` 컴퓨터의 도메인 계정도 사용 하지 않도록 설정 됩니다. 현재 사용자의 자격 증명 인 경우에도 도메인에서 컴퓨터의 가입을 취소 하는 명시적 자격 증명을 제공 해야 합니다. 변경 내용을 적용 하려면 컴퓨터를 다시 시작 해야 합니다. 또한 도메인에서 컴퓨터를 제거하면 작업 그룹으로 이동해야 합니다. **WorkgroupName** 매개 변수를 사용하여 작업 그룹을 지정합니다.

작업 그룹에서 도메인으로 컴퓨터를 이동 하려면 한 작업 그룹에서 다른 작업 그룹으로 또는 한 도메인에서 다른 도메인으로 컴퓨터를 이동 하려면 cmdlet을 사용 `Add-Computer` 합니다.

명령 결과를 얻으려면 **Verbose** 및 **PassThru** 매개 변수를 사용합니다. 사용자 프롬프트를 표시하지 않으려면 **Force** 매개 변수를 사용합니다.

`Remove-Computer` 도메인에서 로컬 컴퓨터 및 원격 컴퓨터를 제거 합니다. 이 cmdlet에는 원격 컴퓨터에 연결하고 도메인 가입을 해제하기 위해 대체 자격 증명을 지정하는 자격 증명 매개 변수, 영향을 받는 컴퓨터를 다시 시작하는 **Restart**  매개 변수 및 컴퓨터가 추가되는 작업 그룹의 이름을 지정하는 **WorkgroupName** 매개 변수가 포함됩니다.

## 예제

### 예 1: 도메인에서 로컬 컴퓨터 제거

이 예제에서는 가입 된 도메인에서 로컬 컴퓨터를 제거 합니다.

```powershell
Remove-Computer -UnjoinDomaincredential Domain01\Admin01 -PassThru -Verbose -Restart
```

**UnjoinDomainCredential** 매개 변수는 도메인 관리자의 자격 증명을 제공 합니다. **PassThru** 및 **Verbose** 일반 매개 변수는 명령의 성공 또는 실패에 대 한 정보를 표시 합니다. **Restart** 매개 변수는 컴퓨터를 다시 시작 하 여 제거 작업을 완료 합니다.

작업 그룹 이름을 지정 하지 않으면 컴퓨터가 도메인에서 제거 된 후 이름이 지정 된 작업 그룹으로 이동 됩니다.

### 예제 2: 여러 컴퓨터를 기존 작업 그룹으로 이동

이 예제에서는 해당 도메인에서 파일에 나열 된 모든 컴퓨터를 제거 `OldServers.txt` 하 고 **레거시** 작업 그룹으로 이동 합니다.

```powershell
Remove-Computer -ComputerName (Get-Content OldServers.txt) -LocalCredential Domain01\Admin01 -UnJoinDomainCredential Domain01\Admin01 -WorkgroupName "Legacy" -Force -Restart
```

**Localcredential** 매개 변수는 원격 컴퓨터에 연결할 수 있는 권한을 가진 사용자의 자격 증명을 제공 합니다. **UnjoinDomainCredential** 매개 변수는 도메인에서 컴퓨터를 제거할 수 있는 권한을 가진 사용자의 자격 증명을 제공 합니다. **Force** 매개 변수는 각 컴퓨터에 대 한 확인 메시지를 표시 하지 않습니다. **Restart** 매개 변수는 도메인에서 제거 된 후 각 컴퓨터를 다시 시작 합니다.

### 예 3: 확인 없이 작업 그룹에서 컴퓨터 제거

이 예제에서는 도메인에서 원격 컴퓨터 Server01 및 로컬 컴퓨터를 제거 하 고 **로컬** 작업 그룹에 추가 합니다.

```powershell
Remove-Computer -ComputerName "Server01", "localhost" -UnjoinDomainCredential Domain01\Admin01 -WorkgroupName "Local" -Restart -Force
```

**Force** 매개 변수는 각 컴퓨터에 대 한 확인 메시지를 표시 하지 않습니다. **Restart** 매개 변수는 컴퓨터를 다시 시작 하 여 변경 내용을 적용 합니다.

## PARAMETERS

### -ComputerName

도메인에서 제거할 컴퓨터를 지정합니다. 기본값은 로컬 컴퓨터입니다.

원격 컴퓨터의 NetBIOS 이름, IP 주소 또는 FQDN (정규화 된 도메인 이름)을 입력 합니다. 로컬 컴퓨터를 지정 하려면 컴퓨터 이름, 점 (.) 또는 localhost를 입력 합니다.

이 매개 변수는 PowerShell 원격을 사용 하지 않습니다. **ComputerName** `Remove-Computer` 컴퓨터가 원격 명령을 실행 하도록 구성 되지 않은 경우에도의 ComputerName 매개 변수를 사용할 수 있습니다.

이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.String[]
Parameter Sets: Remote
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Force

사용자 확인 메시지를 표시하지 않습니다. 기본적으로에서는 `Remove-Computer` 각 컴퓨터를 제거 하기 전에 확인 메시지를 표시 합니다.

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

### -LocalCredential

**ComputerName** 매개 변수가 지정 하는 컴퓨터에 연결할 수 있는 권한을 가진 사용자 계정을 지정 합니다. 기본값은 현재 사용자입니다.

또는와 같은 사용자 이름을 입력 `User01` 하거나, `Domain01\User01` cmdlet에 의해 생성 된 것과 같은 **PSCredential** 개체를 입력 합니다 `Get-Credential` . 사용자 이름을 입력 하는 경우 cmdlet은 암호를 묻는 메시지를 표시 합니다. 현재 도메인에서 컴퓨터를 제거할 수 있는 권한을 가진 사용자 계정을 지정하려면 **UnjoinDomainCredential** 매개 변수를 사용합니다.

이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: Remote
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PassThru

명령의 결과를 반환합니다. 그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.

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

### -Restart

이 cmdlet은 제거 중인 컴퓨터를 다시 시작 함을 나타냅니다. 변경 내용을 적용하려면 컴퓨터를 자주 다시 시작해야 합니다.

이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.

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

### -UnjoinDomainCredential

현재 도메인에서 컴퓨터를 제거할 수 있는 권한을 가진 사용자 계정을 지정합니다.
값이 현재 사용자의 자격 증명인 경우에도 도메인에서 원격 컴퓨터를 제거하려면 이 매개 변수에서 제공하는 명시적 자격 증명이 필요합니다.

User01 또는 Domain01\User01과 같은 사용자 이름을 입력 하거나에 의해 생성 된 것과 같은 **PSCredential** 개체를 입력 `Get-Credential` 합니다. 사용자 이름을 입력 하는 경우이 cmdlet은 암호를 묻는 메시지를 표시 합니다.

원격 컴퓨터에 연결할 수 있는 권한을 가진 사용자 계정을 지정하려면 **LocalCredential** 매개 변수를 사용합니다.

이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: Local, Remote
Aliases: Credential

Required: False (Local), True (Remote)
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -워크 그룹

컴퓨터가 도메인에서 제거될 때 컴퓨터가 추가되어 있는 작업 그룹의 이름을 지정합니다. 기본값은 **작업 그룹** 입니다. 또한 도메인에서 컴퓨터를 제거할 때 해당 컴퓨터를 작업 그룹에 추가해야 합니다.

이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.

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

### System.String

컴퓨터 이름을 thiscmdlet로 파이프 할 수 있습니다.

## 출력

### Microsoft. PowerShell. ComputerChangeInfo

**PassThru** 매개 변수를 사용 하는 경우 `Remove-Computer` **computerchangeinfo** 개체를 반환 합니다.
그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.

## 참고

이 cmdlet은 작업 그룹에 컴퓨터를 제거하지 않습니다.

## 관련 링크

[Add-Computer](Add-Computer.md)

[Checkpoint-Computer](Checkpoint-Computer.md)

[Remove-Computer](Remove-Computer.md)

[Rename-Computer](Rename-Computer.md)

[Restart-Computer](Restart-Computer.md)

[Restore-Computer](Restore-Computer.md)

[Stop-Computer](Stop-Computer.md)

[Test-Connection](Test-Connection.md)
