---
title: GroupBy (형식)에 대 한 CustomControl 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: b8265e872d34ea5dbcedfaa1668d21df8c3b35eb
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786070"
---
# <a name="customcontrol-element-for-groupby-format"></a><span data-ttu-id="3aded-102">GroupBy에 대한 CustomControl 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="3aded-102">CustomControl Element for GroupBy (Format)</span></span>

<span data-ttu-id="3aded-103">새 그룹을 표시 하는 사용자 지정 컨트롤을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="3aded-103">Defines the custom control that displays the new group.</span></span>

<span data-ttu-id="3aded-104">구성 요소 (Format) ViewDefinitions 요소 (Format) View 요소 (format) GroupBy 요소 (형식)에 대 한 View (Format) CustomControl 요소</span><span class="sxs-lookup"><span data-stu-id="3aded-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3aded-105">구문</span><span class="sxs-lookup"><span data-stu-id="3aded-105">Syntax</span></span>

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
<CustomControl>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3aded-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="3aded-106">Attributes and Elements</span></span>

<span data-ttu-id="3aded-107">다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `CustomControl` .</span><span class="sxs-lookup"><span data-stu-id="3aded-107">The following sections describe the attributes, child elements, and parent element of the `CustomControl` element.</span></span> <span data-ttu-id="3aded-108">원하는 수의 자식 요소를 지정 하 고 원하는 순서 대로 나열할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3aded-108">You can specify any number of child elements and list them in any order.</span></span>

### <a name="attributes"></a><span data-ttu-id="3aded-109">특성</span><span class="sxs-lookup"><span data-stu-id="3aded-109">Attributes</span></span>

<span data-ttu-id="3aded-110">없음</span><span class="sxs-lookup"><span data-stu-id="3aded-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3aded-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="3aded-111">Child Elements</span></span>

|<span data-ttu-id="3aded-112">요소</span><span class="sxs-lookup"><span data-stu-id="3aded-112">Element</span></span>|<span data-ttu-id="3aded-113">설명</span><span class="sxs-lookup"><span data-stu-id="3aded-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3aded-114">GroupBy의 CustomControl에 대한 CustomEntries 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="3aded-114">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>](./customentries-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="3aded-115">필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="3aded-115">Required element.</span></span><br /><br /> <span data-ttu-id="3aded-116">컨트롤에 대 한 정의를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="3aded-116">Provides the definitions for the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="3aded-117">부모 요소</span><span class="sxs-lookup"><span data-stu-id="3aded-117">Parent Elements</span></span>

|<span data-ttu-id="3aded-118">요소</span><span class="sxs-lookup"><span data-stu-id="3aded-118">Element</span></span>|<span data-ttu-id="3aded-119">설명</span><span class="sxs-lookup"><span data-stu-id="3aded-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3aded-120">View에 대한 GroupBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="3aded-120">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="3aded-121">Windows PowerShell에서 새로운 개체 그룹을 표시 하는 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="3aded-121">Defines how Windows PowerShell displays a new group of objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3aded-122">설명</span><span class="sxs-lookup"><span data-stu-id="3aded-122">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="3aded-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3aded-123">See Also</span></span>

[<span data-ttu-id="3aded-124">GroupBy의 CustomControl에 대한 CustomEntries 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="3aded-124">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>](./customentries-element-for-customcontrol-for-groupby-format.md)

[<span data-ttu-id="3aded-125">View에 대한 GroupBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="3aded-125">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="3aded-126">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="3aded-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
