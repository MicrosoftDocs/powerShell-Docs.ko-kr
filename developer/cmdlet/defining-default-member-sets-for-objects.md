---
title: 개체에 대 한 기본 멤버 집합을 정의 합니다. | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 77f94326-8ffe-4d40-bd2a-b79fb0b4a4e5
caps.latest.revision: 8
ms.openlocfilehash: e8185eb7221a3be0445eddc537dbca89478c74f2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859799"
---
# <a name="defining-default-member-sets-for-objects"></a><span data-ttu-id="59170-102">개체에 대한 기본 멤버 집합 정의</span><span class="sxs-lookup"><span data-stu-id="59170-102">Defining Default Member Sets for Objects</span></span>

<span data-ttu-id="59170-103">PSStandardMembers 멤버 집합 개체에 대 한 기본 속성 집합을 정의 하려면 Windows PowerShell에서 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="59170-103">The PSStandardMembers member set is used by Windows PowerShell to define the default property sets for an object.</span></span> <span data-ttu-id="59170-104">속성 집합에 정의 된 해당 속성만 표시할 형식 지정 cmdlet와 같은 명령을 사용 하 여 기본 속성 집합을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59170-104">The default property sets can be used by commands such as the formatting cmdlets to display only those properties that are defined by the property set.</span></span> <span data-ttu-id="59170-105">기본 속성 집합에는 DefaultDisplayProperty, DefaultDisplayPropertySet, 및 DefaultKeyPropertySet 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="59170-105">The default property sets include DefaultDisplayProperty, DefaultDisplayPropertySet, and DefaultKeyPropertySet.</span></span> <span data-ttu-id="59170-106">Windows PowerShell은 다른 모든 멤버 집합 및 PSStandardMembers 멤버 집합에 추가할 다른 속성 집합을 무시 합니다.</span><span class="sxs-lookup"><span data-stu-id="59170-106">Windows PowerShell ignores all other member sets and any other property sets added to the PSStandardMembers member set.</span></span>

## <a name="member-set-for-systemdiagnosticsprocess"></a><span data-ttu-id="59170-107">System.Diagnostics.Process 멤버 집합</span><span class="sxs-lookup"><span data-stu-id="59170-107">Member Set for System.Diagnostics.Process</span></span>

<span data-ttu-id="59170-108">다음 예에서 PSStandardMembers 멤버 집합에 대 한 설정 DefaultDisplayPropertySet 속성을 정의 [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="59170-108">In the following example, the PSStandardMembers member set defines the DefaultDisplayPropertySet property set for [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objects.</span></span> <span data-ttu-id="59170-109">이 속성 집합에서 사용 되는 [Format-list](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="59170-109">This property set is used by the [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span></span>
<span data-ttu-id="59170-110">다음 예에서 PSStandardMembers 멤버 집합에 대 한 설정 DefaultDisplayPropertySet 속성을 정의 [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="59170-110">In the following example, the PSStandardMembers member set defines the DefaultDisplayPropertySet property set for [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objects.</span></span> <span data-ttu-id="59170-111">이 속성 집합에서 사용 되는 [Format-list](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="59170-111">This property set is used by the [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span></span>

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

<span data-ttu-id="59170-112">다음 출력에서는에서 반환 되는 기본 속성을 [Format-list](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="59170-112">The following output shows the default properties returned by the [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span></span> <span data-ttu-id="59170-113">만 `Id`, `Handles`를 `CPU`, 및 `Name` 각 프로세스 개체에 대 한 속성이 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="59170-113">Only the `Id`, `Handles`, `CPU`, and `Name` properties are returned for each process object.</span></span>
<span data-ttu-id="59170-114">다음 출력에서는에서 반환 되는 기본 속성을 [Format-list](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="59170-114">The following output shows the default properties returned by the [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span></span> <span data-ttu-id="59170-115">만 `Id`, `Handles`를 `CPU`, 및 `Name` 각 프로세스 개체에 대 한 속성이 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="59170-115">Only the `Id`, `Handles`, `CPU`, and `Name` properties are returned for each process object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="59170-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="59170-116">See Also</span></span>

<span data-ttu-id="59170-117">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="59170-117">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
