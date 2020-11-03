---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 3/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-eventlog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-EventLog
ms.openlocfilehash: ab1a97dc3c78bbfdcc239fd573ef3b1f839e2b21
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93215466"
---
# Get-EventLog

## 개요
로컬 컴퓨터 또는 원격 컴퓨터에 있는 이벤트 로그의 이벤트 또는 이벤트 로그 목록을 가져옵니다.

## SYNTAX

### LogName (기본값)

```
Get-EventLog [-LogName] <String> [-ComputerName <String[]>] [-Newest <Int32>] [-After <DateTime>]
 [-Before <DateTime>] [-UserName <String[]>] [[-InstanceId] <Int64[]>] [-Index <Int32[]>]
 [-EntryType <String[]>] [-Source <String[]>] [-Message <String>] [-AsBaseObject]
 [<CommonParameters>]
```

### 목록

```
Get-EventLog [-ComputerName <String[]>] [-List] [-AsString] [<CommonParameters>]
```

## 설명

`Get-EventLog`Cmdlet은 로컬 및 원격 컴퓨터에서 이벤트 및 이벤트 로그를 가져옵니다. 기본적으로 `Get-EventLog` 는 로컬 컴퓨터에서 로그를 가져옵니다. 원격 컴퓨터에서 로그를 가져오려면 **ComputerName** 매개 변수를 사용 합니다.

`Get-EventLog`매개 변수 및 속성 값을 사용 하 여 이벤트를 검색할 수 있습니다. Cmdlet은 지정 된 속성 값과 일치 하는 이벤트를 가져옵니다.

명사를 포함 하는 PowerShell cmdlet은 `EventLog` 응용 프로그램, 시스템 또는 보안과 같은 Windows 클래식 이벤트 로그 에서만 작동 합니다. Windows Vista 이상 버전의 windows 이벤트 로그 기술을 사용 하는 로그를 가져오려면를 사용 `Get-WinEvent` 합니다.

> [!NOTE]
> `Get-EventLog` 는 사용 되지 않는 Win32 API를 사용 합니다. 결과가 정확 하지 않을 수 있습니다. `Get-WinEvent`대신 cmdlet을 사용 하십시오.

## 예제

### 예 1: 로컬 컴퓨터에서 이벤트 로그 가져오기

이 예에서는 로컬 컴퓨터에서 사용할 수 있는 이벤트 로그 목록을 표시 합니다. 로그 열의 이름은 이벤트를 검색 하는 로그를 지정 하기 위해 **LogName** 매개 변수와 함께 사용 됩니다.

```powershell
Get-EventLog -List
```

```Output
Max(K)   Retain   OverflowAction      Entries  Log
------   ------   --------------      -------  ---
15,168        0   OverwriteAsNeeded   20,792   Application
15,168        0   OverwriteAsNeeded   12,559   System
15,360        0   OverwriteAsNeeded   11,173   Windows PowerShell
```

`Get-EventLog`Cmdlet은 **List** 매개 변수를 사용 하 여 사용 가능한 로그를 표시 합니다.

### 예 2: 로컬 컴퓨터의 이벤트 로그에서 최근 항목 가져오기

이 예제에서는 시스템 이벤트 로그에서 최근 항목을 가져옵니다.

```powershell
Get-EventLog -LogName System -Newest 5
```

```Output
Index   Time          EntryType    Source              InstanceID   Message
-----   ----          ---------    ------              ----------   -------
13820   Jan 17 19:16  Error        DCOM                     10016   The description for Event...
13819   Jan 17 19:08  Error        DCOM                     10016   The description for Event...
13818   Jan 17 19:06  Information  Service Control...  1073748864   The start type of the Back...
13817   Jan 17 19:05  Error        DCOM                     10016   The description for Event...
13815   Jan 17 19:03  Information  Microsoft-Windows...        35   The time service is now sync...
```

`Get-EventLog`Cmdlet은 **LogName** 매개 변수를 사용 하 여 시스템 이벤트 로그를 지정 합니다. **최신** 매개 변수는 최근 5 개의 이벤트를 반환 합니다.

### 예 3: 이벤트 로그의 특정 항목 수에 대 한 모든 소스 찾기

