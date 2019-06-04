---
title: 매개 변수 정보를 추가 하는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cf6c1442-60aa-477a-8f30-ab02b1b11039
caps.latest.revision: 7
ms.openlocfilehash: d4a5fc934a41b00f89862674e44e4540680674f7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083368"
---
# <a name="how-to-add-parameter-information"></a>매개 변수 정보를 추가하는 방법

이 섹션에는 cmdlet 도움말 항목의 매개 변수 섹션에 표시 되는 콘텐츠를 추가 하는 방법을 설명 합니다. 도움말 항목의 매개 변수 섹션에서는 각 cmdlet의 매개 변수를 나열 하 고 각 매개 변수에 대 한 자세한 설명을 제공 합니다.

매개 변수 섹션의 콘텐츠는 도움말 항목의 구문 섹션의 내용과 일치 해야 합니다. 것 도움말 작성자의 구문 및 매개 변수를 모두 노드 유사한 XML 요소를 포함 하 고 있는지 확인 해야 합니다.

> [!NOTE]
> 에 대 한 도움말 파일의 열린 Windows PowerShell 설치 디렉터리에 있는 dll Help.xml 파일 중 하나는 전체 보기입니다. 예를 들어 Microsoft.PowerShell.Commands.Management.dll Help.xml 파일 다양 한 Windows PowerShell cmdlet에 대 한 콘텐츠를 포함합니다.

### <a name="to-add-parameters"></a>매개 변수를 추가 하려면

1. Cmdlet 도움말 파일을 열고 문서화 하는 cmdlet에 대 한 명령 노드를 찾습니다. 새 cmdlet을 추가 하는 경우에 새 명령 노드를 만드는 해야 합니다. 도움말 파일에 대 한 도움말 콘텐츠를 제공 하는 각 cmdlet에 대 한 명령 노드에 포함 됩니다. 빈 명령 노드의 예는 다음과 같습니다.

    ```xml
    <command:command>
    </command:command>
    ```

2. 명령 노드 내에서 설명 노드 찾아 아래와 같이 매개 변수 노드를 추가 합니다. 매개 변수 노드는 하나만 허용 되 고 구문 노드 바로 다음에 나와야 합니다.

    ```xml
    <command:command>
      <command:details></command:details>
      <maml:description></maml:description>
      <command:syntax></command:syntax>
      <command:parameters>
      </command:Parameters>
    </command:command>
    ```

3. 매개 변수 노드 내에서 아래와 같이 cmdlet의 각 매개 변수에 대해 매개 변수 노드를 추가 합니다.

   이 예제에서는 세 가지 매개 변수에 대 한 매개 변수 노드에 추가 됩니다.

    ```xml
    <command:parameters>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
    </command:Parameters>
    ```

   여기에 지정 된 매개 변수 때문에 구문 노드가 지정 된 매개 변수와 일치 해야 및 구문 노드에서 사용 되는 동일한 XML 태그를 이기 때문에 매개 변수 노드 구문 노드에서 복사한 매개 변수 노드에 붙여넣을 수 있습니다. 그러나 하나의 인스턴스만 매개 변수 노드를 복사 해야, 여러 매개 변수 구문에서 설정 되는 매개 변수를 지정 하는 경우에 합니다.

4. 각 매개 변수에 대 한 노드를 각 매개 변수의 특성을 정의 하는 특성 값을 설정 합니다. 이러한 특성에는 다음이 포함 됩니다: 와일드 카드 사용, pipelineinput, 및 위치 해야 합니다.

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

