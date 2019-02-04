---
ms.date: 06/12/2017
keywords: jea,powershell,security
title: JEA 구성 등록
ms.openlocfilehash: 160aa95283da57a10aad5fdd4043adb1354a5db5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55683153"
---
# <a name="registering-jea-configurations"></a>JEA 구성 등록

> 적용 대상: Windows Powershell 5.0

[역할 기능](role-capabilities.md) 및 [세션 구성 파일](session-configurations.md)을 만든 후 JEA를 사용하기 위한 마지막 단계는 JEA 엔드포인트를 등록하는 것입니다.
시스템에 JEA 엔드포인트를 등록하면 사용자 및 자동화 엔진에서 엔드포인트를 사용할 수 있게 됩니다.

## <a name="single-machine-configuration"></a>단일 컴퓨터 구성

소규모 환경에서는 [Register-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/register-pssessionconfiguration) cmdlet을 사용해 세션 구성 파일을 등록하는 방법으로 JEA를 배포할 수 있습니다.

시작하기 전에 다음과 같은 필수 조건을 충족했는지 확인하세요.
- 하나 이상의 역할을 만들어 유효한 PowerShell 모듈의 'RoleCapabilities' 폴더에 배치했습니다.
- 세션 구성 파일을 만들고 테스트했습니다.
- JEA 구성을 등록하는 사용자에게 시스템에 대한 관리자 권한이 있습니다.

