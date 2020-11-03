---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-pshostprocessinfo?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSHostProcessInfo
ms.openlocfilehash: 655cc02e10bdb11092412271c16a002ab89089c3
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93217690"
---
# Get-PSHostProcessInfo

## 개요
PowerShell 호스트에 대 한 프로세스 정보를 가져옵니다.

## SYNTAX

### ProcessNameParameterSet (기본값)

```
Get-PSHostProcessInfo [[-Name] <String[]>] [<CommonParameters>]
```

### ProcessParameterSet

```
Get-PSHostProcessInfo [-Process] <Process[]> [<CommonParameters>]
```

### ProcessIdParameterSet

```
Get-PSHostProcessInfo [-Id] <Int32[]> [<CommonParameters>]
```

## 설명

`Get-PSHostProcessInfo`Cmdlet은 로컬 컴퓨터에서 실행 되는 PowerShell 호스트 프로세스에 대 한 정보를 가져옵니다.

PowerShell 6.2부터이 cmdlet은 Windows 이외의 플랫폼에서 지원 됩니다.

## 예제

### 1: 시스템에서 실행 되는 PowerShell 호스트의 목록 가져오기

```powershell
Get-PSHostProcessInfo
```

```Output
ProcessName ProcessId AppDomainName
----------- --------- -------------
powershell      11204 DefaultAppDomain
pwsh            13912 DefaultAppDomain
```

### 2: 특정 프로세스 이름에 대 한 PowerShell 호스트 정보 가져오기

```powershell
Get-PSHostProcessInfo -Name pwsh
```

```Output
ProcessName ProcessId AppDomainName
----------- --------- -------------
pwsh            13912 DefaultAppDomain
```

## PARAMETERS

### -Id

프로세스 ID로 프로세스를 지정 합니다. 프로세스 ID를 가져오려면 cmdlet을 실행 `Get-Process` 합니다.

```yaml
Type: System.Int32[]
Parameter Sets: ProcessIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

프로세스 이름으로 프로세스를 지정 합니다. 프로세스 이름을 가져오려면 cmdlet을 실행 `Get-Process` 합니다.

```yaml
Type: System.String[]
Parameter Sets: ProcessNameParameterSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Process

프로세스 개체의 프로세스를 지정 합니다. 이 매개 변수를 사용 하는 가장 간단한 방법은 `Get-Process` 변수에 입력 하려는 프로세스를 반환 하는 명령의 결과를 저장 한 다음이 매개 변수의 값으로 변수를 지정 하는 것입니다.

```yaml
Type: System.Diagnostics.Process[]
Parameter Sets: ProcessParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.Diagnostics.Process

**프로세스** 개체를에서이 cmdlet으로 파이프 할 수 있습니다 `Get-Process` .

## 출력

### Exit-pshostprocessinfo.

## 참고

## 관련 링크

[Get-Process](../Microsoft.PowerShell.Management/get-process.md)

