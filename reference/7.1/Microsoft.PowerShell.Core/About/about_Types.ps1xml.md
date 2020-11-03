---
description: 파일을 사용 하 여 `Types.ps1xml` PowerShell에서 사용 되는 개체 유형을 확장 하는 방법을 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 04/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_types.ps1xml?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Types.ps1xml
ms.openlocfilehash: 66c319a6f1e84fb2d7aeea60433a2ddea9fb4616
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93222330"
---
# <a name="about-typesps1xml"></a><span data-ttu-id="6c592-104">Types.ps1xml 정보</span><span class="sxs-lookup"><span data-stu-id="6c592-104">About Types.ps1xml</span></span>

## <a name="short-description"></a><span data-ttu-id="6c592-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="6c592-105">Short description</span></span>
<span data-ttu-id="6c592-106">파일을 사용 하 여 `Types.ps1xml` PowerShell에서 사용 되는 개체 유형을 확장 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-106">Explains how to use `Types.ps1xml` files to extend the types of objects that are used in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="6c592-107">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-107">Long description</span></span>

<span data-ttu-id="6c592-108">확장 유형 데이터는 PowerShell에서 개체 유형의 추가 속성 및 메서드 ("멤버")를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-108">Extended type data defines additional properties and methods ("members") of object types in PowerShell.</span></span> <span data-ttu-id="6c592-109">확장 유형 데이터를 PowerShell 세션에 추가 하는 방법에는 두 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-109">There are two techniques for adding extended type data to a PowerShell session.</span></span>

- <span data-ttu-id="6c592-110">`Types.ps1xml` file: 확장 유형 데이터를 정의 하는 XML 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-110">`Types.ps1xml` file: An XML file that defines extended type data.</span></span>
- <span data-ttu-id="6c592-111">`Update-TypeData`: `Types.ps1xml` 파일을 다시 로드 하 고 현재 세션의 형식에 대 한 확장 데이터를 정의 하는 cmdlet입니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-111">`Update-TypeData`: A cmdlet that reloads `Types.ps1xml` files and defines extended data for types in the current session.</span></span>

<span data-ttu-id="6c592-112">이 항목에서는 파일에 대해 설명 `Types.ps1xml` 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-112">This topic describes `Types.ps1xml` files.</span></span> <span data-ttu-id="6c592-113">Cmdlet을 사용 하 여 동적 확장 유형 데이터를 현재 세션에 추가 하는 방법에 대 한 자세한 내용은 `Update-TypeData` [update-typedata](xref:Microsoft.PowerShell.Utility.Update-TypeData)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6c592-113">For more information about using the `Update-TypeData` cmdlet to add dynamic extended type data to the current session see [Update-TypeData](xref:Microsoft.PowerShell.Utility.Update-TypeData).</span></span>

## <a name="about-extended-type-data"></a><span data-ttu-id="6c592-114">확장 유형 데이터 정보</span><span class="sxs-lookup"><span data-stu-id="6c592-114">About extended type data</span></span>

<span data-ttu-id="6c592-115">확장 유형 데이터는 PowerShell에서 개체 유형의 추가 속성 및 메서드 ("멤버")를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-115">Extended type data defines additional properties and methods ("members") of object types in PowerShell.</span></span> <span data-ttu-id="6c592-116">PowerShell에서 지 원하는 모든 형식을 확장 하 고 개체 형식에 정의 된 속성을 사용 하는 것과 동일한 방식으로 추가 된 속성 및 메서드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-116">You can extend any type that is supported by PowerShell and use the added properties and methods in the same way that you use the properties that are defined on the object types.</span></span>

<span data-ttu-id="6c592-117">예를 들어 PowerShell은 cmdlet이 반환 하는 개체와 같은 모든 개체에 **DateTime** 속성을 추가 `System.DateTime` `Get-Date` 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-117">For example, PowerShell adds a **DateTime** property to all `System.DateTime` objects, such as the ones that the `Get-Date` cmdlet returns.</span></span>

```powershell
(Get-Date).DateTime
```

```Output
Sunday, January 29, 2012 9:43:57 AM
```

<span data-ttu-id="6c592-118">PowerShell에서 속성을 추가 하 고 powershell 에서만 표시 되기 때문에 [System. datetime](/dotnet/api/system.datetime) 구조체의 설명에서 **datetime** 속성을 찾지 못합니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-118">You won't find the **DateTime** property in the description of the [System.DateTime](/dotnet/api/system.datetime) structure, because PowerShell adds the property and it is visible only in PowerShell.</span></span>

<span data-ttu-id="6c592-119">PowerShell은 내부적으로 확장 형식의 기본 집합을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-119">PowerShell internally defines a default set of extended types.</span></span> <span data-ttu-id="6c592-120">이 형식 정보는 시작 시 모든 PowerShell 세션에서 로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-120">This type information is loaded in every PowerShell session at startup.</span></span> <span data-ttu-id="6c592-121">**DateTime** 속성은이 기본 집합의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-121">The **DateTime** property is part of this default set.</span></span> <span data-ttu-id="6c592-122">PowerShell 6 이전에는 형식 정의가 `Types.ps1xml` powershell 설치 디렉터리 ()에 파일을 저장 했습니다 `$PSHOME` .</span><span class="sxs-lookup"><span data-stu-id="6c592-122">Prior to PowerShell 6, the type definitions were stored the `Types.ps1xml` file in the PowerShell installation directory (`$PSHOME`).</span></span>

