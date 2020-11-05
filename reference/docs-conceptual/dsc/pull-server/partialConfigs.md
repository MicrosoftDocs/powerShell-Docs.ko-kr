---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: PowerShell 필요한 상태 구성 부분 구성
description: DSC를 사용하면 구성을 여러 소스에서 조각화하여 제공할 수 있습니다. 대상 노드의 LCM은 이 조각들을 한데 모아 하나의 구성으로 적용합니다.
ms.openlocfilehash: 3afe5d684cabec9c8ab528347610b6dd00c5d4e9
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92661609"
---
# <a name="powershell-desired-state-configuration-partial-configurations"></a><span data-ttu-id="9d6f2-105">PowerShell 필요한 상태 구성 부분 구성</span><span class="sxs-lookup"><span data-stu-id="9d6f2-105">PowerShell Desired State Configuration partial configurations</span></span>

> <span data-ttu-id="9d6f2-106">적용 대상: Windows PowerShell 5.0 이상</span><span class="sxs-lookup"><span data-stu-id="9d6f2-106">Applies To: Windows PowerShell 5.0 and later.</span></span>

<span data-ttu-id="9d6f2-107">PowerShell 5.0에서 DSC(필요한 상태 구성)를 사용하면 구성을 여러 소스에서 조각화하여 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d6f2-107">In PowerShell 5.0, Desired State Configuration (DSC) allows configurations to be delivered in fragments and from multiple sources.</span></span> <span data-ttu-id="9d6f2-108">대상 노드의 LCM(로컬 구성 관리자)은 이 조각들을 한데 모아 하나의 구성으로 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="9d6f2-108">The Local Configuration Manager (LCM) on the target node puts the fragments together before applying them as a single configuration.</span></span> <span data-ttu-id="9d6f2-109">이 기능을 사용하면 구성에 대한 제어권을 팀이나 개인들 간에 공유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d6f2-109">This capability allows sharing control of configuration between teams or individuals.</span></span> <span data-ttu-id="9d6f2-110">예를 들어 두 개 이상의 개발자 팀이 어떤 서비스에 대해 공동으로 작업 중인 경우 이들은 각각 서비스의 해당 부분을 관리하는 구성을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d6f2-110">For example, if two or more teams of developers are collaborating on a service, they might each want to create configurations to manage their part of the service.</span></span> <span data-ttu-id="9d6f2-111">이 구성들의 각각은 서로 다른 끌어오기 서버에서 가져올 수 있으며, 개발의 서로 다른 단계에서 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d6f2-111">Each of these configurations could be pulled from different pull servers, and they could be added at different stages of development.</span></span> <span data-ttu-id="9d6f2-112">부분 구성은 또한 서로 다른 개인이나 팀이 단일 구성 문서에 대한 편집 작업을 조정하지 않고도 노드 구성의 다양한 측면을 제어할 수 있도록 해줍니다.</span><span class="sxs-lookup"><span data-stu-id="9d6f2-112">Partial configurations also allow different individuals or teams to control different aspects of configuring nodes without having to coordinate the editing of a single configuration document.</span></span> <span data-ttu-id="9d6f2-113">예를 들어 한 팀은 VM과 운영 체제를 배포하는 일을 담당하고, 다른 팀은 해당 VM에서 다른 애플리케이션과 서비스를 배포할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d6f2-113">For example, one team might be responsible for deploying a VM and operating system, while another team might deploy other applications and services on that VM.</span></span> <span data-ttu-id="9d6f2-114">부분 구성을 사용하면 어느 한 팀이 불필요하게 복잡해지지 않고 각 팀이 해당 팀의 구성을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d6f2-114">With partial configurations, each team can create its own configuration, without either of them being unnecessarily complicated.</span></span>

<span data-ttu-id="9d6f2-115">밀어넣기 모드, 끌어오기 모드 또는 두 모드의 조합 모드에서 부분 구성을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d6f2-115">You can use partial configurations in push mode, pull mode, or a combination of the two.</span></span>

