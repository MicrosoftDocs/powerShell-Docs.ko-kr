---
ms.date: 10/17/2017
title: 시험판 스크립트 버전
description: PowerShellGet 모듈은 의미 체계 버전 관리를 사용하여 1.0.0보다 큰 버전에 스크립트 태그 지정 지원을 시험판으로 제공합니다.
ms.openlocfilehash: e9873a69148fd80553e566b31c7455a4ecaee5ce
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92661470"
---
---
# <a name="prerelease-versions-of-scripts"></a>시험판 스크립트 버전

버전 1.6.0부터 PowerShellGet 및 PowerShell 갤러리에서 시험판으로 1.0.0보다 큰 버전에 대한 태그 지정을 지원합니다. 이 기능이 출시되기 전에는 시험판 패키지가 0으로 시작하는 버전으로 제한되었습니다. 이러한 기능의 목표는 PowerShell 버전 3 이상 또는 기존 PowerShellGet 버전 및 이전 버전과의 호환성을 손상하지 않으면서 [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) 버전 관리 규칙을 더 효율적으로 지원하기 위한 것입니다. 이 항목에서는 스크립트의 특정 기능에 중점을 둡니다. 모듈에 해당하는 기능은 [시험판 모듈 버전](module-prerelease-support.md) 항목에 있습니다. 게시자는 먼저 이러한 기능을 사용하여 스크립트를 2.5.0-alpha 버전으로 식별하고, 나중에 해당 시험판 버전을 대체하는 2.5.0 프로덕션 준비 버전을 출시할 수 있습니다.

상위 수준의 시험판 스크립트 기능은 다음과 같습니다.

- PrereleaseString 접미사를 스크립트 매니페스트의 버전 문자열에 추가합니다. 스크립트가 PowerShell 갤러리에 게시되면 매니페스트에서 이 데이터를 추출하여 시험판 패키지를 식별하는 데 사용합니다.
- 시험판 패키지를 가져오려면 ind-Script, Install-Script, Update-Scrip 및 Save-Script PowerShellGet 명령에 -AllowPrerelease 플래그를 추가해야 합니다. 플래그를 지정하지 않으면 시험판 패키지가 표시되지 않습니다.
- Find-Script, Get-InstalledScript 및 PowerShell 갤러리에 표시되는 스크립트 버전은 2.5.0-alpha와 같이 PrereleaseString과 함께 표시됩니다.

기능에 대한 자세한 내용은 아래에 나와 있습니다.

## <a name="identifying-a-script-version-as-a-prerelease"></a>스크립트 버전을 시험판 버전으로 식별

시험판 버전에 대한 PowerShellGet 지원에 있어 모듈보다 스크립트를 사용하는 것이 더 쉽습니다. 스크립트 버전은 PowerShellGet에서만 지원되므로 시험판 문자열을 추가함으로써 발생하는 호환성 문제가 없습니다. PowerShell 갤러리에서 스크립트를 시험판으로 식별하려면 스크립트 메타데이터에 있는 올바른 형식의 버전 문자열에 시험판 접미사를 추가합니다.

시험판 버전이 있는 스크립트 매니페스트의 예제 섹션은 다음과 같습니다.

```powershell
<#PSScriptInfo

.VERSION 3.2.1-alpha12

.GUID

...

#>
```

시험판 접미사를 사용하려면 버전 문자열이 다음 요구 사항을 충족해야 합니다.

- Version이 Major.Minor.Build에 해당하는 3개 세그먼트로 구성된 경우에만 시험판 접미사를 지정할 수 있습니다.
  이는 SemVer v1.0.0과 일치합니다.
- 시험판 접미사는 하이픈으로 시작하는 문자열이며, ASCII 영숫자[0-9, A-Z, a-z, -]를 포함할 수 있습니다.
- 현재 SemVer v1.0.0 시험판 문자열만 지원되므로 시험판 접미사에는 SemVer 2.0에서 허용되는 기간 또는 +[.+]는 **포함될 수 없습니다**.
- 지원되는 PrereleaseString 문자열의 예: -alpha, -alpha1, -BETA, -update20171020

### <a name="prerelease-versioning-impact-on-sort-order-and-installation-folders"></a>정렬 순서 및 설치 폴더에 대한 시험판 버전 관리 효과

시험판 버전을 사용하면 정렬 순서가 변경됩니다. 이는 PowerShell 갤러리에 게시할 때 및 PowerShellGet 명령을 사용하여 스크립트를 설치할 때 중요합니다. 버전 번호가 포함된 두 개의 스크립트 버전이 있는 경우 정렬 순서는 하이픈 다음의 문자열 부분을 기반으로 합니다. 따라서 2.5.0-alpha 버전은 2.5.0-beta보다 낮으며, 2.5.0-beta는 2.5.0-gamma보다 낮습니다. 두 스크립트에 동일한 버전 번호가 있고 그 중 하나에만 PrereleaseString이 있는 경우, 시험판 접미사가 **없는** 스크립트가 프로덕션 준비 버전으로 간주되며 시험판 버전보다 높은 버전으로 정렬됩니다. 예를 들어 릴리스 2.5.0과 2.5.0-beta를 비교하는 경우 2.5.0 버전이 두 버전 중 더 높은 버전으로 간주됩니다.