## <a name="adding-extended-type-data-to-powershell"></a><span data-ttu-id="6c592-123">PowerShell에 확장 형식 데이터 추가</span><span class="sxs-lookup"><span data-stu-id="6c592-123">Adding extended type data to PowerShell</span></span>

<span data-ttu-id="6c592-124">PowerShell 세션에는 확장 유형 데이터의 세 가지 원본이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-124">There are three sources of extended type data in PowerShell sessions.</span></span>

- <span data-ttu-id="6c592-125">PowerShell에서 정의 되는는 모든 PowerShell 세션에 자동으로 로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-125">The defined by PowerShell and is loaded automatically into every PowerShell session.</span></span> <span data-ttu-id="6c592-126">PowerShell 6부터이 정보는 PowerShell로 컴파일되며 더 이상 파일에 제공 되지 않습니다 `Types.ps1xml` .</span><span class="sxs-lookup"><span data-stu-id="6c592-126">Beginning with PowerShell 6, this information is compiled into PowerShell and is no longer shipped in a `Types.ps1xml` file.</span></span>

- <span data-ttu-id="6c592-127">`Types.ps1xml`모듈을 현재 세션으로 가져올 때 모듈 내보내기 파일이 로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-127">The `Types.ps1xml` files that modules export are loaded when the module is imported into the current session.</span></span>

- <span data-ttu-id="6c592-128">Cmdlet을 사용 하 여 정의 된 확장 유형 데이터 `Update-TypeData` 는 현재 세션에만 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-128">Extended type data that is defined by using the `Update-TypeData` cmdlet is added only to the current session.</span></span> <span data-ttu-id="6c592-129">파일에 저장 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-129">It is not saved in a file.</span></span>

<span data-ttu-id="6c592-130">세션에서 세 소스의 확장 유형 데이터는 동일한 방식으로 개체에 적용 되며 지정 된 유형의 모든 개체에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-130">In the session, the extended type data from the three sources is applied to objects in the same way and is available on all objects of the specified types.</span></span>

## <a name="the-typedata-cmdlets"></a><span data-ttu-id="6c592-131">Update-typedata cmdlet</span><span class="sxs-lookup"><span data-stu-id="6c592-131">The TypeData cmdlets</span></span>

<span data-ttu-id="6c592-132">다음 cmdlet은 PowerShell 3.0 이상의 **Microsoft powershell** 모듈에 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-132">The following cmdlets are included in the **Microsoft.PowerShell.Utility** module in PowerShell 3.0 and later.</span></span>

- <span data-ttu-id="6c592-133">`Get-TypeData`: 현재 세션에서 확장 유형 데이터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-133">`Get-TypeData`: Gets extended type data in the current session.</span></span>
- <span data-ttu-id="6c592-134">`Update-TypeData`: `Types.ps1xml` 파일을 다시 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-134">`Update-TypeData`: Reloads `Types.ps1xml` files.</span></span> <span data-ttu-id="6c592-135">확장 유형 데이터를 현재 세션에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-135">Adds extended type data to the current session.</span></span>
- <span data-ttu-id="6c592-136">`Remove-TypeData`: 현재 세션에서 확장 유형 데이터를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-136">`Remove-TypeData`: Removes extended type data from the current session.</span></span>

<span data-ttu-id="6c592-137">이러한 cmdlet에 대 한 자세한 내용은 각 cmdlet에 대 한 도움말 항목을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6c592-137">For more information about these cmdlets, see the help topic for each cmdlet.</span></span>

## <a name="built-in-typesps1xml-files"></a><span data-ttu-id="6c592-138">기본 제공 Types.ps1xml 파일</span><span class="sxs-lookup"><span data-stu-id="6c592-138">Built-in Types.ps1xml files</span></span>

<span data-ttu-id="6c592-139">`Types.ps1xml`디렉터리의 파일은 `$PSHOME` 모든 세션에 자동으로 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-139">The `Types.ps1xml` files in the `$PSHOME` directory are added automatically to every session.</span></span>

<span data-ttu-id="6c592-140">`Types.ps1xml`Powershell 설치 디렉터리 ()의 파일은 `$PSHOME` powershell에서 사용 되는 개체에 속성 및 메서드를 추가할 수 있는 XML 기반 텍스트 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-140">The `Types.ps1xml` file in the PowerShell installation directory (`$PSHOME`) is an XML-based text file that lets you add properties and methods to the objects that are used in PowerShell.</span></span> <span data-ttu-id="6c592-141">PowerShell에는 `Types.ps1xml` .net 형식에 여러 요소를 추가 하는 기본 제공 파일이 있지만 추가 `Types.ps1xml` 파일을 만들어 형식을 더 확장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-141">PowerShell has built-in `Types.ps1xml` files that add several elements to the .NET types, but you can create additional `Types.ps1xml` files to further extend the types.</span></span>

<span data-ttu-id="6c592-142">예를 들어 기본적으로 array 개체 ()에는 `System.Array` 배열의 개체 수를 나열 하는 **Length** 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-142">For example, by default, array objects (`System.Array`) have a **Length** property that lists the number of objects in the array.</span></span> <span data-ttu-id="6c592-143">그러나 이름 **길이** 는 속성을 명확 하 게 설명 하지 않으므로 PowerShell은 같은 값을 표시 하는 **Count** 라는 별칭 속성을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-143">However, because the name **Length** does not clearly describe the property, PowerShell adds an alias property named **Count** that displays the same value.</span></span> <span data-ttu-id="6c592-144">다음 XML은 형식에 **Count** 속성을 추가 합니다 `System.Array` .</span><span class="sxs-lookup"><span data-stu-id="6c592-144">The following XML adds the **Count** property to the `System.Array` type.</span></span>

