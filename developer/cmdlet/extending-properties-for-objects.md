---
title: 개체에 대 한 속성을 확장 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f33ff3e9-213c-44aa-92ab-09450e65c676
caps.latest.revision: 11
ms.openlocfilehash: dcab755f565cd176c85ef6b9c719bceae10301b4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854529"
---
# <a name="extending-properties-for-objects"></a><span data-ttu-id="cd829-102">개체 속성 확장</span><span class="sxs-lookup"><span data-stu-id="cd829-102">Extending Properties for Objects</span></span>

<span data-ttu-id="cd829-103">.NET Framework 개체를 확장 하는 경우 추가할 수 있습니다 별칭 속성, 코드 속성, 메모 속성, 스크립트 속성 및 속성 집합 개체.</span><span class="sxs-lookup"><span data-stu-id="cd829-103">When you extend .NET Framework objects, you can add alias properties, code properties, note properties, script properties, and property sets to the objects.</span></span> <span data-ttu-id="cd829-104">이러한 속성을 정의 하는 데 사용 되는 XML은 다음 섹션에 설명 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd829-104">The XML that is used to define these properties is described in the following sections.</span></span>

> [!NOTE]
> <span data-ttu-id="cd829-105">다음 섹션의 예는 Windows PowerShell 설치 디렉터리에서 Types.ps1xml 형식 기본 파일에서 (`$pshome`).</span><span class="sxs-lookup"><span data-stu-id="cd829-105">The examples in the following sections are from the default Types.ps1xml types file in the Windows PowerShell installation directory (`$pshome`).</span></span>

## <a name="alias-properties"></a><span data-ttu-id="cd829-106">별칭 속성</span><span class="sxs-lookup"><span data-stu-id="cd829-106">Alias Properties</span></span>

<span data-ttu-id="cd829-107">별칭 속성을 기존 속성에 대 한 새 이름을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="cd829-107">An alias property defines a new name for an existing property.</span></span>

