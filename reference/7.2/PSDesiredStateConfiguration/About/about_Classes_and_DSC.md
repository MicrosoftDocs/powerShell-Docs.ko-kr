---
description: PowerShell에서 DSC (Desired State Configuration)를 사용 하 여 개발 하는 데 클래스를 사용 하는 방법을 설명 합니다.
Locale: en-US
ms.date: 01/11/2019
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Classes_and_DSC
ms.openlocfilehash: a5819ac54f34393e0fbbf3b8933e840730c5d827
ms.sourcegitcommit: cc72c40315fd2981d3009b335accbfa52d57640c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/30/2020
ms.locfileid: "99602038"
---
# <a name="about-classes-and-desired-state-configuration"></a><span data-ttu-id="e98ee-103">클래스 및 필요한 상태 구성 정보</span><span class="sxs-lookup"><span data-stu-id="e98ee-103">About Classes and Desired State Configuration</span></span>

## <a name="short-description"></a><span data-ttu-id="e98ee-104">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="e98ee-104">Short description</span></span>

<span data-ttu-id="e98ee-105">PowerShell에서 DSC (Desired State Configuration)를 사용 하 여 개발 하는 데 클래스를 사용 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-105">Describes how you can use classes to develop in PowerShell with Desired State Configuration (DSC).</span></span>

## <a name="long-description"></a><span data-ttu-id="e98ee-106">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-106">Long description</span></span>

<span data-ttu-id="e98ee-107">Windows PowerShell 5.0부터 언어는 다른 개체 지향 프로그래밍 언어와 유사한 형식 구문 및 의미 체계를 사용 하 여 클래스 및 기타 사용자 정의 형식을 정의 하기 위해 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-107">Starting in Windows PowerShell 5.0, language was added to define classes and other user-defined types, by using formal syntax and semantics that are similar to other object-oriented programming languages.</span></span> <span data-ttu-id="e98ee-108">목표는 개발자 및 IT 전문가가 보다 광범위 한 사용 사례에 PowerShell을 적용 하 고, DSC 리소스와 같은 PowerShell 아티팩트의 개발을 간소화 하 고, 관리 표면의 범위를 가속화 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-108">The goal is to enable developers and IT professionals to embrace PowerShell for a wider range of use cases, simplify development of PowerShell artifacts such as DSC resources, and accelerate coverage of management surfaces.</span></span>

## <a name="supported-scenarios"></a><span data-ttu-id="e98ee-109">지원되는 시나리오</span><span class="sxs-lookup"><span data-stu-id="e98ee-109">Supported scenarios</span></span>

<span data-ttu-id="e98ee-110">다음과 같은 시나리오가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-110">The following scenarios are supported:</span></span>

- <span data-ttu-id="e98ee-111">PowerShell 언어를 사용 하 여 DSC 리소스 및 관련 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-111">Define DSC resources and their associated types by using the PowerShell language.</span></span>
- <span data-ttu-id="e98ee-112">클래스, 속성, 메서드, 상속 등 친숙 한 개체 지향 프로그래밍 구문을 사용 하 여 PowerShell에서 사용자 지정 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-112">Define custom types in PowerShell by using familiar object-oriented programming constructs, such as classes, properties, methods, and inheritance.</span></span>
- <span data-ttu-id="e98ee-113">PowerShell 언어를 사용 하 여 형식 디버그</span><span class="sxs-lookup"><span data-stu-id="e98ee-113">Debug types by using the PowerShell language.</span></span>
- <span data-ttu-id="e98ee-114">올바른 수준에서 공식 메커니즘을 사용 하 여 예외를 생성 하 고 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-114">Generate and handle exceptions by using formal mechanisms, and at the right level.</span></span>

## <a name="define-dsc-resources-with-classes"></a><span data-ttu-id="e98ee-115">클래스를 사용 하 여 DSC 리소스 정의</span><span class="sxs-lookup"><span data-stu-id="e98ee-115">Define DSC resources with classes</span></span>

<span data-ttu-id="e98ee-116">구문 변경과는 별도로, 클래스 정의 DSC 리소스와 cmdlet DSC 리소스 공급자의 주요 차이점은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-116">Apart from syntax changes, the major differences between a class-defined DSC resource and a cmdlet DSC resource provider are the following items:</span></span>

- <span data-ttu-id="e98ee-117">MOF (Management Object Format) 파일은 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-117">A Management Object Format (MOF) file is not required.</span></span>
- <span data-ttu-id="e98ee-118">모듈 폴더에서 DSCResource 하위 폴더가 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-118">A DSCResource subfolder in the module folder is not required.</span></span>
- <span data-ttu-id="e98ee-119">PowerShell 모듈 파일에 여러 가지 DSC 리소스 클래스가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-119">A PowerShell module file can contain multiple DSC resource classes.</span></span>

## <a name="create-a-class-defined-dsc-resource-provider"></a><span data-ttu-id="e98ee-120">클래스 정의 DSC 리소스 공급자 만들기</span><span class="sxs-lookup"><span data-stu-id="e98ee-120">Create a class-defined DSC resource provider</span></span>

