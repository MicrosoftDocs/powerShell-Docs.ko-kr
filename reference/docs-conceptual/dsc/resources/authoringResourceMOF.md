---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: MOF를 사용하여 사용자 지정 DSC 리소스 작성
ms.openlocfilehash: 24e9d15bcbe1eddd297daeb04e0713c443e52c38
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2020
ms.locfileid: "71952900"
---
# <a name="writing-a-custom-dsc-resource-with-mof"></a>MOF를 사용하여 사용자 지정 DSC 리소스 작성

> 적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0

이 항목에서는 MOF 파일에 Windows PowerShell DSC(필요한 상태 구성) 사용자 지정 리소스에 대한 스키마를 정의하고 Windows PowerShell 스크립트 파일에 리소스를 구현합니다. 이 사용자 지정 리소스는 웹 사이트를 만들고 유지 관리하기 위한 것입니다.

## <a name="creating-the-mof-schema"></a>MOF 스키마 만들기

스키마는 DSC 구성 스크립트를 통해 구성할 수 있는 리소스의 속성을 정의합니다.

### <a name="folder-structure-for-a-mof-resource"></a>MOF 리소스에 대한 폴더 구조

MOF 스키마를 사용하여 DSC 사용자 지정 리소스를 구현하려면 다음 폴더 구조를 만듭니다. MOF 스키마는 Demo_IISWebsite.schema.mof 파일에 정의되며, 리소스 스크립트는 Demo_IISWebsite.psm1에 정의됩니다. 필요에 따라 모듈 매니페스트(psd1) 파일을 만들 수 있습니다.

```
$env:ProgramFiles\WindowsPowerShell\Modules (folder)
    |- MyDscResources (folder)
        |- DSCResources (folder)
            |- Demo_IISWebsite (folder)
                |- Demo_IISWebsite.psd1 (file, optional)
                |- Demo_IISWebsite.psm1 (file, required)
                |- Demo_IISWebsite.schema.mof (file, required)
```

최상위 폴더 아래에 DSCResources라는 폴더를 만들어야 하며, 각 리소스에 대한 폴더의 이름은 리소스의 이름과 동일해야 합니다.

### <a name="the-contents-of-the-mof-file"></a>MOF 파일의 내용

다음은 사용자 지정 웹 사이트 리소스에 사용할 수 있는 MOF 파일의 예입니다. 이 예제를 수행하려면 이 스키마를 파일에 저장하고 *Demo_IISWebsite.schema.mof* 파일을 호출합니다.

```
[ClassVersion("1.0.0"), FriendlyName("Website")]
class Demo_IISWebsite : OMI_BaseResource
{
  [Key] string Name;
  [Required] string PhysicalPath;
  [write,ValueMap{"Present", "Absent"},Values{"Present", "Absent"}] string Ensure;
  [write,ValueMap{"Started","Stopped"},Values{"Started", "Stopped"}] string State;
  [write] string Protocol[];
  [write] string BindingInfo[];
  [write] string ApplicationPool;
  [read] string ID;
};
```

앞의 코드에 대해 다음 사항에 주목합니다.

* `FriendlyName`은 DSC 구성 스크립트에서 이 사용자 지정 리소스를 참조하는 데 사용할 수 있는 이름을 정의합니다. 이 예제에서 `Website`는 기본 제공 보관 리소스에 대한 이름인 `Archive`와 동등합니다.
* 사용자 지정 리소스에 대해 정의하는 클래스는 `OMI_BaseResource`에서 파생해야 합니다.
* 속성의 형식 한정자 `[Key]`는 이 속성이 리소스 인스턴스를 고유하게 식별할 것임을 나타냅니다. 하나 이상의 `[Key]` 속성이 필요합니다.
* `[Required]` 한정자는 이 속성이 필수임을 나타냅니다(이 리소스를 사용하는 모든 구성 스크립트에서 값을 지정해야 함).
* `[write]` 한정자는 구성 스크립트에서 사용자 지정 리소스를 사용할 때 이 속성이 선택 사항임을 나타냅니다. `[read]` 한정자는 속성이 구성으로 설정되지 않으며, 보고만을 위한 것임을 나타냅니다.
* `Values`는 속성에 지정된 할당할 수 있는 값을 `ValueMap`에 정의된 값 목록으로 제한합니다. 자세한 내용은 [ValueMap and Value Qualifiers(ValueMap 및 값 한정자)](/windows/desktop/WmiSdk/value-map)를 참조합니다.
* 기본 제공 DSC 리소스와 일관된 스타일을 유지하는 방법으로서, 리소스에 `Present` 및 `Absent` 값을 갖는 `Ensure`라는 속성을 포함하는 것이 좋습니다.
* 사용자 지정 리소스에 대한 스키마 파일의 이름을 `classname.schema.mof`와 같이 지정합니다. 여기서 `classname`는 스키마 정의에서 `class` 키워드의 뒤에 오는 식별자입니다.

### <a name="writing-the-resource-script"></a>리소스 스크립트 작성

