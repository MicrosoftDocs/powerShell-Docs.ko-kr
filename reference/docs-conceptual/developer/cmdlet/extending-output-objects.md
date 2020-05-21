---
title: 출력 개체 확장 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a252e0ec-d456-42d7-bd49-d6b8bc57f388
caps.latest.revision: 11
ms.openlocfilehash: 12a826363221b8a7ce06245c787a7bd0529e42f8
ms.sourcegitcommit: 17d798a041851382b406ed789097843faf37692d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83690908"
---
# <a name="extending-output-objects"></a><span data-ttu-id="21ccb-102">출력 개체 확장</span><span class="sxs-lookup"><span data-stu-id="21ccb-102">Extending Output Objects</span></span>

<span data-ttu-id="21ccb-103">형식 파일 (. types.ps1xml)을 사용 하 여 cmdlet, 함수 및 스크립트에 의해 반환 되는 .NET Framework 개체를 확장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21ccb-103">You can extend the .NET Framework objects that are returned by cmdlets, functions, and scripts by using types files (.ps1xml).</span></span> <span data-ttu-id="21ccb-104">형식 파일은 기존 개체에 속성 및 메서드를 추가할 수 있는 XML 기반 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="21ccb-104">Types files are XML-based files that let you add properties and methods to existing objects.</span></span> <span data-ttu-id="21ccb-105">예를 들어 Windows PowerShell은 몇 가지 기존 .NET Framework 개체에 요소를 추가 하는 types.ps1xml 파일을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="21ccb-105">For example, Windows PowerShell provides the Types.ps1xml file, which adds elements to several existing .NET Framework objects.</span></span> <span data-ttu-id="21ccb-106">Types.ps1xml 파일은 Windows PowerShell 설치 디렉터리 ()에 있습니다 `$pshome` .</span><span class="sxs-lookup"><span data-stu-id="21ccb-106">The Types.ps1xml file is located in the Windows PowerShell installation directory (`$pshome`).</span></span> <span data-ttu-id="21ccb-107">사용자 고유의 형식 파일을 만들어 이러한 개체를 추가로 확장 하거나 다른 개체를 확장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21ccb-107">You can create your own types file to further extend those objects or to extend other objects.</span></span> <span data-ttu-id="21ccb-108">형식 파일을 사용 하 여 개체를 확장 하는 경우 개체의 모든 인스턴스가 새 요소로 확장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="21ccb-108">When you extend an object by using a types file, any instance of the object is extended with the new elements.</span></span>

## <a name="extending-the-systemarray-object"></a><span data-ttu-id="21ccb-109">System.object 개체 확장</span><span class="sxs-lookup"><span data-stu-id="21ccb-109">Extending the System.Array Object</span></span>

<span data-ttu-id="21ccb-110">다음 예제에서는 Windows PowerShell에서 types.ps1xml 파일의 [system.object](/dotnet/api/System.Array) 개체를 확장 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="21ccb-110">The following example shows how Windows PowerShell extends the [System.Array](/dotnet/api/System.Array) object in the Types.ps1xml file.</span></span> <span data-ttu-id="21ccb-111">기본적으로 [system.object](/dotnet/api/System.Array) 개체에는 `Length` 배열의 개체 수를 나열 하는 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21ccb-111">By default, [System.Array](/dotnet/api/System.Array) objects have a `Length` property that lists the number of objects in the array.</span></span> <span data-ttu-id="21ccb-112">그러나 이름 "length"는 속성을 명확 하 게 설명 하지 않으므로 Windows PowerShell은 속성의 `Count` 값과 동일한 값을 표시 하는 alias 속성을 추가 합니다 `Length` .</span><span class="sxs-lookup"><span data-stu-id="21ccb-112">However, because the name "length" does not clearly describe the property, Windows PowerShell adds the `Count` alias property, which displays the same value as the `Length` property.</span></span> <span data-ttu-id="21ccb-113">다음 XML은 `Count` [system.object](/dotnet/api/System.Array) 형식에 속성을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="21ccb-113">The following XML adds the `Count` property to the [System.Array](/dotnet/api/System.Array) type.</span></span>

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

