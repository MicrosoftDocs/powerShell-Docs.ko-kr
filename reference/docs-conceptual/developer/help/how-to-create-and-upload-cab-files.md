---
title: CAB 파일을 만들고 업로드 하는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8d35f233-5447-48a2-a961-9fbca763262b
caps.latest.revision: 7
ms.openlocfilehash: 37b31aa77dde23c1bd57a9af67e2232ef0827005
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/23/2020
ms.locfileid: "83811762"
---
# <a name="how-to-create-and-upload-cab-files"></a>CAB 파일을 만들고 업로드하는 방법

이 항목에서는 업데이트할 수 있는 도움말 CAB 파일을 만들고 업데이트할 수 있는 도움말 cmdlet에서 해당 파일을 찾을 수 있는 위치에 업로드 하는 방법을 설명 합니다.

## <a name="how-to-create-and-upload-updatable-help-cab-files"></a>업데이트할 수 있는 도움말 CAB 파일을 만들고 업로드 하는 방법

업데이트할 수 있는 도움말 기능을 사용 하 여 여러 언어 및 문화권의 모듈에 대 한 새로운 또는 업데이트 된 도움말 파일을 배달할 수 있습니다. 모듈에 대 한 업데이트할 수 있는 도움말 패키지는 하나의 HelpInfo XML 파일과 하나 이상의 캐비닛 ()으로 구성 됩니다. CAB) 파일. 각 CAB 파일에는 한 가지 UI 문화권의 모듈에 대 한 도움말 파일이 포함 되어 있습니다. 업데이트할 수 있는 도움말의 CAB 파일을 만들려면 다음 절차를 따르십시오.

1. UI 문화권에 따라 모듈에 대 한 도움말 파일을 구성 합니다. 각 업데이트할 수 있는 도움말 CAB 파일에는 한 가지 UI 문화권의 한 모듈에 대 한 도움말 파일이 포함 되어 있습니다. 각 모듈에 대해 서로 다른 UI 문화권에 대 한 여러 도움말 CAB 파일을 제공할 수 있습니다.

2. 도움말 파일에 업데이트 가능한 도움말에 허용 된 파일 형식만 포함 되어 있는지 확인 하 고 도움말 파일 스키마에 대해 유효성 검사를 수행 합니다. Cmdlet이 `Update-Help` 잘못 되었거나 허용 되는 형식이 아닌 파일을 발견 하는 경우 잘못 된 파일을 설치 하지 않고 CAB에서 파일 설치를 중지 합니다. 허용 되는 파일 형식 목록은 [업데이트할 수 있는 도움말 CAB 파일에서 허용 되는 파일 형식](./file-types-permitted-in-an-updatable-help-cab-file.md)을 참조 하세요.

3. 도움말 파일에 디지털 서명 합니다. 디지털 서명은 필요 하지 않지만 모범 사례입니다.

4. 새 파일 또는 변경 된 파일 뿐만 아니라 UI 문화권의 모듈에 대 한 도움말 파일을 모두 포함 합니다. CAB 파일이 완전 하지 않은 경우 처음으로 도움말 파일을 다운로드 하거나 모든 업데이트를 다운로드 하지 않는 사용자에 게는 모듈 도움말 파일이 모두 포함 되지 않습니다.

5. MakeCab와 같은 캐비닛 파일을 만드는 유틸리티를 사용 합니다. Windows PowerShell에는 CAB 파일을 만드는 cmdlet이 포함 되어 있지 않습니다.

6. CAB 파일의 이름을로 합니다. 자세한 내용은 [업데이트할 수 있는 도움말 CAB 파일의 이름을 추가 하는 방법](./how-to-name-an-updatable-help-cab-file.md)을 참조 하세요.

7. 모듈에 대 한 HelpInfo XML 파일의 **Helpcontenturi** 요소에 지정 된 위치에 모듈의 CAB 파일을 업로드 합니다. 그런 다음 HelpInfo XML 파일을 모듈 매니페스트의 **HelpInfoUri** 키로 지정 된 위치에 업로드 합니다. **Helpcontenturi** 및 **HelpInfoUri** 는 동일한 위치를 가리킬 수 있습니다.

> [!CAUTION]
> **HelpInfoUri** Key 및 **helpcontenturi** 요소의 값은 "http" 또는 "https"로 시작 해야 합니다. 값은 인터넷 위치를 나타내야 하며 파일 이름을 포함 하지 않아야 합니다.
