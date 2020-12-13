---
ms.date: 09/12/2016
ms.topic: reference
title: 표시되는 데이터 형식 지정
description: 표시되는 데이터 형식 지정
ms.openlocfilehash: 40f6b3b4fa36062ee0bad3f197ad159f571445c8
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667864"
---
# <a name="formatting-displayed-data"></a><span data-ttu-id="9499b-103">표시되는 데이터 형식 지정</span><span class="sxs-lookup"><span data-stu-id="9499b-103">Formatting Displayed Data</span></span>

<span data-ttu-id="9499b-104">목록, 테이블 또는 넓은 보기에서 개별 데이터 요소를 표시 하는 방법을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9499b-104">You can specify how the individual data points in your List, Table, or Wide view are displayed.</span></span> <span data-ttu-id="9499b-105">`FormatString`뷰의 항목을 정의할 때 요소를 사용 하거나, 요소를 사용 `ScriptBlock` 하 여 `FormatString` 데이터에 대해 메서드를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9499b-105">You can use the `FormatString` element when defining the items of your view, or you can use the `ScriptBlock` element to call the `FormatString` method on the data.</span></span>

## <a name="using-the-formatstring-element"></a><span data-ttu-id="9499b-106">FormatString 요소 사용</span><span class="sxs-lookup"><span data-stu-id="9499b-106">Using the FormatString Element</span></span>

<span data-ttu-id="9499b-107">다음 예제에서 `TotalProcessorTime` [system.object](/dotnet/api/System.Diagnostics.Process) 개체의 속성 값은 FormatString 요소를 사용 하 여 형식이 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9499b-107">In the following example the value of the `TotalProcessorTime` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object is formatted using the FormatString element.</span></span> <span data-ttu-id="9499b-108">`TotalProcessorTime`속성</span><span class="sxs-lookup"><span data-stu-id="9499b-108">the `TotalProcessorTime` property</span></span>

```
<TableColumnItem>
  <PropertyName>TotalProcessorTime</PropertyName>
  <FormatString>{0:MMM}{0:dd}{0:HH}:{0:mm}</FormatString>
</TableColumnItem>
```
