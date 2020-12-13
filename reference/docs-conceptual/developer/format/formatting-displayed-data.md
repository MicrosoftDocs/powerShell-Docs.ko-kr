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
# <a name="formatting-displayed-data"></a>표시되는 데이터 형식 지정

목록, 테이블 또는 넓은 보기에서 개별 데이터 요소를 표시 하는 방법을 지정할 수 있습니다. `FormatString`뷰의 항목을 정의할 때 요소를 사용 하거나, 요소를 사용 `ScriptBlock` 하 여 `FormatString` 데이터에 대해 메서드를 호출할 수 있습니다.

## <a name="using-the-formatstring-element"></a>FormatString 요소 사용

다음 예제에서 `TotalProcessorTime` [system.object](/dotnet/api/System.Diagnostics.Process) 개체의 속성 값은 FormatString 요소를 사용 하 여 형식이 지정 됩니다. `TotalProcessorTime`속성

```
<TableColumnItem>
  <PropertyName>TotalProcessorTime</PropertyName>
  <FormatString>{0:MMM}{0:dd}{0:HH}:{0:mm}</FormatString>
</TableColumnItem>
```
