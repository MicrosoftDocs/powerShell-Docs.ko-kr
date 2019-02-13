---
ms.date: 06/20/2018
keywords: dsc,powershell,configuration,setup
title: DSC PackageManagement 리소스
ms.openlocfilehash: 18cbbfe0715c82dcfdf4a5fb6ee36ee814e43d3b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55681583"
---
# <a name="dsc-packagemanagement-resource"></a><span data-ttu-id="f725b-103">DSC PackageManagement 리소스</span><span class="sxs-lookup"><span data-stu-id="f725b-103">DSC PackageManagement Resource</span></span>

<span data-ttu-id="f725b-104">적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0, Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="f725b-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0, Windows PowerShell 5.1</span></span>

<span data-ttu-id="f725b-105">Windows PowerShell DSC(필요한 상태 구성)의 **PackageManagement** 리소스는 대상 노드에서 패키지 관리 패키지를 설치하거나 제거하는 메커니즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f725b-105">The **PackageManagement** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall Package Management packages on a target node.</span></span> <span data-ttu-id="f725b-106">이 리소스를 사용하려면 [http://PowerShellGallery.com](http://PowerShellGallery.com)에서 제공하는 **PackageManagement** 모듈이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="f725b-106">This resource requires the **PackageManagement** module, available from [http://PowerShellGallery.com](http://PowerShellGallery.com).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f725b-107">다음 속성 정보가 올바르려면 **PackageManagement** 모듈이 버전 1.1.7.0 이상이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f725b-107">The **PackageManagement** module should be at least version 1.1.7.0 for the following property information to be correct.</span></span>

## <a name="syntax"></a><span data-ttu-id="f725b-108">구문</span><span class="sxs-lookup"><span data-stu-id="f725b-108">Syntax</span></span>

```
PackageManagement [string] #ResourceName
{
    Name = [string]
    [AdditionalParameters = [HashTable]]
    [DependsOn = [string[]]]
    [Ensure = [string]{ Absent | Present }]
    [MaximumVersion = [string]]
    [MinimumVersion = [string]]
    [ProviderName = [string]]
    [PsDscRunAsCredential = [PSCredential]]
    [RequiredVersion = [string]]
    [Source = [string]]
    [SourceCredential = [PSCredential]]
}
```

## <a name="properties"></a><span data-ttu-id="f725b-109">속성</span><span class="sxs-lookup"><span data-stu-id="f725b-109">Properties</span></span>

| <span data-ttu-id="f725b-110">속성</span><span class="sxs-lookup"><span data-stu-id="f725b-110">Property</span></span> | <span data-ttu-id="f725b-111">설명</span><span class="sxs-lookup"><span data-stu-id="f725b-111">Description</span></span> |
| --- | --- |
| <span data-ttu-id="f725b-112">이름</span><span class="sxs-lookup"><span data-stu-id="f725b-112">Name</span></span>| <span data-ttu-id="f725b-113">설치하거나 제거할 패키지의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f725b-113">Specifies the name of the Package to be installed or uninstalled.</span></span>|
| <span data-ttu-id="f725b-114">AdditionalParameters</span><span class="sxs-lookup"><span data-stu-id="f725b-114">AdditionalParameters</span></span>| <span data-ttu-id="f725b-115">`Get-Package -AdditionalArguments`에 전달되는 매개 변수의 공급자별 해시 테이블입니다.</span><span class="sxs-lookup"><span data-stu-id="f725b-115">Provider specific hashtable of parameters that would be passed to `Get-Package -AdditionalArguments`.</span></span> <span data-ttu-id="f725b-116">예를 들어 NuGet 공급자의 경우 DestinationPath와 같은 추가 매개 변수를 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f725b-116">For example, for NuGet provider you can pass additional parameters like DestinationPath.</span></span>|
| <span data-ttu-id="f725b-117">Ensure</span><span class="sxs-lookup"><span data-stu-id="f725b-117">Ensure</span></span>| <span data-ttu-id="f725b-118">패키지를 설치할지 또는 제거할지를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="f725b-118">Determines whether the package is to be installed or uninstalled.</span></span>|
| <span data-ttu-id="f725b-119">MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="f725b-119">MaximumVersion</span></span>|<span data-ttu-id="f725b-120">찾으려는 패키지의 최대 허용 버전을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f725b-120">Specifies the maximum allowed version of the package that you want to find.</span></span> <span data-ttu-id="f725b-121">이 매개 변수를 추가하지 않으면 리소스는 패키지의 사용 가능한 가장 높은 버전을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="f725b-121">If you do not add this parameter, the resource finds the highest available version of the package.</span></span>|
| <span data-ttu-id="f725b-122">MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="f725b-122">MinimumVersion</span></span>|<span data-ttu-id="f725b-123">찾으려는 패키지의 최소 허용 버전을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f725b-123">Specifies the minimum allowed version of the package that you want to find.</span></span> <span data-ttu-id="f725b-124">이 매개 변수를 추가하지 않으면 리소스는 _MaximumVersion_ 매개 변수로 지정된 최대 지정 버전도 만족하는 패키지의 사용 가능한 가장 높은 버전을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="f725b-124">If you do not add this parameter, the resource finds the highest available version of the package that also satisfies any maximum specified version specified by the _MaximumVersion_ parameter.</span></span>|
| <span data-ttu-id="f725b-125">ProviderName</span><span class="sxs-lookup"><span data-stu-id="f725b-125">ProviderName</span></span>| <span data-ttu-id="f725b-126">패키지 검색 범위를 지정할 패키지 공급자 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f725b-126">Specifies a package provider name to which to scope your package search.</span></span> <span data-ttu-id="f725b-127">`Get-PackageProvider` cmdlet을 실행하여 패키지 공급자 이름을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f725b-127">You can get package provider names by running the `Get-PackageProvider` cmdlet.</span></span>|
| <span data-ttu-id="f725b-128">RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="f725b-128">RequiredVersion</span></span>| <span data-ttu-id="f725b-129">설치할 패키지의 정확한 버전을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f725b-129">Specifies the exact version of the package that you want to install.</span></span> <span data-ttu-id="f725b-130">이 매개 변수를 지정하지 않으면 이 DSC 리소스는 _MaximumVersion_ 매개 변수로 지정된 최대 버전도 만족하는 패키지의 사용 가능한 최신 버전을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="f725b-130">If you do not specify this parameter, this DSC resource installs the newest available version of the package that also satisfies any maximum version specified by the _MaximumVersion_ parameter.</span></span>|
| <span data-ttu-id="f725b-131">원본</span><span class="sxs-lookup"><span data-stu-id="f725b-131">Source</span></span>| <span data-ttu-id="f725b-132">패키지를 찾을 수 있는 패키지 원본의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f725b-132">Specifies the name of the package source where the package can be found.</span></span> <span data-ttu-id="f725b-133">이는 `Register-PackageSource` 또는 PackageManagementSource DSC 리소스에 등록된 원본 또는 URI일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f725b-133">This can either be a URI or a source registered with `Register-PackageSource` or PackageManagementSource DSC resource.</span></span>|
| <span data-ttu-id="f725b-134">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="f725b-134">SourceCredential</span></span> | <span data-ttu-id="f725b-135">지정된 패키지 공급자 또는 원본에 대한 패키지를 설치하는 권한이 있는 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f725b-135">Specifies a user account that has rights to install a package for a specified package provider or source.</span></span>|

