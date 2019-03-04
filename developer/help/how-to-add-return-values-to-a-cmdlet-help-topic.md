---
title: Cmdlet 도움말 항목 값 반환을 추가 하는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a52ab737-753c-4d04-8af7-758d5c805e18
caps.latest.revision: 7
ms.openlocfilehash: b21811e5a5a819c3d5c4a55fcbe685a84819b71d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859439"
---
# <a name="how-to-add-return-values-to-a-cmdlet-help-topic"></a>Cmdlet 도움말 항목에 반환 값을 추가하는 방법

이 섹션에서는 출력 섹션 Windows PowerShell® cmdlet 도움말 항목을 추가 하는 방법을 설명 합니다. OUTPUTS 섹션 cmdlet을 반환 하거나 파이프라인으로 전달 하는 개체의.NET 클래스를 보여 줍니다.

출력 섹션에 추가할 수 있는 클래스의 수 제한은 없습니다. Cmdlet의 반환 형식에 포함 된를 \<명령: returnValues > 묶인 각 클래스를 사용 하 여 노드를 \<명령: returnValue > 요소입니다.

Cmdlet 출력을 생성 하지 않습니다, 경우 출력이 임을 나타내려면이 섹션에서는 사용 합니다. 예를 들어, 클래스 이름 대신 "None"을 작성 하 고 간략 한 설명을 제공 합니다. Cmdlet은 출력을 조건부로 생성 하는 경우 조건을 설명 하 고 조건부 출력 설명할이 노드를 사용 합니다.

두 개의 스키마 포함 \<maml:description > 각 \<명령: returnValue > 요소입니다. 그러나 합니다 `Get-Help` cmdlet의 콘텐츠만 표시 합니다 \<명령: returnValue > /\<maml:description > 요소.

Windows PowerShell 3.0부터 합니다 `Get-Help` cmdlet의 콘텐츠를 표시 합니다 \<: uri > 요소입니다. 이 요소를 사용 하면.NET 클래스를 설명 하는 항목에는 사용자 수 있습니다.

에서는 다음 XML은 \<maml:returnValues > 노드.

```xml
<command:returnValues>
  <command:returnValue>
    <dev:type>
      <maml:name> Class Name </maml:name>
      <maml:uri>  URI of a topic that describes the class </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
       <maml:para> Brief description <maml:para>

</maml:description>
  </command: returnValue>
</command: returnValues>
```

다음 XML 사용 하는 예제를 보여 줍니다.는 \<maml:returnValues > 노드를 문서 출력 형식입니다.

```xml
<command:returnValues>
  <command:returnValue>
    <dev:type>
      <maml:name> System.DateTime </maml:name>
      <maml:uri>  http://msdn.microsoft.com/library/system.datetime.aspx </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> Get-Date returns a DateTime object. <maml:para>
    </maml:description>
  </command: returnValue>
</command: returnValues>
```



