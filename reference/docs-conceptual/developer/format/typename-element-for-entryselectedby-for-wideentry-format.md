---
title: WideEntry (형식)에 대 한 EntrySelectedBy의 TypeName 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 81a91c74-6229-4b64-aa2b-9123e8b7e9e5
caps.latest.revision: 11
ms.openlocfilehash: be35f6e9e2ad0b2d9a21a91c053aa0f70cafaf9c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361622"
---
# <a name="typename-element-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="ecd9f-102">WideEntry의 EntrySelectedBy에 대한 TypeName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="ecd9f-102">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="ecd9f-103">정의에 대 한 .NET 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd9f-103">Specifies a .NET type for the definition.</span></span> <span data-ttu-id="ecd9f-104">이 개체가 표시 될 때마다 정의가 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ecd9f-104">The definition is used whenever this object is displayed.</span></span>

<span data-ttu-id="ecd9f-105">Configuration 요소 (Format) ViewDefinitions 요소 (format) WideControl Element (format) WideEntries Element (format) WideEntry Element (format) EntrySelectedBy 요소에 대 한 WideEntry (Format) TypeName 요소에 대해 WideEntry ( 형식과</span><span class="sxs-lookup"><span data-stu-id="ecd9f-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) TypeName Element for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ecd9f-106">구문</span><span class="sxs-lookup"><span data-stu-id="ecd9f-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ecd9f-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="ecd9f-107">Attributes and Elements</span></span>

<span data-ttu-id="ecd9f-108">다음 섹션에서는 `TypeName` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd9f-108">The following sections describe the attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ecd9f-109">특성</span><span class="sxs-lookup"><span data-stu-id="ecd9f-109">Attributes</span></span>

<span data-ttu-id="ecd9f-110">없음</span><span class="sxs-lookup"><span data-stu-id="ecd9f-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ecd9f-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="ecd9f-111">Child Elements</span></span>

<span data-ttu-id="ecd9f-112">없음</span><span class="sxs-lookup"><span data-stu-id="ecd9f-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ecd9f-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="ecd9f-113">Parent Elements</span></span>

|<span data-ttu-id="ecd9f-114">요소</span><span class="sxs-lookup"><span data-stu-id="ecd9f-114">Element</span></span>|<span data-ttu-id="ecd9f-115">설명</span><span class="sxs-lookup"><span data-stu-id="ecd9f-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ecd9f-116">WideEntry (형식)에 대 한 EntrySelectedBy 요소</span><span class="sxs-lookup"><span data-stu-id="ecd9f-116">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="ecd9f-117">이 항목을 사용 하기 위해 존재 해야 하는 조건 또는이 광범위 한 항목을 사용 하는 .NET 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd9f-117">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ecd9f-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="ecd9f-118">Text Value</span></span>

<span data-ttu-id="ecd9f-119">.NET 형식의 정규화 된 이름 (예: `System.IO.DirectoryInfo`)을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd9f-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="ecd9f-120">설명</span><span class="sxs-lookup"><span data-stu-id="ecd9f-120">Remarks</span></span>

<span data-ttu-id="ecd9f-121">각 넓은 항목은 정의를 사용 하기 위해 있어야 하는 하나 이상의 .NET 유형, 선택 집합 또는 선택 조건을 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd9f-121">Each wide entry must specify one or more .NET types, a selection set, or the selection condition that must exist for the definition to be used.</span></span>

<span data-ttu-id="ecd9f-122">넓은 보기의 다른 구성 요소에 대 한 자세한 내용은 [넓은 뷰 만들기](./creating-a-wide-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ecd9f-122">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ecd9f-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ecd9f-123">See Also</span></span>

[<span data-ttu-id="ecd9f-124">넓은 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="ecd9f-124">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="ecd9f-125">WideEntry (형식)에 대 한 EntrySelectedBy 요소</span><span class="sxs-lookup"><span data-stu-id="ecd9f-125">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="ecd9f-126">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="ecd9f-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
