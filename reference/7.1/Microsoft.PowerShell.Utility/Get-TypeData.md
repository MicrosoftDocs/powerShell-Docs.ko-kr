---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-typedata?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-TypeData
ms.openlocfilehash: 0a935f03e479ed84fa8167f7c4c29e91bd774009
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93213018"
---
# <span data-ttu-id="5520b-103">Get-TypeData</span><span class="sxs-lookup"><span data-stu-id="5520b-103">Get-TypeData</span></span>

## <span data-ttu-id="5520b-104">개요</span><span class="sxs-lookup"><span data-stu-id="5520b-104">Synopsis</span></span>
<span data-ttu-id="5520b-105">현재 세션에 있는 확장 유형 데이터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="5520b-105">Gets the extended type data in the current session.</span></span>

## <span data-ttu-id="5520b-106">구문</span><span class="sxs-lookup"><span data-stu-id="5520b-106">Syntax</span></span>

```
Get-TypeData [[-TypeName] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="5520b-107">Description</span><span class="sxs-lookup"><span data-stu-id="5520b-107">Description</span></span>

<span data-ttu-id="5520b-108">`Get-TypeData`Cmdlet은 현재 세션에 있는 확장 유형 데이터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="5520b-108">The `Get-TypeData` cmdlet gets the extended type data in the current session.</span></span> <span data-ttu-id="5520b-109">여기에는 `Types.ps1xml` cmdlet의 매개 변수를 사용 하 여 추가 된 파일 및 동적 형식 데이터에 의해 세션에 추가 된 유형 데이터가 포함 됩니다 `Update-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="5520b-109">This includes type data that was added to the session by `Types.ps1xml` file and dynamic type data that was added by using the parameter of the `Update-TypeData` cmdlet.</span></span>

<span data-ttu-id="5520b-110">에서 반환 하는 확장 형식 데이터를 사용 하 여 `Get-TypeData` 세션의 형식 데이터를 검사 하 고이를 및 cmdlet으로 보낼 수 있습니다 `Update-TypeData` `Remove-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="5520b-110">You can use the extended type data that `Get-TypeData` returns to examine the type data in the session and send it to the `Update-TypeData` and `Remove-TypeData` cmdlets.</span></span>

<span data-ttu-id="5520b-111">확장 유형 데이터는 PowerShell의 개체에 속성과 메서드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="5520b-111">Extended type data adds properties and methods to objects in PowerShell.</span></span> <span data-ttu-id="5520b-112">개체 유형에 정의된 속성 및 메서드와 동일한 방식으로 추가된 속성과 메서드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5520b-112">You can use the added properties and methods in the same ways that you would use the properties and methods that are defined in the object type.</span></span> <span data-ttu-id="5520b-113">그러나 스크립트를 작성할 때 추가 된 속성 및 메서드는 모든 PowerShell 세션에 표시 되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5520b-113">However, when writing scripts, be aware that the added properties and methods might not be present in every PowerShell session.</span></span>

<span data-ttu-id="5520b-114">파일에 대 한 자세한 내용은 `Types.ps1xml` [about_Types.ps1xml](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5520b-114">For more information about `Types.ps1xml` files, see [about_Types.ps1xml](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md).</span></span> <span data-ttu-id="5520b-115">Cmdlet에서 추가 하는 동적 형식 데이터에 대 한 자세한 내용은 `Update-TypeData` 을 참조 하십시오 `Update-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="5520b-115">For more information about dynamic type data that the `Update-TypeData` cmdlet adds, see `Update-TypeData`.</span></span>

<span data-ttu-id="5520b-116">이 cmdlet은 Windows PowerShell 3.0에서 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="5520b-116">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="5520b-117">예</span><span class="sxs-lookup"><span data-stu-id="5520b-117">Examples</span></span>

### <span data-ttu-id="5520b-118">예제 1: 모든 확장 형식 데이터 가져오기</span><span class="sxs-lookup"><span data-stu-id="5520b-118">Example 1: Get all extended type data</span></span>

<span data-ttu-id="5520b-119">이 예에서는 현재 세션에 있는 모든 확장 유형 데이터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="5520b-119">This example gets all extended type data in the current session.</span></span>

 ```powershell
Get-TypeData
```

