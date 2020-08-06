---
title: 파일 서식 지정 개요 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: efdd3eed15c5f3c88636fcbe7a39f6c6cfb20ced
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87773507"
---
# <a name="formatting-file-overview"></a>형식 지정 파일 개요

명령 (cmdlet, 함수 및 스크립트)에서 반환 되는 개체에 대 한 표시 형식은 형식 지정 파일 (format.ps1xml 파일)을 사용 하 여 정의 됩니다. 이러한 파일 중 몇 가지는 PowerShell에서 반환 하는 개체에 대 한 표시 형식을 정의 하기 위해 PowerShell에서 제공 됩니다 .이는 cmdlet에서 반환 되는 [system.object](/dotnet/api/System.Diagnostics.Process) 개체와 같이 powershell에서 제공 하는 명령에 의해 반환 됩니다. `Get-Process` 그러나 사용자 고유의 사용자 지정 서식 파일을 만들어 기본 표시 형식을 덮어쓰거나 사용자 지정 서식 파일을 작성 하 여 사용자의 명령에서 반환 하는 개체의 표시를 정의할 수도 있습니다.

> [!IMPORTANT]
> 파일 서식 지정은 파이프라인에 반환 되는 개체의 요소를 결정 하지 않습니다. 개체를 파이프라인으로 반환 하면 일부 표시 되지 않은 경우에도 해당 개체의 모든 멤버를 사용할 수 있습니다.

PowerShell에서는 이러한 서식 파일의 데이터를 사용 하 여 표시 되는 내용과 표시 되는 데이터의 형식을 지정 하는 방법을 결정 합니다. 표시 되는 데이터에는 개체의 속성 또는 스크립트의 값이 포함 될 수 있습니다. 개체의 속성 값을 추가한 다음 합계를 데이터 조각으로 표시 하는 등 개체의 속성에서 직접 사용할 수 없는 일부 값을 표시 하려는 경우 스크립트를 사용 합니다. 표시 되는 데이터의 서식은 표시 하려는 개체에 대 한 뷰를 정의 하 여 수행 됩니다. 각 개체에 대해 단일 뷰를 정의 하거나, 여러 개체에 대해 단일 뷰를 정의 하거나, 동일한 개체에 대해 여러 뷰를 정의할 수 있습니다. 정의할 수 있는 뷰 수에는 제한이 없습니다.

## <a name="common-features-of-formatting-files"></a>서식 파일의 일반적인 기능

각 서식 파일은 파일에 정의 된 모든 보기에서 공유할 수 있는 다음 구성 요소를 정의할 수 있습니다.

- 데이터가 열의 너비 보다 길면 다음 줄에 테이블 행에 표시 되는 데이터를 표시할지 여부와 같은 기본 구성 설정입니다. 이러한 설정에 대 한 자세한 내용은 [공통 구성 설정 정의](./defining-common-configuration-features.md)를 참조 하세요.

- 서식 파일의 모든 보기에서 표시할 수 있는 개체 집합입니다. 이러한 집합 ( *선택 집합*이라고 함)에 대 한 자세한 내용은 [개체 집합 정의](./defining-selection-sets.md)를 참조 하세요.

- 서식 파일의 모든 뷰에서 사용할 수 있는 공용 컨트롤입니다. 컨트롤을 통해 데이터가 표시 되는 방법을 보다 세밀 하 게 제어할 수 있습니다. 컨트롤에 대 한 자세한 내용은 [사용자 지정 컨트롤 정의](./creating-custom-controls.md)를 참조 하세요.

## <a name="formatting-views"></a>보기 서식 지정

서식 보기에서는 개체를 테이블 형식, 목록 형식, 넓은 형식 및 사용자 지정 형식으로 표시할 수 있습니다. 대부분의 경우 각 서식 지정 정의는 뷰를 설명 하는 XML 태그 집합으로 설명 됩니다. 각 뷰에는 뷰 이름, 뷰를 사용 하는 개체 및 뷰의 요소 (예: 테이블 뷰의 열 및 행 정보)가 포함 됩니다.

테이블 뷰 하나 이상의 열에 있는 개체 또는 스크립트 블록 값의 속성을 나열 합니다. 각 열은 개체의 단일 속성 또는 스크립트 값을 나타냅니다. 개체의 모든 속성, 개체 속성의 하위 집합 또는 속성 및 스크립트 값의 조합을 표시 하는 테이블 뷰를 정의할 수 있습니다. 테이블의 각 행은 반환 된 개체를 나타냅니다. 테이블 뷰를 만드는 것은 개체를 cmdlet으로 파이프 하는 경우와 매우 비슷합니다 `Format-Table` . 이 보기에 대 한 자세한 내용은 [테이블 뷰](./creating-a-table-view.md)를 참조 하세요.

