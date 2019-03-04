---
title: Cmdlet 매개 변수 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- optional parameters [PowerShell SDK]
- aliases [PowerShell SDK]
- parameter sets [PowerShell SDK]
- parameters [PowerShell SDK]
- mandatory parameters [PowerShell SDK]
- positional parameters [PowerShell SDK]
- cmdlets [PowerShell SDK], parameters
ms.assetid: 3f1cca5f-5b95-4bce-94a6-a22db1aefd47
caps.latest.revision: 23
ms.openlocfilehash: 914a10907bcf980eed8d7e2f819c382fe6b341ad
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853849"
---
# <a name="cmdlet-parameters"></a><span data-ttu-id="ffa23-102">Cmdlet 매개 변수</span><span class="sxs-lookup"><span data-stu-id="ffa23-102">Cmdlet Parameters</span></span>

<span data-ttu-id="ffa23-103">Cmdlet 매개 변수는 cmdlet의 입력을 받을 수 있는 메커니즘을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="ffa23-103">Cmdlet parameters provide the mechanism that allows a cmdlet to accept input.</span></span> <span data-ttu-id="ffa23-104">매개 변수는 명령줄에서 직접 또는 파이프라인을 인수를 통해 cmdlet에 전달 된 개체에서 입력을 허용할 수 (라고도 *값*) 이러한 매개 변수 cmdlet은 허용 하는 입력을 지정할 수는 방법 cmdlet은 cmdlet을 파이프라인에 반환 하는 데이터 및 해당 작업을 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ffa23-104">Parameters can accept input directly from the command line, or from objects passed to the cmdlet through the pipeline, The arguments (also known as *values*) of these parameters can specify the input that the cmdlet accepts, how the cmdlet should perform its actions, and the data that the cmdlet returns to the pipeline.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="ffa23-105">이 섹션의 내용</span><span class="sxs-lookup"><span data-stu-id="ffa23-105">In This Section</span></span>

<span data-ttu-id="ffa23-106">[속성을 매개 변수로 선언](./declaring-properties-as-parameters.md) cmdlet의 매개 변수를 선언 하기 전에 이해 해야 하는 기본 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="ffa23-106">[Declaring Properties as Parameters](./declaring-properties-as-parameters.md) Provides basic information you must understand before you declare the parameters of a cmdlet.</span></span>

<span data-ttu-id="ffa23-107">[Cmdlet 매개 변수 유형의](./types-of-cmdlet-parameters.md) 다양 한 cmdlet에서 선언할 수 있는 매개 변수를 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="ffa23-107">[Types of Cmdlet Parameters](./types-of-cmdlet-parameters.md) Describes the different types of parameters that you can declare in cmdlets.</span></span>

<span data-ttu-id="ffa23-108">[Cmdlet 매개 변수 이름 및 기능 지침](./standard-cmdlet-parameter-names-and-types.md) Discuses 이름, 데이터 형식 및 표준 매개 변수 기능을 권장 합니다.</span><span class="sxs-lookup"><span data-stu-id="ffa23-108">[Cmdlet Parameter Name and Functionality Guidelines](./standard-cmdlet-parameter-names-and-types.md) Discuses the names, recommended data type, and functionality of standard parameters.</span></span>

<span data-ttu-id="ffa23-109">[매개 변수 별칭](./parameter-aliases.md) 매개 변수를 정의할 수 있는 별칭에 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="ffa23-109">[Parameter Aliases](./parameter-aliases.md) Discusses the aliases that you can define for parameters.</span></span>

<span data-ttu-id="ffa23-110">[일반 매개 변수 이름](./common-parameter-names.md) 이 항목에서는 Windows PowerShell cmdlet에 추가 하는 매개 변수를 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="ffa23-110">[Common Parameter Names](./common-parameter-names.md) This topic describes the parameters that Windows PowerShell adds to cmdlets.</span></span>

<span data-ttu-id="ffa23-111">[Cmdlet 매개 변수 설정](./cmdlet-parameter-sets.md) 매개 변수 집합을 다양 한 시나리오에 대 한 다양 한 작업을 수행할 수 있는 단일 cmdlet를 작성할 수 있도록 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="ffa23-111">[Cmdlet Parameter Sets](./cmdlet-parameter-sets.md) Discusses how parameter sets enable you to write a single cmdlet that can perform different actions for different scenarios.</span></span>

<span data-ttu-id="ffa23-112">[Cmdlet은 동적 매개 변수](./cmdlet-dynamic-parameters.md) 특별 한 상황에서 사용자에 게 사용할 수 있는 매개 변수를 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="ffa23-112">[Cmdlet Dynamic Parameters](./cmdlet-dynamic-parameters.md) Discusses parameters that are available to the user under special conditions.</span></span>

<span data-ttu-id="ffa23-113">[Cmdlet 매개 변수에서 와일드 카드 문자를 지 원하는](./supporting-wildcard-characters-in-cmdlet-parameters.md) 리소스 그룹에 대해 실행 되는 cmdlet를 디자인할 때 와일드 카드 문자에 대 한 지원을 제공 하는 방법에 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="ffa23-113">[Supporting Wildcard Characters in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md) Describes how to provide support for wildcard characters when you design a cmdlet that will be run against a group of resources.</span></span>

<span data-ttu-id="ffa23-114">[매개 변수 입력 유효성 검사](./validating-parameter-input.md) Windows PowerShell cmdlet 매개 변수에 전달 된 인수를 확인 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="ffa23-114">[Validating Parameter Input](./validating-parameter-input.md) Describes how Windows PowerShell validates the arguments passed to cmdlet parameters.</span></span>

<span data-ttu-id="ffa23-115">[필터 매개 변수를 입력](./input-filter-parameters.md) 에 대해 설명 합니다 `Filter`, `Include`, 및 `Exclude` 매개 변수를 cmdlet에 영향을 주는 입력된 개체 집합을 필터링 합니다.</span><span class="sxs-lookup"><span data-stu-id="ffa23-115">[Input Filter Parameters](./input-filter-parameters.md) Discusses the `Filter`, `Include`, and `Exclude` parameters that filter the set of input objects that the cmdlet affects.</span></span>

## <a name="related-sections"></a><span data-ttu-id="ffa23-116">관련 섹션</span><span class="sxs-lookup"><span data-stu-id="ffa23-116">Related Sections</span></span>

[<span data-ttu-id="ffa23-117">매개 변수 입력의 유효성을 검사 하는 방법</span><span class="sxs-lookup"><span data-stu-id="ffa23-117">How to Validate Parameter Input</span></span>](./how-to-validate-parameter-input.md)

## <a name="see-also"></a><span data-ttu-id="ffa23-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ffa23-118">See Also</span></span>

[<span data-ttu-id="ffa23-119">매개 변수 특성 선언</span><span class="sxs-lookup"><span data-stu-id="ffa23-119">Parameter Attribute Declaration</span></span>](./parameter-attribute-declaration.md)

[<span data-ttu-id="ffa23-120">Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="ffa23-120">Windows PowerShell Cmdlets</span></span>](./cmdlet-overview.md)
