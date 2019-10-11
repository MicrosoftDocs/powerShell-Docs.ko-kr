---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: Linux nxEnvironment 리소스용 DSC
ms.openlocfilehash: 55c1b2402e23c1042ed48b40c1084aa63c515b36
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953230"
---
# <a name="dsc-for-linux-nxenvironment-resource"></a><span data-ttu-id="2c748-103">Linux nxEnvironment 리소스용 DSC</span><span class="sxs-lookup"><span data-stu-id="2c748-103">DSC for Linux nxEnvironment Resource</span></span>

<span data-ttu-id="2c748-104">PowerShell DSC(필요한 상태 구성)의 **nxEnvironment** 리소스에서는 Linux 노드 상의 시스템 환경 변수를 관리하는 메커니즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="2c748-104">The **nxEnvironment** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage system environment variables on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="2c748-105">구문</span><span class="sxs-lookup"><span data-stu-id="2c748-105">Syntax</span></span>

```Syntax
nxEnvironment <string> #ResourceName
{
    Name = <string>
    [ Value = <string>
    [ Path = <bool> }
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a><span data-ttu-id="2c748-106">속성</span><span class="sxs-lookup"><span data-stu-id="2c748-106">Properties</span></span>

|<span data-ttu-id="2c748-107">속성</span><span class="sxs-lookup"><span data-stu-id="2c748-107">Property</span></span> |<span data-ttu-id="2c748-108">설명</span><span class="sxs-lookup"><span data-stu-id="2c748-108">Description</span></span> |
|---|---|
|<span data-ttu-id="2c748-109">이름</span><span class="sxs-lookup"><span data-stu-id="2c748-109">Name</span></span> |<span data-ttu-id="2c748-110">특정 상태를 확인하려는 환경 변수의 이름을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="2c748-110">Indicates the name of the environment variable for which you want to ensure a specific state.</span></span> |
|<span data-ttu-id="2c748-111">Value</span><span class="sxs-lookup"><span data-stu-id="2c748-111">Value</span></span> |<span data-ttu-id="2c748-112">환경 변수에 할당할 값입니다.</span><span class="sxs-lookup"><span data-stu-id="2c748-112">The value to assign to the environment variable.</span></span> |
|<span data-ttu-id="2c748-113">경로</span><span class="sxs-lookup"><span data-stu-id="2c748-113">Path</span></span> |<span data-ttu-id="2c748-114">구성 중인 환경 변수를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="2c748-114">Defines the environment variable that is being configured.</span></span> <span data-ttu-id="2c748-115">변수가 **Path** 변수이면 이 속성을 `$true`로 설정하고, 그렇지 않으면 `$false`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="2c748-115">Set this property to `$true` if the variable is the **Path** variable; otherwise, set it to `$false`.</span></span> <span data-ttu-id="2c748-116">기본값은 `$false`입니다.</span><span class="sxs-lookup"><span data-stu-id="2c748-116">The default is `$false`.</span></span> <span data-ttu-id="2c748-117">구성되고 있는 변수가 **Path** 변수라면, **Value** 속성을 통해 제공된 값은 기존 값에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c748-117">If the variable being configured is the **Path** variable, the value provided through the **Value** property will be appended to the existing value.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="2c748-118">공용 속성</span><span class="sxs-lookup"><span data-stu-id="2c748-118">Common properties</span></span>

|<span data-ttu-id="2c748-119">속성</span><span class="sxs-lookup"><span data-stu-id="2c748-119">Property</span></span> |<span data-ttu-id="2c748-120">설명</span><span class="sxs-lookup"><span data-stu-id="2c748-120">Description</span></span> |
|---|---|
|<span data-ttu-id="2c748-121">DependsOn</span><span class="sxs-lookup"><span data-stu-id="2c748-121">DependsOn</span></span> |<span data-ttu-id="2c748-122">이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="2c748-122">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="2c748-123">예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 ID가 ResourceName이고 해당 형식이 ResourceType일 경우, 이 속성을 사용하기 위한 구문은 `DependsOn = "[ResourceType]ResourceName"`입니다.</span><span class="sxs-lookup"><span data-stu-id="2c748-123">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="2c748-124">Ensure</span><span class="sxs-lookup"><span data-stu-id="2c748-124">Ensure</span></span> |<span data-ttu-id="2c748-125">해당 변수가 존재하는지를 확인할지 여부를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="2c748-125">Determines whether to check if the variable exists.</span></span> <span data-ttu-id="2c748-126">변수가 존재하도록 하려면 이 속성을 **Present**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="2c748-126">Set this property to **Present** to ensure the variable exists.</span></span> <span data-ttu-id="2c748-127">변수가 존재하지 않도록 하려면 이 속성을 **Absent**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="2c748-127">Set it to **Absent** to ensure the variable does not exist.</span></span> <span data-ttu-id="2c748-128">기본값은 **Present**입니다.</span><span class="sxs-lookup"><span data-stu-id="2c748-128">The default value is **Present**.</span></span> |

## <a name="additional-information"></a><span data-ttu-id="2c748-129">추가 정보</span><span class="sxs-lookup"><span data-stu-id="2c748-129">Additional Information</span></span>

- <span data-ttu-id="2c748-130">**Path**가 없거나 `$false`로 설정되어 있으면, 환경 변수는 `/etc/environment`에서 관리됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c748-130">If **Path** is absent or set to `$false`, environment variables are managed in `/etc/environment`.</span></span>
  <span data-ttu-id="2c748-131">프로그램 또는 스크립트가 구성을 통해 관리되는 환경 변수에 액세스하도록 `/etc/environment` 파일을 소싱해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c748-131">Your programs or scripts may require configuration to source the `/etc/environment` file to access the managed environment variables.</span></span>
- <span data-ttu-id="2c748-132">**Path**가 `$true`로 설정된 경우, 환경 변수는 `/etc/profile.d/DSCenvironment.sh` 파일에서 관리됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c748-132">If **Path** is set to `$true`, the environment variable is managed in the file `/etc/profile.d/DSCenvironment.sh`.</span></span> <span data-ttu-id="2c748-133">이 파일은 존재하지 않는 경우 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="2c748-133">This file will be created if it does not exist.</span></span> <span data-ttu-id="2c748-134">**Ensure**가 **Absent**로 설정되어 있고, **Path**가 `$true`로 설정되어 있는 경우, 기존 환경 변수는 다른 파일에서는 제거되지 않고 `/etc/profile.d/DSCenvironment.sh`에서만 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c748-134">If **Ensure** is set to **Absent** and **Path** is set to `$true`, an existing environment variable will only be removed from `/etc/profile.d/DSCenvironment.sh` and not from other files.</span></span>

## <a name="example"></a><span data-ttu-id="2c748-135">예제</span><span class="sxs-lookup"><span data-stu-id="2c748-135">Example</span></span>

<span data-ttu-id="2c748-136">다음 예제에서는 **nxEnvironment** 리소스를 사용하여 **TestEnvironmentVariable**이 존재하고 "Test-Value" 값을 갖도록 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2c748-136">The following example shows how to use the **nxEnvironment** resource to ensure that **TestEnvironmentVariable** is present and has the value "Test-Value".</span></span> <span data-ttu-id="2c748-137">**TestEnvironmentVariable**이 존재하지 않을 경우, 자동으로 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="2c748-137">If **TestEnvironmentVariable** is not present, it will be created.</span></span>

```powershell
Import-DSCResource -Module nx

nxEnvironment EnvironmentExample
{
    Ensure = "Present"
    Name = "TestEnvironmentVariable"
    Value = "TestValue"
}
```