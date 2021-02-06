---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/update-typedata?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-TypeData
ms.openlocfilehash: 1314d388bff5a46bcf335f3da7908a65233aa46e
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99600837"
---
# <span data-ttu-id="27461-102">Update-TypeData</span><span class="sxs-lookup"><span data-stu-id="27461-102">Update-TypeData</span></span>

## <span data-ttu-id="27461-103">개요</span><span class="sxs-lookup"><span data-stu-id="27461-103">Synopsis</span></span>
<span data-ttu-id="27461-104">세션에 있는 확장 유형 데이터를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="27461-104">Updates the extended type data in the session.</span></span>

## <span data-ttu-id="27461-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="27461-105">Syntax</span></span>

### <span data-ttu-id="27461-106">FileSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="27461-106">FileSet (Default)</span></span>

```
Update-TypeData [[-AppendPath] <String[]>] [-PrependPath <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="27461-107">DynamicTypeSet</span><span class="sxs-lookup"><span data-stu-id="27461-107">DynamicTypeSet</span></span>

```
Update-TypeData [-MemberType <PSMemberTypes>] [-MemberName <String>] [-Value <Object>]
 [-SecondValue <Object>] [-TypeConverter <Type>] [-TypeAdapter <Type>]
 [-SerializationMethod <String>] [-TargetTypeForDeserialization <Type>]
 [-SerializationDepth <Int32>] [-DefaultDisplayProperty <String>]
 [-InheritPropertySerializationSet <Nullable`1>] [-StringSerializationSource <String>]
 [-DefaultDisplayPropertySet <String[]>] [-DefaultKeyPropertySet <String[]>]
 [-PropertySerializationSet <String[]>] -TypeName <String> [-Force] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="27461-108">TypeDataSet</span><span class="sxs-lookup"><span data-stu-id="27461-108">TypeDataSet</span></span>

```
Update-TypeData [-Force] [-TypeData] <TypeData[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="27461-109">설명</span><span class="sxs-lookup"><span data-stu-id="27461-109">Description</span></span>

<span data-ttu-id="27461-110">`Update-TypeData`Cmdlet은 `Types.ps1xml` 파일을 메모리로 다시 로드 하 고 새 확장 유형 데이터를 추가 하 여 세션에서 확장 유형 데이터를 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="27461-110">The `Update-TypeData` cmdlet updates the extended type data in the session by reloading the `Types.ps1xml` files into memory and adding new extended type data.</span></span>

<span data-ttu-id="27461-111">기본적으로 PowerShell은 필요에 따라 확장 유형 데이터를 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="27461-111">By default, PowerShell loads extended type data as it is needed.</span></span> <span data-ttu-id="27461-112">매개 변수가 없으면는 `Update-TypeData` `Types.ps1xml` 추가한 형식 파일을 포함 하 여 세션에 로드 된 모든 파일을 다시 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="27461-112">Without parameters, `Update-TypeData` reloads all of the `Types.ps1xml` files that it has loaded in the session, including any type files that you added.</span></span> <span data-ttu-id="27461-113">의 매개 변수를 사용 `Update-TypeData` 하 여 새 형식 파일을 추가 하 고 확장 형식 데이터를 추가 하 고 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27461-113">You can use the parameters of `Update-TypeData` to add new type files and add and replace extended type data.</span></span>

<span data-ttu-id="27461-114">`Update-TypeData`Cmdlet을 사용 하 여 모든 형식 데이터를 미리 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27461-114">The `Update-TypeData` cmdlet can be used to preload all type data.</span></span> <span data-ttu-id="27461-115">이 기능은 유형을 개발하는 도중에 테스트를 위해 이러한 새 유형을 로드하려는 경우에 특히 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="27461-115">This feature is particularly useful when you are developing types and want to load those new types for testing purposes.</span></span>

<span data-ttu-id="27461-116">Windows PowerShell 3.0부터를 사용 하 여 `Update-TypeData` 파일을 사용 하지 않고 세션에서 확장 유형 데이터를 추가 하 고 바꿀 수 있습니다 `Types.ps1xml` .</span><span class="sxs-lookup"><span data-stu-id="27461-116">Beginning in Windows PowerShell 3.0, you can use `Update-TypeData` to add and replace extended type data in the session without using a `Types.ps1xml` file.</span></span> <span data-ttu-id="27461-117">파일 없이 동적으로 추가된 유형 데이터는 현재 세션에만 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="27461-117">Type data that is added dynamically, that is, without a file, is added only to the current session.</span></span> <span data-ttu-id="27461-118">모든 세션에 형식 데이터를 추가 하려면 `Update-TypeData` PowerShell 프로필에 명령을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="27461-118">To add the type data to all sessions, add an `Update-TypeData` command to your PowerShell profile.</span></span> <span data-ttu-id="27461-119">자세한 내용은 [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="27461-119">For more information, see [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).</span></span>

<span data-ttu-id="27461-120">또한 Windows PowerShell 3.0부터 cmdlet을 사용 하 여 `Get-TypeData` 현재 세션에서 확장 유형을 가져오고 cmdlet을 사용 하 여 `Remove-TypeData` 현재 세션에서 확장 유형을 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27461-120">Also, beginning in Windows PowerShell 3.0, you can use the `Get-TypeData` cmdlet to get the extended types in the current session and the `Remove-TypeData` cmdlet to delete extended types from the current session.</span></span>

<span data-ttu-id="27461-121">속성에서 발생 하거나 명령에 속성을 추가할 때 발생 하는 예외는 `Update-TypeData` 오류를 보고 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="27461-121">Exceptions that occur in properties, or from adding properties to an `Update-TypeData` command, do not report errors.</span></span> <span data-ttu-id="27461-122">이는 형식 지정 및 출력 중 많은 일반 유형에서 발생하는 예외를 표시하지 않기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="27461-122">This is to suppress exceptions that would occur in many common types during formatting and outputting.</span></span> <span data-ttu-id="27461-123">.NET 속성을 가져오는 경우 다음 예제와 같이 메서드 구문을 대신 사용 하 여 예외를 제거 하는 문제를 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27461-123">If you are getting .NET properties, you can work around the suppression of exceptions by using method syntax instead, as shown in the following example:</span></span>

`"hello".get_Length()`

<span data-ttu-id="27461-124">메서드 구문은 .NET 속성에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27461-124">Note that method syntax can only be used with .NET properties.</span></span> <span data-ttu-id="27461-125">Cmdlet을 실행 하 여 추가 된 속성은 `Update-TypeData` 메서드 구문을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="27461-125">Properties that are added by running the `Update-TypeData` cmdlet cannot use method syntax.</span></span>

<span data-ttu-id="27461-126">PowerShell의 파일에 대 한 자세한 내용은 `Types.ps1xml` [about_Types.ps1xml](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="27461-126">For more information about the `Types.ps1xml` files in PowerShell, see [about_Types.ps1xml](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md).</span></span>

## <span data-ttu-id="27461-127">예</span><span class="sxs-lookup"><span data-stu-id="27461-127">Examples</span></span>

### <span data-ttu-id="27461-128">예제 1: 확장 형식 업데이트</span><span class="sxs-lookup"><span data-stu-id="27461-128">Example 1: Update extended types</span></span>

```powershell
Update-TypeData
```

<span data-ttu-id="27461-129">이 명령은 `Types.ps1xml` 세션에 이미 사용 된 파일에서 확장 유형 구성을 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="27461-129">This command updates the extended type configuration from the `Types.ps1xml` files that have already been used in the session.</span></span>

### <span data-ttu-id="27461-130">예제 2: 여러 번 형식 업데이트</span><span class="sxs-lookup"><span data-stu-id="27461-130">Example 2: Update types multiple times</span></span>

<span data-ttu-id="27461-131">이 예제에서는 동일한 세션에서 유형 파일의 유형을 여러 번 업데이트 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="27461-131">This example shows how to update the types in a type file multiple times in the same session.</span></span>

<span data-ttu-id="27461-132">첫 번째 명령은 파일에서 확장 유형 구성을 업데이트 하 `Types.ps1xml` `TypesA.types.ps1xml` 고 먼저 및 파일을 처리 합니다 `TypesB.types.ps1xml` .</span><span class="sxs-lookup"><span data-stu-id="27461-132">The first command updates the extended type configuration from the `Types.ps1xml` files, processing the `TypesA.types.ps1xml` and `TypesB.types.ps1xml` files first.</span></span>

<span data-ttu-id="27461-133">두 번째 명령은를 다시 업데이트 하는 방법을 보여 줍니다 `TypesA.types.ps1xml` . 예를 들어 파일에서 형식을 추가 하거나 변경 하는 경우를 들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27461-133">The second command shows how to update the `TypesA.types.ps1xml` again, such as you might do if you added or changed a type in the file.</span></span> <span data-ttu-id="27461-134">`TypesA.types.ps1xml` `Update-TypeData` `TypesA.types.ps1xml` 현재 세션에 대 한 형식 파일 목록에가 이미 있으므로 파일에 대해 이전 명령을 반복 하거나 매개 변수 없이 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27461-134">You can either repeat the previous command for the `TypesA.types.ps1xml` file, or run an `Update-TypeData` command without parameters, because `TypesA.types.ps1xml` is already in the type file list for the current session.</span></span>

```powershell
Update-TypeData -PrependPath TypesA.types.ps1xml, TypesB.types.ps1xml
Update-TypeData -PrependPath TypesA.types.ps1xml
```

### <span data-ttu-id="27461-135">예제 3: DateTime 개체에 스크립트 속성 추가</span><span class="sxs-lookup"><span data-stu-id="27461-135">Example 3: Add a script property to DateTime objects</span></span>

<span data-ttu-id="27461-136">이 예에서는 `Update-TypeData` 를 사용 하 여 cmdlet에서 반환 된 것과 같은 현재 세션의 **DateTime** 개체에 **Quarter** 스크립트 속성을 추가 합니다. `Get-Date`</span><span class="sxs-lookup"><span data-stu-id="27461-136">This example uses `Update-TypeData` to add the **Quarter** script property to **System.DateTime** objects in the current session, such as those returned by the `Get-Date` cmdlet.</span></span>

```powershell
Update-TypeData -TypeName "System.DateTime" -MemberType ScriptProperty -MemberName "Quarter" -Value {
  if ($this.Month -in @(1,2,3)) {"Q1"}
  elseif ($this.Month -in @(4,5,6)) {"Q2"}
  elseif ($this.Month -in @(7,8,9)) {"Q3"}
  else {"Q4"}
}
(Get-Date).Quarter
```

```Output
Q1
```

<span data-ttu-id="27461-137">`Update-TypeData` **TypeName** 매개 변수를 사용 하 여 system.string 형식을 지정 하 고, **MemberName** 매개 변수를 사용 하 여 새 속성의 이름을 지정 하 고, **MemberType** 속성을 사용 하 여 **scriptproperty** 유형을 지정 하 고, **Value** 매개 변수를 사용 하 여 연간 사분기를 결정 하는 스크립트를 지정 **합니다.**</span><span class="sxs-lookup"><span data-stu-id="27461-137">The `Update-TypeData` command uses the **TypeName** parameter to specify **the System.DateTime** type, the **MemberName** parameter to specify a name for the new property, the **MemberType** property to specify the **ScriptProperty** type, and the **Value** parameter to specify the script that determines the annual quarter.</span></span>

<span data-ttu-id="27461-138">**Value** 속성 값은 현재 연간 분기를 계산하는 스크립트입니다.</span><span class="sxs-lookup"><span data-stu-id="27461-138">The value of the **Value** property is a script that calculates the current annual quarter.</span></span> <span data-ttu-id="27461-139">스크립트 블록은 자동 변수를 사용 하 여 `$this` 개체의 현재 인스턴스를 나타내고 In 연산자를 사용 하 여 월 값이 각 정수 배열에 표시 되는지 여부를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="27461-139">The script block uses the `$this` automatic variable to represent the current instance of the object and the In operator to determine whether the month value appears in each integer array.</span></span> <span data-ttu-id="27461-140">연산자에 대 한 자세한 내용은 `-in` [about_Comparison_Operators](../Microsoft.PowerShell.Core/about/about_Comparison_Operators.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="27461-140">For more information about the `-in` operator, see [about_Comparison_Operators](../Microsoft.PowerShell.Core/about/about_Comparison_Operators.md).</span></span>

<span data-ttu-id="27461-141">두 번째 명령은 현재 날짜의 새 Quarter 속성을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="27461-141">The second command gets the new Quarter property of the current date.</span></span>

### <span data-ttu-id="27461-142">예제 4: 기본적으로 목록에 표시 되는 형식 업데이트</span><span class="sxs-lookup"><span data-stu-id="27461-142">Example 4: Update a type that displays in lists by default</span></span>

<span data-ttu-id="27461-143">이 예제에서는 기본적으로 (즉, 속성이 지정 되지 않은 경우) 목록에 표시 되는 형식의 속성을 설정 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="27461-143">This example shows how to set the properties of a type that displays in lists by default, that is, when no properties are specified.</span></span> <span data-ttu-id="27461-144">형식 데이터는 파일에 지정 되지 않기 때문에 `Types.ps1xml` 현재 세션 에서만 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="27461-144">Because the type data is not specified in a `Types.ps1xml` file, it is effective only in the current session.</span></span>

```powershell
Update-TypeData -TypeName "System.DateTime" -DefaultDisplayPropertySet "DateTime, DayOfYear, Quarter"
Get-Date | Format-List
```

```Output
Thursday, March 15, 2012 12:00:00 AM
DayOfYear : 75
Quarter   : Q1
```

<span data-ttu-id="27461-145">첫 번째 명령은 cmdlet을 사용 하 여 `Update-TypeData` **DateTime** 형식의 기본 목록 속성을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="27461-145">The first command uses the `Update-TypeData` cmdlet to set the default list properties for the **System.DateTime** type.</span></span> <span data-ttu-id="27461-146">**TypeName** 매개 변수를 사용하여 유형을 지정하고 **DefaultDisplayPropertySet** 매개 변수를 사용하여 목록의 기본 속성을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="27461-146">The command uses the **TypeName** parameter to specify the type and the **DefaultDisplayPropertySet** parameter to specify the default properties for a list.</span></span> <span data-ttu-id="27461-147">선택한 속성에는 이전 예제에서 추가한 새 **Quarter** 스크립트 속성이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="27461-147">The selected properties include the new **Quarter** script property that was added in a previous example.</span></span>

<span data-ttu-id="27461-148">두 번째 명령은 cmdlet을 사용 하 여 `Get-Date` 현재 날짜를 나타내는 **시스템 DateTime** 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="27461-148">The second command uses the `Get-Date` cmdlet to get a **System.DateTime** object that represents the current date.</span></span> <span data-ttu-id="27461-149">이 명령은 파이프라인 연산자 ()를 사용 하 여 `|` **DateTime** 개체를 cmdlet으로 보냅니다 `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="27461-149">The command uses a pipeline operator (`|`) to send the **DateTime** object to the `Format-List` cmdlet.</span></span> <span data-ttu-id="27461-150">`Format-List`이 명령은 목록에 표시할 속성을 지정 하지 않으므로 PowerShell은 명령에 의해 설정 된 기본값을 사용 합니다 `Update-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="27461-150">Because the `Format-List` command does not specify the properties to display in the list, PowerShell uses the default values that were established by the `Update-TypeData` command.</span></span>

### <span data-ttu-id="27461-151">예 5: 파이프 된 개체에 대 한 형식 데이터 업데이트</span><span class="sxs-lookup"><span data-stu-id="27461-151">Example 5: Update type data for a piped object</span></span>

```powershell
Get-Module | Update-TypeData -MemberType ScriptProperty -MemberName "SupportsUpdatableHelp" -Value {
  if ($this.HelpInfoUri) {$True} else {$False}
}
Get-Module -ListAvailable | Format-Table Name, SupportsUpdatableHelp
```

```Output
Name                             SupportsUpdatableHelp
----                             ---------------------
Microsoft.PowerShell.Diagnostics                  True
Microsoft.PowerShell.Host                         True
Microsoft.PowerShell.Management                   True
Microsoft.PowerShell.Security                     True
Microsoft.PowerShell.Utility                      True
Microsoft.WSMan.Management                        True
PSDiagnostics                                    False
PSScheduledJob                                    True
PSWorkflow                                        True
ServerManager                                     True
TroubleshootingPack                              False
```

<span data-ttu-id="27461-152">이 예제에서는 개체를로 파이프 하는 경우 `Update-TypeData` `Update-TypeData` 개체 형식에 대 한 확장 형식 데이터를 추가 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="27461-152">This example demonstrates that when you pipe an object to `Update-TypeData`, `Update-TypeData` adds extended type data for the object type.</span></span>

<span data-ttu-id="27461-153">이 기법은 cmdlet 또는 메서드를 사용 하 여 `Get-Member` `Get-Type` 개체 형식을 가져오는 것 보다 빠릅니다.</span><span class="sxs-lookup"><span data-stu-id="27461-153">This technique is quicker than using the `Get-Member` cmdlet or the `Get-Type` method to get the object type.</span></span> <span data-ttu-id="27461-154">그러나 개체의 컬렉션을로 파이프 하면 `Update-TypeData` 첫 번째 개체 형식의 형식 데이터가 업데이트 된 다음 해당 멤버가 형식에 이미 정의 되어 있기 때문에 컬렉션의 다른 모든 개체에 대해 오류가 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="27461-154">However, if you pipe a collection of objects to `Update-TypeData`, it updates the type data of the first object type and then returns an error for all other objects in the collection because the member is already defined on the type.</span></span>

<span data-ttu-id="27461-155">첫 번째 명령은 cmdlet을 사용 하 여 `Get-Module` PSScheduledJob 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="27461-155">The first command uses the `Get-Module` cmdlet to get the PSScheduledJob module.</span></span> <span data-ttu-id="27461-156">명령을 사용 하 여 모듈 개체를 cmdlet으로 파이프 합니다. `Update-TypeData` 이 cmdlet은  `Get-Module` **ListAvailable** 매개 변수를 사용 하는 경우 반환 되는 moduleinfogrouping 유형과 같이 여기에서 파생 된 형식 및 해당 형식에 대 한 형식 데이터를 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="27461-156">The command pipes the module object to the `Update-TypeData` cmdlet, which updates the type data for the **System.Management.Automation.PSModuleInfo** type and the types derived from it, such as the ModuleInfoGrouping type that `Get-Module` returns when you use the **ListAvailable** parameter in the command.</span></span>

<span data-ttu-id="27461-157">`Update-TypeData`명령은 가져온 모든 모듈에 **SupportsUpdatableHelp** script 속성을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="27461-157">The `Update-TypeData` commands adds the **SupportsUpdatableHelp** script property to all imported modules.</span></span> <span data-ttu-id="27461-158">**Value** 매개 변수 값은 `$True` 모듈의 **HelpInfoUri** 속성이 채워져 있는 경우를 반환 하 고 그렇지 않으면를 반환 하는 스크립트입니다 `$False` .</span><span class="sxs-lookup"><span data-stu-id="27461-158">The value of the **Value** parameter is a script that returns `$True` if the **HelpInfoUri** property of the module is populated and `$False` otherwise.</span></span>

<span data-ttu-id="27461-159">두 번째 명령은 모듈 개체를에서 cmdlet으로 파이프 합니다 `Get-Module` `Format-Table` . 그러면이 cmdlet이 목록에 있는 모든 모듈의 **Name** 및 **SupportsUpdatableHelp** 속성을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="27461-159">The second command pipes the module objects from `Get-Module` to the `Format-Table` cmdlet, which displays the **Name** and **SupportsUpdatableHelp** properties of all modules in a list.</span></span>

## <span data-ttu-id="27461-160">매개 변수</span><span class="sxs-lookup"><span data-stu-id="27461-160">Parameters</span></span>

### <span data-ttu-id="27461-161">-AppendPath</span><span class="sxs-lookup"><span data-stu-id="27461-161">-AppendPath</span></span>

<span data-ttu-id="27461-162">선택적 파일의 경로를 지정 합니다 `.ps1xml` .</span><span class="sxs-lookup"><span data-stu-id="27461-162">Specifies the path to optional `.ps1xml` files.</span></span> <span data-ttu-id="27461-163">지정한 파일은 기본 제공 파일이 로드된 후 나열된 순서대로 로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="27461-163">The specified files are loaded in the order that they are listed after the built-in files are loaded.</span></span> <span data-ttu-id="27461-164">**Appendpath** 값을로 파이프 할 수도 있습니다 `Update-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="27461-164">You can also pipe an **AppendPath** value to `Update-TypeData`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: FileSet
Aliases: PSPath, Path

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="27461-165">-DefaultDisplayProperty</span><span class="sxs-lookup"><span data-stu-id="27461-165">-DefaultDisplayProperty</span></span>

<span data-ttu-id="27461-166">`Format-Wide`다른 속성이 지정 되지 않은 경우 cmdlet에 의해 표시 되는 형식의 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="27461-166">Specifies the property of the type that is displayed by the `Format-Wide` cmdlet when no other properties are specified.</span></span>

<span data-ttu-id="27461-167">유형의 표준 또는 확장 속성 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="27461-167">Type the name of a standard or extended property of the type.</span></span> <span data-ttu-id="27461-168">이 매개 변수 값은 동일한 명령에서 추가된 유형의 이름일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27461-168">The value of this parameter can be the name of a type that is added in the same command.</span></span>

<span data-ttu-id="27461-169">이 값은 파일의 형식에 대해 정의 된 와이드 뷰가 없는 경우에만 적용 됩니다 `Format.ps1xml` .</span><span class="sxs-lookup"><span data-stu-id="27461-169">This value is effective only when there are no wide views defined for the type in a `Format.ps1xml` file.</span></span>

<span data-ttu-id="27461-170">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="27461-170">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="27461-171">-DefaultDisplayPropertySet</span><span class="sxs-lookup"><span data-stu-id="27461-171">-DefaultDisplayPropertySet</span></span>

<span data-ttu-id="27461-172">유형의 속성을 하나 이상 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="27461-172">Specifies one or more properties of the type.</span></span> <span data-ttu-id="27461-173">이러한 속성은 `Format-List` 다른 속성이 지정 되지 않은 경우 cmdlet에 의해 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="27461-173">These properties are displayed by the `Format-List` cmdlet when no other properties are specified.</span></span>

<span data-ttu-id="27461-174">유형의 표준 또는 확장 속성 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="27461-174">Type the names of standard or extended properties of the type.</span></span> <span data-ttu-id="27461-175">이 매개 변수 값은 동일한 명령에서 추가된 유형의 이름일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27461-175">The value of this parameter can be the names of types that are added in the same command.</span></span>

<span data-ttu-id="27461-176">이 값은 파일의 형식에 대해 정의 된 목록 뷰가 없는 경우에만 적용 됩니다 `Format.ps1xml` .</span><span class="sxs-lookup"><span data-stu-id="27461-176">This value is effective only when there are no list views defined for the type in a `Format.ps1xml` file.</span></span>

<span data-ttu-id="27461-177">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="27461-177">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String[]
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="27461-178">-DefaultKeyPropertySet</span><span class="sxs-lookup"><span data-stu-id="27461-178">-DefaultKeyPropertySet</span></span>

<span data-ttu-id="27461-179">유형의 속성을 하나 이상 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="27461-179">Specifies one or more properties of the type.</span></span> <span data-ttu-id="27461-180">이러한 속성은 `Group-Object` `Sort-Object` 다른 속성이 지정 되지 않은 경우 및 cmdlet에서 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="27461-180">These properties are used by the `Group-Object` and `Sort-Object` cmdlets when no other properties are specified.</span></span>

<span data-ttu-id="27461-181">유형의 표준 또는 확장 속성 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="27461-181">Type the names of standard or extended properties of the type.</span></span> <span data-ttu-id="27461-182">이 매개 변수 값은 동일한 명령에서 추가된 유형의 이름일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27461-182">The value of this parameter can be the names of types that are added in the same command.</span></span>

<span data-ttu-id="27461-183">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="27461-183">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String[]
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="27461-184">-Force</span><span class="sxs-lookup"><span data-stu-id="27461-184">-Force</span></span>

<span data-ttu-id="27461-185">해당 형식에 대해 형식 데이터가 이미 지정 된 경우에도 cmdlet에서 지정 된 형식 데이터를 사용 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="27461-185">Indicates that the cmdlet uses the specified type data, even if type data has already been specified for that type.</span></span>

<span data-ttu-id="27461-186">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="27461-186">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DynamicTypeSet, TypeDataSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="27461-187">-InheritPropertySerializationSet</span><span class="sxs-lookup"><span data-stu-id="27461-187">-InheritPropertySerializationSet</span></span>

<span data-ttu-id="27461-188">Serialize 된 속성 집합이 상속 되는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="27461-188">Indicates whether the set of properties that are serialized is inherited.</span></span> <span data-ttu-id="27461-189">기본값은 `$Null`입니다.</span><span class="sxs-lookup"><span data-stu-id="27461-189">The default value is `$Null`.</span></span> <span data-ttu-id="27461-190">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="27461-190">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="27461-191">`$True`.</span><span class="sxs-lookup"><span data-stu-id="27461-191">`$True`.</span></span> <span data-ttu-id="27461-192">속성 집합이 상속됩니다.</span><span class="sxs-lookup"><span data-stu-id="27461-192">The property set is inherited.</span></span>
- <span data-ttu-id="27461-193">`$False`.</span><span class="sxs-lookup"><span data-stu-id="27461-193">`$False`.</span></span> <span data-ttu-id="27461-194">속성 집합이 상속되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="27461-194">The property set is not inherited.</span></span>
- <span data-ttu-id="27461-195">`$Null`.</span><span class="sxs-lookup"><span data-stu-id="27461-195">`$Null`.</span></span> <span data-ttu-id="27461-196">상속이 정의되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="27461-196">Inheritance is not defined.</span></span>

<span data-ttu-id="27461-197">이 매개 변수는 **SerializationMethod** 매개 변수의 값이 인 경우에만 유효 `SpecificProperties` 합니다.</span><span class="sxs-lookup"><span data-stu-id="27461-197">This parameter is valid only when the value of the **SerializationMethod** parameter is `SpecificProperties`.</span></span> <span data-ttu-id="27461-198">이 매개 변수 값이 이면 `$False` **PropertySerializationSet** 매개 변수가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="27461-198">When the value of this parameter is `$False`, the **PropertySerializationSet** parameter is required.</span></span>

<span data-ttu-id="27461-199">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="27461-199">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Nullable`1[System.Boolean]
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="27461-200">-MemberName</span><span class="sxs-lookup"><span data-stu-id="27461-200">-MemberName</span></span>

<span data-ttu-id="27461-201">속성 또는 메서드의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="27461-201">Specifies the name of a property or method.</span></span>

<span data-ttu-id="27461-202">**TypeName**, **MemberType**, **Value** 및 **SecondValue** 매개 변수와 함께 이 매개 변수를 사용하여 유형의 속성 또는 메서드를 추가하거나 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27461-202">Use this parameter with the **TypeName**, **MemberType**, **Value** and **SecondValue** parameters to add or change a property or method of a type.</span></span>

<span data-ttu-id="27461-203">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="27461-203">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="27461-204">-MemberType</span><span class="sxs-lookup"><span data-stu-id="27461-204">-MemberType</span></span>

<span data-ttu-id="27461-205">추가하거나 변경할 멤버의 유형을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="27461-205">Specifies the type of the member to add or change.</span></span>

<span data-ttu-id="27461-206">**TypeName**, **MemberType**, **Value** 및 **SecondValue** 매개 변수와 함께 이 매개 변수를 사용하여 유형의 속성 또는 메서드를 추가하거나 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27461-206">Use this parameter with the **TypeName**, **MemberType**, **Value** and **SecondValue** parameters to add or change a property or method of a type.</span></span> <span data-ttu-id="27461-207">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="27461-207">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="27461-208">AliasProperty</span><span class="sxs-lookup"><span data-stu-id="27461-208">AliasProperty</span></span>
- <span data-ttu-id="27461-209">CodeMethod</span><span class="sxs-lookup"><span data-stu-id="27461-209">CodeMethod</span></span>
- <span data-ttu-id="27461-210">CodeProperty</span><span class="sxs-lookup"><span data-stu-id="27461-210">CodeProperty</span></span>
- <span data-ttu-id="27461-211">Noteproperty</span><span class="sxs-lookup"><span data-stu-id="27461-211">Noteproperty</span></span>
- <span data-ttu-id="27461-212">ScriptMethod</span><span class="sxs-lookup"><span data-stu-id="27461-212">ScriptMethod</span></span>
- <span data-ttu-id="27461-213">ScriptProperty</span><span class="sxs-lookup"><span data-stu-id="27461-213">ScriptProperty</span></span>

<span data-ttu-id="27461-214">이러한 값에 대 한 자세한 내용은 [PSMemberTypes 열거형](/dotnet/api/system.management.automation.psmembertypes)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="27461-214">For information about these values, see [PSMemberTypes Enumeration](/dotnet/api/system.management.automation.psmembertypes).</span></span>

<span data-ttu-id="27461-215">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="27461-215">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.PSMemberTypes
Parameter Sets: DynamicTypeSet
Aliases:
Accepted values: NoteProperty, AliasProperty, ScriptProperty, CodeProperty, ScriptMethod, CodeMethod

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="27461-216">-PrependPath</span><span class="sxs-lookup"><span data-stu-id="27461-216">-PrependPath</span></span>

<span data-ttu-id="27461-217">선택적 파일의 경로를 지정 합니다 `.ps1xml` .</span><span class="sxs-lookup"><span data-stu-id="27461-217">Specifies the path to the optional `.ps1xml` files.</span></span> <span data-ttu-id="27461-218">지정한 파일은 기본 제공 파일이 로드되기 전에 나열된 순서대로 로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="27461-218">The specified files are loaded in the order that they are listed before the built-in files are loaded.</span></span>

```yaml
Type: System.String[]
Parameter Sets: FileSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="27461-219">-PropertySerializationSet</span><span class="sxs-lookup"><span data-stu-id="27461-219">-PropertySerializationSet</span></span>

<span data-ttu-id="27461-220">직렬화된 속성의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="27461-220">Specifies the names of properties that are serialized.</span></span> <span data-ttu-id="27461-221">**SerializationMethod** 매개 변수 값이 **SpecificProperties** 인 경우 이 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="27461-221">Use this parameter when the value of the **SerializationMethod** parameter is **SpecificProperties**.</span></span>

```yaml
Type: System.String[]
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="27461-222">-SecondValue</span><span class="sxs-lookup"><span data-stu-id="27461-222">-SecondValue</span></span>

<span data-ttu-id="27461-223">**AliasProperty**, **ScriptProperty**, **CodeProperty** 또는 **CodeMethod** 멤버에 대한 추가 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="27461-223">Specifies additional values for **AliasProperty**, **ScriptProperty**, **CodeProperty**, or **CodeMethod** members.</span></span>

<span data-ttu-id="27461-224">이 매개 변수를 **TypeName**, **MemberType**, **Value** 및 **SecondValue** 매개 변수와 함께 사용 하 여 형식의 속성이 나 메서드를 추가 하거나 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27461-224">Use this parameter with the **TypeName**, **MemberType**, **Value**, and **SecondValue** parameters to add or change a property or method of a type.</span></span>

<span data-ttu-id="27461-225">**MemberType** 매개 변수의 값이 인 경우 `AliasProperty` **SecondValue** 매개 변수 값은 데이터 형식 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="27461-225">When the value of the **MemberType** parameter is `AliasProperty`, the value of the **SecondValue** parameter must be a data type.</span></span> <span data-ttu-id="27461-226">PowerShell은 alias 속성의 값을 지정 된 형식으로 변환 (즉, 캐스팅) 합니다.</span><span class="sxs-lookup"><span data-stu-id="27461-226">PowerShell converts (that is, casts) the value of the alias property to the specified type.</span></span> <span data-ttu-id="27461-227">예를 들어 문자열 속성에 대 한 대체 이름을 제공 하는 별칭 속성을 추가 하는 경우 **SecondValue** 의 값을 지정 하 여 별칭이 지정 된 문자열 값을 정수로 변환할 수도 있습니다 **.**</span><span class="sxs-lookup"><span data-stu-id="27461-227">For example, if you add an alias property that provides an alternate name for a string property, you can also specify a **SecondValue** of **System.Int32** to convert the aliased string value to an integer.</span></span>

<span data-ttu-id="27461-228">**MemberType** 매개 변수의 값이 인 경우 `ScriptProperty` **SecondValue** 매개 변수를 사용 하 여 추가 스크립트 블록을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27461-228">When the value of the **MemberType** parameter is `ScriptProperty`, you can use the **SecondValue** parameter to specify an additional script block.</span></span> <span data-ttu-id="27461-229">**Value** 매개 변수 값에 있는 스크립트 블록은 변수 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="27461-229">The script block in the value of the **Value** parameter gets the value of a variable.</span></span> <span data-ttu-id="27461-230">**SecondValue** 매개 변수 값에 있는 스크립트 블록은 변수 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="27461-230">The script block in the value of the **SecondValue** parameter set the value of the variable.</span></span>

<span data-ttu-id="27461-231">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="27461-231">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Object
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="27461-232">-SerializationDepth</span><span class="sxs-lookup"><span data-stu-id="27461-232">-SerializationDepth</span></span>

<span data-ttu-id="27461-233">문자열로 직렬화되는 유형 개체의 수준 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="27461-233">Specifies how many levels of type objects are serialized as strings.</span></span> <span data-ttu-id="27461-234">기본값은 `1` 개체와 해당 속성을 serialize 합니다.</span><span class="sxs-lookup"><span data-stu-id="27461-234">The default value `1` serializes the object and its properties.</span></span> <span data-ttu-id="27461-235">값은 `0` 개체를 serialize 하지만 해당 속성은 serialize 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="27461-235">A value of `0` serializes the object, but not its properties.</span></span> <span data-ttu-id="27461-236">값은 `2` 개체, 해당 속성 및 속성 값에 있는 모든 개체를 serialize 합니다.</span><span class="sxs-lookup"><span data-stu-id="27461-236">A value of `2` serializes the object, its properties, and any objects in property values.</span></span>

<span data-ttu-id="27461-237">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="27461-237">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: 1
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="27461-238">-SerializationMethod</span><span class="sxs-lookup"><span data-stu-id="27461-238">-SerializationMethod</span></span>

<span data-ttu-id="27461-239">유형의 직렬화 메서드를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="27461-239">Specifies a serialization method for the type.</span></span> <span data-ttu-id="27461-240">직렬화 메서드는 직렬화되는 유형의 속성과 직렬화에 사용되는 기술을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="27461-240">A serialization method determines which properties of the type are serialized and the technique that is used to serialize them.</span></span> <span data-ttu-id="27461-241">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="27461-241">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="27461-242">`AllPublicProperties`.</span><span class="sxs-lookup"><span data-stu-id="27461-242">`AllPublicProperties`.</span></span> <span data-ttu-id="27461-243">유형의 모든 공용 속성을 직렬화합니다.</span><span class="sxs-lookup"><span data-stu-id="27461-243">Serialize all public properties of the type.</span></span> <span data-ttu-id="27461-244">**SerializationDepth** 매개 변수를 사용하여 자식 속성을 직렬화할지 여부를 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27461-244">You can use the **SerializationDepth** parameter to determine whether child properties are serialized.</span></span>
- <span data-ttu-id="27461-245">`String`.</span><span class="sxs-lookup"><span data-stu-id="27461-245">`String`.</span></span> <span data-ttu-id="27461-246">유형을 문자열로 직렬화합니다.</span><span class="sxs-lookup"><span data-stu-id="27461-246">Serialize the type as a string.</span></span> <span data-ttu-id="27461-247">**StringSerializationSource** 를 사용하여 직렬화 결과로 사용할 유형의 속성을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27461-247">You can use the **StringSerializationSource** to specify a property of the type to use as the serialization result.</span></span> <span data-ttu-id="27461-248">그러지 않으면 유형이 개체의 **ToString** 메서드를 사용하여 직렬화됩니다.</span><span class="sxs-lookup"><span data-stu-id="27461-248">Otherwise, the type is serialized by using the **ToString** method of the object.</span></span>
- <span data-ttu-id="27461-249">`SpecificProperties`.</span><span class="sxs-lookup"><span data-stu-id="27461-249">`SpecificProperties`.</span></span> <span data-ttu-id="27461-250">이 형식의 지정 된 속성만 직렬화 합니다.</span><span class="sxs-lookup"><span data-stu-id="27461-250">Serialize only the specified properties of this type.</span></span> <span data-ttu-id="27461-251">**PropertySerializationSet** 매개 변수를 사용하여 직렬화할 유형의 속성을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27461-251">Use the **PropertySerializationSet** parameter to specify the properties of the type that are serialized.</span></span>
  <span data-ttu-id="27461-252">**InheritPropertySerializationSet** 매개 변수를 사용하여 속성 집합을 상속할지 여부를 결정하고 **SerializationDepth** 매개 변수를 사용하여 자식 속성을 직렬화할지 여부를 결정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27461-252">You can also use the **InheritPropertySerializationSet** parameter to determine whether the property set is inherited and the **SerializationDepth** parameter to determine whether child properties are serialized.</span></span>

<span data-ttu-id="27461-253">PowerShell에서 직렬화 메서드는 **Psstandardmembers** 내부 개체에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="27461-253">In PowerShell, serialization methods are stored in **PSStandardMembers** internal objects.</span></span>

<span data-ttu-id="27461-254">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="27461-254">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="27461-255">-StringSerializationSource</span><span class="sxs-lookup"><span data-stu-id="27461-255">-StringSerializationSource</span></span>

<span data-ttu-id="27461-256">유형의 속성 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="27461-256">Specifies the name of a property of the type.</span></span> <span data-ttu-id="27461-257">지정한 속성 값은 직렬화 결과로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="27461-257">The value of specified property is used as the serialization result.</span></span> <span data-ttu-id="27461-258">이 매개 변수는 **SerializationMethod** 매개 변수 값이 문자열인 경우에만 유효 합니다.</span><span class="sxs-lookup"><span data-stu-id="27461-258">This parameter is valid only when the value of the **SerializationMethod** parameter is String.</span></span>

```yaml
Type: System.String
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="27461-259">-TargetTypeForDeserialization</span><span class="sxs-lookup"><span data-stu-id="27461-259">-TargetTypeForDeserialization</span></span>

<span data-ttu-id="27461-260">역직렬화 시 이 유형의 개체가 변환되는 유형을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="27461-260">Specifies the type to which object of this type are converted when they are deserialized.</span></span>

<span data-ttu-id="27461-261">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="27461-261">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Type
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="27461-262">-TypeAdapter</span><span class="sxs-lookup"><span data-stu-id="27461-262">-TypeAdapter</span></span>

<span data-ttu-id="27461-263">유형 어댑터의 유형 (예: **CimInstanceAdapter**)을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="27461-263">Specifies the type of a type adapter, such as **Microsoft.PowerShell.Cim.CimInstanceAdapter**.</span></span> <span data-ttu-id="27461-264">형식 어댑터를 사용 하면 PowerShell에서 형식의 멤버를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27461-264">A type adapter enables PowerShell to get the members of a type.</span></span>

<span data-ttu-id="27461-265">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="27461-265">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Type
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="27461-266">-TypeConverter</span><span class="sxs-lookup"><span data-stu-id="27461-266">-TypeConverter</span></span>

<span data-ttu-id="27461-267">유형 간에 값을 변환할 유형 변환기를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="27461-267">Specifies a type converter to convert values between different types.</span></span> <span data-ttu-id="27461-268">유형에 대한 유형 변환기를 정의하면 유형 변환기 인스턴스가 변환에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="27461-268">If a type converter is defined for a type, an instance of the type converter is used for the conversion.</span></span>

<span data-ttu-id="27461-269">**System.ComponentModel.TypeConverter** 또는 **System.Management.Automation.PSTypeConverter** 클래스에서 파생된 **System.Type** 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="27461-269">Enter a **System.Type** value that is derived from the **System.ComponentModel.TypeConverter** or **System.Management.Automation.PSTypeConverter** classes.</span></span>

<span data-ttu-id="27461-270">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="27461-270">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Type
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="27461-271">-Update-typedata</span><span class="sxs-lookup"><span data-stu-id="27461-271">-TypeData</span></span>

<span data-ttu-id="27461-272">이 cmdlet이 세션에 추가 하는 형식 데이터의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="27461-272">Specifies an array of type data that this cmdlet adds to the session.</span></span> <span data-ttu-id="27461-273">**Update-typedata** 개체가 포함 된 변수를 입력 하거나 **update-typedata** 개체를 가져오는 명령 (예: 명령)을 입력 `Get-TypeData` 합니다.</span><span class="sxs-lookup"><span data-stu-id="27461-273">Enter a variable that contains a **TypeData** object or a command that gets a **TypeData** object, such as a `Get-TypeData` command.</span></span> <span data-ttu-id="27461-274">**Update-typedata** 개체를로 파이프 할 수도 있습니다 `Update-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="27461-274">You can also pipe a **TypeData** object to `Update-TypeData`.</span></span>

<span data-ttu-id="27461-275">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="27461-275">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.TypeData[]
Parameter Sets: TypeDataSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="27461-276">-TypeName</span><span class="sxs-lookup"><span data-stu-id="27461-276">-TypeName</span></span>

<span data-ttu-id="27461-277">확장할 유형의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="27461-277">Specifies the name of the type to extend.</span></span>

<span data-ttu-id="27461-278">**System** 네임스페이스에 있는 유형의 경우 짧은 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="27461-278">For types in the **System** namespace, enter the short name.</span></span> <span data-ttu-id="27461-279">그러지 않으면 전체 유형 이름이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="27461-279">Otherwise, the full type name is required.</span></span> <span data-ttu-id="27461-280">와일드카드는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="27461-280">Wildcards are not supported.</span></span>

<span data-ttu-id="27461-281">형식 이름을로 파이프 할 수 있습니다 `Update-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="27461-281">You can pipe type names to `Update-TypeData`.</span></span> <span data-ttu-id="27461-282">개체를로 파이프 하는 경우 개체 `Update-TypeData` `Update-TypeData` 의 형식 이름과 개체 형식에 대 한 데이터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="27461-282">When you pipe an object to `Update-TypeData`, `Update-TypeData` gets the type name of the object and type data to the object type.</span></span>

<span data-ttu-id="27461-283">**MemberName**, **MemberType**, **Value** 및 **SecondValue** 매개 변수와 함께이 매개 변수를 사용 하 여 형식의 속성이 나 메서드를 추가 하거나 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27461-283">Use this parameter with the **MemberName**, **MemberType**, **Value** and **SecondValue** parameters to add or change a property or method of a type.</span></span>

<span data-ttu-id="27461-284">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="27461-284">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: DynamicTypeSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="27461-285">-Value</span><span class="sxs-lookup"><span data-stu-id="27461-285">-Value</span></span>

<span data-ttu-id="27461-286">속성 또는 메서드의 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="27461-286">Specifies the value of the property or method.</span></span>

<span data-ttu-id="27461-287">,, 또는 멤버를 추가 하는 경우 `AliasProperty` `CodeProperty` `ScriptProperty` `CodeMethod` **SecondValue** 매개 변수를 사용 하 여 추가 정보를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27461-287">If you add an `AliasProperty`, `CodeProperty`, `ScriptProperty`, or `CodeMethod` member, you can use the **SecondValue** parameter to add additional information.</span></span>

<span data-ttu-id="27461-288">**MemberName**, **MemberType**, **Value** 및 **SecondValue** 매개 변수와 함께이 매개 변수를 사용 하 여 형식의 속성이 나 메서드를 추가 하거나 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27461-288">Use this parameter with the **MemberName**, **MemberType**, **Value** and **SecondValue** parameters to add or change a property or method of a type.</span></span>

<span data-ttu-id="27461-289">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="27461-289">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Object
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="27461-290">-Confirm</span><span class="sxs-lookup"><span data-stu-id="27461-290">-Confirm</span></span>

<span data-ttu-id="27461-291">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="27461-291">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="27461-292">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="27461-292">-WhatIf</span></span>

<span data-ttu-id="27461-293">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="27461-293">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="27461-294">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="27461-294">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="27461-295">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="27461-295">CommonParameters</span></span>

<span data-ttu-id="27461-296">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="27461-296">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="27461-297">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="27461-297">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="27461-298">입력</span><span class="sxs-lookup"><span data-stu-id="27461-298">Inputs</span></span>

### <span data-ttu-id="27461-299">System.String</span><span class="sxs-lookup"><span data-stu-id="27461-299">System.String</span></span>

<span data-ttu-id="27461-300">**Appendpath**, **TypeName** 또는 **update-typedata** 매개 변수의 값이 포함 된 문자열을로 파이프 할 수 있습니다 `Update-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="27461-300">You can pipe a string that contains the values of the **AppendPath**, **TypeName**, or **TypeData** parameters to `Update-TypeData`.</span></span>

## <span data-ttu-id="27461-301">출력</span><span class="sxs-lookup"><span data-stu-id="27461-301">Outputs</span></span>

### <span data-ttu-id="27461-302">없음</span><span class="sxs-lookup"><span data-stu-id="27461-302">None</span></span>

<span data-ttu-id="27461-303">이 cmdlet은 어떠한 출력도 반환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="27461-303">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="27461-304">참고</span><span class="sxs-lookup"><span data-stu-id="27461-304">Notes</span></span>

## <span data-ttu-id="27461-305">관련 링크</span><span class="sxs-lookup"><span data-stu-id="27461-305">Related links</span></span>

[<span data-ttu-id="27461-306">about_Types.ps1xml</span><span class="sxs-lookup"><span data-stu-id="27461-306">about_Types.ps1xml</span></span>](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md)

[<span data-ttu-id="27461-307">Get-TypeData</span><span class="sxs-lookup"><span data-stu-id="27461-307">Get-TypeData</span></span>](Get-TypeData.md)

[<span data-ttu-id="27461-308">Remove-TypeData</span><span class="sxs-lookup"><span data-stu-id="27461-308">Remove-TypeData</span></span>](Remove-TypeData.md)