## <a name="partial-configurations-in-push-mode"></a><span data-ttu-id="9d6f2-116">밀어넣기 모드의 부분 구성</span><span class="sxs-lookup"><span data-stu-id="9d6f2-116">Partial configurations in push mode</span></span>

<span data-ttu-id="9d6f2-117">밀어넣기 모드에서 부분 구성을 사용하려면 부분 구성을 받도록 대상 노드의 LCM을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="9d6f2-117">To use partial configurations in push mode, you configure the LCM on the target node to receive the partial configurations.</span></span> <span data-ttu-id="9d6f2-118">각 부분 구성은 `Publish-DSCConfiguration` cmdlet을 사용하여 대상에 밀어넣어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d6f2-118">Each partial configuration must be pushed to the target by using the `Publish-DSCConfiguration` cmdlet.</span></span> <span data-ttu-id="9d6f2-119">그런 다음 대상 노드가 부분 구성을 단일 구성으로 결합하면 작업자는 [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet을 호출하여 구성을 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d6f2-119">The target node then combines the partial configuration into a single configuration, and you can apply the configuration by calling the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span>

### <a name="configuring-the-lcm-for-push-mode-partial-configurations"></a><span data-ttu-id="9d6f2-120">밀어넣기 모드 부분 구성에 대한 LCM 구성</span><span class="sxs-lookup"><span data-stu-id="9d6f2-120">Configuring the LCM for push-mode partial configurations</span></span>

<span data-ttu-id="9d6f2-121">밀어넣기 모드에서 부분 구성에 대해 LCM을 구성하려면, 각 부분 구성에 대해 하나의 **PartialConfiguration** 블록으로 **DSCLocalConfigurationManager** 구성을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9d6f2-121">To configure the LCM for partial configurations in push mode, you create a **DSCLocalConfigurationManager** configuration with one **PartialConfiguration** block for each partial configuration.</span></span> <span data-ttu-id="9d6f2-122">LCM 구성에 대한 자세한 내용은[로컬 구성 관리자 구성](../managing-nodes/metaConfig.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9d6f2-122">For more information about configuring the LCM, see [Windows Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md).</span></span> <span data-ttu-id="9d6f2-123">다음 예제에서는 두 개의 부분 구성이 예상되는 LCM 구성을 보여 줍니다. 하나는 OS를 배포하고 다른 하나는 SharePoint를 배포 및 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="9d6f2-123">The following example shows an LCM configuration that expects two partial configurations—one that deploys the OS, and one that deploys and configures SharePoint.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PartialConfigDemo
{
    Node localhost
    {

        PartialConfiguration ServiceAccountConfig
        {
            Description = 'Configuration to add the SharePoint service account to the Administrators group.'
            RefreshMode = 'Push'
        }
           PartialConfiguration SharePointConfig
        {
            Description = 'Configuration for the SharePoint server'
            RefreshMode = 'Push'
        }
    }
}

