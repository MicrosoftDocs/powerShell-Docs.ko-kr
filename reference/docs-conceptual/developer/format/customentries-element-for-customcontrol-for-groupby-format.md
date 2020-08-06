---
title: GroupBy (형식)의 CustomControl에 대 한 CustomEntries 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 2221d1bb94159697ff10466e4606d6d54e117e30
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785951"
---
# <a name="customentries-element-for-customcontrol-for-groupby-format"></a>GroupBy의 CustomControl에 대한 CustomEntries 요소(형식)

컨트롤에 대 한 정의를 제공 합니다. 이 요소는 새 개체 그룹이 표시 되는 방법을 정의 하는 데 사용 됩니다.

구성 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format)의 groupby 요소에 대 한 groupby 요소 (format) CustomControl 요소에 대 한 groupby 요소 (형식)의 경우 CustomControl에 대 한 CustomEntries 요소

## <a name="syntax"></a>구문

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `CustomEntries` . 지정할 수 있는 자식 요소 수에 대 한 최대 제한은 없습니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[GroupBy의 CustomControl에 대한 CustomEntry 요소(형식)](./customentry-element-for-customcontrol-for-groupby-format.md)|필수적 요소입니다.<br /><br /> 컨트롤의 정의를 제공 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[GroupBy에 대한 CustomControl 요소(형식)](./customcontrol-element-for-groupby-format.md)|새 그룹을 표시 하는 사용자 지정 컨트롤을 정의 합니다.|

## <a name="remarks"></a>설명

대부분의 경우 컨트롤에는 단일 요소에 지정 된 정의가 하나만 있습니다 `CustomEntry` . 그러나 같은 컨트롤을 사용 하 여 다른 그룹을 표시 하려는 경우에는 여러 정의를 제공할 수 있습니다. 이러한 경우 그룹의 요소를 정의할 수 있습니다 `CustomEntry` .

## <a name="see-also"></a>참고 항목

[View에 대한 Controls의 CustomEntries에 대한 CustomEntry 요소(형식)](./customentry-element-for-customentries-for-controls-for-view-format.md)

[GroupBy에 대한 CustomControl 요소(형식)](./customcontrol-element-for-groupby-format.md)

[PowerShell 형식 지정 파일 작성](./writing-a-powershell-formatting-file.md)
