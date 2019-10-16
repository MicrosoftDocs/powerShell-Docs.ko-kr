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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361872"
---
# <a name="selectionsets-element-format"></a>SelectionSets 요소(형식)

서식 지정 파일의 모든 보기에서 사용할 수 있는 .NET 개체의 공통 집합을 정의 합니다. 서식 파일의 뷰 및 컨트롤은 선택 집합의 이름만 사용 하 여 개체의 전체 집합을 참조할 수 있습니다.

구성 요소 SelectionSets 요소 형식

## <a name="syntax"></a>구문

```xml
<SelectionSets>
  <SelectionSet>...</SelectionSet>
</SelectionSets>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 `SelectionSets` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다. 각 자식 요소는 집합의 이름으로 참조할 수 있는 개체 집합을 정의 합니다. 자식 요소의 순서는 중요 하지 않습니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[SelectionSet 요소 (형식)](./selectionset-element-format.md)|필수 요소입니다.<br /><br /> 집합의 이름으로 참조할 수 있는 단일 .NET 개체 집합을 정의 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[구성 요소](./configuration-element-format.md)|서식 파일의 최상위 요소를 나타냅니다.|

## <a name="remarks"></a>설명

상속을 통해 관련 된 개체 집합과 같이 단일 이름을 사용 하 여 참조 하려는 관련 개체 집합이 있는 경우 선택 집합을 사용할 수 있습니다. 뷰를 정의할 때 각 보기 내에 모든 개체를 나열 하는 대신 선택 집합의 이름을 사용 하 여 개체 집합을 지정할 수 있습니다.

일반 선택 집합은 형식 지정 파일의 뷰나 뷰의 정의를 정의할 때 이름으로 지정 됩니다. 이러한 경우 `ViewSelectedBy` 및 `EntrySelectedBy` 요소의 `SelectionSetName` 자식 요소는 사용할 집합을 지정 합니다. 선택 집합에 대 한 자세한 내용은 [개체 집합 정의](./defining-selection-sets.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[구성 요소](./configuration-element-format.md)

[선택 집합 정의](./defining-selection-sets.md)

[SelectionSet 요소 (형식)](./selectionset-element-format.md)

[PowerShell 서식 파일 작성](./writing-a-powershell-formatting-file.md)
