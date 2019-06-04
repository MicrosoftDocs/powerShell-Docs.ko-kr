---
title: 형식 지정 파일 개요 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fe888fee-1fe9-459f-9d62-35732c19a7f8
caps.latest.revision: 13
ms.openlocfilehash: d418cff70c1197aa3c331eed909f49198da139e9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065736"
---
# <a name="formatting-file-overview"></a>형식 지정 파일 개요

명령 (cmdlet, 함수 및 스크립트)에서 반환 되는 개체에 대 한 표시 형식은 형식 지정 파일 (format.ps1xml 파일)를 사용 하 여 정의 됩니다. 와 같은 PowerShell 제공한 명령에 의해 반환 된 해당 개체에 대 한 표시 형식을 정의 하는 PowerShell에서 제공 하는 다양 한 이러한 파일을 [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) 에서 반환 된 개체는 `Get-Process` cmdlet. 그러나 기본 표시 형식을 덮어쓰려면 사용자 고유의 사용자 지정 형식 지정 파일을 만들 수도 있습니다 또는 고유한 명령에서 반환 된 개체의 표시를 정의 하는 사용자 지정 형식 지정 파일을 작성할 수 있습니다.

> [!IMPORTANT]
> 서식 파일에서 파이프라인에 반환 되는 개체의 요소를 결정 하지 않습니다. 파이프라인에 반환 되는 개체 표시 되지 않는 일부 경우에 해당 개체의 모든 멤버가 사용할 수 있습니다.

표시 되는 항목 및 표시 된 데이터의 서식 지정 하는 방법을 확인 하려면 이러한 서식 파일의 데이터를 사용 하는 PowerShell. 표시 된 데이터 개체의 속성 또는 스크립트의 값을 포함할 수 있습니다. 스크립트 개체의 두 속성의 값을 추가 하 고 다음 데이터 부분으로 합계를 표시 하는 등의 개체의 속성에서 직접 사용할 수 없는 일부 값을 표시 하려는 경우에 사용 됩니다. 표시 된 데이터의 서식을 표시 하려는 개체에 대 한 뷰를 정의 하 여 수행 됩니다. 각 개체에 대 한 단일 뷰를 정의할 수 있습니다, 여러 개체에 대 한 단일 뷰를 정의할 수 있습니다 또는 동일한 개체에 대 한 여러 뷰를 정의할 수 있습니다. 뷰에서 정의할 수 있는 수에 제한은 없습니다.

## <a name="common-features-of-formatting-files"></a>서식 파일의 일반적인 기능

각 형식 지정 파일 파일에서 정의 된 모든 뷰 간에 공유할 수 있는 다음 구성 요소를 정의할 수 있습니다.

- 기본 여부 테이블의 행에 표시 되는 데이터에 표시한 다음 줄 데이터 열의 너비 보다 길 경우와 같은 구성 설정입니다. 이러한 설정에 대 한 자세한 내용은 참조 하세요. [일반 구성 설정을 정의](./defining-common-configuration-features.md)합니다.

- 서식 파일의 뷰 중 하나에서 표시 될 수 있는 개체의 집합입니다. 이러한 설정에 대 한 자세한 (이라고 *선택 집합*)를 참조 하세요 [설정의 개체 정의](./defining-selection-sets.md)합니다.

- 서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤입니다. 컨트롤에 데이터 표시 방법을 보다 세부적으로 제어를 제공 합니다. 컨트롤에 대 한 자세한 내용은 참조 하세요. [사용자 지정 컨트롤 정의](./creating-custom-controls.md)합니다.

## <a name="formatting-views"></a>뷰를 서식 지정

형식 뷰는 테이블 형식, 목록 형식으로, 넓은 형식 및 사용자 지정 형식에서 개체를 표시할 수 있습니다. 대부분의 경우 각 형식 정의 집합 뷰를 설명 하는 XML 태그에 의해 설명 되어 있습니다. 각 뷰는 뷰의 이름을 뷰 및 뷰를 표 보기에 대 한 열 및 행 정보 등의 요소를 사용 하는 개체를 포함 합니다.

테이블 보기 개체 또는 하나 이상의 열에 있는 스크립트 블록 값의 속성을 나열 합니다. 각 열에는 개체 또는 스크립트 값의 단일 속성을 나타냅니다. 개체의 속성 및 스크립트 값의 조합일 개체의 속성 하위 집합의 모든 속성을 표시 하는 테이블 보기를 정의할 수 있습니다. 테이블의 각 행에는 반환 된 개체를 나타냅니다. 테이블 보기를 만드는 방법과 비슷합니다 개체를 파이프 하는 경우에 `Format-Table` cmdlet. 이 보기에 대 한 자세한 내용은 참조 하세요. [테이블 뷰](./creating-a-table-view.md)합니다.

