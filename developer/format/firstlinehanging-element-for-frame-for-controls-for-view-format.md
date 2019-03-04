---
title: 뷰 (형식)에 대 한 컨트롤에 대 한 프레임에 대 한 FirstLineHanging 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53694f08-57f7-4185-b443-1636a0918afc
caps.latest.revision: 8
ms.openlocfilehash: 387340cd9b0aae2ad0419b187d96ab4fee183d5a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858719"
---
# <a name="firstlinehanging-element-for-frame-for-controls-for-view-format"></a>View에 대한 Controls의 Frame에 대한 FirstLineHanging 요소(형식)

데이터의 첫 번째 줄은 왼쪽으로 이동 하는 문자 수를 지정 합니다. 이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의할 때 사용 됩니다.

구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) 컨트롤 요소 (형식) 컨트롤 요소에 대 한 보기 (형식) CustomEntries 요소에 대 한 컨트롤에 대 한 컨트롤에 대 한 보기 (형식) CustomControl 요소에 대 한 컨트롤에 대 한 CustomControl CustomEntries CustomEntry 컨트롤의 보기 (형식) FirstLineHanging 요소에 대 한 컨트롤에 대 한 CustomItem (형식) 보기 프레임 요소에 대 한 보기 (형식) CustomItem 요소에는 컨트롤에 대 한 보기 (형식) CustomEntry 요소에 대 한 컨트롤 (형식) 보기의 프레임

## <a name="syntax"></a>구문

```xml
<FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `FirstLineHanging` 요소입니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[뷰 (형식)에 대 한 컨트롤에 대 한 CustomItem 프레임 요소](./frame-element-for-customitem-for-controls-for-view-format.md)|왼쪽 또는 오른쪽에 데이터를 이동 하는 등 데이터를 표시 하는 방법을 정의 합니다.|

## <a name="text-value"></a>텍스트 값

데이터의 첫 번째 줄을 이동 하려는 문자 수를 지정 합니다.

## <a name="remarks"></a>설명

이 요소를 지정 하는 경우를 지정할 수 없습니다는 [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) 요소입니다.

## <a name="see-also"></a>참고 항목

[뷰 (형식)에 대 한 컨트롤에 대 한 프레임에 대 한 FirstLineIndent 요소](./firstlineindent-element-for-frame-for-controls-for-view-format.md)

[뷰 (형식)에 대 한 컨트롤에 대 한 CustomItem 프레임 요소](./frame-element-for-customitem-for-controls-for-view-format.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
