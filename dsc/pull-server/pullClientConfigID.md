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
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-50-and-later"></a><span data-ttu-id="0c7da-103">PowerShell 5.0 이상 구성 Id를 사용 하 여 끌어오기 클라이언트 설정</span><span class="sxs-lookup"><span data-stu-id="0c7da-103">Set up a Pull Client using Configuration IDs in PowerShell 5.0 and later</span></span>

> <span data-ttu-id="0c7da-104">적용 대상: Windows Powershell 5.0</span><span class="sxs-lookup"><span data-stu-id="0c7da-104">Applies To: Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0c7da-105">끌어오기 서버(Windows 기능 *DSC-Service*)는 Windows Server의 지원되는 구성 요소이지만 새로운 기능을 제공할 계획은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0c7da-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="0c7da-106">관리되는 클라우드를 [Azure Automation DSC](/azure/automation/automation-dsc-getting-started)(Windows Server에 끌어오기 서버 이외의 기능 포함) 또는 [여기](pullserver.md#community-solutions-for-pull-service)에 나열된 커뮤니티 솔루션 중 하나로 전환하기 시작하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0c7da-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="0c7da-107">끌어오기 클라이언트를 설정 하기 전에 끌어오기 서버 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c7da-107">Before setting up a pull client, you should set up a pull server.</span></span> <span data-ttu-id="0c7da-108">이 순서 필요 하지 않은 경우 문제 해결에 도움이 됩니다 하 고 등록 되었는지 확인 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c7da-108">Though this order is not required, it helps with troubleshooting, and helps you ensure that the registration was successful.</span></span> <span data-ttu-id="0c7da-109">끌어오기 서버를 설정 하려면 다음 가이드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c7da-109">To set up a pull server, you can use the following guides:</span></span>

- [<span data-ttu-id="0c7da-110">DSC SMB 끌어오기 서버 설정</span><span class="sxs-lookup"><span data-stu-id="0c7da-110">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="0c7da-111">DSC HTTP 끌어오기 서버 설정</span><span class="sxs-lookup"><span data-stu-id="0c7da-111">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="0c7da-112">각 대상 노드를 구성, 리소스를 다운로드 하 여 해당 상태를 보고할 수도 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c7da-112">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="0c7da-113">아래 섹션에서는 SMB 공유 또는 HTTP DSC 끌어오기 서버를 사용 하 여 끌어오기 클라이언트를 구성 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0c7da-113">The sections below show you how to configure a pull client with an SMB share or HTTP DSC Pull Server.</span></span> <span data-ttu-id="0c7da-114">노드의 LCM 새로 고쳐지면 모든 할당 된 구성을 다운로드 하는 구성 된 위치에 연락을 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c7da-114">When the Node's LCM refreshes, it will reach out to the configured location to download any assigned configurations.</span></span> <span data-ttu-id="0c7da-115">노드에서 필요한 모든 리소스가 존재 하지 않는 경우 자동으로 다운로드 하는 구성 된 위치에서.</span><span class="sxs-lookup"><span data-stu-id="0c7da-115">If any required resources do not exist on the Node, it will automatically download them from the configured location.</span></span> <span data-ttu-id="0c7da-116">노드를 사용 하 여 구성 하는 경우는 [보고서 서버](reportServer.md), 다음 작업의 상태를 보고 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c7da-116">If the Node is configured with a [Report Server](reportServer.md), it will then report the status of the operation.</span></span>

> <span data-ttu-id="0c7da-117">**참고**: 이 항목은 PowerShell 5.0에 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c7da-117">**Note**: This topic applies to PowerShell 5.0.</span></span> <span data-ttu-id="0c7da-118">PowerShell 4.0에서 끌어오기 클라이언트를 설정하는 것에 대해서는 [PowerShell 4.0에서 구성 ID를 사용하여 끌어오기 클라이언트 설정](pullClientConfigID4.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0c7da-118">For information on setting up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md)</span></span>

## <a name="configure-the-pull-client-lcm"></a><span data-ttu-id="0c7da-119">끌어오기 클라이언트를 LCM 구성</span><span class="sxs-lookup"><span data-stu-id="0c7da-119">Configure the pull client LCM</span></span>

