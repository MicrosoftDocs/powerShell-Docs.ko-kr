---
title: HelpInfo XML 버전 번호를 설정 하는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 93a00463-af58-41c8-b088-450909fa1d05
caps.latest.revision: 6
ms.openlocfilehash: b98e6879bbfe0e3ec1a9ab37496dde44caf523a4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082280"
---
# <a name="how-to-set-helpinfo-xml-version-numbers"></a>HelpInfo XML 버전 번호를 설정하는 방법

이 항목에서는 일반적으로 "HelpInfo XML 파일입니다."로 알려진 업데이트할 수 있는 도움말 정보 파일에 버전 번호를 높이고 설정 하는 방법 설명

## <a name="how-to-set-helpinfo-xml-version-numbers"></a>HelpInfo XML 버전 번호를 설정하는 방법

HelpInfo XML 파일에 버전 번호는 업데이트할 수 있는 도움말의 작동에 중요 합니다.
합니다 [Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) 하 고 [Save-help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlet 원격 HelpInfo XML 파일에는 UI 문화권에 대 한 버전 번호를 해당 UI 문화권에 대 한 버전 번호 보다 큰 경우에 새 도움말 파일을 다운로드 합니다 로컬 HelpInfo XML 또는 로컬 HelpInfo XML 파일이 없습니다.

HelpInfo XML 파일에 정의 된 4 부 버전 번호를 사용 합니다 **System.Version** Microsoft.NET Framework의 클래스입니다. 형식은 `N1.N2.N3.N4`합니다. 모듈 작성자는 번호 매기기 체계에서 허용 되는 모든 버전을 사용할 수는 **System.Version** 클래스입니다. 업데이트 가능한 도움말에서는 버전 번호를 증가 하는 UI 문화권에 대 한 해당 UI 문화권에 대 한 CAB 파일의 새 버전으로 지정 된 위치에 업로드 되 면 합니다 **HelpContentURI** HelpInfo XML 파일의 요소입니다.

다음 예제에서는 버전 2.15.0.10 경우 독일어 (DE-DE) UI 문화권에 대 한 HelpInfo XML 파일의 요소를 보여 줍니다.

```xml

<UICulture>
  <UICultureName>de-DE</UICultureName>
  <UICultureVersion>2.15.0.10</UICultureVersion>
</UICulture>
```

UI 문화권에 대 한 버전 번호를 해당 UI 문화권에 대 한 CAB 파일의 버전을 나타냅니다. 전체 CAB 파일에 버전 번호를 적용 됩니다. CAB 파일에 다른 파일에 대 한 다양 한 버전 번호를 설정할 수 없습니다. 각 UI 문화권에 대 한 버전 번호를 독립적으로 계산 됩니다 및 다른 모듈에서 지 원하는 UI 문화권에 대 한 버전 번호에 관련 될 필요 합니다.