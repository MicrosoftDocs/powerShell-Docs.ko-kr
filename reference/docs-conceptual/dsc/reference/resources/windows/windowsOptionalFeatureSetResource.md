---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: DSC WindowsOptionalFeatureSet 리소스
ms.openlocfilehash: f378006a6c362ee9890d70dd76fb552dd262a544
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2020
ms.locfileid: "71952870"
---
# <a name="dsc-windowsoptionalfeatureset-resource"></a><span data-ttu-id="88c2b-103">DSC WindowsOptionalFeatureSet 리소스</span><span class="sxs-lookup"><span data-stu-id="88c2b-103">DSC WindowsOptionalFeatureSet Resource</span></span>

> <span data-ttu-id="88c2b-104">적용 대상: Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="88c2b-104">Applies To: Windows PowerShell 5.x</span></span>

<span data-ttu-id="88c2b-105">Windows PowerShell DSC(필요한 상태 구성)의 **WindowsOptionalFeatureSet** 리소스에서는 대상 노드에서 선택적 기능을 사용할 수 있도록 설정하는 메커니즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="88c2b-105">The **WindowsOptionalFeatureSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that optional features are enabled on a target node.</span></span> <span data-ttu-id="88c2b-106">이 리소스는 **Name** 속성에 지정된 각 기능에 대해 [WindowsOptionalFeature 리소스](windowsOptionalFeatureResource.md)를 호출하는 [복합 리소스](../../../resources/authoringResourceComposite.md)입니다.</span><span class="sxs-lookup"><span data-stu-id="88c2b-106">This resource is a [composite resource](../../../resources/authoringResourceComposite.md) that calls the [WindowsOptionalFeature resource](windowsOptionalFeatureResource.md) for each feature specified in the **Name** property.</span></span>

<span data-ttu-id="88c2b-107">여러 선택적 Windows 기능을 동일한 상태로 구성하려는 경우 이 리소스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="88c2b-107">Use this resource when you want to configure a number of Windows optional features to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="88c2b-108">구문</span><span class="sxs-lookup"><span data-stu-id="88c2b-108">Syntax</span></span>

