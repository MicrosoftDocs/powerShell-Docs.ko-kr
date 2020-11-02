---
ms.date: 08/28/2020
ms.topic: reference
title: DSC WindowsOptionalFeature 리소스
description: DSC WindowsOptionalFeature 리소스
ms.openlocfilehash: 1c7e888ea49b0d1710cc22c975cb618999238f67
ms.sourcegitcommit: 196c7f8cd24560cac70c88acc89909f17a86aea9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2020
ms.locfileid: "93143061"
---
# <a name="dsc-windowsoptionalfeature-resource"></a><span data-ttu-id="26bd0-103">DSC WindowsOptionalFeature 리소스</span><span class="sxs-lookup"><span data-stu-id="26bd0-103">DSC WindowsOptionalFeature Resource</span></span>

> <span data-ttu-id="26bd0-104">적용 대상: Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="26bd0-104">Applies To: Windows PowerShell 5.x</span></span>

<span data-ttu-id="26bd0-105">PowerShell DSC(필요한 상태 구성)의 **WindowsOptionalFeature** 리소스에서는 대상 노드에서 선택적 기능을 사용할 수 있도록 설정하는 메커니즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="26bd0-105">The **WindowsOptionalFeature** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that optional features are enabled on a target node.</span></span>

> [!NOTE]
> <span data-ttu-id="26bd0-106">**WindowsOptionalFeature** 는 Windows 10과 같은 Windows 클라이언트 머신에서만 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="26bd0-106">**WindowsOptionalFeature** only works on Windows client machines like Windows 10.</span></span>

[!INCLUDE [Updated DSC Resources](../../../../../includes/dsc-resources.md)]

## <a name="syntax"></a><span data-ttu-id="26bd0-107">구문</span><span class="sxs-lookup"><span data-stu-id="26bd0-107">Syntax</span></span>

```Syntax
WindowsOptionalFeature [string] #ResourceName
{
    Name = [string]
    [ NoWindowsUpdateCheck = [bool] ]
    [ RemoveFilesOnDisable = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Enable | Disable }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="26bd0-108">속성</span><span class="sxs-lookup"><span data-stu-id="26bd0-108">Properties</span></span>

|<span data-ttu-id="26bd0-109">속성</span><span class="sxs-lookup"><span data-stu-id="26bd0-109">Property</span></span> |<span data-ttu-id="26bd0-110">설명</span><span class="sxs-lookup"><span data-stu-id="26bd0-110">Description</span></span> |
|---|---|
|<span data-ttu-id="26bd0-111">이름</span><span class="sxs-lookup"><span data-stu-id="26bd0-111">Name</span></span> |<span data-ttu-id="26bd0-112">사용 또는 사용하지 않도록 설정하려는 기능의 이름을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="26bd0-112">Indicates the name of the feature that you want to ensure is enabled or disabled.</span></span> |
|<span data-ttu-id="26bd0-113">NoWindowsUpdateCheck</span><span class="sxs-lookup"><span data-stu-id="26bd0-113">NoWindowsUpdateCheck</span></span> |<span data-ttu-id="26bd0-114">기능을 사용하도록 설정하기 위해 원본 파일을 검색할 때 DISM에서 WU(Windows 업데이트)에 연결하는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="26bd0-114">Specifies whether DISM contacts Windows Update (WU) when searching for the source files to enable a feature.</span></span> <span data-ttu-id="26bd0-115">`$true`이면 DISM에서 WU에 연결하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="26bd0-115">If `$true`, DISM does not contact WU.</span></span> |
|<span data-ttu-id="26bd0-116">RemoveFilesOnDisable</span><span class="sxs-lookup"><span data-stu-id="26bd0-116">RemoveFilesOnDisable</span></span> |<span data-ttu-id="26bd0-117">`$true`Ensure **가** Absent **로 설정되어 있을 경우** 로 설정하여 기능과 관련된 모든 파일을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="26bd0-117">Set to `$true` to remove all files associated with the feature when **Ensure** is set to **Absent** .</span></span> |
|<span data-ttu-id="26bd0-118">LogLevel</span><span class="sxs-lookup"><span data-stu-id="26bd0-118">LogLevel</span></span> |<span data-ttu-id="26bd0-119">로그에 표시되는 최대 출력 수준입니다.</span><span class="sxs-lookup"><span data-stu-id="26bd0-119">The maximum output level shown in the logs.</span></span> <span data-ttu-id="26bd0-120">허용되는 값은 **ErrorsOnly** , **ErrorsAndWarning** 및 **ErrorsAndWarningAndInformation** .</span><span class="sxs-lookup"><span data-stu-id="26bd0-120">The accepted values are: **ErrorsOnly** , **ErrorsAndWarning** , and **ErrorsAndWarningAndInformation** .</span></span> |
|<span data-ttu-id="26bd0-121">LogPath</span><span class="sxs-lookup"><span data-stu-id="26bd0-121">LogPath</span></span> |<span data-ttu-id="26bd0-122">리소스 공급자가 작업을 기록할 로그 파일의 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="26bd0-122">The path to a log file where you want the resource provider to log the operation.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="26bd0-123">공용 속성</span><span class="sxs-lookup"><span data-stu-id="26bd0-123">Common properties</span></span>

|<span data-ttu-id="26bd0-124">속성</span><span class="sxs-lookup"><span data-stu-id="26bd0-124">Property</span></span> |<span data-ttu-id="26bd0-125">Description</span><span class="sxs-lookup"><span data-stu-id="26bd0-125">Description</span></span> |
|---|---|
|<span data-ttu-id="26bd0-126">DependsOn</span><span class="sxs-lookup"><span data-stu-id="26bd0-126">DependsOn</span></span> |<span data-ttu-id="26bd0-127">이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="26bd0-127">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="26bd0-128">예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 ID가 ResourceName이고 해당 형식이 ResourceType일 경우, 이 속성을 사용하기 위한 구문은 `DependsOn = "[ResourceType]ResourceName"`입니다.</span><span class="sxs-lookup"><span data-stu-id="26bd0-128">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="26bd0-129">Ensure</span><span class="sxs-lookup"><span data-stu-id="26bd0-129">Ensure</span></span> |<span data-ttu-id="26bd0-130">기능의 사용 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="26bd0-130">Specifies whether the feature is enabled.</span></span> <span data-ttu-id="26bd0-131">기능을 사용하도록 설정하려면 이 속성을 _Enable_ 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="26bd0-131">To ensure that the feature is enabled, set this property to _Enable_ .</span></span> <span data-ttu-id="26bd0-132">기능을 사용하지 않도록 설정하려면 이 속성을 _Disable_ 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="26bd0-132">To ensure that the feature is disabled, set the property to _Disable_ .</span></span> <span data-ttu-id="26bd0-133">기본값은 _Enable_ 입니다.</span><span class="sxs-lookup"><span data-stu-id="26bd0-133">The default value is _Enable_ .</span></span> |
|<span data-ttu-id="26bd0-134">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="26bd0-134">PsDscRunAsCredential</span></span> |<span data-ttu-id="26bd0-135">전체 리소스를 실행하기 위한 자격 증명을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="26bd0-135">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="26bd0-136">**PsDscRunAsCredential** 공용 속성은 다른 자격 증명의 컨텍스트에서 DSC 리소스를 실행할 수 있도록 WMF 5.0에 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="26bd0-136">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="26bd0-137">자세한 내용은 [ DSC 리소스로 자격 증명 사용](../../../configurations/runasuser.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="26bd0-137">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>
