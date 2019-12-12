---
title: Cmdlet 도움말 항목에 입력 유형을 추가 하는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 432798e4-5d69-46b1-9517-ff09bffaa4be
caps.latest.revision: 7
ms.openlocfilehash: f213605dda0132051d983f8608515325e815c455
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361242"
---
# <a name="how-to-add-input-types-to-a-cmdlet-help-topic"></a>Cmdlet 도움말 항목에 입력 형식을 추가하는 방법

이 섹션에서는 Windows PowerShell® cmdlet 도움말 항목에 입력 섹션을 추가 하는 방법에 대해 설명 합니다. 입력 섹션에는 cmdlet이 파이프라인에서 입력으로 허용 하는 개체의 .NET 클래스 (값 또는 속성 이름)가 나열 됩니다.

입력 섹션에 추가할 수 있는 클래스 수에는 제한이 없습니다. 입력 형식은 \<명령: inputTypes > 노드로 묶여 있으며 각 클래스는 \<명령: inputType > 요소에 포함 됩니다.

이 스키마에는 각 \<command: inputType > 요소에 두 개의 \<maml: description > 요소가 포함 되어 있습니다. 그러나 `Get-Help` cmdlet은 \<명령의 inputType >/\<maml: description >) 요소만 표시 합니다.

Windows PowerShell 3.0부터 `Get-Help` cmdlet은 \<maml: uri > 요소의 내용을 표시 합니다. 이 요소를 사용 하 여 .NET 클래스를 설명 하는 항목으로 사용자를 지시할 수 있습니다.

다음 XML은 \<maml: inputTypes > 노드를 보여 줍니다.

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

다음 XML은 \<maml: inputTypes > 노드를 사용 하 여 입력 유형을 문서화 하는 예를 보여 줍니다.

```xml
<command:inputTypes>
  <command:inputType>
    <dev:type>
      <maml:name> System.DateTime </maml:name>
      <maml:uri>  http://msdn.microsoft.com/library/system.datetime.aspx </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> You can pipe a date to the Set-Date cmdlet. <maml:para>
    <maml:description>
  </command:inputType>
</command:inputTypes>
```