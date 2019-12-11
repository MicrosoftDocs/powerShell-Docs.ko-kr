---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: PowerShell 5.0 이상에서 구성 이름을 사용하여 끌어오기 클라이언트 설정
ms.openlocfilehash: d591e2a757130ccecaf4eaf9f363f607fca82b93
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953630"
---
# <a name="set-up-a-pull-client-using-configuration-names-in-powershell-50-and-later"></a><span data-ttu-id="8c452-103">PowerShell 5.0 이상에서 구성 이름을 사용하여 끌어오기 클라이언트 설정</span><span class="sxs-lookup"><span data-stu-id="8c452-103">Set up a Pull Client using Configuration Names in PowerShell 5.0 and later</span></span>

> <span data-ttu-id="8c452-104">적용 대상: Windows Powershell 5.0</span><span class="sxs-lookup"><span data-stu-id="8c452-104">Applies To: Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8c452-105">끌어오기 서버(Windows 기능 *DSC-Service*)는 Windows Server의 지원되는 구성 요소이지만 새로운 기능을 제공할 계획은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8c452-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="8c452-106">관리되는 클라우드를 [Azure Automation DSC](/azure/automation/automation-dsc-getting-started)(Windows Server에 끌어오기 서버 이외의 기능 포함) 또는 [여기](pullserver.md#community-solutions-for-pull-service)에 나열된 커뮤니티 솔루션 중 하나로 전환하기 시작하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8c452-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="8c452-107">끌어오기 클라이언트를 설정하기 전에 끌어오기 서버를 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c452-107">Before setting up a pull client, you should set up a pull server.</span></span> <span data-ttu-id="8c452-108">이 순서가 필요하지 않더라도 문제 해결에 도움이 되고 등록에 성공했는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c452-108">Though this order is not required, it helps with troubleshooting, and helps you ensure that the registration was successful.</span></span> <span data-ttu-id="8c452-109">끌어오기 서버를 설정하려면 다음 가이드를 사용하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c452-109">To set up a pull server, you can use the following guides:</span></span>

