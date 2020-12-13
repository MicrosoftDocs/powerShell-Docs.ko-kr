---
ms.date: 09/13/2016
ms.topic: reference
title: 형식 스키마 XML 참조
description: 형식 스키마 XML 참조
ms.openlocfilehash: f59016df91fe458393655853b9eada0875a8dcb1
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667932"
---
# <a name="format-schema-xml-reference"></a>형식 스키마 XML 참조

이 단원의 항목에서는 서식 파일 (Format.ps1xml 파일)에 사용 되는 XML 요소에 대해 설명 합니다. 파일 서식 지정은 .NET 개체 표시 방법을 정의 합니다. 개체 자체는 변경 하지 않습니다.

## <a name="in-this-section"></a>섹션 내용

[TableControl에 대 한 TableColumnHeader의 Alignment 요소 (Format)](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) 열 머리글의 데이터를 표시 하는 방법을 정의 합니다.

[TableControl에 대 한 TableColumnItem의 Alignment 요소 (Format)](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) 행의 데이터가 표시 되는 방법을 정의 합니다.

[TableControl에 대 한 AutoSize 요소 (형식)](./autosize-element-for-tablecontrol-format.md) 데이터 크기에 따라 열 크기 및 열 수를 조정 하는지 여부를 지정 합니다.

[WideControl에 대 한 Autosize 요소 (형식)](./autosize-element-for-widecontrol-format.md) 데이터 크기에 따라 열 크기 및 열 수를 조정 하는지 여부를 지정 합니다.

[WideControl에 대 한 Columnnumber 요소 (형식)](./columnnumber-element-for-widecontrol-format.md) 넓은 보기에 표시 되는 열 수를 지정 합니다.

[Configuration 요소 (Format)](./configuration-element-format.md) 서식 파일의 최상위 요소를 나타냅니다.

[구성에 대 한 컨트롤 요소 (형식)](./control-element-for-controls-for-configuration-format.md) 서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤 및 컨트롤을 참조 하는 데 사용 되는 이름을 정의 합니다.

[보기에 대 한 컨트롤 요소 (형식)](./control-element-for-controls-for-view-format.md) 뷰에서 사용할 수 있는 컨트롤 및 컨트롤을 참조 하는 데 사용 되는 이름을 정의 합니다.

[구성 요소에 대 한 Controls 요소 (형식)](./controls-element-for-configuration-format.md) 서식 지정 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 정의 합니다.

[View 요소에 대 한 Controls 요소 (Format)](./controls-element-for-view-format.md) 특정 뷰에서 사용할 수 있는 뷰 컨트롤을 정의 합니다.

[구성 (형식)의 컨트롤에 대 한 CustomControl 요소](./customcontrol-element-for-control-for-controls-for-configuration-format.md) 컨트롤을 정의 합니다. 이 요소는 서식 파일의 모든 뷰에서 사용할 수 있는 공용 컨트롤을 정의 하는 데 사용 됩니다.

[View 컨트롤의 컨트롤에 대 한 CustomControl 요소 (형식)](./customcontrol-element-for-control-for-controls-for-view-format.md) 뷰에서 사용 되는 컨트롤을 정의 합니다.

[GroupBy (형식)에 대 한 CustomControl 요소](./customcontrol-element-for-groupby-format.md) 새 그룹을 표시 하는 사용자 지정 컨트롤을 정의 합니다.

[CustomControl 요소 (Format)](./customcontrol-element-for-groupby-format.md) 뷰의 사용자 지정 컨트롤 형식을 정의 합니다.

[구성에 대 한 컨트롤에 대 한 ExpressionBinding의 Customcontrolname 요소 (형식)](./customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format.md) 공용 컨트롤의 이름을 지정 합니다. 이 요소는 서식 파일의 모든 뷰에서 사용할 수 있는 공용 컨트롤을 정의 하는 데 사용 됩니다.

[뷰 (형식)에 대 한 ExpressionBindine 컨트롤에 대 한 Customcontrolname 요소](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md) 공용 컨트롤 또는 뷰 컨트롤의 이름을 지정 합니다. 이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의 하는 데 사용 됩니다.

[GroupBy (형식)의 Customcontrolname 요소](./customcontrolname-element-for-groupby-format.md) 새 그룹을 표시 하는 데 사용 되는 사용자 지정 컨트롤의 이름을 지정 합니다. 이 요소는 테이블, 목록, 전체 또는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.

[구성에 대 한 CustomControl의 Customentry 요소 (형식)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md) 공용 컨트롤의 정의를 제공 합니다. 이 요소는 서식 파일의 모든 뷰에서 사용할 수 있는 공용 컨트롤을 정의 하는 데 사용 됩니다.

[뷰의 컨트롤에 대 한 Customentry 요소 (형식)](./customentry-element-for-customentries-for-controls-for-view-format.md) 컨트롤의 정의를 제공 합니다. 이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의 하는 데 사용 됩니다.

[뷰의 Customentry 요소에 대 한 Customentry 요소 (형식)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md) 사용자 지정 컨트롤 뷰의 정의를 제공 합니다.

[GroupBy (형식)에 대 한 CustomControl의 Customentry 요소](./customentry-element-for-customcontrol-for-groupby-format.md) 컨트롤의 정의를 제공 합니다. 이 요소는 새 개체 그룹이 표시 되는 방법을 정의 하는 데 사용 됩니다.

[구성에 대 한 CustomControl의 Customentries 요소 (형식)](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md) 공용 컨트롤의 정의를 제공 합니다. 이 요소는 서식 파일의 모든 뷰에서 사용할 수 있는 공용 컨트롤을 정의 하는 데 사용 됩니다.

[View 컨트롤의 CustomControl에 대 한 Customentries 요소 (형식)](./customentries-element-for-customcontrol-for-controls-for-view-format.md) 컨트롤에 대 한 정의를 제공 합니다. 이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의 하는 데 사용 됩니다.

[GroupBy (형식)의 CustomControl에 대 한 Customentries 요소](./customentries-element-for-customcontrol-for-groupby-format.md) 컨트롤에 대 한 정의를 제공 합니다. 이 요소는 새 개체 그룹이 표시 되는 방법을 정의 하는 데 사용 됩니다.

CustomControl에 대 한 [Customentries 요소 (형식)](./customentries-element-for-customcontrol-for-view-format.md) 사용자 지정 컨트롤 뷰의 정의를 제공 합니다. 사용자 지정 컨트롤 뷰에서 하나 이상의 정의를 지정 해야 합니다.

[구성에 대 한 컨트롤 Customitem의 Customitem 요소](./customitem-element-for-customentry-for-controls-for-configuration-format.md) 컨트롤에 표시 되는 데이터와 표시 방법을 정의 합니다. 이 요소는 서식 파일의 모든 뷰에서 사용할 수 있는 공용 컨트롤을 정의 하는 데 사용 됩니다.

[뷰의 컨트롤에 대 한 Customitem 요소 (형식)](./customitem-element-for-customentry-for-controls-for-view-format.md) 컨트롤에 표시 되는 데이터와 표시 방법을 정의 합니다. 이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의 하는 데 사용 됩니다.

