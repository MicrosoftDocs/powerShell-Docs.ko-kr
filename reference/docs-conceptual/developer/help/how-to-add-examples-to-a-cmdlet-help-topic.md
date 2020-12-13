---
ms.date: 09/12/2016
ms.topic: reference
title: Cmdlet 도움말 항목에 예제를 추가하는 방법
description: Cmdlet 도움말 항목에 예제를 추가하는 방법
ms.openlocfilehash: 6b72e29c93740b7953d9b68fc8e68c02eb2f4dee
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92654725"
---
# <a name="how-to-add-examples-to-a-cmdlet-help-topic"></a><span data-ttu-id="55451-103">Cmdlet 도움말 항목에 예제를 추가하는 방법</span><span class="sxs-lookup"><span data-stu-id="55451-103">How to Add Examples to a Cmdlet Help Topic</span></span>

## <a name="things-to-know-about-examples-in-cmdlet-help"></a><span data-ttu-id="55451-104">Cmdlet 도움말의 예제에 대해 알아야 할 사항</span><span class="sxs-lookup"><span data-stu-id="55451-104">Things to Know about Examples in Cmdlet Help</span></span>

- <span data-ttu-id="55451-105">매개 변수 이름이 선택적인 경우에도 명령의 모든 매개 변수 이름을 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="55451-105">List all of the parameter names in the command, even when the parameter names are optional.</span></span> <span data-ttu-id="55451-106">이렇게 하면 사용자가 명령을 쉽게 해석할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="55451-106">This helps the user to interpret the command easily.</span></span>

- <span data-ttu-id="55451-107">PowerShell에서 작동 하는 경우에도 별칭 및 부분 매개 변수 이름을 사용 하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="55451-107">Avoid aliases and partial parameter names, even though they work in PowerShell.</span></span>

- <span data-ttu-id="55451-108">예제 설명에서 명령의 생성에 대 한 유리수를 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="55451-108">In the example description, explain the rational for the construction of the command.</span></span> <span data-ttu-id="55451-109">특정 매개 변수 및 값을 선택한 이유와 변수를 사용 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="55451-109">Explain why you chose particular parameters and values, and how you use variables.</span></span>

- <span data-ttu-id="55451-110">명령에서 식을 사용 하는 경우이를 자세히 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="55451-110">If the command uses expressions, explain them in detail.</span></span>

- <span data-ttu-id="55451-111">명령에서 개체의 속성 및 메서드를 사용 하는 경우, 특히 기본 표시에 표시 되지 않는 속성을 사용 하는 경우 사용자에 게 개체에 대 한 지시를 제공 하는 기회로 예제를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="55451-111">If the command uses properties and methods of objects, especially properties that do not appear in the default display, use the example as an opportunity tell the user about the object.</span></span>

## <a name="help-views-that-display-examples"></a><span data-ttu-id="55451-112">예제를 표시 하는 도움말 보기</span><span class="sxs-lookup"><span data-stu-id="55451-112">Help Views that Display Examples</span></span>

<span data-ttu-id="55451-113">예제는 cmdlet 도움말의 상세 및 전체 뷰에만 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="55451-113">Examples appear only in the Detailed and Full views of cmdlet Help.</span></span>

## <a name="adding-an-examples-node"></a><span data-ttu-id="55451-114">예제 노드 추가</span><span class="sxs-lookup"><span data-stu-id="55451-114">Adding an Examples Node</span></span>

<span data-ttu-id="55451-115">다음 XML에서는 단일 **예제** 노드가 포함 된 **예제** 노드를 추가 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="55451-115">The following XML shows how to add an **Examples** node that contains a single **Example** node.</span></span> <span data-ttu-id="55451-116">항목에 포함 하려는 각 예제에 대 한 추가 예제 노드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="55451-116">Add additional example nodes for each examples you want to include in the topic.</span></span>

```xml
<command:examples>
  <command:example>
  </command:example>
</command:examples>
```

## <a name="adding-an-example-title"></a><span data-ttu-id="55451-117">예제 제목 추가</span><span class="sxs-lookup"><span data-stu-id="55451-117">Adding an Example Title</span></span>

