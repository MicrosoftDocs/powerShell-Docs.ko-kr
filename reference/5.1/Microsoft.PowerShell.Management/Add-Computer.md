---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/add-computer?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-Computer
ms.openlocfilehash: e3d1c5c071a334bddbfbc547ef2cc07e9e5c90aa
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388351"
---
# Add-Computer

## 개요
로컬 컴퓨터를 도메인 또는 작업 그룹에 추가합니다.

## SYNTAX

### 도메인 (기본값)

```
Add-Computer [-ComputerName <String[]>] [-LocalCredential <PSCredential>]
 [-UnjoinDomainCredential <PSCredential>] -Credential <PSCredential> [-DomainName] <String> [-OUPath <String>]
 [-Server <String>] [-Unsecure] [-Options <JoinOptions>] [-Restart] [-PassThru] [-NewName <String>] [-Force]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### 작업 그룹

```
Add-Computer [-ComputerName <String[]>] [-LocalCredential <PSCredential>] [-Credential <PSCredential>]
 [-WorkgroupName] <String> [-Restart] [-PassThru] [-NewName <String>] [-Force] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## 설명

`Add-Computer`Cmdlet은 로컬 컴퓨터 또는 원격 컴퓨터를 도메인 또는 작업 그룹에 추가 하거나 한 도메인에서 다른 도메인으로 이동 합니다. 컴퓨터가 계정 없이 도메인에 추가된 경우 도메인 계정도 생성됩니다.

이 cmdlet의 매개 변수를 사용하여 OU(조직 구성 단위) 및 도메인 컨트롤러를 지정하거나 보안되지 않은 가입을 수행할 수 있습니다.

명령 결과를 얻으려면 **Verbose** 및 **PassThru** 매개 변수를 사용합니다.

## 예제

### 예 1: 도메인에 로컬 컴퓨터를 추가한 다음 컴퓨터를 다시 시작 합니다.

```powershell
Add-Computer -DomainName Domain01 -Restart
```

이 명령은 Domain01 도메인에 로컬 컴퓨터를 추가한 다음 컴퓨터를 다시 시작하여 변경 내용을 적용합니다.

### 예 2: 작업 그룹에 로컬 컴퓨터 추가

```powershell
Add-Computer -WorkgroupName WORKGROUP-A
```

이 명령은 Workgroup-A 작업 그룹에 로컬 컴퓨터를 추가합니다.

### 예 3: 도메인에 로컬 컴퓨터 추가

```powershell
Add-Computer -DomainName Domain01 -Server Domain01\DC01 -PassThru -Verbose
```

이 명령은 Domain01\DC01 도메인 컨트롤러를 사용하여 로컬 컴퓨터를 Domain01 도메인에 추가합니다.

이 명령은 **PassThru** 및 **Verbose** 매개 변수를 사용하여 명령의 결과에 대한 자세한 정보를 가져옵니다.

### 예제 4: OUPath 매개 변수를 사용 하 여 도메인에 로컬 컴퓨터 추가

```powershell
Add-Computer -DomainName Domain02 -OUPath "OU=testOU,DC=domain,DC=Domain,DC=com"
```

이 명령은 Domain02 도메인에 로컬 컴퓨터를 추가합니다.
OUPath 매개 변수를 사용하여 새 계정의 조직 구성 단위를 지정합니다.

### 예 5: 자격 증명을 사용 하 여 도메인에 로컬 컴퓨터 추가

```powershell
Add-Computer -ComputerName Server01 -LocalCredential Server01\Admin01 -DomainName Domain02 -Credential Domain02\Admin02 -Restart -Force
```

이 명령은 Domain02 도메인에 Server01 컴퓨터를 추가합니다. **LocalCredential** 매개 변수를 사용하여 Server01 컴퓨터에 연결할 수 있는 권한을 가진 사용자 계정을 지정합니다. **Credential** 매개 변수를 사용하여 도메인에 컴퓨터를 가입시킬 수 있는 권한을 가진 사용자 계정을 지정합니다. **Restart** 매개 변수를 사용하여 가입 작업이 완료된 후 컴퓨터를 다시 시작하고 **Force** 매개 변수를 사용하여 사용자 확인 메시지를 표시하지 않습니다.

### 예제 6: 컴퓨터 그룹을 새 도메인으로 이동

```powershell
Add-Computer -ComputerName Server01, Server02, localhost -DomainName Domain02 -LocalCredential Domain01\User01 -UnjoinDomainCredential Domain01\Admin01 -Credential Domain02\Admin01 -Restart
```

이 명령은 Domain01에서 Domain02로 Server01 및 Server02 컴퓨터와 로컬 컴퓨터를 이동합니다.

