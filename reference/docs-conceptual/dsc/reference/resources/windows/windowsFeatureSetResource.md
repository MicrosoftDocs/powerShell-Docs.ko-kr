---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: DSC WindowsFeatureSet 리소스
ms.openlocfilehash: 1758d248dde4fdee57bd01c157a3f9a8340d6194
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2020
ms.locfileid: "71952960"
---
# <a name="dsc-windowsfeatureset-resource"></a><span data-ttu-id="c98fa-103">DSC WindowsFeatureSet 리소스</span><span class="sxs-lookup"><span data-stu-id="c98fa-103">DSC WindowsFeatureSet Resource</span></span>

> <span data-ttu-id="c98fa-104">적용 대상: Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="c98fa-104">Applies To: Windows PowerShell 5.x</span></span>

<span data-ttu-id="c98fa-105">PowerShell DSC(필요한 상태 구성)의 **WindowsFeatureSet** 리소스에서는 대상 노드에서 역할 및 기능을 추가 또는 제거하는 메커니즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c98fa-105">The **WindowsFeatureSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that roles and features are added or removed on a target node.</span></span> <span data-ttu-id="c98fa-106">이 리소스는 **Name** 속성에 지정된 각 기능에 대해 [WindowsFeature 리소스](windowsfeatureResource.md)를 호출하는 [복합 리소스](../../../resources/authoringResourceComposite.md)입니다.</span><span class="sxs-lookup"><span data-stu-id="c98fa-106">This resource is a [composite resource](../../../resources/authoringResourceComposite.md) that calls the [WindowsFeature resource](windowsfeatureResource.md) for each feature specified in the **Name** property.</span></span>

<span data-ttu-id="c98fa-107">여러 Windows 기능을 동일한 상태로 구성하려는 경우 이 리소스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c98fa-107">Use this resource when you want to configure a number of Windows Features to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="c98fa-108">구문</span><span class="sxs-lookup"><span data-stu-id="c98fa-108">Syntax</span></span>

