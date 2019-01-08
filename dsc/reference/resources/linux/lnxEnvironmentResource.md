---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Linux nxEnvironment 리소스용 DSC
ms.openlocfilehash: 763ec560faa6adaf42aef3c21c9045be95f780bc
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047947"
---
# <a name="dsc-for-linux-nxenvironment-resource"></a><span data-ttu-id="5aa29-103">Linux nxEnvironment 리소스용 DSC</span><span class="sxs-lookup"><span data-stu-id="5aa29-103">DSC for Linux nxEnvironment Resource</span></span>

<span data-ttu-id="5aa29-104">PowerShell DSC(필요한 상태 구성)의 **nxEnvironment** 리소스에서는 Linux 노드 상의 시스템 환경 변수를 관리하는 메커니즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="5aa29-104">The **nxEnvironment** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage system environment variables on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="5aa29-105">구문</span><span class="sxs-lookup"><span data-stu-id="5aa29-105">Syntax</span></span>

```
nxEnvironment <string> #ResourceName
{
    Name = <string>
    [ Value = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ Path = <bool> }
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="5aa29-106">속성</span><span class="sxs-lookup"><span data-stu-id="5aa29-106">Properties</span></span>

|  <span data-ttu-id="5aa29-107">속성</span><span class="sxs-lookup"><span data-stu-id="5aa29-107">Property</span></span> |  <span data-ttu-id="5aa29-108">설명</span><span class="sxs-lookup"><span data-stu-id="5aa29-108">Description</span></span> |
|---|---|
| <span data-ttu-id="5aa29-109">이름</span><span class="sxs-lookup"><span data-stu-id="5aa29-109">Name</span></span>| <span data-ttu-id="5aa29-110">특정 상태를 확인하려는 환경 변수의 이름을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5aa29-110">Indicates the name of the environment variable for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="5aa29-111">Value</span><span class="sxs-lookup"><span data-stu-id="5aa29-111">Value</span></span>| <span data-ttu-id="5aa29-112">환경 변수에 할당할 값입니다.</span><span class="sxs-lookup"><span data-stu-id="5aa29-112">The value to assign to the environment variable.</span></span>|
| <span data-ttu-id="5aa29-113">Ensure</span><span class="sxs-lookup"><span data-stu-id="5aa29-113">Ensure</span></span>| <span data-ttu-id="5aa29-114">해당 변수가 존재하는지를 확인할지 여부를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="5aa29-114">Determines whether to check if the variable exists.</span></span> <span data-ttu-id="5aa29-115">변수가 존재하도록 하려면 이 속성을 "Present"으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="5aa29-115">Set this property to "Present" to ensure the variable exists.</span></span> <span data-ttu-id="5aa29-116">변수가 존재하지 않도록 하려면 이 속성을 "Absent"으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="5aa29-116">Set it to "Absent" to ensure the variable does not exist.</span></span> <span data-ttu-id="5aa29-117">기본값은 "Present"입니다.</span><span class="sxs-lookup"><span data-stu-id="5aa29-117">The default value is "Present".</span></span>|
| <span data-ttu-id="5aa29-118">경로</span><span class="sxs-lookup"><span data-stu-id="5aa29-118">Path</span></span>| <span data-ttu-id="5aa29-119">구성 중인 환경 변수를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="5aa29-119">Defines the environment variable that is being configured.</span></span> <span data-ttu-id="5aa29-120">변수가 **Path** 변수이면 이 속성을 **$true**로 설정하고, 그렇지 않으면 **$false**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="5aa29-120">Set this property to **$true** if the variable is the **Path** variable; otherwise, set it to **$false**.</span></span> <span data-ttu-id="5aa29-121">기본값은 **$false**입니다.</span><span class="sxs-lookup"><span data-stu-id="5aa29-121">The default is **$false**.</span></span> <span data-ttu-id="5aa29-122">구성되고 있는 변수가 **Path** 변수라면, **Value** 속성을 통해 제공된 값은 기존 값에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="5aa29-122">If the variable being configured is the **Path** variable, the value provided through the **Value** property will be appended to the existing value.</span></span>|
| <span data-ttu-id="5aa29-123">DependsOn</span><span class="sxs-lookup"><span data-stu-id="5aa29-123">DependsOn</span></span> | <span data-ttu-id="5aa29-124">이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5aa29-124">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="5aa29-125">예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 **ID**가 **ResourceName**이고 해당 형식이 **ResourceType**일 경우, 이 속성을 사용하기 위한 구문은 `DependsOn = "[ResourceType]ResourceName"`입니다.</span><span class="sxs-lookup"><span data-stu-id="5aa29-125">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="additional-information"></a><span data-ttu-id="5aa29-126">추가 정보</span><span class="sxs-lookup"><span data-stu-id="5aa29-126">Additional Information</span></span>

* <span data-ttu-id="5aa29-127">**Path**가 없거나 **$false**로 설정되어 있으면, 환경 변수는 `/etc/environment`에서 관리됩니다.</span><span class="sxs-lookup"><span data-stu-id="5aa29-127">If **Path** is absent or set to **$false**, environment variables are managed in `/etc/environment`.</span></span> <span data-ttu-id="5aa29-128">프로그램 또는 스크립트가 구성을 통해 관리되는 환경 변수에 액세스하도록 `/etc/environment` 파일을 소싱해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5aa29-128">Your programs or scripts may require configuration to source the `/etc/environment` file to access the managed environment variables.</span></span>
* <span data-ttu-id="5aa29-129">**Path**가 **$true**로 설정된 경우, 환경 변수는 `/etc/profile.d/DSCenvironment.sh` 파일에서 관리됩니다.</span><span class="sxs-lookup"><span data-stu-id="5aa29-129">If **Path** is set to **$true**, the environment variable is managed in the file `/etc/profile.d/DSCenvironment.sh`.</span></span> <span data-ttu-id="5aa29-130">이 파일은 존재하지 않는 경우 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="5aa29-130">This file will be created if it does not exist.</span></span> <span data-ttu-id="5aa29-131">**Ensure**가 "Absent"으로 설정되어 있고, **Path**가 **$true**로 설정되어 있는 경우, 기존 환경 변수는 다른 파일에서는 제거되지 않고 `/etc/profile.d/DSCenvironment.sh`에서만 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="5aa29-131">If **Ensure** is set to "Absent" and **Path** is set to **$true**, an existing environment variable will only be removed from `/etc/profile.d/DSCenvironment.sh` and not from other files.</span></span>

## <a name="example"></a><span data-ttu-id="5aa29-132">예제</span><span class="sxs-lookup"><span data-stu-id="5aa29-132">Example</span></span>

<span data-ttu-id="5aa29-133">다음 예제에서는 **nxEnvironment** 리소스를 사용하여 **TestEnvironmentVariable**이 존재하고 "Test-Value" 값을 갖도록 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5aa29-133">The following example shows how to use the **nxEnvironment** resource to ensure that **TestEnvironmentVariable** is present and has the value "Test-Value".</span></span> <span data-ttu-id="5aa29-134">**TestEnvironmentVariable**이 존재하지 않을 경우, 자동으로 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="5aa29-134">If **TestEnvironmentVariable** is not present, it will be created.</span></span>

```
Import-DSCResource -Module nx


nxEnvironment EnvironmentExample
{
    Ensure = “Present”
    Name = “TestEnvironmentVariable”
    Value = “TestValue”
}
```