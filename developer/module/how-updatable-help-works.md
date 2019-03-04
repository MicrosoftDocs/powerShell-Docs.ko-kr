---
title: 어떻게 업데이트할 수 있는 도움말 Works | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7674636e-a0f2-4587-bfc5-dd3e6ce5489e
caps.latest.revision: 6
ms.openlocfilehash: 8874cc18416937c4d3cb30d801f2714410304c8c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860879"
---
# <a name="how-updatable-help-works"></a>업데이트 가능한 도움말 작동 방법

이 항목에서는 업데이트할 수 있는 도움말 프로세스 HelpInfo XML 파일 및 CAB 파일을 각 모듈에 대 한 설치에서 사용자에 대 한 도움말을 업데이트 하는 방법을 설명 합니다.

## <a name="the-update-help-process"></a>Update-help 프로세스

다음 목록에는 설명의 동작을 [Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet 모듈의 특정 UI 문화권에 대 한 도움말 파일을 업데이트 하는 명령을 실행 하는 경우.
다음 목록에는 설명의 동작을 [Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet 모듈의 특정 UI 문화권에 대 한 도움말 파일을 업데이트 하는 명령을 실행 하는 경우.

1. `Update-Help` 값으로 지정 된 위치에서 원격 HelpInfo XML 파일을 가져옵니다 합니다 **HelpInfoURI** 모듈 매니페스트에서 키를 스키마에 대해 파일의 유효성을 검사 합니다. (스키마를 보려면 [HelpInfo XML 스키마](./helpinfo-xml-schema.md).) 그런 다음 `Update-Help` 사용자의 컴퓨터에서 모듈 디렉터리에 있는 모듈에 대 한 로컬 HelpInfo XML 파일을 찾습니다.

2. `Update-Help` 모듈에 대 한 원격 및 로컬 HelpInfo XML 파일에 지정된 된 UI 문화권에 대 한 도움말 파일의 버전 번호를 비교합니다. 원격 파일에 버전 번호를 로컬 파일에 버전 번호 보다 큰 경우 또는 있는지 모듈에 대 한 로컬 HelpInfo XML 파일이 없는 경우 `Update-Help` 새 도움말 파일을 다운로드 하도록 준비 합니다.

3. `Update-Help` 지정 된 위치에서 모듈에 대 한 CAB 파일을 선택 합니다 **HelpContentUri** 원격 HelpInfo XML 파일의 요소입니다. 모듈 이름, GUID, 모듈 및 UI 문화권 사용 하 여 CAB 파일을 식별 합니다.

4. `Update-Help` CAB 파일 다운로드,이 압축을 푼, 도움말 콘텐츠 파일의 유효성을 검사 및 도움말 콘텐츠 파일에에서 저장 모듈 디렉터리의 언어별 하위 디렉터리 사용자의 컴퓨터

5. `Update-Help` 원격 HelpInfo XML 파일을 복사 하 여 로컬 HelpInfo XML 파일을 만듭니다. 로컬 HelpInfo XML 파일을 편집 하는 요소를 설치 하는 CAB 파일에 대해서만 포함 되도록 합니다. 그런 다음 모듈 디렉터리에 로컬 HelpInfo XML 파일을 저장 하 고 업데이트를 완료 합니다.

## <a name="the-save-help-process"></a>Save-help 프로세스

다음 목록에는 설명의 동작을 [Save-help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) 및 [Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet 도움말 파일을 파일 공유의 업데이트를 사용 하 여 해당 파일에서 도움말 파일을 업데이트 하는 명령을 실행 하는 경우는 사용자의 컴퓨터입니다.
다음 목록에는 설명의 동작을 [Save-help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) 및 [Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet 도움말 파일을 파일 공유의 업데이트를 사용 하 여 해당 파일에서 도움말 파일을 업데이트 하는 명령을 실행 하는 경우는 사용자의 컴퓨터입니다.

합니다 `Save-Help` cmdlet에 지정 된 파일 공유에서 모듈에 대 한 도움말 파일을 저장 하는 명령에 대 한 응답에서 다음 작업을 수행 합니다 **DestinationPath** 매개 변수입니다.

1. `Save-Help` 값으로 지정 된 위치에서 원격 HelpInfo XML 파일을 가져옵니다 합니다 **HelpInfoURI** 모듈 매니페스트에서 키를 스키마에 대해 파일의 유효성을 검사 합니다. (스키마를 보려면 [HelpInfo XML 스키마](./helpinfo-xml-schema.md).) 다음 `Save-Help` 에 지정 된 디렉터리에 로컬 HelpInfo XML 파일을 찾습니다 합니다 **DestinationPath** 에서 매개 변수는 `Save-Help` 명령입니다.

2. `Save-Help` 모듈에 대 한 원격 및 로컬 HelpInfo XML 파일에 지정된 된 UI 문화권에 대 한 도움말 파일의 버전 번호를 비교합니다. 있는지 모듈에 대 한 로컬 HelpInfo XML 파일이 없는 경우 또는 원격 파일에 버전 번호를 로컬 파일에 버전 번호 보다 큰 경우 합니다 **DestinationPath** 디렉터리 `Save-Help` 새 도움말 파일을 다운로드 하도록 준비 합니다.

3. `Save-Help` 지정 된 위치에서 모듈에 대 한 CAB 파일을 선택 합니다 **HelpContentUri** 원격 HelpInfo XML 파일의 요소입니다. 모듈 이름, GUID, 모듈 및 UI 문화권 사용 하 여 CAB 파일을 식별 합니다.

4. `Save-Help` CAB 파일을 다운로드 하 고에 저장 합니다 **DestinationPath** 디렉터리입니다. (문제가 발생 하지 않는 모든 언어별 하위 디렉터리입니다.)

5. `Save-Help` 원격 HelpInfo XML 파일을 복사 하 여 로컬 HelpInfo XML 파일을 만듭니다. 로컬 HelpInfo XML 파일을 편집 하는 요소를 저장 하는 CAB 파일에 대해서만 포함 되도록 합니다. 로컬 HelpInfo XML 파일에 저장 한 다음 합니다 **DestinationPath** 디렉터리 마지막 업데이트 합니다.

   합니다 `Update-Help` cmdlet에 지정 된 파일 공유의 파일에서 사용자의 컴퓨터에서 도움말 파일을 업데이트 하는 명령에 대 한 응답에서 다음 작업을 수행 합니다 **SourcePath** 매개 변수입니다.

1. `Update-Help` 원격 HelpInfo XML 파일을 가져옵니다 합니다 **SourcePath** 디렉터리입니다. 그런 다음 로컬 HelpInfo XML 파일을 모듈 디렉터리에 사용자의 컴퓨터를 찾습니다.

2. `Update-Help` 모듈에 대 한 원격 및 로컬 HelpInfo XML 파일에 지정된 된 UI 문화권에 대 한 도움말 파일의 버전 번호를 비교합니다. 원격 파일에 버전 번호를 로컬 파일에 버전 번호 보다 큰 경우 또는 있는지 로컬 HelpInfo XML 파일이 없는 경우 `Update-Help` 새 도움말 파일 설치를 준비 합니다.

3. `Update-Help` 모듈에 대 한 CAB 파일 선택 **SourcePath** 디렉터리입니다. 모듈 이름, GUID, 모듈 및 UI 문화권 사용 하 여 CAB 파일을 식별 합니다.

4. `Update-Help` CAB 파일의 압축을 푼, 도움말 콘텐츠 파일의 유효성을 검사 및 도움말 콘텐츠 파일에에서 저장 모듈 디렉터리의 언어별 하위 디렉터리 사용자의 컴퓨터

5. `Update-Help` 원격 HelpInfo XML 파일을 복사 하 여 로컬 HelpInfo XML 파일을 만듭니다. 로컬 HelpInfo XML 파일을 편집 하는 요소를 설치 하는 CAB 파일에 대해서만 포함 되도록 합니다. 그런 다음 모듈 디렉터리에 로컬 HelpInfo XML 파일을 저장 하 고 업데이트를 완료 합니다.