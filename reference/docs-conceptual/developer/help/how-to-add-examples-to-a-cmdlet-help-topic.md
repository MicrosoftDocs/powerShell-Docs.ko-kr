---
title: Cmdlet 도움말 항목에 예를 추가 하는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8f723b21-8f95-4981-8b6e-4f07c22d601a
caps.latest.revision: 5
ms.openlocfilehash: b6f8aef76a5f4b5dc1a60425541856ead9a9c77a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368112"
---
# <a name="how-to-add-examples-to-a-cmdlet-help-topic"></a>Cmdlet 도움말 항목에 예제를 추가하는 방법

## <a name="things-to-know-about-examples-in-cmdlet-help"></a>Cmdlet 도움말의 예제에 대해 알아야 할 사항

- 매개 변수 이름이 선택적인 경우에도 명령의 모든 매개 변수 이름을 나열 합니다. 이렇게 하면 사용자가 명령을 쉽게 해석할 수 있습니다.

- Windows PowerShell®에서 작동 하는 경우에도 별칭 및 부분 매개 변수 이름을 사용 하지 마십시오.

- 예제 설명에서 명령의 생성에 대 한 유리수를 설명 합니다. 특정 매개 변수 및 값을 선택한 이유와 변수를 사용 하는 방법을 설명 합니다.

- 명령에서 식을 사용 하는 경우이를 자세히 설명 합니다.

- 명령에서 개체의 속성 및 메서드를 사용 하는 경우, 특히 기본 표시에 표시 되지 않는 속성을 사용 하는 경우 사용자에 게 개체에 대 한 지시를 제공 하는 기회로 예제를 사용 합니다.

## <a name="help-views-that-display-examples"></a>예제를 표시 하는 도움말 보기

예제는 cmdlet 도움말의 상세 및 전체 뷰에만 표시 됩니다.

## <a name="adding-an-examples-node"></a>예제 노드 추가

다음 XML에서는 단일 예제 노드가 포함 된 예제 노드를 추가 하는 방법을 보여 줍니다. 항목에 포함 하려는 각 예제에 대 한 추가 예제 노드를 추가 합니다.

```xml
<command:examples>
  <command:example>
  </command:example>
</command:examples>
```

## <a name="adding-an-example-title"></a>예제 제목 추가

다음 XML은 예제의 제목을 추가 하는 방법을 보여 줍니다. 제목은 다른 예제와는 별도로 예제를 설정 하는 데 사용 됩니다. Windows PowerShell®는 일련의 예제 번호를 포함 하는 표준 헤더를 사용 합니다.

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
  </command:example>
</command:examples>
```

## <a name="adding-preceding-characters"></a>선행 문자 추가

다음 XML은 예 명령 바로 앞에 표시 되는 Windows PowerShell 프롬프트와 같은 문자를 추가 하는 방법을 보여 줍니다 (중간 공간 제외). Windows PowerShell®는 Windows PowerShell 프롬프트: C:\PS >를 사용 합니다.

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

## <a name="adding-the-command"></a>명령 추가

다음 XML은 예제의 실제 명령을 추가 하는 방법을 보여 줍니다. 명령을 추가할 때 cmdlet 및 매개 변수의 전체 이름 (별칭 사용 안 함)을 입력 합니다. 또한 가능한 경우 소문자를 사용 합니다.

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

## <a name="adding-a-description"></a>설명 추가

다음 XML은 예제에 대 한 설명을 추가 하는 방법을 보여 줍니다. 여러 @no__t 1maml: 단락 > 태그를 사용할 수 있는 경우에도 Windows PowerShell®는 설명에 대해 단일 \<maml: 단락 > 태그 집합을 사용 합니다.

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

## <a name="adding-example-output"></a>예제 출력 추가

다음 XML에서는 명령의 출력을 추가 하는 방법을 보여 줍니다. 명령 결과 정보는 선택 사항 이지만 경우에 따라 특정 매개 변수를 사용 하는 경우의 영향을 보여 주는 데 도움이 됩니다. Windows PowerShell®는 두 개의 빈 \<maml: 단락 > 태그 집합을 사용 하 여 명령의 출력을 구분 합니다.

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