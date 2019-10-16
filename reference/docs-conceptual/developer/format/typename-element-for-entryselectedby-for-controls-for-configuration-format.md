---
title: 구성 (형식)의 컨트롤에 대 한 EntrySelectedBy의 TypeName 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30bb1382-8c6b-4371-82e6-baf427fa0781
caps.latest.revision: 6
ms.openlocfilehash: cec8c5d76bded321ec1d6a1cd0409d7c88863c03
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368082"
---
# <a name="typename-element-for-entryselectedby-for-controls-for-configuration-format"></a><span data-ttu-id="3ab01-102">Configuration에 대한 Controls의 EntrySelectedBy에 대한 TypeName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="3ab01-102">TypeName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

<span data-ttu-id="3ab01-103">컨트롤의이 정의를 사용 하는 .NET 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3ab01-103">Specifies a .NET type that uses this definition of the control.</span></span> <span data-ttu-id="3ab01-104">이 요소는 서식 파일의 모든 뷰에서 사용할 수 있는 공용 컨트롤을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3ab01-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="3ab01-105">구성 요소 (format) 컨트롤 요소의 구성 (format) CustomControl 요소에 대 한 Control 요소 구성의 CustomControl에 대 한 구성 (형식) CustomEntries 요소 Format) CustomControl에 대 한 컨트롤의 CustomEntry 요소 구성 (형식)의 컨트롤에 대 한 customentry 요소 구성 (형식)에 대 한 컨트롤에 대 한 컨트롤의 CustomEntry 요소 구성 (형식)</span><span class="sxs-lookup"><span data-stu-id="3ab01-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) TypeName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3ab01-106">구문</span><span class="sxs-lookup"><span data-stu-id="3ab01-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="3ab01-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="3ab01-107">Attributes and Elements</span></span>

<span data-ttu-id="3ab01-108">다음 섹션에서는 `TypeName` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="3ab01-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3ab01-109">특성</span><span class="sxs-lookup"><span data-stu-id="3ab01-109">Attributes</span></span>

<span data-ttu-id="3ab01-110">없음</span><span class="sxs-lookup"><span data-stu-id="3ab01-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3ab01-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="3ab01-111">Child Elements</span></span>

<span data-ttu-id="3ab01-112">없음</span><span class="sxs-lookup"><span data-stu-id="3ab01-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="3ab01-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="3ab01-113">Parent Elements</span></span>

|<span data-ttu-id="3ab01-114">요소</span><span class="sxs-lookup"><span data-stu-id="3ab01-114">Element</span></span>|<span data-ttu-id="3ab01-115">설명</span><span class="sxs-lookup"><span data-stu-id="3ab01-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3ab01-116">구성에 대 한 컨트롤의 CustomEntry에 대 한 EntrySelectedBy 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="3ab01-116">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="3ab01-117">이 컨트롤 정의를 사용 하는 .NET 형식 또는이 정의를 사용 하기 위해 존재 해야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="3ab01-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="3ab01-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="3ab01-118">Text Value</span></span>

<span data-ttu-id="3ab01-119">.NET 형식의 정규화 된 이름 (예: `System.IO.DirectoryInfo`)을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3ab01-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="3ab01-120">설명</span><span class="sxs-lookup"><span data-stu-id="3ab01-120">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="3ab01-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3ab01-121">See Also</span></span>

[<span data-ttu-id="3ab01-122">구성에 대 한 컨트롤의 CustomEntry에 대 한 EntrySelectedBy 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="3ab01-122">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="3ab01-123">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="3ab01-123">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
