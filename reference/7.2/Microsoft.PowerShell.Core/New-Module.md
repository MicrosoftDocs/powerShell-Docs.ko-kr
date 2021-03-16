---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-module?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Module
ms.openlocfilehash: 487fd85bdcc918b7fb360f9c9d23388a06b35f86
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599357"
---
# <span data-ttu-id="9e930-102">New-Module</span><span class="sxs-lookup"><span data-stu-id="9e930-102">New-Module</span></span>

## <span data-ttu-id="9e930-103">개요</span><span class="sxs-lookup"><span data-stu-id="9e930-103">SYNOPSIS</span></span>
<span data-ttu-id="9e930-104">메모리에만 있는 새 동적 모듈을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9e930-104">Creates a new dynamic module that exists only in memory.</span></span>

## <span data-ttu-id="9e930-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9e930-105">SYNTAX</span></span>

### <span data-ttu-id="9e930-106">ScriptBlock (기본값)</span><span class="sxs-lookup"><span data-stu-id="9e930-106">ScriptBlock (Default)</span></span>

```
New-Module [-ScriptBlock] <ScriptBlock> [-Function <String[]>] [-Cmdlet <String[]>] [-ReturnResult]
 [-AsCustomObject] [-ArgumentList <Object[]>] [<CommonParameters>]
```

### <span data-ttu-id="9e930-107">Name</span><span class="sxs-lookup"><span data-stu-id="9e930-107">Name</span></span>

```
New-Module [-Name] <String> [-ScriptBlock] <ScriptBlock> [-Function <String[]>] [-Cmdlet <String[]>]
 [-ReturnResult] [-AsCustomObject] [-ArgumentList <Object[]>] [<CommonParameters>]
```

## <span data-ttu-id="9e930-108">설명</span><span class="sxs-lookup"><span data-stu-id="9e930-108">DESCRIPTION</span></span>

<span data-ttu-id="9e930-109">`New-Module`Cmdlet은 스크립트 블록에서 동적 모듈을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9e930-109">The `New-Module` cmdlet creates a dynamic module from a script block.</span></span> <span data-ttu-id="9e930-110">동적 모듈의 멤버(예: 함수 및 변수)는 세션에서 즉시 사용할 수 있어야 하며 세션을 닫을 때까지 사용할 수 있는 상태로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e930-110">The members of the dynamic module, such as functions and variables, are immediately available in the session and remain available until you close the session.</span></span>

<span data-ttu-id="9e930-111">정적 모듈과 마찬가지로 동적 모듈의 cmdlet과 함수는 기본적으로 내보내고 변수와 별칭은 내보내지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9e930-111">Like static modules, by default, the cmdlets and functions in a dynamic module are exported and the variables and aliases are not.</span></span> <span data-ttu-id="9e930-112">그러나 Export-ModuleMember cmdlet 및의 매개 변수를 사용 하 여 기본값을 재정의할 수 있습니다 `New-Module` .</span><span class="sxs-lookup"><span data-stu-id="9e930-112">However, you can use the Export-ModuleMember cmdlet and the parameters of `New-Module` to override the defaults.</span></span>

<span data-ttu-id="9e930-113">의 **AsCustomObject** 매개 변수를 사용 하 여 `New-Module` 동적 모듈을 사용자 지정 개체로 반환할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e930-113">You can also use the **AsCustomObject** parameter of `New-Module` to return the dynamic module as a custom object.</span></span> <span data-ttu-id="9e930-114">함수와 같은 모듈 멤버는 세션으로 가져오는 대신 사용자 지정 개체의 스크립트 메서드로 구현됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e930-114">The members of the modules, such as functions, are implemented as script methods of the custom object instead of being imported into the session.</span></span>

<span data-ttu-id="9e930-115">동적 모듈은 메모리에만 있고 디스크에는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9e930-115">Dynamic modules exist only in memory, not on disk.</span></span> <span data-ttu-id="9e930-116">모든 모듈과 마찬가지로 동적 모듈의 멤버는 전역 범위의 하위인 개인 모듈 범위에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e930-116">Like all modules, the members of dynamic modules run in a private module scope that is a child of the global scope.</span></span> <span data-ttu-id="9e930-117">Get-Module은 동적 모듈을 가져올 수 없지만 Get-Command는 내보낸 멤버를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e930-117">Get-Module cannot get a dynamic module, but Get-Command can get the exported members.</span></span>

