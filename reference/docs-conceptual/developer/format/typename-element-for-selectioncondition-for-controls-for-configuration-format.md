---
title: 구성 (형식)에 대 한 컨트롤의 SelectionCondition에 대 한 TypeName 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 2db856d1b84dded315204d8c8574ae86acb63515
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780069"
---
# <a name="typename-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="d195c-102">Configuration에 대한 Controls의 SelectionCondition에 대한 TypeName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="d195c-102">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="d195c-103">조건을 트리거하는 .NET 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d195c-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="d195c-104">이 요소는 서식 파일의 모든 뷰에서 사용할 수 있는 공용 컨트롤을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d195c-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="d195c-105">Configuration 요소 (format) 컨트롤의 요소 구성 (format) CustomControl 요소에 대 한 컨트롤의 요소 구성 (format) CustomEntries 요소에 대 한 CustomControl 요소에 대 한 구성 (형식) Customentries 요소 구성에 대 한 컨트롤 (형식) EntrySelectedBy 요소 구성 (형식)에 대 한 컨트롤에 대 한 customentries에 대 한 컨트롤에 대 한 Customentries에 대 한 컨트롤에 대 한 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="d195c-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Controls for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format) TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d195c-106">구문</span><span class="sxs-lookup"><span data-stu-id="d195c-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="d195c-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="d195c-107">Attributes and Elements</span></span>

<span data-ttu-id="d195c-108">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `TypeName` .</span><span class="sxs-lookup"><span data-stu-id="d195c-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d195c-109">특성</span><span class="sxs-lookup"><span data-stu-id="d195c-109">Attributes</span></span>

<span data-ttu-id="d195c-110">없음</span><span class="sxs-lookup"><span data-stu-id="d195c-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d195c-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="d195c-111">Child Elements</span></span>

<span data-ttu-id="d195c-112">없음</span><span class="sxs-lookup"><span data-stu-id="d195c-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d195c-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="d195c-113">Parent Elements</span></span>

|<span data-ttu-id="d195c-114">요소</span><span class="sxs-lookup"><span data-stu-id="d195c-114">Element</span></span>|<span data-ttu-id="d195c-115">설명</span><span class="sxs-lookup"><span data-stu-id="d195c-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d195c-116">구성 (형식)에 대 한 CustomEntry에 대해 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="d195c-116">SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="d195c-117">컨트롤 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="d195c-117">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d195c-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="d195c-118">Text Value</span></span>

<span data-ttu-id="d195c-119">.NET 형식의 정규화 된 이름 (예:)을 지정 합니다 `System.IO.DirectoryInfo` .</span><span class="sxs-lookup"><span data-stu-id="d195c-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="d195c-120">설명</span><span class="sxs-lookup"><span data-stu-id="d195c-120">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="d195c-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d195c-121">See Also</span></span>

[<span data-ttu-id="d195c-122">구성 (형식)에 대 한 CustomEntry에 대해 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="d195c-122">SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="d195c-123">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="d195c-123">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
