---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 서비스 관리
description: PowerShell은 로컬 및 원격 컴퓨터에서 서비스를 관리하는 데 도움이 되는 여러 cmdlet을 제공합니다.
ms.openlocfilehash: 003803cdaa37e51b3788f3f897cbec7d6e243ca8
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500354"
---
# <a name="managing-services"></a><span data-ttu-id="c477b-104">서비스 관리</span><span class="sxs-lookup"><span data-stu-id="c477b-104">Managing Services</span></span>

<span data-ttu-id="c477b-105">다양한 서비스 작업을 위해 설계된 8개의 핵심 Service cmdlet이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c477b-105">There are eight core Service cmdlets, designed for a wide range of service tasks .</span></span> <span data-ttu-id="c477b-106">이 설명서에서는 실행 중인 서비스의 상태를 표시하고 변경하는 방법에 대해서만 설명하지만 `Get-Help \*-Service`를 사용하여 Service cmdlet의 목록을 보거나 `Get-Help New-Service`와 같은 `Get-Help <Cmdlet-Name>`을 사용하여 각 Service cmdlet에 대한 정보를 찾을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c477b-106">We will look only at listing and changing running state for services, but you can get a list of Service cmdlets by using `Get-Help \*-Service`, and you can find information about each Service cmdlet by using `Get-Help <Cmdlet-Name>`, such as `Get-Help New-Service`.</span></span>

## <a name="getting-services"></a><span data-ttu-id="c477b-107">서비스 가져오기</span><span class="sxs-lookup"><span data-stu-id="c477b-107">Getting Services</span></span>

<span data-ttu-id="c477b-108">`Get-Service` cmdlet을 사용하여 로컬 또는 원격 컴퓨터에 있는 서비스를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c477b-108">You can get the services on a local or remote computer by using the `Get-Service` cmdlet.</span></span> <span data-ttu-id="c477b-109">`Get-Process`와 마찬가지로 `Get-Service` 명령을 매개 변수 없이 사용하면 모든 서비스가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="c477b-109">As with `Get-Process`, using the `Get-Service` command without parameters returns all services.</span></span> <span data-ttu-id="c477b-110">이때 다음과 같이 별표를 와일드카드로 사용하여 이름을 기준으로 필터링할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c477b-110">You can filter by name, even using an asterisk as a wildcard:</span></span>

```powershell
PS> Get-Service -Name se*

Status   Name               DisplayName
------   ----               -----------
Running  seclogon           Secondary Logon
Running  SENS               System Event Notification
Stopped  ServiceLayer       ServiceLayer
```

<span data-ttu-id="c477b-111">서비스의 실제 이름이 항상 분명한 것은 아니기 때문에 서비스를 표시 이름으로 찾아야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c477b-111">Because it is not always obvious what the real name for the service is, you may find you need to find services by display name.</span></span> <span data-ttu-id="c477b-112">이렇게 하려면 다음과 같이 와일드카드를 사용하거나 표시 이름 목록을 사용하여 특정 이름으로 찾으면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c477b-112">You can do this by specific name, using wildcards, or using a list of display names:</span></span>

```powershell
PS> Get-Service -DisplayName se*

Status   Name               DisplayName
------   ----               -----------
Running  lanmanserver       Server
Running  SamSs              Security Accounts Manager
Running  seclogon           Secondary Logon
Stopped  ServiceLayer       ServiceLayer
Running  wscsvc             Security Center

PS> Get-Service -DisplayName ServiceLayer,Server

Status   Name               DisplayName
------   ----               -----------
Running  lanmanserver       Server
Stopped  ServiceLayer       ServiceLayer
```

<span data-ttu-id="c477b-113">Get-Service cmdlet의 ComputerName 매개 변수를 사용하여 원격 컴퓨터의 서비스를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c477b-113">You can use the ComputerName parameter of the Get-Service cmdlet to get the services on remote computers.</span></span> <span data-ttu-id="c477b-114">ComputerName 매개 변수는 여러 개의 값과 와일드카드 문자를 받아들이기 때문에 하나의 명령으로 여러 컴퓨터의 서비스를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c477b-114">The ComputerName parameter accepts multiple values and wildcard characters, so you can get the services on multiple computers with a single command.</span></span> <span data-ttu-id="c477b-115">예를 들어 다음 명령은 Server01 원격 컴퓨터의 서비스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c477b-115">For example, the following command gets the services on the Server01 remote computer.</span></span>

```powershell
Get-Service -ComputerName Server01
```

## <a name="getting-required-and-dependent-services"></a><span data-ttu-id="c477b-116">필수 및 종속 서비스 가져오기</span><span class="sxs-lookup"><span data-stu-id="c477b-116">Getting Required and Dependent Services</span></span>

