---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: DSC PackageManagement 리소스
ms.openlocfilehash: dfc23bfabbc45041e15c56a29a77c5bdda430a30
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953240"
---
# <a name="dsc-packagemanagement-resource"></a><span data-ttu-id="f65ae-103">DSC PackageManagement 리소스</span><span class="sxs-lookup"><span data-stu-id="f65ae-103">DSC PackageManagement Resource</span></span>

<span data-ttu-id="f65ae-104">적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0, Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="f65ae-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0, Windows PowerShell 5.1</span></span>

<span data-ttu-id="f65ae-105">Windows PowerShell DSC(필요한 상태 구성)의 **PackageManagement** 리소스는 대상 노드에서 패키지 관리 패키지를 설치하거나 제거하는 메커니즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f65ae-105">The **PackageManagement** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall Package Management packages on a target node.</span></span> <span data-ttu-id="f65ae-106">이 리소스를 사용하려면 [http://PowerShellGallery.com](https://PowerShellGallery.com)에서 제공하는 **PackageManagement** 모듈이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="f65ae-106">This resource requires the **PackageManagement** module, available from [http://PowerShellGallery.com](https://PowerShellGallery.com).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f65ae-107">다음 속성 정보가 올바르려면 **PackageManagement** 모듈이 버전 1.1.7.0 이상이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f65ae-107">The **PackageManagement** module should be at least version 1.1.7.0 for the following property information to be correct.</span></span>

## <a name="syntax"></a><span data-ttu-id="f65ae-108">구문</span><span class="sxs-lookup"><span data-stu-id="f65ae-108">Syntax</span></span>

