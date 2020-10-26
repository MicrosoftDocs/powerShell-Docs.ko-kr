---
ms.date: 07/10/2019
keywords: jea,powershell,security
title: JEA 구성 등록
description: 시스템에 JEA 엔드포인트를 등록하면 사용자 및 자동화 엔진에서 엔드포인트를 사용할 수 있게 됩니다.
ms.openlocfilehash: 6e7f8cdc1e7a666bddaa42034d70fcbcf55c1972
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/24/2020
ms.locfileid: "92499912"
---
# <a name="registering-jea-configurations"></a><span data-ttu-id="6d735-104">JEA 구성 등록</span><span class="sxs-lookup"><span data-stu-id="6d735-104">Registering JEA Configurations</span></span>

<span data-ttu-id="6d735-105">[역할 기능](role-capabilities.md) 및 [세션 구성 파일](session-configurations.md)을 만든 후 마지막 단계는 JEA 엔드포인트를 등록하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="6d735-105">Once you have your [role capabilities](role-capabilities.md) and [session configuration file](session-configurations.md) created, the last step is to register the JEA endpoint.</span></span> <span data-ttu-id="6d735-106">시스템에 JEA 엔드포인트를 등록하면 사용자 및 자동화 엔진에서 엔드포인트를 사용할 수 있게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d735-106">Registering the JEA endpoint with the system makes the endpoint available for use by users and automation engines.</span></span>

## <a name="single-machine-configuration"></a><span data-ttu-id="6d735-107">단일 컴퓨터 구성</span><span class="sxs-lookup"><span data-stu-id="6d735-107">Single machine configuration</span></span>

<span data-ttu-id="6d735-108">소규모 환경에서는 [Register-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/register-pssessionconfiguration) cmdlet을 사용해 세션 구성 파일을 등록하는 방법으로 JEA를 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d735-108">For small environments, you can deploy JEA by registering the session configuration file using the [Register-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/register-pssessionconfiguration) cmdlet.</span></span>

<span data-ttu-id="6d735-109">시작하기 전에 다음과 같은 필수 조건을 충족했는지 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="6d735-109">Before you begin, ensure that the following prerequisites have been met:</span></span>

- <span data-ttu-id="6d735-110">하나 이상의 역할이 생성되어 PowerShell 모듈의 **RoleCapabilities** 폴더에 배치되었습니다.</span><span class="sxs-lookup"><span data-stu-id="6d735-110">One or more roles has been created and placed in the **RoleCapabilities** folder of a PowerShell module.</span></span>
- <span data-ttu-id="6d735-111">세션 구성 파일을 만들고 테스트했습니다.</span><span class="sxs-lookup"><span data-stu-id="6d735-111">A session configuration file has been created and tested.</span></span>
- <span data-ttu-id="6d735-112">JEA 구성을 등록하는 사용자에게 시스템에 대한 관리자 권한이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d735-112">The user registering the JEA configuration has administrator rights on the system.</span></span>
- <span data-ttu-id="6d735-113">JEA 엔드포인트의 이름을 선택했습니다.</span><span class="sxs-lookup"><span data-stu-id="6d735-113">You've selected a name for your JEA endpoint.</span></span>

<span data-ttu-id="6d735-114">사용자가 JEA를 사용하여 시스템에 연결할 때 JEA 엔드포인트의 이름이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="6d735-114">The name of the JEA endpoint is required when users connect to the system using JEA.</span></span> <span data-ttu-id="6d735-115">[Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) cmdlet은 시스템의 엔드포인트 이름을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="6d735-115">The [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) cmdlet lists the names of the endpoints on a system.</span></span> <span data-ttu-id="6d735-116">`microsoft`로 시작하는 엔드포인트는 일반적으로 Windows와 함께 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d735-116">Endpoints that start with `microsoft` are typically shipped with Windows.</span></span> <span data-ttu-id="6d735-117">`microsoft.powershell` 엔드포인트는 원격 PowerShell 엔드포인트에 연결할 때 사용되는 기본 엔드포인트입니다.</span><span class="sxs-lookup"><span data-stu-id="6d735-117">The `microsoft.powershell` endpoint is the default endpoint used when connecting to a remote PowerShell endpoint.</span></span>

