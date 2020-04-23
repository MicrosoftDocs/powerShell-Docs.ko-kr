---
ms.date: 11/22/2019
keywords: powershell,cmdlet
title: 형식 명령을 사용하여 출력 보기 변경
ms.openlocfilehash: f270d5ec5efe5caf506d6a8a45285990996f6ae6
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2020
ms.locfileid: "74417598"
---
# <a name="using-format-commands-to-change-output-view"></a>형식 명령을 사용하여 출력 보기 변경

PowerShell에는 특정 개체에 대한 속성 표시 방법을 제어할 수 있는 일련의 cmdlet이 있습니다. 이러한 cmdlet의 이름은 모두 동사 `Format`으로 시작되며, 표시하려는 속성을 선택할 수 있습니다.

```powershell
Get-Command -Verb Format -Module Microsoft.PowerShell.Utility
```

```Output
CommandType     Name               Version    Source
-----------     ----               -------    ------
Cmdlet          Format-Custom      6.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Format-Hex         6.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Format-List        6.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Format-Table       6.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Format-Wide        6.1.0.0    Microsoft.PowerShell.Utility
```

이 문서에서는 `Format-Wide`, `Format-List` 및 `Format-Table` cmdlet에 대해 설명합니다.

PowerShell의 각 개체 형식에는 표시할 속성을 지정하지 않는 경우에 사용되는 기본 속성이 있습니다. 또한 각 cmdlet은 동일한 **Property** 매개 변수를 사용하여 표시할 속성을 지정합니다. `Format-Wide`는 하나의 속성만 표시하기 때문에 해당 **Property** 매개 변수가 하나의 값만 사용하지만 `Format-List` 및 `Format-Table`의 Property 매개 변수는 속성 이름 목록을 사용합니다.

이 예에서 `Get-Process` cmdlet의 기본 출력은 두 개의 Internet Explorer 인스턴스가 실행 중임을 보여줍니다.

```powershell
Get-Process -Name iexplore
```

**Process** 개체의 기본 형식은 다음과 같은 속성을 표시합니다.

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     32    25.52      10.25      13.11   12808   1 iexplore
     52    11.46      26.46       3.55   21748   1 iexplore
```

## <a name="using-format-wide-for-single-item-output"></a>Format-Wide를 사용하여 단일 항목 출력

기본적으로 `Format-Wide` cmdlet은 개체의 기본 속성만 표시합니다. 다음과 같이 각 개체와 연결된 정보는 하나의 열에 표시됩니다.

```powershell
Get-Command -Verb Format | Format-Wide
```

```Output
Format-Custom          Format-Hex
Format-List            Format-Table
Format-Wide
```

다음과 같이 기본 속성이 아닌 속성을 지정할 수도 있습니다.

```powershell
Get-Command -Verb Format | Format-Wide -Property Noun
```

```Output
Custom                 Hex
List                   Table
Wide
```

### <a name="controlling-format-wide-display-with-column"></a>열이 포함된 Format-Wide 표시 제어

`Format-Wide` cmdlet을 사용하면 한 번에 하나의 속성만 표시할 수 있습니다. 이렇게 하면 여러 열에 많은 목록을 표시하는 데 유용합니다.

```powershell
Get-Command -Verb Format | Format-Wide -Property Noun -Column 3
```

```Output
Custom                 Hex                  List
Table                  Wide

```

## <a name="using-format-list-for-a-list-view"></a>Format-List를 사용하여 목록 보기

`Format-List` cmdlet은 다음과 같이 각 속성에 레이블이 지정되어 있고 이러한 각 속성이 서로 다른 줄에 표시되는 목록 형식으로 개체를 표시합니다.

```powershell
Get-Process -Name iexplore | Format-List
```

```Output
Id      : 12808
Handles : 578
CPU     : 13.140625
SI      : 1
Name    : iexplore

Id      : 21748
Handles : 641
CPU     : 3.59375
SI      : 1
Name    : iexplore
```

다음과 같이 속성을 원하는 대로 지정할 수 있습니다.

```powershell
Get-Process -Name iexplore | Format-List -Property ProcessName,FileVersion,StartTime,Id
```

```Output
ProcessName : iexplore
FileVersion : 11.00.18362.1 (WinBuild.160101.0800)
StartTime   : 10/22/2019 11:23:58 AM
Id          : 12808

