---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: 로컬 구성 관리자 구성
ms.openlocfilehash: 42544036d87fcea3189fd6d2e55579fe87f137e1
ms.sourcegitcommit: 02eed65c526ef19cf952c2129f280bb5615bf0c8
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70215394"
---
# <a name="configuring-the-local-configuration-manager"></a>로컬 구성 관리자 구성

> 적용 대상: Windows Powershell 5.0

LCM(로컬 구성 관리자)은 DSC(필요한 상태 구성)의 엔진입니다.
LCM은 모든 대상 노드에서 실행되며, 노드로 전송되는 구성을 구문 분석하고 시행하는 일을 담당합니다.
다음 작업을 포함하여 DSC의 수 많은 다른 측면을 담당하기도 합니다.

- 새로 고침 모드 결정(밀어넣기 또는 끌어오기)
- 노드가 구성을 끌어와서 시행하는 빈도 지정
- 노드를 풀 서비스와 연결
- 부분 구성 지정

특별한 형식의 구성을 사용하여 이러한 각각의 동작을 지정하도록 LCM을 구성합니다.
다음 섹션에서는 LCM을 구성하는 방법에 대해 설명합니다.

Windows PowerShell 5.0에는 로컬 구성 관리자를 관리하는 데 사용되는 새 설정이 도입되었습니다.
Windows PowerShell 4.0에서 LCM을 구성하는 방법에 대한 자세한 내용은 [이전 버전의 Windows PowerShell에서 로컬 구성 관리자 구성](metaconfig4.md)을 참조하세요.

## <a name="writing-and-enacting-an-lcm-configuration"></a>LCM 구성 작성 및 시행

LCM을 구성하려면 LCM 설정을 적용하는 특수한 형식의 구성을 만들어 실행합니다.
LCM 구성을 지정하려면 DscLocalConfigurationManager 특성을 사용합니다.
다음은 LCM을 밀어넣기 모드로 설정하는 간단한 구성을 보여 줍니다.

```powershell
[DSCLocalConfigurationManager()]
configuration LCMConfig
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Push'
        }
    }
}
```