PartialConfigDemo
```

<span data-ttu-id="9d6f2-124">각 부분 구성에 대해 **RefreshMode** 는 "Push"로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d6f2-124">The **RefreshMode** for each partial configuration is set to "Push".</span></span> <span data-ttu-id="9d6f2-125">**PartialConfiguration** 블록의 이름(이 경우 "ServiceAccountConfig" 및 "SharePointConfig")은 대상 노드에 밀어넣은 구성의 이름과 정확하게 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d6f2-125">The names of the **PartialConfiguration** blocks (in this case, "ServiceAccountConfig" and "SharePointConfig") must match exactly the names of the configurations that are pushed to the target node.</span></span>

> [!Note]
> <span data-ttu-id="9d6f2-126">각각의 명명된 **PartialConfiguration** 블록은 MOF 파일의 이름이 아니라 구성 스크립트에 지정된 구성의 실제 이름과 일치해야 하며, 이 이름은 대상 노드 또는 `localhost`의 이름이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d6f2-126">The named of each **PartialConfiguration** block must match the actual name of the configuration as it is specified in the configuration script, not the name of the MOF file, which should be either the name of the target node or `localhost`.</span></span>

### <a name="publishing-and-starting-push-mode-partial-configurations"></a><span data-ttu-id="9d6f2-127">밀어넣기 모드 부분 구성 게시 및 시작</span><span class="sxs-lookup"><span data-stu-id="9d6f2-127">Publishing and starting push-mode partial configurations</span></span>

<span data-ttu-id="9d6f2-128">그런 다음 각 구성에 대해 [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration)을 호출하여 **Path** 매개 변수로서 구성 문서를 포함하는 폴더를 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="9d6f2-128">You then call [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) for each configuration, passing the folders that contain the configuration documents as the **Path** parameters.</span></span> <span data-ttu-id="9d6f2-129">`Publish-DSCConfiguration`은 구성 MOF 파일을 대상 노드에 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="9d6f2-129">`Publish-DSCConfiguration`places the configuration MOF files to the target nodes.</span></span> <span data-ttu-id="9d6f2-130">두 구성을 모두 게시한 후에는 대상 노드에서 `Start-DSCConfiguration –UseExisting`을 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d6f2-130">After publishing both configurations, you can call `Start-DSCConfiguration –UseExisting` on the target node.</span></span>

<span data-ttu-id="9d6f2-131">예를 들어 다음과 같은 구성 MOF 문서를 제작 노드에 컴파일한다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="9d6f2-131">For example, if you have compiled the following configuration MOF documents on the authoring node:</span></span>

```powershell
Get-ChildItem -Recurse
```

```output
    Directory: C:\PartialConfigTest

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        8/11/2016   1:55 PM                ServiceAccountConfig
d-----       11/17/2016   4:14 PM                SharePointConfig

    Directory: C:\PartialConfigTest\ServiceAccountConfig

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        8/11/2016   2:02 PM           2034 TestVM.mof

    Directory: C:\PartialConfigTest\SharePointConfig

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       11/17/2016   4:14 PM           1930 TestVM.mof
```

<span data-ttu-id="9d6f2-132">다음과 같이 구성을 게시하고 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="9d6f2-132">You would publish and run the configurations as follows:</span></span>

```powershell
Publish-DscConfiguration .\ServiceAccountConfig -ComputerName 'TestVM'
Publish-DscConfiguration .\SharePointConfig -ComputerName 'TestVM'
Start-DscConfiguration -UseExisting -ComputerName 'TestVM'
```

```output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
17     Job17           Configuratio... Running       True            TestVM            Start-DscConfiguration...
```

> [!Note]
> <span data-ttu-id="9d6f2-133">[Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) cmdlet을 실행하는 사용자는 대상 노드에 대한 관리자 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d6f2-133">The user running the [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) cmdlet must have administrator privileges on the target node.</span></span>

## <a name="partial-configurations-in-pull-mode"></a><span data-ttu-id="9d6f2-134">끌어오기 모드의 부분 구성</span><span class="sxs-lookup"><span data-stu-id="9d6f2-134">Partial configurations in pull mode</span></span>

<span data-ttu-id="9d6f2-135">구성 부분은 하나 이상의 끌어오기 서버에서 끌어올 수 있습니다(끌어오기 서버에 대한 자세한 내용은 [Windows PowerShell 필요한 상태 구성 끌어오기 서버](pullServer.md) 참조).</span><span class="sxs-lookup"><span data-stu-id="9d6f2-135">Partial configurations can be pulled from one or more pull servers (for more information about pull servers, see [Windows PowerShell Desired State Configuration Pull Servers](pullServer.md).</span></span> <span data-ttu-id="9d6f2-136">이렇게 하려면 대상 노드에서 LCM을 구성하여 부분 구성을 끌어오고, 끌어오기 서버에서 구성 문서의 이름을 지정하고 이 문서를 배치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d6f2-136">To do this, you have to configure the LCM on the target node to pull the partial configurations, and name and locate the configuration documents properly on the pull servers.</span></span>

### <a name="configuring-the-lcm-for-pull-node-configurations"></a><span data-ttu-id="9d6f2-137">끌어오기 노드 구성을 위한 LCM 구성</span><span class="sxs-lookup"><span data-stu-id="9d6f2-137">Configuring the LCM for pull node configurations</span></span>

<span data-ttu-id="9d6f2-138">끌어오기 서버에서 부분 구성을 가져오도록 LCM을 구성하려면 **ConfigurationRepositoryWeb** (HTTP 끌어오기 서버용) 또는 **ConfigurationRepositoryShare** (SMB 끌어오기 서버용) 블록에서 끌어오기 서버를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="9d6f2-138">To configure the LCM to pull partial configurations from a pull server, you define the pull server in either a **ConfigurationRepositoryWeb** (for an HTTP pull server) or **ConfigurationRepositoryShare** (for an SMB pull server) block.</span></span> <span data-ttu-id="9d6f2-139">그런 다음 **ConfigurationSource** 속성을 사용하여 끌어오기 서버를 참조하는 **PartialConfiguration** 블록을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9d6f2-139">You then create **PartialConfiguration** blocks that refer to the pull server by using the **ConfigurationSource** property.</span></span> <span data-ttu-id="9d6f2-140">또한 LCM이 끌어오기 모드를 사용한다고 지정하고, 끌어오기 서버 및 대상 노드가 구성을 식별하는 데 사용하는 **ConfigurationNames** 또는 **ConfigurationID** 를 지정하기 위한 **설정** 블록을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d6f2-140">You also need to create a **Settings** block to specify that the LCM uses pull mode, and to specify the **ConfigurationNames** or **ConfigurationID** that the pull server and target node use to identify the configurations.</span></span> <span data-ttu-id="9d6f2-141">다음의 메타 구성은 CONTOSO PullSrv라는 HTTP 끌어오기 서버와, 해당 끌어오기 서버를 사용하는 두 개의 부분 구성을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="9d6f2-141">The following meta-configuration defines an HTTP pull server named CONTOSO-PullSrv and two partial configurations that use that pull server.</span></span>

<span data-ttu-id="9d6f2-142">**ConfigurationNames** 를 사용하여 LCM을 구성하는 방법에 대해서는 [구성 이름을 사용하여 끌어오기 클라이언트 설정](pullClientConfigNames.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9d6f2-142">For more information about configuring the LCM using **ConfigurationNames** , see [Setting up a pull client using configuration names](pullClientConfigNames.md).</span></span> <span data-ttu-id="9d6f2-143">**ConfigurationID** 를 사용하여 LCM을 구성하는 방법에 대해서는 [구성 ID를 사용하여 끌어오기 클라이언트 설정](pullClientConfigID.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9d6f2-143">For information about configuring the LCM using **ConfigurationID** , see [Setting up a pull client using configuration ID](pullClientConfigID.md).</span></span>

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configuration-names"></a><span data-ttu-id="9d6f2-144">구성 이름을 사용하여 끌어오기 모드 구성에 대해 LCM 구성</span><span class="sxs-lookup"><span data-stu-id="9d6f2-144">Configuring the LCM for pull mode configurations using configuration names</span></span>

```powershell
[DscLocalConfigurationManager()]
Configuration PartialConfigDemoConfigNames
{
        Settings
        {
            RefreshFrequencyMins            = 30;
            RefreshMode                     = "PULL";
            ConfigurationMode               ="ApplyAndAutocorrect";
            AllowModuleOverwrite            = $true;
            RebootNodeIfNeeded              = $true;
            ConfigurationModeFrequencyMins  = 60;
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL                       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey                 = 5b41f4e6-5e6d-45f5-8102-f2227468ef38
            ConfigurationNames              = @("ServiceAccountConfig", "SharePointConfig")
        }

        PartialConfiguration ServiceAccountConfig
        {
            Description                     = "ServiceAccountConfig"
            ConfigurationSource             = @("[ConfigurationRepositoryWeb]CONTOSO-PullSrv")
        }

        PartialConfiguration SharePointConfig
        {
            Description                     = "SharePointConfig"
            ConfigurationSource             = @("[ConfigurationRepositoryWeb]CONTOSO-PullSrv")
            DependsOn                       = '[PartialConfiguration]ServiceAccountConfig'
        }
}
```

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configurationid"></a><span data-ttu-id="9d6f2-145">ConfigurationID를 사용하여 끌어오기 모드 구성에 대해 LCM 구성</span><span class="sxs-lookup"><span data-stu-id="9d6f2-145">Configuring the LCM for pull mode configurations using ConfigurationID</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PartialConfigDemoConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode                     = 'Pull'
            ConfigurationID                 = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins            = 30
            RebootNodeIfNeeded              = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL                       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

           PartialConfiguration ServiceAccountConfig
        {
            Description                     = 'Configuration for the Base OS'
            ConfigurationSource             = '[ConfigurationRepositoryWeb]CONTOSO-PullSrv'
            RefreshMode                     = 'Pull'
        }
           PartialConfiguration SharePointConfig
        {
            Description                     = 'Configuration for the Sharepoint Server'
            ConfigurationSource             = '[ConfigurationRepositoryWeb]CONTOSO-PullSrv'
            DependsOn                       = '[PartialConfiguration]ServiceAccountConfig'
            RefreshMode                     = 'Pull'
        }
    }
}
PartialConfigDemo
```

