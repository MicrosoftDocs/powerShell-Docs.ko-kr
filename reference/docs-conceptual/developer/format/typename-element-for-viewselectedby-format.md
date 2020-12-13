---
ms.date: 09/13/2016
ms.topic: reference
title: ViewSelectedBy에 대한 TypeName 요소(형식)
description: ViewSelectedBy에 대한 TypeName 요소(형식)
ms.openlocfilehash: 62edc2fe4b4c1c5f1b17dd2f8b0943f28ff5dfb7
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667728"
---
# <a name="typename-element-for-viewselectedby-format"></a><span data-ttu-id="13c5d-103">ViewSelectedBy에 대한 TypeName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="13c5d-103">TypeName Element for ViewSelectedBy (Format)</span></span>

<span data-ttu-id="13c5d-104">뷰에 표시 되는 .NET 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="13c5d-104">Specifies a .NET object that is displayed by the view.</span></span>

<span data-ttu-id="13c5d-105">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) ViewSelectedBy 요소 (형식)에 대 한 viewselectedby (형식)</span><span class="sxs-lookup"><span data-stu-id="13c5d-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ViewSelectedBy Element (Format) TypeName Element for ViewSelectedBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="13c5d-106">구문</span><span class="sxs-lookup"><span data-stu-id="13c5d-106">Syntax</span></span>

```xml
<TypeName>FullyQualifiedTypeName</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="13c5d-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="13c5d-107">Attributes and Elements</span></span>

<span data-ttu-id="13c5d-108">다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `TypeName` .</span><span class="sxs-lookup"><span data-stu-id="13c5d-108">The following sections describe attributes, child elements, and the parent elements of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="13c5d-109">특성</span><span class="sxs-lookup"><span data-stu-id="13c5d-109">Attributes</span></span>

<span data-ttu-id="13c5d-110">없음</span><span class="sxs-lookup"><span data-stu-id="13c5d-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="13c5d-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="13c5d-111">Child Elements</span></span>

<span data-ttu-id="13c5d-112">없음</span><span class="sxs-lookup"><span data-stu-id="13c5d-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="13c5d-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="13c5d-113">Parent Elements</span></span>

|<span data-ttu-id="13c5d-114">요소</span><span class="sxs-lookup"><span data-stu-id="13c5d-114">Element</span></span>|<span data-ttu-id="13c5d-115">설명</span><span class="sxs-lookup"><span data-stu-id="13c5d-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="13c5d-116">ViewSelectedBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="13c5d-116">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="13c5d-117">뷰에 표시 되는 .NET 개체를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="13c5d-117">Defines the .NET objects that are displayed by the view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="13c5d-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="13c5d-118">Text Value</span></span>

<span data-ttu-id="13c5d-119">.NET 형식의 정규화 된 이름 (예:)을 지정 합니다 `System.IO.DirectoryInfo` .</span><span class="sxs-lookup"><span data-stu-id="13c5d-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="13c5d-120">설명</span><span class="sxs-lookup"><span data-stu-id="13c5d-120">Remarks</span></span>

<span data-ttu-id="13c5d-121">여러 보기에서이 요소를 사용 하는 방법에 대 한 자세한 내용은 [테이블 뷰 만들기](./creating-a-table-view.md), [목록 뷰 만들기](./creating-a-list-view.md), [넓은 뷰 만들기](./creating-a-wide-view.md)및 [사용자 지정 뷰 구성 요소](./creating-custom-controls.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="13c5d-121">For more information about how this element is used in different views, see [Creating a Table View](./creating-a-table-view.md), [Creating a List View](./creating-a-list-view.md), [Creating a Wide View](./creating-a-wide-view.md), and [Custom View Components](./creating-custom-controls.md).</span></span>

## <a name="example"></a><span data-ttu-id="13c5d-122">예제</span><span class="sxs-lookup"><span data-stu-id="13c5d-122">Example</span></span>

<span data-ttu-id="13c5d-123">다음 예제에서는 목록 뷰에 대 한 [Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) 개체를 지정 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="13c5d-123">The following example shows how to specify the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object for a list view.</span></span> <span data-ttu-id="13c5d-124">테이블, 전체 및 사용자 지정 보기에도 동일한 스키마가 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="13c5d-124">The same schema is used for table, wide, and custom views.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="13c5d-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="13c5d-125">See Also</span></span>

[<span data-ttu-id="13c5d-126">목록 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="13c5d-126">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="13c5d-127">테이블 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="13c5d-127">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="13c5d-128">넓게 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="13c5d-128">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="13c5d-129">사용자 지정 컨트롤 만들기</span><span class="sxs-lookup"><span data-stu-id="13c5d-129">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="13c5d-130">ViewSelectedBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="13c5d-130">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="13c5d-131">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="13c5d-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
