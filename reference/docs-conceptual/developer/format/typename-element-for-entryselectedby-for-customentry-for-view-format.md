---
title: 보기 (형식)의 CustomEntry에 대해 EntrySelectedBy의 TypeName 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: f8dc2c808e6eb3d6a7873cdbddc936b95d94c541
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785101"
---
# <a name="typename-element-for-entryselectedby-for-customentry-for-view-format"></a><span data-ttu-id="c117d-102">View에 대한 CustomEntry의 EntrySelectedBy에 대한 TypeName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="c117d-102">TypeName Element for EntrySelectedBy for CustomEntry for View (Format)</span></span>

<span data-ttu-id="c117d-103">사용자 지정 컨트롤 뷰의이 정의를 사용 하는 .NET 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c117d-103">Specifies a .NET type that uses this definition of the custom control view.</span></span> <span data-ttu-id="c117d-104">정의에 대해 지정할 수 있는 형식 수에는 제한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c117d-104">There is no limit to the number of types that can be specified for a definition.</span></span>

<span data-ttu-id="c117d-105">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) CustomControl Element (format) customentries 요소에 대 한 view (format) customentries 요소에 대 한 CustomEntries 요소에 대 한 customentries 요소에 대 한 customentries 요소에 대 한 customentries 요소</span><span class="sxs-lookup"><span data-stu-id="c117d-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format) TypeName Element for EntrySelectedBy for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c117d-106">구문</span><span class="sxs-lookup"><span data-stu-id="c117d-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c117d-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="c117d-107">Attributes and Elements</span></span>

<span data-ttu-id="c117d-108">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `TypeName` .</span><span class="sxs-lookup"><span data-stu-id="c117d-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c117d-109">특성</span><span class="sxs-lookup"><span data-stu-id="c117d-109">Attributes</span></span>

<span data-ttu-id="c117d-110">없음</span><span class="sxs-lookup"><span data-stu-id="c117d-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c117d-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="c117d-111">Child Elements</span></span>

<span data-ttu-id="c117d-112">없음</span><span class="sxs-lookup"><span data-stu-id="c117d-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c117d-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="c117d-113">Parent Elements</span></span>

|<span data-ttu-id="c117d-114">요소</span><span class="sxs-lookup"><span data-stu-id="c117d-114">Element</span></span>|<span data-ttu-id="c117d-115">설명</span><span class="sxs-lookup"><span data-stu-id="c117d-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c117d-116">View의 CustomEntry에 대 한 EntrySelectedBy 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="c117d-116">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="c117d-117">이 사용자 지정 컨트롤 뷰 정의를 사용 하는 .NET 형식 또는이 정의를 사용 하기 위해 존재 해야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="c117d-117">Defines the .NET types that use this custom control view definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c117d-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="c117d-118">Text Value</span></span>

<span data-ttu-id="c117d-119">.NET 형식의 정규화 된 이름 (예:)을 지정 합니다 `System.IO.DirectoryInfo` .</span><span class="sxs-lookup"><span data-stu-id="c117d-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="c117d-120">설명</span><span class="sxs-lookup"><span data-stu-id="c117d-120">Remarks</span></span>

<span data-ttu-id="c117d-121">각 사용자 지정 컨트롤 뷰 정의에는 하나 이상의 유형 이름, 선택 집합 또는 선택 조건이 정의 되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c117d-121">Each custom control view definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="c117d-122">사용자 지정 컨트롤 뷰의 구성 요소에 대 한 자세한 내용은 [사용자 지정 컨트롤 만들기](./creating-custom-controls.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c117d-122">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c117d-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c117d-123">See Also</span></span>

[<span data-ttu-id="c117d-124">사용자 지정 컨트롤 만들기</span><span class="sxs-lookup"><span data-stu-id="c117d-124">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="c117d-125">View의 CustomEntry에 대 한 EntrySelectedBy 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="c117d-125">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="c117d-126">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="c117d-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
