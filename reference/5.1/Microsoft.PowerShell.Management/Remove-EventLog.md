---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-eventlog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-EventLog
ms.openlocfilehash: 4cf29146727c9a54715459a2d56e47a27c5bacc0
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93214554"
---
# Remove-EventLog

## 개요
이벤트 로그를 삭제하거나 이벤트 원본의 등록을 취소합니다.

## SYNTAX

### Default (기본값)

```
Remove-EventLog [[-ComputerName] <String[]>] [-LogName] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### 원본

```
Remove-EventLog [[-ComputerName] <String[]>] [-Source <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명
EventLog cmdlet은 로컬 또는 원격 컴퓨터에서 이벤트 로그 파일을 삭제 하 고 로그에 대 한 모든 이벤트 원본의 등록을 **취소** 합니다.
이 cmdlet을 사용하면 이벤트 로그를 삭제하지 않고 이벤트 원본의 등록을 취소할 수 있습니다.

**Eventlog 명사 인** **eventlog** cmdlet은 클래식 이벤트 로그 에서만 작동 합니다.
Windows Vista 이상 버전의 windows 운영 체제에서 Windows 이벤트 로그 기술을 사용 하는 로그에서 이벤트를 가져오려면 WinEvent를 사용 합니다.

주의:이 cmdlet은 운영 체제 이벤트 로그를 삭제할 수 있으며,이로 인해 응용 프로그램 오류 및 예기치 않은 시스템 동작이 발생할 수 있습니다.

## 예제

### 예 1: 로컬 컴퓨터에서 이벤트 로그 제거

```
PS C:\> Remove-EventLog -LogName "MyLog"
```

이 명령은 로컬 컴퓨터에서 MyLog 이벤트 로그를 삭제하고 해당 이벤트 원본의 등록을 취소합니다.

### 예 2: 여러 컴퓨터에서 이벤트 로그 제거

```
PS C:\> Remove-EventLog -LogName "MyLog", "TestLog" -ComputerName "Server01", "Server02", "localhost"
```

이 명령은 로컬 컴퓨터와 Server01 및 Server02 원격 컴퓨터에서 MyLog 및 TestLog 이벤트 로그를 삭제 합니다.
이러한 로그에 대한 이벤트 원본의 등록을 취소합니다.

### 예제 3: 이벤트 소스 삭제

```
PS C:\> Remove-EventLog -Source "MyApp"
```

이 명령은 로컬 컴퓨터의 로그에서 MyApp 이벤트 원본을 삭제합니다.
명령이 완료 되 면 MyApp 프로그램은 이벤트 로그에 쓸 수 없습니다.

### 예제 4: 이벤트 로그 제거 및 작업 확인

```
The first command lists the event logs on the local computer.
PS C:\> Get-EventLog -List
Max(K) Retain OverflowAction        Entries Log
------ ------ --------------        ------- ---
15,168      0 OverwriteAsNeeded      22,923 Application
15,168      0 OverwriteAsNeeded          53 DFS Replication
15,168      7 OverwriteOlder              0 Hardware Events
512      7 OverwriteOlder              0 Internet Explorer
20,480      0 OverwriteAsNeeded           0 Key Management Service
30,016      0 OverwriteAsNeeded      50,060 Security
15,168      0 OverwriteAsNeeded      27,592 System
15,360      0 OverwriteAsNeeded      18,355 Windows PowerShell
15,168      7 OverwriteAsNeeded          12 ZapLog

The second command deletes the ZapLog event log.
PS C:\> Remove-EventLog -LogName "ZapLog"

The third command lists the event logs again. The ZapLog event log no longer appears in the list.
PS C:\> Get-EventLog -List
Max(K) Retain OverflowAction        Entries Log
------ ------ --------------        ------- ---
15,168      0 OverwriteAsNeeded      22,923 Application
15,168      0 OverwriteAsNeeded          53 DFS Replication
15,168      7 OverwriteOlder              0 Hardware Events
512      7 OverwriteOlder              0 Internet Explorer
20,480      0 OverwriteAsNeeded           0 Key Management Service
30,016      0 OverwriteAsNeeded      50,060 Security
15,168      0 OverwriteAsNeeded      27,592 System
15,360      0 OverwriteAsNeeded      18,355 Windows PowerShell
```

이 명령은 컴퓨터의 이벤트 로그를 나열 하 고 이벤트 로그 **제거** 명령이 성공적으로 수행 되었는지 확인 하는 방법을 보여 줍니다.

### 예 5: 이벤트 소스 제거 및 작업 확인

```
PS C:\> Get-WmiObject win32_nteventlogfile -Filter "logfilename='TestLog'" | foreach {$_.sources}
MyApp
TestApp
PS C:\> Remove-Eventlog -Source "MyApp"
PS C:\> Get-WmiObject win32_nteventlogfile -Filter "logfilename='TestLog'"} | foreach {$_.sources}
TestApp
```

이 명령은 Get-WmiObject cmdlet을 사용하여 로컬 컴퓨터의 이벤트 원본을 나열합니다.
이 명령을 사용하면 명령이 성공적으로 실행되었는지 확인하거나 이벤트 원본을 삭제할 수 있습니다.

첫 번째 명령은 로컬 컴퓨터에 있는 TestLog 이벤트 로그의 이벤트 원본을 가져옵니다.
MyApp도 원본 중 하나입니다.

두 번째 명령은 **Remove EventLog** 의 *Source* 매개 변수를 사용 하 여 MyApp 이벤트 원본을 삭제 합니다.

세 번째 명령은 첫 번째 명령과 동일하며
MyApp 이벤트 원본이 삭제되었음을 보여 줍니다.

## PARAMETERS

### -ComputerName
원격 컴퓨터를 지정합니다.
기본값은 로컬 컴퓨터입니다.

원격 컴퓨터의 NetBIOS 이름, IP 주소 또는 정규화된 도메인 이름을 입력하세요.
로컬 컴퓨터를 지정 하려면 컴퓨터 이름, 점 (.) 또는 localhost를 입력 합니다.

이 매개 변수는 Windows PowerShell 원격 기능을 사용하지 않습니다.
컴퓨터에서 원격 명령을 실행 하도록 구성 되지 않은 경우에도 **제거 이벤트** 의 *ComputerName* 매개 변수를 사용할 수 있습니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LogName
이벤트 로그를 지정합니다.
하나 이상의 이벤트 로그에 대 한 로그 이름을 쉼표로 구분 하 여 입력 합니다.
로그 이름은 *Logdisplayname* 이 아닌 **log** 속성의 값입니다. 와일드 카드 문자는 허용 되지 않습니다.
이 매개 변수는 필수적 요소입니다.

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases: LN

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Source
이 cmdlet의 등록을 취소 하는 이벤트 원본을 지정 합니다.
실행 파일 이름이 아닌 원본 이름을 쉼표로 구분 하 여 입력 합니다.

```yaml
Type: System.String[]
Parameter Sets: Source
Aliases: SRC

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

### 없음
이 cmdlet에 입력을 파이프할 수 없습니다.

## 출력

### 없음
이 cmdlet은 어떠한 출력도 반환되지 않습니다.

## 참고

* Windows Vista 및 이후 버전의 Windows 운영 체제에서 **제거 이벤트** 를 사용 하려면 관리자 권한으로 실행 옵션을 사용 하 여 windows PowerShell을 시작 합니다.

  이벤트 로그를 제거한 다음 다시 만들면 같은 이벤트 원본을 등록할 수 없습니다.
이벤트 원본을 사용하여 원래 로그에 항목을 기록했던 애플리케이션에서 새 로그에 항목을 기록할 수 없게 됩니다.

* 특정 로그에 대한 이벤트 원본의 등록을 취소할 경우 이벤트 원본에서 다른 이벤트 로그에 항목을 기록하지 못하게 될 수도 있습니다.

## 관련 링크

[Clear-EventLog](Clear-EventLog.md)

[Get-EventLog](Get-EventLog.md)

[Limit-EventLog](Limit-EventLog.md)

[New-EventLog](New-EventLog.md)

[Remove-EventLog](Remove-EventLog.md)

[Show-EventLog](Show-EventLog.md)

[Write-EventLog](Write-EventLog.md)
