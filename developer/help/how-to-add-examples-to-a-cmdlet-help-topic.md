---
title: 예제 Cmdlet 도움말 항목을 추가 하는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8f723b21-8f95-4981-8b6e-4f07c22d601a
caps.latest.revision: 5
ms.openlocfilehash: b6f8aef76a5f4b5dc1a60425541856ead9a9c77a
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855125"
---
# <a name="how-to-add-examples-to-a-cmdlet-help-topic"></a><span data-ttu-id="8d773-102">Cmdlet 도움말 항목에 예제를 추가하는 방법</span><span class="sxs-lookup"><span data-stu-id="8d773-102">How to Add Examples to a Cmdlet Help Topic</span></span>

## <a name="things-to-know-about-examples-in-cmdlet-help"></a><span data-ttu-id="8d773-103">예제 Cmdlet 도움말에 대해 알아야 할 내용</span><span class="sxs-lookup"><span data-stu-id="8d773-103">Things to Know about Examples in Cmdlet Help</span></span>

- <span data-ttu-id="8d773-104">매개 변수 이름은 선택 사항 하는 경우에 모든 명령에서 매개 변수 이름을 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d773-104">List all of the parameter names in the command, even when the parameter names are optional.</span></span> <span data-ttu-id="8d773-105">그러면 사용자 명령을 쉽게 해석할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d773-105">This helps the user to interpret the command easily.</span></span>

- <span data-ttu-id="8d773-106">Windows PowerShell®에서 작업 하는 경우에 별칭 및 부분 매개 변수 이름에를 방지 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d773-106">Avoid aliases and partial parameter names, even though they work in Windows PowerShell®.</span></span>

- <span data-ttu-id="8d773-107">예제 설명에 유리 명령의 생성을 위한 절차를 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d773-107">In the example description, explain the rational for the construction of the command.</span></span> <span data-ttu-id="8d773-108">특정 매개 변수와 값을 선택한 이유 및 변수를 사용 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d773-108">Explain why you chose particular parameters and values, and how you use variables.</span></span>

- <span data-ttu-id="8d773-109">이 명령은 식을 사용 하는 경우 자세히 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d773-109">If the command uses expressions, explain them in detail.</span></span>

- <span data-ttu-id="8d773-110">이 명령은 개체의 속성 및 메서드를 사용 하는 경우, 기본 표시에 표시 되지 않는 속성 특히 기회를 개체에 대 한 사용자를 알 예제를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d773-110">If the command uses properties and methods of objects, especially properties that do not appear in the default display, use the example as an opportunity tell the user about the object.</span></span>

## <a name="help-views-that-display-examples"></a><span data-ttu-id="8d773-111">예제를 표시 하는 도움말 보기</span><span class="sxs-lookup"><span data-stu-id="8d773-111">Help Views that Display Examples</span></span>

<span data-ttu-id="8d773-112">예제는 cmdlet 도움말의 세부 정보 및 전체 보기에만 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="8d773-112">Examples appear only in the Detailed and Full views of cmdlet Help.</span></span>

## <a name="adding-an-examples-node"></a><span data-ttu-id="8d773-113">예제 노드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="8d773-113">Adding an Examples Node</span></span>

<span data-ttu-id="8d773-114">다음 XML 예제에서는 단일 노드를 포함 하는 예제 노드를 추가 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8d773-114">The following XML shows how to add an Examples node that contains a single Example node.</span></span> <span data-ttu-id="8d773-115">항목에 포함 하려는 각 예제에 대 한 추가 예제 노드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d773-115">Add additional example nodes for each examples you want to include in the topic.</span></span>

```xml
<command:examples>
  <command:example>
  </command:example>
</command:examples>
```

## <a name="adding-an-example-title"></a><span data-ttu-id="8d773-116">예제 제목 추가</span><span class="sxs-lookup"><span data-stu-id="8d773-116">Adding an Example Title</span></span>

