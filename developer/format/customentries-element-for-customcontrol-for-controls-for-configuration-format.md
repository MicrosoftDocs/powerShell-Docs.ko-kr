---
title: 구성 (형식)에 대 한 컨트롤에 대 한 CustomControl CustomEntries 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 80fc4de2-208f-4506-9a6a-c2675bb83be4
caps.latest.revision: 11
ms.openlocfilehash: abef6c91500f665c2366f221496d4cfd6444f5c9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066603"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-configuration-format"></a>Configuration에 대한 Controls의 CustomControl에 대한 CustomEntries 요소(형식)

공용 컨트롤의 정의 제공합니다. 이 요소는 서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 정의할 때 사용 됩니다.

CustomControl Configuration (구성 (형식) CustomEntries 요소에 대 한 컨트롤에 대 한 구성 (형식) CustomControl 요소에 대 한 컨트롤에 대 한 Control 요소 구성 (형식)의 구성 요소 (형식) 컨트롤 요소 형식)

## <a name="syntax"></a>구문

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>

```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `CustomEntries` 요소입니다. 하나 이상의 자식 요소를 지정 해야 합니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[구성 (형식)에 대 한 컨트롤에 대 한 CustomControl CustomEntry 요소](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|공용 컨트롤의 정의 제공 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[구성 (형식)에 대 한 컨트롤에 대 한 CustomControl 요소](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|공용 컨트롤을 정의합니다.|

## <a name="remarks"></a>설명

대부분의 경우 컨트롤에 단일에 정의 되어 있는 하나만 정의 `CustomEntry` 요소입니다. 그러나는 다른.NET 개체를 표시 하려면 동일한 컨트롤을 사용 하려는 경우 정의가 여러 개 있을 수 있습니다. 이러한 경우에 정의할 수 있습니다는 `CustomEntry` 각 개체 또는 개체 집합에 대 한 요소입니다.

## <a name="see-also"></a>참고 항목

[구성 (형식)에 대 한 컨트롤에 대 한 CustomControl 요소](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[구성 (형식)에 대 한 컨트롤에 대 한 CustomControl CustomEntry 요소](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
