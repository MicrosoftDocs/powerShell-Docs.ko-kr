---
title: ViewSelectedBy (형식)에 대 한 TypeName 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0ad807a9-d7d8-4e96-b799-9c6a7677cc2d
caps.latest.revision: 12
ms.openlocfilehash: e2028c479103cc414295dc24a0f9bb69190bfc66
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361442"
---
# <a name="typename-element-for-viewselectedby-format"></a><span data-ttu-id="b6bbb-102">ViewSelectedBy에 대한 TypeName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="b6bbb-102">TypeName Element for ViewSelectedBy (Format)</span></span>

<span data-ttu-id="b6bbb-103">뷰에 표시 되는 .NET 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6bbb-103">Specifies a .NET object that is displayed by the view.</span></span>

<span data-ttu-id="b6bbb-104">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) ViewSelectedBy 요소 (형식)에 대 한 viewselectedby (형식)</span><span class="sxs-lookup"><span data-stu-id="b6bbb-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ViewSelectedBy Element (Format) TypeName Element for ViewSelectedBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b6bbb-105">구문</span><span class="sxs-lookup"><span data-stu-id="b6bbb-105">Syntax</span></span>

```xml
<TypeName>FullyQualifiedTypeName</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b6bbb-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="b6bbb-106">Attributes and Elements</span></span>

<span data-ttu-id="b6bbb-107">다음 섹션에서는 `TypeName` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6bbb-107">The following sections describe attributes, child elements, and the parent elements of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b6bbb-108">특성</span><span class="sxs-lookup"><span data-stu-id="b6bbb-108">Attributes</span></span>

<span data-ttu-id="b6bbb-109">없음</span><span class="sxs-lookup"><span data-stu-id="b6bbb-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b6bbb-110">자식 요소</span><span class="sxs-lookup"><span data-stu-id="b6bbb-110">Child Elements</span></span>

<span data-ttu-id="b6bbb-111">없음</span><span class="sxs-lookup"><span data-stu-id="b6bbb-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b6bbb-112">부모 요소</span><span class="sxs-lookup"><span data-stu-id="b6bbb-112">Parent Elements</span></span>

|<span data-ttu-id="b6bbb-113">요소</span><span class="sxs-lookup"><span data-stu-id="b6bbb-113">Element</span></span>|<span data-ttu-id="b6bbb-114">설명</span><span class="sxs-lookup"><span data-stu-id="b6bbb-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b6bbb-115">ViewSelectedBy 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="b6bbb-115">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="b6bbb-116">뷰에 표시 되는 .NET 개체를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6bbb-116">Defines the .NET objects that are displayed by the view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b6bbb-117">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="b6bbb-117">Text Value</span></span>

<span data-ttu-id="b6bbb-118">.NET 형식의 정규화 된 이름 (예: `System.IO.DirectoryInfo`)을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6bbb-118">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="b6bbb-119">설명</span><span class="sxs-lookup"><span data-stu-id="b6bbb-119">Remarks</span></span>

<span data-ttu-id="b6bbb-120">여러 보기에서이 요소를 사용 하는 방법에 대 한 자세한 내용은 [테이블 뷰 만들기](./creating-a-table-view.md), [목록 뷰 만들기](./creating-a-list-view.md), [넓은 뷰 만들기](./creating-a-wide-view.md)및 [사용자 지정 뷰 구성 요소](./creating-custom-controls.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b6bbb-120">For more information about how this element is used in different views, see [Creating a Table View](./creating-a-table-view.md), [Creating a List View](./creating-a-list-view.md), [Creating a Wide View](./creating-a-wide-view.md), and [Custom View Components](./creating-custom-controls.md).</span></span>

## <a name="example"></a><span data-ttu-id="b6bbb-121">예제</span><span class="sxs-lookup"><span data-stu-id="b6bbb-121">Example</span></span>

<span data-ttu-id="b6bbb-122">다음 예제에서는 목록 뷰에 대 한 [Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) 개체를 지정 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b6bbb-122">The following example shows how to specify the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object for a list view.</span></span> <span data-ttu-id="b6bbb-123">테이블, 전체 및 사용자 지정 보기에도 동일한 스키마가 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6bbb-123">The same schema is used for table, wide, and custom views.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="b6bbb-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b6bbb-124">See Also</span></span>

[<span data-ttu-id="b6bbb-125">목록 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="b6bbb-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="b6bbb-126">테이블 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="b6bbb-126">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="b6bbb-127">넓은 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="b6bbb-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="b6bbb-128">사용자 지정 컨트롤 만들기</span><span class="sxs-lookup"><span data-stu-id="b6bbb-128">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="b6bbb-129">ViewSelectedBy 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="b6bbb-129">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="b6bbb-130">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="b6bbb-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
