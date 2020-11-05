---
ms.date: 06/12/2017
title: WMF 5.0 제거
description: 이 문서에서는 이전 버전의 Windows에서 WMF를 제거하는 방법을 설명합니다.
ms.openlocfilehash: d8078ea918db2c1cf9a7ddd6ea8d1413b593c0ff
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92660812"
---
# <a name="uninstallation-instructions"></a>제거 지침

## <a name="using-command-prompt"></a>명령 프롬프트 사용

1. **명령 프롬프트** 를 엽니다.
2. 아래와 같이 [Windows 업데이트 독립 실행형 시작 관리자](https://support.microsoft.com/kb/934307)를 실행합니다.

Windows Server 2012 R2 및 Windows 8.1:

```powershell
wusa /uninstall /kb:3134758
```

Windows Server 2012:

```powershell
wusa /uninstall /kb:3134759
```

Windows Server 2008 R2 SP1 및 Windows 7 SP1:

```powershell
wusa /uninstall /kb:3134760
```

## <a name="using-control-panel"></a>제어판 사용

1. **제어판** 을 엽니다.
2. **프로그램** 을 연 다음 **프로그램 제거** 를 엽니다.
3. **설치된 업데이트 보기** 를 클릭합니다.
4. 설치된 업데이트 목록에서 **Windows Management Framework 5.0** 을 선택합니다. *KB3134758* , *KB3134759* 또는 *KB3134760* 에 해당합니다. **제거** 를 클릭합니다.
