---
title: XML 참조 스키마 형식 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ac6f7aaa-d0cc-4c7b-a341-85e736174579
caps.latest.revision: 21
ms.openlocfilehash: 4dfe27a5105d82fa18e35f965f92fad16d390a2a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857789"
---
# <a name="format-schema-xml-reference"></a>형식 스키마 XML 참조

이 섹션의에서 항목에서는 형식 지정 파일 (Format.ps1xml 파일)에서 사용 하는 XML 요소를 설명 합니다. .NET 개체 표시 되는 방식을; 형식 지정 파일 정의 개체 자체를 변경 하지 마세요.

## <a name="in-this-section"></a>이 섹션의 내용

[TableControl (형식)에 대 한 TableColumnHeader에 대 한 맞춤 요소](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) 열 머리글의 데이터가 표시 되는 방식을 정의 합니다.

[TableControl (형식)에 대 한 TableColumnItem에 대 한 맞춤 요소](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) 데이터 행에 표시 되는 방식을 정의 합니다.

[TableControl (형식)에 대 한 자동 크기 조정 요소](./autosize-element-for-tablecontrol-format.md) 데이터의 크기에 따라 열의 개수와 열 크기 조정 여부를 지정 합니다.

[WideControl (형식)에 대 한 자동 크기 조정 요소](./autosize-element-for-widecontrol-format.md) 데이터의 크기에 따라 열의 개수와 열 크기 조정 여부를 지정 합니다.

[ColumnNumber 요소 WideControl (형식)에 대 한](./columnnumber-element-for-widecontrol-format.md) 넓은 보기에 표시 된 열의 수를 지정 합니다.

[구성 요소 (형식)](./configuration-element-format.md) 서식 파일의 최상위 요소를 나타냅니다.

[컨트롤 구성 (형식)에 대 한 컨트롤에 대 한 요소](./control-element-for-controls-for-configuration-format.md) 컨트롤을 참조 하는 데 사용 되는 이름과 형식 지정 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 정의 합니다.

[컨트롤 뷰 (형식)에 대 한 컨트롤에 대 한 요소](./control-element-for-controls-for-view-format.md) 보기와 컨트롤을 참조 하는 데 사용 되는 이름으로 사용할 수 있는 컨트롤을 정의 합니다.

[Configuration (형식)의 요소를 제어](./controls-element-for-configuration-format.md) 서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 정의 합니다.

[요소 (형식) 보기에 대 한 제어](./controls-element-for-view-format.md) 특정 보기를 사용할 수 있는 뷰 컨트롤을 정의 합니다.

[구성 (형식)에 대 한 컨트롤에 대 한 CustomControl 요소](./customcontrol-element-for-control-for-controls-for-configuration-format.md) 컨트롤을 정의 합니다. 이 요소는 서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 정의할 때 사용 됩니다.

[뷰 (형식)에 대 한 컨트롤에 대 한 컨트롤에 대 한 CustomControl 요소](./customcontrol-element-for-control-for-controls-for-view-format.md) 보기에서 사용 되는 컨트롤을 정의 합니다.

[GroupBy (형식)에 대 한 CustomControl 요소](./customcontrol-element-for-groupby-format.md) 새 그룹을 표시 하는 사용자 지정 컨트롤을 정의 합니다.

[CustomControl 요소 (형식)](./customcontrol-element-for-groupby-format.md) 뷰에 대 한 사용자 지정 컨트롤 형식을 정의 합니다.

[구성 (형식)에 대 한 컨트롤에 대 한 ExpressionBinding에 대 한 CustomControlName 요소](./customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format.md) 공용 컨트롤의 이름을 지정 합니다. 이 요소는 서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 정의할 때 사용 됩니다.

[뷰 (형식)에 대 한 컨트롤에 대 한 ExpressionBindine CustomControlName 요소](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md) 공용 컨트롤에서 뷰 컨트롤의 이름을 지정 합니다. 이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의할 때 사용 됩니다.

[GroupBy (형식)의 CustomControlName 요소](./customcontrolname-element-for-groupby-format.md) 새 그룹을 표시 하는 데 사용 되는 사용자 지정 컨트롤의 이름을 지정 합니다. 이 요소는 테이블, 목록, 와이드 또는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.

[구성 (형식)에 대 한 컨트롤에 대 한 CustomControl CustomEntry 요소](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md) 공용 컨트롤의 정의 제공 합니다. 이 요소는 서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 정의할 때 사용 됩니다.

[뷰 (형식)에 대 한 컨트롤에 대 한 CustomEntries CustomEntry 요소](./customentry-element-for-customentries-for-controls-for-view-format.md) 컨트롤의 정의 제공 합니다. 이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의할 때 사용 됩니다.

[뷰 (형식)에 대 한 CustomEntries CustomEntry 요소](./customentry-element-for-customentries-for-customcontrol-for-view-format.md) 사용자 지정 컨트롤 뷰의 정의 제공 합니다.

[GroupBy (형식)에 대 한 CustomControl CustomEntry 요소](./customentry-element-for-customcontrol-for-groupby-format.md) 컨트롤의 정의 제공 합니다. 이 요소는 새 개체 그룹에 표시 되는 방식을 정의 하는 경우에 사용 됩니다.

[구성 (형식)에 대 한 CustomControl CustomEntries 요소](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md) 공용 컨트롤의 정의 제공 합니다. 이 요소는 서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 정의할 때 사용 됩니다.

[뷰 (형식)에 대 한 컨트롤에 대 한 CustomControl CustomEntries 요소](./customentries-element-for-customcontrol-for-controls-for-view-format.md) 컨트롤에 대 한 정의 제공 합니다. 이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의할 때 사용 됩니다.

[GroupBy (형식)에 대 한 CustomControl CustomEntries 요소](./customentries-element-for-customcontrol-for-groupby-format.md) 컨트롤에 대 한 정의 제공 합니다. 이 요소는 새 개체 그룹에 표시 되는 방식을 정의 하는 경우에 사용 됩니다.

[뷰 (형식)에 대 한 CustomControl CustomEntries 요소](./customentries-element-for-customcontrol-for-view-format.md) 사용자 지정 컨트롤 뷰의 정의 제공 합니다. 사용자 지정 컨트롤 뷰는 하나 이상의 정의 지정 해야 합니다.

[구성에 대 한 컨트롤에 대 한 CustomEntry CustomItem 요소](./customitem-element-for-customentry-for-controls-for-configuration-format.md) 컨트롤에서 표시 되는 데이터 및 표시 되는 방식을 정의 합니다. 이 요소는 서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 정의할 때 사용 됩니다.

[뷰 (형식)에 대 한 컨트롤에 대 한 CustomEntry CustomItem 요소](./customitem-element-for-customentry-for-controls-for-view-format.md) 컨트롤에서 표시 되는 데이터 및 표시 되는 방식을 정의 합니다. 이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의할 때 사용 됩니다.

