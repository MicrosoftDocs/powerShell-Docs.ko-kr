---
title: WideEntry (형식)에 대 한 EntrySelectedBy의 TypeName 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 9af443067467f590df824b28636f57b807a4fc94
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780188"
---
# <a name="typename-element-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="26a0d-102">WideEntry의 EntrySelectedBy에 대한 TypeName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="26a0d-102">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="26a0d-103">정의에 대 한 .NET 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="26a0d-103">Specifies a .NET type for the definition.</span></span> <span data-ttu-id="26a0d-104">이 개체가 표시 될 때마다 정의가 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="26a0d-104">The definition is used whenever this object is displayed.</span></span>

<span data-ttu-id="26a0d-105">Configuration 요소 (Format) ViewDefinitions 요소 (format) View Element (format) WideControl element (format) WideEntries Element (format) WideEntry Element (format) EntrySelectedBy 요소에 대 한 WideEntry (format) TypeName 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="26a0d-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) TypeName Element for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="26a0d-106">구문</span><span class="sxs-lookup"><span data-stu-id="26a0d-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="26a0d-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="26a0d-107">Attributes and Elements</span></span>

<span data-ttu-id="26a0d-108">다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `TypeName` .</span><span class="sxs-lookup"><span data-stu-id="26a0d-108">The following sections describe the attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="26a0d-109">특성</span><span class="sxs-lookup"><span data-stu-id="26a0d-109">Attributes</span></span>

<span data-ttu-id="26a0d-110">없음</span><span class="sxs-lookup"><span data-stu-id="26a0d-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="26a0d-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="26a0d-111">Child Elements</span></span>

<span data-ttu-id="26a0d-112">없음</span><span class="sxs-lookup"><span data-stu-id="26a0d-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="26a0d-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="26a0d-113">Parent Elements</span></span>

|<span data-ttu-id="26a0d-114">요소</span><span class="sxs-lookup"><span data-stu-id="26a0d-114">Element</span></span>|<span data-ttu-id="26a0d-115">설명</span><span class="sxs-lookup"><span data-stu-id="26a0d-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="26a0d-116">WideEntry에 대한 EntrySelectedBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="26a0d-116">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="26a0d-117">이 항목을 사용 하기 위해 존재 해야 하는 조건 또는이 광범위 한 항목을 사용 하는 .NET 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="26a0d-117">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="26a0d-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="26a0d-118">Text Value</span></span>

<span data-ttu-id="26a0d-119">.NET 형식의 정규화 된 이름 (예:)을 지정 합니다 `System.IO.DirectoryInfo` .</span><span class="sxs-lookup"><span data-stu-id="26a0d-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="26a0d-120">설명</span><span class="sxs-lookup"><span data-stu-id="26a0d-120">Remarks</span></span>

<span data-ttu-id="26a0d-121">각 넓은 항목은 정의를 사용 하기 위해 있어야 하는 하나 이상의 .NET 유형, 선택 집합 또는 선택 조건을 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="26a0d-121">Each wide entry must specify one or more .NET types, a selection set, or the selection condition that must exist for the definition to be used.</span></span>

<span data-ttu-id="26a0d-122">넓은 보기의 다른 구성 요소에 대 한 자세한 내용은 [넓은 뷰 만들기](./creating-a-wide-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="26a0d-122">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="26a0d-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="26a0d-123">See Also</span></span>

[<span data-ttu-id="26a0d-124">넓게 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="26a0d-124">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="26a0d-125">WideEntry에 대한 EntrySelectedBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="26a0d-125">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="26a0d-126">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="26a0d-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
