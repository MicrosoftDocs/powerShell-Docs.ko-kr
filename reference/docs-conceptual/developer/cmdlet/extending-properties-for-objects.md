---
title: 개체에 대 한 속성 확장 | Microsoft Docs
ms.custom: ''
ms.date: 08/21/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f33ff3e9-213c-44aa-92ab-09450e65c676
caps.latest.revision: 11
ms.openlocfilehash: 3b14007384cca0d0cfa35655aee437adf73b1ff0
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364452"
---
# <a name="extending-properties-for-objects"></a><span data-ttu-id="935ed-102">개체 속성 확장</span><span class="sxs-lookup"><span data-stu-id="935ed-102">Extending Properties for Objects</span></span>

<span data-ttu-id="935ed-103">.NET Framework 개체를 확장 하는 경우 개체에 별칭 속성, 코드 속성, 메모 속성, 스크립트 속성 및 속성 집합을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="935ed-103">When you extend .NET Framework objects, you can add alias properties, code properties, note properties, script properties, and property sets to the objects.</span></span> <span data-ttu-id="935ed-104">이러한 속성을 정의 하는 XML은 다음 섹션에 설명 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="935ed-104">The XML that defines these properties is described in the following sections.</span></span>

> [!NOTE]
> <span data-ttu-id="935ed-105">다음 섹션의 예는 PowerShell 설치 디렉터리 (`$PSHOME`)의 기본 `Types.ps1xml` 형식 파일에서 가져온 것입니다.</span><span class="sxs-lookup"><span data-stu-id="935ed-105">The examples in the following sections are from the default `Types.ps1xml` types file in the PowerShell installation directory (`$PSHOME`).</span></span> <span data-ttu-id="935ed-106">자세한 내용은 [Types.ps1xml 정보](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="935ed-106">For more information, see [About Types.ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml).</span></span>

## <a name="alias-properties"></a><span data-ttu-id="935ed-107">별칭 속성</span><span class="sxs-lookup"><span data-stu-id="935ed-107">Alias properties</span></span>

<span data-ttu-id="935ed-108">별칭 속성은 기존 속성의 새 이름을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="935ed-108">An alias property defines a new name for an existing property.</span></span>

<span data-ttu-id="935ed-109">다음 예제에서는 **Count** 속성이 [system.object](/dotnet/api/System.Array) 형식에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="935ed-109">In the following example, the **Count** property is added to the [System.Array](/dotnet/api/System.Array) type.</span></span> <span data-ttu-id="935ed-110">[AliasProperty](/dotnet/api/system.management.automation.psaliasproperty) 요소는 확장 속성을 별칭 속성으로 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="935ed-110">The [AliasProperty](/dotnet/api/system.management.automation.psaliasproperty) element defines the extended property as an alias property.</span></span> <span data-ttu-id="935ed-111">[Name](/dotnet/api/system.management.automation.psmemberinfo.name) 요소는 새 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="935ed-111">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name) element specifies the new name.</span></span> <span data-ttu-id="935ed-112">[ReferencedMemberName](/dotnet/api/system.management.automation.psaliasproperty.referencedmembername) 요소는 별칭에 의해 참조 되는 기존 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="935ed-112">And, the [ReferencedMemberName](/dotnet/api/system.management.automation.psaliasproperty.referencedmembername) element specifies the existing property that is referenced by the alias.</span></span> <span data-ttu-id="935ed-113">[MemberSets](/dotnet/api/system.management.automation.psmemberset) 요소의 멤버에 `AliasProperty` 요소를 추가할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="935ed-113">You can also add the `AliasProperty` element to the members of the [MemberSets](/dotnet/api/system.management.automation.psmemberset) element.</span></span>

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

## <a name="code-properties"></a><span data-ttu-id="935ed-114">코드 속성</span><span class="sxs-lookup"><span data-stu-id="935ed-114">Code properties</span></span>

<span data-ttu-id="935ed-115">코드 속성은 .NET Framework 개체의 정적 속성을 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="935ed-115">A code property references a static property of a .NET Framework object.</span></span>

