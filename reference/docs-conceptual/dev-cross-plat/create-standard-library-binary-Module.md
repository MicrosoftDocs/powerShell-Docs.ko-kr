---
title: 표준 라이브러리 이진 모듈을 만드는 방법
description: PowerShell Standard Library를 사용하면 PowerShell Core와 Windows PowerShell 5.1 모두에서 작동하는 플랫폼 간 모듈을 만들 수 있습니다.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: 51734fd9232e7c33b11c6c5a6abddbcc1f28413c
ms.sourcegitcommit: ed4a895d672334c7b02fb7ef6e950dbc2ba4a197
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/28/2020
ms.locfileid: "84149416"
---
# <a name="how-to-create-a-standard-library-binary-module"></a>표준 라이브러리 이진 모듈을 만드는 방법

얼마 전 이진 모듈로 구현하고 싶은 모듈이 떠올랐습니다. [PowerShell Standard Library][]를 사용하여 만든 적이 없기 때문에 좋은 기회라고 생각했습니다. [플랫폼 간 이진 모듈 만들기][] 가이드를 사용하여 어떤 장애물도 없이 이 모듈을 만들었습니다.
같은 프로세스를 진행하면서 약간의 추가 해설을 해드리겠습니다.

> [!NOTE]
> 이 문서의 [원래 버전][]은 [@KevinMarquette][]가 작성한 블로그에 나옵니다. PowerShell 팀은 이 콘텐츠를 공유해 준 Kevin에게 감사의 말을 전합니다. [PowerShellExplained.com][]에 있는 그의 블로그를 확인하세요.

## <a name="what-is-the-powershell-standard-library"></a>PowerShell Standard Library란 무엇일까요?

PowerShell Standard Library를 사용하면 PowerShell Core와 Windows PowerShell 5.1 (또는 3.0) 모두에서 작동하는 플랫폼 간 모듈을 만들 수 있습니다.

## <a name="planning-our-module"></a>Microsoft 모듈 계획

이 모듈의 목표는 C# 코드용 `src` 폴더를 만들고 나머지 요소는 스크립트 모듈처럼 구성하는 것입니다. 여기에는 빌드 스크립트를 사용하여 모든 요소를 `output` 폴더에 컴파일하는 작업이 포함됩니다. 폴더 구조는 다음과 같습니다.

```
MyModule
├───src
├───Output
│   └───MyModule
├───MyModule
│   ├───Data
│   ├───Private
│   └───Public
└───Tests
```

## <a name="getting-started"></a>시작하기

보통 Plaster 템플릿을 사용하지만 현재 템플릿은 아직 이진 모듈을 지원하지 않습니다. 큰 문제는 아닙니다. 이번에는 직접 만들어보겠습니다.

먼저 폴더를 만들고 git 리포지토리를 만들어야 합니다. 모듈 이름의 자리 표시자로 `$module`를 사용하고 있습니다. 이렇게 하면 필요할 때 이러한 예제를 쉽게 다시 사용할 수 있습니다.

```powershell
$module = 'MyModule'
New-Item -Path $module -Type Directory
Set-Location $module
git init
```

그런 다음 루트 수준 폴더를 만듭니다.

```powershell
New-Item -Path 'src' -Type Directory
New-Item -Path 'Output' -Type Directory
New-Item -Path 'Tests' -Type Directory
New-Item -Path $module -Type Directory
```

### <a name="binary-module-setup"></a>이진 모듈 설정

이 문서의 주제는 이진 모듈이므로 이진 모듈부터 살펴보겠습니다. 이 섹션에서는 [플랫폼 간 이진 모듈 만들기][] 가이드의 예제를 사용합니다. 자세한 내용을 알고 싶거나 문제가 있다면 이 가이드를 검토하세요.

가장 먼저 할 일은 설치한 [dotnet core SDK][]의 버전을 확인하는 것입니다. 2\.1.4를 사용하지만 2.0.0 이상이라면 작업을 계속 진행할 수 있습니다.

```powershell
PS> dotnet --version
2.1.4
```

이 섹션에서는 `src` 폴더에서 작업을 진행합니다.

```powershell
Set-Location 'src'
```

dotnet 명령을 사용하여 새 클래스 라이브러리를 만듭니다.

```powershell
dotnet new classlib --name $module
```

