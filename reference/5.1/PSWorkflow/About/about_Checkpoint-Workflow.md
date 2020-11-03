---
description: 워크플로에서 검사점을 사용 하는 Checkpoint-Workflow 작업에 대해 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflow/about/about_checkpoint-workflow?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Checkpoint 워크플로
ms.openlocfilehash: 223deb07ff6ed387cf04736116ea0ce3f998bb59
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93221913"
---
# <a name="about-checkpoint-workflow"></a>Checkpoint-Workflow 정보

## <a name="short-description"></a>간단한 설명
워크플로에서 검사점을 사용 하는 Checkpoint-Workflow 작업에 대해 설명 합니다.

## <a name="long-description"></a>자세한 설명

Checkpoint-Workflow 작업은 워크플로의 상태와 데이터를 저장 하는 검사점을 사용 합니다. 워크플로가 일시 중단 또는 중단 된 경우 다시 시작 하는 대신 가장 최근 검사점에서 다시 시작할 수 있습니다.

Checkpoint-Workflow 작업은 워크플로에서만 유효 합니다.

### <a name="syntax"></a>SYNTAX

```
Workflow <Verb-Noun>
{
    Checkpoint-Workflow
}
```

Checkpoint-Workflow 활동은 일반 매개 변수 및 워크플로 일반 매개 변수를 포함 하 여 매개 변수를 허용 하지 않습니다.

워크플로 내에서 CmdletBinding 또는 Param 문 뒤에 Checkpoint-Activity 검사점을 추가할 수 있습니다. 그러나 검사점을 배치할 때 데이터를 수집 하 고 워크플로를 실행 하는 컴퓨터의 디스크에 기록 하는 성능 비용을 고려해 야 합니다.

중단된 워크플로의 한 섹션을 다시 실행하는 데 걸리는 시간이 검사점 상태 및 데이터를 디스크에 쓰는 데 걸리는 시간보다 큰지 확인합니다.

워크플로를 다시 시작 하지 않고 다시 시작할 수 있도록 중요 한 단계 다음에 검사점을 만드는 것이 좋습니다. 예를 들어 idempotent 되지 않은 명령 다음에 검사점을 사용 합니다.

### <a name="about-checkpoints"></a>검사점 정보

검사점은 변수의 현재 값 및 해당 지점까지 생성된 출력을 포함하는 현재 워크플로 상태의 스냅숏이며 디스크에 저장됩니다.

워크플로가 중단 된 경우 의도적으로 또는 실수로 Windows PowerShell 워크플로에서 최신 검사점의 데이터를 자동으로 사용 하 여 워크플로를 복구 하 고 다시 시작 합니다.

AsJob 워크플로 일반 매개 변수를 사용 하는 등의 방법으로 워크플로를 작업으로 실행 하는 경우에는 Remove-Job cmdlet을 사용 하는 등의 작업을 삭제할 때까지 워크플로 검사점이 보존 됩니다.
그렇지 않으면 워크플로가 완료 될 때 워크플로 검사점이 삭제 됩니다.

### <a name="other-checkpointing-techniques"></a>기타 검사점 방법

Checkpoint-Workflow 작업 외에도 Windows PowerShell 워크플로는 다음을 비롯 한 다른 검사점을 지원 합니다.

- PSPersist 워크플로 일반 매개 변수
- PSPersist 활동 일반 매개 변수
- PSPersistPreference 설정 변수 (워크플로의)

워크플로에 검사점을 추가 하는 방법에 대 한 자세한 내용은 "워크플로에 검사점을 추가 하는 방법"을 참조 하십시오.

## <a name="examples"></a>예제

다음 워크플로에는 장기 실행 함수를 완료 한 후 Checkpoint-Workflow 작업에 대 한 호출과 데이터를 공유 하는 스크립트가 포함 되어 있습니다.

```powershell
Workflow Test-Workflow
{
    $a = Invoke-LongRunningFunction
    InlineScript { \\Server\Share\Get-DataPacks.ps1 $Using:a}
    Checkpoint-Workflow

    Invoke-LongRunningFunction
    {
        ...
    }
}
```

## <a name="see-also"></a>참고 항목

[Windows PowerShell 워크플로 작성](/previous-versions/powershell/scripting/developer/workflow/writing-a-windows-powershell-workflow)
