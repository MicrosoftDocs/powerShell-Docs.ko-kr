---
title: Cmdlet 도움말 항목에 입력 형식을 추가하는 방법
ms.date: 09/12/2016
ms.openlocfilehash: d41c49ff48cf361c2ba694d11576e84a9367eef5
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893427"
---
# <a name="how-to-add-input-types-to-a-cmdlet-help-topic"></a>Cmdlet 도움말 항목에 입력 형식을 추가하는 방법

이 섹션에서는 PowerShell cmdlet 도움말 항목에 **입력** 섹션을 추가 하는 방법에 대해 설명 합니다. **입력** 섹션에는 cmdlet이 파이프라인에서 입력으로 허용 하는 개체의 .net 클래스 (값 또는 속성 이름)가 나열 됩니다.

**입력** 섹션에 추가할 수 있는 클래스 수에는 제한이 없습니다. 입력 형식은 `<command:inputTypes>` 각 클래스가 요소로 묶여 있는 노드에 포함 됩니다 `<command:inputType>` .

이 스키마는 `<maml:description>` 각 요소에 두 개의 요소를 포함 `<command:inputType>` 합니다.
그러나이 `Get-Help` cmdlet은 요소의 콘텐츠만 표시 합니다 `<command:inputType>/<maml:description>` .

PowerShell 3.0부터 `Get-Help` cmdlet은 요소의 내용을 표시 합니다 `<maml:uri>` .
이 요소를 사용 하 여 .NET 클래스를 설명 하는 항목으로 사용자를 지시할 수 있습니다.

다음 XML에서는 노드를 보여 줍니다 `<maml:inputTypes>` .

```xml
<command:inputTypes>
  <command:inputType>
    <dev:type>
      <maml:name> Class name </maml:name>
      <maml:uri>  URI of a topic that describes the class </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> Brief description </maml:para>
    </maml:description>
  </command:inputType>
</command:inputTypes>
```

다음 XML에서는 노드를 사용 하 여 입력 유형을 문서화 하는 예를 보여 줍니다 `<maml:inputTypes>` .

```xml
<command:inputTypes>
  <command:inputType>
    <dev:type>
      <maml:name> System.DateTime </maml:name>
      <maml:uri>  https://msdn.microsoft.com/library/system.datetime.aspx </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> You can pipe a date to the Set-Date cmdlet. <maml:para>
    <maml:description>
  </command:inputType>
</command:inputTypes>
```
