---
title: GroupBy (형식)에 대 한 ScriptBlock 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e761e02a7910cd598449d564e827889162da9f25
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787685"
---
# <a name="scriptblock-element-for-groupby-format"></a>GroupBy에 대한 ScriptBlock 요소(형식)

값이 변경 될 때마다 새 그룹을 시작 하는 스크립트를 지정 합니다.

구성 요소 (Format) ViewDefinitions 요소 (Format) View 요소 (Format) GroupBy 요소에 대 한 groupby 요소 (형식)

## <a name="syntax"></a>구문

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `ScriptBlock` .

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[View에 대한 GroupBy 요소(형식)](./groupby-element-for-view-format.md)|.NET 개체 그룹이 표시 되는 방법을 정의 합니다.|

## <a name="text-value"></a>텍스트 값

평가 되는 스크립트를 지정 합니다.

## <a name="remarks"></a>설명

PowerShell은이 스크립트의 값이 변경 될 때마다 새 그룹을 시작 합니다.

이 요소를 지정 하면 새 그룹을 시작 하는 [PropertyName](propertyname-element-for-groupby-format.md) 요소를 지정할 수 없습니다.

## <a name="see-also"></a>참고 항목

[GroupBy에 대한 PropertyName 요소(형식)](propertyname-element-for-groupby-format.md)

[View에 대한 GroupBy 요소(형식)](groupby-element-for-view-format.md)

[PowerShell 형식 지정 파일 작성](writing-a-powershell-formatting-file.md)
