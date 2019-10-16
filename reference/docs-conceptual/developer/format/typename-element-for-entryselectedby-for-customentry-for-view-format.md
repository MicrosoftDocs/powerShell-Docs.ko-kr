---
title: 보기 (형식)의 CustomEntry에 대해 EntrySelectedBy의 TypeName 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76548af7-05bd-4d12-bf71-6fb69c434ef2
caps.latest.revision: 10
ms.openlocfilehash: c3dd761cd9b6c468d4833ea35b897ba5d425f598
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368072"
---
# <a name="typename-element-for-entryselectedby-for-customentry-for-view-format"></a>View에 대한 CustomEntry의 EntrySelectedBy에 대한 TypeName 요소(형식)

사용자 지정 컨트롤 뷰의이 정의를 사용 하는 .NET 형식을 지정 합니다. 정의에 대해 지정할 수 있는 형식 수에는 제한이 없습니다.

Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) CustomControl Element (format) Customentries 요소에 대 한 CustomControl의 customentries 요소 view (형식) EntrySelectedBy View (Format)의 CustomEntry에 대해 EntrySelectedBy View (Format) TypeName 요소의 CustomEntry 요소

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
|[View의 CustomEntry에 대 한 EntrySelectedBy 요소 (형식)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|이 사용자 지정 컨트롤 뷰 정의를 사용 하는 .NET 형식 또는이 정의를 사용 하기 위해 존재 해야 하는 조건을 정의 합니다.|

## <a name="text-value"></a>텍스트 값

.NET 형식의 정규화 된 이름 (예: `System.IO.DirectoryInfo`)을 지정 합니다.

## <a name="remarks"></a>설명

각 사용자 지정 컨트롤 뷰 정의에는 하나 이상의 유형 이름, 선택 집합 또는 선택 조건이 정의 되어 있어야 합니다.

사용자 지정 컨트롤 뷰의 구성 요소에 대 한 자세한 내용은 [사용자 지정 컨트롤 만들기](./creating-custom-controls.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[사용자 지정 컨트롤 만들기](./creating-custom-controls.md)

[View의 CustomEntry에 대 한 EntrySelectedBy 요소 (형식)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[PowerShell 서식 파일 작성](./writing-a-powershell-formatting-file.md)