리소스 스크립트는 리소스의 논리를 구현합니다. 이 모듈에서는 **Get-TargetResource**, **Set-TargetResource** 및 **Test-TargetResource**라는 세 가지 함수를 포함해야 합니다. 세 함수는 모두 리소스용으로 만든 MOF 스키마에 정의된 속성 집합과 동일한 매개 변수 집합을 사용해야 합니다. 이 문서에서는 이 속성 세트를 "리소스 속성"이라고 합니다. 이 세 개의 함수를 <ResourceName>.psm1이라는 파일에 저장합니다. 다음 예제에서는 이 함수들이 Demo_IISWebsite.psm1이라는 파일에 저장됩니다.

> [!NOTE]
> 리소스에서 동일한 구성 스크립트를 두 번 이상 실행해도 오류가 표시되지 않고 리소스는 스크립트를 한 번 실행하는 것과 동일한 상태로 유지되어야 합니다. 이 작업을 해내려면 **Get-TargetResource** 및 **Test-TargetResource** 함수가 리소스를 변경하지 않고 그대로 두고, **Set-TargetResource** 함수를 동일한 매개 변수 값으로 순서대로 두 번 이상 호출하는 것은 한 번 호출하는 것과 항상 동일한지 확인합니다.

**Get-TargetResource** 함수 구현에서는 매개 변수로 제공되는 주요 리소스 속성 값을 사용하여 지정된 리소스 인스턴스 상태를 확인합니다. 이 함수는 모든 리소스 속성을 키로 나열하고, 이러한 속성의 실제 값을 그에 대한 해당 값으로 나열하는 해시 테이블을 반환해야 합니다. 다음 코드에 예가 나와 있습니다.

```powershell
# DSC uses the Get-TargetResource function to fetch the status of the resource instance specified in the parameters for the target machine
function Get-TargetResource
{
    param
    (
        [ValidateSet("Present", "Absent")]
        [string]$Ensure = "Present",

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$Name,

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$PhysicalPath,

        [ValidateSet("Started", "Stopped")]
        [string]$State = "Started",

        [string]$ApplicationPool,

        [string[]]$BindingInfo,

        [string[]]$Protocol
    )

        $getTargetResourceResult = $null;

        <# Insert logic that uses the mandatory parameter values to get the website and assign it to a variable called $Website #>
        <# Set $ensureResult to "Present" if the requested website exists and to "Absent" otherwise #>

        # Add all Website properties to the hash table
        # This simple example assumes that $Website is not null
        $getTargetResourceResult = @{
                                      Name = $Website.Name;
                                        Ensure = $ensureResult;
                                        PhysicalPath = $Website.physicalPath;
                                        State = $Website.state;
                                        ID = $Website.id;
                                        ApplicationPool = $Website.applicationPool;
                                        Protocol = $Website.bindings.Collection.protocol;
                                        Binding = $Website.bindings.Collection.bindingInformation;
                                    }

        $getTargetResourceResult;
}
```

구성 스크립트에 있는 리소스 속성에 대해 지정된 값에 따라 **Set-TargetResource**는 다음 중 하나를 수행해야 합니다.

* 새 웹 사이트 만들기
* 기존 웹 사이트 업데이트
* 기존 웹 사이트 삭제

다음은 이에 대한 예입니다.

```powershell
# The Set-TargetResource function is used to create, delete or configure a website on the target machine.
function Set-TargetResource
{
    [CmdletBinding(SupportsShouldProcess=$true)]
    param
    (
        [ValidateSet("Present", "Absent")]
        [string]$Ensure = "Present",

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$Name,

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$PhysicalPath,

        [ValidateSet("Started", "Stopped")]
        [string]$State = "Started",

        [string]$ApplicationPool,

        [string[]]$BindingInfo,

        [string[]]$Protocol
    )

    <# If Ensure is set to "Present" and the website specified in the mandatory input parameters does not exist, then create it using the specified parameter values #>
    <# Else, if Ensure is set to "Present" and the website does exist, then update its properties to match the values provided in the non-mandatory parameter values #>
    <# Else, if Ensure is set to "Absent" and the website does not exist, then do nothing #>
    <# Else, if Ensure is set to "Absent" and the website does exist, then delete the website #>
}
```

마지막으로, **Test-TargetResource** 함수는 **Get-TargetResource** 및 **Set-TargetResource**와 동일한 매개 변수 집합을 사용해야 합니다. **Test-TargetResource**의 구현에서, 키 매개 변수에 지정된 리소스 인스턴스의 상태를 확인하세요. 리소스 인스턴스의 실제 상태가 매개 변수 집합에 지정된 값과 일치하지 않는 경우 **$false**를 반환하세요. 그렇지 않으면 **$true**를 반환하세요.

다음 코드는 **Test-TargetResource** 함수를 구현합니다.