[View 항목에 대 한 Customitem 요소 (형식)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md) 사용자 지정 컨트롤 보기에 표시 되는 데이터와 표시 방법을 정의 합니다. 이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.

[GroupBy (형식)에 대 한 Customitem의 Customitem 요소](./customitem-element-for-customentry-for-groupby-format.md) 사용자 지정 컨트롤 보기에 표시 되는 데이터와 표시 방법을 정의 합니다. 이 요소는 새 개체 그룹이 표시 되는 방법을 정의 하는 데 사용 됩니다.

[Defaultsettings 요소 (Format)](./defaultsettings-element-format.md) 서식 파일의 모든 뷰에 적용 되는 일반 설정을 정의 합니다. 일반 설정에는 오류 표시, 테이블에 텍스트 줄 바꿈, 컬렉션이 확장 되는 방법 정의 등이 포함 됩니다.

[Displayerror 요소 (Format)](./displayerror-element-format.md) 데이터의 일부를 표시 하는 동안 오류가 발생 하는 경우 문자열 #ERR 표시 되도록 지정 합니다.

[구성에 대 한 컨트롤의 CustomEntry에 대 한 Entryselectedby 요소 (형식)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md) 공용 컨트롤의 정의를 사용 하는 .NET 형식 또는이 컨트롤을 사용 하기 위해 존재 해야 하는 조건을 정의 합니다. 이 요소는 서식 파일의 모든 뷰에서 사용할 수 있는 공용 컨트롤을 정의 하는 데 사용 됩니다.

[View 컨트롤의 CustomEntry에 대 한 Entryselectedby 요소 (형식)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md) 이 컨트롤 정의를 사용 하는 .NET 형식 또는이 정의를 사용 하기 위해 존재 해야 하는 조건을 정의 합니다. 이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의 하는 데 사용 됩니다.

[View의 CustomEntry에 대 한 Entryselectedby 요소 (형식)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md) 이 사용자 지정 항목을 사용 하는 .NET 형식 또는이 항목을 사용 하기 위해 존재 해야 하는 조건을 정의 합니다.

[EnumerableExpansion (형식)에 대 한 Entryselectedby 요소](./entryselectedby-element-for-enumerableexpansion-format.md) 이 정의를 사용 하는 .NET 형식 또는이 정의를 사용 하기 위해 존재 해야 하는 조건을 정의 합니다.

[GroupBy (형식)에 대 한 CustomEntry의 Entryselectedby 요소](./entryselectedby-element-for-customentry-for-groupby-format.md) 이 컨트롤 정의를 사용 하는 .NET 형식 또는이 정의를 사용 하기 위해 존재 해야 하는 조건을 정의 합니다. 이 요소는 새 개체 그룹이 표시 되는 방법을 정의 하는 데 사용 됩니다.

[이 listcontrol (형식)의 ListEntry에 대 한 Entryselectedby 요소](./entryselectedby-element-for-listentry-for-listcontrol-format.md) 이 목록 뷰 정의를 사용 하는 .NET 형식 또는이 정의를 사용 하기 위해 존재 해야 하는 조건을 정의 합니다. 대부분의 경우 목록 뷰에 대 한 정의는 하나만 필요 합니다. 그러나 같은 목록 뷰를 사용 하 여 다른 개체에 대해 서로 다른 데이터를 표시 하려는 경우 목록 뷰에 대 한 여러 정의를 제공할 수 있습니다.

[TableRowEntry (형식)에 대 한 Entryselectedby 요소](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) 속성 값이 행에 표시 되는 .NET 형식을 정의 합니다.

[WideEntry (형식)에 대 한 Entryselectedby 요소](./entryselectedby-element-for-wideentry-format.md) 이 정의를 사용 하기 위해 존재 해야 하는 조건 또는 넓은 뷰의이 정의를 사용 하는 .NET 형식을 정의 합니다.

[Enumerableexpansion 요소 (형식)](./enumerableexpansion-element-format.md) 특정 .NET 컬렉션 개체가 뷰에 표시 될 때 확장 되는 방법을 정의 합니다.

[Enumerableexpansions 요소 (형식)](./enumerableexpansions-element-format.md) .NET 컬렉션 개체가 뷰에 표시 될 때 확장 되는 방법을 정의 합니다.

[구성에 대 한 컨트롤의 ExpressionBinding에 대 한 Enumeratecollection 요소 (형식)](./enumeratecollection-element-for-expressionbinding-for-controls-for-configuration-format.md) 컨트롤에서 컬렉션의 요소를 표시 하도록 지정 합니다. 이 요소는 서식 파일의 모든 뷰에서 사용할 수 있는 공용 컨트롤을 정의 하는 데 사용 됩니다.

[View 컨트롤의 ExpressionBinding에 대 한 Enumeratecollection 요소 (형식)](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md) 컬렉션의 요소가 표시 되도록 지정 합니다. 이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의 하는 데 사용 됩니다.

[CustomControl For View (Format)의 식 바인딩에 대 한 Enumeratecollection 요소](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md) 컬렉션의 요소를 표시 하도록 지정 합니다. 이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.

[GroupBy (형식)에 대 한 ExpressionBinding의 Enumeratecollection 요소](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md) 컬렉션의 요소를 표시 하도록 지정 합니다. 이 요소는 새 개체 그룹이 표시 되는 방법을 정의 하는 데 사용 됩니다.

[Expand 요소 (Format)](./expand-element-format.md) 이 정의에 대해 컬렉션 개체를 확장 하는 방법을 지정 합니다.

[구성에 대 한 컨트롤 CustomItem의 Expressionbinding 요소 (형식)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md) 컨트롤에 표시 되는 데이터를 정의 합니다. 이 요소는 서식 파일의 모든 뷰에서 사용할 수 있는 공용 컨트롤을 정의 하는 데 사용 됩니다.

[뷰에 대 한 컨트롤 CustomItem의 Expressionbinding 요소 (형식)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md) 컨트롤에 표시 되는 데이터를 정의 합니다. 이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의 하는 데 사용 됩니다.

[CustomControl의 CustomItem에 대 한 Expressionbinding 요소 (형식)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md) 컨트롤에 표시 되는 데이터를 정의 합니다. 이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.

[GroupBy (형식)에 대 한 CustomItem의 Expressionbinding 요소](./expressionbinding-element-for-customitem-for-groupby-format.md) 컨트롤에 표시 되는 데이터를 정의 합니다. 이 요소는 새 개체 그룹이 표시 되는 방법을 정의 하는 데 사용 됩니다.

[구성에 대 한 컨트롤의 프레임에 대 한 Firstlinehanging 요소 (형식)](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) 첫 번째 데이터 줄이 왼쪽으로 이동 하는 문자 수를 지정 합니다. 이 요소는 서식 파일의 모든 뷰에서 사용할 수 있는 공용 컨트롤을 정의 하는 데 사용 됩니다.

[뷰 컨트롤 프레임의 Firstlinehanging 요소 (형식)](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) 첫 번째 데이터 줄이 왼쪽으로 이동 하는 문자 수를 지정 합니다. 이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의 하는 데 사용 됩니다.