PowerShell 갤러리에 게시할 때 게시되는 스크립트의 버전은 기본적으로 PowerShell 갤러리에 있는 이전에 게시한 버전보다 더 높은 버전이어야 합니다. 게시자는 2.5.0-alpha 버전을 2.5.0-beta 또는 2.5.0(시험판 접미사 없음)으로 업데이트할 수 있습니다.

## <a name="finding-and-acquiring-prerelease-packages-using-powershellget-commands"></a>PowerShellGet 명령으로 시험판 패키지 찾기 및 가져오기

Find-Script, Install-Script, Update-Script 및 Save-Script PowerShellGet 명령을 사용하여 시험판 패키지를 처리하려면 -AllowPrerelease 플래그를 추가해야 합니다. -AllowPrerelease 플래그를 지정하면 시험판 패키지가 있는 경우 해당 패키지가 포함됩니다. -AllowPrerelease 플래그를 지정하지 않으면 시험판 패키지가 표시되지 않습니다.

PowerShellGet 스크립트 명령에서 이 플래그에 대한 유일한 예외로 Get-InstalledScript 및 Uninstall-Script를 사용하는 일부 경우가 있습니다.

- 버전 문자열에 시험판 정보가 있으면 Get-InstalledScript는 항상 해당 정보를 자동으로 표시합니다.
- **지정된 버전이 없는 경우** Uninstall-Script는 기본적으로 스크립트의 최신 버전을 제거합니다. 해당 동작은 변경되지 않았습니다. 그러나 `-RequiredVersion`을 사용하여 시험판 버전이 지정되는 경우 `-AllowPrerelease`가 필요합니다.

## <a name="examples"></a>예

```powershell
# Assume the PowerShell Gallery has TestPackage versions 1.8.0 and 1.9.0-alpha.
# If -AllowPrerelease is not specified, only version 1.8.0 will be returned.
C:\windows\system32> Find-Script TestPackage

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
1.8.0          TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> Find-Script TestPackage -AllowPrerelease

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
1.9.0-alpha    TestPackage                         PSGallery            Package used to validate changes to PowerShe...

# To install a prerelease, you must specify -AllowPrerelease. Specifying a prerelease version string is not sufficient.

C:\windows\system32> Install-Script TestPackage -RequiredVersion 1.9.0-alpha

PackageManagement\Find-Package : No match was found for the specified search criteria and script name 'TestPackage'.
Try Get-PSRepository to see all available registered script repositories.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.6.0\PSModule.psm1:1455 char:3
+         PackageManagement\Find-Package @PSBoundParameters | Microsoft ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...ets.FindPackage:FindPackage)[Find-Package], Exception
    + FullyQualifiedErrorId : NoMatchFoundForCriteria,Microsoft.PowerShell.PackageManagement.Cmdlets.FindPackage

# The previous command failed because -AllowPrerelease was not specified.
# Adding -AllowPrerelease will result in success.

C:\windows\system32> Install-Script TestPackage -RequiredVersion 1.9.0-alpha -AllowPrerelease
C:\windows\system32> Get-InstalledScript TestPackage

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-alpha     TestPackage                         PSGallery            Package used to validate changes to PowerShe...

# Note that Get-InstalledScript shows the prerelease version.
# If -RequiredVersion is not specified, all installed scripts will be displayed by Get-InstalledScript
```

-RequiredVersion이 제공되지 않은 경우 Uninstall-Script는 현재 버전의 스크립트를 제거합니다.
-RequiredVersion을 지정하고 시험판인 경우 -AllowPrerelease를 명령에 추가해야 합니다.

``` powershell
C:\windows\system32> Get-InstalledScript TestPackage

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-alpha     TestPackage                         PSGallery            Package used to validate changes to PowerShe...

C:\windows\system32> Uninstall-Script TestPackage -RequiredVersion 1.9.0-alpha
Uninstall-Script: The '-AllowPrerelease' parameter must be specified when using the Prerelease string in
MinimumVersion, MaximumVersion, or RequiredVersion.
At line:1 char:1
+ Uninstall-Script TestPackage -RequiredVersion 1.9.0-beta
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Uninstall-Script], ArgumentException
    + FullyQualifiedErrorId : AllowPrereleaseRequiredToUsePrereleaseStringInVersion,Uninstall-script


C:\windows\system32> Uninstall-Script TestPackage -RequiredVersion 1.9.0-alpha -AllowPrerelease
# Since script versions are not installed side-by-side, the above could be simply "Uninstall-Script TestPackage"

C:\windows\system32> Get-Installedscript TestPackage
PackageManagement\Get-Package : No match was found for the specified search criteria and script names 'testpackage'.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.5.0.0\PSModule.psm1:4088 char:9
+         PackageManagement\Get-Package @PSBoundParameters | Microsoft. ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...lets.GetPackage:GetPackage) [Get-Package], Exception
    + FullyQualifiedErrorId : NoMatchFound,Microsoft.PowerShell.PackageManagement.Cmdlets.GetPackage
```

## <a name="more-details"></a>자세한 내용

- [시험판 모듈 버전](module-prerelease-support.md)
- [Find-script](/powershell/module/powershellget/find-script)
- [Install-script](/powershell/module/powershellget/install-script)
- [Save-script](/powershell/module/powershellget/save-script)
- [Update-script](/powershell/module/powershellget/update-script)
- [Get-Installedscript](/powershell/module/powershellget/get-installedscript)
- [UnInstall-script](/powershell/module/powershellget/uninstall-script)
