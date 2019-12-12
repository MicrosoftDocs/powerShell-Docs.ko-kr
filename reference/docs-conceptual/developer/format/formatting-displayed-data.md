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
ms.openlocfilehash: e915ac71feb50cb58cfa9195f0de94763affdb77
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363702"
---
# <a name="formatting-displayed-data"></a>표시되는 데이터 형식 지정

목록, 테이블 또는 넓은 보기에서 개별 데이터 요소를 표시 하는 방법을 지정할 수 있습니다. 뷰의 항목을 정의할 때 `FormatString` 요소를 사용 하거나 `ScriptBlock` 요소를 사용 하 여 데이터에 대해 `FormatString` 메서드를 호출할 수 있습니다.

## <a name="using-the-formatstring-element"></a>FormatString 요소 사용

다음 예제에서 [system.object](/dotnet/api/System.Diagnostics.Process) 개체의 `TotalProcessorTime` 속성 값은 FormatString 요소를 사용 하 여 형식이 지정 됩니다. `TotalProcessorTime` 속성

```
<TableColumnItem>
  <PropertyName>TotalProcessorTime</PropertyName>
  <FormatString>{0:MMM}{0:dd}{0:HH}:{0:mm}</FormatString>
</TableColumnItem>
```



