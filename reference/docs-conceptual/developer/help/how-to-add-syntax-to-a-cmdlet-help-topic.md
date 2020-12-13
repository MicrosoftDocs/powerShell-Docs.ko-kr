---
ms.date: 09/12/2016
ms.topic: reference
title: Cmdlet 도움말 항목에 구문을 추가하는 방법
description: Cmdlet 도움말 항목에 구문을 추가하는 방법
ms.openlocfilehash: bcc037d22051c162cd0f70702da17afe7ed9c01a
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659071"
---
# <a name="how-to-add-syntax-to-a-cmdlet-help-topic"></a><span data-ttu-id="76d7d-103">Cmdlet 도움말 항목에 구문을 추가하는 방법</span><span class="sxs-lookup"><span data-stu-id="76d7d-103">How to Add Syntax to a Cmdlet Help Topic</span></span>

<span data-ttu-id="76d7d-104">Cmdlet 도움말 파일의 구문 다이어그램에 대 한 XML의 코딩을 시작 하기 전에이 섹션을 참조 하 여 매개 변수 특성 및 구문 다이어그램에 표시 되는 데이터와 같은 제공 해야 하는 데이터 종류를 명확 하 게 파악할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76d7d-104">Before you start to code the XML for the syntax diagram in the cmdlet Help file, read this section to get a clear picture of the kind of data you need to provide, such as the parameter attributes, and how that data is displayed in the syntax diagram..</span></span>

## <a name="parameter-attributes"></a><span data-ttu-id="76d7d-105">매개 변수 특성</span><span class="sxs-lookup"><span data-stu-id="76d7d-105">Parameter Attributes</span></span>

- <span data-ttu-id="76d7d-106">필수</span><span class="sxs-lookup"><span data-stu-id="76d7d-106">Required</span></span>
  - <span data-ttu-id="76d7d-107">True 이면 매개 변수가 매개 변수 집합을 사용 하는 모든 명령에 표시 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d7d-107">If true, the parameter must appear in all commands that use the parameter set.</span></span>
  - <span data-ttu-id="76d7d-108">False 이면 매개 변수 집합을 사용 하는 모든 명령에서 매개 변수가 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="76d7d-108">If false, the parameter is optional in all commands that use the parameter set.</span></span>
- <span data-ttu-id="76d7d-109">위치</span><span class="sxs-lookup"><span data-stu-id="76d7d-109">Position</span></span>
  - <span data-ttu-id="76d7d-110">명명 된 경우 매개 변수 이름이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d7d-110">If named, the parameter name is required.</span></span>
  - <span data-ttu-id="76d7d-111">위치를 지정 하는 경우 매개 변수 이름은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="76d7d-111">If positional, the parameter name is optional.</span></span> <span data-ttu-id="76d7d-112">생략 하는 경우 매개 변수 값은 명령의 지정 된 위치에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d7d-112">When it is omitted, the parameter value must be in the specified position in the command.</span></span> <span data-ttu-id="76d7d-113">예를 들어 값이 position = "1" 인 경우 매개 변수 값은 명령의 첫 번째 또는 유일한 명명 되지 않은 매개 변수 값 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d7d-113">For example, if the value is position="1", the parameter value must be the first or only unnamed parameter value in the command.</span></span>