<span data-ttu-id="c477b-117">Get-Service cmdlet에는 서비스 관리에 매우 유용한 두 개의 매개 변수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c477b-117">The Get-Service cmdlet has two parameters that are very useful in service administration.</span></span> <span data-ttu-id="c477b-118">DependentServices 매개 변수는 이 서비스에 종속된 서비스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c477b-118">The DependentServices parameter gets services that depend on the service.</span></span> <span data-ttu-id="c477b-119">RequiredServices 매개 변수는 이 서비스가 종속된 서비스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c477b-119">The RequiredServices parameter gets services upon which this service depends.</span></span>

<span data-ttu-id="c477b-120">이러한 매개 변수는 Get-Service가 반환하는 System.ServiceProcess.ServiceController 개체의 DependentServices 및 ServicesDependedOn(별칭=RequiredServices) 속성 값을 표시할 뿐만 아니라 명령을 단순화하고 이 정보를 보다 간단하게 가져올 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="c477b-120">These parameters just display the values of the DependentServices and ServicesDependedOn (alias=RequiredServices) properties of the System.ServiceProcess.ServiceController object that Get-Service returns, but they simplify commands and make getting this information much simpler.</span></span>

<span data-ttu-id="c477b-121">다음 명령은 LanmanWorkstation 서비스에 필요한 서비스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c477b-121">The following command gets the services that the LanmanWorkstation service requires.</span></span>

```powershell
PS> Get-Service -Name LanmanWorkstation -RequiredServices

Status   Name               DisplayName
------   ----               -----------
Running  MRxSmb20           SMB 2.0 MiniRedirector
Running  bowser             Bowser
Running  MRxSmb10           SMB 1.x MiniRedirector
Running  NSI                Network Store Interface Service
```

<span data-ttu-id="c477b-122">다음 명령은 LanmanWorkstation 서비스를 필요로 하는 서비스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c477b-122">The following command gets the services that require the LanmanWorkstation service.</span></span>

```powershell
PS> Get-Service -Name LanmanWorkstation -DependentServices

Status   Name               DisplayName
------   ----               -----------
Running  SessionEnv         Terminal Services Configuration
Running  Netlogon           Netlogon
Stopped  Browser            Computer Browser
Running  BITS               Background Intelligent Transfer Ser...
```

<span data-ttu-id="c477b-123">종속성을 가진 모든 서비스를 가져올 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c477b-123">You can even get all services that have dependencies.</span></span> <span data-ttu-id="c477b-124">다음 명령은 종속성을 가진 모든 서비스를 가져온 다음 cmdlet을 사용하여 컴퓨터에 있는 서비스의 Status, Name, RequiredServices 및 DependentServices 속성을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="c477b-124">The following command does just that, and then it uses the Format-Table cmdlet to display the Status, Name, RequiredServices and DependentServices properties of the services on the computer.</span></span>

```powershell
Get-Service -Name * | Where-Object {$_.RequiredServices -or $_.DependentServices} |
  Format-Table -Property Status, Name, RequiredServices, DependentServices -auto
```

## <a name="stopping-starting-suspending-and-restarting-services"></a><span data-ttu-id="c477b-125">서비스 중지, 시작, 일시 중단 및 다시 시작</span><span class="sxs-lookup"><span data-stu-id="c477b-125">Stopping, Starting, Suspending, and Restarting Services</span></span>

<span data-ttu-id="c477b-126">Service cmdlet은 모두 동일한 일반 형식으로 되어 있기 때문에</span><span class="sxs-lookup"><span data-stu-id="c477b-126">The Service cmdlets all have the same general form.</span></span> <span data-ttu-id="c477b-127">서비스를 일반 이름이나 표시 이름으로 지정할 수 있으며 목록과 와일드카드를 값으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c477b-127">Services can be specified by common name or display name, and take lists and wildcards as values.</span></span> <span data-ttu-id="c477b-128">인쇄 스풀러를 중지하려면 다음 명령을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c477b-128">To stop the print spooler, use:</span></span>

```powershell
Stop-Service -Name spooler
```

<span data-ttu-id="c477b-129">인쇄 스풀러를 중지한 후 다시 시작하려면 다음 명령을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c477b-129">To start the print spooler after it is stopped, use:</span></span>

```powershell
Start-Service -Name spooler
```

<span data-ttu-id="c477b-130">인쇄 스풀러를 일시 중단하려면 다음 명령을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c477b-130">To suspend the print spooler, use:</span></span>

```powershell
Suspend-Service -Name spooler
```

<span data-ttu-id="c477b-131">`Restart-Service` cmdlet은 다른 Service cmdlet과 동일한 방식으로 작동하지만, 이 설명서에서는 이 cmdlet에 대해 약간 더 복잡한 예제를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="c477b-131">The `Restart-Service` cmdlet works in the same manner as the other Service cmdlets, but we will show some more complex examples for it.</span></span> <span data-ttu-id="c477b-132">가장 간단한 사용 시나리오에서는 다음과 같이 서비스 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c477b-132">In the simplest use, you specify the name of the service:</span></span>

