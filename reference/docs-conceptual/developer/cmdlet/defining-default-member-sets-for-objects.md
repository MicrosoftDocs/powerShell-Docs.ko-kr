---
ms.date: 09/13/2016
ms.topic: reference
title: 개체에 대한 기본 멤버 집합 정의
description: 개체에 대한 기본 멤버 집합 정의
ms.openlocfilehash: 919f7ba65322c6a56a27e046fb211bde151abf7d
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92653127"
---
# <a name="defining-default-member-sets-for-objects"></a><span data-ttu-id="f4718-103">개체에 대한 기본 멤버 집합 정의</span><span class="sxs-lookup"><span data-stu-id="f4718-103">Defining Default Member Sets for Objects</span></span>

<span data-ttu-id="f4718-104">PSStandardMembers 멤버 집합은 Windows PowerShell에서 개체에 대 한 기본 속성 집합을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4718-104">The PSStandardMembers member set is used by Windows PowerShell to define the default property sets for an object.</span></span> <span data-ttu-id="f4718-105">기본 속성 집합은 속성 집합에 정의 된 속성만 표시 하도록 서식 지정 cmdlet과 같은 명령에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4718-105">The default property sets can be used by commands such as the formatting cmdlets to display only those properties that are defined by the property set.</span></span> <span data-ttu-id="f4718-106">기본 속성 집합에는 DefaultDisplayProperty, DefaultDisplayPropertySet 및 DefaultKeyPropertySet가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4718-106">The default property sets include DefaultDisplayProperty, DefaultDisplayPropertySet, and DefaultKeyPropertySet.</span></span> <span data-ttu-id="f4718-107">Windows PowerShell은 다른 모든 구성원 집합 및 PSStandardMembers 멤버 집합에 추가 된 다른 속성 집합을 무시 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4718-107">Windows PowerShell ignores all other member sets and any other property sets added to the PSStandardMembers member set.</span></span>

## <a name="member-set-for-systemdiagnosticsprocess"></a><span data-ttu-id="f4718-108">시스템 진단 프로세스에 대 한 멤버 집합</span><span class="sxs-lookup"><span data-stu-id="f4718-108">Member Set for System.Diagnostics.Process</span></span>

<span data-ttu-id="f4718-109">다음 예제에서 PSStandardMembers 멤버 집합은 [DefaultDisplayPropertySet 개체에](/dotnet/api/System.Diagnostics.Process) 대해 설정 된 속성을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4718-109">In the following example, the PSStandardMembers member set defines the DefaultDisplayPropertySet property set for [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objects.</span></span> <span data-ttu-id="f4718-110">이 속성 집합은 [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4718-110">This property set is used by the [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span></span>

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

<span data-ttu-id="f4718-111">다음 출력은 [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet에서 반환 되는 기본 속성을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f4718-111">The following output shows the default properties returned by the [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span></span> <span data-ttu-id="f4718-112">`Id` `Handles` `CPU` `Name` 각 프로세스 개체에 대해,, 및 속성만 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4718-112">Only the `Id`, `Handles`, `CPU`, and `Name` properties are returned for each process object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="f4718-113">관련 항목</span><span class="sxs-lookup"><span data-stu-id="f4718-113">See Also</span></span>

[<span data-ttu-id="f4718-114">Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="f4718-114">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
