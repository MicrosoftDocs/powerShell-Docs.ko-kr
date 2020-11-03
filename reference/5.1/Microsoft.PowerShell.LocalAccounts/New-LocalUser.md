---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/new-localuser?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-LocalUser
ms.openlocfilehash: d83f3ad12481df0849ff2fe3f61d553a9ffdcdde
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93214673"
---
# New-LocalUser

## 개요

로컬 사용자 계정을 만듭니다.

## SYNTAX

### 암호 (기본값)

```
New-LocalUser [-AccountExpires <DateTime>] [-AccountNeverExpires] [-Description <String>] [-Disabled]
 [-FullName <String>] [-Name] <String> -Password <SecureString> [-PasswordNeverExpires]
 [-UserMayNotChangePassword] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### NoPassword

```
New-LocalUser [-AccountExpires <DateTime>] [-AccountNeverExpires] [-Description <String>] [-Disabled]
 [-FullName <String>] [-Name] <String> [-NoPassword] [-UserMayNotChangePassword] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## 설명

`New-LocalUser`Cmdlet은 로컬 사용자 계정을 만듭니다. 이 cmdlet은 Microsoft 계정에 연결 된 로컬 사용자 계정 또는 로컬 사용자 계정을 만듭니다.

> [!NOTE]
> 64 비트 시스템의 32 비트 PowerShell에서는 Microsoft. PowerShell. LocalAccounts 모듈을 사용할 수 없습니다.

## 예제

### 예제 1: 사용자 계정 만들기

```
PS C:\> New-LocalUser -Name "User02" -Description "Description of this account." -NoPassword
Name    Enabled  Description
----    -------  -----------
User02  True     Description of this account.
```

이 명령은 로컬 사용자 계정을 만들고 **Accountexpires** 또는 **Password** 매개 변수를 지정 하지 않습니다. 따라서 계정은 기본적으로 만료 되거나 암호가 포함 되지 않습니다.

### 예 2: 암호를 포함 하는 사용자 계정 만들기

```
PS C:\> $Password = Read-Host -AsSecureString
PS C:\> New-LocalUser "User03" -Password $Password -FullName "Third User" -Description "Description of this account."
Name    Enabled  Description
----    -------  -----------
User03  True     Description of this account.
```

첫 번째 명령은 cmdlet을 사용 하 여 암호를 묻는 메시지를 표시 합니다 `Read-Host` . 명령은 암호를 변수에 보안 문자열로 저장 합니다 `$Password` .

두 번째 명령은에 저장 된 암호를 사용 하 여 로컬 사용자 계정을 만듭니다 `$Password` . 이 명령은 사용자 이름, 전체 이름 및 사용자 계정에 대 한 설명을 지정 합니다.

## PARAMETERS

### -AccountExpires

사용자 계정이 만료 되는 시점을 지정 합니다. **DateTime** 개체를 가져오려면 cmdlet을 사용 `Get-Date` 합니다.
이 매개 변수를 지정 하지 않으면 계정이 만료 되지 않습니다.

```yaml
Type: System.DateTime
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -AccountNeverExpires

계정이 만료 되지 않음을 나타냅니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Description

사용자 계정에 대 한 설명을 지정 합니다.
최대 길이는 48 자입니다.

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

### -사용 안 함

이 cmdlet이 사용자 계정을 사용할 수 없는 것으로 만들기를 나타냅니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -FullName

사용자 계정의 전체 이름을 지정 합니다. 전체 이름이 사용자 계정의 사용자 이름과 다릅니다.

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

### -Name

사용자 계정의 사용자 이름을 지정 합니다.

로컬 시스템에 대 한 로컬 사용자 계정을 만드는 경우 사용자 이름에는 최대 20 자의 대문자 또는 소문자를 사용할 수 있습니다. 사용자 이름에는 다음 문자를 사용할 수 없습니다.

`"`, `/`, `\`, `[`, `]`, `:`, `;`, `|`, `=`, `,`, `+`, `*`, `?`, `<`, `>`, `@`

사용자 이름은 마침표 나 공백으로만 구성 될 수 없습니다 `.` .

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -NoPassword

사용자 계정에 암호가 없음을 나타냅니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NoPassword
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Password

사용자 계정에 대 한 암호를 지정 합니다. `Read-Host -GetCredential`, 또는를 사용 `Get-Credential` 하 여 `ConvertTo-SecureString` 암호에 대 한 **SecureString** 개체를 만들 수 있습니다.

**Password** 및 **nopassword** 매개 변수를 생략 하면에서 `New-LocalUser` 새 사용자의 암호를 묻는 메시지를 표시 합니다.

```yaml
Type: System.Security.SecureString
Parameter Sets: Password
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PasswordNeverExpires

암호가 만료 되는지 여부를 나타냅니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Password
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -UserMayNotChangePassword

사용자가 사용자 계정에 대 한 암호를 변경할 수 없음을 나타냅니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
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

이 cmdlet은,,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` 및 `-WarningVariable` 등의 일반 매개 변수를 지원 합니다. 자세한 내용은 [about_CommonParameters](/reference/6/Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.

## 입력

### System.string, System.string, System.string, System.web. SecureString

이 cmdlet에 문자열, **DateTime** 개체, 부울 값 또는 보안 문자열을 파이프 하 여 사용할 수 있습니다.

## 출력

### SecurityAccountsManager 사용자입니다.

이 cmdlet은 **Localuser** 개체를 반환 합니다.
이 개체는 사용자 계정에 대 한 정보를 제공 합니다.

## 참고

- 사용자 이름은 컴퓨터의 다른 사용자 이름이 나 그룹 이름과 같을 수 없습니다. 사용자 이름은 마침표 나 공백으로만 구성 될 수 없습니다 `.` . 사용자 이름에는 최대 20 자의 대문자 또는 소문자를 사용할 수 있습니다. 사용자 이름에는 다음 문자를 사용할 수 없습니다.

`"`, `/`, `\`, `[`, `]`, `:`, `;`, `|`, `=`, `,`, `+`, `*`, `?`, `<`, `>`, `@`

- 암호에는 최대 127 자까지 사용할 수 있습니다.
- **Principalsource** 속성은 개체의 소스를 설명 하는 **localuser** , **LocalGroup** 및 **localuser** 개체의 속성입니다. 가능한 소스는 다음과 같습니다.

  - 로컬
  - Active Directory
  - Azure Active Directory 그룹
  - Microsoft 계정

> [!NOTE]
> **Principalsource** 는 windows 10, windows Server 2016 이상 버전의 windows 운영 체제 에서만 지원 됩니다. 이전 버전의 경우 속성은 비어 있습니다.

## 관련 링크

[Disable-LocalUser](Disable-LocalUser.md)

[Enable-LocalUser](Enable-LocalUser.md)

[Get-LocalUser](Get-LocalUser.md)

[Remove-LocalUser](Remove-LocalUser.md)

[Rename-LocalUser](Rename-LocalUser.md)

[Set-LocalUser](Set-LocalUser.md)
