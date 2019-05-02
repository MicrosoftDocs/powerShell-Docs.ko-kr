---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: DSC WindowsOptionalFeatureSet 리소스
ms.openlocfilehash: c27d026e01bbb443a82112e37f1d199fb3482e49
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076976"
---
# <a name="dsc-windowsoptionalfeatureset-resource"></a><span data-ttu-id="d9aad-103">DSC WindowsOptionalFeatureSet 리소스</span><span class="sxs-lookup"><span data-stu-id="d9aad-103">DSC WindowsOptionalFeatureSet Resource</span></span>

> <span data-ttu-id="d9aad-104">적용 대상: Windows Powershell 5.0</span><span class="sxs-lookup"><span data-stu-id="d9aad-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="d9aad-105">Windows PowerShell DSC(Desired State Configuration)의 **WindowsOptionalFeatureSet** 리소스에서는 대상 노드에서 선택적 기능을 사용할 수 있도록 설정하는 메커니즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d9aad-105">The **WindowsOptionalFeatureSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that optional features are enabled on a target node.</span></span>
<span data-ttu-id="d9aad-106">이 리소스는 `Name` 속성에 지정된 각 기능에 대해 [WindowsOptionalFeature 리소스](windowsOptionalFeatureResource.md)를 호출하는 [복합 리소스](../../../resources/authoringResourceComposite.md)입니다.</span><span class="sxs-lookup"><span data-stu-id="d9aad-106">This resource is a [composite resource](../../../resources/authoringResourceComposite.md) that calls the [WindowsOptionalFeature resource](windowsOptionalFeatureResource.md) for each feature specified in the `Name` property.</span></span>

<span data-ttu-id="d9aad-107">여러 선택적 Windows 기능을 동일한 상태로 구성하려는 경우 이 리소스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d9aad-107">Use this resource when you want to configure a number of Windows optional features to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="d9aad-108">구문</span><span class="sxs-lookup"><span data-stu-id="d9aad-108">Syntax</span></span>

```
WindowsOptionalFeature [string] #ResourceName
{
    Name = [string[]]
    [ Ensure = [string] { Enable | Disable }  ]
    [ Source = [string] ]
    [ RemoveFilesOnDisable = [bool] ]
    [ LogPath = [string] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ DependsOn = [string[]] ]

}
```

## <a name="properties"></a><span data-ttu-id="d9aad-109">속성</span><span class="sxs-lookup"><span data-stu-id="d9aad-109">Properties</span></span>

|  <span data-ttu-id="d9aad-110">속성</span><span class="sxs-lookup"><span data-stu-id="d9aad-110">Property</span></span>  |  <span data-ttu-id="d9aad-111">설명</span><span class="sxs-lookup"><span data-stu-id="d9aad-111">Description</span></span>   |
|---|---|
| <span data-ttu-id="d9aad-112">이름</span><span class="sxs-lookup"><span data-stu-id="d9aad-112">Name</span></span>| <span data-ttu-id="d9aad-113">사용 또는 사용하지 않도록 설정하려는 기능의 이름을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d9aad-113">Indicates the name of the features that you want to ensure are enabled or disabled.</span></span>|
| <span data-ttu-id="d9aad-114">Ensure</span><span class="sxs-lookup"><span data-stu-id="d9aad-114">Ensure</span></span>| <span data-ttu-id="d9aad-115">기능을 사용하도록 설정할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d9aad-115">Specifies whether the features are enabled.</span></span> <span data-ttu-id="d9aad-116">기능을 사용하도록 설정하려면 이 속성을 "Enable"로 설정하고 기능을 사용하지 않도록 설정하려면 속성을 "Disable"로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="d9aad-116">To ensure that the features are enabled, set this property to "Enable" To ensure that the features are disabled, set the property to "Disable".</span></span>|
| <span data-ttu-id="d9aad-117">원본</span><span class="sxs-lookup"><span data-stu-id="d9aad-117">Source</span></span>| <span data-ttu-id="d9aad-118">구현되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="d9aad-118">Not implemented.</span></span>|
| <span data-ttu-id="d9aad-119">NoWindowsUpdateCheck</span><span class="sxs-lookup"><span data-stu-id="d9aad-119">NoWindowsUpdateCheck</span></span>| <span data-ttu-id="d9aad-120">기능을 사용하도록 설정하기 위해 원본 파일을 검색할 때 DISM에서 WU(Windows 업데이트)에 연결하는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d9aad-120">Specifies whether DISM contacts Windows Update (WU) when searching for the source files to enable features.</span></span> <span data-ttu-id="d9aad-121">$true이면 DISM에서 WU에 연결하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d9aad-121">If $true, DISM does not contact WU.</span></span>|
| <span data-ttu-id="d9aad-122">RemoveFilesOnDisable</span><span class="sxs-lookup"><span data-stu-id="d9aad-122">RemoveFilesOnDisable</span></span>| <span data-ttu-id="d9aad-123">기능을 사용하지 않도록 설정할 때(즉, **Ensure**를 "Absent"로 설정할 때) 기능과 연결된 파일을 모두 제거하려면 **$true**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="d9aad-123">Set to **$true** to remove all files associated with the features when they are disabled (that is, when **Ensure** is set to "Absent").</span></span>|
| <span data-ttu-id="d9aad-124">로그 수준</span><span class="sxs-lookup"><span data-stu-id="d9aad-124">LogLevel</span></span>| <span data-ttu-id="d9aad-125">로그에 표시되는 최대 출력 수준입니다.</span><span class="sxs-lookup"><span data-stu-id="d9aad-125">The maximum output level shown in the logs.</span></span> <span data-ttu-id="d9aad-126">허용되는 값은 "ErrorsOnly"(오류만 기록), "ErrorsAndWarning"(오류와 경고 기록) 및 "ErrorsAndWarningAndInformation"(오류, 경고 및 디버그 정보 기록)입니다.</span><span class="sxs-lookup"><span data-stu-id="d9aad-126">The accepted values are: "ErrorsOnly" (only errors are logged), "ErrorsAndWarning" (errors and warnings are logged), and "ErrorsAndWarningAndInformation" (errors, warnings, and debug information are logged).</span></span>|
| <span data-ttu-id="d9aad-127">LogPath</span><span class="sxs-lookup"><span data-stu-id="d9aad-127">LogPath</span></span>| <span data-ttu-id="d9aad-128">리소스 공급자가 작업을 기록할 로그 파일의 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="d9aad-128">The path to a log file where you want the resource provider to log the operation.</span></span>|
| <span data-ttu-id="d9aad-129">DependsOn</span><span class="sxs-lookup"><span data-stu-id="d9aad-129">DependsOn</span></span>| <span data-ttu-id="d9aad-130">이 리소스를 구성하기 전에 다른 리소스의 구성을 실행해야 함을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d9aad-130">Specifies that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="d9aad-131">예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 ID가 __ResourceName__이고 해당 형식이 __ResourceType__일 경우, 이 속성을 사용하기 위한 구문은 `DependsOn = "[ResourceType]ResourceName"`입니다.</span><span class="sxs-lookup"><span data-stu-id="d9aad-131">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
