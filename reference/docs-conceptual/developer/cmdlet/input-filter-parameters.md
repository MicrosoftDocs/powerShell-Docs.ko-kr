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
ms.openlocfilehash: 553878c34e74129f9876cca25a5393cb0d53445a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364392"
---
# <a name="input-filter-parameters"></a><span data-ttu-id="b6bbb-102">입력 필터 매개 변수</span><span class="sxs-lookup"><span data-stu-id="b6bbb-102">Input Filter Parameters</span></span>

<span data-ttu-id="b6bbb-103">Cmdlet은 cmdlet에 영향을 주는 입력 개체 집합을 필터링 하는 `Filter`, `Include`및 `Exclude` 매개 변수를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6bbb-103">A cmdlet can define `Filter`, `Include`, and `Exclude` parameters that filter the set of input objects that the cmdlet affects.</span></span>

<span data-ttu-id="b6bbb-104">일반적으로 입력 개체 집합은 `InputObject`, `Path`또는 `Name` 매개 변수에 의해 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6bbb-104">Typically, the set of input objects is specified by an `InputObject`, `Path`, or `Name` parameter.</span></span> <span data-ttu-id="b6bbb-105">예를 들어 cmdlet은 와일드 카드 문자를 사용 하 여 여러 경로를 허용 하는 `Path` 매개 변수를 가질 수 있으며 각 경로는 입력 개체를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="b6bbb-105">For example, a cmdlet can have a `Path` parameter that accepts multiple paths by using wildcard characters, and each path points to an input object.</span></span> <span data-ttu-id="b6bbb-106">`Filter`, `Include`및 `Exclude` 매개 변수를 함께 사용 하 여 cmdlet이 호출 될 때마다 작동 하는 경로를 보다 구체적으로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6bbb-106">Used together, the `Filter`, `Include`, and `Exclude` parameters further qualify the paths the cmdlet works on each time it is invoked.</span></span>

## <a name="include-and-exclude-parameters"></a><span data-ttu-id="b6bbb-107">매개 변수 포함 및 제외</span><span class="sxs-lookup"><span data-stu-id="b6bbb-107">Include and Exclude Parameters</span></span>

<span data-ttu-id="b6bbb-108">`Include` 및 `Exclude` 매개 변수는 cmdlet으로 전달 되는 입력 개체 집합에서 제외 되거나 포함 되는 개체를 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6bbb-108">The `Include` and `Exclude` parameters identify the objects that are included or excluded from the set of input objects passed to the cmdlet.</span></span> <span data-ttu-id="b6bbb-109">표준 와일드 카드 언어로 필터를 표현할 수 있는 경우이 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6bbb-109">Use these parameters when the filter can be expressed in the standard wildcard language.</span></span> <span data-ttu-id="b6bbb-110">와일드 카드 문자에 대 한 자세한 내용은 [Cmdlet 매개 변수에서 와일드 카드 지원](./supporting-wildcard-characters-in-cmdlet-parameters.md)을 참조 하세요. `Include` 매개 변수에는 이름이 포함 필터와 일치 하는 모든 개체가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6bbb-110">(For more information about wildcard characters, see [Supporting Wildcards in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md).) The `Include` parameter includes all the objects whose names match the inclusion filter.</span></span> <span data-ttu-id="b6bbb-111">`Exclude` 매개 변수는 이름이 필터와 일치 하는 모든 개체를 제외 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6bbb-111">The `Exclude` parameter excludes all the objects whose names match the filter.</span></span>

## <a name="filter-parameter"></a><span data-ttu-id="b6bbb-112">필터 매개 변수</span><span class="sxs-lookup"><span data-stu-id="b6bbb-112">Filter Parameter</span></span>

<span data-ttu-id="b6bbb-113">`Filter` 매개 변수는 표준 와일드 카드 언어로 표현 되지 않는 필터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6bbb-113">The `Filter` parameter specifies a filter that is not expressed in the standard wildcard language.</span></span> <span data-ttu-id="b6bbb-114">예를 들어 ADSI (Active Directory Service Interface) 또는 SQL 필터는 `Filter` 매개 변수를 통해 cmdlet에 전달 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6bbb-114">For example, Active Directory Service Interfaces (ADSI) or SQL filters might be passed to the cmdlet through its `Filter` parameter.</span></span> <span data-ttu-id="b6bbb-115">Windows PowerShell에서 제공 하는 cmdlet에서는 cmdlet을 사용 하 여 데이터 저장소에 액세스 하는 Windows PowerShell 공급자가 이러한 필터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6bbb-115">In the cmdlets provided by Windows PowerShell, these filters are specified by the Windows PowerShell providers that use the cmdlet to access a data store.</span></span> <span data-ttu-id="b6bbb-116">각 공급자는 일반적으로 자체 필터를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6bbb-116">Each provider typically defines its own filter.</span></span>

## <a name="filtering-if-no-set-of-input-objects-is-specified"></a><span data-ttu-id="b6bbb-117">입력 개체 집합이 지정 되지 않은 경우 필터링</span><span class="sxs-lookup"><span data-stu-id="b6bbb-117">Filtering If No Set of Input Objects Is Specified</span></span>

<span data-ttu-id="b6bbb-118">입력 개체 집합이 지정 되지 않은 경우 일반적으로 모든 개체에 대해 필터링 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="b6bbb-118">If no set of input objects is specified, this typically means to filter against all objects.</span></span> <span data-ttu-id="b6bbb-119">자세한 내용은[Get Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b6bbb-119">For more information, see[Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process).</span></span>

## <a name="see-also"></a><span data-ttu-id="b6bbb-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b6bbb-120">See Also</span></span>

<span data-ttu-id="b6bbb-121">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="b6bbb-121">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>