<span data-ttu-id="935ed-116">다음 예제에서 **Mode** 속성은 [system.io.directoryinfo](/dotnet/api/System.IO.DirectoryInfo) 형식에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="935ed-116">In the following example, the **Mode** property is added to the [System.IO.DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo) type.</span></span> <span data-ttu-id="935ed-117">[Codeproperty](/dotnet/api/system.management.automation.pscodeproperty) 요소는 확장 속성을 코드 속성으로 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="935ed-117">The [CodeProperty](/dotnet/api/system.management.automation.pscodeproperty) element defines the extended property as a code property.</span></span> <span data-ttu-id="935ed-118">[Name](/dotnet/api/system.management.automation.psmemberinfo.name) 요소는 확장 속성의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="935ed-118">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name) element specifies the name of the extended property.</span></span> <span data-ttu-id="935ed-119">그리고 [Getcodereference](/dotnet/api/system.management.automation.pscodeproperty.gettercodereference) 요소는 확장 속성이 참조 하는 정적 메서드를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="935ed-119">And, the [GetCodeReference](/dotnet/api/system.management.automation.pscodeproperty.gettercodereference) element defines the static method that is referenced by the extended property.</span></span> <span data-ttu-id="935ed-120">[MemberSets](/dotnet/api/system.management.automation.psmemberset) 요소의 멤버에 `CodeProperty` 요소를 추가할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="935ed-120">You can also add the `CodeProperty` element to the members of the [MemberSets](/dotnet/api/system.management.automation.psmemberset) element.</span></span>

```xml
<Type>
  <Name>System.IO.DirectoryInfo</Name>
  <Members>
    <CodeProperty>
      <Name>Mode</Name>
      <GetCodeReference>
        <TypeName>Microsoft.PowerShell.Commands.FileSystemProvider</TypeName>
        <MethodName>Mode</MethodName>
      </GetCodeReference>
    </CodeProperty>
  </Members>
</Type>
```

## <a name="note-properties"></a><span data-ttu-id="935ed-121">참고 속성</span><span class="sxs-lookup"><span data-stu-id="935ed-121">Note properties</span></span>

<span data-ttu-id="935ed-122">Note 속성은 정적 값이 있는 속성을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="935ed-122">A note property defines a property that has a static value.</span></span>

<span data-ttu-id="935ed-123">다음 예제에서 값이 항상 **Success**인 **Status** 속성은 [system.io.directoryinfo](/dotnet/api/System.IO.DirectoryInfo) 형식에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="935ed-123">In the following example, the **Status** property, whose value is always **Success**, is added to the [System.IO.DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo) type.</span></span> <span data-ttu-id="935ed-124">[Note property](/dotnet/api/system.management.automation.psnoteproperty) 요소는 확장 속성을 note 속성으로 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="935ed-124">The [NoteProperty](/dotnet/api/system.management.automation.psnoteproperty) element defines the extended property as a note property.</span></span> <span data-ttu-id="935ed-125">[Name](/dotnet/api/system.management.automation.psmemberinfo.name) 요소는 확장 속성의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="935ed-125">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name) element specifies the name of the extended property.</span></span> <span data-ttu-id="935ed-126">[Value](/dotnet/api/system.management.automation.psnoteproperty.value) 요소는 확장 속성의 정적 값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="935ed-126">The [Value](/dotnet/api/system.management.automation.psnoteproperty.value) element specifies the static value of the extended property.</span></span> <span data-ttu-id="935ed-127">[MemberSets](/dotnet/api/system.management.automation.psmemberset) 요소의 멤버에 `NoteProperty` 요소를 추가할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="935ed-127">The `NoteProperty` element can also be added to the members of the [MemberSets](/dotnet/api/system.management.automation.psmemberset) element.</span></span>

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

## <a name="script-properties"></a><span data-ttu-id="935ed-128">스크립트 속성</span><span class="sxs-lookup"><span data-stu-id="935ed-128">Script properties</span></span>

<span data-ttu-id="935ed-129">스크립트 속성은 값이 스크립트의 출력 인 속성을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="935ed-129">A script property defines a property whose value is the output of a script.</span></span>

<span data-ttu-id="935ed-130">다음 예제에서는 **VersionInfo** 속성이 [system.object](/dotnet/api/System.IO.FileInfo) 형식에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="935ed-130">In the following example, the **VersionInfo** property is added to the [System.IO.FileInfo](/dotnet/api/System.IO.FileInfo) type.</span></span> <span data-ttu-id="935ed-131">[Scriptproperty](/dotnet/api/system.management.automation.psscriptproperty) 요소는 확장 속성을 스크립트 속성으로 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="935ed-131">The [ScriptProperty](/dotnet/api/system.management.automation.psscriptproperty) element defines the extended property as a script property.</span></span> <span data-ttu-id="935ed-132">[Name](/dotnet/api/system.management.automation.psmemberinfo.name) 요소는 확장 속성의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="935ed-132">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name) element specifies the name of the extended property.</span></span> <span data-ttu-id="935ed-133">[Getscriptblock](/dotnet/api/system.management.automation.psscriptproperty.getterscript) 요소는 속성 값을 생성 하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="935ed-133">And, the [GetScriptBlock](/dotnet/api/system.management.automation.psscriptproperty.getterscript) element specifies the script that generates the property value.</span></span> <span data-ttu-id="935ed-134">[MemberSets](/dotnet/api/system.management.automation.psmemberset) 요소의 멤버에 `ScriptProperty` 요소를 추가할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="935ed-134">You can also add the `ScriptProperty` element to the members of the [MemberSets](/dotnet/api/system.management.automation.psmemberset) element.</span></span>

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

