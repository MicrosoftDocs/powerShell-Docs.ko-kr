---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: PowerShell 4.0에서 구성 ID를 사용하여 끌어오기 클라이언트 설정
ms.openlocfilehash: 9259c624c8725f7d76f61e9ad7caa42e1bfa308c
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2020
ms.locfileid: "71955150"
---
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-40"></a>PowerShell 4.0에서 구성 ID를 사용하여 끌어오기 클라이언트 설정

>적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0

> [!IMPORTANT]
> 끌어오기 서버(Windows 기능 *DSC-Service*)는 Windows Server의 지원되는 구성 요소이지만 새로운 기능을 제공할 계획은 없습니다. 관리되는 클라우드를 [Azure Automation DSC](/azure/automation/automation-dsc-getting-started)(Windows Server에 끌어오기 서버 이외의 기능 포함) 또는 [여기](pullserver.md#community-solutions-for-pull-service)에 나열된 커뮤니티 솔루션 중 하나로 전환하기 시작하는 것이 좋습니다.

끌어오기 클라이언트를 설정하기 전에 끌어오기 서버를 설정해야 합니다. 이 순서가 필요하지 않더라도 문제 해결에 도움이 되고 등록에 성공했는지 확인할 수 있습니다. 끌어오기 서버를 설정하려면 다음 가이드를 사용하면 됩니다.

- [DSC SMB 끌어오기 서버 설정](pullServerSmb.md)
- [DSC HTTP 끌어오기 서버 설정](pullServer.md)

구성, 리소스를 다운로드하고 해당 상태를 보고하도록 각 대상 노드를 구성할 수 있습니다. 아래 섹션에서는 SMB 공유 또는 HTTP DSC 끌어오기 서버를 사용하여 끌어오기 클라이언트를 구성하는 방법을 보여줍니다. 노드의 LCM가 새로 고쳐지면 구성된 위치에 도달하여 할당된 구성을 다운로드합니다. 노드에서 필수 리소스가 존재하지 않는 경우 구성된 위치로부터 자동으로 다운로드합니다. 노드가 [보고서 서버](reportServer.md)를 사용하여 구성되는 경우 해당 작업의 상태를 보고합니다.

## <a name="configure-the-pull-client-lcm"></a>끌어오기 클라이언트 LCM 구성

아래 예제 중 하나가 실행되면 **PullClientConfigID**라는 새 출력 폴더가 생성되고, 거기에 메타 구성 MOF 파일을 만듭니다. 이 경우 메타 구성 MOF 파일의 이름은 `localhost.meta.mof`로 지정됩니다.

구성을 적용하려면 메타 구성 MOF 파일의 위치로 설정된 **Path**와 함께 **Set-DscLocalConfigurationManager** cmdlet을 호출합니다. 다음은 그 예입니다.

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a>구성 ID

아래 예제에서는 이전에 이 목적으로 만들어진 LCM의 **ConfigurationID** 속성을 **Guid**로 설정합니다. **ConfigurationID**는 LCM이 끌어오기 서버에서 적절한 구성의 찾는 데 사용하는 ID입니다. 끌어오기 서버의 구성 MOF 파일의 이름은 `ConfigurationID.mof`로 지정해야 합니다. 여기서 *ConfigurationID*는 대상 노드의 LCM의 **ConfigurationID** 속성의 값입니다. 자세한 내용은 [끌어오기 서버에 구성 게시(v4/v5)](publishConfigs.md)를 참조하세요.

아래 예제를 사용하여 임의의 **Guid**를 만들 수 있습니다.

```powershell
[System.Guid]::NewGuid()
```

## <a name="set-up-a-pull-client-to-download-configurations"></a>구성을 다운로드하도록 끌어오기 클라이언트 설정

각 클라이언트는 **끌어오기** 모드로 구성되고 구성이 저장된 끌어오기 서버 URL이 지정되어야 합니다. 이를 수행하려면, 필요한 정보와 함께 LCM(로컬 구성 관리자)을 구성해야 합니다. LCM을 구성하려면 **LocalConfigurationManager** 블록을 사용하여 특별한 형식의 구성을 만듭니다. LCM 구성에 대한 자세한 내용은 [로컬 구성 관리자 구성](../managing-nodes/metaConfig4.md)을 참조하세요.

## <a name="http-dsc-pull-server"></a>HTTP DSC 끌어오기 서버

끌어오기 서버가 웹 서비스로 설정되는 경우 **DownloadManagerName**을 **WebDownloadManager**로 설정합니다. **WebDownloadManager**를 사용하려면 **DownloadManagerCustomData** 키에 대한 **ServerUrl**을 지정해야 합니다. 아래 예제와 같이 **AllowUnsecureConnection**의 값을 지정할 수도 있습니다. 다음 스크립트는 "PullServer"라는 서버에서 구성을 끌어오도록 LCM을 구성합니다.

```powershell
Configuration PullClientConfigId
{
    LocalConfigurationManager
    {
        ConfigurationID = "1C707B86-EF8E-4C29-B7C1-34DA2190AE24";
        RefreshMode = "PULL";
        DownloadManagerName = "WebDownloadManager";
        RebootNodeIfNeeded = $true;
        RefreshFrequencyMins = 30;
        ConfigurationModeFrequencyMins = 30;
        ConfigurationMode = "ApplyAndAutoCorrect";
        DownloadManagerCustomData = @{ServerUrl = "http://PullServer:8080/PSDSCPullServer/PSDSCPullServer.svc"; AllowUnsecureConnection = "TRUE"}
    }
}
PullClientConfigId -Output "."
```

## <a name="smb-share"></a>SMB 공유

끌어오기 서버가 웹 서비스가 아닌 SMB 파일 공유로 설정된 경우 **DownloadManagerName**을 **WebDownLoadManager** 대신 **DscFileDownloadManager**로 설정합니다. **DscFileDownloadManager**를 사용하려면 **DownloadManagerCustomData**에서 **SourcePath** 속성을 지정해야 합니다. 다음 스크립트에서는 "CONTOSO-SERVER"라는 서버에서 "SmbDscShare"라는 SMB 공유의 구성을 끌어오도록 LCM을 구성합니다.

```powershell
Configuration PullClientConfigId
{
    LocalConfigurationManager
    {
        ConfigurationID = "1C707B86-EF8E-4C29-B7C1-34DA2190AE24";
        RefreshMode = "PULL";
        DownloadManagerName = "DscFileDownloadManager";
        RebootNodeIfNeeded = $true;
        RefreshFrequencyMins = 30;
        ConfigurationModeFrequencyMins = 30;
        ConfigurationMode = "ApplyAndAutoCorrect";
        DownloadManagerCustomData = @{ServerUrl = "\\CONTOSO-SERVER\SmbDscShare"}
    }
}
PullClientConfigId -Output "."
```

## <a name="next-steps"></a>다음 단계

끌어오기 클라이언트를 구성하면 다음 가이드를 사용하여 다음 단계를 수행할 수 있습니다.

- [끌어오기 서버에 구성 게시(v4/v5)](publishConfigs.md)
- [리소스 패키지 및 끌어오기 서버에 업로드(v4)](package-upload-resources.md)

## <a name="see-also"></a>참고 항목

- [DSC 웹 끌어오기 서버 설정](pullServer.md)
- [DSC SMB 끌어오기 서버 설정](pullServerSMB.md)
