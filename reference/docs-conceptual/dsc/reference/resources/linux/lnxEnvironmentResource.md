---
ms.date: 07/17/2020
ms.topic: reference
title: Linux nxEnvironment 리소스용 DSC
description: Linux nxEnvironment 리소스용 DSC
ms.openlocfilehash: 86ed538732254967cb4a3bb55af4f6b179947e52
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92644679"
---
# <a name="dsc-for-linux-nxenvironment-resource"></a>Linux nxEnvironment 리소스용 DSC

PowerShell DSC(필요한 상태 구성)의 **nxEnvironment** 리소스에서는 Linux 노드 상의 시스템 환경 변수를 관리하는 메커니즘을 제공합니다.

## <a name="syntax"></a>구문

```Syntax
nxEnvironment <string> #ResourceName
{
    Name = <string>
    [ Value = <string>
    [ Path = <bool> }
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a>속성

|속성 |Description |
|---|---|
|속성 |특정 상태를 확인하려는 환경 변수의 이름을 나타냅니다. |
|값 |환경 변수에 할당할 값입니다. |
|경로 |구성 중인 환경 변수를 정의합니다. 변수가 **Path** 변수이면 이 속성을 `$true`로 설정하고, 그렇지 않으면 `$false`로 설정합니다. 기본값은 `$false`입니다. 구성되고 있는 변수가 **Path** 변수라면, **Value** 속성을 통해 제공된 값은 기존 값에 추가됩니다. |

## <a name="common-properties"></a>공용 속성

|속성 |Description |
|---|---|
|DependsOn |이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다. 예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 ID가 ResourceName이고 해당 형식이 ResourceType일 경우, 이 속성을 사용하기 위한 구문은 `DependsOn = "[ResourceType]ResourceName"`입니다. |
|Ensure |해당 변수가 존재하는지를 확인할지 여부를 결정합니다. 변수가 존재하도록 하려면 이 속성을 **Present** 로 설정합니다. 변수가 존재하지 않도록 하려면 이 속성을 **Absent** 로 설정합니다. 기본값은 **Present** 입니다. |

## <a name="additional-information"></a>추가 정보

- **Path** 가 없거나 `$false`로 설정되어 있으면, 환경 변수는 `/etc/environment`에서 관리됩니다.
  프로그램 또는 스크립트가 구성을 통해 관리되는 환경 변수에 액세스하도록 `/etc/environment` 파일을 소싱해야 할 수도 있습니다.
- **Path** 가 `$true`로 설정된 경우, 환경 변수는 `/etc/profile.d/DSCenvironment.sh` 파일에서 관리됩니다. 이 파일은 존재하지 않는 경우 만들어집니다. **Ensure** 가 **Absent** 로 설정되어 있고, **Path** 가 `$true`로 설정되어 있는 경우, 기존 환경 변수는 다른 파일에서는 제거되지 않고 `/etc/profile.d/DSCenvironment.sh`에서만 제거됩니다.

## <a name="example"></a>예제

다음 예제에서는 **nxEnvironment** 리소스를 사용하여 **TestEnvironmentVariable** 이 존재하고 "Test-Value" 값을 갖도록 하는 방법을 보여 줍니다. **TestEnvironmentVariable** 이 존재하지 않을 경우, 자동으로 만들어집니다.

```powershell
Import-DSCResource -Module nx

nxEnvironment EnvironmentExample
{
    Ensure = "Present"
    Name = "TestEnvironmentVariable"
    Value = "TestValue"
}
```
