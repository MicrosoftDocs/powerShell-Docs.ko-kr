---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: PowerShell 5.0 이상 구성 이름을 사용 하 여 끌어오기 클라이언트 설정
ms.openlocfilehash: fd038a105da7a83ecad9b571e611b65c8ec847b3
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53403031"
---
# <a name="set-up-a-pull-client-using-configuration-names-in-powershell-50-and-later"></a><span data-ttu-id="2c011-103">PowerShell 5.0 이상 구성 이름을 사용 하 여 끌어오기 클라이언트 설정</span><span class="sxs-lookup"><span data-stu-id="2c011-103">Set up a Pull Client using Configuration Names in PowerShell 5.0 and later</span></span>

> <span data-ttu-id="2c011-104">적용 대상: Windows Powershell 5.0</span><span class="sxs-lookup"><span data-stu-id="2c011-104">Applies To: Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2c011-105">끌어오기 서버(Windows 기능 *DSC-Service*)는 Windows Server의 지원되는 구성 요소이지만 새로운 기능을 제공할 계획은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2c011-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="2c011-106">관리되는 클라우드를 [Azure Automation DSC](/azure/automation/automation-dsc-getting-started)(Windows Server에 끌어오기 서버 이외의 기능 포함) 또는 [여기](pullserver.md#community-solutions-for-pull-service)에 나열된 커뮤니티 솔루션 중 하나로 전환하기 시작하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="2c011-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="2c011-107">끌어오기 클라이언트를 설정 하기 전에 끌어오기 서버 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c011-107">Before setting up a pull client, you should set up a pull server.</span></span> <span data-ttu-id="2c011-108">이 순서 필요 하지 않은 경우 문제 해결에 도움이 됩니다 하 고 등록 되었는지 확인 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c011-108">Though this order is not required, it helps with troubleshooting, and helps you ensure that the registration was successful.</span></span> <span data-ttu-id="2c011-109">끌어오기 서버를 설정 하려면 다음 가이드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c011-109">To set up a pull server, you can use the following guides:</span></span>

