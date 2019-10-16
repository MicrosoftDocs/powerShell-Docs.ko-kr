---
title: View 컨트롤의 SelectionCondition에 대 한 TypeName 요소 (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7141aefc-6656-4c52-8a9c-c2bfc9c87be9
caps.latest.revision: 6
ms.openlocfilehash: 7a697c286ec9efe750930739cdfa2580003365dd
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361602"
---
# <a name="typename-element-for-selectioncondition-for-controls-for-view-format"></a>View에 대한 Controls의 SelectionCondition에 대한 TypeName 요소(형식)

조건을 트리거하는 .NET 유형을 지정 합니다. 이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의 하는 데 사용 됩니다.

Configuration 요소 (Format) ViewDefinitions 요소 (Format) View 요소 (format) 컨트롤 요소 컨트롤에 대 한 컨트롤의 요소 (format) 컨트롤 요소 뷰 (format) CustomEntries 요소에 대 한 컨트롤에 대 한 컨트롤의 요소입니다. View (format) CustomControl 컨트롤에 대 한 컨트롤의 CustomEntry 요소에 대 한 컨트롤에 대 한 Customentry 요소에 대 한 컨트롤의 CustomEntry 요소 Format) View 컨트롤의 SelectionCondition에 대 한 TypeName 요소 (형식)

## <a name="syntax"></a>구문

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 `TypeName` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[보기의 컨트롤에 대해 EntrySelectedBy의 SelectionCondition 요소 (형식)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|컨트롤 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다.|

## <a name="text-value"></a>텍스트 값

.NET 형식의 정규화 된 이름 (예: `System.IO.DirectoryInfo`)을 지정 합니다.

## <a name="remarks"></a>설명

## <a name="see-also"></a>참고 항목

[보기의 컨트롤에 대해 EntrySelectedBy의 SelectionCondition 요소 (형식)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[PowerShell 서식 파일 작성](./writing-a-powershell-formatting-file.md)
