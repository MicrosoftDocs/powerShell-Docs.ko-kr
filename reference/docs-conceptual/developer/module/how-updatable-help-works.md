---
title: 업데이트할 수 있는 도움말의 작동 방식 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7674636e-a0f2-4587-bfc5-dd3e6ce5489e
caps.latest.revision: 6
ms.openlocfilehash: e555741185f3d17b4099671d70dbc0545bfd5306
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83560239"
---
# <a name="how-updatable-help-works"></a>업데이트 가능한 도움말 작동 방법

이 항목에서는 업데이트 가능한 도움말에서 각 모듈의 HelpInfo XML 파일 및 CAB 파일을 처리 하는 방법에 대해 설명 하 고 사용자를 위해 업데이트 된 도움말을 설치 합니다.

## <a name="the-update-help-process"></a>Update-help 프로세스

다음 목록에서는 사용자가 특정 UI 문화권의 모듈에 대 한 도움말 파일을 업데이트 하는 명령을 실행할 때 [update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet의 작업에 대해 설명 합니다.

1. `Update-Help`모듈 매니페스트의 **HelpInfoURI** 키 값으로 지정 된 위치에서 원격 HelpInfo XML 파일을 가져오고 스키마에 대해 파일의 유효성을 검사 합니다. 스키마를 보려면 [HELPINFO XML 스키마](./helpinfo-xml-schema.md)를 참조 하세요. 그런 다음은 `Update-Help` 사용자의 컴퓨터에 있는 module 디렉터리에서 모듈에 대해 로컬 HELPINFO XML 파일을 찾습니다.

2. `Update-Help`모듈에 대 한 원격 및 로컬 HelpInfo XML 파일에서 지정 된 UI 문화권에 대 한 도움말 파일의 버전 번호를 비교 합니다. 원격 파일의 버전 번호가 로컬 파일의 버전 번호 보다 크거나 모듈에 대해 로컬 HelpInfo XML 파일이 없으면에서 `Update-Help` 새 도움말 파일을 다운로드할 준비를 합니다.

3. `Update-Help`원격 HelpInfo XML 파일의 **Helpcontenturi** 요소에 지정 된 위치에서 모듈의 CAB 파일을 선택 합니다. 모듈 이름, 모듈 GUID 및 UI 문화권을 사용 하 여 CAB 파일을 식별 합니다.

4. `Update-Help`CAB 파일을 다운로드 하 여 압축을 풀고, 도움말 콘텐츠 파일의 유효성을 검사 하 고, 사용자 컴퓨터에 있는 모듈 디렉터리의 언어별 하위 디렉터리에 도움말 콘텐츠 파일을 저장 합니다.

5. `Update-Help`원격 HelpInfo XML 파일을 복사 하 여 로컬 HelpInfo XML 파일을 만듭니다. 설치한 CAB 파일에 대 한 요소만 포함 되도록 로컬 HelpInfo XML 파일을 편집 합니다. 그런 다음 모듈 디렉터리에 로컬 HelpInfo XML 파일을 저장 하 고 업데이트를 마칩니다.

## <a name="the-save-help-process"></a>저장-도움말 프로세스

다음 목록에서는 사용자가 명령을 실행 하 여 파일 공유의 도움말 파일을 업데이트 한 다음 해당 파일을 사용 하 여 사용자 컴퓨터의 도움말 파일을 업데이트할 때 [저장-도움말](/powershell/module/Microsoft.PowerShell.Core/Save-Help) 및 [update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet의 작업에 대해 설명 합니다.

`Save-Help`Cmdlet은 **DestinationPath** 매개 변수로 지정 된 파일 공유의 모듈에 대 한 도움말 파일을 저장 하는 명령에 대 한 응답으로 다음 작업을 수행 합니다.

1. `Save-Help`모듈 매니페스트의 **HelpInfoURI** 키 값으로 지정 된 위치에서 원격 HelpInfo XML 파일을 가져오고 스키마에 대해 파일의 유효성을 검사 합니다. 스키마를 보려면 [HELPINFO XML 스키마](./helpinfo-xml-schema.md)를 참조 하세요. 그런 다음 `Save-Help` 명령에서 **DestinationPath** 매개 변수로 지정 된 디렉터리에서 로컬 HelpInfo XML 파일을 찾습니다 `Save-Help` .

2. `Save-Help`모듈에 대 한 원격 및 로컬 HelpInfo XML 파일에서 지정 된 UI 문화권에 대 한 도움말 파일의 버전 번호를 비교 합니다. 원격 파일의 버전 번호가 로컬 파일의 버전 번호 보다 크거나 **DestinationPath** 디렉터리의 모듈에 대 한 로컬 HelpInfo XML 파일이 없으면에서 `Save-Help` 새 도움말 파일을 다운로드할 준비를 합니다.

3. `Save-Help`원격 HelpInfo XML 파일의 **Helpcontenturi** 요소에 지정 된 위치에서 모듈의 CAB 파일을 선택 합니다. 모듈 이름, 모듈 GUID 및 UI 문화권을 사용 하 여 CAB 파일을 식별 합니다.

4. `Save-Help`CAB 파일을 다운로드 하 여 **DestinationPath** 디렉터리에 저장 합니다. 언어 관련 하위 디렉터리를 만들지 않습니다.

5. `Save-Help`원격 HelpInfo XML 파일을 복사 하 여 로컬 HelpInfo XML 파일을 만듭니다. 저장 한 CAB 파일에 대 한 요소만 포함 되도록 로컬 HelpInfo XML 파일을 편집 합니다. 그런 다음 로컬 HelpInfo XML 파일을 **DestinationPath** 디렉터리에 저장 하 고 업데이트를 마칩니다.

   `Update-Help`Cmdlet은 **SourcePath** 매개 변수로 지정 된 파일 공유의 파일에서 사용자 컴퓨터의 도움말 파일을 업데이트 하는 명령에 대 한 응답으로 다음 작업을 수행 합니다.

1. `Update-Help`**SourcePath** 디렉터리에서 원격 HelpInfo XML 파일을 가져옵니다. 그런 다음 사용자 컴퓨터의 모듈 디렉터리에서 로컬 HelpInfo XML 파일을 찾습니다.

2. `Update-Help`모듈에 대 한 원격 및 로컬 HelpInfo XML 파일에서 지정 된 UI 문화권에 대 한 도움말 파일의 버전 번호를 비교 합니다. 원격 파일의 버전 번호가 로컬 파일의 버전 번호 보다 크거나 로컬 HelpInfo XML 파일이 없는 경우에서 `Update-Help` 새 도움말 파일을 설치할 준비를 합니다.

3. `Update-Help`**SourcePath** 디렉터리에서 모듈의 CAB 파일을 선택 합니다. 모듈 이름, 모듈 GUID 및 UI 문화권을 사용 하 여 CAB 파일을 식별 합니다.

4. `Update-Help`CAB 파일의 압축을 풀고, 도움말 콘텐츠 파일의 유효성을 검사 하 고, 사용자 컴퓨터에 있는 모듈 디렉터리의 언어별 하위 디렉터리에 도움말 콘텐츠 파일을 저장 합니다.

5. `Update-Help`원격 HelpInfo XML 파일을 복사 하 여 로컬 HelpInfo XML 파일을 만듭니다. 설치한 CAB 파일에 대 한 요소만 포함 되도록 로컬 HelpInfo XML 파일을 편집 합니다. 그런 다음 모듈 디렉터리에 로컬 HelpInfo XML 파일을 저장 하 고 업데이트를 마칩니다.
