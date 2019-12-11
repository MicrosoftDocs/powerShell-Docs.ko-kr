---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Import-DSCResource 사용
ms.openlocfilehash: 4bc269ab1dd4696298b4f33f7661473aae869eba
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74417414"
---
# <a name="using-import-dscresource"></a><span data-ttu-id="a9648-103">Import-DSCResource 사용</span><span class="sxs-lookup"><span data-stu-id="a9648-103">Using Import-DSCResource</span></span>

<span data-ttu-id="a9648-104">`Import-DScResource`는 구성 스크립트 블록 내부에서만 사용할 수 있는 동적 키워드입니다.</span><span class="sxs-lookup"><span data-stu-id="a9648-104">`Import-DScResource` is a dynamic keyword, which can only be used inside a Configuration script block.</span></span> <span data-ttu-id="a9648-105">구성에 필요한 모든 리소스를 가져오기 위한 `Import-DSCResource` 키워드입니다.</span><span class="sxs-lookup"><span data-stu-id="a9648-105">The `Import-DSCResource` keyword to import any resources needed in your Configuration.</span></span> <span data-ttu-id="a9648-106">`$pshome` 아래에 있는 리소스를 자동으로 가져오지만, [구성](Configurations.md)에서 사용된 모든 리소스를 명시적으로 가져오는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="a9648-106">Resources under `$pshome` are imported automatically, but it is still considered best practice to explicitly import all resources used in your [Configuration](Configurations.md).</span></span>

<span data-ttu-id="a9648-107">`Import-DSCResource`의 구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a9648-107">The syntax for `Import-DSCResource` is shown below.</span></span>  <span data-ttu-id="a9648-108">이름으로 모듈을 지정하는 경우 각 모듈을 새 줄에 나열해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a9648-108">When specifying modules by name, it is a requirement to list each on a new line.</span></span>

```syntax
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName>] [-ModuleVersion <ModuleVersion>]
```

|<span data-ttu-id="a9648-109">매개 변수</span><span class="sxs-lookup"><span data-stu-id="a9648-109">Parameter</span></span>  |<span data-ttu-id="a9648-110">설명</span><span class="sxs-lookup"><span data-stu-id="a9648-110">Description</span></span>  |
|---------|---------|
|`-Name`|<span data-ttu-id="a9648-111">가져와야 하는 DSC 리소스 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="a9648-111">The DSC resource name(s) that you must import.</span></span> <span data-ttu-id="a9648-112">모듈 이름을 지정하면 명령은 이 모듈 내에서 해당 DSC 리소스를 검색하고, 모듈 이름을 지정하지 않으면 명령은 모든 DSC 리소스 경로에서 DSC 리소스를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="a9648-112">If the module name is specified, the command searches for these DSC resources within this module; otherwise the command searches the DSC resources in all DSC resource paths.</span></span> <span data-ttu-id="a9648-113">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="a9648-113">Wildcards are supported.</span></span>|
|`-ModuleName`|<span data-ttu-id="a9648-114">모듈 이름 또는 모듈 사양입니다.</span><span class="sxs-lookup"><span data-stu-id="a9648-114">The module name, or module specification.</span></span>  <span data-ttu-id="a9648-115">모듈에서 가져올 리소스를 지정하면 명령은 해당 리소스만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a9648-115">If you specify resources to import from a module, the command will try to import only those resources.</span></span> <span data-ttu-id="a9648-116">모듈만 지정하면 명령은 모듈에 있는 모든 DSC 리소스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a9648-116">If you specify the module only, the command imports all the DSC resources in the module.</span></span>|
|`-ModuleVersion`|<span data-ttu-id="a9648-117">PowerShell 5.0부터 구성에서 사용해야 하는 모듈의 버전을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a9648-117">Beginning in PowerShell 5.0, you can specify which version of a module a configuration should use.</span></span> <span data-ttu-id="a9648-118">자세한 내용은 [설치된 리소스의 특정 버전 가져오기](sxsresource.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a9648-118">For more information, see [Import a specific version of an installed resource](sxsresource.md).</span></span>|

```powershell
Import-DscResource -ModuleName xActiveDirectory
```

## <a name="example-use-import-dscresource-within-a-configuration"></a><span data-ttu-id="a9648-119">예: 구성 내에서 Import-DSCResource 사용</span><span class="sxs-lookup"><span data-stu-id="a9648-119">Example: Use Import-DSCResource within a configuration</span></span>