<span data-ttu-id="e98ee-121">다음 예제는 Mydscresource.psd1 모듈로 저장 된 클래스 정의 DSC 리소스 공급자입니다. .psm1.</span><span class="sxs-lookup"><span data-stu-id="e98ee-121">The following example is a class-defined DSC resource provider that is saved as a module, MyDSCResource.psm1.</span></span> <span data-ttu-id="e98ee-122">항상 클래스 정의 DSC 리소스 공급자에 키 속성을 포함 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-122">You must always include a key property in a class-defined DSC resource provider.</span></span>

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
        if($this.ensure -eq [Ensure]::Present)
        {
            if(-not $fileExists)
            {
                $this.CopyFile()
            }
        }
        else
        {
            if($fileExists)
            {
                Write-Verbose -Message "Deleting the file $($this.Path)"
                Remove-Item -LiteralPath $this.Path -Force
            }
        }
    }

    <#

        This method is equivalent of the Test-TargetResource script
        function. It should return True or False, showing whether the
        resource is in a desired state.
    #>
    [bool] Test()
    {
        $present = $this.TestFilePath($this.Path)

        if($this.Ensure -eq [Ensure]::Present)
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
        The implementation should use the keys to find appropriate
        resources. This method returns an instance of this class with the
        updated key properties.
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
        Helper method to check if the file exists and it is correct file
    #>
    [bool] TestFilePath([string] $location)
    {
        $present = $true

        $item = Get-ChildItem -LiteralPath $location -ea Ignore
        if ($null -eq $item)
        {
            $present = $false
        }
        elseif( $item.PSProvider.Name -ne "FileSystem")
        {
            throw "Path $($location) is not a file path."
        }
        elseif($item.PSIsContainer)
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
        if(-not $this.TestFilePath($this.SourcePath))
        {
            throw "SourcePath $($this.SourcePath) is not found."
        }

        [System.IO.FileInfo]
        $destFileInfo = new-object System.IO.FileInfo($this.Path)

        if (-not $destFileInfo.Directory.Exists)
        {
            $FullName = $destFileInfo.Directory.FullName
            $Message = "Creating directory $FullName"

            Write-Verbose -Message $Message

            #use CreateDirectory instead of New-Item to avoid code
            # to handle the non-terminating error
            [System.IO.Directory]::CreateDirectory($FullName)
        }

        if(Test-Path -LiteralPath $this.Path -PathType Container)
        {
            throw "Path $($this.Path) is a directory path"
        }

        Write-Verbose -Message "Copying $this.SourcePath to $this.Path"

        #DSC engine catches and reports any error that occurs
        Copy-Item -Path $this.SourcePath -Destination $this.Path -Force
    }
}
```

## <a name="create-a-module-manifest"></a><span data-ttu-id="e98ee-123">모듈 매니페스트 만들기</span><span class="sxs-lookup"><span data-stu-id="e98ee-123">Create a module manifest</span></span>

<span data-ttu-id="e98ee-124">클래스 정의 DSC 리소스 공급자를 만들고 모듈로 저장한 후 모듈에 대한 모듈 매니페스트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-124">After creating the class-defined DSC resource provider, and saving it as a module, create a module manifest for the module.</span></span> <span data-ttu-id="e98ee-125">DSC 엔진에 사용할 수 있는 클래스 기반 리소스를 만들려면 매니페스트 파일에 리소스를 내보내도록 모듈에게 지시하는 `DscResourcesToExport` 문을 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-125">To make a class-based resource available to the DSC engine, you must include a `DscResourcesToExport` statement in the manifest file that instructs the module to export the resource.</span></span> <span data-ttu-id="e98ee-126">이 예제에서는 다음 모듈 매니페스트가 MyDscResource.psd1로 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-126">In this example, the following module manifest is saved as MyDscResource.psd1.</span></span>

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

# Minimum version of the PowerShell engine required by this module
PowerShellVersion = '5.0'

# Name of the PowerShell host required by this module
# PowerShellHostName = ''

}
```

## <a name="deploy-a-dsc-resource-provider"></a><span data-ttu-id="e98ee-127">DSC 리소스 공급자 배포</span><span class="sxs-lookup"><span data-stu-id="e98ee-127">Deploy a DSC resource provider</span></span>

<span data-ttu-id="e98ee-128">또는에서 Mydscresource.psd1 폴더를 만들어 새 DSC 리소스 공급자를 배포 `$pshome\Modules` 합니다 `$env:SystemDrive\ProgramFiles\WindowsPowerShell\Modules` .</span><span class="sxs-lookup"><span data-stu-id="e98ee-128">Deploy the new DSC resource provider by creating a MyDscResource folder in `$pshome\Modules` or `$env:SystemDrive\ProgramFiles\WindowsPowerShell\Modules`.</span></span>

<span data-ttu-id="e98ee-129">DSCResource 하위 폴더는 만들 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-129">You do not need to create a DSCResource subfolder.</span></span> <span data-ttu-id="e98ee-130">모듈 및 모듈 매니페스트 파일(MyDscResource.psm1 및 MyDscResource.psd1)을 MyDscResource 폴더에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-130">Copy the module and module manifest files (MyDscResource.psm1 and MyDscResource.psd1) to the MyDscResource folder.</span></span>

