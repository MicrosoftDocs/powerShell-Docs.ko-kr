---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: DSC WindowsFeature 리소스
ms.openlocfilehash: d3384b1f45324df6b6b209f25b64d9d77615ad7f
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2020
ms.locfileid: "71954630"
---
# <a name="dsc-windowsfeature-resource"></a><span data-ttu-id="b731f-103">DSC WindowsFeature 리소스</span><span class="sxs-lookup"><span data-stu-id="b731f-103">DSC WindowsFeature Resource</span></span>

> <span data-ttu-id="b731f-104">적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="b731f-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="b731f-105">PowerShell DSC(필요한 상태 구성)의 **WindowsFeature** 리소스에서는 대상 노드에서 역할 및 기능이 추가 또는 제거되었는지를 확인하는 메커니즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b731f-105">The **WindowsFeature** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that roles and features are added or removed on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="b731f-106">구문</span><span class="sxs-lookup"><span data-stu-id="b731f-106">Syntax</span></span>

```Syntax
WindowsFeature [string] #ResourceName
{
    Name = [string]
    [ Credential = [PSCredential] ]
    [ IncludeAllSubFeature = [bool] ]
    [ LogPath = [string] ]
    [ Source = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="b731f-107">속성</span><span class="sxs-lookup"><span data-stu-id="b731f-107">Properties</span></span>

|<span data-ttu-id="b731f-108">속성</span><span class="sxs-lookup"><span data-stu-id="b731f-108">Property</span></span> |<span data-ttu-id="b731f-109">Description</span><span class="sxs-lookup"><span data-stu-id="b731f-109">Description</span></span> |
|---|---|
|<span data-ttu-id="b731f-110">속성</span><span class="sxs-lookup"><span data-stu-id="b731f-110">Name</span></span> |<span data-ttu-id="b731f-111">추가되었는지 또는 제거되었는지를 확인하려는 역할이나 기능의 이름을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b731f-111">Indicates the name of the role or feature that you want to ensure is added or removed.</span></span> <span data-ttu-id="b731f-112">이것은 [Get-WindowsFeature](/powershell/module/servermanager/Get-WindowsFeature) cmdlet의 **Name** 속성과 동일하며, 역할이나 기능의 표시 이름은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="b731f-112">This is the same as the **Name** property from the [Get-WindowsFeature](/powershell/module/servermanager/Get-WindowsFeature) cmdlet, and not the display name of the role or feature.</span></span> |
|<span data-ttu-id="b731f-113">자격 증명</span><span class="sxs-lookup"><span data-stu-id="b731f-113">Credential</span></span> |<span data-ttu-id="b731f-114">역할 또는 기능을 추가 또는 제거하는 데 사용할 자격 증명을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b731f-114">Indicates the credentials to use to add or remove the role or feature.</span></span> |
|<span data-ttu-id="b731f-115">IncludeAllSubFeature</span><span class="sxs-lookup"><span data-stu-id="b731f-115">IncludeAllSubFeature</span></span> |<span data-ttu-id="b731f-116">**Name** 속성으로 지정하는 기능의 상태와 함께 모든 필수 하위 기능의 상태를 보증하려면 이 속성을 `$true`로 설정하세요.</span><span class="sxs-lookup"><span data-stu-id="b731f-116">Set this property to `$true` to ensure the state of all required subfeatures with the state of the feature you specify with the **Name** property.</span></span> |
|<span data-ttu-id="b731f-117">LogPath</span><span class="sxs-lookup"><span data-stu-id="b731f-117">LogPath</span></span> |<span data-ttu-id="b731f-118">리소스 공급자가 작업을 로그하기를 원하는 로그 파일의 경로를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b731f-118">Indicates the path to a log file where you want the resource provider to log the operation.</span></span> |
|<span data-ttu-id="b731f-119">원본</span><span class="sxs-lookup"><span data-stu-id="b731f-119">Source</span></span> |<span data-ttu-id="b731f-120">필요한 경우 설치에 사용할 소스 파일의 위치를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b731f-120">Indicates the location of the source file to use for installation, if necessary.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="b731f-121">공용 속성</span><span class="sxs-lookup"><span data-stu-id="b731f-121">Common properties</span></span>

|<span data-ttu-id="b731f-122">속성</span><span class="sxs-lookup"><span data-stu-id="b731f-122">Property</span></span> |<span data-ttu-id="b731f-123">Description</span><span class="sxs-lookup"><span data-stu-id="b731f-123">Description</span></span> |
|---|---|
|<span data-ttu-id="b731f-124">DependsOn</span><span class="sxs-lookup"><span data-stu-id="b731f-124">DependsOn</span></span> |<span data-ttu-id="b731f-125">이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b731f-125">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="b731f-126">예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 ID가 ResourceName이고 해당 형식이 ResourceType일 경우, 이 속성을 사용하기 위한 구문은 `DependsOn = "[ResourceType]ResourceName"`입니다.</span><span class="sxs-lookup"><span data-stu-id="b731f-126">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="b731f-127">Ensure</span><span class="sxs-lookup"><span data-stu-id="b731f-127">Ensure</span></span> |<span data-ttu-id="b731f-128">역할이나 기능이 추가되었는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b731f-128">Indicates if the role or feature is added.</span></span> <span data-ttu-id="b731f-129">역할이나 기능이 추가되도록 하려면 이 속성을 **Present**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="b731f-129">To ensure that the role or feature is added, set this property to **Present**.</span></span> <span data-ttu-id="b731f-130">역할이나 기능이 제거되도록 하려면 이 속성을 **Absent**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="b731f-130">To ensure that the role or feature is removed, set the property to **Absent**.</span></span> <span data-ttu-id="b731f-131">기본값은 **Present**입니다.</span><span class="sxs-lookup"><span data-stu-id="b731f-131">The default value is **Present**.</span></span> |
|<span data-ttu-id="b731f-132">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="b731f-132">PsDscRunAsCredential</span></span> |<span data-ttu-id="b731f-133">전체 리소스를 실행하기 위한 자격 증명을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="b731f-133">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="b731f-134">**PsDscRunAsCredential** 공용 속성은 다른 자격 증명의 컨텍스트에서 DSC 리소스를 실행할 수 있도록 WMF 5.0에 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b731f-134">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="b731f-135">자세한 내용은 [ DSC 리소스로 자격 증명 사용](../../../configurations/runasuser.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b731f-135">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="b731f-136">예제</span><span class="sxs-lookup"><span data-stu-id="b731f-136">Example</span></span>

```powershell
WindowsFeature RoleExample
{
    Ensure = "Present"
    # Alternatively, to ensure the role is uninstalled, set Ensure to "Absent"
    Name = "Web-Server" # Use the Name property from Get-WindowsFeature
}
```