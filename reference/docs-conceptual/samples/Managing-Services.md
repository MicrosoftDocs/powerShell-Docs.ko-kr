---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 서비스 관리
ms.openlocfilehash: 7a238a3fea857c5dac1c12ca0d0371a49e6bf58c
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75870526"
---
# <a name="managing-services"></a><span data-ttu-id="cd99d-103">서비스 관리</span><span class="sxs-lookup"><span data-stu-id="cd99d-103">Managing Services</span></span>

<span data-ttu-id="cd99d-104">다양한 서비스 작업을 위해 설계된 8개의 핵심 Service cmdlet이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd99d-104">There are eight core Service cmdlets, designed for a wide range of service tasks .</span></span> <span data-ttu-id="cd99d-105">이 설명서에서는 실행 중인 서비스의 상태를 표시하고 변경하는 방법에 대해서만 설명하지만 `Get-Help \*-Service`를 사용하여 Service cmdlet의 목록을 보거나 `Get-Help New-Service`와 같은 `Get-Help <Cmdlet-Name>`을 사용하여 각 Service cmdlet에 대한 정보를 찾을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd99d-105">We will look only at listing and changing running state for services, but you can get a list of Service cmdlets by using `Get-Help \*-Service`, and you can find information about each Service cmdlet by using `Get-Help <Cmdlet-Name>`, such as `Get-Help New-Service`.</span></span>

## <a name="getting-services"></a><span data-ttu-id="cd99d-106">서비스 가져오기</span><span class="sxs-lookup"><span data-stu-id="cd99d-106">Getting Services</span></span>

<span data-ttu-id="cd99d-107">`Get-Service` cmdlet을 사용하여 로컬 또는 원격 컴퓨터에 있는 서비스를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd99d-107">You can get the services on a local or remote computer by using the `Get-Service` cmdlet.</span></span> <span data-ttu-id="cd99d-108">`Get-Process`와 마찬가지로 `Get-Service` 명령을 매개 변수 없이 사용하면 모든 서비스가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd99d-108">As with `Get-Process`, using the `Get-Service` command without parameters returns all services.</span></span> <span data-ttu-id="cd99d-109">이때 다음과 같이 별표를 와일드카드로 사용하여 이름을 기준으로 필터링할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd99d-109">You can filter by name, even using an asterisk as a wildcard:</span></span>

```powershell
PS> Get-Service -Name se*

Status   Name               DisplayName
------   ----               -----------
Running  seclogon           Secondary Logon
Running  SENS               System Event Notification
Stopped  ServiceLayer       ServiceLayer
```

<span data-ttu-id="cd99d-110">서비스의 실제 이름이 항상 분명한 것은 아니기 때문에 서비스를 표시 이름으로 찾아야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd99d-110">Because it is not always obvious what the real name for the service is, you may find you need to find services by display name.</span></span> <span data-ttu-id="cd99d-111">이렇게 하려면 다음과 같이 와일드카드를 사용하거나 표시 이름 목록을 사용하여 특정 이름으로 찾으면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd99d-111">You can do this by specific name, using wildcards, or using a list of display names:</span></span>

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

<span data-ttu-id="cd99d-112">Get-Service cmdlet의 ComputerName 매개 변수를 사용하여 원격 컴퓨터의 서비스를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd99d-112">You can use the ComputerName parameter of the Get-Service cmdlet to get the services on remote computers.</span></span> <span data-ttu-id="cd99d-113">ComputerName 매개 변수는 여러 개의 값과 와일드카드 문자를 받아들이기 때문에 하나의 명령으로 여러 컴퓨터의 서비스를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd99d-113">The ComputerName parameter accepts multiple values and wildcard characters, so you can get the services on multiple computers with a single command.</span></span> <span data-ttu-id="cd99d-114">예를 들어 다음 명령은 Server01 원격 컴퓨터의 서비스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="cd99d-114">For example, the following command gets the services on the Server01 remote computer.</span></span>

```powershell
Get-Service -ComputerName Server01
```

## <a name="getting-required-and-dependent-services"></a><span data-ttu-id="cd99d-115">필수 및 종속 서비스 가져오기</span><span class="sxs-lookup"><span data-stu-id="cd99d-115">Getting Required and Dependent Services</span></span>

