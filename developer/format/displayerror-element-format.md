---
title: DisplayError 요소 (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 45c45800-a87d-456e-b07c-12d4d8c27c67
caps.latest.revision: 8
ms.openlocfilehash: 2c6a3d678ca68dc0d189f6ab981fdea5fef894cb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066263"
---
# <a name="displayerror-element-format"></a><span data-ttu-id="e784f-102">DisplayError 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="e784f-102">DisplayError Element (Format)</span></span>

<span data-ttu-id="e784f-103">오류가 발생 하는 데이터의 일부를 표시 하는 경우 문자열 #ERR 표시 되도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e784f-103">Specifies that the string #ERR is displayed when an error occurs displaying a piece of data.</span></span>

<span data-ttu-id="e784f-104">구성 요소 (형식) DefaultSettings (형식) DisplayError 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="e784f-104">Configuration Element (Format) DefaultSettings Element (Format) DisplayError Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e784f-105">구문</span><span class="sxs-lookup"><span data-stu-id="e784f-105">Syntax</span></span>

```xml
<DisplayError/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e784f-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="e784f-106">Attributes and Elements</span></span>

<span data-ttu-id="e784f-107">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `DisplayError` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="e784f-107">The following sections describe attributes, child elements, and the parent element of the `DisplayError` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e784f-108">특성</span><span class="sxs-lookup"><span data-stu-id="e784f-108">Attributes</span></span>

<span data-ttu-id="e784f-109">없음</span><span class="sxs-lookup"><span data-stu-id="e784f-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e784f-110">자식 요소</span><span class="sxs-lookup"><span data-stu-id="e784f-110">Child Elements</span></span>

<span data-ttu-id="e784f-111">없음</span><span class="sxs-lookup"><span data-stu-id="e784f-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e784f-112">부모 요소</span><span class="sxs-lookup"><span data-stu-id="e784f-112">Parent Elements</span></span>

|<span data-ttu-id="e784f-113">요소</span><span class="sxs-lookup"><span data-stu-id="e784f-113">Element</span></span>|<span data-ttu-id="e784f-114">설명</span><span class="sxs-lookup"><span data-stu-id="e784f-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e784f-115">DefaultSettings 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="e784f-115">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="e784f-116">서식 파일의 모든 뷰에 적용 되는 일반적인 설정을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="e784f-116">Defines common settings that apply to all the views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e784f-117">설명</span><span class="sxs-lookup"><span data-stu-id="e784f-117">Remarks</span></span>

<span data-ttu-id="e784f-118">기본적으로 데이터를 표시 하는 동안 오류가 발생 하는 경우는 데이터의 위치를 비워 둡니다.</span><span class="sxs-lookup"><span data-stu-id="e784f-118">By default, when an error occurs while trying to display a piece of data, the location of the data is left blank.</span></span> <span data-ttu-id="e784f-119">이 요소는 #ERR 문자열을 true로 설정 된 경우 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e784f-119">When this element is set to true, the #ERR string will be displayed.</span></span>

## <a name="see-also"></a><span data-ttu-id="e784f-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e784f-120">See Also</span></span>

[<span data-ttu-id="e784f-121">DefaultSettings 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="e784f-121">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)

[<span data-ttu-id="e784f-122">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="e784f-122">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
