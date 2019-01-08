---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: DSC WindowsOptionalFeatureSet 리소스
ms.openlocfilehash: c27d026e01bbb443a82112e37f1d199fb3482e49
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047613"
---
# <a name="dsc-windowsoptionalfeatureset-resource"></a>DSC WindowsOptionalFeatureSet 리소스

> 적용 대상: Windows Powershell 5.0

Windows PowerShell DSC(필요한 상태 구성)의 **WindowsOptionalFeatureSet** 리소스에서는 대상 노드에서 선택적 기능을 사용할 수 있도록 설정하는 메커니즘을 제공합니다.
이 리소스는 `Name` 속성에 지정된 각 기능에 대해 [WindowsOptionalFeature 리소스](windowsOptionalFeatureResource.md)를 호출하는 [복합 리소스](../../../resources/authoringResourceComposite.md)입니다.

여러 선택적 Windows 기능을 동일한 상태로 구성하려는 경우 이 리소스를 사용합니다.

## <a name="syntax"></a>구문

```
WindowsOptionalFeature [string] #ResourceName
{
    Name = [string[]]
    [ Ensure = [string] { Enable | Disable }  ]
    [ Source = [string] ]
    [ RemoveFilesOnDisable = [bool] ]
    [ LogPath = [string] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ DependsOn = [string[]] ]

}
```

## <a name="properties"></a>속성

|  속성  |  설명   |
|---|---|
| 이름| 사용 또는 사용하지 않도록 설정하려는 기능의 이름을 나타냅니다.|
| Ensure| 기능을 사용하도록 설정할지 여부를 지정합니다. 기능을 사용하도록 설정하려면 이 속성을 "Enable"로 설정하고 기능을 사용하지 않도록 설정하려면 속성을 "Disable"로 설정합니다.|
| 원본| 구현되지 않았습니다.|
| NoWindowsUpdateCheck| 기능을 사용하도록 설정하기 위해 원본 파일을 검색할 때 DISM에서 WU(Windows 업데이트)에 연결하는지 여부를 지정합니다. $true이면 DISM에서 WU에 연결하지 않습니다.|
| RemoveFilesOnDisable| 기능을 사용하지 않도록 설정할 때(즉, **Ensure**를 "Absent"로 설정할 때) 기능과 연결된 파일을 모두 제거하려면 **$true**로 설정합니다.|
| 로그 수준| 로그에 표시되는 최대 출력 수준입니다. 허용 되는 값은: "가능한" (오류만 기록), "ErrorsAndWarning" (오류 및 경고 기록) 및 "ErrorsAndWarningAndInformation" (오류, 경고 및 디버그 정보 기록).|
| LogPath| 리소스 공급자가 작업을 기록할 로그 파일의 경로입니다.|
| DependsOn| 이 리소스를 구성하기 전에 다른 리소스의 구성을 실행해야 함을 지정합니다. 예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 ID가 __ResourceName__이고 해당 형식이 __ResourceType__일 경우, 이 속성을 사용하기 위한 구문은 `DependsOn = "[ResourceType]ResourceName"`입니다.|
