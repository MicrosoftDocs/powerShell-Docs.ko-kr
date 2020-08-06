---
title: GroupBy (형식)에 대 한 EntrySelectedBy의 TypeName 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e62762cf142bd2d20b21ad8f4249285bd3679280
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780270"
---
# <a name="typename-element-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="98c8b-102">GroupBy의 EntrySelectedBy에 대한 TypeName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="98c8b-102">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="98c8b-103">사용자 지정 컨트롤의이 정의를 사용 하는 .NET 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="98c8b-103">Specifies a .NET type that uses this definition of the custom control.</span></span> <span data-ttu-id="98c8b-104">이 요소는 새 개체 그룹이 표시 되는 방법을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="98c8b-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="98c8b-105">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (Format)의 groupby 요소 (format) CustomControl 요소에 대 한 CustomControl의 경우 CustomControl에 대 한 customentries 요소에 대 한 customentries 요소에 대 한 Customentries 요소에 대 한 Customentries for groupby (형식)에 대 한 CustomEntries 요소에 대 한 참조</span><span class="sxs-lookup"><span data-stu-id="98c8b-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="98c8b-106">구문</span><span class="sxs-lookup"><span data-stu-id="98c8b-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="98c8b-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="98c8b-107">Attributes and Elements</span></span>

<span data-ttu-id="98c8b-108">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `TypeName` .</span><span class="sxs-lookup"><span data-stu-id="98c8b-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="98c8b-109">특성</span><span class="sxs-lookup"><span data-stu-id="98c8b-109">Attributes</span></span>

<span data-ttu-id="98c8b-110">없음</span><span class="sxs-lookup"><span data-stu-id="98c8b-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="98c8b-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="98c8b-111">Child Elements</span></span>

<span data-ttu-id="98c8b-112">없음</span><span class="sxs-lookup"><span data-stu-id="98c8b-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="98c8b-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="98c8b-113">Parent Elements</span></span>

|<span data-ttu-id="98c8b-114">요소</span><span class="sxs-lookup"><span data-stu-id="98c8b-114">Element</span></span>|<span data-ttu-id="98c8b-115">설명</span><span class="sxs-lookup"><span data-stu-id="98c8b-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="98c8b-116">GroupBy의 CustomEntry에 대한 EntrySelectedBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="98c8b-116">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="98c8b-117">이 컨트롤 정의를 사용 하는 .NET 형식 또는이 정의를 사용 하기 위해 존재 해야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="98c8b-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="98c8b-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="98c8b-118">Text Value</span></span>

<span data-ttu-id="98c8b-119">.NET 형식의 정규화 된 이름 (예:)을 지정 합니다 `System.IO.DirectoryInfo` .</span><span class="sxs-lookup"><span data-stu-id="98c8b-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="98c8b-120">설명</span><span class="sxs-lookup"><span data-stu-id="98c8b-120">Remarks</span></span>

<span data-ttu-id="98c8b-121">각 컨트롤 정의에는 하나 이상의 형식 이름, 선택 집합 또는 선택 조건이 정의 되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="98c8b-121">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="98c8b-122">사용자 지정 컨트롤 뷰의 구성 요소에 대 한 자세한 내용은 [사용자 지정 컨트롤 만들기](./creating-custom-controls.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="98c8b-122">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="98c8b-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="98c8b-123">See Also</span></span>

[<span data-ttu-id="98c8b-124">사용자 지정 컨트롤 만들기</span><span class="sxs-lookup"><span data-stu-id="98c8b-124">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="98c8b-125">GroupBy의 CustomEntry에 대한 EntrySelectedBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="98c8b-125">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="98c8b-126">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="98c8b-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
