---
external help file: Microsoft.PowerShell.Commands.Diagnostics.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Diagnostics
ms.date: 11/06/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.diagnostics/get-counter?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Counter
ms.openlocfilehash: b8b78c0a2dec0c3e51c91df522cc5b026952a222
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93217618"
---
# Get-Counter

## 개요
로컬 및 원격 컴퓨터에서 성능 카운터 데이터를 가져옵니다.

## SYNTAX

### GetCounterSet (기본값)

```
Get-Counter [[-Counter] <String[]>] [-SampleInterval <Int32>] [-MaxSamples <Int64>] [-Continuous]
 [-ComputerName <String[]>] [<CommonParameters>]
```

### ListSetSet

```
Get-Counter [-ListSet] <String[]> [-ComputerName <String[]>] [<CommonParameters>]
```

## 설명

`Get-Counter`Cmdlet은 Windows 운영 체제 제품군의 성능 모니터링 계측에서 직접 성능 카운터 데이터를 가져옵니다. `Get-Counter` 로컬 컴퓨터 또는 원격 컴퓨터에서 성능 데이터를 가져옵니다.

매개 변수를 사용 `Get-Counter` 하 여 하나 이상의 컴퓨터를 지정 하 고, 성능 카운터 집합과 여기에 포함 된 인스턴스를 나열 하 고, 샘플 간격을 설정 하 고, 최대 샘플 수를 지정할 수 있습니다. 매개 변수가 없는 경우 `Get-Counter` 시스템 카운터 집합에 대 한 성능 카운터 데이터를 가져옵니다.

많은 카운터 집합은 ACL (액세스 제어 목록)에 의해 보호 됩니다. 모든 카운터 집합을 보려면 **관리자 권한으로 실행** 옵션을 사용 하 여 PowerShell을 엽니다.

이 cmdlet은 PowerShell 7에서 다시 도입 되었습니다.

## 예제

### 예제 1: 카운터 집합 목록 가져오기

이 예제에서는 로컬 컴퓨터의 카운터 집합 목록을 가져옵니다.

```powershell
Get-Counter -ListSet *
```

```Output
CounterSetName     : Processor
MachineName        : .
CounterSetType     : MultiInstance
Description        : The Processor performance object consists of counters that measure aspects ...
                     computer that performs arithmetic and logical computations, initiates ...
                     computer can have multiple processors.  The processor object represents ...
Paths              : {\Processor(*)\% Processor Time, \Processor(*)\% User Time, ...
PathsWithInstances : {\Processor(0)\% Processor Time, \Processor(1)\% Processor Time, ...
Counter            : {\Processor(*)\% Processor Time, \Processor(*)\% User Time, ...
```

`Get-Counter`**listset** 매개 변수를 별표 ()와 함께 사용 `*` 하 여 카운터 집합 목록을 가져옵니다.
`.` **MachineName** 열의 점 ()은 로컬 컴퓨터를 나타냅니다.

### 예제 2: SampleInterval 및 MaxSamples 지정

이 예에서는 로컬 컴퓨터의 모든 프로세서에 대 한 카운터 데이터를 가져옵니다. 데이터는 세 개의 샘플이 있을 때까지 2 초 간격으로 수집 됩니다.

```powershell
Get-Counter -Counter "\Processor(_Total)\% Processor Time" -SampleInterval 2 -MaxSamples 3
```

```Output
Timestamp                 CounterSamples
---------                 --------------
6/18/2019 14:39:56        \\Computer01\processor(_total)\% processor time :
                          20.7144271584086

6/18/2019 14:39:58        \\Computer01\processor(_total)\% processor time :
                          10.4391790575511

6/18/2019 14:40:01        \\Computer01\processor(_total)\% processor time :
                          37.5968799396998
```

`Get-Counter`**counter 매개 변수** 를 사용 하 여 카운터 경로를 지정 합니다 `\Processor(_Total)\% Processor Time` . **SampleInterval** 매개 변수는 카운터를 확인 하는 2 초 간격을 설정 합니다. **Maxsamples** 는 카운터가 카운터를 확인할 수 있는 최대 횟수를 3 개 지정 합니다.

