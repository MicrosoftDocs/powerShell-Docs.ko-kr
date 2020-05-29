---
ms.date: 02/28/2020
keywords: dsc,powershell,configuration,setup
title: DSC 리소스
ms.openlocfilehash: bae08447763a3bdb6ee8fcdd4f8d49209a5de805
ms.sourcegitcommit: 17d798a041851382b406ed789097843faf37692d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83692208"
---
# <a name="dsc-resources"></a><span data-ttu-id="85980-103">DSC 리소스</span><span class="sxs-lookup"><span data-stu-id="85980-103">DSC Resources</span></span>

> <span data-ttu-id="85980-104">적용 대상: Windows PowerShell 4.0 이상</span><span class="sxs-lookup"><span data-stu-id="85980-104">Applies to Windows PowerShell 4.0 and up.</span></span>

## <a name="overview"></a><span data-ttu-id="85980-105">개요</span><span class="sxs-lookup"><span data-stu-id="85980-105">Overview</span></span>

<span data-ttu-id="85980-106">DSC(필요한 상태 구성) 리소스에서는 DSC 구성에 대한 구성 요소를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="85980-106">Desired State Configuration (DSC) Resources provide the building blocks for a DSC configuration.</span></span> <span data-ttu-id="85980-107">리소스는 구성할 수 있는 속성(스키마)을 노출하고 LCM(로컬 구성 관리자)이 "그대로 수행"하기 위해 호출하는 PowerShell 스크립트 함수를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="85980-107">A resource exposes properties that can be configured (schema) and contains the PowerShell script functions that the Local Configuration Manager (LCM) calls to "make it so".</span></span>

<span data-ttu-id="85980-108">리소스는 파일만큼 일반적이거나 IIS 서버만큼 특별한 것을 모델링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85980-108">A resource can model something as generic as a file or as specific as an IIS server setting.</span></span> <span data-ttu-id="85980-109">같은 리소스들의 그룹은 모든 필수 파일을 이식 가능한 구조로 정리하고, 리소스를 사용하려고 한 방법을 식별하는 메타데이터를 포함하는 DSC 모듈에 결합됩니다.</span><span class="sxs-lookup"><span data-stu-id="85980-109">Groups of like resources are combined in to a DSC Module, which organizes all the required files in to a structure that is portable and includes metadata to identify how the resources are intended to be used.</span></span>

<span data-ttu-id="85980-110">각 리소스에는 [구성](../configurations/configurations.md)에서 리소스를 사용하는 데 필요한 구문을 결정하는 \*스키마가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85980-110">Each resource has a \*schema that determines the syntax needed to use the resource in a [Configuration](../configurations/configurations.md).</span></span>
<span data-ttu-id="85980-111">리소스 스키마는 다음 방법으로 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85980-111">A resource's schema can be defined in the following ways:</span></span>

