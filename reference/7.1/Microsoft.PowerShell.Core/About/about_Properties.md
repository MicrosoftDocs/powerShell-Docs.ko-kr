---
description: PowerShell에서 개체 속성을 사용 하는 방법을 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 12/01/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_properties?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Properties
ms.openlocfilehash: d4d3cd93e6b177e80d85315f125c647219fc4a45
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93224034"
---
# <a name="about-properties"></a><span data-ttu-id="3c14b-104">속성 정보</span><span class="sxs-lookup"><span data-stu-id="3c14b-104">About Properties</span></span>

## <a name="short-description"></a><span data-ttu-id="3c14b-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="3c14b-105">Short description</span></span>
<span data-ttu-id="3c14b-106">PowerShell에서 개체 속성을 사용 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c14b-106">Describes how to use object properties in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="3c14b-107">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="3c14b-107">Long description</span></span>

<span data-ttu-id="3c14b-108">PowerShell은 개체 라고 하는 구조화 된 정보 컬렉션을 사용 하 여 데이터 저장소의 항목 또는 컴퓨터의 상태를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3c14b-108">PowerShell uses structured collections of information called objects to represent the items in data stores or the state of the computer.</span></span> <span data-ttu-id="3c14b-109">일반적으로 Microsoft .NET 프레임 워크의 일부인 개체로 작업 하지만 PowerShell에서 사용자 지정 개체를 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c14b-109">Typically, you work with object that are part of the Microsoft .NET Framework, but you can also create custom objects in PowerShell.</span></span>

<span data-ttu-id="3c14b-110">항목과 해당 개체 간의 연결이 매우 가깝습니다.</span><span class="sxs-lookup"><span data-stu-id="3c14b-110">The association between an item and its object is very close.</span></span> <span data-ttu-id="3c14b-111">개체를 변경 하는 경우 일반적으로 해당 개체를 나타내는 항목이 변경 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c14b-111">When you change an object, you usually change the item that it represents.</span></span> <span data-ttu-id="3c14b-112">예를 들어 PowerShell에서 파일을 가져올 때 실제 파일을 가져오지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3c14b-112">For example, when you get a file in PowerShell, you do not get the actual file.</span></span> <span data-ttu-id="3c14b-113">대신 파일을 나타내는 FileInfo 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3c14b-113">Instead, you get a FileInfo object that represents the file.</span></span> <span data-ttu-id="3c14b-114">FileInfo 개체를 변경 하면 파일도 변경 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c14b-114">When you change the FileInfo object, the file changes too.</span></span>

<span data-ttu-id="3c14b-115">대부분의 개체에는 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c14b-115">Most objects have properties.</span></span> <span data-ttu-id="3c14b-116">속성은 개체에 연결 된 데이터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c14b-116">Properties are the data that is associated with an object.</span></span> <span data-ttu-id="3c14b-117">개체 유형에 따라 속성이 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="3c14b-117">Different types of object have different properties.</span></span> <span data-ttu-id="3c14b-118">예를 들어 파일을 나타내는 FileInfo 개체는 파일에 읽기 전용 특성이 있는 경우 $True 포함 된 **IsReadOnly** 속성을 포함 하 고, 그렇지 않은 경우 $False 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c14b-118">For example, a FileInfo object, which represents a file, has an **IsReadOnly** property that contains $True if the file the read-only attribute and $False if it does not.</span></span>
<span data-ttu-id="3c14b-119">파일 시스템 디렉터리를 나타내는 System.io.directoryinfo 개체에는 부모 디렉터리의 경로를 포함 하는 부모 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c14b-119">A DirectoryInfo object, which represents a file system directory, has a Parent property that contains the path to the parent directory.</span></span>

### <a name="object-properties"></a><span data-ttu-id="3c14b-120">개체 속성</span><span class="sxs-lookup"><span data-stu-id="3c14b-120">Object properties</span></span>

