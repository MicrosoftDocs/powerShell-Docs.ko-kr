---
title: 업데이트 가능한 도움말을 테스트 하는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e064048-2b94-4365-bdb7-f1ee7c0a7fd7
caps.latest.revision: 6
ms.openlocfilehash: cecc6c26ccaece06462ddd74b53534137fcf3037
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082331"
---
# <a name="how-to-test-updatable-help"></a>업데이트 가능한 도움말을 테스트하는 방법

이 항목에서는 모듈의 업데이트할 수 있는 도움말을 테스트 하는 방법을 설명 합니다.

## <a name="using-verbose-to-detect-errors"></a>오류를 검색 하는 자세한 정보를 사용 하 여

HelpInfo XML 파일 및 모듈에 대 한 CAB 파일을 업로드 한 후 파일을 실행 하 여 테스트를 [Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) 명령에 **Verbose** 매개 변수입니다. 합니다 **Verbose** 매개 변수는 지시 `Update-Help` 읽기에서 해당 작업의 중요 한 단계를 보고 하는 **HelpInfoUri** 압축 푼된 CAB 파일의 파일 형식을 확인을 위해 모듈 매니페스트 키 및 언어별 모듈 디렉터리에 파일을 배치 합니다.

모든 세부 정보 표시 메시지를 해결 하는 경우 실행을 `Update-Help` 명령에 **디버그** 매개 변수입니다. 이 매개 변수는 업데이트할 수 있는 도움말 파일을 사용 하 여 나머지 문제를 감지 해야 합니다.