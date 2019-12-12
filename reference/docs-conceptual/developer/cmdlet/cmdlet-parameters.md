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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365932"
---
# <a name="cmdlet-parameters"></a><span data-ttu-id="57416-102">Cmdlet 매개 변수</span><span class="sxs-lookup"><span data-stu-id="57416-102">Cmdlet Parameters</span></span>

<span data-ttu-id="57416-103">Cmdlet 매개 변수는 cmdlet이 입력을 받을 수 있도록 하는 메커니즘을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="57416-103">Cmdlet parameters provide the mechanism that allows a cmdlet to accept input.</span></span> <span data-ttu-id="57416-104">매개 변수는 명령줄에서 직접 입력을 받을 수 있고 파이프라인을 통해 cmdlet에 전달 된 개체에서 이러한 매개 변수의 인수 ( *값*이 라고도 함)는 cmdlet이 허용 하는 입력, cmdlet에서 해당 작업을 수행 하는 방법 및 cmdlet이 파이프라인으로 반환 하는 데이터를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57416-104">Parameters can accept input directly from the command line, or from objects passed to the cmdlet through the pipeline, The arguments (also known as *values*) of these parameters can specify the input that the cmdlet accepts, how the cmdlet should perform its actions, and the data that the cmdlet returns to the pipeline.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="57416-105">이 섹션의 내용</span><span class="sxs-lookup"><span data-stu-id="57416-105">In This Section</span></span>

<span data-ttu-id="57416-106">[속성을 매개 변수로 선언](./declaring-properties-as-parameters.md) Cmdlet의 매개 변수를 선언 하기 전에 이해 해야 하는 기본적인 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="57416-106">[Declaring Properties as Parameters](./declaring-properties-as-parameters.md) Provides basic information you must understand before you declare the parameters of a cmdlet.</span></span>

<span data-ttu-id="57416-107">[Cmdlet 매개 변수의 유형](./types-of-cmdlet-parameters.md) Cmdlet에서 선언할 수 있는 다양 한 형식의 매개 변수를 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="57416-107">[Types of Cmdlet Parameters](./types-of-cmdlet-parameters.md) Describes the different types of parameters that you can declare in cmdlets.</span></span>

<span data-ttu-id="57416-108">[Cmdlet 매개 변수 이름 및 기능 지침](./standard-cmdlet-parameter-names-and-types.md) 표준 매개 변수의 이름, 권장 데이터 형식 및 기능을 Discuses 합니다.</span><span class="sxs-lookup"><span data-stu-id="57416-108">[Cmdlet Parameter Name and Functionality Guidelines](./standard-cmdlet-parameter-names-and-types.md) Discuses the names, recommended data type, and functionality of standard parameters.</span></span>

<span data-ttu-id="57416-109">[매개 변수 별칭](./parameter-aliases.md) 매개 변수에 대해 정의할 수 있는 별칭에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="57416-109">[Parameter Aliases](./parameter-aliases.md) Discusses the aliases that you can define for parameters.</span></span>

<span data-ttu-id="57416-110">[일반 매개 변수 이름](./common-parameter-names.md) 이 항목에서는 Windows PowerShell에서 cmdlet에 추가 하는 매개 변수에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="57416-110">[Common Parameter Names](./common-parameter-names.md) This topic describes the parameters that Windows PowerShell adds to cmdlets.</span></span>

<span data-ttu-id="57416-111">[Cmdlet 매개 변수 집합](./cmdlet-parameter-sets.md) 매개 변수 집합을 사용 하 여 여러 시나리오에 대해 다른 작업을 수행할 수 있는 단일 cmdlet을 작성 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="57416-111">[Cmdlet Parameter Sets](./cmdlet-parameter-sets.md) Discusses how parameter sets enable you to write a single cmdlet that can perform different actions for different scenarios.</span></span>

<span data-ttu-id="57416-112">[Cmdlet 동적 매개 변수](./cmdlet-dynamic-parameters.md) 사용자가 특별 한 조건에서 사용할 수 있는 매개 변수에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="57416-112">[Cmdlet Dynamic Parameters](./cmdlet-dynamic-parameters.md) Discusses parameters that are available to the user under special conditions.</span></span>

<span data-ttu-id="57416-113">[Cmdlet 매개 변수에 와일드 카드 문자 지원](./supporting-wildcard-characters-in-cmdlet-parameters.md) 리소스 그룹에 대해 실행 될 cmdlet을 디자인할 때 와일드 카드 문자에 대 한 지원을 제공 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="57416-113">[Supporting Wildcard Characters in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md) Describes how to provide support for wildcard characters when you design a cmdlet that will be run against a group of resources.</span></span>

<span data-ttu-id="57416-114">[매개 변수 입력 유효성 검사](./validating-parameter-input.md) Windows PowerShell에서 cmdlet 매개 변수에 전달 된 인수의 유효성을 검사 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="57416-114">[Validating Parameter Input](./validating-parameter-input.md) Describes how Windows PowerShell validates the arguments passed to cmdlet parameters.</span></span>

<span data-ttu-id="57416-115">[입력 필터 매개 변수](./input-filter-parameters.md) Cmdlet에서 적용 하는 입력 개체 집합을 필터링 하는 `Filter`, `Include`및 `Exclude` 매개 변수에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="57416-115">[Input Filter Parameters](./input-filter-parameters.md) Discusses the `Filter`, `Include`, and `Exclude` parameters that filter the set of input objects that the cmdlet affects.</span></span>

## <a name="related-sections"></a><span data-ttu-id="57416-116">관련 섹션</span><span class="sxs-lookup"><span data-stu-id="57416-116">Related Sections</span></span>

[<span data-ttu-id="57416-117">매개 변수 입력의 유효성을 검사 하는 방법</span><span class="sxs-lookup"><span data-stu-id="57416-117">How to Validate Parameter Input</span></span>](./how-to-validate-parameter-input.md)

## <a name="see-also"></a><span data-ttu-id="57416-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="57416-118">See Also</span></span>

[<span data-ttu-id="57416-119">매개 변수 특성 선언</span><span class="sxs-lookup"><span data-stu-id="57416-119">Parameter Attribute Declaration</span></span>](./parameter-attribute-declaration.md)

[<span data-ttu-id="57416-120">Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="57416-120">Windows PowerShell Cmdlets</span></span>](./cmdlet-overview.md)
