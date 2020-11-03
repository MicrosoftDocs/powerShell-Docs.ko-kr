---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/remove-cimsession?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-CimSession
ms.openlocfilehash: 729b0d1c860d29190ab4b87b818dd7b89018bfd7
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93210050"
---
# Remove-CimSession

## 개요
하나 이상의 CIM 세션을 제거 합니다.

## SYNTAX

### CimSessionSet (기본값)

```
Remove-CimSession [-CimSession] <CimSession[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ComputerNameSet

```
Remove-CimSession [-ComputerName] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### SessionIdSet

```
Remove-CimSession [-Id] <UInt32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InstanceIdSet

```
Remove-CimSession -InstanceId <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### NameSet

```
Remove-CimSession -Name <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명

`Remove-CimSession`Cmdlet은 로컬 PowerShell 세션에서 CIM 세션 개체를 하나 이상 제거 합니다.

## 예제

### 예제 1: 모든 CIM 세션 제거

이 예제에서는 [CimSession](Get-CimSession.md) cmdlet을 사용 하 여 로컬 컴퓨터에서 사용 가능한 모든 CIM 세션을 검색 한 다음를 사용 하 여 제거 합니다 `Remove-CimSession` .

```powershell
Get-CimSession | Remove-CimSession
```

### 예 2: 특정 CIM 세션 제거

이 예에서는 **Id** 값이 5 인 CIM 세션을 제거 합니다.

```powershell
Remove-CimSession -Id 5
```

### 예제 3: WhatIf 매개 변수를 사용 하 여 제거할 CIM 세션 목록 표시

이 예제에서는 일반 매개 변수 **WhatIf** 를 사용 하 여 제거를 수행 하지 않도록 지정 하지만 완료 된 경우에만 발생 하는 결과를 출력 합니다.

```powershell
Remove-CimSession -Name a* -WhatIf
```

## PARAMETERS

### -CimSession

종료할 CIM 세션의 세션 개체를 지정 합니다.

CIM 세션을 포함 하는 변수 또는 CIM 세션을 만들거나 가져오는 명령 (예: 또는 cmdlet)을 입력 합니다 [`New-CimSession`](New-CimSession.md) [`Get-CimSession`](Get-CimSession.md) .
자세한 내용은 [about_CimSessions](../Microsoft.PowerShell.Core/About/about_CimSession.md)를 참조 하세요.

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: CimSessionSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -ComputerName

컴퓨터 이름 배열을 지정 합니다. 지정 된 컴퓨터에 연결 되는 세션을 제거 합니다. FQDN (정규화 된 도메인 이름) 또는 NetBIOS 이름을 지정할 수 있습니다.

```yaml
Type: System.String[]
Parameter Sets: ComputerNameSet
Aliases: CN, ServerName

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Id

제거할 CIM 세션의 ID를 지정 합니다. 하나 이상의 Id를 쉼표로 구분 하 여 지정 하거나 범위 연산자 ()를 사용 `..` 하 여 id 범위를 지정 하십시오. **Id** 는 현재 PowerShell 세션에서 CIM 세션을 고유 하 게 식별 하는 정수입니다.

범위 연산자에 대 한 자세한 내용은 [about_Operators](../Microsoft.PowerShell.Core/About/about_Operators.md)를 참조 하세요.

```yaml
Type: System.UInt32[]
Parameter Sets: SessionIdSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -InstanceId

제거할 CIM 세션의 인스턴스 ID를 지정 합니다. **InstanceId** 는 CIM 세션을 고유 하 게 식별 하는 Guid (Globally Unique Identifier)입니다. **InstanceId** 는 PowerShell에서 여러 세션을 실행 하는 경우에도 고유 합니다.

**Instanceid** 는 CIM 세션을 나타내는 개체의 **instanceid** 속성에 저장 됩니다.

```yaml
Type: System.Guid[]
Parameter Sets: InstanceIdSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

제거할 CIM 세션의 이름을 지정 합니다. 이 매개 변수와 함께 와일드 카드 문자를 사용할 수 있습니다.

```yaml
Type: System.String[]
Parameter Sets: NameSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
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

### 없음

이 cmdlet은 입력 개체를 허용 하지 않습니다.

## 출력

### System.Object

이 cmdlet은 CIM 세션 정보를 포함 하는 개체를 반환 합니다.

## 참고

## 관련 링크

[Get-CimSession](Get-CimSession.md)

[New-CimSession](New-CimSession.md)

[about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md)
