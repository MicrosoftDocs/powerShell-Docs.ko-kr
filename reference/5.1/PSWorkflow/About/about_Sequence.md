---
description: '`Sequence`선택한 작업을 순차적으로 실행 하는 키워드에 대해 설명 합니다.'
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflow/about/about_sequence?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Sequence
ms.openlocfilehash: a9dd4fb24274fe4e1478ca69c734b43a2f196792
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93221882"
---
# <a name="about-sequence"></a>시퀀스 정보

## <a name="short-description"></a>간단한 설명

`Sequence`선택한 작업을 순차적으로 실행 하는 키워드에 대해 설명 합니다.

## <a name="long-description"></a>자세한 설명입니다.

`Sequence`키워드는 선택한 워크플로 활동을 순차적으로 실행 합니다. 워크플로 작업은 표시 되는 순서 대로 실행 되며 동시에 실행 되지 않습니다. `Sequence`키워드는 PowerShell 워크플로에서만 유효 합니다.

`Sequence`키워드는 `Parallel` 스크립트 블록에서 선택 된 명령을 순차적으로 실행 하는 데 사용 됩니다.

워크플로 작업은 기본적으로 순차적으로 실행 되므로 `Sequence` 키워드는 스크립트 블록 에서만 유효 `Parallel` 합니다. `Sequence`키워드가 스크립트 블록에 포함 되지 않은 경우 `Parallel` 유효 하지만 유효 하지 않습니다.

`Sequence`스크립트 블록을 사용 하면 종속 명령을 순차적으로 실행할 수 있으므로 더 많은 명령을 병렬로 실행할 수 있습니다.

## <a name="syntax"></a>구문

### <a name="workflow-using-sequence"></a>시퀀스를 사용 하는 워크플로

```
workflow <Verb-Noun>
{
    Sequence
    {
        [<Activity>]
        [<Activity>]
        # ...
    }
}
```

### <a name="workflow-using-parallel-and-sequence"></a>병렬 및 시퀀스를 사용 하는 워크플로

```
workflow <Verb-Noun>
{
    Parallel
    {
        [<Activity>]
        Sequence
        {
            [<Activity>]
            [<Activity>]
            # ...
        }
    }
}
```

## <a name="detailed-description"></a>자세한 설명

`Parallel` 스크립트 블록의 명령은 동시에 실행될 수 있습니다. 실행 순서가 정해져 있지 않습니다. 이 기능은 스크립트 워크플로의 성능을 향상 시킵니다.

`Sequence`활동을 스크립트 블록에 표시 하더라도 스크립트 블록을 사용 하 여 선택한 활동을 순차적으로 실행할 수 있습니다 `Parallel` .

스크립트 블록의 활동은 `Sequence` 나열 된 순서 대로 연속적으로 실행 됩니다. 스크립트 블록의 작업은 `Sequence` 이전 작업이 완료 된 후에만 시작 됩니다.

그러나 스크립트 블록이 스크립트 블록에 표시 되 면 스크립트 블록을 실행 하는 `Sequence` `Parallel` 순서는 `Sequence` 결정 되지 않습니다. 스크립트 블록에서 다른 작업을 수행 하기 전이나 후에 실행 될 수 있습니다 `Parallel` .

예를 들어 다음 워크플로에는 `Parallel` 컴퓨터의 프로세스 및 서비스를 가져오는 활동을 실행 하는 스크립트 블록이 포함 되어 있습니다. `Parallel`스크립트 블록에는 `Sequence` 파일에서 정보를 가져오고 스크립트에 대 한 입력으로 정보를 사용 하는 스크립트 블록이 포함 되어 있습니다.

`Get-Process`, `Get-Service` 및 핫픽스 관련 명령은 서로 독립적입니다. 명령은 순서에 관계 없이 동시에 실행할 수 있습니다. 그러나 핫픽스 정보를 가져오는 명령은이 명령을 사용 하는 명령을 실행 하기 전에 실행 해야 합니다.

```powershell
workflow Test-Workflow
{
    Parallel
    {
    Get-Process
    Get-Service

    Sequence
    {
        $Hotfix = Get-Content 'D:\HotFixes\Required.txt'
        Foreach ($h in $Hotfix) {'D:\Scripts\Verify-Hotfix' -Hotfix $h}
        }
    }
}
```

## <a name="see-also"></a>참고 항목

[about_ForEach](../../Microsoft.PowerShell.Core/About/about_Foreach.md)

[about_ForEach-병렬](about_ForEach-Parallel.md)

[about_Language_Keywords](../../Microsoft.PowerShell.Core/About/about_Language_Keywords.md)

[about_Parallel](about_Parallel.md)

[about_Workflows](about_Workflows.md)

[Windows PowerShell 스크립트를 사용하여 워크플로 만들기](/previous-versions/powershell/scripting/developer/workflow/creating-a-workflow-by-using-a-windows-powershell-script)