- <span data-ttu-id="76d7d-114">파이프라인 입력</span><span class="sxs-lookup"><span data-stu-id="76d7d-114">Pipeline Input</span></span>
  - <span data-ttu-id="76d7d-115">True (ByValue) 인 경우 입력을 매개 변수로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76d7d-115">If true (ByValue), you can pipe input to the parameter.</span></span> <span data-ttu-id="76d7d-116">입력은 속성 이름과 개체 형식이 예상 형식과 일치 하지 않는 경우에도 매개 변수에 연결 됩니다 ("bound to").</span><span class="sxs-lookup"><span data-stu-id="76d7d-116">The input is associated with ("bound to") the parameter even if the property name and the object type do not match the expected type.</span></span>
    <span data-ttu-id="76d7d-117">PowerShell 매개 변수 바인딩 구성 요소는 입력을 올바른 유형으로 변환 하려고 시도 하 고 유형을 변환할 수 없는 경우에만 명령이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d7d-117">The PowerShell parameter binding components try to convert the input to the correct type and fail the command only when the type cannot be converted.</span></span> <span data-ttu-id="76d7d-118">매개 변수 집합에서 하나의 매개 변수만 값으로 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76d7d-118">Only one parameter in a parameter set can be associated by value.</span></span>
  - <span data-ttu-id="76d7d-119">True (ByPropertyName) 인 경우 입력을 매개 변수로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76d7d-119">If true (ByPropertyName), you can pipe input to the parameter.</span></span> <span data-ttu-id="76d7d-120">그러나 매개 변수 이름이 입력 개체의 속성 이름과 일치 하는 경우에만 입력이 매개 변수와 연결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="76d7d-120">However, the input is associated with the parameter only when the parameter name matches the name of a property of the input object.</span></span> <span data-ttu-id="76d7d-121">예를 들어 매개 변수 이름이 인 경우 `Path` cmdlet으로 파이프 된 개체는 개체에 path 라는 속성을 가진 경우에만 해당 매개 변수와 연결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="76d7d-121">For example, if the parameter name is `Path`, objects piped to the cmdlet are associated with that parameter only when the object has a property named path.</span></span>
  - <span data-ttu-id="76d7d-122">True (ByValue, Byvalue) 인 경우 속성 이름 또는 값을 기준으로 매개 변수에 입력을 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76d7d-122">If true (ByValue, ByPropertyName), you can pipe input to the parameter either by property name or by value.</span></span> <span data-ttu-id="76d7d-123">매개 변수 집합에서 하나의 매개 변수만 값으로 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76d7d-123">Only one parameter in a parameter set can be associated by value.</span></span>
  - <span data-ttu-id="76d7d-124">False 이면이 매개 변수에 입력을 파이프 할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="76d7d-124">If false, you cannot pipe input to this parameter.</span></span>
- <span data-ttu-id="76d7d-125">와일드 카드 사용</span><span class="sxs-lookup"><span data-stu-id="76d7d-125">Globbing</span></span>
  - <span data-ttu-id="76d7d-126">True 이면 사용자가 매개 변수 값을 입력 하는 텍스트에 와일드 카드 문자가 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76d7d-126">If true, the text that the user types for the parameter value can include wildcard characters.</span></span>
  - <span data-ttu-id="76d7d-127">False 이면 사용자가 매개 변수 값을 입력 하는 텍스트에 와일드 카드 문자를 포함할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="76d7d-127">If false, the text that the user types for the parameter value cannot include wildcard characters.</span></span>

### <a name="parameter-value-attributes"></a><span data-ttu-id="76d7d-128">매개 변수 값 특성</span><span class="sxs-lookup"><span data-stu-id="76d7d-128">Parameter Value Attributes</span></span>

- <span data-ttu-id="76d7d-129">필수</span><span class="sxs-lookup"><span data-stu-id="76d7d-129">Required</span></span>
  - <span data-ttu-id="76d7d-130">True 이면 명령에 매개 변수를 사용할 때마다 지정 된 값을 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d7d-130">If true, the specified value must be used whenever using the parameter in a command.</span></span>
  - <span data-ttu-id="76d7d-131">False 이면 매개 변수 값이 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="76d7d-131">If false, the parameter value is optional.</span></span> <span data-ttu-id="76d7d-132">일반적으로 값은 매개 변수에 대 한 몇 가지 유효한 값 (예: 열거 형식) 중 하나인 경우에만 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="76d7d-132">Typically, a value is optional only when it is one of several valid values for a parameter, such as in an enumerated type.</span></span>

<span data-ttu-id="76d7d-133">매개 변수 값의 **필수** 특성이 매개 변수의 **필수** 특성과 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="76d7d-133">The **Required** attribute of a parameter value is different from the **Required** attribute of a parameter.</span></span>