LCM에 설정을 적용하는 프로세스는 DSC 구성을 적용하는 프로세스와 비슷합니다.
LCM 구성을 만들고 MOF 파일에 컴파일한 후 노드에 적용합니다.
DSC 구성과 달리 [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet을 호출하여 LCM 구성을 시행하지 않습니다.
대신, LCM 구성 MOF 경로를 매개 변수로 제공하는 [Set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager)를 호출합니다.
LCM 구성 시행 후에는 [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) cmdlet을 호출하여 LCM의 속성을 확인할 수 있습니다.

LCM 구성은 제한된 리소스 집합에 대한 블록만 포함할 수 있습니다.
이전 예에서 유일하게 호출된 리소스는 **Settings**입니다.
다른 사용 가능한 리소스는 다음과 같습니다.

* **ConfigurationRepositoryWeb**: 구성에 대한 HTTP 풀 서비스를 지정합니다.
* **ConfigurationRepositoryShare**: 구성에 대한 SMB 공유를 지정합니다.
* **ResourceRepositoryWeb**: 모듈에 대한 HTTP 풀 서비스를 지정합니다.
* **ResourceRepositoryShare**: 모듈에 대한 SMB 공유를 지정합니다.
* **ReportServerWeb**: 보고서를 전송받을 HTTP 풀 서비스를 지정합니다.
* **PartialConfiguration**: 부분 구성을 사용하는 데이터를 제공합니다.

## <a name="basic-settings"></a>기본 설정

풀 서비스 엔드포인트/경로와 부분 구성을 지정하는 것 외에 LCM의 모든 속성은 **Settings** 블록에 구성되어 있습니다.
**Settings** 블록에서는 다음 속성을 사용할 수 있습니다.

|  속성  |  유형  |  설명   |
|----------- |------- |--------------- |
| ActionAfterReboot| string| 구성을 적용하는 동안 다시 부팅하면 어떤 일이 일어나는지 지정합니다. 가능한 값은 __"ContinueConfiguration"__ 및 __"StopConfiguration"__ 입니다. <ul><li> __ContinueConfiguration__: 머신을 다시 부팅한 후 현재 구성을 계속 적용합니다. 기본값입니다.</li><li>__StopConfiguration__: 머신을 다시 부팅한 후 현재 구성을 중지합니다.</li></ul>|
| AllowModuleOverwrite| 부울| 풀 서비스에서 다운로드한 새 구성이 대상 노드에 있는 이전 구성을 덮어쓰도록 허용되는 경우 __$TRUE__입니다. 그렇지 않으면 $FALSE입니다.|
| CertificateID| string| 구성으로 전달된 자격 증명을 보호하는 데 사용되는 인증서의 지문입니다. 자세한 내용은 [Want to secure credentials in Windows PowerShell Desired State Configuration(Windows PowerShell 필요한 상태 구성의 자격 증명 보호가 필요하세요)](http://blogs.msdn.com/b/powershell/archive/2014/01/31/want-to-secure-credentials-in-windows-powershell-desired-state-configuration.aspx)을 참조하세요. <br> __참고:__ Azure Automation DSC 풀 서비스를 사용하는 경우 자동으로 관리됩니다.|
| ConfigurationDownloadManagers| CimInstance[]| 사용되지 않습니다. 구성 풀 서비스 엔드포인트를 정의하려면 __ConfigurationRepositoryWeb__ 및 __ConfigurationRepositoryShare__ 블록을 사용합니다.|
| ConfigurationID| string| 이전 풀 서비스 버전과의 호환성을 위해 사용합니다. 풀 서비스에서 가져올 구성 파일을 식별하는 GUID입니다. 구성 MOF의 이름이 ConfigurationID.mof로 지정된 경우 노드는 풀 서비스에서 구성을 끌어옵니다.<br> __참고:__ 이 속성을 설정하는 경우 __RegistrationKey__를 사용하여 풀 서비스에서 노드가 등록되지 않습니다. 자세한 내용은 [Setting up a pull client with configuration names(구성 이름을 사용하여 끌어오기 클라이언트 설정)](../pull-server/pullClientConfigNames.md)를 참조합니다.|
| ConfigurationMode| string | LCM이 구성을 실제로 대상 노드를 적용하는 방식을 지정합니다. 가능한 값은 __“ApplyOnly”__ , __“ApplyAndMonitor”__ , __“ApplyAndAutoCorrect”__ 입니다. <ul><li>__ApplyOnly__: 새 구성이 대상 노드에 밀어넣어지지 않은 경우, 또는 새 구성이 서비스에서 끌어온 구성인 경우 DSC가 구성을 적용하고 더 이상의 작업은 수행하지 않습니다. 새 구성의 초기 적용 후에는 DSC에서 이전에 구성된 상태가 변경되었는지 여부를 확인하지 않습니다. DSC는 __ApplyOnly__가 적용되기 전에 성공할 때까지 구성을 적용하려고 시도합니다. </li><li> __ApplyAndMonitor__: 기본값입니다. LCM이 새 구성을 적용합니다. 새 구성의 초기 적용 후, 대상 노드의 상태가 필요한 상태에서 변경되는 경우 DSC에서는 로그의 불일치를 보고합니다. DSC는 __ApplyAndMonitor__가 적용되기 전에 성공할 때까지 구성을 적용하려고 시도합니다.</li><li>__ApplyAndAutoCorrect__: DSC에서 모든 새 구성을 적용합니다. 새 구성의 초기 적용 후, 대상 노드의 상태가 필요한 상태에서 변경되는 경우 DSC에서는 로그의 불일치를 보고한 다음, 현재 구성을 다시 적용합니다.</li></ul>|
| ConfigurationModeFrequencyMins| UInt32| 현재 구성이 확인 및 적용되는 분 단위 빈도입니다. 이 속성은 ConfigurationMode 속성이 ApplyOnly로 설정되어 있을 경우 무시됩니다. 기본값은 15입니다.|
| DebugMode| string| 가능한 값은 __None__, __ForceModuleImport__ 및 __All__입니다. <ul><li>캐시된 리소스를 사용하려면 __None__으로 설정합니다. 기본값이며 프로덕션 시나리오에서 사용해야 합니다.</li><li>__ForceModuleImport__로 설정하면 DSC 리소스 모듈이 이전에 로드되어 캐시되었더라도 LCM에서 이 모듈들을 다시 로드합니다. 이것은 각 모듈이 사용 시 다시 로드되는 대로 DSC 작업의 성능에 영향을 줍니다. 일반적으로 리소스를 디버그할 때 이 값을 사용합니다.</li><li>이 릴리스에서 __All__은 __ForceModuleImport__와 동일합니다.</li></ul> |
| RebootNodeIfNeeded| 부울| 이 값을 `$true`로 설정하여 리소스가 `$global:DSCMachineStatus` 플래그를 사용하는 노드를 다시 부팅할 수 있습니다. 그렇지 않으면 다시 부팅해야 하는 구성에 대해 노드를 수동으로 다시 부팅해야 합니다. 기본값은 `$false`입니다. DSC 이외의 다른 항목(예: Windows Installer)에서 재부팅 조건을 시행하는 경우 이 설정을 사용하려면 설정을 [xPendingReboot](https://github.com/powershell/xpendingreboot) 모듈과 결합합니다.|
| RefreshMode| string| LCM이 구성을 가져오는 방법을 지정합니다. 가능한 값은 __"Disabled"__ , __"Push"__ 및 __"Pull"__ 입니다. <ul><li>__Disabled__: 이 노드에 대해 DSC 구성을 사용할 수 없게 됩니다.</li><li> __Push__: [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet을 호출하여 구성을 시작합니다. 구성이 즉시 노드에 적용됩니다. 기본값입니다.</li><li>__Pull:__ 끌어오기 서비스 또는 SMB 경로의 구성을 정기적으로 확인하도록 노드를 구성합니다. 이 속성이 __Pull__로 설정되어 있으면 __ConfigurationRepositoryWeb__ 또는 __ConfigurationRepositoryShare__ 블록에서 HTTP(서비스) 또는 SMB(공유) 경로를 지정해야 합니다.</li></ul>|
| RefreshFrequencyMins| Uint32| LCM에서 업데이트된 구성을 가져오기 위해 풀 서비스를 확인하는 분 단위 시간 간격입니다. 이 값은 LCM이 끌어오기 모드로 구성되지 않은 경우 무시됩니다. 기본값은 30입니다.|
| ReportManagers| CimInstance[]| 사용되지 않습니다. __ReportServerWeb__ 블록을 사용하여 풀 서비스에 보고 데이터를 보낼 엔드포인트를 정의합니다.|
| ResourceModuleManagers| CimInstance[]| 사용되지 않습니다. __ResourceRepositoryWeb__ 및 __ResourceRepositoryShare__ 블록을 사용하여 풀 서비스 HTTP 엔드포인트 또는 SMB 경로를 각각 정의합니다.|
| PartialConfigurations| CimInstance| 구현되지 않았습니다. 사용하지 마세요.|
| StatusRetentionTimeInDays | UInt32| LCM에서 현재 구성의 상태를 유지하는 일 수입니다.|

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

## <a name="pull-service"></a>풀 서비스

LCM 구성에서는 다음 형식의 풀 서비스 엔드포인트를 정의할 수 있습니다.

- **구성 서버**: DSC 구성용 리포지토리입니다. **ConfigurationRepositoryWeb**(웹 기반 서버용) 및 **ConfigurationRepositoryShare**(SMB 기반 서버용) 블록을 사용하여 구성 서버를 정의합니다.
- **리소스 서버**: PowerShell 모듈로서 패키지에 포함된 DSC 리소스용 리포지토리입니다. **ResourceRepositoryWeb**(웹 기반 서버용) 및 **ResourceRepositoryShare**(SMB 기반 서버용) 블록을 사용하여 리소스 서버를 정의합니다.
- **보고서 서버**: DSC에서 보내는 보고서 데이터를 전송받는 서비스입니다. **ReportServerWeb** 블록을 사용하여 보고서 서버를 정의합니다. 보고서 서버는 웹 서비스여야 합니다.

끌어오기 서비스에 대한 자세한 내용은 [원하는 상태 구성 끌어오기 서비스](../pull-server/pullServer.md)를 참조하세요.

## <a name="configuration-server-blocks"></a>구성 서버 블록

웹 기반 구성 서버를 정의하려면 **ConfigurationRepositoryWeb** 블록을 만듭니다.
**ConfigurationRepositoryWeb**은 다음 속성을 정의합니다.

|속성|유형|설명|
|---|---|---|
|AllowUnsecureConnection|부울|인증 없이 노드에서 서버에 연결할 수 있도록 하려면 **$TRUE**로 설정합니다. 인증을 요구하려면 **$FALSE**로 설정합니다.|
|CertificateID|string|서버를 인증하는 데 사용되는 인증서의 지문입니다.|
|ConfigurationNames|String[]|대상 노드에서 끌어올 일련의 구성 이름입니다. 이 이름들은 노드가 **RegistrationKey**를 사용하여 풀 서비스에 등록되어 있지 않은 경우에만 사용됩니다. 자세한 내용은 [Setting up a pull client with configuration names(구성 이름을 사용하여 끌어오기 클라이언트 설정)](../pull-server/pullClientConfigNames.md)를 참조합니다.|
|RegistrationKey|string|풀 서비스에 노드를 등록하는 GUID입니다. 자세한 내용은 [Setting up a pull client with configuration names(구성 이름을 사용하여 끌어오기 클라이언트 설정)](../pull-server/pullClientConfigNames.md)를 참조합니다.|
|ServerURL|string|구성 서비스의 URL입니다.|
|ProxyURL*|string|구성 서비스와 통신할 때 사용할 http 프록시의 URL입니다.|
|ProxyCredential*|pscredential|Http 프록시에 사용할 자격 증명입니다.|

> [!NOTE]
> * Windows 버전 1809 이상에서 지원됩니다.

온-프레미스 노드에 대해 ConfigurationRepositoryWeb 값 구성을 간소화하는 예제 스크립트를 사용할 수 있습니다([DSC 메타 구성 생성](https://docs.microsoft.com/azure/automation/automation-dsc-onboarding#generating-dsc-metaconfigurations) 참조).

SMB 기반 구성 서버를 정의하려면 **ConfigurationRepositoryShare** 블록을 만듭니다.
**ConfigurationRepositoryShare**는 다음 속성을 정의합니다.

|속성|유형|설명|
|---|---|---|
|자격 증명|MSFT_Credential|SMB 공유에 인증하는 데 사용되는 자격 증명입니다.|
|SourcePath|string|SMB 공유의 경로입니다.|

## <a name="resource-server-blocks"></a>리소스 서버 블록

웹 기반 리소스 서버를 정의하려면 **ResourceRepositoryWeb** 블록을 만듭니다.
**ResourceRepositoryWeb**은 다음 속성을 정의합니다.

|속성|유형|설명|
|---|---|---|
|AllowUnsecureConnection|부울|인증 없이 노드에서 서버에 연결할 수 있도록 하려면 **$TRUE**로 설정합니다. 인증을 요구하려면 **$FALSE**로 설정합니다.|
|CertificateID|string|서버를 인증하는 데 사용되는 인증서의 지문입니다.|
|RegistrationKey|string|풀 서비스에 대해 노드를 식별하는 GUID입니다.|
|ServerURL|string|구성 서버의 URL입니다.|
|ProxyURL*|string|구성 서비스와 통신할 때 사용할 http 프록시의 URL입니다.|
|ProxyCredential*|pscredential|Http 프록시에 사용할 자격 증명입니다.|

> [!NOTE]
> * Windows 버전 1809 이상에서 지원됩니다.

온-프레미스 노드에 대해 ResourceRepositoryWeb 값 구성을 간소화하는 예제 스크립트를 사용할 수 있습니다([DSC 메타 구성 생성](https://docs.microsoft.com/azure/automation/automation-dsc-onboarding#generating-dsc-metaconfigurations) 참조).

SMB 기반 리소스 서버를 정의하려면 **ResourceRepositoryShare** 블록을 만듭니다.
**ResourceRepositoryShare**는 다음 속성을 정의합니다.

|속성|유형|설명|
|---|---|---|
|자격 증명|MSFT_Credential|SMB 공유에 인증하는 데 사용되는 자격 증명입니다. 자격 증명 전달 예는 [DSC SMB 끌어오기 서버 설정](../pull-server/pullServerSMB.md)을 참조하세요.|
|SourcePath|string|SMB 공유의 경로입니다.|

## <a name="report-server-blocks"></a>보고서 서버 블록

보고서 서버를 정의하려면, **ReportServerWeb** 블록을 만듭니다.
보고서 서버 역할은 SMB 기반 풀 서비스와 호환되지 않습니다.
**ReportServerWeb**은 다음 속성을 정의합니다.

|속성|유형|설명|
|---|---|---|
|AllowUnsecureConnection|부울|인증 없이 노드에서 서버에 연결할 수 있도록 하려면 **$TRUE**로 설정합니다. 인증을 요구하려면 **$FALSE**로 설정합니다.|
|CertificateID|string|서버를 인증하는 데 사용되는 인증서의 지문입니다.|
|RegistrationKey|string|풀 서비스에 대해 노드를 식별하는 GUID입니다.|
|ServerURL|string|구성 서버의 URL입니다.|
|ProxyURL*|string|구성 서비스와 통신할 때 사용할 http 프록시의 URL입니다.|
|ProxyCredential*|pscredential|Http 프록시에 사용할 자격 증명입니다.|

> [!NOTE]
> * Windows 버전 1809 이상에서 지원됩니다.

온-프레미스 노드에 대해 ReportServerWeb 값 구성을 간소화하는 예제 스크립트를 사용할 수 있습니다([DSC 메타 구성 생성](https://docs.microsoft.com/azure/automation/automation-dsc-onboarding#generating-dsc-metaconfigurations) 참조).

## <a name="partial-configurations"></a>부분 구성

부분 구성을 정의하려면 **PartialConfiguration** 블록을 만듭니다.
부분 구성에 대한 자세한 내용은 [DSC Partial configurations(DSC 부분 구성)](../pull-server/partialConfigs.md)를 참조하세요.
**PartialConfiguration**은 다음 속성을 정의합니다.

|속성|유형|설명|
|---|---|---|
|ConfigurationSource|string[]|이전에 **ConfiguratoinRepositoryWeb** 및 **ConfigurationRepositoryShare** 블록에서 정의한 구성 서버 이름 배열입니다. 이러한 서버에서 부분 구성을 가져옵니다.|
|DependsOn|string{}|이 부분 구성을 적용하기 전에 먼저 완료해야 하는 다른 구성의 이름 목록입니다.|
|설명|string|부분 구성을 설명하는 데 사용되는 텍스트입니다.|
|ExclusiveResources|string[]|이 부분 구성에만 사용하는 일련의 리소스입니다.|
|RefreshMode|string|LCM에서 이 부분 구성을 가져오는 방법을 지정합니다. 가능한 값은 __"Disabled"__ , __"Push"__ 및 __"Pull"__ 입니다. <ul><li>__Disabled__: 이 부분 구성이 사용되지 않도록 설정됩니다.</li><li> __Push__: [Publish-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) cmdlet을 호출하여 부분 구성을 노드에 밀어넣습니다. 노드에 대한 모든 부분 구성을 서비스에서 밀어넣었거나 끌어오면 `Start-DscConfiguration –UseExisting`을 호출하여 구성을 시작할 수 있습니다. 기본값입니다.</li><li>__Pull:__ 끌어오기 서비스의 부분 구성을 정기적으로 확인하도록 노드를 구성합니다. 이 속성이 __Pull__로 설정되어 있으면 __ConfigurationSource__ 속성에서 풀 서비스를 지정해야 합니다. Azure Automation 풀 서비스에 대한 자세한 내용은 [Azure Automation DSC 개요](https://docs.microsoft.com/azure/automation/automation-dsc-overview)를 참조하세요.</li></ul>|
|ResourceModuleSource|string[]|이 부분 구성에 대해 다운로드할 필수 리소스가 있었던 일련의 리소스 서버 이름입니다. 이 이름들은 이전에 **ResourceRepositoryWeb** 및 **ResourceRepositoryShare** 블록에서 정의한 서비스 엔드포인트를 참조해야 합니다.|

__참고:__ 부분 구성은 Azure Automation DSC에서 지원되지만 각 자동화 계정에서 노드당 구성 하나만 가져올 수 있습니다.

## <a name="see-also"></a>참고 항목

### <a name="concepts"></a>개념
[원하는 상태 구성 개요](../overview/overview.md)

[Azure Automation DSC 시작하기](https://docs.microsoft.com/azure/automation/automation-dsc-getting-started)

### <a name="other-resources"></a>관련 자료

[Set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager)

[Setting up a pull client with configuration names(구성 이름을 사용하여 끌어오기 클라이언트 설정)](../pull-server/pullClientConfigNames.md)
