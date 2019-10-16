---
title: 뷰 (형식)의 컨트롤에 대 한 EntrySelectedBy의 TypeName 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 52003450-07ca-41e5-b075-8b6b03fc6e88
caps.latest.revision: 6
ms.openlocfilehash: 30215734ef832d778b08d3d7be224ff8d88b0579
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361782"
---
# <a name="typename-element-for-entryselectedby-for-controls-for-view-format"></a><span data-ttu-id="4e28d-102">View에 대한 Controls의 EntrySelectedBy에 대한 TypeName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="4e28d-102">TypeName Element for EntrySelectedBy for Controls for View (Format)</span></span>

<span data-ttu-id="4e28d-103">컨트롤의이 정의를 사용 하는 .NET 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e28d-103">Specifies a .NET type that uses this definition of the control.</span></span> <span data-ttu-id="4e28d-104">이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4e28d-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="4e28d-105">Configuration 요소 (Format) ViewDefinitions 요소 (Format) View 요소 (format) 컨트롤 요소 컨트롤에 대 한 컨트롤의 요소 (format) 컨트롤 요소 뷰 (format) CustomEntries 요소에 대 한 컨트롤에 대 한 컨트롤의 요소입니다. 보기 (형식)의 컨트롤에 대 한 CustomControl for view (format) CustomEntry 요소에 대 한 컨트롤의 Customentry 요소</span><span class="sxs-lookup"><span data-stu-id="4e28d-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) TypeName Element for EntrySelectedBy for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4e28d-106">구문</span><span class="sxs-lookup"><span data-stu-id="4e28d-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="4e28d-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="4e28d-107">Attributes and Elements</span></span>

<span data-ttu-id="4e28d-108">다음 섹션에서는 `TypeName` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e28d-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4e28d-109">특성</span><span class="sxs-lookup"><span data-stu-id="4e28d-109">Attributes</span></span>

<span data-ttu-id="4e28d-110">없음</span><span class="sxs-lookup"><span data-stu-id="4e28d-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4e28d-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="4e28d-111">Child Elements</span></span>

<span data-ttu-id="4e28d-112">없음</span><span class="sxs-lookup"><span data-stu-id="4e28d-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4e28d-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="4e28d-113">Parent Elements</span></span>

|<span data-ttu-id="4e28d-114">요소</span><span class="sxs-lookup"><span data-stu-id="4e28d-114">Element</span></span>|<span data-ttu-id="4e28d-115">설명</span><span class="sxs-lookup"><span data-stu-id="4e28d-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4e28d-116">View 컨트롤의 CustomEntry에 대 한 EntrySelectedBy 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="4e28d-116">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="4e28d-117">이 컨트롤 정의를 사용 하는 .NET 형식 또는이 정의를 사용 하기 위해 존재 해야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e28d-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="4e28d-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="4e28d-118">Text Value</span></span>

<span data-ttu-id="4e28d-119">.NET 형식의 정규화 된 이름 (예: `System.IO.DirectoryInfo`)을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e28d-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="4e28d-120">설명</span><span class="sxs-lookup"><span data-stu-id="4e28d-120">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="4e28d-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4e28d-121">See Also</span></span>

[<span data-ttu-id="4e28d-122">View 컨트롤의 CustomEntry에 대 한 EntrySelectedBy 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="4e28d-122">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="4e28d-123">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="4e28d-123">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
