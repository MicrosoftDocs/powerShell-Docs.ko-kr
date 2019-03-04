---
title: Cmdlet 도움말 항목에 메모를 추가 하는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2bea35e5-b680-4f86-b928-176890aac99d
caps.latest.revision: 5
ms.openlocfilehash: 4e9ca9a3bbcbc900d079b9275bc47d21de9e2996
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862269"
---
# <a name="how-to-add-notes-to-a-cmdlet-help-topic"></a><span data-ttu-id="41497-102">Cmdlet 도움말 항목에 메모를 추가하는 방법</span><span class="sxs-lookup"><span data-stu-id="41497-102">How to Add Notes to a Cmdlet Help Topic</span></span>

<span data-ttu-id="41497-103">이 섹션에서는 참고 섹션 Windows PowerShell® cmdlet 도움말 항목을 추가 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="41497-103">This section describes how to add a Notes section to a Windows PowerShell® cmdlet Help topic.</span></span> <span data-ttu-id="41497-104">참고 섹션에 맞지 않고 쉽게 다른 구조적된 섹션, 매개 변수의 자세한 설명 같은 세부 정보를 설명 하기 위해 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="41497-104">The Notes section is used to explain details that do not fit easily into the other structured sections, such as a more detailed explanation of a parameter.</span></span> <span data-ttu-id="41497-105">이 콘텐츠는 특정 공급자를 사용 하 여 cmdlet이 작동 하는 방법, cmdlet 또는 가능한 오류 상태를 방지 하는 방법의 몇 가지 고유 하면서도 중요 한, 사용에 대 한 의견을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41497-105">This content could include comments on how the cmdlet works with a specific provider, some unique, yet important, uses of the cmdlet, or ways to avoid possible error conditions.</span></span>

<span data-ttu-id="41497-106">참고 사항 섹션에 추가할 수 있는 주석의 수에 한도가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41497-106">There are no limits to the number of notes that you can add to a Notes section.</span></span> <span data-ttu-id="41497-107">각 메모에 대 한 쌍을 추가 \<maml:alert > 태그를 \<maml:alertset > 노드.</span><span class="sxs-lookup"><span data-stu-id="41497-107">For each note, add a pair of \<maml:alert> tags to the \<maml:alertset> node.</span></span> <span data-ttu-id="41497-108">각 메모의 콘텐츠 집합에 추가 됩니다 \<maml:para > 태그입니다.</span><span class="sxs-lookup"><span data-stu-id="41497-108">The content of each note is added within a set of \<maml:para> tags.</span></span> <span data-ttu-id="41497-109">사용 하 여 빈 \<maml:para > 간격에 대 한 태그입니다.</span><span class="sxs-lookup"><span data-stu-id="41497-109">Use blank \<maml:para> tags for spacing.</span></span>

<span data-ttu-id="41497-110">에서는 다음 XML \<maml:alertset > 두 가지 정보를 사용 하 여 노드.</span><span class="sxs-lookup"><span data-stu-id="41497-110">The following XML shows an \<maml:alertset> node with two notes.</span></span> <span data-ttu-id="41497-111">각 메모는 선택적인 \<maml:title > 태그 (제목을 사용 하 여 집합이 그룹화 할 수 있습니다 \<maml:alert > 태그), 그리고 각 참고 간격에 대 한 콘텐츠를 다음 빈 줄에 합니다.</span><span class="sxs-lookup"><span data-stu-id="41497-111">Notice that each note has an optional \<maml:title> tag (titles can be used to group any set of \<maml:alert> tags), and that each note has a blank line following the content for spacing.</span></span>

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