<span data-ttu-id="9d6f2-146">둘 이상의 끌어오기 서버에서 부분 구성을 끌어올 수 있습니다. 각 끌어오기 서버를 정의한 다음, 각 **PartialConfiguration** 블록에서 적절한 끌어오기 서버를 참조하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d6f2-146">You can pull partial configurations from more than one pull server—you would just need to define each pull server, and then refer to the appropriate pull server in each **PartialConfiguration** block.</span></span>

<span data-ttu-id="9d6f2-147">메타 구성을 만든 후 실행하여 구성 문서(MOF 파일)를 만들고 [Set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager)를 호출하여 LCM을 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d6f2-147">After creating the meta-configuration, you must run it to create a configuration document (a MOF file), and then call [Set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) to configure the LCM.</span></span>

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationnames"></a><span data-ttu-id="9d6f2-148">끌어오기 서버에서 구성 문서 이름 지정 및 배치(ConfigurationNames)</span><span class="sxs-lookup"><span data-stu-id="9d6f2-148">Naming and placing the configuration documents on the pull server (ConfigurationNames)</span></span>

<span data-ttu-id="9d6f2-149">부분 구성 문서는 끌어오기 서버용의 `web.config` 파일에서 **ConfigurationPath** 로 지정된 폴더에 배치해야 합니다(일반적으로 `C:\Program
Files\WindowsPowerShell\DscService\Configuration`).</span><span class="sxs-lookup"><span data-stu-id="9d6f2-149">The partial configuration documents must be placed in the folder specified as the **ConfigurationPath** in the `web.config` file for the pull server (typically `C:\Program
Files\WindowsPowerShell\DscService\Configuration`).</span></span>

