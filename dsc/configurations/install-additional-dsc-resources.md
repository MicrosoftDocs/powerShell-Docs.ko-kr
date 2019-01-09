---
ms.date: 12/12/2018
keywords: dsc, powershell, 리소스, 갤러리, 설치
title: 추가 DSC 리소스 설치
ms.openlocfilehash: ecaf176230ccd934b57b1c27d72ff83e6ba906e9
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402908"
---
# <a name="install-additional-dsc-resources"></a><span data-ttu-id="6ee9d-103">추가 DSC 리소스 설치</span><span class="sxs-lookup"><span data-stu-id="6ee9d-103">Install Additional DSC Resources</span></span>

<span data-ttu-id="6ee9d-104">PowerShell Desired State Configuration (DSC)에 대 한 몇 가지 기본 제공 리소스를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="6ee9d-104">PowerShell includes several Out-of-the-box resources for Desired State Configuration (DSC).</span></span> <span data-ttu-id="6ee9d-105">합니다 **PSDesiredStateConfiguration** 모듈 PowerShell의 특정 인스턴스에서 사용 가능한 OOB DSC 리소스를 모두 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ee9d-105">The **PSDesiredStateConfiguration** module contains all of the OOB DSC resources available on your specific instance of PowerShell.</span></span>

<span data-ttu-id="6ee9d-106">PowerShell 4.0 및 리소스의 기능에 대 한 설명을 포함 된 OOB 리소스의 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="6ee9d-106">This is a list of the OOB resources included in PowerShell 4.0 and a description of the resource's capabilities.</span></span>

> [!NOTE]
> <span data-ttu-id="6ee9d-107">각 버전의 PowerShell 사용 하 여 OOB 리소스 수가 늘어날수록는 불완전 한 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="6ee9d-107">This is an incomplete list, as the number of OOB resources has grown with each version of PowerShell.</span></span>

