---
title: Cmdlet 도움말 항목에 관련 링크를 추가하는 방법
ms.date: 09/12/2016
ms.openlocfilehash: 7557b3856d8470434070dd286cd7e30c9ba015c5
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893376"
---
# <a name="how-to-add-related-links-to-a-cmdlet-help-topic"></a>Cmdlet 도움말 항목에 관련 링크를 추가하는 방법

이 섹션에서는 PowerShell cmdlet 도움말 항목과 관련 된 다른 콘텐츠에 대 한 참조를 추가 하는 방법에 대해 설명 합니다. 이러한 참조는 명령 창에 표시 되기 때문에 참조 된 콘텐츠에 직접 연결 되지 않습니다.

PowerShell에 포함 된 cmdlet 도움말 항목에서 이러한 링크는 다른 cmdlet, 개념 콘텐츠 ( `about_` ) 및 powershell과 관련이 없는 다른 문서 및 도움말 파일을 참조 합니다.

다음 XML에서는 관련 항목에 대 한 두 개의 참조를 포함 하는 **RelatedLinks** 노드를 추가 하는 방법을 보여 줍니다.

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
