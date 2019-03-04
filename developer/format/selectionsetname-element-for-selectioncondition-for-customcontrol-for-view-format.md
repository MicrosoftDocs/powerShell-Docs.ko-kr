---
title: CustomControl 보려면 (형식)에 대 한 SelectionCondition SelectionSetName 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a52b05a9-762e-4f1c-ad57-9d1710149722
caps.latest.revision: 10
ms.openlocfilehash: 25d46665ca5df3ddf49af5718d513b84c77988c8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862769"
---
# <a name="selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format"></a>View에 대한 CustomControl의 SelectionCondition에 대한 SelectionSetName 요소(형식)

트리거 조건이 있는.NET 형식의 집합을 지정 합니다. 있는 경우이 집합의 형식 중 하나는 조건이 충족 되 고이 컨트롤을 사용 하 여 개체가 표시 됩니다. 이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.

구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) CustomControl 요소 (형식) CustomEntries 요소 CustomControl CustomEntries EntrySelectedBy 보기 (형식)에 대 한 보기 (형식) CustomEntry 요소에 대 한 뷰 (형식)에 대 한 CustomEntry 요소

## <a name="syntax"></a>구문

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `SelectionSetName` 요소입니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[CustomControl 보려면 (형식)에 대 한 EntrySelectedBy SelectionCondition 요소](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|사용할 컨트롤 정의에 있어야 하는 조건을 정의 합니다.|

## <a name="text-value"></a>텍스트 값

선택 항목 집합의 이름을 지정 합니다.

## <a name="remarks"></a>설명

선택 영역 집합은 일반적인 그룹 형식 지정 파일을 정의 하는 모든 보기에서 사용할 수 있는.NET 개체입니다. 만들기 및 선택 집합을 참조 하는 방법에 대 한 자세한 내용은 참조 하세요. [설정의 개체 정의](./defining-selection-sets.md)합니다.

선택 조건 선택 집합 또는.NET 형식을 지정할 수 있지만 둘 다 지정할 수 없습니다. 선택 조건을 사용 하는 방법에 대 한 자세한 내용은 참조 하세요. [데이터를 표시 하는 경우에 대 한 조건을 정의](./defining-conditions-for-displaying-data.md)합니다.

## <a name="see-also"></a>참고 항목

[CustomControl 보려면 (형식)에 대 한 EntrySelectedBy SelectionCondition 요소](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[데이터 표시 되 면에 대 한 조건을 정의 합니다.](./defining-conditions-for-displaying-data.md)

[선택 영역 집합을 정의](./defining-selection-sets.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
