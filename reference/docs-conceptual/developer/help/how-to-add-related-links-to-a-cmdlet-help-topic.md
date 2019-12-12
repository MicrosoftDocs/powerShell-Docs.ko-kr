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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361222"
---
# <a name="how-to-add-related-links-to-a-cmdlet-help-topic"></a>Cmdlet 도움말 항목에 관련 링크를 추가하는 방법

이 섹션에서는 Windows PowerShell® cmdlet 도움말 항목과 관련 된 다른 콘텐츠에 대 한 참조를 추가 하는 방법에 대해 설명 합니다. 이러한 참조는 명령 창에 표시 되기 때문에 참조 된 콘텐츠에 직접 연결 되지 않습니다.

Windows PowerShell®에 포함 된 cmdlet 도움말 항목에서 이러한 링크는 다른 cmdlet, 개념 콘텐츠 ("about_"), Windows PowerShell®와 관련 되지 않은 기타 문서 및 도움말 파일을 참조 합니다.

다음 XML에서는 관련 항목에 대 한 두 개의 참조를 포함 하는 RelatedLinks 노드를 추가 하는 방법을 보여 줍니다.

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