<span data-ttu-id="e98ee-131">이 시점에서 DSC 리소스와 마찬가지로 구성 스크립트를 만들어 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-131">From this point, you create and run a configuration script as you would with any DSC resource.</span></span>

## <a name="create-a-dsc-configuration-script"></a><span data-ttu-id="e98ee-132">DSC 구성 스크립트 만들기</span><span class="sxs-lookup"><span data-stu-id="e98ee-132">Create a DSC configuration script</span></span>

<span data-ttu-id="e98ee-133">앞에서 설명한 대로 폴더 구조에 클래스 및 매니페스트 파일을 저장한 후에는 새 리소스를 사용하는 구성을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-133">After saving the class and manifest files in the folder structure as described earlier, you can create a configuration that uses the new resource.</span></span> <span data-ttu-id="e98ee-134">다음 구성에서는 Mydscresource.psd1 모듈을 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-134">The following configuration references the MyDSCResource module.</span></span> <span data-ttu-id="e98ee-135">구성을 MyResource.ps1 스크립트로 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-135">Save the configuration as a script, MyResource.ps1.</span></span>

<span data-ttu-id="e98ee-136">DSC 구성을 실행 하는 방법에 대 한 자세한 내용은 [Windows PowerShell 필요한 상태 구성 개요](/powershell/scripting/dsc/overview/dscforengineers)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e98ee-136">For information about how to run a DSC configuration, see [Windows PowerShell Desired State Configuration Overview](/powershell/scripting/dsc/overview/dscforengineers).</span></span>

<span data-ttu-id="e98ee-137">구성을 실행 하기 전에를 만듭니다 `C:\test.txt` .</span><span class="sxs-lookup"><span data-stu-id="e98ee-137">Before you run the configuration, create `C:\test.txt`.</span></span> <span data-ttu-id="e98ee-138">구성에서는 파일이에 있는지 확인 `c:\test\test.txt` 합니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-138">The configuration checks if the file exists at `c:\test\test.txt`.</span></span> <span data-ttu-id="e98ee-139">파일이 없는 경우 구성은에서 파일을 복사 합니다 `C:\test.txt` .</span><span class="sxs-lookup"><span data-stu-id="e98ee-139">If the file does not exist, the configuration copies the file from `C:\test.txt`.</span></span>

```powershell
Configuration Test
{
    Import-DSCResource -module MyDscResource
    FileResource file
    {
        Path = "C:\test\test.txt"
        SourcePath = "C:\test.txt"
        Ensure = "Present"
    }
}
Test
Start-DscConfiguration -Wait -Force Test
```

<span data-ttu-id="e98ee-140">DSC 구성 스크립트와 마찬가지로이 스크립트를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-140">Run this script as you would any DSC configuration script.</span></span> <span data-ttu-id="e98ee-141">구성을 시작 하려면 관리자 권한 PowerShell 콘솔에서 다음을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-141">To start the configuration, in an elevated PowerShell console, run the following:</span></span>

`PS C:\test> .\MyResource.ps1`

## <a name="inheritance-in-powershell-classes"></a><span data-ttu-id="e98ee-142">PowerShell 클래스의 상속</span><span class="sxs-lookup"><span data-stu-id="e98ee-142">Inheritance in PowerShell classes</span></span>

### <a name="declare-base-classes-for-powershell-classes"></a><span data-ttu-id="e98ee-143">PowerShell 클래스에 대 한 기본 클래스 선언</span><span class="sxs-lookup"><span data-stu-id="e98ee-143">Declare base classes for PowerShell classes</span></span>

<span data-ttu-id="e98ee-144">다음 예제와 같이 PowerShell 클래스를 다른 PowerShell 클래스의 기본 형식으로 선언할 수 있습니다. 여기서 **과일** 은 **apple** 의 기본 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-144">You can declare a PowerShell class as a base type for another PowerShell class, as shown in the following example, in which **fruit** is a base type for **apple**.</span></span>

```powershell
class fruit
{
    [int]sold() {return 100500}
}

class apple : fruit {}
    [apple]::new().sold() # return 100500
```

### <a name="declare-implemented-interfaces-for-powershell-classes"></a><span data-ttu-id="e98ee-145">PowerShell 클래스에 대해 구현 된 인터페이스 선언</span><span class="sxs-lookup"><span data-stu-id="e98ee-145">Declare implemented interfaces for PowerShell classes</span></span>

<span data-ttu-id="e98ee-146">구현 된 인터페이스는 기본 형식 뒤에 선언 하거나, `:` 지정 된 기본 형식이 없는 경우 콜론 () 바로 다음에 선언할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-146">You can declare implemented interfaces after base types, or immediately after a colon (`:`) if there is no base type specified.</span></span> <span data-ttu-id="e98ee-147">쉼표를 사용하여 모든 형식 이름을 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-147">Separate all type names by using commas.</span></span> <span data-ttu-id="e98ee-148">이는 c # 구문과 유사 합니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-148">This is similar to C# syntax.</span></span>

```powershell
class MyComparable : system.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}

class MyComparableTest : test, system.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}
```

### <a name="call-base-class-constructors"></a><span data-ttu-id="e98ee-149">기본 클래스 생성자 호출</span><span class="sxs-lookup"><span data-stu-id="e98ee-149">Call base class constructors</span></span>

