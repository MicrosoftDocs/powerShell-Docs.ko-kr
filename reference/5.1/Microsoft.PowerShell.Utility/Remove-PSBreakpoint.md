---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/remove-psbreakpoint?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-PSBreakpoint
ms.openlocfilehash: b12913cd10c2c505322c1f922a05ecc98987e830
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93213754"
---
# Remove-PSBreakpoint

## 개요
현재 콘솔에서 중단점을 삭제합니다.

## SYNTAX

### 중단점 (기본값)

```
Remove-PSBreakpoint [-Breakpoint] <Breakpoint[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Id

```
Remove-PSBreakpoint [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명
**Remove psbreakpoint** cmdlet은 중단점을 삭제 합니다.
중단점 개체 또는 중단점 ID를 입력합니다.

중단점을 제거하면 중단점 개체는 더 이상 사용할 수 없게 되며 작동하지 않습니다.
변수에 중단점 개체를 저장한 경우 참조는 계속 존재하지만 중단점은 작동하지 않습니다.

**Remove-PSBreakpoint** Windows PowerShell 스크립트를 디버깅 하기 위해 디자인 된 여러 cmdlet 중 하나입니다.
Windows PowerShell 디버거에 대한 자세한 내용은 about_Debuggers를 참조하세요.

## 예제

### 예제 1: 모든 중단점 제거

```
PS C:\> Get-PSBreakpoint | Remove-PSBreakpoint
```

이 명령은 현재 콘솔의 모든 중단점을 삭제합니다.

### 예제 2: 지정 된 중단점 제거

```
PS C:\> $B = Set-PSBreakpoint -Script "sample.ps1" -Variable "Name"
PS C:\> $B | Remove-PSBreakpoint
```

이 명령은 중단점을 삭제합니다.

첫 번째 명령은 Set-PSBreakpoint cmdlet을 사용하여 Sample.ps1 스크립트의 Name 변수에 중단점을 만듭니다.
그런 다음 $B 변수에 중단점 개체를 저장 합니다.

두 번째 명령은 **Remove psbreakpoint** cmdlet을 사용 하 여 새 중단점을 삭제 합니다.
파이프라인 연산자 (|)를 사용 하 여 $B 변수의 중단점 개체를 **Remove PSBreakpoint** cmdlet으로 보냅니다.

이 명령을 실행한 후에 실행하는 스크립트는 중지되지 않고 끝까지 실행됩니다.
또한, **Get psbreakpoint** cmdlet은이 중단점을 반환 하지 않습니다.

### 예제 3: ID로 중단점 제거

```
PS C:\> Remove-PSBreakpoint -Id 2
```

이 명령은 중단점 ID가 2인 중단점을 삭제합니다.

### 예제 4: 함수를 사용 하 여 모든 중단점 제거

```
PS C:\> function del-psb { get-psbreakpoint | remove-psbreakpoint }
```

이 간단한 함수는 현재 콘솔의 모든 중단점을 삭제합니다.
함수는 Get-PSBreakpoint cmdlet을 사용하여 중단점을 가져오며
그런 다음 파이프라인 연산자 (|)를 사용 하 여 중단점을 **Remove psbreakpoint** cmdlet으로 보냅니다. 그러면이 cmdlet이 중단점을 삭제 합니다.

따라서 `del-psb` 더 긴 명령 대신을 입력할 수 있습니다.

함수를 저장하려면 Windows PowerShell 프로필에 추가하세요.

## PARAMETERS

### -중단점
삭제할 중단점을 지정합니다.
중단점 개체를 포함 하는 변수를 입력 하거나 중단점 개체 (예: **Get PSBreakpoint command)** 를 가져오는 명령을 입력 합니다.
중단점 개체를 **-Psbreakpoint 제거** 하도록 파이프 할 수도 있습니다.

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
이 cmdlet이 중단점을 삭제 하는 중단점 Id를 지정 합니다.

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
중단점 개체를 **-Psbreakpoint 제거** 하도록 파이프 할 수 있습니다.

## 출력

### 없음
이 cmdlet에서 어떠한 출력도 생성되지 않습니다.

## 참고

## 관련 링크

[Disable-PSBreakpoint](Disable-PSBreakpoint.md)

[Enable-PSBreakpoint](Enable-PSBreakpoint.md)

[Get-PSBreakpoint](Get-PSBreakpoint.md)

[Get-PSCallStack](Get-PSCallStack.md)

[Set-PSBreakpoint](Set-PSBreakpoint.md)
