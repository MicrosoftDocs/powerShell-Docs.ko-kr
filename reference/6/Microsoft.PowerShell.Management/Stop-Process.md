---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/stop-process?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Process
ms.openlocfilehash: a2f340f0119823ddc0876d86fc38e49edc51fe5d
ms.sourcegitcommit: 11abf355ac545531c2b04217a08ebe6be609c0bb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2020
ms.locfileid: "93220001"
---
# Stop-Process

## 개요
실행 중인 하나 이상의 프로세스를 중지합니다.

## SYNTAX

### Id (기본값)

```
Stop-Process [-Id] <Int32[]> [-PassThru] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### 속성

```
Stop-Process -Name <String[]> [-PassThru] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InputObject

```
Stop-Process [-InputObject] <Process[]> [-PassThru] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명

**Stop Process** cmdlet은 실행 중인 하나 이상의 프로세스를 중지 합니다.
프로세스 이름 또는 프로세스 ID (PID)로 프로세스를 지정 하거나 프로세스 개체를 전달 하 여 프로세스를 **중단할** 수 있습니다.
**중지-프로세스** 는 로컬 컴퓨터에서 실행 중인 프로세스 에서만 작동 합니다.

Windows Vista 이상 버전의 Windows 운영 체제에서 현재 사용자가 소유 하지 않은 프로세스를 중지 하려면 관리자 권한으로 실행 옵션을 사용 하 여 PowerShell을 시작 해야 합니다.
또한 *Confirm* 매개 변수를 지정 하지 않으면 확인 메시지가 표시 되지 않습니다.

## 예제

### 예제 1: 프로세스의 모든 인스턴스 중지

```
PS C:\> Stop-Process -Name "notepad"
```

이 명령은 컴퓨터의 Notepad 프로세스의 모든 인스턴스를 중지합니다.
각 메모장 인스턴스는 자체 프로세스에서 실행 됩니다.
*Name* 매개 변수를 사용 하 여 프로세스를 지정 합니다 .이는 모두 동일한 이름을 갖습니다.
*Id* 매개 변수를 사용 하 여 동일한 프로세스를 중지 하는 경우 각 Notepad 인스턴스의 프로세스 id를 나열 해야 합니다.

### 예 2: 특정 프로세스 인스턴스 중지

```
PS C:\> Stop-Process -Id 3952 -Confirm -PassThru
Confirm
Are you sure you want to perform this action?
Performing operation "Stop-Process" on Target "notepad (3952)".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):y
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
41       2      996       3212    31            3952 notepad
```

이 명령은 Notepad 프로세스의 특정 인스턴스를 중지합니다.
먼저 프로세스 ID, 3952를 사용하여 프로세스를 식별합니다.
*Confirm* 매개 변수는 프로세스를 중지 하기 전에 사용자에 게 메시지를 표시 하도록 지시 합니다.
프롬프트에는 ID 외에 프로세스 이름이 포함 되어 있으므로이 방법이 가장 좋습니다.
*PassThru* 매개 변수는 표시를 위해 프로세스 개체를 포맷터로 전달 합니다.
이 매개 변수를 사용 하지 않으면 **중지-처리** 명령 후에는 표시 되지 않습니다.

### 예 3: 프로세스를 중지 하 고 중지 되었음을 감지

```
PS C:\> calc
PS C:\> $p = Get-Process -Name "calc"
PS C:\> Stop-Process -InputObject $p
PS C:\> Get-Process | Where-Object {$_.HasExited}
```

이 일련의 명령은 계산 프로세스를 시작 및 중지 한 다음 중지 된 프로세스를 검색 합니다.

첫 번째 명령은 계산기의 인스턴스를 시작 합니다.

두 번째 명령은 **Get process** 를 사용 하 여 Calc 프로세스를 나타내는 개체를 가져온 다음 $p 변수에 저장 합니다.

세 번째 명령은 Calc 프로세스를 중지 합니다.
*InputObject* 매개 변수를 사용 하 여 개체를 **중지 프로세스** 에 전달 합니다.

마지막 명령은 이전에 실행되었지만 지금은 중지된 컴퓨터의 모든 프로세스를 가져옵니다.
**Get Process** 를 사용 하 여 컴퓨터의 모든 프로세스를 가져옵니다.
파이프라인 연산자 (|)는 결과를 Where-Object cmdlet으로 전달 합니다 .이 cmdlet은 **HasExited** 속성 값이 $True 되는 항목을 선택 합니다.
**HasExited** 는 프로세스 개체의 속성 중 하나에 불과합니다.
모든 속성을 찾으려면를 입력 `Get-Process | Get-Member` 합니다.

### 예제 4: 현재 사용자가 소유 하지 않은 프로세스 중지

```
PS C:\> Get-Process -Name "lsass" | Stop-Process