<span data-ttu-id="e98ee-150">서브 클래스에서 기본 클래스 생성자를 호출 하려면 `base` 다음 예제와 같이 키워드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-150">To call a base class constructor from a subclass, add the `base` keyword, as shown in the following example:</span></span>

```powershell
class A {
    [int]$a
    A([int]$a)
    {
        $this.a = $a
    }
}

class B : A
{
    B() : base(103) {}
}

    [B]::new().a # return 103
```

<span data-ttu-id="e98ee-151">기본 클래스에 기본 생성자 (매개 변수 없음)가 있는 경우 다음과 같이 명시적 생성자 호출을 생략할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-151">If a base class has a default constructor (no parameters), you can omit an explicit constructor call, as shown.</span></span>

```powershell
class C : B
{
    C([int]$c) {}
}
```

### <a name="call-base-class-methods"></a><span data-ttu-id="e98ee-152">기본 클래스 메서드 호출</span><span class="sxs-lookup"><span data-stu-id="e98ee-152">Call base class methods</span></span>

<span data-ttu-id="e98ee-153">하위 클래스에서 기존 메서드를 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-153">You can override existing methods in subclasses.</span></span> <span data-ttu-id="e98ee-154">재정의를 수행 하려면 동일한 이름과 서명을 사용 하 여 메서드를 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-154">To do the override, declare methods by using the same name and signature.</span></span>

```powershell
class baseClass
{
    [int]days() {return 100500}
}
class childClass1 : baseClass
{
    [int]days () {return 200600}
}

    [childClass1]::new().days() # return 200600
```

<span data-ttu-id="e98ee-155">재정의 된 구현에서 기본 클래스 메서드를 호출 하려면 호출 시 기본 클래스로 캐스팅 `([baseclass]$this)` 합니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-155">To call base class methods from overridden implementations, cast to the base class `([baseclass]$this)` on invocation.</span></span>

```powershell
class childClass2 : baseClass
{
    [int]days()
    {
        return 3 * ([baseClass]$this).days()
    }
}

    [childClass2]::new().days() # return 301500
```

<span data-ttu-id="e98ee-156">모든 PowerShell 메서드는 가상입니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-156">All PowerShell methods are virtual.</span></span> <span data-ttu-id="e98ee-157">재정의할 때와 동일한 구문을 사용 하 여 하위 클래스에서 비가상 .NET 메서드를 숨길 수 있습니다. 동일한 이름 및 서명을 사용 하 여 메서드를 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-157">You can hide non-virtual .NET methods in a subclass by using the same syntax as you do for an override: declare methods with same name and signature.</span></span>

```powershell
class MyIntList : system.collections.generic.list[int]
{
    # Add is final in system.collections.generic.list
    [void] Add([int]$arg)
    {
        ([system.collections.generic.list[int]]$this).Add($arg * 2)
    }
}

$list = [MyIntList]::new()
$list.Add(100)
$list[0] # return 200
```

### <a name="current-limitations-with-class-inheritance"></a><span data-ttu-id="e98ee-158">클래스 상속의 현재 제한 사항</span><span class="sxs-lookup"><span data-stu-id="e98ee-158">Current limitations with class inheritance</span></span>

<span data-ttu-id="e98ee-159">클래스 상속의 제한 사항은 PowerShell에서 인터페이스를 선언 하는 구문이 없다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-159">A limitation with class inheritance is that there is no syntax to declare interfaces in PowerShell.</span></span>

## <a name="defining-custom-types-in-powershell"></a><span data-ttu-id="e98ee-160">PowerShell에서 사용자 지정 형식 정의</span><span class="sxs-lookup"><span data-stu-id="e98ee-160">Defining custom types in PowerShell</span></span>

<span data-ttu-id="e98ee-161">Windows PowerShell 5.0에서는 몇 가지 언어 요소를 소개 했습니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-161">Windows PowerShell 5.0 introduced several language elements.</span></span>

### <a name="class-keyword"></a><span data-ttu-id="e98ee-162">Class 키워드</span><span class="sxs-lookup"><span data-stu-id="e98ee-162">Class keyword</span></span>

<span data-ttu-id="e98ee-163">새 클래스를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-163">Defines a new class.</span></span>
<span data-ttu-id="e98ee-164">`class`키워드는 true .NET Framework 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-164">The `class` keyword is a true .NET Framework type.</span></span>
<span data-ttu-id="e98ee-165">클래스 멤버는 공용입니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-165">Class members are public.</span></span>

```powershell
class MyClass
{
}
```

### <a name="enum-keyword-and-enumerations"></a><span data-ttu-id="e98ee-166">Enum 키워드 및 열거형</span><span class="sxs-lookup"><span data-stu-id="e98ee-166">Enum keyword and enumerations</span></span>