- <span data-ttu-id="85980-112">`Schema.Mof` 파일: 대부분의 리소스는 [Managed Object Format](/windows/desktop/wmisdk/managed-object-format--mof-)을 사용하여 'schema.mof' 파일에서 해당 ‘스키마’를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="85980-112">`Schema.Mof` file: Most resources define their _schema_ in a 'schema.mof' file, using [Managed Object Format](/windows/desktop/wmisdk/managed-object-format--mof-).</span></span>
- <span data-ttu-id="85980-113">`<Resource Name>.schema.psm1`파일: [복합 리소스](../configurations/compositeConfigs.md)는 [매개 변수 블록](/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-6#functions-with-parameters)을 사용하여 `<ResourceName>.schema.psm1` 파일에서 해당 ‘스키마’를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="85980-113">`<Resource Name>.schema.psm1` file: [Composite Resources](../configurations/compositeConfigs.md) define their *schema* in a `<ResourceName>.schema.psm1` file using a [Parameter Block](/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-6#functions-with-parameters).</span></span>
- <span data-ttu-id="85980-114">`<Resource Name>.psm1` 파일: 클래스 기반 DSC 리소스는 클래스 정의에서 해당 ‘스키마’를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="85980-114">`<Resource Name>.psm1` file: Class based DSC resources define their _schema_ in the class definition.</span></span> <span data-ttu-id="85980-115">구문 항목은 클래스 속성으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="85980-115">Syntax items are denoted as Class properties.</span></span> <span data-ttu-id="85980-116">자세한 내용은 [about_Classes](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="85980-116">For more information, see [about_Classes](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc).</span></span>

<span data-ttu-id="85980-117">DSC 리소스의 구문을 검색하려면 [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet과 함께 `-Syntax` 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="85980-117">To retrieve the syntax for a DSC resource, use the [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet with the `-Syntax` parameter.</span></span> <span data-ttu-id="85980-118">이 사용법은 [Get-Command](/powershell/module/microsoft.powershell.core/get-command)와 함께 `-Syntax` 매개 변수를 사용하여 cmdlet 구문을 가져오는 것과 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="85980-118">This usage is similar to using [Get-Command](/powershell/module/microsoft.powershell.core/get-command) with the `-Syntax` parameter to get cmdlet syntax.</span></span> <span data-ttu-id="85980-119">표시되는 출력은 지정하는 리소스의 리소스 블록에 사용되는 템플릿을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="85980-119">The output you see will show the template used for a resource block for the resource you specify.</span></span>

```powershell
Get-DscResource -Syntax Service
```

<span data-ttu-id="85980-120">표시되는 출력은 아래 출력과 비슷하지만, 이 리소스의 구문은 나중에 변경될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85980-120">The output you see should be similar to the output below, though this resource's syntax could change in the future.</span></span> <span data-ttu-id="85980-121">cmdlet 구문과 같이 대괄호 안에 표시되는 ‘키’는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="85980-121">Like cmdlet syntax, the _keys_ seen in square brackets, are optional.</span></span> <span data-ttu-id="85980-122">형식은 각 키에 필요한 데이터 형식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="85980-122">The types specify the type of data each key expects.</span></span>

> [!NOTE]
> <span data-ttu-id="85980-123">**Ensure** 키는 기본적으로 "Present"로 설정되므로 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="85980-123">The **Ensure** key is optional because it defaults to "Present".</span></span>

```output
Service [String] #ResourceName
{
    Name = [string]
    [BuiltInAccount = [string]{ LocalService | LocalSystem | NetworkService }]
    [Credential = [PSCredential]]
    [Dependencies = [string[]]]
    [DependsOn = [string[]]]
    [Description = [string]]
    [DisplayName = [string]]
    [Ensure = [string]{ Absent | Present }]
    [Path = [string]]
    [PsDscRunAsCredential = [PSCredential]]
    [StartupType = [string]{ Automatic | Disabled | Manual }]
    [State = [string]{ Running | Stopped }]
}
```

<span data-ttu-id="85980-124">구성 내부에 있는 **Service** 리소스 블록은 Spooler 서비스가 실행 중인지 **확인**하기 위해 이와 같이 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85980-124">Inside a Configuration, a **Service** resource block might look like this to **Ensure** that the Spooler service is running.</span></span>

> [!NOTE]
> <span data-ttu-id="85980-125">구성에서 리소스를 사용하기 전에 [Import-DSCResource](../configurations/import-dscresource.md)를 사용하여 리소스를 가져와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="85980-125">Before using a resource in a Configuration, you must import it using [Import-DSCResource](../configurations/import-dscresource.md).</span></span>

```powershell
Configuration TestConfig
{
    # It is best practice to always directly import resources, even if the resource is a built-in resource.
    Import-DSCResource -Name Service
    Node localhost
    {
        # The name of this resource block, can be anything you choose, as long as it is of type [String] as indicated by the schema.
        Service "Spooler:Running"
        {
            Name = "Spooler"
            State = "Running"
        }
    }
}
```

<span data-ttu-id="85980-126">구성에는 동일한 리소스 종류의 여러 인스턴스가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85980-126">Configurations can contain multiple instances of the same resource type.</span></span> <span data-ttu-id="85980-127">각 인스턴스의 이름은 고유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="85980-127">Each instance must be uniquely named.</span></span> <span data-ttu-id="85980-128">다음 예제에서는 "DHCP" 서비스를 구성하는 두 번째 **Service** 리소스 블록이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="85980-128">In the following example, a second **Service** resource block is added to configure the "DHCP" service.</span></span>

```powershell
Configuration TestConfig
{
    # It is best practice to always directly import resources, even if the resource is a built-in resource.
    Import-DSCResource -Name Service
    Node localhost
    {
        # The name of this resource block, can be anything you choose, as long as it is of type [String] as indicated by the schema.
        Service "Spooler:Running"
        {
            Name = "Spooler"
            State = "Running"
        }

        # To configure a second service resource block, add another Service resource block and use a unique name.
        Service "DHCP:Running"
        {
            Name = "DHCP"
            State = "Running"
        }
    }
}
```

> [!NOTE]
> <span data-ttu-id="85980-129">PowerShell 5.0부터, IntelliSense가 DSC용으로 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="85980-129">Beginning in PowerShell 5.0, intellisense was added for DSC.</span></span> <span data-ttu-id="85980-130">이 새로운 기능을 통해 <kbd>TAB</kbd> 및 <kbd>Ctr</kbd>+<kbd>Space</kbd> 를 사용하여 키 이름을 자동 완성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85980-130">This new feature allows you to use <kbd>TAB</kbd> and <kbd>Ctr</kbd>+<kbd>Space</kbd> to auto-complete key names.</span></span>

![리소스 탭 완성](media/resources/resource-tabcompletion.png)

## <a name="types-of-resources"></a><span data-ttu-id="85980-132">리소스 유형</span><span class="sxs-lookup"><span data-stu-id="85980-132">Types of resources</span></span>

<span data-ttu-id="85980-133">Windows에는 기본 제공 리소스가 제공되며 Linux에는 OS 관련 리소스가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85980-133">Windows comes with built in resources and Linux has OS specific resources.</span></span> <span data-ttu-id="85980-134">[노드 간 종속성](../configurations/crossNodeDependencies.md) 리소스, 패키지 관리 리소스뿐만 아니라 [커뮤니티 소유 및 유지 관리 리소스](https://github.com/dsccommunity)도 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="85980-134">There are resources for [cross-node dependencies](../configurations/crossNodeDependencies.md), package management resources, as well as[community owned and maintained resources](https://github.com/dsccommunity).</span></span> <span data-ttu-id="85980-135">위의 단계를 사용하여 이 리소스의 구문 및 리소스 사용 방법을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85980-135">You can use the above steps to determine the syntax of these resources and how to use them.</span></span> <span data-ttu-id="85980-136">이 리소스를 제공하는 페이지는 **참조**아래에 보관되었습니다.</span><span class="sxs-lookup"><span data-stu-id="85980-136">The pages that serve these resources have been archived under **Reference**.</span></span>

### <a name="windows-built-in-resources"></a><span data-ttu-id="85980-137">Windows 기본 제공 리소스</span><span class="sxs-lookup"><span data-stu-id="85980-137">Windows built-in resources</span></span>

- [<span data-ttu-id="85980-138">보관 리소스</span><span class="sxs-lookup"><span data-stu-id="85980-138">Archive Resource</span></span>](../reference/resources/windows/archiveResource.md)
- [<span data-ttu-id="85980-139">환경 리소스</span><span class="sxs-lookup"><span data-stu-id="85980-139">Environment Resource</span></span>](../reference/resources/windows/environmentResource.md)
- [<span data-ttu-id="85980-140">파일 리소스</span><span class="sxs-lookup"><span data-stu-id="85980-140">File Resource</span></span>](../reference/resources/windows/fileResource.md)
- [<span data-ttu-id="85980-141">그룹 리소스</span><span class="sxs-lookup"><span data-stu-id="85980-141">Group Resource</span></span>](../reference/resources/windows/groupResource.md)
- [<span data-ttu-id="85980-142">GroupSet 리소스</span><span class="sxs-lookup"><span data-stu-id="85980-142">GroupSet Resource</span></span>](../reference/resources/windows/groupSetResource.md)
- [<span data-ttu-id="85980-143">로그 리소스</span><span class="sxs-lookup"><span data-stu-id="85980-143">Log Resource</span></span>](../reference/resources/windows/logResource.md)
- [<span data-ttu-id="85980-144">패키지 리소스</span><span class="sxs-lookup"><span data-stu-id="85980-144">Package Resource</span></span>](../reference/resources/windows/packageResource.md)
- [<span data-ttu-id="85980-145">ProcessSet 리소스</span><span class="sxs-lookup"><span data-stu-id="85980-145">ProcessSet Resource</span></span>](../reference/resources/windows/ProcessSetResource.md)
- [<span data-ttu-id="85980-146">레지스트리 리소스</span><span class="sxs-lookup"><span data-stu-id="85980-146">Registry Resource</span></span>](../reference/resources/windows/registryResource.md)
- [<span data-ttu-id="85980-147">스크립트 리소스</span><span class="sxs-lookup"><span data-stu-id="85980-147">Script Resource</span></span>](../reference/resources/windows/scriptResource.md)
- [<span data-ttu-id="85980-148">서비스 리소스</span><span class="sxs-lookup"><span data-stu-id="85980-148">Service Resource</span></span>](../reference/resources/windows/serviceResource.md)
- [<span data-ttu-id="85980-149">ServiceSet 리소스</span><span class="sxs-lookup"><span data-stu-id="85980-149">ServiceSet Resource</span></span>](../reference/resources/windows/serviceSetResource.md)
- [<span data-ttu-id="85980-150">사용자 리소스</span><span class="sxs-lookup"><span data-stu-id="85980-150">User Resource</span></span>](../reference/resources/windows/userResource.md)
- [<span data-ttu-id="85980-151">WindowsFeature 리소스</span><span class="sxs-lookup"><span data-stu-id="85980-151">WindowsFeature Resource</span></span>](../reference/resources/windows/windowsFeatureResource.md)
- [<span data-ttu-id="85980-152">WindowsFeatureSet 리소스</span><span class="sxs-lookup"><span data-stu-id="85980-152">WindowsFeatureSet Resource</span></span>](../reference/resources/windows/windowsFeatureSetResource.md)
- [<span data-ttu-id="85980-153">WindowsOptionalFeature 리소스</span><span class="sxs-lookup"><span data-stu-id="85980-153">WindowsOptionalFeature Resource</span></span>](../reference/resources/windows/windowsOptionalFeatureResource.md)
- [<span data-ttu-id="85980-154">WindowsOptionalFeatureSet 리소스</span><span class="sxs-lookup"><span data-stu-id="85980-154">WindowsOptionalFeatureSet Resource</span></span>](../reference/resources/windows/windowsOptionalFeatureSetResource.md)
- [<span data-ttu-id="85980-155">WindowsPackageCabResource 리소스</span><span class="sxs-lookup"><span data-stu-id="85980-155">WindowsPackageCabResource Resource</span></span>](../reference/resources/windows/windowsPackageCabResource.md)
- [<span data-ttu-id="85980-156">WindowsProcess 리소스</span><span class="sxs-lookup"><span data-stu-id="85980-156">WindowsProcess Resource</span></span>](../reference/resources/windows/windowsProcessResource.md)

### <a name="cross-node-dependency-resources"></a><span data-ttu-id="85980-157">노드 간 종속성 리소스</span><span class="sxs-lookup"><span data-stu-id="85980-157">Cross-Node dependency resources</span></span>

- [<span data-ttu-id="85980-158">WaitForAll 리소스</span><span class="sxs-lookup"><span data-stu-id="85980-158">WaitForAll Resource</span></span>](../reference/resources/windows/waitForAllResource.md)
- [<span data-ttu-id="85980-159">WaitForSome 리소스</span><span class="sxs-lookup"><span data-stu-id="85980-159">WaitForSome Resource</span></span>](../reference/resources/windows/waitForSomeResource.md)
- [<span data-ttu-id="85980-160">WaitForAny 리소스</span><span class="sxs-lookup"><span data-stu-id="85980-160">WaitForAny Resource</span></span>](../reference/resources/windows/waitForAnyResource.md)

### <a name="package-management-resources"></a><span data-ttu-id="85980-161">패키지 관리 리소스</span><span class="sxs-lookup"><span data-stu-id="85980-161">Package Management resources</span></span>

- [<span data-ttu-id="85980-162">PackageManagement 리소스</span><span class="sxs-lookup"><span data-stu-id="85980-162">PackageManagement Resource</span></span>](../reference/resources/packagemanagement/PackageManagementDscResource.md)
- [<span data-ttu-id="85980-163">PackageManagementSource 리소스</span><span class="sxs-lookup"><span data-stu-id="85980-163">PackageManagementSource Resource</span></span>](../reference/resources/packagemanagement/PackageManagementSourceDscResource.md)

#### <a name="linux-resources"></a><span data-ttu-id="85980-164">Linux 리소스</span><span class="sxs-lookup"><span data-stu-id="85980-164">Linux resources</span></span>

- [<span data-ttu-id="85980-165">Linux 보관 리소스</span><span class="sxs-lookup"><span data-stu-id="85980-165">Linux Archive Resource</span></span>](../reference/resources/linux/lnxArchiveResource.md)
- [<span data-ttu-id="85980-166">Linux 환경 리소스</span><span class="sxs-lookup"><span data-stu-id="85980-166">Linux Environment Resource</span></span>](../reference/resources/linux/lnxEnvironmentResource.md)
- [<span data-ttu-id="85980-167">Linux FileLine 리소스</span><span class="sxs-lookup"><span data-stu-id="85980-167">Linux FileLine Resource</span></span>](../reference/resources/linux/lnxFileLineResource.md)
- [<span data-ttu-id="85980-168">Linux 파일 리소스</span><span class="sxs-lookup"><span data-stu-id="85980-168">Linux File Resource</span></span>](../reference/resources/linux/lnxFileResource.md)
- [<span data-ttu-id="85980-169">Linux 그룹 리소스</span><span class="sxs-lookup"><span data-stu-id="85980-169">Linux Group Resource</span></span>](../reference/resources/linux/lnxGroupResource.md)
- [<span data-ttu-id="85980-170">Linux 패키지 리소스</span><span class="sxs-lookup"><span data-stu-id="85980-170">Linux Package Resource</span></span>](../reference/resources/linux/lnxPackageResource.md)
- [<span data-ttu-id="85980-171">Linux 스크립트 리소스</span><span class="sxs-lookup"><span data-stu-id="85980-171">Linux Script Resource</span></span>](../reference/resources/linux/lnxScriptResource.md)
- [<span data-ttu-id="85980-172">Linux 서비스 리소스</span><span class="sxs-lookup"><span data-stu-id="85980-172">Linux Service Resource</span></span>](../reference/resources/linux/lnxServiceResource.md)
- [<span data-ttu-id="85980-173">Linux SshAuthorizedKeys 리소스</span><span class="sxs-lookup"><span data-stu-id="85980-173">Linux SshAuthorizedKeys Resource</span></span>](../reference/resources/linux/lnxSshAuthorizedKeysResource.md)
- [<span data-ttu-id="85980-174">Linux 사용자 리소스</span><span class="sxs-lookup"><span data-stu-id="85980-174">Linux User Resource</span></span>](../reference/resources/linux/lnxUserResource.md)
