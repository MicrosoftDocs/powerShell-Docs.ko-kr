---
title: Cmdlet 도움말 파일을 만드는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4a88dd89-6beb-494f-9e2a-6b10baed1a8d
caps.latest.revision: 17
ms.openlocfilehash: 08e05939f8aee42f2cd502a3da7a528d8460dec1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858979"
---
# <a name="how-to-create-the-cmdlet-help-file"></a>Cmdlet 도움말 파일을 만드는 방법

이 섹션에는 Windows PowerShell cmdlet 도움말 항목에 대 한 콘텐츠를 포함 하는 유효한 XML 파일을 만드는 방법을 설명 합니다. 이 섹션에는 도움말 파일 이름 지정 방법, 적절 한 XML 헤더를 추가 하는 방법 및 다양 한 cmdlet 도움말 콘텐츠 섹션을 포함 하는 노드를 추가 하는 방법을 설명 합니다.

> [!NOTE]
> 에 대 한 도움말 파일의 열린 Windows PowerShell 설치 디렉터리에 있는 dll Help.xml 파일 중 하나는 전체 보기입니다. 예를 들어 Microsoft.PowerShell.Commands.Management.dll Help.xml 파일 다양 한 Windows PowerShell cmdlet에 대 한 콘텐츠를 포함합니다.

### <a name="how-to-create-a-cmdlet-help-file"></a>Cmdlet 도움말 파일을 만드는 방법

1. 텍스트 파일을 만들고 UTF8 인코딩을 사용 하 여 저장 합니다. Windows PowerShell cmdlet 도움말 파일을 검색할 수 있도록 파일 이름 형식은 있어야 합니다.

   `<PSSnapInAssemblyName>.dll-Help.xml`

2. 텍스트 파일에 다음 XML 헤더를 추가 합니다. 다중 에이전트 모델링 언어 (MAML) 스키마에 대해 파일을 검사할 알아야 합니다. 현재 Windows PowerShell은 파일의 유효성을 검사 하려면 도구를 제공 하지 않습니다.

   `<?xml version="1.0" encoding="utf-8" ?> <helpItems xmlns="http://msh" schema="maml">`

3. 어셈블리의 각 cmdlet에 대 한 cmdlet 도움말 파일을 명령 노드를 추가 합니다. 명령 노드에 내의 각 노드는 cmdlet 도움말 항목의 다른 섹션 관련이 있습니다.

   다음 표에서 각 노드의 설명 뒤에 각 노드에 대 한 XML 요소를 나열 합니다.

   |노드|설명|
   |----------|-----------------|
   |`<details>`|Cmdlet 도움말 항목의 이름 및 개요 섹션에 대 한 콘텐츠를 추가합니다. 자세한 내용은 [개요와 Cmdlet 이름을 추가 하는 방법을](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)합니다.|
   |`<maml:description>`|Cmdlet 도움말 항목의 설명 섹션에 대 한 콘텐츠를 추가합니다. 자세한 내용은 [자세히 기술 한 Cmdlet 도움말 항목을 추가 하는 방법을](./how-to-add-a-cmdlet-description.md)합니다.|
   |`<command:syntax>`|Cmdlet 도움말 항목의 구문 섹션에 대 한 콘텐츠를 추가합니다. 자세한 내용은 [구문 Cmdlet 도움말 항목을 추가 하는 방법을](./how-to-add-syntax-to-a-cmdlet-help-topic.md)합니다.|
   |`<command:parameters>`|Cmdlet 도움말 항목의 매개 변수 섹션에 대 한 콘텐츠를 추가합니다. 자세한 내용은 [추가 매개 변수는 Cmdlet 도움말 항목을 방법](./how-to-add-parameter-information.md)합니다.|
   |`<command:inputTypes>`|Cmdlet 도움말 항목을 입력 부분에 대 한 콘텐츠를 추가합니다. 자세한 내용은 [Cmdlet 도움말 항목을 입력 유형을 추가 하는 방법](./how-to-add-input-types-to-a-cmdlet-help-topic.md)합니다.|
   |`<command:returnValues>`|Cmdlet 도움말 항목의 출력 섹션에 대 한 콘텐츠를 추가합니다. 자세한 내용은 [반환 값 추가 Cmdlet 도움말 항목을 하는 방법](./how-to-add-return-values-to-a-cmdlet-help-topic.md)합니다.|
   |`<maml:alertset>`|Cmdlet 도움말 항목의 NOTES 섹션에 콘텐츠를 추가합니다. 자세한 내용은 [추가 하는 방법에는 Cmdlet 도움말 항목에 정보](./how-to-add-notes-to-a-cmdlet-help-topic.md)합니다.|
   |`<command:examples>`|Cmdlet 도움말 항목의 예 섹션에 대 한 콘텐츠를 추가합니다. 자세한 내용은 [예제 Cmdlet 도움말 항목을 추가 하는 방법을](./how-to-add-examples-to-a-cmdlet-help-topic.md)합니다.|
   |`<maml:relatedLinks>`|Cmdlet 도움말 항목의 관련 링크 섹션에 대 한 콘텐츠를 추가합니다. 자세한 내용은 [관련 링크 추가 Cmdlet 도움말 항목을 방법](./how-to-add-related-links-to-a-cmdlet-help-topic.md)합니다.|

## <a name="example"></a>예제

 Cmdlet 도움말 항목의 여러 섹션에 대 한 노드를 포함 하는 명령 노드의 예는 다음과 같습니다.

```xml
<command:command
  xmlns:maml="http://schemas.microsoft.com/maml/2004/10"
  xmlns:command="http://schemas.microsoft.com/maml/dev/command/2004/10"
  xmlns:dev="http://schemas.microsoft.com/maml/dev/2004/10">
  <command:details>
    <!--Add name an synopsis here-->
  </command:details>
  <maml:description>
    <!--Add detailed description here-->
  </maml:description>
  <command:syntax>
    <!--Add syntax information here-->
  </command:syntax>
  <command:parameters>
    <!--Add parameter information here-->
  </command:parameters>
  <command:inputTypes>
    <!--Add input type information here-->
  </command:inputTypes>
  <command:returnValues>
    <!--Add return value information here-->
  </command:returnValues>
  <maml:alertSet>
    <!--Add Note information here-->
  </maml:alertSet>
  <command:examples>
    <!--Add cmdlet examples here-->
  </command:examples>
  <maml:relatedLinks>
    <!--Add links to related content here-->
  </maml:relatedLinks>
</command:command>
```

## <a name="see-also"></a>참고 항목

 [Cmdlet 이름 및 개요를 추가 하는 방법](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [자세한 설명은 Cmdlet 도움말 항목을 추가 하는 방법](./how-to-add-a-cmdlet-description.md)

 [구문 Cmdlet 도움말 항목을 추가 하는 방법](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [Cmdlet 도움말 항목 매개 변수를 추가 하는 방법](./how-to-add-parameter-information.md)

 [입력된 형식 Cmdlet 도움말 항목을 추가 하는 방법](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [Cmdlet 도움말 항목에 반환 값을 추가 하는 방법](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [추가 하는 방법에는 Cmdlet 도움말 항목을 참고 사항](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [예제 Cmdlet 도움말 항목을 추가 하는 방법](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [관련된 링크 Cmdlet 도움말 항목을 추가 하는 방법](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [Windows PowerShell SDK](../windows-powershell-reference.md)