#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-51"></a><span data-ttu-id="9d6f2-150">PowerShell 5.1의 끌어오기 서버에서 구성 문서 이름 지정</span><span class="sxs-lookup"><span data-stu-id="9d6f2-150">Naming configuration documents on the pull server in PowerShell 5.1</span></span>

<span data-ttu-id="9d6f2-151">개별 끌어오기 서버에서 부분 구성 하나만 끌어오는 경우 구성 문서에 아무 이름이나 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d6f2-151">If you are pulling only one partial configuration from an individual pull server, the configuration document can have any name.</span></span> <span data-ttu-id="9d6f2-152">끌어오기 서버에서 둘 이상의 부분 구성을 끌어오는 경우 구성 문서 이름은 `<ConfigurationName>.mof`(여기서 *ConfigurationName* 은 부분 구성의 이름임) 또는 `<ConfigurationName>.<NodeName>.mof`(여기서 *ConfigurationName* 은 부분 구성의 이름이고 *NodeName* 은 대상 노드의 이름임)로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d6f2-152">If you are pulling more than one partial configuration from a pull server, the configuration document can be named either `<ConfigurationName>.mof`, where *ConfigurationName* is the name of the partial configuration, or `<ConfigurationName>.<NodeName>.mof`, where *ConfigurationName* is the name of the partial configuration, and *NodeName* is the name of the target node.</span></span> <span data-ttu-id="9d6f2-153">따라서 Azure 자동화 DSC 끌어오기 서버에서 구성을 끌어올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d6f2-153">This allows you to pull configurations from Azure Automation DSC pull server.</span></span>

