---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: PowerShell 4.0에서 구성 Id를 사용 하 여 끌어오기 클라이언트 설정
ms.openlocfilehash: 9adc767e91ff19d373c122a0d493e7b8703d5476
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402991"
---
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-40"></a>PowerShell 4.0에서 구성 Id를 사용 하 여 끌어오기 클라이언트 설정

>적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0

> [!IMPORTANT]
> 끌어오기 서버(Windows 기능 *DSC-Service*)는 Windows Server의 지원되는 구성 요소이지만 새로운 기능을 제공할 계획은 없습니다. 관리되는 클라우드를 [Azure Automation DSC](/azure/automation/automation-dsc-getting-started)(Windows Server에 끌어오기 서버 이외의 기능 포함) 또는 [여기](pullserver.md#community-solutions-for-pull-service)에 나열된 커뮤니티 솔루션 중 하나로 전환하기 시작하는 것이 좋습니다.

끌어오기 클라이언트를 설정 하기 전에 끌어오기 서버 설정 해야 합니다. 이 순서 필요 하지 않은 경우 문제 해결에 도움이 됩니다 하 고 등록 되었는지 확인 수 있습니다. 끌어오기 서버를 설정 하려면 다음 가이드를 사용할 수 있습니다.

- [DSC SMB 끌어오기 서버 설정](pullServerSmb.md)
- [DSC HTTP 끌어오기 서버 설정](pullServer.md)

각 대상 노드를 구성, 리소스를 다운로드 하 여 해당 상태를 보고할 수도 구성할 수 있습니다. 아래 섹션에서는 SMB 공유 또는 HTTP DSC 끌어오기 서버를 사용 하 여 끌어오기 클라이언트를 구성 하는 방법을 보여 줍니다. 노드의 LCM 새로 고쳐지면 모든 할당 된 구성을 다운로드 하는 구성 된 위치에 연락을 합니다. 노드에서 필요한 모든 리소스가 존재 하지 않는 경우 자동으로 다운로드 하는 구성 된 위치에서. 노드를 사용 하 여 구성 하는 경우는 [보고서 서버](reportServer.md), 다음 작업의 상태를 보고 합니다.

## <a name="configure-the-pull-client-lcm"></a>끌어오기 클라이언트를 LCM 구성

라는 새 출력 폴더를 만들고 아래 예제 중 하나를 실행 **PullClientConfigID** 넣습니다 메타 구성 MOF 파일이 있습니다. 이 경우 메타 구성 MOF 파일의 이름은 `localhost.meta.mof`로 지정됩니다.

구성을 적용하려면 메타 구성 MOF 파일의 위치로 설정된 **Path**와 함께 **Set-DscLocalConfigurationManager** cmdlet을 호출합니다. 예:

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a>구성 ID

집합 아래 예제는 **ConfigurationID** 에 LCM의 속성을 **Guid** 이 목적을 위해 이전에 만든 것입니다. **ConfigurationID**는 LCM이 끌어오기 서버에서 적절한 구성의 찾는 데 사용하는 ID입니다. 끌어오기 서버의 구성 MOF 파일의 이름은 `ConfigurationID.mof`로 지정해야 합니다. 여기서 *ConfigurationID*는 대상 노드의 LCM의 **ConfigurationID** 속성의 값입니다. 자세한 내용은 [끌어오기 서버 (v4/v5) 구성을 게시](publishConfigs.md)합니다.

임의 만들 수 있습니다 **Guid** 아래 예제를 사용 하 여 합니다.

```powershell
[System.Guid]::NewGuid()
```

## <a name="set-up-a-pull-client-to-download-configurations"></a>구성 다운로드를 끌어오기 클라이언트 설정

각 클라이언트에서 구성 해야 **끌어오기** 모드의 구성이 저장 된 끌어오기 서버 url을 지정 합니다. 이를 수행하려면, 필요한 정보와 함께 LCM(로컬 구성 관리자)을 구성해야 합니다. 특별 한 형식의 구성 사용 하 여 만들 있습니다 LCM을 구성 하는 **LocalConfigurationManager** 블록입니다. LCM 구성에 대한 자세한 내용은 [로컬 구성 관리자 구성](../managing-nodes/metaConfig4.md)을 참조하세요.

## <a name="http-dsc-pull-server"></a>HTTP DSC 끌어오기 서버

끌어오기 서버를 웹 서비스로 설정 된 경우 설정 합니다 **DownloadManagerName** 에 **WebDownloadManager**합니다. **WebDownloadManager** 을 지정 해야는 **ServerUrl** 에 **DownloadManagerCustomData** 키입니다. 에 대 한 값을 지정할 수도 있습니다 **AllowUnsecureConnection**아래 예제와 같이 합니다. 다음 스크립트는 "PullServer"라는 서버에서 구성을 끌어오도록 LCM을 구성합니다.

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
        DownloadManagerCustomData = @{ServerUrl = "http://PullServer:8080/PSDSCPullServer/PSDSCPullServer.svc"; AllowUnsecureConnection = “TRUE”}
    }
}
PullClientConfigId -Output "."
```

## <a name="smb-share"></a>SMB 공유

끌어오기 서버가 웹 서비스가 아닌 SMB 파일 공유로 설정 된 경우 설정 합니다 **DownloadManagerName** 하 **DscFileDownloadManager** 대신 **WebDownLoadManager**. **DscFileDownloadManager** 을 지정 해야는 **SourcePath** 속성에는 **DownloadManagerCustomData**합니다. 다음 스크립트에서는 "CONTOSO-SERVER"라는 서버에서 "SmbDscShare"라는 SMB 공유의 구성을 끌어오도록 LCM을 구성합니다.

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

끌어오기 클라이언트를 구성한 후 다음 단계를 수행 하려면 다음 가이드를 사용할 수 있습니다.

- [끌어오기 서버에 구성 게시(v4/v5)](publishConfigs.md)
- [리소스 패키지 및 끌어오기 서버에 업로드(v4)](package-upload-resources.md)

## <a name="see-also"></a>참고 항목

- [DSC 웹 끌어오기 서버 설정](pullServer.md)
- [DSC SMB 끌어오기 서버 설정](pullServerSMB.md)
