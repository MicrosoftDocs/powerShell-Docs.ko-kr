---
title: 만들기 및 CAB 파일을 업로드 하는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8d35f233-5447-48a2-a961-9fbca763262b
caps.latest.revision: 7
ms.openlocfilehash: 9928a0b31a57d42eb39cea1af0509613c483caf7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082382"
---
# <a name="how-to-create-and-upload-cab-files"></a>CAB 파일을 만들고 업로드하는 방법

이 항목에서는 업데이트 가능한 도움말 CAB 파일을 만들고 업데이트할 수 있는 도움말 cmdlet을 찾을 수 있는 위치에 업로드 하는 방법을 설명 합니다.

## <a name="how-to-create-and-upload-updatable-help-cab-files"></a>만들기 및 업데이트 가능한 도움말 CAB 파일을 업로드 하는 방법

여러 언어 및 문화권의 모듈에 대 한 새롭거나 업데이트 된 도움말 파일을 제공 하도록 업데이트할 수 있는 도움말 기능을 사용할 수 있습니다. 한 HelpInfo XML 파일의 모듈을 업데이트할 수 있는 도움말 패키지를 구성 하 고 하나 이상의 캐비닛 (합니다. CAB) 파일입니다. 각 CAB 파일에는 UI 문화권의 모듈에 대 한 도움말 파일이 포함 됩니다. 업데이트할 수 있는 도움말에 대 한 CAB 파일을 만들려면 다음 절차를 사용 합니다.

1. UI 문화권에 따라 모듈에 대 한 도움말 파일을 구성 합니다. 업데이트 가능한 도움말 CAB 파일 각 UI 문화권에 하나의 모듈에 대 한 도움말 파일을 포함합니다. 여러 UI 문화권에 대 한 각 모듈에 대 한 CAB 파일 여러 도움말을 제공할 수 있습니다.

2. 확인 하는 도움말 파일 도움말 파일 스키마에 대해 유효성을 검사할 및 업데이트할 수 있는 도움말에 대 한 허용 파일 형식만 포함 됩니다. 경우는 `Update-Help` 는 유효 하지 않거나 허용 된 형식이 아닌 파일을 발견 하는 cmdlet를에서 CAB 파일 설치를 중지 하 고 잘못 된 파일을 설치 하지 않습니다. 허용 된 파일 형식 목록을 참조 하세요 [업데이트할 수 있는 도움말 CAB 파일에서 파일 형식을 허용](./file-types-permitted-in-an-updatable-help-cab-file.md)합니다.

3. 도움말 파일을 디지털 서명 합니다. 디지털 서명 필요 없는 되지만 가장 좋습니다.

4. 도움말 파일 UI에서 모듈에 대 한 문화권을 새롭게 제공 되는 파일 뿐 아니라 추가 되거나 변경 된 모든 포함 됩니다. CAB 파일을 완전 하지 않으면 처음에 대 한 도움말 파일을 다운로드 하거나 모든 업데이트를 다운로드 하려면 사용자에 모듈 도움말 파일의 모두가지고 있지 않습니다.

5. MakeCab.exe 같은 캐비닛 파일을 만드는 유틸리티를 사용 합니다. Windows PowerShell에서 CAB 파일을 만드는 cmdlet을 포함 하지 않습니다.

6. CAB 파일 이름을 지정 합니다. 자세한 내용은 [업데이트할 수 있는 도움말 CAB 파일 이름 지정 방법](./how-to-name-an-updatable-help-cab-file.md)합니다.

7. 지정 된 위치에 모듈에 대 한 CAB 파일을 업로드 합니다 **HelpContentUri** 모듈에 대 한 HelpInfo XML 파일의 요소입니다. 다음으로 지정 된 위치로 HelpInfo XML 파일을 업로드 합니다 **HelpInfoUri** 모듈 매니페스트 키입니다. 합니다 **HelpContentUri** 하 고 **HelpInfoUri** 동일한 위치를 가리킬 수 있습니다.

> [!CAUTION]
> 값을 **HelpInfoUri** 키와 **HelpContentUri** 요소 "http" 또는 "https"로 시작 해야 합니다. 값에는 인터넷 위치를 나타내야 하 고 파일 이름을 포함할 수 없습니다.