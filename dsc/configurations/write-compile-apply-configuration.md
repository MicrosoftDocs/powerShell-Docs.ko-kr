---
ms.date: 12/12/2018
keywords: DSC, PowerShell, 구성, 서비스, 설정
title: 구성 작성, 컴파일 및 적용
ms.openlocfilehash: 8bcd55518b0409b9a4b02ca95f027a0a77eb5300
ms.sourcegitcommit: 118eb294d5a84a772e6449d42a9d9324e18ef6b9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/22/2019
ms.locfileid: "68372184"
---
> 적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0

# <a name="write-compile-and-apply-a-configuration"></a>구성 작성, 컴파일 및 적용

이 연습에서는 DSC(필요한 상태 구성) 구성을 만들고 적용하는 과정을 처음부터 끝까지 자세히 설명합니다.
다음 예제에서는 매우 간단한 구성을 작성하고 적용하는 방법을 알아봅니다. 이 구성은 "HelloWorld.txt" 파일이 로컬 머신에 존재하는지 확인합니다. 해당 파일을 삭제하는 경우 DSC는 다음 업데이트 시 이를 다시 생성합니다.

DSC가 무엇이며 어떻게 작동하는지에 대한 개요는 [개발자를 위한 필요한 상태 구성 개요](../overview/overview.md)를 참조하세요.

## <a name="requirements"></a>요구 사항

이 예제를 실행하려면 PowerShell 4.0 이상을 실행하는 컴퓨터가 필요합니다.

## <a name="write-the-configuration"></a>구성 작성

DSC [구성](configurations.md)은 하나 이상의 대상 컴퓨터(노드)를 구성할 방법을 정의하는 특수한 PowerShell 기능입니다.

PowerShell ISE 또는 다른 PowerShell 편집기에서 다음을 입력합니다.

```powershell
Configuration HelloWorld {

    # Import the module that contains the File resource.
    Import-DscResource -ModuleName PsDesiredStateConfiguration

    # The Node statement specifies which targets to compile MOF files for, when this configuration is executed.
    Node 'localhost' {

        # The File resource can ensure the state of files, or copy them from a source to a destination with persistent updates.
        File HelloWorld {
            DestinationPath = "C:\Temp\HelloWorld.txt"
            Ensure = "Present"
            Contents   = "Hello World from DSC!"
        }
    }
}
```

> !Important 여러 DSC 리소스를 작업할 수 있도록 여러 모듈을 가져와야 하는 고급 시나리오에서는 `Import-DscResource`를 사용하여 각 모듈을 별도의 줄에 둡니다.
> 이는 소스 제어에서 관리하기가 쉽고 Azure State Configuration에서 DSC를 작업할 때 필요합니다.
>
> ```powershell
>  Configuration HelloWorld {
>
>   # Import the module that contains the File resource.
>   Import-DscResource -ModuleName PsDesiredStateConfiguration
>   Import-DscResource -ModuleName xWebAdministration
>
> ```

파일을 "HelloWorld.ps1"로 저장합니다.

구성을 정의하는 것은 함수를 정의하는 것과 비슷합니다. **Node** 블록은 구성할 대상 노드를 지정하며, 이 경우는 `localhost`입니다.

해당 구성은 하나의 [리소스](../resources/resources.md)인 `File` 리소스를 호출합니다. 리소스는 대상 노드가 구성에 정의된 상태에 있는지 확인합니다.

## <a name="compile-the-configuration"></a>구성 컴파일

