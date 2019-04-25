---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Linux용 DSC nxScript 리소스
ms.openlocfilehash: 339968512ab1c16c4c3785a3a19b00c3fbbf9ea1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077826"
---
# <a name="dsc-for-linux-nxscript-resource"></a><span data-ttu-id="c98e1-103">Linux용 DSC nxScript 리소스</span><span class="sxs-lookup"><span data-stu-id="c98e1-103">DSC for Linux nxScript Resource</span></span>

<span data-ttu-id="c98e1-104">PowerShell DSC(필요한 상태 구성)의 **nxScript** 리소스에서는 Linux 노드에 있는 Linux 스크립트를 실행하는 메커니즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c98e1-104">The **nxScript** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to run Linux scripts on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="c98e1-105">구문</span><span class="sxs-lookup"><span data-stu-id="c98e1-105">Syntax</span></span>

```
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

## <a name="properties"></a><span data-ttu-id="c98e1-106">속성</span><span class="sxs-lookup"><span data-stu-id="c98e1-106">Properties</span></span>

|  <span data-ttu-id="c98e1-107">속성</span><span class="sxs-lookup"><span data-stu-id="c98e1-107">Property</span></span> |  <span data-ttu-id="c98e1-108">설명</span><span class="sxs-lookup"><span data-stu-id="c98e1-108">Description</span></span> |
|---|---|
| <span data-ttu-id="c98e1-109">GetScript</span><span class="sxs-lookup"><span data-stu-id="c98e1-109">GetScript</span></span>| <span data-ttu-id="c98e1-110">[Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet을 호출할 때 실행되는 스크립트를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c98e1-110">Provides a script that runs when you invoke the [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet.</span></span> <span data-ttu-id="c98e1-111">스크립트는 #!/bin/bash와 같은 구조로 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c98e1-111">The script must begin with a shebang, such as #!/bin/bash.</span></span>|
| <span data-ttu-id="c98e1-112">SetScript</span><span class="sxs-lookup"><span data-stu-id="c98e1-112">SetScript</span></span>| <span data-ttu-id="c98e1-113">스크립트를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c98e1-113">Provides a script.</span></span> <span data-ttu-id="c98e1-114">[Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet을 호출하면 **TestScript**가 가장 먼저 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="c98e1-114">When you invoke the [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet, the **TestScript** runs first.</span></span> <span data-ttu-id="c98e1-115">**TestScript** 블록에서 0이 아닌 종료 코드를 반환한다면, **SetScript** 블록이 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="c98e1-115">If the **TestScript** block returns an exit code other than 0, the **SetScript** block will run.</span></span> <span data-ttu-id="c98e1-116">**TestScript**에서 0이라는 종료 코드를 반환한다면, **SetScript**가 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c98e1-116">If the **TestScript** returns an exit code of 0, the **SetScript** will not run.</span></span> <span data-ttu-id="c98e1-117">스크립트는 `#!/bin/bash`와 같은 구조로 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c98e1-117">The script must begin with a shebang, such as `#!/bin/bash`.</span></span>|
| <span data-ttu-id="c98e1-118">TestScript</span><span class="sxs-lookup"><span data-stu-id="c98e1-118">TestScript</span></span>| <span data-ttu-id="c98e1-119">스크립트를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c98e1-119">Provides a script.</span></span> <span data-ttu-id="c98e1-120">[Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet을 호출하면 이 스크립트가 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="c98e1-120">When you invoke the [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet, this script runs.</span></span> <span data-ttu-id="c98e1-121">이 스크립트에서 0이 아닌 종료 코드를 반환한다면, SetScript가 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="c98e1-121">If it returns an exit code other than 0, the SetScript will run.</span></span> <span data-ttu-id="c98e1-122">이 스크립트에서 0이라는 종료 코드를 반환한다면, **SetScript**가 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c98e1-122">If it returns an exit code of 0, the **SetScript** will not run.</span></span> <span data-ttu-id="c98e1-123">[Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) cmdlet을 호출하면 **TestScript**도 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="c98e1-123">The **TestScript** also runs when you invoke the [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) cmdlet.</span></span> <span data-ttu-id="c98e1-124">그러나 이 경우에서는 **TestScript**에서 어떤 종료 코드가 반환되는지 관계없이 **SetScript**가 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c98e1-124">However, in this case, the **SetScript** will not run, no matter what exit code is returned from the **TestScript**.</span></span> <span data-ttu-id="c98e1-125">실제 구성이 현재 필요한 상태 구성과 일치하는 경우 **TestScript**는 종료 코드 0을 반환해야 하고, 일치하지 않는 경우에는 0이 아닌 종료 코드를 반환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c98e1-125">The **TestScript** must return an exit code of 0 if the actual configuration matches the current desired state configuration, and an exit code other than 0 if it does not match.</span></span> <span data-ttu-id="c98e1-126">(현재 필요한 상태 구성은 DSC를 사용하는 노드에서 시행된 마지막 구성입니다.)</span><span class="sxs-lookup"><span data-stu-id="c98e1-126">(The current desired state configuration is the last configuration enacted on the node that is using DSC).</span></span> <span data-ttu-id="c98e1-127">스크립트는 1#!/bin/bash.1과 같은 구조로 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c98e1-127">The script must begin with a shebang, such as 1#!/bin/bash.1</span></span>|
| <span data-ttu-id="c98e1-128">사용자</span><span class="sxs-lookup"><span data-stu-id="c98e1-128">User</span></span>| <span data-ttu-id="c98e1-129">스크립트를 실행할 권한이 있는 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="c98e1-129">The user to run the script as.</span></span>|
| <span data-ttu-id="c98e1-130">그룹</span><span class="sxs-lookup"><span data-stu-id="c98e1-130">Group</span></span>| <span data-ttu-id="c98e1-131">스크립트를 실행할 권한이 있는 그룹입니다.</span><span class="sxs-lookup"><span data-stu-id="c98e1-131">The group to run the script as.</span></span>|
| <span data-ttu-id="c98e1-132">DependsOn</span><span class="sxs-lookup"><span data-stu-id="c98e1-132">DependsOn</span></span> | <span data-ttu-id="c98e1-133">이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c98e1-133">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="c98e1-134">예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 **ID**가 **ResourceName**이고 해당 형식이 **ResourceType**일 경우, 이 속성을 사용하기 위한 구문은 `DependsOn = "[ResourceType]ResourceName"`입니다.</span><span class="sxs-lookup"><span data-stu-id="c98e1-134">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="c98e1-135">예제</span><span class="sxs-lookup"><span data-stu-id="c98e1-135">Example</span></span>

<span data-ttu-id="c98e1-136">다음 예제에서는 추가적인 구성 관리를 수행하는 **nxScript** 리소스 사용을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c98e1-136">The following example demonstrates the use of the **nxScript** resource to perform additional configuration management.</span></span>

```
Import-DSCResource -Module nx

Node $node {
nxScript KeepDirEmpty{

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