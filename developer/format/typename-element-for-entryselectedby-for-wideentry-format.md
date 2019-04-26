---
title: EntrySelectedBy WideEntry (형식)에 대 한 TypeName 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 81a91c74-6229-4b64-aa2b-9123e8b7e9e5
caps.latest.revision: 11
ms.openlocfilehash: be35f6e9e2ad0b2d9a21a91c053aa0f70cafaf9c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083929"
---
# <a name="typename-element-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="880b8-102">WideEntry의 EntrySelectedBy에 대한 TypeName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="880b8-102">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="880b8-103">정의 대 한.NET 유형을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="880b8-103">Specifies a .NET type for the definition.</span></span> <span data-ttu-id="880b8-104">이 개체에 표시 될 때마다 정이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="880b8-104">The definition is used whenever this object is displayed.</span></span>

<span data-ttu-id="880b8-105">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) WideControl 요소 (형식) WideEntries 요소 (형식) WideEntry 요소 (형식) EntrySelectedBy 요소 WideEntry (TypeName 요소의 WideEntry (형식) 형식)</span><span class="sxs-lookup"><span data-stu-id="880b8-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) TypeName Element for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="880b8-106">구문</span><span class="sxs-lookup"><span data-stu-id="880b8-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="880b8-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="880b8-107">Attributes and Elements</span></span>

<span data-ttu-id="880b8-108">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `TypeName` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="880b8-108">The following sections describe the attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="880b8-109">특성</span><span class="sxs-lookup"><span data-stu-id="880b8-109">Attributes</span></span>

<span data-ttu-id="880b8-110">없음</span><span class="sxs-lookup"><span data-stu-id="880b8-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="880b8-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="880b8-111">Child Elements</span></span>

<span data-ttu-id="880b8-112">없음</span><span class="sxs-lookup"><span data-stu-id="880b8-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="880b8-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="880b8-113">Parent Elements</span></span>

|<span data-ttu-id="880b8-114">요소</span><span class="sxs-lookup"><span data-stu-id="880b8-114">Element</span></span>|<span data-ttu-id="880b8-115">설명</span><span class="sxs-lookup"><span data-stu-id="880b8-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="880b8-116">WideEntry (형식)에 대 한 EntrySelectedBy 요소</span><span class="sxs-lookup"><span data-stu-id="880b8-116">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="880b8-117">이 와이드 항목 또는 사용할이 항목에 대 한 있어야 하는 조건을 사용 하는.NET 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="880b8-117">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="880b8-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="880b8-118">Text Value</span></span>

<span data-ttu-id="880b8-119">와 같이.NET 형식의 정규화 된 이름을 지정 `System.IO.DirectoryInfo`합니다.</span><span class="sxs-lookup"><span data-stu-id="880b8-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="880b8-120">설명</span><span class="sxs-lookup"><span data-stu-id="880b8-120">Remarks</span></span>

<span data-ttu-id="880b8-121">각 와이드 항목 하나 이상의.NET 형식, 선택 항목 집합 또는 사용할 정의에 있어야 하는 선택 조건을 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="880b8-121">Each wide entry must specify one or more .NET types, a selection set, or the selection condition that must exist for the definition to be used.</span></span>

<span data-ttu-id="880b8-122">넓은 보기의 다른 구성 요소에 대 한 자세한 내용은 참조 [넓은 보기를 만드는](./creating-a-wide-view.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="880b8-122">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="880b8-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="880b8-123">See Also</span></span>

[<span data-ttu-id="880b8-124">넓은 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="880b8-124">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="880b8-125">WideEntry (형식)에 대 한 EntrySelectedBy 요소</span><span class="sxs-lookup"><span data-stu-id="880b8-125">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="880b8-126">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="880b8-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
