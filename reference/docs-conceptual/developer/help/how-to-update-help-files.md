---
title: 도움말 파일을 업데이트하는 방법
ms.date: 09/12/2016
ms.openlocfilehash: 80f7c8865729515de98648765fa36ce540e00162
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86892951"
---
# <a name="how-to-update-help-files"></a>도움말 파일을 업데이트하는 방법

이 항목에서는 업데이트할 수 있는 도움말을 지 원하는 모듈에 대 한 도움말 파일을 업데이트 하는 방법을 설명 합니다.

## <a name="updating-help-files"></a>도움말 파일 업데이트

오류 수정, 개념을 명확 하 게 하기, 자주 묻는 질문에 대 한 답변, 새 파일 추가, 새 예제 추가 등의 여러 가지 이유로 도움말 파일을 업데이트할 수 있습니다.

도움말 파일을 업데이트 하려면:

1. 파일을 변경 합니다.
1. 다른 UI 문화권으로 파일을 변환 합니다.
1. 각 UI 문화권의 모듈에 대 한 모든 도움말 파일 (새로운, 변경 및 변경 되지 않음)을 수집 합니다.
1. XML 스키마에 대해 파일의 유효성을 검사 합니다.
1. 각 UI 문화권에 대 한 CAB 파일을 다시 빌드합니다.
1. HelpInfo XML 파일에서 각 UI 문화권에 대 한 CAB 파일의 버전 번호를 늘립니다.
1. HelpInfo XML 파일에서 **Helpcontenturi** 요소의 값으로 지정 된 위치에 새 CAB 파일을 업로드 합니다. 이전 CAB 파일을 새 CAB 파일로 바꿉니다.
1. 모듈 매니페스트에서 **HelpInfoUri** 키로 지정 된 위치에 업데이트 된 HelpInfo XML 파일을 업로드 합니다. 이전 HelpInfo XML 파일을 새 파일로 바꿉니다.
