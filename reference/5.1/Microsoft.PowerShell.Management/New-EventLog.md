---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 01/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-eventlog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-EventLog
ms.openlocfilehash: 61fafc0670a24fd6ca057e4cf0c7179d90446b07
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93214618"
---
# New-EventLog

## 개요
로컬 또는 원격 컴퓨터에 새 이벤트 로그 및 새 이벤트 원본을 만듭니다.

## SYNTAX

```
New-EventLog [-LogName] <string> [-Source] <string[]> [[-ComputerName] <string[]>]
  [-CategoryResourceFile <string>] [-MessageResourceFile <string>] [-ParameterResourceFile <string>]
  [<CommonParameters>]
```

## 설명

이 cmdlet은 로컬 또는 원격 컴퓨터에 새 기본 이벤트 로그를 만듭니다. 새 로그나 기존 로그에 항목을 기록하는 이벤트 원본을 등록할 수도 있습니다.

EventLog 명사(이벤트 로그 cmdlet)를 포함하는 cmdlet은 기본 이벤트 로그에서만 작동합니다.
Windows Vista 이상 버전의 windows 이벤트 로그 기술을 사용 하는 로그에서 이벤트를 가져오려면를 사용 `Get-WinEvent` 합니다.

## 예제

### 예 1-새 이벤트 로그 만들기

이 명령은 로컬 컴퓨터에 TestLog 이벤트 로그를 만들고 이 이벤트 로그에 대한 새 원본을 등록합니다.

```powershell
New-EventLog -source TestApp -LogName TestLog -MessageResourceFile C:\Test\TestApp.dll
```

### 예 2-기존 로그에 새 이벤트 원본 추가

이 명령은 NewTestApp라는 새 이벤트 원본을 Server01 원격 컴퓨터의 Application 로그에 추가합니다.

```powershell
$file = "C:\Program Files\TestApps\NewTestApp.dll"
New-EventLog -ComputerName Server01 -Source NewTestApp -LogName Application -MessageResourceFile $file -CategoryResourceFile $file
```

이 명령을 실행하려면 Server01 컴퓨터에 NewTestApp.dll 파일이 있어야 합니다.

## PARAMETERS

### -CategoryResourceFile

원본 이벤트에 대한 범주 문자열이 포함된 파일의 경로를 지정합니다. 이 파일을 범주 메시지 파일이라고도 합니다.

이 파일은 이벤트 로그가 작성되는 컴퓨터에 있어야 합니다. 이 매개 변수는 파일을 만들거나 이동하지 않습니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: CRF

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

지정된 컴퓨터에 새 이벤트 로그를 만듭니다. 기본값은 로컬 컴퓨터입니다.

원격 컴퓨터의 NetBIOS 이름, IP 주소 또는 정규화 된 도메인 이름입니다.
로컬 컴퓨터를 지정하려면 컴퓨터 이름, 점(.) 또는 "localhost"를 입력합니다.

이 매개 변수는 PowerShell 원격을 사용 하지 않습니다. **ComputerName** `Get-EventLog` 컴퓨터가 원격 명령을 실행 하도록 구성 되지 않은 경우에도의 ComputerName 매개 변수를 사용할 수 있습니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN

Required: False
Position: 3
Default value: Local computer
Accept pipeline input: False
Accept wildcard characters: False
```

### -LogName

이벤트 로그의 이름을 지정합니다.

로그가 없으면에서 `New-EventLog` 로그를 만들고 새 이벤트 로그의 **Log** 및 **logdisplayname** 속성에이 값을 사용 합니다. 로그가 있으면에서 `New-EventLog` 이벤트 로그에 대 한 새 원본을 등록 합니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: LN

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MessageResourceFile

원본 이벤트에 대한 메시지 형식 지정 문자열이 포함된 파일의 경로를 지정합니다.
이 파일을 이벤트 메시지 파일이라고도 합니다.

이 파일은 이벤트 로그가 작성되는 컴퓨터에 있어야 합니다.
이 매개 변수는 파일을 만들거나 이동하지 않습니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: MRF

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ParameterResourceFile

이벤트 설명에서 매개 변수 대체에 사용되는 문자열이 포함된 파일의 경로를 지정합니다. 이 파일을 매개 변수 메시지 파일이라고도 합니다.

이 파일은 이벤트 로그가 작성되는 컴퓨터에 있어야 합니다.
이 매개 변수는 파일을 만들거나 이동하지 않습니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PRF

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Source

이벤트 로그에 기록하는 애플리케이션과 같은 이벤트 로그 원본의 이름을 지정합니다. 이 매개 변수는 필수적 요소입니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: SRC

Required: True
Position: 2
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

## 참고

`New-EventLog`Windows Vista 이상 버전에서을 사용 하려면 "관리자 권한으로 실행" 옵션을 사용 하 여 PowerShell을 엽니다.

Windows Vista, Windows XP Professional 또는 Windows Server 2003에서 이벤트 원본을 만들려면 해당 컴퓨터의 관리자 그룹 멤버여야 합니다.

새 이벤트 로그 및 새 이벤트 원본을 만들면 새 로그에 대한 새 원본이 시스템에 등록되지만 로그에 첫 번째 항목이 기록되기 전까지는 로그가 만들어지지 않습니다.

이벤트 로그는 운영 체제에 파일로 저장됩니다.

새 이벤트 로그를 만들 때 연결 된 파일은 `$env:SystemRoot\System32\Config` 지정 된 컴퓨터의 디렉터리에 저장 됩니다.

파일 이름은 **Log** 속성의 처음 8 자와 .evt 파일 이름 확장명을 사용 합니다.

## 관련 링크

[Clear-EventLog](Clear-EventLog.md)

[Get-EventLog](Get-EventLog.md)

[Get-WinEvent](../Microsoft.PowerShell.Diagnostics/Get-WinEvent.md)

[Limit-EventLog](Limit-EventLog.md)

[New-EventLog](New-EventLog.md)

[Remove-EventLog](Remove-EventLog.md)

[Show-EventLog](Show-EventLog.md)

[Write-EventLog](Write-EventLog.md)
