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
ms.openlocfilehash: 1a365a167c245006bb882a542aedb5c43cfc4c96
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83557110"
---
# <a name="how-to-add-notes-to-a-cmdlet-help-topic"></a>Cmdlet 도움말 항목에 메모를 추가하는 방법

이 섹션에서는 Windows PowerShell® cmdlet 도움말 항목에 메모 섹션을 추가 하는 방법에 대해 설명 합니다. 참고 섹션은 매개 변수에 대 한 자세한 설명과 같이 다른 구조화 된 섹션에 쉽게 맞지 않는 세부 정보를 설명 하는 데 사용 됩니다. 이 콘텐츠에는 cmdlet이 특정 공급자와 작동 하는 방식, 몇 가지 고유 하 고 중요 한 cmdlet의 용도 또는 가능한 오류 조건을 방지 하는 방법에 대 한 설명을 포함할 수 있습니다.

참고 섹션에 추가할 수 있는 메모 수에는 제한이 없습니다. 각 메모에 대해 \< maml: alert> 태그 쌍을 \< maml: alertset> 노드에 추가 합니다. 각 메모의 내용은 \< maml: 단락> 태그 집합 내에 추가 됩니다. 공백 \< 에는 빈 maml: 단락> 태그를 사용 합니다.

다음 XML은 \< 두 개의 메모가 있는 maml: alertset> 노드를 보여 줍니다. 각 메모에는 선택적 \< maml: title> 태그가 있으며 (제목은 maml: alert> 태그 집합을 그룹화 하는 데 사용할 수 있음 \< ) 각 메모에는 공백에 대 한 콘텐츠 다음에 빈 줄이 있습니다.

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
