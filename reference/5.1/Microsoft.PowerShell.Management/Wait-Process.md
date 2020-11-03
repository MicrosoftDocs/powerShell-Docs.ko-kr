---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/wait-process?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Wait-Process
ms.openlocfilehash: 38e225a1973022f82a40694cfad89b94d050509e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93214329"
---
# Wait-Process

## 개요
프로세스가 중지될 때까지 대기한 후 추가 입력을 받습니다.

## SYNTAX

### 이름 (기본값)

```
Wait-Process [-Name] <String[]> [[-Timeout] <Int32>] [<CommonParameters>]
```

### Id

```
Wait-Process [-Id] <Int32[]> [[-Timeout] <Int32>] [<CommonParameters>]
```

### InputObject

```
Wait-Process [[-Timeout] <Int32>] -InputObject <Process[]> [<CommonParameters>]
```

## 설명
**대기 프로세스** cmdlet은 실행 중인 하나 이상의 프로세스가 중지 될 때까지 대기한 후 입력을 허용 합니다.
Windows PowerShell 콘솔에서 이 cmdlet을 실행하면 프로세스가 중지될 때까지 명령 프롬프트가 나타나지 않습니다.
프로세스 이름 또는 프로세스 ID (PID)로 프로세스를 지정 하거나 프로세스 개체를 **대기 프로세스로** 파이프 하 여 지정할 수 있습니다.

**대기 프로세스** 는 로컬 컴퓨터에서 실행 중인 프로세스 에서만 작동 합니다.

## 예제

### 예 1: 프로세스를 중지 하 고 대기

```
PS C:\> $nid = (Get-Process notepad).id
PS C:\> Stop-Process -Id $nid
PS C:\> Wait-Process -Id $nid
```

이 예제에서는 메모장 프로세스를 중지 하 고 프로세스가 중지 될 때까지 기다린 후 다음 명령을 실행 합니다.

첫 번째 명령은 **Get process** cmdlet을 사용 하 여 메모장 프로세스의 ID를 가져옵니다.
$Nid 변수에 ID를 저장 합니다.

두 번째 명령은 Stop-Process cmdlet을 사용 하 여 $nid에 저장 된 ID를 사용 하 여 프로세스를 중지 합니다.

세 번째 명령은 **대기 프로세스** 를 사용 하 여 Notepad 프로세스가 중지 될 때까지 대기 합니다.
**대기 프로세스** 의 *Id* 매개 변수를 사용 하 여 프로세스를 식별 합니다.

### 예제 2: 프로세스 지정

```
PS C:\> $p = Get-Process notepad
PS C:\> Wait-Process -Id $p.id
PS C:\> Wait-Process -Name "notepad"
PS C:\> Wait-Process -InputObject $p
```

이러한 명령은 프로세스를 **대기 프로세스로** 지정 하는 세 가지 방법을 보여 줍니다.
첫 번째 명령은 메모장 프로세스를 가져와 $p 변수에 저장 합니다.

두 번째 명령은 *Id* 매개 변수를 사용 하 고, 세 번째 명령은 *Name* 매개 변수를 사용 하며, 네 번째 명령은 *InputObject* 매개 변수를 사용 합니다.

이 세 명령의 결과는 동일하며 상호 교환적으로 사용할 수 있습니다.

### 예제 3: 지정 된 시간 동안 프로세스 대기

```
PS C:\> Wait-Process -Name outlook, winword -Timeout 30
```

이 명령은 Outlook 및 Winword 프로세스가 중지될 때까지 30초 동안 대기합니다.
두 프로세스 모두 중지되지 않으면 종료되지 않는 오류와 명령 프롬프트를 반환합니다.

## PARAMETERS

### -Id
프로세스의 프로세스 ID를 지정합니다.
여러 ID를 지정하려면 쉼표를 사용하여 ID를 구분합니다.
프로세스의 PID를 찾으려면를 입력 `Get-Process` 합니다.

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
프로세스 개체를 전송하여 프로세스를 지정합니다.
프로세스 개체가 포함 된 변수를 입력 하거나 프로세스 개체를 가져오는 명령 또는 식 (예: Get-Process cmdlet)을 입력 합니다.

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
프로세스의 프로세스 이름을 지정합니다.
여러 이름을 지정하려면 쉼표를 사용하여 이름을 구분합니다.
와일드카드 문자는 지원되지 않습니다.

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

### -시간 제한
지정 된 프로세스가 중지 될 때까지이 cmdlet이 대기 하는 최대 시간 (초)을 지정 합니다.
이 간격이 만료되면 명령은 여전히 실행되고 있는 프로세스를 나열하는 종료되지 않은 오류를 표시하고 대기를 종료합니다.
기본적으로 시간 제한이 없습니다.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: TimeoutSec

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.Diagnostics.Process
프로세스 개체를이 cmdlet으로 파이프 할 수 있습니다.

## 출력

### 없음
이 cmdlet은 어떠한 출력도 생성하지 않습니다.

## 참고

* 이 cmdlet은 System.object 클래스의 **Waitforexit** 메서드를 사용 합니다. 이 메서드에 대한 자세한 내용은 Microsoft .NET Framework SDK를 참조하세요.

*

## 관련 링크

[Debug-Process](Debug-Process.md)

[Get-Process](Get-Process.md)

[Start-Process](Start-Process.md)

[Stop-Process](Stop-Process.md)

[Wait-Process](Wait-Process.md)