Stop-Process : Cannot stop process 'lsass (596)' because of the following error: Access is denied
At line:1 char:34
+ Get-Process -Name "lsass" | Stop-Process <<<<

[ADMIN]: PS C:\> Get-Process -Name "lsass" | Stop-Process

Warning!
Are you sure you want to perform this action?
Performing operation 'Stop-Process' on Target 'lsass(596)'
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
[ADMIN]: PS C:\> Get-Process -Name "lsass" | Stop-Process -Force
[ADMIN]: PS C:\>
```

이러한 명령은 *Force* 를 사용 하 여 사용자가 소유 하지 않은 프로세스를 중지 하는 경우의 결과를 보여 줍니다.

첫 번째 명령은 **Get process** 를 사용 하 여 Lsass 프로세스를 가져옵니다.
파이프라인 연산자는 프로세스를 **중지** 하는 프로세스를 전송 하 여 중지 합니다.
샘플 출력에 표시 된 것 처럼 첫 번째 명령은 액세스 거부 메시지와 함께 실패 합니다 .이 프로세스는 컴퓨터의 Administrator 그룹 구성원만 중지할 수 있기 때문입니다.

관리자 권한으로 실행 옵션을 사용 하 여 PowerShell을 열고 명령이 반복 되 면 PowerShell에서 확인 메시지를 표시 합니다.

두 번째 명령은 *Force* 를 지정 하 여 프롬프트를 표시 하지 않습니다.
그 결과 확인 메시지 없이 프로세스가 중지됩니다.

## PARAMETERS

### -Force

확인 메시지 없이 지정된 프로세스를 중지합니다.
기본적으로 **중지 프로세스** 는 현재 사용자가 소유 하지 않은 프로세스를 중지 하기 전에 확인 메시지를 표시 합니다.

프로세스의 소유자를 찾으려면 cmdlet을 사용 하 여 `Get-CimInstance` 프로세스를 나타내는 **Win32_Process** 개체를 가져온 다음 개체의 **getowner** 메서드를 사용 합니다.

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

### -Id

중지할 프로세스의 프로세스 Id를 지정 합니다.
여러 ID를 지정하려면 쉼표를 사용하여 ID를 구분합니다.
프로세스의 PID를 찾으려면를 입력 `Get-Process` 합니다.

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

### -InputObject

중지할 프로세스 개체를 지정 합니다.
개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요.

```yaml
Type: System.Diagnostics.Process[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name

중지할 프로세스의 프로세스 이름을 지정 합니다.
쉼표로 구분 된 여러 프로세스 이름을 입력 하거나 와일드 카드 문자를 사용할 수 있습니다.

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases: ProcessName

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -PassThru

프로세스를 나타내는 개체를 반환 합니다.
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

### System.Diagnostics.Process

프로세스 개체를이 cmdlet으로 파이프 할 수 있습니다.

## 출력

### 없음, 시스템 진단 프로세스

이 cmdlet은 *PassThru* 매개 변수를 지정 하는 경우 중지 된 프로세스를 나타내는 **system.object** 개체를 반환 합니다.
그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.

## 참고

* 기본 제공 별칭, **kill** 및 **spps** 를 기준으로 **중지 프로세스** 를 참조할 수도 있습니다. 자세한 내용은 about_Aliases를 참조하세요.

  Windows PowerShell에서 WMI (WMI(Windows Management Instrumentation)) **Win32_Process** 개체의 속성 및 메서드를 사용할 수도 있습니다.
자세한 내용은 `Get-CimInstance` 및 WMI SDK를 참조 하십시오.

* 프로세스를 중지 하면 프로세스를 중지 하 고 프로세스에 의존 하는 서비스가 중지 될 수 있습니다.
극히 드문 경우이지만 프로세스를 중지하면 Windows가 중지될 수도 있습니다.

## 관련 링크

[Debug-Process](Debug-Process.md)

[Get-Process](Get-Process.md)

[Start-Process](Start-Process.md)

[Stop-Process](Stop-Process.md)

[Wait-Process](Wait-Process.md)
