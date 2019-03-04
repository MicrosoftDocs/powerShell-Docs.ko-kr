---
title: 구성 (형식)에 대 한 컨트롤에 대 한 SelectionCondition TypeName 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 477c8711-fffc-4f92-af45-6d4f80990474
caps.latest.revision: 7
ms.openlocfilehash: 60f02f3240c5574e1b1f9027b060bd9af89a11d2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853599"
---
# <a name="typename-element-for-selectioncondition-for-controls-for-configuration-format"></a>Configuration에 대한 Controls의 SelectionCondition에 대한 TypeName 요소(형식)

조건이 트리거하는.NET 형식을 지정 합니다. 이 요소는 서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 정의할 때 사용 됩니다.

구성 (형식)에 대 한 컨트롤에 대 한 CustomControl CustomEntries 요소에 대 한 컨트롤에 대 한 구성 (형식) CustomControl 요소에 대 한 컨트롤에 대 한 Control 요소 구성 (형식)의 구성 요소 (형식) 컨트롤 요소 CustomControl CustomEntry 구성 (형식)에 대 한 CustomEntry에 대 한 EntrySelectedBy SelectionCondition 요소에 대 한 컨트롤에 대 한 구성 (형식) EntrySelectedBy 요소에 대 한 컨트롤에 대 한 구성 (형식) CustomEntry 요소 구성 (형식) 구성 (형식)에 대 한 컨트롤에 대 한 SelectionCondition TypeName 요소

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
|[CustomEntry 구성 (형식)에 대 한 EntrySelectedBy SelectionCondition 요소](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|사용할 컨트롤 정의에 있어야 하는 조건을 정의 합니다.|

## <a name="text-value"></a>텍스트 값

와 같이.NET 형식의 정규화 된 이름을 지정 `System.IO.DirectoryInfo`합니다.

## <a name="remarks"></a>설명

## <a name="see-also"></a>참고 항목

[CustomEntry 구성 (형식)에 대 한 EntrySelectedBy SelectionCondition 요소](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