## <a name="additional-parameters"></a><span data-ttu-id="f725b-136">추가 매개 변수</span><span class="sxs-lookup"><span data-stu-id="f725b-136">Additional Parameters</span></span>

<span data-ttu-id="f725b-137">다음 표에는 AdditionalParameters 속성에 대한 옵션이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f725b-137">The following table lists options for the AdditionalParameters property.</span></span>

| <span data-ttu-id="f725b-138">매개 변수</span><span class="sxs-lookup"><span data-stu-id="f725b-138">Parameter</span></span> | <span data-ttu-id="f725b-139">설명</span><span class="sxs-lookup"><span data-stu-id="f725b-139">Description</span></span> |
| --- | --- |
| <span data-ttu-id="f725b-140">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="f725b-140">DestinationPath</span></span>| <span data-ttu-id="f725b-141">기본 제공 Nuget 공급자와 같은 공급자에서 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f725b-141">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="f725b-142">패키지를 설치할 파일 위치를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f725b-142">Specifies a file location where you want the package to be installed.</span></span>|
| <span data-ttu-id="f725b-143">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="f725b-143">InstallationPolicy</span></span>| <span data-ttu-id="f725b-144">기본 제공 Nuget 공급자와 같은 공급자에서 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f725b-144">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="f725b-145">패키지 원본을 신뢰할 수 있는지를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="f725b-145">Determines whether you trust the package's source.</span></span> <span data-ttu-id="f725b-146">다음 중 하나: `Untrusted`, `Trusted`.</span><span class="sxs-lookup"><span data-stu-id="f725b-146">One of: `Untrusted`, `Trusted`.</span></span>|

## <a name="example"></a><span data-ttu-id="f725b-147">예제</span><span class="sxs-lookup"><span data-stu-id="f725b-147">Example</span></span>

<span data-ttu-id="f725b-148">이 예제에서는 **PackageManagement** DSC 리소스를 사용하여 **JQuery** NuGet 패키지 및 **GistProvider** PowerShell 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="f725b-148">This example installs the **JQuery** NuGet package and **GistProvider** PowerShell module using the **PackageManagement** DSC resource.</span></span> <span data-ttu-id="f725b-149">이 예제에서는 먼저 필요한 패키지 원본을 사용할 수 있는지를 확인한 다음 **JQuery** 및 **GistProvider** 패키지(각각 NuGet 및 PowerShell)의 필요한 상태를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="f725b-149">This example first ensures the required package sources are available then defines the expected state of the **JQuery** and **GistProvider** packages (NuGet and PowerShell, respectively).</span></span>

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
        SourceLocation   = "https://www.powershellgallery.com/api/v2/"
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