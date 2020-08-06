---
title: EnumerableExpansion (형식)에 대 한 EntrySelectedBy의 TypeName 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 670aeb0986b07c8b7834a9f4f9510f1757a62186
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785084"
---
# <a name="typename-element-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="8bea6-102">EnumerableExpansion의 EntrySelectedBy에 대한 TypeName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="8bea6-102">TypeName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="8bea6-103">이 정의에 의해 확장 되는 .NET 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bea6-103">Specifies a .NET type that is expanded by this definition.</span></span> <span data-ttu-id="8bea6-104">이 요소는 기본 설정을 정의할 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8bea6-104">This element is used when defining a default settings.</span></span>

<span data-ttu-id="8bea6-105">Configuration 요소 (Format) DefaultSettings 요소 (format) enumerableexpansions 요소 (format) enumerableexpansions 요소 (format)에 대 한 EntrySelectedBy 요소에 대 한 ' enumerableexpansions (형식)</span><span class="sxs-lookup"><span data-stu-id="8bea6-105">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) TypeName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8bea6-106">구문</span><span class="sxs-lookup"><span data-stu-id="8bea6-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="8bea6-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="8bea6-107">Attributes and Elements</span></span>

<span data-ttu-id="8bea6-108">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `TypeName` .</span><span class="sxs-lookup"><span data-stu-id="8bea6-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8bea6-109">특성</span><span class="sxs-lookup"><span data-stu-id="8bea6-109">Attributes</span></span>

<span data-ttu-id="8bea6-110">없음</span><span class="sxs-lookup"><span data-stu-id="8bea6-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8bea6-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="8bea6-111">Child Elements</span></span>

<span data-ttu-id="8bea6-112">없음</span><span class="sxs-lookup"><span data-stu-id="8bea6-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8bea6-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="8bea6-113">Parent Elements</span></span>

|<span data-ttu-id="8bea6-114">요소</span><span class="sxs-lookup"><span data-stu-id="8bea6-114">Element</span></span>|<span data-ttu-id="8bea6-115">설명</span><span class="sxs-lookup"><span data-stu-id="8bea6-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8bea6-116">EnumerableExpansion에 대한 EntrySelectedBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="8bea6-116">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="8bea6-117">이 정의를 사용 하는 .NET 형식 또는이 정의를 사용 하기 위해 존재 해야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bea6-117">Defines the .NET types that use this definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="8bea6-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="8bea6-118">Text Value</span></span>

<span data-ttu-id="8bea6-119">.NET 형식의 정규화 된 이름 (예:)을 지정 합니다 `System.IO.DirectoryInfo` .</span><span class="sxs-lookup"><span data-stu-id="8bea6-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="8bea6-120">설명</span><span class="sxs-lookup"><span data-stu-id="8bea6-120">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="8bea6-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8bea6-121">See Also</span></span>

[<span data-ttu-id="8bea6-122">EnumerableExpansion에 대한 EntrySelectedBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="8bea6-122">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)

[<span data-ttu-id="8bea6-123">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="8bea6-123">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
