---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: PowerShell 클래스를 사용하여 사용자 지정 DSC 리소스 작성
ms.openlocfilehash: 34356f65bcb83153e7395a16d2a4a5cf2e507332
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55682618"
---
# <a name="writing-a-custom-dsc-resource-with-powershell-classes"></a><span data-ttu-id="30d1b-103">PowerShell 클래스를 사용하여 사용자 지정 DSC 리소스 작성</span><span class="sxs-lookup"><span data-stu-id="30d1b-103">Writing a custom DSC resource with PowerShell classes</span></span>

> <span data-ttu-id="30d1b-104">적용 대상: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="30d1b-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="30d1b-105">Windows PowerShell 5.0의 PowerShell 클래스 도입으로 이제 클래스를 만들어 DSC 리소스를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30d1b-105">With the introduction of PowerShell classes in Windows PowerShell 5.0, you can now define a DSC resource by creating a class.</span></span> <span data-ttu-id="30d1b-106">클래스는 리소스의 스키마와 구현을 모두 정의하며, 따라서 별도의 MOF 파일을 만들 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="30d1b-106">The class defines both the schema and the implementation of the resource, so there is no need to create a separate MOF file.</span></span> <span data-ttu-id="30d1b-107">**DSCResources** 폴더가 필요하지 않으므로 클래스 기반 리소스의 폴더 구조도 더 간단합니다.</span><span class="sxs-lookup"><span data-stu-id="30d1b-107">The folder structure for a class-based resource is also simpler, because a **DSCResources** folder is not necessary.</span></span>

