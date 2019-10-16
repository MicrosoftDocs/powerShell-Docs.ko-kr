---
title: Cmdlet 도움말 항목에 관련 링크를 추가 하는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5aadb730-4eb7-4936-b8df-3b0c0ca04fd5
caps.latest.revision: 5
ms.openlocfilehash: aa46cbc5bfcfdfec9fcf9d2581ff641baa532860
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361222"
---
# <a name="how-to-add-related-links-to-a-cmdlet-help-topic"></a><span data-ttu-id="196f7-102">Cmdlet 도움말 항목에 관련 링크를 추가하는 방법</span><span class="sxs-lookup"><span data-stu-id="196f7-102">How to Add Related Links to a Cmdlet Help Topic</span></span>

<span data-ttu-id="196f7-103">이 섹션에서는 Windows PowerShell® cmdlet 도움말 항목과 관련 된 다른 콘텐츠에 대 한 참조를 추가 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="196f7-103">This section describes how to add references to other content that is related to a Windows PowerShell® cmdlet Help topic.</span></span> <span data-ttu-id="196f7-104">이러한 참조는 명령 창에 표시 되기 때문에 참조 된 콘텐츠에 직접 연결 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="196f7-104">Because these references appear in a command window, they do not link directly to the referenced content.</span></span>

<span data-ttu-id="196f7-105">Windows PowerShell®에 포함 된 cmdlet 도움말 항목에서 이러한 링크는 다른 cmdlet, 개념 콘텐츠 ("about_") 및 Windows PowerShell®와 관련이 없는 기타 문서 및 도움말 파일을 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="196f7-105">In the cmdlet Help topics that are included in Windows PowerShell®, these links reference other cmdlets, conceptual content ("about_"), and other documents and Help files that are not related to Windows PowerShell®.</span></span>

<span data-ttu-id="196f7-106">다음 XML에서는 관련 항목에 대 한 두 개의 참조를 포함 하는 RelatedLinks 노드를 추가 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="196f7-106">The following XML shows how to add a RelatedLinks node that contains two references to related topics.</span></span>

```xml
<maml:relatedLinks>
  <maml:navigationLink>
    <maml:linkText>Topic-name</maml:linkText>
  </maml:navigationLink>
  <maml:navigationLink>
    <maml:linkText>Topic-name</maml:linkText>
  </maml:navigationLink>
</ maml:relatedLinks >
```



