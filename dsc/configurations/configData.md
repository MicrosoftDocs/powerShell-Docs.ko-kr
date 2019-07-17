---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: 구성 데이터 사용
ms.openlocfilehash: 7d13b19ba932d1a818194a221f145fd1a3832547
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67727212"
---
# <a name="using-configuration-data-in-dsc"></a>DSC에서 구성 데이터 사용

> 적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0

기본 제공 DSC**ConfigurationData** 매개 변수를 사용하여 구성 내에서 사용할 수 있는 데이터를 정의할 수 있습니다.
그러면 여러 노드 또는 다양한 환경에 사용할 수 있는 단일 구성을 만들 수 있습니다.
예를 들어 애플리케이션을 개발할 경우 한 구성을 개발 및 프로덕션 환경 모두에 사용하고 구성 데이터를 사용하여 각 환경의 데이터를 지정할 수 있습니다.

이 항목에서는 **ConfigurationData** 해시 테이블의 구조를 설명합니다.
구성 데이터를 사용하는 방법에 대한 예제는 [구성 및 환경 데이터 분리](separatingEnvData.md)를 참조하세요.

## <a name="the-configurationdata-common-parameter"></a>ConfigurationData 일반 매개 변수

DSC 구성에서는 구성을 컴파일할 때 지정하는 일반 매개 변수 **ConfigurationData**를 사용합니다.
구성을 컴파일하는 방법에 대한 자세한 내용은 [DSC 구성](configurations.md)을 참조하세요.

**ConfigurationData** 매개 변수는 **AllNodes**라는 키가 하나 이상 있어야 하는 해시 테이블입니다.
다른 키도 하나 이상 있을 수 있습니다.

> [!NOTE]
> 이 항목의 예제에서는 명명된**AllNodes** 키가 아닌 단일 추가 키 `NonNodeData`를 사용하지만, 추가 키는 원하는 수만큼 포함하고 원하는 이름을 지정할 수 있습니다.

```powershell
$MyData =
@{
    AllNodes = @()
    NonNodeData = ""
}
```

**AllNodes** 키의 값은 배열입니다. 이 배열의 각 요소도 **NodeName**이라는 키가 하나 이상 있어야 하는 해시 테이블입니다.

```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName = "VM-1"
        },


        @{
            NodeName = "VM-2"
        },


        @{
            NodeName = "VM-3"
        }
    );

    NonNodeData = ""
}
```

각 해시 테이블에도 다른 키를 추가할 수 있습니다.

```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName = "VM-1"
            Role     = "WebServer"
        },


        @{
            NodeName = "VM-2"
            Role     = "SQLServer"
        },


        @{
            NodeName = "VM-3"
            Role     = "WebServer"
        }
    );

    NonNodeData = ""
}
```

모든 노드에 한 속성을 적용하려면 **AllNodes** 배열에 **NodeName**이 `*`인 원소를 만들 수 있습니다.
예를 들어 모든 노드에 `LogPath` 속성을 지정하기 위해 다음을 수행할 수 있습니다.

```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName     = "*"
            LogPath      = "C:\Logs"
        },


        @{
            NodeName     = "VM-1"
            Role         = "WebServer"
            SiteContents = "C:\Site1"
            SiteName     = "Website1"
        },


        @{
            NodeName     = "VM-2"
            Role         = "SQLServer"
        },


        @{
            NodeName     = "VM-3"
            Role         = "WebServer"
            SiteContents = "C:\Site2"
            SiteName     = "Website3"
        }
    );
}
```

이 작업은 이름이 `LogPath`이고 값이 `"C:\Logs"`인 속성을 다른 블록 각각에(`VM-1`, `VM-2`, `VM-3`) 추가하는 것과 같습니다.

## <a name="defining-the-configurationdata-hashtable"></a>ConfigurationData 해시 테이블 정의

**ConfigurationData**는 이전 예제에서와 같이 구성과 동일한 스크립트 파일 내에서 변수로 정의할 수도 있고, 별도의 `.psd1` 파일에서 정의할 수도 있습니다.
**ConfigurationData**를 `.psd1` 파일에 정의하려면 구성 데이터를 나타내는 해시 테이블만 포함된 파일을 만듭니다.