<span data-ttu-id="cd99d-116">Get-Service cmdlet에는 서비스 관리에 매우 유용한 두 개의 매개 변수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd99d-116">The Get-Service cmdlet has two parameters that are very useful in service administration.</span></span> <span data-ttu-id="cd99d-117">DependentServices 매개 변수는 이 서비스에 종속된 서비스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="cd99d-117">The DependentServices parameter gets services that depend on the service.</span></span> <span data-ttu-id="cd99d-118">RequiredServices 매개 변수는 이 서비스가 종속된 서비스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="cd99d-118">The RequiredServices parameter gets services upon which this service depends.</span></span>

<span data-ttu-id="cd99d-119">이러한 매개 변수는 Get-Service가 반환하는 System.ServiceProcess.ServiceController 개체의 DependentServices 및 ServicesDependedOn(별칭=RequiredServices) 속성 값을 표시할 뿐만 아니라 명령을 단순화하고 이 정보를 보다 간단하게 가져올 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd99d-119">These parameters just display the values of the DependentServices and ServicesDependedOn (alias=RequiredServices) properties of the System.ServiceProcess.ServiceController object that Get-Service returns, but they simplify commands and make getting this information much simpler.</span></span>

<span data-ttu-id="cd99d-120">다음 명령은 LanmanWorkstation 서비스에 필요한 서비스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="cd99d-120">The following command gets the services that the LanmanWorkstation service requires.</span></span>

```powershell
PS> Get-Service -Name LanmanWorkstation -RequiredServices

Status   Name               DisplayName
------   ----               -----------
Running  MRxSmb20           SMB 2.0 MiniRedirector
Running  bowser             Bowser
Running  MRxSmb10           SMB 1.x MiniRedirector
Running  NSI                Network Store Interface Service
```

<span data-ttu-id="cd99d-121">다음 명령은 LanmanWorkstation 서비스를 필요로 하는 서비스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="cd99d-121">The following command gets the services that require the LanmanWorkstation service.</span></span>

```powershell
PS> Get-Service -Name LanmanWorkstation -DependentServices

Status   Name               DisplayName
------   ----               -----------
Running  SessionEnv         Terminal Services Configuration
Running  Netlogon           Netlogon
Stopped  Browser            Computer Browser
Running  BITS               Background Intelligent Transfer Ser...
```

<span data-ttu-id="cd99d-122">종속성을 가진 모든 서비스를 가져올 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd99d-122">You can even get all services that have dependencies.</span></span> <span data-ttu-id="cd99d-123">다음 명령은 종속성을 가진 모든 서비스를 가져온 다음 cmdlet을 사용하여 컴퓨터에 있는 서비스의 Status, Name, RequiredServices 및 DependentServices 속성을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="cd99d-123">The following command does just that, and then it uses the Format-Table cmdlet to display the Status, Name, RequiredServices and DependentServices properties of the services on the computer.</span></span>

```powershell
Get-Service -Name * | Where-Object {$_.RequiredServices -or $_.DependentServices} |
  Format-Table -Property Status, Name, RequiredServices, DependentServices -auto
```

## <a name="stopping-starting-suspending-and-restarting-services"></a><span data-ttu-id="cd99d-124">서비스 중지, 시작, 일시 중단 및 다시 시작</span><span class="sxs-lookup"><span data-stu-id="cd99d-124">Stopping, Starting, Suspending, and Restarting Services</span></span>

<span data-ttu-id="cd99d-125">Service cmdlet은 모두 동일한 일반 형식으로 되어 있기 때문에</span><span class="sxs-lookup"><span data-stu-id="cd99d-125">The Service cmdlets all have the same general form.</span></span> <span data-ttu-id="cd99d-126">서비스를 일반 이름이나 표시 이름으로 지정할 수 있으며 목록과 와일드카드를 값으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd99d-126">Services can be specified by common name or display name, and take lists and wildcards as values.</span></span> <span data-ttu-id="cd99d-127">인쇄 스풀러를 중지하려면 다음 명령을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="cd99d-127">To stop the print spooler, use:</span></span>

```powershell
Stop-Service -Name spooler
```

<span data-ttu-id="cd99d-128">인쇄 스풀러를 중지한 후 다시 시작하려면 다음 명령을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="cd99d-128">To start the print spooler after it is stopped, use:</span></span>

```powershell
Start-Service -Name spooler
```

<span data-ttu-id="cd99d-129">인쇄 스풀러를 일시 중단하려면 다음 명령을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="cd99d-129">To suspend the print spooler, use:</span></span>

```powershell
Suspend-Service -Name spooler
```

