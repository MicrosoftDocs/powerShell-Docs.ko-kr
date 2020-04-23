---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: PowerShell 4.0에서 LCM 구성
ms.openlocfilehash: 747b15c483c79a7ecbb62214ef5a59f8dc137bd4
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2020
ms.locfileid: "71953830"
---
# <a name="configuring-the-lcm-in-powershell-40"></a>PowerShell 4.0에서 LCM 구성

>적용 대상: Windows PowerShell 4.0

**Windows PowerShell 5.0 이상과 관련된 자세한 내용은 [로컬 구성 관리자 구성](metaConfig.md)을 참조하세요.**

로컬 구성 관리자는 Windows PowerShell DSC(필요한 상태 구성) 엔진으로서,
모든 대상 노드에서 실행되며 DSC 구성 스크립트에 포함된 구성 리소스를 호출하는 일을 담당합니다.
이 항목에서는 로컬 구성 관리자의 속성을 나열하고 대상 노드에서 로컬 구성 관리자 설정을 수정할 수 있는 방법을 설명합니다.

## <a name="local-configuration-manager-properties"></a>로컬 구성 관리자 속성

다음은 설정하거나 검색할 수 있는 로컬 구성 관리자 속성 목록입니다.

- **AllowModuleOverwrite**: 구성 서비스에서 다운로드한 새 구성이 대상 노드에 있는 이전 구성을 덮어쓰도록 허용되는지 여부를 제어합니다. 가능한 값은 True와 False입니다.
- **CertificateID**: 구성으로 전달된 자격 증명을 보호하는 데 사용되는 인증서의 지문입니다. 자세한 내용은 [Want to secure credentials in Windows PowerShell Desired State Configuration?(Windows PowerShell 필요한 상태 구성의 자격 증명 보호가 필요하세요?)](https://blogs.msdn.microsoft.com/powershell/2014/01/31/want-to-secure-credentials-in-windows-powershell-desired-state-configuration/)을 참조하세요.
- **ConfigurationID**: 풀 서비스에서 특정 구성 파일을 가져오는 데 사용되는 GUID를 나타냅니다. 이 GUID는 올바른 구성 파일에 액세스하도록 해줍니다.
- **ConfigurationMode**: 로컬 구성 관리자가 실제로 구성을 대상 노드에 적용하는 방법을 지정합니다. 사용되는 값은 다음과 같습니다.
  - **ApplyOnly**: 이 옵션을 사용하면 새 구성을 대상 노드에 직접 전송하여 새 구성이 검색되지 않은 경우 또는 풀 서비스에 연결하고 풀 서비스에서 확인하면 DSC에서 새 구성을 검색하는 경우, DSC가 구성을 적용하는 작업만을 수행합니다. 대상 노드의 구성이 변경되지 않는 경우 아무 작업도 수행되지 않습니다.
  - **ApplyAndMonitor**: 이 옵션(기본값)을 사용하면 대상 노드에 직접 전송했든지 아니면 풀 서비스에서 검색되었든지 관계없이 DSC에서 모든 새 구성을 적용합니다. 그 후 대상 노드의 구성이 구성 파일과 달라지면, DSC에서 로그 불일치를 보고합니다. DSC 로깅에 대한 자세한 내용은 [Using Event Logs to Diagnose Errors in Desired State Configuration(이벤트 로그를 사용하여 필요한 상태 구성에 있는 오류 진단)](https://blogs.msdn.com/b/powershell/archive/2014/01/03/using-event-logs-to-diagnose-errors-in-desired-state-configuration.aspx)을 참조하세요.
  - **ApplyAndAutoCorrect**: 이 옵션을 사용하면 작업자가 대상 노드에 직접 전송했든지, 아니면 풀 서비스에서 검색되었든지 관계없이 DSC에서 모든 새 구성을 적용합니다. 그 후 대상 노드의 구성이 구성 파일과 달라지면, DSC에서 로그 불일치를 보고한 다음, 구성 파일에 따라 가져올 대상 노드 구성에 대한 조정을 시도합니다.
- **ConfigurationModeFrequencyMins**: DSC의 백그라운드 애플리케이션이 대상 노드에서 현재 구성을 구현하려고 시도하는 빈도(분)를 나타냅니다. 기본값은 15입니다. 이 값은 RefreshMode와 함께 설정할 수 있습니다. RefreshMode를 PULL로 설정하면 대상 노드에서는 RefreshFrequencyMins로 설정한 간격으로 구성 서비스에 연결하여 현재 구성을 다운로드합니다. RefreshMode 값에 관계없이 ConfigurationModeFrequencyMins로 설정한 간격으로, 대상 노드에 다운로드한 최신 구성을 일관성 엔진이 적용합니다. RefreshFrequencyMins는 ConfigurationModeFrequencyMins의 정수 배로 설정해야 합니다.
- **Credential**: 구성 서비스 연결과 같이 원격 리소스에 액세스하는 데 필요한 자격 증명(Get-Credential과 마찬가지로)을 나타냅니다.
- **DownloadManagerCustomData**: 다운로드 관리자에 특정된 사용자 지정 데이터를 포함하는 배열을 나타냅니다.
- **DownloadManagerName**: 구성 및 모듈 다운로드 관리자의 이름을 나타냅니다.
- **RebootNodeIfNeeded**: 이 값을 `$true`로 설정하여 리소스가 `$global:DSCMachineStatus` 플래그를 사용하는 노드를 다시 부팅할 수 있습니다. 그렇지 않으면 다시 부팅해야 하는 구성에 대해 노드를 수동으로 다시 부팅해야 합니다. 기본값은 `$false`입니다. DSC 이외의 다른 항목(예: Windows Installer)에서 재부팅 조건을 시행하는 경우 이 설정을 사용하려면 설정을 [xPendingReboot](https://github.com/powershell/xpendingreboot) 모듈과 결합합니다.
- **RefreshFrequencyMins**: 풀 서비스를 설정하면 사용됩니다. 로컬 구성 관리자가 현재 구성을 다운로드하기 위해 풀 서비스에 연결하는 빈도(분)를 나타냅니다. 이 값은 ConfigurationModeFrequencyMins와 함께 설정할 수 있습니다. RefreshMode를 PULL로 설정하면 대상 노드에서는 RefreshFrequencyMins로 설정한 간격으로 풀 서비스에 연결하여 현재 구성을 다운로드합니다. 그러면 ConfigurationModeFrequencyMins로 설정한 간격으로, 대상 노드에 다운로드한 최신 구성을 일관성 엔진이 적용합니다. RefreshFrequencyMins가 ConfigurationModeFrequencyMins의 정수 배로 설정되어 있지 않으면 시스템에서 반올림합니다. 기본값은 30입니다.
- **RefreshMode**: 가능한 값은 **푸시**(기본값)와 **끌어오기**입니다. "밀어넣기" 구성에서는 임의의 클라이언트 컴퓨터를 사용하여 각 대상 노드에 구성 파일을 배치해야 합니다. “풀” 모드에서는 연결할 로컬 Configuration Manager에 대한 풀 서비스를 설정하고 구성 파일에 액세스해야 합니다.

> [!NOTE]
> LCM은 다음에 따라 **ConfigurationModeFrequencyMins** 주기를 시작합니다.
>
> - 새 메타 구성은 `Set-DscLocalConfigurationManager`를 사용하여 적용됩니다.
> - 머신 다시 시작
>
> 타이머 프로세스가 충돌하는 조건의 경우 해당 기능이 30초 내에 검색되고 주기가 다시 시작됩니다.
> 동시 실행 작업은 주기가 다시 시작되는 것을 지연시킬 수 있습니다. 이 작업의 기간이 구성된 주기 빈도를 초과하면 다음 타이머가 시작되지 않습니다.
>
> 예를 들어 메타 구성은 끌어오기 빈도 15분으로 구성되고 끌어오기는 T1에 발생합니다.  노드는 16분 동안 작업을 완료하지 않습니다.  첫 번째 15분 주기가 무시되고, 다음 끌어오기는 T1+15+15분에 발생합니다.

### <a name="example-of-updating-local-configuration-manager-settings"></a>로컬 구성 관리자 설정을 업데이트하는 예제

다음 예제에서 보듯이, 구성 스크립트의 노드 블록 내에 **LocalConfigurationManager** 블록을 포함하여 대상 노드의 로컬 구성 관리자 설정을 업데이트할 수 있습니다.

```powershell
Configuration ExampleConfig
{
    Node "Server001"
    {
        LocalConfigurationManager
        {
            ConfigurationID = "646e48cb-3082-4a12-9fd9-f71b9a562d4e"
            ConfigurationModeFrequencyMins = 45
            ConfigurationMode = "ApplyAndAutocorrect"
            RefreshMode = "Pull"
            RefreshFrequencyMins = 90
            DownloadManagerName = "WebDownloadManager"
            DownloadManagerCustomData = (@{ServerUrl="https://$PullService/psdscpullserver.svc"})
            CertificateID = "71AA68562316FE3F73536F1096B85D66289ED60E"
            Credential = $cred
            RebootNodeIfNeeded = $true
            AllowModuleOverwrite = $false
        }
# One or more resource blocks can be added here
    }
}

# The following line invokes the configuration and creates a file called Server001.meta.mof at the specified path
ExampleConfig -OutputPath "c:\users\public\dsc"
```

이전 예제의 스크립트를 실행하면 원하는 설정을 지정하고 저장하는 MOF 파일이 생성됩니다.
설정을 적용하기 위해 다음 예제에서 보듯이 **Set-DscLocalConfigurationManager** cmdlet을 사용할 수 있습니다.

```powershell
Set-DscLocalConfigurationManager -Path "c:\users\public\dsc"
```

> [!NOTE]
> **Path** 매개 변수의 경우, 앞의 예제에서 구성을 호출할 때 **OutputPath**에 대해 지정한 것과 동일한 경로를 지정해야 합니다.

현재 로컬 구성 관리자 설정을 확인하기 위해 **Get-DscLocalConfigurationManager** cmdlet을 사용할 수 있습니다.
매개 변수 없이 이 cmdlet을 호출하는 경우, 기본적으로, 작업자가 실행하는 노드에 대한 로컬 구성 관리자 설정을 가져오게 됩니다.
다른 노드를 지정하려면 이 cmdlet에 **CimSession** 매개 변수를 사용합니다.
