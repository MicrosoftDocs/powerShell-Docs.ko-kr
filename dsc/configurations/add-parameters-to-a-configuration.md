---
ms.date: 12/12/2018
keywords: dsc, powershell, 리소스, 갤러리, 설치
title: 구성에 매개 변수 추가
ms.openlocfilehash: 15213404f0cdd6416baf1f83af91b8f5279cc97f
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402556"
---
# <a name="add-parameters-to-a-configuration"></a>구성에 매개 변수 추가

함수에서 처럼 [구성을](configurations.md) 사용자 입력을 기반으로 하는 보다 동적인 구성을 허용 하 여 매개 변수화 할 수 있습니다. 단계에 설명 된 내용과 비슷합니다 [매개 변수를 사용 하 여 함수](/powershell/module/microsoft.powershell.core/about/about_functions)합니다.

이 예제에서는 "Running" 이어야 하는 "Spooler" 서비스를 구성 하는 기본 구성을 시작 합니다.

```powershell
Configuration TestConfig
{
    # It is best practice to implicitly import any required resources or modules.
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

함수와 달리 그러나 합니다 [CmdletBinding](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute) 특성 추가 기능이 없습니다. 외에 [일반 매개 변수](/powershell/module/microsoft.powershell.core/about/about_commonparameters), 구성을 다음 매개 변수를 정의 할 필요 없이 기본 제공을 사용할 수도 있습니다.

|매개 변수  |설명  |
|---------|---------|
|`-InstanceName`|정의에 사용 되는 [복합 구성](compositeconfigs.md)|
|`-DependsOn`|정의에 사용 되는 [복합 구성](compositeconfigs.md)|
|`-PSDSCRunAsCredential`|정의에 사용 되는 [복합 구성](compositeconfigs.md)|
|`-ConfigurationData`|전달 하는 데에 구조적 [구성 데이터](configData.md) 구성에 사용 합니다.|
|`-OutputPath`|위치를 지정 하는 데에 "\<computername\>.mof" 파일 컴파일|

## <a name="adding-your-own-parameters-to-configurations"></a>구성에 사용자 고유의 매개 변수를 추가합니다.

기본 제공 매개 변수 외에도 사용자 구성에도 고유한 매개 변수를 추가할 수 있습니다. 매개 변수 블록 함수 처럼 구성 선언 내에서 직접 이동합니다. 구성 매개 변수 블록을 하나 밖에 있어야 **노드** 선언 및 위에 *가져오기* 문입니다. 매개 변수를 추가 하면 더 강력 하 고 동적 구성을 만들 수 있습니다.

```powershell
Configuration TestConfig
{
    param
    (

    )
```

### <a name="add-a-computername-parameter"></a>ComputerName 매개 변수 추가

첫 번째 매개 변수인 추가할 수 있습니다는 `-Computername` 에 대 한 "mof" 파일을 동적으로 컴파일할 수 있도록 하는 매개 변수 `-Computername` 구성에 전달 합니다. 함수와 마찬가지로 정의할 수도 있습니다는 기본값을 사용자에 대 한 값에 통과 하지 못하는 경우 `-ComputerName`

```powershell
param
(
    [String]
    $ComputerName="localhost"
)
```

구성에 지정할 수 있습니다 다음에 `-ComputerName` 노드 블록을 정의할 때 매개 변수입니다.

```powershell
Node $ComputerName
{

}
```

### <a name="calling-your-configuration-with-parameters"></a>에 대 한 구성 매개 변수를 호출합니다.

구성에 매개 변수를 추가한 후 cmdlet을 사용 하는 것 처럼 사용할 수 있습니다.

```powershell
TestConfig -ComputerName "server01"
```

### <a name="compiling-multiple-mof-files"></a>여러.mof 파일 컴파일

노드 블록 컴퓨터 이름의 쉼표로 구분 된 목록을 그대로 사용할 수도 있습니다 및 각각에 대해 ".mof" 파일을 생성 합니다. 에 전달 된 컴퓨터의 모든 ".mof" 파일을 생성 하려면 다음 예제에서는 실행할 수 있습니다는 `-ComputerName` 매개 변수입니다.

```powershell
Configuration TestConfig
{
    param
    (
        [String]
        $ComputerName="localhost"
    )

    # It is best practice to implicitly import any required resources or modules.
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

## <a name="advanced-parameters-in-configurations"></a>구성에서 고급 매개 변수

이외에 `-ComputerName` 매개 변수, 서비스 이름 및 상태에 대 한 매개 변수를 추가할 수 있습니다. 사용 하 여 매개 변수 블록을 추가 하는 다음 예제는 `-ServiceName` 매개 변수 동적으로 정의 하는 데 사용 합니다 **서비스** 리소스 블록. 또한 추가 `-State` 매개 변수를 동적으로 정의할 합니다 **상태** 에 **서비스** 리소스 블록.

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

    # It is best practice to implicitly import any required resources or modules.
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
> 더 많은 advacned 시나리오에서 동적 데이터는 구조적으로 이동할 것이 더 적절 해야 [구성 데이터](configData.md)입니다.

지금 구성을 예제에서는 동적 `$ServiceName`를 지정 하지 않으면 컴파일 오류가 발생 하지만 합니다. 이 예제와 같이 기본 값을 추가할 수 있습니다.

```powershell
[String]
$ServiceName="Spooler"
```

이 인스턴스에서 그러나 편이 사용자에 대 한 값을 지정 하려면 강제 적용 하는 `$ServiceName` 매개 변수입니다. `parameter` 특성을 사용 하면 추가 유효성 검사 및 파이프라인 지원 구성에 매개 변수를 추가할 수 있습니다.

모든 매개 변수 선언 위에 추가 합니다 `parameter` 아래 예제와 같이 특성 블록입니다.

```powershell
[parameter()]
[String]
$ServiceName
```

각 인수를 지정할 수 있습니다 `parameter` 여러 측면을 제어할 정의 된 매개 변수 특성입니다. 다음 예에서는 합니다 `$ServiceName` 는 **필수** 매개 변수입니다.

```powershell
[parameter(Mandatory)]
[String]
$ServiceName
```

에 대 한 합니다 `$State` 미리 정의 된 집합 외부의 값을 지정할 필요가 없도록 사용자를 방지 하고자 매개 변수 (실행 중인, 중지 됨)는 `ValidationSet*`특성 (예: 실행 중, 미리 정의 된 집합 외부의 값을 지정할 필요가 없도록 사용자를 방해 중지 됨). 다음 예제에 추가 합니다 `ValidationSet` 특성을 `$State` 매개 변수입니다. 확인 하지 않을 것 이므로 합니다 `$State` 매개 변수 **필수**에 대 한 기본값을 추가 해야 합니다.

```powershell
[ValidateSet("Running", "Stopped")]
[String]
$State="Running"
```

> [!NOTE]
> 지정할 필요가 없습니다를 `parameter` 사용 하는 경우 특성을 `validation` 특성입니다.

에 대 한 자세한 내용은 합니다 `parameter` 및 유효성 검사 특성 [about_Functions_Advanced_Parameters](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters.md)합니다.

## <a name="fully-parameterized-configuration"></a>매개 변수가 있는 완벽 하 게 구성

이제 사용자가 지정 하는 매개 변수가 있는 구성을 `-InstanceName`, `-ServiceName`, 유효성을 검사 하 고는 `-State` 매개 변수입니다.

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

    # It is best practice to implicitly import any required resources or modules.
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
- [구성에 구성 데이터를 사용 합니다.](configData.md)
- [별도 구성 및 환경 데이터입니다.](separatingEnvData.md)
