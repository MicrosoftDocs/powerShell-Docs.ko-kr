---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/clear-host?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-Host
ms.openlocfilehash: de7dc6027653db063311bd34e1282e3cb5294e92
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599583"
---
# Clear-Host

## 개요

호스트 프로그램의 표시를 지웁니다.

## SYNTAX

```
Clear-Host [<CommonParameters>]
```

## 설명

`Clear-Host`함수는 누적 되었을 수 있는 명령 및 출력을 포함 하 여 현재 디스플레이에서 모든 텍스트를 제거 합니다. 완료되면 명령 프롬프트가 표시됩니다. 함수 이름 또는 해당 별칭인를 사용할 수 있습니다 `cls` .

`Clear-Host` 현재 표시에만 영향을 줍니다. 세션에서 저장된 결과를 삭제하지 않으며 어떤 항목도 제거하지 않습니다. 세션별 항목(예: 변수 및 함수)은 이 함수의 영향을 받지 않습니다.

`Clear-Host`함수의 동작은 호스트 프로그램에 의해 결정 되므로 `Clear-Host` 호스트 프로그램 마다 다르게 작동할 수 있습니다.

## 예제

### 예제 1

```
# Before

PS C:\> Get-Process

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    843      33    14428      22556    99    17.41   1688 CcmExec
     44       6     2196       4964    52     0.23    692 conhost
    646      12     2332       4896    49     1.12    388 csrss
    189      11     2860       7084   114     0.66   2896 csrss
     78      11     1876       4008    42     0.22   4000 csrss
     76       7     1848       5064    54     0.08   1028 dwm
    610      41    23952      44048   208     4.40   2080 explorer
      0       0        0         24     0               0 Idle
    182      32     7692      15980    91     0.23   3056 LogonUI
    186      25     7832      16068    91     0.27   3996 LogonUI
   1272      32    11512      20432    58    25.07    548 lsass
    267      10     3536       6736    34     0.80    556 lsm
    137      17     3520       7472    61     0.05   1220 msdtc
    447      31    70316      84476   201 1,429.67    836 MsMpEng
    265      18     7136      15628   134     2.20   3544 msseces
    248      16     6476       4076    76     0.22   1592 NisSrv
    368      25    61312      65508   614     1.78    848 powershell
    101       8     2304       6624    70     0.64   3648 rdpclip
    258      15     6804      12156    50     2.65    536 services
...

PS C:\> cls
#After

PS C:>
```

이 명령은의 별칭을 사용 하 여 `cls` `Clear-Host` 현재 표시를 지웁니다.

## PARAMETERS

### CommonParameters
이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### 없음

입력을로 파이프 할 수 없습니다 `Clear-Host` .

## 출력

### 없음

`Clear-Host` 출력을 생성 하지 않습니다.

## 참고

`Clear-Host` 는 고급 함수가 아닌 간단한 함수입니다. 따라서 **디버그** 와 같은 일반 매개 변수를 명령에서 사용할 수 없습니다 `Clear-Host` .

## 관련 링크

[Get-Host](../Microsoft.PowerShell.Utility/Get-Host.md)

[Out-Host](Out-Host.md)

[Read-Host](../Microsoft.PowerShell.Utility/Read-Host.md)

[Write-Host](../Microsoft.PowerShell.Utility/Write-Host.md)

