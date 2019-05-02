---
ms.date: 12/14/2018
keywords: powershell,cmdlet
title: 이식 가능한 모듈 작성
ms.openlocfilehash: 38a93b5b030d58784b91292e2cd060b3a2c19a00
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086411"
---
# <a name="portable-modules"></a>이식 가능한 모듈

Windows PowerShell은 [.NET Framework][]용으로 작성되지만 PowerShell Core는 [.NET Core][]용으로 작성됩니다. 이식 가능한 모듈은 Windows PowerShell 및 PowerShell Core에서 모두 작동하는 모듈입니다. .NET Framework 및 .NET Core는 호환성이 높지만 사용 가능한 API에는 차이가 있습니다. Windows PowerShell 및 PowerShell Core에서 사용할 수 있는 API에도 차이가 있습니다. 두 환경에서 모두 사용할 수 있는 모듈이 이 차이를 인식해야 합니다.

## <a name="porting-an-existing-module"></a>기존 모듈 이식

### <a name="porting-a-pssnapin"></a>PSSnapIn 이식

PSSnapIn(PowerShell 스냅인)은 PowerShell Core에서 지원되지 않습니다. 그러나 PSSnapIn을 PowerShell 모듈로 변환하는 것은 간단합니다. 일반적으로 PSSnapIn 등록 코드는 [PSSnapIn][]에서 파생되는 클래스의 단일 원본 파일에 있습니다. 빌드에서 이 원본 파일을 제거하세요. 이 파일은 더 이상 필요하지 않습니다.

[New-ModuleManifest][]를 사용하여 PSSnapIn 등록 코드를 사용할 필요가 없는 새 모듈 매니페스트를 만듭니다. PSSnapIn의 일부 값(예: Description)은 모듈 매니페스트 내에서 다시 사용할 수 있습니다.

모듈 매니페스트의 `RootModule` 속성은 cmdlet을 구현하는 어셈블리(dll)의 이름으로 설정해야 합니다.

### <a name="the-net-portability-analyzer-aka-apiport"></a>.NET 이식성 분석기(APIPort)

Windows PowerShell용으로 작성된 모듈을 PowerShell Core에서 작동하도록 이식하려면 [.NET 이식성 분석기][]로 시작합니다. 컴파일된 어셈블리에서 이 도구를 실행하여 모듈에서 사용되는 .NET API가 .NET Framework, .NET Core 및 기타 .NET 런타임과 호환되는지 확인합니다. 대체 API가 있는 경우, 이 도구에서는 대체 API를 제안합니다. 제안이 없는 경우 [런타임 검사][]를 추가하고 특정 런타임에서 사용할 수 없는 기능을 제한해야 할 수 있습니다.

## <a name="creating-a-new-module"></a>새 모듈 만들기

새 모듈을 만드는 경우 [.NET CLI][]를 사용하는 것이 좋습니다.

### <a name="installing-the-powershell-standard-module-template"></a>PowerShell Standard 모듈 템플릿 설치

.NET CLI가 설치된 후 템플릿 라이브러리를 설치하여 간단한 PowerShell 모듈을 생성합니다.
이 모듈은 Windows PowerShell, PowerShell Core, Windows, Linux 및 macOS와 호환됩니다.

다음 예제에서는 템플릿 설치 방법을 보여 줍니다.

```powershell
dotnet new -i Microsoft.PowerShell.Standard.Module.Template
```

