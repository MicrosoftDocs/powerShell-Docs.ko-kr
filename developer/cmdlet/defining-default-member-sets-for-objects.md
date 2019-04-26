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
ms.openlocfilehash: 2d634e7638ec0e0117d65ca0b2d08e68f0068a03
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068252"
---
# <a name="defining-default-member-sets-for-objects"></a>개체에 대한 기본 멤버 집합 정의

PSStandardMembers 멤버 집합 개체에 대 한 기본 속성 집합을 정의 하려면 Windows PowerShell에서 사용 됩니다. 속성 집합에 정의 된 해당 속성만 표시할 형식 지정 cmdlet와 같은 명령을 사용 하 여 기본 속성 집합을 사용할 수 있습니다. 기본 속성 집합에는 DefaultDisplayProperty, DefaultDisplayPropertySet, 및 DefaultKeyPropertySet 포함 됩니다. Windows PowerShell은 다른 모든 멤버 집합 및 PSStandardMembers 멤버 집합에 추가할 다른 속성 집합을 무시 합니다.

## <a name="member-set-for-systemdiagnosticsprocess"></a>System.Diagnostics.Process 멤버 집합

다음 예에서 PSStandardMembers 멤버 집합에 대 한 설정 DefaultDisplayPropertySet 속성을 정의 [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) 개체입니다. 이 속성 집합에서 사용 되는 [Format-list](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.

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

다음 출력에서는에서 반환 되는 기본 속성을 [Format-list](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet. 만 `Id`, `Handles`를 `CPU`, 및 `Name` 각 프로세스 개체에 대 한 속성이 반환 됩니다.

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

## <a name="see-also"></a>참고 항목

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)