### <span data-ttu-id="5520b-120">예제 2: 이름을 기준으로 형식 가져오기</span><span class="sxs-lookup"><span data-stu-id="5520b-120">Example 2: Get types by name</span></span>

<span data-ttu-id="5520b-121">이 예제에서는 현재 세션에서 이벤트를 포함 하는 이름을 가진 모든 형식을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="5520b-121">This example gets all types in the current session that have names that contain Eventing.</span></span>

 ```powershell
"*Eventing*" | Get-TypeData
```

```Output
TypeName                                                  Members
--------                                                  -------
System.Diagnostics.Eventing.Reader.EventLogConfiguration  {}System.Diagnostics.Eventing.Reader.EventLogRecord
                                                          {}System.Diagnostics.Eventing.Reader.ProviderMetadata
                                                          {[ProviderName, System.Management.Automation.Runspaces.AliasProper...
```

### <span data-ttu-id="5520b-122">예제 3: 속성 값을 만드는 스크립트 블록 가져오기</span><span class="sxs-lookup"><span data-stu-id="5520b-122">Example 3: Get the script block that creates a property value</span></span>

<span data-ttu-id="5520b-123">이 예제에서는 **EventLogEntry** 개체의 **EventID** 속성 값을 만드는 스크립트 블록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="5520b-123">This example gets the script block that creates the value of the **EventID** property of **EventLogEntry** objects.</span></span>

 ```powershell
(Get-TypeData *EventLogEntry*).Members.EventID
```

```Output
GetScriptBlock                     SetScriptBlock     IsHidden Name
--------------                     --------------     -------- ----
$this.get_EventID() -band 0xFFFF                         False EventID
```

### <span data-ttu-id="5520b-124">예제 4: 지정 된 개체에 대 한 속성을 정의 하는 스크립트 블록 가져오기</span><span class="sxs-lookup"><span data-stu-id="5520b-124">Example 4: Get the script block that defines a property for a specified object</span></span>

<span data-ttu-id="5520b-125">이 예제에서는 PowerShell에서 **system.string 개체의** **datetime** 속성을 정의 하는 스크립트 블록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="5520b-125">This example gets the script block that defines the **DateTime** property of **System.DateTime** objects in PowerShell.</span></span>

 ```powershell
(Get-TypeData -TypeName System.DateTime).Members["DateTime"].GetScriptBlock
if ((& { Set-StrictMode -Version 1; $this.DisplayHint }) -ieq  "Date") {
    "{0}" -f $this.ToLongDateString()
}
elseif ((& { Set-StrictMode -Version 1; $this.DisplayHint }) -ieq "Time") {
    "{0}" -f  $this.ToLongTimeString()
}
else {
    "{0} {1}" -f $this.ToLongDateString(), $this.ToLongTimeString()
}
```

<span data-ttu-id="5520b-126">이 명령은 cmdlet을 사용 하 여 `Get-TypeData` **DataTime** 유형에 대 한 확장 유형 데이터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="5520b-126">The command uses the `Get-TypeData` cmdlet to get the extended type data for the **System.DataTime** type.</span></span> <span data-ttu-id="5520b-127">또한 **TypeData** 개체의 **Members** 속성을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="5520b-127">The command gets the **Members** property of the **TypeData** object.</span></span>

<span data-ttu-id="5520b-128">**Members** 속성에는 확장 형식 데이터로 정의 된 속성 및 메서드의 해시 테이블이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5520b-128">The **Members** property contains a hash table of properties and methods that are defined by extended type data.</span></span> <span data-ttu-id="5520b-129">Members 해시 테이블의 각 키는 속성 또는 메서드 이름이고 각 값은 속성 또는 메서드 값의 정의입니다.</span><span class="sxs-lookup"><span data-stu-id="5520b-129">Each key in the Members hash table is a property or method name and each value is the definition of the property or method value.</span></span>

<span data-ttu-id="5520b-130">이 명령은 **멤버** 의 **DateTime** 키와 해당 **getscriptblock** 속성 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="5520b-130">The command gets the **DateTime** key in **Members** and its **GetScriptBlock** property value.</span></span>