```output
  Restoring packages for C:\Users\Steve\.templateengine\dotnetcli\v2.1.302\scratch\restore.csproj...
  Installing Microsoft.PowerShell.Standard.Module.Template 0.1.3.
  Generating MSBuild file C:\Users\Steve\.templateengine\dotnetcli\v2.1.302\scratch\obj\restore.csproj.nuget.g.props.
  Generating MSBuild file C:\Users\Steve\.templateengine\dotnetcli\v2.1.302\scratch\obj\restore.csproj.nuget.g.targets.
  Restore completed in 1.66 sec for C:\Users\Steve\.templateengine\dotnetcli\v2.1.302\scratch\restore.csproj.

Usage: new [options]

Options:
  -h, --help          Displays help for this command.
  -l, --list          Lists templates containing the specified name. If no name is specified, lists all templates.
  -n, --name          The name for the output being created. If no name is specified, the name of the current directory is used.
  -o, --output        Location to place the generated output.
  -i, --install       Installs a source or a template pack.
  -u, --uninstall     Uninstalls a source or a template pack.
  --nuget-source      Specifies a NuGet source to use during install.
  --type              Filters templates based on available types. Predefined values are "project", "item" or "other".
  --force             Forces content to be generated even if it would change existing files.
  -lang, --language   Filters templates based on language and specifies the language of the template to create.


Templates                                         Short Name         Language          Tags
----------------------------------------------------------------------------------------------------------------------------
Console Application                               console            [C#], F#, VB      Common/Console
Class library                                     classlib           [C#], F#, VB      Common/Library
PowerShell Standard Module                        psmodule           [C#]              Library/PowerShell/Module
...
```

### <a name="creating-a-new-module-project"></a>새 모듈 프로젝트 만들기

템플릿이 설치된 후 템플릿을 사용하여 새 PowerShell 모듈 프로젝트를 만들 수 있습니다. 이 예제에서 샘플 모듈을 'myModule'이라고 합니다.

```
PS> mkdir myModule

    Directory: C:\Users\Steve

Mode LastWriteTime Length Name
---- ------------- ------ ----
d----- 8/3/2018 2:41 PM myModule

PS> cd myModule
PS C:\Users\Steve\myModule> dotnet new psmodule

The template "PowerShell Standard Module" was created successfully.

Processing post-creation actions...
Running 'dotnet restore' on C:\Users\Steve\myModule\myModule.csproj...
  Restoring packages for C:\Users\Steve\myModule\myModule.csproj...
  Installing PowerShellStandard.Library 5.1.0.
  Generating MSBuild file C:\Users\Steve\myModule\obj\myModule.csproj.nuget.g.props.
  Generating MSBuild file C:\Users\Steve\myModule\obj\myModule.csproj.nuget.g.targets.
  Restore completed in 1.76 sec for C:\Users\Steve\myModule\myModule.csproj.

Restore succeeded.
```

### <a name="building-the-module"></a>모듈 빌드

표준 .NET CLI 명령을 사용하여 프로젝트를 빌드합니다.

```powershell
dotnet build
```

```output
PS C:\Users\Steve\myModule> dotnet build
Microsoft (R) Build Engine version 15.7.179.6572 for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

  Restore completed in 76.85 ms for C:\Users\Steve\myModule\myModule.csproj.
  myModule -> C:\Users\Steve\myModule\bin\Debug\netstandard2.0\myModule.dll

Build succeeded.
    0 Warning(s)
    0 Error(s)

Time Elapsed 00:00:05.40
```

### <a name="testing-the-module"></a>모듈 테스트

모듈을 빌드한 후 모듈을 가져오고 샘플 cmdlet을 실행할 수 있습니다.

```powershell
ipmo .\bin\Debug\netstandard2.0\myModule.dll
Test-SampleCmdlet -?
Test-SampleCmdlet -FavoriteNumber 7 -FavoritePet Cat
```

```output
PS C:\Users\Steve\myModule> ipmo .\bin\Debug\netstandard2.0\myModule.dll
PS C:\Users\Steve\myModule> Test-SampleCmdlet -?

NAME
    Test-SampleCmdlet

SYNTAX
    Test-SampleCmdlet [-FavoriteNumber] <int> [[-FavoritePet] {Cat | Dog | Horse}] [<CommonParameters>]


ALIASES
    None


REMARKS
    None


PS C:\Users\Steve\myModule> Test-SampleCmdlet -FavoriteNumber 7 -FavoritePet Cat

FavoriteNumber FavoritePet
-------------- -----------
             7 Cat
```

