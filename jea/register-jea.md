---
ms.date: 06/12/2017
keywords: jea,powershell,security
title: JEA 구성 등록
ms.openlocfilehash: 6fa0ce434c8e70eb718545e99417bfe034cda6bf
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084830"
---
# <a name="registering-jea-configurations"></a><span data-ttu-id="4a1fc-103">JEA 구성 등록</span><span class="sxs-lookup"><span data-stu-id="4a1fc-103">Registering JEA Configurations</span></span>

> <span data-ttu-id="4a1fc-104">적용 대상: Windows Powershell 5.0</span><span class="sxs-lookup"><span data-stu-id="4a1fc-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="4a1fc-105">[역할 기능](role-capabilities.md) 및 [세션 구성 파일](session-configurations.md)을 만든 후 JEA를 사용하기 위한 마지막 단계는 JEA 엔드포인트를 등록하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="4a1fc-105">Once you have your [role capabilities](role-capabilities.md) and [session configuration file](session-configurations.md) created, the last step before you can use JEA is to register the JEA endpoint.</span></span>
<span data-ttu-id="4a1fc-106">시스템에 JEA 엔드포인트를 등록하면 사용자 및 자동화 엔진에서 엔드포인트를 사용할 수 있게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4a1fc-106">Registering the JEA endpoint with the system makes the endpoint available for use by users and automation engines.</span></span>

## <a name="single-machine-configuration"></a><span data-ttu-id="4a1fc-107">단일 컴퓨터 구성</span><span class="sxs-lookup"><span data-stu-id="4a1fc-107">Single machine configuration</span></span>

<span data-ttu-id="4a1fc-108">소규모 환경에서는 [Register-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/register-pssessionconfiguration) cmdlet을 사용해 세션 구성 파일을 등록하는 방법으로 JEA를 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4a1fc-108">For small environments, you can deploy JEA by registering the session configuration file using the [Register-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/register-pssessionconfiguration) cmdlet.</span></span>

<span data-ttu-id="4a1fc-109">시작하기 전에 다음과 같은 필수 조건을 충족했는지 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="4a1fc-109">Before you begin, ensure that the following prerequisites have been met:</span></span>
- <span data-ttu-id="4a1fc-110">하나 이상의 역할을 만들어 유효한 PowerShell 모듈의 'RoleCapabilities' 폴더에 배치했습니다.</span><span class="sxs-lookup"><span data-stu-id="4a1fc-110">One or more roles has been created and placed in the 'RoleCapabilities' folder of a valid PowerShell module.</span></span>
- <span data-ttu-id="4a1fc-111">세션 구성 파일을 만들고 테스트했습니다.</span><span class="sxs-lookup"><span data-stu-id="4a1fc-111">A session configuration file has been created and tested.</span></span>
- <span data-ttu-id="4a1fc-112">JEA 구성을 등록하는 사용자에게 시스템에 대한 관리자 권한이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4a1fc-112">The user registering the JEA configuration has administrator rights on the system(s).</span></span>