이 예제에서는 시스템 이벤트 로그에서 가장 최근 1000 항목에 포함 된 모든 원본을 찾는 방법을 보여 줍니다.

```powershell
$Events = Get-EventLog -LogName System -Newest 1000
$Events | Group-Object -Property Source -NoElement | Sort-Object -Property Count -Descending
```

```Output
Count   Name
-----   ----
  110   DCOM
   65   Service Control Manager
   51   Microsoft-Windows-Kern...
   14   EventLog
   14   BTHUSB
   13   Win32k
```

`Get-EventLog`Cmdlet은 **LogName** 매개 변수를 사용 하 여 시스템 로그를 지정 합니다. **최신** 매개 변수는 1000 최신 이벤트를 선택 합니다. 이벤트 개체는 변수에 저장 됩니다 `$Events` . `$Events`개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Group-Object` .
`Group-Object`**Property** 매개 변수를 사용 하 여 개체를 원본 별로 그룹화 하 고 각 원본에 대 한 개체 수를 계산 합니다. **Noelement** 매개 변수는 출력에서 그룹 멤버를 제거 합니다.
이 `Sort-Object` cmdlet은 **Property** 매개 변수를 사용 하 여 각 소스 이름의 수를 기준으로 정렬 합니다.
**내림차순** 매개 변수는 목록을 순서 대로 오름차순으로 정렬 합니다.

### 예 4: 특정 이벤트 로그에서 오류 이벤트 가져오기

이 예제에서는 시스템 이벤트 로그에서 오류 이벤트를 가져옵니다.

```powershell
Get-EventLog -LogName System -EntryType Error
```

```Output
Index Time          EntryType   Source  InstanceID Message
----- ----          ---------   ------  ---------- -------
13296 Jan 16 13:53  Error       DCOM    10016 The description for Event ID '10016' in Source...
13291 Jan 16 13:51  Error       DCOM    10016 The description for Event ID '10016' in Source...
13245 Jan 16 11:45  Error       DCOM    10016 The description for Event ID '10016' in Source...
13230 Jan 16 11:07  Error       DCOM    10016 The description for Event ID '10016' in Source...
```

`Get-EventLog`Cmdlet은 **LogName** 매개 변수를 사용 하 여 시스템 로그를 지정 합니다. **Entrytype 관련이** 매개 변수는 이벤트를 필터링 하 여 오류 이벤트만 표시 합니다.

### 예 5: InstanceId 및 Source 값을 사용 하 여 이벤트 로그에서 이벤트 가져오기

이 예에서는 시스템 로그에서 특정 InstanceId 및 원본에 대 한 이벤트를 가져옵니다.

```powershell
Get-EventLog -LogName System -InstanceId 10016 -Source DCOM
```

```Output
Index Time          EntryType  Source  InstanceID  Message
----- ----          ---------  ------  ----------  -------
13245 Jan 16 11:45  Error      DCOM         10016  The description for Event ID '10016' in Source...
13230 Jan 16 11:07  Error      DCOM         10016  The description for Event ID '10016' in Source...
13219 Jan 16 10:00  Error      DCOM         10016  The description for Event ID '10016' in Source...
```

`Get-EventLog`Cmdlet은 **LogName** 매개 변수를 사용 하 여 시스템 로그를 지정 합니다. **InstanceID** 매개 변수는 지정 된 인스턴스 ID를 가진 이벤트를 선택 합니다. **Source** 매개 변수는 이벤트 속성을 지정 합니다.

### 예제 6: 여러 컴퓨터에서 이벤트 가져오기

이 명령은 Server01, Server02 및 Server03 컴퓨터의 시스템 이벤트 로그에서 이벤트를 가져옵니다.

```powershell
Get-EventLog -LogName System -ComputerName Server01, Server02, Server03
```

`Get-EventLog`Cmdlet은 **LogName** 매개 변수를 사용 하 여 시스템 로그를 지정 합니다. **ComputerName** 매개 변수는 쉼표로 구분 된 문자열을 사용 하 여 이벤트 로그를 가져오려는 컴퓨터를 나열 합니다.

### 예 7: 메시지에 특정 단어가 포함 된 모든 이벤트 가져오기

이 명령은 이벤트 메시지의 특정 단어가 포함 된 시스템 이벤트 로그의 모든 이벤트를 가져옵니다. 지정 된 **메시지** 매개 변수의 값이 메시지의 콘텐츠에 포함 되지만 PowerShell 콘솔에는 표시 되지 않을 수 있습니다.

```powershell
Get-EventLog -LogName System -Message *description*
```

```Output
Index Time          EntryType   Source       InstanceID   Message
----- ----          ---------   ------       ----------   -------
13821 Jan 17 19:17  Error       DCOM              10016   The description for Event ID '10016'...
13820 Jan 17 19:16  Error       DCOM              10016   The description for Event ID '10016'...
13819 Jan 17 19:08  Error       DCOM              10016   The description for Event ID '10016'...
```

`Get-EventLog`Cmdlet은 **LogName** 매개 변수를 사용 하 여 시스템 이벤트 로그를 지정 합니다. **메시지** 매개 변수는 각 이벤트의 메시지 필드에서 검색할 단어를 지정 합니다.

### 예 8: 이벤트의 속성 값 표시

이 예제에서는 이벤트의 모든 속성 및 값을 표시 하는 방법을 보여 줍니다.

```powershell
$A = Get-EventLog -LogName System -Newest 1
$A | Select-Object -Property *
```

```Output
EventID            : 10016
MachineName        : localhost
Data               : {}
Index              : 13821
Category           : (0)
CategoryNumber     : 0
EntryType          : Error
Message            : The description for Event ID '10016' in Source 'DCOM'...
Source             : DCOM
ReplacementStrings : {Local,...}
InstanceId         : 10016
TimeGenerated      : 1/17/2019 19:17:23
TimeWritten        : 1/17/2019 19:17:23
UserName           : username
Site               :
Container          :
```

`Get-EventLog`Cmdlet은 **LogName** 매개 변수를 사용 하 여 시스템 이벤트 로그를 지정 합니다. **최신** 매개 변수는 가장 최근 이벤트 개체를 선택 합니다. 개체는 변수에 저장 됩니다 `$A` . 변수의 개체는 `$A` 파이프라인에서 cmdlet으로 전송 됩니다 `Select-Object` .
`Select-Object` 별표 ()와 함께 **Property** 매개 변수를 사용 `*` 하 여 개체의 모든 속성을 선택 합니다.

### 예 9: 원본 및 이벤트 ID를 사용 하 여 이벤트 로그에서 이벤트 가져오기

이 예제에서는 지정 된 원본 및 이벤트 ID에 대 한 이벤트를 가져옵니다.

```powershell
Get-EventLog -LogName Application -Source Outlook | Where-Object {$_.EventID -eq 63} |
              Select-Object -Property Source, EventID, InstanceId, Message
