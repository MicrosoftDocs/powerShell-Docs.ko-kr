---
ms.date: 07/17/2020
ms.topic: reference
title: Linux용 DSC nxService 리소스
description: Linux용 DSC nxService 리소스
ms.openlocfilehash: 4eefe491c491c9245732def1cc85260f368ef9e1
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92648786"
---
# <a name="dsc-for-linux-nxservice-resource"></a><span data-ttu-id="dbb08-103">Linux용 DSC nxService 리소스</span><span class="sxs-lookup"><span data-stu-id="dbb08-103">DSC for Linux nxService Resource</span></span>

<span data-ttu-id="dbb08-104">PowerShell DSC(필요한 상태 구성)의 **nxService** 리소스에서는 Linux 노드에 있는 서비스를 관리하는 메커니즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="dbb08-104">The **nxService** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="dbb08-105">구문</span><span class="sxs-lookup"><span data-stu-id="dbb08-105">Syntax</span></span>

```Syntax
nxService <string> #ResourceName
{
    Name = <string>
    [ Controller = <string> { init | upstart | systemd } ]
    [ Enabled = <bool> ]
    [ State = <string> { Running | Stopped } ]
    [ DependsOn = <string[]> ]
}
```

## <a name="properties"></a><span data-ttu-id="dbb08-106">속성</span><span class="sxs-lookup"><span data-stu-id="dbb08-106">Properties</span></span>

|<span data-ttu-id="dbb08-107">속성</span><span class="sxs-lookup"><span data-stu-id="dbb08-107">Property</span></span> |<span data-ttu-id="dbb08-108">Description</span><span class="sxs-lookup"><span data-stu-id="dbb08-108">Description</span></span> |
|---|---|
|<span data-ttu-id="dbb08-109">속성</span><span class="sxs-lookup"><span data-stu-id="dbb08-109">Name</span></span> |<span data-ttu-id="dbb08-110">구성할 서비스/데몬의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="dbb08-110">The name of the service/daemon to configure.</span></span> |
|<span data-ttu-id="dbb08-111">컨트롤러</span><span class="sxs-lookup"><span data-stu-id="dbb08-111">Controller</span></span> |<span data-ttu-id="dbb08-112">서비스를 구성할 때 사용할 서비스 컨트롤러의 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="dbb08-112">The type of service controller to use when configuring the service.</span></span> |
|<span data-ttu-id="dbb08-113">사용</span><span class="sxs-lookup"><span data-stu-id="dbb08-113">Enabled</span></span> |<span data-ttu-id="dbb08-114">부팅 시 서비스가 시작되는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="dbb08-114">Indicates whether the service starts on boot.</span></span> |
|<span data-ttu-id="dbb08-115">시스템 상태</span><span class="sxs-lookup"><span data-stu-id="dbb08-115">State</span></span> |<span data-ttu-id="dbb08-116">서비스가 실행되고 있는지를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="dbb08-116">Indicates whether the service is running.</span></span> <span data-ttu-id="dbb08-117">서비스가 실행 중이 아니도록 설정하려면 이 속성을 **Stopped** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="dbb08-117">Set this property to **Stopped** to ensure that the service is not running.</span></span> <span data-ttu-id="dbb08-118">서비스가 실행 중이도록 하려면 이 속성을 **Running** 으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="dbb08-118">Set it to **Running** to ensure that the service is running.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="dbb08-119">공용 속성</span><span class="sxs-lookup"><span data-stu-id="dbb08-119">Common properties</span></span>

|<span data-ttu-id="dbb08-120">속성</span><span class="sxs-lookup"><span data-stu-id="dbb08-120">Property</span></span> |<span data-ttu-id="dbb08-121">Description</span><span class="sxs-lookup"><span data-stu-id="dbb08-121">Description</span></span> |
|---|---|
|<span data-ttu-id="dbb08-122">DependsOn</span><span class="sxs-lookup"><span data-stu-id="dbb08-122">DependsOn</span></span> |<span data-ttu-id="dbb08-123">이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="dbb08-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="dbb08-124">예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 ID가 ResourceName이고 해당 형식이 ResourceType일 경우, 이 속성을 사용하기 위한 구문은 `DependsOn = "[ResourceType]ResourceName"`입니다.</span><span class="sxs-lookup"><span data-stu-id="dbb08-124">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |

## <a name="additional-information"></a><span data-ttu-id="dbb08-125">추가 정보</span><span class="sxs-lookup"><span data-stu-id="dbb08-125">Additional Information</span></span>

<span data-ttu-id="dbb08-126">**nxService** 리소스는 서비스 정의나 서비스에 대한 스크립트가 존재하지 않는 경우 만들지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dbb08-126">The **nxService** resource will not create a service definition or script for the service if it does not exist.</span></span> <span data-ttu-id="dbb08-127">PowerShell 필요한 상태 구성 **nxFile** 리소스를 사용하여 서비스 정의 파일 또는 스크립트의 존재 또는 내용을 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dbb08-127">You can use the PowerShell Desired State Configuration **nxFile** Resource resource to manage the existence or contents of the service definition file or script.</span></span>

## <a name="example"></a><span data-ttu-id="dbb08-128">예제</span><span class="sxs-lookup"><span data-stu-id="dbb08-128">Example</span></span>

<span data-ttu-id="dbb08-129">다음 예에서는 **SystemD** 서비스 컨트롤러로 등록된 ‘httpd’ 서비스(Apache HTTP Server용)의 구성을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="dbb08-129">The following example shows configuration of the 'httpd' service (for Apache HTTP Server), registered with the **SystemD** service controller.</span></span>

```powershell
Import-DSCResource -Module nx

Node $node
{
    #Apache Service
    nxService ApacheService {
        Name = 'httpd'
        State = 'running'
        Enabled = $true
        Controller = 'systemd'
    }
}
```