<span data-ttu-id="9e930-118">에서 동적 모듈을 사용할 수 있도록 하려면 `Get-Module` `New-Module` 명령을 import-module으로 파이프 하거나로 반환 되는 module 개체를 파이프 `New-Module` `Import-Module` 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e930-118">To make a dynamic module available to `Get-Module`, pipe a `New-Module` command to Import-Module, or pipe the module object that `New-Module` returns to `Import-Module`.</span></span> <span data-ttu-id="9e930-119">이 작업은 동적 모듈을 목록에 추가 `Get-Module` 하지만 모듈을 디스크에 저장 하거나 영구적으로 설정 하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9e930-119">This action adds the dynamic module to the `Get-Module` list, but it does not save the module to disk or make it persistent.</span></span>

## <span data-ttu-id="9e930-120">예제</span><span class="sxs-lookup"><span data-stu-id="9e930-120">EXAMPLES</span></span>

### <span data-ttu-id="9e930-121">예제 1: 동적 모듈 만들기</span><span class="sxs-lookup"><span data-stu-id="9e930-121">Example 1: Create a dynamic module</span></span>

<span data-ttu-id="9e930-122">이 예에서는 라는 함수를 사용 하 여 새 동적 모듈을 만듭니다 `Hello` .</span><span class="sxs-lookup"><span data-stu-id="9e930-122">This example creates a new dynamic module with a function called `Hello`.</span></span> <span data-ttu-id="9e930-123">이 명령은 새 동적 모듈을 나타내는 모듈 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="9e930-123">The command returns a module object that represents the new dynamic module.</span></span>

```powershell
New-Module -ScriptBlock {function Hello {"Hello!"}}
```

```Output
Name              : __DynamicModule_2ceb1d0a-990f-45e4-9fe4-89f0f6ead0e5
Path              : 2ceb1d0a-990f-45e4-9fe4-89f0f6ead0e5
Description       :
Guid              : 00000000-0000-0000-0000-000000000000
Version           : 0.0
ModuleBase        :
ModuleType        : Script
PrivateData       :
AccessMode        : ReadWrite
ExportedAliases   : {}
ExportedCmdlets   : {}
ExportedFunctions : {[Hello, Hello]}
ExportedVariables : {}
NestedModules     : {}
```

### <span data-ttu-id="9e930-124">예 2: 동적 모듈과 Get-Module 및 Get-Command 사용</span><span class="sxs-lookup"><span data-stu-id="9e930-124">Example 2: Working with dynamic modules and Get-Module and Get-Command</span></span>

<span data-ttu-id="9e930-125">이 예에서는 cmdlet에서 동적 모듈을 반환 하지 않는 방법을 보여 줍니다 `Get-Module` .</span><span class="sxs-lookup"><span data-stu-id="9e930-125">This example demonstrates that dynamic modules are not returned by the `Get-Module` cmdlet.</span></span> <span data-ttu-id="9e930-126">이러한 멤버가 내보내는 멤버는 cmdlet에 의해 반환 됩니다 `Get-Command` .</span><span class="sxs-lookup"><span data-stu-id="9e930-126">The members that they export are returned by the `Get-Command` cmdlet.</span></span>

```powershell
new-module -scriptblock {function Hello {"Hello!"}}
```

```Output
Name              : __DynamicModule_2ceb1d0a-990f-45e4-9fe4-89f0f6ead0e5
Path              : 2ceb1d0a-990f-45e4-9fe4-89f0f6ead0e5
Description       :
Guid              : 00000000-0000-0000-0000-000000000000
Version           : 0.0
ModuleBase        :
ModuleType        : Script
PrivateData       :
AccessMode        : ReadWrite
ExportedAliases   : {}
ExportedCmdlets   : {}
ExportedFunctions : {[Hello, Hello]}
ExportedVariables : {}
NestedModules     : {}
```

```powershell
Get-Module

Get-Command Hello
```

```Output
CommandType     Name   Definition
-----------     ----   ----------
Function        Hello  "Hello!"
```

### <span data-ttu-id="9e930-127">예제 3: 변수를 현재 세션으로 내보내기</span><span class="sxs-lookup"><span data-stu-id="9e930-127">Example 3: Export a variable into the current session</span></span>

