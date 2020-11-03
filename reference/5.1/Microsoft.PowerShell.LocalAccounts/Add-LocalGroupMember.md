---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 04/09/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/add-localgroupmember?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-LocalGroupMember
ms.openlocfilehash: 06993c8f6618472f4809e37fbf83d298d13ae515
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93211929"
---
# Add-LocalGroupMember

## 개요
로컬 그룹에 멤버를 추가 합니다.

## SYNTAX

### 그룹

```
Add-LocalGroupMember [-Group] <LocalGroup> [-Member] <LocalPrincipal[]> [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### 기본값

```
Add-LocalGroupMember [-Member] <LocalPrincipal[]> [-Name] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### SecurityIdentifier

```
Add-LocalGroupMember [-Member] <LocalPrincipal[]> [-SID] <SecurityIdentifier> [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## 설명

`Add-LocalGroupMember`Cmdlet은 로컬 보안 그룹에 사용자 또는 그룹을 추가 합니다. 그룹에 할당된 권리와 사용 권한은 모두 해당 그룹의 구성원 전체에게 할당됩니다.

로컬 컴퓨터의 Administrators 그룹 구성원은 해당 컴퓨터에 대한 모든 권한을 갖습니다. Administrators 그룹의 사용자 수를 제한할 수 있습니다.

컴퓨터가 도메인에 가입되어 있는 경우에는 해당 도메인과 트러스트된 도메인의 사용자 계정, 컴퓨터 계정 및 그룹 계정을 로컬 그룹에 추가할 수 있습니다.

> [!NOTE]
> 컴퓨터가 도메인에 가입 되어 있는 경우 도메인의 구성원과 이름이 같은 로컬 사용자를 추가 하려고 하면 도메인 구성원이 추가 됩니다.

## 예제

### 예제 1: Administrators 그룹에 멤버 추가

이 명령은 로컬 Administrators 그룹에 여러 개의 멤버를 추가 합니다. 새 구성원에는 로컬 사용자 계정, Microsoft 계정, Azure Active Directory 계정 및 도메인 그룹이 포함 됩니다. 이 예제에서는 Outlook.com에서 계정의 사용자 이름에 자리 표시자 값을 사용 합니다.

```powershell
Add-LocalGroupMember -Group "Administrators" -Member "Admin02", "MicrosoftAccount\username@Outlook.com", "AzureAD\DavidChew@contoso.com", "CONTOSO\Domain Admins"
```

## PARAMETERS

### -그룹

이 cmdlet이 구성원을 추가할 보안 그룹을 지정 합니다.

```yaml
Type: Microsoft.PowerShell.Commands.LocalGroup
Parameter Sets: Group
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Member

이 cmdlet이 보안 그룹에 추가 하는 사용자 또는 그룹의 배열을 지정 합니다. 이름, SID (보안 ID) 또는 **Localprincipal** 개체를 기준으로 사용자 또는 그룹을 지정할 수 있습니다.

```yaml
Type: Microsoft.PowerShell.Commands.LocalPrincipal[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Name

이 cmdlet이 멤버를 추가 하는 보안 그룹의 이름을 지정 합니다.

```yaml
Type: System.String
Parameter Sets: Default
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SID

이 cmdlet이 멤버를 추가 하는 보안 그룹의 보안 ID를 지정 합니다.

```yaml
Type: System.Security.Principal.SecurityIdentifier
Parameter Sets: SecurityIdentifier
Aliases:

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

### SecurityAccountsManager. LocalGroup, System.string, SecurityIdentifier.. n a m a.

로컬 보안 주체, 문자열 또는 SID를이 cmdlet으로 파이프 할 수 있습니다.

## 출력

### 없음

이 cmdlet은 어떠한 출력도 생성하지 않습니다.

## 참고

64 비트 시스템의 32 비트 PowerShell에서는 Microsoft. PowerShell. LocalAccounts 모듈을 사용할 수 없습니다.

**Principalsource** 속성은 개체의 소스를 설명 하는 **localuser** , **LocalGroup** 및 **localuser** 개체의 속성입니다. 가능한 소스는 다음과 같습니다.

- 로컬
- Active Directory
- Azure Active Directory 그룹
- Microsoft 계정

**Principalsource** 는 windows 10, windows Server 2016 이상 버전의 windows 운영 체제 에서만 지원 됩니다. 이전 버전의 경우 속성은 비어 있습니다.

## 관련 링크

[Get-LocalGroupMember](Get-LocalGroupMember.md)

[New-LocalGroup](New-LocalGroup.md)

[Remove-LocalGroupMember](Remove-LocalGroupMember.md)