### 예제 3: 카운터의 연속 샘플 가져오기

이 예에서는 초 마다 카운터에 대 한 연속 샘플을 가져옵니다. 명령을 중지 하려면 <kbd>ctrl</kbd> + <kbd>C</kbd>를 누릅니다. 샘플 사이에 더 긴 간격을 지정 하려면 **SampleInterval** 매개 변수를 사용 합니다.

```powershell
Get-Counter -Counter "\Processor(_Total)\% Processor Time" -Continuous
```

```Output
Timestamp                 CounterSamples
---------                 --------------
6/19/2019 15:35:03        \\Computer01\processor(_total)\% processor time :
                          43.8522842937022

6/19/2019 15:35:04        \\Computer01\processor(_total)\% processor time :
                          29.7896844697383

6/19/2019 15:35:05        \\Computer01\processor(_total)\% processor time :
                          29.4962645638135

6/19/2019 15:35:06        \\Computer01\processor(_total)\% processor time :
                          25.5901500127408
```

`Get-Counter`**counter 매개 변수** 를 사용 하 여 카운터를 지정 합니다 `\Processor\% Processor Time` .
**연속** 매개 변수는 명령이 <kbd>CTRL</kbd>C를 사용 하 여 중지 될 때까지 초 마다 샘플을 가져오도록 지정 합니다 + <kbd>C</kbd>.

### 예제 4: 카운터 집합의 사전순 목록

이 예제에서는 파이프라인을 사용 하 여 카운터 목록 집합을 가져온 다음 목록을 사전순으로 정렬 합니다.

```powershell
Get-Counter -ListSet * |
  Sort-Object -Property CounterSetName |
    Format-Table CounterSetName, CounterSetType -AutoSize
```

```Output
CounterSetName                        CounterSetType
--------------                        --------------
.NET CLR Data                         SingleInstance
.NET Data Provider for SqlServer      SingleInstance
AppV Client Streamed Data Percentage  SingleInstance
Authorization Manager Applications    SingleInstance
BitLocker                             MultiInstance
Bluetooth Device                      SingleInstance
Cache                                 SingleInstance
Client Side Caching                   SingleInstance
```

`Get-Counter`**Listset** 매개 변수를 별표 ()와 함께 사용 `*` 하 여 전체 카운터 집합 목록을 가져옵니다. **CounterSet** 개체는 파이프라인으로 전송 됩니다. `Sort-Object`**Property** 매개 변수를 사용 하 여 **CounterSetName** 를 기준으로 개체를 정렬 하도록 지정 합니다. 개체는 파이프라인에서로 전송 됩니다 `Format-Table` . **AutoSize** 매개 변수는 잘림을 최소화 하도록 열 너비를 조정 합니다.

`.` **MachineName** 열의 점 ()은 로컬 컴퓨터를 나타냅니다.

### 예 5: 백그라운드 작업을 실행 하 여 카운터 데이터 가져오기

이 예에서는 `Start-Job` `Get-Counter` 로컬 컴퓨터에서 명령을 백그라운드 작업으로 실행 합니다.
작업에서 성능 카운터 출력을 보려면 cmdlet을 사용 합니다 `Receive-Job` .

```powershell
Start-Job -ScriptBlock {Get-Counter -Counter "\LogicalDisk(_Total)\% Free Space" -MaxSamples 1000}
```

```Output
Id     Name  PSJobTypeName   State    HasMoreData  Location   Command
--     ----  -------------   -----    -----------  --------   -------
1      Job1  BackgroundJob   Running  True         localhost  Get-Counter -Counter
```

`Start-Job`**ScriptBlock** 매개 변수를 사용 하 여 `Get-Counter` 명령을 실행 합니다. `Get-Counter`**counter 매개 변수** 를 사용 하 여 카운터 경로를 지정 합니다 `\LogicalDisk(_Total)\% Free Space` . **Maxsamples** 매개 변수는 카운터의 1000 샘플을 가져오도록 지정 합니다.

### 예제 6: 여러 컴퓨터에서 카운터 데이터 가져오기