[보기에 대 한 CustomControl Frame의 Firstlinehanging 요소 (형식)](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) 첫 번째 데이터 줄이 왼쪽으로 이동 하는 문자 수를 지정 합니다. 이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.

[GroupBy의 프레임에 대 한 Firstlinehanging 요소 (형식)](./firstlinehanging-element-for-frame-for-groupby-format.md) 첫 번째 데이터 줄이 왼쪽으로 이동 하는 문자 수를 지정 합니다. 이 요소는 새 개체 그룹이 표시 되는 방법을 정의 하는 데 사용 됩니다.

[구성에 대 한 컨트롤용 프레임에 대 한 FirstLineIndent 요소 (형식)](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) 첫 번째 데이터 줄이 오른쪽으로 이동 하는 문자 수를 지정 합니다. 이 요소는 서식 파일의 모든 뷰에서 사용할 수 있는 공용 컨트롤을 정의 하는 데 사용 됩니다.

[뷰 컨트롤의 프레임 요소 FirstLineIndent 요소 (형식)](./firstlineindent-element-for-frame-for-controls-for-view-format.md) 첫 번째 데이터 줄이 오른쪽으로 이동 하는 문자 수를 지정 합니다. 이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의 하는 데 사용 됩니다.

[FirstLineIndent 요소](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) 첫 번째 데이터 줄이 오른쪽으로 이동 하는 문자 수를 지정 합니다. 이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.

[GroupBy의 프레임에 대 한 FirstLineIndent 요소 (형식)](./firstlineindent-element-for-frame-for-groupby-format.md) 첫 번째 데이터 줄이 오른쪽으로 이동 하는 문자 수를 지정 합니다. 이 요소는 새 개체 그룹이 표시 되는 방법을 정의 하는 데 사용 됩니다.

[ListItem의 FormatString 요소 (형식)](./formatstring-element-for-listitem-for-listcontrol-format.md) 속성 또는 스크립트 값이 표시 되는 방법을 정의 하는 형식 패턴을 지정 합니다.

[TableColumnItem에 대 한 FormatString 요소 (형식)](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md) 테이블의 속성 또는 스크립트 값이 표시 되는 방법을 정의 하는 형식 패턴을 지정 합니다.

[WideControl의 WideItem에 대 한 FormatString 요소 (형식)](./formatstring-element-for-wideitem-for-widecontrol-format.md) 속성 또는 스크립트 값이 뷰에 표시 되는 방법을 정의 하는 형식 패턴을 지정 합니다.

[구성에 대 한 컨트롤의 CustomItem에 대 한 Frame 요소 (형식)](./frame-element-for-customitem-for-controls-for-configuration-format.md) 데이터를 왼쪽 또는 오른쪽으로 이동 하는 것과 같이 데이터를 표시 하는 방법을 정의 합니다. 이 요소는 서식 파일의 모든 뷰에서 사용할 수 있는 공용 컨트롤을 정의 하는 데 사용 됩니다.

[View 컨트롤의 CustomItem에 대 한 Frame 요소 (형식)](./frame-element-for-customitem-for-controls-for-view-format.md) 데이터를 왼쪽 또는 오른쪽으로 이동 하는 것과 같이 데이터를 표시 하는 방법을 정의 합니다. 이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의 하는 데 사용 됩니다.

[CustomControl의 CustomItem에 대 한 Frame 요소 (형식)](./frame-element-for-customitem-for-customcontrol-for-view-format.md) 데이터를 왼쪽 또는 오른쪽으로 이동 하는 것과 같이 데이터를 표시 하는 방법을 정의 합니다. 이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.

[GroupBy의 CustomItem에 대 한 Frame 요소 (형식)](./frame-element-for-customitem-for-groupby-format.md) 데이터를 왼쪽 또는 오른쪽으로 이동 하는 것과 같이 데이터를 표시 하는 방법을 정의 합니다. 이 요소는 새 개체 그룹이 표시 되는 방법을 정의 하는 데 사용 됩니다.

[보기에 대 한 GroupBy 요소 (형식)](./groupby-element-for-view-format.md) Windows PowerShell에서 새로운 개체 그룹을 표시 하는 방법을 정의 합니다.

[HideTableHeaders 요소 (Format)](./hidetableheaders-element-format.md) 테이블의 헤더가 표시 되지 않도록 지정 합니다.

[구성에 대 한 컨트롤에 대 한 ExpressionBinding의 Itemselectioncondition 요소 (형식)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md) 이 컨트롤을 사용 하기 위해 있어야 하는 조건을 정의 합니다. 이 요소는 서식 파일의 모든 뷰에서 사용할 수 있는 공용 컨트롤을 정의 하는 데 사용 됩니다.

[View 컨트롤에 대 한 ExpressionBinding의 Itemselectioncondition 요소 (형식)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md) 이 컨트롤을 사용 하기 위해 있어야 하는 조건을 정의 합니다. 이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의 하는 데 사용 됩니다.

[CustomControl For View (Format)의 식 바인딩에 대 한 Itemselectioncondition 요소](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md) 이 컨트롤을 사용 하기 위해 있어야 하는 조건을 정의 합니다. 컨트롤 항목에 대해 지정할 수 있는 선택 조건 수에는 제한이 없습니다. 이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.

[GroupBy (형식)에 대 한 ExpressionBinding의 Itemselectioncondition 요소](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md) 이 컨트롤을 사용 하기 위해 있어야 하는 조건을 정의 합니다. 컨트롤 항목에 대해 지정할 수 있는 선택 조건 수에는 제한이 없습니다. 이 요소는 새 개체 그룹이 표시 되는 방법을 정의 하는 데 사용 됩니다.

[ListItem (형식)에 대 한 Itemselectioncondition 요소](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md) 이 목록 항목을 사용 하기 위해 있어야 하는 조건을 정의 합니다.

[이 listcontrol (형식)의 ListItem에 대 한 Label 요소](./label-element-for-listitem-for-listcontrol-format.md) 행의 속성 또는 스크립트 값에 대 한 레이블을 지정 합니다.

[GroupBy (Format)의 Label 요소](./label-element-for-groupby-format.md) 새 그룹이 발견 될 때 표시 되는 레이블을 지정 합니다.

[TableColumnHeader에 대 한 Label 요소 (Format)](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) 열 맨 위에 표시 되는 레이블을 정의 합니다.

[구성에 대 한 컨트롤의 프레임에 대 한 왼쪽 들여쓰기 요소 (형식)](./leftindent-element-for-frame-for-controls-for-configuration-format.md) 왼쪽 여백에서 데이터를 이동할 문자 수를 지정 합니다. 이 요소는 서식 파일의 모든 뷰에서 사용할 수 있는 공용 컨트롤을 정의 하는 데 사용 됩니다.

[뷰 컨트롤 프레임의 왼쪽 들여쓰기 요소 (형식)](./leftindent-element-for-frame-for-controls-for-view-format.md) 왼쪽 여백에서 데이터를 이동할 문자 수를 지정 합니다. 이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의 하는 데 사용 됩니다.

