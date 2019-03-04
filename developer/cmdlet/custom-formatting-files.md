---
title: 사용자 지정 형식 지정 파일 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 85d27545-8097-4010-9947-6d8b3ce2eac0
caps.latest.revision: 15
ms.openlocfilehash: 71c1c181058c5646c817b90d9832976a78c6c7de
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860609"
---
# <a name="custom-formatting-files"></a>형식 지정 파일 사용자 지정

Cmdlet, 함수 및 스크립트에서 반환한 개체에 대 한 표시 형식은 형식 지정 파일 (format.ps1xml 파일)를 사용 하 여 정의 됩니다. 이러한 파일의 여러 Windows PowerShell cmdlet에서 반환 되는 해당 개체에 대 한 기본 표시 형식을 정의 하는 Windows PowerShell에서 제공 됩니다. 그러나 사용자 고유의 사용자 지정 형식 지정 파일의 기본 표시 형식을 덮어쓸지 아니면 고유한 명령에서 반환 된 개체의 표시를 정의 만들 수 있습니다.

Windows PowerShell 이러한 서식 파일의 데이터를 사용 하 여 표시 되는 내용 및 데이터를 포맷 하는 방법 확인. 표시 된 데이터 개체의 속성 또는 스크립트 블록의 값을 포함할 수 있습니다.  스크립트 블록은 개체의 속성에서 직접 사용할 수 없는 일부 값을 표시 하려는 경우 사용 됩니다. 예를 들어, 다음 개체의 두 속성의 값을 추가 하 고 데이터의 개별 조각으로 합계를 표시 하는 것이 좋습니다. 사용자 지정 서식 파일을 작성할 때 정의 해야 합니다 *뷰* 표시 하려는 개체에 대 한 합니다. 각 개체에 대 한 단일 뷰를 정의할 수 있습니다, 여러 개체에 대 한 단일 뷰를 정의할 수 있습니다 또는 동일한 개체에 대 한 여러 뷰를 정의할 수 있습니다. 뷰에서 정의할 수 있는 수에 제한은 없습니다.

> [!IMPORTANT]
> 서식 파일에서 파이프라인에 반환 되는 개체의 요소를 결정 하지 않습니다. 개체를 파이프라인에 반환 되 면 해당 개체의 모든 멤버가 사용할 수 있습니다.

## <a name="format-views"></a>형식 뷰

형식 뷰는 테이블 형식으로를 목록 형식으로, 넓은 형식으로 사용자 지정 형식에 개체를 표시할 수 있습니다. 대부분의 경우 각 형식 정의 집합 뷰를 설명 하는 XML 태그에 의해 설명 되어 있습니다. 각 뷰는 뷰의 이름을 뷰 및 뷰를 표 보기에 대 한 열 및 행 정보 등의 요소를 사용 하는 개체를 포함 합니다.

다음 뷰를 사용할 수 있습니다.

테이블 뷰 개체 또는 하나 이상의 열에 있는 스크립트 블록 값의 속성을 나열합니다. 각 열에는 스크립트 블록 값 또는 개체의 속성을 나타냅니다. 개체를 개체의 속성 및 값을 차단 하는 스크립트의 조합 속성의 하위 집합의 모든 속성을 표시 하는 테이블 보기를 정의할 수 있습니다. 테이블의 각 행에는 반환 된 개체를 나타냅니다. 이 보기에 대 한 자세한 내용은 참조 하세요. [테이블 뷰](../format/creating-a-table-view.md)합니다.

목록 뷰 개체 또는 단일 열에는 스크립트 블록 값의 속성을 나열합니다. 목록의 각 행에는 선택적 레이블을 또는 속성 또는 스크립트 블록의 값을 뒤에 속성 이름을 표시 합니다. 이 보기에 대 한 자세한 내용은 참조 하세요. [목록 뷰에](../format/creating-a-list-view.md)합니다.

넓은 보기 개체 또는 하나 이상의 열에 있는 스크립트 블록 값의 단일 속성을 나열합니다. 레이블 또는이 보기에 대 한 헤더 필요 하지 않습니다. 이 보기에 대 한 자세한 내용은 참조 하세요. [와이드 보기인 경우](../format/creating-a-wide-view.md)합니다.

사용자 지정 보기 표 보기, 목록 뷰 또는 와이드 뷰가의 고정 된 구조로를 따르지 않는 개체 속성 값을 차단 하는 스크립트의 사용자 지정 가능한 뷰를 표시 합니다. 독립 실행형 사용자 지정 보기를 정의 하거나 테이블 뷰 또는 목록 보기와 같은 다른 보기에서 사용 되는 사용자 지정 보기를 정의할 수 있습니다. 이 보기에 대 한 자세한 내용은 참조 하세요. [사용자 지정 보기](../format/creating-custom-controls.md)합니다.

## <a name="view-xml-elements"></a>보기 XML 요소

다음 예제에서는 두 개의 열이 포함 된 테이블 뷰를 정의 하는 데 XML 태그를 보여 줍니다. 합니다 [ViewDefinitions](../format/viewdefinitions-element-format.md) 요소는 서식 파일에 정의 된 모든 보기에 대 한 컨테이너 요소입니다. 합니다 [보기](../format/view-element-format.md) 요소는 특정 테이블, 목록, 넓게 또는 사용자 지정 보기를 정의 합니다. 각 보기 내에서 [이름](../format/name-element-for-view-format.md) 요소 뷰의 이름을 지정 합니다 [ViewSelectedBy](../format/viewselectedby-element-format.md) 뷰 및 다른 컨트롤 요소를 사용 하는 개체를 정의 하는 요소 (같은 `TableControl` 요소) 보기의 형식을 정의 합니다.

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

[테이블 뷰](../format/creating-a-table-view.md)

[목록 보기](../format/creating-a-list-view.md)

[넓은 보기](../format/creating-a-wide-view.md)

[사용자 지정 보기](../format/creating-custom-controls.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)
