---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: DSC WindowsOptionalFeature 리소스
ms.openlocfilehash: 7312edcaeb47427bf4736f466a9ed41bd7c31f6a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "71954650"
---
# <a name="dsc-windowsoptionalfeature-resource"></a>DSC WindowsOptionalFeature 리소스

> 적용 대상: Windows PowerShell 5.x

PowerShell DSC(필요한 상태 구성)의 **WindowsOptionalFeature** 리소스에서는 대상 노드에서 선택적 기능을 사용할 수 있도록 설정하는 메커니즘을 제공합니다.

## <a name="syntax"></a>구문

```Syntax
WindowsOptionalFeature [string] #ResourceName
{
    Name = [string]
    [ Source = [string[]] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ RemoveFilesOnDisable = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Enable | Disable }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>속성

|속성 |설명 |
|---|---|
|이름 |사용 또는 사용하지 않도록 설정하려는 기능의 이름을 나타냅니다. |
|원본 |구현되지 않았습니다. |
|NoWindowsUpdateCheck |기능을 사용하도록 설정하기 위해 원본 파일을 검색할 때 DISM에서 WU(Windows 업데이트)에 연결하는지 여부를 지정합니다. `$true`이면 DISM에서 WU에 연결하지 않습니다. |
|RemoveFilesOnDisable |`$true`Ensure**가** Absent**로 설정되어 있을 경우** 로 설정하여 기능과 관련된 모든 파일을 제거합니다. |
|로그 수준 |로그에 표시되는 최대 출력 수준입니다. 허용되는 값은 **ErrorsOnly**, **ErrorsAndWarning** 및 **ErrorsAndWarningAndInformation**. |
|LogPath |리소스 공급자가 작업을 기록할 로그 파일의 경로입니다. |

## <a name="common-properties"></a>공용 속성

|속성 |설명 |
|---|---|
|DependsOn |이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다. 예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 ID가 ResourceName이고 해당 형식이 ResourceType일 경우, 이 속성을 사용하기 위한 구문은 `DependsOn = "[ResourceType]ResourceName"`입니다. |
|Ensure |기능을 사용하도록 설정할지 여부를 지정합니다. 기능을 사용하도록 설정하려면 이 속성을 _Enable_로 설정합니다. 기능을 사용하지 않도록 설정하려면 이 속성을 _Disable_로 설정합니다. 기본값은 _Enable_입니다. |
|PsDscRunAsCredential |전체 리소스를 실행하기 위한 자격 증명을 설정합니다. |

> [!NOTE]
> **PsDscRunAsCredential** 공용 속성은 다른 자격 증명의 컨텍스트에서 DSC 리소스를 실행할 수 있도록 WMF 5.0에 추가되었습니다. 자세한 내용은 [ DSC 리소스로 자격 증명 사용](../../../configurations/runasuser.md)을 참조하세요.