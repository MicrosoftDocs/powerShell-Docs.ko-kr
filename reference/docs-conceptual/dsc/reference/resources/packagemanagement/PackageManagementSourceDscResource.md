---
ms.date: 07/15/2020
ms.topic: reference
title: DSC PackageManagementSource 리소스
description: DSC PackageManagementSource 리소스
ms.openlocfilehash: 495b6548ef86f639e93b914ec8bd8ea7818ff8dd
ms.sourcegitcommit: 196c7f8cd24560cac70c88acc89909f17a86aea9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2020
ms.locfileid: "93142857"
---
# <a name="dsc-packagemanagementsource-resource"></a><span data-ttu-id="042e5-103">DSC PackageManagementSource 리소스</span><span class="sxs-lookup"><span data-stu-id="042e5-103">DSC PackageManagementSource Resource</span></span>

> <span data-ttu-id="042e5-104">적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="042e5-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="042e5-105">Windows PowerShell DSC(필요한 상태 구성)의 **PackageManagementSource** 리소스는 대상 노드에서 패키지 관리 원본을 등록하거나 등록 취소하는 메커니즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="042e5-105">The **PackageManagementSource** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to register or unregister Package Management sources on a target node.</span></span>
<span data-ttu-id="042e5-106">**이 방법으로 등록된 패키지 관리 원본은 시스템 계정이나 DSC 엔진에서 사용할 수 있는 시스템 컨텍스트에서 등록됩니다.**</span><span class="sxs-lookup"><span data-stu-id="042e5-106">**Package Management sources registered in this way are registered under the System context, usable by the System account or by the DSC engine.**</span></span> <span data-ttu-id="042e5-107">이 리소스를 사용하려면 [PowerShell 갤러리](https://PowerShellGallery.com)에서 제공하는 **PackageManagement** 모듈이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="042e5-107">This resource requires the **PackageManagement** module, available from the [PowerShell Gallery](https://PowerShellGallery.com).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="042e5-108">다음 속성 정보가 올바르려면 **PackageManagement** 모듈이 버전 1.1.7.0 이상이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="042e5-108">The **PackageManagement** module should be at least version 1.1.7.0 for the following property information to be correct.</span></span>

[!INCLUDE [Updated DSC Resources](../../../../../includes/dsc-resources.md)]

## <a name="syntax"></a><span data-ttu-id="042e5-109">구문</span><span class="sxs-lookup"><span data-stu-id="042e5-109">Syntax</span></span>

```Syntax
PackageManagementSource [String] #ResourceName
{
    Name = [string]
    ProviderName = [string]
    SourceLocation = [string]
    [ InstallationPolicy = [string]{ Trusted | Untrusted } ]
    [ SourceCredential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string]{ Absent | Present } ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="042e5-110">속성</span><span class="sxs-lookup"><span data-stu-id="042e5-110">Properties</span></span>

|<span data-ttu-id="042e5-111">속성</span><span class="sxs-lookup"><span data-stu-id="042e5-111">Property</span></span> |<span data-ttu-id="042e5-112">Description</span><span class="sxs-lookup"><span data-stu-id="042e5-112">Description</span></span> |
|---|---|
|<span data-ttu-id="042e5-113">속성</span><span class="sxs-lookup"><span data-stu-id="042e5-113">Name</span></span> |<span data-ttu-id="042e5-114">시스템에서 등록하거나 등록 취소할 패키지 원본의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="042e5-114">Specifies the name of the package source to be registered or unregistered on your system.</span></span> |
|<span data-ttu-id="042e5-115">ProviderName</span><span class="sxs-lookup"><span data-stu-id="042e5-115">ProviderName</span></span> |<span data-ttu-id="042e5-116">패키지 원본과 상호 운용할 수 있는 OneGet 공급자의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="042e5-116">Specifies the name of the OneGet provider through which you can interop with the package source.</span></span> |
|<span data-ttu-id="042e5-117">SourceLocation</span><span class="sxs-lookup"><span data-stu-id="042e5-117">SourceLocation</span></span> |<span data-ttu-id="042e5-118">패키지 원본의 URI를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="042e5-118">Specifies the URI of the package source.</span></span> |
|<span data-ttu-id="042e5-119">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="042e5-119">InstallationPolicy</span></span> |<span data-ttu-id="042e5-120">기본 제공 Nuget 공급자와 같은 공급자에서 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="042e5-120">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="042e5-121">패키지 원본을 신뢰할 수 있는지를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="042e5-121">Determines whether you trust the package's source.</span></span> <span data-ttu-id="042e5-122">다음 중 하나: **신뢰 안 함** 또는 **신뢰함** .</span><span class="sxs-lookup"><span data-stu-id="042e5-122">One of: **Untrusted** or **Trusted** .</span></span> |
|<span data-ttu-id="042e5-123">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="042e5-123">SourceCredential</span></span> |<span data-ttu-id="042e5-124">원격 소스에 있는 패키지에 액세스할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="042e5-124">Provides access to the package on a remote source.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="042e5-125">공용 속성</span><span class="sxs-lookup"><span data-stu-id="042e5-125">Common properties</span></span>

|<span data-ttu-id="042e5-126">속성</span><span class="sxs-lookup"><span data-stu-id="042e5-126">Property</span></span> |<span data-ttu-id="042e5-127">Description</span><span class="sxs-lookup"><span data-stu-id="042e5-127">Description</span></span> |
|---|---|
|<span data-ttu-id="042e5-128">DependsOn</span><span class="sxs-lookup"><span data-stu-id="042e5-128">DependsOn</span></span> |<span data-ttu-id="042e5-129">이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="042e5-129">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="042e5-130">예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 ID가 ResourceName이고 해당 형식이 ResourceType일 경우, 이 속성을 사용하기 위한 구문은 `DependsOn = "[ResourceType]ResourceName"`입니다.</span><span class="sxs-lookup"><span data-stu-id="042e5-130">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="042e5-131">Ensure</span><span class="sxs-lookup"><span data-stu-id="042e5-131">Ensure</span></span> |<span data-ttu-id="042e5-132">패키지 원본을 등록할지 또는 등록 취소할지를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="042e5-132">Determines whether the package source is to be registered or unregistered.</span></span> <span data-ttu-id="042e5-133">기본값은 **Present** 입니다.</span><span class="sxs-lookup"><span data-stu-id="042e5-133">The default value is **Present** .</span></span> |
|<span data-ttu-id="042e5-134">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="042e5-134">PsDscRunAsCredential</span></span> |<span data-ttu-id="042e5-135">전체 리소스를 실행하기 위한 자격 증명을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="042e5-135">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="042e5-136">**PsDscRunAsCredential** 공용 속성은 다른 자격 증명의 컨텍스트에서 DSC 리소스를 실행할 수 있도록 WMF 5.0에 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="042e5-136">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="042e5-137">자세한 내용은 [ DSC 리소스로 자격 증명 사용](../../../configurations/runasuser.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="042e5-137">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="042e5-138">예제</span><span class="sxs-lookup"><span data-stu-id="042e5-138">Example</span></span>

<span data-ttu-id="042e5-139">이 예제에서는 **PackageManagementSource** DSC 리소스를 사용하여 `https://nuget.org` 패키지 원본을 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="042e5-139">This example registers the `https://nuget.org` package source using the **PackageManagementSource** DSC resource.</span></span>

```powershell
Configuration PackageManagementSourceTest
{
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present"
        Name        = "MyNuget"
        ProviderName= "Nuget"
        SourceLocation   = "https://api.nuget.org/api/v3/"
        InstallationPolicy ="Trusted"
    }
}
```
