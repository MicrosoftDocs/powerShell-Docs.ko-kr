---
title: View 컨트롤의 SelectionCondition에 대 한 TypeName 요소 (형식) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 4795c3af40cf60fb8e71185feced18c192b3a0aa
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780052"
---
# <a name="typename-element-for-selectioncondition-for-controls-for-view-format"></a><span data-ttu-id="6717e-102">View에 대한 Controls의 SelectionCondition에 대한 TypeName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="6717e-102">TypeName Element for SelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="6717e-103">조건을 트리거하는 .NET 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6717e-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="6717e-104">이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6717e-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="6717e-105">Configuration 요소 (Format) ViewDefinitions 요소 (Format) View 요소 (format) 컨트롤 요소 컨트롤에 대 한 컨트롤의 요소 (format) CustomControl 요소에 대 한 컨트롤의 컨트롤에 대 한 컨트롤의 요소입니다. view (format) EntrySelectedBy의 컨트롤에 대 한 CustomEntries 요소의 항목 요소에 대 한 참조 요소 뷰 (format)의 컨트롤에 대 한 SelectionCondition 요소에 대 한 컨트롤</span><span class="sxs-lookup"><span data-stu-id="6717e-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format) TypeName Element for SelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6717e-106">구문</span><span class="sxs-lookup"><span data-stu-id="6717e-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="6717e-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="6717e-107">Attributes and Elements</span></span>

<span data-ttu-id="6717e-108">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `TypeName` .</span><span class="sxs-lookup"><span data-stu-id="6717e-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6717e-109">특성</span><span class="sxs-lookup"><span data-stu-id="6717e-109">Attributes</span></span>

<span data-ttu-id="6717e-110">없음</span><span class="sxs-lookup"><span data-stu-id="6717e-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6717e-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="6717e-111">Child Elements</span></span>

<span data-ttu-id="6717e-112">없음</span><span class="sxs-lookup"><span data-stu-id="6717e-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="6717e-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="6717e-113">Parent Elements</span></span>

|<span data-ttu-id="6717e-114">요소</span><span class="sxs-lookup"><span data-stu-id="6717e-114">Element</span></span>|<span data-ttu-id="6717e-115">설명</span><span class="sxs-lookup"><span data-stu-id="6717e-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6717e-116">View에 대한 Controls의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="6717e-116">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="6717e-117">컨트롤 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="6717e-117">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="6717e-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="6717e-118">Text Value</span></span>

<span data-ttu-id="6717e-119">.NET 형식의 정규화 된 이름 (예:)을 지정 합니다 `System.IO.DirectoryInfo` .</span><span class="sxs-lookup"><span data-stu-id="6717e-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="6717e-120">설명</span><span class="sxs-lookup"><span data-stu-id="6717e-120">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="6717e-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6717e-121">See Also</span></span>

[<span data-ttu-id="6717e-122">View에 대한 Controls의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="6717e-122">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[<span data-ttu-id="6717e-123">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="6717e-123">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
