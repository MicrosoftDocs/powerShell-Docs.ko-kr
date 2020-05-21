---
title: 입력 필터 매개 변수 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e45929d1-bbb4-4dc6-892f-f9eacdb1c84c
caps.latest.revision: 8
ms.openlocfilehash: 7a1582031d27f78bad069f5539408312ccabb3f2
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83563882"
---
# <a name="input-filter-parameters"></a><span data-ttu-id="21947-102">입력 필터 매개 변수</span><span class="sxs-lookup"><span data-stu-id="21947-102">Input Filter Parameters</span></span>

<span data-ttu-id="21947-103">Cmdlet은 cmdlet이 `Filter` `Include` `Exclude` 적용 되는 입력 개체 집합을 필터링 하는, 및 매개 변수를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21947-103">A cmdlet can define `Filter`, `Include`, and `Exclude` parameters that filter the set of input objects that the cmdlet affects.</span></span>

<span data-ttu-id="21947-104">일반적으로 입력 개체 집합은 `InputObject` , `Path` 또는 매개 변수에 의해 지정 됩니다 `Name` .</span><span class="sxs-lookup"><span data-stu-id="21947-104">Typically, the set of input objects is specified by an `InputObject`, `Path`, or `Name` parameter.</span></span> <span data-ttu-id="21947-105">예를 들어 cmdlet은 `Path` 와일드 카드 문자를 사용 하 여 여러 경로를 허용 하는 매개 변수를 가질 수 있으며 각 경로는 입력 개체를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="21947-105">For example, a cmdlet can have a `Path` parameter that accepts multiple paths by using wildcard characters, and each path points to an input object.</span></span> <span data-ttu-id="21947-106">, 및 매개 변수를 함께 사용 하는 경우 `Filter` `Include` `Exclude` cmdlet이 호출 될 때마다 작동 하는 경로를 더 합니다.</span><span class="sxs-lookup"><span data-stu-id="21947-106">Used together, the `Filter`, `Include`, and `Exclude` parameters further qualify the paths the cmdlet works on each time it is invoked.</span></span>

## <a name="include-and-exclude-parameters"></a><span data-ttu-id="21947-107">매개 변수 포함 및 제외</span><span class="sxs-lookup"><span data-stu-id="21947-107">Include and Exclude Parameters</span></span>

<span data-ttu-id="21947-108">`Include`및 `Exclude` 매개 변수는 cmdlet으로 전달 되는 입력 개체 집합에서 제외 되거나 포함 되는 개체를 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="21947-108">The `Include` and `Exclude` parameters identify the objects that are included or excluded from the set of input objects passed to the cmdlet.</span></span> <span data-ttu-id="21947-109">표준 와일드 카드 언어로 필터를 표현할 수 있는 경우이 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="21947-109">Use these parameters when the filter can be expressed in the standard wildcard language.</span></span> <span data-ttu-id="21947-110">와일드 카드 문자에 대 한 자세한 내용은 [Cmdlet 매개 변수에서 와일드 카드 지원](./supporting-wildcard-characters-in-cmdlet-parameters.md)을 참조 하세요. `Include`매개 변수는 이름이 포함 필터와 일치 하는 모든 개체를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="21947-110">(For more information about wildcard characters, see [Supporting Wildcards in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md).) The `Include` parameter includes all the objects whose names match the inclusion filter.</span></span> <span data-ttu-id="21947-111">`Exclude`매개 변수는 이름이 필터와 일치 하는 모든 개체를 제외 합니다.</span><span class="sxs-lookup"><span data-stu-id="21947-111">The `Exclude` parameter excludes all the objects whose names match the filter.</span></span>

## <a name="filter-parameter"></a><span data-ttu-id="21947-112">필터 매개 변수</span><span class="sxs-lookup"><span data-stu-id="21947-112">Filter Parameter</span></span>

<span data-ttu-id="21947-113">`Filter`매개 변수는 표준 와일드 카드 언어로 표현 되지 않는 필터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="21947-113">The `Filter` parameter specifies a filter that is not expressed in the standard wildcard language.</span></span> <span data-ttu-id="21947-114">예를 들어 ADSI (Active Directory Service Interface) 또는 SQL 필터는 매개 변수를 통해 cmdlet에 전달 될 수 있습니다 `Filter` .</span><span class="sxs-lookup"><span data-stu-id="21947-114">For example, Active Directory Service Interfaces (ADSI) or SQL filters might be passed to the cmdlet through its `Filter` parameter.</span></span> <span data-ttu-id="21947-115">Windows PowerShell에서 제공 하는 cmdlet에서는 cmdlet을 사용 하 여 데이터 저장소에 액세스 하는 Windows PowerShell 공급자가 이러한 필터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="21947-115">In the cmdlets provided by Windows PowerShell, these filters are specified by the Windows PowerShell providers that use the cmdlet to access a data store.</span></span> <span data-ttu-id="21947-116">각 공급자는 일반적으로 자체 필터를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="21947-116">Each provider typically defines its own filter.</span></span>

## <a name="filtering-if-no-set-of-input-objects-is-specified"></a><span data-ttu-id="21947-117">입력 개체 집합이 지정 되지 않은 경우 필터링</span><span class="sxs-lookup"><span data-stu-id="21947-117">Filtering If No Set of Input Objects Is Specified</span></span>

<span data-ttu-id="21947-118">입력 개체 집합이 지정 되지 않은 경우 일반적으로 모든 개체에 대해 필터링 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="21947-118">If no set of input objects is specified, this typically means to filter against all objects.</span></span> <span data-ttu-id="21947-119">자세한 내용은[Get Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="21947-119">For more information, see[Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process).</span></span>

## <a name="see-also"></a><span data-ttu-id="21947-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="21947-120">See Also</span></span>

[<span data-ttu-id="21947-121">Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="21947-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
