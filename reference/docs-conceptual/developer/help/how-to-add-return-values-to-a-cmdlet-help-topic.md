---
ms.date: 09/12/2016
ms.topic: reference
title: Cmdlet 도움말 항목에 반환 값을 추가하는 방법
description: Cmdlet 도움말 항목에 반환 값을 추가하는 방법
ms.openlocfilehash: 8c556821a257451a320916231cb20fc82e75ebb4
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "94389745"
---
# <a name="how-to-add-return-values-to-a-cmdlet-help-topic"></a><span data-ttu-id="a881a-103">Cmdlet 도움말 항목에 반환 값을 추가하는 방법</span><span class="sxs-lookup"><span data-stu-id="a881a-103">How to Add Return Values to a Cmdlet Help Topic</span></span>

<span data-ttu-id="a881a-104">이 섹션에서는 PowerShell cmdlet 도움말 항목에 출력 섹션을 추가 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="a881a-104">This section describes how to add an OUTPUTS section to a PowerShell cmdlet Help topic.</span></span> <span data-ttu-id="a881a-105">**출력** 섹션에는 cmdlet이 파이프라인을 반환 하거나 전달 하는 개체의 .net 클래스가 나열 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a881a-105">The **OUTPUTS** section lists the .NET classes of objects that the cmdlet returns or passes down the pipeline.</span></span>

<span data-ttu-id="a881a-106">**출력** 섹션에 추가할 수 있는 클래스의 수에는 제한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a881a-106">There is no limit to the number of classes that you can add to the **OUTPUTS** section.</span></span> <span data-ttu-id="a881a-107">Cmdlet의 반환 형식은 `<command:returnValues>` 각 클래스가 요소로 묶여 있는 노드에 포함 됩니다 `<command:returnValue>` .</span><span class="sxs-lookup"><span data-stu-id="a881a-107">The return types of a cmdlet are enclosed in a `<command:returnValues>` node, with each class enclosed in a `<command:returnValue>` element.</span></span>

<span data-ttu-id="a881a-108">Cmdlet에서 출력을 생성 하지 않는 경우이 섹션을 사용 하 여 출력이 없음을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a881a-108">If a cmdlet does not generate any output, use this section to indicate that there is no output.</span></span> <span data-ttu-id="a881a-109">예를 들어 클래스 이름 대신 **None** 을 작성 하 고 간략 한 설명을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="a881a-109">For example, in place of the class name, write **None** and provide a brief explanation.</span></span> <span data-ttu-id="a881a-110">Cmdlet이 조건에 따라 출력을 생성 하는 경우이 노드를 사용 하 여 조건을 설명 하 고 조건부 출력을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="a881a-110">If the cmdlet generates output conditionally, use this node to explain the conditions and describe the conditional output.</span></span>

<span data-ttu-id="a881a-111">이 스키마는 `<maml:description>` 각 요소에 두 개의 요소를 포함 `<command:returnValue>` 합니다.</span><span class="sxs-lookup"><span data-stu-id="a881a-111">The schema includes two `<maml:description>` elements in each `<command:returnValue>` element.</span></span>
<span data-ttu-id="a881a-112">그러나이 `Get-Help` cmdlet은 요소의 콘텐츠만 표시 합니다 `<command:returnValue>/<maml:description>` .</span><span class="sxs-lookup"><span data-stu-id="a881a-112">However, the `Get-Help` cmdlet displays only the content of the `<command:returnValue>/<maml:description>` element.</span></span>

<span data-ttu-id="a881a-113">PowerShell 3.0부터 `Get-Help` cmdlet은 요소의 내용을 표시 합니다 `<maml:uri>` .</span><span class="sxs-lookup"><span data-stu-id="a881a-113">Beginning in PowerShell 3.0, the `Get-Help` cmdlet displays the content of the `<maml:uri>` element.</span></span>
<span data-ttu-id="a881a-114">이 요소를 사용 하 여 .NET 클래스를 설명 하는 항목으로 사용자를 지시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a881a-114">This element lets you direct users to topics that describe the .NET class.</span></span>

<span data-ttu-id="a881a-115">다음 XML에서는 노드를 보여 줍니다 `<maml:returnValues>` .</span><span class="sxs-lookup"><span data-stu-id="a881a-115">The following XML shows the `<maml:returnValues>` node.</span></span>

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

<span data-ttu-id="a881a-116">다음 XML에서는 노드를 사용 하 여 출력 형식을 문서화 하는 예를 보여 줍니다 `<maml:returnValues>` .</span><span class="sxs-lookup"><span data-stu-id="a881a-116">The following XML shows an example of using the `<maml:returnValues>` node to document an output type.</span></span>

```xml
<command:returnValues>
  <command:returnValue>
    <dev:type>
      <maml:name> System.DateTime </maml:name>
      <maml:uri>  https://docs.microsoft.com/dotnet/api/system.datetime </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> Get-Date returns a DateTime object. <maml:para>
    </maml:description>
  </command: returnValue>
</command: returnValues>
```