```Syntax
WindowsOptionalFeatureSet [string] #ResourceName
{
    Name = [string[]]
    [ Source = [string] ]
    [ RemoveFilesOnDisable = [bool] ]
    [ LogPath = [string] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Enable | Disable }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="88c2b-109">속성</span><span class="sxs-lookup"><span data-stu-id="88c2b-109">Properties</span></span>

|<span data-ttu-id="88c2b-110">속성</span><span class="sxs-lookup"><span data-stu-id="88c2b-110">Property</span></span> |<span data-ttu-id="88c2b-111">Description</span><span class="sxs-lookup"><span data-stu-id="88c2b-111">Description</span></span> |
|---|---|
|<span data-ttu-id="88c2b-112">속성</span><span class="sxs-lookup"><span data-stu-id="88c2b-112">Name</span></span> |<span data-ttu-id="88c2b-113">사용 또는 사용하지 않도록 설정하려는 기능의 이름을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="88c2b-113">Indicates the name of the features that you want to ensure are enabled or disabled.</span></span> |
|<span data-ttu-id="88c2b-114">원본</span><span class="sxs-lookup"><span data-stu-id="88c2b-114">Source</span></span> |<span data-ttu-id="88c2b-115">구현되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="88c2b-115">Not implemented.</span></span> |
|<span data-ttu-id="88c2b-116">NoWindowsUpdateCheck</span><span class="sxs-lookup"><span data-stu-id="88c2b-116">NoWindowsUpdateCheck</span></span> |<span data-ttu-id="88c2b-117">기능을 사용하도록 설정하기 위해 원본 파일을 검색할 때 DISM에서 WU(Windows 업데이트)에 연결하는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="88c2b-117">Specifies whether DISM contacts Windows Update (WU) when searching for the source files to enable features.</span></span> <span data-ttu-id="88c2b-118">`$true`이면 DISM에서 WU에 연결하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="88c2b-118">If `$true`, DISM does not contact WU.</span></span> |
|<span data-ttu-id="88c2b-119">RemoveFilesOnDisable</span><span class="sxs-lookup"><span data-stu-id="88c2b-119">RemoveFilesOnDisable</span></span> |<span data-ttu-id="88c2b-120">`$true`Ensure**가** Absent**로 설정되어 있을 경우** 로 설정하여 기능과 관련된 모든 파일을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="88c2b-120">Set to `$true` to remove all files associated with the features when **Ensure** is set to **Absent**.</span></span> |
|<span data-ttu-id="88c2b-121">LogLevel</span><span class="sxs-lookup"><span data-stu-id="88c2b-121">LogLevel</span></span> |<span data-ttu-id="88c2b-122">로그에 표시되는 최대 출력 수준입니다.</span><span class="sxs-lookup"><span data-stu-id="88c2b-122">The maximum output level shown in the logs.</span></span> <span data-ttu-id="88c2b-123">허용되는 값은 **ErrorsOnly**, **ErrorsAndWarning** 및 **ErrorsAndWarningAndInformation**.</span><span class="sxs-lookup"><span data-stu-id="88c2b-123">The accepted values are: **ErrorsOnly**, **ErrorsAndWarning**, and **ErrorsAndWarningAndInformation**.</span></span> |
|<span data-ttu-id="88c2b-124">LogPath</span><span class="sxs-lookup"><span data-stu-id="88c2b-124">LogPath</span></span> |<span data-ttu-id="88c2b-125">리소스 공급자가 작업을 기록할 로그 파일의 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="88c2b-125">The path to a log file where you want the resource provider to log the operation.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="88c2b-126">공용 속성</span><span class="sxs-lookup"><span data-stu-id="88c2b-126">Common properties</span></span>

|<span data-ttu-id="88c2b-127">속성</span><span class="sxs-lookup"><span data-stu-id="88c2b-127">Property</span></span> |<span data-ttu-id="88c2b-128">Description</span><span class="sxs-lookup"><span data-stu-id="88c2b-128">Description</span></span> |
|---|---|
|<span data-ttu-id="88c2b-129">DependsOn</span><span class="sxs-lookup"><span data-stu-id="88c2b-129">DependsOn</span></span> |<span data-ttu-id="88c2b-130">이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="88c2b-130">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="88c2b-131">예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 ID가 ResourceName이고 해당 형식이 ResourceType일 경우, 이 속성을 사용하기 위한 구문은 `DependsOn = "[ResourceType]ResourceName"`입니다.</span><span class="sxs-lookup"><span data-stu-id="88c2b-131">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="88c2b-132">Ensure</span><span class="sxs-lookup"><span data-stu-id="88c2b-132">Ensure</span></span> |<span data-ttu-id="88c2b-133">기능을 사용하도록 설정할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="88c2b-133">Specifies whether the features are enabled.</span></span> <span data-ttu-id="88c2b-134">기능을 사용하도록 설정하려면 이 속성을 **Enable**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="88c2b-134">To ensure that the features are enabled, set this property to **Enable**.</span></span> <span data-ttu-id="88c2b-135">기능을 사용하지 않도록 설정하려면 이 속성을 **Disable**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="88c2b-135">To ensure that the features are disabled, set the property to **Disable**.</span></span> <span data-ttu-id="88c2b-136">기본값은 **Enable**입니다.</span><span class="sxs-lookup"><span data-stu-id="88c2b-136">The default value is **Enable**.</span></span> |
|<span data-ttu-id="88c2b-137">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="88c2b-137">PsDscRunAsCredential</span></span> |<span data-ttu-id="88c2b-138">전체 리소스를 실행하기 위한 자격 증명을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="88c2b-138">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="88c2b-139">**PsDscRunAsCredential** 공용 속성은 다른 자격 증명의 컨텍스트에서 DSC 리소스를 실행할 수 있도록 WMF 5.0에 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="88c2b-139">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="88c2b-140">자세한 내용은 [ DSC 리소스로 자격 증명 사용](../../../configurations/runasuser.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="88c2b-140">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>