다음 섹션에서는 이 템플릿에서 사용되는 일부 기술을 자세히 설명합니다.

## <a name="net-standard-library"></a>.NET Standard 라이브러리

[.NET Standard][]는 모든 .NET 구현에서 사용할 수 있는 .NET API의 공식 사양입니다. .NET Standard를 대상으로 하는 관리 코드는 .NET Standard의 해당 버전과 호환되는 .NET Framework 및 .NET Core 버전에서 작동합니다.

> [!NOTE]
> .NET Standard에 API가 있을 수 있지만 .NET Core의 API 구현에서 런타임에 `PlatformNotSupportedException`이 throw될 수 있으므로, Windows PowerShell 및 PowerShell Core와 호환되는지 확인하려면 두 환경에서 모두 모듈 테스트를 실행하는 것이 좋습니다.
> 모듈을 플랫폼 간에 사용해야 하는 경우 Linux 및 macOS에서도 테스트를 실행합니다.

.NET Standard를 대상으로 지정하면 모듈이 발전됨에 따라 호환되지 않은 API가 실수로 모듈에 도입되지 않도록 할 수 있습니다. 비호환성은 런타임이 아니라 컴파일 시간에 검색됩니다.

그러나 호환되는 API를 사용한다면 모듈을 Windows PowerShell 및 PowerShell Core에서 모두 작동하기 위해 .NET Standard를 대상으로 지정할 필요가 없습니다. IL(중간 언어)은 두 런타임 간에 호환됩니다. .NET Standard 2.0과 호환되는 .NET Framework 4.6.1을 대상으로 지정할 수 있습니다. .NET Standard 2.0 외부에서 API를 사용하지 않는 경우에는 다시 컴파일하지 않고도 모듈이 PowerShell Core 6에서 작동합니다.

## <a name="powershell-standard-library"></a>PowerShell Standard Library

[PowerShell Standard][] 라이브러리는 해당 표준 버전 이상의 모든 PowerShell 버전에서 사용할 수 있는 PowerShell API의 공식 사양입니다.

예를 들어 [PowerShell Standard 5.1][]은 Windows PowerShell 5.1 및 PowerShell Core 6.0 이상과 호환됩니다.

PowerShell Standard Library를 사용하여 모듈을 컴파일하는 것이 좋습니다. 라이브러리를 사용하면 API가 Windows PowerShell 및 PowerShell Core 6에서 모두 사용 가능하고 구현됩니다.
PowerShell Standard는 항상 상위 버전과 호환됩니다. PowerShell Standard Library 5.1을 사용하여 구축된 모듈은 항상 PowerShell의 상위 버전과 호환됩니다.

## <a name="module-manifest"></a>모듈 매니페스트

### <a name="indicating-compatibility-with-windows-powershell-and-powershell-core"></a>Windows PowerShell 및 PowerShell Core와의 호환성 표시

모듈이 Windows PowerShell 및 PowerShell Core에서 모두 작동하는지 유효성을 검사한 후 모듈 매니페스트에서 [CompatiblePSEditions][] 속성을 사용하여 호환성을 명시적으로 표시해야 합니다. `Desktop` 값은 모듈이 Windows PowerShell과 호환됨을 의미하지만, `Core` 값은 모듈이 PowerShell Core와 호환됨을 의미합니다. `Desktop` 및 `Core`를 둘 다 포함하면 모듈이 Windows PowerShell 및 PowerShell Core와 모두 호환됨을 의미합니다.

> [!NOTE]
> `Core`는 자동으로 모듈이 Windows, Linux 및 macOS아 호환됨을 의미하지 않습니다.
> **CompatiblePSEditions** 속성은 PowerShell v5에서 도입되었습니다. **CompatiblePSEditions** 속성을 사용하는 모듈 매니페스트는 PowerShell v5 이전 버전에 로드되지 않습니다.

