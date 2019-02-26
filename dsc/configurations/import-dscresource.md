---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Import-DSCResource 사용
ms.openlocfilehash: ee0b2f0469c6507c8f0148138198597a9e57cdd7
ms.sourcegitcommit: c581c4c8036edf55147e7bce4b00c860da6c5a8b
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 02/25/2019
ms.locfileid: "56803415"
---
# <a name="using-import-dscresource"></a><span data-ttu-id="9def5-103">Import-DSCResource 사용</span><span class="sxs-lookup"><span data-stu-id="9def5-103">Using Import-DSCResource</span></span>

<span data-ttu-id="9def5-104">`Import-DScResource` 구성 스크립트 블록 내부 에서만 사용할 수 있는 동적 키워드가입니다.</span><span class="sxs-lookup"><span data-stu-id="9def5-104">`Import-DScResource` is a dynamic keyword, which can only be used inside a Configuration script block.</span></span> <span data-ttu-id="9def5-105">`Import-DSCResource` 구성에 필요한 모든 리소스를 가져오기 위해 키워드입니다.</span><span class="sxs-lookup"><span data-stu-id="9def5-105">The `Import-DSCResource` keyword to import any resources needed in your Configuration.</span></span> <span data-ttu-id="9def5-106">아래에 있는 리소스 `$pshome` 자동으로 가져와집니다를 명시적으로 사용 되는 모든 리소스를 가져와야 하는 모범 사례는 여전히 간주 하지만 하 [구성](Configurations.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="9def5-106">Resources under `$pshome` are imported automatically, but it is still considered best practice to explicitly import all resources used in your [Configuration](Configurations.md).</span></span>

<span data-ttu-id="9def5-107">구문은 `Import-DSCResource` 아래에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9def5-107">The syntax for `Import-DSCResource` is shown below.</span></span>  <span data-ttu-id="9def5-108">모듈 이름으로 지정, 경우 새 줄에 나열 하는 요구 사항이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9def5-108">When specifying modules by name, it is a requirement to list each on a new line.</span></span>

```syntax
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName>]
```

|<span data-ttu-id="9def5-109">매개 변수</span><span class="sxs-lookup"><span data-stu-id="9def5-109">Parameter</span></span>  |<span data-ttu-id="9def5-110">설명</span><span class="sxs-lookup"><span data-stu-id="9def5-110">Description</span></span>  |
|---------|---------|
|`-Name`|<span data-ttu-id="9def5-111">가져와야 하는 DSC 리소스 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="9def5-111">The DSC resource name(s) that you must import.</span></span> <span data-ttu-id="9def5-112">모듈 이름 지정,이 모듈 내에서 이러한 DSC 리소스에 대 한 명령 검색 그렇지 않은 경우 명령은 모든 DSC 리소스 경로에 DSC 리소스를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="9def5-112">If the module name is specified, the command searches for these DSC resources within this module; otherwise the command searches the DSC resources in all DSC resource paths.</span></span> <span data-ttu-id="9def5-113">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="9def5-113">Wildcards are supported.</span></span>|
|`-ModuleName`|<span data-ttu-id="9def5-114">모듈 이름 또는 모듈 사양입니다.</span><span class="sxs-lookup"><span data-stu-id="9def5-114">The module name, or module specification.</span></span>  <span data-ttu-id="9def5-115">모듈에서 가져올 리소스를 지정 하는 경우이 명령은 해당 리소스에만 가져오기 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="9def5-115">If you specify resources to import from a module, the command will try to import only those resources.</span></span> <span data-ttu-id="9def5-116">만 모듈을 지정 하는 경우 명령 모듈에 있는 모든 DSC 리소스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9def5-116">If you specify the module only, the command imports all the DSC resources in the module.</span></span>|

```powershell
Import-DscResource -ModuleName xActiveDirectory;
```

## <a name="example-use-import-dscresource-within-a-configuration"></a><span data-ttu-id="9def5-117">예: 사용 하 여 Import-dscresource 구성 내에서</span><span class="sxs-lookup"><span data-stu-id="9def5-117">Example: Use Import-DSCResource within a configuration</span></span>

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
    Import-DSCResource -ModuleName ComputerManagementDsc
...
```

> [!NOTE]
> <span data-ttu-id="9def5-118">동일한 명령에서 리소스 이름과 모듈에 대 한 여러 값을 지정 하는 것은 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9def5-118">Specifying multiple values for Resource names and modules names in same command are not supported.</span></span> <span data-ttu-id="9def5-119">여러 모듈에 동일한 리소스가 있는 경우에 모듈에서 로드 하는 리소스에 대 한 비 결정적인 동작을 가질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9def5-119">It can have non-deterministic behavior about which resource to load from which module in case same resource exists in multiple modules.</span></span> <span data-ttu-id="9def5-120">아래 명령을 오류가 발생 합니다 컴파일하는 동안.</span><span class="sxs-lookup"><span data-stu-id="9def5-120">Below command will result in error during compilation.</span></span>
>
> ```powershell
> Import-DscResource -Name UserConfigProvider*,TestLogger1 -ModuleName UserConfigProv,PsModuleForTestLogger
> ```

<span data-ttu-id="9def5-121">Name 매개 변수를 사용 하는 경우를 고려해 야 할 사항은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9def5-121">Things to consider when using only the Name parameter:</span></span>

- <span data-ttu-id="9def5-122">이 컴퓨터에 설치 된 모듈 수에 따라 리소스 집약적 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="9def5-122">It is a resource-intensive operation depending on the number of modules installed on machine.</span></span>
- <span data-ttu-id="9def5-123">첫 번째 리소스를 지정 된 이름을 사용 하 여 찾을 수 로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9def5-123">It will load the first resource found with the given name.</span></span> <span data-ttu-id="9def5-124">경우에서 잘못 된 리소스를 다시 로드할를 설치 하는 동일한 이름 가진 둘 이상의 리소스가 있는 합니다.</span><span class="sxs-lookup"><span data-stu-id="9def5-124">In the case where there is more than one resource with same name installed, it could load the wrong resource.</span></span>

<span data-ttu-id="9def5-125">권장된 사용법을 지정 하는 것 `–ModuleName` 사용 하 여는 `-Name` 아래 설명 된 대로 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="9def5-125">The recommended usage is to specify `–ModuleName` with the `-Name` parameter, as described below.</span></span>

<span data-ttu-id="9def5-126">이 사용에는 다음과 같은 이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9def5-126">This usage has the following benefits:</span></span>

- <span data-ttu-id="9def5-127">지정된 된 리소스에 대 한 검색 범위를 제한 하 여 성능에 영향을 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="9def5-127">It reduces the performance impact by limiting the search scope for the specified resource.</span></span>
- <span data-ttu-id="9def5-128">명시적으로 로드 되 고 올바른 리소스를 보장 된 리소스를 정의 하는 모듈을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="9def5-128">It explicitly defines the module defining the resource, ensuring the correct resource is loaded.</span></span>

> [!NOTE]
> <span data-ttu-id="9def5-129">PowerShell 5.0에서 DSC 리소스는 여러 버전이 있을 수 있으며, 이러한 버전들을 컴퓨터에 병렬로 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9def5-129">In PowerShell 5.0, DSC resources can have multiple versions, and versions can be installed on a computer side-by-side.</span></span> <span data-ttu-id="9def5-130">이는 동일한 모듈 폴더에 포함된 여러 버전의 리소스 모듈에 의해 구현됩니다.</span><span class="sxs-lookup"><span data-stu-id="9def5-130">This is implemented by having multiple versions of a resource module that are contained in the same module folder.</span></span>
> <span data-ttu-id="9def5-131">자세한 내용은 [여러 버전의 리소스 사용](sxsresource.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9def5-131">For more information, see [Using resources with multiple versions](sxsresource.md).</span></span>

## <a name="intellisense-with-import-dscresource"></a><span data-ttu-id="9def5-132">Import-dscresource를 사용 하 여 Intellisense</span><span class="sxs-lookup"><span data-stu-id="9def5-132">Intellisense with Import-DSCResource</span></span>

<span data-ttu-id="9def5-133">ISE에서 DSC 구성을 작성, PowerShell 리소스 및 리소스 속성에 대 한 IntelliSence를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="9def5-133">When authoring the DSC configuration in ISE, PowerShell provides IntelliSence for resources and resource properties.</span></span> <span data-ttu-id="9def5-134">아래 리소스 정의 `$pshome` 모듈 경로 자동으로 로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9def5-134">Resource definitions under the `$pshome` module path are loaded automatically.</span></span> <span data-ttu-id="9def5-135">사용 하 여 리소스를 가져올 때는 `Import-DSCResource` 키워드를 지정 된 리소스 정의 추가 하 고 Intellisense 가져온된 리소스의 스키마를 포함 하도록 확장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9def5-135">When you import resources using the `Import-DSCResource` keyword, the specified resource definitions are added and Intellisense is expanded to include the imported resource's schema.</span></span>

![리소스 Intellisense](/media/resource-intellisense.png)

> [!NOTE]
> <span data-ttu-id="9def5-137">PowerShell 5.0부터, 탭 완성 기능 DSC 리소스 및 해당 속성에 대 한 ISE에 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9def5-137">Beginning in PowerShell 5.0, tab completion was added to the ISE for DSC resources and their properties.</span></span> <span data-ttu-id="9def5-138">자세한 내용은 [리소스](../resources/resources.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="9def5-138">For more information, see [Resources](../resources/resources.md).</span></span>

<span data-ttu-id="9def5-139">구성을 컴파일할 때 PowerShell를 사용 하 여 가져온된 리소스 정의 구성에서 모든 리소스 블록의 유효성을 검사 합니다.</span><span class="sxs-lookup"><span data-stu-id="9def5-139">When compiling the Configuration, PowerShell uses the imported resource definitions to validate all resource blocks in the configuration.</span></span>
<span data-ttu-id="9def5-140">다음 규칙에 대 한 리소스의 스키마 정의 사용 하 여 각 리소스 블록의 유효성이 검사 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9def5-140">Each resource block is validated, using the resource's schema definition, for the following rules.</span></span>

- <span data-ttu-id="9def5-141">스키마에 정의 된 속성에 대해서만 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9def5-141">Only properties defined in schema are used.</span></span>
- <span data-ttu-id="9def5-142">각 속성에 대 한 데이터 형식이 올바릅니다.</span><span class="sxs-lookup"><span data-stu-id="9def5-142">The data types for each property are correct.</span></span>
- <span data-ttu-id="9def5-143">키 속성 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9def5-143">Keys properties are specified.</span></span>
- <span data-ttu-id="9def5-144">읽기 전용 속성이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9def5-144">No read-only property is used.</span></span>
- <span data-ttu-id="9def5-145">값에 대 한 유효성 검사 형식을 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="9def5-145">Validation on value maps types.</span></span>

<span data-ttu-id="9def5-146">다음 구성을 고려 합니다.</span><span class="sxs-lookup"><span data-stu-id="9def5-146">Consider the following configuration:</span></span>

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
            Name = “Telnet-Client”
            Ensure = “Invalid”
        }
    }
}
```

<span data-ttu-id="9def5-147">오류가이 구성 결과 컴파일하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9def5-147">Compiling this Configuration results in an error.</span></span>

```output
PSDesiredStateConfiguration\WindowsFeature: At least one of the values ‘Invalid’ is not supported or valid for property ‘Ensure’ on class ‘WindowsFeature’. Please specify only supported values: Present, Absent.
```

<span data-ttu-id="9def5-148">Intellisense 및 스키마 유효성 검사를 사용 하면 런타임에 복잡성을 방지 구문 분석 및 컴파일 시간 동안 더 많은 오류를 catch 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9def5-148">Intellisense and schema validation allow you to catch more errors during parse and compilation time, avoiding complications at run time.</span></span>

> [!NOTE]
> <span data-ttu-id="9def5-149">각 DSC 리소스는 이름이 나 지정할 수와 **FriendlyName** 리소스의 스키마에 의해 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9def5-149">Each DSC resource can have a name, and a **FriendlyName** defined by the resource's schema.</span></span> <span data-ttu-id="9def5-150">"MSFT_ServiceResource.shema.mof"의 처음 두 줄은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9def5-150">Below are the first two lines of "MSFT_ServiceResource.shema.mof".</span></span>
> ```syntax
> [ClassVersion("1.0.0"),FriendlyName("Service")]
> class MSFT_ServiceResource : OMI_BaseResource
> ```
> <span data-ttu-id="9def5-151">구성에서이 리소스를 사용 하는 경우 지정할 수 있습니다 **MSFT_ServiceResource** 하거나 **서비스**합니다.</span><span class="sxs-lookup"><span data-stu-id="9def5-151">When using this resource in a Configuration, you can specify **MSFT_ServiceResource** or **Service**.</span></span>

## <a name="powershell-v4-and-v5-differences"></a><span data-ttu-id="9def5-152">PowerShell v4 및 v5 차이점</span><span class="sxs-lookup"><span data-stu-id="9def5-152">PowerShell v4 and v5 differences</span></span>

<span data-ttu-id="9def5-153">PowerShell 4.0 vs에서 구성을 작성 하는 경우 표시는 여러 차이점이 있습니다. PowerShell 5.0 이상</span><span class="sxs-lookup"><span data-stu-id="9def5-153">There are multiple differences you see when authoring Configurations in PowerShell 4.0 vs. PowerShell 5.0 and later.</span></span> <span data-ttu-id="9def5-154">이 섹션에서는 차이점을 강조 표시는이 문서와 관련 된 표시를 합니다.</span><span class="sxs-lookup"><span data-stu-id="9def5-154">This section will highlight the differences that you see relevant to this article.</span></span>

### <a name="multiple-resource-versions"></a><span data-ttu-id="9def5-155">여러 리소스 버전</span><span class="sxs-lookup"><span data-stu-id="9def5-155">Multiple Resource Versions</span></span>

<span data-ttu-id="9def5-156">설치 하 고 여러 버전의 리소스를 함께 사용 된 PowerShell 4.0에서 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9def5-156">Installing and using multiple versions of resources side by side was not supported in PowerShell 4.0.</span></span> <span data-ttu-id="9def5-157">구성에 리소스를 가져오는 문제를 발견 하는 경우 설치 리소스의 버전 하나만 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="9def5-157">If you notice issues importing resources into your Configuration, ensure that you only have one version of the resource installed.</span></span>

<span data-ttu-id="9def5-158">두 가지 버전의 아래 이미지에는 **xPSDesiredStateConfiguration** 모듈이 설치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9def5-158">In the image below, two versions of the **xPSDesiredStateConfiguration** module are installed.</span></span>

![고정 하는 여러 리소스 버전](/media/multiple-resource-versions-broken.md)

<span data-ttu-id="9def5-160">모듈 디렉터리의 최상위 수준으로 원하는 모듈 버전의 콘텐츠를 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="9def5-160">Copy the contents of your desired module version to the top level of the module directory.</span></span>

![고정 하는 여러 리소스 버전](/media/multiple-resource-versions-fixed.md)

### <a name="resource-location"></a><span data-ttu-id="9def5-162">리소스 위치</span><span class="sxs-lookup"><span data-stu-id="9def5-162">Resource location</span></span>

<span data-ttu-id="9def5-163">리소스에서 지정 된 디렉터리에 저장할 수 제작 및 구성 컴파일링, 경우에 [PSModulePath](/powershell/developer/module/modifying-the-psmodulepath-installation-path)합니다.</span><span class="sxs-lookup"><span data-stu-id="9def5-163">When authoring and compiling Configurations, your resources can be stored in any directory specified by your [PSModulePath](/powershell/developer/module/modifying-the-psmodulepath-installation-path).</span></span> <span data-ttu-id="9def5-164">PowerShell 4.0에서 LCM 필요 "프로그램 Files\WindowsPowerShell\Modules" 아래에 저장 될 모든 DSC 리소스 모듈 또는 `$pshome\Modules`합니다.</span><span class="sxs-lookup"><span data-stu-id="9def5-164">In PowerShell 4.0, the LCM requires all DSC resource modules to be stored under "Program Files\WindowsPowerShell\Modules" or `$pshome\Modules`.</span></span> <span data-ttu-id="9def5-165">PowerShell 5.0부터,이 요구 사항이 제거 되었지만, 및 리소스 모듈에서 지정 된 디렉터리에 저장할 수 있습니다 `PSModulePath`합니다.</span><span class="sxs-lookup"><span data-stu-id="9def5-165">Beginning in PowerShell 5.0, this requirement was removed, and resource modules can be stored in any directory specified by `PSModulePath`.</span></span>

## <a name="see-also"></a><span data-ttu-id="9def5-166">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9def5-166">See also</span></span>

- [<span data-ttu-id="9def5-167">리소스</span><span class="sxs-lookup"><span data-stu-id="9def5-167">Resources</span></span>](../resources/resources.md)
