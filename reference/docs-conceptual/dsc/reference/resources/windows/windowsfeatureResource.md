---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: DSC WindowsFeature 리소스
ms.openlocfilehash: 7f9b200b4d10aef6c8a3f76c497f4d60e8062cb5
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83557400"
---
# <a name="dsc-windowsfeature-resource"></a>DSC WindowsFeature 리소스

> 적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.x

PowerShell DSC(필요한 상태 구성)의 **WindowsFeature** 리소스에서는 대상 노드에서 역할 및 기능이 추가 또는 제거되었는지를 확인하는 메커니즘을 제공합니다.

## <a name="syntax"></a>구문

```Syntax
WindowsFeature [string] #ResourceName
{
    Name = [string]
    [ Credential = [PSCredential] ]
    [ IncludeAllSubFeature = [bool] ]
    [ LogPath = [string] ]
    [ Source = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>속성

|속성 |Description |
|---|---|
|속성 |추가되었는지 또는 제거되었는지를 확인하려는 역할이나 기능의 이름을 나타냅니다. 이것은 **Get-WindowsFeature** cmdlet의 [Name](/powershell/module/servermanager/Get-WindowsFeature) 속성과 동일하며, 역할이나 기능의 표시 이름은 아닙니다. |
|자격 증명 |역할 또는 기능을 추가 또는 제거하는 데 사용할 자격 증명을 나타냅니다. |
|IncludeAllSubFeature |`$true`Name**속성으로 지정하는 기능의 상태와 함께 모든 필수 하위 기능의 상태를 보증하려면 이 속성을**로 설정하세요. |
|LogPath |리소스 공급자가 작업을 로그하기를 원하는 로그 파일의 경로를 나타냅니다. |
|원본 |필요한 경우 설치에 사용할 소스 파일의 위치를 나타냅니다. |

## <a name="common-properties"></a>공용 속성

|속성 |Description |
|---|---|
|DependsOn |이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다. 예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 ID가 ResourceName이고 해당 형식이 ResourceType일 경우, 이 속성을 사용하기 위한 구문은 `DependsOn = "[ResourceType]ResourceName"`입니다. |
|Ensure |역할이나 기능이 추가되었는지 여부를 나타냅니다. 역할이나 기능이 추가되도록 하려면 이 속성을 **Present**로 설정합니다. 역할이나 기능이 제거되도록 하려면 이 속성을 **Absent**로 설정합니다. 기본값은 **Present**입니다. |
|PsDscRunAsCredential |전체 리소스를 실행하기 위한 자격 증명을 설정합니다. |

> [!NOTE]
> **PsDscRunAsCredential** 공용 속성은 다른 자격 증명의 컨텍스트에서 DSC 리소스를 실행할 수 있도록 WMF 5.0에 추가되었습니다. 자세한 내용은 [ DSC 리소스로 자격 증명 사용](../../../configurations/runasuser.md)을 참조하세요.

## <a name="example"></a>예제

```powershell
WindowsFeature RoleExample
{
    Ensure = "Present"
    # Alternatively, to ensure the role is uninstalled, set Ensure to "Absent"
    Name = "Web-Server" # Use the Name property from Get-WindowsFeature
}
```
