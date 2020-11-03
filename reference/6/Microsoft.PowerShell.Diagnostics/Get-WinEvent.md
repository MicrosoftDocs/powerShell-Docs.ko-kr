---
external help file: Microsoft.PowerShell.Commands.Diagnostics.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Diagnostics
ms.date: 11/20/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.diagnostics/get-winevent?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-WinEvent
ms.openlocfilehash: 72455745d4523a33cac4ccca5af9c8be29ac9e37
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93217114"
---
# Get-WinEvent

## 개요
로컬 및 원격 컴퓨터의 이벤트 로그 및 이벤트 추적 로그 파일에서 이벤트를 가져옵니다.

## SYNTAX

### GetLogSet (기본값)

```
Get-WinEvent [[-LogName] <String[]>] [-MaxEvents <Int64>] [-ComputerName <String>]
 [-Credential <PSCredential>] [-FilterXPath <String>] [-Force] [-Oldest] [<CommonParameters>]
```

### ListLogSet

```
Get-WinEvent [-ListLog] <String[]> [-ComputerName <String>] [-Credential <PSCredential>] [-Force]
 [<CommonParameters>]
```

### ListProviderSet

```
Get-WinEvent [-ListProvider] <String[]> [-ComputerName <String>] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### GetProviderSet

```
Get-WinEvent [-ProviderName] <String[]> [-MaxEvents <Int64>] [-ComputerName <String>]
 [-Credential <PSCredential>] [-FilterXPath <String>] [-Force] [-Oldest] [<CommonParameters>]
```

### FileSet

```
Get-WinEvent [-Path] <String[]> [-MaxEvents <Int64>] [-Credential <PSCredential>]
 [-FilterXPath <String>] [-Oldest] [<CommonParameters>]
```

### HashQuerySet

```
Get-WinEvent [-MaxEvents <Int64>] [-ComputerName <String>] [-Credential <PSCredential>]
 [-FilterHashtable] <Hashtable[]> [-Force] [-Oldest] [<CommonParameters>]
```

### XmlQuerySet

```
Get-WinEvent [-MaxEvents <Int64>] [-ComputerName <String>] [-Credential <PSCredential>]
 [-FilterXml] <XmlDocument> [-Oldest] [<CommonParameters>]