목록 뷰 단일 열에 있는 개체 또는 스크립트 값의 속성을 나열 합니다. 목록의 각 행에는 선택적 레이블 또는 속성 이름과 속성 또는 스크립트의 값이 표시 됩니다. 목록 뷰를 만드는 것은 개체를 cmdlet으로 파이프 하는 것과 매우 비슷합니다 `Format-List` . 이 보기에 대 한 자세한 내용은 [목록 뷰](./creating-a-list-view.md)를 참조 하세요.

넓은 뷰 하나 이상의 열에 있는 단일 개체 속성 또는 스크립트 값을 나열 합니다. 이 보기에 대 한 레이블이나 머리글이 없습니다. 넓은 뷰를 만드는 것은 개체를 cmdlet으로 파이프 하는 것과 매우 비슷합니다 `Format-Wide` . 이 보기에 대 한 자세한 내용은 [Wide view](./creating-a-wide-view.md)를 참조 하세요.

사용자 지정 보기에는 테이블 뷰, 목록 뷰 또는 넓은 보기의 고정 구조를 준수 하지 않는 개체 속성 또는 스크립트 값을 사용자 지정할 수 있는 뷰가 표시 됩니다. 독립 실행형 사용자 지정 뷰를 정의 하거나 다른 보기에서 사용 되는 사용자 지정 보기 (예: 테이블 뷰 또는 목록 보기)를 정의할 수 있습니다. 사용자 지정 뷰를 만드는 것은 개체를 cmdlet으로 파이프 하는 것과 매우 비슷합니다 `Format-Custom` . 이 보기에 대 한 자세한 내용은 [사용자 지정 뷰](./creating-custom-controls.md)를 참조 하세요.

## <a name="components-of-a-view"></a>뷰의 구성 요소

다음 XML 예제에서는 뷰의 기본 XML 구성 요소를 보여 줍니다. 개별 XML 요소는 만들려는 뷰에 따라 다르지만 뷰의 기본 구성 요소는 모두 동일 합니다.

먼저 각 뷰에는 `Name` 뷰를 참조 하는 데 사용 되는 사용자에 게 친숙 한 이름을 지정 하는 요소가 있습니다. `ViewSelectedBy`뷰가 표시 하는 .net 개체와 뷰를 정의 하는 *컨트롤* 요소를 정의 하는 요소입니다.

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

컨트롤 요소 내에서 하나 이상의 *항목* 요소를 정의할 수 있습니다. 여러 정의를 사용 하는 경우 각 정의를 사용 하는 .NET 개체를 지정 해야 합니다. 일반적으로 각 컨트롤에는 하나의 정의만 있는 항목이 하나만 필요 합니다.

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

뷰의 각 entry 요소 내에서 해당 보기에 표시 되는 .NET 속성 또는 스크립트를 정의 하는 *항목* 요소를 지정 합니다.

```xml

<ListItems>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
</ListItems>

```

앞의 예제에서 볼 수 있듯이 서식 파일에는 여러 뷰가 포함 될 수 있으며, 뷰에는 여러 개의 정의가 포함 될 수 있으며 각 정의에는 여러 항목이 포함 될 수 있습니다.

## <a name="example-of-a-table-view"></a>테이블 뷰의 예

다음 예에서는 두 개의 열이 포함 된 테이블 뷰를 정의 하는 데 사용 되는 XML 태그를 보여 줍니다. [Viewdefinitions](./viewdefinitions-element-format.md) 요소는 서식 파일에 정의 된 모든 뷰에 대 한 컨테이너 요소입니다. [View](./view-element-format.md) 요소는 특정 테이블, 목록, 전체 또는 사용자 지정 뷰를 정의 합니다. 각 [뷰](./view-element-format.md) 요소 내에서 [name](./name-element-for-view-format.md) 요소는 뷰의 이름을 지정 하 고 [viewselectedby](./viewselectedby-element-format.md) 요소는 뷰를 사용 하는 개체를 정의 하며 다음 예제에 표시 된 요소와 같은 다른 컨트롤 요소는 `TableControl` 뷰의 형식을 정의 합니다.

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

[목록 보기 만들기](./creating-a-list-view.md)

[테이블 보기 만들기](./creating-a-table-view.md)

[넓게 보기 만들기](./creating-a-wide-view.md)

[사용자 지정 컨트롤 만들기](./creating-custom-controls.md)

[PowerShell 서식 지정 및 형식 파일 작성](./writing-a-powershell-formatting-file.md)