노드에 DSC 구성을 적용하려면 먼저 MOF 파일로 컴파일해야 합니다.
함수처럼 구성을 실행하면 `Node` 블록에 의해 정의된 모든 노드에서 하나의 ".mof" 파일을 컴파일합니다.
구성을 실행하기 위해 "HelloWorld.ps1" 스크립트를 현재 범위로 *도트 소스*해야 합니다.
자세한 내용은 [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-6#script-scope-and-dot-sourcing)를 참조하세요.

<!-- markdownlint-disable MD038 -->
‘점, 공백’ 뒤에 "HelloWorld.ps1" 스크립트를 저장한 경로를 입력하여 `. `(도트 소스)합니다.  그런 다음, 함수처럼 구성을 호출하여 실행합니다.
<!-- markdownlint-enable MD038 -->

```powershell
. C:\Scripts\HelloWorld.ps1
HelloWorld
```

그러면 다음과 같은 출력이 생성됩니다.

```output
Directory: C:\Scripts\HelloWorld


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

## <a name="apply-the-configuration"></a>구성 적용

이제 MOF를 컴파일했으므로 [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet을 호출하여 구성을 대상 노드(이 경우 로컬 컴퓨터)에 적용할 수 있습니다.

`Start-DscConfiguration` cmdlet은 DSC의 엔진인 [LCM(로컬 구성 관리자)](../managing-nodes/metaConfig.md)에 구성을 적용하라고 지시합니다.
LCM은 DSC 리소스를 호출하여 구성을 적용합니다.

아래 코드를 사용하여 `Start-DSCConfiguration` cmdlet을 실행합니다. "localhost.mof"가 저장된 디렉터리 경로를 `-Path` 매개 변수로 지정합니다. `Start-DSCConfiguration` cmdlet은 "\<computername\>.mof" 파일에서 지정된 디렉터리를 살펴봅니다. `Start-DSCConfiguration` cmdlet은 파일 이름별로 지정된 컴퓨터 이름에 찾은 ".mof" 파일을 적용하려고 합니다("localhost", "server01", "dc-02" 등).

> [!NOTE]
> `-Wait` 매개 변수가 지정되지 않으면 `Start-DSCConfiguration`은 백그라운드 작업을 만들어서 작업을 수행합니다. `-Verbose` 매개 변수를 지정하면 작업의 **자세한 정보 표시** 출력을 볼 수 있습니다. `-Wait` 및 `-Verbose`는 모두 선택적 매개 변수입니다.

```powershell
Start-DscConfiguration -Path C:\Scripts\HelloWorld -Verbose -Wait
```

## <a name="test-the-configuration"></a>구성 테스트

`Start-DSCConfiguration` cmdlet이 완료되면 지정한 위치에서 "HelloWorld.txt" 파일을 표시합니다. [Get-Content](/powershell/module/microsoft.powershell.management/get-content) cmdlet을 사용하여 콘텐츠를 확인할 수 있습니다.

[Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)을 사용하여 현재 상태를 *테스트*할 수도 있습니다.

노드가 현재 적용된 구성을 준수하는 경우 출력은 "True"여야 합니다.

```powershell
Test-DSCConfiguration
```

```output
True
```

```powershell
Get-Content -Path C:\Temp\HelloWorld.txt
```

```output
Hello World from DSC!
```

## <a name="re-applying-the-configuration"></a>구성 다시 적용

구성이 다시 적용되는지 확인하려면 구성에 의해 생성된 텍스트 파일을 제거하면 됩니다. `-UseExisting` 매개 변수와 `Start-DSCConfiguration` cmdlet을 사용합니다. `-UseExisting` 매개 변수는 `Start-DSCConfiguration`이 가장 최근에 성공적으로 적용된 구성을 나타내는 "current.mof" 파일을 다시 적용하도록 지시합니다.

```powershell
Remove-Item -Path C:\Temp\HelloWorld.txt
```

## <a name="next-steps"></a>다음 단계

- DSC 구성에 대한 자세한 내용은 [DSC 구성](configurations.md)을 참조하세요.
- [DSC 리소스](../resources/resources.md)에서는 어떤 DSC 리소스를 사용할 수 있으며 사용자 지정 DSC 리소스를 만드는 방법은 무엇인지 확인할 수 있습니다.
- [PowerShell 갤러리](https://www.powershellgallery.com/)에서는 DSC 구성 및 리소스를 찾을 수 있습니다.