[CustomControl For Frame의 왼쪽 들여쓰기 요소 (형식)](./leftindent-element-for-frame-for-customcontrol-for-view-format.md) 왼쪽 여백에서 데이터를 이동할 문자 수를 지정 합니다. 이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.

[GroupBy의 프레임에 대 한 왼쪽 들여쓰기 요소 (형식)](./leftindent-element-for-frame-for-groupby-format.md) 왼쪽 여백에서 데이터를 이동할 문자 수를 지정 합니다. 이 요소는 새 개체 그룹이 표시 되는 방법을 정의 하는 데 사용 됩니다.

[이 listcontrol 요소 (Format)](./listcontrol-element-format.md) 뷰의 목록 형식을 정의 합니다.

[ListEntry 요소 (Format)](./listentry-element-for-listcontrol-format.md) 목록 뷰의 정의를 제공 합니다.

[ListEntries 요소 (Format)](./listentries-element-for-listcontrol-format.md) 목록 뷰의 행이 표시 되는 방법을 정의 합니다.

[ListItem 요소 (Format)](./listitem-element-for-listitems-for-listcontrol-format.md) 목록 뷰의 행에 값이 표시 되는 속성 또는 스크립트를 정의 합니다.

[ListItems 요소 (Format)](./listitems-element-for-listentry-for-listcontrol-format.md) 목록 뷰에 표시 되는 속성 및 스크립트를 정의 합니다.

[구성 컨트롤에 대 한 컨트롤의 Name 요소 (형식)](./name-element-for-control-for-controls-for-configuration-format.md) 컨트롤의 이름을 지정 합니다. 이 요소는 서식 파일의 모든 뷰에서 사용할 수 있는 공용 컨트롤을 정의 하는 데 사용 됩니다.

[SelectionSet (Format)의 Name 요소](./name-element-for-selectionset-format.md) 선택 집합을 참조 하는 데 사용 되는 이름을 지정 합니다.

[View의 Name 요소 (Format)](./name-element-for-view-format.md) 뷰를 식별 하는 데 사용 되는 이름을 지정 합니다.

[구성에 대 한 컨트롤 CustomItem의 줄 바꿈 요소 (형식)](./newline-element-for-customitem-for-controls-for-configuration-format.md) 컨트롤의 표시에 빈 줄을 추가 합니다. 이 요소는 서식 파일의 모든 뷰에서 사용할 수 있는 공용 컨트롤을 정의 하는 데 사용 됩니다.

[뷰 컨트롤의 CustomItem에 대 한 줄 바꿈 요소 (형식)](./newline-element-for-customitem-for-controls-for-view-format.md) 컨트롤의 표시에 빈 줄을 추가 합니다. 이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의 하는 데 사용 됩니다.

[CustomControl의 CustomItem에 대 한 줄 바꿈 요소 (형식)](./newline-element-for-customitem-for-customcontrol-for-view-format.md) 컨트롤의 표시에 빈 줄을 추가 합니다. 이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.

[GroupBy (형식)에 대 한 CustomItem의 줄 바꿈 요소](./newline-element-for-customitem-for-groupby-format.md) 컨트롤의 표시에 빈 줄을 추가 합니다. 이 요소는 새 개체 그룹이 표시 되는 방법을 정의 하는 데 사용 됩니다.

[구성에 대 한 컨트롤의 ExpressionBinding에 대 한 PropertyName 요소 (형식)](./propertyname-element-for-expressionbinding-for-controls-for-configuration-format.md) 공용 컨트롤에서 값을 표시 하는 .NET 속성을 지정 합니다. 이 요소는 서식 파일의 모든 뷰에서 사용할 수 있는 공용 컨트롤을 정의 하는 데 사용 됩니다.

[View 컨트롤의 ExpressionBinding에 대 한 PropertyName 요소 (형식)](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md) 컨트롤에서 값을 표시 하는 .NET 속성을 지정 합니다. 이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의 하는 데 사용 됩니다.

CustomControl에 대 한 [ExpressionBinding의 PropertyName 요소 (형식)](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md) 컨트롤에서 값을 표시 하는 .NET 속성을 지정 합니다. 이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.

[GroupBy (형식)에 대 한 ExpressionBinding의 PropertyName 요소](./propertyname-element-for-expressionbinding-for-groupby-format.md) 컨트롤에서 값을 표시 하는 .NET 속성을 지정 합니다. 이 요소는 새 개체 그룹이 표시 되는 방법을 정의 하는 데 사용 됩니다.

[GroupBy (형식)에 대 한 PropertyName 요소](./propertyname-element-for-groupby-format.md) 값이 변경 될 때마다 새 그룹을 시작 하는 .NET 속성을 지정 합니다.

구성에 대 한 ItemSeclectionCondition에 대 한 [PropertyName 요소 (형식)](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) 조건을 트리거하는 .NET 속성을 지정 합니다. 이 속성이 존재 하거나로 확인 되 면 `true` 조건이 충족 되 고 컨트롤이 사용 됩니다. 이 요소는 서식 파일의 모든 뷰에서 사용할 수 있는 공용 컨트롤을 정의 하는 데 사용 됩니다.

[View 컨트롤에 대 한 ItemSelectionCondition의 PropertyName 요소 (형식)](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md) 조건을 트리거하는 .NET 속성을 지정 합니다. 이 속성이 존재 하거나로 확인 되 면 `true` 조건이 충족 되 고 컨트롤이 사용 됩니다. 이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의 하는 데 사용 됩니다.

CustomControl에 대 한 [ItemSelectionCondition의 PropertyName 요소 (Format)](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) 는 조건을 트리거하는 .net 속성을 지정 합니다. 이 속성이 존재 하거나로 확인 되 면 `true` 조건이 충족 되 고 컨트롤이 사용 됩니다. 이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.

[GroupBy (형식)에 대 한 ItemSelectionCondition의 PropertyName 요소](./propertyname-element-for-itemselectioncondition-for-groupby-format.md) 조건을 트리거하는 .NET 속성을 지정 합니다. 이 속성이 존재 하거나로 확인 되 면 `true` 조건이 충족 되 고 컨트롤이 사용 됩니다. 이 요소는 새 개체 그룹이 표시 되는 방법을 정의 하는 데 사용 됩니다.

[ListItem (형식)에 대 한 ItemSelectionCondition의 PropertyName 요소](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md) 조건을 트리거하는 .NET 속성을 지정 합니다. 이 속성이 존재 하거나로 확인 되 면 `true` 조건이 충족 되 고 뷰가 사용 됩니다. 이 요소는 목록 뷰를 정의할 때 사용 됩니다.

[이 listcontrol의 ListItem 요소에 대 한 PropertyName 요소 (형식)](./propertyname-element-for-listitem-for-listcontrol-format.md) 값이 목록에 표시 되는 .NET 속성을 지정 합니다.

