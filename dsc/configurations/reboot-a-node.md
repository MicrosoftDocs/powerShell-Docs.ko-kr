---
ms.date: 1/17/2019
keywords: dsc,powershell,configuration,setup
title: 노드 다시 부팅
ms.openlocfilehash: 33ecd98aa62c3dc94a8ff2213fd3e68bf0c05cb7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55680743"
---
# <a name="reboot-a-node"></a><span data-ttu-id="4fe24-103">노드 다시 부팅</span><span class="sxs-lookup"><span data-stu-id="4fe24-103">Reboot a Node</span></span>

> [!NOTE]
> <span data-ttu-id="4fe24-104">이 항목에서는 노드를 다시 부팅 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="4fe24-104">This topic talks about how to reboot a Node.</span></span> <span data-ttu-id="4fe24-105">찾기가 성공 하려면 다시 부팅 순서에서를 **ActionAfterReboot** 및 **RebootNodeIfNeeded** LCM 설정을 올바르게 구성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4fe24-105">In order for the reboot to be successful the **ActionAfterReboot** and **RebootNodeIfNeeded** LCM settings need to be configured properly.</span></span>
> <span data-ttu-id="4fe24-106">로컬 구성 관리자 설정에 대 한 내용은 참조 하세요 [로컬 구성 관리자 구성](../managing-nodes/metaConfig.md), 또는 [구성 로컬 구성 관리자 (v4)](../managing-nodes/metaConfig4.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="4fe24-106">To read about Local Configuration Manager settings, see [Configure the Local Configuration Manager](../managing-nodes/metaConfig.md), or [Configure the Local Configuration Manager (v4)](../managing-nodes/metaConfig4.md).</span></span>

<span data-ttu-id="4fe24-107">노드 다시 부팅할 수에서 리소스를 내에서 사용 하 여는 `$global:DSCMachineStatus` 플래그입니다.</span><span class="sxs-lookup"><span data-stu-id="4fe24-107">Nodes can be rebooted from within a resource, by using the `$global:DSCMachineStatus` flag.</span></span> <span data-ttu-id="4fe24-108">이 플래그 설정 `1` 에 `Set-TargetResource` 함수 후 노드를 직접 다시 부팅 하도록 LCM을 강제로 합니다 **설정** 현재 리소스의 메서드.</span><span class="sxs-lookup"><span data-stu-id="4fe24-108">Setting this flag to `1` in the `Set-TargetResource` function forces the LCM to reboot the Node directly after the **Set** method of the current resource.</span></span> <span data-ttu-id="4fe24-109">이 플래그를 사용 하는 **xPendingReboot** 리소스 검색을 다시 부팅이 보류 중인 경우 DSC 외부입니다.</span><span class="sxs-lookup"><span data-stu-id="4fe24-109">Using this flag, the **xPendingReboot** resource detects if a reboot is pending outside of DSC.</span></span>

<span data-ttu-id="4fe24-110">프로그램 [구성을](configurations.md) 노드를 다시 부팅 해야 하는 단계를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fe24-110">Your [configurations](configurations.md) may perform steps that require the Node to reboot.</span></span> <span data-ttu-id="4fe24-111">와 같은 작업을 포함할 수 없습니다이:</span><span class="sxs-lookup"><span data-stu-id="4fe24-111">This could include things such as:</span></span>

- <span data-ttu-id="4fe24-112">Windows: 업데이트</span><span class="sxs-lookup"><span data-stu-id="4fe24-112">Windows updates</span></span>
- <span data-ttu-id="4fe24-113">소프트웨어 설치</span><span class="sxs-lookup"><span data-stu-id="4fe24-113">Software install</span></span>
- <span data-ttu-id="4fe24-114">파일의 이름을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="4fe24-114">File renames</span></span>
- <span data-ttu-id="4fe24-115">컴퓨터 이름 바꾸기</span><span class="sxs-lookup"><span data-stu-id="4fe24-115">Computer rename</span></span>

<span data-ttu-id="4fe24-116">합니다 **xPendingReboot** 리소스는 다시 부팅이 보류 중인 경우를 확인 하려면 특정 컴퓨터 위치를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="4fe24-116">The **xPendingReboot** resource checks specific computer locations to determine if a reboot is pending.</span></span> <span data-ttu-id="4fe24-117">노드는 DSC 외부에서 다시 부팅 해야 하는 경우는 **xPendingReboot** 리소스 집합을 `$global:DSCMachineStatus` 플래그를 `1` 강제로 다시 부팅 되 고, 보류 중 상태를 해결 합니다.</span><span class="sxs-lookup"><span data-stu-id="4fe24-117">If the Node requires a reboot outside of DSC, the **xPendingReboot** resource sets the `$global:DSCMachineStatus` flag to `1` forcing a reboot and resolving the pending condition.</span></span>

> [!NOTE]
> <span data-ttu-id="4fe24-118">모든 DSC 리소스는 LCM에서이 플래그를 설정 하 여 노드를 다시 부팅을 지시할 수는 `Set-TargetResource` 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="4fe24-118">Any DSC resource can instruct the LCM to reboot the node by setting this flag in the `Set-TargetResource` function.</span></span> <span data-ttu-id="4fe24-119">자세한 내용은 [MOF 사용 하 여 사용자 지정 DSC 리소스 작성](../resources/authoringResourceMOF.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="4fe24-119">For more information, see [Writing a custom DSC resource with MOF](../resources/authoringResourceMOF.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="4fe24-120">구문</span><span class="sxs-lookup"><span data-stu-id="4fe24-120">Syntax</span></span>

```
xPendingReboot [String] #ResourceName
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

## <a name="properties"></a><span data-ttu-id="4fe24-121">속성</span><span class="sxs-lookup"><span data-stu-id="4fe24-121">Properties</span></span>

| <span data-ttu-id="4fe24-122">속성</span><span class="sxs-lookup"><span data-stu-id="4fe24-122">Property</span></span> | <span data-ttu-id="4fe24-123">설명</span><span class="sxs-lookup"><span data-stu-id="4fe24-123">Description</span></span> |
| --- | --- |
| <span data-ttu-id="4fe24-124">이름</span><span class="sxs-lookup"><span data-stu-id="4fe24-124">Name</span></span>| <span data-ttu-id="4fe24-125">구성 내에서 리소스의 인스턴스당 고유 해야 하는 필수 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="4fe24-125">Required parameter that must be unique per instance of the resource within a configuration.</span></span>|
| <span data-ttu-id="4fe24-126">SkipComponentBasedServicing</span><span class="sxs-lookup"><span data-stu-id="4fe24-126">SkipComponentBasedServicing</span></span> | <span data-ttu-id="4fe24-127">구성 요소 기반 서비스 구성 요소에 의해 트리거되는 Skip 재부팅 합니다.</span><span class="sxs-lookup"><span data-stu-id="4fe24-127">Skip reboots triggered by the Component-Based Servicing component.</span></span> |
| <span data-ttu-id="4fe24-128">SkipWindowsUpdate</span><span class="sxs-lookup"><span data-stu-id="4fe24-128">SkipWindowsUpdate</span></span> | <span data-ttu-id="4fe24-129">Windows 업데이트에 의해 트리거되는 Skip 재부팅 합니다.</span><span class="sxs-lookup"><span data-stu-id="4fe24-129">Skip reboots triggered by Windows Update.</span></span>|
| <span data-ttu-id="4fe24-130">SkipPendingFileRename</span><span class="sxs-lookup"><span data-stu-id="4fe24-130">SkipPendingFileRename</span></span> | <span data-ttu-id="4fe24-131">보류 중인 파일 이름 바꾸기 다시 부팅을 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="4fe24-131">Skip pending file rename reboots.</span></span> |
| <span data-ttu-id="4fe24-132">SkipCcmClientSDK</span><span class="sxs-lookup"><span data-stu-id="4fe24-132">SkipCcmClientSDK</span></span> | <span data-ttu-id="4fe24-133">ConfigMgr 클라이언트에 의해 트리거되는 Skip 재부팅 합니다.</span><span class="sxs-lookup"><span data-stu-id="4fe24-133">Skip reboots triggered by the ConfigMgr client.</span></span> |
| <span data-ttu-id="4fe24-134">SkipComputerRename</span><span class="sxs-lookup"><span data-stu-id="4fe24-134">SkipComputerRename</span></span> | <span data-ttu-id="4fe24-135">Skip은 컴퓨터 이름을 변경 하 여 트리거된 다시 부팅 합니다.</span><span class="sxs-lookup"><span data-stu-id="4fe24-135">Skip reboots triggerd by Computer renames.</span></span> |
| <span data-ttu-id="4fe24-136">PSDSCRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="4fe24-136">PSDSCRunAsCredential</span></span> | <span data-ttu-id="4fe24-137">V5에서 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="4fe24-137">Supported in v5.</span></span> <span data-ttu-id="4fe24-138">지정된 된 사용자로 리소스를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="4fe24-138">Executes the resource as the specified user.</span></span> |
| <span data-ttu-id="4fe24-139">DependsOn</span><span class="sxs-lookup"><span data-stu-id="4fe24-139">DependsOn</span></span> | <span data-ttu-id="4fe24-140">이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4fe24-140">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="4fe24-141">예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 ID가 **ResourceName**이고 해당 형식이 **ResourceType**일 경우, 이 속성을 사용하기 위한 구문은 `DependsOn = "[ResourceType]ResourceName"`입니다.</span><span class="sxs-lookup"><span data-stu-id="4fe24-141">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> <span data-ttu-id="4fe24-142">자세한 내용은 참조 하세요. [DependsOn 사용](resource-depends-on.md)</span><span class="sxs-lookup"><span data-stu-id="4fe24-142">For more information, see [Using DependsOn](resource-depends-on.md)</span></span>|

## <a name="example"></a><span data-ttu-id="4fe24-143">예제</span><span class="sxs-lookup"><span data-stu-id="4fe24-143">Example</span></span>

<span data-ttu-id="4fe24-144">다음 예제에서는 Microsoft Exchange를 사용 하 여 설치 합니다 [xExchange](https://github.com/PowerShell/xExchange) 리소스입니다.</span><span class="sxs-lookup"><span data-stu-id="4fe24-144">The following example installs Microsoft Exchange using the [xExchange](https://github.com/PowerShell/xExchange) resource.</span></span>
<span data-ttu-id="4fe24-145">전체 설치를 **xPendingReboot** 리소스는 노드를 다시 부팅 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4fe24-145">Throughout the install, the **xPendingReboot** resource is used to reboot the Node.</span></span>

> [!NOTE]
> <span data-ttu-id="4fe24-146">이 예제에는 포리스트에 Exchange server를 추가할 권한이 있는 계정의 자격 증명이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="4fe24-146">This example requires the credential of an account that has rights to add an Exchange server to the forest.</span></span> <span data-ttu-id="4fe24-147">자격 증명을 사용 하 여 DSC에 대 한 자세한 내용은 참조 하세요. [DSC에서 자격 증명 처리](../configurations/configDataCredentials.md)</span><span class="sxs-lookup"><span data-stu-id="4fe24-147">For more information on using credentials in DSC, see [Handling Credentials in DSC](../configurations/configDataCredentials.md)</span></span>

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
    Import-DscResource -Module xPendingReboot

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
        xPendingReboot BeforeExchangeInstall
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
            DependsOn  = '[xPendingReboot]BeforeExchangeInstall'
        }

        # See if a reboot is required after installing Exchange
        xPendingReboot AfterExchangeInstall
        {
            Name      = 'AfterExchangeInstall'
            DependsOn = '[xExchInstall]InstallExchange'
        }
    }
}
```

> [!NOTE]
> <span data-ttu-id="4fe24-148">이 예제에서는 재부팅을 허용 하 고 다시 부팅 한 후 구성을 계속 하려면 로컬 Configuration Manager 구성 했다고 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4fe24-148">This example assumes that you have configured your Local Configuration Manager to allow reboots and continue the configuration after a reboot.</span></span>

## <a name="where-to-download"></a><span data-ttu-id="4fe24-149">다운로드 위치</span><span class="sxs-lookup"><span data-stu-id="4fe24-149">Where to Download</span></span>

<span data-ttu-id="4fe24-150">다음 위치에서 또는 PowerShell 갤러리를 사용 하 여이 항목에서 사용 하는 리소스를 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fe24-150">You can download the resources used in this topic at the following locations, or by using the PowerShell gallery.</span></span>

- [<span data-ttu-id="4fe24-151">xPendingReboot</span><span class="sxs-lookup"><span data-stu-id="4fe24-151">xPendingReboot</span></span>](https://github.com/PowerShell/xPendingReboot)
- [<span data-ttu-id="4fe24-152">xExchange</span><span class="sxs-lookup"><span data-stu-id="4fe24-152">xExchange</span></span>](https://github.com/PowerShell/xExchange)
