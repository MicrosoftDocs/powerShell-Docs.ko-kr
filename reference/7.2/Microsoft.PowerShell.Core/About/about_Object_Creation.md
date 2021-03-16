---
description: PowerShell에서 개체를 만드는 방법을 설명 합니다.
Locale: en-US
ms.date: 09/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_object_creation?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Object_Creation
ms.openlocfilehash: 72c0d763fe7f3838c8b2ca68930521e24d0e6139
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99601864"
---
# <a name="about-object-creation"></a><span data-ttu-id="997a5-103">개체 만들기 정보</span><span class="sxs-lookup"><span data-stu-id="997a5-103">About Object Creation</span></span>

## <a name="short-description"></a><span data-ttu-id="997a5-104">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="997a5-104">Short description</span></span>

<span data-ttu-id="997a5-105">PowerShell에서 개체를 만드는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="997a5-105">Explains how to create objects in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="997a5-106">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="997a5-106">Long description</span></span>

<span data-ttu-id="997a5-107">PowerShell에서 개체를 만들고 명령 및 스크립트에서 만든 개체를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="997a5-107">You can create objects in PowerShell and use the objects that you create in commands and scripts.</span></span>

<span data-ttu-id="997a5-108">여러 가지 방법으로 개체를 만들 수 있으며,이 목록은 명확 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="997a5-108">There are many ways to create objects, this list is not definitive:</span></span>

- <span data-ttu-id="997a5-109">[새 개체](xref:Microsoft.PowerShell.Utility.New-Object): .NET Framework 개체 또는 COM 개체의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="997a5-109">[New-Object](xref:Microsoft.PowerShell.Utility.New-Object): Creates an instance of a .NET Framework object or COM object.</span></span>
- <span data-ttu-id="997a5-110">[가져오기-Csv](xref:Microsoft.PowerShell.Utility.Import-Csv) /
   [Convertfrom-csv](xref:Microsoft.PowerShell.Utility.ConvertFrom-Csv): 쉼표로 구분 된 값으로 정의 된 항목에서 사용자 지정 개체 (**PSCustomObject**)를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="997a5-110">[Import-Csv](xref:Microsoft.PowerShell.Utility.Import-Csv)/
  [ConvertFrom-CSV](xref:Microsoft.PowerShell.Utility.ConvertFrom-Csv): Creates custom objects (**PSCustomObject**) from the items defined as comma separated values.</span></span>
- <span data-ttu-id="997a5-111">[Convertfrom-csv](xref:Microsoft.PowerShell.Utility.ConvertFrom-Json): JAVASCRIPT OBJECT NOTATION (json)에 정의 된 사용자 지정 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="997a5-111">[ConvertFrom-Json](xref:Microsoft.PowerShell.Utility.ConvertFrom-Json): Creates custom objects defined in JavaScript Object Notation (JSON).</span></span>
- <span data-ttu-id="997a5-112">[Convertfrom-csv-StringData](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData): 키 값 쌍으로 정의 된 사용자 지정 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="997a5-112">[ConvertFrom-StringData](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData): Creates custom objects defined as key value pairs.</span></span>
- <span data-ttu-id="997a5-113">[추가-형식](xref:Microsoft.PowerShell.Utility.Add-Type):를 사용 하 여 인스턴스화할 수 있는 클래스를 PowerShell 세션에서 정의할 수 있습니다 `New-Object` .</span><span class="sxs-lookup"><span data-stu-id="997a5-113">[Add-Type](xref:Microsoft.PowerShell.Utility.Add-Type): Allows you to define a class in your PowerShell session that you can instantiate with `New-Object`.</span></span>
- <span data-ttu-id="997a5-114">**AsCustomObject** :이 매개 변수는 스크립트 블록을 사용 하 여 정의 하는 사용자 지정 개체를 [만듭니다.](xref:Microsoft.PowerShell.Core.New-Module)</span><span class="sxs-lookup"><span data-stu-id="997a5-114">[New-Module](xref:Microsoft.PowerShell.Core.New-Module): The **AsCustomObject** parameter creates a custom object you define using script block.</span></span>
- <span data-ttu-id="997a5-115">[멤버 추가](xref:Microsoft.PowerShell.Utility.Add-Member): 기존 개체에 속성을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="997a5-115">[Add-Member](xref:Microsoft.PowerShell.Utility.Add-Member): Adds properties to existing objects.</span></span> <span data-ttu-id="997a5-116">`Add-Member`를 사용 하 여와 같은 단순 형식에서 사용자 지정 개체를 만들 수 있습니다 `[System.Int32]` .</span><span class="sxs-lookup"><span data-stu-id="997a5-116">You can use `Add-Member` to create a custom object out of a simple type, like `[System.Int32]`.</span></span>
- <span data-ttu-id="997a5-117">[Select-object](xref:Microsoft.PowerShell.Utility.Select-Object): 개체의 속성을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="997a5-117">[Select-Object](xref:Microsoft.PowerShell.Utility.Select-Object): Selects properties on an object.</span></span> <span data-ttu-id="997a5-118">`Select-Object`를 사용 하 여 이미 인스턴스화된 개체에서 사용자 지정 및 계산 된 속성을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="997a5-118">You can use `Select-Object` to create custom and calculated properties on an already instantiated object.</span></span>