<span data-ttu-id="e98ee-167">키워드에 대 한 지원이 `enum` 추가 되었으며 주요 변경 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-167">Support for the `enum` keyword was added and is a breaking change.</span></span> <span data-ttu-id="e98ee-168">`enum`구분 기호는 현재 줄 바꿈입니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-168">The `enum` delimiter is currently a newline.</span></span> <span data-ttu-id="e98ee-169">이미를 사용 하 고 있는 사용자에 대 한 해결 방법은 `enum` 단어 앞에 앰퍼샌드 ()를 삽입 하는 것입니다 `&` .</span><span class="sxs-lookup"><span data-stu-id="e98ee-169">A workaround for those who are already using `enum` is to insert an ampersand (`&`) before the word.</span></span> <span data-ttu-id="e98ee-170">현재 제한 사항: `enum` 다음 예제와 같이 열거자 자체를 기준으로 열거자를 정의할 수 없지만 다른 방식으로 초기화할 수 있습니다 `enum` .</span><span class="sxs-lookup"><span data-stu-id="e98ee-170">Current limitations: you cannot define an enumerator in terms of itself, but you can initialize `enum` in terms of another `enum`, as shown in the following example:</span></span>

<span data-ttu-id="e98ee-171">현재 기본 유형을 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-171">The base type cannot currently be specified.</span></span> <span data-ttu-id="e98ee-172">기본 형식은 항상 [int]입니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-172">The base type is always [int].</span></span>

```powershell
enum Color2
{
    Yellow = [Color]::Blue
}
```

<span data-ttu-id="e98ee-173">열거자 값은 구문 분석 시간 상수여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-173">An enumerator value must be a parse time constant.</span></span> <span data-ttu-id="e98ee-174">열거자 값은 호출 된 명령의 결과로 설정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-174">The enumerator value cannot be set to the result of an invoked command.</span></span>

```powershell
enum MyEnum
{
    Enum1
    Enum2
    Enum3 = 42
    Enum4 = [int]::MaxValue
}
```

<span data-ttu-id="e98ee-175">`Enum` 에서는 다음 예제와 같이 산술 연산을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-175">`Enum` supports arithmetic operations, as shown in the following example:</span></span>

```powershell
enum SomeEnum { Max = 42 }
enum OtherEnum { Max = [SomeEnum]::Max + 1 }
```

### <a name="hidden-keyword"></a><span data-ttu-id="e98ee-176">Hidden 키워드</span><span class="sxs-lookup"><span data-stu-id="e98ee-176">Hidden keyword</span></span>

