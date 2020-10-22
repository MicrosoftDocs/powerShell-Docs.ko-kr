---
title: Cmdlet 도움말 항목에 메모를 추가하는 방법
ms.date: 10/20/2020
ms.openlocfilehash: 7f8be34a82de2c12cfd2a05deed139ddb30da95f
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/21/2020
ms.locfileid: "92298306"
---
# <a name="how-to-add-notes-to-a-cmdlet-help-topic"></a><span data-ttu-id="7e7d5-102">Cmdlet 도움말 항목에 메모를 추가하는 방법</span><span class="sxs-lookup"><span data-stu-id="7e7d5-102">How to Add Notes to a Cmdlet Help Topic</span></span>

<span data-ttu-id="7e7d5-103">이 섹션에서는 PowerShell cmdlet 도움말 항목에 **참고** 섹션을 추가하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="7e7d5-103">This section describes how to add a **NOTES** section to a PowerShell cmdlet Help topic.</span></span> <span data-ttu-id="7e7d5-104">**참고** 섹션은 매개 변수에 대한 자세한 설명과 같이 다른 구조화된 섹션에 잘 맞지 않는 세부 정보를 설명하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="7e7d5-104">The **NOTES** section is used to explain details that do not fit easily into the other structured sections, such as a more detailed explanation of a parameter.</span></span> <span data-ttu-id="7e7d5-105">이 콘텐츠는 일부 고유하지만 중요한 특정 공급자에서 cmdlet이 작동하는 방법, cmdlet의 용도 또는 발생 가능한 오류 조건을 방지하는 방법에 대한 설명을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e7d5-105">This content could include comments on how the cmdlet works with a specific provider, some unique, yet important, uses of the cmdlet, or ways to avoid possible error conditions.</span></span>

<span data-ttu-id="7e7d5-106">**참고** 섹션은 단일 `<maml:alertset>` 노드를 사용하여 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="7e7d5-106">The **NOTES** section is defined using a single `<maml:alertset>` node.</span></span> <span data-ttu-id="7e7d5-107">참고 섹션에 추가할 수 있는 메모 수에는 제한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7e7d5-107">There are no limits to the number of notes that you can add to a Notes section.</span></span> <span data-ttu-id="7e7d5-108">각 메모에 대해 `<maml:alertset>` 노드에 `<maml:alert>` 태그 쌍을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="7e7d5-108">For each note, add a pair of `<maml:alert>` tags to the `<maml:alertset>` node.</span></span> <span data-ttu-id="7e7d5-109">각 메모의 내용은 `<maml:para>` 태그 집합 내에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="7e7d5-109">The content of each note is added within a set of `<maml:para>` tags.</span></span> <span data-ttu-id="7e7d5-110">공백에는 빈 `<maml:para>` 태그를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="7e7d5-110">Use blank `<maml:para>` tags for spacing.</span></span>

```xml
<maml:alertSet>
  <maml:title>Optional title for Note</maml:title>
  <maml:alert>
    <maml:para>Note 1</maml:para>
    <maml:para>Note a</maml:para>
  </maml:alert>
  <maml:alert>
    <maml:para>Note 2</maml:para>
  </maml:alert>
</maml:alertSet>
```
