---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: PowerShell 5.0 이상 구성 Id를 사용 하 여 끌어오기 클라이언트 설정
ms.openlocfilehash: 8d8cf478f9127e1b7005d1b9e832e84b11612c9c
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402783"
---
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-50-and-later"></a>PowerShell 5.0 이상 구성 Id를 사용 하 여 끌어오기 클라이언트 설정

> 적용 대상: Windows Powershell 5.0

> [!IMPORTANT]
> 끌어오기 서버(Windows 기능 *DSC-Service*)는 Windows Server의 지원되는 구성 요소이지만 새로운 기능을 제공할 계획은 없습니다. 관리되는 클라우드를 [Azure Automation DSC](/azure/automation/automation-dsc-getting-started)(Windows Server에 끌어오기 서버 이외의 기능 포함) 또는 [여기](pullserver.md#community-solutions-for-pull-service)에 나열된 커뮤니티 솔루션 중 하나로 전환하기 시작하는 것이 좋습니다.

끌어오기 클라이언트를 설정 하기 전에 끌어오기 서버 설정 해야 합니다. 이 순서 필요 하지 않은 경우 문제 해결에 도움이 됩니다 하 고 등록 되었는지 확인 수 있습니다. 끌어오기 서버를 설정 하려면 다음 가이드를 사용할 수 있습니다.

- [DSC SMB 끌어오기 서버 설정](pullServerSmb.md)
- [DSC HTTP 끌어오기 서버 설정](pullServer.md)

각 대상 노드를 구성, 리소스를 다운로드 하 여 해당 상태를 보고할 수도 구성할 수 있습니다. 아래 섹션에서는 SMB 공유 또는 HTTP DSC 끌어오기 서버를 사용 하 여 끌어오기 클라이언트를 구성 하는 방법을 보여 줍니다. 노드의 LCM 새로 고쳐지면 모든 할당 된 구성을 다운로드 하는 구성 된 위치에 연락을 합니다. 노드에서 필요한 모든 리소스가 존재 하지 않는 경우 자동으로 다운로드 하는 구성 된 위치에서. 노드를 사용 하 여 구성 하는 경우는 [보고서 서버](reportServer.md), 다음 작업의 상태를 보고 합니다.

> **참고**: 이 항목은 PowerShell 5.0에 적용 됩니다. PowerShell 4.0에서 끌어오기 클라이언트를 설정하는 것에 대해서는 [PowerShell 4.0에서 구성 ID를 사용하여 끌어오기 클라이언트 설정](pullClientConfigID4.md)을 참조하세요.

## <a name="configure-the-pull-client-lcm"></a>끌어오기 클라이언트를 LCM 구성

라는 새 출력 폴더를 만들고 아래 예제 중 하나를 실행 **PullClientConfigID** 넣습니다 메타 구성 MOF 파일이 있습니다. 이 경우 메타 구성 MOF 파일의 이름은 `localhost.meta.mof`로 지정됩니다.

구성을 적용하려면 메타 구성 MOF 파일의 위치로 설정된 **Path**와 함께 **Set-DscLocalConfigurationManager** cmdlet을 호출합니다. 예:

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a>구성 ID

집합 아래 예제는 **ConfigurationID** 에 LCM의 속성을 **Guid** 이 목적을 위해 이전에 만든 것입니다. **ConfigurationID**는 LCM이 끌어오기 서버에서 적절한 구성의 찾는 데 사용하는 ID입니다. 끌어오기 서버의 구성 MOF 파일의 이름은 `ConfigurationID.mof`로 지정해야 합니다. 여기서 *ConfigurationID*는 대상 노드의 LCM의 **ConfigurationID** 속성의 값입니다. 자세한 내용은 참조 [끌어오기 서버 (v4/v5) 구성을 게시](publishConfigs.md)합니다.

임의 만들 수 있습니다 **Guid** 아래 또는 사용 하 여 예제를 사용 하 여 [New-guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.

```powershell
[System.Guid]::NewGuid()
```

사용에 대 한 자세한 내용은 **Guid** 환경에서 참조 [Guid에 대 한 계획](/powershell/dsc/secureserver#guids)합니다.

## <a name="set-up-a-pull-client-to-download-configurations"></a>구성 다운로드를 끌어오기 클라이언트 설정

각 클라이언트에서 구성 해야 **끌어오기** 모드의 구성이 저장 된 끌어오기 서버 url을 지정 합니다. 이를 수행하려면, 필요한 정보와 함께 LCM(로컬 구성 관리자)을 구성해야 합니다. LCM을 구성하려면 **DSCLocalConfigurationManager** 특성으로 데코레이팅된 특별한 형식의 구성을 만듭니다. LCM 구성에 대한 자세한 내용은 [로컬 구성 관리자 구성](../managing-nodes/metaConfig.md)을 참조하세요.

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

스크립트에서 **ConfigurationRepositoryWeb** 블록은 끌어오기 서버를 정의합니다. 합니다 **ServerUrl** DSC 끌어오기의 url을 지정

### <a name="smb-share"></a>SMB 공유

다음 스크립트는 구성을 끌어오고 다른 서버의 SMB 공유에서 LCM을 구성 `\\SMBPullServer\Pull`합니다.

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

스크립트에는 **ConfigurationRepositoryShare** 블록은 SMB 공유를 방금이 경우에 끌어오기 서버를 정의 합니다.

## <a name="set-up-a-pull-client-to-download-resources"></a>리소스를 다운로드 하 여 끌어오기 클라이언트 설정

만 지정한 경우는 **ConfigurationRepositoryWeb** 하거나 **ConfigurationRepositoryShare** (앞의 예와) LCM 구성에서 블록에서 끌어오기 클라이언트를 같은 리소스를 가져올 구성을 검색 하는 위치입니다. 또한 리소스에 대 한 별도 위치를 지정할 수 있습니다. 별도 서버로 리소스 위치를 지정 하려면 사용 합니다 **ResourceRepositoryWeb** 블록입니다. SMB 공유로 리소스 위치를 지정 하려면 사용 합니다 **ResourceRepositoryShare** 블록입니다.

> [!NOTE]
> 결합할 수 있습니다 **ConfigurationRepositoryWeb** 사용 하 여 **ResourceRepositoryShare** 하거나 **ConfigurationRepositoryShare** 사용 하 여 **ResourceRepositoryWeb** . 이 예가 아래에 표시 되지 않습니다.

### <a name="http-dsc-pull-server"></a>HTTP DSC 끌어오기 서버

다음 메타 구성에서 해당 구성을 가져오도록 끌어오기 클라이언트 구성 **Contoso-pullsrv** 에서 리소스 **Contoso-resourcesrv**합니다.

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

다음 예제에서는 SMB 공유에서 구성을 끌어오고 다른 서버의 클라이언트를 설정 하는 메타 구성을 `\\SMBPullServer\Configurations`, 및 SMB 공유에서 리소스 `\\SMBPullServer\Resources`합니다.

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

#### <a name="automatically-download-resources-in-push-mode"></a>밀어넣기 모드에서 리소스를 자동으로 다운로드

PowerShell 5.0부터 끌어오기 클라이언트에서에서 다운로드할 수 모듈 SMB 공유를 사용 하도록 구성 된 경우에 **푸시** 모드입니다. 여기서 하지 않으려는 경우 끌어오기 서버를 설정 하는 시나리오에서 특히 유용 합니다. 합니다 **ResourceRepositoryShare** 블록을 지정 하지 않고 사용할 수는 **ConfigurationRepositoryShare**합니다. 다음 예제에서는 SMB 공유에서 리소스를 가져올 클라이언트를 설정 하는 메타 구성을 `\\SMBPullServer\Resources`합니다. 노드가 **PUSHED** 구성을 자동으로 다운로드를 필요한 모든 리소스에서 지정 된 공유 합니다.

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

## <a name="set-up-a-pull-client-to-report-status"></a>상태 보고에 대 한 끌어오기 클라이언트 설정

기본적으로 노드 구성된 끌어오기 서버에 보고서를 보내지 않습니다. 구성, 리소스 및 보고에 단일 끌어오기 서버를 사용할 수 있지만 **ReportRepositoryWeb** 블록을 만들어 보고를 설정해야 합니다.

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

보고서 서버는 SMB 공유 일 수 없습니다.

## <a name="next-steps"></a>다음 단계

끌어오기 클라이언트를 구성한 후 다음 단계를 수행 하려면 다음 가이드를 사용할 수 있습니다.

- [끌어오기 서버에 구성 게시(v4/v5)](publishConfigs.md)
- [리소스 패키지 및 끌어오기 서버에 업로드(v4)](package-upload-resources.md)

## <a name="see-also"></a>참고 항목

* [Setting up a pull client with configuration names(구성 이름을 사용하여 끌어오기 클라이언트 설정)](pullClientConfigNames.md)
