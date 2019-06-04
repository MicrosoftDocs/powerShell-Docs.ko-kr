---
title: GroupBy (형식)에 대 한 CustomControl CustomEntries 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: af83c0f6-7fdd-4aa0-af12-efc62f632974
caps.latest.revision: 7
ms.openlocfilehash: f073142bf836ae892f161cf8c36ed16c35e311f5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066545"
---
# <a name="customentries-element-for-customcontrol-for-groupby-format"></a>GroupBy의 CustomControl에 대한 CustomEntries 요소(형식)

컨트롤에 대 한 정의 제공합니다. 이 요소는 새 개체 그룹에 표시 되는 방식을 정의 하는 경우에 사용 됩니다.

구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) GroupBy 요소 GroupBy (형식)에 대 한 CustomControl CustomEntries 요소 GroupBy (형식)에 대 한 보기 (형식) CustomControl 요소에 대 한

## <a name="syntax"></a>구문

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 부모 요소는 `CustomEntries` 요소입니다. 지정할 수 있는 자식 요소의 수를 최대 제한은 없습니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[GroupBy (형식)에 대 한 CustomControl CustomEntry 요소](./customentry-element-for-customcontrol-for-groupby-format.md)|필수 요소입니다.<br /><br /> 컨트롤의 정의 제공합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[GroupBy (형식)에 대 한 CustomControl 요소](./customcontrol-element-for-groupby-format.md)|새 그룹을 표시 하는 사용자 지정 컨트롤을 정의 합니다.|

## <a name="remarks"></a>설명

대부분의 경우 컨트롤에 단일에서 지정 되는 정의가 하나만 `CustomEntry` 요소입니다. 그러나 동일한 컨트롤을 사용 하 여 다른 그룹을 표시 하려는 경우 여러 정의 제공 하는 것이 같습니다. 이러한 경우에 정의할 수 있습니다는 `CustomEntry` 그룹에 대 한 요소입니다.

## <a name="see-also"></a>참고 항목

[뷰 (형식)에 대 한 컨트롤에 대 한 CustomEntries CustomEntry 요소](./customentry-element-for-customentries-for-controls-for-view-format.md)

[GroupBy (형식)에 대 한 CustomControl 요소](./customcontrol-element-for-groupby-format.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
