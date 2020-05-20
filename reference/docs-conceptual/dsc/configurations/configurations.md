---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: DSC 구성
ms.openlocfilehash: d7749ec88f9cca3e29c6b38d61fb73776af7ceb4
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2020
ms.locfileid: "71954500"
---
# <a name="dsc-configurations"></a>DSC 구성

> 적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0

DSC 구성은 특별한 형식의 함수를 정의하는 PowerShell 스크립트입니다.
구성을 정의하려면 PowerShell 키워드 **Configuration**을 사용합니다.

```powershell
Configuration MyDscConfiguration {
    Node "TEST-PC1" {
        WindowsFeature MyFeatureInstance {
            Ensure = 'Present'
            Name = 'RSAT'
        }
        WindowsFeature My2ndFeatureInstance {
            Ensure = 'Present'
            Name = 'Bitlocker'
        }
    }
}
MyDscConfiguration
```

스크립트를 `.ps1` 파일로 저장합니다.

## <a name="configuration-syntax"></a>구성 구문

구성 스크립트는 다음의 부분들로 구성됩니다.

- **Configuration** 블록. 가장 바깥쪽 스크립트 블록입니다. **Configuration** 키워드를 사용하고 이름을 제공하여 정의합니다. 이 경우 구성의 이름은 "MyDscConfiguration"입니다.
- 하나 이상의 **Node** 블록. 이 블록에서는 구성 중인 노드(컴퓨터 또는 VM)를 정의합니다. 위의 구성에는 "TEST-PC1"이라는 컴퓨터를 대상으로 하는 하나의 **Node** 블록이 있습니다. Node 블록에서는 여러 컴퓨터 이름을 사용할 수 있습니다.
- 하나 이상의 리소스 블록. 이 블록은 구성으로 구성 중인 리소스에 대한 속성을 설정하는 위치입니다. 이 경우 두 개의 리소스 블록이 있으며, 각각 "WindowsFeature" 리소스를 호출합니다.

**Configuration** 블록 내에서는 PoweShell 함수에서 일반적으로 수행할 수도 있는 모든 작업을 수행할 수 있습니다. 예를 들어 앞의 예에서는, 구성에서 대상 컴퓨터의 이름을 하드 코드하지 않으려는 경우 노드 이름에 대한 매개 변수를 추가할 수도 있습니다.

이 예제에서는 구성을 컴파일할 때 **ComputerName** 매개 변수로 전달하여 노드의 이름을 지정합니다. 이름의 기본값은 "localhost"입니다.

```powershell
Configuration MyDscConfiguration
{
    param
    (
        [string[]]$ComputerName='localhost'
    )

    Node $ComputerName
    {
        WindowsFeature MyFeatureInstance
        {
            Ensure = 'Present'
            Name = 'RSAT'
        }

        WindowsFeature My2ndFeatureInstance
        {
            Ensure = 'Present'
            Name = 'Bitlocker'
        }
    }
}

MyDscConfiguration
```

**Node** 블록에서는 여러 컴퓨터 이름을 사용할 수도 있습니다. 위의 예제에서 `-ComputerName` 매개 변수를 사용하거나, 쉼표로 구분된 컴퓨터 목록을 **Node** 블록에 직접 전달할 수 있습니다.

```powershell
MyDscConfiguration -ComputerName "localhost", "Server01"
```

컴퓨터 목록을 **Node** 블록으로 지정하면 구성 내에서 배열 표기법을 사용해야 합니다.

```powershell
Configuration MyDscConfiguration
{
    Node @('localhost', 'Server01')
    {
        WindowsFeature MyFeatureInstance
        {
            Ensure = 'Present'
            Name = 'RSAT'
        }

        WindowsFeature My2ndFeatureInstance
        {
            Ensure = 'Present'
            Name = 'Bitlocker'
        }
    }
}

MyDscConfiguration
```

## <a name="compiling-the-configuration"></a>구성 컴파일

구성을 시행할 수 있으려면 먼저 MOF 문서로 컴파일해야 합니다.
PowerShell 함수를 호출하는 것처럼 구성을 호출하면 됩니다.
구성의 이름만을 포함하는 예제의 마지막 줄은 구성을 호출합니다.

