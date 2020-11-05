---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: 초기 부팅 시 DSC를 사용하여 가상 컴퓨터 구성
description: 이 문서에서는 초기 부팅 시 DSC를 사용하여 가상 머신을 구성하는 방법을 설명합니다.
ms.openlocfilehash: 9fa8c4a21486aaef87e1c0a3097e5983a378d98d
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92656199"
---
# <a name="configure-a-virtual-machines-at-initial-boot-up-by-using-dsc"></a><span data-ttu-id="979de-104">초기 부팅 시 DSC를 사용하여 가상 컴퓨터 구성</span><span class="sxs-lookup"><span data-stu-id="979de-104">Configure a virtual machines at initial boot-up by using DSC</span></span>

> [!IMPORTANT]
> <span data-ttu-id="979de-105">적용 대상: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="979de-105">Applies To: Windows PowerShell 5.0</span></span>

## <a name="requirements"></a><span data-ttu-id="979de-106">요구 사항</span><span class="sxs-lookup"><span data-stu-id="979de-106">Requirements</span></span>

> [!NOTE]
> <span data-ttu-id="979de-107">PowerShell 4.0에서는 이 항목에서 설명하는 **DSCAutomationHostEnabled** 레지스트리 키를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="979de-107">The **DSCAutomationHostEnabled** registry key described in this topic is not available in PowerShell 4.0.</span></span> <span data-ttu-id="979de-108">PowerShell 4.0에서 초기 부팅 시 새 가상 컴퓨터를 구성하는 방법에 대한 자세한 내용은 [Want to Automatically Configure Your Machines Using DSC at Initial Boot-up?](https://blogs.msdn.microsoft.com/powershell/2014/02/28/want-to-automatically-configure-your-machines-using-dsc-at-initial-boot-up/)(초기 부팅 시 DSC를 사용하여 컴퓨터를 자동으로 구성하고 싶나요?)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="979de-108">For information on how to configure new virtual machines at initial boot-up in PowerShell 4.0, see [Want to Automatically Configure Your Machines Using DSC at Initial Boot-up?](https://blogs.msdn.microsoft.com/powershell/2014/02/28/want-to-automatically-configure-your-machines-using-dsc-at-initial-boot-up/)</span></span>

<span data-ttu-id="979de-109">이러한 예제를 실행하려면 다음이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="979de-109">To run these examples, you will need:</span></span>

- <span data-ttu-id="979de-110">작업할 부팅 가능한 VHD.</span><span class="sxs-lookup"><span data-stu-id="979de-110">A bootable VHD to work with.</span></span> <span data-ttu-id="979de-111">[TechNet Evaluation Center](https://www.microsoft.com/evalcenter/evaluate-windows-server-2016)에서 Windows Server 2016 평가판이 포함된 ISO를 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="979de-111">You can download an ISO with an evaluation copy of Windows Server 2016 at [TechNet Evaluation Center](https://www.microsoft.com/evalcenter/evaluate-windows-server-2016).</span></span>
  <span data-ttu-id="979de-112">ISO 이미지에서 VHD를 만드는 방법에 지침은 [Creating Bootable Virtual Hard Disks](/previous-versions/windows/it-pro/windows-7/gg318049(v=ws.10))(부팅 가능한 가상 하드 디스크 만들기)에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="979de-112">You can find instructions on how to create a VHD from an ISO image at [Creating Bootable Virtual Hard Disks](/previous-versions/windows/it-pro/windows-7/gg318049(v=ws.10)).</span></span>
- <span data-ttu-id="979de-113">Hyper-V 사용하도록 설정한 호스트 컴퓨터.</span><span class="sxs-lookup"><span data-stu-id="979de-113">A host computer that has Hyper-V enabled.</span></span> <span data-ttu-id="979de-114">자세한 내용은 [Hyper-V 개요](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831531(v=ws.11))를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="979de-114">For information, see [Hyper-V overview](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831531(v=ws.11)).</span></span>

  <span data-ttu-id="979de-115">DSC를 사용하면 초기 부팅 시 컴퓨터에서 소프트웨어 설치 및 구성을 자동화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="979de-115">By using DSC, you can automate software installation and configuration for a computer at initial boot-up.</span></span> <span data-ttu-id="979de-116">이렇게 하려면 구성 MOF 문서 또는 메타 구성을 부팅 가능한 미디어(예: VHD)에 삽입하여 초기 부팅 과정 중 실행되게 합니다.</span><span class="sxs-lookup"><span data-stu-id="979de-116">You do this by either injecting a configuration MOF document or a metaconfiguration into bootable media (such as a VHD) so that they are run during the initial boot-up process.</span></span> <span data-ttu-id="979de-117">이 동작은 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System` 아래에 [DSCAutomationHostEnabled 레지스트리 키](DSCAutomationHostEnabled.md) 레지스트리 키로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="979de-117">This behavior is specified by the [DSCAutomationHostEnabled registry key](DSCAutomationHostEnabled.md) registry key under `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System`.</span></span>
  <span data-ttu-id="979de-118">기본적으로 이 키의 값은 2이며, 이 경우 DSC가 부팅 시 실행될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="979de-118">By default, the value of this key is 2, which allows DSC to run at boot time.</span></span>

  <span data-ttu-id="979de-119">부팅 시 DSC가 실행되지 않게 하려면 [DSCAutomationHostEnabled 레지스트리 키](DSCAutomationHostEnabled.md) 레지스트리 키 값을 0으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="979de-119">If you do not want DSC to run at boot time, set the value of the [DSCAutomationHostEnabled registry key](DSCAutomationHostEnabled.md) registry key to 0.</span></span>

- <span data-ttu-id="979de-120">구성 MOF 문서를 VHD에 삽입</span><span class="sxs-lookup"><span data-stu-id="979de-120">Inject a configuration MOF document into a VHD</span></span>
- <span data-ttu-id="979de-121">DSC 메타 구성을 VHD에 삽입</span><span class="sxs-lookup"><span data-stu-id="979de-121">Inject a DSC metaconfiguration into a VHD</span></span>
- <span data-ttu-id="979de-122">부팅 시 DSC를 사용하지 않도록 설정</span><span class="sxs-lookup"><span data-stu-id="979de-122">Disable DSC at boot time</span></span>

> [!NOTE]
> <span data-ttu-id="979de-123">`Pending.mof` 및 `MetaConfig.mof` 모두를 컴퓨터에 동시에 삽입할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="979de-123">You can inject both `Pending.mof` and `MetaConfig.mof` into a computer at the same time.</span></span>
> <span data-ttu-id="979de-124">두 파일 모두 있는 경우 `MetaConfig.mof`에 지정된 설정이 우선합니다.</span><span class="sxs-lookup"><span data-stu-id="979de-124">If both files are present, the settings specified in `MetaConfig.mof` take precedence.</span></span>

## <a name="inject-a-configuration-mof-document-into-a-vhd"></a><span data-ttu-id="979de-125">구성 MOF 문서를 VHD에 삽입</span><span class="sxs-lookup"><span data-stu-id="979de-125">Inject a configuration MOF document into a VHD</span></span>

<span data-ttu-id="979de-126">초기 부팅 시 구성을 시행하려면 컴파일된 구성 MOF 문서를 VHD에 `Pending.mof` 파일로 삽입할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="979de-126">To enact a configuration at initial boot-up, you can inject a compiled configuration MOF document into the VHD as its `Pending.mof` file.</span></span> <span data-ttu-id="979de-127">**DSCAutomationHostEnabled** 레지스트리 키가 2(기본값)로 설정된 경우 컴퓨터가 처음으로 부팅할 때 DSC에서 `Pending.mof`에 정의된 구성을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="979de-127">If the **DSCAutomationHostEnabled** registry key is set to 2 (the default value), DSC will apply the configuration defined by `Pending.mof` when the computer boots up for the first time.</span></span>

<span data-ttu-id="979de-128">이 예제에서는 새 컴퓨터에 IIS를 설치하는 다음 구성을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="979de-128">For this example, we will use the following configuration, which will install IIS on the new computer:</span></span>

```powershell
Configuration SampleIISInstall
{
    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

    node ('localhost')
    {
        WindowsFeature IIS
        {
            Ensure = 'Present'
            Name   = 'Web-Server'
        }
    }
}
```

### <a name="to-inject-the-configuration-mof-document-on-the-vhd"></a><span data-ttu-id="979de-129">구성 MOF 문서를 VHD에 삽입하려면</span><span class="sxs-lookup"><span data-stu-id="979de-129">To inject the configuration MOF document on the VHD</span></span>

1. <span data-ttu-id="979de-130">구성을 삽입할 VHD를 [Mount-VHD](/powershell/module/hyper-v/mount-vhd) cmdlet을 호출하여 탑재합니다.</span><span class="sxs-lookup"><span data-stu-id="979de-130">Mount the VHD into which you want to inject the configuration by calling the [Mount-VHD](/powershell/module/hyper-v/mount-vhd) cmdlet.</span></span> <span data-ttu-id="979de-131">예를 들어:</span><span class="sxs-lookup"><span data-stu-id="979de-131">For example:</span></span>

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

1. <span data-ttu-id="979de-132">PowerShell 5.0 이상을 실행하는 컴퓨터에서 위의 구성( **SampleIISInstall** )을 PowerShell 스크립트(.ps1) 파일로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="979de-132">On a computer running PowerShell 5.0 or later, save the above configuration ( **SampleIISInstall** ) as a PowerShell script (.ps1) file.</span></span>

1. <span data-ttu-id="979de-133">PowerShell 콘솔에서 .ps1 파일을 저장한 폴더로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="979de-133">In a PowerShell console, navigate to the folder where you saved the .ps1 file.</span></span>

1. <span data-ttu-id="979de-134">다음 PowerShell 명령을 실행하여 MOF 문서를 컴파일합니다(DSC 구성 컴파일에 대한 자세한 내용은 [DSC 구성](../configurations/configurations.md) 참조).</span><span class="sxs-lookup"><span data-stu-id="979de-134">Run the following PowerShell commands to compile the MOF document (for information about compiling DSC configurations, see [DSC Configurations](../configurations/configurations.md):</span></span>

   ```powershell
   . .\SampleIISInstall.ps1
   SampleIISInstall
   ```

1. <span data-ttu-id="979de-135">그러면 `localhost.mof` 파일이 `SampleIISInstall`이라는 폴더에 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="979de-135">This will create a `localhost.mof` file in a new folder named `SampleIISInstall`.</span></span> <span data-ttu-id="979de-136">이 파일을 `Pending.mof`로 이름을 바꾸고 [Move-item](/powershell/module/microsoft.powershell.management/move-item) cmdlet을 사용하여 VHD에서 적절한 위치로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="979de-136">Rename and move that file into the proper location on the VHD as `Pending.mof` by using the [Move-Item](/powershell/module/microsoft.powershell.management/move-item) cmdlet.</span></span> <span data-ttu-id="979de-137">예를 들어:</span><span class="sxs-lookup"><span data-stu-id="979de-137">For example:</span></span>

   ```powershell
   Move-Item -Path C:\DSCTest\SampleIISInstall\localhost.mof -Destination E:\Windows\System32\Configuration\Pending.mof
   ```

1. <span data-ttu-id="979de-138">[Dismount-VHD](/powershell/module/hyper-v/dismount-vhd) cmdlet을 호출하여 VHD를 분리합니다.</span><span class="sxs-lookup"><span data-stu-id="979de-138">Dismount the VHD by calling the [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd) cmdlet.</span></span>
   <span data-ttu-id="979de-139">예를 들어:</span><span class="sxs-lookup"><span data-stu-id="979de-139">For example:</span></span>

   ```powershell
   Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

1. <span data-ttu-id="979de-140">DSC MOF 문서를 설치한 VHD를 사용하여 VM을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="979de-140">Create a VM by using the VHD where you installed the DSC MOF document.</span></span>

<span data-ttu-id="979de-141">초기 부팅 및 운영 체제 설치 후에 IIS가 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="979de-141">After initial boot-up and operating system installation, IIS will be installed.</span></span> <span data-ttu-id="979de-142">이 작업은 [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature) cmdlet을 호출하여 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="979de-142">You can verify this by calling the [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature) cmdlet.</span></span>

## <a name="inject-a-dsc-metaconfiguration-into-a-vhd"></a><span data-ttu-id="979de-143">DSC 메타 구성을 VHD에 삽입</span><span class="sxs-lookup"><span data-stu-id="979de-143">Inject a DSC metaconfiguration into a VHD</span></span>

<span data-ttu-id="979de-144">또한 메타 구성([LCM(로컬 구성 관리자) 구성](../managing-nodes/metaConfig.md) 참조)을 VHD에 `MetaConfig.mof` 파일로 삽입하여 초기 부팅 시 구성을 가져오도록 컴퓨터를 구성할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="979de-144">You can also configure a computer to pull a configuration at initial boot-up by injecting a metaconfiguration (see [Configuring the Local Configuration Manager (LCM)](../managing-nodes/metaConfig.md)) into the VHD as its `MetaConfig.mof` file.</span></span> <span data-ttu-id="979de-145">**DSCAutomationHostEnabled** 레지스트리 키가 2(기본값)로 설정된 경우 DSC는 컴퓨터가 처음 부팅될 때 `MetaConfig.mof`에 정의된 구성을 LCM에 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="979de-145">If the **DSCAutomationHostEnabled** registry key is set to 2 (the default value), DSC will apply the metaconfiguration defined by `MetaConfig.mof` to the LCM when the computer boots up for the first time.</span></span> <span data-ttu-id="979de-146">메타 구성에서 LCM이 끌어오기 서버로부터 구성을 가져오도록 지정하는 경우 컴퓨터에서는 초기 부팅 시 해당 끌어오기 서버로부터 구성을 가져오려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="979de-146">If the metaconfiguration specifies that the LCM should pull configurations from a pull server, the computer will attempt to pull a configuration from that pull server at initial boot-up.</span></span> <span data-ttu-id="979de-147">DSC 끌어오기 서버 설정에 대한 자세한 내용은 [DSC 웹 끌어오기 서버 설정](../pull-server/pullServer.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="979de-147">For information about setting up a DSC pull server, see [Setting up a DSC web pull server](../pull-server/pullServer.md).</span></span>

<span data-ttu-id="979de-148">이 예제에서는 이전 섹션에 설명된 구성( **SampleIISInstall** ) 및 다음 메타 구성을 모두 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="979de-148">For this example, we will use both the configuration described in the previous section ( **SampleIISInstall** ), and the following metaconfiguration:</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientBootstrap
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
            ConfigurationNames = @('SampleIISInstall')
        }
    }
}
```

### <a name="to-inject-the-metaconfiguration-mof-document-on-the-vhd"></a><span data-ttu-id="979de-149">메타 구성 MOF 문서를 VHD에 삽입하려면</span><span class="sxs-lookup"><span data-stu-id="979de-149">To inject the metaconfiguration MOF document on the VHD</span></span>

1. <span data-ttu-id="979de-150">메타 구성을 삽입할 VHD를 [Mount-VHD](/powershell/module/hyper-v/mount-vhd) cmdlet을 호출하여 탑재합니다.</span><span class="sxs-lookup"><span data-stu-id="979de-150">Mount the VHD into which you want to inject the metaconfiguration by calling the [Mount-VHD](/powershell/module/hyper-v/mount-vhd) cmdlet.</span></span> <span data-ttu-id="979de-151">예를 들어:</span><span class="sxs-lookup"><span data-stu-id="979de-151">For example:</span></span>

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

1. <span data-ttu-id="979de-152">[웹 DSC 끌어오기 서버를 설정](../pull-server/pullServer.md)하고, **SampleIISInstall** 구성을 적절한 폴더에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="979de-152">[Set up a DSC web pull server](../pull-server/pullServer.md), and save the **SampleIISInstall** configuration to the appropriate folder.</span></span>

1. <span data-ttu-id="979de-153">PowerShell 5.0 이상을 실행하는 컴퓨터에서 위의 메타 구성( **PullClientBootstrap** )을 PowerShell 스크립트(.ps1) 파일로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="979de-153">On a computer running PowerShell 5.0 or later, save the above metaconfiguration ( **PullClientBootstrap** ) as a PowerShell script (.ps1) file.</span></span>

1. <span data-ttu-id="979de-154">PowerShell 콘솔에서 .ps1 파일을 저장한 폴더로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="979de-154">In a PowerShell console, navigate to the folder where you saved the .ps1 file.</span></span>

1. <span data-ttu-id="979de-155">다음 PowerShell 명령을 실행하여 메타 구성 MOF 문서를 컴파일합니다(DSC 구성 컴파일에 대한 자세한 내용은 [DSC 구성](../configurations/configurations.md) 참조).</span><span class="sxs-lookup"><span data-stu-id="979de-155">Run the following PowerShell commands to compile the metaconfiguration MOF document (for information about compiling DSC configurations, see [DSC Configurations](../configurations/configurations.md):</span></span>

   ```powershell
   . .\PullClientBootstrap.ps1
   PullClientBootstrap
   ```

1. <span data-ttu-id="979de-156">그러면 `localhost.meta.mof` 파일이 `PullClientBootstrap`이라는 폴더에 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="979de-156">This will create a `localhost.meta.mof` file in a new folder named `PullClientBootstrap`.</span></span> <span data-ttu-id="979de-157">이 파일을 `MetaConfig.mof`로 이름을 바꾸고 [Move-item](/powershell/module/microsoft.powershell.management/move-item) cmdlet을 사용하여 VHD에서 적절한 위치로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="979de-157">Rename and move that file into the proper location on the VHD as `MetaConfig.mof` by using the [Move-Item](/powershell/module/microsoft.powershell.management/move-item) cmdlet.</span></span>

   ```powershell
   Move-Item -Path C:\DSCTest\PullClientBootstrap\localhost.meta.mof -Destination E:\Windows\System32\Configuration\MetaConfig.mof
   ```

1. <span data-ttu-id="979de-158">[Dismount-VHD](/powershell/module/hyper-v/dismount-vhd) cmdlet을 호출하여 VHD를 분리합니다.</span><span class="sxs-lookup"><span data-stu-id="979de-158">Dismount the VHD by calling the [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd) cmdlet.</span></span>
   <span data-ttu-id="979de-159">예를 들어:</span><span class="sxs-lookup"><span data-stu-id="979de-159">For example:</span></span>

   ```powershell
   Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