```xml
<Type>
  <Name>System.Array</Name>
  <Members>
    <AliasProperty>
      <Name>Count</Name>
      <ReferencedMemberName>
        Length
      </ReferencedMemberName>
    </AliasProperty>
  </Members>
</Type>
```

<span data-ttu-id="6c592-145">새 **AliasProperty** 을 가져오려면 `Get-Member` 다음 예제와 같이 배열에 대해 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-145">To get the new **AliasProperty** , use a `Get-Member` command on any array, as shown in the following example.</span></span>

```powershell
Get-Member -InputObject (1,2,3,4)
```

<span data-ttu-id="6c592-146">이 명령은 다음 결과를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-146">The command returns the following results.</span></span>

```Output
Name       MemberType    Definition
----       ----------    ----------
Count      AliasProperty Count = Length
Address    Method        System.Object& Address(Int32)
Clone      Method        System.Object Clone()
CopyTo     Method        System.Void CopyTo(Array array, Int32 index):
Equals     Method        System.Boolean Equals(Object obj)
Get        Method        System.Object Get(Int32)
# ...
```

<span data-ttu-id="6c592-147">따라서 PowerShell에서 배열의 **Count** 속성 또는 **Length** 속성 중 하나를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-147">As a result, you can use either the **Count** property or the **Length** property of arrays in PowerShell.</span></span> <span data-ttu-id="6c592-148">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="6c592-148">For example:</span></span>

```powershell
(1, 2, 3, 4).count
4
```

```powershell
(1, 2, 3, 4).length
4
```

## <a name="creating-new-typesps1xml-files"></a><span data-ttu-id="6c592-149">새 Types.ps1xml 파일 만들기</span><span class="sxs-lookup"><span data-stu-id="6c592-149">Creating new Types.ps1xml files</span></span>

<span data-ttu-id="6c592-150">`.ps1xml`PowerShell과 함께 설치 되는 파일은 서식에 스크립트 블록을 포함할 수 있으므로 변조를 방지 하기 위해 디지털로 서명 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-150">The `.ps1xml` files that are installed with PowerShell are digitally signed to prevent tampering because the formatting can include script blocks.</span></span> <span data-ttu-id="6c592-151">따라서 .NET 형식에 속성 또는 메서드를 추가 하려면 고유한 `Types.ps1xml` 파일을 만든 다음 PowerShell 세션에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-151">Therefore, to add a property or method to a .NET type, create your own `Types.ps1xml` files, and then add them to your PowerShell session.</span></span>

<span data-ttu-id="6c592-152">새 파일을 만들려면 기존 파일을 복사 하 여 시작 `Types.ps1xml` 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-152">To create a new file, start by copying an existing `Types.ps1xml` file.</span></span> <span data-ttu-id="6c592-153">새 파일에는 아무 이름이 나 지정할 수 있지만 `.ps1xml` 파일 이름 확장명이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-153">The new file can have any name, but it must have a `.ps1xml` file name extension.</span></span> <span data-ttu-id="6c592-154">PowerShell에 액세스할 수 있는 모든 디렉터리에 새 파일을 저장할 수 있지만 PowerShell 설치 디렉터리 ( `$PSHOME` ) 또는 설치 디렉터리의 하위 디렉터리에 파일을 저장 하는 것이 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-154">You can place the new file in any directory that is accessible to PowerShell, but it is useful to place the files in the PowerShell installation directory (`$PSHOME`) or in a subdirectory of the installation directory.</span></span>

<span data-ttu-id="6c592-155">새 파일을 저장 한 후 cmdlet을 사용 `Update-TypeData` 하 여 PowerShell 세션에 새 파일을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-155">When you have saved the new file, use the `Update-TypeData` cmdlet to add the new file to your PowerShell session.</span></span> <span data-ttu-id="6c592-156">형식이 정의 된 기본 제공 형식 보다 우선적으로 적용 되도록 하려면 cmdlet의 **PrependData** 매개 변수를 사용 합니다 `Update-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="6c592-156">If you want your types to take precedence over the built-in types that are defined, use the **PrependData** parameter of the `Update-TypeData` cmdlet.</span></span> <span data-ttu-id="6c592-157">`Update-TypeData` 현재 세션에만 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-157">`Update-TypeData` affects only the current session.</span></span> <span data-ttu-id="6c592-158">이후 모든 세션을 변경 하려면 콘솔을 내보내거나 `Update-TypeData` PowerShell 프로필에 명령을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-158">To make the change to all future sessions, export the console, or add the `Update-TypeData` command to your PowerShell profile.</span></span>

## <a name="typesps1xml-and-add-member"></a><span data-ttu-id="6c592-159">Xml 및 Add-Member Types.ps1</span><span class="sxs-lookup"><span data-stu-id="6c592-159">Types.ps1xml and Add-Member</span></span>

<span data-ttu-id="6c592-160">이 `Types.ps1xml` 파일은 영향을 받는 PowerShell 세션에서 지정 된 .net 형식의 모든 개체 인스턴스에 대 한 속성 및 메서드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-160">The `Types.ps1xml` files add properties and methods to all the instances of the objects of the specified .NET type in the affected PowerShell session.</span></span> <span data-ttu-id="6c592-161">그러나 개체의 한 인스턴스에만 속성 또는 메서드를 추가 해야 하는 경우에는 cmdlet을 사용 `Add-Member` 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-161">However, if you need to add properties or methods only to one instance of an object, use the `Add-Member` cmdlet.</span></span>

