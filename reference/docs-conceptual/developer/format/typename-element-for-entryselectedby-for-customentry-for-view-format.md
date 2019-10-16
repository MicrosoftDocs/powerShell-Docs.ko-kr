---
title: 보기 (형식)의 CustomEntry에 대해 EntrySelectedBy의 TypeName 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76548af7-05bd-4d12-bf71-6fb69c434ef2
caps.latest.revision: 10
ms.openlocfilehash: c3dd761cd9b6c468d4833ea35b897ba5d425f598
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368072"
---
# <a name="typename-element-for-entryselectedby-for-customentry-for-view-format"></a><span data-ttu-id="5431e-102">View에 대한 CustomEntry의 EntrySelectedBy에 대한 TypeName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="5431e-102">TypeName Element for EntrySelectedBy for CustomEntry for View (Format)</span></span>

<span data-ttu-id="5431e-103">사용자 지정 컨트롤 뷰의이 정의를 사용 하는 .NET 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5431e-103">Specifies a .NET type that uses this definition of the custom control view.</span></span> <span data-ttu-id="5431e-104">정의에 대해 지정할 수 있는 형식 수에는 제한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5431e-104">There is no limit to the number of types that can be specified for a definition.</span></span>

<span data-ttu-id="5431e-105">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) CustomControl Element (format) Customentries 요소에 대 한 CustomControl의 customentries 요소 view (형식) EntrySelectedBy View (Format)의 CustomEntry에 대해 EntrySelectedBy View (Format) TypeName 요소의 CustomEntry 요소</span><span class="sxs-lookup"><span data-stu-id="5431e-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format) TypeName Element for EntrySelectedBy for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5431e-106">구문</span><span class="sxs-lookup"><span data-stu-id="5431e-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5431e-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="5431e-107">Attributes and Elements</span></span>

<span data-ttu-id="5431e-108">다음 섹션에서는 `TypeName` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="5431e-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5431e-109">특성</span><span class="sxs-lookup"><span data-stu-id="5431e-109">Attributes</span></span>

<span data-ttu-id="5431e-110">없음</span><span class="sxs-lookup"><span data-stu-id="5431e-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5431e-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="5431e-111">Child Elements</span></span>

<span data-ttu-id="5431e-112">없음</span><span class="sxs-lookup"><span data-stu-id="5431e-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5431e-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="5431e-113">Parent Elements</span></span>

|<span data-ttu-id="5431e-114">요소</span><span class="sxs-lookup"><span data-stu-id="5431e-114">Element</span></span>|<span data-ttu-id="5431e-115">설명</span><span class="sxs-lookup"><span data-stu-id="5431e-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5431e-116">View의 CustomEntry에 대 한 EntrySelectedBy 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="5431e-116">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="5431e-117">이 사용자 지정 컨트롤 뷰 정의를 사용 하는 .NET 형식 또는이 정의를 사용 하기 위해 존재 해야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="5431e-117">Defines the .NET types that use this custom control view definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="5431e-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="5431e-118">Text Value</span></span>

<span data-ttu-id="5431e-119">.NET 형식의 정규화 된 이름 (예: `System.IO.DirectoryInfo`)을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5431e-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="5431e-120">설명</span><span class="sxs-lookup"><span data-stu-id="5431e-120">Remarks</span></span>

<span data-ttu-id="5431e-121">각 사용자 지정 컨트롤 뷰 정의에는 하나 이상의 유형 이름, 선택 집합 또는 선택 조건이 정의 되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5431e-121">Each custom control view definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="5431e-122">사용자 지정 컨트롤 뷰의 구성 요소에 대 한 자세한 내용은 [사용자 지정 컨트롤 만들기](./creating-custom-controls.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5431e-122">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5431e-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5431e-123">See Also</span></span>

[<span data-ttu-id="5431e-124">사용자 지정 컨트롤 만들기</span><span class="sxs-lookup"><span data-stu-id="5431e-124">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="5431e-125">View의 CustomEntry에 대 한 EntrySelectedBy 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="5431e-125">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="5431e-126">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="5431e-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