<span data-ttu-id="3c14b-121">개체의 속성을 가져오려면 cmdlet을 사용 합니다 `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="3c14b-121">To get the properties of an object, use the `Get-Member` cmdlet.</span></span> <span data-ttu-id="3c14b-122">예를 들어 **fileinfo** 개체의 속성을 가져오려면 cmdlet을 사용 하 여 `Get-ChildItem` 파일을 나타내는 FileInfo 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3c14b-122">For example, to get the properties of a **FileInfo** object, use the `Get-ChildItem` cmdlet to get the FileInfo object that represents a file.</span></span> <span data-ttu-id="3c14b-123">그런 다음 파이프라인 연산자 (&#124;)를 사용 하 여 **FileInfo** 개체를로 보냅니다 `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="3c14b-123">Then, use a pipeline operator (&#124;) to send the **FileInfo** object to `Get-Member`.</span></span> <span data-ttu-id="3c14b-124">다음 명령은 PowerShell.exe 파일을 가져와로 보냅니다 `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="3c14b-124">The following command gets the PowerShell.exe file and sends it to `Get-Member`.</span></span>
<span data-ttu-id="3c14b-125">\$Pshome 자동 변수는 PowerShell 설치 디렉터리의 경로를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c14b-125">The \$Pshome automatic variable contains the path of the PowerShell installation directory.</span></span>

```powershell
Get-ChildItem $pshome\PowerShell.exe | Get-Member
```

<span data-ttu-id="3c14b-126">명령의 출력에는 **FileInfo** 개체의 멤버가 나열 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c14b-126">The output of the command lists the members of the **FileInfo** object.</span></span>
<span data-ttu-id="3c14b-127">멤버에는 속성과 메서드가 모두 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c14b-127">Members include both properties and methods.</span></span> <span data-ttu-id="3c14b-128">PowerShell에서 작업 하는 경우 개체의 모든 멤버에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c14b-128">When you work in PowerShell, you have access to all the members of the objects.</span></span>

<span data-ttu-id="3c14b-129">메서드가 아니라 개체의 속성만 가져오려면 `Get-Member` 다음 예제와 같이 "property" 값을 사용 하 여 cmdlet의 MemberType 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c14b-129">To get only the properties of an object and not the methods, use the MemberType parameter of the `Get-Member` cmdlet with a value of "property", as shown in the following example.</span></span>

```powershell
Get-ChildItem $pshome\PowerShell.exe | Get-Member -MemberType property
```

```Output
TypeName: System.IO.FileInfo

Name              MemberType Definition
----              ---------- ----------
Attributes        Property   System.IO.FileAttributes Attributes {get;set;}
CreationTime      Property   System.DateTime CreationTime {get;set;}
CreationTimeUtc   Property   System.DateTime CreationTimeUtc {get;set;}
Directory         Property   System.IO.DirectoryInfo Directory {get;}
DirectoryName     Property   System.String DirectoryName {get;}
Exists            Property   System.Boolean Exists {get;}
Extension         Property   System.String Extension {get;}
FullName          Property   System.String FullName {get;}
IsReadOnly        Property   System.Boolean IsReadOnly {get;set;}
LastAccessTime    Property   System.DateTime LastAccessTime {get;set;}
LastAccessTimeUtc Property   System.DateTime LastAccessTimeUtc {get;set;}
LastWriteTime     Property   System.DateTime LastWriteTime {get;set;}
LastWriteTimeUtc  Property   System.DateTime LastWriteTimeUtc {get;set;}
Length            Property   System.Int64 Length {get;}
Name              Property   System.String Name {get;}
```

<span data-ttu-id="3c14b-130">속성을 찾은 후 PowerShell 명령에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c14b-130">After you find the properties, you can use them in your PowerShell commands.</span></span>

## <a name="property-values"></a><span data-ttu-id="3c14b-131">속성 값</span><span class="sxs-lookup"><span data-stu-id="3c14b-131">Property values</span></span>

<span data-ttu-id="3c14b-132">특정 형식의 모든 개체에 동일한 속성이 있지만 해당 속성의 값은 특정 개체를 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c14b-132">Although every object of a specific type has the same properties, the values of those properties describe the particular object.</span></span> <span data-ttu-id="3c14b-133">예를 들어 모든 FileInfo 개체에는 CreationTime 속성이 있지만 각 파일에 대해 해당 속성의 값이 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="3c14b-133">For example, every FileInfo object has a CreationTime property, but the value of that property differs for each file.</span></span>

<span data-ttu-id="3c14b-134">개체의 속성 값을 가져오는 가장 일반적인 방법은 점 메서드를 사용 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="3c14b-134">The most common way to get the values of the properties of an object is to use the dot method.</span></span> <span data-ttu-id="3c14b-135">개체를 포함 하는 변수와 같은 개체에 대 한 참조 나 개체를 가져오는 명령을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c14b-135">Type a reference to the object, such as a variable that contains the object, or a command that gets the object.</span></span> <span data-ttu-id="3c14b-136">그런 다음 점 (.)과 속성 이름을 차례로 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c14b-136">Then, type a dot (.) followed by the property name.</span></span>

<span data-ttu-id="3c14b-137">예를 들어 다음 명령은 PowerShell.exe 파일의 CreationTime 속성 값을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c14b-137">For example, the following command displays the value of the CreationTime property of the PowerShell.exe file.</span></span> <span data-ttu-id="3c14b-138">`Get-ChildItem`명령은 PowerShell.exe 파일을 나타내는 FileInfo 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c14b-138">The `Get-ChildItem` command returns a FileInfo object that represents the PowerShell.exe file.</span></span> <span data-ttu-id="3c14b-139">명령은 속성에 액세스 하기 전에 실행 되도록 하기 위해 괄호로 묶여 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c14b-139">The command is enclosed in parentheses to make sure that it is executed before any properties are accessed.</span></span> <span data-ttu-id="3c14b-140">`Get-ChildItem`명령은 다음과 같이 CreationTime 속성의 점과 이름을 차례로 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c14b-140">The `Get-ChildItem` command is followed by a dot and the name of the CreationTime property, as follows:</span></span>

```powershell
(Get-ChildItem $pshome\PowerShell.exe).creationtime
```

```output
Tuesday, March 18, 2008 12:07:52 AM
```

<span data-ttu-id="3c14b-141">다음 예제와 같이 개체를 변수에 저장 한 다음 점 메서드를 사용 하 여 해당 속성을 가져올 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c14b-141">You can also save an object in a variable and then get its properties by using the dot method, as shown in the following example:</span></span>

```powershell
$a = Get-ChildItem $pshome\PowerShell.exe
$a.CreationTime
```

```output
Tuesday, March 18, 2008 12:07:52 AM
```

<span data-ttu-id="3c14b-142">`Select-Object`및 cmdlet을 사용 하 여 `Format-List` 개체의 속성 값을 표시할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c14b-142">You can also use the `Select-Object` and `Format-List` cmdlets to display the property values of an object.</span></span> <span data-ttu-id="3c14b-143">`Select-Object` 및에 `Format-List` 는 각각 **속성** 매개 변수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c14b-143">`Select-Object` and `Format-List` each have a **Property** parameter.</span></span> <span data-ttu-id="3c14b-144">**Property** 매개 변수를 사용 하 여 속성 및 해당 값을 하나 이상 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c14b-144">You can use the **Property** parameter to specify one or more properties and their values.</span></span> <span data-ttu-id="3c14b-145">또는 와일드 카드 문자 ()를 사용 \* 하 여 모든 속성을 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c14b-145">Or, you can use the wildcard character (\*) to represent all the properties.</span></span>

<span data-ttu-id="3c14b-146">예를 들어 다음 명령은 PowerShell.exe 파일의 모든 속성 값을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c14b-146">For example, the following command displays the values of all the properties of the PowerShell.exe file.</span></span>

```powershell
Get-ChildItem $pshome\PowerShell.exe | Format-List -Property *
```

```output
PSPath            : Microsoft.PowerShell.Core\FileSystem::C:\Windows\System3
                    2\WindowsPowerShell\v1.0\PowerShell.exe
PSParentPath      : Microsoft.PowerShell.Core\FileSystem::C:\Windows\System3
                    2\WindowsPowerShell\v1.0
PSChildName       : PowerShell.exe
PSDrive           : C
PSProvider        : Microsoft.PowerShell.Core\FileSystem
PSIsContainer     : False
Mode              : -a----
VersionInfo       : File:             C:\Windows\System32\WindowsPowerShell\
                    v1.0\PowerShell.exe
                    InternalName:     POWERSHELL
                    OriginalFilename: PowerShell.EXE.MUI
                    FileVersion:      10.0.16299.15 (WinBuild.160101.0800)
                    FileDescription:  Windows PowerShell
                    Product:          Microsoft Windows Operating System
                    ProductVersion:   10.0.16299.15
                    Debug:            False
                    Patched:          False
                    PreRelease:       False
                    PrivateBuild:     False
                    SpecialBuild:     False
                    Language:         English (United States)

BaseName          : PowerShell
Target            : {C:\Windows\WinSxS\amd64_microsoft-windows-powershell-ex
                    e_31bf3856ad364e35_10.0.16299.15_none_8c022aa6735716ae\p
                    owershell.exe}
LinkType          : HardLink
Name              : PowerShell.exe
Length            : 449024
DirectoryName     : C:\Windows\System32\WindowsPowerShell\v1.0
Directory         : C:\Windows\System32\WindowsPowerShell\v1.0
IsReadOnly        : False
Exists            : True
FullName          : C:\Windows\System32\WindowsPowerShell\v1.0\PowerShell.ex
Extension         : .exe
CreationTime      : 9/29/2017 6:43:19 AM
CreationTimeUtc   : 9/29/2017 1:43:19 PM
LastAccessTime    : 9/29/2017 6:43:19 AM
LastAccessTimeUtc : 9/29/2017 1:43:19 PM
LastWriteTime     : 9/29/2017 6:43:19 AM
LastWriteTimeUtc  : 9/29/2017 1:43:19 PM
Attributes        : Archive
```

### <a name="static-properties"></a><span data-ttu-id="3c14b-147">정적 속성</span><span class="sxs-lookup"><span data-stu-id="3c14b-147">Static properties</span></span>

<span data-ttu-id="3c14b-148">PowerShell에서 .NET 클래스의 정적 속성을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c14b-148">You can use the static properties of .NET classes in PowerShell.</span></span> <span data-ttu-id="3c14b-149">정적 속성은 개체의 속성인 표준 속성과 달리 클래스의 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="3c14b-149">Static properties are properties of class, unlike standard properties, which are properties of an object.</span></span>

<span data-ttu-id="3c14b-150">클래스의 정적 속성을 가져오려면 Get-Member cmdlet의 Static 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c14b-150">To get the static properties of an class, use the Static parameter of the Get-Member cmdlet.</span></span>

<span data-ttu-id="3c14b-151">예를 들어 다음 명령은 클래스의 정적 속성을 가져옵니다 `System.DateTime` .</span><span class="sxs-lookup"><span data-stu-id="3c14b-151">For example, the following command gets the static properties of the `System.DateTime` class.</span></span>

```powershell
Get-Date | Get-Member -MemberType Property -Static
```

```Output
TypeName: System.DateTime

Name     MemberType Definition
----     ---------- ----------
MaxValue Property   static datetime MaxValue {get;}
MinValue Property   static datetime MinValue {get;}
Now      Property   datetime Now {get;}
Today    Property   datetime Today {get;}
UtcNow   Property   datetime UtcNow {get;}
```

<span data-ttu-id="3c14b-152">정적 속성의 값을 가져오려면 다음 구문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c14b-152">To get the value of a static property, use the following syntax.</span></span>

```
[<ClassName>]::<Property>
```

<span data-ttu-id="3c14b-153">예를 들어 다음 명령은 클래스의 UtcNow static 속성 값을 가져옵니다 `System.DateTime` .</span><span class="sxs-lookup"><span data-stu-id="3c14b-153">For example, the following command gets the value of the UtcNow static property of the `System.DateTime` class.</span></span>

```powershell
[System.DateTime]::UtcNow
```

### <a name="properties-of-scalar-objects-and-collections"></a><span data-ttu-id="3c14b-154">스칼라 개체 및 컬렉션의 속성</span><span class="sxs-lookup"><span data-stu-id="3c14b-154">Properties of scalar objects and collections</span></span>

<span data-ttu-id="3c14b-155">특정 형식의 한 개의 ("스칼라") 개체 속성은 일반적으로 동일한 형식의 개체 컬렉션 속성과는 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="3c14b-155">The properties of one ("scalar") object of a particular type are often different from the properties of a collection of objects of the same type.</span></span>
<span data-ttu-id="3c14b-156">예를 들어 모든 서비스에 **displayname** 속성이 있지만 서비스 컬렉션에 **displayname** 속성이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3c14b-156">For example, every service has as **DisplayName** property, but a collection of services does not have a **DisplayName** property.</span></span>

<span data-ttu-id="3c14b-157">다음 명령은 ' Audiosrv ' 서비스의 **DisplayName** 속성 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3c14b-157">The following command gets the value of the **DisplayName** property of the 'Audiosrv' service.</span></span>

```powershell
(Get-Service Audiosrv).DisplayName
```

```output
Windows Audio
```

<span data-ttu-id="3c14b-158">PowerShell 3.0부터 PowerShell은 스칼라 개체 및 컬렉션의 서로 다른 속성으로 인해 발생 하는 스크립팅 오류를 방지 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c14b-158">Beginning in PowerShell 3.0, PowerShell tries to prevent scripting errors that result from the differing properties of scalar objects and collections.</span></span> <span data-ttu-id="3c14b-159">동일한 명령은를 반환 하는 모든 서비스의 **DisplayName** 속성 값을 반환 합니다 `Get-Service` .</span><span class="sxs-lookup"><span data-stu-id="3c14b-159">The same command returns the value of the **DisplayName** property of every service that `Get-Service` returns.</span></span>

```powershell
(Get-Service).DisplayName
```

```output
Application Experience
Application Layer Gateway Service
Windows All-User Install Agent
Application Identity
Application Information
...
```

<span data-ttu-id="3c14b-160">컬렉션을 제출할 때 단일 ("스칼라") 개체에만 존재 하는 속성을 요청 하는 경우 PowerShell은 컬렉션의 모든 개체에 대해 해당 속성의 값을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c14b-160">When you submit a collection, but request a property that exists only on single ("scalar") objects, PowerShell returns the value of that property for every object in the collection.</span></span>

<span data-ttu-id="3c14b-161">모든 컬렉션에는 컬렉션에 있는 개체 수를 반환 하는 **Count** 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c14b-161">All collections have a **Count** property that returns how many objects are in the collection.</span></span>

```powershell
(Get-Service).Count
```

```output
176
```

<span data-ttu-id="3c14b-162">PowerShell 3.0부터 0 개의 개체나 하나의 개체의 Count 또는 Length 속성을 요청 하는 경우 PowerShell은 올바른 값을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c14b-162">Beginning in PowerShell 3.0, if you request the Count or Length property of zero objects or one object, PowerShell returns the correct value.</span></span>

```powershell
(Get-Service Audiosrv).Count
```

```output
1
```

<span data-ttu-id="3c14b-163">속성이 개별 개체 및 컬렉션에 있으면 컬렉션의 속성만 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c14b-163">If a property exists on the individual objects and on the collection, only the collection's property is returned.</span></span>

 ```powershell
 $collection = @(
 [pscustomobject]@{length = "foo"}
 [pscustomobject]@{length = "bar"}
 )
 # PowerShell returns the collection's Length.
 $collection.length
 ```

 ```output
 2
 ```

<span data-ttu-id="3c14b-164">이 기능은 스칼라 개체 및 컬렉션의 메서드에도 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c14b-164">This feature also works on methods of scalar objects and collections.</span></span> <span data-ttu-id="3c14b-165">자세한 내용은 [about_Methods](about_methods.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3c14b-165">For more information, see [about_Methods](about_methods.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3c14b-166">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3c14b-166">See also</span></span>

[<span data-ttu-id="3c14b-167">about_Methods</span><span class="sxs-lookup"><span data-stu-id="3c14b-167">about_Methods</span></span>](about_Methods.md)

[<span data-ttu-id="3c14b-168">about_Objects</span><span class="sxs-lookup"><span data-stu-id="3c14b-168">about_Objects</span></span>](about_Objects.md)

[<span data-ttu-id="3c14b-169">Get-Member</span><span class="sxs-lookup"><span data-stu-id="3c14b-169">Get-Member</span></span>](xref:Microsoft.PowerShell.Utility.Get-Member)

[<span data-ttu-id="3c14b-170">Select-Object</span><span class="sxs-lookup"><span data-stu-id="3c14b-170">Select-Object</span></span>](xref:Microsoft.PowerShell.Utility.Select-Object)

[<span data-ttu-id="3c14b-171">Format-List</span><span class="sxs-lookup"><span data-stu-id="3c14b-171">Format-List</span></span>](xref:Microsoft.PowerShell.Utility.Format-List)

