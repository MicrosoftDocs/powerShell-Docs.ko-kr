---
title: GroupBy (형식)에 대 한 CustomControl 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: b8265e872d34ea5dbcedfaa1668d21df8c3b35eb
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786070"
---
# <a name="customcontrol-element-for-groupby-format"></a>GroupBy에 대한 CustomControl 요소(형식)

새 그룹을 표시 하는 사용자 지정 컨트롤을 정의 합니다.

구성 요소 (Format) ViewDefinitions 요소 (Format) View 요소 (format) GroupBy 요소 (형식)에 대 한 View (Format) CustomControl 요소

## <a name="syntax"></a>구문

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
<CustomControl>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `CustomControl` . 원하는 수의 자식 요소를 지정 하 고 원하는 순서 대로 나열할 수 있습니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[GroupBy의 CustomControl에 대한 CustomEntries 요소(형식)](./customentries-element-for-customcontrol-for-groupby-format.md)|필수적 요소입니다.<br /><br /> 컨트롤에 대 한 정의를 제공 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[View에 대한 GroupBy 요소(형식)](./groupby-element-for-view-format.md)|Windows PowerShell에서 새로운 개체 그룹을 표시 하는 방법을 정의 합니다.|

## <a name="remarks"></a>설명

## <a name="see-also"></a>참고 항목

[GroupBy의 CustomControl에 대한 CustomEntries 요소(형식)](./customentries-element-for-customcontrol-for-groupby-format.md)

[View에 대한 GroupBy 요소(형식)](./groupby-element-for-view-format.md)

[PowerShell 형식 지정 파일 작성](./writing-a-powershell-formatting-file.md)
