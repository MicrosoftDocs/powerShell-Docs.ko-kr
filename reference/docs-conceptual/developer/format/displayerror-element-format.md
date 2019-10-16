---
title: DisplayError 요소 (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 45c45800-a87d-456e-b07c-12d4d8c27c67
caps.latest.revision: 8
ms.openlocfilehash: 2c6a3d678ca68dc0d189f6ab981fdea5fef894cb
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363992"
---
# <a name="displayerror-element-format"></a><span data-ttu-id="b3868-102">DisplayError 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="b3868-102">DisplayError Element (Format)</span></span>

<span data-ttu-id="b3868-103">데이터의 일부를 표시 하는 동안 오류가 발생 하는 경우 문자열 #ERR 표시 되도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3868-103">Specifies that the string #ERR is displayed when an error occurs displaying a piece of data.</span></span>

<span data-ttu-id="b3868-104">Configuration 요소 (Format) DefaultSettings 요소 (format) DisplayError 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="b3868-104">Configuration Element (Format) DefaultSettings Element (Format) DisplayError Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b3868-105">구문</span><span class="sxs-lookup"><span data-stu-id="b3868-105">Syntax</span></span>

```xml
<DisplayError/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b3868-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="b3868-106">Attributes and Elements</span></span>

<span data-ttu-id="b3868-107">다음 섹션에서는 `DisplayError` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3868-107">The following sections describe attributes, child elements, and the parent element of the `DisplayError` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b3868-108">특성</span><span class="sxs-lookup"><span data-stu-id="b3868-108">Attributes</span></span>

<span data-ttu-id="b3868-109">없음</span><span class="sxs-lookup"><span data-stu-id="b3868-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b3868-110">자식 요소</span><span class="sxs-lookup"><span data-stu-id="b3868-110">Child Elements</span></span>

<span data-ttu-id="b3868-111">없음</span><span class="sxs-lookup"><span data-stu-id="b3868-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b3868-112">부모 요소</span><span class="sxs-lookup"><span data-stu-id="b3868-112">Parent Elements</span></span>

|<span data-ttu-id="b3868-113">요소</span><span class="sxs-lookup"><span data-stu-id="b3868-113">Element</span></span>|<span data-ttu-id="b3868-114">설명</span><span class="sxs-lookup"><span data-stu-id="b3868-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b3868-115">DefaultSettings 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="b3868-115">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="b3868-116">서식 파일의 모든 뷰에 적용 되는 일반 설정을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3868-116">Defines common settings that apply to all the views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b3868-117">설명</span><span class="sxs-lookup"><span data-stu-id="b3868-117">Remarks</span></span>

<span data-ttu-id="b3868-118">기본적으로 데이터의 일부를 표시 하는 동안 오류가 발생 하면 데이터의 위치를 비워 둡니다.</span><span class="sxs-lookup"><span data-stu-id="b3868-118">By default, when an error occurs while trying to display a piece of data, the location of the data is left blank.</span></span> <span data-ttu-id="b3868-119">이 요소를 true로 설정 하면 #ERR 문자열이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3868-119">When this element is set to true, the #ERR string will be displayed.</span></span>

## <a name="see-also"></a><span data-ttu-id="b3868-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b3868-120">See Also</span></span>

[<span data-ttu-id="b3868-121">DefaultSettings 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="b3868-121">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)

[<span data-ttu-id="b3868-122">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="b3868-122">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
