---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: DSC WaitForSome 리소스
ms.openlocfilehash: 888da1810f0a9233579bad5eef8d5dd556947c61
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076857"
---
# <a name="dsc-waitforsome-resource"></a><span data-ttu-id="834ca-103">DSC WaitForSome 리소스</span><span class="sxs-lookup"><span data-stu-id="834ca-103">DSC WaitForSome Resource</span></span>

> <span data-ttu-id="834ca-104">적용 대상: Windows PowerShell 5.0 이상</span><span class="sxs-lookup"><span data-stu-id="834ca-104">Applies To: Windows PowerShell 5.0 and later</span></span>

<span data-ttu-id="834ca-105">**WaitForSome** DSC(Desired State Configuration) 리소스를 [DSC 구성](../../../configurations/configurations.md)의 노드 블록 내에서 사용하면 다른 노드의 구성에 대한 종속성을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="834ca-105">The **WaitForSome** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](../../../configurations/configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="834ca-106">**ResourceName** 속성으로 지정된 리소스가 **NodeName** 속성으로 정의된 최소 노드 수(**NodeCount**를 통해 지정함)에서 필요한 상태이면 이 리소스가 정상적으로 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="834ca-106">This resource succeeds if the resource specified by the **ResourceName** property is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span>


## <a name="syntax"></a><span data-ttu-id="834ca-107">구문</span><span class="sxs-lookup"><span data-stu-id="834ca-107">Syntax</span></span>

```
WaitForSome [String] #ResourceName
{
    NodeCount = [UInt32]
    NodeName = [string[]]
    ResourceName = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
    [RetryCount = [UInt32]]
    [RetryIntervalSec = [UInt64]]
    [ThrottleLimit = [UInt32]]
}
```

## <a name="properties"></a><span data-ttu-id="834ca-108">속성</span><span class="sxs-lookup"><span data-stu-id="834ca-108">Properties</span></span>

|  <span data-ttu-id="834ca-109">속성</span><span class="sxs-lookup"><span data-stu-id="834ca-109">Property</span></span>  |  <span data-ttu-id="834ca-110">설명</span><span class="sxs-lookup"><span data-stu-id="834ca-110">Description</span></span>   |
|---|---|
| <span data-ttu-id="834ca-111">NodeCount</span><span class="sxs-lookup"><span data-stu-id="834ca-111">NodeCount</span></span>| <span data-ttu-id="834ca-112">이 리소스를 정상적으로 적용하려면 필요한 상태여야 하는 최소 노드 수입니다.</span><span class="sxs-lookup"><span data-stu-id="834ca-112">The minimum number of nodes that must be in the desired state for this resource to succeed.</span></span>|
| <span data-ttu-id="834ca-113">NodeName</span><span class="sxs-lookup"><span data-stu-id="834ca-113">NodeName</span></span>| <span data-ttu-id="834ca-114">사용할 리소스의 대상 노드입니다.</span><span class="sxs-lookup"><span data-stu-id="834ca-114">The target nodes of the resource to depend on.</span></span>|
| <span data-ttu-id="834ca-115">ResourceName</span><span class="sxs-lookup"><span data-stu-id="834ca-115">ResourceName</span></span>| <span data-ttu-id="834ca-116">사용할 리소스 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="834ca-116">The resource name to depend on.</span></span> <span data-ttu-id="834ca-117">이 리소스가 다른 구성에 속하는 경우 "[__ResourceType__]__ResourceName__::[__ConfigurationName__]::[__ConfigurationName__]"으로 이름의 형식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="834ca-117">If this resource belongs to a different configuration, format the name as "[__ResourceType__]__ResourceName__::[__ConfigurationName__]::[__ConfigurationName__]"</span></span>|
| <span data-ttu-id="834ca-118">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="834ca-118">RetryIntervalSec</span></span>| <span data-ttu-id="834ca-119">다시 시도할 때까지의 시간(초)입니다.</span><span class="sxs-lookup"><span data-stu-id="834ca-119">The number of seconds before retrying.</span></span> <span data-ttu-id="834ca-120">최소값은 1입니다.</span><span class="sxs-lookup"><span data-stu-id="834ca-120">Minimum is 1.</span></span>|
| <span data-ttu-id="834ca-121">RetryCount</span><span class="sxs-lookup"><span data-stu-id="834ca-121">RetryCount</span></span>| <span data-ttu-id="834ca-122">최대 다시 시도 횟수입니다.</span><span class="sxs-lookup"><span data-stu-id="834ca-122">The maximum number of times to retry.</span></span>|
| <span data-ttu-id="834ca-123">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="834ca-123">ThrottleLimit</span></span>| <span data-ttu-id="834ca-124">동시에 연결하는 컴퓨터의 수입니다.</span><span class="sxs-lookup"><span data-stu-id="834ca-124">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="834ca-125">기본값은 new-cimsession 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="834ca-125">Default is new-cimsession default.</span></span>|
| <span data-ttu-id="834ca-126">DependsOn</span><span class="sxs-lookup"><span data-stu-id="834ca-126">DependsOn</span></span> | <span data-ttu-id="834ca-127">이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="834ca-127">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="834ca-128">예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 ID가 __ResourceName__이고 해당 형식이 __ResourceType__일 경우, 이 속성을 사용하기 위한 구문은 `DependsOn = "[ResourceType]ResourceName"`입니다.</span><span class="sxs-lookup"><span data-stu-id="834ca-128">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="834ca-129">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="834ca-129">PsDscRunAsCredential</span></span> | <span data-ttu-id="834ca-130">[사용자 자격 증명을 사용하여 DSC 실행](https://docs.microsoft.com/powershell/dsc/runasuser) 참조</span><span class="sxs-lookup"><span data-stu-id="834ca-130">See [Using DSC with User Credentials](https://docs.microsoft.com/powershell/dsc/runasuser)</span></span> |

## <a name="example"></a><span data-ttu-id="834ca-131">예제</span><span class="sxs-lookup"><span data-stu-id="834ca-131">Example</span></span>

<span data-ttu-id="834ca-132">이 리소스를 사용하는 방법의 예제를 보려면 [노드 간 종속성 지정](../../../configurations/crossNodeDependencies.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="834ca-132">For an example of how to use this resource, see [Specifying cross-node dependencies](../../../configurations/crossNodeDependencies.md)</span></span>
