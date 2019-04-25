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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083368"
---
# <a name="how-to-add-parameter-information"></a><span data-ttu-id="2fc40-102">매개 변수 정보를 추가하는 방법</span><span class="sxs-lookup"><span data-stu-id="2fc40-102">How to Add Parameter Information</span></span>

<span data-ttu-id="2fc40-103">이 섹션에는 cmdlet 도움말 항목의 매개 변수 섹션에 표시 되는 콘텐츠를 추가 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="2fc40-103">This section describes how to add content that is displayed in the PARAMETERS section of the cmdlet Help topic.</span></span> <span data-ttu-id="2fc40-104">도움말 항목의 매개 변수 섹션에서는 각 cmdlet의 매개 변수를 나열 하 고 각 매개 변수에 대 한 자세한 설명을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="2fc40-104">The PARAMETERS section of the Help topic lists each of the parameters of the cmdlet and provides a detailed description of each parameter.</span></span>

<span data-ttu-id="2fc40-105">매개 변수 섹션의 콘텐츠는 도움말 항목의 구문 섹션의 내용과 일치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2fc40-105">The content of the PARAMETERS section should be consistent with the content of the SYNTAX section of the Help topic.</span></span> <span data-ttu-id="2fc40-106">것 도움말 작성자의 구문 및 매개 변수를 모두 노드 유사한 XML 요소를 포함 하 고 있는지 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2fc40-106">It is the responsibility of the Help author to make sure that both the Syntax and Parameters node contain similar XML elements.</span></span>

> [!NOTE]
> <span data-ttu-id="2fc40-107">에 대 한 도움말 파일의 열린 Windows PowerShell 설치 디렉터리에 있는 dll Help.xml 파일 중 하나는 전체 보기입니다.</span><span class="sxs-lookup"><span data-stu-id="2fc40-107">For a complete view of a Help file, open one of the dll-Help.xml files located in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="2fc40-108">예를 들어 Microsoft.PowerShell.Commands.Management.dll Help.xml 파일 다양 한 Windows PowerShell cmdlet에 대 한 콘텐츠를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="2fc40-108">For example, the Microsoft.PowerShell.Commands.Management.dll-Help.xml file contains content for several of the Windows PowerShell cmdlets.</span></span>

### <a name="to-add-parameters"></a><span data-ttu-id="2fc40-109">매개 변수를 추가 하려면</span><span class="sxs-lookup"><span data-stu-id="2fc40-109">To Add Parameters</span></span>

1. <span data-ttu-id="2fc40-110">Cmdlet 도움말 파일을 열고 문서화 하는 cmdlet에 대 한 명령 노드를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="2fc40-110">Open the cmdlet Help file and locate the Command node for the cmdlet you are documenting.</span></span> <span data-ttu-id="2fc40-111">새 cmdlet을 추가 하는 경우에 새 명령 노드를 만드는 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2fc40-111">If you are adding a new cmdlet you will need to create a new Command node.</span></span> <span data-ttu-id="2fc40-112">도움말 파일에 대 한 도움말 콘텐츠를 제공 하는 각 cmdlet에 대 한 명령 노드에 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2fc40-112">Your Help file will contain a Command node for each cmdlet that you are providing Help content for.</span></span> <span data-ttu-id="2fc40-113">빈 명령 노드의 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2fc40-113">Here is an example of a blank Command node.</span></span>

    ```xml
    <command:command>
    </command:command>
    ```

2. <span data-ttu-id="2fc40-114">명령 노드 내에서 설명 노드 찾아 아래와 같이 매개 변수 노드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="2fc40-114">Within the Command node, locate the Description node and add a Parameters node as shown below.</span></span> <span data-ttu-id="2fc40-115">매개 변수 노드는 하나만 허용 되 고 구문 노드 바로 다음에 나와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2fc40-115">Only one Parameters node is allowed, and it should immediately follow the Syntax node.</span></span>

    ```xml
    <command:command>
      <command:details></command:details>
      <maml:description></maml:description>
      <command:syntax></command:syntax>
      <command:parameters>
      </command:Parameters>
    </command:command>
    ```

