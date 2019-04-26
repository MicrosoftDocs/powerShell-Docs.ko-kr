---
title: Name 요소 (형식) 보기에 대 한 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3a31010d-1db9-44ae-a7f3-6ed32cb641cb
caps.latest.revision: 16
ms.openlocfilehash: 097d20cb6a04635124d1f96823248df6095ca1af
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065073"
---
# <a name="name-element-for-view-format"></a>View에 대한 Name 요소(형식)

뷰를 식별 하는 데 사용 되는 이름을 지정 합니다.

구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) 이름 요소 (형식)

## <a name="syntax"></a>구문

```xml
<Name>ViewName</Name>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `Name` 요소입니다. 하나의 `Name` 각 보기에 대 한 요소를 사용할 수 있습니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[뷰 요소 (형식)](./view-element-format.md)|하나 이상의.NET 개체의 멤버를 표시 하는 데 사용 되는 뷰를 정의 합니다.|

## <a name="text-value"></a>텍스트 값

뷰에 대 한 고유한 이름을 지정 합니다. 이 이름에는 어떤 개체 또는 개체 집합을 사용 하 여 어떤 명령이 반환 된 개체 또는 이들의 조합으로 뷰를 뷰 (예: 테이블 뷰 또는 목록 보기)의 형식에 대 한 참조를 포함할 수 있습니다.

## <a name="remarks"></a>설명

다양 한 보기에 대 한 자세한 내용은 다음 항목을 참조 합니다. [테이블 뷰](./creating-a-table-view.md), [목록 보기](./creating-a-list-view.md), [와이드 보기인](./creating-a-wide-view.md), 및 [사용자 지정 보기](./creating-custom-controls.md)합니다.

## <a name="example"></a>예제

에서는 다음 예제는 `View` 테이블 뷰를 정의 하는 요소는 [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) 개체입니다. 뷰의 이름을 "service"입니다.

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>

```

## <a name="see-also"></a>참고 항목

[목록 뷰 만들기](./creating-a-list-view.md)

[테이블 뷰 만들기](./creating-a-table-view.md)

[넓은 보기 만들기](./creating-a-wide-view.md)

[사용자 지정 컨트롤 만들기](./creating-custom-controls.md)

[뷰 요소 (형식)](./view-element-format.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
