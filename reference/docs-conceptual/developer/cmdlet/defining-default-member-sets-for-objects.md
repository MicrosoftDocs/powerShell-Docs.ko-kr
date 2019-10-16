---
title: 개체에 대 한 기본 멤버 집합 정의 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 77f94326-8ffe-4d40-bd2a-b79fb0b4a4e5
caps.latest.revision: 8
ms.openlocfilehash: 2d634e7638ec0e0117d65ca0b2d08e68f0068a03
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369782"
---
# <a name="defining-default-member-sets-for-objects"></a><span data-ttu-id="fdf63-102">개체에 대한 기본 멤버 집합 정의</span><span class="sxs-lookup"><span data-stu-id="fdf63-102">Defining Default Member Sets for Objects</span></span>

<span data-ttu-id="fdf63-103">PSStandardMembers 멤버 집합은 Windows PowerShell에서 개체에 대 한 기본 속성 집합을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fdf63-103">The PSStandardMembers member set is used by Windows PowerShell to define the default property sets for an object.</span></span> <span data-ttu-id="fdf63-104">기본 속성 집합은 속성 집합에 정의 된 속성만 표시 하도록 서식 지정 cmdlet과 같은 명령에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fdf63-104">The default property sets can be used by commands such as the formatting cmdlets to display only those properties that are defined by the property set.</span></span> <span data-ttu-id="fdf63-105">기본 속성 집합에는 DefaultDisplayProperty, DefaultDisplayPropertySet 및 DefaultKeyPropertySet가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fdf63-105">The default property sets include DefaultDisplayProperty, DefaultDisplayPropertySet, and DefaultKeyPropertySet.</span></span> <span data-ttu-id="fdf63-106">Windows PowerShell은 다른 모든 구성원 집합 및 PSStandardMembers 멤버 집합에 추가 된 다른 속성 집합을 무시 합니다.</span><span class="sxs-lookup"><span data-stu-id="fdf63-106">Windows PowerShell ignores all other member sets and any other property sets added to the PSStandardMembers member set.</span></span>

## <a name="member-set-for-systemdiagnosticsprocess"></a><span data-ttu-id="fdf63-107">시스템 진단 프로세스에 대 한 멤버 집합</span><span class="sxs-lookup"><span data-stu-id="fdf63-107">Member Set for System.Diagnostics.Process</span></span>

<span data-ttu-id="fdf63-108">다음 예제에서 PSStandardMembers 멤버 집합은 [DefaultDisplayPropertySet 개체에](/dotnet/api/System.Diagnostics.Process) 대해 설정 된 속성을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="fdf63-108">In the following example, the PSStandardMembers member set defines the DefaultDisplayPropertySet property set for [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objects.</span></span> <span data-ttu-id="fdf63-109">이 속성 집합은 [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fdf63-109">This property set is used by the [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span></span>

```xml
<Type>
  <Name>System.Diagnostics.Process</Name>
  <Members>
    <MemberSet>
     <Name>PSStandardMembers</Name>
     <Members>
       <PropertySet>
         <Name>DefaultDisplayPropertySet</Name>
         <ReferencedProperties>
           <Name>Id</Name>
           <Name>Handles</Name>
           <Name>CPU</Name>
           <Name>Name</Name>
         </ReferencedProperties>
      </PropertySet>
    </Members>
  </MemberSet>
```

<span data-ttu-id="fdf63-110">다음 출력은 [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet에서 반환 되는 기본 속성을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="fdf63-110">The following output shows the default properties returned by the [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span></span> <span data-ttu-id="fdf63-111">각 프로세스 개체에 대해 `Id`, `Handles`, `CPU` 및 `Name` 속성만 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fdf63-111">Only the `Id`, `Handles`, `CPU`, and `Name` properties are returned for each process object.</span></span>

```powershell
Get-Process | format-list
```

```output
Id      : 2036
Handles : 27
CPU     :
Name    : AEADISRV

Id      : 272
Handles : 38
CPU     :
Name    : agrsmsvc
...
```

## <a name="see-also"></a><span data-ttu-id="fdf63-112">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fdf63-112">See Also</span></span>

<span data-ttu-id="fdf63-113">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="fdf63-113">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
