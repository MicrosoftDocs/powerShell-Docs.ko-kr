---
ms.date: 01/17/2019
keywords: dsc,powershell,configuration,setup
title: 노드 다시 부팅
ms.openlocfilehash: 22c63fab9b6646f522f8531b46a43a94ff883552
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2020
ms.locfileid: "71954030"
---
# <a name="reboot-a-node"></a><span data-ttu-id="d049f-103">노드 다시 부팅</span><span class="sxs-lookup"><span data-stu-id="d049f-103">Reboot a Node</span></span>

> [!NOTE]
> <span data-ttu-id="d049f-104">이 토픽에서는 노드를 다시 부팅하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="d049f-104">This topic talks about how to reboot a Node.</span></span> <span data-ttu-id="d049f-105">다시 부팅에 성공하기 위해 **ActionAfterReboot** 및 **RebootNodeIfNeeded** LCM 설정을 올바르게 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d049f-105">In order for the reboot to be successful the **ActionAfterReboot** and **RebootNodeIfNeeded** LCM settings need to be configured properly.</span></span>
> <span data-ttu-id="d049f-106">로컬 구성 관리자 설정에 대해 알라보려면 [로컬 구성 관리자 구성](../managing-nodes/metaConfig.md) 또는 [로컬 구성 관리자 구성(v4)](../managing-nodes/metaConfig4.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d049f-106">To read about Local Configuration Manager settings, see [Configure the Local Configuration Manager](../managing-nodes/metaConfig.md), or [Configure the Local Configuration Manager (v4)](../managing-nodes/metaConfig4.md).</span></span>

<span data-ttu-id="d049f-107">노드는 `$global:DSCMachineStatus` 플래그를 사용하여 리소스 내에서 다시 부팅될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d049f-107">Nodes can be rebooted from within a resource, by using the `$global:DSCMachineStatus` flag.</span></span> <span data-ttu-id="d049f-108">`1` 함수에서 이 플래그를 `Set-TargetResource`로 설정하면 현재 리소스의 **설정** 메서드 이후에 LCM가 노드를 직접 다시 부팅하도록 강제합니다.</span><span class="sxs-lookup"><span data-stu-id="d049f-108">Setting this flag to `1` in the `Set-TargetResource` function forces the LCM to reboot the Node directly after the **Set** method of the current resource.</span></span> <span data-ttu-id="d049f-109">이 플래그를 사용하여 **ComputerManagementDsc** DSC 리소스 모듈의 [PendingReboot](https://github.com/PowerShell/ComputerManagementDsc) 리소스는 재부팅이 DSC 외부에서 보류 중인지 탐지합니다.</span><span class="sxs-lookup"><span data-stu-id="d049f-109">Using this flag, the **PendingReboot** resource in the [ComputerManagementDsc](https://github.com/PowerShell/ComputerManagementDsc) DSC Resource module detects if a reboot is pending outside of DSC.</span></span>

<span data-ttu-id="d049f-110">[구성](configurations.md)은 노드를 다시 부팅해야 하는 단계를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d049f-110">Your [configurations](configurations.md) may perform steps that require the Node to reboot.</span></span> <span data-ttu-id="d049f-111">다음과 같은 작업을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d049f-111">This could include things such as:</span></span>

- <span data-ttu-id="d049f-112">Windows 업데이트</span><span class="sxs-lookup"><span data-stu-id="d049f-112">Windows updates</span></span>
- <span data-ttu-id="d049f-113">소프트웨어 설치</span><span class="sxs-lookup"><span data-stu-id="d049f-113">Software install</span></span>
- <span data-ttu-id="d049f-114">파일 이름 바꾸기</span><span class="sxs-lookup"><span data-stu-id="d049f-114">File renames</span></span>
- <span data-ttu-id="d049f-115">컴퓨터 이름 바꾸기</span><span class="sxs-lookup"><span data-stu-id="d049f-115">Computer rename</span></span>

<span data-ttu-id="d049f-116">**PendingReboot** 리소스는 특정 컴퓨터 위치를 검사하여 다시 부팅이 보류 중인지를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d049f-116">The **PendingReboot** resource checks specific computer locations to determine if a reboot is pending.</span></span> <span data-ttu-id="d049f-117">노드를 DSC 외부에서 다시 부팅해야 하는 경우 **PendingReboot** 리소스는 `$global:DSCMachineStatus` 플래그를 `1`로 설정하여 다시 부팅을 강제하고, 보류 중 상태를 해결합니다.</span><span class="sxs-lookup"><span data-stu-id="d049f-117">If the Node requires a reboot outside of DSC, the **PendingReboot** resource sets the `$global:DSCMachineStatus` flag to `1` forcing a reboot and resolving the pending condition.</span></span>

> [!NOTE]
> <span data-ttu-id="d049f-118">DSC 리소스는 LCM이 `Set-TargetResource` 함수에서 이 플래그를 설정하여 노드를 다시 부팅하도록 지시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d049f-118">Any DSC resource can instruct the LCM to reboot the node by setting this flag in the `Set-TargetResource` function.</span></span> <span data-ttu-id="d049f-119">자세한 내용은 [MOF를 사용하여 사용자 지정 DSC 리소스 작성](../resources/authoringResourceMOF.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d049f-119">For more information, see [Writing a custom DSC resource with MOF](../resources/authoringResourceMOF.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="d049f-120">구문</span><span class="sxs-lookup"><span data-stu-id="d049f-120">Syntax</span></span>

```
PendingReboot [String] #ResourceName
{
    Name = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
    [SkipCcmClientSDK = [bool]]
    [SkipComponentBasedServicing = [bool]]
    [SkipPendingComputerRename = [bool]]
    [SkipPendingFileRename = [bool]]
    [SkipWindowsUpdate = [bool]]
}
```

## <a name="properties"></a><span data-ttu-id="d049f-121">속성</span><span class="sxs-lookup"><span data-stu-id="d049f-121">Properties</span></span>

| <span data-ttu-id="d049f-122">속성</span><span class="sxs-lookup"><span data-stu-id="d049f-122">Property</span></span> | <span data-ttu-id="d049f-123">Description</span><span class="sxs-lookup"><span data-stu-id="d049f-123">Description</span></span> |
| --- | --- |
| <span data-ttu-id="d049f-124">속성</span><span class="sxs-lookup"><span data-stu-id="d049f-124">Name</span></span>| <span data-ttu-id="d049f-125">구성 내에서 리소스의 인스턴스마다 고유해야 하는 필수 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="d049f-125">Required parameter that must be unique per instance of the resource within a configuration.</span></span>|
| <span data-ttu-id="d049f-126">SkipComponentBasedServicing</span><span class="sxs-lookup"><span data-stu-id="d049f-126">SkipComponentBasedServicing</span></span> | <span data-ttu-id="d049f-127">구성 요소 기반 서비스 구성 요소에 의해 트리거되는 다시 부팅을 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="d049f-127">Skip reboots triggered by the Component-Based Servicing component.</span></span> |
| <span data-ttu-id="d049f-128">SkipWindowsUpdate</span><span class="sxs-lookup"><span data-stu-id="d049f-128">SkipWindowsUpdate</span></span> | <span data-ttu-id="d049f-129">Windows 업데이트에 의해 트리거되는 다시 부팅을 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="d049f-129">Skip reboots triggered by Windows Update.</span></span>|
| <span data-ttu-id="d049f-130">SkipPendingFileRename</span><span class="sxs-lookup"><span data-stu-id="d049f-130">SkipPendingFileRename</span></span> | <span data-ttu-id="d049f-131">보류 중인 파일 이름 바꾸기 다시 부팅을 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="d049f-131">Skip pending file rename reboots.</span></span> |
| <span data-ttu-id="d049f-132">SkipCcmClientSDK</span><span class="sxs-lookup"><span data-stu-id="d049f-132">SkipCcmClientSDK</span></span> | <span data-ttu-id="d049f-133">ConfigMgr 클라이언트에 의해 트리거되는 다시 부팅을 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="d049f-133">Skip reboots triggered by the ConfigMgr client.</span></span> |
| <span data-ttu-id="d049f-134">SkipComputerRename</span><span class="sxs-lookup"><span data-stu-id="d049f-134">SkipComputerRename</span></span> | <span data-ttu-id="d049f-135">컴퓨터 이름 바꾸기에 의해 트리거되는 다시 부팅을 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="d049f-135">Skip reboots triggered by Computer renames.</span></span> |
| <span data-ttu-id="d049f-136">PSDSCRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="d049f-136">PSDSCRunAsCredential</span></span> | <span data-ttu-id="d049f-137">v5에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="d049f-137">Supported in v5.</span></span> <span data-ttu-id="d049f-138">지정된 사용자로 리소스를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d049f-138">Executes the resource as the specified user.</span></span> |
| <span data-ttu-id="d049f-139">DependsOn</span><span class="sxs-lookup"><span data-stu-id="d049f-139">DependsOn</span></span> | <span data-ttu-id="d049f-140">이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d049f-140">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="d049f-141">예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 ID가 **ResourceName**이고 해당 형식이 **ResourceType**일 경우, 이 속성을 사용하기 위한 구문은 `DependsOn = "[ResourceType]ResourceName"`입니다.</span><span class="sxs-lookup"><span data-stu-id="d049f-141">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> <span data-ttu-id="d049f-142">자세한 내용은 [DependsOn 사용](resource-depends-on.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d049f-142">For more information, see [Using DependsOn](resource-depends-on.md)</span></span>|

## <a name="example"></a><span data-ttu-id="d049f-143">예제</span><span class="sxs-lookup"><span data-stu-id="d049f-143">Example</span></span>

<span data-ttu-id="d049f-144">다음 예제에서는 [xExchange](https://github.com/PowerShell/xExchange) 리소스를 사용하여 Microsoft Exchange를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="d049f-144">The following example installs Microsoft Exchange using the [xExchange](https://github.com/PowerShell/xExchange) resource.</span></span>
<span data-ttu-id="d049f-145">설치에서 **PendingReboot** 리소스는 노드를 다시 부팅하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d049f-145">Throughout the install, the **PendingReboot** resource is used to reboot the Node.</span></span>

> [!NOTE]
> <span data-ttu-id="d049f-146">이 예제에는 포리스트에 Exchange Server를 추가할 권한이 있는 계정의 자격 증명이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="d049f-146">This example requires the credential of an account that has rights to add an Exchange server to the forest.</span></span> <span data-ttu-id="d049f-147">DSC에서 자격 증명을 사용하는 방법에 대한 자세한 내용은 [DSC에서 자격 증명 처리](../configurations/configDataCredentials.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d049f-147">For more information on using credentials in DSC, see [Handling Credentials in DSC](../configurations/configDataCredentials.md)</span></span>

```powershell
$ConfigurationData = @{
    AllNodes = @(
        @{
            NodeName                    = '*'
            PSDSCAllowPlainTextPassword = $true
        },
        @{
            NodeName = 'DSCPULL-1'
        }
    )
}

Configuration Example
{
    param
    (
        [Parameter(Mandatory = $true)]
        [System.Management.Automation.PSCredential]
        $ExchangeAdminCredential
    )

    Import-DscResource -Module xExchange
    Import-DscResource -Module ComputerManagementDsc

    Node $AllNodes.NodeName
    {
        # Copy the Exchange setup files locally
        File ExchangeBinaries
        {
            Ensure          = 'Present'
            Type            = 'Directory'
            Recurse         = $true
            SourcePath      = '\\rras-1\Binaries\E15CU6'
            DestinationPath = 'C:\Binaries\E15CU6'
        }

        # Check if a reboot is needed before installing Exchange
        PendingReboot BeforeExchangeInstall
        {
            Name       = 'BeforeExchangeInstall'
            DependsOn  = '[File]ExchangeBinaries'
        }

        # Do the Exchange install
        xExchInstall InstallExchange
        {
            Path       = 'C:\Binaries\E15CU6\Setup.exe'
            Arguments  = '/mode:Install /role:Mailbox /Iacceptexchangeserverlicenseterms'
            Credential = $ExchangeAdminCredential
            DependsOn  = '[PendingReboot]BeforeExchangeInstall'
        }

        # See if a reboot is required after installing Exchange
        PendingReboot AfterExchangeInstall
        {
            Name      = 'AfterExchangeInstall'
            DependsOn = '[xExchInstall]InstallExchange'
        }
    }
}
```

> [!NOTE]
> <span data-ttu-id="d049f-148">이 예제에서는 다시 부팅을 허하고 다시 부팅 후에 구성을 계속하도록 로컬 구성 관리자를 구성했다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="d049f-148">This example assumes that you have configured your Local Configuration Manager to allow reboots and continue the configuration after a reboot.</span></span>

## <a name="where-to-download"></a><span data-ttu-id="d049f-149">다운로드 위치</span><span class="sxs-lookup"><span data-stu-id="d049f-149">Where to Download</span></span>

<span data-ttu-id="d049f-150">다음 위치에서 또는 PowerShell 갤러리를 사용하여 이 토픽에서 사용되는 리소스를 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d049f-150">You can download the resources used in this topic at the following locations, or by using the PowerShell gallery.</span></span>

- [<span data-ttu-id="d049f-151">ComputerManagementDsc</span><span class="sxs-lookup"><span data-stu-id="d049f-151">ComputerManagementDsc</span></span>](https://github.com/PowerShell/ComputerManagementDsc)
- [<span data-ttu-id="d049f-152">xExchange</span><span class="sxs-lookup"><span data-stu-id="d049f-152">xExchange</span></span>](https://github.com/PowerShell/xExchange)
