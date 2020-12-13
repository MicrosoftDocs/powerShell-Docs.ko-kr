---
ms.date: 09/12/2016
ms.topic: reference
title: Cmdlet 도움말 항목에 입력 형식을 추가하는 방법
description: Cmdlet 도움말 항목에 입력 형식을 추가하는 방법
ms.openlocfilehash: f2ad87c54230bcdd7e0ea708e9a1869daef7495f
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "94391105"
---
# <a name="how-to-add-input-types-to-a-cmdlet-help-topic"></a><span data-ttu-id="a1419-103">Cmdlet 도움말 항목에 입력 형식을 추가하는 방법</span><span class="sxs-lookup"><span data-stu-id="a1419-103">How to Add Input Types to a Cmdlet Help Topic</span></span>

<span data-ttu-id="a1419-104">이 섹션에서는 PowerShell cmdlet 도움말 항목에 **입력** 섹션을 추가 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1419-104">This section describes how to add an **INPUTS** section to a PowerShell cmdlet Help topic.</span></span> <span data-ttu-id="a1419-105">**입력** 섹션에는 cmdlet이 파이프라인에서 입력으로 허용 하는 개체의 .net 클래스 (값 또는 속성 이름)가 나열 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1419-105">The **INPUTS** section lists the .NET classes of objects that the cmdlet accepts as input from the pipeline, either by value or by property name.</span></span>

<span data-ttu-id="a1419-106">**입력** 섹션에 추가할 수 있는 클래스 수에는 제한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a1419-106">There is no limit to the number of classes that you can add to an **INPUTS** section.</span></span> <span data-ttu-id="a1419-107">입력 형식은 `<command:inputTypes>` 각 클래스가 요소로 묶여 있는 노드에 포함 됩니다 `<command:inputType>` .</span><span class="sxs-lookup"><span data-stu-id="a1419-107">The input types are enclosed in a `<command:inputTypes>` node, with each class enclosed in a `<command:inputType>` element.</span></span>

<span data-ttu-id="a1419-108">이 스키마는 `<maml:description>` 각 요소에 두 개의 요소를 포함 `<command:inputType>` 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1419-108">The schema includes two `<maml:description>` elements in each `<command:inputType>` element.</span></span>
<span data-ttu-id="a1419-109">그러나이 `Get-Help` cmdlet은 요소의 콘텐츠만 표시 합니다 `<command:inputType>/<maml:description>` .</span><span class="sxs-lookup"><span data-stu-id="a1419-109">However, the `Get-Help` cmdlet displays only the content of the `<command:inputType>/<maml:description>` element.</span></span>

<span data-ttu-id="a1419-110">PowerShell 3.0부터 `Get-Help` cmdlet은 요소의 내용을 표시 합니다 `<maml:uri>` .</span><span class="sxs-lookup"><span data-stu-id="a1419-110">Beginning in PowerShell 3.0, the `Get-Help` cmdlet displays the content of the `<maml:uri>` element.</span></span>
<span data-ttu-id="a1419-111">이 요소를 사용 하 여 .NET 클래스를 설명 하는 항목으로 사용자를 지시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1419-111">This element lets you direct users to topics that describe the .NET class.</span></span>

<span data-ttu-id="a1419-112">다음 XML에서는 노드를 보여 줍니다 `<maml:inputTypes>` .</span><span class="sxs-lookup"><span data-stu-id="a1419-112">The following XML shows the `<maml:inputTypes>` node.</span></span>

```xml
<command:inputTypes>
  <command:inputType>
    <dev:type>
      <maml:name> Class name </maml:name>
      <maml:uri>  URI of a topic that describes the class </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> Brief description </maml:para>
    </maml:description>
  </command:inputType>
</command:inputTypes>
```

<span data-ttu-id="a1419-113">다음 XML에서는 노드를 사용 하 여 입력 유형을 문서화 하는 예를 보여 줍니다 `<maml:inputTypes>` .</span><span class="sxs-lookup"><span data-stu-id="a1419-113">The following XML shows an example of using the `<maml:inputTypes>` node to document an input type.</span></span>

```xml
<command:inputTypes>
  <command:inputType>
    <dev:type>
      <maml:name>System.DateTime</maml:name>
      <maml:uri>https://docs.microsoft.com/dotnet/api/system.datetime</maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> You can pipe a date to the Set-Date cmdlet. <maml:para>
    <maml:description>
  </command:inputType>
</command:inputTypes>
```
