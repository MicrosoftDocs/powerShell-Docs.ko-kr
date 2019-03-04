---
title: GroupBy (형식)에 대 한 EntrySelectedBy TypeName 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b8b6739b-770c-432a-95ab-551c7507c51f
caps.latest.revision: 6
ms.openlocfilehash: 3b5ce60d3a0d76988af48f49445a5478a415d498
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861669"
---
# <a name="typename-element-for-entryselectedby-for-groupby-format"></a>GroupBy의 EntrySelectedBy에 대한 TypeName 요소(형식)

사용자 지정 컨트롤의이 정의 사용 하는.NET 형식을 지정 합니다. 이 요소는 새 개체 그룹에 표시 되는 방식을 정의 하는 경우에 사용 됩니다.

구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) GroupBy 요소 CustomControl GroupBy (형식) CustomEntry 요소에 대 한 GroupBy (형식) CustomEntries 요소에 대 한 보기 (형식) CustomControl 요소에 대 한 CustomControl CustomEntry EntrySelectedBy GroupBy (형식)에 대 한 TypeName 요소 GroupBy (형식)에 대 한 GroupBy (형식) EntrySelectedBy 요소에

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
|[GroupBy (형식)에 대 한 CustomEntry EntrySelectedBy 요소](./entryselectedby-element-for-customentry-for-groupby-format.md)|이 컨트롤 정의 또는이 정의를 사용할 수 있어야 하는 조건을 사용 하는.NET 형식을 정의 합니다.|

## <a name="text-value"></a>텍스트 값

와 같이.NET 형식의 정규화 된 이름을 지정 `System.IO.DirectoryInfo`합니다.

## <a name="remarks"></a>설명

각 컨트롤 정의 형식 이름, 선택 집합 또는 정의 된 선택 조건을 하나 이상 있어야 합니다.

사용자 지정 컨트롤 보기의 구성 요소에 대 한 자세한 내용은 참조 [사용자 지정 컨트롤 만들기](./creating-custom-controls.md)합니다.

## <a name="see-also"></a>참고 항목

[사용자 지정 컨트롤 만들기](./creating-custom-controls.md)

[GroupBy (형식)에 대 한 CustomEntry EntrySelectedBy 요소](./entryselectedby-element-for-customentry-for-groupby-format.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