```Syntax
PackageManagement [string] #ResourceName
{
    Name = [string]
    [ AdditionalParameters = [HashTable] ]
    [ MaximumVersion = [string] ]
    [ MinimumVersion = [string] ]
    [ ProviderName = [string] ]
    [ RequiredVersion = [string] ]
    [ Source = [string] ]
    [ SourceCredential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string]{ Absent | Present } ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="f65ae-109">속성</span><span class="sxs-lookup"><span data-stu-id="f65ae-109">Properties</span></span>

|<span data-ttu-id="f65ae-110">속성</span><span class="sxs-lookup"><span data-stu-id="f65ae-110">Property</span></span> |<span data-ttu-id="f65ae-111">설명</span><span class="sxs-lookup"><span data-stu-id="f65ae-111">Description</span></span> |
|---|---|
|<span data-ttu-id="f65ae-112">이름</span><span class="sxs-lookup"><span data-stu-id="f65ae-112">Name</span></span> |<span data-ttu-id="f65ae-113">설치하거나 제거할 패키지의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f65ae-113">Specifies the name of the Package to be installed or uninstalled.</span></span> |
|<span data-ttu-id="f65ae-114">AdditionalParameters</span><span class="sxs-lookup"><span data-stu-id="f65ae-114">AdditionalParameters</span></span> |<span data-ttu-id="f65ae-115">`Get-Package -AdditionalArguments`에 전달되는 매개 변수의 공급자별 해시 테이블입니다.</span><span class="sxs-lookup"><span data-stu-id="f65ae-115">Provider specific hashtable of parameters that would be passed to `Get-Package -AdditionalArguments`.</span></span> <span data-ttu-id="f65ae-116">예를 들어 NuGet 공급자의 경우 DestinationPath와 같은 추가 매개 변수를 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f65ae-116">For example, for NuGet provider you can pass additional parameters like DestinationPath.</span></span> |
|<span data-ttu-id="f65ae-117">MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="f65ae-117">MaximumVersion</span></span> |<span data-ttu-id="f65ae-118">찾으려는 패키지의 최대 허용 버전을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f65ae-118">Specifies the maximum allowed version of the package that you want to find.</span></span> <span data-ttu-id="f65ae-119">이 매개 변수를 추가하지 않으면 리소스는 패키지의 사용 가능한 가장 높은 버전을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="f65ae-119">If you do not add this parameter, the resource finds the highest available version of the package.</span></span> |
|<span data-ttu-id="f65ae-120">MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="f65ae-120">MinimumVersion</span></span> |<span data-ttu-id="f65ae-121">찾으려는 패키지의 최소 허용 버전을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f65ae-121">Specifies the minimum allowed version of the package that you want to find.</span></span> <span data-ttu-id="f65ae-122">이 매개 변수를 추가하지 않으면 리소스는 **MaximumVersion** 매개 변수로 지정된 최대 지정 버전도 만족하는 패키지의 사용 가능한 가장 높은 버전을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="f65ae-122">If you do not add this parameter, the resource finds the highest available version of the package that also satisfies any maximum specified version specified by the **MaximumVersion** parameter.</span></span> |
|<span data-ttu-id="f65ae-123">ProviderName</span><span class="sxs-lookup"><span data-stu-id="f65ae-123">ProviderName</span></span> |<span data-ttu-id="f65ae-124">패키지 검색 범위를 지정할 패키지 공급자 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f65ae-124">Specifies a package provider name to which to scope your package search.</span></span> <span data-ttu-id="f65ae-125">`Get-PackageProvider` cmdlet을 실행하여 패키지 공급자 이름을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f65ae-125">You can get package provider names by running the `Get-PackageProvider` cmdlet.</span></span> |
|<span data-ttu-id="f65ae-126">RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="f65ae-126">RequiredVersion</span></span> |<span data-ttu-id="f65ae-127">설치할 패키지의 정확한 버전을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f65ae-127">Specifies the exact version of the package that you want to install.</span></span> <span data-ttu-id="f65ae-128">이 매개 변수를 지정하지 않으면 이 DSC 리소스는 **MaximumVersion** 매개 변수로 지정된 최대 버전도 만족하는 패키지의 사용 가능한 최신 버전을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="f65ae-128">If you do not specify this parameter, this DSC resource installs the newest available version of the package that also satisfies any maximum version specified by the **MaximumVersion** parameter.</span></span> |
|<span data-ttu-id="f65ae-129">원본</span><span class="sxs-lookup"><span data-stu-id="f65ae-129">Source</span></span> |<span data-ttu-id="f65ae-130">패키지를 찾을 수 있는 패키지 원본의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f65ae-130">Specifies the name of the package source where the package can be found.</span></span> <span data-ttu-id="f65ae-131">이는 `Register-PackageSource` 또는 PackageManagementSource DSC 리소스에 등록된 원본 또는 URI일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f65ae-131">This can either be a URI or a source registered with `Register-PackageSource` or PackageManagementSource DSC resource.</span></span> |
|<span data-ttu-id="f65ae-132">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="f65ae-132">SourceCredential</span></span> |<span data-ttu-id="f65ae-133">지정된 패키지 공급자 또는 원본에 대한 패키지를 설치하는 권한이 있는 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f65ae-133">Specifies a user account that has rights to install a package for a specified package provider or source.</span></span> |

## <a name="additional-parameters"></a><span data-ttu-id="f65ae-134">추가 매개 변수</span><span class="sxs-lookup"><span data-stu-id="f65ae-134">Additional Parameters</span></span>

<span data-ttu-id="f65ae-135">다음 표에는 AdditionalParameters 속성에 대한 옵션이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f65ae-135">The following table lists options for the AdditionalParameters property.</span></span>

|<span data-ttu-id="f65ae-136">매개 변수</span><span class="sxs-lookup"><span data-stu-id="f65ae-136">Parameter</span></span> |<span data-ttu-id="f65ae-137">설명</span><span class="sxs-lookup"><span data-stu-id="f65ae-137">Description</span></span> |
|---|---|
|<span data-ttu-id="f65ae-138">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="f65ae-138">DestinationPath</span></span> |<span data-ttu-id="f65ae-139">기본 제공 Nuget 공급자와 같은 공급자에서 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f65ae-139">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="f65ae-140">패키지를 설치할 파일 위치를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f65ae-140">Specifies a file location where you want the package to be installed.</span></span> |
|<span data-ttu-id="f65ae-141">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="f65ae-141">InstallationPolicy</span></span> |<span data-ttu-id="f65ae-142">기본 제공 Nuget 공급자와 같은 공급자에서 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f65ae-142">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="f65ae-143">패키지 원본을 신뢰할 수 있는지를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="f65ae-143">Determines whether you trust the package's source.</span></span> <span data-ttu-id="f65ae-144">다음 중 하나: **신뢰 안 함** 또는 **신뢰함**.</span><span class="sxs-lookup"><span data-stu-id="f65ae-144">One of: **Untrusted** or **Trusted**.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="f65ae-145">공용 속성</span><span class="sxs-lookup"><span data-stu-id="f65ae-145">Common properties</span></span>

|<span data-ttu-id="f65ae-146">속성</span><span class="sxs-lookup"><span data-stu-id="f65ae-146">Property</span></span> |<span data-ttu-id="f65ae-147">설명</span><span class="sxs-lookup"><span data-stu-id="f65ae-147">Description</span></span> |
|---|---|
|<span data-ttu-id="f65ae-148">DependsOn</span><span class="sxs-lookup"><span data-stu-id="f65ae-148">DependsOn</span></span> |<span data-ttu-id="f65ae-149">이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f65ae-149">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="f65ae-150">예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 ID가 ResourceName이고 해당 형식이 ResourceType일 경우, 이 속성을 사용하기 위한 구문은 `DependsOn = "[ResourceType]ResourceName"`입니다.</span><span class="sxs-lookup"><span data-stu-id="f65ae-150">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="f65ae-151">Ensure</span><span class="sxs-lookup"><span data-stu-id="f65ae-151">Ensure</span></span> |<span data-ttu-id="f65ae-152">패키지를 설치할지 또는 제거할지를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="f65ae-152">Determines whether the package is to be installed or uninstalled.</span></span> <span data-ttu-id="f65ae-153">기본값은 **Present**입니다.</span><span class="sxs-lookup"><span data-stu-id="f65ae-153">The default value is **Present**.</span></span> |
|<span data-ttu-id="f65ae-154">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="f65ae-154">PsDscRunAsCredential</span></span> |<span data-ttu-id="f65ae-155">전체 리소스를 실행하기 위한 자격 증명을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f65ae-155">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="f65ae-156">**PsDscRunAsCredential** 공용 속성은 다른 자격 증명의 컨텍스트에서 DSC 리소스를 실행할 수 있도록 WMF 5.0에 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f65ae-156">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="f65ae-157">자세한 내용은 [ DSC 리소스로 자격 증명 사용](../../../configurations/runasuser.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f65ae-157">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="f65ae-158">예제</span><span class="sxs-lookup"><span data-stu-id="f65ae-158">Example</span></span>

<span data-ttu-id="f65ae-159">이 예제에서는 **PackageManagement** DSC 리소스를 사용하여 **JQuery** NuGet 패키지 및 **GistProvider** PowerShell 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="f65ae-159">This example installs the **JQuery** NuGet package and **GistProvider** PowerShell module using the **PackageManagement** DSC resource.</span></span> <span data-ttu-id="f65ae-160">이 예제에서는 먼저 필요한 패키지 원본을 사용할 수 있는지를 확인한 다음 **JQuery** 및 **GistProvider** 패키지(각각 NuGet 및 PowerShell)의 필요한 상태를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="f65ae-160">This example first ensures the required package sources are available then defines the expected state of the **JQuery** and **GistProvider** packages (NuGet and PowerShell, respectively).</span></span>

```powershell
Configuration PackageTest
{
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present"
        Name        = "MyNuget"
        ProviderName= "Nuget"
        SourceLocation   = "http://nuget.org/api/v2/"
        InstallationPolicy ="Trusted"
    }

    PackageManagementSource PSGallery
    {
        Ensure      = "Present"
        Name        = "psgallery"
        ProviderName= "PowerShellGet"
        SourceLocation   = "https://www.powershellgallery.com/api/v2"
        InstallationPolicy ="Trusted"
    }

    PackageManagement NugetPackage
    {
        Ensure               = "Present"
        Name                 = "JQuery"
        AdditionalParameters = "$env:HomeDrive\nuget"
        RequiredVersion      = "2.0.1"
        DependsOn            = "[PackageManagementSource]SourceRepository"
    }

    PackageManagement PSModule
    {
        Ensure               = "Present"
        Name                 = "gistprovider"
        Source               = "PSGallery"
        DependsOn            = "[PackageManagementSource]PSGallery"
    }
}
```