[뷰 (형식)에 대 한 CustomEntry CustomItem 요소](./customitem-element-for-customentry-for-customcontrol-for-view-format.md) 사용자 지정 컨트롤 보기에 의해 표시 되는 데이터 및 표시 되는 방식을 정의 합니다. 이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.

[GroupBy (형식)에 대 한 CustomEntry CustomItem 요소](./customitem-element-for-customentry-for-groupby-format.md) 사용자 지정 컨트롤 보기에 의해 표시 되는 데이터 및 표시 되는 방식을 정의 합니다. 이 요소는 새 개체 그룹에 표시 되는 방식을 정의 하는 경우에 사용 됩니다.

[DefaultSettings 요소 (형식)](./defaultsettings-element-format.md) 서식 파일의 모든 뷰에 적용 되는 일반적인 설정을 정의 합니다. 일반적인 설정의 컬렉션 확장 되는 방법을 정의 하는 테이블 및 기타 자동 줄 바꿈 오류 표시 포함 됩니다.

[DisplayError 요소 (Frmat)](./displayerror-element-format.md) 오류가 발생 하는 데이터의 일부를 표시 하는 경우 문자열 #ERR 표시 되도록 지정 합니다.

[구성 (형식)에 대 한 컨트롤에 대 한 CustomEntry EntrySelectedBy 요소](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md) 공용 컨트롤 또는이 컨트롤을 사용할 수 있어야 하는 조건을 정의 사용 하는.NET 유형을 정의 합니다. 이 요소는 서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 정의할 때 사용 됩니다.

[뷰 (형식)에 대 한 컨트롤에 대 한 CustomEntry EntrySelectedBy 요소](./entryselectedby-element-for-customentry-for-controls-for-view-format.md) 이 컨트롤 정의 또는이 정의를 사용할 수 있어야 하는 조건을 사용 하는.NET 유형을 정의 합니다. 이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의할 때 사용 됩니다.

[뷰 (형식)에 대 한 CustomEntry EntrySelectedBy 요소](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md) 이 사용자 지정 항목 또는 사용할이 항목에 대 한 있어야 하는 조건을 사용 하는.NET 유형을 정의 합니다.

[EnumerableExpansion (형식)에 대 한 EntrySelectedBy 요소](./entryselectedby-element-for-enumerableexpansion-format.md) 이 정의 또는이 정의를 사용할 수 있어야 하는 조건을 사용 하는.NET 유형을 정의 합니다.

[GroupBy (형식)에 대 한 CustomEntry EntrySelectedBy 요소](./entryselectedby-element-for-customentry-for-groupby-format.md) 이 컨트롤 정의 또는이 정의를 사용할 수 있어야 하는 조건을 사용 하는.NET 유형을 정의 합니다. 이 요소는 새 개체 그룹에 표시 되는 방식을 정의 하는 경우에 사용 됩니다.

[ListControl (형식)에 대 한 ListEntry EntrySelectedBy 요소](./entryselectedby-element-for-listentry-for-listcontrol-format.md) 이 목록 뷰 정의 또는이 정의를 사용할 수 있어야 하는 조건을 사용 하는.NET 유형을 정의 합니다. 대부분의 경우 목록 보기에 대 한 정의 하나만 필요 합니다. 그러나 동일한 목록 뷰를 사용 하 여 다른 개체에 대 한 다양 한 데이터를 표시 하려면 목록 보기에 대 한 여러 정의 제공할 수 있습니다.

[TableRowEntry (형식)에 대 한 EntrySelectedBy 요소](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) 행에 속성 값을 표시는.NET 형식을 정의 합니다.

[WideEntry (형식)에 대 한 EntrySelectedBy 요소](./entryselectedby-element-for-wideentry-format.md) 이 정의 된 와이드 보기인 경우 또는이 정의를 사용할 수 있어야 하는 조건을 사용 하는.NET 유형을 정의 합니다.

[EnumerableExpansion 요소 (형식)](./enumerableexpansion-element-format.md) 개체 뷰의 표시 될 때 확장 되는 특정.NET 컬렉션을 정의 합니다.

[EnumerableExpansions 요소 (형식)](./enumerableexpansions-element-format.md) .NET 컬렉션 개체를 보기에 표시 될 때 확장 되는 방법을 정의 합니다.

[구성 (형식)에 대 한 컨트롤에 대 한 ExpressionBinding에 대 한 EnumerateCollection 요소](./enumeratecollection-element-for-expressionbinding-for-controls-for-configuration-format.md) 지정 컬렉션의 요소가 컨트롤에서 표시 됩니다. 이 요소는 서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 정의할 때 사용 됩니다.

[뷰 (형식)에 대 한 컨트롤에 대 한 ExpressionBinding에 대 한 EnumerateCollection 요소](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md) 지정 컬렉션의 요소가 표시 됩니다. 이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의할 때 사용 됩니다.

[CustomControl 보려면 (형식)에 대 한 바인딩 식에 대 한 EnumerateCollection 요소](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md) 컬렉션의 요소 표시 되도록 지정 합니다. 이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.

[GroupBy (형식)에 대 한 ExpressionBinding에 대 한 EnumerateCollection 요소](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md) 컬렉션의 요소 표시 되도록 지정 합니다. 이 요소는 새 개체 그룹에 표시 되는 방식을 정의 하는 경우에 사용 됩니다.

[요소 (형식)를 확장](./expand-element-format.md) 이 정의 대 한 컬렉션 개체는 확장 하는 방법을 지정 합니다.

[ExpressionBinding 요소 구성 (형식)에 대 한 컨트롤에 대 한 CustomItem](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md) 컨트롤에 표시 되는 데이터를 정의 합니다. 이 요소는 서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 정의할 때 사용 됩니다.

[ExpressionBinding 요소 (형식) 보기에 대 한 컨트롤에 대 한 CustomItem](./expressionbinding-element-for-customitem-for-controls-for-view-format.md) 컨트롤에 표시 되는 데이터를 정의 합니다. 이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의할 때 사용 됩니다.

[ExpressionBinding 요소 CustomControl 보려면 (형식)에 대 한 CustomItem](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md) 컨트롤에 표시 되는 데이터를 정의 합니다. 이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.

[GroupBy (형식)에 대 한 CustomItem ExpressionBinding 요소](./expressionbinding-element-for-customitem-for-groupby-format.md) 컨트롤에 표시 되는 데이터를 정의 합니다. 이 요소는 새 개체 그룹에 표시 되는 방식을 정의 하는 경우에 사용 됩니다.

[구성 (형식)에 대 한 컨트롤에 대 한 프레임에 대 한 FirstLineHanging 요소](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) 데이터의 첫 번째 줄은 왼쪽으로 이동 하는 문자 수를 지정 합니다. 이 요소는 서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 정의할 때 사용 됩니다.

[프레임의 컨트롤의 보기 (형식)의 FirstLineHanging 요소](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) 데이터의 첫 번째 줄은 왼쪽으로 이동 하는 문자 수를 지정 합니다. 이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의할 때 사용 됩니다.

