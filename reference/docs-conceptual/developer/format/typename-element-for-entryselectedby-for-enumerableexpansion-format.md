---
title: EnumerableExpansion (형식)에 대 한 EntrySelectedBy의 TypeName 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c0506928-db92-4ec4-855f-6f3592a383ae
caps.latest.revision: 6
ms.openlocfilehash: 5ead806d956ebbef95eeffc42bb39ef784208017
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361752"
---
# <a name="typename-element-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="bd09d-102">EnumerableExpansion의 EntrySelectedBy에 대한 TypeName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="bd09d-102">TypeName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="bd09d-103">이 정의에 의해 확장 되는 .NET 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd09d-103">Specifies a .NET type that is expanded by this definition.</span></span> <span data-ttu-id="bd09d-104">이 요소는 기본 설정을 정의할 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bd09d-104">This element is used when defining a default settings.</span></span>

<span data-ttu-id="bd09d-105">Configuration 요소 (Format) DefaultSettings 요소 (format) EnumerableExpansions element (format) enumerableexpansions 요소 (format) Entry Selectedby 요소에 대 한 EnumerableExpansion (형식)</span><span class="sxs-lookup"><span data-stu-id="bd09d-105">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) TypeName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="bd09d-106">구문</span><span class="sxs-lookup"><span data-stu-id="bd09d-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="bd09d-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="bd09d-107">Attributes and Elements</span></span>

<span data-ttu-id="bd09d-108">다음 섹션에서는 특성, 자식 요소 및 `TypeName` 요소의 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd09d-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="bd09d-109">특성</span><span class="sxs-lookup"><span data-stu-id="bd09d-109">Attributes</span></span>

<span data-ttu-id="bd09d-110">없음</span><span class="sxs-lookup"><span data-stu-id="bd09d-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="bd09d-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="bd09d-111">Child Elements</span></span>

<span data-ttu-id="bd09d-112">없음</span><span class="sxs-lookup"><span data-stu-id="bd09d-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="bd09d-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="bd09d-113">Parent Elements</span></span>

|<span data-ttu-id="bd09d-114">요소</span><span class="sxs-lookup"><span data-stu-id="bd09d-114">Element</span></span>|<span data-ttu-id="bd09d-115">설명</span><span class="sxs-lookup"><span data-stu-id="bd09d-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bd09d-116">EnumerableExpansion (형식)에 대 한 EntrySelectedBy 요소</span><span class="sxs-lookup"><span data-stu-id="bd09d-116">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="bd09d-117">이 정의를 사용 하는 .NET 형식 또는이 정의를 사용 하기 위해 존재 해야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd09d-117">Defines the .NET types that use this definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="bd09d-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="bd09d-118">Text Value</span></span>

<span data-ttu-id="bd09d-119">`System.IO.DirectoryInfo`와 같은 .NET 형식의 정규화 된 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd09d-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="bd09d-120">설명</span><span class="sxs-lookup"><span data-stu-id="bd09d-120">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="bd09d-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bd09d-121">See Also</span></span>

[<span data-ttu-id="bd09d-122">EnumerableExpansion (형식)에 대 한 EntrySelectedBy 요소</span><span class="sxs-lookup"><span data-stu-id="bd09d-122">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)

[<span data-ttu-id="bd09d-123">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="bd09d-123">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
