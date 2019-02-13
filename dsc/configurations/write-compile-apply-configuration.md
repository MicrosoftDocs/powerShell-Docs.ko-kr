---
ms.date: 12/12/2018
keywords: dsc, powershell, 구성, 서비스, 설치
title: 구성 작성, 컴파일 및 적용
ms.openlocfilehash: fa4d98fd12202439ba7025fd8af3fa398653ca05
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55679982"
---
> 적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0

# <a name="write-compile-and-apply-a-configuration"></a>구성 작성, 컴파일 및 적용

이 연습에서는 DSC(필요한 상태 구성) 구성을 만들고 적용하는 과정을 처음부터 끝까지 자세히 설명합니다.
다음 예제에서는 작성 하는 매우 간단한 구성을 적용 하는 방법을 배웁니다. "HelloWorld.txt" 파일이 로컬 컴퓨터에 구성 해야 합니다. 파일을 삭제 하는 경우 DSC는 다시 다음에 업데이트 합니다.

DSC 란 무엇 이며 작동 원리의 개요를 참조 하세요 [개발자를 위한 개요 Desired State Configuration](../overview/overview.md)합니다.

## <a name="requirements"></a>요구 사항

이 예제를 실행 하려면 PowerShell 4.0 이상을 실행 하 고 컴퓨터를 해야 합니다.

## <a name="write-the-configuration"></a>구성 작성

DSC [구성](configurations.md)은 하나 이상의 대상 컴퓨터(노드)를 구성할 방법을 정의하는 특수한 PowerShell 기능입니다.

PowerShell ISE 또는 다른 PowerShell 편집기에서 다음을 입력 합니다.

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

"HelloWorld.ps1"로 파일을 저장 합니다.

구성을 정의 하는 것은 함수 정의 비슷합니다. **Node** 블록은 구성할 대상 노드를 지정하며, 이 경우는 `localhost`입니다.

구성을 하나를 호출 [리소스](../resources/resources.md)는 `File` 리소스입니다. 리소스는 대상 노드가 구성에 정의된 상태에 있는지 확인합니다.

## <a name="compile-the-configuration"></a>구성 컴파일

노드에 DSC 구성을 적용하려면 먼저 MOF 파일로 컴파일해야 합니다.
구성을 함수 처럼 실행 정의한 모든 노드에 대해 하나의 ".mof" 파일을 컴파일하는 `Node` 블록입니다.
구성을 실행 하기 위해 해야 할 *도트 소싱* "HelloWorld.ps1" 스크립트를 현재 범위에 있습니다.
자세한 내용은 [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-6#script-scope-and-dot-sourcing)합니다.

*도트 소싱* 를 저장 한 경로로, 뒤에 입력 하 여 "HelloWorld.ps1" 스크립트는 `. ` (점, 공백). 그런 다음 할 구성을 함수 처럼 호출 하 여 실행 합니다.

```powershell
. C:\Scripts\WebsiteTest.ps1
HelloWolrd
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

`Start-DscConfiguration` cmdlet 지시 합니다 [구성 관리자 (LCM (로컬)](../managing-nodes/metaConfig.md), 구성을 적용 하려면 DSC의 엔진입니다.
LCM은 DSC 리소스를 호출하여 구성을 적용합니다.

아래 코드를 사용 하 여 실행 된 `Start-DSCConfiguration` cmdlet. "localhost.mof" 저장 된 디렉터리 경로 지정 합니다 `-Path` 매개 변수입니다. 합니다 `Start-DSCConfiguration` cmdlet에 대 한 지정 된 디렉터리를 조사 "\<computername\>.mof" 파일입니다. `Start-DSCConfiguration` cmdlet은 찾은 각 ".mof" 파일 이름 ("localhost", "server01", "dc-02" 등)으로 지정 된 컴퓨터 이름에 적용 하려고 합니다.

> [!NOTE]
> 경우는 `-Wait` 매개 변수를 지정 하지 않으면 `Start-DSCConfiguration` 작업을 수행 하는 백그라운드 작업을 만듭니다. 지정 하는 `-Verbose` 매개 변수를 사용 하면 볼 수 있습니다 합니다 **Verbose** 작업의 출력입니다. `-Wait`및 `-Verbose` 모두 선택적 매개 변수입니다.

```powershell
Start-DscConfiguration -Path C:\Scripts\HelloWorld -Verbose -Wait
```

## <a name="test-the-configuration"></a>구성 테스트

한 번의 `Start-DSCConfiguration` cmdlet 완료 되 면 지정한 위치에 있는 "HelloWorld.txt" 파일을 표시 합니다. 포함 된 콘텐츠를 확인할 수 있습니다 합니다 [Get-content](/powershell/module/microsoft.powershell.management/get-content) cmdlet.

할 수도 있습니다 *테스트할* 사용 하 여 현재 상태 [Test-dscconfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)합니다.

출력 노드는 현재 적용된 된 구성을 준수 하는 경우 "True" 이어야 합니다.

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

## <a name="re-applying-the-configuration"></a>구성을 다시 적용

구성을 다시 적용 하세요를 구성 하 여 만든 텍스트 파일을 제거할 수 있습니다. 사용 합니다 `Start-DSCConfiguration` cmdlet을 사용 합니다 `-UseExisting` 매개 변수입니다. 합니다 `-UseExisting` 매개 변수 지시 `Start-DSCConfiguration` "current.mof" 파일에 다시 적용 하려면 구성 적용을 가장 최근에 성공적으로 나타냅니다.

```powershell
Remove-Item -Path C:\Temp\HelloWorld.txt
```

## <a name="next-steps"></a>다음 단계

- DSC 구성에 대한 자세한 내용은 [DSC 구성](configurations.md)을 참조하세요.
- [DSC 리소스](../resources/resources.md)에서는 어떤 DSC 리소스를 사용할 수 있으며 사용자 지정 DSC 리소스를 만드는 방법은 무엇인지 확인할 수 있습니다.
- [PowerShell 갤러리](https://www.powershellgallery.com/)에서는 DSC 구성 및 리소스를 찾을 수 있습니다.
