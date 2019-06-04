---
title: 도움말 파일을 업데이트 하는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 495869a6-080e-4401-9ddc-16edd2f86857
caps.latest.revision: 6
ms.openlocfilehash: 2c1fbd70aab1f65f33ea206b7ab1e2bd3dfd8c7a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082316"
---
# <a name="how-to-update-help-files"></a>도움말 파일을 업데이트하는 방법

이 항목에서는 업데이트 가능한 도움말을 지 원하는 모듈에 대 한 도움말 파일을 업데이트 하는 방법에 설명 합니다.

## <a name="updating-help-files"></a>도움말 파일 업데이트

오류를 수정, 개념을 명확히, 자주 묻는 질문에 답하려면, 새 파일을 추가 또는 새롭고 더 나은 예제 추가 같은 도움말 파일을 업데이트 하는 방법은 여러 가지가 있습니다.

도움말 파일을 업데이트 합니다.

1. 파일을 변경 합니다.

2. 다른 UI 문화권으로 파일을 변환 합니다.

3. 각 UI 문화권의 모듈에 대 한 모든 도움말 파일 (새, 변경 및 변경 되지 않은)를 수집 합니다.

4. XML 스키마에 대해 파일의 유효성을 검사 합니다.

5. 각 UI 문화권에 대 한 CAB 파일을 다시 작성 합니다.

6. HelpInfo XML 파일에서 각 UI 문화권에 대 한 CAB 파일의 버전 번호를 하나씩 늘립니다.

7. 값으로 지정 된 위치에 새 CAB 파일을 업로드 합니다 **HelpContentUri** HelpInfo XML 파일의 요소입니다. 새 CAB 파일을 사용 하 여 오래 된 CAB 파일을 대체 합니다.

8. 지정 된 위치에 업데이트 된 HelpInfo XML 파일을 업로드 합니다 **HelpInfoUri** 모듈 매니페스트 키입니다. 새 파일을 사용 하 여 이전 HelpInfo XML 파일을 대체 합니다.