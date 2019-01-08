---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: 노드 간 종속성 지정
ms.openlocfilehash: 1bdfbd9f8a94809d6bf410eff525e1c877fb6aad
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402199"
---
# <a name="specifying-cross-node-dependencies"></a><span data-ttu-id="3812a-103">노드 간 종속성 지정</span><span class="sxs-lookup"><span data-stu-id="3812a-103">Specifying cross-node dependencies</span></span>

> <span data-ttu-id="3812a-104">적용 대상: Windows Powershell 5.0</span><span class="sxs-lookup"><span data-stu-id="3812a-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="3812a-105">DSC는 다른 노드에서 구성에 대한 종속성을 지정하기 위한 구성에 사용할 수 있는 특별한 리소스 **WaitForAll**, **WaitForAny** 및 **WaitForSome**을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="3812a-105">DSC provides special resources, **WaitForAll**, **WaitForAny**, and **WaitForSome** that can be used in configurations to specify dependencies on configurations on other nodes.</span></span> <span data-ttu-id="3812a-106">이러한 리소스의 동작은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3812a-106">The behavior of these resources is as follows:</span></span>

- <span data-ttu-id="3812a-107">**WaitForAll**: 지정된 된 리소스에 정의 된 모든 대상 노드에서 필요한 상태 이면 성공 합니다 **NodeName** 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="3812a-107">**WaitForAll**: Succeeds if the specified resource is in the desired state on all target nodes defined in the **NodeName** property.</span></span>
- <span data-ttu-id="3812a-108">**WaitForAny**: 지정된 된 리소스에 정의 된 대상 노드 중 하나 이상에서 필요한 상태 이면 성공 합니다 **NodeName** 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="3812a-108">**WaitForAny**: Succeeds if the specified resource is in the desired state on at least one of the target nodes defined in the **NodeName** property.</span></span>
- <span data-ttu-id="3812a-109">**WaitForSome**: 지정 된 **NodeCount** 속성 외에을 **NodeName** 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="3812a-109">**WaitForSome**: Specifies a **NodeCount** property in addition to a **NodeName** property.</span></span> <span data-ttu-id="3812a-110">**NodeCount**에서 지정되고 **NodeName** 속성에서 정의된 최소 숫자의 노드에서 리소스가 원하는 상태이면 리소스가 성공합니다.</span><span class="sxs-lookup"><span data-stu-id="3812a-110">The resource succeeds if the resource is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span>

## <a name="syntax"></a><span data-ttu-id="3812a-111">구문</span><span class="sxs-lookup"><span data-stu-id="3812a-111">Syntax</span></span>

<span data-ttu-id="3812a-112">**WaitForAll** 하 고 **WaitForAny** 리소스는 동일한 구문을 공유 합니다.</span><span class="sxs-lookup"><span data-stu-id="3812a-112">The **WaitForAll** and **WaitForAny** resources share the same syntax.</span></span> <span data-ttu-id="3812a-113">바꿉니다 \<ResourceType\> 중 하나를 사용 하 여 아래 예제의 **WaitForAny** 또는 **WaitForAll**합니다.</span><span class="sxs-lookup"><span data-stu-id="3812a-113">Replace \<ResourceType\> in the example below with either **WaitForAny** or **WaitForAll**.</span></span>
<span data-ttu-id="3812a-114">같은 합니다 **DependsOn** "[ResourceType] ResourceName"으로 이름의 형식을 해야 키워드입니다.</span><span class="sxs-lookup"><span data-stu-id="3812a-114">Like the **DependsOn** keyword, you will need to format the name as "[ResourceType]ResourceName".</span></span> <span data-ttu-id="3812a-115">별도의 리소스가 속한 경우 [구성](configurations.md)를 포함 합니다 **ConfigurationName** 서식이 지정 된 문자열에서 "[ResourceType] ResourceName:: [ConfigurationName]:: [ConfigurationName]"입니다.</span><span class="sxs-lookup"><span data-stu-id="3812a-115">If the resource belongs to a separate [Configuration](configurations.md), include the **ConfigurationName** in the formatted string "[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]".</span></span> <span data-ttu-id="3812a-116">합니다 **NodeName** 컴퓨터 또는 노드를 현재 리소스 기다려야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3812a-116">The **NodeName** is the computer, or Node, on which the current resource should wait.</span></span>

```
<ResourceType> [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential]]
    [ RetryCount = [Uint32] ]
    [ RetryIntervalSec = [Uint64] ]
    [ ThrottleLimit = [Uint32]]
}
```

<span data-ttu-id="3812a-117">합니다 **WaitForSome** 리소스 위의 예와 비슷한 구문을 갖지만 추가 합니다 **NodeCount** 키입니다.</span><span class="sxs-lookup"><span data-stu-id="3812a-117">The **WaitForSome** resource has a similar syntax to the example above, but adds the **NodeCount** key.</span></span> <span data-ttu-id="3812a-118">합니다 **NodeCount** 현재 리소스에서 대기 해야 하는 노드 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3812a-118">The **NodeCount** indicates how many Nodes the current resource should wait on.</span></span>

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

<span data-ttu-id="3812a-119">모든 **WaitForXXXX** 다음 구문을 키를 공유 합니다.</span><span class="sxs-lookup"><span data-stu-id="3812a-119">All **WaitForXXXX** share the following syntax keys.</span></span>

