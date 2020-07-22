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
ms.openlocfilehash: b5a5f3e187634b38ba3ce3da18a7ad64ccc09ce2
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893019"
---
# <a name="how-to-create-the-cmdlet-help-file"></a>Cmdlet 도움말 파일을 만드는 방법

이 섹션에서는 Windows PowerShell cmdlet 도움말 항목에 대 한 콘텐츠를 포함 하는 올바른 XML 파일을 만드는 방법을 설명 합니다. 이 섹션에서는 도움말 파일의 이름을로 하는 방법, 적절 한 XML 헤더를 추가 하는 방법 및 cmdlet 도움말 콘텐츠의 여러 섹션이 포함 될 노드를 추가 하는 방법에 대해 설명 합니다.

> [!NOTE]
> 도움말 파일의 전체 보기를 보려면 `dll-Help.xml` Windows PowerShell 설치 디렉터리에 있는 파일 중 하나를 엽니다. 예를 `Microsoft.PowerShell.Commands.Management.dll-Help.xml` 들어 파일에는 몇 가지 PowerShell cmdlet에 대 한 내용이 포함 되어 있습니다.

### <a name="how-to-create-a-cmdlet-help-file"></a>Cmdlet 도움말 파일을 만드는 방법

1. 텍스트 파일을 만들고 UTF8 인코딩을 사용 하 여 저장 합니다. 파일 이름에는 Windows PowerShell에서 cmdlet 도움말 파일로 검색할 수 있도록 다음과 같은 형식이 있어야 합니다.

   `<PSSnapInAssemblyName>.dll-Help.xml`

1. 텍스트 파일에 다음 XML 헤더를 추가 합니다. 이 파일은 MAML (Microsoft 지원 마크업 언어) 스키마에 대해 유효성을 검사 합니다. 현재 PowerShell에서는 파일의 유효성을 검사 하는 도구를 제공 하지 않습니다.

   `<?xml version="1.0" encoding="utf-8" ?> <helpItems xmlns="http://msh" schema="maml">`

1. 어셈블리의 각 cmdlet에 대 한 cmdlet 도움말 파일에 **명령** 노드를 추가 합니다. **명령** 노드 내의 각 노드는 cmdlet 도움말 항목의 다른 섹션과 관련이 있습니다.

   다음 표에는 각 노드에 대 한 XML 요소와 각 노드에 대 한 설명이 나와 있습니다.

   |           노드           |                                                                                                     설명                                                                                                     |
   | ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
   | `<details>`              | Cmdlet 도움말 항목의 NAME and 개요 섹션에 대 한 콘텐츠를 추가 합니다. 자세한 내용은 [Cmdlet 이름 및 개요를 추가 하는 방법](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)을 참조 하세요. |
   | `<maml:description>`     | Cmdlet 도움말 항목의 설명 섹션에 대 한 콘텐츠를 추가 합니다. 자세한 내용은 [Cmdlet 도움말 항목에 자세한 설명을 추가](./how-to-add-a-cmdlet-description.md)하는 방법을 참조 하십시오.                    |
   | `<command:syntax>`       | Cmdlet 도움말 항목의 구문 섹션에 대 한 내용을 추가 합니다. 자세한 내용은 [Cmdlet 도움말 항목에 구문을 추가 하는 방법](./how-to-add-syntax-to-a-cmdlet-help-topic.md)을 참조 하세요.                                  |
   | `<command:parameters>`   | Cmdlet 도움말 항목의 매개 변수 섹션에 대 한 콘텐츠를 추가 합니다. 자세한 내용은 [Cmdlet 도움말 항목에 매개 변수를 추가 하는 방법 항목](./how-to-add-parameter-information.md)을 참조 하세요.                                  |
   | `<command:inputTypes>`   | Cmdlet 도움말 항목의 입력 섹션에 대 한 콘텐츠를 추가 합니다. 자세한 내용은 [Cmdlet 도움말 항목에 입력 유형을 추가 하는 방법 항목](./how-to-add-input-types-to-a-cmdlet-help-topic.md)을 참조 하세요.                        |
   | `<command:returnValues>` | Cmdlet 도움말 항목의 출력 섹션에 대 한 콘텐츠를 추가 합니다. 자세한 내용은 [Cmdlet 도움말 항목에 반환 값을 추가 하는 방법](./how-to-add-return-values-to-a-cmdlet-help-topic.md)을 참조 하세요.                   |
   | `<maml:alertset>`        | Cmdlet 도움말 항목의 참고 항목 섹션에 대 한 내용을 추가 합니다. 자세한 내용은 [Cmdlet 도움말 항목에 메모를 추가 하는 방법 항목](./how-to-add-notes-to-a-cmdlet-help-topic.md)을 참조 하세요.                                      |
   | `<command:examples>`     | Cmdlet 도움말 항목의 예제 섹션에 대 한 콘텐츠를 추가 합니다. 자세한 내용은 [Cmdlet 도움말 항목에 예를 추가 하는 방법](./how-to-add-examples-to-a-cmdlet-help-topic.md)을 참조 하세요.                            |
   | `<maml:relatedLinks>`    | Cmdlet 도움말 항목의 관련 링크 섹션에 대 한 콘텐츠를 추가 합니다. 자세한 내용은 [Cmdlet 도움말 항목에 관련 링크를 추가 하는 방법](./how-to-add-related-links-to-a-cmdlet-help-topic.md)을 참조 하세요.             |

## <a name="example"></a>예제

 다음은 cmdlet 도움말 항목의 다양 한 섹션에 대 한 노드를 포함 하는 **명령** 노드의 예입니다.

```xml
<command:command
  xmlns:maml="https://schemas.microsoft.com/maml/2004/10"
  xmlns:command="https://schemas.microsoft.com/maml/dev/command/2004/10"
  xmlns:dev="https://schemas.microsoft.com/maml/dev/2004/10">
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

 [Cmdlet 도움말 항목에 자세한 설명을 추가 하는 방법](./how-to-add-a-cmdlet-description.md)

 [Cmdlet 도움말 항목에 구문을 추가하는 방법](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [Cmdlet 도움말 항목에 매개 변수를 추가 하는 방법](./how-to-add-parameter-information.md)

 [Cmdlet 도움말 항목에 입력 형식을 추가하는 방법](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [Cmdlet 도움말 항목에 반환 값을 추가하는 방법](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [Cmdlet 도움말 항목에 메모를 추가 하는 방법](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [Cmdlet 도움말 항목에 예제를 추가하는 방법](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [Cmdlet 도움말 항목에 관련 링크를 추가하는 방법](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [Windows PowerShell SDK](../windows-powershell-reference.md)