<span data-ttu-id="6c592-162">자세한 내용은 [구성원 추가](xref:Microsoft.PowerShell.Utility.Add-Member)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6c592-162">For more information, see [Add-Member](xref:Microsoft.PowerShell.Utility.Add-Member).</span></span>

## <a name="example-adding-an-age-member-to-fileinfo-objects"></a><span data-ttu-id="6c592-163">예: FileInfo 개체에 Age 멤버 추가</span><span class="sxs-lookup"><span data-stu-id="6c592-163">Example: Adding an Age member to FileInfo objects</span></span>

<span data-ttu-id="6c592-164">이 예제에서는 **Age** 속성을 **system.object** 개체에 추가 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-164">This example shows how to add an **Age** property to **System.IO.FileInfo** objects.</span></span> <span data-ttu-id="6c592-165">파일의 보존 기간은 만든 시간과 현재 시간 (일) 간의 차이입니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-165">The age of a file is the difference between its creation time and the current time in days.</span></span>

<span data-ttu-id="6c592-166">**Age** 속성은 스크립트 블록을 사용 하 여 계산 되므로 `<ScriptProperty>` 새 **age** 속성의 모델로 사용할 태그를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-166">Because the **Age** property is calculated by using a script block, find a `<ScriptProperty>` tag to use as a model for the new **Age** property.</span></span>

<span data-ttu-id="6c592-167">다음 XML 코드를 파일에 저장 `$PSHOME\MyTypes.ps1xml` 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-167">Save the follow XML code to the file `$PSHOME\MyTypes.ps1xml`.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<Types>
  <Type>
    <Name>System.IO.FileInfo</Name>
    <Members>
      <ScriptProperty>
        <Name>Age</Name>
        <GetScriptBlock>
          ((Get-Date) - ($this.CreationTime)).Days
        </GetScriptBlock>
      </ScriptProperty>
    </Members>
  </Type>
</Types>
```

<span data-ttu-id="6c592-168">`Update-TypeData`를 실행 하 여 `Types.ps1xml` 현재 세션에 새 파일을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-168">Run `Update-TypeData` to add the new `Types.ps1xml` file to the current session.</span></span> <span data-ttu-id="6c592-169">이 명령은 **PrependData** 매개 변수를 사용 하 여 새 파일을 원래 정의 보다 높은 우선 순위 순서 대로 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-169">The command uses the **PrependData** parameter to place the new file in a precedence order higher than the original definitions.</span></span>

<span data-ttu-id="6c592-170">에 대 한 자세한 내용은 `Update-TypeData` [update-typedata](xref:Microsoft.PowerShell.Utility.Update-TypeData)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6c592-170">For more information about `Update-TypeData`, see [Update-TypeData](xref:Microsoft.PowerShell.Utility.Update-TypeData).</span></span>

```powershell
Update-Typedata -PrependPath $PSHOME\MyTypes.ps1xml
```

<span data-ttu-id="6c592-171">변경을 테스트 하려면 명령을 실행 하 여 `Get-ChildItem` 디렉터리에서 PowerShell.exe 파일을 가져온 다음 파일을 `$PSHOME` cmdlet으로 파이프 하 여 `Format-List` 파일의 모든 속성을 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-171">To test the change, run a `Get-ChildItem` command to get the PowerShell.exe file in the `$PSHOME` directory, and then pipe the file to the `Format-List` cmdlet to list all of the properties of the file.</span></span> <span data-ttu-id="6c592-172">변경의 결과로 **Age** 속성이 목록에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-172">As a result of the change, the **Age** property appears in the list.</span></span>

```powershell
Get-ChildItem $PSHOME\pwsh.exe | Select-Object Age
```

```Output
142
```

## <a name="the-xml-in-typesps1xml-files"></a><span data-ttu-id="6c592-173">Types.ps1xml 파일의 XML</span><span class="sxs-lookup"><span data-stu-id="6c592-173">The XML in Types.ps1xml files</span></span>

<span data-ttu-id="6c592-174">전체 스키마 정의는 GitHub의 PowerShell 소스 코드 리포지토리에서 [Types. xsd](https://github.com/PowerShell/PowerShell/blob/master/src/Schemas/Types.xsd) 에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-174">The full schema definition can be found in [Types.xsd](https://github.com/PowerShell/PowerShell/blob/master/src/Schemas/Types.xsd) in the PowerShell source code repository on GitHub.</span></span>

<span data-ttu-id="6c592-175">`<Types>`태그는 파일에 정의 된 모든 형식을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-175">The `<Types>` tag encloses all of the types that are defined in the file.</span></span> <span data-ttu-id="6c592-176">태그는 하나만 있어야 합니다 `<Types>` .</span><span class="sxs-lookup"><span data-stu-id="6c592-176">There should be only one `<Types>` tag.</span></span>

<span data-ttu-id="6c592-177">파일에 언급 된 각 .NET 형식은 태그로 표시 되어야 합니다 `<Type>` .</span><span class="sxs-lookup"><span data-stu-id="6c592-177">Each .NET type mentioned in the file should be represented by a `<Type>` tag.</span></span>

<span data-ttu-id="6c592-178">형식 태그는 다음 태그를 포함 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-178">The type tags must contain the following tags:</span></span>

<span data-ttu-id="6c592-179">`<Name>`: 영향을 받는 .NET 형식의 이름을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-179">`<Name>`: Encloses the name of the affected .NET type.</span></span>

<span data-ttu-id="6c592-180">`<Members>`: .NET 형식에 대해 정의 된 새 속성 및 메서드에 대 한 태그를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-180">`<Members>`: Encloses the tags for the new properties and methods that are defined for the .NET type.</span></span>

<span data-ttu-id="6c592-181">다음 멤버 태그는 태그 내부에 있을 수 있습니다 `<Members>` .</span><span class="sxs-lookup"><span data-stu-id="6c592-181">Any of the following member tags can be inside the `<Members>` tag.</span></span>

<span data-ttu-id="6c592-182">`<AliasProperty>`: 기존 속성의 새 이름을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-182">`<AliasProperty>`: Defines a new name for an existing property.</span></span>

<span data-ttu-id="6c592-183">태그에는 `<AliasProperty>` `<Name>` 새 속성의 이름을 지정 하는 태그와 `<ReferencedMemberName>` 기존 속성을 지정 하는 태그가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-183">The `<AliasProperty>` tag must have a `<Name>` tag that specifies the name of the new property and a `<ReferencedMemberName>` tag that specifies the existing property.</span></span>

<span data-ttu-id="6c592-184">예를 들어 **Count** alias 속성은 array 개체의 **Length** 속성에 대 한 별칭입니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-184">For example, the **Count** alias property is an alias for the **Length** property of array objects.</span></span>

```xml
<Type>
  <Name>System.Array</Name>
  <Members>
    <AliasProperty>
      <Name>Count</Name>
      <ReferencedMemberName>Length</ReferencedMemberName>
    </AliasProperty>
  </Members>
