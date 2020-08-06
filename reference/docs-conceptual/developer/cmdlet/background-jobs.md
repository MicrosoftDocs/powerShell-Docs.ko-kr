---
title: 백그라운드 작업 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 2a1297b8dfe087474564078cca2a5a0526ed0f36
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774850"
---
# <a name="background-jobs"></a>백그라운드 작업

Cmdlet은 내부적으로 또는 Windows PowerShell*백그라운드 작업*으로 작업을 수행할 수 있습니다. Cmdlet이 백그라운드 작업으로 실행 되는 경우 cmdlet에서 사용 하는 파이프라인 스레드와는 별도의 스레드에서 비동기적으로 작업이 수행 됩니다. 사용자 관점에서 cmdlet이 백그라운드 작업으로 실행 되는 경우 작업을 완료 하는 데 시간이 오래 걸리고 사용자가 작업을 실행 하는 동안 중단 없이 계속할 수 있는 경우에도 명령 프롬프트가 즉시 반환 됩니다.

## <a name="background-jobs-child-jobs-and-the-job-repository"></a>백그라운드 작업, 자식 작업 및 작업 리포지토리

백그라운드 작업을 지 원하는 cmdlet에 의해 반환 되는 작업 개체는 작업을 정의 합니다. [시작-작업](/powershell/module/Microsoft.PowerShell.Core/Start-Job) cmdlet은 작업 개체를 반환 하기도 합니다. 작업 이름, 작업을 지정 하는 데 사용 되는 식별자, 상태 정보 및 자식 작업이이 정의에 포함 됩니다. 작업은 작업을 수행 하지 않습니다. 자식 작업에서 실제 작업을 수행 하기 때문에 각 백그라운드 작업에는 자식 작업이 하나 이상 있습니다. 작업을 백그라운드 작업으로 수행 하기 위해 cmdlet을 실행 하는 경우 cmdlet은 작업 및 자식 작업을 *작업 리포지토리*라고 하는 공용 리포지토리에 추가 해야 합니다.

명령줄에서 백그라운드 작업을 처리 하는 방법에 대 한 자세한 내용은 다음을 참조 하세요.

- [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs)

- [about_Job_Details](/powershell/module/microsoft.powershell.core/about/about_job_details)

- [about_Remote_Jobs](/powershell/module/microsoft.powershell.core/about/about_remote_jobs)

## <a name="writing-a-cmdlet-that-runs-as-a-background-job"></a>백그라운드 작업으로 실행 되는 Cmdlet 작성

백그라운드 작업으로 실행할 수 있는 cmdlet을 작성 하려면 다음 작업을 완료 해야 합니다.

- `asJob`사용자가 cmdlet을 백그라운드 작업으로 실행할지 여부를 결정할 수 있도록 switch 매개 변수를 정의 합니다.

- [System.object](/dotnet/api/System.Management.Automation.Job) 클래스에서 파생 되는 개체를 만듭니다. 이 개체는 사용자 지정 작업 개체 이거나 Windows PowerShell에서 제공 하는 작업 개체 (예: [Pseventjob](/dotnet/api/System.Management.Automation.PSEventJob) 개체) 일 수 있습니다.

- 레코드 처리 방법에서 `if` cmdlet을 백그라운드 작업으로 실행할지 여부를 검색 하는 문을 추가 합니다.

- 사용자 지정 작업 개체의 경우 작업 클래스를 구현 합니다.

- Cmdlet이 백그라운드 작업으로 실행 되는지 여부에 따라 적절 한 개체를 반환 합니다.

코드 예제는 [작업을 지 원하는 방법](./how-to-support-jobs.md)을 참조 하세요.

## <a name="background-job-related-apis"></a>백그라운드 작업 관련 Api

백그라운드 작업을 관리 하기 위해 Windows PowerShell에서 제공 하는 Api는 다음과 같습니다.

[System.object](/dotnet/api/System.Management.Automation.Job) 는 사용자 지정 작업 개체를 파생 합니다. 이 클래스는 추상 클래스입니다.

[System.object 리포지토리](/dotnet/api/System.Management.Automation.JobRepository) 는 현재 활성 백그라운드 작업에 대 한 정보를 관리 하 고 제공 합니다.

[Jobstate](/dotnet/api/System.Management.Automation.JobState) 는 백그라운드 작업의 상태를 정의 합니다. 상태에는 시작 됨, 실행 중, 중지 됨이 포함 됩니다.

[System.object](/dotnet/api/System.Management.Automation.JobStateInfo) 는 백그라운드 작업의 상태에 대 한 정보를 제공 하 고, 마지막 상태 변경이 오류로 인해 발생 한 경우, 작업이 현재 상태로 들어간 이유를 제공 합니다.

[System.object](/dotnet/api/System.Management.Automation.JobStateEventArgs) 는 백그라운드 작업의 상태가 변경 될 때 발생 하는 이벤트에 대 한 인수를 제공 합니다.

## <a name="windows-powershell-job-cmdlets"></a>Windows PowerShell 작업 Cmdlet

다음 cmdlet은 Windows PowerShell에서 백그라운드 작업을 관리 하는 데 제공 됩니다.

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

[Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)](./writing-a-windows-powershell-cmdlet.md)
