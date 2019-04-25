---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 7ad95f288e2eb7cb68341a4932500a20e7740236
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085102"
---
# <a name="powershellget-cmdlets-for-module-management"></a>모듈 관리를 위한 PowerShellGet Cmdlet

- [Find-DscResource](https://technet.microsoft.com/library/mt654006.aspx)
- [Find-Module](https://technet.microsoft.com/library/dn807167.aspx)
- [Find-Script](https://technet.microsoft.com/library/mt654001.aspx)
- [Get-InstalledModule](https://technet.microsoft.com/library/mt653990.aspx)
- [Get-InstalledScript](https://technet.microsoft.com/library/mt653994.aspx)
- [Get-PSRepository](https://technet.microsoft.com/library/dn807170.aspx)
- [Install-Module](https://technet.microsoft.com/library/dn807162.aspx)
- [Install-Script](https://technet.microsoft.com/library/mt653998.aspx)
- [New-ScriptFileInfo](https://technet.microsoft.com/library/mt653995.aspx)
- [Publish-Module](https://technet.microsoft.com/library/dn807163.aspx)
- [Publish-Script](https://technet.microsoft.com/library/mt654003.aspx)
- [Register-PSRepository](https://technet.microsoft.com/library/dn807168.aspx)
- [Save-Module](https://technet.microsoft.com/library/mt653992.aspx)
- [Save-Script](https://technet.microsoft.com/library/mt654004.aspx)
- [Set-PSRepository](https://technet.microsoft.com/library/dn807165.aspx)
- [Test-ScriptFileInfo](https://technet.microsoft.com/library/mt654005.aspx)
- [Uninstall-Module](https://technet.microsoft.com/library/mt653996.aspx)
- [Uninstall-Script](https://technet.microsoft.com/library/mt653989.aspx)
- [Update-Module](https://technet.microsoft.com/library/dn807166.aspx)
- [Update-ModuleManifest](https://technet.microsoft.com/library/mt654002.aspx)
- [Update-Script](https://technet.microsoft.com/library/mt653997.aspx)
- [Update-ScriptFileInfo](https://technet.microsoft.com/library/mt653991.aspx)
- [Unregister-PSRepository](https://technet.microsoft.com/library/dn807161.aspx)

## <a name="module-dependency-installation-support-get-installedmodule-and-uninstall-module-cmdlets"></a>모듈 종속성 설치 지원, Get-InstalledModule 및 Uninstall-Module cmdlet

- Publish-Module cmdlet에서 모듈 종속성 채우기를 추가했습니다. PSModuleInfo의 RequiredModules 및 NestedModules 목록은 게시할 모듈의 종속성 목록을 준비하는 데 사용됩니다.
- Install-Module 및 Update-Module cmdlet에서 종속성 설치 지원을 추가했습니다. 모듈 종속성이 기본적으로 설치되고 업데이트됩니다.
- 결과에 모듈 종속성을 포함하도록 Find-Module cmdlet에 -IncludeDependencies 매개 변수를 추가했습니다.
- Find-Module, Install-Module 및 Update-Module cmdlet에서 -MaximumVersion 지원을 추가했습니다.
- 새로운 Get-InstalledModule 및 Uninstall-Module cmdlet을 추가했습니다.

## <a name="powershellget-cmdlets-demo-with-module-dependencies-support"></a>모듈 종속성이 지원되는 PowerShellGet cmdlet 데모:

### <a name="ensure-that-module-dependencies-are-available-on-the-repository"></a>리포지토리에서 모듈 종속성을 사용할 수 있는지 확인합니다.

```powershell
Find-Module -Repository LocalRepo -Name RequiredModule1,RequiredModule2,RequiredModule3,NestedRequiredModule1,NestedRequiredModule2,NestedRequiredModule3 | Sort-Object -Property Name

Version    Name                     Repository    Description
-------    ----                     ----------    -----------
2.5        NestedRequiredModule1    LocalRepo     NestedRequiredModule1 module
2.5        NestedRequiredModule2    LocalRepo     NestedRequiredModule2 module
2.0        NestedRequiredModule3    LocalRepo     NestedRequiredModule3 module
2.5        RequiredModule1          LocalRepo     RequiredModule1 module
2.5        RequiredModule2          LocalRepo     RequiredModule2 module
2.0        RequiredModule3          LocalRepo     RequiredModule3 module
```

### <a name="create-a-module-with-dependencies-that-are-specified-in-the-requiredmodules-and-nestedmodules-properties-of-its-module-manifest"></a>모듈 매니페스트의 RequiredModules 및 NestedModules 속성에 지정된 종속성이 있는 모듈을 만듭니다.

```powershell
$RequiredModules = @('RequiredModule1',
                     @{ModuleName = 'RequiredModule2'; ModuleVersion = '1.5'; },
                     @{ModuleName = 'RequiredModule3'; RequiredVersion = '2.0'; })

$NestedRequiredModules = @('TestDepWithNestedRequiredModules1.psm1', 'NestedRequiredModule1',
                            @{ModuleName = 'NestedRequiredModule2'; ModuleVersion = '1.5'; },
                            @{ModuleName = 'NestedRequiredModule3'; RequiredVersion = '2.0'; })

New-ModuleManifest -Path 'C:\Program Files\WindowsPowerShell\Modules\TestDepWithNestedRequiredModules1\TestDepWithNestedRequiredModules1.psd1' `
-NestedModules $NestedRequiredModules -RequiredModules $RequiredModules -ModuleVersion "1.0" -Description "TestDepWithNestedRequiredModules1 module"
```

### <a name="publish-two-versions-10-and-20-of-the-testdepwithnestedrequiredmodules1-module-with-dependencies-to-the-repository"></a>종속성이 있는 TestDepWithNestedRequiredModules1 모듈의 두 버전(**“1.0”** 및 **“2.0”**)을 리포지토리에 게시합니다.

```powershell
Publish-Module -Name TestDepWithNestedRequiredModules1 -Repository LocalRepo -NuGetApiKey "MyNuGet-ApiKey-For-LocalRepo"
```

### <a name="find-the-testdepwithnestedrequiredmodules1-module-with-its-dependencies-by-specifying--includedependencies"></a>-IncludeDependencies를 지정하여 종속성이 있는 TestDepWithNestedRequiredModules1 모듈을 찾습니다.

```powershell
Find-Module -Name TestDepWithNestedRequiredModules1 -Repository LocalRepo –IncludeDependencies -MaximumVersion "1.0"

Version    Name                                Repository  Description
-------    ----                                ----------  -----------
1.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module
2.5        RequiredModule1                     LocalRepo   RequiredModule1 module
2.5        RequiredModule2                     LocalRepo   RequiredModule2 module
2.0        RequiredModule3                     LocalRepo   RequiredModule3 module
2.5        NestedRequiredModule1               LocalRepo   NestedRequiredModule1 module
2.5        NestedRequiredModule2               LocalRepo   NestedRequiredModule2 module
2.0        NestedRequiredModule3               LocalRepo   NestedRequiredModule3 module
```

### <a name="use-find-module-metadata-to-find-the-module-dependencies"></a>Find-Module 메타데이터를 사용하여 모듈 종속성을 찾습니다.

```powershell
$psgetModuleInfo = Find-Module -Repository MSPSGallery -Name ModuleWithDependencies2
$psgetModuleInfo.Dependencies.ModuleName

RequiredModule1
RequiredModule2
RequiredModule3
NestedRequiredModule1
NestedRequiredModule2
NestedRequiredModule3

$psgetModuleInfo.Dependencies

Name Value
---- -----
ModuleName RequiredModule1
CanonicalId PowerShellGet:RequiredModule1/#http://psget/psGallery/api/v2/

ModuleName RequiredModule2
ModuleVersion 2.0
CanonicalId PowerShellGet:RequiredModule2/2.0#http://psget/psGallery/api/v2/

ModuleName RequiredModule3
RequiredVersion 2.5
CanonicalId PowerShellGet:RequiredModule3/2.5#http://psget/psGallery/api/v2/

ModuleName NestedRequiredModule1
CanonicalId PowerShellGet:NestedRequiredModule1/#http://psget/psGallery/api/v2/

ModuleName NestedRequiredModule2
ModuleVersion 2.0
CanonicalId PowerShellGet:NestedRequiredModule2/2.0#http://psget/psGallery/api/v2/

ModuleName NestedRequiredModule3
RequiredVersion 2.5
CanonicalId PowerShellGet:NestedRequiredModule3/2.5#http://psget/psGallery/api/v2/
```

### <a name="install-the-testdepwithnestedrequiredmodules1-module-with-dependencies"></a>종속성이 있는 TestDepWithNestedRequiredModules1 모듈을 설치합니다.

```powershell
Install-Module -Name TestDepWithNestedRequiredModules1 -Repository LocalRepo -RequiredVersion "1.0"
Get-InstalledModule

Version    Name                    Repository   Description
-------    ----                    ----------   -----------
1.0        NestedRequiredModule1   LocalRepo    NestedRequiredModule1 module
2.5        NestedRequiredModule2   LocalRepo    NestedRequiredModule2 module
2.0        NestedRequiredModule3   LocalRepo    NestedRequiredModule3 module
1.0        RequiredModule1         LocalRepo    RequiredModule1 module
2.5        RequiredModule2                    LocalRepo    RequiredModule2 module
2.0        RequiredModule3                    LocalRepo    RequiredModule3 module
1.0        TestDepWithNestedRequiredModules1  LocalRepo    TestDepWithNestedRequiredModules1 module
```

### <a name="update-the-testdepwithnestedrequiredmodules1-module-with-dependencies"></a>종속성이 있는 TestDepWithNestedRequiredModules1 모듈을 업데이트합니다.

```powershell
Find-Module -Name TestDepWithNestedRequiredModules1 -Repository LocalRepo -AllVersions

Version    Name                                Repository  Description
-------    ----                                ----------  -----------
1.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module
2.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module

Update-Module -Name TestDepWithNestedRequiredModules1 -RequiredVersion 2.0
Get-InstalledModule

Version    Name                                Repository  Description
-------    ----                                ----------  -----------
1.0        NestedRequiredModule1               LocalRepo   NestedRequiredModule1 module
2.5        NestedRequiredModule2               LocalRepo   NestedRequiredModule2 module
2.0        NestedRequiredModule3               LocalRepo   NestedRequiredModule3 module
2.5        NestedRequiredModule3               LocalRepo   NestedRequiredModule3 module
1.0        RequiredModule1                     LocalRepo   RequiredModule1 module
2.5        RequiredModule2                     LocalRepo   RequiredModule2 module
2.0        RequiredModule3                     LocalRepo   RequiredModule3 module
2.5        RequiredModule3                     LocalRepo   RequiredModule3 module
1.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module
2.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module
```

### <a name="run-the-uninstall-module-cmdlet-to-uninstall-a-module-that-you-installed-by-using-powershellget"></a>Uninstall-Module cmdlet을 실행하여 PowerShellGet을 사용하여 설치한 모듈을 제거합니다.

다른 모든 모듈이 삭제하려는 모듈에 종속되어 있는 경우 PowerShellGet에서 오류가 throw됩니다.

```powershell
Get-InstalledModule -Name RequiredModule1 | Uninstall-Module

PackageManagement\Uninstall-Package : The module 'RequiredModule1' of version '2.5' in module base folder 'C:\Program Files\WindowsPowerShell\Modules\RequiredModule1\2.5' cannot be uninstalled, because one or more other modules 'ModuleWithDependencies2' are dependent on this module. Uninstall the modules that depend on this module before uninstalling module 'RequiredModule1'.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\PSGet.psm1:1303 char:25
+ ... $null = PackageManagement\\Uninstall-Package @PSBoundParameters
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo : InvalidOperation: (Microsoft.Power...ninstallPackage:UninstallPackage) [Uninstall-Package], Exception
+ FullyQualifiedErrorId : UnableToUninstallAsOtherModulesNeedThisModule,Uninstall-Package,Microsoft.PowerShell.PackageManagement.Cmdlets.UninstallPackage
```

## <a name="save-module-cmdlet"></a>Save-Module cmdlet

```powershell
Save-Module -Repository MSPSGallery -Name ModuleWithDependencies2 -Path C:\MySavedModuleLocation
dir C:\MySavedModuleLocation

Directory: C:\MySavedModuleLocation

Mode LastWriteTime Length Name
---- ------------- ------ ----
d----- 4/21/2015 5:40 PM ModuleWithDependencies2
d----- 4/21/2015 5:40 PM NestedRequiredModule1
d----- 4/21/2015 5:40 PM NestedRequiredModule2
d----- 4/21/2015 5:40 PM NestedRequiredModule3
d----- 4/21/2015 5:40 PM RequiredModule1
d----- 4/21/2015 5:40 PM RequiredModule2
d----- 4/21/2015 5:40 PM RequiredModule3
```

## <a name="update-modulemanifest-cmdlet"></a>Update-ModuleManifest cmdlet

이 새로운 cmdlet을 사용하여 입력 속성 값으로 매니페스트 파일을 업데이트할 수 있습니다. 이 cmdlet은 Test-modulemanifest에서 사용하는 모든 매개 변수를 사용합니다.

많은 모듈 작성자가 FunctionsToExport, CmdletsToExport 등의 내보낸 값에 “\*”를 지정하려고 함을 알 수 있습니다. PowerShell 갤러리에 모듈을 게시하는 동안 지정되지 않은 함수 및 명령은 갤러리에 제대로 채워지지 않습니다. 따라서 모듈 작성자가 적절한 값으로 매니페스트를 업데이트하는 것이 좋습니다.

속성을 내보낸 모듈이 있는 경우 Update-ModuleManifest에서 내보낸 함수, cmdlet, 변수 등의 정보로 지정된 매니페스트 파일을 채웁니다.

```powershell
Get-Content -Path "C:\Temp\PSGTEST-TestPackageMetadata\2.5\PSGTEST-TestPackageMetadata.psd1"
@{
# Script module or binary module file associated with this manifest.
# RootModule = ''
# Version number of this module.
ModuleVersion = '2.5'
# ID used to uniquely identify this module
GUID = '610e5c5b-dc42-4eaa-8511-ebfb44066d5e'

#(Other properties removed here for Simplicity…)

# Functions to export from this module
FunctionsToExport = '*'
# Cmdlets to export from this module
CmdletsToExport = '*'
# Variables to export from this module
VariablesToExport = '*'
# Aliases to export from this module
AliasesToExport = '*'
}
```

Update-ModuleManifest 후:

```powershell
Update-ModuleManifest -Path "C:\Temp\PSGTEST-TestPackageMetadata\2.5\PSGTEST-TestPackageMetadata.psd1"
Get-Content -Path "C:\Temp\PSGTEST-TestPackageMetadata\2.5\PSGTEST-TestPackageMetadata.psd1"
#
# Module manifest for module 'NewManifest'
#
# Generated by: author name
#
# Generated on: 11/13/2015
#
@{
# Script module or binary module file associated with this manifest.
# RootModule = ''
# Version number of this module.
ModuleVersion = '2.5'
# ID used to uniquely identify this module
GUID = '610e5c5b-dc42-4eaa-8511-ebfb44066d5e'
# Functions to export from this module
FunctionsToExport = 'Get-FooFn Get-FooWF'
# Cmdlets to export from this module
CmdletsToExport = 'Test-PSGetTestCmdlet'
}
```

각 모듈의 경우 연결된 메타데이터 필드도 있습니다. PowerShell 갤러리에 메타데이터를 올바르게 표시하기 위해 Update-ModuleManifest를 사용하여 PrivateData 아래의 해당 필드를 채우면 됩니다.

```powershell
Update-ModuleManifest -Path "C:\Temp\PSGTEST-TestPackageMetadata\2.5\PSGTEST-TestPackageMetadata.psd1" -Tags "Tag1" -LicenseUri "http://license.com" -ProjectUri "http://project.com" -IconUri "http://icon.com" -ReleaseNotes "Test module"
```

매니페스트 파일 템플릿의 PrivateData 해시 테이블에는 다음과 같은 속성이 있습니다.

```powershell
# Private data to pass to the module specified in RootModule/ModuleToProcess. This may also contain a PSData hashtable with additional module metadata used by PowerShell.
PrivateData = @{
    PSData = @{
        # Tags applied to this module. These help with module discovery in online galleries.
        # Tags = @()

        # A URL to the license for this module.
        # LicenseUri = ''

        # A URL to the main website for this project.
        # ProjectUri = ''

        # A URL to an icon representing this module.
        # IconUri = ''

        # ReleaseNotes of this module
        # ReleaseNotes = ''

        # External dependent modules of this module
        # ExternalModuleDependencies = ''
    } # End of PSData hashtable
} # End of PrivateData hashtable
```

> [!NOTE]
> DscResourcesToExport는 최신 PowerShell 버전 5.0에서만 지원됩니다. 이전 PowerShell 버전에서 실행하고 있는 경우 필드를 업데이트할 수 없습니다.
