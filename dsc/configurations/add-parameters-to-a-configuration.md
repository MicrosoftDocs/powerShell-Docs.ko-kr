---
ms.date: 12/12/2018
keywords: dsc,powershell,리소스,갤러리,설정
title: 구성에 매개 변수 추가
ms.openlocfilehash: 72e6c15593d11ed39d7fe8ea79f794089f410cf8
ms.sourcegitcommit: d1ba596f9e0d4df9565601a70687a126d535c917
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/05/2019
ms.locfileid: "70386321"
---
# <a name="add-parameters-to-a-configuration"></a>구성에 매개 변수 추가

함수처럼, 사용자 입력에 따라 더 동적인 구성을 허용하도록 [구성](configurations.md)을 매개 변수화할 수 있습니다. 단계는 [함수 및 매개 변수](/powershell/module/microsoft.powershell.core/about/about_functions)에 설명된 단계와 비슷합니다.

이 예제에서는 "Spooler" 서비스를 "Running"으로 구성하는 기본 구성으로 시작합니다.

```powershell
Configuration TestConfig
{
    # It is best practice to explicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node localhost
    {
        Service 'Spooler'
        {
            Name = 'Spooler'
            State = 'Running'
        }
    }
}
```

## <a name="built-in-configuration-parameters"></a>기본 제공 구성 매개 변수

함수와 달리 [CmdletBinding](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute) 특성은 기능을 추가하지 않습니다. [일반 매개 변수](/powershell/module/microsoft.powershell.core/about/about_commonparameters) 외에도 구성에서는 매개 변수를 정의할 필요 없이 다음 기본 제공 매개 변수를 사용할 수도 있습니다.

|매개 변수  |설명  |
|---------|---------|
|`-InstanceName`|[복합 구성](compositeconfigs.md)을 정의하는 데 사용됩니다.|
|`-DependsOn`|[복합 구성](compositeconfigs.md)을 정의하는 데 사용됩니다.|
|`-PSDSCRunAsCredential`|[복합 구성](compositeconfigs.md)을 정의하는 데 사용됩니다.|
|`-ConfigurationData`|구성에서 사용하도록 구조적 [구성 데이터](configData.md)를 전달하는 데 사용됩니다.|
|`-OutputPath`|"\<computername\>.mof" 파일을 컴파일할 위치를 지정하는 데 사용됩니다.|

## <a name="adding-your-own-parameters-to-configurations"></a>구성에 고유한 매개 변수 추가

기본 제공 매개 변수 외에 고유한 매개 변수를 구성에 추가할 수도 있습니다. 매개 변수 블록은 함수처럼 구성 선언 내부로 직접 이동합니다. 구성 매개 변수 블록은 **Node** 선언 외부 및 *import* 문 위에 있어야 합니다. 매개 변수를 추가하면 더 강력하고 동적인 구성을 만들 수 있습니다.

```powershell
Configuration TestConfig
{
    param
    (

    )
```

### <a name="add-a-computername-parameter"></a>ComputerName 매개 변수 추가

추가할 수 있는 첫 번째 매개 변수는 `-Computername` 매개 변수이므로 구성에 전달하는 모든 `-Computername`에 대해 ".mof" 파일을 동적으로 컴파일할 수 있습니다. 함수처럼, 사용자가 `-ComputerName` 값을 전달하지 않는 경우 기본값을 정의할 수도 있습니다.

```powershell
param
(
    [String]
    $ComputerName="localhost"
)
```

구성 내에서 Node 블록을 정의할 때 `-ComputerName` 매개 변수를 지정할 수 있습니다.

```powershell
Node $ComputerName
{

}
```

### <a name="calling-your-configuration-with-parameters"></a>매개 변수를 사용하여 구성 호출

구성에 매개 변수를 추가한 후 cmdlet에서 사용하는 것처럼 이 매개 변수를 사용할 수 있습니다.

```powershell
TestConfig -ComputerName "server01"
```

### <a name="compiling-multiple-mof-files"></a>여러 .mof 파일 컴파일

Node 블록은 쉼표로 구분된 컴퓨터 이름 목록을 사용할 수 있고 각 컴퓨터 이름에 대해 ".mof" 파일을 생성합니다. 다음 예제를 실행하여 `-ComputerName` 매개 변수에 전달된 모든 컴퓨터에 대해 ".mof" 파일을 생성할 수 있습니다.

