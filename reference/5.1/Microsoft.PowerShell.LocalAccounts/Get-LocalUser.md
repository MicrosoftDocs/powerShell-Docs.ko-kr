---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 02/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/get-localuser?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-LocalUser
ms.openlocfilehash: 34210145bcddc8d9420552d637a6cd6e5f8e61cc
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93211889"
---
# Get-LocalUser

## 개요
로컬 사용자 계정을 가져옵니다.

## SYNTAX

### Default (기본값)

```
Get-LocalUser [[-Name] <String[]>] [<CommonParameters>]
```

### SecurityIdentifier

```
Get-LocalUser [[-SID] <SecurityIdentifier[]>] [<CommonParameters>]
```

## 설명

`Get-LocalUser`Cmdlet은 로컬 사용자 계정을 가져옵니다. 이 cmdlet은 기본 제공 되는 기본 제공 사용자 계정, 사용자가 만든 로컬 사용자 계정 및 Microsoft 계정에 연결 된 로컬 계정을 가져옵니다.

> [!NOTE]
> 64 비트 시스템의 32 비트 PowerShell에서는 Microsoft. PowerShell. LocalAccounts 모듈을 사용할 수 없습니다.

## 예제

### 예제 1: 이름을 사용 하 여 계정 가져오기

이 예제에서는 AdminContoso02 이라는 사용자 계정을 가져옵니다.

```powershell
Get-LocalUser -Name "AdminContoso02"
```

```Output
Name             Enabled Description
----             ------- -----------
AdminContoso02   True    Description of this account.
```

### 예 2: Microsoft 계정에 연결 된 계정 가져오기

이 예제에서는 Microsoft 계정에 연결 된 사용자 계정을 가져옵니다. 이 예제에서는 Outlook.com에서 계정의 사용자 이름에 자리 표시자 값을 사용 합니다.

```powershell
Get-LocalUser -Name "MicrosoftAccount\username@Outlook.com"
```

```Output
Name                                    Enabled  Description
----                                    -------  -----------
MicrosoftAccount\username@outlook.com  True     Description of this account.
```

### 예 3: Microsoft 계정에 연결 된 계정 가져오기

이 예제에서는 지정 된 SID를 가진 로컬 사용자 계정을 가져옵니다.

```powershell
Get-LocalUser -SID S-1-5-21-9526073513-1762370368-3942940353-500
```

```Output
Name          Enabled Description
----          ------- -----------
Administrator True    Built-in account for administering the computer/domain
```

## PARAMETERS

### -Name

이 cmdlet이 가져오는 사용자 계정의 이름 배열을 지정 합니다. 와일드 카드 문자를 사용할 수 있습니다.

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -SID

이 cmdlet이 가져오는 사용자 계정의 Sid (보안 Id) 배열을 지정 합니다.

```yaml
Type: System.Security.Principal.SecurityIdentifier[]
Parameter Sets: SecurityIdentifier
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.string (SecurityIdentifier, 시스템)

문자열이 나 SID를이 cmdlet으로 파이프 할 수 있습니다.

## 출력

### SecurityAccountsManager. 사용자 []

이 cmdlet은 로컬 사용자 계정을 반환 합니다.

## 참고

**Localuser** , **LocalGroup** 및 **localuser** 개체의 **principalsource** 속성은 개체의 원본을 설명 합니다. 가능한 소스는 다음과 같습니다.

- 로컬
- Active Directory
- Azure Active Directory 그룹
- Microsoft 계정

**Principalsource** 는 windows 10, windows Server 2016 이상 버전의 windows 운영 체제 에서만 지원 됩니다. 이전 버전의 경우 속성은 비어 있습니다.

## 관련 링크

[Disable-LocalUser](Disable-LocalUser.md)

[Enable-LocalUser](Enable-LocalUser.md)

[New-LocalUser](New-LocalUser.md)

[Remove-LocalUser](Remove-LocalUser.md)

[Rename-LocalUser](Rename-LocalUser.md)

[Set-LocalUser](Set-LocalUser.md)