```powershell
Configuration MSDSCConfiguration
{
    # Search for and imports Service, File, and Registry from the module PSDesiredStateConfiguration.
    Import-DSCResource -ModuleName PSDesiredStateConfiguration -Name Service, File, Registry

    # Search for and import Resource1 from the module that defines it.
    # If only –Name parameter is used then resources can belong to different PowerShell modules as well.
    # TimeZone resource is from the ComputerManagementDSC module which is not installed by default.
    # As a best practice, list each requirement on a different line if possible.  This makes reviewing
    # multiple changes in source control a bit easier.
    Import-DSCResource -Name File
    Import-DSCResource -Name TimeZone

    # Search for and import all DSC resources inside the module PSDesiredStateConfiguration.
    # When specifying the modulename parameter, it is a requirement to list each on a new line.
    Import-DSCResource -ModuleName PSDesiredStateConfiguration
    # In PowerShell 5.0 and later, you can specify a ModuleVersion parameter
    Import-DSCResource -ModuleName ComputerManagementDsc -ModuleVersion 6.0.0.0
...
```

> [!NOTE]
> <span data-ttu-id="a9648-120">동일한 명령에서 리소스 이름 및 모듈 이름에 여러 값을 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a9648-120">Specifying multiple values for Resource names and modules names in same command are not supported.</span></span> <span data-ttu-id="a9648-121">명령은 동일한 리소스가 여러 모듈에 있는 경우 어떤 모듈에서 어떤 리소스를 로드할지에 대한 비결정적 동작을 포함할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a9648-121">It can have non-deterministic behavior about which resource to load from which module in case same resource exists in multiple modules.</span></span> <span data-ttu-id="a9648-122">아래 명령을 실행하면 컴파일하는 동안 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="a9648-122">Below command will result in error during compilation.</span></span>
>
> ```powershell
> Import-DscResource -Name UserConfigProvider*,TestLogger1 -ModuleName UserConfigProv,PsModuleForTestLogger
> ```

<span data-ttu-id="a9648-123">Name 매개 변수를 사용하는 경우 고려해야 할 사항:</span><span class="sxs-lookup"><span data-stu-id="a9648-123">Things to consider when using only the Name parameter:</span></span>

- <span data-ttu-id="a9648-124">머신에 설치된 모듈 수에 따라 리소스가 많이 사용되는 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="a9648-124">It is a resource-intensive operation depending on the number of modules installed on machine.</span></span>
- <span data-ttu-id="a9648-125">지정된 이름을 사용하여 발견된 첫 번째 리소스를 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="a9648-125">It will load the first resource found with the given name.</span></span> <span data-ttu-id="a9648-126">동일한 이름을 가진 둘 이상의 리소스가 설치된 경우 잘못된 리소스를 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a9648-126">In the case where there is more than one resource with same name installed, it could load the wrong resource.</span></span>

<span data-ttu-id="a9648-127">아래 설명된 대로 `-Name` 매개 변수를 사용하여 `–ModuleName`을 지정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="a9648-127">The recommended usage is to specify `–ModuleName` with the `-Name` parameter, as described below.</span></span>

<span data-ttu-id="a9648-128">이 방법은 다음과 같은 이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a9648-128">This usage has the following benefits:</span></span>

- <span data-ttu-id="a9648-129">지정된 리소스의 검색 범위를 제한하여 성능에 미치는 영향을 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="a9648-129">It reduces the performance impact by limiting the search scope for the specified resource.</span></span>
- <span data-ttu-id="a9648-130">리소스를 정의하는 모듈을 명시적으로 정의하므로 올바른 리소스가 로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="a9648-130">It explicitly defines the module defining the resource, ensuring the correct resource is loaded.</span></span>

