---
title: 매개 변수 정보를 추가하는 방법
ms.date: 09/12/2016
ms.openlocfilehash: 15d0194a1d5449c65977703faf245e449d75d176
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893393"
---
# <a name="how-to-add-parameter-information"></a>매개 변수 정보를 추가하는 방법

이 섹션에서는 cmdlet 도움말 항목의 **매개 변수** 섹션에 표시 되는 콘텐츠를 추가 하는 방법에 대해 설명 합니다. 도움말 항목의 **매개 변수** 섹션은 cmdlet의 각 매개 변수를 나열 하 고 각 매개 변수에 대 한 자세한 설명을 제공 합니다.

**매개 변수** 섹션의 내용은 도움말 항목의 **구문** 섹션 내용과 일치 해야 합니다. **구문** 및 **매개 변수** 노드에 유사한 XML 요소가 포함 되어 있는지 확인 하는 것은 도움말 작성자의 책임입니다.

> [!NOTE]
> 도움말 파일의 전체 보기를 보려면 `dll-Help.xml` PowerShell 설치 디렉터리에 있는 파일 중 하나를 엽니다. 예를 `Microsoft.PowerShell.Commands.Management.dll-Help.xml` 들어 파일에는 몇 가지 PowerShell cmdlet에 대 한 내용이 포함 되어 있습니다.

### <a name="to-add-parameters"></a>매개 변수를 추가 하려면

1. Cmdlet 도움말 파일을 열고 문서화할 cmdlet에 대 한 명령 노드를 찾습니다. 새 cmdlet을 추가 하는 경우에는 새 명령 노드를 만들어야 합니다. 도움말 파일에는 도움말 콘텐츠를 제공 하는 각 cmdlet에 대 한 명령 노드가 포함 됩니다. 빈 명령 노드의 예는 다음과 같습니다.

    ```xml
    <command:command>
    </command:command>
    ```

1. 명령 노드 내에서 아래와 같이 설명 노드를 찾아 매개 변수 노드를 추가 합니다.
   매개 변수 노드는 하나만 허용 되며 구문 노드 바로 뒤에와 야 합니다.

    ```xml
    <command:command>
      <command:details></command:details>
      <maml:description></maml:description>
      <command:syntax></command:syntax>
      <command:parameters>
      </command:Parameters>
    </command:command>
    ```

1. 매개 변수 노드 내에서 아래와 같이 cmdlet의 각 매개 변수에 대 한 **매개 변수** 노드를 추가 합니다.

   이 예에서는 **매개 변수** 노드가 세 개의 매개 변수에 추가 됩니다.

    ```xml
    <command:parameters>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
    </command:Parameters>
    ```

   이러한 매개 변수는 구문 노드에서 사용 되는 것과 동일한 XML 태그 이며 여기에 지정 된 매개 변수는 구문 노드에 지정 된 매개 변수와 일치 해야 하기 때문에 구문 노드에서 매개 변수 노드를 복사 하 여 Parameters 노드에 붙여 넣을 수 있습니다. 그러나 매개 변수가 구문의 여러 매개 변수 집합에 지정 된 경우에도 매개 변수 노드의 인스턴스를 하나만 복사 해야 합니다.

1. 각 매개 변수 노드에 대해 각 매개 변수의 특징을 정의 하는 특성 값을 설정 합니다. 이러한 특성에는 required, 와일드 카드 사용, pipelineinput 및 position이 포함 됩니다.

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
      </command:parameter>
      <command:parameter required="false" globbing="false"
               pipelineInput="false" position="named">
      </command:parameter>
      <command:parameter required="false" globbing="false"
               pipelineInput="false" position="named" ></command:parameter>
    </command:Parameters>
    ```

1. 각 매개 변수 노드에 대해 매개 변수의 이름을 추가 합니다. 매개 변수 노드에 추가 된 매개 변수 이름의 예는 다음과 같습니다.

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
      </command:parameter>
    </command:Parameters>
    ```

1. 각 **매개 변수** 노드에 대해 매개 변수에 대 한 설명을 추가 합니다. **매개 변수 노드에 추가** 된 매개 변수 설명의 예는 다음과 같습니다.

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
        <maml:description>
          <maml:para> Add parameter description... </maml:para>
        </maml:description>
      </command:parameter>
    </command:parameters>
    ```

1. 각 **매개 변수** 노드에 대해 .net 형식의 매개 변수를 추가 합니다. 매개 변수 형식은 매개 변수 이름과 함께 표시 됩니다.

   다음 **은 매개 변수 노드에 추가** 된 .net 형식의 매개 변수 예제입니다.

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
        <maml:description>
          <maml:para> Add parameter description... </maml:para>
        </maml:description>
        <dev:type> Add .NET Framework type... </dev:type>
      </command:parameter>
    </command:parameters>
    ```