이 예에서는 변수를 사용 하 여 두 컴퓨터에서 성능 카운터 데이터를 가져옵니다.

```powershell
$DiskReads = "\LogicalDisk(C:)\Disk Reads/sec"
$DiskReads | Get-Counter -ComputerName Server01, Server02 -MaxSamples 10
```

```Output
Timestamp                 CounterSamples
---------                 --------------
6/21/2019 10:51:04        \\Server01\logicaldisk(c:)\disk reads/sec :
                          0

                          \\Server02\logicaldisk(c:)\disk reads/sec :
                          0.983050344269146
```

`$DiskReads`변수는 카운터 경로를 저장 합니다 `\LogicalDisk(C:)\Disk Reads/sec` . `$DiskReads`변수가 파이프라인에서로 전송 됩니다 `Get-Counter` . **Counter** 는 첫 번째 위치 매개 변수 이며에 저장 된 경로를 허용 합니다 `$DiskReads` . **ComputerName** 은 두 컴퓨터를 지정 하 고 **maxsamples** 는 각 컴퓨터에서 10 개의 샘플을 가져오도록 지정 합니다.

### 예 7: 여러 임의의 컴퓨터에서 카운터의 인스턴스 값 가져오기

이 예제에서는 엔터프라이즈의 원격 컴퓨터 50 대 한 성능 카운터 값을 가져옵니다. **ComputerName** 매개 변수는 변수에 저장 된 임의의 컴퓨터 이름을 사용 합니다. 변수의 컴퓨터 이름을 업데이트 하려면 변수를 다시 만듭니다.

**ComputerName** 매개 변수의 서버 이름에 대 한 대안은 텍스트 파일을 사용 하는 것입니다. 다음은 그 예입니다. 

`-ComputerName (Get-Random (Get-Content -Path C:\Servers.txt) -Count 50)`

카운터 경로에는 `*` 각 원격 컴퓨터의 프로세서에 대 한 데이터를 가져오기 위해 인스턴스 이름에 별표 ()가 포함 됩니다.

```powershell
$Servers = Get-Random (Get-Content -Path C:\Servers.txt) -Count 50
$Counter = "\Processor(*)\% Processor Time"
Get-Counter -Counter $Counter -ComputerName $Servers
```

```Output
Timestamp                 CounterSamples
---------                 --------------
6/20/2019 12:20:35        \\Server01\processor(0)\% processor time :
                          6.52610319637854

                          \\Server01\processor(1)\% processor time :
                          3.41030663625782

                          \\Server01\processor(2)\% processor time :
                          9.64189975649925

                          \\Server01\processor(3)\% processor time :
                          1.85240835619747

                          \\Server01\processor(_total)\% processor time :
                          5.35768447160776
```

`Get-Random`Cmdlet은 `Get-Content` 를 사용 하 여 파일에서 50 임의의 컴퓨터 이름을 선택 `Servers.txt` 합니다. 원격 컴퓨터 이름은 변수에 저장 됩니다 `$Servers` . `\Processor(*)\% Processor Time`카운터의 경로는 변수에 저장 됩니다 `$Counter` . `Get-Counter`**Counter** 매개 변수를 사용 하 여 변수의 카운터를 지정 `$Counter` 합니다. **ComputerName** 매개 변수는 변수의 컴퓨터 이름을 지정 합니다 `$Servers` .

### 예 8: 경로 속성을 사용 하 여 형식이 지정 된 경로 이름 가져오기

이 예제에서는 카운터 집합의 **path** 속성을 사용 하 여 성능 카운터에 대해 형식이 지정 된 경로 이름을 찾습니다.

파이프라인은 cmdlet과 함께 `Where-Object` 경로 이름의 하위 집합을 찾는 데 사용 됩니다. 카운터 집합의 전체 목록을 검색 하려면 파이프라인 ( `|` ) 및 명령을 제거 합니다 `Where-Object` .

는 `$_` 파이프라인의 현재 개체에 대 한 자동 변수입니다.
자세한 내용은 [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)를 참조 하세요.

