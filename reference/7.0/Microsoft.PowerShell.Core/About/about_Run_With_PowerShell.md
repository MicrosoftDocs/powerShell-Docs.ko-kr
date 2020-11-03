---
description: "\"PowerShell에서 실행\" 기능을 사용 하 여 파일 시스템 드라이브에서 스크립트를 실행 하는 방법을 설명 합니다."
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_run_with_powershell?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Run_With_PowerShell
ms.openlocfilehash: c5b1ca5d924c6eddd6371a269f694a5304510b25
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93223729"
---
# <a name="about-run-with-powershell"></a>PowerShell을 사용 하 여 실행 정보

## <a name="short-description"></a>간단한 설명
"PowerShell에서 실행" 기능을 사용 하 여 파일 시스템 드라이브에서 스크립트를 실행 하는 방법을 설명 합니다.

## <a name="long-description"></a>자세한 설명

Windows PowerShell 3.0부터 "PowerShell에서 실행" 기능을 사용 하 여 Windows 8 및 Windows Server 2012의 파일 탐색기와 이전 Windows 버전의 windows 탐색기에서 스크립트를 실행할 수 있습니다.

"PowerShell에서 실행" 기능은 필수 매개 변수가 없는 스크립트를 실행 하 고 출력을 명령 프롬프트로 반환 하지 않도록 설계 되었습니다.

"PowerShell에서 실행" 기능을 사용 하는 경우 PowerShell 콘솔 창이 잠깐 표시 됩니다 (있는 경우). 상호 작용할 수는 없습니다.

"PowerShell에서 실행" 기능을 사용 하려면 다음을 수행 합니다.

파일 탐색기 (또는 Windows 탐색기)에서 스크립트 파일 이름을 마우스 오른쪽 단추로 클릭 한 다음 "PowerShell에서 실행"을 선택 합니다.

"PowerShell을 사용 하 여 실행" 기능은 바이패스 실행 정책이 있는 PowerShell 세션을 시작 하 고, 스크립트를 실행 하 고, 세션을 닫습니다.

다음 형식의 명령을 실행 합니다.

```
PowerShell.exe -File <FileName> -ExecutionPolicy Bypass
```

"PowerShell에서 실행"은 스크립트가 실행 되는 세션 (PowerShell 프로세스의 현재 인스턴스)에 대해서만 바이패스 실행 정책을 설정 합니다.
이 기능은 컴퓨터 또는 사용자에 대 한 실행 정책을 변경 하지 않습니다.

"PowerShell에서 실행" 기능은 AllSigned 실행 정책에 의해서만 영향을 받습니다. AllSigned 실행 정책이 컴퓨터 또는 사용자에 게 적용 되는 경우 "PowerShell에서 실행"은 서명 된 스크립트만 실행 합니다. "PowerShell에서 실행"은 다른 실행 정책의 영향을 받지 않습니다. 자세한 내용은 [about_Execution_Policies](about_Execution_Policies.md)를 참조하세요.

문제 해결 참고: PowerShell을 사용 하 여 실행 명령은 실행 정책 변경을 확인 하는 메시지를 표시할 수 있습니다.

## <a name="see-also"></a>참고 항목

[about_Execution_Policies](about_Execution_Policies.md)

[about_Group_Policy_Settings](about_Group_Policy_Settings.md)

[about_Scripts](about_Scripts.md)
