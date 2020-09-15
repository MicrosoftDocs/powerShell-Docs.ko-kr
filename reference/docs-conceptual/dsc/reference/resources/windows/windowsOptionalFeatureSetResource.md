---
ms.date: 07/16/2020
keywords: dsc,powershell,configuration,setup
title: DSC WindowsOptionalFeatureSet 리소스
ms.openlocfilehash: e4f88f1cae6d7ddb3596ab4f27eb3766259f1a31
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464165"
---
# <a name="dsc-windowsoptionalfeatureset-resource"></a><span data-ttu-id="1e806-103">DSC WindowsOptionalFeatureSet 리소스</span><span class="sxs-lookup"><span data-stu-id="1e806-103">DSC WindowsOptionalFeatureSet Resource</span></span>

> <span data-ttu-id="1e806-104">적용 대상: Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="1e806-104">Applies To: Windows PowerShell 5.x</span></span>

<span data-ttu-id="1e806-105">Windows PowerShell DSC(필요한 상태 구성)의 **WindowsOptionalFeatureSet** 리소스에서는 대상 노드에서 선택적 기능을 사용할 수 있도록 설정하는 메커니즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1e806-105">The **WindowsOptionalFeatureSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that optional features are enabled on a target node.</span></span> <span data-ttu-id="1e806-106">이 리소스는 **Name** 속성에 지정된 각 기능에 대해 [WindowsOptionalFeature 리소스](windowsOptionalFeatureResource.md)를 호출하는 [복합 리소스](../../../resources/authoringResourceComposite.md)입니다.</span><span class="sxs-lookup"><span data-stu-id="1e806-106">This resource is a [composite resource](../../../resources/authoringResourceComposite.md) that calls the [WindowsOptionalFeature resource](windowsOptionalFeatureResource.md) for each feature specified in the **Name** property.</span></span>

<span data-ttu-id="1e806-107">여러 선택적 Windows 기능을 동일한 상태로 구성하려는 경우 이 리소스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1e806-107">Use this resource when you want to configure a number of Windows optional features to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="1e806-108">구문</span><span class="sxs-lookup"><span data-stu-id="1e806-108">Syntax</span></span>

