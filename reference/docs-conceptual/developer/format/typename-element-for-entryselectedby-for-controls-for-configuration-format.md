---
title: 구성 (형식)의 컨트롤에 대 한 EntrySelectedBy의 TypeName 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 994cd368872392abe47b4e9422c661cd8c03e05c
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783350"
---
# <a name="typename-element-for-entryselectedby-for-controls-for-configuration-format"></a><span data-ttu-id="521ad-102">Configuration에 대한 Controls의 EntrySelectedBy에 대한 TypeName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="521ad-102">TypeName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

<span data-ttu-id="521ad-103">컨트롤의이 정의를 사용 하는 .NET 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="521ad-103">Specifies a .NET type that uses this definition of the control.</span></span> <span data-ttu-id="521ad-104">이 요소는 서식 파일의 모든 뷰에서 사용할 수 있는 공용 컨트롤을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="521ad-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="521ad-105">구성 요소 (format) 컨트롤 요소 구성 (format) CustomControl 요소에 대 한 컨트롤 요소 구성 (형식)의 CustomControl에 대 한 CustomEntries 요소 구성 (형식)의 컨트롤에 대 한 CustomControl의 Customentries 요소 구성 (형식)에 대 한 컨트롤에 대 한 컨트롤의 Customentries 요소 구성 (형식)에 대 한 컨트롤</span><span class="sxs-lookup"><span data-stu-id="521ad-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) TypeName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="521ad-106">구문</span><span class="sxs-lookup"><span data-stu-id="521ad-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="521ad-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="521ad-107">Attributes and Elements</span></span>

<span data-ttu-id="521ad-108">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `TypeName` .</span><span class="sxs-lookup"><span data-stu-id="521ad-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="521ad-109">특성</span><span class="sxs-lookup"><span data-stu-id="521ad-109">Attributes</span></span>

<span data-ttu-id="521ad-110">없음</span><span class="sxs-lookup"><span data-stu-id="521ad-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="521ad-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="521ad-111">Child Elements</span></span>

<span data-ttu-id="521ad-112">없음</span><span class="sxs-lookup"><span data-stu-id="521ad-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="521ad-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="521ad-113">Parent Elements</span></span>

|<span data-ttu-id="521ad-114">요소</span><span class="sxs-lookup"><span data-stu-id="521ad-114">Element</span></span>|<span data-ttu-id="521ad-115">설명</span><span class="sxs-lookup"><span data-stu-id="521ad-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="521ad-116">Configuration에 대한 Controls의 CustomEntry에 대한 EntrySelectedBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="521ad-116">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="521ad-117">이 컨트롤 정의를 사용 하는 .NET 형식 또는이 정의를 사용 하기 위해 존재 해야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="521ad-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="521ad-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="521ad-118">Text Value</span></span>

<span data-ttu-id="521ad-119">.NET 형식의 정규화 된 이름 (예:)을 지정 합니다 `System.IO.DirectoryInfo` .</span><span class="sxs-lookup"><span data-stu-id="521ad-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="521ad-120">설명</span><span class="sxs-lookup"><span data-stu-id="521ad-120">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="521ad-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="521ad-121">See Also</span></span>

[<span data-ttu-id="521ad-122">Configuration에 대한 Controls의 CustomEntry에 대한 EntrySelectedBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="521ad-122">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="521ad-123">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="521ad-123">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