## <a name="property-sets"></a><span data-ttu-id="935ed-135">속성 집합</span><span class="sxs-lookup"><span data-stu-id="935ed-135">Property sets</span></span>

<span data-ttu-id="935ed-136">속성 집합은 집합의 이름으로 참조할 수 있는 확장 속성의 그룹을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="935ed-136">A property set defines a group of extended properties that can be referenced by the name of the set.</span></span>
<span data-ttu-id="935ed-137">예를 들어 [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table)
**property** 매개 변수는 표시할 특정 속성 집합을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="935ed-137">For example, the [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table)
**Property** parameter can specify a specific property set to be displayed.</span></span> <span data-ttu-id="935ed-138">속성 집합을 지정 하면 해당 집합에 속한 속성만 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="935ed-138">When a property set is specified, only those properties that belong to the set are displayed.</span></span>

<span data-ttu-id="935ed-139">개체에 대해 정의할 수 있는 속성 집합의 수에는 제한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="935ed-139">There's no restriction on the number of property sets that can be defined for an object.</span></span> <span data-ttu-id="935ed-140">그러나 개체의 기본 표시 속성을 정의 하는 데 사용 되는 속성 집합은 **Psstandardmembers** 멤버 집합 내에서 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="935ed-140">However, the property sets used to define the default display properties of an object must be specified within the **PSStandardMembers** member set.</span></span> <span data-ttu-id="935ed-141">`Types.ps1xml` 형식 파일에서 기본 속성 집합 이름에는 **Defaultdisplayproperty**, **DefaultDisplayPropertySet**및 **DefaultKeyPropertySet**가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="935ed-141">In the `Types.ps1xml` types file, the default property set names include **DefaultDisplayProperty**, **DefaultDisplayPropertySet**, and **DefaultKeyPropertySet**.</span></span> <span data-ttu-id="935ed-142">**Psstandardmembers** 멤버 집합에 추가 하는 모든 추가 속성 집합은 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="935ed-142">Any additional property sets that you add to the **PSStandardMembers** member set are ignored.</span></span>

<span data-ttu-id="935ed-143">다음 예제에서는 **DefaultDisplayPropertySet** 속성 집합이 [Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) 형식의 **psstandardmembers** 멤버 집합에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="935ed-143">In the following example, the **DefaultDisplayPropertySet** property set is added to the **PSStandardMembers** member set of the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) type.</span></span> <span data-ttu-id="935ed-144">[PropertySet](/dotnet/api/system.management.automation.pspropertyset) 요소는 속성의 그룹을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="935ed-144">The [PropertySet](/dotnet/api/system.management.automation.pspropertyset) element defines the group of properties.</span></span> <span data-ttu-id="935ed-145">[Name](/dotnet/api/system.management.automation.psmemberinfo.name) 요소는 속성 집합의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="935ed-145">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name) element specifies the name of the property set.</span></span> <span data-ttu-id="935ed-146">그리고 [Referencedproperties](/dotnet/api/system.management.automation.pspropertyset.referencedpropertynames) 요소는 집합의 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="935ed-146">And, the [ReferencedProperties](/dotnet/api/system.management.automation.pspropertyset.referencedpropertynames) element specifies the properties of the set.</span></span> <span data-ttu-id="935ed-147">또한 [Type](/dotnet/api/system.management.automation.pstypename) 요소의 멤버에 `PropertySet` 요소를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="935ed-147">You can also add the `PropertySet` element to the members of the [Type](/dotnet/api/system.management.automation.pstypename) element.</span></span>

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
            <Name>Status</Name
            <Name>Name</Name>
            <Name>DisplayName</Name>
          </ReferencedProperties>
        </PropertySet>
      </Members>
    </MemberSet>
  </Members>
</Type>
```

## <a name="see-also"></a><span data-ttu-id="935ed-148">참고자료</span><span class="sxs-lookup"><span data-stu-id="935ed-148">See also</span></span>

[<span data-ttu-id="935ed-149">Types.ps1xml 정보</span><span class="sxs-lookup"><span data-stu-id="935ed-149">About Types.ps1xml</span></span>](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml)

[<span data-ttu-id="935ed-150">시스템 관리. 자동화</span><span class="sxs-lookup"><span data-stu-id="935ed-150">System.Management.Automation</span></span>](/dotnet/api/System.Management.Automation)

<span data-ttu-id="935ed-151">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="935ed-151">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
