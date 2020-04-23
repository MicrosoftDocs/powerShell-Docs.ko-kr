---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: Linux용 DSC nxScript 리소스
ms.openlocfilehash: a7f2114aba47bb581cdd19168e784b79dfc5b6ad
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2020
ms.locfileid: "71953190"
---
# <a name="dsc-for-linux-nxscript-resource"></a><span data-ttu-id="1787a-103">Linux용 DSC nxScript 리소스</span><span class="sxs-lookup"><span data-stu-id="1787a-103">DSC for Linux nxScript Resource</span></span>

<span data-ttu-id="1787a-104">PowerShell DSC(필요한 상태 구성)의 **nxScript** 리소스에서는 Linux 노드에 있는 Linux 스크립트를 실행하는 메커니즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1787a-104">The **nxScript** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to run Linux scripts on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="1787a-105">구문</span><span class="sxs-lookup"><span data-stu-id="1787a-105">Syntax</span></span>

```Syntax
nxScript <string> #ResourceName
{
    GetScript = <string>
    SetScript = <string>
    TestScript = <string>
    [ User = <string> ]
    [ Group = <string> ]
    [ DependsOn = <string[]> ]
}
```

## <a name="properties"></a><span data-ttu-id="1787a-106">속성</span><span class="sxs-lookup"><span data-stu-id="1787a-106">Properties</span></span>

|<span data-ttu-id="1787a-107">속성</span><span class="sxs-lookup"><span data-stu-id="1787a-107">Property</span></span> |<span data-ttu-id="1787a-108">Description</span><span class="sxs-lookup"><span data-stu-id="1787a-108">Description</span></span> |
|---|---|
|<span data-ttu-id="1787a-109">GetScript</span><span class="sxs-lookup"><span data-stu-id="1787a-109">GetScript</span></span> |<span data-ttu-id="1787a-110">머신의 현재 상태를 반환하는 스크립트를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1787a-110">Provides a script to return current status of the machine.</span></span> <span data-ttu-id="1787a-111">이 스크립트는 [GetDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) 스크립트를 호출할 때 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="1787a-111">This script runs when you invoke the [GetDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) script.</span></span> <span data-ttu-id="1787a-112">스크립트는 `#!/bin/bash`와 같은 구조로 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1787a-112">The script must begin with a shebang, such as `#!/bin/bash`.</span></span> |
|<span data-ttu-id="1787a-113">SetScript</span><span class="sxs-lookup"><span data-stu-id="1787a-113">SetScript</span></span> |<span data-ttu-id="1787a-114">머신을 올바른 상태로 전환하는 스크립트를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1787a-114">Provides a script that puts the machine in the correct state.</span></span> <span data-ttu-id="1787a-115">[StartDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) 스크립트를 호출하면 **TestScript**가 먼저 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="1787a-115">When you invoke the [StartDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) script, the **TestScript** runs first.</span></span> <span data-ttu-id="1787a-116">**TestScript** 블록에서 0이 아닌 종료 코드를 반환한다면, **SetScript** 블록이 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="1787a-116">If the **TestScript** block returns an exit code other than 0, the **SetScript** block will run.</span></span> <span data-ttu-id="1787a-117">**TestScript**에서 0이라는 종료 코드를 반환한다면, **SetScript**가 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1787a-117">If the **TestScript** returns an exit code of 0, the **SetScript** will not run.</span></span> <span data-ttu-id="1787a-118">스크립트는 `#!/bin/bash`와 같은 구조로 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1787a-118">The script must begin with a shebang, such as `#!/bin/bash`.</span></span> |
|<span data-ttu-id="1787a-119">TestScript</span><span class="sxs-lookup"><span data-stu-id="1787a-119">TestScript</span></span> |<span data-ttu-id="1787a-120">현재 노드가 올바른 상태인지 여부를 평가하는 스크립트를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1787a-120">Provides a script that evaluates whether the node is currently in the correct state.</span></span> <span data-ttu-id="1787a-121">[StartDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) 스크립트를 호출하면 이 스크립트가 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="1787a-121">When you invoke the [StartDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) script, this script runs.</span></span> <span data-ttu-id="1787a-122">이 스크립트에서 0이 아닌 종료 코드를 반환한다면, **SetScript**가 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="1787a-122">If it returns an exit code other than 0, the **SetScript** will run.</span></span> <span data-ttu-id="1787a-123">이 스크립트에서 0이라는 종료 코드를 반환한다면, **SetScript**가 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1787a-123">If it returns an exit code of 0, the **SetScript** will not run.</span></span> <span data-ttu-id="1787a-124">**Test-DscConfiguration** 스크립트를 호출하면 [TestScript](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer)도 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="1787a-124">The **TestScript** also runs when you invoke the [TestDscConfiguration](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) script.</span></span> <span data-ttu-id="1787a-125">그러나 이 경우에서는 **TestScript**에서 어떤 종료 코드가 반환되는지 관계없이 **SetScript**가 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1787a-125">However, in this case, the **SetScript** will not run, no matter what exit code is returned from the **TestScript**.</span></span> <span data-ttu-id="1787a-126">실제 구성이 현재 필요한 상태 구성과 일치하는 경우 **TestScript**는 콘텐츠를 포함하고 종료 코드 0을 반환해야 하며, 일치하지 않는 경우에는 0이 아닌 종료 코드를 반환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1787a-126">The **TestScript** must contain content and must return an exit code of 0 if the actual configuration matches the current desired state configuration, and an exit code other than 0 if it does not match.</span></span> <span data-ttu-id="1787a-127">현재 필요한 상태 구성은 DSC를 사용하는 노드에서 시행된 마지막 구성입니다.</span><span class="sxs-lookup"><span data-stu-id="1787a-127">The current desired state configuration is the last configuration enacted on the node that is using DSC.</span></span> <span data-ttu-id="1787a-128">스크립트는 `#!/bin/bash`와 같은 구조로 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1787a-128">The script must begin with a shebang, such as `#!/bin/bash`.</span></span> |
|<span data-ttu-id="1787a-129">사용자</span><span class="sxs-lookup"><span data-stu-id="1787a-129">User</span></span> |<span data-ttu-id="1787a-130">스크립트를 실행할 권한이 있는 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="1787a-130">The user to run the script as.</span></span> |
|<span data-ttu-id="1787a-131">그룹</span><span class="sxs-lookup"><span data-stu-id="1787a-131">Group</span></span> |<span data-ttu-id="1787a-132">스크립트를 실행할 권한이 있는 그룹입니다.</span><span class="sxs-lookup"><span data-stu-id="1787a-132">The group to run the script as.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="1787a-133">공용 속성</span><span class="sxs-lookup"><span data-stu-id="1787a-133">Common properties</span></span>

