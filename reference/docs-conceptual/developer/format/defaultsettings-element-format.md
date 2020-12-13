---
ms.date: 09/13/2016
ms.topic: reference
title: DefaultSettings 요소(형식)
description: DefaultSettings 요소(형식)
ms.openlocfilehash: 1c2055b38a416fe2d75fa20c6c87e92d9eed4285
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666725"
---
# <a name="defaultsettings-element-format"></a>DefaultSettings 요소(형식)

서식 파일의 모든 뷰에 적용 되는 일반 설정을 정의 합니다. 일반 설정에는 오류 표시, 테이블에 텍스트 줄 바꿈, 컬렉션이 확장 되는 방법 정의 등이 포함 됩니다.

Configuration 요소 (Format) DefaultSettings 요소 (Format)

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

다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `DefaultSettings` .

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[DisplayError 요소(형식)](./displayerror-element-format.md)|선택적 요소입니다.<br /><br /> 데이터의 일부를 표시 하는 동안 오류가 발생 하는 경우 문자열 #ERR 표시 되도록 지정 합니다.|
|[EnumerableExpansions 요소(형식)](./enumerableexpansions-element-format.md)|선택적 요소입니다.<br /><br /> .NET 개체가 뷰에 표시 될 때 확장 되는 다양 한 방법을 정의 합니다.|
|[PropertyCountForTable (형식)](./propertycountfortable-element-format.md)|선택적 요소입니다.<br /><br /> 개체가 테이블 뷰에 개체를 표시 하는 데 필요한 최소 속성 수를 지정 합니다.|
|[ShowError 요소(형식)](./showerror-element-format.md)|선택적 요소입니다.<br /><br /> 데이터 조각을 표시 하는 동안 오류가 발생 하면 전체 오류 레코드가 표시 되도록 지정 합니다.|
|[WrapTables 요소(형식)](./wraptables-element-format.md)|선택적 요소입니다.<br /><br /> 열의 너비에 맞지 않는 경우 테이블의 데이터를 다음 줄로 이동 하도록 지정 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[구성 요소](./configuration-element-format.md)|서식 파일의 최상위 요소를 나타냅니다.|

## <a name="remarks"></a>설명

## <a name="see-also"></a>참고 항목

[구성 요소](./configuration-element-format.md)

[DisplayError 요소(형식)](./displayerror-element-format.md)

[EnumerableExpansions 요소(형식)](./enumerableexpansions-element-format.md)

[PropertyCountForTable (형식)](./propertycountfortable-element-format.md)

[ShowError 요소(형식)](./showerror-element-format.md)

[WrapTables 요소(형식)](./wraptables-element-format.md)

[PowerShell 형식 지정 파일 작성](./writing-a-powershell-formatting-file.md)
