---
ms.date: 09/13/2016
ms.topic: reference
title: DisplayError 요소(형식)
description: DisplayError 요소(형식)
ms.openlocfilehash: fb54df86a3558263687a8c417870495b7066f563
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92649928"
---
# <a name="displayerror-element-format"></a><span data-ttu-id="8eef5-103">DisplayError 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="8eef5-103">DisplayError Element (Format)</span></span>

<span data-ttu-id="8eef5-104">데이터의 일부를 표시 하는 동안 오류가 발생 하는 경우 문자열 #ERR 표시 되도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8eef5-104">Specifies that the string #ERR is displayed when an error occurs displaying a piece of data.</span></span>

<span data-ttu-id="8eef5-105">Configuration 요소 (Format) DefaultSettings 요소 (format) DisplayError 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="8eef5-105">Configuration Element (Format) DefaultSettings Element (Format) DisplayError Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8eef5-106">구문</span><span class="sxs-lookup"><span data-stu-id="8eef5-106">Syntax</span></span>

```xml
<DisplayError/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8eef5-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="8eef5-107">Attributes and Elements</span></span>

<span data-ttu-id="8eef5-108">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `DisplayError` .</span><span class="sxs-lookup"><span data-stu-id="8eef5-108">The following sections describe attributes, child elements, and the parent element of the `DisplayError` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8eef5-109">특성</span><span class="sxs-lookup"><span data-stu-id="8eef5-109">Attributes</span></span>

<span data-ttu-id="8eef5-110">없음</span><span class="sxs-lookup"><span data-stu-id="8eef5-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8eef5-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="8eef5-111">Child Elements</span></span>

<span data-ttu-id="8eef5-112">없음</span><span class="sxs-lookup"><span data-stu-id="8eef5-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8eef5-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="8eef5-113">Parent Elements</span></span>

|<span data-ttu-id="8eef5-114">요소</span><span class="sxs-lookup"><span data-stu-id="8eef5-114">Element</span></span>|<span data-ttu-id="8eef5-115">설명</span><span class="sxs-lookup"><span data-stu-id="8eef5-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8eef5-116">DefaultSettings 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="8eef5-116">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="8eef5-117">서식 파일의 모든 뷰에 적용 되는 일반 설정을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="8eef5-117">Defines common settings that apply to all the views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="8eef5-118">설명</span><span class="sxs-lookup"><span data-stu-id="8eef5-118">Remarks</span></span>

<span data-ttu-id="8eef5-119">기본적으로 데이터의 일부를 표시 하는 동안 오류가 발생 하면 데이터의 위치를 비워 둡니다.</span><span class="sxs-lookup"><span data-stu-id="8eef5-119">By default, when an error occurs while trying to display a piece of data, the location of the data is left blank.</span></span> <span data-ttu-id="8eef5-120">이 요소를 true로 설정 하면 #ERR 문자열이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8eef5-120">When this element is set to true, the #ERR string will be displayed.</span></span>

## <a name="see-also"></a><span data-ttu-id="8eef5-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8eef5-121">See Also</span></span>

[<span data-ttu-id="8eef5-122">DefaultSettings 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="8eef5-122">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)

[<span data-ttu-id="8eef5-123">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="8eef5-123">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