|<span data-ttu-id="6ee9d-108">리소스</span><span class="sxs-lookup"><span data-stu-id="6ee9d-108">Resource</span></span>  |<span data-ttu-id="6ee9d-109">설명</span><span class="sxs-lookup"><span data-stu-id="6ee9d-109">Description</span></span>  |
|---------|---------|
|<span data-ttu-id="6ee9d-110">**File**</span><span class="sxs-lookup"><span data-stu-id="6ee9d-110">**File**</span></span>|<span data-ttu-id="6ee9d-111">파일 및 디렉터리의 상태를 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="6ee9d-111">Controls the state of files and directories.</span></span> <span data-ttu-id="6ee9d-112">파일을 복사를 **원본** 에 **대상** 업데이트 하 고 때를 **원본** 날짜, 체크섬을 및 해시를 비교 하 여 변경 내용을.</span><span class="sxs-lookup"><span data-stu-id="6ee9d-112">Copies files from a **Source** to a **Destination** and updates them when the **Source** changes by comparing dates, checksums, and hashes.</span></span>|
|<span data-ttu-id="6ee9d-113">**Archive**</span><span class="sxs-lookup"><span data-stu-id="6ee9d-113">**Archive**</span></span>|<span data-ttu-id="6ee9d-114">지정된 된 위치 및 보관 압축을 풉니다.</span><span class="sxs-lookup"><span data-stu-id="6ee9d-114">Unpacks archives and a specified location.</span></span> <span data-ttu-id="6ee9d-115">지정 된 보관의 유효성을 검사 **체크섬**합니다.</span><span class="sxs-lookup"><span data-stu-id="6ee9d-115">Validates the archives with a specified **Checksum**.</span></span>|
|<span data-ttu-id="6ee9d-116">**Environment**</span><span class="sxs-lookup"><span data-stu-id="6ee9d-116">**Environment**</span></span>|<span data-ttu-id="6ee9d-117">환경 변수를 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ee9d-117">Manages environment variables.</span></span>|
|<span data-ttu-id="6ee9d-118">**그룹**</span><span class="sxs-lookup"><span data-stu-id="6ee9d-118">**Group**</span></span>|<span data-ttu-id="6ee9d-119">로컬 그룹을 관리 하 고 그룹 멤버 자격을 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ee9d-119">Manages local groups and controls group membership.</span></span>|
|<span data-ttu-id="6ee9d-120">**Log**</span><span class="sxs-lookup"><span data-stu-id="6ee9d-120">**Log**</span></span>|<span data-ttu-id="6ee9d-121">메시지를 기록 합니다 `Microsoft-Windows-Desired State Configuration/Analytic` 이벤트 로그입니다.</span><span class="sxs-lookup"><span data-stu-id="6ee9d-121">Writes messages to the `Microsoft-Windows-Desired State Configuration/Analytic` event log.</span></span>|
|<span data-ttu-id="6ee9d-122">**패키지**</span><span class="sxs-lookup"><span data-stu-id="6ee9d-122">**Package**</span></span>|<span data-ttu-id="6ee9d-123">설치 하거나 사용 하 여 패키지를 제거 **인수**, **LogPath**를 **ReturnCode**, 기타 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ee9d-123">Installs or uninstalls packages using **Arguments**, **LogPath**, **ReturnCode**, other settings.</span></span>|
|<span data-ttu-id="6ee9d-124">**Registry**</span><span class="sxs-lookup"><span data-stu-id="6ee9d-124">**Registry**</span></span>|<span data-ttu-id="6ee9d-125">레지스트리 키와 값을 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="6ee9d-125">Manages registry keys and values.</span></span>|
|<span data-ttu-id="6ee9d-126">**Script**</span><span class="sxs-lookup"><span data-stu-id="6ee9d-126">**Script**</span></span>|<span data-ttu-id="6ee9d-127">사용 하면 디자인을 사용자 고유의 [get-테스트-집합](../resources/get-test-set.md) 스크립트 블록입니다.</span><span class="sxs-lookup"><span data-stu-id="6ee9d-127">Allows you to design your own [get-test-set](../resources/get-test-set.md) script blocks.</span></span>|
|<span data-ttu-id="6ee9d-128">**Service**</span><span class="sxs-lookup"><span data-stu-id="6ee9d-128">**Service**</span></span>|<span data-ttu-id="6ee9d-129">Windows 서비스를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="6ee9d-129">Configures Windows services.</span></span>|
|<span data-ttu-id="6ee9d-130">**User**</span><span class="sxs-lookup"><span data-stu-id="6ee9d-130">**User**</span></span> |<span data-ttu-id="6ee9d-131">로컬 사용자 및 특성을 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="6ee9d-131">Manages local users and attributes.</span></span>|
|<span data-ttu-id="6ee9d-132">**WindowsFeature**</span><span class="sxs-lookup"><span data-stu-id="6ee9d-132">**WindowsFeature**</span></span>|<span data-ttu-id="6ee9d-133">역할 및 기능을 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="6ee9d-133">Manages roles and features.</span></span>|
|<span data-ttu-id="6ee9d-134">**WindowsProcess**</span><span class="sxs-lookup"><span data-stu-id="6ee9d-134">**WindowsProcess**</span></span>|<span data-ttu-id="6ee9d-135">Windows 프로세스를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="6ee9d-135">Configures Windows processes.</span></span>|

<span data-ttu-id="6ee9d-136">OOB 리소스 일반적인 작업을 위한 좋은 출발점을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ee9d-136">The OOB resources allow a good starting point for common operations.</span></span> <span data-ttu-id="6ee9d-137">OOB 리소스 요구를 충족 하지 않으면 작성할 수 있습니다 고유한 [사용자 지정 리소스](../resources/authoringResource.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="6ee9d-137">If the OOB resources do not meet your needs, you can write your own [Custom Resource](../resources/authoringResource.md).</span></span> <span data-ttu-id="6ee9d-138">문제를 해결 하기 위해 사용자 지정 리소스를 작성 하기 전에 다양 한 Microsoft와 PowerShell 커뮤니티에서 이미 만들어져 있는 DSC 리소스를 통해 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ee9d-138">Before you write a custom resource to solve your problem, you should look through the vast number of DSC resources that have already been created by both Microsoft and the PowerShell community.</span></span>