</Type>
```

<span data-ttu-id="6c592-185">`<CodeMethod>`: .NET 클래스의 정적 메서드를 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-185">`<CodeMethod>`:  References a static method of a .NET class.</span></span>

<span data-ttu-id="6c592-186">태그에는 `<CodeMethod>` `<Name>` 새 메서드의 이름을 지정 하는 태그와 `<GetCodeReference>` 메서드가 정의 된 코드를 지정 하는 태그가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-186">The `<CodeMethod>` tag must have a `<Name>` tag that specifies the name of the new method and a `<GetCodeReference>` tag that specifies the code in which the method is defined.</span></span>

<span data-ttu-id="6c592-187">예를 들어 개체의 **모드** 속성은 `System.IO.DirectoryInfo` PowerShell FileSystem 공급자에 정의 된 코드 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-187">For example, the **Mode** property of `System.IO.DirectoryInfo` objects is a code property defined in the PowerShell FileSystem provider.</span></span>

```xml
<Type>
  <Name>System.IO.DirectoryInfo</Name>
  <Members>
    <CodeProperty>
      <Name>Mode</Name>
      <GetCodeReference>
        <TypeName>
          Microsoft.PowerShell.Commands.FileSystemProvider
        </TypeName>
        <MethodName>Mode</MethodName>
      </GetCodeReference>
    </CodeProperty>
  </Members>
</Type>
```

<span data-ttu-id="6c592-188">`<CodeProperty>`: .NET 클래스의 정적 메서드를 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-188">`<CodeProperty>`: References a static method of a .NET class.</span></span>

<span data-ttu-id="6c592-189">태그에는 `<CodeProperty>` `<Name>` 새 속성의 이름을 지정 하는 태그와 `<GetCodeReference>` 속성이 정의 된 코드를 지정 하는 태그가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-189">The `<CodeProperty>` tag must have a `<Name>` tag that specifies the name of the new property and a `<GetCodeReference>` tag that specifies the code in which the property is defined.</span></span>

<span data-ttu-id="6c592-190">예를 들어 개체의 **모드** 속성은 `System.IO.DirectoryInfo` PowerShell FileSystem 공급자에 정의 된 코드 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-190">For example, the **Mode** property of `System.IO.DirectoryInfo` objects is a code property defined in the PowerShell FileSystem provider.</span></span>

```xml
<Type>
  <Name>System.IO.DirectoryInfo</Name>
  <Members>
    <CodeProperty>
      <Name>Mode</Name>
      <GetCodeReference>
        <TypeName>
          Microsoft.PowerShell.Commands.FileSystemProvider
        </TypeName>
        <MethodName>Mode</MethodName>
      </GetCodeReference>
    </CodeProperty>
  </Members>
