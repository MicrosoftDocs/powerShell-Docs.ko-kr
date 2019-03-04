---
title: 구문 Cmdlet 도움말 항목을 추가 하는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d0c6d03f-1c1a-43d8-928e-e3290e90e0bc
caps.latest.revision: 5
ms.openlocfilehash: 947d0c0188df5bba3a9fb617fe5abf0b3b28eb51
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857999"
---
# <a name="how-to-add-syntax-to-a-cmdlet-help-topic"></a><span data-ttu-id="2a500-102">Cmdlet 도움말 항목에 구문을 추가하는 방법</span><span class="sxs-lookup"><span data-stu-id="2a500-102">How to Add Syntax to a Cmdlet Help Topic</span></span>

- [<span data-ttu-id="2a500-103">매개 변수 특성</span><span class="sxs-lookup"><span data-stu-id="2a500-103">Parameter Attributes</span></span>](#Parameter-Attributes)

- [<span data-ttu-id="2a500-104">매개 변수 값 특성</span><span class="sxs-lookup"><span data-stu-id="2a500-104">Parameter Value Attributes</span></span>](#Parameter-Value-Attributes)

- [<span data-ttu-id="2a500-105">구문 정보 수집</span><span class="sxs-lookup"><span data-stu-id="2a500-105">Gathering Syntax Information</span></span>](#Gathering-Syntax-Information)

- [<span data-ttu-id="2a500-106">XML 구문 다이어그램은 코딩</span><span class="sxs-lookup"><span data-stu-id="2a500-106">Coding the Syntax Diagram XML</span></span>](#Coding-the-Syntax-Diagram-XML)

## <a name="things-to-know-about-the-syntax-diagram-in-cmdlet-help"></a><span data-ttu-id="2a500-107">Cmdlet 도움말의 구문 다이어그램에 대해 알아야 할 내용</span><span class="sxs-lookup"><span data-stu-id="2a500-107">Things to Know About the Syntax Diagram in Cmdlet Help</span></span>

<span data-ttu-id="2a500-108">Cmdlet 도움말 파일의 구문 다이어그램에 대 한 XML 코드를 시작 하기 전에 명확히 제공 하는 데 필요한 데이터의 매개 변수 특성 및 해당 데이터를 구문 다이어그램에 표시 되는 방식을 같은 종류의이 섹션을 읽고...</span><span class="sxs-lookup"><span data-stu-id="2a500-108">Before you start to code the XML for the syntax diagram in the cmdlet Help file, read this section to get a clear picture of the kind of data you need to provide, such as the parameter attributes, and how that data is displayed in the syntax diagram..</span></span>

### <a name="parameter-attributes"></a><span data-ttu-id="2a500-109">매개 변수 특성</span><span class="sxs-lookup"><span data-stu-id="2a500-109">Parameter Attributes</span></span>

- <span data-ttu-id="2a500-110">필수</span><span class="sxs-lookup"><span data-stu-id="2a500-110">Required</span></span>

  - <span data-ttu-id="2a500-111">True 이면 매개 변수는 매개 변수 집합을 사용 하는 모든 명령에 나타나야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a500-111">If true, the parameter must appear in all commands that use the parameter set.</span></span>

  - <span data-ttu-id="2a500-112">False 이면 매개 변수 집합을 사용 하는 모든 명령에서 선택적입니다.</span><span class="sxs-lookup"><span data-stu-id="2a500-112">If false, the parameter is optional in all commands that use the parameter set.</span></span>

- <span data-ttu-id="2a500-113">위치</span><span class="sxs-lookup"><span data-stu-id="2a500-113">Position</span></span>

  - <span data-ttu-id="2a500-114">이름이 인 경우 매개 변수 이름이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a500-114">If named, the parameter name is required.</span></span>

  - <span data-ttu-id="2a500-115">위치 하는 경우 매개 변수 이름은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="2a500-115">If positional, the parameter name is optional.</span></span> <span data-ttu-id="2a500-116">생략 하는 경우 매개 변수 값을 명령에 지정된 된 위치에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a500-116">When it is omitted, the parameter value must be in the specified position in the command.</span></span> <span data-ttu-id="2a500-117">값이 위치 = "1", 예를 들어, 매개 변수 값은 첫 번째 이거나 이어야만 명명 되지 않은 명령에 매개 변수 값입니다.</span><span class="sxs-lookup"><span data-stu-id="2a500-117">For example, if the value is position="1", the parameter value must be the first or only unnamed parameter value in the command.</span></span>

- <span data-ttu-id="2a500-118">파이프라인 입력</span><span class="sxs-lookup"><span data-stu-id="2a500-118">Pipeline Input</span></span>

  - <span data-ttu-id="2a500-119">True 이면 (ByValue) 입력 매개 변수에 파이프할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a500-119">If true (ByValue), you can pipe input to the parameter.</span></span> <span data-ttu-id="2a500-120">연결 된 입력 ("에 바인딩")를 사용 하 여 속성 이름 및 개체 형식이 예상된 형식과 일치 하지 않는 경우에 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="2a500-120">The input is associated with ("bound to") the parameter even if the property name and the object type do not match the expected type.</span></span> <span data-ttu-id="2a500-121">Windows PowerShell? 매개 변수 바인딩 구성 요소를 올바른 형식에 대 한 입력을 변환 하 고 형식을 변환할 수 없는 경우에 명령 실패 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a500-121">The Windows PowerShell? parameter binding components try to convert the input to the correct type and fail the command only when the type cannot be converted.</span></span> <span data-ttu-id="2a500-122">매개 변수 집합에 하나의 매개 변수 값으로 연결 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a500-122">Only one parameter in a parameter set can be associated by value.</span></span>

  - <span data-ttu-id="2a500-123">True (ByPropertyName) 입력 매개 변수에 파이프할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a500-123">If true (ByPropertyName), you can pipe input to the parameter.</span></span> <span data-ttu-id="2a500-124">그러나 매개 변수 이름 입력된 개체의 속성 이름과 일치 하는 경우에 입력 매개 변수 연관 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2a500-124">However, the input is associated with the parameter only when the parameter name matches the name of a property of the input object.</span></span> <span data-ttu-id="2a500-125">예를 들어 매개 변수 이름은 `Path`, 개체 경로 라는 속성이 있는 경우에 cmdlet에 파이프 하는 개체는 해당 매개 변수를 사용 하 여 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a500-125">For example, if the parameter name is `Path`, objects piped to the cmdlet are associated with that parameter only when the object has a property named path.</span></span>

  - <span data-ttu-id="2a500-126">경우 true (ByValue, ByPropertyName) 속성 이름 또는 값으로 입력 매개 변수에 파이프할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a500-126">If true (ByValue, ByPropertyName), you can pipe input to the parameter either by property name or by value.</span></span> <span data-ttu-id="2a500-127">매개 변수 집합에 하나의 매개 변수 값으로 연결 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a500-127">Only one parameter in a parameter set can be associated by value.</span></span>

  - <span data-ttu-id="2a500-128">False 이면이 매개 변수의 입력을 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2a500-128">If false, you cannot pipe input to this parameter.</span></span>

- <span data-ttu-id="2a500-129">와일드 카드 사용</span><span class="sxs-lookup"><span data-stu-id="2a500-129">Globbing</span></span>

  - <span data-ttu-id="2a500-130">True 이면 사용자가 입력 한 매개 변수 값에 대 한 텍스트는 와일드 카드 문자를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a500-130">If true, the text that the user types for the parameter value can include wildcard characters.</span></span>

  - <span data-ttu-id="2a500-131">False 인 경우 사용자가 입력 한 매개 변수 값에 대 한 텍스트는 와일드 카드 문자를 포함할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2a500-131">If false, the text that the user types for the parameter value cannot include wildcard characters.</span></span>

### <a name="parameter-value-attributes"></a><span data-ttu-id="2a500-132">매개 변수 값 특성</span><span class="sxs-lookup"><span data-stu-id="2a500-132">Parameter Value Attributes</span></span>

- <span data-ttu-id="2a500-133">필수</span><span class="sxs-lookup"><span data-stu-id="2a500-133">Required</span></span>

  - <span data-ttu-id="2a500-134">True 이면 명령에서 매개 변수를 사용 하 여 때마다 지정 된 값을 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a500-134">If true, the specified value must be used whenever using the parameter in a command.</span></span>

  - <span data-ttu-id="2a500-135">False 이면 매개 변수 값은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="2a500-135">If false, the parameter value is optional.</span></span> <span data-ttu-id="2a500-136">일반적으로 경우에 매개 변수의 경우 몇 가지 유효한 값 중 하나 같은 열거 형식에는 값은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="2a500-136">Typically, a value is optional only when it is one of several valid values for a parameter, such as in an enumerated type.</span></span>

<span data-ttu-id="2a500-137">매개 변수 값의 필수 특성에 필요한 매개 변수 특성이 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="2a500-137">The Required attribute of a parameter value is different from the Required attribute of a parameter.</span></span>

<span data-ttu-id="2a500-138">매개 변수의 필수 특성 해야 하는지 여부를 매개 변수 (및 해당 값) 포함 된 cmdlet을 호출 하는 경우를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="2a500-138">The required attribute of a parameter indicates whether the parameter (and its value) must be included when invoking the cmdlet.</span></span> <span data-ttu-id="2a500-139">반면, 매개 변수 값에 필요한 특성이 매개 변수는 명령에 포함 하는 경우에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2a500-139">In contrast, the required attribute of a parameter value is used only when the parameter is included in the command.</span></span> <span data-ttu-id="2a500-140">매개 변수를 사용 하 여 해당 특정 값을 사용 해야 하는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="2a500-140">It indicates whether that particular value must be used with the parameter.</span></span>

<span data-ttu-id="2a500-141">일반적으로 자리 표시자는 매개 변수 값이 필요 하 고 매개 변수를 사용 하 여 사용할 수 있는 몇 가지 값 중 하나 이기 때문에 매개 변수 값은 리터럴 필요 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2a500-141">Typically, parameter values that are placeholders are required and parameter values that are literal are not required, because they are one of several values that might be used with the parameter.</span></span>

### <a name="gathering-syntax-information"></a><span data-ttu-id="2a500-142">구문 정보 수집</span><span class="sxs-lookup"><span data-stu-id="2a500-142">Gathering Syntax Information</span></span>

1. <span data-ttu-id="2a500-143">Cmdlet 이름으로 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a500-143">Start with the cmdlet name.</span></span>

   ```
   SYNTAX
       Get-Tech
   ```

2. <span data-ttu-id="2a500-144">Cmdlet의 모든 매개 변수를 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a500-144">List all the parameters of the cmdlet.</span></span> <span data-ttu-id="2a500-145">(라고도 "대시" 또는 "앞에 빼기 기호" (ASCII 45) 각 매개 변수 이름 대시를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a500-145">Type a dash (also known as a "dash" or "minus sign" (ASCII 45) before each parameter name.</span></span> <span data-ttu-id="2a500-146">매개 변수 (일부 cmdlet 설정 매개 변수는 하나만 있을 수 있습니다) 매개 변수 집합으로 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a500-146">Separate the parameters into parameter sets (some cmdlets may have only one parameter set).</span></span> <span data-ttu-id="2a500-147">이 예제에서는 Get-기술 cmdlet에는 두 매개 변수 집합이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a500-147">In this example the Get-Tech cmdlet has two parameter sets.</span></span>

   ```
   SYNTAX
       Get-Tech -name -type
       Get-Tech -ID -list -type
   ```

   <span data-ttu-id="2a500-148">Cmdlet 이름으로 설정 하는 각 매개 변수를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a500-148">Start each parameter set with the cmdlet name.</span></span>

   <span data-ttu-id="2a500-149">먼저 설정 기본 매개 변수를 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a500-149">List the default parameter set first.</span></span> <span data-ttu-id="2a500-150">기본 매개 변수는 cmdlet 클래스에 의해 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2a500-150">The default parameter is specified by the cmdlet class.</span></span>

   <span data-ttu-id="2a500-151">각 매개 변수 집합에 대 한 첫 번째 표시 되어야 하는 위치 매개 변수 없는 고유한 매개 변수를 먼저 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a500-151">For each parameter set, list its unique parameter first, unless there are positional parameters that must appear first.</span></span> <span data-ttu-id="2a500-152">이 예에서 이름 및 ID 매개 변수는 두 매개 변수 집합에 대 한 고유한 매개 변수 (매개 변수 집합이 각 매개 변수 하나가 있어야 해당 매개 변수 집합에 고유한).</span><span class="sxs-lookup"><span data-stu-id="2a500-152">In the previous example, the Name and ID parameters are unique parameters for the two parameter sets (each parameter set must have one parameter that is unique to that parameter set).</span></span> <span data-ttu-id="2a500-153">이 매개 변수에 대해 제공 하는 데 필요한 어떤 매개 변수 집합을 식별 하는 사용자에 대해 쉽게 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a500-153">This makes it easier for users to identify what parameter they need to supply for the parameter set.</span></span>

   <span data-ttu-id="2a500-154">명령에 표시 된 순서 대로 매개 변수를 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a500-154">List the parameters in the order that they should appear in the command.</span></span> <span data-ttu-id="2a500-155">순서는 중요 하지 않습니다, 경우 관련된 매개 변수를 함께 나열 하거나 먼저 가장 자주 사용 되는 매개 변수를 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a500-155">If the order does not matter, list related parameters together, or list the most frequently used parameters first.</span></span>

   <span data-ttu-id="2a500-156">Cmdlet은 ShouldProcess를 지 원하는 경우 WhatIf 및 Confirm 매개 변수를 나열 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a500-156">Be sure to list the WhatIf and Confirm parameters if the cmdlet supports ShouldProcess.</span></span>

   <span data-ttu-id="2a500-157">구문 다이어그램에서 (예: Verbose, Debug, ErrorAction) 공통 매개 변수를 나열 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2a500-157">Do not list the common parameters (such as Verbose, Debug, and ErrorAction) in your syntax diagram.</span></span> <span data-ttu-id="2a500-158">`Get-Help` cmdlet 도움말 항목을 표시 하는 경우 해당 정보를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a500-158">The `Get-Help` cmdlet adds that information for you when it displays the Help topic.</span></span>

3. <span data-ttu-id="2a500-159">매개 변수 값을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a500-159">Add the parameter values.</span></span> <span data-ttu-id="2a500-160">Windows PowerShell에?를 매개 변수 값은.NET 형식으로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2a500-160">In Windows PowerShell?, parameter values are represented by their .NET type.</span></span> <span data-ttu-id="2a500-161">그러나 형식 이름 "문자열" System.String에 대해 같은 축약할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a500-161">However, the type name can be abbreviated, such as "string" for System.String.</span></span>

   ```
   SYNTAX
       Get-Tech -name string -type basic advanced
       Get-Tech -ID int -list -type basic advanced
   ```

   <span data-ttu-id="2a500-162">매개 변수의 의미는 분명 System.Int32에 대 한 "int" System.String "문자열" 등으로 형식 약어입니다.</span><span class="sxs-lookup"><span data-stu-id="2a500-162">Abbreviate types as long as their meaning is clear, such as "string" for System.String and "int" for System.Int32.</span></span>

   <span data-ttu-id="2a500-163">열거형의 모든 값을 같은 목록 앞의 예제에서-형식 매개 변수 본 "basic" 또는 "고급"로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a500-163">List all values of enumerations, such as the -type parameter in the previous example, wich can be set to "basic" or "advanced".</span></span>

   <span data-ttu-id="2a500-164">스위치 매개 변수-앞의 예제에서 목록 등, 하는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="2a500-164">Switch parameters, such as -list in the previous example, do not have values.</span></span>

4. <span data-ttu-id="2a500-165">자리 표시자를 리터럴 매개 변수 값을 비교 하 여 매개 변수 값에 꺾쇠 괄호를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a500-165">Add angle brackets to parameters values that are placeholder, as compared to parameter values that are literals.</span></span>

   ```
   SYNTAX
       Get-Tech -name <string> -type basic advanced
       Get-Tech -ID <int> -list -type basic advanced
   ```

5. <span data-ttu-id="2a500-166">선택적 매개 변수 및 해당 값을 대괄호로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="2a500-166">Enclose optional parameters and their vales in square brackets.</span></span>

   ```
   SYNTAX
       Get-Tech -name <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

6. <span data-ttu-id="2a500-167">(위치 매개 변수)에 대 한 선택적 매개 변수 이름을 대괄호로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="2a500-167">Enclose optional parameters names (for positional parameters) in square brackets.</span></span> <span data-ttu-id="2a500-168">다음 예제에서는 이름 매개 변수 같은 위치는 매개 변수에 대 한 이름을 명령에 포함 될 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2a500-168">The name for parameters that are positional, such as the Name parameter in the following example, do not have to be included in the command.</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

7. <span data-ttu-id="2a500-169">매개 변수 값을 Name 매개 변수 이름 목록 같은 여러 값을 포함할 수 있는 경우 바로 다음 매개 변수 값을 대괄호 쌍을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a500-169">If a parameter value can contain multiple values, such as a list of names in the Name parameter, add a pair of square brackets directly following the parameter value.</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type basic advanced]
       Get-Tech -ID <int[]> [-list] [-type basic advanced]
   ```

8. <span data-ttu-id="2a500-170">매개 변수 또는 매개 변수 값에서 선택할 수 있으며, 경우 형식 매개 변수를 같은 선택 중괄호로 묶고 배타적 OR symbol(;)를 구별 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a500-170">If the user can choose from parameters or parameter values, such as the Type parameter, enclose the choices in curly brackets and separate them with the exclusive OR symbol(;).</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

9. <span data-ttu-id="2a500-171">매개 변수 값을 따옴표 또는 괄호와 같은 특정 서식에 사용 해야 하는 경우 구문에서 형식을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2a500-171">If the parameter value must use specific formatting, such as quotation marks or parentheses, show the format in the syntax.</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <"string[]"> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

## <a name="coding-the-syntax-diagram-xml"></a><span data-ttu-id="2a500-172">XML 구문 다이어그램은 코딩</span><span class="sxs-lookup"><span data-stu-id="2a500-172">Coding the Syntax Diagram XML</span></span>

<span data-ttu-id="2a500-173">XML 구문 노드의 끝나는 설명 노드를 후 즉시 시작 되는 \</maml:description > 태그입니다.</span><span class="sxs-lookup"><span data-stu-id="2a500-173">The syntax node of the XML begins immediately after the description node, which ends with the \</maml:description> tag.</span></span> <span data-ttu-id="2a500-174">구문 다이어그램에 사용 된 데이터를 수집 하는 방법에 대 한 내용은 [구문 정보 수집](#Gathering-Syntax-Information)합니다.</span><span class="sxs-lookup"><span data-stu-id="2a500-174">For information about gathering the data used in the syntax diagram, see [Gathering Syntax Information](#Gathering-Syntax-Information).</span></span>

### <a name="adding-a-syntax-node"></a><span data-ttu-id="2a500-175">구문 노드 추가</span><span class="sxs-lookup"><span data-stu-id="2a500-175">Adding a Syntax Node</span></span>

<span data-ttu-id="2a500-176">Cmdlet 도움말 항목에 표시 된 구문 다이어그램은 구문 노드의 XML 데이터에서 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2a500-176">The syntax diagram displayed in the cmdlet Help topic is generated from the data in the syntax node of the XML.</span></span> <span data-ttu-id="2a500-177">구문 노드가 경우 쌍에 포함 되어 \<명령: 구문 > 태그입니다.</span><span class="sxs-lookup"><span data-stu-id="2a500-177">The syntax node is enclosed in a pair if \<command:syntax> tags.</span></span> <span data-ttu-id="2a500-178">한 쌍의 묶인 cmdlet의 각 매개 변수 집합을 사용 하 여 \<명령: syntaxitem > 태그입니다.</span><span class="sxs-lookup"><span data-stu-id="2a500-178">With each parameter set of the cmdlet enclosed in a pair of \<command:syntaxitem> tags.</span></span> <span data-ttu-id="2a500-179">수에 대 한 제한은 없습니다 \<명령: syntaxitem > 태그를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a500-179">There is no limit to the number of \<command:syntaxitem> tags that you can add.</span></span>

<span data-ttu-id="2a500-180">다음 예제에서는 구문 노드를 두 매개 변수 집합에 대 한 구문 항목 노드를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2a500-180">The following example shows a syntax node that has syntax item nodes for two parameter sets.</span></span>

```xml
<command:syntax>
  <command:syntaxItem>
    ...
    <!--Parameter Set 1 (default parameter set) parameters go here-->
    ...
  </command:syntaxItem>
  <command:syntaxItem>
    ...
    <!--Parameter Set 2 parameters go here-->
    ...
  </command:syntaxItem>
</command:syntax>
```

### <a name="adding-the-cmdlet-name-to-the-parameter-set-data"></a><span data-ttu-id="2a500-181">Cmdlet 이름 집합에 추가 매개 변수 데이터</span><span class="sxs-lookup"><span data-stu-id="2a500-181">Adding the Cmdlet Name to the Parameter Set Data</span></span>

<span data-ttu-id="2a500-182">각 매개 변수 집합 cmdlet의 구문 항목 노드가 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2a500-182">Each parameter set of the cmdlet is specified in a syntax item node.</span></span> <span data-ttu-id="2a500-183">각 구문 항목 노드가 한 쌍의 시작 \<maml:name > cmdlet의 이름을 포함 하는 태그입니다.</span><span class="sxs-lookup"><span data-stu-id="2a500-183">Each syntax item node begins with a pair of \<maml:name> tags that include the name of the cmdlet.</span></span>

<span data-ttu-id="2a500-184">다음 예제에서는 구문 노드 두 매개 변수 집합에 대 한 구문 항목 노드를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a500-184">The following example includes a syntax node that has syntax item nodes for two parameter sets.</span></span>

```xml
<command:syntax>
  <command:syntaxItem>
    <maml:name>Cmdlet-Name</maml:name>
  </command:syntaxItem>
  <command:syntaxItem>
    <maml:name>Cmdlet-Name</maml:name>
  </command:syntaxItem>
</command:syntax>
```

### <a name="adding-parameters"></a><span data-ttu-id="2a500-185">매개 변수 추가</span><span class="sxs-lookup"><span data-stu-id="2a500-185">Adding Parameters</span></span>

<span data-ttu-id="2a500-186">쌍 내에서 구문 항목 노드를 추가 하는 각 매개 변수를 지정 하는 \<명령: 매개 변수 > 태그입니다.</span><span class="sxs-lookup"><span data-stu-id="2a500-186">Each parameter added to the syntax item node is specified within a pair of \<command:parameter> tags.</span></span> <span data-ttu-id="2a500-187">한 쌍의 필요한 \<명령: 매개 변수 > Windows PowerShell에서 제공 하는 일반 매개 변수를 제외 하 고 매개 변수 집합에 포함 된 각 매개 변수에 대 한 태그.</span><span class="sxs-lookup"><span data-stu-id="2a500-187">You need a pair of \<command:parameter> tags for each parameter included in the parameter set, with the exception of the common parameters that are provided by Windows PowerShell?.</span></span>

<span data-ttu-id="2a500-188">열기의 특성 \<명령: 매개 변수 > 태그는 매개 변수 구문 다이어그램에 표시 되는 방식을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a500-188">The attributes of the opening \<command:parameter> tag determine how the parameter appears in the syntax diagram.</span></span> <span data-ttu-id="2a500-189">매개 변수 특성에 대 한 자세한 내용은 [매개 변수 특성](#Parameter-Attributes)합니다.</span><span class="sxs-lookup"><span data-stu-id="2a500-189">For information on parameter attributes, see [Parameter Attributes](#Parameter-Attributes).</span></span>

> [!NOTE]
> <span data-ttu-id="2a500-190">합니다 \<명령: 매개 변수 > 태그가 자식 요소를 지원 합니다. \<maml:description > 내용이 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2a500-190">The \<command:parameter> tag supports a child element \<maml:description> whose content is never displayed.</span></span> <span data-ttu-id="2a500-191">매개 변수 설명은 XML의 매개 변수 노드에 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2a500-191">The parameter descriptions are specified in the parameter node of the XML.</span></span> <span data-ttu-id="2a500-192">구문 항목의 정보 간 불일치를 방지 하려면 했 노드와 매개 변수를 생략 합니다 (\<maml:description > 하거나 비워 두세요.</span><span class="sxs-lookup"><span data-stu-id="2a500-192">To avoid inconsistencies between the information in the syntax item bodes and the parameter node, omit the (\<maml:description> or leave it empty.</span></span>

<span data-ttu-id="2a500-193">다음 예제에서는 두 개의 매개 변수를 사용 하 여 설정 매개 변수에 대해 구문이 항목 노드를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a500-193">The following example includes a syntax item node for a parameter set with two parameters.</span></span>

```xml
<command:syntaxItem>
  <maml:name>Cmdlet-Name</maml:name>
  <command:parameter required="true" globbing="true"
    pipelineInput="true (ByValue)" position="1">
    <maml:name>ParameterName1</maml:name>
    <command:parameterValue required="true">
      string[]
    </command:parameterValue>
  </command:parameter>
  <command:parameter required="true" globbing="true"
    pipelineInput="true (ByPropertyName)">
    <maml:name>ParameterName2</maml:name>
    <command:parameterValue required="true">
      int32[]
    </command:parameterValue>
  </command:parameter>
</command:syntaxItem>
```
