---
ms.date: 09/13/2016
ms.topic: reference
title: PowerShell cmdlet에 대한 도움말 작성
description: PowerShell cmdlet에 대한 도움말 작성
ms.openlocfilehash: b1deaa5998dbc54add93764db785d57afcc0a779
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92658109"
---
# <a name="writing-help-for-powershell-cmdlets"></a>PowerShell cmdlet에 대한 도움말 작성

PowerShell cmdlet은 유용할 수 있지만, 도움말 항목에서 cmdlet이 수행 하는 작업 및 사용 방법에 대해 명확 하 게 설명 하지 않는 한, cmdlet을 사용 하지 못할 수도 있습니다. 그렇지 않으면 사용자가 불편 수 있습니다. XML 기반 cmdlet 도움말 파일 형식을 사용 하면 일관성을 향상 시킬 수 있지만 매우 많은 도움이 됩니다.

Cmdlet 도움말을 작성 한 적이 없는 경우에는 다음 지침을 검토 하세요. 다음 섹션에서는 cmdlet 도움말 항목을 작성 하는 데 필요한 XML 스키마에 대해 설명 합니다. [Cmdlet 도움말 파일을 만드는](./how-to-create-the-cmdlet-help-file.md)것으로 시작 합니다. 이 항목에는 최상위 XML 노드에 대 한 설명이 포함 되어 있습니다.

## <a name="writing-guidelines-for-cmdlet-help"></a>Cmdlet 도움말 작성 지침

### <a name="write-well"></a>쓰기 웰

잘 작성 된 항목은 아무 것도 대체 되지 않습니다. 전문 작성자가 아닌 경우 도움이 되는 작성기 또는 편집기를 찾으십시오. 다른 대안은 도움말 텍스트를 Microsoft Word로 복사 하 고 문법 및 맞춤법 검사를 사용 하 여 작업을 개선 하는 것입니다.

### <a name="write-simply"></a>쓰기 간단히

간단한 단어와 구를 사용 합니다. 전문 용어를 사용하지 않습니다. 대부분의 판독기는 외국어 사전과 도움말 항목에만 포함 되어 있다고 가정 합니다.

### <a name="write-consistently"></a>일관 되 게 쓰기

관련 cmdlet에 대 한 도움말은 유사 해야 합니다 (예: get x 및 set-x). **Force** 및 **InputObject** 와 같은 표준 매개 변수에 대 한 표준 설명을 사용 합니다. 핵심 cmdlet에 대 한 도움말에서 복사 합니다. 표준 용어를 사용 합니다. 예를 들어 "argument"가 아닌 "parameter"를 사용 하 고 "command" 또는 "command-let"이 아닌 "cmdlet"을 사용 합니다.

### <a name="start-the-synopsis-with-a-verb"></a>동사를 사용 하 여 개요 시작

개요 필드는 cmdlet이 수행 하는 작업 또는 작동 방식을 사용자에 게 알립니다. 동사는이 cmdlet이 요구 사항을 충족 하는 경우 사용자에 게 알리는 작업 기반 문을 만듭니다. "Get", "create" 및 "change"와 같은 간단한 동사를 사용 합니다. "설정"을 사용 하지 마세요 .이는 모호 하 고 "수정"과 같은 유용한 단어 일 수 있습니다.

### <a name="focus-on-objects"></a>개체에 포커스 설정

대부분의 "get" cmdlet은 무언가를 표시 하지만 기본 함수는 개체를 가져오는 것입니다. 사용자가 기본 표시 중 하나를 다른 방식으로 검색 한 개체의 메서드 및 속성을 사용할 수 있도록 도움말에서 개체에 대해 중점적으로 설명 합니다.

### <a name="write-detailed-descriptions"></a>자세한 설명 작성

자세한 설명에서 cmdlet이 수행할 수 있는 모든 항목을 간략하게 나열 합니다. Main 함수가 속성 하나를 변경 하는 것 이지만 cmdlet이 모든 속성을 변경할 수 있는 경우 자세한 설명에이 목록을 표시 합니다.

### <a name="use-conventional-syntax"></a>기본 구문 사용

Windows 및 UNIX 명령줄 도움말에 일반적으로 사용 되는 표준 Backus-Naur 형식을 사용 합니다.

### <a name="use-microsoft-net-types-for-parameter-values"></a>매개 변수 값에 Microsoft .NET 형식 사용

매개 변수 값에 대 한 자리 표시자 (구문 및 매개 변수 설명)에는 매개 변수가 허용 하는 개체의 .NET Framework 형식이 표시 됩니다. PowerShell 팀은 사용자에 게 .NET Framework에 대해 학습 하는 데 도움이 되는이 규칙을 개발 했습니다.

### <a name="write-complete-parameter-descriptions"></a>전체 매개 변수 설명을 작성 합니다.

매개 변수 설명은 매개 변수의 용도, 매개 변수 값에 입력 해야 하는 항목에 대 한 두 가지 사항을 사용자에 게 알려 주어 야 합니다.

### <a name="write-practical-examples"></a>실제 사례 작성

이 예에서는 모든 매개 변수를 사용 하는 방법을 보여 주지만, 가장 중요 한 점은 실제 작업에서 cmdlet을 사용 하는 방법을 보여 주는 것입니다. 간단한 예제를 시작 하 고 점점 더 복잡 한 예제를 작성 합니다. 마지막 예제에서는 파이프라인에서 cmdlet을 사용 하는 방법을 보여 줍니다.

### <a name="use-the-notes-field"></a>참고 필드 사용

참고 필드를 사용 하 여 사용자가 cmdlet을 이해 하는 데 필요한 개념을 설명 합니다. 또한 사용자가 일반적인 오류를 방지 하는 데 도움이 되는 정보를 사용할 수 있습니다. Url이 변경 되 면 사용 하지 마십시오. 대신 검색할 사용자 용어를 제공 합니다.

### <a name="test-your-help"></a>도움말 테스트

코드를 테스트 하는 것과 같은 방법으로 도움말을 테스트 합니다. 친구와 동료가 도움말 콘텐츠를 읽고 피드백을 제공 하도록 합니다. 뉴스 그룹에서 피드백을 요청할 수도 있습니다.

## <a name="see-also"></a>참고 항목

 [Cmdlet 도움말 파일을 만드는 방법](./how-to-create-the-cmdlet-help-file.md)

 [Cmdlet 도움말 항목에 Cmdlet 이름 및 개요를 추가하는 방법](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [Cmdlet 도움말 항목에 자세한 설명을 추가 하는 방법](./how-to-add-a-cmdlet-description.md)

 [Cmdlet 도움말 항목에 구문을 추가하는 방법](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [Cmdlet 도움말 항목에 매개 변수를 추가 하는 방법](./how-to-add-parameter-information.md)

 [Cmdlet 도움말 항목에 입력 유형을 추가 하는 방법](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [Cmdlet 도움말 항목에 반환 값을 추가하는 방법](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [Cmdlet 도움말 항목에 메모를 추가하는 방법](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [Cmdlet 도움말 항목에 예제를 추가하는 방법](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [Cmdlet 도움말 항목에 관련 링크를 추가하는 방법](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [Windows PowerShell SDK](../windows-powershell-reference.md)
