---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: 초기 부팅 시 DSC를 사용하여 가상 컴퓨터 구성
ms.openlocfilehash: 2ae6f7a85af3d08bad9e97b90efaefb2ff8410ca
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55681613"
---
# <a name="configure-a-virtual-machines-at-initial-boot-up-by-using-dsc"></a><span data-ttu-id="ebcdd-103">초기 부팅 시 DSC를 사용하여 가상 컴퓨터 구성</span><span class="sxs-lookup"><span data-stu-id="ebcdd-103">Configure a virtual machines at initial boot-up by using DSC</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ebcdd-104">적용 대상: Windows Powershell 5.0</span><span class="sxs-lookup"><span data-stu-id="ebcdd-104">Applies To: Windows PowerShell 5.0</span></span>

## <a name="requirements"></a><span data-ttu-id="ebcdd-105">요구 사항</span><span class="sxs-lookup"><span data-stu-id="ebcdd-105">Requirements</span></span>

> [!NOTE]
> <span data-ttu-id="ebcdd-106">PowerShell 4.0에서는 이 항목에서 설명하는 **DSCAutomationHostEnabled** 레지스트리 키를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ebcdd-106">The **DSCAutomationHostEnabled** registry key described in this topic is not available in PowerShell 4.0.</span></span>
> <span data-ttu-id="ebcdd-107">PowerShell 4.0에서 초기 부팅 시 새 가상 컴퓨터를 구성하는 방법에 대한 자세한 내용은 [Want to Automatically Configure Your Machines Using DSC at Initial Boot-up?](https://blogs.msdn.microsoft.com/powershell/2014/02/28/want-to-automatically-configure-your-machines-using-dsc-at-initial-boot-up/)(초기 부팅 시 DSC를 사용하여 컴퓨터를 자동으로 구성하고 싶나요?)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ebcdd-107">For information on how to configure new virtual machines at initial boot-up in PowerShell 4.0, see [Want to Automatically Configure Your Machines Using DSC at Initial Boot-up?](https://blogs.msdn.microsoft.com/powershell/2014/02/28/want-to-automatically-configure-your-machines-using-dsc-at-initial-boot-up/)</span></span>

<span data-ttu-id="ebcdd-108">이러한 예제를 실행하려면 다음이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="ebcdd-108">To run these examples, you will need:</span></span>

- <span data-ttu-id="ebcdd-109">작업할 부팅 가능한 VHD.</span><span class="sxs-lookup"><span data-stu-id="ebcdd-109">A bootable VHD to work with.</span></span> <span data-ttu-id="ebcdd-110">[TechNet Evaluation Center](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016)에서 Windows Server 2016 평가판이 포함된 ISO를 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebcdd-110">You can download an ISO with an evaluation copy of Windows Server 2016 at [TechNet Evaluation Center](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span></span>
  <span data-ttu-id="ebcdd-111">ISO 이미지에서 VHD를 만드는 방법에 지침은 [Creating Bootable Virtual Hard Disks](/previous-versions/windows/it-pro/windows-7/gg318049(v=ws.10))(부팅 가능한 가상 하드 디스크 만들기)에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebcdd-111">You can find instructions on how to create a VHD from an ISO image at [Creating Bootable Virtual Hard Disks](/previous-versions/windows/it-pro/windows-7/gg318049(v=ws.10)).</span></span>
- <span data-ttu-id="ebcdd-112">Hyper-V 사용하도록 설정한 호스트 컴퓨터.</span><span class="sxs-lookup"><span data-stu-id="ebcdd-112">A host computer that has Hyper-V enabled.</span></span> <span data-ttu-id="ebcdd-113">자세한 내용은 [Hyper-V 개요](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831531(v=ws.11))를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ebcdd-113">For information, see [Hyper-V overview](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831531(v=ws.11)).</span></span>

  <span data-ttu-id="ebcdd-114">DSC를 사용하면 초기 부팅 시 컴퓨터에서 소프트웨어 설치 및 구성을 자동화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebcdd-114">By using DSC, you can automate software installation and configuration for a computer at initial boot-up.</span></span>
  <span data-ttu-id="ebcdd-115">이렇게 하려면 구성 MOF 문서 또는 메타 구성을 부팅 가능한 미디어(예: VHD)에 삽입하여 초기 부팅 과정 중 실행되게 합니다.</span><span class="sxs-lookup"><span data-stu-id="ebcdd-115">You do this by either injecting a configuration MOF document or a metaconfiguration into bootable media (such as a VHD) so that they are run during the initial boot-up process.</span></span>
  <span data-ttu-id="ebcdd-116">이 동작은 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System` 아래에 [DSCAutomationHostEnabled 레지스트리 키](DSCAutomationHostEnabled.md) 레지스트리 키로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ebcdd-116">This behavior is specified by the [DSCAutomationHostEnabled registry key](DSCAutomationHostEnabled.md) registry key under `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System`.</span></span>
  <span data-ttu-id="ebcdd-117">기본적으로 이 키의 값은 2이며, 이 경우 DSC가 부팅 시 실행될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebcdd-117">By default, the value of this key is 2, which allows DSC to run at boot time.</span></span>

  <span data-ttu-id="ebcdd-118">부팅 시 DSC가 실행되지 않게 하려면 [DSCAutomationHostEnabled 레지스트리 키](DSCAutomationHostEnabled.md) 레지스트리 키 값을 0으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ebcdd-118">If you do not want DSC to run at boot time, set the value of the [DSCAutomationHostEnabled registry key](DSCAutomationHostEnabled.md) registry key to 0.</span></span>

- <span data-ttu-id="ebcdd-119">구성 MOF 문서를 VHD에 삽입</span><span class="sxs-lookup"><span data-stu-id="ebcdd-119">Inject a configuration MOF document into a VHD</span></span>
- <span data-ttu-id="ebcdd-120">DSC 메타 구성을 VHD에 삽입</span><span class="sxs-lookup"><span data-stu-id="ebcdd-120">Inject a DSC metaconfiguration into a VHD</span></span>
- <span data-ttu-id="ebcdd-121">부팅 시 DSC를 사용하지 않도록 설정</span><span class="sxs-lookup"><span data-stu-id="ebcdd-121">Disable DSC at boot time</span></span>

> [!NOTE]
> <span data-ttu-id="ebcdd-122">`Pending.mof` 및 `MetaConfig.mof` 모두를 컴퓨터에 동시에 삽입할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebcdd-122">You can inject both `Pending.mof` and `MetaConfig.mof` into a computer at the same time.</span></span>
> <span data-ttu-id="ebcdd-123">두 파일 모두 있는 경우 `MetaConfig.mof`에 지정된 설정이 우선합니다.</span><span class="sxs-lookup"><span data-stu-id="ebcdd-123">If both files are present, the settings specified in `MetaConfig.mof` take precedence.</span></span>

## <a name="inject-a-configuration-mof-document-into-a-vhd"></a><span data-ttu-id="ebcdd-124">구성 MOF 문서를 VHD에 삽입</span><span class="sxs-lookup"><span data-stu-id="ebcdd-124">Inject a configuration MOF document into a VHD</span></span>

<span data-ttu-id="ebcdd-125">초기 부팅 시 구성을 시행하려면 컴파일된 구성 MOF 문서를 VHD에 `Pending.mof` 파일로 삽입할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebcdd-125">To enact a configuration at initial boot-up, you can inject a compiled configuration MOF document into the VHD as its `Pending.mof` file.</span></span>
<span data-ttu-id="ebcdd-126">**DSCAutomationHostEnabled** 레지스트리 키가 2(기본값)로 설정된 경우 컴퓨터가 처음으로 부팅할 때 DSC에서 `Pending.mof`에 정의된 구성을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="ebcdd-126">If the **DSCAutomationHostEnabled** registry key is set to 2 (the default value), DSC will apply the configuration defined by `Pending.mof` when the computer boots up for the first time.</span></span>

<span data-ttu-id="ebcdd-127">이 예제에서는 새 컴퓨터에 IIS를 설치하는 다음 구성을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ebcdd-127">For this example, we will use the following configuration, which will install IIS on the new computer:</span></span>

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

### <a name="to-inject-the-configuration-mof-document-on-the-vhd"></a><span data-ttu-id="ebcdd-128">구성 MOF 문서를 VHD에 삽입하려면</span><span class="sxs-lookup"><span data-stu-id="ebcdd-128">To inject the configuration MOF document on the VHD</span></span>

1. <span data-ttu-id="ebcdd-129">구성을 삽입할 VHD를 [Mount-VHD](/powershell/module/hyper-v/mount-vhd) cmdlet을 호출하여 탑재합니다.</span><span class="sxs-lookup"><span data-stu-id="ebcdd-129">Mount the VHD into which you want to inject the configuration by calling the [Mount-VHD](/powershell/module/hyper-v/mount-vhd) cmdlet.</span></span> <span data-ttu-id="ebcdd-130">예:</span><span class="sxs-lookup"><span data-stu-id="ebcdd-130">For example:</span></span>

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

2. <span data-ttu-id="ebcdd-131">PowerShell 5.0 이상을 실행하는 컴퓨터에서 위의 구성(**SampleIISInstall**)을 PowerShell 스크립트(.ps1) 파일로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="ebcdd-131">On a computer running PowerShell 5.0 or later, save the above configuration (**SampleIISInstall**) as a PowerShell script (.ps1) file.</span></span>

3. <span data-ttu-id="ebcdd-132">PowerShell 콘솔에서 .ps1 파일을 저장한 폴더로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="ebcdd-132">In a PowerShell console, navigate to the folder where you saved the .ps1 file.</span></span>

4. <span data-ttu-id="ebcdd-133">다음 PowerShell 명령을 실행하여 MOF 문서를 컴파일합니다(DSC 구성 컴파일에 대한 자세한 내용은 [DSC 구성](../configurations/configurations.md) 참조).</span><span class="sxs-lookup"><span data-stu-id="ebcdd-133">Run the following PowerShell commands to compile the MOF document (for information about compiling DSC configurations, see [DSC Configurations](../configurations/configurations.md):</span></span>

   ```powershell
   . .\SampleIISInstall.ps1
   SampleIISInstall
   ```

5. <span data-ttu-id="ebcdd-134">그러면 `localhost.mof` 파일이 `SampleIISInstall`이라는 폴더에 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="ebcdd-134">This will create a `localhost.mof` file in a new folder named `SampleIISInstall`.</span></span>
   <span data-ttu-id="ebcdd-135">이 파일을 `Pending.mof`로 이름을 바꾸고 [Move-item](/powershell/module/microsoft.powershell.management/move-item) cmdlet을 사용하여 VHD에서 적절한 위치로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="ebcdd-135">Rename and move that file into the proper location on the VHD as `Pending.mof` by using the [Move-Item](/powershell/module/microsoft.powershell.management/move-item) cmdlet.</span></span> <span data-ttu-id="ebcdd-136">예:</span><span class="sxs-lookup"><span data-stu-id="ebcdd-136">For example:</span></span>

   ```powershell
       Move-Item -Path C:\DSCTest\SampleIISInstall\localhost.mof -Destination E:\Windows\System32\Configuration\Pending.mof
   ```

6. <span data-ttu-id="ebcdd-137">[Dismount-VHD](/powershell/module/hyper-v/dismount-vhd) cmdlet을 호출하여 VHD를 분리합니다.</span><span class="sxs-lookup"><span data-stu-id="ebcdd-137">Dismount the VHD by calling the [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd) cmdlet.</span></span> <span data-ttu-id="ebcdd-138">예:</span><span class="sxs-lookup"><span data-stu-id="ebcdd-138">For example:</span></span>

   ```powershell
   Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

7. <span data-ttu-id="ebcdd-139">DSC MOF 문서를 설치한 VHD를 사용하여 VM을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ebcdd-139">Create a VM by using the VHD where you installed the DSC MOF document.</span></span>

<span data-ttu-id="ebcdd-140">초기 부팅 및 운영 체제 설치 후 IIS가 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="ebcdd-140">After intial boot-up and operating system installation, IIS will be installed.</span></span>
<span data-ttu-id="ebcdd-141">이 작업은 [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature) cmdlet을 호출하여 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebcdd-141">You can verify this by calling the [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature) cmdlet.</span></span>

## <a name="inject-a-dsc-metaconfiguration-into-a-vhd"></a><span data-ttu-id="ebcdd-142">DSC 메타 구성을 VHD에 삽입</span><span class="sxs-lookup"><span data-stu-id="ebcdd-142">Inject a DSC metaconfiguration into a VHD</span></span>

<span data-ttu-id="ebcdd-143">또한 메타 구성([LCM(로컬 구성 관리자) 구성](../managing-nodes/metaConfig.md) 참조)을 VHD에 `MetaConfig.mof` 파일로 삽입하여 초기 부팅 시 구성을 가져오도록 컴퓨터를 구성할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebcdd-143">You can also configure a computer to pull a configuration at intial boot-up by injecting a metaconfiguration (see [Configuring the Local Configuration Manager (LCM)](../managing-nodes/metaConfig.md)) into the VHD as its `MetaConfig.mof` file.</span></span>
<span data-ttu-id="ebcdd-144">**DSCAutomationHostEnabled** 레지스트리 키가 2(기본값)로 설정된 경우 컴퓨터가 처음으로 부팅할 때 DSC에서 `MetaConfig.mof`에 정의된 구성을 LCM에 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="ebcdd-144">If the **DSCAutomationHostEnabled** registry key is set to 2 (the default value),  DSC will apply the metaconfiguration defined by `MetaConfig.mof` to the LCM when the computer boots up for the first time.</span></span>
<span data-ttu-id="ebcdd-145">메타 구성에서 LCM이 끌어오기 서버에서 구성을 가져오도록 지정하는 경우 컴퓨터에서는 초기 부팅 시 해당 끌어오기 서버에서 구성을 가져오려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="ebcdd-145">If the metaconfiguration specifies that the LCM should pull configurations from a pull server, the computer will attempt to pull a configuration from that pull server at inital boot-up.</span></span>
<span data-ttu-id="ebcdd-146">DSC 끌어오기 서버 설정에 대한 자세한 내용은 [DSC 웹 끌어오기 서버 설정](../pull-server/pullServer.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ebcdd-146">For information about setting up a DSC pull server, see [Setting up a DSC web pull server](../pull-server/pullServer.md).</span></span>

<span data-ttu-id="ebcdd-147">이 예제에서는 이전 섹션에 설명된 구성(**SampleIISInstall**) 및 다음 메타 구성을 모두 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ebcdd-147">For this example, we will use both the configuration described in the previous section (**SampleIISInstall**), and the following metaconfiguration:</span></span>

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

### <a name="to-inject-the-metaconfiguration-mof-document-on-the-vhd"></a><span data-ttu-id="ebcdd-148">메타 구성 MOF 문서를 VHD에 삽입하려면</span><span class="sxs-lookup"><span data-stu-id="ebcdd-148">To inject the metaconfiguration MOF document on the VHD</span></span>

1. <span data-ttu-id="ebcdd-149">메타 구성을 삽입할 VHD를 [Mount-VHD](/powershell/module/hyper-v/mount-vhd) cmdlet을 호출하여 탑재합니다.</span><span class="sxs-lookup"><span data-stu-id="ebcdd-149">Mount the VHD into which you want to inject the metaconfiguration by calling the [Mount-VHD](/powershell/module/hyper-v/mount-vhd) cmdlet.</span></span> <span data-ttu-id="ebcdd-150">예:</span><span class="sxs-lookup"><span data-stu-id="ebcdd-150">For example:</span></span>

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

2. <span data-ttu-id="ebcdd-151">[웹 DSC 끌어오기 서버를 설정](../pull-server/pullServer.md)하고 **SampleIISInistall** 구성을 적절한 폴더에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="ebcdd-151">[Set up a DSC web pull server](../pull-server/pullServer.md), and save the **SampleIISInistall** configuration to the appropriate folder.</span></span>

3. <span data-ttu-id="ebcdd-152">PowerShell 5.0 이상을 실행하는 컴퓨터에서 위의 메타 구성(**PullClientBootstrap**)을 PowerShell 스크립트(.ps1) 파일로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="ebcdd-152">On a computer running PowerShell 5.0 or later, save the above metaconfiguration (**PullClientBootstrap**) as a PowerShell script (.ps1) file.</span></span>

4. <span data-ttu-id="ebcdd-153">PowerShell 콘솔에서 .ps1 파일을 저장한 폴더로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="ebcdd-153">In a PowerShell console, navigate to the folder where you saved the .ps1 file.</span></span>

5. <span data-ttu-id="ebcdd-154">다음 PowerShell 명령을 실행하여 메타 구성 MOF 문서를 컴파일합니다(DSC 구성 컴파일에 대한 자세한 내용은 [DSC 구성](../configurations/configurations.md) 참조).</span><span class="sxs-lookup"><span data-stu-id="ebcdd-154">Run the following PowerShell commands to compile the  metaconfiguration MOF document (for information about compiling DSC configurations, see [DSC Configurations](../configurations/configurations.md):</span></span>

   ```powershell
   . .\PullClientBootstrap.ps1
   PullClientBootstrap
   ```

6. <span data-ttu-id="ebcdd-155">그러면 `localhost.meta.mof` 파일이 `PullClientBootstrap`이라는 폴더에 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="ebcdd-155">This will create a `localhost.meta.mof` file in a new folder named `PullClientBootstrap`.</span></span>
   <span data-ttu-id="ebcdd-156">이 파일을 `MetaConfig.mof`로 이름을 바꾸고 [Move-item](/powershell/module/microsoft.powershell.management/move-item) cmdlet을 사용하여 VHD에서 적절한 위치로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="ebcdd-156">Rename and move that file into the proper location on the VHD as `MetaConfig.mof` by using the [Move-Item](/powershell/module/microsoft.powershell.management/move-item) cmdlet.</span></span>

   ```powershell
   Move-Item -Path C:\DSCTest\PullClientBootstrap\localhost.meta.mof -Destination E:\Windows\System32\Configuration\MetaConfig.mof
   ```

7. <span data-ttu-id="ebcdd-157">[Dismount-VHD](/powershell/module/hyper-v/dismount-vhd) cmdlet을 호출하여 VHD를 분리합니다.</span><span class="sxs-lookup"><span data-stu-id="ebcdd-157">Dismount the VHD by calling the [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd) cmdlet.</span></span> <span data-ttu-id="ebcdd-158">예:</span><span class="sxs-lookup"><span data-stu-id="ebcdd-158">For example:</span></span>

   ```powershell
   Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

8. <span data-ttu-id="ebcdd-159">DSC MOF 문서를 설치한 VHD를 사용하여 VM을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ebcdd-159">Create a VM by using the VHD where you installed the DSC MOF document.</span></span>

<span data-ttu-id="ebcdd-160">초기 부팅 및 운영 체제 설치 후 DSC는 끌어오기 서버에서 구성을 가져오고 IIS가 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="ebcdd-160">After intial boot-up and operating system installation, DSC will pull the configuration from the pull server, and IIS will be installed.</span></span>
<span data-ttu-id="ebcdd-161">이 작업은 [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature) cmdlet을 호출하여 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebcdd-161">You can verify this by calling the [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature) cmdlet.</span></span>

## <a name="disable-dsc-at-boot-time"></a><span data-ttu-id="ebcdd-162">부팅 시 DSC를 사용하지 않도록 설정</span><span class="sxs-lookup"><span data-stu-id="ebcdd-162">Disable DSC at boot time</span></span>

<span data-ttu-id="ebcdd-163">기본적으로 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System\DSCAutomationHostEnabled` 키 값은 2로 설정되며, 이 경우 컴퓨터가 보류 중이거나 현재 상태이면 DSC 구성을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebcdd-163">By default, the value of the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System\DSCAutomationHostEnabled` key is set to 2, which allows a DSC configuration to run if the computer is in pending or current state.</span></span> <span data-ttu-id="ebcdd-164">초기 부팅 시 구성이 실행되지 않게 하려면 이 키 값을 0으로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ebcdd-164">If you do not want a configuration to run at initial boot-up, you need so set the value of this key to 0:</span></span>

1. <span data-ttu-id="ebcdd-165">[Mount-VHD](/powershell/module/hyper-v/mount-vhd) cmdlet을 호출하여 VHD를 탑재합니다.</span><span class="sxs-lookup"><span data-stu-id="ebcdd-165">Mount the VHD by calling the [Mount-VHD](/powershell/module/hyper-v/mount-vhd) cmdlet.</span></span> <span data-ttu-id="ebcdd-166">예:</span><span class="sxs-lookup"><span data-stu-id="ebcdd-166">For example:</span></span>

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

2. <span data-ttu-id="ebcdd-167">`reg load`를 호출하여 VHD에서 레지스트리 `HKLM\Software` 하위 키를 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="ebcdd-167">Load the registry `HKLM\Software` subkey from the VHD by calling `reg load`.</span></span>

   ```powershell
   reg load HKLM\Vhd E:\Windows\System32\Config\Software`
   ```

3. <span data-ttu-id="ebcdd-168">PowerShell 레지스트리 공급자를 사용하여 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System`으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="ebcdd-168">Navigate to the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System` by using the PowerShell Registry provider.</span></span>

   ```powershell
   Set-Location HKLM:\Software\Microsoft\Windows\CurrentVersion\Policies\System`
   ```

4. <span data-ttu-id="ebcdd-169">`DSCAutomationHostEnabled` 값을 0으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="ebcdd-169">Change the value of `DSCAutomationHostEnabled` to 0.</span></span>

   ```powershell
   Set-ItemProperty -Path . -Name DSCAutomationHostEnabled -Value 0
   ```

5. <span data-ttu-id="ebcdd-170">다음 명령을 실행하여 레지스트리를 언로드합니다.</span><span class="sxs-lookup"><span data-stu-id="ebcdd-170">Unload the registry by running the following commands:</span></span>

   ```powershell
   [gc]::Collect()
   reg unload HKLM\Vhd
   ```

## <a name="see-also"></a><span data-ttu-id="ebcdd-171">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ebcdd-171">See Also</span></span>

[<span data-ttu-id="ebcdd-172">DSC 구성</span><span class="sxs-lookup"><span data-stu-id="ebcdd-172">DSC Configurations</span></span>](../configurations/configurations.md)

[<span data-ttu-id="ebcdd-173">DSCAutomationHostEnabled 레지스트리 키</span><span class="sxs-lookup"><span data-stu-id="ebcdd-173">DSCAutomationHostEnabled registry key</span></span>](DSCAutomationHostEnabled.md)

[<span data-ttu-id="ebcdd-174">LCM(로컬 구성 관리자) 구성</span><span class="sxs-lookup"><span data-stu-id="ebcdd-174">Configuring the Local Configuration Manager (LCM)</span></span>](../managing-nodes/metaConfig.md)

[<span data-ttu-id="ebcdd-175">DSC 웹 끌어오기 서버 설정</span><span class="sxs-lookup"><span data-stu-id="ebcdd-175">Setting up a DSC web pull server</span></span>](../pull-server/pullServer.md)
