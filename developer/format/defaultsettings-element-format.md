---
title: DefaultSettings 요소 (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 41c56499-ee20-4821-830a-478fdcc33f83
caps.latest.revision: 11
ms.openlocfilehash: bc95c62222eb2806f92499257a397c2e4ec5dbab
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066348"
---
# <a name="defaultsettings-element-format"></a>DefaultSettings 요소(형식)

서식 파일의 모든 뷰에 적용 되는 일반적인 설정을 정의 합니다. 일반적인 설정의 컬렉션 확장 되는 방법을 정의 하는 테이블 및 기타 자동 줄 바꿈 오류 표시 포함 됩니다.

구성 요소 (형식) DefaultSettings 요소 (형식)

## <a name="syntax"></a>구문

```xml
<DefaultSettings>
  <ShowError/>
  <DisplayError/>
 <PropertyCountForTable>NumberOfProperties</PropertyCountFortable>
  <WrapTables/>
  <EnumerableExpansions>...</EnumerableExpansions>
</DefaultSettings>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `DefaultSettings` 요소입니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[DisplayError 요소 (형식)](./displayerror-element-format.md)|선택적 요소입니다.<br /><br /> 일부 데이터를 표시 하는 동안 오류가 발생 하면 #ERR 문자열 표시 되도록 지정 합니다.|
|[EnumerableExpansions 요소 (형식)](./enumerableexpansions-element-format.md)|선택적 요소입니다.<br /><br /> .NET 개체 뷰의 표시 될 때 확장 되는 다양 한 방법을 정의 합니다.|
|[PropertyCountForTable (형식)](./propertycountfortable-element-format.md)|선택적 요소입니다.<br /><br /> 개체 표 보기에서 개체를 표시 해야 하는 속성의 최소 수를 지정 합니다.|
|[ShowError 요소 (형식)](./showerror-element-format.md)|선택적 요소입니다.<br /><br /> 일부 데이터를 표시 하는 동안 오류가 발생 하면 전체 오류 레코드 표시 되도록 지정 합니다.|
|[WrapTables 요소 (형식)](./wraptables-element-format.md)|선택적 요소입니다.<br /><br /> 테이블의 데이터 다음 줄으로 이동 되 면 열의 너비에 들어가지 않습니다 지정 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[구성 요소](./configuration-element-format.md)|서식 파일의 최상위 요소를 나타냅니다.|

## <a name="remarks"></a>설명

## <a name="see-also"></a>참고 항목

[구성 요소](./configuration-element-format.md)

[DisplayError 요소 (형식)](./displayerror-element-format.md)

[EnumerableExpansions 요소 (형식)](./enumerableexpansions-element-format.md)

[PropertyCountForTable (형식)](./propertycountfortable-element-format.md)

[ShowError 요소 (형식)](./showerror-element-format.md)

[WrapTables 요소 (형식)](./wraptables-element-format.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