<span data-ttu-id="30d1b-108">클래스 기반 DSC 리소스에서 스키마는 속성 유형을 지정하는 특성으로 수정할 수 있는 클래스의 속성으로 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="30d1b-108">In a class-based DSC resource, the schema is defined as properties of the class which can be modified with attributes to specify the property type..</span></span> <span data-ttu-id="30d1b-109">리소스는 스크립트 리소스에 있는 **Get()**, **Set()** 및 **Test()** 메서드(**Get-TargetResource**, **Set-TargetResource** 및 **Test-TargetResource**) 함수에 의해 구현됩니다.</span><span class="sxs-lookup"><span data-stu-id="30d1b-109">The resource is implemented by **Get()**, **Set()**, and **Test()** methods (equivalent to the **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource** functions in a script resource.</span></span>

<span data-ttu-id="30d1b-110">이 항목에서는 지정된 경로에 있는 파일을 관리하는 **FileResource**라는 간단한 리소스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="30d1b-110">In this topic, we will create a simple resource named **FileResource** that manages a file in a specified path.</span></span>

<span data-ttu-id="30d1b-111">DSC 리소스에 대한 자세한 내용은 [Build Custom Windows PowerShell Desired State Configuration Resources(사용자 지정 Windows PowerShell 필요한 상태 구성 리소스 빌드)](authoringResource.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="30d1b-111">For more information about DSC resources, see [Build Custom Windows PowerShell Desired State Configuration Resources](authoringResource.md)</span></span>

><span data-ttu-id="30d1b-112">**참고:** 제네릭 컬렉션 클래스 기반 리소스에서 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="30d1b-112">**Note:** Generic collections are not supported in class-based resources.</span></span>

## <a name="folder-structure-for-a-class-resource"></a><span data-ttu-id="30d1b-113">클래스 리소스에 대한 폴더 구조</span><span class="sxs-lookup"><span data-stu-id="30d1b-113">Folder structure for a class resource</span></span>

<span data-ttu-id="30d1b-114">PowerShell 클래스를 사용하여 DSC 사용자 지정 리소스를 구현하려면 다음 폴더 구조를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="30d1b-114">To implement a DSC custom resource with a PowerShell class, create the following folder structure.</span></span> <span data-ttu-id="30d1b-115">클래스는 **MyDscResource.psm1**에 정의되어 있으며, 모듈 매니페스트는 **MyDscResource.psd1**에 정의되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30d1b-115">The class is defined in **MyDscResource.psm1** and the module manifest is defined in **MyDscResource.psd1**.</span></span>

```
$env:ProgramFiles\WindowsPowerShell\Modules (folder)
    |- MyDscResource (folder)
        MyDscResource.psm1
        MyDscResource.psd1
```

## <a name="create-the-class"></a><span data-ttu-id="30d1b-116">클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="30d1b-116">Create the class</span></span>

<span data-ttu-id="30d1b-117">클래스 키워드를 사용하여 PowerShell 클래스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="30d1b-117">You use the class keyword to create a PowerShell class.</span></span> <span data-ttu-id="30d1b-118">클래스가 DSC 리소스임을 지정하려면 **DscResource()** 특성을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="30d1b-118">To specify that a class is a DSC resource, use the **DscResource()** attribute.</span></span> <span data-ttu-id="30d1b-119">클래스의 이름은 DSC 리소스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="30d1b-119">The name of the class is the name of the DSC resource.</span></span>

```powershell
[DscResource()]
class FileResource {
}
```

### <a name="declare-properties"></a><span data-ttu-id="30d1b-120">속성 선언</span><span class="sxs-lookup"><span data-stu-id="30d1b-120">Declare properties</span></span>

<span data-ttu-id="30d1b-121">DSC 리소스 스키마는 클래스의 속성으로 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="30d1b-121">The DSC resource schema is defined as properties of the class.</span></span> <span data-ttu-id="30d1b-122">세 가지 속성을 다음과 같이 선언합니다.</span><span class="sxs-lookup"><span data-stu-id="30d1b-122">We declare three properties as follows.</span></span>

```powershell
[DscProperty(Key)]
[string]$Path

[DscProperty(Mandatory)]
[Ensure] $Ensure

[DscProperty(Mandatory)]
[string] $SourcePath

[DscProperty(NotConfigurable)]
[Nullable[datetime]] $CreationTime
```

<span data-ttu-id="30d1b-123">속성은 특성으로 수정되고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30d1b-123">Notice that the properties are modified by attributes.</span></span> <span data-ttu-id="30d1b-124">특성의 의미는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="30d1b-124">The meaning of the attributes is as follows:</span></span>

- <span data-ttu-id="30d1b-125">**DscProperty(Key)**: 필수 속성이입니다.</span><span class="sxs-lookup"><span data-stu-id="30d1b-125">**DscProperty(Key)**: The property is required.</span></span> <span data-ttu-id="30d1b-126">속성이 키입니다.</span><span class="sxs-lookup"><span data-stu-id="30d1b-126">The property is a key.</span></span> <span data-ttu-id="30d1b-127">키로 표시된 모든 속성의 값은 구성 내 리소스 인스턴스를 고유하게 식별하도록 결합해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="30d1b-127">The values of all properties marked as keys must combine to uniquely identify a resource instance within a configuration.</span></span>
- <span data-ttu-id="30d1b-128">**DscProperty(Mandatory)**: 필수 속성이입니다.</span><span class="sxs-lookup"><span data-stu-id="30d1b-128">**DscProperty(Mandatory)**: The property is required.</span></span>
- <span data-ttu-id="30d1b-129">**DscProperty(NotConfigurable)**: 읽기 전용 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="30d1b-129">**DscProperty(NotConfigurable)**: The property is read-only.</span></span> <span data-ttu-id="30d1b-130">이 특성으로 표시된 속성은 구성으로 설정할 수 없지만 존재할 경우 **Get()** 메서드로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="30d1b-130">Properties marked with this attribute cannot be set by a configuration, but are populated by the **Get()** method when present.</span></span>
- <span data-ttu-id="30d1b-131">**DscProperty()**: 속성은 구성할 수 있지만 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="30d1b-131">**DscProperty()**: The property is configurable, but it is not required.</span></span>

<span data-ttu-id="30d1b-132">**$Path** 및 **$SourcePath** 속성은 모두 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="30d1b-132">The **$Path** and **$SourcePath** properties are both strings.</span></span> <span data-ttu-id="30d1b-133">**$CreationTime**은 [DateTime](/dotnet/api/system.datetime) 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="30d1b-133">The **$CreationTime** is a [DateTime](/dotnet/api/system.datetime) property.</span></span> <span data-ttu-id="30d1b-134">**$Ensure** 속성은 다음과 같이 정의하는 열거형 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="30d1b-134">The **$Ensure** property is an enumeration type, defined as follows.</span></span>

```powershell
enum Ensure
{
    Absent
    Present
}
```

### <a name="implementing-the-methods"></a><span data-ttu-id="30d1b-135">메서드 구현</span><span class="sxs-lookup"><span data-stu-id="30d1b-135">Implementing the methods</span></span>

<span data-ttu-id="30d1b-136">The **Get()**, **Set()** 및 **Test()** 메서드는 스크립트 리소스의 **Get-TargetResource**, **Set-TargetResource** 및 **Test-TargetResource** 함수와 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="30d1b-136">The **Get()**, **Set()**, and **Test()** methods are analogous to the **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource** functions in a script resource.</span></span>

<span data-ttu-id="30d1b-137">이 코드에는 **$SourcePath**의 파일을 **$Path**에 복사하는 도우미 함수인 CopyFile() 함수도 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30d1b-137">This code also includes the CopyFile() function, a helper function that copies the file from **$SourcePath** to **$Path**.</span></span>

```powershell
    <#
        This method is equivalent of the Set-TargetResource script function.
        It sets the resource to the desired state.
    #>
    [void] Set()
    {
        $fileExists = $this.TestFilePath($this.Path)

        if ($this.ensure -eq [Ensure]::Present)
        {
            if(-not $fileExists)
            {
                $this.CopyFile()
            }
        }
        else
        {
            if ($fileExists)
            {
                Write-Verbose -Message "Deleting the file $($this.Path)"
                Remove-Item -LiteralPath $this.Path -Force
            }
        }
    }

    <#
        This method is equivalent of the Test-TargetResource script function.
        It should return True or False, showing whether the resource
        is in a desired state.
    #>
    [bool] Test()
    {
        $present = $this.TestFilePath($this.Path)

        if ($this.Ensure -eq [Ensure]::Present)
        {
            return $present
        }
        else
        {
            return -not $present
        }
    }

    <#
        This method is equivalent of the Get-TargetResource script function.
        The implementation should use the keys to find appropriate resources.
        This method returns an instance of this class with the updated key
         properties.
    #>
    [FileResource] Get()
    {
        $present = $this.TestFilePath($this.Path)

        if ($present)
        {
            $file = Get-ChildItem -LiteralPath $this.Path
            $this.CreationTime = $file.CreationTime
            $this.Ensure = [Ensure]::Present
        }
        else
        {
            $this.CreationTime = $null
            $this.Ensure = [Ensure]::Absent
        }

        return $this
    }

    <#
        Helper method to check if the file exists and it is file
    #>
    [bool] TestFilePath([string] $location)
    {
        $present = $true

        $item = Get-ChildItem -LiteralPath $location -ErrorAction Ignore

        if ($item -eq $null)
        {
            $present = $false
        }
        elseif ($item.PSProvider.Name -ne "FileSystem")
        {
            throw "Path $($location) is not a file path."
        }
        elseif ($item.PSIsContainer)
        {
            throw "Path $($location) is a directory path."
        }

        return $present
    }

    <#
        Helper method to copy file from source to path
    #>
    [void] CopyFile()
    {
        if (-not $this.TestFilePath($this.SourcePath))
        {
            throw "SourcePath $($this.SourcePath) is not found."
        }

        [System.IO.FileInfo] $destFileInfo = New-Object -TypeName System.IO.FileInfo($this.Path)

        if (-not $destFileInfo.Directory.Exists)
        {
            Write-Verbose -Message "Creating directory $($destFileInfo.Directory.FullName)"

            <#
                Use CreateDirectory instead of New-Item to avoid code
                to handle the non-terminating error
            #>
            [System.IO.Directory]::CreateDirectory($destFileInfo.Directory.FullName)
        }

        if (Test-Path -LiteralPath $this.Path -PathType Container)
        {
            throw "Path $($this.Path) is a directory path"
        }

        Write-Verbose -Message "Copying $($this.SourcePath) to $($this.Path)"

        # DSC engine catches and reports any error that occurs
        Copy-Item -LiteralPath $this.SourcePath -Destination $this.Path -Force
    }
```

### <a name="the-complete-file"></a><span data-ttu-id="30d1b-138">전체 파일</span><span class="sxs-lookup"><span data-stu-id="30d1b-138">The complete file</span></span>

<span data-ttu-id="30d1b-139">전체 클래스 파일은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="30d1b-139">The complete class file follows.</span></span>

```powershell
enum Ensure
{
    Absent
    Present
}

<#
   This resource manages the file in a specific path.
   [DscResource()] indicates the class is a DSC resource
#>

[DscResource()]
class FileResource
{
    <#
       This property is the fully qualified path to the file that is
       expected to be present or absent.

       The [DscProperty(Key)] attribute indicates the property is a
       key and its value uniquely identifies a resource instance.
       Defining this attribute also means the property is required
       and DSC will ensure a value is set before calling the resource.

       A DSC resource must define at least one key property.
    #>
    [DscProperty(Key)]
    [string]$Path

    <#
        This property indicates if the settings should be present or absent
        on the system. For present, the resource ensures the file pointed
        to by $Path exists. For absent, it ensures the file point to by
        $Path does not exist.

        The [DscProperty(Mandatory)] attribute indicates the property is
        required and DSC will guarantee it is set.

        If Mandatory is not specified or if it is defined as
        Mandatory=$false, the value is not guaranteed to be set when DSC
        calls the resource.  This is appropriate for optional properties.
    #>
    [DscProperty(Mandatory)]
    [Ensure] $Ensure

    <#
       This property defines the fully qualified path to a file that will
       be placed on the system if $Ensure = Present and $Path does not
        exist.

       NOTE: This property is required because [DscProperty(Mandatory)] is
        set.
    #>
    [DscProperty(Mandatory)]
    [string] $SourcePath

    <#
       This property reports the file's create timestamp.

       [DscProperty(NotConfigurable)] attribute indicates the property is
       not configurable in DSC configuration.  Properties marked this way
       are populated by the Get() method to report additional details
       about the resource when it is present.

    #>
    [DscProperty(NotConfigurable)]
    [Nullable[datetime]] $CreationTime

    <#
        This method is equivalent of the Set-TargetResource script function.
        It sets the resource to the desired state.
    #>
    [void] Set()
    {
        $fileExists = $this.TestFilePath($this.Path)
        if ($this.ensure -eq [Ensure]::Present)
        {
            if (-not $fileExists)
            {
                $this.CopyFile()
            }
        }
        else
        {
            if ($fileExists)
            {
                Write-Verbose -Message "Deleting the file $($this.Path)"
                Remove-Item -LiteralPath $this.Path -Force
            }
        }
    }

    <#
        This method is equivalent of the Test-TargetResource script function.
        It should return True or False, showing whether the resource
        is in a desired state.
    #>
    [bool] Test()
    {
        $present = $this.TestFilePath($this.Path)

        if ($this.Ensure -eq [Ensure]::Present)
        {
            return $present
        }
        else
        {
            return -not $present
        }
    }

    <#
        This method is equivalent of the Get-TargetResource script function.
        The implementation should use the keys to find appropriate resources.
        This method returns an instance of this class with the updated key
         properties.
    #>
    [FileResource] Get()
    {
        $present = $this.TestFilePath($this.Path)

        if ($present)
        {
            $file = Get-ChildItem -LiteralPath $this.Path
            $this.CreationTime = $file.CreationTime
            $this.Ensure = [Ensure]::Present
        }
        else
        {
            $this.CreationTime = $null
            $this.Ensure = [Ensure]::Absent
        }

        return $this
    }

    <#
        Helper method to check if the file exists and it is file
    #>
    [bool] TestFilePath([string] $location)
    {
        $present = $true

        $item = Get-ChildItem -LiteralPath $location -ea Ignore
        if ($item -eq $null)
        {
            $present = $false
        }
        elseif ($item.PSProvider.Name -ne "FileSystem")
        {
            throw "Path $($location) is not a file path."
        }
        elseif ($item.PSIsContainer)
        {
            throw "Path $($location) is a directory path."
        }

        return $present
    }

    <#
        Helper method to copy file from source to path
    #>
    [void] CopyFile()
    {
        if (-not $this.TestFilePath($this.SourcePath))
        {
            throw "SourcePath $($this.SourcePath) is not found."
        }

        [System.IO.FileInfo] $destFileInfo = new-object System.IO.FileInfo($this.Path)
        if (-not $destFileInfo.Directory.Exists)
        {
            Write-Verbose -Message "Creating directory $($destFileInfo.Directory.FullName)"

            <#
                Use CreateDirectory instead of New-Item to avoid code
                 to handle the non-terminating error
            #>
            [System.IO.Directory]::CreateDirectory($destFileInfo.Directory.FullName)
        }

        if (Test-Path -LiteralPath $this.Path -PathType Container)
        {
            throw "Path $($this.Path) is a directory path"
        }

        Write-Verbose -Message "Copying $($this.SourcePath) to $($this.Path)"

        # DSC engine catches and reports any error that occurs
        Copy-Item -LiteralPath $this.SourcePath -Destination $this.Path -Force
    }
} # This module defines a class for a DSC "FileResource" provider.
```

## <a name="create-a-manifest"></a><span data-ttu-id="30d1b-140">매니페스트 만들기</span><span class="sxs-lookup"><span data-stu-id="30d1b-140">Create a manifest</span></span>

<span data-ttu-id="30d1b-141">DSC 엔진에 사용할 수 있는 클래스 기반 리소스를 만들려면 매니페스트 파일에 리소스를 내보내도록 모듈에게 지시하는 **DscResourcesToExport** 문을 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="30d1b-141">To make a class-based resource available to the DSC engine, you must include a **DscResourcesToExport** statement in the manifest file that instructs the module to export the resource.</span></span> <span data-ttu-id="30d1b-142">이 매니페스트는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="30d1b-142">Our manifest looks like this:</span></span>

```powershell
@{

# Script module or binary module file associated with this manifest.
RootModule = 'MyDscResource.psm1'

DscResourcesToExport = 'FileResource'

# Version number of this module.
ModuleVersion = '1.0'

# ID used to uniquely identify this module
GUID = '81624038-5e71-40f8-8905-b1a87afe22d7'

# Author of this module
Author = 'Microsoft Corporation'

# Company or vendor of this module
CompanyName = 'Microsoft Corporation'

# Copyright statement for this module
Copyright = '(c) 2014 Microsoft. All rights reserved.'

# Description of the functionality provided by this module
# Description = ''

# Minimum version of the Windows PowerShell engine required by this module
PowerShellVersion = '5.0'

# Name of the Windows PowerShell host required by this module
# PowerShellHostName = ''
}
```

## <a name="test-the-resource"></a><span data-ttu-id="30d1b-143">리소스 테스트</span><span class="sxs-lookup"><span data-stu-id="30d1b-143">Test the resource</span></span>

<span data-ttu-id="30d1b-144">앞에서 설명한 대로 폴더 구조에 클래스 및 매니페스트 파일을 저장한 후에는 새 리소스를 사용하는 구성을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30d1b-144">After saving the class and manifest files in the folder structure as described earlier, you can create a configuration that uses the new resource.</span></span> <span data-ttu-id="30d1b-145">DSC 구성을 실행하는 방법에 대한 정보는 [구성 시행](../pull-server/enactingConfigurations.md)을 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="30d1b-145">For information about how to run a DSC configuration, see [Enacting configurations](../pull-server/enactingConfigurations.md).</span></span> <span data-ttu-id="30d1b-146">다음 구성은 `c:\test\test.txt`의 파일이 있는지 여부를 확인하게 되며, 없을 경우 `c:\test.txt`의 파일을 복사합니다(구성을 실행하기 전에 `c:\test.txt`를 만들어야 함).</span><span class="sxs-lookup"><span data-stu-id="30d1b-146">The following configuration will check to see whether the file at `c:\test\test.txt` exists, and, if not, copies the file from `c:\test.txt` (you should create `c:\test.txt` before you run the configuration).</span></span>

```powershell
Configuration Test
{
    Import-DSCResource -module MyDscResource
    FileResource file
    {
        Path = "C:\test\test.txt"
        SourcePath = "c:\test.txt"
        Ensure = "Present"
    }
}
Test
Start-DscConfiguration -Wait -Force Test
```

## <a name="supporting-psdscrunascredential"></a><span data-ttu-id="30d1b-147">PsDscRunAsCredential 지원</span><span class="sxs-lookup"><span data-stu-id="30d1b-147">Supporting PsDscRunAsCredential</span></span>

><span data-ttu-id="30d1b-148">**참고:** **PsDscRunAsCredential** PowerShell 5.0 이상에 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="30d1b-148">**Note:** **PsDscRunAsCredential** is supported in PowerShell 5.0 and later.</span></span>

<span data-ttu-id="30d1b-149">**PsDscRunAsCredential** 속성을 [DSC 구성](../configurations/configurations.md) 리소스 블록에서 사용하면 지정된 자격 증명 집합으로 리소스를 실행해야 함을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30d1b-149">The **PsDscRunAsCredential** property can be used in [DSC configurations](../configurations/configurations.md) resource block to specify that the resource should be run under a specified set of credentials.</span></span>
<span data-ttu-id="30d1b-150">자세한 내용은 [사용자 자격 증명을 사용하여 DSC 실행](../configurations/runAsUser.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="30d1b-150">For more information, see [Running DSC with user credentials](../configurations/runAsUser.md).</span></span>

### <a name="require-or-disallow-psdscrunascredential-for-your-resource"></a><span data-ttu-id="30d1b-151">리소스에 대해 PsDscRunAsCredential을 필수 항목으로 지정하거나 사용 차단</span><span class="sxs-lookup"><span data-stu-id="30d1b-151">Require or disallow PsDscRunAsCredential for your resource</span></span>

<span data-ttu-id="30d1b-152">**DscResource()** 특성은 선택적 매개 변수 **RunAsCredential**을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="30d1b-152">The **DscResource()** attribute takes an optional parameter **RunAsCredential**.</span></span>
<span data-ttu-id="30d1b-153">이 매개 변수는 다음의 3개 값 중 하나를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="30d1b-153">This parameter takes one of three values:</span></span>

- <span data-ttu-id="30d1b-154">`Optional`: 이 리소스를 호출하는 구성에 대해 필요에 따라 **PsDscRunAsCredential**을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30d1b-154">`Optional` **PsDscRunAsCredential** is optional for configurations that call this resource.</span></span> <span data-ttu-id="30d1b-155">기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="30d1b-155">This is the default value.</span></span>
- <span data-ttu-id="30d1b-156">`Mandatory`: 이 리소스를 호출하는 모든 구성에 대해 **PsDscRunAsCredential**을 반드시 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="30d1b-156">`Mandatory` **PsDscRunAsCredential** must be used for any configuration that calls this resource.</span></span>
- <span data-ttu-id="30d1b-157">`NotSupported`: 이 리소스를 호출하는 구성에서 **PsDscRunAsCredential**을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="30d1b-157">`NotSupported` Configurations that call this resource cannot use **PsDscRunAsCredential**.</span></span>
- <span data-ttu-id="30d1b-158">`Default`: `Optional`과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="30d1b-158">`Default` Same as `Optional`.</span></span>

<span data-ttu-id="30d1b-159">예를 들어 사용자 지정 리소스가 **PsDscRunAsCredential** 사용을 지원하지 않도록 지정하려면 다음 특성을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="30d1b-159">For example, use the following attribute to specify that your custom resource does not support using **PsDscRunAsCredential**:</span></span>

```powershell
[DscResource(RunAsCredential=NotSupported)]
class FileResource {
}
```

### <a name="declaring-multiple-class-resources-in-a-module"></a><span data-ttu-id="30d1b-160">모듈의 여러 클래스 리소스를 선언합니다.</span><span class="sxs-lookup"><span data-stu-id="30d1b-160">Declaring multiple class resources in a module</span></span>

<span data-ttu-id="30d1b-161">모듈 여러 클래스 기반 DSC 리소스를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30d1b-161">A module can define multiple class based DSC resources.</span></span> <span data-ttu-id="30d1b-162">다음과 같은 방법으로 폴더 구조를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30d1b-162">You can create the folder structure in the following ways:</span></span>

1. <span data-ttu-id="30d1b-163">첫 번째 리소스를 정의 합니다 "<ModuleName>. psm1" 파일 및 후속 리소스를 **DSCResources** 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="30d1b-163">Define the first resource in the "<ModuleName>.psm1" file and subsequent resources under the **DSCResources** folder.</span></span>

   ```
   $env:ProgramFiles\WindowsPowerShell\Modules (folder)
        |- MyDscResource (folder)
           |- MyDscResource.psm1
              MyDscResource.psd1
        |- DSCResources
           |- SecondResource.psm1
   ```

2. <span data-ttu-id="30d1b-164">아래의 모든 리소스를 정의 합니다 **DSCResources** 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="30d1b-164">Define all resources under the **DSCResources** folder.</span></span>

   ```
   $env:ProgramFiles\WindowsPowerShell\Modules (folder)
        |- MyDscResource (folder)
           |- MyDscResource.psm1
              MyDscResource.psd1
        |- DSCResources
           |- FirstResource.psm1
              SecondResource.psm1
   ```

> [!NOTE]
> <span data-ttu-id="30d1b-165">위의 예제에서는 아래에 있는 모든 PSM1 파일을 추가 합니다 **DSCResources** 에 **NestedModules** PSD1 파일에서 키입니다.</span><span class="sxs-lookup"><span data-stu-id="30d1b-165">In the examples above, add any PSM1 files under the **DSCResources** to the **NestedModules** key in your PSD1 file.</span></span>

### <a name="access-the-user-context"></a><span data-ttu-id="30d1b-166">사용자 컨텍스트 액세스</span><span class="sxs-lookup"><span data-stu-id="30d1b-166">Access the user context</span></span>

<span data-ttu-id="30d1b-167">사용자 지정 리소스 내에서 사용자 컨텍스트에 액세스하려는 경우 `$global:PsDscContext` 자동 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30d1b-167">To access the user context from within a custom resource, you can use the automatic variable `$global:PsDscContext`.</span></span>

<span data-ttu-id="30d1b-168">예를 들어 다음 코드는 리소스가 자세한 정보 출력 스트림으로 실행되는 사용자 컨텍스트를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="30d1b-168">For example the following code would write the user context under which the resource is running to the verbose output stream:</span></span>

```powershell
if (PsDscContext.RunAsUser) {
    Write-Verbose "User: $global:PsDscContext.RunAsUser";
}
```

## <a name="see-also"></a><span data-ttu-id="30d1b-169">참고 항목</span><span class="sxs-lookup"><span data-stu-id="30d1b-169">See Also</span></span>

[<span data-ttu-id="30d1b-170">사용자 지정 Windows PowerShell 필요한 상태 구성 리소스 빌드</span><span class="sxs-lookup"><span data-stu-id="30d1b-170">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>](authoringResource.md)