#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-50"></a><span data-ttu-id="9d6f2-154">PowerShell 5.0의 끌어오기 서버에서 구성 문서 이름 지정</span><span class="sxs-lookup"><span data-stu-id="9d6f2-154">Naming configuration documents on the pull server in PowerShell 5.0</span></span>

<span data-ttu-id="9d6f2-155">구성 문서의 이름은 `ConfigurationName.mof`와 같이 지정해야 합니다. 여기서 *ConfigurationName* 은 부분 구성의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="9d6f2-155">The configuration documents must be named as follows: `ConfigurationName.mof`, where *ConfigurationName* is the name of the partial configuration.</span></span> <span data-ttu-id="9d6f2-156">이 예에서 구성 문서의 이름은 다음과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d6f2-156">For our example, the configuration documents should be named as follows:</span></span>

```
ServiceAccountConfig.mof
ServiceAccountConfig.mof.checksum
SharePointConfig.mof
SharePointConfig.mof.checksum
```

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationid"></a><span data-ttu-id="9d6f2-157">끌어오기 서버에서 구성 문서 이름 지정 및 배치(ConfigurationID)</span><span class="sxs-lookup"><span data-stu-id="9d6f2-157">Naming and placing the configuration documents on the pull server (ConfigurationID)</span></span>

<span data-ttu-id="9d6f2-158">부분 구성 문서는 끌어오기 서버용의 `web.config` 파일에서 **ConfigurationPath** 로 지정된 폴더에 배치해야 합니다(일반적으로 `C:\Program Files\WindowsPowerShell\DscService\Configuration`).</span><span class="sxs-lookup"><span data-stu-id="9d6f2-158">The partial configuration documents must be placed in the folder specified as the **ConfigurationPath** in the `web.config` file for the pull server (typically `C:\Program Files\WindowsPowerShell\DscService\Configuration`).</span></span> <span data-ttu-id="9d6f2-159">구성 문서 이름을 다음과 같이 지정해야 합니다. `<ConfigurationName>.<ConfigurationID>.mof`. 여기서 _ConfigurationName_ 은 부분 구성의 이름이고, _ConfigurationID_ 는 대상 노드의 LCM에 정의된 구성 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="9d6f2-159">The configuration documents must be named as follows: `<ConfigurationName>.<ConfigurationID>.mof`, where _ConfigurationName_ is the name of the partial configuration and _ConfigurationID_ is the configuration ID defined in the LCM on the target node.</span></span> <span data-ttu-id="9d6f2-160">이 예에서 구성 문서의 이름은 다음과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d6f2-160">For our example, the configuration documents should be named as follows:</span></span>

```
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
```

### <a name="running-partial-configurations-from-a-pull-server"></a><span data-ttu-id="9d6f2-161">끌어오기 서버에서 부분 구성 실행</span><span class="sxs-lookup"><span data-stu-id="9d6f2-161">Running partial configurations from a pull server</span></span>

<span data-ttu-id="9d6f2-162">대상 노드의 LCM이 구성되고, 구성 문서가 만들어져서 끌어오기 서버에서 적절히 이름이 지정되면, 대상 노드는 부분 구성들을 끌어와서, 결합하고, 그에 따른 결과 구성을 LCM의 **RefreshFrequencyMins** 속성으로 지정한 일정한 간격으로 적용하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d6f2-162">After the LCM on the target node has been configured, and the configuration documents have been created and properly named on the pull server, the target node will pull the partial configurations, combine them, and apply the resulting configuration at regular intervals as specified by the **RefreshFrequencyMins** property of the LCM.</span></span> <span data-ttu-id="9d6f2-163">새로 고침을 강제 적용하려는 경우 [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration) cmdlet을 호출하여 구성을 끌어온 다음, `Start-DSCConfiguration –UseExisting`을 사용하여 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="9d6f2-163">If you want to force a refresh, you can call the [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration) cmdlet, to pull the configurations, and then `Start-DSCConfiguration –UseExisting` to apply them.</span></span>