[뷰 (형식)에 대 한 CustomControl 프레임에 대 한 FirstLineHanging 요소](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) 데이터의 첫 번째 줄은 왼쪽으로 이동 하는 문자 수를 지정 합니다. 이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.

[GroupBy (형식)에 대 한 프레임에 대 한 FirstLineHanging 요소](./firstlinehanging-element-for-frame-for-groupby-format.md) 데이터의 첫 번째 줄은 왼쪽으로 이동 하는 문자 수를 지정 합니다. 이 요소는 새 개체 그룹에 표시 되는 방식을 정의 하는 경우에 사용 됩니다.

[구성 (형식)에 대 한 컨트롤에 대 한 프레임에 대 한 FirstLineIndent 요소](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) 데이터의 첫 번째 줄은 오른쪽으로 옮겨집니다 문자 수를 지정 합니다. 이 요소는 서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 정의할 때 사용 됩니다.

[프레임의 컨트롤의 보기 (형식)의 FirstLineIndent 요소](./firstlineindent-element-for-frame-for-controls-for-view-format.md) 데이터의 첫 번째 줄은 오른쪽으로 옮겨집니다 문자 수를 지정 합니다. 이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의할 때 사용 됩니다.

[FirstLineIndent 요소](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) 데이터의 첫 번째 줄은 오른쪽으로 옮겨집니다 문자 수를 지정 합니다. 이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.

[GroupBy (형식)에 대 한 프레임에 대 한 FirstLineIndent 요소](./firstlineindent-element-for-frame-for-groupby-format.md) 데이터의 첫 번째 줄은 오른쪽으로 옮겨집니다 문자 수를 지정 합니다. 이 요소는 새 개체 그룹에 표시 되는 방식을 정의 하는 경우에 사용 됩니다.

[ListItem (형식)에 대 한 FormatString 요소](./formatstring-element-for-listitem-for-listcontrol-format.md) 스크립트나 속성 값이 표시 되는 방식을 정의 하는 형식 패턴을 지정 합니다.

[FormatString 요소 TableColumnItem (형식)에 대 한](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md) 테이블의 속성이 나 스크립트 값 표시 되는 방식을 정의 하는 형식 패턴을 지정 합니다.

[FormatString 요소 WideControl (형식)에 대 한 WideItem](./formatstring-element-for-wideitem-for-widecontrol-format.md) 스크립트나 속성 값을 보기에 표시 되는 방식을 정의 하는 형식 패턴을 지정 합니다.

[구성 (형식)에 대 한 컨트롤에 대 한 CustomItem에 대 한 요소를 프레임](./frame-element-for-customitem-for-controls-for-configuration-format.md) 왼쪽 이나 오른쪽으로 데이터를 이동 하는 같은 데이터 표시 방법을 정의 합니다. 이 요소는 서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 정의할 때 사용 됩니다.

[요소 (형식) 보기에 대 한 컨트롤에 대 한 CustomItem에 대 한 프레임](./frame-element-for-customitem-for-controls-for-view-format.md) 왼쪽 이나 오른쪽으로 데이터를 이동 하는 같은 데이터 표시 방법을 정의 합니다. 이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의할 때 사용 됩니다.

[CustomControl 보려면 (형식)에 대 한 요소 CustomItem에 대 한 프레임](./frame-element-for-customitem-for-customcontrol-for-view-format.md) 왼쪽 이나 오른쪽으로 데이터를 이동 하는 같은 데이터 표시 방법을 정의 합니다. 이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.

[GroupBy (형식)에 대 한 요소 CustomItem에 대 한 프레임](./frame-element-for-customitem-for-groupby-format.md) 왼쪽 이나 오른쪽으로 데이터를 이동 하는 같은 데이터 표시 방법을 정의 합니다. 이 요소는 새 개체 그룹에 표시 되는 방식을 정의 하는 경우에 사용 됩니다.

[GroupBy 요소 (형식) 보기에 대 한](./groupby-element-for-view-format.md) Windows PowerShell 개체의 새 그룹을 표시 하는 방법을 정의 합니다.

[HideTableHeaders 요소 (형식)](./hidetableheaders-element-format.md) 테이블의 머리글은 표시 되지 않도록 지정 합니다.

[구성 (형식)에 대 한 컨트롤에 대 한 ExpressionBinding에 대 한 ItemSelectionCondition 요소](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md) 이 컨트롤을 사용할 수 있어야 하는 조건을 정의 합니다. 이 요소는 서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 정의할 때 사용 됩니다.

[ExpressionBinding 보기 (형식)에 대 한 컨트롤에 대 한 요소의 ItemSelectionCondition](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md) 이 컨트롤을 사용할 수 있어야 하는 조건을 정의 합니다. 이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의할 때 사용 됩니다.

[CustomControl 보려면 (형식)에 대 한 바인딩 식에 대 한 ItemSelectionCondition 요소](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md) 이 컨트롤을 사용할 수 있어야 하는 조건을 정의 합니다. 컨트롤 항목에 지정 될 수 있는 선택 조건 수 제한은 없습니다. 이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.

[GroupBy (형식)에 대 한 ExpressionBinding에 대 한 ItemSelectionCondition 요소](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md) 이 컨트롤을 사용할 수 있어야 하는 조건을 정의 합니다. 컨트롤 항목에 지정 될 수 있는 선택 조건 수 제한은 없습니다. 이 요소는 새 개체 그룹에 표시 되는 방식을 정의 하는 경우에 사용 됩니다.

[ListItem (형식)에 대 한 ItemSelectionCondition 요소](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md) 사용할이 목록 항목에 대 한 있어야 하는 조건을 정의 합니다.

[ListItem 요소 ListControl(Format)에 대 한 레이블에](./label-element-for-listitem-for-listcontrol-format.md) 행의 속성이 나 스크립트 값에 대 한 레이블을 지정 합니다.

[GroupBy (형식)에 대 한 요소 레이블을](./label-element-for-groupby-format.md) 새 그룹이 발견 될 때 표시 되는 레이블을 지정 합니다.

[TableColumnHeader (형식)에 대 한 요소 레이블을](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) 열의 맨 위에 있는 표시 되는 레이블을 정의 합니다.

[구성 (형식)에 대 한 컨트롤에 대 한 프레임에 대 한 LeftIndent 요소](./leftindent-element-for-frame-for-controls-for-configuration-format.md) 왼쪽된 여백에서 데이터 이동은 문자 수를 지정 합니다. 이 요소는 서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 정의할 때 사용 됩니다.

[프레임의 컨트롤의 보기 (형식)의 LeftIndent 요소](./leftindent-element-for-frame-for-controls-for-view-format.md) 왼쪽된 여백에서 데이터 이동은 문자 수를 지정 합니다. 이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의할 때 사용 됩니다.