- [<span data-ttu-id="2c011-110">DSC SMB 끌어오기 서버 설정</span><span class="sxs-lookup"><span data-stu-id="2c011-110">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="2c011-111">DSC HTTP 끌어오기 서버 설정</span><span class="sxs-lookup"><span data-stu-id="2c011-111">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="2c011-112">각 대상 노드를 구성, 리소스를 다운로드 하 여 해당 상태를 보고할 수도 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c011-112">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="2c011-113">아래 섹션에서는 SMB 공유 또는 HTTP DSC 끌어오기 서버를 사용 하 여 끌어오기 클라이언트를 구성 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2c011-113">The sections below show you how to configure a pull client with an SMB share or HTTP DSC Pull Server.</span></span> <span data-ttu-id="2c011-114">노드의 LCM 새로 고쳐지면 모든 할당 된 구성을 다운로드 하는 구성 된 위치에 연락을 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c011-114">When the Node's LCM refreshes, it will reach out to the configured location to download any assigned configurations.</span></span> <span data-ttu-id="2c011-115">노드에서 필요한 모든 리소스가 존재 하지 않는 경우 자동으로 다운로드 하는 구성 된 위치에서.</span><span class="sxs-lookup"><span data-stu-id="2c011-115">If any required resources do not exist on the Node, it will automatically download them from the configured location.</span></span> <span data-ttu-id="2c011-116">노드를 사용 하 여 구성 하는 경우는 [보고서 서버](reportServer.md), 다음 작업의 상태를 보고 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c011-116">If the Node is configured with a [Report Server](reportServer.md), it will then report the status of the operation.</span></span>

> <span data-ttu-id="2c011-117">**참고**: 이 항목은 PowerShell 5.0에 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c011-117">**Note**: This topic applies to PowerShell 5.0.</span></span>
<span data-ttu-id="2c011-118">PowerShell 4.0에서 끌어오기 클라이언트 설정에 대 한 자세한 내용은 [PowerShell 4.0에서 구성 ID를 사용 하 여 끌어오기 클라이언트 설정](pullClientConfigID4.md)</span><span class="sxs-lookup"><span data-stu-id="2c011-118">For information on setting up a pull client in PowerShell 4.0, see [Set up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md)</span></span>

## <a name="configure-the-pull-client-lcm"></a><span data-ttu-id="2c011-119">끌어오기 클라이언트를 LCM 구성</span><span class="sxs-lookup"><span data-stu-id="2c011-119">Configure the pull client LCM</span></span>

<span data-ttu-id="2c011-120">라는 새 출력 폴더를 만들고 아래 예제 중 하나를 실행 **PullClientConfigName** 넣습니다 메타 구성 MOF 파일이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c011-120">Executing any of the examples below creates a new output folder named **PullClientConfigName** and puts a metaconfiguration MOF file there.</span></span> <span data-ttu-id="2c011-121">이 경우 메타 구성 MOF 파일의 이름은 `localhost.meta.mof`로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c011-121">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="2c011-122">구성을 적용하려면 메타 구성 MOF 파일의 위치로 설정된 **Path**와 함께 **Set-DscLocalConfigurationManager** cmdlet을 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="2c011-122">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span> <span data-ttu-id="2c011-123">예:</span><span class="sxs-lookup"><span data-stu-id="2c011-123">For example:</span></span>

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigName –Verbose.
```

## <a name="configuration-name"></a><span data-ttu-id="2c011-124">구성 이름</span><span class="sxs-lookup"><span data-stu-id="2c011-124">Configuration Name</span></span>

<span data-ttu-id="2c011-125">설정 아래 예제는 **ConfigurationName** 이 목적을 위해 이전에 컴파일된 구성의 이름에 LCM의 속성 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c011-125">The examples below sets the **ConfigurationName** property of the LCM to the name of a previously compiled Configuration, created for this purpose.</span></span> <span data-ttu-id="2c011-126">합니다 **ConfigurationName** LCM 끌어오기 서버에서 적절 한 구성의 찾는 데 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c011-126">The **ConfigurationName** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="2c011-127">끌어오기 서버의 구성 MOF 파일의 이름은 `<ConfigurationName>.mof`,이 경우 "ClientConfig.mof"입니다.</span><span class="sxs-lookup"><span data-stu-id="2c011-127">The configuration MOF file on the pull server must be named `<ConfigurationName>.mof`, in this case, "ClientConfig.mof".</span></span> <span data-ttu-id="2c011-128">자세한 내용은 [끌어오기 서버 (v4/v5) 구성을 게시](publishConfigs.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="2c011-128">For more information, see [Publish Configurations to a Pull Server (v4/v5)](publishConfigs.md).</span></span>

## <a name="set-up-a-pull-client-to-download-configurations"></a><span data-ttu-id="2c011-129">구성 다운로드를 끌어오기 클라이언트 설정</span><span class="sxs-lookup"><span data-stu-id="2c011-129">Set up a Pull Client to download Configurations</span></span>

<span data-ttu-id="2c011-130">각 클라이언트에서 구성 해야 **끌어오기** 모드의 구성이 저장 된 끌어오기 서버 url을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c011-130">Each client must be configured in **Pull** mode and given the pull server url where its configuration is stored.</span></span> <span data-ttu-id="2c011-131">이를 수행하려면, 필요한 정보와 함께 LCM(로컬 구성 관리자)을 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c011-131">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="2c011-132">LCM을 구성하려면 **DSCLocalConfigurationManager** 특성으로 데코레이팅된 특별한 형식의 구성을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2c011-132">To configure the LCM, you create a special type of configuration, decorated with the **DSCLocalConfigurationManager** attribute.</span></span> <span data-ttu-id="2c011-133">LCM 구성에 대한 자세한 내용은 [로컬 구성 관리자 구성](../managing-nodes/metaConfig.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2c011-133">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md).</span></span>

<span data-ttu-id="2c011-134">다음 스크립트는 "CONTOSO-PullSrv"라는 서버에서 구성을 끌어오도록 LCM을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="2c011-134">The following script configures the LCM to pull configurations from a server named "CONTOSO-PullSrv".</span></span>

- <span data-ttu-id="2c011-135">스크립트에서 **ConfigurationRepositoryWeb** 블록은 끌어오기 서버를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="2c011-135">In the script, the **ConfigurationRepositoryWeb** block defines the pull server.</span></span> <span data-ttu-id="2c011-136">**ServerURL** 속성은 끌어오기 서버에 대한 엔드포인트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2c011-136">The **ServerURL** property specifies the endpoint for the pull server.</span></span>

- <span data-ttu-id="2c011-137">**RegistrationKey** 속성은 끌어오기 서버에 대한 모든 클라이언트 노드와 해당 끌어오기 서버 간의 공유 키입니다.</span><span class="sxs-lookup"><span data-stu-id="2c011-137">The **RegistrationKey** property is a shared key between all client nodes for a pull server and that pull server.</span></span> <span data-ttu-id="2c011-138">동일한 값이 끌어오기 서버에 있는 파일에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c011-138">The same value is stored in a file on the pull server.</span></span>
  > <span data-ttu-id="2c011-139">**참고**: 등록 키는에 작동 **웹** 끌어오기 서버.</span><span class="sxs-lookup"><span data-stu-id="2c011-139">**Note**: Registration keys work only with **web** pull servers.</span></span> <span data-ttu-id="2c011-140">**SMB** 끌어오기 서버에는 여전히 **ConfigurationID**를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c011-140">You must still use **ConfigurationID** with an **SMB** pull server.</span></span>
  > <span data-ttu-id="2c011-141">**ConfigurationID**를 사용하여 끌어오기 서버를 구성하는 것에 대해서는 [구성 ID를 사용하여 끌어오기 클라이언트 설정](pullClientConfigId.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2c011-141">For information about configuring a pull server by using **ConfigurationID**, see [Setting up a pull client using configuration ID](pullClientConfigId.md)</span></span>

- <span data-ttu-id="2c011-142">**ConfigurationNames** 속성은 클라이언트 노드용으로 의도된 구성의 이름을 지정하는 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="2c011-142">The **ConfigurationNames** property is an array that specifies the names of the configurations intended for the client node.</span></span>
  ><span data-ttu-id="2c011-143">**참고:** **ConfigurationNames**에 둘 이상의 값을 지정하는 경우 구성에서 **PartialConfiguration** 블록도 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c011-143">**Note:** If you specify more than one value in the **ConfigurationNames**, you must also specify **PartialConfiguration** blocks in your configuration.</span></span>
  ><span data-ttu-id="2c011-144">부분 구성에 대한 자세한 내용은 [PowerShell 필요한 상태 구성 부분 구성](partialConfigs.md) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2c011-144">For information about partial configurations, see [PowerShell Desired State Configuration partial configurations](partialConfigs.md).</span></span>

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

## <a name="set-up-a-pull-client-to-download-resources"></a><span data-ttu-id="2c011-145">리소스를 다운로드 하 여 끌어오기 클라이언트 설정</span><span class="sxs-lookup"><span data-stu-id="2c011-145">Set up a Pull Client to download Resources</span></span>

<span data-ttu-id="2c011-146">만 지정한 경우는 **ConfigurationRepositoryWeb** 하거나 **ConfigurationRepositoryShare** 이전 예에서 같이 LCM 구성에서 블록에서 끌어오기 클라이언트에서 동일한 리소스를 가져올 ".mof" 파일로 저장 된 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="2c011-146">If you specify only a **ConfigurationRepositoryWeb** or **ConfigurationRepositoryShare** block in your LCM configuration (as in the previous example), the pull client will pull resources from same location where your ".mof" files are stored.</span></span> <span data-ttu-id="2c011-147">또한 클라이언트가 리소스를 다운로드할 수 있는 다른 위치를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c011-147">You can also specify different locations where clients can download resources.</span></span> <span data-ttu-id="2c011-148">리소스 서버를 지정하려면, **ResourceRepositoryWeb**(웹 끌어오기 서버용) 및 **ResourceRepositoryShare**(SMB 끌어오기 서버용) 블록을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2c011-148">To specify a resource server, you use either a **ResourceRepositoryWeb** (for a web pull server) or a **ResourceRepositoryShare** block (for an SMB pull server).</span></span>

<span data-ttu-id="2c011-149">다음 예제에서는 구성 끌어오기 서버에 SMB 공유에서 리소스를 다운로드 하도록 클라이언트를 설정 하는 메타 구성을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2c011-149">The following example shows a metaconfiguration that sets up a client to download configurations from a Pull Server, and resources from an SMB share.</span></span>

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

## <a name="set-up-a-pull-client-to-report-status"></a><span data-ttu-id="2c011-150">상태 보고에 대 한 끌어오기 클라이언트 설정</span><span class="sxs-lookup"><span data-stu-id="2c011-150">Set up a Pull Client to report status</span></span>

<span data-ttu-id="2c011-151">구성, 리소스 및 보고에 대 한 단일 끌어오기 서버를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c011-151">You can use a single pull server for configurations, resources, and reporting.</span></span> <span data-ttu-id="2c011-152">보고는 기본적으로 클라이언트에 대 한 구성 되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="2c011-152">Reporting is not configured for clients by default.</span></span> <span data-ttu-id="2c011-153">만들 필요가 클라이언트 상태 보고를 구성 하는 **ReportRepositoryWeb** 블록입니다.</span><span class="sxs-lookup"><span data-stu-id="2c011-153">To configure a client to report status, you have to create a **ReportRepositoryWeb** block.</span></span> <span data-ttu-id="2c011-154">다음 예제에서는 구성 및 리소스를 끌어오고 보고 데이터를 단일 서버에 보내도록 클라이언트를 설정하는 메타 구성을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2c011-154">The following example shows a metaconfiguration that sets up a client to pull configurations and resources, and send reporting data, to a single pull server.</span></span>

> [!NOTE]
> <span data-ttu-id="2c011-155">보고서 서버는 SMB 공유 일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2c011-155">A report server cannot be an SMB share.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="2c011-156">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2c011-156">See Also</span></span>

* [<span data-ttu-id="2c011-157">구성 ID를 사용하여 끌어오기 클라이언트 설정</span><span class="sxs-lookup"><span data-stu-id="2c011-157">Setting up a pull client with configuration ID</span></span>](PullClientConfigNames.md)
* [<span data-ttu-id="2c011-158">DSC 웹 끌어오기 서버 설정</span><span class="sxs-lookup"><span data-stu-id="2c011-158">Setting up a DSC web pull server</span></span>](pullServer.md)