<span data-ttu-id="e98ee-177">`hidden`Windows PowerShell 5.0에 도입 된 키워드는 기본 결과에서 클래스 멤버를 숨깁니다 `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="e98ee-177">The `hidden` keyword, introduced in Windows PowerShell 5.0, hides class members from default `Get-Member` results.</span></span> <span data-ttu-id="e98ee-178">다음 줄과 같이 hidden 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-178">Specify the hidden property as shown in the following line:</span></span>

```powershell
hidden [type] $classmember = <value>
```

<span data-ttu-id="e98ee-179">숨겨진 멤버를 정의 하는 클래스에서 완료가 발생 하지 않은 경우에는 탭 완성 또는 IntelliSense를 사용 하 여 숨겨진 멤버를 표시 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-179">Hidden members are not displayed by using tab completion or IntelliSense, unless the completion occurs in the class that defines the hidden member.</span></span>

<span data-ttu-id="e98ee-180">새 특성인 **system.management.automation.hiddenattribute** 가 추가 되어 c # 코드가 PowerShell 내에서 동일한 의미 체계를 가질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-180">A new attribute, **System.Management.Automation.HiddenAttribute**, was added, so that C# code can have the same semantics within PowerShell.</span></span>

<span data-ttu-id="e98ee-181">자세한 내용은 [about_Hidden](../../Microsoft.PowerShell.Core/About/about_hidden.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e98ee-181">For more information, see [about_Hidden](../../Microsoft.PowerShell.Core/About/about_hidden.md).</span></span>

### <a name="import-dscresource"></a><span data-ttu-id="e98ee-182">Import-DscResource</span><span class="sxs-lookup"><span data-stu-id="e98ee-182">Import-DscResource</span></span>

<span data-ttu-id="e98ee-183">`Import-DscResource`는 이제 진정한 동적 키워드입니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-183">`Import-DscResource` is now a true dynamic keyword.</span></span> <span data-ttu-id="e98ee-184">PowerShell은 지정된 모듈의 루트 모듈을 구문 분석하여 DscResource 특성이 포함된 클래스를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-184">PowerShell parses the specified module's root module, searching for classes that contain the DscResource attribute.</span></span>

### <a name="properties"></a><span data-ttu-id="e98ee-185">속성</span><span class="sxs-lookup"><span data-stu-id="e98ee-185">Properties</span></span>

<span data-ttu-id="e98ee-186">새 필드인가 `ImplementingAssembly` 에 추가 되었습니다 `ModuleInfo` .</span><span class="sxs-lookup"><span data-stu-id="e98ee-186">A new field, `ImplementingAssembly`, was added to `ModuleInfo`.</span></span> <span data-ttu-id="e98ee-187">스크립트가 클래스를 정의 하거나 이진 모듈에 대해 로드 된 어셈블리가 `ImplementingAssembly` 스크립트 모듈에 대해 만들어진 동적 어셈블리로 설정 된 경우</span><span class="sxs-lookup"><span data-stu-id="e98ee-187">If the script defines classes, or the loaded assembly for binary modules `ImplementingAssembly` is set to the dynamic assembly created for a script module.</span></span> <span data-ttu-id="e98ee-188">ModuleType = Manifest인 경우에는 설정되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-188">It is not set when ModuleType = Manifest.</span></span>

<span data-ttu-id="e98ee-189">필드에 대 한 리플렉션은 `ImplementingAssembly` 모듈에서 리소스를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-189">Reflection on the `ImplementingAssembly` field discovers resources in a module.</span></span> <span data-ttu-id="e98ee-190">즉, PowerShell이나 다른 관리 언어로 작성된 리소스를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-190">This means you can discover resources written in either PowerShell or other managed languages.</span></span>

<span data-ttu-id="e98ee-191">이니셜라이저가 있는 필드</span><span class="sxs-lookup"><span data-stu-id="e98ee-191">Fields with initializers.</span></span>

`[int] $i = 5`

<span data-ttu-id="e98ee-192">Static은 지원 되며 형식 제약 조건과 유사한 특성 처럼 작동 하므로 순서에 관계 없이 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-192">Static is supported and works like an attribute, similar to the type constraints, so it can be specified in any order.</span></span>

`static [int] $count = 0`

<span data-ttu-id="e98ee-193">형식은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-193">A type is optional.</span></span>

`$s = "hello"`

<span data-ttu-id="e98ee-194">모든 멤버는 공용입니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-194">All members are public.</span></span> <span data-ttu-id="e98ee-195">속성에는 줄 바꿈이나 세미콜론이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-195">Properties require either a newline or semicolon.</span></span> <span data-ttu-id="e98ee-196">개체 형식이 지정 되지 않은 경우 속성 형식은 **object** 입니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-196">If no object type is specified, the property type is **Object**.</span></span>

### <a name="constructors-and-instantiation"></a><span data-ttu-id="e98ee-197">생성자 및 인스턴스화</span><span class="sxs-lookup"><span data-stu-id="e98ee-197">Constructors and instantiation</span></span>

<span data-ttu-id="e98ee-198">PowerShell 클래스에는 클래스와 이름이 같은 생성자가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-198">PowerShell classes can have constructors that have the same name as their class.</span></span> <span data-ttu-id="e98ee-199">생성자는 오버로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-199">Constructors can be overloaded.</span></span> <span data-ttu-id="e98ee-200">정적 생성자가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-200">Static constructors are supported.</span></span>
<span data-ttu-id="e98ee-201">초기화 식이 있는 속성은 생성자에서 코드를 실행하기 전에 초기화됩니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-201">Properties with initialization expressions are initialized before running any code in a constructor.</span></span> <span data-ttu-id="e98ee-202">정적 속성은 정적 생성자의 본문보다 먼저 초기화되고, 인스턴스 속성은 비정적 생성자의 본문보다 먼저 초기화됩니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-202">Static properties are initialized before the body of a static constructor, and instance properties are initialized before the body of the non-static constructor.</span></span> <span data-ttu-id="e98ee-203">현재는 c # 구문과 같은 다른 생성자에서 생성자를 호출 하기 위한 구문이 `": this()")` 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-203">Currently, there is no syntax for calling a constructor from another constructor such as the C# syntax: `": this()")`.</span></span> <span data-ttu-id="e98ee-204">해결 방법은 일반적인 Init 메서드를 정의하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-204">The workaround is to define a common Init method.</span></span>

<span data-ttu-id="e98ee-205">다음은 클래스를 인스턴스화하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-205">The following are ways of instantiating classes:</span></span>

- <span data-ttu-id="e98ee-206">기본 생성자를 사용하여 인스턴스화합니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-206">Instantiating by using the default constructor.</span></span> <span data-ttu-id="e98ee-207">는 `New-Object` 이 릴리스에서 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-207">Note that `New-Object` is not supported in this release.</span></span>

  `$a = [MyClass]::new()`

- <span data-ttu-id="e98ee-208">매개 변수를 사용 하 여 생성자를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-208">Calling a constructor with a parameter.</span></span>

  `$b = [MyClass]::new(42)`

- <span data-ttu-id="e98ee-209">매개 변수가 여러 개인 생성자에 배열을 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-209">Passing an array to a constructor with multiple parameters</span></span>

  `$c = [MyClass]::new(@(42,43,44), "Hello")`

<span data-ttu-id="e98ee-210">이 릴리스의 경우 형식 이름이 어휘 적 으로만 표시 됩니다. 즉, 클래스를 정의 하는 모듈이 나 스크립트 외부에는 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-210">For this release, the type name is only visible lexically, meaning it is not visible outside of the module or script that defines the class.</span></span> <span data-ttu-id="e98ee-211">함수는 PowerShell에 정의 된 클래스의 인스턴스를 반환할 수 있으며 인스턴스는 모듈 또는 스크립트 외부에서 잘 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-211">Functions can return instances of a class defined in PowerShell, and instances work well outside of the module or script.</span></span>

<span data-ttu-id="e98ee-212">`Get-Member` **정적** 매개 변수는 생성자를 나열 하므로 다른 모든 메서드와 마찬가지로 오버 로드를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-212">The `Get-Member` **Static** parameter lists constructors, so you can view overloads like any other method.</span></span> <span data-ttu-id="e98ee-213">이 구문의 성능 또한 `New-Object`보다 현저하게 빠릅니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-213">The performance of this syntax is also considerably faster than `New-Object`.</span></span>

<span data-ttu-id="e98ee-214">**new** 라는 의사 정적 메서드는 다음 예제와 같이 .NET 형식에서 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-214">The pseudo-static method named **new** works with .NET types, as shown in the following example.</span></span> `[hashtable]::new()`

<span data-ttu-id="e98ee-215">이제 `Get-Member`를 사용하거나 다음 예제와 같이 생성자 오버로드를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-215">You can now see constructor overloads with `Get-Member`, or as shown in this example:</span></span>

```powershell
[hashtable]::new
OverloadDefinitions
-------------------
hashtable new()
hashtable new(int capacity)
hashtable new(int capacity, float loadFactor)
```

### <a name="methods"></a><span data-ttu-id="e98ee-216">메서드</span><span class="sxs-lookup"><span data-stu-id="e98ee-216">Methods</span></span>

<span data-ttu-id="e98ee-217">PowerShell 클래스 메서드는 끝 블록만 있는 **ScriptBlock** 으로 구현됩니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-217">A PowerShell class method is implemented as a **ScriptBlock** that has only an end block.</span></span> <span data-ttu-id="e98ee-218">모든 메서드는 공용입니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-218">All methods are public.</span></span> <span data-ttu-id="e98ee-219">다음에서는 **DoSomething** 이라는 메서드를 정의하는 예제를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-219">The following shows an example of defining a method named **DoSomething**.</span></span>

```powershell
class MyClass
{
    DoSomething($x)
    {
        $this._doSomething($x)       # method syntax
    }
    private _doSomething($a) {}
}
```

### <a name="method-invocation"></a><span data-ttu-id="e98ee-220">메서드 호출</span><span class="sxs-lookup"><span data-stu-id="e98ee-220">Method invocation</span></span>

<span data-ttu-id="e98ee-221">오버 로드 된 메서드가 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-221">Overloaded methods are supported.</span></span> <span data-ttu-id="e98ee-222">오버 로드 된 메서드는 기존 메서드와 동일 하 게 이름이 지정 되지만 지정 된 값으로 구별 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-222">Overloaded methods are named the same as an existing method but differentiated by their specified values.</span></span>

```powershell
$b = [MyClass]::new()
$b.DoSomething(42)
```

### <a name="invocation"></a><span data-ttu-id="e98ee-223">호출</span><span class="sxs-lookup"><span data-stu-id="e98ee-223">Invocation</span></span>

<span data-ttu-id="e98ee-224">[메서드 호출](#method-invocation)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e98ee-224">See [Method invocation](#method-invocation).</span></span>

### <a name="attributes"></a><span data-ttu-id="e98ee-225">특성</span><span class="sxs-lookup"><span data-stu-id="e98ee-225">Attributes</span></span>

<span data-ttu-id="e98ee-226">`DscResource`, 및의 세 가지 새 특성이 추가 되었습니다. `DscResourceKey` `DscResourceMandatory`</span><span class="sxs-lookup"><span data-stu-id="e98ee-226">Three new attributes were added: `DscResource`, `DscResourceKey`, and `DscResourceMandatory`.</span></span>

### <a name="return-types"></a><span data-ttu-id="e98ee-227">반환 형식</span><span class="sxs-lookup"><span data-stu-id="e98ee-227">Return types</span></span>

<span data-ttu-id="e98ee-228">반환 형식은 계약입니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-228">Return type is a contract.</span></span> <span data-ttu-id="e98ee-229">반환 값은 필요한 형식으로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-229">The return value is converted to the expected type.</span></span>
<span data-ttu-id="e98ee-230">반환 형식이 지정되지 않은 경우 반환 형식은 void입니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-230">If no return type is specified, the return type is void.</span></span> <span data-ttu-id="e98ee-231">개체 및 개체의 스트리밍은 의도적으로 또는 실수로 파이프라인에 쓸 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-231">There is no streaming of objects and objects cannot be written to the pipeline either intentionally or by accident.</span></span>

### <a name="lexical-scoping-of-variables"></a><span data-ttu-id="e98ee-232">변수의 어휘 범위 지정</span><span class="sxs-lookup"><span data-stu-id="e98ee-232">Lexical scoping of variables</span></span>

<span data-ttu-id="e98ee-233">다음에서는 이 릴리스에서 어휘 범위 지정이 작동하는 방식에 대한 예를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-233">The following shows an example of how lexical scoping works in this release.</span></span>

```powershell
$d = 42  # Script scope

