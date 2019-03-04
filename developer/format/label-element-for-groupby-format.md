---
title: GroupBy (형식)에 대 한 요소 레이블을 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3351d237-e8c2-4ec5-9500-4eceadb407c2
caps.latest.revision: 11
ms.openlocfilehash: e7158711c60d13c745bbdfab9b1b9fc7d98b34e2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862399"
---
# <a name="label-element-for-groupby-format"></a>GroupBy에 대한 Label 요소(형식)

새 그룹이 발견 될 때 표시 되는 레이블을 지정 합니다.

구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) GroupBy 요소 GroupBy (형식)에 대 한 보기 (형식) 레이블 요소에 대 한

## <a name="syntax"></a>구문

```xml
<Label>DisplayedLabel</Label>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `Label` 요소입니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[뷰 (형식)에 대 한 GroupBy 요소](./groupby-element-for-view-format.md)|새 개체 그룹에 표시 되는 방식을 정의 합니다.|

## <a name="text-value"></a>텍스트 값

Windows PowerShell에서 새 속성 또는 스크립트 값을 발견 될 때마다 표시 되는 텍스트를 지정 합니다.

## <a name="remarks"></a>설명

이 요소에 의해 지정 된 텍스트, 외에도 Windows PowerShell의 그룹을 시작 하 고 그룹 전후에 빈 줄을 추가 하는 새 값을 표시 합니다.

## <a name="example"></a>예제

다음 예제에서는 새 그룹의 레이블을 보여 줍니다. 표시 된 레이블을 다음과 유사 하 게 보입니다. `Service Type: NewValueofProperty`

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

이 요소를 포함 하는 전체 서식 파일의 예제를 보려면 [넓은 보기 (GroupBy)](./wide-view-groupby.md)합니다.

## <a name="see-also"></a>참고 항목

[뷰 (형식)에 대 한 GroupBy 요소](./groupby-element-for-view-format.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