예를 들어, 이름이 `MyData.psd1`이고 다음과 같은 내용이 있는 파일을 만들 수 있습니다.

```powershell
@{
    AllNodes =
    @(
        @{
            NodeName    = 'VM-1'
            FeatureName = 'Web-Server'
        },

        @{
            NodeName    = 'VM-2'
            FeatureName = 'Hyper-V'
        }
    )
}
```

## <a name="compiling-a-configuration-with-configuration-data"></a>구성 데이터와 함께 구성 컴파일

구성 데이터를 정의한 구성을 컴파일하려면 **ConfigurationData** 매개 변수의 값으로 구성 데이터를 전달합니다.

이렇게 하면 **AllNodes** 배열의 각 항목에 대해 MOF 파일이 작성됩니다.
각 MOF 파일의 이름은 해당하는 배열 항목의 `NodeName` 속성으로 지정됩니다.

예를 들어 위의 `MyData.psd1` 파일에서와 같이 구성 데이터를 정의하는 경우 해당 구성을 컴파일하면 `VM-1.mof` 및 `VM-2.mof` 파일이 둘 다 작성됩니다.

### <a name="compiling-a-configuration-with-configuration-data-using-a-variable"></a>변수를 사용하여 구성 데이터와 함께 구성 컴파일

구성과 동일한 `.ps1` 파일에 변수로 정의된 구성 데이터를 사용하려면 구성을 컴파일할 때 **ConfigurationData** 매개 변수 값으로 변수 이름을 전달합니다.

```powershell
MyDscConfiguration -ConfigurationData $MyData
```

### <a name="compiling-a-configuration-with-configuration-data-using-a-data-file"></a>데이터 파일을 사용하여 구성 데이터와 함께 구성 컴파일

.psd1 파일에 정의된 구성 데이터를 사용하려면 구성을 컴파일할 때 해당 파일의 경로와 이름을 **ConfigurationData** 매개 변수 값으로 전달합니다.

```powershell
MyDscConfiguration -ConfigurationData .\MyData.psd1
```

## <a name="using-configurationdata-variables-in-a-configuration"></a>구성에 ConfigurationData 변수 사용

DSC에서는 구성 스크립트에 사용할 수 있는 다음 특수 변수를 제공합니다.

- **$AllNodes**는 **ConfigurationData**에 정의된 노드의 컬렉션 전체를 참조합니다. **AllNodes** 컬렉션은 **.Where()** 및 **.ForEach()** 를 사용하여 필터링할 수 있습니다.
- **ConfigurationData**는 구성을 컴파일할 때 매개 변수로 전달된 해시 테이블 전체를 참조합니다.
- **MyTypeName**에는 변수가 사용되는 [구성](configurations.md) 이름이 포함됩니다. 예를 들어 `MyDscConfiguration` 구성에서 `$MyTypeName`에는 `MyDscConfiguration` 값이 포함됩니다.
- **Node**는 **AllNodes** 컬렉션이 **.Where()** 또는 **.ForEach()** 로 필터링된 후에 특정 항목을 참조합니다.
  - [about_arrays](/powershell/module/microsoft.powershell.core/about/about_arrays)의 이 메서드에 대해 자세히 알아볼 수 있습니다.

## <a name="using-non-node-data"></a>비노드 데이터 사용

이전 예제에서 살펴본 것처럼, **ConfigurationData** 해시 테이블은 필수 **AllNodes** 키 외에 키를 하나 이상 추가로 포함할 수 있습니다.
이 항목의 예제에서는 추가 노드를 하나만 사용했으며 이름을 `NonNodeData`로 지정했습니다.
그러나 추가 키는 원하는 수만큼 정의할 수 있으며 원하는 이름을 지정할 수 있습니다.

비노드 데이터 사용 예제는 [구성 및 환경 데이터 분리](separatingEnvData.md)를 참조하세요.

## <a name="see-also"></a>참고 항목

- [구성 데이터의 자격 증명 옵션](configDataCredentials.md)
- [DSC 구성](configurations.md)