</Type>
```

<span data-ttu-id="6c592-191">`<MemberSet>`: 멤버 컬렉션 (속성 및 메서드)을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-191">`<MemberSet>`: Defines a collection of members (properties and methods).</span></span>

<span data-ttu-id="6c592-192">`<MemberSet>`태그는 기본 태그 안에 표시 `<Members>` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-192">The `<MemberSet>` tags appear within the primary `<Members>` tags.</span></span> <span data-ttu-id="6c592-193">태그는 `<Name>` 멤버 집합의 이름 및 `<Members>` 집합의 멤버 (속성 및 메서드)를 포함 하는 보조 태그를 둘러싸는 태그를 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-193">The tags must enclose a `<Name>` tag surrounding the name of the member set and a secondary `<Members>` tag that surround the members (properties and methods) in the set.</span></span> <span data-ttu-id="6c592-194">속성 (예: `<NoteProperty>` 또는 `<ScriptProperty>` ) 또는 메서드 (예: 또는)를 만드는 모든 태그는 `<Method>` `<ScriptMethod>` 집합의 멤버일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-194">Any of the tags that create a property (such as `<NoteProperty>` or `<ScriptProperty>`) or a method (such as `<Method>` or `<ScriptMethod>`) can be members of the set.</span></span>

<span data-ttu-id="6c592-195">`Types.ps1xml`파일에서 태그는 `<MemberSet>` PowerShell에서 .net 개체의 기본 뷰를 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-195">In `Types.ps1xml` files, the `<MemberSet>` tag is used to define the default views of the .NET objects in PowerShell.</span></span> <span data-ttu-id="6c592-196">이 경우 멤버 집합의 이름 (태그 내의 값 `<Name>` )은 항상 **Psstandardmembers** 이며 속성 이름 (태그의 값 `<Name>` )은 다음 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-196">In this case, the name of the member set (the value within the `<Name>` tags) is always **PsStandardMembers** , and the names of the properties (the value of the `<Name>` tag) are one of the following:</span></span>

- <span data-ttu-id="6c592-197">`DefaultDisplayProperty`: 개체의 단일 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-197">`DefaultDisplayProperty`: A single property of an object.</span></span>

- <span data-ttu-id="6c592-198">`DefaultDisplayPropertySet`: 개체의 하나 이상의 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-198">`DefaultDisplayPropertySet`: One or more properties of an object.</span></span>

- <span data-ttu-id="6c592-199">`DefaultKeyPropertySet`: 개체의 하나 이상의 키 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-199">`DefaultKeyPropertySet`: One or more key properties of an object.</span></span> <span data-ttu-id="6c592-200">키 속성은 세션 기록에 있는 항목의 ID 수와 같은 속성 값의 인스턴스를 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-200">A key property identifies instances of property values, such as the ID number of items in a session history.</span></span>

<span data-ttu-id="6c592-201">예를 들어 다음 XML은 cmdlet에서 반환 되는 서비스 (개체)의 기본 표시를 정의 합니다 `System.ServiceProcess.ServiceController` `Get-Service` .</span><span class="sxs-lookup"><span data-stu-id="6c592-201">For example, the following XML defines the default display of services (`System.ServiceProcess.ServiceController` objects) that are returned by the `Get-Service` cmdlet.</span></span> <span data-ttu-id="6c592-202">**Status** , **Name** 및 **DisplayName** 속성으로 설정 된 기본 속성으로 구성 된 **psstandardmembers** 라는 구성원 집합을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-202">It defines a member set named **PsStandardMembers** that consists of a default property set with the **Status** , **Name** , and **DisplayName** properties.</span></span>

```xml
<Type>
  <Name>System.ServiceProcess.ServiceController</Name>
  <Members>
    <MemberSet>
      <Name>PSStandardMembers</Name>
      <Members>
        <PropertySet>
          <Name>DefaultDisplayPropertySet</Name>
          <ReferencedProperties>
            <Name>Status</Name>
            <Name>Name</Name>
            <Name>DisplayName</Name>
          </ReferencedProperties>
        </PropertySet>
      </Members>
    </MemberSet>
  </Members>
</Type>
```

<span data-ttu-id="6c592-203">`<Method>`: 기본 개체의 네이티브 메서드를 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-203">`<Method>`: References a native method of the underlying object.</span></span>

<span data-ttu-id="6c592-204">`<Methods>`: 개체의 메서드 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-204">`<Methods>`: A collection of the methods of the object.</span></span>

<span data-ttu-id="6c592-205">`<NoteProperty>`: 정적 값을 사용 하 여 속성을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-205">`<NoteProperty>`: Defines a property with a static value.</span></span>

<span data-ttu-id="6c592-206">태그에는 `<NoteProperty>` `<Name>` 새 속성의 이름을 지정 하는 태그와 `<Value>` 속성의 값을 지정 하는 태그가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-206">The `<NoteProperty>` tag must have a `<Name>` tag that specifies the name of the new property and a `<Value>` tag that specifies the value of the property.</span></span>

<span data-ttu-id="6c592-207">예를 들어 다음 XML은 **system.io.directoryinfo** 개체에 대 한 **상태** 속성을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-207">For example, the following XML creates a **Status** property for **System.IO.DirectoryInfo** objects.</span></span> <span data-ttu-id="6c592-208">**Status** 속성의 값은 항상 **Success** 입니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-208">The value of the **Status** property is always **Success**.</span></span>

```xml
<Type>
  <Name>System.IO.DirectoryInfo</Name>
  <Members>
    <NoteProperty>
      <Name>Status</Name>
      <Value>Success</Value>
    </NoteProperty>
  </Members>
