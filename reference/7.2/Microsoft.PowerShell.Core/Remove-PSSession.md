---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/remove-pssession?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-PSSession
ms.openlocfilehash: cd0e2b62464a4c34278d42b833a669c6c28e377f
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603300"
---
# <span data-ttu-id="e0de4-102">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="e0de4-102">Remove-PSSession</span></span>

## <span data-ttu-id="e0de4-103">개요</span><span class="sxs-lookup"><span data-stu-id="e0de4-103">SYNOPSIS</span></span>
<span data-ttu-id="e0de4-104">하나 이상의 PowerShell 세션 (PSSessions)을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="e0de4-104">Closes one or more PowerShell sessions (PSSessions).</span></span>

## <span data-ttu-id="e0de4-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e0de4-105">SYNTAX</span></span>

### <span data-ttu-id="e0de4-106">Id (기본값)</span><span class="sxs-lookup"><span data-stu-id="e0de4-106">Id (Default)</span></span>

```
Remove-PSSession [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="e0de4-107">세션</span><span class="sxs-lookup"><span data-stu-id="e0de4-107">Session</span></span>

```
Remove-PSSession [-Session] <PSSession[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="e0de4-108">ContainerId</span><span class="sxs-lookup"><span data-stu-id="e0de4-108">ContainerId</span></span>

```
Remove-PSSession -ContainerId <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="e0de4-109">VMId</span><span class="sxs-lookup"><span data-stu-id="e0de4-109">VMId</span></span>

```
Remove-PSSession -VMId <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="e0de4-110">VMName</span><span class="sxs-lookup"><span data-stu-id="e0de4-110">VMName</span></span>

```
Remove-PSSession -VMName <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="e0de4-111">InstanceId</span><span class="sxs-lookup"><span data-stu-id="e0de4-111">InstanceId</span></span>

```
Remove-PSSession -InstanceId <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="e0de4-112">Name</span><span class="sxs-lookup"><span data-stu-id="e0de4-112">Name</span></span>

```
Remove-PSSession -Name <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="e0de4-113">컴퓨터 이름</span><span class="sxs-lookup"><span data-stu-id="e0de4-113">ComputerName</span></span>

```
Remove-PSSession [-ComputerName] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="e0de4-114">설명</span><span class="sxs-lookup"><span data-stu-id="e0de4-114">DESCRIPTION</span></span>

<span data-ttu-id="e0de4-115">**Remove PSSession** cmdlet은 현재 세션에서 PowerShell 세션 (**pssessions**)을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="e0de4-115">The **Remove-PSSession** cmdlet closes PowerShell sessions (**PSSessions**) in the current session.</span></span>
<span data-ttu-id="e0de4-116">**Pssession은 pssession** 에서 실행 되는 모든 명령을 **중지 하 고** pssession을 종료 한 다음 **pssession** 이 사용 하 던 리소스를 해제 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0de4-116">It stops any commands that are running in the **PSSessions**, ends the **PSSession**, and releases the resources that the **PSSession** was using.</span></span>
<span data-ttu-id="e0de4-117">**PSSession** 이 원격 컴퓨터에 연결 되어 있는 경우이 cmdlet은 로컬 컴퓨터와 원격 컴퓨터 간의 연결도 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="e0de4-117">If the **PSSession** is connected to a remote computer, this cmdlet also closes the connection between the local and remote computers.</span></span>

<span data-ttu-id="e0de4-118">**PSSession** 을 제거 하려면 세션의 *Name*, *ComputerName*, *ID* 또는 *InstanceID* 를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0de4-118">To remove a **PSSession**, enter the *Name*, *ComputerName*, *ID*, or *InstanceID* of the session.</span></span>

<span data-ttu-id="e0de4-119">*Pssession* 을 변수에 저장 한 경우 세션 개체는 변수에 남아 있지만 *pssession* 의 상태는 닫힙니다.</span><span class="sxs-lookup"><span data-stu-id="e0de4-119">If you have saved the *PSSession* in a variable, the session object remains in the variable, but the state of the *PSSession* is Closed.</span></span>

## <span data-ttu-id="e0de4-120">예제</span><span class="sxs-lookup"><span data-stu-id="e0de4-120">EXAMPLES</span></span>

### <span data-ttu-id="e0de4-121">예제 1: Id를 사용 하 여 세션 제거</span><span class="sxs-lookup"><span data-stu-id="e0de4-121">Example 1: Remove sessions by using IDs</span></span>

```powershell
Remove-PSSession -Id 1, 2
```

<span data-ttu-id="e0de4-122">이 명령은 Id가 1과 **2 인 pssession을 제거 합니다.**</span><span class="sxs-lookup"><span data-stu-id="e0de4-122">This command removes the **PSSessions** that have IDs 1 and 2.</span></span>

### <span data-ttu-id="e0de4-123">예 2: 현재 세션의 모든 세션 제거</span><span class="sxs-lookup"><span data-stu-id="e0de4-123">Example 2: Remove all the sessions in the current session</span></span>

```powershell
Get-PSSession | Remove-PSSession
Remove-PSSession -Session (Get-PSSession)
$s = Get-PSSession
Remove-PSSession -Session $s
```

<span data-ttu-id="e0de4-124">이러한 명령은 현재 **세션의 모든** pssession을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0de4-124">These commands remove all of the **PSSessions** in the current session.</span></span>
<span data-ttu-id="e0de4-125">이 세 명령 형식이 다르게 보이지만 효과는 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="e0de4-125">Although the three command formats look different, they have the same effect.</span></span>

### <span data-ttu-id="e0de4-126">예제 3: 이름을 사용 하 여 세션 닫기</span><span class="sxs-lookup"><span data-stu-id="e0de4-126">Example 3: Close sessions by using names</span></span>

```powershell
$r = Get-PSSession -ComputerName Serv*
$r | Remove-PSSession
```

<span data-ttu-id="e0de4-127">이러한 명령은 이름이 Serv로 시작 하는 컴퓨터에 연결 된 **Pssessions** 를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="e0de4-127">These commands close the **PSSessions** that are connected to computers that have names that begin with Serv.</span></span>

### <span data-ttu-id="e0de4-128">예제 4: 포트에 연결 된 세션 닫기</span><span class="sxs-lookup"><span data-stu-id="e0de4-128">Example 4: Close sessions connected to a port</span></span>

```powershell
Get-PSSession | where {$_.port -eq 90} | Remove-PSSession
```

<span data-ttu-id="e0de4-129">이 명령은 포트 90에 연결 된 **Pssessions** 를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="e0de4-129">This command closes the **PSSessions** that are connected to port 90.</span></span>
<span data-ttu-id="e0de4-130">이 명령 형식을 사용 하 여 *ComputerName*, *Name*, *InstanceID* 및 *ID* 이외의 속성으로 **pssessions** 를 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0de4-130">You can use this command format to identify **PSSessions** by properties other than *ComputerName*, *Name*, *InstanceID*, and *ID*.</span></span>

### <span data-ttu-id="e0de4-131">예 5: 인스턴스 ID에 따라 세션 닫기</span><span class="sxs-lookup"><span data-stu-id="e0de4-131">Example 5: Close a session based on instance ID</span></span>

```powershell
Get-PSSession | Format-Table ComputerName, InstanceID  -AutoSize
```

```Output
ComputerName InstanceId
------------ ----------------
Server01     875d231b-2788-4f36-9f67-2e50d63bb82a
localhost    c065ffa0-02c4-406e-84a3-dacb0d677868
Server02     4699cdbc-61d5-4e0d-b916-84f82ebede1f
Server03     4e5a3245-4c63-43e4-88d0-a7798bfc2414
TX-TEST-01   fc4e9dfa-f246-452d-9fa3-1adbdd64ae85 PS C:\> Remove-PSSession -InstanceID fc4e9dfa-f246-452d-9fa3-1adbdd64ae85
```

<span data-ttu-id="e0de4-132">이러한 명령은 인스턴스 ID 또는 **RemoteRunspaceID** 을 기반으로 **PSSession** 을 닫는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e0de4-132">These commands show how to close a **PSSession** based on its instance ID, or **RemoteRunspaceID**.</span></span>

<span data-ttu-id="e0de4-133">첫 번째 명령은 **Get PSSession** cmdlet을 사용 하 여 현재 세션 **의 PSSession을 가져옵니다** .</span><span class="sxs-lookup"><span data-stu-id="e0de4-133">The first command uses the **Get-PSSession** cmdlet to get the **PSSessions** in the current session.</span></span>
<span data-ttu-id="e0de4-134">파이프라인 연산자 (|)를 사용 하 여 **pssession을 Format-Table cmdlet으로 보냅니다** . 그러면이 Cmdlet에서 **ComputerName** 및 **InstanceID** 속성을 테이블 형식으로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0de4-134">It uses a pipeline operator (|) to send the **PSSessions** to the Format-Table cmdlet, which formats their **ComputerName** and **InstanceID** properties in a table.</span></span>
<span data-ttu-id="e0de4-135">*AutoSize* 매개 변수는 표시할 열을 압축 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0de4-135">The *AutoSize* parameter compresses the columns for display.</span></span>

<span data-ttu-id="e0de4-136">결과 디스플레이에서 닫을 **PSSession** 을 식별 하 고 해당 **pssession** 의 *InstanceID* 를 복사 하 여 두 번째 명령에 붙여 넣을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0de4-136">From the resulting display, you can identify the **PSSession** to be closed, and copy and paste the *InstanceID* of that **PSSession** into the second command.</span></span>

<span data-ttu-id="e0de4-137">두 번째 명령은 **Remove pssession** cmdlet을 사용 하 여 지정 된 인스턴스 ID의 *pssession* 을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0de4-137">The second command uses the **Remove-PSSession** cmdlet to remove the *PSSession* with the specified instance ID.</span></span>

### <span data-ttu-id="e0de4-138">예제 6: 현재 세션의 모든 세션을 삭제 하는 함수 만들기</span><span class="sxs-lookup"><span data-stu-id="e0de4-138">Example 6: Create a function that deletes all sessions in the current session</span></span>

```powershell
Function EndPSS { Get-PSSession | Remove-PSSession }
```

<span data-ttu-id="e0de4-139">이 함수는 현재 **세션의 모든** pssession을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0de4-139">This function deletes all of the **PSSessions** in the current session.</span></span>
<span data-ttu-id="e0de4-140">이 함수를 PowerShell 프로필에 추가한 후 모든 세션을 삭제 하려면를 입력 `EndPSS` 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0de4-140">After you add this function to your PowerShell profile, to delete all sessions, type `EndPSS`.</span></span>

## <span data-ttu-id="e0de4-141">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e0de4-141">PARAMETERS</span></span>

### <span data-ttu-id="e0de4-142">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="e0de4-142">-ComputerName</span></span>

<span data-ttu-id="e0de4-143">컴퓨터 이름 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0de4-143">Specifies an array of names of computers.</span></span>
<span data-ttu-id="e0de4-144">이 cmdlet은 지정 된 컴퓨터에 연결 된 **Pssessions** 를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="e0de4-144">This cmdlet closes the **PSSessions** that are connected to the specified computers.</span></span>
<span data-ttu-id="e0de4-145">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0de4-145">Wildcard characters are permitted.</span></span>

<span data-ttu-id="e0de4-146">하나 이상의 원격 컴퓨터의 NetBIOS 이름, IP 주소 또는 정규화된 도메인 이름을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="e0de4-146">Type the NetBIOS name, an IP address, or a fully qualified domain name of one or more remote computers.</span></span>
<span data-ttu-id="e0de4-147">로컬 컴퓨터를 지정 하려면 컴퓨터 이름, localhost 또는 점 (.)을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0de4-147">To specify the local computer, type the computer name, localhost, or a dot (.).</span></span>

```yaml
Type: System.String[]
Parameter Sets: ComputerName
Aliases: Cn

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="e0de4-148">-ContainerId</span><span class="sxs-lookup"><span data-stu-id="e0de4-148">-ContainerId</span></span>

<span data-ttu-id="e0de4-149">컨테이너의 Id 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0de4-149">Specifies an array of IDs of containers.</span></span> <span data-ttu-id="e0de4-150">이 cmdlet은 지정 된 각 컨테이너에 대 한 세션을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0de4-150">This cmdlet removes sessions for each of the specified containers.</span></span> <span data-ttu-id="e0de4-151">명령을 사용 `docker ps` 하 여 컨테이너 id 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="e0de4-151">Use the `docker ps` command to get a list of container IDs.</span></span> <span data-ttu-id="e0de4-152">자세한 내용은 [docker ps](https://docs.docker.com/engine/reference/commandline/ps/) 명령에 대 한 도움말을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e0de4-152">For more information, see the help for the [docker ps](https://docs.docker.com/engine/reference/commandline/ps/) command.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ContainerId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="e0de4-153">-Id</span><span class="sxs-lookup"><span data-stu-id="e0de4-153">-Id</span></span>

<span data-ttu-id="e0de4-154">세션의 Id 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0de4-154">Specifies an array of IDs of sessions.</span></span>
<span data-ttu-id="e0de4-155">이 cmdlet은 지정 된 Id *를 가진 pssession을 닫습니다* .</span><span class="sxs-lookup"><span data-stu-id="e0de4-155">This cmdlet closes the *PSSessions* with the specified IDs.</span></span>
<span data-ttu-id="e0de4-156">하나 이상의 Id를 쉼표로 구분 하 여 입력 하거나 범위 연산자 (...)를 사용 하 여 Id 범위를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0de4-156">Type one or more IDs, separated by commas, or use the range operator (..) to specify a range of IDs.</span></span>

<span data-ttu-id="e0de4-157">ID는 현재 세션의 **PSSession** 을 고유 하 게 식별 하는 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="e0de4-157">An ID is an integer that uniquely identifies the **PSSession** in the current session.</span></span>
<span data-ttu-id="e0de4-158">이는 *InstanceId* 보다 쉽게 기억할 수 있으며, 입력은 현재 세션 에서만 고유 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0de4-158">It is easier to remember and type than the *InstanceId*, but it is unique only in the current session.</span></span>
<span data-ttu-id="e0de4-159">**PSSession** 의 ID를 찾으려면 매개 변수 없이 Get-PSSession cmdlet을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0de4-159">To find the ID of a **PSSession**, run the Get-PSSession cmdlet without parameters.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="e0de4-160">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="e0de4-160">-InstanceId</span></span>

<span data-ttu-id="e0de4-161">인스턴스 Id의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0de4-161">Specifies an array of instance IDs.</span></span>
<span data-ttu-id="e0de4-162">이 cmdlet은 지정 된 인스턴스 Id를 가진 **pssession을 닫습니다** .</span><span class="sxs-lookup"><span data-stu-id="e0de4-162">This cmdlet closes the **PSSessions** that have the specified instance IDs.</span></span>

<span data-ttu-id="e0de4-163">인스턴스 ID는 현재 세션의 **PSSession** 을 고유 하 게 식별 하는 GUID입니다.</span><span class="sxs-lookup"><span data-stu-id="e0de4-163">The instance ID is a GUID that uniquely identifies a **PSSession** in the current session.</span></span>
<span data-ttu-id="e0de4-164">인스턴스 ID는 단일 컴퓨터에서 여러 세션이 실행 되는 경우에도 고유 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0de4-164">The instance ID is unique, even when you have multiple sessions running on a single computer.</span></span>

<span data-ttu-id="e0de4-165">인스턴스 ID는 **PSSession** 을 나타내는 개체의 **InstanceID** 속성에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0de4-165">The instance ID is stored in the **InstanceID** property of the object that represents a **PSSession**.</span></span>
<span data-ttu-id="e0de4-166">현재 **세션에서 pssession의** **InstanceID** 를 찾으려면를 입력 `Get-PSSession | Format-Table Name, ComputerName, InstanceId` 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0de4-166">To find the **InstanceID** of the **PSSessions** in the current session, type `Get-PSSession | Format-Table Name, ComputerName, InstanceId`.</span></span>

```yaml
Type: System.Guid[]
Parameter Sets: InstanceId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="e0de4-167">-Name</span><span class="sxs-lookup"><span data-stu-id="e0de4-167">-Name</span></span>

<span data-ttu-id="e0de4-168">세션의 이름 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0de4-168">Specifies an array of friendly names of sessions.</span></span>
<span data-ttu-id="e0de4-169">이 cmdlet은 지정 된 이름을 가진 **pssession을 닫습니다** .</span><span class="sxs-lookup"><span data-stu-id="e0de4-169">This cmdlet closes the **PSSessions** that have the specified friendly names.</span></span>
<span data-ttu-id="e0de4-170">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0de4-170">Wildcard characters are permitted.</span></span>

<span data-ttu-id="e0de4-171">**PSSession** 이름이 고유 하지 않을 수 있으므로 *name* 매개 변수를 사용 하는 경우에는 **Remove Pssession** 명령에 *WhatIf* 또는 *Confirm* 매개 변수도 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="e0de4-171">Because the friendly name of a **PSSession** might not be unique, when you use the *Name* parameter, consider also using the *WhatIf* or *Confirm* parameter in the **Remove-PSSession** command.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="e0de4-172">-Session</span><span class="sxs-lookup"><span data-stu-id="e0de4-172">-Session</span></span>

<span data-ttu-id="e0de4-173">닫을 **pssession의 세션** 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0de4-173">Specifies the session objects of the **PSSessions** to close.</span></span>
<span data-ttu-id="e0de4-174">PSSession이 포함 된 변수 또는 PSSession을 만들거나 가져오는 **명령 (예**: New-PSSession 또는 **Get PSSession** 명령)을 **입력 합니다.**</span><span class="sxs-lookup"><span data-stu-id="e0de4-174">Enter a variable that contains the **PSSessions** or a command that creates or gets the **PSSessions**, such as a New-PSSession or **Get-PSSession** command.</span></span>
<span data-ttu-id="e0de4-175">하나 이상의 세션 개체를 **제거** 로 파이프 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0de4-175">You can also pipe one or more session objects to **Remove-PSSession**.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSession[]
Parameter Sets: Session
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="e0de4-176">-VMId</span><span class="sxs-lookup"><span data-stu-id="e0de4-176">-VMId</span></span>

<span data-ttu-id="e0de4-177">가상 컴퓨터의 ID 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0de4-177">Specifies an array of ID of virtual machines.</span></span>
<span data-ttu-id="e0de4-178">이 cmdlet은 지정 된 각 가상 컴퓨터와 대화형 세션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0de4-178">This cmdlet starts an interactive session with each of the specified virtual machines.</span></span>
<span data-ttu-id="e0de4-179">사용할 수 있는 가상 컴퓨터를 보려면 다음 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0de4-179">To see the virtual machines that are available to you, use the following command:</span></span>

`Get-VM | Select-Object -Property Name, ID`

```yaml
Type: System.Guid[]
Parameter Sets: VMId
Aliases: VMGuid

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="e0de4-180">-VMName</span><span class="sxs-lookup"><span data-stu-id="e0de4-180">-VMName</span></span>

<span data-ttu-id="e0de4-181">가상 컴퓨터의 이름 배열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e0de4-181">Specifies an array of names of virtual machines.</span></span>
<span data-ttu-id="e0de4-182">이 cmdlet은 지정 된 각 가상 컴퓨터와 대화형 세션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0de4-182">This cmdlet starts an interactive session with each of the specified virtual machines.</span></span>
<span data-ttu-id="e0de4-183">사용할 수 있는 가상 컴퓨터를 확인 하려면 **GET VM** cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0de4-183">To see the virtual machines that are available to you, use the **Get-VM** cmdlet.</span></span>

```yaml
Type: System.String[]
Parameter Sets: VMName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="e0de4-184">-Confirm</span><span class="sxs-lookup"><span data-stu-id="e0de4-184">-Confirm</span></span>

<span data-ttu-id="e0de4-185">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="e0de4-185">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e0de4-186">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="e0de4-186">-WhatIf</span></span>

<span data-ttu-id="e0de4-187">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e0de4-187">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="e0de4-188">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e0de4-188">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e0de4-189">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e0de4-189">CommonParameters</span></span>

<span data-ttu-id="e0de4-190">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e0de4-190">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e0de4-191">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e0de4-191">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e0de4-192">입력</span><span class="sxs-lookup"><span data-stu-id="e0de4-192">INPUTS</span></span>

### <span data-ttu-id="e0de4-193">Runspace입니다.</span><span class="sxs-lookup"><span data-stu-id="e0de4-193">System.Management.Automation.Runspaces.PSSession</span></span>

<span data-ttu-id="e0de4-194">세션 개체를이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0de4-194">You can pipe a session object to this cmdlet.</span></span>

## <span data-ttu-id="e0de4-195">출력</span><span class="sxs-lookup"><span data-stu-id="e0de4-195">OUTPUTS</span></span>

### <span data-ttu-id="e0de4-196">없음</span><span class="sxs-lookup"><span data-stu-id="e0de4-196">None</span></span>

<span data-ttu-id="e0de4-197">이 cmdlet은 개체를 반환하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e0de4-197">This cmdlet does not return any objects.</span></span>

## <span data-ttu-id="e0de4-198">참고</span><span class="sxs-lookup"><span data-stu-id="e0de4-198">NOTES</span></span>

* <span data-ttu-id="e0de4-199">*Id* 매개 변수는 필수입니다.</span><span class="sxs-lookup"><span data-stu-id="e0de4-199">The *Id* parameter is mandatory.</span></span> <span data-ttu-id="e0de4-200">현재 **세션의 모든** pssession을 삭제 하려면를 입력 `Get-PSSession | Remove-PSSession` 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0de4-200">To delete all the **PSSessions** in the current session, type `Get-PSSession | Remove-PSSession`.</span></span>
* <span data-ttu-id="e0de4-201">**PSSession** 은 원격 컴퓨터에 대 한 영구 연결을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0de4-201">A **PSSession** uses a persistent connection to a remote computer.</span></span> <span data-ttu-id="e0de4-202">데이터를 공유 하는 일련의 명령을 실행 하는 **PSSession** 을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e0de4-202">Create a **PSSession** to run a series of commands that share data.</span></span> <span data-ttu-id="e0de4-203">자세한 내용을 보려면 `Get-Help about_PSSessions`를 입력하십시오.</span><span class="sxs-lookup"><span data-stu-id="e0de4-203">For more information, type `Get-Help about_PSSessions`.</span></span>
* <span data-ttu-id="e0de4-204">Pssession **은 현재 세션에만 적용** 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0de4-204">**PSSessions** are specific to the current session.</span></span> <span data-ttu-id="e0de4-205">세션을 종료 하면 해당 세션에서 만든 **pssession이 강제로** 닫힙니다.</span><span class="sxs-lookup"><span data-stu-id="e0de4-205">When you end a session, the **PSSessions** that you created in that session are forcibly closed.</span></span>

## <span data-ttu-id="e0de4-206">관련 링크</span><span class="sxs-lookup"><span data-stu-id="e0de4-206">RELATED LINKS</span></span>

[<span data-ttu-id="e0de4-207">Connect-PSSession</span><span class="sxs-lookup"><span data-stu-id="e0de4-207">Connect-PSSession</span></span>](Connect-PSSession.md)

[<span data-ttu-id="e0de4-208">Disconnect-PSSession</span><span class="sxs-lookup"><span data-stu-id="e0de4-208">Disconnect-PSSession</span></span>](Disconnect-PSSession.md)

[<span data-ttu-id="e0de4-209">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="e0de4-209">Enter-PSSession</span></span>](Enter-PSSession.md)

[<span data-ttu-id="e0de4-210">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="e0de4-210">Exit-PSSession</span></span>](Exit-PSSession.md)

[<span data-ttu-id="e0de4-211">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="e0de4-211">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="e0de4-212">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="e0de4-212">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="e0de4-213">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="e0de4-213">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="e0de4-214">Receive-PSSession</span><span class="sxs-lookup"><span data-stu-id="e0de4-214">Receive-PSSession</span></span>](Receive-PSSession.md)

[<span data-ttu-id="e0de4-215">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="e0de4-215">about_PSSessions</span></span>](About/about_PSSessions.md)

[<span data-ttu-id="e0de4-216">about_Remote</span><span class="sxs-lookup"><span data-stu-id="e0de4-216">about_Remote</span></span>](About/about_Remote.md)
