---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 4/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/add-member?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-Member
ms.openlocfilehash: 8c27ebe1c5f1a0c53f5012f1faa17a9fdb1cdcff
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94391037"
---
# <span data-ttu-id="93cd9-103">Add-Member</span><span class="sxs-lookup"><span data-stu-id="93cd9-103">Add-Member</span></span>

## <span data-ttu-id="93cd9-104">개요</span><span class="sxs-lookup"><span data-stu-id="93cd9-104">SYNOPSIS</span></span>
<span data-ttu-id="93cd9-105">사용자 지정 속성 및 메서드를 PowerShell 개체의 인스턴스에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-105">Adds custom properties and methods to an instance of a PowerShell object.</span></span>

## <span data-ttu-id="93cd9-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="93cd9-106">SYNTAX</span></span>

### <span data-ttu-id="93cd9-107">TypeNameSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="93cd9-107">TypeNameSet (Default)</span></span>

```
Add-Member -InputObject <PSObject> -TypeName <String> [-PassThru] [<CommonParameters>]
```

### <span data-ttu-id="93cd9-108">참고 Propertymultimemberset</span><span class="sxs-lookup"><span data-stu-id="93cd9-108">NotePropertyMultiMemberSet</span></span>

```
Add-Member -InputObject <PSObject> [-TypeName <String>] [-Force] [-PassThru]
 [-NotePropertyMembers] <IDictionary> [<CommonParameters>]
```

### <span data-ttu-id="93cd9-109">NotePropertySingleMemberSet</span><span class="sxs-lookup"><span data-stu-id="93cd9-109">NotePropertySingleMemberSet</span></span>

```
Add-Member -InputObject <PSObject> [-TypeName <String>] [-Force] [-PassThru] [-NotePropertyName] <String>
 [-NotePropertyValue] <Object> [<CommonParameters>]
```

### <span data-ttu-id="93cd9-110">집합</span><span class="sxs-lookup"><span data-stu-id="93cd9-110">MemberSet</span></span>

```
Add-Member -InputObject <PSObject> [-MemberType] <PSMemberTypes> [-Name] <String> [[-Value] <Object>]
 [[-SecondValue] <Object>] [-TypeName <String>] [-Force] [-PassThru] [<CommonParameters>]
```

## <span data-ttu-id="93cd9-111">설명</span><span class="sxs-lookup"><span data-stu-id="93cd9-111">DESCRIPTION</span></span>

<span data-ttu-id="93cd9-112">`Add-Member`Cmdlet을 사용 하면 PowerShell 개체의 인스턴스에 멤버 (속성 및 메서드)를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-112">The `Add-Member` cmdlet lets you add members (properties and methods) to an instance of a PowerShell object.</span></span> <span data-ttu-id="93cd9-113">예를 들어 개체에 대 한 설명이 포함 된 메모 속성 멤버를 추가 하거나 스크립트를 실행 하 여 개체를 변경 하는 **ScriptMethod** 멤버를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-113">For instance, you can add a NoteProperty member that contains a description of the object or a **ScriptMethod** member that runs a script to change the object.</span></span>

<span data-ttu-id="93cd9-114">를 사용 하려면 `Add-Member` 개체를로 파이프 `Add-Member` 하거나 **InputObject** 매개 변수를 사용 하 여 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-114">To use `Add-Member`, pipe the object to `Add-Member`, or use the **InputObject** parameter to specify the object.</span></span>

<span data-ttu-id="93cd9-115">**MemberType** 매개 변수는 추가 하려는 멤버의 유형을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-115">The **MemberType** parameter indicates the type of member that you want to add.</span></span> <span data-ttu-id="93cd9-116">**Name** 매개 변수는 새 멤버에 이름을 할당 하 고 **value** 매개 변수는 멤버의 값을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-116">The **Name** parameter assigns a name to the new member, and the **Value** parameter sets the value of the member.</span></span>

<span data-ttu-id="93cd9-117">추가한 속성 및 메서드는 지정한 개체의 특정 인스턴스에만 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-117">The properties and methods that you add are added only to the particular instance of the object that you specify.</span></span> <span data-ttu-id="93cd9-118">`Add-Member` 는 개체 유형을 변경 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-118">`Add-Member` does not change the object type.</span></span> <span data-ttu-id="93cd9-119">새 개체 유형을 만들려면 cmdlet을 사용 `Add-Type` 합니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-119">To create a new object type, use the `Add-Type` cmdlet.</span></span>

