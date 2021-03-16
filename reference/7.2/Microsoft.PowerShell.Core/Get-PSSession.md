---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 05/15/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-pssession?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSSession
ms.openlocfilehash: e06eaaa3b6042a2105462adfc2ba8f0a4867f045
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99600631"
---
# <span data-ttu-id="6403a-102">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="6403a-102">Get-PSSession</span></span>

## <span data-ttu-id="6403a-103">개요</span><span class="sxs-lookup"><span data-stu-id="6403a-103">SYNOPSIS</span></span>
<span data-ttu-id="6403a-104">로컬 및 원격 컴퓨터의 PowerShell 세션을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-104">Gets the PowerShell sessions on local and remote computers.</span></span>

## <span data-ttu-id="6403a-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="6403a-105">SYNTAX</span></span>

### <span data-ttu-id="6403a-106">이름 (기본값)</span><span class="sxs-lookup"><span data-stu-id="6403a-106">Name (Default)</span></span>

```
Get-PSSession [-Name <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="6403a-107">컴퓨터 이름</span><span class="sxs-lookup"><span data-stu-id="6403a-107">ComputerName</span></span>

```
Get-PSSession [-ComputerName] <String[]> [-ApplicationName <String>] [-ConfigurationName <String>]
 [-Name <String[]>] [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [-Port <Int32>] [-UseSSL] [-ThrottleLimit <Int32>]
 [-State <SessionFilterState>] [-SessionOption <PSSessionOption>] [<CommonParameters>]
```

### <span data-ttu-id="6403a-108">ComputerInstanceId</span><span class="sxs-lookup"><span data-stu-id="6403a-108">ComputerInstanceId</span></span>

```
Get-PSSession [-ComputerName] <String[]> [-ApplicationName <String>] [-ConfigurationName <String>]
 -InstanceId <Guid[]> [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [-Port <Int32>] [-UseSSL] [-ThrottleLimit <Int32>]
 [-State <SessionFilterState>] [-SessionOption <PSSessionOption>] [<CommonParameters>]
```

### <span data-ttu-id="6403a-109">ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="6403a-109">ConnectionUri</span></span>

```
Get-PSSession [-ConnectionUri] <Uri[]> [-ConfigurationName <String>] [-AllowRedirection] [-Name <String[]>]
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [-ThrottleLimit <Int32>] [-State <SessionFilterState>] [-SessionOption <PSSessionOption>] [<CommonParameters>]
```

### <span data-ttu-id="6403a-110">ConnectionUriInstanceId</span><span class="sxs-lookup"><span data-stu-id="6403a-110">ConnectionUriInstanceId</span></span>

```
Get-PSSession [-ConnectionUri] <Uri[]> [-ConfigurationName <String>] [-AllowRedirection] -InstanceId <Guid[]>
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [-ThrottleLimit <Int32>] [-State <SessionFilterState>] [-SessionOption <PSSessionOption>] [<CommonParameters>]
```

### <span data-ttu-id="6403a-111">VMNameInstanceId</span><span class="sxs-lookup"><span data-stu-id="6403a-111">VMNameInstanceId</span></span>

```
Get-PSSession [-ConfigurationName <String>] -InstanceId <Guid[]> [-State <SessionFilterState>]
 -VMName <String[]> [<CommonParameters>]
```

### <span data-ttu-id="6403a-112">ContainerId</span><span class="sxs-lookup"><span data-stu-id="6403a-112">ContainerId</span></span>

```
Get-PSSession [-ConfigurationName <String>] [-Name <String[]>] [-State <SessionFilterState>]
 -ContainerId <String[]> [<CommonParameters>]
```

### <span data-ttu-id="6403a-113">ContainerIdInstanceId</span><span class="sxs-lookup"><span data-stu-id="6403a-113">ContainerIdInstanceId</span></span>

```
Get-PSSession [-ConfigurationName <String>] -InstanceId <Guid[]> [-State <SessionFilterState>]
 -ContainerId <String[]> [<CommonParameters>]
```

### <span data-ttu-id="6403a-114">VMId</span><span class="sxs-lookup"><span data-stu-id="6403a-114">VMId</span></span>

```
Get-PSSession [-ConfigurationName <String>] [-Name <String[]>] [-State <SessionFilterState>] -VMId <Guid[]>
 [<CommonParameters>]
```

### <span data-ttu-id="6403a-115">VMIdInstanceId</span><span class="sxs-lookup"><span data-stu-id="6403a-115">VMIdInstanceId</span></span>

```
Get-PSSession [-ConfigurationName <String>] -InstanceId <Guid[]> [-State <SessionFilterState>] -VMId <Guid[]>
 [<CommonParameters>]
```

### <span data-ttu-id="6403a-116">VMName</span><span class="sxs-lookup"><span data-stu-id="6403a-116">VMName</span></span>

```
Get-PSSession [-ConfigurationName <String>] [-Name <String[]>] [-State <SessionFilterState>] -VMName <String[]>
 [<CommonParameters>]
```

### <span data-ttu-id="6403a-117">InstanceId</span><span class="sxs-lookup"><span data-stu-id="6403a-117">InstanceId</span></span>

```
Get-PSSession [-InstanceId <Guid[]>] [<CommonParameters>]
```

### <span data-ttu-id="6403a-118">Id</span><span class="sxs-lookup"><span data-stu-id="6403a-118">Id</span></span>

```
Get-PSSession [-Id] <Int32[]> [<CommonParameters>]
```

## <span data-ttu-id="6403a-119">설명</span><span class="sxs-lookup"><span data-stu-id="6403a-119">DESCRIPTION</span></span>

<span data-ttu-id="6403a-120">`Get-PSSession`Cmdlet은 로컬 및 원격 컴퓨터의 사용자 관리 PowerShell 세션 (**pssessions**)을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-120">The `Get-PSSession` cmdlet gets the user-managed PowerShell sessions (**PSSessions**) on local and remote computers.</span></span>

<span data-ttu-id="6403a-121">Windows PowerShell 3.0부터 세션은 각 연결의 원격 끝에 있는 컴퓨터에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-121">Starting in Windows PowerShell 3.0, sessions are stored on the computers at the remote end of each connection.</span></span> <span data-ttu-id="6403a-122">의 **ComputerName** 또는 **connectionuri** 매개 변수를 사용 하 여 `Get-PSSession` 현재 세션에서 생성 되지 않은 경우에도 로컬 컴퓨터 또는 원격 컴퓨터에 연결 되는 세션을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-122">You can use the **ComputerName** or **ConnectionUri** parameters of `Get-PSSession` to get the sessions that connect to the local computer or remote computers, even if they were not created in the current session.</span></span>

<span data-ttu-id="6403a-123">매개 변수가 없으면 `Get-PSSession` 현재 세션에서 만들어진 모든 세션을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-123">Without parameters, `Get-PSSession` gets all sessions that were created in the current session.</span></span>

<span data-ttu-id="6403a-124">**Name**, **ID**, **InstanceID**, **State**, **ApplicationName** 및 **ConfigurationName** 을 비롯 한 필터링 매개 변수를 사용 하 여에서 반환 하는 세션 중에서 선택할 수 `Get-PSSession` 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-124">Use the filtering parameters, including **Name**, **ID**, **InstanceID**, **State**, **ApplicationName**, and **ConfigurationName** to select from among the sessions that `Get-PSSession` returns.</span></span>

<span data-ttu-id="6403a-125">`Get-PSSession` **ComputerName** 또는 **connectionuri** 매개 변수를 사용할 때 명령이 실행 되는 임시 연결을 구성 하려면 나머지 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-125">Use the remaining parameters to configure the temporary connection in which the `Get-PSSession` command runs when you use the **ComputerName** or **ConnectionUri** parameters.</span></span>

<span data-ttu-id="6403a-126">참고: Windows PowerShell 2.0에서 매개 변수가 없는 경우 `Get-PSSession` 현재 세션에서 만들어진 모든 세션을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-126">NOTE: In Windows PowerShell 2.0, without parameters, `Get-PSSession` gets all sessions that were created in the current session.</span></span> <span data-ttu-id="6403a-127">**ComputerName** 매개 변수는 현재 세션에서 생성 된 세션을 가져오고 지정 된 컴퓨터에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-127">The **ComputerName** parameter gets sessions that were created in the current session and connect to the specified computer.</span></span>

<span data-ttu-id="6403a-128">PowerShell 세션에 대 한 자세한 내용은 [about_PSSessions](about/about_PSSessions.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6403a-128">For more information about PowerShell sessions, see [about_PSSessions](about/about_PSSessions.md).</span></span>

## <span data-ttu-id="6403a-129">예제</span><span class="sxs-lookup"><span data-stu-id="6403a-129">EXAMPLES</span></span>

### <span data-ttu-id="6403a-130">예 1: 현재 세션에서 만든 세션 가져오기</span><span class="sxs-lookup"><span data-stu-id="6403a-130">Example 1: Get sessions created in the current session</span></span>

```powershell
Get-PSSession
```

<span data-ttu-id="6403a-131">이 명령은 현재 세션에서 만들어진 모든 **pssession을 가져옵니다** .</span><span class="sxs-lookup"><span data-stu-id="6403a-131">This command gets all of the **PSSessions** that were created in the current session.</span></span> <span data-ttu-id="6403a-132">다른 세션이 나 다른 컴퓨터에서 만들어진 pssession은이 컴퓨터에 연결 하는 경우에 **도 가져오지 않습니다** .</span><span class="sxs-lookup"><span data-stu-id="6403a-132">It does not get **PSSessions** that were created in other sessions or on other computers, even if they connect to this computer.</span></span>

### <span data-ttu-id="6403a-133">예 2: 로컬 컴퓨터에 연결 된 세션 가져오기</span><span class="sxs-lookup"><span data-stu-id="6403a-133">Example 2: Get sessions connected to the local computer</span></span>

```powershell
Get-PSSession -ComputerName "localhost"
```

<span data-ttu-id="6403a-134">이 명령은 로컬 컴퓨터에 연결 된 **Pssessions** 를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-134">This command gets the **PSSessions** that are connected to the local computer.</span></span> <span data-ttu-id="6403a-135">로컬 컴퓨터를 나타내려면 컴퓨터 이름, localhost 또는 점 (.)을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-135">To indicate the local computer, type the computer name, localhost, or a dot (.)</span></span>

<span data-ttu-id="6403a-136">이 명령은 다른 세션이나 다른 컴퓨터에서 만들어진 세션을 비롯하여 로컬 컴퓨터의 모든 세션을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-136">The command returns all of the sessions on the local computer, even if they were created in different sessions or on different computers.</span></span>

### <span data-ttu-id="6403a-137">예 3: 컴퓨터에 연결 된 세션 가져오기</span><span class="sxs-lookup"><span data-stu-id="6403a-137">Example 3: Get sessions connected to a computer</span></span>

```powershell
Get-PSSession -ComputerName "Server02"
```

```Output
 Id Name            ComputerName    State         ConfigurationName     Availability
 -- ----            ------------    -----         -----------------     ------------
  2 Session3        Server02       Disconnected  ITTasks                       Busy
  1 ScheduledJobs   Server02       Opened        Microsoft.PowerShell     Available
  3 Test            Server02       Disconnected  Microsoft.PowerShell          Busy
```

<span data-ttu-id="6403a-138">이 명령은 Server02 컴퓨터에 연결 된 **Pssessions** 를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-138">This command gets the **PSSessions** that are connected to the Server02 computer.</span></span>

<span data-ttu-id="6403a-139">이 명령은 다른 세션이나 다른 컴퓨터에서 만들어진 세션을 비롯하여 Server02의 모든 세션을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-139">The command returns all of the sessions on Server02, even if they were created in different sessions or on different computers.</span></span>

<span data-ttu-id="6403a-140">출력은 두 세션에 Disconnected 상태와 Busy 가용성이 있음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-140">The output shows that two of the sessions have a Disconnected state and a Busy availability.</span></span> <span data-ttu-id="6403a-141">두 세션은 다른 세션에서 만들어졌으며 현재 사용 중입니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-141">They were created in different sessions and are currently in use.</span></span> <span data-ttu-id="6403a-142">현재 세션에서 열려 있고 사용할 수 있는 ScheduledJobs 세션이 생성 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-142">The ScheduledJobs session, which is Opened and Available, was created in the current session.</span></span>

### <span data-ttu-id="6403a-143">예제 4:이 명령의 결과 저장</span><span class="sxs-lookup"><span data-stu-id="6403a-143">Example 4: Save results of this command</span></span>

```powershell
New-PSSession -ComputerName Server01, Server02, Server03
$s1, $s2, $s3 = Get-PSSession
```

<span data-ttu-id="6403a-144">이 예에서는 명령의 결과를 여러 변수에 저장 하는 방법을 보여 줍니다 `Get-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="6403a-144">This example shows how to save the results of a `Get-PSSession` command in multiple variables.</span></span>

<span data-ttu-id="6403a-145">첫 번째 명령은 cmdlet을 사용 하 여 `New-PSSession` 세 개의 원격 컴퓨터에 pssession을 만듭니다. </span><span class="sxs-lookup"><span data-stu-id="6403a-145">The first command uses the `New-PSSession` cmdlet to create **PSSessions** on three remote computers.</span></span>

<span data-ttu-id="6403a-146">두 번째 명령은 cmdlet을 사용 하 여 `Get-PSSession` 세 개의 pssession을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-146">The second command uses a `Get-PSSession` cmdlet to get the three **PSSessions**.</span></span> <span data-ttu-id="6403a-147">그런 다음 **별도의 변수에** 각 pssession을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-147">It then saves each of the **PSSessions** in a separate variable.</span></span>

<span data-ttu-id="6403a-148">PowerShell은 개체 배열을 변수 배열에 할당할 때 첫 번째 변수에 첫 번째 개체를 할당 하 고 두 번째 개체를 두 번째 변수에 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-148">When PowerShell assigns an array of objects to an array of variables, it assigns the first object to the first variable, the second object to the second variable, and so on.</span></span> <span data-ttu-id="6403a-149">개체가 변수보다 많을 경우 배열의 마지막 변수에 남은 개체를 모두 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-149">If there are more objects than variables, it assigns all remaining objects to the last variable in the array.</span></span> <span data-ttu-id="6403a-150">변수가 개체보다 많을 경우 추가 변수는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-150">If there are more variables than objects, the extra variables are not used.</span></span>

### <span data-ttu-id="6403a-151">예 5: 인스턴스 ID를 사용 하 여 세션 삭제</span><span class="sxs-lookup"><span data-stu-id="6403a-151">Example 5: Delete a session by using an instance ID</span></span>

```powershell
Get-PSSession | Format-Table -Property ComputerName, InstanceID
$s = Get-PSSession -InstanceID a786be29-a6bb-40da-80fb-782c67f7db0f
Remove-PSSession -Session $s
```

<span data-ttu-id="6403a-152">이 예제에서는 인스턴스 ID를 사용 하 여 **pssession** 을 가져온 다음 **pssession** 을 삭제 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-152">This example shows how to get a **PSSession** by using its instance ID, and then to delete the **PSSession**.</span></span>

<span data-ttu-id="6403a-153">첫 번째 명령은 현재 세션에서 만들어진 모든 **pssession을 가져옵니다** .</span><span class="sxs-lookup"><span data-stu-id="6403a-153">The first command gets all of the **PSSessions** that were created in the current session.</span></span> <span data-ttu-id="6403a-154">이 명령은 각 **PSSession** 의 **ComputerName** 및 **InstanceID** 속성을 표시 하는 Format-Table cmdlet으로 **pssessions** 를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-154">It sends the **PSSessions** to the Format-Table cmdlet, which displays the **ComputerName** and **InstanceID** properties of each **PSSession**.</span></span>

<span data-ttu-id="6403a-155">두 번째 명령은 cmdlet을 사용 하 여 `Get-PSSession` 특정 **PSSession** 을 가져온 다음 변수에 저장 합니다 `$s` .</span><span class="sxs-lookup"><span data-stu-id="6403a-155">The second command uses the `Get-PSSession` cmdlet to get a particular **PSSession** and to save it in the `$s` variable.</span></span> <span data-ttu-id="6403a-156">이 명령은 **InstanceID** 매개 변수를 사용 하 여 **PSSession** 을 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-156">The command uses the **InstanceID** parameter to identify the **PSSession**.</span></span>

<span data-ttu-id="6403a-157">세 번째 명령은 Remove-PSSession cmdlet을 사용 하 여 변수의 **PSSession** 을 삭제 합니다 `$s` .</span><span class="sxs-lookup"><span data-stu-id="6403a-157">The third command uses the Remove-PSSession cmdlet to delete the **PSSession** in the `$s` variable.</span></span>

### <span data-ttu-id="6403a-158">예 6: 특정 이름을 가진 세션 가져오기</span><span class="sxs-lookup"><span data-stu-id="6403a-158">Example 6: Get a session that has a particular name</span></span>

<span data-ttu-id="6403a-159">이 예제의 명령은 특정 이름 형식으로 되어 있으며 특정 세션 구성을 사용하는 세션을 찾아 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-159">The commands in this example find a session that has a particular name format and uses a particular session configuration and then connect to the session.</span></span> <span data-ttu-id="6403a-160">이러한 명령을 사용하면 동료가 작업을 시작한 세션을 찾아 연결하여 작업을 마칠 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-160">You can use a command like this one to find a session in which a colleague started a task and connect to finish the task.</span></span>

```powershell
Get-PSSession -ComputerName Server02, Server12 -Name BackupJob* -ConfigurationName ITTasks -SessionOption @{OperationTimeout=240000}
```

```Output
 Id Name            ComputerName    State         ConfigurationName     Availability
 -- ----            ------------    -----         -----------------     ------------
  3 BackupJob04     Server02        Disconnected        ITTasks                  None
```

```powershell
$s = Get-PSSession -ComputerName Server02 -Name BackupJob04 -ConfigurationName ITTasks | Connect-PSSession
$s
```

```Output
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 5 BackupJob04     Server02        Opened        ITTasks                  Available
```

<span data-ttu-id="6403a-161">첫 번째 명령은 Server02 및 Server12 원격 컴퓨터에서 이름이 BackupJob로 시작 하 고 ITTasks 세션 구성을 사용 하는 세션을 가져옵니다. 이 명령은 **name** 매개 변수를 사용 하 여 이름 패턴을 지정 하 고 **ConfigurationName** 매개 변수를 사용 하 여 세션 구성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-161">The first command gets sessions on the Server02 and Server12 remote computers that have names that begin with BackupJob and use the ITTasks session configuration.The command uses the **Name** parameter to specify the name pattern and the **ConfigurationName** parameter to specify the session configuration.</span></span> <span data-ttu-id="6403a-162">**SessionOption** 매개 변수 값은 **OperationTimeout** 값을 240000밀리초(4분)로 설정하는 해시 테이블입니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-162">The value of the **SessionOption** parameter is a hash table that sets the value of the **OperationTimeout** to 240000 milliseconds (4 minutes).</span></span> <span data-ttu-id="6403a-163">이 설정은 명령을 완료 하는 데 더 많은 시간을 제공 합니다. **ConfigurationName** 및 **sessionoption** 매개 변수는 `Get-PSSession` 각 컴퓨터에서 cmdlet이 실행 되는 임시 세션을 구성 하는 데 사용 됩니다. 출력은 명령이 BackupJob04 세션을 반환 한다는 것을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-163">This setting gives the command more time to complete.The **ConfigurationName** and **SessionOption** parameters are used to configure the temporary sessions in which the `Get-PSSession` cmdlet runs on each computer.The output shows that the command returns the BackupJob04 session.</span></span> <span data-ttu-id="6403a-164">세션의 연결이 끊어져 **가용성이** None 이며 사용 중이 아님을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-164">The session is disconnected and the **Availability** is None, which indicates that it is not in use.</span></span>

<span data-ttu-id="6403a-165">두 번째 명령은 cmdlet을 사용 하 여 `Get-PSSession` BackupJob04 세션을 가져오고 Connect-PSSession cmdlet을 사용 하 여 세션에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-165">The second command uses the `Get-PSSession` cmdlet to get to the BackupJob04 session and the Connect-PSSession cmdlet to connect to the session.</span></span> <span data-ttu-id="6403a-166">이 명령은 세션을 $s 변수에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-166">The command saves the session in the $s variable.</span></span>

<span data-ttu-id="6403a-167">세 번째 명령은 $s 변수의 세션을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-167">The third command gets the session in the $s variable.</span></span> <span data-ttu-id="6403a-168">출력은 명령이 성공 했음을 보여 줍니다 `Connect-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="6403a-168">The output shows that the `Connect-PSSession` command was successful.</span></span> <span data-ttu-id="6403a-169">세션이 **Opened** 상태이며 사용 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-169">The session is in the **Opened** state and is available for use.</span></span>

### <span data-ttu-id="6403a-170">예 7: 해당 ID를 사용 하 여 세션 가져오기</span><span class="sxs-lookup"><span data-stu-id="6403a-170">Example 7: Get a session by using its ID</span></span>

```powershell
Get-PSSession -Id 2
```

<span data-ttu-id="6403a-171">이 명령은 ID가 2 인 **PSSession** 을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-171">This command gets the **PSSession** with ID 2.</span></span> <span data-ttu-id="6403a-172">**Id** 속성의 값은 현재 세션 에서만 고유 하기 때문에 **id** 매개 변수는 로컬 명령에 대해서만 유효 합니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-172">Because the value of the **ID** property is unique only in the current session, the **Id** parameter is valid only for local commands.</span></span>

## <span data-ttu-id="6403a-173">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6403a-173">PARAMETERS</span></span>

### <span data-ttu-id="6403a-174">-AllowRedirection</span><span class="sxs-lookup"><span data-stu-id="6403a-174">-AllowRedirection</span></span>

<span data-ttu-id="6403a-175">이 cmdlet이이 연결을 대체 URI (Uniform Resource Identifier)로 리디렉션할 수 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-175">Indicates that this cmdlet allows redirection of this connection to an alternate Uniform Resource Identifier (URI).</span></span> <span data-ttu-id="6403a-176">기본적으로 PowerShell은 연결을 리디렉션하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-176">By default, PowerShell does not redirect connections.</span></span>

<span data-ttu-id="6403a-177">이 매개 변수는 `Get-PSSession` **connectionuri** 매개 변수를 사용 하 여 명령을 실행 하기 위해 만들어지는 임시 연결을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-177">This parameter configures the temporary connection that is created to run a `Get-PSSession` command with the **ConnectionUri** parameter.</span></span>

<span data-ttu-id="6403a-178">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-178">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ConnectionUriInstanceId, ConnectionUri
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6403a-179">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="6403a-179">-ApplicationName</span></span>

<span data-ttu-id="6403a-180">애플리케이션의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-180">Specifies the name of an application.</span></span> <span data-ttu-id="6403a-181">이 cmdlet은 지정 된 응용 프로그램을 사용 하는 세션에만 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-181">This cmdlet connects only to sessions that use the specified application.</span></span>

<span data-ttu-id="6403a-182">연결 URI의 애플리케이션 이름 세그먼트를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-182">Enter the application name segment of the connection URI.</span></span> <span data-ttu-id="6403a-183">예를 들어, 다음 연결 URI에서 응용 프로그램 이름은 WSMan입니다 `http://localhost:5985/WSMAN` .</span><span class="sxs-lookup"><span data-stu-id="6403a-183">For example, in the following connection URI, the application name is WSMan: `http://localhost:5985/WSMAN`.</span></span> <span data-ttu-id="6403a-184">세션의 응용 프로그램 이름은 세션의 **Runspace.ConnectionInfo.AppName** 속성에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-184">The application name of a session is stored in the **Runspace.ConnectionInfo.AppName** property of the session.</span></span>

<span data-ttu-id="6403a-185">이 매개 변수 값은 세션을 선택 및 필터링하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-185">The value of this parameter is used to select and filter sessions.</span></span> <span data-ttu-id="6403a-186">세션에서 사용하는 애플리케이션을 변경하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-186">It does not change the application that the session uses.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerInstanceId, ComputerName
Aliases:

Required: False
Position: Named
Default value: All sessions
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6403a-187">-인증</span><span class="sxs-lookup"><span data-stu-id="6403a-187">-Authentication</span></span>

<span data-ttu-id="6403a-188">명령이 실행 되는 세션에 대 한 자격 증명을 인증 하는 데 사용 되는 메커니즘을 지정 합니다 `Get-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="6403a-188">Specifies the mechanism that is used to authenticate credentials for the session in which the `Get-PSSession` command runs.</span></span>

<span data-ttu-id="6403a-189">이 매개 변수는 `Get-PSSession` **ComputerName** 또는 **connectionuri** 매개 변수를 사용 하 여 명령을 실행 하기 위해 만들어지는 임시 연결을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-189">This parameter configures the temporary connection that is created to run a `Get-PSSession` command with the **ComputerName** or **ConnectionUri** parameter.</span></span>

<span data-ttu-id="6403a-190">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-190">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="6403a-191">기본값</span><span class="sxs-lookup"><span data-stu-id="6403a-191">Default</span></span>
- <span data-ttu-id="6403a-192">Basic</span><span class="sxs-lookup"><span data-stu-id="6403a-192">Basic</span></span>
- <span data-ttu-id="6403a-193">Credssp</span><span class="sxs-lookup"><span data-stu-id="6403a-193">Credssp</span></span>
- <span data-ttu-id="6403a-194">다이제스트</span><span class="sxs-lookup"><span data-stu-id="6403a-194">Digest</span></span>
- <span data-ttu-id="6403a-195">Kerberos</span><span class="sxs-lookup"><span data-stu-id="6403a-195">Kerberos</span></span>
- <span data-ttu-id="6403a-196">Negotiate</span><span class="sxs-lookup"><span data-stu-id="6403a-196">Negotiate</span></span>
- <span data-ttu-id="6403a-197">NegotiateWithImplicitCredential.</span><span class="sxs-lookup"><span data-stu-id="6403a-197">NegotiateWithImplicitCredential.</span></span>

<span data-ttu-id="6403a-198">기본값은 Default입니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-198">The default value is Default.</span></span>

<span data-ttu-id="6403a-199">이 매개 변수 값에 대 한 자세한 내용은 [Authenticationmechanism 열거](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6403a-199">For more information about the values of this parameter, see [AuthenticationMechanism Enumeration](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

<span data-ttu-id="6403a-200">주의: 사용자의 자격 증명이 인증을 위해 원격 컴퓨터에 전달 되는 CredSSP (자격 증명 보안 지원 공급자) 인증은 원격 네트워크 공유에 액세스 하는 것과 같이 둘 이상의 리소스에서 인증이 필요한 명령에 대해 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-200">CAUTION: Credential Security Support Provider (CredSSP) authentication, in which the user's credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="6403a-201">이렇게 하면 원격 작업의 보안 위험이 커집니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-201">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="6403a-202">원격 컴퓨터가 손상된 경우 이 컴퓨터로 전달된 자격 증명을 사용하여 네트워크 세션을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-202">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

<span data-ttu-id="6403a-203">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-203">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUriInstanceId, ConnectionUri
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6403a-204">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="6403a-204">-CertificateThumbprint</span></span>

<span data-ttu-id="6403a-205">명령이 실행 되는 세션을 만들 수 있는 권한이 있는 사용자 계정의 디지털 공개 키 인증서 (X509)를 지정 합니다 `Get-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="6403a-205">Specifies the digital public key certificate (X509) of a user account that has permission to create the session in which the `Get-PSSession` command runs.</span></span> <span data-ttu-id="6403a-206">인증서의 인증서 지문을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-206">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="6403a-207">이 매개 변수는 `Get-PSSession` **ComputerName** 또는 **connectionuri** 매개 변수를 사용 하 여 명령을 실행 하기 위해 만들어지는 임시 연결을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-207">This parameter configures the temporary connection that is created to run a `Get-PSSession` command with the **ComputerName** or **ConnectionUri** parameter.</span></span>

<span data-ttu-id="6403a-208">인증서는 클라이언트 인증서 기반 인증에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-208">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="6403a-209">인증서는 로컬 사용자 계정에만 매핑할 수 있으며 도메인 계정에는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-209">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="6403a-210">인증서 지문을 가져오려면 PowerShell Cert: 드라이브에서 Get-Item 또는 Get-ChildItem 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-210">To get a certificate thumbprint, use a Get-Item or Get-ChildItem command in the PowerShell Cert: drive.</span></span>

<span data-ttu-id="6403a-211">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-211">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUriInstanceId, ConnectionUri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6403a-212">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="6403a-212">-ComputerName</span></span>

<span data-ttu-id="6403a-213">컴퓨터 이름 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-213">Specifies an array of names of computers.</span></span> <span data-ttu-id="6403a-214">지정한 컴퓨터에 연결되는 세션을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-214">Gets the sessions that connect to the specified computers.</span></span>
<span data-ttu-id="6403a-215">와일드카드 문자는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-215">Wildcard characters are not permitted.</span></span> <span data-ttu-id="6403a-216">기본값은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-216">There is no default value.</span></span>

<span data-ttu-id="6403a-217">Windows PowerShell 3.0부터 **PSSession** 개체는 각 연결의 원격 끝에 있는 컴퓨터에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-217">Beginning in Windows PowerShell 3.0, **PSSession** objects are stored on the computers at the remote end of each connection.</span></span> <span data-ttu-id="6403a-218">지정 된 컴퓨터의 세션을 가져오기 위해 PowerShell은 각 컴퓨터에 대 한 임시 연결을 만들고 `Get-PSSession` 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-218">To get the sessions on the specified computers, PowerShell creates a temporary connection to each computer and runs a `Get-PSSession` command.</span></span>

<span data-ttu-id="6403a-219">하나 이상 컴퓨터의 NetBIOS 이름, IP 주소 또는 정규화된 도메인 이름을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="6403a-219">Type the NetBIOS name, an IP address, or a fully-qualified domain name of one or more computers.</span></span> <span data-ttu-id="6403a-220">로컬 컴퓨터를 지정 하려면 컴퓨터 이름, localhost 또는 점 (.)을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-220">To specify the local computer, type the computer name, localhost, or a dot (.).</span></span>

<span data-ttu-id="6403a-221">참고:이 매개 변수는 Windows PowerShell 3.0 이상 버전의 PowerShell을 실행 하는 컴퓨터 에서만 세션을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-221">Note: This parameter gets sessions only from computers that run Windows PowerShell 3.0 or later versions of PowerShell.</span></span> <span data-ttu-id="6403a-222">이전 버전은 세션을 저장하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-222">Earlier versions do not store sessions.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ComputerInstanceId, ComputerName
Aliases: Cn

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6403a-223">-ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="6403a-223">-ConfigurationName</span></span>

<span data-ttu-id="6403a-224">구성의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-224">Specifies the name of a configuration.</span></span> <span data-ttu-id="6403a-225">이 cmdlet은 지정 된 세션 구성을 사용 하는 세션만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-225">This cmdlet gets only to sessions that use the specified session configuration.</span></span>

<span data-ttu-id="6403a-226">세션 구성의 구성 이름 또는 정규화된 리소스 URI를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-226">Enter a configuration name or the fully qualified resource URI for a session configuration.</span></span> <span data-ttu-id="6403a-227">구성 이름만 지정 하는 경우에는 다음 스키마 URI가 앞에와 야 `http://schemas.microsoft.com/powershell` 합니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-227">If you specify only the configuration name, the following schema URI is prepended: `http://schemas.microsoft.com/powershell`.</span></span> <span data-ttu-id="6403a-228">세션의 구성 이름은 세션의 **ConfigurationName** 속성에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-228">The configuration name of a session is stored in the **ConfigurationName** property of the session.</span></span>

<span data-ttu-id="6403a-229">이 매개 변수 값은 세션을 선택 및 필터링하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-229">The value of this parameter is used to select and filter sessions.</span></span> <span data-ttu-id="6403a-230">세션에서 사용하는 세션 구성을 변경하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-230">It does not change the session configuration that the session uses.</span></span>

<span data-ttu-id="6403a-231">세션 구성에 대 한 자세한 내용은 [about_Session_Configurations](About/about_Session_Configurations.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6403a-231">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUriInstanceId, ConnectionUri, ContainerId, ContainerIdInstanceId, VMId, VMIdInstanceId, VMName, VMNameInstanceId
Aliases:

Required: False
Position: Named
Default value: All sessions
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6403a-232">-ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="6403a-232">-ConnectionUri</span></span>

<span data-ttu-id="6403a-233">명령이 실행 되는 임시 세션의 연결 끝점을 정의 하는 URI를 지정 합니다 `Get-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="6403a-233">Specifies a URI that defines the connection endpoint for the temporary session in which the `Get-PSSession` command runs.</span></span> <span data-ttu-id="6403a-234">URI는 정규화된 URI여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-234">The URI must be fully qualified.</span></span>

<span data-ttu-id="6403a-235">이 매개 변수는 `Get-PSSession` **connectionuri** 매개 변수를 사용 하 여 명령을 실행 하기 위해 만들어지는 임시 연결을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-235">This parameter configures the temporary connection that is created to run a `Get-PSSession` command with the **ConnectionUri** parameter.</span></span>

<span data-ttu-id="6403a-236">이 문자열의 형식은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-236">The format of this string is:</span></span>

`<Transport>://<ComputerName>:<Port\>/<ApplicationName>`

<span data-ttu-id="6403a-237">기본값은 `http://localhost:5985/WSMAN` 입니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-237">The default value is: `http://localhost:5985/WSMAN`.</span></span>

<span data-ttu-id="6403a-238">**Connectionuri** 를 지정 하지 않으면 **UseSSL**, **ComputerName**, **Port** 및 **ApplicationName** 매개 변수를 사용 하 여 **connectionuri** 값을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-238">If you do not specify a **ConnectionUri**, you can use the **UseSSL**, **ComputerName**, **Port**, and **ApplicationName** parameters to specify the **ConnectionURI** values.</span></span> <span data-ttu-id="6403a-239">URI의 전송 세그먼트에 유효한 값은 HTTP 및 HTTPS입니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-239">Valid values for the Transport segment of the URI are HTTP and HTTPS.</span></span> <span data-ttu-id="6403a-240">전송 세그먼트를 사용 하 여 연결 URI를 지정 하 고 포트를 지정 하지 않으면 세션은 표준 포트 80 (HTTP의 경우, HTTPS의 경우 443)를 사용 하 여 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-240">If you specify a connection URI with a Transport segment, but do not specify a port, the session is created with standards ports: 80 for HTTP and 443 for HTTPS.</span></span> <span data-ttu-id="6403a-241">PowerShell 원격을 위한 기본 포트를 사용 하려면 HTTP의 경우 포트 5985을, HTTPS의 경우 5986을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-241">To use the default ports for PowerShell remoting, specify port 5985 for HTTP or 5986 for HTTPS.</span></span>

<span data-ttu-id="6403a-242">대상 컴퓨터에서 연결을 다른 URI로 리디렉션하는 경우 명령에서 **allowredirection** 매개 변수를 사용 하지 않으면 PowerShell에서 리디렉션을 방지 합니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-242">If the destination computer redirects the connection to a different URI, PowerShell prevents the redirection unless you use the **AllowRedirection** parameter in the command.</span></span>

<span data-ttu-id="6403a-243">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-243">This parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="6403a-244">이 매개 변수는 windows powershell 3.0 이상 버전의 Windows PowerShell을 실행 하는 컴퓨터 에서만 세션을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-244">This parameter gets sessions only from computers that run Windows PowerShell 3.0 or later versions of Windows PowerShell.</span></span> <span data-ttu-id="6403a-245">이전 버전은 세션을 저장하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-245">Earlier versions do not store sessions.</span></span>

```yaml
Type: System.Uri[]
Parameter Sets: ConnectionUriInstanceId, ConnectionUri
Aliases: URI, CU

Required: True
Position: 0
Default value: Http://localhost:5985/WSMAN
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6403a-246">-ContainerId</span><span class="sxs-lookup"><span data-stu-id="6403a-246">-ContainerId</span></span>

<span data-ttu-id="6403a-247">컨테이너의 Id 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-247">Specifies an array of IDs of containers.</span></span> <span data-ttu-id="6403a-248">이 cmdlet은 지정 된 각 컨테이너와 대화형 세션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-248">This cmdlet starts an interactive session with each of the specified containers.</span></span> <span data-ttu-id="6403a-249">명령을 사용 `docker ps` 하 여 컨테이너 id 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-249">Use the `docker ps` command to get a list of container IDs.</span></span> <span data-ttu-id="6403a-250">자세한 내용은 [docker ps](https://docs.docker.com/engine/reference/commandline/ps/) 명령에 대 한 도움말을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6403a-250">For more information, see the help for the [docker ps](https://docs.docker.com/engine/reference/commandline/ps/) command.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ContainerId, ContainerIdInstanceId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6403a-251">-Credential</span><span class="sxs-lookup"><span data-stu-id="6403a-251">-Credential</span></span>

<span data-ttu-id="6403a-252">사용자 자격 증명을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-252">Specifies a user credential.</span></span> <span data-ttu-id="6403a-253">이 cmdlet은 지정 된 사용자의 권한으로 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-253">This cmdlet runs the command with the permissions of the specified user.</span></span> <span data-ttu-id="6403a-254">원격 컴퓨터에 연결할 수 있는 권한을 가진 사용자 계정을 지정 하 고 `Get-PSSession` 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-254">Specify a user account that has permission to connect to the remote computer and run a `Get-PSSession` command.</span></span> <span data-ttu-id="6403a-255">기본값은 현재 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-255">The default is the current user.</span></span>

<span data-ttu-id="6403a-256">**User01** 또는 **Domain01\User01** 과 같은 사용자 이름을 입력 하거나 cmdlet에 의해 생성 된 **PSCredential** 개체를 입력 합니다 `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="6403a-256">Type a user name, such as **User01** or **Domain01\User01**, or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="6403a-257">사용자 이름을 입력 하면 암호를 입력 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-257">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="6403a-258">자격 증명은 [PSCredential](/dotnet/api/system.management.automation.pscredential) 개체에 저장 되 고 암호는 [SecureString](/dotnet/api/system.security.securestring)으로 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-258">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="6403a-259">**Securestring** 데이터 보호에 대 한 자세한 [내용은 참조 하십시오](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="6403a-259">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

<span data-ttu-id="6403a-260">이 매개 변수 `Get-PSSession` 는 **ComputerName** 또는 **connectionuri** 매개 변수를 사용 하 여 명령을 실행 하기 위해 만들어지는 임시 연결을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-260">This parameter configures to the temporary connection that is created to run a `Get-PSSession` command with the **ComputerName** or **ConnectionUri** parameter.</span></span>

<span data-ttu-id="6403a-261">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-261">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUriInstanceId, ConnectionUri
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6403a-262">-Id</span><span class="sxs-lookup"><span data-stu-id="6403a-262">-Id</span></span>

<span data-ttu-id="6403a-263">세션 Id의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-263">Specifies an array of session IDs.</span></span> <span data-ttu-id="6403a-264">이 cmdlet은 지정 된 Id를 가진 세션만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-264">This cmdlet gets only the sessions with the specified IDs.</span></span> <span data-ttu-id="6403a-265">하나 이상의 Id를 쉼표로 구분 하 여 입력 하거나 범위 연산자 (...)를 사용 하 여 Id 범위를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-265">Type one or more IDs, separated by commas, or use the range operator (..) to specify a range of IDs.</span></span> <span data-ttu-id="6403a-266">**ComputerName** 매개 변수와 함께 ID 매개 변수를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-266">You cannot use the ID parameter together with the **ComputerName** parameter.</span></span>

<span data-ttu-id="6403a-267">ID는 현재 세션의 사용자 관리 세션을 고유 하 게 식별 하는 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-267">An ID is an integer that uniquely identifies the user-managed sessions in the current session.</span></span> <span data-ttu-id="6403a-268">**InstanceId** 보다 쉽게 기억할 수 있으며 입력 하는 것은 쉽지만 현재 세션 내 에서만 고유 합니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-268">It is easier to remember and type than the **InstanceId**, but it is unique only within the current session.</span></span> <span data-ttu-id="6403a-269">세션 ID는 세션의 ID 속성에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-269">The ID of a session is stored in the ID property of the session.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases:

Required: True
Position: 0
Default value: All sessions
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6403a-270">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="6403a-270">-InstanceId</span></span>

<span data-ttu-id="6403a-271">세션의 인스턴스 Id 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-271">Specifies an array of instance IDs of sessions.</span></span> <span data-ttu-id="6403a-272">이 cmdlet은 지정 된 인스턴스 Id를 가진 세션만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-272">This cmdlet gets only the sessions with the specified instance IDs.</span></span>

<span data-ttu-id="6403a-273">인스턴스 ID는 로컬 또는 원격 컴퓨터의 세션을 고유하게 식별하는 GUID입니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-273">The instance ID is a GUID that uniquely identifies a session on a local or remote computer.</span></span> <span data-ttu-id="6403a-274">**InstanceID** 는 PowerShell에서 여러 세션을 실행 하는 경우에도 고유 합니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-274">The **InstanceID** is unique, even when you have multiple sessions running in PowerShell.</span></span>

<span data-ttu-id="6403a-275">세션의 인스턴스 ID는 세션의 **InstanceID** 속성에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-275">The instance ID of a session is stored in the **InstanceID** property of the session.</span></span>

```yaml
Type: System.Guid[]
Parameter Sets: ComputerInstanceId, ConnectionUriInstanceId, ContainerIdInstanceId, VMIdInstanceId, VMNameInstanceId, InstanceId
Aliases:

Required: True (ComputerInstanceId, ConnectionUriInstanceId, ContainerIdInstanceId, VMIdInstanceId, VMNameInstanceId), False (InstanceId)
Position: Named
Default value: All sessions
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6403a-276">-Name</span><span class="sxs-lookup"><span data-stu-id="6403a-276">-Name</span></span>

<span data-ttu-id="6403a-277">세션 이름 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-277">Specifies an array of session names.</span></span> <span data-ttu-id="6403a-278">이 cmdlet은 지정한 이름을 가진 세션만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-278">This cmdlet gets only the sessions that have the specified friendly names.</span></span> <span data-ttu-id="6403a-279">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-279">Wildcard characters are permitted.</span></span>

<span data-ttu-id="6403a-280">세션 이름은 세션의 **Name** 속성에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-280">The friendly name of a session is stored in the **Name** property of the session.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Name, ComputerName, ConnectionUri, ContainerId, VMId, VMName
Aliases:

Required: False
Position: Named
Default value: All sessions
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="6403a-281">-Port</span><span class="sxs-lookup"><span data-stu-id="6403a-281">-Port</span></span>

<span data-ttu-id="6403a-282">명령이 실행 되는 임시 연결에 사용 되는 지정 된 네트워크 포트를 지정 합니다 `Get-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="6403a-282">Specifies the specified network port that is used for the temporary connection in which the `Get-PSSession` command runs.</span></span> <span data-ttu-id="6403a-283">원격 컴퓨터에 연결하려면 원격 컴퓨터가 연결에서 사용하는 포트에서 수신 대기하고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-283">To connect to a remote computer, the remote computer must be listening on the port that the connection uses.</span></span> <span data-ttu-id="6403a-284">기본 포트는 HTTP의 WinRM 포트인 5985이 고, HTTPS의 경우 WinRM 포트인 5986입니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-284">The default ports are 5985, which is the WinRM port for HTTP, and 5986, which is the WinRM port for HTTPS.</span></span>

<span data-ttu-id="6403a-285">대체 포트를 사용하려면 먼저 원격 컴퓨터에 해당 포트에서 수신 대기할 WinRM 수신기를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-285">Before using an alternate port, you must configure the WinRM listener on the remote computer to listen at that port.</span></span> <span data-ttu-id="6403a-286">수신기를 구성 하려면 PowerShell 프롬프트에 다음 두 명령을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-286">To configure the listener, type the following two commands at the PowerShell prompt:</span></span>

`Remove-Item -Path WSMan:\Localhost\listener\listener* -Recurse`

`New-Item -Path WSMan:\Localhost\listener -Transport http -Address * -Port \<port-number\>`

<span data-ttu-id="6403a-287">이 매개 변수 `Get-PSSession` 는 **ComputerName** 또는 **connectionuri** 매개 변수를 사용 하 여 명령을 실행 하기 위해 만들어지는 임시 연결을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-287">This parameter configures to the temporary connection that is created to run a `Get-PSSession` command with the **ComputerName** or **ConnectionUri** parameter.</span></span>

<span data-ttu-id="6403a-288">필요한 경우가 아니면 **Port** 매개 변수를 사용하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="6403a-288">Do not use the **Port** parameter unless you must.</span></span> <span data-ttu-id="6403a-289">명령에 설정 된 **포트** 는 명령이 실행 되는 모든 컴퓨터 또는 세션에 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-289">The **Port** set in the command applies to all computers or sessions on which the command runs.</span></span> <span data-ttu-id="6403a-290">대체 포트 설정을 사용하면 일부 컴퓨터에서 명령이 실행되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-290">An alternate port setting might prevent the command from running on all computers.</span></span>

<span data-ttu-id="6403a-291">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-291">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ComputerInstanceId, ComputerName
Aliases:

Required: False
Position: Named
Default value: 5985, 5986
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6403a-292">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="6403a-292">-SessionOption</span></span>

<span data-ttu-id="6403a-293">세션에 대 한 고급 옵션을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-293">Specifies advanced options for the session.</span></span> <span data-ttu-id="6403a-294">New-PSSessionOption cmdlet을 사용 하 여 만든 것과 같은 **sessionoption** 개체를 입력 하거나 키가 세션 옵션 이름이 고 값이 session 옵션 값인 해시 테이블을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-294">Enter a **SessionOption** object, such as one that you create by using the New-PSSessionOption cmdlet, or a hash table in which the keys are session option names and the values are session option values.</span></span>

<span data-ttu-id="6403a-295">옵션의 기본값은 $PSSessionOption 기본 설정 변수 값(설정되어 있는 경우)에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-295">The default values for the options are determined by the value of the $PSSessionOption preference variable, if it is set.</span></span> <span data-ttu-id="6403a-296">그러지 않으면 기본값은 세션 구성에 설정된 옵션에 따라 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-296">Otherwise, the default values are established by options set in the session configuration.</span></span>

<span data-ttu-id="6403a-297">세션 옵션 값은 $PSSessionOption 기본 설정 변수 및 세션 구성에 설정된 세션의 기본값보다 우선합니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-297">The session option values take precedence over default values for sessions set in the $PSSessionOption preference variable and in the session configuration.</span></span> <span data-ttu-id="6403a-298">그러나 이러한 값은 세션 구성에 설정된 최대값, 할당량 또는 제한보다 우선하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-298">However, they do not take precedence over maximum values, quotas or limits set in the session configuration.</span></span>

<span data-ttu-id="6403a-299">기본값을 포함 하 여 세션 옵션에 대 한 자세한 내용은을 참조 하십시오 `New-PSSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="6403a-299">For a description of the session options, including the default values, see `New-PSSessionOption`.</span></span>
<span data-ttu-id="6403a-300">기본 설정 변수에 대 한 자세한 내용은 `$PSSessionOption` [about_Preference_Variables](About/about_Preference_Variables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6403a-300">For information about the `$PSSessionOption` preference variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span> <span data-ttu-id="6403a-301">세션 구성에 대 한 자세한 내용은 [about_Session_Configurations](About/about_Session_Configurations.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6403a-301">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

```yaml
Type: System.Management.Automation.Remoting.PSSessionOption
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUriInstanceId, ConnectionUri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6403a-302">-상태</span><span class="sxs-lookup"><span data-stu-id="6403a-302">-State</span></span>

<span data-ttu-id="6403a-303">세션 상태를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-303">Specifies a session state.</span></span> <span data-ttu-id="6403a-304">이 cmdlet은 지정 된 상태의 세션만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-304">This cmdlet gets only sessions in the specified state.</span></span> <span data-ttu-id="6403a-305">이 매개 변수에 허용 되는 값은 모두, 열린, 연결 끊김, 닫힘 및 손상입니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-305">The acceptable values for this parameter are: All, Opened, Disconnected, Closed, and Broken.</span></span> <span data-ttu-id="6403a-306">기본값은 All입니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-306">The default value is All.</span></span>

<span data-ttu-id="6403a-307">세션 상태 값은 현재 세션을 기준으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-307">The session state value is relative to the current sessions.</span></span> <span data-ttu-id="6403a-308">현재 세션에서 만들어지지 않았으며 현재 세션에 연결되지 않은 세션은 다른 세션에 연결된 경우에도 Disconnected 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-308">Sessions that were not created in the current sessions and are not connected to the current session have a state of Disconnected even when they are connected to a different session.</span></span>

<span data-ttu-id="6403a-309">세션 상태는 세션의 **State** 속성에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-309">The state of a session is stored in the **State** property of the session.</span></span>

<span data-ttu-id="6403a-310">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-310">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.SessionFilterState
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUriInstanceId, ConnectionUri, ContainerId, ContainerIdInstanceId, VMId, VMIdInstanceId, VMName, VMNameInstanceId
Aliases:
Accepted values: All, Opened, Disconnected, Closed, Broken

Required: False
Position: Named
Default value: All
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6403a-311">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="6403a-311">-ThrottleLimit</span></span>

<span data-ttu-id="6403a-312">명령을 실행 하기 위해 설정할 수 있는 최대 동시 연결 수를 지정 합니다 `Get-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="6403a-312">Specifies the maximum number of concurrent connections that can be established to run the `Get-PSSession` command.</span></span> <span data-ttu-id="6403a-313">이 매개 변수를 생략하거나 값 0을 입력하면 기본값 32가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-313">If you omit this parameter or enter a value of 0 (zero), the default value, 32, is used.</span></span> <span data-ttu-id="6403a-314">제한 한도는 현재 명령에만 적용되며 세션이나 컴퓨터에는 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-314">The throttle limit applies only to the current command, not to the session or to the computer.</span></span>

<span data-ttu-id="6403a-315">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-315">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUriInstanceId, ConnectionUri
Aliases:

Required: False
Position: Named
Default value: 32
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6403a-316">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="6403a-316">-UseSSL</span></span>

<span data-ttu-id="6403a-317">이 cmdlet이 SSL(Secure Sockets Layer) (SSL) 프로토콜을 사용 하 여 명령이 실행 되는 연결을 설정 함을 나타냅니다 `Get-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="6403a-317">Indicates that this cmdlet uses the Secure Sockets Layer (SSL) protocol to establish the connection in which the `Get-PSSession` command runs.</span></span> <span data-ttu-id="6403a-318">기본적으로 SSL은 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-318">By default, SSL is not used.</span></span> <span data-ttu-id="6403a-319">이 매개 변수를 사용하지만 명령에 사용되는 포트에서 SSL을 사용할 수 없는 경우 명령이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-319">If you use this parameter, but SSL is not available on the port used for the command, the command fails.</span></span>

<span data-ttu-id="6403a-320">이 매개 변수는 `Get-PSSession` **ComputerName** 매개 변수를 사용 하 여 명령을 실행 하기 위해 만들어지는 임시 연결을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-320">This parameter configures the temporary connection that is created to run a `Get-PSSession` command with the **ComputerName** parameter.</span></span>

<span data-ttu-id="6403a-321">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-321">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerInstanceId, ComputerName
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6403a-322">-VMId</span><span class="sxs-lookup"><span data-stu-id="6403a-322">-VMId</span></span>

<span data-ttu-id="6403a-323">가상 컴퓨터의 ID 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-323">Specifies an array of ID of virtual machines.</span></span> <span data-ttu-id="6403a-324">이 cmdlet은 지정 된 각 가상 컴퓨터와 대화형 세션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-324">This cmdlet starts an interactive session with each of the specified virtual machines.</span></span> <span data-ttu-id="6403a-325">사용할 수 있는 가상 컴퓨터를 보려면 다음 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-325">To see the virtual machines that are available to you, use the following command:</span></span>

`Get-VM | Select-Object -Property Name, ID`

```yaml
Type: System.Guid[]
Parameter Sets: VMId, VMIdInstanceId
Aliases: VMGuid

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6403a-326">-VMName</span><span class="sxs-lookup"><span data-stu-id="6403a-326">-VMName</span></span>

<span data-ttu-id="6403a-327">가상 컴퓨터의 이름 배열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-327">Specifies an array of names of virtual machines.</span></span> <span data-ttu-id="6403a-328">이 cmdlet은 지정 된 각 가상 컴퓨터와 대화형 세션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-328">This cmdlet starts an interactive session with each of the specified virtual machines.</span></span> <span data-ttu-id="6403a-329">사용할 수 있는 가상 컴퓨터를 확인 하려면 cmdlet을 사용 합니다 `Get-VM` .</span><span class="sxs-lookup"><span data-stu-id="6403a-329">To see the virtual machines that are available to you, use the `Get-VM` cmdlet.</span></span>

```yaml
Type: System.String[]
Parameter Sets: VMName, VMNameInstanceId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6403a-330">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6403a-330">CommonParameters</span></span>

<span data-ttu-id="6403a-331">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="6403a-331">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6403a-332">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6403a-332">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6403a-333">입력</span><span class="sxs-lookup"><span data-stu-id="6403a-333">INPUTS</span></span>

### <span data-ttu-id="6403a-334">없음</span><span class="sxs-lookup"><span data-stu-id="6403a-334">None</span></span>

<span data-ttu-id="6403a-335">이 cmdlet에 입력을 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-335">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="6403a-336">출력</span><span class="sxs-lookup"><span data-stu-id="6403a-336">OUTPUTS</span></span>

### <span data-ttu-id="6403a-337">Runspace입니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-337">System.Management.Automation.Runspaces.PSSession</span></span>

## <span data-ttu-id="6403a-338">참고</span><span class="sxs-lookup"><span data-stu-id="6403a-338">NOTES</span></span>

- <span data-ttu-id="6403a-339">이 cmdlet은 새 PSSession, 및 Invoke-Command cmdlet을 사용 하 여 만든 것과 같은 사용자 관리 세션 **PSSession** 개체를 가져옵니다 `Enter-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="6403a-339">This cmdlet gets user-managed sessions **PSSession** objects" such as those that are created by using the New-PSSession, `Enter-PSSession`, and Invoke-Command cmdlets.</span></span> <span data-ttu-id="6403a-340">PowerShell을 시작할 때 만들어진 시스템 관리 세션은 가져오지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-340">It does not get the system-managed session that is created when you start PowerShell.</span></span>
- <span data-ttu-id="6403a-341">Windows PowerShell 3.0부터 **PSSession** 개체는 연결의 서버 쪽 또는 수신 끝에 있는 컴퓨터에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-341">Starting in Windows PowerShell 3.0, **PSSession** objects are stored on the computer that is at the server-side or receiving end of a connection.</span></span> <span data-ttu-id="6403a-342">PowerShell은 로컬 컴퓨터 또는 원격 컴퓨터에 저장 된 세션을 가져오기 위해 지정 된 컴퓨터에 대 한 임시 세션을 설정 하 고 세션에서 쿼리 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-342">To get the sessions that are stored on the local computer or a remote computer, PowerShell establishes a temporary session to the specified computer and runs query commands in the session.</span></span>
- <span data-ttu-id="6403a-343">원격 컴퓨터에 연결되는 세션을 가져오려면 **ComputerName** 또는 **ConnectionUri** 매개 변수를 사용하여 원격 컴퓨터를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-343">To get sessions that connect to a remote computer, use the **ComputerName** or **ConnectionUri** parameters to specify the remote computer.</span></span> <span data-ttu-id="6403a-344">에서 가져오는 세션을 필터링 하려면 `Get-PSSession` **Name**, **ID**, **InstanceID** 및 **State** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-344">To filter the sessions that `Get-PSSession` gets, use the **Name**, **ID**, **InstanceID**, and **State** parameters.</span></span> <span data-ttu-id="6403a-345">나머지 매개 변수를 사용 하 여에서 사용 하는 임시 세션을 구성 합니다 `Get-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="6403a-345">Use the remaining parameters to configure the temporary session that `Get-PSSession` uses.</span></span>
- <span data-ttu-id="6403a-346">**ComputerName** 또는 **connectionuri** 매개 변수를 사용 하는 경우 `Get-PSSession` Windows PowerShell 3.0 이상 버전의 powershell을 실행 하는 컴퓨터의 세션만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-346">When you use the **ComputerName** or **ConnectionUri** parameters, `Get-PSSession` gets only sessions from computers running Windows PowerShell 3.0 and later versions of PowerShell.</span></span>
- <span data-ttu-id="6403a-347">**PSSession** 의 **State** 속성 값은 현재 세션을 기준으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-347">The value of the **State** property of a **PSSession** is relative to the current session.</span></span>
  <span data-ttu-id="6403a-348">따라서 **연결 끊김** 값은 **PSSession** 이 현재 세션에 연결 되지 않았음을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-348">Therefore, a value of **Disconnected** means that the **PSSession** is not connected to the current session.</span></span> <span data-ttu-id="6403a-349">그러나 모든 세션에서 **PSSession** 의 연결이 끊어졌음을 의미 하는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-349">However, it does not mean that the **PSSession** is disconnected from all sessions.</span></span> <span data-ttu-id="6403a-350">다른 세션에 연결되어 있을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-350">It might be connected to a different session.</span></span> <span data-ttu-id="6403a-351">현재 세션에서 **PSSession** 에 연결 하거나 다시 연결할 수 있는지 확인 하려면 **Availability** 속성을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-351">To determine whether you can connect or reconnect to the **PSSession** from the current session, use the **Availability** property.</span></span>

<span data-ttu-id="6403a-352">**Availability** 값이 **None** 이면 세션에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-352">An **Availability** value of **None** indicates that you can connect to the session.</span></span> <span data-ttu-id="6403a-353">**사용 중** 값은 다른 세션에 연결 되어 있으므로 **PSSession** 에 연결할 수 없음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="6403a-353">A value of **Busy** indicates that you cannot connect to the **PSSession** because it is connected to another session.</span></span>

<span data-ttu-id="6403a-354">세션의 **State** 속성 값에 대 한 자세한 내용은 [RunspaceState 열거형](/dotnet/api/system.management.automation.runspaces.runspacestate)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6403a-354">For more information about the values of the **State** property of sessions, see [RunspaceState Enumeration](/dotnet/api/system.management.automation.runspaces.runspacestate).</span></span>

<span data-ttu-id="6403a-355">세션의 **Availability** 속성 값에 대 한 자세한 내용은 [RunspaceAvailability 열거형](/dotnet/api/system.management.automation.runspaces.runspaceavailability)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6403a-355">For more information about the values of the **Availability** property of sessions, see [RunspaceAvailability Enumeration](/dotnet/api/system.management.automation.runspaces.runspaceavailability).</span></span>

## <span data-ttu-id="6403a-356">관련 링크</span><span class="sxs-lookup"><span data-stu-id="6403a-356">RELATED LINKS</span></span>

[<span data-ttu-id="6403a-357">Connect-PSSession</span><span class="sxs-lookup"><span data-stu-id="6403a-357">Connect-PSSession</span></span>](Connect-PSSession.md)

[<span data-ttu-id="6403a-358">Disconnect-PSSession</span><span class="sxs-lookup"><span data-stu-id="6403a-358">Disconnect-PSSession</span></span>](Disconnect-PSSession.md)

[<span data-ttu-id="6403a-359">Receive-PSSession</span><span class="sxs-lookup"><span data-stu-id="6403a-359">Receive-PSSession</span></span>](Receive-PSSession.md)

[<span data-ttu-id="6403a-360">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="6403a-360">Enter-PSSession</span></span>](Enter-PSSession.md)

[<span data-ttu-id="6403a-361">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="6403a-361">Exit-PSSession</span></span>](Exit-PSSession.md)

[<span data-ttu-id="6403a-362">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="6403a-362">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="6403a-363">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="6403a-363">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="6403a-364">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="6403a-364">Remove-PSSession</span></span>](Remove-PSSession.md)

[<span data-ttu-id="6403a-365">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="6403a-365">about_PSSessions</span></span>](About/about_PSSessions.md)

[<span data-ttu-id="6403a-366">about_Remote</span><span class="sxs-lookup"><span data-stu-id="6403a-366">about_Remote</span></span>](About/about_Remote.md)
