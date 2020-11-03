---
description: '`ForEach -Parallel`Windows PowerShell 워크플로의 언어 구문에 대해 설명 합니다.'
keywords: powershell,cmdlet
Locale: en-US
ms.date: 07/10/2019
online version: https://docs.microsoft.com/powershell/module/psworkflow/about/about_foreach-parallel?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: 병렬 about_Foreach
ms.openlocfilehash: 1012b45396b65d424dacac067c2af8d3b6823f92
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93221906"
---
# <a name="about-foreach-parallel"></a>Foreach-Parallel 정보

## <a name="short-description"></a>간단한 설명
`ForEach -Parallel`Windows PowerShell 워크플로의 언어 구문에 대해 설명 합니다.

## <a name="long-description"></a>자세한 설명

키워드의 **Parallel** 매개 변수는 `ForEach` `ForEach` 지정 된 컬렉션의 각 항목에 대해 한 번씩 스크립트 블록의 명령을 실행 합니다.

디스크 컬렉션의 디스크와 같은 컬렉션의 항목은 병렬로 처리 됩니다. 스크립트 블록의 명령은 컬렉션의 각 항목에 대해 순차적으로 실행 됩니다.

`ForEach -Parallel` 는 Windows PowerShell 워크플로에서만 유효 합니다.

### <a name="syntax"></a>SYNTAX

```
ForEach -Parallel ($<item> in $<collection>)
{
    [<Activity1>]
    [<Activity2>]
    ...
}
```

### <a name="detailed-description"></a>자세한 설명

Windows PowerShell의 ForEach 문과 마찬가지로, 컬렉션을 포함 하는 변수는 `$<collection>` 문 앞에 정의 되어야 `ForEach -Parallel` 하지만 현재 항목을 나타내는 변수는 `$<item>` 문에서 정의 됩니다 `ForEach -Parallel` .

`ForEach -Parallel`구문은 `ForEach` 키워드와 **Parallel** 매개 변수와 다릅니다. `ForEach`키워드는 컬렉션의 항목을 순서 대로 처리 합니다. **Parallel** 매개 변수는 스크립트 블록에서 명령을 병렬로 실행 합니다. 스크립트 블록에서 Parallel 스크립트 블록을 묶을 수 있습니다 `ForEach -Parallel` .

**PSComputerName** 워크플로 일반 매개 변수에서 지정한 것과 같은 워크플로의 대상 컴퓨터는 항상 병렬로 처리 됩니다.
`ForEach -Parallel`이 목적을 위해 키워드를 지정할 필요가 없습니다.

### <a name="examples"></a>예제

다음 워크플로에는 `ForEach -Parallel` 활동에서 가져오는 디스크를 처리 하는 문이 포함 되어 있습니다 `Get-Disk` . 스크립트 블록의 명령은 `ForEach -Parallel` 순차적으로 실행 되지만 디스크에서 병렬로 실행 됩니다. 디스크는 순서에 관계 없이 동시에 처리 될 수 있습니다.

```powershell
workflow Test-Workflow
{
    $Disks = Get-Disk

    # The disks are processed in parallel.
    ForEach -Parallel ($Disk in $Disks)
    {
        # The commands run sequentially on each disk.
        $DiskPath = $Disk.Path
        $Disk | Initialize-Disk
        Set-Disk -Path $DiskPath
    }
}

workflow Test-Workflow
{
    #Run commands in parallel.
    Parallel
    {
        Get-Process
        Get-Service
    }

   $Disks = Get-Disk

   # The disks are processed in parallel.
   ForEach -Parallel ($Disk in $Disks)
   {
       # The commands run in parallel on each disk.
       Parallel
       {
           Initialize-Disk
           InlineScript {.\Get-DiskInventory}
       }
   }
}
```

## <a name="see-also"></a>참고 항목

[Writing a Script Workflow](/previous-versions/powershell/scripting/developer/workflow/creating-a-workflow-by-using-a-windows-powershell-script)

[about_ForEach](../../Microsoft.PowerShell.Core/About/about_ForEach.md)

[about_Language_Keywords](../../Microsoft.PowerShell.Core/About/about_Language_Keywords.md)

[about_Parallel](about_Parallel.md)

[about_Workflows](about_Workflows.md)