<span data-ttu-id="997a5-119">이 문서에서는 다음과 같은 추가 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="997a5-119">The following additional methods are covered in this article:</span></span>

- <span data-ttu-id="997a5-120">정적 메서드를 사용 하 여 형식의 생성자 호출 `new()`</span><span class="sxs-lookup"><span data-stu-id="997a5-120">By calling a type's constructor using a static `new()` method</span></span>
- <span data-ttu-id="997a5-121">Typecasting 속성 이름 및 속성 값의 해시 테이블</span><span class="sxs-lookup"><span data-stu-id="997a5-121">By typecasting hash tables of property names and property values</span></span>

## <a name="static-new-method"></a><span data-ttu-id="997a5-122">Static new () 메서드</span><span class="sxs-lookup"><span data-stu-id="997a5-122">Static new() method</span></span>

<span data-ttu-id="997a5-123">모든 .NET 형식에는 `new()` 인스턴스를 보다 쉽게 구성할 수 있는 메서드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="997a5-123">All .NET types have a `new()` method that allows you to construct instances more easily.</span></span> <span data-ttu-id="997a5-124">지정 된 형식에 대해 사용 가능한 생성자를 모두 볼 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="997a5-124">You can also see all the available constructors for a given type.</span></span>

<span data-ttu-id="997a5-125">형식에 대 한 생성자를 보려면 `new` 형식 이름 다음에 메서드 이름을 지정 하 고 키를 누릅니다 `<ENTER>` .</span><span class="sxs-lookup"><span data-stu-id="997a5-125">To see the constructors for a type, specify the `new` method name after the type name and press `<ENTER>`.</span></span>

```powershell
[System.Uri]::new
```

```Output
OverloadDefinitions
-------------------
uri new(string uriString)
uri new(string uriString, bool dontEscape)
uri new(uri baseUri, string relativeUri, bool dontEscape)
uri new(string uriString, System.UriKind uriKind)
uri new(uri baseUri, string relativeUri)
uri new(uri baseUri, uri relativeUri)
```

<span data-ttu-id="997a5-126">이제 적절 한 생성자를 지정 하 여 **system.uri** 를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="997a5-126">Now, you can create a **System.Uri** by specifying the appropriate constructor.</span></span>

```powershell
[System.Uri]::new("https://www.bing.com")
```

```Output
AbsolutePath   : /
AbsoluteUri    : https://www.bing.com/
LocalPath      : /
Authority      : www.bing.com
...
```

<span data-ttu-id="997a5-127">다음 샘플을 사용 하 여 현재 인스턴스화할 수 있도록 로드 된 .NET 형식을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="997a5-127">You can use the following sample to determine what .NET types are currently loaded for you to instantiate.</span></span>

```powershell
[AppDomain]::CurrentDomain.GetAssemblies() |
  ForEach-Object {
    $_.GetExportedTypes() |
      ForEach-Object { $_.FullName }
  }
```

