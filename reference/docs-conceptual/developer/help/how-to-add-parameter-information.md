---
title: 매개 변수 정보를 추가 하는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cf6c1442-60aa-477a-8f30-ab02b1b11039
caps.latest.revision: 7
ms.openlocfilehash: d4a5fc934a41b00f89862674e44e4540680674f7
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361232"
---
# <a name="how-to-add-parameter-information"></a><span data-ttu-id="0807c-102">매개 변수 정보를 추가하는 방법</span><span class="sxs-lookup"><span data-stu-id="0807c-102">How to Add Parameter Information</span></span>

<span data-ttu-id="0807c-103">이 섹션에서는 cmdlet 도움말 항목의 매개 변수 섹션에 표시 되는 콘텐츠를 추가 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="0807c-103">This section describes how to add content that is displayed in the PARAMETERS section of the cmdlet Help topic.</span></span> <span data-ttu-id="0807c-104">도움말 항목의 매개 변수 섹션은 cmdlet의 각 매개 변수를 나열 하 고 각 매개 변수에 대 한 자세한 설명을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="0807c-104">The PARAMETERS section of the Help topic lists each of the parameters of the cmdlet and provides a detailed description of each parameter.</span></span>

<span data-ttu-id="0807c-105">매개 변수 섹션의 내용은 도움말 항목의 구문 섹션 내용과 일치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0807c-105">The content of the PARAMETERS section should be consistent with the content of the SYNTAX section of the Help topic.</span></span> <span data-ttu-id="0807c-106">구문 및 매개 변수 노드에 유사한 XML 요소가 포함 되어 있는지 확인 하는 것은 도움말 작성자의 책임입니다.</span><span class="sxs-lookup"><span data-stu-id="0807c-106">It is the responsibility of the Help author to make sure that both the Syntax and Parameters node contain similar XML elements.</span></span>

> [!NOTE]
> <span data-ttu-id="0807c-107">도움말 파일의 전체 보기를 보려면 Windows PowerShell 설치 디렉터리에 있는 dll-Help 파일 중 하나를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="0807c-107">For a complete view of a Help file, open one of the dll-Help.xml files located in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="0807c-108">예를 들어 dll-Help 파일에는 몇 가지 Windows PowerShell cmdlet에 대 한 내용이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0807c-108">For example, the Microsoft.PowerShell.Commands.Management.dll-Help.xml file contains content for several of the Windows PowerShell cmdlets.</span></span>

### <a name="to-add-parameters"></a><span data-ttu-id="0807c-109">매개 변수를 추가 하려면</span><span class="sxs-lookup"><span data-stu-id="0807c-109">To Add Parameters</span></span>

1. <span data-ttu-id="0807c-110">Cmdlet 도움말 파일을 열고 문서화할 cmdlet에 대 한 명령 노드를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="0807c-110">Open the cmdlet Help file and locate the Command node for the cmdlet you are documenting.</span></span> <span data-ttu-id="0807c-111">새 cmdlet을 추가 하는 경우에는 새 명령 노드를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0807c-111">If you are adding a new cmdlet you will need to create a new Command node.</span></span> <span data-ttu-id="0807c-112">도움말 파일에는 도움말 콘텐츠를 제공 하는 각 cmdlet에 대 한 명령 노드가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0807c-112">Your Help file will contain a Command node for each cmdlet that you are providing Help content for.</span></span> <span data-ttu-id="0807c-113">빈 명령 노드의 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="0807c-113">Here is an example of a blank Command node.</span></span>

    ```xml
    <command:command>
    </command:command>
    ```

2. <span data-ttu-id="0807c-114">명령 노드 내에서 아래와 같이 설명 노드를 찾아 매개 변수 노드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="0807c-114">Within the Command node, locate the Description node and add a Parameters node as shown below.</span></span> <span data-ttu-id="0807c-115">매개 변수 노드는 하나만 허용 되며 구문 노드 바로 뒤에와 야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0807c-115">Only one Parameters node is allowed, and it should immediately follow the Syntax node.</span></span>

    ```xml
    <command:command>
      <command:details></command:details>
      <maml:description></maml:description>
      <command:syntax></command:syntax>
      <command:parameters>
      </command:Parameters>
    </command:command>
    ```