```powershell
Get-PSSessionConfiguration | Select-Object Name
```

```Output
Name
----
microsoft.powershell
microsoft.powershell.workflow
microsoft.powershell32
```

<span data-ttu-id="6d735-118">다음 명령을 실행하여 엔드포인트를 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="6d735-118">Run the following command to register the endpoint.</span></span>

```powershell
Register-PSSessionConfiguration -Path .\MyJEAConfig.pssc -Name 'JEAMaintenance' -Force
```

> [!WARNING]
> <span data-ttu-id="6d735-119">이전 명령은 시스템에서 WinRM 서비스를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="6d735-119">The previous command restarts the WinRM service on the system.</span></span> <span data-ttu-id="6d735-120">그러면 모든 PowerShell 원격 세션과 진행 중인 모든 DSC 구성이 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d735-120">This terminates all PowerShell remoting sessions and any ongoing DSC configurations.</span></span> <span data-ttu-id="6d735-121">비즈니스 운영이 중단되지 않게 하려면 명령을 실행하기 전에 프로덕션 머신을 오프라인 상태로 전환하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="6d735-121">We recommended you take production machines offline before running the command to avoid disrupting business operations.</span></span>

<span data-ttu-id="6d735-122">등록 후 [JEA를 사용](using-jea.md)할 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="6d735-122">After registration, you're ready to [use JEA](using-jea.md).</span></span> <span data-ttu-id="6d735-123">언제든지 세션 구성 파일을 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d735-123">You may delete the session configuration file at any time.</span></span> <span data-ttu-id="6d735-124">구성 파일은 엔드포인트 등록 후에 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6d735-124">The configuration file isn't used after registration of the endpoint.</span></span>

## <a name="multi-machine-configuration-with-dsc"></a><span data-ttu-id="6d735-125">DSC를 사용한 다중 컴퓨터 구성</span><span class="sxs-lookup"><span data-stu-id="6d735-125">Multi-machine configuration with DSC</span></span>

<span data-ttu-id="6d735-126">JEA를 여러 머신에 배포할 때 가장 간단한 배포 모델은 JEA [DSC(필요한 상태 구성)](../../../dsc/overview/overview.md) 리소스를 사용하여 각 머신에 신속하고 일관되게 JEA를 배포하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="6d735-126">When deploying JEA on multiple machines, the simplest deployment model uses the JEA [Desired State Configuration (DSC)](../../../dsc/overview/overview.md) resource to quickly and consistently deploy JEA on each machine.</span></span>

<span data-ttu-id="6d735-127">DSC를 사용하여 JEA를 배포하려면 다음 필수 조건이 충족되는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="6d735-127">To deploy JEA with DSC, ensure the following prerequisites are met:</span></span>

