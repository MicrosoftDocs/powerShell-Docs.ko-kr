---
title: 구문 Cmdlet 도움말 항목을 추가 하는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d0c6d03f-1c1a-43d8-928e-e3290e90e0bc
caps.latest.revision: 5
ms.openlocfilehash: 947d0c0188df5bba3a9fb617fe5abf0b3b28eb51
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857999"
---
# <a name="how-to-add-syntax-to-a-cmdlet-help-topic"></a>Cmdlet 도움말 항목에 구문을 추가하는 방법

- [매개 변수 특성](#Parameter-Attributes)

- [매개 변수 값 특성](#Parameter-Value-Attributes)

- [구문 정보 수집](#Gathering-Syntax-Information)

- [XML 구문 다이어그램은 코딩](#Coding-the-Syntax-Diagram-XML)

## <a name="things-to-know-about-the-syntax-diagram-in-cmdlet-help"></a>Cmdlet 도움말의 구문 다이어그램에 대해 알아야 할 내용

Cmdlet 도움말 파일의 구문 다이어그램에 대 한 XML 코드를 시작 하기 전에 명확히 제공 하는 데 필요한 데이터의 매개 변수 특성 및 해당 데이터를 구문 다이어그램에 표시 되는 방식을 같은 종류의이 섹션을 읽고...

### <a name="parameter-attributes"></a>매개 변수 특성

- 필수

  - True 이면 매개 변수는 매개 변수 집합을 사용 하는 모든 명령에 나타나야 합니다.

  - False 이면 매개 변수 집합을 사용 하는 모든 명령에서 선택적입니다.

- 위치

  - 이름이 인 경우 매개 변수 이름이 필요 합니다.

  - 위치 하는 경우 매개 변수 이름은 선택 사항입니다. 생략 하는 경우 매개 변수 값을 명령에 지정된 된 위치에 있어야 합니다. 값이 위치 = "1", 예를 들어, 매개 변수 값은 첫 번째 이거나 이어야만 명명 되지 않은 명령에 매개 변수 값입니다.

- 파이프라인 입력

  - True 이면 (ByValue) 입력 매개 변수에 파이프할 수 있습니다. 연결 된 입력 ("에 바인딩")를 사용 하 여 속성 이름 및 개체 형식이 예상된 형식과 일치 하지 않는 경우에 매개 변수입니다. Windows PowerShell? 매개 변수 바인딩 구성 요소를 올바른 형식에 대 한 입력을 변환 하 고 형식을 변환할 수 없는 경우에 명령 실패 하려고 합니다. 매개 변수 집합에 하나의 매개 변수 값으로 연결 될 수 있습니다.

  - True (ByPropertyName) 입력 매개 변수에 파이프할 수 있습니다. 그러나 매개 변수 이름 입력된 개체의 속성 이름과 일치 하는 경우에 입력 매개 변수 연관 됩니다. 예를 들어 매개 변수 이름은 `Path`, 개체 경로 라는 속성이 있는 경우에 cmdlet에 파이프 하는 개체는 해당 매개 변수를 사용 하 여 연결 합니다.

  - 경우 true (ByValue, ByPropertyName) 속성 이름 또는 값으로 입력 매개 변수에 파이프할 수 있습니다. 매개 변수 집합에 하나의 매개 변수 값으로 연결 될 수 있습니다.

  - False 이면이 매개 변수의 입력을 파이프할 수 없습니다.

- 와일드 카드 사용

  - True 이면 사용자가 입력 한 매개 변수 값에 대 한 텍스트는 와일드 카드 문자를 포함할 수 있습니다.

  - False 인 경우 사용자가 입력 한 매개 변수 값에 대 한 텍스트는 와일드 카드 문자를 포함할 수 없습니다.

### <a name="parameter-value-attributes"></a>매개 변수 값 특성

- 필수

  - True 이면 명령에서 매개 변수를 사용 하 여 때마다 지정 된 값을 사용 해야 합니다.

  - False 이면 매개 변수 값은 선택 사항입니다. 일반적으로 경우에 매개 변수의 경우 몇 가지 유효한 값 중 하나 같은 열거 형식에는 값은 선택 사항입니다.

매개 변수 값의 필수 특성에 필요한 매개 변수 특성이 다릅니다.

매개 변수의 필수 특성 해야 하는지 여부를 매개 변수 (및 해당 값) 포함 된 cmdlet을 호출 하는 경우를 나타냅니다. 반면, 매개 변수 값에 필요한 특성이 매개 변수는 명령에 포함 하는 경우에 사용 됩니다. 매개 변수를 사용 하 여 해당 특정 값을 사용 해야 하는지 여부를 나타냅니다.

일반적으로 자리 표시자는 매개 변수 값이 필요 하 고 매개 변수를 사용 하 여 사용할 수 있는 몇 가지 값 중 하나 이기 때문에 매개 변수 값은 리터럴 필요 않습니다.

### <a name="gathering-syntax-information"></a>구문 정보 수집

1. Cmdlet 이름으로 시작 합니다.

   ```
   SYNTAX
       Get-Tech
   ```

2. Cmdlet의 모든 매개 변수를 나열 합니다. (라고도 "대시" 또는 "앞에 빼기 기호" (ASCII 45) 각 매개 변수 이름 대시를 입력 합니다. 매개 변수 (일부 cmdlet 설정 매개 변수는 하나만 있을 수 있습니다) 매개 변수 집합으로 구분 합니다. 이 예제에서는 Get-기술 cmdlet에는 두 매개 변수 집합이 있습니다.

   ```
   SYNTAX
       Get-Tech -name -type
       Get-Tech -ID -list -type
   ```

   Cmdlet 이름으로 설정 하는 각 매개 변수를 시작 합니다.

   먼저 설정 기본 매개 변수를 나열 합니다. 기본 매개 변수는 cmdlet 클래스에 의해 지정 됩니다.

   각 매개 변수 집합에 대 한 첫 번째 표시 되어야 하는 위치 매개 변수 없는 고유한 매개 변수를 먼저 나열 합니다. 이 예에서 이름 및 ID 매개 변수는 두 매개 변수 집합에 대 한 고유한 매개 변수 (매개 변수 집합이 각 매개 변수 하나가 있어야 해당 매개 변수 집합에 고유한). 이 매개 변수에 대해 제공 하는 데 필요한 어떤 매개 변수 집합을 식별 하는 사용자에 대해 쉽게 있습니다.

   명령에 표시 된 순서 대로 매개 변수를 나열 합니다. 순서는 중요 하지 않습니다, 경우 관련된 매개 변수를 함께 나열 하거나 먼저 가장 자주 사용 되는 매개 변수를 나열 합니다.

   Cmdlet은 ShouldProcess를 지 원하는 경우 WhatIf 및 Confirm 매개 변수를 나열 해야 합니다.

   구문 다이어그램에서 (예: Verbose, Debug, ErrorAction) 공통 매개 변수를 나열 하지 않습니다. `Get-Help` cmdlet 도움말 항목을 표시 하는 경우 해당 정보를 추가 합니다.

3. 매개 변수 값을 추가 합니다. Windows PowerShell에?를 매개 변수 값은.NET 형식으로 표시 됩니다. 그러나 형식 이름 "문자열" System.String에 대해 같은 축약할 수 있습니다.

   ```
   SYNTAX
       Get-Tech -name string -type basic advanced
       Get-Tech -ID int -list -type basic advanced
   ```

   매개 변수의 의미는 분명 System.Int32에 대 한 "int" System.String "문자열" 등으로 형식 약어입니다.

   열거형의 모든 값을 같은 목록 앞의 예제에서-형식 매개 변수 본 "basic" 또는 "고급"로 설정할 수 있습니다.

   스위치 매개 변수-앞의 예제에서 목록 등, 하는 값입니다.

4. 자리 표시자를 리터럴 매개 변수 값을 비교 하 여 매개 변수 값에 꺾쇠 괄호를 추가 합니다.

   ```
   SYNTAX
       Get-Tech -name <string> -type basic advanced
       Get-Tech -ID <int> -list -type basic advanced
   ```

5. 선택적 매개 변수 및 해당 값을 대괄호로 묶습니다.

   ```
   SYNTAX
       Get-Tech -name <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

6. (위치 매개 변수)에 대 한 선택적 매개 변수 이름을 대괄호로 묶습니다. 다음 예제에서는 이름 매개 변수 같은 위치는 매개 변수에 대 한 이름을 명령에 포함 될 필요가 없습니다.

   ```
   SYNTAX
       Get-Tech [-name] <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

7. 매개 변수 값을 Name 매개 변수 이름 목록 같은 여러 값을 포함할 수 있는 경우 바로 다음 매개 변수 값을 대괄호 쌍을 추가 합니다.

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type basic advanced]
       Get-Tech -ID <int[]> [-list] [-type basic advanced]
   ```

8. 매개 변수 또는 매개 변수 값에서 선택할 수 있으며, 경우 형식 매개 변수를 같은 선택 중괄호로 묶고 배타적 OR symbol(;)를 구별 합니다.

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

9. 매개 변수 값을 따옴표 또는 괄호와 같은 특정 서식에 사용 해야 하는 경우 구문에서 형식을 보여 줍니다.

   ```
   SYNTAX
       Get-Tech [-name] <"string[]"> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

## <a name="coding-the-syntax-diagram-xml"></a>XML 구문 다이어그램은 코딩

XML 구문 노드의 끝나는 설명 노드를 후 즉시 시작 되는 \</maml:description > 태그입니다. 구문 다이어그램에 사용 된 데이터를 수집 하는 방법에 대 한 내용은 [구문 정보 수집](#Gathering-Syntax-Information)합니다.

### <a name="adding-a-syntax-node"></a>구문 노드 추가

Cmdlet 도움말 항목에 표시 된 구문 다이어그램은 구문 노드의 XML 데이터에서 생성 됩니다. 구문 노드가 경우 쌍에 포함 되어 \<명령: 구문 > 태그입니다. 한 쌍의 묶인 cmdlet의 각 매개 변수 집합을 사용 하 여 \<명령: syntaxitem > 태그입니다. 수에 대 한 제한은 없습니다 \<명령: syntaxitem > 태그를 추가할 수 있습니다.

다음 예제에서는 구문 노드를 두 매개 변수 집합에 대 한 구문 항목 노드를 보여 줍니다.

```xml
<command:syntax>
  <command:syntaxItem>
    ...
    <!--Parameter Set 1 (default parameter set) parameters go here-->
    ...
  </command:syntaxItem>
  <command:syntaxItem>
    ...
    <!--Parameter Set 2 parameters go here-->
    ...
  </command:syntaxItem>
</command:syntax>
```

### <a name="adding-the-cmdlet-name-to-the-parameter-set-data"></a>Cmdlet 이름 집합에 추가 매개 변수 데이터

각 매개 변수 집합 cmdlet의 구문 항목 노드가 지정 됩니다. 각 구문 항목 노드가 한 쌍의 시작 \<maml:name > cmdlet의 이름을 포함 하는 태그입니다.

다음 예제에서는 구문 노드 두 매개 변수 집합에 대 한 구문 항목 노드를 포함 합니다.

```xml
<command:syntax>
  <command:syntaxItem>
    <maml:name>Cmdlet-Name</maml:name>
  </command:syntaxItem>
  <command:syntaxItem>
    <maml:name>Cmdlet-Name</maml:name>
  </command:syntaxItem>
</command:syntax>
```

### <a name="adding-parameters"></a>매개 변수 추가

쌍 내에서 구문 항목 노드를 추가 하는 각 매개 변수를 지정 하는 \<명령: 매개 변수 > 태그입니다. 한 쌍의 필요한 \<명령: 매개 변수 > Windows PowerShell에서 제공 하는 일반 매개 변수를 제외 하 고 매개 변수 집합에 포함 된 각 매개 변수에 대 한 태그.

열기의 특성 \<명령: 매개 변수 > 태그는 매개 변수 구문 다이어그램에 표시 되는 방식을 결정 합니다. 매개 변수 특성에 대 한 자세한 내용은 [매개 변수 특성](#Parameter-Attributes)합니다.

> [!NOTE]
> 합니다 \<명령: 매개 변수 > 태그가 자식 요소를 지원 합니다. \<maml:description > 내용이 표시 되지 않습니다. 매개 변수 설명은 XML의 매개 변수 노드에 지정 됩니다. 구문 항목의 정보 간 불일치를 방지 하려면 했 노드와 매개 변수를 생략 합니다 (\<maml:description > 하거나 비워 두세요.

다음 예제에서는 두 개의 매개 변수를 사용 하 여 설정 매개 변수에 대해 구문이 항목 노드를 포함 합니다.

```xml
<command:syntaxItem>
  <maml:name>Cmdlet-Name</maml:name>
  <command:parameter required="true" globbing="true"
    pipelineInput="true (ByValue)" position="1">
    <maml:name>ParameterName1</maml:name>
    <command:parameterValue required="true">
      string[]
    </command:parameterValue>
  </command:parameter>
  <command:parameter required="true" globbing="true"
    pipelineInput="true (ByPropertyName)">
    <maml:name>ParameterName2</maml:name>
    <command:parameterValue required="true">
      int32[]
    </command:parameterValue>
  </command:parameter>
</command:syntaxItem>
```