</Type>
```

<span data-ttu-id="6c592-209">`<ParameterizedProperty>`: 인수를 사용 하 고 값을 반환 하는 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-209">`<ParameterizedProperty>`: Properties that take arguments and return a value.</span></span>

<span data-ttu-id="6c592-210">`<Properties>`: 개체 속성의 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-210">`<Properties>`: A collection of the properties of the object.</span></span>

<span data-ttu-id="6c592-211">`<Property>`: 기본 개체의 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-211">`<Property>`: A property of the base object.</span></span>

<span data-ttu-id="6c592-212">`<PropertySet>`: 개체의 속성 컬렉션을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-212">`<PropertySet>`: Defines a collection of properties of the object.</span></span>

<span data-ttu-id="6c592-213">태그에는 `<PropertySet>` `<Name>` 속성 집합의 이름과 `<ReferencedProperty>` 속성을 지정 하는 태그를 지정 하는 태그가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-213">The `<PropertySet>` tag must have a `<Name>` tag that specifies the name of the property set and a `<ReferencedProperty>` tag that specifies the properties.</span></span> <span data-ttu-id="6c592-214">속성의 이름은 태그로 묶여 있습니다 `<Name>` .</span><span class="sxs-lookup"><span data-stu-id="6c592-214">The names of the properties are enclosed in `<Name>` tag.</span></span>

<span data-ttu-id="6c592-215">에서 `Types.ps1xml` `<PropertySet>` 태그는 개체의 기본 표시에 대 한 속성 집합을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-215">In `Types.ps1xml`, `<PropertySet>` tags are used to define sets of properties for the default display of an object.</span></span> <span data-ttu-id="6c592-216">태그의 태그에서 **Psstandardmembers** 값으로 기본 표시를 식별할 수 있습니다 `<Name>` `<MemberSet>` .</span><span class="sxs-lookup"><span data-stu-id="6c592-216">You can identify the default displays by the value **PsStandardMembers** in the `<Name>` tag of a `<MemberSet>` tag.</span></span>

<span data-ttu-id="6c592-217">예를 들어 다음 XML은 개체에 대 한 **상태** 속성을 만듭니다 `System.IO.DirectoryInfo` .</span><span class="sxs-lookup"><span data-stu-id="6c592-217">For example, the following XML creates a **Status** property for the `System.IO.DirectoryInfo` object.</span></span> <span data-ttu-id="6c592-218">**Status** 속성의 값은 항상 **Success** 입니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-218">The value of the **Status** property is always **Success**.</span></span>

```xml
<Type>
  <Name>System.ServiceProcess.ServiceController</Name>
  <Members>
    <MemberSet>
      <Name>PSStandardMembers</Name>
      <Members>
        <PropertySet>
          <Name>DefaultDisplayPropertySet</Name>
          <ReferencedProperties>
            <Name>Status</Name>
            <Name>Name</Name>
            <Name>DisplayName</Name>
          </ReferencedProperties>
        </PropertySet>
      </Members>
    </MemberSet>
  </Members>
</Type>
```

<span data-ttu-id="6c592-219">`<ScriptMethod>`: 값이 스크립트의 출력을 포함 하는 메서드를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-219">`<ScriptMethod>`: Defines a method whose value is the output of a script.</span></span>

<span data-ttu-id="6c592-220">태그에는 `<ScriptMethod>` `<Name>` 새 메서드의 이름을 지정 하는 태그와 `<Script>` 메서드 결과를 반환 하는 스크립트 블록을 포함 하는 태그가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-220">The `<ScriptMethod>` tag must have a `<Name>` tag that specifies the name of the new method and a `<Script>` tag that encloses the script block that returns the method result.</span></span>

<span data-ttu-id="6c592-221">예를 들어 `ConvertToDateTime` `ConvertFromDateTime` 관리 개체 ()의 및 메서드는 `System.System.Management.ManagementObject` `ToDateTime` `ToDmtfDateTime` 클래스의 및 정적 메서드를 사용 하는 스크립트 메서드입니다 `System.Management.ManagementDateTimeConverter` .</span><span class="sxs-lookup"><span data-stu-id="6c592-221">For example, the `ConvertToDateTime` and `ConvertFromDateTime` methods of management objects (`System.System.Management.ManagementObject`) are script methods that use the `ToDateTime` and `ToDmtfDateTime` static methods of the `System.Management.ManagementDateTimeConverter` class.</span></span>

```xml
<Type>
 <Name>System.Management.ManagementObject</Name>
 <Members>
 <ScriptMethod>
   <Name>ConvertToDateTime</Name>
   <Script>
   [System.Management.ManagementDateTimeConverter]::ToDateTime($args[0])
   </Script>
 </ScriptMethod>
 <ScriptMethod>
   <Name>ConvertFromDateTime</Name>
   <Script>
   [System.Management.ManagementDateTimeConverter]::ToDmtfDateTime($args[0])
   </Script>
 </ScriptMethod>
 </Members>
</Type>
```

<span data-ttu-id="6c592-222">`<ScriptProperty>`: 값이 스크립트의 출력 인 속성을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-222">`<ScriptProperty>`: Defines a property whose value is the output of a script.</span></span>

<span data-ttu-id="6c592-223">태그에는 `<ScriptProperty>` `<Name>` 새 속성의 이름과 `<GetScriptBlock>` 속성 값을 반환 하는 스크립트 블록을 포함 하는 태그를 지정 하는 태그가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-223">The `<ScriptProperty>` tag must have a `<Name>` tag that specifies the name of the new property and a `<GetScriptBlock>` tag that encloses the script block that returns the property value.</span></span>

<span data-ttu-id="6c592-224">예를 들어 GetVersionInfo 개체의 **VersionInfo** 속성은 **FileVersionInfo** **개체의** **GetVersionInfo** 정적 메서드의 **FullName** 속성을 사용 하 여 생성 되는 스크립트 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-224">For example, the **VersionInfo** property of the **System.IO.FileInfo** object is a script property that results from using the **FullName** property of the **GetVersionInfo** static method of **System.Diagnostics.FileVersionInfo** objects.</span></span>

```xml
<Type>
  <Name>System.IO.FileInfo</Name>
  <Members>
    <ScriptProperty>
      <Name>VersionInfo</Name>
      <GetScriptBlock>
      [System.Diagnostics.FileVersionInfo]::GetVersionInfo($this.FullName)
      </GetScriptBlock>
    </ScriptProperty>
  </Members>