- <span data-ttu-id="6d735-128">하나 이상의 역할 기능을 작성하여 PowerShell 모듈에 추가했습니다.</span><span class="sxs-lookup"><span data-stu-id="6d735-128">One or more role capabilities have been authored and added to a PowerShell module.</span></span>
- <span data-ttu-id="6d735-129">역할을 포함하는 PowerShell 모듈을 각 컴퓨터에서 액세스할 수 있는 (읽기 전용) 파일 공유에 저장했습니다.</span><span class="sxs-lookup"><span data-stu-id="6d735-129">The PowerShell module containing the roles is stored on a (read-only) file share accessible by each machine.</span></span>
- <span data-ttu-id="6d735-130">세션 구성에 대한 설정을 결정했습니다.</span><span class="sxs-lookup"><span data-stu-id="6d735-130">Settings for the session configuration have been determined.</span></span> <span data-ttu-id="6d735-131">JEA DSC 리소스를 사용할 때 세션 구성 파일을 만들 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6d735-131">You don't need to create a session configuration file when using the JEA DSC resource.</span></span>
- <span data-ttu-id="6d735-132">각 머신에서 관리 작업을 허용하거나 해당 머신을 관리하는 데 사용되는 DSC 끌어오기 서버에 액세스할 수 있는 자격 증명이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d735-132">You have credentials that allow administrative actions on each machine or access to the DSC pull server used to manage the machines.</span></span>
- <span data-ttu-id="6d735-133">[JEA DSC 리소스](https://github.com/powershell/JEA/tree/master/DSC%20Resource)를 다운로드했습니다.</span><span class="sxs-lookup"><span data-stu-id="6d735-133">You've downloaded the [JEA DSC resource](https://github.com/powershell/JEA/tree/master/DSC%20Resource).</span></span>

<span data-ttu-id="6d735-134">대상 머신 또는 풀 서버에 JEA 엔드포인트에 대한 DSC 구성을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6d735-134">Create a DSC configuration for your JEA endpoint on a target machine or pull server.</span></span> <span data-ttu-id="6d735-135">이 구성에서는 **JustEnoughAdministration** DSC 리소스가 세션 구성 파일을 정의하고 **File** 리소스가 파일 공유에서 역할 기능을 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="6d735-135">In this configuration, the **JustEnoughAdministration** DSC resource defines the session configuration file and the **File** resource copies the role capabilities from the file share.</span></span>

<span data-ttu-id="6d735-136">DSC 리소스를 사용하여 다음 속성을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d735-136">The following properties are configurable using the DSC resource:</span></span>

- <span data-ttu-id="6d735-137">역할 정의</span><span class="sxs-lookup"><span data-stu-id="6d735-137">Role Definitions</span></span>
- <span data-ttu-id="6d735-138">가상 계정 그룹</span><span class="sxs-lookup"><span data-stu-id="6d735-138">Virtual account groups</span></span>
- <span data-ttu-id="6d735-139">그룹 관리 서비스 계정 이름</span><span class="sxs-lookup"><span data-stu-id="6d735-139">Group-managed service account name</span></span>
- <span data-ttu-id="6d735-140">기록 디렉터리</span><span class="sxs-lookup"><span data-stu-id="6d735-140">Transcript directory</span></span>
- <span data-ttu-id="6d735-141">사용자 드라이브</span><span class="sxs-lookup"><span data-stu-id="6d735-141">User drive</span></span>
- <span data-ttu-id="6d735-142">조건부 액세스 규칙</span><span class="sxs-lookup"><span data-stu-id="6d735-142">Conditional access rules</span></span>
- <span data-ttu-id="6d735-143">JEA 세션에 대한 시작 스크립트</span><span class="sxs-lookup"><span data-stu-id="6d735-143">Startup scripts for the JEA session</span></span>

<span data-ttu-id="6d735-144">DSC 구성에서 이러한 각 속성에 대한 구문은 PowerShell 세션 구성 파일과 일치합니다.</span><span class="sxs-lookup"><span data-stu-id="6d735-144">The syntax for each of these properties in a DSC configuration is consistent with the PowerShell session configuration file.</span></span>

<span data-ttu-id="6d735-145">다음은 일반 서버 유지 관리 모듈에 대한 샘플 DSC 구성입니다.</span><span class="sxs-lookup"><span data-stu-id="6d735-145">Below is a sample DSC configuration for a general server maintenance module.</span></span> <span data-ttu-id="6d735-146">역할 기능을 포함하는 유효한 PowerShell 모듈이 `\\myfileshare\JEA` 파일 공유에 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="6d735-146">It assumes that a valid PowerShell module containing role capabilities is located on the `\\myfileshare\JEA` file share.</span></span>

```powershell
Configuration JEAMaintenance
{
    Import-DscResource -Module JustEnoughAdministration, PSDesiredStateConfiguration

    File MaintenanceModule
    {
        SourcePath = "\\myfileshare\JEA\ContosoMaintenance"
        DestinationPath = "C:\Program Files\WindowsPowerShell\Modules\ContosoMaintenance"
        Checksum = "SHA-256"
        Ensure = "Present"
        Type = "Directory"
        Recurse = $true
    }

    JeaEndpoint JEAMaintenanceEndpoint
    {
        EndpointName = "JEAMaintenance"
        RoleDefinitions = "@{ 'CONTOSO\JEAMaintenanceAuditors' = @{ RoleCapabilities = 'GeneralServerMaintenance-Audit' }; 'CONTOSO\JEAMaintenanceAdmins' = @{ RoleCapabilities = 'GeneralServerMaintenance-Audit', 'GeneralServerMaintenance-Admin' } }"
        TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
        DependsOn = '[File]MaintenanceModule'
    }
}
```

<span data-ttu-id="6d735-147">그런 다음, [로컬 구성 관리자](/powershell/scripting/dsc/managing-nodes/metaConfig)를 직접 호출하거나 [끌어오기 서버 구성](/powershell/scripting/dsc/pull-server/pullServer)을 업데이트하여 시스템에 이 구성을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="6d735-147">Next, the configuration is applied on a system by directly invoking the [Local Configuration Manager](/powershell/scripting/dsc/managing-nodes/metaConfig) or updating the [pull server configuration](/powershell/scripting/dsc/pull-server/pullServer).</span></span>

<span data-ttu-id="6d735-148">DSC 리소스를 사용하여 기본 **Microsoft.PowerShell** 엔드포인트를 바꿀 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d735-148">The DSC resource also allows you to replace the default **Microsoft.PowerShell** endpoint.</span></span> <span data-ttu-id="6d735-149">바꾸면 리소스가 **Microsoft.PowerShell.Restricted** 라는 백업 엔드포인트를 자동으로 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="6d735-149">When replaced, the resource automatically registers a backup endpoint named **Microsoft.PowerShell.Restricted** .</span></span> <span data-ttu-id="6d735-150">백업 엔드포인트에는 원격 관리 사용자 및 로컬 Administrators 그룹 멤버가 액세스할 수 있도록 하는 기본 WinRM ACL이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d735-150">The backup endpoint has the default WinRM ACL that allows Remote Management Users and local Administrators group members to access it.</span></span>

## <a name="unregistering-jea-configurations"></a><span data-ttu-id="6d735-151">JEA 구성 등록 취소</span><span class="sxs-lookup"><span data-stu-id="6d735-151">Unregistering JEA configurations</span></span>

<span data-ttu-id="6d735-152">[Unregister-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/Unregister-PSSessionConfiguration) cmdlet이 JEA 엔드포인트를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="6d735-152">The [Unregister-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/Unregister-PSSessionConfiguration) cmdlet removes a JEA endpoint.</span></span> <span data-ttu-id="6d735-153">JEA 엔드포인트를 등록 취소하면 새 사용자가 시스템에서 새 JEA 세션을 만들지 못합니다.</span><span class="sxs-lookup"><span data-stu-id="6d735-153">Unregistering a JEA endpoint prevents new users from creating new JEA sessions on the system.</span></span> <span data-ttu-id="6d735-154">같은 엔드포인트 이름을 사용하여 업데이트된 세션 구성 파일을 다시 등록하는 방법으로 JEA 구성을 업데이트할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d735-154">It also allows you to update a JEA configuration by re-registering an updated session configuration file using the same endpoint name.</span></span>

```powershell
# Unregister the JEA endpoint called "ContosoMaintenance"
Unregister-PSSessionConfiguration -Name 'ContosoMaintenance' -Force
```

> [!WARNING]
> <span data-ttu-id="6d735-155">JEA 엔드포인트를 등록 취소하면 WinRM 서비스가 다시 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d735-155">Unregistering a JEA endpoint causes the WinRM service to restart.</span></span> <span data-ttu-id="6d735-156">그러면 다른 PowerShell 세션, WMI 호출 및 일부 관리 도구를 비롯한 진행 중인 대부분의 원격 관리 작업이 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d735-156">This interrupts most remote management operations in progress, including other PowerShell sessions, WMI invocations, and some management tools.</span></span> <span data-ttu-id="6d735-157">계획된 유지 관리 기간에는 PowerShell 엔드포인트만 등록 취소하세요.</span><span class="sxs-lookup"><span data-stu-id="6d735-157">Only unregister PowerShell endpoints during planned maintenance windows.</span></span>

## <a name="next-steps"></a><span data-ttu-id="6d735-158">다음 단계</span><span class="sxs-lookup"><span data-stu-id="6d735-158">Next steps</span></span>

[<span data-ttu-id="6d735-159">JEA 엔드포인트 테스트</span><span class="sxs-lookup"><span data-stu-id="6d735-159">Test the JEA endpoint</span></span>](using-jea.md)