[ListEntry (형식)의 경우 EntrySelectedBy에 대 한 SelectionCondition의 PropertyName 요소](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md) 조건을 트리거하는 .NET 속성을 지정 합니다. 이 속성이 존재 하거나로 확인 되 면 `true` 조건이 충족 되 고 항목이 사용 됩니다. 이 요소는 서식 파일의 모든 뷰에서 사용할 수 있는 공용 컨트롤을 정의 하는 데 사용 됩니다.

[View 컨트롤의 SelectionCondition에 대 한 PropertyName 요소 (형식)](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md) 조건을 트리거하는 .NET 속성을 지정 합니다. 이 속성이 존재 하거나로 확인 되 면 `true` 조건이 충족 되 고 항목이 사용 됩니다. 이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의 하는 데 사용 됩니다.

CustomControl에 대 한 [SelectionCondition의 PropertyName 요소 (형식)](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md) 조건을 트리거하는 .NET 속성을 지정 합니다. 이 속성이 존재 하거나로 평가 될 때 `true` 조건이 충족 되 고 정의가 사용 됩니다. 이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.

[EnumerableExpansion (형식)의 경우 EntrySelectedBy의 SelectionCondition에 대 한 PropertyName 요소](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md) 조건을 트리거하는 .NET 속성을 지정 합니다. 이 속성이 존재 하거나로 평가 될 때 `true` 조건이 충족 되 고 정의가 사용 됩니다.

[GroupBy (형식)에 대 한 SelectionCondition의 PropertyName 요소](./propertyname-element-for-selectioncondition-for-groupby-format.md) 조건을 트리거하는 .NET 속성을 지정 합니다. 이 속성이 존재 하거나로 평가 될 때 `true` 조건이 충족 되 고 정의가 사용 됩니다. 이 요소는 새 개체 그룹이 표시 되는 방법을 정의 하는 데 사용 됩니다.

[ListEntry (형식)의 경우 EntrySelectedBy에 대 한 SelectionCondition의 PropertyName 요소](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md) 조건을 트리거하는 .NET 속성을 지정 합니다. 이 속성이 존재 하거나로 확인 되 면 `true` 조건이 충족 되 고 목록 항목이 사용 됩니다.

[TableRowEntry (형식)의 경우 EntrySelectedBy에 대 한 SelectionCondition의 PropertyName 요소](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md) 조건을 트리거하는 .NET 속성을 지정 합니다. 이 속성이 존재 하거나로 평가 될 때 `true` 조건이 충족 되 고 테이블 항목이 사용 됩니다.

[WideEntry (형식)의 경우 EntrySelectedBy에 대 한 SelectionCondition의 PropertyName 요소](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md) 조건을 트리거하는 .NET 속성을 지정 합니다. 이 속성이 존재 하거나로 평가 될 때 `true` 조건이 충족 되 고 정의가 사용 됩니다.

[TableColumnItem에 대 한 PropertyName 요소 (형식)](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) 행의 열에 값이 표시 되는 속성을 지정 합니다.

[WideItem에 대 한 PropertyName 요소 (형식)](./propertyname-element-for-wideitem-for-widecontrol-format.md) 넓은 보기에 값이 표시 되는 개체의 속성을 지정 합니다.

[구성에 대 한 컨트롤의 프레임에 대 한 Rightindent 요소 (형식)](./rightindent-element-for-frame-for-controls-for-configuration-format.md) 데이터가 오른쪽 여백에서 벗어나 이동 하는 문자 수를 지정 합니다. 이 요소는 서식 파일의 모든 뷰에서 사용할 수 있는 공용 컨트롤을 정의 하는 데 사용 됩니다.

[View 컨트롤 프레임의 오른쪽 들여쓰기 요소 (형식)](./rightindent-element-for-frame-for-controls-for-view-format.md) 데이터가 오른쪽 여백에서 벗어나 이동 하는 문자 수를 지정 합니다. 이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의 하는 데 사용 됩니다.

[Rightindent 요소](./rightindent-element-for-frame-for-customcontrol-for-view-format.md) 데이터가 오른쪽 여백에서 벗어나 이동 하는 문자 수를 지정 합니다. 이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.

[GroupBy의 프레임에 대 한 Rightindent 요소 (형식)](./rightindent-element-for-frame-for-groupby-format.md) 데이터가 오른쪽 여백에서 벗어나 이동 하는 문자 수를 지정 합니다. 이 요소는 새 개체 그룹이 표시 되는 방법을 정의 하는 데 사용 됩니다.

[구성에 대 한 컨트롤에 대 한 ExpressionBinding의 ScriptBlock 요소 (형식)](./scriptblock-element-for-expressionbinding-for-controls-for-configuration-format.md) 공용 컨트롤에서 값을 표시 하는 스크립트를 지정 합니다. 이 요소는 서식 파일의 모든 뷰에서 사용할 수 있는 공용 컨트롤을 정의 하는 데 사용 됩니다.

[View 컨트롤의 ExpressionBinding에 대 한 ScriptBlock 요소 (형식)](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md) 컨트롤에서 값을 표시 하는 스크립트를 지정 합니다. 이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의 하는 데 사용 됩니다.

CustomCustomControl에 대 한 [ExpressionBinding의 ScriptBlock 요소 (형식)](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md) 컨트롤에서 값을 표시 하는 스크립트를 지정 합니다. 이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.

[GroupBy (형식)에 대 한 ExpressionBinding의 ScriptBlock 요소](./scriptblock-element-for-expressionbinding-for-groupby-format.md) 컨트롤에서 값을 표시 하는 스크립트를 지정 합니다. 이 요소는 새 개체 그룹이 표시 되는 방법을 정의 하는 데 사용 됩니다.

[GroupBy (형식)에 대 한 ScriptBlock 요소](./scriptblock-element-for-groupby-format.md) 값이 변경 될 때마다 새 그룹을 시작 하는 스크립트를 지정 합니다.

[구성에 대 한 ItemSelectionCondition의 ScriptBlock 요소 (형식)](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) 조건을 트리거하는 스크립트를 지정 합니다. 이 스크립트를로 계산 하면 `true` 조건이 충족 되 고 컨트롤이 사용 됩니다. 이 요소는 서식 파일의 모든 뷰에서 사용할 수 있는 공용 컨트롤을 정의 하는 데 사용 됩니다.

[View 컨트롤에 대 한 ItemSelectionCondition의 ScriptBlock 요소 (형식)](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md) 조건을 트리거하는 스크립트를 지정 합니다. 이 스크립트를로 계산 하면 `true` 조건이 충족 되 고 컨트롤이 사용 됩니다. 이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의 하는 데 사용 됩니다.

CustomControl에 대 한 [ItemSelectionCondition의 ScriptBlock 요소 (형식)](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) 조건을 트리거하는 스크립트를 지정 합니다. 이 스크립트를로 계산 하면 `true` 조건이 충족 되 고 컨트롤이 사용 됩니다. 이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.

[GroupBy (형식)에 대 한 ItemSelectionCondition의 ScriptBlock 요소](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md) 조건을 트리거하는 스크립트를 지정 합니다. 이 스크립트를로 계산 하면 `true` 조건이 충족 되 고 컨트롤이 사용 됩니다. 이 요소는 새 개체 그룹이 표시 되는 방법을 정의 하는 데 사용 됩니다.