3. <span data-ttu-id="0807c-116">매개 변수 노드 내에서 아래와 같이 cmdlet의 각 매개 변수에 대 한 매개 변수 노드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="0807c-116">Within the Parameters node, add a Parameter node for each parameter of the cmdlet as shown below.</span></span>

   <span data-ttu-id="0807c-117">이 예에서는 매개 변수 노드가 세 개의 매개 변수에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0807c-117">In this example, a Parameter node is added for three parameters.</span></span>

    ```xml
    <command:parameters>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
    </command:Parameters>
    ```

   <span data-ttu-id="0807c-118">이러한 매개 변수는 구문 노드에서 사용 되는 것과 동일한 XML 태그 이며 여기에 지정 된 매개 변수는 구문 노드에 지정 된 매개 변수와 일치 해야 하기 때문에 구문 노드에서 매개 변수 노드를 복사 하 여 Parameters 노드에 붙여 넣을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0807c-118">Because these are the same XML tags that are used in the Syntax node, and because the parameters specified here must match the parameters specified by the Syntax node, you can copy the Parameter nodes from the Syntax node and paste them into the Parameters node.</span></span> <span data-ttu-id="0807c-119">그러나 매개 변수가 구문의 여러 매개 변수 집합에 지정 된 경우에도 매개 변수 노드의 인스턴스를 하나만 복사 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0807c-119">However, be sure to copy only one instance of a Parameter node, even if the parameter is specified in multiple parameter sets in the syntax.</span></span>

4. <span data-ttu-id="0807c-120">각 매개 변수 노드에 대해 각 매개 변수의 특징을 정의 하는 특성 값을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0807c-120">For each Parameter node, set the attribute values that define the characteristics of each parameter.</span></span> <span data-ttu-id="0807c-121">이러한 특성에는 required, 와일드 카드 사용, pipelineinput 및 position이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0807c-121">These attributes include the following: required, globbing, pipelineinput, and position.</span></span>

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
      </command:parameter>
      <command:parameter required="false" globbing="false"
               pipelineInput="false" position="named">
      </command:parameter>
      <command:parameter required="false" globbing="false"
               pipelineInput="false" position="named" ></command:parameter>
    </command:Parameters>
    ```

5. <span data-ttu-id="0807c-122">각 매개 변수 노드에 대해 매개 변수의 이름을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="0807c-122">For each Parameter node, add the name of the parameter.</span></span> <span data-ttu-id="0807c-123">매개 변수 노드에 추가 된 매개 변수 이름의 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="0807c-123">Here is an example of the parameter name added to the Parameter node.</span></span>

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
      </command:parameter>
    </command:Parameters>
    ```

6. <span data-ttu-id="0807c-124">각 매개 변수 노드에 대해 매개 변수에 대 한 설명을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="0807c-124">For each Parameter node, add the description of the parameter.</span></span> <span data-ttu-id="0807c-125">매개 변수 노드에 추가 된 매개 변수 설명의 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="0807c-125">Here is an example of the parameter description added to the Parameter node.</span></span>

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
        <maml:description>
          <maml:para> Add parameter description... </maml:para>
        </maml:description>
      </command:parameter>
    </command:parameters>
    ```

7. <span data-ttu-id="0807c-126">각 매개 변수 노드에 대해 매개 변수의 .NET Framework 유형을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="0807c-126">For each Parameter node, add the .NET Framework type of the parameter.</span></span> <span data-ttu-id="0807c-127">매개 변수 형식은 매개 변수 이름과 함께 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0807c-127">The parameter type is displayed along with the parameter name.</span></span>

   <span data-ttu-id="0807c-128">다음은 매개 변수 노드에 추가 된 매개 변수 .NET Framework 형식의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="0807c-128">Here is an example of the parameter .NET Framework type added to the Parameter node.</span></span>

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
        <maml:description>
          <maml:para> Add parameter description... </maml:para>
        </maml:description>
        <dev:type> Add .NET Framework type... </dev:type>
      </command:parameter>
    </command:parameters>
    ```

