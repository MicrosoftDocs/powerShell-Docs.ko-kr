---
description: PowerShell에서 DSC (Desired State Configuration)를 사용 하 여 개발 하는 데 클래스를 사용 하는 방법을 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 1/11/2019
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Classes_and_DSC
ms.openlocfilehash: 272d6872d096de864044ae41449caff472bb1799
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93222386"
---
# <a name="about-classes-and-desired-state-configuration"></a>클래스 및 필요한 상태 구성 정보

## <a name="short-description"></a>간단한 설명

PowerShell에서 DSC (Desired State Configuration)를 사용 하 여 개발 하는 데 클래스를 사용 하는 방법을 설명 합니다.

## <a name="long-description"></a>자세한 설명입니다.

Windows PowerShell 5.0부터 언어는 다른 개체 지향 프로그래밍 언어와 유사한 형식 구문 및 의미 체계를 사용 하 여 클래스 및 기타 사용자 정의 형식을 정의 하기 위해 추가 되었습니다. 목표는 개발자 및 IT 전문가가 보다 광범위 한 사용 사례에 PowerShell을 적용 하 고, DSC 리소스와 같은 PowerShell 아티팩트의 개발을 간소화 하 고, 관리 표면의 범위를 가속화 하는 것입니다.

## <a name="supported-scenarios"></a>지원되는 시나리오

다음과 같은 시나리오가 지원됩니다.

- PowerShell 언어를 사용 하 여 DSC 리소스 및 관련 형식을 정의 합니다.
- 클래스, 속성, 메서드, 상속 등 친숙 한 개체 지향 프로그래밍 구문을 사용 하 여 PowerShell에서 사용자 지정 형식을 정의 합니다.
- PowerShell 언어를 사용 하 여 형식 디버그
- 올바른 수준에서 공식 메커니즘을 사용 하 여 예외를 생성 하 고 처리 합니다.

## <a name="define-dsc-resources-with-classes"></a>클래스를 사용 하 여 DSC 리소스 정의

구문 변경과는 별도로, 클래스 정의 DSC 리소스와 cmdlet DSC 리소스 공급자의 주요 차이점은 다음과 같습니다.

- MOF (Management Object Format) 파일은 필요 하지 않습니다.
- 모듈 폴더에서 DSCResource 하위 폴더가 필요하지 않습니다.
- PowerShell 모듈 파일에 여러 가지 DSC 리소스 클래스가 포함될 수 있습니다.

## <a name="create-a-class-defined-dsc-resource-provider"></a>클래스 정의 DSC 리소스 공급자 만들기

다음 예제는 Mydscresource.psd1 모듈로 저장 된 클래스 정의 DSC 리소스 공급자입니다. .psm1. 항상 클래스 정의 DSC 리소스 공급자에 키 속성을 포함 해야 합니다.

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
        if ($item -eq $null)
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
# This module defines a class for a DSC "FileResource" provider.

enum Ensure
{
    Absent
    Present
}

<# This resource manages the file in a specific path.
[DscResource()] indicates the class is a DSC resource
#>

[DscResource()]
class FileResource{

    <# This is a key property
        [DscResourceKey()] also means the property is required.
        It is guaranteed to be set, other properties may not
        be set if the configuration did not specify values.
    #>
    [DscResourceKey()]
    [string]$Path

    <#
        [DscResourceMandatory()] means the property is required.
        It is guaranteed to be set, other properties may not be set
        if the configuration did not specify values.
    #>
    [DscResourceMandatory()]
    [Ensure] $Ensure

    <#
        [DscResourceMandatory()] means the property is required.
    #>
    [DscResourceMandatory()]
    [string] $SourcePath

