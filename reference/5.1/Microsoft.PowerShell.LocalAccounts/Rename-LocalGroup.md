---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/rename-localgroup?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Rename-LocalGroup
ms.openlocfilehash: 566d33bdeb52323cca41fa9757d36334b40f1654
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93215625"
---
# Rename-LocalGroup

## 개요
로컬 보안 그룹의 이름을 바꿉니다.

## SYNTAX

### InputObject

```
Rename-LocalGroup [-InputObject] <LocalGroup> [-NewName] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### 기본값

```
Rename-LocalGroup [-Name] <String> [-NewName] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### SecurityIdentifier

```
Rename-LocalGroup [-NewName] <String> [-SID] <SecurityIdentifier> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명
**LocalGroup** cmdlet은 로컬 보안 그룹의 이름을 바꿉니다.

> [!NOTE]
> 64 비트 시스템의 32 비트 PowerShell에서는 Microsoft. PowerShell. LocalAccounts 모듈을 사용할 수 없습니다.

## 예제

### 예제 1: 그룹 이름 변경

```
PS C:\> Rename-LocalGroup -Name "SecurityGroup" -NewName "SecurityGroup04"
```

이 명령은 SecurityGroup 이라는 보안 그룹의 이름을 바꿉니다.

## PARAMETERS

### -InputObject
이 cmdlet이 이름을 바꿀 보안 그룹을 지정 합니다.
보안 그룹을 얻으려면 Get-LocalGroup cmdlet을 사용 합니다.

```yaml
Type: Microsoft.PowerShell.Commands.LocalGroup
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Name
이 cmdlet이 이름을 바꿀 보안 그룹의 이름을 지정 합니다.

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

### -NewName
보안 그룹의 새 이름을 지정 합니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SID
이 cmdlet이 이름을 바꾸는 보안 그룹의 SID (보안 ID)를 지정 합니다.

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

* **Principalsource** 속성은 개체의 소스를 설명 하는 **localuser** , **LocalGroup** 및 **localuser** 개체의 속성입니다. 가능한 소스는 다음과 같습니다.

- 로컬
- Active Directory
- Azure Active Directory 그룹
- Microsoft 계정

**Principalsource** 는 windows 10, windows Server 2016 이상 버전의 windows 운영 체제 에서만 지원 됩니다. 이전 버전의 경우 속성은 비어 있습니다.

## 관련 링크

[Get-LocalGroup](Get-LocalGroup.md)

[New-LocalGroup](New-LocalGroup.md)

[Remove-LocalGroup](Remove-LocalGroup.md)

[Set-LocalGroup](Set-LocalGroup.md)