또한 JEA 엔드포인트의 이름을 선택해야 합니다.
사용자가 JEA를 사용하여 시스템에 연결하려고 할 경우 JEA 엔드포인트의 이름이 필요합니다.
[Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet을 사용하여 시스템에 있는 기존 엔드포인트의 이름을 확인할 수 있습니다.
'microsoft'로 시작하는 엔드포인트는 일반적으로 Windows와 함께 제공됩니다.
'microsoft.powershell' 엔드포인트는 원격 PowerShell 엔드포인트에 연결할 때 사용되는 기본 엔드포인트입니다.

```powershell
PS C:\> Get-PSSessionConfiguration | Select-Object Name

Name
----
microsoft.powershell
microsoft.powershell.workflow
microsoft.powershell32
```

JEA 엔드포인트에 대한 적절한 이름을 결정했으면 다음 명령을 실행하여 엔드포인트를 등록합니다.

```powershell
Register-PSSessionConfiguration -Path .\MyJEAConfig.pssc -Name 'JEAMaintenance' -Force
```

> [!WARNING]
> 위의 명령은 시스템에서 WinRM 서비스를 다시 시작합니다.
> 그러면 진행 중인 모든 DSC 구성뿐만 아니라 모든 PowerShell 원격 세션이 종료됩니다.
> 비즈니스 운영이 중단되지 않게 하려면 명령을 실행하기 전에 모든 프로덕션 컴퓨터를 오프라인 상태로 전환하는 것이 좋습니다.

등록에 성공하면 [JEA를 사용](using-jea.md)할 준비가 된 것입니다.
엔드포인트를 등록한 후에는 세션 구성 파일이 사용되지 않으므로 언제든지 삭제할 수 있습니다.

## <a name="multi-machine-configuration-with-dsc"></a>DSC를 사용한 다중 컴퓨터 구성

JEA를 여러 컴퓨터에 배포하는 경우 가장 간단한 배포 모델은 JEA [필요한 상태 구성](https://msdn.microsoft.com/powershell/dsc/overview) 리소스를 사용하여 각 컴퓨터에 신속하고 일관되게 JEA를 배포하는 것입니다.

DSC를 사용하여 JEA를 배포하려면 다음 필수 조건을 충족해야 합니다.
- 하나 이상의 역할 기능을 작성하여 유효한 PowerShell 모듈에 추가했습니다.
- 역할을 포함하는 PowerShell 모듈을 각 컴퓨터에서 액세스할 수 있는 (읽기 전용) 파일 공유에 저장했습니다.
- 세션 구성에 대한 설정을 결정했습니다. JEA DSC 리소스를 사용하는 경우 세션 구성 파일을 만들 필요가 없습니다.
- 각 컴퓨터에서 관리 작업을 수행할 수 있는 자격 증명이 있거나, 컴퓨터를 관리하는 데 사용되는 DSC 끌어오기 서버에 대한 액세스 권한이 있습니다.
- [JEA DSC resource](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource)(JEA DSC 리소스)를 다운로드했습니다.

대상 컴퓨터(또는 끌어오기 서버를 사용하는 경우 끌어오기 서버)에서 JEA 엔드포인트에 대한 DSC 구성을 만듭니다.
이 구성에서는 JustEnoughAdministration DSC 리소스를 사용하여 세션 구성 파일을 설정하고 File 리소스를 사용하여 파일 공유에서 역할 기능을 복사합니다.

DSC 리소스를 사용하여 다음 속성을 구성할 수 있습니다.
- 역할 정의
- 가상 계정 그룹
- 그룹 관리 서비스 계정 이름
- 기록 디렉터리
- 사용자 드라이브
- 조건부 액세스 규칙
- JEA 세션에 대한 시작 스크립트

DSC 구성에서 이러한 각 속성에 대한 구문은 PowerShell 세션 구성 파일과 일치합니다.

다음은 일반 서버 유지 관리 모듈에 대한 샘플 DSC 구성입니다.

여기서는 'RoleCapabilities' 하위 폴더의 역할 기능을 포함하는 유효한 PowerShell 모듈이 '\\\\myfileshare\\JEA' 파일 공유에 있다고 가정합니다.


```powershell
Configuration JEAMaintenance
{
    Import-DscResource -Module JustEnoughAdministration, PSDesiredStateConfiguration

    File MaintenanceModule
    {
        SourcePath = "\\myfileshare\JEA\ContosoMaintenance"
        DestinationPath = "C:\Program Files\WindowsPowerShell\Modules\ContosoMaintenance"
        Checksum = "SHA-256"
        Ensure = "Present"
        Type = "Directory"
        Recurse = $true
    }

    JeaEndpoint JEAMaintenanceEndpoint
    {
        EndpointName = "JEAMaintenance"
        RoleDefinitions = "@{ 'CONTOSO\JEAMaintenanceAuditors' = @{ RoleCapabilities = 'GeneralServerMaintenance-Audit' }; 'CONTOSO\JEAMaintenanceAdmins' = @{ RoleCapabilities = 'GeneralServerMaintenance-Audit', 'GeneralServerMaintenance-Admin' } }"
        TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
        DependsOn = '[File]MaintenanceModule'
    }
}
```

그러면 [직접 로컬 구성 관리자를 호출](https://msdn.microsoft.com/powershell/dsc/metaconfig)하거나 [가져오기 서버 구성](https://msdn.microsoft.com/powershell/dsc/pullserver)을 업데이트하여 시스템에 이 구성을 적용할 수 있습니다.

DSC 리소스를 사용하여 기본 Microsoft.PowerShell 원격 엔드포인트를 바꿀 수도 있습니다.
이렇게 할 경우 리소스가 기본 WinRM ACL(Remote Management Users 및 로컬 Administrators 그룹 구성원이 다음에 언급된 엔드포인트에 액세스할 수 있음)인 "Microsoft.PowerShell.Restricted"라는 백업 비제한 엔드포인트를 자동으로 등록합니다.

## <a name="unregistering-jea-configurations"></a>JEA 구성 등록 취소

시스템에서 JEA 엔드포인트를 제거하려면 [Unregister-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Unregister-PSSessionConfiguration) cmdlet을 사용합니다.
JEA 엔드포인트를 등록 취소하면 새 사용자가 시스템에서 새 JEA 세션을 만들지 못합니다.
같은 엔드포인트 이름을 사용하여 업데이트된 세션 구성 파일을 다시 등록하는 방법으로 JEA 구성을 업데이트할 수도 있습니다.

```powershell
# Unregister the JEA endpoint called "ContosoMaintenance"
Unregister-PSSessionConfiguration -Name 'ContosoMaintenance' -Force
```

> [!WARNING]
> JEA 엔드포인트를 등록 취소하면 WinRM 서비스가 다시 시작됩니다.
> 그러면 다른 PowerShell 세션, WMI 호출 및 일부 관리 도구를 비롯한 진행 중인 대부분의 원격 관리 작업이 중단됩니다.
> 계획된 유지 관리 기간에는 PowerShell 엔드포인트만 등록 취소하세요.

## <a name="next-steps"></a>다음 단계

- [JEA 엔드포인트 테스트](using-jea.md)