```powershell
(Get-Counter -ListSet Memory).Paths | Where-Object { $_ -like "*Cache*" }
```

```Output
\Memory\Cache Faults/sec
\Memory\Cache Bytes
\Memory\Cache Bytes Peak
\Memory\System Cache Resident Bytes
\Memory\Standby Cache Reserve Bytes
\Memory\Standby Cache Normal Priority Bytes
\Memory\Standby Cache Core Bytes
\Memory\Long-Term Average Standby Cache Lifetime (s)
```

`Get-Counter`**listset** 매개 변수를 사용 하 여 **메모리** 카운터 집합을 지정 합니다. **경로** 속성이 각 경로를 문자열로 반환 하도록 명령이 괄호로 묶여 있습니다. 개체는 파이프라인에서로 전송 됩니다 `Where-Object` . `Where-Object` 변수를 사용 하 여 `$_` 각 개체를 처리 하 고 연산자를 사용 하 여 `-like` 문자열에 대 한 일치 항목을 찾습니다 `*Cache*` . 별표 ( `*` )는 모든 문자에 대 한 와일드 카드입니다.

### 예 9: PathsWithInstances 속성을 사용 하 여 형식이 지정 된 경로 이름 가져오기

이 예제에서는 **PhysicalDisk** 성능 카운터에 대 한 인스턴스를 포함 하는 형식이 지정 된 경로 이름을 가져옵니다.

```powershell
(Get-Counter -ListSet PhysicalDisk).PathsWithInstances
```

```Output
\PhysicalDisk(0 C:)\Current Disk Queue Length
\PhysicalDisk(_Total)\Current Disk Queue Length
\PhysicalDisk(0 C:)\% Disk Time
\PhysicalDisk(_Total)\% Disk Time
\PhysicalDisk(0 C:)\Avg. Disk Queue Length
\PhysicalDisk(_Total)\Avg. Disk Queue Length
\PhysicalDisk(0 C:)\% Disk Read Time
\PhysicalDisk(_Total)\% Disk Read Time
```

`Get-Counter`**listset** 매개 변수를 사용 하 여 **PhysicalDisk** 카운터 집합을 지정 합니다. **Pathswithinstances** 속성이 각 경로 인스턴스를 문자열로 반환 하도록 명령이 괄호로 묶여 있습니다.

### 예 10: 카운터 집합의 각 카운터에 대 한 단일 값 가져오기

이 예제에서는 로컬 컴퓨터의 **메모리** 카운터 집합에 있는 각 성능 카운터에 대해 단일 값이 반환 됩니다.

```powershell
$MemCounters = (Get-Counter -ListSet Memory).Paths
Get-Counter -Counter $MemCounters
```

```Output
Timestamp                 CounterSamples
---------                 --------------
6/19/2019 12:05:00        \\Computer01\memory\page faults/sec :
                          868.772077545597

                          \\Computer01\memory\available bytes :
                          9031176192

                          \\Computer01\memory\committed bytes :
                          8242982912

                          \\Computer01\memory\commit limit :
                          19603333120
```

`Get-Counter`**listset** 매개 변수를 사용 하 여 **메모리** 카운터 집합을 지정 합니다. **경로** 속성이 각 경로를 문자열로 반환 하도록 명령이 괄호로 묶여 있습니다. 경로는 변수에 저장 됩니다 `$MemCounters` . `Get-Counter`**counter** 매개 변수를 사용 하 여 변수의 카운터 경로를 지정 `$MemCounters` 합니다.

### 예 11: 개체의 속성 값 표시

**Microsoft.powershell.commands.getcounter.performancecountersample** 개체의 속성 값은 각 데이터 샘플을 나타냅니다. 이 예제에서는 **Countersamples** 개체의 속성을 사용 하 여 데이터를 검사, 선택, 정렬 및 그룹화 합니다.

```powershell
$Counter = "\\Server01\Process(Idle)\% Processor Time"
$Data = Get-Counter $Counter
$Data.CounterSamples | Format-List -Property *
```

