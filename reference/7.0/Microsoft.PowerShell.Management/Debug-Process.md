---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/debug-process?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Debug-Process
ms.openlocfilehash: 7a439cc3f15b319f5f56709260035ffa8fc03c12
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94391377"
---
# Debug-Process

## 개요
로컬 컴퓨터에서 실행 중인 하나 이상의 프로세스를 디버그합니다.

## SYNTAX

### 이름 (기본값)

```
Debug-Process [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Id

```
Debug-Process [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InputObject

```
Debug-Process -InputObject <Process[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명

`Debug-Process`Cmdlet은 로컬 컴퓨터에서 실행 중인 하나 이상의 프로세스에 디버거를 연결 합니다.
프로세스 이름 또는 프로세스 ID (PID)로 프로세스를 지정 하거나 프로세스 개체를이 cmdlet으로 파이프 할 수 있습니다.

이 cmdlet은 프로세스에 대해 현재 등록 된 디버거를 연결 합니다. 이 cmdlet을 사용하기 전에 디버거가 다운로드되었으며 올바르게 구성되었는지 확인합니다.

## 예제

### 예제 1: 컴퓨터의 프로세스에 디버거 연결

```
PS C:\> Debug-Process -Name "Windows Powershell"
```

이 명령은 컴퓨터의 PowerShell 프로세스에 디버거를 연결합니다.

### 예제 2: 지정 된 문자열로 시작 하는 모든 프로세스에 디버거 연결

```
PS C:\> Debug-Process -Name "SQL*"
```

이 명령은 이름이 SQL로 시작 하는 모든 프로세스에 디버거를 연결 합니다.

### 예제 3: 여러 프로세스에 디버거 연결

```
PS C:\> Debug-Process "Winlogon", "Explorer", "Outlook"
```

이 명령은 Winlogon, Explorer 및 Outlook 프로세스에 디버거를 연결합니다.

### 예제 4: 여러 프로세스 Id에 디버거 연결

```
PS C:\> Debug-Process -Id 1132, 2028
```

이 명령은 프로세스 ID가 1132 및 2028인 프로세스에 디버거를 연결합니다.

### 예 5: Get-Process을 사용 하 여 프로세스를 가져온 다음 디버거를 연결 합니다.

```
PS C:\> Get-Process "Windows PowerShell" | Debug-Process
```

이 명령은 컴퓨터의 PowerShell 프로세스에 디버거를 연결합니다. Cmdlet을 사용 하 여 `Get-Process` 컴퓨터의 PowerShell 프로세스를 가져온 다음 파이프라인 연산자 ()를 사용 하 여 `|` 프로세스를 cmdlet으로 보냅니다 `Debug-Process` .

특정 PowerShell 프로세스를 지정 하려면의 ID 매개 변수를 사용 `Get-Process` 합니다.

### 예제 6: 로컬 컴퓨터의 현재 프로세스에 디버거 연결

```
PS C:\> $PID | Debug-Process
```

이 명령은 컴퓨터의 현재 PowerShell 프로세스에 디버거를 연결합니다.

`$PID`이 명령은 현재 PowerShell 프로세스의 프로세스 ID가 포함 된 자동 변수를 사용 합니다. 그런 다음 파이프라인 연산자 ()를 사용 하 여 `|` 프로세스 ID를 cmdlet으로 보냅니다 `Debug-Process` .

자동 변수에 대 한 자세한 내용은 `$PID` about_Automatic_Variables를 참조 하세요.

### 예 7: InputObject 매개 변수를 사용 하는 프로세스에 디버거 연결

```
PS C:\> $P = Get-Process "Windows PowerShell"
PS C:\> Debug-Process -InputObject $P
```

이 명령은 로컬 컴퓨터의 PowerShell 프로세스에 디버거를 연결합니다.

첫 번째 명령은 cmdlet을 사용 하 여 `Get-Process` 컴퓨터의 PowerShell 프로세스를 가져옵니다. 결과 프로세스 개체를 이라는 변수에 저장 `$P` 합니다.

두 번째 명령은 cmdlet의 **InputObject** 매개 변수를 사용 하 여 `Debug-Process` 변수의 프로세스 개체를 제출 `$P` 합니다.

## PARAMETERS

### -Id

디버그할 프로세스의 프로세스 ID를 지정합니다. **Id** 매개 변수 이름은 선택 사항입니다.

프로세스의 프로세스 ID를 찾으려면를 입력 `Get-Process` 합니다.

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases: PID, ProcessId

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -InputObject

디버그할 프로세스를 나타내는 프로세스 개체를 지정합니다. 프로세스 개체가 포함 된 변수를 입력 하거나 프로세스 개체를 가져오는 명령 (예: cmdlet)을 입력 합니다 `Get-Process` . 프로세스 개체를이 cmdlet으로 파이프 할 수도 있습니다.

```yaml
Type: System.Diagnostics.Process[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name

디버그할 프로세스의 이름을 지정합니다. 이름이 같은 프로세스가 둘 이상 있는 경우이 cmdlet은 해당 이름을 가진 모든 프로세스에 디버거를 연결 합니다. **Name** 매개 변수는 선택 사항입니다.

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases: ProcessName

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

### System.string, system.web. Process, System.string

프로세스 ID (Int32), 프로세스 개체 (System.web) 또는 프로세스 이름 (문자열)을이 cmdlet으로 파이프 할 수 있습니다.

## 출력

### 없음

이 cmdlet은 어떠한 출력도 생성하지 않습니다.

## 참고

이 cmdlet은 WMI(Windows Management Instrumentation) Win32_Process 클래스의 AttachDebugger 메서드를 사용합니다. 이 메서드에 대 한 자세한 내용은 MSDN library에서 [AttachDebugger 메서드](https://go.microsoft.com/fwlink/?LinkId=143640) 를 참조 하세요.

## 관련 링크

[Debug-Process](Debug-Process.md)

[Get-Process](Get-Process.md)

[Start-Process](Start-Process.md)

[Stop-Process](Stop-Process.md)

[Wait-Process](Wait-Process.md)
