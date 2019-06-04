---
title: 입력된 형식 Cmdlet 도움말 항목을 추가 하는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 432798e4-5d69-46b1-9517-ff09bffaa4be
caps.latest.revision: 7
ms.openlocfilehash: f213605dda0132051d983f8608515325e815c455
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083436"
---
# <a name="how-to-add-input-types-to-a-cmdlet-help-topic"></a>Cmdlet 도움말 항목에 입력 형식을 추가하는 방법

이 섹션에서는 입력 섹션 Windows PowerShell® cmdlet 도움말 항목을 추가 하는 방법을 설명 합니다. 입력 섹션 값 또는 속성 이름으로 cmdlet은 파이프라인의 입력으로 허용 하는 개체의.NET 클래스를 보여 줍니다.

입력 섹션에 추가할 수 있는 클래스의 수 제한은 없습니다. 입력된 형식에 포함 된를 \<명령: inputTypes > 묶인 각 클래스를 사용 하 여 노드를 \<명령: inputType > 요소입니다.

두 개의 스키마 포함 \<maml:description > 각 \<명령: inputType > 요소입니다. 그러나 합니다 `Get-Help` cmdlet의 콘텐츠만 표시 합니다 \<명령: inputType > /\<maml:description >) 요소.

Windows PowerShell 3.0부터 합니다 `Get-Help` cmdlet의 콘텐츠를 표시 합니다 \<: uri > 요소입니다. 이 요소를 사용 하면.NET 클래스를 설명 하는 항목에는 사용자 수 있습니다.

에서는 다음 XML은 \<maml:inputTypes > 노드.

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

다음 XML 사용 하는 예제를 보여 줍니다.는 \<maml:inputTypes > 노드는 입력된 형식을 문서화 합니다.

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