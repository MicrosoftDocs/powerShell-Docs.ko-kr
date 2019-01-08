---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: DSC WindowsFeature 리소스
ms.openlocfilehash: 7a57f4b2797ab3bb202aea8b2543d1e3f14074e9
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047693"
---
# <a name="dsc-windowsfeature-resource"></a>DSC WindowsFeature 리소스

> 적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0

PowerShell DSC(필요한 상태 구성)의 **WindowsFeature** 리소스에서는 대상 노드에서 역할 및 기능이 추가 또는 제거되었는지를 확인하는 메커니즘을 제공합니다.

## <a name="syntax"></a>구문

```
WindowsFeature [string] #ResourceName
{
    Name = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ IncludeAllSubFeature = [bool] ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ Source = [string] ]
}
```

## <a name="properties"></a>속성

|  속성  |  설명   |
|---|---|
| 이름| 추가되었는지 또는 제거되었는지를 확인하려는 역할이나 기능의 이름을 나타냅니다. 이것은 [Get-WindowsFeature](/powershell/module/servermanager/Get-WindowsFeature) cmdlet의 __Name__ 속성과 동일하며, 역할이나 기능의 표시 이름은 아닙니다.|
| 자격 증명| 역할 또는 기능을 추가 또는 제거하는 데 사용할 자격 증명을 나타냅니다.|
| Ensure| 역할이나 기능이 추가되었는지 여부를 나타냅니다. 역할이나 기능이 추가된 것을 보증하려면, 이 속성을 "Present"으로 설정하고, 역할이나 기능이 제거된 것을 보증하려면 이 속성을 "Absent"으로 설정합니다.|
| IncludeAllSubFeature| __Name__ 속성으로 지정하는 기능의 상태와 함께 모든 필수 하위 기능의 상태를 보증하려면 이 속성을 __$true__로 설정하세요.|
| LogPath| 리소스 공급자가 작업을 로그하기를 원하는 로그 파일의 경로를 나타냅니다.|
| DependsOn| 이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다. 예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 ID가 __ResourceName__이고 해당 형식이 __ResourceType__일 경우, 이 속성을 사용하기 위한 구문은 `DependsOn = "[ResourceType]ResourceName"`입니다.|
| 원본| 필요한 경우 설치에 사용할 소스 파일의 위치를 나타냅니다.|

## <a name="example"></a>예제
```powershell
WindowsFeature RoleExample
{
    Ensure = "Present"
    # Alternatively, to ensure the role is uninstalled, set Ensure to "Absent"
    Name = "Web-Server" # Use the Name property from Get-WindowsFeature
}
```