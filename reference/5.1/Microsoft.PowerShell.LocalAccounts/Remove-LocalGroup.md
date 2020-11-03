---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/remove-localgroup?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-LocalGroup
ms.openlocfilehash: 6a2f921972fef1794581b301df6e7439e56c7f47
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93214674"
---
# Remove-LocalGroup

## 개요
로컬 보안 그룹을 삭제 합니다.

## SYNTAX

### InputObject

```
Remove-LocalGroup [-InputObject] <LocalGroup[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### 기본값

```
Remove-LocalGroup [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### SecurityIdentifier

```
Remove-LocalGroup [-SID] <SecurityIdentifier[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명
**LocalGroup** cmdlet은 로컬 보안 그룹을 삭제 합니다.
이 cmdlet은 로컬 그룹만 삭제 합니다.
해당 그룹에 속한 사용자 계정, 컴퓨터 계정 또는 그룹 계정은 삭제 되지 않습니다.
삭제 된 그룹은 복구할 수 없습니다.

그룹을 삭제 하 고 그룹 이름이 같은 다른 그룹을 만든 경우 새 그룹에 대 한 새 권한을 설정 해야 합니다.
새 그룹은 해당 그룹에 할당 된 사용 권한을 상속 하지 않습니다.

> [!NOTE]
> 64 비트 시스템의 32 비트 PowerShell에서는 Microsoft. PowerShell. LocalAccounts 모듈을 사용할 수 없습니다.

## 예제

### 예제 1: 보안 그룹 삭제

```
PS C:\> Remove-LocalGroup -Name "SecurityGroup04"
```

이 명령은 SecurityGroup04 라는 그룹을 삭제 합니다.

## PARAMETERS

### -InputObject
이 cmdlet이 삭제 하는 보안 그룹의 배열을 지정 합니다.
그룹을 얻으려면 Get-LocalGroup cmdlet을 사용 합니다.

```yaml
Type: Microsoft.PowerShell.Commands.LocalGroup[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Name
이 cmdlet이 삭제 하는 보안 그룹의 이름 배열을 지정 합니다.

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
이 cmdlet이 삭제 하는 보안 그룹의 보안 Id (Sid) 배열을 지정 합니다.

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

### SecurityAccountsManager. LocalGroup, System.string, SecurityIdentifier.. n a m a.
보안 그룹, 문자열 또는 SID를이 cmdlet으로 파이프 할 수 있습니다.

## 출력

### 없음
이 cmdlet은 어떠한 출력도 생성하지 않습니다.

## 참고

* 이 cmdlet은 다음과 같은 기본 그룹을 삭제할 수 없습니다.

- 관리자
- Backup Operators
- Cryptographic Operators
- Distributed COM Users
- Event Log Readers
- 게스트
- Hyper-V 관리자
- IIS_IUSRS
- Network Configuration Operators
- 성능 로그 사용자
- 성능 모니터 사용자
- Power Users
- Remote Desktop Users
- 원격 관리 사용자
- Replicator
- 사용자
- WinRMRemoteWMIUsers__

* **Principalsource** 속성은 개체의 소스를 설명 하는 **localuser** , **LocalGroup** 및 **localuser** 개체의 속성입니다. 가능한 소스는 다음과 같습니다.

- 로컬
- Active Directory
- Azure Active Directory 그룹
- Microsoft 계정

**Principalsource** 는 windows 10, windows Server 2016 이상 버전의 windows 운영 체제 에서만 지원 됩니다. 이전 버전의 경우 속성은 비어 있습니다.

## 관련 링크

[Get-LocalGroup](Get-LocalGroup.md)

[New-LocalGroup](New-LocalGroup.md)

[Rename-LocalGroup](Rename-LocalGroup.md)

[Set-LocalGroup](Set-LocalGroup.md)