- [<span data-ttu-id="8c452-110">DSC SMB 끌어오기 서버 설정</span><span class="sxs-lookup"><span data-stu-id="8c452-110">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="8c452-111">DSC HTTP 끌어오기 서버 설정</span><span class="sxs-lookup"><span data-stu-id="8c452-111">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="8c452-112">구성, 리소스를 다운로드하고 해당 상태를 보고하도록 각 대상 노드를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c452-112">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="8c452-113">아래 섹션에서는 SMB 공유 또는 HTTP DSC 끌어오기 서버를 사용하여 끌어오기 클라이언트를 구성하는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="8c452-113">The sections below show you how to configure a pull client with an SMB share or HTTP DSC Pull Server.</span></span> <span data-ttu-id="8c452-114">노드의 LCM가 새로 고쳐지면 구성된 위치에 도달하여 할당된 구성을 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="8c452-114">When the Node's LCM refreshes, it will reach out to the configured location to download any assigned configurations.</span></span> <span data-ttu-id="8c452-115">노드에서 필수 리소스가 존재하지 않는 경우 구성된 위치로부터 자동으로 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="8c452-115">If any required resources do not exist on the Node, it will automatically download them from the configured location.</span></span> <span data-ttu-id="8c452-116">노드가 [보고서 서버](reportServer.md)를 사용하여 구성되는 경우 해당 작업의 상태를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="8c452-116">If the Node is configured with a [Report Server](reportServer.md), it will then report the status of the operation.</span></span>

> [!NOTE]
> <span data-ttu-id="8c452-117">이 토픽은 PowerShell 5.0에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c452-117">This topic applies to PowerShell 5.0.</span></span>
> <span data-ttu-id="8c452-118">PowerShell 4.0에서 끌어오기 클라이언트를 설정하는 방법에 대한 정보는 [PowerShell 4.0에서 구성 ID를 사용하여 끌어오기 클라이언트 설정](pullClientConfigID4.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8c452-118">For information on setting up a pull client in PowerShell 4.0, see [Set up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md)</span></span>

## <a name="configure-the-pull-client-lcm"></a><span data-ttu-id="8c452-119">끌어오기 클라이언트 LCM 구성</span><span class="sxs-lookup"><span data-stu-id="8c452-119">Configure the pull client LCM</span></span>

<span data-ttu-id="8c452-120">아래 예제 중 하나가 실행되면 **PullClientConfigName**이라는 새 출력 폴더가 생성되고, 거기에 메타 구성 MOF 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8c452-120">Executing any of the examples below creates a new output folder named **PullClientConfigName** and puts a metaconfiguration MOF file there.</span></span> <span data-ttu-id="8c452-121">이 경우 메타 구성 MOF 파일의 이름은 `localhost.meta.mof`로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c452-121">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="8c452-122">구성을 적용하려면 메타 구성 MOF 파일의 위치로 설정된 **Path**와 함께 **Set-DscLocalConfigurationManager** cmdlet을 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="8c452-122">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span> <span data-ttu-id="8c452-123">예:</span><span class="sxs-lookup"><span data-stu-id="8c452-123">For example:</span></span>

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigName –Verbose.
```

## <a name="configuration-name"></a><span data-ttu-id="8c452-124">구성 이름</span><span class="sxs-lookup"><span data-stu-id="8c452-124">Configuration Name</span></span>

<span data-ttu-id="8c452-125">아래 예제에서는 LCM의 **ConfigurationName** 속성을 이전에 컴파일된 구성의 이름(이 목적을 위해 생성됨)으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8c452-125">The examples below sets the **ConfigurationName** property of the LCM to the name of a previously compiled Configuration, created for this purpose.</span></span> <span data-ttu-id="8c452-126">**ConfigurationName**은 LCM이 끌어오기 서버에서 적절한 구성을 찾는 데 사용하는 항목입니다.</span><span class="sxs-lookup"><span data-stu-id="8c452-126">The **ConfigurationName** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="8c452-127">끌어오기 서버의 구성 MOF 파일의 이름은 `<ConfigurationName>.mof`입니다(이 경우에 "ClientConfig.mof").</span><span class="sxs-lookup"><span data-stu-id="8c452-127">The configuration MOF file on the pull server must be named `<ConfigurationName>.mof`, in this case, "ClientConfig.mof".</span></span> <span data-ttu-id="8c452-128">자세한 내용은 [끌어오기 서버에 구성 게시(v4/v5)](publishConfigs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8c452-128">For more information, see [Publish Configurations to a Pull Server (v4/v5)](publishConfigs.md).</span></span>

## <a name="set-up-a-pull-client-to-download-configurations"></a><span data-ttu-id="8c452-129">구성을 다운로드하도록 끌어오기 클라이언트 설정</span><span class="sxs-lookup"><span data-stu-id="8c452-129">Set up a Pull Client to download Configurations</span></span>

<span data-ttu-id="8c452-130">각 클라이언트는 **끌어오기** 모드로 구성되고 구성이 저장된 끌어오기 서버 URL이 지정되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c452-130">Each client must be configured in **Pull** mode and given the pull server url where its configuration is stored.</span></span> <span data-ttu-id="8c452-131">이를 수행하려면, 필요한 정보와 함께 LCM(로컬 구성 관리자)을 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c452-131">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="8c452-132">LCM을 구성하려면 **DSCLocalConfigurationManager** 특성으로 데코레이팅된 특별한 형식의 구성을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8c452-132">To configure the LCM, you create a special type of configuration, decorated with the **DSCLocalConfigurationManager** attribute.</span></span> <span data-ttu-id="8c452-133">LCM 구성에 대한 자세한 내용은 [로컬 구성 관리자 구성](../managing-nodes/metaConfig.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8c452-133">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md).</span></span>

<span data-ttu-id="8c452-134">다음 스크립트는 "CONTOSO-PullSrv"라는 서버에서 구성을 끌어오도록 LCM을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="8c452-134">The following script configures the LCM to pull configurations from a server named "CONTOSO-PullSrv".</span></span>

- <span data-ttu-id="8c452-135">스크립트에서 **ConfigurationRepositoryWeb** 블록은 끌어오기 서버를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="8c452-135">In the script, the **ConfigurationRepositoryWeb** block defines the pull server.</span></span> <span data-ttu-id="8c452-136">**ServerURL** 속성은 끌어오기 서버에 대한 엔드포인트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8c452-136">The **ServerURL** property specifies the endpoint for the pull server.</span></span>

- <span data-ttu-id="8c452-137">**RegistrationKey** 속성은 끌어오기 서버에 대한 모든 클라이언트 노드와 해당 끌어오기 서버 간의 공유 키입니다.</span><span class="sxs-lookup"><span data-stu-id="8c452-137">The **RegistrationKey** property is a shared key between all client nodes for a pull server and that pull server.</span></span> <span data-ttu-id="8c452-138">동일한 값이 끌어오기 서버에 있는 파일에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c452-138">The same value is stored in a file on the pull server.</span></span>
  > [!NOTE]
  > <span data-ttu-id="8c452-139">등록 키는 **웹** 끌어오기 서버에서만 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="8c452-139">Registration keys work only with **web** pull servers.</span></span> <span data-ttu-id="8c452-140">**SMB** 끌어오기 서버에는 여전히 **ConfigurationID**를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c452-140">You must still use **ConfigurationID** with an **SMB** pull server.</span></span>
  > <span data-ttu-id="8c452-141">**ConfigurationID**를 사용하여 끌어오기 서버를 구성하는 것에 대해서는 [구성 ID를 사용하여 끌어오기 클라이언트 설정](pullClientConfigId.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8c452-141">For information about configuring a pull server by using **ConfigurationID**, see [Setting up a pull client using configuration ID](pullClientConfigId.md)</span></span>

- <span data-ttu-id="8c452-142">**ConfigurationNames** 속성은 클라이언트 노드용으로 의도된 구성의 이름을 지정하는 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="8c452-142">The **ConfigurationNames** property is an array that specifies the names of the configurations intended for the client node.</span></span>
  ><span data-ttu-id="8c452-143">**참고:** **ConfigurationNames**에 둘 이상의 값을 지정하는 경우 구성에서 **PartialConfiguration** 블록도 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c452-143">**Note:** If you specify more than one value in the **ConfigurationNames**, you must also specify **PartialConfiguration** blocks in your configuration.</span></span>
  ><span data-ttu-id="8c452-144">부분 구성에 대한 자세한 내용은 [PowerShell 필요한 상태 구성 부분 구성](partialConfigs.md) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8c452-144">For information about partial configurations, see [PowerShell Desired State Configuration partial configurations](partialConfigs.md).</span></span>

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

## <a name="set-up-a-pull-client-to-download-resources"></a><span data-ttu-id="8c452-145">리소스를 다운로드하도록 끌어오기 클라이언트 설정</span><span class="sxs-lookup"><span data-stu-id="8c452-145">Set up a Pull Client to download Resources</span></span>

<span data-ttu-id="8c452-146">앞의 예와 같이 LCM 구성에서 **ConfigurationRepositoryWeb** 또는 **ConfigurationRepositoryShare** 블록만 지정하는 경우 끌어오기 클라이언트는 ".mof" 파일이 저장된 동일한 위치로부터 리소스를 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="8c452-146">If you specify only a **ConfigurationRepositoryWeb** or **ConfigurationRepositoryShare** block in your LCM configuration (as in the previous example), the pull client will pull resources from same location where your ".mof" files are stored.</span></span> <span data-ttu-id="8c452-147">클라이언트가 리소스를 다운로드할 수 있는 다른 위치를 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c452-147">You can also specify different locations where clients can download resources.</span></span> <span data-ttu-id="8c452-148">리소스 서버를 지정하려면, **ResourceRepositoryWeb**(웹 끌어오기 서버용) 및 **ResourceRepositoryShare**(SMB 끌어오기 서버용) 블록을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8c452-148">To specify a resource server, you use either a **ResourceRepositoryWeb** (for a web pull server) or a **ResourceRepositoryShare** block (for an SMB pull server).</span></span>

<span data-ttu-id="8c452-149">다음 예제에서는 끌어오기 서버로부터 구성을 다운로드하고, SMB 공유로부터 리소스를 다운로드하도록 클라이언트를 설정하는 메타 구성을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="8c452-149">The following example shows a metaconfiguration that sets up a client to download configurations from a Pull Server, and resources from an SMB share.</span></span>

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

## <a name="set-up-a-pull-client-to-report-status"></a><span data-ttu-id="8c452-150">상태를 보고하도록 끌어오기 클라이언트 설정</span><span class="sxs-lookup"><span data-stu-id="8c452-150">Set up a Pull Client to report status</span></span>

<span data-ttu-id="8c452-151">구성, 리소스 및 보고에 단일 끌어오기 서버를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c452-151">You can use a single pull server for configurations, resources, and reporting.</span></span> <span data-ttu-id="8c452-152">보고는 기본적으로 클라이언트에서 구성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8c452-152">Reporting is not configured for clients by default.</span></span> <span data-ttu-id="8c452-153">상태를 보고하도록 클라이언트를 구성하려면 **ReportRepositoryWeb** 블록을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c452-153">To configure a client to report status, you have to create a **ReportRepositoryWeb** block.</span></span> <span data-ttu-id="8c452-154">다음 예제에서는 구성 및 리소스를 끌어오고 보고 데이터를 단일 서버에 보내도록 클라이언트를 설정하는 메타 구성을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8c452-154">The following example shows a metaconfiguration that sets up a client to pull configurations and resources, and send reporting data, to a single pull server.</span></span>

> [!NOTE]
> <span data-ttu-id="8c452-155">보고서 서버는 SMB 공유일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8c452-155">A report server cannot be an SMB share.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="8c452-156">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8c452-156">See Also</span></span>

* [<span data-ttu-id="8c452-157">구성 ID를 사용하여 끌어오기 클라이언트 설정</span><span class="sxs-lookup"><span data-stu-id="8c452-157">Setting up a pull client with configuration ID</span></span>](PullClientConfigNames.md)
* [<span data-ttu-id="8c452-158">DSC 웹 끌어오기 서버 설정</span><span class="sxs-lookup"><span data-stu-id="8c452-158">Setting up a DSC web pull server</span></span>](pullServer.md)