|<span data-ttu-id="1787a-134">속성</span><span class="sxs-lookup"><span data-stu-id="1787a-134">Property</span></span> |<span data-ttu-id="1787a-135">Description</span><span class="sxs-lookup"><span data-stu-id="1787a-135">Description</span></span> |
|---|---|
|<span data-ttu-id="1787a-136">DependsOn</span><span class="sxs-lookup"><span data-stu-id="1787a-136">DependsOn</span></span> |<span data-ttu-id="1787a-137">이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1787a-137">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="1787a-138">예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 ID가 ResourceName이고 해당 형식이 ResourceType일 경우, 이 속성을 사용하기 위한 구문은 `DependsOn = "[ResourceType]ResourceName"`입니다.</span><span class="sxs-lookup"><span data-stu-id="1787a-138">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |

## <a name="example"></a><span data-ttu-id="1787a-139">예제</span><span class="sxs-lookup"><span data-stu-id="1787a-139">Example</span></span>

<span data-ttu-id="1787a-140">다음 예제에서는 추가적인 구성 관리를 수행하는 **nxScript** 리소스 사용을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1787a-140">The following example demonstrates the use of the **nxScript** resource to perform additional configuration management.</span></span>

```powershell
Import-DSCResource -Module nx

Node $node
{
    nxScript KeepDirEmpty {

    GetScript = @"
#!/bin/bash
ls /tmp/mydir/ | wc -l
"@

    SetScript = @"
#!/bin/bash
rm -rf /tmp/mydir/*
"@

    TestScript = @'
#!/bin/bash
filecount=`ls /tmp/mydir | wc -l`
if [ $filecount -gt 0 ]
then
    exit 1
else
    exit 0
fi
'@
    }
}
```
