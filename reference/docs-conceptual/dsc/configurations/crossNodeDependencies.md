---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: 노드 간 종속성 지정
description: DSC는 다른 노드에서 구성에 대한 종속성을 지정하기 위해 구성에 사용되는 특별한 리소스를 제공합니다.
ms.openlocfilehash: a9fc09af922839b37db476c24c113efc5e3e8cb1
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92658496"
---
# <a name="specifying-cross-node-dependencies"></a><span data-ttu-id="5957f-104">노드 간 종속성 지정</span><span class="sxs-lookup"><span data-stu-id="5957f-104">Specifying cross-node dependencies</span></span>

> <span data-ttu-id="5957f-105">적용 대상: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="5957f-105">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="5957f-106">DSC는 다른 노드에서 구성에 대한 종속성을 지정하기 위한 구성에 사용할 수 있는 특별한 리소스 **WaitForAll** , **WaitForAny** 및 **WaitForSome** 을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="5957f-106">DSC provides special resources, **WaitForAll** , **WaitForAny** , and **WaitForSome** that can be used in configurations to specify dependencies on configurations on other nodes.</span></span> <span data-ttu-id="5957f-107">이러한 리소스의 동작은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="5957f-107">The behavior of these resources is as follows:</span></span>

- <span data-ttu-id="5957f-108">**WaitForAll** : **NodeName** 속성에 정의된 모든 대상 노드에서 지정된 리소스가 원하는 상태이면 성공합니다.</span><span class="sxs-lookup"><span data-stu-id="5957f-108">**WaitForAll** : Succeeds if the specified resource is in the desired state on all target nodes defined in the **NodeName** property.</span></span>
- <span data-ttu-id="5957f-109">**WaitForAny** : **NodeName** 속성에 정의된 대상 노드 중 최소 하나 이상에서 지정된 리소스가 원하는 상태이면 성공합니다.</span><span class="sxs-lookup"><span data-stu-id="5957f-109">**WaitForAny** : Succeeds if the specified resource is in the desired state on at least one of the target nodes defined in the **NodeName** property.</span></span>
- <span data-ttu-id="5957f-110">**WaitForSome** : **NodeName** 속성과 더불어 **NodeCount** 속성을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5957f-110">**WaitForSome** : Specifies a **NodeCount** property in addition to a **NodeName** property.</span></span> <span data-ttu-id="5957f-111">**NodeCount** 에서 지정되고 **NodeName** 속성에서 정의된 최소 숫자의 노드에서 리소스가 원하는 상태이면 리소스가 성공합니다.</span><span class="sxs-lookup"><span data-stu-id="5957f-111">The resource succeeds if the resource is in the desired state on a minimum number of nodes (specified by **NodeCount** ) defined by the **NodeName** property.</span></span>

## <a name="syntax"></a><span data-ttu-id="5957f-112">Syntax</span><span class="sxs-lookup"><span data-stu-id="5957f-112">Syntax</span></span>

<span data-ttu-id="5957f-113">**WaitForAll** 및 **WaitForAny** 리소스는 동일한 구문을 공유합니다.</span><span class="sxs-lookup"><span data-stu-id="5957f-113">The **WaitForAll** and **WaitForAny** resources share the same syntax.</span></span> <span data-ttu-id="5957f-114">아래 예제에서 `<ResourceType>`을 **WaitForAny** 또는 **WaitForAll** 로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="5957f-114">Replace `<ResourceType>` in the example below with either **WaitForAny** or **WaitForAll**.</span></span> <span data-ttu-id="5957f-115">**DependsOn** 키워드처럼 `[ResourceType]ResourceName`으로 이름 형식을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5957f-115">Like the **DependsOn** keyword, you will need to format the name as `[ResourceType]ResourceName`.</span></span> <span data-ttu-id="5957f-116">리소스가 별도 [구성](configurations.md)에 속하는 경우에는 **ConfigurationName** 을 형식 문자열 `[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]`에 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="5957f-116">If the resource belongs to a separate [Configuration](configurations.md), include the **ConfigurationName** in the formatted string `[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]`.</span></span> <span data-ttu-id="5957f-117">**NodeName** 은 현재 리소스가 기다려야 하는 컴퓨터 또는 노드입니다.</span><span class="sxs-lookup"><span data-stu-id="5957f-117">The **NodeName** is the computer, or Node, on which the current resource should wait.</span></span>

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

<span data-ttu-id="5957f-118">**WaitForSome** 리소스에는 위의 예제와 비슷한 구문이 있지만, **NodeCount** 키가 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="5957f-118">The **WaitForSome** resource has a similar syntax to the example above, but adds the **NodeCount** key.</span></span> <span data-ttu-id="5957f-119">**NodeCount** 는 현재 리소스가 기다려야 하는 노드 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5957f-119">The **NodeCount** indicates how many Nodes the current resource should wait on.</span></span>

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

<span data-ttu-id="5957f-120">모든 **WaitForXXXX** 는 다음 구문 키를 공유합니다.</span><span class="sxs-lookup"><span data-stu-id="5957f-120">All **WaitForXXXX** share the following syntax keys.</span></span>

