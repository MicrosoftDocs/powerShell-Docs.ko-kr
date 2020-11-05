---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: PowerShell 5.0 이상에서 구성 이름을 사용하여 끌어오기 클라이언트 설정
description: 이 문서에서는 PowerShell 5.0 이상에서 구성 이름을 사용하여 끌어오기 클라이언트를 설정하는 방법을 설명합니다.
ms.openlocfilehash: db2b08605dd8bc7e48d9d5153861ce9b36118e21
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92644908"
---
# <a name="set-up-a-pull-client-using-configuration-names-in-powershell-50-and-later"></a>PowerShell 5.0 이상에서 구성 이름을 사용하여 끌어오기 클라이언트 설정

> 적용 대상: Windows PowerShell 5.0

> [!IMPORTANT]
> 끌어오기 서버(Windows 기능 *DSC-Service* )는 Windows Server의 지원되는 구성 요소이지만 새로운 기능을 제공할 계획은 없습니다. 관리되는 클라우드를 [Azure Automation DSC](/azure/automation/automation-dsc-getting-started)(Windows Server에 끌어오기 서버 이외의 기능 포함) 또는 [여기](pullserver.md#community-solutions-for-pull-service)에 나열된 커뮤니티 솔루션 중 하나로 전환하기 시작하는 것이 좋습니다.

끌어오기 클라이언트를 설정하기 전에 끌어오기 서버를 설정해야 합니다. 이 순서가 필요하지 않더라도 문제 해결에 도움이 되고 등록에 성공했는지 확인할 수 있습니다. 끌어오기 서버를 설정하려면 다음 가이드를 사용하면 됩니다.

- [DSC SMB 끌어오기 서버 설정](pullServerSmb.md)
- [DSC HTTP 끌어오기 서버 설정](pullServer.md)

구성, 리소스를 다운로드하고 해당 상태를 보고하도록 각 대상 노드를 구성할 수 있습니다. 아래 섹션에서는 SMB 공유 또는 HTTP DSC 끌어오기 서버를 사용하여 끌어오기 클라이언트를 구성하는 방법을 보여줍니다. 노드의 LCM가 새로 고쳐지면 구성된 위치에 도달하여 할당된 구성을 다운로드합니다. 노드에서 필수 리소스가 존재하지 않는 경우 구성된 위치로부터 자동으로 다운로드합니다. 노드가 [보고서 서버](reportServer.md)를 사용하여 구성되는 경우 해당 작업의 상태를 보고합니다.

> [!NOTE]
> 이 토픽은 PowerShell 5.0에 적용됩니다. PowerShell 4.0에서 끌어오기 클라이언트를 설정하는 방법에 대한 정보는 [PowerShell 4.0에서 구성 ID를 사용하여 끌어오기 클라이언트 설정](pullClientConfigID4.md)을 참조하세요.

## <a name="configure-the-pull-client-lcm"></a>끌어오기 클라이언트 LCM 구성

아래 예제 중 하나가 실행되면 **PullClientConfigName** 이라는 새 출력 폴더가 생성되고, 거기에 메타 구성 MOF 파일을 만듭니다. 이 경우 메타 구성 MOF 파일의 이름은 `localhost.meta.mof`로 지정됩니다.

구성을 적용하려면 메타 구성 MOF 파일의 위치로 설정된 **Path** 와 함께 **Set-DscLocalConfigurationManager** cmdlet을 호출합니다. 예를 들어:

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigName –Verbose.
```

## <a name="configuration-name"></a>구성 이름

아래 예제에서는 LCM의 **ConfigurationName** 속성을 이전에 컴파일된 구성의 이름(이 목적을 위해 생성됨)으로 설정합니다. **ConfigurationName** 은 LCM이 끌어오기 서버에서 적절한 구성을 찾는 데 사용하는 항목입니다. 끌어오기 서버의 구성 MOF 파일의 이름은 `<ConfigurationName>.mof`입니다(이 경우에 "ClientConfig.mof"). 자세한 내용은 [끌어오기 서버에 구성 게시(v4/v5)](publishConfigs.md)를 참조하세요.

## <a name="set-up-a-pull-client-to-download-configurations"></a>구성을 다운로드하도록 끌어오기 클라이언트 설정

각 클라이언트는 **끌어오기** 모드로 구성되고 구성이 저장된 끌어오기 서버 URL이 지정되어야 합니다. 이를 수행하려면, 필요한 정보와 함께 LCM(로컬 구성 관리자)을 구성해야 합니다. LCM을 구성하려면 **DSCLocalConfigurationManager** 특성으로 데코레이팅된 특별한 형식의 구성을 만듭니다. LCM 구성에 대한 자세한 내용은 [로컬 구성 관리자 구성](../managing-nodes/metaConfig.md)을 참조하세요.

다음 스크립트는 "CONTOSO-PullSrv"라는 서버에서 구성을 끌어오도록 LCM을 구성합니다.

- 스크립트에서 **ConfigurationRepositoryWeb** 블록은 끌어오기 서버를 정의합니다. **ServerURL** 속성은 끌어오기 서버에 대한 엔드포인트를 지정합니다.

- **RegistrationKey** 속성은 끌어오기 서버에 대한 모든 클라이언트 노드와 해당 끌어오기 서버 간의 공유 키입니다. 동일한 값이 끌어오기 서버에 있는 파일에 저장됩니다. > [!NOTE] > 등록 키는 **웹** 끌어오기 서버에서만 작동합니다. **SMB** 끌어오기 서버에는 여전히 **ConfigurationID** 를 사용해야 합니다. > **ConfigurationID** 를 사용하여 끌어오기 서버를 구성하는 방법은 [구성 ID를 사용하여 끌어오기 클라이언트 설정](pullClientConfigId.md)을 참조하세요.

- **ConfigurationNames** 속성은 클라이언트 노드용으로 의도된 구성의 이름을 지정하는 배열입니다. >**참고:** **ConfigurationNames** 에 둘 이상의 값을 지정하는 경우 구성에서 **PartialConfiguration** 블록도 지정해야 합니다. > 부분 구성에 대한 자세한 내용은 [PowerShell Desired State Configuration 부분 구성](partialConfigs.md)을 참조하세요.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
            ConfigurationNames = @('ClientConfig')
        }
    }
}
PullClientConfigNames
```

## <a name="set-up-a-pull-client-to-download-resources"></a>리소스를 다운로드하도록 끌어오기 클라이언트 설정

앞의 예와 같이 LCM 구성에서 **ConfigurationRepositoryWeb** 또는 **ConfigurationRepositoryShare** 블록만 지정하는 경우 끌어오기 클라이언트는 ".mof" 파일이 저장된 동일한 위치로부터 리소스를 끌어옵니다. 클라이언트가 리소스를 다운로드할 수 있는 다른 위치를 지정할 수도 있습니다. 리소스 서버를 지정하려면, **ResourceRepositoryWeb** (웹 끌어오기 서버용) 및 **ResourceRepositoryShare** (SMB 끌어오기 서버용) 블록을 사용합니다.

다음 예제에서는 끌어오기 서버로부터 구성을 다운로드하고, SMB 공유로부터 리소스를 다운로드하도록 클라이언트를 설정하는 메타 구성을 보여줍니다.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }

        ResourceRepositoryShare SMBResources
        {
            SourcePath = '\\SMBPullServer\Resources'
        }
    }
}
PullClientConfigNames
```

## <a name="set-up-a-pull-client-to-report-status"></a>상태를 보고하도록 끌어오기 클라이언트 설정

구성, 리소스 및 보고에 단일 끌어오기 서버를 사용할 수 있습니다. 보고는 기본적으로 클라이언트에서 구성되지 않습니다. 상태를 보고하도록 클라이언트를 구성하려면 **ReportRepositoryWeb** 블록을 만들어야 합니다. 다음 예제에서는 구성 및 리소스를 끌어오고 보고 데이터를 단일 서버에 보내도록 클라이언트를 설정하는 메타 구성을 보여 줍니다.

> [!NOTE]
> 보고서 서버는 SMB 공유일 수 없습니다.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }

        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }
    }
}
PullClientConfigNames
```

## <a name="see-also"></a>참고 항목

- [구성 ID를 사용하여 끌어오기 클라이언트 설정](PullClientConfigNames.md)
- [DSC 웹 끌어오기 서버 설정](pullServer.md)
