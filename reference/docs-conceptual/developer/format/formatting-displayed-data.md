---
title: 표시 된 데이터 서식 지정 | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 38971643-2a3d-4f5b-a1fa-6334c162b8ed
caps.latest.revision: 4
ms.openlocfilehash: 9f3a3176ae16ac7c014cadce6b4e856f9bd3b5da
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83560392"
---
# <a name="formatting-displayed-data"></a><span data-ttu-id="deab4-102">표시되는 데이터 형식 지정</span><span class="sxs-lookup"><span data-stu-id="deab4-102">Formatting Displayed Data</span></span>

<span data-ttu-id="deab4-103">목록, 테이블 또는 넓은 보기에서 개별 데이터 요소를 표시 하는 방법을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="deab4-103">You can specify how the individual data points in your List, Table, or Wide view are displayed.</span></span> <span data-ttu-id="deab4-104">`FormatString`뷰의 항목을 정의할 때 요소를 사용 하거나, 요소를 사용 `ScriptBlock` 하 여 `FormatString` 데이터에 대해 메서드를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="deab4-104">You can use the `FormatString` element when defining the items of your view, or you can use the `ScriptBlock` element to call the `FormatString` method on the data.</span></span>

## <a name="using-the-formatstring-element"></a><span data-ttu-id="deab4-105">FormatString 요소 사용</span><span class="sxs-lookup"><span data-stu-id="deab4-105">Using the FormatString Element</span></span>

<span data-ttu-id="deab4-106">다음 예제에서 `TotalProcessorTime` [system.object](/dotnet/api/System.Diagnostics.Process) 개체의 속성 값은 FormatString 요소를 사용 하 여 형식이 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="deab4-106">In the following example the value of the `TotalProcessorTime` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object is formatted using the FormatString element.</span></span> <span data-ttu-id="deab4-107">`TotalProcessorTime`속성</span><span class="sxs-lookup"><span data-stu-id="deab4-107">the `TotalProcessorTime` property</span></span>

```
<TableColumnItem>
  <PropertyName>TotalProcessorTime</PropertyName>
  <FormatString>{0:MMM}{0:dd}{0:HH}:{0:mm}</FormatString>
</TableColumnItem>
```
