---
title: ListControl 요소 (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 37beeb0b-7a81-4747-becb-e309e17278fb
caps.latest.revision: 12
ms.openlocfilehash: 7a117c25b0d117dc846ba8e060e31e838b5edd52
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065260"
---
# <a name="listcontrol-element-format"></a>ListControl 요소(형식)

뷰를 목록 형식으로 정의합니다.

구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) ListControl 요소 (형식)

## <a name="syntax"></a>구문

```xml
<ListControl>
  <ListEntries>...</ListEntries>
</ListControl>

```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `ListControl` 요소입니다. 이 요소는 단일 자식 요소만을 포함 해야 합니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[ListEntries 요소 (형식)](./listentries-element-for-listcontrol-format.md)|필수 요소입니다.<br /><br /> 목록 보기의 정의 제공합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[뷰 요소 (형식)](./view-element-format.md)|하나 이상의 개체의 멤버를 표시 하는 데 사용 되는 뷰를 정의 합니다.|

## <a name="remarks"></a>설명

목록 뷰를 만드는 방법에 대 한 자세한 내용은 참조 하세요. [목록 뷰를 만들면](./creating-a-list-view.md)합니다.

## <a name="example"></a>예제

이 예제에 대 한 목록 뷰를 표시 합니다 [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) 개체입니다.

```
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>...</ListEntry>
    </ListEntries>
  </ListControl>
</View>
```

## <a name="see-also"></a>참고 항목

[뷰 요소 (형식)](./view-element-format.md)

[ListEntries 요소 (형식)](./listentries-element-for-listcontrol-format.md)

[목록 뷰 만들기](./creating-a-list-view.md)

[Windows PowerShell 형식 지정을 작성 하 고 파일 형식](./writing-a-powershell-formatting-file.md)
