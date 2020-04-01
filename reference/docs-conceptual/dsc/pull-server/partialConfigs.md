---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: PowerShell 필요한 상태 구성 부분 구성
ms.openlocfilehash: 842acad221d468ca5e4c9e660f0205c567bcc220
ms.sourcegitcommit: 30ccbbb32915b551c4cd4c91ef1df96b5b7514c4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/01/2020
ms.locfileid: "80500765"
---
# <a name="powershell-desired-state-configuration-partial-configurations"></a>PowerShell 필요한 상태 구성 부분 구성

_적용 대상: Windows PowerShell 5.0 이상._

PowerShell 5.0에서 DSC(필요한 상태 구성)를 사용하면 구성을 여러 소스에서 조각화하여 제공할 수 있습니다. 대상 노드의 LCM(로컬 구성 관리자)은 이 조각들을 한데 모아 하나의 구성으로 적용합니다. 이 기능을 사용하면 구성에 대한 제어권을 팀이나 개인들 간에 공유할 수 있습니다. 예를 들어 두 개 이상의 개발자 팀이 어떤 서비스에 대해 공동으로 작업 중인 경우 이들은 각각 서비스의 해당 부분을 관리하는 구성을 만들 수 있습니다. 이 구성들의 각각은 서로 다른 끌어오기 서버에서 가져올 수 있으며, 개발의 서로 다른 단계에서 추가할 수 있습니다. 부분 구성은 또한 서로 다른 개인이나 팀이 단일 구성 문서에 대한 편집 작업을 조정하지 않고도 노드 구성의 다양한 측면을 제어할 수 있도록 해줍니다. 예를 들어 한 팀은 VM과 운영 체제를 배포하는 일을 담당하고, 다른 팀은 해당 VM에서 다른 애플리케이션과 서비스를 배포할 수도 있습니다. 부분 구성을 사용하면 어느 한 팀이 불필요하게 복잡해지지 않고 각 팀이 해당 팀의 구성을 만들 수 있습니다.

밀어넣기 모드, 끌어오기 모드 또는 두 모드의 조합 모드에서 부분 구성을 사용할 수 있습니다.

## <a name="partial-configurations-in-push-mode"></a>밀어넣기 모드의 부분 구성