    [DscResource

    <#
        This method replaces the Set-TargetResource DSC script function.
        It sets the resource to the desired state.
    #>
    [void] Set()
    {
        $fileExists = Test-Path -path $this.Path -PathType Leaf
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
                Write-Verbose -Message "Deleting the file $this.Path"
                Remove-Item -LiteralPath $this.Path
            }
        }
    }

    <#

        This method replaces the Test-TargetResource function.
        It should return True or False, showing whether the resource
        is in a desired state.
    #>

    [bool] Test()
    {
        if(Test-Path -path $this.Path -PathType Container)
        {
            throw "Path '$this.Path' is a directory path."
        }

        $fileExists = Test-Path -path $this.Path -PathType Leaf

        if($this.ensure -eq [Ensure]::Present)
        {
            return $fileExists
        }

        return (-not $fileExists)
    }

    <#
        This method replaces the Get-TargetResource function.
        The implementation should use the keys to find appropriate
        resources. This method returns an instance of this class with the
        updated key properties.
    #>

    [FileResource] Get()
    {
        $file = Get-item $this.Path
        return $this
    }

    <#
        Helper method to copy file from source to path.
        Because this resource provider run under system,
        Only the Administrators and system have full
        access to the new created directory and file
    #>
    CopyFile()
    {
        if(Test-Path -path $this.SourcePath -PathType Container)
        {
            throw "SourcePath '$this.SourcePath' is a directory path"
        }

        if( -not (Test-Path -path $this.SourcePath -PathType Leaf))
        {
            throw "SourcePath '$this.SourcePath' is not found."
        }

        [System.IO.FileInfo]
        $destFileInfo = new-object System.IO.FileInfo($this.Path)

        if (-not $destFileInfo.Directory.Exists)
        {
            $FullName = $destFileInfo.Directory.FullName
            $Message = "Creating directory $FullName"

            Write-Verbose -Message $Message

            #use CreateDirectory instead of New-Item to avoid lines
            # to handle the non-terminating error
            [System.IO.Directory]::CreateDirectory($FullName)
        }

        if(Test-Path -path $this.Path -PathType Container)
        {
            throw "Path '$this.Path' is a directory path"
        }

        Write-Verbose -Message "Copying $this.SourcePath to $this.Path"

        #DSC engine catches and reports any error that occurs
        Copy-Item -Path $this.SourcePath -Destination $this.Path -Force
    }
}
```

## <a name="create-a-module-manifest"></a>모듈 매니페스트 만들기

클래스 정의 DSC 리소스 공급자를 만들고 모듈로 저장한 후 모듈에 대한 모듈 매니페스트를 만듭니다. DSC 엔진에 사용할 수 있는 클래스 기반 리소스를 만들려면 매니페스트 파일에 리소스를 내보내도록 모듈에게 지시하는 `DscResourcesToExport` 문을 포함해야 합니다. 이 예제에서는 다음 모듈 매니페스트가 MyDscResource.psd1로 저장됩니다.

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

## <a name="deploy-a-dsc-resource-provider"></a>DSC 리소스 공급자 배포

또는에서 Mydscresource.psd1 폴더를 만들어 새 DSC 리소스 공급자를 배포 `$pshome\Modules` 합니다 `$env:SystemDrive\ProgramFiles\WindowsPowerShell\Modules` .

DSCResource 하위 폴더는 만들 필요가 없습니다. 모듈 및 모듈 매니페스트 파일(MyDscResource.psm1 및 MyDscResource.psd1)을 MyDscResource 폴더에 복사합니다.

이 시점에서 DSC 리소스와 마찬가지로 구성 스크립트를 만들어 실행합니다.

## <a name="create-a-dsc-configuration-script"></a>DSC 구성 스크립트 만들기

앞에서 설명한 대로 폴더 구조에 클래스 및 매니페스트 파일을 저장한 후에는 새 리소스를 사용하는 구성을 만들 수 있습니다. 다음 구성에서는 Mydscresource.psd1 모듈을 참조 합니다. 구성을 MyResource.ps1 스크립트로 저장 합니다.

DSC 구성을 실행 하는 방법에 대 한 자세한 내용은 [Windows PowerShell 필요한 상태 구성 개요](/powershell/scripting/dsc/overview/dscforengineers)를 참조 하세요.

구성을 실행 하기 전에를 만듭니다 `C:\test.txt` . 구성에서는 파일이에 있는지 확인 `c:\test\test.txt` 합니다. 파일이 없는 경우 구성은에서 파일을 복사 합니다 `C:\test.txt` .

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

DSC 구성 스크립트와 마찬가지로이 스크립트를 실행 합니다. 구성을 시작 하려면 관리자 권한 PowerShell 콘솔에서 다음을 실행 합니다.

`PS C:\test> .\MyResource.ps1`

## <a name="inheritance-in-powershell-classes"></a>PowerShell 클래스의 상속

### <a name="declare-base-classes-for-powershell-classes"></a>PowerShell 클래스에 대 한 기본 클래스 선언

다음 예제와 같이 PowerShell 클래스를 다른 PowerShell 클래스의 기본 형식으로 선언할 수 있습니다. 여기서 **과일** 은 **apple** 의 기본 형식입니다.

```powershell
class fruit
{
    [int]sold() {return 100500}
}

