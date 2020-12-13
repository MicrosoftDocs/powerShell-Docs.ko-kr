---
ms.date: 09/12/2016
ms.topic: reference
title: HelpInfo XML 버전 번호를 설정하는 방법
description: HelpInfo XML 버전 번호를 설정하는 방법
ms.openlocfilehash: 9ef1940ca05d8aa9b04770013287490b71c8065a
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92658839"
---
# <a name="how-to-set-helpinfo-xml-version-numbers"></a>HelpInfo XML 버전 번호를 설정하는 방법

이 항목에서는 일반적으로 "HelpInfo XML file" 이라는 업데이트 가능한 도움말 정보 파일에서 버전 번호를 설정 하 고 늘리는 방법을 설명 합니다.

## <a name="how-to-set-helpinfo-xml-version-numbers"></a>HelpInfo XML 버전 번호를 설정하는 방법

HelpInfo XML 파일의 버전 번호는 업데이트할 수 있는 도움말의 작업에 중요 합니다. [업데이트-도움말](/powershell/module/Microsoft.PowerShell.Core/Update-Help) 및 [저장-도움말](/powershell/module/Microsoft.PowerShell.Core/Save-Help) CMDLET은 원격 HELPINFO xml 파일의 ui 문화권에 대 한 버전 번호가 로컬 HELPINFO xml의 해당 ui 문화권에 대 한 버전 번호 보다 크거나 로컬 HelpInfo xml 파일이 없는 경우에만 새 도움말 파일을 다운로드 합니다.

HelpInfo XML 파일은 Microsoft .NET Framework의 **system.object** 클래스에 정의 된 네 부분으로 구성 된 버전 번호를 사용 합니다. 형식은 `N1.N2.N3.N4`입니다. 모듈 작성자는 **system.object** 클래스에서 허용 하는 모든 버전 번호 지정 체계를 사용할 수 있습니다. 업데이트할 수 있는 도움말을 사용 하려면 해당 UI 문화권에 대 한 새 버전의 CAB 파일을 HelpInfo XML 파일의 **Helpcontenturi** 요소로 지정 된 위치에 업로드할 때 ui 문화권의 버전 번호를 늘려야 합니다.

다음 예제에서는 버전이 2.15.0.10 인 경우 독일어 (de-de) UI 문화권에 대 한 HelpInfo XML 파일의 요소를 보여 줍니다.

```xml
<UICulture>
  <UICultureName>de-DE</UICultureName>
  <UICultureVersion>2.15.0.10</UICultureVersion>
</UICulture>
```

UI 문화권의 버전 번호는 해당 UI 문화권에 대 한 CAB 파일의 버전을 반영 합니다. 버전 번호는 전체 CAB 파일에 적용 됩니다. CAB 파일의 다른 파일에 다른 버전 번호를 설정할 수 없습니다. 각 UI 문화권의 버전 번호는 독립적으로 평가 되며 모듈에서 지 원하는 다른 UI 문화권의 버전 번호와 관련 될 필요가 없습니다.