<span data-ttu-id="4a1fc-113">또한 JEA 엔드포인트의 이름을 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4a1fc-113">You also need to select a name for your JEA endpoint.</span></span>
<span data-ttu-id="4a1fc-114">사용자가 JEA를 사용하여 시스템에 연결하려고 할 경우 JEA 엔드포인트의 이름이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="4a1fc-114">The name of the JEA endpoint is required when users want to connect to the system using JEA.</span></span>
<span data-ttu-id="4a1fc-115">[Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet을 사용하여 시스템에 있는 기존 엔드포인트의 이름을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4a1fc-115">You can use the [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet to check the names of existing endpoints on the system.</span></span>
<span data-ttu-id="4a1fc-116">'microsoft'로 시작하는 엔드포인트는 일반적으로 Windows와 함께 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="4a1fc-116">Endpoints that start with 'microsoft' are typically shipped with Windows.</span></span>
<span data-ttu-id="4a1fc-117">'microsoft.powershell' 엔드포인트는 원격 PowerShell 엔드포인트에 연결할 때 사용되는 기본 엔드포인트입니다.</span><span class="sxs-lookup"><span data-stu-id="4a1fc-117">The 'microsoft.powershell' endpoint is the default endpoint used when connecting to a remote PowerShell endpoint.</span></span>

```powershell
PS C:\> Get-PSSessionConfiguration | Select-Object Name

Name
----
microsoft.powershell
microsoft.powershell.workflow
microsoft.powershell32
```

<span data-ttu-id="4a1fc-118">JEA 엔드포인트에 대한 적절한 이름을 결정했으면 다음 명령을 실행하여 엔드포인트를 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="4a1fc-118">When you have determined an appropriate name for your JEA endpoint, run the following command to register the endpoint.</span></span>

```powershell
Register-PSSessionConfiguration -Path .\MyJEAConfig.pssc -Name 'JEAMaintenance' -Force
```

> [!WARNING]
> <span data-ttu-id="4a1fc-119">위의 명령은 시스템에서 WinRM 서비스를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="4a1fc-119">The above command restarts the WinRM service on the system.</span></span>
> <span data-ttu-id="4a1fc-120">그러면 진행 중인 모든 DSC 구성뿐만 아니라 모든 PowerShell 원격 세션이 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="4a1fc-120">This terminates all PowerShell remoting sessions as well as any ongoing DSC configurations.</span></span>
> <span data-ttu-id="4a1fc-121">비즈니스 운영이 중단되지 않게 하려면 명령을 실행하기 전에 모든 프로덕션 컴퓨터를 오프라인 상태로 전환하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="4a1fc-121">It is recommended that you take any production machines offline before running the command to avoid disrupting business operations.</span></span>

<span data-ttu-id="4a1fc-122">등록에 성공하면 [JEA를 사용](using-jea.md)할 준비가 된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="4a1fc-122">If registration is successful, you are ready to [use JEA](using-jea.md).</span></span>
<span data-ttu-id="4a1fc-123">엔드포인트를 등록한 후에는 세션 구성 파일이 사용되지 않으므로 언제든지 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4a1fc-123">You may delete the session configuration file at any time; it is not used after registration of the end point.</span></span>

## <a name="multi-machine-configuration-with-dsc"></a><span data-ttu-id="4a1fc-124">DSC를 사용한 다중 컴퓨터 구성</span><span class="sxs-lookup"><span data-stu-id="4a1fc-124">Multi-machine configuration with DSC</span></span>

<span data-ttu-id="4a1fc-125">JEA를 여러 컴퓨터에 배포하는 경우 가장 간단한 배포 모델은 JEA [필요한 상태 구성](https://msdn.microsoft.com/powershell/dsc/overview) 리소스를 사용하여 각 컴퓨터에 신속하고 일관되게 JEA를 배포하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="4a1fc-125">If you are deploying JEA on multiple machines, the simplest deployment model is to use the JEA [Desired State Configuration](https://msdn.microsoft.com/powershell/dsc/overview) resource to quickly and consistently deploy JEA on each machine.</span></span>

<span data-ttu-id="4a1fc-126">DSC를 사용하여 JEA를 배포하려면 다음 필수 조건을 충족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4a1fc-126">To deploy JEA with DSC, you need to ensure the following prerequisites are met:</span></span>
- <span data-ttu-id="4a1fc-127">하나 이상의 역할 기능을 작성하여 유효한 PowerShell 모듈에 추가했습니다.</span><span class="sxs-lookup"><span data-stu-id="4a1fc-127">One or more role capabilities have been authored and added to a valid PowerShell module.</span></span>
- <span data-ttu-id="4a1fc-128">역할을 포함하는 PowerShell 모듈을 각 컴퓨터에서 액세스할 수 있는 (읽기 전용) 파일 공유에 저장했습니다.</span><span class="sxs-lookup"><span data-stu-id="4a1fc-128">The PowerShell module containing the roles is stored on a (read-only) file share accessible by each machine.</span></span>
- <span data-ttu-id="4a1fc-129">세션 구성에 대한 설정을 결정했습니다.</span><span class="sxs-lookup"><span data-stu-id="4a1fc-129">Settings for the session configuration have been determined.</span></span> <span data-ttu-id="4a1fc-130">JEA DSC 리소스를 사용하는 경우 세션 구성 파일을 만들 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4a1fc-130">You do not need to create a session configuration file when using the JEA DSC resource.</span></span>
- <span data-ttu-id="4a1fc-131">각 컴퓨터에서 관리 작업을 수행할 수 있는 자격 증명이 있거나, 컴퓨터를 관리하는 데 사용되는 DSC 끌어오기 서버에 대한 액세스 권한이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4a1fc-131">You have credentials that allow you to perform administrative actions on each machine, or have access to a DSC pull server used to manage the machines.</span></span>
- <span data-ttu-id="4a1fc-132">[JEA DSC resource](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource)(JEA DSC 리소스)를 다운로드했습니다.</span><span class="sxs-lookup"><span data-stu-id="4a1fc-132">You have downloaded the [JEA DSC resource](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource)</span></span>

<span data-ttu-id="4a1fc-133">대상 컴퓨터(또는 끌어오기 서버를 사용하는 경우 끌어오기 서버)에서 JEA 엔드포인트에 대한 DSC 구성을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4a1fc-133">On a target machine (or pull server, if you are using one), create a DSC configuration for your JEA endpoint.</span></span>
<span data-ttu-id="4a1fc-134">이 구성에서는 JustEnoughAdministration DSC 리소스를 사용하여 세션 구성 파일을 설정하고 File 리소스를 사용하여 파일 공유에서 역할 기능을 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="4a1fc-134">In this configuration, you use the JustEnoughAdministration DSC resource to set up the session configuration file and the File resource to copy over the role capabilities from the file share.</span></span>

<span data-ttu-id="4a1fc-135">DSC 리소스를 사용하여 다음 속성을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4a1fc-135">The following properties are configurable using the DSC resource:</span></span>
- <span data-ttu-id="4a1fc-136">역할 정의</span><span class="sxs-lookup"><span data-stu-id="4a1fc-136">Role Definitions</span></span>
- <span data-ttu-id="4a1fc-137">가상 계정 그룹</span><span class="sxs-lookup"><span data-stu-id="4a1fc-137">Virtual Account groups</span></span>
- <span data-ttu-id="4a1fc-138">그룹 관리 서비스 계정 이름</span><span class="sxs-lookup"><span data-stu-id="4a1fc-138">Group Managed Service Account name</span></span>
- <span data-ttu-id="4a1fc-139">기록 디렉터리</span><span class="sxs-lookup"><span data-stu-id="4a1fc-139">Transcript directory</span></span>
- <span data-ttu-id="4a1fc-140">사용자 드라이브</span><span class="sxs-lookup"><span data-stu-id="4a1fc-140">User drive</span></span>
- <span data-ttu-id="4a1fc-141">조건부 액세스 규칙</span><span class="sxs-lookup"><span data-stu-id="4a1fc-141">Conditional access rules</span></span>
- <span data-ttu-id="4a1fc-142">JEA 세션에 대한 시작 스크립트</span><span class="sxs-lookup"><span data-stu-id="4a1fc-142">Startup scripts for the JEA session</span></span>

<span data-ttu-id="4a1fc-143">DSC 구성에서 이러한 각 속성에 대한 구문은 PowerShell 세션 구성 파일과 일치합니다.</span><span class="sxs-lookup"><span data-stu-id="4a1fc-143">The syntax for each of these properties in a DSC configuration is consistent with the PowerShell session configuration file.</span></span>

<span data-ttu-id="4a1fc-144">다음은 일반 서버 유지 관리 모듈에 대한 샘플 DSC 구성입니다.</span><span class="sxs-lookup"><span data-stu-id="4a1fc-144">Below is a sample DSC configuration for a general server maintenance module.</span></span>

<span data-ttu-id="4a1fc-145">여기서는 'RoleCapabilities' 하위 폴더의 역할 기능을 포함하는 유효한 PowerShell 모듈이 '\\\\myfileshare\\JEA' 파일 공유에 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="4a1fc-145">It assumes that a valid PowerShell module containing role capabilities in a 'RoleCapabilities' subfolder is located on the '\\\\myfileshare\\JEA' file share.</span></span>


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

<span data-ttu-id="4a1fc-146">그러면 [직접 로컬 구성 관리자를 호출](https://msdn.microsoft.com/powershell/dsc/metaconfig)하거나 [가져오기 서버 구성](https://msdn.microsoft.com/powershell/dsc/pullserver)을 업데이트하여 시스템에 이 구성을 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4a1fc-146">This configuration can then be applied on a system by [directly invoking the Local Configuration Manager](https://msdn.microsoft.com/powershell/dsc/metaconfig) or updating the [pull server configuration](https://msdn.microsoft.com/powershell/dsc/pullserver).</span></span>

<span data-ttu-id="4a1fc-147">DSC 리소스를 사용하여 기본 Microsoft.PowerShell 원격 엔드포인트를 바꿀 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4a1fc-147">The DSC resource also allows you to replace the default Microsoft.PowerShell remoting endpoint.</span></span>
<span data-ttu-id="4a1fc-148">이렇게 하면 리소스가 기본 WinRM ACL을 포함한 "Microsoft.PowerShell.Restricted"라는 백업 비제한 엔드포인트를 자동으로 등록합니다(원격 관리 사용자 및 로컬 관리자 그룹 멤버가 여기에 액세스하도록 허용함).</span><span class="sxs-lookup"><span data-stu-id="4a1fc-148">If you do this, the resource automatically registers a backup unconstrained endpoint named "Microsoft.PowerShell.Restricted" which has the default WinRM ACL (allowing Remote Management Users and local Administrators group members to access it).</span></span>

## <a name="unregistering-jea-configurations"></a><span data-ttu-id="4a1fc-149">JEA 구성 등록 취소</span><span class="sxs-lookup"><span data-stu-id="4a1fc-149">Unregistering JEA configurations</span></span>

<span data-ttu-id="4a1fc-150">시스템에서 JEA 엔드포인트를 제거하려면 [Unregister-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Unregister-PSSessionConfiguration) cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4a1fc-150">To remove a JEA endpoint on a system, use the [Unregister-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Unregister-PSSessionConfiguration) cmdlet.</span></span>
<span data-ttu-id="4a1fc-151">JEA 엔드포인트를 등록 취소하면 새 사용자가 시스템에서 새 JEA 세션을 만들지 못합니다.</span><span class="sxs-lookup"><span data-stu-id="4a1fc-151">Unregistering a JEA endpoint prevents new users from creating new JEA sessions on the system.</span></span>
<span data-ttu-id="4a1fc-152">같은 엔드포인트 이름을 사용하여 업데이트된 세션 구성 파일을 다시 등록하는 방법으로 JEA 구성을 업데이트할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4a1fc-152">It also allows you to update a JEA configuration by re-registering an updated session configuration file using the same endpoint name.</span></span>

```powershell
# Unregister the JEA endpoint called "ContosoMaintenance"
Unregister-PSSessionConfiguration -Name 'ContosoMaintenance' -Force
```

> [!WARNING]
> <span data-ttu-id="4a1fc-153">JEA 엔드포인트를 등록 취소하면 WinRM 서비스가 다시 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="4a1fc-153">Unregistering a JEA endpoint causes the WinRM service to restart.</span></span>
> <span data-ttu-id="4a1fc-154">그러면 다른 PowerShell 세션, WMI 호출 및 일부 관리 도구를 비롯한 진행 중인 대부분의 원격 관리 작업이 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="4a1fc-154">This interrupts most remote management operations in progress, including other PowerShell sessions, WMI invocations, and some management tools.</span></span>
> <span data-ttu-id="4a1fc-155">계획된 유지 관리 기간에는 PowerShell 엔드포인트만 등록 취소하세요.</span><span class="sxs-lookup"><span data-stu-id="4a1fc-155">Only unregister PowerShell endpoints during planned maintenance windows.</span></span>

## <a name="next-steps"></a><span data-ttu-id="4a1fc-156">다음 단계</span><span class="sxs-lookup"><span data-stu-id="4a1fc-156">Next steps</span></span>

- [<span data-ttu-id="4a1fc-157">JEA 엔드포인트 테스트</span><span class="sxs-lookup"><span data-stu-id="4a1fc-157">Test the JEA endpoint</span></span>](using-jea.md)