밀어넣기 모드에서 부분 구성을 사용하려면 부분 구성을 받도록 대상 노드의 LCM을 구성합니다. 각 부분 구성은 `Publish-DSCConfiguration` cmdlet을 사용하여 대상에 밀어넣어야 합니다. 그런 다음 대상 노드가 부분 구성을 단일 구성으로 결합하면 작업자는 [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet을 호출하여 구성을 적용할 수 있습니다.

### <a name="configuring-the-lcm-for-push-mode-partial-configurations"></a>밀어넣기 모드 부분 구성에 대한 LCM 구성

밀어넣기 모드에서 부분 구성에 대해 LCM을 구성하려면, 각 부분 구성에 대해 하나의 **PartialConfiguration** 블록으로 **DSCLocalConfigurationManager** 구성을 만듭니다. LCM 구성에 대한 자세한 내용은[Configuring the Local Configuration Manager(로컬 구성 관리자 구성)](../managing-nodes/metaConfig.md)를 참조합니다. 다음 예제에서는 두 개의 부분 구성이 예상되는 LCM 구성을 보여 줍니다. 하나는 OS를 배포하고 다른 하나는 SharePoint를 배포 및 구성합니다.

```powershell
[DSCLocalConfigurationManager()]
configuration PartialConfigDemo
{
    Node localhost
    {

        PartialConfiguration ServiceAccountConfig
        {
            Description = 'Configuration to add the SharePoint service account to the Administrators group.'
            RefreshMode = 'Push'
        }
           PartialConfiguration SharePointConfig
        {
            Description = 'Configuration for the SharePoint server'
            RefreshMode = 'Push'
        }
    }
}

PartialConfigDemo
```

각 부분 구성에 대해 **RefreshMode**는 "Push"로 설정됩니다. **PartialConfiguration** 블록의 이름(이 경우 "ServiceAccountConfig" 및 "SharePointConfig")은 대상 노드에 밀어넣은 구성의 이름과 정확하게 일치해야 합니다.

> [!Note]
> 각각의 명명된 **PartialConfiguration** 블록은 MOF 파일의 이름이 아니라 구성 스크립트에 지정된 구성의 실제 이름과 일치해야 하며, 이 이름은 대상 노드 또는 `localhost`의 이름이어야 합니다.

### <a name="publishing-and-starting-push-mode-partial-configurations"></a>밀어넣기 모드 부분 구성 게시 및 시작

그런 다음 각 구성에 대해 [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration)을 호출하여 **Path** 매개 변수로서 구성 문서를 포함하는 폴더를 전달합니다. `Publish-DSCConfiguration`은 구성 MOF 파일을 대상 노드에 배치합니다. 두 구성을 모두 게시한 후에는 대상 노드에서 `Start-DSCConfiguration –UseExisting`을 호출할 수 있습니다.

예를 들어 다음과 같은 구성 MOF 문서를 제작 노드에 컴파일한다고 가정합니다.

```powershell
Get-ChildItem -Recurse
```

```output
    Directory: C:\PartialConfigTest

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        8/11/2016   1:55 PM                ServiceAccountConfig
d-----       11/17/2016   4:14 PM                SharePointConfig

    Directory: C:\PartialConfigTest\ServiceAccountConfig

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        8/11/2016   2:02 PM           2034 TestVM.mof

    Directory: C:\PartialConfigTest\SharePointConfig

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       11/17/2016   4:14 PM           1930 TestVM.mof
```

다음과 같이 구성을 게시하고 실행합니다.

```powershell
Publish-DscConfiguration .\ServiceAccountConfig -ComputerName 'TestVM'
Publish-DscConfiguration .\SharePointConfig -ComputerName 'TestVM'
Start-DscConfiguration -UseExisting -ComputerName 'TestVM'
```

```output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
17     Job17           Configuratio... Running       True            TestVM            Start-DscConfiguration...
```

> [!Note]
> [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) cmdlet을 실행하는 사용자는 대상 노드에 대한 관리자 권한이 있어야 합니다.

## <a name="partial-configurations-in-pull-mode"></a>끌어오기 모드의 부분 구성

구성 부분은 하나 이상의 끌어오기 서버에서 끌어올 수 있습니다(끌어오기 서버에 대한 자세한 내용은 [Windows PowerShell Desired State Configuration Pull Servers(Windows PowerShell 필요한 상태 구성 끌어오기 서버)](pullServer.md) 참조). 이렇게 하려면 대상 노드에서 LCM을 구성하여 부분 구성을 끌어오고, 끌어오기 서버에서 구성 문서의 이름을 지정하고 이 문서를 배치해야 합니다.

### <a name="configuring-the-lcm-for-pull-node-configurations"></a>끌어오기 노드 구성을 위한 LCM 구성

끌어오기 서버에서 부분 구성을 가져오도록 LCM을 구성하려면 **ConfigurationRepositoryWeb**(HTTP 끌어오기 서버용) 또는 **ConfigurationRepositoryShare**(SMB 끌어오기 서버용) 블록에서 끌어오기 서버를 정의합니다. 그런 다음 **ConfigurationSource** 속성을 사용하여 끌어오기 서버를 참조하는 **PartialConfiguration** 블록을 만듭니다. 또한 LCM이 끌어오기 모드를 사용한다고 지정하고, 끌어오기 서버 및 대상 노드가 구성을 식별하는 데 사용하는 **ConfigurationNames** 또는 **ConfigurationID**를 지정하기 위한 **설정** 블록을 만들어야 합니다. 다음의 메타 구성은 CONTOSO PullSrv라는 HTTP 끌어오기 서버와, 해당 끌어오기 서버를 사용하는 두 개의 부분 구성을 정의합니다.

**ConfigurationNames**를 사용하여 LCM을 구성하는 방법에 대해서는 [구성 이름을 사용하여 끌어오기 클라이언트 설정](pullClientConfigNames.md)을 참조하세요. **ConfigurationID**를 사용하여 LCM을 구성하는 방법에 대해서는 [구성 ID를 사용하여 끌어오기 클라이언트 설정](pullClientConfigID.md)을 참조하세요.

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configuration-names"></a>구성 이름을 사용하여 끌어오기 모드 구성에 대해 LCM 구성

```powershell
[DscLocalConfigurationManager()]
Configuration PartialConfigDemoConfigNames
{
        Settings
        {
            RefreshFrequencyMins            = 30;
            RefreshMode                     = "PULL";
            ConfigurationMode               ="ApplyAndAutocorrect";
            AllowModuleOverwrite            = $true;
            RebootNodeIfNeeded              = $true;
            ConfigurationModeFrequencyMins  = 60;
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL                       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey                 = 5b41f4e6-5e6d-45f5-8102-f2227468ef38
            ConfigurationNames              = @("ServiceAccountConfig", "SharePointConfig")
        }

        PartialConfiguration ServiceAccountConfig
        {
            Description                     = "ServiceAccountConfig"
            ConfigurationSource             = @("[ConfigurationRepositoryWeb]CONTOSO-PullSrv")
        }

        PartialConfiguration SharePointConfig
        {
            Description                     = "SharePointConfig"
            ConfigurationSource             = @("[ConfigurationRepositoryWeb]CONTOSO-PullSrv")
            DependsOn                       = '[PartialConfiguration]ServiceAccountConfig'
        }
}
```

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configurationid"></a>ConfigurationID를 사용하여 끌어오기 모드 구성에 대해 LCM 구성

```powershell
[DSCLocalConfigurationManager()]
configuration PartialConfigDemoConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode                     = 'Pull'
            ConfigurationID                 = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins            = 30
            RebootNodeIfNeeded              = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL                       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

           PartialConfiguration ServiceAccountConfig
        {
            Description                     = 'Configuration for the Base OS'
            ConfigurationSource             = '[ConfigurationRepositoryWeb]CONTOSO-PullSrv'
            RefreshMode                     = 'Pull'
        }
           PartialConfiguration SharePointConfig
        {
            Description                     = 'Configuration for the Sharepoint Server'
            ConfigurationSource             = '[ConfigurationRepositoryWeb]CONTOSO-PullSrv'
            DependsOn                       = '[PartialConfiguration]ServiceAccountConfig'
            RefreshMode                     = 'Pull'
        }
    }
}
PartialConfigDemo
```

둘 이상의 끌어오기 서버에서 부분 구성을 끌어올 수 있습니다. 각 끌어오기 서버를 정의한 다음, 각 **PartialConfiguration** 블록에서 적절한 끌어오기 서버를 참조하기만 하면 됩니다.

메타 구성을 만든 후 실행하여 구성 문서(MOF 파일)를 만들고 [Set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager)를 호출하여 LCM을 구성해야 합니다.

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationnames"></a>끌어오기 서버에서 구성 문서 이름 지정 및 배치(ConfigurationNames)

부분 구성 문서는 끌어오기 서버용의 `web.config` 파일에서 **ConfigurationPath**로 지정된 폴더에 배치해야 합니다(일반적으로 `C:\Program
Files\WindowsPowerShell\DscService\Configuration`).

#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-51"></a>PowerShell 5.1의 끌어오기 서버에서 구성 문서 이름 지정

개별 끌어오기 서버에서 부분 구성 하나만 끌어오는 경우 구성 문서에 아무 이름이나 지정할 수 있습니다. 끌어오기 서버에서 둘 이상의 부분 구성을 끌어오는 경우 구성 문서 이름은 `<ConfigurationName>.mof`(여기서 *ConfigurationName*은 부분 구성의 이름임) 또는 `<ConfigurationName>.<NodeName>.mof`(여기서 *ConfigurationName*은 부분 구성의 이름이고 *NodeName*은 대상 노드의 이름임)로 지정할 수 있습니다. 따라서 Azure 자동화 DSC 끌어오기 서버에서 구성을 끌어올 수 있습니다.

#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-50"></a>PowerShell 5.0의 끌어오기 서버에서 구성 문서 이름 지정

구성 문서의 이름은 `ConfigurationName.mof`와 같이 지정해야 합니다. 여기서 *ConfigurationName*은 부분 구성의 이름입니다. 이 예에서 구성 문서의 이름은 다음과 같아야 합니다.

```
ServiceAccountConfig.mof
ServiceAccountConfig.mof.checksum
SharePointConfig.mof
SharePointConfig.mof.checksum
```

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationid"></a>끌어오기 서버에서 구성 문서 이름 지정 및 배치(ConfigurationID)

부분 구성 문서는 끌어오기 서버용의 `web.config` 파일에서 **ConfigurationPath**로 지정된 폴더에 배치해야 합니다(일반적으로 `C:\Program Files\WindowsPowerShell\DscService\Configuration`). 구성 문서 이름을 다음과 같이 지정해야 합니다. `<ConfigurationName>.<ConfigurationID>.mof`. 여기서 _ConfigurationName_은 부분 구성의 이름이고, _ConfigurationID_는 대상 노드의 LCM에 정의된 구성 ID입니다. 이 예에서 구성 문서의 이름은 다음과 같아야 합니다.

```
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
```

### <a name="running-partial-configurations-from-a-pull-server"></a>끌어오기 서버에서 부분 구성 실행

대상 노드의 LCM이 구성되고, 구성 문서가 만들어져서 끌어오기 서버에서 적절히 이름이 지정되면, 대상 노드는 부분 구성들을 끌어와서, 결합하고, 그에 따른 결과 구성을 LCM의 **RefreshFrequencyMins** 속성으로 지정한 일정한 간격으로 적용하게 됩니다. 새로 고침을 강제 적용하려는 경우 [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration) cmdlet을 호출하여 구성을 끌어온 다음, `Start-DSCConfiguration –UseExisting`을 사용하여 적용합니다.

## <a name="partial-configurations-in-mixed-push-and-pull-modes"></a>밀어넣기 및 끌어오기 혼합 모드의 부분 구성

부분 구성을 위해 밀어넣기 모드와 끌어오기 모드를 혼합할 수도 있습니다. 즉, 끌어오기 서버에서 끌어온 부분 구성 하나와 밀어넣은 또 다른 부분 구성이 있을 수 있습니다. 이전 섹션에 설명된 대로 각 부분 구성에 대해 새로 고침 모드를 지정합니다. 예를 들어 다음의 메타 구성은 끌어오기 모드의 `ServiceAccountConfig` 부분 구성과 밀어넣기 모드의 `SharePointConfig` 부분 구성으로 같은 예를 설명합니다.

### <a name="mixed-push-and-pull-modes-using-configurationnames"></a>ConfigurationNames를 사용한 혼합된 밀어넣기 및 끌어오기 모드

```powershell
[DscLocalConfigurationManager()]
Configuration PartialConfigDemoConfigNames
{
        Settings
        {
            RefreshFrequencyMins            = 30;
            RefreshMode                     = "PULL";
            ConfigurationMode               = "ApplyAndAutocorrect";
            AllowModuleOverwrite            = $true;
            RebootNodeIfNeeded              = $true;
            ConfigurationModeFrequencyMins  = 60;
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL                       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey                 = 5b41f4e6-5e6d-45f5-8102-f2227468ef38
            ConfigurationNames              = @("ServiceAccountConfig", "SharePointConfig")
        }

        PartialConfiguration ServiceAccountConfig
        {
            Description                     = "ServiceAccountConfig"
            ConfigurationSource             = @("[ConfigurationRepositoryWeb]CONTOSO-PullSrv")
            RefreshMode                     = 'Pull'
        }

        PartialConfiguration SharePointConfig
        {
            Description                     = "SharePointConfig"
            DependsOn                       = '[PartialConfiguration]ServiceAccountConfig'
            RefreshMode                     = 'Push'
        }

}
```

### <a name="mixed-push-and-pull-modes-using-configurationid"></a>ConfigurationID를 사용한 혼합된 밀어넣기 및 끌어오기 모드

```powershell
[DSCLocalConfigurationManager()]
configuration PartialConfigDemo
{
    Node localhost
    {
        Settings
        {
            RefreshMode             = 'Pull'
            ConfigurationID         = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins    = 30
            RebootNodeIfNeeded      = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL               = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

           PartialConfiguration ServiceAccountConfig
        {
            Description             = 'Configuration for the Base OS'
            ConfigurationSource     = '[ConfigurationRepositoryWeb]CONTOSO-PullSrv'
            RefreshMode             = 'Pull'
        }
           PartialConfiguration SharePointConfig
        {
            Description             = 'Configuration for the Sharepoint Server'
            DependsOn               = '[PartialConfiguration]ServiceAccountConfig'
            RefreshMode             = 'Push'
        }
    }
}
PartialConfigDemo
```

Settings 블록에 지정된 **RefreshMode**는 "Pull"이지만, `SharePointConfig` 부분 구성에 대한 **RefreshMode**는 "Push"입니다.

각각의 새로 고침 모드에 대해 위에서 설명한 대로 구성 MOF 파일에 이름을 지정하고 배치합니다.
`Publish-DSCConfiguration`을 호출하여 `SharePointConfig` 부분 구성을 게시하고, 끌어오기 서버에서 `ServiceAccountConfig` 구성을 끌어오기를 기다리거나 [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration)을 호출하여 새로 고침을 적용합니다.

## <a name="example-serviceaccountconfig-partial-configuration"></a>ServiceAccountConfig 부분 구성 예

```powershell
Configuration ServiceAccountConfig
{
    Param (
        [Parameter(Mandatory,
                   HelpMessage="Domain credentials required to add domain\sharepoint_svc to the local Administrators group.")]
        [ValidateNotNullOrEmpty()]
        [pscredential]$Credential
    )

    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node localhost
    {
        Group LocalAdmins
        {
            GroupName           = 'Administrators'
            MembersToInclude    = 'domain\sharepoint_svc',
                                  'admins@example.domain'
            Ensure              = 'Present'
            Credential          = $Credential
        }

        WindowsFeature Telnet
        {
            Name                = 'Telnet-Server'
            Ensure              = 'Absent'
        }
    }
}
ServiceAccountConfig
```

## <a name="example-sharepointconfig-partial-configuration"></a>SharePointConfig 부분 구성 예제

```powershell
Configuration SharePointConfig
{
    Param (
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [pscredential]$ProductKey
    )

    Import-DscResource -ModuleName xSharePoint

    Node localhost
    {
        xSPInstall SharePointDefault
        {
            Ensure      = 'Present'
            BinaryDir   = '\\FileServer\Installers\Sharepoint\'
            ProductKey  = $ProductKey
        }
    }
}
SharePointConfig
```

## <a name="see-also"></a>참고 항목

[Windows PowerShell Desired State Configuration 끌어오기 서버](pullServer.md)

[Configuring the Local Configuration Manager(로컬 구성 관리자 구성)](../managing-nodes/metaConfig.md)