<span data-ttu-id="76d7d-134">매개 변수의 필수 특성은 cmdlet을 호출할 때 매개 변수 및 해당 값을 포함 해야 하는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="76d7d-134">The required attribute of a parameter indicates whether the parameter (and its value) must be included when invoking the cmdlet.</span></span> <span data-ttu-id="76d7d-135">반면 매개 변수 값의 필수 특성은 매개 변수가 명령에 포함 된 경우에만 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="76d7d-135">In contrast, the required attribute of a parameter value is used only when the parameter is included in the command.</span></span> <span data-ttu-id="76d7d-136">특정 값을 매개 변수와 함께 사용 해야 하는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="76d7d-136">It indicates whether that particular value must be used with the parameter.</span></span>

<span data-ttu-id="76d7d-137">일반적으로 자리 표시자 인 매개 변수 값은 필수 이며, 매개 변수 값은 매개 변수와 함께 사용 될 수 있는 여러 값 중 하나 이기 때문에 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="76d7d-137">Typically, parameter values that are placeholders are required and parameter values that are literal are not required, because they are one of several values that might be used with the parameter.</span></span>

### <a name="gathering-syntax-information"></a><span data-ttu-id="76d7d-138">구문 정보 수집</span><span class="sxs-lookup"><span data-stu-id="76d7d-138">Gathering Syntax Information</span></span>

1. <span data-ttu-id="76d7d-139">Cmdlet 이름으로 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d7d-139">Start with the cmdlet name.</span></span>

   ```
   SYNTAX
       Get-Tech
   ```

1. <span data-ttu-id="76d7d-140">Cmdlet의 모든 매개 변수를 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d7d-140">List all the parameters of the cmdlet.</span></span> <span data-ttu-id="76d7d-141">`-`각 매개 변수 이름 앞에 하이픈 () (ASCII 45)을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d7d-141">Type a hyphen (`-`) (ASCII 45) before each parameter name.</span></span>
   <span data-ttu-id="76d7d-142">매개 변수를 매개 변수 집합으로 구분 합니다. 일부 cmdlet에는 하나의 매개 변수 집합만 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76d7d-142">Separate the parameters into parameter sets (some cmdlets may have only one parameter set).</span></span> <span data-ttu-id="76d7d-143">이 예에서 Get-Tech cmdlet에는 두 개의 매개 변수 집합이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76d7d-143">In this example the Get-Tech cmdlet has two parameter sets.</span></span>

   ```
   SYNTAX
       Get-Tech -name -type
       Get-Tech -ID -list -type
   ```

   <span data-ttu-id="76d7d-144">Cmdlet 이름을 사용 하 여 각 매개 변수 집합을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d7d-144">Start each parameter set with the cmdlet name.</span></span>

   <span data-ttu-id="76d7d-145">기본 매개 변수 집합을 먼저 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d7d-145">List the default parameter set first.</span></span> <span data-ttu-id="76d7d-146">기본 매개 변수는 cmdlet 클래스에서 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d7d-146">The default parameter is specified by the cmdlet class.</span></span>

   <span data-ttu-id="76d7d-147">먼저 표시 되어야 하는 위치 매개 변수가 없는 경우 각 매개 변수 집합에 대해 고유한 매개 변수를 먼저 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d7d-147">For each parameter set, list its unique parameter first, unless there are positional parameters that must appear first.</span></span> <span data-ttu-id="76d7d-148">이전 예에서 Name 및 ID 매개 변수는 두 매개 변수 집합에 대 한 고유한 매개 변수입니다. 각 매개 변수 집합은 해당 매개 변수 집합에 고유한 하나의 매개 변수를 포함 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d7d-148">In the previous example, the Name and ID parameters are unique parameters for the two parameter sets (each parameter set must have one parameter that is unique to that parameter set).</span></span> <span data-ttu-id="76d7d-149">이렇게 하면 사용자가 매개 변수 집합에 제공 해야 하는 매개 변수를 더 쉽게 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76d7d-149">This makes it easier for users to identify what parameter they need to supply for the parameter set.</span></span>

   <span data-ttu-id="76d7d-150">명령에 표시 되어야 하는 순서로 매개 변수를 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d7d-150">List the parameters in the order that they should appear in the command.</span></span> <span data-ttu-id="76d7d-151">순서가 중요 하지 않은 경우 관련 매개 변수를 함께 나열 하거나 가장 자주 사용 되는 매개 변수를 먼저 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d7d-151">If the order does not matter, list related parameters together, or list the most frequently used parameters first.</span></span>

   <span data-ttu-id="76d7d-152">Cmdlet에서 ShouldProcess를 지 원하는 경우 WhatIf 및 Confirm 매개 변수를 나열 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d7d-152">Be sure to list the WhatIf and Confirm parameters if the cmdlet supports ShouldProcess.</span></span>

   <span data-ttu-id="76d7d-153">구문 다이어그램에서 일반 매개 변수 (예: Verbose, Debug, ErrorAction)를 나열 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="76d7d-153">Do not list the common parameters (such as Verbose, Debug, and ErrorAction) in your syntax diagram.</span></span> <span data-ttu-id="76d7d-154">`Get-Help`Cmdlet은 도움말 항목이 표시 될 때 해당 정보를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d7d-154">The `Get-Help` cmdlet adds that information for you when it displays the Help topic.</span></span>

