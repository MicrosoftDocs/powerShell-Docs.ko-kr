---
ms.date: 09/13/2016
ms.topic: reference
title: WideControl의 WideItem에 대한 FormatString 요소(형식)
description: WideControl의 WideItem에 대한 FormatString 요소(형식)
ms.openlocfilehash: f67a18e3ec4f1323e7f9be8904db518c679d53e5
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667881"
---
# <a name="formatstring-element-for-wideitem-for-widecontrol-format"></a>WideControl의 WideItem에 대한 FormatString 요소(형식)

속성 또는 스크립트 값이 뷰에 표시 되는 방법을 정의 하는 형식 패턴을 지정 합니다.

Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) WideControl element (format) WideEntries element (format) WideEntry Element for WideControl (format) WideItem 요소의 WideControl for WideItem (형식)

## <a name="syntax"></a>구문

```xml
<FormatString>PropertyPattern</FormatString>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `FormatString` .

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[WideControl에 대한 WideItem 요소(형식)](./wideitem-element-for-widecontrol-format.md)|목록 뷰의 행에 값이 표시 되는 속성 또는 스크립트를 정의 합니다.|

## <a name="text-value"></a>텍스트 값

데이터의 형식을 지정 하는 데 사용 되는 패턴을 지정 합니다. 예를 들어이 패턴을 사용 하 여 [System. Timespan](/dotnet/api/System.TimeSpan): {0: MMM} {0: dd} {0: HH}: {0: mm} 형식의 속성 값에 서식을 지정할 수 있습니다.

## <a name="remarks"></a>설명

형식 문자열은 테이블 뷰, 목록 뷰, 넓은 뷰 또는 사용자 지정 뷰를 만들 때 사용할 수 있습니다. 뷰에 표시 되는 값의 서식을 지정 하는 방법에 대 한 자세한 내용은 [표시 된 데이터 서식 지정](./formatting-displayed-data.md)을 참조 하세요.

넓은 보기에서 서식 문자열을 사용 하는 방법에 대 한 자세한 내용은 [넓은 뷰 만들기](./creating-a-wide-view.md)를 참조 하세요.

## <a name="example"></a>예제

다음 예제에서는 속성의 값에 대 한 서식 문자열을 정의 하는 방법을 보여 줍니다 `StartTime` .

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

## <a name="see-also"></a>참고 항목

[넓게 보기 만들기](./creating-a-wide-view.md)

[WideControl에 대한 WideItem 요소(형식)](./wideitem-element-for-widecontrol-format.md)

[Windows PowerShell 서식 지정 및 형식 파일 작성](./writing-a-powershell-formatting-file.md)