5. 각 매개 변수 노드, 매개 변수 이름을 추가 합니다. 매개 변수 노드 추가 매개 변수 이름의 예는 다음과 같습니다.

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
      </command:parameter>
    </command:Parameters>
    ```

6. 각 매개 변수 노드는 매개 변수의 설명을 추가 합니다. 매개 변수 노드 추가 매개 변수 설명의 예는 다음과 같습니다.

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

7. 각 매개 변수 노드에 대 한.NET Framework 형식의 매개 변수를 추가 합니다. 매개 변수 형식 매개 변수 이름과 함께 표시 됩니다.

   매개 변수 노드 추가 매개 변수.NET Framework 형식의 예는 다음과 같습니다.

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

8. 각 매개 변수 노드에 대 한 매개 변수의 기본값을 추가 합니다. 내용을 표시 하는 경우 다음 문장은 매개 변수 설명에 추가 됩니다. "DefaultValue" 기본값입니다.

   매개 변수 기본값의 예가 매개 변수 노드를 추가할 다음과 같습니다.

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

9. 여러 값이 있는 각 매개 변수에 가능한 값 노드를 추가 합니다.

   예로 두 가지 가능한 매개 변수 값을 정의 하는 가능한 값 노드

    ```xml
    <dev:possiblevalues>
      <dev:possiblevalue>
        <dev:value>Unknown</dev:value>
        <maml:description>
          <maml:para></maml:para>
        </maml:description>
      /dev:possiblevalue>
      <dev:possiblevalue>
        <dev:value>String</dev:value>
        <maml:description>
          <maml:para></maml:para>
        </maml:description>
      </dev:possibleValue>
    </dev:possiblevalues>
    ```

매개 변수를 추가할 때 기억해 야 할 몇 가지 사항은 다음과 같습니다.

- 매개 변수의 특성 cmdlet 도움말 항목의 모든 보기에서 표시 되지 않습니다. 그러나 매개 변수 설명 전체에 대 한 사용자 요청 하는 경우 다음 표에 표시 됩니다 (Get-help \<cmdletname >-전체) 또는 매개 변수 (Get-help \<cmdletname >-매개 변수) 항목의 보기입니다.

- 매개 변수 설명에는 cmdlet 도움말 항목의 가장 중요 한 부분 중 하나입니다. 간단 하면서도 뿐만 아니라 철저 한에 대 한 설명 이어야 합니다. 또한 매개 변수 설명 등 두 개의 매개 변수가 서로 상호 작용 하는 경우 너무 오래 되 면 추가할 수 있습니다 콘텐츠 더 보기 cmdlet 도움말 항목의 NOTES 섹션에서 기억 합니다.

  매개 변수 설명을 두 가지 유형의 정보를 제공합니다.

- 새로운 cmdlet이 수행 하는 매개 변수를 사용 하는 경우.

- 유효한 값은 매개 변수입니다.

- 매개 변수 값을.net 개체로 표현 되는 때문에 사용자는 기존의 명령줄 도움말에서 것 보다 이러한 값에 대 한 자세한 내용은 해야 합니다. 어떤 유형의 데이터를 허용 하도록 매개 변수를 사용자에 게 알림 및 예제가 포함 되어 있습니다.

매개 변수의 기본값은 명령줄에서 매개 변수를 지정 하지 않으면 사용 되는 값입니다. Note 기본값 선택 사항이 며 필요한 매개 변수와 같은 일부 매개 변수에 대해 필요 하지 않습니다. 그러나 대부분의 선택적 매개 변수 기본값을 지정 해야 합니다.

기본값 매개 변수를 사용 하지의 효과 이해 하려면 사용자 하는 데 도움이 됩니다. 기본값을 "현재 디렉터리" 또는 "Windows PowerShell 설치 디렉터리 ($pshome)"를 선택적 경로 같은 매우 특별 하 게 설명 합니다. 에 사용 되는 다음 문장 같은 기본값을 설명 하는 문장 작성할 수도 있습니다는 `PassThru` 매개 변수: "PassThru 지정 하지 않으면 cmdlet은 전달 하지 않습니다 개체를 파이프라인."  또한 반대 되는 필드 이름 값이 표시 되기 때문에 "**기본값**", 항목의 "기본값" 용어를 포함 해야 합니다.

매개 변수의 기본값 cmdlet 도움말 항목의 모든 보기에서 표시 되지 않습니다. 그러나 전체에 대 한 사용자 요청 매개 변수 설명에 다음 매개 변수 특성) (함께 표에 표시 됩니다 (Get-help \<cmdletname >-전체) 또는 매개 변수 (Get-help \<cmdletname >-매개 변수) 보기 항목입니다.

다음 XML의 쌍을 보여 줍니다 `<dev:defaultValue>` 에 추가 된 태그는 `<command:parameter>` 노드. 기본값 바로 뒤에 오는 닫는 통지 `</command:parameterValue>` (매개 변수 값을 지정 하는) 경우에 태그 또는 닫는 `</maml:description>` 매개 변수 설명의 태그입니다. 이름입니다.

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

열거형된 형식에 대 한 값을 추가 합니다.

매개 변수의 여러 값 또는 열거형 형식의 값이를 사용할 수는 선택적 \<dev:possibleValues > 노드. 이 노드를 사용 하면 이름 및 설명을 여러 값을 지정할 수 있습니다.

열거형된 값의 설명에 표시 되지 않습니다 기본값 중 하나에서 표시 하는 도움말 보기에 유의 합니다 `Get-Help` cmdlet, 하지만 다른 도움말 뷰어는 보기에서이 콘텐츠 표시 될 수 있습니다.

에서는 다음 XML `<dev:possibleValues>` 지정 된 두 값을 사용 하 여 노드.

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