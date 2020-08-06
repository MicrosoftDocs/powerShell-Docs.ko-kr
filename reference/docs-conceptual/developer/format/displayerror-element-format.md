---
title: DisplayError 요소 (Format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 5d46c2fbd48f592db5ba1b33eb6cead8dc1c4698
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774289"
---
# <a name="displayerror-element-format"></a><span data-ttu-id="a9981-102">DisplayError 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="a9981-102">DisplayError Element (Format)</span></span>

<span data-ttu-id="a9981-103">데이터의 일부를 표시 하는 동안 오류가 발생 하는 경우 문자열 #ERR 표시 되도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a9981-103">Specifies that the string #ERR is displayed when an error occurs displaying a piece of data.</span></span>

<span data-ttu-id="a9981-104">Configuration 요소 (Format) DefaultSettings 요소 (format) DisplayError 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="a9981-104">Configuration Element (Format) DefaultSettings Element (Format) DisplayError Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a9981-105">구문</span><span class="sxs-lookup"><span data-stu-id="a9981-105">Syntax</span></span>

```xml
<DisplayError/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a9981-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="a9981-106">Attributes and Elements</span></span>

<span data-ttu-id="a9981-107">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `DisplayError` .</span><span class="sxs-lookup"><span data-stu-id="a9981-107">The following sections describe attributes, child elements, and the parent element of the `DisplayError` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a9981-108">특성</span><span class="sxs-lookup"><span data-stu-id="a9981-108">Attributes</span></span>

<span data-ttu-id="a9981-109">없음</span><span class="sxs-lookup"><span data-stu-id="a9981-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a9981-110">자식 요소</span><span class="sxs-lookup"><span data-stu-id="a9981-110">Child Elements</span></span>

<span data-ttu-id="a9981-111">없음</span><span class="sxs-lookup"><span data-stu-id="a9981-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a9981-112">부모 요소</span><span class="sxs-lookup"><span data-stu-id="a9981-112">Parent Elements</span></span>

|<span data-ttu-id="a9981-113">요소</span><span class="sxs-lookup"><span data-stu-id="a9981-113">Element</span></span>|<span data-ttu-id="a9981-114">설명</span><span class="sxs-lookup"><span data-stu-id="a9981-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a9981-115">DefaultSettings 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="a9981-115">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="a9981-116">서식 파일의 모든 뷰에 적용 되는 일반 설정을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="a9981-116">Defines common settings that apply to all the views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a9981-117">설명</span><span class="sxs-lookup"><span data-stu-id="a9981-117">Remarks</span></span>

<span data-ttu-id="a9981-118">기본적으로 데이터의 일부를 표시 하는 동안 오류가 발생 하면 데이터의 위치를 비워 둡니다.</span><span class="sxs-lookup"><span data-stu-id="a9981-118">By default, when an error occurs while trying to display a piece of data, the location of the data is left blank.</span></span> <span data-ttu-id="a9981-119">이 요소를 true로 설정 하면 #ERR 문자열이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a9981-119">When this element is set to true, the #ERR string will be displayed.</span></span>

## <a name="see-also"></a><span data-ttu-id="a9981-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a9981-120">See Also</span></span>

[<span data-ttu-id="a9981-121">DefaultSettings 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="a9981-121">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)

[<span data-ttu-id="a9981-122">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="a9981-122">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
