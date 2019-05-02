---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: ff2c2bd7369893d72db001ecabf63991ded0bfd5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058984"
---
# <a name="unified-and-consistent-state-and-status-representation"></a>통합되고 일관된 상태 및 상태 표현

이번 릴리스에서는 자동화 빌드 LCM 상태 및 DSC 상태에 대한 일련의 기능이 향상되었습니다. 여기에는 통합되고 일관된 상태 및 상태 표현, `Get-DscConfigurationStatus` cmdlet에서 반환하는 상태 개체의 관리 가능한 datetime 속성 및 `Get-DscLocalConfigurationManager` cmdlet에서 반환하는 향상된 LCM 상태 세부 정보 속성이 포함됩니다.

다음 규칙에 따라 LCM 상태 및 DSC 작업 상태의 표현을 다시 찾아 통합합니다.

1. 처리되지 않은 리소스는 LCM 상태 및 DSC 상태에 영향을 주지 않습니다.
2. LCM은 다시 부팅을 요청하는 리소스가 발견되면 추가 리소스 처리를 중지합니다.
3. 다시 부팅을 요청하는 리소스는 실제로 다시 부팅된 다음에야 원하는 상태가 됩니다.
4. 실패한 리소스가 발견되면 LCM은 추가 리소스가 실패 리소스에 종속되지 않는 한 계속 처리합니다.
5. `Get-DscConfigurationStatus` cmdlet에서 반환하는 전체 상태는 모든 리소스 상태의 상위 집합입니다.
6. PendingReboot 상태는 PendingConfiguration 상태의 상위 집합입니다.

다음 표에서는 몇 가지 일반적인 시나리오의 결과 상태 및 상태 관련 속성을 보여 줍니다.

| 시나리오                        | LCMState             | 상태     | 다시 부팅 요청 | ResourcesInDesiredState   | ResourcesNotInDesiredState |
|---------------------------------|----------------------|------------|---------------|------------------------------|--------------------------------|
| S<sub>i</sub>                   | 유휴 상태                 | Success    | $false        | S                            | $null                          |
| F<sub>i</sub>                   | PendingConfiguration | 실패    | $false        | $null                        | F                              |
| S,F                             | PendingConfiguration | 실패    | $false        | S                            | F                              |
| F,S                             | PendingConfiguration | 실패    | $false        | S                            | F                              |
| S<sub>1</sub>, F, S<sub>2</sub> | PendingConfiguration | 실패    | $false        | S<sub>1</sub>, S<sub>2</sub> | F                              |
| F<sub>1</sub>, S, F<sub>2</sub> | PendingConfiguration | 실패    | $false        | S                            | F<sub>1</sub>, F<sub>2</sub>   |
| S, r                            | PendingReboot        | Success    | $true         | S                            | r                              |
| F, r                            | PendingReboot        | 실패    | $true         | $null                        | F, r                           |
| r, S                            | PendingReboot        | Success    | $true         | $null                        | r                              |
| r, F                            | PendingReboot        | Success    | $true         | $null                        | r                              |

- S<sub>i</sub>: 제대로 적용된 일련의 리소스
- F<sub>i</sub>: 제대로 적용되지 않은 일련의 리소스
- r: 다시 부팅이 필요한 리소스

```powershell
$LCMState = (Get-DscLocalConfigurationManager).LCMState
$Status = (Get-DscConfigurationStatus).Status

$RebootRequested = (Get-DscConfigurationStatus).RebootRequested

$ResourcesInDesiredState = (Get-DscConfigurationStatus).ResourcesInDesiredState

$ResourcesNotInDesiredState = (Get-DscConfigurationStatus).ResourcesNotInDesiredState
```

## <a name="enhancement-in-get-dscconfigurationstatus-cmdlet"></a>Get-DscConfigurationStatus cmdlet의 향상된 기능

이번 릴리스에서는 `Get-DscConfigurationStatus` cmdlet의 몇 가지 기능이 향상되었습니다. 이전에는 cmdlet에서 반환하는 개체의 StartDate 속성이 String 형식이었습니다. 지금은 Datetime 형식이어서 Datetime 개체의 기본 속성에 따라 복잡한 선택 및 필터링을 더 쉽게 수행할 수 있습니다.

```powershell
(Get-DscConfigurationStatus).StartDate | Format-List *

DateTime    : Friday, November 13, 2015 1:39:44 PM
Date        : 11/13/2015 12:00:00 AM
Day         : 13
DayOfWeek   : Friday
DayOfYear   : 317
Hour        : 13
Kind        : Local
Millisecond : 886
Minute      : 39
Month       : 11
Second      : 44
Ticks       : 635830187848860000
TimeOfDay   : 13:39:44.8860000
Year        : 2015
```

다음 예제에서는 오늘과 같은 요일에 수행된 모든 DSC 작업 레코드를 반환합니다.

```powershell
(Get-DscConfigurationStatus –All) | Where-Object { $_.startdate.dayofweek -eq (Get-Date).DayOfWeek }
```

노드의 구성을 변경하지 않는 작업(예: 읽기 전용 작업)의 레코드는 제거됩니다. 따라서, `Test-DscConfiguration`, `Get-DscConfiguration` 작업이 `Get-DscConfigurationStatus` cmdlet에서 반환된 개체에서 더 이상 저하되지 않습니다. 메타 구성 설정 작업의 레코드는 `Get-DscConfigurationStatus` cmdlet의 반환 값에 추가됩니다.

다음은 `Get-DscConfigurationStatus –All` cmdlet에서 반환된 결과의 예입니다.

```output
All configuration operations:

Status StartDate Type RebootRequested
------ --------- ---- ---------------
Success 11/13/2015 11:38:16 AM Consistency False
Success 11/13/2015 11:23:16 AM Reboot False
Success 11/13/2015 11:21:43 AM Reboot True
Success 11/13/2015 11:20:44 AM Initial True
Success 11/13/2015 11:20:44 AM LocalConfigurationManager False
```

## <a name="enhancement-in-get-dsclocalconfigurationmanager-cmdlet"></a>Get-DscLocalConfigurationManager cmdlet에서 향상된 기능

LCMStateDetail의 새 필드가 `Get-DscLocalConfigurationManager` cmdlet에서 반환된 개체에 추가되었습니다. 이 필드는 LCMState가 “사용 중”일 때 채워지며. 다음 cmdlet으로 검색할 수 있습니다.

```powershell
(Get-DscLocalConfigurationManager).LCMStateDetail
```

다음은 원격 노드에서 두 번 다시 부팅해야 하는 구성에 대한 연속 모니터링의 예제 출력입니다.

```output
Start a configuration that requires two reboots

Monitor LCM State:
LCM State: Busy, LCM is applying a new configuration.
LCM State: PendingReboot,
Machine is rebooting...
LCM State: Busy, LCM is continuing applying configuration after last reboot.
LCM State: PendingReboot,
Machine is rebooting...
LCM State: Busy, LCM is continuing applying configuration after last reboot.
LCM State: Idle,
LCM State: Busy, LCM is performing a consistency check.
LCM State: Idle,
```