**LocalCredential** 매개 변수를 사용하여 영향받는 3대의 컴퓨터에 연결할 수 있는 권한을 가진 사용자 계정을 지정합니다. **UnjoinDomainCredential** 매개 변수를 사용하여 Domain01 도메인에서 컴퓨터를 가입 해지할 수 있는 권한을 가진 사용자 계정을 지정하고 **Credential** 매개 변수를 사용하여 Domain02 도메인에 컴퓨터를 가입시킬 수 있는 권한을 가진 사용자 계정을 지정합니다. **Restart** 매개 변수를 사용하여 이동이 완료된 후 3대의 컴퓨터를 모두 다시 시작합니다.

### 예 7: 컴퓨터를 새 도메인으로 이동 하 고 컴퓨터 이름을 변경 합니다.

```powershell
Add-Computer -ComputerName Server01 -DomainName Domain02 -NewName Server044 -Credential Domain02\Admin01 -Restart
```

이 명령은 Server01 컴퓨터를 Domain02로 이동하고 컴퓨터 이름을 Server044로 변경합니다.

이 명령은 현재 사용자의 자격 증명을 사용하여 Server01 컴퓨터에 연결하고 현재 도메인에서 가입을 해제합니다. **Credential** 매개 변수를 사용 하 여 Domain02 도메인에 컴퓨터를 가입 시킬 수 있는 권한을 가진 사용자 계정을 지정 합니다.

### 예 8: 파일에 나열 된 컴퓨터를 새 도메인에 추가

```powershell
Add-Computer -ComputerName (Get-Content Servers.txt) -DomainName Domain02 -Credential Domain02\Admin02 -Options Win9xUpgrade  -Restart
```

이 명령은 Servers.txt 파일에 나열된 컴퓨터만 Domain02 도메인에 추가합니다. **Options** 매개 변수를 사용하여 **Win9xUpgrade** 옵션을 지정합니다. **Restart** 매개 변수는 가입 작업이 완료된 후 새로 추가된 모든 컴퓨터를 다시 시작합니다.

### 예 9: 미리 정의 된 컴퓨터 자격 증명을 사용 하 여 도메인에 컴퓨터 추가

이 첫 번째 명령은 이미 도메인에 가입 되어 있는 컴퓨터의 관리자가 실행 해야 합니다 `Domain03` .

```powershell
New-ADComputer -Name "Server02" -AccountPassword (ConvertTo-SecureString -String 'TempJoinPA$$' -AsPlainText -Force)

# Then this command is run from `Server02` which is not yet domain-joined:

$joinCred = New-Object pscredential -ArgumentList ([pscustomobject]@{
    UserName = $null
    Password = (ConvertTo-SecureString -String 'TempJoinPA$$' -AsPlainText -Force)[0]
})
Add-Computer -Domain "Domain03" -Options UnsecuredJoin,PasswordPass -Credential $joinCred
```

이 명령 조합은 기존 도메인에 가입 된 컴퓨터를 사용 하 여 도메인에 미리 정의 된 이름 및 임시 조인 암호를 사용 하 여 새 컴퓨터 계정을 만듭니다. 그런 다음, 컴퓨터 이름과 임시 조인 암호만 사용 하 여 미리 정의 된 이름을 사용 하는 컴퓨터가 도메인에 가입 됩니다.
미리 정의 된 암호는 가입 작업을 지 원하는 데만 사용 되며 컴퓨터가 조인을 완료 한 후 정상적인 컴퓨터 계정 절차의 일부로 대체 됩니다.

## PARAMETERS

### -ComputerName

도메인 또는 작업 그룹에 추가할 컴퓨터를 지정합니다.
기본값은 로컬 컴퓨터입니다.

각 원격 컴퓨터의 NetBIOS 이름, IP (인터넷 프로토콜) 주소 또는 정규화 된 도메인 이름을 입력 합니다. 로컬 컴퓨터를 지정 하려면 컴퓨터 이름, 점 ( `.` ) 또는 "localhost"를 입력 합니다.

이 매개 변수는 Windows PowerShell 원격 기능을 사용하지 않습니다. **ComputerName** `Add-Computer` 컴퓨터가 원격 명령을 실행 하도록 구성 되지 않은 경우에도의 ComputerName 매개 변수를 사용할 수 있습니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입되었습니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Local computer
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Credential

새 도메인에 컴퓨터를 가입시킬 수 있는 권한을 가진 사용자 계정을 지정합니다.
기본값은 현재 사용자입니다.