3. <span data-ttu-id="2fc40-116">매개 변수 노드 내에서 아래와 같이 cmdlet의 각 매개 변수에 대해 매개 변수 노드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="2fc40-116">Within the Parameters node, add a Parameter node for each parameter of the cmdlet as shown below.</span></span>

   <span data-ttu-id="2fc40-117">이 예제에서는 세 가지 매개 변수에 대 한 매개 변수 노드에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2fc40-117">In this example, a Parameter node is added for three parameters.</span></span>

    ```xml
    <command:parameters>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
    </command:Parameters>
    ```

   <span data-ttu-id="2fc40-118">여기에 지정 된 매개 변수 때문에 구문 노드가 지정 된 매개 변수와 일치 해야 및 구문 노드에서 사용 되는 동일한 XML 태그를 이기 때문에 매개 변수 노드 구문 노드에서 복사한 매개 변수 노드에 붙여넣을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2fc40-118">Because these are the same XML tags that are used in the Syntax node, and because the parameters specified here must match the parameters specified by the Syntax node, you can copy the Parameter nodes from the Syntax node and paste them into the Parameters node.</span></span> <span data-ttu-id="2fc40-119">그러나 하나의 인스턴스만 매개 변수 노드를 복사 해야, 여러 매개 변수 구문에서 설정 되는 매개 변수를 지정 하는 경우에 합니다.</span><span class="sxs-lookup"><span data-stu-id="2fc40-119">However, be sure to copy only one instance of a Parameter node, even if the parameter is specified in multiple parameter sets in the syntax.</span></span>

4. <span data-ttu-id="2fc40-120">각 매개 변수에 대 한 노드를 각 매개 변수의 특성을 정의 하는 특성 값을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2fc40-120">For each Parameter node, set the attribute values that define the characteristics of each parameter.</span></span> <span data-ttu-id="2fc40-121">이러한 특성에는 다음이 포함 됩니다: 와일드 카드 사용, pipelineinput, 및 위치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2fc40-121">These attributes include the following: required, globbing, pipelineinput, and position.</span></span>

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