1. <span data-ttu-id="76d7d-155">매개 변수 값을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d7d-155">Add the parameter values.</span></span> <span data-ttu-id="76d7d-156">PowerShell에서 매개 변수 값은 .NET 형식으로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="76d7d-156">In PowerShell, parameter values are represented by their .NET type.</span></span>
   <span data-ttu-id="76d7d-157">그러나 System.string의 경우 형식 이름 (예: "string")을 약어로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76d7d-157">However, the type name can be abbreviated, such as "string" for System.String.</span></span>

   ```
   SYNTAX
       Get-Tech -name string -type basic advanced
       Get-Tech -ID int -list -type basic advanced
   ```

   <span data-ttu-id="76d7d-158">System.string의 **문자열과 system.string** 의 경우 **int** **와 같이** 의미를 명확 하 게 하는 형식으로 **축약 합니다.**</span><span class="sxs-lookup"><span data-stu-id="76d7d-158">Abbreviate types as long as their meaning is clear, such as **string** for **System.String** and **int** for **System.Int32**.</span></span>

   <span data-ttu-id="76d7d-159">열거의 모든 값 (예: `-type` **기본** 또는 **고급** 으로 설정 될 수 있는 이전 예제의 매개 변수)을 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d7d-159">List all values of enumerations, such as the `-type` parameter in the previous example, which can be set to **basic** or **advanced**.</span></span>

   <span data-ttu-id="76d7d-160">이전 예제와 같은 스위치 매개 변수는 `-list` 값을 포함 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="76d7d-160">Switch parameters, such as `-list` in the previous example, do not have values.</span></span>

1. <span data-ttu-id="76d7d-161">리터럴인 매개 변수 값과 비교할 수 있는 매개 변수 값에 꺾쇠 괄호를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d7d-161">Add angle brackets to parameters values that are placeholder, as compared to parameter values that are literals.</span></span>

   ```
   SYNTAX
       Get-Tech -name <string> -type basic advanced
       Get-Tech -ID <int> -list -type basic advanced
   ```