"User01" 또는 "Domain01\User01"과 같은 사용자 이름을 입력 하거나, cmdlet에 의해 생성 된 것과 같은 **PSCredential** 개체를 입력 합니다 `Get-Credential` . 사용자 이름을 입력하면 암호를 입력하라는 메시지가 표시됩니다.

현재 도메인에서 컴퓨터를 제거할 수 있는 권한을 가진 사용자 계정을 지정하려면 **UnjoinDomainCredential** 매개 변수를 사용합니다. 원격 컴퓨터에 연결할 수 있는 권한을 가진 사용자 계정을 지정하려면 **LocalCredential** 매개 변수를 사용합니다.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: Domain, Workgroup
Aliases: DomainCredential

Required: True (Domain), False (Workgroup)
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DomainName

컴퓨터가 추가된 도메인을 지정합니다. 컴퓨터를 도메인에 추가할 때 이 매개 변수는 필수입니다.

```yaml
Type: System.String
Parameter Sets: Domain
Aliases: DN, Domain

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

사용자 확인 메시지를 표시하지 않습니다. 이 매개 변수를 `Add-Computer` 사용 하지 않으면 각 컴퓨터의 추가를 확인 해야 합니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입되었습니다.

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

### -LocalCredential

**ComputerName** 매개 변수로 지정된 컴퓨터에 연결할 수 있는 권한을 가진 사용자 계정을 지정합니다. 기본값은 현재 사용자입니다.

"User01" 또는 "Domain01\User01"과 같은 사용자 이름을 입력 하거나, cmdlet에 의해 생성 된 것과 같은 **PSCredential** 개체를 입력 합니다 `Get-Credential` . 사용자 이름을 입력하면 암호를 입력하라는 메시지가 표시됩니다.

새 도메인에 컴퓨터를 추가할 수 있는 권한을 가진 사용자 계정을 지정하려면 **Credential** 매개 변수를 사용합니다. 현재 도메인에서 컴퓨터를 제거할 수 있는 권한을 가진 사용자 계정을 지정하려면 **UnjoinDomainCredential** 매개 변수를 사용합니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입되었습니다.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### -NewName

새 도메인의 새로운 컴퓨터 이름을 지정합니다. 이 매개 변수는 한 컴퓨터만 추가하거나 이동하는 경우에만 유효합니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입되었습니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -옵션

**컴퓨터 추가** 조인 작업에 대 한 고급 옵션을 지정 합니다. 쉼표로 구분된 문자열로 값을 하나 이상 입력하세요.

이 매개 변수에 허용되는 값은 다음과 같습니다.

- **Accountcreate** : 도메인 계정을 만듭니다. 컴퓨터 **추가** cmdlet은 도메인에 컴퓨터를 추가할 때 자동으로 도메인 계정을 만듭니다. 이 옵션은 완전성을 위해 포함 되었습니다.

- **Win9XUpgrade** : 가입 작업이 Windows 운영 체제 업그레이드의 일부임을 나타냅니다.

- **UnsecuredJoin** : 보안 되지 않은 조인을 수행 합니다. 보안 되지 않은 조인을 요청 *하려면 보안 되지 않은 매개 변수* 또는이 옵션을 사용 합니다. 컴퓨터 암호를 전달 하려는 경우이 옵션을 옵션과 함께 사용 해야 합니다 `PasswordPass` .

- **Passwordpass** : 보안 되지 않은 조인을 수행한 후 *자격 증명* (DomainCredential) 매개 변수 값으로 컴퓨터 암호를 설정 합니다. 이 옵션은 *Credential* (DomainCredential) 매개 변수 값이 사용자 암호가 아닌 컴퓨터 암호인 것도 나타냅니다. 이 옵션은 옵션이 지정 된 경우에만 유효 `UnsecuredJoin` 합니다. 이 옵션을 사용 하는 경우 매개 변수에 제공 된 자격 증명에 `-Credential` null 사용자 이름이 *있어야* 합니다.

- **Joinwithnewname** : 새 도메인의 컴퓨터 이름을 *NewName* 매개 변수로 지정 된 이름으로 바꿉니다. *NewName* 매개 변수를 사용하는 경우 이 옵션은 자동으로 설정됩니다. 이 옵션은 Rename-Computer cmdlet과 함께 사용 하도록 설계 되었습니다. 컴퓨터 **이름 바꾸기 cmdlet을** 사용 하 여 컴퓨터 이름을 변경 하 고 변경 내용을 적용 하기 위해 컴퓨터를 다시 시작 하지 않는 경우이 매개 변수를 사용 하 여 컴퓨터를 새 이름으로 도메인에 가입 시킬 수 있습니다.

- **Joinreadonly** : 기존 컴퓨터 계정을 사용 하 여 컴퓨터를 읽기 전용 도메인 컨트롤러에 가입 시킵니다. 컴퓨터 계정은 암호 복제 정책에 대해 허용 된 목록에 추가 해야 하며, 가입 작업 전에 계정 암호를 읽기 전용 도메인 컨트롤러에 복제 해야 합니다.

- **Installinvoke** : **JoinDomainOrWorkgroup** 메서드의 **fjoinoptions** 매개 변수에 대 한 create (0x2) 및 delete (0x4) 플래그를 설정 합니다. **JoinDomainOrWorkgroup** 메서드에 대 한 자세한 내용은 [Win32_ComputerSystem 클래스의 JoinDomainOrWorkgroup 메서드](/windows/win32/cimwin32prov/joindomainorworkgroup-method-in-class-win32-computersystem)를 참조 하세요.
  이러한 옵션에 대 한 자세한 내용은 [NetJoinDomain 함수](/windows/win32/api/lmjoin/nf-lmjoin-netjoindomain)를 참조 하세요.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: Microsoft.PowerShell.Commands.JoinOptions
Parameter Sets: Domain
Aliases:
Accepted values: AccountCreate, Win9XUpgrade, UnsecuredJoin, PasswordPass, DeferSPNSet, JoinWithNewName, JoinReadOnly, InstallInvoke

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -OUPath

도메인 계정의 OU(조직 구성 단위)를 지정합니다. 따옴표로 OU의 전체 고유 이름을 입력합니다. 기본값은 도메인의 컴퓨터 개체에 대한 기본 OU입니다.

```yaml
Type: System.String
Parameter Sets: Domain
Aliases: OU

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PassThru