## <a name="partial-configurations-in-mixed-push-and-pull-modes"></a><span data-ttu-id="9d6f2-164">밀어넣기 및 끌어오기 혼합 모드의 부분 구성</span><span class="sxs-lookup"><span data-stu-id="9d6f2-164">Partial configurations in mixed push and pull modes</span></span>

<span data-ttu-id="9d6f2-165">부분 구성을 위해 밀어넣기 모드와 끌어오기 모드를 혼합할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d6f2-165">You can also mix push and pull modes for partial configurations.</span></span> <span data-ttu-id="9d6f2-166">즉, 끌어오기 서버에서 끌어온 부분 구성 하나와 밀어넣은 또 다른 부분 구성이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d6f2-166">That is, you could have one partial configuration that is pulled from a pull server, while another partial configuration is pushed.</span></span> <span data-ttu-id="9d6f2-167">이전 섹션에 설명된 대로 각 부분 구성에 대해 새로 고침 모드를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9d6f2-167">Specify the refresh mode for each partial configuration as described in the previous sections.</span></span> <span data-ttu-id="9d6f2-168">예를 들어 다음의 메타 구성은 끌어오기 모드의 `ServiceAccountConfig` 부분 구성과 밀어넣기 모드의 `SharePointConfig` 부분 구성으로 같은 예를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="9d6f2-168">For example, the following meta-configuration describes the same example, with the `ServiceAccountConfig` partial configuration in pull mode and the `SharePointConfig` partial configuration in push mode.</span></span>

### <a name="mixed-push-and-pull-modes-using-configurationnames"></a><span data-ttu-id="9d6f2-169">ConfigurationNames를 사용한 혼합된 밀어넣기 및 끌어오기 모드</span><span class="sxs-lookup"><span data-stu-id="9d6f2-169">Mixed push and pull modes using ConfigurationNames</span></span>

```powershell
[DscLocalConfigurationManager()]
Configuration PartialConfigDemoConfigNames
{
        Settings
        {
            RefreshFrequencyMins            = 30;
            RefreshMode                     = "PULL";
            ConfigurationMode               = "ApplyAndAutocorrect";
            AllowModuleOverwrite            = $true;
            RebootNodeIfNeeded              = $true;
            ConfigurationModeFrequencyMins  = 60;
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL                       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey                 = 5b41f4e6-5e6d-45f5-8102-f2227468ef38
            ConfigurationNames              = @("ServiceAccountConfig", "SharePointConfig")
        }

        PartialConfiguration ServiceAccountConfig
        {
            Description                     = "ServiceAccountConfig"
            ConfigurationSource             = @("[ConfigurationRepositoryWeb]CONTOSO-PullSrv")
            RefreshMode                     = 'Pull'
        }

        PartialConfiguration SharePointConfig
        {
            Description                     = "SharePointConfig"
            DependsOn                       = '[PartialConfiguration]ServiceAccountConfig'
            RefreshMode                     = 'Push'
        }

}
```