<span data-ttu-id="997a5-128">메서드를 사용 하 여 만든 개체는 `new()` PowerShell cmdlet에 의해 생성 된 것과 동일한 형식의 개체와 동일한 속성을 가질 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="997a5-128">Objects created using the `new()` method may not have the same properties as objects of the same type that are created by PowerShell cmdlets.</span></span> <span data-ttu-id="997a5-129">PowerShell cmdlet, 공급자 및 확장 유형 시스템은 인스턴스에 추가 속성을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="997a5-129">PowerShell cmdlets, providers, and Extended Type System can add extra properties to the instance.</span></span>

<span data-ttu-id="997a5-130">예를 들어 PowerShell의 FileSystem 공급자는에서 반환 된 **system.io.directoryinfo** 개체에 6 개의 **참고 속성** 값을 추가 `Get-Item` 합니다.</span><span class="sxs-lookup"><span data-stu-id="997a5-130">For example, the FileSystem provider in PowerShell adds six **NoteProperty** values to the **DirectoryInfo** object returned by `Get-Item`.</span></span>

```powershell
$PSDirInfo = Get-Item /
$PSDirInfo | Get-Member | Group-Object MemberType | Select-Object Count, Name
```

```Output
Count Name
----- ----
    4 CodeProperty
   13 Property
    6 NoteProperty
    1 ScriptProperty
   18 Method
```

<span data-ttu-id="997a5-131">**System.io.directoryinfo** 개체를 직접 만드는 경우에는 이러한 6 개의 **참고 속성** 값이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="997a5-131">When you create a **DirectoryInfo** object directly, it does not have those six **NoteProperty** values.</span></span>

```powershell
$NewDirInfo = [System.IO.DirectoryInfo]::new('/')
$NewDirInfo | Get-Member | Group-Object MemberType | Select-Object Count, Name
```

```Output
Count Name
----- ----
    4 CodeProperty
   13 Property
    1 ScriptProperty
   18 Method
```