[뷰 (형식)에 대 한 CustomControl 프레임에 대 한 LeftIndent 요소](./leftindent-element-for-frame-for-customcontrol-for-view-format.md) 왼쪽된 여백에서 데이터 이동은 문자 수를 지정 합니다. 이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.

[GroupBy (형식)에 대 한 프레임에 대 한 LeftIndent 요소](./leftindent-element-for-frame-for-groupby-format.md) 왼쪽된 여백에서 데이터 이동은 문자 수를 지정 합니다. 이 요소는 새 개체 그룹에 표시 되는 방식을 정의 하는 경우에 사용 됩니다.

[ListControl 요소 (형식)](./listcontrol-element-format.md) 뷰에 대 한 목록 형식을 정의 합니다.

[ListEntry 요소 (형식)](./listentry-element-for-listcontrol-format.md) 목록 보기의 정의 제공 합니다.

[ListEntries 요소 (형식)](./listentries-element-for-listcontrol-format.md) 목록 뷰의 행 표시 되는 방식을 정의 합니다.

[ListItem 요소 (형식)](./listitem-element-for-listitems-for-listcontrol-format.md) 속성 또는 목록 보기 행에 해당 값이 표시 되는 스크립트를 정의 합니다.

[ListItems 요소 (형식)](./listitems-element-for-listentry-for-listcontrol-format.md) 속성 및 목록 보기에 표시 되는 스크립트를 정의 합니다.

[구성 (형식)에 대 한 컨트롤에 대 한 컨트롤에 대 한 요소 이름을](./name-element-for-control-for-controls-for-configuration-format.md) 컨트롤의 이름을 지정 합니다. 이 요소는 서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 정의할 때 사용 됩니다.

[SelectionSet (형식)에 대 한 요소 이름을](./name-element-for-selectionset-format.md) 선택 집합을 참조 하는 데 사용 하는 이름을 지정 합니다.

[Name 요소 (형식) 보기에 대 한](./name-element-for-view-format.md) 뷰를 식별 하는 데 사용 되는 이름을 지정 합니다.

[줄 바꿈 요소 구성 (형식)에 대 한 컨트롤에 대 한 CustomItem](./newline-element-for-customitem-for-controls-for-configuration-format.md) 컨트롤의 표시에 빈 줄을 추가 합니다. 이 요소는 서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 정의할 때 사용 됩니다.

[줄 바꿈 (형식) 보기에 대 한 컨트롤에 대 한 CustomItem 요소](./newline-element-for-customitem-for-controls-for-view-format.md) 컨트롤의 표시에 빈 줄을 추가 합니다. 이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의할 때 사용 됩니다.

[줄 바꿈 CustomItem CustomControl 보려면 (형식)에 대 한 요소](./newline-element-for-customitem-for-customcontrol-for-view-format.md) 컨트롤의 표시에 빈 줄을 추가 합니다. 이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.

[GroupBy (형식)에 대 한 CustomItem 줄 바꿈 요소](./newline-element-for-customitem-for-groupby-format.md) 컨트롤의 표시에 빈 줄을 추가 합니다. 이 요소는 새 개체 그룹에 표시 되는 방식을 정의 하는 경우에 사용 됩니다.

[구성 (형식)에 대 한 컨트롤에 대 한 ExpressionBinding에 대 한 PropertyName 요소](./propertyname-element-for-expressionbinding-for-controls-for-configuration-format.md) 일반적인 컨트롤에서 해당 값이 표시 하는.NET 속성을 지정 합니다. 이 요소는 서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 정의할 때 사용 됩니다.

[뷰 (형식)에 대 한 컨트롤에 대 한 ExpressionBinding에 대 한 PropertyName 요소](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md) 컨트롤에서 해당 값이 표시 하는.NET 속성을 지정 합니다. 이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의할 때 사용 됩니다.

[ExpressionBinding CustomControl 보려면 (형식)에 대 한 PropertyName 요소](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md) 컨트롤에서 해당 값이 표시 하는.NET 속성을 지정 합니다. 사용자 지정 컨트롤 뷰를 정의 하는 경우이 요소를 사용 합니다.

[GroupBy (형식)에 대 한 ExpressionBinding에 대 한 PropertyName 요소](./propertyname-element-for-expressionbinding-for-groupby-format.md) 컨트롤에서 해당 값이 표시 하는.NET 속성을 지정 합니다. 이 요소는 새 개체 그룹에 표시 되는 방식을 정의 하는 경우에 사용 됩니다.

[GroupBy (형식)에 대 한 PropertyName 요소](./propertyname-element-for-groupby-format.md) 해당 값이 변경 될 때마다 새 그룹을 시작 하는.NET 속성을 지정 합니다.

[구성 (형식)에 대 한 컨트롤에 대 한 ItemSeclectionCondition PropertyName 요소](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) 조건을 트리거하는.NET 속성을 지정 합니다. 이 속성이 있는 경우 또는로 평가 되 면 `true`조건이 충족 되 고 컨트롤이 사용 합니다. 이 요소는 서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 정의할 때 사용 됩니다.

[PropertyName 요소 (형식) 보기에 대 한 컨트롤에 대 한 ItemSelectionCondition](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md) 조건을 트리거하는.NET 속성을 지정 합니다. 이 속성이 있는 경우 또는로 평가 되 면 `true`조건이 충족 되 고 컨트롤이 사용 합니다. 이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의할 때 사용 됩니다.