하위 폴더에 라이브러리 폴더가 생성되지만 추가 중첩 수준은 원하지 않습니다. 이 파일들의 수준을 한 단계 올리겠습니다.

```powershell
Move-Item -Path .\$module\* -Destination .\
Remove-Item $module -Recurse
```

프로젝트의 .NET core SDK 버전을 설정합니다. 2\.1 SDK를 이용하니 2.1.0을 지정하겠습니다.
2\.0 SDK를 사용한다면 2.0.0를 지정하면 됩니다.

```powershell
dotnet new globaljson --sdk-version 2.1.0
```

PowerShell Standard Library [NuGet 패키지][]를 프로젝트에 추가합니다. 필요한 호환성 수준에 맞는 최신 버전을 사용하는지 확인하세요. 기본적으로 최신 버전을 사용하지만 이 모듈에서는 PowerShell 3.0 이상에서 제공하는 기능은 사용하지 않습니다.

```powershell
dotnet add package PowerShellStandard.Library --version 7.0.0-preview.1
```

다음과 같은 src 폴더가 있어야 합니다.

```powershell
PS> Get-ChildItem
    Directory: \MyModule\src

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        7/14/2018   9:51 PM                obj
-a----        7/14/2018   9:51 PM             86 Class1.cs
-a----        7/14/2018  10:03 PM            259 MyModule.csproj
-a----        7/14/2018  10:05 PM             45 global.json
```

이제 자체 코드를 프로젝트에 추가할 수 있습니다.

### <a name="building-a-binary-cmdlet"></a>이진 cmdlet 빌드

이 시작 cmdlet을 포함하도록 `src\Class1.cs`를 업데이트해야 합니다.

```csharp
using System;
using System.Management.Automation;

namespace MyModule
{
    [Cmdlet( VerbsDiagnostic.Resolve , "MyCmdlet")]
    public class ResolveMyCmdletCommand : PSCmdlet
    {
        [Parameter(Position=0)]
        public Object InputObject { get; set; }

        protected override void EndProcessing()
        {
            this.WriteObject(this.InputObject);
            base.EndProcessing();
        }
    }
}
```

클래스 이름과 일치하도록 파일 이름을 바꿉니다.

```powershell
Rename-Item .\Class1.cs .\ResolveMyCmdletCommand.cs
```

그래야 모듈을 빌드할 수 있습니다.

```powershell
PS> dotnet build

Microsoft (R) Build Engine version 15.5.180.51428 for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

Restore completed in 18.19 ms for C:\workspace\MyModule\src\MyModule.csproj.
MyModule -> C:\workspace\MyModule\src\bin\Debug\netstandard2.0\MyModule.dll

Build succeeded.
    0 Warning(s)
    0 Error(s)

Time Elapsed 00:00:02.19
```

새 dll에서 `Import-Module`을 호출하면 새 CMDlet을 로드할 수 있습니다.

```powershell
PS> Import-Module .\bin\Debug\netstandard2.0\$module.dll
PS> Get-Command -Module $module

CommandType Name                    Version Source
----------- ----                    ------- ------
Cmdlet      Resolve-MyCmdlet        1.0.0.0 MyModule
```

시스템에서 가져오기에 실패한다면 .NET을 4.7.1 이상으로 업데이트하세요. [플랫폼 간 이진 모듈 만들기][] 가이드에서 .NET 기존 버전에 대한 지원과 호환성 관련 정보를 확인할 수 있습니다.

### <a name="module-manifest"></a>모듈 매니페스트

다행히 우리는 dll을 가져오고 작업 모듈을 이용할 수 있습니다. 작업 모듈을 계속 이용해 모듈 매니페스트를 만들어보겠습니다. 나중에 PSGallery에 게시하려면 매니페스트가 필요합니다.

프로젝트의 루트에서 이 명령을 실행하면 필요한 모듈 매니페스트를 만들 수 있습니다.

```powershell
$manifestSplat = @{
    Path              = ".\$module\$module.psd1"
    Author            = 'Kevin Marquette'
    NestedModules     = @('bin\MyModule.dll')
    RootModule        = "$module.psm1"
    FunctionsToExport = @('Resolve-MyCmdlet')
}
New-ModuleManifest @manifestSplat
```

이후 PowerShell 함수를 위한 빈 루트 모듈도 만들겠습니다.

```powershell
Set-Content -Value '' -Path ".\$module\$module.psm1"
```

