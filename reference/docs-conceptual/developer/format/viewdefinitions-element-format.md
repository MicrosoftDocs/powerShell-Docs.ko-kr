---
title: ViewDefinitions 요소 (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 29840c10-2b30-4bb1-a8a0-ddf84d19c2d0
caps.latest.revision: 18
ms.openlocfilehash: c5ec80350c7707ccd41112ab5e1952e5dc198cca
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361422"
---
# <a name="viewdefinitions-element-format"></a>ViewDefinitions 요소(형식)

.NET 개체를 표시 하는 데 사용 되는 뷰를 정의 합니다. 이러한 뷰에서는 개체의 속성 및 스크립트 값을 테이블 형식, 목록 형식, 넓은 형식 및 사용자 지정 컨트롤 형식으로 표시할 수 있습니다.

Configuration 요소 (Format) ViewDefinitions (Format XML) 요소

## <a name="syntax"></a>구문

```xml

<ViewDefinitions>
  <View>...</View>
</ViewDefinitions>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 `ViewDefinitions` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다. 서식 파일에서 정의할 수 있는 뷰 수에는 제한이 없으며 순서에 관계 없이 추가할 수 있습니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[View 요소 (Format)](./view-element-format.md)|하나 이상의 .NET 개체를 표시 하는 데 사용 되는 뷰를 정의 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[Configuration 요소 (Format)](./configuration-element-format.md)|서식 파일의 최상위 요소를 나타냅니다.|

## <a name="remarks"></a>설명

여러 유형의 보기 구성 요소에 대 한 자세한 내용은 다음 항목을 참조 하십시오.

- [테이블 뷰 만들기](./creating-a-table-view.md)

- [목록 보기 만들기](./creating-a-list-view.md)

- [넓은 뷰 만들기](./creating-a-wide-view.md)

- [사용자 지정 컨트롤](./creating-custom-controls.md)

## <a name="example"></a>예제

이 예에서는 테이블 뷰의 부모 요소와 목록 뷰를 포함 하는 `ViewDefinitions` 요소를 보여 줍니다.

```xml
<Configuration>
  <ViewDefinitions>
    <View>
      <TableControl>...</TableControl>
    </View>
    <View>
      <ListControl>...</ListControl>
    </View>
  </ViewDefinitions>
</Configuration>
```

## <a name="see-also"></a>참고 항목

[Configuration 요소 (Format)](./configuration-element-format.md)

[View 요소 (Format)](./view-element-format.md)

[테이블 뷰 만들기](./creating-a-table-view.md)

[목록 보기 만들기](./creating-a-list-view.md)

[넓은 뷰 만들기](./creating-a-wide-view.md)

[사용자 지정 컨트롤](./creating-custom-controls.md)

[PowerShell 서식 파일 작성](./writing-a-powershell-formatting-file.md)
