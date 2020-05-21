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
ms.openlocfilehash: 0a6403e2dea16d73e2fdcb8cf5df39b2aa5b5dae
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83560273"
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