<span data-ttu-id="3812a-120">|  속성 |  설명 | | RetryIntervalSec | 다시 시도 하기 전에 시간 (초) 수입니다.</span><span class="sxs-lookup"><span data-stu-id="3812a-120">|  Property  |  Description   | | RetryIntervalSec| The number of seconds before retrying.</span></span> <span data-ttu-id="3812a-121">최소값은 1입니다. | | RetryCount | 최대 다시 시도 횟수입니다. | | ThrottleLimit | 동시에 연결 하는 컴퓨터의 수입니다.</span><span class="sxs-lookup"><span data-stu-id="3812a-121">Minimum is 1.| | RetryCount| The maximum number of times to retry.| | ThrottleLimit| Number of machines to connect simultaneously.</span></span> <span data-ttu-id="3812a-122">기본값은 `New-CimSession` 기본. | | DependsOn | 이 리소스를 구성 하기 전에 다른 리소스의 구성을 실행 해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3812a-122">Default is `New-CimSession` default.| | DependsOn | Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="3812a-123">자세한 내용은 [DependsOn](resource-depends-on.md)| | PsDscRunAsCredential | 참조 [DSC를 사용 하 여 사용자 자격 증명을 사용 하 여](./runAsUser.md) |</span><span class="sxs-lookup"><span data-stu-id="3812a-123">For more information, see [DependsOn](resource-depends-on.md)| | PsDscRunAsCredential | See [Using DSC with User Credentials](./runAsUser.md) |</span></span>


## <a name="using-waitforxxxx-resources"></a><span data-ttu-id="3812a-124">WaitForXXXX 리소스 사용</span><span class="sxs-lookup"><span data-stu-id="3812a-124">Using WaitForXXXX resources</span></span>

<span data-ttu-id="3812a-125">각 **WaitForXXXX** 지정 된 노드에서 완료 하려면 지정된 된 리소스에 대 한 리소스를 대기 합니다.</span><span class="sxs-lookup"><span data-stu-id="3812a-125">Each **WaitForXXXX** resource waits for the specified resources to complete on the specified Node.</span></span> <span data-ttu-id="3812a-126">그런 다음 동일한 구성의 다른 리소스 *에 따라 달라 집니다* 는 **WaitForXXXX** 사용 하 여 리소스를 **DependsOn** 키입니다.</span><span class="sxs-lookup"><span data-stu-id="3812a-126">Other resources in the same Configuration can then *depend on* the **WaitForXXXX** resource using the **DependsOn** key.</span></span>

<span data-ttu-id="3812a-127">예를 들어 다음 구성에서 대상 노드는 대상 노드가 도메인에 가입하기 전에 **xADDomain** 리소스가 **MyDC** 노드에서 최대 30번의 시도를 15초 간격으로 완료할 때까지 대기합니다.</span><span class="sxs-lookup"><span data-stu-id="3812a-127">For example, in the following configuration, the target node is waiting for the **xADDomain** resource to finish on the **MyDC** node with maximum number of 30 retries, at 15-second intervals, before the target node can join the domain.</span></span>

```powershell
Configuration JoinDomain
{
    Import-DscResource -Module xComputerManagement, xActiveDirectory

    Node myDC
    {
        WindowsFeature InstallAD
        {
            Ensure = 'Present'
            Name = 'AD-Domain-Services'
        }

        xADDomain NewDomain
        {
            DomainName = 'Contoso.com'
            DomainAdministratorCredential = (Get-Credential)
            SafemodeAdministratorPassword = (Get-Credential)
            DatabasePath = "C:\Windows\NTDS"
            LogPath = "C:\Windows\NTDS"
            SysvolPath = "C:\Windows\Sysvol"
        }
    }

    Node myDomainJoinedServer
    {
        WaitForAll DC
        {
            ResourceName      = '[xADDomain]NewDomain'
            NodeName          = 'MyDC'
            RetryIntervalSec  = 15
            RetryCount        = 30
        }

        xComputer JoinDomain
        {
            Name             = 'myPC'
            DomainName       = 'Contoso.com'
            Credential       = (Get-Credential)
            DependsOn        ='[WaitForAll]DC'
        }
    }
}
```

<span data-ttu-id="3812a-128">구성을 컴파일하면 두 ".mof" 파일이 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3812a-128">When you compile the Configuration, two ".mof" files are generated.</span></span> <span data-ttu-id="3812a-129">".Mof" 파일을 모두 사용 하 여 대상 노드에 적용 합니다 [Start-dscconfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet</span><span class="sxs-lookup"><span data-stu-id="3812a-129">Apply both ".mof" files to the target Nodes using the [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet</span></span>

><span data-ttu-id="3812a-130">**참고:** WaitForXXX 기본적으로 리소스 번 시도 하 고 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="3812a-130">**Note:** By default the WaitForXXX resources try one time and then fail.</span></span> <span data-ttu-id="3812a-131">필요한 경우에 일반적으로 하려는 지정 된 **RetryCount** 및 **RetryIntervalSec**합니다.</span><span class="sxs-lookup"><span data-stu-id="3812a-131">Although it is not required, you will typically want to specify a **RetryCount** and **RetryIntervalSec**.</span></span>

## <a name="see-also"></a><span data-ttu-id="3812a-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3812a-132">See Also</span></span>

- [<span data-ttu-id="3812a-133">DSC 구성</span><span class="sxs-lookup"><span data-stu-id="3812a-133">DSC Configurations</span></span>](configurations.md)
- [<span data-ttu-id="3812a-134">리소스 종속성을 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="3812a-134">Use Resource Dependencies</span></span>](resource-depends-on.md)
- [<span data-ttu-id="3812a-135">DSC 리소스</span><span class="sxs-lookup"><span data-stu-id="3812a-135">DSC Resources</span></span>](../resources/resources.md)
- [<span data-ttu-id="3812a-136">로컬 구성 관리자 구성</span><span class="sxs-lookup"><span data-stu-id="3812a-136">Configuring The Local Configuration Manager</span></span>](../managing-nodes/metaConfig.md)