1. <span data-ttu-id="979de-160">DSC MOF 문서를 설치한 VHD를 사용하여 VM을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="979de-160">Create a VM by using the VHD where you installed the DSC MOF document.</span></span>

<span data-ttu-id="979de-161">초기 부팅 및 운영 체제 설치 후에 DSC가 끌어오기 서버로부터 구성을 가져오면 IIS가 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="979de-161">After initial boot-up and operating system installation, DSC will pull the configuration from the pull server, and IIS will be installed.</span></span> <span data-ttu-id="979de-162">이 작업은 [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature) cmdlet을 호출하여 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="979de-162">You can verify this by calling the [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature) cmdlet.</span></span>

## <a name="disable-dsc-at-boot-time"></a><span data-ttu-id="979de-163">부팅 시 DSC를 사용하지 않도록 설정</span><span class="sxs-lookup"><span data-stu-id="979de-163">Disable DSC at boot time</span></span>

<span data-ttu-id="979de-164">기본적으로 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System\DSCAutomationHostEnabled`</span><span class="sxs-lookup"><span data-stu-id="979de-164">By default, the value of the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System\DSCAutomationHostEnabled`</span></span>
<span data-ttu-id="979de-165">키 값은 2로 설정되며, 이 경우 컴퓨터가 보류 중이거나 현재 상태이면 DSC 구성을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="979de-165">key is set to 2, which allows a DSC configuration to run if the computer is in pending or current state.</span></span> <span data-ttu-id="979de-166">초기 부팅 시 구성이 실행되지 않게 하려면 이 키 값을 0으로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="979de-166">If you do not want a configuration to run at initial boot-up, you need so set the value of this key to 0:</span></span>

