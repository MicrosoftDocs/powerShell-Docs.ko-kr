---
description: PowerShell에서 수집 된 원격 분석과 옵트아웃 하는 방법에 대해 설명 합니다.
keywords: PowerShell
Locale: en-US
ms.date: 08/09/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_telemetry?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Telemetry
ms.openlocfilehash: ef921d0feefe277c2832c0a459ae150c9a6b4acb
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93222338"
---
# <a name="about-telemetry"></a>원격 분석 정보

## <a name="short-description"></a>간단한 설명

PowerShell에서 수집 된 원격 분석과 옵트아웃 하는 방법에 대해 설명 합니다.

## <a name="long-description"></a>자세한 설명

PowerShell은 기본 원격 분석 데이터를 Microsoft로 보냅니다.
이 데이터를 사용하면 PowerShell이 사용되는 환경을 더 잘 이해할 수 있으며, 새 기능 및 수정 사항의 우선 순위를 지정할 수 있습니다.
다음 원격 분석 지점이 기록 됩니다.

- 유형별 PowerShell 시작 수 (API vs 콘솔)
- 고유한 PowerShell 사용 수
- 다음 실행 유형의 수:
  - 응용 프로그램 (네이티브 명령)
  - ExternalScript
  - 스크립트
  - 함수
  - cmdlet
- PowerShell과 함께 제공 되는 Microsoft 소유의 실험적 기능 또는 실험적 기능 개수
- 호스트 된 세션 수
- 로드 된 Microsoft 소유 모듈 수

이 데이터에는 OS 이름, OS 버전, PowerShell 버전 및 배포 채널이 포함 됩니다.

이 원격 분석을 옵트아웃 하려면 환경 변수 POWERSHELL_TELEMETRY_OPTOUT을 true, 예 또는 1로 설정 합니다.