### <a name="mixed-push-and-pull-modes-using-configurationid"></a><span data-ttu-id="9d6f2-170">ConfigurationID를 사용한 혼합된 밀어넣기 및 끌어오기 모드</span><span class="sxs-lookup"><span data-stu-id="9d6f2-170">Mixed push and pull modes using ConfigurationID</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PartialConfigDemo
{
    Node localhost
    {
        Settings
        {
            RefreshMode             = 'Pull'
            ConfigurationID         = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins    = 30
            RebootNodeIfNeeded      = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL               = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

           PartialConfiguration ServiceAccountConfig
        {
            Description             = 'Configuration for the Base OS'
            ConfigurationSource     = '[ConfigurationRepositoryWeb]CONTOSO-PullSrv'
            RefreshMode             = 'Pull'
        }
           PartialConfiguration SharePointConfig
        {
            Description             = 'Configuration for the Sharepoint Server'
            DependsOn               = '[PartialConfiguration]ServiceAccountConfig'
            RefreshMode             = 'Push'
        }
    }
}
PartialConfigDemo
```

<span data-ttu-id="9d6f2-171">Settings 블록에 지정된 **RefreshMode** 는 "Pull"이지만, `SharePointConfig` 부분 구성에 대한 **RefreshMode** 는 "Push"입니다.</span><span class="sxs-lookup"><span data-stu-id="9d6f2-171">Note that the **RefreshMode** specified in the Settings block is "Pull", but the **RefreshMode** for the `SharePointConfig` partial configuration is "Push".</span></span>

<span data-ttu-id="9d6f2-172">각각의 새로 고침 모드에 대해 위에서 설명한 대로 구성 MOF 파일에 이름을 지정하고 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="9d6f2-172">Name and locate the configuration MOF files as described above for their respective refresh modes.</span></span>
<span data-ttu-id="9d6f2-173">`Publish-DSCConfiguration`을 호출하여 `SharePointConfig` 부분 구성을 게시하고, 끌어오기 서버에서 `ServiceAccountConfig` 구성을 끌어오기를 기다리거나 [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration)을 호출하여 새로 고침을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="9d6f2-173">Call `Publish-DSCConfiguration` to publish the `SharePointConfig` partial configuration, and either wait for the `ServiceAccountConfig` configuration to be pulled from the pull server, or force a refresh by calling [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration).</span></span>

## <a name="example-serviceaccountconfig-partial-configuration"></a><span data-ttu-id="9d6f2-174">ServiceAccountConfig 부분 구성 예</span><span class="sxs-lookup"><span data-stu-id="9d6f2-174">Example ServiceAccountConfig Partial Configuration</span></span>

```powershell
Configuration ServiceAccountConfig
{
    Param (
        [Parameter(Mandatory,
                   HelpMessage="Domain credentials required to add domain\sharepoint_svc to the local Administrators group.")]
        [ValidateNotNullOrEmpty()]
        [pscredential]$Credential
    )

    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node localhost
    {
        Group LocalAdmins
        {
            GroupName           = 'Administrators'
            MembersToInclude    = 'domain\sharepoint_svc',
                                  'admins@example.domain'
            Ensure              = 'Present'
            Credential          = $Credential
        }

        WindowsFeature Telnet
        {
            Name                = 'Telnet-Server'
            Ensure              = 'Absent'
        }
    }
}
ServiceAccountConfig
```

## <a name="example-sharepointconfig-partial-configuration"></a><span data-ttu-id="9d6f2-175">SharePointConfig 부분 구성 예제</span><span class="sxs-lookup"><span data-stu-id="9d6f2-175">Example SharePointConfig Partial Configuration</span></span>

```powershell
Configuration SharePointConfig
{
    Param (
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [pscredential]$ProductKey
    )

    Import-DscResource -ModuleName xSharePoint

    Node localhost
    {
        xSPInstall SharePointDefault
        {
            Ensure      = 'Present'
            BinaryDir   = '\\FileServer\Installers\Sharepoint\'
            ProductKey  = $ProductKey
        }
    }
}
SharePointConfig
```

## <a name="see-also"></a><span data-ttu-id="9d6f2-176">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9d6f2-176">See Also</span></span>

[<span data-ttu-id="9d6f2-177">Windows PowerShell 필요한 상태 구성 끌어오기 서버</span><span class="sxs-lookup"><span data-stu-id="9d6f2-177">Windows PowerShell Desired State Configuration Pull Servers</span></span>](pullServer.md)

[<span data-ttu-id="9d6f2-178">Configuring the Local Configuration Manager(로컬 구성 관리자 구성)</span><span class="sxs-lookup"><span data-stu-id="9d6f2-178">Windows Configuring the Local Configuration Manager</span></span>](../managing-nodes/metaConfig.md)
