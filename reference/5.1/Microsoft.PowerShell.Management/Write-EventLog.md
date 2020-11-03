---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/write-eventlog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-EventLog
ms.openlocfilehash: cae34c4cf942d9aa4abb9a2d716ef9854f70de2e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93214297"
---
# Write-EventLog

## 개요
이벤트 로그에 이벤트를 기록합니다.

## SYNTAX

```
Write-EventLog [-LogName] <String> [-Source] <String> [[-EntryType] <EventLogEntryType>] [-Category <Int16>]
 [-EventId] <Int32> [-Message] <String> [-RawData <Byte[]>] [-ComputerName <String>] [<CommonParameters>]
```

## 설명
**EventLog** cmdlet은 이벤트 로그에 이벤트를 기록 합니다.

이벤트 로그에 이벤트를 쓰려면 컴퓨터에 이벤트 로그가 있어야 하고 이벤트 로그의 원본이 등록되어 있어야 합니다.

**Eventlog** 명사를 포함 하는 Cmdlet ( **eventlog** cmdlet)은 클래식 이벤트 로그 에서만 작동 합니다.
Windows Vista 이상 버전의 windows 운영 체제에서 Windows 이벤트 로그 기술을 사용 하는 로그에서 이벤트를 가져오려면 Get-WinEvent cmdlet을 사용 합니다.

## 예제

### 예제 1: 응용 프로그램 이벤트 로그에 이벤트 쓰기

```
PS C:\> Write-EventLog -LogName "Application" -Source "MyApp" -EventID 3001 -EntryType Information -Message "MyApp added a user-requested feature to the display." -Category 1 -RawData 10,20
```

이 명령은 MyApp 원본의 이벤트를 애플리케이션 이벤트 로그에 씁니다.

### 예제 2: 원격 컴퓨터의 응용 프로그램 이벤트 로그에 이벤트 쓰기

```
PS C:\> Write-EventLog -ComputerName "Server01" -LogName Application -Source "MyApp" -EventID 3001 -Message "MyApp added a user-requested feature to the display."
```

이 명령은 MyApp 원본의 이벤트를 Server01 원격 컴퓨터의 애플리케이션 이벤트 로그에 씁니다.

## PARAMETERS

### -범주
이벤트의 작업 범주를 지정합니다.
이벤트 로그에 대한 범주 메시지 파일의 문자열과 연결된 정수를 입력합니다.

```yaml
Type: System.Int16
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName
원격 컴퓨터를 지정합니다.
기본값은 로컬 컴퓨터입니다.

원격 컴퓨터의 NetBIOS 이름, IP 주소 또는 정규화된 도메인 이름을 입력하세요.

이 매개 변수는 Windows PowerShell 원격 기능을 사용하지 않습니다.
컴퓨터가 원격 명령을 실행 하도록 구성 되지 않은 경우에도 Get-EventLog cmdlet의 *ComputerName* 매개 변수를 사용할 수 있습니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: CN

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Entrytype 관련이
이벤트의 항목 유형을 지정합니다.
이 매개 변수에 허용 되는 값은 Error, Warning, Information, SuccessAudit 및 FailureAudit입니다.
기본값은 Information입니다.

값에 대 한 설명은 MSDN library에서 [EventLogEntryType 열거](https://go.microsoft.com/fwlink/?LinkId=143599) 를 참조 하세요.

```yaml
Type: System.Diagnostics.EventLogEntryType
Parameter Sets: (All)
Aliases: ET
Accepted values: Error, Information, FailureAudit, SuccessAudit, Warning

Required: False
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -EventId
이벤트 식별자를 지정합니다.
이 매개 변수는 필수적 요소입니다.
*EventId* 매개 변수의 최대값은 65535입니다.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: ID, EID

Required: True
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LogName
이벤트가 기록되는 로그의 이름을 지정합니다.
로그 이름을 입력 합니다.
로그 이름은 **Logdisplayname** 이 아닌 **log** 속성의 값입니다.
와일드카드 문자는 사용할 수 없습니다.
이 매개 변수는 필수적 요소입니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: LN

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -메시지
이벤트 메시지를 지정합니다.
이 매개 변수는 필수적 요소입니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: MSG

Required: True
Position: 4
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RawData
이벤트와 연결된 이진 데이터를 바이트 단위로 지정합니다.

```yaml
Type: System.Byte[]
Parameter Sets: (All)
Aliases: RD

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Source
이벤트 원본을 지정합니다. 일반적으로 로그에 이벤트를 쓰는 애플리케이션의 이름입니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: SRC

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### 없음
이 cmdlet에 입력을 파이프할 수 없습니다.

## 출력

### EventLogEntry
이 cmdlet은 로그의 이벤트를 나타내는 개체를 반환 합니다.

## 참고

* **쓰기 이벤트** 를 사용 하려면 관리자 권한으로 실행 옵션을 사용 하 여 Windows PowerShell을 시작 합니다.

*

## 관련 링크

[Clear-EventLog](Clear-EventLog.md)

[Get-EventLog](Get-EventLog.md)

[Limit-EventLog](Limit-EventLog.md)

[New-EventLog](New-EventLog.md)

[Remove-EventLog](Remove-EventLog.md)

[Show-EventLog](Show-EventLog.md)

[Write-EventLog](Write-EventLog.md)
