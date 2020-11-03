---
description: 워크플로에서 작업을 병렬로 실행 하는 Parallel 키워드에 대해 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflow/about/about_parallel?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Parallel
ms.openlocfilehash: 402e93672bbea4ec9b6bfda8d608f266f6c40a21
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93221890"
---
# <a name="about-parallel"></a>병렬 정보

## <a name="short-description"></a>간단한 설명
워크플로에서 작업을 병렬로 실행 하는 Parallel 키워드에 대해 설명 합니다.

## <a name="long-description"></a>자세한 설명

Parallel 키워드는 워크플로 작업을 병렬로 실행 합니다. 이 키워드는 Windows PowerShell 워크플로에서만 유효 합니다.

### <a name="syntax"></a>SYNTAX

```
workflow <Verb-Noun>
{
     Parallel
     {
          [<Activity>]
          [<Activity>]
        ...
     }
 }
```

## <a name="detailed-description"></a>자세한 설명

Parallel 스크립트 블록의 명령은 동시에 실행될 수 있습니다. 실행 순서가 정해져 있지 않습니다.

예를 들어 다음 워크플로에는 컴퓨터의 프로세스 및 서비스를 가져오는 활동을 실행하는 Parallel 스크립트 블록이 포함되어 있습니다. Get-Process 및 Get-Service 명령은 서로 독립적 이므로 순서에 관계 없이 동시에 실행할 수 있습니다.

```powershell
workflow Test-Workflow
{
    Parallel
    {
         Get-Process
         Get-Service
    }
}
```

명령을 병렬로 실행 하는 것은 매우 효율적 이며 워크플로를 크게 완료 하는 데 걸리는 시간을 줄입니다.

병렬 스크립트 블록에서 선택 된 명령을 순차적으로 실행 하려면 Sequence 키워드를 사용 합니다. 자세한 내용은 about_Sequence를 참조 하세요.

컬렉션의 항목에서 Parallel 스크립트 블록을 실행 하려면 ForEach 또는 ForEach-Parallel 키워드를 사용 합니다.

## <a name="see-also"></a>참고 항목

["스크립트 워크플로 작성"](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj574157(v=ws.11))

[about_ForEach](../../Microsoft.PowerShell.Core/About/about_Foreach.md)

[about_ForEach-병렬](about_ForEach-Parallel.md)

[about_Language_Keywords](../../Microsoft.PowerShell.Core/About/about_Language_Keywords.md)

[about_Sequence](about_Sequence.md)

[about_Workflows](about_workflows.md)
