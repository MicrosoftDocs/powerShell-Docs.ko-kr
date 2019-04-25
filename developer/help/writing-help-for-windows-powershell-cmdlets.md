---
title: PowerShell Cmdlet에 대 한 도움말을 작성 합니다. | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 55908d67-7cbe-482a-a105-5a6da93c5311
caps.latest.revision: 4
ms.openlocfilehash: 8d692cf88d1d356886ef973f0989294d6b51ee6d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083164"
---
# <a name="writing-help-for-powershell-cmdlets"></a>PowerShell Cmdlet에 대 한 도움말 작성

PowerShell cmdlet 유용할 수 있지만 도움말 항목에는 명확 하 게 cmdlet이 수행 하 고 사용 하는 방법을 설명, 하지 않으면 cmdlet은 사용 되지 않을 수 있습니다, 설상가상으로 사용자가 불편 해질 수 있습니다 것입니다.
XML 기반 cmdlet 도움말 파일 형식 일관성을 향상 시킵니다. 하지만 큰 도움이 더 필요 합니다.

Cmdlet 도움말을 작성 하지 한 경우 다음 지침을 검토 합니다.
Cmdlet 도움말 항목을 작성 하는 데 필요한 XML 스키마는 다음 섹션에 설명 되어 있습니다.
시작 [Cmdlet 도움말 파일을 만드는](./how-to-create-the-cmdlet-help-file.md)합니다.
해당 항목에는 최상위 XML 노드에 대 한 설명을 포함합니다.

## <a name="writing-guidelines-for-cmdlet-help"></a>Cmdlet 도움말에 대 한 작성 지침

### <a name="write-well"></a>잘 작성
아무 것도 잘 작성 된 항목을 바꿉니다.
전문 기록기에 없는 경우에 기록기 또는 편집기를 찾습니다.
Microsoft Word에 도움말 텍스트를 복사 하 여 문법을 사용 하는 다른 대안은 및 작업을 개선 하기 위해 맞춤법 검사 합니다.

### <a name="write-simply"></a>단순히 작성
간단한 단어 및 구를 사용 합니다.
용어를 방지 합니다.
여러 독자 여러분 장착 되어만 외국어 사전 및 도움말 항목을 고려 합니다.

### <a name="write-consistently"></a>일관 되 게 작성
도움말 관련된 cmdlet (예를 들어, get-x 및 x 집합) 유사 해야 합니다.
표준 매개 변수에 대 한 표준 설명을 사용할 **Force** 하 고 **InputObject**합니다.
(복사한 도움말에서 핵심 cmdlet에 대 한 합니다.) 표준 용어를 사용 합니다.
예: 사용 하 여 "매개 변수", 없습니다 "인수" 및 "cmdlet" 사용 되지 않습니다 "명령" 또는 "명령을 사용 합니다."

### <a name="start-the-synopsis-with-a-verb"></a>개요는 동사를 사용 하 여 시작
어떤 cmdlet이 수행, 없습니다 무엇 인지 또는 작동 방식 개요 필드를 사용자에 게 알립니다.
동사에는이 cmdlet은 해당 요구 사항을 충족 하는 경우 사용자에 게 알려 주는 작업 기반의 문을 만듭니다.
"Get", "만들기" 및 "변경"과 같은 간단한 동사 사용
"수정"와 같은 단어를 모호 하 고 멋진 일 수 있음 "설정"을 방지 합니다.

### <a name="focus-on-objects"></a>개체에 집중
대부분 "get" cmdlet 디스플레이 무엇 인가 이지만 해당 기본 함수 개체를 가져옵니다.
도움을 집중적으로 개체를 사용자가 이해할 기본 표시는 많은 중 고 메서드 및 다양 한 방식에 검색 된 개체의 속성을 사용할 수 있도록 합니다.

### <a name="write-detailed-descriptions"></a>자세한 설명을 기록합니다
간단히 cmdlet 자세한 설명에서는 할 수 있는 모든를 나열 합니다.
주 함수 하나의 속성을 변경 하는 cmdlet은 모든 속성을 변경할 수 있지만 경우 자세한 설명에이 나열 합니다.

### <a name="use-conventional-syntax"></a>기존 구문을 사용 하십시오.
Windows 및 UNIX 명령줄 도움말에 공통 되는 표준 Backus Naur 형식을 사용 합니다.

### <a name="use-microsoft-net-framework-types-for-parameter-values"></a>매개 변수 값에 대 한 Microsoft.NET Framework 형식을 사용합니다
매개 변수 값 (구문 및 매개 변수 설명)에 대 한 자리 표시자 매개 변수 허용 하는 개체의.NET Framework 형식을 보여 줍니다.
PowerShell 팀에는.NET Framework에 대 한 사용자를 교육 하는 데이 규칙 개발 했습니다.

### <a name="write-complete-parameter-descriptions"></a>전체 매개 변수 설명 작성
매개 변수 설명의 두 가지 사용자에 게 알려야 합니다: 어떤 매개 변수 (미치는) 않으며 매개 변수 값에 대 한 입력 해야 새로운 합니다.

### <a name="write-practical-examples"></a>실제 예제를 작성 합니다.
예에는 모든 매개 변수를 사용 하는 방법을 보여 줍니다 해야 하지만 가장 중요 한 점은 실제 작업에서 cmdlet을 사용 하는 방법을 보여 주는 합니다.
간단한 예제로 시작 하 고 점점 더 복잡 한 예제를 작성 합니다.
마지막 예제에서는 파이프라인에서 cmdlet을 사용 하는 방법을 보여 줍니다.

### <a name="use-the-notes-field"></a>참고 필드를 사용 합니다.
참고 필드를 사용 하 여 사용자가 cmdlet을 이해 해야 하는 개념을 설명 합니다.
또한 일반 오류를 방지 하는 사용자가 정보를 사용할 수 있습니다.
변경 될 때 해당 Url을 방지 합니다.
대신, 검색할 사용자 사용 약관을 제공 합니다.

### <a name="test-your-help"></a>테스트 프로그램 도움말
코드를 테스트 하는 것 처럼 도움말을 테스트 합니다.
친구 있고 동료 도움말 콘텐츠를 읽기 및 피드백을 제공 합니다.
또한 뉴스 그룹에서 피드백을 받을 수 있습니다.

## <a name="see-also"></a>참고 항목

 [Cmdlet 도움말 파일을 만드는 방법](./how-to-create-the-cmdlet-help-file.md)

 [Cmdlet 이름 및 개요 Cmdlet 도움말 항목을 추가 하는 방법](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [자세한 설명은 Cmdlet 도움말 항목을 추가 하는 방법](./how-to-add-a-cmdlet-description.md)

 [구문 Cmdlet 도움말 항목을 추가 하는 방법](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [Cmdlet 도움말 항목 매개 변수를 추가 하는 방법](./how-to-add-parameter-information.md)

 [입력 형식 Cmdlet 도움말 항목을 추가 하는 방법](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [Cmdlet 도움말 항목에 반환 값을 추가 하는 방법](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [Cmdlet 도움말 항목을 추가 하는 방법 정보](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [예제 Cmdlet 도움말 항목을 추가 하는 방법](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [관련된 링크 Cmdlet 도움말 항목을 추가 하는 방법](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [Windows PowerShell SDK](../windows-powershell-reference.md)