```Output
Path             : \\Server01\process(idle)\% processor time
InstanceName     : idle
CookedValue      : 198.467899571389
RawValue         : 14329160321003
SecondValue      : 128606459528326201
MultipleCount    : 1
CounterType      : Timer100Ns
Timestamp        : 6/19/2019 12:20:49
Timestamp100NSec : 128606207528320000
Status           : 0
DefaultScale     : 0
TimeBase         : 10000000
```

카운터 경로는 변수에 저장 됩니다 `$Counter` . `Get-Counter` 카운터 값의 샘플 하나를 가져오고 결과를 `$Data` 변수에 저장 합니다. `$Data`변수는 **countersamples** 속성을 사용 하 여 개체의 속성을 가져옵니다. 개체는 파이프라인에서로 전송 됩니다 `Format-List` . **Property** 매개 변수는 별표 ( `*` ) 와일드 카드를 사용 하 여 모든 속성을 선택 합니다.

### 예 12: 성능 카운터 배열 값

이 예제에서 변수는 각 성능 카운터를 저장 합니다. **Countersamples** 속성은 특정 카운터 값을 표시할 수 있는 배열입니다.

각 카운터 샘플을 표시 하려면를 사용 `$Counter.CounterSamples` 합니다.

```powershell
$Counter = Get-Counter -Counter "\Processor(*)\% Processor Time"
$Counter.CounterSamples[0]
```

```Output
Path                                         InstanceName        CookedValue
----                                         ------------        -----------
\\Computer01\processor(0)\% processor time   0              1.33997091699662
```

`Get-Counter`**counter 매개 변수** 를 사용 하 여 카운터를 지정 합니다 `\Processor(*)\% Processor Time` . 값은 변수에 저장 됩니다 `$Counter` .
`$Counter.CounterSamples[0]` 첫 번째 카운터 값의 배열 값을 표시 합니다.

### 예 13: 성능 카운터 값 비교

이 예에서는 로컬 컴퓨터의 각 프로세서에서 사용 하는 프로세서 시간 크기를 찾습니다. **Countersamples** 속성은 카운터 데이터를 지정 된 값과 비교 하는 데 사용 됩니다.

각 카운터 샘플을 표시 하려면를 사용 `$Counter.CounterSamples` 합니다.

```powershell
$Counter = Get-Counter -Counter "\Processor(*)\% Processor Time"
$Counter.CounterSamples | Where-Object { $_.CookedValue -lt "20" }
```

```Output
Path                                         InstanceName        CookedValue
----                                         ------------        -----------
\\Computer01\processor(0)\% processor time   0              12.6398025240208
\\Computer01\processor(1)\% processor time   1              15.7598095767344
```

`Get-Counter`**counter 매개 변수** 를 사용 하 여 카운터를 지정 합니다 `\Processor(*)\% Processor Time` . 값은 변수에 저장 됩니다 `$Counter` . 에 저장 된 개체는 `$Counter.CounterSamples` 파이프라인으로 전송 됩니다. `Where-Object` 는 스크립트 블록을 사용 하 여 각 개체 값을 지정 된 값 20과 비교 합니다. 는 `$_.CookedValue` 파이프라인의 현재 개체에 대 한 변수입니다. **CookedValue** 가 20 미만인 카운터가 표시 됩니다.

### 예 14: 성능 카운터 데이터 정렬

이 예제에서는 성능 카운터 데이터를 정렬 하는 방법을 보여 줍니다. 이 예제에서는 샘플 중 프로세서 시간을 가장 많이 사용 하는 컴퓨터에서 프로세스를 찾습니다.

```powershell
$Procs = Get-Counter -Counter "\Process(*)\% Processor Time"
$Procs.CounterSamples | Sort-Object -Property CookedValue -Descending |
   Format-Table -Property Path, InstanceName, CookedValue -AutoSize
```

