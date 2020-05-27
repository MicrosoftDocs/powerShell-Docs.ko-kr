---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: DSC ServiceSet 리소스
ms.openlocfilehash: a071a8cdd4a7dc6fd050fc1b88901aa0ce428615
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83563963"
---
# <a name="dsc-serviceset-resource"></a><span data-ttu-id="c15bb-103">DSC ServiceSet 리소스</span><span class="sxs-lookup"><span data-stu-id="c15bb-103">DSC ServiceSet Resource</span></span>

> <span data-ttu-id="c15bb-104">적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="c15bb-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="c15bb-105">Windows PowerShell DSC(필요한 상태 구성)의 **ServiceSet** 리소스에서는 대상 노드에 있는 서비스를 관리하는 메커니즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c15bb-105">The **ServiceSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on the target node.</span></span> <span data-ttu-id="c15bb-106">이 리소스는 **이름** 속성에 지정된 각 서비스에 대해 [서비스 리소스](serviceResource.md)를 호출하는 [복합 리소스](../../../resources/authoringResourceComposite.md)입니다.</span><span class="sxs-lookup"><span data-stu-id="c15bb-106">This resource is a [composite resource](../../../resources/authoringResourceComposite.md) that calls the [Service resource](serviceResource.md) for each service specified in the **Name** property.</span></span>

<span data-ttu-id="c15bb-107">여러 서비스를 동일한 상태로 구성하려는 경우 이 리소스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c15bb-107">Use this resource when you want to configure a number of services to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="c15bb-108">구문</span><span class="sxs-lookup"><span data-stu-id="c15bb-108">Syntax</span></span>