```powershell
PS> Restart-Service -Name spooler

WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
PS>
```

<span data-ttu-id="c477b-133">그러면 인쇄 스풀러 시작에 대한 경고 메시지가 반복해서 나타나는데,</span><span class="sxs-lookup"><span data-stu-id="c477b-133">You will notice that you get a repeated warning message about the Print Spooler starting up.</span></span> <span data-ttu-id="c477b-134">다소 시간이 걸리는 서비스 작업을 수행하면 Windows PowerShell이 계속 작업을 시도하고 있다는 내용의 메시지를 표시하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="c477b-134">When you perform a service operation that takes some time, Windows PowerShell will notify you that it is still attempting to perform the task.</span></span>

<span data-ttu-id="c477b-135">여러 서비스를 다시 시작하려면 다음과 같이 서비스 목록을 보고, 필터링한 다음 원하는 서비스를 다시 시작하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c477b-135">If you want to restart multiple services, you can get a list of services, filter them, and then perform the restart:</span></span>

```powershell
PS> Get-Service | Where-Object -FilterScript {$_.CanStop} | Restart-Service

WARNING: Waiting for service 'Computer Browser (Browser)' to finish stopping...
WARNING: Waiting for service 'Computer Browser (Browser)' to finish stopping...
Restart-Service : Cannot stop service 'Logical Disk Manager (dmserver)' because
 it has dependent services. It can only be stopped if the Force flag is set.
At line:1 char:57
+ Get-Service | Where-Object -FilterScript {$_.CanStop} | Restart-Service <<<<
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
```

<span data-ttu-id="c477b-136">이러한 Service cmdlet에는 ComputerName 매개 변수가 없지만 Invoke-Command cmdlet을 사용하여 원격 컴퓨터에서 실행할 수는 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c477b-136">These Service cmdlets do not have a ComputerName parameter, but you can run them on a remote computer by using the Invoke-Command cmdlet.</span></span> <span data-ttu-id="c477b-137">예를 들어 다음 명령은 Server01 원격 컴퓨터에서 스풀러 서비스를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="c477b-137">For example, the following command restarts the Spooler service on the Server01 remote computer.</span></span>

```powershell
Invoke-Command -ComputerName Server01 {Restart-Service Spooler}
```

## <a name="setting-service-properties"></a><span data-ttu-id="c477b-138">서비스 속성 설정</span><span class="sxs-lookup"><span data-stu-id="c477b-138">Setting Service Properties</span></span>

<span data-ttu-id="c477b-139">`Set-Service` cmdlet은 로컬 또는 원격 컴퓨터에서 서비스의 속성을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="c477b-139">The `Set-Service` cmdlet changes the properties of a service on a local or remote computer.</span></span> <span data-ttu-id="c477b-140">서비스 상태는 속성이기 때문에 이 cmdlet을 사용하여 서비스를 시작, 중지 및 일시 중단할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c477b-140">Because the service status is a property, you can use this cmdlet to start, stop, and suspend a service.</span></span>
<span data-ttu-id="c477b-141">Set-Service cmdlet에는 서비스 시작 유형을 변경할 수 있도록 해주는 StartupType 매개 변수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c477b-141">The Set-Service cmdlet also has a StartupType parameter that lets you change the service startup type.</span></span>

<span data-ttu-id="c477b-142">Windows Vista 이상에서 `Set-Service`를 사용하려면 “관리자 권한으로 실행” 옵션을 사용하여 Windows PowerShell을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="c477b-142">To use `Set-Service` on Windows Vista and later versions of Windows, open Windows PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="c477b-143">자세한 내용은 [Set-Service](/powershell/module/Microsoft.PowerShell.Management/set-service)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c477b-143">For more information, see [Set-Service](/powershell/module/Microsoft.PowerShell.Management/set-service)</span></span>

## <a name="see-also"></a><span data-ttu-id="c477b-144">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c477b-144">See Also</span></span>

- [<span data-ttu-id="c477b-145">Get-Service</span><span class="sxs-lookup"><span data-stu-id="c477b-145">Get-Service</span></span>](/powershell/module/Microsoft.PowerShell.Management/get-service)
- [<span data-ttu-id="c477b-146">Set-Service</span><span class="sxs-lookup"><span data-stu-id="c477b-146">Set-Service</span></span>](/powershell/module/Microsoft.PowerShell.Management/set-service)
- [<span data-ttu-id="c477b-147">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="c477b-147">Restart-Service</span></span>](/powershell/module/Microsoft.PowerShell.Management/restart-service)
- [<span data-ttu-id="c477b-148">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="c477b-148">Suspend-Service</span></span>](/powershell/module/Microsoft.PowerShell.Management/suspend-service)
