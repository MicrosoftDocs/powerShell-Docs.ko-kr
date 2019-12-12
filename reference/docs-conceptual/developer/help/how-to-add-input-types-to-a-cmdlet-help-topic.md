---
title: Cmdlet 도움말 항목에 입력 유형을 추가 하는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 432798e4-5d69-46b1-9517-ff09bffaa4be
caps.latest.revision: 7
ms.openlocfilehash: f213605dda0132051d983f8608515325e815c455
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361242"
---
# <a name="how-to-add-input-types-to-a-cmdlet-help-topic"></a><span data-ttu-id="75eea-102">Cmdlet 도움말 항목에 입력 형식을 추가하는 방법</span><span class="sxs-lookup"><span data-stu-id="75eea-102">How to Add Input Types to a Cmdlet Help Topic</span></span>

<span data-ttu-id="75eea-103">이 섹션에서는 Windows PowerShell® cmdlet 도움말 항목에 입력 섹션을 추가 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="75eea-103">This section describes how to add an INPUTS section to a Windows PowerShell® cmdlet Help topic.</span></span> <span data-ttu-id="75eea-104">입력 섹션에는 cmdlet이 파이프라인에서 입력으로 허용 하는 개체의 .NET 클래스 (값 또는 속성 이름)가 나열 됩니다.</span><span class="sxs-lookup"><span data-stu-id="75eea-104">The INPUTS section lists the .NET classes of objects that the cmdlet accepts as input from the pipeline, either by value or by property name.</span></span>

<span data-ttu-id="75eea-105">입력 섹션에 추가할 수 있는 클래스 수에는 제한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="75eea-105">There is no limit to the number of classes that you can add to an INPUTS section.</span></span> <span data-ttu-id="75eea-106">입력 형식은 \<명령: inputTypes > 노드로 묶여 있으며 각 클래스는 \<명령: inputType > 요소에 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="75eea-106">The input types are enclosed in a \<command:inputTypes> node, with each class enclosed in a  \<command:inputType> element.</span></span>

<span data-ttu-id="75eea-107">이 스키마에는 각 \<command: inputType > 요소에 두 개의 \<maml: description > 요소가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75eea-107">The schema includes two \<maml:description> elements in each \<command:inputType> element.</span></span> <span data-ttu-id="75eea-108">그러나 `Get-Help` cmdlet은 \<명령의 inputType >/\<maml: description >) 요소만 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="75eea-108">However, the `Get-Help` cmdlet displays only the content of the \<command:inputType>/\<maml:description>) element.</span></span>

<span data-ttu-id="75eea-109">Windows PowerShell 3.0부터 `Get-Help` cmdlet은 \<maml: uri > 요소의 내용을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="75eea-109">Beginning in Windows PowerShell 3.0, the `Get-Help` cmdlet displays the content of the \<maml:uri> element.</span></span> <span data-ttu-id="75eea-110">이 요소를 사용 하 여 .NET 클래스를 설명 하는 항목으로 사용자를 지시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75eea-110">This element lets you direct users to topics that describe the .NET class.</span></span>

<span data-ttu-id="75eea-111">다음 XML은 \<maml: inputTypes > 노드를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="75eea-111">The following XML shows the \<maml:inputTypes> node.</span></span>

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

<span data-ttu-id="75eea-112">다음 XML은 \<maml: inputTypes > 노드를 사용 하 여 입력 유형을 문서화 하는 예를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="75eea-112">The following XML shows an example of using the \<maml:inputTypes> node to document an input type.</span></span>

```xml
<command:inputTypes>
  <command:inputType>
    <dev:type>
      <maml:name> System.DateTime </maml:name>
      <maml:uri>  http://msdn.microsoft.com/library/system.datetime.aspx </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> You can pipe a date to the Set-Date cmdlet. <maml:para>
    <maml:description>
  </command:inputType>
</command:inputTypes>
```