<span data-ttu-id="6ee9d-139">둘 다에서 DSC 리소스를 찾을 수 있습니다 합니다 [PowerShell 갤러리](https://www.powershellgallery.com/) 하 고 [GitHub](https://github.com/)합니다.</span><span class="sxs-lookup"><span data-stu-id="6ee9d-139">You can find DSC resources in both the [PowerShell Gallery](https://www.powershellgallery.com/) and [GitHub](https://github.com/).</span></span> <span data-ttu-id="6ee9d-140">DSC 리소스를 사용 하 여 PowerShell 콘솔에서 직접 설치할 수도 있습니다 [PowerShellGet](/powershell/module/powershellget/)합니다.</span><span class="sxs-lookup"><span data-stu-id="6ee9d-140">You can also install DSC resources directly from the PowerShell console using [PowerShellGet](/powershell/module/powershellget/).</span></span>

## <a name="installing-powershellget"></a><span data-ttu-id="6ee9d-141">PowerShellGet 설치</span><span class="sxs-lookup"><span data-stu-id="6ee9d-141">Installing PowerShellGet</span></span>

<span data-ttu-id="6ee9d-142">이미 있는 경우 결정할 **PowerShell** 가져오기 또는 설치 도움말을 보려면 다음 가이드를 참조 하십시오. [PowerShellGet 설치](/powershell/gallery/installing-psget)</span><span class="sxs-lookup"><span data-stu-id="6ee9d-142">To determine if you already have **PowerShell** get, or to get help installing it, see the following guide: [Installing PowerShellGet](/powershell/gallery/installing-psget).</span></span>

## <a name="finding-dsc-resources-using-powershellget"></a><span data-ttu-id="6ee9d-143">PowerShellGet을 사용 하 여 DSC 리소스 찾기</span><span class="sxs-lookup"><span data-stu-id="6ee9d-143">Finding DSC resources using PowerShellGet</span></span>

<span data-ttu-id="6ee9d-144">한 번 **PowerShellGet** 되어 시스템에서 찾을 고에서 호스팅되는 DSC 리소스를 설치할 수 있습니다 합니다 [PowerShell 갤러리](https://www.powershellgallery.com/)합니다.</span><span class="sxs-lookup"><span data-stu-id="6ee9d-144">Once **PowerShellGet** is installed on your system, you can find and install DSC resources hosted in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>

<span data-ttu-id="6ee9d-145">먼저 사용 하 여 합니다 [Find-dscresource](/powershell/module/powershellget/find-dscresource) cmdlet DSC 리소스를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ee9d-145">First, use the [Find-DSCResource](/powershell/module/powershellget/find-dscresource) cmdlet to find DSC resources.</span></span> <span data-ttu-id="6ee9d-146">실행할 때 `Find-DSCResource` 처음으로 "NuGet 공급자"를 설치 하려면 다음과 같은 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6ee9d-146">When you run `Find-DSCResource` for the first time, you see the following prompt to install the "NuGet provider".</span></span>

```
PS> Find-DSCResource

NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based repositories. The
NuGet provider must be available in 'C:\Program Files\PackageManagement\ProviderAssemblies' or
'C:\Users\xAdministrator\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet provider
 by running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to
install and import the NuGet provider now?
[Y] Yes  [N] No  [?] Help (default is "Y"):
```

<span data-ttu-id="6ee9d-147">키를 눌러 'y' 후 "NuGet" 공급자가 설치 되어, PowerShell 갤러리에서 설치할 수 있는 DSC 리소스의 목록을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ee9d-147">After pressing 'y', the "NuGet" provider is installed, you see a list of DSC resources that you can install from the PowerShell Gallery.</span></span>

> [!NOTE]
> <span data-ttu-id="6ee9d-148">목록에는 매우 큰 이기 때문에 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6ee9d-148">List is not shown because it is very large.</span></span>

<span data-ttu-id="6ee9d-149">지정할 수도 있습니다는 `-Name` 와일드 카드를 사용 하 여 매개 변수 또는 `-Filter` 검색 범위를 좁힐에 와일드 카드 없이 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="6ee9d-149">You can also specify the `-Name` parameter using wildcards, or `-Filter` parameter without wildcards to narrow down your search.</span></span> <span data-ttu-id="6ee9d-150">이 예제에서는 와일드 카드를 사용 하 여 "시간대" DSC 리소스를 찾으려고 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ee9d-150">This example attempts to find a "TimeZone" DSC resource using the wildcards.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6ee9d-151">현재는의 버그를 `Find-DSCResource` 둘 다에 와일드 카드 사용을 방지 하는 cmdlet의 `-Name` 및 `-Filter` 매개 변수.</span><span class="sxs-lookup"><span data-stu-id="6ee9d-151">Currently there is a bug in the `Find-DSCResource` cmdlet that prevents using wildcards in both the `-Name` and `-Filter` parameters.</span></span> <span data-ttu-id="6ee9d-152">아래 두 번째 예제에서는 사용 하 여 해결 방법을 보여 줍니다. `Where-Object`합니다.</span><span class="sxs-lookup"><span data-stu-id="6ee9d-152">The second example below shows a workaround using `Where-Object`.</span></span>

```
PS> Find-DSCResource -Name *Time*

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
Carbon_EnvironmentVariable          2.6.0      Carbon                              PSGallery
Carbon_FirewallRule                 2.6.0      Carbon                              PSGallery
Carbon_Group                        2.6.0      Carbon                              PSGallery
Carbon_IniFile                      2.6.0      Carbon                              PSGallery
Carbon_Permission                   2.6.0      Carbon                              PSGallery
Carbon_Privilege                    2.6.0      Carbon                              PSGallery
Carbon_ScheduledTask                2.6.0      Carbon                              PSGallery
Carbon_Service                      2.6.0      Carbon                              PSGallery
TimeZone                            6.0.0.0    ComputerManagementDsc               PSGallery
xTimeZone                           1.8.0.0    xTimeZone                           PSGallery
xSqlServerDefaultDir                1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerMoveDatabaseFiles         1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerSQLDataRoot               1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerStartupParam              1.0.0      mlSqlServerDSC                      PSGallery
```

<span data-ttu-id="6ee9d-153">사용할 수도 있습니다 `Where-Object` 보다 세분화 된 필터링 된 DSC 리소스를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ee9d-153">You can also use `Where-Object` to find DSC resources with more granular filtering.</span></span> <span data-ttu-id="6ee9d-154">이 방법은 기본 제공 매개 변수 필터링을 사용 하 여 보다 낮아집니다.</span><span class="sxs-lookup"><span data-stu-id="6ee9d-154">This approach will be slower than using built in filtering parameters.</span></span>

```
PS> Find-DSCResource | Where-Object {$_.Name -like "Time*"}

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
TimeZone                            6.0.0.0    ComputerManagementDsc               PSGallery
```

<span data-ttu-id="6ee9d-155">필터링에 대 한 자세한 내용은 참조 하세요. [Where-object](/powershell/module/microsoft.powershell.core/where-object)합니다.</span><span class="sxs-lookup"><span data-stu-id="6ee9d-155">For more information on filtering, see [Where-Object](/powershell/module/microsoft.powershell.core/where-object).</span></span>

## <a name="installing-dsc-resources-using-powershellget"></a><span data-ttu-id="6ee9d-156">PowerShellGet을 사용 하 여 DSC 리소스를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ee9d-156">Installing DSC Resources using PowerShellGet</span></span>

<span data-ttu-id="6ee9d-157">DSC 리소스를 설치 하려면 사용 합니다 [Install-module](/powershell/module/PowershellGet/Install-Module) cmdlet을 아래에 표시 된 모듈의 이름을 지정 하 **모듈** 검색 결과의 이름.</span><span class="sxs-lookup"><span data-stu-id="6ee9d-157">To install a DSC resource, use the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet, specifying the name of the module shown under **Module** name in your search results.</span></span>

<span data-ttu-id="6ee9d-158">"시간대" 리소스 이므로 즉 모듈이 예제 설치 "ComputerManagementDSC" 모듈에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ee9d-158">The "TimeZone" resource exists in the "ComputerManagementDSC" module, so that is the module this example installs.</span></span>

> [!NOTE]
> <span data-ttu-id="6ee9d-159">PowerShell 갤러리를 신뢰할 수 있는 경우 확인을 묻는 아래 경고를 표시 하 고 설치에서 후속 프롬프트를 방지 하는 방법 하도록 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ee9d-159">If you have not trusted the PowerShell gallery, you see the warning below asking for confirmation, and instructing you how to avoid subsequent prompts on installs.</span></span>

```
PS> Install-Module -Name ComputerManagementDSC

Untrusted repository
You are installing the modules from an untrusted repository. If you trust this repository, change its
InstallationPolicy value by running the Set-PSRepository cmdlet. Are you sure you want to install the modules from
'PSGallery'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

<span data-ttu-id="6ee9d-160">모듈 설치를 계속 하려면 ' y'를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="6ee9d-160">Press 'y' to continue installing the module.</span></span> <span data-ttu-id="6ee9d-161">설치 후 확인할 수 있습니다 새 리소스를 사용 하 여이 설치 되어 있는지 [Get-dscresource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)합니다.</span><span class="sxs-lookup"><span data-stu-id="6ee9d-161">After install, you can verify that your new resource is installed using [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource).</span></span>

```
PS> Get-DSCResource -Name TimeZone -Syntax

TimeZone [String] #ResourceName
{
    IsSingleInstance = [string]{ Yes }
    TimeZone = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
}
```

<span data-ttu-id="6ee9d-162">지정 하 여 새로 설치 된 모듈의 다른 리소스를 볼 수도 있습니다는 `-ModuleName` 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="6ee9d-162">You can also view other resources in your newly installed module, by specifying the `-ModuleName` parameter.</span></span>

```
PS> Get-DSCResource -Module ComputerManagementDSC

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      Computer                  ComputerManagementDsc          6.0.0.0    {Name, Credential, DependsOn, ...
PowerShell      OfflineDomainJoin         ComputerManagementDsc          6.0.0.0    {IsSingleInstance, RequestFile...
PowerShell      PowerPlan                 ComputerManagementDsc          6.0.0.0    {IsSingleInstance, Name, Depen...
PowerShell      PowerShellExecutionPolicy ComputerManagementDsc          6.0.0.0    {ExecutionPolicy, ExecutionPol...
PowerShell      ScheduledTask             ComputerManagementDsc          6.0.0.0    {TaskName, ActionArguments, Ac...
PowerShell      TimeZone                  ComputerManagementDsc          6.0.0.0    {IsSingleInstance, TimeZone, D...
PowerShell      VirtualMemory             ComputerManagementDsc          6.0.0.0    {Drive, Type, DependsOn, Initi...
```

## <a name="see-also"></a><span data-ttu-id="6ee9d-163">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6ee9d-163">See also</span></span>

- [<span data-ttu-id="6ee9d-164">리소스란?</span><span class="sxs-lookup"><span data-stu-id="6ee9d-164">What are Resources?</span></span>](../resources/resources.md)
