---
ms.date: 09/13/2016
ms.topic: reference
title: Cmdlet 매개 변수
description: Cmdlet 매개 변수
ms.openlocfilehash: 1ab495cb674f6b2cd769c3f64d899aec67704216
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92668272"
---
# <a name="cmdlet-parameters"></a><span data-ttu-id="881ce-103">Cmdlet 매개 변수</span><span class="sxs-lookup"><span data-stu-id="881ce-103">Cmdlet Parameters</span></span>

<span data-ttu-id="881ce-104">Cmdlet 매개 변수는 cmdlet이 입력을 받을 수 있도록 하는 메커니즘을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="881ce-104">Cmdlet parameters provide the mechanism that allows a cmdlet to accept input.</span></span> <span data-ttu-id="881ce-105">매개 변수는 명령줄에서 직접 입력을 받을 수 있고 파이프라인을 통해 cmdlet에 전달 된 개체에서 이러한 매개 변수의 인수 ( *값* 이 라고도 함)는 cmdlet이 허용 하는 입력, cmdlet에서 해당 작업을 수행 하는 방법 및 cmdlet이 파이프라인으로 반환 하는 데이터를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="881ce-105">Parameters can accept input directly from the command line, or from objects passed to the cmdlet through the pipeline, The arguments (also known as *values*) of these parameters can specify the input that the cmdlet accepts, how the cmdlet should perform its actions, and the data that the cmdlet returns to the pipeline.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="881ce-106">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="881ce-106">In This Section</span></span>

<span data-ttu-id="881ce-107">[속성을 매개 변수로 선언](./declaring-properties-as-parameters.md) Cmdlet의 매개 변수를 선언 하기 전에 이해 해야 하는 기본적인 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="881ce-107">[Declaring Properties as Parameters](./declaring-properties-as-parameters.md) Provides basic information you must understand before you declare the parameters of a cmdlet.</span></span>

<span data-ttu-id="881ce-108">[Cmdlet 매개 변수의 유형](./types-of-cmdlet-parameters.md) Cmdlet에서 선언할 수 있는 다양 한 형식의 매개 변수를 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="881ce-108">[Types of Cmdlet Parameters](./types-of-cmdlet-parameters.md) Describes the different types of parameters that you can declare in cmdlets.</span></span>

<span data-ttu-id="881ce-109">[Cmdlet 매개 변수 이름 및 기능 지침](./standard-cmdlet-parameter-names-and-types.md) 표준 매개 변수의 이름, 권장 데이터 형식 및 기능을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="881ce-109">[Cmdlet Parameter Name and Functionality Guidelines](./standard-cmdlet-parameter-names-and-types.md) Discusses the names, recommended data type, and functionality of standard parameters.</span></span>

<span data-ttu-id="881ce-110">[매개 변수 별칭](./parameter-aliases.md) 매개 변수에 대해 정의할 수 있는 별칭에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="881ce-110">[Parameter Aliases](./parameter-aliases.md) Discusses the aliases that you can define for parameters.</span></span>

<span data-ttu-id="881ce-111">[일반 매개 변수 이름](./common-parameter-names.md) 이 항목에서는 Windows PowerShell에서 cmdlet에 추가 하는 매개 변수에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="881ce-111">[Common Parameter Names](./common-parameter-names.md) This topic describes the parameters that Windows PowerShell adds to cmdlets.</span></span>

<span data-ttu-id="881ce-112">[Cmdlet 매개 변수 집합](./cmdlet-parameter-sets.md) 매개 변수 집합을 사용 하 여 여러 시나리오에 대해 다른 작업을 수행할 수 있는 단일 cmdlet을 작성 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="881ce-112">[Cmdlet Parameter Sets](./cmdlet-parameter-sets.md) Discusses how parameter sets enable you to write a single cmdlet that can perform different actions for different scenarios.</span></span>

<span data-ttu-id="881ce-113">[Cmdlet 동적 매개 변수](./cmdlet-dynamic-parameters.md) 사용자가 특별 한 조건에서 사용할 수 있는 매개 변수에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="881ce-113">[Cmdlet Dynamic Parameters](./cmdlet-dynamic-parameters.md) Discusses parameters that are available to the user under special conditions.</span></span>

<span data-ttu-id="881ce-114">[Cmdlet 매개 변수에 와일드 카드 문자 지원](./supporting-wildcard-characters-in-cmdlet-parameters.md) 리소스 그룹에 대해 실행 될 cmdlet을 디자인할 때 와일드 카드 문자에 대 한 지원을 제공 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="881ce-114">[Supporting Wildcard Characters in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md) Describes how to provide support for wildcard characters when you design a cmdlet that will be run against a group of resources.</span></span>

<span data-ttu-id="881ce-115">[매개 변수 입력 유효성 검사](./validating-parameter-input.md) Windows PowerShell에서 cmdlet 매개 변수에 전달 된 인수의 유효성을 검사 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="881ce-115">[Validating Parameter Input](./validating-parameter-input.md) Describes how Windows PowerShell validates the arguments passed to cmdlet parameters.</span></span>

<span data-ttu-id="881ce-116">[입력 필터 매개 변수](./input-filter-parameters.md) `Filter` `Include` `Exclude` Cmdlet이 적용 되는 입력 개체 집합을 필터링 하는, 및 매개 변수에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="881ce-116">[Input Filter Parameters](./input-filter-parameters.md) Discusses the `Filter`, `Include`, and `Exclude` parameters that filter the set of input objects that the cmdlet affects.</span></span>

## <a name="related-sections"></a><span data-ttu-id="881ce-117">관련 단원</span><span class="sxs-lookup"><span data-stu-id="881ce-117">Related Sections</span></span>

[<span data-ttu-id="881ce-118">매개 변수 입력 유효성을 검사하는 방법</span><span class="sxs-lookup"><span data-stu-id="881ce-118">How to Validate Parameter Input</span></span>](./how-to-validate-parameter-input.md)

## <a name="see-also"></a><span data-ttu-id="881ce-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="881ce-119">See Also</span></span>

[<span data-ttu-id="881ce-120">Parameter 특성 선언</span><span class="sxs-lookup"><span data-stu-id="881ce-120">Parameter Attribute Declaration</span></span>](./parameter-attribute-declaration.md)

[<span data-ttu-id="881ce-121">Windows PowerShell cmdlet</span><span class="sxs-lookup"><span data-stu-id="881ce-121">Windows PowerShell Cmdlets</span></span>](./cmdlet-overview.md)