<span data-ttu-id="997a5-132">확장 유형 시스템에 대 한 자세한 내용은 [about_Types.ps1xml](about_Types.ps1xml.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="997a5-132">For more information about the Extended Type System, see [about_Types.ps1xml](about_Types.ps1xml.md).</span></span>

<span data-ttu-id="997a5-133">이 기능은 PowerShell 5.0에 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="997a5-133">This feature was added in PowerShell 5.0</span></span>

## <a name="create-objects-from-hash-tables"></a><span data-ttu-id="997a5-134">해시 테이블에서 개체 만들기</span><span class="sxs-lookup"><span data-stu-id="997a5-134">Create objects from hash tables</span></span>

<span data-ttu-id="997a5-135">속성 및 속성 값의 해시 테이블에서 개체를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="997a5-135">You can create an object from a hash table of properties and property values.</span></span>

<span data-ttu-id="997a5-136">구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="997a5-136">The syntax is as follows:</span></span>

```
[<class-name>]@{
  <property-name>=<property-value>
  <property-name>=<property-value>
}
```

<span data-ttu-id="997a5-137">이 메서드는 매개 변수가 없는 생성자가 있는 클래스에 대해서만 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="997a5-137">This method works only for classes that have a parameterless constructor.</span></span> <span data-ttu-id="997a5-138">개체 속성은 public 이어야 하며 설정 가능 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="997a5-138">The object properties must be public and settable.</span></span>

<span data-ttu-id="997a5-139">이 기능은 PowerShell 버전 3.0에 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="997a5-139">This feature was added in PowerShell version 3.0</span></span>

## <a name="create-custom-objects-from-hash-tables"></a><span data-ttu-id="997a5-140">해시 테이블에서 사용자 지정 개체 만들기</span><span class="sxs-lookup"><span data-stu-id="997a5-140">Create custom objects from hash tables</span></span>

<span data-ttu-id="997a5-141">사용자 지정 개체는 매우 유용 하며 해시 테이블 메서드를 사용 하 여 쉽게 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="997a5-141">Custom objects are very useful and are easy to create using the hash table method.</span></span> <span data-ttu-id="997a5-142">**PSCustomObject** 클래스는이 목적을 위해 특별히 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="997a5-142">The **PSCustomObject** class is designed specifically for this purpose.</span></span>

<span data-ttu-id="997a5-143">사용자 지정 개체는 함수 또는 스크립트에서 사용자 지정 된 출력을 반환 하는 좋은 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="997a5-143">Custom objects are an excellent way to return customized output from a function or script.</span></span> <span data-ttu-id="997a5-144">이는 다른 명령으로 다시 포맷 하거나 파이프 할 수 없는 형식이 지정 된 출력을 반환 하는 것 보다 더 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="997a5-144">This is more useful than returning formatted output that cannot be reformatted or piped to other commands.</span></span>

<span data-ttu-id="997a5-145">의 명령은 `Test-Object function` 일부 변수 값을 설정 하 고 해당 값을 사용 하 여 사용자 지정 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="997a5-145">The commands in the `Test-Object function` set some variable values and then use those values to create a custom object.</span></span> <span data-ttu-id="997a5-146">Cmdlet 도움말 항목의 예제 섹션에서 사용 중이 개체를 볼 수 있습니다 `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="997a5-146">You can see this object in use in the example section of the `Update-Help` cmdlet help topic.</span></span>

```powershell
function Test-Object {
  $ModuleName = "PSScheduledJob"
  $HelpCulture = "en-us"
  $HelpVersion = "3.1.0.0"
  [PSCustomObject]@{
    "ModuleName"=$ModuleName
    "UICulture"=$HelpCulture
    "Version"=$HelpVersion
  }
  $ModuleName = "PSWorkflow"
  $HelpCulture = "en-us"
  $HelpVersion = "3.0.0.0"
  [PSCustomObject]@{
    "ModuleName"=$ModuleName
    "UICulture"=$HelpCulture
    "Version"=$HelpVersion
  }
}
Test-Object
```

<span data-ttu-id="997a5-147">이 함수의 출력은 기본적으로 테이블로 형식이 지정 된 사용자 지정 개체의 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="997a5-147">The output of this function is a collection of custom objects formatted as a table by default.</span></span>

```Output
ModuleName        UICulture      Version
---------         ---------      -------
PSScheduledJob    en-us          3.1.0.0
PSWorkflow        en-us          3.0.0.0
```

<span data-ttu-id="997a5-148">사용자는 표준 개체와 동일한 방식으로 사용자 지정 개체의 속성을 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="997a5-148">Users can manage the properties of the custom objects just as they do with standard objects.</span></span>

```powershell
(Test-Object).ModuleName
```

```Output
 PSScheduledJob
 PSWorkflow
```

## <a name="create-non-custom-objects-from-hash-tables"></a><span data-ttu-id="997a5-149">해시 테이블에서 사용자 지정 되지 않은 개체 만들기</span><span class="sxs-lookup"><span data-stu-id="997a5-149">Create non-custom objects from hash tables</span></span>

<span data-ttu-id="997a5-150">해시 테이블을 사용 하 여 사용자 지정 클래스가 아닌 클래스에 대 한 개체를 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="997a5-150">You can also use hash tables to create objects for non-custom classes.</span></span> <span data-ttu-id="997a5-151">사용자 지정 클래스가 아닌 클래스에 대 한 개체를 만드는 경우 초기 **시스템** 네임 스페이스 구성 요소를 생략할 수 있지만 네임 스페이스로 한정 된 형식 이름이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="997a5-151">When you create an object for a non-custom class, the namespace-qualified type name is required, although you may omit any initial **System** namespace component.</span></span>

<span data-ttu-id="997a5-152">예를 들어 다음 명령은 세션 옵션 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="997a5-152">For example, the following command creates a session option object.</span></span>

```powershell
[System.Management.Automation.Remoting.PSSessionOption]@{
  IdleTimeout=43200000
  SkipCnCheck=$True
}
```

<span data-ttu-id="997a5-153">해시 테이블 기능의 요구 사항, 특히 매개 변수가 없는 생성자 요구 사항으로 인해 기존 클래스가 많이 제거 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="997a5-153">The requirements of the hash table feature, especially the parameterless constructor requirement, eliminate many existing classes.</span></span> <span data-ttu-id="997a5-154">그러나 대부분의 PowerShell _옵션_ 클래스는이 기능과 **ProcessStartInfo** 클래스와 같은 매우 유용한 기타 클래스와 함께 작동 하도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="997a5-154">However, most PowerShell _option_ classes are designed to work with this feature, as well as other very useful classes, such as the **ProcessStartInfo** class.</span></span>

```powershell
[System.Diagnostics.ProcessStartInfo]@{
  CreateNoWindow="$true"
  Verb="run as"
}
```

```Output
Arguments               :
ArgumentList            : {}
CreateNoWindow          : True
EnvironmentVariables    : {OneDriveConsumer, PROCESSOR_ARCHITECTURE,
                           CommonProgramFiles(x86), APPDATA...}
Environment             : {[OneDriveConsumer, C:\Users\user1\OneDrive],
                           [PROCESSOR_ARCHITECTURE, AMD64],
                           [CommonProgramFiles(x86),
                           C:\Program Files (x86)\Common Files],
                           [APPDATA, C:\Users\user1\AppData\Roaming]...}
RedirectStandardInput   : False
RedirectStandardOutput  : False
RedirectStandardError   : False
...
```

<span data-ttu-id="997a5-155">매개 변수 값을 설정할 때 해시 테이블 기능을 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="997a5-155">You can also use the hash table feature when setting parameter values.</span></span> <span data-ttu-id="997a5-156">예를 들어의 **Sessionoption** 매개 변수 값입니다 `New-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="997a5-156">For example, the value of the **SessionOption** parameter of the `New-PSSession`.</span></span>
<span data-ttu-id="997a5-157">cmdlet은 해시 테이블 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="997a5-157">cmdlet can be a hash table.</span></span>

```powershell
New-PSSession -ComputerName Server01 -SessionOption @{
  IdleTimeout=43200000
  SkipCnCheck=$True
}
Register-ScheduledJob Name Test -FilePath .\Get-Inventory.ps1 -Trigger @{
  Frequency="Daily"
  At="15:00"
}
```

## <a name="generic-objects"></a><span data-ttu-id="997a5-158">제네릭 개체</span><span class="sxs-lookup"><span data-stu-id="997a5-158">Generic objects</span></span>

<span data-ttu-id="997a5-159">PowerShell에서 제네릭 개체를 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="997a5-159">You can also create generic objects in PowerShell.</span></span> <span data-ttu-id="997a5-160">제네릭은 저장하거나 사용하는 하나 이상의 형식에 대한 자리 표시자(형식 매개 변수)를 포함하는 클래스, 구조체, 인터페이스 및 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="997a5-160">Generics are classes, structures, interfaces, and methods that have placeholders (type parameters) for one or more of the types that they store or use.</span></span>

<span data-ttu-id="997a5-161">다음 예제에서는 **사전** 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="997a5-161">The following example creates a **Dictionary** object.</span></span>

```powershell
$dict = New-Object 'System.Collections.Generic.Dictionary[String,Int]'
$dict.Add("One", 1)
$dict
```

```Output
Key Value
--- -----
One     1
```

<span data-ttu-id="997a5-162">제네릭에 대 한 자세한 내용은 [.net의 제네릭](/dotnet/standard/generics)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="997a5-162">For more information on Generics, see [Generics in .NET](/dotnet/standard/generics).</span></span>

## <a name="see-also"></a><span data-ttu-id="997a5-163">참고 항목</span><span class="sxs-lookup"><span data-stu-id="997a5-163">See also</span></span>

[<span data-ttu-id="997a5-164">about_Objects</span><span class="sxs-lookup"><span data-stu-id="997a5-164">about_Objects</span></span>](about_Objects.md)

[<span data-ttu-id="997a5-165">about_Methods</span><span class="sxs-lookup"><span data-stu-id="997a5-165">about_Methods</span></span>](about_Methods.md)

[<span data-ttu-id="997a5-166">about_Properties</span><span class="sxs-lookup"><span data-stu-id="997a5-166">about_Properties</span></span>](about_Properties.md)

[<span data-ttu-id="997a5-167">about_Pipelines</span><span class="sxs-lookup"><span data-stu-id="997a5-167">about_Pipelines</span></span>](about_Pipelines.md)

[<span data-ttu-id="997a5-168">about_Types.ps1xml</span><span class="sxs-lookup"><span data-stu-id="997a5-168">about_Types.ps1xml</span></span>](about_Types.ps1xml.md)