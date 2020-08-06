---
title: GroupBy (형식)에 대 한 ScriptBlock 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e761e02a7910cd598449d564e827889162da9f25
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787685"
---
# <a name="scriptblock-element-for-groupby-format"></a><span data-ttu-id="f93cd-102">GroupBy에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="f93cd-102">ScriptBlock Element for GroupBy (Format)</span></span>

<span data-ttu-id="f93cd-103">값이 변경 될 때마다 새 그룹을 시작 하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f93cd-103">Specifies the script that starts a new group whenever its value changes.</span></span>

<span data-ttu-id="f93cd-104">구성 요소 (Format) ViewDefinitions 요소 (Format) View 요소 (Format) GroupBy 요소에 대 한 groupby 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="f93cd-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) ScriptBlock Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f93cd-105">구문</span><span class="sxs-lookup"><span data-stu-id="f93cd-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f93cd-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="f93cd-106">Attributes and Elements</span></span>

<span data-ttu-id="f93cd-107">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `ScriptBlock` .</span><span class="sxs-lookup"><span data-stu-id="f93cd-107">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f93cd-108">특성</span><span class="sxs-lookup"><span data-stu-id="f93cd-108">Attributes</span></span>

<span data-ttu-id="f93cd-109">없음</span><span class="sxs-lookup"><span data-stu-id="f93cd-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f93cd-110">자식 요소</span><span class="sxs-lookup"><span data-stu-id="f93cd-110">Child Elements</span></span>

<span data-ttu-id="f93cd-111">없음</span><span class="sxs-lookup"><span data-stu-id="f93cd-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f93cd-112">부모 요소</span><span class="sxs-lookup"><span data-stu-id="f93cd-112">Parent Elements</span></span>

|<span data-ttu-id="f93cd-113">요소</span><span class="sxs-lookup"><span data-stu-id="f93cd-113">Element</span></span>|<span data-ttu-id="f93cd-114">설명</span><span class="sxs-lookup"><span data-stu-id="f93cd-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f93cd-115">View에 대한 GroupBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="f93cd-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="f93cd-116">.NET 개체 그룹이 표시 되는 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="f93cd-116">Defines how a group of .NET objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f93cd-117">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="f93cd-117">Text Value</span></span>

<span data-ttu-id="f93cd-118">평가 되는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f93cd-118">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="f93cd-119">설명</span><span class="sxs-lookup"><span data-stu-id="f93cd-119">Remarks</span></span>

<span data-ttu-id="f93cd-120">PowerShell은이 스크립트의 값이 변경 될 때마다 새 그룹을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="f93cd-120">PowerShell starts a new group whenever the value of this script changes.</span></span>

<span data-ttu-id="f93cd-121">이 요소를 지정 하면 새 그룹을 시작 하는 [PropertyName](propertyname-element-for-groupby-format.md) 요소를 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f93cd-121">When this element is specified, you cannot specify the [PropertyName](propertyname-element-for-groupby-format.md) element to start a new group.</span></span>

## <a name="see-also"></a><span data-ttu-id="f93cd-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f93cd-122">See Also</span></span>

[<span data-ttu-id="f93cd-123">GroupBy에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="f93cd-123">PropertyName Element for GroupBy (Format)</span></span>](propertyname-element-for-groupby-format.md)

[<span data-ttu-id="f93cd-124">View에 대한 GroupBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="f93cd-124">GroupBy Element for View (Format)</span></span>](groupby-element-for-view-format.md)

[<span data-ttu-id="f93cd-125">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="f93cd-125">Writing a PowerShell Formatting File</span></span>](writing-a-powershell-formatting-file.md)
