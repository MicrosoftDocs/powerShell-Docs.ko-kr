---
title: ViewSelectedBy (형식)에 대 한 TypeName 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e9a391565c3e66041dd9a340455dccfce9ce929b
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780035"
---
# <a name="typename-element-for-viewselectedby-format"></a>ViewSelectedBy에 대한 TypeName 요소(형식)

뷰에 표시 되는 .NET 개체를 지정 합니다.

Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) ViewSelectedBy 요소 (형식)에 대 한 viewselectedby (형식)

## <a name="syntax"></a>구문

```xml
<TypeName>FullyQualifiedTypeName</TypeName>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `TypeName` .

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[ViewSelectedBy 요소(형식)](./viewselectedby-element-format.md)|뷰에 표시 되는 .NET 개체를 정의 합니다.|

## <a name="text-value"></a>텍스트 값

.NET 형식의 정규화 된 이름 (예:)을 지정 합니다 `System.IO.DirectoryInfo` .

## <a name="remarks"></a>설명

여러 보기에서이 요소를 사용 하는 방법에 대 한 자세한 내용은 [테이블 뷰 만들기](./creating-a-table-view.md), [목록 뷰 만들기](./creating-a-list-view.md), [넓은 뷰 만들기](./creating-a-wide-view.md)및 [사용자 지정 뷰 구성 요소](./creating-custom-controls.md)를 참조 하세요.

## <a name="example"></a>예제

다음 예제에서는 목록 뷰에 대 한 [Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) 개체를 지정 하는 방법을 보여 줍니다. 테이블, 전체 및 사용자 지정 보기에도 동일한 스키마가 사용 됩니다.

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

[목록 보기 만들기](./creating-a-list-view.md)

[테이블 보기 만들기](./creating-a-table-view.md)

[넓게 보기 만들기](./creating-a-wide-view.md)

[사용자 지정 컨트롤 만들기](./creating-custom-controls.md)

[ViewSelectedBy 요소(형식)](./viewselectedby-element-format.md)

[PowerShell 형식 지정 파일 작성](./writing-a-powershell-formatting-file.md)
