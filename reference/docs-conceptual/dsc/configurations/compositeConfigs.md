---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: 구성 중첩
description: DSC를 사용하면 다른 구성 내에 구성을 중첩하여 복합 구성을 만들 수 있습니다.
ms.openlocfilehash: d7a81cb9673126e92e9185aacf19c5c7c17da8ca
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92667422"
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

이 예에서 `FileConfig`는 `File` 리소스 블록에서 **SourcePath** 및 **DestinationPath** 속성에 대한 값으로 사용되는 두 개의 필수 매개 변수 즉, **CopyFrom** 및 **CopyTo** 를 사용합니다. `NestedConfig` 구성은 마치 리소스인 것처럼 `FileConfig`를 호출합니다. `NestedConfig` 리소스 블록의 속성( **CopyFrom** 및 **CopyTo** )은 `FileConfig` 구성의 매개 변수입니다.

DSC는 지금은 중첩된 구성 내의 중첩 구성을 지원하지 않습니다. 구성을 하나만 계층 깊이로만 중첩할 수 있습니다.

## <a name="see-also"></a>참고 항목

- [복합 리소스--DSC 구성을 리소스로 사용](../resources/authoringResourceComposite.md)
