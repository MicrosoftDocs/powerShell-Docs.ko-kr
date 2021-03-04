---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/clear-eventlog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-EventLog
ms.openlocfilehash: af1c808b22a812700857e756136fd570fa0acc35
ms.sourcegitcommit: 1dfd5554b70c7e8f4e3df19e29c384a9c0a4b227
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/03/2021
ms.locfileid: "101685907"
---
# Clear-EventLog

## 개요
로컬 또는 원격 컴퓨터의 지정 된 이벤트 로그에서 모든 항목을 지웁니다.

## SYNTAX

```
Clear-EventLog [-LogName] <String[]> [[-ComputerName] <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명

`Clear-EventLog`Cmdlet은 로컬 컴퓨터 또는 원격 컴퓨터의 지정 된 이벤트 로그에서 모든 항목을 삭제 합니다. 를 사용 하려면 `Clear-EventLog` 영향을 받는 컴퓨터에서 Administrators 그룹의 구성원 이어야 합니다.

**Eventlog** 명사를 포함 하는 Cmdlet (eventlog cmdlet)은 클래식 이벤트 로그 에서만 작동 합니다. Windows Vista 이상 버전의 windows 이벤트 로그 기술을 사용 하는 로그에서 이벤트를 가져오려면 Get-WinEvent cmdlet을 사용 합니다.

## 예제

### 예 1: 로컬 컴퓨터에서 특정 이벤트 로그 유형 지우기

```powershell
Clear-EventLog "Windows PowerShell"
```

이 명령은 로컬 컴퓨터의 Windows PowerShell 이벤트 로그에서 항목을 지웁니다.

### 예 2: 로컬 및 원격 컴퓨터에서 특정 다중 로그 형식 지우기

```powershell
Clear-EventLog -LogName ODiag, OSession -ComputerName localhost, Server02
```

이 명령은 로컬 컴퓨터와 Server02 원격 컴퓨터의 ODiag (Microsoft Office 진단) 및 Microsoft Office 세션 (Odiag) 로그에 있는 모든 항목을 지웁니다.

### 예 3: 지정 된 컴퓨터의 모든 로그를 지우고 이벤트 로그 목록을 표시 합니다.

```powershell
Clear-EventLog -LogName application, system -confirm
```

이 명령은 지정된 이벤트 로그의 항목을 삭제하기 전에 사용자에게 확인 메시지를 표시합니다.

### 예 4: 지정 된 컴퓨터의 모든 로그를 지우고 이벤트 로그 목록을 표시 합니다.

```powershell
function clear-all-event-logs ($computerName="localhost")
{
   $logs = Get-EventLog -ComputerName $computername -List | ForEach-Object {$_.Log}
   $logs | ForEach-Object {Clear-EventLog -ComputerName $computername -LogName $_ }
   Get-EventLog -ComputerName $computername -list
}

clear-all-event-logs -ComputerName Server01
```

```Output
Max(K) Retain OverflowAction        Entries Log
------ ------ --------------        ------- ---
15,168      0 OverwriteAsNeeded           0 Application
15,168      0 OverwriteAsNeeded           0 DFS Replication
512         7 OverwriteOlder              0 DxStudio
20,480      0 OverwriteAsNeeded           0 Hardware Events
512         7 OverwriteOlder              0 Internet Explorer
20,480      0 OverwriteAsNeeded           0 Key Management Service
16,384      0 OverwriteAsNeeded           0 Microsoft Office Diagnostics
16,384      0 OverwriteAsNeeded           0 Microsoft Office Sessions
30,016      0 OverwriteAsNeeded           1 Security
15,168      0 OverwriteAsNeeded           2 System
15,360      0 OverwriteAsNeeded           0 Windows PowerShell
```

이 함수는 지정된 컴퓨터의 모든 이벤트 로그를 지운 다음 결과 이벤트 로그 목록을 표시합니다.

로그를 지운 후 표시하기 전에 시스템 로그 및 보안 로그에 몇 개의 항목이 추가되었습니다.

## PARAMETERS

### -ComputerName

원격 컴퓨터를 지정합니다. 기본값은 로컬 컴퓨터입니다.

원격 컴퓨터의 NetBIOS 이름, IP(인터넷 프로토콜) 주소 또는 정규화된 도메인 이름을 입력하세요. 로컬 컴퓨터를 지정하려면 컴퓨터 이름, 점(.) 또는 "localhost"를 입력합니다.

이 매개 변수는 Windows PowerShell 원격 기능을 사용하지 않습니다.  `Get-EventLog` 컴퓨터가 원격 명령을 실행 하도록 구성 되지 않은 경우에도의 ComputerName 매개 변수를 사용할 수 있습니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Cn

Required: False
Position: 1
Default value: Local computer
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -LogName

이벤트 로그를 지정합니다. 하나 이상의 이벤트 로그에 대 한 로그 이름 ( **Logdisplayname** 이 아닌 **log** 속성 값)을 쉼표로 구분 하 여 입력 합니다. 와일드카드 문자는 사용할 수 없습니다. 이 매개 변수는 필수적 요소입니다.

> [!IMPORTANT]
> 이 매개 변수는 속성 이름별로 파이프라인의 값을 허용 합니다. 그러나이 작업을 수행 하지 못하게 하는 버그가 있습니다. 매개 변수를 직접 사용 하 여 값을 전달 해야 합니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: LN

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

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.

## 입력

### 없음

개체를에 연결할 수 없습니다 `Clear-EventLog` .

## 출력

### 없음

이 cmdlet은 어떠한 출력도 생성하지 않습니다.

## 참고

- Windows `Clear-EventLog` Vista 이상 버전에서을 사용 하려면 "관리자 권한으로 실행" 옵션을 사용 하 여 Windows PowerShell을 시작 합니다.

## 관련 링크

[Get-EventLog](Get-EventLog.md)

[Limit-EventLog](Limit-EventLog.md)

[New-EventLog](New-EventLog.md)

[Remove-EventLog](Remove-EventLog.md)

[Show-EventLog](Show-EventLog.md)

[Write-EventLog](Write-EventLog.md)
