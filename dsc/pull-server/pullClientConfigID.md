---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: PowerShell 5.0 이상에서 구성 ID를 사용하여 끌어오기 클라이언트 설정
ms.openlocfilehash: 14db98d240bc87aca3ee985db08c14b7c65d8bb8
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2019
ms.locfileid: "58055719"
---
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-50-and-later"></a>PowerShell 5.0 이상에서 구성 ID를 사용하여 끌어오기 클라이언트 설정

> 적용 대상: Windows Powershell 5.0

> [!IMPORTANT]
> 끌어오기 서버(Windows 기능 *DSC-Service*)는 Windows Server의 지원되는 구성 요소이지만 새로운 기능을 제공할 계획은 없습니다. 관리되는 클라우드를 [Azure Automation DSC](/azure/automation/automation-dsc-getting-started)(Windows Server에 끌어오기 서버 이외의 기능 포함) 또는 [여기](pullserver.md#community-solutions-for-pull-service)에 나열된 커뮤니티 솔루션 중 하나로 전환하기 시작하는 것이 좋습니다.

끌어오기 클라이언트를 설정하기 전에 끌어오기 서버를 설정해야 합니다. 이 순서가 필요하지 않더라도 문제 해결에 도움이 되고 등록에 성공했는지 확인할 수 있습니다. 끌어오기 서버를 설정하려면 다음 가이드를 사용하면 됩니다.

- [DSC SMB 끌어오기 서버 설정](pullServerSmb.md)
- [DSC HTTP 끌어오기 서버 설정](pullServer.md)

구성, 리소스를 다운로드하고 해당 상태를 보고하도록 각 대상 노드를 구성할 수 있습니다. 아래 섹션에서는 SMB 공유 또는 HTTP DSC 끌어오기 서버를 사용하여 끌어오기 클라이언트를 구성하는 방법을 보여줍니다. 노드의 LCM가 새로 고쳐지면 구성된 위치에 도달하여 할당된 구성을 다운로드합니다. 노드에서 필수 리소스가 존재하지 않는 경우 구성된 위치로부터 자동으로 다운로드합니다. 노드가 [보고서 서버](reportServer.md)를 사용하여 구성되는 경우 해당 작업의 상태를 보고합니다.

> [!NOTE]
> 이 토픽은 PowerShell 5.0에 적용됩니다. PowerShell 4.0에서 끌어오기 클라이언트를 설정하는 것에 대해서는 [PowerShell 4.0에서 구성 ID를 사용하여 끌어오기 클라이언트 설정](pullClientConfigID4.md)을 참조하세요.

## <a name="configure-the-pull-client-lcm"></a>끌어오기 클라이언트 LCM 구성

아래 예제 중 하나가 실행되면 **PullClientConfigID**라는 새 출력 폴더가 생성되고, 거기에 메타 구성 MOF 파일을 만듭니다. 이 경우 메타 구성 MOF 파일의 이름은 `localhost.meta.mof`로 지정됩니다.

구성을 적용하려면 메타 구성 MOF 파일의 위치로 설정된 **Path**와 함께 **Set-DscLocalConfigurationManager** cmdlet을 호출합니다. 예:

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a>구성 ID

아래 예제에서는 이전에 이 목적으로 만들어진 LCM의 **ConfigurationID** 속성을 **Guid**로 설정합니다. **ConfigurationID**는 LCM이 끌어오기 서버에서 적절한 구성의 찾는 데 사용하는 ID입니다. 끌어오기 서버의 구성 MOF 파일의 이름은 `ConfigurationID.mof`로 지정해야 합니다. 여기서 *ConfigurationID*는 대상 노드의 LCM의 **ConfigurationID** 속성의 값입니다. 자세한 내용은 [끌어오기 서버에 구성 게시(v4/v5)](publishConfigs.md)를 참조하세요.

아래 예제 또는 [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet을 사용하여 임의의 **Guid**를 만들 수 있습니다.

```powershell
[System.Guid]::NewGuid()
```

환경에서 **Guid**를 사용하는 방법에 대한 자세한 내용은 [Guid에 대한 계획](/powershell/dsc/secureserver#guids)을 참조하세요.

## <a name="set-up-a-pull-client-to-download-configurations"></a>구성을 다운로드하도록 끌어오기 클라이언트 설정

각 클라이언트는 **끌어오기** 모드로 구성되고 구성이 저장된 끌어오기 서버 URL이 지정되어야 합니다. 이를 수행하려면, 필요한 정보와 함께 LCM(로컬 구성 관리자)을 구성해야 합니다. LCM을 구성하려면 **DSCLocalConfigurationManager** 특성으로 데코레이팅된 특별한 형식의 구성을 만듭니다. LCM 구성에 대한 자세한 내용은 [로컬 구성 관리자 구성](../managing-nodes/metaConfig.md)을 참조하세요.

### <a name="http-dsc-pull-server"></a>HTTP DSC 끌어오기 서버

다음 스크립트는 "CONTOSO-PullSrv"라는 서버에서 구성을 끌어오도록 LCM을 구성합니다.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }
    }
}
PullClientConfigID
```

스크립트에서 **ConfigurationRepositoryWeb** 블록은 끌어오기 서버를 정의합니다. **ServerUrl**은 DSC 끌어오기의 URL을 지정합니다.

### <a name="smb-share"></a>SMB 공유

다음 스크립트에서는 SMB 공유 `\\SMBPullServer\Pull`로부터 구성을 끌어오도록 LCM을 구성합니다.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryShare SMBPullServer
        {
            SourcePath = '\\SMBPullServer\Pull'
        }
    }
}
PullClientConfigID
```