이렇게 하면 동일한 프로젝트에서 일반 PowerShell 함수와 이진 Cmdlet을 혼합할 수 있습니다.

### <a name="building-the-full-module"></a>전체 모듈 빌드

모든 요소를 출력 폴더로 컴파일합니다. 이 작업을 수행하려면 빌드 스크립트를 만들어야 합니다. 보통은 `Invoke-Build` 스크립트에 추가하지만 이번 예제에서는 간단하게 진행하겠습니다. 이 스크립트를 프로젝트 루트에 있는 `build.ps1`에 추가합니다.

```powershell
$module = 'MyModule'
Push-Location $PSScriptRoot

dotnet build $PSScriptRoot\src -o $PSScriptRoot\output\$module\bin
Copy-Item "$PSScriptRoot\$module\*" "$PSScriptRoot\output\$module" -Recurse -Force

Import-Module "$PSScriptRoot\Output\$module\$module.psd1"
Invoke-Pester "$PSScriptRoot\Tests"
```

이러한 명령은 DLL을 빌드하고 `output\$module\bin` 폴더에 배치합니다. 그러면 다른 모듈 파일을 현재 위치로 복사합니다.

```
Output
└───MyModule
    │   MyModule.psd1
    │   MyModule.psm1
    │
    └───bin
            MyModule.deps.json
            MyModule.dll
            MyModule.pdb
```

이 시점에서 psd1 파일을 사용하여 모듈을 가져올 수 있습니다.

```powershell
Import-Module ".\Output\$module\$module.psd1"
```

여기서 `.\Output\$module` 폴더를 `$env:PSModulePath` 디렉터리에 드롭하면 필요할 때마다 명령을 자동으로 로드할 수 있습니다.

### <a name="update-dotnet-new-psmodule"></a>업데이트: dotnet 신규 PSModule

`dotnet` 도구에 `PSModule` 템플릿이 있음을 알게 되었습니다.

위에서 설명한 모든 단계는 여전히 유효하지만 이 템플릿은 여러 단계를 생략합니다. 아직도 지속적으로 개선되고 있는 신규 템플릿입니다. 여기서도 계속 개선될 것입니다.

PSModule 템플릿은 이런 식으로 설치하고 사용합니다.

```powershell
dotnet new -i Microsoft.PowerShell.Standard.Module.Template
dotnet new psmodule
dotnet build
Import-Module "bin\Debug\netstandard2.0\$module.dll"
Get-Module $module
```

최소 실행 가능 템플릿은 .NET SDK와 PowerShell Standard Library 추가를 처리하고 프로젝트에 예제 클래스를 만듭니다. 이 템플릿은 바로 빌드하고 실행할 수 있습니다.

## <a name="important-details"></a>중요 세부 정보

이 문서를 끝내기 전에 다음과 같은 몇 가지 다른 세부 정보를 살펴보겠습니다.

### <a name="unloading-dlls"></a>DLL 언로드

이진 모듈이 로드되면 언로드할 수는 없습니다. DLL 파일은 사용자가 언로드할 때까지 잠금 상태가 됩니다. 변경 작업을 수행하고 빌드할 때마다 파일이 자주 잠기기 때문에 개발에 지장을 줄 수 있습니다. 이 문제를 확실하게 해결하는 유일한 방법은 DLL을 로드한 PowerShell 세션을 닫는 것입니다.

### <a name="vs-code-reload-window-action"></a>VS Code 창 다시 로드 작업

PowerShell 개발 작업 대부분을 [VS 코드][]에서 수행합니다. 이진 모듈(또는 클래스가 포함된 모듈)에서 작업할 때는 빌드할 때마다 VS Code를 다시 로드하곤 했습니다.
<kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>를 누르면 명령 창을 나타나며 `Reload Window`가 항상 목록 최상단에 표시됩니다.

### <a name="nested-powershell-sessions"></a>중첩된 PowerShell 세션

우수한 Pester 테스트 검사를 확보하는 것도 좋은 방법입니다. 그러면 build.ps1 스크립트를 수정하여 새 PowerShell 세션을 시작하고, 빌드를 수행하고, 테스트를 실행하고, 세션을 닫을 수 있습니다.

### <a name="updating-installed-modules"></a>설치된 모듈 업데이트