[보기에 대 한 CustomControl에 대 한 ItemSelectionCondition PropertyName 요소 (형식](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) 조건을 트리거하는.NET 속성을 지정 합니다. 이 속성이 있는 경우 또는로 평가 되 면 `true`조건이 충족 되 고 컨트롤이 사용 합니다. 이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.

[GroupBy (형식)에 대 한 ItemSelectionCondition PropertyName 요소](./propertyname-element-for-itemselectioncondition-for-groupby-format.md) 조건을 트리거하는.NET 속성을 지정 합니다. 이 속성이 있는 경우 또는로 평가 되 면 `true`조건이 충족 되 고 컨트롤이 사용 합니다. 이 요소는 새 개체 그룹에 표시 되는 방식을 정의 하는 경우에 사용 됩니다.

[ListItem (형식)에 대 한 ItemSelectionCondition PropertyName 요소](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md) 조건을 트리거하는.NET 속성을 지정 합니다. 이 속성이 있는 경우 또는로 평가 되 면 `true`, 조건이 충족 될 및 뷰가 사용 됩니다. 이 요소는 목록 뷰를 정의할 때 사용 됩니다.

[PropertyName ListControl (형식)에 대 한 ListItem 요소](./propertyname-element-for-listitem-for-listcontrol-format.md) 값 목록에 표시 되는.NET 속성을 지정 합니다.

[EntrySelectedBy ListEntry (형식)에 대 한에 대 한 SelectionCondition PropertyName 요소](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md) 조건을 트리거하는.NET 속성을 지정 합니다. 이 속성이 있는 경우 또는로 평가 되 면 `true`조건이 충족 되 고 항목이 사용 됩니다. 이 요소는 서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 정의할 때 사용 됩니다.

[PropertyName 요소 (형식) 보기에 대 한 컨트롤에 대 한 SelectionCondition](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md) 조건을 트리거하는.NET 속성을 지정 합니다. 이 속성이 있는 경우 또는로 평가 되 면 `true`조건이 충족 되 고 항목이 사용 됩니다. 이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의할 때 사용 됩니다.

[CustomControl 보려면 (형식)에 대 한 SelectionCondition PropertyName 요소](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md) 조건을 트리거하는.NET 속성을 지정 합니다. 이 속성이 있는 경우 또는로 평가 되 면 `true`조건이 충족 되 고 정의가 사용 됩니다. 이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.

[EntrySelectedBy EnumerableExpansion (형식)에 대 한에 대 한 SelectionCondition PropertyName 요소](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md) 조건을 트리거하는.NET 속성을 지정 합니다. 이 속성이 있는 경우 또는로 평가 되 면 `true`조건이 충족 되 고 정의가 사용 됩니다.

[GroupBy (형식)에 대 한 SelectionCondition PropertyName 요소](./propertyname-element-for-selectioncondition-for-groupby-format.md) 조건을 트리거하는.NET 속성을 지정 합니다. 이 속성이 있는 경우 또는로 평가 되 면 `true`조건이 충족 되 고 정의가 사용 됩니다. 이 요소는 새 개체 그룹에 표시 되는 방식을 정의 하는 경우에 사용 됩니다.

[EmtrySelectedBy ListEntry (형식)에 대 한에 대 한 SelectionCondition PropertyName 요소](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md) 조건을 트리거하는.NET 속성을 지정 합니다. 이 속성이 있는 경우 또는로 평가 되 면 `true`조건이 충족 되 고 목록 항목이 사용 됩니다.

[EntrySelectedBy TableRowEntry (형식)에 대 한에 대 한 SelectionCondition PropertyName 요소](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md) 조건을 트리거하는.NET 속성을 지정 합니다. 이 속성이 있는 경우 또는로 평가 되 면 `true`조건이 충족 되 고 테이블 항목이 사용 됩니다.

[EntrySelectedBy WideEntry (형식)에 대 한에 대 한 SelectionCondition PropertyName 요소](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md) 조건을 트리거하는.NET 속성을 지정 합니다. 이 속성이 있는 경우 또는로 평가 되 면 `true`조건이 충족 되 고 정의가 사용 됩니다.

[TableColumnItem (형식)에 대 한 PropertyName 요소](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) 값은 행의 열에 표시 되는 속성을 지정 합니다.

[WideItem (형식)에 대 한 PropertyName 요소](./propertyname-element-for-wideitem-for-widecontrol-format.md) 값인 와이드 보기에 표시 되는 개체의 속성을 지정 합니다.

[구성 (형식)에 대 한 컨트롤에 대 한 프레임에 대 한 RightIndent 요소](./rightindent-element-for-frame-for-controls-for-configuration-format.md) 오른쪽 여백에서 데이터 이동은 문자 수를 지정 합니다. 이 요소는 서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 정의할 때 사용 됩니다.

[프레임의 컨트롤의 보기 (형식)의 RightIndent 요소](./rightindent-element-for-frame-for-controls-for-view-format.md) 오른쪽 여백에서 데이터 이동은 문자 수를 지정 합니다. 이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의할 때 사용 됩니다.

[RightIndent 요소](./rightindent-element-for-frame-for-customcontrol-for-view-format.md) 오른쪽 여백에서 데이터 이동은 문자 수를 지정 합니다. 이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.

[GroupBy (형식)에 대 한 프레임에 대 한 RightIndent 요소](./rightindent-element-for-frame-for-groupby-format.md) 오른쪽 여백에서 데이터 이동은 문자 수를 지정 합니다. 이 요소는 새 개체 그룹에 표시 되는 방식을 정의 하는 경우에 사용 됩니다.

[구성 (형식)에 대 한 컨트롤에 대 한 ExpressionBinding에 대 한 ScriptBlock 요소](./scriptblock-element-for-expressionbinding-for-controls-for-configuration-format.md) 일반적인 컨트롤에서 해당 값이 표시 하는 스크립트를 지정 합니다. 이 요소는 서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 정의할 때 사용 됩니다.

[뷰 (형식)에 대 한 컨트롤에 대 한 ExpressionBinding에 대 한 ScriptBlock 요소](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md) 컨트롤에서 해당 값이 표시 하는 스크립트를 지정 합니다. 이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의할 때 사용 됩니다.

[ExpressionBinding CustomCustomControl 보려면 (형식)에 대 한 ScriptBlock 요소](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md) 컨트롤에서 해당 값이 표시 하는 스크립트를 지정 합니다. 이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.

[GroupBy (형식)에 대 한 ExpressionBinding에 대 한 ScriptBlock 요소](./scriptblock-element-for-expressionbinding-for-groupby-format.md) 컨트롤에서 해당 값이 표시 하는 스크립트를 지정 합니다. 이 요소는 새 개체 그룹에 표시 되는 방식을 정의 하는 경우에 사용 됩니다.

[GroupBy (형식)에 대 한 ScriptBlock 요소](./scriptblock-element-for-groupby-format.md) 해당 값이 변경 될 때마다 새 그룹을 시작 하는 스크립트를 지정 합니다.

[구성 (형식)에 대 한 컨트롤에 대 한 ItemSelectionCondition ScriptBlock 요소](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) 조건을 트리거하는 스크립트를 지정 합니다. 이 스크립트를 계산할 때 `true`조건이 충족 되 고 컨트롤이 사용 합니다. 이 요소는 서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 정의할 때 사용 됩니다.

[뷰 (형식)에 대 한 컨트롤에 대 한 ItemSelectionCondition ScriptBlock 요소](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md) 조건을 트리거하는 스크립트를 지정 합니다. 이 스크립트를 계산할 때 `true`조건이 충족 되 고 컨트롤이 사용 합니다. 이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의할 때 사용 됩니다.

[ScriptBlock 요소 CustomControl 보려면 (형식)에 대 한 ItemSelectionCondition](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) 조건을 트리거하는 스크립트를 지정 합니다. 이 스크립트를 계산할 때 `true`조건이 충족 되 고 컨트롤이 사용 합니다. 이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.

[GroupBy (형식)에 대 한 ItemSelectionCondition ScriptBlock 요소](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md) 조건을 트리거하는 스크립트를 지정 합니다. 이 스크립트를 계산할 때 `true`조건이 충족 되 고 컨트롤이 사용 합니다. 이 요소는 새 개체 그룹에 표시 되는 방식을 정의 하는 경우에 사용 됩니다.

[ScriptBlock 요소 ListControl (형식)에 대 한 ItemSelectionCondition](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) 조건을 트리거하는 스크립트를 지정 합니다. 이 스크립트를 계산할 때 `true`조건이 충족 되 고 목록 항목이 사용 됩니다. 이 요소는 목록 뷰를 정의할 때 사용 됩니다.

[ListItem (형식)에 대 한 ScriptBlock 요소](./scriptblock-element-for-listitem-for-listcontrol-format.md) 값인 목록의 행에 표시 되는 스크립트를 지정 합니다.

[구성 (형식)에 대 한 컨트롤에 대 한 SelectionCondition ScriptBlock 요소](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md) 조건을 트리거하는 스크립트를 지정 합니다. 이 스크립트를 계산할 때 `true`조건이 충족 되 고 정의가 사용 됩니다. 이 요소는 서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 정의할 때 사용 됩니다.

[뷰 (형식)에 대 한 컨트롤에 대 한 SelectionCondition ScriptBlock 요소](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md) 조건을 트리거하는 스크립트를 지정 합니다. 이 스크립트를 계산할 때 `true`조건이 충족 되 고 정의가 사용 됩니다. 이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의할 때 사용 됩니다.

[ScriptBlock 요소 CustomControl 보려면 (형식)에 대 한 SelectionCondition](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md) 조건을 트리거하는 스크립트를 지정 합니다. 이 스크립트를 계산할 때 `true`조건이 충족 되 고 정의가 사용 됩니다. 이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.

[ScriptBlock 요소 EntrySelectedBy EnumerableExpansion (형식)에 대 한에 대 한 SelectionCondition](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md) 조건을 트리거하는 스크립트를 지정 합니다.

[GroupBy (형식)에 대 한 SelectionCondition ScriptBlock 요소](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format.md) 조건을 트리거하는 스크립트를 지정 합니다. 이 스크립트를 계산할 때 `true`조건이 충족 되 고 정의가 사용 됩니다. 이 요소는 새 개체 그룹에 표시 되는 방식을 정의 하는 경우에 사용 됩니다.

[ScriptBlock 요소 EntrySelectedBy ListEntry (형식)에 대 한에 대 한 SelectionCondition](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md) 조건을 트리거하는 스크립트를 지정 합니다. 이 스크립트를 계산할 때 `true`조건이 충족 되 고 목록 항목이 사용 됩니다.

[ScriptBlock 요소 EntrySelectedBy TableRowEntry (형식)에 대 한에 대 한 SelectionCondition](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md) 조건을 트리거하는 스크립트 블록을 지정 합니다. 이 스크립트를 계산할 때 `true`조건이 충족 되 고 테이블 항목이 사용 됩니다.

[ScriptBlock 요소 EntrySelectedBy WideEntry (형식)에 대 한에 대 한 SelectionCondition](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md) 조건을 트리거하는 스크립트를 지정 합니다. 이 스크립트를 계산할 때 `true`조건이 충족 되 고 와이드 항목 정의가 사용 됩니다.

[TableColumnItem (형식)에 대 한 ScriptBlock 요소](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) 값인 행의 열에 표시 되는 스크립트를 지정 합니다.

[WideItem (형식)에 대 한 ScriptBlock 요소](./scriptblock-element-for-wideitem-for-widecontrol-format.md) 값인 와이드 보기에 표시 되는 스크립트를 지정 합니다.

[CustomEntry 구성 (형식)에 대 한 EntrySelectedBy SelectionCondition 요소](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md) 사용할 일반적인 컨트롤 정의에 있어야 하는 조건을 정의 합니다. 이 요소는 서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 정의할 때 사용 됩니다.

[뷰 (형식)에 대 한 컨트롤에 대 한 EntrySelectedBy SelectionCondition 요소](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md) 컨트롤 정의 사용할 수 있어야 하는 조건을 정의 합니다. 이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의할 때 사용 됩니다.

[CustomControl 보려면 (형식)에 대 한 EntrySelectedBy SelectionCondition 요소](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md) 컨트롤 정의 사용할 수 있어야 하는 조건을 정의 합니다. 이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.

[EnumerableExpansion (형식)에 대 한 EntrySelectedBy SelectionCondition 요소](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md) 이 정의의 컬렉션 개체를 확장 하려면 있어야 하는 조건을 정의 합니다.

[GroupBy (형식)에 대 한 EntrySelectedBy SelectionCondition 요소](./selectioncondition-element-for-entryselectedby-for-groupby-format.md) 컨트롤 정의 사용할 수 있어야 하는 조건을 정의 합니다. 이 요소는 새 개체 그룹에 표시 되는 방식을 정의 하는 경우에 사용 됩니다.

[ListEntry (형식)에 대 한 EntrySelectedBy SelectionCondition 요소](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) 목록 보기의이 정의 사용 하도록 있어야 하는 조건을 정의 합니다. 목록 정의 대해 지정할 수 있는 선택 조건 수 제한은 없습니다.

[TableRowEntry (형식)에 대 한 EntrySelectedBy SelectionCondition 요소](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md) 테이블 보기의이 정의에 사용할 있어야 하는 조건을 정의 합니다. 테이블 정의에 지정 될 수 있는 선택 조건 수 제한은 없습니다.

[WideEntry (형식)에 대 한 EntrySelectedBy SelectionCondition 요소](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) 이 정의를 사용할 수 있어야 하는 조건을 정의 합니다. 수가 와이드 항목 정의 대해 지정할 수 있는 선택 조건 제한은 없습니다.

[SelectionSet 요소 (형식)](./selectionset-element-format.md) 집합의 이름으로 참조할 수 있는.NET 개체 집합을 정의 합니다.

[구성 (형식)에 대 한 컨트롤에 대 한 EntrySelectedBy SelectionSetName 요소](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md) 컨트롤의이 정의 사용 하는.NET 형식의 집합을 지정 합니다. 이 요소는 서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 정의할 때 사용 됩니다.

[뷰 (형식)에 대 한 컨트롤에 대 한 EntrySelectedBy SelectionSetName 요소](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md) 컨트롤의이 정의 사용 하는.NET 형식의 집합을 지정 합니다. 이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의할 때 사용 됩니다.

[CustomEntry (형식)에 대 한 EntrySelectedBy SelectionSetName 요소](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md) 목록 항목에 대 한.NET 개체 집합을 지정 합니다. 항목에 대해 지정할 수 있는 선택 항목 집합 수에 제한은 없습니다.

[EnumerableExpansion (형식)에 대 한 EntrySelectedBy SelectionSetName 요소](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md) 이 정의 의해 확장 되는.NET 형식의 집합을 지정 합니다.

[GroupBy (형식)에 대 한 EntrySelectedBy SelectionSetName 요소](./selectionsetname-element-for-entryselectedby-for-groupby-format.md) 목록 항목에 대 한.NET 개체 집합을 지정 합니다. 항목에 대해 지정할 수 있는 선택 항목 집합 수에 제한은 없습니다. 이 요소는 새 개체 그룹에 표시 되는 방식을 정의 하는 경우에 사용 됩니다.

[ListEntry (형식)에 대 한 EntrySelectedBy SelectionSetName 요소](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) 목록 항목에 대 한.NET 개체 집합을 지정 합니다. 항목에 대해 지정할 수 있는 선택 항목 집합 수에 제한은 없습니다.

[TableRowEntry (형식)에 대 한 EntrySelectedBy SelectionSetName 요소](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md) 집합이.NET 형식을 사용 하 여 테이블 보기의이 항목을 지정 합니다. 항목에 대해 지정할 수 있는 선택 항목 집합 수에 제한은 없습니다.

[WideEntry (형식)에 대 한 EntrySelectedBy SelectionSetName 요소](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md) 정의 대 한.NET 개체 집합을 지정 합니다. 정의는 이러한 개체 중 하나가 표시 될 때마다 사용 됩니다.

[구성 (형식)에 대 한 컨트롤에 대 한 SelectionCondition SelectionSetName 요소](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md) 트리거 조건이 있는.NET 형식의 집합을 지정 합니다. 이 형식의 값이 있는 경우 조건이 충족 될 하 고 개체는이 컨트롤을 사용 하 여 표시 됩니다. 이 요소는 서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 정의할 때 사용 됩니다.

[뷰 (형식)에 대 한 컨트롤에 대 한 SelectionCondition SelectionSetName 요소](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md) 트리거 조건이 있는.NET 형식의 집합을 지정 합니다. 있는 경우이 집합의 형식 중 하나는 조건이 충족 되 고이 컨트롤을 사용 하 여 개체가 표시 됩니다. 이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의할 때 사용 됩니다.

[뷰 (형식)에 대 한 CustomEntry EntrySelectedBy 요소](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md) 트리거 조건이 있는.NET 형식의 집합을 지정 합니다. 있는 경우이 집합의 형식 중 하나는 조건이 충족 되 고이 컨트롤을 사용 하 여 개체가 표시 됩니다. 이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.

[EntrySelectedBy EnumerableExpansion (형식)에 대 한에 대 한 SelectionCondition SelectionSetName 요소](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md) 트리거 조건이 있는.NET 형식의 집합을 지정 합니다. 이 형식의 값이 있는 경우에 조건이 충족 됩니다.

[GroupBy (형식)에 대 한 SelectionCondition SelectionSetName 요소](./selectionsetname-element-for-selectioncondition-for-groupby-format.md) 트리거 조건이 있는.NET 형식의 집합을 지정 합니다. 이 형식의 값이 있는 경우 조건이 충족 될 하 고 개체는이 컨트롤을 사용 하 여 표시 됩니다. 이 요소는 새 개체 그룹에 표시 되는 방식을 정의 하는 경우에 사용 됩니다.

[EntrySelectedBy ListEntry (형식)에 대 한에 대 한 SelectionCondition SelectionSetName 요소](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md) 트리거 조건이 있는.NET 형식의 집합을 지정 합니다. 있는 경우이 집합의 형식 중 하나는 조건이 충족 하 고 개체 목록 보기의이 정의 사용 하 여 표시 됩니다.

[EntrySelectedBy TableRowEntry (형식)에 대 한에 대 한 SelectionCondition SelectionSetName 요소](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md) 트리거 조건이 있는.NET 형식의 집합을 지정 합니다. 있는 경우이 집합의 형식 중 하나는 조건이 충족 하 고 개체 테이블 보기의이 정의 사용 하 여 표시 됩니다.

[EntrySelectedBy WideEntry (형식)에 대 한에 대 한 SelectionCondition SelectionSetName 요소](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md) 트리거 조건이 있는.NET 형식의 집합을 지정 합니다. 있는 경우이 집합의 형식 중 하나는 조건이 충족 되 면 하 고 개체의 넓은 보기가이 정의 사용 하 여 표시 됩니다.

[ViewSelectedBy (형식)에 대 한 SelectionSetName 요소](./selectionsetname-element-for-viewselectedby-format.md) 뷰에서 표시 되는.NET 개체 집합을 지정 합니다.

[SelectionSets 요소 (형식)](./selectionsets-element-format.md) 개별 형식 보기에서 사용할 수 있는.NET 개체의 집합을 정의 합니다.

[ShowError 요소 (형식)](./showerror-element-format.md) 데이터 부분을 표시 하는 동안 오류가 발생 하면 전체 오류 레코드 표시 되도록 지정 합니다.

[TableControl (형식)에 대 한 TableHeaders TableColumnHeader 요소](./tablecolumnheader-element-format.md) 레이블, 열 너비와 테이블의 열 레이블 맞춤을 정의 합니다.

[TableColumnItem 요소 (형식)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) 속성 또는 값은 행의 열에 표시 된 스크립트를 정의 합니다.

[TableColumnItems 요소 (형식)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) 속성 또는 행의 값을 표시 하는 스크립트를 정의 합니다.

[TableControl 요소 (형식)](./tablecontrol-element-format.md) 보려면 테이블 형식을 정의 합니다.

[TableHeaders 요소 (형식)](./tableheaders-element-format.md) 테이블의 열에 대 한 헤더를 정의 합니다.

[TableRowEntries 요소 (형식)](./tablerowentries-element-for-tablecontrol-format.md) 테이블의 행을 정의 합니다.

[TableRowEntry 요소 (형식)](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md) 테이블의 행에 표시 되는 데이터를 정의 합니다.

[텍스트 요소 구성 (형식)에 대 한 컨트롤에 대 한 CustomItem](./text-element-for-customitem-for-controls-for-configuration-format.md) 지정 텍스트 레이블과 같은 컨트롤에 의해 표시 되는 데이터에 추가 되는 괄호를 사용 하는 데이터 및 데이터를 들여쓸 공간을 묶습니다. 이 요소는 서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 정의할 때 사용 됩니다.

[텍스트 요소 (형식) 보기에 대 한 컨트롤에 대 한 CustomItem](./text-element-for-customitem-for-controls-for-view-format.md) 지정 텍스트 레이블과 같은 컨트롤에 의해 표시 되는 데이터에 추가 되는 괄호를 사용 하는 데이터 및 데이터를 들여쓸 공간을 묶습니다. 이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의할 때 사용 됩니다.

[CustomItem (형식)에 대 한 텍스트 요소](./text-element-for-customitem-for-customview-for-view-format.md) 지정 텍스트 레이블과 같은 컨트롤에 의해 표시 되는 데이터에 추가 되는 괄호를 사용 하는 데이터 및 데이터를 들여쓸 공간을 묶습니다. 이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.

[GroupBy (형식)에 대 한 CustomItem에 대 한 텍스트 요소](./text-element-for-customitem-for-groupby-format.md) 지정 텍스트 레이블과 같은 컨트롤에 의해 표시 되는 데이터에 추가 되는 괄호를 사용 하는 데이터 및 데이터를 들여쓸 공간을 묶습니다. 이 요소는 새 개체 그룹에 표시 되는 방식을 정의 하는 경우에 사용 됩니다.

[구성 (형식)에 대 한 컨트롤에 대 한 EntrySelectedBy TypeName 요소](./typename-element-for-entryselectedby-for-controls-for-configuration-format.md) 컨트롤의이 정의 사용 하는.NET 유형을 지정 합니다. 이 요소는 서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 정의할 때 사용 됩니다.

[TypeName 요소 (형식) 보기에 대 한 컨트롤에 대 한 EntrySelectedBy](./typename-element-for-entryselectedby-for-controls-for-view-format.md) 컨트롤의이 정의 사용 하는.NET 유형을 지정 합니다. 이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의할 때 사용 됩니다.

[EntrySelectedBy CustomEntry 보려면 (형식)에 대 한 TypeName 요소](./typename-element-for-entryselectedby-for-customentry-for-view-format.md) 이 사용자 지정 컨트롤 뷰의이 정의 사용 하는.NET 유형을 지정 합니다. 형식 정의 대해 지정할 수 있는 수에 제한은 없습니다.

[EntrySelectedBy EnumerableExpansion (형식)에 대 한 TypeName 요소](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md) 이 정의 의해 확장 되는.NET 유형을 지정 합니다. 이 요소는 기본 설정을 정의 하는 경우에 사용 됩니다.

[GroupBy (형식)에 대 한 EntrySelectedBy TypeName 요소](./typename-element-for-entryselectedby-for-groupby-format.md) 이 정의 사용자 지정 컨트롤을 사용 하는.NET 유형을 지정 합니다. 이 요소는 새 개체 그룹에 표시 되는 방식을 정의 하는 경우에 사용 됩니다.

[EntrySelectedBy ListControl (형식)에 대 한 TypeName 요소](./typename-element-for-entryselectedby-for-listcontrol-format.md) 목록 보기의이 항목을 사용 하는.NET 유형을 지정 합니다. 목록 항목에 대해 지정할 수 있는 형식의 수 제한은 없습니다.

[EntrySelectedBy TableRowEntry (형식)에 대 한 TypeName 요소](./typename-element-for-entryselectedby-for-tablecontrol-format.md) 테이블 보기의이 항목을 사용 하는.NET 유형을 지정 합니다. 테이블 항목에 대해 지정할 수 있는 형식의 수 제한은 없습니다.

[EntrySelectedBy WideEntry (형식)에 대 한 TypeName 요소](./typename-element-for-entryselectedby-for-wideentry-format.md) 정의 대 한.NET 형식을 지정 합니다. 이 개체에 표시 될 때마다 정이 됩니다.

[구성 (형식)에 대 한 컨트롤에 대 한 SelectionCondition TypeName 요소](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md) 조건을 트리거하는.NET 유형을 지정 합니다. 이 요소는 서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 정의할 때 사용 됩니다.

[TypeName 요소 (형식) 보기에 대 한 컨트롤에 대 한 SelectionCondition](./typename-element-for-selectioncondition-for-controls-for-view-format.md) 조건을 트리거하는.NET 유형을 지정 합니다. 이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의할 때 사용 됩니다.

[SelectionCondition CustomControl 보려면 (형식)에 대 한 TypeName 요소](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md) 조건을 트리거하는.NET 유형을 지정 합니다. 이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.

[SelectionCondition EntrySelectedBy EnumerableExpansion (형식)에 대 한에 대 한 TypeName 요소](./typename-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md) 조건을 트리거하는.NET 유형을 지정 합니다.

[GroupBy (형식)에 대 한 SelectionCondition TypeName 요소](./typename-element-for-selectioncondition-for-groupby-format.md) 조건을 트리거하는.NET 유형을 지정 합니다. 이 요소는 새 개체 그룹에 표시 되는 방식을 정의 하는 경우에 사용 됩니다.

[SelectionCondition EntrySelectedBy ListControl (형식)에 대 한에 대 한 TypeName 요소](./typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md) 조건을 트리거하는.NET 유형을 지정 합니다. 이 형식이 있는 경우에 목록 항목이 사용 됩니다.

[SelectionCondition EntrySelectedBy TableRowEntry (형식)에 대 한에 대 한 TypeName 요소](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md) 조건을 트리거하는.NET 유형을 지정 합니다. 이 형식은 존재 하는 경우 조건이 충족 되 고 테이블 행 사용 됩니다.

[SelectionCondition EntrySelectedBy WideEntry (형식)에 대 한에 대 한 TypeName 요소](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md) 조건을 트리거하는.NET 유형을 지정 합니다. 이 형식은 존재 하는 경우 정이 됩니다.

[형식 (형식)에 대 한 TypeName 요소](./typename-element-for-types-format.md) 선택 집합에 속한 개체의.NET 유형을 지정 합니다.

[ViewSelectedBy (형식)에 대 한 TypeName 요소](./typename-element-for-viewselectedby-format.md) 보기에 표시 되는.NET 개체를 지정 합니다.

[요소 (형식) 형식은](./types-element-for-selectionset-format.md) 집합 선택 영역에 있는.NET 개체를 정의 합니다.

[요소 (형식)를 보려면](./view-element-format.md) 하나 이상의.NET 개체를 표시 하는 데 사용 되는 뷰를 정의 합니다.

[ViewDefinitions 요소 (형식)](./viewdefinitions-element-format.md) 개체를 표시 하는 데 사용 하는 뷰를 정의 합니다.

[ViewSelectedBy 요소 (형식)](./viewselectedby-element-format.md) 뷰에서 표시 되는.NET 개체를 정의 합니다.

[WideControl 요소 (형식)](./widecontrol-element-format.md) 와이드 (단일 값) 목록 보기에 대 한 형식을 정의 합니다. 이 보기에는 단일 속성 값 또는 각 개체에 대 한 스크립트 값을 표시합니다.

[WideEntries 요소 (형식)](./wideentries-element-for-widecontrol-format.md) 넓은 보기의 정의 제공 합니다. 와이드 보기인 경우 하나 이상의 정의 지정 해야 합니다.

[WideEntry 요소 (형식)](./wideentry-element-for-widecontrol-format.md) 넓은 보기의 정의 제공 합니다.

[WideItem 요소 (형식)](./wideitem-element-for-widecontrol-format.md) 속성 또는 해당 값이 표시 되는 스크립트를 정의 합니다.

[Width 요소 (형식)](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) 의 너비 (문자 단위) 열을 정의 합니다.

[요소 (형식)를 래핑할](./wrap-element-for-tablerowentry-for-tablecontrl-format.md) 열 너비를 초과 하는 텍스트가 다음 줄에 표시 되도록 지정 합니다.

[WrapTables 요소 (형식)](./wraptables-element-format.md) 데이터 표 셀에 다음 줄으로 이동 되 면 데이터 열의 너비 보다 길이 지정 합니다.

## <a name="see-also"></a>참고 항목

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