[이 listcontrol (형식)에 대 한 ItemSelectionCondition의 ScriptBlock 요소](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) 조건을 트리거하는 스크립트를 지정 합니다. 이 스크립트를로 평가 하면 `true` 조건이 충족 되 고 목록 항목이 사용 됩니다. 이 요소는 목록 뷰를 정의할 때 사용 됩니다.

[ListItem의 ScriptBlock 요소 (Format)](./scriptblock-element-for-listitem-for-listcontrol-format.md) 목록의 행에 값이 표시 되는 스크립트를 지정 합니다.

[구성 컨트롤에 대 한 SelectionCondition의 ScriptBlock 요소 (형식)](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md) 조건을 트리거하는 스크립트를 지정 합니다. 이 스크립트를로 평가 하면 `true` 조건이 충족 되 고 정의가 사용 됩니다. 이 요소는 서식 파일의 모든 뷰에서 사용할 수 있는 공용 컨트롤을 정의 하는 데 사용 됩니다.

[View 컨트롤의 SelectionCondition에 대 한 ScriptBlock 요소 (형식)](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md) 조건을 트리거하는 스크립트를 지정 합니다. 이 스크립트를로 평가 하면 `true` 조건이 충족 되 고 정의가 사용 됩니다. 이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의 하는 데 사용 됩니다.

CustomControl에 대 한 [SelectionCondition의 ScriptBlock 요소 (형식)](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md) 조건을 트리거하는 스크립트를 지정 합니다. 이 스크립트를로 평가 하면 `true` 조건이 충족 되 고 정의가 사용 됩니다. 이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.

