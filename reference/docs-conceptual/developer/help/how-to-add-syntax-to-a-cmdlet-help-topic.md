---
title: Cmdlet 도움말 항목에 구문을 추가하는 방법
ms.date: 09/12/2016
ms.openlocfilehash: 3457341a577b283bf3da5dc010de9bbbb36b78d2
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893053"
---
# <a name="how-to-add-syntax-to-a-cmdlet-help-topic"></a>Cmdlet 도움말 항목에 구문을 추가하는 방법

Cmdlet 도움말 파일의 구문 다이어그램에 대 한 XML의 코딩을 시작 하기 전에이 섹션을 참조 하 여 매개 변수 특성 및 구문 다이어그램에 표시 되는 데이터와 같은 제공 해야 하는 데이터 종류를 명확 하 게 파악할 수 있습니다.

## <a name="parameter-attributes"></a>매개 변수 특성

- 필수
  - True 이면 매개 변수가 매개 변수 집합을 사용 하는 모든 명령에 표시 되어야 합니다.
  - False 이면 매개 변수 집합을 사용 하는 모든 명령에서 매개 변수가 선택 사항입니다.
- 위치
  - 명명 된 경우 매개 변수 이름이 필요 합니다.
  - 위치를 지정 하는 경우 매개 변수 이름은 선택 사항입니다. 생략 하는 경우 매개 변수 값은 명령의 지정 된 위치에 있어야 합니다. 예를 들어 값이 position = "1" 인 경우 매개 변수 값은 명령의 첫 번째 또는 유일한 명명 되지 않은 매개 변수 값 이어야 합니다.
- 파이프라인 입력
  - True (ByValue) 인 경우 입력을 매개 변수로 파이프 할 수 있습니다. 입력은 속성 이름과 개체 형식이 예상 형식과 일치 하지 않는 경우에도 매개 변수에 연결 됩니다 ("bound to").
    PowerShell 매개 변수 바인딩 구성 요소는 입력을 올바른 유형으로 변환 하려고 시도 하 고 유형을 변환할 수 없는 경우에만 명령이 실패 합니다. 매개 변수 집합에서 하나의 매개 변수만 값으로 연결할 수 있습니다.
  - True (ByPropertyName) 인 경우 입력을 매개 변수로 파이프 할 수 있습니다. 그러나 매개 변수 이름이 입력 개체의 속성 이름과 일치 하는 경우에만 입력이 매개 변수와 연결 됩니다. 예를 들어 매개 변수 이름이 인 경우 `Path` cmdlet으로 파이프 된 개체는 개체에 path 라는 속성을 가진 경우에만 해당 매개 변수와 연결 됩니다.
  - True (ByValue, Byvalue) 인 경우 속성 이름 또는 값을 기준으로 매개 변수에 입력을 파이프 할 수 있습니다. 매개 변수 집합에서 하나의 매개 변수만 값으로 연결할 수 있습니다.
  - False 이면이 매개 변수에 입력을 파이프 할 수 없습니다.
- 와일드 카드 사용
  - True 이면 사용자가 매개 변수 값을 입력 하는 텍스트에 와일드 카드 문자가 포함 될 수 있습니다.
  - False 이면 사용자가 매개 변수 값을 입력 하는 텍스트에 와일드 카드 문자를 포함할 수 없습니다.

### <a name="parameter-value-attributes"></a>매개 변수 값 특성

- 필수
  - True 이면 명령에 매개 변수를 사용할 때마다 지정 된 값을 사용 해야 합니다.
  - False 이면 매개 변수 값이 선택 사항입니다. 일반적으로 값은 매개 변수에 대 한 몇 가지 유효한 값 (예: 열거 형식) 중 하나인 경우에만 선택 사항입니다.

매개 변수 값의 **필수** 특성이 매개 변수의 **필수** 특성과 다릅니다.