function bar
{
    $d = 0  # Function scope
    [MyClass]::DoSomething()
}

class MyClass
{
    static [object] DoSomething()
    {
        return $d  # error, not found dynamically
        return $script:d # no error

        $d = $script:d
        return $d # no error, found lexically
    }
}

$v = bar
$v -eq $d # true
```

## <a name="example-create-custom-classes"></a><span data-ttu-id="e98ee-234">예: 사용자 지정 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="e98ee-234">Example: Create custom classes</span></span>

<span data-ttu-id="e98ee-235">다음 예제에서는 여러 가지 새로운 사용자 지정 클래스를 만들어 HTML DSL (동적 스타일 시트 언어)을 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-235">The following example creates several new, custom classes to implement an HTML Dynamic Stylesheet Language (DSL).</span></span> <span data-ttu-id="e98ee-236">이 예제에서는 모듈의 범위 외부에서 형식을 사용할 수 없기 때문에 도우미 함수를 추가 하 여 요소 클래스의 일부로 제목 스타일 및 표와 같은 특정 요소 형식을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e98ee-236">The example adds helper functions to create specific element types as part of the element class, such as heading styles and tables, because types cannot be used outside the scope of a module.</span></span>

```powershell
# Classes that define the structure of the document
#
class Html
{
    [string] $docType
    [HtmlHead] $Head
    [Element[]] $Body