```

```Output
Source   EventID   InstanceId   Message
------   -------   ----------   -------
Outlook       63   1073741887   The Exchange web service request succeeded.
Outlook       63   1073741887   Outlook detected a change notification.
Outlook       63   1073741887   The Exchange web service request succeeded.
```

`Get-EventLog`Cmdlet은 **LogName** 매개 변수를 사용 하 여 응용 프로그램 이벤트 로그를 지정 합니다. **원본** 매개 변수는 응용 프로그램 이름인 Outlook을 지정 합니다. 개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Where-Object` . Cmdlet은 파이프라인의 각 개체에 대해 `Where-Object` 변수를 사용 하 여 `$_.EventID` 이벤트 ID 속성을 지정 된 값과 비교 합니다. 개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Select-Object` . `Select-Object`**Property** 매개 변수를 사용 하 여 PowerShell 콘솔에 표시할 속성을 선택 합니다.

### 예제 10: 속성으로 이벤트 및 그룹 가져오기

```powershell
Get-EventLog -LogName System -UserName NT* | Group-Object -Property UserName -NoElement |
              Select-Object -Property Count, Name
```

```Output
Count  Name
-----  ----
6031   NT AUTHORITY\SYSTEM
  42   NT AUTHORITY\LOCAL SERVICE
   4   NT AUTHORITY\NETWORK SERVICE
