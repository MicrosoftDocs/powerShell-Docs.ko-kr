---
title: EntrySelectedBy CustomEntry 보려면 (형식)에 대 한 TypeName 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76548af7-05bd-4d12-bf71-6fb69c434ef2
caps.latest.revision: 10
ms.openlocfilehash: c3dd761cd9b6c468d4833ea35b897ba5d425f598
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858839"
---
# <a name="typename-element-for-entryselectedby-for-customentry-for-view-format"></a>View에 대한 CustomEntry의 EntrySelectedBy에 대한 TypeName 요소(형식)

이 사용자 지정 컨트롤 뷰의이 정의 사용 하는.NET 형식을 지정 합니다. 형식 정의 대해 지정할 수 있는 수에 제한은 없습니다.

구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) CustomControl 요소 (형식) CustomEntries 요소 CustomControl CustomEntries EntrySelectedBy 보기 (형식)에 대 한 보기 (형식) CustomEntry 요소에 대 한 CustomEntry EntrySelectedBy CustomEntry 보려면 (형식)에 대 한 보기 (형식) TypeName 요소에 대 한 요소

## <a name="syntax"></a>구문

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `TypeName` 요소입니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[뷰 (형식)에 대 한 CustomEntry EntrySelectedBy 요소](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|이 사용자 지정 컨트롤 뷰 정의 사용 하는.NET 형식 또는이 정의를 사용할 수 있어야 하는 조건을 정의 합니다.|

## <a name="text-value"></a>텍스트 값

와 같이.NET 형식의 정규화 된 이름을 지정 `System.IO.DirectoryInfo`합니다.

## <a name="remarks"></a>설명

각 사용자 지정 컨트롤 뷰 정의 형식 이름, 선택 집합 또는 정의 된 선택 조건을 하나 이상 있어야 합니다.

사용자 지정 컨트롤 보기의 구성 요소에 대 한 자세한 내용은 참조 [사용자 지정 컨트롤 만들기](./creating-custom-controls.md)합니다.

## <a name="see-also"></a>참고 항목

[사용자 지정 컨트롤 만들기](./creating-custom-controls.md)

[뷰 (형식)에 대 한 CustomEntry EntrySelectedBy 요소](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