1. <span data-ttu-id="979de-167">[Mount-VHD](/powershell/module/hyper-v/mount-vhd) cmdlet을 호출하여 VHD를 탑재합니다.</span><span class="sxs-lookup"><span data-stu-id="979de-167">Mount the VHD by calling the [Mount-VHD](/powershell/module/hyper-v/mount-vhd) cmdlet.</span></span> <span data-ttu-id="979de-168">예를 들어:</span><span class="sxs-lookup"><span data-stu-id="979de-168">For example:</span></span>

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

1. <span data-ttu-id="979de-169">`reg load`를 호출하여 VHD에서 레지스트리 `HKLM\Software` 하위 키를 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="979de-169">Load the registry `HKLM\Software` subkey from the VHD by calling `reg load`.</span></span>

   ```powershell
   reg load HKLM\Vhd E:\Windows\System32\Config\Software`
   ```

1. <span data-ttu-id="979de-170">PowerShell 레지스트리 공급자를 사용하여 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System`으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="979de-170">Navigate to the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System` by using the PowerShell Registry provider.</span></span>

   ```powershell
   Set-Location HKLM:\Software\Microsoft\Windows\CurrentVersion\Policies\System`
   ```

1. <span data-ttu-id="979de-171">`DSCAutomationHostEnabled` 값을 0으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="979de-171">Change the value of `DSCAutomationHostEnabled` to 0.</span></span>

   ```powershell
   Set-ItemProperty -Path . -Name DSCAutomationHostEnabled -Value 0
   ```

