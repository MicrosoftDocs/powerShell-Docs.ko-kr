---
external help file: PSDiagnostics-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/start-trace?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Trace
ms.openlocfilehash: cbdb40edf85dd4645552f6e096a99384532b4443
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93213514"
---
# Start-Trace

## 개요
이벤트 추적 로깅 세션을 시작 합니다.

## SYNTAX

```
Start-Trace [-SessionName] <String> [[-OutputFilePath] <String>] [[-ProviderFilePath] <String>]
 [-ETS] [-Format <String>] [-MinBuffers <Int32>] [-MaxBuffers <Int32>]
 [-BufferSizeInKB <Int32>] [-MaxLogFileSizeInMB <Int32>] [<CommonParameters>]
```

## 설명
이 cmdlet은 Windows 이벤트 추적 로깅 세션을 시작 합니다.

이 cmdlet은 다음 cmdlet에서 사용 됩니다.

- `Enable-PSWSManCombinedTrace`
- `Enable-WSManTrace`

관리자 권한 PowerShell 세션에서이 cmdlet을 실행 해야 합니다.

## 예제

### 예제 1: WSMan 추적 로깅 세션 시작

```powershell
Start-Trace -SessionName 'wsmlog' -ETS -OutputFilePath "$env:windir\system32\wsmtraces.log" -Format 'bincirc' -MinBuffers 16 -MaxBuffers 256 -BufferSizeInKb 64 -MaxLogFileSizeInMB 256 -ProviderFilePath "$env:windir\system32\wsmtraceproviders.txt"
```

## PARAMETERS

### -BufferSizeInKB
이벤트 추적 세션 버퍼 크기 (kb)입니다.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 0
Accept pipeline input: False
Accept wildcard characters: False
```

### -%
이벤트 추적 세션 명령을 저장 하거나 예약 하지 않고 직접 보냅니다.

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

### -형식
데이터 수집기에 대 한 로그 형식을 지정합니다. SQL database 형식의 경우 명령줄에서 값을 사용 하 여 **Outputfilepath** 옵션을 사용 해야 합니다 `dsn!log` . 기본값은 binary (bin)입니다. 가능한 값은 다음과 같습니다.

- bin-이진
- bincirc-순환 로깅을 사용 하는 이진 파일
- csv-쉼표로 구분 된 값
- tsv-탭으로 구분 된 값
- sql-SQL 데이터베이스

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:
Accepted values: bin, bincirc, csv, tsv, sql

Required: False
Position: Named
Default value: bin
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaxBuffers
이벤트 추적 세션 버퍼의 최대 수를 설정 합니다.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 256
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaxLogFileSizeInMB
SQL 로그의 최대 로그 파일 크기 (MB) 또는 레코드 수를 설정 합니다.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 0 (no limit)
Accept pipeline input: False
Accept wildcard characters: False
```

### -MinBuffers
이벤트 추적 세션 버퍼의 최소 수를 설정 합니다.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 0
Accept pipeline input: False
Accept wildcard characters: False
```

### -OutputFilePath
SQL 데이터베이스에 있는 출력 로그 파일의 경로 또는 DSN 및 로그 집합 이름입니다. 기본 경로는 `$env:systemdrive\PerfLogs\Admin`입니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: $env:systemdrive\PerfLogs\Admin
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProviderFilePath
사용할 여러 이벤트 추적 공급자를 나열 하는 파일입니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -세션 이름
이벤트 추적 세션의 이름입니다. 추적 세션을 중지 하려면 세션 이름을 알아야 합니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### 없음

## 출력

### System.Object

## 참고

## 관련 링크

[이벤트 추적](/windows/desktop/ETW/event-tracing-portal)

[Stop-Trace](stop-trace.md)

[Disable-PSWSManCombinedTrace](Disable-PSWSManCombinedTrace.md)

[Disable-WSManTrace](Disable-WSManTrace.md)

[Enable-PSWSManCombinedTrace](Enable-PSWSManCombinedTrace.md)

[Enable-WSManTrace](Enable-WSManTrace.md)
