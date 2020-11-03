---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/09/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/enable-psbreakpoint?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSBreakpoint
ms.openlocfilehash: 547739d6482e86bc558245bc5c5f04eddcfe9614
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93215849"
---
# Enable-PSBreakpoint

## 개요
현재 콘솔의 중단점을 설정합니다.

## SYNTAX

### Id (기본값)

```
Enable-PSBreakpoint [-PassThru] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### 중단점

```
Enable-PSBreakpoint [-PassThru] [-Breakpoint] <Breakpoint[]> [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## 설명

`Enable-PSBreakpoint`Cmdlet은 해제 된 중단점을 다시 사용 하도록 설정 합니다. 중단점 개체 또는 Id를 제공 하 여 모든 중단점 또는 특정 중단점을 사용 하도록 설정 하는 데 사용할 수 있습니다.

중단점은 스크립트의 상태를 검사할 수 있도록 실행이 일시적으로 중지 되는 스크립트의 지점입니다. 새로 만든 중단점은 자동으로 사용 하도록 설정 되지만를 사용 하 여 사용 하지 않도록 설정할 수 있습니다 `Disable-PSBreakpoint` .

기술적으로이 cmdlet은 중단점 개체의 **Enabled** 속성 값을 **True** 로 변경 합니다.

`Enable-PSBreakpoint` 는 PowerShell 스크립트 디버깅을 위해 설계 된 여러 cmdlet 중 하나입니다. PowerShell 디버거에 대 한 자세한 내용은 [about_Debuggers](../Microsoft.PowerShell.Core/About/about_Debuggers.md)를 참조 하세요.

## 예제

### 예제 1: 모든 중단점 사용

이 예에서는 현재 세션의 모든 중단점을 설정 합니다.

```powershell
Get-PSBreakpoint | Enable-PSBreakpoint
```

별칭을 사용 하 여이 예제를 약식으로 사용할 수 있습니다 `gbp | ebp` .

### 예제 2: ID로 중단점 사용

이 예제에서는 중단점 Id를 사용 하 여 여러 중단점을 설정 합니다.

```powershell
Enable-PSBreakpoint -Id 0, 1, 5
```

### 예제 3: 비활성화 된 중단점 설정

이 예제에서는 사용 하지 않도록 설정 된 중단점을 다시 설정 합니다.

```powershell
$B = Set-PSBreakpoint -Script "sample.ps1" -Variable Name -PassThru
$B | Enable-PSBreakpoint -PassThru
```

```Output
AccessMode : Write
Variable   : Name
Action     :
Enabled    : False
HitCount   : 0
Id         : 0
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1

AccessMode : Write
Variable   : Name
Action     :
Enabled    : True
HitCount   : 0
Id         : 0
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1
```

`Set-PSBreakpoint`**Name** `Sample.ps1` 변수에 중단점 개체를 저장 하는 스크립트의 이름 변수에 중단점을 만듭니다 `$B` . **PassThru** 매개 변수는 중단점의 **Enabled** 속성 값이 **False** 인 것을 표시 합니다.

`Enable-PSBreakpoint` 중단점을 다시 설정 합니다. 다시 **PassThru** 매개 변수를 사용 하 여 Enabled 속성의 값이 **True** 인 것을 확인할 **수** 있습니다.

### 예제 4: 변수를 사용 하 여 중단점 설정

이 예제에서는 중단점 개체를 사용 하 여 중단점 집합을 활성화 합니다.

```powershell
$B = Get-PSBreakpoint -Id 3, 5
Enable-PSBreakpoint -Breakpoint $B
```

`Get-PSBreakpoint` 중단점을 가져와서 `$B` 변수에 저장 합니다. **중단점** 매개 변수를 사용 하 여 중단점을 사용 `Enable-PSBreakpoint` 하도록 설정 합니다.

이 예제는를 실행 하는 것과 같습니다 `Enable-PSBreakpoint -Id 3, 5` .

## PARAMETERS

### -중단점

설정할 중단점을 지정합니다. 중단점을 포함 하는 변수 또는와 같은 중단점 개체를 가져오는 명령을 제공 `Get-PSBreakpoint` 합니다. 중단점 개체를로 파이프 할 수도 있습니다 `Enable-PSBreakpoint` .

```yaml
Type: System.Management.Automation.Breakpoint[]
Parameter Sets: Breakpoint
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Id

사용할 중단점의 **Id** 번호를 지정 합니다. 기본값은 모든 중단점입니다.
**Id** 를 숫자나 변수로 제공 합니다. **Id** 번호는로 파이프 할 수 없습니다 `Enable-PSBreakpoint` . 중단점의 **Id** 를 확인 하려면 cmdlet을 사용 합니다 `Get-PSBreakpoint` .

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PassThru

사용할 중단점을 나타내는 개체를 반환 합니다. 기본적으로이 cmdlet은 출력을 생성 하지 않습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
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

cmdlet을 실행할 경우 발생하는 일을 표시합니다. Cmdlet이 실행 되지 않습니다.

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

### System.object. 중단점

중단점 개체를로 파이프 할 수 있습니다 `Enable-PSBreakpoint` .

## 출력

### 없음 또는 System.object

**PassThru** 매개 변수를 사용 하는 경우은 `Enable-PSBreakpoint` 사용 하도록 설정 된 중단점을 나타내는 중단점 개체를 반환 합니다. 그렇지 않으면이 cmdlet은 출력을 생성 하지 않습니다.

## 참고

- `Enable-PSBreakpoint`이미 사용 하도록 설정 된 중단점을 설정 하려고 하면 cmdlet에서 오류를 생성 하지 않습니다. 따라서 중단점 중 몇 개만 해제되어 있는 경우에도 오류 없이 모든 중단점을 설정할 수 있습니다.

- 중단점은 cmdlet을 사용 하 여 만들 때 사용할 수 있습니다 `Set-PSBreakpoint` . 새로 만든 중단점을 설정 하지 않아도 됩니다.

## 관련 링크

[Disable-PSBreakpoint](Disable-PSBreakpoint.md)

[Get-PSBreakpoint](Get-PSBreakpoint.md)

[Get-PSCallStack](Get-PSCallStack.md)

[Remove-PSBreakpoint](Remove-PSBreakpoint.md)

[Set-PSBreakpoint](Set-PSBreakpoint.md)