<span data-ttu-id="93cd9-120">Cmdlet을 사용 하 여 `Export-Clixml` 추가 멤버를 비롯 한 개체의 인스턴스를 파일에 저장할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-120">You can also use the `Export-Clixml` cmdlet to save the instance of the object, including the additional members, in a file.</span></span> <span data-ttu-id="93cd9-121">그런 다음 cmdlet을 사용 `Import-Clixml` 하 여 내보낸 파일에 저장 된 정보에서 개체의 인스턴스를 다시 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-121">Then you can use the `Import-Clixml` cmdlet to re-create the instance of the object from the information that is stored in the exported file.</span></span>

<span data-ttu-id="93cd9-122">Windows PowerShell 3.0부터에는 `Add-Member` 개체에 메모 속성을 더 쉽게 추가할 수 있도록 하는 새로운 기능이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-122">Beginning in Windows PowerShell 3.0, `Add-Member` has new features that make it easier to add note properties to objects.</span></span>
<span data-ttu-id="93cd9-123">**NotePropertyName** 및 **NotePropertyValue** 매개 변수를 사용하여 메모 속성을 정의하거나 **NotePropertyMembers** 매개 변수를 사용하여 메모 속성 이름 및 값의 해시 테이블을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-123">You can use the **NotePropertyName** and **NotePropertyValue** parameters to define a note property or use the **NotePropertyMembers** parameter, which takes a hash table of note property names and values.</span></span>

<span data-ttu-id="93cd9-124">또한 Windows PowerShell 3.0부터는 출력 개체를 생성하는 **PassThru** 매개 변수의 필요성이 줄어듭니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-124">Also, beginning in Windows PowerShell 3.0, the **PassThru** parameter, which generates an output object, is needed less frequently.</span></span> <span data-ttu-id="93cd9-125">`Add-Member` 이제는 더 많은 형식의 입력 개체에 직접 새 멤버를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-125">`Add-Member` now adds the new members directly to the input object of more types.</span></span> <span data-ttu-id="93cd9-126">자세한 내용은 **PassThru** 매개 변수 설명을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="93cd9-126">For more information, see the **PassThru** parameter description.</span></span>

## <span data-ttu-id="93cd9-127">예제</span><span class="sxs-lookup"><span data-stu-id="93cd9-127">EXAMPLES</span></span>

### <span data-ttu-id="93cd9-128">예제 1: PSObject에 메모 속성 추가</span><span class="sxs-lookup"><span data-stu-id="93cd9-128">Example 1: Add a note property to a PSObject</span></span>

<span data-ttu-id="93cd9-129">다음 예에서는 값이 "Done" 인 **상태** 메모 속성을 파일을 나타내는 **FileInfo** 개체에 추가 합니다 `Test.txt` .</span><span class="sxs-lookup"><span data-stu-id="93cd9-129">The following example adds a **Status** note property with a value of "Done" to the **FileInfo** object that represents the `Test.txt` file.</span></span>

<span data-ttu-id="93cd9-130">첫 번째 명령은 cmdlet을 사용 하 여 `Get-ChildItem` 파일을 나타내는 **FileInfo** 개체를 가져옵니다 `Test.txt` .</span><span class="sxs-lookup"><span data-stu-id="93cd9-130">The first command uses the `Get-ChildItem` cmdlet to get a **FileInfo** object representing the `Test.txt` file.</span></span> <span data-ttu-id="93cd9-131">`$a`변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-131">It saves it in the `$a` variable.</span></span>

<span data-ttu-id="93cd9-132">두 번째 명령은 메모 속성을의 개체에 추가 합니다 `$a` .</span><span class="sxs-lookup"><span data-stu-id="93cd9-132">The second command adds the note property to the object in `$a`.</span></span>

<span data-ttu-id="93cd9-133">세 번째 명령은 점 표기법을 사용 하 여에서 개체의 **Status** 속성 값을 가져옵니다 `$a` .</span><span class="sxs-lookup"><span data-stu-id="93cd9-133">The third command uses dot notation to get the value of the **Status** property of the object in `$a`.</span></span> <span data-ttu-id="93cd9-134">출력에서 볼 수 있듯이 값은 "Done"입니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-134">As the output shows, the value is "Done".</span></span>

```powershell
$A = Get-ChildItem c:\ps-test\test.txt
$A | Add-Member -NotePropertyName Status -NotePropertyValue Done
$A.Status
```

```Output
Done
```

### <span data-ttu-id="93cd9-135">예제 2: PSObject에 별칭 속성 추가</span><span class="sxs-lookup"><span data-stu-id="93cd9-135">Example 2: Add an alias property to a PSObject</span></span>

