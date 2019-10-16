---
title: View (Format)의 CustomControl 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2edac16c-0b30-4985-ac84-0821aa9a9f6d
caps.latest.revision: 12
ms.openlocfilehash: bd0f7ca4de8dede97d1553cd62884ea45876e0c7
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363362"
---
# <a name="customcontrol-element-for-view-format"></a>View에 대한 CustomControl 요소(형식)

뷰의 사용자 지정 컨트롤 형식을 정의 합니다.

Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) CustomControl 요소 (Format)

## <a name="syntax"></a>구문

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
</CustomControl>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 `CustomControl` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다. 하나의 자식 요소를 지정 해야 합니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[CustomControl에 대 한 CustomEntries 요소 (형식)](./customentries-element-for-customcontrol-for-view-format.md)|필수 요소입니다.<br /><br /> 사용자 지정 컨트롤 뷰의 정의를 제공 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[View 요소 (Format)](./view-element-format.md)|하나 이상의 .NET 개체를 표시 하는 데 사용 되는 뷰를 정의 합니다.|

## <a name="remarks"></a>설명

대부분의 경우 각 컨트롤 뷰에 대해 정의가 하나만 필요 하지만 동일한 뷰를 사용 하 여 다른 .NET 개체를 표시 하려는 경우에는 여러 정의를 제공할 수 있습니다. 이러한 경우 각 개체 또는 개체 집합에 대 한 별도의 정의를 제공할 수 있습니다.

## <a name="see-also"></a>참고 항목

[CustomControl에 대 한 CustomEntries 요소 (형식)](./customentries-element-for-customcontrol-for-view-format.md)

[View 요소 (Format)](./view-element-format.md)

[PowerShell 서식 파일 작성](./writing-a-powershell-formatting-file.md)