```Output
Path                                                         InstanceName             CookedValue
----                                                         ------------             -----------
\\Computer01\process(_total)\% processor time                _total              395.464129650573
\\Computer01\process(idle)\% processor time                  idle                389.356575524695
\\Computer01\process(mssense)\% processor time               mssense             3.05377706293879
\\Computer01\process(csrss#1)\% processor time               csrss               1.52688853146939
\\Computer01\process(microsoftedgecp#10)\% processor time    microsoftedgecp     1.52688853146939
\\Computer01\process(runtimebroker#5)\% processor time       runtimebroker                      0
\\Computer01\process(settingsynchost)\% processor time       settingsynchost                    0
\\Computer01\process(microsoftedgecp#16)\% processor time    microsoftedgecp                    0
```

`Get-Counter`**counter** 매개 변수를 사용 하 여 `\Process(*)\% Processor Time` 로컬 컴퓨터의 모든 프로세스에 대 한 카운터를 지정 합니다. 결과는 변수에 저장 됩니다 `$Procs` . `$Procs` **Countersamples** 속성이 있는 변수는 **microsoft.powershell.commands.getcounter.performancecountersample** 개체를 파이프라인으로 보냅니다. `Sort-Object`**Property** 매개 변수를 사용 하 여 **CookedValue** 를 기준으로 개체를 **내림차순** 으로 정렬 합니다. `Format-Table`**Property** 매개 변수를 사용 하 여 출력에 대 한 열을 선택 합니다. **AutoSize** 매개 변수는 잘림을 최소화 하도록 열 너비를 조정 합니다.

## PARAMETERS

### -ComputerName

단일 컴퓨터 이름 또는 쉼표로 구분 된 **원격** 컴퓨터 이름 배열을 지정 합니다. NetBIOS 이름, IP 주소 또는 컴퓨터의 정규화 된 도메인 이름을 사용 합니다.

**로컬** 컴퓨터에서 성능 카운터 데이터를 가져오려면 **ComputerName** 매개 변수를 제외 합니다.
**MachineName** 열을 포함 하는 **listset** 과 같은 출력의 경우 점 ( `.` )은 로컬 컴퓨터를 나타냅니다.

`Get-Counter` 은 PowerShell 원격을 사용 하지 않습니다. 컴퓨터에서 원격 명령을 실행 하도록 구성 되지 않은 경우에도 **ComputerName** 매개 변수를 사용할 수 있습니다.

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

### -Continuous

**연속** 이 지정 된 경우 `Get-Counter` <kbd>ctrl</kbd>C를 누를 때까지 샘플을 가져옵니다 + <kbd>C</kbd>. 지정 된 각 성능 카운터에 대해 매 초 마다 샘플이 얻어집니다. 연속 샘플 간 간격을 늘리려면 **SampleInterval** 매개 변수를 사용 합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GetCounterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Counter

하나 이상의 카운터 경로에 대 한 경로를 지정 합니다. 경로는 쉼표로 구분 된 배열, 변수 또는 텍스트 파일의 값으로 입력 됩니다. 파이프라인에서로 카운터 경로 문자열을 보낼 수 있습니다 `Get-Counter` .

카운터 경로는 다음 구문을 사용 합니다.

`\\ComputerName\CounterSet(Instance)\CounterName`

`\CounterSet(Instance)\CounterName`

다음은 그 예입니다. 

`\\Server01\Processor(*)\% User Time`

`\Processor(*)\% User Time`

는 `\\ComputerName` 성능 카운터 경로에서 선택 사항입니다. 카운터 경로에 컴퓨터 이름이 포함 되지 않은 경우는 `Get-Counter` 로컬 컴퓨터를 사용 합니다.

인스턴스의 별표 ( `*` )는 카운터의 모든 인스턴스를 가져오기 위한 와일드 카드 문자입니다.