```powershell
function Test-TargetResource
{
[CmdletBinding()]
[OutputType([System.Boolean])]
param
(
[ValidateSet("Present","Absent")]
[System.String]
$Ensure,

[parameter(Mandatory = $true)]
[System.String]
$Name,

[parameter(Mandatory = $true)]
[System.String]
$PhysicalPath,

[ValidateSet("Started","Stopped")]
[System.String]
$State,

[System.String[]]
$Protocol,

[System.String[]]
$BindingData,

[System.String]
$ApplicationPool
)

#Write-Verbose "Use this cmdlet to deliver information about command processing."

#Write-Debug "Use this cmdlet to write debug information while troubleshooting."


#Include logic to
$result = [System.Boolean]
#Add logic to test whether the website is present and its status mathes the supplied parameter values. If it does, return true. If it does not, return false.
$result
}
```

**참고**: 보다 쉽게 디버그하려면 이전 세 개의 함수를 구현할 때 **Write-Verbose** cmdlet을 사용하세요.
>이 cmdlet은 자세한 정보 메시지 스트림에 텍스트를 씁니다.
>자세한 정보 메시지 스트림은 기본적으로 표시되지 않지만 **$VerbosePreference** 변수 값을 변경하거나 DSC cmdlets = new에 **Verbose** 매개 변수를 사용하여 표시할 수 있습니다.

### <a name="creating-the-module-manifest"></a>모듈 매니페스트 만들기

마지막으로, **New-ModuleManifest** cmdlet을 사용하여 사용자 지정 리소스 모듈에 대한 <ResourceName>.psd1 파일을 정의하세요. 이 cmdlet을 호출할 때에는 이전 섹션에서 설명한 스크립트 모듈(.psm1) 파일을 참조합니다. 내보낼 함수 목록에 **Get-TargetResource**, **Set-TargetResource** 및 **Test-TargetResource**를 포함하세요. 다음은 매니페스트 파일의 예입니다.

```powershell
# Module manifest for module 'Demo.IIS.Website'
#
# Generated on: 1/10/2013
#

@{

# Script module or binary module file associated with this manifest.
# RootModule = ''

# Version number of this module.
ModuleVersion = '1.0'

# ID used to uniquely identify this module
GUID = '6AB5ED33-E923-41d8-A3A4-5ADDA2B301DE'

# Author of this module
Author = 'Contoso'

# Company or vendor of this module
CompanyName = 'Contoso'

# Copyright statement for this module
Copyright = 'Contoso. All rights reserved.'

# Description of the functionality provided by this module
Description = 'This Module is used to support the creation and configuration of IIS Websites through Get, Set and Test API on the DSC managed nodes.'

# Minimum version of the Windows PowerShell engine required by this module
PowerShellVersion = '4.0'

# Minimum version of the common language runtime (CLR) required by this module
CLRVersion = '4.0'

# Modules that must be imported into the global environment prior to importing this module
RequiredModules = @("WebAdministration")

# Modules to import as nested modules of the module specified in RootModule/ModuleToProcess
NestedModules = @("Demo_IISWebsite.psm1")

# Functions to export from this module
FunctionsToExport = @("Get-TargetResource", "Set-TargetResource", "Test-TargetResource")

# Cmdlets to export from this module
#CmdletsToExport = '*'

# HelpInfo URI of this module
# HelpInfoURI = ''
}
```

## <a name="supporting-psdscrunascredential"></a>PsDscRunAsCredential 지원

>**참고:** **PsDscRunAsCredential**은 PowerShell 5.0이상에서 지원됩니다.

**PsDscRunAsCredential** 속성을 [DSC 구성](../configurations/configurations.md) 리소스 블록에서 사용하면 지정된 자격 증명 집합으로 리소스를 실행해야 함을 지정할 수 있습니다.
자세한 내용은 [사용자 자격 증명을 사용하여 DSC 실행](../configurations/runAsUser.md)을 참조하세요.

사용자 지정 리소스 내에서 사용자 컨텍스트에 액세스하려는 경우 `$PsDscContext` 자동 변수를 사용할 수 있습니다.

예를 들어 다음 코드는 리소스가 자세한 정보 출력 스트림으로 실행되는 사용자 컨텍스트를 작성합니다.

```powershell
if (PsDscContext.RunAsUser) {
    Write-Verbose "User: $PsDscContext.RunAsUser";
}
```

## <a name="rebooting-the-node"></a>노드 다시 부팅

`Set-TargetResource` 함수에서 수행된 작업에 다시 부팅이 필요한 경우 글로벌 플래그를 사용하여 LCM이 노드를 다시 부팅하도록 지시할 수 있습니다. 이 다시 부팅은 `Set-TargetResource` 함수가 완료된 후에 바로 발생합니다.

`Set-TargetResource` 함수 내에 다음 코드 줄을 추가합니다.

```powershell
# Include this line if the resource requires a system reboot.
$global:DSCMachineStatus = 1
```

LCM이 노드를 다시 부팅하기 위해 **RebootNodeIfNeeded** 플래그는 `$true`로 설정되어야 합니다. **ActionAfterReboot** 설정도 기본값인 **ContinueConfiguration**으로 설정되어야 합니다. LCM 구성에 대한 자세한 내용은 [로컬 구성 관리자 구성](../managing-nodes/metaConfig.md) 또는 [로컬 구성 관리자 구성(v4)](../managing-nodes/metaConfig4.md)을 참조하세요.