1. <span data-ttu-id="76d7d-162">선택적 매개 변수 및 해당 기본값를 대괄호로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="76d7d-162">Enclose optional parameters and their vales in square brackets.</span></span>

   ```
   SYNTAX
       Get-Tech -name <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

1. <span data-ttu-id="76d7d-163">선택적 매개 변수 이름 (위치 매개 변수의 경우)을 대괄호로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="76d7d-163">Enclose optional parameters names (for positional parameters) in square brackets.</span></span> <span data-ttu-id="76d7d-164">다음 예제의 Name 매개 변수와 같은 위치에 있는 매개 변수의 이름은 명령에 포함 될 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="76d7d-164">The name for parameters that are positional, such as the Name parameter in the following example, do not have to be included in the command.</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

1. <span data-ttu-id="76d7d-165">Name 매개 변수의 이름 목록과 같이 매개 변수 값에 여러 값이 포함 될 수 있는 경우 매개 변수 값 바로 뒤에 대괄호 쌍을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d7d-165">If a parameter value can contain multiple values, such as a list of names in the Name parameter, add a pair of square brackets directly following the parameter value.</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type basic advanced]
       Get-Tech -ID <int[]> [-list] [-type basic advanced]
   ```

1. <span data-ttu-id="76d7d-166">사용자가 매개 변수 또는 매개 변수 값 (예: 형식 매개 변수) 중에서 선택할 수 있는 경우 선택 항목을 중괄호로 묶고 단독 또는 기호 (;)로 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d7d-166">If the user can choose from parameters or parameter values, such as the Type parameter, enclose the choices in curly brackets and separate them with the exclusive OR symbol(;).</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

1. <span data-ttu-id="76d7d-167">매개 변수 값이 따옴표 또는 괄호와 같은 특정 서식을 사용 해야 하는 경우 구문에 형식을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d7d-167">If the parameter value must use specific formatting, such as quotation marks or parentheses, show the format in the syntax.</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <"string[]"> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

## <a name="coding-the-syntax-diagram-xml"></a><span data-ttu-id="76d7d-168">구문 다이어그램 XML 코딩</span><span class="sxs-lookup"><span data-stu-id="76d7d-168">Coding the Syntax Diagram XML</span></span>