```yaml
Type: System.String[]
Parameter Sets: GetCounterSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -ListSet

컴퓨터에 대 한 성능 카운터 집합을 나열 합니다. 별표 ( `*` )를 사용 하 여 모든 카운터 집합을 지정 합니다. 이름 또는 쉼표로 구분 된 카운터 집합 이름 문자열을 입력 합니다. 파이프라인에서 카운터 집합 이름을 보낼 수 있습니다.

카운터 집합 형식의 카운터 경로를 가져오려면 **Listset** 매개 변수를 사용 합니다. 각 카운터 집합의 **Paths** 및 **Pathswithinstances** 속성은 문자열로 형식이 지정 된 개별 카운터 경로를 포함 합니다.

카운터 경로 문자열을 변수에 저장 하거나 파이프라인을 사용 하 여 문자열을 다른 명령으로 보낼 수 있습니다 `Get-Counter` .

예를 들어 각 **프로세서** 카운터 경로를로 보내려면 `Get-Counter` 다음을 수행 합니다.

`Get-Counter -ListSet Processor | Get-Counter`

> [!NOTE]
> PowerShell 7에서 `Get-Counter` 카운터 집합의 **Description** 속성을 검색할 수 없습니다. **설명은** 로 설정 됩니다 `$null` .

```yaml
Type: System.String[]
Parameter Sets: ListSetSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
```

### -MaxSamples

지정 된 각 성능 카운터에서 가져올 샘플 수를 지정 합니다. 샘플의 상수 스트림을 가져오려면 **연속** 매개 변수를 사용 합니다.

**Maxsamples** 매개 변수를 지정 하지 않으면 `Get-Counter` 지정 된 각 카운터에 대해 하나의 샘플만 가져옵니다.

대량 데이터 집합을 수집 하려면를 `Get-Counter` PowerShell 백그라운드 작업으로 실행 합니다. 자세한 내용은 [about_Jobs](../Microsoft.PowerShell.Core/About/about_Jobs.md)를 참조하세요.

```yaml
Type: System.Int64
Parameter Sets: GetCounterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SampleInterval

지정 된 각 성능 카운터에 대 한 샘플 사이의 시간 (초)을 지정 합니다. **SampleInterval** 매개 변수가 지정 되지 않은 경우는 `Get-Counter` 1 초 간격을 사용 합니다.

```yaml
Type: System.Int32
Parameter Sets: GetCounterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.String[]

`Get-Counter` 카운터 경로 및 카운터 집합 이름에 대 한 파이프라인 입력을 허용 합니다.

## 출력

### PerformanceCounterSampleSet, Microsoft.powershell.commands.getcounter.performancecountersample,. m a. m a.. m a.. m a..

개체의 속성을 보려면 출력을 파이프라인에서로 보냅니다 `Get-Member` . 출력 되는 개체 유형은 다음과 같습니다.

**Listset** 매개 변수: **Microsoft. PowerShell** .

**Counter** 매개 변수: **PerformanceCounterSampleSet.**

**Countersamples** 속성은 **microsoft.powershell.commands.getcounter.performancecountersample** 입니다.

## 참고

매개 변수를 지정 하지 않으면 `Get-Counter` 지정 된 각 성능 카운터에 대해 하나의 샘플을 가져옵니다. **Maxsamples** 및 **연속** 매개 변수를 사용 하 여 더 많은 샘플을 가져옵니다.

`Get-Counter` 샘플 사이에 1 초 간격을 사용 합니다. **SampleInterval** 매개 변수를 사용 하 여 간격을 늘립니다.

**Maxsamples** 및 **SampleInterval** 값은 명령에서 각 컴퓨터의 모든 카운터에 적용 됩니다. 다른 카운터에 대해 다른 값을 설정 하려면 별도의 `Get-Counter` 명령을 입력 합니다.

PowerShell 7에서 **listset** 매개 변수를 사용 하는 경우에서 `Get-Counter` 카운터 집합의 **Description** 속성을 검색할 수 없습니다. **설명은** 로 설정 됩니다 `$null` .

## 관련 링크

[about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

[about_Jobs](../Microsoft.PowerShell.Core/About/about_Jobs.md)

[Format-List](../Microsoft.PowerShell.Utility/Format-List.md)

[Format-Table](../Microsoft.PowerShell.Utility/Format-Table.md)

[Get-Member](../Microsoft.PowerShell.Utility/Get-Member.md)

[Receive-Job](../Microsoft.PowerShell.Core/Receive-Job.md)

[Start-Job](../Microsoft.PowerShell.Core/Start-Job.md)

[Where-Object](..//Microsoft.PowerShell.Core/Where-Object.md)