<span data-ttu-id="21ccb-114">이 새 별칭 속성을 보려면 다음 예제에 표시 된 것 처럼 모든 배열에서 [Get Member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="21ccb-114">To see this new alias property, use a [Get-Member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) command on any array, as shown in the following example.</span></span>

```powershell
Get-Member -InputObject (1,2,3,4)
```

<span data-ttu-id="21ccb-115">이 명령은 다음 결과를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="21ccb-115">The command returns the following results.</span></span>

```output
Name           MemberType    Definition
----           ----------    ----------
Count          AliasProperty Count = Length
Address        Method        System.Object& Address(Int32 )
Clone          Method        System.Object Clone()
CopyTo         Method        System.Void CopyTo(Array array, Int32 index):
Equals         Method        System.Boolean Equals(Object obj)
Get            Method        System.Object Get(Int32 )
...
Length         Property      System.Int32 Length {get;}
```

<span data-ttu-id="21ccb-116">`Count`속성 또는 속성 중 하나 `Length` 를 사용 하 여 배열에 있는 개체 수를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21ccb-116">You can use either the `Count` property or the `Length` property to determine how many objects are in an array.</span></span> <span data-ttu-id="21ccb-117">다음은 그 예입니다.</span><span class="sxs-lookup"><span data-stu-id="21ccb-117">For example:</span></span>

```powershell
PS> (1, 2, 3, 4).Count
```

```output
4
```

```powershell
PS> (1, 2, 3, 4).Length
```

```output
4
```

## <a name="custom-types-files"></a><span data-ttu-id="21ccb-118">사용자 지정 형식 파일</span><span class="sxs-lookup"><span data-stu-id="21ccb-118">Custom Types Files</span></span>

<span data-ttu-id="21ccb-119">사용자 지정 형식 파일을 만들려면 기존 형식 파일을 복사 하 여 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="21ccb-119">To create a custom types file, start by copying an existing types file.</span></span> <span data-ttu-id="21ccb-120">새 파일에는 아무 이름이 나 사용할 수 있지만 types.ps1xml 파일 이름 확장명을 포함 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="21ccb-120">The new file can have any name, but it must have a .ps1xml file name extension.</span></span> <span data-ttu-id="21ccb-121">파일을 복사할 때 Windows PowerShell에 액세스할 수 있는 모든 디렉터리에 새 파일을 저장할 수 있지만 Windows PowerShell 설치 디렉터리 ( `$pshome` ) 또는 설치 디렉터리의 하위 디렉터리에 파일을 저장 하는 것이 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="21ccb-121">When you copy the file, you can place the new file in any directory that is accessible to Windows PowerShell, but it is useful to place the files in the Windows PowerShell installation directory (`$pshome`) or in a subdirectory of the installation directory.</span></span>

<span data-ttu-id="21ccb-122">자체 확장 형식을 파일에 추가 하려면 확장 하려는 각 개체의 types 요소를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="21ccb-122">To add your own extended types to the file, add a types element for each object that you want to extend.</span></span> <span data-ttu-id="21ccb-123">다음 항목에서는 예제를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="21ccb-123">The following topics provide examples.</span></span>

- <span data-ttu-id="21ccb-124">속성 및 속성 집합을 추가 하는 방법에 대 한 자세한 내용은 [확장 속성](./extending-properties-for-objects.md) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="21ccb-124">For more information about adding properties and property sets, see [Extended Properties](./extending-properties-for-objects.md)</span></span>

- <span data-ttu-id="21ccb-125">메서드를 추가 하는 방법에 대 한 자세한 내용은 [확장 메서드](./defining-default-methods-for-objects.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="21ccb-125">For more information about adding methods, see [Extended Methods](./defining-default-methods-for-objects.md).</span></span>

- <span data-ttu-id="21ccb-126">멤버 집합을 추가 하는 방법에 대 한 자세한 내용은 [확장 멤버 집합](./defining-default-member-sets-for-objects.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="21ccb-126">For more information about adding member sets, see [Extended Member Sets](./defining-default-member-sets-for-objects.md).</span></span>

<span data-ttu-id="21ccb-127">사용자 고유의 확장 형식을 정의한 후 다음 방법 중 하나를 사용 하 여 확장 개체를 사용할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="21ccb-127">After you define your own extended types, use one of the following methods to make your extended objects available:</span></span>

- <span data-ttu-id="21ccb-128">확장 형식 파일을 현재 세션에서 사용할 수 있도록 설정 하려면 [update-typedata](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet을 사용 하 여 새 파일을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="21ccb-128">To make your extended types file available to the current session, use the [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet to add the new file.</span></span> <span data-ttu-id="21ccb-129">형식이 다른 형식 파일 (types.ps1xml 파일 포함)에 정의 된 형식 보다 우선적으로 적용 되도록 하려면 `PrependData` [update-typedata](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet의 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="21ccb-129">If you want your types to take precedence over the types that are defined in other types files (including the Types.ps1xml file), use the `PrependData` parameter of the [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet.</span></span>
- <span data-ttu-id="21ccb-130">모든 이후 세션에서 확장 형식 파일을 사용할 수 있도록 하려면 형식 파일을 모듈에 추가 하 고 현재 세션을 내보내거나 [update-typedata](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) 명령을 Windows PowerShell 프로필에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="21ccb-130">To make your extended types file available to all future sessions, add the types file to a module, export the current session, or add the [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) command to your Windows PowerShell profile.</span></span>

## <a name="signing-types-files"></a><span data-ttu-id="21ccb-131">형식 파일 서명</span><span class="sxs-lookup"><span data-stu-id="21ccb-131">Signing Types Files</span></span>

<span data-ttu-id="21ccb-132">XML에 스크립트 블록이 포함 될 수 있으므로 변조를 방지 하기 위해 형식 파일을 디지털 서명 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="21ccb-132">Types files should be digitally signed to prevent tampering because the XML can include script blocks.</span></span> <span data-ttu-id="21ccb-133">디지털 서명을 추가 하는 방법에 대 한 자세한 내용은 [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="21ccb-133">For more information about adding digital signatures, see [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing)</span></span>

## <a name="see-also"></a><span data-ttu-id="21ccb-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="21ccb-134">See Also</span></span>

[<span data-ttu-id="21ccb-135">개체의 기본 속성 정의</span><span class="sxs-lookup"><span data-stu-id="21ccb-135">Defining Default Properties for Objects</span></span>](./extending-properties-for-objects.md)

[<span data-ttu-id="21ccb-136">개체에 대한 기본 메서드 정의</span><span class="sxs-lookup"><span data-stu-id="21ccb-136">Defining Default Methods for Objects</span></span>](./defining-default-methods-for-objects.md)

[<span data-ttu-id="21ccb-137">개체에 대한 기본 멤버 집합 정의</span><span class="sxs-lookup"><span data-stu-id="21ccb-137">Defining Default Member Sets for Objects</span></span>](./defining-default-member-sets-for-objects.md)

[<span data-ttu-id="21ccb-138">Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="21ccb-138">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