5. <span data-ttu-id="979de-172">다음 명령을 실행하여 레지스트리를 언로드합니다.</span><span class="sxs-lookup"><span data-stu-id="979de-172">Unload the registry by running the following commands:</span></span>

   ```powershell
   [gc]::Collect()
   reg unload HKLM\Vhd
   ```

## <a name="see-also"></a><span data-ttu-id="979de-173">참고 항목</span><span class="sxs-lookup"><span data-stu-id="979de-173">See Also</span></span>

[<span data-ttu-id="979de-174">DSC 구성</span><span class="sxs-lookup"><span data-stu-id="979de-174">DSC Configurations</span></span>](../configurations/configurations.md)

[<span data-ttu-id="979de-175">DSCAutomationHostEnabled 레지스트리 키</span><span class="sxs-lookup"><span data-stu-id="979de-175">DSCAutomationHostEnabled registry key</span></span>](DSCAutomationHostEnabled.md)

[<span data-ttu-id="979de-176">LCM(로컬 구성 관리자) 구성</span><span class="sxs-lookup"><span data-stu-id="979de-176">Configuring the Local Configuration Manager (LCM)</span></span>](../managing-nodes/metaConfig.md)

[<span data-ttu-id="979de-177">DSC 웹 끌어오기 서버 설정</span><span class="sxs-lookup"><span data-stu-id="979de-177">Setting up a DSC web pull server</span></span>](../pull-server/pullServer.md)
