---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/09/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-runspace?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Runspace
ms.openlocfilehash: cb179dc442334dace45a1b83e36158fc53584ff9
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93213033"
---
# Get-Runspace

## 개요
PowerShell 호스트 프로세스 내의 활성 runspace를 가져옵니다.

## SYNTAX

### NameParameterSet (기본값)

```
Get-Runspace [[-Name] <String[]>] [<CommonParameters>]
```

### IdParameterSet

```
Get-Runspace [-Id] <Int32[]> [<CommonParameters>]
```

### InstanceIdParameterSet

```
Get-Runspace [-InstanceId] <Guid[]> [<CommonParameters>]
```

## 설명

`Get-Runspace`Cmdlet은 PowerShell 호스트 프로세스에서 활성 runspace를 가져옵니다.

## 예제

### 예제 1: runspace 가져오기

```powershell
Get-Runspace
```

```Output
Id Name            ComputerName    Type          State         Availability
 -- ----            ------------    ----          -----         ------------
  1 Runspace1       localhost       Local         Opened        Busy
  2 Runspace2       localhost       Local         Opened        Available
  3 Runspace3       localhost       Local         Opened        Available
```

### 예제 2: Id로 runspace 가져오기

```powershell
Get-Runspace -Id 2
```

```Output
Id Name            ComputerName    Type          State         Availability
 -- ----            ------------    ----          -----         ------------
  2 Runspace2       localhost       Local         Opened        Available
```

### 예제 3: 이름으로 runspace 가져오기

```powershell
Get-Runspace -Name Runspace1
```

```Output
Id Name            ComputerName    Type          State         Availability
 -- ----            ------------    ----          -----         ------------
  1 Runspace1       localhost       Local         Opened        Busy
```

### 예제 4: InstanceId로 runspace 가져오기

이 예제에서는 매개 변수를 사용 하 여 사용 가능한 runspace를 식별 하 `Name` 고 반환 개체를 변수에 저장 `$activeRunspace` 합니다. 이렇게 하면 이후 실행에서 **Runspace** 의 속성을 사용할 수 있습니다 `Get-Runspace` .

```powershell
$activeRunspace = Get-Runspace -Name Runspace1
Get-Runspace -InstanceId $activeRunspace.InstanceId
```

```Output
Id Name            ComputerName    Type          State         Availability
 -- ----            ------------    ----          -----         ------------
  1 Runspace1       localhost       Local         Opened        Busy
```

## PARAMETERS

### -Id

Runspace의 Id를 지정 합니다.

```yaml
Type: System.Int32[]
Parameter Sets: IdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InstanceId

실행 중인 작업의 인스턴스 ID GUID를 지정 합니다.

```yaml
Type: System.Guid[]
Parameter Sets: InstanceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Runspace의 이름을 지정 합니다.

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

## 출력

### Runspace입니다.

명령의 결과를로 파이프 할 수 있습니다 `Get-Runspace` `Debug-Runspace` .

## 참고

## 관련 링크

[Debug-Runspace](Debug-Runspace.md)