<span data-ttu-id="cd99d-130">`Restart-Service` cmdlet은 다른 Service cmdlet과 동일한 방식으로 작동하지만, 이 설명서에서는 이 cmdlet에 대해 약간 더 복잡한 예제를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="cd99d-130">The `Restart-Service` cmdlet works in the same manner as the other Service cmdlets, but we will show some more complex examples for it.</span></span> <span data-ttu-id="cd99d-131">가장 간단한 사용 시나리오에서는 다음과 같이 서비스 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="cd99d-131">In the simplest use, you specify the name of the service:</span></span>

```powershell
PS> Restart-Service -Name spooler

WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
PS>
```

<span data-ttu-id="cd99d-132">그러면 인쇄 스풀러 시작에 대한 경고 메시지가 반복해서 나타나는데,</span><span class="sxs-lookup"><span data-stu-id="cd99d-132">You will notice that you get a repeated warning message about the Print Spooler starting up.</span></span> <span data-ttu-id="cd99d-133">다소 시간이 걸리는 서비스 작업을 수행하면 Windows PowerShell이 계속 작업을 시도하고 있다는 내용의 메시지를 표시하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="cd99d-133">When you perform a service operation that takes some time, Windows PowerShell will notify you that it is still attempting to perform the task.</span></span>

<span data-ttu-id="cd99d-134">여러 서비스를 다시 시작하려면 다음과 같이 서비스 목록을 보고, 필터링한 다음 원하는 서비스를 다시 시작하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd99d-134">If you want to restart multiple services, you can get a list of services, filter them, and then perform the restart:</span></span>

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

<span data-ttu-id="cd99d-135">이러한 Service cmdlet에는 ComputerName 매개 변수가 없지만 Invoke-Command cmdlet을 사용하여 원격 컴퓨터에서 실행할 수는 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd99d-135">These Service cmdlets do not have a ComputerName parameter, but you can run them on a remote computer by using the Invoke-Command cmdlet.</span></span> <span data-ttu-id="cd99d-136">예를 들어 다음 명령은 Server01 원격 컴퓨터에서 스풀러 서비스를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="cd99d-136">For example, the following command restarts the Spooler service on the Server01 remote computer.</span></span>

```powershell
Invoke-Command -ComputerName Server01 {Restart-Service Spooler}
```

## <a name="setting-service-properties"></a><span data-ttu-id="cd99d-137">서비스 속성 설정</span><span class="sxs-lookup"><span data-stu-id="cd99d-137">Setting Service Properties</span></span>

<span data-ttu-id="cd99d-138">`Set-Service` cmdlet은 로컬 또는 원격 컴퓨터에서 서비스의 속성을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="cd99d-138">The `Set-Service` cmdlet changes the properties of a service on a local or remote computer.</span></span> <span data-ttu-id="cd99d-139">서비스 상태는 속성이기 때문에 이 cmdlet을 사용하여 서비스를 시작, 중지 및 일시 중단할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd99d-139">Because the service status is a property, you can use this cmdlet to start, stop, and suspend a service.</span></span>
<span data-ttu-id="cd99d-140">Set-Service cmdlet에는 서비스 시작 유형을 변경할 수 있도록 해주는 StartupType 매개 변수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd99d-140">The Set-Service cmdlet also has a StartupType parameter that lets you change the service startup type.</span></span>

<span data-ttu-id="cd99d-141">Windows Vista 이상에서 `Set-Service`를 사용하려면 “관리자 권한으로 실행” 옵션을 사용하여 Windows PowerShell을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="cd99d-141">To use `Set-Service` on Windows Vista and later versions of Windows, open Windows PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="cd99d-142">자세한 내용은 [Set-Service](/powershell/module/Microsoft.PowerShell.Management/set-service)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cd99d-142">For more information, see [Set-Service](/powershell/module/Microsoft.PowerShell.Management/set-service)</span></span>

## <a name="see-also"></a><span data-ttu-id="cd99d-143">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cd99d-143">See Also</span></span>

- [<span data-ttu-id="cd99d-144">Get-Service</span><span class="sxs-lookup"><span data-stu-id="cd99d-144">Get-Service</span></span>](/powershell/module/Microsoft.PowerShell.Management/get-service)
- [<span data-ttu-id="cd99d-145">Set-Service</span><span class="sxs-lookup"><span data-stu-id="cd99d-145">Set-Service</span></span>](/powershell/module/Microsoft.PowerShell.Management/set-service)
- [<span data-ttu-id="cd99d-146">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="cd99d-146">Restart-Service</span></span>](/powershell/module/Microsoft.PowerShell.Management/restart-service)
- [<span data-ttu-id="cd99d-147">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="cd99d-147">Suspend-Service</span></span>](/powershell/module/Microsoft.PowerShell.Management/suspend-service)