<span data-ttu-id="93cd9-136">다음 예에서는 파일을 나타내는 개체에 **크기** 별칭 속성을 추가 합니다 `Test.txt` .</span><span class="sxs-lookup"><span data-stu-id="93cd9-136">The following example adds a **Size** alias property to the object that represents the `Test.txt` file.</span></span> <span data-ttu-id="93cd9-137">새 속성은 **Length** 속성에 대 한 별칭입니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-137">The new property is an alias for the **Length** property.</span></span>

<span data-ttu-id="93cd9-138">첫 번째 명령은 cmdlet을 사용 하 여 `Get-ChildItem` `Test.txt` **FileInfo** 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-138">The first command uses the `Get-ChildItem` cmdlet to get the `Test.txt` **FileInfo** object.</span></span>

<span data-ttu-id="93cd9-139">두 번째 명령은 **크기** 별칭 속성을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-139">The second command adds the **Size** alias property.</span></span>
<span data-ttu-id="93cd9-140">세 번째 명령은 점 표기법을 사용 하 여 새 **크기** 속성의 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-140">The third command uses dot notation to get the value of the new **Size** property.</span></span>

```powershell
$A = Get-ChildItem C:\Temp\test.txt
$A | Add-Member -MemberType AliasProperty -Name Size -Value Length
$A.Size
```

```Output
2394
```

### <span data-ttu-id="93cd9-141">예제 3: 문자열에 StringUse 메모 속성 추가</span><span class="sxs-lookup"><span data-stu-id="93cd9-141">Example 3: Add a StringUse note property to a string</span></span>

<span data-ttu-id="93cd9-142">이 예에서는 문자열에 **Stringuse** note 속성을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-142">This example adds the **StringUse** note property to a string.</span></span>
<span data-ttu-id="93cd9-143">는 `Add-Member` **문자열** 입력 개체에 형식을 추가할 수 없으므로 **PassThru** 매개 변수를 지정 하 여 출력 개체를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-143">Because `Add-Member` cannot add types to **String** input objects, you can specify the **PassThru** parameter to generate an output object.</span></span> <span data-ttu-id="93cd9-144">예제의 마지막 명령은 새 속성을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-144">The last command in the example displays the new property.</span></span>

<span data-ttu-id="93cd9-145">이 예에서는 **참고 Propertymembers** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-145">This example uses the **NotePropertyMembers** parameter.</span></span> <span data-ttu-id="93cd9-146">**NotePropertyMembers** 매개 변수 값은 해시 테이블입니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-146">The value of the **NotePropertyMembers** parameter is a hash table.</span></span> <span data-ttu-id="93cd9-147">키는 메모 속성 이름인 **Stringuse** 이 고 값은 메모 속성 값인 **Display** 입니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-147">The key is the note property name, **StringUse** , and the value is the note property value, **Display**.</span></span>

```powershell
$A = "A string"
$A = $A | Add-Member -NotePropertyMembers @{StringUse="Display"} -PassThru
$A.StringUse
```

```Output
Display
```

### <span data-ttu-id="93cd9-148">예제 4: FileInfo 개체에 스크립트 메서드 추가</span><span class="sxs-lookup"><span data-stu-id="93cd9-148">Example 4: Add a script method to a FileInfo object</span></span>

<span data-ttu-id="93cd9-149">이 예에서는 파일 크기를 가장 가까운 메가바이트 수로 계산 하는 **FileInfo** 개체에 **sizeinmb** 스크립트 메서드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-149">This example adds the **SizeInMB** script method to a **FileInfo** object which calculates the file size to the nearest MegaByte.</span></span> <span data-ttu-id="93cd9-150">두 번째 명령은 형식의 **round** 정적 메서드를 사용 하 여 **ScriptBlock** `[math]` 파일 크기를 두 번째 소수 자리로 반올림 하는 ScriptBlock을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-150">The second command creates a **ScriptBlock** that uses the **Round** static method from the `[math]` type to round the file size to the second decimal place.</span></span>

<span data-ttu-id="93cd9-151">또한 **Value** 매개 변수는 `$This` 현재 개체를 나타내는 자동 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-151">The **Value** parameter also uses the `$This` automatic variable, which represents the current object.</span></span> <span data-ttu-id="93cd9-152">`$This`변수는 새 속성 및 메서드를 정의 하는 스크립트 블록 에서만 유효 합니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-152">The `$This` variable is valid only in script blocks that define new properties and methods.</span></span>

