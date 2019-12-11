---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: PowerShell 5.0 이상에서 구성 ID를 사용하여 끌어오기 클라이언트 설정
ms.openlocfilehash: bd173a1079b916c450a0292dca7a595a9bcff985
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74417240"
---
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-50-and-later"></a><span data-ttu-id="989d6-103">PowerShell 5.0 이상에서 구성 ID를 사용하여 끌어오기 클라이언트 설정</span><span class="sxs-lookup"><span data-stu-id="989d6-103">Set up a Pull Client using Configuration IDs in PowerShell 5.0 and later</span></span>

> <span data-ttu-id="989d6-104">적용 대상: Windows Powershell 5.0</span><span class="sxs-lookup"><span data-stu-id="989d6-104">Applies To: Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="989d6-105">끌어오기 서버(Windows 기능 *DSC-Service*)는 Windows Server의 지원되는 구성 요소이지만 새로운 기능을 제공할 계획은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="989d6-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="989d6-106">관리되는 클라우드를 [Azure Automation DSC](/azure/automation/automation-dsc-getting-started)(Windows Server에 끌어오기 서버 이외의 기능 포함) 또는 [여기](pullserver.md#community-solutions-for-pull-service)에 나열된 커뮤니티 솔루션 중 하나로 전환하기 시작하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="989d6-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="989d6-107">끌어오기 클라이언트를 설정하기 전에 끌어오기 서버를 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="989d6-107">Before setting up a pull client, you should set up a pull server.</span></span> <span data-ttu-id="989d6-108">이 순서가 필요하지 않더라도 문제 해결에 도움이 되고 등록에 성공했는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="989d6-108">Though this order is not required, it helps with troubleshooting, and helps you ensure that the registration was successful.</span></span> <span data-ttu-id="989d6-109">끌어오기 서버를 설정하려면 다음 가이드를 사용하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="989d6-109">To set up a pull server, you can use the following guides:</span></span>