```

`Get-EventLog`Cmdlet은 **LogName** 매개 변수를 사용 하 여 시스템 로그를 지정 합니다. **UserName** 매개 변수는 별표 ( `*` ) 와일드 카드를 포함 하 여 사용자 이름의 일부를 지정 합니다. 이벤트 개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Group-Object` . `Group-Object`**property** 매개 변수를 사용 하 **여 사용자 이름 속성을** 사용 하 여 개체를 그룹화 하 고 각 사용자 이름에 대 한 개체 수를 계산 하도록 지정 합니다. **Noelement** 매개 변수는 출력에서 그룹 멤버를 제거 합니다. 개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Select-Object` .
`Select-Object`**Property** 매개 변수를 사용 하 여 PowerShell 콘솔에 표시할 속성을 선택 합니다.

### 예 11: 특정 날짜 및 시간 범위 동안 발생 한 이벤트 가져오기

이 예에서는 지정 된 날짜 및 시간 범위에 대 한 시스템 이벤트 로그에서 오류 이벤트를 가져옵니다. **Before** 및 **After** 매개 변수는 날짜 및 시간 범위를 설정 하지만 출력에서 제외 됩니다.

```powershell
$Begin = Get-Date -Date '1/17/2019 08:00:00'
$End = Get-Date -Date '1/17/2019 17:00:00'
Get-EventLog -LogName System -EntryType Error -After $Begin -Before $End
```

```Output
Index Time          EntryType   Source   InstanceID  Message
----- ----          ---------   ------   ----------  -------
13821 Jan 17 13:40  Error       DCOM          10016  The description for Event ID...
13820 Jan 17 13:11  Error       DCOM          10016  The description for Event ID...
...
12372 Jan 17 10:08  Error       DCOM          10016  The description for Event ID...
12371 Jan 17 09:04  Error       DCOM          10016  The description for Event ID...
```

이 `Get-Date` cmdlet은 **date** 매개 변수를 사용 하 여 날짜 및 시간을 지정 합니다. **DateTime** 개체는 및 변수에 저장 됩니다 `$Begin` `$End` . `Get-EventLog`Cmdlet은 **LogName** 매개 변수를 사용 하 여 시스템 로그를 지정 합니다. **Entrytype 관련이** 매개 변수는 Error 이벤트 유형을 지정 합니다. 날짜 및 시간 범위는 **이후** 매개 변수 및 `$Begin` 변수와 **Before** 매개 변수 및 변수에 의해 설정 됩니다 `$End` .

## PARAMETERS

### -이후

지정 된 날짜 및 시간 이후에 발생 한 이벤트를 가져옵니다. **이후** 매개 변수 날짜 및 시간이 출력에서 제외 됩니다. Cmdlet에서 반환 되는 값과 같은 **DateTime** 개체를 입력 합니다 `Get-Date` .

```yaml
Type: System.DateTime
Parameter Sets: LogName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AsBaseObject

이 cmdlet이 각 이벤트에 대 한 표준 **EventLogEntry** 개체를 반환 함을 나타냅니다. 이 매개 변수가 없으면는 `Get-EventLog` 추가 **eventlogname** , **Source** 및 **InstanceId** 속성이 있는 확장 된 **PSObject** 개체를 반환 합니다.

이 매개 변수의 효과를 확인 하려면 이벤트를 cmdlet으로 파이프 하 `Get-Member` 고 결과의 **TypeName** 값을 검사 합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LogName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AsString

이 cmdlet은 개체가 아닌 문자열로 출력을 반환 함을 나타냅니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: List
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -이전

지정 된 날짜 및 시간 이전에 발생 한 이벤트를 가져옵니다. 매개 **변수** 날짜 및 시간이 출력에서 제외 됩니다. Cmdlet에서 반환 되는 값과 같은 **DateTime** 개체를 입력 합니다 `Get-Date` .

