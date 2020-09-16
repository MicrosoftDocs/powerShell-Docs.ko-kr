---
ms.date: 08/15/2019
keywords: dsc,powershell,configuration,setup
title: Windows용 DSC(필요한 상태 구성) 시작
ms.openlocfilehash: 00e1cf545b19f054b4b1ff468c9f6ad94e5cef55
ms.sourcegitcommit: c4906f4c9fa4ef1a16dcd6dd00ff960d19446d71
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/01/2020
ms.locfileid: "89236325"
---
# <a name="get-started-with-desired-state-configuration-dsc-for-windows"></a><span data-ttu-id="911cd-103">Windows용 DSC(필요한 상태 구성) 시작</span><span class="sxs-lookup"><span data-stu-id="911cd-103">Get started with Desired State Configuration (DSC) for Windows</span></span>

<span data-ttu-id="911cd-104">이 항목에서는 Windows용 PowerShell DSC(필요한 상태 구성) 사용 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="911cd-104">This topic explains how to get started using PowerShell Desired State Configuration (DSC) for Windows.</span></span>
<span data-ttu-id="911cd-105">DSC에 대한 일반적인 내용은 [Windows PowerShell 필요한 상태 구성 시작](../overview/overview.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="911cd-105">For general information about DSC, see [Get Started with Windows PowerShell Desired State Configuration](../overview/overview.md).</span></span>

## <a name="supported-windows-operation-system-versions"></a><span data-ttu-id="911cd-106">지원되는 Windows 운영 체제 버전</span><span class="sxs-lookup"><span data-stu-id="911cd-106">Supported Windows operation system versions</span></span>

<span data-ttu-id="911cd-107">지원되는 버전은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="911cd-107">The following versions are supported:</span></span>

- <span data-ttu-id="911cd-108">Windows Server 2019</span><span class="sxs-lookup"><span data-stu-id="911cd-108">Windows Server 2019</span></span>
- <span data-ttu-id="911cd-109">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="911cd-109">Windows Server 2016</span></span>
- <span data-ttu-id="911cd-110">Windows Server 2012R2</span><span class="sxs-lookup"><span data-stu-id="911cd-110">Windows Server 2012R2</span></span>
- <span data-ttu-id="911cd-111">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="911cd-111">Windows Server 2012</span></span>
- <span data-ttu-id="911cd-112">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="911cd-112">Windows Server 2008 R2 SP1</span></span>
- <span data-ttu-id="911cd-113">윈도우 10</span><span class="sxs-lookup"><span data-stu-id="911cd-113">Windows 10</span></span>
- <span data-ttu-id="911cd-114">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="911cd-114">Windows 8.1</span></span>
- <span data-ttu-id="911cd-115">Windows 7</span><span class="sxs-lookup"><span data-stu-id="911cd-115">Windows 7</span></span>

<span data-ttu-id="911cd-116">[Microsoft Hyper-V Server](/windows-server/virtualization/hyper-v/hyper-v-server-2016) 독립 실행형 제품 SKU는 필요한 상태 구성의 구현을 포함하지 않으므로 PowerShell DSC 또는 Azure Automation 상태 구성으로 관리할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="911cd-116">The [Microsoft Hyper-V Server](/windows-server/virtualization/hyper-v/hyper-v-server-2016) standalone product sku doesn't contain an implementation of Desired State Configuration so it cannot be managed by PowerShell DSC or Azure Automation State Configuration.</span></span>

## <a name="installing-dsc"></a><span data-ttu-id="911cd-117">DSC 설치</span><span class="sxs-lookup"><span data-stu-id="911cd-117">Installing DSC</span></span>

<span data-ttu-id="911cd-118">PowerShell 필요한 상태 구성은 Windows에 포함되어 있으며 Windows Management Framework를 통해 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="911cd-118">PowerShell Desired State Configuration is included in Windows and updated through Windows Management Framework.</span></span> <span data-ttu-id="911cd-119">최신 버전은 [Windows Management Framework 5.1](https://www.microsoft.com/download/details.aspx?id=54616)입니다.</span><span class="sxs-lookup"><span data-stu-id="911cd-119">The latest version is [Windows Management Framework 5.1](https://www.microsoft.com/download/details.aspx?id=54616).</span></span>

> [!NOTE]
> <span data-ttu-id="911cd-120">DSC를 사용하여 머신을 관리하기 위해 Windows Server 기능 ' DSC-서비스'를 사용하도록 설정할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="911cd-120">You do not need to enable the Windows Server feature 'DSC-Service' to manage a machine using DSC.</span></span>
> <span data-ttu-id="911cd-121">이 기능은 Windows 끌어오기 서버 인스턴스를 빌드할 때만 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="911cd-121">That feature is only needed when building a Windows Pull Server instance.</span></span>

## <a name="using-dsc-for-windows"></a><span data-ttu-id="911cd-122">Windows용 DSC 사용</span><span class="sxs-lookup"><span data-stu-id="911cd-122">Using DSC for Windows</span></span>

<span data-ttu-id="911cd-123">다음 섹션에서는 Windows 컴퓨터에서 DSC 구성을 만들고 실행하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="911cd-123">The following sections explain how to create and run DSC configurations on Windows computers.</span></span>

### <a name="creating-a-configuration-mof-document"></a><span data-ttu-id="911cd-124">구성 MOF 문서 만들기</span><span class="sxs-lookup"><span data-stu-id="911cd-124">Creating a configuration MOF document</span></span>

<span data-ttu-id="911cd-125">Windows PowerShell `Configuration` 키워드는 구성을 만드는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="911cd-125">The Windows PowerShell `Configuration` keyword is used to create a configuration.</span></span>
<span data-ttu-id="911cd-126">다음 단계에서는 Windows PowerShell을 사용한 구성 문서 작성에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="911cd-126">The following steps describe the creation of a configuration document using Windows PowerShell.</span></span>

#### <a name="define-a-configuration-and-generate-the-configuration-document"></a><span data-ttu-id="911cd-127">구성을 정의하고 구성 문서를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="911cd-127">Define a configuration and generate the configuration document:</span></span>

```powershell
Configuration EnvironmentVariable_Path
{
    param ()

    Import-DscResource -ModuleName 'PSDscResources'

    Node localhost
    {
        Environment CreatePathEnvironmentVariable
        {
            Name = 'TestPathEnvironmentVariable'
            Value = 'TestValue'
            Ensure = 'Present'
            Path = $true
            Target = @('Process', 'Machine')
        }
    }
}

EnvironmentVariable_Path -OutputPath:"C:\EnvironmentVariable_Path"
```

#### <a name="install-a-module-containing-dsc-resources"></a><span data-ttu-id="911cd-128">DSC 리소스를 포함하는 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="911cd-128">Install a module containing DSC resources</span></span>

<span data-ttu-id="911cd-129">Windows PowerShell 필요한 상태 구성에는 DSC 리소스를 포함하는 기본 제공 모듈이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="911cd-129">Windows PowerShell Desired State Configuration includes built-in modules containing DSC resources.</span></span>
<span data-ttu-id="911cd-130">PowerShellGet cmdlet을 사용하는 PowerShell 갤러리 같은 외부 소스에서 모듈을 로드할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="911cd-130">You can also load modules from external sources such as the PowerShell Gallery, using the PowerShellGet cmdlets.</span></span>

```PowerShell
Install-Module 'PSDscResources' -Verbose
```

#### <a name="apply-the-configuration-to-the-machine"></a><span data-ttu-id="911cd-131">머신에 구성 적용</span><span class="sxs-lookup"><span data-stu-id="911cd-131">Apply the configuration to the machine</span></span>

> [!NOTE]
> <span data-ttu-id="911cd-132">DSC를 실행할 수 있도록 하려면 `localhost` 구성을 실행 하는 경우에도 PowerShell 원격 명령을 받도록 Windows를 구성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="911cd-132">To allow DSC to run, Windows needs to be configured to receive PowerShell remote commands even when you're running a `localhost` configuration.</span></span> <span data-ttu-id="911cd-133">환경을 올바르게 구성하려면 관리자 권한 PowerShell 터미널에서 `Set-WsManQuickConfig -Force`를 실행하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="911cd-133">To easily configure your environment correctly, just run `Set-WsManQuickConfig -Force` in an elevated PowerShell Terminal.</span></span>

<span data-ttu-id="911cd-134">구성 문서(MOF 파일)를 [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet을 사용하여 머신에 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="911cd-134">Configuration documents (MOF files) can be applied to the machineusing the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span>

```powershell
Start-DscConfiguration -Path 'C:\EnvironmentVariable_Path' -Wait -Verbose
```

#### <a name="get-the-current-state-of-the-configuration"></a><span data-ttu-id="911cd-135">구성의 현재 상태 가져오기</span><span class="sxs-lookup"><span data-stu-id="911cd-135">Get the current state of the configuration</span></span>

<span data-ttu-id="911cd-136">[Get-DscConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) cmdlet은 머신의 현재 상태를 쿼리하고 구성에 대한 현재 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="911cd-136">The [Get-DscConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) cmdlet queries the current status of the machine and returns the current values for the configuration.</span></span>

```powershell
Get-DscConfiguration
```

<span data-ttu-id="911cd-137">[Get-DscLocalConfigurationManager](/powershell/module/psdesiredstateconfiguration/get-dscLocalConfigurationManager) cmdlet은 머신에 적용된 현재 메타 구성을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="911cd-137">The [Get-DscLocalConfigurationManager](/powershell/module/psdesiredstateconfiguration/get-dscLocalConfigurationManager) cmdlet returns the current meta-configuration applied to the machine.</span></span>

```powershell
Get-DscLocalConfigurationManager
```

#### <a name="remove-the-current-configuration-from-a-machine"></a><span data-ttu-id="911cd-138">머신에서 현재 구성 제거</span><span class="sxs-lookup"><span data-stu-id="911cd-138">Remove the current configuration from a machine</span></span>

<span data-ttu-id="911cd-139">[Remove-DscConfigurationDocument](/powershell/module/psdesiredstateconfiguration/remove-dscconfigurationdocument)</span><span class="sxs-lookup"><span data-stu-id="911cd-139">The [Remove-DscConfigurationDocument](/powershell/module/psdesiredstateconfiguration/remove-dscconfigurationdocument)</span></span>

```powershell
Remove-DscConfigurationDocument -Stage Current -Verbose
```

#### <a name="configure-settings-in-local-configuration-manager"></a><span data-ttu-id="911cd-140">로컬 구성 관리자에서 설정 구성</span><span class="sxs-lookup"><span data-stu-id="911cd-140">Configure settings in Local Configuration Manager</span></span>

<span data-ttu-id="911cd-141">[Set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) cmdlet을 사용하여 메타 구성 MOF 파일을 머신에 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="911cd-141">Apply a Meta Configuration MOF file to the machine using the [Set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) cmdlet.</span></span>
<span data-ttu-id="911cd-142">메타 구성 MOF의 경로가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="911cd-142">Requires the path to the Meta Configuration MOF.</span></span>

```powershell
Set-DSCLocalConfigurationManager -Path 'c:\metaconfig\localhost.meta.mof' -Verbose
```

## <a name="windows-powershell-desired-state-configuration-log-files"></a><span data-ttu-id="911cd-143">Windows PowerShell 필요한 상태 구성 로그 파일</span><span class="sxs-lookup"><span data-stu-id="911cd-143">Windows PowerShell Desired State Configuration log files</span></span>

<span data-ttu-id="911cd-144">DSC에 대한 로그는 경로 `Microsoft-Windows-Dsc/Operational`에 있는 Windows 이벤트 로그에 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="911cd-144">Logs for DSC are written to Windows Event Log in the path `Microsoft-Windows-Dsc/Operational`.</span></span>
<span data-ttu-id="911cd-145">디버깅 목적을 위한 추가 로그는 [DSC 이벤트 로그 위치](/powershell/scripting/dsc/troubleshooting/troubleshooting#where-are-dsc-event-logs)의 단계에 따라 사용하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="911cd-145">Additional logs for debugging purposes can be enabled following the steps in [Where Are DSC Event Logs](/powershell/scripting/dsc/troubleshooting/troubleshooting#where-are-dsc-event-logs).</span></span>
