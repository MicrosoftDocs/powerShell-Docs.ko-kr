---
title: DisplayError 요소 (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 45c45800-a87d-456e-b07c-12d4d8c27c67
caps.latest.revision: 8
ms.openlocfilehash: 2c6a3d678ca68dc0d189f6ab981fdea5fef894cb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066263"
---
# <a name="displayerror-element-format"></a>DisplayError 요소(형식)

오류가 발생 하는 데이터의 일부를 표시 하는 경우 문자열 #ERR 표시 되도록 지정 합니다.

구성 요소 (형식) DefaultSettings (형식) DisplayError 요소 (형식)

## <a name="syntax"></a>구문

```xml
<DisplayError/>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `DisplayError` 요소입니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[DefaultSettings 요소 (형식)](./defaultsettings-element-format.md)|서식 파일의 모든 뷰에 적용 되는 일반적인 설정을 정의 합니다.|

## <a name="remarks"></a>설명

기본적으로 데이터를 표시 하는 동안 오류가 발생 하는 경우는 데이터의 위치를 비워 둡니다. 이 요소는 #ERR 문자열을 true로 설정 된 경우 표시 됩니다.

## <a name="see-also"></a>참고 항목

[DefaultSettings 요소 (형식)](./defaultsettings-element-format.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
