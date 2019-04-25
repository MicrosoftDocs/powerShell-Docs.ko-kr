---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: WMF 5.1의 향상된 PowerShell 엔진
ms.openlocfilehash: 738f72b910de7d44f48309013237d523d0dd40a4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62055567"
---
# <a name="powershell-engine-improvements"></a>향상된 PowerShell 엔진

WMF 5.1에서는 핵심 PowerShell 엔진에 대한 다음과 같은 개선 사항이 구현되었습니다.

## <a name="performance"></a>성능

몇 가지 중요한 영역에서 성능이 향상되었습니다.

- 시작
- `ForEach-Object` 및 `Where-Object`와 같은 cmdlet에 대한 파이프라이닝이 약 50% 더 빠릅니다.

몇 가지 예제 개선 사항(하드웨어에 따라 결과가 달라질 수 있음):

| 시나리오 | 5.0 시간(밀리초) | 5.1 시간(밀리초) |
| -------- | :---------------: | :---------------: |
| `powershell -command "echo 1"` | 900 | 250 |
| 처음 PowerShell 실행: `powershell -command "Unknown-Command"` | 30000 | 13000 |
| 빌드된 명령 분석 캐시: `powershell -command "Unknown-Command"` | 7000 | 520 |
| <code>1..1000000 &#124; % { }</code> | 1400 | 750 |

> [!Note]
> 시작과 관련된 한 가지 변경이 몇 가지 지원되지 않는 시나리오에 영향을 줄 수 있습니다.
> PowerShell은 더 이상 `$pshome\*.ps1xml` 파일을 읽지 않습니다. XML 파일 처리의 일부 파일 및 CPU 오버헤드를 방지하기 위해 이러한 파일이 C#으로 변환되었습니다.
> 이러한 파일은 V2를 나란히 지원하기 위해 여전이 있으므로 파일 콘텐츠를 변경하는 경우 V5에는 아무 영향이 없고 V2에만 영향을 줍니다.
> 이러한 파일의 콘텐츠를 변경하는 시나리오는 지원되지 않았습니다.

또 하나의 뚜렷한 변경 사항은 PowerShell이 시스템에 설치된 모듈에 대해 내보낸 명령 및 기타 정보를 캐시하는 방법입니다.
이전에는 이 캐시가 `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis` 디렉터리에 저장되었습니다.
WMF 5.1에서 이 캐시는 단일 파일 `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache`입니다.
자세한 내용은 [모듈 분석 캐시](scenarios-features.md#module-analysis-cache)를 참조하세요.