<span data-ttu-id="0c7da-120">라는 새 출력 폴더를 만들고 아래 예제 중 하나를 실행 **PullClientConfigID** 넣습니다 메타 구성 MOF 파일이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c7da-120">Executing any of the examples below creates a new output folder named **PullClientConfigID** and puts a metaconfiguration MOF file there.</span></span> <span data-ttu-id="0c7da-121">이 경우 메타 구성 MOF 파일의 이름은 `localhost.meta.mof`로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c7da-121">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="0c7da-122">구성을 적용하려면 메타 구성 MOF 파일의 위치로 설정된 **Path**와 함께 **Set-DscLocalConfigurationManager** cmdlet을 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="0c7da-122">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span> <span data-ttu-id="0c7da-123">예:</span><span class="sxs-lookup"><span data-stu-id="0c7da-123">For example:</span></span>

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a><span data-ttu-id="0c7da-124">구성 ID</span><span class="sxs-lookup"><span data-stu-id="0c7da-124">Configuration ID</span></span>

<span data-ttu-id="0c7da-125">집합 아래 예제는 **ConfigurationID** 에 LCM의 속성을 **Guid** 이 목적을 위해 이전에 만든 것입니다.</span><span class="sxs-lookup"><span data-stu-id="0c7da-125">The examples below sets the **ConfigurationID** property of the LCM to a **Guid** that had been previously created for this purpose.</span></span> <span data-ttu-id="0c7da-126">**ConfigurationID**는 LCM이 끌어오기 서버에서 적절한 구성의 찾는 데 사용하는 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="0c7da-126">The **ConfigurationID** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="0c7da-127">끌어오기 서버의 구성 MOF 파일의 이름은 `ConfigurationID.mof`로 지정해야 합니다. 여기서 *ConfigurationID*는 대상 노드의 LCM의 **ConfigurationID** 속성의 값입니다.</span><span class="sxs-lookup"><span data-stu-id="0c7da-127">The configuration MOF file on the pull server must be named `ConfigurationID.mof`, where *ConfigurationID* is the value of the **ConfigurationID** property of the target node's LCM.</span></span> <span data-ttu-id="0c7da-128">자세한 내용은 참조 [끌어오기 서버 (v4/v5) 구성을 게시](publishConfigs.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="0c7da-128">For more information see [Publish Configurations to a Pull Server (v4/v5)](publishConfigs.md).</span></span>

