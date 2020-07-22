---
title: Cmdlet 도움말 항목에 메모를 추가하는 방법
ms.date: 09/12/2016
ms.openlocfilehash: d3679126ea34d7e86bcda700d0d050d8312a7aa2
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893410"
---
# <a name="how-to-add-notes-to-a-cmdlet-help-topic"></a><span data-ttu-id="c8236-102">Cmdlet 도움말 항목에 메모를 추가하는 방법</span><span class="sxs-lookup"><span data-stu-id="c8236-102">How to Add Notes to a Cmdlet Help Topic</span></span>

<span data-ttu-id="c8236-103">이 섹션에서는 PowerShell cmdlet 도움말 항목에 **NOTES** 섹션을 추가 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8236-103">This section describes how to add a **NOTES** section to a PowerShell cmdlet Help topic.</span></span> <span data-ttu-id="c8236-104">**참고** 섹션은 매개 변수에 대 한 자세한 설명과 같이 다른 구조화 된 섹션에 쉽게 맞지 않는 세부 정보를 설명 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8236-104">The **NOTES** section is used to explain details that do not fit easily into the other structured sections, such as a more detailed explanation of a parameter.</span></span> <span data-ttu-id="c8236-105">이 콘텐츠에는 cmdlet이 특정 공급자와 작동 하는 방식, 몇 가지 고유 하 고 중요 한 cmdlet의 용도 또는 가능한 오류 조건을 방지 하는 방법에 대 한 설명을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8236-105">This content could include comments on how the cmdlet works with a specific provider, some unique, yet important, uses of the cmdlet, or ways to avoid possible error conditions.</span></span>

<span data-ttu-id="c8236-106">참고 섹션에 추가할 수 있는 메모 수에는 제한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c8236-106">There are no limits to the number of notes that you can add to a Notes section.</span></span> <span data-ttu-id="c8236-107">각 메모에 대해 노드에 태그 쌍을 추가 `<maml:alert>` `<maml:alertset>` 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8236-107">For each note, add a pair of `<maml:alert>` tags to the `<maml:alertset>` node.</span></span> <span data-ttu-id="c8236-108">각 메모의 내용은 태그 집합 내에 추가 됩니다 `<maml:para>` .</span><span class="sxs-lookup"><span data-stu-id="c8236-108">The content of each note is added within a set of `<maml:para>` tags.</span></span> <span data-ttu-id="c8236-109">공백 `<maml:para>` 에는 빈 태그를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8236-109">Use blank `<maml:para>` tags for spacing.</span></span>

<span data-ttu-id="c8236-110">다음 XML에서는 `<maml:alertset>` 두 개의 노트가 있는 노드를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c8236-110">The following XML shows an `<maml:alertset>` node with two notes.</span></span> <span data-ttu-id="c8236-111">각 메모에는 선택적 태그가 있으며 `<maml:title>` (제목은 모든 태그 집합을 그룹화 하는 데 사용 될 수 있음 `<maml:alert>` ) 각 메모에는 공백에 대 한 콘텐츠 다음에 빈 줄이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8236-111">Notice that each note has an optional `<maml:title>` tag (titles can be used to group any set of `<maml:alert>` tags), and that each note has a blank line following the content for spacing.</span></span>

```xml
<maml:alertSet>
  <maml:title>title for Note 1</maml:title>
  <maml:alert>
    <maml:para> Note 1</maml:para>
    <maml:para></maml:para>
  </maml:alert>
  <maml:title>title for Note 2</maml:title>
  <maml:alert>
    <maml:para> Note 1</maml:para>
    <maml:para></maml:para>
  </maml:alert>
</maml:alertSet>
```