<span data-ttu-id="cd829-108">다음 예제에서는 `Count` 속성을 추가 합니다 [System.Array? Displayproperty =](/dotnet/api/System.Array) 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="cd829-108">In the following example, the `Count` property is added to the [System.Array?Displayproperty=Fullname](/dotnet/api/System.Array) type.</span></span> <span data-ttu-id="cd829-109">합니다 [AliasProperty](http://msdn.microsoft.com/en-us/b140038c-807a-4bb9-beca-332491cda1b1) 요소 별칭 속성으로 확장 된 속성을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd829-109">The [AliasProperty](http://msdn.microsoft.com/en-us/b140038c-807a-4bb9-beca-332491cda1b1) element defines the extended property as an alias property.</span></span> <span data-ttu-id="cd829-110">합니다 [이름을](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) 요소에 새 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd829-110">The [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the new name.</span></span> <span data-ttu-id="cd829-111">그 뿐만 아니라 [ReferencedMemberName](http://msdn.microsoft.com/en-us/0c5db6cc-9033-4d48-88a7-76b962882f7a) 요소 별칭에서 참조 되는 기존 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd829-111">And, the [ReferencedMemberName](http://msdn.microsoft.com/en-us/0c5db6cc-9033-4d48-88a7-76b962882f7a) element specifies the existing property that is referenced by the alias.</span></span> <span data-ttu-id="cd829-112">(추가할 수도 있습니다는 [AliasProperty](http://msdn.microsoft.com/en-us/d6647953-94ad-4b0b-af2e-4dda6952dee1) 의 멤버에는 요소는 [구성원 집합](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) 요소입니다.)</span><span class="sxs-lookup"><span data-stu-id="cd829-112">(You can also add the [AliasProperty](http://msdn.microsoft.com/en-us/d6647953-94ad-4b0b-af2e-4dda6952dee1) element to the members of the [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span></span>

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

## <a name="code-properties"></a><span data-ttu-id="cd829-113">코드 속성</span><span class="sxs-lookup"><span data-stu-id="cd829-113">Code Properties</span></span>

<span data-ttu-id="cd829-114">코드 속성에는.NET Framework 개체의 정적 속성을 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="cd829-114">A code property references a static property of a .NET Framework object.</span></span>

<span data-ttu-id="cd829-115">다음 예제에서는 `Node` 속성을 추가 합니다 [System.IO.Directoryinfo? Displayproperty =](/dotnet/api/System.IO.DirectoryInfo) 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="cd829-115">In the following example, the `Node` property is added to the [System.IO.Directoryinfo?Displayproperty=Fullname](/dotnet/api/System.IO.DirectoryInfo) type.</span></span> <span data-ttu-id="cd829-116">합니다 [CodeProperty](http://msdn.microsoft.com/en-us/59bc4d18-41eb-4c0d-8ad3-bbfa5dc488db) 요소 코드 속성으로 확장 된 속성을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd829-116">The [CodeProperty](http://msdn.microsoft.com/en-us/59bc4d18-41eb-4c0d-8ad3-bbfa5dc488db) element defines the extended property as a code property.</span></span> <span data-ttu-id="cd829-117">합니다 [이름을](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) 요소 확장된 속성의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd829-117">The [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the name of the extended property.</span></span> <span data-ttu-id="cd829-118">그 뿐만 아니라 [GetCodeReference](http://msdn.microsoft.com/en-us/62af34f5-cc22-42c0-9e0c-3bd0f5c1a4a0) 요소 확장된 속성에서 참조 되는 정적 메서드를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd829-118">And, the [GetCodeReference](http://msdn.microsoft.com/en-us/62af34f5-cc22-42c0-9e0c-3bd0f5c1a4a0) element defines the static method that is referenced by the extended property.</span></span> <span data-ttu-id="cd829-119">(추가할 수도 있습니다는 [CodeProperty](http://msdn.microsoft.com/en-us/59bc4d18-41eb-4c0d-8ad3-bbfa5dc488db) 의 멤버에는 요소는 [구성원 집합](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) 요소입니다.)</span><span class="sxs-lookup"><span data-stu-id="cd829-119">(You can also add the [CodeProperty](http://msdn.microsoft.com/en-us/59bc4d18-41eb-4c0d-8ad3-bbfa5dc488db) element to the members of the [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span></span>

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

## <a name="note-properties"></a><span data-ttu-id="cd829-120">참고 속성</span><span class="sxs-lookup"><span data-stu-id="cd829-120">Note Properties</span></span>

<span data-ttu-id="cd829-121">메모 속성을 정적 값이 있는 속성을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd829-121">A note property defines a property that has a static value.</span></span>

<span data-ttu-id="cd829-122">다음 예제에서는 `Status` (값은 "성공"이 항상) 속성을 추가 합니다 [System.IO.Directoryinfo? Displayproperty =](/dotnet/api/System.IO.DirectoryInfo) 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="cd829-122">In the following example, the `Status` property (whose value is always "Success") is added to the [System.IO.Directoryinfo?Displayproperty=Fullname](/dotnet/api/System.IO.DirectoryInfo) type.</span></span> <span data-ttu-id="cd829-123">[NoteProperty](http://msdn.microsoft.com/en-us/331e6c50-d703-43f0-89bc-ca9fb97800eb) 참고 속성으로 확장 된 속성을 정의 하는 요소는 [이름](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) 요소는 확장된 속성의 이름을 지정 하며 [값](http://msdn.microsoft.com/en-us/f3c77546-b98e-4c4e-bbe0-6dfd06696d1c) 요소 확장된 속성의 정적 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="cd829-123">The [NoteProperty](http://msdn.microsoft.com/en-us/331e6c50-d703-43f0-89bc-ca9fb97800eb) element defines the extended property as a note property; the [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the name of the extended property; and the [Value](http://msdn.microsoft.com/en-us/f3c77546-b98e-4c4e-bbe0-6dfd06696d1c) element specifies the static value of the extended property.</span></span> <span data-ttu-id="cd829-124">(합니다 [NoteProperty](http://msdn.microsoft.com/en-us/331e6c50-d703-43f0-89bc-ca9fb97800eb) 의 멤버에 요소를 추가할 수도 있습니다는 [구성원 집합](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) 요소입니다.)</span><span class="sxs-lookup"><span data-stu-id="cd829-124">(The [NoteProperty](http://msdn.microsoft.com/en-us/331e6c50-d703-43f0-89bc-ca9fb97800eb) element can also be added to the members of the [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span></span>

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

## <a name="script-properties"></a><span data-ttu-id="cd829-125">스크립트 속성</span><span class="sxs-lookup"><span data-stu-id="cd829-125">Script Properties</span></span>

<span data-ttu-id="cd829-126">스크립트 속성 값은 스크립트의 출력 속성을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd829-126">A script property defines a property whose value is the output of a script.</span></span>

<span data-ttu-id="cd829-127">다음 예제에서는 `VersionInfo` 속성을 추가 합니다 [System.IO.Fileinfo? Displayproperty =](/dotnet/api/System.IO.FileInfo) 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="cd829-127">In the following example, the `VersionInfo` property is added to the [System.IO.Fileinfo?Displayproperty=Fullname](/dotnet/api/System.IO.FileInfo) type.</span></span> <span data-ttu-id="cd829-128">합니다 [ScriptProperty](http://msdn.microsoft.com/en-us/858a4247-676b-4cc9-9f3e-057109aad350) 요소 스크립트 속성으로 확장 된 속성을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd829-128">The [ScriptProperty](http://msdn.microsoft.com/en-us/858a4247-676b-4cc9-9f3e-057109aad350) element defines the extended property as a script property.</span></span> <span data-ttu-id="cd829-129">합니다 [이름을](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) 요소 확장된 속성의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd829-129">The [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the name of the extended property.</span></span> <span data-ttu-id="cd829-130">그 뿐만 아니라 [GetScriptBlock](http://msdn.microsoft.com/en-us/f3c77546-b98e-4c4e-bbe0-6dfd06696d1c) 요소는 속성 값을 생성 하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd829-130">And, the [GetScriptBlock](http://msdn.microsoft.com/en-us/f3c77546-b98e-4c4e-bbe0-6dfd06696d1c) element specifies the script that generates the property value.</span></span> <span data-ttu-id="cd829-131">(추가할 수도 있습니다는 [ScriptProperty](http://msdn.microsoft.com/en-us/858a4247-676b-4cc9-9f3e-057109aad350) 의 멤버에는 요소는 [구성원 집합](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) 요소입니다.)</span><span class="sxs-lookup"><span data-stu-id="cd829-131">(You can also add the [ScriptProperty](http://msdn.microsoft.com/en-us/858a4247-676b-4cc9-9f3e-057109aad350) element to the members of the [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span></span>

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

## <a name="property-sets"></a><span data-ttu-id="cd829-132">속성 집합</span><span class="sxs-lookup"><span data-stu-id="cd829-132">Property Sets</span></span>

<span data-ttu-id="cd829-133">속성 집합을 그룹 집합의 이름으로 참조할 수 있는 확장된 속성을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd829-133">A property set defines a group of extended properties that can be referenced by the name of the set.</span></span> <span data-ttu-id="cd829-134">예를 들어 합니다 `Property` 의 매개 변수를 [Format-table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table) cmdlet 집합을 표시할 특정 속성을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd829-134">For example, the `Property` parameter of the [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table) cmdlet can specify a specific property set to be displayed.</span></span> <span data-ttu-id="cd829-135">지정 된 속성 집합은 집합에 속해 있는 속성만 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd829-135">When a property set is specified, only those properties that belong to the set are displayed.</span></span>
<span data-ttu-id="cd829-136">속성 집합을 그룹 집합의 이름으로 참조할 수 있는 확장된 속성을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd829-136">A property set defines a group of extended properties that can be referenced by the name of the set.</span></span> <span data-ttu-id="cd829-137">예를 들어 합니다 `Property` 의 매개 변수를 [Format-table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table) cmdlet 집합을 표시할 특정 속성을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd829-137">For example, the `Property` parameter of the [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table) cmdlet can specify a specific property set to be displayed.</span></span> <span data-ttu-id="cd829-138">지정 된 속성 집합은 집합에 속해 있는 속성만 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd829-138">When a property set is specified, only those properties that belong to the set are displayed.</span></span>

<span data-ttu-id="cd829-139">개체에 대해 정의 될 수 있는 속성 집합의 수에 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cd829-139">There is no restriction on the number of property sets that can be defined for an object.</span></span> <span data-ttu-id="cd829-140">그러나 개체의 기본 표시 속성을 정의 하는 데 사용 되는 속성 집합 PSStandardMembers 멤버 집합 내에서 지정 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd829-140">However, the property sets used to define the default display properties of an object must be specified within the PSStandardMembers member set.</span></span> <span data-ttu-id="cd829-141">Types.ps1xml 형식 파일의 기본 속성 집합 이름을 DefaultDisplayProperty, DefaultDisplayPropertySet, 및 DefaultKeyPropertySet 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd829-141">In the Types.ps1xml types file, the default property set names include DefaultDisplayProperty, DefaultDisplayPropertySet, and DefaultKeyPropertySet.</span></span> <span data-ttu-id="cd829-142">PSStandardMembers 멤버 집합에 추가한 모든 추가 속성 집합은 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd829-142">Any additional property sets that you add to the PSStandardMembers member set are ignored.</span></span>

<span data-ttu-id="cd829-143">다음 예제에서는 DefaultDisplayPropertySet 속성 집합 PSStandardMembers 멤버 집합에 추가 되는 [System.Serviceprocess.Servicecontroller? Displayproperty =](/dotnet/api/System.ServiceProcess.ServiceController) 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="cd829-143">In the following example, the DefaultDisplayPropertySet property set is added to the PSStandardMembers member set of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) type.</span></span> <span data-ttu-id="cd829-144">합니다 [PropertySet](http://msdn.microsoft.com/en-us/14cdc234-796e-4857-9b51-bdbaa1412188) 요소 그룹 속성을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd829-144">The [PropertySet](http://msdn.microsoft.com/en-us/14cdc234-796e-4857-9b51-bdbaa1412188) element defines the group of properties.</span></span> <span data-ttu-id="cd829-145">합니다 [이름을](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) 요소 속성 집합의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd829-145">The [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the name of the property set.</span></span> <span data-ttu-id="cd829-146">그 뿐만 아니라 [ReferencedProperties](http://msdn.microsoft.com/en-us/5e620423-8679-4fbf-b6db-9f79288e4786) 요소 집합의 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd829-146">And, the [ReferencedProperties](http://msdn.microsoft.com/en-us/5e620423-8679-4fbf-b6db-9f79288e4786) element specifies the properties of the set.</span></span> <span data-ttu-id="cd829-147">(추가할 수도 있습니다는 [PropertySet](http://msdn.microsoft.com/en-us/14cdc234-796e-4857-9b51-bdbaa1412188) 의 멤버에는 요소는 [형식](http://msdn.microsoft.com/en-us/e5dbd353-d6b2-40a1-92b6-6f1fea744ebe) 요소입니다.)</span><span class="sxs-lookup"><span data-stu-id="cd829-147">(You can also add the [PropertySet](http://msdn.microsoft.com/en-us/14cdc234-796e-4857-9b51-bdbaa1412188) element to the members of the [Type](http://msdn.microsoft.com/en-us/e5dbd353-d6b2-40a1-92b6-6f1fea744ebe) element.)</span></span>

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

## <a name="see-also"></a><span data-ttu-id="cd829-148">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cd829-148">See Also</span></span>

<span data-ttu-id="cd829-149">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="cd829-149">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
