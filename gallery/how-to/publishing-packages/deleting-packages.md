---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: 패키지 삭제
ms.openlocfilehash: ca5e68fcad52e4c7561d2c2b3858228652f22e0b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084167"
---
# <a name="deleting-packages"></a>패키지 삭제

PowerShell 갤러리는 패키지를 계속 사용해야 하는 사용자에게 영향을 주기 때문에 패키지의 영구 삭제를 지원하지 않습니다.

대신, PowerShell 갤러리는 패키지를 '목록에서 제거'하는 방법을 지원합니다. 이 작업은 웹 사이트의 패키지 관리 페이지에서 수행할 수 있습니다.
패키지가 목록에서 제거되면 PowerShell 갤러리와 PowerShellGet 명령 사용 시 둘 다에서 검색과 패키지 목록에 더 이상 표시되지 않습니다.
그러나 정확한 버전을 지정하여 자동화된 스크립트가 계속 작동할 수 있게 하면 항목을 다운로드할 수 있습니다.

패키지 중 하나를 삭제해야 하는 예외적인 상황이 발생할 경우 PowerShell 갤러리 팀이 수동으로 처리할 수 있습니다.
예를 들어 저작권 침해 문제 또는 잠재적으로 유해한 콘텐츠가 있을 경우 항목을 삭제해야 하는 유효한 이유가 될 수 있습니다.
이 경우 [PowerShell 갤러리](http://www.PowerShellGallery.com)를 통해 지원 요청을 제출해야 합니다.
