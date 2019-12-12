---
title: 사용자 지정 서식 파일 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 85d27545-8097-4010-9947-6d8b3ce2eac0
caps.latest.revision: 15
ms.openlocfilehash: 71c1c181058c5646c817b90d9832976a78c6c7de
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369832"
---
# <a name="custom-formatting-files"></a>형식 지정 파일 사용자 지정

Cmdlet, 함수 및 스크립트에서 반환 되는 개체의 표시 형식은 형식 지정 파일 (types.ps1xml 파일)을 사용 하 여 정의 됩니다. 이러한 파일 중 일부는 windows powershell cmdlet에서 반환 되는 개체에 대 한 기본 표시 형식을 정의 하기 위해 Windows PowerShell에서 제공 됩니다. 그러나 사용자 고유의 사용자 지정 서식 파일을 만들어 기본 표시 형식을 덮어쓰거나 사용자의 명령으로 반환 되는 개체의 표시를 정의할 수도 있습니다.

Windows PowerShell은 이러한 서식 지정 파일의 데이터를 사용 하 여 표시 되는 내용과 데이터의 형식 지정 방법을 결정 합니다. 표시 되는 데이터에는 개체의 속성 또는 스크립트 블록의 값이 포함 될 수 있습니다.  스크립트 블록은 개체의 속성에서 직접 사용할 수 없는 일부 값을 표시 하려는 경우에 사용 됩니다. 예를 들어 개체의 두 속성 값을 추가 하 고 합계를 별도의 데이터로 표시할 수 있습니다. 사용자 고유의 서식 지정 파일을 작성 하는 경우 표시할 개체에 대 한 *보기* 를 정의 해야 합니다. 각 개체에 대해 단일 뷰를 정의 하거나, 여러 개체에 대해 단일 뷰를 정의 하거나, 동일한 개체에 대해 여러 뷰를 정의할 수 있습니다. 정의할 수 있는 뷰 수에는 제한이 없습니다.

> [!IMPORTANT]
> 파일 서식 지정은 파이프라인에 반환 되는 개체의 요소를 결정 하지 않습니다. 개체가 파이프라인으로 반환 되 면 해당 개체의 모든 멤버를 사용할 수 있습니다.

## <a name="format-views"></a>뷰 서식

서식 보기에서는 개체를 테이블 형식으로 표시 하 고, 목록 형식, 너비를 지정 하 고, 사용자 지정 형식을 지정할 수 있습니다. 대부분의 경우 각 서식 정의는 뷰를 설명 하는 XML 태그 집합으로 설명 됩니다. 각 뷰에는 뷰 이름, 뷰를 사용 하는 개체 및 뷰의 요소 (예: 테이블 뷰의 열 및 행 정보)가 포함 됩니다.

다음 뷰를 사용할 수 있습니다.

테이블 뷰 하나 이상의 열에 있는 개체 또는 스크립트 블록 값의 속성을 나열 합니다. 각 열은 개체의 속성 또는 스크립트 블록 값을 나타냅니다. 개체의 모든 속성, 개체 속성의 하위 집합 또는 속성 및 스크립트 블록 값의 조합을 표시 하는 테이블 뷰를 정의할 수 있습니다. 테이블의 각 행은 반환 된 개체를 나타냅니다. 이 보기에 대 한 자세한 내용은 [테이블 뷰](../format/creating-a-table-view.md)를 참조 하세요.

목록 뷰 단일 열에 개체 또는 스크립트 블록 값의 속성을 나열 합니다. 목록의 각 행에는 선택적 레이블 또는 속성 이름과 속성 또는 스크립트 블록 값이 표시 됩니다. 이 보기에 대 한 자세한 내용은 [목록 뷰](../format/creating-a-list-view.md)를 참조 하세요.

넓은 뷰 하나 이상의 열에 있는 단일 개체 속성 또는 스크립트 블록 값을 나열 합니다. 이 보기에 대 한 레이블이나 머리글이 없습니다. 이 보기에 대 한 자세한 내용은 [Wide view](../format/creating-a-wide-view.md)를 참조 하세요.

사용자 지정 뷰는 테이블 뷰, 목록 뷰 또는 넓은 보기의 고정 구조를 따르지 않는 개체 속성 또는 스크립트 블록 값의 사용자 지정 가능한 뷰를 표시 합니다. 독립 실행형 사용자 지정 보기를 정의 하거나, 다른 보기에서 사용 되는 사용자 지정 보기 (예: 테이블 뷰 또는 목록 보기)를 정의할 수 있습니다. 이 보기에 대 한 자세한 내용은 [사용자 지정 뷰](../format/creating-custom-controls.md)를 참조 하세요.

## <a name="view-xml-elements"></a>XML 요소 보기

다음 예에서는 두 개의 열이 포함 된 테이블 뷰를 정의 하는 데 사용 되는 XML 태그를 보여 줍니다. [Viewdefinitions](../format/viewdefinitions-element-format.md) 요소는 서식 파일에 정의 된 모든 뷰에 대 한 컨테이너 요소입니다. [View](../format/view-element-format.md) 요소는 특정 테이블, 목록, 전체 또는 사용자 지정 뷰를 정의 합니다. 각 뷰 내에서 [name](../format/name-element-for-view-format.md) 요소는 뷰의 이름을 지정 하 고 [viewselectedby](../format/viewselectedby-element-format.md) 요소는 뷰를 사용 하는 개체를 정의 하며 `TableControl` 요소와 같은 다른 컨트롤 요소는 뷰의 형식을 정의 합니다.

```xml
ViewDefinitions
  <View>
    <Name>Name of View</Name>
    <ViewSelectedBy>
      <TypeName>Object to display using this view</TypeName>
      <TypeName>Object to display using this view</TypeName>
    </ViewSelectedBy>
    <TableControl>
      <TableHeaders>
        <TableColumnHeader>
          <Width></Width>
        </TableColumnHeader>
        <TableColumnHeader>
          <Width></Width>
        </TableColumnHeader>
      </TableHeaders>
      <TableRowEntries>
        <TableRowEntry>
          <TableColumnItems>
            <TableColumnItem>
              <PropertyName>Header for column 1</PropertyName>
            </TableColumnItem>
            <TableColumnItem>
              <PropertyName>Header for column 2</PropertyName>
            </TableColumnItem>
          </TableColumnItems>
        </TableRowEntry>
      </TableRowEntries>
    </TableControl)
  </View>
</ViewDefinitions>

```

## <a name="see-also"></a>참고 항목

[테이블 보기](../format/creating-a-table-view.md)

[목록 보기](../format/creating-a-list-view.md)

[넓은 보기](../format/creating-a-wide-view.md)

[사용자 지정 보기](../format/creating-custom-controls.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)
