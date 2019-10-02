---
ms.date: 09/26/2017
contributor: keithb
keywords: gallery,powershell,cmdlet,psget
title: 시험판 모듈 버전
ms.openlocfilehash: eced067dd21082de0db653daf3b838217154f1dd
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71328144"
---
# <a name="prerelease-module-versions"></a>시험판 모듈 버전

버전 1.6.0부터 PowerShellGet 및 PowerShell 갤러리에서 시험판으로 1.0.0보다 큰 버전에 대한 태그 지정을 지원합니다. 이 기능이 출시되기 전에는 시험판 패키지가 0으로 시작하는 버전으로 제한되었습니다. 이러한 기능의 목표는 PowerShell 버전 3 이상 또는 기존 PowerShellGet 버전 및 이전 버전과의 호환성을 손상하지 않으면서 [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) 버전 관리 규칙을 더 효율적으로 지원하기 위한 것입니다. 이 항목에서는 모듈의 특정 기능에 중점을 둡니다. 스크립트에 해당하는 기능은 [시험판 스크립트 버전](script-prerelease-support.md) 항목에 있습니다. 게시자는 먼저 이러한 기능을 사용하여 모듈 또는 스크립트를 2.5.0-alpha 버전으로 식별하고, 나중에 해당 시험판 버전을 대체하는 2.5.0 프로덕션 준비 버전을 출시할 수 있습니다.

상위 수준의 시험판 모듈 기능은 다음과 같습니다.

- 모듈 매니페스트의 PSData 섹션에 Prerelease 문자열을 추가하면 해당 모듈이 시험판 버전으로 식별됩니다. 모듈이 PowerShell 갤러리에 게시되면 매니페스트에서 이 데이터를 추출하여 시험판 패키지를 식별하는 데 사용합니다.
- 시험판 패키지를 가져오려면 PowerShellGet 명령 `Find-Module`, `Install-Module`, `Update-Module` 및 `Save-Module`에 `-AllowPrerelease` 플래그를 추가해야 합니다. 플래그를 지정하지 않으면 시험판 패키지가 표시되지 않습니다.
- `Find-Module`, `Get-InstalledModule` 및 PowerShell 갤러리에 표시되는 모듈 버전은 2.5.0-alpha와 같이 Prerelease 문자열이 추가된 단일 문자열로 표시됩니다.

기능에 대한 자세한 내용은 아래에 나와 있습니다.

이러한 변경 내용은 PowerShell에 기본 제공되는 모듈 버전 지원에 영향을 주지 않으며 PowerShell 3.0, 4.0 및 5와 호환됩니다.

## <a name="identifying-a-module-version-as-a-prerelease"></a>모듈 버전을 시험판 버전으로 식별

PowerShellGet으로 시험판 버전을 지원하려면 모듈 매니페스트 내에서 다음 두 필드를 사용해야 합니다.

- 시험판 버전이 사용되는 경우 모듈 매니페스트에 포함된 ModuleVersion이 세 부분으로 구성된 버전이어야 하며 기존 PowerShell 버전 관리를 준수해야 합니다. 버전 형식은 A.B.C이며, 여기서 A, B 및 C는 모두 정수입니다.
- Prerelease 문자열은 모듈 매니페스트에 있는PrivateData의 PSData 섹션에 지정됩니다.

Prerelease 문자열에 대한 자세한 요구 사항은 다음과 같습니다.

모듈을 시험판으로 정의하는 모듈 매니페스트의 예제 섹션은 다음과 같습니다.

```powershell
@{
    ModuleVersion = '2.5.0'
    #---
    PrivateData = @{
        PSData = @{
            Prerelease = 'alpha'
        }
    }
}
```

Prerelease 문자열의 세부 요구 사항은 다음과 같습니다.

- ModuleVersion이 Major.Minor.Build에 해당하는 3개 세그먼트로 구성된 경우에만 Prerelease 문자열을 지정할 수 있습니다. 이는 SemVer v1.0.0과 일치합니다.
- 하이픈은 Build 숫자와 Prerelease 문자열 사이의 구분 기호입니다. Prerelease 문자열에서 하이픈은 첫 번째 문자로만 포함될 수 있습니다.
- Prerelease 문자열에는 ASCII 영숫자[0-9, A-Z, a-z, -]만 포함될 수 있습니다. Prerelease 문자열은 alpha 문자로 시작하는 것이 좋습니다. 이렇게 하면 패키지 목록을 검색할 때 시험판 버전임을 쉽게 식별할 수 있기 때문입니다.
- 현재 SemVer v1.0.0 시험판 문자열만 지원됩니다. Prerelease 문자열에는 마침표 또는 +[.+]가 **포함되지 않아야** 하지만, SemVer 2.0에서는 허용됩니다.
- 지원되는 Prerelease 문자열의 예: -alpha, -alpha1, -BETA, -update20171020

