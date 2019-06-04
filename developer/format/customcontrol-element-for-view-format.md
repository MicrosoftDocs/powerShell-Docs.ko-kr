---
title: CustomControl 요소 보려면 (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2edac16c-0b30-4985-ac84-0821aa9a9f6d
caps.latest.revision: 12
ms.openlocfilehash: bd0f7ca4de8dede97d1553cd62884ea45876e0c7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066671"
---
# <a name="customcontrol-element-for-view-format"></a>View에 대한 CustomControl 요소(형식)

뷰에 대 한 사용자 지정 컨트롤 형식을 정의 합니다.

구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) CustomControl 요소 (형식)

## <a name="syntax"></a>구문

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
</CustomControl>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `CustomControl` 요소입니다. 자식 요소가 하나를 지정 해야 합니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[뷰 (형식)에 대 한 CustomControl CustomEntries 요소](./customentries-element-for-customcontrol-for-view-format.md)|필수 요소입니다.<br /><br /> 사용자 지정 컨트롤 뷰의 정의 제공합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[뷰 요소 (형식)](./view-element-format.md)|하나 이상의.NET 개체를 표시 하는 데 사용 되는 뷰를 정의 합니다.|

## <a name="remarks"></a>설명

대부분의 경우에서 각 컨트롤 보기에 대 한 정의 하나만 필요 하지만 다른.NET 개체를 표시 하려면 같은 뷰를 사용 하려는 경우에 여러 정의 제공 하려면 가능 합니다. 이러한 경우 각 개체 또는 개체 집합에 대 한 별도 정의 제공할 수 있습니다.

## <a name="see-also"></a>참고 항목

[뷰 (형식)에 대 한 CustomControl CustomEntries 요소](./customentries-element-for-customcontrol-for-view-format.md)

[뷰 요소 (형식)](./view-element-format.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