로컬로 설치한 모듈을 업데이트할 때 이러한 잠금이 방해가 될 수 있습니다. 모듈을 로드한 세션이 있다면 추적하여 닫아야 합니다. PSGallery에서 설치할 때는 큰 문제가 되지 않는데, 모듈 버전 지정에서 새 모듈을 다른 폴더에 배치하기 때문입니다.

로컬 PSGallery를 설정하고 빌드의 일부로 게시할 수 있습니다. 그러면 PSGallery에서 로컬 설치를 수행합니다. 일이 많아 보이지만 docker 컨테이너를 시작하는 것만큼 간단합니다. [PSRepository에 NuGet 서버 사용][]이라는 제 게시물에서 방법을 확인할 수 있습니다.

## <a name="why-binary-modules"></a>이진 모듈이란 무엇일까요?

이진 모듈을 만드는 방법부터 설명했고 만드는 이유는 설명하지 않았습니다. 현실에서는 C#을 작성하고 PowerShell Cmdlet 및 함수에 대한 쉬운 액세스는 포기해야 합니다. 바로 이점 때문에 이진 모듈을 바로 설명하지 않습니다.

하지만 다른 많은 PowerShell 명령에 의존하지 않는 모듈을 만든다면 성능 혜택이 대단히 중요할 수 있습니다. C#에 드롭하면 PowerShell이 유발하는 오버헤드를 줄일 수 있습니다. PowerShell은 컴퓨터가 아닌 관리자를 위해 최적화되었으며 따라서 약간의 오버헤드가 추가됩니다.

작업 시에는 JSON 및 해시 테이블을 이용해 수많은 일을 수행하는 중요 프로세스를 진행하게 됩니다. PowerShell을 최대한 최적화했지만 이 프로세스는 지금도 12분 동안 실행됩니다. 모듈에는 이미 다양한 C# PowerShell이 포함되어 있습니다. 따라서 이진 모듈로의 변환을 쉽고 깔끔하게 수행할 수 있습니다. 변환 덕분에 프로세스 시간이 12분 이상에서 4분 이내로 단축되었습니다.

### <a name="hybrid-modules"></a>하이브리드 모듈

PowerShell 고급 함수를 사용하여 이진 Cmdlet을 혼합할 수 있습니다. 이 가이드에서 수행하는 작업이기도 합니다. 스크립트 모듈 관련 사항은 모두 동일한 방식으로 적용됩니다.
오늘 만든 빈 `psm1` 파일이 있으니 나중에 다른 PowerShell 함수에 드롭할 수 있습니다.

우리가 만든 거의 모든 컴파일된 cmdlet은 먼저 PowerShell 함수로 실행됩니다. 우리의 모든 이진 모듈은 실제로는 하이브리드 모듈입니다.

### <a name="build-scripts"></a>빌드 스크립트

여기서는 간단한 빌드 스크립트만 사용했습니다. 보통은 긴 `Invoke-Build` 스크립트를 CI/CD 파이프라인의 일부로 사용합니다. Pester 테스트 실행, PSScriptAnalyzer 실행, 버전 지정 관리, PSGallery에 게시 같은 놀라운 작업을 수행합니다. 제 모듈에 빌드 스크립트를 사용했을 때 추가할 항목 다수를 발견할 수 있었습니다.

## <a name="final-thoughts"></a>맺음말

이진 모듈은 쉽게 만들 수 있습니다. C# 구문을 이용한 Cmdlet 제작은 다루지 않았지만 [Windows PowerShell SDK][]에서 다양한 문서를 확인할 수 있습니다. C#을 심층적으로 살펴보기 전의 준비 단계로 탁월한 효과가 있을 것입니다.

<!-- link references -->
[원래 버전]: https://powershellexplained.com/2018-08-04-Powershell-Standard-Library-Binary-Module/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[PowerShell Standard Library]: https://github.com/PowerShell/PowerShellStandard
[플랫폼 간 이진 모듈 만들기]: https://github.com/PowerShell/PowerShell/blob/master/docs/cmdlet-example/command-line-simple-example.md
[dotnet core SDK]: https://www.microsoft.com/net/download/core
[PSRepository에 NuGet 서버 사용]: https://powershellexplained.com/2018-03-03-Powershell-Using-a-NuGet-server-for-a-PSRepository/
[Windows PowerShell SDK]: /powershell/scripting/developer/windows-powershell-reference
[VS 코드]: https://code.visualstudio.com
[nuget 패키지]: https://www.nuget.org/packages/PowerShellStandard.Library/
