---
title: Cmdlet 도움말 항목에 반환 값을 추가 하는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a52ab737-753c-4d04-8af7-758d5c805e18
caps.latest.revision: 7
ms.openlocfilehash: ad0fe5c63b145c681f14328d5ef5a8784a035e26
ms.sourcegitcommit: bc9a4904c2b1561386d748fc9ac242699d2f1694
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/04/2020
ms.locfileid: "76995941"
---
# <a name="how-to-add-return-values-to-a-cmdlet-help-topic"></a><span data-ttu-id="7712e-102">Cmdlet 도움말 항목에 반환 값을 추가하는 방법</span><span class="sxs-lookup"><span data-stu-id="7712e-102">How to Add Return Values to a Cmdlet Help Topic</span></span>

<span data-ttu-id="7712e-103">이 섹션에서는 Windows PowerShell® cmdlet 도움말 항목에 출력 섹션을 추가 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="7712e-103">This section describes how to add an OUTPUTS section to a Windows PowerShell® cmdlet Help topic.</span></span> <span data-ttu-id="7712e-104">출력 섹션에는 cmdlet이 파이프라인을 반환 하거나 전달 하는 개체의 .NET 클래스가 나열 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7712e-104">The OUTPUTS section lists the .NET classes of objects that the cmdlet returns or passes down the pipeline.</span></span>

<span data-ttu-id="7712e-105">출력 섹션에 추가할 수 있는 클래스의 수에는 제한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7712e-105">There is no limit to the number of classes that you can add to the OUTPUTS section.</span></span> <span data-ttu-id="7712e-106">Cmdlet의 반환 형식은 \<command: returnValues > node로 묶여 있으며 각 클래스는 \<command: returnValue > 요소에 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7712e-106">The return types of a cmdlet are enclosed in a \<command:returnValues> node, with each class enclosed in a \<command:returnValue> element.</span></span>

<span data-ttu-id="7712e-107">Cmdlet에서 출력을 생성 하지 않는 경우이 섹션을 사용 하 여 출력이 없음을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="7712e-107">If a cmdlet does not generate any output, use this section to indicate that there is no output.</span></span> <span data-ttu-id="7712e-108">예를 들어 클래스 이름 대신 "None"을 작성 하 고 간략 한 설명을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="7712e-108">For example, in place of the class name, write "None" and provide a brief explanation.</span></span> <span data-ttu-id="7712e-109">Cmdlet이 조건에 따라 출력을 생성 하는 경우이 노드를 사용 하 여 조건을 설명 하 고 조건부 출력을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="7712e-109">If the cmdlet generates output conditionally, use this node to explain the conditions and describe the conditional output.</span></span>

<span data-ttu-id="7712e-110">이 스키마에는 각 \<명령에 \<maml: description > 요소가 포함 됩니다. returnValue > 요소.</span><span class="sxs-lookup"><span data-stu-id="7712e-110">The schema includes two \<maml:description> elements in each \<command:returnValue> element.</span></span> <span data-ttu-id="7712e-111">그러나 `Get-Help` cmdlet은 \<명령의 콘텐츠만 표시 합니다. returnValue >/\<maml: description > 요소.</span><span class="sxs-lookup"><span data-stu-id="7712e-111">However, the `Get-Help` cmdlet displays only the content of the \<command:returnValue>/\<maml:description> element.</span></span>

<span data-ttu-id="7712e-112">Windows PowerShell 3.0부터 `Get-Help` cmdlet은 \<maml: uri > 요소의 내용을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="7712e-112">Beginning in Windows PowerShell 3.0, the `Get-Help` cmdlet displays the content of the \<maml:uri> element.</span></span> <span data-ttu-id="7712e-113">이 요소를 사용 하 여 .NET 클래스를 설명 하는 항목으로 사용자를 지시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7712e-113">This element lets you direct users to topics that describe the .NET class.</span></span>

<span data-ttu-id="7712e-114">다음 XML은 \<maml: returnValues > 노드를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7712e-114">The following XML shows the \<maml:returnValues> node.</span></span>

```xml
<command:returnValues>
  <command:returnValue>
    <dev:type>
      <maml:name> Class Name </maml:name>
      <maml:uri>  URI of a topic that describes the class </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
       <maml:para> Brief description <maml:para>

</maml:description>
  </command: returnValue>
</command: returnValues>
```

<span data-ttu-id="7712e-115">다음 XML에서는 \<maml: returnValues > 노드를 사용 하 여 출력 형식을 문서화 하는 예를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7712e-115">The following XML shows an example of using the \<maml:returnValues> node to document an output type.</span></span>

```xml
<command:returnValues>
  <command:returnValue>
    <dev:type>
      <maml:name> System.DateTime </maml:name>
      <maml:uri>  https://msdn.microsoft.com/library/system.datetime.aspx </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> Get-Date returns a DateTime object. <maml:para>
    </maml:description>
  </command: returnValue>
</command: returnValues>
```



