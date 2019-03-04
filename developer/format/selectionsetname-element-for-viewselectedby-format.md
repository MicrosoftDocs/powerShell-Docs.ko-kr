---
title: SelectionSetName 요소 ViewSelectedBy (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ab0f033-df09-4435-a8bd-76ec2d01f13b
caps.latest.revision: 13
ms.openlocfilehash: d1de2b30860bac80bf17508f40eec33c2794c4b2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858339"
---
# <a name="selectionsetname-element-for-viewselectedby-format"></a>ViewSelectedBy에 대한 SelectionSetName 요소(형식)

보기에 표시 되는.NET 개체 집합을 지정 합니다.

구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) ViewSelectedBy 요소 (형식) SelectionSetName 요소 ViewSelectedBy (형식)에 대 한

## <a name="syntax"></a>구문

```xml
<SelectionSetName>Name of selection set<SelectionSetName>
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
|[ViewSelectedBy 요소 (형식)](./viewselectedby-element-format.md)|보기에 표시 되는.NET 개체를 정의 합니다.|

## <a name="text-value"></a>텍스트 값

정의한 선택 세트의 이름을 지정 합니다 `Name` 선택 세트에 대 한 요소입니다.

## <a name="remarks"></a>설명

상속을 통해 관련 된 개체와 같이 단일 이름을 사용 하 여 참조 하려는 관련된 개체 집합이 있는 경우 선택 집합을 사용할 수 있습니다. 정의 및 선택 집합을 참조 하는 방법에 대 한 자세한 내용은 참조 하세요. [설정의 개체 정의](./defining-selection-sets.md)합니다.

## <a name="example"></a>예제

다음 예제에서는 선택 목록 보기에 대 한 세트를 지정 하는 방법을 보여 줍니다. 동일한 스키마는 테이블, 넓게 및 사용자 지정 보기에 사용 됩니다.

```xml
<View>
  <Name>Name of View</Name>
  <ViewSelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a>참고 항목

[선택 영역 집합을 정의](./defining-selection-sets.md)

[ViewSelectedBy 요소 (형식)](./viewselectedby-element-format.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