8. <span data-ttu-id="0807c-129">각 매개 변수 노드에 대해 매개 변수의 기본값을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="0807c-129">For each Parameter node, add the default value of the parameter.</span></span> <span data-ttu-id="0807c-130">내용이 표시 되 면 매개 변수 설명에 다음 문장이 추가 됩니다. "DefaultValue"가 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="0807c-130">The following sentence is added to the parameter description when the content is displayed: "DefaultValue" is the default.</span></span>

   <span data-ttu-id="0807c-131">매개 변수 기본값에 대 한 예제는 매개 변수 노드에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0807c-131">Here is an example of the parameter default value is added to the Parameter node.</span></span>

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
        <maml:description>
          <maml:para> Add parameter description... </maml:para>
        </maml:description>
        <dev:type> Add .NET Framework type... </dev:type>
        <dev:defaultvalue> Add default value...</dev:defaultvalue>
      </command:parameter>
    </command:parameters>
    ```

9. <span data-ttu-id="0807c-132">여러 값이 있는 각 매개 변수에 대해 가능한 값 노드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="0807c-132">For each Parameter that has multiple values, add a possible values node.</span></span>

   <span data-ttu-id="0807c-133">매개 변수에 대 한 두 가지 가능한 값을 정의 하는 가능한 값 노드의 예제는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="0807c-133">Here is an example of the of a possible values node that defines two possible values for the parameter</span></span>

    ```xml
    <dev:possiblevalues>
      <dev:possiblevalue>
        <dev:value>Unknown</dev:value>
        <maml:description>
          <maml:para></maml:para>
        </maml:description>
      /dev:possiblevalue>
      <dev:possiblevalue>
        <dev:value>String</dev:value>
        <maml:description>
          <maml:para></maml:para>
        </maml:description>
      </dev:possibleValue>
    </dev:possiblevalues>
    ```

<span data-ttu-id="0807c-134">매개 변수를 추가할 때 기억할 몇 가지 사항은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="0807c-134">Here are some things to remember when adding parameters.</span></span>

- <span data-ttu-id="0807c-135">매개 변수의 특성은 cmdlet 도움말 항목의 모든 뷰에 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0807c-135">The attributes of the parameter are not displayed in all views of the cmdlet Help topic.</span></span> <span data-ttu-id="0807c-136">그러나 사용자가 토픽의 Full (@no__t Get-help 0cmdletname >-full) 또는 매개 변수 (@no__t Get-help 1cmdletname->) 보기를 요청 하는 경우 매개 변수 설명 다음의 표에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0807c-136">However, they are displayed in a table following the parameter description when the user asks for the Full (Get-Help \<cmdletname> -full) or Parameter (Get-Help \<cmdletname> -parameter) view of the topic.</span></span>

- <span data-ttu-id="0807c-137">매개 변수 설명은 cmdlet 도움말 항목의 가장 중요 한 부분 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="0807c-137">The parameter description is one of the most important parts of a cmdlet Help topic.</span></span> <span data-ttu-id="0807c-138">설명은 간결 하 고 철저 하 게 설명 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0807c-138">The description should be brief, as well as thorough.</span></span> <span data-ttu-id="0807c-139">또한 두 매개 변수가 서로 상호 작용 하는 경우와 같이 매개 변수 설명이 너무 길면 cmdlet 도움말 항목의 참고 섹션에서 더 많은 내용을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0807c-139">Also, remember that if the parameter description becomes too long, such as when two parameters interact with each other, you can add more content in the NOTES section of the cmdlet Help topic.</span></span>

  <span data-ttu-id="0807c-140">매개 변수 설명은 두 가지 유형의 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="0807c-140">The parameter description provides two types of information.</span></span>

- <span data-ttu-id="0807c-141">매개 변수를 사용 하는 경우 cmdlet이 수행 하는 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="0807c-141">What the cmdlet does when the parameter is used.</span></span>

- <span data-ttu-id="0807c-142">매개 변수에 대 한 올바른 값은 무엇 인가요?</span><span class="sxs-lookup"><span data-stu-id="0807c-142">What a legal value is for the parameter.</span></span>

- <span data-ttu-id="0807c-143">매개 변수 값은 .NET Framework 개체로 표시 되기 때문에 사용자에 게 일반적인 명령줄 도움말에서와 동일한 값에 대 한 자세한 정보가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="0807c-143">Because the parameter values are expressed as .NET Framework objects, users need more information about these values than they would in a traditional command-line Help.</span></span> <span data-ttu-id="0807c-144">사용자에 게 매개 변수가 허용 하도록 디자인 된 데이터 형식을 알리고 예제를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="0807c-144">Tell the user what type of data the parameter is designed to accept, and include examples.</span></span>

<span data-ttu-id="0807c-145">매개 변수의 기본값은 명령줄에서 매개 변수를 지정 하지 않은 경우에 사용 되는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="0807c-145">The default value of the parameter is the value that is used if the parameter is not specified on the command line.</span></span> <span data-ttu-id="0807c-146">기본값은 선택 사항이 며, 필수 매개 변수와 같은 일부 매개 변수에는 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0807c-146">Note that the default value is optional, and is not needed for some parameters, such as required parameters.</span></span> <span data-ttu-id="0807c-147">그러나 대부분의 선택적 매개 변수에는 기본값을 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0807c-147">However, you should specify a default value for most optional parameters.</span></span>

<span data-ttu-id="0807c-148">기본값을 사용 하면 사용자가 매개 변수를 사용 하지 않는 효과를 이해할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0807c-148">The default value helps the user to understand the effect of not using the parameter.</span></span> <span data-ttu-id="0807c-149">선택적인 경로에 대 한 "현재 디렉터리" 또는 "Windows PowerShell 설치 디렉터리 ($pshome)"와 같은 구체적으로 구체적으로 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="0807c-149">Describe the default value very specifically, such as the "Current directory" or the "Windows PowerShell installation directory ($pshome)" for an optional path.</span></span> <span data-ttu-id="0807c-150">@No__t-0 매개 변수에 사용 되는 다음 문장과 같이 기본값을 설명 하는 문장을 작성할 수도 있습니다. "PassThru를 지정 하지 않으면 cmdlet은 개체를 파이프라인으로 전달 하지 않습니다."</span><span class="sxs-lookup"><span data-stu-id="0807c-150">You can also write a sentence that describes the default, such as the following sentence used for the `PassThru` parameter: "If PassThru is not specified, the cmdlet does not pass objects down the pipeline."</span></span>  <span data-ttu-id="0807c-151">또한 값이 필드 이름 "**default value**"와 반대 되는 것으로 표시 되기 때문에 항목에 "default value" 라는 용어를 포함할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0807c-151">Also, because the value is displayed opposite the field name "**Default value**", you do not need to include the term "default value" in the entry.</span></span>

<span data-ttu-id="0807c-152">매개 변수의 기본값은 cmdlet 도움말 항목의 모든 뷰에 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0807c-152">The default value of the parameter is not displayed in all views of the cmdlet Help topic.</span></span> <span data-ttu-id="0807c-153">그러나이 속성은 사용자가 토픽의 Full (@no__t Get-help 0cmdletname >-full) 또는 매개 변수 (@no__t Get-help 1cmdletname->-parameter) 보기를 요청 하는 경우 매개 변수 설명에 따라 매개 변수 특성을 사용 하 여 테이블에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0807c-153">However, it is displayed in a table (along with the parameter attributes) following the parameter description when the user asks for the Full (Get-Help \<cmdletname> -full) or Parameter (Get-Help \<cmdletname> -parameter) view of the topic.</span></span>

<span data-ttu-id="0807c-154">다음 XML에서는 `<command:parameter>` 노드에 추가 된 `<dev:defaultValue>` 태그 쌍을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0807c-154">The following XML shows a pair of `<dev:defaultValue>` tags added to the `<command:parameter>` node.</span></span> <span data-ttu-id="0807c-155">기본값은 닫는 `</command:parameterValue>` 태그 (매개 변수 값이 지정 된 경우) 또는 매개 변수 설명의 닫는 `</maml:description>` 태그 바로 다음에 옵니다.</span><span class="sxs-lookup"><span data-stu-id="0807c-155">Notice that the default value follows immediately after the closing `</command:parameterValue>` tag (when the parameter value is specified) or the closing `</maml:description>` tag of the parameter description.</span></span> <span data-ttu-id="0807c-156">이름의.</span><span class="sxs-lookup"><span data-stu-id="0807c-156">name.</span></span>

```xml
<command:parameters>
  <command:parameter required="true" globbing="true"
           pipelineInput="false" position="named">
    <maml:name> Parameter name </maml:name>
    <maml:description>
      <maml:para> Parameter Description </maml:para>
    </maml:description>
    <command:parameterValue required="true">
      Value
    </command:parameterValue>
    <dev:defaultValue> Default parameter value </dev:defaultValue>
  </command:parameter>
