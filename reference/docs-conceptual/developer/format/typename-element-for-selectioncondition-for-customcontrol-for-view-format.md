---
title: CustomControl에 대 한 SelectionCondition의 TypeName 요소 (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2c65171-4d4c-46a9-a545-591df058acd1
caps.latest.revision: 7
ms.openlocfilehash: 00e9ae0916dd6d22602b99b201c9c4b7e549dc48
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361592"
---
# <a name="typename-element-for-selectioncondition-for-customcontrol-for-view--format"></a><span data-ttu-id="f7b78-102">View에 대한 CustomControl의 SelectionCondition에 대한 TypeName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="f7b78-102">TypeName Element for SelectionCondition for CustomControl for View  (Format)</span></span>

<span data-ttu-id="f7b78-103">조건을 트리거하는 .NET 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7b78-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="f7b78-104">이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7b78-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="f7b78-105">Configuration 요소 (Format) ViewDefinitions element (Format) View 요소 (format) CustomControl 요소에 대 한 view (format) CustomEntries 요소에 대 한 CustomControl Format) CustomItem 요소에 대해 CustomControl for view (format) SelectionCondition 요소에 대 한 CustomControl for view (format) TypeName 요소에 대해 SelectionCondition for CustomControl for View (Format)</span><span class="sxs-lookup"><span data-stu-id="f7b78-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format) TypeName Element for SelectionCondition for CustomControl for View  (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f7b78-106">구문</span><span class="sxs-lookup"><span data-stu-id="f7b78-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="f7b78-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="f7b78-107">Attributes and Elements</span></span>

<span data-ttu-id="f7b78-108">다음 섹션에서는 특성, 자식 요소 및 `TypeName` 요소의 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7b78-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f7b78-109">특성</span><span class="sxs-lookup"><span data-stu-id="f7b78-109">Attributes</span></span>

<span data-ttu-id="f7b78-110">없음</span><span class="sxs-lookup"><span data-stu-id="f7b78-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f7b78-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="f7b78-111">Child Elements</span></span>

<span data-ttu-id="f7b78-112">없음</span><span class="sxs-lookup"><span data-stu-id="f7b78-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f7b78-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="f7b78-113">Parent Elements</span></span>

|<span data-ttu-id="f7b78-114">요소</span><span class="sxs-lookup"><span data-stu-id="f7b78-114">Element</span></span>|<span data-ttu-id="f7b78-115">설명</span><span class="sxs-lookup"><span data-stu-id="f7b78-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f7b78-116">CustomControl for View (Format)에 대해 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="f7b78-116">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="f7b78-117">컨트롤 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7b78-117">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f7b78-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="f7b78-118">Text Value</span></span>

<span data-ttu-id="f7b78-119">`System.IO.DirectoryInfo`와 같은 .NET 형식의 정규화 된 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7b78-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="f7b78-120">설명</span><span class="sxs-lookup"><span data-stu-id="f7b78-120">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="f7b78-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f7b78-121">See Also</span></span>

[<span data-ttu-id="f7b78-122">CustomControl for View (Format)에 대해 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="f7b78-122">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="f7b78-123">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="f7b78-123">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
