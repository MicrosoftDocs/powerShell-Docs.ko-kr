---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: DSC 리소스
ms.openlocfilehash: 1f77b5e6630a2e3de6e1d1a05638f94d2df039ae
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954250"
---
# <a name="dsc-resources"></a><span data-ttu-id="1e026-103">DSC 리소스</span><span class="sxs-lookup"><span data-stu-id="1e026-103">DSC Resources</span></span>

><span data-ttu-id="1e026-104">적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="1e026-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="1e026-105">DSC(필요한 상태 구성) 리소스에서는 DSC 구성에 대한 구성 요소를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1e026-105">Desired State Configuration (DSC) Resources provide the building blocks for a DSC configuration.</span></span> <span data-ttu-id="1e026-106">리소스는 구성할 수 있는 속성(스키마)을 노출하고 LCM(로컬 구성 관리자)이 "그대로 수행"하기 위해 호출하는 PowerShell 스크립트 함수를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="1e026-106">A resource exposes properties that can be configured (schema) and contains the PowerShell script functions that the Local Configuration Manager (LCM) calls to "make it so".</span></span>

<span data-ttu-id="1e026-107">리소스는 파일만큼 일반적이거나 IIS 서버만큼 특별한 것을 모델링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e026-107">A resource can model something as generic as a file or as specific as an IIS server setting.</span></span>  <span data-ttu-id="1e026-108">같은 리소스들의 그룹은 모든 필수 파일을 이식 가능한 구조로 정리하고, 리소스를 사용하려고 한 방법을 식별하는 메타데이터를 포함하는 DSC 모듈에 결합됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e026-108">Groups of like resources are combined in to a DSC Module, which organizes all the required files in to a structure that is portable and includes metadata to identify how the resources are intended to be used.</span></span>

<span data-ttu-id="1e026-109">각 리소스에는 [구성](../configurations/configurations.md)에서 리소스를 사용하는 데 필요한 구문을 결정하는 \*스키마가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e026-109">Each resource has a \*schema that determines the syntax needed to use the resource in a [Configuration](../configurations/configurations.md).</span></span> <span data-ttu-id="1e026-110">리소스 스키마는 다음 방법으로 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e026-110">A resource's schema can be defined in the following ways:</span></span>

