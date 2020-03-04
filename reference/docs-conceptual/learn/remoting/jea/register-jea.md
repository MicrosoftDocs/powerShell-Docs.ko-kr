---
ms.date: 07/10/2019
keywords: jea,powershell,security
title: JEA 구성 등록
ms.openlocfilehash: 7cc67e891bc14dd667c97e9a8b550b33b4c2b874
ms.sourcegitcommit: 0a3f9945d52e963e9cba2538ffb33e42156e1395
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/27/2020
ms.locfileid: "77706209"
---
# <a name="registering-jea-configurations"></a>JEA 구성 등록

[역할 기능](role-capabilities.md) 및 [세션 구성 파일](session-configurations.md)을 만든 후 마지막 단계는 JEA 엔드포인트를 등록하는 것입니다. 시스템에 JEA 엔드포인트를 등록하면 사용자 및 자동화 엔진에서 엔드포인트를 사용할 수 있게 됩니다.

## <a name="single-machine-configuration"></a>단일 컴퓨터 구성

소규모 환경에서는 [Register-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/register-pssessionconfiguration) cmdlet을 사용해 세션 구성 파일을 등록하는 방법으로 JEA를 배포할 수 있습니다.

시작하기 전에 다음과 같은 필수 조건을 충족했는지 확인하세요.

- 하나 이상의 역할이 생성되어 PowerShell 모듈의 **RoleCapabilities** 폴더에 배치되었습니다.
- 세션 구성 파일을 만들고 테스트했습니다.
- JEA 구성을 등록하는 사용자에게 시스템에 대한 관리자 권한이 있습니다.
- JEA 엔드포인트의 이름을 선택했습니다.

사용자가 JEA를 사용하여 시스템에 연결할 때 JEA 엔드포인트의 이름이 필요합니다. [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) cmdlet은 시스템의 엔드포인트 이름을 나열합니다. `microsoft`로 시작하는 엔드포인트는 일반적으로 Windows와 함께 제공됩니다. `microsoft.powershell` 엔드포인트는 원격 PowerShell 엔드포인트에 연결할 때 사용되는 기본 엔드포인트입니다.

```powershell
Get-PSSessionConfiguration | Select-Object Name
```

```Output
Name
----
microsoft.powershell
microsoft.powershell.workflow
microsoft.powershell32
```

다음 명령을 실행하여 엔드포인트를 등록합니다.

```powershell
Register-PSSessionConfiguration -Path .\MyJEAConfig.pssc -Name 'JEAMaintenance' -Force
```

> [!WARNING]
> 이전 명령은 시스템에서 WinRM 서비스를 다시 시작합니다. 그러면 모든 PowerShell 원격 세션과 진행 중인 모든 DSC 구성이 종료됩니다. 비즈니스 운영이 중단되지 않게 하려면 명령을 실행하기 전에 프로덕션 머신을 오프라인 상태로 전환하는 것이 좋습니다.

등록 후 [JEA를 사용](using-jea.md)할 준비가 되었습니다. 언제든지 세션 구성 파일을 삭제할 수 있습니다. 구성 파일은 엔드포인트 등록 후에 사용되지 않습니다.

## <a name="multi-machine-configuration-with-dsc"></a>DSC를 사용한 다중 컴퓨터 구성

JEA를 여러 머신에 배포할 때 가장 간단한 배포 모델은 JEA [DSC(필요한 상태 구성)](../../../dsc/overview/overview.md) 리소스를 사용하여 각 머신에 신속하고 일관되게 JEA를 배포하는 것입니다.

DSC를 사용하여 JEA를 배포하려면 다음 필수 조건이 충족되는지 확인합니다.

- 하나 이상의 역할 기능을 작성하여 PowerShell 모듈에 추가했습니다.
- 역할을 포함하는 PowerShell 모듈을 각 컴퓨터에서 액세스할 수 있는 (읽기 전용) 파일 공유에 저장했습니다.
- 세션 구성에 대한 설정을 결정했습니다. JEA DSC 리소스를 사용할 때 세션 구성 파일을 만들 필요가 없습니다.
- 각 머신에서 관리 작업을 허용하거나 해당 머신을 관리하는 데 사용되는 DSC 끌어오기 서버에 액세스할 수 있는 자격 증명이 있습니다.
- [JEA DSC 리소스](https://github.com/powershell/JEA/tree/master/DSC%20Resource)를 다운로드했습니다.

대상 머신 또는 풀 서버에 JEA 엔드포인트에 대한 DSC 구성을 만듭니다. 이 구성에서는 **JustEnoughAdministration** DSC 리소스가 세션 구성 파일을 정의하고 **File** 리소스가 파일 공유에서 역할 기능을 복사합니다.

DSC 리소스를 사용하여 다음 속성을 구성할 수 있습니다.

- 역할 정의
- 가상 계정 그룹
- 그룹 관리 서비스 계정 이름
- 기록 디렉터리
- 사용자 드라이브
- 조건부 액세스 규칙
- JEA 세션에 대한 시작 스크립트

DSC 구성에서 이러한 각 속성에 대한 구문은 PowerShell 세션 구성 파일과 일치합니다.

다음은 일반 서버 유지 관리 모듈에 대한 샘플 DSC 구성입니다. 역할 기능을 포함하는 유효한 PowerShell 모듈이 `\\myfileshare\JEA` 파일 공유에 있다고 가정합니다.

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

그런 다음, [로컬 구성 관리자](/powershell/scripting/dsc/managing-nodes/metaConfig)를 직접 호출하거나 [끌어오기 서버 구성](/powershell/scripting/dsc/pull-server/pullServer)을 업데이트하여 시스템에 이 구성을 적용합니다.

DSC 리소스를 사용하여 기본 **Microsoft.PowerShell** 엔드포인트를 바꿀 수도 있습니다. 바꾸면 리소스가 **Microsoft.PowerShell.Restricted**라는 백업 엔드포인트를 자동으로 등록합니다. 백업 엔드포인트에는 원격 관리 사용자 및 로컬 Administrators 그룹 멤버가 액세스할 수 있도록 하는 기본 WinRM ACL이 있습니다.

## <a name="unregistering-jea-configurations"></a>JEA 구성 등록 취소

[Unregister-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/Unregister-PSSessionConfiguration) cmdlet이 JEA 엔드포인트를 제거합니다. JEA 엔드포인트를 등록 취소하면 새 사용자가 시스템에서 새 JEA 세션을 만들지 못합니다. 같은 엔드포인트 이름을 사용하여 업데이트된 세션 구성 파일을 다시 등록하는 방법으로 JEA 구성을 업데이트할 수도 있습니다.

```powershell
# Unregister the JEA endpoint called "ContosoMaintenance"
Unregister-PSSessionConfiguration -Name 'ContosoMaintenance' -Force
```

> [!WARNING]
> JEA 엔드포인트를 등록 취소하면 WinRM 서비스가 다시 시작됩니다. 그러면 다른 PowerShell 세션, WMI 호출 및 일부 관리 도구를 비롯한 진행 중인 대부분의 원격 관리 작업이 중단됩니다. 계획된 유지 관리 기간에는 PowerShell 엔드포인트만 등록 취소하세요.

## <a name="next-steps"></a>다음 단계

[JEA 엔드포인트 테스트](using-jea.md)
