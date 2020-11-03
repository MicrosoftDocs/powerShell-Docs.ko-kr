---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/get-localgroupmember?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-LocalGroupMember
ms.openlocfilehash: 200368c5d13bd027302ad824533e6c187906ed0f
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93211890"
---
# Get-LocalGroupMember

## 개요
로컬 그룹에서 멤버를 가져옵니다.

## SYNTAX

### Default (기본값)

```
Get-LocalGroupMember [[-Member] <String>] [-Name] <String> [<CommonParameters>]
```

### 그룹

```
Get-LocalGroupMember [-Group] <LocalGroup> [[-Member] <String>] [<CommonParameters>]
```

### SecurityIdentifier

```
Get-LocalGroupMember [[-Member] <String>] [-SID] <SecurityIdentifier> [<CommonParameters>]
```

## 설명
**Get LocalGroupMember** cmdlet은 로컬 그룹에서 구성원을 가져옵니다.

> [!NOTE]
> 64 비트 시스템의 32 비트 PowerShell에서는 Microsoft. PowerShell. LocalAccounts 모듈을 사용할 수 없습니다.

## 예제

### 예 1: Administrators 그룹의 모든 구성원 가져오기

```
PS C:\> Get-LocalGroupMember -Group "Administrators"
ObjectClass Name                    PrincipalSource
----------- ----                    ---------------
User        CONTOSOPC\Administrator Local
User        CONTOSOPC\LocalAdmin    Local
```

이 명령은 로컬 Administrators 그룹의 모든 구성원을 가져옵니다.

## PARAMETERS

### -그룹
이 cmdlet이 멤버를 가져오는 보안 그룹을 지정 합니다.

```yaml
Type: Microsoft.PowerShell.Commands.LocalGroup
Parameter Sets: Group
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Member
이 cmdlet이 보안 그룹에서 가져온 사용자 또는 그룹을 지정 합니다.
이름 또는 SID (보안 ID)를 기준으로 사용자 또는 그룹을 지정할 수 있습니다.
S-R-I-s-s에서 SID 문자열을 지정 합니다.
. .
형식.
와일드 카드 문자를 사용할 수 있습니다.
이 매개 변수를 지정 하지 않으면 cmdlet은 그룹의 모든 구성원을 가져옵니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name
이 cmdlet이 멤버를 가져오는 보안 그룹의 이름을 지정 합니다.

```yaml
Type: System.String
Parameter Sets: Default
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -SID
이 cmdlet이 구성원을 가져오는 보안 그룹의 보안 ID를 지정 합니다.

```yaml
Type: System.Security.Principal.SecurityIdentifier
Parameter Sets: SecurityIdentifier
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### CommonParameters
이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### SecurityAccountsManager. LocalGroup, System.string, SecurityIdentifier.. n a m a.
로컬 그룹, 문자열 또는 SID를이 cmdlet으로 파이프 할 수 있습니다.

## 출력

### SecurityAccountsManager
이 cmdlet은 로컬 보안 주체를 반환 합니다.

## 참고

* **Principalsource** 속성은 개체의 소스를 설명 하는 **localuser** , **LocalGroup** 및 **localuser** 개체의 속성입니다. 가능한 소스는 다음과 같습니다.

- 로컬
- Active Directory
- Azure Active Directory 그룹
- Microsoft 계정

**Principalsource** 는 windows 10, windows Server 2016 이상 버전의 windows 운영 체제 에서만 지원 됩니다. 이전 버전의 경우 속성은 비어 있습니다.

## 관련 링크

[Add-LocalGroupMember](Add-LocalGroupMember.md)

[New-LocalGroup](New-LocalGroup.md)

[Remove-LocalGroupMember](Remove-LocalGroupMember.md)
