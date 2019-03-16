---
title: GroupBy (형식)에 대 한 ScriptBlock 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30183927-6f0e-4717-b6f5-f07a6e134cfb
caps.latest.revision: 6
ms.openlocfilehash: f2f6b9af7740b1231881294c2f32bf97b5a1568b
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054428"
---
# <a name="scriptblock-element-for-groupby-format"></a>GroupBy에 대한 ScriptBlock 요소(형식)

해당 값이 변경 될 때마다 새 그룹을 시작 하는 스크립트를 지정 합니다.

구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) GroupBy 요소 GroupBy (형식)에 대 한 보기 (형식) ScriptBlock 요소에 대 한

## <a name="syntax"></a>구문

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `ScriptBlock` 요소입니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[뷰 (형식)에 대 한 GroupBy 요소](./groupby-element-for-view-format.md)|.NET 개체 그룹에 표시 되는 방식을 정의 합니다.|

## <a name="text-value"></a>텍스트 값

계산 되는 스크립트를 지정 합니다.

## <a name="remarks"></a>설명

Windows PowerShell이이 스크립트의 값이 변경 될 때마다 새 그룹을 시작 합니다.

이 요소를 지정 하는 경우 지정할 수 없습니다는 [PropertyName](http://msdn.microsoft.com/en-us/396dede0-039a-4a87-a5ef-3ecabb729676) 요소를 새 그룹을 시작 합니다.

## <a name="see-also"></a>참고 항목

[GroupBy (형식)에 대 한 PropertyName 요소](./propertyname-element-for-groupby-format.md)

[뷰 (형식)에 대 한 GroupBy 요소](./groupby-element-for-view-format.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
