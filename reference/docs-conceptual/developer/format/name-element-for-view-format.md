---
title: View의 Name 요소 (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3a31010d-1db9-44ae-a7f3-6ed32cb641cb
caps.latest.revision: 16
ms.openlocfilehash: 097d20cb6a04635124d1f96823248df6095ca1af
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362642"
---
# <a name="name-element-for-view-format"></a>View에 대한 Name 요소(형식)

뷰를 식별 하는 데 사용 되는 이름을 지정 합니다.

Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) Name 요소 (Format)

## <a name="syntax"></a>구문

```xml
<Name>ViewName</Name>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 `Name` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다. 각 뷰에는 하나의 `Name` 요소만 사용할 수 있습니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[View 요소 (Format)](./view-element-format.md)|하나 이상의 .NET 개체의 멤버를 표시 하는 데 사용 되는 뷰를 정의 합니다.|

## <a name="text-value"></a>텍스트 값

보기의 고유 이름을 지정 합니다. 이 이름에는 뷰 형식 (예: 테이블 뷰 또는 목록 뷰)에 대 한 참조, 뷰를 사용 하는 개체 또는 개체 집합, 개체를 반환 하는 명령 또는 이러한 항목의 조합이 포함 될 수 있습니다.

## <a name="remarks"></a>설명

다양 한 보기 유형에 대 한 자세한 내용은 [테이블 뷰](./creating-a-table-view.md), [목록 뷰](./creating-a-list-view.md), [넓은 뷰](./creating-a-wide-view.md)및 [사용자 지정 보기](./creating-custom-controls.md)항목을 참조 하세요.

## <a name="example"></a>예제

다음 예에서는 [Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) 개체에 대 한 테이블 뷰를 정의 하는 `View` 요소를 보여 줍니다. 뷰 이름은 "service"입니다.

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>

```

## <a name="see-also"></a>참고 항목

[목록 보기 만들기](./creating-a-list-view.md)

[테이블 뷰 만들기](./creating-a-table-view.md)

[넓은 뷰 만들기](./creating-a-wide-view.md)

[사용자 지정 컨트롤 만들기](./creating-custom-controls.md)

[View 요소 (Format)](./view-element-format.md)

[PowerShell 서식 파일 작성](./writing-a-powershell-formatting-file.md)
