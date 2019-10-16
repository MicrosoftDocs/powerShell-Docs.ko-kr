---
title: GroupBy (형식)에 대 한 PropertyName 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ddcecc46-ac75-43fa-b03a-802a68524ec3
caps.latest.revision: 10
ms.openlocfilehash: da6ac5abe7acbbee8f57b3e81529664f81800b86
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362522"
---
# <a name="propertyname-element-for-groupby-format"></a>GroupBy에 대한 PropertyName 요소(형식)

값이 변경 될 때마다 새 그룹을 시작 하는 .NET 속성을 지정 합니다.

구성 요소 (Format) ViewDefinitions 요소 (Format) View 요소 (format) GroupBy 요소 (형식)에 대 한 View (Format) PropertyName 요소

## <a name="syntax"></a>구문

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 `PropertyName` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[보기에 대 한 GroupBy 요소 (형식)](./groupby-element-for-view-format.md)|.NET 개체 그룹이 표시 되는 방법을 정의 합니다.|

## <a name="text-value"></a>텍스트 값

.NET 속성 이름을 지정 합니다.

## <a name="remarks"></a>설명

Windows PowerShell은이 속성 값이 변경 될 때마다 새 그룹을 시작 합니다.

이 요소를 지정 하면 새 그룹을 시작 하는 [ScriptBlock](./scriptblock-element-for-groupby-format.md) 요소를 지정할 수 없습니다.

## <a name="example"></a>예제

다음 예제에서는 속성 값이 변경 될 때 새 그룹을 시작 하는 방법을 보여 줍니다.

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

이 요소를 포함 하는 전체 서식 파일의 예는 [전체 뷰 (GroupBy)](./wide-view-groupby.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[보기에 대 한 GroupBy 요소 (형식)](./groupby-element-for-view-format.md)

[GroupBy (형식)에 대 한 ScriptBlock 요소](./scriptblock-element-for-groupby-format.md)

[PowerShell 서식 파일 작성](./writing-a-powershell-formatting-file.md)
