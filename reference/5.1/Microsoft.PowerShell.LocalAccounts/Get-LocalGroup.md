---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/get-localgroup?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-LocalGroup
ms.openlocfilehash: 2cd77c2766840527825b0ccf68abaac3c2ea6c16
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93211905"
---
# Get-LocalGroup

## 개요
로컬 보안 그룹을 가져옵니다.

## SYNTAX

### Default (기본값)

```
Get-LocalGroup [[-Name] <String[]>] [<CommonParameters>]
```

### SecurityIdentifier

```
Get-LocalGroup [[-SID] <SecurityIdentifier[]>] [<CommonParameters>]
```

## 설명
**LocalGroup** Cmdlet은 보안 계정 관리자에서 로컬 보안 그룹을 가져옵니다.
이 cmdlet은 기본 제공 되는 기본 제공 그룹 및 사용자가 만든 로컬 보안 그룹을 가져옵니다.

> [!NOTE]
> 64 비트 시스템의 32 비트 PowerShell에서는 Microsoft. PowerShell. LocalAccounts 모듈을 사용할 수 없습니다.

## 예제

### 예 1: Administrators 그룹 가져오기

```
PS C:\> Get-LocalGroup -Name "Administrators"
Name           Description
----           -----------
Administrators Administrators have complete and unrestricted access to the computer/domain
```

이 명령은 로컬 관리자 그룹을 가져옵니다.
이 명령은 콘솔에서 그룹의 속성을 표시 합니다.

## PARAMETERS

### -Name
이 cmdlet이 가져오는 보안 그룹의 이름 배열을 지정 합니다.
와일드 카드 문자를 사용할 수 있습니다.

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -SID
이 cmdlet이 가져오는 보안 그룹의 Sid (보안 Id) 배열을 지정 합니다.

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

### SecurityAccountsManager. LocalGroup
이 cmdlet은 로컬 그룹을 반환 합니다.

## 참고

* **Principalsource** 속성은 개체의 소스를 설명 하는 **localuser** , **LocalGroup** 및 **localuser** 개체의 속성입니다. 가능한 소스는 다음과 같습니다.

- 로컬
- Active Directory
- Azure Active Directory 그룹
- Microsoft 계정

**Principalsource** 는 windows 10, windows Server 2016 이상 버전의 windows 운영 체제 에서만 지원 됩니다. 이전 버전의 경우 속성은 비어 있습니다.

## 관련 링크

[New-LocalGroup](New-LocalGroup.md)

[Remove-LocalGroup](Remove-LocalGroup.md)

[Rename-LocalGroup](Rename-LocalGroup.md)

[Set-LocalGroup](Set-LocalGroup.md)
