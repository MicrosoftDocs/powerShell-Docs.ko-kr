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
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-40"></a><span data-ttu-id="85f1f-103">PowerShell 4.0에서 구성 Id를 사용 하 여 끌어오기 클라이언트 설정</span><span class="sxs-lookup"><span data-stu-id="85f1f-103">Set up a Pull Client using Configuration IDs in PowerShell 4.0</span></span>

><span data-ttu-id="85f1f-104">적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="85f1f-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="85f1f-105">끌어오기 서버(Windows 기능 *DSC-Service*)는 Windows Server의 지원되는 구성 요소이지만 새로운 기능을 제공할 계획은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="85f1f-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="85f1f-106">관리되는 클라우드를 [Azure Automation DSC](/azure/automation/automation-dsc-getting-started)(Windows Server에 끌어오기 서버 이외의 기능 포함) 또는 [여기](pullserver.md#community-solutions-for-pull-service)에 나열된 커뮤니티 솔루션 중 하나로 전환하기 시작하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="85f1f-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="85f1f-107">끌어오기 클라이언트를 설정 하기 전에 끌어오기 서버 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="85f1f-107">Before setting up a pull client, you should set up a pull server.</span></span> <span data-ttu-id="85f1f-108">이 순서 필요 하지 않은 경우 문제 해결에 도움이 됩니다 하 고 등록 되었는지 확인 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85f1f-108">Though this order is not required, it helps with troubleshooting, and helps you ensure that the registration was successful.</span></span> <span data-ttu-id="85f1f-109">끌어오기 서버를 설정 하려면 다음 가이드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85f1f-109">To set up a pull server, you can use the following guides:</span></span>

- [<span data-ttu-id="85f1f-110">DSC SMB 끌어오기 서버 설정</span><span class="sxs-lookup"><span data-stu-id="85f1f-110">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="85f1f-111">DSC HTTP 끌어오기 서버 설정</span><span class="sxs-lookup"><span data-stu-id="85f1f-111">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="85f1f-112">각 대상 노드를 구성, 리소스를 다운로드 하 여 해당 상태를 보고할 수도 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85f1f-112">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="85f1f-113">아래 섹션에서는 SMB 공유 또는 HTTP DSC 끌어오기 서버를 사용 하 여 끌어오기 클라이언트를 구성 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="85f1f-113">The sections below show you how to configure a pull client with an SMB share or HTTP DSC Pull Server.</span></span> <span data-ttu-id="85f1f-114">노드의 LCM 새로 고쳐지면 모든 할당 된 구성을 다운로드 하는 구성 된 위치에 연락을 합니다.</span><span class="sxs-lookup"><span data-stu-id="85f1f-114">When the Node's LCM refreshes, it will reach out to the configured location to download any assigned configurations.</span></span> <span data-ttu-id="85f1f-115">노드에서 필요한 모든 리소스가 존재 하지 않는 경우 자동으로 다운로드 하는 구성 된 위치에서.</span><span class="sxs-lookup"><span data-stu-id="85f1f-115">If any required resources do not exist on the Node, it will automatically download them from the configured location.</span></span> <span data-ttu-id="85f1f-116">노드를 사용 하 여 구성 하는 경우는 [보고서 서버](reportServer.md), 다음 작업의 상태를 보고 합니다.</span><span class="sxs-lookup"><span data-stu-id="85f1f-116">If the Node is configured with a [Report Server](reportServer.md), it will then report the status of the operation.</span></span>

## <a name="configure-the-pull-client-lcm"></a><span data-ttu-id="85f1f-117">끌어오기 클라이언트를 LCM 구성</span><span class="sxs-lookup"><span data-stu-id="85f1f-117">Configure the pull client LCM</span></span>

<span data-ttu-id="85f1f-118">라는 새 출력 폴더를 만들고 아래 예제 중 하나를 실행 **PullClientConfigID** 넣습니다 메타 구성 MOF 파일이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85f1f-118">Executing any of the examples below creates a new output folder named **PullClientConfigID** and puts a metaconfiguration MOF file there.</span></span> <span data-ttu-id="85f1f-119">이 경우 메타 구성 MOF 파일의 이름은 `localhost.meta.mof`로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="85f1f-119">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="85f1f-120">구성을 적용하려면 메타 구성 MOF 파일의 위치로 설정된 **Path**와 함께 **Set-DscLocalConfigurationManager** cmdlet을 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="85f1f-120">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span> <span data-ttu-id="85f1f-121">예:</span><span class="sxs-lookup"><span data-stu-id="85f1f-121">For example:</span></span>

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a><span data-ttu-id="85f1f-122">구성 ID</span><span class="sxs-lookup"><span data-stu-id="85f1f-122">Configuration ID</span></span>

<span data-ttu-id="85f1f-123">집합 아래 예제는 **ConfigurationID** 에 LCM의 속성을 **Guid** 이 목적을 위해 이전에 만든 것입니다.</span><span class="sxs-lookup"><span data-stu-id="85f1f-123">The examples below set the **ConfigurationID** property of the LCM to a **Guid** that had been previously created for this purpose.</span></span> <span data-ttu-id="85f1f-124">**ConfigurationID**는 LCM이 끌어오기 서버에서 적절한 구성의 찾는 데 사용하는 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="85f1f-124">The **ConfigurationID** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="85f1f-125">끌어오기 서버의 구성 MOF 파일의 이름은 `ConfigurationID.mof`로 지정해야 합니다. 여기서 *ConfigurationID*는 대상 노드의 LCM의 **ConfigurationID** 속성의 값입니다.</span><span class="sxs-lookup"><span data-stu-id="85f1f-125">The configuration MOF file on the pull server must be named `ConfigurationID.mof`, where *ConfigurationID* is the value of the **ConfigurationID** property of the target node's LCM.</span></span> <span data-ttu-id="85f1f-126">자세한 내용은 [끌어오기 서버 (v4/v5) 구성을 게시](publishConfigs.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="85f1f-126">For more information, see [Publish Configurations to a Pull Server (v4/v5)](publishConfigs.md).</span></span>

<span data-ttu-id="85f1f-127">임의 만들 수 있습니다 **Guid** 아래 예제를 사용 하 여 합니다.</span><span class="sxs-lookup"><span data-stu-id="85f1f-127">You can create a random **Guid** using the example below.</span></span>

```powershell
[System.Guid]::NewGuid()
```

## <a name="set-up-a-pull-client-to-download-configurations"></a><span data-ttu-id="85f1f-128">구성 다운로드를 끌어오기 클라이언트 설정</span><span class="sxs-lookup"><span data-stu-id="85f1f-128">Set up a Pull Client to download Configurations</span></span>

<span data-ttu-id="85f1f-129">각 클라이언트에서 구성 해야 **끌어오기** 모드의 구성이 저장 된 끌어오기 서버 url을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="85f1f-129">Each client must be configured in **Pull** mode and given the pull server url where its configuration is stored.</span></span> <span data-ttu-id="85f1f-130">이를 수행하려면, 필요한 정보와 함께 LCM(로컬 구성 관리자)을 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="85f1f-130">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="85f1f-131">특별 한 형식의 구성 사용 하 여 만들 있습니다 LCM을 구성 하는 **LocalConfigurationManager** 블록입니다.</span><span class="sxs-lookup"><span data-stu-id="85f1f-131">To configure the LCM, you create a special type of configuration, with a **LocalConfigurationManager** block.</span></span> <span data-ttu-id="85f1f-132">LCM 구성에 대한 자세한 내용은 [로컬 구성 관리자 구성](../managing-nodes/metaConfig4.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="85f1f-132">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig4.md).</span></span>

## <a name="http-dsc-pull-server"></a><span data-ttu-id="85f1f-133">HTTP DSC 끌어오기 서버</span><span class="sxs-lookup"><span data-stu-id="85f1f-133">HTTP DSC Pull Server</span></span>

<span data-ttu-id="85f1f-134">끌어오기 서버를 웹 서비스로 설정 된 경우 설정 합니다 **DownloadManagerName** 에 **WebDownloadManager**합니다.</span><span class="sxs-lookup"><span data-stu-id="85f1f-134">If the pull server is set up as a web service, you set the **DownloadManagerName** to **WebDownloadManager**.</span></span> <span data-ttu-id="85f1f-135">**WebDownloadManager** 을 지정 해야는 **ServerUrl** 에 **DownloadManagerCustomData** 키입니다.</span><span class="sxs-lookup"><span data-stu-id="85f1f-135">The **WebDownloadManager** requires that you specify a **ServerUrl** to the **DownloadManagerCustomData** key.</span></span> <span data-ttu-id="85f1f-136">에 대 한 값을 지정할 수도 있습니다 **AllowUnsecureConnection**아래 예제와 같이 합니다.</span><span class="sxs-lookup"><span data-stu-id="85f1f-136">You can also specify a value for **AllowUnsecureConnection**, as in the example below.</span></span> <span data-ttu-id="85f1f-137">다음 스크립트는 "PullServer"라는 서버에서 구성을 끌어오도록 LCM을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="85f1f-137">The following script configures the LCM to pull configurations from a server named "PullServer".</span></span>

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

## <a name="smb-share"></a><span data-ttu-id="85f1f-138">SMB 공유</span><span class="sxs-lookup"><span data-stu-id="85f1f-138">SMB Share</span></span>

<span data-ttu-id="85f1f-139">끌어오기 서버가 웹 서비스가 아닌 SMB 파일 공유로 설정 된 경우 설정 합니다 **DownloadManagerName** 하 **DscFileDownloadManager** 대신 **WebDownLoadManager**.</span><span class="sxs-lookup"><span data-stu-id="85f1f-139">If the pull server is set up as an SMB file share, rather than a web service, you set the **DownloadManagerName** to **DscFileDownloadManager** rather than the **WebDownLoadManager**.</span></span> <span data-ttu-id="85f1f-140">**DscFileDownloadManager** 을 지정 해야는 **SourcePath** 속성에는 **DownloadManagerCustomData**합니다.</span><span class="sxs-lookup"><span data-stu-id="85f1f-140">The **DscFileDownloadManager** requires that you specify a **SourcePath** property in the **DownloadManagerCustomData**.</span></span> <span data-ttu-id="85f1f-141">다음 스크립트에서는 "CONTOSO-SERVER"라는 서버에서 "SmbDscShare"라는 SMB 공유의 구성을 끌어오도록 LCM을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="85f1f-141">The following script configures the LCM to pull configurations from an SMB share named "SmbDscShare" on a server named "CONTOSO-SERVER".</span></span>

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

## <a name="next-steps"></a><span data-ttu-id="85f1f-142">다음 단계</span><span class="sxs-lookup"><span data-stu-id="85f1f-142">Next Steps</span></span>

<span data-ttu-id="85f1f-143">끌어오기 클라이언트를 구성한 후 다음 단계를 수행 하려면 다음 가이드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85f1f-143">Once the pull client has been configured, you can use the following guides to perform the next steps:</span></span>

- [<span data-ttu-id="85f1f-144">끌어오기 서버에 구성 게시(v4/v5)</span><span class="sxs-lookup"><span data-stu-id="85f1f-144">Publish Configurations to a Pull Server (v4/v5)</span></span>](publishConfigs.md)
- [<span data-ttu-id="85f1f-145">리소스 패키지 및 끌어오기 서버에 업로드(v4)</span><span class="sxs-lookup"><span data-stu-id="85f1f-145">Package and Upload Resources to a Pull Server (v4)</span></span>](package-upload-resources.md)

## <a name="see-also"></a><span data-ttu-id="85f1f-146">참고 항목</span><span class="sxs-lookup"><span data-stu-id="85f1f-146">See Also</span></span>

- [<span data-ttu-id="85f1f-147">DSC 웹 끌어오기 서버 설정</span><span class="sxs-lookup"><span data-stu-id="85f1f-147">Set up a DSC web pull server</span></span>](pullServer.md)
- [<span data-ttu-id="85f1f-148">DSC SMB 끌어오기 서버 설정</span><span class="sxs-lookup"><span data-stu-id="85f1f-148">Set up a DSC SMB pull server</span></span>](pullServerSMB.md)
