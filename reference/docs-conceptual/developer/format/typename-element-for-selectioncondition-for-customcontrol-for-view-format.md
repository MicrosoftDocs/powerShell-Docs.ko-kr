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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361592"
---
# <a name="typename-element-for-selectioncondition-for-customcontrol-for-view--format"></a><span data-ttu-id="3d537-102">View에 대한 CustomControl의 SelectionCondition에 대한 TypeName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="3d537-102">TypeName Element for SelectionCondition for CustomControl for View  (Format)</span></span>

<span data-ttu-id="3d537-103">조건을 트리거하는 .NET 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d537-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="3d537-104">이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3d537-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="3d537-105">Configuration 요소 (Format) ViewDefinitions element (Format) View 요소 (format) CustomControl 요소에 대 한 view (format) CustomEntries 요소에 대 한 CustomControl Format) CustomItem 요소에 대해 CustomControl for view (format) SelectionCondition 요소에 대 한 CustomControl for view (format) TypeName 요소에 대해 SelectionCondition for CustomControl for View (Format)</span><span class="sxs-lookup"><span data-stu-id="3d537-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format) TypeName Element for SelectionCondition for CustomControl for View  (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3d537-106">구문</span><span class="sxs-lookup"><span data-stu-id="3d537-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="3d537-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="3d537-107">Attributes and Elements</span></span>

<span data-ttu-id="3d537-108">다음 섹션에서는 `TypeName` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d537-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3d537-109">특성</span><span class="sxs-lookup"><span data-stu-id="3d537-109">Attributes</span></span>

<span data-ttu-id="3d537-110">없음</span><span class="sxs-lookup"><span data-stu-id="3d537-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3d537-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="3d537-111">Child Elements</span></span>

<span data-ttu-id="3d537-112">없음</span><span class="sxs-lookup"><span data-stu-id="3d537-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="3d537-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="3d537-113">Parent Elements</span></span>

|<span data-ttu-id="3d537-114">요소</span><span class="sxs-lookup"><span data-stu-id="3d537-114">Element</span></span>|<span data-ttu-id="3d537-115">설명</span><span class="sxs-lookup"><span data-stu-id="3d537-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3d537-116">CustomControl for View (Format)에 대해 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="3d537-116">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="3d537-117">컨트롤 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d537-117">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="3d537-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="3d537-118">Text Value</span></span>

<span data-ttu-id="3d537-119">.NET 형식의 정규화 된 이름 (예: `System.IO.DirectoryInfo`)을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d537-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="3d537-120">설명</span><span class="sxs-lookup"><span data-stu-id="3d537-120">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="3d537-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3d537-121">See Also</span></span>

[<span data-ttu-id="3d537-122">CustomControl for View (Format)에 대해 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="3d537-122">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="3d537-123">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="3d537-123">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