<span data-ttu-id="9e930-128">이 예에서는 cmdlet을 사용 하 여 `Export-ModuleMember` 변수를 현재 세션으로 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="9e930-128">This example uses the `Export-ModuleMember` cmdlet to export a variable into the current session.</span></span>
<span data-ttu-id="9e930-129">명령이 없으면 `Export-ModuleMember` 함수만 내보내집니다.</span><span class="sxs-lookup"><span data-stu-id="9e930-129">Without the `Export-ModuleMember` command, only the function is exported.</span></span>

```powershell
New-Module -ScriptBlock {$SayHelloHelp="Type 'SayHello', a space, and a name."; function SayHello ($name) { "Hello, $name" }; Export-ModuleMember -function SayHello -Variable SayHelloHelp}
$SayHelloHelp
```

```Output
Type 'SayHello', a space, and a name.
```

```powershell
SayHello Jeffrey
```

```Output
Hello, Jeffrey
```

<span data-ttu-id="9e930-130">출력에는 변수와 함수 모두 세션으로 내보냈다고 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e930-130">The output shows that both the variable and the function were exported into the session.</span></span>

### <span data-ttu-id="9e930-131">예 4: Get-Module에서 동적 모듈을 사용할 수 있도록 설정</span><span class="sxs-lookup"><span data-stu-id="9e930-131">Example 4: Make a dynamic module available to Get-Module</span></span>

<span data-ttu-id="9e930-132">이 예에서는 동적 모듈을로 파이프 하 여에서 동적 모듈을 사용할 수 있도록 설정 하는 방법을 보여 줍니다 `Get-Module` `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="9e930-132">This example demonstrates that you can make a dynamic module available to `Get-Module` by piping the dynamic module to `Import-Module`.</span></span>

<span data-ttu-id="9e930-133">`New-Module` cmdlet으로 파이프 되는 module 개체를 만듭니다 `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="9e930-133">`New-Module` creates a module object that is piped to the `Import-Module` cmdlet.</span></span> <span data-ttu-id="9e930-134">의 **name** 매개 변수는 `New-Module` 모듈에 이름을 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e930-134">The **Name** parameter of `New-Module` assigns a friendly name to the module.</span></span> <span data-ttu-id="9e930-135">`Import-Module`는 기본적으로 개체를 반환 하지 않으므로이 명령의 출력은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9e930-135">Because `Import-Module` does not return any objects by default, there is no output from this command.</span></span> <span data-ttu-id="9e930-136">`Get-Module`**GreetingModule** 를 현재 세션으로 가져왔습니다.</span><span class="sxs-lookup"><span data-stu-id="9e930-136">`Get-Module` that the **GreetingModule** has been imported into the current session.</span></span>

```powershell
New-Module -ScriptBlock {function Hello {"Hello!"}} -name GreetingModule | Import-Module
Get-Module
```

```Output
Name              : GreetingModule
Path              : d54dfdac-4531-4db2-9dec-0b4b9c57a1e5
Description       :
Guid              : 00000000-0000-0000-0000-000000000000
Version           : 0.0
ModuleBase        :
ModuleType        : Script
PrivateData       :
AccessMode        : ReadWrite
ExportedAliases   : {}
ExportedCmdlets   : {}
ExportedFunctions : {[Hello, Hello]}
ExportedVariables : {}
NestedModules     : {}
```

```powershell
Get-Command hello
```

```Output
CommandType     Name                                                               Definition
-----------     ----                                                               ----------
Function        Hello                                                              "Hello!"
```

<span data-ttu-id="9e930-137">`Get-Command`Cmdlet은 `Hello` 동적 모듈이 내보내는 함수를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9e930-137">The `Get-Command` cmdlet shows the `Hello` function that the dynamic module exports.</span></span>

### <span data-ttu-id="9e930-138">예 5: 내보낸 함수를 포함 하는 사용자 지정 개체 생성</span><span class="sxs-lookup"><span data-stu-id="9e930-138">Example 5: Generate a custom object that has exported functions</span></span>

<span data-ttu-id="9e930-139">이 예제에서는의 **AsCustomObject** 매개 변수를 사용 하 여 `New-Module` 내보낸 함수를 나타내는 스크립트 메서드를 포함 하는 사용자 지정 개체를 생성 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9e930-139">This example shows how to use the **AsCustomObject** parameter of `New-Module` to generate a custom object that has script methods that represent the exported functions.</span></span>