1. 각 **매개 변수** 노드에 대해 매개 변수의 기본값을 추가 합니다. 내용이 표시 되 면 매개 변수 설명에 다음 문장이 추가 됩니다. **DefaultValue** 는 기본값입니다.

   매개 변수 기본값에 대 한 예제는 **매개 변수** 노드에 추가 됩니다.

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
        <maml:description>
          <maml:para> Add parameter description... </maml:para>
        </maml:description>
        <dev:type> Add .NET Framework type... </dev:type>
        <dev:defaultvalue> Add default value...</dev:defaultvalue>
      </command:parameter>
    </command:parameters>
    ```

1. 여러 값이 있는 각 매개 변수에 대해 가능한 값 노드를 추가 합니다.

   매개 변수에 대 한 두 가지 가능한 값을 정의 하는 가능한 값 노드의 예제는 다음과 같습니다.

    ```xml
    <dev:possiblevalues>
      <dev:possiblevalue>
        <dev:value>Unknown</dev:value>
        <maml:description>
          <maml:para></maml:para>
        </maml:description>
      </dev:possiblevalue>
      <dev:possiblevalue>
        <dev:value>String</dev:value>
        <maml:description>
          <maml:para></maml:para>
        </maml:description>
      </dev:possibleValue>
    </dev:possiblevalues>
    ```

매개 변수를 추가할 때 기억할 몇 가지 사항은 다음과 같습니다.

- 매개 변수의 특성은 cmdlet 도움말 항목의 모든 뷰에 표시 되지 않습니다. 그러나 사용자가 토픽의 **전체** ( `Get-Help <cmdletname> -full` ) 또는 **매개 변수** () 보기를 요청 하면 매개 변수 설명 다음에 테이블에 표시 됩니다 `Get-Help <cmdletname> -parameter` .

- 매개 변수 설명은 cmdlet 도움말 항목의 가장 중요 한 부분 중 하나입니다. 설명은 간결 하 고 철저 하 게 설명 해야 합니다. 또한 두 매개 변수가 서로 상호 작용 하는 경우와 같이 매개 변수 설명이 너무 길면 cmdlet 도움말 항목의 참고 섹션에서 더 많은 내용을 추가할 수 있습니다.

  매개 변수 설명은 두 가지 유형의 정보를 제공 합니다.

- 매개 변수를 사용 하는 경우 cmdlet이 수행 하는 작업입니다.

- 매개 변수에 대 한 올바른 값은 무엇 인가요?

- 매개 변수 값은 .NET 개체로 표시 되기 때문에 사용자에 게는 일반적인 명령줄 도움말에서와 동일한 값에 대 한 자세한 정보가 필요 합니다. 사용자에 게 매개 변수가 허용 하도록 디자인 된 데이터 형식을 알리고 예제를 포함 합니다.

매개 변수의 기본값은 명령줄에서 매개 변수를 지정 하지 않은 경우에 사용 되는 값입니다. 기본값은 선택 사항이 며, 필수 매개 변수와 같은 일부 매개 변수에는 필요 하지 않습니다. 그러나 대부분의 선택적 매개 변수에는 기본값을 지정 해야 합니다.

기본값을 사용 하면 사용자가 매개 변수를 사용 하지 않는 효과를 이해할 수 있습니다. 선택적인 경로에 대 한 "현재 디렉터리" 또는 "PowerShell 설치 디렉터리 ()"와 같이 특별히 구체적 값을 설명 합니다 `$PSHOME` . **Passthru** 매개 변수에 사용 되는 다음 문장과 같이 기본값을 설명 하는 문장을 작성할 수도 있습니다. "passthru를 지정 하지 않으면 cmdlet은 개체를 파이프라인으로 전달 하지 않습니다." 또한 값이 필드 이름 **기본값과**반대로 표시 되기 때문에 항목에 "Default value" 라는 용어를 포함할 필요가 없습니다.

매개 변수의 기본값은 cmdlet 도움말 항목의 모든 뷰에 표시 되지 않습니다. 그러나 사용자가 토픽의 **전체** ( `Get-Help <cmdletname> -full` ) 또는 **매개 변수** () 보기를 요청 하는 경우 매개 변수 설명에 따라 매개 변수 특성을 사용 하 여 테이블에 표시 됩니다 `Get-Help
<cmdletname> -parameter` .

다음 XML에서는 노드에 추가 된 태그 쌍을 보여 줍니다 `<dev:defaultValue>` `<command:parameter>` .
기본값은 닫는 `</command:parameterValue>` 태그 (매개 변수 값이 지정 된 경우) 또는 `</maml:description>` 매개 변수 설명의 닫는 태그 바로 다음에 옵니다. name.

```xml
<command:parameters>
  <command:parameter required="true" globbing="true"
           pipelineInput="false" position="named">
    <maml:name> Parameter name </maml:name>
    <maml:description>
      <maml:para> Parameter Description </maml:para>
    </maml:description>
    <command:parameterValue required="true">
      Value
    </command:parameterValue>
    <dev:defaultValue> Default parameter value </dev:defaultValue>
  </command:parameter>
</command:parameters>
```

열거 형식에 대 한 값 추가

매개 변수에 여러 값 또는 열거 형식의 값이 있는 경우 선택적 노드를 사용할 수 있습니다 \<dev:possibleValues> . 이 노드를 사용 하 여 여러 값의 이름과 설명을 지정할 수 있습니다.

열거 된 값에 대 한 설명은 cmdlet에 표시 되는 기본 도움말 뷰에 표시 되지 `Get-Help` 않지만 다른 도움말 뷰어는 해당 보기에서이 콘텐츠를 표시할 수 있습니다.

다음 XML에서는 `<dev:possibleValues>` 두 개의 값이 지정 된 노드를 보여 줍니다.

```xml
<command:parameters>
  <command:parameter required="true" globbing="true"
           pipelineInput="false" position="named">
    <maml:name> Parameter name </maml:name>
    <maml:description>
      <maml:para> Parameter Description </maml:para>
    </maml:description>
    <command:parameterValue required="true">
      Value
    </command:parameterValue>
    <dev:defaultValue> Default parameter value </dev:defaultValue>
    <dev:possibleValues>
      <dev:possibleValue>
        <dev:value> Value 1 </dev:value>
        <maml:description>
          <maml:para> Description 1 </maml:para>
        </maml:description>
      <dev:possibleValue>
      <dev:possibleValue>
        <dev:value> Value 2 </dev:value>
        <maml:description>
          <maml:para> Description 2 </maml:para>
        </maml:description>
      <dev:possibleValue>
    </dev:possibleValues>
  </command:parameter>
</command:parameters>
```
