---
ms.date: 07/16/2020
keywords: dsc,powershell,configuration,setup
title: DSC WindowsOptionalFeatureSet 리소스
ms.openlocfilehash: e4f88f1cae6d7ddb3596ab4f27eb3766259f1a31
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464165"
---
# <a name="dsc-windowsoptionalfeatureset-resource"></a>DSC WindowsOptionalFeatureSet 리소스

> 적용 대상: Windows PowerShell 5.x

Windows PowerShell DSC(필요한 상태 구성)의 **WindowsOptionalFeatureSet** 리소스에서는 대상 노드에서 선택적 기능을 사용할 수 있도록 설정하는 메커니즘을 제공합니다. 이 리소스는 **Name** 속성에 지정된 각 기능에 대해 [WindowsOptionalFeature 리소스](windowsOptionalFeatureResource.md)를 호출하는 [복합 리소스](../../../resources/authoringResourceComposite.md)입니다.

여러 선택적 Windows 기능을 동일한 상태로 구성하려는 경우 이 리소스를 사용합니다.

## <a name="syntax"></a>구문

```Syntax
WindowsOptionalFeatureSet [string] #ResourceName
{
    Name = [string[]]
    [ RemoveFilesOnDisable = [bool] ]
    [ LogPath = [string] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Enable | Disable }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>속성

|속성 |Description |
|---|---|
|속성 |사용 또는 사용하지 않도록 설정하려는 기능의 이름을 나타냅니다. |
|NoWindowsUpdateCheck |기능을 사용하도록 설정하기 위해 원본 파일을 검색할 때 DISM에서 WU(Windows 업데이트)에 연결하는지 여부를 지정합니다. `$true`이면 DISM에서 WU에 연결하지 않습니다. |
|RemoveFilesOnDisable |`$true`Ensure**가 **Absent**로 설정되어 있을 경우 **로 설정하여 기능과 관련된 모든 파일을 제거합니다. |
|LogLevel |로그에 표시되는 최대 출력 수준입니다. 허용되는 값은 **ErrorsOnly**, **ErrorsAndWarning** 및 **ErrorsAndWarningAndInformation**. |
|LogPath |리소스 공급자가 작업을 기록할 로그 파일의 경로입니다. |

## <a name="common-properties"></a>공용 속성

|속성 |Description |
|---|---|
|DependsOn |이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다. 예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 ID가 ResourceName이고 해당 형식이 ResourceType일 경우, 이 속성을 사용하기 위한 구문은 `DependsOn = "[ResourceType]ResourceName"`입니다. |
|Ensure |기능을 사용하도록 설정할지 여부를 지정합니다. 기능을 사용하도록 설정하려면 이 속성을 **Enable**로 설정합니다. 기능을 사용하지 않도록 설정하려면 이 속성을 **Disable**로 설정합니다. 기본값은 **Enable**입니다. |
|PsDscRunAsCredential |전체 리소스를 실행하기 위한 자격 증명을 설정합니다. |

> [!NOTE]
> **PsDscRunAsCredential** 공용 속성은 다른 자격 증명의 컨텍스트에서 DSC 리소스를 실행할 수 있도록 WMF 5.0에 추가되었습니다. 자세한 내용은 [ DSC 리소스로 자격 증명 사용](../../../configurations/runasuser.md)을 참조하세요.