<span data-ttu-id="93cd9-153">마지막 명령은 점 표기법을 사용 하 여 변수의 개체에서 새 **Sizeinmb** 스크립트 메서드를 호출 합니다 `$A` .</span><span class="sxs-lookup"><span data-stu-id="93cd9-153">The last command uses dot notation to call the new **SizeInMB** script method on the object in the `$A` variable.</span></span>

```powershell
$A = Get-ChildItem C:\Temp\test.txt
$S = {[math]::Round(($this.Length / 1MB), 2)}
$A | Add-Member -MemberType ScriptMethod -Name "SizeInMB" -Value $S
$A.SizeInMB()
```

```Output
0.43
```

### <span data-ttu-id="93cd9-154">예제 5: 개체의 모든 속성을 다른 개체에 복사</span><span class="sxs-lookup"><span data-stu-id="93cd9-154">Example 5: Copy all properties of an object to another</span></span>

<span data-ttu-id="93cd9-155">이 함수는 한 개체의 모든 속성을 다른 개체에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-155">This function copies all of the properties of one object to another object.</span></span>

<span data-ttu-id="93cd9-156">루프는 cmdlet을 사용 하 여 `foreach` `Get-Member` **From** 개체의 각 속성을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-156">The `foreach` loop uses the `Get-Member` cmdlet to get each of the properties of the **From** object.</span></span> <span data-ttu-id="93cd9-157">루프 내의 명령은 `foreach` 각 속성에서 계열로 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-157">The commands within the `foreach` loop are performed in series on each of the properties.</span></span>

<span data-ttu-id="93cd9-158">이 `Add-Member` 명령은 **From** 개체의 속성을 **To** 개체에 **메모 속성** 으로 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-158">The `Add-Member` command adds the property of the **From** object to the **To** object as a **NoteProperty**.</span></span> <span data-ttu-id="93cd9-159">값은 **value** 매개 변수를 사용 하 여 복사 됩니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-159">The value is copied using the **Value** parameter.</span></span> <span data-ttu-id="93cd9-160">**Force** 매개 변수를 사용 하 여 멤버 이름이 같은 멤버를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-160">It uses the **Force** parameter to add members with the same member name.</span></span>

```powershell
function Copy-Property ($From, $To)
{
    $properties = Get-Member -InputObject $From -MemberType Property
    foreach ($p in $properties)
    {
        $To | Add-Member -MemberType NoteProperty -Name $p.Name -Value $From.$($p.Name) -Force
    }
}
```

### <span data-ttu-id="93cd9-161">예제 6: 사용자 지정 개체 만들기</span><span class="sxs-lookup"><span data-stu-id="93cd9-161">Example 6: Create a custom object</span></span>

<span data-ttu-id="93cd9-162">이 예제에서는 **Asset** 사용자 지정 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-162">This example creates an **Asset** custom object.</span></span>

<span data-ttu-id="93cd9-163">이 `New-Object` cmdlet은 **PSObject** 를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-163">The `New-Object` cmdlet creates a **PSObject**.</span></span> <span data-ttu-id="93cd9-164">이 예에서는 **PSObject** 를 변수에 저장 합니다 `$Asset` .</span><span class="sxs-lookup"><span data-stu-id="93cd9-164">The example saves the **PSObject** in the `$Asset` variable.</span></span>

<span data-ttu-id="93cd9-165">두 번째 명령은 형식 액셀러레이터를 사용 하 여 `[ordered]` 이름 및 값의 정렬 된 사전을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-165">The second command uses the `[ordered]` type accelerator to create an ordered dictionary of names and values.</span></span> <span data-ttu-id="93cd9-166">이 명령은 결과를 `$D` 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-166">The command saves the result in the `$D` variable.</span></span>

<span data-ttu-id="93cd9-167">세 번째 명령은 cmdlet의 **참고 Propertymembers** 매개 변수를 사용 하 여 `Add-Member` `$D` 변수의 사전을 **PSObject** 에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-167">The third command uses the **NotePropertyMembers** parameter of the `Add-Member` cmdlet to add the dictionary in the `$D` variable to the **PSObject**.</span></span>
<span data-ttu-id="93cd9-168">**TypeName** 속성은 새 이름인 **Asset** 를 **PSObject** 에 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-168">The **TypeName** property assigns a new name, **Asset** , to the **PSObject**.</span></span>