매개 변수의 필수 특성은 cmdlet을 호출할 때 매개 변수 및 해당 값을 포함 해야 하는지 여부를 나타냅니다. 반면 매개 변수 값의 필수 특성은 매개 변수가 명령에 포함 된 경우에만 사용 됩니다. 특정 값을 매개 변수와 함께 사용 해야 하는지 여부를 나타냅니다.

일반적으로 자리 표시자 인 매개 변수 값은 필수 이며, 매개 변수 값은 매개 변수와 함께 사용 될 수 있는 여러 값 중 하나 이기 때문에 필요 하지 않습니다.

### <a name="gathering-syntax-information"></a>구문 정보 수집

1. Cmdlet 이름으로 시작 합니다.

   ```
   SYNTAX
       Get-Tech
   ```

1. Cmdlet의 모든 매개 변수를 나열 합니다. `-`각 매개 변수 이름 앞에 하이픈 () (ASCII 45)을 입력 합니다.
   매개 변수를 매개 변수 집합으로 구분 합니다. 일부 cmdlet에는 하나의 매개 변수 집합만 있을 수 있습니다. 이 예제에서 Get-help cmdlet은 두 개의 매개 변수 집합을 포함 합니다.

   ```
   SYNTAX
       Get-Tech -name -type
       Get-Tech -ID -list -type
   ```

   Cmdlet 이름을 사용 하 여 각 매개 변수 집합을 시작 합니다.

   기본 매개 변수 집합을 먼저 나열 합니다. 기본 매개 변수는 cmdlet 클래스에서 지정 합니다.

   먼저 표시 되어야 하는 위치 매개 변수가 없는 경우 각 매개 변수 집합에 대해 고유한 매개 변수를 먼저 나열 합니다. 이전 예에서 Name 및 ID 매개 변수는 두 매개 변수 집합에 대 한 고유한 매개 변수입니다. 각 매개 변수 집합은 해당 매개 변수 집합에 고유한 하나의 매개 변수를 포함 해야 합니다. 이렇게 하면 사용자가 매개 변수 집합에 제공 해야 하는 매개 변수를 더 쉽게 식별할 수 있습니다.

   명령에 표시 되어야 하는 순서로 매개 변수를 나열 합니다. 순서가 중요 하지 않은 경우 관련 매개 변수를 함께 나열 하거나 가장 자주 사용 되는 매개 변수를 먼저 나열 합니다.

   Cmdlet에서 ShouldProcess를 지 원하는 경우 WhatIf 및 Confirm 매개 변수를 나열 해야 합니다.

   구문 다이어그램에서 일반 매개 변수 (예: Verbose, Debug, ErrorAction)를 나열 하지 않습니다. `Get-Help`Cmdlet은 도움말 항목이 표시 될 때 해당 정보를 추가 합니다.

1. 매개 변수 값을 추가 합니다. PowerShell에서 매개 변수 값은 .NET 형식으로 표시 됩니다.
   그러나 System.string의 경우 형식 이름 (예: "string")을 약어로 사용할 수 있습니다.

   ```
   SYNTAX
       Get-Tech -name string -type basic advanced
       Get-Tech -ID int -list -type basic advanced
   ```

   System.string의 **문자열과 system.string** 의 경우 **int** **와 같이** 의미를 명확 하 게 하는 형식으로 **축약 합니다.**

   열거의 모든 값 (예: `-type` **기본** 또는 **고급**으로 설정 될 수 있는 이전 예제의 매개 변수)을 나열 합니다.

   이전 예제와 같은 스위치 매개 변수는 `-list` 값을 포함 하지 않습니다.

1. 리터럴인 매개 변수 값과 비교할 수 있는 매개 변수 값에 꺾쇠 괄호를 추가 합니다.

   ```
   SYNTAX
       Get-Tech -name <string> -type basic advanced
       Get-Tech -ID <int> -list -type basic advanced
   ```

