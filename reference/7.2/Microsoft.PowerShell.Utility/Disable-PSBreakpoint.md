---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/disable-psbreakpoint?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSBreakpoint
ms.openlocfilehash: 2bd1a48d2075950cdb337063a100bf31534ac6fe
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99600443"
---
# Disable-PSBreakpoint

## 개요
현재 콘솔의 중단점을 해제합니다.

## SYNTAX

### 중단점 (기본값)

```
Disable-PSBreakpoint [-PassThru] [-Breakpoint] <Breakpoint[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Id

```
Disable-PSBreakpoint [-PassThru] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명

**Disable-psbreakpoint** cmdlet은 스크립트가 실행 될 때 적중 되지 않도록 하는 중단점을 사용 하지 않도록 설정 합니다.
이 cmdlet을 사용하여 모든 중단점을 해제하거나 중단점 개체 또는 중단점 ID를 제출하여 중단점을 지정할 수 있습니다.

기술적으로 이 cmdlet은 중단점 개체의 Enabled 속성 값을 False로 변경합니다.
중단점을 다시 설정하려면 Enable-PSBreakpoint cmdlet을 사용합니다.
Set-PSBreakpoint cmdlet을 사용하여 중단점을 만드는 경우 중단점이 기본적으로 설정됩니다.

중단점은 스크립트의 명령을 검사할 수 있도록 실행이 일시적으로 중지되는 스크립트의 한 지점입니다.
**Disable-PSBreakpoint** PowerShell 스크립트를 디버깅 하기 위해 디자인 된 여러 cmdlet 중 하나입니다.
PowerShell 디버거에 대 한 자세한 내용은 about_Debuggers를 참조 하세요.

## 예제

### 예제 1: 중단점 설정 및 사용 안 함

```
PS C:\> $B = Set-PSBreakpoint -Script "sample.ps1" -Variable "name"
PS C:\> $B | Disable-PSBreakpoint
```

이 명령은 새로 만든 중단점을 해제합니다.

첫 번째 명령은 Set-PSBreakpoint cmdlet을 사용 하 여 Sample.ps1 스크립트의 *이름* 변수에 중단점을 만듭니다.
그런 다음 $B 변수에 중단점 개체를 저장 합니다.

두 번째 명령은 **disable-psbreakpoint** cmdlet을 사용 하 여 새 중단점을 해제 합니다.
파이프라인 연산자 (|)를 사용 하 여 $B에 있는 중단점 개체를 **Disable-PSBreakpoint** cmdlet으로 보냅니다.

이 명령의 결과로 $B에 있는 중단점 개체의 Enabled 속성 값은 False입니다.

### 예제 2: 중단점 사용 안 함

```
PS C:\> Disable-PSBreakpoint -Id 0
```

이 명령은 중단점 ID가 0인 중단점을 해제합니다.

### 예제 3: 비활성화 된 중단점 만들기

```
PS C:\> Disable-PSBreakpoint -Breakpoint ($B = Set-PSBreakpoint -Script "sample.ps1" -Line 5)
PS C:\> $B
```

이 명령은 설정할 때까지 해제된 상태로 있는 새 중단점을 만듭니다.

**Disable-psbreakpoint** cmdlet을 사용 하 여 중단점을 해제 합니다.
*중단점* 매개 변수 값은 새 중단점을 설정 하 고, 중단점 개체를 생성 하 고, 개체를 $B 변수에 저장 하는 Set-PSBreakpoint 명령입니다.

값으로 개체를 사용하는 cmdlet 매개 변수는 개체 또는 개체를 가져오거나 생성하는 명령이 포함된 변수를 받을 수 있습니다.
이 경우 **Set-PSBreakpoint** 중단점 개체를 생성 하므로 *중단점* 매개 변수의 값으로 사용할 수 있습니다.

두 번째 명령은 $B 변수 값에 있는 중단점 개체를 표시 합니다.

### 예제 4: 현재 콘솔의 모든 중단점 사용 안 함

```
PS C:\> Get-PSBreakpoint | Disable-PSBreakpoint
```

이 명령은 현재 콘솔의 모든 중단점을 해제합니다.
이 명령의 약어는 다음과 같이 지정할 수 있습니다. "gbp | .dbp ".

## PARAMETERS

### -중단점

해제할 중단점을 지정합니다.
중단점 개체가 포함된 변수를 입력하거나 중단점 개체를 가져오는 명령(예: Get-PSBreakpoint 명령)을 입력합니다.
중단점 개체를 **Disable-psbreakpoint** cmdlet으로 파이프 할 수도 있습니다.

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

지정한 중단점 ID를 가진 중단점을 해제합니다.
ID 또는 ID가 포함된 변수를 입력합니다.
**-PSBreakpoint을 사용 하지 않도록 설정** 하려면 id를 파이프 할 수 없습니다.

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

설정된 중단점을 나타내는 개체를 반환합니다.
기본적으로 이 cmdlet은 출력을 생성하지 않습니다.

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

### System.object. 중단점

중단점 개체를 **사용 하지 않도록 설정 하 여-PSBreakpoint을 사용 하지 않도록 설정할** 수 있습니다.

## 출력

### 없음 또는 System.object

*PassThru* 매개 변수를 사용 하는 경우 **-psbreakpoint** 사용 하지 않도록 설정 된 중단점을 나타내는 개체를 반환 합니다.
그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.

## 참고

## 관련 링크

[Enable-PSBreakpoint](Enable-PSBreakpoint.md)

[Get-PSBreakpoint](Get-PSBreakpoint.md)

[Get-PSCallStack](Get-PSCallStack.md)

[Remove-PSBreakpoint](Remove-PSBreakpoint.md)

[Set-PSBreakpoint](Set-PSBreakpoint.md)