목록 보기의 속성을 나열할 개체 또는 단일 열에 스크립트 값입니다. 선택적 레이블을 또는 속성 또는 스크립트의 값이 오는 속성 이름 목록의 각 행에 표시 됩니다. 목록 보기를 만드는 방법과 비슷합니다 개체를 파이프 하 여 `Format-List` cmdlet. 이 보기에 대 한 자세한 내용은 참조 하세요. [목록 뷰에](./creating-a-list-view.md)합니다.

넓은 보기 개체 또는 하나 이상의 열에 스크립트 값의 단일 속성을 나열합니다. 레이블 또는이 보기에 대 한 헤더 필요 하지 않습니다. 넓은 보기를 만드는 과정은 매우 개체를 파이프 비슷합니다는 `Format-Wide` cmdlet. 이 보기에 대 한 자세한 내용은 참조 하세요. [와이드 보기인 경우](./creating-a-wide-view.md)합니다.

사용자 지정 보기 개체 속성 또는 스크립트 값의 테이블 뷰, 목록 뷰 또는 와이드 뷰가의 고정 된 구조로를 따르지 않으면 하는 사용자 지정 가능한 보기를 표시 합니다. 독립 실행형 사용자 지정 보기를 정의 하거나 테이블 뷰 또는 목록 보기와 같은 다른 보기에서 사용 되는 사용자 지정 보기를 정의할 수 있습니다. 사용자 지정 보기를 만드는 방법과 비슷합니다 개체를 파이프 하 여 `Format-Custom` cmdlet. 이 보기에 대 한 자세한 내용은 참조 하세요. [사용자 지정 보기](./creating-custom-controls.md)합니다.

## <a name="components-of-a-view"></a>뷰 구성 요소

다음 XML 예제에서는 뷰의 기본 XML 구성 요소를 보여 줍니다. 개별 XML 요소를 만들려고 할 수는 보기에 따라 다르지만 뷰의 기본 구성 요소는 모두 동일 합니다.

시작 하려면 각 보기에는 `Name` 뷰를 참조 하는 데 사용 되는 알기 쉬운 이름을 지정 하는 요소입니다. `ViewSelectedBy` 뷰에.NET 개체를 표시를 정의 하는 요소 및 *제어* 뷰를 정의 하는 요소입니다.

```xml
<ViewDefinitions>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <TableControl>...</TableControl>
  </View>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <ListControl>...</ListControl>
  <View>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <WideControl>...</WideControl>
  <View>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <CustomControl>...</CustomControl>
  </View>
</ViewDefinitions>

```

Control 요소 내에서 하나 이상 정의할 수 있습니다 *항목이* 요소입니다. 여러 정의 사용 하는 경우 각 정의 사용 하 여.NET 개체를 지정 해야 합니다. 일반적으로 각 컨트롤에 대 한 하나의 정의 사용 하 여 항목이 하나만 필요 합니다.

```xml
<ListControl>
  <ListEntries>
    <ListEntry>
      <EntrySelectedBy>...</EntrySelectedBy>
      <ListItems>...</ListItems>
    <ListEntry>
    <ListEntry>
        <EntrySelectedBy>...</EntrySelectedBy>
      <ListItems>...</ListItems>
    <ListEntry>
    <ListEntry>
        <EntrySelectedBy>...</EntrySelectedBy>
      <ListItems>...</ListItems>
    <ListEntry>
  </ListEntries>
</ListControl>

```

뷰의 각 항목 요소 내에서 지정 된 *항목* .NET 속성 또는 보기에 표시 되는 스크립트를 정의 하는 요소.

```xml

<ListItems>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
</ListItems>

```

앞의 예제와 같이 서식 파일에는 여러 뷰가 포함 될 수 있습니다, 뷰 정의가 여러 개 포함할 수 있습니다 및 각 정의 여러 항목을 포함할 수 있습니다.

## <a name="example-of-a-table-view"></a>테이블 보기의 예

다음 예제에서는 두 개의 열이 포함 된 테이블 뷰를 정의 하는 데 XML 태그를 보여 줍니다. 합니다 [ViewDefinitions](./viewdefinitions-element-format.md) 요소는 서식 파일에 정의 된 모든 보기에 대 한 컨테이너 요소입니다. 합니다 [보기](./view-element-format.md) 요소는 특정 테이블, 목록, 넓게 또는 사용자 지정 보기를 정의 합니다. 각 [뷰](./view-element-format.md) 요소를 [이름](./name-element-for-view-format.md) 요소 뷰의 이름을 지정 합니다 [ViewSelectedBy](./viewselectedby-element-format.md) 뷰 및 다양 한를 사용 하는 개체를 정의 하는 요소 컨트롤 요소 (같은 `TableControl` 다음 예제에 표시 된 요소) 보기의 유형을 정의 합니다.

```xml
<ViewDefinitions>
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

[목록 뷰 만들기](./creating-a-list-view.md)

[테이블 뷰 만들기](./creating-a-table-view.md)

[넓은 보기 만들기](./creating-a-wide-view.md)

[사용자 지정 컨트롤 만들기](./creating-custom-controls.md)

[PowerShell 서식 및 형식 파일 작성](./writing-a-powershell-formatting-file.md)
