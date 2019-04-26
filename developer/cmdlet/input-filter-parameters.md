---
title: 필터 매개 변수를 입력 합니다. | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e45929d1-bbb4-4dc6-892f-f9eacdb1c84c
caps.latest.revision: 8
ms.openlocfilehash: 553878c34e74129f9876cca25a5393cb0d53445a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067691"
---
# <a name="input-filter-parameters"></a><span data-ttu-id="6c328-102">입력 필터 매개 변수</span><span class="sxs-lookup"><span data-stu-id="6c328-102">Input Filter Parameters</span></span>

<span data-ttu-id="6c328-103">Cmdlet을 정의할 수 있습니다 `Filter`, `Include`, 및 `Exclude` 매개 변수를 cmdlet에 영향을 주는 입력된 개체 집합을 필터링 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c328-103">A cmdlet can define `Filter`, `Include`, and `Exclude` parameters that filter the set of input objects that the cmdlet affects.</span></span>

<span data-ttu-id="6c328-104">입력된 개체 집합으로 지정 됩니다는 일반적으로 `InputObject`, `Path`, 또는 `Name` 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="6c328-104">Typically, the set of input objects is specified by an `InputObject`, `Path`, or `Name` parameter.</span></span> <span data-ttu-id="6c328-105">예를 들어 cmdlet을 가질 수 있습니다는 `Path` 와일드 카드 문자 및 각 경로 지점을 입력 개체를 사용 하 여 여러 경로 허용 하는 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="6c328-105">For example, a cmdlet can have a `Path` parameter that accepts multiple paths by using wildcard characters, and each path points to an input object.</span></span> <span data-ttu-id="6c328-106">함께 사용 합니다 `Filter`, `Include`, 및 `Exclude` 매개 변수 추가 cmdlet를 호출할 때마다에서 작동 하는 경로 정규화 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c328-106">Used together, the `Filter`, `Include`, and `Exclude` parameters further qualify the paths the cmdlet works on each time it is invoked.</span></span>

## <a name="include-and-exclude-parameters"></a><span data-ttu-id="6c328-107">Include 및 Exclude 매개 변수</span><span class="sxs-lookup"><span data-stu-id="6c328-107">Include and Exclude Parameters</span></span>

<span data-ttu-id="6c328-108">합니다 `Include` 고 `Exclude` 매개 변수를 cmdlet으로 전달 하는 입력된 개체 집합에서 제외 되거나 포함 되는 개체를 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c328-108">The `Include` and `Exclude` parameters identify the objects that are included or excluded from the set of input objects passed to the cmdlet.</span></span> <span data-ttu-id="6c328-109">필터는 표준 와일드 카드 언어로 표현 될 수 있습니다 하는 경우 이러한 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c328-109">Use these parameters when the filter can be expressed in the standard wildcard language.</span></span> <span data-ttu-id="6c328-110">(와일드 카드 문자에 대 한 자세한 내용은 참조 하세요. [Cmdlet 매개 변수에서 와일드 카드를 지 원하는](./supporting-wildcard-characters-in-cmdlet-parameters.md).) `Include` 매개 변수 이름이 포함 필터와 일치 하는 모든 개체를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c328-110">(For more information about wildcard characters, see [Supporting Wildcards in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md).) The `Include` parameter includes all the objects whose names match the inclusion filter.</span></span> <span data-ttu-id="6c328-111">`Exclude` 매개 변수 이름이 필터와 일치 하는 모든 개체를 제외 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c328-111">The `Exclude` parameter excludes all the objects whose names match the filter.</span></span>

## <a name="filter-parameter"></a><span data-ttu-id="6c328-112">Filter 매개 변수</span><span class="sxs-lookup"><span data-stu-id="6c328-112">Filter Parameter</span></span>

<span data-ttu-id="6c328-113">`Filter` 매개 변수는 표준 와일드 카드 언어로 표시 되지 않을 필터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c328-113">The `Filter` parameter specifies a filter that is not expressed in the standard wildcard language.</span></span> <span data-ttu-id="6c328-114">예를 들어, 서비스 인터페이스 ADSI (Active Directory) 또는 SQL 필터 전달 될 수 있는 cmdlet을 통해 해당 `Filter` 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="6c328-114">For example, Active Directory Service Interfaces (ADSI) or SQL filters might be passed to the cmdlet through its `Filter` parameter.</span></span> <span data-ttu-id="6c328-115">Windows PowerShell에서 제공 하는 cmdlet에 이러한 필터는 cmdlet을 사용 하 여 데이터 저장소에 액세스 하는 Windows PowerShell 공급자에 의해 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c328-115">In the cmdlets provided by Windows PowerShell, these filters are specified by the Windows PowerShell providers that use the cmdlet to access a data store.</span></span> <span data-ttu-id="6c328-116">각 공급자는 일반적으로 자체 필터를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="6c328-116">Each provider typically defines its own filter.</span></span>

## <a name="filtering-if-no-set-of-input-objects-is-specified"></a><span data-ttu-id="6c328-117">필터링 입력된 개체 집합이 지정 된 경우</span><span class="sxs-lookup"><span data-stu-id="6c328-117">Filtering If No Set of Input Objects Is Specified</span></span>

<span data-ttu-id="6c328-118">입력된 개체 집합이 지정 된 경우 일반적으로 즉, 모든 개체에 대해 필터링 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c328-118">If no set of input objects is specified, this typically means to filter against all objects.</span></span> <span data-ttu-id="6c328-119">자세한 내용은[Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process)합니다.</span><span class="sxs-lookup"><span data-stu-id="6c328-119">For more information, see[Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process).</span></span>

## <a name="see-also"></a><span data-ttu-id="6c328-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6c328-120">See Also</span></span>

<span data-ttu-id="6c328-121">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="6c328-121">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>