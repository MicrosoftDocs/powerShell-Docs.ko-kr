---
description: 활동이 표시 되는 `Suspend-Workflow` 워크플로를 일시 중단 하는 활동에 대해 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflow/about/about_suspend-workflow?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Suspend 워크플로
ms.openlocfilehash: cbe5386ae5aa4bd863079fde240ddf2ce5384727
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93221865"
---
# <a name="about-suspend-workflow"></a>Suspend-Workflow 정보

## <a name="short-description"></a>간단한 설명

활동이 표시 되는 `Suspend-Workflow` 워크플로를 일시 중단 하는 활동에 대해 설명 합니다.

## <a name="long-description"></a>자세한 설명입니다.

`Suspend-Workflow`활동은 워크플로 내에서 워크플로 처리를 일시적으로 중지 합니다. 일시 중단 하기 전에 Windows PowerShell 워크플로는 검사점을 사용 하 여 워크플로의 상태와 데이터가 유지 되 고 워크플로가 일시 중단 지점에서 다시 시작 될 수 있도록 합니다.

워크플로를 다시 시작 하려면 워크플로를 실행 하는 사용자가 cmdlet을 사용 합니다 `Resume-Job` . 워크플로 내에서 워크플로를 다시 시작할 수 없습니다.

## <a name="syntax"></a>구문

```
workflow <Verb-Noun>
{
    Suspend-Workflow
}
```

## <a name="detailed-description"></a>자세한 설명

는 `Suspend-Workflow` 워크플로를 일시적으로 중지 하 고 워크플로 작업을 나타내는 작업 개체를 반환 합니다. 작업으로 워크플로를 실행 하지 않은 경우에도 작업 개체가 반환 됩니다. 예를 들어 **AsJob** 워크플로 일반 매개 변수를 사용 합니다. 작업 상태가 **일시 중단** 됨입니다.

작업 cmdlet을 사용 하 여 일시 중단 된 워크플로 작업을 관리할 수 있습니다. 워크플로 작업을 다시 시작 하려면 cmdlet을 사용 합니다 `Resume-Job` .

워크플로 작업을 다시 시작 하면 해당 활동 뒤에 오는 명령에서 워크플로가 다시 시작 `Suspend-Workflow` 됩니다.

예를 들어 다음 워크플로에는 활동이 포함 되어 있습니다 `Suspend-Workflow` .
워크플로를 실행 하는 경우 작업을 실행 하 고 `Get-Date` 해당 출력 `$a` 을 변수에 저장 한 다음 워크플로를 일시 중단 하 고 일시 중단 된 워크플로를 나타내는 job 개체를 반환 합니다. 작업 유형은 **PSWorkflowJob** 입니다.

작업 cmdlet (예:)을 사용 `Get-Job` 하 여 워크플로 작업을 관리할 수 있습니다.

```powershell
Workflow Test-Suspend
{
    $a = Get-Date
    Suspend-Workflow
    (Get-Date)- $a
}

Test-Suspend
```

```Output
Id  Name  PSJobTypeName  State      HasMoreData  Location  Command
--  ----  -------------  -----      -----------  --------  -------
8   Job8  PSWorkflowJob  Suspended  True         localhost Test-Suspend
```

## <a name="resuming-a-workflow-job"></a>워크플로 작업 다시 시작

워크플로 작업을 다시 시작 하려면 cmdlet을 사용 합니다 `Resume-Job` . `Resume-Job` cmdlet은 아직 다시 시작할 수 없는 경우에도 워크플로 작업 개체를 즉시 반환합니다. 작업이 다시 시작 될 때까지 기다리려면 **wait** 매개 변수를 사용 하거나 cmdlet을 사용 `Get-Job` 하 여 현재 작업 개체를 가져옵니다.

```powershell
Resume-Job -Name Job8
```

```Output
Id  Name  PSJobTypeName  State    HasMoreData  Location  Command
--  ----  -------------  -----    -----------  --------  -------
8   Job8  PSWorkflowJob  Running  True         localhost Test-Suspend
```

```powershell
Get-Job -Name Job8
```

```Output
Id  Name  PSJobTypeName  State      HasMoreData  Location  Command
--  ----  -------------  -----      -----------  --------  -------
8   Job8  PSWorkflowJob  Completed  True         localhost Test-Suspend
```

## <a name="getting-the-output-of-a-workflow-job"></a>워크플로 작업의 출력 가져오기

워크플로 작업의 출력을 가져오려면 cmdlet을 사용 합니다 `Receive-Job` . 출력은 cmdlet을 수행한 명령에서 워크플로를 다시 시작 했음을 보여 줍니다 `Suspend-Workflow` . `$a`일시 중단 전에 채워진 변수의 값은 워크플로를 다시 시작할 때 사용할 수 있습니다.

```powershell
Get-Job -Name Job8 | Receive-Job
```

```Output
Days              : 0
Hours             : 0
Minutes           : 0
Seconds           : 19
Milliseconds      : 823
Ticks             : 198230041
TotalDays         : 0.000229432917824074
TotalHours        : 0.00550639002777778
TotalMinutes      : 0.330383401666667
TotalSeconds      : 19.8230041
TotalMilliseconds : 19823.0041
PSComputerName    : localhost
```

## <a name="see-also"></a>참고 항목

[about_Workflows](about_Workflows.md)

[about_WorkflowCommonParameters](about_WorkflowCommonParameters.md)

[Psworkflow](xref:PSWorkflow) cmdlet

[워크플로 가이드](/previous-versions/powershell/scripting/components/workflows-guide)

[Windows PowerShell 워크플로 작성](/previous-versions/powershell/scripting/developer/workflow/writing-a-windows-powershell-workflow)
