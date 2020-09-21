---
ms.date: 07/16/2020
keywords: dsc,powershell,configuration,setup
title: DSC 환경 리소스
ms.openlocfilehash: d8519a66d457767dcbc0e08b01a69a9264997479
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464420"
---
# <a name="dsc-environment-resource"></a><span data-ttu-id="cf193-103">DSC 환경 리소스</span><span class="sxs-lookup"><span data-stu-id="cf193-103">DSC Environment Resource</span></span>

> <span data-ttu-id="cf193-104">적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="cf193-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="cf193-105">PowerShell DSC(필요한 상태 구성)의 **Environment** 리소스에서는 시스템 환경 변수를 관리하는 메커니즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="cf193-105">The **Environment** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage system environment variables.</span></span>

## <a name="syntax"></a><span data-ttu-id="cf193-106">구문</span><span class="sxs-lookup"><span data-stu-id="cf193-106">Syntax</span></span>

```Syntax
Environment [string] #ResourceName
{
    Name = [string]
    [ Path = [bool] ]
    [ Target = [string] { Process | Machine } ]
    [ Value = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="cf193-107">속성</span><span class="sxs-lookup"><span data-stu-id="cf193-107">Properties</span></span>

|<span data-ttu-id="cf193-108">속성</span><span class="sxs-lookup"><span data-stu-id="cf193-108">Property</span></span> |<span data-ttu-id="cf193-109">Description</span><span class="sxs-lookup"><span data-stu-id="cf193-109">Description</span></span> |
|---|---|
|<span data-ttu-id="cf193-110">속성</span><span class="sxs-lookup"><span data-stu-id="cf193-110">Name</span></span> |<span data-ttu-id="cf193-111">특정 상태를 확인하려는 환경 변수의 이름을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="cf193-111">Indicates the name of the environment variable for which you want to ensure a specific state.</span></span> |
|<span data-ttu-id="cf193-112">경로</span><span class="sxs-lookup"><span data-stu-id="cf193-112">Path</span></span> |<span data-ttu-id="cf193-113">구성 중인 환경 변수를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="cf193-113">Defines the environment variable that is being configured.</span></span> <span data-ttu-id="cf193-114">변수가 **Path** 변수이면 이 속성을 `$true`로 설정하고, 그렇지 않으면 `$false`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="cf193-114">Set this property to `$true` if the variable is the **Path** variable; otherwise, set it to `$false`.</span></span> <span data-ttu-id="cf193-115">기본값은 `$false`입니다.</span><span class="sxs-lookup"><span data-stu-id="cf193-115">The default is `$false`.</span></span> <span data-ttu-id="cf193-116">구성되고 있는 변수가 **Path** 변수라면, **Value** 속성을 통해 제공된 값은 기존 값에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf193-116">If the variable being configured is the **Path** variable, the value provided through the **Value** property will be appended to the existing value.</span></span> |
|<span data-ttu-id="cf193-117">Target</span><span class="sxs-lookup"><span data-stu-id="cf193-117">Target</span></span>| <span data-ttu-id="cf193-118">변수를 검색할 위치를 나타냅니다. 머신 또는 프로세스입니다.</span><span class="sxs-lookup"><span data-stu-id="cf193-118">Indicates where to retrieve the variable: The machine or the process.</span></span> <span data-ttu-id="cf193-119">둘 다 지정된 경우 머신의 값이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf193-119">If both are indicated then only the value from the machine is returned.</span></span> <span data-ttu-id="cf193-120">둘 다가 나머지 리소스의 기본값이기 기본값은 둘 다입니다.</span><span class="sxs-lookup"><span data-stu-id="cf193-120">The default is both since that is the default for the rest of the resource.</span></span> |
|<span data-ttu-id="cf193-121">값</span><span class="sxs-lookup"><span data-stu-id="cf193-121">Value</span></span> |<span data-ttu-id="cf193-122">환경 변수에 할당할 값입니다.</span><span class="sxs-lookup"><span data-stu-id="cf193-122">The value to assign to the environment variable.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="cf193-123">공용 속성</span><span class="sxs-lookup"><span data-stu-id="cf193-123">Common properties</span></span>

|<span data-ttu-id="cf193-124">속성</span><span class="sxs-lookup"><span data-stu-id="cf193-124">Property</span></span> |<span data-ttu-id="cf193-125">Description</span><span class="sxs-lookup"><span data-stu-id="cf193-125">Description</span></span> |
|---|---|
|<span data-ttu-id="cf193-126">DependsOn</span><span class="sxs-lookup"><span data-stu-id="cf193-126">DependsOn</span></span> |<span data-ttu-id="cf193-127">이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="cf193-127">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="cf193-128">예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 ID가 ResourceName이고 해당 형식이 ResourceType일 경우, 이 속성을 사용하기 위한 구문은 `DependsOn = "[ResourceType]ResourceName"`입니다.</span><span class="sxs-lookup"><span data-stu-id="cf193-128">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="cf193-129">Ensure</span><span class="sxs-lookup"><span data-stu-id="cf193-129">Ensure</span></span> |<span data-ttu-id="cf193-130">변수가 있는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="cf193-130">Indicates if a variable exists.</span></span> <span data-ttu-id="cf193-131">변수가 없는 경우 환경 변수를 만들거나 변수가 이미 있는 경우 그 값이 **Value** 속성을 통해 제공된 값과 일치하는지 확인하려면 이 속성을 **있음**으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="cf193-131">Set this property to **Present** to create the environment variable if it does not exist or to ensure that its value matches what is provided through the **Value** property if the variable already exists.</span></span> <span data-ttu-id="cf193-132">변수가 존재하는 경우 변수를 삭제하려면 이 속성을 **없음**으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="cf193-132">Set it to **Absent** to delete the variable if it exists.</span></span> |
|<span data-ttu-id="cf193-133">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="cf193-133">PsDscRunAsCredential</span></span> |<span data-ttu-id="cf193-134">전체 리소스를 실행하기 위한 자격 증명을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="cf193-134">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="cf193-135">**PsDscRunAsCredential** 공용 속성은 다른 자격 증명의 컨텍스트에서 DSC 리소스를 실행할 수 있도록 WMF 5.0에 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="cf193-135">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="cf193-136">자세한 내용은 [ DSC 리소스로 자격 증명 사용](../../../configurations/runasuser.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cf193-136">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="cf193-137">예제</span><span class="sxs-lookup"><span data-stu-id="cf193-137">Example</span></span>

<span data-ttu-id="cf193-138">다음 예제에서는 TestEnvironmentVariable이 있고 그 값이 _TestValue_인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="cf193-138">The following example ensures that TestEnvironmentVariable is present and it has the value _TestValue_.</span></span> <span data-ttu-id="cf193-139">없을 경우 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="cf193-139">If it is not present, it creates it.</span></span>

```powershell
Environment EnvironmentExample
{
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Name = "TestEnvironmentVariable"
    Value = "TestValue"
}
```
