---
title: PowerShell 스크립트 및 함수에 대 한 도움말 작성 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 859a6e22-75b1-43d4-ba62-62c107803b37
caps.latest.revision: 7
ms.openlocfilehash: 98a3f61ff4fa2367f69357173d4e8e14288ff429
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083113"
---
# <a name="writing-help-for-powershell-scripts-and-functions"></a>PowerShell 스크립트 및 함수에 대 한 도움말 작성

PowerShell 스크립트 및 함수 완벽 하 게 문서화 해야 때마다 다른 사용자와 공유 합니다.
합니다 `Get-Help` cmdlet 도움말 항목에서는 스크립트 및 함수 같은 형식으로 표시 하 고 모든 cmdlet에 대 한 도움말을 표시 하는 `Get-Help` 매개 변수는 함수 및 스크립트 도움말 항목에서 작동 합니다.

PowerShell 스크립트는 스크립트에서 스크립트에 대 한 도움말 항목 및 각 함수에 대 한 도움말 항목이 포함 됩니다.
스크립트와 독립적으로 공유 되는 함수 자체 도움말 항목을 포함할 수 있습니다.

이 문서에서는 형식 및 도움말 항목의 올바른 배치를 설명 하 고 콘텐츠에 대 한 지침 제안 합니다.

## <a name="types-of-script-and-function-help"></a>스크립트 및 함수 도움말 형식

### <a name="comment-based-help"></a>주석 기반 도움말
스크립트 또는 함수 내에서 주석의 집합으로 스크립트 또는 함수를 설명 하는 도움말 항목을 구현할 수 있습니다.
스크립트 및 함수에 대 한 설명 기반 도움말 스크립트에서를 작성할 때는 주석 기반 도움말을 배치에 대 한 규칙 주의 기울여야 합니다.
위치에 따라 결정 여부는 `Get-Help` cmdlet 스크립트 또는 함수를 사용 하 여 도움말 항목을 연결 합니다.
주석 기반 도움말 항목을 작성 하는 방법에 대 한 자세한 내용은 참조 하세요. [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)합니다.

### <a name="xml-based-command-help"></a>XML 기반 명령 도움말
명령 도움말 스키마를 사용 하는 XML 파일에 스크립트 또는 함수를 설명 하는 도움말 항목을 구현할 수 있습니다.
XML 파일을 사용 하 여 스크립트 또는 함수를 연결 하려면 사용는 `ExternalHelp` 키워드 뒤에 XML 파일의 이름과 경로 주석 처리 합니다.

경우는 `ExternalHelp` 키워드를 사용할 수 있는지 설명 기반 도움말을 통해 우선, 주석, 경우에 `Get-Help` 값과 일치 하는 도움말 파일을 찾을 수 없습니다는 `ExternalHelp` 키워드입니다.

### <a name="online-help"></a>온라인 도움말
인터넷에서 도움말 항목을 게시 하 고 다음 직접 `Get-Help` 항목을 열입니다.
주석 기반 도움말 항목을 작성 하는 방법에 대 한 자세한 내용은 참조 하세요. [온라인 도움말 지원](../module/supporting-online-help.md)합니다.

개념 ("정보") 스크립트 및 함수에 대 한 항목 작성에 대 한 설정 된 메서드가 없는 합니다.
그러나 명령 도움말 항목의 관련 링크 섹션에 인터넷 목록에 대 한 개념적인 항목 항목 및 해당 Url 게시할 수 있습니다.

## <a name="content-considerations-for-script-and-function-help"></a>스크립트 및 함수에 대 한 콘텐츠 고려 사항 도움말

- 사용 가능한 명령 도움말 섹션 중 일부를 사용 하 여 매우 간단한 도움말 항목을 작성 하는 경우에 명확한 설명은 스크립트 또는 함수 매개 변수를 포함 해야 합니다. 예제에서는 설명을 생략 하기로 한 경우에 예제 섹션에서 하나 또는 두 개의 샘플 명령을 포함 합니다.

- 모든 설명으로 스크립트 또는 함수의 명령 참조 합니다. 이 정보를 파악 하 고 명령을 관리 있습니다.

  예를 들어, 다음을 자세히 기술 한 새 항목 명령을 스크립트 임을 알려 줍니다. 이 실행할 때 전체 이름과 경로 지정 하는 데 필요한 사용자를 게 알립니다.

  > "새 항목 스크립트 입력된 파일에서 각 항목 이름에 대 한 빈 개념 항목을 만드는"

  다음 자세한 설명을 나타내는 `Disable-PSRemoting` 함수입니다. 이 정보는 세션 중 일부는 의해 숨겨질 수 명령 우선 순위가 높은, 동일한 이름 가진 여러 명령이 포함 된 경우 사용자에 게 특히 유용 합니다.

  > `Disable-PSRemoting` 함수 로컬 컴퓨터의 모든 세션 구성을 사용 하지 않도록 설정 하는 중...

- 스크립트 도움말 항목을 전체적으로 스크립트를 사용 하는 방법을 설명 합니다. 스크립트에서 함수에 대 한 도움말 항목을 한도 작성 하는 경우 스크립트 도움말 항목에 함수를 언급 하 고 스크립트 도움말 항목의 관련 링크 섹션에 함수 도움말 항목에 대 한 참조를 포함 합니다. 반대로, 함수를 스크립트의 일부 이면 설명 함수 도움말 항목의 함수에 스크립트를 어떻게 사용할 수 있습니다 하지 독립적으로 수행 하는 역할입니다. 다음 함수 도움말 항목의 관련 링크 섹션의 스크립트 도움말 항목을 나열 합니다.

- 스크립트 도움말 항목에 대 한 예제를 작성 하는 경우에 예제 명령에서 스크립트 파일의 경로를 포함 해야 합니다. 이러한 경로 지정 해야 명시적으로 스크립트는 현재 디렉터리의 경우에 사용자가 기억 합니다.

- 함수 도움말 항목에는 함수가 현재 세션에만 존재 하 고, 다른 세션에서 사용 하려면 PowerShell 프로필을 추가 하거나, 추가 사용자에 게 알림.

- `Get-Help` 스크립트 파일 및 도움말 항목 파일의 올바른 위치에 저장 되는 경우에 스크립트 또는 함수에 대 한 도움말 항목을 표시 합니다. 따라서 PowerShell을 설치 또는 저장 하거나 함수나 스크립트 도움말 항목의 스크립트 또는 함수를 설치 하기 위한 지침을 포함 하도록 유용 하지 않습니다. 대신 스크립트 또는 함수를 배포 하는 데 사용 하는 문서에는 설치 지침을 포함 합니다.

## <a name="see-also"></a>참고 항목

 [스크립트 및 함수에 대 한 XML 기반 도움말 항목을 작성합니다.](./writing-xml-based-help-topics-for-scripts-and-functions.md)

 [명령에 대 한 XML 기반 도움말 항목을 작성합니다.](./writing-xml-based-help-topics-for-commands.md)

 [쓰기 설명 기반 도움말 항목](./writing-comment-based-help-topics.md)