해당 스크립트에서 **ConfigurationRepositoryShare** 블록은 끌어오기 서버를 정의합니다(이 경우에는 SMB 공유임).

## <a name="set-up-a-pull-client-to-download-resources"></a>리소스를 다운로드하도록 끌어오기 클라이언트 설정

앞의 예와 같이 LCM 구성에서 **ConfigurationRepositoryWeb** 또는 **ConfigurationRepositoryShare** 블록만 지정하는 경우 끌어오기 클라이언트는 해당 구성을 가져온 것과 동일한 위치에서 리소스를 끌어옵니다. 리소스에 대해 별도 위치를 지정할 수도 있습니다. 별도 서버로 리소스 위치를 지정하려면 **ResourceRepositoryWeb** 블록을 사용합니다. SMB 공유로 리소스 위치를 지정하려면 **ResourceRepositoryShare** 블록을 사용합니다.

> [!NOTE]
> **ConfigurationRepositoryWeb**을 **ResourceRepositoryShare**와 결합하거나 **ConfigurationRepositoryShare**를 **ResourceRepositoryWeb** 과 결합할 수 있습니다. 이 예제가 아래에 표시되지 않았습니다.

### <a name="http-dsc-pull-server"></a>HTTP DSC 끌어오기 서버

다음 메타 구성은 **CONTOSO-PullSrv**로부터 구성을 가져오고 **CONTOSO-ResourceSrv**로부터 리소스를 가져오도록 끌어오기 클라이언트를 구성합니다.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

        ResourceRepositoryWeb CONTOSO-ResourceSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

### <a name="smb-share"></a>SMB 공유

다음 예제에서는 SMB 공유 `\\SMBPullServer\Configurations`로부터 구성을 끌어오고, SMB 공유 `\\SMBPullServer\Resources`로부터 리소스를 끌어오도록 클라이언트를 설정하는 메타 구성을 보여줍니다.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryShare SMBPullServer
        {
            SourcePath = '\\SMBPullServer\Configurations'
        }

        ResourceRepositoryShare SMBResourceServer
        {
            SourcePath = '\\SMBPullServer\Resources'
        }
    }
}
PullClientConfigID
```

#### <a name="automatically-download-resources-in-push-mode"></a>푸시 모드에서 자동으로 리소스 다운로드

PowerShell 5.0부터 끌어오기 클라이언트는 **푸시** 모드로 구성된 경우에도 SMB 공유로부터 모듈을 다운로드할 수 있습니다. 이 기능은 끌어오기 서버를 설정하지 않으려는 시나리오에서 특히 유용합니다. **ResourceRepositoryShare** 블록은 **ConfigurationRepositoryShare**를 지정하지 않고 사용할 수 있습니다. 다음 예제에서는 SMB 공유 `\\SMBPullServer\Resources`로부터 리소스를 끌어오도록 클라이언트를 설정하는 메타 구성을 보여줍니다. 노드가 **PUSHED** 구성이면 지정된 공유로부터 모든 필수 리소스를 자동으로 다운로드합니다.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Push'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
        }

        ResourceRepositoryShare SMBResourceServer
        {
            SourcePath = '\\SMBPullServer\Resources'
        }
    }
}
PullClientConfigID
```

## <a name="set-up-a-pull-client-to-report-status"></a>상태를 보고하도록 끌어오기 클라이언트 설정

기본적으로 노드는 구성된 끌어오기 서버로 보고서를 보내지 않습니다. 구성, 리소스 및 보고에 단일 끌어오기 서버를 사용할 수 있지만 **ReportRepositoryWeb** 블록을 만들어 보고를 설정해야 합니다.

### <a name="http-dsc-pull-server"></a>HTTP DSC 끌어오기 서버

다음 예제에서는 구성 및 리소스를 끌어오고 보고 데이터를 단일 서버에 보내도록 클라이언트를 설정하는 메타 구성을 보여 줍니다.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
        }

        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

보고서 서버를 지정하려면 **ReportRepositoryWeb** 블록을 사용합니다. 보고서 서버는 SMB 서버일 수 없습니다.
해당 메타 구성은 **CONTOSO-PullSrv**에서 구성을 가져오고 **CONTOSO-ResourceSrv**에서 리소스를 가져오고, **CONTOSO-ReportSrv**에 상태 보고서를 보내도록 끌어오기 클라이언트를 구성합니다.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

        ResourceRepositoryWeb CONTOSO-ResourceSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }

        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

### <a name="smb-share"></a>SMB 공유

보고서 서버는 SMB 공유일 수 없습니다.

## <a name="next-steps"></a>다음 단계

끌어오기 클라이언트를 구성하면 다음 가이드를 사용하여 다음 단계를 수행할 수 있습니다.

- [끌어오기 서버에 구성 게시(v4/v5)](publishConfigs.md)
- [리소스 패키지 및 끌어오기 서버에 업로드(v4)](package-upload-resources.md)

## <a name="see-also"></a>참고 항목

* [Setting up a pull client with configuration names(구성 이름을 사용하여 끌어오기 클라이언트 설정)](pullClientConfigNames.md)