```Syntax
ServiceSet [string] #ResourceName
{
    Name = [string[]]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="c15bb-109">속성</span><span class="sxs-lookup"><span data-stu-id="c15bb-109">Properties</span></span>

|<span data-ttu-id="c15bb-110">속성</span><span class="sxs-lookup"><span data-stu-id="c15bb-110">Property</span></span> |<span data-ttu-id="c15bb-111">Description</span><span class="sxs-lookup"><span data-stu-id="c15bb-111">Description</span></span> |
|---|---|
|<span data-ttu-id="c15bb-112">속성</span><span class="sxs-lookup"><span data-stu-id="c15bb-112">Name</span></span> |<span data-ttu-id="c15bb-113">서비스 이름을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c15bb-113">Indicates the service names.</span></span> <span data-ttu-id="c15bb-114">이 속성은 경우에 따라 표시 이름과 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="c15bb-114">Note that sometimes this is different from the display names.</span></span> <span data-ttu-id="c15bb-115">`Get-Service` cmdlet으로 서비스 목록과 현재 상태를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c15bb-115">You can get a list of the services and their current state with the `Get-Service` cmdlet.</span></span> |
|<span data-ttu-id="c15bb-116">StartupType</span><span class="sxs-lookup"><span data-stu-id="c15bb-116">StartupType</span></span> |<span data-ttu-id="c15bb-117">서비스의 시작 유형을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c15bb-117">Indicates the startup type for the services.</span></span> <span data-ttu-id="c15bb-118">이 속성에 허용된 값은 **Automatic**, **Disabled** 및 **Manual**입니다.</span><span class="sxs-lookup"><span data-stu-id="c15bb-118">The values that are allowed for this property are: **Automatic**, **Disabled**, and **Manual**.</span></span> |
|<span data-ttu-id="c15bb-119">BuiltInAccount</span><span class="sxs-lookup"><span data-stu-id="c15bb-119">BuiltInAccount</span></span> |<span data-ttu-id="c15bb-120">서비스에 사용할 로그인 계정을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c15bb-120">Indicates the sign-in account to use for the services.</span></span> <span data-ttu-id="c15bb-121">이 속성에 허용된 값은 **LocalService**, **LocalSystem** 및 **NetworkService**입니다.</span><span class="sxs-lookup"><span data-stu-id="c15bb-121">The values that are allowed for this property are: **LocalService**, **LocalSystem**, and **NetworkService**.</span></span> |
|<span data-ttu-id="c15bb-122">시스템 상태</span><span class="sxs-lookup"><span data-stu-id="c15bb-122">State</span></span> |<span data-ttu-id="c15bb-123">서비스에 대해 확인하려는 상태 즉, **Stopped** 또는 **Running**을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c15bb-123">Indicates the state you want to ensure for the services: **Stopped** or **Running**.</span></span> |
|<span data-ttu-id="c15bb-124">자격 증명</span><span class="sxs-lookup"><span data-stu-id="c15bb-124">Credential</span></span> |<span data-ttu-id="c15bb-125">서비스 리소스가 실행될 계정에 대한 자격 증명을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c15bb-125">Indicates credentials for the account that the service resource will run under.</span></span> <span data-ttu-id="c15bb-126">이 속성과 **BuiltinAccount** 속성은 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c15bb-126">This property and the **BuiltinAccount** property cannot be used together.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="c15bb-127">공용 속성</span><span class="sxs-lookup"><span data-stu-id="c15bb-127">Common properties</span></span>

|<span data-ttu-id="c15bb-128">속성</span><span class="sxs-lookup"><span data-stu-id="c15bb-128">Property</span></span> |<span data-ttu-id="c15bb-129">Description</span><span class="sxs-lookup"><span data-stu-id="c15bb-129">Description</span></span> |
|---|---|
|<span data-ttu-id="c15bb-130">DependsOn</span><span class="sxs-lookup"><span data-stu-id="c15bb-130">DependsOn</span></span> |<span data-ttu-id="c15bb-131">이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c15bb-131">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="c15bb-132">예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 ID가 ResourceName이고 해당 형식이 ResourceType일 경우, 이 속성을 사용하기 위한 구문은 `DependsOn = "[ResourceType]ResourceName"`입니다.</span><span class="sxs-lookup"><span data-stu-id="c15bb-132">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="c15bb-133">Ensure</span><span class="sxs-lookup"><span data-stu-id="c15bb-133">Ensure</span></span> |<span data-ttu-id="c15bb-134">서비스가 시스템에 있는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c15bb-134">Indicates whether the services exist on the system.</span></span> <span data-ttu-id="c15bb-135">서비스가 존재하지 않도록 하려면 이 속성을 **Absent**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c15bb-135">Set this property to **Absent** to ensure that the services do not exist.</span></span> <span data-ttu-id="c15bb-136">서비스가 존재하도록 하려면 이 속성을 **Present**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c15bb-136">Setting it to **Present** ensures that target services exist.</span></span> <span data-ttu-id="c15bb-137">기본값은 **Present**입니다.</span><span class="sxs-lookup"><span data-stu-id="c15bb-137">The default value is **Present**.</span></span> |
|<span data-ttu-id="c15bb-138">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="c15bb-138">PsDscRunAsCredential</span></span> |<span data-ttu-id="c15bb-139">전체 리소스를 실행하기 위한 자격 증명을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c15bb-139">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="c15bb-140">**PsDscRunAsCredential** 공용 속성은 다른 자격 증명의 컨텍스트에서 DSC 리소스를 실행할 수 있도록 WMF 5.0에 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c15bb-140">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="c15bb-141">자세한 내용은 [ DSC 리소스로 자격 증명 사용](../../../configurations/runasuser.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c15bb-141">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="c15bb-142">예제</span><span class="sxs-lookup"><span data-stu-id="c15bb-142">Example</span></span>

<span data-ttu-id="c15bb-143">다음 구성에서는 "Windows 오디오" 및 "원격 데스크톱 서비스" 서비스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="c15bb-143">The following configuration starts the "Windows Audio" and "Remote Desktop Services" services.</span></span>

```powershell
configuration ServiceSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {
        ServiceSet ServiceSetExample
        {
            Name        = @("TermService", "Audiosrv")
            StartupType = "Manual"
            State       = "Running"
        }
    }
}
```
