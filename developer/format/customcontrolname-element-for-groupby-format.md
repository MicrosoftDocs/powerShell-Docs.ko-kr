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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066546"
---
# <a name="customcontrolname-element-for-groupby-format"></a>GroupBy에 대한 CustomControlName 요소(형식)

새 그룹을 표시 하는 데 사용 되는 사용자 지정 컨트롤의 이름을 지정 합니다. 이 요소는 테이블, 목록, 와이드 또는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.

구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) GroupBy 요소 (형식) 보기 CustomControlName 요소의 GroupBy (형식)에 대 한

## <a name="syntax"></a>구문

```xml
<CustomControlName>ControlName</CustomControlName>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 부모 요소는 `CustomControlName` 요소입니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[뷰 (형식)에 대 한 GroupBy 요소](./groupby-element-for-view-format.md)|Windows PowerShell에서 개체의 새 그룹을 표시 하는 방법을 정의 합니다.|

## <a name="text-value"></a>텍스트 값

새 그룹을 표시 하는 데 사용 되는 사용자 지정 컨트롤의 이름을 지정 합니다.

## <a name="remarks"></a>설명

서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 만들 수 있습니다 하 고 특정 뷰에서 사용할 수 있는 뷰 컨트롤을 만들 수 있습니다. 다음 요소에는 이러한 사용자 지정 컨트롤의 이름을 지정합니다.

- [구성 (형식)에 대 한 컨트롤에 대 한 컨트롤의 name 요소](./name-element-for-control-for-controls-for-configuration-format.md)

- [뷰 (형식)에 대 한 컨트롤에 대 한 컨트롤의 name 요소](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>참고 항목

[뷰 (형식)에 대 한 GroupBy 요소](./groupby-element-for-view-format.md)

[구성 (형식)에 대 한 컨트롤에 대 한 컨트롤의 name 요소](./name-element-for-control-for-controls-for-configuration-format.md)

[뷰 (형식)에 대 한 컨트롤에 대 한 컨트롤의 name 요소](./name-element-for-control-for-controls-for-view-format.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
