---
title: CustomControl에 대 한 SelectionCondition의 TypeName 요소 (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2c65171-4d4c-46a9-a545-591df058acd1
caps.latest.revision: 7
ms.openlocfilehash: 00e9ae0916dd6d22602b99b201c9c4b7e549dc48
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361592"
---
# <a name="typename-element-for-selectioncondition-for-customcontrol-for-view--format"></a>View에 대한 CustomControl의 SelectionCondition에 대한 TypeName 요소(형식)

조건을 트리거하는 .NET 유형을 지정 합니다. 이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.

Configuration 요소 (Format) ViewDefinitions element (Format) View 요소 (format) CustomControl 요소에 대 한 view (format) CustomEntries 요소에 대 한 CustomControl Format) CustomItem 요소에 대해 CustomControl for view (format) SelectionCondition 요소에 대 한 CustomControl for view (format) TypeName 요소에 대해 SelectionCondition for CustomControl for View (Format)

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
|[CustomControl for View (Format)에 대해 EntrySelectedBy의 SelectionCondition 요소](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|컨트롤 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다.|

## <a name="text-value"></a>텍스트 값

.NET 형식의 정규화 된 이름 (예: `System.IO.DirectoryInfo`)을 지정 합니다.

## <a name="remarks"></a>설명

## <a name="see-also"></a>참고 항목

[CustomControl for View (Format)에 대해 EntrySelectedBy의 SelectionCondition 요소](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[PowerShell 서식 파일 작성](./writing-a-powershell-formatting-file.md)