ProcessName : iexplore
FileVersion : 11.00.18362.1 (WinBuild.160101.0800)
StartTime   : 10/22/2019 11:23:57 AM
Id          : 21748
```

### <a name="getting-detailed-information-by-using-format-list-with-wildcards"></a>와일드카드와 함께 Format-List를 사용하여 자세한 정보 보기

`Format-List` cmdlet을 사용하면 와일드카드를 해당 **Property** 매개 변수의 값으로 사용할 수 있습니다. 이 경우 자세한 정보를 표시할 수 있습니다. 필요한 것보다 많은 정보가 개체에 포함되는 경우가 종종 있는데, 이는 PowerShell이 기본적으로 모든 속성 값을 표시하지는 않기 때문입니다. 개체의 모든 속성을 표시하려면 `Format-List -Property *` 명령을 사용합니다. 다음 명령은 단일 프로세스의 출력을 위해 60개 이상의 줄을 생성합니다.

```powershell
Get-Process -Name iexplore | Format-List -Property *
```

`Format-List` 명령은 자세한 정보를 표시하는 데 유용하지만 많은 항목을 포함하는 개요를 출력하려는 경우에는 대개 간단한 테이블 형식의 보기가 더 유용합니다.

## <a name="using-format-table-for-tabular-output"></a>Format-Table을 사용하여 표 형식으로 출력

속성 이름이 지정되지 않은 `Format-Table` cmdlet을 사용하여 `Get-Process` 명령의 출력 형식을 지정하면 `Format` cmdlet 없이 이와 같은 작업을 수행할 때와 동일한 내용이 출력됩니다. 기본적으로 PowerShell은 **Process** 개체를 테이블 형식으로 표시합니다.

```powershell
Get-Service -Name win* | Format-Table
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  WinDefend          Windows Defender Antivirus Service
Running  WinHttpAutoProx... WinHTTP Web Proxy Auto-Discovery Se...
Running  Winmgmt            Windows Management Instrumentation
Running  WinRM              Windows Remote Management (WS-Manag...
```

### <a name="improving-format-table-output-autosize"></a>Format-Table 출력 향상(AutoSize)

테이블 형식 보기는 많은 정보를 표시하는 데 유용하지만 열이 너무 좁아 데이터를 모두 표시할 수 없는 경우에는 정보를 해석하기 어려울 수 있습니다. 이전 예에서는 출력이 잘립니다. **명령을 실행할 때**AutoSize`Format-Table` 매개 변수를 지정하면 PowerShell은 표시된 실제 데이터를 기준으로 열 너비를 계산합니다. 그러면 열을 읽을 수 있습니다.

```powershell
Get-Service -Name win* | Format-Table -AutoSize
```

```Output
Status  Name                DisplayName
------  ----                -----------
Running WinDefend           Windows Defender Antivirus Service
Running WinHttpAutoProxySvc WinHTTP Web Proxy Auto-Discovery Service
Running Winmgmt             Windows Management Instrumentation
Running WinRM               Windows Remote Management (WS-Management)
```

`Format-Table` cmdlet을 실행하면 여전히 데이터가 잘릴 수 있지만 화면 끝에 있는 데이터만 잘립니다. 마지막으로 표시되는 속성을 제외하고 속성에는 가장 긴 데이터 요소를 올바로 표시하는 데 필요한 충분한 크기가 지정됩니다.

```powershell
Get-Service -Name win* | Format-Table -Property Name,Status,StartType,DisplayName,DependentServices -AutoSize
```

```Output
Name                 Status StartType DisplayName                               DependentServi
                                                                                ces
----                 ------ --------- -----------                               --------------
WinDefend           Running Automatic Windows Defender Antivirus Service        {}
WinHttpAutoProxySvc Running    Manual WinHTTP Web Proxy Auto-Discovery Service  {NcaSvc, iphl…
Winmgmt             Running Automatic Windows Management Instrumentation        {vmms, TPHKLO…
WinRM               Running Automatic Windows Remote Management (WS-Management) {}
```

`Format-Table` 명령은 속성이 중요도 순으로 나열되어 있다고 가정합니다. 그래서 시작 부분에 가장 가까이 있는 속성을 완전히 표시하려고 합니다. `Format-Table` 명령이 모든 속성을 표시할 수 없는 경우에는 일부 열을 표시에서 제거합니다. **DependentServices** 속성의 이전 예에서 이 동작을 확인할 수 있습니다.

### <a name="wrapping-format-table-output-in-columns-wrap"></a>열에 Format-Table 출력 래핑(Wrap)

`Format-Table`Wrap**매개 변수를 사용하여 긴** 데이터를 해당 표시 열 내에서 래핑할 수 있습니다. 다음과 같이 **Wrap** 매개 변수를 사용하는 경우에도 **AutoSize**를 지정하지 않으면 기본 설정이 사용되기 때문에 예상되는 작업을 수행하지 않아도 됩니다.

```powershell
Get-Service -Name win* | Format-Table -Property Name,Status,StartType,DisplayName,DependentServices -Wrap
```

```Output
Name                 Status StartType DisplayName                               DependentServi
                                                                                ces
----                 ------ --------- -----------                               --------------
WinDefend           Running Automatic Windows Defender Antivirus Service        {}
WinHttpAutoProxySvc Running    Manual WinHTTP Web Proxy Auto-Discovery Service  {NcaSvc,
                                                                                iphlpsvc}
Winmgmt             Running Automatic Windows Management Instrumentation        {vmms,
                                                                                TPHKLOAD,
                                                                                SUService,
                                                                                smstsmgr…}
WinRM               Running Automatic Windows Remote Management (WS-Management) {}
```

**Wrap** 매개 변수를 단독으로 사용하면 프로세스 속도가 크게 느려지지 않습니다. 그러나 **AutoSize**를 사용하여 큰 디렉터리 구조의 재귀 파일 목록 서식을 지정하면 첫 번째 출력 항목을 표시할 때까지 시간이 오래 걸리고 많은 메모리가 사용될 수 있습니다.

시스템 로드에 신경 쓰지 않아도 되는 경우에는 **AutoSize**가 **Wrap** 매개 변수와 함께 정상적으로 작동합니다.
초기 열은 한 줄에 항목을 표시하는 데 필요한 만큼의 너비를 여전히 사용하지만 필요한 경우 마지막 열이 래핑됩니다.

> [!NOTE]
> 가장 넓은 열을 먼저 지정하면 일부 열이 표시되지 않을 수 있습니다. 최상의 결과를 위해서는 가장 작은 데이터 요소를 먼저 지정합니다.

다음 예에서는 너비가 가장 넓은 속성을 먼저 지정합니다.

```powershell
Get-Process -Name iexplore | Format-Table -Wrap -AutoSize -Property FileVersion,Path,Name,Id
```

래핑이 있어도 최종 **ID** 열은 다음과 같이 생략됩니다.

```Output
FileVersion                          Path                                                  Nam
                                                                                           e
-----------                          ----                                                  ---
11.00.18362.1 (WinBuild.160101.0800) C:\Program Files (x86)\Internet Explorer\IEXPLORE.EXE iex
                                                                                           plo
                                                                                           re
11.00.18362.1 (WinBuild.160101.0800) C:\Program Files\Internet Explorer\iexplore.exe       iex
                                                                                           plo
                                                                                           re
```

### <a name="organizing-table-output--groupby"></a>표 형식의 출력 구성(-GroupBy)

표 형식의 출력을 제어하는 데 사용할 수 있는 또 다른 유용한 매개 변수는 **GroupBy**입니다. 특히 긴 표 형식의 목록은 비교하기 어려울 수 있지만 **GroupBy** 매개 변수를 사용하면 속성 값을 기준으로 출력을 그룹화할 수 있습니다. 예를 들어 서비스를 더 쉽게 검사하기 위해 다음과 같이 속성 목록에서 **StartType** 값을 제거하여 해당 서비스를 **StartType**별로 그룹화할 수 있습니다.

```powershell
Get-Service -Name win* | Sort-Object StartType | Format-Table -GroupBy StartType
```

```Output
   StartType: Automatic
Status   Name               DisplayName
------   ----               -----------
Running  WinDefend          Windows Defender Antivirus Service
Running  Winmgmt            Windows Management Instrumentation
Running  WinRM              Windows Remote Management (WS-Managem…

   StartType: Manual
Status   Name               DisplayName
------   ----               -----------
Running  WinHttpAutoProxyS… WinHTTP Web Proxy Auto-Discovery Serv…
```
