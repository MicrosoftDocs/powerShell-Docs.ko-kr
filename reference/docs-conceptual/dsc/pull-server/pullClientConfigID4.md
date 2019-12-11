---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: PowerShell 4.0에서 구성 ID를 사용하여 끌어오기 클라이언트 설정
ms.openlocfilehash: 9259c624c8725f7d76f61e9ad7caa42e1bfa308c
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "71955150"
---
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-40"></a><span data-ttu-id="2d3d6-103">PowerShell 4.0에서 구성 ID를 사용하여 끌어오기 클라이언트 설정</span><span class="sxs-lookup"><span data-stu-id="2d3d6-103">Set up a Pull Client using Configuration IDs in PowerShell 4.0</span></span>

><span data-ttu-id="2d3d6-104">적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="2d3d6-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2d3d6-105">끌어오기 서버(Windows 기능 *DSC-Service*)는 Windows Server의 지원되는 구성 요소이지만 새로운 기능을 제공할 계획은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2d3d6-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="2d3d6-106">관리되는 클라우드를 [Azure Automation DSC](/azure/automation/automation-dsc-getting-started)(Windows Server에 끌어오기 서버 이외의 기능 포함) 또는 [여기](pullserver.md#community-solutions-for-pull-service)에 나열된 커뮤니티 솔루션 중 하나로 전환하기 시작하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="2d3d6-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="2d3d6-107">끌어오기 클라이언트를 설정하기 전에 끌어오기 서버를 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d3d6-107">Before setting up a pull client, you should set up a pull server.</span></span> <span data-ttu-id="2d3d6-108">이 순서가 필요하지 않더라도 문제 해결에 도움이 되고 등록에 성공했는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d3d6-108">Though this order is not required, it helps with troubleshooting, and helps you ensure that the registration was successful.</span></span> <span data-ttu-id="2d3d6-109">끌어오기 서버를 설정하려면 다음 가이드를 사용하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2d3d6-109">To set up a pull server, you can use the following guides:</span></span>

- [<span data-ttu-id="2d3d6-110">DSC SMB 끌어오기 서버 설정</span><span class="sxs-lookup"><span data-stu-id="2d3d6-110">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="2d3d6-111">DSC HTTP 끌어오기 서버 설정</span><span class="sxs-lookup"><span data-stu-id="2d3d6-111">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="2d3d6-112">구성, 리소스를 다운로드하고 해당 상태를 보고하도록 각 대상 노드를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d3d6-112">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="2d3d6-113">아래 섹션에서는 SMB 공유 또는 HTTP DSC 끌어오기 서버를 사용하여 끌어오기 클라이언트를 구성하는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="2d3d6-113">The sections below show you how to configure a pull client with an SMB share or HTTP DSC Pull Server.</span></span> <span data-ttu-id="2d3d6-114">노드의 LCM가 새로 고쳐지면 구성된 위치에 도달하여 할당된 구성을 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="2d3d6-114">When the Node's LCM refreshes, it will reach out to the configured location to download any assigned configurations.</span></span> <span data-ttu-id="2d3d6-115">노드에서 필수 리소스가 존재하지 않는 경우 구성된 위치로부터 자동으로 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="2d3d6-115">If any required resources do not exist on the Node, it will automatically download them from the configured location.</span></span> <span data-ttu-id="2d3d6-116">노드가 [보고서 서버](reportServer.md)를 사용하여 구성되는 경우 해당 작업의 상태를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="2d3d6-116">If the Node is configured with a [Report Server](reportServer.md), it will then report the status of the operation.</span></span>

## <a name="configure-the-pull-client-lcm"></a><span data-ttu-id="2d3d6-117">끌어오기 클라이언트 LCM 구성</span><span class="sxs-lookup"><span data-stu-id="2d3d6-117">Configure the pull client LCM</span></span>

<span data-ttu-id="2d3d6-118">아래 예제 중 하나가 실행되면 **PullClientConfigID**라는 새 출력 폴더가 생성되고, 거기에 메타 구성 MOF 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2d3d6-118">Executing any of the examples below creates a new output folder named **PullClientConfigID** and puts a metaconfiguration MOF file there.</span></span> <span data-ttu-id="2d3d6-119">이 경우 메타 구성 MOF 파일의 이름은 `localhost.meta.mof`로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="2d3d6-119">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="2d3d6-120">구성을 적용하려면 메타 구성 MOF 파일의 위치로 설정된 **Path**와 함께 **Set-DscLocalConfigurationManager** cmdlet을 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="2d3d6-120">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span> <span data-ttu-id="2d3d6-121">예:</span><span class="sxs-lookup"><span data-stu-id="2d3d6-121">For example:</span></span>

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a><span data-ttu-id="2d3d6-122">구성 ID</span><span class="sxs-lookup"><span data-stu-id="2d3d6-122">Configuration ID</span></span>

<span data-ttu-id="2d3d6-123">아래 예제에서는 이전에 이 목적으로 만들어진 LCM의 **ConfigurationID** 속성을 **Guid**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="2d3d6-123">The examples below set the **ConfigurationID** property of the LCM to a **Guid** that had been previously created for this purpose.</span></span> <span data-ttu-id="2d3d6-124">**ConfigurationID**는 LCM이 끌어오기 서버에서 적절한 구성의 찾는 데 사용하는 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="2d3d6-124">The **ConfigurationID** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="2d3d6-125">끌어오기 서버의 구성 MOF 파일의 이름은 `ConfigurationID.mof`로 지정해야 합니다. 여기서 *ConfigurationID*는 대상 노드의 LCM의 **ConfigurationID** 속성의 값입니다.</span><span class="sxs-lookup"><span data-stu-id="2d3d6-125">The configuration MOF file on the pull server must be named `ConfigurationID.mof`, where *ConfigurationID* is the value of the **ConfigurationID** property of the target node's LCM.</span></span> <span data-ttu-id="2d3d6-126">자세한 내용은 [끌어오기 서버에 구성 게시(v4/v5)](publishConfigs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2d3d6-126">For more information, see [Publish Configurations to a Pull Server (v4/v5)](publishConfigs.md).</span></span>

<span data-ttu-id="2d3d6-127">아래 예제를 사용하여 임의의 **Guid**를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d3d6-127">You can create a random **Guid** using the example below.</span></span>

```powershell
[System.Guid]::NewGuid()
```

## <a name="set-up-a-pull-client-to-download-configurations"></a><span data-ttu-id="2d3d6-128">구성을 다운로드하도록 끌어오기 클라이언트 설정</span><span class="sxs-lookup"><span data-stu-id="2d3d6-128">Set up a Pull Client to download Configurations</span></span>

<span data-ttu-id="2d3d6-129">각 클라이언트는 **끌어오기** 모드로 구성되고 구성이 저장된 끌어오기 서버 URL이 지정되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d3d6-129">Each client must be configured in **Pull** mode and given the pull server url where its configuration is stored.</span></span> <span data-ttu-id="2d3d6-130">이를 수행하려면, 필요한 정보와 함께 LCM(로컬 구성 관리자)을 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d3d6-130">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="2d3d6-131">LCM을 구성하려면 **LocalConfigurationManager** 블록을 사용하여 특별한 형식의 구성을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2d3d6-131">To configure the LCM, you create a special type of configuration, with a **LocalConfigurationManager** block.</span></span> <span data-ttu-id="2d3d6-132">LCM 구성에 대한 자세한 내용은 [로컬 구성 관리자 구성](../managing-nodes/metaConfig4.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2d3d6-132">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig4.md).</span></span>

## <a name="http-dsc-pull-server"></a><span data-ttu-id="2d3d6-133">HTTP DSC 끌어오기 서버</span><span class="sxs-lookup"><span data-stu-id="2d3d6-133">HTTP DSC Pull Server</span></span>

<span data-ttu-id="2d3d6-134">끌어오기 서버가 웹 서비스로 설정되는 경우 **DownloadManagerName**을 **WebDownloadManager**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="2d3d6-134">If the pull server is set up as a web service, you set the **DownloadManagerName** to **WebDownloadManager**.</span></span> <span data-ttu-id="2d3d6-135">**WebDownloadManager**를 사용하려면 **DownloadManagerCustomData** 키에 대한 **ServerUrl**을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d3d6-135">The **WebDownloadManager** requires that you specify a **ServerUrl** to the **DownloadManagerCustomData** key.</span></span> <span data-ttu-id="2d3d6-136">아래 예제와 같이 **AllowUnsecureConnection**의 값을 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d3d6-136">You can also specify a value for **AllowUnsecureConnection**, as in the example below.</span></span> <span data-ttu-id="2d3d6-137">다음 스크립트는 "PullServer"라는 서버에서 구성을 끌어오도록 LCM을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="2d3d6-137">The following script configures the LCM to pull configurations from a server named "PullServer".</span></span>

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

## <a name="smb-share"></a><span data-ttu-id="2d3d6-138">SMB 공유</span><span class="sxs-lookup"><span data-stu-id="2d3d6-138">SMB Share</span></span>

<span data-ttu-id="2d3d6-139">끌어오기 서버가 웹 서비스가 아닌 SMB 파일 공유로 설정된 경우 **DownloadManagerName**을 **WebDownLoadManager** 대신 **DscFileDownloadManager**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="2d3d6-139">If the pull server is set up as an SMB file share, rather than a web service, you set the **DownloadManagerName** to **DscFileDownloadManager** rather than the **WebDownLoadManager**.</span></span> <span data-ttu-id="2d3d6-140">**DscFileDownloadManager**를 사용하려면 **DownloadManagerCustomData**에서 **SourcePath** 속성을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d3d6-140">The **DscFileDownloadManager** requires that you specify a **SourcePath** property in the **DownloadManagerCustomData**.</span></span> <span data-ttu-id="2d3d6-141">다음 스크립트에서는 "CONTOSO-SERVER"라는 서버에서 "SmbDscShare"라는 SMB 공유의 구성을 끌어오도록 LCM을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="2d3d6-141">The following script configures the LCM to pull configurations from an SMB share named "SmbDscShare" on a server named "CONTOSO-SERVER".</span></span>

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

## <a name="next-steps"></a><span data-ttu-id="2d3d6-142">다음 단계</span><span class="sxs-lookup"><span data-stu-id="2d3d6-142">Next Steps</span></span>

<span data-ttu-id="2d3d6-143">끌어오기 클라이언트를 구성하면 다음 가이드를 사용하여 다음 단계를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d3d6-143">Once the pull client has been configured, you can use the following guides to perform the next steps:</span></span>

- [<span data-ttu-id="2d3d6-144">끌어오기 서버에 구성 게시(v4/v5)</span><span class="sxs-lookup"><span data-stu-id="2d3d6-144">Publish Configurations to a Pull Server (v4/v5)</span></span>](publishConfigs.md)
- [<span data-ttu-id="2d3d6-145">리소스 패키지 및 끌어오기 서버에 업로드(v4)</span><span class="sxs-lookup"><span data-stu-id="2d3d6-145">Package and Upload Resources to a Pull Server (v4)</span></span>](package-upload-resources.md)

## <a name="see-also"></a><span data-ttu-id="2d3d6-146">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2d3d6-146">See Also</span></span>

- [<span data-ttu-id="2d3d6-147">DSC 웹 끌어오기 서버 설정</span><span class="sxs-lookup"><span data-stu-id="2d3d6-147">Set up a DSC web pull server</span></span>](pullServer.md)
- [<span data-ttu-id="2d3d6-148">DSC SMB 끌어오기 서버 설정</span><span class="sxs-lookup"><span data-stu-id="2d3d6-148">Set up a DSC SMB pull server</span></span>](pullServerSMB.md)
