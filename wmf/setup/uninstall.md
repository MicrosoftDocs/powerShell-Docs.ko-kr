---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: WMF 5.0 제거
ms.openlocfilehash: f562a4a4506bfdede6b23bd186b80f40cc9e45ca
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855468"
---
# <a name="uninstallation-instructions"></a>제거 지침

## <a name="using-command-prompt"></a>명령 프롬프트 사용

1. **명령 프롬프트**를 엽니다.
2. 아래와 같이 [Windows 업데이트 독립 실행형 시작 관리자](https://support.microsoft.com/en-us/kb/934307)를 실행합니다.

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

1. **제어판**을 엽니다.
2. **프로그램**을 연 다음 **프로그램 제거**를 엽니다.
3. **설치된 업데이트 보기**를 클릭합니다.
4. 설치된 업데이트 목록에서 **Windows Management Framework 5.0**을 선택합니다. *KB3134758*, *KB3134759* 또는 *KB3134760*에 해당합니다. **제거**를 클릭합니다.
