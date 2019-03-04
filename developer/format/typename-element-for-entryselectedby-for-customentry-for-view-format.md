---
title: EntrySelectedBy CustomEntry 보려면 (형식)에 대 한 TypeName 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76548af7-05bd-4d12-bf71-6fb69c434ef2
caps.latest.revision: 10
ms.openlocfilehash: c3dd761cd9b6c468d4833ea35b897ba5d425f598
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858839"
---
# <a name="typename-element-for-entryselectedby-for-customentry-for-view-format"></a><span data-ttu-id="31f06-102">View에 대한 CustomEntry의 EntrySelectedBy에 대한 TypeName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="31f06-102">TypeName Element for EntrySelectedBy for CustomEntry for View (Format)</span></span>

<span data-ttu-id="31f06-103">이 사용자 지정 컨트롤 뷰의이 정의 사용 하는.NET 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="31f06-103">Specifies a .NET type that uses this definition of the custom control view.</span></span> <span data-ttu-id="31f06-104">형식 정의 대해 지정할 수 있는 수에 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="31f06-104">There is no limit to the number of types that can be specified for a definition.</span></span>

<span data-ttu-id="31f06-105">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) CustomControl 요소 (형식) CustomEntries 요소 CustomControl CustomEntries EntrySelectedBy 보기 (형식)에 대 한 보기 (형식) CustomEntry 요소에 대 한 CustomEntry EntrySelectedBy CustomEntry 보려면 (형식)에 대 한 보기 (형식) TypeName 요소에 대 한 요소</span><span class="sxs-lookup"><span data-stu-id="31f06-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format) TypeName Element for EntrySelectedBy for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="31f06-106">구문</span><span class="sxs-lookup"><span data-stu-id="31f06-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="31f06-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="31f06-107">Attributes and Elements</span></span>

<span data-ttu-id="31f06-108">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `TypeName` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="31f06-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="31f06-109">특성</span><span class="sxs-lookup"><span data-stu-id="31f06-109">Attributes</span></span>

<span data-ttu-id="31f06-110">없음</span><span class="sxs-lookup"><span data-stu-id="31f06-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="31f06-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="31f06-111">Child Elements</span></span>

<span data-ttu-id="31f06-112">없음</span><span class="sxs-lookup"><span data-stu-id="31f06-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="31f06-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="31f06-113">Parent Elements</span></span>

|<span data-ttu-id="31f06-114">요소</span><span class="sxs-lookup"><span data-stu-id="31f06-114">Element</span></span>|<span data-ttu-id="31f06-115">설명</span><span class="sxs-lookup"><span data-stu-id="31f06-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="31f06-116">뷰 (형식)에 대 한 CustomEntry EntrySelectedBy 요소</span><span class="sxs-lookup"><span data-stu-id="31f06-116">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="31f06-117">이 사용자 지정 컨트롤 뷰 정의 사용 하는.NET 형식 또는이 정의를 사용할 수 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="31f06-117">Defines the .NET types that use this custom control view definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="31f06-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="31f06-118">Text Value</span></span>

<span data-ttu-id="31f06-119">와 같이.NET 형식의 정규화 된 이름을 지정 `System.IO.DirectoryInfo`합니다.</span><span class="sxs-lookup"><span data-stu-id="31f06-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="31f06-120">설명</span><span class="sxs-lookup"><span data-stu-id="31f06-120">Remarks</span></span>

<span data-ttu-id="31f06-121">각 사용자 지정 컨트롤 뷰 정의 형식 이름, 선택 집합 또는 정의 된 선택 조건을 하나 이상 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="31f06-121">Each custom control view definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="31f06-122">사용자 지정 컨트롤 보기의 구성 요소에 대 한 자세한 내용은 참조 [사용자 지정 컨트롤 만들기](./creating-custom-controls.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="31f06-122">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="31f06-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="31f06-123">See Also</span></span>

[<span data-ttu-id="31f06-124">사용자 지정 컨트롤 만들기</span><span class="sxs-lookup"><span data-stu-id="31f06-124">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="31f06-125">뷰 (형식)에 대 한 CustomEntry EntrySelectedBy 요소</span><span class="sxs-lookup"><span data-stu-id="31f06-125">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="31f06-126">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="31f06-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
