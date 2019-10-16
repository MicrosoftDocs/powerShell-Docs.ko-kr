---
title: View 컨트롤의 SelectionCondition에 대 한 TypeName 요소 (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7141aefc-6656-4c52-8a9c-c2bfc9c87be9
caps.latest.revision: 6
ms.openlocfilehash: 7a697c286ec9efe750930739cdfa2580003365dd
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361602"
---
# <a name="typename-element-for-selectioncondition-for-controls-for-view-format"></a><span data-ttu-id="70a18-102">View에 대한 Controls의 SelectionCondition에 대한 TypeName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="70a18-102">TypeName Element for SelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="70a18-103">조건을 트리거하는 .NET 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="70a18-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="70a18-104">이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="70a18-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="70a18-105">Configuration 요소 (Format) ViewDefinitions 요소 (Format) View 요소 (format) 컨트롤 요소 컨트롤에 대 한 컨트롤의 요소 (format) 컨트롤 요소 뷰 (format) CustomEntries 요소에 대 한 컨트롤에 대 한 컨트롤의 요소입니다. View (format) CustomControl 컨트롤에 대 한 컨트롤의 CustomEntry 요소에 대 한 컨트롤에 대 한 Customentry 요소에 대 한 컨트롤의 CustomEntry 요소 Format) View 컨트롤의 SelectionCondition에 대 한 TypeName 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="70a18-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format) TypeName Element for SelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="70a18-106">구문</span><span class="sxs-lookup"><span data-stu-id="70a18-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="70a18-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="70a18-107">Attributes and Elements</span></span>

<span data-ttu-id="70a18-108">다음 섹션에서는 `TypeName` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="70a18-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="70a18-109">특성</span><span class="sxs-lookup"><span data-stu-id="70a18-109">Attributes</span></span>

<span data-ttu-id="70a18-110">없음</span><span class="sxs-lookup"><span data-stu-id="70a18-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="70a18-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="70a18-111">Child Elements</span></span>

<span data-ttu-id="70a18-112">없음</span><span class="sxs-lookup"><span data-stu-id="70a18-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="70a18-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="70a18-113">Parent Elements</span></span>

|<span data-ttu-id="70a18-114">요소</span><span class="sxs-lookup"><span data-stu-id="70a18-114">Element</span></span>|<span data-ttu-id="70a18-115">설명</span><span class="sxs-lookup"><span data-stu-id="70a18-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="70a18-116">보기의 컨트롤에 대해 EntrySelectedBy의 SelectionCondition 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="70a18-116">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="70a18-117">컨트롤 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="70a18-117">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="70a18-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="70a18-118">Text Value</span></span>

<span data-ttu-id="70a18-119">.NET 형식의 정규화 된 이름 (예: `System.IO.DirectoryInfo`)을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="70a18-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="70a18-120">설명</span><span class="sxs-lookup"><span data-stu-id="70a18-120">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="70a18-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="70a18-121">See Also</span></span>

[<span data-ttu-id="70a18-122">보기의 컨트롤에 대해 EntrySelectedBy의 SelectionCondition 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="70a18-122">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[<span data-ttu-id="70a18-123">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="70a18-123">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