```Syntax
WindowsOptionalFeatureSet [string] #ResourceName
{
    Name = [string[]]
    [ RemoveFilesOnDisable = [bool] ]
    [ LogPath = [string] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Enable | Disable }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="1e806-109">속성</span><span class="sxs-lookup"><span data-stu-id="1e806-109">Properties</span></span>

|<span data-ttu-id="1e806-110">속성</span><span class="sxs-lookup"><span data-stu-id="1e806-110">Property</span></span> |<span data-ttu-id="1e806-111">Description</span><span class="sxs-lookup"><span data-stu-id="1e806-111">Description</span></span> |
|---|---|
|<span data-ttu-id="1e806-112">속성</span><span class="sxs-lookup"><span data-stu-id="1e806-112">Name</span></span> |<span data-ttu-id="1e806-113">사용 또는 사용하지 않도록 설정하려는 기능의 이름을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1e806-113">Indicates the name of the features that you want to ensure are enabled or disabled.</span></span> |
|<span data-ttu-id="1e806-114">NoWindowsUpdateCheck</span><span class="sxs-lookup"><span data-stu-id="1e806-114">NoWindowsUpdateCheck</span></span> |<span data-ttu-id="1e806-115">기능을 사용하도록 설정하기 위해 원본 파일을 검색할 때 DISM에서 WU(Windows 업데이트)에 연결하는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1e806-115">Specifies whether DISM contacts Windows Update (WU) when searching for the source files to enable features.</span></span> <span data-ttu-id="1e806-116">`$true`이면 DISM에서 WU에 연결하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1e806-116">If `$true`, DISM does not contact WU.</span></span> |
|<span data-ttu-id="1e806-117">RemoveFilesOnDisable</span><span class="sxs-lookup"><span data-stu-id="1e806-117">RemoveFilesOnDisable</span></span> |<span data-ttu-id="1e806-118">`$true`Ensure\*\*가 **Absent**로 설정되어 있을 경우 \*\*로 설정하여 기능과 관련된 모든 파일을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="1e806-118">Set to `$true` to remove all files associated with the features when **Ensure** is set to **Absent**.</span></span> |
|<span data-ttu-id="1e806-119">LogLevel</span><span class="sxs-lookup"><span data-stu-id="1e806-119">LogLevel</span></span> |<span data-ttu-id="1e806-120">로그에 표시되는 최대 출력 수준입니다.</span><span class="sxs-lookup"><span data-stu-id="1e806-120">The maximum output level shown in the logs.</span></span> <span data-ttu-id="1e806-121">허용되는 값은 **ErrorsOnly**, **ErrorsAndWarning** 및 **ErrorsAndWarningAndInformation**.</span><span class="sxs-lookup"><span data-stu-id="1e806-121">The accepted values are: **ErrorsOnly**, **ErrorsAndWarning**, and **ErrorsAndWarningAndInformation**.</span></span> |
|<span data-ttu-id="1e806-122">LogPath</span><span class="sxs-lookup"><span data-stu-id="1e806-122">LogPath</span></span> |<span data-ttu-id="1e806-123">리소스 공급자가 작업을 기록할 로그 파일의 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="1e806-123">The path to a log file where you want the resource provider to log the operation.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="1e806-124">공용 속성</span><span class="sxs-lookup"><span data-stu-id="1e806-124">Common properties</span></span>

|<span data-ttu-id="1e806-125">속성</span><span class="sxs-lookup"><span data-stu-id="1e806-125">Property</span></span> |<span data-ttu-id="1e806-126">Description</span><span class="sxs-lookup"><span data-stu-id="1e806-126">Description</span></span> |
|---|---|
|<span data-ttu-id="1e806-127">DependsOn</span><span class="sxs-lookup"><span data-stu-id="1e806-127">DependsOn</span></span> |<span data-ttu-id="1e806-128">이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1e806-128">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="1e806-129">예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 ID가 ResourceName이고 해당 형식이 ResourceType일 경우, 이 속성을 사용하기 위한 구문은 `DependsOn = "[ResourceType]ResourceName"`입니다.</span><span class="sxs-lookup"><span data-stu-id="1e806-129">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="1e806-130">Ensure</span><span class="sxs-lookup"><span data-stu-id="1e806-130">Ensure</span></span> |<span data-ttu-id="1e806-131">기능을 사용하도록 설정할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1e806-131">Specifies whether the features are enabled.</span></span> <span data-ttu-id="1e806-132">기능을 사용하도록 설정하려면 이 속성을 **Enable**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="1e806-132">To ensure that the features are enabled, set this property to **Enable**.</span></span> <span data-ttu-id="1e806-133">기능을 사용하지 않도록 설정하려면 이 속성을 **Disable**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="1e806-133">To ensure that the features are disabled, set the property to **Disable**.</span></span> <span data-ttu-id="1e806-134">기본값은 **Enable**입니다.</span><span class="sxs-lookup"><span data-stu-id="1e806-134">The default value is **Enable**.</span></span> |
|<span data-ttu-id="1e806-135">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="1e806-135">PsDscRunAsCredential</span></span> |<span data-ttu-id="1e806-136">전체 리소스를 실행하기 위한 자격 증명을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="1e806-136">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="1e806-137">**PsDscRunAsCredential** 공용 속성은 다른 자격 증명의 컨텍스트에서 DSC 리소스를 실행할 수 있도록 WMF 5.0에 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1e806-137">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="1e806-138">자세한 내용은 [ DSC 리소스로 자격 증명 사용](../../../configurations/runasuser.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1e806-138">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>
