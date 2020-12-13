---
ms.date: 09/13/2016
ms.topic: reference
title: WideEntry의 EntrySelectedBy에 대한 TypeName 요소(형식)
description: WideEntry의 EntrySelectedBy에 대한 TypeName 요소(형식)
ms.openlocfilehash: 2e0facd6ff7c6fec96dabf488449a8502429bcff
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92654787"
---
# <a name="typename-element-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="ba29e-103">WideEntry의 EntrySelectedBy에 대한 TypeName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="ba29e-103">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="ba29e-104">정의에 대 한 .NET 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ba29e-104">Specifies a .NET type for the definition.</span></span> <span data-ttu-id="ba29e-105">이 개체가 표시 될 때마다 정의가 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ba29e-105">The definition is used whenever this object is displayed.</span></span>

<span data-ttu-id="ba29e-106">Configuration 요소 (Format) ViewDefinitions 요소 (format) View Element (format) WideControl element (format) WideEntries Element (format) WideEntry Element (format) EntrySelectedBy 요소에 대 한 WideEntry (format) TypeName 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="ba29e-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) TypeName Element for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ba29e-107">구문</span><span class="sxs-lookup"><span data-stu-id="ba29e-107">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ba29e-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="ba29e-108">Attributes and Elements</span></span>

<span data-ttu-id="ba29e-109">다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `TypeName` .</span><span class="sxs-lookup"><span data-stu-id="ba29e-109">The following sections describe the attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ba29e-110">특성</span><span class="sxs-lookup"><span data-stu-id="ba29e-110">Attributes</span></span>

<span data-ttu-id="ba29e-111">없음</span><span class="sxs-lookup"><span data-stu-id="ba29e-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ba29e-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="ba29e-112">Child Elements</span></span>

<span data-ttu-id="ba29e-113">없음</span><span class="sxs-lookup"><span data-stu-id="ba29e-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ba29e-114">부모 요소</span><span class="sxs-lookup"><span data-stu-id="ba29e-114">Parent Elements</span></span>

|<span data-ttu-id="ba29e-115">요소</span><span class="sxs-lookup"><span data-stu-id="ba29e-115">Element</span></span>|<span data-ttu-id="ba29e-116">설명</span><span class="sxs-lookup"><span data-stu-id="ba29e-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ba29e-117">WideEntry에 대한 EntrySelectedBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="ba29e-117">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="ba29e-118">이 항목을 사용 하기 위해 존재 해야 하는 조건 또는이 광범위 한 항목을 사용 하는 .NET 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="ba29e-118">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ba29e-119">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="ba29e-119">Text Value</span></span>

<span data-ttu-id="ba29e-120">.NET 형식의 정규화 된 이름 (예:)을 지정 합니다 `System.IO.DirectoryInfo` .</span><span class="sxs-lookup"><span data-stu-id="ba29e-120">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="ba29e-121">설명</span><span class="sxs-lookup"><span data-stu-id="ba29e-121">Remarks</span></span>

<span data-ttu-id="ba29e-122">각 넓은 항목은 정의를 사용 하기 위해 있어야 하는 하나 이상의 .NET 유형, 선택 집합 또는 선택 조건을 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ba29e-122">Each wide entry must specify one or more .NET types, a selection set, or the selection condition that must exist for the definition to be used.</span></span>

<span data-ttu-id="ba29e-123">넓은 보기의 다른 구성 요소에 대 한 자세한 내용은 [넓은 뷰 만들기](./creating-a-wide-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ba29e-123">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ba29e-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ba29e-124">See Also</span></span>

[<span data-ttu-id="ba29e-125">넓게 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="ba29e-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="ba29e-126">WideEntry에 대한 EntrySelectedBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="ba29e-126">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="ba29e-127">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="ba29e-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
