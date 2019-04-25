---
title: 표시 되는 데이터 서식 지정 | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 38971643-2a3d-4f5b-a1fa-6334c162b8ed
caps.latest.revision: 4
ms.openlocfilehash: e915ac71feb50cb58cfa9195f0de94763affdb77
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065668"
---
# <a name="formatting-displayed-data"></a><span data-ttu-id="5444c-102">표시되는 데이터 형식 지정</span><span class="sxs-lookup"><span data-stu-id="5444c-102">Formatting Displayed Data</span></span>

<span data-ttu-id="5444c-103">개별 데이터 요소에 목록, 테이블 또는 와이드 보기인 경우에 표시 되는 방식을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5444c-103">You can specify how the individual data points in your List, Table, or Wide view are displayed.</span></span> <span data-ttu-id="5444c-104">사용할 수는 `FormatString` 요소 보기의 항목을 정의할 때 사용할 수는 `ScriptBlock` 를 호출 하는 요소는 `FormatString` 메서드 데이터를 합니다.</span><span class="sxs-lookup"><span data-stu-id="5444c-104">You can use the `FormatString` element when defining the items of your view, or you can use the `ScriptBlock` element to call the `FormatString` method on the data.</span></span>

## <a name="using-the-formatstring-element"></a><span data-ttu-id="5444c-105">FormatString 요소를 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="5444c-105">Using the FormatString Element</span></span>

<span data-ttu-id="5444c-106">다음 예제 값의는 `TotalProcessorTime` 의 속성을 [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) FormatString 요소를 사용 하 여 개체 형식이 합니다.</span><span class="sxs-lookup"><span data-stu-id="5444c-106">In the following example the value of the `TotalProcessorTime` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object is formatted using the FormatString element.</span></span> <span data-ttu-id="5444c-107">`TotalProcessorTime` 속성</span><span class="sxs-lookup"><span data-stu-id="5444c-107">the `TotalProcessorTime` property</span></span>

```
<TableColumnItem>
  <PropertyName>TotalProcessorTime</PropertyName>
  <FormatString>{0:MMM}{0:dd}{0:HH}:{0:mm}</FormatString>
</TableColumnItem>
```