> [!NOTE]
> 구성을 호출하려면 (다른 PowerShell 함수에서처럼) 함수가 전역 범위에 있어야 합니다.
> 스크립트를 "도트 소싱"하거나, F5 키를 사용하거나 ISE에서 **스크립트 실행** 단추를 클릭하여 구성 스크립트를 실행하면 이렇게 할 수 있습니다.
> 스크립트를 도트 소싱하려면 명령을 `. .\myConfig.ps1`을 실행합니다. 여기서 `myConfig.ps1`은 구성을 포함하는 스크립트 파일의 이름입니다.

구성을 호출하면 다음을 수행합니다.

- 모든 변수를 확인합니다.
- 현재 디렉터리에 구성과 같은 이름으로 폴더를 생성합니다.
- 새 디렉터리에 _NodeName_.mof라는 파일을 생성합니다. _NodeName_은 구성의 대상 노드 이름입니다.
  노드가 두 개 이상 있을 경우에는 각 노드에 대해 MOF 파일이 생성됩니다.

> [!NOTE]
> MOF 파일은 대상 노드에 대한 모든 구성 정보를 포함합니다. 이 때문에 안전하게 유지해야 합니다.
> 자세한 내용은 [MOF 파일 보안](../pull-server/secureMOF.md)을 참조하세요.

위의 첫 번째 구성을 컴파일하면 다음 폴더 구조가 생성됩니다.

```powershell
. .\MyDscConfiguration.ps1
MyDscConfiguration
```

```
    Directory: C:\users\default\Documents\DSC Configurations\MyDscConfiguration
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       10/23/2015   4:32 PM           2842 localhost.mof
```

구성에서 매개 변수를 사용하는 경우, 두 번째 예제에서처럼 컴파일 시 제공해야 합니다. 다음과 같은 모습이 됩니다.

```powershell
. .\MyDscConfiguration.ps1
MyDscConfiguration -ComputerName 'MyTestNode'
```

```
    Directory: C:\users\default\Documents\DSC Configurations\MyDscConfiguration
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       10/23/2015   4:32 PM           2842 MyTestNode.mof
```

## <a name="using-new-resources-in-your-configuration"></a>구성에서 새 리소스 사용

앞의 예제를 실행했다면 명시적으로 가져오지 않고 리소스를 사용하고 있다는 경고가 표시된 것을 보았을 수 있습니다.
오늘, DSC는 PSDesiredStateConfiguration 모듈의 일부로서 12개의 리소스와 함께 제공됩니다.

cmdlet인 [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)는 시스템에 설치되어 있고 LCM에서 사용할 수 있는 리소스를 파악하는 데 사용할 수 있습니다.
이러한 모듈은 `$env:PSModulePath`에 배치되어 [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)에 의해 제대로 인식된 후에도 여전히 구성 내에서 로드되어야 합니다.

**Import-DscResource**는 **구성** 블록 내에서만 인식될 수 있는 동적 키워드이며, cmdlet이 아닙니다.
**Import-DscResource**에서는 두 개의 매개 변수를 지원합니다.

- **ModuleName**은 **Import-DscResource**를 사용하는 권장 방법입니다. 가져올 리소스를 포함하는 모듈의 이름을 받습니다(모듈 이름으로 이루어진 문자열 배열도 받음).
- **Name**은 가져올 리소스의 이름입니다. 이 이름은 [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)에 의해 "Name"으로 반환한 친숙한 이름이 아니라, 리소스 스키마를 정의할 때 사용된 클래스 이름입니다([Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)에 의해 **ResourceType**으로 반환됨).

`Import-DSCResource` 사용에 대한 자세한 내용은 [Import-DSCResource 사용](import-dscresource.md)을 참조하세요.

## <a name="powershell-v4-and-v5-differences"></a>PowerShell v4 및 v5의 차이

PowerShell 4.0에서 DSC 리소스를 저장해야 하는 경우에는 차이가 있습니다. 자세한 내용은 [리소스 위치](import-dscresource.md#resource-location)를 참조하세요.

## <a name="see-also"></a>참고 항목

- [Windows PowerShell Desired State Configuration 개요](../overview/overview.md)
- [DSC 리소스](../resources/resources.md)
- [로컬 구성 관리자 구성](../managing-nodes/metaConfig.md)
