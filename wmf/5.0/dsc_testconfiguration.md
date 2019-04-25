---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 4008a7f91af41150f26c4147135b30aa8835281c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058746"
---
# <a name="test-dscconfiguration-cmdlet-supports-reference-configurations"></a>Test-DscConfiguration cmdlet에서 참조 구성 지원

Test-DscConfiguration cmdlet은 비교할 참조 구성 문서를 지정하여 하나 이상 대상 노드의 원하는 구성 상태를 테스트할 수 있도록 업데이트되었습니다.

다음과 같은 새 매개 변수 집합은 지정된 경로의 DSC 구성을 사용하여 테스트만 수행하고 지정된 대상 노드에서 각 구성을 적용하지는 않습니다. Start-DscConfiguration 및 다른 DSC cmdlet과 마찬가지로 각 MOF의 이름을 사용하여 구성을 테스트할 대상 노드를 확인합니다.

```powershell
Test-DscConfiguration   [-Path] <string>
                        [[-ComputerName] <string[]>]
                        [-Credential <pscredential>]
                        [-ThrottleLimit <int>]
                        [-AsJob]
                        [<CommonParameters>]

Test-DscConfiguration   [-Path] <string>
                        -CimSession <CimSession[]>
                        [-ThrottleLimit <int>]
                        [-AsJob]
                        [<CommonParameters>]
```

다음과 같은 새 매개 변수 집합은 단일 DSC 구성을 사용하여 테스트만 수행하고 지정된 대상 노드에서 구성을 적용하지는 않습니다.

```powershell
Test-DscConfiguration   -ReferenceConfiguration <string>
                        [[-ComputerName] <string[]>]
                        [-Credential <pscredential>]
                        [-ThrottleLimit <int>]
                        [-AsJob]
                        [<CommonParameters>]

Test-DscConfiguration   -ReferenceConfiguration <string>
                        -CimSession <CimSession[]>
                        [-ThrottleLimit <int>]
                        [-AsJob]
                        [<CommonParameters>]
```
