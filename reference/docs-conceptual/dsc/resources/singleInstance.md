---
ms.date: 07/08/2020
keywords: dsc,powershell,configuration,setup
title: 단일 인스턴스 DSC 리소스 작성(모범 사례)
ms.openlocfilehash: cd6048c0f8aeef7fb5458a5f0bfefef25169297c
ms.sourcegitcommit: d26e2237397483c6333abcf4331bd82f2e72b4e3
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/10/2020
ms.locfileid: "86217613"
---
# <a name="writing-a-single-instance-dsc-resource-best-practice"></a>단일 인스턴스 DSC 리소스 작성(모범 사례)

> [!NOTE]
> 이 항목에서는 구성에서 단일 인스턴스만 허용하는 DSC 리소스를 정의하는 모범 사례에 대해 설명합니다. 현재, 이 작업을 수행하는 기본 제공 DSC 기능은 없습니다. 이는 나중에 변경될 수 있습니다.

구성에서 리소스를 여러 번 사용할 수 없도록 하려는 경우가 있습니다. 예를 들어 [xTimeZone](https://github.com/PowerShell/xTimeZone) 리소스의 이전 구현에서는 다음과 같이 각 리소스 블록에서 표준 시간대를 다른 설정으로 지정하여 구성에서 리소스를 여러 번 호출할 수 있었습니다.

```powershell
Configuration SetTimeZone
{
    Param
    (
        [String[]]$NodeName = $env:COMPUTERNAME

    )

    Import-DSCResource -ModuleName xTimeZone


    Node $NodeName
    {
         xTimeZone TimeZoneExample
         {

            TimeZone = 'Eastern Standard Time'
         }

         xTimeZone TimeZoneExample2
         {

            TimeZone = 'Pacific Standard Time'

         }

    }
}
```

이는 DSC 리소스 키가 작동하는 방식 때문입니다. 리소스에는 키 속성이 하나 이상 있어야 합니다. 리소스 인스턴스는 모든 키 속성 값의 조합이 고유한 경우에만 고유하다고 간주됩니다. 이전 구현에서는 [xTimeZone](https://github.com/PowerShell/xTimeZone) 리소스에 **TimeZone**이라는 하나의 속성만 있었으며, 이 속성이 키여야 했습니다. 이 때문에 위와 같은 구성이 경고 없이 컴파일되고 실행되었습니다. 각 **xTimeZone** 리소스 블록이 고유한 것으로 간주되었습니다. 이로 인해 구성이 노드에 반복해서 적용되고 표준 시간대를 앞뒤로 순환했습니다.

구성에서 대상 노드에 대한 표준 시간대를 한 번만 설정할 수 있도록 하기 위해 리소스를 업데이트하여 두 번째 속성인 **IsSingleInstance**를 추가했으며 키 속성이 되었습니다. **ValueMap**을 사용하여 **IsSingleInstance**를 단일 값 "Yes"로 제한했습니다. 리소스에 대한 이전 MOF 스키마는 다음과 같습니다.

```powershell
[ClassVersion("1.0.0.0"), FriendlyName("xTimeZone")]
class xTimeZone : OMI_BaseResource
{
    [Key, Description("Specifies the TimeZone.")] String TimeZone;
};
```

리소스에 대한 업데이트된 MOF 스키마는 다음과 같습니다.

```powershell
[ClassVersion("1.0.0.0"), FriendlyName("xTimeZone")]
class xTimeZone : OMI_BaseResource
{
    [Key, Description("Specifies the resource is a single instance, the value must be 'Yes'"), ValueMap{"Yes"}, Values{"Yes"}] String IsSingleInstance;
    [Required, Description("Specifies the TimeZone.")] String TimeZone;
};
```

리소스 스크립트도 새 매개 변수를 사용하도록 업데이트되었습니다. 리소스 스크립트를 변경한 방법은 다음과 같습니다.

```powershell
function Get-TargetResource
{
    [CmdletBinding()]
    [OutputType([Hashtable])]
    param
    (
        [parameter(Mandatory = $true)]
        [ValidateSet('Yes')]
        [String]
        $IsSingleInstance,

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $TimeZone
    )

    #Get the current TimeZone
    $CurrentTimeZone = Get-TimeZone

    $returnValue = @{
        TimeZone = $CurrentTimeZone
        IsSingleInstance = 'Yes'
    }

    #Output the target resource
    $returnValue
}

function Set-TargetResource
{
    [CmdletBinding()]
    param
    (
        [parameter(Mandatory = $true)]
        [ValidateSet('Yes')]
        [String]
        $IsSingleInstance,

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $TimeZone
    )

    #Output the result of Get-TargetResource function.
    $CurrentTimeZone = Get-TimeZone

    Write-Verbose -Message "Replace the System Time Zone to $TimeZone"

    try
    {
        if($CurrentTimeZone -ne $TimeZone)
        {
            Write-Verbose -Verbose "Setting the TimeZone"
            Set-TimeZone -TimeZone $TimeZone
        }
        else
        {
            Write-Verbose -Verbose "TimeZone already set to $TimeZone"
        }
    }
    catch
    {
        $ErrorMsg = $_.Exception.Message
        Write-Verbose -Verbose $ErrorMsg
    }
}


function Test-TargetResource
{
    [CmdletBinding()]
    [OutputType([Boolean])]
    param
    (
        [parameter(Mandatory = $true)]
        [ValidateSet('Yes')]
        [String]
        $IsSingleInstance,

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $TimeZone
    )

    #Output from Get-TargetResource
    $CurrentTimeZone = Get-TimeZone

    if($TimeZone -eq $CurrentTimeZone)
    {
        return $true
    }
    else
    {
        return $false
    }
}

Function Get-TimeZone {
    [CmdletBinding()]
    param()

    & tzutil.exe /g
}

Function Set-TimeZone {
    [CmdletBinding()]
    param(
        [Parameter(Mandatory=$true)]
        [System.String]
        $TimeZone
    )

    try
    {
        & tzutil.exe /s $TimeZone
    }
    catch
    {
        $ErrorMsg = $_.Exception.Message
        Write-Verbose $ErrorMsg
    }
}

Export-ModuleMember -Function *-TargetResource
```

**TimeZone** 속성은 더 이상 키가 아닙니다. 이제, 구성에서 각기 다른 **TimeZone** 값으로 두 개의 **xTimeZone** 블록을 사용하여 표준 시간대를 두 번 설정하려고 하면 구성을 컴파일할 때 오류가 발생합니다.

```Output
Test-ConflictingResources : A conflict was detected between resources '[xTimeZone]TimeZoneExample (::15::10::xTimeZone)' and
'[xTimeZone]TimeZoneExample2 (::22::10::xTimeZone)' in node 'CONTOSO-CLIENT'. Resources have identical key properties but there are differences in the
following non-key properties: 'TimeZone'. Values 'Eastern Standard Time' don't match values 'Pacific Standard Time'. Please update these property
values so that they are identical in both cases.
At line:271 char:9
+         Test-ConflictingResources $keywordName $canonicalizedValue $k ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Write-Error], InvalidOperationException
    + FullyQualifiedErrorId : ConflictingDuplicateResource,Test-ConflictingResources
Errors occurred while processing configuration 'SetTimeZone'.
At C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\PSDesiredStateConfiguration.psm1:3705 char:5
+     throw $ErrorRecord
+     ~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (SetTimeZone:String) [], InvalidOperationException
    + FullyQualifiedErrorId : FailToProcessConfiguration
```