<span data-ttu-id="0c7da-129">임의 만들 수 있습니다 **Guid** 아래 또는 사용 하 여 예제를 사용 하 여 [New-guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0c7da-129">You can create a random **Guid** using the example below, or by using the [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.</span></span>

```powershell
[System.Guid]::NewGuid()
```

<span data-ttu-id="0c7da-130">사용에 대 한 자세한 내용은 **Guid** 환경에서 참조 [Guid에 대 한 계획](/powershell/dsc/secureserver#guids)합니다.</span><span class="sxs-lookup"><span data-stu-id="0c7da-130">For more information about using **Guids** in your environment, see [Plan for Guids](/powershell/dsc/secureserver#guids).</span></span>

## <a name="set-up-a-pull-client-to-download-configurations"></a><span data-ttu-id="0c7da-131">구성 다운로드를 끌어오기 클라이언트 설정</span><span class="sxs-lookup"><span data-stu-id="0c7da-131">Set up a Pull Client to download Configurations</span></span>

<span data-ttu-id="0c7da-132">각 클라이언트에서 구성 해야 **끌어오기** 모드의 구성이 저장 된 끌어오기 서버 url을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c7da-132">Each client must be configured in **Pull** mode and given the pull server url where its configuration is stored.</span></span> <span data-ttu-id="0c7da-133">이를 수행하려면, 필요한 정보와 함께 LCM(로컬 구성 관리자)을 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c7da-133">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="0c7da-134">LCM을 구성하려면 **DSCLocalConfigurationManager** 특성으로 데코레이팅된 특별한 형식의 구성을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0c7da-134">To configure the LCM, you create a special type of configuration, decorated with the **DSCLocalConfigurationManager** attribute.</span></span> <span data-ttu-id="0c7da-135">LCM 구성에 대한 자세한 내용은 [로컬 구성 관리자 구성](../managing-nodes/metaConfig.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0c7da-135">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md).</span></span>

### <a name="http-dsc-pull-server"></a><span data-ttu-id="0c7da-136">HTTP DSC 끌어오기 서버</span><span class="sxs-lookup"><span data-stu-id="0c7da-136">HTTP DSC Pull Server</span></span>

<span data-ttu-id="0c7da-137">다음 스크립트는 "CONTOSO-PullSrv"라는 서버에서 구성을 끌어오도록 LCM을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="0c7da-137">The following script configures the LCM to pull configurations from a server named "CONTOSO-PullSrv".</span></span>

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

<span data-ttu-id="0c7da-138">스크립트에서 **ConfigurationRepositoryWeb** 블록은 끌어오기 서버를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="0c7da-138">In the script, the **ConfigurationRepositoryWeb** block defines the pull server.</span></span> <span data-ttu-id="0c7da-139">합니다 **ServerUrl** DSC 끌어오기의 url을 지정</span><span class="sxs-lookup"><span data-stu-id="0c7da-139">The **ServerUrl** specifies the url of the DSC Pull</span></span>

### <a name="smb-share"></a><span data-ttu-id="0c7da-140">SMB 공유</span><span class="sxs-lookup"><span data-stu-id="0c7da-140">SMB Share</span></span>

<span data-ttu-id="0c7da-141">다음 스크립트는 구성을 끌어오고 다른 서버의 SMB 공유에서 LCM을 구성 `\\SMBPullServer\Pull`합니다.</span><span class="sxs-lookup"><span data-stu-id="0c7da-141">The following script configures the LCM to pull configurations from the SMB Share `\\SMBPullServer\Pull`.</span></span>

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

<span data-ttu-id="0c7da-142">스크립트에는 **ConfigurationRepositoryShare** 블록은 SMB 공유를 방금이 경우에 끌어오기 서버를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c7da-142">In the script, the **ConfigurationRepositoryShare** block defines the pull server, which in this case, is just an SMB share.</span></span>

## <a name="set-up-a-pull-client-to-download-resources"></a><span data-ttu-id="0c7da-143">리소스를 다운로드 하 여 끌어오기 클라이언트 설정</span><span class="sxs-lookup"><span data-stu-id="0c7da-143">Set up a Pull Client to download Resources</span></span>

<span data-ttu-id="0c7da-144">만 지정한 경우는 **ConfigurationRepositoryWeb** 하거나 **ConfigurationRepositoryShare** (앞의 예와) LCM 구성에서 블록에서 끌어오기 클라이언트를 같은 리소스를 가져올 구성을 검색 하는 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="0c7da-144">If you specify only the **ConfigurationRepositoryWeb** or **ConfigurationRepositoryShare** block in your LCM configuration (as in the previous examples), the pull client will pull resources from the same location it retrieves its configurations.</span></span> <span data-ttu-id="0c7da-145">또한 리소스에 대 한 별도 위치를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c7da-145">You can also specify separate locations for resources.</span></span> <span data-ttu-id="0c7da-146">별도 서버로 리소스 위치를 지정 하려면 사용 합니다 **ResourceRepositoryWeb** 블록입니다.</span><span class="sxs-lookup"><span data-stu-id="0c7da-146">To specify a resource location as a separate server, use the **ResourceRepositoryWeb** block.</span></span> <span data-ttu-id="0c7da-147">SMB 공유로 리소스 위치를 지정 하려면 사용 합니다 **ResourceRepositoryShare** 블록입니다.</span><span class="sxs-lookup"><span data-stu-id="0c7da-147">To specify a resource location as an SMB share, use the **ResourceRepositoryShare** block.</span></span>

> [!NOTE]
> <span data-ttu-id="0c7da-148">결합할 수 있습니다 **ConfigurationRepositoryWeb** 사용 하 여 **ResourceRepositoryShare** 하거나 **ConfigurationRepositoryShare** 사용 하 여 **ResourceRepositoryWeb** .</span><span class="sxs-lookup"><span data-stu-id="0c7da-148">You can combine **ConfigurationRepositoryWeb** with **ResourceRepositoryShare** or **ConfigurationRepositoryShare** with **ResourceRepositoryWeb**.</span></span> <span data-ttu-id="0c7da-149">이 예가 아래에 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0c7da-149">Examples of this are not shown below.</span></span>

### <a name="http-dsc-pull-server"></a><span data-ttu-id="0c7da-150">HTTP DSC 끌어오기 서버</span><span class="sxs-lookup"><span data-stu-id="0c7da-150">HTTP DSC Pull Server</span></span>

<span data-ttu-id="0c7da-151">다음 메타 구성에서 해당 구성을 가져오도록 끌어오기 클라이언트 구성 **Contoso-pullsrv** 에서 리소스 **Contoso-resourcesrv**합니다.</span><span class="sxs-lookup"><span data-stu-id="0c7da-151">The following metaconfiguration configures a pull client to get its configurations from **CONTOSO-PullSrv** and its resources from **CONTOSO-ResourceSrv**.</span></span>

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

### <a name="smb-share"></a><span data-ttu-id="0c7da-152">SMB 공유</span><span class="sxs-lookup"><span data-stu-id="0c7da-152">SMB Share</span></span>

<span data-ttu-id="0c7da-153">다음 예제에서는 SMB 공유에서 구성을 끌어오고 다른 서버의 클라이언트를 설정 하는 메타 구성을 `\\SMBPullServer\Configurations`, 및 SMB 공유에서 리소스 `\\SMBPullServer\Resources`합니다.</span><span class="sxs-lookup"><span data-stu-id="0c7da-153">The following example shows a metaconfiguration that sets up a client to pull configurations from the SMB share `\\SMBPullServer\Configurations`, and resources from the SMB share `\\SMBPullServer\Resources`.</span></span>

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

#### <a name="automatically-download-resources-in-push-mode"></a><span data-ttu-id="0c7da-154">밀어넣기 모드에서 리소스를 자동으로 다운로드</span><span class="sxs-lookup"><span data-stu-id="0c7da-154">Automatically download Resources in Push Mode</span></span>

<span data-ttu-id="0c7da-155">PowerShell 5.0부터 끌어오기 클라이언트에서에서 다운로드할 수 모듈 SMB 공유를 사용 하도록 구성 된 경우에 **푸시** 모드입니다.</span><span class="sxs-lookup"><span data-stu-id="0c7da-155">Beginning in PowerShell 5.0, your pull clients can download modules from an SMB share, even when they are configured for **Push** mode.</span></span> <span data-ttu-id="0c7da-156">여기서 하지 않으려는 경우 끌어오기 서버를 설정 하는 시나리오에서 특히 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c7da-156">This is especially useful in scenarios where you do not want to set up a Pull Server.</span></span> <span data-ttu-id="0c7da-157">합니다 **ResourceRepositoryShare** 블록을 지정 하지 않고 사용할 수는 **ConfigurationRepositoryShare**합니다.</span><span class="sxs-lookup"><span data-stu-id="0c7da-157">The **ResourceRepositoryShare** block can be used without specifying a **ConfigurationRepositoryShare**.</span></span> <span data-ttu-id="0c7da-158">다음 예제에서는 SMB 공유에서 리소스를 가져올 클라이언트를 설정 하는 메타 구성을 `\\SMBPullServer\Resources`합니다.</span><span class="sxs-lookup"><span data-stu-id="0c7da-158">The following example shows a metaconfiguration that sets up a client to pull resources from an SMB Share `\\SMBPullServer\Resources`.</span></span> <span data-ttu-id="0c7da-159">노드가 **PUSHED** 구성을 자동으로 다운로드를 필요한 모든 리소스에서 지정 된 공유 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c7da-159">When the Node is **PUSHED** a configuration, it will automatically download any required resources, from the share specified.</span></span>

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

## <a name="set-up-a-pull-client-to-report-status"></a><span data-ttu-id="0c7da-160">상태 보고에 대 한 끌어오기 클라이언트 설정</span><span class="sxs-lookup"><span data-stu-id="0c7da-160">Set up a Pull Client to report status</span></span>

<span data-ttu-id="0c7da-161">기본적으로 노드 구성된 끌어오기 서버에 보고서를 보내지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0c7da-161">By default, Nodes will not send reports to a configured Pull Server.</span></span> <span data-ttu-id="0c7da-162">구성, 리소스 및 보고에 단일 끌어오기 서버를 사용할 수 있지만 **ReportRepositoryWeb** 블록을 만들어 보고를 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c7da-162">You can use a single pull server for configurations, resources, and reporting, but you have to create a **ReportRepositoryWeb** block to set up reporting.</span></span>

### <a name="http-dsc-pull-server"></a><span data-ttu-id="0c7da-163">HTTP DSC 끌어오기 서버</span><span class="sxs-lookup"><span data-stu-id="0c7da-163">HTTP DSC Pull Server</span></span>

<span data-ttu-id="0c7da-164">다음 예제에서는 구성 및 리소스를 끌어오고 보고 데이터를 단일 서버에 보내도록 클라이언트를 설정하는 메타 구성을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0c7da-164">The following example shows a metaconfiguration that sets up a client to pull configurations and resources, and send reporting data, to a single pull server.</span></span>

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

<span data-ttu-id="0c7da-165">보고서 서버를 지정하려면 **ReportRepositoryWeb** 블록을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0c7da-165">To specify a report server, you use a **ReportRepositoryWeb** block.</span></span> <span data-ttu-id="0c7da-166">보고서 서버는 SMB 서버일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0c7da-166">A report server cannot be an SMB server.</span></span>
<span data-ttu-id="0c7da-167">해당 메타 구성은 **CONTOSO-PullSrv**에서 구성을 가져오고 **CONTOSO-ResourceSrv**에서 리소스를 가져오고, **CONTOSO-ReportSrv**에 상태 보고서를 보내도록 끌어오기 클라이언트를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="0c7da-167">The following metaconfiguration configures a pull client to get its configurations from **CONTOSO-PullSrv** and its resources from **CONTOSO-ResourceSrv**, and to send status reports to **CONTOSO-ReportSrv**:</span></span>

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

### <a name="smb-share"></a><span data-ttu-id="0c7da-168">SMB 공유</span><span class="sxs-lookup"><span data-stu-id="0c7da-168">SMB Share</span></span>

<span data-ttu-id="0c7da-169">보고서 서버는 SMB 공유 일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0c7da-169">A report server cannot be an SMB share.</span></span>

## <a name="next-steps"></a><span data-ttu-id="0c7da-170">다음 단계</span><span class="sxs-lookup"><span data-stu-id="0c7da-170">Next Steps</span></span>

<span data-ttu-id="0c7da-171">끌어오기 클라이언트를 구성한 후 다음 단계를 수행 하려면 다음 가이드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c7da-171">Once the pull client has been configured, you can use the following guides to perform the next steps:</span></span>

- [<span data-ttu-id="0c7da-172">끌어오기 서버에 구성 게시(v4/v5)</span><span class="sxs-lookup"><span data-stu-id="0c7da-172">Publish Configurations to a Pull Server (v4/v5)</span></span>](publishConfigs.md)
- [<span data-ttu-id="0c7da-173">리소스 패키지 및 끌어오기 서버에 업로드(v4)</span><span class="sxs-lookup"><span data-stu-id="0c7da-173">Package and Upload Resources to a Pull Server (v4)</span></span>](package-upload-resources.md)

## <a name="see-also"></a><span data-ttu-id="0c7da-174">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0c7da-174">See Also</span></span>

* [<span data-ttu-id="0c7da-175">Setting up a pull client with configuration names(구성 이름을 사용하여 끌어오기 클라이언트 설정)</span><span class="sxs-lookup"><span data-stu-id="0c7da-175">Setting up a pull client with configuration names</span></span>](pullClientConfigNames.md)
