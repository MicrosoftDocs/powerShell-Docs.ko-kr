---
title: TypeName 요소 ViewSelectedBy (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0ad807a9-d7d8-4e96-b799-9c6a7677cc2d
caps.latest.revision: 12
ms.openlocfilehash: e2028c479103cc414295dc24a0f9bb69190bfc66
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857899"
---
# <a name="typename-element-for-viewselectedby-format"></a>ViewSelectedBy에 대한 TypeName 요소(형식)

보기에 표시 되는.NET 개체를 지정 합니다.

구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) ViewSelectedBy 요소 (형식) TypeName 요소 ViewSelectedBy (형식)에 대 한

## <a name="syntax"></a>구문

```xml
<TypeName>FullyQualifiedTypeName</TypeName>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 부모 요소는 `TypeName` 요소입니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[ViewSelectedBy 요소 (형식)](./viewselectedby-element-format.md)|보기에 표시 되는.NET 개체를 정의 합니다.|

## <a name="text-value"></a>텍스트 값

와 같이.NET 형식의 정규화 된 이름을 지정 `System.IO.DirectoryInfo`합니다.

## <a name="remarks"></a>설명

다른 보기에이 요소를 사용 하는 방법에 대 한 자세한 내용은 참조 하세요. [테이블 뷰를 만드는](./creating-a-table-view.md), [목록 뷰를 만들면](./creating-a-list-view.md)를 [넓은 보기를 만드는](./creating-a-wide-view.md), 및 [ 사용자 지정 뷰 구성 요소](./creating-custom-controls.md)합니다.

## <a name="example"></a>예제

다음 예제에서는 지정 하는 방법을 보여 줍니다 합니다 [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) 목록 보기에 대 한 개체입니다. 동일한 스키마는 테이블, 넓게 및 사용자 지정 보기에 사용 됩니다.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a>참고 항목

[목록 뷰 만들기](./creating-a-list-view.md)

[테이블 뷰 만들기](./creating-a-table-view.md)

[넓은 보기 만들기](./creating-a-wide-view.md)

[사용자 지정 컨트롤 만들기](./creating-custom-controls.md)

[ViewSelectedBy 요소 (형식)](./viewselectedby-element-format.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
