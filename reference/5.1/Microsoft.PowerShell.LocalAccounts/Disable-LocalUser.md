---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/disable-localuser?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-LocalUser
ms.openlocfilehash: a62242251da00688d3299c60e4cdae7aae6f581a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93211922"
---
# Disable-LocalUser

## 개요
로컬 사용자 계정을 사용 하지 않도록 설정 합니다.

## SYNTAX

### InputObject

```
Disable-LocalUser [-InputObject] <LocalUser[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### 기본값

```
Disable-LocalUser [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### SecurityIdentifier

```
Disable-LocalUser [-SID] <SecurityIdentifier[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명
**Disable-localuser** cmdlet은 로컬 사용자 계정을 사용 하지 않도록 설정 합니다.
사용자 계정이 사용 하지 않도록 설정 된 경우 사용자가 로그온 할 수 없습니다.
사용자 계정을 사용 하도록 설정 하면 사용자가 로그온 할 수 있습니다.

> [!NOTE]
> 64 비트 시스템의 32 비트 PowerShell에서는 Microsoft. PowerShell. LocalAccounts 모듈을 사용할 수 없습니다.

## 예제

### 예 1: 이름을 지정 하 여 계정을 사용 하지 않도록 설정

```
PS C:\> Disable-LocalUser -Name "Admin02"
```

이 명령은 Admin02 이라는 사용자 계정을 사용 하지 않도록 설정 합니다.

### 예제 2: 파이프라인을 사용 하 여 계정 사용 안 함

```
PS C:\> Get-LocalUser Guest | Disable-LocalUser
```

이 명령은 **LocalUser** 를 사용 하 여 기본 제공 게스트 계정을 가져온 다음 파이프라인 연산자를 사용 하 여 현재 cmdlet으로 전달 합니다.
이 cmdlet은 해당 계정을 사용 하지 않도록 설정 합니다.

## PARAMETERS

### -InputObject
이 cmdlet이 사용 하지 않도록 설정 하는 사용자 계정 배열을 지정 합니다.
사용자 계정을 가져오려면 Get-LocalUser cmdlet을 사용 합니다.

```yaml
Type: Microsoft.PowerShell.Commands.LocalUser[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Name
이 cmdlet이 사용 하지 않도록 설정 된 사용자 계정의 이름 배열을 지정 합니다.

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -SID
이 cmdlet이 사용 하지 않도록 설정 하는 사용자 계정 배열을 지정 합니다.

```yaml
Type: System.Security.Principal.SecurityIdentifier[]
Parameter Sets: SecurityIdentifier
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
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

### SecurityAccountsManager, SecurityIdentifier, system.web. 사용자. n a m l.
로컬 사용자, 문자열 또는 SID를이 cmdlet으로 파이프 할 수 있습니다.

## 출력

### 없음
이 cmdlet은 어떠한 출력도 생성하지 않습니다.

## 참고

* **Principalsource** 속성은 개체의 소스를 설명 하는 **localuser** , **LocalGroup** 및 **localuser** 개체의 속성입니다. 가능한 소스는 다음과 같습니다.

- 로컬
- Active Directory
- Azure Active Directory 그룹
- Microsoft 계정

**Principalsource** 는 windows 10, windows Server 2016 이상 버전의 windows 운영 체제 에서만 지원 됩니다. 이전 버전의 경우 속성은 비어 있습니다.

## 관련 링크

[Enable-LocalUser](Enable-LocalUser.md)

[Get-LocalUser](Get-LocalUser.md)

[New-LocalUser](New-LocalUser.md)

[Remove-LocalUser](Remove-LocalUser.md)

[Rename-LocalUser](Rename-LocalUser.md)

[Set-LocalUser](Set-LocalUser.md)
