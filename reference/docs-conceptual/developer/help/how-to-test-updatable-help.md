---
ms.date: 09/12/2016
ms.topic: reference
title: 업데이트 가능한 도움말을 테스트하는 방법
description: 업데이트 가능한 도움말을 테스트하는 방법
ms.openlocfilehash: 47873089bfa1b918ea9970915e829a22aa7254c5
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667626"
---
# <a name="how-to-test-updatable-help"></a>업데이트 가능한 도움말을 테스트하는 방법

이 항목에서는 모듈에 대해 업데이트할 수 있는 도움말을 테스트 하는 방법을 설명 합니다.

## <a name="using-verbose-to-detect-errors"></a>자세한 정보를 사용 하 여 오류 검색

모듈에 대 한 HelpInfo XML 파일 및 CAB 파일을 업로드 한 후 **Verbose** 매개 변수를 사용 하 여 [update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) 명령을 실행 하 여 파일을 테스트 합니다. **Verbose** 매개 변수는 `Update-Help` 모듈 매니페스트의 **HelpInfoUri** 키를 읽고, 압축을 푼 CAB 파일의 파일 형식에 대 한 유효성을 검사 하 고, 파일을 언어별 모듈 디렉터리에 배치 하는 작업의 중요 한 단계를 보고 하도록 지시 합니다.

모든 자세한 정보 메시지가 확인 되 면 `Update-Help` **Debug** 매개 변수를 사용 하 여 명령을 실행 합니다.
이 매개 변수는 업데이트할 수 있는 도움말 파일의 나머지 문제를 검색 합니다.