```powershell
Configuration TestConfig
{
    param
    (
        [String]
        $ComputerName="localhost"
    )

    # It is best practice to explicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node $ComputerName
    {
        Service 'Spooler'
        {
            Name = 'Spooler'
            State = 'Running'
        }
    }
}

TestConfig -ComputerName "server01", "server02", "server03"
```

## <a name="advanced-parameters-in-configurations"></a>구성의 고급 매개 변수

`-ComputerName` 매개 변수 외에도 서비스 이름 및 상태에 대한 매개 변수를 추가할 수 있습니다. 다음 예제에서는 `-ServiceName`을 사용하여 매개 변수 블록을 추가하고 이 매개 변수를 **Service** 리소스 블록을 동적으로 정의하는 데 사용합니다. 또한 `-State` 매개 변수를 추가하여 **Service** 리소스 블록에서 **State**를 동적으로 정의합니다.

```powershell
Configuration TestConfig
{
    param
    (
        [String]
        $ServiceName,

        [String]
        $State,

        [String]
        $ComputerName="localhost"
    )

    # It is best practice to explicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node $ComputerName
    {
        Service $ServiceName
        {
            Name = $ServiceName
            State = $State
        }
    }
}
```

> [!NOTE]
> 더 고급 시나리오에서는 동적 데이터를 구조적 [구성 데이터](configData.md)로 이동하는 것이 좋습니다.

예제 구성에서는 이제 동적 `$ServiceName`을 사용하지만 이 매개 변수를 지정하지 않을 경우 컴파일 시 오류가 발생합니다. 이 예제와 같이 기본값을 추가할 수 있습니다.

```powershell
[String]
$ServiceName="Spooler"
```

하지만 이 경우에는 간단히 사용자에게 `$ServiceName` 매개 변수를 지정하도록 하는 것이 좋습니다. `parameter` 특성을 사용하여 구성의 매개 변수에 유효성 검사 및 파이프라인 지원을 추가할 수 있습니다.

모든 매개 변수 선언 위에 아래 예제와 같이 `parameter` 특성 블록을 추가합니다.

```powershell
[parameter()]
[String]
$ServiceName
```

각 `parameter` 특성에 대한 인수를 지정하여 정의된 매개 변수의 측면을 제어할 수 있습니다. 다음 예제에서는 `$ServiceName`을 **Mandatory** 매개 변수로 설정합니다.

```powershell
[parameter(Mandatory)]
[String]
$ServiceName
```

`$State` 매개 변수의 경우 사용자가 미리 정의된 세트(예: Running, Stopped) 외부 값을 지정하지 못하도록 합니다. `ValidationSet*` 특성은 사용자가 미리 정의된 세트(예: Running, Stopped) 외부 값을 지정하지 못하도록 합니다. 다음 예제에서는 `ValidationSet` 특성을 `$State` 매개 변수에 추가합니다. `$State` 매개 변수를 **Mandatory**로 설정하지 않을 것이므로 기본값을 추가해야 합니다.

```powershell
[ValidateSet("Running", "Stopped")]
[String]
$State="Running"
```

> [!NOTE]
> `validation` 특성을 사용하는 경우 `parameter` 특성을 지정할 필요가 없습니다.

[about_Functions_Advanced_Parameters](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters)에서 `parameter` 및 validation 특성에 대해 자세히 알아보세요.

## <a name="fully-parameterized-configuration"></a>완전 매개 변수화된 구성

이제 사용자가 `-InstanceName`, `-ServiceName`을 지정하도록 하고 `-State` 매개 변수의 유효성을 검사하는 매개 변수화된 구성이 있습니다.

```powershell
Configuration TestConfig
{
    param
    (
        [parameter(Mandatory)]
        [String]
        $ServiceName,

        [ValidateSet("Running","Stopped")]
        [String]
        $State="Running",

        [String]
        $ComputerName="localhost",
    )

    # It is best practice to explicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node localhost
    {
        Service $ServiceName
        {
            Name = $ServiceName
            State = $State
        }
    }
}
```

## <a name="see-also"></a>참고 항목

- [DSC 구성에 대한 도움말 작성](configHelp.md)
- [동적 구성](flow-control-in-configurations.md)
- [구성에서 구성 데이터 사용](configData.md)
- [구성 및 환경 데이터 분리](separatingEnvData.md)
