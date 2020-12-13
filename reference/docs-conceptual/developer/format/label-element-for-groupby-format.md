---
ms.date: 09/13/2016
ms.topic: reference
title: GroupBy에 대한 Label 요소(형식)
description: GroupBy에 대한 Label 요소(형식)
ms.openlocfilehash: ff4b0dec01bb5b472b1813540661791b91568eed
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92649793"
---
# <a name="label-element-for-groupby-format"></a>GroupBy에 대한 Label 요소(형식)

새 그룹이 발견 될 때 표시 되는 레이블을 지정 합니다.

구성 요소 (Format) ViewDefinitions 요소 (Format) View 요소 (format) GroupBy 요소 (형식)에 대 한 View (Format) Label 요소

## <a name="syntax"></a>구문

```xml
<Label>DisplayedLabel</Label>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `Label` .

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[View에 대한 GroupBy 요소(형식)](./groupby-element-for-view-format.md)|새 개체 그룹을 표시 하는 방법을 정의 합니다.|

## <a name="text-value"></a>텍스트 값

Windows PowerShell에서 새 속성이 나 스크립트 값을 발견할 때마다 표시 되는 텍스트를 지정 합니다.

## <a name="remarks"></a>설명

이 요소에 지정 된 텍스트 외에도 Windows PowerShell은 그룹을 시작 하는 새 값을 표시 하 고 그룹 앞과 뒤에 빈 줄을 추가 합니다.

## <a name="example"></a>예제

다음 예에서는 새 그룹의 레이블을 보여 줍니다. 표시 되는 레이블은 다음과 유사 합니다. `Service Type: NewValueofProperty`

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

이 요소를 포함 하는 전체 서식 파일의 예는 [전체 뷰 (GroupBy)](./wide-view-groupby.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[View에 대한 GroupBy 요소(형식)](./groupby-element-for-view-format.md)

[PowerShell 형식 지정 파일 작성](./writing-a-powershell-formatting-file.md)
