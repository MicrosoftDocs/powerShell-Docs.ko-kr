---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: DSC WindowsPackageCab 리소스
ms.openlocfilehash: 035944e7ca5c7469250c48a19b79f2f2d5d38e9a
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047586"
---
# <a name="dsc-windowspackagecab-resource"></a>DSC WindowsPackageCab 리소스

> 적용 대상: Windows PowerShell 5.1 이상

Windows PowerShell DSC(Desired State Configuration)의 **WindowsPackageCab** 리소스는 대상 노드에서 Windows 캐비닛(.cab) 패키지를 설치하거나 제거하는 메커니즘을 제공합니다.

대상 노드에는 DISM PowerShell 모듈이 설치되어 있어야 합니다. 자세한 내용은 [Windows PowerShell에서 DISM 사용](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/use-dism-in-windows-powershell-s14)을 참조하세요.


## <a name="syntax"></a>구문

```
{
    Name = [string]
    Ensure = [string] { Absent | Present }
    SourcePath = [string]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a>속성

|  속성  |  설명   |
|---|---|
| 이름| 특정 상태가 되게 할 패키지의 이름을 나타냅니다.|
| Ensure| 패키지가 설치되어 있는지 여부를 나타냅니다. 패키지가 설치되어 있지 않도록 하려면(또는 설치되어 있다면 패키지를 제거) 이 속성을 "Absent"으로 설정합니다. 패키지가 설치되어 있도록 하려면 이 속성을 "Present"(기본값)으로 설정합니다.|
| 경로| 패키지가 있는 경로 나타냅니다.|
| LogPath| 패키지를 설치하거나 제거하기 위해 공급자가 로그 파일을 저장하도록 하려는 전체 경로를 나타냅니다.|
| DependsOn | 이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다. 예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 ID가 **ResourceName**이고 해당 형식이 **ResourceType**일 경우, 이 속성을 사용하는 구문은 `DependsOn = "[ResourceType]ResourceName"``입니다.|

## <a name="example"></a>예제

다음 예제 구성에서는 입력 매개 변수를 사용하며 `$Name` 매개 변수로 지정된 .cab 파일이 설치되어 있는지를 확인합니다.

```powershell
Configuration Sample_WindowsPackageCab
{
    param
    (
        [Parameter (Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $Name,

        [Parameter (Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $SourcePath,

        [Parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $LogPath
    )

    Import-DscResource -ModuleName 'PSDscResources'

    WindowsPackageCab WindowsPackageCab1
    {
        Name = $Name
        Ensure = 'Present'
        SourcePath = $SourcePath
        LogPath = $LogPath
    }
}
```