5. <span data-ttu-id="2fc40-122">각 매개 변수 노드, 매개 변수 이름을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="2fc40-122">For each Parameter node, add the name of the parameter.</span></span> <span data-ttu-id="2fc40-123">매개 변수 노드 추가 매개 변수 이름의 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2fc40-123">Here is an example of the parameter name added to the Parameter node.</span></span>

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
      </command:parameter>
    </command:Parameters>
    ```

6. <span data-ttu-id="2fc40-124">각 매개 변수 노드는 매개 변수의 설명을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="2fc40-124">For each Parameter node, add the description of the parameter.</span></span> <span data-ttu-id="2fc40-125">매개 변수 노드 추가 매개 변수 설명의 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2fc40-125">Here is an example of the parameter description added to the Parameter node.</span></span>

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

7. <span data-ttu-id="2fc40-126">각 매개 변수 노드에 대 한.NET Framework 형식의 매개 변수를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="2fc40-126">For each Parameter node, add the .NET Framework type of the parameter.</span></span> <span data-ttu-id="2fc40-127">매개 변수 형식 매개 변수 이름과 함께 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2fc40-127">The parameter type is displayed along with the parameter name.</span></span>

   <span data-ttu-id="2fc40-128">매개 변수 노드 추가 매개 변수.NET Framework 형식의 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2fc40-128">Here is an example of the parameter .NET Framework type added to the Parameter node.</span></span>

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

8. <span data-ttu-id="2fc40-129">각 매개 변수 노드에 대 한 매개 변수의 기본값을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="2fc40-129">For each Parameter node, add the default value of the parameter.</span></span> <span data-ttu-id="2fc40-130">내용을 표시 하는 경우 다음 문장은 매개 변수 설명에 추가 됩니다. "DefaultValue" 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="2fc40-130">The following sentence is added to the parameter description when the content is displayed: "DefaultValue" is the default.</span></span>

   <span data-ttu-id="2fc40-131">매개 변수 기본값의 예가 매개 변수 노드를 추가할 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2fc40-131">Here is an example of the parameter default value is added to the Parameter node.</span></span>

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

9. <span data-ttu-id="2fc40-132">여러 값이 있는 각 매개 변수에 가능한 값 노드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="2fc40-132">For each Parameter that has multiple values, add a possible values node.</span></span>

   <span data-ttu-id="2fc40-133">예로 두 가지 가능한 매개 변수 값을 정의 하는 가능한 값 노드</span><span class="sxs-lookup"><span data-stu-id="2fc40-133">Here is an example of the of a possible values node that defines two possible values for the parameter</span></span>

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

<span data-ttu-id="2fc40-134">매개 변수를 추가할 때 기억해 야 할 몇 가지 사항은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2fc40-134">Here are some things to remember when adding parameters.</span></span>

- <span data-ttu-id="2fc40-135">매개 변수의 특성 cmdlet 도움말 항목의 모든 보기에서 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2fc40-135">The attributes of the parameter are not displayed in all views of the cmdlet Help topic.</span></span> <span data-ttu-id="2fc40-136">그러나 매개 변수 설명 전체에 대 한 사용자 요청 하는 경우 다음 표에 표시 됩니다 (Get-help \<cmdletname >-전체) 또는 매개 변수 (Get-help \<cmdletname >-매개 변수) 항목의 보기입니다.</span><span class="sxs-lookup"><span data-stu-id="2fc40-136">However, they are displayed in a table following the parameter description when the user asks for the Full (Get-Help \<cmdletname> -full) or Parameter (Get-Help \<cmdletname> -parameter) view of the topic.</span></span>

- <span data-ttu-id="2fc40-137">매개 변수 설명에는 cmdlet 도움말 항목의 가장 중요 한 부분 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="2fc40-137">The parameter description is one of the most important parts of a cmdlet Help topic.</span></span> <span data-ttu-id="2fc40-138">간단 하면서도 뿐만 아니라 철저 한에 대 한 설명 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2fc40-138">The description should be brief, as well as thorough.</span></span> <span data-ttu-id="2fc40-139">또한 매개 변수 설명 등 두 개의 매개 변수가 서로 상호 작용 하는 경우 너무 오래 되 면 추가할 수 있습니다 콘텐츠 더 보기 cmdlet 도움말 항목의 NOTES 섹션에서 기억 합니다.</span><span class="sxs-lookup"><span data-stu-id="2fc40-139">Also, remember that if the parameter description becomes too long, such as when two parameters interact with each other, you can add more content in the NOTES section of the cmdlet Help topic.</span></span>

  <span data-ttu-id="2fc40-140">매개 변수 설명을 두 가지 유형의 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="2fc40-140">The parameter description provides two types of information.</span></span>

- <span data-ttu-id="2fc40-141">새로운 cmdlet이 수행 하는 매개 변수를 사용 하는 경우.</span><span class="sxs-lookup"><span data-stu-id="2fc40-141">What the cmdlet does when the parameter is used.</span></span>

- <span data-ttu-id="2fc40-142">유효한 값은 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="2fc40-142">What a legal value is for the parameter.</span></span>

- <span data-ttu-id="2fc40-143">매개 변수 값을.net 개체로 표현 되는 때문에 사용자는 기존의 명령줄 도움말에서 것 보다 이러한 값에 대 한 자세한 내용은 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2fc40-143">Because the parameter values are expressed as .NET Framework objects, users need more information about these values than they would in a traditional command-line Help.</span></span> <span data-ttu-id="2fc40-144">어떤 유형의 데이터를 허용 하도록 매개 변수를 사용자에 게 알림 및 예제가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2fc40-144">Tell the user what type of data the parameter is designed to accept, and include examples.</span></span>

<span data-ttu-id="2fc40-145">매개 변수의 기본값은 명령줄에서 매개 변수를 지정 하지 않으면 사용 되는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="2fc40-145">The default value of the parameter is the value that is used if the parameter is not specified on the command line.</span></span> <span data-ttu-id="2fc40-146">Note 기본값 선택 사항이 며 필요한 매개 변수와 같은 일부 매개 변수에 대해 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2fc40-146">Note that the default value is optional, and is not needed for some parameters, such as required parameters.</span></span> <span data-ttu-id="2fc40-147">그러나 대부분의 선택적 매개 변수 기본값을 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2fc40-147">However, you should specify a default value for most optional parameters.</span></span>

<span data-ttu-id="2fc40-148">기본값 매개 변수를 사용 하지의 효과 이해 하려면 사용자 하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2fc40-148">The default value helps the user to understand the effect of not using the parameter.</span></span> <span data-ttu-id="2fc40-149">기본값을 "현재 디렉터리" 또는 "Windows PowerShell 설치 디렉터리 ($pshome)"를 선택적 경로 같은 매우 특별 하 게 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="2fc40-149">Describe the default value very specifically, such as the "Current directory" or the "Windows PowerShell installation directory ($pshome)" for an optional path.</span></span> <span data-ttu-id="2fc40-150">에 사용 되는 다음 문장 같은 기본값을 설명 하는 문장 작성할 수도 있습니다는 `PassThru` 매개 변수: "PassThru 지정 하지 않으면 cmdlet은 전달 하지 않습니다 개체를 파이프라인."</span><span class="sxs-lookup"><span data-stu-id="2fc40-150">You can also write a sentence that describes the default, such as the following sentence used for the `PassThru` parameter: "If PassThru is not specified, the cmdlet does not pass objects down the pipeline."</span></span>  <span data-ttu-id="2fc40-151">또한 반대 되는 필드 이름 값이 표시 되기 때문에 "**기본값**", 항목의 "기본값" 용어를 포함 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2fc40-151">Also, because the value is displayed opposite the field name "**Default value**", you do not need to include the term "default value" in the entry.</span></span>

<span data-ttu-id="2fc40-152">매개 변수의 기본값 cmdlet 도움말 항목의 모든 보기에서 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2fc40-152">The default value of the parameter is not displayed in all views of the cmdlet Help topic.</span></span> <span data-ttu-id="2fc40-153">그러나 전체에 대 한 사용자 요청 매개 변수 설명에 다음 매개 변수 특성) (함께 표에 표시 됩니다 (Get-help \<cmdletname >-전체) 또는 매개 변수 (Get-help \<cmdletname >-매개 변수) 보기 항목입니다.</span><span class="sxs-lookup"><span data-stu-id="2fc40-153">However, it is displayed in a table (along with the parameter attributes) following the parameter description when the user asks for the Full (Get-Help \<cmdletname> -full) or Parameter (Get-Help \<cmdletname> -parameter) view of the topic.</span></span>

<span data-ttu-id="2fc40-154">다음 XML의 쌍을 보여 줍니다 `<dev:defaultValue>` 에 추가 된 태그는 `<command:parameter>` 노드.</span><span class="sxs-lookup"><span data-stu-id="2fc40-154">The following XML shows a pair of `<dev:defaultValue>` tags added to the `<command:parameter>` node.</span></span> <span data-ttu-id="2fc40-155">기본값 바로 뒤에 오는 닫는 통지 `</command:parameterValue>` (매개 변수 값을 지정 하는) 경우에 태그 또는 닫는 `</maml:description>` 매개 변수 설명의 태그입니다.</span><span class="sxs-lookup"><span data-stu-id="2fc40-155">Notice that the default value follows immediately after the closing `</command:parameterValue>` tag (when the parameter value is specified) or the closing `</maml:description>` tag of the parameter description.</span></span> <span data-ttu-id="2fc40-156">이름입니다.</span><span class="sxs-lookup"><span data-stu-id="2fc40-156">name.</span></span>

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

<span data-ttu-id="2fc40-157">열거형된 형식에 대 한 값을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="2fc40-157">Add Values for Enumerated Types</span></span>

<span data-ttu-id="2fc40-158">매개 변수의 여러 값 또는 열거형 형식의 값이를 사용할 수는 선택적 \<dev:possibleValues > 노드.</span><span class="sxs-lookup"><span data-stu-id="2fc40-158">If the parameter has multiple values or values of an enumerated type, you can use an optional \<dev:possibleValues> node.</span></span> <span data-ttu-id="2fc40-159">이 노드를 사용 하면 이름 및 설명을 여러 값을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2fc40-159">This node allows you to specify a name and description for multiple values.</span></span>

<span data-ttu-id="2fc40-160">열거형된 값의 설명에 표시 되지 않습니다 기본값 중 하나에서 표시 하는 도움말 보기에 유의 합니다 `Get-Help` cmdlet, 하지만 다른 도움말 뷰어는 보기에서이 콘텐츠 표시 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2fc40-160">Be aware that the descriptions of the enumerated values do not appear in any of the default Help views displayed by the `Get-Help` cmdlet, but other Help viewers may display this content in their views.</span></span>

<span data-ttu-id="2fc40-161">에서는 다음 XML `<dev:possibleValues>` 지정 된 두 값을 사용 하 여 노드.</span><span class="sxs-lookup"><span data-stu-id="2fc40-161">The following XML shows a `<dev:possibleValues>` node with two values specified.</span></span>

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