- <span data-ttu-id="1e026-111">**'Schema.Mof'** 파일: 대부분의 리소스는 [Managed Object Format](/windows/desktop/wmisdk/managed-object-format--mof-)을 사용하여 'schema.mof' 파일에서 해당 ‘스키마’를 정의합니다. </span><span class="sxs-lookup"><span data-stu-id="1e026-111">**'Schema.Mof'** file: Most resources define their *schema* in a 'schema.mof' file, using [Managed Object Format](/windows/desktop/wmisdk/managed-object-format--mof-).</span></span>
- <span data-ttu-id="1e026-112">**'\<리소스 이름\>.schema.psm1'** 파일: [복합 리소스](../configurations/compositeConfigs.md)는 [매개 변수 블록](/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-6#functions-with-parameters)을 사용하여 '<ResourceName>.schema.psm1' 파일에서 해당 ‘스키마’를 정의합니다. </span><span class="sxs-lookup"><span data-stu-id="1e026-112">**'\<Resource Name\>.schema.psm1'** file: [Composite Resources](../configurations/compositeConfigs.md) define their *schema* in a '<ResourceName>.schema.psm1' file using a [Parameter Block](/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-6#functions-with-parameters).</span></span>
- <span data-ttu-id="1e026-113">**'\<리소스 이름\>.psm1'** 파일: 클래스 기반 DSC 리소스는 클래스 정의에서 해당 ‘스키마’를 정의합니다. </span><span class="sxs-lookup"><span data-stu-id="1e026-113">**'\<Resource Name\>.psm1'** file: Class based DSC resources define their *schema* in the class definition.</span></span> <span data-ttu-id="1e026-114">구문 항목은 클래스 속성으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e026-114">Syntax items are denoted as Class properties.</span></span> <span data-ttu-id="1e026-115">자세한 내용은 [about_Classes](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1e026-115">For more information, see [about_Classes](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc).</span></span>

<span data-ttu-id="1e026-116">DSC 리소스의 구문을 검색하려면 [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet과 함께 `-Syntax` 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1e026-116">To retrieve the syntax for a DSC resource, use the [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet with the `-Syntax` parameter.</span></span> <span data-ttu-id="1e026-117">이 사용법은 [Get-Command](/powershell/module/microsoft.powershell.core/get-command)와 함께 `-Syntax` 매개 변수를 사용하여 cmdlet 구문을 가져오는 것과 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="1e026-117">This usage is similar to using [Get-Command](/powershell/module/microsoft.powershell.core/get-command) with the `-Syntax` parameter to get cmdlet syntax.</span></span> <span data-ttu-id="1e026-118">표시되는 출력은 지정하는 리소스의 리소스 블록에 사용되는 템플릿을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1e026-118">The output you see will show the template used for a resource block for the resource you specify.</span></span>

```powershell
Get-DscResource -Syntax Service
```

<span data-ttu-id="1e026-119">표시되는 출력은 아래 출력과 비슷하지만, 이 리소스의 구문은 나중에 변경될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e026-119">The output you see should be similar to the output below, though this resource's syntax could change in the future.</span></span> <span data-ttu-id="1e026-120">cmdlet 구문과 같이 대괄호 안에 표시되는 ‘키’는 선택 사항입니다. </span><span class="sxs-lookup"><span data-stu-id="1e026-120">Like cmdlet syntax, the *keys* seen in square brackets, are optional.</span></span> <span data-ttu-id="1e026-121">형식은 각 키에 필요한 데이터 형식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1e026-121">The types specify the type of data each key expects.</span></span>

> [!NOTE]
> <span data-ttu-id="1e026-122">**Ensure** 키는 기본적으로 "Present"로 설정되므로 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="1e026-122">The **Ensure** key is optional because it defaults to "Present".</span></span>

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

<span data-ttu-id="1e026-123">구성 내부에 있는 **Service** 리소스 블록은 Spooler 서비스가 실행 중인지 **확인**하기 위해 이와 같이 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e026-123">Inside a Configuration, a **Service** resource block might look like this to **Ensure** that the Spooler service is running.</span></span>

> [!NOTE]
> <span data-ttu-id="1e026-124">구성에서 리소스를 사용하기 전에 [Import-DSCResource](../configurations/import-dscresource.md)를 사용하여 리소스를 가져와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e026-124">Before using a resource in a Configuration, you must import it using [Import-DSCResource](../configurations/import-dscresource.md).</span></span>

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

<span data-ttu-id="1e026-125">구성에는 동일한 리소스 종류의 여러 인스턴스가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e026-125">Configurations can contain multiple instances of the same resource type.</span></span> <span data-ttu-id="1e026-126">각 인스턴스의 이름은 고유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e026-126">Each instance must be uniquely named.</span></span> <span data-ttu-id="1e026-127">다음 예제에서는 "DHCP" 서비스를 구성하는 두 번째 **Service** 리소스 블록이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e026-127">In the following example, a second **Service** resource block is added to configure the "DHCP" service.</span></span>

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
> <span data-ttu-id="1e026-128">PowerShell 5.0부터, IntelliSense가 DSC용으로 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1e026-128">Beginning in PowerShell 5.0, intellisense was added for DSC.</span></span> <span data-ttu-id="1e026-129">이 새로운 기능을 통해 \<TAB\> 및 \<Ctrl+Space\>를 사용하여 키 이름을 자동 완성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e026-129">This new feature allows you to use \<TAB\> and \<Ctrl+Space\> to auto-complete key names.</span></span>

![리소스 탭 완성](../media/resource-tabcompletion.png)

## <a name="built-in-resources"></a><span data-ttu-id="1e026-131">기본 제공 리소스</span><span class="sxs-lookup"><span data-stu-id="1e026-131">Built-in resources</span></span>

<span data-ttu-id="1e026-132">커뮤니티 리소스 외에도 Windows용 기본 제공 리소스, Linux용 리소스 및 노드 간 종속성용 리소스가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e026-132">In addition to community resources, there are built-in resources for Windows, resources for Linux, and resources for cross-node dependency.</span></span> <span data-ttu-id="1e026-133">위의 단계를 사용하여 이 리소스의 구문 및 리소스 사용 방법을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e026-133">You can use the steps above to determine the syntax of these resources and how to use them.</span></span> <span data-ttu-id="1e026-134">이 리소스를 제공하는 페이지는 **참조**아래에 보관되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1e026-134">The pages that serve these resources have been archived under **Reference**.</span></span>

<span data-ttu-id="1e026-135">Windows 기본 제공 리소스</span><span class="sxs-lookup"><span data-stu-id="1e026-135">Windows built-in resources</span></span>

* [<span data-ttu-id="1e026-136">보관 리소스</span><span class="sxs-lookup"><span data-stu-id="1e026-136">Archive Resource</span></span>](../reference/resources/windows/archiveResource.md)
* [<span data-ttu-id="1e026-137">환경 리소스</span><span class="sxs-lookup"><span data-stu-id="1e026-137">Environment Resource</span></span>](../reference/resources/windows/environmentResource.md)
* [<span data-ttu-id="1e026-138">파일 리소스</span><span class="sxs-lookup"><span data-stu-id="1e026-138">File Resource</span></span>](../reference/resources/windows/fileResource.md)
* [<span data-ttu-id="1e026-139">그룹 리소스</span><span class="sxs-lookup"><span data-stu-id="1e026-139">Group Resource</span></span>](../reference/resources/windows/groupResource.md)
* [<span data-ttu-id="1e026-140">GroupSet 리소스</span><span class="sxs-lookup"><span data-stu-id="1e026-140">GroupSet Resource</span></span>](../reference/resources/windows/groupSetResource.md)
* [<span data-ttu-id="1e026-141">로그 리소스</span><span class="sxs-lookup"><span data-stu-id="1e026-141">Log Resource</span></span>](../reference/resources/windows/logResource.md)
* [<span data-ttu-id="1e026-142">패키지 리소스</span><span class="sxs-lookup"><span data-stu-id="1e026-142">Package Resource</span></span>](../reference/resources/windows/packageResource.md)
* [<span data-ttu-id="1e026-143">ProcessSet 리소스</span><span class="sxs-lookup"><span data-stu-id="1e026-143">ProcessSet Resource</span></span>](../reference/resources/windows/ProcessSetResource.md)
* [<span data-ttu-id="1e026-144">레지스트리 리소스</span><span class="sxs-lookup"><span data-stu-id="1e026-144">Registry Resource</span></span>](../reference/resources/windows/registryResource.md)
* [<span data-ttu-id="1e026-145">스크립트 리소스</span><span class="sxs-lookup"><span data-stu-id="1e026-145">Script Resource</span></span>](../reference/resources/windows/scriptResource.md)
* [<span data-ttu-id="1e026-146">서비스 리소스</span><span class="sxs-lookup"><span data-stu-id="1e026-146">Service Resource</span></span>](../reference/resources/windows/serviceResource.md)
* [<span data-ttu-id="1e026-147">ServiceSet 리소스</span><span class="sxs-lookup"><span data-stu-id="1e026-147">ServiceSet Resource</span></span>](../reference/resources/windows/serviceSetResource.md)
* [<span data-ttu-id="1e026-148">사용자 리소스</span><span class="sxs-lookup"><span data-stu-id="1e026-148">User Resource</span></span>](../reference/resources/windows/userResource.md)
* [<span data-ttu-id="1e026-149">WindowsFeature 리소스</span><span class="sxs-lookup"><span data-stu-id="1e026-149">WindowsFeature Resource</span></span>](../reference/resources/windows/windowsFeatureResource.md)
* [<span data-ttu-id="1e026-150">WindowsFeatureSet 리소스</span><span class="sxs-lookup"><span data-stu-id="1e026-150">WindowsFeatureSet Resource</span></span>](../reference/resources/windows/windowsFeatureSetResource.md)
* [<span data-ttu-id="1e026-151">WindowsOptionalFeature 리소스</span><span class="sxs-lookup"><span data-stu-id="1e026-151">WindowsOptionalFeature Resource</span></span>](../reference/resources/windows/windowsOptionalFeatureResource.md)
* [<span data-ttu-id="1e026-152">WindowsOptionalFeatureSet 리소스</span><span class="sxs-lookup"><span data-stu-id="1e026-152">WindowsOptionalFeatureSet Resource</span></span>](../reference/resources/windows/windowsOptionalFeatureSetResource.md)
* [<span data-ttu-id="1e026-153">WindowsPackageCabResource 리소스</span><span class="sxs-lookup"><span data-stu-id="1e026-153">WindowsPackageCabResource Resource</span></span>](../reference/resources/windows/windowsPackageCabResource.md)
* [<span data-ttu-id="1e026-154">WindowsProcess 리소스</span><span class="sxs-lookup"><span data-stu-id="1e026-154">WindowsProcess Resource</span></span>](../reference/resources/windows/windowsProcessResource.md)

<span data-ttu-id="1e026-155">[노드 간 종속성](../configurations/crossNodeDependencies.md) 리소스</span><span class="sxs-lookup"><span data-stu-id="1e026-155">[Cross-Node dependency](../configurations/crossNodeDependencies.md) resources</span></span>

* [<span data-ttu-id="1e026-156">WaitForAll 리소스</span><span class="sxs-lookup"><span data-stu-id="1e026-156">WaitForAll Resource</span></span>](../reference/resources/windows/waitForAllResource.md)
* [<span data-ttu-id="1e026-157">WaitForSome 리소스</span><span class="sxs-lookup"><span data-stu-id="1e026-157">WaitForSome Resource</span></span>](../reference/resources/windows/waitForSomeResource.md)
* [<span data-ttu-id="1e026-158">WaitForAny 리소스</span><span class="sxs-lookup"><span data-stu-id="1e026-158">WaitForAny Resource</span></span>](../reference/resources/windows/waitForAnyResource.md)

<span data-ttu-id="1e026-159">패키지 관리 리소스</span><span class="sxs-lookup"><span data-stu-id="1e026-159">Package Management resources</span></span>

* [<span data-ttu-id="1e026-160">PackageManagement 리소스</span><span class="sxs-lookup"><span data-stu-id="1e026-160">PackageManagement Resource</span></span>](../reference/resources/packagemanagement/PackageManagementDscResource.md)
* [<span data-ttu-id="1e026-161">PackageManagementSource 리소스</span><span class="sxs-lookup"><span data-stu-id="1e026-161">PackageManagementSource Resource</span></span>](../reference/resources/packagemanagement/PackageManagementSourceDscResource.md)

<span data-ttu-id="1e026-162">Linux 리소스</span><span class="sxs-lookup"><span data-stu-id="1e026-162">Linux resources</span></span>

* [<span data-ttu-id="1e026-163">Linux 보관 리소스</span><span class="sxs-lookup"><span data-stu-id="1e026-163">Linux Archive Resource</span></span>](../reference/resources/linux/lnxArchiveResource.md)
* [<span data-ttu-id="1e026-164">Linux 환경 리소스</span><span class="sxs-lookup"><span data-stu-id="1e026-164">Linux Environment Resource</span></span>](../reference/resources/linux/lnxEnvironmentResource.md)
* [<span data-ttu-id="1e026-165">Linux FileLine 리소스</span><span class="sxs-lookup"><span data-stu-id="1e026-165">Linux FileLine Resource</span></span>](../reference/resources/linux/lnxFileLineResource.md)
* [<span data-ttu-id="1e026-166">Linux 파일 리소스</span><span class="sxs-lookup"><span data-stu-id="1e026-166">Linux File Resource</span></span>](../reference/resources/linux/lnxFileResource.md)
* [<span data-ttu-id="1e026-167">Linux 그룹 리소스</span><span class="sxs-lookup"><span data-stu-id="1e026-167">Linux Group Resource</span></span>](../reference/resources/linux/lnxGroupResource.md)
* [<span data-ttu-id="1e026-168">Linux 패키지 리소스</span><span class="sxs-lookup"><span data-stu-id="1e026-168">Linux Package Resource</span></span>](../reference/resources/linux/lnxPackageResource.md)
* [<span data-ttu-id="1e026-169">Linux 스크립트 리소스</span><span class="sxs-lookup"><span data-stu-id="1e026-169">Linux Script Resource</span></span>](../reference/resources/linux/lnxScriptResource.md)
* [<span data-ttu-id="1e026-170">Linux 서비스 리소스</span><span class="sxs-lookup"><span data-stu-id="1e026-170">Linux Service Resource</span></span>](../reference/resources/linux/lnxServiceResource.md)
* [<span data-ttu-id="1e026-171">Linux SshAuthorizedKeys 리소스</span><span class="sxs-lookup"><span data-stu-id="1e026-171">Linux SshAuthorizedKeys Resource</span></span>](../reference/resources/linux/lnxSshAuthorizedKeysResource.md)
* [<span data-ttu-id="1e026-172">Linux 사용자 리소스</span><span class="sxs-lookup"><span data-stu-id="1e026-172">Linux User Resource</span></span>](../reference/resources/linux/lnxUserResource.md)