<span data-ttu-id="9e930-140">`New-Module`Cmdlet은 및 라는 두 개의 함수를 사용 하 여 동적 모듈을 만듭니다 `Hello` `Goodbye` .</span><span class="sxs-lookup"><span data-stu-id="9e930-140">The `New-Module` cmdlet creates a dynamic module with two functions, `Hello` and `Goodbye`.</span></span> <span data-ttu-id="9e930-141">**AsCustomObject** 매개 변수는 기본적으로 생성 되는 **psmoduleinfo** 개체 대신 사용자 지정 개체를 만듭니다 `New-Module` .</span><span class="sxs-lookup"><span data-stu-id="9e930-141">The **AsCustomObject** parameter creates a custom object instead of the **PSModuleInfo** object that `New-Module` generates by default.</span></span> <span data-ttu-id="9e930-142">이 사용자 지정 개체는 변수에 저장 됩니다 `$m` .</span><span class="sxs-lookup"><span data-stu-id="9e930-142">This custom object is saved in the `$m` variable.</span></span>
<span data-ttu-id="9e930-143">`$m`변수에 할당 된 값이 없는 것으로 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="9e930-143">The `$m` variable appears to have no assigned value.</span></span>

```powershell
$m = New-Module -ScriptBlock {
  function Hello ($name) {"Hello, $name"}
  function Goodbye ($name) {"Goodbye, $name"}
} -AsCustomObject
$m
$m | Get-Member
```

```Output
TypeName: System.Management.Automation.PSCustomObject

Name        MemberType   Definition
----        ----------   ----------
Equals      Method       bool Equals(System.Object obj)
GetHashCode Method       int GetHashCode()
GetType     Method       type GetType()
ToString    Method       string ToString()
Goodbye     ScriptMethod System.Object Goodbye();
Hello       ScriptMethod System.Object Hello();
```

```powershell
$m.goodbye("Jane")
```

```Output
Goodbye, Jane
```

```powershell
$m.hello("Manoj")
```

```Output
Hello, Manoj
```

<span data-ttu-id="9e930-144">`$m`Cmdlet에 파이프 하 여 `Get-Member` 사용자 지정 개체의 속성 및 메서드를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e930-144">Piping `$m` to the `Get-Member` cmdlet displays the properties and methods of the custom object.</span></span> <span data-ttu-id="9e930-145">출력은 개체에 및 함수를 나타내는 스크립트 메서드가 있음을 보여 `Hello` 줍니다 `Goodbye` .</span><span class="sxs-lookup"><span data-stu-id="9e930-145">The output shows that the object has script methods that represent the `Hello` and `Goodbye` functions.</span></span>
<span data-ttu-id="9e930-146">마지막으로 이러한 스크립트 메서드를 호출 하 고 결과를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e930-146">Finally, we call these script methods and display the results.</span></span>

### <span data-ttu-id="9e930-147">예제 6: 스크립트 블록의 결과 가져오기</span><span class="sxs-lookup"><span data-stu-id="9e930-147">Example 6: Get the results of the script block</span></span>

<span data-ttu-id="9e930-148">이 예에서는 **Returnresult** 매개 변수를 사용 하 여 모듈 개체를 요청 하는 대신 스크립트 블록의 실행 결과를 요청 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e930-148">This example uses the **ReturnResult** parameter to request the results of running the script block instead of requesting a module object.</span></span> <span data-ttu-id="9e930-149">새 모듈의 스크립트 블록은 함수를 정의한 `SayHello` 다음 함수를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e930-149">The script block in the new module defines the `SayHello` function and then calls the function.</span></span>

```powershell
New-Module -ScriptBlock {function SayHello {"Hello, World!"}; SayHello} -ReturnResult
```

```Output
Hello, World!
```

## <span data-ttu-id="9e930-150">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9e930-150">PARAMETERS</span></span>

### <span data-ttu-id="9e930-151">-ArgumentList</span><span class="sxs-lookup"><span data-stu-id="9e930-151">-ArgumentList</span></span>

