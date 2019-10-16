---
title: WideEntry (형식)에 대 한 EntrySelectedBy의 TypeName 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 81a91c74-6229-4b64-aa2b-9123e8b7e9e5
caps.latest.revision: 11
ms.openlocfilehash: be35f6e9e2ad0b2d9a21a91c053aa0f70cafaf9c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361622"
---
# <a name="typename-element-for-entryselectedby-for-wideentry-format"></a>WideEntry의 EntrySelectedBy에 대한 TypeName 요소(형식)

정의에 대 한 .NET 유형을 지정 합니다. 이 개체가 표시 될 때마다 정의가 사용 됩니다.

Configuration 요소 (Format) ViewDefinitions 요소 (format) WideControl Element (format) WideEntries Element (format) WideEntry Element (format) EntrySelectedBy 요소에 대 한 WideEntry (Format) TypeName 요소에 대해 WideEntry ( 형식과

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
|[WideEntry (형식)에 대 한 EntrySelectedBy 요소](./entryselectedby-element-for-wideentry-format.md)|이 항목을 사용 하기 위해 존재 해야 하는 조건 또는이 광범위 한 항목을 사용 하는 .NET 형식을 정의 합니다.|

## <a name="text-value"></a>텍스트 값

.NET 형식의 정규화 된 이름 (예: `System.IO.DirectoryInfo`)을 지정 합니다.

## <a name="remarks"></a>설명

각 넓은 항목은 정의를 사용 하기 위해 있어야 하는 하나 이상의 .NET 유형, 선택 집합 또는 선택 조건을 지정 해야 합니다.

넓은 보기의 다른 구성 요소에 대 한 자세한 내용은 [넓은 뷰 만들기](./creating-a-wide-view.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[넓은 뷰 만들기](./creating-a-wide-view.md)

[WideEntry (형식)에 대 한 EntrySelectedBy 요소](./entryselectedby-element-for-wideentry-format.md)

[PowerShell 서식 파일 작성](./writing-a-powershell-formatting-file.md)
