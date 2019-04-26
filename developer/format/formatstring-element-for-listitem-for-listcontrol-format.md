---
title: FormatString 요소 ListControl (형식)에 대 한 ListItem | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd2cac66-88bb-449f-9d47-bd2cd4fe1801
caps.latest.revision: 13
ms.openlocfilehash: e6024ec4f7fc490c92408047c8c15c775e45bf9d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065623"
---
# <a name="formatstring-element-for-listitem-for-listcontrol--format"></a>ListControl의 ListItem에 대한 FormatString 요소(형식)

스크립트나 속성 값이 표시 되는 방식을 정의 하는 형식 패턴을 지정 합니다.

구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) ListControl 요소 (형식) ListEntries 요소 ListControl (형식)에 대 한 ListControl (형식) ListItems 요소에 대 한 ListEntry 요소의 ListControl (형식) FormatString 요소 ListControl (형식)에 대 한 ListItem ListControl (형식)에 대 한 ListItem 요소

## <a name="syntax"></a>구문

```xml
<FormatString>PropertyPattern</FormatString>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `FormatString` 요소입니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[ListItem 요소 (형식)](./listitem-element-for-listitems-for-listcontrol-format.md)|속성 또는 목록 보기 행에 해당 값이 표시 되는 스크립트를 정의 합니다.|

## <a name="text-value"></a>텍스트 값

데이터의 형식을 지정 하는 데 사용 되는 패턴을 지정 합니다. 예를 들어, 형식의 모든 속성의 값 형식을 지정 하려면이 패턴을 사용할 수 있습니다 [System.Timespan](/dotnet/api/System.TimeSpan): {0: MMM} {0:dd} {{0:hh}: {{0:mm}&fmt=csv}.

## <a name="remarks"></a>설명

테이블 뷰, 목록 뷰, 와이드 뷰 또는 사용자 지정 보기를 만들 때 형식 문자열을 사용할 수 있습니다. 보기에 표시 된 값 형식에 대 한 자세한 내용은 참조 하세요. [표시 된 데이터 서식 지정](./formatting-displayed-data.md)합니다.

형식 문자열을 사용 하 여 목록 보기에 대 한 자세한 내용은 참조 하세요. [목록 보기 만들기](./creating-a-list-view.md)합니다.

## <a name="example"></a>예제

다음 예제에서는 값의 서식 지정 문자열을 정의 하는 방법의 `StartTime` 속성입니다.

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

## <a name="see-also"></a>참고 항목

[목록 뷰 만들기](./creating-a-list-view.md)

[ListItem 요소 (형식)](./listitem-element-for-listitems-for-listcontrol-format.md)

[Windows PowerShell 형식 지정을 작성 하 고 파일 형식](./writing-a-powershell-formatting-file.md)