```Syntax
WindowsFeatureSet [string] #ResourceName
{
    Name = [string[]]
    [ Source = [string] ]
    [ IncludeAllSubFeature = [Boolean] ]
    [ Credential = [PSCredential] ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="c98fa-109">속성</span><span class="sxs-lookup"><span data-stu-id="c98fa-109">Properties</span></span>

|  <span data-ttu-id="c98fa-110">속성</span><span class="sxs-lookup"><span data-stu-id="c98fa-110">Property</span></span>  |  <span data-ttu-id="c98fa-111">Description</span><span class="sxs-lookup"><span data-stu-id="c98fa-111">Description</span></span>   |
|---|---|
|<span data-ttu-id="c98fa-112">속성</span><span class="sxs-lookup"><span data-stu-id="c98fa-112">Name</span></span> |<span data-ttu-id="c98fa-113">추가 또는 제거하려는 역할이나 기능의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="c98fa-113">The names of the roles or features that you want to ensure are added or removed.</span></span> <span data-ttu-id="c98fa-114">이것은 [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature?view=winserver2012r2-ps) cmdlet의 **Name** 속성과 동일하며, 역할이나 기능의 표시 이름은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="c98fa-114">This is the same as the **Name** property of the [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature?view=winserver2012r2-ps) cmdlet, and not the display name of the roles or features.</span></span> |
|<span data-ttu-id="c98fa-115">원본</span><span class="sxs-lookup"><span data-stu-id="c98fa-115">Source</span></span> |<span data-ttu-id="c98fa-116">필요한 경우 설치에 사용할 소스 파일의 위치를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c98fa-116">Indicates the location of the source file to use for installation, if necessary.</span></span> |
|<span data-ttu-id="c98fa-117">IncludeAllSubFeature</span><span class="sxs-lookup"><span data-stu-id="c98fa-117">IncludeAllSubFeature</span></span> |<span data-ttu-id="c98fa-118">**Name** 속성에 지정하는 기능과 함께 모든 필수 하위 기능을 포함하려면 이 속성을 `$true`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c98fa-118">Set this property to `$true` to include all required subfeatures with of the features you specify with the **Name** property.</span></span> |
|<span data-ttu-id="c98fa-119">자격 증명</span><span class="sxs-lookup"><span data-stu-id="c98fa-119">Credential</span></span> |<span data-ttu-id="c98fa-120">역할 또는 기능을 추가 또는 제거하는 데 사용할 자격 증명입니다.</span><span class="sxs-lookup"><span data-stu-id="c98fa-120">The credentials to use to add or remove the roles or features.</span></span> |
|<span data-ttu-id="c98fa-121">LogPath</span><span class="sxs-lookup"><span data-stu-id="c98fa-121">LogPath</span></span> |<span data-ttu-id="c98fa-122">리소스 공급자가 작업을 기록할 로그 파일의 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="c98fa-122">The path to a log file where you want the resource provider to log the operation.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="c98fa-123">공용 속성</span><span class="sxs-lookup"><span data-stu-id="c98fa-123">Common properties</span></span>

|<span data-ttu-id="c98fa-124">속성</span><span class="sxs-lookup"><span data-stu-id="c98fa-124">Property</span></span> |<span data-ttu-id="c98fa-125">Description</span><span class="sxs-lookup"><span data-stu-id="c98fa-125">Description</span></span> |
|---|---|
|<span data-ttu-id="c98fa-126">DependsOn</span><span class="sxs-lookup"><span data-stu-id="c98fa-126">DependsOn</span></span> |<span data-ttu-id="c98fa-127">이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c98fa-127">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="c98fa-128">예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 ID가 ResourceName이고 해당 형식이 ResourceType일 경우, 이 속성을 사용하기 위한 구문은 `DependsOn = "[ResourceType]ResourceName"`입니다.</span><span class="sxs-lookup"><span data-stu-id="c98fa-128">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="c98fa-129">Ensure</span><span class="sxs-lookup"><span data-stu-id="c98fa-129">Ensure</span></span> |<span data-ttu-id="c98fa-130">역할이나 기능이 추가되는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c98fa-130">Indicates whether the roles or features are added.</span></span> <span data-ttu-id="c98fa-131">역할이나 기능이 추가되도록 하려면 이 속성을 **Present**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c98fa-131">To ensure that the roles or features are added, set this property to **Present**.</span></span> <span data-ttu-id="c98fa-132">역할이나 기능이 제거되도록 하려면 이 속성을 **Absent**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c98fa-132">To ensure that the roles or features are removed, set the property to **Absent**.</span></span> <span data-ttu-id="c98fa-133">기본값은 **Present**입니다.</span><span class="sxs-lookup"><span data-stu-id="c98fa-133">The default value is **Present**.</span></span> |
|<span data-ttu-id="c98fa-134">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="c98fa-134">PsDscRunAsCredential</span></span> |<span data-ttu-id="c98fa-135">전체 리소스를 실행하기 위한 자격 증명을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c98fa-135">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="c98fa-136">**PsDscRunAsCredential** 공용 속성은 다른 자격 증명의 컨텍스트에서 DSC 리소스를 실행할 수 있도록 WMF 5.0에 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c98fa-136">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="c98fa-137">자세한 내용은 [ DSC 리소스로 자격 증명 사용](../../../configurations/runasuser.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c98fa-137">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="c98fa-138">예제</span><span class="sxs-lookup"><span data-stu-id="c98fa-138">Example</span></span>

<span data-ttu-id="c98fa-139">다음 구성을 사용하면 **Web-Server**(IIS) 및 **SMTP 서버** 기능과 각각의 모든 하위 기능이 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="c98fa-139">The following configuration ensures that the **Web-Server** (IIS) and **SMTP Server** features, and all subfeatures of each, are installed.</span></span>

```powershell
configuration FeatureSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        WindowsFeatureSet WindowsFeatureSetExample
        {
            Name                    = @("SMTP-Server", "Web-Server")
            Ensure                  = 'Present'
            IncludeAllSubFeature    = $true
        }
    }
}
```