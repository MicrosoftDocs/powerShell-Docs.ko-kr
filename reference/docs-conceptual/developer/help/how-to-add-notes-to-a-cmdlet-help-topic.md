---
ms.date: 10/20/2020
ms.topic: reference
title: Cmdlet 도움말 항목에 메모를 추가하는 방법
description: Cmdlet 도움말 항목에 메모를 추가하는 방법
ms.openlocfilehash: 61363c26ab0172277d1332ed1e9de080d8da200c
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659558"
---
# <a name="how-to-add-notes-to-a-cmdlet-help-topic"></a>Cmdlet 도움말 항목에 메모를 추가하는 방법

이 섹션에서는 PowerShell cmdlet 도움말 항목에 **참고** 섹션을 추가하는 방법을 설명합니다. **참고** 섹션은 매개 변수에 대한 자세한 설명과 같이 다른 구조화된 섹션에 잘 맞지 않는 세부 정보를 설명하는 데 사용됩니다. 이 콘텐츠는 일부 고유하지만 중요한 특정 공급자에서 cmdlet이 작동하는 방법, cmdlet의 용도 또는 발생 가능한 오류 조건을 방지하는 방법에 대한 설명을 포함할 수 있습니다.

**참고** 섹션은 단일 `<maml:alertset>` 노드를 사용하여 정의됩니다. 참고 섹션에 추가할 수 있는 메모 수에는 제한이 없습니다. 각 메모에 대해 `<maml:alertset>` 노드에 `<maml:alert>` 태그 쌍을 추가합니다. 각 메모의 내용은 `<maml:para>` 태그 집합 내에 추가됩니다. 공백에는 빈 `<maml:para>` 태그를 사용합니다.

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