<span data-ttu-id="9e930-152">스크립트 블록으로 전달 되는 매개 변수 값인 인수 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e930-152">Specifies an array of arguments which are parameter values that are passed to the script block.</span></span> <span data-ttu-id="9e930-153">**Argumentlist** 의 동작에 대 한 자세한 내용은 [about_Splatting](about/about_Splatting.md#splatting-with-arrays)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9e930-153">For more information about the behavior of **ArgumentList**, see [about_Splatting](about/about_Splatting.md#splatting-with-arrays).</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9e930-154">-AsCustomObject</span><span class="sxs-lookup"><span data-stu-id="9e930-154">-AsCustomObject</span></span>

<span data-ttu-id="9e930-155">이 cmdlet이 동적 모듈을 나타내는 사용자 지정 개체를 반환 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9e930-155">Indicates that this cmdlet returns a custom object that represents the dynamic module.</span></span> <span data-ttu-id="9e930-156">모듈 멤버는 사용자 지정 개체의 스크립트 메서드로 구현되지만 세션으로 가져오지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9e930-156">The module members are implemented as script methods of the custom object, but they are not imported into the session.</span></span> <span data-ttu-id="9e930-157">사용자 지정 개체를 변수에 저장하고 점 표기법을 사용하여 멤버를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e930-157">You can save the custom object in a variable and use dot notation to invoke the members.</span></span>

<span data-ttu-id="9e930-158">모듈에 이름이 같은 멤버가 여러 개 있는 경우 (예: 이름이 인 함수 및 변수) 사용자 지정 개체에서 각 이름을 가진 하나의 멤버에만 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e930-158">If the module has multiple members with the same name, such as a function and a variable that are both named A, only one member with each name can be accessed from the custom object.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9e930-159">-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="9e930-159">-Cmdlet</span></span>

<span data-ttu-id="9e930-160">이 cmdlet이 모듈에서 현재 세션으로 내보내는 cmdlet의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e930-160">Specifies an array of cmdlets that this cmdlet exports from the module into the current session.</span></span>
<span data-ttu-id="9e930-161">쉼표로 구분된 cmdlet 목록을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="9e930-161">Enter a comma-separated list of cmdlets.</span></span> <span data-ttu-id="9e930-162">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e930-162">Wildcard characters are permitted.</span></span> <span data-ttu-id="9e930-163">기본적으로 모듈의 모든 cmdlet을 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="9e930-163">By default, all cmdlets in the module are exported.</span></span>

<span data-ttu-id="9e930-164">스크립트 블록에서 cmdlet을 정의할 수는 없지만 동적 모듈이 이진 모듈에서 cmdlet을 가져오는 경우 동적 모듈에 cmdlet이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e930-164">You cannot define cmdlets in a script block, but a dynamic module can include cmdlets if it imports the cmdlets from a binary module.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9e930-165">-함수</span><span class="sxs-lookup"><span data-stu-id="9e930-165">-Function</span></span>

<span data-ttu-id="9e930-166">이 cmdlet이 모듈에서 현재 세션으로 내보내는 함수 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e930-166">Specifies an array of functions that this cmdlet exports from the module into the current session.</span></span>
<span data-ttu-id="9e930-167">쉼표로 구분된 함수 목록을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="9e930-167">Enter a comma-separated list of functions.</span></span> <span data-ttu-id="9e930-168">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e930-168">Wildcard characters are permitted.</span></span> <span data-ttu-id="9e930-169">기본적으로 모듈에 정의된 모든 함수를 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="9e930-169">By default, all functions defined in a module are exported.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="9e930-170">-Name</span><span class="sxs-lookup"><span data-stu-id="9e930-170">-Name</span></span>

<span data-ttu-id="9e930-171">새 모듈의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9e930-171">Specifies a name for the new module.</span></span> <span data-ttu-id="9e930-172">또한 모듈 이름을 New-Module로 파이프할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e930-172">You can also pipe a module name to New-Module.</span></span>

<span data-ttu-id="9e930-173">기본값은로 시작 하 여 `__DynamicModule_` 동적 모듈의 경로를 지정 하는 GUID가 뒤에 오는 자동 생성 된 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="9e930-173">The default value is an autogenerated name that starts with `__DynamicModule_` and is followed by a GUID that specifies the path of the dynamic module.</span></span>

```yaml
Type: System.String
Parameter Sets: Name
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="9e930-174">-ReturnResult</span><span class="sxs-lookup"><span data-stu-id="9e930-174">-ReturnResult</span></span>

<span data-ttu-id="9e930-175">이 cmdlet이 스크립트 블록을 실행 하 고 모듈 개체를 반환 하는 대신 스크립트 블록 결과를 반환 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9e930-175">Indicates that this cmdlet runs the script block and returns the script block results instead of returning a module object.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9e930-176">-ScriptBlock</span><span class="sxs-lookup"><span data-stu-id="9e930-176">-ScriptBlock</span></span>

<span data-ttu-id="9e930-177">동적 모듈의 내용을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9e930-177">Specifies the contents of the dynamic module.</span></span> <span data-ttu-id="9e930-178">내용을 중괄호 ()로 묶어 `{}` 스크립트 블록을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9e930-178">Enclose the contents in braces (`{}`) to create a script block.</span></span> <span data-ttu-id="9e930-179">이 매개 변수는 필수입니다.</span><span class="sxs-lookup"><span data-stu-id="9e930-179">This parameter is required.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9e930-180">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9e930-180">CommonParameters</span></span>

<span data-ttu-id="9e930-181">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9e930-181">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9e930-182">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9e930-182">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9e930-183">입력</span><span class="sxs-lookup"><span data-stu-id="9e930-183">INPUTS</span></span>

### <span data-ttu-id="9e930-184">System.String</span><span class="sxs-lookup"><span data-stu-id="9e930-184">System.String</span></span>

<span data-ttu-id="9e930-185">모듈 이름을이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e930-185">You can pipe a module name to this cmdlet.</span></span>

## <span data-ttu-id="9e930-186">출력</span><span class="sxs-lookup"><span data-stu-id="9e930-186">OUTPUTS</span></span>

### <span data-ttu-id="9e930-187">PSCustomObject 또는 None 중에서 하나를 일치 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9e930-187">System.Management.Automation.PSModuleInfo, System.Management.Automation.PSCustomObject, or None</span></span>

<span data-ttu-id="9e930-188">이 cmdlet은 기본적으로 **Psmoduleinfo** 개체를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e930-188">This cmdlet generates a **PSModuleInfo** object, by default.</span></span> <span data-ttu-id="9e930-189">**AsCustomObject** 매개 변수를 사용 하는 경우 **PSCustomObject** 개체를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e930-189">If you use the **AsCustomObject** parameter, it generates a **PSCustomObject** object.</span></span> <span data-ttu-id="9e930-190">**Returnresult** 매개 변수를 사용 하는 경우 동적 모듈의 스크립트 블록 평가 결과가 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e930-190">If you use the **ReturnResult** parameter, it returns the result of evaluating the script block in the dynamic module.</span></span>

## <span data-ttu-id="9e930-191">참고</span><span class="sxs-lookup"><span data-stu-id="9e930-191">NOTES</span></span>

<span data-ttu-id="9e930-192">별칭으로를 참조할 수도 있습니다 `New-Module` `nmo` .</span><span class="sxs-lookup"><span data-stu-id="9e930-192">You can also refer to `New-Module` by its alias, `nmo`.</span></span> <span data-ttu-id="9e930-193">자세한 내용은 [about_Aliases](About/about_Aliases.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9e930-193">For more information, see [about_Aliases](About/about_Aliases.md).</span></span>

## <span data-ttu-id="9e930-194">관련 링크</span><span class="sxs-lookup"><span data-stu-id="9e930-194">RELATED LINKS</span></span>

[<span data-ttu-id="9e930-195">Export-ModuleMember</span><span class="sxs-lookup"><span data-stu-id="9e930-195">Export-ModuleMember</span></span>](Export-ModuleMember.md)

[<span data-ttu-id="9e930-196">Get-Module</span><span class="sxs-lookup"><span data-stu-id="9e930-196">Get-Module</span></span>](Get-Module.md)

[<span data-ttu-id="9e930-197">모듈 가져오기</span><span class="sxs-lookup"><span data-stu-id="9e930-197">Import-Module</span></span>](Import-Module.md)

[<span data-ttu-id="9e930-198">Remove-Module</span><span class="sxs-lookup"><span data-stu-id="9e930-198">Remove-Module</span></span>](Remove-Module.md)