<span data-ttu-id="76d7d-169">XML의 구문 노드는 tag로 끝나는 description 노드 바로 다음에 시작 됩니다 `</maml:description>` .</span><span class="sxs-lookup"><span data-stu-id="76d7d-169">The syntax node of the XML begins immediately after the description node, which ends with the `</maml:description>` tag.</span></span> <span data-ttu-id="76d7d-170">구문 다이어그램에 사용 된 데이터를 수집 하는 방법에 대 한 자세한 내용은 [구문 정보 수집](#gathering-syntax-information)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="76d7d-170">For information about gathering the data used in the syntax diagram, see [Gathering Syntax Information](#gathering-syntax-information).</span></span>

### <a name="adding-a-syntax-node"></a><span data-ttu-id="76d7d-171">구문 노드 추가</span><span class="sxs-lookup"><span data-stu-id="76d7d-171">Adding a Syntax Node</span></span>

<span data-ttu-id="76d7d-172">Cmdlet 도움말 항목에 표시 된 구문 다이어그램은 XML의 구문 노드에 있는 데이터에서 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="76d7d-172">The syntax diagram displayed in the cmdlet Help topic is generated from the data in the syntax node of the XML.</span></span> <span data-ttu-id="76d7d-173">구문 노드는 tags 인 경우 쌍으로 묶입니다 `<command:syntax>` .</span><span class="sxs-lookup"><span data-stu-id="76d7d-173">The syntax node is enclosed in a pair if `<command:syntax>` tags.</span></span> <span data-ttu-id="76d7d-174">Cmdlet의 각 매개 변수 집합을 태그 쌍으로 묶습니다 `<command:syntaxitem>` .</span><span class="sxs-lookup"><span data-stu-id="76d7d-174">With each parameter set of the cmdlet enclosed in a pair of `<command:syntaxitem>` tags.</span></span> <span data-ttu-id="76d7d-175">추가할 수 있는 태그 수에는 제한이 없습니다 `<command:syntaxitem>` .</span><span class="sxs-lookup"><span data-stu-id="76d7d-175">There is no limit to the number of `<command:syntaxitem>` tags that you can add.</span></span>

<span data-ttu-id="76d7d-176">다음 예에서는 두 개의 매개 변수 집합에 대 한 구문 항목 노드가 있는 구문 노드를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="76d7d-176">The following example shows a syntax node that has syntax item nodes for two parameter sets.</span></span>

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

### <a name="adding-the-cmdlet-name-to-the-parameter-set-data"></a><span data-ttu-id="76d7d-177">매개 변수 집합 데이터에 Cmdlet 이름 추가</span><span class="sxs-lookup"><span data-stu-id="76d7d-177">Adding the Cmdlet Name to the Parameter Set Data</span></span>

<span data-ttu-id="76d7d-178">Cmdlet의 각 매개 변수 집합은 구문 항목 노드에 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="76d7d-178">Each parameter set of the cmdlet is specified in a syntax item node.</span></span> <span data-ttu-id="76d7d-179">각 구문 항목 노드는 `<maml:name>` cmdlet의 이름을 포함 하는 태그 쌍으로 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d7d-179">Each syntax item node begins with a pair of `<maml:name>` tags that include the name of the cmdlet.</span></span>

<span data-ttu-id="76d7d-180">다음 예에서는 두 개의 매개 변수 집합에 대 한 구문 항목 노드가 있는 구문 노드를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d7d-180">The following example includes a syntax node that has syntax item nodes for two parameter sets.</span></span>

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

### <a name="adding-parameters"></a><span data-ttu-id="76d7d-181">매개 변수 추가</span><span class="sxs-lookup"><span data-stu-id="76d7d-181">Adding Parameters</span></span>

<span data-ttu-id="76d7d-182">구문 항목 노드에 추가 된 각 매개 변수는 태그 쌍 내에서 지정 됩니다 `<command:parameter>` .</span><span class="sxs-lookup"><span data-stu-id="76d7d-182">Each parameter added to the syntax item node is specified within a pair of `<command:parameter>` tags.</span></span> <span data-ttu-id="76d7d-183">`<command:parameter>`PowerShell에서 제공 하는 일반 매개 변수를 제외 하 고 매개 변수 집합에 포함 된 각 매개 변수에 대 한 쌍의 태그를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d7d-183">You need a pair of `<command:parameter>` tags for each parameter included in the parameter set, with the exception of the common parameters that are provided by PowerShell.</span></span>

<span data-ttu-id="76d7d-184">여는 태그의 특성은 `<command:parameter>` 매개 변수가 구문 다이어그램에 표시 되는 방식을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d7d-184">The attributes of the opening `<command:parameter>` tag determine how the parameter appears in the syntax diagram.</span></span> <span data-ttu-id="76d7d-185">매개 변수 특성에 대 한 자세한 내용은 [매개 변수 특성](#parameter-attributes)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="76d7d-185">For information on parameter attributes, see [Parameter Attributes](#parameter-attributes).</span></span>

> [!NOTE]
> <span data-ttu-id="76d7d-186">`<command:parameter>`태그는 콘텐츠가 표시 되지 않는 자식 요소를 지원 `<maml:description>` 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d7d-186">The `<command:parameter>` tag supports a child element `<maml:description>` whose content is never displayed.</span></span> <span data-ttu-id="76d7d-187">매개 변수 설명은 XML의 parameter 노드에 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="76d7d-187">The parameter descriptions are specified in the parameter node of the XML.</span></span> <span data-ttu-id="76d7d-188">구문 항목 bodes와 매개 변수 노드의 정보가 일치 하지 않도록 하려면를 생략 `<maml:description>` 하거나 비워 둡니다.</span><span class="sxs-lookup"><span data-stu-id="76d7d-188">To avoid inconsistencies between the information in the syntax item bodes and the parameter node, omit the (`<maml:description>` or leave it empty.</span></span>

<span data-ttu-id="76d7d-189">다음 예제에는 두 개의 매개 변수를 사용 하는 매개 변수 집합에 대 한 구문 항목 노드가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76d7d-189">The following example includes a syntax item node for a parameter set with two parameters.</span></span>

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
