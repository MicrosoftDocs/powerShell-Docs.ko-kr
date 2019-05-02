---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: DSC ServiceSet 리소스
ms.openlocfilehash: 5694c2abc5c0caf0098670b629af464b35125583
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076838"
---
# <a name="dsc-serviceset-resource"></a><span data-ttu-id="e035f-103">DSC ServiceSet 리소스</span><span class="sxs-lookup"><span data-stu-id="e035f-103">DSC ServiceSet Resource</span></span>

> <span data-ttu-id="e035f-104">적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="e035f-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="e035f-105">Windows PowerShell DSC(Desired State Configuration)의 **ServiceSet** 리소스에서는 대상 노드에 있는 서비스를 관리하는 메커니즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="e035f-105">The **ServiceSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on the target node.</span></span> <span data-ttu-id="e035f-106">이 리소스는 `Name` 속성에 지정된 각 서비스에 대해 [서비스 리소스](serviceResource.md)를 호출하는 [복합 리소스](../../../resources/authoringResourceComposite.md)입니다.</span><span class="sxs-lookup"><span data-stu-id="e035f-106">This resource is a [composite resource](../../../resources/authoringResourceComposite.md) that calls the [Service resource](serviceResource.md) for each service specified in the `Name` property.</span></span>

<span data-ttu-id="e035f-107">여러 서비스를 동일한 상태로 구성하려는 경우 이 리소스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e035f-107">Use this resource when you want to configure a number of services to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="e035f-108">구문</span><span class="sxs-lookup"><span data-stu-id="e035f-108">Syntax</span></span>

```
Service [string] #ResourceName
{
    Name = [string[]]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Ensure = [string] { Absent | Present }  ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]

}
```

## <a name="properties"></a><span data-ttu-id="e035f-109">속성</span><span class="sxs-lookup"><span data-stu-id="e035f-109">Properties</span></span>

|  <span data-ttu-id="e035f-110">속성</span><span class="sxs-lookup"><span data-stu-id="e035f-110">Property</span></span>  |  <span data-ttu-id="e035f-111">설명</span><span class="sxs-lookup"><span data-stu-id="e035f-111">Description</span></span>   |
|---|---|
| <span data-ttu-id="e035f-112">이름</span><span class="sxs-lookup"><span data-stu-id="e035f-112">Name</span></span>| <span data-ttu-id="e035f-113">서비스 이름을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e035f-113">Indicates the service names.</span></span> <span data-ttu-id="e035f-114">이 속성은 경우에 따라 표시 이름과 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="e035f-114">Note that sometimes this is different from the display names.</span></span> <span data-ttu-id="e035f-115">[Get-Service](https://technet.microsoft.com/library/hh849804.aspx) cmdlet으로 서비스 목록과 현재 상태를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e035f-115">You can get a list of the services and their current state with the [Get-Service](https://technet.microsoft.com/library/hh849804.aspx) cmdlet.</span></span>|
| <span data-ttu-id="e035f-116">StartupType</span><span class="sxs-lookup"><span data-stu-id="e035f-116">StartupType</span></span>| <span data-ttu-id="e035f-117">서비스의 시작 유형을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e035f-117">Indicates the startup type for the service.</span></span> <span data-ttu-id="e035f-118">이 속성에 허용된 값은 **Automatic**, **Disabled** 및 **Manual**입니다.</span><span class="sxs-lookup"><span data-stu-id="e035f-118">The values that are allowed for this property are: **Automatic**, **Disabled**, and **Manual**</span></span>|
| <span data-ttu-id="e035f-119">BuiltInAccount</span><span class="sxs-lookup"><span data-stu-id="e035f-119">BuiltInAccount</span></span>| <span data-ttu-id="e035f-120">서비스에 사용할 로그인 계정을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e035f-120">Indicates the sign-in account to use for the services.</span></span> <span data-ttu-id="e035f-121">이 속성에 허용된 값은 **LocalService**, **LocalSystem** 및 **NetworkService**입니다.</span><span class="sxs-lookup"><span data-stu-id="e035f-121">The values that are allowed for this property are: **LocalService**, **LocalSystem**, and **NetworkService**.</span></span>|
| <span data-ttu-id="e035f-122">State</span><span class="sxs-lookup"><span data-stu-id="e035f-122">State</span></span>| <span data-ttu-id="e035f-123">서비스에 대해 확인하려는 상태 즉, **Stopped** 또는 **Running**을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e035f-123">Indicates the state you want to ensure for the services: **Stopped** or **Running**.</span></span>|
| <span data-ttu-id="e035f-124">Ensure</span><span class="sxs-lookup"><span data-stu-id="e035f-124">Ensure</span></span>| <span data-ttu-id="e035f-125">서비스가 시스템에 있는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e035f-125">Indicates whether the services exist on the system.</span></span> <span data-ttu-id="e035f-126">서비스가 존재하지 않도록 하려면 이 속성을 **Absent**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e035f-126">Set this property to **Absent** to ensure that the services do not exist.</span></span> <span data-ttu-id="e035f-127">서비스가 존재하도록 하려면 이 속성을 **Present**(기본값)로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e035f-127">Setting it to **Present** (the default value) ensures that target services exist.</span></span>|
| <span data-ttu-id="e035f-128">자격 증명</span><span class="sxs-lookup"><span data-stu-id="e035f-128">Credential</span></span>| <span data-ttu-id="e035f-129">서비스 리소스가 실행될 계정에 대한 자격 증명을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e035f-129">Indicates credentials for the account that the service resource will run under.</span></span> <span data-ttu-id="e035f-130">이 속성과 **BuiltinAccount** 속성은 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e035f-130">This property and the **BuiltinAccount** property cannot be used together.</span></span>|
| <span data-ttu-id="e035f-131">DependsOn</span><span class="sxs-lookup"><span data-stu-id="e035f-131">DependsOn</span></span>| <span data-ttu-id="e035f-132">이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e035f-132">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="e035f-133">예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 ID가 *ResourceName*이고 해당 형식이 *ResourceType*일 경우, 이 속성을 사용하기 위한 구문은 `DependsOn = "[ResourceType]ResourceName"`입니다.</span><span class="sxs-lookup"><span data-stu-id="e035f-133">For example, if the ID of the resource configuration script block that you want to run first is *ResourceName* and its type is *ResourceType*, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|



## <a name="example"></a><span data-ttu-id="e035f-134">예제</span><span class="sxs-lookup"><span data-stu-id="e035f-134">Example</span></span>

<span data-ttu-id="e035f-135">다음 구성에서는 "Windows 오디오" 및 "원격 데스크톱 서비스" 서비스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="e035f-135">The following configuration starts the "Windows Audio" and "Remote Desktop Services" services.</span></span>

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
