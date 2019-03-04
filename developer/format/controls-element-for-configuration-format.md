---
title: 구성 (형식)에 대 한 controls 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4d4ef63d-5866-4319-ba00-7ed96de26821
caps.latest.revision: 18
ms.openlocfilehash: ac9f7ff08f6e87ef83b5a2fe23fc58ee2651566d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861179"
---
# <a name="controls-element-for-configuration-format"></a>Configuration에 대한 Controls 요소(형식)

서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 정의 합니다.

구성 (형식)의 구성 요소 (형식) 컨트롤 요소

## <a name="syntax"></a>구문

```xml
<Controls>
  <Control>...</Control>
</Controls>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `Controls` 요소입니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[구성 (형식)에 대 한 컨트롤에 대 한 control 요소](./control-element-for-controls-for-configuration-format.md)|필수 요소입니다.<br /><br /> 서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 정의 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[구성 요소 (형식)](./configuration-element-format.md)|서식 파일의 최상위 요소를 나타냅니다.|

## <a name="remarks"></a>설명

임의 개수의 공용 컨트롤을 만들 수 있습니다. 각 컨트롤에 대 한 컨트롤 및 컨트롤의 구성 요소를 참조 하는 데 사용 되는 이름을 지정 해야 합니다.

## <a name="see-also"></a>참고 항목

[구성 요소 (형식)](./configuration-element-format.md)

[구성 (형식)에 대 한 컨트롤에 대 한 control 요소](./control-element-for-controls-for-configuration-format.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