    [string] Render()
    {
        $text = "<html>`n<head>`n"
        $text += $Head
        $text += "`n</head>`n<body>`n"
        $text += $Body -join "`n" # Render all of the body elements
        $text += "</body>`n</html>"
        return $text
    }
    [string] ToString() { return $this.Render() }
}

class HtmlHead
{
    $Title
    $Base
    $Link
    $Style
    $Meta
    $Script
    [string] Render() { return "<title>$Title</title>" }
    [string] ToString() { return $this.Render() }
}

class Element
{
    [string] $Tag
    [string] $Text
    [hashtable] $Attributes
    [string] Render() {
        $attributesText= ""
        if ($Attributes)
        {
            foreach ($attr in $Attributes.Keys)
            {
                $attributesText = " $attr=`"$($Attributes[$attr])`""
            }
        }

        return "<${tag}${attributesText}>$text</$tag>`n"
    }
    [string] ToString() { return $this.Render() }
}

#
# Helper functions for creating specific element types on top of the classes.
# These are required because types aren't visible outside of the module.
#
function H1 {[Element] @{Tag = "H1"; Text = $args.foreach{$_} -join " "}}
function H2 {[Element] @{Tag = "H2"; Text = $args.foreach{$_} -join " "}}
function H3 {[Element] @{Tag = "H3"; Text = $args.foreach{$_} -join " "}}
function P  {[Element] @{Tag = "P" ; Text = $args.foreach{$_} -join " "}}
function B  {[Element] @{Tag = "B" ; Text = $args.foreach{$_} -join " "}}
function I  {[Element] @{Tag = "I" ; Text = $args.foreach{$_} -join " "}}
function HREF
{
    param (
        $Name,
        $Link
    )

    return [Element] @{
        Tag = "A"
        Attributes = @{ HREF = $link }
        Text = $name
    }
}
function Table
{
    param (
        [Parameter(Mandatory)]
        [object[]]
            $Data,
        [Parameter()]
        [string[]]
            $Properties = "*",
        [Parameter()]
        [hashtable]
            $Attributes = @{ border=2; cellpadding=2; cellspacing=2 }
    )

    $bodyText = ""
    # Add the header tags
    $bodyText +=  $Properties.foreach{TH $_}
    # Add the rows
    $bodyText += foreach ($row in $Data)
                {
                            TR (-join $Properties.Foreach{ TD ($row.$_) } )
                }

    $table = [Element] @{
                Tag = "Table"
                Attributes = $Attributes
                Text = $bodyText
            }
    $table
}
function TH  {([Element] @{Tag="TH"; Text=$args.foreach{$_} -join " "})}
function TR  {([Element] @{Tag="TR"; Text=$args.foreach{$_} -join " "})}
function TD  {([Element] @{Tag="TD"; Text=$args.foreach{$_} -join " "})}

function Style
{
    return  [Element]  @{
        Tag = "style"
        Text = "$args"
    }
}

# Takes a hash table, casts it to and HTML document
# and then returns the resulting type.
#
function Html ([HTML] $doc) { return $doc }
```

## <a name="see-also"></a><span data-ttu-id="e98ee-237">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e98ee-237">See also</span></span>

[<span data-ttu-id="e98ee-238">about_Enum</span><span class="sxs-lookup"><span data-stu-id="e98ee-238">about_Enum</span></span>](../../Microsoft.PowerShell.Core/About/about_Enum.md)

[<span data-ttu-id="e98ee-239">about_Hidden</span><span class="sxs-lookup"><span data-stu-id="e98ee-239">about_Hidden</span></span>](../../Microsoft.PowerShell.Core/About/about_hidden.md)

[<span data-ttu-id="e98ee-240">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="e98ee-240">about_Language_Keywords</span></span>](../../Microsoft.PowerShell.Core/About/about_Language_Keywords.md)

[<span data-ttu-id="e98ee-241">about_Methods</span><span class="sxs-lookup"><span data-stu-id="e98ee-241">about_Methods</span></span>](../../Microsoft.PowerShell.Core/About/about_Methods.md)

[<span data-ttu-id="e98ee-242">사용자 지정 PowerShell 필요한 상태 구성 리소스 빌드</span><span class="sxs-lookup"><span data-stu-id="e98ee-242">Build Custom PowerShell Desired State Configuration Resources</span></span>](/powershell/scripting/dsc/resources/authoringResource)