<span data-ttu-id="8d773-117">다음 XML 예제에 대 한 제목을 추가 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8d773-117">The following XML shows how to add a title for the example.</span></span> <span data-ttu-id="8d773-118">이 예제에서는 다른 예제 외에도 설정 하는 제목이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d773-118">The title is used to set the example apart from other examples.</span></span> <span data-ttu-id="8d773-119">Windows PowerShell® 순차 예제 수를 포함 하는 표준 헤더를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d773-119">Windows PowerShell® uses a standard header that includes a sequential example number.</span></span>

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
  </command:example>
</command:examples>
```

## <a name="adding-preceding-characters"></a><span data-ttu-id="8d773-120">문자 앞에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d773-120">Adding Preceding Characters</span></span>

<span data-ttu-id="8d773-121">다음 XML 등의 문자를 Windows PowerShell 프롬프트에서 예제 명령을 (중간 공백 없이) 바로 앞에 표시 되는 추가 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8d773-121">The following XML shows how to add characters, such as the Windows PowerShell prompt, that are displayed immediately before the example command (without any intervening spaces).</span></span> <span data-ttu-id="8d773-122">Windows PowerShell®는 Windows PowerShell 프롬프트를 사용합니다. C:\PS>.</span><span class="sxs-lookup"><span data-stu-id="8d773-122">Windows PowerShell® uses the Windows PowerShell prompt: C:\PS>.</span></span>

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
</command:example>
</command:examples>
```

## <a name="adding-the-command"></a><span data-ttu-id="8d773-123">명령 추가</span><span class="sxs-lookup"><span data-stu-id="8d773-123">Adding the Command</span></span>

<span data-ttu-id="8d773-124">다음 XML 예제에서는 실제 명령을 추가 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8d773-124">The following XML shows how to add the actual command of the example.</span></span> <span data-ttu-id="8d773-125">명령에 추가 하는 경우 전체 이름을 입력 (별칭을 사용 하지 마십시오) cmdlet 및 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="8d773-125">When adding the command, type the entire name (do not use alias) of cmdlets and parameters.</span></span> <span data-ttu-id="8d773-126">또한 가능한 경우 항상 소문자를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d773-126">Also, use lowercase characters whenever possible.</span></span>

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
    <dev:code> command </dev:code>
</command:example>
</command:examples>
```

## <a name="adding-a-description"></a><span data-ttu-id="8d773-127">설명 추가</span><span class="sxs-lookup"><span data-stu-id="8d773-127">Adding a Description</span></span>

<span data-ttu-id="8d773-128">다음 XML 예제에 대 한 설명을 추가 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8d773-128">The following XML shows how to add a description for the example.</span></span> <span data-ttu-id="8d773-129">Windows PowerShell® 단일 집합을 사용 하 여 \<maml:para >도 태그에 대 한 여러 \<maml:para > 태그를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d773-129">Windows PowerShell® uses a single set of \<maml:para> tags for the description, even though multiple \<maml:para> tags can be used.</span></span>

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
    <dev:code> command </dev:code>
    <dev:remarks>
      <maml:para> command description </maml:para>
    </dev:remarks>
</command:example>
</command:examples>
```

## <a name="adding-example-output"></a><span data-ttu-id="8d773-130">추가 예제 출력</span><span class="sxs-lookup"><span data-stu-id="8d773-130">Adding Example Output</span></span>

<span data-ttu-id="8d773-131">다음 XML에는 명령의 출력을 추가 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8d773-131">The following XML shows how to add the output of the command.</span></span> <span data-ttu-id="8d773-132">명령 결과 정보는 선택 사항이 있지만 일부 경우에서 특정 매개 변수를 사용 하 여 효과 보여 주기 위해 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d773-132">The command results information is optional, but in some cases it is helpful to demonstrate the effect of using specific parameters.</span></span> <span data-ttu-id="8d773-133">두 개의 빈 집합을 사용 하 여 Windows PowerShell® \<maml:para > 명령에서 명령 출력을 구분 하는 태그입니다.</span><span class="sxs-lookup"><span data-stu-id="8d773-133">Windows PowerShell® uses two sets of blank \<maml:para> tags to separate the command output from the command.</span></span>

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
    <dev:code> command </dev:code>
    <dev:remarks>
      <maml:para> command description </maml:para>
      <maml:para></maml:para>
      <maml:para></maml:para>
      <maml:para> command output </maml:para>
</dev:remarks>
</command:example>
</command:examples>
```