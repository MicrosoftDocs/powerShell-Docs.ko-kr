---
title: ViewSelectedBy (형식)에 대 한 SelectionSetName 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: f6410b463bcb00d2758849c2f7e13cd839277e50
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87772606"
---
# <a name="selectionsetname-element-for-viewselectedby-format"></a>ViewSelectedBy에 대한 SelectionSetName 요소(형식)

뷰에 표시 되는 .NET 개체의 집합을 지정 합니다.

Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format)의 ViewSelectedBy 요소 (format) SelectionSetName 요소 (형식)

## <a name="syntax"></a>구문

```xml
<SelectionSetName>Name of selection set<SelectionSetName>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `SelectionSetName` .

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[ViewSelectedBy 요소(형식)](./viewselectedby-element-format.md)|뷰에 표시 되는 .NET 개체를 정의 합니다.|

## <a name="text-value"></a>텍스트 값

선택 집합의 요소에 정의 된 선택 집합의 이름을 지정 `Name` 합니다.

## <a name="remarks"></a>설명

상속을 통해 관련 된 개체 집합과 같이 단일 이름을 사용 하 여 참조 하려는 관련 개체 집합이 있는 경우 선택 집합을 사용할 수 있습니다. 선택 집합 정의 및 참조에 대 한 자세한 내용은 [개체 집합 정의](./defining-selection-sets.md)를 참조 하세요.

## <a name="example"></a>예제

다음 예에서는 목록 뷰에 대 한 선택 집합을 지정 하는 방법을 보여 줍니다. 테이블, 전체 및 사용자 지정 보기에도 동일한 스키마가 사용 됩니다.

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

[선택 영역 집합 정의](./defining-selection-sets.md)

[ViewSelectedBy 요소(형식)](./viewselectedby-element-format.md)

[PowerShell 형식 지정 파일 작성](./writing-a-powershell-formatting-file.md)