class apple : fruit {}
    [apple]::new().sold() # return 100500
```

### <a name="declare-implemented-interfaces-for-powershell-classes"></a>PowerShell 클래스에 대해 구현 된 인터페이스 선언

구현 된 인터페이스는 기본 형식 뒤에 선언 하거나, `:` 지정 된 기본 형식이 없는 경우 콜론 () 바로 다음에 선언할 수 있습니다. 쉼표를 사용하여 모든 형식 이름을 구분합니다. 이는 c # 구문과 유사 합니다.

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

### <a name="call-base-class-constructors"></a>기본 클래스 생성자 호출

서브 클래스에서 기본 클래스 생성자를 호출 하려면 `base` 다음 예제와 같이 키워드를 추가 합니다.

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

기본 클래스에 기본 생성자 (매개 변수 없음)가 있는 경우 다음과 같이 명시적 생성자 호출을 생략할 수 있습니다.

```powershell
class C : B
{
    C([int]$c) {}
}
```

### <a name="call-base-class-methods"></a>기본 클래스 메서드 호출

하위 클래스에서 기존 메서드를 재정의할 수 있습니다. 재정의를 수행 하려면 동일한 이름과 서명을 사용 하 여 메서드를 선언 합니다.

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

재정의 된 구현에서 기본 클래스 메서드를 호출 하려면 호출 시 기본 클래스로 캐스팅 `([baseclass]$this)` 합니다.

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

모든 PowerShell 메서드는 가상입니다. 재정의할 때와 동일한 구문을 사용 하 여 하위 클래스에서 비가상 .NET 메서드를 숨길 수 있습니다. 동일한 이름 및 서명을 사용 하 여 메서드를 선언 합니다.

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

### <a name="current-limitations-with-class-inheritance"></a>클래스 상속의 현재 제한 사항

클래스 상속의 제한 사항은 PowerShell에서 인터페이스를 선언 하는 구문이 없다는 것입니다.

## <a name="defining-custom-types-in-powershell"></a>PowerShell에서 사용자 지정 형식 정의

Windows PowerShell 5.0에서는 몇 가지 언어 요소를 소개 했습니다.

### <a name="class-keyword"></a>Class 키워드

새 클래스를 정의 합니다.
`class`키워드는 true .NET Framework 형식입니다.
클래스 멤버는 공용입니다.

```powershell
class MyClass
{
}
```

### <a name="enum-keyword-and-enumerations"></a>Enum 키워드 및 열거형

키워드에 대 한 지원이 `enum` 추가 되었으며 주요 변경 사항입니다. `enum`구분 기호는 현재 줄 바꿈입니다. 이미를 사용 하 고 있는 사용자에 대 한 해결 방법은 `enum` 단어 앞에 앰퍼샌드 ()를 삽입 하는 것입니다 `&` . 현재 제한 사항: `enum` 다음 예제와 같이 열거자 자체를 기준으로 열거자를 정의할 수 없지만 다른 방식으로 초기화할 수 있습니다 `enum` .

현재 기본 유형을 지정할 수 없습니다. 기본 형식은 항상 [int]입니다.

```powershell
enum Color2
{
    Yellow = [Color]::Blue
}
```

열거자 값은 구문 분석 시간 상수여야 합니다. 열거자 값은 호출 된 명령의 결과로 설정할 수 없습니다.

```powershell
enum MyEnum
{
    Enum1
    Enum2
    Enum3 = 42
    Enum4 = [int]::MaxValue
}
```

`Enum` 에서는 다음 예제와 같이 산술 연산을 지원 합니다.

```powershell
enum SomeEnum { Max = 42 }
enum OtherEnum { Max = [SomeEnum]::Max + 1 }
```

### <a name="hidden-keyword"></a>Hidden 키워드

`hidden`Windows PowerShell 5.0에 도입 된 키워드는 기본 결과에서 클래스 멤버를 숨깁니다 `Get-Member` . 다음 줄과 같이 hidden 속성을 지정 합니다.

```powershell
hidden [type] $classmember = <value>
```

숨겨진 멤버를 정의 하는 클래스에서 완료가 발생 하지 않은 경우에는 탭 완성 또는 IntelliSense를 사용 하 여 숨겨진 멤버를 표시 하지 않습니다.

새 특성인 **system.management.automation.hiddenattribute** 가 추가 되어 c # 코드가 PowerShell 내에서 동일한 의미 체계를 가질 수 있습니다.

자세한 내용은 [about_Hidden](../../Microsoft.PowerShell.Core/About/about_hidden.md)를 참조 하세요.

### <a name="import-dscresource"></a>Import-DscResource

`Import-DscResource`는 이제 진정한 동적 키워드입니다. PowerShell은 지정된 모듈의 루트 모듈을 구문 분석하여 DscResource 특성이 포함된 클래스를 검색합니다.

### <a name="properties"></a>속성

새 필드인가 `ImplementingAssembly` 에 추가 되었습니다 `ModuleInfo` . 스크립트가 클래스를 정의 하거나 이진 모듈에 대해 로드 된 어셈블리가 `ImplementingAssembly` 스크립트 모듈에 대해 만들어진 동적 어셈블리로 설정 된 경우 ModuleType = Manifest인 경우에는 설정되지 않습니다.

필드에 대 한 리플렉션은 `ImplementingAssembly` 모듈에서 리소스를 검색 합니다. 즉, PowerShell이나 다른 관리 언어로 작성된 리소스를 검색할 수 있습니다.

이니셜라이저가 있는 필드

`[int] $i = 5`

Static은 지원 되며 형식 제약 조건과 유사한 특성 처럼 작동 하므로 순서에 관계 없이 지정할 수 있습니다.

`static [int] $count = 0`

형식은 선택 사항입니다.

`$s = "hello"`

모든 멤버는 공용입니다. 속성에는 줄 바꿈이나 세미콜론이 필요합니다. 개체 형식이 지정 되지 않은 경우 속성 형식은 **object** 입니다.

### <a name="constructors-and-instantiation"></a>생성자 및 인스턴스화

PowerShell 클래스에는 클래스와 이름이 같은 생성자가 있을 수 있습니다. 생성자는 오버로드할 수 있습니다. 정적 생성자가 지원됩니다.
초기화 식이 있는 속성은 생성자에서 코드를 실행하기 전에 초기화됩니다. 정적 속성은 정적 생성자의 본문보다 먼저 초기화되고, 인스턴스 속성은 비정적 생성자의 본문보다 먼저 초기화됩니다. 현재는 c # 구문과 같은 다른 생성자에서 생성자를 호출 하기 위한 구문이 `": this()")` 없습니다. 해결 방법은 일반적인 Init 메서드를 정의하는 것입니다.

다음은 클래스를 인스턴스화하는 방법입니다.

- 기본 생성자를 사용하여 인스턴스화합니다. 는 `New-Object` 이 릴리스에서 지원 되지 않습니다.

  `$a = [MyClass]::new()`

- 매개 변수를 사용 하 여 생성자를 호출 합니다.

  `$b = [MyClass]::new(42)`

- 매개 변수가 여러 개인 생성자에 배열을 전달합니다.

  `$c = [MyClass]::new(@(42,43,44), "Hello")`

이 릴리스의 경우 형식 이름이 어휘 적 으로만 표시 됩니다. 즉, 클래스를 정의 하는 모듈이 나 스크립트 외부에는 표시 되지 않습니다. 함수는 PowerShell에 정의 된 클래스의 인스턴스를 반환할 수 있으며 인스턴스는 모듈 또는 스크립트 외부에서 잘 작동 합니다.

`Get-Member` **정적** 매개 변수는 생성자를 나열 하므로 다른 모든 메서드와 마찬가지로 오버 로드를 볼 수 있습니다. 이 구문의 성능 또한 `New-Object`보다 현저하게 빠릅니다.

**new** 라는 의사 정적 메서드는 다음 예제와 같이 .NET 형식에서 작동합니다. `[hashtable]::new()`

이제 `Get-Member`를 사용하거나 다음 예제와 같이 생성자 오버로드를 확인할 수 있습니다.

```powershell
[hashtable]::new
OverloadDefinitions
-------------------
hashtable new()
hashtable new(int capacity)
hashtable new(int capacity, float loadFactor)
```

### <a name="methods"></a>메서드

PowerShell 클래스 메서드는 끝 블록만 있는 **ScriptBlock** 으로 구현됩니다. 모든 메서드는 공용입니다. 다음에서는 **DoSomething** 이라는 메서드를 정의하는 예제를 보여 줍니다.

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

### <a name="method-invocation"></a>메서드 호출

오버 로드 된 메서드가 지원 됩니다. 오버 로드 된 메서드는 기존 메서드와 동일 하 게 이름이 지정 되지만 지정 된 값으로 구별 됩니다.

```powershell
$b = [MyClass]::new()
$b.DoSomething(42)
```

### <a name="invocation"></a>호출

[메서드 호출](#method-invocation)을 참조 하세요.

### <a name="attributes"></a>특성

`DscResource`, 및의 세 가지 새 특성이 추가 되었습니다. `DscResourceKey` `DscResourceMandatory`

### <a name="return-types"></a>반환 형식

반환 형식은 계약입니다. 반환 값은 필요한 형식으로 변환됩니다.
반환 형식이 지정되지 않은 경우 반환 형식은 void입니다. 개체 및 개체의 스트리밍은 의도적으로 또는 실수로 파이프라인에 쓸 수 없습니다.

### <a name="lexical-scoping-of-variables"></a>변수의 어휘 범위 지정

다음에서는 이 릴리스에서 어휘 범위 지정이 작동하는 방식에 대한 예를 보여 줍니다.

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

## <a name="example-create-custom-classes"></a>예: 사용자 지정 클래스 만들기

다음 예제에서는 여러 가지 새로운 사용자 지정 클래스를 만들어 HTML DSL (동적 스타일 시트 언어)을 구현 합니다. 이 예제에서는 모듈의 범위 외부에서 형식을 사용할 수 없기 때문에 도우미 함수를 추가 하 여 요소 클래스의 일부로 제목 스타일 및 표와 같은 특정 요소 형식을 만듭니다.

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

## <a name="see-also"></a>참고 항목

[about_Enum](../../Microsoft.PowerShell.Core/About/about_Enum.md)

[about_Hidden](../../Microsoft.PowerShell.Core/About/about_hidden.md)

[about_Language_Keywords](../../Microsoft.PowerShell.Core/About/about_Language_Keywords.md)

[about_Methods](../../Microsoft.PowerShell.Core/About/about_Methods.md)

[사용자 지정 PowerShell 필요한 상태 구성 리소스 빌드](/powershell/scripting/dsc/resources/authoringResource)