</Type>
```

<span data-ttu-id="6c592-225">자세한 내용은 [Windows POWERSHELL SDK (소프트웨어 개발 키트)](/powershell/scripting/developer/windows-powershell)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6c592-225">For more information, see the [Windows PowerShell Software Development Kit (SDK)](/powershell/scripting/developer/windows-powershell).</span></span>

## <a name="update-typedata"></a><span data-ttu-id="6c592-226">Update-TypeData</span><span class="sxs-lookup"><span data-stu-id="6c592-226">Update-TypeData</span></span>

<span data-ttu-id="6c592-227">`Types.ps1xml`PowerShell 세션에 파일을 로드 하려면 cmdlet을 실행 `Update-TypeData` 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-227">To load your `Types.ps1xml` files into a PowerShell session, run the `Update-TypeData` cmdlet.</span></span> <span data-ttu-id="6c592-228">파일의 형식이 기본 제공 파일의 형식 보다 우선적으로 적용 되도록 하려면 `Types.ps1xml` 의 **PrependData** 매개 변수를 추가 합니다 `Update-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="6c592-228">If you want the types in your file to take precedence over types in the built-in `Types.ps1xml` file, add the **PrependData** parameter of `Update-TypeData`.</span></span> <span data-ttu-id="6c592-229">`Update-TypeData` 현재 세션에만 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-229">`Update-TypeData` affects only the current session.</span></span> <span data-ttu-id="6c592-230">이후 모든 세션을 변경 하려면 세션을 내보내거나 `Update-TypeData` PowerShell 프로필에 명령을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-230">To make the change to all future sessions, export the session, or add the `Update-TypeData` command to your PowerShell profile.</span></span>

<span data-ttu-id="6c592-231">속성에서 발생 하거나 명령에 속성을 추가 하 여 발생 하는 예외는 `Update-TypeData` 에 오류를 보고 하지 않습니다 `StdErr` .</span><span class="sxs-lookup"><span data-stu-id="6c592-231">Exceptions that occur in properties, or from adding properties to an `Update-TypeData` command, do not report errors to `StdErr`.</span></span> <span data-ttu-id="6c592-232">이는 형식 지정 및 출력 중 많은 일반 유형에서 발생하는 예외를 표시하지 않기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-232">This is to suppress exceptions that would occur in many common types during formatting and outputting.</span></span> <span data-ttu-id="6c592-233">.NET 속성을 가져오는 경우 다음 예제와 같이 메서드 구문을 대신 사용 하 여 예외를 제거 하는 문제를 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-233">If you are getting .NET properties, you can work around the suppression of exceptions by using method syntax instead, as shown in the following example:</span></span>

```powershell
"hello".get_Length()
```

<span data-ttu-id="6c592-234">메서드 구문은 .NET 속성에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-234">Note that method syntax can only be used with .NET properties.</span></span> <span data-ttu-id="6c592-235">Cmdlet을 실행 하 여 추가 된 속성은 `Update-TypeData` 메서드 구문을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-235">Properties that are added by running the `Update-TypeData` cmdlet cannot use method syntax.</span></span>

## <a name="signing-a-typesps1xml-file"></a><span data-ttu-id="6c592-236">Types.ps1xml 파일에 서명</span><span class="sxs-lookup"><span data-stu-id="6c592-236">Signing a Types.ps1xml file</span></span>

<span data-ttu-id="6c592-237">파일의 사용자를 보호 하려면 `Types.ps1xml` 디지털 서명을 사용 하 여 파일에 서명 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c592-237">To protect users of your `Types.ps1xml` file, you can sign the file using a digital signature.</span></span> <span data-ttu-id="6c592-238">자세한 내용은 [about_Signing](about_Signing.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6c592-238">For more information, see [about_Signing](about_Signing.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6c592-239">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6c592-239">See also</span></span>

[<span data-ttu-id="6c592-240">about_Signing</span><span class="sxs-lookup"><span data-stu-id="6c592-240">about_Signing</span></span>](about_Signing.md)

[<span data-ttu-id="6c592-241">Copy-Item</span><span class="sxs-lookup"><span data-stu-id="6c592-241">Copy-Item</span></span>](xref:Microsoft.PowerShell.Management.Copy-Item)

[<span data-ttu-id="6c592-242">Copy-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="6c592-242">Copy-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Copy-ItemProperty)

[<span data-ttu-id="6c592-243">Get-Member</span><span class="sxs-lookup"><span data-stu-id="6c592-243">Get-Member</span></span>](xref:Microsoft.PowerShell.Utility.Get-Member)

[<span data-ttu-id="6c592-244">Get-TypeData</span><span class="sxs-lookup"><span data-stu-id="6c592-244">Get-TypeData</span></span>](xref:Microsoft.PowerShell.Utility.Get-TypeData)

[<span data-ttu-id="6c592-245">Remove-TypeData</span><span class="sxs-lookup"><span data-stu-id="6c592-245">Remove-TypeData</span></span>](xref:Microsoft.PowerShell.Utility.Remove-TypeData)

[<span data-ttu-id="6c592-246">Update-TypeData</span><span class="sxs-lookup"><span data-stu-id="6c592-246">Update-TypeData</span></span>](xref:Microsoft.PowerShell.Utility.Update-TypeData)

