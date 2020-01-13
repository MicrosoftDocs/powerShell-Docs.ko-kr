---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: 구성 중첩
ms.openlocfilehash: 07e4fb5b9d406153d2fbb4285e28b8d1f0dfdcf5
ms.sourcegitcommit: 1b88c280dd0799f225242608f0cbdab485357633
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75417859"
---
# <a name="nesting-dsc-configurations"></a>DSC 구성 중첩

중첩된 구성(복합 구성이라고도 함)은 다른 구성 내에서 마치 리소스인 것처럼 호출되는 구성입니다. 두 구성이 모두 같은 파일에 정의되어 있어야 합니다.

간단한 예를 살펴보겠습니다.

```powershell
Configuration FileConfig
{
    param (
        [Parameter(Mandatory = $true)]
        [String] $CopyFrom,

        [Parameter(Mandatory = $true)]
        [String] $CopyTo
    )

    Import-DscResource -ModuleName PSDesiredStateConfiguration

    File FileTest
    {
        SourcePath = $CopyFrom
        DestinationPath = $CopyTo
        Ensure = 'Present'
    }
}

Configuration NestedFileConfig
{
    Node localhost
    {
        FileConfig NestedConfig
        {
            CopyFrom = 'C:\Test\TestFile.txt'
            CopyTo = 'C:\Test2'
        }
    }
}
```

이 예에서 `FileConfig`는 `File` 리소스 블록에서 **SourcePath** 및 **DestinationPath** 속성에 대한 값으로 사용되는 두 개의 필수 매개 변수 즉, **CopyFrom** 및 **CopyTo**를 사용합니다. `NestedConfig` 구성은 마치 리소스인 것처럼 `FileConfig`를 호출합니다. `NestedConfig` 리소스 블록의 속성(**CopyFrom** 및 **CopyTo**)은 `FileConfig` 구성의 매개 변수입니다.

DSC는 지금은 중첩된 구성 내의 중첩 구성을 지원하지 않습니다. 구성을 하나만 계층 깊이로만 중첩할 수 있습니다.

## <a name="see-also"></a>참고 항목

- [복합 리소스--DSC 구성을 리소스로 사용](../resources/authoringResourceComposite.md)