### <a name="prerelease-versioning-impact-on-sort-order-and-installation-folders"></a>정렬 순서 및 설치 폴더에 대한 시험판 버전 관리 효과

시험판 버전을 사용하면 정렬 순서가 변경됩니다. 이는 PowerShell 갤러리에 게시할 때 및 PowerShellGet 명령을 사용하여 모듈을 설치할 때 중요합니다. 두 모듈에 대한 Prerelease 문자열이 지정되면 정렬 순서는 하이픈 다음의 문자열 부분을 기반으로 합니다. 따라서 2.5.0-alpha 버전은 2.5.0-beta보다 낮으며, 2.5.0-beta는 2.5.0-gamma보다 낮습니다. 두 모듈에 동일한 ModuleVersion이 있고 그 중 하나에만 Prerelease 문자열이 있는 경우, Prerelease 문자열이 없는 모듈이 프로덕션 준비 버전으로 간주되며 Prerelease 문자열이 포함된 시험판 버전보다 높은 버전으로 정렬됩니다. 예를 들어 릴리스 2.5.0과 2.5.0-beta를 비교하는 경우 2.5.0 버전이 두 버전 중 더 높은 버전으로 간주됩니다.

PowerShell 갤러리에 게시할 때 게시되는 모듈의 버전은 기본적으로 PowerShell 갤러리에 있는 이전에 게시한 버전보다 더 높은 버전이어야 합니다.

## <a name="finding-and-acquiring-prerelease-packages-using-powershellget-commands"></a>PowerShellGet 명령으로 시험판 패키지 찾기 및 가져오기

Find-Module, Install-Module, Update-Module 및 Save-Module PowerShellGet 명령을 사용하여 시험판 패키지를 처리하려면 -AllowPrerelease 플래그를 추가해야 합니다. -AllowPrerelease 플래그를 지정하면 시험판 패키지가 있는 경우 해당 패키지가 포함됩니다. -AllowPrerelease 플래그를 지정하지 않으면 시험판 패키지가 표시되지 않습니다.

PowerShellGet 모듈 명령에서 이 플래그에 대한 유일한 예외로 Get-InstalledModule 및 Uninstall-Module을 사용하는 일부 경우가 있습니다.

- Get-InstalledModule은 항상 모듈에 대한 버전 문자열에 있는 시험판 정보를 자동으로 표시합니다.
- __지정된 버전이 없는 경우__ Uninstall-Module은 기본적으로 모듈의 최신 버전을 제거합니다. 해당 동작은 변경되지 않았습니다. 그러나 -RequiredVersion을 사용하여 시험판 버전이 지정되는 경우 -AllowPrerelease가 필요합니다.

## <a name="examples"></a>예

PowerShell 갤러리에 TestPackage 모듈 버전 1.8.0 및 1.9.0-alpha가 있다고 가정합니다. `-AllowPrerelease`가 지정되지 않은 경우에는 버전 1.8.0만 반환됩니다.

```powershell
find-module TestPackage
```

```output
Version        Name           Repository  Description
-------        ----           ----------  -----------
1.8.0          TestPackage    PSGallery   Package used to validate changes to the PowerShe...
```

```powershell
find-module TestPackage -AllowPrerelease
```

```output
Version        Name           Repository  Description
-------        ----           ----------  -----------
1.9.0-alpha    TestPackage    PSGallery   Package used to validate changes to the PowerShe...
```

시험판을 설치하려면 항상 -AllowPrerelease를 지정합니다. 시험판 버전 문자열을 지정하는 것은 충분하지 않습니다.

```powershell
Install-module TestPackage -RequiredVersion 1.9.0-alpha
```