|       <span data-ttu-id="5957f-121">속성</span><span class="sxs-lookup"><span data-stu-id="5957f-121">Property</span></span>       |                                                                           <span data-ttu-id="5957f-122">설명</span><span class="sxs-lookup"><span data-stu-id="5957f-122">Description</span></span>                                                                           |
| -------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="5957f-123">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="5957f-123">RetryIntervalSec</span></span>     | <span data-ttu-id="5957f-124">다시 시도할 때까지의 시간(초)입니다.</span><span class="sxs-lookup"><span data-stu-id="5957f-124">The number of seconds before retrying.</span></span> <span data-ttu-id="5957f-125">최소값은 1입니다.</span><span class="sxs-lookup"><span data-stu-id="5957f-125">Minimum is 1.</span></span>                                                                                                            |
| <span data-ttu-id="5957f-126">RetryCount</span><span class="sxs-lookup"><span data-stu-id="5957f-126">RetryCount</span></span>           | <span data-ttu-id="5957f-127">최대 다시 시도 횟수입니다.</span><span class="sxs-lookup"><span data-stu-id="5957f-127">The maximum number of times to retry.</span></span>                                                                                                                           |
| <span data-ttu-id="5957f-128">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="5957f-128">ThrottleLimit</span></span>        | <span data-ttu-id="5957f-129">동시에 연결하는 컴퓨터의 수입니다.</span><span class="sxs-lookup"><span data-stu-id="5957f-129">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="5957f-130">기본값은 `New-CimSession` 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="5957f-130">Default is `New-CimSession` default.</span></span>                                                                              |
| <span data-ttu-id="5957f-131">DependsOn</span><span class="sxs-lookup"><span data-stu-id="5957f-131">DependsOn</span></span>            | <span data-ttu-id="5957f-132">이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5957f-132">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="5957f-133">자세한 내용은 [DependsOn](resource-depends-on.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5957f-133">For more information, see [DependsOn](resource-depends-on.md)</span></span> |
| <span data-ttu-id="5957f-134">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="5957f-134">PsDscRunAsCredential</span></span> | <span data-ttu-id="5957f-135">[사용자 자격 증명을 사용하여 DSC 실행](./runAsUser.md) 참조</span><span class="sxs-lookup"><span data-stu-id="5957f-135">See [Using DSC with User Credentials](./runAsUser.md)</span></span>                                                                                                           |

## <a name="using-waitforxxxx-resources"></a><span data-ttu-id="5957f-136">WaitForXXXX 리소스 사용</span><span class="sxs-lookup"><span data-stu-id="5957f-136">Using WaitForXXXX resources</span></span>

<span data-ttu-id="5957f-137">각 **WaitForXXXX** 리소스는 지정된 리소스가 지정된 노드에서 완료될 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="5957f-137">Each **WaitForXXXX** resource waits for the specified resources to complete on the specified Node.</span></span>
<span data-ttu-id="5957f-138">동일한 구성의 다른 리소스는 **DependsOn** 키를 사용하는 **WaitForXXXX** 리소스에 따라 ‘달라’질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5957f-138">Other resources in the same Configuration can then *depend on* the **WaitForXXXX** resource using the **DependsOn** key.</span></span>

<span data-ttu-id="5957f-139">예를 들어 다음 구성에서 대상 노드는 대상 노드가 도메인에 가입하기 전에 **xADDomain** 리소스가 **MyDC** 노드에서 최대 30번의 시도를 15초 간격으로 완료할 때까지 대기합니다.</span><span class="sxs-lookup"><span data-stu-id="5957f-139">For example, in the following configuration, the target node is waiting for the **xADDomain** resource to finish on the **MyDC** node with maximum number of 30 retries, at 15-second intervals, before the target node can join the domain.</span></span>

<span data-ttu-id="5957f-140">기본적으로 **WaitForXXX** 리소스는 한 번 시도한 다음, 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="5957f-140">By default the **WaitForXXX** resources try one time and then fail.</span></span> <span data-ttu-id="5957f-141">필수는 아니지만 일반적으로 **RetryCount** 및 **RetryIntervalSec** 을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5957f-141">Although it is not required, you will typically want to specify a **RetryCount** and **RetryIntervalSec**.</span></span>

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

<span data-ttu-id="5957f-142">구성을 컴파일하면 두 개의 ".mof" 파일이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="5957f-142">When you compile the Configuration, two ".mof" files are generated.</span></span> <span data-ttu-id="5957f-143">[Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet을 사용하여 대상 노드에 ".mof" 파일을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="5957f-143">Apply both ".mof" files to the target Nodes using the [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet</span></span>

> [!NOTE]
> <span data-ttu-id="5957f-144">**WaitForXXX** 리소스는 Windows 원격 관리를 사용하여 다른 노드의 상태를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="5957f-144">**WaitForXXX** resources use Windows Remote Management to check the state of other Nodes.</span></span> <span data-ttu-id="5957f-145">WinRM에 대한 포트 및 보안 요구 사항에 대한 자세한 내용은 [PowerShell Remoting 보안 고려 사항](/powershell/scripting/learn/remoting/winrmsecurity)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5957f-145">For more information about port and security requirements for WinRM, see [PowerShell Remoting Security Considerations](/powershell/scripting/learn/remoting/winrmsecurity).</span></span>

## <a name="see-also"></a><span data-ttu-id="5957f-146">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5957f-146">See Also</span></span>

- [<span data-ttu-id="5957f-147">DSC 구성</span><span class="sxs-lookup"><span data-stu-id="5957f-147">DSC Configurations</span></span>](configurations.md)
- [<span data-ttu-id="5957f-148">리소스 종속성 나열</span><span class="sxs-lookup"><span data-stu-id="5957f-148">Use Resource Dependencies</span></span>](resource-depends-on.md)
- [<span data-ttu-id="5957f-149">DSC 리소스</span><span class="sxs-lookup"><span data-stu-id="5957f-149">DSC Resources</span></span>](../resources/resources.md)
- [<span data-ttu-id="5957f-150">로컬 구성 관리자 구성</span><span class="sxs-lookup"><span data-stu-id="5957f-150">Configuring The Local Configuration Manager</span></span>](../managing-nodes/metaConfig.md)