<span data-ttu-id="5520b-131">출력은 PowerShell **에서 모든 system.string** 개체의 **datetime** 속성 값을 만드는 스크립트 블록을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5520b-131">The output shows the script block that creates the value of the **DateTime** property of every **System.DateTime** object in PowerShell.</span></span>

## <span data-ttu-id="5520b-132">매개 변수</span><span class="sxs-lookup"><span data-stu-id="5520b-132">Parameters</span></span>

### <span data-ttu-id="5520b-133">-TypeName</span><span class="sxs-lookup"><span data-stu-id="5520b-133">-TypeName</span></span>

<span data-ttu-id="5520b-134">지정 된 이름을 가진 형식에 대 한 배열로만 형식 데이터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5520b-134">Specifies type data as an array only for the types with the specified names.</span></span> <span data-ttu-id="5520b-135">기본적으로 `Get-TypeData` 세션의 모든 형식을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="5520b-135">By default, `Get-TypeData` gets all types in the session.</span></span>

<span data-ttu-id="5520b-136">유형 이름 또는 이름 패턴을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="5520b-136">Enter type names or a name patterns.</span></span> <span data-ttu-id="5520b-137">시스템 네임 스페이스의 형식에 대해서도 전체 이름 또는 와일드 카드 문자가 포함 된 이름 패턴이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="5520b-137">Full names, or name patterns with wildcard characters are required, even for types in the System namespace.</span></span> <span data-ttu-id="5520b-138">와일드 카드가 지원 되며 매개 변수 이름 **TypeName** 은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="5520b-138">Wildcards are supported and the parameter name **TypeName** is optional.</span></span> <span data-ttu-id="5520b-139">형식 이름을로 파이프 할 수도 있습니다 `Get-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="5520b-139">You can also pipe type names to `Get-TypeData`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="5520b-140">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5520b-140">CommonParameters</span></span>

<span data-ttu-id="5520b-141">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="5520b-141">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5520b-142">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5520b-142">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5520b-143">입력</span><span class="sxs-lookup"><span data-stu-id="5520b-143">Inputs</span></span>

### <span data-ttu-id="5520b-144">System.String</span><span class="sxs-lookup"><span data-stu-id="5520b-144">System.String</span></span>

<span data-ttu-id="5520b-145">형식 이름을로 파이프 할 수 있습니다 `Get-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="5520b-145">You can pipe type names to `Get-TypeData`.</span></span>

## <span data-ttu-id="5520b-146">outputs</span><span class="sxs-lookup"><span data-stu-id="5520b-146">Outputs</span></span>

### <span data-ttu-id="5520b-147">Runspace. Update-typedata</span><span class="sxs-lookup"><span data-stu-id="5520b-147">System.Management.Automation.Runspaces.TypeData</span></span>

## <span data-ttu-id="5520b-148">메모</span><span class="sxs-lookup"><span data-stu-id="5520b-148">Notes</span></span>

<span data-ttu-id="5520b-149">`Get-TypeData` 현재 세션에 있는 확장 유형 데이터만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="5520b-149">`Get-TypeData` gets only the extended type data in the current session.</span></span> <span data-ttu-id="5520b-150">컴퓨터에 있지만 현재 세션에 추가되지 않은 확장 유형 데이터(에: 현재 세션으로 가져오지 않은 모듈에서 정의된 확장 유형)는 가져오지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5520b-150">It does not get extended type data that is on the computer, but has not been added to the current session, such as extended types that are defined in modules that have not been imported into the current session.</span></span>

## <span data-ttu-id="5520b-151">관련 링크</span><span class="sxs-lookup"><span data-stu-id="5520b-151">Related links</span></span>

[<span data-ttu-id="5520b-152">about_Types.ps1xml</span><span class="sxs-lookup"><span data-stu-id="5520b-152">about_Types.ps1xml</span></span>](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md)

[<span data-ttu-id="5520b-153">Remove-TypeData</span><span class="sxs-lookup"><span data-stu-id="5520b-153">Remove-TypeData</span></span>](Remove-TypeData.md)

[<span data-ttu-id="5520b-154">Update-TypeData</span><span class="sxs-lookup"><span data-stu-id="5520b-154">Update-TypeData</span></span>](Update-TypeData.md)