<span data-ttu-id="93cd9-169">마지막 명령은 새 **자산** 개체를 cmdlet으로 파이프 합니다 `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="93cd9-169">The last command pipes the new **Asset** object to the `Get-Member` cmdlet.</span></span> <span data-ttu-id="93cd9-170">출력은 개체에 **자산의** 형식 이름과 정렬 된 사전에 정의한 메모 속성이 있음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-170">The output shows that the object has a type name of **Asset** and the note properties that we defined in the ordered dictionary.</span></span>

```powershell
$Asset = New-Object -TypeName PSObject
$d = [ordered]@{Name="Server30";System="Server Core";PSVersion="4.0"}
$Asset | Add-Member -NotePropertyMembers $d -TypeName Asset
$Asset | Get-Member
```

```Output
   TypeName: Asset

Name        MemberType   Definition
----        ----------   ----------
Equals      Method       bool Equals(System.Object obj)
GetHashCode Method       int GetHashCode()
GetType     Method       type GetType()
ToString    Method       string ToString()
Name        NoteProperty System.String Name=Server30
PSVersion   NoteProperty System.String PSVersion=4.0
System      NoteProperty System.String System=Server Core
```

## <span data-ttu-id="93cd9-171">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="93cd9-171">PARAMETERS</span></span>

### <span data-ttu-id="93cd9-172">-Force</span><span class="sxs-lookup"><span data-stu-id="93cd9-172">-Force</span></span>

<span data-ttu-id="93cd9-173">개체에 이름이 같은 사용자 지정 멤버가 있는 경우에도이 cmdlet이 새 멤버를 추가 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-173">Indicates that this cmdlet adds a new member even the object has a custom member with the same name.</span></span>
<span data-ttu-id="93cd9-174">**Force** 매개 변수를 사용 하 여 형식의 표준 멤버를 바꿀 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-174">You cannot use the **Force** parameter to replace a standard member of a type.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NotePropertyMultiMemberSet, NotePropertySingleMemberSet, MemberSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="93cd9-175">-InputObject</span><span class="sxs-lookup"><span data-stu-id="93cd9-175">-InputObject</span></span>

<span data-ttu-id="93cd9-176">새 멤버를 추가할 개체를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-176">Specifies the object to which the new member is added.</span></span>
<span data-ttu-id="93cd9-177">개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="93cd9-177">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="93cd9-178">-MemberType</span><span class="sxs-lookup"><span data-stu-id="93cd9-178">-MemberType</span></span>

<span data-ttu-id="93cd9-179">추가할 멤버의 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-179">Specifies the type of the member to add.</span></span>
<span data-ttu-id="93cd9-180">이 매개 변수는 필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-180">This parameter is required.</span></span>
<span data-ttu-id="93cd9-181">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-181">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="93cd9-182">NoteProperty</span><span class="sxs-lookup"><span data-stu-id="93cd9-182">NoteProperty</span></span>
- <span data-ttu-id="93cd9-183">AliasProperty</span><span class="sxs-lookup"><span data-stu-id="93cd9-183">AliasProperty</span></span>
- <span data-ttu-id="93cd9-184">ScriptProperty</span><span class="sxs-lookup"><span data-stu-id="93cd9-184">ScriptProperty</span></span>
- <span data-ttu-id="93cd9-185">CodeProperty</span><span class="sxs-lookup"><span data-stu-id="93cd9-185">CodeProperty</span></span>
- <span data-ttu-id="93cd9-186">ScriptMethod</span><span class="sxs-lookup"><span data-stu-id="93cd9-186">ScriptMethod</span></span>
- <span data-ttu-id="93cd9-187">CodeMethod</span><span class="sxs-lookup"><span data-stu-id="93cd9-187">CodeMethod</span></span>

<span data-ttu-id="93cd9-188">이러한 값에 대 한 자세한 내용은 PowerShell SDK의 [PSMemberTypes 열거](/dotnet/api/system.management.automation.psmembertypes) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="93cd9-188">For information about these values, see [PSMemberTypes Enumeration](/dotnet/api/system.management.automation.psmembertypes) in the PowerShell SDK.</span></span>

<span data-ttu-id="93cd9-189">모든 개체가 모든 멤버 유형을 포함하는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-189">Not all objects have every type of member.</span></span>
<span data-ttu-id="93cd9-190">개체에 포함 되지 않은 멤버 유형을 지정 하면 PowerShell에서 오류를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-190">If you specify a member type that the object does not have, PowerShell returns an error.</span></span>

```yaml
Type: System.Management.Automation.PSMemberTypes
Parameter Sets: MemberSet
Aliases: Type
Accepted values: AliasProperty, CodeProperty, Property, NoteProperty, ScriptProperty, Properties, PropertySet, Method, CodeMethod, ScriptMethod, Methods, ParameterizedProperty, MemberSet, Event, Dynamic, All

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="93cd9-191">-Name</span><span class="sxs-lookup"><span data-stu-id="93cd9-191">-Name</span></span>