</command:parameters>
```

<span data-ttu-id="0807c-157">열거 형식에 대 한 값 추가</span><span class="sxs-lookup"><span data-stu-id="0807c-157">Add Values for Enumerated Types</span></span>

<span data-ttu-id="0807c-158">매개 변수에 여러 값 또는 열거 형식의 값이 있는 경우 선택적 \<dev: possibleValues > 노드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0807c-158">If the parameter has multiple values or values of an enumerated type, you can use an optional \<dev:possibleValues> node.</span></span> <span data-ttu-id="0807c-159">이 노드를 사용 하 여 여러 값의 이름과 설명을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0807c-159">This node allows you to specify a name and description for multiple values.</span></span>

<span data-ttu-id="0807c-160">열거형 값에 대 한 설명은 `Get-Help` cmdlet에 의해 표시 되는 기본 도움말 뷰에 나타나지 않지만 다른 도움말 뷰어는 보기에서이 콘텐츠를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0807c-160">Be aware that the descriptions of the enumerated values do not appear in any of the default Help views displayed by the `Get-Help` cmdlet, but other Help viewers may display this content in their views.</span></span>

<span data-ttu-id="0807c-161">다음 XML에서는 두 개의 값이 지정 된 `<dev:possibleValues>` 노드를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0807c-161">The following XML shows a `<dev:possibleValues>` node with two values specified.</span></span>

```xml
<command:parameters>
  <command:parameter required="true" globbing="true"
           pipelineInput="false" position="named">
    <maml:name> Parameter name </maml:name>
    <maml:description>
      <maml:para> Parameter Description </maml:para>
    </maml:description>
    <command:parameterValue required="true">
      Value
    </command:parameterValue>
    <dev:defaultValue> Default parameter value </dev:defaultValue>
    <dev:possibleValues>
      <dev:possibleValue>
        <dev:value> Value 1 </dev:value>
        <maml:description>
          <maml:para> Description 1 </maml:para>
        </maml:description>
      <dev:possibleValue>
      <dev:possibleValue>
        <dev:value> Value 2 </dev:value>
        <maml:description>
          <maml:para> Description 2 </maml:para>
        </maml:description>
      <dev:possibleValue>
    </dev:possibleValues>
  </command:parameter>
</command:parameters>
```