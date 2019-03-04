---
title: ListEntry 요소 ListControl (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6d16bca8-d025-432d-aa84-8b607b8af3ae
caps.latest.revision: 12
ms.openlocfilehash: 1a3bafd4ca94aee70e869c699f7a4ef8befc5511
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862249"
---
# <a name="listentry-element-for-listcontrol-format"></a>ListControl에 대한 ListEntry 요소(형식)

목록 보기의 정의 제공 합니다.

구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) ListControl 요소 (형식) ListEntries 요소 (형식) ListEntry 요소 (형식)

## <a name="syntax"></a>구문

```xml
<ListEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `ListEntry` 요소입니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[ListEntry (형식)에 대 한 EntrySelectedBy 요소](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|선택적 요소입니다.<br /><br /> 이 목록 뷰 정의 또는이 정의를 사용할 수 있어야 하는 조건을 사용 하는.NET 개체를 정의 합니다.|
|[ListItems 요소 (형식)](./listitems-element-for-listentry-for-listcontrol-format.md)|필수 요소입니다.<br /><br /> 속성 및 값을 목록 보기에서 표시 하는 스크립트를 정의 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[ListEntries 요소 (형식)](./listentries-element-for-listcontrol-format.md)|목록 보기의 정의 제공합니다.|

## <a name="remarks"></a>설명

목록 뷰를 목록 형식으로 속성 값 이나 각 개체에 대 한 스크립트 값을 표시 하는 경우 목록 보기에 대 한 자세한 내용은 참조 하세요. [목록 뷰를 만들면](./creating-a-list-view.md)합니다.

## <a name="example"></a>예제

목록 뷰를 정의 하는 XML 요소를 보여 주는이 예제는 [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) 개체입니다.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>...</ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>
</View>
```

## <a name="see-also"></a>참고 항목

[목록 뷰 만들기](./creating-a-list-view.md)

[ListEntry (형식)에 대 한 EntrySelectedBy 요소](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[ListEntries 요소 (형식)](./listentries-element-for-listcontrol-format.md)

[ListItems 요소 (형식)](./listitems-element-for-listentry-for-listcontrol-format.md)

[Windows PowerShell 형식 지정을 작성 하 고 파일 형식](./writing-a-powershell-formatting-file.md)
