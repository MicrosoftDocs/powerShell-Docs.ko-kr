---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: DSC WindowsFeature 리소스
ms.openlocfilehash: 7a57f4b2797ab3bb202aea8b2543d1e3f14074e9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55680943"
---
# <a name="dsc-windowsfeature-resource"></a><span data-ttu-id="4e63a-103">DSC WindowsFeature 리소스</span><span class="sxs-lookup"><span data-stu-id="4e63a-103">DSC WindowsFeature Resource</span></span>

> <span data-ttu-id="4e63a-104">적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="4e63a-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="4e63a-105">PowerShell DSC(필요한 상태 구성)의 **WindowsFeature** 리소스에서는 대상 노드에서 역할 및 기능이 추가 또는 제거되었는지를 확인하는 메커니즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="4e63a-105">The **WindowsFeature** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that roles and features are added or removed on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="4e63a-106">구문</span><span class="sxs-lookup"><span data-stu-id="4e63a-106">Syntax</span></span>

```
WindowsFeature [string] #ResourceName
{
    Name = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ IncludeAllSubFeature = [bool] ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ Source = [string] ]
}
```

## <a name="properties"></a><span data-ttu-id="4e63a-107">속성</span><span class="sxs-lookup"><span data-stu-id="4e63a-107">Properties</span></span>

|  <span data-ttu-id="4e63a-108">속성</span><span class="sxs-lookup"><span data-stu-id="4e63a-108">Property</span></span>  |  <span data-ttu-id="4e63a-109">설명</span><span class="sxs-lookup"><span data-stu-id="4e63a-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="4e63a-110">이름</span><span class="sxs-lookup"><span data-stu-id="4e63a-110">Name</span></span>| <span data-ttu-id="4e63a-111">추가되었는지 또는 제거되었는지를 확인하려는 역할이나 기능의 이름을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4e63a-111">Indicates the name of the role or feature that you want to ensure is added or removed.</span></span> <span data-ttu-id="4e63a-112">이것은 [Get-WindowsFeature](/powershell/module/servermanager/Get-WindowsFeature) cmdlet의 __Name__ 속성과 동일하며, 역할이나 기능의 표시 이름은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="4e63a-112">This is the same as the __Name__ property from the [Get-WindowsFeature](/powershell/module/servermanager/Get-WindowsFeature) cmdlet, and not the display name of the role or feature.</span></span>|
| <span data-ttu-id="4e63a-113">자격 증명</span><span class="sxs-lookup"><span data-stu-id="4e63a-113">Credential</span></span>| <span data-ttu-id="4e63a-114">역할 또는 기능을 추가 또는 제거하는 데 사용할 자격 증명을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4e63a-114">Indicates the credentials to use to add or remove the role or feature.</span></span>|
| <span data-ttu-id="4e63a-115">Ensure</span><span class="sxs-lookup"><span data-stu-id="4e63a-115">Ensure</span></span>| <span data-ttu-id="4e63a-116">역할이나 기능이 추가되었는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4e63a-116">Indicates if the role or feature is added.</span></span> <span data-ttu-id="4e63a-117">역할이나 기능이 추가된 것을 보증하려면, 이 속성을 "Present"으로 설정하고, 역할이나 기능이 제거된 것을 보증하려면 이 속성을 "Absent"으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="4e63a-117">To ensure that the role or feature is added, set this property to "Present" To ensure that the role or feature is removed, set the property to "Absent".</span></span>|
| <span data-ttu-id="4e63a-118">IncludeAllSubFeature</span><span class="sxs-lookup"><span data-stu-id="4e63a-118">IncludeAllSubFeature</span></span>| <span data-ttu-id="4e63a-119">__Name__ 속성으로 지정하는 기능의 상태와 함께 모든 필수 하위 기능의 상태를 보증하려면 이 속성을 __$true__로 설정하세요.</span><span class="sxs-lookup"><span data-stu-id="4e63a-119">Set this property to __$true__ to ensure the state of all required subfeatures with the state of the feature you specify with the __Name__ property.</span></span>|
| <span data-ttu-id="4e63a-120">LogPath</span><span class="sxs-lookup"><span data-stu-id="4e63a-120">LogPath</span></span>| <span data-ttu-id="4e63a-121">리소스 공급자가 작업을 로그하기를 원하는 로그 파일의 경로를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4e63a-121">Indicates the path to a log file where you want the resource provider to log the operation.</span></span>|
| <span data-ttu-id="4e63a-122">DependsOn</span><span class="sxs-lookup"><span data-stu-id="4e63a-122">DependsOn</span></span>| <span data-ttu-id="4e63a-123">이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4e63a-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="4e63a-124">예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 ID가 __ResourceName__이고 해당 형식이 __ResourceType__일 경우, 이 속성을 사용하기 위한 구문은 `DependsOn = "[ResourceType]ResourceName"`입니다.</span><span class="sxs-lookup"><span data-stu-id="4e63a-124">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="4e63a-125">원본</span><span class="sxs-lookup"><span data-stu-id="4e63a-125">Source</span></span>| <span data-ttu-id="4e63a-126">필요한 경우 설치에 사용할 소스 파일의 위치를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4e63a-126">Indicates the location of the source file to use for installation, if necessary.</span></span>|

## <a name="example"></a><span data-ttu-id="4e63a-127">예제</span><span class="sxs-lookup"><span data-stu-id="4e63a-127">Example</span></span>
```powershell
WindowsFeature RoleExample
{
    Ensure = "Present"
    # Alternatively, to ensure the role is uninstalled, set Ensure to "Absent"
    Name = "Web-Server" # Use the Name property from Get-WindowsFeature
}
```