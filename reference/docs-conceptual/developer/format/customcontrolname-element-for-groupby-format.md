---
title: GroupBy (형식)에 대 한 CustomControlName 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 473d9b56-521b-479a-8010-67fe9f040063
caps.latest.revision: 8
ms.openlocfilehash: 3a386eff95044eae573c255a451c5c8b8f16714d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368882"
---
# <a name="customcontrolname-element-for-groupby-format"></a>GroupBy에 대한 CustomControlName 요소(형식)

새 그룹을 표시 하는 데 사용 되는 사용자 지정 컨트롤의 이름을 지정 합니다. 이 요소는 테이블, 목록, 전체 또는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.

Configuration 요소 (Format) Viewcontrolelement (Format) View Element (format) GroupBy 요소 (GroupBy)의 CustomControlName 요소 (형식)

## <a name="syntax"></a>구문

```xml
<CustomControlName>ControlName</CustomControlName>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 `CustomControlName` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[보기에 대 한 GroupBy 요소 (형식)](./groupby-element-for-view-format.md)|Windows PowerShell에서 새로운 개체 그룹을 표시 하는 방법을 정의 합니다.|

## <a name="text-value"></a>텍스트 값

새 그룹을 표시 하는 데 사용 되는 사용자 지정 컨트롤의 이름을 지정 합니다.

## <a name="remarks"></a>설명

서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 만들 수 있으며, 특정 뷰에서 사용할 수 있는 뷰 컨트롤을 만들 수 있습니다. 다음 요소는 이러한 사용자 지정 컨트롤의 이름을 지정 합니다.

- [구성 컨트롤에 대 한 컨트롤의 Name 요소 (형식)](./name-element-for-control-for-controls-for-configuration-format.md)

- [View 컨트롤의 컨트롤에 대 한 Name 요소 (Format)](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>참고 항목

[보기에 대 한 GroupBy 요소 (형식)](./groupby-element-for-view-format.md)

[구성 컨트롤에 대 한 컨트롤의 Name 요소 (형식)](./name-element-for-control-for-controls-for-configuration-format.md)

[View 컨트롤의 컨트롤에 대 한 Name 요소 (Format)](./name-element-for-control-for-controls-for-view-format.md)

[PowerShell 서식 파일 작성](./writing-a-powershell-formatting-file.md)