1. 선택적 매개 변수 및 해당 기본값를 대괄호로 묶습니다.

   ```
   SYNTAX
       Get-Tech -name <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

1. 선택적 매개 변수 이름 (위치 매개 변수의 경우)을 대괄호로 묶습니다. 다음 예제의 Name 매개 변수와 같은 위치에 있는 매개 변수의 이름은 명령에 포함 될 필요가 없습니다.

   ```
   SYNTAX
       Get-Tech [-name] <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

1. Name 매개 변수의 이름 목록과 같이 매개 변수 값에 여러 값이 포함 될 수 있는 경우 매개 변수 값 바로 뒤에 대괄호 쌍을 추가 합니다.

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type basic advanced]
       Get-Tech -ID <int[]> [-list] [-type basic advanced]
   ```

1. 사용자가 매개 변수 또는 매개 변수 값 (예: 형식 매개 변수) 중에서 선택할 수 있는 경우 선택 항목을 중괄호로 묶고 단독 또는 기호 (;)로 구분 합니다.

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

1. 매개 변수 값이 따옴표 또는 괄호와 같은 특정 서식을 사용 해야 하는 경우 구문에 형식을 표시 합니다.

   ```
   SYNTAX
       Get-Tech [-name] <"string[]"> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

## <a name="coding-the-syntax-diagram-xml"></a>구문 다이어그램 XML 코딩

XML의 구문 노드는 tag로 끝나는 description 노드 바로 다음에 시작 됩니다 `</maml:description>` . 구문 다이어그램에 사용 된 데이터를 수집 하는 방법에 대 한 자세한 내용은 [구문 정보 수집](#gathering-syntax-information)을 참조 하세요.

### <a name="adding-a-syntax-node"></a>구문 노드 추가

Cmdlet 도움말 항목에 표시 된 구문 다이어그램은 XML의 구문 노드에 있는 데이터에서 생성 됩니다. 구문 노드는 tags 인 경우 쌍으로 묶입니다 `<command:syntax>` . Cmdlet의 각 매개 변수 집합을 태그 쌍으로 묶습니다 `<command:syntaxitem>` . 추가할 수 있는 태그 수에는 제한이 없습니다 `<command:syntaxitem>` .

다음 예에서는 두 개의 매개 변수 집합에 대 한 구문 항목 노드가 있는 구문 노드를 보여 줍니다.

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

### <a name="adding-the-cmdlet-name-to-the-parameter-set-data"></a>매개 변수 집합 데이터에 Cmdlet 이름 추가

Cmdlet의 각 매개 변수 집합은 구문 항목 노드에 지정 됩니다. 각 구문 항목 노드는 `<maml:name>` cmdlet의 이름을 포함 하는 태그 쌍으로 시작 합니다.

다음 예에서는 두 개의 매개 변수 집합에 대 한 구문 항목 노드가 있는 구문 노드를 포함 합니다.

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

구문 항목 노드에 추가 된 각 매개 변수는 태그 쌍 내에서 지정 됩니다 `<command:parameter>` . `<command:parameter>`PowerShell에서 제공 하는 일반 매개 변수를 제외 하 고 매개 변수 집합에 포함 된 각 매개 변수에 대 한 쌍의 태그를 사용 해야 합니다.

여는 태그의 특성은 `<command:parameter>` 매개 변수가 구문 다이어그램에 표시 되는 방식을 결정 합니다. 매개 변수 특성에 대 한 자세한 내용은 [매개 변수 특성](#parameter-attributes)을 참조 하세요.

> [!NOTE]
> `<command:parameter>`태그는 콘텐츠가 표시 되지 않는 자식 요소를 지원 `<maml:description>` 합니다. 매개 변수 설명은 XML의 parameter 노드에 지정 됩니다. 구문 항목 bodes와 매개 변수 노드의 정보가 일치 하지 않도록 하려면를 생략 `<maml:description>` 하거나 비워 둡니다.

다음 예제에는 두 개의 매개 변수를 사용 하는 매개 변수 집합에 대 한 구문 항목 노드가 포함 되어 있습니다.

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
