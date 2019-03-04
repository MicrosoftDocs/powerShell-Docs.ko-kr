---
title: SelectionSets 요소 (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ebbac73a-1c99-4388-9f47-703cd024dc6d
caps.latest.revision: 18
ms.openlocfilehash: a9356635d60d5f8c5d4dec4ec8b7d0aea2b037dd
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853569"
---
# <a name="selectionsets-element-format"></a>SelectionSets 요소(형식)

서식 파일의 모든 보기에서 사용할 수 있는.NET 개체의 공통 집합을 정의 합니다. 뷰 및 서식 파일의 컨트롤을 선택 세트의 이름만 사용 하 여 개체의 전체 집합을 참조할 수 있습니다.

구성 요소 SelectionSets 요소 형식

## <a name="syntax"></a>구문

```xml
<SelectionSets>
  <SelectionSet>...</SelectionSet>
</SelectionSets>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `SelectionSets` 요소입니다. 각 자식 요소 집합의 이름으로 참조할 수 있는 개체 집합을 정의 합니다. 자식 요소의 순서가 중요 합니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[SelectionSet 요소 (형식)](./selectionset-element-format.md)|필수 요소입니다.<br /><br /> 단일 집합의 이름으로 참조할 수 있는.NET 개체 집합을 정의 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[구성 요소](./configuration-element-format.md)|서식 파일의 최상위 요소를 나타냅니다.|

## <a name="remarks"></a>설명

상속을 통해 관련 된 개체와 같이 단일 이름을 사용 하 여 참조 하려는 관련된 개체 집합이 있는 경우 선택 집합을 사용할 수 있습니다. 뷰를 정의할 때 각 보기 내에서 모든 개체를 나열 하는 대신 설정 선택 항목의 이름을 사용 하 여 개체 집합을 지정할 수 있습니다.

서식 파일의 뷰 또는 뷰의 정의 정의 하는 경우 일반적인 선택 집합 이름으로 지정 됩니다. 이러한 경우에는 `SelectionSetName` 자식 요소를 `ViewSelectedBy` 및 `EntrySelectedBy` 요소에 사용할 집합을 지정 합니다. 선택 영역 집합에 대 한 자세한 내용은 참조 하세요. [설정의 개체 정의](./defining-selection-sets.md)합니다.

## <a name="see-also"></a>참고 항목

[구성 요소](./configuration-element-format.md)

[선택 영역 집합을 정의](./defining-selection-sets.md)

[SelectionSet 요소 (형식)](./selectionset-element-format.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
