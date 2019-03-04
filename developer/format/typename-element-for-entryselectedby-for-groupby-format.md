---
title: GroupBy (형식)에 대 한 EntrySelectedBy TypeName 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b8b6739b-770c-432a-95ab-551c7507c51f
caps.latest.revision: 6
ms.openlocfilehash: 3b5ce60d3a0d76988af48f49445a5478a415d498
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861669"
---
# <a name="typename-element-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="b205e-102">GroupBy의 EntrySelectedBy에 대한 TypeName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="b205e-102">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="b205e-103">사용자 지정 컨트롤의이 정의 사용 하는.NET 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b205e-103">Specifies a .NET type that uses this definition of the custom control.</span></span> <span data-ttu-id="b205e-104">이 요소는 새 개체 그룹에 표시 되는 방식을 정의 하는 경우에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b205e-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="b205e-105">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) GroupBy 요소 CustomControl GroupBy (형식) CustomEntry 요소에 대 한 GroupBy (형식) CustomEntries 요소에 대 한 보기 (형식) CustomControl 요소에 대 한 CustomControl CustomEntry EntrySelectedBy GroupBy (형식)에 대 한 TypeName 요소 GroupBy (형식)에 대 한 GroupBy (형식) EntrySelectedBy 요소에</span><span class="sxs-lookup"><span data-stu-id="b205e-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b205e-106">구문</span><span class="sxs-lookup"><span data-stu-id="b205e-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b205e-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="b205e-107">Attributes and Elements</span></span>

<span data-ttu-id="b205e-108">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `TypeName` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="b205e-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b205e-109">특성</span><span class="sxs-lookup"><span data-stu-id="b205e-109">Attributes</span></span>

<span data-ttu-id="b205e-110">없음</span><span class="sxs-lookup"><span data-stu-id="b205e-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b205e-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="b205e-111">Child Elements</span></span>

<span data-ttu-id="b205e-112">없음</span><span class="sxs-lookup"><span data-stu-id="b205e-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b205e-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="b205e-113">Parent Elements</span></span>

|<span data-ttu-id="b205e-114">요소</span><span class="sxs-lookup"><span data-stu-id="b205e-114">Element</span></span>|<span data-ttu-id="b205e-115">설명</span><span class="sxs-lookup"><span data-stu-id="b205e-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b205e-116">GroupBy (형식)에 대 한 CustomEntry EntrySelectedBy 요소</span><span class="sxs-lookup"><span data-stu-id="b205e-116">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="b205e-117">이 컨트롤 정의 또는이 정의를 사용할 수 있어야 하는 조건을 사용 하는.NET 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="b205e-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b205e-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="b205e-118">Text Value</span></span>

<span data-ttu-id="b205e-119">와 같이.NET 형식의 정규화 된 이름을 지정 `System.IO.DirectoryInfo`합니다.</span><span class="sxs-lookup"><span data-stu-id="b205e-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="b205e-120">설명</span><span class="sxs-lookup"><span data-stu-id="b205e-120">Remarks</span></span>

<span data-ttu-id="b205e-121">각 컨트롤 정의 형식 이름, 선택 집합 또는 정의 된 선택 조건을 하나 이상 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b205e-121">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="b205e-122">사용자 지정 컨트롤 보기의 구성 요소에 대 한 자세한 내용은 참조 [사용자 지정 컨트롤 만들기](./creating-custom-controls.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="b205e-122">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b205e-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b205e-123">See Also</span></span>

[<span data-ttu-id="b205e-124">사용자 지정 컨트롤 만들기</span><span class="sxs-lookup"><span data-stu-id="b205e-124">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="b205e-125">GroupBy (형식)에 대 한 CustomEntry EntrySelectedBy 요소</span><span class="sxs-lookup"><span data-stu-id="b205e-125">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="b205e-126">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="b205e-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
