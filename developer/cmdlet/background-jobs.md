---
title: 백그라운드 작업 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a0ef5ac9-8254-4832-ace8-84b356c10f08
caps.latest.revision: 13
ms.openlocfilehash: 9aff23647e55e8c9c41c54e5b62cedc15fb28a2d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857169"
---
# <a name="background-jobs"></a>백그라운드 작업

내부적으로 또는 Windows PowerShell Cmdlet이 해당 작업을 수행할 수 있습니다*백그라운드 작업*합니다. Cmdlet을 백그라운드 작업으로 실행 되 면 작업 cmdlet을 사용 하는 파이프라인 스레드에서 별도 자체 스레드에서 비동기적으로 수행 됩니다. 사용자 관점에서 cmdlet을 백그라운드 작업으로 실행 될 때 명령 프롬프트 바로 반환 작업은 완료 하는 데는 오랜된 시간 및 작업이 실행 되는 동안은 사용자가 중단 없이 계속 하는 경우에 합니다.

## <a name="background-jobs-child-jobs-and-the-job-repository"></a>백그라운드 작업, 자식 작업 및 작업 저장소

백그라운드 작업을 지 원하는 cmdlet에서 반환 되는 작업 개체는 작업을 정의 합니다. (합니다 [Start-job](/powershell/module/Microsoft.PowerShell.Core/Start-Job) cmdlet도 작업 개체를 반환 합니다.) 작업, 작업, 상태 정보 및 자식 작업을 지정 하는 데 사용 되는 식별자의 이름은이 정의에 포함 됩니다. 작업 작업은 수행 하지 않습니다. 각 백그라운드 작업에는 하나 이상의 자식 작업이 자식 작업 실제 작업을 수행 하기 때문에 백그라운드 작업으로 수행 됩니다 있도록 cmdlet을 실행 하면 cmdlet을 추가 해야 작업 및 자식 작업 이라고 공용 리포지토리에 *작업 리포지토리가*합니다.
백그라운드 작업을 지 원하는 cmdlet에서 반환 되는 작업 개체는 작업을 정의 합니다. (합니다 [Start-job](/powershell/module/Microsoft.PowerShell.Core/Start-Job) cmdlet도 작업 개체를 반환 합니다.) 작업, 작업, 상태 정보 및 자식 작업을 지정 하는 데 사용 되는 식별자의 이름은이 정의에 포함 됩니다. 작업 작업은 수행 하지 않습니다. 각 백그라운드 작업에는 하나 이상의 자식 작업이 자식 작업 실제 작업을 수행 하기 때문에 백그라운드 작업으로 수행 됩니다 있도록 cmdlet을 실행 하면 cmdlet을 추가 해야 작업 및 자식 작업 이라고 공용 리포지토리에 *작업 리포지토리가*합니다.

명령줄에서 백그라운드 작업은 처리 하는 방법에 대 한 자세한 내용은 다음을 참조 하세요.

- [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs)

- [about_Job_Details](/powershell/module/microsoft.powershell.core/about/about_job_details)

- [about_Remote_Jobs](/powershell/module/microsoft.powershell.core/about/about_remote_jobs)

## <a name="writing-a-cmdlet-that-runs-as-a-background-job"></a>백그라운드 작업으로 실행 되는 Cmdlet를 작성 합니다.

백그라운드 작업으로 실행할 수 있는 cmdlet를 작성 하려면 다음 작업을 완료 해야 합니다.

- 정의 `asJob` 스위치 매개 변수를 cmdlet을 백그라운드 작업으로 실행할지 여부를 결정할 수 있습니다.

- 파생 되는 개체를 만들 합니다 [System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) 클래스입니다. 이 개체는 사용자 지정 작업 개체 또는 같은 Windows PowerShell에서 제공 하는 작업 개체 수를 [System.Management.Automation.Pseventjob](/dotnet/api/System.Management.Automation.PSEventJob) 개체입니다.

- 추가 레코드 처리 메서드에서 `if` cmdlet을 백그라운드 작업으로 실행할지 여부를 검색 하는 문.

- 사용자 지정 작업 개체에 대 한 작업 클래스를 구현 합니다.

- Cmdlet을 백그라운드 작업으로 실행 되는 여부에 따라 적절 한 개체를 반환 합니다.

코드 예제를 참조 하세요 [지원 작업 방법](./how-to-support-jobs.md)합니다.

## <a name="background-job-related-apis"></a>백그라운드 작업 관련 Api

다음 Api는 Windows PowerShell 백그라운드 작업을 관리 하 여 제공 됩니다.

[System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) 사용자 지정 작업 개체를 파생 합니다. 이 클래스는 추상 클래스입니다.

[System.Management.Automation.Jobrepository](/dotnet/api/System.Management.Automation.JobRepository) 관리 하 고 현재 활성 상태인 백그라운드 작업에 대 한 정보를 제공 합니다.

[System.Management.Automation.Jobstate](/dotnet/api/System.Management.Automation.JobState) 백그라운드 작업의 상태를 정의 합니다. 상태 시작, 실행 및 중지를 포함 합니다.

[System.Management.Automation.Jobstateinfo](/dotnet/api/System.Management.Automation.JobStateInfo) 백그라운드 작업의 상태에 대 한 정보를 제공 하 고 마지막 상태를 변경 하는 경우 오류가 작업의 현재 상태가 된 이유를 인해 발생 합니다.

[System.Management.Automation.Jobstateeventargs](/dotnet/api/System.Management.Automation.JobStateEventArgs) 백그라운드 작업 상태가 변경 될 때 발생 하는 이벤트에 대 한 인수를 제공 합니다.

## <a name="windows-powershell-job-cmdlets"></a>Windows PowerShell 작업 Cmdlet

다음 cmdlet은 Windows PowerShell 백그라운드 작업을 관리 하 여 제공 됩니다.

[Get-Job](/powershell/module/Microsoft.PowerShell.Core/Get-Job)

현재 세션에서 실행되는 Windows PowerShell 백그라운드 작업을 가져옵니다.

[Receive-Job](/powershell/module/Microsoft.PowerShell.Core/Receive-Job)

현재 세션의 Windows PowerShell 백그라운드 작업에 대한 결과를 가져옵니다.

[Remove-Job](/powershell/module/Microsoft.PowerShell.Core/Remove-Job)

Windows PowerShell 백그라운드 작업을 삭제합니다.

[Start-Job](/powershell/module/Microsoft.PowerShell.Core/Start-Job)

Windows PowerShell 백그라운드 작업을 시작합니다.

[Stop-Job](/powershell/module/Microsoft.PowerShell.Core/Stop-Job)

Windows PowerShell 백그라운드 작업을 중지합니다.

[Wait-Job](/powershell/module/Microsoft.PowerShell.Core/Wait-Job)

세션에서 실행 중인 Windows PowerShell 백그라운드 작업 중 하나 또는 모두가 완료될 때까지 명령 프롬프트를 표시하지 않습니다.

## <a name="see-also"></a>참고 항목

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)
