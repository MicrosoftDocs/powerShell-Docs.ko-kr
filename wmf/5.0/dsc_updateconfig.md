---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 31fde15e644455dbe77f68bca713bf026544fdc7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55682773"
---
# <a name="on-demand-pull-of-dsc-configurations"></a>DSC 구성의 요청 시 끌어오기

새로운 Update-DscConfiguration cmdlet은 메타 구성에 정의된 끌어오기 서버에서 끌어오기를 트리거합니다. 이러한 동작을 종종 '지금 끌어오기'라고 합니다.


트리거된 끌어오기는 일반적인 주기 중에 트리거된 경우와 정확히 동일하게 동작합니다.

1. 현재 구성에 대한 체크섬을 끌어오기 서버의 구성에 대한 체크섬과 비교합니다.
2. 동일한 경우 구성을 적용하지 않고 완료합니다.
3. 다른 경우 구성을 끌어오기 서버에서 아래로 끌어와 적용합니다.

**참고:** 메타 구성 RefreshMode = 'Push'이면 이 cmdlet에서 오류가 반환되므로 이 cmdlet은 대상 노드가 '밀어넣기' 모드일 경우 항상 아무 작업도 수행하지 않습니다.

```powershell
Update-DscConfiguration     [[-ComputerName] <string[]>]
                            [-Wait]
                            [-Force]
                            [-JobName <string>]
                            [-Credential<pscredential>]
                            [-ThrottleLimit <int>]
                            [-WhatIf]
                            [-Confirm]
                            [<CommonParameters>]

Update-DscConfiguration     -CimSession <CimSession[]>
                            [-Wait]
                            [-Force]
                            [-JobName <string>]
                            [-ThrottleLimit <int>]
                            [-WhatIf]
                            [-Confirm]
                            [<CommonParameters>]
```
