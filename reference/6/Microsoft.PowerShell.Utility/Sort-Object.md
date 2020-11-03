---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/20/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/sort-object?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Sort-Object
ms.openlocfilehash: 3eef18677c8f81b560354303c2d685abfc44601c
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/10/2020
ms.locfileid: "93219385"
---
# Sort-Object

## 개요
속성 값에 따라 개체를 정렬합니다.

## SYNTAX

### Default (기본값)

```
Sort-Object [-Stable] [-Descending] [-Unique] [-InputObject <PSObject>] [[-Property] <Object[]>]
 [-Culture <String>] [-CaseSensitive] [<CommonParameters>]
```

### 상위

```
Sort-Object [-Descending] [-Unique] -Top <Int32> [-InputObject <PSObject>] [[-Property] <Object[]>]
 [-Culture <String>] [-CaseSensitive] [<CommonParameters>]
```

### 아래쪽

```
Sort-Object [-Descending] [-Unique] -Bottom <Int32> [-InputObject <PSObject>] [[-Property] <Object[]>]
 [-Culture <String>] [-CaseSensitive] [<CommonParameters>]
```

## 설명

`Sort-Object`Cmdlet은 개체 속성 값을 기준으로 개체를 오름차순 또는 내림차순으로 정렬 합니다. 명령에 정렬 속성이 포함 되지 않은 경우 PowerShell은 첫 번째 입력 개체의 기본 정렬 속성을 사용 합니다. 입력 개체의 형식에 기본 정렬 속성이 없으면 PowerShell에서 개체 자체를 비교 하려고 시도 합니다. 자세한 내용은 [참고](#notes) 섹션을 참조 하세요.

단일 속성 또는 여러 속성을 기준으로 개체를 정렬할 수 있습니다. 여러 속성은 해시 테이블을 사용 하 여 오름차순, 내림차순 또는 정렬 주문의 조합을 정렬 합니다. 속성이 대/소문자를 구분 하거나 대/소문자를 구분 하지 않고 정렬 됩니다. **Unique** 매개 변수를 사용 하 여 출력에서 중복 항목을 제거 합니다.

## 예제

### 예제 1: 이름을 기준으로 현재 디렉터리 정렬

이 예에서는 디렉터리의 파일 및 하위 디렉터리를 정렬 합니다.

```
PS> Get-ChildItem -Path C:\Test | Sort-Object

    Directory: C:\Test

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/13/2019     08:55             26 anotherfile.txt
-a----        2/13/2019     13:26             20 Bfile.txt
-a----        2/12/2019     15:40         118014 Command.txt
-a----         2/1/2019     08:43            183 CreateTestFile.ps1
d-----        2/25/2019     18:25                Files
d-----        2/25/2019     18:24                Logs
-ar---        2/12/2019     14:31             27 ReadOnlyFile.txt
-a----        2/12/2019     16:24             23 Zsystemlog.log
```

`Get-ChildItem`Cmdlet은 **Path** 매개 변수 **C:\Test** 로 지정 된 디렉터리에서 파일 및 하위 디렉터리를 가져옵니다. 개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Sort-Object` .
`Sort-Object` 는 속성을 지정 하지 않으므로 출력은 기본 정렬 속성인 **Name** 을 기준으로 정렬 됩니다.

### 예제 2: 파일 길이를 기준으로 현재 디렉터리 정렬

이 명령은 현재 디렉터리의 파일 길이를 오름차순으로 표시 합니다.

```
PS> Get-ChildItem -Path C:\Test -File | Sort-Object -Property Length

    Directory: C:\Test

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/13/2019     13:26             20 Bfile.txt
-a----        2/12/2019     16:24             23 Zsystemlog.log
-a----        2/13/2019     08:55             26 anotherfile.txt
-ar---        2/12/2019     14:31             27 ReadOnlyFile.txt
-a----         2/1/2019     08:43            183 CreateTestFile.ps1
-a----        2/12/2019     15:40         118014 Command.txt
```

`Get-ChildItem`Cmdlet은 **Path** 매개 변수로 지정 된 디렉터리에서 파일을 가져옵니다.
**File** 매개 변수는에서 파일 개체만을 가져오기로 지정 합니다 `Get-ChildItem` . 개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Sort-Object` . `Sort-Object`**길이** 매개 변수를 사용 하 여 파일을 오름차순으로 정렬 합니다.

### 예제 3: 메모리 사용량을 기준으로 프로세스 정렬

이 예제에서는 WS (작업 집합) 크기를 기준으로 메모리 사용량이 가장 높은 프로세스를 표시 합니다.

```
PS> Get-Process | Sort-Object -Property WS | Select-Object -Last 5

 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
    136   193.92     217.11     889.16   87492   8 OUTLOOK
    112   347.73     297.02      95.19  106908   8 Teams
    206   266.54     323.71      37.17   60620   8 MicrosoftEdgeCP
     35   552.19     549.94     131.66    6552   8 Code
      0     1.43     595.12       0.00    2780   0 Memory Compression
```

`Get-Process`Cmdlet은 컴퓨터에서 실행 중인 프로세스 목록을 가져옵니다. 프로세스 개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Sort-Object` . `Sort-Object`**Property** 매개 변수를 사용 하 여 **WS** 를 기준으로 개체를 정렬 합니다. 개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Select-Object` .
`Select-Object`**마지막** 매개 변수를 사용 하 여 가장 높은 **WS** 사용을 가진 개체인 마지막 5 개 개체를 지정 합니다.

PowerShell 6에서 `Sort-Object` **아래쪽** 매개 변수는 대신 사용할 수 `Select-Object` 있습니다. 예들 들어 `Get-Process | Sort-Object -Property WS -Bottom 5`입니다.

### 예제 4: Id 별 HistoryInfo 개체 정렬

이 명령은 **Id** 속성을 사용 하 여 PowerShell 세션의 **HistoryInfo** 개체를 정렬 합니다. 각 PowerShell 세션에는 자체 명령 기록이 있습니다.

```
PS> Get-History | Sort-Object -Property Id -Descending

  Id CommandLine
  -- -----------
  10 Get-Command Sort-Object -Syntax
   9 $PSVersionTable
   8 Get-Command Sort-Object -Syntax
   7 Get-Command Sort-Object -ShowCommandInfo
   6 Get-ChildItem -Path C:\Test | Sort-Object -Property Length
   5 Get-Help Clear-History -online
   4 Get-Help Clear-History -full
   3 Get-ChildItem | Get-Member
   2 Get-Command Sort-Object -Syntax
   1 Set-Location C:\Test\
```

`Get-History`Cmdlet은 현재 PowerShell 세션에서 기록 개체를 가져옵니다. 개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Sort-Object` . `Sort-Object`**Property** 매개 변수를 사용 하 여 **Id** 를 기준으로 개체를 정렬 합니다. **내림차순** 매개 변수는 명령 기록을 최신에서 가장 오래 된 순서로 정렬 합니다.

### 예 5: 해시 테이블을 사용 하 여 속성을 오름차순 및 내림차순으로 정렬

이 예제에서는 두 가지 속성을 사용 하 여 개체, **상태** 및 **DisplayName** 을 정렬 합니다. **상태** 는 내림차순으로 정렬 되 고 **DisplayName** 은 오름차순으로 정렬 됩니다.

해시 테이블은 **속성** 매개 변수의 값을 지정 하는 데 사용 됩니다. 해시 테이블은 식을 사용 하 여 속성 이름과 정렬 순서를 지정 합니다. 해시 테이블에 대한 자세한 내용은 [about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md)를 참조하세요.

해시 테이블에 사용 되는 **Status** 속성은 열거 된 속성입니다.
자세한 내용은 [ServiceControllerStatus](/dotnet/api/system.serviceprocess.servicecontrollerstatus)를 참조 하세요.

```
PS C:\> Get-Service | Sort-Object -Property @{Expression = "Status"; Descending = $True}, @{Expression = "DisplayName"; Descending = $False}

Status   Name               DisplayName
------   ----               -----------
Running  Appinfo            Application Information
Running  BthAvctpSvc        AVCTP service
Running  BrokerInfrastru... Background Tasks Infrastructure Ser...
Running  BDESVC             BitLocker Drive Encryption Service
Running  CoreMessagingRe... CoreMessaging
Running  VaultSvc           Credential Manager
Running  DsSvc              Data Sharing Service
Running  Dhcp               DHCP Client
...
Stopped  ALG                Application Layer Gateway Service
Stopped  AppMgmt            Application Management
Stopped  BITS               Background Intelligent Transfer Ser...
Stopped  wbengine           Block Level Backup Engine Service
Stopped  BluetoothUserSe... Bluetooth User Support Service_14fb...
Stopped  COMSysApp          COM+ System Application
Stopped  smstsmgr           ConfigMgr Task Sequence Agent
Stopped  DeviceInstall      Device Install Service
Stopped  MSDTC              Distributed Transaction Coordinator
```

`Get-Service`Cmdlet은 컴퓨터의 서비스 목록을 가져옵니다. Service 개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Sort-Object` . `Sort-Object`**property 매개 변수** 를 해시 테이블에 사용 하 여 속성 이름과 정렬 순서를 지정 합니다. **Property** 매개 변수는 **상태** 를 내림차순으로, **DisplayName** 을 오름차순으로 정렬 하 여 두 개의 속성을 기준으로 정렬 됩니다.

**Status** 는 열거 된 속성입니다. **중지 됨** 의 값은 **1** 이 고 **실행** 값은 **4** 입니다. 중지 **Descending** 된 `$True` 프로세스 전에 **실행 중인** 프로세스가 표시 되도록 내림차순 매개 변수가로 **Stopped** 설정 됩니다. **DisplayName** 은 **내림차순** 매개 변수를로 설정 `$False` 하 여 표시 이름을 알파벳 순서로 정렬 합니다.

### 예제 6: 시간 범위를 기준으로 텍스트 파일 정렬

이 명령은 **CreationTime** 와 **LastWriteTime** 사이의 시간 간격에 따라 텍스트 파일을 내림차순으로 정렬 합니다.

```
PS> Get-ChildItem -Path C:\Test\*.txt | Sort-Object -Property @{Expression = {$_.CreationTime - $_.LastWriteTime}; Descending = $False} | Format-Table CreationTime, LastWriteTime, FullName

CreationTime          LastWriteTime        FullName
------------          -------------        --------
11/21/2018 12:39:01   2/26/2019 08:59:36   C:\Test\test2.txt
12/4/2018 08:29:41    2/26/2019 08:57:05   C:\Test\powershell_list.txt
2/20/2019 08:15:59    2/26/2019 12:09:43   C:\Test\CreateTestFile.txt
2/20/2019 08:15:59    2/26/2019 12:07:41   C:\Test\Command.txt
2/20/2019 08:15:59    2/26/2019 08:57:52   C:\Test\ReadOnlyFile.txt
11/29/2018 15:16:50   12/4/2018 16:16:24   C:\Test\LogData.txt
2/25/2019 18:25:11    2/26/2019 12:08:47   C:\Test\Zsystemlog.txt
2/25/2019 18:25:11    2/26/2019 08:55:33   C:\Test\Bfile.txt
2/26/2019 08:46:59    2/26/2019 12:12:19   C:\Test\LogFile3.txt
```

`Get-ChildItem`Cmdlet은 **Path** 매개 변수를 사용 하 여 **C:\Test** 및 모든 파일 디렉터리를 지정 합니다 `*.txt` . 개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Sort-Object` .
`Sort-Object` 는 해시 테이블에 **Property** 매개 변수를 사용 하 여 **CreationTime** 와 **LastWriteTime** 사이의 각 파일 시간 범위를 확인 합니다. **내림차순** 매개 변수가로 설정 되어 가장 `$False` 긴 시간 범위에서 가장 짧은 시간 범위 순으로 정렬 됩니다.

### 예 7: 텍스트 파일에서 이름 정렬

이 예제에서는 텍스트 파일에서 목록을 정렬 하는 방법을 보여 줍니다. 원본 파일은 정렬 되지 않은 목록으로 표시 됩니다. `Sort-Object` 내용을 정렬 하 고 중복 항목을 제거 하는 **고유한** 매개 변수를 사용 하 여 내용을 정렬 합니다.

```
PS> Get-Content -Path C:\Test\ServerNames.txt
localhost
server01
server25
LOCALHOST
Server19
server3
localhost

PS> Get-Content -Path C:\Test\ServerNames.txt | Sort-Object
localhost
LOCALHOST
localhost
server01
Server19
server25
server3

PS> Get-Content -Path C:\Test\ServerNames.txt | Sort-Object -Unique
localhost
server01
Server19
server25
server3
```

`Get-Content`Cmdlet은 **Path** 매개 변수를 사용 하 여 디렉터리 및 파일 이름을 지정 합니다. 파일 **ServerNames.txt** 에는 정렬 되지 않은 컴퓨터 이름 목록이 포함 되어 있습니다.

`Get-Content`Cmdlet은 **Path** 매개 변수를 사용 하 여 디렉터리 및 파일 이름을 지정 합니다. 파일 **ServerNames.txt** 에는 정렬 되지 않은 컴퓨터 이름 목록이 포함 되어 있습니다. 개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Sort-Object` . `Sort-Object` 목록을 기본 순서 오름차순으로 정렬 합니다.

`Get-Content`Cmdlet은 **Path** 매개 변수를 사용 하 여 디렉터리 및 파일 이름을 지정 합니다. 파일 **ServerNames.txt** 에는 정렬 되지 않은 컴퓨터 이름 목록이 포함 되어 있습니다. 개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Sort-Object` . `Sort-Object`**Unique** 매개 변수를 사용 하 여 중복 된 컴퓨터 이름을 제거 합니다. 목록은 기본 순서 오름차순으로 정렬 됩니다.

### 예 8: 문자열을 정수로 정렬

이 예제에서는 문자열 개체를 포함 하는 텍스트 파일을 정수로 정렬 하는 방법을 보여 줍니다. 각 명령을 파이프라인에서로 보내고 `Get-Member` 개체가 정수 대신 문자열 인지 확인할 수 있습니다. 이러한 예제에서 파일에는 `ProductId.txt` 정렬 되지 않은 제품 번호 목록이 포함 되어 있습니다.

첫 번째 예제에서 `Get-Content` 파일의 내용을 가져오고 해당 줄을 cmdlet으로 파이프 합니다 `Sort-Object` . `Sort-Object` 문자열 개체를 오름차순으로 정렬 합니다.

```
PS> Get-Content -Path C:\Test\ProductId.txt | Sort-Object
0
1
12345
1500
2
2800
3500
4100
500
6200
77
88
99999

PS> Get-Content -Path C:\Test\ProductId.txt | Sort-Object {[int]$_}
0
1
2
77
88
500
1500
2800
3500
4100
6200
12345
99999
```

두 번째 예제에서는 `Get-Content` 파일의 내용을 가져오고이를 cmdlet으로 파이프 합니다 `Sort-Object` . `Sort-Object` 는 스크립트 블록을 사용 하 여 문자열을 정수로 변환 합니다. 샘플 코드에서는 `[int]` 문자열을 정수로 변환 하 고 `$_` 파이프라인에서 제공 되는 각 문자열을 나타냅니다. 정수 개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Sort-Object` .
`Sort-Object` 정수 개체를 숫자 순서로 정렬 합니다.

### 예 9: 안정적인 정렬 사용

**Top** , **Bottom** 또는 **안정** 된 매개 변수를 사용할 경우 정렬 된 개체는 `Sort-Object` 정렬 기준이 같을 때에서 받은 순서 대로 배달 됩니다. 이 예제에서는 값 ' 모듈로 3 '을 기준으로 1부터 20 까지의 숫자를 정렬 합니다. 모듈로 값의 범위는 0에서 2 사이입니다.

```powershell
PS> 1..20 |Sort-Object {$_ % 3}
18
3
15
6
12
9
1
16
13
10
7
4
19
11
8
14
5
17
2
20

PS> 1..20 |Sort-Object {$_ % 3} -Stable
3
6
9
12
15
18
1
4
7
10
13
16
19
2
5
8
11
14
17
20
```

첫 번째 정렬의 출력은 모듈러스 값에 의해 올바르게 그룹화 되지만 개별 항목은 모듈러스 범위 내에서 정렬 되지 않습니다. 두 번째 정렬은 **안정** 된 옵션을 사용 하 여 안정적인 정렬을 반환 합니다.

## PARAMETERS

### -아래쪽

정렬 된 개체 배열의 끝에서 가져올 개체 수를 지정 합니다. 이로 인해 안정적으로 정렬 됩니다.

이 매개 변수는 PowerShell 6.0에서 도입 되었습니다.

```yaml
Type: System.Int32
Parameter Sets: Bottom
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CaseSensitive

정렬에서 대/소문자를 구분 함을 나타냅니다. 기본적으로 정렬은 대/소문자를 구분 하지 않습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Case-insensitive
Accept pipeline input: False
Accept wildcard characters: False
```

### -문화권

정렬에 사용할 문화권 구성을 지정 합니다. `Get-Culture`를 사용 하 여 시스템의 문화권 구성을 표시 합니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -내림차순

`Sort-Object`에서 개체를 내림차순으로 정렬 함을 나타냅니다. 기본값은 오름차순입니다.

여러 정렬 순서를 사용 하 여 여러 속성을 정렬 하려면 해시 테이블을 사용 합니다. 예를 들어 해시 테이블을 사용 하면 한 속성을 오름차순으로 정렬 하 고 다른 속성은 내림차순으로 정렬할 수 있습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Ascending
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

개체를 정렬 하려면 파이프라인에서로 보냅니다 `Sort-Object` . **InputObject** 매개 변수를 사용 하 여 항목 컬렉션을 전송 하는 경우는 `Sort-Object` 컬렉션을 나타내는 개체 하나를 수신 합니다. 하나의 개체를 정렬할 수 없기 때문에에서 `Sort-Object` 전체 컬렉션을 변경 하지 않고 반환 합니다.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -속성

`Sort-Object`에서 개체를 정렬 하는 데 사용 하는 속성 이름을 지정 합니다. 와일드카드가 지원됩니다.
개체는 속성 값을 기준으로 정렬 됩니다. 속성을 지정 하지 않을 경우는 `Sort-Object` 개체 형식 또는 개체 자체에 대 한 기본 속성을 기준으로 정렬 합니다.

여러 속성을 오름차순, 내림차순 또는 정렬 순서의 조합으로 정렬할 수 있습니다. 여러 속성을 지정 하는 경우 개체는 첫 번째 속성을 기준으로 정렬 됩니다. 여러 개체가 첫 번째 속성에 대해 동일한 값을 가지는 경우 해당 개체는 두 번째 속성에 따라 정렬 됩니다. 지정된 속성이나 개체 그룹이 더 이상 없을 때까지 이 프로세스가 계속됩니다.

**속성** 매개 변수의 값은 계산 된 속성 일 수 있습니다. 계산된 속성을 만들려면 해시 테이블을 사용하세요.

해시 테이블에 대 한 유효한 키는 다음과 같습니다.

- `expression` - `<string>` 또는 `<script block>`
- `ascending` 디스크나 `descending` - `<boolean>`

자세한 내용은 [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)를 참조 하세요.

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: Default properties
Accept pipeline input: False
Accept wildcard characters: True
```

### -상단

정렬 된 개체 배열의 시작 부분에서 가져올 개체 수를 지정 합니다. 이로 인해 안정적으로 정렬 됩니다.

이 매개 변수는 PowerShell 6.0에서 도입 되었습니다.

```yaml
Type: System.Int32
Parameter Sets: Top
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -고유

에서 `Sort-Object` 중복을 제거 하 고 컬렉션의 고유한 멤버만 반환 함을 나타냅니다. 고유 값의 첫 번째 인스턴스는 정렬 된 출력에 포함 됩니다.

**Unique** 는 대/소문자를 구분 하지 않습니다. 문자 대/소문자만 다른 문자열은 동일한 것으로 간주 됩니다.
예를 들면 문자 및 문자입니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: All
Accept pipeline input: False
Accept wildcard characters: False
```

### -안정적인

정렬 된 개체는 정렬 기준이 같을 때 받은 순서 대로 배달 됩니다.

이 매개 변수는 PowerShell v 6.2.0에서 추가 되었습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Default
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

### System.web. PSObject

정렬할 개체를 파이프 할 수 있습니다 `Sort-Object` .

## 출력

### System.web. PSObject

`Sort-Object` 정렬 된 개체를 반환 합니다.

## 참고

`Sort-Object`Cmdlet은 명령에 지정 된 속성 또는 개체 유형에 대 한 기본 정렬 속성을 기준으로 개체를 정렬 합니다. 기본 정렬 속성은 `PropertySet` 파일의 명명 된를 사용 하 여 정의 됩니다 `DefaultKeyPropertySet` `types.ps1xml` . 자세한 내용은 [about_Types.ps1xml](/powershell/module/Microsoft.PowerShell.Core/About/about_Types.ps1xml)을 참조 하세요.

개체에 지정 된 속성 중 하나가 없는 경우 해당 개체의 속성 값은에서 `Sort-Object` **Null** 로 해석 되 고 정렬 순서의 끝에 배치 됩니다.

사용할 수 있는 정렬 속성이 없으면 PowerShell에서 개체 자체를 비교 하려고 시도 합니다.
`Sort-Object` 각 속성에 대해 **Compare** 메서드를 사용 합니다. 속성이 **IComparable** 을 구현 하지 않는 경우 cmdlet은 속성 값을 문자열로 변환 하 **고 System.string에 대해** **Compare** 메서드를 사용 합니다. 자세한 내용은 [PSObject. CompareTo (Object) 메서드](/dotnet/api/system.management.automation.psobject.compareto)를 참조 하세요.

**상태** 와 같은 열거 된 속성을 기준으로 정렬 하는 경우 `Sort-Object` 열거형 값을 기준으로 정렬 합니다. Windows 서비스의 경우 **중지** 됨의 값은 **1** 이 고 **실행** 값은 **4** 입니다.
열거 된 값 때문에 **중지** 됨이 **실행** 되기 전에 정렬 됩니다. 자세한 내용은 [ServiceControllerStatus](/dotnet/api/system.serviceprocess.servicecontrollerstatus)를 참조 하세요.

안정적인 정렬을 수행할 때 정렬 알고리즘의 성능이 느려집니다.

## 관련 링크

[about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md)

[about_Types.ps1xml](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md)

[Compare-Object](Compare-Object.md)

[ForEach-Object](../Microsoft.PowerShell.Core/ForEach-Object.md)

[Group-Object](Group-Object.md)

[Measure-Object](Measure-Object.md)

[New-Object](New-Object.md)

[Select-Object](Select-Object.md)

[Tee-Object](Tee-Object.md)
