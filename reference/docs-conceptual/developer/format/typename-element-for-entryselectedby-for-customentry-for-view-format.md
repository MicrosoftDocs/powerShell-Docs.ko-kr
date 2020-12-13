---
ms.date: 09/13/2016
ms.topic: reference
title: View에 대한 CustomEntry의 EntrySelectedBy에 대한 TypeName 요소(형식)
description: View에 대한 CustomEntry의 EntrySelectedBy에 대한 TypeName 요소(형식)
ms.openlocfilehash: 72bb88bccc2bbd62f7ed160b820cf9169cb69341
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645737"
---
# <a name="typename-element-for-entryselectedby-for-customentry-for-view-format"></a><span data-ttu-id="92e73-103">View에 대한 CustomEntry의 EntrySelectedBy에 대한 TypeName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="92e73-103">TypeName Element for EntrySelectedBy for CustomEntry for View (Format)</span></span>

<span data-ttu-id="92e73-104">사용자 지정 컨트롤 뷰의이 정의를 사용 하는 .NET 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="92e73-104">Specifies a .NET type that uses this definition of the custom control view.</span></span> <span data-ttu-id="92e73-105">정의에 대해 지정할 수 있는 형식 수에는 제한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="92e73-105">There is no limit to the number of types that can be specified for a definition.</span></span>

<span data-ttu-id="92e73-106">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) CustomControl Element (format) customentries 요소에 대 한 view (format) customentries 요소에 대 한 CustomEntries 요소에 대 한 customentries 요소에 대 한 customentries 요소에 대 한 customentries 요소</span><span class="sxs-lookup"><span data-stu-id="92e73-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format) TypeName Element for EntrySelectedBy for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="92e73-107">구문</span><span class="sxs-lookup"><span data-stu-id="92e73-107">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="92e73-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="92e73-108">Attributes and Elements</span></span>

<span data-ttu-id="92e73-109">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `TypeName` .</span><span class="sxs-lookup"><span data-stu-id="92e73-109">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="92e73-110">특성</span><span class="sxs-lookup"><span data-stu-id="92e73-110">Attributes</span></span>

<span data-ttu-id="92e73-111">없음</span><span class="sxs-lookup"><span data-stu-id="92e73-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="92e73-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="92e73-112">Child Elements</span></span>

<span data-ttu-id="92e73-113">없음</span><span class="sxs-lookup"><span data-stu-id="92e73-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="92e73-114">부모 요소</span><span class="sxs-lookup"><span data-stu-id="92e73-114">Parent Elements</span></span>

|<span data-ttu-id="92e73-115">요소</span><span class="sxs-lookup"><span data-stu-id="92e73-115">Element</span></span>|<span data-ttu-id="92e73-116">설명</span><span class="sxs-lookup"><span data-stu-id="92e73-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="92e73-117">View의 CustomEntry에 대 한 EntrySelectedBy 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="92e73-117">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="92e73-118">이 사용자 지정 컨트롤 뷰 정의를 사용 하는 .NET 형식 또는이 정의를 사용 하기 위해 존재 해야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="92e73-118">Defines the .NET types that use this custom control view definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="92e73-119">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="92e73-119">Text Value</span></span>

<span data-ttu-id="92e73-120">.NET 형식의 정규화 된 이름 (예:)을 지정 합니다 `System.IO.DirectoryInfo` .</span><span class="sxs-lookup"><span data-stu-id="92e73-120">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="92e73-121">설명</span><span class="sxs-lookup"><span data-stu-id="92e73-121">Remarks</span></span>

<span data-ttu-id="92e73-122">각 사용자 지정 컨트롤 뷰 정의에는 하나 이상의 유형 이름, 선택 집합 또는 선택 조건이 정의 되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="92e73-122">Each custom control view definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="92e73-123">사용자 지정 컨트롤 뷰의 구성 요소에 대 한 자세한 내용은 [사용자 지정 컨트롤 만들기](./creating-custom-controls.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="92e73-123">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="92e73-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="92e73-124">See Also</span></span>

[<span data-ttu-id="92e73-125">사용자 지정 컨트롤 만들기</span><span class="sxs-lookup"><span data-stu-id="92e73-125">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="92e73-126">View의 CustomEntry에 대 한 EntrySelectedBy 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="92e73-126">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="92e73-127">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="92e73-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
