---
ms.date: 08/15/2019
keywords: dsc,powershell,configuration,setup
title: Windows용 DSC(필요한 상태 구성) 시작
ms.openlocfilehash: 2add2c936e60c0c9446bf4b398fbf7b4bd6407f7
ms.sourcegitcommit: 1b88c280dd0799f225242608f0cbdab485357633
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75416170"
---
# <a name="get-started-with-desired-state-configuration-dsc-for-windows"></a>Windows용 DSC(필요한 상태 구성) 시작

이 항목에서는 Windows용 PowerShell DSC(필요한 상태 구성) 사용 방법에 대해 설명합니다.
DSC에 대한 일반적인 내용은 [Windows PowerShell 필요한 상태 구성 시작](../overview/overview.md)을 참조하세요.

## <a name="supported-windows-operation-system-versions"></a>지원되는 Windows 운영 체제 버전

지원되는 버전은 다음과 같습니다.

- Windows Server 2019
- Windows Server 2016
- Windows Server 2012R2
- Windows Server 2012
- Windows Server 2008 R2 SP1
- 윈도우 10
- Windows 8.1
- Windows 7

[Microsoft Hyper-V Server](/windows-server/virtualization/hyper-v/hyper-v-server-2016) 독립 실행형 제품 SKU는 필요한 상태 구성의 구현을 포함하지 않으므로 PowerShell DSC 또는 Azure Automation 상태 구성으로 관리할 수 없습니다.

## <a name="installing-dsc"></a>DSC 설치

PowerShell 필요한 상태 구성은 Windows에 포함되어 있으며 Windows Management Framework를 통해 업데이트됩니다. 최신 버전은 [Windows Management Framework 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616)입니다.

> [!NOTE]
> DSC를 사용하여 머신을 관리하기 위해 Windows Server 기능 ' DSC-서비스'를 사용하도록 설정할 필요는 없습니다.
> 이 기능은 Windows 끌어오기 서버 인스턴스를 빌드할 때만 필요합니다.

## <a name="using-dsc-for-windows"></a>Windows용 DSC 사용

다음 섹션에서는 Windows 컴퓨터에서 DSC 구성을 만들고 실행하는 방법을 설명합니다.

### <a name="creating-a-configuration-mof-document"></a>구성 MOF 문서 만들기

Windows PowerShell `Configuration` 키워드는 구성을 만드는 데 사용됩니다.
다음 단계에서는 Windows PowerShell을 사용한 구성 문서 작성에 대해 설명합니다.

#### <a name="define-a-configuration-and-generate-the-configuration-document"></a>구성을 정의하고 구성 문서를 생성합니다.

```powershell
Configuration EnvironmentVariable_Path
{
    param ()

    Import-DscResource -ModuleName 'PSDscResources'

    Node localhost
    {
        Environment CreatePathEnvironmentVariable
        {
            Name = 'TestPathEnvironmentVariable'
            Value = 'TestValue'
            Ensure = 'Present'
            Path = $true
            Target = @('Process', 'Machine')
        }
    }
}

EnvironmentVariable_Path -OutputPath:"C:\EnvironmentVariable_Path"
```

#### <a name="install-a-module-containing-dsc-resources"></a>DSC 리소스를 포함하는 모듈 설치

Windows PowerShell 필요한 상태 구성에는 DSC 리소스를 포함하는 기본 제공 모듈이 포함되어 있습니다.
PowerShellGet cmdlet을 사용하는 PowerShell 갤러리 같은 외부 소스에서 모듈을 로드할 수도 있습니다.

```PowerShell
Install-Module 'PSDscResources' -Verbose
```

#### <a name="apply-the-configuration-to-the-machine"></a>머신에 구성 적용

> [!NOTE]
> DSC를 실행할 수 있도록 하려면 `localhost` 구성을 실행 하는 경우에도 PowerShell 원격 명령을 받도록 Windows를 구성 해야 합니다. 환경을 올바르게 구성하려면 관리자 권한 PowerShell 터미널에서 `Set-WsManQuickConfig -Force`를 실행하면 됩니다.

구성 문서(MOF 파일)를 [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet을 사용하여 머신에 적용할 수 있습니다.

```powershell
Start-DscConfiguration -Path 'C:\EnvironmentVariable_Path' -Wait -Verbose
```

#### <a name="get-the-current-state-of-the-configuration"></a>구성의 현재 상태 가져오기

[Get-DscConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) cmdlet은 머신의 현재 상태를 쿼리하고 구성에 대한 현재 값을 반환합니다.

```powershell
Get-DscConfiguration
```

[Get-DscLocalConfigurationManager](/powershell/module/psdesiredstateconfiguration/get-dscLocalConfigurationManager) cmdlet은 머신에 적용된 현재 메타 구성을 반환합니다.

```powershell
Get-DscLocalConfigurationManager
```

#### <a name="remove-the-current-configuration-from-a-machine"></a>머신에서 현재 구성 제거

[Remove-DscConfigurationDocument](/powershell/module/psdesiredstateconfiguration/remove-dscconfigurationdocument)

```powershell
Remove-DscConfigurationDocument -Stage Current -Verbose
```

#### <a name="configure-settings-in-local-configuration-manager"></a>로컬 구성 관리자에서 설정 구성

[Set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) cmdlet을 사용하여 메타 구성 MOF 파일을 머신에 적용합니다.
메타 구성 MOF의 경로가 필요합니다.

```powershell
Set-DSCLocalConfigurationManager -Path 'c:\metaconfig\localhost.meta.mof' -Verbose
```

## <a name="windows-powershell-desired-state-configuration-log-files"></a>Windows PowerShell 필요한 상태 구성 로그 파일

DSC에 대한 로그는 경로 `Microsoft-Windows-Dsc/Operational`에 있는 Windows 이벤트 로그에 기록됩니다.
디버깅 목적을 위한 추가 로그는 [DSC 이벤트 로그 위치](/powershell/scripting/dsc/troubleshooting/troubleshooting#where-are-dsc-event-logs)의 단계에 따라 사용하도록 설정할 수 있습니다.