> [!NOTE]
> <span data-ttu-id="a9648-131">PowerShell 5.0에서 DSC 리소스는 여러 버전이 있을 수 있으며, 이러한 버전들을 컴퓨터에 병렬로 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a9648-131">In PowerShell 5.0, DSC resources can have multiple versions, and versions can be installed on a computer side-by-side.</span></span> <span data-ttu-id="a9648-132">이는 동일한 모듈 폴더에 포함된 여러 버전의 리소스 모듈에 의해 구현됩니다.</span><span class="sxs-lookup"><span data-stu-id="a9648-132">This is implemented by having multiple versions of a resource module that are contained in the same module folder.</span></span>
> <span data-ttu-id="a9648-133">자세한 내용은 [여러 버전의 리소스 사용](sxsresource.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a9648-133">For more information, see [Using resources with multiple versions](sxsresource.md).</span></span>

## <a name="intellisense-with-import-dscresource"></a><span data-ttu-id="a9648-134">Intellisense 및 Import-DSCResource</span><span class="sxs-lookup"><span data-stu-id="a9648-134">Intellisense with Import-DSCResource</span></span>

<span data-ttu-id="a9648-135">ISE에서 DSC 구성을 작성하면 PowerShell에서는 리소스 및 리소스 속성에 대한 IntelliSense를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a9648-135">When authoring the DSC configuration in ISE, PowerShell provides IntelliSence for resources and resource properties.</span></span> <span data-ttu-id="a9648-136">`$pshome` 모듈 경로 아래에 있는 리소스 정의가 자동으로 로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="a9648-136">Resource definitions under the `$pshome` module path are loaded automatically.</span></span> <span data-ttu-id="a9648-137">`Import-DSCResource` 키워드를 사용하여 리소스를 가져오면 지정된 리소스 정의가 추가되고 가져온 리소스의 스키마를 포함하도록 IntelliSense가 확장됩니다.</span><span class="sxs-lookup"><span data-stu-id="a9648-137">When you import resources using the `Import-DSCResource` keyword, the specified resource definitions are added and Intellisense is expanded to include the imported resource's schema.</span></span>

![리소스 IntelliSense](../media/resource-intellisense.png)

> [!NOTE]
> <span data-ttu-id="a9648-139">PowerShell 5.0부터, 탭 완성이 DSC 리소스 및 해당 속성에 대한 ISE에 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a9648-139">Beginning in PowerShell 5.0, tab completion was added to the ISE for DSC resources and their properties.</span></span> <span data-ttu-id="a9648-140">자세한 내용은 [리소스](../resources/resources.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a9648-140">For more information, see [Resources](../resources/resources.md).</span></span>

<span data-ttu-id="a9648-141">구성을 컴파일할 때 PowerShell에서는 가져온 리소스 정의를 사용하여 구성에 있는 모든 리소스 블록의 유효성을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="a9648-141">When compiling the Configuration, PowerShell uses the imported resource definitions to validate all resource blocks in the configuration.</span></span>
<span data-ttu-id="a9648-142">다음 규칙에 대해 리소스의 스키마 정의를 사용하여 각 리소스 블록의 유효성을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="a9648-142">Each resource block is validated, using the resource's schema definition, for the following rules.</span></span>

- <span data-ttu-id="a9648-143">스키마에 정의된 속성만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="a9648-143">Only properties defined in schema are used.</span></span>
- <span data-ttu-id="a9648-144">각 속성의 데이터 형식이 올바릅니다.</span><span class="sxs-lookup"><span data-stu-id="a9648-144">The data types for each property are correct.</span></span>
- <span data-ttu-id="a9648-145">키 속성이 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="a9648-145">Keys properties are specified.</span></span>
- <span data-ttu-id="a9648-146">읽기 전용 속성이 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a9648-146">No read-only property is used.</span></span>
- <span data-ttu-id="a9648-147">값에 대한 유효성 검사가 형식을 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="a9648-147">Validation on value maps types.</span></span>

<span data-ttu-id="a9648-148">다음 구성을 고려하세요.</span><span class="sxs-lookup"><span data-stu-id="a9648-148">Consider the following configuration:</span></span>

```powershell
Configuration SchemaValidationInCorrectEnumValue
{
    # It is best practice to explicitly import all resources used in your Configuration.
    # This includes resources that are imported automatically, like WindowsFeature.
    Import-DSCResource -Name WindowsFeature
    Node localhost
    {
        WindowsFeature ROLE1
        {
            Name = "Telnet-Client"
            Ensure = "Invalid"
        }
    }
}
```

<span data-ttu-id="a9648-149">이 구성을 컴파일하면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="a9648-149">Compiling this Configuration results in an error.</span></span>

```output
PSDesiredStateConfiguration\WindowsFeature: At least one of the values 'Invalid' is not supported or valid for property 'Ensure' on class 'WindowsFeature'. Please specify only supported values: Present, Absent.
```

<span data-ttu-id="a9648-150">IntelliSense 및 스키마 유효성 검사를 사용하면 구문 분석 및 컴파일 시간에 더 많은 오류를 catch할 수 있어 런타임에 컴플리케이션이 방지됩니다.</span><span class="sxs-lookup"><span data-stu-id="a9648-150">Intellisense and schema validation allow you to catch more errors during parse and compilation time, avoiding complications at run time.</span></span>

> [!NOTE]
> <span data-ttu-id="a9648-151">각 DSC 리소스에는 이름 및 리소스 스키마에서 정의한 **FriendlyName**이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a9648-151">Each DSC resource can have a name, and a **FriendlyName** defined by the resource's schema.</span></span> <span data-ttu-id="a9648-152">"MSFT_ServiceResource.shema.mof"의 처음 두 줄은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a9648-152">Below are the first two lines of "MSFT_ServiceResource.shema.mof".</span></span>
> ```syntax
> [ClassVersion("1.0.0"),FriendlyName("Service")]
> class MSFT_ServiceResource : OMI_BaseResource
> ```
> <span data-ttu-id="a9648-153">구성에서 이 리소스를 사용하는 경우 **MSFT_ServiceResource** 또는 **Service**를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a9648-153">When using this resource in a Configuration, you can specify **MSFT_ServiceResource** or **Service**.</span></span>

## <a name="powershell-v4-and-v5-differences"></a><span data-ttu-id="a9648-154">PowerShell v4 및 v5의 차이</span><span class="sxs-lookup"><span data-stu-id="a9648-154">PowerShell v4 and v5 differences</span></span>

<span data-ttu-id="a9648-155">PowerShell 4.0 및 PowerShell 5.0 이상에서 구성을 작성할 때 확인되는 여러 가지 차이가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a9648-155">There are multiple differences you see when authoring Configurations in PowerShell 4.0 vs. PowerShell 5.0 and later.</span></span> <span data-ttu-id="a9648-156">이 섹션에서는 이 문서에 관련된 차이를 중점적으로 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a9648-156">This section will highlight the differences that you see relevant to this article.</span></span>

### <a name="multiple-resource-versions"></a><span data-ttu-id="a9648-157">여러 리소스 버전</span><span class="sxs-lookup"><span data-stu-id="a9648-157">Multiple Resource Versions</span></span>

<span data-ttu-id="a9648-158">PowerShell 4.0에서는 여러 리소스 버전을 병렬로 설치 및 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a9648-158">Installing and using multiple versions of resources side by side was not supported in PowerShell 4.0.</span></span> <span data-ttu-id="a9648-159">리소스를 구성으로 가져오는 동안 문제가 발생하면 설치된 리소스 버전이 하나만 있는지 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="a9648-159">If you notice issues importing resources into your Configuration, ensure that you only have one version of the resource installed.</span></span>

<span data-ttu-id="a9648-160">아래 이미지에는 **xPSDesiredStateConfiguration** 모듈의 두 가지 버전이 설치되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a9648-160">In the image below, two versions of the **xPSDesiredStateConfiguration** module are installed.</span></span>

![수정된 여러 리소스 버전](../media/multiple-resource-versions-broken.png)

<span data-ttu-id="a9648-162">원하는 모듈 버전의 콘텐츠를 모듈 디렉터리의 맨 위 수준으로 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="a9648-162">Copy the contents of your desired module version to the top level of the module directory.</span></span>

![수정된 여러 리소스 버전](../media/multiple-resource-versions-fixed.png)

### <a name="resource-location"></a><span data-ttu-id="a9648-164">리소스 위치</span><span class="sxs-lookup"><span data-stu-id="a9648-164">Resource location</span></span>

<span data-ttu-id="a9648-165">구성을 작성하고 컴파일하면 [PSModulePath](/powershell/scripting/developer/module/modifying-the-psmodulepath-installation-path)에서 지정한 디렉터리에 리소스를 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a9648-165">When authoring and compiling Configurations, your resources can be stored in any directory specified by your [PSModulePath](/powershell/scripting/developer/module/modifying-the-psmodulepath-installation-path).</span></span> <span data-ttu-id="a9648-166">PowerShell 4.0에서 LCM을 사용하려면 모든 DSC 리소스 모듈을 “Program Files\WindowsPowerShell\Modules” 또는 `$pshome\Modules` 아래에 저장해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a9648-166">In PowerShell 4.0, the LCM requires all DSC resource modules to be stored under "Program Files\WindowsPowerShell\Modules" or `$pshome\Modules`.</span></span> <span data-ttu-id="a9648-167">PowerShell 5.0부터, 이 요구 사항이 제거되었고 리소스 모듈은 `PSModulePath`에서 지정한 모든 디렉터리에 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a9648-167">Beginning in PowerShell 5.0, this requirement was removed, and resource modules can be stored in any directory specified by `PSModulePath`.</span></span>

### <a name="moduleversion-added"></a><span data-ttu-id="a9648-168">ModuleVersion 추가됨</span><span class="sxs-lookup"><span data-stu-id="a9648-168">ModuleVersion added</span></span>

<span data-ttu-id="a9648-169">PowerShell 5.0부터 `-ModuleVersion` 매개 변수를 사용하여 구성 내에서 사용할 모듈의 버전을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a9648-169">Beginning in PowerShell 5.0, the `-ModuleVersion` parameter allows you to specify which version of a module to use within your configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="a9648-170">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a9648-170">See also</span></span>

- [<span data-ttu-id="a9648-171">리소스</span><span class="sxs-lookup"><span data-stu-id="a9648-171">Resources</span></span>](../resources/resources.md)