```yaml
Type: System.DateTime
Parameter Sets: LogName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

이 매개 변수는 원격 컴퓨터의 NetBIOS 이름, IP (인터넷 프로토콜) 주소 또는 FQDN (정규화 된 도메인 이름)을 지정 합니다.

**ComputerName** 매개 변수가 지정 되지 않은 경우 `Get-EventLog` 기본값은 로컬 컴퓨터입니다. 또한 매개 변수는 점 ()을 허용 `.` 하 여 로컬 컴퓨터를 지정 합니다.

**ComputerName** 매개 변수는 Windows PowerShell 원격을 사용 하지 않습니다. `Get-EventLog`컴퓨터에서 원격 명령을 실행 하도록 구성 되지 않은 경우에도 **ComputerName** 매개 변수와 함께를 사용할 수 있습니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Cn

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Entrytype 관련이

이 cmdlet이 가져오는 이벤트의 항목 형식을 문자열 배열로 지정 합니다.

이 매개 변수에 허용되는 값은 다음과 같습니다.

- 오류
- 정보
- FailureAudit
- SuccessAudit
- 경고

```yaml
Type: System.String[]
Parameter Sets: LogName
Aliases: ET
Accepted values: Error, Information, FailureAudit, SuccessAudit, Warning

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -인덱스

이벤트 로그에서 가져올 인덱스 값을 지정 합니다. 매개 변수는 쉼표로 구분 된 값 문자열을 허용 합니다.

```yaml
Type: System.Int32[]
Parameter Sets: LogName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InstanceId

이벤트 로그에서 가져올 인스턴스 Id를 지정 합니다. 매개 변수는 쉼표로 구분 된 값 문자열을 허용 합니다.

```yaml
Type: System.Int64[]
Parameter Sets: LogName
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -목록

컴퓨터에 있는 이벤트 로그 목록을 표시 합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: List
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LogName

하나의 이벤트 로그 이름을 지정 합니다. 로그 이름을 찾으려면를 사용 `Get-EventLog -List` 합니다. 와일드카드 문자를 사용할 수 있습니다. 이 매개 변수는 필수적 요소입니다.

```yaml
Type: System.String
Parameter Sets: LogName
Aliases: LN

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -메시지

이벤트 메시지의 문자열을 지정 합니다. 이 매개 변수를 사용 하 여 특정 단어나 구가 포함 된 메시지를 검색할 수 있습니다. 와일드카드가 지원됩니다.

```yaml
Type: System.String
Parameter Sets: LogName
Aliases: MSG

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -최신

최신 이벤트로 시작 하 고 지정 된 수의 이벤트를 가져옵니다. 예를 들어 이벤트 수가 필요 `-Newest 100` 합니다. 반환 되는 최대 이벤트 수를 지정 합니다.

```yaml
Type: System.Int32
Parameter Sets: LogName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Source

이 cmdlet이 가져오는 로그에 기록 된 원본 (문자열 배열)을 지정 합니다. 와일드카드가 지원됩니다.

```yaml
Type: System.String[]
Parameter Sets: LogName
Aliases: ABO

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -UserName

이벤트와 연결 된 사용자 이름을 문자열 배열로 지정 합니다. 이름 또는 이름 패턴 (예:, 또는)을 입력 `User01` `User*` `Domain01\User*` 합니다. 와일드카드가 지원됩니다.

```yaml
Type: System.String[]
Parameter Sets: LogName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### 없음

입력을로 파이프 할 수 없습니다 `Get-EventLog` .

## 출력

### EventLogEntry. System.web. EventLog. System.String

**LogName** 매개 변수가 지정 된 경우 출력은 **EventLogEntry** 개체의 컬렉션입니다.

**List** 매개 변수만 지정 된 경우 출력은 **system.web** 개체의 컬렉션입니다.

**List** 및 **asstring** 매개 변수를 모두 지정 하는 경우 출력은 **system.string** 개체의 컬렉션입니다.

## 참고

Cmdlet `Get-EventLog` 및는 `Get-WinEvent` Windows 사전 설치 환경 (Windows PE)에서 지원 되지 않습니다.

## 관련 링크

[Clear-EventLog](Clear-EventLog.md)

[Get-WinEvent](../Microsoft.PowerShell.Diagnostics/Get-WinEvent.md)

[Group-Object](../Microsoft.PowerShell.Utility/Group-Object.md)

[Limit-EventLog](Limit-EventLog.md)

[New-EventLog](New-EventLog.md)

[Remove-EventLog](Remove-EventLog.md)

[Select-Object](../Microsoft.PowerShell.Utility/Select-Object.md)

[Show-EventLog](Show-EventLog.md)

[Write-EventLog](Write-EventLog.md)