[EnumerableExpansion (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md) 조건을 트리거하는 스크립트를 지정 합니다.

[GroupBy (형식)에 대 한 SelectionCondition의 ScriptBlock 요소](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format.md) 조건을 트리거하는 스크립트를 지정 합니다. 이 스크립트를로 평가 하면 `true` 조건이 충족 되 고 정의가 사용 됩니다. 이 요소는 새 개체 그룹이 표시 되는 방법을 정의 하는 데 사용 됩니다.

[ListEntry (형식)의 경우 EntrySelectedBy에 대 한 SelectionCondition의 ScriptBlock 요소](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md) 조건을 트리거하는 스크립트를 지정 합니다. 이 스크립트를로 평가 하면 `true` 조건이 충족 되 고 목록 항목이 사용 됩니다.

[TableRowEntry (형식)의 경우 EntrySelectedBy에 대 한 SelectionCondition의 ScriptBlock 요소](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md) 조건을 트리거하는 스크립트 블록을 지정 합니다. 이 스크립트를로 평가 하면 `true` 조건이 충족 되 고 테이블 항목이 사용 됩니다.

[WideEntry (형식)의 경우 EntrySelectedBy에 대 한 SelectionCondition의 ScriptBlock 요소](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md) 조건을 트리거하는 스크립트를 지정 합니다. 이 스크립트를로 평가 하면 `true` 조건이 충족 되 고 넓은 항목 정의가 사용 됩니다.

[TableColumnItem에 대 한 ScriptBlock 요소 (형식)](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) 행의 열에 값이 표시 되는 스크립트를 지정 합니다.

[WideItem에 대 한 ScriptBlock 요소 (형식)](./scriptblock-element-for-wideitem-for-widecontrol-format.md) 넓은 보기에 값이 표시 되는 스크립트를 지정 합니다.

[구성 (형식)에 대 한 CustomEntry에 대해 EntrySelectedBy의 Selectioncondition 요소](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md) 공용 컨트롤 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다. 이 요소는 서식 파일의 모든 뷰에서 사용할 수 있는 공용 컨트롤을 정의 하는 데 사용 됩니다.

[보기의 컨트롤에 대해 EntrySelectedBy의 Selectioncondition 요소 (형식)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md) 컨트롤 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다. 이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의 하는 데 사용 됩니다.

[CustomControl For View (Format)에 대해 EntrySelectedBy의 Selectioncondition 요소](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md) 컨트롤 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다. 이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.

[EnumerableExpansion (형식)에 대 한 EntrySelectedBy의 Selectioncondition 요소](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md) 이 정의의 컬렉션 개체를 확장 하기 위해 있어야 하는 조건을 정의 합니다.

[GroupBy (형식)에 대 한 EntrySelectedBy의 Selectioncondition 요소](./selectioncondition-element-for-entryselectedby-for-groupby-format.md) 컨트롤 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다. 이 요소는 새 개체 그룹이 표시 되는 방법을 정의 하는 데 사용 됩니다.

[ListEntry (형식)에 대 한 EntrySelectedBy의 Selectioncondition 요소](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) 목록 뷰의이 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다. 목록 정의에 지정할 수 있는 선택 조건 수에는 제한이 없습니다.

[TableRowEntry (형식)에 대 한 EntrySelectedBy의 Selectioncondition 요소](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md) 테이블 뷰의이 정의에 사용할 조건을 정의 합니다. 테이블 정의에 지정할 수 있는 선택 조건 수에는 제한이 없습니다.

[WideEntry (형식)에 대 한 EntrySelectedBy의 Selectioncondition 요소](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) 이 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다. 넓은 항목 정의에 대해 지정할 수 있는 선택 조건 수에는 제한이 없습니다.

[Selectionset 요소 (형식)](./selectionset-element-format.md) 집합의 이름으로 참조할 수 있는 .NET 개체 집합을 정의 합니다.

[구성 (형식)의 컨트롤에 대 한 EntrySelectedBy의 SelectionSetName 요소](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md) 컨트롤의이 정의를 사용 하는 .NET 형식 집합을 지정 합니다. 이 요소는 서식 파일의 모든 뷰에서 사용할 수 있는 공용 컨트롤을 정의 하는 데 사용 됩니다.

[View의 컨트롤에 대 한 EntrySelectedBy의 SelectionSetName 요소 (형식)](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md) 컨트롤의이 정의를 사용 하는 .NET 형식 집합을 지정 합니다. 이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의 하는 데 사용 됩니다.

[Customentry (형식)에 대 한 EntrySelectedBy 요소](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md) 목록 항목에 대 한 .NET 개체 집합을 지정 합니다. 항목에 지정할 수 있는 선택 집합 수에는 제한이 없습니다.

[EnumerableExpansion (형식)에 대 한 EntrySelectedBy의 SelectionSetName 요소](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md) 이 정의에 의해 확장 되는 .NET 형식 집합을 지정 합니다.

[GroupBy (형식)에 대 한 EntrySelectedBy의 SelectionSetName 요소](./selectionsetname-element-for-entryselectedby-for-groupby-format.md) 목록 항목에 대 한 .NET 개체 집합을 지정 합니다. 항목에 지정할 수 있는 선택 집합 수에는 제한이 없습니다. 이 요소는 새 개체 그룹이 표시 되는 방법을 정의 하는 데 사용 됩니다.

[ListEntry (형식)에 대 한 EntrySelectedBy의 SelectionSetName 요소](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) 목록 항목에 대 한 .NET 개체 집합을 지정 합니다. 항목에 지정할 수 있는 선택 집합 수에는 제한이 없습니다.

[TableRowEntry (형식)에 대 한 EntrySelectedBy의 SelectionSetName 요소](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md) 테이블 뷰의이 항목을 사용 하는 .NET 형식 집합을 지정 합니다. 항목에 지정할 수 있는 선택 집합 수에는 제한이 없습니다.

[WideEntry (형식)에 대 한 EntrySelectedBy의 SelectionSetName 요소](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md) 정의에 대 한 .NET 개체 집합을 지정 합니다. 정의는 이러한 개체 중 하나가 표시 될 때마다 사용 됩니다.

[구성에 대 한 컨트롤의 SelectionCondition에 대 한 SelectionSetName 요소 (형식)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md) 조건을 트리거하는 .NET 형식 집합을 지정 합니다. 이 집합에 있는 형식이 있으면 조건이 충족 되 고이 컨트롤을 사용 하 여 개체가 표시 됩니다. 이 요소는 서식 파일의 모든 뷰에서 사용할 수 있는 공용 컨트롤을 정의 하는 데 사용 됩니다.

[View 컨트롤의 SelectionCondition에 대 한 SelectionSetName 요소 (형식)](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md) 조건을 트리거하는 .NET 형식 집합을 지정 합니다. 이 집합에 있는 형식이 있으면 조건이 충족 되 고이 컨트롤을 사용 하 여 개체가 표시 됩니다. 이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의 하는 데 사용 됩니다.

[View의 CustomEntry에 대 한 Entryselectedby 요소 (형식)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md) 조건을 트리거하는 .NET 형식 집합을 지정 합니다. 이 집합에 있는 형식이 있으면 조건이 충족 되 고이 컨트롤을 사용 하 여 개체가 표시 됩니다. 이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.

[EnumerableExpansion (Format)에 대해 EntrySelectedBy의 SelectionCondition에 대 한 SelectionSetName 요소](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md) 조건을 트리거하는 .NET 형식 집합을 지정 합니다. 이 집합에 있는 형식이 있으면 조건이 충족 됩니다.

[GroupBy (Format)의 SelectionCondition에 대 한 SelectionSetName 요소](./selectionsetname-element-for-selectioncondition-for-groupby-format.md) 조건을 트리거하는 .NET 형식 집합을 지정 합니다. 이 집합에 있는 형식이 있으면 조건이 충족 되 고이 컨트롤을 사용 하 여 개체가 표시 됩니다. 이 요소는 새 개체 그룹이 표시 되는 방법을 정의 하는 데 사용 됩니다.

[ListEntry (형식)에 대 한 EntrySelectedBy의 SelectionCondition에 대 한 SelectionSetName 요소](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md) 조건을 트리거하는 .NET 형식 집합을 지정 합니다. 이 집합에 있는 형식이 있으면 조건이 충족 되 고 목록 뷰의이 정의를 사용 하 여 개체가 표시 됩니다.

[TableRowEntry (형식)에 대 한 EntrySelectedBy의 SelectionCondition에 대 한 SelectionSetName 요소](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md) 조건을 트리거하는 .NET 형식 집합을 지정 합니다. 이 집합의 형식 중 하나라도 있으면 조건이 충족 되 고 테이블 뷰의이 정의를 사용 하 여 개체가 표시 됩니다.

[WideEntry (형식)에 대 한 EntrySelectedBy의 SelectionCondition에 대 한 SelectionSetName 요소](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md) 조건을 트리거하는 .NET 형식 집합을 지정 합니다. 이 집합의 형식 중 하나라도 있으면 조건이 충족 되 고이 개체는 넓은 보기의이 정의를 사용 하 여 표시 됩니다.

[ViewSelectedBy (형식)에 대 한 SelectionSetName 요소](./selectionsetname-element-for-viewselectedby-format.md) 뷰에 표시 되는 .NET 개체의 집합을 지정 합니다.

[Selectionsets 요소 (형식)](./selectionsets-element-format.md) 개별 형식 보기에서 사용할 수 있는 .NET 개체 집합을 정의 합니다.

[Showerror 요소 (Format)](./showerror-element-format.md) 데이터 조각을 표시 하는 동안 오류가 발생 하면 전체 오류 레코드가 표시 되도록 지정 합니다.

[TableControl (Format)의 TableHeaders에 대 한 TableColumnHeader 요소](./tablecolumnheader-element-format.md) 테이블의 열에 대 한 레이블, 열의 너비 및 레이블의 맞춤을 정의 합니다.

[TableColumnItem 요소 (Format)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) 행의 열에 값이 표시 되는 속성이 나 스크립트를 정의 합니다.

[TableColumnItems 요소 (Format)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) 행에 값이 표시 되는 속성 또는 스크립트를 정의 합니다.

[TableControl 요소 (Format)](./tablecontrol-element-format.md) 뷰의 테이블 형식을 정의 합니다.

[Tableheaders 요소 (Format)](./tableheaders-element-format.md) 테이블의 열에 대 한 헤더를 정의 합니다.

[TableRowEntries 요소 (Format)](./tablerowentries-element-for-tablecontrol-format.md) 테이블의 행을 정의 합니다.

[TableRowEntry 요소 (Format)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md) 테이블의 행에 표시 되는 데이터를 정의 합니다.

[구성에 대 한 컨트롤의 CustomItem에 대 한 텍스트 요소 (형식)](./text-element-for-customitem-for-controls-for-configuration-format.md) 컨트롤에 의해 표시 되는 데이터에 추가 되는 텍스트를 지정 합니다. 예를 들어 레이블, 데이터를 묶는 대괄호 및 데이터를 들여쓰는 공간입니다. 이 요소는 서식 파일의 모든 뷰에서 사용할 수 있는 공용 컨트롤을 정의 하는 데 사용 됩니다.

[뷰 컨트롤의 CustomItem에 대 한 텍스트 요소 (형식)](./text-element-for-customitem-for-controls-for-view-format.md) 컨트롤에 의해 표시 되는 데이터에 추가 되는 텍스트를 지정 합니다. 예를 들어 레이블, 데이터를 묶는 대괄호 및 데이터를 들여쓰는 공간입니다. 이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의 하는 데 사용 됩니다.

[CustomItem에 대 한 텍스트 요소 (형식)](./text-element-for-customitem-for-customview-for-view-format.md) 컨트롤에 의해 표시 되는 데이터에 추가 되는 텍스트를 지정 합니다. 예를 들어 레이블, 데이터를 묶는 대괄호 및 데이터를 들여쓰는 공간입니다. 이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.

[GroupBy의 CustomItem에 대 한 텍스트 요소 (형식)](./text-element-for-customitem-for-groupby-format.md) 컨트롤에 의해 표시 되는 데이터에 추가 되는 텍스트를 지정 합니다. 예를 들어 레이블, 데이터를 묶는 대괄호 및 데이터를 들여쓰는 공간입니다. 이 요소는 새 개체 그룹이 표시 되는 방법을 정의 하는 데 사용 됩니다.

[구성 (형식)의 컨트롤에 대 한 EntrySelectedBy의 TypeName 요소](./typename-element-for-entryselectedby-for-controls-for-configuration-format.md) 컨트롤의이 정의를 사용 하는 .NET 형식을 지정 합니다. 이 요소는 서식 파일의 모든 뷰에서 사용할 수 있는 공용 컨트롤을 정의 하는 데 사용 됩니다.

[View 컨트롤에 대 한 EntrySelectedBy (형식)의 TypeName 요소](./typename-element-for-entryselectedby-for-controls-for-view-format.md) 컨트롤의이 정의를 사용 하는 .NET 형식을 지정 합니다. 이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의 하는 데 사용 됩니다.

[View (Format)의 CustomEntry에 대해 EntrySelectedBy의 TypeName 요소](./typename-element-for-entryselectedby-for-customentry-for-view-format.md) 사용자 지정 컨트롤 뷰의이 정의를 사용 하는 .NET 형식을 지정 합니다. 정의에 대해 지정할 수 있는 형식 수에는 제한이 없습니다.

[EnumerableExpansion (형식)에 대 한 EntrySelectedBy의 TypeName 요소](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md) 이 정의에 의해 확장 되는 .NET 형식을 지정 합니다. 이 요소는 기본 설정을 정의할 때 사용 됩니다.

[GroupBy (형식)에 대 한 EntrySelectedBy의 TypeName 요소](./typename-element-for-entryselectedby-for-groupby-format.md) 사용자 지정 컨트롤의이 정의를 사용 하는 .NET 형식을 지정 합니다. 이 요소는 새 개체 그룹이 표시 되는 방법을 정의 하는 데 사용 됩니다.

[이 listcontrol에 대 한 EntrySelectedBy (형식)의 TypeName 요소](./typename-element-for-entryselectedby-for-listcontrol-format.md) 목록 뷰의이 항목을 사용 하는 .NET 형식을 지정 합니다. 목록 항목에 대해 지정할 수 있는 형식 수에는 제한이 없습니다.

[TableRowEntry에 대 한 EntrySelectedBy (형식)의 TypeName 요소](./typename-element-for-entryselectedby-for-tablecontrol-format.md) 테이블 뷰의이 항목을 사용 하는 .NET 유형을 지정 합니다. 테이블 항목에 대해 지정할 수 있는 형식 수에는 제한이 없습니다.

[WideEntry에 대 한 EntrySelectedBy (형식)의 TypeName 요소](./typename-element-for-entryselectedby-for-wideentry-format.md) 정의에 대 한 .NET 유형을 지정 합니다. 이 개체가 표시 될 때마다 정의가 사용 됩니다.

[구성 컨트롤에 대 한 SelectionCondition의 TypeName 요소 (형식)](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md) 조건을 트리거하는 .NET 유형을 지정 합니다. 이 요소는 서식 파일의 모든 뷰에서 사용할 수 있는 공용 컨트롤을 정의 하는 데 사용 됩니다.

[View 컨트롤의 SelectionCondition에 대 한 TypeName 요소 (형식)](./typename-element-for-selectioncondition-for-controls-for-view-format.md) 조건을 트리거하는 .NET 유형을 지정 합니다. 이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의 하는 데 사용 됩니다.

CustomControl에 대 한 [SelectionCondition의 TypeName 요소 (형식)](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md) 조건을 트리거하는 .NET 유형을 지정 합니다. 이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.

[EnumerableExpansion (형식)의 경우 EntrySelectedBy에 대 한 SelectionCondition의 TypeName 요소](./typename-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md) 조건을 트리거하는 .NET 유형을 지정 합니다.

[GroupBy (형식)에 대 한 SelectionCondition의 TypeName 요소](./typename-element-for-selectioncondition-for-groupby-format.md) 조건을 트리거하는 .NET 유형을 지정 합니다. 이 요소는 새 개체 그룹이 표시 되는 방법을 정의 하는 데 사용 됩니다.

[이 listcontrol (형식)에 대해 EntrySelectedBy의 SelectionCondition에 대 한 TypeName 요소](./typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md) 조건을 트리거하는 .NET 유형을 지정 합니다. 이 형식이 있으면 목록 항목이 사용 됩니다.

[TableRowEntry (형식)에 대해 EntrySelectedBy의 SelectionCondition에 대 한 TypeName 요소](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md) 조건을 트리거하는 .NET 유형을 지정 합니다. 이 형식이 있으면 조건이 충족 되 고 테이블 행이 사용 됩니다.

[WideEntry (형식)에 대해 EntrySelectedBy의 SelectionCondition에 대 한 TypeName 요소](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md) 조건을 트리거하는 .NET 유형을 지정 합니다. 이 형식이 있으면 정의가 사용 됩니다.

[형식에 대 한 TypeName 요소 (형식)](./typename-element-for-types-format.md) 선택 집합에 속하는 개체의 .NET 유형을 지정 합니다.

[ViewSelectedBy (형식)에 대 한 TypeName 요소](./typename-element-for-viewselectedby-format.md) 뷰에 표시 되는 .NET 개체를 지정 합니다.

[Types 요소 (Format)](./types-element-for-selectionset-format.md) 선택 집합에 있는 .NET 개체를 정의 합니다.

[View 요소 (Format)](./view-element-format.md) 하나 이상의 .NET 개체를 표시 하는 데 사용 되는 뷰를 정의 합니다.

[Viewdefinitions 요소 (형식)](./viewdefinitions-element-format.md) 개체를 표시 하는 데 사용 되는 뷰를 정의 합니다.

[Viewselectedby 요소 (형식)](./viewselectedby-element-format.md) 뷰에 표시 되는 .NET 개체를 정의 합니다.

[WideControl 요소 (Format)](./widecontrol-element-format.md) 뷰의 넓은 (단일 값) 목록 형식을 정의 합니다. 이 보기에는 각 개체에 대 한 단일 속성 값 또는 스크립트 값이 표시 됩니다.

[WideEntries 요소 (Format)](./wideentries-element-for-widecontrol-format.md) 넓은 뷰의 정의를 제공 합니다. 넓은 보기는 하나 이상의 정의를 지정 해야 합니다.

[WideEntry 요소 (Format)](./wideentry-element-for-widecontrol-format.md) 넓은 뷰의 정의를 제공 합니다.

[WideItem 요소 (Format)](./wideitem-element-for-widecontrol-format.md) 값이 표시 되는 속성 또는 스크립트를 정의 합니다.

[Width 요소 (Format)](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) 열의 너비 (문자)를 정의 합니다.

[Wrap 요소 (Format)](./wrap-element-for-tablerowentry-for-tablecontrol-format.md) 열 너비를 초과 하는 텍스트를 다음 줄에 표시 하도록 지정 합니다.

[WrapTables 요소 (Format)](./wraptables-element-format.md) 데이터가 열의 너비 보다 길면 표 셀의 데이터가 다음 줄로 이동 하도록 지정 합니다.

## <a name="see-also"></a>참고 항목

[PowerShell 형식 지정 파일 작성](./writing-a-powershell-formatting-file.md)