<span data-ttu-id="55451-118">다음 XML은 예제의 **제목을** 추가 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="55451-118">The following XML shows how to add a **title** for the example.</span></span> <span data-ttu-id="55451-119">**제목은** 다른 예제와는 별도로 예제를 설정 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="55451-119">The **title** is used to set the example apart from other examples.</span></span> <span data-ttu-id="55451-120">PowerShell은 순차 예제 번호를 포함 하는 표준 헤더를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="55451-120">PowerShell uses a standard header that includes a sequential example number.</span></span>

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
  </command:example>
</command:examples>
```

## <a name="adding-preceding-characters"></a><span data-ttu-id="55451-121">선행 문자 추가</span><span class="sxs-lookup"><span data-stu-id="55451-121">Adding Preceding Characters</span></span>

<span data-ttu-id="55451-122">다음 XML은 예 명령 바로 앞에 표시 되는 Windows PowerShell 프롬프트와 같은 문자를 추가 하는 방법을 보여 줍니다 (중간 공간 제외).</span><span class="sxs-lookup"><span data-stu-id="55451-122">The following XML shows how to add characters, such as the Windows PowerShell prompt, that are displayed immediately before the example command (without any intervening spaces).</span></span> <span data-ttu-id="55451-123">PowerShell에서는 Windows PowerShell 프롬프트를 사용 `C:\PS>` 합니다.</span><span class="sxs-lookup"><span data-stu-id="55451-123">PowerShell uses the Windows PowerShell prompt: `C:\PS>`.</span></span>

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

## <a name="adding-the-command"></a><span data-ttu-id="55451-124">명령 추가</span><span class="sxs-lookup"><span data-stu-id="55451-124">Adding the Command</span></span>

<span data-ttu-id="55451-125">다음 XML은 예제의 실제 명령을 추가 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="55451-125">The following XML shows how to add the actual command of the example.</span></span> <span data-ttu-id="55451-126">명령을 추가할 때 cmdlet 및 매개 변수의 전체 이름 (별칭 사용 안 함)을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="55451-126">When adding the command, type the entire name (do not use alias) of cmdlets and parameters.</span></span> <span data-ttu-id="55451-127">또한 가능한 경우 소문자를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="55451-127">Also, use lowercase characters whenever possible.</span></span>

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

## <a name="adding-a-description"></a><span data-ttu-id="55451-128">설명 추가</span><span class="sxs-lookup"><span data-stu-id="55451-128">Adding a Description</span></span>

<span data-ttu-id="55451-129">다음 XML은 예제에 대 한 설명을 추가 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="55451-129">The following XML shows how to add a description for the example.</span></span> <span data-ttu-id="55451-130">`<maml:para>`여러 태그를 사용할 수 있는 경우에도 PowerShell은 설명에 대해 단일 태그 집합을 사용 `<maml:para>` 합니다.</span><span class="sxs-lookup"><span data-stu-id="55451-130">PowerShell uses a single set of `<maml:para>` tags for the description, even though multiple `<maml:para>` tags can be used.</span></span>

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

## <a name="adding-example-output"></a><span data-ttu-id="55451-131">예제 출력 추가</span><span class="sxs-lookup"><span data-stu-id="55451-131">Adding Example Output</span></span>

<span data-ttu-id="55451-132">다음 XML에서는 명령의 출력을 추가 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="55451-132">The following XML shows how to add the output of the command.</span></span> <span data-ttu-id="55451-133">명령 결과 정보는 선택 사항 이지만 경우에 따라 특정 매개 변수를 사용 하는 경우의 영향을 보여 주는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="55451-133">The command results information is optional, but in some cases it is helpful to demonstrate the effect of using specific parameters.</span></span>
<span data-ttu-id="55451-134">PowerShell에서는 두 개의 빈 태그 집합을 사용 하 여 명령 `<maml:para>` 출력을 명령에서 분리 합니다.</span><span class="sxs-lookup"><span data-stu-id="55451-134">PowerShell uses two sets of blank `<maml:para>` tags to separate the command output from the command.</span></span>

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