```

## 설명

`Get-WinEvent`Cmdlet은 **시스템** 및 **응용 프로그램** 로그와 같은 클래식 로그를 비롯 하 여 이벤트 로그에서 이벤트를 가져옵니다. Cmdlet은 Windows Vista에 도입 된 Windows 이벤트 로그 기술에 의해 생성 되는 이벤트 로그에서 데이터를 가져옵니다. 및는 **ETW(Windows용 이벤트 추적) (ETW)** 에서 생성 된 로그 파일의 이벤트입니다. 기본적으로는 `Get-WinEvent` 가장 오래 된 순으로 이벤트 정보를 반환 합니다.

`Get-WinEvent` 이벤트 로그 및 이벤트 로그 공급자를 나열 합니다. 명령을 중단 하려면 <kbd>ctrl</kbd> + <kbd>C</kbd>를 누릅니다. 선택한 로그나 선택한 이벤트 공급자를 통해 생성된 로그에서 이벤트를 가져올 수 있습니다. 하나의 명령에 여러 원본의 이벤트를 결합할 수도 있습니다.
`Get-WinEvent` XPath 쿼리, 구조화 된 XML 쿼리 및 해시 테이블 쿼리를 사용 하 여 이벤트를 필터링 할 수 있습니다.

관리자 권한으로 PowerShell을 실행 하 고 있지 않은 경우 로그에 대 한 정보를 검색할 수 없다는 오류 메시지가 표시 될 수 있습니다.

## 예제

### 예 1: 로컬 컴퓨터에서 모든 로그 가져오기

이 명령은 로컬 컴퓨터에 있는 모든 이벤트 로그를 가져옵니다. 로그는 해당 로그를 가져오는 순서로 나열 됩니다 `Get-WinEvent` . 클래식 로그가 먼저 검색 된 다음 새 Windows 이벤트 로그가 검색 됩니다.
로그의 **RecordCount** 가 null 이거나 비어 있거나 0 일 수 있습니다.

```powershell
Get-WinEvent -ListLog *
```

```Output
LogMode   MaximumSizeInBytes RecordCount LogName
-------   ------------------ ----------- -------
Circular            15532032       14500 Application
Circular             1052672         117 Azure Information Protection
Circular             1052672        3015 CxAudioSvcLog
Circular            20971520             ForwardedEvents
Circular            20971520           0 HardwareEvents
```

`Get-WinEvent`Cmdlet은 컴퓨터에서 로그 정보를 가져옵니다. **Listlog** 매개 변수는 별표 ( `*` ) 와일드 카드를 사용 하 여 각 로그에 대 한 정보를 표시 합니다.

### 예 2: 클래식 설치 로그 가져오기

이 명령은 클래식 **설치** 로그를 나타내는 **EventLogConfiguration** 개체를 가져옵니다. 개체에는 로그에 대 한 정보 (예: 파일 크기, 공급자, 파일 경로 및 로그 사용 여부)가 포함 됩니다.

```powershell
Get-WinEvent -ListLog Setup | Format-List -Property *
```

```Output
FileSize                       : 69632
IsLogFull                      : False
LastAccessTime                 : 3/13/2019 09:41:46
LastWriteTime                  : 3/13/2019 09:41:46
OldestRecordNumber             : 1
RecordCount                    : 23
LogName                        : Setup
LogType                        : Operational
LogIsolation                   : Application
IsEnabled                      : True
IsClassicLog                   : False
SecurityDescriptor             : O:BAG:SYD: ...
LogFilePath                    : %SystemRoot%\System32\Winevt\Logs\Setup.evtx
MaximumSizeInBytes             : 1052672
LogMode                        : Circular
OwningProviderName             : Microsoft-Windows-Eventlog
ProviderNames                  : {Microsoft-Windows-WUSA, Microsoft-Windows-ActionQueue...
ProviderLevel                  :
ProviderKeywords               :
ProviderBufferSize             : 64
ProviderMinimumNumberOfBuffers : 0
ProviderMaximumNumberOfBuffers : 64
ProviderLatency                : 1000
ProviderControlGuid            :
```

`Get-WinEvent`Cmdlet은 **listlog** 매개 변수를 사용 하 여 **설치** 로그를 지정 합니다. 개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Format-List` . `Format-List` 별표 () 와일드 카드와 함께 **property** 매개 변수를 사용 하 여 `*` 각 속성을 표시 합니다.

### 예 3: 서버에서 이벤트 로그 가져오기

이 명령은 이벤트를 포함 하는 로컬 컴퓨터의 이벤트 로그만 가져옵니다. 로그의 **RecordCount** 는 null 또는 0 일 수 있습니다. 이 예에서는 변수를 사용 합니다 `$_` . 자세한 내용은 [about_Automatic_Variables](../Microsoft.PowerShell.Core/about/about_automatic_variables.md)를 참조 하세요.

```powershell
Get-WinEvent -ListLog * -ComputerName localhost | Where-Object { $_.RecordCount }
```

```Output
LogMode   MaximumSizeInBytes RecordCount LogName
-------   ------------------ ----------- -------
Circular            15532032       14546 Application
Circular             1052672         117 Azure Information Protection
Circular             1052672        2990 CxAudioSvcLog
Circular             1052672           9 MSFTVPN Setup
Circular             1052672         282 OAlerts
```

`Get-WinEvent`Cmdlet은 컴퓨터에서 로그 정보를 가져옵니다. **Listlog** 매개 변수는 별표 ( `*` ) 와일드 카드를 사용 하 여 각 로그에 대 한 정보를 표시 합니다. **ComputerName** 매개 변수는 로컬 컴퓨터 **localhost** 에서 로그를 가져오도록 지정 합니다. 개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Where-Object` . `Where-Object` 는 `$_.RecordCount` 를 사용 하 여 데이터가 포함 된 로그만 반환 합니다. `$_` 파이프라인의 현재 개체를 나타내는 변수입니다. **RecordCount** 는 null이 아닌 값을 가진 개체의 속성입니다.

### 예 4: 여러 서버에서 이벤트 로그 가져오기

이 예제에서는 Server01, Server02 및 Server03의 세 컴퓨터에서 **응용 프로그램** 이벤트 로그를 나타내는 개체를 가져옵니다. **ComputerName** 매개 변수는 하나의 값만 허용 하므로 **ForEach** 키워드가 사용 됩니다. 자세한 내용은 [about_Foreach](../Microsoft.PowerShell.Core/about/about_Foreach.md)를 참조 하세요.

```powershell
$S = 'Server01', 'Server02', 'Server03'
ForEach ($Server in $S) {
  Get-WinEvent -ListLog Application -ComputerName $Server |
    Select-Object LogMode, MaximumSizeInBytes, RecordCount, LogName,
      @{name='ComputerName'; expression={$Server}} |
    Format-Table -AutoSize
}
```

```Output
 LogMode MaximumSizeInBytes RecordCount LogName     ComputerName
 ------- ------------------ ----------- -------     ------------
Circular           15532032       14577 Application Server01
Circular           15532032        9689 Application Server02
Circular           15532032        5309 Application Server03
```

변수는 `$S` 세 개의 서버 ( **Server01** , **Server02** 및 **Server03** )를 저장 합니다. **ForEach** 문은 루프를 사용 하 여 각 서버를 처리 `($Server in $S)` 합니다. 중괄호 ()의 스크립트 블록은 `{ }` 명령을 실행 합니다 `Get-WinEvent` . **Listlog** 매개 변수는 **응용 프로그램** 로그를 지정 합니다. **ComputerName** 매개 변수는 변수를 사용 하 여 `$Server` 각 서버에서 로그 정보를 가져옵니다.

개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Select-Object` . `Select-Object`**Logmode** , **maximumsizeinbytes** , **RecordCount** , **LogName** 속성을 가져오고 변수를 사용 하 여 **ComputerName** 을 표시 하는 계산 식을 사용 합니다 `$Server` . 개체는 파이프라인에서 cmdlet으로 전송 되어 `Format-Table` PowerShell 콘솔에 출력을 표시 합니다. **AutoSize** 매개 변수는 화면에 맞게 출력의 서식을 지정 합니다.

### 예 5: 이벤트 로그 공급자 및 로그 이름 가져오기

이 명령은 이벤트 로그 공급자와 해당 공급자가 작성 하는 로그를 가져옵니다.

```powershell
Get-WinEvent -ListProvider *
```

```Output
Name     : .NET Runtime
LogLinks : {Application}
Opcodes  : {}
Tasks    : {}

Name     : .NET Runtime Optimization Service
LogLinks : {Application}
Opcodes  : {}
Tasks    : {}
```

`Get-WinEvent`Cmdlet은 컴퓨터에서 로그 정보를 가져옵니다. **Listprovider** 매개 변수는 별표 () 와일드 카드를 사용 하 여 `*` 각 공급자에 대 한 정보를 표시 합니다. 출력에서 **이름은** 공급자 이며 **loglinks** 는 공급자가 기록 하는 로그입니다.

### 예 6: 특정 로그에 쓰는 모든 이벤트 로그 공급자 가져오기

이 명령은 **응용 프로그램** 로그에 기록 하는 모든 공급자를 가져옵니다.

```powershell
(Get-WinEvent -ListLog Application).ProviderNames
```

```Output
.NET Runtime
.NET Runtime Optimization Service
Application
Application Error
Application Hang
Application Management
```

`Get-WinEvent`Cmdlet은 컴퓨터에서 로그 정보를 가져옵니다. **Listlog** 매개 변수는 **응용 프로그램** 을 사용 하 여 해당 로그에 대 한 개체를 가져옵니다. **Providernames** 는 개체의 속성 이며 **응용 프로그램** 로그에 기록 하는 공급자를 표시 합니다.

### 예 7: 특정 문자열이 포함 된 이벤트 로그 공급자 이름 가져오기

이 명령은 공급자 이름에 특정 문자열을 포함 하는 이름의 이벤트 로그 공급자를 가져옵니다.

```powershell
Get-WinEvent -ListProvider *Policy*
```

```Output
Name     : Group Policy Applications
LogLinks : {Application}
Opcodes  : {}
Tasks    : {}

Name     : Group Policy Client
LogLinks : {Application}
Opcodes  : {}
Tasks    : {}

Name     : Group Policy Data Sources
LogLinks : {Application}
Opcodes  : {}
Tasks    : {}
```

`Get-WinEvent`Cmdlet은 컴퓨터에서 로그 정보를 가져옵니다. **Listprovider** 매개 변수는 별표 ( `*` ) 와일드 카드를 사용 하 여 공급자 이름 내에서 **정책을** 찾습니다.

### 예 8: 이벤트 공급자가 생성 하는 이벤트 Id 가져오기

이 명령은 **Microsoft Windows-GroupPolicy** 이벤트 공급자가 이벤트 설명과 함께 생성 하는 이벤트 id를 나열 합니다.

```powershell
(Get-WinEvent -ListProvider Microsoft-Windows-GroupPolicy).Events | Format-Table Id, Description
```

```Output
  Id  Description
  --  -----------
1500  The Group Policy settings for the computer were processed successfully...
1501  The Group Policy settings for the user were processed successfully...
4115  Group Policy Service started.
4116  Started the Group Policy service initialization phase.
4117  Group Policy Session started.
```

`Get-WinEvent`Cmdlet은 컴퓨터에서 로그 정보를 가져옵니다. **Listprovider** 매개 변수는 공급자 ( **Microsoft-Windows-grouppolicy)** 를 지정 합니다. 식은 괄호로 래핑되고 **Events** 속성을 사용 하 여 개체를 가져옵니다. 개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Format-Table` . `Format-Table` 이벤트 개체의 **Id** 및 **설명을** 표시 합니다.

### 예 9: 이벤트 개체 속성에서 로그 정보 가져오기

이 예제에서는 이벤트 개체 속성을 사용 하 여 로그 내용에 대 한 정보를 가져오는 방법을 보여 줍니다.
이벤트 개체는 변수에 저장 된 다음 **이벤트 Id** 및 **수준** 에 따라 그룹화 되 고 계산 됩니다.

```powershell
$Event = Get-WinEvent -LogName 'Windows PowerShell'
$Event.Count
$Event | Group-Object -Property Id -NoElement | Sort-Object -Property Count -Descending
$Event | Group-Object -Property LevelDisplayName -NoElement
```

```Output
195

Count  Name
-----  ----
  147  600
   22  400
   21  601
    3  403
    2  103

Count  Name
-----  ----
    2  Warning
  193  Information
```

`Get-WinEvent`Cmdlet은 **LogName** 매개 변수를 사용 하 여 **Windows PowerShell** 이벤트 로그를 지정 합니다. 이벤트 개체는 변수에 저장 됩니다 `$Event` . 의 **Count** 속성은 `$Event` 로깅된 이벤트의 총 수를 표시 합니다.

`$Event`변수가 파이프라인에서 cmdlet으로 전송 됩니다 `Group-Object` . `Group-Object`**property** 매개 변수를 사용 하 여 **Id** 속성을 지정 하 고 이벤트 id 값을 기준으로 개체의 수를 계산 합니다. **Noelement** 매개 변수는 개체 출력에서 다른 속성을 제거 합니다. 그룹화 된 개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Sort-Object` . `Sort-Object`**Property** 매개 변수를 사용 하 여 **개수** 를 기준으로 개체를 정렬 합니다. **내림차순** 매개 변수는 결과를 최고에서 최저 순으로 계산 하 여 표시 합니다. 출력에서 **Count** 열은 각 이벤트의 총 수를 포함 합니다. **이름** 열에는 그룹화 된 이벤트 Id 번호가 포함 됩니다.

`$Event`변수가 파이프라인에서 cmdlet으로 전송 됩니다 `Group-Object` . `Group-Object`**property** 매개 변수를 사용 하 여 **leveldisplayname** 속성을 지정 하 고 개체의 수를 **leveldisplayname** 으로 계산 합니다. 개체는 **경고** 및 **정보와** 같은 수준에 따라 그룹화 됩니다.
**Noelement** 매개 변수는 출력에서 다른 속성을 제거 합니다. 출력에서 **Count** 열은 각 이벤트의 총 수를 포함 합니다. **이름** 열에는 그룹화 된 **leveldisplayname** 이 포함 됩니다.

### 예 10: 이름에 지정 된 문자열이 있는 오류 이벤트 가져오기

이 예에서는 쉼표로 구분 된 로그 이름 문자열을 사용 합니다. 출력은 오류, 경고 및 로그 이름과 같은 수준에 따라 그룹화 됩니다.

```powershell
Get-WinEvent -LogName *PowerShell*, Microsoft-Windows-Kernel-WHEA* |
  Group-Object -Property LevelDisplayName, LogName -NoElement |
    Format-Table -AutoSize
```

```Output
Count  Name
-----  ----
    1  Error, PowerShellCore/Operational
   26  Information, Microsoft-Windows-Kernel-WHEA/Operational
  488  Information, Microsoft-Windows-PowerShell/Operational
   77  Information, PowerShellCore/Operational
 9835  Information, Windows PowerShell
   19  Verbose, PowerShellCore/Operational
  444  Warning, Microsoft-Windows-PowerShell/Operational
  512  Warning, PowerShellCore/Operational
```

`Get-WinEvent`Cmdlet은 컴퓨터에서 로그 정보를 가져옵니다. **LogName** 매개 변수는 별표 () 와일드 카드와 함께 쉼표로 구분 된 문자열을 사용 하 여 `*` 로그 이름을 지정 합니다. 개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Group-Object` . `Group-Object`**Property** 매개 변수를 사용 하 여 **Leveldisplayname** 및 **LogName** 을 기준으로 개체를 그룹화 합니다. **Noelement** 매개 변수는 출력에서 다른 속성을 제거 합니다. 그룹화 된 개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Format-Table` . `Format-Table`**AutoSize** 매개 변수를 사용 하 여 열의 서식을 지정 합니다. **Count** 열에는 각 이벤트의 총 수가 포함 됩니다. **이름** 열에는 그룹화 된 **Leveldisplayname** 및 **LogName** 이 포함 됩니다.

### 예 11: 보관 된 이벤트 로그에서 이벤트 가져오기

`Get-WinEvent` 저장 된 로그 파일에서 이벤트 정보를 가져올 수 있습니다. 이 샘플에서는 로컬 컴퓨터에 저장 된 보관 된 PowerShell 로그를 사용 합니다.

```powershell
Get-WinEvent -Path 'C:\Test\Windows PowerShell.evtx'
```

```Output
   ProviderName: PowerShell

TimeCreated              Id LevelDisplayName  Message
-----------              -- ----------------  -------
3/15/2019 13:54:13      403 Information       Engine state is changed from Available to Stopped...
3/15/2019 13:54:13      400 Information       Engine state is changed from None to Available...
3/15/2019 13:54:13      600 Information       Provider "Variable" is Started...
3/15/2019 13:54:13      600 Information       Provider "Function" is Started...
3/15/2019 13:54:13      600 Information       Provider "FileSystem" is Started...
```

`Get-WinEvent`Cmdlet은 컴퓨터에서 로그 정보를 가져옵니다. **Path** 매개 변수는 디렉터리와 파일 이름을 지정 합니다.

### 예 12: 보관 된 이벤트 로그에서 특정 이벤트 수 가져오기

이러한 명령은 보관 된 이벤트 로그에서 특정 수의 이벤트를 가져옵니다. `Get-WinEvent` 에는 최대 이벤트 수 또는 가장 오래 된 이벤트를 가져올 수 있는 매개 변수가 있습니다. 이 샘플에서는 **C:\Test\PowerShellCore** 에 저장 된 보관 된 PowerShell 로그를 사용 합니다.

```powershell
Get-WinEvent -Path 'C:\Test\PowerShellCore Operational.evtx' -MaxEvents 100
```

```Output
   ProviderName: PowerShellCore

TimeCreated                 Id   LevelDisplayName  Message
-----------                 --   ----------------  -------
3/15/2019 09:54:54        4104   Warning           Creating Scriptblock text (1 of 1):...
3/15/2019 09:37:13       40962   Information       PowerShell console is ready for user input
3/15/2019 07:56:24        4104   Warning           Creating Scriptblock text (1 of 1):...
...
3/7/2019 10:53:22        40961   Information       PowerShell console is starting up
3/7/2019 10:53:22         8197   Verbose           Runspace state changed to Opening
3/7/2019 10:53:22         8195   Verbose           Opening RunspacePool
```

`Get-WinEvent`Cmdlet은 컴퓨터에서 로그 정보를 가져옵니다. **Path** 매개 변수는 디렉터리와 파일 이름을 지정 합니다. **Maxevents** 매개 변수는 100 레코드가 최신에서 가장 오래 된 것으로 표시 되도록 지정 합니다.

### 예 13: ETW(Windows용 이벤트 추적)

ETW (ETW(Windows용 이벤트 추적))는 이벤트 발생 시 로그에 이벤트를 기록 합니다. 이벤트는 가장 오래 된 순서로 저장 됩니다. 보관 된 ETW 파일은 `.etl` **tracelog** 와 같은로 저장 됩니다.
이벤트는 로그에 기록 되는 순서 대로 나열 되므로 *가장 오래* 된 매개 변수가 필요 합니다.

```powershell
Get-WinEvent -Path 'C:\Tracing\TraceLog.etl' -Oldest |
  Sort-Object -Property TimeCreated -Descending |
    Select-Object -First 100
```

`Get-WinEvent`Cmdlet은 보관 된 파일에서 로그 정보를 가져옵니다. **Path** 매개 변수는 디렉터리와 파일 이름을 지정 합니다. **가장 오래** 된 매개 변수는 기록 된 순서 대로 이벤트를 출력 하는 데 사용 됩니다. 개체는 파이프라인에서 cmdlet으로 전송 되며, `Sort-Object` `Sort-Object` **TimeCreated** 속성 값을 기준으로 내림차순으로 개체를 정렬 합니다. 개체는 `Select-Object` 100 최신 이벤트를 표시 하는 cmdlet에 파이프라인으로 전송 됩니다.

### 예제 14: 이벤트 추적 로그에서 이벤트 가져오기

이 예제에서는 이벤트 추적 로그 파일 ( `.etl` ) 및 보관 된 Windows PowerShell 로그 파일 ()에서 이벤트를 가져오는 방법을 보여 줍니다 `.evtx` . 단일 명령으로 여러 파일 유형을 결합할 수 있습니다.
이 파일에는 동일한 형식의 **.NET Framework** 개체 **EventLogRecord** 이 포함 되어 있으므로 동일한 속성을 사용 하 여 파일을 필터링 할 수 있습니다. 명령에는 파일에서 읽기는 **가장 오래** 된 매개 변수가 필요 하지만 가장 오래 된 매개 변수는 `.etl` 각 파일에 적용 됩니다. **Oldest**

```powershell
Get-WinEvent -Path 'C:\Tracing\TraceLog.etl', 'C:\Test\Windows PowerShell.evtx' -Oldest |
  Where-Object { $_.Id -eq '403' }
```

`Get-WinEvent`Cmdlet은 보관 된 파일에서 로그 정보를 가져옵니다. **Path** 매개 변수는 쉼표로 구분 된 목록을 사용 하 여 각 파일 디렉터리와 파일 이름을 지정 합니다. **가장 오래** 된 매개 변수는 기록 된 순서 대로 이벤트를 출력 하는 데 사용 됩니다. 개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Where-Object` . `Where-Object` 는 스크립트 블록을 사용 하 여 및 **Id가** **403** 인 이벤트를 찾습니다. `$_`변수는 파이프라인의 현재 개체를 나타내고 **Id** 는 이벤트 id 속성입니다.

### 예 15: 이벤트 로그 결과 필터링

이 예제에서는 이벤트 로그에서 이벤트를 필터링 하 고 선택 하는 다양 한 메서드를 보여 줍니다. 이러한 모든 명령은 **Windows PowerShell** 이벤트 로그에서 최근 24 시간 동안 발생 한 이벤트를 가져옵니다.
필터 메서드는 cmdlet을 사용 하는 것 보다 더 효율적 `Where-Object` 입니다. 필터가 개체를 검색할 때 적용 됩니다. `Where-Object` 모든 개체를 검색 한 다음 모든 개체에 필터를 적용 합니다.

```powershell
# Using the Where-Object cmdlet:
$Yesterday = (Get-Date) - (New-TimeSpan -Day 1)
Get-WinEvent -LogName 'Windows PowerShell' | Where-Object { $_.TimeCreated -ge $Yesterday }

# Using the FilterHashtable parameter:
$Yesterday = (Get-Date) - (New-TimeSpan -Day 1)
Get-WinEvent -FilterHashtable @{ LogName='Windows PowerShell'; Level=3; StartTime=$Yesterday }

# Using the FilterXML parameter:
$xmlQuery = @'
<QueryList>
  <Query Id="0" Path="Windows PowerShell">
    <Select Path="System">*[System[(Level=3) and
        TimeCreated[timediff(@SystemTime) &lt;= 86400000]]]</Select>
  </Query>
</QueryList>
'@
Get-WinEvent -FilterXML $xmlQuery

# Using the FilterXPath parameter:
$XPath = '*[System[Level=3 and TimeCreated[timediff(@SystemTime) &lt;= 86400000]]]'
Get-WinEvent -LogName 'Windows PowerShell' -FilterXPath $XPath
```

### 예 16: FilterHashtable을 사용 하 여 응용 프로그램 로그에서 이벤트 가져오기

이 예에서는 **Filterhashtable** 매개 변수를 사용 하 여 **응용 프로그램** 로그에서 이벤트를 가져옵니다. 해시 테이블은 **키/값** 쌍을 사용 합니다. **Filterhashtable** 매개 변수에 대 한 자세한 내용은 [filterhashtable를 사용 하 여 쿼리 Get-WinEvent 만들기](/powershell/scripting/samples/Creating-Get-WinEvent-queries-with-FilterHashtable)를 참조 하세요.
해시 테이블에 대한 자세한 내용은 [about_Hash_Tables](../Microsoft.PowerShell.Core/about/about_hash_tables.md)를 참조하세요.

```powershell
$Date = (Get-Date).AddDays(-2)
Get-WinEvent -FilterHashtable @{ LogName='Application'; StartTime=$Date; Id='1003' }
```

`Get-Date`이 cmdlet은 **AddDays** 메서드를 사용 하 여 현재 날짜 로부터 2 일 이전 날짜를 가져옵니다. Date 개체는 변수에 저장 됩니다 `$Date` .

`Get-WinEvent`Cmdlet은 로그 정보를 가져옵니다. **Filterhashtable** 매개 변수는 출력을 필터링 하는 데 사용 됩니다. **LogName** 키는 값을 **응용 프로그램** 로그로 지정 합니다. **StartTime** 키는 변수에 저장 된 값을 사용 합니다 `$Date` . **Id** 키에는 이벤트 id 값인 **1003** 이 사용 됩니다.

### 예제 17: FilterHashtable을 사용 하 여 응용 프로그램 오류 가져오기

이 예에서는 **Filterhashtable** 매개 변수를 사용 하 여 지난 주에 발생 한 Internet Explorer 응용 프로그램 오류를 찾습니다.

```powershell
$StartTime = (Get-Date).AddDays(-7)
Get-WinEvent -FilterHashtable @{
  Logname='Application'
  ProviderName='Application Error'
  Data='iexplore.exe'
  StartTime=$StartTime
}
```

`Get-Date`이 cmdlet은 **AddDays** 메서드를 사용 하 여 현재 날짜의 7 일 이전 날짜를 가져옵니다. Date 개체는 변수에 저장 됩니다 `$StartTime` .

`Get-WinEvent`Cmdlet은 로그 정보를 가져옵니다. **Filterhashtable** 매개 변수는 출력을 필터링 하는 데 사용 됩니다. **LogName** 키는 값을 **응용 프로그램** 로그로 지정 합니다. **ProviderName** 키에는 이벤트 **소스인** **응용 프로그램 오류** 값이 사용 됩니다. **데이터** 키는 값을 사용 합니다. **StartTime** 키는 변수에 저장 된 값을 사용 **iexplore.exe** 합니다 `$StartTime` .

### 예 18: SuppressHashFilter를 사용 하 여 응용 프로그램 오류 필터링

위의 예제 16과 같이이 예제에서는 **Filterhashtable** 매개 변수를 사용 하 여 **응용 프로그램** 로그에서 이벤트를 가져옵니다. 그러나 **SuppressHashFilter** 키를 추가 하 여 **정보** 수준 이벤트를 필터링 합니다.

```powershell
$Date = (Get-Date).AddDays(-2)
$filter = @{
  LogName='Application'
  StartTime=$Date
  SuppressHashFilter=@{Level=4}
}
Get-WinEvent -FilterHashtable $filter
```

이 예에서는 `Get-WinEvent` 4 (정보) **수준이** 있는 이벤트를 제외 하 고 지난 2 일간의 **응용 프로그램** 로그에서 모든 이벤트를 가져옵니다.

## PARAMETERS

### -ComputerName

이 cmdlet이 이벤트 로그에서 이벤트를 가져오는 컴퓨터의 이름을 지정 합니다. 컴퓨터의 NetBIOS 이름, IP 주소 또는 FQDN (정규화 된 도메인 이름)을 입력 합니다. 기본값은 로컬 컴퓨터 **localhost** 입니다. 이 매개 변수는 한 번에 하나의 컴퓨터 이름만 받습니다.

원격 컴퓨터에서 이벤트 로그를 가져오려면 원격 액세스를 허용 하도록 이벤트 로그 서비스에 대 한 방화벽 포트를 구성 합니다.

이 cmdlet은 PowerShell 원격을 사용 하지 않습니다. 원격 명령을 실행하도록 컴퓨터를 구성하지 않은 경우에도 **ComputerName** 매개 변수를 사용할 수 있습니다.

```yaml
Type: System.String
Parameter Sets: GetLogSet, ListLogSet, ListProviderSet, GetProviderSet, HashQuerySet, XmlQuerySet
Aliases: Cn

Required: False
Position: Named
Default value: Local computer
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential

이 작업을 수행할 권한이 있는 사용자 계정을 지정합니다. 기본값은 현재 사용자입니다.

**User01** 또는 **Domain01\User01** 과 같은 사용자 이름을 입력 합니다. 또는 cmdlet에 의해 생성 된 것과 같은 **PSCredential** 개체를 입력 합니다 `Get-Credential` . 사용자 이름을 입력 하면 암호를 입력 하 라는 메시지가 표시 됩니다. 매개 변수 이름만 입력 하면 사용자 이름 및 암호를 입력 하 라는 메시지가 표시 됩니다.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilterHashtable

하나 이상의 이벤트 로그에서 이벤트를 선택 하는 해시 테이블 형식의 쿼리를 지정 합니다. 쿼리에 하나 이상의 **키/값** 쌍이 있는 해시 테이블이 포함 되어 있습니다.

해시 테이블 쿼리의 규칙은 다음과 같습니다.

- 키와 값은 대/소문자를 구분 하지 않습니다.
- 와일드 카드 문자는 **LogName** 및 **ProviderName** 키와 연결 된 값에만 사용할 수 있습니다.
- 각 키는 각 해시 테이블에 한 번만 나열 될 수 있습니다.
- **경로** 값은 `.etl` , `.evt` 및 로그 파일에 대 한 경로를 사용 합니다 `.evtx` .
- 같은 쿼리에서는 **LogName** , **Path** 및 **ProviderName** 키를 사용할 수 있습니다.
- **UserID** 키는 올바른 SID (보안 식별자) 또는 올바른 system.web. n a m a. n a m **account 개체** 를 구성 하는 데 사용할 수 있는 도메인 계정 이름을 사용할 수 있습니다.
- **데이터** 값은 명명 되지 않은 필드에 이벤트 데이터를 사용 합니다. 예를 들어, 클래식 이벤트 로그의 이벤트입니다.
- `<named-data>` key는 명명 된 이벤트 데이터 필드를 나타냅니다.

에서 `Get-WinEvent` **키/값** 쌍을 해석할 수 없는 경우 키가 이벤트의 이벤트 데이터에 대 한 대/소문자를 구분 하는 이름으로 해석 됩니다.

유효한 `Get-WinEvent` **키/값** 쌍은 다음과 같습니다.

- **LogName**=`<String[]>`
- **ProviderName**=`<String[]>`
- **Path**=`<String[]>`
- **어**=`<Long[]>`
- **A-ID**=`<Int32[]>`
- **저수준**=`<Int32[]>`
- **StartTime**=`<DateTime>`
- **EndTime**=`<DateTime>`
- **Id**=`<SID>`
- **데이터로**=`<String[]>`
- `<named-data>`=`<String[]>`
- **SuppressHashFilter**=`<Hashtable>`

```yaml
Type: System.Collections.Hashtable[]
Parameter Sets: HashQuerySet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilterXml

이 cmdlet이 하나 이상의 이벤트 로그에서 이벤트를 선택 하는 구조화 된 XML 쿼리를 지정 합니다.

유효한 XML 쿼리를 생성 하려면 Windows의 **사용자 지정 뷰 만들기** 및 **현재 로그 기능 필터링** 이벤트 뷰어을 사용 합니다. 대화 상자의 항목을 사용하여 쿼리를 만든 다음 XML 탭을 클릭하여 XML 형식으로 쿼리를 봅니다. XML 탭의 XML을 **FilterXml** 매개 변수 값으로 복사할 수 있습니다. 이벤트 뷰어 기능에 대한 자세한 내용은 이벤트 뷰어 도움말을 참조하세요.

XML 쿼리를 사용 하 여 여러 XPath 문을 포함 하는 복잡 한 쿼리를 만듭니다. 또한 XML 형식을 사용 하면 쿼리에서 이벤트를 제외 하는 **표시 안 함 xml** 요소를 사용할 수 있습니다. 이벤트 로그 쿼리의 XML 스키마에 대 한 자세한 내용은 [이벤트 선택](/previous-versions/aa385231(v=vs.85))의 [쿼리 스키마](/windows/win32/wes/queryschema-schema) 및 xml 이벤트 쿼리 섹션을 참조 하십시오.

**Filterhashtable** 매개 변수를 사용 하 여 **표시 안 함** 요소를 만들 수도 있습니다.

```yaml
Type: System.Xml.XmlDocument
Parameter Sets: XmlQuerySet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilterXPath

이 cmdlet이 하나 이상의 로그에서 이벤트를 선택 하는 XPath 쿼리를 지정 합니다.

XPath 언어에 대 한 자세한 내용은 [이벤트 선택](/previous-versions/aa385231(v=vs.85))의 [Xpath 참조](/previous-versions/dotnet/netframework-4.0/ms256115(v=vs.100)) 및 선택 필터 섹션을 참조 하십시오.

```yaml
Type: System.String
Parameter Sets: GetLogSet, GetProviderSet, FileSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

다른 이벤트 로그와 함께 디버그 및 분석 로그를 가져옵니다. **Force** 매개 변수는 name 매개 변수 값에 와일드카드 문자가 포함된 경우 디버그 또는 분석 로그를 가져오는 데 필요합니다.

기본적으로 `Get-WinEvent` 이 cmdlet은 디버그 또는 분석 로그의 전체 이름을 지정 하지 않는 한 이러한 로그를 제외 합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GetLogSet, ListLogSet, GetProviderSet, HashQuerySet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ListLog

이벤트 로그를 지정합니다. 이벤트 로그 이름을 쉼표로 구분된 목록으로 입력합니다. 와일드카드가 지원됩니다. 모든 로그를 가져오려면 별표 ( `*` ) 와일드 카드를 사용 합니다.

```yaml
Type: System.String[]
Parameter Sets: ListLogSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -ListProvider

이 cmdlet이 가져오는 이벤트 로그 공급자를 지정 합니다. 이벤트 로그 공급자는 이벤트 로그에 이벤트를 기록하는 프로그램 또는 서비스이며

공급자 이름을 쉼표로 구분된 목록으로 입력합니다. 와일드카드가 지원됩니다. 컴퓨터에 있는 모든 이벤트 로그의 공급자를 가져오려면 별표 ( `*` ) 와일드 카드를 사용 합니다.

```yaml
Type: System.String[]
Parameter Sets: ListProviderSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -LogName

이 cmdlet이 이벤트를 가져올 이벤트 로그를 지정 합니다. 이벤트 로그 이름을 쉼표로 구분된 목록으로 입력합니다. 와일드카드가 지원됩니다. Cmdlet에 로그 이름을 파이프 할 수도 있습니다 `Get-WinEvent` .

> [!NOTE]
> PowerShell은 요청할 수 있는 로그의 양을 제한 하지 않습니다. 그러나 `Get-WinEvent` 이 cmdlet은 256의 제한이 있는 WINDOWS API를 쿼리 합니다. 이렇게 하면 한 번에 모든 로그를 필터링 하기 어려울 수 있습니다. 루프를 사용 하 여 `foreach` 다음과 같이 각 로그를 반복 하면이 문제를 해결할 수 있습니다. `Get-WinEvent -ListLog * | ForEach-Object{ Get-WinEvent -LogName $_.Logname }`

```yaml
Type: System.String[]
Parameter Sets: GetLogSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -MaxEvents

반환 되는 최대 이벤트 수를 지정 합니다. 100과 같은 정수를 입력 합니다. 기본값은 로그 또는 파일의 모든 이벤트를 반환하는 것입니다.

```yaml
Type: System.Int64
Parameter Sets: GetLogSet, GetProviderSet, FileSet, HashQuerySet, XmlQuerySet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -가장 오래 된

이 cmdlet이 가장 오래 된 순서로 이벤트를 가져오기 시작 함을 표시 합니다. 기본적으로 이벤트는 최신 것 먼저 순서로 반환됩니다.

이 매개 변수는 `.etl` 및 `.evt` 파일과 디버그 및 분석 로그에서 이벤트를 가져오는 데 필요 합니다. 이 파일에서 이벤트는 오래된 것 먼저 순서로 기록되며 오래된 것 먼저 순서로만 반환될 수 있습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GetLogSet, GetProviderSet, FileSet, HashQuerySet, XmlQuerySet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

이 cmdlet이 이벤트를 가져오는 이벤트 로그 파일의 경로를 지정 합니다. 로그 파일의 경로를 쉼표로 구분된 목록으로 입력하거나 와일드카드 문자를 사용하여 파일 경로 패턴을 만듭니다.

`Get-WinEvent` 는 `.evt` , `.evtx` 및 파일 이름 확장명을 가진 파일을 지원 `.etl` 합니다. 다양한 파일 및 파일 형식의 이벤트를 동일한 명령에 포함할 수 있습니다.

```yaml
Type: System.String[]
Parameter Sets: FileSet
Aliases: PSPath

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -ProviderName

이 cmdlet이 이벤트를 가져오는 이벤트 로그 공급자를 문자열 배열로 지정 합니다. 공급자 이름을 쉼표로 구분된 목록으로 입력하거나 와일드카드 문자를 사용하여 공급자 이름 패턴을 만듭니다.

이벤트 로그 공급자는 이벤트 로그에 이벤트를 기록하는 프로그램 또는 서비스이며 PowerShell 공급자가 아닙니다.

```yaml
Type: System.String[]
Parameter Sets: GetProviderSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.string, System.Xml.Xml문서, System.object

**LogName** (string), **filterxml** 쿼리 또는 **filterxml** 쿼리를에 파이프라인으로 지정할 수 있습니다 `Get-WinEvent` .

## 출력

### EventLogConfiguration, EventLogRecord,,. m a.. m a.. m a.

**Listlog** 매개 변수를 사용 하 여 `Get-WinEvent` **EventLogConfiguration** 개체를 반환 합니다.

**Listprovider** 매개 변수를 사용 하 여는 `Get-WinEvent` **system.object** 를 반환 합니다.

다른 모든 매개 변수를 사용 하 여 `Get-WinEvent` **EventLogRecord** 개체를 반환 합니다.

## 참고

`Get-WinEvent` 는 `Get-EventLog` Windows Vista 이상 버전의 windows를 실행 하는 컴퓨터에서 cmdlet을 대체 하도록 설계 되었습니다. `Get-EventLog` 클래식 이벤트 로그 에서만 이벤트를 가져옵니다. `Get-EventLog`는 이전 버전과의 호환성을 위해 유지됩니다.

`Get-WinEvent`및 cmdlet은 Windows `Get-EventLog` 사전 설치 환경 (windows PE)에서 지원 되지 않습니다.

## 관련 링크

[about_Automatic_Variables](../Microsoft.PowerShell.Core/about/about_automatic_variables.md)

[about_Foreach](../Microsoft.PowerShell.Core/about/about_Foreach.md)

[about_Hash_Tables](../Microsoft.PowerShell.Core/about/about_hash_tables.md)

[FilterHashtable를 사용하여 Get-WinEvent 쿼리 만들기](/powershell/scripting/samples/Creating-Get-WinEvent-queries-with-FilterHashtable)

[Format-Table](../Microsoft.PowerShell.Utility/Format-Table.md)

[Group-Object](../Microsoft.PowerShell.Utility/Group-Object.md)

[Sort-Object](../Microsoft.PowerShell.Utility/Sort-Object.md)

[Where-Object](../Microsoft.PowerShell.Core/Where-Object.md)
