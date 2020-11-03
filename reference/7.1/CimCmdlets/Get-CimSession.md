---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/get-cimsession?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-CimSession
ms.openlocfilehash: 45a1aacd855ba1a2479fc3bf4d2ce991a87ddb09
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93217826"
---
# Get-CimSession

## 개요
현재 세션에서 CIM 세션 개체를 가져옵니다.

## SYNTAX

### ComputerNameSet (기본값)

```
Get-CimSession [[-ComputerName] <String[]>] [<CommonParameters>]
```

### SessionIdSet

```
Get-CimSession [-Id] <UInt32[]> [<CommonParameters>]
```

### InstanceIdSet

```
Get-CimSession -InstanceId <Guid[]> [<CommonParameters>]
```

### NameSet

```
Get-CimSession -Name <String[]> [<CommonParameters>]
```

## 설명

기본적으로이 cmdlet은 현재 PowerShell 세션에서 만든 모든 CIM 세션을 가져옵니다. 의 매개 변수를 사용 `Get-CimSession` 하 여 특정 컴퓨터에 대 한 세션을 가져오거나 이름 또는 다른 식별자로 세션을 식별할 수 있습니다. `Get-CimSession` 다른 PowerShell 세션에서 만들었거나 다른 컴퓨터에서 만들어진 CIM 세션은 가져오지 않습니다.

CIM 세션에 대 한 자세한 내용은 [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md)를 참조 하세요.

## 예제

### 예제 1: 현재 PowerShell 세션에서 CIM 세션 가져오기

이 예제에서는 [CimSession](New-CimSession.md)를 사용 하 여 cim 세션을 만든 다음를 사용 하 여 cim 세션을 가져옵니다 `Get-CimSession` .

```powershell
New-CimSession -ComputerName Server01,Server02
Get-CimSession
```

```Output
Id           : 1
Name         : CimSession1
InstanceId   : d1413bc3-162a-4cb8-9aec-4d2c61253d59
ComputerName : Server01
Protocol     : WSMAN

Id           : 2
Name         : CimSession2
InstanceId   : c0095981-52c5-4e7f-a5bb-c4c680541710
ComputerName : Server02
Protocol     : WSMAN
```

### 예 2: 특정 컴퓨터에 대 한 CIM 세션 가져오기

이 예제에서는 **Server02** 이라는 컴퓨터에 연결 된 CIM 세션을 가져옵니다.

```powershell
Get-CimSession -ComputerName Server02
```

```Output
Id           : 2
Name         : CimSession2
InstanceId   : c0095981-52c5-4e7f-a5bb-c4c680541710
ComputerName : Server02
Protocol     : WSMAN
```

### 예 3: CIM 세션 목록을 가져온 다음 목록의 서식을 지정 합니다.

이 예에서는 현재 PowerShell 세션의 모든 CIM 세션을 가져오고 **ComputerName** 및 **InstanceID** 속성만 포함 하는 테이블을 표시 합니다.

```powershell
Get-CimSession | Format-Table -Property ComputerName,InstanceId
```

```Output
ComputerName InstanceId
------------ ----------
Server01     d1413bc3-162a-4cb8-9aec-4d2c61253d59
Server02     c0095981-52c5-4e7f-a5bb-c4c680541710
```

### 예제 4: 특정 이름을 가진 모든 CIM 세션 가져오기

이 예제에서는 이름이 **serv** 로 시작 하는 모든 CIM 세션을 가져옵니다.

```powershell
Get-CimSession -ComputerName Serv*
```

```Output
Id           : 1
Name         : CimSession1
InstanceId   : d1413bc-162a-4cb8-9aec-4d2c61253d59
ComputerName : Server01
Protocol     : WSMAN

Id           : 2
Name         : CimSession2
InstanceId   : c0095981-52c5-4e7f-a5bb-c4c680541710
ComputerName : Server02
Protocol     : WSMAN
```

### 예 5: 특정 CIM 세션 가져오기

이 예제에서는 **Id** 가 2 인 CIM 세션을 가져옵니다.

```powershell
Get-CimSession -ID 2
```

```Output
Id           : 2
Name         : CimSession2
InstanceId   : c0095981-52c5-4e7f-a5bb-c4c680541710
ComputerName : Server02
Protocol     : WSMAN
```

## PARAMETERS

### -ComputerName

연결 된 CIM 세션을 가져올 컴퓨터의 이름을 지정 합니다. 와일드카드 문자를 사용할 수 있습니다.

```yaml
Type: System.String[]
Parameter Sets: ComputerNameSet
Aliases: CN, ServerName

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Id

가져올 CIM 세션의 식별자를 지정 합니다. 여러 Id의 경우 쉼표를 사용 하 여 Id를 구분 하거나 범위 연산자 ()를 사용 하 여 `..` id 범위를 지정 합니다. **Id** 는 현재 PowerShell 세션 내에서 CIM 세션을 고유 하 게 식별 하는 정수입니다.

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

가져올 CIM 세션의 인스턴스 Id를 지정 합니다.

**InstanceId** 는 CIM 세션을 고유 하 게 식별 하는 guid (globally unique identifier)입니다. **InstanceId** 는 PowerShell에서 여러 세션을 실행 하는 경우에도 고유 합니다.

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

지정 된 이름을 포함 하는 CIM 세션을 하나 이상 가져옵니다. 와일드카드 문자를 사용할 수 있습니다.

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

### CommonParameters
이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### 없음

## 출력

### Microsoft.Management.Infrastructure.CimSession

## 참고

## 관련 링크

[Format-Table](../microsoft.powershell.utility/format-table.md)

[New-CimSession](New-CimSession.md)

[Remove-CimSession](remove-cimsession.md)

[about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md)