### <a name="indicating-os-compatibility"></a>OS 호환성 표시

먼저 모듈이 Linux 및 macOS에서 작동하는지 유효성을 검사합니다. 다음으로, 모듈 매니페스트에서 해당 운영 체제와의 호환성을 표시합니다. 이렇게 하면 모듈이 [PowerShell 갤러리][]에 게시되는 경우 사용자가 사용 중인 운영 체제용 모듈을 더 쉽게 찾을 수 있습니다.

모듈 매니페스트 내에서 `PrivateData` 속성에는 `PSData` 하위 속성이 있습니다. `PSData`의 선택적 `Tags` 속성은 PowerShell 갤러리에 표시되는 값 배열을 사용합니다. PowerShell 갤러리는 다음 호환성 값을 지원합니다.

| 태그               | 설명                                |
|-------------------|--------------------------------------------|
| PSEdition_Core    | PowerShell Core 6과 호환 가능          |
| PSEdition_Desktop | Windows PowerShell과 호환 가능         |
| Windows           | Windows와 호환 가능                    |
| Linux             | Linux와 호환 가능(특정 배포판 없음) |
| macOS             | macOS와 호환 가능                      |

예:

```powershell
@{
    GUID = "4ae9fd46-338a-459c-8186-07f910774cb8"
    Author = "Microsoft Corporation"
    CompanyName = "Microsoft Corporation"
    Copyright = "(C) Microsoft Corporation. All rights reserved."
    HelpInfoUri = "https://go.microsoft.com/fwlink/?linkid=855962"
    ModuleVersion = "1.2.4"
    PowerShellVersion = "3.0"
    ClrVersion = "4.0"
    RootModule = "PackageManagement.psm1"
    Description = 'PackageManagement (a.k.a. OneGet) is a new way to discover and install software packages from around the web.
 It is a manager or multiplexer of existing package managers (also called package providers) that unifies Windows package management with a single Windows PowerShell interface. With PackageManagement, you can do the following.
  - Manage a list of software repositories in which packages can be searched, acquired and installed
  - Discover software packages
  - Seamlessly install, uninstall, and inventory packages from one or more software repositories'

    CmdletsToExport = @(
        'Find-Package',
        'Get-Package',
        'Get-PackageProvider',
        'Get-PackageSource',
        'Install-Package',
        'Import-PackageProvider'
        'Find-PackageProvider'
        'Install-PackageProvider'
        'Register-PackageSource',
        'Set-PackageSource',
        'Unregister-PackageSource',
        'Uninstall-Package'
        'Save-Package'
    )

    FormatsToProcess  = @('PackageManagement.format.ps1xml')

    PrivateData = @{
        PSData = @{
            Tags = @('PackageManagement', 'PSEdition_Core', 'PSEdition_Desktop', 'Windows', 'Linux', 'macOS')
            ProjectUri = 'https://oneget.org'
        }
    }
}
```

<!-- reference links -->
[.NET Framework]: /dotnet/framework/
[.NET Core]: /dotnet/core/
[PSSnapIn]: /dotnet/api/system.management.automation.pssnapin
[New-ModuleManifest]: /powershell/module/microsoft.powershell.core/new-modulemanifest
[런타임 검사]: /dotnet/api/system.runtime.interopservices.runtimeinformation.frameworkdescription#System_Runtime_InteropServices_RuntimeInformation_FrameworkDescription
[.NET CLI]: /dotnet/core/tools/?tabs=netcore2x
[.NET Standard]: /dotnet/standard/net-standard
[PowerShell Standard]: https://github.com/PowerShell/PowerShellStandard
[PowerShell Standard 5.1]: https://www.nuget.org/packages/PowerShellStandard.Library/5.1.0
[PowerShell 갤러리]: https://www.powershellgallery.com
[.NET 이식성 분석기]: https://github.com/Microsoft/dotnet-apiport
[CompatiblePSEditions]: /powershell/gallery/concepts/module-psedition-support
