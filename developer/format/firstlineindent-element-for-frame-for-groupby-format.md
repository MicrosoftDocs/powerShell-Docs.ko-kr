---
title: GroupBy (형식)에 대 한 프레임에 대 한 FirstLineIndent 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33be3b9e-53c8-433f-8c11-c65b0d46744c
caps.latest.revision: 6
ms.openlocfilehash: 9ba6fc1b9924a4b0d5b56ee15290a2293217403c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065855"
---
# <a name="firstlineindent-element-for-frame-for-groupby-format"></a>GroupBy의 Frame에 대한 FirstLineIndent 요소(형식)

데이터의 첫 번째 줄은 오른쪽으로 옮겨집니다 문자 수를 지정 합니다. 이 요소는 새 개체 그룹에 표시 되는 방식을 정의 하는 경우에 사용 됩니다.

구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) GroupBy 요소 CustomControl GroupBy (형식) CustomEntry 요소에 대 한 GroupBy (형식) CustomEntries 요소에 대 한 보기 (형식) CustomControl 요소에 대 한 CustomControl CustomEntry CustomItem GroupBy (형식)에 대 한 프레임 FirstLineIndent 요소 GroupBy (형식)에 대 한 GroupBy (형식) 프레임 요소에 대 한 GroupBy (형식) CustomItem 요소에

## <a name="syntax"></a>구문

```xml
<FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `FirstLineIndent` 요소입니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[GroupBy (형식)에 대 한 CustomItem 프레임 요소](./frame-element-for-customitem-for-groupby-format.md)|왼쪽 또는 오른쪽에 데이터를 이동 하는 등 데이터를 표시 하는 방법을 정의 합니다.|

## <a name="text-value"></a>텍스트 값

데이터의 첫 번째 줄을 이동 하려는 문자 수를 지정 합니다.

## <a name="remarks"></a>설명

이 요소를 지정 하는 경우를 지정할 수 없습니다는 [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) 요소입니다.

## <a name="see-also"></a>참고 항목

[GroupBy (형식)에 대 한 프레임에 대 한 FirstLineHanging 요소](./firstlinehanging-element-for-frame-for-groupby-format.md)

[GroupBy (형식)에 대 한 CustomItem 프레임 요소](./frame-element-for-customitem-for-groupby-format.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
