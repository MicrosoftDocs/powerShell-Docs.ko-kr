---
title: TypeName 요소 ViewSelectedBy (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0ad807a9-d7d8-4e96-b799-9c6a7677cc2d
caps.latest.revision: 12
ms.openlocfilehash: e2028c479103cc414295dc24a0f9bb69190bfc66
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857899"
---
# <a name="typename-element-for-viewselectedby-format"></a><span data-ttu-id="78b2b-102">ViewSelectedBy에 대한 TypeName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="78b2b-102">TypeName Element for ViewSelectedBy (Format)</span></span>

<span data-ttu-id="78b2b-103">보기에 표시 되는.NET 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="78b2b-103">Specifies a .NET object that is displayed by the view.</span></span>

<span data-ttu-id="78b2b-104">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) ViewSelectedBy 요소 (형식) TypeName 요소 ViewSelectedBy (형식)에 대 한</span><span class="sxs-lookup"><span data-stu-id="78b2b-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ViewSelectedBy Element (Format) TypeName Element for ViewSelectedBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="78b2b-105">구문</span><span class="sxs-lookup"><span data-stu-id="78b2b-105">Syntax</span></span>

```xml
<TypeName>FullyQualifiedTypeName</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="78b2b-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="78b2b-106">Attributes and Elements</span></span>

<span data-ttu-id="78b2b-107">다음 섹션에서는 특성, 자식 요소 및 부모 요소는 `TypeName` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="78b2b-107">The following sections describe attributes, child elements, and the parent elements of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="78b2b-108">특성</span><span class="sxs-lookup"><span data-stu-id="78b2b-108">Attributes</span></span>

<span data-ttu-id="78b2b-109">없음</span><span class="sxs-lookup"><span data-stu-id="78b2b-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="78b2b-110">자식 요소</span><span class="sxs-lookup"><span data-stu-id="78b2b-110">Child Elements</span></span>

<span data-ttu-id="78b2b-111">없음</span><span class="sxs-lookup"><span data-stu-id="78b2b-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="78b2b-112">부모 요소</span><span class="sxs-lookup"><span data-stu-id="78b2b-112">Parent Elements</span></span>

|<span data-ttu-id="78b2b-113">요소</span><span class="sxs-lookup"><span data-stu-id="78b2b-113">Element</span></span>|<span data-ttu-id="78b2b-114">설명</span><span class="sxs-lookup"><span data-stu-id="78b2b-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="78b2b-115">ViewSelectedBy 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="78b2b-115">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="78b2b-116">보기에 표시 되는.NET 개체를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="78b2b-116">Defines the .NET objects that are displayed by the view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="78b2b-117">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="78b2b-117">Text Value</span></span>

<span data-ttu-id="78b2b-118">와 같이.NET 형식의 정규화 된 이름을 지정 `System.IO.DirectoryInfo`합니다.</span><span class="sxs-lookup"><span data-stu-id="78b2b-118">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="78b2b-119">설명</span><span class="sxs-lookup"><span data-stu-id="78b2b-119">Remarks</span></span>

<span data-ttu-id="78b2b-120">다른 보기에이 요소를 사용 하는 방법에 대 한 자세한 내용은 참조 하세요. [테이블 뷰를 만드는](./creating-a-table-view.md), [목록 뷰를 만들면](./creating-a-list-view.md)를 [넓은 보기를 만드는](./creating-a-wide-view.md), 및 [ 사용자 지정 뷰 구성 요소](./creating-custom-controls.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="78b2b-120">For more information about how this element is used in different views, see [Creating a Table View](./creating-a-table-view.md), [Creating a List View](./creating-a-list-view.md), [Creating a Wide View](./creating-a-wide-view.md), and [Custom View Components](./creating-custom-controls.md).</span></span>

## <a name="example"></a><span data-ttu-id="78b2b-121">예제</span><span class="sxs-lookup"><span data-stu-id="78b2b-121">Example</span></span>

<span data-ttu-id="78b2b-122">다음 예제에서는 지정 하는 방법을 보여 줍니다 합니다 [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) 목록 보기에 대 한 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="78b2b-122">The following example shows how to specify the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object for a list view.</span></span> <span data-ttu-id="78b2b-123">동일한 스키마는 테이블, 넓게 및 사용자 지정 보기에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="78b2b-123">The same schema is used for table, wide, and custom views.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="78b2b-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="78b2b-124">See Also</span></span>

[<span data-ttu-id="78b2b-125">목록 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="78b2b-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="78b2b-126">테이블 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="78b2b-126">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="78b2b-127">넓은 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="78b2b-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="78b2b-128">사용자 지정 컨트롤 만들기</span><span class="sxs-lookup"><span data-stu-id="78b2b-128">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="78b2b-129">ViewSelectedBy 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="78b2b-129">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="78b2b-130">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="78b2b-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