작업 중인 항목을 나타내는 개체를 반환합니다. 기본적으로 이 cmdlet은 출력을 생성하지 않습니다.

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

도메인 또는 작업 그룹에 추가된 컴퓨터를 다시 시작합니다. 변경 내용을 적용하려면 컴퓨터를 자주 다시 시작해야 합니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입되었습니다.

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

### -Server

도메인에 컴퓨터를 추가하는 도메인 컨트롤러의 이름을 지정합니다. 도메인이름\컴퓨터이름 형식으로 이름을 입력합니다. 기본적으로 도메인 컨트롤러는 지정되지 않습니다.

```yaml
Type: System.String
Parameter Sets: Domain
Aliases: DC

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UnjoinDomainCredential

현재 도메인에서 컴퓨터를 제거할 수 있는 권한을 가진 사용자 계정을 지정합니다. 기본값은 현재 사용자입니다.

"User01" 또는 "Domain01\User01"과 같은 사용자 이름을 입력 하거나, cmdlet에 의해 생성 된 것과 같은 **PSCredential** 개체를 입력 합니다 `Get-Credential` . 사용자 이름을 입력하면 암호를 입력하라는 메시지가 표시됩니다.

다른 도메인으로 컴퓨터를 이동하는 경우 이 매개 변수를 사용합니다. 새 도메인에 가입할 수 있는 권한을 가진 사용자 계정을 지정하려면 **Credential** 매개 변수를 사용합니다. 원격 컴퓨터에 연결할 수 있는 권한을 가진 사용자 계정을 지정하려면 **LocalCredential** 매개 변수를 사용합니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입되었습니다.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: Domain
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -안전 하지 않음

지정된 도메인에 대한 보안되지 않은 가입을 수행합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Domain
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -워크 그룹

컴퓨터가 추가된 작업 그룹의 이름을 지정합니다. 기본값은 "WORKGROUP"입니다.

```yaml
Type: System.String
Parameter Sets: Workgroup
Aliases: WGN

Required: True
Position: 0
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

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.

## 입력

### System.String

컴퓨터 이름과 새 이름을 Cmdlet으로 파이프 할 수 있습니다 `Add-Computer` .

## 출력

### Microsoft. PowerShell. ComputerChangeInfo

**PassThru** 매개 변수를 사용 하는 경우 `Add-Computer` **computerchangeinfo** 개체를 반환 합니다.
그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.

## 참고

- Windows PowerShell 2.0에서 **서버 매개 변수** 는 `Add-Computer` 서버가 있는 경우에도 실패 합니다. Windows PowerShell 3.0에서는 **Server** 매개 변수의 구현이 안정적으로 작동되도록 변경됩니다.

## 관련 링크

[Checkpoint-Computer](Checkpoint-Computer.md)

[Remove-Computer](Remove-Computer.md)

[Restart-Computer](Restart-Computer.md)

[Rename-Computer](Rename-Computer.md)

[Restore-Computer](Restore-Computer.md)

[Stop-Computer](Stop-Computer.md)

[Test-Connection](Test-Connection.md)
