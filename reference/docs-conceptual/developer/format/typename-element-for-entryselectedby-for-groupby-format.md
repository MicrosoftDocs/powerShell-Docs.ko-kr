---
title: GroupBy (형식)에 대 한 EntrySelectedBy의 TypeName 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b8b6739b-770c-432a-95ab-551c7507c51f
caps.latest.revision: 6
ms.openlocfilehash: 3b5ce60d3a0d76988af48f49445a5478a415d498
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361672"
---
# <a name="typename-element-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="226e3-102">GroupBy의 EntrySelectedBy에 대한 TypeName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="226e3-102">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="226e3-103">사용자 지정 컨트롤의이 정의를 사용 하는 .NET 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="226e3-103">Specifies a .NET type that uses this definition of the custom control.</span></span> <span data-ttu-id="226e3-104">이 요소는 새 개체 그룹이 표시 되는 방법을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="226e3-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="226e3-105">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format)의 groupby 요소 (groupby (format) CustomEntries 요소에 대 한 CustomControl 요소에 대 한 groupby (format) Customentries 요소에 대 한 CustomControl Groupby (format) EntrySelectedBy 요소에 대 한 CustomControl 요소에 대 한 CustomEntry for groupby (형식)의 경우 EntrySelectedBy</span><span class="sxs-lookup"><span data-stu-id="226e3-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="226e3-106">구문</span><span class="sxs-lookup"><span data-stu-id="226e3-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="226e3-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="226e3-107">Attributes and Elements</span></span>

<span data-ttu-id="226e3-108">다음 섹션에서는 `TypeName` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="226e3-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="226e3-109">특성</span><span class="sxs-lookup"><span data-stu-id="226e3-109">Attributes</span></span>

<span data-ttu-id="226e3-110">없음</span><span class="sxs-lookup"><span data-stu-id="226e3-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="226e3-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="226e3-111">Child Elements</span></span>

<span data-ttu-id="226e3-112">없음</span><span class="sxs-lookup"><span data-stu-id="226e3-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="226e3-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="226e3-113">Parent Elements</span></span>

|<span data-ttu-id="226e3-114">요소</span><span class="sxs-lookup"><span data-stu-id="226e3-114">Element</span></span>|<span data-ttu-id="226e3-115">설명</span><span class="sxs-lookup"><span data-stu-id="226e3-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="226e3-116">GroupBy (형식)에 대 한 CustomEntry의 EntrySelectedBy 요소</span><span class="sxs-lookup"><span data-stu-id="226e3-116">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="226e3-117">이 컨트롤 정의를 사용 하는 .NET 형식 또는이 정의를 사용 하기 위해 존재 해야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="226e3-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="226e3-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="226e3-118">Text Value</span></span>

<span data-ttu-id="226e3-119">.NET 형식의 정규화 된 이름 (예: `System.IO.DirectoryInfo`)을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="226e3-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="226e3-120">설명</span><span class="sxs-lookup"><span data-stu-id="226e3-120">Remarks</span></span>

<span data-ttu-id="226e3-121">각 컨트롤 정의에는 하나 이상의 형식 이름, 선택 집합 또는 선택 조건이 정의 되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="226e3-121">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="226e3-122">사용자 지정 컨트롤 뷰의 구성 요소에 대 한 자세한 내용은 [사용자 지정 컨트롤 만들기](./creating-custom-controls.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="226e3-122">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="226e3-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="226e3-123">See Also</span></span>

[<span data-ttu-id="226e3-124">사용자 지정 컨트롤 만들기</span><span class="sxs-lookup"><span data-stu-id="226e3-124">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="226e3-125">GroupBy (형식)에 대 한 CustomEntry의 EntrySelectedBy 요소</span><span class="sxs-lookup"><span data-stu-id="226e3-125">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="226e3-126">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="226e3-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