- [<span data-ttu-id="989d6-110">DSC SMB 끌어오기 서버 설정</span><span class="sxs-lookup"><span data-stu-id="989d6-110">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="989d6-111">DSC HTTP 끌어오기 서버 설정</span><span class="sxs-lookup"><span data-stu-id="989d6-111">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="989d6-112">구성, 리소스를 다운로드하고 해당 상태를 보고하도록 각 대상 노드를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="989d6-112">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="989d6-113">아래 섹션에서는 SMB 공유 또는 HTTP DSC 끌어오기 서버를 사용하여 끌어오기 클라이언트를 구성하는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="989d6-113">The sections below show you how to configure a pull client with an SMB share or HTTP DSC Pull Server.</span></span> <span data-ttu-id="989d6-114">노드의 LCM가 새로 고쳐지면 구성된 위치에 도달하여 할당된 구성을 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="989d6-114">When the Node's LCM refreshes, it will reach out to the configured location to download any assigned configurations.</span></span> <span data-ttu-id="989d6-115">노드에서 필수 리소스가 존재하지 않는 경우 구성된 위치로부터 자동으로 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="989d6-115">If any required resources do not exist on the Node, it will automatically download them from the configured location.</span></span> <span data-ttu-id="989d6-116">노드가 [보고서 서버](reportServer.md)를 사용하여 구성되는 경우 해당 작업의 상태를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="989d6-116">If the Node is configured with a [Report Server](reportServer.md), it will then report the status of the operation.</span></span>

> [!NOTE]
> <span data-ttu-id="989d6-117">이 토픽은 PowerShell 5.0에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="989d6-117">This topic applies to PowerShell 5.0.</span></span> <span data-ttu-id="989d6-118">PowerShell 4.0에서 끌어오기 클라이언트를 설정하는 것에 대해서는 [PowerShell 4.0에서 구성 ID를 사용하여 끌어오기 클라이언트 설정](pullClientConfigID4.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="989d6-118">For information on setting up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md)</span></span>

## <a name="configure-the-pull-client-lcm"></a><span data-ttu-id="989d6-119">끌어오기 클라이언트 LCM 구성</span><span class="sxs-lookup"><span data-stu-id="989d6-119">Configure the pull client LCM</span></span>

<span data-ttu-id="989d6-120">아래 예제 중 하나가 실행되면 **PullClientConfigID**라는 새 출력 폴더가 생성되고, 거기에 메타 구성 MOF 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="989d6-120">Executing any of the examples below creates a new output folder named **PullClientConfigID** and puts a metaconfiguration MOF file there.</span></span> <span data-ttu-id="989d6-121">이 경우 메타 구성 MOF 파일의 이름은 `localhost.meta.mof`로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="989d6-121">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="989d6-122">구성을 적용하려면 메타 구성 MOF 파일의 위치로 설정된 **Path**와 함께 **Set-DscLocalConfigurationManager** cmdlet을 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="989d6-122">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span> <span data-ttu-id="989d6-123">예:</span><span class="sxs-lookup"><span data-stu-id="989d6-123">For example:</span></span>

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a><span data-ttu-id="989d6-124">구성 ID</span><span class="sxs-lookup"><span data-stu-id="989d6-124">Configuration ID</span></span>

<span data-ttu-id="989d6-125">아래 예제에서는 이전에 이 목적으로 만들어진 LCM의 **ConfigurationID** 속성을 **Guid**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="989d6-125">The examples below sets the **ConfigurationID** property of the LCM to a **Guid** that had been previously created for this purpose.</span></span> <span data-ttu-id="989d6-126">**ConfigurationID**는 LCM이 끌어오기 서버에서 적절한 구성의 찾는 데 사용하는 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="989d6-126">The **ConfigurationID** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="989d6-127">끌어오기 서버의 구성 MOF 파일의 이름은 `ConfigurationID.mof`로 지정해야 합니다. 여기서 *ConfigurationID*는 대상 노드의 LCM의 **ConfigurationID** 속성의 값입니다.</span><span class="sxs-lookup"><span data-stu-id="989d6-127">The configuration MOF file on the pull server must be named `ConfigurationID.mof`, where *ConfigurationID* is the value of the **ConfigurationID** property of the target node's LCM.</span></span> <span data-ttu-id="989d6-128">자세한 내용은 [끌어오기 서버에 구성 게시(v4/v5)](publishConfigs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="989d6-128">For more information see [Publish Configurations to a Pull Server (v4/v5)](publishConfigs.md).</span></span>

<span data-ttu-id="989d6-129">아래 예제 또는 [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet을 사용하여 임의의 **Guid**를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="989d6-129">You can create a random **Guid** using the example below, or by using the [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.</span></span>

```powershell
[System.Guid]::NewGuid()
```

<span data-ttu-id="989d6-130">환경에서 **Guid**를 사용하는 방법에 대한 자세한 내용은 [Guid에 대한 계획](/powershell/scripting/dsc/secureserver#guids)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="989d6-130">For more information about using **Guids** in your environment, see [Plan for Guids](/powershell/scripting/dsc/secureserver#guids).</span></span>

## <a name="set-up-a-pull-client-to-download-configurations"></a><span data-ttu-id="989d6-131">구성을 다운로드하도록 끌어오기 클라이언트 설정</span><span class="sxs-lookup"><span data-stu-id="989d6-131">Set up a Pull Client to download Configurations</span></span>

<span data-ttu-id="989d6-132">각 클라이언트는 **끌어오기** 모드로 구성되고 구성이 저장된 끌어오기 서버 URL이 지정되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="989d6-132">Each client must be configured in **Pull** mode and given the pull server url where its configuration is stored.</span></span> <span data-ttu-id="989d6-133">이를 수행하려면, 필요한 정보와 함께 LCM(로컬 구성 관리자)을 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="989d6-133">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="989d6-134">LCM을 구성하려면 **DSCLocalConfigurationManager** 특성으로 데코레이팅된 특별한 형식의 구성을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="989d6-134">To configure the LCM, you create a special type of configuration, decorated with the **DSCLocalConfigurationManager** attribute.</span></span> <span data-ttu-id="989d6-135">LCM 구성에 대한 자세한 내용은 [로컬 구성 관리자 구성](../managing-nodes/metaConfig.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="989d6-135">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md).</span></span>

### <a name="http-dsc-pull-server"></a><span data-ttu-id="989d6-136">HTTP DSC 끌어오기 서버</span><span class="sxs-lookup"><span data-stu-id="989d6-136">HTTP DSC Pull Server</span></span>

<span data-ttu-id="989d6-137">다음 스크립트는 "CONTOSO-PullSrv"라는 서버에서 구성을 끌어오도록 LCM을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="989d6-137">The following script configures the LCM to pull configurations from a server named "CONTOSO-PullSrv".</span></span>

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

<span data-ttu-id="989d6-138">스크립트에서 **ConfigurationRepositoryWeb** 블록은 끌어오기 서버를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="989d6-138">In the script, the **ConfigurationRepositoryWeb** block defines the pull server.</span></span> <span data-ttu-id="989d6-139">**ServerUrl**은 DSC 끌어오기의 URL을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="989d6-139">The **ServerUrl** specifies the url of the DSC Pull</span></span>

### <a name="smb-share"></a><span data-ttu-id="989d6-140">SMB 공유</span><span class="sxs-lookup"><span data-stu-id="989d6-140">SMB Share</span></span>

<span data-ttu-id="989d6-141">다음 스크립트에서는 SMB 공유 `\\SMBPullServer\Pull`로부터 구성을 끌어오도록 LCM을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="989d6-141">The following script configures the LCM to pull configurations from the SMB Share `\\SMBPullServer\Pull`.</span></span>

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

<span data-ttu-id="989d6-142">해당 스크립트에서 **ConfigurationRepositoryShare** 블록은 끌어오기 서버를 정의합니다(이 경우에는 SMB 공유임).</span><span class="sxs-lookup"><span data-stu-id="989d6-142">In the script, the **ConfigurationRepositoryShare** block defines the pull server, which in this case, is just an SMB share.</span></span>

## <a name="set-up-a-pull-client-to-download-resources"></a><span data-ttu-id="989d6-143">리소스를 다운로드하도록 끌어오기 클라이언트 설정</span><span class="sxs-lookup"><span data-stu-id="989d6-143">Set up a Pull Client to download Resources</span></span>

<span data-ttu-id="989d6-144">앞의 예와 같이 LCM 구성에서 **ConfigurationRepositoryWeb** 또는 **ConfigurationRepositoryShare** 블록만 지정하는 경우 끌어오기 클라이언트는 해당 구성을 가져온 것과 동일한 위치에서 리소스를 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="989d6-144">If you specify only the **ConfigurationRepositoryWeb** or **ConfigurationRepositoryShare** block in your LCM configuration (as in the previous examples), the pull client will pull resources from the same location it retrieves its configurations.</span></span> <span data-ttu-id="989d6-145">리소스에 대해 별도 위치를 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="989d6-145">You can also specify separate locations for resources.</span></span> <span data-ttu-id="989d6-146">별도 서버로 리소스 위치를 지정하려면 **ResourceRepositoryWeb** 블록을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="989d6-146">To specify a resource location as a separate server, use the **ResourceRepositoryWeb** block.</span></span> <span data-ttu-id="989d6-147">SMB 공유로 리소스 위치를 지정하려면 **ResourceRepositoryShare** 블록을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="989d6-147">To specify a resource location as an SMB share, use the **ResourceRepositoryShare** block.</span></span>

> [!NOTE]
> <span data-ttu-id="989d6-148">**ConfigurationRepositoryWeb**을 **ResourceRepositoryShare**와 결합하거나 **ConfigurationRepositoryShare**를 **ResourceRepositoryWeb** 과 결합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="989d6-148">You can combine **ConfigurationRepositoryWeb** with **ResourceRepositoryShare** or **ConfigurationRepositoryShare** with **ResourceRepositoryWeb**.</span></span> <span data-ttu-id="989d6-149">이 예제가 아래에 표시되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="989d6-149">Examples of this are not shown below.</span></span>

### <a name="http-dsc-pull-server"></a><span data-ttu-id="989d6-150">HTTP DSC 끌어오기 서버</span><span class="sxs-lookup"><span data-stu-id="989d6-150">HTTP DSC Pull Server</span></span>

<span data-ttu-id="989d6-151">다음 메타 구성은 **CONTOSO-PullSrv**로부터 구성을 가져오고 **CONTOSO-ResourceSrv**로부터 리소스를 가져오도록 끌어오기 클라이언트를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="989d6-151">The following metaconfiguration configures a pull client to get its configurations from **CONTOSO-PullSrv** and its resources from **CONTOSO-ResourceSrv**.</span></span>

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

### <a name="smb-share"></a><span data-ttu-id="989d6-152">SMB 공유</span><span class="sxs-lookup"><span data-stu-id="989d6-152">SMB Share</span></span>

<span data-ttu-id="989d6-153">다음 예제에서는 SMB 공유 `\\SMBPullServer\Configurations`로부터 구성을 끌어오고, SMB 공유 `\\SMBPullServer\Resources`로부터 리소스를 끌어오도록 클라이언트를 설정하는 메타 구성을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="989d6-153">The following example shows a metaconfiguration that sets up a client to pull configurations from the SMB share `\\SMBPullServer\Configurations`, and resources from the SMB share `\\SMBPullServer\Resources`.</span></span>

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

#### <a name="automatically-download-resources-in-push-mode"></a><span data-ttu-id="989d6-154">푸시 모드에서 자동으로 리소스 다운로드</span><span class="sxs-lookup"><span data-stu-id="989d6-154">Automatically download Resources in Push Mode</span></span>

<span data-ttu-id="989d6-155">PowerShell 5.0부터 끌어오기 클라이언트는 **푸시** 모드로 구성된 경우에도 SMB 공유로부터 모듈을 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="989d6-155">Beginning in PowerShell 5.0, your pull clients can download modules from an SMB share, even when they are configured for **Push** mode.</span></span> <span data-ttu-id="989d6-156">이 기능은 끌어오기 서버를 설정하지 않으려는 시나리오에서 특히 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="989d6-156">This is especially useful in scenarios where you do not want to set up a Pull Server.</span></span> <span data-ttu-id="989d6-157">**ResourceRepositoryShare** 블록은 **ConfigurationRepositoryShare**를 지정하지 않고 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="989d6-157">The **ResourceRepositoryShare** block can be used without specifying a **ConfigurationRepositoryShare**.</span></span> <span data-ttu-id="989d6-158">다음 예제에서는 SMB 공유 `\\SMBPullServer\Resources`로부터 리소스를 끌어오도록 클라이언트를 설정하는 메타 구성을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="989d6-158">The following example shows a metaconfiguration that sets up a client to pull resources from an SMB Share `\\SMBPullServer\Resources`.</span></span> <span data-ttu-id="989d6-159">노드가 **PUSHED** 구성이면 지정된 공유로부터 모든 필수 리소스를 자동으로 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="989d6-159">When the Node is **PUSHED** a configuration, it will automatically download any required resources, from the share specified.</span></span>

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

## <a name="set-up-a-pull-client-to-report-status"></a><span data-ttu-id="989d6-160">상태를 보고하도록 끌어오기 클라이언트 설정</span><span class="sxs-lookup"><span data-stu-id="989d6-160">Set up a Pull Client to report status</span></span>

<span data-ttu-id="989d6-161">기본적으로 노드는 구성된 끌어오기 서버로 보고서를 보내지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="989d6-161">By default, Nodes will not send reports to a configured Pull Server.</span></span> <span data-ttu-id="989d6-162">구성, 리소스 및 보고에 단일 끌어오기 서버를 사용할 수 있지만 **ReportRepositoryWeb** 블록을 만들어 보고를 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="989d6-162">You can use a single pull server for configurations, resources, and reporting, but you have to create a **ReportRepositoryWeb** block to set up reporting.</span></span>

### <a name="http-dsc-pull-server"></a><span data-ttu-id="989d6-163">HTTP DSC 끌어오기 서버</span><span class="sxs-lookup"><span data-stu-id="989d6-163">HTTP DSC Pull Server</span></span>

<span data-ttu-id="989d6-164">다음 예제에서는 구성 및 리소스를 끌어오고 보고 데이터를 단일 서버에 보내도록 클라이언트를 설정하는 메타 구성을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="989d6-164">The following example shows a metaconfiguration that sets up a client to pull configurations and resources, and send reporting data, to a single pull server.</span></span>

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

<span data-ttu-id="989d6-165">보고서 서버를 지정하려면 **ReportRepositoryWeb** 블록을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="989d6-165">To specify a report server, you use a **ReportRepositoryWeb** block.</span></span> <span data-ttu-id="989d6-166">보고서 서버는 SMB 서버일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="989d6-166">A report server cannot be an SMB server.</span></span>
<span data-ttu-id="989d6-167">해당 메타 구성은 **CONTOSO-PullSrv**에서 구성을 가져오고 **CONTOSO-ResourceSrv**에서 리소스를 가져오고, **CONTOSO-ReportSrv**에 상태 보고서를 보내도록 끌어오기 클라이언트를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="989d6-167">The following metaconfiguration configures a pull client to get its configurations from **CONTOSO-PullSrv** and its resources from **CONTOSO-ResourceSrv**, and to send status reports to **CONTOSO-ReportSrv**:</span></span>

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

### <a name="smb-share"></a><span data-ttu-id="989d6-168">SMB 공유</span><span class="sxs-lookup"><span data-stu-id="989d6-168">SMB Share</span></span>

<span data-ttu-id="989d6-169">보고서 서버는 SMB 공유일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="989d6-169">A report server cannot be an SMB share.</span></span>

## <a name="next-steps"></a><span data-ttu-id="989d6-170">다음 단계</span><span class="sxs-lookup"><span data-stu-id="989d6-170">Next Steps</span></span>

<span data-ttu-id="989d6-171">끌어오기 클라이언트를 구성하면 다음 가이드를 사용하여 다음 단계를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="989d6-171">Once the pull client has been configured, you can use the following guides to perform the next steps:</span></span>

- [<span data-ttu-id="989d6-172">끌어오기 서버에 구성 게시(v4/v5)</span><span class="sxs-lookup"><span data-stu-id="989d6-172">Publish Configurations to a Pull Server (v4/v5)</span></span>](publishConfigs.md)
- [<span data-ttu-id="989d6-173">리소스 패키지 및 끌어오기 서버에 업로드(v4)</span><span class="sxs-lookup"><span data-stu-id="989d6-173">Package and Upload Resources to a Pull Server (v4)</span></span>](package-upload-resources.md)

## <a name="see-also"></a><span data-ttu-id="989d6-174">참고 항목</span><span class="sxs-lookup"><span data-stu-id="989d6-174">See Also</span></span>

* [<span data-ttu-id="989d6-175">Setting up a pull client with configuration names(구성 이름을 사용하여 끌어오기 클라이언트 설정)</span><span class="sxs-lookup"><span data-stu-id="989d6-175">Setting up a pull client with configuration names</span></span>](pullClientConfigNames.md)