```output
PackageManagement\Find-Package : No match was found for the specified search criteria and module name 'TestPackage'.
Try Get-PSRepository to see all available registered module repositories.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.6.0\PSModule.psm1:1455 char:3
+         PackageManagement\Find-Package @PSBoundParameters | Microsoft ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...ets.FindPackage:FindPackage) [Find-Package], Exception
    + FullyQualifiedErrorId : NoMatchFoundForCriteria,Microsoft.PowerShell.PackageManagement.Cmdlets.FindPackage
```

-AllowPrerelease가 지정되지 않았으므로 이전 명령이 실패했습니다. `-AllowPrerelease`를 추가하면 성공합니다.

```powershell
Install-module TestPackage -RequiredVersion 1.9.0-alpha -AllowPrerelease
Get-InstalledModule TestPackage
```

```output
Version         Name          Repository  Description
-------         ----          ----------  -----------
1.9.0-alpha     TestPackage   PSGallery   Package used to validate changes to the PowerShe...
```

지정된 시험판으로 인해서만 다른 모듈 버전을 나란히 설치하는 것은 지원되지 않습니다. PowerShellGet을 사용하여 모듈을 설치할 때 ModuleVersion을 사용하여 폴더 이름을 만들어 동일한 모듈의 다른 버전을 나란히 설치합니다. 시험판 문자열이 없는 ModuleVersion이 폴더 이름으로 사용됩니다. 사용자가 MyModule 버전 2.5.0-alpha를 설치하면 `MyModule\2.5.0` 폴더에 설치됩니다. 그런 다음 사용자가 2.5.0-beta를 설치하면 2.5.0-beta 버전은 `MyModule\2.5.0` 폴더의 내용을 **덮어씁니다**. 이 방법의 장점 중 하나는 프로덕션 준비 버전을 설치한 후에 시험판 버전을 제거할 필요가 없다는 것입니다. 아래 예제에서는 예상되는 항목을 보여 줍니다.

``` powershell
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name           Repository  Description
-------         ----           ----------  -----------
1.9.0-alpha     TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.8.0           TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage    PSGallery   Package used to validate changes to the PowerShe...

C:\windows\system32> find-module TestPackage -AllowPrerelease

Version        Name            Repository  Description
-------        ----            ----------  -----------
1.9.0-beta     TestPackage     PSGallery   Package used to validate changes to the PowerShe...

C:\windows\system32> Update-Module TestPackage -AllowPrerelease
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name           Repository  Description
-------         ----           ----------  -----------
1.9.0-beta      TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.8.0           TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage    PSGallery   Package used to validate changes to the PowerShe...

```

-RequiredVersion이 제공되지 않은 경우 Uninstall-Module은 최신 버전의 모듈을 제거합니다.
-RequiredVersion을 지정하고 시험판인 경우 -AllowPrerelease를 명령에 추가해야 합니다.

``` powershell
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name           Repository  Description
-------         ----           ----------  -----------
2.0.0-alpha1    TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.9.0-beta      TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.8.0           TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage    PSGallery   Package used to validate changes to the PowerShe...

C:\windows\system32> Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta

Uninstall-Module : The '-AllowPrerelease' parameter must be specified when using the Prerelease string in
MinimumVersion, MaximumVersion, or RequiredVersion.
At line:1 char:1
+ Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Uninstall-Module], ArgumentException
    + FullyQualifiedErrorId : AllowPrereleaseRequiredToUsePrereleaseStringInVersion,Uninstall-Module

C:\windows\system32> Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta -AllowPrerelease
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name          Repository   Description
-------         ----          ----------   -----------
2.0.0-alpha1    TestPackage   PSGallery    Package used to validate changes to the PowerShe...
1.8.0           TestPackage   PSGallery    Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage   PSGallery    Package used to validate changes to the PowerShe...

C:\windows\system32> Uninstall-Module TestPackage
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name          Repository   Description
-------         ----          ----------   -----------
1.8.0           TestPackage   PSGallery    Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage   PSGallery    Package used to validate changes to the PowerShe...
```

## <a name="more-details"></a>자세한 내용

- [시험판 스크립트 버전](script-prerelease-support.md)
- [Find-Module](/powershell/module/powershellget/find-module)
- [Install-Module](/powershell/module/powershellget/install-module)
- [Save-Module](/powershell/module/powershellget/save-module)
- [Update-Module](/powershell/module/powershellget/Update-Module)
- [Get-InstalledModule](/powershell/module/powershellget/get-installedmodule)
- [UnInstall-Module](/powershell/module/powershellget/uninstall-module)