<span data-ttu-id="93cd9-192">이 cmdlet이 추가 하는 멤버의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-192">Specifies the name of the member that this cmdlet adds.</span></span>

```yaml
Type: System.String
Parameter Sets: MemberSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="93cd9-193">-참고 Propertymembers</span><span class="sxs-lookup"><span data-stu-id="93cd9-193">-NotePropertyMembers</span></span>

<span data-ttu-id="93cd9-194">메모 속성 이름 및 값의 해시 테이블 또는 순서가 지정된 사전을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-194">Specifies a hash table or ordered dictionary of note property names and values.</span></span>
<span data-ttu-id="93cd9-195">키는 메모 속성 이름이고 값은 메모 속성 값인 해시 테이블이나 사전을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-195">Type a hash table or dictionary in which the keys are note property names and the values are note property values.</span></span>

<span data-ttu-id="93cd9-196">PowerShell의 해시 테이블 및 순서가 지정 된 사전에 대 한 자세한 내용은 [about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="93cd9-196">For more information about hash tables and ordered dictionaries in PowerShell, see [about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md).</span></span>

<span data-ttu-id="93cd9-197">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-197">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Collections.IDictionary
Parameter Sets: NotePropertyMultiMemberSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="93cd9-198">-참고 Propertyname</span><span class="sxs-lookup"><span data-stu-id="93cd9-198">-NotePropertyName</span></span>

<span data-ttu-id="93cd9-199">메모 속성 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-199">Specifies the note property name.</span></span>

<span data-ttu-id="93cd9-200">이 매개 변수는 **NotePropertyValue** 매개 변수와 함께 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-200">Use this parameter with the **NotePropertyValue** parameter.</span></span>
<span data-ttu-id="93cd9-201">이 매개 변수는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-201">This parameter is optional.</span></span>

<span data-ttu-id="93cd9-202">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-202">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: NotePropertySingleMemberSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="93cd9-203">-참고 Propertyvalue</span><span class="sxs-lookup"><span data-stu-id="93cd9-203">-NotePropertyValue</span></span>

<span data-ttu-id="93cd9-204">메모 속성 값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-204">Specifies the note property value.</span></span>

<span data-ttu-id="93cd9-205">이 매개 변수는 **메모 propertyname** 매개 변수와 함께 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-205">Use this parameter with the **NotePropertyName** parameter.</span></span>
<span data-ttu-id="93cd9-206">이 매개 변수는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-206">This parameter is optional.</span></span>

<span data-ttu-id="93cd9-207">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-207">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Object
Parameter Sets: NotePropertySingleMemberSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="93cd9-208">-PassThru</span><span class="sxs-lookup"><span data-stu-id="93cd9-208">-PassThru</span></span>

<span data-ttu-id="93cd9-209">작업 중인 항목을 나타내는 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-209">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="93cd9-210">기본적으로 이 cmdlet은 출력을 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-210">By default, this cmdlet does not generate any output.</span></span>

<span data-ttu-id="93cd9-211">대부분의 개체에 대해는 `Add-Member` 입력 개체에 새 멤버를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-211">For most objects, `Add-Member` adds the new members to the input object.</span></span>
<span data-ttu-id="93cd9-212">그러나 입력 개체가 문자열이 면는 `Add-Member` 입력 개체에 멤버를 추가할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-212">However, when the input object is a string, `Add-Member` cannot add the member to the input object.</span></span>
<span data-ttu-id="93cd9-213">이러한 개체의 경우 **PassThru** 매개 변수를 사용하여 출력 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-213">For these objects, use the **PassThru** parameter to create an output object.</span></span>

<span data-ttu-id="93cd9-214">Windows PowerShell 2.0에서 `Add-Member` 개체가 아닌 개체의 **PSObject** 래퍼로 멤버를 추가 했습니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-214">In Windows PowerShell 2.0, `Add-Member` added members only to the **PSObject** wrapper of objects, not to the object.</span></span>
<span data-ttu-id="93cd9-215">**PassThru** 매개 변수를 사용 하 여 **PSObject** 래퍼가 있는 모든 개체에 대 한 출력 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-215">Use the **PassThru** parameter to create an output object for any object that has a **PSObject** wrapper.</span></span>

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

### <span data-ttu-id="93cd9-216">-SecondValue</span><span class="sxs-lookup"><span data-stu-id="93cd9-216">-SecondValue</span></span>

<span data-ttu-id="93cd9-217">**AliasProperty** , **ScriptProperty** , **CodeProperty** 또는 **CodeMethod** 멤버에 대한 선택적 추가 정보를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-217">Specifies optional additional information about **AliasProperty** , **ScriptProperty** , **CodeProperty** , or **CodeMethod** members.</span></span>

<span data-ttu-id="93cd9-218">**AliasProperty** 를 추가할 때 사용 하는 경우이 매개 변수는 데이터 형식 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-218">If used when adding an **AliasProperty** , this parameter must be a data type.</span></span>
<span data-ttu-id="93cd9-219">지정 된 데이터 형식으로의 변환은 **AliasProperty** 의 값에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-219">A conversion to the specified data type is added to the value of the **AliasProperty**.</span></span>

<span data-ttu-id="93cd9-220">예를 들어 문자열 속성에 대 한 대체 이름을 제공 하는 **AliasProperty** 을 추가 하는 경우 해당 **AliasProperty** 를 사용 하 여 액세스할 때 해당 문자열 속성의 값이 정수로 변환 되어야 함을 나타내도록 **SecondValue의** 매개 변수를 지정할 수도 **있습니다.**</span><span class="sxs-lookup"><span data-stu-id="93cd9-220">For example, if you add an **AliasProperty** that provides an alternate name for a string property, you can also specify a **SecondValue** parameter of **System.Int32** to indicate that the value of that string property should be converted to an integer when accessed by using the corresponding **AliasProperty**.</span></span>

<span data-ttu-id="93cd9-221">**Scriptproperty** 멤버를 추가할 때 **SecondValue** 매개 변수를 사용 하 여 추가 **ScriptBlock** 을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-221">You can use the **SecondValue** parameter to specify an additional **ScriptBlock** when adding a **ScriptProperty** member.</span></span> <span data-ttu-id="93cd9-222">**값** 매개 변수에 지정 된 첫 번째 **ScriptBlock** 은 변수의 값을 가져오는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-222">The first **ScriptBlock** , specified in the **Value** parameter, is used to get the value of a variable.</span></span> <span data-ttu-id="93cd9-223">**SecondValue** 매개 변수에 지정 된 두 번째 **ScriptBlock** 은 변수의 값을 설정 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-223">The second **ScriptBlock** , specified in the **SecondValue** parameter, is used to set the value of a variable.</span></span>

```yaml
Type: System.Object
Parameter Sets: MemberSet
Aliases:

Required: False
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="93cd9-224">-Value</span><span class="sxs-lookup"><span data-stu-id="93cd9-224">-Value</span></span>

<span data-ttu-id="93cd9-225">추가된 멤버의 초기값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-225">Specifies the initial value of the added member.</span></span>
<span data-ttu-id="93cd9-226">**AliasProperty** , **codeproperty** , **scriptproperty** 또는 **codeproperty** 멤버를 추가 하는 경우 **SecondValue** 매개 변수를 사용 하 여 선택적 추가 정보를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-226">If you add an **AliasProperty** , **CodeProperty** , **ScriptProperty** or **CodeMethod** member, you can supply optional, additional information by using the **SecondValue** parameter.</span></span>

```yaml
Type: System.Object
Parameter Sets: MemberSet
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="93cd9-227">-TypeName</span><span class="sxs-lookup"><span data-stu-id="93cd9-227">-TypeName</span></span>

<span data-ttu-id="93cd9-228">형식의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-228">Specifies a name for the type.</span></span>

<span data-ttu-id="93cd9-229">형식이 **시스템** 네임 스페이스의 클래스 이거나 형식이 액셀러레이터 인 형식이 면 형식의 짧은 이름을 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-229">When the type is a class in the **System** namespace or a type that has a type accelerator, you can enter the short name of the type.</span></span> <span data-ttu-id="93cd9-230">그러지 않으면 전체 유형 이름이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-230">Otherwise, the full type name is required.</span></span>
<span data-ttu-id="93cd9-231">이 매개 변수는 **InputObject** 가 **PSObject** 인 경우에만 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-231">This parameter is effective only when the **InputObject** is a **PSObject**.</span></span>

<span data-ttu-id="93cd9-232">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-232">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: TypeNameSet, NotePropertyMultiMemberSet, NotePropertySingleMemberSet, MemberSet
Aliases:

Required: True (TypeNameSet), False (NotePropertyMultiMemberSet, NotePropertySingleMemberSet, MemberSet)
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="93cd9-233">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="93cd9-233">CommonParameters</span></span>

<span data-ttu-id="93cd9-234">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="93cd9-234">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="93cd9-235">자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="93cd9-235">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="93cd9-236">입력</span><span class="sxs-lookup"><span data-stu-id="93cd9-236">INPUTS</span></span>

### <span data-ttu-id="93cd9-237">System.web. PSObject</span><span class="sxs-lookup"><span data-stu-id="93cd9-237">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="93cd9-238">모든 개체 형식을이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-238">You can pipe any object type to this cmdlet.</span></span>

## <span data-ttu-id="93cd9-239">출력</span><span class="sxs-lookup"><span data-stu-id="93cd9-239">OUTPUTS</span></span>

### <span data-ttu-id="93cd9-240">None 또는 System.object</span><span class="sxs-lookup"><span data-stu-id="93cd9-240">None or System.Object</span></span>

<span data-ttu-id="93cd9-241">**PassThru** 매개 변수를 사용 하는 경우이 cmdlet은 새로 확장 된 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-241">When you use the **PassThru** parameter, this cmdlet returns the newly-extended object.</span></span>
<span data-ttu-id="93cd9-242">그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-242">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="93cd9-243">참고</span><span class="sxs-lookup"><span data-stu-id="93cd9-243">NOTES</span></span>

<span data-ttu-id="93cd9-244">**PSObject** 개체에만 멤버를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-244">You can add members only to **PSObject** objects.</span></span> <span data-ttu-id="93cd9-245">개체가 **PSObject** 개체 인지 여부를 확인 하려면 연산자를 사용 `-is` 합니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-245">To determine whether an object is a **PSObject** object, use the `-is` operator.</span></span>

<span data-ttu-id="93cd9-246">예를 들어 변수에 저장 된 개체를 테스트 하려면 `$obj` 을 입력 `$obj -is [PSObject]` 합니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-246">For instance, to test an object stored in the `$obj` variable, type `$obj -is [PSObject]`.</span></span>

<span data-ttu-id="93cd9-247">**MemberType** , **Name** , **Value** 및 **SecondValue** 매개 변수의 이름은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-247">The names of the **MemberType** , **Name** , **Value** , and **SecondValue** parameters are optional.</span></span>
<span data-ttu-id="93cd9-248">매개 변수 이름을 생략 하는 경우 명명 되지 않은 매개 변수 값은 **MemberType** , **Name** , **Value** 및 **SecondValue** 순서로 표시 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-248">If you omit the parameter names, the unnamed parameter values must appear in this order: **MemberType** , **Name** , **Value** , and **SecondValue**.</span></span>

<span data-ttu-id="93cd9-249">매개 변수 이름을 포함할 경우 원하는 순서대로 매개 변수를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-249">If you include the parameter names, the parameters can appear in any order.</span></span>

<span data-ttu-id="93cd9-250">`$this`새 속성 및 메서드의 값을 정의 하는 스크립트 블록에서 자동 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-250">You can use the `$this` automatic variable in script blocks that define the values of new properties and methods.</span></span>
<span data-ttu-id="93cd9-251">`$this`변수는 속성 및 메서드가 추가 되는 개체의 인스턴스를 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="93cd9-251">The `$this` variable refers to the instance of the object to which the properties and methods are being added.</span></span> <span data-ttu-id="93cd9-252">변수에 대 한 자세한 내용은 `$this` [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="93cd9-252">For more information about the `$this` variable, see [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md).</span></span>

## <span data-ttu-id="93cd9-253">관련 링크</span><span class="sxs-lookup"><span data-stu-id="93cd9-253">RELATED LINKS</span></span>

[<span data-ttu-id="93cd9-254">Export-Clixml</span><span class="sxs-lookup"><span data-stu-id="93cd9-254">Export-Clixml</span></span>](Export-Clixml.md)

[<span data-ttu-id="93cd9-255">Get-Member</span><span class="sxs-lookup"><span data-stu-id="93cd9-255">Get-Member</span></span>](Get-Member.md)

[<span data-ttu-id="93cd9-256">Import-Clixml</span><span class="sxs-lookup"><span data-stu-id="93cd9-256">Import-Clixml</span></span>](Import-Clixml.md)

[<span data-ttu-id="93cd9-257">New-Object</span><span class="sxs-lookup"><span data-stu-id="93cd9-257">New-Object</span></span>](New-Object.md)

[<span data-ttu-id="93cd9-258">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="93cd9-258">about_Automatic_Variables</span></span>](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)
